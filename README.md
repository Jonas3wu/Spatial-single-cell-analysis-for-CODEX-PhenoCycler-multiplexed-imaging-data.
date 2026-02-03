# Acknowledgement
This pipeline is adapted and tailored from the SPACEc project by the SPACEc authors/contributors:
https://github.com/yuqiyuqitan/SPACEc

# Spatial-single-cell-analysis-for-CODEX-PhenoCycler-multiplexed-imaging-data.
In this end-to-end analysis, it took a multichannel .tif slide image, performed tissue extraction + cell segmentation, exported per-cell features into .csv, then run region-wise preprocessing, neighborhood analysis, clustering/annotation, and spatial plotting (cell types/clusters overlaid on the image).

# What I operationalized & customized

HPC-ready, CPU-first execution: made the SPACEc workflow reproducible on an HPC cluster for CODEX/PhenoCycler-style multichannel TIFFs (tonsil TMA example).

Containerized run (Docker → Singularity → Jupyter): built a CPU Docker image, exported to .tar, converted to a Singularity .sif, then ran on a compute node with bind mounts + Jupyter Lab port-forwarding (port 7777).

Pipeline flow: segmentation → preprocessing/normalization → clustering/annotation → spatial overlays.

Fixed the pipeline crash when the input data changes slightly: Handled tutorial/output drift (e.g., label as index vs column), added stable cell_id, fixed NaN-driven plotting issues, and auto-generated scalable cell-type color palettes.

Optimized Clustering: Fine-tuned the Leiden algorithm to find the "sweet spot" of cell-type granularity while keeping it efficient for CPU processing.


# example of what my analysis found: 
CD20⁺CXCR5⁺ B cells increased from ~12.5% of total B cells in healthy tonsil to ~67% in tonsillitis.




