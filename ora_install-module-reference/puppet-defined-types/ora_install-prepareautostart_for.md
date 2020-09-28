# ora\_install::prepareautostart_for

## Overview

Prepare autostart of the database for linux.

This defined creates the script needed to start the database after a system reboot. It supports both `systemd` and the older startup scripts.

## Example

Here is an example on how to use it:

```puppet
  ora_install::prepareautostart {'DB1':
    oracle_home  => '/oracle/db1',
    user         => 'oracle',
    service_name => 'start_db1',
  }
```




## Attributes



Attribute Name                                     | Short Description                                                  |
-------------------------------------------------- | ------------------------------------------------------------------ |
[logoutput](#prepareautostart_for_logoutput)       | log the outputs of Puppet exec or not.                             |
[oracle_home](#prepareautostart_for_oracle_home)   | A directory to be used as Oracle home directory for this software. |
[service_name](#prepareautostart_for_service_name) | The name of the init service to use.                               |
[user](#prepareautostart_for_user)                 | The user used for the specified installation.                      |




### oracle_home<a name='prepareautostart_for_oracle_home'>

A directory to be used as Oracle home directory for this software.

Type: `String[1]`

Default:`undef`

[Back to overview of prepareautostart_for](#attributes)

### user<a name='prepareautostart_for_user'>

The user used for the specified installation.
The install class will not create the user for you. You must do that yourself.

The default value is: `oracle`

Type: `String[1]`

Default:`'oracle'`

[Back to overview of prepareautostart_for](#attributes)

### service_name<a name='prepareautostart_for_service_name'>

The name of the init service to use.

The default value is: `dbora`


[Back to overview of prepareautostart_for](#attributes)

### logoutput<a name='prepareautostart_for_logoutput'>

log the outputs of Puppet exec or not.

When you specify `true` Puppet will log all output of `exec` types.

Valid values are:

- `true`
- `false`
- `on_failure`

Type: `Variant[Boolean,Enum['on_failure']]`

Default:`lookup({name => 'logoutput', default_value => 'on_failure'})`

[Back to overview of prepareautostart_for](#attributes)
