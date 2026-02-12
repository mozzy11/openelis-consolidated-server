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
- `oe.openelis.org` (from docker-compose-OE1.yml)
- `oe.openelis.org2` (from docker-compose-OE2.yml)

With the external network in place, the openelis instances can connect to the SHR FHIR server using the container name:
- URL: `http://shr-hapi-fhir:8080/fhir/`

### Starting the Services

1. Start the SHR (Shared Health Record) FHIR server:
```bash
docker compose up -d
```

it can be accesed at http://localhost:8090/fhir/

2. Start OpenELIS Instance 1:
```bash
docker compose -f docker-compose-OE1.yml up -d 
```

it can be accesed at https://localhost/

3. Start OpenELIS Instance 2:
```bash
docker compose -f docker-compose-OE2.yml up -d 
```

it can be accesed at https://localhost:444/




