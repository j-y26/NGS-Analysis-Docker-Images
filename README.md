# NGS-Analysis-Docker-Images
A repository hosting docker images for NGS analysis

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

Docker images are available at https://hub.docker.com/kirin26/

# Docker Images

- [NGS-Analysis-Docker-Images](#ngs-analysis-docker-images)
- [Docker Images](#docker-images)
  - [rnaseq-cuttag\_r:v1.2](#rnaseq-cuttag_rv12)
    - [Usage](#usage)
  - [rnaseq-cuttag\_linux:v1.2](#rnaseq-cuttag_linuxv12)
    - [Softwares:](#softwares)
    - [Environment:](#environment)
    - [Usage](#usage-1)



## rnaseq-cuttag_r:v1.2

**A docker image for analysis of RNA sequencing data and CUT&Tag data using R.**

![](https://img.shields.io/badge/tag-v1.2-brightgreen)
![](https://img.shields.io/badge/tag-latest-orange)

[Link to Docker Hub](https://hub.docker.com/r/kirin26/rnaseq-cuttag_r)

The image is based on Bioconductoe release 3.16 and contains the following R packages:

**CRAN:**
- RColorBrewer 
- ggplot2 
- devtools 
- rmarkdown 
- httr 
- knitr 
- xaringan 
- bookdown 
- gprofiler2 
- data.table 
- tidyverse 
- dplyr 
- tidyr 
- shiny 
- plotly 
- kableExtra 
- stringr 
- stringi 
- DT 
- reshape2 
- here 
- pheatmap 
- devtools
- cowplot
- ggrepel
- readxl
- stringi
- stringr
- CVXR
- mixtools
- randomForest
- minerva
- igraph

**Bioconductor:**
- GEOQuery 
- DESeq2 
- edgeR 
- limma 
- ComplexHeatmap 
- biomaRt 
- GEOmetadb 
- BiocGenerics 
- Biobase 
- GSEABase 
- GSVA 
- BiocStyle 
- fgsea 
- BiocParallel 
- GSA 
- RCy3 
- seurat
- circlize
- gprofiler2
- viper
- minet

**GitHub:**
- stjude/ChIPseqSpikeInFree

### Usage

```bash
# Navigate to the directory where you would like to store your project

# Pull and run the docker image
docker run -e PASSWORD=changeit -v ${pwd}:/home/rstudio/projects -p 8787:8787 kirin26/rnaseq-cuttag_r:v1.2
```

In your browser, navigate to http://localhost:8787 and log in with username `rstudio` and the password you specified.


---

## rnaseq-cuttag_linux:v1.2

**A docker image for analysis of RNA sequencing data and CUT&Tag data based on command line tools**

![](https://img.shields.io/badge/tag-v1.2-blue)
![](https://img.shields.io/badge/tag-latest-orange)

[Link to Docker Hub](https://hub.docker.com/r/kirin26/rnaseq-cuttag_linux)

The image is based on Ubuntu 22.04 with the following specifications:

### Softwares:

- HTSlib 1.17
- SAMtools 1.17
- BEDtools 2.30.0
- Bowtie2 2.5.1
- STAR 2.7.10b
- FastQC latest
- Subread 2.0.3
- Sambamba 0.8.2
- Fastp 0.23.2
- Trimmomatic 0.39
- Picard 3.0.0
- HOMER 4.11


### Environment:
**Ubuntu 22.04**

**Java**
 - OpenJDK 17

**Python 3**
- numpy (1.24.2)
- pandas (1.5.3)
- scipy (1.10.1)
- matplotlib (3.6.0)
- seaborn (0.12.2)
- scikit-learn (1.2.1)
- statsmodels (0.13.5)
- pysam (0.20.0)
- pyBigWig (0.3.18)
- pyfaidx (0.7.2.1)
- pyyaml (6.0)
- py2bit (0.3.0)
- cython


### Usage

```bash
# Navigate to the directory where you would like to store your project

# Pull and run the docker image
docker run -it -v ${pwd}:/home kirin26/rnaseq-cuttag_linux:v1.2

# Exit the linux container
exit

# Restart the linux container
docker start -i <container_id>
docker attach <container_id>
```
