# Module 6: CME and GST Data Analysis Project

## Overview
This project extracts and analyzes data from NASA's API about Coronal Mass Ejections (CMEs) and Geomagnetic Storms (GSTs). The goal is to prepare a dataset for a prediction system that will help the NOAA Space Weather Prediction Center forecast geomagnetic storms by calculating the average time it takes for a CME to cause a GST.

## Background
Coronal Mass Ejections (CMEs) are massive bursts of plasma emitted from the Sun at irregular intervals. When these ejections interact with Earth's magnetic shield, they can cause Geomagnetic Storms (GSTs), which may be harmful to electronic devices such as satellites, GPS systems, and power grids. Understanding the relationship between CMEs and GSTs is crucial for providing timely warnings to operators of critical infrastructure.

## Project Structure
This project consists of three main parts:
1. **Data Collection from CME API**: Retrieving data about Coronal Mass Ejections from NASA's DONKI API
2. **Data Collection from GST API**: Retrieving data about Geomagnetic Storms from NASA's DONKI API 
3. **Data Merging and Analysis**: Combining the datasets to calculate the time difference between CMEs and their resulting GSTs

## Technologies Used
- Python 3
- Pandas for data manipulation
- Requests for API interaction
- JSON for data parsing
- Datetime for time calculations

## Installation and Setup
1. Clone this repository
2. Install required dependencies:
   ```
   pip install pandas requests python-dotenv
   ```
3. Create a `.env` file in the project root with your NASA API key:
   ```
   NASA_API_KEY=your_api_key_here
   ```
   To get a NASA API key, visit: https://api.nasa.gov/

## File Descriptions
- `retrieve_data.ipynb`: Jupyter notebook containing the code for data extraction, processing, and analysis
- `cme_gst_data.csv`: The output file containing the processed dataset
- `.env`: Configuration file for storing the NASA API key (not included in the repository)
- `README.md`: Project documentation

## Data Collection Process
The data collection process involves making API requests to NASA's DONKI API to retrieve information about CMEs and GSTs between May 1, 2013, and May 1, 2024. The process includes:

1. **CME Data**:
   - Retrieving CME data from the API
   - Extracting relevant fields (activityID, startTime, linkedEvents)
   - Processing the nested linkedEvents data structure
   - Creating a mapping between CMEs and their linked GSTs

2. **GST Data**:
   - Retrieving GST data from the API
   - Extracting relevant fields (gstID, startTime, linkedEvents)
   - Expanding the linkedEvents column
   - Creating a mapping between GSTs and their linked CMEs

## Data Analysis
The analysis phase merges the CME and GST datasets based on their activity IDs and calculates the time difference between a CME occurrence and its resulting GST. The results show that:

- The average time for a CME to cause a GST is approximately 3 days
- The minimum observed time is around 1.5 days
- The maximum observed time is about 6 days
- The median time is approximately 2.8 days

These findings can help the Space Weather Prediction Center improve their forecasting models by providing more accurate timeframes for when a CME might lead to a geomagnetic storm.

## Results
The results of this analysis show that there is a consistent temporal relationship between CMEs and GSTs. The calculated time differences can be used for developing predictive models that could potentially improve the accuracy of geomagnetic storm forecasts.

## Future Work
- Incorporate additional data sources such as solar wind parameters
- Develop a machine learning model to predict GST occurrence based on CME characteristics
- Analyze the relationship between CME speed/energy and the resulting GST intensity
- Investigate the impact of solar cycle on the frequency and intensity of CMEs and GSTs

## License
This project is licensed under the MIT License - see the LICENSE file for details.

## Acknowledgments
- NASA for providing the DONKI API and data
- NOAA Space Weather Prediction Center for their work in space weather forecasting
- The scientific community for ongoing research in space weather phenomena
