# phy

_Spike sorting and ephys data analysis for 1000 channels and beyond._


## Overview

[**phy**](https://github.com/kwikteam/phy) is an open source electrophysiological data analysis library in Python. It targets neuronal recordings made with high-density multielectrode arrays containing up to thousands of channels.

This library allows you to spike-sort, analyze, and visualize your data interactively. It is currently based on the [KWIK format](kwik-format.md). *phy* provides:

* Full I/O support of the KWIK format](kwik-format.md)
* High-performance plotting tools
* Spike detection algorithms (*SpikeDetekt*)
* Automatic clustering algorithms (*KlustaKwik2*)
* User-friendly, semi-automatic GUIs for manual sorting (similar to *KlustaViewa*)
* Command-line tools to manage, analyze, and visualize your KWIK datasets.

The API is highly modular, and you can extend the library in many ways.

Please subscribe to the [mailing list](https://groups.google.com/forum/#!forum/klustaviewas) to be kept up-to-date with new releases and changes!


## Quick install

This will install **miniconda** (a lightweight scientific Python distribution) and **phy** in your `$HOME/miniconda` by default (normally `/home/username/miniconda` on Linux/Mac OS X, and `C:\Users\Username\miniconda\` on Windows).

### Linux (in "Terminal" / "XTerm"):
```
wget http://phy.cortexlab.net/install/latest.sh
bash latest.sh
```
Replace the last line with `bash latest.sh -h` to list the available options.

### Mac OS X (in "Terminal"):
```
curl -LO http://phy.cortexlab.net/install/latest.sh
bash latest.sh
```
Replace the last line with `bash latest.sh -h` to list the available options.

### Windows (in "PowerShell"):

#### Prerequisites:
- [PowerShell](http://social.technet.microsoft.com/wiki/contents/articles/21016.how-to-install-windows-powershell-4-0.aspx).
- [Microsoft Visual C++ 2010 Redistributable](https://www.microsoft.com/en-gb/download/details.aspx?id=14632)

```
iex ((new-object net.webclient).DownloadString('http://phy.cortexlab.net/install/latest.ps1'))
```

For other platforms or more detailed installation instructions, see [the Installation page](install.md).
