## First Airflow DAG: Data ingestion pipeline

if your docker-compose gives problem then 

 sudo apt-get remove docker-compose
 pip3 install -U docker-compose

1. Prepare the database first `docker-compose up airflow-init`

Unable to load the config, contains a configuration error.
airflow-init_1       | Traceback (most recent call last):
airflow-init_1       |   File "/usr/local/lib/python3.8/pathlib.py", line 1288, in mkdir
airflow-init_1       |     self._accessor.mkdir(self, mode)
airflow-init_1       | FileNotFoundError: [Errno 2] No such file or directory: '/opt/airflow/logs/scheduler/2022-04-11'

Then give root permission to  db and logs in this project structure.

sudo chmod -R 777  db/
sudo chmod -R 777 logs/

To use spark 

pip install apache-airflow-providers-apache-spark

This is going to created db/airflow.db sqlite database

2. Add raw data for current execution date and hour to be ingested

Add the date and time in the raw_data folder as follows.
         date:  2021-04-11
             hour : 11

4. - Launch Airflow `docker-compose up`

Wait for scheduler and webserver to get healthy, then go to `localhost:8081` 

```python
username: admin
password: airflow
```


4. Enable the DAG and watch it ingest data.
