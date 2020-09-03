# Introduction

This repository is meant to be the how and the what of everything.

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT) [![Maintenance](https://img.shields.io/badge/Maintained%3F-yes-green.svg)](https://GitHub.com/Naereen/StrapDown.js/graphs/commit-activity) [![GitHub contributors](https://img.shields.io/github/contributors/Naereen/StrapDown.js.svg)](https://github.com/SmartMobilityAlgorithms/GettingStarted/graphs/contributors) 
[![GitHub issues](https://img.shields.io/github/issues/Naereen/StrapDown.js.svg)](https://github.com/SmartMobilityAlgorithms/GettingStarted/issues) 
[![PRs Welcome](https://img.shields.io/badge/PRs-welcome-brightgreen.svg?style=flat-square)](https://github.com/SmartMobilityAlgorithms/GettingStarted/pulls)

### Contents

1.  Introduction and Quick Overview 

2.  General structure of the repositories

3.  Libraries used
    * osmnx
    * networkx
    * osrm
    * geopandas
    * shapely
    * nominatim
    * visualization libraries 
    
4.  Quick tutorials
    * snapshots of all the tools
    * networkx
    * osmnx
    * geopandas/ shapely
    * osrm and routing
    
5. Setting up your environment
    * Linux 
    * MacOS 
    * Windows 10
    * Jupyter Notebooks

6. Getting the data

7. Relevant Tools

---

## Introduction and Quick Overview

This organization is meant to accompany ECE1724H S Bio-inspired Algorithms for Smart Mobility course being offered at University of Toronto. This project-based course provides a comprehensive introduction to bio-inspired search algorithms and highlights the power of these computational techniques in solving ill-structured problems in the context of smart mobility.

The code in all of the notebooks is step-by-step guide for the implementation of the algorithms in the course using actual maps from OpenStreetMaps. 


### Language Choice

We have choosen `python` as the main and only language as it doesn't have much jargon and the signal to noise ratio in code is very high; it is almost like pseudocode. `Python` is not the optimal language for scientific computing and especially with large graphs that we extract from maps. All the major routing and navigation engines usually use `C++` or `Java` and most of the authors of the seminal papers in the field usually provide `C++` implementation accompying their papers. What would be the perfect trade-off between `python` and `C++`? `Julia`; it was made with scientific computing in mind and it gives a comparable performance with `C++` and with almost the readability  of `python`.

Surely, We would love to have `Julia` implementation for the algorithms in so if you want to do so, don't hesitate to open PR with your `Julia` code and just change the code line by line from `Python` to `Julia`.

---

## General structure of the repository and reusability of the code


Each repository contains three sections:

### 1. Algorithms Notebooks

Here we introduce the algorithms and how to implement them on a real world `.osm` data and we would provide the pseudocode to tune down the noise of programming languages quirks and what to consider and what you should be aware of when implementing these algorithms. These notebooks are complementary for the materials in the lectures.

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

### osrm

Sometimes in a lot of problems, you are not concerned about finding the route between two places and want to have the routes as given. [OSRM](http://project-osrm.org/) does exactly that; it is a routing engine with an API that you would feed with coordinates and gives you the fastest route between them. It has other useful capabilities like doing travelling salesman and solving all pairs shortest path.

### geopandas

It is an extension to pandas to handle geospatial data by extending the datatypes of pandas and be able to query and manipulate spatial data otherwise you would need to deal with [spatial databases](https://en.wikipedia.org/wiki/Spatial_database) for these operations, like how to properly and efficiently represent polygons and curved lines and query them without much overhead (for database folks, the indexing of spatial data is different than normal data).

### shapely

It provides us with datatypes to represent geometric objects that geopandas exploit to represent spatial data.

### nominatim

It is used to look up a location from a textual description (the official website description). This is called geocoding and decoding which is translating address of a location to its coordinates.

### visualization libraries

There are <b>many</b> libraries for visualization, but we are mainly using [folium](https://python-visualization.github.io/folium/) and [ipyleaflet](https://ipyleaflet.readthedocs.io/en/latest/) and both of them are just wrapper around [leaflet.js](https://github.com/Leaflet/Leaflet) which is the go-to library for any kind of map visualization in almost all web and mobile applications.

Although `ipyleaflet` is much powerful and easy to use than `folium` but unfortunately you can't use `ipyleaflet` on google colab because of security issue; see [googlecolab/colabtools#60](https://github.com/googlecolab/colabtools/issues/60) for more details. That is why `osmnx` use `folium` and offers a good enough interface for visualization. **Anyways**, you don't have to worry about that at all, as we offer in the repositories an API that knows when you are running the notebook on your local machine and uses `ipyleaflet` and uses `folium` when you are running the notebook on google colab and we have made them offer *almost* identical visualization capabilities (`ipyleaflet` is better). If you want to see how they work, check the code in `Utilities/utils/viz.py`.

There are other visualization libraries that you should be aware of: 
* [hvplot](https://hvplot.holoviz.org/user_guide/Geographic_Data.html), if you want to get going through your analysis with geopandas and dataframes and all that. There are no place for that but you need to be aware of the significance of working with vanilla [GeoPandas](https://geopandas.org/), and that `osmnx` [supports that](https://osmnx.readthedocs.io/en/stable/osmnx.html#module-osmnx.projection) and yields two dataframes: one for all your nodes and one for all the edges.

* [mplleaflet](https://github.com/jwass/mplleaflet), which is another `leaflet` based library, but it plays really nice with `matplotlib`.

#### Note

Most of these libraries uses coordinates of a certain place to do its job, but please take into account that some of them accept the coordinates as (longtitude, latitude) and others as (latitude, longtitude). 


---

## Quick Tutorials

1.
2.
3.
4.
5.

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
```\> conda create -n uoft python=3.7```

Activate the environment
```\> conda activate uoft```

Install the following packages

```\> conda install -c conda-forge rtree```

```\> conda install -c conda-forge osmnx```

```\> conda install -c conda-forge ipyleaflet```

```\> conda install -c conda-forge folium```

```\> conda install -c conda-forge tqdm```

<!--- 
We don't want to *make* anything on ```Windows``` for sure so we will be using ```conda```. Open your command prompt as enter these two commands

```\> conda config --prepend channels conda-forge```

```\> conda create -n ox --strict-channel-priority osmnx```
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

## Getting the data

There are many ways to get the data including using `osmnx` directly and get your data in a very clean way, but in some situations you need to have more control over the data and need to tune it and alter it in ways that `osmnx` can't do. So we need to get down to get the data from the original source of OpenStreetMaps and download the data directly and after that we let `osmnx` parse it.</br>

We will be talking now about two ways of getting the data from OpenStreetMaps:

1. Download the data in their vanilla form and structure straight out of OpenStreetMaps (hard way and not widely used in practice).
2. Use OpenStreetMaps API which is called Overpass API and get your data and filter it on the fly and can be used from `Python` and `Javascript`.

#

* You can acquire street system map for the province of any region of interest (ROI) from [OpenStreetMap](https://www.openstreetmap.org/). Note that the size of some ROI map after decompressing may be is several GBs.

* Filter-out the map of ROI to contain only the major roads using the [osmfilter tool](https://wiki.openstreetmap.org/wiki/Osmfilter).

* Pre-filtered datasets that contain actual mapping data can be downloaded from [Geofabrik](https://download.geofabrik.de/index.html)

* [POI Factory](http://www.poi-factory.com/) can be used to get map data of any point of interest. You have to create an account to get access to the data.

* Use `osmnx` to read `.osm` file with [`osmnx.graph_from_xml`](https://osmnx.readthedocs.io/en/stable/osmnx.html?highlight=from%20file#osmnx.graph.graph_from_xml) and [voila](https://github.com/voila-dashboards/voila).

#

Check [Open-Datasets](https://github.com/SmartMobilityAlgorithms/Open-Datasets) in which we discuss in enough details how to use Overpass API.

#

### Completness of the data

There are some things that you need to be aware of: the data from OpenStreetMaps are not complete, not in the sense that there are major uncharted areas of the earth but the nodes of the same area usually are not grouped properly so you can have two places with obvious and feasible route between them but the two nodes are not related in any way in the `.osm` file and there is no [way](https://wiki.openstreetmap.org/wiki/Way)/[relation](https://wiki.openstreetmap.org/wiki/Relation) between these nodes, so `osmnx` parser put them in different graph component at this point we would go to use `osrm` to find the route between these nodes and make the graph complete. 

---

## Relevant Tools

1. Developing web/mobile application and you want to get really fancy with your maps, you have [Open layers](https://openlayers.org/) which is the industry standard for that.

2. Traffic beyond just max speed and duration? [traffic per edge](https://github.com/Project-OSRM/osrm-backend/wiki/Traffic) or [Open traffic](https://github.com/opentraffic)




