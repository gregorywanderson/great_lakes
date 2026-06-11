# Great Lakes Environmental Data Analysis

Python notebooks for fetching, processing, and visualizing satellite and buoy
data over the Great Lakes, with a focus on southern Lake Michigan. The notebooks
look at coastal upwelling, lake breezes, surface water temperature, and clouds —
combining in-situ buoy observations (NDBC), gridded satellite SST (NOAA CoastWatch /
GLERL via ERDDAP), and GOES-East satellite imagery.

## Notebooks

- **`gl_sst.ipynb`** — Surface water temperature from the GLSEA gridded product.
  Builds ERDDAP requests, loads NetCDF into xarray, maps daily and averaged SST,
  and animates day-to-day SST anomalies to spot upwelling events.

- **`goes_cloud_animation.ipynb`** — A configurable pipeline that downloads
  GOES-East ABI imagery, renders each scan over a chosen region, and assembles
  the frames into an animation. Used here to look for lake-breeze cloud signatures,
  but the machinery works for any mesoscale cloud phenomenon.

- **`buoy.ipynb`** — Buoy diagnostics for southern Lake Michigan: wind, waves,
  and water-temperature drops associated with upwelling and lake breezes.

## Supporting files

- **`ndbc_io.py`** — Helper functions for fetching and parsing NDBC buoy text feeds.
- **`images/`** — Saved figures and animations.
- **`.gitignore`** — Ignores cached downloads and local NetCDF slices (`*.nc`).

## Data sources

- **GLSEA / ACSPO** — Daily gridded Great Lakes surface temperature (NOAA GLERL),
  derived from polar-orbiting satellite infrared via the ACSPO algorithm.
- **NDBC** — Real-time and historical buoy observations.
- **GOES-East ABI** — Geostationary satellite imagery, accessed with `goes2go`.

## Getting started

### Setup

**Recommended (conda):** this installs cartopy and the NetCDF libraries cleanly,
which is the easiest path on Windows.

```bash
conda env create -f environment.yml
conda activate great_lakes
```

**Alternative (pip):**

```bash
pip install -r requirements.txt
```

### Running the notebooks

Open any notebook and run the cells top to bottom. Each notebook sets its case
date, region, and parameters in a configuration cell near the top — change those
to retarget it to a different event or area.

New here? Start with `buoy.ipynb` — it begins by fetching and plotting buoy
observations (a gentle introduction), then builds toward wind roses and
statistical fits in later sections.

