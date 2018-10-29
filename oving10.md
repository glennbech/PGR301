# Øving 10

I denne øvingen skal vi brukke terraform og tjenesten "StatusCake" for å sette opp varsling og overvåkning av applikasjonen 
vår fra skyen. 

## Hent kildekode

### Lag en fork av to repositories

* https://github.com/PGR301-2018/monitoring-app
* https://github.com/PGR301-2018/monitoring-infra

Lag deploy keys for disse. Putt private key i credentials.yaml, og public i repisotoriet sit "settings"  (Hvis noe er uklart, 
kan dere bruke litt tid på lese dere opp på Deploy keys her ; https://developer.github.com/v3/guides/managing-deploy-keys/
)

Du må endre litt på pipeline.yaml etter du har laget egen fork. Sjekk under "resources" og bytt ut source/uri for både infra- og app repo 
 
## Lag en bruker på statuscake

Statuscake er en varsling- og overvåkningstjeneste som har en gratis "Free tier", men også en Terraform provider. Det liker vi!
Registrer deg på Statucake og finn API key ved å klikke på profil- ikonet, og epost-adressen din. 

Modifiser statuscake.tf i https://github.com/PGR301-2018/monitoring-infra - med ditt username *NB!!!* "Username" som skal inn her er ikke e-post adressem din. 
Brukernavnet står på profilsiden din og er din epost uten spesialtegn som . og @ 

Bruk gjerne litt tid til å bli kjent med tjenesten. Man kan legge på varsling på eksisterende tjenester som feks VG.no eller noe annet moro. 

## Lag credentials.yaml

Husk at hemmeligheter ikke skal inn i terraform kode!! Det ligger en eksempel credentials.yaml i *monitoring-infra* 

## Start pipeline 

Sørg for at concourse kjører lokalt ved å se på http://localhost:8080 - hvis ikke kjør ```docker-compose up -d``` som vanlig, Verifiser at 
docker funker ved å fekes skrive ```docker ps```

Stå i monitoring-infra/

```
fly -t pgr301 sp -c concourse/pipeline.yml -p monitoring -l credentials.yaml
```

Denne pipelinen har ingen automatisk triggering. Du må kjøre 'infra' jobben for å få opprettet Heroku pipeline og overvåkningen. Det samme gjelder applikasjonen, for å få pushet den opp på heroku. 




## 
