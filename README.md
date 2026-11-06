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


# P3: Acquisition, join, verification

**Notebook:** `DSA405_P3_pdcurry_FA26.ipynb` (Restart runtime, then Run all)
### Acquisition behavior
Honest User-Agent naming the coursework, 2 s pause between real requests, 20 s timeout, up to 3 retries on timeouts and 429/5xx, a content check before anything is saved (data present, correct month, no -99 values), and rate-limit headers read from each response. A failed or malformed response stops the code with an error and saves nothing.

### Join
NOAA left-joined to price on `date` (first of month), `validate="one_to_one"`. Expected rows = rows in NOAA. NOAA months with no price stay with price = NaN. Price months with no NOAA row would be dropped and counted.

### Verification
`verify()` checks row count, value ranges (temperature 15-85 °F, price $0.01-$1.00 per kWh), and month uniqueness.

### Attribution
- U.S. Bureau of Labor Statistics, Average Price: Electricity per Kilowatt-Hour in U.S. City Average [APU000072610], retrieved from FRED, Federal Reserve Bank of St. Louis.
- NOAA National Centers for Environmental Information, Climate at a Glance: National Time Series.
