# Azure multi-container Docker application sample
This repository contains a sample Azure multi-container Docker application.

* service-a: Angular.js sample application with Node.js backend 
* service-b: ASP .NET Core sample service

## Configuration
If you want to try logging to Application Insights, set the `APPINSIGHTS_INSTRUMENTATIONKEY` environment variable, e.g.

```
export APPINSIGHTS_INSTRUMENTATIONKEY=488811fc-e1e1-4ba2-9278-f38ce88559c2
```

## Run application locally
First, compile the ASP .NET Core application code. This uses a container to isolate build dependencies that is also used by VSTS for continuous integration:

```
docker-compose -f docker-compose.ci.build.yml run ci-build
```

(On Windows, you currently need to pass the -d flag to docker-compose run and poll the container to determine when it has completed).

Now build Docker images and run the services:

```
docker-compose up --build
```

The frontend service (service-a) will be available at http://localhost:8080.

## Deploy to Azure Container Service
TBD