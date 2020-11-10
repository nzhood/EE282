
# Q1


### Acquiring data

``wget ftp://ftp.flybase.net/genomes/Drosophila_melanogaster/dmel_r6.36_FB2020_05/fasta/dmel-all-chromosome-r6.36.fasta.gz``

### File intengrity

``(ee282) [nzhood@hpc3-19-00:~] $cksum dmel-all-chromosome-r6.36.fasta.gz``

### Genome Summarry: 

``(ee282) [nzhood@hpc3-19-00:~] $faSize dmel-all-chromosome-r6.36.fasta.gz
    1. Total number of nucleotides = 143726002
    2. Total number of N's = 1152978
    3. Total number of sequences = 1870``


### Pipeline:

``gawk ' { print $3 } ' <(zcat del-all-r6.36.gtf.gz) | sort | uniq -c | sort -r -n | head``

### Total number of features of each type, sorted from the most common to the least common:

``189268 exon
 162578 CDS
  46664 5UTR
  33629 3UTR
  30812 start_codon
  30754 stop_codon
  30728 mRNA
  17875 gene
   3047 ncRNA
    485 miRNA
    366 pseudogene
    312 tRNA
    300 snoRNA
    262 pre_miRNA
    115 rRNA
     32 snRNA``


# Q2


### Acquiring data: 

``(ee282) [nzhood@hpc3-19-00:~] $wget ftp://ftp.flybase.net/genomes/dmel/dmel_r6.36_FB2020_05/gtf/md5sum.txt``

``(ee282) [nzhood@hpc3-19-00:~]$ wget ftp://ftp.flybase.net/genomes/dmel/dmel_r6.36_FB2020_05/gtf/dmel-all-r6.36.gtf.gz``

### File integrity: 

``(ee282) [nzhood@hpc3-19-00:~] $cksum dmel-all-r6.36.gtf.gz``

### Unzipping the file: 

``(ee282) [nzhood@hpc3-19-00:~] $gunzip dmel-all-r6.36.gtf.gz``



## Total number of genes per chromosome arm (X, Y, 2L, 3L, 3R, 4):

### Selecting only for genes: 

``(ee282) [nzhood@hpc3-19-00:~] $ gawk -F '\t' '$3 == "gene" {print $1}' dmel-all-r6.36.gtf > genes.txt``

### Sorting:

``(ee282) [nzhood@hpc3-19-00:~] $ sort genes.txt > sgenes.txt``

### Getting counts of each type: 

``(ee282) [nzhood@hpc3-19-00:~] $ uniq -c sgenes.txt > unq.sgenes.txt``

### Grabbing the data with grep:

``(ee282) [nzhood@hpc3-19-00:~] $ grep -P '\b(X|Y|(2L)|(2R)|(3L)|(3R)|4)\b' unq.sgenes.txt | head``
 
  `` 3516 2L
   3653 2R
   3486 3L
   4225 3R
    114 4
   2691 X
    113 Y``

### Pipeline:

``gawk -F '\t' '$3 == "gene" {print $1}' dmel-all-r6.36.gtf | sort | uniq -c | grep -P '\b(X|Y|(2L)|(2R)|(3L)|(3R)|4)\b' unq.sgenes.txt | head``

