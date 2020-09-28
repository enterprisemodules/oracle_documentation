# ora\_install::tnsnames

## Overview

Manages an entry in a `tnsnames.ora` file.

## Example

Here is an examples on how to use this:

```puppet
ora_install::tnsnames{'entry':
  oracle_home          => '/u01/app/oracle/product/12.2.0.1/db_home1',
  user                 => 'oracle',
  group                => 'dba',
  server               => { myserver1 => { host => DB122a.example.nl, port => '1521', protocol => 'TCP' },
                            myserver2 => { host => DB122b.example.nl, port => '1521', protocol => 'TCP' }},
  connect_service_name => 'DB122.domain.local',
  connect_server       => 'DEDICATED',
  entry_type           => 'tnsname',
}
```




## Attributes



Attribute Name                                         | Short Description                                                  |
------------------------------------------------------ | ------------------------------------------------------------------ |
[connect_server](#tnsnames_connect_server)             | The name of the server to connect to.                              |
[connect_service_name](#tnsnames_connect_service_name) | The name of the service to connect to.                             |
[entry_type](#tnsnames_entry_type)                     | The type of entry to manage.                                       |
[failover](#tnsnames_failover)                         | Failover ON or OFF.                                                |
[group](#tnsnames_group)                               | The os group to use for these Oracle puppet definitions.           |
[loadbalance](#tnsnames_loadbalance)                   | Load balance ON or OFF.                                            |
[oracle_home](#tnsnames_oracle_home)                   | A directory to be used as Oracle home directory for this software. |
[server](#tnsnames_server)                             | A Hash defining the server entry.                                  |
[user](#tnsnames_user)                                 | The user used for the specified installation.                      |




### connect_server<a name='tnsnames_connect_server'>

The name of the server to connect to.

Type: `String[1]`

Default:`'DEDICATED'`

[Back to overview of tnsnames](#attributes)

### connect_service_name<a name='tnsnames_connect_service_name'>

The name of the service to connect to.

Type: `Optional[String[1]]`

Default:`undef`

[Back to overview of tnsnames](#attributes)

### entry_type<a name='tnsnames_entry_type'>

The type of entry to manage.

You can manage the next type of entries:
- `tnsname`
- `listener`

The default value is: `tnsname`

Type: `Enum['tnsname','listener']`

Default:`'tnsname'`

[Back to overview of tnsnames](#attributes)

### failover<a name='tnsnames_failover'>

Failover ON or OFF.

Valid values are:
- `ON`
- `OFF`

The default value is: `ON`

Type: `String[1]`

Default:`'ON'`

[Back to overview of tnsnames](#attributes)

### group<a name='tnsnames_group'>

The os group to use for these Oracle puppet definitions.

The default value is: `dba`

Type: `String[1]`

Default:`'dba'`

[Back to overview of tnsnames](#attributes)

### loadbalance<a name='tnsnames_loadbalance'>

Load balance ON or OFF.

Valid values are:
- `ON`
- `OFF`

The default value is: `ON`

Type: `port => '1521', protocol => 'TCP' }},
  String[1]`

Default:`'ON'`

[Back to overview of tnsnames](#attributes)

### oracle_home<a name='tnsnames_oracle_home'>

A directory to be used as Oracle home directory for this software.

Type: `Stdlib::Absolutepath`

Default:`undef`

[Back to overview of tnsnames](#attributes)

### server<a name='tnsnames_server'>

A Hash defining the server entry.

The default value is: 
```
{myserver => { host => undef, port => '1521', protocol => 'TCP' }}
```

Type: `Hash`

Default:`{myserver => { host => undef`

[Back to overview of tnsnames](#attributes)

### user<a name='tnsnames_user'>

The user used for the specified installation.
The install class will not create the user for you. You must do that yourself.

The default value is: `oracle`

Type: `String[1]`

Default:`'oracle'`

[Back to overview of tnsnames](#attributes)
