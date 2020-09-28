# ora\_install::ora_tab_entry

## Overview

With this type you can manage entries in the systems oratab file.

## Example

Here is an example on how to use this:

  ora_tab_entry { 'MYDB':
      ensure      => 'present',
      comment     => 'My own database',
      oracle_home => '/u01/app/oracle/product/12.2.0.1/db_home1',
      startup     => 'Y',
    }

## Attributes



Attribute Name                                                        | Short Description                                                                         |
--------------------------------------------------------------------- | ----------------------------------------------------------------------------------------- |
[comment](#ora_tab_entry_comment)                                     | The comments belonging to this database sid.                                              |
[disable_corrective_change](#ora_tab_entry_disable_corrective_change) | Disable the modification of a resource when Puppet decides it is a corrective change.     |
[disable_corrective_ensure](#ora_tab_entry_disable_corrective_ensure) | Disable the creation or removal of a resource when Puppet decides is a corrective change. |
[ensure](#ora_tab_entry_ensure)                                       | The basic property that the resource should be in.                                        |
[name](#ora_tab_entry_name)                                           | The sid of the database entry you want to register in the oratab.                         |
[oracle_home](#ora_tab_entry_oracle_home)                             | The Oracle home directory to be registered for this databse sid.                          |
[provider](#ora_tab_entry_provider)                                   | resource.                                                                                 |
[startup](#ora_tab_entry_startup)                                     | Determines if this database will be started at boot time.                                 |




### comment<a name='ora_tab_entry_comment'>

The comments belonging to this database sid. This is a readonly attribute. You cannot
add or change comments using this property.



[Back to overview of ora_tab_entry](#attributes)

### disable_corrective_change<a name='ora_tab_entry_disable_corrective_change'>

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



[Back to overview of ora_tab_entry](#attributes)

### disable_corrective_ensure<a name='ora_tab_entry_disable_corrective_ensure'>

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



[Back to overview of ora_tab_entry](#attributes)

### ensure<a name='ora_tab_entry_ensure'>

The basic property that the resource should be in.

Valid values are `present`, `absent`. 

[Back to overview of ora_tab_entry](#attributes)

### name<a name='ora_tab_entry_name'>

The sid of the database entry you want to register in the oratab.



[Back to overview of ora_tab_entry](#attributes)

### oracle_home<a name='ora_tab_entry_oracle_home'>

The Oracle home directory to be registered for this databse sid.



[Back to overview of ora_tab_entry](#attributes)

### provider<a name='ora_tab_entry_provider'>

The specific backend to use for this `ora_tab_entry`
resource. You will seldom need to specify this --- Puppet will usually
discover the appropriate provider for your platform.Available providers are:

simple
: Manage /etc/oratab entries



[Back to overview of ora_tab_entry](#attributes)

### startup<a name='ora_tab_entry_startup'>

Determines if this database will be started at boot time.

Valid values are `Y`, `N`. 

[Back to overview of ora_tab_entry](#attributes)
