# Great Lakes Environmental Data Analysis: Satellite and Buoy Data 

An open-source Python toolkit for programmatically fetching, processing, and visualizing meteorological and oceanographic data across the Great Lakes. This repository combines in-situ observations from the National Data Buoy Center (NDBC) API with high-resolution satellite gridded data from NOAA CoastWatch ERDDAP servers to analyze coastal upwelling events, lake breeze dynamics, surface water temperatures, wind, and waves.

## Project Overview

Analyzing complex coastal dynamics requires blending distinct environmental data streams. This project provides a localized, programmatic workflow that eliminates the need for manual, high-bandwidth data downloads by slicing and streaming data directly into memory.

The core analytical pipeline covers:
* **In-Situ Buoy Diagnostics:** Automating real-time and historical data extraction from NDBC stations in southern Lake Michigan to track micro-climate indicators like wind stress and wave heights.
* **Remote Data Slicing:** Building precise, dimension-aware REST queries for the NOAA Great Lakes Environmental Research Laboratory (GLERL) ERDDAP server.
* **Multidimensional Data Ingestion:** Streaming NetCDF (`.nc`) grids straight into Xarray datasets without local manual file assembly.
* **Coordinate Conversion:** Translating raw, numeric NetCDF time offsets into standard Python datetime objects for seamless downstream plotting.
* **Geospatial Mapping:** Correcting unprojected Geographic Coordinate System (GCS) stretching with adaptive aspect ratios to accurately plot physical lake features.

## Scientific Data Products

This analysis cross-references real-time station instrumentation with regional satellite environmental grids:
* **NDBC Station Telemetry:** In-situ measurements capture high-frequency physical transitions (e.g., rapid water temperature drops indicating coastal upwelling or sharp wind direction shifts signaling a lake breeze).
* **GLSEA (Great Lakes Surface Environmental Analysis):** A daily gridded map showing surface water temperature and ice cover of the Great Lakes, combining cloud-free satellite observations with a transition model.
* **ACSPO (Advanced Clear-Sky Processor for Oceans):** The underlying NOAA processing algorithm that translates raw infrared data from polar-orbiting and geostationary satellites into highly accurate sea surface temperatures (SST).
* **GCS (Geographic Coordinate System):** An unprojected, ellipsoidal grid layout utilizing decimal degrees (Latitude/Longitude) rather than a projected plane, allowing for rapid coordinate bounding and subsetting.

## Core Repository Architecture

The workspace is organized into modular notebooks and data access scripts:

* `buoy.ipynb` — The primary analysis notebook focusing on southern Lake Michigan buoy dynamics, upwelling events, and wind/wave relationships.
* `ndbc_io.py` — A dedicated utility module containing custom functions for fetching and parsing raw NDBC real-time and historical text streams.
* `gl_sst.ipynb` — The secondary data access and visualization notebook detailing API integrations, spatial bounding box arrays, and interactive Xarray/ERDDAP dataset exploration.
* `.gitignore` — Pre-configured to ignore local cache outputs, system variables, and local NetCDF binary slices (`*.nc`).

## Getting Started

### Prerequisites

This project relies on the standard Python scientific data ecosystem. Ensure you have the following third-party libraries installed:

```bash
pip install pandas numpy matplotlib requests lxml xarray netCDF4