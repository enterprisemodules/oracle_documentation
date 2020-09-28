# ora\_install::net

## Overview

Installs and configures Oracle SQL*Net

This defined type allows you to install and configure Oracle SQL*net.

## Example

```puppet
ora_install::net{ 'config net8':
  oracle_home   => '/oracle/product/11.2/db',
  version       => '11.2',
  user          => 'oracle',
  group         => 'dba',
  download_dir  => '/install',
  db_port       => 1521,
}
```




## Attributes



Attribute Name                      | Short Description                                                  |
----------------------------------- | ------------------------------------------------------------------ |
[db_port](#net_db_port)             | The IP port number to use for connecting to the database.          |
[download_dir](#net_download_dir)   | The directory where the Puppet software puts all downloaded files. |
[group](#net_group)                 | The os group to use for these Oracle puppet definitions.           |
[listener_name](#net_listener_name) | The name of the listener process.                                  |
[logoutput](#net_logoutput)         | log the outputs of Puppet exec or not.                             |
[oracle_home](#net_oracle_home)     | A directory to be used as Oracle home directory for this software. |
[temp_dir](#net_temp_dir)           | Directory to use for temporary files.                              |
[user](#net_user)                   | The user used for the specified installation.                      |
[version](#net_version)             | The version that is installed in the used Oracle home.             |




### db_port<a name='net_db_port'>

The IP port number to use for connecting to the database.

The default value is: `1521`

Type: `Integer`

Default:`1521`

[Back to overview of net](#attributes)

### download_dir<a name='net_download_dir'>

The directory where the Puppet software puts all downloaded files.

Before Puppet can actually use remote files, they must be downloaded first. Puppet uses this directory to put all files in.

The default value is: `/install`

Type: `Stdlib::Absolutepath`

Default:`'/install'`

[Back to overview of net](#attributes)

### group<a name='net_group'>

The os group to use for these Oracle puppet definitions.

The default value is: `dba`

Type: `String[1]`

Default:`'dba'`

[Back to overview of net](#attributes)

### logoutput<a name='net_logoutput'>

log the outputs of Puppet exec or not.

When you specify `true` Puppet will log all output of `exec` types.

Valid values are:

- `true`
- `false`
- `on_failure`

Type: `Variant[Boolean,Enum['on_failure']]`

Default:`lookup({name => 'logoutput', default_value => 'on_failure'})`

[Back to overview of net](#attributes)

### oracle_home<a name='net_oracle_home'>

A directory to be used as Oracle home directory for this software.

Type: `Stdlib::Absolutepath`

Default:`undef`

[Back to overview of net](#attributes)

### temp_dir<a name='net_temp_dir'>

Directory to use for temporary files.

Type: `Stdlib::Absolutepath`

Default:`'/tmp'`

[Back to overview of net](#attributes)

### user<a name='net_user'>

The user used for the specified installation.
The install class will not create the user for you. You must do that yourself.

The default value is: `oracle`

Type: `String[1]`

Default:`'oracle'`

[Back to overview of net](#attributes)

### version<a name='net_version'>

The version that is installed in the used Oracle home.

Puppet uses this value to decide on version specific actions.

Type: `Ora_install::ShortVersion`

Default:`'11.2'`

[Back to overview of net](#attributes)

### listener_name<a name='net_listener_name'>

The name of the listener process.

The default value is: `listener`

Type: `String[1]`

Default:`'listener'`

[Back to overview of net](#attributes)
