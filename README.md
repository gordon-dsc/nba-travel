# NBA Travel, Rest, and Performance Data 

## Project Overview

This project looks at how travel and rest may relate to NBA player performance during the
2024–2025 NBA season. Using a reproducible data pipeline, this project makes clean,
analysis ready tables that have player game logs, geographic information, and city rankings.

The units of analysis for the main dataset is one row per player per game. Player performance is
looked at using points per minute played and schedule related factors, like days of rest
and back-to-backs. Geographic info is added using city location data and latitude/longitude coordinates.

The workflow of the project focuses on three NBA players of different calibers:
- Jayson Tatum
- Dejounte Murray
- Quentin Grimes

The pipeline is designed to be applied to league analysis with additional player
game logs.
## Software and Platform
- macOS Sequoia 15.6.1
- R (version 4.x)
- RStudio
- Git and GitHub
### R Packages
- tidyverse
- lubridate
- janitor
- here
- rvest
- httr2
- jsonlite
## Documentation Map
project/
├── README.md
├── data/
│ ├── imported_data/
│ │ ├── tatum_game_log_raw.rds
│ │ ├── murray_game_log_raw.rds
│ │ ├── grimes_game_log_raw.rds
│ │ ├── team_cities_raw.rds
│ │ └── worlds_best_cities_raw.rds
│ └── cleaned_data/
│ ├── games_final_clean.rds
│ ├── games_with_location_clean.csv
│ └── worlds_best_cities_clean.csv
├── scripts/
│ ├── import.qmd
│ └── cleaning.qmd
├── output/
│ ├── games_final.csv
│ ├── games_with_location.csv
│ ├── worlds_best_cities.csv
│ └── metadata/
│ ├── games_final_source.txt
│ ├── games_final_codebook.txt
│ ├── games_with_location_source.txt
│ ├── games_with_location_codebook.txt
│ ├── worlds_best_cities_source.txt
│ └── worlds_best_cities_codebook.txt




## Instructions for Reproducing the Data

To reproduce the final datasets from raw data, follow these steps:

1. Clone this repository and open it as an RStudio project.

2. Run the script:
scripts/import.qmd
- scrapes player game logs via Basketball Reference
- imports team city information
- scrapes city ranking data from World’s Best Cities 
- saves all uncleaned data to `data/imported_data/`

3. Run the script:
scripts/cleaning.qmd
This script:
- cleans and combines game logs
- computes performance and rest stats
- adds city, state, latitude, and longitude using the OpenStreetMap API
- cleans city ranking data
- writes three final datasets to `output/` 

4. The following files are created:
- `output/games_final.csv`
- `output/games_with_location.csv`
- `output/worlds_best_cities.csv`

Each output file is accompanied by a source file and codebook located in
`output/metadata/`.





