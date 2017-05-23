# Chapter 1, Section 1: Introduction to Hadoop

## What is Apache Hadoop?

Hadoop is a collection of open source software frameworks for distributed processing and storage of large data sets. Hadoop is a community project, distributed under licenses from the Apache Software Foundation. Contributions to Hadoop can be made by anyone: performance improvements, new features, bug fixes are well welcomed.

Hadoop Clusters are scalable and range from as few as one machine (virtual or physical) to thousands. Clusters are fault tolerant. Hadoop services achieve this through redundancy. Clusters are designed to be created using commodity hardware, which not only reduces the price of platform, but potentially reduces support costs as well.

Hadoop also uses distributed storage and processing to achieve massive scalability. Large datasets are automatically split into smaller chunks, called blocks which are distributed across the cluster of machines. In addition to this, each machine commonly processes its local block of data. This means that processing is distributed too, potentially across hundreds of CPUs and hundreds of gigabytes of memory.

## Hadoop Cluster Node Types

Hadoop is often deployed on rack-based servers but can be deployed on Virtual Machines either on-premises or on public cloud.

```
   Need diagram for cluster types
```

This diagram illustrates the main types of nodes in a Hadoop cluster:

- Master Nodes: These types of node manage and coordinate cluster services and tasks. They are master nodes because they have various Hadoop master processes running on them. For example, a master node runs the NameNode process that coordinates Hadoop storage operations. A single machine can run all of the Hadoop master processes, however, for better scalability and higher availability, it is common to have all the various Hadoop master processes spread across multiple master nodes.

- Worker Nodes: These types of node provide the CPU, memory and local disk resources to store and process data. They are worker nodes because they have various Hadoop worker processes running on them. For example, a worker node runs a DataNode process which is managed by the NameNode. The DataNode performs the task of actually reading and writing data blocks to storage. A Hadoop cluster is easily scaled up by adding additional worker machines.

- Utility Machine: These types of node have the Hadoop client-side software installed. Client software is used to submit data processing jobs to the cluster. Machines outside of the cluster can also act as a gateway machine to the cluster. Such machines may have dedicated network access or cluster management software available, such as Apache Knox or Apache Ambari.

## Hadoop Cluster Resource Management

```
  Need Diagram of YARN/HDFS
```

YARN: Yet Another Resource Negotiator. This service manages worker node CPU and memory resources. Other lessons provide more detail about the architecture and operation of the YARN service.

HDFS: Hadoop Distributed File System (HDFS). This service manages cluster storage resources.

Worker nodes provide CPU, memory, storage and network resources to a Hadoop cluster. The resources provided by these nodes are used to process data. The network resources for worker nodes are managed by the underlying operating system. Network resources are also managed at the switch level by the network operating system (NOS).

## Apache Software Frameworks

```
  Need diagram of Hadoop and different apache frameworks
```

Hadoop is a collection of different software frameworks and not a single piece of software. Most of the frameworks are part of the Apache software ecosystem. Each tool in Hadoop is designed for a specific purpose. The functionality of some tools overlap but typically one tool is going to be better than others when performing certain tasks.

## Data Management and Operations Frameworks

There are two data management frameworks known as HDFS and YARN:

- HDFS is a Java-based distributed file system which provides scalable, reliable and high-throughput access to application data stored across multiple servers. The file system is similar to many other conventional file systems such as the Linux File System. HDFS supports read, write and delete operations on file.

- YARN is used for cluster resource management and job scheduling. It allows for multiple data processing engines such as Interactive SQL, real-time streaming, data science and batch processing to con-exist on a single cluster.

There are four Operations Frameworks:

- Ambari provides a Web UI for managing, provisioning and monitoring Hadoop clusters. The software also provides a collection of intuitive  operator tools and RESTful APIS that simplify the complexity of Hadoop and the operations of clusters.

- Zookeeper is used to coordinate distributed applications and services. It is designed to mitigate race conditions, deadlock, scalability and security issues, network outages, bandwidth limitations and synchronization issues.

- CloudBreak is a tool for provisioning, managing and monitoring on-demand clusters. It is used to automate the launching of elastic Hadoop clusters with policy-based autoscaling on most major cloud platforms, such as Microsoft Azure, Amazon Web Services (AWS), Google Cloud Platform, Openstack and Docker containers.

- Oozie is a server-based workflow engine used to execute Hadoop jobs. Oozie enables Hadoop users to build and schedule complex data transformations by coming MapReduce, Apache Hive, Apache Pig and Apache Sqoop jobs into a single, logical unit of work. Oozie can also perform Java, Linux shell, distcp, SSH, email and other operations.

## Data Access Frameworks

Hadoop includes a number of different Data Access Frameworks:

- Apache Pig is used for extracting, transforming and analyzing large datasets. It is also useful for traversing the HDFS file system with commands like cd and ls. Pig includes a scripted, procedural-based language that excels at building data pipelines to aggregate and add structure to data.

- Apache Hive is a tool which allows you to use SQL-like queries against data in Hadoop. The SQL queries are automatically converted to

- Apache HCatalog is a table information, schema, and metadata management system for Hive, Pig, MapReduce, Tez. HCatalog is actually a module in Hive that enables non-Hive tools to access Hive metadata tables. This tool also provides a REST API named WebHCat which makes metadata and table information available to other vendors tools.

- Cascading is an application development framework for building data applications on top of Hadoop. Acting an an abstraction layer, it allows applications to run MapReduce jobs.

- Apache HBase is a non-relation database (otherwise known as a no SQL database). HBase was created for hosting very large tables with billions of rows and millions of columns. HBase was created for hosting very large tables with billions of rows and millions of columns. HBase provides random, real-time access to data. It adds some transactional capabilities to Hadoop, allowing users to conduct table inserts, updates, scans and deletes.

- Apache Phoenix is a client-side SQL front-end for HBase that provides direct, low-latency access to HBase. It is written in Java and enables querying and managing HBase tables using SQL commands.

- Apache Accumulo is a low-latency, large table data storage and retrieval system with cell-level security. It is based on Google's Bigtable but runs on YARN.

- Apache Storm is a distributed computation system for processing continuous streams of real-time data. Storm augments the batch processing capabilities provided by MapReduce and

- Apache Solr is a distributed search platform capable of indexing petabytes of data. It provides user-friendly, interactive search to help businesses find data patterns, relationships and correlations across such data.

- Apache Spark is an open source, general purpose processing engine that allows data scientists to build and run fast, sophisticated applications on Hadoop. It provides a simple set of easy-to-understand programming APIS that are used to build applications at a rapid pace in Scala. It also supports SQL-like queries, streaming data applications, complex analytics such as machine learning and graph algorithms.

- Apache Falcon is a data governance tool. It provides a workflow orchestration framework for data motion, coordination of data pipelines, lifecycle management and data discovery. Falcon enables data stewards and Hadoop administrators to quickly onboard data and configure its associated processing and management on Hadoop clusters.

- WebHDFS uses the standard HTTP verbs GET, PUT, POST and DELETE to access, operate and manage HDFS. Using WebHDFS, a user can create, list and delete directories, as well as create, read, append and delete files. A user can also manage file and directory ownership/permissions using WebHDFS.

- The HDFS NFS Gateway allows access to HDFS as though it were part of an NFS client's local file system. The Hadoop file system can be mounted using a regular NFS client mount, which allows regular bash commands to be used for copying/backing up data, running scripts, exploring the file system, or modifying data on HDFS.

- Apache Flume is a distributed, reliable and available service that efficiently collects, aggregates and moves streaming data. It is a distributed service because it can be deployed across many systems. The benefits of a distributed system include increased scalability and redundancy. It is reliable because its architecture and components are designed to prevent data loss. It is highly-available because it uses redundancy to limit downtime.

- Apache Sqoop is a collection of related tools. The primary tools are the import and export tools. Sqoop makes it easier to transfer data between a relational database, data warehouse and Hadoop.

- Apache Kafka is a fast, scalable, durable, fault-tolerant publish-subscribe messaging system. Kafka is often use din place of traditional message brokers like Java Messaging Service (JMS) or Advance Message Queueing Protocol (AMQP).

- Apache Atlas provides governance services that enable enterprises to meet compliance requirements within Hadoop and enables integration with the complete enterprise data ecosystem.

### Security Frameworks

There are a number of different security frameworks within Hadoop:

- HDFS provides security through access control lists, directory permissions and transparent data encryption.

- YARN includes access control lists and control access to cluster memory, CPU resources along with YARN administrative capabilities.

- Hive can be configured to control access to table rows and columns.

- Falcon is a data governance tool that also includes access controls that limit who may submit workflow jobs on a Hadoop cluster.

- Apache Knox is the perimeter gateway protecting a Hadoop cluster. It provides a single point of authentication into a Hadoop cluster.

- Apache Ranger is a centralized security framework offering fine-grained policy controls for HDFS, Hive, KBase, Knox, Storm, Kafka and Solr. Using the ranger console, security administrators can easily manage policies for access to files, directories, databases, tables and columns. These policies can be set for individual users or groups within Hadoop.

### Hortonworks Data Platform (HDP)

HDP (HortonWorks Data Platform) is an open enterprise version of Hadoop distributed by Hortonworks. It includes a single installation utility that installs many of the Apache Hadoop software frameworks. Even the installer is pure Hadoop.

The main benefit to using the HDP distribution is that HortonWorks has tested the distribution thoroughly.

### An example Hadoop cluster

```
  Need hadoop cluster diagram
```

This particular Hadoop cluster is made up of four master nodes, six worker nodes and two utility nodes. The cluster is running various services, like YARN and HDFS. Each node in the cluster can run one or more services.

Master Nodes: the four master nodes are running typical master node components: NameNode, ZooKeeper, MapReduce History Server, Resource Manager, ZooKeeper, Oozie, YARN Timeline Server, Falcon Server, WebHCat, Hive, etc.

Worker Nodes: The worker nodes run worker node services, such as the NodeManager (part of YARN) and the DataNode is a HDFS Component.

Utility Nodes: The utility nodes are running redunant Knox 

Cluster Services:
