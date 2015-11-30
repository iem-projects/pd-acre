Ambisonics Toolbox
==================

Ambisonics Toolbox is a collection of high level Pd abstraction, to implement Ambisonics integration either in a mixer or compositions or Effects. One goal is to easily integrade Ambisonics encoder, decoder and processing for various purposes without a deep understanding of underlying mathematics, execpt mentioned here.

This module is based on the iem_ambi Pd-library and some parts also on the iem_bin_ambi Pd-library, which is based on iemmatrix Pd-library.
It is also depended on the acre/acre and acre/mxr module.


Background
----------

In Ambisonics 3D- or 2D-audiosignals are handled as an Ambisonics signals, which in fact is a multichannel audio-signal. 
With higher orders , better spatial resolution are provided and more channels are used.
The channel count is calculated by the formulas ``n=(order+1)²`` for 3D and ``n=(2*order+1)`` for 2D. 
Therefore Ambisonics buses has to be used which are for example on 5th order 3D 36 channels. 
Until there is a snake functionality standard in Pd[snake]_ , we handle Ambisonics Buses with abstraction and dynamic generated ``catch~/throw~`` and/or ``send~/receive~`` pairs to prevent excessive Pd cabling.



Structure
---------

Buses
.....

Ambisonics buses are named used within the Ambisonics abstractions, defined by name ``<bus-id>`` and order ``<order>``.



Notes
-----

- parts are from an Implementation of the CUBEmixer

.. [snake] Pd-snake was an idea 2013 within a workshop with Miller Puckette at the IEM to extend Pd with multichannel signal connection, which is backwards compatible, but has not been implemented yet.