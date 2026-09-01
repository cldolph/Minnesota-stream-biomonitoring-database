# Minnesota-stream-biomonitoring-database

Author: Christy Dolph

Updated: September 1, 2026

Contact: dolph008\@umn.edu

# Overview

This repository contains macroinvertebrate relative abundance data and associated environmental data for streams and rivers in Minnesota, compiled from local, state and federal sources. The repository consists of information for 2.6 million macroinvertebrate specimens from 765 taxa collected across 4,737 unique sites in Minnesota (7,706 total site visits, which include repeat visits to some sites). The database also contains R Markdown scripts used to process and analyze data.

Macroinvertebrate data was compiled from the following sources: U.S. Geological Survey (USGS), Environmental Protection Agency (EPA), Minnesota Pollution Control Agency (MPCA), Twin Cities Metropolitan Council, Carver County (MN), Dakota County Soil and Water Conservation District (MN), Anoka Conservation District (MN), Riley-Purgatory-Bluff Creek Watershed District (MN), Washington Conservation District (MN), Bassett Creek Watershed Management Commission (MN), Friends of the Mississippi River Stream Health Evaluation Program, Scott County Watershed Management Organization (MN), and Brown's Creek Watershed District (MN).

Most data was obtained by direct request to the relevant agency. USGS and EPA data compiled using the finsync package in R (<https://usepa.github.io/finsyncR/>; Mahon et al., 2024).

This effort was funded by the **Legislative-Citizen Commission on Minnesota Resources (LCCMR) under the grant "Impact of statewide conservation practices on stream biodiversity (ID: 2025-150).** <https://www.lccmr.mn.gov/projects/2025-index.html>

# Set Up & Installation

1.  Download `~/Minnesota-stream-biomonitoring-database.zip` to local file system.

2.  Unzip the files to a folder labeled `~/Minnesota-stream-biomonitoring-database`.

3.  Still in the local file system, open the `Minnesota-stream-biomonitoring-database_PRproj` file. This will open the project in RStudio and set the working directory to `~/Streambank_P`.

4.  All file paths within the scripts are relative.

# Datasets

Macroinvertebrate data was compiled from multiple sources, and received considerable cleaning and processing prior to compilation.

## Processed macroinvertebrate data

All of the fully processed macroinvertebrate data files are in the folder `Data/processed_taxonomic_datasets` (See below). This folder contains 3 separate files:

1)  `Genus_relative_abundance_rarified.xlsx` - contains information for all genus-level IDs in the dataset; specimens without at least a genus-level ID are omitted.

2)  `Family_relative_abundance_rarified.xlsx` - contains information for all family-level IDs in the dataset; specimens without at least a family-level ID are omitted.

3)  `MixedID_relative_abundance_rarified.csv` - contains information about all IDs in the dataset; no specimens are omitted, but note that this dataset contains "mixed" IDs (where specimens may be identified at various taxonomic resolutions; e.g., specimens IDed at a family level at one site may be identified at a genus level at another site.

For each of these datasets, specimens at each site are rarified to 300 individuals maximum (i.e., specimens are randomly selected from the original count to a maximum of 300 individuals).

Macroinvertebrate samples were collected with semi-quantitative methods (typically D-frame dipnets where an equal effort was applied at each site). Thus, the available data constitutes relative abundance at each site, not absolute abundance.

Taxonomic units were derived in the R Markdown file: `module_OTUs.Rmd` if you want to see more specific details of how data was assembled.

## Input Data

Files in the `Data/cleaned_input_data` folder represent intermediately-cleaned data (i.e., data processed into uniform columns), as well as ancillary data used to aid in the processing of taxonomic data in `module_OTUS.Rmd`.

## Environmental Data

Files in the `Data/environmental_data` folder include EPA StreamCat attributes (<https://www.epa.gov/national-aquatic-resource-surveys/streamcat-dataset>) attributes for all macroinvertebrate sampling locations in the dataset. EPA’s StreamCat dataset contains information for over 600 different environmental metrics linked to individual stream reaches in the NHDv2Plus dataset (Hill et al., 2015). These metrics summarize diverse geospatial attributes -- including aspects of land cover including land use, impervious surfaces and road density, soil type, point source and nutrient inputs, and climatic factors (temperature and precipitation), among others – at the catchment and watershed scale draining into each reach.

# R Markdown Scripts Used for Analysis

This repository contains the following R Markdown scripts:

- module_OTUs.Rmd - used to clean and process macroinvertebrate taxonomic information, with the output being the files in `Data/processed_taxonomic_datasets`

- module_environmental_variables.Rmd - used to compile StreamCat and NHD attributes for macroinvertebrate sampling locations

- module_data_processing_finsyncR.Rmd - used to download and process macroinvertebrate data from USGS and EPA using the finsyncR package (Mahon et al., 2024)

# Citations

Hill, R.A., Weber, M.H., Leibowitz, S.G., Olsen, A.R., Thornbrugh, D.J., 2015. The Stream-Catchment (StreamCat) Dataset: A Database of Watershed Metrics for the Conterminous United States. JAWRA Journal of the American Water Resources Association 52, 120–128. <https://doi.org/10.1111/17521688.12372>

Mahon, M.B., Jones, D.K., Hill, R.A., Brown, T.N., Brown, E.A., Kunz, S., Rumschlag, S.L. 2024. finsyncR, an R package to synchronize 27 years of fish and invertebrate data across the United States. bioRxiv doi: <https://doi.org/10.1101/2024.02.22.581615>
