ds - Data Storage
=================

:Author: Winfried Ritsch
:Contact: ritsch@algo.mur.at
:Revision: $Revision: 0.31 2015 $
:Copyright: GPL: IEM/algorythmics, 2012+


A simple data storage library to store different sets of parameters as messages 
in files for defined *domains*. 
The main target is  a simple session management within a Puredata project.


Dependencies
------------

zexy 
 Puredata library, needed for the indexed data storage in text-files.

Concept
-------

Data of `variables`, represented as names in send/receive objects
and called here *parameter* in the objects.
Parameter data is stored in indexed sets of message lists in Pd memory and
can be saved in and loaded from text files.
An *index number* is used to switch between different sets of messages. 
It works like most storage funtionality of sound programs in synthesizer,
including the concept of edit buffer, storage slot and storage files.

Each  indexed list of parameters is associated with an `domain` name.
With this concept, different indexed parameter spaces can be handled in
memory and different files.

For each domain a ``[ds/storage_logic]`` object is needed. 
For controlling this a corresponding GUI object ds/ctl is provided.

Each parameter to be stored has to be registered for a data storage domain with 
either ``[register <domain> <parameter>]``,  where domain is prepended 
to the parameter name, 
or ``[register_map <domain> <parameter>]`` where the domain is not prepended.

To make the parameters exchangeable between domains without edit, 
the second form can be used. If Parameter files should be merged, the first
form is handy to distinguish between domains.
Anyhow this should not be needed in normal operation and should be avoided to 
keep naming in files tight to domains to prevent confusion.

The ``store`` message stores the current parameter set to an internal buffer
to the current storage slot set with the *index*. 
``recall`` recalls the stored parameter set from slot *index*.
The stored parameter sets can saved in an human readable text file.
Each slot index separates  a set, one message per line, prepended by the domain.

``load <filname>;`` loads a filename with a file dialog, ``reload;`` reloads the
last used file.
``save;`` saves the indexed parameter sets to a file popping up a file dialog
and ``resave;`` saves on the file with the last used filename.

The default filename is the domain name (without preceding /).

Note: send/receive names should not contain special characters, except the "/" 
for forming a OSC associated name, legal in for OSC address, 
for future extension.

objects:
--------

main functions
..............

storage_logic.pd <domain>
 the main heart doing storing, loading and holding the parameter  indexed.
 it handles all the commands which are executed on the storage, using an indexed
 msgfile object from the library "zexy".

ctl.pd <domain>
 The controls as GUI of the storage_logic 

register.pd <domain> <parameter>
  registers a parameter for a domain, with domain prepended in the variable name
  and data storage.

register_map.pd <domain> <parameter>
  registers a parameter for a domain, without prepending the domain in the
  variable name, only in the data storage.

register_raw.pd <domain> <parameter>
  registers a parameter for a domain, without prepending the domain in the 
  variable name and in the data storage.


internal helper functions
.........................

msg_pbank.pd
   the indexed msgfile object

#.pd
   comment object: other object can be commented out without losing parameters 
   ( mainly for development, best copied to a path to be used without a prefix)

Notes 
-----

- Will be enhanced with OSC functionality, where registered parameter
  are also send and received over OSC to synchronize Pd Patches in different
  Pd instances. (already done in some projects but interface is not stable enough
  to released now.)

- This module is quite stable and used since several years in different projects

- It will make me happy, of some native English speaker will edit this 
  documentation  and englishfy it.

(c) GPL, algorythmics, IEM, winfried ritsch