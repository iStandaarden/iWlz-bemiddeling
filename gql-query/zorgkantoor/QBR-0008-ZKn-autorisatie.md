# Autorisatie-flow Zorgaanbieder: QBR-0008-ZKn.graphql

Beschrijving van het autorisatieproces door de PEP, voor query [QBR-0008-ZKn.graphql](/gql-query/zorgkantoor/QBR-0008-ZKn.graphql).

**schematisch:**

```mermaid
---
config:
  theme: neutral
  look: classic
---
stateDiagram
  direction TB
  [*] -->  indienen
  indienen --> validerenT
  state nID {
    direction TB

    validerenT --> validerenR
    validerenR --> checkInput01


    state check01 <<choice>>
    checkInput01 --> check01
    check01 --> error:nee
    check01 --> checkInput02:ja

    state check02 <<choice>>
    checkInput02 --> check02
    check02 --> error:nee
    check02 --> access:ja
   

  }

  error --> [*]
  access --> resource
  resource --> [*]
  
  nID:Autorisatie controle PEP
  indienen: Ontvang  QBR-0008-ZKn.graphql + Access token
  validerenT: Valideer access token
  validerenR: Valideer Request
  checkInput01:Check input aanwezig?
  checkInput01:- overdrachtID
  checkInput01:- verantwoordelijkZorgkantoor
  checkInput01:- overdrachtDatum
  checkInput02:Check
  checkInput02:input verantwoordelijkZorgkantoor matcht Access token
  error:geen toegang tot Resource

  access:toegang tot Resource
  resource: Query mag door naar Bemiddelingsregister
  style validerenT,validerenR fill:#FFD600
  style valideer2 fill:#C8E6C9
  style error fill:#D50000
  style access,Query,resource fill:#00C853
  style indienen fill:#BBDEFB,color:none

```

Controle query PIP:
```gql
niet van toepassing

```


---
[Terug naar Query overzicht](/gql-query/README.md)