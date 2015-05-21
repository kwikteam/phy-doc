## Interactive plotting

phy 0.1.0 provides advanced interactive visualization routines to explore large volumes of data. These routines are based on VisPy, a Python library that leverages the graphics card acceleration for fast display of data.

> VisPy requires a graphics driver compatible with OpenGL 2.1+. Any decent computer less than ten years old will work. That being said, computers with a more recent and capable graphics cards (AMD or NVIDIA) will allow you to visualize more data. **You need to have the latest drivers of your graphics card properly installed**.

Here are the currently-supported visualizations:

* Waveforms with probe geometry
* Multi-dimensional features
* Extracellular traces with spikes
* Matrix of auto- and cross-correlograms

All of these plots are highly interactive and let you explore your data effectively.

More interactive and static visualization routines (for publication-ready plotting, for example) will be added in future releases.

### Keyboard and mouse shortcuts

Press `h` to see the shortcuts in any given view.

#### Pan and zoom

* pan: `arrows`, left-drag
* zoom: `+`, `-`, wheel, right-drag
* reset: `r`

In grid views (feature view and CCG view):

* subplot pan: `arrows`, left-drag
* subplot zoom: `+`, `-`, right-drag
* subplot reset: `r`
* global zoom: `shift+wheel`
* global reset: `shift+r`

#### Waveforms

* change waveform scaling: `ctrl+arrows`
* change probe scaling: `shift+arrows`
* select a channel: `1+left click` to select that channel in the corresponding subplots in the feature view (only valid in the manual clustering GUI)

#### Features

* set marker size: `ctrl++`, `ctrl+-`
* toggle enlarge a subplot: `double click`
* add lasso point: `ctrl+left click`
* clear lasso: `ctrl+right click`

#### Traces

* change channel scale: `ctrl+up`, `ctrl+down`
* scroll: `ctrl+arrows`
* fast scroll: `shift+arrows`

#### Correlograms
