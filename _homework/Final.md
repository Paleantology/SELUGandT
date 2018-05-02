---
title: Computational Practical Final
teaching: 180
exercises: 0
questions:
- "How can we compute a partitioned topology on LONI?"
---


### Stage One: Data management (10 pts)

1. Initiailize a new Git repo for your final project.
2. Populate it with the normal directories we put in these directories. Add the hybrid assembly file, and the Illumina reads (concatenated fastq is fine). _Do not commit genomic files to git, unless told to._
3. Each of the below segments asks for specific files to be committed. Do not do one commit of the whole group. Commit each file as noted.

### Stage Two: Mapping reads to the assembly (10 pts)

1. Install: [minimap](https://github.com/lh3/minimap2#install) in your work directory. Minimap is bwa for long-read assemblies.
2. Create a script to run minimap. It must:
	+ Run on a workq node
	+ Have a walltime limit of six hours
	+ Produce an output file called minimap.out
3. Run minimap. The command is as follows:

```unix
/work/UserName/minimap2-2.10_x64-linux/minimap2 -ax sr -t 20 Path/To/Hybrid_assembly.fasta Path/to/IlluminaReads > aln.sam
```

This will take walltime=05:47:10 or so.

4. Commit the minimap script and the minimap.out file.

### Stage Three: Sam to Bam Conversion

1. Convert the sam file to bam using samtools view. Sort with sambamba sort, and index with samtools index
2. These steps should be performed on the workq
3.  Commit your script, and the sam.out file

walltime=00:59:09

### Stage Four: Improving the assembly 

1. Create a pilon script to run on the indexed bam file, using the hybrid assembly as the reference.
2. 	Decide if you would like to run pilon on the default settings, or if there are specific improvements you'd like to try (Note: there is no right answer)
3. Briefly justify the choice you made in (2). 
4. Run pilon on a bigmem node. Request 24 cores.
5. Add and commit the run script and the .out file.

Walltime: 02:40:38

### Stage Five: Quantifying assembly metrics

1. Create a BUSCO script for each assembly, the raw Hybrid_assembly and the one improved by Pilon. 
2. Run busco. Workq will be fine.
3. Have a look at the metrics - were you able to recover any more complete genes? Did improving the assembly with Pilon make a difference?
4. Add and commit the BUSCO scripts, and the summary gene table of each. 

wall_hours=2.90 per run

### Have it done May 11th. Add and commit it, and email me a link.