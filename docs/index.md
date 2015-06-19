#phy
_Spike sorting and data analysis for 1000 channels and beyond._

## Overview

[**phy**](https://github.com/kwikteam/phy) is an open source electrophysiological data analysis library in Python for neuronal recordings made with high-density multielectrode arrays containing up to thousands of channels.

This library provides a Python API to analyze and visualize data interactively, as well as user-friendly graphical interfaces to quickly inspect and refine your data.

The API is highly modular and allows you to adapt it to your workflows. For example, you can create your own custom GUI.

## Quick install

On Linux or Mac OS X, run this in a console:

```
curl http://phy.cortexlab.net/install/latest.sh
bash latest.sh
```

This will install **miniconda** (a Python distribution) and **phy** in your `$HOME/miniconda` by default. To install phy without reinstalling miniconda, use `bash latest.sh -s`. For more options, run `bash latest.sh -h`.

For other platforms or more detailed installation instructions, see [the Installation page](install.md).

Then, use `phy cluster-manual myexperiment.kwik` to launch the GUI on a [Kwik](https://github.com/klusta-team/kwiklib/wiki/Kwik-format) dataset. Note that you have some test datasets [here](http://phy.cortexlab.net/data/).

## Use-cases

As of v0.1.0, you can use phy to:

* Open a Kwik dataset and access all the data fields for inspection, visualization, and analysis.
* Manually refine a dataset that has been automatically clustered by KlustaKwik.

Future versions will allow you to spike sort raw data and make custom analyses of extracellular and spiking data.

It is recommended to use the library in IPython (terminal or notebook) for interactive use. **Use tab completion without moderation**: it lets you discover the objects and methods that are available.

You can also use phy in regular Python scripts. Finally, you can use the public Python API to customize the interfaces or integrate phy in your own projects.

## Milestones

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