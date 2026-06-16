# Toegangscontrole: Raadplegen van de zorgkantoren die als uitvoerend zorgkantoor betrokken zijn of waren bij de Wlz indicatie (UCBR-0011)

Beschrijving van de **toegangscontrole** door de Policy Decision Point (PDP) en indien van toepassing Policy Information Point (PIP).

N.b. Het valideren van de Acces-token door de PEP is geen onderdeel van deze beschrijving. Zie daarvoor het [Afsprakenstelsel iWlz - nID netwerkstelsel - 5. Policy Enforcement Point.](https://wlz.atlassian.net/wiki/spaces/IWLZAS/pages/229441537/nID+netwerkstelsel#5.-Policy-Enforcement-Point-(PEP)).

## Toegangscontrole PDP

### Subject
- **Entiteit:** CIZ
- **Kenmerk:** In het bezit van een acces-token met daarin de eigen `kvkcode`

### Action
- **Type:** `raadplegen` (read)
- **Omschrijving:** Uitvoeren van GraphQL-query [QBR-0011-CIZ.graphql](/gql-query/ciz/QBR-0011-CIZ.graphql) op het bemiddelingsregister door het CIZ

### Resource
- **Type:** `Bemiddelingsregister`
- **ID:** `wlzIndicatieID`
- **Beperking:** Alleen toegang tot gegevens waarvoor het CIZ autorisatie heeft.
- **Inhoud:** Alleen `uitvoerendZorgkantoor` in de `Bemiddelingspecificaties` horend bij de Bemiddeling bij het `wlzIndicatieID`. 

### Context
- **Query-parameters vereist:** Het `wlzIndicatieID` moet aanwezig zijn in de query
- **Toegangsvoorwaarde:**  Er is alleen toegang als aan alle volgende voorwaarden is voldaan:
  - De parameter `wlzIndicatieID` is aanwezig in de query;
  - De **access-token** bevat een geldige `kvkcode` van het CIZ.

### Resultaat

> Toegang tot het Bemiddelingsregister via query [`QBR-0011-CIZ.graphql`](QBR-0011-CIZ.graphql) is **alleen toegestaan** als:
>
> - Parameter **`wlzIndicatieID`** is meegegeven in de query
> - De **access-token** bevat een geldige `kvkcode` van het CIZ.
> 
> Als aan alle voorwaarden is voldaan, mag het `uitvoerendZorgkantoor` uit `Bemiddelingspecificatie` horend bij de `Bemidddeling` bij het `wlzIndicatieID` direct worden opgevraagd.

## Toegangscontrole-flows CIZ: QBR-0011-CIZ.graphql

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

    check01 --> access:ja
    check01 --> error:nee
    error
    access
    }

  }

  error --> [*]
  access --> resource
  resource --> [*]
  
  PEP:Autorisatie controle PEP
  PDP:Toegangscontrole PDP
  indienen: Ontvang QBR-0011-CIZ + Access token
  validerenT: Valideer access token
  validerenR: Valideer Request
  checkInput01:Check input aanwezig?
  checkInput01:- WlzIndicatieID
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
| 3. |De **PDP** controleert op:<br/>1. Of het request voldoet aan de template en er geen ongeoorloofde gegevens worden opgevraagd.<br/>2. Aanwezigheid van de verplichte parameters in het request;<br/><br/>Is aan alle voorwaarden voldaan?<br/> - **Ja** →  Ga verder naar stap 4<br/>- **Nee** → *Einde proces (geen toegang.)*   |
| 4. | De zorgaanbieder krijgt toegang tot het bemiddelingsregister.|
| 5. | *Einde* |


## Toegangscontrole PIP:
```gql
nvt

```


---
Ga naar [UC beschrijving raadplegen](UCBR-0011-raadplegen.md) -- Terug naar [Raadplegen](/raadplegen/README.md)
