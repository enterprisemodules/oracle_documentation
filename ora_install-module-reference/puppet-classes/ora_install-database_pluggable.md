# ora\_install::database_pluggable

## Overview

Creates or delete a pluggable database.

Under the hood, this defined type calls the `dbca` utility to create or delete a pluggable database in the specified source database.

Here is an example on how to create pluggable database:

```puppet
ora_install::database_pluggable{'pdb1':
  ensure                   => 'present',
  version                  => '12.1',
  oracle_home_dir          => '/oracle/product/12.1/db',
  user                     => 'oracle',
  group                    => 'dba',
  source_db                => 'orcl',
  pdb_name                 => 'pdb1',
  pdb_admin_username       => 'pdb_adm',
  pdb_admin_password       => 'Welcome01',
  pdb_datafile_destination => "/oracle/oradata/orcl/pdb1",
  create_user_tablespace   => true,
  logoutput                => true,
}
```
Here is an example on how to remove a pluggable database:

```puppet
ora_install::database_pluggable{'pdb1':
  ensure                   => 'absent',
  version                  => '12.1',
  oracle_home_dir          => '/oracle/product/12.1/db',
  user                     => 'oracle',
  group                    => 'dba',
  source_db                => 'orcl',
  pdb_name                 => 'pdb1',
  pdb_datafile_destination => "/oracle/oradata/orcl/pdb1",
  logoutput                => true,
}
```




## Attributes



Attribute Name                                                           | Short Description                                                                                 |
------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------- |
[create_user_tablespace](#database_pluggable_create_user_tablespace)     | Create a user tablespace in the PDB.                                                              |
[ensure](#database_pluggable_ensure)                                     | State to obtain.                                                                                  |
[group](#database_pluggable_group)                                       | The os group to use for these Oracle puppet definitions.                                          |
[log_output](#database_pluggable_log_output)                             | **DEPRECATED** This parameter is replaced by 'logoutput' and will be removed in a future release. |
[logoutput](#database_pluggable_logoutput)                               | log the outputs of Puppet exec or not.                                                            |
[oracle_home_dir](#database_pluggable_oracle_home_dir)                   | A directory to be used as Oracle home directory for this software.                                |
[pdb_admin_password](#database_pluggable_pdb_admin_password)             | Password for the admin user in the PDB.                                                           |
[pdb_admin_username](#database_pluggable_pdb_admin_username)             | Username for the admin user in the pluggable database.                                            |
[pdb_datafile_destination](#database_pluggable_pdb_datafile_destination) | The location where the PDB datafiles will be stored.                                              |
[pdb_name](#database_pluggable_pdb_name)                                 | Name of the pluggable database.                                                                   |
[source_db](#database_pluggable_source_db)                               | The database name of the container(source) database.                                              |
[user](#database_pluggable_user)                                         | The user used for the specified installation.                                                     |
[version](#database_pluggable_version)                                   | The version that is installed in the used Oracle home.                                            |




### create_user_tablespace<a name='database_pluggable_create_user_tablespace'>

Create a user tablespace in the PDB.

The default value is: `false`

Type: `Boolean`

Default:`true`

[Back to overview of database_pluggable](#attributes)

### ensure<a name='database_pluggable_ensure'>

State to obtain.

The ensure attribute can be one of two values:

- present
- absent

When you specify `present`, Puppet will make sure the resource is available with all specified options and properties.

When the resource is already available(installed), and all attributes are as the are specified, Puppet will do nothing.

When you specify `absent`, Puppet will remove the resource if it is available. If it is not installed, Puppet will do nothing.

Type: `Enum[present,absent]`

Default:`present`

[Back to overview of database_pluggable](#attributes)

### group<a name='database_pluggable_group'>

The os group to use for these Oracle puppet definitions.

The default value is: `dba`

Type: `String[1]`

Default:`'dba'`

[Back to overview of database_pluggable](#attributes)

### log_output<a name='database_pluggable_log_output'>

**DEPRECATED** This parameter is replaced by 'logoutput' and will be removed in a future release.
log the outputs of Puppet exec or not.

When you specify `true` Puppet will log all output of `exec` types.

Valid values are:

- `true`
- `false`
- `on_failure`

Type: `Optional[Variant[Boolean,Enum['on_failure']]]`

Default:`undef`

[Back to overview of database_pluggable](#attributes)

### logoutput<a name='database_pluggable_logoutput'>

log the outputs of Puppet exec or not.

When you specify `true` Puppet will log all output of `exec` types.

Valid values are:

- `true`
- `false`
- `on_failure`

Type: `Variant[Boolean,Enum['on_failure']]`

Default:`lookup({name => 'logoutput', default_value => 'on_failure'})`

[Back to overview of database_pluggable](#attributes)

### oracle_home_dir<a name='database_pluggable_oracle_home_dir'>

A directory to be used as Oracle home directory for this software.

Type: `Stdlib::Absolutepath`

Default:`undef`

[Back to overview of database_pluggable](#attributes)

### pdb_admin_password<a name='database_pluggable_pdb_admin_password'>

Password for the admin user in the PDB.

Type: `String[1]`

Default:`undef`

[Back to overview of database_pluggable](#attributes)

### pdb_admin_username<a name='database_pluggable_pdb_admin_username'>

Username for the admin user in the pluggable database.

The default value is: `pdb_adm`

Type: `String[1]`

Default:`'pdb_adm'`

[Back to overview of database_pluggable](#attributes)

### pdb_datafile_destination<a name='database_pluggable_pdb_datafile_destination'>

The location where the PDB datafiles will be stored.

Type: `String[1]`

Default:`undef`

[Back to overview of database_pluggable](#attributes)

### pdb_name<a name='database_pluggable_pdb_name'>

Name of the pluggable database.

Type: `String[1]`

Default:`undef`

[Back to overview of database_pluggable](#attributes)

### source_db<a name='database_pluggable_source_db'>

The database name of the container(source) database.

Type: `String[1]`

Default:`undef`

[Back to overview of database_pluggable](#attributes)

### user<a name='database_pluggable_user'>

The user used for the specified installation.
The install class will not create the user for you. You must do that yourself.

The default value is: `oracle`

Type: `String[1]`

Default:`'oracle'`

[Back to overview of database_pluggable](#attributes)

### version<a name='database_pluggable_version'>

The version that is installed in the used Oracle home.

Puppet uses this value to decide on version specific actions.

Type: `Enum['12.1','12.2', '18.0', '19.0']`

Default:`'12.1'`

[Back to overview of database_pluggable](#attributes)
