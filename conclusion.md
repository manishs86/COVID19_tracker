## Introcution 
COVID19_Tracker is an interactive dashboard build in `python` and `Dash` with charts made with `plotly` to track the covid cases in the United States. The dashboard deployed to `Heroku` Paas platform for easy access and sharing. 

## Installation $ running
- `git clone` or fork the repo
- `cd COVID19_tracker` 
- Activate the virtualenv `source dev/bin/activate`
- Install the dependencies `python3 pip install -rrequirements.txt upgrade pip`
- Run the application from the `app.py` entry point.

## Why it is important
Covid had changed our personal lives dramatically. One of the significant changes within the lifestyle is the way of how we keep ourselves safe. So, it become essential to track the spread of the virus across the nation. From this aspect, it is important to compare the upto date numbers with the previous day to correctly judge the situation. Additionally, it would be good to see which state across the nation has a good control over the virus spread by looking over the trajectory chart. 

## Main Features
The dashboard has 5 main componets:
- Indicators show current cases and the increase/decrease from the day before.

    - CUMULATIVE CONFIRMED is the running total of all cases tested and confirmed in the selected region. (Note: This value is highly dependent upon the testing rate and almost certainly is an underestimate of actual infections.)
    - CURRENTLY ACTIVE measures only the cases active today.
    It is calculated as `ACTIVE = CONFIRMED - DEATHS - RECOVERED`
    - DEATHS TO DATE measures the running total of all COVID-19-related deaths
    - RECOVERED CASES is the number of cases in which the patient is deemed to have recovered from the illness and is no longer infected nor contagious.

- The infections rate for selected region

    The cases graphic displays a line chart by sub-region of either `CONFIRMED`, `ACTIVE`, `RECOVERED`, or `DEATHS`, selectable with the radio buttons below the chart. The sub-regions are the states or provinces; on hover, the exact count of the selected metric is displayed for the sub-region the mouse is over.

    By default, it displays sub-regions which were of particular interest when this dashboard was created. The dropdown-bar on the bottom allows you to select different sub-regions for display. Typing in the dropdown-bar will allow you to search for sub-regions.

- Case analysis by sub-region
    There are two regional charts. These charts can display absolute infection numbers within a region, or numbers relative to the region's population. Selecting the radio button for Values per `100,000 of population` normalizes each curve by population and can make it easier to compare the infection rates of regions with vastly different population counts. Selecting Total values returns the charts to absolute numbers.

- Infection map

    The infection map features a circular marker over each sub-region. The size of the marker is relative to the square root of the `CONFIRMED` cases within that sub-region and the color indicates the percentage of those cases which were newly confirmed within the previous 7 days. Essentially, the size of the marker is a measure of how many people have caught the virus within that sub-region since the outbreak began. The color is a measure of how active the virus currently is, with dark red indicating the virus is actively spreading and white indicating that it is more under control. Hovering over a marker will reveal the state name and the exact value of the two measures. As with the other charts, the map is zoomable and dragable. By default it is set for the most recent date available but by dragging to the left you can see the spread of the pandemic through time.

- The trajectory chart 

    This chart displays the trajectory of the pandemic within sub-regions. The x-axis displays the cumulative confirmed count by sub-region and the y-axis displays the count of cases which were confirmed in the previous week. With this visualization, once a sub-region has managed to control the pandemic to some extent, the line should suddenly drop down. Although date is not on either of the axes, the data is still plotted by date; hovering over any line will display the date on which that data point was recorded. Additionally, the date slider on the bottom also controls this chart; so along with the map, the progress throughout time of the trajectories can be inspected.

## Project workflow:
- Data source: 
    The data was collected from the [Johns Hopkins Center for Systems Science and Engineering](https://github.com/CSSEGISandData/COVID-19). scrapping the data from the public repo and download it was challenging where I had to scrape the data and cases per day store them as time series then processing. However, this step was mandatory to be able to calculate a more reliable indicators.

-  Data Preparation: 
    - The data per day cases was merged into tables `confirmed`, `active`,etc.
    - Join tables into one `pandas` dataframe preparing for visualization. 
    - Remove dulpicates in the states names
    - Fill missing values with `pd.fillna(0)`
    - Replace missing values for latitude and longitude
    - Create Active cases column
    - Manually change some country centroids which are mislocated due to far off colonies
    - Only keep county-level data for previous 8 days for share_of_last_week
    - Calculate the US population projected from 2010 Census
