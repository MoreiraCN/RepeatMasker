### RepeatMasker

The following pipeline was used to identify repetitive DNA content of assembled genome of the species *Holochilus sciureus* (2n = 56, NF = 56), a Neotropical rodent of tribe Oryzomyini.

**Software used:**

[RepeatMasker_version_4.1.1](https://www.repeatmasker.org/). Tarailo‐Graovac M, Chen N (2009) Using RepeatMasker to identify repetitive elements in genomic sequences. Curr Protoc Bioinformatics, 25(1):4-10.

**Input data:**
 
- [Assembled](https://github.com/MoreiraCN/Assembling_Illumina_sequences) genome in fasta format.

**Step 1 > BuildDatabase (preparing the data to build a repeat library):**

`/BuildDatabase -name sample_name.DB -engine rmblast assembly.fa`

**Step 2 > RepeatModeler (building a repeat library):**

`/RepeatModeler -database sample_name.DB -engine ncbi`

**Step 3 > Masking:**

`/RepeatMasker perl -pa 20 -gff -lib /repeatmodeler/sample_name/consensi.fa.classified -s -a -dir RepeatMasker_sample_name assembly.fa`

**Parameters used:**
 
- All parameters used are available at [Using and understanding RepeatMasker](https://link.springer.com/protocol/10.1007/978-1-61779-603-6_2) and [TETools](https://github.com/Dfam-consortium/TETools).
