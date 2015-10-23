# phy

_Spike sorting and ephys data analysis for 1000 channels and beyond._


## Overview

[**phy**](https://github.com/kwikteam/phy) is an open source electrophysiological data analysis library in Python. It targets neuronal recordings made with high-density multielectrode arrays containing up to thousands of channels.

This library allows you to spike-sort, analyze, and visualize your data interactively. It is currently based on the [KWIK format](kwik-format.md). *phy* provides:

* Full I/O support of the [KWIK format](kwik-format.md)
* High-performance plotting tools
* Spike detection algorithms (*SpikeDetekt*)
* Automatic clustering algorithms (*KlustaKwik2*)
* User-friendly, semi-automatic GUIs for manual sorting (similar to *KlustaViewa*)
* Command-line tools to manage, analyze, and visualize your KWIK datasets.

The API is highly modular, and you can extend the library in many ways.

Please subscribe to the [mailing list](https://groups.google.com/forum/#!forum/phy-users) to be kept up-to-date with new releases and changes!


## Quick install

This will install **miniconda** (a lightweight scientific Python distribution) and **phy** in a subdirectory called "miniconda" of your home directory.

### Linux
Open Terminal (or "XTerm"), and copy-paste the following:
```
wget http://phy.cortexlab.net/install/latest.sh
bash latest.sh
```
Then close and re-open the terminal before continuing.

Replace the last line with `bash latest.sh -h` to list the available options.

### Mac OS X:
Press Command + Space, type "Terminal", press Enter, then copy-paste the following:
```
curl -LO http://phy.cortexlab.net/install/latest.sh
bash latest.sh
```
Then close and re-open the terminal before continuing.

Replace the last line with `bash latest.sh -h` to list the available options.

### Windows (in "PowerShell"):

#### Prerequisites:
- [PowerShell](http://social.technet.microsoft.com/wiki/contents/articles/21016.how-to-install-windows-powershell-4-0.aspx).
- [Microsoft Visual C++ 2010 Redistributable](https://www.microsoft.com/en-gb/download/details.aspx?id=14632)

Open up "PowerShell" (you should be able to find this in your list of applications - if not, download it from the link above). Then copy-paste the following (in Powershell, you can paste with a right-click in the terminal):

```
iex ((new-object net.webclient).DownloadString('http://phy.cortexlab.net/install/latest.ps1'))
```

For other platforms or more detailed installation instructions, see [the advanced installation page](install.md).

When you've done installing, get started with the [quick start guide](quick-start.md)!
