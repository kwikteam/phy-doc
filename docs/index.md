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

If you already have a `miniconda` or full `anaconda` Python installation (e.g. for the legacy `KlustaViewa`/`Klusta-Suite`, or a previous version of `phy`) then replace the last line with `bash latest.sh -s` to *S*kip the miniconda installation. If you wish to use Klusta-Suite and phy simultaneously, then you should make sure to install at least one of them in a virtual environment (do not leave this field blank when prompted).

Replace the last line with `bash latest.sh -h` to list the available options.

### Mac OS X:
Press Command + Space, type "Terminal", press Enter, then copy-paste the following:
```
curl -LO http://phy.cortexlab.net/install/latest.sh
bash latest.sh
```
Then close and re-open the terminal before continuing.

If you already have a `miniconda` or full `anaconda` Python installation (e.g. for the legacy `KlustaViewa`/`Klusta-Suite`, or a previous version of `phy`) then replace the last line with `bash latest.sh -s` to *S*kip the miniconda installation. If you wish to use Klusta-Suite and phy simultaneously, then you should make sure to install at least one of them in a virtual environment (do not leave this field blank when prompted).

Replace the last line with `bash latest.sh -h` to list the available options.

### Windows (in "PowerShell"):

#### Prerequisites:
- [PowerShell](http://social.technet.microsoft.com/wiki/contents/articles/21016.how-to-install-windows-powershell-4-0.aspx).
- [Microsoft Visual C++ 2010 Redistributable](https://www.microsoft.com/en-gb/download/details.aspx?id=14632)

If you're trying to repair a failed installation or you tried to install before removing the old installation from your $PATH, then you might need to use the Advanced Install instructions.

Open up "PowerShell" (you should be able to find this in your list of applications - if not, download it from the link above). Then copy-paste the following (in Powershell, you can paste with a right-click in the terminal):

```
iex ((new-object net.webclient).DownloadString('http://phy.cortexlab.net/install/latest.ps1'))
```

*Warning:*  These instructions will not work if you have another installation of Python, e.g. if you have previously installed `KlustaViewa`. For this quick installation script to work, you need to make sure that you remove all references (there might be several!) to the old Python installation, or any path with `WinPython` or `KlustaViewa` in both your system and user `$PATH`. For more information on editing your user and system `$PATH`, [see here](http://www.computerhope.com/issues/ch000549.htm). Once you've done this and closed/opened a new instance of PowerShell, you'll be able to use the quick-install script and run `KlustaViewa` and `phy` simultaneously.

For other platforms or more detailed installation instructions - for example, if you wish to continue using an existing Python installation - see [the advanced installation page](install.md).

When you've done installing, get started with the [quick start guide](quick-start.md)!
