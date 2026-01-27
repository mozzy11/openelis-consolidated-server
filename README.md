# OpenELIS3-OpenMRS3-HIE SETUP

Spin up the services

```
docker-compose up -d
```

Acces the services at 

| Instance  |     URL       | credentials (user : password)|
|---------- |:-------------:|------:                       |
| OpenMRS3   |  http://localhost/openmrs/spa | admin : Admin123 |
| OpenELIS3 | https://localhost/ |    admin : adminADMIN!| 
| OpenHIM   |    http://localhost:9000/  |  root@openhim.org : openhim |
| SHR      | http://localhost:8090/fhir  |   | 
<!-- | FHIR PipeLine       | http://localhost:8095  |   |  -->

## Instructions 


1. Ensure Add the Right Test Catalogue ie tests with `Loinc Codes`

see [more](https://digi-uw.github.io/healthinformationexchange/lis-workflows/lis-workflows.html#tutorial-lab-order-communication-between-openmrs-and-openelis) for the EMR-LIS communication


watch the EMR-LIS Exhange [demo video](https://www.youtube.com/watch?v=LsHhDrrlvKw) using the Lab on FHIR module
