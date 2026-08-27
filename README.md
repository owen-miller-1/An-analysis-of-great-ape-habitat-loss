# The plight of great apes: An analysis of great ape habitat loss
![Python](https://img.shields.io/badge/PYTHON-3776AB?style=for-the-badge&logo=python&logoColor=white)
![GeoPandas](https://img.shields.io/badge/GEOPANDAS-139C5A?style=for-the-badge)
![Rasterio](https://img.shields.io/badge/RASTERIO-CC5500?style=for-the-badge)
![Plotly](https://img.shields.io/badge/PLOTLY-3F4F75?style=for-the-badge&logo=plotly&logoColor=white)
![Folium](https://img.shields.io/badge/FOLIUM-77B829?style=for-the-badge&logo=leaflet&logoColor=white)
![Quarto](https://img.shields.io/badge/QUARTO-4E9C81?style=for-the-badge&logo=quarto&logoColor=white)

## 📊 [Read the full analysis](https://019fd814-974a-9d9c-98af-ba485ec47718.share.connect.posit.cloud/)

## Overview
This project examines 25 years (2001-2025) of satellite-derived tree cover loss across the core range of non-human great apes: orangutans, gorillas, chimpanzees and bonobos. It spans 13 countries across equatorial Africa and Southeast Asia. The analysis combines Hansen Global Forest Change data, WDPA protected area boundaries, and IUCN species ranges to quantify how much great ape habitat is contained within protected areas, and whether protection is associated with reduced forest loss.

**Key findings**: 
- Great ape range countries lost approximately 84 million hectares of tree cover between 2001 and 2025, equivalent to 11.8% of forest extent in 2000
- Only about a fifth (19.8%) of mapped great ape range falls within protected area boundaries
- Forest loss was substantially lower inside protected areas: roughly 63% lower in Africa and 73% lower in Asia

The full geospatial pipeline, including raster processing, protected area effectiveness and interactive visualizations, is available in this repository, with technical documentation contained in [`notebooks/Great_ape_habitat_loss_documentation.ipynb`](./notebooks/Great_ape_habitat_loss_documentation.ipynb).

## Data sources
- **Forest cover and forest cover loss:** [Hansen Global Forest Change dataset](https://storage.googleapis.com/earthenginepartners-hansen/GFC-2025-v1.13/download.html) (GFC-2025-v1.13), 10% canopy cover threshold
- **Great ape ranges:** [IUCN Red List of Threatened Species](https://www.iucnredlist.org/resources/spatial-data-download) spatial data (2024 release)
- **Protected areas:** [Protected Planet World Database on Protected Areas (WDPA)](https://www.protectedplanet.net/en/thematic-areas/wdpa), UNEP-WCMC and IUCN (2026 release); excludes areas with `STATUS` of "Proposed"
- **Country boundaries:** [Natural Earth](https://www.naturalearthdata.com/downloads/10m-cultural-vectors/), 1:10,000,000 scale Admin 0 countries dataset, used to assign each great ape range polygon to a country

## Repository structure
```
An-analysis-of-great-ape-habitat-loss/
├── Great Ape Conservation Script.qmd   # Main Quarto document (source for the published analysis)
├── README.md
├── requirements.txt
├── references.bib                      # Full source citations
├── .gitignore
│
├── data/                                # All source and processed data (CSVs, shapefiles)
│   ├── Ape_ranges.shp
│   ├── PAs_within_ape_ranges.shp
│   ├── ne_10m_admin_0_countries.shp
│   ├── Forest_data.csv
│   ├── pa_coverage_by_country.csv
│   ├── pa_effectiveness_by_country_combined.csv
│   └── Hansen_Spatial/                  # Raw Hansen GFC tiles (not included — see Data sources)
│
├── notebooks/
│   └── Great_ape_habitat_loss_documentation.ipynb   # Full methodology and pipeline walkthrough
│
├── archive/                             # Exploratory or superseded files, not used by current pipeline
│
└── Images/                              # Static images used in the QMD (silhouettes, donation logos)
```
## Reproducing this analysis

```bash
git clone https://github.com/owen-miller-1/An-analysis-of-great-ape-habitat-loss.git
cd An-analysis-of-great-ape-habitat-loss
pip install -r requirements.txt
quarto render "Great Ape Conservation Script.qmd"
```

**Note on raw data:** the Hansen GFC forest-loss tiles used in the rasterio pipeline (`data/Hansen_Spatial/`) are not included in this repository due to file size. See [Data sources](#data-sources) for download links. Without these tiles, the QMD will still render using the pre-computed summary CSVs already included in `data/` (`pa_effectiveness_by_country_combined.csv`, `pa_coverage_by_country.csv`, `Forest_data.csv`) — only the raw tile processing step in the documentation notebook requires the tiles themselves.

## About me 
I’m currently working with the Multilateral Fund Secretariat, an entity of the United Nations Environment Programme, in Montreal. I have an academic background in environmental science and public policy, and a profound connection to great apes. I’m always looking to broaden my network. Find me on [LinkedIn](https://www.linkedin.com/in/owen-miller1999/).
