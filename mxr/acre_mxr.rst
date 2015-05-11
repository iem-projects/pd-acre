mxr
===
module of puredata library ACRE
-------------------------------

:Author: Winfried Ritsch
:Contact: ritsch@algo.mur.at
:Revision: $Revision: 0.2 Scan 2014 $
:Copyright: algorythmics, 2012+

Note: Complete rework of this lib for Scan !!!! (This line will be deleted if finished)


Within this library basic audio mixer functionality should be granted inlcuding
the "traditional" master section with DSP control, out buses and sub-channels, 
in channels with some more specialized inputs for pickups or others.

With this library also base functions for fader und GUIs are provided to be included
in other modules of ACRE.


structure
---------

A master~.pd is needed for also for DSP functionality and global parameter like 
fadetime,... (see examples for more details)
Sub_outs are optional extensions  for each out channel for implementing simple 
crossovers.

Out Functions
-------------

master~ master_ctl master_ds
  Master controls Master volumes, mutes, DSP  and global settings: fadetime, ...

out~ out_ctl out_ds
  out channel which sums up the signal with $catch~$, 

  provides: volume and individual mute.
  needs: master~ for master volume

out_sub~ out_sub_ctl out_sub_ds
  As an extensions, it adds subwoofer functionality to out channels.   
  Each instance adds a output of one out channel to one sub.

  provides: vol, highpass for out channel
  needs: matching sub~ master sections


monitor~ monitor_ctl monitor_prepost~ monitor_send~
  monitoring functionality, with a master monitor 

  Note: Monitoring has no storage module by default


sub~ sub_ctl sub_ds
  a subwoofer mastersection

  provides: volume and filters
  needs: master~ section

Helpers
------

prvu_send
  used for all VU outs

example.pd
  test and example patch of the out library

master_bus4sub1~ master_bus4sub1_ctl master_bus4sub1_ds
  example for 4 out buses and one sub combined (untested)

acre_out.rst 
   this document   



obsolete will be removed or revised
-----------------------------------

(and some, especially MIDI moved to other lib)


dac8~.pd
recorder~.pd
dac8~.pd
recorder~.pd
