===========
ACRE - acre
===========
-------------------------------------------
acre - base abstractions and helpers module
-------------------------------------------
:Author: Winfried Ritsch
:Contact: ritsch _at_ algo.mur.at, ritsch _at_ iem.at
:Copyright: winfried ritsch - IEM / algorythmics 2012+
:Version: 1.0.1

.. _`../docu/acre_title.rst`:  ../docu/acre_title.rst

This is the common base module for the different ACRE-modules.

Special care is taken not. altering the abstractions  herein, especially
whan already used in other modules. 

Most documentation is in example.pd and the objects themselves.

debug and reporting Functions
-----------------------------

filename_shorten filename_split
  handling of filenames for relative paths and shorten for on GUI

scope
 simple oscilloscope, dsp and controls not separated, no triggers

scope_threshold
 like scope with threshold

spectroscope.pd
 simple Spectroscope,  dsp and controls not separated, no auto-gain
 
testtones~ testtones_ctl
  A test tones generator: noise, sine, saw generator, pulse played for better
  localization
  
table_hanning
  hanning table, generated
 
spectro_fft~.pd
  FFT for the spectroscope

conversions and mappings
------------------------
 
samples2ms ms2samples
  uses samplerate to convert between samples and ms

m2fakt fakt2m
 converts between midi-note  interval (cents/100) an  factor of frequencies

ms2Hz Hz2ms
 convert between frequency in Hertz and time in ms as wavelength, respect sample-rate and 0
 
samplerate
 trace samplerate changes within DSP on/off periods

counting and indexing
---------------------

count_until
 count until some number

testing
-------

some test funcions.

ts ts_ctl
  testsamples in a sample library in data

Helpers
-------

arg_default
  helps handle default arguments for not given ones

acre_acre.rst 
   documentation of this module, this document

Tests
-----

example.pd
 simple examples holds test objects and needs the ds lib
 
additional docu
---------------

for an introduction see `../docu/acre_intro.rst`_ ,
for more documentation explore docu_ .

.. _docu: ../docu/

.. _`../docu/acre_intro.rst`: acre_acre.rst
