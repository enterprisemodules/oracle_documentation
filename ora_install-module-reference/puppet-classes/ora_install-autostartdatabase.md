# ora\_install::autostartdatabase

## Overview

This defined type create's a startup script for the specified database and enables the service. The end result is that the named Oracle database is restarted after a system restart.

## Example

Here is an example on how to use it:

```text
ora_install::autostartdatabase{ 'autostart oracle':
  oracle_home             => '/oracle/product/12.1/db',
  user                    => 'oracle',
  db_name                 => 'test',
}
```

## Attributes

| Attribute Name | Short Description |
| :--- | :--- |
| [db\_domain]() | The domain of the database. |
| [db\_name]() | The name of the database. |
| [db\_policy]() | The srvctl management policy for the database |
| [db\_type]() | The type of the database used to specify if the database should be started by an init script or srvctl. |
| [group]() | The os group to use for these Oracle puppet definitions. |
| [logoutput]() | log the outputs of Puppet exec or not. |
| [oracle\_home]() | A directory to be used as Oracle home directory for this software. |
| [service\_name]() | The service name to start. |
| [start\_option]() | The srvctl startup options for the database. |
| [user]() | The user used for the specified installation. |

### db\_domain

The domain of the database.

Type: `Optional[String[1]]`

Default:`undef`

[Back to overview of autostartdatabase]()

### db\_name

The name of the database.

Type: `String[1]`

Default:`undef`

[Back to overview of autostartdatabase]()

### db\_policy

The srvctl management policy for the database

Valid values are:

* `AUTOMATIC`
* `MANUAL`
* `NORESTART`

The default value is: `AUTOMATIC`

Type: `Enum['AUTOMATIC','MANUAL','NORESTART']`

Default:`'AUTOMATIC'`

[Back to overview of autostartdatabase]()

### db\_type

The type of the database used to specify if the database should be started by an init script or srvctl.

Valid values are:

* `grid`
* `database`

The default value is: 'database'

Type: `Enum['database','grid']`

Default:`'database'`

[Back to overview of autostartdatabase]()

### group

The os group to use for these Oracle puppet definitions.

The default value is: `dba`

Type: `String[1]`

Default:`'dba'`

[Back to overview of autostartdatabase]()

### logoutput

log the outputs of Puppet exec or not.

When you specify `true` Puppet will log all output of `exec` types.

Valid values are:

* `true`
* `false`
* `on_failure`

Type: `Variant[Boolean,Enum['on_failure']]`

Default:`lookup({name => 'logoutput', default_value => 'on_failure'})`

[Back to overview of autostartdatabase]()

### oracle\_home

A directory to be used as Oracle home directory for this software.

Type: `Stdlib::Absolutepath`

Default:`undef`

[Back to overview of autostartdatabase]()

### service\_name

The service name to start.

Type: `String[1]`

Default:`'dbora'`

[Back to overview of autostartdatabase]()

### start\_option

The srvctl startup options for the database.

Valid values are:

* `OPEN`
* `MOUNT`
* `READ ONLY`

The default value is: `OPEN`

Type: `Enum['OPEN','MOUNT','READ ONLY']`

Default:`'OPEN'`

[Back to overview of autostartdatabase]()

### user

The user used for the specified installation. The install class will not create the user for you. You must do that yourself.

The default value is: `oracle`

Type: `String[1]`

Default:`'oracle'`

[Back to overview of autostartdatabase]()

