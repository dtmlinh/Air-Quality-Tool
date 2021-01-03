# Chicago PM2.5 Levels
 
## Project Description
This [prototype tool](https://chicago-air-quality.herokuapp.com/) illustrates and compares 3 different PM 2.5 data sources, by day and neighborhood, in Chicago:

- ELPC community monitoring [data](https://airqualitychicago.org/)
- Environmental Protection Agency public air sample [data](https://aqs.epa.gov/aqsweb/documents/data_api.html)
- Purple Air self-reported [data](https://www2.purpleair.com/)

Contributors: Linh Dinh

## Objectives
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
Run shell script to launch a command-line utility that lets you interact with this Django project. 
```bash
$ ./run_software.sh
```
Adding `-d` will re-pull the data from web scraping and API. If this is run, newer data (up to 14 days ago from run date) will get pulled and appended to the master data files. 

Adding `-g` will recreate graphs from the master data files.

Once the interface is started, you can use it by pointing a browser to `http://127.0.0.1:8000/`.

## Structure of the software
1. Helper functions scripts:
    - `pipeline.py`: General helper functions to process, clean, and aggregate non-specific data.
    - `process_data.py`: Helper functions to process, clean, and aggregate air-quality-specific data (EPA, PurpleAir, AirQuality).
    - `plot_functions.py`: Helper functions to create visualizations from processed data.
    
2. Data collecting scripts:
    - `load_geo_files.py`: Retrieve relevant geo/shape files for Chicago. Store this data as .csv files in './data'. Utilize helper functions above.
    - `load_data_files.py`: Crawl EPA, PurpleAir, AirQuality and retrieve all relevant data. Then, combine this data with appropriate geo/shape files to create master data files. Store these master data files as .csv files in './data'. Utilize helper functions above. If this script is run, newer data (up to 14 days ago from run date) will get pulled and appended to the master data files. 

3. Data visualization/display scripts:
    - `create_visualizations.py`: Python script that creates all graphs used by the Django application. If run locally, all the graphs are created and saved in the “static/graphs” folder. Need to be rerun if the data is updated.
