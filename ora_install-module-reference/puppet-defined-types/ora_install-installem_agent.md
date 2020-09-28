# ora\_install::installem_agent

## Overview

Installs the Oracle Enterprise Manager Agent.

## Suppirted versions

This defined type supports the following versions of Oracle:
- 12.1.0.4
- 12.1.0.5
- 13.1.0.0
- 13.2.0.0

## Example

Here is an example:

```puppet
ora_install::installem_agent{ 'Install em agent':
  version                     => '13.2.0.0',
  install_type                => 'agentPull',
  install_version             => '13.2.0.0.0',
  oracle_base_dir             => '/u01/app',
  agent_base_dir              => '/u01/app/agent/product',
  agent_instance_home_dir     => '/u01/app/agent/product/agent_inst',
  agent_registration_password => 'regme',
  agent_port                  => 3872,
  sysman_password             => 'Welkom01',
  oms_host                    => 'em1320.example.com',
  oms_port                    => 7799,
  em_upload_port              => 1159,
  logoutput                   => true,
}
```




## Attributes



Attribute Name                                                              | Short Description                                                                                 |
--------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------- |
[agent_base_dir](#installem_agent_agent_base_dir)                           | The directory to use as base for the agent software.                                              |
[agent_instance_home_dir](#installem_agent_agent_instance_home_dir)         | The directory to use as instance home.                                                            |
[agent_port](#installem_agent_agent_port)                                   | The IP port to use to for the agent.                                                              |
[agent_registration_password](#installem_agent_agent_registration_password) | The password to use to register the agent.                                                        |
[download_dir](#installem_agent_download_dir)                               | The directory where the Puppet software puts all downloaded files.                                |
[em_upload_port](#installem_agent_em_upload_port)                           | The port number of the HTTP port for the upload service.                                          |
[group](#installem_agent_group)                                             | The os group to use for these Oracle puppet definitions.                                          |
[install_platform](#installem_agent_install_platform)                       | The type of platform you want to install.                                                         |
[install_type](#installem_agent_install_type)                               | The type of install.                                                                              |
[install_version](#installem_agent_install_version)                         | The version you want to install.                                                                  |
[log_output](#installem_agent_log_output)                                   | **DEPRECATED** This parameter is replaced by 'logoutput' and will be removed in a future release. |
[logoutput](#installem_agent_logoutput)                                     | log the outputs of Puppet exec or not.                                                            |
[oms_host](#installem_agent_oms_host)                                       | The OMS host to use.                                                                              |
[oms_port](#installem_agent_oms_port)                                       | The IP port to use for connecting to the OMS host.                                                |
[ora_inventory_dir](#installem_agent_ora_inventory_dir)                     | The directory that contains the oracle inventory.                                                 |
[oracle_base_dir](#installem_agent_oracle_base_dir)                         | A directory to use as Oracle base directory.                                                      |
[source](#installem_agent_source)                                           | The source to use for the installation of the EM agent.                                           |
[sysman_password](#installem_agent_sysman_password)                         | The password to use for sysman.                                                                   |
[sysman_user](#installem_agent_sysman_user)                                 | The sysman user.                                                                                  |
[user](#installem_agent_user)                                               | The user used for the specified installation.                                                     |
[version](#installem_agent_version)                                         | The agent version to be installed
                                                                |




### agent_base_dir<a name='installem_agent_agent_base_dir'>

The directory to use as base for the agent software.

Type: `Stdlib::Absolutepath`

Default:`undef`

[Back to overview of installem_agent](#attributes)

### agent_instance_home_dir<a name='installem_agent_agent_instance_home_dir'>

The directory to use as instance home.

Type: `Optional[Stdlib::Absolutepath]`

Default:`undef`

[Back to overview of installem_agent](#attributes)

### agent_port<a name='installem_agent_agent_port'>

The IP port to use to for the agent.

The default value is: `3872`

Type: `Integer`

Default:`1830`

[Back to overview of installem_agent](#attributes)

### agent_registration_password<a name='installem_agent_agent_registration_password'>

The password to use to register the agent.

Type: `Optional[Easy_type::Password]`

Default:`undef`

[Back to overview of installem_agent](#attributes)

### download_dir<a name='installem_agent_download_dir'>

The directory where the Puppet software puts all downloaded files.

Before Puppet can actually use remote files, they must be downloaded first. Puppet uses this directory to put all files in.

The default value is: `/install`

Type: `Stdlib::Absolutepath`

Default:`'/install'`

[Back to overview of installem_agent](#attributes)

### em_upload_port<a name='installem_agent_em_upload_port'>

The port number of the HTTP port for the upload service.

The default value is: `1159`

Type: `Integer`

Default:`undef`

[Back to overview of installem_agent](#attributes)

### group<a name='installem_agent_group'>

The os group to use for these Oracle puppet definitions.

The default value is: `dba`

Type: `String[1]`

Default:`'oinstall'`

[Back to overview of installem_agent](#attributes)

### install_platform<a name='installem_agent_install_platform'>

The type of platform you want to install.

The default value is: `Linux x86-64`

Type: `String[1]`

Default:`'Linux x86-64'`

[Back to overview of installem_agent](#attributes)

### install_type<a name='installem_agent_install_type'>

The type of install.

valid values are:
- `undefined`
- `agentPull`
- `agentDeploy`

The default value is: `undefined`

Type: `Enum['agentPull','agentDeploy']`

Default:`undef`

[Back to overview of installem_agent](#attributes)

### install_version<a name='installem_agent_install_version'>

The version you want to install.

The default value is: `12.1.0.5.0`

Type: `Enum[
    '12.1.0.4.0',
    '12.1.0.5.0',
    '13.1.0.0.0',
    '13.2.0.0.0',
    '13.3.0.0.0'
  ]`

Default:`'12.1.0.5.0'`

[Back to overview of installem_agent](#attributes)

### log_output<a name='installem_agent_log_output'>

**DEPRECATED** This parameter is replaced by 'logoutput' and will be removed in a future release.
log the outputs of Puppet exec or not.

When you specify `true` Puppet will log all output of `exec` types.

Valid values are:

- `true`
- `false`
- `on_failure`

Type: `Optional[Variant[Boolean,Enum['on_failure']]]`

Default:`undef`

[Back to overview of installem_agent](#attributes)

### logoutput<a name='installem_agent_logoutput'>

log the outputs of Puppet exec or not.

When you specify `true` Puppet will log all output of `exec` types.

Valid values are:

- `true`
- `false`
- `on_failure`

Type: `Variant[Boolean, Enum['on_failure']]`

Default:`lookup({name => 'logoutput', default_value => 'on_failure'})`

[Back to overview of installem_agent](#attributes)

### oms_host<a name='installem_agent_oms_host'>

The OMS host to use.

Type: `String[1]`

Default:`undef`

[Back to overview of installem_agent](#attributes)

### oms_port<a name='installem_agent_oms_port'>

The IP port to use for connecting to the OMS host.

Type: `Integer`

Default:`undef`

[Back to overview of installem_agent](#attributes)

### ora_inventory_dir<a name='installem_agent_ora_inventory_dir'>

The directory that contains the oracle inventory.

The default value is: `/oracle_base/oraInventory`

Type: `Optional[Stdlib::Absolutepath]`

Default:`undef`

[Back to overview of installem_agent](#attributes)

### oracle_base_dir<a name='installem_agent_oracle_base_dir'>

A directory to use as Oracle base directory.

Type: `Stdlib::Absolutepath`

Default:`undef`

[Back to overview of installem_agent](#attributes)

### source<a name='installem_agent_source'>

The source to use for the installation of the EM agent.

Valid values are:

- an URL like: `https://<OMS_HOST>:<OMS_PORT>/em/install/getAgentImage`
- a local file like: `/tmp/12.1.0.4.0_AgentCore_226_Linux_x64.zip`

Type: `Optional[String[1]]`

Default:`undef`

[Back to overview of installem_agent](#attributes)

### sysman_password<a name='installem_agent_sysman_password'>

The password to use for sysman.

Type: `Optional[Easy_type::Password]`

Default:`undef`

[Back to overview of installem_agent](#attributes)

### sysman_user<a name='installem_agent_sysman_user'>

The sysman user.

The default value is: `sysman`

Type: `String[1]`

Default:`'sysman'`

[Back to overview of installem_agent](#attributes)

### user<a name='installem_agent_user'>

The user used for the specified installation.
The install class will not create the user for you. You must do that yourself.

The default value is: `oracle`

Type: `String[1]`

Default:`'oracle'`

[Back to overview of installem_agent](#attributes)

### version<a name='installem_agent_version'>

The agent version to be installed

- `12.1.0.4`
- `12.1.0.5`
- `13.1.0.0`
- `13.2.0.0`

Type: `Enum[
    '12.1.0.4',
    '12.1.0.5',
    '13.1.0.0',
    '13.2.0.0',
    '13.3.0.0'
  ]`

Default:`'12.1.0.5'`

[Back to overview of installem_agent](#attributes)
