## Installation

phy is written in pure Python. It works with Python 2.7, 3.3, and 3.4 on Windows, Mac OS X, and Linux.

There are several dependencies:

* pip (for installing phy)
* NumPy (mandatory)
* SciPy (for filtering waveforms)
* h5py (for reading/saving Kwik files)
* VisPy (for interactive plotting)
* PyQt4 (for the graphical interfaces)
* matplotlib (optional, for plotting)
* IPython and its notebook (optional, but recommended for interactive use)
* requests (for downloading test data)

Most of these dependencies are only imported when you use a feature that needs them. This means that you don't need all dependencies if you're just interested in a small part of the library.

Here are further dependencies useful for development (advanced users):

* py.test (for testing)
* coverage (for code coverage)
* flake8 (for testing code quality)
* responses (for testing downloading functionality)

**It is highly recommended to use the free Miniconda distribution**. This software comes with a package manager that lets you easily install, update, and remove Python packages.

> **Miniconda** is a lightweight Python distribution. **Anaconda** is Miniconda + many common Python packages. **Conda** is the package manager used by Miniconda and Anaconda. We recommend that you first install Miniconda, and then use Conda to install the packages you need.

Advanced users may use other Python distributions, but we will only provide installation-related support on Miniconda/Anaconda.

> If you install Miniconda/Anaconda while you already have Python installed, you might end up with some conflicts. You're encouraged to uninstall all previous non-Conda Python installations, unless you're already using them.

Here are the installation instructions when you're starting from scratch:

1. Install Miniconda.
2. Create a Conda environment with all the dependencies for phy.
3. Install phy.
4. Use phy.

### 0. Opening a terminal

* Windows: press `Windows` + `R`, type `cmd`, and press `Enter`.
* Mac OS X: TODO.
* Linux: you probably know how to do it.

### 1. Installing Miniconda

TODO

### 2. Creating a Conda environment for phy

TODO

### 3. Installing phy

For the time being, we recommend to install the development version on GitHub:

* `pip install git+git://github.com/kwikteam/phy.git`

You can use the same command at any time to update the package to the latest version.

> Advanced users can also clone the package manually with git and install phy with `python setup.py develop`.

### 4. Use phy

Open an IPython terminal with `ipython` or a notebook server with `ipython notebook`. Using the notebook is recommended for extended use. The notebook offers a web interface to write Python code, run analyses, and display visualizations.

Import phy with `import phy`. To import a subpackage: `import phy.io`, for example. Then use tab completion to find the functions and classes available.

### Remote use

You normally install phy on your local computer. However you can also install an IPython notebook server on a remote computer, and access your data from anywhere with a web browser. You can enable live visualizations with (experimental):

```python
from vispy.app import use_app
use_app('ipynb_webgl')
```
