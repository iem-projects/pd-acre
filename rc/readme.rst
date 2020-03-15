=========
ACRE - rc
=========
-------------------
Data Remote Control
-------------------

:Author: Winfried Ritsch
:Contact: ritsch _at_ algo.mur.at, ritsch _at_ iem.at
:Copyright: winfried ritsch - IEM / algorythmics 2012+
:Version: 2.0rc4

.. _`../docu/acre_title.rst`:  ../docu/acre_title.rst
 

A simple connection library to remotely reflect send/receive parameter as control data.
 
The main target is to replicate a graphical User Interface on another computer for remote control.
Each send receive name has to be registered as parameter to be send/received in the patch.
There is no real master client, each parallel running patches are the same from the connection point of view.
If an parameter is received it is send without being send out again.

The connection management must take care how data is distributed of network.
To keep it simpe as protocol a list is used with connection name prepended to parameter name and data.

It is sufficient to use netsend and netreceive, but also other communication channels like OSC or pipes can be used.


Dependencies
------------

zexy 
 Puredata library, needed for the indexed data storage in text-files.

  
remote concept
..............

New at version 1.1, for easier handling of remote control, eg. over OSC, the remote functionality was added.

rc/par <par> [connection name]
    registers a paramter for remote control, optional for a connection ID
    
rc/connection, rc/ctl
    collects all parameter send  to be transmitted and distributes also parameter received within a connection ``name``.
    Default is the the ``_DEFAULT_`` connection if the connection name is omitted.
    If a parameter is received it is not send out again for feedback protection.


(c) GPL, acre - algorythmics, IEM, winfried ritsch
