# braker-docker
Docker container for running braker gene finder

To use this docker you should

1. checkout this repo:

```
git clone https://github.com/blaxterlab/braker-docker.git
cd braker-docker
```

2. Download your OWN copy of the genemark key which you can get from http://exon.gatech.edu/GeneMark/license_download.cgi (pick the GeneMark-ES / ET v.4.33 LINUX 64 option for this docker) and save the gm_key64.gz file in the braker-docker folder

3. Run docker build:

```
docker build -t braker .
```

4. Go to the folder where you have the aligned.bam and genome.fasta files (or replace `pwd` with the absolute path of that folder) and run braker:

```
docker run --rm \
  -u $UID:$GROUPS \
  -v `pwd`:/data \
  braker \
  braker.pl --species=CPLIC --UTR=on --cores=8 \
  --genome=/data/genome.fasta \
  --bam=/data/aligned.bam
```

