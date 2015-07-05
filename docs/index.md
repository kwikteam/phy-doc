# phy

_Spike sorting and ephys data analysis for 1000 channels and beyond._

## Overview

[**phy**](https://github.com/kwikteam/phy) is an open source electrophysiological data analysis library in Python. It targets neuronal recordings made with high-density multielectrode arrays containing up to thousands of channels.

This library allows you to spike-sort, analyze, and visualize your data interactively. It is currently based on the [Kwik format](kwik-format.md). *phy* provides:

* A Python API, to be used in scripts or interactively in an IPython terminal or notebook
* User-friendly, high-performance plotting facilities
* GUIs for manual sorting
* Command-line tools to manage, analyze, and visualize your Kwik datasets

The API is highly modular, and you can extend the library in many ways. You can even create your own GUIs.

## Quick install

On Linux or Mac OS X, run this in a console:

```
curl -O http://phy.cortexlab.net/install/latest.sh
bash latest.sh
```

This will install **miniconda** (a Python distribution) and **phy** in your `$HOME/miniconda` by default. To install phy without reinstalling miniconda, use `bash latest.sh -s`. For more options, run `bash latest.sh -h`.

For other platforms or more detailed installation instructions, see [the Installation page](install.md).

## Features

As of v0.2.0, the current features are implemented:

* Full read/write API for Kwik datasets
* Interactive and fast visualization of traces, waveforms, features, and cross-correlograms
* Spike detection optimized for hundreds of channels (*SpikeDetekt* algorithm)
* Automatic spike clustering through a KlustaKwik2 wrapper (expectation-maximization clustering algorithm)
* User-friendly manual sorting GUI with a semi-automated assistant that guides you through merge candidates
