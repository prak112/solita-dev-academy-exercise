# Project Documentation
## Background
- Helsinki Regional Transport (HSL) service provides city-bikes for hour-based rental seasonally (spring-autumn)
- HSL requires a web application to understand the usage of their city-bikes.

## Aim
- Create application to :
    - display journeys made by customers within Helsinki capital area
    - fetch journey data from database based on user query and display information as mentioned in [Recommended in Functional Requirements section of TaskInfo](TaskInfo.md) 

## Features to Implement
- Recommended Features :
    - *Data Import and Validation*, based on Duration (> 10 seconds) and Journey (> 10 metres)
    - *Journey List*, either with Pagination or Hard-coded limit for browser stability
    - *Stations List*, 
    - *Single Station* consisting of name, address, total number of start and end journeys
    - *Add Journey / Station*

- Key Features for *Journey List*:
    - *Departure and Return Stations*
    - *Covered Distance (in kilometres)*
    - *Duration (in minutes)*

## Workflow
- Dump provided into SQL database
- Build Backend service to access data from Database to application
- If possible, Auotmate testing with specific requirements as mentioned in [TaskInfo-Testing Primer](https://dev.solita.fi/2022/11/01/testing-primer-dev-academy.html)

## Tools & Libraries
- **Backend :** 
    - Language : Python 3.11.x
- **Database :**
    - Maria DB (*version to declare*)
