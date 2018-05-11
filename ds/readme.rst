=========
ACRE - ds
=========
-------------------
Data Storage module
-------------------

:Author: Winfried Ritsch
:Contact: ritsch _at_ algo.mur.at, ritsch _at_ iem.at
:Copyright: winfried ritsch - IEM / algorythmics 2012+
:Version: 1.1a

.. _`../docu/acre_title.rst`:  ../docu/acre_title.rst

 
A simple data storage library to store different sets of parameters as messages in files for defined *domains*. 
The main target is a simple session management as data storage, within a Puredata project.
Added also a remote functionality over OSC or other channels

Dependencies
------------

zexy 
 Puredata library, needed for the indexed data storage in text-files.

Concept
-------

For datastorage, send/receive names are used as `variables` names within Pd.
the data of `variables` are messages. Variables are used to store *parameter* or *settings*.
Parameter data are stored in indexed sets of messages in Pd memory and can be saved in and loaded from text files.
An *index number* is used to switch between different sets of messages, also known as *scenes* and separated in the text file with ``#scene <nr>`` (see the listobject object of zexy for more information).

Datastorage is similar to the storage functionality in hardware devices like synthesizers, mixing consoles, etc including the concept of edit buffer, program numbers and storage in files.

Each storage is associated with an *domain-name*, to operate parallel data storages within a Pd applications.
With the concept of domains and domain-names different indexed parameter name-spaces can be handled in memory and within separate files.

As a naming convention, the address naming used in Open Sound Control (OSC) or in unix file systems, is associated and also used all over the ACRE libraries: 
The domain-name should be used as prefix for variable names in storage and files, (see also register-functions).

For each domain a ``[ds/storage_logic]`` object is needed. 
For controlling this a corresponding GUI object ds/ctl is provided.

Each parameter has to be registered for a data storage domain with either ``[register <domain> <parameter>]``,  where the domain name is prepended to the parameter name, or ``[register_map <domain> <parameter>]`` where the domain is not prepended and ``[register_raw <domain> <parameter>]`` where the domain is also removed from the file storage.

To make the parameters exchangeable between domains without much editing work, the second and third form can be used.
If parameter files should be merged, the first two forms can be used to distinguish different domains.
Anyhow merging data-files should not be needed in most cases and should be avoided to keep naming in files tight to domains to prevent confusion in future and enable easier manual edit.

The ``store`` message stores the current parameter set to an internal buffer to the current storage slot set with the *index*. 
``recall`` recalls the stored parameter set from slot *index*.
The stored parameter sets can saved in an human readable text file.
Each slot index separates  a set, one message per line, prepended by the domain.

``load <filename>;`` loads a filename with a file dialog, ``reload;`` reloads the last used file.
``save;`` saves the indexed parameter sets to a file popping up a file dialog and ``resave;`` saves on the file with the last used filename.

The default filename is the domain name (without preceding /).

Note: send/receive names should not contain special characters and the "/" as separator for forming a OSC associated name and should be also legal in  OSC address names, needed for future extension as OSC connection.

objects:
--------

main functions
..............

storage_logic.pd <domain>
 the main heart doing storing, loading and holding the parameter  indexed.
 it handles all the commands which are executed on the storage, using an indexed `msgfile` object from the library `zexy`.

ctl.pd <domain>
 The controls as GUI of the storage_logic 

register.pd <domain> <parameter>
  registers a parameter for a domain, with domain prepended in the variable name and data storage.

  e.g.: with the domain "/mxr" in storage file the parameter "/master" is named /mxr/master and send/received as "/mxr/master" 
  
register_map.pd <domain> <parameter>
  registers a parameter for a domain, without prepending the domain in the variable name, only in the data storage, separating the variable from domain-name with `::`.

  e.g.: with the domain "/mxr" in storage file the parameter "/master" is named /mxr::/master and send/received as "/master"

register_raw.pd <domain> <parameter>
  registers a parameter for a domain, without prepending the domain in the variable name and in the data storage.

  e.g.: with the domain "/mxr" in storage file the parameter "/master" is named "/master" and send/received as "/master"
  
  
remote concept
..............

New at version 1.1, for easier handling of remote control, eg. over OSC, the remote functionality was added.
This can be used independently fron the ds but is integrated optionial in ds.

remote_par <par> [connection name]
    registers a paramter for remote control, optional for a connection ID
    
remote
    collects all parameter send  to be transmitted and distributes alss parameter received. If a parameter is received it is not send 


  
internal helper functions
.........................

local send receive names are prefixed with _ds, they can be altered vanisch in future, so do not rely on them for your functionality.

msg_pbank.pd
   the indexed msgfile object

#.pd
   comment object: other object can be commented out without losing parameters ( mainly for development, best copied to a path to be used without a prefix)

Notes 
-----

-   This module is quite stable and used since several years in different projects

-   Will be enhanced with OSC functionality, where registered parameter are also send and received over OSC to synchronize Pd Patches in different Pd instances. 
    This was already implemented in some projects, but interface was not stable enough to released now, especially for backwards compatibility and should be implemented with a overloading ds module with ds_osc module.

-   This module was derived from the setting storage done in the CUBEMIXER (2001) project of the IEM and rewritten simplified as a module for later projects at Atelier Algorythmics, Maschinenhalle and courses at the IEM and later used for the ICE-Ensemble project as a base at the IEM. Some forks has been made and out of control, so be carefully with compatibility. 

-   It would make me happy, if some native English speaker will edit this documentation and englishfy it.

additional docu
---------------

for an introduction see `../docu/acre_intro.rst`_ ,
for more documentation explore docu_ .

.. _docu: ../docu/

.. _`../docu/acre_intro.rst`: acre_acre.rst

(c) GPL, acre - algorythmics, IEM, winfried ritsch
