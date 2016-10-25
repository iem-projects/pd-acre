====
ACRE
====
--------------------------------------------
Algorithmic Composition Realtime Environment
--------------------------------------------

:Author: Winfried Ritsch
:Contact: ritsch _at_ algo.mur.at, ritsch _at_ iem.at
:Version: 1.01
:Copyright: Winfried Ritsch - IEM / algorythmics 2012+

ACRE is collection of Puredata_ Patches, Externals and example applications targeting algorithmic composition in an realtime computermusic environment. 
It was dedicated to be integrated in open source projects at Atelier Algorythmics AA_ and IEM_ first hand and now is public to be useful for others.

Already integrated modules:
   acre ds mxr amb wg

Pending modules:
   midi an fx np lg ca gen rep vi

Note: Version of submodules now indepent from whole Version, since some can be still in development phase, but base modules now in release.

Some new modules maybe "development version < 1.0"

"development version" means in this context:
-    Structure and namespaces of this library will change if necessary,
-    ignoring backwards compatibility unless Version "1.x"  of the library and/or 
     module is reached.
-    Modules already used and tested in various previous projects will be added, 
     so this lib may grow.

more on these names in ./acre_intro.rst

.. [AA] Atelier Algorythmics http://algo.mur.at/

.. [IEM] Institut for Electronic Music and Acoustics, Art University Graz
         see http://iem.at/

.. [Puredata] graphical computermusic programming language, see http://puredata.info
