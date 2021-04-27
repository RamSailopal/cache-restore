Role Name
=========

This role automates the process of restoring a cache backup on an already installed Cache environment - see https://github.com/RamSailopal/cache.

Devices can also be added to the environment

Requirements
------------

It is assumed that Cache is already installed on either a Red Hat or SuSE derived system as advised by Intersystems

A Cache backup file is required, named cache.cbk and placed in the files folder ready to be sent to the remote machine as part of the restore process

Role Variables
--------------

instname - The name of the Cache instance that is installed

[ Default - TEST ]

mangrp - The management group to that Cache is installed under

[ Default - cacheusr ]

manusr - The management user that Cache is installed under

[ Default - cacheusr ]

cusr - The "normal" user that Cache is installed under

[ Default - cacheusr ]

cmgr - The "normal" group Cache is installed under

[ Default - cacheusr ]


currjourn - The directory used to store journal files

[ Default -  ]

altjourn - The alternative directory used to store journal files

[ Default -  ]

databases - The list of databases to set up

[ Default - ['TEST=/var/test/test/','TEST1=/var/test/test1']]

namespaces - The list of namespaces to set up

[ Default - ['TEST=TEST1','TEST=TEST1']]

Directories - The list of directories to set up

[ Default - ['/var/test/test','/var/test/test1']]

IMPORTANT - To ensure that there are no errors with the restore process, make sure that all of the entries above are consistent and the directories configured in namespaces are also configured in databases and Directories respectively.

devices - Any additional devices to configure

[ Default - ['Test printer=lpr -Prprt10^OTH^P-DEC^^"QW"^^Test Printer^10] ]

Where:

       Test printer - The name of the device
       lpr -Prprt10 - The physical device name
       OTH - Type
       P-DEC - Sub-Type
       QW - Open parameters
       Test Printer - The description of the device
       10 - Alias

backlist - The list of directories to backup, old location to new

[ Default - ['/test/test','/var/test/test,Y','/test/test1','/var/test/test1,Y']]

Example - '/test/test','/var/test/test,Y

          /test/test - Represents the old location of the database
          /var/test/test - Represents the new location where the database should be restored to
          Y - Signifies that "yes" we want to restore this database.

Example Playbook
----------------

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

    - hosts: servers
      role: cache-restore
      instname: CACHE
      ...

License
-------

BSD

Author Information
------------------

Raman Sailopal
