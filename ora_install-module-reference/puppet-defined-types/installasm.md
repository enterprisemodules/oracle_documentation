# ora\_install::installasm

## Overview

Installs and configures Oracle grid.

## Supported versions

This defined class supports the following versions of grid:
- 11.2.0.4
- 12.1.0.1
- 12.1.0.2
- 12.2.0.1
- 18.0.0.0
- 19.0.0.0

## Example

Here is an example on how to use this:

```puppet
ora_install::installasm{ 'db_linux-x64':
  version                   => hiera('db_version'),
  file                      => hiera('asm_file'),
  grid_type                 => 'HA_CONFIG',
  grid_base                 => hiera('grid_base_dir'),
  grid_home                 => hiera('grid_home_dir'),
  ora_inventory_dir         => hiera('oraInventory_dir'),
  user_base_dir             => '/home',
  user                      => hiera('grid_os_user'),
  group                     => 'asmdba',
  group_install             => 'oinstall',
  group_oper                => 'asmoper',
  group_asm                 => 'asmadmin',
  sys_asm_password          => 'Welcome01',
  asm_monitor_password      => 'Welcome01',
  asm_diskgroup             => 'DATA',
  disk_discovery_string     => "/nfs_client/asm*",
  disks                     => "/nfs_client/asm_sda_nfs_b1,/nfs_client/asm_sda_nfs_b2",
  # disk_discovery_string   => "ORCL:*",
  # disks                   => "ORCL:DISK1,ORCL:DISK2",
  disk_redundancy           => "EXTERNAL",
  download_dir              => hiera('oracle_download_dir'),
  remote_file               => false,
  puppet_download_mnt_point => hiera('oracle_source'),
}
```




## Attributes



Attribute Name                                                             | Short Description                                                                       |
-------------------------------------------------------------------------- | --------------------------------------------------------------------------------------- |
[asm_diskgroup](#installasm_asm_diskgroup)                                 | The name of the ASM diskgroup to use.                                                   |
[asm_monitor_password](#installasm_asm_monitor_password)                   | The password for the ASMSNMP user for monitoring in EM.                                 |
[bash_additions](#installasm_bash_additions)                               | The text to add at the end of the bash_profile.                                         |
[bash_profile](#installasm_bash_profile)                                   | Create a bash profile for the specified user or not.                                    |
[cluster_name](#installasm_cluster_name)                                   | The name of the cluster.                                                                |
[cluster_nodes](#installasm_cluster_nodes)                                 | The names of the nodes in the RAC cluster.                                              |
[configure_afd](#installasm_configure_afd)                                 | Specify whether or not to configure ASM Filter Driver instead of ASMLib.                |
[disk_au_size](#installasm_disk_au_size)                                   | The disk_au size to use for the ASM disks.                                              |
[disk_discovery_string](#installasm_disk_discovery_string)                 | The search string to use for discovering disks for ASM.                                 |
[disk_redundancy](#installasm_disk_redundancy)                             | The type of redundancy to use.                                                          |
[disks](#installasm_disks)                                                 | List of disks to create a ASM DiskGroup.                                                |
[disks_failgroup_names](#installasm_disks_failgroup_names)                 | A comma seperated list of device and failure group name.                                |
[download_dir](#installasm_download_dir)                                   | The directory where the Puppet software puts all downloaded files.                      |
[file](#installasm_file)                                                   | The source file to use.                                                                 |
[gimr_configure](#installasm_gimr_configure)                               | Specify whether or not to configure GIMR database (MGMTDB), 19c and higher only.        |
[gimr_dg_ausize](#installasm_gimr_dg_ausize)                               | The disk_au size to use for the for the GIMR database (MGMTDB) diskgroup.               |
[gimr_dg_disks](#installasm_gimr_dg_disks)                                 | List of disks to create the GIMR database (MGMTDB).                                     |
[gimr_dg_disks_failgroup_names](#installasm_gimr_dg_disks_failgroup_names) | A comma seperated list of device and failure group name for the GIMR database (MGMTDB). |
[gimr_dg_fg_names](#installasm_gimr_dg_fg_names)                           | Failure Groups for the GIMR storage data ASM disk group.                                |
[gimr_dg_name](#installasm_gimr_dg_name)                                   | Specify the name of the diskgroup for the GIMR database (MGMTDB), 12.2 and up only.     |
[gimr_dg_redundancy](#installasm_gimr_dg_redundancy)                       | The type of redundancy to use for the GIMR database (MGMTDB) diskgroup.                 |
[grid_base](#installasm_grid_base)                                         | The directory to use as grid base.                                                      |
[grid_home](#installasm_grid_home)                                         | The directory to use as grid home.                                                      |
[grid_type](#installasm_grid_type)                                         | The type of grid.                                                                       |
[group](#installasm_group)                                                 | The os group to use for these Oracle puppet definitions.                                |
[group_asm](#installasm_group_asm)                                         | The OS group to use.                                                                    |
[group_install](#installasm_group_install)                                 | The os group to use for installation.                                                   |
[group_oper](#installasm_group_oper)                                       | The OS group to allow ASM oper operations.                                              |
[logoutput](#installasm_logoutput)                                         | log the outputs of Puppet exec or not.                                                  |
[network_interface_list](#installasm_network_interface_list)               | The list of interfaces to use for RAC.                                                  |
[ora_inventory_dir](#installasm_ora_inventory_dir)                         | The directory that contains the oracle inventory.                                       |
[puppet_download_mnt_point](#installasm_puppet_download_mnt_point)         | The base path of all remote files for the defined type or class.                        |
[remote_file](#installasm_remote_file)                                     | This parameter is not being used anymore and will be removed in a future release.       |
[scan_name](#installasm_scan_name)                                         | The name to use for the SCAN service.                                                   |
[scan_port](#installasm_scan_port)                                         | The IP portnumber to use for the SCAN service.                                          |
[stand_alone](#installasm_stand_alone)                                     | Configuring Grid Infrastructure for a Stand-Alone Server.                               |
[storage_option](#installasm_storage_option)                               | The type of storage to use.                                                             |
[sys_asm_password](#installasm_sys_asm_password)                           | The password to use for the SYSASM user.                                                |
[temp_dir](#installasm_temp_dir)                                           | Directory to use for temporary files.                                                   |
[user](#installasm_user)                                                   | The user used for the specified installation.                                           |
[user_base_dir](#installasm_user_base_dir)                                 | The directory to use as base directory for the users.                                   |
[version](#installasm_version)                                             | The version that is installed in the used Oracle home.                                  |
[zip_extract](#installasm_zip_extract)                                     | The specified source file is a zip file that needs te be extracted.                     |




### asm_diskgroup<a name='installasm_asm_diskgroup'>

The name of the ASM diskgroup to use.

`DATA`

Type: `String[1]`

Default:`'DATA'`

[Back to overview of installasm](#attributes)

### asm_monitor_password<a name='installasm_asm_monitor_password'>

The password for the ASMSNMP user for monitoring in EM.

Type: `Easy_type::Password`


[Back to overview of installasm](#attributes)

### cluster_name<a name='installasm_cluster_name'>

The name of the cluster.

Type: `Optional[String[1]]`

Default:`undef`

[Back to overview of installasm](#attributes)

### cluster_nodes<a name='installasm_cluster_nodes'>

The names of the nodes in the RAC cluster.

Valid values are:

- `node1:node1-vip,node2:node2-vip`                     (version >= 11 <= 12.1)
- `node1:node1-vip:HUB,node2:node2-vip:LEAF`            (version >= 12.1 Flex Cluster)
- `node1,node2`                                         (version = 12.2 Application Cluster)
- `node1:node1-vip:HUB:site1,node2:node2-vip:HUB:site2` (version = 12.2 Extended Cluster)

Type: `Optional[String[1]]`

Default:`undef`

[Back to overview of installasm](#attributes)

### configure_afd<a name='installasm_configure_afd'>

Specify whether or not to configure ASM Filter Driver instead of ASMLib.

The default value is: `false`

Type: `Optional[Boolean]`

Default:`false`

[Back to overview of installasm](#attributes)

### disk_au_size<a name='installasm_disk_au_size'>

The disk_au size to use for the ASM disks.
**Attention** this is a String value not an Integer.

The default value is: `1`

Type: `Enum['1','2','4','8','16','32','64']`

Default:`'1'`

[Back to overview of installasm](#attributes)

### disk_discovery_string<a name='installasm_disk_discovery_string'>

The search string to use for discovering disks for ASM.

Type: `Optional[String[1]]`

Default:`undef`

[Back to overview of installasm](#attributes)

### disk_redundancy<a name='installasm_disk_redundancy'>

The type of redundancy to use.

Valid values are:
- `NORMAL`
- `HIGH`
- `EXTERNAL`

The default value is: `NORMAL`

Type: `Enum['NORMAL','HIGH','EXTERNAL']`

Default:`'NORMAL'`

[Back to overview of installasm](#attributes)

### disks_failgroup_names<a name='installasm_disks_failgroup_names'>

A comma seperated list of device and failure group name.

Valid values are:

- `/dev/sdb,CRSFG1,/dev/sdc,CRSFG2,/dev/sdd,CRSFG3`                                 (NORMAL redundancy)
- `/dev/sdb,,/dev/sdc,,/dev/sdd,,/dev/sde,`                                         (EXTERNAL redundancy)
- `/dev/sdb,CRSFG1,/dev/sdc,CRSFG2,/dev/sdd,CRSFG3,/dev/sde,CRSFG4,/dev/sdf,CRSFG5` (HIGH redundancy)

Type: `Optional[String[1]]`

Default:`undef`

[Back to overview of installasm](#attributes)

### bash_profile<a name='installasm_bash_profile'>

Create a bash profile for the specified user or not.

Valid values are `true` and `false`.

When you specify a `true` for the parameter, Puppet will create a standard bash profile for the specified user. The bash profile will be placed in a directory named `user_base_dir/user`.

```puppet
ora_install::client { 'Oracle client':
  ...
  bash_profile  => true,
  user          => 'oracle',
  user_base_dir => '/home',
  ...
}
```

This snippet will create a bash profile called `/home/oracle/.bash_profile`.

Type: `Boolean`

Default:`true`

[Back to overview of installasm](#attributes)

### bash_additions<a name='installasm_bash_additions'>

The text to add at the end of the bash_profile. This parameter will only be used when you have specified `true` for the parameter `bash_profile`

The default value is an empty string.

Type: `String`

Default:`''`

[Back to overview of installasm](#attributes)

### disks<a name='installasm_disks'>

List of disks to create a ASM DiskGroup.

Type: `Optional[String[1]]`

Default:`undef`

[Back to overview of installasm](#attributes)

### download_dir<a name='installasm_download_dir'>

The directory where the Puppet software puts all downloaded files.

Before Puppet can actually use remote files, they must be downloaded first. Puppet uses this directory to put all files in.

The default value is: `/install`

Type: `Stdlib::Absolutepath`

Default:`'/install'`

[Back to overview of installasm](#attributes)

### file<a name='installasm_file'>

The source file to use.

Type: `String[1]`

Default:`undef`

[Back to overview of installasm](#attributes)

### gimr_configure<a name='installasm_gimr_configure'>

Specify whether or not to configure GIMR database (MGMTDB), 19c and higher only.

The default value is: `false`

Type: `Optional[Boolean]`

Default:`false`

[Back to overview of installasm](#attributes)

### gimr_dg_ausize<a name='installasm_gimr_dg_ausize'>

The disk_au size to use for the for the GIMR database (MGMTDB) diskgroup.
**Attention** this is a String value not an Integer.

The default value is: `1`

Type: `Optional[Enum['1','2','4','8','16','32','64']]`

Default:`'1'`

[Back to overview of installasm](#attributes)

### gimr_dg_disks<a name='installasm_gimr_dg_disks'>

List of disks to create the GIMR database (MGMTDB).

Type: `Optional[String[1]]`

Default:`undef`

[Back to overview of installasm](#attributes)

### gimr_dg_disks_failgroup_names<a name='installasm_gimr_dg_disks_failgroup_names'>

A comma seperated list of device and failure group name for the GIMR database (MGMTDB).

Valid values are:

- `/dev/sdb,GIMRFG1,/dev/sdc,GIMRFG2,/dev/sdd,GIMRFG3`                                   (NORMAL redundancy)
- `/dev/sdb,,/dev/sdc,,/dev/sdd,,/dev/sde,`                                              (EXTERNAL redundancy)
- `/dev/sdb,GIMRFG1,/dev/sdc,GIMRFG2,/dev/sdd,GIMRFG3,/dev/sde,GIMRFG4,/dev/sdf,GIMRFG5` (HIGH redundancy)

Type: `Optional[String[1]]`

Default:`undef`

[Back to overview of installasm](#attributes)

### gimr_dg_fg_names<a name='installasm_gimr_dg_fg_names'>

Failure Groups for the GIMR storage data ASM disk group.

Type: `Optional[String[1]]`

Default:`undef`

[Back to overview of installasm](#attributes)

### gimr_dg_name<a name='installasm_gimr_dg_name'>

Specify the name of the diskgroup for the GIMR database (MGMTDB), 12.2 and up only.

Type: `Optional[String[1]]`

Default:`undef`

[Back to overview of installasm](#attributes)

### gimr_dg_redundancy<a name='installasm_gimr_dg_redundancy'>

The type of redundancy to use for the GIMR database (MGMTDB) diskgroup.

Valid values are:
- `NORMAL`
- `HIGH`
- `EXTERNAL`

Type: `Optional[Enum['NORMAL','HIGH','EXTERNAL']]`

Default:`undef`

[Back to overview of installasm](#attributes)

### grid_base<a name='installasm_grid_base'>

The directory to use as grid base.

Type: `Stdlib::Absolutepath`

Default:`undef`

[Back to overview of installasm](#attributes)

### grid_home<a name='installasm_grid_home'>

The directory to use as grid home.

Type: `Stdlib::Absolutepath`

Default:`undef`

[Back to overview of installasm](#attributes)

### grid_type<a name='installasm_grid_type'>

The type of grid.

Valid values are:
- `HA_CONFIG`
- `CRS_CONFIG`
- `HA_SWONLY`   (versions > 11)
- `UPGRADE`
- `CRS_SWONLY`

The default value is: `HA_CONFIG`

Type: `Enum['CRS_CONFIG','HA_CONFIG','UPGRADE','CRS_SWONLY','HA_SWONLY']`

Default:`'HA_CONFIG'`

[Back to overview of installasm](#attributes)

### group<a name='installasm_group'>

The os group to use for these Oracle puppet definitions.

The default value is: `dba`

Type: `String[1]`

Default:`'asmdba'`

[Back to overview of installasm](#attributes)

### group_asm<a name='installasm_group_asm'>

The OS group to use.

The default value is: `asmdba`

Type: `String[1]`

Default:`'asmadmin'`

[Back to overview of installasm](#attributes)

### group_install<a name='installasm_group_install'>

The os group to use for installation.

The default value is: `oinstall`

Type: `String[1]`

Default:`'oinstall'`

[Back to overview of installasm](#attributes)

### group_oper<a name='installasm_group_oper'>

The OS group to allow ASM oper operations.

The default value is: `asmoper`

Type: `String[1]`

Default:`'asmoper'`

[Back to overview of installasm](#attributes)

### logoutput<a name='installasm_logoutput'>

log the outputs of Puppet exec or not.

When you specify `true` Puppet will log all output of `exec` types.

Valid values are:

- `true`
- `false`
- `on_failure`

Type: `Variant[Boolean,Enum['on_failure']]`

Default:`lookup({name => 'logoutput', default_value => 'on_failure'})`

[Back to overview of installasm](#attributes)

### network_interface_list<a name='installasm_network_interface_list'>

The list of interfaces to use for RAC.

The value should be a comma separated strings where each string is as shown below

```
InterfaceName:SubnetAddress:InterfaceType
```

where InterfaceType can be either "1", "2", or "3" (1 indicates public, 2 indicates private, and 3 indicates the interface is not used)

An example on how to use this:

```puppet
installasm{'asm12':
  ...
  network_interface_list => 'eth0:140.87.24.0:1,eth1:10.2.1.0:2,eth2:140.87.52.0:3'
  ...
}
```

Type: `Optional[String[1]]`

Default:`undef`

[Back to overview of installasm](#attributes)

### ora_inventory_dir<a name='installasm_ora_inventory_dir'>

The directory that contains the oracle inventory.

The default value is: `/oracle_base/oraInventory`

Type: `Optional[Stdlib::Absolutepath]`

Default:`undef`

[Back to overview of installasm](#attributes)

### puppet_download_mnt_point<a name='installasm_puppet_download_mnt_point'>

The base path of all remote files for the defined type or class.

The default value is: `puppet:///modules/ora_install`

Type: `Optional[String[1]]`

Default:`undef`

[Back to overview of installasm](#attributes)

### remote_file<a name='installasm_remote_file'>

**DEPRECATED**
This parameter is not being used anymore and will be removed in a future release.

`true`.

Type: `Optional[Boolean]`

Default:`undef`

[Back to overview of installasm](#attributes)

### scan_name<a name='installasm_scan_name'>

The name to use for the SCAN service.

Type: `Optional[String[1]]`

Default:`undef`

[Back to overview of installasm](#attributes)

### scan_port<a name='installasm_scan_port'>

The IP portnumber to use for the SCAN service.

Type: `Optional[Integer]`

Default:`undef`

[Back to overview of installasm](#attributes)

### stand_alone<a name='installasm_stand_alone'>

Configuring Grid Infrastructure for a Stand-Alone Server.

The default value is: `true`

Type: `Boolean`

Default:`true`

[Back to overview of installasm](#attributes)

### storage_option<a name='installasm_storage_option'>

The type of storage to use.

Valid values are:
- `ASM_STORAGE`          (versions = 11)
- `FILE_SYSTEM_STORAGE`  (versions <= 12.1)
- `LOCAL_ASM_STORAGE`    (versions >= 12.1)
- `CLIENT_ASM_STORAGE`   (versions >= 12.2)
- `FLEX_ASM_STORAGE`     (versions >= 12.1)

Type: `Optional[Enum['FLEX_ASM_STORAGE','CLIENT_ASM_STORAGE','LOCAL_ASM_STORAGE','FILE_SYSTEM_STORAGE','ASM_STORAGE']]`

Default:`undef`

[Back to overview of installasm](#attributes)

### sys_asm_password<a name='installasm_sys_asm_password'>

The password to use for the SYSASM user.

Type: `Easy_type::Password`


[Back to overview of installasm](#attributes)

### temp_dir<a name='installasm_temp_dir'>

Directory to use for temporary files.

Type: `Stdlib::Absolutepath`

Default:`'/tmp'`

[Back to overview of installasm](#attributes)

### user<a name='installasm_user'>

The user used for the specified installation.
The install class will not create the user for you. You must do that yourself.

The default value is: `oracle`

Type: `String[1]`

Default:`'grid'`

[Back to overview of installasm](#attributes)

### user_base_dir<a name='installasm_user_base_dir'>

The directory to use as base directory for the users.

Type: `Stdlib::Absolutepath`

Default:`'/home'`

[Back to overview of installasm](#attributes)

### version<a name='installasm_version'>

The version that is installed in the used Oracle home.

Puppet uses this value to decide on version specific actions.

Type: `Ora_install::Version`

Default:`undef`

[Back to overview of installasm](#attributes)

### zip_extract<a name='installasm_zip_extract'>

The specified source file is a zip file that needs te be extracted.
When you specify a value of false, the source attribute must contain a reference to a directory instead of a zip file.

The default value is: `true`

Type: `Boolean`

Default:`true`

[Back to overview of installasm](#attributes)
