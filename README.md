# Midterm-project-LHL
___

##### Project by: Angelo Reyes & David Oladipo 

##### Dataset: [United States Airline Delays for December 2019 and 2020.](https://www.openintro.org/data/csv/airline_delay.csv)

## Project/Goals
___

The airline industry is a significant driver of the global economy, with an estimated market size just below 814.5 billion U.S. dollars in the United States last year. However, it faces various challenges that impact carriers, airports, and passengers alike. Flight delays, redirections, and cancellations have substantial financial repercussions and pose considerable inconveniences to travelers. The increasing demand for air travel, coupled with shortages in staff, suggests that delays may become more prevalent. The purpose of our project is to analyze trends in flight delays from 2019 to 2020, focusing on data from the United States. By examining the causes of delays, including carrier-related issues, security concerns, weather conditions, and contributions from the National Aviation System (NAS), we aim to provide insights into the challenges faced by the U.S. airline industry and propose potential solutions to mitigate the impact of delays on both operational efficiency and passenger experience.

**Overall Trend Analysis:** Identify patterns and shifts in flight delays for 2019 and 2020.

**Airline Performance Assessment:** Evaluate individual airline punctuality and identify areas for improvement.

**Identification of Delay Causes:** Categorize delays by carrier issues, security concerns, weather, and NAS disruptions.

**Time-based Causes Analysis:** Uncover temporal patterns in delays to optimize scheduling and resource allocation.

**City-wise Delay Visualization:** Highlight geographical patterns of delays across different cities.

**Carrier vs. Airport Impact Analysis**: Assess the relationship between specific carriers and airports in contributing to delays.

The project aims to provide insights into U.S. airline industry challenges, guiding targeted solutions for operational efficiency and enhancing passenger experience. While direct intervention to prevent delays may not be possible, the analysis of delay data offers a wealth of information that can be leveraged for strategic decision-making, risk mitigation, and overall improvement in the efficiency and effectiveness of airline operations.

## Process
___

### Cleaning the Data
The initial step involved cleaning the data and creating appropriate tables to normalize the dataset.

#### Normalizing the Data
1. Table Creation:
   Six tables were created to normalize the data:
   airport_info, arrival_delay, carrier_info, flight_delay_time, flight_info, flight_details

2. Ensured a standardized format across tables for consistency.

3. Assigned primary keys to uniquely identify records in each table and  foreign key relationships to connect related tables.
   
#### Data Cleaning
1. Relevant data was moved and inserted into the appropriate tables.
   
2. Filtered out irrelevant data and addressed null values appropriately.
   
3. Altered table structures and updated empty or missing values.
   
#### Data Type Validation
1. Employed case statements to populate columns based on predefined criteria.
   
2. Conducted tests to validate data consistency and accuracy.
   
3. Implemented checks for null values to maintain data integrity.

## Results
___
#### Overall Trend Analysis:
There were significant reduction in delays in December 2020 compared to December 2019 which indicates that certain factors or improvements in the airline industry may have positively impacted on-time performance.
#### Airline Performance:
- Allegiant Air and Frontier Airlines show relatively lower average delays which suggest that these carriers have more efficient operational processes or better strategies for managing delays while major carriers like American Airlines and JetBlue Airways experience substantially higher average delays.
#### Delay Causes:
- The result indicated that late aircraft caused the most delay in air flights.
- Late Aircraft delays being the most frequent indicates that issues related to the arrival or departure of aircraft from previous flights significantly contribute to delays.
- Carrier delays and National Aviation System delays also play substantial roles, emphasizing the need to address both airline-specific and broader aviation system issues.


## Challenges
___

## Future Goals
___
#### Build Regression Model:
- Develop a regression model to predict flight delays based on historical data and relevant features.
- Explore the impact of different variables such as weather conditions, carrier type, and time of day on delays.
- Fine-tune the model to improve accuracy and reliability.
- Forecast potential delays and take proactive measures.

#### Continuous Monitoring:
Establish a system for continuous monitoring of delay trends and performance metrics.

#### Conduct further exploratory analysis to uncover additional insights.
