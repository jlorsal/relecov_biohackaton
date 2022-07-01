<a name="home"></a>
  
## I Relecov Biohackathon
## Group 4
Participants: Joan Gibert Fernández, Joan R. Grande, José Miguel Lorenzo Salazar, Sarai Varona Fernández.

## Tasks

<ul>
  <li><a href="#BibliographySeeking">Task 1. Bibliography seeking.</a></li>
  <li><a href="#IonTorrentData">Task 2. Provide Ion Torrent data set.</a></li>
  <li><a href="#SoftwareImplementation">Task 3. Software implementation: preprocessing, mapping and variant calling.</a></li>
</ul>

## Hackathon in detail
<ul>
  <li><a href="#Day1">Day 1 (June 29, 2022)</a></i>
  <li><a href="#Day2">Day 2 (June 30, 2022</a></i>
  <li><a href="#Day3">Day 3 (July 1, 2022)</a></i>
</ul>

---

<a name="Day1"></a>
### Day 1

<!-- ************************** SECTION HERE -->

Helps
- [MarkDown cheatsheet](https://www.markdownguide.org/cheat-sheet/)
- [NF code of ViralRecon](https://github.com/jlorsal/viralrecon)

---

<a name="BibliographySeeking"></a>
### Task 1: Bibliography Seeking

- **SARS-CoV-2 RECoVERY: a multi-platform open-source bioinformatic pipeline for the automatic construction and 
analysis of SARS-CoV-2 genomes from NGS sequencing data**. 

Sabato, L. D. et al. (2021).

[DOI](https://doi.org/10.1101/2021.01.16.425365)

[bioRxiv](https://www.biorxiv.org/content/10.1101/2021.01.16.425365v1)

Available at Galaxy: [](https://https//aries.iss.it)

[Github](https://github.com/aknijn/sars-cov-2-recovery)

[Flowchart](https://github.com/aknijn/sars-cov-2-recovery/blob/main/sars-cov-2-recovery.png)

<img src="../group4/images/sars-cov-2-recovery.png" />

---

- **A Novel SARS-CoV-2 Viral Sequence Bioinformatic Pipeline Has Found Genetic Evidence That the Viral 3′ Untranslated Region (UTR) Is Evolving and Generating Increased Viral Diversity**

Carlos Farkas et al. (2021).

[DOI](https://doi.org/10.3389/fmicb.2021.665041)

[Journal](https://www.frontiersin.org/articles/10.3389/fmicb.2021.665041/full)

[GitHub]( https://github.com/cfarkas/SARS-CoV-2-freebayes)

[Galaxy Project](https://usegalaxy.org/u/carlosfarkas/h/snpeffsars-cov-2)

---

- **ASPICov: An automated pipeline for identification of SARS-Cov2 nucleotidic variants**

Valentin Tilloy et al. 

[DOI](https://doi.org/10.1371/journal.pone.0262953)

[Journal](https://journals.plos.org/plosone/article?id=10.1371/journal.pone.0262953)

[Workflow](https://journals.plos.org/plosone/article/figure/image?size=large&id=10.1371/journal.pone.0262953.g001)

[GitLab](https://gitlab.com/vtilloy/aspicov)

Singularity images

<img src="../group4/images/journal.pone.0262953.g001.PNG" width="75%" />

---

- **Ion torrent-based nasopharyngeal swab metatranscriptomics in COVID-19**

Gubio S. Campos et al. (2020).

[DOI](https://doi.org/10.1016/j.jviromet.2020.113888)

[Journal]https://www.sciencedirect.com/science/article/pii/S0166093420301403)

Workflow:

<img src="../group4/images/1-s2.0-S0166093420301403-gr1_lrg.jpg" />

---

- **Comparison of Illumina MiSeq and the Ion Torrent PGM and S5 platforms for whole-genome sequencing of picornaviruses and caliciviruses**

Rachel L. Marine et atl. (2020).

[DOI](https://doi.org/10.1016/j.jviromet.2020.113865)

[Journal](https://www.sciencedirect.com/science/article/pii/S0166093420301178)

---

- **SARS-CoV-2 Whole-Genome Sequencing by Ion S5 Technology—Challenges, Protocol Optimization and Success Rates for Different Strains**

Maria Szargut et al. (2022).

[DOI](https://doi.org/10.3390%2Fv14061230)

[Journal](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC9227152/)

  <p align="right" dir="auto">
   <a href="#home" title="Up">
    <img src="../group4/images/home-icon.png" style="max-width: 100%;">
   </a>
 </p>
  

---
  
<!-- ************************** SECTION HERE -->

<a name="IonTorrentData"></a>
### Task 2: Ion Torrent dataset

- Use FASTQ files from IonTorrent sequencing technology (PGM and/or S5) from the HERA project as benchmarking to test Viral-Recon. We have access to FASTQ files for ten known samples provided by BU-ISCIII. We want to test:
  <ol>
    <li>The raw FASTQ files into Viral-Recon.</li>
    <li>The uBam files (some sort of raw FASTQ format file from IonTorrent).</li>
    <li>The FASTQ files with some preprocessing filtering (BQ>20).</li>
  </ol>
- Test directly with the FASTQ files provided (if any) into Viral-Recon.
- Set a BaseQuality filter (?) and other possible filters (depending on the noise within the input reads, specially in indels) in the config of Viral-Recon.
- Sarai and Joan provided examples of FASTQ obtained with IonTorrent technologies.

  <p align="right" dir="auto">
   <a href="#home" title="Up">
    <img src="../group4/images/home-icon.png" style="max-width: 100%;">
   </a>
 </p>
  
  
---

<!-- ************************** SECTION HERE -->
 
<a name="SoftwareImplementation"></a>
### Task 3: Software Implementation

- Check if a UBam-to-FASTQ is needed depending on the IonTorrent datasets provided.
- Several outputs are expected: FASTQ (if the user knows how to download files in this format from the sequencing platform), uBAM and BAM.
- We will need to test TMAP and IRMA.

**Tools to preprocess the Ion Torrent FASTQ files in case they are provided as BAM or uBAM**

**How to perform BAM-to-FASTQ**

> [Samtools: bam2fq](http://www.htslib.org/doc/1.1/samtools.html)

```Bash
inBAM="unsorted.bam"
outBAM="sorted.bam"

# Sort paired-end read alignment in BAM file (sort by name -n)
samtools sort -n ${inBAM} -o ${outBAM}

# Convert BAM to single FASTQ
BAM="sorted.bam"
FASTQ="output.fastq"
samtools bam2fq ${BAM} > ${FASTQ}

# Convert BAM into separate R1 and R2 FASTQ files
BAM="sorted.bam"
FASTQ1="sample_R1.fastq"
FASTQ2="sample_R2.fastq"
samtools fastq -@ 8 ${BAM} \
    -1 ${FASTQ1} \
    -2 ${FASTQ2} \
    -0 /dev/null -s /dev/null -n
```

> [BEDtools: bamtofastq](https://bedtools.readthedocs.io/en/latest/content/tools/bamtofastq.html)

```Bash
BAM="input.bam"
FASTQ1="forward.fastq"
FASTQ2="reverse.fastq"
bedtools bamtofastq -i ${BAM} -fq ${FASTQ1} -fq2 ${FASTQ2}
```

> [PICARD](http://broadinstitute.github.io/picard/command-line-overview.html#SamToFastq)
```Bash
BAM="input.bam"
FASTQ1="forward.fastq"
FASTQ2="reverse.fastq"
java -Xmx2g -jar Picard-SamToFastq.jar \
    I=${BAM} \
    F=${FASTQ1} \
    F2=${FASTQ2}

#Note, F2 to get paired-end fastq files (R1 and R2)
```

> [bamtools](https://github.com/pezmaster31/bamtools)

```Bash
BAM="input.bam"
FASTQ="output.fastq"
bamtools convert -in ${BAM} --format fastq > ${FASTQ}

# Split an interleaved FASTQ extracting reads ending with '/1' or '/2'
FASTQ="interleaved.fastq"
FASTQ1="forward.fastq"
FASTQ2="reverse.fastq"
cat ${FASTQ} | grep '^@.*/1$' -A 3 --no-group-separator > ${FASTQ1}
cat ${FASTQ} | grep '^@.*/2$' -A 3 --no-group-separator > ${FASTQ2}
```

---

> Tools used with IonTorrent data

<ul>
  <li><a href="https://wonder.cdc.gov/amd/flu/irma/">IRMA, Iterative Refinement Meta-Assembler (from CDC):</li>
  <ul>
    <li><a href="https://github.com/peterk87/irma">IRMA GitHub.</a></li>
    <li><a href="https://bmcgenomics.biomedcentral.com/articles/10.1186/s12864-016-3030-6">IRMA paper.</a></li>
    <li><a href="https://github.com/peterk87/irma/blob/master/IRMA_RES/defaults.sh">IRMA default values.</a></li>
  </ul>
  <li><a href="https://github.com/iontorrent/TS/tree/master/Analysis/TMAP">TMAP, Torrent Mapping Alignment Program (GitHub repository).</a></li>
</ul>


  <p align="right" dir="auto">
   <a href="#home" title="Up">
    <img src="../group4/images/home-icon.png" style="max-width: 100%;">
   </a>
 </p>
  
---

**Experiments**

- Run ViralRecon with FASTQ from the HERA QCs.
- Run IRMA with FASTQ files.

  <p align="right" dir="auto">
   <a href="#home" title="Up">
    <img src="../group4/images/home-icon.png" style="max-width: 100%;">
   </a>
 </p>
 
---

<a name="Day2"></a>
### Day 2

<!-- ************************** SECTION HERE -->

> SyncUP meeting in the morning:

- To get IonTorrent output files: FASTQ, uBAM or BAM? It depends on the sequencer: PGM or S5?
- Ask the HERA staff about the QC results: how many laboratories in RELECOV are producing IonTorrent data? In which format?
- If we start from BAM (already mapped reads with TMAP), we can go directly with ViralRecon?
- If we start from uBAM, try the BAM-to-FASTQ.
- If we start from FASTQ, find the corresponging BED files.
- Provide SFTP credentials to Joan to share data.
- Several things to do in the very near future:
<ul>
  <ul>
  <li>Perform a survey within the RELECOV labs currently using IonTorrent technology to know which files they produce (BAM, uBAM, FASTQ...).</li>
  <li>Test ViralRecon using a uBAM previously converted to FASTQ from the very first step of the pipeline.</li>
  <li>Test ViralRecon using a BAM (already mapped with TMAP) after the mapping step.</li>
  </ul> 
</ul>

**Experimental code for TMAP**

```Bash
# Define dirs and files
refdir="dir-to-reference"
ref="NC_045512.2.fasta"
indir="dir-to-FASTQ"
fastq="sample.fastq.gz"
tmap="dir-to-tmap/tmap"
sam="test.sam"
bam="test.bam"

$tmap mapall -f ${refdir}/${ref} \
  -i fastq -r ${fastqdir}/${fastq} \
  -s ${sam} \
  -v -Y -u -o 0 stage1 map4

samtools view -S -b ${sam} > ${bam}

samtools flagstat ${bam}
# Example
#262144 + 0 in total (QC-passed reads + QC-failed reads)
#262144 + 0 primary
#0 + 0 secondary
#0 + 0 supplementary
#0 + 0 duplicates
#0 + 0 primary duplicates
#261016 + 0 mapped (99.57% : N/A)
#261016 + 0 primary mapped (99.57% : N/A)
#0 + 0 paired in sequencing
#0 + 0 read1
#0 + 0 read2
#0 + 0 properly paired (N/A : N/A)
#0 + 0 with itself and mate mapped
#0 + 0 singletons (N/A : N/A)
#0 + 0 with mate mapped to a different chr
#0 + 0 with mate mapped to a different chr (mapQ>=5)

# Sort BAM
inBAM="test.bam"
outBAM="test.sorted.bam"
samtools sort ${inBAM} > ${outBAM}

# Keep only mapped reads [Optional]
inBAM="test.sorted.bam"
outBAM="test.sorted.mapped.bam"
samtools view -F 0x04 -b ${inBAM} > ${outBAM}

# Pileup and make consensus FASTA using different thresholds for 'minimum quality score threshold to count base' (q), 
# 'minimum frequency threshold to call consensus (t=0-1)', and 'minimum depth to call consensus' (m)
q=20
t=0
m=10
BAM="test.sorted.mapped.bam"
FASTA="test.fasta"
samtools mpileup -A -Q 0 ${BAM} | ivar consensus -p test.fasta -q ${q} -t ${0} -m ${10}
```

  <p align="right" dir="auto">
   <a href="#home" title="Up">
    <img src="../group4/images/home-icon.png" style="max-width: 100%;">
   </a>
 </p>

---

> Wrap up of Day 2

- We tested 10 FASTQ files from Ion Torrent technology from the HERA QC with ViralRecon.
- We compared the global results provided by Nexclade-web. The lineages/clades match is total (10 out of 10).
- At the nucleotide level, we saw some divergences across the viral genome, probably related to how IonTorrent (IRMA?) and ViralRecon process the allele frequencies at the variant calling and consensus steps.
- We suggest widening the benchmarking using tens of samples (provided by Joan) to find other mismatches and study in detail some of the discrepancies (i.e. nucleotides close to primer ends, deletions of two and three AA, etc.).
- We clean-the-house at the sFTP site to upload more IonTorrent files for Day 3.
- We need the IonTorrent SARS-CoV-2 protocol primer manifest BED files!

  <p align="right" dir="auto">
   <a href="#home" title="Up">
    <img src="../group4/images/home-icon.png" style="max-width: 100%;">
   </a>
 </p>
 
---

<a name="Day3"></a>
### Day 3

<!-- ************************** SECTION HERE -->

> SyncUP meeting in the morning:

- We checked the Base Quality encoding of IonTorrent FASTQ files. As it uses the tilde character ('~'), which is ASCII(126), it seems IonTorrent provides Phred-like values as Illumina 1.3-1.8 encoding scale, ranging from 64 to 126. Therefore, it will be necessary to **substract 64 from the Phred-like values used by these FASTQ or adapt the corresponging filters in Viral-Recon NF configuration**. [See Phylogenomics: An Introduction, p. 84](https://books.google.es/books?id=ZGsmDwAAQBAJ&pg=PA83&lpg=PA83&dq=what+is+~+in+phred+Ion+Torrent+FASTQ&source=bl&ots=j4GdHZCWZA&sig=ACfU3U0mfwn8ddmorz-kpQJi6BQqvpxB4w&hl=en&sa=X&ved=2ahUKEwi5qcGCsdf4AhWFC-wKHY8iBEwQ6AF6BAgTEAM#v=onepage&q=what%20is%20~%20in%20phred%20Ion%20Torrent%20FASTQ&f=false)

<p>
  <center>
    <img src="https://github.com/jlorsal/relecov_biohackaton/blob/ion_torrent/group4/images/FASTQ_IonTorrent_base-qual_encoding.png" width=75%" />
    </center>
</p>

- FASTQ automatically detects this encoding and shows the corresponding Sanger/Illumina 1.9 equivalente encoding:

<p>
  <center>
  <img src="https://github.com/jlorsal/relecov_biohackaton/blob/ion_torrent/group4/images/FASTQ_IonTorrent_phred-like-encoding.png" width="75%" />
  </center>
</p>

...




