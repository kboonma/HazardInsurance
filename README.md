# Thailand Rainfall Intensity Viewer

This project provides a lightweight, client-side tool to explore rainfall intensity-duration-frequency (IDF) data for Thailand. The map loads a cropped subset of the BURGER dataset and lets you interactively inspect grid values, visualize different duration/return-period combinations, and analyze return-period profiles at individual locations.

## Features
- Interactive Leaflet map with 0.1° rainfall grid coverage over Thailand.
- Duration and return-period selectors with instant updates across 80 IDF layers.
- Layer control for rainfall grid, rain gauges, and river basins (GRRR) overlays.
- Rain gauge and river popups that update the sidebar chart and display the relevant mm/hr or m³/s value.
- Custom canvas chart with hover tooltips for return-period profiles.
- Searchable lat/lon lookup, cell highlighting, and adjustable rainfall opacity.

## Data
The viewer expects the following datasets in the same directory:
- `BURGER_1.0_thailand.json` – sub-daily rainfall intensities (1–24 hour durations, 2–10,000 year return periods) over Thailand at 0.1° resolution.
- `thailand_gauge_IDF.csv` – point-based IDF estimates for rain gauges across Thailand (mm/hr).
- `GRRR_thailand_river_discharge_rps.json` – Google Runoff Reanalysis & Reforecast (GRRR) river discharge return periods (m³/s).

### Citation
Please credit the underlying datasets when sharing results:
- Hoch, J. (2025) “BURGER - A bottom-up regionalization approach for global sub-daily intensity-duration-frequency data”, *Water Resources Research*. Zenodo. [https://doi.org/10.5281/zenodo.15473689](https://doi.org/10.5281/zenodo.15473689)
- Yamoat, N. et al. (2023) “Estimation of regional intensity–duration–frequency relationships of extreme rainfall by simple scaling in Thailand.” *Journal of Water and Climate Change*. [https://doi.org/10.2166/wcc.2023.430](https://doi.org/10.2166/wcc.2023.430)
- Google Runoff Reanalysis & Reforecast (GRRR) dataset notebook. [https://colab.research.google.com/drive/1FnXXSEQqU1TJhMPiNeWUTr9LnbJwZzMm?usp=sharing#scrollTo=UTbokLLWp_9o](https://colab.research.google.com/drive/1FnXXSEQqU1TJhMPiNeWUTr9LnbJwZzMm?usp=sharing#scrollTo=UTbokLLWp_9o)

### Licensing
The dataset is distributed under [CC BY-NC-SA 4.0](https://creativecommons.org/licenses/by-nc-sa/4.0/). Please review the license before commercial use.

## Usage
1. Ensure `index.html`, `BURGER_1.0_thailand.json`, `thailand_gauge_IDF.csv`, and `GRRR_thailand_river_discharge_rps.json` reside in the same folder.
2. Serve the directory (e.g. `python -m http.server`) and visit `http://localhost:8000/`.
3. Select a rainfall duration and return period; hover or click the rainfall grid to inspect values.
4. Use the layer control to toggle rainfall grid, rain gauges, and river basins.
5. Click a gauge or river marker to update the sidebar chart with the corresponding IDF/discharge profile.
6. Use the opacity slider, search box, and chart tooltips for deeper analysis.

## Dependencies
The UI is entirely client-side and references CDN-hosted libraries:
- Leaflet for mapping
- Chroma.js for colour scaling

Custom canvas rendering is used for the sidebar chart, so no additional charting library is required. No build tooling is required; simply serve the folder and explore.
