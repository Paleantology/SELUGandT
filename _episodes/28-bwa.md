---
title: Improving assemblies
teaching: 180
exercises: 0
questions:
 - How can we improve on genome assemblies?
---

First: Download the two assemblies. Save them in your clownfish_data/data folder, in a directory called "assembled".

How will you transform this URL: https://figshare.com/s/d183eabb0e149095fb96 into a command that allows you to download the files? Once they download, unzip the files.

In order to use our reads to improve the assembly, we need to know where in the genome our reads map to. To do this, we will use [bwa](https://github.com/lh3/bwa).

First, we index the genome. This step creates a reference index by which reads can be located to specific regions of the genome:

```unix
bwa index data/assembled/Illumina.fasta
```

Secondly, we map the low-error Illumina reads back to the genome. The syntax for doing this looks like this:

```UNIX
 bwa mem assembled/Illumina_assembly.fasta -p raw_data_illumina/SRR6255796.fastq > aln-pe.sam
```
 
 This command accepts a paired-end read in an interleaved file format. But it only takes one! What is a problem with this for us? 
 
## Practical:
 
How will we map all our Illumina reads to our genome? 

Running one genome file takes about ~6 hours for one file of reads. How can we use our qsub file, and options in the bwa software (manual [here](http://bio-bwa.sourceforge.net/bwa.shtml)) to speed up our run? 

Make a copy of the long_clean script. Add your bwa command with your data paths and all the relevant QSUB options. Either show it to me before you leave, or commit and push to github by Thursday. Run it.