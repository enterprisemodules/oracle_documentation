# ora\_install::prepareautostart

## Overview

Prepare autostart of the database for linux.

This class creates the script needed to start the database after a system reboot. It supports both `systemd` and the older startup scripts.

# Example

Here is an example on how to use it:

```puppet
  class { 'class ora_install::prepareautostart':
    oracle_home  => '/oracle/db1',
    user         => 'oracle',
    service_name => 'start_db1',
  }
```
This class is a conveniance class arround the defined type `prepareautostart_for`.




## Attributes



Attribute Name                                 | Short Description                                                  |
---------------------------------------------- | ------------------------------------------------------------------ |
[logoutput](#prepareautostart_logoutput)       | log the outputs of Puppet exec or not.                             |
[oracle_home](#prepareautostart_oracle_home)   | A directory to be used as Oracle home directory for this software. |
[service_name](#prepareautostart_service_name) | The name of the init service to use.                               |
[user](#prepareautostart_user)                 | The user used for the specified installation.                      |




### oracle_home<a name='prepareautostart_oracle_home'>

A directory to be used as Oracle home directory for this software.

Type: `Stdlib::Absolutepath`

Default:`undef`

[Back to overview of prepareautostart](#attributes)

### user<a name='prepareautostart_user'>

The user used for the specified installation.
The install class will not create the user for you. You must do that yourself.

The default value is: `oracle`

Type: `String[1]`

Default:`'oracle'`

[Back to overview of prepareautostart](#attributes)

### service_name<a name='prepareautostart_service_name'>

The name of the init service to use.

The default value is: `dbora`

Type: `String[1]`

Default:`'dbora'`

[Back to overview of prepareautostart](#attributes)

### logoutput<a name='prepareautostart_logoutput'>

log the outputs of Puppet exec or not.

When you specify `true` Puppet will log all output of `exec` types.

Valid values are:

- `true`
- `false`
- `on_failure`

Type: `Variant[Boolean,Enum['on_failure']]`

Default:`lookup({name => 'logoutput', default_value => 'on_failure'})`

[Back to overview of prepareautostart](#attributes)
