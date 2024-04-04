## Custom Reference for Cell Ranger (mkref)

### Overview
To create a custom reference for Cell Ranger, you need to follow several steps. This tutorial outlines the process of building a custom reference using the `cellranger mkref` pipeline.

### Find the Input Files
Locate the reference genome FASTA and GTF files for your species. For this tutorial, we'll use zebrafish (Danio rerio) as an example. Download the required files from Ensembl or other sources if not available on Ensembl.

#### Downloading Files
```bash
wget http://ftp.ensembl.org/pub/release-105/gtf/danio_rerio/Danio_rerio.GRCz11.105.gtf.gz
gunzip Danio_rerio.GRCz11.105.gtf.gz

wget http://ftp.ensembl.org/pub/release-105/fasta/danio_rerio/dna/Danio_rerio.GRCz11.dna.primary_assembly.fa.gz
gunzip Danio_rerio.GRCz11.dna.primary_assembly.fa.gz
```

Incase, you have the .fa/.fna and .gtf files already saved in a directory, replace below with the files locations or run commands from the directory where the files exists

### Filter the GTF
GTF files can contain entries for non-polyA transcripts, causing issues. To filter these, use the `cellranger mkgtf` command.

```bash
cellranger mkgtf \
    Danio_rerio.GRCz11.105.gtf \
    Danio_rerio.GRCz11.105.filtered.gtf \
    --attribute=gene_biotype:protein_coding
```

### Setup the `cellranger mkref` Command
Now, set up the command to run the `cellranger mkref` pipeline.

```bash
cellranger mkref \
    --genome=Drerio_genome \
    --fasta=Danio_rerio.GRCz11.dna.primary_assembly.fa \
    --genes=Danio_rerio.GRCz11.105.filtered.gtf
```

### Run `cellranger mkref`
Execute the above command. This may take several hours. Ensure to run it in a suitable High Performance computing environment.

Upon successful completion, you'll see:

```bash
>>> Reference successfully created! <<<
cellranger --transcriptome=/Danio.rerio_genome ...
```
The reference was successfully created, as noted in the output message above, in the directory specified by the --genome flag (Danio.rerio_genome in this case). If you do not see this message, an error likely occurred. The outputs are organized as below:


```
├── fasta
    │   ├── genome.fa
    │   └── genome.fa.fai
    ├── genes
    │   └── genes.gtf.gz
    ├── reference.json
    └── star
        ├── chrLength.txt
        ├── chrNameLength.txt
        ├── chrName.txt
        ├── chrStart.txt
        ├── exonGeTrInfo.tab
        ├── exonInfo.tab
        ├── geneInfo.tab
        ├── Genome
        ├── genomeParameters.txt
        ├── SA
        ├── SAindex
        ├── sjdbInfo.txt
        ├── sjdbList.fromGTF.out.tab
        ├── sjdbList.out.tab
        └── transcriptInfo.tab

```
