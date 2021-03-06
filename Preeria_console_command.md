
#### Flye assembler

<pre><code>flye --meta --nano-raw /Bmo/jyakovleva/parampampam/genomes/PGD/data/nanopore_length_filtering/len1000_filtered.fastq \ 
--out-dir /Bmo/jyakovleva/Panshin/out_nano/assembly.fasta -t 32</code></pre>

#### Minimap

<pre><code>minimap2 -t 32 -ax map-ont /Bmo/jyakovleva/Panshin/out_nano/assembly.fasta \ 
/Bmo/jyakovleva/Panshin/oper/len1000_filtered.fastq > /Bmo/jyakovleva/Panshin/oper/aln1.sam</code></pre>

#### Quast

<pre><code>quast.py -o /Bmo/jyakovleva/Panshin/oper/quast_output -r /Bmo/jyakovleva/Panshin/oper/len1000_filtered.fastq \
-g /Bmo/jyakovleva/Panshin/oper/first_cycle/medaka_1/consensus.fasta /Bmo/jyakovleva/Panshin/oper/second_circle/medaka_11/consensus.fasta \ 
/Bmo/jyakovleva/Panshin/oper/third_cycle/medaka_3/consensus.fasta</code></pre>

#### Proteinortho

<pre><code>proteinortho -cpus=16 -ram=25 -project=preeria *.faa 40-19</code></pre>

#### Prokka

<pre><code>prokka --outdir mydir --prefix mygenome /Bmo/jyakovleva/parampampam/genomes/PGD/data/split/subassembly_three_rounds/assembly.fasta</code></pre>

#### Racon

<pre><code>/Bmo/jyakovleva/Programs/racon/build/bin/racon -t 32 /Bmo/jyakovleva/Panshin/oper/len1000_filtered.fastq /Bmo/jyakovleva/Panshin/oper/aln1.sam /Bmo/jyakovleva/Panshin/out_nano/assembly.fasta > /Bmo/jyakovleva/Panshin/oper/racon2true.fasta</code></pre>

#### Medaka

<pre><code>medaka_consensus -i /Bmo/jyakovleva/Panshin/oper/len1000_filtered.fastq -d /Bmo/jyakovleva/Panshin/oper/racon2true.fasta -o
/Bmo/jyakovleva/Panshin/oper/medaka_1 -t 32 -m r941_min_high_g303</code></pre>

#### BWA

<pre><code>bwa mem ref.fa read1.fq read2.fq > aln-pe.sam</code></pre>

#### Prodigal

<pre><code>prodigal -i my.genome.fna -o my.genes -a my.proteins.faa</code></pre>


