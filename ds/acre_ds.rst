ds - Data Storage
=================

:Author: Winfried Ritsch
:Contact: ritsch@algo.mur.at
:Revision: $Revision: 0.3 Scan 2014 $
:Copyright: GPL: IEM/algorythmics, 2012+

A simple data storage library to store different sets of parameters as messages 
for a project in different files defined as domain.

Note: to be enhanced with OSC functionality, 
 (done in some projects but not stable to release now.)

Dependencies
------------

zexy lib is needed for the indexed storage of data storage and in text-files.

Concept
-------

Variables, represented as send/receives names, are stored in sets as an indexed 
list in RAM and can be saved as and loaded from text files.
A *index number* is used to switch between different sets of messages. 

For each domain a $ds/storage_logic$ object is needed. For controlling this a 
corresponding
GUI object ds/ctl is provided.

Each parameter to be stored hast to be registered for a data storage domain with 
either
register <domain> <parameter>  where domain is perpended to the parameter name
or register_map <domain> <parameter> where the domain is not perpended on 
recall.

If the parameters should be exchangeable between domains, the second form can be 
used. However this also can be achieved by manual renaming the domain in there. 
Anyhow this should not be needed in normal operation and should be avoided to 
keep naming in files tight to domains so they cannot be confused.

The "store" message stores the current parameter set to an internal buffer on 
the
current index "nr". "recall" recalls the stored parameter set. The "stored" 
parameter sets can saved in an easy readable text file, with slot numbers and a 
message per line, to be loaded from this.

"load" loads a filename with a file dialog, "reload" loads the last filename 
again. 
"save" saves the indexed parameter sets to a file with a file dialog and 
"resave"
saves it again to the same file.

A default filename is the domain name (without preceding /).

Note: send/receive names should not contain special characters, except the "/" 
for
forming a OSC like name.

objects:
--------

objects of library:
...................

storage_logic.pd <domain>
 the main heart doing storing, loading and holding the parameter  indexed.
 it handles all the commands which are executed on the storage, using an indexed
 msgfile object from the library "zexy".

ctl.pd <domain>
 The controls as GUI of the storage_logic 

register.pd <domain> <parameter>
  registers a parameter for a domain, with domain prepended in the storage-file.


register_map.pd <domain> <parameter>

  registers a parameter for a domain, without prepending the domain in the 
variable name, only in the storage and storage files.

internal helper functions
.........................

msg_pbank.pd
   the indexed msgfile object

acre_ds.rst
   this file

#.pd
   trick object, object can be commented out without losing parameters (for 
developing)
   copy to a path to be found without a prefix path to use more easily

(c) GPL, algorythmics,  winfried ritsch