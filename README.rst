.. include:: docu/acre_title.rst
.. .. Note: synchronise head with docu/acre_title.rst by hand instead of include

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

"development version" means in this context:
  Structure and namespaces of this library will change if necessary, ignoring backwards compatibility unless Version "1.x"  is reached. Until the "stable" version 1 is reached, modules can change.
  
  Modules already used and tested in various projects and lectures will be added, so this lib can grow quite often in steps.

Introduction
............

ACRE is collection of Puredata_ Patches, Externals and example applications targeting algorithmic composition in an realtime computermusic environment. 
It was dedicated to be integrated in open source projects at Atelier Algorythmics AA_ and IEM_ first hand and now is public to be useful for others.

Modules of this library can and should be used as submodules in projects.

Mission
~~~~~~~

An Algorithmic Composition Real-time Environment (ACRE) should be assembled to enable composers to generate compositions,  computermusic ensembles to share instruments, musicians build and extend their tools and media artists to include realtime computermusic projects in their projects.
As artistic research environment this should evolve from within projects done at the IEM or elsewhere, especially within courses. 
Therefore as an academic development strategy is used: 
"develop during project phase and sharing valuable changes afterwards" ;-) 

The "Algorithmic Composition Realtime Environment" aka ACRE is a library, 
assembling and extending modules to implement pieces for robotic instruments and musicians in computer music realtime environments.
This artistic research environment will also integrate algorithms for generation and analysis for  parameter data-streams for the robotic machinery and other compositions. 
Also it is an documentation of the accumulation on the ideas and algorithms used in compositions and realizations of art installations at IEM and Atelier Algorythmics [AA]_ .

The ACRE tools, as a framework should guarantee a modularized usage of algorithms, enabling parts of algorithms to be moved to realtime operating systems on small computers like embedded devices with modern micro-controllers and used as electronic instruments.

Documentation
-------------

is in docu_ directory and every module directory starting with acre_<module>.rst

.. _docu: docu/

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
