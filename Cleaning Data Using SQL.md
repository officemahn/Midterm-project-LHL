# Cleaning Data Using SQL 

### Normalizing the Data

**Table Creation:**

```SQL
CREATE TABLE Airport_info (
    Airport_code TEXT PRIMARY KEY,
    Airport_name TEXT
);

CREATE TABLE Carrier_info (
    Carrier_code TEXT PRIMARY KEY,
    Carrier_Name TEXT
);

CREATE TABLE Flight_delay_time (
    Flight_code TEXT PRIMARY KEY,
    Arr_delay INTEGER,
    Carrier_delay INTEGER,
    Weather_delay INTEGER,
    Nas_delay INTEGER,
    Security_delay INTEGER,
    Late_aircraft_delay INTEGER
);

CREATE TABLE Flight_info (
    Flight_code TEXT PRIMARY KEY,
    Carrier_code TEXT REFERENCES Carrier_info (Carrier_code),
    Airport_code TEXT REFERENCES Airport_info (Airport_code)
);

CREATE TABLE Flights_details (
    Flight_code TEXT REFERENCES Flight_info (Flight_code),
    Year INTEGER,
    Month INTEGER
);

CREATE TABLE Arrival_delay (
    Flight_code TEXT REFERENCES Flight_info (Flight_code),
    Airport_code TEXT REFERENCES Airport_info (Airport_code),
    Arr_flights INTEGER,
    Arr_del15 INTEGER,
    Carrier_ct DOUBLE PRECISION,
    Weather_ct DOUBLE PRECISION,
    Nas_ct DOUBLE PRECISION,
    Security_ct DOUBLE PRECISION,
    Late_aircraft_ct DOUBLE PRECISION,
    Arr_cancelled INTEGER,
    Arr_diverted INTEGER
);

```
### Data Cleaning 

**Dropping Irrelevant Rows:**

```SQL
Select *
FROM airline_delay
Where 
	year = 'NA' or
	month = 'NA' or 
	carrier = 'NA' or 
	carrier_name = 'NA' or
	airport = 'NA' or
	airport_name = 'NA' or 
	arr_flights = 'NA' or
	arr_del15 = 'NA' or 
	carrier_ct = 'NA' or 
	weather_ct = 'NA' or 
	nas_ct = 'NA' or 
	security_ct = 'NA' or
	late_aircraft_ct = 'NA' or 
	arr_cancelled = 'NA' or 
	arr_diverted = 'NA' or 
	carrier_delay = 'NA' or 
	weather_delay = 'NA' or 
	nas_delay = 'NA' or 
	security_delay = 'NA' or 
	late_aircraft_delay = 'NA' 
);
```



