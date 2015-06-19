### Quick-install (Linux and Mac OS X)

Run this in a console:

```
curl http://phy.cortexlab.net/install/latest.sh
bash latest.sh
```

This will install **miniconda** (a Python distribution) and **phy** in your `$HOME/miniconda` by default. To install phy without reinstalling miniconda, use `bash latest.sh -s`. For more options, run `bash latest.sh -h`.

Then, use `phy cluster-manual myexperiment.kwik` to launch the GUI on a [Kwik](https://github.com/klusta-team/kwiklib/wiki/Kwik-format) dataset. Note that you have some test datasets [here](http://phy.cortexlab.net/data/).

Below are more detailled instructions if you don't want to use the automatic installer.

> We will provide Windows and GUI installers in the near future.

### Detailed instructions

phy is written in pure Python. It works with Python 2.7, 3.3, and 3.4 on Windows, Mac OS X, and Linux.

**It is highly recommended to use the free Miniconda distribution**. This software comes with a package manager named **conda** that lets you easily install, update, and remove Python packages.

> **Miniconda** is a lightweight Python distribution. **Anaconda** is Miniconda + many common Python packages. **Conda** is the package manager used by Miniconda and Anaconda. We recommend that you first install Miniconda, and then use Conda to install just the packages you need.

Advanced users may use other Python distributions, but we will only provide installation-related support on Miniconda/Anaconda.

> If you install Miniconda/Anaconda while you already have Python installed, you might end up with some conflicts. You're encouraged to uninstall all previous non-Conda Python installations, unless you're already using them.

Here are the installation instructions when you're starting from scratch:

#### 1. Open a terminal

* Windows: press `Windows` + `R`, type `cmd`, and press `Enter`.
* Mac OS X: TODO.
* Linux: you probably already know how to do it.

#### 2. Install miniconda

* http://conda.pydata.org/miniconda.html
* Download the **Python 3.4, 64-bit** version for your OS (this is the recommended version)
* Install Miniconda (**no need for root privileges**), for example with:

```
bash Miniconda3-latest-Linux-x86_64.sh -b -p $HOME/miniconda
```

(or choose any other path)

#### 3. Install phy and its dependencies

```bash
conda install conda python=3 pip numpy matplotlib scipy h5py pyqt ipython-notebook requests && pip install vispy phy
```

> Advanced users can use the development version with `git clone git://github.com/kwikteam/phy.git && cd phy && python setup.py develop`.


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

Most of these dependencies are only imported when you use a feature that needs them. This means that you don't need all dependencies if you're just interested in a small part of the library.

Here are further dependencies useful for development (advanced users):

* py.test (for testing)
* coverage (for code coverage)
* flake8 (for testing code quality)
* responses (for testing downloading functionality)


### Using phy

There is a command-line tool that you can use for quick manual clustering:

```
phy cluster-manual myexperiment.kwik
```

Use the optional `-i` option to start an interactive IPython terminal at the same time.

You can also start a notebook server with `ipython notebook`. Using the notebook is recommended when you want to do custom analyses. The notebook offers a web interface to write Python code, run analyses, and display visualizations.

In the notebook, import phy with `import phy`. To import a subpackage: `import phy.io`, for example. Then use tab completion to find the functions and classes available. See also the rest of the user guide for more documentation.


### Remote use

You normally install phy on your local computer. However you can also install an [IPython notebook server on a remote computer](https://ipython.org/ipython-doc/dev/notebook/public_server.html), and access your data from anywhere in the world with a web browser. You can even enable live visualizations with (**still highly experimental**):

```python
from vispy.app import use_app
use_app('ipynb_webgl')
```

In the near future we'll work particularly on this, so that you can use phy in the browser without installing the software or downloading the data.
