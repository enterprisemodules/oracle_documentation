# ora\_install::autostartdatabase

# Overview

This defined type create's a startup script for the specified database and enables the service. The end result is that the named Oracle database is
restarted after a system restart.

# Example

Here is an example on how to use it:

``` puppet
ora_install::autostartdatabase{ 'autostart oracle':
  oracle_home             => '/oracle/product/12.1/db',
  user                    => 'oracle',
  db_name                 => 'test',
}
```

# Attributes

Attribute Name                                  | Short Description                                                                                       |
----------------------------------------------- | ------------------------------------------------------------------------------------------------------- |
[db_domain](#autostartdatabase_db_domain)       | The domain of the database.                                                                             |
[db_name](#autostartdatabase_db_name)           | The name of the database.                                                                               |
[db_policy](#autostartdatabase_db_policy)       | The srvctl management policy for the database|
[db_type](#autostartdatabase_db_type)           | The type of the database used to specify if the database should be started by an init script or srvctl. |
[group](#autostartdatabase_group)               | The os group to use for these Oracle puppet definitions.                                                |
[logoutput](#autostartdatabase_logoutput)       | log the outputs of Puppet exec or not.                                                                  |
[oracle_home](#autostartdatabase_oracle_home)   | A directory to be used as Oracle home directory for this software.                                      |
[service_name](#autostartdatabase_service_name) | The service name to start.                                                                              |
[start_option](#autostartdatabase_start_option) | The srvctl startup options for the database.                                                            |
[user](#autostartdatabase_user)                 | The user used for the specified installation.                                                           |




### db_domain<a name='autostartdatabase_db_domain'>

The domain of the database.

Type: `Optional[String[1]]`

Default:`undef`

[Back to overview of autostartdatabase](#attributes)

### db_name<a name='autostartdatabase_db_name'>

The name of the database.

Type: `String[1]`

Default:`undef`

[Back to overview of autostartdatabase](#attributes)

### db_policy<a name='autostartdatabase_db_policy'>

The srvctl management policy for the database

Valid values are:
- `AUTOMATIC`
- `MANUAL`
- `NORESTART`

The default value is: `AUTOMATIC`

Type: `Enum['AUTOMATIC','MANUAL','NORESTART']`

Default:`'AUTOMATIC'`

[Back to overview of autostartdatabase](#attributes)

### db_type<a name='autostartdatabase_db_type'>

The type of the database used to specify if the database should be started by an init script or srvctl.

Valid values are:
- `grid`
- `database`

The default value is: 'database'

Type: `Enum['database','grid']`

Default:`'database'`

[Back to overview of autostartdatabase](#attributes)

### group<a name='autostartdatabase_group'>

The os group to use for these Oracle puppet definitions.

The default value is: `dba`

Type: `String[1]`

Default:`'dba'`

[Back to overview of autostartdatabase](#attributes)

### logoutput<a name='autostartdatabase_logoutput'>

log the outputs of Puppet exec or not.

When you specify `true` Puppet will log all output of `exec` types.

Valid values are:

- `true`
- `false`
- `on_failure`

Type: `Variant[Boolean,Enum['on_failure']]`

Default:`lookup({name => 'logoutput', default_value => 'on_failure'})`

[Back to overview of autostartdatabase](#attributes)

### oracle_home<a name='autostartdatabase_oracle_home'>

A directory to be used as Oracle home directory for this software.

Type: `Stdlib::Absolutepath`

Default:`undef`

[Back to overview of autostartdatabase](#attributes)

### service_name<a name='autostartdatabase_service_name'>

The service name to start.

Type: `String[1]`

Default:`'dbora'`

[Back to overview of autostartdatabase](#attributes)

### start_option<a name='autostartdatabase_start_option'>

The srvctl startup options for the database.

Valid values are:
- `OPEN`
- `MOUNT`
- `READ ONLY`

The default value is: `OPEN`

Type: `Enum['OPEN','MOUNT','READ ONLY']`

Default:`'OPEN'`

[Back to overview of autostartdatabase](#attributes)

### user<a name='autostartdatabase_user'>

The user used for the specified installation.
The install class will not create the user for you. You must do that yourself.

The default value is: `oracle`

Type: `String[1]`

Default:`'oracle'`

[Back to overview of autostartdatabase](#attributes)