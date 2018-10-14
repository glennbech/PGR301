# Øvingsoppgave 8 

I denne oppgaven skal vi bli bedre kjent med Environment Parity. Vi skal også lage databaser, og la terraform kjøre infrastrukturkode vår

## Miljøvariable

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

## Pipeline og concourse oppsett 



### Lag en fork av disse

- https://github.com/PGR301-2018/heroku-pipeline-infra
- https://github.com/PGR301-2018/heroku-pipeline-app

### Modifiser 

- provider.tf med din eget brukernavn på heroku
- variables.tf med applikasjonnavn og prefix 

### Rydd opp i Heroku

Dette oppsettet trenger 3 applikasjoner i heroku. Hvis du har fler en to der fra før, eller en annen pipeline. Slett disse, og lag rom. 


