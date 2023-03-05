FROM ubuntu:22.04
LABEL maintainer="Jielin Yang"
LABEL email="jielin.yang@mail.utoronto.ca"
LABEL version="1.1"
LABEL description="Docker image for RNAseq and CUT&Tag analysis on Linux"

# Install Java JDK 17
RUN apt-get update -y && apt-get install -y openjdk-17-jdk

# Initialize command line interface
RUN apt-get update -y && apt-get install -y \
    build-essential \
    bzip2 \
    cmake \
    default-jdk \
    git \
    libnss-sss \
    libtbb2 \
    libtbb-dev \
    ncurses-dev \
    nodejs \
    python-pip \
    unzip \
    wget \
    zlib1g \
    zlib1g-dev \
    libbz2-dev \
    libncurses5-dev \
    libncursesw5-dev \
    liblzma-dev \
    libcurl4-openssl-dev \
    libssl-dev \
    libxml2-dev \
    libcairo2-dev \
    libxt-dev \
    libglpk-dev \
    libglpk40 \
    libglu1-mesa-dev \
    unzip \
    gzip \
    tmux

# Install python
RUN apt-get install -y python3 python-is-python3 python3-dev python3-pip python3-setuptools python3-wheel

# Install python packages
RUN pip3 install --upgrade pip
RUN pip3 install numpy==1.24.2
RUN pip3 install pandas==1.5.3
RUN pip3 install scipy==1.10.1
RUN pip3 install matplotlib==3.6.0
RUN pip3 install seaborn==0.12.2
RUN pip3 install scikit-learn==1.2.1
RUN pip3 install statsmodels==0.13.5
RUN pip3 install pysam==0.20.0
RUN pip3 install pyBigWig==0.3.18
RUN pip3 install pyfaidx==0.7.2.1
RUN pip3 install pyyaml==6.0
RUN pip3 install py2bit==0.3.0
RUN pip3 install cython


#######################
# HTSlib 1.17
#######################
RUN mkdir -p /opt/htslib-1.17
ENV HTSLIB_DIR=/opt/htslib-1.17

WORKDIR /tmp
RUN wget https://github.com/samtools/htslib/releases/download/1.17/htslib-1.17.tar.bz2 -O htslib-1.17.tar.bz2 \
    && tar -xjf htslib-1.17.tar.bz2 \
    && cd /tmp/htslib-1.17 \
    && ./configure --prefix=$HTSLIB_DIR \
    && make \
    && make install \
    && cd .. \
    && rm -rf htslib-1.17 htslib-1.17.tar.bz2

#######################
# SAMtools 1.17
#######################
RUN mkdir -p /opt/samtools-1.17
ENV SAMTOOLS_DIR=/opt/samtools-1.17

WORKDIR /tmp
RUN wget https://sourceforge.net/projects/samtools/files/samtools/1.17/samtools-1.17.tar.bz2/download -O samtools-1.17.tar.bz2 \
    && tar -xjf samtools-1.17.tar.bz2 \
    && cd /tmp/samtools-1.17 \
    && ./configure --prefix=$SAMTOOLS_DIR --with-htslib=$HTSLIB_DIR \
    && make \
    && make install \
    && cd .. \
    && rm -rf samtools-1.17 samtools-1.17.tar.bz2

#######################
# BEDtools 2.30.0
#######################
WORKDIR /tmp
RUN wget https://github.com/arq5x/bedtools2/releases/download/v2.30.0/bedtools-2.30.0.tar.gz \
    && tar -zxvf bedtools-2.30.0.tar.gz \
    && cd /tmp/bedtools2 \
    && make \
    && cd .. \
    && mv bedtools2 /opt \
    && rm bedtools-2.30.0.tar.gz

#######################
# Bowtie2 2.5.1
#######################
WORKDIR /tmp
RUN wget https://sourceforge.net/projects/bowtie-bio/files/bowtie2/2.5.1/bowtie2-2.5.1-source.zip/download -O bowtie2-2.5.1-source.zip \
    && unzip bowtie2-2.5.1-source.zip \
    && cd /tmp/bowtie2-2.5.1 \
    && make \
    && cd .. \
    && mv bowtie2-2.5.1 /opt \
    && rm bowtie2-2.5.1-source.zip

#######################
# STAR 2.7.10b
#######################
WORKDIR /tmp
RUN wget https://github.com/alexdobin/STAR/archive/2.7.10b.tar.gz -O STAR-2.7.10b.tar.gz \
    && tar -xzf STAR-2.7.10b.tar.gz \
    && cd /tmp/STAR-2.7.10b/source \
    && make STAR \
    && cd ../.. \
    && mv STAR-2.7.10b /opt \
    && rm STAR-2.7.10b.tar.gz

#######################
# FastQC Latest
#######################
RUN apt-get install -y fastqc

#######################
# Subread 2.0.3
#######################
WORKDIR /tmp
RUN wget https://sourceforge.net/projects/subread/files/subread-2.0.3/subread-2.0.3-Linux-x86_64.tar.gz/download -O subread-2.0.3-Linux-x86_64.tar.gz \
    && tar -xzf subread-2.0.3-Linux-x86_64.tar.gz \
    && mv subread-2.0.3-Linux-x86_64 /opt \
    && rm subread-2.0.3-Linux-x86_64.tar.gz

#######################
# Sambamba 0.8.2
#######################
WORKDIR /tmp
RUN wget https://github.com/biod/sambamba/releases/download/v0.8.2/sambamba-0.8.2-linux-amd64-static.gz -O sambamba-0.8.2.gz \
    && gunzip sambamba-0.8.2.gz \
    && mv sambamba-0.8.2 /opt \
    && chmod +x /opt/sambamba-0.8.2 \
    && export PATH=/opt:$PATH

#######################
# Fastp 0.23.2
#######################
WORKDIR /tmp
RUN wget http://opengene.org/fastp/fastp \
    && mv fastp /opt \
    && chmod +x /opt/fastp \
    && export PATH=/opt:$PATH

#######################
# Trimmomatic 0.39
#######################
WORKDIR /tmp
RUN wget http://www.usadellab.org/cms/uploads/supplementary/Trimmomatic/Trimmomatic-0.39.zip \
    && unzip Trimmomatic-0.39.zip \
    && mv Trimmomatic-0.39 /opt \
    && rm Trimmomatic-0.39.zip

#######################
# Picard 3.0.0
#######################
WORKDIR /tmp
RUN wget https://github.com/broadinstitute/picard/releases/download/3.0.0/picard.jar \
    && mv picard.jar /opt

#######################
# Deeptools 3.5.1
#######################
RUN pip3 install deeptools==3.5.1

#######################
# MACS3 3.0.0
#######################
RUN pip3 install macs3


# Create .bash_profile and add the first line
RUN echo ". ~/.profile" >> /root/.bash_profile

# Add the rest of the lines to set PATH
RUN echo "export PATH=/opt/stringtie-2.2.1:/opt/samtools-1.17/bin: \
    /opt/htslib-1.17/bin:/opt/bedtools2/bin:/opt/bowtie2-2.5.1: \
    /opt/STAR-2.7.10b/source:/opt/subread-2.0.3-Linux-x86_64/bin:/opt:$PATH" >> /root/.bash_profile

# Setting the shell prompt to $
RUN echo "export PS1='\$ '" >> /root/.bash_profile

# Clean up
RUN apt-get clean \
    && rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/* \
    && apt-get autoremove -y \
    && apt-get autoclean -y