---
title: "Bio282Hmwk3 Analysis Proposal"
author: "Newton Z. Hood"
date: "10/30/2020"
output: html_document
---
Having a working assembly for _Xiphister mucosus_ would allow for comparative analyses between _X. mucosus_ and other members within the Stichaedae family. The Stichaedae family contains species with varying dietary needs, assembling the _X. mucosus_ genome would allow for closer examination of regions that govern digestive enzymne production and metabolism across various Stichaedae lineages. This would add an extra layer to data collected from the enzymatic assays done previously on _X. mucosus_. Hopefully, we will eventually be able to map the sequence changes on a phylogenetic map in order to see what variations lie within the family.   

I am proposing assembling a genome for _Xiphister mucosus_ by merging Pacific Biocience long-read datasets with Illumina short-read datasets. The _X. mucosus_ was collected in Washington state and the DNA was extracted by Dr. Joseph Herras, and the sample was sent to Pacific Bio for sequencing. The sequence data was then stored on the synology for future analyses. I believe that the program miniasm would be the best tool for assembing the _X. mucosus_ genome. miniasm is a free command-line based software that is used for assembling  long read sequence data, and the software is already downloaded on the HPC. miniasm is unique in that it does not go through a consensus step. I will use fastqc in order to check the quality of the sequences, generate cumulative distribution plots, and then align them using the software Jalview. Jalview allows for the identification of regions of conservation and generating consensus sequences. 

Assembling the _X. mucosus_ genome will further help evaluate how the feeding ecology and physiology of the Stichaedae family once compared to the genomes of other Stichaedae through the comparison of the expression of their digestive enzymes.I plan on using the annotated genomes of other Stichaedae to locate the sequences for trypsin and pepsin production. This will offer interesting insight into the evolution of diet choice and ontogenetic dietary shifts. 

