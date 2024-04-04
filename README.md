# scRNAseq preprocessing  <img align = 'right' width="150" height = '60' alt="image" src="https://github.com/CiQi-Lab/10xgenomics_scRNAseq/assets/64673748/c333c7de-510f-4808-939e-e10200938bd0"> <img width="150" height='60' align = 'right' alt="image" src="https://github.com/CiQi-Lab/10xgenomics_scRNAseq/assets/64673748/1e9565e4-3e00-4e85-88ff-9f8009ff8890">


### CellRanger for scRNA-seq Pre-processing

CellRanger is already included as a module with Alpine High Perfoming Computing Cluster. In order to view whether CellRanger is already part of your Alpine env., Please run the below from the home directory.

```
acompile
```

```
module list
```

if module list does not retrieve all the softwares included in your Alpine env., please run-

```
module avail
```

This would retrieve all the Softwares installed. To futher understand the required software, please run as below.

```
module spider cellranger
```


To use cellranger and run scripts, start or submit job with a script similar to below

```

#!/bin/bash

#SBATCH --partition=aa100
#SBATCH --nodes=1
#SBATCH --ntasks=8
#SBATCH --time=24:00:00
#SBATCH --gres=gpu:1
#SBATCH --mail-type=ALL
#SBATCH --mail-user= <replace with your email id>


module purge
module load  cellranger

echo "== This is the scripting step! =="


----      cellranger commands    ------


echo "== End of Job =="

```


- To understand on how to generate a reference file for the genome, follow [make_genome_ref.md](https://github.com/CiQi-Lab/10xgenomics_scRNAseq/blob/main/make_genome_ref.md)

- For pre-processing and creating count matrix from fastq file, follow [create_cmatrix.md](https://github.com/CiQi-Lab/10xgenomics_scRNAseq/blob/main/create_cmatrix.md)
