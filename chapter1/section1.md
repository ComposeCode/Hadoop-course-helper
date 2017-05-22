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
