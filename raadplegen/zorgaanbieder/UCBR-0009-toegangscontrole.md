# Toegangscontrole: Raadplegen van Regiehouder door de Zorgaanbieder (UCBR-0009)  

Beschrijving van de **toegangscontrole** door de Policy Decision Point (PDP) en indien van toepassing Policy Information Point (PIP).

N.b. Het valideren van de Acces-token door de PEP is geen onderdeel van de ze beschrijving. Zie daarvoor het [Afsprakenstelsel iWlz - nID netwerkstelsel - 5. Policy Enforcement Point.](https://wlz.atlassian.net/wiki/spaces/IWLZAS/pages/229441537/nID+netwerkstelsel#5.-Policy-Enforcement-Point-(PEP))

## Toegangscontrole PDP
### Subject
- **Entiteit:** Zorgaanbieder (toegewezen)
- **Kenmerk:** In bezit van een access-token met daarin de eigen `agbcode`


### **Action**
- **Type:** `raadplegen` (read)
- **Omschrijving:** Uitvoeren van GraphQL-query [`QBR-0009-ZAr.graphql`](/gql-query/zorgaanbieder/QBR-0009-ZAr.graphql) op het bemiddelingsregister door een zorgaanbieder


### **Resource**
- **Type:** `Bemiddelingsregister`
- **ID:** `regiehouderID`
- **Beperking:** Alleen toegang tot gegevens waarvoor de zorgaanbieder regiehouder is.
- **Inhoud:** Alleen de nodes Regiehouder en de gerelateerde Bemiddeling en Client die horen bij de opgevraagde Regiehouder, mogen direct worden opgevraagd.


### **Context**
- **Query-parameters vereist:** De `regiehouderID` en de `agbcode` moeten aanwezig zijn in de query
- **Toegangsvoorwaarde:**  Er is alleen toegang als aan alle volgende voorwaarden is voldaan:
  - De parameter `regiehouderID` is aanwezig in de query;
  - De parameter `agbcode` is aanwezig in de query;
  - De **access-token** bevat een geldige `agbcode` van de zorgaanbieder;
  - De in de query meegegeven `agbcode` komt overeen met de `agbcode` in de access-token;


### Resultaat

> Toegang tot het Bemiddelingsregister via query [`QBR-0009-ZAr.graphql`](/gql-query/zorgaanbieder/QBR-0009-ZAr.graphql) is **alleen toegestaan** als:
>
> - Parameter **`regiehouderID`** is meegegeven in de query
> - Parameter **`agbcode`** is meegegeven in de query
> - De access-token bevat een geldige **`agbcode`**
> - De in de query meegegeven `agbcode` komt overeen met de `agbcode` in de access-token; 
> 
> Als aan alle voorwaarden is voldaan, mogen de nodes `Regiehouder`, `Bemiddeling` en `Client` die horen bij deze `Regiehouder` direct worden opgevraagd.


## Toegangscontrole-flows Zorgaanbieder: QBR-0001-ZA.graphql

Beschrijving van het autorisatieproces door de PEP.

### **schematisch:**

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
  state PEP {
    direction TB

    validerenT --> validerenR: access-token is geldig
    state PDP {
    validerenR --> checkInput01
    state check01 <<choice>>
    checkInput01 --> check01

    check01 --> checkInput02:ja
    check01 --> error:nee
        state check02 <<choice>>
        checkInput02 --> check02
        check02 --> error:nee
        check02 --> access:ja
    error
    access
    }

  }

  error --> [*]
  access --> resource
  resource --> [*]
  
  PEP:Autorisatie controle PEP
  PDP:Toegangscontrole PDP
  indienen: Ontvang QBR-0009-ZAr + Access token
  validerenT: Valideer access token
  validerenR: Valideer Request
  checkInput01:Check input aanwezig?
  checkInput01:- regiehouderID
  checkInput01:- Instelling
  checkInput02:Check
  checkInput02:input Instelling matcht 
  checkInput02: waarde in Access token
  error:geen toegang tot Resource

  access:toegang tot Resource
  resource: Query mag door naar Bemiddelingsregister
  style validerenR,checkInput01,checkInput02 fill:#FFD600
  style valideer2 fill:#C8E6C9
  style error fill:#D50000
  style access,Query,resource fill:#00C853
  style indienen fill:#BBDEFB,color:none

```


| # | Toelichting |
| --: | :-- |
| 1. |Ontvangst GraphQL-request + access-token door **PEP** |
| 2. |De **PEP** valideert de access-token en geeft na goedkeur het request door aan de PDP |
| 3. |De **PDP** controleert op:<br/>1. Of het request voldoet aan de template en er geen ongeoorloofde gegevens worden opgevraagd.<br/>2. Aanwezigheid van de verplichte parameters in het request;<br/>3. Of de **`agbcode`** in request overeenkomt met de waarde in de **`access-token`**;<br/><br/>Is aan alle voorwaarden voldaan?<br/> - **Ja** →  Ga verder naar stap 4<br/>- **Nee** → *Einde proces (geen toegang.)*   |
| 4. | De zorgaanbieder krijgt toegang tot het bemiddelingsregister.|
| 5. | *Einde* |


## Toegangscontrole PIP:
```gql
nvt

```


---
Ga naar [UC beschrijving raadplegen](UCBR-0009-raadplegen.md) -- Terug naar [Raadplegen](/raadplegen/README.md)
