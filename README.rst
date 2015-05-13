.. include:: docu/acre_title.rst

.. ====
.. ACRE
.. ====
.. Algorithmic Composition Realtime Environment
.. --------------------------------------------
.. 
.. :Author: Winfried Ritsch
.. :Contact: ritsch _at_ algo.mur.at, ritsch _at_ iem.at
.. :Revision: 0.31 "development"
.. :Copyright: Winfried Ritsch - IEM / algorythmics 2012+
.. 
 
"development version" means in this context:
    Structure and namespaces of this library will change if necessary,
    ignoring backwards compatibility unless Version "1.x"  is reached.
    Until the "stable" version 1.0 is reached, modules already used  and tested in 
    various projects will be added, so this lib can grow in next month often.

Introduction
............

ACRE is collection of Patches Externals for Puredata_ and helping applications 
targeting algorithmic composition in an realtime computermusic environment. 
It was dedicated to be integrated in open source projects at Atelier 
Algorythmics AA_ or IEM_ and now also to published to be used by others.

Modules of this library can and should be used as submodules in projects.

Mission
~~~~~~~

An Algorithmic Composition Real-time Environment (ACRE) should be assembled to 
enable composers to generate compositions,  computermusic ensembles to share 
instruments, musicians build their tools on this basis and media artists to 
construct projects in the area of computermusic. This artistic research 
environment should evolve from within projects done at the IEM or other place, 
especially from lectures and therefore academic development strategy is used - 
develop during project phase and sharing valuable changes afterwards ;-).

The "Algorithmic Composition Realtime Environment" aka ACRE is  a library, 
assembling and extending modules to implement pieces for robotic instruments 
and musicians in computer music realtime environments.
This artistic research environment will also integrate algorithms for generation
and analysis for  parameter data-streams for the robotic machinery and other 
compositions. 
Also it is  an documentation of the accumulation on the ideas and algorithms 
used in compositions and realizations of art installations at IEM 
and Atelier Algorythmics [AA]_ .

The ACRE tools, as a framework should guarantee a modularized usage of 
algorithms, enabling parts of algorithms to be moved to realtime operating 
systems on small computers like modern micro-controllers and used as electronic 
instruments.

Documentation
-------------

is in docu_ directory and every module directory starting with acre_<module>.rst

.. _docu: docu/

Notes
-----

Updated for Scan_ Project at IEM 2014 used in the lecture "Klangsynthese in 
Echtzeit WS14/15" and now for Waveguide and Tetraspeaker project.


References and Footnotes
------------------------

.. [Puredata] graphical computermusic programming language by Miller Puckette 
   see http://puredata.info/

.. [OSC] Open Sound Control protocoll see (http://opensoundcontrol.org/)

.. [MH] Maschinehalle performance at Steirischer Herbst 2010 
   see http://maschinenhalle.at/

.. [Autopiano] Pieces with robot piano players 
   see http://algo.mur.at/projects/autoklavierspieler/performances/heptapiano

.. [Scan] http://iaem.at/kurse/projekte/scan/


.. .. [AA] Atelier Algorythmics http://algo.mur.at/
.. .. 
.. .. [IEM] Institut for Electronic Music and Acoustics, Art University Graz
.. ..          see http://iem.at/