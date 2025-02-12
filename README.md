# Setup webinar

## Requirements

- Docker (to run Metabase and the setup containers)
- Optional: a database to connect to

## How to run (Docker - easier)

1) Install Docker if you haven't done so
2) clone this repository and get into it
3) insert your database connection string on line 51 (you can leave the default if needed) and one of the table names in your DW on line 52
4) run `docker compose up` on the base folder of the repository
5) wait for everything to start and then go to http://localhost:3000 and use the credentials a@b.com / metabot1 to authenticate
6) enjoy Metabase with your data!

## How to run (without Docker - a bit more complicated)

1) clone this repository
2) install a Java Runtime Environment (JRE) from https://adoptium.net/es/temurin/releases. Download the JRE MSI file and install. Install Python (https://www.python.org/downloads/) as well, since it will be needed for the automated setup.
2) download Metabase from https://downloads.metabase.com/enterprise/v1.53.1/metabase.jar
3) now open a terminal or command prompt and go to the place that you downloaded Metabase and run the following: `java -jar metabase.jar`
4) once Metabase finishes starting, go to the setup folder, install the dependencies (`pip -r requirements.txt`) and run `host=http://localhost port=3000 connection_string=<your_database_connection_string> table=<your_table> python setup.py` (replace <your_database_connection_string> and <your_table> with your data)
5) wait a few seconds till the process finishes and go to http://localhost:3000. Authenticate with a@b.com / metabot1
6) enjoy Metabase with your data!

## To do

- support more databases other than Postgres and MySQL