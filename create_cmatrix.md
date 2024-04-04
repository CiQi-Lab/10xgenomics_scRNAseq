## Running `cellranger count` and getting `count matrix`

### Overview

To run `cellranger count`, you need to provide input FASTQ files and a reference transcriptome. The command generates gene expression and/or feature barcode reads from a single sample and GEM well.

### Usage

Print the usage statement to see the required parameters:

```bash
cellranger count --help
```

### Running the Command

To run `cellranger count`, you need to specify an `--id`, which is a unique identifier for the pipeline instance. You also need to provide the `--fastqs` parameter, pointing to the directory containing the FASTQ files. Optionally, use the `--sample` argument to specify which samples to use if there are multiple samples in the FASTQ directory. Finally, provide the path to the `--transcriptome` reference package.

```bash
cellranger count --id=run_count_1kpbmcs \
   --fastqs=/mnt/home/user.name/yard/run_cellranger_count/pbmc_1k_v3_fastqs \
   --sample=pbmc_1k_v3 \
   --transcriptome=/mnt/home/user.name/yard/run_cellranger_count/refdata-gex-GRCh38-2020-A
```

### Explore the Output

The output of the `cellranger count` pipeline is located in the `outs` folder within the pipeline instance directory. You can explore the contents of this directory using the `ls` command:

```bash
ls -1 run_count_1kpbmcs/outs
```

### Conclusion

After running `cellranger count`, check the `web_summary.html` file to view the results of the experiment. Additionally, you can load the `cloupe.cloupe` file into the Loupe Browser for further analysis. The `outs` directory contains various outputs that can be used with external software tools like the Seurat R package.
The output is similar to the following:


```
├── analysis
├── cloupe.cloupe
├── filtered_feature_bc_matrix
├── filtered_feature_bc_matrix.h5
├── metrics_summary.csv
├── molecule_info.h5
├── possorted_genome_bam.bam
├── possorted_genome_bam.bam.bai
├── raw_feature_bc_matrix
├── raw_feature_bc_matrix.h5
└── web_summary.html

```
