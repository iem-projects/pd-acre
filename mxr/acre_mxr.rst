mxr
===
module of puredata library ACRE
-------------------------------

:Author: Winfried Ritsch
:Contact: ritsch@algo.mur.at
:Revision: $Revision: 0.31 development 2014 $
:Copyright: algorythmics, 2012+

Note: in development means: names and structure can change ...

Within this library basic audio mixer functionality is provided, including
the "traditional" master section with DSP control, out buses and sub-channels, 
channel-strips with some more specialized functions for inputs for pickups or others.

To achieve this, some helper functions are included to be used by other modules.
This library include base functions for fader and GUI's to be included
in other modules of ACRE.

Most functions are documented and explained in their patch.

structure
---------

The master sections also provides the DSP functionality for the patch, like
turning dsp on/off and showing CPU usage. Out functions are for collecting
signals and prepare for output mostly to speakers including, crossover and 
equalization solution for multi-bus systems.

Parallel monitoring section is included as bypass for debugging the signal path.
For grouping the functions, they are separated in sub-folders, which will part
of the object name, so they should not be declared as search paths, since
same names are in different folder.

Out Functions
-------------


A ``[mxr/master/fade~]`` is needed for out channels. 
Also for DSP functionality  and global parameter like  fadetime,... 
(see examples for more details) are included.
``[mxr/out/sub~ <out id> <sub id>]`` are optional extensions 
for each out channel ``[mxr/out/ch~ <out id>]`` for implementing simple 
crossovers and needs a ``[mxr/sub/master~ <sub id>]``

short summary of out objects
............................

(prefix ``mxr/`` is ommitted in favour for shorter names in documentation only)

master/fade~ master/ctl master/ds master/gain~
  Master controls Master volumes, mutes, DSP  and global settings: fadetime, ...

master/stereo~ master/stereo_ctl master/stereo_ds
  a sample stereo config without subs

out/ch~ out/ctl out/ds
  out channel which sums up the signal with $catch~ <out-id>~ 

  :provides: volume and individual mute.
  :needs: master~ for master volume

out/sub~ out/sub_ctl out/sub_ds
  As an extensions, it adds sub-woofer functionality to out channels.   
  Each instance adds a output of one out channel to one sub.

  :provides: vol, highpass for out channel
  :needs: matching sub~ master sections

mo/master~ mo/ctl mo/prepost~ mo/send~
  monitoring functionality, with a master monitor 

  :Note: Monitoring has no storage module by default


sub/master~ sub/ctl sub/ds
  a sub-woofer master-section

  :provides: volume and filters
  :needs: master~ section

Helpers
-------

fader/fader~ fader/gain~ fader/volvu_ctl fader/ctl fader/vol_ctlfader/vu_ctl
   provides fader functionality unlike linear dB scaling they are more like
   faders on a mixer.

fader/db fader/rms fader/db2 fader/rms2
   fader curve conversions


test/tones_ctl test/tones~
   a test-tones generator with pulse function
   
prvu/send prvu/ctl
  used for all VU outs to be able to reset them, enhance in future ...

example.pd example_stereo.pd
  test and example patch of the out library

obsolete will be removed or revised
-----------------------------------

(and some, especially MIDI moved to other lib)

test/recorder~.pd