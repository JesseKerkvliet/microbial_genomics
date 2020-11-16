# Exercise Whole Genome Sequencing and Bioinformatics

## Getting started
This is the bioinformatics exercise for the lecture "Whole Genome Sequencing and bioinformatics". First, download the data using the .zip download at the top of the page. In the zip file you'll find a folder called 'data'. This is what you're going to need during this exercise.

## Background
The goal of this exercise is to give you a feel for the kind of tools you can use to answer biological questions using Whole Genome Sequencing (WGS). Usually, bioinformatics is done using a remote computer (usually a powerful specialized server) in a commandline interface. However, due to time constraints, we will only use webtools for this exercise.   
### The experiment
For an antibiotic surveilance experiment, the genome of multiple samples of several species has been sequenced.You are tasked with finding out which antibiotic resistance genes are present in four samples of one species, and if they are located on plasmids that can make spreading of the genes throughout the population possible. Some of the samples were mislabeled after sequencing, so although your sample says *"S. aureus"* you will need to make sure that this is correct. 
Before you continue, think about the following questions:

1. **Can we infer antibiotic resistance from the whole genome only?**
2. **Can we infer a gene being located on a plasmid with whole genome only?**

## Quality Control
WGS produces a wealth of data that needs careful processing by specialized software in order to be used to give insights in biological questions. The first step after sequencing reads are provided by the sequencer, is to get an idea of the overall quality of the data. To do this, we usually generate a quality report using the tool FastQC. In the /data/ folder, you'll find a .html file **(fastqc_report.html)**. Open this file in your web browser or [open this link in a new tab](/data/fastqc_report.html)
Using this report, answer the following questions:

1. **What kind of sequencing technique was used in this sample?**
2. **Do the reads need trimming? Why (not)?**
3. **Why did the per-base sequence content fail? Can this be due to adapter sequences from the sequencer still in the reads?**

## Annotation
After genome assembly, which is too computationally demanding to do on a web service, contigs are annotated to shed light on the function of the genetic structures on those contigs. In this exercise you will use four assembled genomes to find genes associated with antibiotic resistance and the genetic context in which these genes are.

To find antibbiotic resistance genes (ARGs), we will use the ResFinder database. This database is an important database with ARGs per species. As of August 2020, this database contains 2690 ARGs that are curated by experts. This number is still growing. 
To use this database, it's important to know what species we're dealing with. To get this information, open the .fasta file in the data folder using a text editor like Notepad.
### BLAST
The easiest way to find out what species is in your WGS assembly, is to use BLAST. BLAST is an algorithm often used to compare a sequence of interest (query) with sequences (DNA, RNA or peptide) in a database. In this case, the database is the nucleotide database of the NCBI, containing a vast amount of sequence data from many different sources. To use BLAST, go to [this link](https://blast.ncbi.nlm.nih.gov/Blast.cgi). Choose "Nucleotide BLAST". In the webform, enter one of the contigs from the assembly file *(hint for faster results: assembly files are ordered from long to short sequences)*. Next, click the "BLAST" button and wait for the BLAST run to be completed.

4. **Which species is in our samples?**
5. **Is there any functional information on the contig you chose? (e.g. a protein match)**

### ResFinder
Now that we know which species we have in our samples, we can use the species-specific datasets in the ResFinder database. Go to [the ResFinder website](https://cge.cbs.dtu.dk/services/ResFinder/). Click the "acquired antimicrobial resistance" checkbox and select the following antibiotics: 
- Beta-lactam
- Colistilin
- Tetracyclin
- Aminoglycoside

Click while holding the control key to add to your selection. Next, select the species you found earlier in the drop-down menu. Upload one of your files using the "Isolate files" button. Upload one and click upload. *Note: uploading all 4 files at the same time doesn't work, so repeat this step for all 4 assemblies*

**For each of the four files:**

6. **Which antibiotic resistance phenotypes are predicted for the sample?**
7. **On which contig is the resistance gene located?**
8. **Are any of the hits originating from a plasmid?**
9. **The names of the contigs between samples are the same: NODE_[number]\_length\_[number]\_cov\_[number]. Are contigs that have the same name in different samples also the same sequence?**

## Plasmids
One of the results that shows up often in these samples is the ampicillin resistance gene *blaTEM-1B*. This gene encodes a beta-lactamase, providing resistance against beta-lactam-based antibiotics. According to the ResFinder hit, this is gene is usually located on a plasmid. We want to know if this is the case in our samples. ResFinder only shows a hit with the *blaTEM-1B* gene, not with the genetic context. We are therefore not sure that this gene is located on a plasmid in our sample. To check if this is the case, we return to [BLAST](blast.ncbi.nlm.nih.gov/Blast.cgi). Open one of your assembly files in a text editor and copy the contig that contains the *blaTEM-1B* gene according to ResFinder. Go back to BLAST and choose blastn once more. In the entry field, paste the contig you chose and start the tool. 

10. **Is the contig a plasmid? How do you know?**
11. **Is the sequence your contig matches to the same length as your contig? If not, what could be an explanation for that?**

## Answers
The answers to these questions will be discussed during the lecture (if time allows it), and will be uploaded [here](answers.md) after the lecture.
