---
layout: post
title: "A1. Alternative ways of getting OrthoFinder"
author: "David Emms"
categories: orthofinder_tutorials
tags: [documentation]
post_type: supplementary
---

In most cases the easiest way to get OrthoFinder is to download the latest release package from [github](https://github.com/davidemms/OrthoFinder/releases) as described here: [Downloading and checking OrthoFinder]({% post_url 2019-09-18-downloading-and-checking-orthofinder %}). Here are some alternatives in case of problems.

## Common problems

**OrthoFinder help file prints, but it cannot run one of the dependencies:**

* If one of the dependencies (diamond, mcl or fastme) does not work on your machine then you will need to delete the file in the `OrthoFinder/bin` directory and install it yourself. There's guidance on installing the dependencied here: <https://github.com/davidemms/OrthoFinder#installing-dependencies>

## OrthoFinder on Mac

The best way to use OrthoFinder on a Mac is to use the source code version and install the dependencies yourself: mcl, diamond & fastme. See <https://github.com/davidemms/OrthoFinder#installing-dependencies>. Alternatively you can use Bioconda or Docker.

## Source code version

* You can also just use the standard python version, **OrthoFinder_source.tar.gz** from the [releases](https://github.com/davidemms/OrthoFinder/releases) page. This will require a python installation (version 2.7 or 3) together with the numpy and scipy libraries. There are detailed instructions here: <https://github.com/davidemms/OrthoFinder/#python-source-code-version>.

**If the binary package doesn't work on your computer then:**

* Previously, a second packaged version of OrthoFinder was provided, **OrthoFinder_glibc-2.17.tar.gz** to support older operating systems. Now, by default there is only one packaged version and it is built with glbic version 2.15. This should be compatible with all linux machines. If for some reason this isn't the case and you get an error message like the following then please let me know: `ImportError: /usr/lib64/libc.so.6: version GLIBC_2.15' not found`. Alternatively, you can also use the standard python version, **OrthoFinder_source.tar.gz**, described above.

## Bioconda 
OrthoFinder is available with bioconda: <https://bioconda.github.io/recipes/orthofinder/README.html>. Thanks to the many people who I'm aware of having contributed to setting this up: Anthony Bretaudeau, Nicola Soranzo, Sacha Laurent, Christian Brueffer, Nathan Weeks, Johannes Köster, pvanheus, Björn Grüning, Emil Hägglund, Andreas Sjödin, Gildas Le Corguillé & Devon Ryan. And thanks also to anyone else who has helped.

Bioconda: Getting Started: <https://bioconda.github.io/user/install.html>

Installing OrthoFinder:
```
conda install orthofinder
```

## Docker
OrthoFinder 2.3.3 is available on Docker: [davidemms/orthofinder](https://hub.docker.com/repository/docker/davidemms/orthofinder) thanks to Thomas Roder & Monjeaud Cyril. 

Running OrthoFinder using Docker:
```
docker run -it --rm davidemms/orthofinder orthofinder -h
docker run --ulimit nofile=1000000:1000000 -it --rm -v /full/path/to/fastas:/input:Z davidemms/orthofinder orthofinder -f /input
```

## Installing OrthoFinder
OrthoFinder doesn't need to be installed, you can just call it from where you downloaded it. If you do want to install it somewhere, you will need to include the config.json file in the directory containing orthofinder or in the "source_of" directory if using the source code version.

