# 2023-actin-embedding

We used the [ProteinCartography](https://github.com/Arcadia-Science/ProteinCartography) pipeline and the [Actin Prediction](https://github.com/Arcadia-Science/2022-actin-prediction) pipeline to investigate the well-known actin family of proteins. 

You can find a summary of this study and the results in the Pub: [![Arcadia Pub](https://img.shields.io/badge/Arcadia-Pub-596F74.svg?logo=data:image/svg%2bxml;base64,PD94bWwgdmVyc2lvbj0iMS4wIiBlbmNvZGluZz0idXRmLTgiPz4KPCEtLSBHZW5lcmF0b3I6IEFkb2JlIElsbHVzdHJhdG9yIDI3LjcuMCwgU1ZHIEV4cG9ydCBQbHVnLUluIC4gU1ZHIFZlcnNpb246IDYuMDAgQnVpbGQgMCkgIC0tPgo8c3ZnIHZlcnNpb249IjEuMSIgaWQ9IkxheWVyXzEiIHhtbG5zPSJodHRwOi8vd3d3LnczLm9yZy8yMDAwL3N2ZyIgeG1sbnM6eGxpbms9Imh0dHA6Ly93d3cudzMub3JnLzE5OTkveGxpbmsiIHg9IjBweCIgeT0iMHB4IgoJIHZpZXdCb3g9IjAgMCA0My4yIDQwLjQiIHN0eWxlPSJlbmFibGUtYmFja2dyb3VuZDpuZXcgMCAwIDQzLjIgNDAuNDsiIHhtbDpzcGFjZT0icHJlc2VydmUiPgo8c3R5bGUgdHlwZT0idGV4dC9jc3MiPgoJLnN0MHtmaWxsOm5vbmU7c3Ryb2tlOiNGRkZGRkY7c3Ryb2tlLXdpZHRoOjI7c3Ryb2tlLWxpbmVqb2luOmJldmVsO3N0cm9rZS1taXRlcmxpbWl0OjEwO30KPC9zdHlsZT4KPGc+Cgk8cG9seWdvbiBjbGFzcz0ic3QwIiBwb2ludHM9IjIxLjYsMyAxLjcsMzcuNCA0MS41LDM3LjQgCSIvPgoJPGxpbmUgY2xhc3M9InN0MCIgeDE9IjIxLjYiIHkxPSIzIiB4Mj0iMjEuNiIgeTI9IjI3LjMiLz4KCTxwb2x5bGluZSBjbGFzcz0ic3QwIiBwb2ludHM9IjEyLjIsMTkuNCAyNC42LDMwLjEgMjQuNiwzNy40IAkiLz4KCTxsaW5lIGNsYXNzPSJzdDAiIHgxPSIxNy42IiB5MT0iMTYuNyIgeDI9IjE3LjYiIHkyPSIyNC4xIi8+Cgk8bGluZSBjbGFzcz0ic3QwIiB4MT0iMjguNiIgeTE9IjE1LjIiIHgyPSIyMS43IiB5Mj0iMjIuMSIvPgoJPHBvbHlsaW5lIGNsYXNzPSJzdDAiIHBvaW50cz0iNi44LDI4LjcgMTkuNSwzNC40IDE5LjUsMzcuNCAJIi8+Cgk8bGluZSBjbGFzcz0ic3QwIiB4MT0iMzQuOCIgeTE9IjI1LjgiIHgyPSIyNC42IiB5Mj0iMzYuMSIvPgoJPGxpbmUgY2xhc3M9InN0MCIgeDE9IjI5LjciIHkxPSIyMi4yIiB4Mj0iMjkuNyIgeTI9IjMwLjkiLz4KPC9nPgo8L3N2Zz4K)](LINK)

The full analysis and results are linked in on Zenodo: [![DOI](https://zenodo.org/badge/DOI/10.5281/zenodo.8377393.svg)](LINK) 

## Purpose
The [ProteinCartography](https://github.com/Arcadia-Science/ProteinCartography) pipeline is designed to explore protein families based on their structural relationships. The pipeline produces interactive maps with clusters and various overlays that can be used to analyze families. For more information on the ProteinCartography pipeline checkout the [pub](https://research.arcadiascience.com/pub/resource-protein-cartography/release/6?readingCollection=9a516d32). 

As a use case of this tool, we analyzed the actin family. This is a well-studied family with multiple subfamilies that makes it an interesting choice for the pipeline. Additionally, this protein family is involved in a plethora of cellular functions, meaning the results we find will have relevance to many fields. We've previously investigated this family in our [Defining Actin](https://research.arcadiascience.com/pub/idea-defining-actin/release/4?readingCollection=9a516d32) pub and the corresponding [GitHub repo](https://github.com/Arcadia-Science/2022-actin-prediction). In this analysis, we gathered a list of actins via a BLAST search for the top 50,000 proteins in the NCBI non-redundant (nr) database with no taxonomic constrictions. This list is used in the current analysis.

## Overview

To begin, visit the [ProteinCartography](https://github.com/Arcadia-Science/ProteinCartography) for a guide on running the pipeline. The notebooks used in this repo are designed to run alongside the ProteinCartography pipeline, so we recommend cloning the ProteinCartography pipeline before beginning.

You can find the data generated in the [Actin Prediction](https://github.com/Arcadia-Science/2022-actin-prediction) pipeline on [Zenodo](https://zenodo.org/records/7384393). This data is also included in the `Inputs` folder of this repository as `all_outputs_summarized.tsv`. 

The notebooks in this repository were created to help prepare the metadata, download AlphaFold structures, and apply additional custom overlays to the output map. 

### Set up directory structure

After cloning this repository and the ProteinCartography repository. You should set up your directory structure as follows: 

```
├── ProteinCartography
│   └── actin     # preparatory files and ProteinCartography run results end up here
├── 2023-actin-embedding
│   ├── notebooks     # notebooks should be in a folder
│   ├── input      # files from actin prediction get downloaded to here from Zenodo
│   └── output     # final pub figures end up here
```

### Prepare metadata

We prepared these proteins for use in the ProteinCartography pipeline using the `prep_metadata.ipynb` notebook.

### Download AlphaFold structures

Next, we downloaded all available AlphaFold sturctures using the `get_alphafold_structures.ipynb` notebook. 

### Run ProteinCartography "Cluster Mode"

We then ran the [ProteinCartography](https://github.com/Arcadia-Science/ProteinCartography) in "Cluster Mode" using the standard pipeline parameters. The complete analysis is linked in the Zenodo (LINK).

### Create custom plots

Finally, we combined the results of ProteinCartography with the results form the Actin Prediction pipeline in the `plotting_overlays.ipynb` notebook to create interactive plots. 
