# ora\_install::rcu

## Overview

Install the repository for several Oracle Fusion products.

## Creating a repository

Using this defined class, you can create repositories for several Oracle products. Here are some examples.

Here is an example on how to use it:

### SOA suite repository

```puppet
ora_install::rcu{'install_SOA_v11.1.1.9.0':
  rcu_file                  => 'V75907-01.zip',
  product                   => 'soasuite',
  version                   => '11.1.1.9.0',
  oracle_home               => '/u01/app/oracle/product/11.2.0.4/db_home1',
  user                      => 'oracle',
  group                     => 'dba',
  download_dir              => '/install',
  action                    => 'create',
  db_server                 => 'asm112.example.com:1521',
  db_service                => 'DB112.domain.local',
  sys_password              => 'Welcome01',
  schema_prefix             => 'DEV',
  repos_password            => 'Welcome02',
  puppet_download_mnt_point => 'puppet:///modules/software',
}
```

### webcenter repository

```puppet
ora_install::rcu{'install_WebCenter_11.1.1.7':
  rcu_file                  => 'ofm_rcu_linux_11.1.1.7.0_32_disk1_1of1.zip',
  product                   => 'webcenter',
  version                   => '11.1.1.7',
  oracle_home               => '/u01/app/oracle/product/11.2.0.4/db_home1',
  user                      => 'oracle',
  group                     => 'dba',
  download_dir              => '/install',
  action                    => 'create',
  db_server                 => 'asm112.example.com:1521',
  db_service                => 'DB112.domain.local',
  sys_password              => 'Welcome01',
  schema_prefix             => 'DEV',
  temp_tablespace           => 'TEMP',
  repos_password            => 'Welcome02',
  puppet_download_mnt_point => 'puppet:///modules/software',
}
```

### OIM, OAM repository

OIM needs an Oracle Enterprise Edition database

```puppet
ora_install::rcu{'install_OIM_11.1.2.1':
  rcu_file                  => 'V37476-01.zip',
  product                   => 'oim',
  version                   => '11.1.2.1',
  oracle_home               => '/u01/app/oracle/product/11.2.0.4/db_home1',
  user                      => 'oracle',
  group                     => 'dba',
  download_dir              => '/data/install',
  action                    => 'create',
  db_server                 => 'asm112.example.com:1521',
  db_service                => 'DB112.domain.local',
  sys_password              => 'Welcome01',
  schema_prefix             => 'DEV',
  repos_password            => 'Welcome02',
  puppet_download_mnt_point => 'puppet:///modules/software',
  logoutput                 => true,
 }
```

## deleting a repository

You can also use this defined type to delete a repository. To do so, you need te specify `delete` as action.

Here is an example:

```puppet
ora_install::rcu{'delete_SOA_11.1.1.6':
  rcu_file          => 'ofm_rcu_linux_11.1.1.6.0_disk1_1of1.zip',
  product           => 'soasuite',
  version           => '11.1.1.6',
  oracle_home       => '/oracle/product/11.2/db',
  user              => 'oracle',
  group             => 'dba',
  download_dir      => '/install',
  action            => 'delete',
  db_server         => 'asm112.example.com:1521',
  db_service        => 'DB112.domain.local',
  sys_password      => 'Welcome01',
  schema_prefix     => 'DEV',
  repos_password    => 'Welcome02',
}
```




## Attributes



Attribute Name                                              | Short Description                                                                 |
----------------------------------------------------------- | --------------------------------------------------------------------------------- |
[action](#rcu_action)                                       | The action to perform.                                                            |
[db_server](#rcu_db_server)                                 | The name of the database server to use.                                           |
[db_service](#rcu_db_service)                               | The name of the database service to use.                                          |
[download_dir](#rcu_download_dir)                           | The directory where the Puppet software puts all downloaded files.                |
[group](#rcu_group)                                         | The os group to use for these Oracle puppet definitions.                          |
[logoutput](#rcu_logoutput)                                 | log the outputs of Puppet exec or not.                                            |
[oracle_home](#rcu_oracle_home)                             | A directory to be used as Oracle home directory for this software.                |
[product](#rcu_product)                                     | The name of the product for which you want to install the RCU.                    |
[puppet_download_mnt_point](#rcu_puppet_download_mnt_point) | The base path of all remote files for the defined type or class.                  |
[rcu_file](#rcu_rcu_file)                                   | The file containing the RCU definition.                                           |
[remote_file](#rcu_remote_file)                             | This parameter is not being used anymore and will be removed in a future release. |
[repos_password](#rcu_repos_password)                       | The password for the repo user.                                                   |
[schema_prefix](#rcu_schema_prefix)                         | The prefix name to use for the schema.                                            |
[sys_password](#rcu_sys_password)                           | The password of the `SYS` user on the database.                                   |
[sys_user](#rcu_sys_user)                                   | The name of the `SYS` user on the database.                                       |
[temp_tablespace](#rcu_temp_tablespace)                     | Create a temporary tablespace with this name.                                     |
[user](#rcu_user)                                           | The user used for the specified installation.                                     |
[version](#rcu_version)                                     | The version that is installed in the used Oracle home.                            |




### action<a name='rcu_action'>

The action to perform.

Valid actions are:
- `create`
- `delete`

The default value is: `create`

Type: `Enum['create','delete']`

Default:`'create'`

[Back to overview of rcu](#attributes)

### db_server<a name='rcu_db_server'>

The name of the database server to use.

Type: `String[1]`

Default:`undef`

[Back to overview of rcu](#attributes)

### db_service<a name='rcu_db_service'>

The name of the database service to use.

Type: `String[1]`

Default:`undef`

[Back to overview of rcu](#attributes)

### download_dir<a name='rcu_download_dir'>

The directory where the Puppet software puts all downloaded files.

Before Puppet can actually use remote files, they must be downloaded first. Puppet uses this directory to put all files in.

The default value is: `/install`

Type: `Stdlib::Absolutepath`

Default:`'/install'`

[Back to overview of rcu](#attributes)

### group<a name='rcu_group'>

The os group to use for these Oracle puppet definitions.

The default value is: `dba`

Type: `String[1]`

Default:`'dba'`

[Back to overview of rcu](#attributes)

### logoutput<a name='rcu_logoutput'>

log the outputs of Puppet exec or not.

When you specify `true` Puppet will log all output of `exec` types.

Valid values are:

- `true`
- `false`
- `on_failure`

Type: `Variant[Boolean,Enum['on_failure']]`

Default:`lookup({name => 'logoutput', default_value => 'on_failure'})`

[Back to overview of rcu](#attributes)

### oracle_home<a name='rcu_oracle_home'>

A directory to be used as Oracle home directory for this software.

Type: `Optional[Stdlib::Absolutepath]`

Default:`undef`

[Back to overview of rcu](#attributes)

### product<a name='rcu_product'>

The name of the product for which you want to install the RCU.

The following strings are supported as product:
- `soasuite`
- `webcenter`
- `oam`
- `oim`
- `all`

The default value is: `soasuite`

Type: `Enum['soasuite','webcenter','oam','oim','all']`

Default:`'soasuite'`

[Back to overview of rcu](#attributes)

### puppet_download_mnt_point<a name='rcu_puppet_download_mnt_point'>

The base path of all remote files for the defined type or class.

The default value is: `puppet:///modules/ora_install`

Type: `Optional[String[1]]`

Default:`undef`

[Back to overview of rcu](#attributes)

### rcu_file<a name='rcu_rcu_file'>

The file containing the RCU definition.

Type: `String[1]`

Default:`undef`

[Back to overview of rcu](#attributes)

### remote_file<a name='rcu_remote_file'>

**DEPRECATED**
This parameter is not being used anymore and will be removed in a future release.

`true`.

Type: `Optional[Boolean]`

Default:`true`

[Back to overview of rcu](#attributes)

### repos_password<a name='rcu_repos_password'>

The password for the repo user.

Type: `Easy_type::Password`


[Back to overview of rcu](#attributes)

### schema_prefix<a name='rcu_schema_prefix'>

The prefix name to use for the schema.

Type: `String[1]`

Default:`undef`

[Back to overview of rcu](#attributes)

### sys_password<a name='rcu_sys_password'>

The password of the `SYS` user on the database.

Type: `Easy_type::Password`


[Back to overview of rcu](#attributes)

### sys_user<a name='rcu_sys_user'>

The name of the `SYS` user on the database.

The default value is: `sys`

Type: `String[1]`

Default:`'sys'`

[Back to overview of rcu](#attributes)

### temp_tablespace<a name='rcu_temp_tablespace'>

Create a temporary tablespace with this name.

Type: `Optional[String[1]]`

Default:`undef`

[Back to overview of rcu](#attributes)

### user<a name='rcu_user'>

The user used for the specified installation.
The install class will not create the user for you. You must do that yourself.

The default value is: `oracle`

Type: `String[1]`

Default:`'oracle'`

[Back to overview of rcu](#attributes)

### version<a name='rcu_version'>

The version that is installed in the used Oracle home.

Puppet uses this value to decide on version specific actions.

Type: `String[1]`

Default:`'11.1.1.7'`

[Back to overview of rcu](#attributes)
