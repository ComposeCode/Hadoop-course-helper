# Hadoop Course Helper - Managing Hadoop Services

The core of the current Hadoop version consists primarily of HDFS and YARN, although MapReduce has historically been an important service within Hadoop. As a result, the core cluster configuration files define the configuration settings for HDFS, YARN and MapReduce.

- These core services are primarily configured using files installed by Ambari in the /etc/hadoop/conf directory.

Some of the important configuration files:

- core-site.xml (Hadoop Configuration XML): Hadoop core configuration settings that can be used by HDFS, YARN, MapReduce and others.
- hdfs-site.xml (Hadoop Configuration XML): HDFS Configuration Settings (NameNode and DataNode)
- yarn-site.xml (Hadoop Configuration XML): YARN configuration settings
- mapred-site.xml (Hadoop Configuration XML): MapReduce Configuration settings
- hadoop-env.sh (Hadoop Configuration XML): Bash Script (Environment Variables used by various hadoop scripts and programs)
- log4j.properties (Java Properties):  System log file configuration settings
- hadoop-metrics2.properties (Java Properties): Metrics publishing configuration settings

The core configuration files also define what should be recorded to log files and how to process these log files. Many Hadoop frameworks, including the core frameworks, implement Apache Log4j for their logging system.

## Configuration Precedence

```
  Need diagram of configuration Precedence
```

- A configuration for a cluster is derived from a combination of sources. These sources include the default configuration, the per cluster or per node configuration and the per job configuration.

- Hadoop software is installed with a set of default configuration settings. These settings are defined in various .xml files (usually named *-default.xml). These files are embedded in various JAR files and are the same for any installation of the same version of Hadoop. These default configuration settings are not changed.

- Each Hadoop installation includes a set of per-cluster configuration files that commonly include the word site in their file names. For example, there is a core-site.xml, an hdfs-site.xml and others. The per-cluster configuration inherits configuration property settings from the default configuration. For example, any property that is set in the default configuration is used on the cluster even if that property is not found in the per-cluster configuration.

- The per-cluster configuration can also extend the default configuration by adding additional configuration properties. The per-cluster configuration setting may also override a default configuration setting. Ambari, either during installation or any time after installation, can be used to modify these files to customize the configuration properties of a specific cluster instance.

- Some configuration property settings are based on the hardware configuration of master and worker nodes. For example, if all the work nodes share a common hardware specification, then the same *-site.xml files could be used across the entire cluster. However, if there are two groups of worker nodes with different hardware specifications, then you would need two sets of the *-site.xml files, one for each group of worker nodes. Ambari can manage this setting for you using a feature named Configuration groups.

Finally, each job can be submitted with options requesting one or more specific configuration settings. These requests override the per-cluster and default configuration settings. For example, the user submitting a job could use the -D option to set a specific configuration property.

## Final Properties

- Final properties cannot be overridden by user applications.

- User applications may specify their own configuration settings when they are submitted to a cluster. In some cases, a user could choose a configuration setting that unfairly consumes a resource and negatively effects the performance of other use applications.

- To prevent this, an administrator can declare a comfiguration property value as final. This prevents any user application from overriding a property's value. The Ambari web UI or a command line editor can be used to make a property settings final.

## Other framework configuration files

- Other Hadoop frameworks also use files to define their configuration settings. They commonly use configuration files that have similar formats and naming conventions as those used for thecore frameworks like HDFS or YARN.

- The Hadoop config files are found in /etc/hadoop/conf but for individual services, they are found in directories for specific services, I.E /etc/hive/conf or /etc/pig/conf etc.

## Configuration Management Options

```
  Need table of configuration management options
```

- There are several available options for configuration management. Hortonworks recommends using either the Ambari Web UI or Ambari REST API.

- The Ambari Web UI can be used to automate configuration tasks of Hadoop clusters.  

- When configuration files are modified ambari ensures that these config files are automatically updated on the appropriate cluster nodes.

- After configuration files have been changed, Ambari can also be used to restart the services.

- REST API calls offer the same functionality as the various UI components of HDP. The difference is that the REST APIs enable the integration of Hadoop with other web based management platforms. The REST APIS enable an organization to develop their own management interface.

- An administrator may also manually edit a configuration file, transfer the modified file to the appropriate cluster nodes and then manually restart the affected service or service components. While this does provide very low-level control, it is also a slower, more error prone method of configuration method.

- If using Ambari, it is not recommended to use other management methods as it will result in split-brain management issues (contention). If an administrator manually edits a configuration file and restarts services or service components, these changes are not reflected in the Ambari database. The Ambari database will overwrite the configuration text file with the information contained in its database.

- Many of the Apache frameworks include their own command-line management interfaces. The command line utilities can be used to change a service or service components configuration. These utilities can be added to scripts to automate tasks, and these scripts do not depend on the availability of a graphic user environment. In an Ambari-managed cluster it is recommended to exclusively use Ambari.

### Ambari Web UI Service Management Overview

```
  - Need walk through of different UI components
```

- Configuration change history is stored in /var/log/ambari-server/ambari-config-changes.log

-
