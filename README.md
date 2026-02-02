# Spatial-single-cell-analysis-for-CODEX-PhenoCycler-multiplexed-imaging-data.
In this end-to-end analysis, it took a multichannel .tif slide image, performed tissue extraction + cell segmentation, exported per-cell features into .csv, then run region-wise preprocessing, neighborhood analysis, clustering/annotation, and spatial plotting (cell types/clusters overlaid on the image).

# Acknowledgement
This pipeline is adapted and tailored from the SPACEc project by the SPACEc authors/contributors:
https://github.com/yuqiyuqitan/SPACEc

# What I operationalized & customized 

HPC-ready, CPU-first execution: made the workflow reproducible on an HPC cluster specifically for CODEX/PhenoCycler-style multichannel TIFFs (tonsil TMA example).

1. Containerized environment (Docker → Singularity → Jupyter on compute node): 1) Build a CPU image locally with Docker using the SPACEc Dockerfile, with a small contingency to relax a strict libxml2 pin if builds fail; then docker save to a .tar. 2)Upload the .tar to HPC, convert it to a Singularity .sif via singularity build ... docker-archive://.... 3) Run on a compute node (interactive srun), bind-mount project directory, activate the conda env inside the container, and launch Jupyter Lab; then port-forward from your laptop to the compute node’s 7777 port.

2. Practical robustness fixes for my runs: stabilized the notebook flow when tutorial outputs differ (e.g., treating label as index vs column; adding cell_id; preventing NaN-driven plotting failures; scalable cell-type coloring).

3. End-to-end “assembled pipeline” structure: organized a consistent folder layout + step order (inputs → segmentation outputs → preprocessing/normalization → clustering/annotation → spatial overlays).




