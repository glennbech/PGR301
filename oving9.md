# Øving 9. Docker, Google Cloud Platform og Terraform  

I denne øvingen skal vi se mer på Docker - som er blitt en veldig viktig teknologi i "DevOps" Sfæren . Vi sklal lage egne Docker "Images" og kjøre de.

Målet er å pakke en enkel Spring Boot applikasjon (REST API) inn i en Docker Container og få kjørt den. Vi skal også komme i gang med Google Cloud Platform (GCP) - og bruke tjenesten _Cloud Build_ og _Container registry_ til å holde Docker Containerene våre

Lag en fork av https://github.com/PGR301-2018/gcloud-start  og en klone av din egen fork som et utgangspunkt

## "Sign up" for GCP

Du må inne med et kredittkort - men Google trekker deg ikke i løpet av uten at du selv gir aktivt samtykke
Du får $300 å leke med. 

## Installer gcloud CLI

Vi gjør alltid ting fra kommando-linje i "DevOps" verdenen!

* https://cloud.google.com/sdk/docs/quickstart-windows
* https://cloud.google.com/sdk/docs/quickstart-macos

## Følg Google Quick Guide

Kjør følgende tuturoial for å komme i gang med 

https://cloud.google.com/cloud-build/docs/quickstart-docker

## Verifiser at vi kan administrere GCP med terraform 

Først må vi lage nøkler som vil gi Terrafrom (eller hvem- som helst- som innehar nøklene) å aksessere vår konto. Følg oppskriften - https://cloud.google.com/iam/docs/creating-managing-service-account-keys

Last ned nøkler JSON fil og legg den i terraform katalogen 

kjør terraform apply!

## Deep dive på terraform + Google cloud 

https://cloud.google.com/community/tutorials/getting-started-on-gcp-with-terraform


