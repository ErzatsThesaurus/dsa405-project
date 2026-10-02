# dsa405-project

## What this project is

This project seeks to determine what coloration exists between the price of electricity and the weather. It does this by analyzing monthly data from two federal agencies, NOAA and FRED. The data dates back to 1978.

# Where the data came from

Both raw files are in `data/raw/` and are never modified.

| File | What it is | Source | Retrieved |
|---|---|---|---|
| `noaa_tavg_raw.json` | Average monthly temperature for the contiguous U.S., in degrees Fahrenheit, Jan 1978 to Aug 2026 | NOAA National Centers for Environmental Information, Climate at a Glance: https://www.ncei.noaa.gov/access/monitoring/climate-at-a-glance/ | September 3 |
| `APU000072610.xlsx` | Average monthly price of electricity per kilowatt-hour, U.S. city average, in dollars, Nov 1978 to Jul 2026 | U.S. Bureau of Labor Statistics, downloaded from FRED: https://fred.stlouisfed.org/series/APU000072610 | 2026-09-03 |

Full download details are in `data/raw/SOURCES.md`.


# How to run it

1. Open `DSA405_P2_pdcurry_FA26_md.ipynb` and click the "Open in Colab" button at the top.
2. Choose Runtime, then Run all.

Nothing needs to be downloaded or installed. The notebook reads the data
directly from this repository.
