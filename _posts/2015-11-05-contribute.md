---
layout: default
title: "Contribute"
category: con
section: "contribute"
date: 2015-11-05 14:08:09
order: 3
---

<div class="page-header">
  <h1>Contribute to Hydrograph!</h1>
</div>

- [Overview](#overview)
- [Initial Setup](#setup)
- [Create Working Directory](#working)
- [Commit](#commit)
- [Push](#push)
- [Rebase](#rebase)
- [Pull Request](#pullrequest)


<a name="overview"><br><br><br></a>
### Overview
Please see our <a href="https://github.kdc.capitalone.com/SDH/Hydrograph/issues">GitHub Issues</a> for detailed information on the features/bugs in our backlog. Feel free to pick and work on an issue of interest. Our suggested Git workflow on how to contribute is detailed in the below sections.
<div class="left">
<img src="{{ site.baseurl }}/assets/img/git_flow.png">
<br>Figure 1. Git Workflow Diagram.
</div>
<br>
<a name="setup"></a><p><br><br><br></p>
### Initial Setup
1. Fork <a href="https://github.kdc.capitalone.com/SDH/Hydrograph/">Hydrograph</a>, this will fork the project under your user as, user_name/Hydrograph. Clone this project with url given on screen:<br>
```
git clone https://github.com/user-name/Hydrograph.git
```
2. Cloned project will be available on your machine under git directory, this will be your working directory
3. Create a remote to main-remote project from the command line with following command:<br>
```
git remote add upstream https://github.com/capitalone/Hydrograph.git
```
<br>
Now you have two remotes with your working directory:<br>
  * origin: This remote is created when you clone the project. We will use this remote to push the changes to user-remote project (the one cloned above).<br>
  * upstream:  This remote will be used to sync(pull) the working directory from main-remote project. We will rebase new branch with ui_integrator branch.

4.	Fetch all upstream branches to local<br>
```
git fetch --all
```
5.	Create local branches from remote branches<br>
```
git checkout –b ui_integrator upstream/ui_integrator
```

<a name="working"></a><p><br><br><br></p>
### Create Working Directory
You will be working on local branches which will be created from ui_integrator. Below command creates a local branch from ui_integrator:<br>
```
git checkout –b branchName ui_integrator
```
<br>
Follow one of the below naming conventions for branchName:<br>
<ul><li>feature/featureName</li>
<li>hotfix/hotFixName</li>
<li>bug/bugIdOrShortDescription</li></ul>

<a name="commit"></a><p><br><br><br></p>

### Commit


In order to commit the changes, mark the files(add to index) which needs to be committed.<br>
To check which files have been changed since last commit, use<br>
```
git status
```
<br>To mark files one by one, use<br>
```
git add file_name
```
<br>
To mark all the added/modified files at once, use<br>
```
git add --all
```
<br>
Now commit to commit changes, use<br>
```
git commit -m 'provide the commit message description here'
```

<a name="push"></a><p><br><br><br></p>
### Push
After adding and committing your changes on local branchName, push it to user-remote with below commands<br>
```
git checkout branchName
```
<br>
```
git push origin branchName
```
<br><b>Note</b>: Above push command would work when you are pushing new branch for the first time only. For pushing rebased code, please refer <a href="#rebase">Rebase</a> section.

<a name="rebase"></a><p><br><br><br></p>
### Rebase
You should rebase your branchName periodically, in order to solve any file merges locally. Also make sure branch is rebased to latest commit before sending a merge request.<br>
```
git checkout branchName
```
<br>
```
git rebase integrator
```
<br><br>
This process might halt when git cannot do a merge automatically and has to be done manually. In that case:<br>

1. Go to the file specified on command prompt and do the manual merge
2. Add those files to index with:
```
git add -u
```
3. Continue the rebase with:
```
git rebase --continue
```

If you want to abort this process in between then use,
```
git rebase -–abort
```

Once done with rebase, you can push your changes to origin branch.Please note that after rebase, push may fail because changes in branch history. 
Hence, we need to force push using -f option.
```
git push -f origin branchName
```

<a name="pullrequest"></a><p><br><br></p>
### Pull Request
Raise pull request in order to send your changes for review and merging in ui_integrator branch.

1. Click on New Pull Request
2. Select base fork as capitalone/Hydrograph
3. Select base as ui_integrator
4. Select head fork as user-name/Hydrograph
5. Select compare as branchName
  * If it says can’t automatically merge, follow the [Rebase](#rebase) step again
6. Provide description and click on Create Pull Request
