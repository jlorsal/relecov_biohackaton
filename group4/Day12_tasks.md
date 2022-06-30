<a name="home"></a>
  
## I Relecov Biohackathon
## Group 4

## Tasks

<ul>
  <li><a href="#BibliographySeeking">Task 1. Bibliography seeking.</a></li>
  <li><a href="#IonTorrentData">Task 2. Provide Ion Torrent data set.</a></li>
  <li><a href="#SoftwareImplementation">Task 3. Software implementation: preprocessing, mapping and variant calling.</a></li>
</ul>

---

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

  <p align="right" dir="auto">
   <a href="#home" title="Up">
    <img src="../group4/images/home-icon.png" style="max-width: 100%;">
   </a>
 </p>
  

---
  
<!-- ************************** SECTION HERE -->

<a name="IonTorrentData"></a>
### Task 2: Ion Torrent dataset

- Check if FASTQ files from IonTorrent sequencing technology (PGM and/or S5) from the HERA project are available.
- Test directly with the FASTQ files provided (if any) into Viral-Recon.
- Set a BaseQuality filter (?) and other possible filters (depending on the noise within the input reads, specially in indels) in the config of Viral-Recon.
- ...

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
- ...

Some tools for BAM-to-FASTQ:
- [Samtools: bam2fq](http://www.htslib.org/doc/1.1/samtools.html)
- [BEDtools: bamtofastq](https://bedtools.readthedocs.io/en/latest/content/tools/bamtofastq.html)
- [bamtools](https://github.com/pezmaster31/bamtools)

  <p align="right" dir="auto">
   <a href="#home" title="Up">
    <img src="../group4/images/home-icon.png" style="max-width: 100%;">
   </a>
 </p>
  
---
