====
ACRE
====
Algorithmic Composition Realtime Environment
--------------------------------------------

:Author: Winfried Ritsch
:Contact: ritsch _at_ algo.mur.at, ritsch _at_ iem.at
:Copyright: winfried ritsch - IEM / algorythmics 2012+
:Revision: see `docu/acre_title.rst`_
:Master: https://git.iem.at/pd/acre

.. _`docu/acre_title.rst`:  docu/acre_title.rst


Introduction
............

ACRE is collection of Puredata_ patches organized in modules with example applications targeting algorithmic composition in an realtime computermusic environment. 
ACRE is used in open source projects within Atelier Algorythmics AA_ and IEM_  and was made public to be useful for others.

Modules of this library can and should be used as sub-modules in projects. 

Mission
~~~~~~~

An Algorithmic Composition Real-time Environment (ACRE) using Puredata should be assembled to enable composers to generate compositions,  computermusic ensembles to share instruments, musicians to build and extend their tools and media artists to include realtime computermusic in their projects.
As artistic research environment this should evolve from within projects and courses, mostly done at the IEM_. 
Therefore the academic development strategy is used: 
"develop during project phase and publish and share valuable parts afterwards" ;-) 

The "Algorithmic Composition Realtime Environment" aka ACRE is a library, 
assembling and extending modules to implement pieces for robotic instruments and musicians in computer music realtime environments.
This artistic research environment will also integrate algorithms for generation and analysis for parameter data-streams for robotic machinery and algorithmic compositions.
Also it is an documentation of an accumulation on ideas and algorithms used in compositions and realizations of art installations at IEM and Atelier Algorythmics [AA]_ .

Documentation
-------------

is in the docu_ directory and in every module directory named acre_<module>.rst

.. _docu: docu/

Installation and usage
----------------------

Installation methods:

- download and unpack the directory acre in a Pd search path of your patch.

- clone from git in one of your PD-paths::

  git clone https://git.iem.at/pd/acre

- Use deken: search for 'acre', download and install.

Best practice to use it to set the `-stdpath` or '-path' to the base directory of acre adding a declare object in the main patch::

 [declare -stdpath acre]
 
Afterwards all objects can referenced by <module>/<object> eg::

 [acre/initbang]


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