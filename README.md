# phy documentation

**phy** is an open source electrophysiological data analysis package for neuronal recordings made with high-density multielectrode arrays containing tens, hundreds, or thousands of channels.


## Overview

The current 0.1.0 release implements the following features:

* Read/save Kwik files, as created by the Klusta-suite (SpikeDetekt2 and klustakwik).
* Interactive visualization of:
    * waveforms with probe geometry
    * multi-dimensional features
    * raw traces with clusters and spikes
* Some basic cluster statistics, mainly auto- and cross-correlograms.
* Manual clustering functionality: merging, splitting.
* A semi-automatic assistant for the manual clustering step. This assistant guides you through clusters that are candidates for merging, and allows you to quickly make decisions through a streamlined graphical interface.

The 0.2.0 release (~Summer 2015) will be the first release of phy to implement a complete spike sorting toolchain, from raw data to spike trains:

* Automatic spike detection using a flood-fill algorithm that takes the probe geometry and topology into account (previously known as SpikeDetekt).
* Automatic clustering of spikes into putative neurons through a custom version of the expectation-maximization algorithm (previously known as masked KlustaKwik).

The 0.3.0 release (~Fall 2015) will bring further improvements and optimizations to scale to 1000+ channels (mainly sparse array structures).


## Table of contents

* [Installation](install.md)
* [Working with Kwik files](kwik-model.md)
* Interactive plotting
* Manual clustering


## Contact

phy is developed in the [cortexlab](http://cortexlab.net) at University College London by:

* [Cyrille Rossant](http://cyrille.rossant.net/)
* Max Hunter (graphical interfaces)
* Dan Goodman (automatic clustering with KlustaKwik2)
* Shabnam Kadir
* Kenneth Harris

Here are a few useful links:

* [Mailing list](https://groups.google.com/forum/#!forum/klustaviewas)
* [Issue tracker](https://github.com/kwikteam/phy/issues)
* [GitHub repository](https://github.com/kwikteam/phy)
