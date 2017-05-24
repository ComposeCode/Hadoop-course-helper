# Chapter 1, Section 3: Ambari

### Management with Ambari

```
  Need an Ambari screenshot or other info.
```

Ambari is the primary management interface in today's Hadoop cluster. Ambari provides a single control point with many important features:

- Enables interactive, wizard-driven installation of Hadop across any number of hosts. Ambari automatically chooses how to distribute Hadoop services across cluster nodes but those choices can be user-modified prior to software installation.

- Provides a non-interactive, API-drive installation of Hadoop using Ambari Blueprints. Ambari Blueprints enables an administrator to create installation configuration templates that are executed by Ambari. Thse templates provide an administrator control over the installation process and result in consistent installation across multiple clusters.

- Enables granular control of Hadoop service startup and shutdown. Ambari can start up and shut down individual services, groups of services or all services. Ambari makes changes to service states in the proper sequence when multiple services are selected.

- Provides an administrator with an easy interface to view and update Hadoop service configurations. Once changes are made, Ambari edits the underlying Hadoop configuration files. Ambari also tracks configuration file versions in its databas.e When adding, deleting or modifying service parameters, the service configuraiton windows in the web-based interface provide on-screen help information. Ambari also alerts an administrator when a service must be restart to effect a change.

- Offers a web-based interface that includes a dashboard window that enables simplified monitoring of cluster services. Automated service alerts are available in the interface and can also beemailed or sent by SNMP traps to a configurable list of recipients.

- Features advanced Web-based job diagnostics and heat maps to help simplify troubleshooting issues. Heat maps are a visualization tool that graphically depicts resource usage within a Hadoop cluster. This is useful when looking for areas of resource contention.

- Includes RESTful APIS for customization and integration with enterprise systems such as Microsoft System Center and Teradata Viewpoint.

- Includes Ambari Views which offer a systematic way to plug-in Web UI capabilities to enable custom visualization, management and monitoring tools.

### Apache Ambari

```
  Need architecture diagram of Ambari
```

- The Ambari server serves as the collection point for data from across the cluster. The Ambari server is accesssible through a REST API. The Ambari server relis on a database that maintains cluster topology and configuration information.

- Each cluster node has a copy of the Ambari Agent that is either installed autoamtically by the installation wizard or instlled manually by the administrator. The ambari agent enables the ambari server to monitor and control each cluster node.

- The Ambari Web UI is a client-side JavaScript application, which access the Ambari Server through the REST API. It is served on port 8080. Access to Ambari is username and password controlled. Ambari also features administrator and non-administrator permissions.

- Using Ambari views, custom web-based tools can be plugged into Ambari web. Several view plugins come with HDP, with more being added to new versions of the software.

### Ambari Server Architecture

```
  Need architecture of Apache Ambari application
```

- The Ambari server is written in Jaa. The Ambari Server features a REST API interface, an orchestration function, metrics monitoring, alerts function and an authentication provider function.

- The REST API is used by the Web UI and any other program or utility that can issue REST API commands. The Ambari Web UI is written in JavaScript.

- Starting with Ambari 2.0, the Ambari server incldues built-in metrics monitoring and alerting functions. These enable an administrator to monitor and troubleshoot cluster issues. These functions remove the dependencies on Ganglia and Nagios that were necessary in earlier versions of Hadoop.

- A metric monitor is installed on each cluster node. It collects information and sens it to a standalone metrics collector machine. The metrics collector stores data on disk and forwards current metric data to the Ambari Server. The Ambari Server enables metric information to be displayed in the Ambari Web UI.

- The Authentication provider function enables Ambari Server to access user and group information from multiple sources. By default, Ambari Server maintains user and group information in its own database. Users logging into Ambari would authenticate to the Ambari Server. However, an administrator may configure Ambari Server to access user and group information from LDAP or Active Directory. In this case, users logging in to Ambari would authenticate to either LDAP or Active Directory.

- The Ambari database maintains cluster configuration and topology information, along with user and group information. By default, Ambari uses an internal Derby Database. Ambari may be configured to use an external Oracle, MySQL or PostgreSQL database.

### The Ambari Web UI & Ambari Views

The main interface for managing hadoop clusters is the Ambari Web UI.

```
  Ambari View diagram
```

Ambari Views are web applications that can be plugged into Ambari. The development and use of Views enables an dorganization to extend and customize the Ambari Web UI to meet specific needs.

Just like a typical web application, a view can include server-side resources and client-side assets. Server side resources, which are written in Java and someitmes referred to as providers, can integrate with external systems -- such as cluster services and expose REST end-points that are used by the View. Client-side assets, such as HTML/JavaScript/CSS provide the user interface for the view that is refnered in the Ambari Web UI.

Administrators deploy a view package to the Ambari server, which enables them to subsequently create specific View instances. A view instance acts like a new web applicaiton running inside the Ambari Web UI. Users must be given access to a View instance by an administrator.


### Views Framework

The views framework is separate from views themselves. The views framework is a core feature of Ambari and specific views build on that Framework. The framework exists to enable the development, deployment, creation and management of Views.
Developers use the views framework to develop new views. Developers create a view package that includes any server and client-side software components along with any optional APIs.
