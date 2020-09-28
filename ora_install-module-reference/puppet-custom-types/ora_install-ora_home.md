# ora\_install::ora_home

## Overview

This resource allows you to manage Oracle homes.

## Attributes



Attribute Name                                                   | Short Description                                                                         |
---------------------------------------------------------------- | ----------------------------------------------------------------------------------------- |
[asm_group](#ora_home_asm_group)                                 | The oracle ASM group
                                                                     |
[dba_group](#ora_home_dba_group)                                 | The oracle DBA group
                                                                     |
[disable_corrective_change](#ora_home_disable_corrective_change) | Disable the modification of a resource when Puppet decides it is a corrective change.     |
[disable_corrective_ensure](#ora_home_disable_corrective_ensure) | Disable the creation or removal of a resource when Puppet decides is a corrective change. |
[ensure](#ora_home_ensure)                                       | The basic property that the resource should be in.                                        |
[grid](#ora_home_grid)                                           | eather the home needs to be a grid home
                                                  |
[location](#ora_home_location)                                   | The path e.g.                                                                             |
[name](#ora_home_name)                                           | The name
                                                                                 |
[oper_group](#ora_home_oper_group)                               | The oracle oper group.                                                                    |
[oracle_base](#ora_home_oracle_base)                             | The oracle_base directory.                                                                |
[provider](#ora_home_provider)                                   | resource.                                                                                 |
[source](#ora_home_source)                                       | A source directory, but can also contain a zip or a tar file.                             |
[tmp_dir](#ora_home_tmp_dir)                                     | The tmp extract directory of the patch.                                                   |
[user](#ora_home_user)                                           | The oracle user.                                                                          |




### asm_group<a name='ora_home_asm_group'>

The oracle ASM group



[Back to overview of ora_home](#attributes)

### dba_group<a name='ora_home_dba_group'>

The oracle DBA group



[Back to overview of ora_home](#attributes)

### disable_corrective_change<a name='ora_home_disable_corrective_change'>

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



[Back to overview of ora_home](#attributes)

### disable_corrective_ensure<a name='ora_home_disable_corrective_ensure'>

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



[Back to overview of ora_home](#attributes)

### ensure<a name='ora_home_ensure'>

The basic property that the resource should be in.

Valid values are `present`, `absent`. 

[Back to overview of ora_home](#attributes)

### grid<a name='ora_home_grid'>

eather the home needs to be a grid home

Valid values are `true`, `false`. 

[Back to overview of ora_home](#attributes)

### location<a name='ora_home_location'>

The path e.g. location of the Oracle home



[Back to overview of ora_home](#attributes)

### name<a name='ora_home_name'>

The name



[Back to overview of ora_home](#attributes)

### oper_group<a name='ora_home_oper_group'>

The oracle oper group.



[Back to overview of ora_home](#attributes)

### oracle_base<a name='ora_home_oracle_base'>

The oracle_base directory.



[Back to overview of ora_home](#attributes)

### provider<a name='ora_home_provider'>

The specific backend to use for this `ora_home`
resource. You will seldom need to specify this --- Puppet will usually
discover the appropriate provider for your platform.Available providers are:

simple
: Manage ora_home



[Back to overview of ora_home](#attributes)

### source<a name='ora_home_source'>

A source directory, but can also contain a zip or a tar file.

This parameter can contain the following types of values:

* `puppet:` URIs, which point to files in modules or Puppet file server
mount points.
* Fully qualified paths to locally available files (including files on NFS
shares or Windows mapped drives).
* `file:` URIs, which behave the same as local file paths.
* `http:` URIs, which point to files served by common web servers

The normal form of a `puppet:` URI is:

`puppet:///modules/<MODULE NAME>/<FILE PATH>`

This will fetch a file from a module on the Puppet master (or from a
local module when using Puppet apply). Given a `modulepath` of
`/etc/puppetlabs/code/modules`, the example above would resolve to
`/etc/puppetlabs/code/modules/<MODULE NAME>/files/<FILE PATH>`.

## Container file

When the file is a container file, it will automaticaly be extracted. At this point in
time the follwoing container types are supported:

- zip
- tar

## Compressed files

When the file is compressed, it will be uncompressed before beeing procesed further. This means that for example
a file `https://www.puppet.com/files/all.tar.gz` will be uncompressed before being unpackes with `tar`

## Examples

Here are some examples:

### Regular directories

    ... { '...':
      ...
      source  => '/home/software',
      ...
    }

The `/home/software` will be used by the custom type. Other Puppet code must make sure the directory contains the right files.

### A puppet url containing a zip file

    ... { '...':
      ...
      source  => 'puppet:///modules/software/software.zip',
      tmp_dir => '/tmp/mysoftware'
      ...
    }

The `software.zip` file will be fetched from the puppet server software module and put in `/tmp/mysoftware`, it will be unzipped and used for the actions
in the custom type. The file will be temporary put in


### A http url containing a tar file

... { '...':
  ...
  source  => 'http:///www.enterprisemodules.com/software/software.tar',
  tmp_dir => '/tmp/mysoftware'
  ...
}


The `software.tar` file will be fetched from the named web server and put in `/tmp/mysoftware`, it will be untarred and
used for the actions in the custom type.

### A file url fcontaining a compressed tar file

... { '...':
  ...
  source  => 'file:///nfsshare/software/software.tar.Z',
  tmp_dir => '/tmp/mysoftware'
  ...
}

The `software.tar.Z` file will be fetched from the namedd irectory, it will be uncompressed and then untarred on and put in `/tmp/mysoftware`
and used for the actions in the custom type.



[Back to overview of ora_home](#attributes)

### tmp_dir<a name='ora_home_tmp_dir'>

The tmp extract directory of the patch.



[Back to overview of ora_home](#attributes)

### user<a name='ora_home_user'>

The oracle user.



[Back to overview of ora_home](#attributes)
