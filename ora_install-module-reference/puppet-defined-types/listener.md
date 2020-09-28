# ora\_install::listener

## Overview

Manage the oracle listener[DEPRECATED]

This defined type is deprecated. Please use [db_listener](/docs/ora_install/db_listener.html) custom type to manage your listener.

## Example

Here is an example on how to use this:

```puppet
ora_install::listener{'start listener':
  action        => 'start',
  oracle_base   => '/oracle',
  oracle_home   => '/oracle/product/11.2/db',
  user          => 'oracle',
  group         => 'dba',
  listener_name => 'listener'
}
```




## Attributes



Attribute Name                           | Short Description                                                  |
---------------------------------------- | ------------------------------------------------------------------ |
[action](#listener_action)               | The action to take.                                                |
[group](#listener_group)                 | The os group to use for these Oracle puppet definitions.           |
[listener_name](#listener_listener_name) | The name of the listener process.                                  |
[oracle_base](#listener_oracle_base)     | A directory to use as Oracle base directory.                       |
[oracle_home](#listener_oracle_home)     | A directory to be used as Oracle home directory for this software. |
[user](#listener_user)                   | The user used for the specified installation.                      |




### action<a name='listener_action'>

The action to take.

Valid values are:
- `running`
- `start`
- `abort`
- `stop`

The default value is: `start`

Type: `Enum['running','start','abort','stop']`

Default:`'start'`

[Back to overview of listener](#attributes)

### group<a name='listener_group'>

The os group to use for these Oracle puppet definitions.

The default value is: `dba`

Type: `String[1]`

Default:`'dba'`

[Back to overview of listener](#attributes)

### listener_name<a name='listener_listener_name'>

The name of the listener process.

The default value is: `listener`

Type: `String[1]`

Default:`'listener'`

[Back to overview of listener](#attributes)

### oracle_base<a name='listener_oracle_base'>

A directory to use as Oracle base directory.

Type: `Stdlib::Absolutepath`

Default:`undef`

[Back to overview of listener](#attributes)

### oracle_home<a name='listener_oracle_home'>

A directory to be used as Oracle home directory for this software.

Type: `Stdlib::Absolutepath`

Default:`undef`

[Back to overview of listener](#attributes)

### user<a name='listener_user'>

The user used for the specified installation.
The install class will not create the user for you. You must do that yourself.

The default value is: `oracle`

Type: `String[1]`

Default:`'oracle'`

[Back to overview of listener](#attributes)
