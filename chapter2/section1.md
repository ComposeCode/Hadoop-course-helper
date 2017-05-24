# Chapter 2, Section 1: Managing Ambari Users and Groups

- Ambari users are defiend in the Ambari database. Ambari users may also be imported from an LDAP/AD database. User privileges are defined in Ambari and limit what a user can do within the tool.

- Hadoop users can be defined in an LDAP/AD database or in the Linux /etc/passwd (using tools like useradd). Hadoop users may use Hadoop cluster applications. What any specific Hadoop user can do in a cluster depends on their Hadoop permissions. Hadoop permissions are defined in a variety of places. For example, the hadoop distributed file system has permissions, Apache Hive defines permissions, apache knox defines permissions etc.

- LDAP/AD users can be imported into Ambari and also used by Linux. For this reason an LDAP/AD user might be able to use both Ambari and various Hadoop custer applicaitons. Which actions a user can perform depends on their Ambari and Hadoop permissions.

## Hadoop Service Users

- Each Hadoop service is run under the ownership of a corresponding Linux account. These accounts are known as service users. Service users are given special privileges for accessing and managing their servce. For example, in another lesson you will see how the HDFS command hdfs fsck / fails if they run this command as any other user instead of the hdfs user.

- In addition, there is a special service user for runing smoke tests on components following installation. Smoke tests validate proper service operation. Smoke tests are also available on demand using the run service check from the service actions menu in the ambari web UI.

- Service accounts can be checked inside the Ambari Web UI by selecting Service Accounts from the admin menu button. Service accounts also appear in the operating system files. For example, service acocunts appear in the Linux /etc/passwd file.

## Ambari Users and Groups

```
   - Need Ambari users and groups diagram
```

- Ambari supports two types of users and groups: Local and LDAP/AD. To access LDAP/AD users and groups, the Ambari server must be configured to communicate with an LDAP server or an Active Directory domain.

- Local groups and users are created, managed and deleted by Ambari Administrators and maintained in the Ambari database. LDAP/AD users and groups are created, managaed and deleted by LDAP or active directory tools and maintained in an LDAP/AD directory database. LDAP/AD users and groups have only basic account and group membership information stored in the Ambari database. This information is transferred from LDAP/AD when an administrator runs an import and synchronization command.

- Local users authenticate to Ambari during login. LDAP/AD users authenticate to an LDAP or Active Directory server during log in.

- An Ambari administrator assigns ambari permissions to users and groups. These permissions determine user and group Ambari privileges. Ambari privileges determine what a user or group is allowed to see or do when using Ambari.

### Ambari User and Group Permissions

```
  Need user and group permissions table
```
-

- Ambari features four levels of user and group permissions. They are no permission, read-only permission, operator permission and admin permission. These permissions determine how a user can use Ambari to interact with Hadoop services and configurations. Services are sich things as HDFS, YARN, Hive and so on.  Services for example, can be stopped and started. Configurations affect running services and the cluster topology.

- The default for newly created Ambari users and groups is no permissions. Thes eusers may log in to Ambari but cannot see any service or cluster informaiton or perform any actions.

- Users or groups with read only permission may log in to Ambari and view, but not modify service and configuration information.

- Those users and groups with OPerator permission may log in to Ambari and view service and configuration information. They may also start, restart and stop existing services as well as a new services. They amay also modify current configurations or revert to previous configurations.

- Ambari users with admin permission may do anything. They may log in, view information and manage services and configurations. In addition, they may also create new uers and groups, manage group membership and assign permisisons to users and groups. They may even create other ambari users with admin permissions. By default during installation, an Ambari admin user account is created and assigned Admin permission.

- In addition to the four permission types, users and groups may be assigned access to one or more Ambari views. An ambari view is an optional, custom 'plug-in' tool added to the Ambari Web UI and designed to perform one or more specific tasks.

```
  Need diagram of Ambari admin privileges
```

- As an Ambari user with admin permission, you can create new local users, delete local users change local user passwords and edit user settings. You can also control certain privileges for local and LDAP/AD users. However, may user and gorup management functions are not acailable to an Ambari administrator for LDAP/AD users and groups.

- This s because you need an LDAP/AD user or group management tool to manage LDAP/AD users and groups. Ambari can import these users and groups can assign them Ambari permissions, but Ambari cannot administer the user and groups themselves.

- The table shown here lists the privileges available as well as those not available to an ambari administrator user.

### Managing Users, Groups and Permissions

```
  Need steps + screenshots for creating/modifying users in Ambari web GUI
  - and groups 
```
