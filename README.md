# 2023-actin-embedding

We used the [ProteinCartography](https://github.com/Arcadia-Science/ProteinCartography) (v0.4.2) pipeline and the [Actin Prediction](https://github.com/Arcadia-Science/2022-actin-prediction) pipeline to investigate the well-known actin family of proteins. 

You can find a summary of this study and the results in the Pub: [![Arcadia Pub](https://img.shields.io/badge/Arcadia-Pub-596F74.svg?logo=data:image/svg%2bxml;base64,PD94bWwgdmVyc2lvbj0iMS4wIiBlbmNvZGluZz0idXRmLTgiPz4KPCEtLSBHZW5lcmF0b3I6IEFkb2JlIElsbHVzdHJhdG9yIDI3LjcuMCwgU1ZHIEV4cG9ydCBQbHVnLUluIC4gU1ZHIFZlcnNpb246IDYuMDAgQnVpbGQgMCkgIC0tPgo8c3ZnIHZlcnNpb249IjEuMSIgaWQ9IkxheWVyXzEiIHhtbG5zPSJodHRwOi8vd3d3LnczLm9yZy8yMDAwL3N2ZyIgeG1sbnM6eGxpbms9Imh0dHA6Ly93d3cudzMub3JnLzE5OTkveGxpbmsiIHg9IjBweCIgeT0iMHB4IgoJIHZpZXdCb3g9IjAgMCA0My4yIDQwLjQiIHN0eWxlPSJlbmFibGUtYmFja2dyb3VuZDpuZXcgMCAwIDQzLjIgNDAuNDsiIHhtbDpzcGFjZT0icHJlc2VydmUiPgo8c3R5bGUgdHlwZT0idGV4dC9jc3MiPgoJLnN0MHtmaWxsOm5vbmU7c3Ryb2tlOiNGRkZGRkY7c3Ryb2tlLXdpZHRoOjI7c3Ryb2tlLWxpbmVqb2luOmJldmVsO3N0cm9rZS1taXRlcmxpbWl0OjEwO30KPC9zdHlsZT4KPGc+Cgk8cG9seWdvbiBjbGFzcz0ic3QwIiBwb2ludHM9IjIxLjYsMyAxLjcsMzcuNCA0MS41LDM3LjQgCSIvPgoJPGxpbmUgY2xhc3M9InN0MCIgeDE9IjIxLjYiIHkxPSIzIiB4Mj0iMjEuNiIgeTI9IjI3LjMiLz4KCTxwb2x5bGluZSBjbGFzcz0ic3QwIiBwb2ludHM9IjEyLjIsMTkuNCAyNC42LDMwLjEgMjQuNiwzNy40IAkiLz4KCTxsaW5lIGNsYXNzPSJzdDAiIHgxPSIxNy42IiB5MT0iMTYuNyIgeDI9IjE3LjYiIHkyPSIyNC4xIi8+Cgk8bGluZSBjbGFzcz0ic3QwIiB4MT0iMjguNiIgeTE9IjE1LjIiIHgyPSIyMS43IiB5Mj0iMjIuMSIvPgoJPHBvbHlsaW5lIGNsYXNzPSJzdDAiIHBvaW50cz0iNi44LDI4LjcgMTkuNSwzNC40IDE5LjUsMzcuNCAJIi8+Cgk8bGluZSBjbGFzcz0ic3QwIiB4MT0iMzQuOCIgeTE9IjI1LjgiIHgyPSIyNC42IiB5Mj0iMzYuMSIvPgoJPGxpbmUgY2xhc3M9InN0MCIgeDE9IjI5LjciIHkxPSIyMi4yIiB4Mj0iMjkuNyIgeTI9IjMwLjkiLz4KPC9nPgo8L3N2Zz4K)](https://doi.org/10.57844/arcadia-a7cb-9f5c)

The results of the analysis performed in this repository can be found on Zenodo: [![DOI](https://zenodo.org/badge/DOI/10.5281/zenodo.8377393.svg)](LINK) 

## Purpose
The [ProteinCartography](https://github.com/Arcadia-Science/ProteinCartography) pipeline is designed to explore protein families based on their structural relationships. The pipeline produces interactive maps with clusters and various overlays that can be used to analyze families. For more information on the ProteinCartography pipeline checkout the [pub](https://research.arcadiascience.com/pub/resource-protein-cartography/). 

As a use case of this tool, we analyzed the actin family. This is a well-studied family with multiple subfamilies that makes it an interesting choice for the pipeline. Additionally, this protein family is involved in a plethora of cellular functions, meaning the results we find will have relevance to many fields. We've previously investigated this family in our [Defining Actin](https://research.arcadiascience.com/pub/idea-defining-actin/release/4?readingCollection=9a516d32) pub and the corresponding [GitHub repo](https://github.com/Arcadia-Science/2022-actin-prediction). In this analysis, we gathered a list of actins via a BLAST search for the top 50,000 proteins in the NCBI non-redundant (nr) database with no taxonomic constrictions. This list is used in the current analysis.

## General overview
For in depth instructions regarding how to use this repository in conjunction with the [ProteinCartography](https://github.com/Arcadia-Science/ProteinCartography) pipeline and the [Actin Prediction](https://github.com/Arcadia-Science/2022-actin-prediction) pipeline, see the [Walkthrough](#walkthrough) below. Briefly, you should follow these steps: 

1. Clone this repository, set up the `2023-actin` environment
2. Clone the [ProteinCartography](https://github.com/Arcadia-Science/ProteinCartography) pipeline, set up the `cartography_tidy` environment
3. Set up the general directory structure
4. Fetch data from the [Actin Prediction](https://github.com/Arcadia-Science/2022-actin-prediction) repo
5. Use the `1_prepare_metadata.ipynb` notebook to prepare metadata for the ProteinCartography analysis
6. Use the `2_get_alphafold_structures.ipynb` notebook to download all relevant AlphaFold structures
7. Run ProteinCartography in "Cluster Mode"
8. Create custom plots using the `3_plotting_overlays.ipynb`
9. Evaluate cluster distributions using `4_cluster_distributions.ipynb` 


## Walkthrough

### 1. Clone this repository

First, you should clone this repository using the following command: 

```
git clone https://github.com/Arcadia-Science/2023-actin-embedding.git
```

For this repository, we use the `2023-actin` environment, which is the `cartography_tidy` environment from the ProteinCartography pipeline plus a few bonus packages. We recommend using [conda](https://conda.io/projects/conda/en/latest/user-guide/install/index.html) and/or [mamba](https://github.com/mamba-org/mamba) to set up your environment. Create the environment using conda by running the following code from within the repository: 

````
conda env create -f envs/2023-actin-embedding.yml -n 2023-actin-embedding
conda activate 2023-actin-embedding
````


### 2. Set up the `ProteinCartography` pipeline

To begin, visit the [ProteinCartography](https://github.com/Arcadia-Science/ProteinCartography) repo for a guide on running the pipeline. The notebooks used in this repo are designed to run alongside the ProteinCartography pipeline, so we recommend cloning the ProteinCartography pipeline before beginning. We used the [ProteinCartography pub release v0.4.2 release](https://github.com/Arcadia-Science/ProteinCartography/tree/v0.4.2) for this analysis.

The Quickstart guide in the ProteinCartography repository should get you started. But briefly, to clone the repository, use the following command: 

```
git clone https://github.com/Arcadia-Science/ProteinCartography.git
```

You can then checkout the specific [v0.4.2 release](https://github.com/Arcadia-Science/ProteinCartography/tree/v0.4.2) using the following: 

```
git checkout v0.4.2
```

We will use the `cartography_tidy` environment from the ProteinCartography pipeline to run the ProteinCartography analysis. Create the environment using conda by running the following code from within the repository: 

````
conda env create -f envs/cartography_tidy.yml -n cartography_tidy
conda activate cartography_tidy
````

### 3. Set up directory structure

After cloning this repository and the ProteinCartography repository. You should set up your directory structure as follows: 

```
├── ProteinCartography
│   └── actin     # preparatory files and ProteinCartography run results end up here
|       └── structures # structures downloaded from the AlphaFold database
|       └── output # ProteinCartography results end up here
├── 2023-actin-embedding
│   ├── notebooks       # notebooks used for analysis
│   ├── input      # files from actin prediction pipeline
│   └── output     # final figures will end up here
```

Then move into the `2023-actin-embedding` folder for the remainder of the analysis.

### 4. Fetch data from the `Actin Prediction` repo

Once ProteinCartography is installed, you can find the data generated in the [Actin Prediction](https://github.com/Arcadia-Science/2022-actin-prediction) pipeline on [Zenodo](https://zenodo.org/records/7384393). This data is also included in the `Inputs` folder of this repository as `all_outputs_summarized.tsv`. The proteins from this file were used as our input for the analysis in this repository. Because it includes many proteins, this was broken up into 2 batches: `2022-actin-prediction-blastoutputs1.txt` and `2022-actin-prediction-blastoutputs2.txt`.

The notebooks in this repository were created to help prepare the metadata, download AlphaFold structures, and apply additional custom overlays to the output map. 

### 5. Prepare metadata

We started this analysis with a list of the 50,000 proteins most related to human actin according to protein BLAST. Before the ProteinCartography pipeline could be used, we prepared the list of proteins using the `1_prep_metadata.ipynb` notebook from within the `2023-actin-embedding/notebooks` folder using the `2023-actin-embedding` environment. To activate this environment, use the shell command: 

```
conda activate 2023-actin-embedding
```

This involves mapping RefSeq IDs to UniProt accession IDs, then retrieving data from UniProt for each protein. The data retrieved from UniProt include protein name, organism, taxonomic information, length, annotation score, length, fragment status, sequence, and gene name. The fragmentary proteins are then filtered out. 

The final list of proteins is reformatted to the [format required](https://github.com/Arcadia-Science/ProteinCartography#feature-file-main-columns) for "Cluster mode" of the ProteinCartography pipeline. 

### 6. Download AlphaFold structures

Next, we downloaded all available AlphaFold structures using the `2_get_alphafold_structures.ipynb` notebook. This notebook should be ran from within the `2023-actin-embedding/notebooks` folder using the `2023-actin-embedding` environment, but will deposit structures into `ProteinCartography/actin/structures` if you've set up your directory structure as above.

### 7. Run ProteinCartography "Cluster Mode"

We then ran the [ProteinCartography](https://github.com/Arcadia-Science/ProteinCartography) in "Cluster Mode" using the standard pipeline parameters. The complete analysis is linked in the Zenodo (LINK).

We placed the `config_ff_actin.yml` file, which can be found in the `ProteinCartography_docs` folder of this repository inside the `ProteinCartography/actin` folder. We moved into the `ProteinCartography` directory and then used the `cartography-tidy` environment to run the analysis. To activate the environment, use the following command: 

```
conda activate cartography-tidy
```

Then, from within the `ProteinCartography` folder, the following command used to run the ProteinCartography pipeline from "Cluster Mode" was: 

```
snakemake --snakefile Snakefile_ff --configfile actin/config_ff_actin.yml --use-conda --cores 2
```

### 8. Create custom plots

We used the results of ProteinCartography and the results form the Actin Prediction pipeline to create custom plots. To do this, we moved back into the `2023-actin-emedding/notebooks` folder, and then used the `3_plotting_overlays.ipynb` using the `2023-actin-embedding` environment. To activate this environment, run the following command: 

```
conda activate 2023-actin-embedding
```

### 9. Evaluate cluster distributions

Finally, we evaluated the distributions of proteins within clusters in the `4_cluster_distributions.ipynb`.
