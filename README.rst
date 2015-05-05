====
ACRE
====
Algorithmic Composition Realtime Environment
--------------------------------------------

:Author: Winfried Ritsch
:Contact: ritsch@algo.mur.at
:Revision: $Revision: 0.3 Scan 2014 $
:Copyright: Winfried Ritscg - IEM / algorythmics 2012+


Introduction
............

Mission
~~~~~~~

An Algorithmic Composition Real-time Environment (ACRE) should be assembled to enable composers to generate compositions,  computermusic ensembles to share instruments, musicians build their tools on this basis and media artists to construct projects in the area of computermusic. This artistic research environment should evolve from within projects done at the IEM or other place, especially from lectures and therefore academic development strategy is used - develop during project phase and sharing valuable changes afterwards ;-).

The "Algorithmic Composition Realtime Environment" aka ACRE is  a library, assembling and extending modules to implement pieces for robotic instruments and musicians in computer music realtime environments. This artistic research environment will also integrate algorithms for generation and analysis for parameter data-streams for the robotic machinery and other compositions. Also this library is  an documentation for the accumulation on the ideas and algorithms used in compositions and realisations of art installations at IEM and Atelier Algorythmics [AA]_ .

The ACRE tools, as a framework should guarantee a modularized usage of algorithms, enabling parts of algorithms to be moved to realtime operating systems on small computers like modern micro-controllers and used as electronic instruments.

History
~~~~~~~

The development of real-time composition and signal processing tools, referring to the procedural thinking in computermusic compositions has been done since the beginning of Atelier Algorythmics [AA]_ . Starting with MIDI-Processing in the 80s and later with micro-controllers in the 90s, the deployment of Pure Data [PureData] has become a main base for most pieces done in this area.

After the Development of singular applications and libraries for each artwork, each time a copy of such a library has been used for the further development. With the art works "Maschinenhalle" [MH]_, "Heptapiano" and "Five Piano Metal Space" [Autopiano], ACRE has become a base library of this ideas, going onwards a GPL open source library. The problem of being a specialized library for some pieces,  still is virulent and discussed, so that only parts which are really common will be released with the sanction of the artist which helped develop these pieces.

Structure of the Library
........................

The library is divided in modules. Each of this should have its own test patches and should have no dependencies on others, except the base modules. This modules are included in the projects declaring the path to this library. Since shared within others projects all changes has to be done in a way to stay upwards compatible, and done per project with "overwritten objects" in an additional "overwrite path" declared before the acre path.

eg.:
 declare -path local_acre:acre

naming and conventions
~~~~~~~~~~~~~~~~~~~~~~

Path-names within acre should be short, since they will be used as namespace prefix on objects and mostly the same prefix is used in name definitions like for send/receives names or tables. e.g. in the `out` module, aka `out`, the master object is used as `out/master` and one receive/send parameter is `/out/master/vol`. 

Additional objects should be divided in object for the graphical user interface (GUI) and DSP processing without GUI-objects and data storage for them. 
(see ds-modul for further info)

functions
  should be named within groups starting always with the same prefix
  
  e.g: out/monitor.pd, out/monitor_prepost.pd, ....

gui objects
  should be named with an additional `_ctl` 
  
  e.g.: `out/master_ctl` which is implemented in the file `out/master_ctl.pd` 
  
  gui also should follow the raster with "graph on parents" of "50x50" pixels, like "150x100". 
  
data storages
  should be named with an additional `_ds` 
  
  e.g: filename: out/master_ds.ctl

  Hint: variables in `ds` namespace is also the send/receive namespace which can be activated as OSC-send [OSC] receive parameter within the ds module (see docu there).

documentation
  In each module an extra documentation file should be placed as "acre_<modulename>.rst" and an example and test patch to test the module.


Initialization
~~~~~~~~~~~~~~

Each object should be initialized with default values inside the function patch using loadbang. Do not use delays or send/receives between loadbang and initialization. Also from acre-lib the [initbang] is provided, so all objects from acre can be reinitialized.

In a second step the user application can use for example his initialization with a delay of 0 or more, mostly through loading parameters within the ds-module.

Overview of Modules
-------------------

Dependencies on externals are individual described in this folders. All modules are  mostly depending on the base modules, e.g. `out` depends on `ds` module, which depends on externals like zexy.

Base Modules
............

Common abstractions - acre
~~~~~~~~~~~~~~~~~~~~~~~~~~

The idea is to collect common abstraction needed in other libraries, which should not be duplicated.
Every abstraction in here should not depend on another acre module. Since used by more modules, it so should not change very much in function and should be at least backward compatible. 

Note: Names should not collide if you use the acre prefix like: acre/split_filename with abstraction in other directories.

Data Storage - ds
~~~~~~~~~~~~~~~~~

Used for storing parameters (send/receive pairs) of the modules in an indexed local and file storage, like it can be found
on most audio-devices such as synthesizers, mixers. Settings are colletions of messages, which can be
send on numbered indexes. Every collection has a domain.

Parameter for storage can be selected with registering send/receives (here also referenced as variables) for the setting machine and/or can be used for control via OSC over a data-network.

Output - out
~~~~~~~~~~~~

Used for flexible DA audio interface and MIDI out interface. 
DSP status is also controlled for building a simple out bus for multichannel output, flexible DAC assignes. Features like MUTE Master and Monitoring the signals are also provided.

Depends: ds, acre

Main Modules
............


Input - in
~~~~~~~~~~

For Audio input processing and live amplification (if needed), including Filter and Dynamics and Buses, using the monitoring functionality of out.

Depends: ds, acre, out

controller - midi
~~~~~~~~~~~~~~~~~

Interface for flexible use of MIDI and/or other controllers

audio processing
................

used for processing audio data

an
~~

Analysis modules for converting audio in messages
 
fx  
~~

effects for playback and processing

gen 
~~~

generators like sample-player, sub generators, ....


structure synthesis
===================

This modules can do note processing and modifications of notes. Notes are not MIDI notes, but can be converted from/to these. This includes Note-Mixer, time corrections and cleaning.

np
~~

note processor for filtering etc.

lg
~~

loop generator for synthesis

ca
~~

cellular automata (to be done)


synthesis
=========

rep 
~~~

replicator is a concept which is derived from loop processors, where stored material can be replicated 
with different paramter like notes or grains.

visualization
.............

vi
~~

Visualization of Messages in the OpenGL domain, especially over monitors for musician and dancer. To be enhanced and reworked in near future for more general usage.

Notes
-----

Updated for Scan_ Project at IEM 2014 used in the lecture Klangsynthese in Echtzeit: 


References and Footnotes
------------------------

.. [PureData] graphical computermusic programming language by Miller Puckette (http://puredata.info/)

.. [OSC] Open Sound Control protocoll see (http://opensoundcontrol.org/)

.. [MH] Maschinehalle performance at Steirischer Herbst 2010 http://maschinenhalle.at/

.. [Autopiano] Pieces with robot piano players see http://algo.mur.at/projects/autoklavierspieler/performances/heptapiano

.. [AA] Atelier Algorythmics http://algo.mur.at/

.. _Scan: http://iaem.at/kurse/projekte/scan/
