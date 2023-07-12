# dnaSeq4GermlinerMutations 

[![Snakemake](https://img.shields.io/badge/snakemake-≥6.1.0-brightgreen.svg)](https://snakemake.github.io)
[![GitHub actions status](https://github.com/snakemake-workflows/dna-seq-gatk-variant-calling/workflows/Tests/badge.svg?branch=main)](https://github.com/snakemake-workflows/dna-seq-gatk-variant-calling/actions?query=branch%3Amain+workflow%3ATests)

This Snakemake pipeline implements the [GATK best-practices workflow](https://gatk.broadinstitute.org/hc/en-us/articles/360035535932-Germline-short-variant-discovery-SNPs-Indels-) for calling small germline variants.

这个repo fork from [dna-seq-gatk-variant-calling](https://github.com/snakemake-workflows/dna-seq-gatk-variant-calling),我clone下俩并不能直接运行，我在他的基础上做了一些改变，目前可以正常运行。
- 改动1:在线的snakemake-wrappers并不能用，即使设置了翻墙代理还是不能用，这里通过--wrapper-prefix设定本地wrapper
- 改动2：samtools运行过程中需要tmp作为缓存，而缓存一般在/home下面，很多机器这里空间并不是很大。
- 改动3：在获取germline mutations后得到突变后的序列。
  
![pipeline](./dag.svg)

## Usage
```sh
wget  https://github.com/snakemake/snakemake-wrappers/archive/refs/tags/0.59.0.tar.gz
tar -zxvf 0.59.0.tar.gz && mv snakemake-wrappers-0.59.0 0.59.0  && rm  0.59.0.tar.gz
wget https://github.com/snakemake/snakemake-wrappers/archive/refs/tags/0.74.0.tar.gz
tar -zxvf 0.74.0.tar.gz && mv snakemake-wrappers-0.74.0 0.59.0  && rm  0.74.0.tar.gz
snakemake --cores all --use-conda --wrapper-prefix file:///data/wenyuhao/tmp/runWGS/tmp/dna-seq-gatk-variant-calling/
```
