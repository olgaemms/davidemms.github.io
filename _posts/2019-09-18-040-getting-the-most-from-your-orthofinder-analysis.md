---
layout: post
title: "4. Getting the most from your OrthoFinder analysis"
author: "David Emms"
categories: orthofinder_tutorials
tags: [documentation]
post_type: getting_started
---

## Selecting which species to include
The first question to ask yourself is what species should you include. The answer to this probably depends on what kind of analysis you want to perform. Three standard analyses are: 

* Performing a comparative analysis across a clade of species
* Identifying orthologs between a pair, or among a small number, of species
* Investigating changes at a particular point in evolutionary history

In the first case just get the proteomes for all the species in your clade that you can. Generally, you don't need to include an outgroup for your clade of interest--in fact, this will push back the point in evolutionary history at which your orthogroups are defined (<a href="https://github.com/davidemms/OrthoFinder#orthogroups-orthologs--paralogs">Orthogroups, Orthologs & Paralogs</a>) and so it's usually better not to since your orthogroups will have lower resolution.

In the second case, it is good to ensure you have sufficient species sampling so as to get the best results. The same rule applies as for inferring a good phylogenetic tree: you should break up long branches with intermediate species. You want an absolute minimum of 4 species and somewhere between 6-10 is probably optimal. 

If you're interested in what happened on a particular branch of the species tree, then you should likewise ensure good species sampling&mdash;ideally at least two species below the branch, at least two species on the closest branch above and two or more species in the outgroup.

### Transcriptomes & low quality genomes
In general it is good to use the best annotated genomes available, but OrthoFinder is pretty robust to missing genes so this is not a big concern. One problem that can arise with transcriptomes is when you start with ~100,000 transcripts per species. This can be computationally expensive and will likely result in a very large number of files being generated, so be careful in such cases.

### Which proteome version to use
OrthoFinder uses the amino acid sequences for the protein coding genes. This is generally in a folder for the species called "annotation". The ideal is to use a single primary/longest transcript variant for each gene. This will also reduce the runtime considerably. Often the files are gzipped (end in .gz) and so need to be extracted first (e.g. with the command: `gunzip Danio_rerio.GRCz11.pep.all.fa.gz`)  

* **Ensembl: <http://ensembl.org>**: Use the **.pep.all.fa** file rather than the .pep.abinitio.fa, since, as I understand it, these are the better supported gene models (someone please correct me if I'm wrong here). Usually these don't have just one representative transcript per gene, but I've written a script that comes with OrthoFinder to extract the longest transcript variant per gene, I'd definitely recommend using it. Note, there are also sub-sites on Ensmbl for downloading genomes: http://bacteria.ensembl.org, http://protists.ensembl.org, http://fungi.ensembl.org, http://metazoa.ensembl.org
* **Phytozome: <https://phytozome.jgi.doe.gov>**: Use the **.protein_primaryTranscriptOnly.fa** file.
<!--- * **NCBI: ftp://ftp.ncbi.nih.gov/genomes/**--->
<!--- * And many other sources--->

## Pre-processing of input proteomes
This is not required, but can help by making your results files tidier and considerably smaller.

### Species names
OrthoFinder will use each proteome filename as the name for that species. One place these are used is in the gene tree, where each gene name is prefixed by its species name. This helps greatly with interpretation of any gene trees you need to look at, as it becomes immediately apparent if a node is a duplication or a speciation event. It also lets you see if the genes in the gene tree are related in the way you would expect them to be given your knowledge of the species tree. 

For this reason, use a concise naming style for your files. For example, when I run OrthoFinder on plant genomes from Phytozome I'll give the files names like "A_thaliana.fa" and "O_sativa.fa". In general, use whatever names are familiar to you.

### Gene names 
OrthoFinder will try and find a set of short, unique gene names to reference each sequence, by testing if the first (space-delimited) word on each accession line is unique. If they are, then genes will be identified by these names. Otherwise, the complete accession lines will be used to refer to each gene. Because of the quadratic nature of orthology (one orthologs result file per species pair), each gene name will get written out O(n) times, so for large analyses getting your accession lines tidy will result in a considerable saving in terms of disk space and also the time taken by OrthoFinder to write out all the ortholog results files!

If you've used the script above for Ensembl proteomes then the files will have already been correctly interpreted so that they are in a suitable format, with a single gene identifier for each sequence. 

<!--- ## Running OrthoFinder with a corrected species tree.--->