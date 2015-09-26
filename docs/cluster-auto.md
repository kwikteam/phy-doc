## Spike sorting session

*phy* 0.2.0 provides automatic spike detection and clustering algorithms.

### Session

The `Session` represents an interactive session around a given dataset. You can use it to detect spikes, cluster spikes, inspect and analyze your data, and open the manual clustering GUI.

Let's create a new session around a Kwik file (after `phy spikesort` has run):

```python
>>> import numpy as np
>>> from phy.session import Session
```

```python
>>> session = Session('data/hybrid_10sec.kwik')
Features and masks initialized.[K
Waveforms initialized.[K
Statistics initialized.[K
```

Opening the session automatically initializes the **cluster store**. This is an internal cache used by phy to accelerate access to per-cluster data. It is located in the `hybrid_10sec.phy/` subdirectory.

The session provides access to several objects:

* `session.model`: the underlying `KwikModel` instance
* `session.store`: the cluster store

```python
>>> session.model.describe()
Kwik file               /data/git/phy/doc/docs/data/hybrid_10sec.kwik
Recordings              1
List of shanks          0*
Clusterings             main*, empty, kk2_current, original
Channels                32
Spikes                  1603
Clusters                19
Duration                10s
```

```python
>>> session.store.display_status()
Cluster store status (/data/git/phy/doc/docs/data/hybrid_10sec.phy/cluster_store/0/main)
----------------------------------------------------------------------------------------
Number of clusters in the store     19
Number of old clusters               0
Total size (MB)                      6
Consistent                        True
```

The store gives you access to per-cluster data like features, masks, waveforms, their means, and other information.

```python
>>> session.store.mean_masks(14)
array([  0.00000000e+00,   0.00000000e+00,   0.00000000e+00,
         0.00000000e+00,   0.00000000e+00,   0.00000000e+00,
         0.00000000e+00,   0.00000000e+00,   0.00000000e+00,
         0.00000000e+00,   0.00000000e+00,   0.00000000e+00,
         0.00000000e+00,   7.15117727e-04,   6.62863022e-03,
         1.09908376e-02,   7.21668033e-03,   1.46417338e-02,
         1.87453795e-02,   3.88467051e-02,   4.11636345e-02,
         8.84853676e-02,   8.97215530e-02,   3.50288361e-01,
         2.48874888e-01,   7.05275834e-01,   6.27078891e-01,
         9.15426850e-01,   9.13762569e-01,   9.69715059e-01,
         9.12764490e-01,   9.03752923e-01], dtype=float32)
```

You can add your own cluster statistics as follows:

```python
>>> @session.register_statistic
... def n_refractory_violations(cluster):
...     return np.sum(np.diff(session.model.spike_train(cluster)) < .003)
12:45:18 [I] Registered statistic `n_refractory_violations`.
```

```python
>>> session.store.n_refractory_violations(10)
17
```

### Spike detection

The code comes from the previous SpikeDetekt2 software. The steps are the following:

* filtering of the raw data
* automatic threshold detection
* thresholding of the filtered data
* spike detection
* connected component extraction (using the probe's adjacency graph)
* mask computation (channels on which spikes are detected)
* waveform extraction (including realignment with respect to the peak)
* per-channel PCA of the waveforms
* projection of all waveforms on the PCs to compute the spike features

All of these steps are implemented in modular classes in the `phy.traces` package. The whole algorithm is implemented in `phy.cluster`.

> A parallel implementation will be provided in the next version.


### Automatic clustering

The code is implemented in the KlustaKwik2 program, written in Python and Cython. It implements a modified version of the expectation-maximization algorithm.
