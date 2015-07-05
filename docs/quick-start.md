# Quick start guide

Here is a short tutorial for phy, focusing on manual clustering.

## Installation

https://github.com/kwikteam/phy-doc/blob/master/install.md

## Importing phy

```python
>>> import phy
>>> # Necessary when using the manual clustering GUI in the notebook:
... phy.enable_qt()
2015-05-26 14:31:28  dock:142                Qt event loop activated.
```

## Downloading a test dataset

Let's download a test dataset in Kwik format:

```python
>>> phy.download_test_data('test_hybrid_120sec')
2015-05-26 14:31:30  datasets:50             Downloading http://phy.cortexlab.net/data/test_hybrid_120sec.kwik...
2015-05-26 14:31:30  datasets:50             Downloading http://phy.cortexlab.net/data/test_hybrid_120sec.kwx...
2015-05-26 14:31:42  datasets:50             Downloading http://phy.cortexlab.net/data/test_hybrid_120sec.raw.kwd...
```

This creates a `test_hybrid_120sec` subdirectory with three files:

```python
>>> %ls test_hybrid_120sec
[0m[01;32mtest_hybrid_120sec.kwik[0m*  [01;32mtest_hybrid_120sec.kwx[0m*  [01;32mtest_hybrid_120sec.raw.kwd[0m*
```

## Creating a manual clustering session

```python
>>> from phy.cluster.manual import Session
```

We create a `Session` and pass the path to the `.kwik` file:

```python
>>> session = Session('test_hybrid_120sec/test_hybrid_120sec.kwik')
2015-05-26 14:31:48  session:117             Saving a backup of the Kwik file in test_hybrid_120sec/test_hybrid_120sec.kwik.bak.
Features and masks initialized.[K
Features and masks initialized.[K
Waveforms initialized.[K
Statistics initialized.[K
```

**Side note**: A backup of the `.kwik` file has been automatically-created, as well as an internal cluster store that acts as a cache (needed for performance reasons):

```python
>>> %ls test_hybrid_120sec/test_hybrid_120sec.phy/cluster_store/0/main
[0m[01;32m10.features[0m*        [01;32m16.masks[0m*           [01;32m21.mean_features[0m*   [01;32m4.mean_masks[0m*
[01;32m10.masks[0m*           [01;32m16.mean_features[0m*   [01;32m21.mean_masks[0m*      [01;32m4.mean_waveforms[0m*
[01;32m10.mean_features[0m*   [01;32m16.mean_masks[0m*      [01;32m21.mean_waveforms[0m*  [01;32m4.waveforms[0m*
[01;32m10.mean_masks[0m*      [01;32m16.mean_waveforms[0m*  [01;32m21.waveforms[0m*       [01;32m5.features[0m*
[01;32m10.mean_waveforms[0m*  [01;32m16.waveforms[0m*       [01;32m22.features[0m*        [01;32m5.masks[0m*
[01;32m10.waveforms[0m*       [01;32m17.features[0m*        [01;32m22.masks[0m*           [01;32m5.mean_features[0m*
[01;32m11.features[0m*        [01;32m17.masks[0m*           [01;32m22.mean_features[0m*   [01;32m5.mean_masks[0m*
[01;32m11.masks[0m*           [01;32m17.mean_features[0m*   [01;32m22.mean_masks[0m*      [01;32m5.mean_waveforms[0m*
[01;32m11.mean_features[0m*   [01;32m17.mean_masks[0m*      [01;32m22.mean_waveforms[0m*  [01;32m5.waveforms[0m*
[01;32m11.mean_masks[0m*      [01;32m17.mean_waveforms[0m*  [01;32m22.waveforms[0m*       [01;32m6.features[0m*
[01;32m11.mean_waveforms[0m*  [01;32m17.waveforms[0m*       [01;32m23.features[0m*        [01;32m6.masks[0m*
[01;32m11.waveforms[0m*       [01;32m18.features[0m*        [01;32m23.masks[0m*           [01;32m6.mean_features[0m*
[01;32m12.features[0m*        [01;32m18.masks[0m*           [01;32m23.mean_features[0m*   [01;32m6.mean_masks[0m*
[01;32m12.masks[0m*           [01;32m18.mean_features[0m*   [01;32m23.mean_masks[0m*      [01;32m6.mean_waveforms[0m*
[01;32m12.mean_features[0m*   [01;32m18.mean_masks[0m*      [01;32m23.mean_waveforms[0m*  [01;32m6.waveforms[0m*
[01;32m12.mean_masks[0m*      [01;32m18.mean_waveforms[0m*  [01;32m23.waveforms[0m*       [01;32m7.features[0m*
[01;32m12.mean_waveforms[0m*  [01;32m18.waveforms[0m*       [01;32m24.features[0m*        [01;32m7.masks[0m*
[01;32m12.waveforms[0m*       [01;32m19.features[0m*        [01;32m24.masks[0m*           [01;32m7.mean_features[0m*
[01;32m13.features[0m*        [01;32m19.masks[0m*           [01;32m24.mean_features[0m*   [01;32m7.mean_masks[0m*
[01;32m13.masks[0m*           [01;32m19.mean_features[0m*   [01;32m24.mean_masks[0m*      [01;32m7.mean_waveforms[0m*
[01;32m13.mean_features[0m*   [01;32m19.mean_masks[0m*      [01;32m24.mean_waveforms[0m*  [01;32m7.waveforms[0m*
[01;32m13.mean_masks[0m*      [01;32m19.mean_waveforms[0m*  [01;32m24.waveforms[0m*       [01;32m8.features[0m*
[01;32m13.mean_waveforms[0m*  [01;32m19.waveforms[0m*       [01;32m25.features[0m*        [01;32m8.masks[0m*
[01;32m13.waveforms[0m*       [01;32m2.features[0m*         [01;32m25.masks[0m*           [01;32m8.mean_features[0m*
[01;32m14.features[0m*        [01;32m2.masks[0m*            [01;32m25.mean_features[0m*   [01;32m8.mean_masks[0m*
[01;32m14.masks[0m*           [01;32m2.mean_features[0m*    [01;32m25.mean_masks[0m*      [01;32m8.mean_waveforms[0m*
[01;32m14.mean_features[0m*   [01;32m2.mean_masks[0m*       [01;32m25.mean_waveforms[0m*  [01;32m8.waveforms[0m*
[01;32m14.mean_masks[0m*      [01;32m2.mean_waveforms[0m*   [01;32m25.waveforms[0m*       [01;32m9.features[0m*
[01;32m14.mean_waveforms[0m*  [01;32m2.waveforms[0m*        [01;32m3.features[0m*         [01;32m9.masks[0m*
[01;32m14.waveforms[0m*       [01;32m20.features[0m*        [01;32m3.masks[0m*            [01;32m9.mean_features[0m*
[01;32m15.features[0m*        [01;32m20.masks[0m*           [01;32m3.mean_features[0m*    [01;32m9.mean_masks[0m*
[01;32m15.masks[0m*           [01;32m20.mean_features[0m*   [01;32m3.mean_masks[0m*       [01;32m9.mean_waveforms[0m*
[01;32m15.mean_features[0m*   [01;32m20.mean_masks[0m*      [01;32m3.mean_waveforms[0m*   [01;32m9.waveforms[0m*
[01;32m15.mean_masks[0m*      [01;32m20.mean_waveforms[0m*  [01;32m3.waveforms[0m*        [01;32mwaveforms_spikes[0m*
[01;32m15.mean_waveforms[0m*  [01;32m20.waveforms[0m*       [01;32m4.features[0m*
[01;32m15.waveforms[0m*       [01;32m21.features[0m*        [01;32m4.masks[0m*
[01;32m16.features[0m*        [01;32m21.masks[0m*           [01;32m4.mean_features[0m*
```

## Inspect the data

The dataset is now loaded. Let's inspect it:

```python
>>> session.model.describe()
Kwik file               test_hybrid_120sec/test_hybrid_120sec.kwik
Recordings              1
List of shanks          0*
Clusterings             main*, original
Channels                32
Spikes                  18539
Clusters                24
Duration                120s
```

Use tab completion to discover the list of properties and methods: type `session.model.` then press `tab`.

## Start the manual clustering GUI

```python
>>> session.show_gui()
<phy.cluster.manual.gui.ClusterManualGUI at 0x7f7e6c1031d0>
```

![GUI](images/quick-start-gui.png)

Press `space` and `shift+space` to go through the list of best clusters. Press `enter` to pin the best cluster and go through the list of closest matches.  Press `backspace` to unpin. Press `h` to see the other shortcuts.
