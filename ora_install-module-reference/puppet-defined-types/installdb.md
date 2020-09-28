# ora\_install::installdb

## Overview

You can use this class to install a working oracle database on your system.

## Supported versions

This defined type supports the following versions of Oracle:

- 11.2.0.1
- 11.2.0.3
- 11.2.0.4
- 12.1.0.1
- 12.1.0.2
- 12.2.0.1
- 18.0.0.0
- 19.0.0.0

## Example

Here is an example on how you can use this class to install an Oracle database
on your system.

```puppet
ora_install::installdb{ '12.1.0.2_Linux-x86-64':
  version                   => '12.1.0.2',
  file                      => 'V46095-01',
  database_type             => 'SE',
  oracle_base               => '/oracle',
  oracle_home               => '/oracle/product/12.1/db',
  bash_profile              => true,
  user                      => 'oracle',
  group                     => 'dba',
  group_install             => 'oinstall',
  group_oper                => 'oper',
  download_dir              => '/data/install',
  zip_extract               => true,
  puppet_download_mnt_point => $puppet_download_mnt_point,
}
```




## Attributes



Attribute Name                                                    | Short Description                                                                 |
----------------------------------------------------------------- | --------------------------------------------------------------------------------- |
[bash_additions](#installdb_bash_additions)                       | The text to add at the end of the bash_profile.                                   |
[bash_profile](#installdb_bash_profile)                           | Create a bash profile for the specified user or not.                              |
[cleanup_install_files](#installdb_cleanup_install_files)         | Cleanup extracted files after use.                                                |
[cluster_nodes](#installdb_cluster_nodes)                         | A comma seperated list of the nodes running in the RAC cluster.                   |
[database_type](#installdb_database_type)                         | Selects the type of database you want to install.                                 |
[download_dir](#installdb_download_dir)                           | The directory where the Puppet software puts all downloaded files.                |
[ee_optional_components](#installdb_ee_optional_components)       | This variable is used to enable or disable custom install.                        |
[ee_options_selection](#installdb_ee_options_selection)           | List of Enterprise Edition Options you would like to install.                     |
[file](#installdb_file)                                           | The source file to use.                                                           |
[group](#installdb_group)                                         | The os group to use for these Oracle puppet definitions.                          |
[group_install](#installdb_group_install)                         | The os group to use for installation.                                             |
[group_oper](#installdb_group_oper)                               | The OS group to allow operator rights.                                            |
[is_rack_one_install](#installdb_is_rack_one_install)             | This variable is used to enable or disable RAC One Node install.                  |
[ora_inventory_dir](#installdb_ora_inventory_dir)                 | The directory that contains the oracle inventory.                                 |
[oracle_base](#installdb_oracle_base)                             | A directory to use as Oracle base directory.                                      |
[oracle_home](#installdb_oracle_home)                             | A directory to be used as Oracle home directory for this software.                |
[puppet_download_mnt_point](#installdb_puppet_download_mnt_point) | The base path of all remote files for the defined type or class.                  |
[remote_file](#installdb_remote_file)                             | This parameter is not being used anymore and will be removed in a future release. |
[temp_dir](#installdb_temp_dir)                                   | Directory to use for temporary files.                                             |
[user](#installdb_user)                                           | The user used for the specified installation.                                     |
[user_base_dir](#installdb_user_base_dir)                         | The directory to use as base directory for the users.                             |
[version](#installdb_version)                                     | Specifies the version of the component you want to manage or install.             |
[zip_extract](#installdb_zip_extract)                             | The specified source file is a zip file that needs te be extracted.               |




### database_type<a name='installdb_database_type'>

Selects the type of database you want to install.

At this point in time the following database types are supported and allowed:

- `EE`     : Enterprise Edition   (all versions)
- `SE`     : Standard Edition     (versions <= 12.1.0.1)
- `SEONE`  : Standard Edition One (versions <= 12.1.0.1)
- `SE2`    : Standard Edition Two (versions >= 12.1.0.2)

The default value is: `SE2`

Type: `Enum['SE2', 'SE', 'EE', 'SEONE']`

Default:`'SE2'`

[Back to overview of installdb](#attributes)

### download_dir<a name='installdb_download_dir'>

The directory where the Puppet software puts all downloaded files.

Before Puppet can actually use remote files, they must be downloaded first. Puppet uses this directory to put all files in.

The default value is: `/install`

Type: `Stdlib::Absolutepath`

Default:`'/install'`

[Back to overview of installdb](#attributes)

### bash_profile<a name='installdb_bash_profile'>

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

[Back to overview of installdb](#attributes)

### bash_additions<a name='installdb_bash_additions'>

The text to add at the end of the bash_profile. This parameter will only be used when you have specified `true` for the parameter `bash_profile`

The default value is an empty string.

Type: `String`

Default:`''`

[Back to overview of installdb](#attributes)

### cleanup_install_files<a name='installdb_cleanup_install_files'>

Cleanup extracted files after use.

This is a boolean value. When you set this value to `true`. The installer class will
remove all extracted zip files after it has done its work.

The default value is: `true`

Here is an example:

```puppet
ora_install::....{...
  ...
  cleanup_install_files => false,  # Keep all unzipped files
  ...
}
```

Type: `Boolean`

Default:`true`

[Back to overview of installdb](#attributes)

### cluster_nodes<a name='installdb_cluster_nodes'>

A comma seperated list of the nodes running in the RAC cluster.

Example: `node1,node2`

Type: `Optional[String[1]]`

Default:`undef`

[Back to overview of installdb](#attributes)

### ee_optional_components<a name='installdb_ee_optional_components'>

This variable is used to enable or disable custom install.

When its is set to  true, the attribute `ee_options_selection` is used. When this value is false, the attribute `ee_options_selection` is ignored.

Type: `Optional[String[1]]`

Default:`undef`

[Back to overview of installdb](#attributes)

### ee_options_selection<a name='installdb_ee_options_selection'>

List of Enterprise Edition Options you would like to install.

Check the oracle documentation what values are valid.

Type: `Boolean`

Default:`false`

[Back to overview of installdb](#attributes)

### file<a name='installdb_file'>

The source file to use.

Type: `String[1]`

Default:`undef`

[Back to overview of installdb](#attributes)

### group<a name='installdb_group'>

The os group to use for these Oracle puppet definitions.

The default value is: `dba`

Type: `String[1]`

Default:`'dba'`

[Back to overview of installdb](#attributes)

### group_install<a name='installdb_group_install'>

The os group to use for installation.

The default value is: `oinstall`

Type: `String[1]`

Default:`'oinstall'`

[Back to overview of installdb](#attributes)

### group_oper<a name='installdb_group_oper'>

The OS group to allow operator rights.

The default value is: `oper`

Type: `String[1]`

Default:`'oper'`

[Back to overview of installdb](#attributes)

### is_rack_one_install<a name='installdb_is_rack_one_install'>

This variable is used to enable or disable RAC One Node install.

- true  : Value of RAC One Node service name is used.
- false : Value of RAC One Node service name is not used.

The default value is: `false`

Type: `Boolean`

Default:`false`

[Back to overview of installdb](#attributes)

### ora_inventory_dir<a name='installdb_ora_inventory_dir'>

The directory that contains the oracle inventory.

The default value is: `/oracle_base/oraInventory`

Type: `Optional[Stdlib::Absolutepath]`

Default:`undef`

[Back to overview of installdb](#attributes)

### oracle_base<a name='installdb_oracle_base'>

A directory to use as Oracle base directory.

Type: `Stdlib::Absolutepath`

Default:`undef`

[Back to overview of installdb](#attributes)

### oracle_home<a name='installdb_oracle_home'>

A directory to be used as Oracle home directory for this software.

Type: `Stdlib::Absolutepath`

Default:`undef`

[Back to overview of installdb](#attributes)

### puppet_download_mnt_point<a name='installdb_puppet_download_mnt_point'>

The base path of all remote files for the defined type or class.

The default value is: `puppet:///modules/ora_install`

Type: `Optional[String[1]]`

Default:`undef`

[Back to overview of installdb](#attributes)

### remote_file<a name='installdb_remote_file'>

**DEPRECATED**
This parameter is not being used anymore and will be removed in a future release.

`true`.

Type: `Optional[Boolean]`

Default:`undef`

[Back to overview of installdb](#attributes)

### temp_dir<a name='installdb_temp_dir'>

Directory to use for temporary files.

Type: `Stdlib::Absolutepath`

Default:`'/tmp'`

[Back to overview of installdb](#attributes)

### user<a name='installdb_user'>

The user used for the specified installation.
The install class will not create the user for you. You must do that yourself.

The default value is: `oracle`

Type: `String[1]`

Default:`'oracle'`

[Back to overview of installdb](#attributes)

### user_base_dir<a name='installdb_user_base_dir'>

The directory to use as base directory for the users.

Type: `Stdlib::Absolutepath`

Default:`'/home'`

[Back to overview of installdb](#attributes)

### version<a name='installdb_version'>

Specifies the version of the component you want to manage or install.

At this point in type we support the installation of:

- `11.2.0.1`
- `11.2.0.3`
- `11.2.0.4`
- `12.1.0.1`
- `12.1.0.2`
- `12.2.0.1`
- `18.0.0.0`
- `19.0.0.0`

Here is an example on how to specify the version:

```puppet
ora_install::....{...
  ...
  version => '12.1.0.2',
  ...
}
```

Type: `Ora_install::Version`

Default:`undef`

[Back to overview of installdb](#attributes)

### zip_extract<a name='installdb_zip_extract'>

The specified source file is a zip file that needs te be extracted.
When you specify a value of false, the source attribute must contain a reference to a directory instead of a zip file.

The default value is: `true`

Type: `Boolean`

Default:`true`

[Back to overview of installdb](#attributes)
