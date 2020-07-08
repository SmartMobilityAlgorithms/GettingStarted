# Introduction

This repository is meant to be the how and the what of everything.

### Contents

1. Setting up your environment
    * Linux 
    * MacOS 
    * Windows 10
    * Don't bother
2. Libraries used
    * osmnx
    * networkx
3. Final comments and notes

---

## Setting up your environment


I assume that you have Python 3.6+ installed in your system and I will go through how to install ```osmnx``` and ```networkx``` and ```jupyter```

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

Unfortunately we just can't "pip" our way through the dependencies required and that is it, ```osmnx``` depends on library called ```Rtree``` which needs to be *made* using this command

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

We don't want to *make* anything on ```Windows``` for sure so we will be using ```conda```. Open your command prompt as enter these two commands

```>\ conda config --prepend channels conda-forge```

```>\ conda create -n ox --strict-channel-priority osmnx```

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

---

## Libraries Used

*in progress*

---

## Final comments and notes

The [`osmnx` tutorial](/home/omar/DrAlaaKhamies/GettingStarted/osmnx_tutorial.ipynb) in this repository is the easy way to get the data and construct the graph structure and get cracking with search algorithms, but in some situations you need to have more control over the data and need to tune it and alter it in ways `osmnx` can't do.</br>

* You can acquire street system map for the province of any region of interest (ROI) from [OpenStreetMap](https://www.openstreetmap.org/). Note that the size of some ROI map after decompressing may be is several GBs.

* Filter-out the map of ROI to contain only the major roads using the [osmfilter tool](https://wiki.openstreetmap.org/wiki/Osmfilter ).

    * Pre-filtered datasets that contain actual mapping data can be downloaded from [Geofabrik](https://download.geofabrik.de/index.html)

    * [POI Factory](http://www.poi-
factory.com/) can be used to get map data of any point of interest. You have to create an account to get access to the data

* Use `osmnx` to read `.osm` file with [`osmnx.graph_from_xml`](https://osmnx.readthedocs.io/en/stable/osmnx.html?highlight=from%20file#osmnx.graph.graph_from_xml) and voila, you have your graph.