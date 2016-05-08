Introduction
============

Background
----------

The development of real-time composition and signal processing tools, referring to the procedural thinking in computermusic compositions has been done since the beginning of Atelier Algorythmics [AA]_ 1983.
Starting with MIDI-Processing in the 80s and later with micro-controllers in the 90s, the deployment of Pure Data [PureData] has become a main base for most pieces done in this area.

Within the development of singular applications and libraries for each artwork, each time a copy of such a library has been used for the further development. 
With the art works "Maschinenhalle" [MH]_, "Heptapiano" and "Five Piano Metal Space" [Autopiano], ACRE has become a base library of this ideas, going onward to be a GPL open source library.
The problem of being a specialized library for some pieces is  still virulent and discussed. As an outcome of that only parts which are really common will be released with the sanction of the artist and programmers of these pieces.
With the integration of parts of this library for [ICE] projection within the IEM, parts has been changed
and forked in different other developments, but basic function stayed now in  an central repository the acre.

First version was on private CVS then subversion repositories at algo.mur.at and now (May 2015) started to be pushed for public access to github. After migration of all pd libraries of IEM,  http://git.iem.at/pd/acre is the choosen master.


Structure of the Library
------------------------

The library is divided in modules. 
Each of these modules should have own test patches and no dependencies on others, except the base modules acre and ds. 
This modules are included in the projects declaring the path to this library. Since shared within others projects all changes has to be done with upwards compatibility in mind.
Library objects, which are abstractions files with the extension .pd, can be  "overwritten" with abstractions in an "overwrite path" declared before the acre module path. This can also be used for extending functionality within the ACRE library

eg.:
 `declare -path local_acre:acre` for local overwrite of objects

 `declare -path acre/ds_osc:acre/ds` for local overwrite of ds abstraction providing and osc functionality

names and path naming conventions
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Path-names within acre should be short, since they will be used as namespace 
prefix on objects. 
Mostly the same prefix is used in name definitions in send/receives names or tables, filenames and signals. 
For example in the `out` module, aka `out`, the master section object is named `out/master` and the receive/send parameter  for master-volume is `/out/master/vol`. 

abstractions which are objects as functions, should be divided in objects for the graphical user interface GUI, DSP processing (without GUI-objects) and data storage:

functions
  should be named within groups starting always with the same prefix
  
  e.g: `out/monitor.pd`, `out/monitor_prepost.pd`, ...

gui objects
  should be named with an additional `_ctl` 
  
  e.g.: `out/master_ctl` which is implemented in the file `out/master_ctl.pd` 

  Additional GUI-canvas should follow a raster-measurement with "graph on parents" of 50 pixels in vertical and horizontal direction as <width>x<height>, like "150x100". 
  
data storages
  should be named with an additional `_ds` 
  
  e.g: filename: out/master_ds

  Hint: variables in the `ds` name-space are also the send/receive name-space and can be activated as OSC-send [OSC] receive parameter within the ds module 
  (see docu there).

  See more discussion on this subject in the data-storage module ds.

documentation
  In each module an extra documentation file should be placed as ``readme.rst`` and an example and test patch to test the module.
  Mostly the object description are in their object, just open them.

Initialization
^^^^^^^^^^^^^^

Each object should be initialized with default values inside the function patch using `acre/initbang`.
Do not use delays or send/receives between `loadbang` oe `acre/initbang` and initialization.
Also from acre-lib the `[initbang]` is provided, so all variables in the objects from acre can be reinitialized.

The user application can use, for example his initialization routine started with a delay of 0 or more, mostly through loading parameters within the `ds-module`.

Overview of Modules
-------------------

Dependencies on externals are described in the module folders individually.

All modules are  mostly depending on the base modules, e.g. `mxr` depends on `ds` module, which depends on externals like `zexy`.

Base Modules
^^^^^^^^^^^^

Common abstractions - acre
""""""""""""""""""""""""""

The idea is to collect common abstraction often needed in the different modules to prevent redundancy.
Every abstraction in the acre module should not depend on another acre module.
Since used by more modules, care is taken in favor for backward compatible. 

Note: Names should not collide if you use the acre prefix like: 
`acre/split_filename` with abstraction in other directories.

Data Storage - ds
"""""""""""""""""

Data Storage is a Data Management library used for storing parameters or settings (send/receive pairs) in indexed sets in RAM and files, like it can be found on many audio-devices such especially synthesizers, mixers and effects.
Settings are collections of messages, which can be send on numbered indexes. 
Each collection can be stored in files. See more in `ds/acre_ds.rst`


Mixer - mxr
"""""""""""

The Mixer module provides all functionality for building individual mixer consoles, from simple multichannel outputs to complex spatialization mixers within Pd.

It can be used for programming a flexible audio output interface, a audio input processing with live amplification (if needed), including filter, dynamic effects, buses and includes a monitoring section. 

The mixer module now combines the out, in, fx and other modules of older implementations in one module. 

Depends: ds, acre

Ambisonics -Ambisonics
""""""""""""""""""""""

The Ambisonics toolbox is a collection of high level Pd abstraction, to implement Ambisonics integration either in a mixer or compositions or Effects using iem_ambi.
One goal is to easily integrate Ambisonics encoder, decoder and processing for various purposes as modules.
A special feature is patching multichannel signals as buses with arguments.


Control Modules
^^^^^^^^^^^^^^^

midi - controller
"""""""""""""""""

*unreleased, planed for next project*

Interface for flexible use of MIDI and/or other controllers including MIDI out interface. 
Functionality for OSC-controllers should be integrated.

an - Analysis
"""""""""""""

*done for maschinenhalle, to be integrated*

Analysis modules for converting audio in messages in different domains like Piano Player.

fx - effects lib
""""""""""""""""

*done for heptapiano, to be integrated*

effects for playback and processing of sounds for using transducers in and out to physical objects.

np - note processor
"""""""""""""""""""

*done for maschinenhalle, to be integrated*

This modules can do note processing and modifications of notes. Notes are not MIDI notes, but can be converted from/to these. This includes a Note-Mixer, time corrections and cleaning, filters and others.

Structure Synthesis
^^^^^^^^^^^^^^^^^^^

lg - loop generator
"""""""""""""""""""

*done for maschinenhalle, to be integrated*

Loop generator for synthesis of loop control messages.

ca - cellular automaton
"""""""""""""""""""""""

*for scan, external libraries so outsourced at the moment*

Cellular Automaton library for synthesis of CA control messages.

synthesis
^^^^^^^^^

*unreleased, planed for next project*

gen - genrerators
"""""""""""""""""

Generators like sample-player, sub generators, ....

rep - replicator
""""""""""""""""

*unreleased, done for "differenz/wiederholung" DW series*

Replicator is a concept which is derived from loop processors, where stored material can be replicated with different parameter like notes or grains.

visualization
^^^^^^^^^^^^^

vi - optic signaling and conducting
"""""""""""""""""""""""""""""""""""

*unreleased, done for "maschinenhalle conductor views" series*

Visualization of Messages in the OpenGL domain, especially over monitors for musician and dancer. To be enhanced and reworked in near future for more general usage.

References and Footnotes
^^^^^^^^^^^^^^^^^^^^^^^^

.. [PureData] graphical computermusic programming language by Miller Puckette, see http://puredata.info/

.. [OSC] Open Sound Control protocol, see http://opensoundcontrol.org/

.. [MH] Maschinehalle performance at Steirischer Herbst 2010 
        see http://maschinenhalle.at/


.. [Autopiano] Pieces with robot piano players 
   see http://algo.mur.at/projects/autoklavierspieler/performances/heptapiano

.. [Scan] Project "Scan" see http://iaem.at/kurse/projekte/scan/

.. [AA] Atelier Algorythmics http://algo.mur.at/

.. [IEM] Institut for Electronic Music and Acoustics, Art University Graz
         see http://iem.at/

.. [ICE] ICE - IEM Computermusic Ensemble:  http://iaem.at/projekte/ice