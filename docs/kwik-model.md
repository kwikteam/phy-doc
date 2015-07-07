## Working with Kwik files

> phy 0.2.0 only supports files in the Kwik format. Future versions may support other file formats.

The [**Kwik format**](kwik-format.md) features several files:

* `.kwik`: metadata, spikes, clusters
* `.kwx`: masks, features
* `.dat`: raw extracellular traces

> OpenEphys can also generate Kwik files. Feel free to contact us if you get any problem or incompatibility.


### Opening a dataset

Open a Kwik dataset with:

```python
>>> from phy.io import KwikModel
```

Let's assume that we have a Kwik dataset in the current directory:

```python
>>> %ls data/hybrid*
[0m[01;32mdata/hybrid_10sec.dat[0m*   [01;32mdata/hybrid_10sec.kwik.bak[0m*  [01;32mdata/hybrid_10sec.log[0m*
[01;32mdata/hybrid_10sec.kwik[0m*  [01;32mdata/hybrid_10sec.kwx[0m*       [01;32mdata/hybrid_10sec.prm[0m*
```

```python
>>> kwik_path = 'data/hybrid_10sec.kwik'
>>> model = KwikModel(kwik_path)
```

Now, you can use the `model` to access your data. See the [API](api.md#phyiokwikmodel) for more details. In IPython, use tab completion to discover the attributes and methods of the object.

```python
>>> model.describe()
Kwik file               /data/git/phy/doc/docs/data/hybrid_10sec.kwik
Recordings              1
List of shanks          0*
Clusterings             main*, empty, kk2_current, original
Channels                32
Spikes                  1603
Clusters                19
Duration                10s
```

### Spikes and clusters

```python
>>> model.spike_samples
array([    35,    812,    833, ..., 197537, 197550, 197670], dtype=uint64)
```

```python
>>> model.spike_times
array([  1.75000000e-03,   4.06000000e-02,   4.16500000e-02, ...,
         9.87685000e+00,   9.87750000e+00,   9.88350000e+00])
```

```python
>>> model.spike_clusters
array([19, 16,  6, ...,  3, 16, 14], dtype=int32)
```

```python
>>> model.cluster_ids
array([ 0,  2,  3,  4,  5,  6,  7,  8,  9, 10, 11, 12, 13, 14, 15, 16, 17,
       18, 19])
```

```python
>>> model.cluster_groups
{0: 3,
 2: 3,
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
 19: 3}
```

Here are the default cluster groups:

```python
>>> model.default_cluster_groups
{0: 'Noise', 1: 'MUA', 2: 'Good', 3: 'Unsorted'}
```

### Metadata

The metadata contains information from the PRM file (used by the spike detection algorithm):

```python
>>> model.metadata
{'chunk_overlap_seconds': 0.014999999999999999,
 'chunk_size_seconds': 1,
 'connected_component_join_size': 1,
 'detect_spikes': 'negative',
 'dtype': 'int16',
 'excerpt_size_seconds': 1,
 'extract_s_after': 16,
 'extract_s_before': 16,
 'filter_butter_order': 3,
 'filter_high_factor': 0.47499999999999998,
 'filter_low': 500.0,
 'n_channels': 32,
 'n_excerpts': 50,
 'n_features_per_channel': 3,
 'pca_n_waveforms_max': 10000,
 'prb_file': '1x32_buzsaki',
 'raw_data_files': 'hybrid_10sec.dat',
 'sample_rate': 20000,
 'threshold_strong_std_factor': 4.5,
 'threshold_weak_std_factor': 2.0,
 'use_single_threshold': 0,
 'weight_power': 2}
```

### Masks and features

You have two ways to access masks and features. One is faster when you want to access to particular spikes, the other when you want to access to particular clusters. The two methods only differ in the speed of data access. The second method is described in the manual clustering guide.

#### Accessing spikes

The `model.masks` acts as a memory-mapped array to HDF5. You can access the masks of individual spikes. The shape is `(n_spikes, n_channels)`.

```python
>>> model.masks.shape
(1603, 32)
```

> This is an instance of `PartialArray`: in the current file format, masks and features are stored in the same array, for historical reasons. This partial array dyamically maps indexing to the original HDF5 array. This is why this object is not just an `h5py` dataset.

Mask vector of spike number 10:

```python
>>> model.masks[10]
array([ 0.,  0.,  0.,  0.,  0.,  0.,  0.,  0.,  0.,  0.,  0.,  1.,  0.,
        0.,  0.,  0.,  0.,  0.,  0.,  0.,  0.,  0.,  0.,  0.,  0.,  0.,
        0.,  0.,  0.,  0.,  0.,  0.], dtype=float32)
```

Masks of the first ten spikes:

```python
>>> model.masks[:10].shape
(10, 32)
```

Masks of three spikes:

```python
>>> model.masks[[10, 20, 30]].shape
(3, 32)
```

This is the same thing for the features, except that this is now a 2D `(n_spikes, n_channels * n_features)` array:

```python
>>> model.features.shape
(1603, 96)
```

### Waveforms

Waveforms are dynamically fetched and filtered from the raw data file. This is all transparent, and you can access them as if it was a `(n_spikes, n_samples, n_channels)` array:

```python
>>> model.waveforms
<phy.io.kwik.model.SpikeLoader at 0x7ff4b39a5ba8>
```

```python
>>> model.waveforms.shape
(1603, 32, 32)
```

```python
>>> model.waveforms[:3].shape
(3, 32, 32)
```

### Extracellular traces

The following is a memory-mapped array from the `.raw.kwd` file:

```python
>>> model.traces.shape
(200000, 32)
```

### Working with multiple shanks and clusterings

```python
>>> model.channel_groups
[0]
```

```python
>>> model.channel_group
0
```

```python
>>> model.clusterings
['main', 'empty', 'kk2_current', 'original']
```

```python
>>> model.clustering
'main'
```

Here is how to change the current clustering (by default, the **main** clustering is the one that you modify during manual clustering, while the **original** one comes from the automatic clustering algorithm like KlustaKwik):

```python
>>> model.clustering = 'original'
```

```python
>>> model.spike_clusters
array([19, 16,  6, ...,  3, 16, 14], dtype=int32)
```

### Modifying the data

If you want to modify the clusters, you need to start a manual clustering session, as described later in the user guide.
