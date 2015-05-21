## Manual clustering

The manual clustering subpackage (`phy.cluster.manual`) is the main component of phy 0.1.0. It provides a programmatic Python API as well as a lightweight graphical interface to manually refine the automatic clustering.

There is a light command-line tool to start the GUI on a dataset. Type the following in a terminal: `phy cluster manual myexperiment.kwik`. Add `-i` to start an IPython console at the same time.

In the following, we describe the API in case you want more control on the process.

### Session

The `Session` is the main interface to the manual clustering engine. Use tab completion in IPython to discover the methods. See also the [API documentation](https://github.com/kwikteam/phy-doc/blob/master/api.md#phyclustermanualsession).

Let's create a new manual clustering session using an already automatically clustered dataset:

```python
>>> from phy.cluster.manual import Session
```

```python
>>> kwik_path = 'myexperiment.kwik'
>>> session = Session(kwik_path)
2015-05-21 11:54:32  session:118             Saving a backup of the Kwik file in myexperiment.kwik.bak.
Features and masks initialized.[K
Waveforms initialized.[K
Statistics initialized.[K
```

> Putting your data files on a SSD is **highly recommended** for performance reasons.

This may take a while the first time, because a **cluster store** is automatically created. This folder in `myexperiment.phy/cluster_store/` contains a copy of all masks, features, and part of the waveforms for every cluster (one file per cluster). This makes the GUI orders of magnitude faster than fetching data from the HDF5 kwik files. The cluster store is transparently handled by the engine and you don't have to worry about it. The cluster store is also used to compute various cluster statistics at initialization time so that the interface is fast during manual clustering.

Oncce the session is loaded, you can view the data and start clustering it. See the API documentation for more details.

### Wizard GUI

Type `session.show_gui()` to launch the clustering GUI. This minimal GUI provides two things:

* A window where to dock visualization widgets.
* Keyboard shortcuts to go through your best clusters and a list of potential merge candidates (**wizard**).

> Type `ctrl+h` to see the list of keyboard shortcuts.

The wizard is there to save you a lot of time clustering your data manually. It makes you propositions with 1 or 2 clusters, and you have to decide an outcome based on the views in the window.

Here is the intended workflow:

* Initially, the **best** cluster found is shown. You can explore it in the various views (waveforms, features, traces, ACG).
* Use `space` and `shift+space` to scroll through your best clusters by decreasing quality.
* At any point, you can **pin** a cluster by pressing `enter`. Then you'll see a second cluster selected: this is the **closest match**. Unpin with `backspace`.
* When a cluster is pinned, scroll through the list of closest matches with `space` and `shift+space`. The pinned cluster stays selected.
* You have keyboard shortcuts to:
    * Merge the two displayed clusters.
    * Move either or both clusters to cluster groups (noise, MUA, good).

> Better quality and similarity measures will be used in the future. You'll also be able to write your own functions in Python.

![Wizard GUI screenshot](images/cluster-manual-gui.png)

### The cluster store

#### Features and masks

#### Cluster statistics

### Visualization

### Extending and customizing the interface

#### Using custom statistics in the wizard

#### Integrating your analyses in the engine

#### User parameters

#### Internal settings
