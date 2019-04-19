# Alternative to Make - Snakemake

Make is an old (1976) which was originally developed for compiling and building executable programs from source code. There are newer packages which are targeted at the need to run consistent, reproducible experiments which are more appropriate in most of our situations where we need to run a pipeline of jobs.

There are many alternatives to Make for workflow management, a discussion of them can be seen here:
   https://www.biostars.org/p/91301/

We will give a brief overview of Snakemake, a 'workflow management system is a tool to create reproducible and scalable data analyses'. You can find more information on it here:
    https://snakemake.readthedocs.io/en/stable/

Snakemake's advantages over Make are summarized below:
   1. It's python3-based, rather than shell-based. Snakemake rules can be written in python or shell commands. Its rules can access python variables and datastructures. Those variables and datastructures can be initialized before the rules are run using ordinary python code. Make has an old, obtuse syntax (eg. .PHONY $< -o $@ WTF!!) that is an impediment to quickly creating workable workflows. In fact, Make is so old, obtuse and functionality-poor that other tools (automake, cmake, configure etc) are often used to create the actual Make files.
   2. Snakemake is specifically designed for reproduciable workflows and has many features for this purpose that are not available in Make. Using Make for workflow management is repurposing a build tool, the results will not be as good, elegant, reliable, flexible or extendible.
   2. The variables that defines an instantiation of a particular workflow can be kept separately in a YAML or JSON file from the rules that make up the workflow which are in the Snakefile. The workflow can then be used on different datasets by changing the variables while keeping the rules untouched. These variables are available to the rules as Python variables or lists. This can be done with Make but the framework is less clear; a separate Makefile is intended to be included with each project.
  3. Snakemake workflows can be easily executed on workstations, clusters, the grid, and in the cloud without modification. The job scheduling can be constrained by arbitrary resources like e.g. available CPU cores, memory or GPUs. This is important when your experiments have to run on your own laptop, then transferred to Azure, or one of the academic clusters (Cirrus, Archer, CSD3 etc). Each will have their own method to schedule jobs on their cluster nodes. Make is designed for single machine usage. Creating cluster-aware Make-rules is complicated and error-prone.
  4. Snakemake is currently being developed and extended. There is a thriving community of developers and users who are willing to help you. Two good forums for Snakemake are:
      https://bitbucket.org/snakemake/snakemake/issues
      https://www.google.com/search?client=ubuntu&channel=fs&q=snakemake+forum&ie=utf-8&oe=utf-8
  I (Hieu Hoang) can personally attest to this. In comparison, the last Make release on the latest Ubuntu is from 2014, the community is dispersed.

The Machine Translation Group at the University of Edinburgh has experience with complex pipelines, we've even written our own workflow system a long time ago (https://ufal.mff.cuni.cz/pbml/94/art-koehn-ems.pdf)! We have been using Snakemake to crawl and process approx. 300,000 websites to create multi-lingual corpora where a reliable and scalable workflow system is a necessity. We had assessed the merits of a few packages, including Make, and found merits and downsides to many of them. In our view, Snakemake is overall the clear choice.
