# ora\_install::db_directory_structure

## Overview

add all the directories needed by the oracle db or asm installation

## Attributes



Attribute Name                                                     | Short Description             |
------------------------------------------------------------------ | ----------------------------- |
[create_orainst_only](#db_directory_structure_create_orainst_only) | Only create oraInst.loc file. |
[download_dir](#db_directory_structure_download_dir)               | The download folder.          |
[ensure](#db_directory_structure_ensure)                           | Whether to do something.      |
[name](#db_directory_structure_name)                               | The title.                    |
[ora_inventory_dir](#db_directory_structure_ora_inventory_dir)     | The oracle inventory folder.  |
[oracle_base_dir](#db_directory_structure_oracle_base_dir)         | The oracle base folder.       |
[os_group](#db_directory_structure_os_group)                       | The operating system group.   |
[os_user](#db_directory_structure_os_user)                         | The operating system user.    |
[provider](#db_directory_structure_provider)                       | resource.                     |




### create_orainst_only<a name='db_directory_structure_create_orainst_only'>

Only create oraInst.loc file.

Valid values are `true`, `false`. 

[Back to overview of db_directory_structure](#attributes)

### download_dir<a name='db_directory_structure_download_dir'>

The download folder.



[Back to overview of db_directory_structure](#attributes)

### ensure<a name='db_directory_structure_ensure'>

Whether to do something.

Valid values are `present`. 

[Back to overview of db_directory_structure](#attributes)

### name<a name='db_directory_structure_name'>

The title.



[Back to overview of db_directory_structure](#attributes)

### ora_inventory_dir<a name='db_directory_structure_ora_inventory_dir'>

The oracle inventory folder.



[Back to overview of db_directory_structure](#attributes)

### oracle_base_dir<a name='db_directory_structure_oracle_base_dir'>

The oracle base folder.



[Back to overview of db_directory_structure](#attributes)

### os_group<a name='db_directory_structure_os_group'>

The operating system group.



[Back to overview of db_directory_structure](#attributes)

### os_user<a name='db_directory_structure_os_user'>

The operating system user.



[Back to overview of db_directory_structure](#attributes)

### provider<a name='db_directory_structure_provider'>

The specific backend to use for this `db_directory_structure`
resource. You will seldom need to specify this --- Puppet will usually
discover the appropriate provider for your platform.Available providers are:

db_directory_structure
: 



[Back to overview of db_directory_structure](#attributes)
