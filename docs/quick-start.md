# Quick start guide

Here is a short tutorial for phy, showing how to spikesort a sample data file, from raw data to manually-refined spike trains.


## Installation

We assume that *phy* has been correctly installed on your computer (see [install instructions here](install.md)). To check that this is the case, open a terminal and type:

```bash
$ phy -v
0.2.0
```


## Download a sample dataset

Create a new folder for your experiments, and type the following:

```bash
$ phy download hybrid_120sec.dat
```

This should download a 150MB raw data file, containing a 2 minutes recordings with 32 channels.

> `hybrid_120sec.dat` is a flat binary file containing `int16` samples. The first 32 numbers correspond to the first time sample, all 32 channels, etc.


##
