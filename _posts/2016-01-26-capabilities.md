---
layout: default
title: "Capabilities"
category: ref
section: "system-and-capabilities"
date: 2016-01-26 14:02:27
order: 1
---

<div class="page-header">
<h1>Capabilities</h1>
</div>

  - [Development Interface](#Dev-Int)
  - [Sources](#Sources)
  - [Sinks](#Sinks)
  - [Transformations](#Transformations)

<a name="Dev-Int"></a>

---
<br>
<br>
<h2> Development Interface </h2>

<p> This section outlines the capabilities of Hydrograph's development interface that are either available or will be implemented in the future.
 </p>

<table class="table table-hover" style="width:100%">
  <tr class = "info"><i>
    <td> High Level Capability </td>
    <td> Capability Category </td>
    <td> Status </td>
    <td> Description </td>
  </i></tr>

  <tr>
    <td> Schema Propagation </td>
    <td> Dev TTM </td>
    <td> Available </td>
    <td> Hydrograph will automatically propagate schema from one component to the next connected component(s) to remove unnecessary re-entering of schema. </td>
  </tr>

  <tr>
    <td> Content Assistance </td>
    <td> Dev TTM </td>
    <td> Available </td>
    <td> Hydrograph inherently has auto completion and contents assistance based off of Eclipse IDE. </td>
  </tr>

  <tr>
    <td> Hydrograph Local Execution </td>
    <td> Dev TTM </td>
    <td> Available </td>
    <td> In order to allow for quick validation of data pipeline, Hydrograph allows for the execution to occur within the interface, utilizing local filesystem and resources. </td>
  </tr>

  <tr>
    <td> Hydrograph Remote Execution </td>
    <td> Dev TTM </td>
    <td> Available </td>
    <td> Hydrograph can launch the ETL job remotely via an edge node and submit to a Hadoop cluster. </td>
  </tr>

  <tr>
    <td> Github Integration </td>
    <td> CICD </td>
    <td> Available </td>
    <td> Hydrograph is integrated with Github such that users can check-in and check-out code from Git through interface. </td>
  </tr>

  <tr>
    <td> Data Inspection </td>
    <td> Debug </td>
    <td> In-progress </td>
    <td> In order for users to validate ETL pipeline is functioning, Hydrograph allows for users to inspect data at each point of the pipeline. </td>
  </tr>

</table>
<!--due to page spacing on top bar, anchoring here-->
<a name="Sources"></a>

<div class = "center"> <p> Table 1. Hydrograph's development interface capabilities. </p> </div>

<br>
<h2> Sources </h2>

<p> This section outlines the data sources Hydrograph can ingest from as part of it's data pipeline.
</p>

<table class="table table-hover" style="width:100%">
  <tr class = "info"><i>
    <td> Data Source </td>
    <td> Grouping </td>
    <td> Status </td>
    <td> Description </td>
  </i></tr>

  <tr>
    <td> Delimited File </td>
    <td> Flat File </td>
    <td> Available </td>
    <td> File with fields separated by a single unique delimiter value. </td>
  </tr>

  <tr>
    <td> Fixed Width File </td>
    <td> Flat File </td>
    <td> Available </td>
    <td> File with fixed length fields. </td>
  </tr>

  <tr>
    <td> Mixed Scheme File </td>
    <td> Flat File </td>
    <td> Available </td>
    <td> File with fields separated by varied delimiter values. </td>
  </tr>

  <tr>
    <td> S3 </td>
    <td> Flat File </td>
    <td> Backlog </td>
    <td> File residing in AWS S3 bucket. </td>
  </tr>

  <tr>
    <td> EBCDIC File </td>
    <td> Flat File </td>
    <td> Backlog </td>
    <td> Mainframe EBCDIC formatted file. </td>
  </tr>

  <tr>
    <td> Parquet File </td>
    <td> File with Schema </td>
    <td> Available </td>
    <td> Apache Parquet columnar storage format. </td>
  </tr>

  <tr>
    <td> Hive </td>
    <td> Database </td>
    <td> Available </td>
    <td> Text or Parquet Hive table. </td>
  </tr>

  <tr>
    <td> Generate Record </td>
    <td> Misc </td>
    <td> Available </td>
    <td> Ability to generate datasets at a record level that correspond to the datatypes specified by the schema. </td>
  </tr>  

</table>
<!--due to page spacing on top bar, anchoring here-->
<a name="Sinks"></a>

<div class = "center"> <p> Table 2. Hydrograph's source taps. </p> </div>


<br>
<h2> Sinks </h2>
<p> This section outlines the data sinks Hydrograph can load to as part of it's data pipeline.
</p>

<table class="table table-hover" style="width:100%">
  <tr class = "info"><i>
    <td> Data Sink </td>
    <td> Grouping </td>
    <td> Status </td>
    <td> Description </td>
  </i></tr>

  <tr>
    <td> Delimited File </td>
    <td> Flat File </td>
    <td> Available </td>
    <td> File with fields separated by a single unique delimiter value. </td>
  </tr>

  <tr>
    <td> Fixed Width File </td>
    <td> Flat File </td>
    <td> Available </td>
    <td> File with fixed length fields. </td>
  </tr>

  <tr>
    <td> Mixed Scheme File </td>
    <td> Flat File </td>
    <td> Available </td>
    <td> File with fields separated by varied delimiter values. </td>
  </tr>

  <tr>
    <td> S3 </td>
    <td> Flat File </td>
    <td> Backlog </td>
    <td> File residing in AWS S3 bucket. </td>
  </tr>

  <tr>
    <td> Parquet File </td>
    <td> File with Schema </td>
    <td> Available </td>
    <td> Apache Parquet columnar storage format. </td>
  </tr>

  <tr>
    <td> Hive </td>
    <td> Database </td>
    <td> Available </td>
    <td> Text or Parquet Hive table.  </td>
  </tr>

  <tr>
    <td> Redshift </td>
    <td> Database </td>
    <td> Backlog </td>
    <td> Redshift table with defined schema. </td>
  </tr>

</table>
<!--due to page spacing on top bar, anchoring here-->
<a name="Transformations"></a>

<div class = "center"> <p> Table 3. Hydrograph's sink taps. </p> </div>


<br>
<h2> Transformations </h2>

<p> This section outlines the data transformation capabilities of Hydrograph.
</p>

<table class="table table-hover" style="width:100%">
  <tr class = "info"><i>
    <td> Data Transformation </td>
    <td> Grouping </td>
    <td> Status </td>
    <td> Description </td>
  </i></tr>

  <tr>
    <td> Aggregate </td>
    <td> Transform </td>
    <td> Available </td>
    <td> Ability to aggregate fields across multiple records grouped by specified key field(s). </td>
  </tr>

  <tr>
    <td> Cumulate </td>
    <td> Transform </td>
    <td> Available </td>
    <td> Similar to Aggregate but has additional capabilities to output intermediate data points within groups specified by key field(s). </td>
  </tr>

  <tr>
    <td> Filter </td>
    <td> Transform </td>
    <td> Available </td>
    <td> Ability to filter data at a record level from 1 input flow into 2 output flows. </td>
  </tr>

  <tr>
    <td> Join </td>
    <td> Transform </td>
    <td> Available </td>
    <td> Ability to join multiple datasets based on common key field(s) specified. </td>
  </tr>  

  <tr>
    <td> Lookup </td>
    <td> Transform </td>
    <td> Available </td>
    <td> Ability to join a large dataset with a small dataset based on common key field(s) specified. </td>
  </tr>

  <tr>
    <td> Normalize </td>
    <td> Transform </td>
    <td> Available </td>
    <td> Ability to explode a single record into many. </td>
  </tr>

  <tr>
    <td> Transform </td>
    <td> Transform </td>
    <td> Available </td>
    <td> Ability to transform 1 input record scheme into 1 output record scheme. </td>
  </tr>

  <tr>
    <td> Unique Sequence </td>
    <td> Transform </td>
    <td> Available </td>
    <td> Ability to generate an unique sequence on a defined field for each record in dataset. </td>
  </tr>

  <tr>
    <td> Clone </td>
    <td> Straight Pull </td>
    <td> Available </td>
    <td> Ability to clone a dataset from 1 input to many. </td>
  </tr>

  <tr>
    <td> Discard </td>
    <td> Straight Pull </td>
    <td> Available </td>
    <td> Ability to explicitly declare removal of unnecessary data from an entire pipeline. </td>
  </tr>

  <tr>
    <td> Limit </td>
    <td> Straight Pull </td>
    <td> Available </td>
    <td> Ability to limit the number of records flowing out of component. </td>
  </tr>

  <tr>
    <td> Sort </td>
    <td> Straight Pull </td>
    <td> Available </td>
    <td> Ability to sort input dataset based on defined key(s). </td>
  </tr>

  <tr>
    <td> Remove Duplicate </td>
    <td> Straight Pull </td>
    <td> Available </td>
    <td> Ability to remove duplicate records based on defined key(s) and order to remove/retain. </td>
  </tr>

  <tr>
    <td> Union All </td>
    <td> Straight Pull </td>
    <td> Available </td>
    <td> Ability to combine multiple datasets of the same schema into one stream in the pipeline. </td>
  </tr>  






</table>
<div class = "center"> <p> Table 4. Hydrograph's data transformation components. </p> </div>
