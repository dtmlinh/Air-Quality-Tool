# Chicago PM2.5 Project
 
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
`requirement.txt` contains the required packages to run our program.


### Running a command in your environment

Run shell script to launch a command-line utility that lets you interact with this Django project. 
```bash
$ python3 manage.py runserver
```
Once the interface is started, you can use it by pointing a browser to `http://127.0.0.1:8000/`.

## Results
More detailed (but also preliminary) analysis results can be found [here](https://dtmlinh.github.io/bio/blog/2020/11/02/blog-post)

