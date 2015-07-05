# Quick start guide: spike sorting

Here is a short tutorial for phy, showing how to spikesort a sample data file, from raw data to manually-refined spike trains.

> This quick-start guide shows how to use the command-line interface for spike sorting. For more advanced use-cases, you are encouraged to use phy's Python API. This will give you more control and flexibility. Also, some analysis features are most useful in the context of an interactive session with IPython.


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


## Download and edit the parameters file

TODO


## Run spike detection and automatic clustering

Type the following command:

```bash
$ phy spikesort hybrid_120sec.prm
```

This will take a few minutes to complete. The spike detection and automatic clustering algorithms will save their results in the `hybrid_120sec.kwik` and `hybrid_120sec.kwx` files.


## Run the manual clustering GUI

```bash
$ phy spikesort hybrid_120sec.kwik
```

