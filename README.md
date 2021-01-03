# Chicago PM2.5 Levels
 
## Project Description
This [prototype tool](https://chicago-air-quality.herokuapp.com/) illustrates and compares 3 different PM 2.5 data sources, by day and neighborhood, in Chicago:

- ELPC community monitoring [data](https://airqualitychicago.org/)
- Environmental Protection Agency public air sample [data](https://aqs.epa.gov/aqsweb/documents/data_api.html)
- Purple Air self-reported [data](https://www2.purpleair.com/)

Contributors: Linh Dinh

## This tool aims to:
- illustrate the trends of PM 2.5 measurements in the Chicago area for 4 summers: 2017, 2018, 2019, 2020
- identify days where the discrepancies (in terms of PM 2.5 levels) between AirQuality, EPA, and PurpleAir data are significant and locate the neighborhoods where these discrepancies might be coming from
- provide a more detailed view into specific neighborhoods, more specifically:
  + locate blocks with much higher average PM 2.5 levels
  + identify hours/time periods with much higher average PM 2.5 levels

## Results
More detailed (but also preliminary) analysis results can be found [here](https://dtmlinh.github.io/bio/blog/2020/11/02/blog-post)

## Usage
## Online Access
The program was packaged and uploaded online to be accessed [here](https://chicago-air-quality.herokuapp.com/).
![alt-text](image/state_energy_search.gif)

## Local Access
### Activating your environment
To install the required packages in a new environment:
```bash
$ python3 -m venv env
$ source env/bin/ac
$ pip install -r requirements.txt
```
`requirement.txt` contains the required packages to run this program.

### Running a command in your environment
Run this command-line to interact with this Django application. 
```bash
$ python3 manage.py runserver
```
Once the interface is started, you can use it by pointing a browser to `http://127.0.0.1:8000/`.

## Structure of the software
1. Data collecting and schema building scripts:
    - `webscraper.py`: Scrapes 2017 data from EIA website on on [energy consumption by source] (https://www.eia.gov/state/seds/seds-data-complete.php?sid=US). The script crawls the index page and retrieves the datasets of interest for year 2017. The relevant datasets are then saved in the “data” folder.
    - `pull_api.py`: Leverages EIA’s API to retrieve trend data for a longer time period (1960 - 2017), which is not available in a web page format. The relevant datasets are saved in the “data” folder.
    - `db.sql`: sql file that converts data retrieved from web scraping and API into a sql3.lite database.

2. Data visualization/display scripts:
    - `make_2017_graph.py`: Python script that creates graphs showing the total energy consumption pattern by state in 2017. All the graphs are created and saved in the “static/graphs” folder. When a user selects a state, we’ll find the correct path of the state’s graph to display.
    - `make_1960_2017_graph.py`: Python script to create graphs showing the total energy consumption pattern by state for 1960-2017. All the graphs are created and saved in the “static/graphs” folder. When a user selects a state, we’ll find the correct path of the state’s graph to display.
    - `make_2017_table.py`: Python script that queries data on the total energy consumption pattern by state in 2017 from the database we created above. Convert the data into a formatted table to be displayed when a user selects a state.
