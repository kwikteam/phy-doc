## Spike detection and automatic clustering

*phy* 0.2.0 provides automatic spike detection and clustering algorithms.

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
