# Air Quality and Sickle Cell Disease Analysis

## Project Overview

This project analyzes the associations between air pollutants and potential impacts on Sickle Cell Disease (SCD) patients in Durham County, North Carolina. The analysis processes EPA air quality data from the RDU airport monitoring station for the years 2018-2020.

## Background

Sickle cell disease (SCD) is a group of genetic disorders in which red blood cells contort into a sickle shape. There is evidence that exposure to air pollution aggravates vaso-occlusion and pain in SCD patients. This project examines daily measurements of three key pollutants:

- **CO** (Carbon Monoxide)
- **PM2.5** (Particulate Matter ≤ 2.5 micrometers)
- **O3** (Ozone)

## Repository Structure

```
project/
│
├── AQ_2018.csv                    # Air quality data for 2018
├── AQ_2019.csv                    # Air quality data for 2019
├── AQ_2020.csv                    # Air quality data for 2020 (through April)
├── project2.Rmd                   # Main RMarkdown analysis file
├── project2.docx                  # Knitted Word document output
└── README.md                      # This file
```

## Data Description

The raw data files contain daily measurements from the EPA air quality monitor at RDU airport:

- **Date**: Date of measurement (MM/DD/YYYY format)
- **Daily Max 8-hour CO Concentration**: Maximum 8-hour carbon monoxide concentration (ppm)
- **Daily Mean PM2.5 Concentration**: Mean particulate matter concentration (μg/m³)
- **Daily Max 8-hour Ozone Concentration**: Maximum 8-hour ozone concentration (ppm)

### Data Quality Issues

The raw data contains several issues that are addressed in the processing function:

- Multiple measurements per day for some pollutants
- Duplicate rows
- Negative concentration values (measurement errors)
- Missing data (NA values)
- Inconsistent date formatting

## Methods

### Data Processing Function

The `process_air_quality()` function performs the following operations:

1. **Renames variables** to shorter, more informative names without spaces
2. **Formats dates** using `lubridate::mdy()`
3. **Handles negative values** by setting them to zero (measurement error correction)
4. **Calculates daily averages** for days with multiple measurements
5. **Removes duplicates** through grouping and summarization

### Analysis

The analysis includes:

- Summary statistics for all three pollutants across the study period
- Monthly trend analysis averaged over all years
- Year-by-year comparison of pollutant patterns
- Visualization with 95% confidence intervals

## Key Findings

### Seasonal Patterns

- **CO**: Relatively stable throughout the year with slightly elevated concentrations in winter months
- **O3**: Clear summer peaks (June-August), consistent with increased photochemical activity in warmer weather
- **PM2.5**: Variable patterns with generally higher concentrations in cooler months

### Temporal Trends

- 2020 data (available through April only) shows relatively lower PM2.5 levels compared to 2018-2019, potentially reflecting reduced human activity during the early COVID-19 pandemic period

## Requirements

### R Version
- R version 4.0.0 or higher recommended

### Required Packages

```r
install.packages(c("tidyverse", "lubridate", "knitr"))
```

- **tidyverse**: Data manipulation and visualization
- **lubridate**: Date/time handling
- **knitr**: Document generation

## Usage

1. Clone this repository to your local machine
2. Ensure all CSV files are in the project directory
3. Open `project2.Rmd` in RStudio
4. Install required packages (see Requirements section)
5. Click "Knit" to generate the Word document

Alternatively, run from the R console:

```r
rmarkdown::render("project2.Rmd")
```

## Outputs

The analysis produces:

1. **Word Document** (`project2.docx`): Complete analysis report with:
   - Summary statistics table
   - Plot 1: Monthly average CO and O3 concentrations with 95% CI
   - Plot 2: Monthly PM2.5 concentrations by year
   - Interpretations and conclusions

## Author

**Haruma Kurita**  
Duke University  
Course: BIOSTAT721
Date: November 15, 2025

## License

This project is submitted as coursework for BIOSTAT721 at Duke University.

## Contact

For questions or feedback, please contact: haruma.kurita@duke.edu
