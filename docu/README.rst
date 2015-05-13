.. include:: acre_title.rst


:Author: Winfried Ritsch
:Contact: ritsch _at_ algo.mur.at, ritsch _at_ iem.at
:Copyright: winfried ritsch - IEM / algorythmics 2012+
:Revision: see `../docu/acre_title.rst`_

.. _`../docu/acre_title.rst`:  ../docu/acre_title.rst


Installation
============

Nothing to compile at the moment.

Copy the module folders in ACRE to one of the PD search paths either global
or local in your project or add a path to this directory with 
``[declare -path acre]`` (or deprecated in the settings).

:main document: acre.rst_


.. include:: acre_intro.rst 


Documentation
=============

can be compiled within the docu folder searching for sub-Documents
in the module folders for files matching ``acre_<module id>.rst``
with ``docutils`` see RestructuredText_ .

Following sectioning is recommended::

    # with overline, for parts
    * with overline, for chapters
    =, for sections
    -, for subsections
    ^, for subsubsections
    ", for paragraphs

.. _acre.rst: acre.rst

.. _RestructuredText:  http://docutils.sourceforge.net/rst.html