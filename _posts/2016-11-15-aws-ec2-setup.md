---
layout: default
title: "AWS EC2 Setup"
category: aws
section: "ec2-setup"
date: 2015-11-05 14:08:09
order: 3
---

<div class="page-header">
  <h1>Setup Hydrograph on EC2</h1>
</div>

- [Create Key Pair](#create_key_pair)
- [Setup EC2](#setup)
   - [Select AMI] (#select-ami)
   - [Choose Instance Type] (#choose-instance-type)
   - [Configure Instance] (#configure-instance)
   - [Add Storage] (#add-storage)
   - [Add Tags] (#add-tags)
   - [Configure Security Group] (#configure-security-group)
   - [Review] (#review)
- [Hydrograph Setup Script](#hydrograph-setup-script)
- [Connecting to EC2 with WinSCP](#connect_with_winscp)
- [Connecting to EC2 with putty](#connect_with_putty)
- [Executing a job on EC2](#execute_job)
- [Commands](#commands)
- [Uninstall Hydrograph] (#uninstall-hydrograph)


Setting up Hydrograph on AWS EC2 instance is pretty easy and involves only a couple of 
extra steps if you are planning to spawn a new instance. 

If you already have an EC2 instance and want to setup Hydrograph on it, you can directly 
skip to the [Hydrograph Setup Script] (#hydrograph-setup-script) section. Please continue 
reading if you plan to spawn a new EC2 instance and setup Hydrograph on it.


<a name="create_key_pair"><br><br><br></a>
### Create Key Pair
In order to create an instance of EC2 or login through putty you must have a secure key, 
this key can be generated with below steps. This is one-time activity, as this key-pair 
can be used while creating any number of EC2 instances.<br>
Click on <b>Key Pairs</b> in left section of the screen.
<div class="left">
<img src="{{ site.baseurl }}/assets/img/aws_create_key_pair.png">
<br>Figure 1. Create Key Pair.
</div>
<br>

Provide a distinct <b>Key pair name</b>, e.g Eid-Hydrograph<br>Click on <b>Create</b>. 	
<br>A key-pair file is generated and downloaded with your browser. Save this file, as it 
will be used for login purpose.<br>

<div class="left">
<img src="{{ site.baseurl }}/assets/img/key_pair_name.png">
<br>Figure 2. Provide Key pair name.
</div>
<br>


<a name="setup"></a><br><br><br>
### Setup EC2
Check that the correct region is selected. For Richmond, VA, we use N. Virginia<br>

<div class="left">
<img src="{{ site.baseurl }}/assets/img/region_selection.png">
<br>Figure 3. Confirm you are pointing to the correct region.
</div>
<br>

<a name="select-ami"><br></a>
#### Select AMI
<b>Go to below link and select the appropriate AMI id assigned for your team based on - 
</b><br><ul>
	<li>Linux version (we recommend RHEL 7) </li><li>Account</li>
</ul>

Here, we have selected RHEL 7, us-east-1, STS Dev based on the Pulse reference page - 
<a href="https://pulse.kdc.capitalone.com/docs/DOC-80886">https://pulse.kdc.capitalone.com/docs/DOC-80886</a>
Select <b>My AMIs</b> tab and search for <b>AMI</b> and click on <b>Select</b><div class="left">
<img src="{{ site.baseurl }}/assets/img/search-ami.png">
<br>Figure 4. Search AMI id.
</div>
<a name="choose-instance-type"><br></a>
#### Choose Instance Type
<br>Select <b>m4.2xlarge</b> instance (you can choose other instances as per your need)<div class="left">
<img src="{{ site.baseurl }}/assets/img/select-instance-type.png">
<br>Figure 5. Select instance type.
</div>
Click on <b>Next: Configure Instance Details</b>

<a name="configure-instance-details"><br></a>
#### Configure Instance Details
Select Network as <b>vpc-c54307a0(10.206.32.0/19) | STS Dev East VPC</b><br>Select Subnet as <b>subnet-ba177e91(10.206.44.0/22) | STS Dev East VPC</b><br>Select IAM role as <b>CapOne-STS-Dev-CustomRole-Allinaws</b><br>
<div class="left">
<img src="{{ site.baseurl }}/assets/img/instance-details.png">
<br>Figure 6.1. Configure instance details.
</div>
<br>In this step, we’ll also setup Hydrograph and its dependencies by providing the below command under <b><i>Advanced Details > User data > As text</i></b> - <br>

```
#!/bin/bash

aws s3 cp s3://hydrograph-dev/setup_scripts/1.0.0/hydrograph-ec2-setup-userData.sh /home/ec2-user &&
chmod 755  /home/ec2-user/hydrograph-ec2-setup-userData.sh &&
/home/ec2-user/hydrograph-ec2-setup-userData.sh
```
<br><b><u>Note:</u></b> Please replace the Hydrograph version number (1.0.0 in the above example) 
          with the correct version. The <a href="{{ site.baseurl }}/versions">Hydrograph Engine Releases</a> page will 
          help you in selecting the version of Hydrograph Engine that best suited for you.
<br><br>
<div class="left">
<img src="{{ site.baseurl }}/assets/img/configureinstance-advanced.png" width="100%" height=100%">
<br>Figure 6.2. Configure instance details - Advanced Details.
</div>
<br><b><u>Note:</u></b> 
<br>This script will be run using the root user. Hence, appropriate IAM role should be selected. 
( IAM role may govern the root access ). 
<br>
The above script will install mainly following components on the EC2:
<br>1.	JDK
<br>2.	Hadoop
<br>3.	Hive
<br>4.	MySQL
<br>5.	Hydrograph Engine and its dependent libraries
<br>Alternatively, Hydrograph and its components can be manually installing using these <a href="#hydrograph-setup-script" >steps</a>.
<br>

Click on <b>Next: Add Storage</b>

<a name="add-storage"><br></a>
#### Add Storage
Hydrograph installation takes 7 GB of space approximately.  You must decide the amount of storage required, based on the Input files used and Output files generated by your job. <div class="left">
<img src="{{ site.baseurl }}/assets/img/add-storage.png">
<br>Figure 7. Add Storage.
</div>Click on <b>Next: Tag Instance</b>

<a name="add-tags"><br></a>
#### Add Tags
Add Below tags,<br> <b>ASV: </b><span style="background-color: #00FFFF">ASVSTSRESEARCH</span>
<br><b>CMDBEnvironment: </b><span style="background-color: #00FFFF">ENVNPSTSEDSRESEARCHAWS</span>
<br><b>Name: </b>Hydrograph-Hadoop (change the highlighted portion as per your need e.g. Hydrograph-
<span style="background-color: #FFFF00">projectName</span>)
<br><b>OwnerContact :</b>EDS-<span style="background-color: #FFFF00">rwq133</span> 
(change the highlighted portion with your id)<br>
<br>Use <span style="background-color: #00FFFF">Highlighted</span> values as per your project/team
<br>Refer below pages for more information on AWS tags,
<br><a href="https://pulse.kdc.capitalone.com/docs/DOC-102610">https://pulse.kdc.capitalone.com/docs/DOC-102610</a>
<br><a href="https://pulse.kdc.capitalone.com/docs/DOC-166586">https://pulse.kdc.capitalone.com/docs/DOC-166586</a>
<br><a href="https://pulse.kdc.capitalone.com/docs/DOC-123713">https://pulse.kdc.capitalone.com/docs/DOC-123713</a>
<br><div class="left">
<img src="{{ site.baseurl }}/assets/img/tag-instance.png" style="width:100%">
<br>Figure 8. Tag instance.
</div>Click <b>Next: Configure Security Group</b>

<a name="configure-security-group"><br></a>
#### Configure Security Group
<br>Select security role as <b>sg-1b6f3e7f</b>
<div class="left">
<img src="{{ site.baseurl }}/assets/img/configure-security-group.png">
<br>Figure 9. Configure security group.
</div>Click <b>Review and Launch</b>

<a name="review"><br></a>
#### Review
Review the configurations<br><div class="left">
<img src="{{ site.baseurl }}/assets/img/review-instance.png">
<br>Figure 10. Review instance configuration before launch.
</div>Click on <b>Launch</b>Create a key pair for first time if you don’t have a key-pair 
or select one if you have one.
<br>Make sure it is distinct (add your Eid in it, do not use the one shown in slides)
<br><div class="left">
<img src="{{ site.baseurl }}/assets/img/select-create-key-pair.png">
<br>Figure 11. Select an existing key pair or create new one.
</div>Click on <b>Launch Instances</b>,<br>

Click on the link provided in green area to see the progress of the instance you have created. i.e. <b>i-26cb7216</b><div class="left">
<img src="{{ site.baseurl }}/assets/img/launch-status.png">
<br>Figure 12. Launch status.
</div>
<br>
Once the instance is up and running, you can try connecting to it using Putty (or any of your favourite ssh client) and check the progress of the installation by using below command:
<br>
``
tail -f /var/log/cloud-init.log
``
<br><br>The script also saves installation logs in <b>/home/ec2-user/logs/hydrograph_setup.log</b>.


<a name="hydrograph-setup-script"></a><br><br><br>
###Manually setting up Hydrograph using a setup script
In case you already have an EC2 instance up and running, go to the <a href="https://console.aws.amazon.com/s3/home?region=us-east-1#&bucket=hydrograph-dev&prefix=setup_scripts/">S3</a>
 location and copy the setup script file - <b><i> hydrograph-ec2-setup-1.0.0.sh</i></b> to your local computer based on the version of the Hydrograph you want to setup on EC2 instance.<br>
 <b>Note:</b> There may be multiple versions of Hydrograph present in the S3 location provided above. Refer this link to find more on the latest version of Hydrograph available.<br>



<a name="connect_with_winscp"></a><br><br><br>
### Connecting to EC2 with WinSCP
<ul>	<li>Open WinSCP</li>	<li>Use private ip address of the EC2 instance as host name</li>	<li>Provide ec2-user as User name</li>	<li>Click on Advanced button</li>
</ul><div class="left">
<img src="{{ site.baseurl }}/assets/img/winscp-details.png" width=50%>
<br>Figure 13. WinSCP connection details.
</div><br><ul>	<li>Select Authentication section and provide ppk file</li>	<li>Click OK</li>	<li>Login to the EC2 instance and copy script file( copied from s3 ) to /home/ec2-user/</li>
</ul><a name="connect_with_putty"></a><br><br><br>
### Connecting to EC2 with puttyFollow below link to setup putty session to connect to ec2 <a href="https://pulse.kdc.capitalone.com/docs/DOC-130260">https://pulse.kdc.capitalone.com/docs/DOC-130260</a><div class="left">
<img src="{{ site.baseurl }}/assets/img/connect-with-putty.png" width=50%>
<br>Figure 14. Putty connection details.
</div>
<br>
Change the script permission to 754 with below command<br>
``
	chmod 754 hydrograph-ec2-setup-1.0.0.sh
``
<ul>
	<li>Run script with below command</li>
</ul>
``
	./hydrograph-ec2-setup-1.0.0.sh
``

If Script asks for yes/no option, type yes and hit Enter.
<br>The above script will install mainly following components on the EC2:
<br>1.	JDK
<br>2.	Hadoop
<br>3.	Hive
<br>4.	MySQL
<br>5.	Hydrograph Engine and its dependent libraries



<a name="execute_job"></a><br><br><br>### Executing a job on EC2
<ul>	<li>As a part of initial setup some preloaded examples are added in the ec2 instance with folder structure similar as below, under /home/ec2-user/</li>
</ul><div class="left">
<img src="{{ site.baseurl }}/assets/img/directory_structure.png">
<br>Figure 15. Directory structure of the sample project.
</div><ul>	<li>Use below command to execute the job, update the highlighted sections as per your directory structure and file names</li>
</ul>
``cd /home/ec2-user/examples && /devl/code/tools/sts_hydrogrph_engn/scripts/hydrograph-exec.sh -xmlpath jobs/Generate_Records.xml -libjars lib/TestingSetup-1.0.jar -paramfiles param/Generate_Records.properties``

Use below values as Runtime Properties in hydrograph job when job contains hive component,<br>
``Key: hive.metastore.uris Value: thrift://localhost:9083``<a name="commands"></a><br><br><br>### Commands Hadoop services are shut down whenever EC2 instance is restarted/stopped. Use below commands to start the services again before executing any job.<br><br>To start Hadoop <br>
``$HADOOP_HOME/sbin/start-dfs.sh``
<br>
``$HADOOP_HOME/sbin/start-yarn.sh
``<br><br>To start Hive Service<br>``hive --service hiveserver &
``
<br>
``hive --service metastore &``<br>Hive services are not started by default. Hence in order to run a job containing hive component, start the hive services with above command.<br><br>To Stop Hadoop
<br>``$HADOOP_HOME/sbin/stop-yarn.sh``
<br>
``$HADOOP_HOME/sbin/stop-dfs.sh``
<br>
<a name="uninstall-hydrograph"></a><br><br><br>	
### Uninstall Hydrograph
The <b>uninstall_hydrograph.sh</b> script can be used for uninstalling Hydrograph and all its dependencies from the EC2 instance. 
This script can be found under the same <a href="https://console.aws.amazon.com/s3/home?region=us-east-1#&bucket=hydrograph-dev&prefix=setup_scripts/">S3 bucket</a>.
<br>
This script may be useful if you come across any issues with automated Hydrograph install and components are partially installed. In such cases, run both, uninstall script and then installation script (<b>hydrograph-ec2-setup-1.0.0.sh</b>) manually.   

