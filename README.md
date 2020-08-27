# M.A.R.C.H. target data analysis — 2012 to 2017

This repository contains data, analytic code, and findings that support portions of the BuzzFeed News article, “[As Their Neighborhoods Grew Whiter and Wealthier, These Minority-Owned Businesses Found Themselves Targeted By Police](https://www.buzzfeednews.com/article/lamvo/gentrification-noise-complaints-police),” published August 27, 2020. Please read that article, which contains important context and details, before proceeding.

## Data

The analysis uses the following data sources:

### M.A.R.C.H. target data

[New York Police Department data on M.A.R.C.H. targeting, obtained and published by the New York City Artist Coalition](https://github.com/gltd/march/tree/master/data). The [`data/march_raids_with_lat.csv`](https://github.com/gltd/march/blob/master/data/https://github.com/gltd/march/blob/master/data/march_raids_with_lat.csv) spreadsheet lists the M.A.R.C.H. targets, with latitude and longitude coordinates added by Brian Abelson. The data was published in 2018 and contains potential M.A.R.C.H. raid targets from 2012 to 2017. Abelson told BuzzFeed News that it was unclear whether NYPD raided every address listed in the data and would not answer questions about the data.

### NYC 311 Data

The [`data/311_Service_Requests_from_2010_to_Present.csv`](data/311_Service_Requests_from_2010_to_Present.csv) spreadsheet lists complaints that were affiliated with the address of one specific bar featured in the story, Ode To Babel, obtained through [NYC's 311 data portal](https://nycopendata.socrata.com/Social-Services/311-Service-Requests-from-2010-to-Present/erm2-nwe9/data).

### Census tract shapefiles

BuzzFeed News downloaded shapefiles detailing the geographic boundaries and Census tracts for the state of New York, [from the Census Bureau’s website](https://www.census.gov/geographies/mapping-files/time-series/geo/carto-boundary-file.2018.html), saved in `data/censusTracts/states/`.

### Demographic data and gentrification measures

The [`data/gentrification.csv`](data/gentrification.csv) spreadsheet comes a previous BuzzFeed News [analysis](https://github.com/BuzzFeedNews/2020-02-gentrification/blob/master/output/gentrification.csv), which computed gentrification metrics for all Census tracts in Atlanta, Baltimore, New York, Oakland and Washington, DC. It includes the following relevant columns:

* `GEOID` — Census tract ID
* `total_population_17` — The tract’s total population in 2017
* `gentrified` — Whether the tract gentrified between 2000 and 2017
* `pct_white_alone_change` — Percentage-point change for population that was white alone
* `pct_black_alone_change` — Percentage-point change for population that was black alone
* `pct_native_alone_change` — Percentage-point change for population that was Native American
* `pct_asian_alone_change` — Percentage-point change for population that was Asian alone
* `pct_hispanic_or_latino_alone_change` — Percentage-point change for population that was Hispanic or Latino alone
* `pct_native_hawaiian_pacific_islander_change` — Percentage-point change for population that was Native Hawaiian or Pacific Islander
* `median_income_00` - the tract's median income in 2000
* `median_home_value_00` - the tract's median home value in 2000
* `median_income_17` - the tract's median income in 2017
* `median_home_value_17`- the tract's median home value in 2017

### Other Data

We used the [Bureau of Labor Statistics Inflation Calculator](https://www.bls.gov/data/inflation_calculator.htm) to find an inflation rate to adjust median incomes and median home values for inflation (values are in 2017 dollars and adjusted from January 2000 to January 2017). The [NYC Population FactFinder tool](https://popfactfinder.planning.nyc.gov/#14/40.67871/-73.95851) was used to identify a list of Census tracts that are adjacent to the tract where Friends and Lovers is located.

## Data analysis

The Python code for BuzzFeed News analysis, can be found in this repository's [`01-march-and-311-analysis.ipynb` notebook](notebooks/01-march-and-311-analysis.ipynb). In it, we conduct the following analyses:

- Identify M.A.R.C.H. listings in the area surrounding one of the bars mentioned in the story
- Count how often each address, in that area, occurs in the data
- Count the number of noise complaints, over time, affiliated with Ode to Babel's address

The notebook produces the following files:
* [`output/neighborhood_raids.csv`](output/neighborhood_raids.csv) — a list of all entries in the M.A.R.C.H. in the Census tracts of interest merged with demographic data
* [`output/neighborhood_target_list.csv`](output/neighborhood_target_list.csv) — a tally of how often each address shows up in the list of M.A.R.C.H. targets in the Census tracts of interest. This was information that was used to do on-the-ground reporting.
* [`output/noise_complaints_ode_to_babel.csv`](output/noise_complaints_ode_to_babel.csv) — a monthly aggregate of noise complaints related to the address where Ode to Babel is located

## Licensing

All code in this repository is available under the [MIT License](https://opensource.org/licenses/MIT). All data files in the output/ directory are available under the [Creative Commons Attribution 4.0 International](https://creativecommons.org/licenses/by/4.0/) (CC BY 4.0) license. All data files in the data/ directory are available, under their own terms, from the sources described above.

## Feedback / Questions?

Contact Lam Thuy Vo at lam.vo@buzzfeed.com.

Looking for more from BuzzFeed News? [Click here for a list of our open-sourced projects, data, and code.](https://github.com/buzzfeednews/)
