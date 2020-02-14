---
layout: post
title: "A1. Alternative ways of getting OrthoFinder"
author: "David Emms"
categories: orthofinder_tutorials
tags: [documentation]
post_type: supplementary
---

On Linux the easiest way to get OrthoFinder is to download the latest release package from [github](https://github.com/davidemms/OrthoFinder/releases) as described here: [Downloading and checking OrthoFinder]({% post_url 2019-09-18-downloading-and-checking-orthofinder %}). This contains everything that's required in a single package, so you don't need to install anything.

## OrthoFinder on Mac

The best way to use OrthoFinder on a Mac is to use Bioconda, see the Bioconda section below for details.

An alternative is to use the source code version and install the dependencies yourself: python together with the numpy and scipy libraries plus the external programs mcl, diamond & fastme. See <https://github.com/davidemms/OrthoFinder#installing-dependencies>. There is also a Docker image.

## OrthoFinder on Windows

You can run OrthoFinder on Windows using Docker if your computer meets Docker's system requirements. See below for details.

## Bioconda 
Bioconda provides a very easy way to install OrthoFinder on Linux or Mac. You can refer to the [Bioconda Getting Started](https://bioconda.github.io/user/install.html) page for details, but the basic steps are:

On Mac:

```
curl -L -O https://repo.anaconda.com/miniconda/Miniconda3-latest-MacOSX-x86_64.sh
sh Miniconda3-latest-MacOSX-x86_64.sh
```

Or, on Linux:

```
wget https://repo.anaconda.com/miniconda/Miniconda3-latest-Linux-x86_64.sh
sh Miniconda3-latest-Linux-x86_64.sh
```

Then for both Linux & Mac:

```
conda config --add channels defaults
conda config --add channels bioconda
conda config --add channels conda-forge
```

Then close your terminal and open a new one to complete the installation. Now install OrthoFinder:

```
conda install orthofinder
```
Test you can run OrthoFinder by downloading the Example Dataset to your current working directory from here: <https://bioinformatics.plants.ox.ac.uk/davidemms/public_data/ExampleData.zip>. Unzip it and then run:
```
orthofinder -f ExampleData
```

*Thanks to the many people who I'm aware of having contributed to setting this up: Anthony Bretaudeau, Nicola Soranzo, Sacha Laurent, Christian Brueffer, Nathan Weeks, Johannes Köster, pvanheus, Björn Grüning, Emil Hägglund, Andreas Sjödin, Gildas Le Corguillé & Devon Ryan. And thanks also to anyone else who has helped.*


## Source code version

You can also just use the standard python version, **OrthoFinder_source.tar.gz** from the [releases](https://github.com/davidemms/OrthoFinder/releases) page. This will require a python installation (version 2.7 or 3) together with the numpy and scipy libraries. There are detailed instructions here: <https://github.com/davidemms/OrthoFinder/#python-source-code-version>.


## Docker
OrthoFinder is available on Docker: [davidemms/orthofinder](https://hub.docker.com/repository/docker/davidemms/orthofinder) thanks to Thomas Roder & Monjeaud Cyril for their work on this. 

To install Docker, follow the instructions here: <https://docs.docker.com/install/>

To run OrthoFinder on Windows using Docker:

1. Open the Windows PowerShell from the Start Menu

2. Make a directory to work in & cd into it (you can paste into the shell by right-clicking on it): 
``` 
mkdir orthofinder
cd orthofinder
```

3. Get OrthoFinder:
```
docker pull davidemms/orthofinder
```

4. Check you can run OrthoFinder and get it to display help file:
```
docker run -it --rm davidemms/orthofinder orthofinder -h
```

5. Download the Example Data and unzip it ()
```
wget https://bioinformatics.plants.ox.ac.uk/davidemms/public_data/ExampleData.zip -outfile ExampleData.zip
Expand-Archive -LiteralPath ExampleData.zip -DestinationPath .
```

    > You might find it easier to download and extract the files without using the shell, these commands are provided to make it easy to run these steps by copying and pasting if you prefer. The file is here: <https://bioinformatics.plants.ox.ac.uk/davidemms/public_data/ExampleData.zip>

6. Now run OrthoFinder on the Example Dataset. **You'll have to edit this command to replace the "C:\Users\dops0000\orthofinder\ExampleData\" part with full path to the ExampleData folder on your computer**:
```
docker run --ulimit nofile=1000000:1000000 -it --rm -v C:\Users\dops0000\orthofinder\ExampleData\:/input:Z davidemms/orthofinder orthofinder -f /input
```

7. You can now use the same command to call OrthoFinder on your input folder of proteomes. See the other tutorials for further guidance.

    > Running OrthoFinder via Docker is likely to be less quick than it would be run directly on a linux server but should be more than enough for many analyses.

## Installing OrthoFinder
OrthoFinder doesn't need to be installed, you can just call it from where you downloaded it. If you do want to install it somewhere, you will need to include the config.json file in the directory containing orthofinder or in the "source_of" directory if using the source code version.

## Possible problems

**OrthoFinder help file prints, but it cannot run one of the dependencies:**

* If one of the dependencies (diamond, mcl or fastme) does not work on your machine then you will need to delete the file in the `OrthoFinder/bin` directory and install it yourself. There's guidance on installing the dependencied here: <https://github.com/davidemms/OrthoFinder#installing-dependencies>

**If the binary package doesn't work on your computer then:**

* Previously, a second packaged version of OrthoFinder was provided, **OrthoFinder_glibc-2.17.tar.gz** to support older operating systems. Now, by default there is only one packaged version and it is built with glbic version 2.15. This should be compatible with all linux machines. If for some reason this isn't the case and you get an error message like the following then please let me know: `ImportError: /usr/lib64/libc.so.6: version GLIBC_2.15' not found`. Alternatively, you can also use the standard python version, **OrthoFinder_source.tar.gz**, described above.