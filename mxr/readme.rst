==========
ACRE - mxr
==========
------------
Mixer module
------------

:Author: Winfried Ritsch
:Contact: ritsch _at_ algo.mur.at, ritsch _at_ iem.at
:Copyright: winfried ritsch - IEM / algorythmics 2012+
:Version: 1.0

.. _`../docu/acre_title.rst`:  ../docu/acre_title.rst


The Mixer module provides all functionality for building individual mixer consoles from simple outputs to complex spatialization mixers within Pd.

It can be used for programming a flexible audio output interface, a audio input processing with live amplification (if needed), including filter, dynamic effects, buses and includes a monitoring section. 

Extension can be different spatialization functionality like Ambisonics.

The mixer module now combines the out, in, fx and other modules of older implementations in one module. 

Within this library basic audio mixer functionality  is provided, including the "traditional" master section with DSP control, out buses and sub-channels, channel-strips with some more specialized functions for inputs for pickups or others.

To achieve this, some helper functions are included to be used by other modules.
This library include base functions for fader and GUI's to be included in other modules of ACRE or moved to the acre-modules, where it depends from.

Most functions are documented and explained in their patch.

Structure
---------

The master sections also provides the DSP functionality for the patch, like turning `dsp on/off` and showing CPU usage.
Out functions are for collecting signals and prepare for output mostly to speakers including, crossover and equalization solution for multi-bus systems.

Parallel monitoring section is included as bypass for debugging the signal path.
For grouping the functions, they are separated in sub-folders, which will part of the object name, so they must not be declared as search paths, since same names are used in different folders.

Out functions
-------------

A ``[mxr/master/master~]`` is needed for out channels. 
Also for DSP functionality  and global parameter like  fadetime,... (see examples for more details) are included.
``[mxr/out/sub~ <out id> <sub id>]`` are optional extensions for each out channel ``[mxr/out/ch~ <out id>]`` to implement simple crossovers and will need a ``[mxr/sub/master~ <sub id>]``

(prefix ``mxr/`` is omitted only in the documentation in favour for shorter names)

master/fade~ master/ctl master/ds master/gain~
  Master controls for Master volumes, mutes, DSP and global settings like fadetime, ...

master/stereo~ master/stereo_ctl master/stereo_ds
  a sample stereo configuration without subs

out/ch~ out/ctl out/ds
  out channel which sums up the signal with $catch~ <out-id>~

  :provides: volume and individual mute.
  :needs: master~ for master volume

out/sub~ out/sub_ctl out/sub_ds
  As an extensions, it adds sub-woofer functionality to out channels.
  Each instance adds a tap of one out channel to one sub.

  :provides: vol, high-pass for out channel
  :needs: matching sub/master~ and out/ch~

sub/master~ sub/ctl sub/ds
  a sub-woofer management system for out buses and a master-section

  :provides: sub-volumes and filters
  :needs: master section

mo/master~ mo/ctl mo/prepost~ mo/send~
  audio signal monitoring with sends and a master monitor section

  :provides: monitoring functionality
  :needs:

in functions
------------

`in` functions simplifies channel strip building, with small units.

A channel in strip consists of:
   - `in~` which represents the `adc~` with pregain and DC-removal and phase inversion
   - `limiter~`
   - EQ filter section with hi- and low-cut and parametric EQ
   - VU and monitoring

A bus collects the in channels strip and let them feed further processing.

Distribution of ins with panorama functions or other spatial encoding can be added in later versions, but complex spatialization is outsourced in separate modules.

in/ch~  in/ch_ctl in/ch_ds
  a default channel strip which puts most of functionality of the lib.

  :provides: in, limiter, eq, fader in an channel strip
  :needs: master section

in/bus~ in/bus_ctl in/bus_ds in/buslive~ in/buslive_ctl in/buslive_ds
  collects in thrown from anywhere and distributes the signal.

  :provides: Bus channels and distribution
  :needs: master section


Helpers
-------

General functions used in for signal path

amplifying
^^^^^^^^^^

fader/db fader/rms fader/db2 fader/rms2
   unlike linear dB scaling (dbtorms), they behave more like faders on a mixer.

   :provides: fader curve conversions


fader/fader~ fader/gain~ fader/volvu_ctl fader/ctl fader/vol_ctlfader/vu_ctl
   fader using fader/db mapping.

   :provides: fader~ functionality 
   :needs: conversion functions

test functions
^^^^^^^^^^^^^^

test/tones_ctl test/tones~
   a test-tones generator with pulse function

   :provides: a testtone signal generator with GUI

prvu/send~ prvu/ctl
  used for all VU outs to be able to reset them, enhance in future ...

  :provides: conversion of signal to vu-meters with additional reset
  :needs:

signal conditioning
^^^^^^^^^^^^^^^^^^^

eq/dsp~ eq/ctl eq/ds  eq/hilo, eq/para eq/para~ eq/para_ds eq/hilo~ eq/hilo_ds
  a filter section with high low cut filter and parametric eq, 
  (original implemented for CUBEMixer by thomas musil)

  :provides: a low-cut and high-cut filter, parametric filter, low and high shelf
  :needs:

limiter/dsp~ limiter/ctl limiter/ds
  a limiter in a channel strip 

  :provides: a simple limiter to prevent digital clipping (CRACKLE)
  :needs:

Examples
--------

Example patches also for testing the  module.

example.pd example_stereo.pd
  test and example patch of the mixer library


Obsoletes
---------

will be removed or revised (and some moved to other modules).

test/recorder~.pd
   a session driven audio recorder

Notes
-----

- mxr now is a merge of previous in, out and fx modules

- spatial modules will be added within this mixer.

additional docu
---------------

for an introduction see `../docu/acre_intro.rst`_ ,
for more documentation explore docu_ .

.. _docu: ../docu/

.. _`../docu/acre_intro.rst`: acre_acre.rst
