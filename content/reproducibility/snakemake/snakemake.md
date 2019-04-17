# Alternative to Make - Snakemake

Make is an old (1976) which was originally developed for compiling and building executable programs from source code. There are newer packages which are targeted at the need to run consistent, reproducible experiments which are more appropriate in most of our situations where we need to run a pipeline of jobs.

There are many alternatives to Make, a discussion of them can be seen here:
   https://www.biostars.org/p/91301/

We will give a brief overview of Snakemake, a 'workflow management system is a tool to create reproducible and scalable data analyses'. You can find more information on it here:
    https://snakemake.readthedocs.io/en/stable/

Snakemake's advantages over Make are summarized below:
   1. It's python3-based, rather than shell-based. Make has an old, obtuse syntax (eg. $< -o $@ WTF!!) that is a barrier to creating a realistic-size workflow quickly. Snakemake rules can be written in python or shell commands. Its rules can access python variables and datastructures. Those variables and datastructures can be initialized before the rules are run using ordinary python code.
   2. Snakemake is specifically designed for reproduciable workflows and has many features for this purpose that are not available in Make. Using Make for workflow management is repurposing a build tool, the results will not be as good or as elegant.
   2. The variables that defines an instantiation of a particular workflow can be kept separately from the definition of the workflow in a YAML or JSON file. These variables are available to the rules was variables or lists. This can be done with Make but the framework is less clear; custom Makefiles are designed to be included with every project.
  3. Snakemake workflows can be easily executed on workstations, clusters, the grid, and in the cloud without modification. The job scheduling can be constrained by arbitrary resources like e.g. available CPU cores, memory or GPUs. Make is designed for single machine usage. Creating cluster-aware Make-rules is complicated and error-prone.
  4. Snakemake is currently being developed and extended. There is a thriving community of developers and users who are willing to help you. Two good forums for Snakemake are:
      https://bitbucket.org/snakemake/snakemake/issues
      https://www.google.com/search?client=ubuntu&channel=fs&q=snakemake+forum&ie=utf-8&oe=utf-8
  I (Hieu Hoang) can personally attest to this. In comparison, the last Make release is from 2014, the community is dispersed.

The machine translation group at the University of Edinburgh have been using it to crawl and processing approx. 300,000 website to create a multi-lingual corpora so we have experience with its reliability and scalability. We had assessed the merits of a few workflow packages, including Make, before the project and found merits and downsides to many of them. In our view, Snakemake is overall the clear choice for researchers creating consistent, reproducible workflows.
