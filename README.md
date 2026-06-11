# Lake Michigan Buoy and Environmental Data Analysis

Python notebooks and utilities for analyzing National Data Buoy Center (NDBC) 
data from buoys in southern Lake Michigan, with a focus on coastal upwelling 
events, lake breeze dynamics, wind and waves.

## Core Files

- `buoy.ipynb` — main analysis notebook
- `ndbc_io.py` — utilities for fetching NDBC realtime and historical data
- `gl_sst.ipynb` — data access and visualization for SST on the Great Lakes

## Dependencies

- pandas, numpy, matplotlib
- requests, lxml, xarray

## Data

Buoy data is fetched directly from the NDBC API and is not stored in this repository.

Great Lakes SST is fetched from the GLSEA via ERDDAP