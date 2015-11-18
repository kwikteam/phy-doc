# Quick start guide: spike sorting

Here is a short tutorial for phy, showing how to spikesort a sample data file, from raw data to manually-refined spike trains.

> This quick-start guide shows how to use the command-line interface for spike sorting. For more advanced use-cases, you are encouraged to use phy's Python API. This will give you more control and flexibility. Also, some analysis features are most useful in the context of an interactive session with IPython. You will find more details about the API in the next sections.


## Installation

We assume that *phy* has been correctly installed on your computer (see the [quick install](index.md) or [advanced install](install.md) instructions). To check that this is the case, open a terminal and type:

```bash
$ phy -v
```

`0.2.2` should be displayed (sometimes followed by other characters). If this is not the case, please make sure you have activated your virtual environment (if created), follow the installation instructions again, or [file an issue](http://github.com/kwikteam/phy/issues/).

## Download a sample dataset

Create a new folder for your experiments, and type the following:

```bash
$ phy download hybrid_10sec.dat
```

This will download a raw data file containing a 10-seconds-long recordings with 32 channels.

> `hybrid_10sec.dat` is a flat binary file containing `int16` samples. The first 32 numbers correspond to the first time sample and all 32 channels, etc.


## Download and edit the parameters file

```bash
$ phy download hybrid_10sec.prm
```

This will download a parameters file, named **PRM file**. This Python text file contains the parameters required to run the spike sorting algorithms on the data.


## Run spike detection and automatic clustering

Type the following command:

```bash
$ phy spikesort hybrid_10sec.prm
```

This will take a few minutes to complete. The spike detection and automatic clustering algorithms will save their results in the `hybrid_10sec.kwik` and `hybrid_10sec.kwx` files.


## Run the manual clustering GUI

```bash
$ phy cluster-manual hybrid_10sec.kwik
```

This will open the manual sorting GUI.
