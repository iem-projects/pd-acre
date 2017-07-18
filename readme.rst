====
ACRE
====
Algorithmic Composition Realtime Environment
--------------------------------------------

:Author: Winfried Ritsch
:Contact: ritsch _at_ algo.mur.at, ritsch _at_ iem.at
:Copyright: winfried ritsch - IEM / algorythmics 2012+
:Version: 2.0-rc3
:Master: https://git.iem.at/pd/acre

Introduction
............

ACRE is collection of Puredata_ patches organized in modules with example applications targeting algorithmic composition in an realtime computermusic environment. 
ACRE is used in open source projects within Atelier Algorythmics AA_ and IEM_  and was made public to be useful for others.


Mission
~~~~~~~

An Algorithmic Composition Real-time Environment (ACRE) using Puredata should be assembled, to enable composers to create compositions,  computermusic ensembles to share instruments, musicians to build and extend their tools and media artists to include realtime computermusic in their projects.
As an artistic research environment ACRE should evolve from within projects and courses, mostly done at the IEM_.
Therefore an academic development strategy is used: 
"develop during project phase and publish and share valuable parts afterwards" ;-) 

The "Algorithmic Composition Realtime Environment" aka ACRE is a library, 
assembling and extending modules to implement pieces for robotic instruments and musicians in computer music realtime environments.
This artistic research environment will also integrate algorithms for generation and analysis of data-streams for robotic machinery and algorithmic compositions.
As an accumulation of ideas and algorithms used in compositions and realizations of art installations at IEM and Atelier Algorythmics [AA]_  it is also an documentation of this development process.

Documentation
-------------

goes in the docu_ directory and in every module directory named ``readme.rst`` and ``<modulename>.rst`` 

.. _docu: docu/

base modules
------------

`basemodule acre`_
 base module for common used functions and transformations.

.. _`basemodule acre`: acre/readme.rst

ds_
 data storage

.. _ds: ds/readme.rst

mxr_
 general mixer and audio routing functions

.. _mxr: mxr/readme.rst


Further modules see ``acre-<modulename>`` at  https://git.iem.at/pd/ .


Installation and usage
----------------------

Installation methods:

- download and unpack the directory acre in a Pd search path of your patch.

- clone from git in one of your PD-paths::

   https://git.iem.at/pd/acre

- Use deken: search for 'acre', download and install.

Best practice is to set the `-stdpath` or '-path' to the base directory of acre adding a declare object in the main patch::

 [declare -stdpath acre]
 
so objects can referenced by the namespace of the module: <module>/<object> eg::

 [acre/initbang]

Modules from seperate packages like `acre-wg` should be placed within the basemodule, as
module without àcre-`prefix eg.: `acre/wg` 

For development, these module namespaces are ignored by git within .gitignore , to integrate them
execute within the acre module::

    https://git.iem.at/pd/acre-amb -> amb
    https://git.iem.at/pd/acre-wg -> wg

eg. cd to acre bas lib directory and do a::

    git clone  https://git.iem.at/pd/acre-amb.git amb
    git clone  https://git.iem.at/pd/acre-wg.git wg

History
-------

- initiated by Winfried 2007 derived from previous pd-works
- extended for Autoklavier Konzerts, Metalspace and others
- extended for performance Maschinenhalle 2010 
- extended for lecture "Klangsynthese in Echtzeit" since 2012
- cleaned and shrinked for open-source publish of documented parts
- enhanced within the [scan] Project at IEM 2014
- Extended in the courses using Waveguide- and Tetraspeaker project.
- Integrated parts of it into the [ICE] development 2010-
- published for Ambisonics Mixer Tools development for Studios at IEM. 2015
- published Waveguide library after editing for teaching purposes  IEM 2016
- split modules amb and wg to separate git repos for better development and distribution
- Enhanced mxr with better parameter naming scheme.
- moved to 2.0 with split

References and Footnotes
------------------------

.. [ACRE] Algorithmic Composition Realtime Environment 

.. [Puredata] graphical computermusic programming language by Miller Puckette 
   see http://puredata.info/, http://msp.ucsd.edu/

.. [OSC] Open Sound Control protocoll see (http://opensoundcontrol.org/)

.. [MH] Maschinehalle performance at Steirischer Herbst 2010 
   see http://maschinenhalle.at/

.. [Autopiano] Pieces with robot piano players 
   see http://algo.mur.at/projects/autoklavierspieler/performances/heptapiano

.. [scan] http://iaem.at/kurse/projekte/scan/

.. [AA] Atelier Algorythmics http://algo.mur.at/

.. [IEM] Institut for Electronic Music and Acoustics, Art University Graz
         see http://iem.at/
         
.. [ICE] ICE - IEM Computermusic Ensemble:  http://iaem.at/projekte/ice
