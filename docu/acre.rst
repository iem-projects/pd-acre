====
ACRE
====
--------------------------------------------
Algorithmic Composition Realtime Environment
--------------------------------------------

:Author: Winfried Ritsch
:Contact: ritsch _at_ algo.mur.at, ritsch _at_ iem.at
:Version: 2.0-dev
:Copyright: Winfried Ritsch - IEM / algorythmics 2012+

ACRE is collection of Puredata_ Patches, Externals and example applications targeting algorithmic composition in an realtime computermusic environment. 
ACRE is used in open source projects within Atelier Algorythmics AA_ and IEM_ and was made public to be useful for others.

Note: Version of submodules are now independent from version of base modules.

"development version" means in this context:
- structure and namespaces of the library will change if necessary
- ignoring backwards compatibility unless Version "1.x,2.x, ..."  of the library and/or 
module is reached.
- modules already used and tested in various previous projects will be added in extra packages.

Introduction
============

Background
----------

The development of real-time composition and signal processing tools, referring to the procedural thinking in computermusic compositions has been practiced since the beginning of Atelier Algorythmics [AA]_ 1983.
Starting with MIDI-Processing in the 80s and later with micro-controllers in the 90s, the deployment of Pure Data [PureData] as first adapter has become a main base for most pieces.

Within the development of singular applications and libraries for each artwork, each time a copy of such a library has been used for the further development. 
With the art works "Maschinenhalle" [MH]_, "Heptapiano" and "Five Piano Metal Space" [Autopiano], ACRE has become a base library of this ideas, going onward to be a GPL open source library.
The problem of being a specialized library for some pieces is  still virulent and discussed. As an outcome of that only parts which are really more universal will be released with the sanction of the artists and programmers of these pieces.
With the integration of parts of this library for [ICE] project within the IEM, parts has been changed and forked in different other developments, but basic function are implemented now in  the acre repository. Special functions are now split in other modules.

A first version was on private CVS, afterwards subversion, repositories at algo.mur.at and now (May 2015) started to be pushed for public access to git.iem.at and github. 
After a first migration within IEM,  http://git.iem.at/pd/acre is now the chosen master.


Structure of the Library
------------------------

The library is divided in modules. 
Each of these modules should have own test patches and no dependencies on others, except the base modules.
The modules can be used declaring the path to the acre library directory where the modules sit in.
Since base modules are shared within other modules or projects, all changes has to be done with upwards-compatibility in mind.
Library objects, which are abstractions files with the extension .pd, can be  "overwritten" with abstractions in an "overwrite path" declared before the acre module path.
This method is also used for extending functionality within the ACRE library.

eg.:
 `declare -path local_acre:acre` for local overwrite of objects

 `declare -path acre/ds_osc:acre/ds` for local overwrite of ds abstraction providing and osc functionality

names and path naming conventions
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Path-names within acre should be short, since they will be used as namespace 
prefix on objects. 
Mostly the same prefix is used in name definitions in send/receives names or tables, filenames and signals. 
For example in the `mixer` module, aka `mxr`, the master section object is named `mxr/master~ <ID>` and the receive/send parameter for master-mute is `/mxr/master/<id>/mute`.  
Since Version 2.0, the prefix for parameters within base modules has been dropped in favour for a more universal usage in complex projects.

Abstractions which are objects as functions, should be divided in objects for the graphical user interface GUI, DSP processing (without GUI-objects) and data storage:

functions
  should be named within groups starting always with the same prefix and signal processing objects should end with a `~`.
  
  e.g: `mxr/mo/send~.pd`, `mxr/mo/prepost~.pd`, ...

gui objects
  should be named with an additional `_ctl` 
  
  e.g.: `mxr/master/ctl` which is implemented in the file `mxr/master/ctl.pd` or stereo master `mxr/master/stereo_ctl` in `mxr/master/stereo_ctl.pd`

  All GUI-canvas should follow a raster-measurement for "graph on parents" of 50 pixels in vertical and horizontal direction as <width>x<height>, like "150x100", so they can be arranged nicely.
  
data storages
  should be named with an additional `_ds` 
  
  e.g: filename: `mxr/master/ds` or `mxr/master/stereo_ds` 

  Hint: variables in the `ds` name-space are also the send/receive name-space and can be activated as OSC-send [OSC] receive parameter within the ds module 
  (see docu there).

  See more discussion on this subject in the data-storage module ds.

documentation
  In each module an extra documentation file should be placed as ``readme.rst`` and an example and test patch to test the module.
  Mostly the object description are in the object itself, just open it.

Initialization
^^^^^^^^^^^^^^

Each object should be initialized with default values inside the function patch using `acre/initbang`.
Do not use delays or send/receives between `loadbang` or `acre/initbang` and initialization.
All variables in the objects from acre can be reinitialized using `acre/initbang` instead of `loadbang`.

The user application can use a own initialization routine triggered by a delay of 0 or more, mostly used for loading parameters within the `ds-module` after a default initialization with `acre/initbang` or loadbang.

Overview of Modules
-------------------

Dependencies on externals are described in the module folders individually.

All modules in the acre library are depending on the base modules: wherein `mxr` depends on `ds` and `acre` module but `ds` not on `mxr`.

Base Modules
^^^^^^^^^^^^

Common abstractions - acre
""""""""""""""""""""""""""

The idea of this module is to collect abstractions often used in the other modules to prevent redundancy and provide a defined behavior.
Every abstraction in the acre module should not depend on another acre modules.
Since used by all other modules, special care is taken in favor for backward compatibility. 

Note: Names should be different including the acre prefix like: 
`acre/split_filename` with abstraction in other directories.

Data Storage - ds
"""""""""""""""""

Data Storage is a data management library dedicated for storing parameters or settings (send/receive pairs) in indexed sets in memory and files like it can be found on many audio-devices such as synthesizers, mixers and effects.
Settings are collections of messages, which can be send on numbered indexes. 
Each collection can be stored in files. More information can be found in `ds/acre_ds.rst`
This module was historical used in the CUBEmixer since 2000, but is now independent from it.


Mixer - mxr
"""""""""""

The Mixer module provides all functionality for building individual mixer consoles, from simple multichannel outputs to complex spatialization mixers within Pd and providing basic functionality for handling DSP and loadmeter within a master section.

It can be used for programming a flexible audio output interface, a audio input processing with live amplification (if needed), including filter, dynamic effects, buses and includes a monitoring section. 

The mixer module combines the out, in, master and simple effects needed for a channel strip and out processing. 

Dependencies: ds, acre

Ambisonics -Ambisonics
""""""""""""""""""""""

The Ambisonics toolbox is a collection of high level Pd abstraction, to implement Ambisonics integration either in a mixer or compositions or Effects using iem_ambi.
One goal is to easily integrate Ambisonics encoder, decoder and processing for various purposes as modules.
A special feature is patching multichannel signals as buses with arguments.

Waveguides
""""""""""

The simple waveguide library contains blocks to build phyical modeling instruments with waveguides, as also some example instruments.

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

This modules allows note processing and modifications of notes. Notes are not MIDI notes, but can be converted from/to these. This includes a Note(MIDI)-Mixer, time corrections and cleaning, filters and others.

Structure Synthesis
^^^^^^^^^^^^^^^^^^^

lg - loop generator
"""""""""""""""""""

*done for maschinenhalle, to be integrated*

Loop generator for synthesis of loop control messages.

ca - cellular automaton
"""""""""""""""""""""""

*generating CA as external libraries is outsourced at the moment*

Cellular Automaton library for synthesis of CA control messages.

synthesis
^^^^^^^^^

*unreleased, planed for next project*

gen - generators
""""""""""""""""

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
