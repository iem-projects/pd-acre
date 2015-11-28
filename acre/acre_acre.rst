acre - base abstractions and helpers
====================================
common module objects used in the different modules of ACRE
-----------------------------------------------------------

For more documentation see ../docu/acre_title.rst

Functions
---------

filename_shorten filename_split
  handling of filenames for relative paths and shorten for on GUI

scope
 simple oscilloscope, dsp and controls not separated, no triggers

spectroscope.pd
 simple Spectroscope,  dsp and controls not separated, no auto-gain
 
testtones~ testtones_ctl
  A test tones generator: noise, sine, saw generator, pulse played for better
  localization


Helpers
-------

tests, documentation and patches used by other abstraction in this module

acre_acre.rst 
   documentation of this module, this document

main.pd
  test and example patches for this library module

table_hanning
  hanning table, generated
 
spectro_fft~.pd
  FFT for the spectroscope

fader2db db2fader fader2rms rms2fader fader_gain~ fader~
  used as for mapping of fader characteristics  instead linear dbtorms and using 
  them in simple signal objects
 
samples2ms ms2samples
  uses samplerate to convert between samples and ms

m2fakt fakt2m
 converts between midinote  interval (cents/100) an  factor of frequencies
  
obsolete
--------

This files will be removed or revised.

ts ts_ctl
  testsamples in a sample library in data

none
 none

Tests
-----

example.pd
 holds test objects and needs the ds lib