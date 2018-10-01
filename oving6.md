Vi er nå blitt kjent med Heroku- Målet er å få en "Hello world" spring booot applikasjon opp å kjøre
på platformen som har automatisk deployment, hver gang vi pusher endringer til master branch i GIT. Automatisk deployment skal skje via Concourse.

NB.

Vi skal "Jukse litt" i dag og opprette Heroku app fra kommando-linje, senere skal vi se på å opprette all infrastruktur med Terraform.

Vi har også sett at det er fornuftig å skille Infrastruktur-dokumenter fra kildekode, så vi skal lage et eget
repository for concourse pipeline ogspå

Dere kan bruke følgende repositories som utgangspunkt

* [Infrastruktur og pipeline - https://github.com/PGR301-2018/heroku_example](https://github.com/PGR301-2018/heroku_example)  
* [Spring boot hello world - https://github.com/PGR301-2018/heroku_example-app](https://github.com/PGR301-2018/heroku_example-app)

TIPS:

* Klone disse, og ta bort .git katalogen
* Lag nye Repositories i egen organisasjon, gjerne ved hjelp av terrafomr og Concourse fra sist øving
* Kopi

 NB! Dere må erstatte verdier i pipeline.yml filen, som er laget for dette eksemple. De nødvendige endringene er kommentert i
 filen.

# Lag en Heroku app

Dere skal ha installert Heroku CLI, [hvis ikke gjør det](https://devcenter.heroku.com/articles/heroku-cli)

```
heroku create some-app-name-that-you-like
```

# Til info: Hemmeligheter Concourse trenger

## Github token & Nøkkelpar

* For å sjekking om ny versjon av kode er tilgjengelig, og for å gjøre andre API kall trenger Concourse et API token. Lag et Personal Access Token, og ha dette klart.

 * For å pushe kode, og for å bruke SSH autentisering til dit eget repo, må du lage en [deploy key med write access](https://developer.github.com/v3/guides/managing-deploy-keys/) 

## Heroku API Key

Heroku API Key kan lett finnes under account settings / i Heroku. Denne er nødendig for å autentisere mot Heroku API + Git

# Lag en credentials.yml

Kopier disse hemmelighetene inn i en credentials.yml fil

```yaml

github_token: 182da696sdsdsdsdsdd64550

deploy-key-app: |
  -----BEGIN RSA PRIVATE KEY-----
  MIIEowIBAAKCAQEAudQywpLcFLe1kIuNwscrw1Qz+ftoF2KZyZwPqj7Wr8UUS56m
  tIC/MD+phE851+O4A0sPOMUlyIHtxi9/MAGWIQhHA5HP5g4Xa51lnBIi1X+pkYPj
  eUbxqjghEX94JDufODOz6lCjzLDI2GKahf/IpVRZLe+Yq70LXpt2xPBAacyObPL3
  OH8Cld44tFpiOCYAb4ye/cv/PWr0W5EdqxNBpaySl8XZkMC7bkGQbAFwpic9G/MV
  k1GSOzESCvteKtcyF/DtJ/9EC4Ic8yuuQUPbKqa4p52A3Fyzs8+ozct6UX56Uzbn
  umqo/K+ZPViO2g93aq5gUt2qzN/JUlB8skIsYQIDAQABAoIBAEZ5GP79XwVkXjEB
  G7PggNJE3qlRFLq5pAT3cGFqD1T9cqLy+dm+ccNEgW8x9IfRTnnBP3aSHbAaxifA
  34U/NMY2M2hBJgzjDzK6asdadasdasdasdadsasdas7mXpOvIMTZpsOX7Wa1LJYT
  XvKufFNm16M6GDYZLXSllLc/Pc5hJP3tqslgexvEQqpqmn7nMYm9nGCzbbKWyPdg
  DIW+fUU5fPEa8hViJMMMJZjupq2gxr7nS8QS5HQKko0Vqw9FIKFEMsOKECFVjrXm
  e0//6DnPaiUe6Y5iHauQe4es+bmeKrr6N+esefQq3YI0iGv4sXzjwg2t05/Qr0qs
  og75hSECgYEA775rxEzA7AXI3ebVw10F0g6cdbr8YEhIKpmYtJxjqTnh+ZgNW980
  0hJlsoaKg8pzZxY+bKhqL0Xy2LJUbLtersvtiyOZYN7PH+U6GQAWjBtr4rCuQPT5
  5DuBDeBHebC6SpAEKhr/KqRFzSqeK5FztyorCu+8c0hlmqk1L5plK80CgYEAxm3l
  7q6RMfAmLkIKeM/xZLEqG85G7w0mn9Wc0o28+aMImlTx/qstvv4JI72phgoJxtKT
  R8ssL6dSd89ZTI+/35UNqYDA5ygbyCNLPmDOdnM/fe8Ydr/GZEozteRX4f0+A2Ct
  gmsnKolkccVfnc3MahsXDHKE+IE9ZmQYrWdX9uUCgYBkn+T1kE2NAuSLFp70D7Ao
  uU88Ls5MzynTD4LDk7xUw+Gv8/zvaaDu5x/eLZAnvqpvQyvSSWHAE7jY8Qh0VrRn
  41oBg2CWAw6mUXzwD1RnW/8NN6D7zJayD7OcEl2Nmvql3wqQbaJZ0HcnpNKccMFD
  yKQmQ/cx39odbxXOtBvwpQKBgQCSMQ2iWAKpJCE9G3LTp4BViyFW8xbXsHywbZTo
  m3yK/06rRcI0urEtccQSDP4EvwiM7z+LOWkIguIDW0STX6UheJNkOnPk2mv9e+NH
  xdLW+fnhMnJ3qrrj0LdgXydQXF9/5Y5v87obYLYcDCpx/NmJowPMK+NDoxQ1h7GW
  r/ji8QKBgGmLcTQ0ZgZea7vP6fvik/6kayuKz5OT5/nE3eEO+D84mz9vU7AFn2wf
  G53punMQq/lZ2lfYPgw4eJGL9OiKs6+rBGCi2UoW8ybUDrH8vl5V0URRr0xah1Q6
  qvTFPQEUOn3/DgRZgUHMbdtEbUQlxrvQCCbKou10QQpbX+bnfvIK
  -----END RSA PRIVATE KEY-----
deploy_key : |
   -----BEGIN RSA PRIVATE KEY-----
   MIIEpAIBAAKCAQEA0ehcT11UEPQtffohtr4h91u9v706UX+8newdlZq2VRMnKusd
   MRTb6ONJfbd+xz3yYYhzZY2NID19PGPM/t0BKJZrvtJJH4S7/1VB3aZTzntk9kb7
   oYt43pN9PGHvCrV7o7ssHkOZ4RslY9s1bpsuG6WCGzkyzFraNj0X5mZ/5NpsmEqU
   R1JWCWwHBptCwzAF1Wg1RNeIkwd1fLIVbpPXGLNr+mrO08YnRooyID27+BEr2LA9
   n556nZrgi3PUtnwKmelcrRY1v97JZAXqIM69y3RBfqJISRV5w7HsRQA12tn3PgfE
   b+zGcq+hC+GOWR86g749C1zAYBbKY9blN3R9+wIDAQABAoIBAQC4qZlj/K/zRk0r
   Mb0tHjGVgjD5GIjQn/aYW9te/L+BMptXh4Wj4zzfsey6W459y8KLCVaztYa9ITsm
   wIncgSL+yO467paD0urs4t1SGHxL/4Q/oQzH/oI0FT6su19nZWdDEGvsp/4c6hvH
   sFZeWsiCa+V8+6Hz4asdadasdasdasdasdasdasItbknuKguUEMpYCd9xz9g1D4s
   iLqpQRph8YLxjRPZJ4obA5dAEdBgRta/FtG8RIb4Jnbn1Ds6MH5SoWikZp3AVoMR
   BZO4RflL9aplEVuKUVtKj+gC48QkUswceePpF+uRGmVYJknmTLFqFtLxt31NJQUN
   BxGMS0KxAoGBAPJrD9J+JTkarYo9DNgk9XP4qg/rePG2kDPKzrQii4LrN97joxvz
   gluy+72FZ0WFw0OGwwif0SDw3On4D2QddifgWMNpN9GM0sBGRq2Kl0kjaCahE7RP
   57j1UdP+x1FIjDYJgEUkts2W/o7nHmAlHTyrxT5tmWtcG261+sNKgH5pAoGBAN2r
   AkG7dx+4Y2ADSMSSg3isssZuX3DtnZfkwE00hKyGMskaPkt52GhgFSAvSpAsMm1N
   8hZscIEq2c611Ztpq2DxCr0W61xOD19y/LnL+b0e8VwqDu7JLjm9a/qMTGzYbZtX
   pHV/r5hiv+LHC25n6UCEyxCh2JidZyAeNtxxlBTDAoGABKNzzA1J3QvbojeE1WXv
   pGZvqppQ2B8sJzGMPvoiPUEO8p7cch54shR8qKWy0iu7DsG3XaThNYYmU/vBH6NI
   rX6ndCXBQas2JSOzGoL6XhXlWkfevqaAwpM/G5VWbwG6XRZVc/092jU3bbiSZjiP
   lKecwJMMSneatsWYpL/6MXECgYEAy04pB7i0jTdEja71crUeN/PNFAnvJ1gIDmQT
   q7vbY5DBy4hyUi8yuKhHN/mn3YtrxKyUuNREa3OtyNUlUSEdug/Z1YvL2iEOIHEK
   Mi5Oo5JZtDou7/s8lmCRRH6hKcNm4+8CO3Iczxri+0+rwFs1p6Mjy+FlErRq/R45
   Gv5g3pkCgYBnvRQ1b3s5eddyOUz5iYW/Vshh8Hr73ZlzjIaS7N7x5u5K48Xv1C2g
   Hcn1QWh0zj69EcwhmG99DdVg8XXtpSv7GQoBRIhS3qg5UbNGPAexmx+k9pDsWW04
   zblEIppkjFxJcc0srC65PSDpCvKa6UrOOik3Bt4u4Rh1NYZ4u/+Rvg==
   -----END RSA PRIVATE KEY-----
heroku_email: glenn.bech@gmail.com
heroku_api_token: 1fceedcc-12343434-4781-9416-8c4ddf61f59b
```

# Kjør pipeline

Følgende kommando vil lage en concourse pipeline. Når pipeline kjører så vil
concourse automatisk publisere det som ligger i Master branchen din, til heroku
applikasjonen

```
fly -t pgr301 sp  -p heroku-example -c concourse/pipeline.yml -l credentials.yml
```

* -p er pipeline navnet som dukker opp i menyen i concourseci
* -l er variabler
* -c er lenke til pipeline.yml
