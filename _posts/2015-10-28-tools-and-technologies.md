---
layout: default
title: "Technologies"
category: con
section: "technologies"
date: 2015-10-28 18:59:19
order: 4
---

<div class="page-header">
<h1>Tools and Technologies</h1>
<p>The parts that make up Hydrograph and why.</p>
</div>

<h3>User Interface</h3>

<table class="table table-hover" style="width:100%">
  <tr class = "info"><i>
    <td> Technology </td>
    <td> Description/Usage </td>
    <td> Version </td>
    <td> License </td>
  </i></tr>

  <tr>
    <td> Java </td>
    <td> A high-level, object-oriented programming language </td>
    <td> 1.7 </td>
    <td> Oracle Binary Code License </td>
  </tr>

  <tr>
    <td> Eclipse IDE </td>
    <td> An itegrated development environment (IDE)</td>
    <td> 3.7 </td>
    <td> Eclipse Public License 1.0</td>
  </tr>

  <tr>
    <td> Graphical Editing Framework (GEF) </td>
    <td> An extensible framework used to create rich graphical applications on the Eclipse platofrm </td>
    <td> 3.11 </td>
    <td> Eclipse Public License 1.0 </td>
  </tr>

  <tr>
    <td> Rich Client Platform (RCP) </td>
    <td> The minimal set of plug-ins needed to build a rich client application in the Eclipse platform </td>
    <td> 3.7 </td>
    <td> Eclipse Public License 1.0 </td>
  </tr>

  <tr>
    <td> RCP Testing Tool (RCPTT) </td>
    <td> A utility for testing Eclipse plug-ins and RCP applications </td>
    <td> 2.0.0 </td>
    <td> Eclipse Public License 1.0 </td>
  </tr>

  <tr>
    <td> XStream </td>
    <td> A library to serialize objects to XML </td>
    <td> 1.4.4 </td>
    <td> BSD </td>
  </tr>

  <tr>
    <td> Java Architecture for XML Binding (JAXB) </td>
    <td> Used to read config files and generate target XML </td>
    <td> 2.2 </td>
    <td> CDDL & GPL2 </td>
  </tr>

  <tr>
    <td> SLF4J </td>
    <td> Used for logging </td>
    <td> 1.6 </td>
    <td> MIT </td>
  </tr>

  <tr>
    <td> Maven </td>
    <td> To build and package the application </td>
    <td> 3.2 </td>
    <td> Apache License 2.0 </td>
  </tr>

  <tr>
    <td> Tycho </td>
    <td> A set of Maven plugins for building Eclipse plugins </td>
    <td> 0.23 </td>
    <td> Eclipse Public License 1.0 </td>
  </tr>

  <tr>
    <td> Gradle </td>
    <td> To automate cross platform builds </td>
    <td> 2.7 </td>
    <td> Apache License 2.0 </td>
  </tr>

</table>

<h3>Engine</h3>

<table class="table table-hover" style="width:100%">
  <tr class = "info"><i>
    <td> Technology </td>
    <td> Description/Usage </td>
    <td> Version </td>
    <td> License </td>
  </i></tr>

  <tr>
    <td>Cascading</td>
    <td>The underlying execution platform. Cascading is an application development platform for building data applications on Hadoop. Cascading supports MapReduce and Tez.</td>
    <td>3.0.2</td>
    <td>Apache License 2.0</td>
  </tr>

  <tr>
    <td>Cascading-Hive</td>
    <td>Integrates Apache Hive and Cascading. Used for creating Hive based input/output components.</td>
    <td>2.0</td>
    <td>Apache License 2.0</td>
  </tr>

  <tr>
    <td> Java Architecture for XML Binding (JAXB) </td>
    <td> Used for binding Hydrograph XML to Java classes. JAXB classes are generated from the XSD defined for XML structure. These JAXB classes are used to pass the XML content to the execution layer. </td>
    <td> 2.2 </td>
    <td> CDDL & GPL2 </td>
  </tr>

  <tr>
    <td>Parquet-Cascading</td>
    <td>Used for creating Parquet based input/output components and transforming a Cascading object to/from a Parquet schema.</td>
    <td>1.6</td>
    <td>Apache License 2.0</td>
  </tr>

  <tr>
    <td>Cascading.Avro</td>
    <td>Used for reading and writing data serialized using Apache Avro.</td>
    <td>2.5</td>
    <td>Apache License 2.0</td>
  </tr>

  <tr>
    <td>Riffle</td>
    <td>A lightweight Java library for executing collections of dependent processes as a single process. Is used in tandem with Cascading flows.</td>
    <td>1.0</td>
    <td>Apache License 2.0</td>
  </tr>

  <tr>
    <td>Plunger</td>
    <td>A unit test framework for Cascading.</td>
    <td>3.0.1</td>
    <td>Apache License 2.0</td>
  </tr>

</table>

<h3> Decision Rationale </h3>
<br>
<i> Eclipse vs. NetBeans </i>
<br>

<table class="table table-hover" style="width:100%">
  <tr class = "info"><i>
    <td> Feature </td>
    <td> Eclipse </td>
    <td> NetBeans </td>
  </i></tr>

  <tr>
    <td> Community support & documentation </td>
    <td> Large community; comprehensive documentation </td>
    <td> Small community; commercial support available; comprehensive documentation </td>
  </tr>

  <tr>
    <td> Tutorials and books </td>
    <td> Available </td>
    <td> Available </td>
  </tr>

  <tr>
    <td> Visual library </td>
    <td> Although RCP has a learning curve, there are an ample number of tutorials </td>
    <td> Easy to use </td>
  </tr>  

  <tr>
    <td> Build tool support </td>
    <td> Development on PDE halted March 2015, but another plugin, https://eclipse.org/tycho/, still has traction. </td>
    <td> Ant & Maven supported </td>
  </tr>

  <tr>
    <td> Internet app </td>
    <td> Eclipse Remote Application Platform (RAP) enables you to reuse your desktop application as an internet app </td>
    <td> N/A </td>
  </tr>

  <tr>
    <td> Unit/integration/functional Testing </td>
    <td> There are several available frameworks: https://github.com/lcarbonn/robotframework-eclipselibrary, https://www.eclipse.org/jubula/ & https://www.eclipse.org/rcptt/ </td>
    <td> Built-in support </td>
  </tr>

  <tr>
    <td> Platform support </td>
    <td> Separate distributions for 64-bit and 32-bit </td>
    <td> Same installation for both </td>
  </tr>

  <tr>
    <td> Platform applications </td>
    <td> More than 19 million applications are available via the Eclipse Marketplace, http://marketplace.eclipse.org/ </td>
    <td> Projects span across 14 industries (https://platform.netbeans.org/screenshots.html) </td>
  </tr>

</table>
