# ora\_install::opatch

## Overview

[DEPRECATED] Wrapper defined type for installing patches. 

Please use[`ora_opatch`](/docs/ora_install/ora_opatch.html) to manage patches of your database software.

## Example

Here is an example on how to use this:

```puppet
ora_install::opatch{'19121551_db_patch':
  ensure                    => 'present',
  oracle_product_home       => hiera('oracle_home_dir'),
  patch_id                  => '19121551',
  patch_file                => 'p19121551_112040_Linux-x86-64.zip',
  user                      => hiera('oracle_os_user'),
  group                     => 'oinstall',
  download_dir              => hiera('oracle_download_dir'),
  ocmrf                     => true,
  require                   => Ora_install::Opatchupgrade['112000_opatch_upgrade_db'],
  puppet_download_mnt_point => hiera('oracle_source'),
}
```




## Attributes



Attribute Name                                                 | Short Description                                                                 |
-------------------------------------------------------------- | --------------------------------------------------------------------------------- |
[bundle_sub_folder](#opatch_bundle_sub_folder)                 | The folder in the zip file used for the specified patch.                          |
[bundle_sub_patch_id](#opatch_bundle_sub_patch_id)             | The subid of the patch.                                                           |
[clusterware](#opatch_clusterware)                             | When true use opatch auto.                                                        |
[download_dir](#opatch_download_dir)                           | The directory where the Puppet software puts all downloaded files.                |
[ensure](#opatch_ensure)                                       | State to obtain.                                                                  |
[group](#opatch_group)                                         | The os group to use for these Oracle puppet definitions.                          |
[ocmrf](#opatch_ocmrf)                                         | Wether or not to use OCMRF file.                                                  |
[oracle_product_home](#opatch_oracle_product_home)             | The Oracle home to use.                                                           |
[patch_file](#opatch_patch_file)                               | The name of the patch file.                                                       |
[patch_id](#opatch_patch_id)                                   | The ID of the patch to apply.                                                     |
[puppet_download_mnt_point](#opatch_puppet_download_mnt_point) | The base path of all remote files for the defined type or class.                  |
[remote_file](#opatch_remote_file)                             | This parameter is not being used anymore and will be removed in a future release. |
[user](#opatch_user)                                           | The user used for the specified installation.                                     |




### bundle_sub_folder<a name='opatch_bundle_sub_folder'>

The folder in the zip file used for the specified patch.

Type: `Optional[Integer]`

Default:`undef`

[Back to overview of opatch](#attributes)

### bundle_sub_patch_id<a name='opatch_bundle_sub_patch_id'>

The subid of the patch.

Type: `Optional[Integer]`

Default:`undef`

[Back to overview of opatch](#attributes)

### clusterware<a name='opatch_clusterware'>

When true use opatch auto.

Default value `false`

Type: `Boolean`

Default:`false`

[Back to overview of opatch](#attributes)

### download_dir<a name='opatch_download_dir'>

The directory where the Puppet software puts all downloaded files.

Before Puppet can actually use remote files, they must be downloaded first. Puppet uses this directory to put all files in.

The default value is: `/install`

Type: `Stdlib::Absolutepath`

Default:`'/install'`

[Back to overview of opatch](#attributes)

### ensure<a name='opatch_ensure'>

State to obtain.

The ensure attribute can be one of two values:

- present
- absent

When you specify `present`, Puppet will make sure the resource is available with all specified options and properties.

When the resource is already available(installed), and all attributes are as the are specified, Puppet will do nothing.

When you specify `absent`, Puppet will remove the resource if it is available. If it is not installed, Puppet will do nothing.

Type: `Enum[present, absent]`

Default:`present`

[Back to overview of opatch](#attributes)

### group<a name='opatch_group'>

The os group to use for these Oracle puppet definitions.

The default value is: `dba`

Type: `String[1]`

Default:`'dba'`

[Back to overview of opatch](#attributes)

### ocmrf<a name='opatch_ocmrf'>

Wether or not to use OCMRF file.

The default value is: `false`

Type: `Boolean`

Default:`false`

[Back to overview of opatch](#attributes)

### oracle_product_home<a name='opatch_oracle_product_home'>

The Oracle home to use.

Type: `Stdlib::Absolutepath`

Default:`undef`

[Back to overview of opatch](#attributes)

### patch_file<a name='opatch_patch_file'>

The name of the patch file.

Type: `String[1]`

Default:`undef`

[Back to overview of opatch](#attributes)

### patch_id<a name='opatch_patch_id'>

The ID of the patch to apply.

Type: `Integer`

Default:`undef`

[Back to overview of opatch](#attributes)

### puppet_download_mnt_point<a name='opatch_puppet_download_mnt_point'>

The base path of all remote files for the defined type or class.

The default value is: `puppet:///modules/ora_install`

Type: `Optional[String[1]]`

Default:`undef`

[Back to overview of opatch](#attributes)

### remote_file<a name='opatch_remote_file'>

**DEPRECATED**
This parameter is not being used anymore and will be removed in a future release.

`true`.

Type: `Optional[Boolean]`

Default:`undef`

[Back to overview of opatch](#attributes)

### user<a name='opatch_user'>

The user used for the specified installation.
The install class will not create the user for you. You must do that yourself.

The default value is: `oracle`

Type: `String[1]`

Default:`'oracle'`

[Back to overview of opatch](#attributes)
