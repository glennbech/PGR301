I denne øvingen skal dere lage en ny GitHub Organization, repository og team med medlemmer. Dette skal gjøres via Terraform. 
Vi skal også øve på å lage Pull-requester mot repositories vi ikke har skrive-tilgang på. 

# Lage pull request fra fork 
[https://github.com/glennbech/pgr301-infra-as-code](https://github.com/glennbech/pgr301-infra-as-code)

* Endre filen https://github.com/glennbech/pgr301-infra-as-code/blob/master/github_team.tf, og legg til din egen bruker i teamet. 
* Lag en Pull reuqest basert på egen fork
* https://help.github.com/articles/creating-a-pull-request-from-a-fork/
* https://help.github.com/articles/fork-a-repo/

# Administrere GitHub ved hjelp av Terraform

[Terraform installeres på lokal maskin](https://www.terraform.io/intro/getting-started/install.html)

## Lag et Personal Access token for GitHub

* [https://help.github.com/articles/creating-a-personal-access-token-for-the-command-line/](https://help.github.com/articles/creating-a-personal-access-token-for-the-command-line/)

Ta godt vare på dette, det er like "viktig"/"Sensitivt" som både brukernavn og passord sammen. 

## Lag en GitHub Organizaion 

Sjekk ut https://help.github.com/articles/creating-a-new-organization-from-scratch/

## Verifiser terraform + github token 

Klone [dette repositoriet for inspirasjon](https://github.com/glennbech/pgr301-infra-as-code) som inspirasjon.

Leg et nytt *public* repository for videre arbeid. Kopier gjerne filene fra pgr301-infra-as-code som et startpunkt

Dere må modifidsere filen https://github.com/glennbech/pgr301-infra-as-code/blob/master/provider.tf og bruke eget organizationnavn (laget i forrige steg). 

Dere må også sørge for at environment variabel GITHUB_TOKEN er satt når dere jobber med terraform.

Legg til noen medelever i egen organisasjon ved å modifisere på terraform filene

For å verifisere at alt er okey, kjør 
```
terraform plan
```

Her vil dere se hva Terraform mener er differansen mellom faktisk tilstand og TF filene. 
For å utføre endringene kjører dere
```
terraform apply
```
# Concourse Pipeline for Terraform 

I denne oppgaven er målet å få Concourse til å kjøre en pipeline, slik at din organisasjon automatisk blir endret dersom du endrer på kildekoden i ditt eget repository. 

Ta utgangspunkt i filene under /concourse i https://github.com/glennbech/pgr301-infra-as-code

# For å legge til Pipeline blir kommandoen 

```
fly -t <din target som laget ved login> sp -c concourse/pipeline.yml -p infra-as-code-github -v github_token=<github_token>
```

