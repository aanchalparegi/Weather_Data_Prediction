---

# Weather Data Scraping: Sudbury, Ontario

## Project Overview

This project scrapes daily weather data for Sudbury, Ontario, from the **Meteostat** API. The data includes temperature, precipitation, wind speed, and more, covering the last five years (January 1, 2019, to December 31, 2023). The collected data is saved as a CSV file for analysis.

## Dataset

- **Location**: Sudbury, Ontario, Canada (Lat: 46.49, Lon: -80.99)
- **Time Frame**: January 1, 2019 - December 31, 2023
- **Columns**: `tavg`, `tmin`, `tmax`, `prcp`, `snow`, `wdir`, `wspd`, `wpgt`, `pres`, `tsun`, `time`

## Prerequisites

Install the required Python libraries:

```bash
pip install pandas meteostat
```

## How to Run the Script

1. Clone or download the repository.
2. Navigate to the project directory.
3. Run the script:

   ```bash
   python datamining_weather_data_prediction.py
   ```

4. Check the output in `sudbury_weather_data.csv`.

## Code Overview

The script fetches weather data using the Meteostat API and saves it as a CSV file:

```python
import meteostat
from meteostat import Point, Daily
import pandas as pd
from datetime import datetime

# Define location and time period
sudbury = Point(46.49, -80.99)
start = datetime(2019, 1, 1)
end = datetime(2023, 12, 31)

# Fetch and save data
weather_data = Daily(sudbury, start, end).fetch()
df = pd.DataFrame(weather_data)
df['time'] = pd.to_datetime(df.index)
df.to_csv('sudbury_weather_data.csv', index=False)
```

## Conclusion

This project provides a simple way to scrape and store weather data for Sudbury, Ontario, or any other city by adjusting the latitude and longitude, facilitating further analysis.


---
