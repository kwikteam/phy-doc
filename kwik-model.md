## Working with Kwik files

> phy 0.1.0 only supports files in the Kwik format. Future versions may support other file formats.

The [**Kwik format**](https://github.com/klusta-team/kwiklib/wiki/Kwik-format) features several files:

* `.kwik`: metadata, spikes, clusters
* `.kwx`: features, waveforms
* `.raw.kwd`: raw extracellular traces

phy 0.1.0 requires you to provide all of these files. You can use the [`klusta`](https://github.com/klusta-team/example) program to generate them from raw data in `.dat` format (flat binary file with int16 samples). As part of this process, spikes are detected, extracted, and grouped into putative clusters.

> OpenEphys can also generate Kwik files. Feel free to contact us if you get any problem or incompatibility.

phy 0.2.0 will integrate the entire toolchain to go from raw data to Kwik files, and you won't need to use the external `klusta` program anymore.

> Currently, the `klusta` program may complete in minutes to hours, days, or even weeks for the largest datasets. We will make this process considerably faster (notably using parallelization) in phy 0.2.0 and later.


### Opening a dataset

Open a Kwik dataset with:

```python
>>> from phy.io import KwikModel
```

Let's assume that we have a Kwik dataset in the current directory:

```python
>>> !ls | grep myexperiment
myexperiment.kwik
myexperiment.kwx
myexperiment.raw.kwd
```

```python
>>> kwik_path = 'myexperiment.kwik'
>>> model = KwikModel(kwik_path)
```

The waveforms in the `.kwx` file are not used at all in phy: rather, they are dynamically extracted and filtered from the raw data. This is because storing waveforms takes too much storage space.

Now, `model` offers you access to all of your data. See the [API](https://github.com/kwikteam/phy-doc/blob/master/api.md#phyiokwikmodel) for more details. In IPython, use tab completion to discover the attributes and methods of the object.

### Spikes and clusters

```python
>>> model.spike_samples
array([     35,     795,     812, ..., 2398670, 2398753, 2399983], dtype=uint64)
```

```python
>>> model.spike_times
array([  1.75000000e-03,   3.97500000e-02,   4.06000000e-02, ...,
         1.19933500e+02,   1.19937650e+02,   1.19999150e+02])
```

```python
>>> model.spike_clusters
array([20, 10, 25, ..., 10, 12, 20], dtype=uint32)
```

```python
>>> model.cluster_ids
array([ 2,  3,  4,  5,  6,  7,  8,  9, 10, 11, 12, 13, 14, 15, 16, 17, 18,
       19, 20, 21, 22, 23, 24, 25])
```

```python
>>> model.cluster_groups
{2: 3,
 3: 3,
 4: 3,
 5: 3,
 6: 3,
 7: 3,
 8: 3,
 9: 3,
 10: 3,
 11: 3,
 12: 3,
 13: 3,
 14: 3,
 15: 3,
 16: 3,
 17: 3,
 18: 3,
 19: 3,
 20: 3,
 21: 3,
 22: 3,
 23: 3,
 24: 3,
 25: 3}
```

Here are the default cluster groups:

```python
>>> model.default_cluster_groups
{0: 'Noise', 1: 'MUA', 2: 'Good', 3: 'Unsorted'}
```

### Metadata


### Features


### Waveforms


### Extracellular traces


### Working with multiple clusterings


### Modifying spike clusters manually
