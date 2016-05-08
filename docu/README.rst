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

can be compiled within the ``docu`` folder with ``docutils`` , including sub-documents in the module folders name ``readme.rst``
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