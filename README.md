# Introduction

This repository is meant to be the how and the what of everything.

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT) [![Maintenance](https://img.shields.io/badge/Maintained%3F-yes-green.svg)](https://GitHub.com/Naereen/StrapDown.js/graphs/commit-activity) [![GitHub contributors](https://img.shields.io/github/contributors/Naereen/StrapDown.js.svg)](https://github.com/SmartMobilityAlgorithms/GettingStarted/graphs/contributors) [![GitHub issues](https://img.shields.io/github/issues/Naereen/StrapDown.js.svg)](https://github.com/SmartMobilityAlgorithms/GettingStarted/issues) [![GitHub issues-closed](https://img.shields.io/github/issues-closed/Naereen/StrapDown.js.svg)](https://github.com/SmartMobilityAlgorithms/GettingStarted/issues?q=is%3Aissue+is%3Aclosed) [![PRs Welcome](https://img.shields.io/badge/PRs-welcome-brightgreen.svg?style=flat-square)](https://github.com/SmartMobilityAlgorithms/GettingStarted/pulls)

### Contents

1.  General structure of the repository and reusability of the code

2.  Libraries used
    * osmnx
    * networkx
    * visualization Libraries 
    
3. Setting up your environment
    * Linux 
    * MacOS 
    * Windows 10
    * Don't bother

4. Final Comments and Important Notes

---

## General structure of the repository and reusability of the code

We are trying to introduce the implemenation and the usage of new search technique in each repository and their most widely used algorithms in practice by applying the algorithms on `OpenStreetMaps`data with usage of `osmnx` and animating these algorithms and solving real world problems as case studies in each repository. 

Each repository contains three sections:

### 1. Algorithms Notebooks

Here we introduce the algorithms and how to implement them on a real world `.osm` data and providing the pseudocode and what to consider and should be aware of when implementing these algorithms. These notebooks are complementary for the materials in the lectures.

### 2. Toy Problems Notebooks

These are more or less like the algorithm notebooks but with more focus on solving toy problems such as travelling salesman problem (TSP) or finding how to optimally pave a muddy city using minimum spanning tree (MST).

### 3. Case Studies Notebooks

These are real world problems found in the literature and potential course projects. We usually need to exert some efforts to get the data and think about how to solve the problem.


---

## Libraries Used

### osmnx

This library was developed by [geoff boeing](https://geoffboeing.com/) from University of Southren California to ease the process of retrieving and manipulating the data from OpenStreetMap and make it easier to be interpolated into Python applications. It offeres the ability to download the data (filtered) from OSM and returns the network as networkx graph data structure. The library is really big to be explained entirely in a README file but you can check the official website from [here](https://osmnx.readthedocs.io/en/stable/#) and follow Professor Geoff Boeing website as he posts regularly on the recent updates and trends about osmnx and the field.

### networkx

This is one of the pillars of Python programming and scientific computing besides numpy and scipy. Its main and only goal is supporting graphs data structures and the associated algorithms like shortest path and networks flow and optimization. `osmnx` returns the map as `networkx` network so it is possible to use all the library's functionalities on the maps obtained from OSM. Networkx has books written explaining its API's and we wholeheartedly recommend [Complex Network Analysis in Python: Recognize - Construct - Visualize - Analyze - Interpret](https://www.amazon.com/Complex-Network-Analysis-Python-Recognize/dp/1680502697) if you want to dive into it. Information about `networkx` is also available [here](https://networkx.github.io/). 

### visualization libraries

There are <b>many</b> libraries for visualization, but we are mainly using [folium](https://python-visualization.github.io/folium/) and [ipyleaflet](https://ipyleaflet.readthedocs.io/en/latest/) and both of them are just wrapper around [leaflet.js](https://github.com/Leaflet/Leaflet) which is the go-to library for any kind of map visualization in almost all web and mobile applications.

Although `ipyleaflet` is much powerful and easy to use than `folium` but unfortunately you can't use `ipyleaflet` on google colab because of security issue; see [googlecolab/colabtools#60](https://github.com/googlecolab/colabtools/issues/60) for more details. That is why `osmnx` use `folium` and offers a good enough interface for visualization. **Anyways**, you don't have to worry about that at all, as we offer in the repositories an API that knows when you are running the notebook on your local machine and uses `ipyleaflet` and uses `folium` when you are running the notebook on google colab and we have made them offer *almost* identical visualization capabilities (`ipyleaflet` is better). If you want to see how they work, check the code in `Utilities/utils/viz.py`.

There are other visualization libraries that you should be aware of: 
* [hvplot](https://hvplot.holoviz.org/user_guide/Geographic_Data.html), if you want to get going through your analysis with geopandas and dataframes and all that. There are no place for that but you need to be aware of the significance of working with vanilla [GeoPandas](https://geopandas.org/), and that `osmnx` [supports that](https://osmnx.readthedocs.io/en/stable/osmnx.html#module-osmnx.projection) and yields two dataframes: one for all your nodes and one for all the edges.

* [mplleaflet](https://github.com/jwass/mplleaflet), which is another `leaflet` based library, but it plays really nice with `matplotlib`.


---

## Setting up your environment

We assume that you have Python 3.6+ installed in your system and we will go through how to install ```osmnx``` and ```networkx``` and ```jupyter```

---

### Linux

You have two way either to use ```conda``` or ```pip``` to get everything working, but ```conda``` usually messes up the system dependencies on linux and complicate easy things and it is a bad idea to use it.

</br>

If you still want to use ```conda```, you can just execute the following command.

```$ conda install -c conda-forge osmnx```

and that is it.

</br>

If else, you need to get ```pip``` package manager installed to use it to fetch the other libraries.

```$ sudo apt install python3-pip```

Unfortunately we just can't "pip" our way through the dependencies because ```osmnx``` depends on library called ```Rtree``` which needs to be *made* using this command

```$ apt-get install libspatialindex-c4v5```

and then after that we can use ```pip``` to get osmnx

```$ pip3 install osmnx```

To test that everything is working, issue the following command

```$ python3 -c "import osmnx"```

If there is any error in installation, the terminal will whine about missing module and whatnot. If so, open an issue and we will walk through the problem together.

---

### MacOS

That exact same steps as above but instead of using ```apt```, you are going to use ```brew``` and that if you want to do the ```pip``` way. If you want to use ```conda```, it would be the exact same command.

---

### Windows

Create a conda environment
```>\ conda create -n uoft python=3.7```

Activate the environment
```>\ activate uoft```

Install the following packages

```>\ conda install -c conda-forge retree```

```>\ conda install -c conda-forge osmnx```

```>\ conda install -c conda-forge tqdm```

```>\ conda install -c conda-forge ipyleaflet```

```>\ conda install -c conda-forge follium```

<!--- 
We don't want to *make* anything on ```Windows``` for sure so we will be using ```conda```. Open your command prompt as enter these two commands

```>\ conda config --prepend channels conda-forge```

```>\ conda create -n ox --strict-channel-priority osmnx```
-->

---

### Jupyter -- For all operating systems

All the codes in the repositories are in jupyter notebooks so, we need to install that to launch the environment.</br>
For ```conda``` users and such
</br>

```conda install -c conda-forge jupyterlab```

```conda install -c conda-forge notebook```

</br>

For ```pip``` people
</br>

```pip install jupyterlab```

```pip install notebook```

---

### Don't bother

With every notebook, we are providing a google colab link to it and you don't have to setup anything at all.

#### Note

Things can go wrong very easily when you install the libraries because of building `Rtree` and you can miss up your whole `python` environment if you played with `pip` and `conda` at the same time.

Don't hesitate to open an issue if any thing comes up with you.

---

## Final comments and notes

The [`osmnx` tutorial](https://github.com/SmartMobilityAlgorithms/GettingStarted/blob/master/osmnx_tutorial.ipynb) in this repository is the easy way to get the data and construct the graph structure and get cracking with your analysis in python, but in some situations you need to have more control over the data and need to tune it and alter it in ways that `osmnx` can't do. So we need to get down to get the data from the original source of OpenStreetMaps and download the data directly and let `osmnx` parse it.</br>

Here are some few tips on how to get started with the whole getting data from the original source thing:

* You can acquire street system map for the province of any region of interest (ROI) from [OpenStreetMap](https://www.openstreetmap.org/). Note that the size of some ROI map after decompressing may be is several GBs.

* Filter-out the map of ROI to contain only the major roads using the [osmfilter tool](https://wiki.openstreetmap.org/wiki/Osmfilter).

* Pre-filtered datasets that contain actual mapping data can be downloaded from [Geofabrik](https://download.geofabrik.de/index.html)

* [POI Factory](http://www.poi-factory.com/) can be used to get map data of any point of interest. You have to create an account to get access to the data.

* Use `osmnx` to read `.osm` file with [`osmnx.graph_from_xml`](https://osmnx.readthedocs.io/en/stable/osmnx.html?highlight=from%20file#osmnx.graph.graph_from_xml) and [voila](https://github.com/voila-dashboards/voila).

---

There are some things that you need to be aware of: the data from OpenStreetMaps are not complete, not in the sense that there are uncharted areas of the earth but the nodes of the same area are not grouped properly so you can have two places with obvious and feasible route between them but the two nodes are not related in any way in the `.osm` file and there is no [way](https://wiki.openstreetmap.org/wiki/Way)/[relation](https://wiki.openstreetmap.org/wiki/Relation) between these nodes. 

But we really need to stitch these nodes together and find routes between them and that we would be talking about in [Open-Datasets](https://github.com/SmartMobilityAlgorithms/Open-Datasets) repository and how to use OpenStreetMaps API and their domain-specific language for querying their data and stitching things together.
