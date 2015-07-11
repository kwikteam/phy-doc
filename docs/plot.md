## Interactive plotting

phy 0.2.0 provides advanced interactive visualization routines to explore large volumes of data. These routines are based on [VisPy](http://vispy.org/), a Python library that leverages the graphics card acceleration for fast display of data.

> VisPy requires a graphics driver compatible with OpenGL 2.1+. Although any recent computer should work, it is recommended to use a relatively powerful graphics cards (AMD or NVIDIA). **You need to have the latest proprietary drivers of your graphics card properly installed**. On Linux, Mesa it not supported.

Here are the currently-supported visualizations:

* Waveforms with probe geometry
* Multi-dimensional features
* Extracellular traces with spikes
* Matrix of auto- and cross-correlograms

All of these plots are highly interactive and let you explore your data effectively.

More interactive and static visualization routines (for publication-ready plotting, for example) will be added in future releases.

The plots are displayed in the manual sorting GUI. You can also create independent plots with the `plot_***()` functions in the `phy.plot` package.

### Keyboard and mouse shortcuts

Press `h` to see the shortcuts in any given view. The shortcuts will show up in your terminal.
