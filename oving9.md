# Øving 9. Docker, Google Cloud Platform og Terraform  

I denne øvingen skal vi se mer på Docker - som er blitt en veldig viktig teknologi i "DevOps" Sfæren . Vi sklal lage egne Docker "Images" og kjøre de.
Målet er å pakke en enkel Spring Boot applikasjon (REST API) inn i en Docker Container og få kjørt den. Vi skal også komme i gang med Google Cloud Platform (GCP) - og bruke tjenesten _Cloud Build_ og _Container registry_ til å holde Docker Containerene våre


## Sign up for GCP

Du må inne med et kredittkort - men Google trekker deg ikke i løpet av "trial perioden", og du må selv gi aktivt samtykke for at de skal trekke deg for penger.
Du får $300 å leke med. 

## Følg Google Quick Guide

Kjør følgende tuturoial 

https://cloud.google.com/cloud-build/docs/quickstart-docker

## Verifiser at vi kan administrere GCP med terraform 

https://cloud.google.com/iam/docs/creating-managing-service-account-keys

Last ned nøkler JSON fil og legg den i _terraform_ katalogen 

kjør terraform apply!



