# KWIK format

**NOTE: this format occasionally changes. Subscribe to the [Klustaviewas mailing list](https://groups.google.com/forum/#!forum/klustaviewas) to be kept up to date.**

This document describes the current working version of the "KWIK format" as implemented in `phy`. This is almost identical to that in **KlustaViewa 0.3.0** with the major change being the omission of stored waveforms in the `KWX` file; these are instead loaded dynamically from raw data on-the-fly. Files created in `phy` are thus untested in KlustaViewa and unlikely to work correctly.

## Quick info

You can open all the KWIK files in recent versions of MATLAB (they have [native support for HDF5](http://uk.mathworks.com/help/matlab/hdf5.html)).

To read the spike times and cluster numbers, type (`filename` is the `.kwik` file):

```matlab
hdf5read(filename, '/channel_groups/0/spikes/time_samples');
hdf5read(filename, '/channel_groups/0/spikes/clusters/main');
```

The `channel_group` number is the shank number (indexing starts at 0).

## Data files

All files are in HDF5.

  * The data are stored in the following files:

      * the **KWIK** file is the main file, it contains:
          * all metadata
          * spike times
          * clusters
          * recording for each spike time
          * probe-related information
          * information about channels
          * information about cluster groups
          * events, event_types
          * aesthetic information, user data, application data
      * the **KWX** file contains the **spiking data**: features, masks
      * the **KWD** files (deprecated in `phy` in favour of reading off the raw data file) contains the **raw/filtered recordings**

  * Once spike sorting is finished, one can discard the KWX and KWD files and just keep the KWIK file for subsequent analysis (where spike sorting information like features, waveforms... are not necessary).

  * All files contain a **version number** in `/` (`kwik_version` attribute), which is an integer equal to 2 now.

  * There can be other HDF5 .kwd files with similar structures, containing more specific information related to particular experiments and protocols. This should make possible the compatibility with [Open Ephys](http://www.open-ephys.org).

  * The input files the user provides to the programs to generate these data are:

      * the **raw data** coming out from the acquisition system, in any proprietary format (NS5, etc.)
      * processing parameters (PRM file) and description of the probe (PRB file)

  * There's support for multiple clusterings. By default, there are two clusterings: `main` (manual) and `original` (output of KlustaKwik). More clusterings can be added.

  * The mapping between the columns in the raw data array (old `.dat` file, or new `.kwd` file), and the channels (defined in the probe file), is trivial. In other words, column #i in the raw data array corresponds to channel #i. Channels have absolute indices spanning all shanks.

### KWIK

Below is the structure of the KWIK file.Everything is a group, except fields with a star (*) which are either leaves (datasets: arrays or tables) or attributes of their parents.

[X] is 0, 1, 2...

    /kwik_version* [=2]
    /name*
    /application_data
        spikedetekt
            MY_SPIKEDETEKT_PARAM*
            ...
    /user_data
    /channel_groups
        [X]  # Absolute channel group index from 0 to Nchannelgroups-1
            name*
            channel_order*  # ordered list of channels, as specified in the PRB file
            adjacency_graph* [Kx2 array of integers]
            application_data
            user_data
            channels
                [X]  # Relative channel index from 0 to shanksize-1
                    name*
                    ignored*
                    position* (a pair (x, y) in microns relative to the whole multishank probe)
                    voltage_gain* (a float32 number, in microvolts)
                    display_threshold*
                    application_data
                        klustaviewa
                        spikedetekt
                    user_data
            spikes
                time_samples* [N-long EArray of UInt64]
                time_fractional* [N-long EArray of UInt8]
                recording* [N-long EArray of UInt16]
                clusters
                    main* [N-long EArray of UInt32]
                    original* [N-long EArray of UInt32]
                features_masks
                    hdf5_path* [='{kwx}/channel_groups/X/features_masks']
                waveforms_raw
                    hdf5_path* [='{kwx}/channel_groups/X/waveforms_raw']
                waveforms_filtered
                    hdf5_path* [='{kwx}/channel_groups/X/waveforms_filtered']
            clusters
                [clustering_name]
                    [X]  # Cluster number from 0 to Nclusters-1 (unique within a given channel group & clustering name)
                        application_data
                            klustaviewa
                                color*
                        cluster_group*
                        mean_waveform_raw*
                        mean_waveform_filtered*
                        quality_measures
                            isolation_distance*
                            matrix_isolation*
                            refractory_violation*
                            amplitude*
                        user_data
                            ...
            cluster_groups
                [clustering_name]
                    [X]  # Cluster group number
                        name*
                        application_data
                            klustaviewa
                                color*
                        user_data
    /recordings
        [X]  # Recording index from 0 to Nrecordings-1
            name*
            start_time*
            start_sample*
            sample_rate*
            bit_depth*
            band_high*
            band_low*
            raw
                hdf5_path* [='{raw.kwd}/recordings/X']
            high
                hdf5_path* [='{high.kwd}/recordings/X']
            low
                hdf5_path* [='{low.kwd}/recordings/X']
            user_data
    /event_types
        [X]  # The name of the event type.
            user_data
            application_data
                klustaviewa
                    color*
            events
                time_samples* [N-long EArray of UInt64]
                recording* [N-long EArray of UInt16]
                user_data [group or EArray]

### KWX

The **KWX** file contains spike-sorting-related information.

    /kwik_version* [=2]
    /channel_groups
        [X]
            features_masks* [(N x NFEATURES x 2) EArray of Float32]
            waveforms_raw* [(N x NWAVESAMPLES x NCHANNELS) EArray of Int16] # DEPRECATED IN PHY
            waveforms_filtered* [(N x NWAVESAMPLES x NCHANNELS) EArray of Int16] # DEPRECATED IN PHY

### KWD

The **KWD** files contain the original recordings (raw and filtered). Each file among the `.raw`, `.high` and `.low` contains:

    /kwik_version* [=2]
    /recordings
        [X]
            data* [(Nsamples x Nchannels) EArray of Int16]
            filter
                name*
                param1*
            downsample_factor*

            # The following metadata fields are duplicated from the .kwik files
            # and are here for convenience only. The KWIK programs will not read
            # them, they are only there for other programs.
            name
            start_time
            start_sample
            sample_rate
            bit_depth

            application_data
                band_high
                band_low

## User files

### PRB

This Python script describes the probe used for the experiment: its geometry and topology. It must define a `channel_groups` variable, which is a list where each item is a dictionary with the following keys:

* channels
* graph
* geometry

**Note**: the channel order used in the dat file is specified in the `channels` property (the order matters).

Example:

    channel_groups = {
                0: {
                    "channels": [0, 1, 2, 3],  # list of channels to keep
                    "graph": [[0, 1], [2, 3], ...],  # list of pairs of connected (nearby) channels
                    "geometry": {0: [0.1, 0.2], 1: [0.3, 0.4], ...}  # (x,y) coordinates of each channel (for visualization purposes only)
                    },
                1: {
                    "channels": [4, 5, 6, 7],
                    "graph": [[4, 5], [6, 7], ...],
                    "geometry": {4: [0.1, 0.2], 5: [0.3, 0.4], ...}
                    }
            }


### PRM

This Python script defines all parameters necessary for the programs to process, open and display the data.

    experiment_name = 'hybrid_10sec'
    prb_file = '1x32_buzsaki'

    traces = dict(
        raw_data_files=[experiment_name + '.dat'],
        voltage_gain=10.,
        sample_rate=20000,
        n_channels=32,
    )

    spikedetekt = dict(
        filter_low=500.,  # Low pass frequency (Hz)
        filter_high_factor=0.95 * .5,
        filter_butter_order=3,  # Order of Butterworth filter.

        filter_lfp_low=0,  # LFP filter low-pass frequency
        filter_lfp_high=300,  # LFP filter high-pass frequency

        chunk_size_seconds=1,
        chunk_overlap_seconds=.015,

        n_excerpts=50,
        excerpt_size_seconds=1,
        threshold_strong_std_factor=4.5,
        threshold_weak_std_factor=2.,
        detect_spikes='negative',

        connected_component_join_size=1,

        extract_s_before=16,
        extract_s_after=16,

        n_features_per_channel=3,  # Number of features per channel.
        pca_n_waveforms_max=10000,
    )
