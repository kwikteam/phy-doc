## Working with Kwik files

> phy 0.1.0 only supports files in the Kwik format. Future versions may support other file formats.

The [**Kwik format**](https://github.com/klusta-team/kwiklib/wiki/Kwik-format) features several files:

* `.kwik`: metadata, spikes, clusters
* `.kwx`: features, waveforms
* `.raw.kwd`: raw extracellular traces

phy 0.1.0 requires you to provide these files. You can use the [`klusta`](https://github.com/klusta-team/example) program to generate them from raw data in `.dat` format (flat binary file with int16 samples). As part of this process, spikes are detected, extracted, and grouped into putative clusters.

> OpenEphys can also generate Kwik files. Feel free to contact us if you get any problem or incompatibility.

phy 0.2.0 will integrate the entire toolchain to go from raw data to Kwik files, and you won't need to use the external `klusta` program anymore.

> Currently, the `klusta` program may complete in minutes to hours, days, or even weeks for the largest datasets. We will make this process considerably faster (notably using parallelization) in phy 0.2.0 and later.


### Opening a dataset


### Spikes and clusters


### Metadata


### Features


### Waveforms


### Extracellular traces


### Working with multiple clusterings


### Modifying spike clusters manually



