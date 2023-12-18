# lab 1
## author - `Khlyvniuk Daniil`
## group - `i-12`

## Overview

This project demonstrates the setup of a PostgreSQL database using Docker Compose and includes the creation of a table
named `actors`. Actors are added to the database based on specific criteria, and queries are performed to select actors
meeting certain conditions.

## Prerequisites 
- Docker installed on your machine 
- Docker Compose installed on your machine

## Setup 
1. Clone the repository to your local machine. 
2. ```git clone <repository_url>```
3. ```cd <repository_url>```

# Start the PostgreSQL database using Docker Compose.
1. ```docker-compose up -d``` This command launches the PostgreSQL container as specified in the docker-compose.yml file.
2. Open terminal inside the docker container
    ```Bash
    docker-compose exec db /bin/bash
    ```
3. Create new table `actors`
    ``` SQL
    psql -U ${POSTGRES_USER} -d ${POSTGRES_DB} -c "CREATE TABLE actors ( id SERIAL PRIMARY KEY, firstName VARCHAR(255) NOT NULL, lastName VARCHAR(255) NOT NULL );"
    ```
4. Example: Actors with names not consisting of 3 characters and/or last names not containing the letter 'J'
code
    ```SQL
    INSERT INTO actors (firstName, lastName) VALUES ('Robert', 'Smith'), ('Jennifer', 'Lopez'), ('Michael', 'Brown'), ('Emily', 'Davis');
    ```
5. Verify the inserted data.
    ```SQL
    SELECT * FROM actors;
    ```
6. Query actors with names consisting of 3 characters and last names containing the letter 'J'.
```SQL
SELECT * FROM actors WHERE LENGTH(firstName) = 3 AND POSITION('J' IN lastName) > 0;
```
