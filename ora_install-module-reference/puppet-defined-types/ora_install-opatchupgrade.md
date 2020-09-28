# ora\_install::opatchupgrade

## Overview

Installs or upgrades the specified version of the Oracle OPatch utility.

For `opatchupgrade` you need to provide the Oracle support csi_number and supportId and need to be online. Or leave them empty but it needs the Expect rpm to emulate OCM.

## Example

Here is an example on how to use this:

```puppet
ora_install::opatchupgrade{'112000_opatch_upgrade':
  oracle_home               => '/oracle/product/11.2/db',
  patch_file                => 'p6880880_112000_Linux-x86-64.zip',
  csi_number                => '11111',
  support_id                => 'john.doe@gmail.com',
  csi_number                => undef,
  support_id                => undef,
  opversion                 => '11.2.0.3.6',
  user                      => 'oracle',
  group                     => 'dba',
  download_dir              => '/install',
  puppet_download_mnt_point => 'puppet:///modules/software',
}
```




## Attributes



Attribute Name                                                        | Short Description                                                  |
--------------------------------------------------------------------- | ------------------------------------------------------------------ |
[csi_number](#opatchupgrade_csi_number)                               | The Customer Service Identification number.                        |
[download_dir](#opatchupgrade_download_dir)                           | The directory where the Puppet software puts all downloaded files. |
[group](#opatchupgrade_group)                                         | The os group to use for these Oracle puppet definitions.           |
[logoutput](#opatchupgrade_logoutput)                                 | log the outputs of Puppet exec or not.                             |
[opversion](#opatchupgrade_opversion)                                 | The version of Opatch you want to install.                         |
[oracle_home](#opatchupgrade_oracle_home)                             | A directory to be used as Oracle home directory for this software. |
[patch_file](#opatchupgrade_patch_file)                               | The zip file containing the Opatch utility.                        |
[puppet_download_mnt_point](#opatchupgrade_puppet_download_mnt_point) | The base path of all remote files for the defined type or class.   |
[support_id](#opatchupgrade_support_id)                               | Your support ID.                                                   |
[user](#opatchupgrade_user)                                           | The user used for the specified installation.                      |




### csi_number<a name='opatchupgrade_csi_number'>

The Customer Service Identification number.

This is used to generate an OCMRF file.

Type: `Optional[Integer]`

Default:`undef`

[Back to overview of opatchupgrade](#attributes)

### download_dir<a name='opatchupgrade_download_dir'>

The directory where the Puppet software puts all downloaded files.

Before Puppet can actually use remote files, they must be downloaded first. Puppet uses this directory to put all files in.

The default value is: `/install`

Type: `Stdlib::Absolutepath`

Default:`'/install'`

[Back to overview of opatchupgrade](#attributes)

### group<a name='opatchupgrade_group'>

The os group to use for these Oracle puppet definitions.

The default value is: `dba`

Type: `String[1]`

Default:`'dba'`

[Back to overview of opatchupgrade](#attributes)

### logoutput<a name='opatchupgrade_logoutput'>

log the outputs of Puppet exec or not.

When you specify `true` Puppet will log all output of `exec` types.

Valid values are:

- `true`
- `false`
- `on_failure`

Type: `Variant[Boolean,Enum['on_failure']]`

Default:`lookup({name => 'logoutput', default_value => 'on_failure'})`

[Back to overview of opatchupgrade](#attributes)

### opversion<a name='opatchupgrade_opversion'>

The version of Opatch you want to install.

Type: `String[1]`

Default:`undef`

[Back to overview of opatchupgrade](#attributes)

### oracle_home<a name='opatchupgrade_oracle_home'>

A directory to be used as Oracle home directory for this software.

Type: `Stdlib::Absolutepath`

Default:`undef`

[Back to overview of opatchupgrade](#attributes)

### patch_file<a name='opatchupgrade_patch_file'>

The zip file containing the Opatch utility.

Type: `String[1]`

Default:`undef`

[Back to overview of opatchupgrade](#attributes)

### puppet_download_mnt_point<a name='opatchupgrade_puppet_download_mnt_point'>

The base path of all remote files for the defined type or class.

The default value is: `puppet:///modules/ora_install`

Type: `Optional[String[1]]`

Default:`undef`

[Back to overview of opatchupgrade](#attributes)

### support_id<a name='opatchupgrade_support_id'>

Your support ID.

This is used to generate an OCMRF file.

Type: `Optional[String[1]]`

Default:`undef`

[Back to overview of opatchupgrade](#attributes)

### user<a name='opatchupgrade_user'>

The user used for the specified installation.
The install class will not create the user for you. You must do that yourself.

The default value is: `oracle`

Type: `String[1]`

Default:`'oracle'`

[Back to overview of opatchupgrade](#attributes)
