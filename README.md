# EC2-ATACseq-Pipeline
Some scripts to efficiently run ATAC-seq jobs on AWS EC2 instances

## Dependencies
1. Bowtie2
2. Samtools
3. NGmerge

## Notes on choice of EC2 instance
-   Scripts were written with c5 and m5 type instances in mind [c5n and m5n were used to build out all scripts]
-   Number of cores: choose the number of cores for the instance based on the number of samples and the number of cores per sample (parameter choice) i.e. tot cores >= n_samples * (n_align_cores + n_sort_cores)
-   Memory: the memory parameter is only passed to Samtools for the sorting step. Therefore it is *per core* and does not include memory overhead required for the bowtie2 steps. A good starting point for this parameter seems to be: [total_memory - (5gb * n_samples)] / (n_sorting_cores * n_samples)


