# Øving til forelesing #2

Målet med denne oppgaven er å lage et nytt Java prosjekt, sjekke dette inn i et offentlig GitHib repository, 
og få Concourse til å bygge dette hver gang man sjekker inn en endring på master branch

## Oppgave 1

* Lag et nytt repository under din egen bruker på GitHub
* Lag et "Hello world" Javaprosjekt, som kan bygge med Gradle eller Maven. Sjekk koden inn. 
* Prosjektet skal inneholde både Javakode og tester med Junit. 

TIPS

Dere kan lage et "quickstart" prosjekt med mvn archetype 

```
mvn archetype:generate -DgroupId=com.glennbech.pgr301 -DartifactId=hello-world -DarchetypeArtifactId=maven-archetype-quickstart -DinteractiveMode=false
```

OBS! 

følgende XML blokk må da legges til i pom.xml etterpå  

```xml
    <properties>
        <maven.compiler.source>1.8</maven.compiler.source>
        <maven.compiler.target>1.8</maven.compiler.target>
    </properties>
```



## Oppgave 2. Software as a Service (SAAS) Travis CI

Demo; 

https://travis-ci.org/glennbech/pgr301-helloworld

Travis er en enkel CI/CD tjeneste som kan gjøre kontinuerlig integrasjon. Tjenesten er gratis 
for offentlige repo. Travis integrerer med GitHub. Du kan logge på - og registrere deg med GitHub. Når du har logget deg på kan du aktivere travis bygg for 
en eller flere av dine repo.


Følg instruksjonene her [https://docs.travis-ci.com/user/getting-started/](https://docs.travis-ci.com/user/getting-started/)
    

Prøv å skrive en eller flere tester slik at de feiler, og se hva som skjer i Travis CI. 

## Oppgave 3. Concourse Pipeline 

Oppgaven er å få det lokale Concourse miljøet som kjører i Docker, til å bygge prosjektet 

Dere kan sjekke ut mitt repo som et startpunkt ; https://github.com/glennbech/pgr301-helloworld

Man legger til en ny pipeline på denne måten 
```
fly -t pgr301  set-pipeline -c pipeline.yml -p hello-world
```
