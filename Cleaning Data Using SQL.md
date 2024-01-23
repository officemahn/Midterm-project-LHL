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

INSERT INTO Airport_info (state)
SELECT DISTINCT MAX(airport_name) 
FROM airline_delay


INSERT INTO Carrier_info (carrier_code, carrier_name)
SELECT DISTINCT carrier, MAX(carrier_name) 
FROM airline_delay
GROUP BY carrier;



INSERT INTO Flight_info (flight_code, carrier_code, airport_code)
SELECT DISTINCT
    a.row_id,
    c.carrier_code,
    a.airport
FROM
    airline_delay a
    JOIN Carrier_info c ON a.carrier = c.carrier_code
    JOIN Airport_info ap ON a.airport = ap.airport_code;



ALTER TABLE flight_details
ADD COLUMN flight_date DATE;


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

**Cleaning the Data**
```SQL
-- Update data in the existing Airport_info table
UPDATE Airport_info
SET
    City = SPLIT_PART(airport_name, ',', 1),
    State = TRIM(SPLIT_PART(SPLIT_PART(airport_name, ':', 1), ';', 2)),
    Airport_name = SPLIT_PART(SPLIT_PART(airport_name, ':', 2), '/', 1);

ALTER TABLE Airport_info
ADD COLUMN City TEXT,
ADD COLUMN State TEXT;

-- Update the State column in Airport_info table
UPDATE Airport_info
SET State = TRIM(SPLIT_PART(State, ',', 2));


-- Update the State column in Airport_info table
UPDATE Airport_info
SET State = TRIM(SPLIT_PART(airline_delay.airport_name, ':', 1))
FROM airline_delay
WHERE Airport_info.AIRPORT_CODE = airline_delay.AIRPORT;

ALTER TABLE flight_details
ADD COLUMN flight_date DATE;

```



