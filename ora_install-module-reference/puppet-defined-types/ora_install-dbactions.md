# ora\_install::dbactions

## Overview

Defined type to start and stop a database. [DEPRECATED]

This is defined type to start or stop a database. Usage of this type is discouraged. Please use [db_control](/docs/ora_install/db_control.html) for this function.

Here is an example on how to use this:
```puppet
ora_install::dbactions{ 'stop testDb':
  db_name     => 'test',
  oracle_home => '/oracle/product/11.2/db',
  user        => 'oracle',
  group       => 'dba',
  action      => 'stop',
}
```




## Attributes



Attribute Name                        | Short Description                                                  |
------------------------------------- | ------------------------------------------------------------------ |
[action](#dbactions_action)           | The action you want to take.                                       |
[db_name](#dbactions_db_name)         | The database you want to do the action on.                         |
[db_type](#dbactions_db_type)         | The type of service you want to manage.                            |
[grid_home](#dbactions_grid_home)     | The oracle home directory to use for the GRID software.            |
[group](#dbactions_group)             | The os group to use for these Oracle puppet definitions.           |
[oracle_home](#dbactions_oracle_home) | A directory to be used as Oracle home directory for this software. |
[user](#dbactions_user)               | The user used for the specified installation.                      |




### action<a name='dbactions_action'>

The action you want to take.

Valid values are:
- `start`
- `running`
- `stop`
- `abort`

Default value is: `start`

Type: `Enum['running','start','stop','abort']`

Default:`'start'`

[Back to overview of dbactions](#attributes)

### db_name<a name='dbactions_db_name'>

The database you want to do the action on.

Type: `String[1]`

Default:`'orcl'`

[Back to overview of dbactions](#attributes)

### db_type<a name='dbactions_db_type'>

The type of service you want to manage.

Valid values are:

- `database`
- `grid`
- `asm`

Type: `Enum['database','asm','grid']`

Default:`'database'`

[Back to overview of dbactions](#attributes)

### grid_home<a name='dbactions_grid_home'>

The oracle home directory to use for the GRID software.

Type: `Optional[Stdlib::Absolutepath]`

Default:`undef`

[Back to overview of dbactions](#attributes)

### group<a name='dbactions_group'>

The os group to use for these Oracle puppet definitions.

The default value is: `dba`

Type: `String[1]`

Default:`'dba'`

[Back to overview of dbactions](#attributes)

### oracle_home<a name='dbactions_oracle_home'>

A directory to be used as Oracle home directory for this software.

Type: `Stdlib::Absolutepath`

Default:`undef`

[Back to overview of dbactions](#attributes)

### user<a name='dbactions_user'>

The user used for the specified installation.
The install class will not create the user for you. You must do that yourself.

The default value is: `oracle`

Type: `String[1]`

Default:`'oracle'`

[Back to overview of dbactions](#attributes)
