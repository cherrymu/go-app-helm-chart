# Go API Helm Chart 

This is a repo containing Helm Chart for Deploying a simple Go CRUD API connecting to a postgresql database.

Prerequisite: Create a scheme in your postgresql database before install the helm chart
```
CREATE TABLE movies (
    id SERIAL,
    movieID varchar(50) NOT NULL,
    movieName varchar(50) NOT NULL,
    PRIMARY KEY (id)
);
```

To install this chart on your kubernetes enviroment, please follow the below instructions 

Step 1: Add the Helm repo 

```
helm repo add go-api https://cherrymu.github.io/go-app-helm-chart/

helm repo update
```
Step 2: Create namespace for go-api deployment

```
kubectl create namespace go-api
```

Step 3: Getting the values.yaml of the chart locally

Before we proceed with installation of the chart we need to set some custom values. To see what options are configurable on a chart and save that options to a custom values.yaml file run

```
helm show values go-api/go-api > values.yaml
```

Step 4: Mention your Database connection values like db name, db hosturl, db user, db password, db port in the ```values.yaml``` file we fetched from Step 3 under ```dbinfo``` section 

Step 5: Deploy the Chart

```
helm install go-api go-api/go-api -f values.yaml -n go-api
```

#### Follow the instructions notes to access the application that will be appear on the screen after the successful deployment of the chart.


