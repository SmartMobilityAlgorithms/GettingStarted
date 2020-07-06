# Introduction
---
This repository is meant to the how and what we are going to do in these repositories.

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

---

I assume that you have Python 3.6+ installed in your system and I will go through how to install ```osmnx``` and ```networkx``` and ```jupyter```

---

#### Linux

---

You have two way either to use ```conda``` or ```pip``` to get everything working, but ```conda``` usually messes up the system dependencies and it is a bad idea to use it.

</br>

If you want to use ```conda```, you can just execute the following command.

```$ conda install -c conda-forge osmnx```

and that is it.

you need to get ```pip``` package manager installed to use it to fetch the other libraries.

```$ sudo apt install python3-pip```

Unfortunately we just can't "pip" our way through the dependencies required and that is it, ```osmnx``` depends on library called ```Rtree``` which needs to be *made* using this command

```$ apt-get install libspatialindex-c4v5```

and then after that we can use ```pip``` to get osmnx

```$ pip3 install osmnx```

To test that everything is working, issue the following command

```python3 -c "import osmnx"```

If there is any error in installation, the terminal will whine about missing module and whatnot. If so, open an issue and we will walk through the problems.

