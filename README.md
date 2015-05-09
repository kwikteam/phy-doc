# phy documentation

[**phy**](https://github.com/kwikteam/phy) is an open source electrophysiological data analysis libbrary in Python for neuronal recordings made with high-density multielectrode arrays containing tens, hundreds, or thousands of channels.

## Overview

This library provides a Python API to analyze and visualize data interactively, as well as user-friendly graphical interfaces to quickly inspect and refine your data.


### Use-cases

As of v0.1.0, you can use phy to:

* Open a Kwik dataset and access all the data fields for inspection, visualization, and analysis.
* Manually refine a dataset that has been automatically clustered by KlustaKwik.

Future versions will allow you to spike sort raw data and make custom analyses of extracellular and spiking data.

It is recommended to use the library in IPython (terminal or notebook) for interactive use. **Use tab completion without moderation**: it lets you discover the objects and methods that are available.

You can also use phy in regular Python scripts. Finally, you can use the public Python API to customize the interfaces or integrate phy in your own projects.

### Milestones

The current 0.1.0 release implements the following features:

* Read/save Kwik files, as created by the Klusta-suite (SpikeDetekt2 and klustakwik).
* Interactive visualization of:
    * waveforms with probe geometry
    * multi-dimensional features
    * raw traces with clusters and spikes
* Some basic cluster statistics, mainly auto- and cross-correlograms.
* Manual clustering functionality: merging, splitting, undo stack.
* A semi-automatic assistant for the manual clustering step. This assistant guides you through clusters that are candidates for merging, and allows you to quickly make decisions through a streamlined graphical interface.

The 0.2.0 release (~Summer 2015) will be the first release of phy to implement a complete spike sorting toolchain, from raw data to spike trains:

* Automatic spike detection using a flood-fill algorithm that takes the probe geometry and topology into account (previously known as SpikeDetekt).
* Automatic clustering of spikes into putative neurons through a custom version of the expectation-maximization algorithm (previously known as masked KlustaKwik).

The 0.3.0 release (~Fall 2015) will bring further improvements and optimizations to scale to 1000+ channels (mainly sparse array structures).


## Table of contents

Here is the table of contents of the user guide:

* 1. [Installation](install.md)
* 2. [Working with Kwik files](kwik-model.md)
* 3. [Interactive plotting](plot.md)
* 4. Spike detection (planned for 0.2.0)
* 5. Automatic clustering (planned for 0.2.0)
* 6. [Manual clustering](cluster-manual.md)
* 7. Neuronal data analysis
* [API documentation](api.md)

If you're just interested in the replacement of KlustaViewa for manual
clustering, you can just read section 6.

If you want to make custom analyses and visualizations of your data, read the other sections.

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
