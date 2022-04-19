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

**Step 4 > Landscape (step 1):**

`/repeatmasker_rmblast /RepeatMasker/util/calcDivergenceFromAlign.pl -s landscape_step1_sample_name.sumary -a landscape_step1_sample_name.align /RepeatMasker_sample_name/sample_name_assembly.fasta.align`

**Step 5 > Landscape:**

`/repeatmasker_rmblast /RepeatMasker/util/createRepeatLandscape.pl -div landscape_step1_sample_name.sumary -g genome_size > sample_name_landscape.html`

**Parameters used:**
 
- All parameters used are available at [Using and understanding RepeatMasker](https://link.springer.com/protocol/10.1007/978-1-61779-603-6_2) and [TETools](https://github.com/Dfam-consortium/TETools).
- For genome size use: `grep -v '>' | wc -c sample_name_assembly.fasta.align`
