# API documentation of phy

Spike sorting and ephys data analysis for 1000 channels and beyond.

## Table of contents

### [phy.cluster](#phycluster)



### [phy.cluster.manual](#phyclustermanual)

* [phy.cluster.manual.BaseClusterViewModel](#phyclustermanualbaseclusterviewmodel)
* [phy.cluster.manual.ClusterManualGUI](#phyclustermanualclustermanualgui)
* [phy.cluster.manual.Clustering](#phyclustermanualclustering)
* [phy.cluster.manual.CorrelogramViewModel](#phyclustermanualcorrelogramviewmodel)
* [phy.cluster.manual.FeatureViewModel](#phyclustermanualfeatureviewmodel)
* [phy.cluster.manual.HTMLClusterViewModel](#phyclustermanualhtmlclusterviewmodel)
* [phy.cluster.manual.StatsViewModel](#phyclustermanualstatsviewmodel)
* [phy.cluster.manual.TraceViewModel](#phyclustermanualtraceviewmodel)
* [phy.cluster.manual.WaveformViewModel](#phyclustermanualwaveformviewmodel)
* [phy.cluster.manual.Wizard](#phyclustermanualwizard)


### [phy.electrode](#phyelectrode)

* [phy.electrode.load_probe](#phyelectrodeload_probename)
* [phy.electrode.MEA](#phyelectrodemea)


### [phy.gui](#phygui)

* [phy.gui.enable_qt](#phyguienable_qt)
* [phy.gui.qt_app](#phyguiqt_appargs-kwds)
* [phy.gui.run_qt_app](#phyguirun_qt_app)
* [phy.gui.start_qt_app](#phyguistart_qt_app)
* [phy.gui.BaseGUI](#phyguibasegui)
* [phy.gui.BaseViewModel](#phyguibaseviewmodel)
* [phy.gui.DockWindow](#phyguidockwindow)
* [phy.gui.HTMLViewModel](#phyguihtmlviewmodel)
* [phy.gui.WidgetCreator](#phyguiwidgetcreator)


### [phy.io](#phyio)

* [phy.io.create_kwik](#phyiocreate_kwikprm_filenone-kwik_pathnone-overwritefalse-probenone-kwargs)
* [phy.io.open_h5](#phyioopen_h5filename-modenone)
* [phy.io.read_dat](#phyioread_datfilename-dtypenone-shapenone-offset0-n_channelsnone)
* [phy.io.read_kwd](#phyioread_kwdkwd_handle)
* [phy.io.BaseModel](#phyiobasemodel)
* [phy.io.BaseSession](#phyiobasesession)
* [phy.io.ClusterStore](#phyioclusterstore)
* [phy.io.File](#phyiofile)
* [phy.io.KwikCreator](#phyiokwikcreator)
* [phy.io.KwikModel](#phyiokwikmodel)
* [phy.io.StoreItem](#phyiostoreitem)


### [phy.plot](#phyplot)

* [phy.plot.plot_correlograms](#phyplotplot_correlogramsargs-kwargs)
* [phy.plot.plot_features](#phyplotplot_featuresargs-kwargs)
* [phy.plot.plot_traces](#phyplotplot_tracesargs-kwargs)
* [phy.plot.plot_waveforms](#phyplotplot_waveformsargs-kwargs)
* [phy.plot.BaseSpikeCanvas](#phyplotbasespikecanvas)
* [phy.plot.BaseSpikeVisual](#phyplotbasespikevisual)
* [phy.plot.CorrelogramView](#phyplotcorrelogramview)
* [phy.plot.FeatureView](#phyplotfeatureview)
* [phy.plot.FeatureVisual](#phyplotfeaturevisual)
* [phy.plot.PanZoom](#phyplotpanzoom)
* [phy.plot.PanZoomGrid](#phyplotpanzoomgrid)
* [phy.plot.TraceView](#phyplottraceview)
* [phy.plot.WaveformView](#phyplotwaveformview)
* [phy.plot.WaveformVisual](#phyplotwaveformvisual)


### [phy.stats](#phystats)

* [phy.stats.pairwise_correlograms](#phystatspairwise_correlogramsspike_samples-spike_clusters-binsizenone-winsize_binsnone)


### [phy.traces](#phytraces)

* [phy.traces.compute_threshold](#phytracescompute_thresholdarr-single_thresholdtrue-std_factornone)
* [phy.traces.Filter](#phytracesfilter)
* [phy.traces.FloodFillDetector](#phytracesfloodfilldetector)
* [phy.traces.PCA](#phytracespca)
* [phy.traces.SpikeLoader](#phytracesspikeloader)
* [phy.traces.Thresholder](#phytracesthresholder)
* [phy.traces.WaveformExtractor](#phytraceswaveformextractor)
* [phy.traces.WaveformLoader](#phytraceswaveformloader)
* [phy.traces.Whitening](#phytraceswhitening)


### [phy.utils](#phyutils)

* [phy.utils.debug](#phyutilsdebugmsg)
* [phy.utils.download_file](#phyutilsdownload_fileurl-output_pathnone)
* [phy.utils.download_sample_data](#phyutilsdownload_sample_datafilename-output_dirnone-basecortexlab)
* [phy.utils.info](#phyutilsinfomsg)
* [phy.utils.register](#phyutilsregisterlogger)
* [phy.utils.set_level](#phyutilsset_levellevel)
* [phy.utils.unregister](#phyutilsunregisterlogger)
* [phy.utils.warn](#phyutilswarnmsg)
* [phy.utils.Bunch](#phyutilsbunch)
* [phy.utils.EventEmitter](#phyutilseventemitter)
* [phy.utils.ProgressReporter](#phyutilsprogressreporter)
* [phy.utils.Settings](#phyutilssettings)




## phy.cluster

Automatic and manual clustering facilities.

## phy.cluster.manual

Manual clustering facilities.

### phy.cluster.manual.BaseClusterViewModel

Interface between a view and a model.

#### Methods

##### BaseClusterViewModel.close()

Close the view.

##### BaseClusterViewModel.connect(*args, **kwargs)

Connect a callback function.

##### BaseClusterViewModel.emit(*args, **kwargs)

Emit an event.

##### BaseClusterViewModel.exported_params(save_size_pos=True)

Return a dictionary of variables to save when the view is closed.

##### BaseClusterViewModel.get_params(cls, settings)

Return the parameter values for the creation of the view.

##### BaseClusterViewModel.imported_params(cls)

All parameter names to be imported on object creation.

##### BaseClusterViewModel.on_close()

Called when the model is closed.

May be overriden.

##### BaseClusterViewModel.on_cluster(up)

Called when a clustering action occurs.

May be overriden.

##### BaseClusterViewModel.on_open()

Initialize the view after the model has been loaded.

May be overriden.

##### BaseClusterViewModel.on_select(cluster_ids, **kwargs)

Update the view after a new selection has been made.

Must be overriden.

##### BaseClusterViewModel.select(cluster_ids, **kwargs)

Select a list of clusters.

##### BaseClusterViewModel.show()

Show the view.

#### Properties

##### BaseClusterViewModel.cluster_ids

Selected clusters.

##### BaseClusterViewModel.model

The model.

##### BaseClusterViewModel.n_clusters

Number of selected clusters.

##### BaseClusterViewModel.name

The view model's name.

##### BaseClusterViewModel.store

The cluster store.

##### BaseClusterViewModel.view

The underlying view.

##### BaseClusterViewModel.wizard

The wizard.

### phy.cluster.manual.ClusterManualGUI

Manual clustering GUI.

This object represents a main window with:

* multiple views
* high-level clustering methods
* global keyboard shortcuts

*Events*

cluster
select
request_save

#### Methods

##### ClusterManualGUI.add_view(item, title=None, **kwargs)

Add a new view instance to the GUI.

##### ClusterManualGUI.close()

Close the GUI.

##### ClusterManualGUI.connect(func=None, event=None, set_method=False)

Register a callback function to a given event.

To register a callback function to the `spam` event, where `obj` is
an instance of a class deriving from `EventEmitter`:

```python
@obj.connect
def on_spam(arg1, arg2):
    pass
```

This is called when `obj.emit('spam', arg1, arg2)` is called.

Several callback functions can be registered for a given event.

The registration order is conserved and may matter in applications.

##### ClusterManualGUI.connect_views(name_0, name_1)

Decorator for a function called on every pair of views of a
given type.

##### ClusterManualGUI.disable_snippet_mode()



##### ClusterManualGUI.emit(event, *args, **kwargs)

Call all callback functions registered with an event.

Any positional and keyword arguments can be passed here, and they will
be fowarded to the callback functions.

Return the list of callback return results.

##### ClusterManualGUI.enable_snippet_mode()



##### ClusterManualGUI.exit()

Close the GUI.

##### ClusterManualGUI.first()

Go to the first cluster proposed by the wizard.

##### ClusterManualGUI.get_views(*names)

Return the list of views of a given type.

##### ClusterManualGUI.isVisible()



##### ClusterManualGUI.last()

Go to the last cluster proposed by the wizard.

##### ClusterManualGUI.merge(clusters=None)

Merge some clusters.

##### ClusterManualGUI.move(clusters, group)

Move some clusters to a cluster group.

Here is the list of cluster groups:

* 0=Noise
* 1=MUA
* 2=Good
* 3=Unsorted

##### ClusterManualGUI.next()

Go to the next cluster proposed by the wizard.

##### ClusterManualGUI.on_open()

Reinitialize the GUI after new data has been loaded.

##### ClusterManualGUI.pin()

Pin the current best cluster.

##### ClusterManualGUI.previous()

Go to the previous cluster proposed by the wizard.

##### ClusterManualGUI.process_snippet(snippet)

Processes a snippet.

May be overriden.

##### ClusterManualGUI.redo()

Redo the last undone action.

##### ClusterManualGUI.reset()

Remove all registered callbacks.

##### ClusterManualGUI.reset_gui()

Reset the GUI configuration.

##### ClusterManualGUI.reset_wizard()

Restart the wizard.

##### ClusterManualGUI.save()

Save the changes.

##### ClusterManualGUI.select(cluster_ids, **kwargs)

Select clusters.

##### ClusterManualGUI.show()

Show the GUI

##### ClusterManualGUI.show_features_time()

Set the x dimension to time in all feature views.

##### ClusterManualGUI.show_shortcuts()

Show the list of all keyboard shortcuts.

##### ClusterManualGUI.split(spikes=None)

Make a new cluster out of some spikes.

*Notes*

Spikes belonging to affected clusters, but not part of the `spikes`
array, will move to brand new cluster ids. This is because a new
cluster id must be used as soon as a cluster changes.

##### ClusterManualGUI.start()

Start the wizard.

##### ClusterManualGUI.toggle_correlogram_normalization()

Toggle CCG normalization in the correlograms views.

##### ClusterManualGUI.toggle_waveforms_mean()

Toggle mean mode in the waveform views.

##### ClusterManualGUI.toggle_waveforms_overlap()

Toggle cluster overlap in the waveform views.

##### ClusterManualGUI.unconnect(*funcs)

Unconnect specified callback functions.

##### ClusterManualGUI.undo()

Undo the last clustering action.

##### ClusterManualGUI.unpin()

Unpin the current best cluster.

##### ClusterManualGUI.view_count()

Number of views of each type.

#### Properties

##### ClusterManualGUI.cluster_ids

Array of all cluster ids used in the current clustering.

##### ClusterManualGUI.main_window

Main Qt window.

##### ClusterManualGUI.n_clusters

Number of clusters in the current clustering.

##### ClusterManualGUI.selected_clusters

The list of selected clusters.

##### ClusterManualGUI.status_message

Message in the status bar.

##### ClusterManualGUI.title

Title of the main window.

##### ClusterManualGUI.views

List of all open views.

### phy.cluster.manual.Clustering

Handle cluster changes in a set of spikes.

*Features*

* List of clusters appearing in a `spike_clusters` array
* Dictionary of spikes per cluster
* Merge
* Split and assign
* Undo/redo stack

*Notes*

The undo stack works by keeping the list of all spike cluster changes
made successively. Undoing consists of reapplying all changes from the
original `spike_clusters` array, except the last one.

*UpdateInfo*

Most methods of this class return an UpdateInfo instance. This object
contains information about the clustering changes done by the operation.
This object is used throughout the `phy.cluster.manual` package to let
different classes know about clustering changes.

`UpdateInfo` is a dictionary that also supports dot access (`Bunch` class).
The keys are the following:


* `description` (str)

    Description of the clustering operation. It is one of  `merge`,
    `assign`, or `metadata_group`.

* `history` (str or None)

    This is None except when it is `undo` or `redo`.

* `spikes` (array)

    Array of all spike ids affected by the update.

* `added` (list)

    New cluster ids created by this operation.

* `deleted` (list)

    Cluster ids that are deleted following this operation.

* `descendants` (list)

    List of `(old, new)` pairs of cluster ids to track provenance
    information about the clusters.

* `metadata_changed` (list)

    List of clusters with changed metadata (cluster group changes)

* `old_spikes_per_cluster` (dict)

    Dictionary of `{cluster: spikes}` for the old clusters and
    old clustering.

* `new_spikes_per_cluster` (dict)

    Dictionary of `{cluster: spikes}` for the new clusters and
    new clustering.

#### Methods

##### Clustering.assign(spike_ids, spike_clusters_rel=0)

Make new spike cluster assignements.

*Parameters*


* `spike_ids` (array-like)

    List of spike ids.

* `spike_clusters_rel` (array-like)

    Relative cluster ids of the spikes in `spike_ids`. This
    must have the same size as `spike_ids`.

*Returns*


* `up` (UpdateInfo instance)


*Note*

`spike_clusters_rel` contain *relative* cluster indices. Their values
don't matter: what matters is whether two give spikes
should end up in the same cluster or not. Adding a constant number
to all elements in `spike_clusters_rel` results in exactly the same
operation.

The final cluster ids are automatically generated by the `Clustering`
class. This is because we must ensure that all modified clusters
get brand new ids. The whole library is based on the assumption that
cluster ids are unique and "disposable". Changing a cluster always
results in a new cluster id being assigned.

If a spike is assigned to a new cluster, then all other spikes
belonging to the same cluster are assigned to a brand new cluster,
even if they were not changed explicitely by the `assign()` method.

In other words, the list of spikes affected by an `assign()` is almost
always a strict superset of the `spike_ids` parameter. The only case
where this is not true is when whole clusters change: this is called
a merge. It is implemented in a separate `merge()` method because it
is logically much simpler, and faster to execute.

##### Clustering.merge(cluster_ids, to=None)

Merge several clusters to a new cluster.

*Parameters*


* `cluster_ids` (array-like)

    List of clusters to merge.

* `to` (integer or None)

    The id of the new cluster. By default, this is `new_cluster_id()`.

*Returns*


* `up` (UpdateInfo instance)


##### Clustering.new_cluster_id()

Generate a brand new cluster id.

This is `maximum cluster id + 1`.

##### Clustering.redo()

Redo the last cluster assignement operation.

*Returns*


* `up` (UpdateInfo instance of the changes done by this operation.)


##### Clustering.reset()

Reset the clustering to the original clustering.

All changes are lost.

##### Clustering.spikes_in_clusters(clusters)

Return the array of spike ids belonging to a list of clusters.

##### Clustering.split(spike_ids)

Split a number of spikes into a new cluster.

This is equivalent to an `assign()` to a single new cluster.

*Parameters*


* `spike_ids` (array-like)

    Array of spike ids to merge.

*Returns*


* `up` (UpdateInfo instance)


*Note*

The note in the `assign()` method applies here as well. The list
of spikes affected by the split is almost always a strict superset
of the spike_ids parameter.

##### Clustering.undo()

Undo the last cluster assignement operation.

*Returns*


* `up` (UpdateInfo instance of the changes done by this operation.)


#### Properties

##### Clustering.cluster_counts

Dictionary with the number of spikes in each cluster.

##### Clustering.cluster_ids

Ordered list of ids of all non-empty clusters.

##### Clustering.n_clusters

Total number of clusters.

##### Clustering.n_spikes

Number of spikes.

##### Clustering.spike_clusters

A n_spikes-long vector containing the cluster ids of all spikes.

##### Clustering.spike_ids

Array of all spike ids.

##### Clustering.spikes_per_cluster

A dictionary `{cluster: spikes}`.

### phy.cluster.manual.CorrelogramViewModel

Correlograms.

#### Methods

##### CorrelogramViewModel.change_bins(bin=None, half_width=None)

Change the parameters of the correlograms.

*Parameters*

* `bin` (float (ms))

    Bin size.

* `half_width` (float (ms))

    Half window size.

##### CorrelogramViewModel.close()

Close the view.

##### CorrelogramViewModel.connect(*args, **kwargs)

Connect a callback function.

##### CorrelogramViewModel.emit(*args, **kwargs)

Emit an event.

##### CorrelogramViewModel.exported_params(save_size_pos=True)

Parameters to save automatically when the view is closed.

##### CorrelogramViewModel.get_params(cls, settings)

Return the parameter values for the creation of the view.

##### CorrelogramViewModel.imported_params(cls)

All parameter names to be imported on object creation.

##### CorrelogramViewModel.on_close()

Clear the view when the model is closed.

##### CorrelogramViewModel.on_cluster(up)

Called when a clustering action occurs.

May be overriden.

##### CorrelogramViewModel.on_key_press(event)

Called when a key is pressed.

##### CorrelogramViewModel.on_open()

Initialize the view after the model has been loaded.

May be overriden.

##### CorrelogramViewModel.on_select(clusters, **kwargs)

Update the view when the selection changes.

##### CorrelogramViewModel.select(cluster_ids, **kwargs)

Select a set of clusters.

##### CorrelogramViewModel.show()

Show the view.

##### CorrelogramViewModel.toggle_normalization()

Change the correlogram normalization.

##### CorrelogramViewModel.update()

Update the view.

##### CorrelogramViewModel.update_spike_clusters(spikes=None, spike_clusters=None)

Update the spike clusters and cluster colors.

#### Properties

##### CorrelogramViewModel.cluster_ids

Selected clusters.

##### CorrelogramViewModel.lines



##### CorrelogramViewModel.model

The model.

##### CorrelogramViewModel.n_clusters

Number of selected clusters.

##### CorrelogramViewModel.n_spikes

Number of selected spikes.

##### CorrelogramViewModel.name

The view model's name.

##### CorrelogramViewModel.normalization

Correlogram normalization: `equal` or `independent`.

##### CorrelogramViewModel.selector

A Selector instance managing the selected spikes and clusters.

##### CorrelogramViewModel.spike_ids

Selected spikes.

##### CorrelogramViewModel.store

The cluster store.

##### CorrelogramViewModel.view

The underlying view.

##### CorrelogramViewModel.wizard

The wizard.

### phy.cluster.manual.FeatureViewModel

Feature view with a single subplot.

#### Methods

##### FeatureViewModel.add_extra_feature(name, array)

Add an extra feature.

*Parameters*


* `name` (str)

    The feature's name.

* `array` (ndarray)

    A `(n_spikes,)` array with the feature's value for every spike.

##### FeatureViewModel.close()

Close the view.

##### FeatureViewModel.connect(*args, **kwargs)

Connect a callback function.

##### FeatureViewModel.dimensions_for_clusters(cluster_ids)

Current dimensions.

##### FeatureViewModel.emit(*args, **kwargs)

Emit an event.

##### FeatureViewModel.exported_params(save_size_pos=True)

Parameters to save automatically when the view is closed.

##### FeatureViewModel.get_params(cls, settings)

Return the parameter values for the creation of the view.

##### FeatureViewModel.imported_params(cls)

All parameter names to be imported on object creation.

##### FeatureViewModel.on_close()

Clear the view when the model is closed.

##### FeatureViewModel.on_cluster(up)

Called when a clustering action occurs.

May be overriden.

##### FeatureViewModel.on_key_press(event)

Handle key press events.

##### FeatureViewModel.on_open()

Initialize the view when the model is opened.

##### FeatureViewModel.on_select(clusters, auto_update=True)

Update the view when the selection changes.

##### FeatureViewModel.select(cluster_ids, **kwargs)

Select a set of clusters.

##### FeatureViewModel.set_dimension(axis, dim, smart=True)

Set a (smart) dimension.

"smart" means that the dimension may be changed if it is the same
than the other dimension, to avoid x=y.

##### FeatureViewModel.show()

Show the view.

##### FeatureViewModel.spikes_in_lasso()

Return the spike ids from the selected clusters within the lasso.

##### FeatureViewModel.update()

Update the view.

##### FeatureViewModel.update_spike_clusters(spikes=None, spike_clusters=None)

Update the spike clusters and cluster colors.

#### Properties

##### FeatureViewModel.cluster_ids

Selected clusters.

##### FeatureViewModel.lasso

The spike lasso visual.

##### FeatureViewModel.marker_size

Marker size, in pixels.

##### FeatureViewModel.model

The model.

##### FeatureViewModel.n_clusters

Number of selected clusters.

##### FeatureViewModel.n_features

Number of features.

##### FeatureViewModel.n_rows

Number of rows.

##### FeatureViewModel.n_spikes

Number of selected spikes.

##### FeatureViewModel.name

The view model's name.

##### FeatureViewModel.selector

A Selector instance managing the selected spikes and clusters.

##### FeatureViewModel.spike_ids

Selected spikes.

##### FeatureViewModel.store

The cluster store.

##### FeatureViewModel.view

The underlying view.

##### FeatureViewModel.wizard

The wizard.

##### FeatureViewModel.x_dim

x dimension.

##### FeatureViewModel.y_dim

y dimension.

### phy.cluster.manual.HTMLClusterViewModel

HTML view model that displays per-cluster information.

#### Methods

##### HTMLClusterViewModel.close()

Close the view.

##### HTMLClusterViewModel.connect(*args, **kwargs)

Connect a callback function.

##### HTMLClusterViewModel.emit(*args, **kwargs)

Emit an event.

##### HTMLClusterViewModel.exported_params(save_size_pos=True)

Return a dictionary of variables to save when the view is closed.

##### HTMLClusterViewModel.get_css(**kwargs)



##### HTMLClusterViewModel.get_html(**kwargs)

Return the non-formatted HTML contents of the view.

##### HTMLClusterViewModel.get_params(cls, settings)

Return the parameter values for the creation of the view.

##### HTMLClusterViewModel.imported_params(cls)

All parameter names to be imported on object creation.

##### HTMLClusterViewModel.isVisible()



##### HTMLClusterViewModel.on_close()

Called when the model is closed.

May be overriden.

##### HTMLClusterViewModel.on_cluster(up)

Update the view after a clustering action.

##### HTMLClusterViewModel.on_open()

Initialize the view after the model has been loaded.

May be overriden.

##### HTMLClusterViewModel.on_select(cluster_ids, **kwargs)

Update the view after a new selection has been made.

##### HTMLClusterViewModel.select(cluster_ids, **kwargs)

Select a list of clusters.

##### HTMLClusterViewModel.show()

Show the view.

##### HTMLClusterViewModel.update(**kwargs)

Update the widget's HTML contents.

#### Properties

##### HTMLClusterViewModel.cluster_ids

Selected clusters.

##### HTMLClusterViewModel.model

The model.

##### HTMLClusterViewModel.n_clusters

Number of selected clusters.

##### HTMLClusterViewModel.name

The view model's name.

##### HTMLClusterViewModel.store

The cluster store.

##### HTMLClusterViewModel.view

The underlying view.

##### HTMLClusterViewModel.wizard

The wizard.

### phy.cluster.manual.StatsViewModel

Display cluster statistics.

#### Methods

##### StatsViewModel.close()

Close the view.

##### StatsViewModel.connect(*args, **kwargs)

Connect a callback function.

##### StatsViewModel.emit(*args, **kwargs)

Emit an event.

##### StatsViewModel.exported_params(save_size_pos=True)

Return a dictionary of variables to save when the view is closed.

##### StatsViewModel.get_css(cluster_ids=None, up=None)



##### StatsViewModel.get_html(cluster_ids=None, up=None)

Return the HTML table with the cluster statistics.

##### StatsViewModel.get_params(cls, settings)

Return the parameter values for the creation of the view.

##### StatsViewModel.imported_params(cls)

All parameter names to be imported on object creation.

##### StatsViewModel.isVisible()



##### StatsViewModel.on_close()

Called when the model is closed.

May be overriden.

##### StatsViewModel.on_cluster(up)

Update the view after a clustering action.

##### StatsViewModel.on_open()

Initialize the view after the model has been loaded.

May be overriden.

##### StatsViewModel.on_select(cluster_ids, **kwargs)

Update the view after a new selection has been made.

##### StatsViewModel.select(cluster_ids, **kwargs)

Select a list of clusters.

##### StatsViewModel.show()

Show the view.

##### StatsViewModel.update(**kwargs)

Update the widget's HTML contents.

#### Properties

##### StatsViewModel.cluster_ids

Selected clusters.

##### StatsViewModel.model

The model.

##### StatsViewModel.n_clusters

Number of selected clusters.

##### StatsViewModel.name

The view model's name.

##### StatsViewModel.store

The cluster store.

##### StatsViewModel.view

The underlying view.

##### StatsViewModel.wizard

The wizard.

### phy.cluster.manual.TraceViewModel

Traces.

#### Methods

##### TraceViewModel.close()

Close the view.

##### TraceViewModel.connect(*args, **kwargs)

Connect a callback function.

##### TraceViewModel.emit(*args, **kwargs)

Emit an event.

##### TraceViewModel.exported_params(save_size_pos=True)

Parameters to save automatically when the view is closed.

##### TraceViewModel.get_params(cls, settings)

Return the parameter values for the creation of the view.

##### TraceViewModel.imported_params(cls)

All parameter names to be imported on object creation.

##### TraceViewModel.move(amount)

Move the current interval by a given amount (in samples).

##### TraceViewModel.move_left(fraction=0.05)

Move the current interval to the left.

##### TraceViewModel.move_right(fraction=0.05)

Move the current interval to the right.

##### TraceViewModel.on_close()

Clear the view when the model is closed.

##### TraceViewModel.on_cluster(up)

Called when a clustering action occurs.

May be overriden.

##### TraceViewModel.on_key_press(event)

Called when a key is pressed.

##### TraceViewModel.on_open()

Initialize the view when the model is opened.

##### TraceViewModel.on_select(clusters, **kwargs)

Update the view when the selection changes.

##### TraceViewModel.select(cluster_ids, **kwargs)

Select a set of clusters.

##### TraceViewModel.show()

Show the view.

##### TraceViewModel.update()

Update the view.

##### TraceViewModel.update_spike_clusters(spikes=None, spike_clusters=None)

Update the spike clusters and cluster colors.

#### Properties

##### TraceViewModel.channel_scale

Vertical scale of the traces.

##### TraceViewModel.cluster_ids

Selected clusters.

##### TraceViewModel.interval

The interval of the view, in unit of sample.

##### TraceViewModel.model

The model.

##### TraceViewModel.n_clusters

Number of selected clusters.

##### TraceViewModel.n_spikes

Number of selected spikes.

##### TraceViewModel.name

The view model's name.

##### TraceViewModel.selector

A Selector instance managing the selected spikes and clusters.

##### TraceViewModel.spike_ids

Selected spikes.

##### TraceViewModel.store

The cluster store.

##### TraceViewModel.view

The underlying view.

##### TraceViewModel.wizard

The wizard.

### phy.cluster.manual.WaveformViewModel

Waveforms.

#### Methods

##### WaveformViewModel.close()

Close the view.

##### WaveformViewModel.connect(*args, **kwargs)

Connect a callback function.

##### WaveformViewModel.emit(*args, **kwargs)

Emit an event.

##### WaveformViewModel.exported_params(save_size_pos=True)

Parameters to save automatically when the view is closed.

##### WaveformViewModel.get_params(cls, settings)

Return the parameter values for the creation of the view.

##### WaveformViewModel.imported_params(cls)

All parameter names to be imported on object creation.

##### WaveformViewModel.on_close()

Clear the view when the model is closed.

##### WaveformViewModel.on_cluster(up)

Called when a clustering action occurs.

May be overriden.

##### WaveformViewModel.on_key_press(event)

Called when a key is pressed.

##### WaveformViewModel.on_open()

Initialize the view when the model is opened.

##### WaveformViewModel.on_select(clusters, **kwargs)

Update the view when the selection changes.

##### WaveformViewModel.select(cluster_ids, **kwargs)

Select a set of clusters.

##### WaveformViewModel.show()

Show the view.

##### WaveformViewModel.update()

Update the view.

##### WaveformViewModel.update_spike_clusters(spikes=None)

Update the view's spike clusters.

#### Properties

##### WaveformViewModel.box_scale

Scale of the waveforms.

This is a pair of scalars.

##### WaveformViewModel.cluster_ids

Selected clusters.

##### WaveformViewModel.model

The model.

##### WaveformViewModel.n_clusters

Number of selected clusters.

##### WaveformViewModel.n_spikes

Number of selected spikes.

##### WaveformViewModel.name

The view model's name.

##### WaveformViewModel.overlap

Whether to overlap waveforms.

##### WaveformViewModel.probe_scale

Scale of the probe.

This is a pair of scalars.

##### WaveformViewModel.selector

A Selector instance managing the selected spikes and clusters.

##### WaveformViewModel.show_mean

Whether to show mean waveforms.

##### WaveformViewModel.spike_ids

Selected spikes.

##### WaveformViewModel.store

The cluster store.

##### WaveformViewModel.view

The underlying view.

##### WaveformViewModel.wizard

The wizard.

### phy.cluster.manual.Wizard

Propose a selection of high-quality clusters and merge candidates.

#### Methods

##### Wizard.best_clusters(n_max=None, quality=None)

Return the list of best clusters sorted by decreasing quality.

The default quality function is the registered one.

##### Wizard.first()

First match or first best.

##### Wizard.get_panel_params()

Return the parameters for the HTML panel.

##### Wizard.last()

Last match or last best.

##### Wizard.most_similar_clusters(cluster=None, n_max=None, similarity=None)

Return the `n_max` most similar clusters to a given cluster.

The default similarity function is the registered one.

##### Wizard.next()

Next cluster proposition.

##### Wizard.next_best()

Select the next best cluster.

##### Wizard.next_match()

Select the next match.

##### Wizard.on_cluster(up)



##### Wizard.pin(cluster=None)

Pin the current best cluster and set the list of closest matches.

##### Wizard.previous()

Previous cluster proposition.

##### Wizard.previous_best()

Select the previous best in cluster.

##### Wizard.previous_match()

Select the previous match.

##### Wizard.reset()



##### Wizard.set_quality_function(func)

Register a function returning the quality of a cluster.

Can be used as a decorator.

##### Wizard.set_similarity_function(func)

Register a function returning the similarity between two clusters.

Can be used as a decorator.

##### Wizard.start()

Start the wizard by setting the list of best clusters.

##### Wizard.unpin()

Unpin the current cluster.

#### Properties

##### Wizard.best

Currently-selected best cluster.

##### Wizard.best_list

Current list of best clusters, by decreasing quality.

##### Wizard.cluster_groups

Dictionary with the groups of each cluster.

The groups are: `None` (corresponds to unsorted), `good`, or `ignored`.

##### Wizard.cluster_ids

Array of cluster ids in the current clustering.

##### Wizard.has_started



##### Wizard.match

Currently-selected closest match.

##### Wizard.match_list

Current list of closest matches, by decreasing similarity.

##### Wizard.n_clusters

Total number of clusters.

##### Wizard.n_processed

Numbered of processed clusters so far.

A cluster is considered processed if its group is not `None`.

##### Wizard.selection

Return the current best/match cluster selection.

## phy.electrode

Electrodes.

##### phy.electrode.load_probe(name)

Load one of the built-in probes.

### phy.electrode.MEA

A Multi-Electrode Array.

There are two modes:

* No probe specified: one single channel group, positions and adjacency
  list specified directly.
* Probe specified: one can change the current channel_group.

#### Methods

##### MEA.change_channel_group(group)

Change the current channel group.

#### Properties

##### MEA.adjacency

Adjacency graph in the current channel group.

##### MEA.channels

Channel ids in the current channel group.

##### MEA.n_channels

Number of channels in the current channel group.

##### MEA.positions

Channel positions in the current channel group.

## phy.gui

GUI routines.

##### phy.gui.enable_qt()



##### phy.gui.qt_app(*args, **kwds)

Context manager to ensure that a Qt app is running.

##### phy.gui.run_qt_app()

Start the Qt application's event loop.

##### phy.gui.start_qt_app()

Start a Qt application if necessary.

If a new Qt application is created, this function returns it.
If no new application is created, the function returns None.

### phy.gui.BaseGUI

Base GUI.

This object represents a main window with:

* multiple dockable views
* user-exposed actions
* keyboard shortcuts

*Parameters*


* `config` (list)

    List of pairs `(name, kwargs)` to create default views.

* `vm_classes` (dict)

    Dictionary `{name: view_model_class}`.

* `state` (object)

    Default Qt GUI state.

* `shortcuts` (dict)

    Dictionary `{function_name: keyboard_shortcut}`.

*Events*

add_view
close_view
reset_gui

#### Methods

##### BaseGUI.add_view(item, title=None, **kwargs)

Add a new view instance to the GUI.

##### BaseGUI.close()

Close the GUI.

##### BaseGUI.connect(func=None, event=None, set_method=False)

Register a callback function to a given event.

To register a callback function to the `spam` event, where `obj` is
an instance of a class deriving from `EventEmitter`:

```python
@obj.connect
def on_spam(arg1, arg2):
    pass
```

This is called when `obj.emit('spam', arg1, arg2)` is called.

Several callback functions can be registered for a given event.

The registration order is conserved and may matter in applications.

##### BaseGUI.connect_views(name_0, name_1)

Decorator for a function called on every pair of views of a
given type.

##### BaseGUI.disable_snippet_mode()



##### BaseGUI.emit(event, *args, **kwargs)

Call all callback functions registered with an event.

Any positional and keyword arguments can be passed here, and they will
be fowarded to the callback functions.

Return the list of callback return results.

##### BaseGUI.enable_snippet_mode()



##### BaseGUI.exit()

Close the GUI.

##### BaseGUI.get_views(*names)

Return the list of views of a given type.

##### BaseGUI.isVisible()



##### BaseGUI.on_open()

Callback function when the model is opened.

Must be overriden.

##### BaseGUI.process_snippet(snippet)

Processes a snippet.

May be overriden.

##### BaseGUI.reset()

Remove all registered callbacks.

##### BaseGUI.reset_gui()

Reset the GUI configuration.

##### BaseGUI.show()

Show the GUI

##### BaseGUI.show_shortcuts()

Show the list of all keyboard shortcuts.

##### BaseGUI.unconnect(*funcs)

Unconnect specified callback functions.

##### BaseGUI.view_count()

Number of views of each type.

#### Properties

##### BaseGUI.main_window

Main Qt window.

##### BaseGUI.status_message

Message in the status bar.

##### BaseGUI.title

Title of the main window.

May be overriden.

##### BaseGUI.views

List of all open views.

### phy.gui.BaseViewModel

Interface between a view and a model.

*Events*

show_view
close_view

#### Methods

##### BaseViewModel.close()

Close the view.

##### BaseViewModel.connect(*args, **kwargs)

Connect a callback function.

##### BaseViewModel.emit(*args, **kwargs)

Emit an event.

##### BaseViewModel.exported_params(save_size_pos=True)

Return a dictionary of variables to save when the view is closed.

##### BaseViewModel.get_params(cls, settings)

Return the parameter values for the creation of the view.

##### BaseViewModel.imported_params(cls)

All parameter names to be imported on object creation.

##### BaseViewModel.on_close()

Called when the model is closed.

May be overriden.

##### BaseViewModel.on_open()

Initialize the view after the model has been loaded.

May be overriden.

##### BaseViewModel.show()

Show the view.

#### Properties

##### BaseViewModel.model

The model.

##### BaseViewModel.name

The view model's name.

##### BaseViewModel.view

The underlying view.

### phy.gui.DockWindow

A Qt main window holding docking Qt or VisPy widgets.

*Events*

close_gui
show_gui
keystroke

*Note*

Use `connect_()`, not `connect()`, because of a name conflict with Qt.

#### Methods

##### DockWindow.add_action(name, callback=None, shortcut=None, checkable=False, checked=False)

Add an action with a keyboard shortcut.

##### DockWindow.add_view(view, title='view', position=None, closable=True, floatable=True, floating=None, **kwargs)

Add a widget to the main window.

##### DockWindow.closeEvent(e)

Qt slot when the window is closed.

##### DockWindow.connect_(*args, **kwargs)



##### DockWindow.emit(*args, **kwargs)



##### DockWindow.keyReleaseEvent(e)



##### DockWindow.list_views(title='', is_visible=True)

List all views which title start with a given string.

##### DockWindow.remove_action(name)

Remove an action.

##### DockWindow.remove_actions()

Remove all actions.

##### DockWindow.restore_geometry_state(gs)

Restore the position of the main window and the docks.

The dock widgets need to be recreated first.

This function can be called in `on_show()`.

##### DockWindow.save_geometry_state()

Return picklable geometry and state of the window and docks.

This function can be called in `on_close()`.

##### DockWindow.shortcut(name, key=None)

Decorator to add a global keyboard shortcut.

##### DockWindow.show()

Show the window.

##### DockWindow.unconnect_(*args, **kwargs)



##### DockWindow.view_count(is_visible=True)

Return the number of opened views.

#### Properties

##### DockWindow.status_message

The message in the status bar.

### phy.gui.HTMLViewModel

Widget with custom HTML code.

To create a new HTML view, derive from `HTMLViewModel`, and implement
`get_html()` which returns HTML code.

#### Methods

##### HTMLViewModel.close()

Close the view.

##### HTMLViewModel.connect(*args, **kwargs)

Connect a callback function.

##### HTMLViewModel.emit(*args, **kwargs)

Emit an event.

##### HTMLViewModel.exported_params(save_size_pos=True)

Return a dictionary of variables to save when the view is closed.

##### HTMLViewModel.get_css(**kwargs)

Return the view's CSS styles.

##### HTMLViewModel.get_html(**kwargs)

Return the non-formatted HTML contents of the view.

##### HTMLViewModel.get_params(cls, settings)

Return the parameter values for the creation of the view.

##### HTMLViewModel.imported_params(cls)

All parameter names to be imported on object creation.

##### HTMLViewModel.isVisible()



##### HTMLViewModel.on_close()

Called when the model is closed.

May be overriden.

##### HTMLViewModel.on_open()

Initialize the view after the model has been loaded.

May be overriden.

##### HTMLViewModel.show()

Show the view.

##### HTMLViewModel.update(**kwargs)

Update the widget's HTML contents.

#### Properties

##### HTMLViewModel.model

The model.

##### HTMLViewModel.name

The view model's name.

##### HTMLViewModel.view

The underlying view.

### phy.gui.WidgetCreator

Manage the creation of widgets.

A widget must implement:

* `name`
* `show()`
* `connect` (for `close` event)

*Events*

add(widget): when a widget is added.
close(widget): when a widget is closed.

#### Methods

##### WidgetCreator.add(widget_class, show=False, **kwargs)

Add a new widget.

##### WidgetCreator.connect(func=None, event=None, set_method=False)

Register a callback function to a given event.

To register a callback function to the `spam` event, where `obj` is
an instance of a class deriving from `EventEmitter`:

```python
@obj.connect
def on_spam(arg1, arg2):
    pass
```

This is called when `obj.emit('spam', arg1, arg2)` is called.

Several callback functions can be registered for a given event.

The registration order is conserved and may matter in applications.

##### WidgetCreator.emit(event, *args, **kwargs)

Call all callback functions registered with an event.

Any positional and keyword arguments can be passed here, and they will
be fowarded to the callback functions.

Return the list of callback return results.

##### WidgetCreator.get(*names)

Return the list of widgets of a given type.

##### WidgetCreator.remove(widget)

Remove a widget.

##### WidgetCreator.reset()

Remove all registered callbacks.

##### WidgetCreator.unconnect(*funcs)

Unconnect specified callback functions.

#### Properties

##### WidgetCreator.widget_classes

The registered widget classes that can be created.

## phy.io

Input/output.

##### phy.io.create_kwik(prm_file=None, kwik_path=None, overwrite=False, probe=None, **kwargs)

Create a new Kwik dataset from a PRM file.

##### phy.io.open_h5(filename, mode=None)

Open an HDF5 file and return a File instance.

##### phy.io.read_dat(filename, dtype=None, shape=None, offset=0, n_channels=None)

Read traces from a flat binary `.dat` file.

The output is a memory-mapped file.

*Parameters*


* `filename` (str)

    The path to the `.dat` file.

* `dtype` (dtype)

    The NumPy dtype.

* `offset` (0)

    The header size.

* `n_channels` (int)

    The number of channels in the data.

* `shape` (tuple (optional))

    The array shape. Typically `(n_samples, n_channels)`. The shape is
    automatically computed from the file size if the number of channels
    and dtype are specified.

##### phy.io.read_kwd(kwd_handle)

Read all traces in a  `.kwd` file.

The output is a memory-mapped file.

### phy.io.BaseModel

This class holds data from an experiment.

This base class must be derived.

#### Methods

##### BaseModel.close()

Close the model and the underlying files.

May be implemented by child classes.

##### BaseModel.save()

Save the data.

May be implemented by child classes.

##### BaseModel.spike_train(cluster_id)

Return the spike times of a given cluster.

##### BaseModel.update_spikes_per_cluster(spc)



#### Properties

##### BaseModel.channel_group



##### BaseModel.channel_groups

List of channel groups.

May be implemented by child classes.

##### BaseModel.cluster_groups

Groups of all clusters in the current channel group and clustering.

This is a regular Python dictionary.

##### BaseModel.cluster_metadata

ClusterMetadata instance holding information about the clusters.

Must be implemented by child classes.

##### BaseModel.clustering



##### BaseModel.clusterings

List of clusterings.

May be implemented by child classes.

##### BaseModel.features

Features from the current channel_group (may be memory-mapped).

May be implemented by child classes.

##### BaseModel.masks

Masks from the current channel_group (may be memory-mapped).

May be implemented by child classes.

##### BaseModel.metadata

A dictionary holding metadata about the experiment.

May be implemented by child classes.

##### BaseModel.path



##### BaseModel.probe

A Probe instance.

May be implemented by child classes.

##### BaseModel.sample_rate



##### BaseModel.spike_clusters

Spike clusters from the current channel_group.

Must be implemented by child classes.

##### BaseModel.spike_samples

Spike times from the current channel_group.

Must be implemented by child classes.

##### BaseModel.spike_times

Spike times from the current channel_group.

This is a NumPy array containing `float64` values (in seconds).

The spike times of all recordings are concatenated. There is no gap
between consecutive recordings, currently.

##### BaseModel.spikes_per_cluster

Spikes per cluster dictionary.

Must be implemented by child classes.

##### BaseModel.traces

Traces (may be memory-mapped).

May be implemented by child classes.

##### BaseModel.waveforms

Waveforms from the current channel_group (may be memory-mapped).

May be implemented by child classes.

### phy.io.BaseSession

Give access to the data, views, and GUIs in an interactive session.

The model must implement:

* `model(path)`
* `model.path`
* `model.close()`

*Events*

open
close

#### Methods

##### BaseSession.close()

Close the currently-open dataset.

##### BaseSession.connect(func=None, event=None, set_method=False)

Register a callback function to a given event.

To register a callback function to the `spam` event, where `obj` is
an instance of a class deriving from `EventEmitter`:

```python
@obj.connect
def on_spam(arg1, arg2):
    pass
```

This is called when `obj.emit('spam', arg1, arg2)` is called.

Several callback functions can be registered for a given event.

The registration order is conserved and may matter in applications.

##### BaseSession.emit(event, *args, **kwargs)

Call all callback functions registered with an event.

Any positional and keyword arguments can be passed here, and they will
be fowarded to the callback functions.

Return the list of callback return results.

##### BaseSession.on_close()



##### BaseSession.on_open()



##### BaseSession.open(path=None, model=None)

Open a dataset.

##### BaseSession.reopen()



##### BaseSession.reset()

Remove all registered callbacks.

##### BaseSession.save()



##### BaseSession.save_view_params(vm, save_size_pos=True)

Save the parameters exported by a view model instance.

##### BaseSession.show_gui(name=None, show=True, **kwargs)

Show a new GUI.

##### BaseSession.unconnect(*funcs)

Unconnect specified callback functions.

#### Properties

### phy.io.ClusterStore

Hold per-cluster information on disk and in memory.

*Note*

Currently, this is used to accelerate access to per-cluster data
and statistics. All data is dynamically updated when clustering
changes occur.

#### Methods

##### ClusterStore.clean()

Erase all old files in the store.

##### ClusterStore.clear()

Erase all files in the store.

##### ClusterStore.display_status()

Display the current status of the cluster store.

##### ClusterStore.generate(mode=None)

Generate the cluster store.

*Parameters*


* `mode` (str (default is None))

    How the cluster store should be generated. Options are:

    * None or `default`: only regenerate the missing or inconsistent
      clusters
    * `force`: fully regenerate the cluster
    * `read-only`: just load the existing files, do not write anything

##### ClusterStore.is_consistent()

Return whether the cluster store is probably consistent.

Return true if all cluster stores files exist and have the expected
file size.

##### ClusterStore.load(name, clusters=None, spikes=None)

Load some data for a number of clusters and spikes.

##### ClusterStore.register_field(name, item_name=None)

Register a new piece of data to store on memory or on disk.

*Parameters*


* `name` (str)

    The name of the field.

* `item_name` (str)

    The name of the item.

##### ClusterStore.register_item(item_cls, **kwargs)

Register a `StoreItem` class in the store.

A `StoreItem` class is responsible for storing some data to disk
and memory. It must register one or several pieces of data.

##### ClusterStore.update_spikes_per_cluster(spikes_per_cluster)



#### Properties

##### ClusterStore.cluster_ids

All cluster ids appearing in the `spikes_per_cluster` dictionary.

##### ClusterStore.disk_store

Manage the cache of per-cluster voluminous data.

##### ClusterStore.files

List of files present in the disk store.

##### ClusterStore.items

Dictionary of registered store items.

##### ClusterStore.memory_store

Hold some cluster statistics.

##### ClusterStore.model

Model.

##### ClusterStore.old_clusters

Clusters in the disk store that are no longer in the clustering.

##### ClusterStore.path

Path to the disk store cache.

##### ClusterStore.spikes_per_cluster

Dictionary `{cluster_id: spike_ids}`.

##### ClusterStore.status

Return the current status of the cluster store.

##### ClusterStore.total_size

Total size of the disk store.

### phy.io.File



#### Methods

##### File.attrs(path='/')

Return the list of attributes at the given path.

##### File.children(path='/')

Return the list of children of a given node.

##### File.close()



##### File.copy(path, new_path)

Copy a group or dataset to another location.

##### File.datasets(path='/')

Return the list of datasets under a given node.

##### File.delete(path)

Delete a group or dataset.

##### File.describe()

Display the list of all groups and datasets in the file.

##### File.exists(path)



##### File.groups(path='/')

Return the list of groups under a given node.

##### File.has_attr(path, attr_name)

Return whether an attribute exists at a given path.

##### File.is_open()



##### File.move(path, new_path)

Move a group or dataset to another location.

##### File.open(mode=None)



##### File.read(path)

Read an HDF5 dataset, given its HDF5 path in the file.

##### File.read_attr(path, attr_name)

Read an attribute of an HDF5 group.

##### File.write(path, array=None, dtype=None, shape=None, overwrite=False)

Write a NumPy array in the file.

*Parameters*

* `path` (str)

    Full HDF5 path to the dataset to create.

* `array` (ndarray)

    Array to write in the file.

* `dtype` (dtype)

    If `array` is None, the dtype of the array.

* `shape` (tuple)

    If `array` is None, the shape of the array.

* `overwrite` (bool)

    If False, raise an error if the dataset already exists. Defaults
    to False.

##### File.write_attr(path, attr_name, value)

Write an attribute of an HDF5 group.

#### Properties

##### File.h5py_file

Native h5py file handle.

### phy.io.KwikCreator

Create and modify a `.kwik` file.

#### Methods

##### KwikCreator.add_cluster_group(group=None, id=None, name=None, clustering=None)

Add a cluster group.

*Parameters*


* `group` (int)

    The channel group.

* `id` (int)

    The cluster group id.

* `name` (str)

    The cluster group name.

* `clustering` (str)

    The name of the clustering.

##### KwikCreator.add_clustering(group=None, name=None, spike_clusters=None, cluster_groups=None)

Add a clustering.

*Parameters*


* `group` (int)

    The channel group.

* `name` (str)

    The clustering name.

* `spike_clusters` (ndarray)

    The spike clusters assignements. This is `(n_spikes,)` array.

* `cluster_groups` (dict)

    The cluster group of every cluster.

##### KwikCreator.add_recording(id=None, raw_path=None, start_sample=None, sample_rate=None)

Add a recording.

*Parameters*


* `id` (int)

    The recording id (0, 1, 2, etc.).

* `raw_path` (str)

    Path to the file containing the raw data.

* `start_sample` (int)

    The offset of the recording, in number of samples.

* `sample_rate` (float)

    The sample rate of the recording

##### KwikCreator.add_spikes(group=None, spike_samples=None, spike_recordings=None, masks=None, features=None, n_channels=None, n_features=None)

Add spikes in the file.

*Parameters*


* `group` (int)

    Channel group.

* `spike_samples` (ndarray)

    The spike times in number of samples.

* `spike_recordings` (ndarray (optional))

    The recording indices of every spike.

* `masks` (ndarray or list of ndarrays)

    The masks.

* `features` (ndarray or list of ndarrays)

    The features.

*Note*

The features and masks can be passed as lists or generators of
(memmapped) data chunks in order to avoid loading the entire arrays
in RAM.

##### KwikCreator.create_empty()

Create empty `.kwik` and `.kwx` files.

##### KwikCreator.set_metadata(path, **kwargs)

Set metadata fields in a HDF5 path.

##### KwikCreator.set_probe(probe)

Save a probe dictionary in the file.

#### Properties

### phy.io.KwikModel

Holds data contained in a kwik file.

#### Methods

##### KwikModel.add_cluster_group(group_id, name)

Add a new cluster group.

##### KwikModel.add_clustering(name, spike_clusters)

Save a new clustering to the file.

##### KwikModel.close()

Close the `.kwik` and `.kwx` files if they are open, and cleanup
handles to all raw data files

##### KwikModel.copy_clustering(name, new_name)

Copy a clustering in the `.kwik` file.

##### KwikModel.delete_cluster_group(group_id)



##### KwikModel.delete_clustering(name)

Delete a clustering.

##### KwikModel.describe()

Display information about the dataset.

##### KwikModel.has_kwx()

Returns whether the `.kwx` file is present.

If not, the features and masks won't be available.

##### KwikModel.open(kwik_path, channel_group=None, clustering=None)

Open a Kwik dataset.

The `.kwik` and `.kwx` must be in the same folder with the
same basename.

The files containing the traces (`.raw.kwd` or `.dat` / `.bin`) are
determined according to the following logic:

- Is there a path specified to a file which exists in
[KWIK]/recordings/[X]/raw? If so, open it.
- If this file does not exist, does a file exist with the same name
in the current directory? If so, open it.
- If such a file does not exist, or no filename is specified in
the [KWIK], then is there a `raw.kwd` with the experiment basename
in the current directory? If so, open it.
- If not, return with a warning.

*Notes*

The `.kwik` file is opened in read-only mode, and is automatically
closed when this function returns. It is temporarily reopened when
the channel group or clustering changes.

The `.kwik` file is temporarily opened in append mode when saving.

The `.kwx` and `.raw.kwd` or `.dat` / `.bin` files stay open in
read-only mode as long as `model.close()` is not called. This is
because there might be read accesses to `features_masks` (`.kwx`)
and waveforms (`.raw.kwd` or `.dat` / `.bin`) while the dataset is
opened.

*Parameters*


* `kwik_path` (str)

    Path to a `.kwik` file.

* `channel_group` (int or None (default is None))

    The channel group (shank) index to use. This can be changed
    later after the file has been opened. By default, the first
    channel group is used.

* `clustering` (str or None (default is None))

    The clustering to use. This can be changed later after the file
    has been opened. By default, the `main` clustering is used. An
    error is raised if the `main` clustering doesn't exist.

##### KwikModel.rename_cluster_group(group_id, name)

Rename an existing cluster group.

##### KwikModel.rename_clustering(old_name, new_name)

Rename a clustering in the `.kwik` file.

##### KwikModel.save(spike_clusters, cluster_groups, clustering_metadata=None)

Save the spike clusters and cluster groups in the Kwik file.

##### KwikModel.spike_train(cluster_id)

Return the spike times of a given cluster.

##### KwikModel.update_spikes_per_cluster(spc)



#### Properties

##### KwikModel.channel_group



##### KwikModel.channel_groups

List of channel groups found in the Kwik file.

##### KwikModel.channel_order

List of kept channels in the current channel group.

If you want the channels used in the features, masks, and waveforms,
this is the property you want to use, and not `model.channels`.

The channel order is the same than the one from the PRB file.
This order was used when generating the features and masks
in SpikeDetekt2. The same order is used in phy when loading the
waveforms from the traces file(s).

##### KwikModel.channels

List of all channels in the current channel group.

This list comes from the /channel_groups HDF5 group in the Kwik file.

##### KwikModel.cluster_groups

Groups of all clusters in the current channel group and clustering.

This is a regular Python dictionary.

##### KwikModel.cluster_ids

List of cluster ids from the current channel group and clustering.

This is a sorted list of unique cluster ids as found in the current
`spike_clusters` array.

##### KwikModel.cluster_metadata

Metadata about the clusters in the current channel group and
clustering.

`cluster_metadata.group(cluster_id)` returns the group of a given
cluster. The default group is 3 (unsorted).

##### KwikModel.clustering

The currently-active clustering.

Default is `main`.

##### KwikModel.clustering_metadata

A dictionary of key-value metadata specific to the current
clustering.

##### KwikModel.clusterings

List of clusterings found in the Kwik file.

The first one is always `main`.

##### KwikModel.duration

Duration of the experiment (in seconds).

##### KwikModel.features

Features from the current channel group.

This is memory-mapped to the `.kwx` file.

Note: in general, it is better to use the cluster store to access
the features and masks of some clusters.

##### KwikModel.features_masks

Features-masks from the current channel group.

This is memory-mapped to the `.kwx` file.

Note: in general, it is better to use the cluster store to access
the features and masks of some clusters.

##### KwikModel.masks

Masks from the current channel group.

This is memory-mapped to the `.kwx` file.

Note: in general, it is better to use the cluster store to access
the features and masks of some clusters.

##### KwikModel.metadata

A dictionary holding metadata about the experiment.

This information comes from the PRM file. It was used by
SpikeDetekt2 and KlustaKwik during automatic clustering.

##### KwikModel.n_channels

Number of all channels in the current channel group.

##### KwikModel.n_clusters

Number of clusters in the current channel group and clustering.

##### KwikModel.n_features_per_channel

Number of features per channel (generally 3).

##### KwikModel.n_recordings

Number of recordings found in the Kwik file.

##### KwikModel.n_samples_waveforms



##### KwikModel.n_spikes

Number of spikes in the current channel group.

##### KwikModel.path



##### KwikModel.probe

A `Probe` instance representing the probe used for the recording.

This object contains information about the adjacency graph and
the channel positions.

##### KwikModel.recordings

List of recording indices found in the Kwik file.

##### KwikModel.sample_rate

Sample rate of the recording.

This value is found in the metadata coming from the PRM file.

##### KwikModel.spike_clusters

Spike clusters from the current channel group and clustering.

Every element is the cluster identifier of a spike.

The shape is `(n_spikes,)`.

##### KwikModel.spike_ids

List of spike ids.

##### KwikModel.spike_recordings

The recording index for each spike.

This is a NumPy array of integers with `n_spikes` elements.

##### KwikModel.spike_samples

Spike samples from the current channel group.

This is a NumPy array containing `uint64` values (number of samples
in unit of the sample rate).

The spike times of all recordings are concatenated. There is no gap
between consecutive recordings, currently.

##### KwikModel.spike_times

Spike times from the current channel_group.

This is a NumPy array containing `float64` values (in seconds).

The spike times of all recordings are concatenated. There is no gap
between consecutive recordings, currently.

##### KwikModel.spikes_per_cluster

Spikes per cluster from the current channel group and clustering.

##### KwikModel.traces

Raw traces as found in the traces file(s).

This object is memory-mapped to the HDF5 file, or `.dat` / `.bin` file,
or both.

##### KwikModel.waveforms

High-passed filtered waveforms from the current channel group.

This is a virtual array mapped to the traces file(s). Filtering is
done on the fly.

The shape is `(n_spikes, n_samples, n_channels)`.

### phy.io.StoreItem

A class describing information stored in the cluster store.

*Parameters*


* `name` (str)

    Name of the item.

* `fields` (list)

    A list of field names.

* `model` (Model)

    A `Model` instance for the current dataset.

* `memory_store` (MemoryStore)

    The `MemoryStore` instance for the current dataset.

* `disk_store` (DiskStore)

    The DiskStore instance for the current dataset.

#### Methods

##### StoreItem.empty_values(name)

Return a null array of the right shape for a given field.

##### StoreItem.is_consistent(cluster, spikes)

Return whether the stored item is consistent.

To be overriden.

##### StoreItem.load(cluster, name)

Load data for one cluster.

##### StoreItem.load_multi(clusters, name)

Load data for several clusters.

##### StoreItem.load_spikes(spikes, name)

Load data from an array of spikes.

##### StoreItem.on_assign(up)

Called when a new split occurs.

May be overriden.

##### StoreItem.on_cluster(up=None)

Called when the clusters change.

Old data is kept on disk and in memory, which is useful for
undo and redo. The `cluster_store.clean()` method can be called to
delete the old files.

Nothing happens during undo and redo (the data is already there).

##### StoreItem.on_merge(up)

Called when a new merge occurs.

May be overriden if there's an efficient way to update the data
after a merge.

##### StoreItem.spikes_in_clusters(clusters)

Return the spikes belonging to clusters.

##### StoreItem.store(cluster)

Store data for a cluster from the model to the store.

May be overridden.

##### StoreItem.store_all(mode=None, **kwargs)

Copy all data for that item from the model to the cluster store.

##### StoreItem.to_generate(mode=None)

Return the list of clusters that need to be regenerated.

#### Properties

##### StoreItem.cluster_ids

Array of cluster ids.

##### StoreItem.progress_reporter

Progress reporter instance.

##### StoreItem.spikes_per_cluster

Spikes per cluster.

## phy.plot

Interactive and static visualization of data.

##### phy.plot.plot_correlograms(*args, **kwargs)

Plot an array of correlograms.

*Parameters*


* `correlograms` (array)

    A `(n_clusters, n_clusters, n_bins)` array.

* `lines` ( ndarray)

    Array of x coordinates where to put vertical lines (in number of
    samples).

* `colors` (array-like (optional))

    A list of colors as RGB tuples.

##### phy.plot.plot_features(*args, **kwargs)

Plot features.

*Parameters*


* `features` (ndarray)

    The features to plot. A `(n_spikes, n_channels, n_features)` array.

* `spike_clusters` (ndarray (optional))

    A `(n_spikes,)` int array with the spike clusters.

* `masks` (ndarray (optional))

    A `(n_spikes, n_channels)` float array with the spike masks.

* `n_rows` (int)

    Number of rows (= number of columns) in the grid view.

* `x_dimensions` (list)

    List of dimensions for the x axis.

* `y_dimensions` (list)

    List of dimensions for the yœ axis.

* `extra_features` (dict)

    A dictionary `{feature_name: array}` where `array` has
    `n_spikes` elements.

* `background_features` (ndarray)

    The background features. A `(n_spikes, n_channels, n_features)` array.

##### phy.plot.plot_traces(*args, **kwargs)

Plot traces.

*Parameters*


* `traces` (ndarray)

    The traces to plot. A `(n_samples, n_channels)` array.

* `spike_samples` (ndarray (optional))

    A `(n_spikes,)` int array with the spike times in number of samples.

* `spike_clusters` (ndarray (optional))

    A `(n_spikes,)` int array with the spike clusters.

* `masks` (ndarray (optional))

    A `(n_spikes, n_channels)` float array with the spike masks.

* `n_samples_per_spike` (int)

    Waveform size in number of samples.

##### phy.plot.plot_waveforms(*args, **kwargs)

Plot waveforms.

*Parameters*


* `waveforms` (ndarray)

    The waveforms to plot. A `(n_spikes, n_samples, n_channels)` array.

* `spike_clusters` (ndarray (optional))

    A `(n_spikes,)` int array with the spike clusters.

* `masks` (ndarray (optional))

    A `(n_spikes, n_channels)` float array with the spike masks.

* `channel_positions` (ndarray)

    A `(n_channels, 2)` array with the channel positions.

### phy.plot.BaseSpikeCanvas

Base class for a VisPy canvas with spike data.

Display a main `BaseSpikeVisual` with pan zoom.

#### Methods

##### BaseSpikeCanvas.emit(name, **kwargs)



##### BaseSpikeCanvas.on_draw(event)

Draw the main visual.

##### BaseSpikeCanvas.on_resize(event)

Resize the OpenGL context.

#### Properties

### phy.plot.BaseSpikeVisual

Base class for a VisPy visual showing spike data.

There is a notion of displayed spikes and displayed clusters.

#### Methods

##### BaseSpikeVisual.draw()

Draw the waveforms.

##### BaseSpikeVisual.set_to_bake(*bakes)

Mark data items to be prepared for GPU.

##### BaseSpikeVisual.update()



#### Properties

##### BaseSpikeVisual.cluster_colors

Colors of the displayed clusters.

The first color is the color of the smallest cluster.

##### BaseSpikeVisual.cluster_ids

Cluster ids of the displayed spikes.

##### BaseSpikeVisual.cluster_order

List of selected clusters in display order.

##### BaseSpikeVisual.empty

Specify whether the visual is currently empty or not.

##### BaseSpikeVisual.masks

Masks of the displayed spikes.

##### BaseSpikeVisual.n_clusters

Number of displayed clusters.

##### BaseSpikeVisual.spike_clusters

The clusters assigned to the displayed spikes.

##### BaseSpikeVisual.spike_ids

Spike ids to display.

### phy.plot.CorrelogramView

A VisPy canvas displaying correlograms.

#### Methods

##### CorrelogramView.emit(name, **kwargs)



##### CorrelogramView.on_draw(event)

Draw the correlograms visual.

##### CorrelogramView.on_resize(event)

Resize the OpenGL context.

##### CorrelogramView.set_data(correlograms=None, colors=None, lines=None)



#### Properties

##### CorrelogramView.cluster_ids

Displayed cluster ids.

##### CorrelogramView.correlograms



##### CorrelogramView.lines

List of x coordinates where to put vertical lines.

This is unit of samples.

##### CorrelogramView.lines_color



### phy.plot.FeatureView

A VisPy canvas displaying features.

#### Methods

##### FeatureView.add_extra_feature(name, array, array_min, array_max, array_bg=None)



##### FeatureView.emit(name, **kwargs)



##### FeatureView.init_grid(n_rows)

Initialize the view with a given number of rows.

*Note*

This function *must* be called before setting the attributes.

##### FeatureView.on_draw(event)

Draw the features in a grid view.

##### FeatureView.on_key_press(event)

Handle key press events.

##### FeatureView.on_mouse_press(e)



##### FeatureView.on_resize(event)

Resize the OpenGL context.

##### FeatureView.set_data(features=None, n_rows=1, x_dimensions=None, y_dimensions=None, masks=None, spike_clusters=None, extra_features=None, background_features=None, colors=None)



##### FeatureView.set_dimensions(axis, dimensions)



##### FeatureView.smart_dimension(axis, box, dim)

Smartify a dimension selection by ensuring x != y.

#### Properties

##### FeatureView.marker_size

Marker size.

##### FeatureView.x_dim



##### FeatureView.y_dim



### phy.plot.FeatureVisual

Display a grid of multidimensional features.

#### Methods

##### FeatureVisual.add_extra_feature(name, array, array_min, array_max)



##### FeatureVisual.draw()

Draw the waveforms.

##### FeatureVisual.project(box, features=None, extra_features=None)

Project data to a subplot's two-dimensional subspace.

*Parameters*

* `box` (2-tuple)

    The `(row, col)` of the box.

* `features` (array)


* `extra_features` (dict)


*Notes*

The coordinate system is always the world coordinate system, i.e.
`[-1, 1]`.

##### FeatureVisual.set_dimension(axis, box, dim)



##### FeatureVisual.set_to_bake(*bakes)

Mark data items to be prepared for GPU.

##### FeatureVisual.update()



#### Properties

##### FeatureVisual.cluster_colors

Colors of the displayed clusters.

The first color is the color of the smallest cluster.

##### FeatureVisual.cluster_ids

Cluster ids of the displayed spikes.

##### FeatureVisual.cluster_order

List of selected clusters in display order.

##### FeatureVisual.empty

Specify whether the visual is currently empty or not.

##### FeatureVisual.extra_features



##### FeatureVisual.features

Displayed features.

This is a `(n_spikes, n_features)` array.

##### FeatureVisual.marker_size

Marker size in pixels.

##### FeatureVisual.masks

Masks of the displayed spikes.

##### FeatureVisual.n_boxes

Number of boxes in the grid.

##### FeatureVisual.n_clusters

Number of displayed clusters.

##### FeatureVisual.spike_clusters

The clusters assigned to the displayed spikes.

##### FeatureVisual.spike_ids

Spike ids to display.

##### FeatureVisual.x_dim

Dimensions in the x axis of all subplots.

This is a matrix of items which can be:

* tuple `(channel_id, feature_idx)`
* an extra feature name (string)

##### FeatureVisual.y_dim

Dimensions in the y axis of all subplots.

This is a matrix of items which can be:

* tuple `(channel_id, feature_idx)`
* an extra feature name (string)

### phy.plot.PanZoom

Pan & zoom transform.

The panzoom transform allow to translate and scale an object in the window
space coordinate (2D). This means that whatever point you grab on the
screen, it should remains under the mouse pointer. Zoom is realized using
the mouse scroll and is always centered on the mouse pointer.

You can also control programmatically the transform using:

* aspect: control the aspect ratio of the whole scene
* pan   : translate the scene to the given 2D coordinates
* zoom  : set the zoom level (centered at current pan coordinates)
* zmin  : minimum zoom level
* zmax  : maximum zoom level

#### Methods

##### PanZoom.add(programs)

Add programs to this tranform.

##### PanZoom.attach(canvas)

Attach this tranform to a canvas.

##### PanZoom.on_key_press(event)

Key press event.

##### PanZoom.on_mouse_move(event)

Pan and zoom with the mouse.

##### PanZoom.on_mouse_wheel(event)

Zoom with the mouse wheel.

##### PanZoom.on_resize(event)

Resize event.

#### Properties

##### PanZoom.aspect

Aspect (width/height).

##### PanZoom.is_attached

Whether the transform is attached to a canvas.

##### PanZoom.pan

Pan translation.

##### PanZoom.xmax

Maximum x allowed for pan.

##### PanZoom.xmin

Minimum x allowed for pan.

##### PanZoom.ymax

Maximum y allowed for pan.

##### PanZoom.ymin

Minimum y allowed for pan.

##### PanZoom.zmax

Maximal zoom level.

##### PanZoom.zmin

Minimum zoom level.

##### PanZoom.zoom

Zoom level.

##### PanZoom.zoom_to_pointer

Whether to zoom toward the pointer position.

### phy.plot.PanZoomGrid

Pan & zoom transform for a grid view.

This is used in a grid view with independent per-subplot pan & zoom.

The currently-active subplot depends on where the cursor was when
the mouse was clicked.

#### Methods

##### PanZoomGrid.add(programs)

Add programs to this tranform.

##### PanZoomGrid.attach(canvas)

Attach this tranform to a canvas.

##### PanZoomGrid.on_key_press(event)

Key press event.

##### PanZoomGrid.on_mouse_double_click(event)

Double click event.

##### PanZoomGrid.on_mouse_move(event)

Mouse move event.

##### PanZoomGrid.on_mouse_press(event)

Mouse press event.

##### PanZoomGrid.on_mouse_wheel(event)

Mouse wheel event.

##### PanZoomGrid.on_resize(event)

Resize event.

#### Properties

##### PanZoomGrid.aspect

Aspect (width/height).

##### PanZoomGrid.is_attached

Whether the transform is attached to a canvas.

##### PanZoomGrid.n_rows

Number of rows.

##### PanZoomGrid.pan

Pan translation.

##### PanZoomGrid.pan_matrix

Pan in every subplot.

##### PanZoomGrid.xmax



##### PanZoomGrid.xmin



##### PanZoomGrid.ymax



##### PanZoomGrid.ymin



##### PanZoomGrid.zmax

Maximal zoom level.

##### PanZoomGrid.zmin

Minimum zoom level.

##### PanZoomGrid.zoom

Zoom level.

##### PanZoomGrid.zoom_matrix

Zoom in every subplot.

##### PanZoomGrid.zoom_to_pointer

Whether to zoom toward the pointer position.

### phy.plot.TraceView

A VisPy canvas displaying traces.

#### Methods

##### TraceView.emit(name, **kwargs)



##### TraceView.on_draw(event)

Draw the main visual.

##### TraceView.on_key_press(event)

Handle key press events.

##### TraceView.on_resize(event)

Resize the OpenGL context.

##### TraceView.set_data(traces=None, spike_samples=None, spike_clusters=None, n_samples_per_spike=50, masks=None, colors=None)



#### Properties

##### TraceView.channel_scale

Vertical scale of the traces.

### phy.plot.WaveformView

A VisPy canvas displaying waveforms.

#### Methods

##### WaveformView.emit(name, **kwargs)



##### WaveformView.on_draw(event)

Draw the visual.

##### WaveformView.on_key_press(event)

Handle key press events.

##### WaveformView.on_key_release(event)



##### WaveformView.on_mouse_press(e)



##### WaveformView.on_mouse_wheel(event)

Handle mouse wheel events.

##### WaveformView.on_resize(event)

Resize the OpenGL context.

##### WaveformView.set_data(waveforms=None, masks=None, spike_clusters=None, channel_positions=None, channel_order=None, colors=None, **kwargs)



#### Properties

##### WaveformView.alpha

Opacity.

##### WaveformView.box_scale

Scale of the waveforms.

This is a pair of scalars.

##### WaveformView.overlap

Whether to overlap waveforms.

##### WaveformView.probe_scale

Scale of the probe.

This is a pair of scalars.

##### WaveformView.show_mean

Whether to show_mean waveforms.

### phy.plot.WaveformVisual

Display waveforms with probe geometry.

#### Methods

##### WaveformVisual.channel_hover(position)

Return the channel id closest to the mouse pointer.

*Parameters*


* `position` (tuple)

    The normalized coordinates of the mouse pointer, in world
    coordinates (in `[-1, 1]`).

##### WaveformVisual.draw()

Draw the waveforms.

##### WaveformVisual.set_to_bake(*bakes)

Mark data items to be prepared for GPU.

##### WaveformVisual.update()



#### Properties

##### WaveformVisual.alpha

Alpha transparency (between 0 and 1).

##### WaveformVisual.box_scale

Scale of the waveforms.

This is a pair of scalars.

##### WaveformVisual.channel_order



##### WaveformVisual.channel_positions

Positions of the channels.

This is a `(n_channels, 2)` array.

##### WaveformVisual.cluster_colors

Colors of the displayed clusters.

The first color is the color of the smallest cluster.

##### WaveformVisual.cluster_ids

Cluster ids of the displayed spikes.

##### WaveformVisual.cluster_order

List of selected clusters in display order.

##### WaveformVisual.empty

Specify whether the visual is currently empty or not.

##### WaveformVisual.masks

Masks of the displayed spikes.

##### WaveformVisual.n_clusters

Number of displayed clusters.

##### WaveformVisual.overlap

Whether to overlap waveforms.

##### WaveformVisual.probe_scale

Scale of the probe.

This is a pair of scalars.

##### WaveformVisual.spike_clusters

The clusters assigned to the displayed spikes.

##### WaveformVisual.spike_ids

Spike ids to display.

##### WaveformVisual.waveforms

Displayed waveforms.

This is a `(n_spikes, n_samples, n_channels)` array.

## phy.stats

Statistics functions.

##### phy.stats.pairwise_correlograms(spike_samples, spike_clusters, binsize=None, winsize_bins=None)

Compute all pairwise correlograms in a set of neurons.

TODO: improve interface and documentation.

## phy.traces

Spike detection, waveform extraction.

##### phy.traces.compute_threshold(arr, single_threshold=True, std_factor=None)

Compute the threshold(s) of filtered traces.

*Parameters*


* `arr` (ndarray)

    Filtered traces, shape `(n_samples, n_channels)`.

* `single_threshold` (bool)

    Whether there should be a unique threshold for all channels, or
    one threshold per channel.

* `std_factor` (float or 2-tuple)

    The threshold in unit of signal std. Two values can be specified
    for multiple thresholds (weak and strong).

*Returns*


* `thresholds` (ndarray)

    A `(2,)` or `(2, n_channels)` array with the thresholds.

### phy.traces.Filter

Multichannel bandpass filter.

The filter is applied on every column of a 2D array.

*Example*

```python
fil = Filter(rate=20000., low=5000., high=15000., order=4)
traces_f = fil(traces)
```

#### Methods

#### Properties

### phy.traces.FloodFillDetector

Detect spikes in weak and strong threshold crossings.

*Parameters*


* `probe_adjacency_list` (dict)

    A dict `{channel: [neighbors]}`.

* `join_size` (int)

    The number of samples defining the tolerance in time for
    finding connected components

*Example*

```python
det = FloodFillDetector(probe_adjacency_list=...,
                        join_size=...)
components = det(weak_crossings, strong_crossings)
```

`components` is a list of `(n, 2)` int arrays with the sample and channel
for every sample in the component.

#### Methods

#### Properties

### phy.traces.PCA

Apply PCA to waveforms.

#### Methods

##### PCA.fit(waveforms, masks=None)

Compute the PCs of waveforms.

*Parameters*


* `waveforms` (ndarray)

    Shape: `(n_spikes, n_samples, n_channels)`

* `masks` (ndarray)

    Shape: `(n_spikes, n_channels)`

##### PCA.transform(waveforms, pcs=None)

Project waveforms on the PCs.

*Parameters*


* `waveforms` (ndarray)

    Shape: `(n_spikes, n_samples, n_channels)`

#### Properties

### phy.traces.SpikeLoader

Translate selection with spike ids into selection with
absolute times.

#### Methods

#### Properties

### phy.traces.Thresholder

Threshold traces to detect spikes.

*Parameters*


* `mode` (str)

    `'positive'`, `'negative'`, or `'both'`.

* `thresholds` (dict)

    A `{str: float}` mapping for multiple thresholds (e.g. `weak`
    and `strong`).

*Example*

```python
thres = Thresholder('positive', thresholds=(.1, .2))
crossings = thres(traces)
```

#### Methods

##### Thresholder.detect(data_t, threshold=None)

Perform the thresholding operation.

##### Thresholder.transform(data)

Return `data`, `-data`, or `abs(data)` depending on the mode.

#### Properties

### phy.traces.WaveformExtractor

Extract waveforms after data filtering and spike detection.

#### Methods

##### WaveformExtractor.align(waveform, s_aligned)



##### WaveformExtractor.extract(data, s_aligned, channels=None)



##### WaveformExtractor.masks(data_t, wave, comp)



##### WaveformExtractor.set_thresholds(**kwargs)



##### WaveformExtractor.spike_sample_aligned(wave, comp)



#### Properties

### phy.traces.WaveformLoader

Load waveforms from filtered or unfiltered traces.

#### Methods

#### Properties

##### WaveformLoader.channels

List of channels.

##### WaveformLoader.n_channels_waveforms

Number of channels kept for the waveforms.

##### WaveformLoader.traces

Raw traces.

### phy.traces.Whitening

Compute a whitening matrix and apply it to data.

Contributed by Pierre Yger.

#### Methods

##### Whitening.fit(x, fudge=1e-18)

Compute the whitening matrix.

*Parameters*


* `x` (array)

    An `(n_samples, n_channels)` array.

##### Whitening.transform(x)

Whiten some data.

*Parameters*


* `x` (array)

    An `(n_samples, n_channels)` array.

#### Properties

## phy.utils

Utilities.

##### phy.utils.debug(*msg)

Generate a debug message.

##### phy.utils.download_file(url, output_path=None)

Download a binary file from an URL.

The checksum will be downloaded from `URL + .md5`. If this download
succeeds, the file's MD5 will be compared to the expected checksum.

*Parameters*


* `url` (str)

    The file's URL.

* `output_path` (str or None)

    The path where the file is to be saved.

*Returns*


* `output_path` (str)

    The path where the file was downloaded.

##### phy.utils.download_sample_data(filename, output_dir=None, base='cortexlab')

Download a sample dataset.

*Parameters*


* `filename` (str)

    Name of the sample dataset to download.

* `output_dir` (str)

    The directory where to save the file.

* `base` (str)

    The id of the base URL. Can be `'cortexlab'` or `'github'`.

##### phy.utils.info(*msg)

Generate an info message.

##### phy.utils.register(logger)

Register a logger.

##### phy.utils.set_level(level)

Set the level of all registered loggers.

*Parameters*


* `level` (str)

    Can be `warn`, `info`, or `debug`.

##### phy.utils.unregister(logger)

Unregister a logger.

##### phy.utils.warn(*msg)

Generate a warning.

### phy.utils.Bunch

A dict with additional dot syntax.

#### Methods

##### Bunch.copy()



#### Properties

### phy.utils.EventEmitter

Class that emits events and accepts registered callbacks.

Derive from this class to emit events and let other classes know
of occurrences of actions and events.

*Example*

```python
class MyClass(EventEmitter):
    def f(self):
        self.emit('my_event', 1, key=2)

o = MyClass()

# The following function will be called when `o.f()` is called.
@o.connect
def on_my_event(arg, key=None):
    print(arg, key)

```

#### Methods

##### EventEmitter.connect(func=None, event=None, set_method=False)

Register a callback function to a given event.

To register a callback function to the `spam` event, where `obj` is
an instance of a class deriving from `EventEmitter`:

```python
@obj.connect
def on_spam(arg1, arg2):
    pass
```

This is called when `obj.emit('spam', arg1, arg2)` is called.

Several callback functions can be registered for a given event.

The registration order is conserved and may matter in applications.

##### EventEmitter.emit(event, *args, **kwargs)

Call all callback functions registered with an event.

Any positional and keyword arguments can be passed here, and they will
be fowarded to the callback functions.

Return the list of callback return results.

##### EventEmitter.reset()

Remove all registered callbacks.

##### EventEmitter.unconnect(*funcs)

Unconnect specified callback functions.

#### Properties

### phy.utils.ProgressReporter

A class that reports progress done.

*Example*

```python
pr = ProgressReporter()
pr.set_progress_message("Progress: {progress}%...")
pr.set_complete_message("Completed!")
pr.value_max = 10

for i in range(10):
    pr.value += 1  # or pr.increment()
```

You can also add custom keyword arguments in `pr.increment()`: these
will be replaced in the message string.

*Emits*

* `progress(value, value_max)`
* `complete()`

#### Methods

##### ProgressReporter.connect(func=None, event=None, set_method=False)

Register a callback function to a given event.

To register a callback function to the `spam` event, where `obj` is
an instance of a class deriving from `EventEmitter`:

```python
@obj.connect
def on_spam(arg1, arg2):
    pass
```

This is called when `obj.emit('spam', arg1, arg2)` is called.

Several callback functions can be registered for a given event.

The registration order is conserved and may matter in applications.

##### ProgressReporter.emit(event, *args, **kwargs)

Call all callback functions registered with an event.

Any positional and keyword arguments can be passed here, and they will
be fowarded to the callback functions.

Return the list of callback return results.

##### ProgressReporter.increment(**kwargs)

Equivalent to `self.value += 1`.

Custom keywoard arguments can also be passed to be processed in the
progress message format string.

##### ProgressReporter.is_complete()

Return whether the task has completed.

##### ProgressReporter.reset(value_max=None)

Reset the value to 0 and the value max to a given value.

##### ProgressReporter.set_complete(**kwargs)

Set the task as complete.

##### ProgressReporter.set_complete_message(message)

Set a complete message.

##### ProgressReporter.set_progress_message(message, line_break=False)

Set a progress message.

The string needs to contain `{progress}`.

##### ProgressReporter.unconnect(*funcs)

Unconnect specified callback functions.

#### Properties

##### ProgressReporter.progress

Return the current progress as a float value in `[0, 1]`.

##### ProgressReporter.value

Current value (integer).

##### ProgressReporter.value_max

Maximum value (integer).

### phy.utils.Settings

Manage default, user-wide, and experiment-wide settings.

#### Methods

##### Settings.get(key, default=None)

Return a settings value.

##### Settings.keys()

Return the list of settings keys.

##### Settings.on_open(path)

Initialize settings when loading an experiment.

##### Settings.save()

Save settings to an internal settings file.

#### Properties

