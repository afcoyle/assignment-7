# Analyzing RNA-Seq Data with DESeq2

### Aidan Coyle

### 03-02-2021

### HW 7, FISH 497

## Location and Installation: 

DESeq2 is hosted on Bioconductor, which provides open-source tools for analysis of bioinformatics data. To install DESeq2, you must first install the BiocManager package with `install.packages("BiocManager")`. Once BiocManager is installed, you can install DESeq2 with `BiocManager::install("DESeq2")`.

## Vignettes:

At the time of writing, there is one vignette available for DESeq2. It demonstrates the workflow for analyzing RNA-seq data. The vignette can be seen with `browseVignettes("DESeq2")`.

## Application:

[Here is a good breakdown of how to format inputs for DESeq2 and some ways to interpret results!](https://rstudio-pubs-static.s3.amazonaws.com/329027_593046fb6d7a427da6b2c538caf601e1.html)

## Review:

DESeq2 is an R package used to conduct analyses of RNA-seq data, thus providing the statistical significance of any observed differences in gene expression

As input, you provide a table containing all contigs and their counts for each sample, with each sample as a different column. This means that prior to DESeq2, you must quantify your RNA-seq data. This can either be done by a variety of tools, including [Bowtie2](http://bowtie-bio.sourceforge.net/bowtie2/index.shtml) or [kallisto](https://www.nature.com/articles/nbt.3519). You also must provide a dataframe mapping each sample (e.g. each column) to your experimental conditions. Of course, replication in experimental conditions is necessary for DESeq2 to be able to draw any statistical comparisons.

DESeq2 can provide a large number of formats - PCA plots, MA plots, tables of contigs with p-values and adjusted p-values for differential expression, dispersion estimates, tables of differentially-expressed contigs, and more!

As a warning to new users, the runtime for the `DESeq()` function can be quite long - on a laptop, it may be several hours until the function has finished running. If you have hundreds of samples, the runtime may be far, far longer. In that case, it may be optimal to switch to [limma-voom](https://ucdavis-bioinformatics-training.github.io/2018-June-RNA-Seq-Workshop/thursday/DE.html), which utilizes the voom package

Overall, DESeq2 is quite an impressive package. It is powerful, can be easily streamlined, and is excellent at what it does. However, it does have some downsides. One of the biggest issues is that it isn't optimized for user-friendliness. To some degree, this makes sense. DESeq2 is an extremely specific package, with no uses beyond analyzing RNA-seq data. This means that generally, potential users will already have a general idea of what your potential inputs should be and how to generate them. However, the vignette is precisely detailed to an overwhelming degree, which can cause less-knowledgeable users to easily become lost in the details. This could be remedied by providing a tutorial for new users with some example data and a single workflow.


There are several alternatives to DESeq2, most notably the package edgeR (also a Bioconductor package). Both are roughly equivalent in precision and use roughly the same process to determine differential expression. If you are deciding between the two, I suggest using whichever package is most often used by members of your lab in order to maximize help if you run into issues! If you're still having trouble deciding, [I suggest consulting this article!](https://mikelove.wordpress.com/2016/09/28/deseq2-or-edger/)
