# phy

_Spike sorting and ephys data analysis for 1000 channels and beyond._


## Overview

[**phy**](https://github.com/kwikteam/phy) is an open source electrophysiological data analysis library in Python. It targets neuronal recordings made with high-density multielectrode arrays containing up to thousands of channels.

This library allows you to spike-sort, analyze, and visualize your data interactively. It is currently based on the [Kwik format](kwik-format.md). *phy* provides:

* Full I/O support of the Kwik format
* High-performance plotting tools
* Spike detection algorithms (*SpikeDetekt*)
* Automatic clustering algorithms (*KlustaKwik2*)
* User-friendly, semi-automatic GUIs for manual sorting
* Command-line tools to manage, analyze, and visualize your Kwik datasets.

The API is highly modular, and you can extend the library in many ways.


## Quick install

On Linux or Mac OS X, run this in a console:

```
curl -O http://phy.cortexlab.net/install/latest.sh
bash latest.sh
```

This will install **miniconda** (a lightweight scientific Python distribution) and **phy** in your `$HOME/miniconda` by default. To install phy without reinstalling miniconda, use `bash latest.sh -s`. For more options, run `bash latest.sh -h`.

For other platforms or more detailed installation instructions, see [the Installation page](install.md).
