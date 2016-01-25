Ambisonics Tools
================

:author: winfried ritsch WDC3/WS2015

Collection standalone application for supporting to set up an Ambisonics system.

This tools has to be adapted for the actual setup and therefore should be seen as examples and a starting point.


A Calibrator
------------

To callibrate a speaker with delays and levels using an measurement microphone.

Workflow
........

0.) Enter number of speaker and assign DAC in dac objects

1.) choose the right ADC channel and level the input to about -10dB at loudest.

2.) optional Microphone at one speaker (reduce volume) and measure latency or
enter the minimum expected latence (see audio buffer).

3.) Microphone in the middle of the sweet spot. 

4.) place yourself not near the microphone

5.) test if all speaker are working with lower volume.

6.) raise volume and start automatic measurement (use ear protectors !!!)

7.) store results


Hints
.....

Microphone position
 The microphone should be out of the reverberation radius of the speaker::

  Rr ~ 0.057 * sqrt(V/T60)

  T60(T30,T20) ... reverberation time for -60dB,-30dB,-20dB measurement method
  V ... room volume

latency 
 of computer should be measured first, but since only relative delay values are used it is not really important.

B Simple Decoder Matrix calculator
----------------------------------

The decoder matrix calculator is taken from the CUBEmixer and iemambi library.
For better decoder matrixes use tools provided by other sources like Ambisonics Decoder Toolbox [ADT] by Aaron J. Heller 
( https://bitbucket.org/ambidecodertoolbox/adt.git )

The inverse of the speaker matrix is calculated, but this can be singular. Especially for hemisphere arragement of speakers,
use phantom speakers to fill the sphere. This would give better results.


References
----------

.. [ADT] Ambisonics Decoder Toolbox paper LAC: http://lac.linuxaudio.org/2014/papers/17.pdf

.. [iem_ambi] https://git.iem.at/pd/iem_ambi

