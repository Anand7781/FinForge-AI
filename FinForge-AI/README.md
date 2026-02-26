# FinForge-AI
> AI-powered financial complaint analysis and dispute prediction system.

# Problem Statement
Understanding customer complaints is crucial for identifying issues in financial products. By analyzing these complaints, we can enhance existing products and ensure they meet customer needs effectively.

### Solution Proposed 
By analyzing customer complaints, we can develop a machine learning model that identifies whether new complaints are likely to be problematic. This proactive approach allows companies to address issues swiftly and improve customer satisfaction.

The problem is to identify registered complaints that will be disputed by customers or not.

## Tech Stack Used
1. Python 
2. PySpark
3. PySpark ML
4. Airflow as Scheduler
5. MongoDB

## Infrastructure Required
1. GCP Compute Engine
2. S3 Bucket
3. Artifact Registry

## Dashboarding
1. Grafana
2. Prometheus
3. Node Exporter
4. Promtail
5. Loki

## How to run?

## Workflow setup
Create .env file

```
AWS_ACCESS_KEY_ID=
AWS_SECRET_ACCESS_KEY=
MONGO_DB_URL=
TRAINING=1
PREDICTION=1
```
1- Trigger
0- Bypass

Build docker image
```
docker build -t tc:lts .
```

Launch docker image
```
docker run -it -v $(pwd)/finance_artifact:/app/finance_artifact  --env-file=$(pwd)/.env fc:lts
```

Steps to run project in local system
1. Build docker image
   ```
   docker build -t fc:lts .
   ```
2. Set environment variable
```
export AWS_ACCESS_KEY_ID=
export AWS_SECRET_ACCESS_KEY=
export MONGO_DB_URL=
export AWS_DEFAULT_REGION="ap-south-1"
export IMAGE_NAME=fc:lts
```
3. To start your application
```
docker-compose up
```
4. To stop your application
```
docker-compose down
``` 

In your local system to setup airflow 
AIRFLOW SETUP

## How to setup airflow
Set airflow directory
```
export AIRFLOW_HOME="/home/anand/census_consumer_project/census_consumer_complaint/airflow"
```

To install airflow 
```
pip install apache-airflow
```

To configure database
```
airflow db init
```

To create login user for airflow
```
airflow users create  -e anandkatkade96@gmail.com -f Anand -l Katkade -p admin -r Admin  -u admin
```

To start scheduler
```
airflow scheduler
```

To launch airflow server
```
airflow webserver -p <port_number>
```

Update in airflow.cfg
```
enable_xcom_pickling = True
