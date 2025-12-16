# Step 1: Data acquisition and preprocessing

This project relies exclusively on publicly available datasets.
Due to data volume, raw remote sensing and climate datasets are not redistributed.

## NDVI (GeoTIFF input)
- Product: MODIS MOD13A1 NDVI
- Temporal resolution: 16-day
- Spatial resolution: 1 km
- Processing steps:
  1. Aggregate 16-day NDVI to annual NDVI using maximum value composite (MVC)
  2. Reproject all layers to WGS84 (EPSG:4326)
  3. Resample to a 0.05° grid
  4. Export annual NDVI as GeoTIFF

## Climate variables
- CRU TS v4.08: temperature (TEM), precipitation (PRE), potential evapotranspiration (PET)
- ERA5-Land: shortwave radiation
- Processing:
  - Convert monthly data to annual means or totals
  - Resample to 0.05° using bilinear interpolation
  - Export as GeoTIFF

## Topography and land surface
- DEM: SRTM
  - Derive slope and aspect
  - Resample to 0.05°
- Soil: HWSD v2.0 (categorical, nearest-neighbor resampling)
- Land cover: GLC-SHARE (categorical, nearest-neighbor resampling)

## Masking
- Water bodies and built-up areas are excluded prior to analysis.

The processed GeoTIFF layers are used as inputs for the analysis workflow.
