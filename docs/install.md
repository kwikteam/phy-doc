* For quick install instructions, please see the [homepage](index.md). **

phy is written in pure Python. It works with Python 2.7, 3.3, and 3.4 on Windows, Mac OS X, and Linux.

**It is highly recommended to use the free Miniconda distribution**. This software comes with a package manager named **conda** that lets you easily install, update, and remove Python packages.

> **Miniconda** is a lightweight Python distribution. **Anaconda** is Miniconda + many common Python packages. **Conda** is the package manager used by Miniconda and Anaconda. We recommend that you first install Miniconda, and then use Conda to install just the packages you need.

Advanced users may use other Python distributions, but we will only provide installation-related support on Miniconda/Anaconda.

> If you install Miniconda/Anaconda while you already have Python installed, you might end up with some conflicts. You're encouraged to uninstall all previous non-Conda Python installations, unless you're already using them.

Here are the installation instructions when you're starting from scratch:

#### 1. Open a terminal

On Windows, you will need [PowerShell](http://social.technet.microsoft.com/wiki/contents/articles/21016.how-to-install-windows-powershell-4-0.aspx) and the [Microsoft Visual C++ 2010 Redistributable](https://www.microsoft.com/en-gb/download/details.aspx?id=14632) installed.

* Windows: press `Windows` + `R`, type `powershell`, and press `Enter`.
* Mac OS X: press `Command` + `Space`, type `Terminal`, and press `Enter`.
* Linux: you probably already know how to do it.

#### 2. Install miniconda

* http://conda.pydata.org/miniconda.html
* Download the **Python 3.4, 64-bit** version for your OS (this is the recommended version)
* Install Miniconda (**no need for root privileges**), for example with:

```
bash Miniconda3-latest-Linux-x86_64.sh -b -p $HOME/miniconda
```

(or choose any other path)

On Windows, launch the GUI Miniconda installer.

#### 3. Install dependencies

```
conda install conda python=3 pip numpy matplotlib scipy h5py pyqt ipython-notebook requests --yes && conda install -c http://conda.binstar.org/kwikteam klustakwik2 --yes && pip install vispy
```

#### 4. Install phy

To install the latest stable version:

```
pip install phy
```

To install the development version (you must have **git** installed, for example using the GitHub desktop client):

```
git clone git://github.com/kwikteam/phy.git ~/phy && cd ~/phy && python setup.py develop
```
This will keep your working copy in `~/phy` (`~` is a link to your home folder) can change the directory 

### Dependencies

There are several dependencies:

* pip (for installing phy)
* NumPy (mandatory)
* SciPy (for filtering waveforms)
* h5py (for reading/saving Kwik files)
* VisPy (for interactive plotting, **development version on GitHub required**)
* PyQt4 (for graphical interfaces)
* matplotlib (optional, for plotting)
* IPython and its notebook (optional, but recommended for interactive use)
* requests (for downloading test data)
* klustakwik2 (fast masked-EM clustering algorithm)

Most of these dependencies are only imported when you use a feature that needs them. This means that you don't need all dependencies if you're just interested in a small part of the library.

Here are further dependencies useful for development (advanced users):

* py.test (for testing)
* coverage (for code coverage)
* flake8 (for testing code quality)
* responses (for testing downloading functionality)


### Using phy

There is a command-line tool named `phy` that you can use for automatic and manual clustering. Type the following to see the help.

```
phy -h
```

The `-i` option launches phy in an interactive IPython terminal.

You can also start a notebook server with `ipython notebook`. Using the notebook is recommended when you want to do custom analyses. The notebook offers a web interface to write Python code, run analyses, and display visualizations.

In the notebook, import phy with `import phy`. To import a subpackage: `import phy.io`, for example. Then use tab completion to find the functions and classes available. See also the rest of the user guide for more documentation.


### Remote use

You normally install phy on your local computer. However you can also install an [IPython notebook server on a remote computer](https://ipython.org/ipython-doc/dev/notebook/public_server.html), and access your data from anywhere in the world with a web browser. You can even enable live visualizations with (**still highly experimental and largely untested**):

```python
from vispy.app import use_app
use_app('ipynb_webgl')
```

In the near future we'll work particularly on this, so that you can use phy in the browser without installing the software or downloading the data.
