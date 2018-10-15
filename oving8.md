# Øvingsoppgave 8 

I denne oppgaven skal vi bli bedre kjent med Environment Parity. Vi skal også lage databaser, og la terraform kjøre infrastrukturkode vår - målet med dagens øving er å gjøre seg kjent med denne applikasjonen og få den til å virke i eget miljø. 

## Docker-compose for docker 

https://gist.github.com/glennbech/267519c4b8aa9840352155b363777684

## Miljøvariable

Sett som vanlig følgende miljøvariabler 

* GITHUB_TOKEN 
* HEROKU_API_KEY  

mac/linux
```
export GITHUB_TOKEN=
```
Microsoft Windows 
```
set GITHUB_TOKEN=
```

### Lag en fork av disse

- https://github.com/PGR301-2018/heroku-pipeline-infra
- https://github.com/PGR301-2018/heroku-pipeline-app

### Modifiser 

- provider.tf med din eget brukernavn på heroku
- variables.tf med applikasjonnavn og prefix 

### Rydd opp i Heroku

Dette oppsettet trenger 3 applikasjoner i heroku. Hvis du har fler en to der fra før, eller en annen pipeline. Slett disse, og lag rom. 

### Heroku git:remote 

Bruk heroku CLI til å knytte app-repo til CI miljø appen

```
heroku git:remote -a thawing-inlet-61413
```

# Bonus


## Auto promote
Improviser med det du har, og lag jobber i concourse for å promotere til stage - og prod 
https://devcenter.heroku.com/articles/pipelines

CLI for å gjøer dette er... 
```
heroku pipelines:promote -r staging
```
... Hvordan kan vi få concourse til å gjøre dette ? (Hint: se på Heroku sync task)


## Kan vi få concourse til å kople git-repositoryet vårt med heroku appen?
Det er det eneste manuelle steget vi har i pipeline så langt. 




