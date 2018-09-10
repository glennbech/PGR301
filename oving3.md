# Øving til forelesing #3

Målet med denne oppgaven er å øve på kontinuerlig integrasjon, Dere skal jobbe i par, og godkjenne endringer før de går inn i "master".
Dere skal også se hvordan en CI/CD motor kan benyttes for å kontrolere integritet før integrasjon. 


## Oppsett i GIT

* Fortsett gjerne på Repository fra Øving #2
* Gå sammen to- og to. 
* Den som eier repository inviterer den andre parten som "collaborator"
* Den inviterte parten kloner 

## Arbeidsflyt 


### ny branch 
```
git checkout master
git pull
git checkout -b "nytt_branch_navn"
```

### Commit 

Gjør endring i koden 
```
git commit -am"i changeds something!"
git push (doh! *)
```

* Se på den flotte feilmeldingen som kommer- og kopier forlsaget til git. 

### Lag Pull request i GIT

Når du ser på reposutory i Github vil du som regel få et forslag til å lage en PR.

## Introdduser Travis CI 

Eier av Repo går inn i Settings/Branches og velger "Apply rule to" master + "Add rule" og velg 

* Require pull request reviews before merging
* Require status checks to pass before merging (Her skal Travis dukke opp fra Øving #2)





Introduser test - og kompileringsfeil med vilje i minst en Pull request

## Bonus 

CODEOWNERS er en relativ ny mekanisme i GIT som bestemmer hvem som må kontrollere PR før den godkjennes. s
https://blog.github.com/2017-07-06-introducing-code-owners/

## Bonus 2

Pass på at dere har gått igjennom hele [concourse tutorial](https://concoursetutorial.com/)