# ora\_install::goldengate

## Overview

Installs the Oracle goldengate software.

## Supported versions

This module supports the following versions:

- 12.1.2
- 12.2.1
- 18.1.0
- 19.1.0

## Example

Here is an example on how to use this:

```puppet
ora_install::goldengate{ 'ggate12.1.2':
  version                  => '12.1.2',
  file                     => '121200_fbo_ggs_Linux_x64_shiphome.zip',
  database_type            => 'Oracle',
  database_version         => 'ORA11g',
  database_home            => '/oracle/product/12.1/db',
  oracle_base              => '/oracle',
  goldengate_home          => "/oracle/product/12.1/ggate",
  manager_port             => 16000,
  user                     => 'ggate',
  group                    => 'dba',
  group_install            => 'oinstall',
  download_dir             => '/install',
  puppet_download_mnt_point => puppet://modules/software,
}
```




## Attributes



Attribute Name                                                     | Short Description                                                  |
------------------------------------------------------------------ | ------------------------------------------------------------------ |
[database_home](#goldengate_database_home)                         | The home directory of the database.                                |
[database_type](#goldengate_database_type)                         | The type of database.                                              |
[database_version](#goldengate_database_version)                   | The version of the database.                                       |
[download_dir](#goldengate_download_dir)                           | The directory where the Puppet software puts all downloaded files. |
[file](#goldengate_file)                                           | The file containing the software.                                  |
[goldengate_home](#goldengate_goldengate_home)                     | The home to use for the goldengate software.                       |
[group](#goldengate_group)                                         | The os group to use for these Oracle puppet definitions.           |
[group_install](#goldengate_group_install)                         | The os group to use for installation.                              |
[logoutput](#goldengate_logoutput)                                 | log the outputs of Puppet exec or not.                             |
[manager_port](#goldengate_manager_port)                           | The IP port number of the manager.                                 |
[oracle_base](#goldengate_oracle_base)                             | A directory to use as Oracle base directory.                       |
[puppet_download_mnt_point](#goldengate_puppet_download_mnt_point) | The base path of all remote files for the defined type or class.   |
[temp_dir](#goldengate_temp_dir)                                   | Directory to use for temporary files.                              |
[user](#goldengate_user)                                           | The user used for the specified installation.                      |
[version](#goldengate_version)                                     | The version that is installed in the used Oracle home.             |




### database_home<a name='goldengate_database_home'>

The home directory of the database.

Type: `Stdlib::Absolutepath`

Default:`undef`

[Back to overview of goldengate](#attributes)

### database_type<a name='goldengate_database_type'>

The type of database.

The default value is: `Oracle`

Type: `Enum['Oracle']`

Default:`'Oracle'`

[Back to overview of goldengate](#attributes)

### database_version<a name='goldengate_database_version'>

The version of the database.

Valid values are:
- `ORA11g`
- `ORA12c`

`ORA11g`

Type: `Enum['ORA11g','ORA12c']`

Default:`'ORA11g'`

[Back to overview of goldengate](#attributes)

### download_dir<a name='goldengate_download_dir'>

The directory where the Puppet software puts all downloaded files.

Before Puppet can actually use remote files, they must be downloaded first. Puppet uses this directory to put all files in.

The default value is: `/install`

Type: `Stdlib::Absolutepath`

Default:`'/install'`

[Back to overview of goldengate](#attributes)

### file<a name='goldengate_file'>

The file containing the software.

Type: `String[1]`

Default:`undef`

[Back to overview of goldengate](#attributes)

### goldengate_home<a name='goldengate_goldengate_home'>

The home to use for the goldengate software.

Type: `Stdlib::Absolutepath`

Default:`undef`

[Back to overview of goldengate](#attributes)

### group<a name='goldengate_group'>

The os group to use for these Oracle puppet definitions.

The default value is: `dba`

Type: `String[1]`

Default:`'dba'`

[Back to overview of goldengate](#attributes)

### group_install<a name='goldengate_group_install'>

The os group to use for installation.

The default value is: `oinstall`

Type: `String[1]`

Default:`'oinstall'`

[Back to overview of goldengate](#attributes)

### logoutput<a name='goldengate_logoutput'>

log the outputs of Puppet exec or not.

When you specify `true` Puppet will log all output of `exec` types.

Valid values are:

- `true`
- `false`
- `on_failure`

Type: `Variant[Boolean,Enum['on_failure']]`

Default:`lookup({name => 'logoutput', default_value => 'on_failure'})`

[Back to overview of goldengate](#attributes)

### manager_port<a name='goldengate_manager_port'>

The IP port number of the manager.

This is a required value.

Type: `Integer`

Default:`undef`

[Back to overview of goldengate](#attributes)

### oracle_base<a name='goldengate_oracle_base'>

A directory to use as Oracle base directory.

Type: `Stdlib::Absolutepath`

Default:`undef`

[Back to overview of goldengate](#attributes)

### puppet_download_mnt_point<a name='goldengate_puppet_download_mnt_point'>

The base path of all remote files for the defined type or class.

The default value is: `puppet:///modules/ora_install`

Type: `Optional[String[1]]`

Default:`undef`

[Back to overview of goldengate](#attributes)

### temp_dir<a name='goldengate_temp_dir'>

Directory to use for temporary files.

Type: `Stdlib::Absolutepath`

Default:`'/tmp'`

[Back to overview of goldengate](#attributes)

### user<a name='goldengate_user'>

The user used for the specified installation.
The install class will not create the user for you. You must do that yourself.

The default value is: `oracle`

Type: `String[1]`

Default:`'ggate'`

[Back to overview of goldengate](#attributes)

### version<a name='goldengate_version'>

The version that is installed in the used Oracle home.

Puppet uses this value to decide on version specific actions.

Type: `Enum['12.1.2','12.2.1', '12.3.0','18.1.0', '19.1.0']`

Default:`'12.3.0'`

[Back to overview of goldengate](#attributes)
