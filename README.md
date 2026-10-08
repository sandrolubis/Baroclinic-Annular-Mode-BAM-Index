# Baroclinic Annular Mode (BAM) Indices (1979–2020)

This repository provides daily principal component (PC) time series of the first three empirical orthogonal function (EOF) modes of zonal-mean eddy kinetic energy (EKE) for the Northern Hemisphere (NH) and Southern Hemisphere (SH) during 1979–2020.

## Methodology

The BAM is defined separately for each hemisphere as the leading EOF of zonal-mean EKE over 20°–70° latitude and 1000–200 hPa (Thompson & Woodworth, 2014).

The seasonal cycle is removed, and the data are weighted by √cos(φ), where φ is latitude. For NH BAM, zonal wavenumbers less than 4 are removed from the wind fields before calculating EKE to exclude planetary-scale wave contributions (Thompson & Li, 2015).

Positive and negative BAM events are identified using a 5-day smoothed BAM index exceeding ±1 standard deviation.

## Data Files

- `pc.eke_NH_1979_2020.nc` — Northern Hemisphere
- `pc.eke_SH_1979_2020.nc` — Southern Hemisphere

Each NetCDF file contains daily PC time series with dimensions `pc(evn, time)`.

| Dimension | Description |
|---|---|
| `evn=1` | PC1: Baroclinic Annular Mode (BAM) |
| `evn=2` | PC2: Second EOF mode |
| `evn=3` | PC3: Third EOF mode |
| `time` | Daily time steps (1979–2020; 15,341 days) |

## Python Example

```python
import xarray as xr

ds = xr.open_dataset("pc.eke_NH_1979_2020.nc")

bam = ds.pc.isel(evn=0)  # BAM (PC1)
pc2 = ds.pc.isel(evn=1)  # PC2
pc3 = ds.pc.isel(evn=2)  # PC3
```

## Citation

If you use these BAM indices in your research, please cite:

Lubis, S. W., Leung, L. R., & Battalio, J. M. (2026). **More Frequent Atmospheric Rivers and Associated Precipitation Extremes Induced by the Baroclinic Annular Mode.** *Geophysical Research Letters* (Accepted).

## References

- Thompson, D. W. J., & Woodworth, J. D. (2014).
- Thompson, D. W. J., & Li, Y. (2015).
