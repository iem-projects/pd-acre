acre - base abstractions and helpers
====================================
shared objects in ACRE
----------------------

This is library of objects as Puredata patches is a base library for the different ACRE-modules and will be extended, as they grows.

Special care is taken not altering code of abstractions already used in other modules. 

debugf and reporting Functions
------------------------------

reporting
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
  
table_hanning
  hanning table, generated
 
spectro_fft~.pd
  FFT for the spectroscope

conversions and mappings
------------------------

fader2db db2fader fader2rms rms2fader fader_gain~ fader~
  used as for mapping of fader characteristics  instead linear dbtorms and using 
  them in simple signal objects
 
samples2ms ms2samples
  uses samplerate to convert between samples and ms

m2fakt fakt2m
 converts between midinote  interval (cents/100) an  factor of frequencies

ms2Hz Hz2ms
 convert between frequency in Hertz and time in ms as wavelength, respect sample-rate and 0

 
counting and indexing
---------------------

count_until
 count until some number
 



obsolete
--------

This files will be removed or revised.

ts ts_ctl
  testsamples in a sample library in data
 
Helpers
-------

acre_acre.rst 
   documentation of this module, this document

Tests
-----

example.pd
 holds test objects and needs the ds lib