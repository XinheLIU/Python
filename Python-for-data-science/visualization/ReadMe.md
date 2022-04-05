# Visualization

- [Visualization](#visualization)
  - [Matplotlib](#matplotlib)
    - [Basic](#basic)
      - [Matplotlib Object Layers](#matplotlib-object-layers)
      - [Colors and Styles (Attributes control)](#colors-and-styles-attributes-control)
      - [Ax vs Plt](#ax-vs-plt)
    - [Matplot Lib APIs](#matplot-lib-apis)
      - [MatplotLib\_Utils](#matplotlib_utils)
  - [Pandas Ploting](#pandas-ploting)
  - [Seaborn](#seaborn)
    - [Basic](#basic-1)
    - [Replot (relational plot)](#replot-relational-plot)
    - [Distplot (distribution plots)](#distplot-distribution-plots)
  - [Catplot (Categorical)](#catplot-categorical)
  - [Other Useful Visualization Libaries](#other-useful-visualization-libaries)
    - [PyLab](#pylab)
  - [Boken](#boken)
  - [Plotly](#plotly)

## Matplotlib

### Basic

```py
# use in notebook: the output is displayed inline in notebook
%matplotlib inline
import matplotlib.pyplot as plt
# set style
plt.style.use('seaborn-whitegrid')
import numpy as np
```

- plt.style
  - [sns styles](http://seaborn.pydata.org/tutorial/aesthetics.html)

#### Matplotlib Object Layers

![Matplotlib-1](2022-04-05-21-09-35.png)

```py
fig = plt.figure()
ax = plt.axes()

x = np.linspace(0, 10, 1000)
ax.plot(x, np.sin(x)) # alternatively, use plt.plot(x, np.sin(x));
```

- the figure (an instance of the class plt.Figure) can be thought of as a single container that contains all the objects representing axes, graphics, text, and labels. 
- The axes (an instance of the class plt.Axes) : a bounding box with ticks and labels, which will eventually contain the plot elements that make up our visualization.

#### Colors and Styles (Attributes control)

- [color](https://matplotlib.org/3.5.0/gallery/color/named_colors.html)
- [cmap](https://matplotlib.org/3.5.1/tutorials/colors/colormaps.html)
- [linestyle](https://matplotlib.org/3.5.1/gallery/lines_bars_and_markers/linestyles.html)
- plt.xlim(), plt.ylim
- [plt.axis](https://matplotlib.org/3.5.0/api/_as_gen/matplotlib.pyplot.axis.html)
  - 'tight', 'equal', ...
- plt.title(), .xlabel(),.ylabel(), .legend

#### Ax vs Plt

Most plt functions translate directly to ax method, few exceptions

- plt.xlabel() → ax.set_xlabel()
- plt.ylabel() → ax.set_ylabel()
- plt.xlim() → ax.set_xlim()
- plt.ylim() → ax.set_ylim()
- plt.title() → ax.set_title()
  
use ax.set() method

```py
ax = plt.axes()
ax.plot(x, np.sin(x))
ax.set(xlim=(0, 10), ylim=(-2, 2),
       xlabel='x', ylabel='sin(x)',
       title='A Simple Plot');
```

### Matplot Lib APIs

plotting API - pyplot module

- plt.plot(x1,y1,x2,y2..., attributes controls ...)
  - attributes control
    - type
    - [markers](https://matplotlib.org/3.5.1/gallery/lines_bars_and_markers/marker_reference.html)
    - markersize, linewidth, markerfacecolor, markeredgecolor, markeredgewidth, etc
- plt.subplot\(&lt;nrow&gt;&lt;ncol&gt;&lt;ind&gt;, [color, maker..]) 
- other kinds of plots
  - plt.scatter
  - plt.hist
    - plt.hist2d, plt.hexbin
  - plt.bar
  - plt.errorbar(x, y, yerr, fmt, color, eclor, elinewidth, capsize)
  - plt.fill_between(x, ydown, yup, color, alpha = )
  - plt.contor(X, Y, Z, colors = )
- plt.gca\(\) - set axes
    - .setx\_lim\(\), .set\_ylim\(\)
- plt.figure\figsize&gt;,&lt;dpi&gt;
- plt.subplots
  - 

Ax object

- ax.legend()
  - loc, frameon, ncol, borderpad

**Pyplot Module**: MATLAB-like interfaces

#### MatplotLib\_Utils

- simpleTrainingCurves\(\)
  - to visualize training

## Pandas Ploting

- &lt;dataframe/data column/ data series&gt;.plot\(\[kind\]\)
  - return to plt directly
  - use plt to set up arguments
    - x, y
    - kind
      - bar, pie
    - subplots = True/False
      - default plot all columns together
  - autopct = &lt;format string&gt;
- &lt;df&gt;.boxplot\(\)
  - 3 idioms returns different things
    - &lt;df&gt;.plot\(kind='hist'\)
    - &lt;df&gt;.plot.hist\(\)
    - &lt;df&gt;.hist\(\)

## Seaborn

> Seaborn is a Python data visualization library based on matplotlib. It provides a high-level interface for drawing attractive and informative statistical graphics.
> 
> - [Introduction](https://seaborn.pydata.org/introduction.html)
> - [Tutorial](https://seaborn.pydata.org/tutorial.html)

### Basic

- sns.set_theme()

### Replot (relational plot)

- sns.replot
- sns.scatterplot
- sns.lineplot

### Distplot (distribution plots)

- sns.histplot
  - plot.hist
- sns.kdeplot
- sns.jointplot
- sns.ecdfplot
- sns.rugplot
- sns.pairplot
- sns.FacetGrid

## Catplot (Categorical)

- sns.catplot
- stripplot() (with kind="strip"; the default)
- swarmplot() (with kind="swarm")
- Categorical distribution plots:
- boxplot() (with kind="box")
- violinplot() (with kind="violin")
- boxenplot() (with kind="boxen")
- Categorical estimate plots:
- pointplot() (with kind="point")
- barplot() (with kind="bar")
- countplot() (with kind="count")

## Other Useful Visualization Libaries

### PyLab

## Boken

## Plotly