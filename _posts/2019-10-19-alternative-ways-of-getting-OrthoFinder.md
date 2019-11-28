---
layout: post
title: "A1. Alternative ways of getting OrthoFinder"
author: "David Emms"
categories: orthofinder_tutorials
tags: [documentation]
post_type: supplementary
---

In most cases the easiest way to get OrthoFinder is to download the lastest release package from [github](https://github.com/davidemms/OrthoFinder/releases) as described here: [Downloading and checking OrthoFinder]({% post_url 2019-09-18-downloading-and-checking-orthofinder %}). Here are some alternatives in case of problems:

**If the binary package doesn't work on your computer then:**

* It may be that you have an old version of glibc on your computer you might see an error which includes this message: `ImportError: /usr/lib64/libc.so.6: version GLIBC_2.18' not found`. In this case you might still be able to use the **OrthoFinder_glibc-2.17.tar.gz** package from the [releases](https://github.com/davidemms/OrthoFinder/releases) page instead and then follow the instructions as before. 

* You can also just use the standard python version, **OrthoFinder_source.tar.gz** from the [releases](https://github.com/davidemms/OrthoFinder/releases) page. This will require a python installation (version 2.7 or 3) together with the numpy and scipy libraries. There are detailed instructions here: <https://github.com/davidemms/OrthoFinder/#python-source-code-version>.


**OrthoFinder help file prints, but it cannot run one of the dependencies:**

* If one of the dependencies (diamond, mcl or fastme) does not work on your machine then you will need to delete the file in the `OrthoFinder/bin` directory and install it yourself. There's guidance on installing the dependencied here: <https://github.com/davidemms/OrthoFinder#installing-dependencies>


**Packaged solutions:**

* **Bioconda:** OrthoFinder is available with bioconda: <https://bioconda.github.io/recipes/orthofinder/README.html>. Thanks to the many people who I'm aware of having contributed to setting this up: Anthony Bretaudeau, Nicola Soranzo, Sacha Laurent, Christian Brueffer, Nathan Weeks, Johannes Köster, pvanheus, Björn Grüning, Emil Hägglund, Andreas Sjödin, Gildas Le Corguillé & Devon Ryan. And thanks also to anyone else who has helped.

* **Docker:** OrthoFinder 2.3.3 is available on [Docker](https://github.com/MrTomRod/Orthofinder-Dockerfile) thanks to Thomas Roder & Monjeaud Cyril. 

**Installing OrthoFinder**
* OrthoFinder doesn't need to be installed, you can just call it from where you downloaded it. If you do want to install it somewhere, you will need to include the config.json file in the directory containing orthofinder.

