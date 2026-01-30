# OpenELIS-Consolidated-Server

## Instructions to run the OpenELIS Consolidated Server with Two Instances and a Central SHR

### Prerequisites

#### Create the External Docker Network

Before starting any of the docker-compose services, you must create the external network that allows the pipeline controllers to communicate with the SHR FHIR server:

```bash
docker network create shr-pipeline-network
```

This network enables communication between:
- `shr-hapi-fhir` (SHR FHIR server from docker-compose.yml)
- `pipeline-controller` (from docker-compose-OE1.yml)
- `pipeline-controller2` (from docker-compose-OE2.yml)

With the external network in place, the pipeline controllers can connect to the SHR FHIR server using the container name:
- URL: `http://shr-hapi-fhir:8080/fhir/`

### Starting the Services

1. Start the SHR (Shared Health Record) FHIR server:
```bash
docker compose up -d
```

it can be accesed at http://localhost:8090/fhir/

2. Start OpenELIS Instance 1:
```bash
docker compose -f docker-compose-OE1.yml up -d proxy
```

it can be accesed at https://localhost/

3. Start OpenELIS Instance 2:
```bash
docker compose -f docker-compose-OE2.yml up -d proxy2
```

it can be accesed at https://localhost:444/

### Start the Pipelines 

4. Start Pipeline Instance 1 for Sending FHIR data from OpenELIS instance 1 to the SHR:
```bash
docker compose -f docker-compose-OE1.yml up -d pipeline-controller
```
it can be accesed at http://localhost:8095

4. Start Pipeline Instance 2 for Sending FHIR data from OpenELIS instance 2 to the SHR:
```bash
docker compose -f docker-compose-OE2.yml up -d pipeline-controller2
```

it can be accesed at http://localhost:8096


Note : To run the Pipeline , Acces the Pipeline Controller in the UI ,First run the Full Pipeline (Batch mode) and the Incremental Pipeline (Streaming Mode)will start by default 


