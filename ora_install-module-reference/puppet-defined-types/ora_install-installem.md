# ora\_install::installem

## Overview

Installs the Oracle Enterprse Manager.

## Example

Here is an example on how to use this:

```puppet
ora_install::installem{ 'em13200':
  version                     => '13.2.0.0',
  file                        => 'em13200p1_linux64',
  oracle_base_dir             => '/u01/app/oracle',
  oracle_home_dir             => '/u01/app/oracle/product/13.2.0.0/em_home1',
  agent_base_dir              => '/u01/app/oracle/agent',
  software_library_dir        => '/u01/app/oracle/swlib',
  weblogic_user               => 'weblogic',
  weblogic_password           => 'Welcome01',
  database_hostname           => 'em1320.example.com',
  database_listener_port      => 1521,
  database_service_sid_name   => 'EM122.domain.local',
  database_sys_password       => 'Welcome01',
  sysman_password             => 'Welcome01',
  agent_registration_password => 'Welcome01',
  deployment_size             => 'SMALL',
  user                        => 'oracle',
  group                       => 'oinstall',
  download_dir                => '/install',
  zip_extract                 => true,
  puppet_download_mnt_point   => 'puppet:///modules/software',
  logoutput                   => true,
}

```



## Attributes



Attribute Name                                                            | Short Description                                                                                 |
------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------- |
[admin_server_https_port](#installem_admin_server_https_port)             | The https IP port from the WLS Admin server.                                                      |
[agent_base_dir](#installem_agent_base_dir)                               | The directory to use as base for the agent software.                                              |
[agent_port](#installem_agent_port)                                       | The IP port to use to for the agent.                                                              |
[agent_registration_password](#installem_agent_registration_password)     | The password to use to register the agent.                                                        |
[bi_publisher_http_port](#installem_bi_publisher_http_port)               | The http port to use for the BI Publisher.                                                        |
[bi_publisher_https_port](#installem_bi_publisher_https_port)             | The https port to use for the BI Publisher.                                                       |
[database_hostname](#installem_database_hostname)                         | The DNS name of the database host.                                                                |
[database_listener_port](#installem_database_listener_port)               | The IP port for the database listener.                                                            |
[database_service_sid_name](#installem_database_service_sid_name)         | The database service SID name for the database.                                                   |
[database_sys_password](#installem_database_sys_password)                 | The password of the SYS user of the database.                                                     |
[deployment_size](#installem_deployment_size)                             | The size of the deployment.                                                                       |
[download_dir](#installem_download_dir)                                   | The directory where the Puppet software puts all downloaded files.                                |
[em_central_console_http_port](#installem_em_central_console_http_port)   | The port number of the HTTP port for the central console.                                         |
[em_central_console_https_port](#installem_em_central_console_https_port) | The port number of the HTTPS port for the central console.                                        |
[em_upload_http_port](#installem_em_upload_http_port)                     | The port number of the HTTP port for the upload service.                                          |
[em_upload_https_port](#installem_em_upload_https_port)                   | The port number of the HTTPS port for the upload service.                                         |
[file](#installem_file)                                                   | The source file to use.                                                                           |
[group](#installem_group)                                                 | The os group to use for these Oracle puppet definitions.                                          |
[log_output](#installem_log_output)                                       | **DEPRECATED** This parameter is replaced by 'logoutput' and will be removed in a future release. |
[logoutput](#installem_logoutput)                                         | log the outputs of Puppet exec or not.                                                            |
[managed_server_http_port](#installem_managed_server_http_port)           | The port number of the HTTP port for the Managed server.                                          |
[managed_server_https_port](#installem_managed_server_https_port)         | The port number of the HTTPS port for the Managed server.                                         |
[nodemanager_https_port](#installem_nodemanager_https_port)               | The port number of the HTTPS port for the Node manager.                                           |
[ora_inventory_dir](#installem_ora_inventory_dir)                         | The directory that contains the oracle inventory.                                                 |
[oracle_base_dir](#installem_oracle_base_dir)                             | A directory to use as Oracle base directory.                                                      |
[oracle_home_dir](#installem_oracle_home_dir)                             | A directory to be used as Oracle home directory for this software.                                |
[puppet_download_mnt_point](#installem_puppet_download_mnt_point)         | The base path of all remote files for the defined type or class.                                  |
[remote_file](#installem_remote_file)                                     | This parameter is not being used anymore and will be removed in a future release.                 |
[software_library_dir](#installem_software_library_dir)                   | The directory to use for the software library.                                                    |
[sysman_password](#installem_sysman_password)                             | The password to use for sysman.                                                                   |
[temp_dir](#installem_temp_dir)                                           | Directory to use for temporary files.                                                             |
[user](#installem_user)                                                   | The user used for the specified installation.                                                     |
[version](#installem_version)                                             | The version that is installed in the used Oracle home.                                            |
[weblogic_password](#installem_weblogic_password)                         | The password to use for WebLogic.                                                                 |
[weblogic_user](#installem_weblogic_user)                                 | The username to use for WebLogic.                                                                 |
[zip_extract](#installem_zip_extract)                                     | The specified source file is a zip file that needs te be extracted.                               |




### admin_server_https_port<a name='installem_admin_server_https_port'>

The https IP port from the WLS Admin server.

The default value is: `7101`

Type: `Integer`

Default:`7101`

[Back to overview of installem](#attributes)

### agent_base_dir<a name='installem_agent_base_dir'>

The directory to use as base for the agent software.

Type: `Stdlib::Absolutepath`

Default:`undef`

[Back to overview of installem](#attributes)

### agent_port<a name='installem_agent_port'>

The IP port to use to for the agent.

The default value is: `3872`

Type: `Integer`

Default:`3872`

[Back to overview of installem](#attributes)

### agent_registration_password<a name='installem_agent_registration_password'>

The password to use to register the agent.

Type: `Easy_type::Password`


[Back to overview of installem](#attributes)

### bi_publisher_http_port<a name='installem_bi_publisher_http_port'>

The http port to use for the BI Publisher.

The default value is: `9701`

Type: `Integer`

Default:`9701`

[Back to overview of installem](#attributes)

### bi_publisher_https_port<a name='installem_bi_publisher_https_port'>

The https port to use for the BI Publisher.

The default value is: `9801`

Type: `Integer`

Default:`9801`

[Back to overview of installem](#attributes)

### database_hostname<a name='installem_database_hostname'>

The DNS name of the database host.

Type: `String[1]`

Default:`undef`

[Back to overview of installem](#attributes)

### database_listener_port<a name='installem_database_listener_port'>

The IP port for the database listener.

The default value is: `1521`

Type: `Integer`

Default:`1521`

[Back to overview of installem](#attributes)

### database_service_sid_name<a name='installem_database_service_sid_name'>

The database service SID name for the database.

Type: `String[1]`

Default:`undef`

[Back to overview of installem](#attributes)

### database_sys_password<a name='installem_database_sys_password'>

The password of the SYS user of the database.

Type: `Easy_type::Password`


[Back to overview of installem](#attributes)

### deployment_size<a name='installem_deployment_size'>

The size of the deployment.

Valid values are:
- `SMALL`
- `MEDIUM`
- `LARGE`

The default value is: `SMALL`

Type: `Enum['SMALL','MEDIUM','LARGE']`

Default:`'SMALL'`

[Back to overview of installem](#attributes)

### download_dir<a name='installem_download_dir'>

The directory where the Puppet software puts all downloaded files.

Before Puppet can actually use remote files, they must be downloaded first. Puppet uses this directory to put all files in.

The default value is: `/install`

Type: `Stdlib::Absolutepath`

Default:`'/install'`

[Back to overview of installem](#attributes)

### em_central_console_http_port<a name='installem_em_central_console_http_port'>

The port number of the HTTP port for the central console.

The default value is: `7788`

Type: `Integer`

Default:`7788`

[Back to overview of installem](#attributes)

### em_central_console_https_port<a name='installem_em_central_console_https_port'>

The port number of the HTTPS port for the central console.

The default value is: `7799`

Type: `Integer`

Default:`7799`

[Back to overview of installem](#attributes)

### em_upload_http_port<a name='installem_em_upload_http_port'>

The port number of the HTTP port for the upload service.

The default value is: `1159`

Type: `Integer`

Default:`4889`

[Back to overview of installem](#attributes)

### em_upload_https_port<a name='installem_em_upload_https_port'>

The port number of the HTTPS port for the upload service.

The default value is: `4889`

Type: `Integer`

Default:`1159`

[Back to overview of installem](#attributes)

### file<a name='installem_file'>

The source file to use.

Type: `String[1]`

Default:`undef`

[Back to overview of installem](#attributes)

### group<a name='installem_group'>

The os group to use for these Oracle puppet definitions.

The default value is: `dba`

Type: `String[1]`

Default:`'oinstall'`

[Back to overview of installem](#attributes)

### log_output<a name='installem_log_output'>

**DEPRECATED** This parameter is replaced by 'logoutput' and will be removed in a future release.
log the outputs of Puppet exec or not.

When you specify `true` Puppet will log all output of `exec` types.

Valid values are:

- `true`
- `false`
- `on_failure`

Type: `Optional[Variant[Boolean,Enum['on_failure']]]`

Default:`undef`

[Back to overview of installem](#attributes)

### logoutput<a name='installem_logoutput'>

log the outputs of Puppet exec or not.

When you specify `true` Puppet will log all output of `exec` types.

Valid values are:

- `true`
- `false`
- `on_failure`

Type: `Variant[Boolean,Enum['on_failure']]`

Default:`lookup({name => 'logoutput', default_value => 'on_failure'})`

[Back to overview of installem](#attributes)

### managed_server_http_port<a name='installem_managed_server_http_port'>

The port number of the HTTP port for the Managed server.

The default value is: `7201`

Type: `Integer`

Default:`7201`

[Back to overview of installem](#attributes)

### managed_server_https_port<a name='installem_managed_server_https_port'>

The port number of the HTTPS port for the Managed server.

The default value is: `7301`

Type: `Integer`

Default:`7301`

[Back to overview of installem](#attributes)

### nodemanager_https_port<a name='installem_nodemanager_https_port'>

The port number of the HTTPS port for the Node manager.

The default value is: `7401`

Type: `Integer`

Default:`7401`

[Back to overview of installem](#attributes)

### ora_inventory_dir<a name='installem_ora_inventory_dir'>

The directory that contains the oracle inventory.

The default value is: `/oracle_base/oraInventory`

Type: `Optional[Stdlib::Absolutepath]`

Default:`undef`

[Back to overview of installem](#attributes)

### oracle_base_dir<a name='installem_oracle_base_dir'>

A directory to use as Oracle base directory.

Type: `Stdlib::Absolutepath`

Default:`undef`

[Back to overview of installem](#attributes)

### oracle_home_dir<a name='installem_oracle_home_dir'>

A directory to be used as Oracle home directory for this software.

Type: `Stdlib::Absolutepath`

Default:`undef`

[Back to overview of installem](#attributes)

### puppet_download_mnt_point<a name='installem_puppet_download_mnt_point'>

The base path of all remote files for the defined type or class.

The default value is: `puppet:///modules/ora_install`

Type: `String[1]`

Default:`undef`

[Back to overview of installem](#attributes)

### remote_file<a name='installem_remote_file'>

**DEPRECATED**
This parameter is not being used anymore and will be removed in a future release.

`true`.

Type: `Optional[Boolean]`

Default:`undef`

[Back to overview of installem](#attributes)

### software_library_dir<a name='installem_software_library_dir'>

The directory to use for the software library.

Type: `Stdlib::Absolutepath`

Default:`undef`

[Back to overview of installem](#attributes)

### sysman_password<a name='installem_sysman_password'>

The password to use for sysman.

Type: `Easy_type::Password`


[Back to overview of installem](#attributes)

### temp_dir<a name='installem_temp_dir'>

Directory to use for temporary files.

Type: `Stdlib::Absolutepath`

Default:`'/tmp'`

[Back to overview of installem](#attributes)

### user<a name='installem_user'>

The user used for the specified installation.
The install class will not create the user for you. You must do that yourself.

The default value is: `oracle`

Type: `String[1]`

Default:`'oracle'`

[Back to overview of installem](#attributes)

### version<a name='installem_version'>

The version that is installed in the used Oracle home.

Puppet uses this value to decide on version specific actions.

Type: `Enum['12.1.0.4','12.1.0.5','13.1.0.0','13.2.0.0','13.3.0.0']`

Default:`'12.1.0.5'`

[Back to overview of installem](#attributes)

### weblogic_password<a name='installem_weblogic_password'>

The password to use for WebLogic.

Type: `Easy_type::Password`


[Back to overview of installem](#attributes)

### weblogic_user<a name='installem_weblogic_user'>

The username to use for WebLogic.

The default value is: `weblogic`

Type: `String[1]`

Default:`'weblogic'`

[Back to overview of installem](#attributes)

### zip_extract<a name='installem_zip_extract'>

The specified source file is a zip file that needs te be extracted.
When you specify a value of false, the source attribute must contain a reference to a directory instead of a zip file.

The default value is: `true`

Type: `Boolean`

Default:`true`

[Back to overview of installem](#attributes)
