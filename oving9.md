# Øving 9: Docker, Google Cloud, Terraform. 

I denne øvingen skal vi se mer på Docker - som er blitt en veldig viktig teknologi i "DevOps" Sfæren . Vi sklal lage egne Docker "Images" og kjøre de.

Målet er å pakke en enkel Spring Boot applikasjon (REST API) inn i en Docker Container og få kjørt den. Vi skal også komme i gang med Google Cloud Platform (GCP) - og bruke tjenesten _Cloud Build_ og _Container registry_ til å holde Docker Contaionerene våre - 

I senere øvinger skal vi kjøre Spring Boot applikasjonen vår på Google Cloud Platform - og integrere en pipeline med Concourse

### Nødvendige kunnskaper og nyttige lenker

* Hvordan lage en fork av et repository ; https://help.github.com/articles/fork-a-repo/

## Docker 

Lag en fork av koden fra Øving 7 og øving 8 - https://github.com/PGR301-2018/heroku-pipeline-app

Målet med denne oppgaven er å lage en Docker Container som kjører Spring boot applikasjonen.

* Kjør ```mvn install``` slik at vi får bygget jar filer under target katalogen
* Bygg en Docker Container av applikasjonen ved å lage en fil som heter _Dockerfile_ i rotkatalogen til _heroku-pipeline-app_ som ser slik ut ; 

```
FROM openjdk:8-jdk-alpine
VOLUME /tmp
ARG JAR_FILE
COPY ${JAR_FILE} app.jar
ENTRYPOINT ["java","-jar","/app.jar"]
```

* Bygg en container 

Starte en kommandolinje og stå i _heroku-pipeline-app_
Kjør kommandoen (OBS! Legg merke til siste punktum)

```
docker build --build-arg JAR_FILE=target/herokupipe-example-0.0.1-SNAPSHOT.jar .
```

* Sjekk at du kan starte containeren din med

```
docker run -e JDBC_DATABASE_URL=jdbc:h2:mem:test -d -p 8000:8080 <container id- output fra build>
```

* Applikasjonen blir tilgengelig på port 8000

# Google Cloud Platform 

Lag en fork av https://github.com/PGR301-2018/gcloud-start  og en klone av din egen fork som et utgangspunkt

## "Sign up" for GCP

Du må inne med et kredittkort - men Google trekker deg ikke i løpet av uten at du selv gir aktivt samtykke
Du får $300 å leke med. 

## Installer gcloud CLI

Vi gjør alltid ting fra kommando-linje i "DevOps" verdenen!

* https://cloud.google.com/sdk/docs/quickstart-windows
* https://cloud.google.com/sdk/docs/quickstart-macos

## Følg Google Quick Guide

Kjør følgende tuturoial for å komme i gang med Docker på GCP - Dette vil gjøre deg istand til å gjøre det samme som ble demonstrert av foreleser. 

https://cloud.google.com/cloud-build/docs/quickstart-docker

# Terraform 

Først må vi lage nøkler som vil gi Terrafrom (eller hvem- som helst- som innehar nøklene) å aksessere vår konto. Følg oppskriften - https://cloud.google.com/iam/docs/creating-managing-service-account-keys

Service Account må ha rolle "editor"

Last ned nøkler JSON fil og legg den i _heroku-pipeline-app_/terraform/ katalogen. Kall filen application.json

* kjør terraform apply
* se at det er blitt opprettet en VM i GCP Dashboard
* kjør terraform destroy
* se at VM som ble opprettet er borte 

## Deep dive på terraform + Google cloud. 

Følg tutorialen her - https://cloud.google.com/community/tutorials/getting-started-on-gcp-with-terraform  

NB! dere har gjort omtrent halve tutorialen i steget over. Fortsett fra avsnittet *Running a server on Google Cloud Platform*

Noen viktige læringspunkter i tutorialen er

* Terraform output - slik at du får tak i IP til server som blir startet
* Hvordan du kan gi terraform filer fra ditt lokale filsystem (SSH keys i dette tilfelle her)

## ressurser

* https://spring.io/guides/gs/spring-boot-docker/


