# COVID19 TRACKER 

[Live Demo](https://covid-tracker-states.herokuapp.com/)

## Introduction
COVID19_Tracker is an interactive dashboard build in `python` and `Dash` with charts made with `plotly` to track the covid cases in the United States. The dashboard deployed to `Heroku` Paas platform for easy access and sharing. 


## Installation $ running
- `git clone` or fork the repo
- `cd COVID19_tracker` 
- Activate the virtualenv `source dev/bin/activate`
- Install the dependencies `python3 pip install -rrequirements.txt upgrade pip`
- Run the application from the `app.py` entry point.

## Dashboard Main Features
To design a well communicative dashboard, we need to identify the major features we may include. Some of the preliminary features would be:
1. Indicators 
2. The infections rate for selected region.
3. Case analysis by sub-region
4. Infection map
5. The trajectory chart 

## The data source used for that project
For this project, I would rely on the data that most news used from the [Johns Hopkins University Center for Systems Science and Engineering](https://github.com/CSSEGISandData/COVID-19). I intend to use the [COVIDTracking](https://covidtracking.com/) repository, where it has the features I need to build the dashboard. 

## The Tech Stack
- Python 3.7.6 backend
- Dash plotting
- Heroku for deployment


