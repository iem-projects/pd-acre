====
ACRE
====
--------------------------------------------
Algorithmic Composition Realtime Environment
--------------------------------------------

:Author: Winfried Ritsch
:Contact: ritsch _at_ algo.mur.at, ritsch _at_ iem.at
:Copyright: winfried ritsch - IEM / algorythmics 2012+
:Revision: see `acre.rst`_

Installation
============

Nothing to compile at the moment.

Checkout from git or download it use deken to install it.

Copy the module folders in ACRE to one of the PD search paths either global
or local in your project or add a path to this directory with 
``[declare -path acre]`` (or, deprecated, in the settings).

Documentation
=============

can be compiled within the ``docu`` folder with ``docutils`` here as `acre.rst` and in the module folders named ``<modulename>.rst``
(see RestructuredText_ ).

Section title hierarchy recommended::

    # with overline, for parts
    * with overline, for chapters
    =, for sections
    -, for subsections
    ^, for subsubsections
    ", for paragraphs

.. _acre.rst: acre.rst

.. _RestructuredText:  http://docutils.sourceforge.net/rst.html
