# ora\_install::db_listener

## Overview

control the oracle db listener state like running,stop,restart

## Attributes



Attribute Name                                                      | Short Description                                                                         |
------------------------------------------------------------------- | ----------------------------------------------------------------------------------------- |
[disable_corrective_change](#db_listener_disable_corrective_change) | Disable the modification of a resource when Puppet decides it is a corrective change.     |
[disable_corrective_ensure](#db_listener_disable_corrective_ensure) | Disable the creation or removal of a resource when Puppet decides is a corrective change. |
[ensure](#db_listener_ensure)                                       | Whether to do something.                                                                  |
[listener_name](#db_listener_listener_name)                         | Listener name.                                                                            |
[name](#db_listener_name)                                           | The title.                                                                                |
[oracle_base_dir](#db_listener_oracle_base_dir)                     | The oracle base folder.                                                                   |
[oracle_home_dir](#db_listener_oracle_home_dir)                     | The oracle home folder.                                                                   |
[os_user](#db_listener_os_user)                                     | The weblogic operating system user.                                                       |
[provider](#db_listener_provider)                                   | resource.                                                                                 |
[refreshonly](#db_listener_refreshonly)                             | refresh mechanism for when a dependent object is changed.                                 |




### disable_corrective_change<a name='db_listener_disable_corrective_change'>

Disable the modification of a resource when Puppet decides it is a corrective change.

(requires easy_type V2.11.0 or higher)

When using a Puppet Server, Puppet knows about adaptive and corrective changes. A corrective change
is when Puppet notices that the resource has changed, but the catalog has not changed. This can occur
for example, when a user, by accident or willingly, changed something on the system that Puppet is
managing. The normal Puppet process then repairs this and puts the resource back in the state as defined
in the catalog. This process is precisely what you want most of the time, but not always. This can
sometimes also occur when a hardware or network error occurs. Then Puppet cannot correctly determine
the current state of the system and thinks the resource is changed, while in fact, it is not. Letting
Puppet recreate remove or change the resource in these cases, is NOT wat you want.

Using the `disable_corrective_change` parameter, you can disable corrective changes on the current resource.

Here is an example of this:

    crucial_resource {'be_carefull':
      ...
      disable_corrective_change => true,
      ...
    }

When a corrective ensure does happen on the resource Puppet will not modify the resource
and signal an error:

        Error: Corrective change present requested by catalog, but disabled by parameter disable_corrective_change
        Error: /Stage[main]/Main/Crucial_resource[be_carefull]/parameter: change from '10' to '20' failed: Corrective change present requested by catalog, but disabled by parameter disable_corrective_change. (corrective)



[Back to overview of db_listener](#attributes)

### disable_corrective_ensure<a name='db_listener_disable_corrective_ensure'>

Disable the creation or removal of a resource when Puppet decides is a corrective change.

(requires easy_type V2.11.0 or higher)

When using a Puppet Server, Puppet knows about adaptive and corrective changes. A corrective change
is when Puppet notices that the resource has changed, but the catalog has not changed. This can occur
for example, when a user, by accident or willingly, changed something on the system that Puppet is
managing. The normal Puppet process then repairs this and puts the resource back in the state as defined
in the catalog. This process is precisely what you want most of the time, but not always. This can
sometimes also occur when a hardware or network error occurs. Then Puppet cannot correctly determine
the current state of the system and thinks the resource is changed, while in fact, it is not. Letting
Puppet recreate remove or change the resource in these cases, is NOT wat you want.

Using the `disable_corrective_ensure` parameter, you can disable corrective ensure present or ensure absent actions on the current resource.

Here is an example of this:

    crucial_resource {'be_carefull':
      ensure                    => 'present',
      ...
      disable_corrective_ensure => true,
      ...
    }

When a corrective ensure does happen on the resource Puppet will not create or remove the resource
and signal an error:

        Error: Corrective ensure present requested by catalog, but disabled by parameter disable_corrective_ensure.
        Error: /Stage[main]/Main/Crucial_resource[be_carefull]/ensure: change from 'absent' to 'present' failed: Corrective ensure present requested by catalog, but disabled by parameter disable_corrective_ensure. (corrective)



[Back to overview of db_listener](#attributes)

### ensure<a name='db_listener_ensure'>

Whether to do something.

Valid values are `start` (also called `running`), `stop` (also called `abort`). 

[Back to overview of db_listener](#attributes)

### listener_name<a name='db_listener_listener_name'>

Listener name.



[Back to overview of db_listener](#attributes)

### name<a name='db_listener_name'>

The title.



[Back to overview of db_listener](#attributes)

### oracle_base_dir<a name='db_listener_oracle_base_dir'>

The oracle base folder.



[Back to overview of db_listener](#attributes)

### oracle_home_dir<a name='db_listener_oracle_home_dir'>

The oracle home folder.



[Back to overview of db_listener](#attributes)

### os_user<a name='db_listener_os_user'>

The weblogic operating system user.



[Back to overview of db_listener](#attributes)

### provider<a name='db_listener_provider'>

The specific backend to use for this `db_listener`
resource. You will seldom need to specify this --- Puppet will usually
discover the appropriate provider for your platform.Available providers are:

db_listener
: 



[Back to overview of db_listener](#attributes)

### refreshonly<a name='db_listener_refreshonly'>

The command should only be run as a
refresh mechanism for when a dependent object is changed.

Valid values are `true`, `false`. 

[Back to overview of db_listener](#attributes)
