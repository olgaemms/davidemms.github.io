---
layout: post
title: "A2. Getting OrthoFinder input data"
author: "David Emms"
categories: orthofinder_tutorials
tags: [documentation]
post_type: supplementary
---

Proteomes may be available in a number of places. The ([Running an example OrthoFinder analysis]({% post_url 2019-09-19-running-an-example-orthofinder-analysis %})) showed how to download data from Ensembl, here are a few pointers for other popular websites.

## Phytozome
1. You'll first need to create an account and log in.

2. Go to the download section:
 <img src="{{ site.github.url }}/assets/img/Phytozome.png">

3. Select the **_primaryTranscriptOnly.fa.gz** files for each species you want.
<img src="{{ site.github.url }}/assets/img/Phytozome_download.png">

4. Go to the top of the page, and click "Download Selected Files". They'll be in a package with the original directory structure so you'll have to get each of the files, put them in a single file and gunzip them. You don't need to run the `primary_transcript.py` script on them as Phytozome has already done that step.

## Others?
Let me know if you think pointers to any other sites would be helpful.