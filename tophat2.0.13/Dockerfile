#################################################################
# Dockerfile to build TopHat 2.0.13 with Bowtie 2.2.3 container 
# images
# Based on Ubuntu:20.04
##################################################################
# set the base image to Ubuntu:20.04
FROM ubuntu:20.04
# File/Author/Maintainer shengyiyan <shengyiyanwork@gmail.com>
# Update the repository sources list, install wget, unzip, python
RUN apt-get update && apt-get install --yes wget unzip python
# change working dir
WORKDIR /bin
# download TopHat2 and bowtie2
RUN wget http://ccb.jhu.edu/software/tophat/downloads/tophat-2.0.13.Linux_x86_64.tar.gz \
    && wget --default-page=bowtie2-2.2.3-linux-x86_64.zip http://sourceforge.net/projects/bowtie-bio/files/bowtie2/2.2.3/bowtie2-2.2.3-linux-x86_64.zip/ \
# Unzip the archive
    && tar zxvf tophat-2.0.13.Linux_x86_64.tar.gz \
    && unzip bowtie2-2.2.3-linux-x86_64.zip \
# Remove the archive
    && rm tophat-2.0.13.Linux_x86_64.tar.gz bowtie2-2.2.3-linux-x86_64.zip
# change working dir
WORKDIR /bin/bowtie2-2.2.3
# build a Symbolic link from "bowtie" to "bowtie2"
RUN ln -s bowtie2 bowtie \
# remove wget unzip
    && apt-get purge --yes wget unzip
# set env in PATH
ENV PATH $PATH:/bin/tophat-2.0.13.Linux_x86_64:/bin/bowtie2-2.2.3
# set final working dir
WORKDIR /app