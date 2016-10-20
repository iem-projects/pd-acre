==========
ACRE - amb
==========
------------------
Ambisonics Toolbox
------------------

:Author: Winfried Ritsch
:Contact: ritsch _at_ algo.mur.at, ritsch _at_ iem.at
:Copyright: winfried ritsch - IEM / algorythmics 2012+
:Version: 0.71 development, mostly stable but clone could be used
          for Pd Versions 0.47.1 instead of dynmic patching

.. _`../docu/acre_title.rst`:  ../docu/acre_title.rst

Ambisonics Toolbox is a collection of high level Pd abstraction, to implement Ambisonics integration either in a mixer or compositions or effects using iem_ambi.
One goal is to easily integrate Ambisonics encoder, decoder and processing for various purposes as modules. Another to provide Multichannel operations and signaling.

This module is based on the iem_ambi and some parts also on the iem_bin_ambi Pd-library, which is based on iemmatrix Pd-library.
It also depends on the acre/acre and acre/mxr module of the acre library.

Background
----------

In Ambisonics 3D or 2D Ambisonics signal is a multichannel audio-signal.
With higher orders, better spatial resolutions are provided and more Ambisonics channels are needed.
The channel count is calculated by the formulas ``n=(order+1)²`` for 3D and ``n=2*order+1`` for 2D. 
Therefore Ambisonics buses has to be implemented, which handle, for example on 5th order 3D 36 channels.
Until there is a snake functionality standard in Pd[snake]_ , we handle Ambisonics buses with abstraction and dynamic generated ``catch~/throw~`` and/or ``send~/receive~`` pairs to prevent excessive Pd cabling.
The order of the Ambisonics channels is important. Within 'amb' it complies with the ACN [ACN], N3D standard, which is used troughout the iem_ambi library.

Structure
---------

Buses
.....

Ambisonics buses have a name asiocated within an abstractions, which uses it. The chosen name ``<bus-id>`` also needs the order ``<order>`` and dimensionality to be defined. An abstraction with lower order, but same dimensionality, can be used to add to an Ambisonics bus with 'catch~'es and also to read from one with 'receive~'s, therefore a bus catches Ambisonics signals and sends.



Encoders and decoders
.....................

Encoders use Ambisonics Busses to throw their signals to them and decoders read from a Ambisonics bus and distribute it to speaker outs.


Outs
....

The outputs can be calibrated with Volume and delay and also host the master fader functionality.

Simple outs should only provide master fader.

Notes
-----

- parts are from an Implementation of the CUBEmixer

- since simple dynamic patching is used, r~/s~ and catch~/throw~ pairs can be created in a wrong order which drops an error warning on the console.
Since [savebang] is not implemented in Pd until now, we have to clear these abstractions before saving when developing to reduce warnings a little bit.
To prevent this a little bit more the initialization order is important, see example, using own initbang order.

Todo
----

implementation

 - use clone for buses and others instead of dynamic patcher, which should clean the library.

ambisonics mixer::

 - Distance from 0..1 (has to be discussed)
 - distance signal objects with first reflection simulation
 - directional loudness
 - rotate, mirror
 - widening
 - virtual microphones

processing::

 - Binaural rendering
 - Headtracker support for binaural
 - 3D-Reverb
 - B-Format encoder for various microphones from A-format

 
change names:
 - all signal objects with ~ at end like player, outs
 
additional docu
---------------

for an introduction see `../docu/acre_intro.rst`_ ,
for more documentation explore docu_ .

.. _docu: ../docu/

.. _`../docu/acre_intro.rst`: acre_acre.rst

References
----------

.. [snake] Pd-snake was an idea 2013 within a workshop with Miller Puckette at the IEM to extend Pd with multichannel signal connection, which is backwards compatible, but has not been implemented yet.

.. [ACN] The Ambisonics Association, “Ambisonic Channels,” checked: 2011-09-09.  [Online].  Available: http://ambisonics.ch/standards/channels/
