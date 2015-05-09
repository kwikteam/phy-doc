## Manual clustering

The manual clustering subpackage (`phy.cluster.manual`) is the main component of phy 0.1.0. It provides a programmatic Python API as well as a lightweight graphical interface to manually refine the automatic clustering.

### Session

The `Session` is the main interface to the manual clustering engine. Use tab completion in IPython to discover the methods. See also the [API documentation](https://github.com/kwikteam/phy-doc/blob/master/api.md#phyclustermanualsession).

Let's create a new manual clustering session using an already automatically clustered dataset:

```python
from phy.cluster.manual import Session
session = Session(kwik_path)
```

> Putting your data files on a SSD is **highly recommended** for performance reasons.

This may take a while the first time, because a **cluster store** is automatically created. This folder in `your_data.phy/cluster_store/` contains a copy of all masks and features for every cluster (one file per cluster). This makes performance orders of magnitude faster than fetching data from the HDF5 kwik files. The cluster store is transparently handled by the engine and you don't have to worry about it. The cluster store is also used to compute various cluster statistics at initialization time so that the interface is fast during manual clustering.

Oncce the session is loaded, you can view the data and start clustering it. See the API documentation for more details.

### Wizard GUI

Type `session.show_gui()` to launch the clustering GUI. This minimal GUI provides two things:

* A window where to dock visualization widgets.
* Keyboard shortcuts to go through your best clusters and a list of potential merge candidates.

> Type `h` for the list of keyboard shortcuts.

### Extending and customizing the interface

#### Using custom statistics in the wizard

#### Integrating your analyses in the engine

#### User parameters

#### Internal settings
