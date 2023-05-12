# Prerequisites
- Python 3.11
- MariaDB 11.1
- Django 4.2

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
    - fetch journey data from database based on user query and display information as mentioned in [Recommended in Functional Requirements section of Info](TaskInfo.md) 

## Features to Implement
- Recommended Features :
    - *Data Import and Validation*, based on Duration (> 10 seconds) and Journey (> 10 metres)
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
- Create tables with non-null columns and replicate table structure for similar tables (*journeys*) using the following command :
>>>
    CREATE TABLE journeys_june LIKE journeys_may;
    CREATE TABLE journeys_july LIKE journeys_may;
    
- Setup all tables (*stations, journeys*) using the following command :
>>>
    LOAD DATA INFILE '/path/to/csv/file.csv'
    INTO TABLE table_name
    FIELDS TERMINATED BY ','
    ENCLOSED BY '"'
    LINES TERMINATED BY '\n'
    IGNORE 1 ROWS;
    
- Create a virtual environment to install MariaDB Connector/Python package, *mariadb*
- Build methods to [implement features](#features-to-implement)
- Build Backend service to access data from Database to application
- If possible, Auotmate testing with specific requirements as mentioned in [Info-Testing Primer](https://dev.solita.fi/2022/11/01/testing-primer-dev-academy.html)

## Tools
- **Backend :** 
    - Language : Python 3.11 
        - REASON : Learning C# but have enough proficiency with methods and classes to implement a backend application
- **Database :**
    - Maria DB 11.1
        - REASON : Mostly for a single reason that it is an open-source RDBMS that is compatible with multiple operating systems and programming languages
- **Web Server Framework**
    - Django (*version to declare*)
        - REASON : Compatibility of Django with MariaDB is mainly because it supports modeling and managing databases (CRUD operations)