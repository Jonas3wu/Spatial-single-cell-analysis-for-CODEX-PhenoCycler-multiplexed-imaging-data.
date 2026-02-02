# Acknowledgement
This pipeline is adapted and tailored from the SPACEc project by the SPACEc authors/contributors:
https://github.com/yuqiyuqitan/SPACEc

# Spatial-single-cell-analysis-for-CODEX-PhenoCycler-multiplexed-imaging-data.
In this end-to-end analysis, it took a multichannel .tif slide image, performed tissue extraction + cell segmentation, exported per-cell features into .csv, then run region-wise preprocessing, neighborhood analysis, clustering/annotation, and spatial plotting (cell types/clusters overlaid on the image).

# What I operationalized & customized

HPC-ready, CPU-first execution: made the SPACEc workflow reproducible on an HPC cluster for CODEX/PhenoCycler-style multichannel TIFFs (tonsil TMA example).

Containerized run (Docker → Singularity → Jupyter): built a CPU Docker image, exported to .tar, converted to a Singularity .sif, then ran on a compute node with bind mounts + Jupyter Lab port-forwarding (port 7777).

Pipeline flow: segmentation → preprocessing/normalization → clustering/annotation → spatial overlays.

# example of what my analysis found: 
CD20⁺CXCR5⁺ B cells increased from ~12.5% of total B cells in healthy tonsil to ~67% in tonsillitis.




