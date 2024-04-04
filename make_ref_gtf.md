### Filter GTF file

```{}
cellranger mkgtf \
    Danio_rerio.GRCz11.105.gtf \
    Danio_rerio.GRCz11.105.filtered.gtf \
    --attribute=gene_biotype:protein_coding

```


### Creating Genome Reference File

```{}
cellranger mkref \
    --genome=Drerio_genome \
    --fasta=Danio_rerio.GRCz11.dna.primary_assembly.fa \
    --genes=Danio_rerio.GRCz11.105.filtered.gtf
```

#### On successful generation of FASTA genome Referrence file, Alpine would should sho
