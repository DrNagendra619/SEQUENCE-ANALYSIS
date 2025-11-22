# SEQUENCE-ANALYSIS
SEQUENCE ANALYSIS
# 🧬 Bioinformatics Sequence Analysis with BioPython

## 📝 Overview

This Jupyter Notebook demonstrates a comprehensive set of fundamental tasks in **Bioinformatics Sequence Analysis** using the **BioPython** library. The script covers operations ranging from basic DNA/RNA manipulation and translation to advanced tasks like sequence alignment, motif searching, and retrieving data directly from NCBI.

The examples use both simple inline sequences and data loaded from an uploaded genomic FASTA file, intended for analysis of a large DNA sequence (referenced as "E. coli Genome" in the file name, though the imported data appears to be from *Prosopis alba* LOC114717194).

## 🚀 Analysis Workflow

The notebook executes the following key steps:

### 1. Basic Sequence Manipulation

* **Complement & Reverse Complement**: Demonstrates finding the complementary strand (`my_seq.complement()`) and the reverse complementary strand (`my_seq.reverse_complement()`) of a small DNA sequence.
* **Transcription & Translation**: Shows how to transcribe DNA to mRNA (`my_seq.transcribe()`) and translate mRNA to an amino acid sequence (`my_seq.translate()`).
* **Protein Translation**: Translates a larger DNA sequence into a protein sequence (`dna_seq.translate()`), illustrating the process of reading codons.

---

### 2. File Handling and Genomic Analysis

The following steps rely on an uploaded FASTA file named **`gene.fna`** (which contains a sequence labeled `NW_021636346.1:c40256-27400`):

* **File Upload**: Uses `google.colab.files.upload()` to import the required sequence file (`gene.fna`).
* **Sequence Inspection**: Parses the uploaded FASTA file to print the **ID**, **Description**, **Length**, and the **first 100 bases** of the sequence record.
* **GC Content Calculation**: Defines a function to manually calculate the **GC content** (percentage of Guanine and Cytosine bases) for the loaded sequence.
* **Sequence Filtering**: Filters the records in `gene.fna` based on a minimum length (`min_length = 300`) and writes the resulting sequences to a new file, **`long_sequences.fasta`**.
* **Translation and Saving**: Translates the sequence in `gene.fna` into a protein sequence, stopping at the first encountered stop codon (`to_stop=True`), and saves the result to **`translated_proteins.fasta`**.

---

### 3. Advanced Analysis

* **Pairwise Sequence Alignment**: Performs a **Global Sequence Alignment** (`globalxx`) between two short, distinct sequences (`GATTACA` and `GCATGCU`) using the Needleman-Wunsch algorithm and prints the formatted alignments and scores.
* **Motif Searching (Regex)**: Uses Python's built-in `re` module along with BioPython to define a regular expression motif (`ATG[ATGC]{3,}TAA`) and search for it within the genomic sequence, printing the number of matches found.
* **NCBI Entrez Query**: Demonstrates fetching a record (NM\_001301717) from the NCBI Nucleotide database using **`Bio.Entrez`** and printing its details (ID, Description, and Sequence snippet).
* **ORF Prediction**: Contains a custom function (`find_codons`) to identify the **Start Codon ("ATG")** and the first **Stop Codon** ("TAA", "TAG", or "TGA") in a test sequence, predicting the length of a potential Open Reading Frame (ORF).

## 🛠️ Requirements

The notebook requires the following Python library:

```bash
!pip install biopython
