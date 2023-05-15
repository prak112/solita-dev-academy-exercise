# Prerequisites
- Python 3.8.10
- MariaDB 11.1.0
- Django 4.2.1

# Configuration
- 

# Execution
- 

# Documentation
## Background
- Helsinki Regional Transport (HSL) service provides city-bikes for hour-based rental seasonally (spring-autumn)
- HSL requires a web application to understand the usage of their city-bikes.

## Aim
- Create application to :
    - display journeys made by customers within Helsinki capital area
    - fetch journey data from database based on user query and display information as mentioned in [Recommended in Functional Requirements section of Info](INFO.md) 

## Features to Implement
- Recommended Features :
    - *Data Import and Validation* - filter by : Duration (> 10 seconds) and Journey (> 10 metres)
    - *Journey List*, either with Pagination or Hard-coded limit for browser stability
        - *Departure and Return Stations*
        - *Covered Distance (in kilometres)*
        - *Duration (in minutes)* 
    - *Stations List*, 
    - *Single Station* consisting of name, address, total number of start and end journeys
    - *Add Journey / Station*

## Workflow
- Install MariaDB
- Setup database (*hsl_city_bikes*)
- Create tables with non-null columns and replicate table structure for similar tables (*journeys*) 
   
- Create *bike_stations* table with renamed columns as listed below
>
    +------------+-------------+------+-----+---------+-------+
    | Field      | Type        | Null | Key | Default | Extra |
    +------------+-------------+------+-----+---------+-------+
    | fid        | int(11)     | NO   |     | NULL    |       |
    | id         | int(11)     | NO   | PRI | NULL    |       |
    | name_fi    | varchar(50) | NO   |     | NULL    |       |
    | name_sv    | varchar(50) | NO   |     | NULL    |       |
    | name       | varchar(50) | NO   |     | NULL    |       |
    | address_fi | varchar(50) | NO   |     | NULL    |       |
    | address_sv | varchar(50) | NO   |     | NULL    |       |
    | city_fi    | varchar(50) | NO   |     | NULL    |       |
    | city_sv    | varchar(50) | NO   |     | NULL    |       |
    | operator   | varchar(50) | NO   |     | NULL    |       |
    | capacity   | int(11)     | NO   |     | NULL    |       |
    | longitude  | float       | NO   |     | NULL    |       |
    | latitude   | float       | NO   |     | NULL    |       |
    +------------+-------------+------+-----+---------+-------+

- Create *journeys* table using the following columns
>   
    CREATE TABLE journeys_may2021 (
        departure TIMESTAMP,
        arrival TIMESTAMP,
        departure_station_id INT NOT NULL,
        departure_station_name VARCHAR(50) NOT NULL,
        arrival_station_id INT NOT NULL,
        arrival_station_name VARCHAR(50) NOT NULL,
        distance_in_meters INT NOT NULL,
        duration_in_seconds INT NOT NULL,
        PRIMARY KEY (departure_station_id, return_station_id));

- Create additional *journey* tables using the following command, since their columns are same 
>

    CREATE TABLE journeys_june LIKE journeys_may;
    CREATE TABLE journeys_july LIKE journeys_may;

- Setup tables' data (*stations, journeys*) from the URLs provided in the [INFO](INFO.md) using the following command :
>
    LOAD DATA INFILE '<file_url_path>'
    INTO TABLE <table_name>
    FIELDS TERMINATED BY ','
    ENCLOSED BY '"'
    LINES TERMINATED BY '\n'
    IGNORE 1 ROWS;



    
- Create a virtual environment to install MariaDB Connector/Python package, *mariadb*
- Build methods to [implement features](#features-to-implement)
- Build backend application to display data on webpage using Django by retrieving required data from *hsl_city_bikes* database
- *If possible,* build tests with specific requirements as mentioned in [INFO-Testing Primer](https://dev.solita.fi/2022/11/01/testing-primer-dev-academy.html)

## Tools
- **Language : Python 3.8.10**
- REASON : Developed enough proficiency with methods and classes to implement a backend application

- **Database : Maria DB 11.1.0**
- REASON : Mostly for a single reason that it is an open-source RDBMS that is compatible with multiple operating systems and programming languages

- **Web Server Framework : Django 4.2.1**
- REASON : Compatibility of Django with MariaDB to support modeling and managing database (CRUD operations)
- MVC (Model-View-Controller) Framework, and a To-Learn item on the learning list.