# Toegangscontrole: Raadplegen van de eigen en overlappende Bemiddelingspecificatie(s) en overige informatie door het zorgkantoor (UCBR-0005_6)

Beschrijving van de **toegangscontrole** door de Policy Decision Point (PDP) en indien van toepassing Policy Information Point (PIP).

N.b. Het valideren van de Acces-token door de PEP is geen onderdeel van de ze beschrijving. Zie daarvoor het [Afsprakenstelsel iWlz - nID netwerkstelsel - 5. Policy Enforcement Point.](https://wlz.atlassian.net/wiki/spaces/IWLZAS/pages/229441537/nID+netwerkstelsel#5.-Policy-Enforcement-Point-(PEP))

## Toegangscontrole PDP
### Subject
- **Entiteit:** Zorgkantoor (bovenregionaal)
- **Kenmerk:** In bezit van een access-token met eigen `uzovicode`


### **Action**
- **Type:** `raadplegen` (read)
- **Omschrijving:** Uitvoeren van GraphQL-query [`QBR-0005-ZKu.graphql`](/gql-query/zorgkantoor/QBR-0005-ZKu.graphql) of [`QBR-0006-ZKu.graphql`](/gql-query/zorgkantoor/QBR-0006-ZKu.graphql) (wanneer de eigen `bemiddelingspecificatie` een einddatum heeft) op het bemiddelingsregister door een zorgaanbieder. 


### **Resource**
- **Type:** `Bemiddelingsregister`
- **ID:** `bemiddelingspecificatieID`
- **Beperking:** Toegang tot gegevens waarvoor het zorgkantoor een toewijzing heeft en de gegevens die periode-overlap hebben met die toewijzing
- **Inhoud:** De nodes Bemiddelingspecificatie en de gerelateerde Bemiddeling en Client die horen bij de opgevraagde Bemiddelingspecificatie, en de Regiehouder, contactgegevens, contactpersoon en Bemiddelingspecificaties van andere aanbieders die in periode overlap hebben met de eigen Bemiddelingspecificatie, mogen direct worden opgevraagd.


### **Context**
- **Query-parameters vereist:** 
  | QBR-0005-ZKu                   | QBR-0006-ZKu                   |
  | :---------------------------- | :---------------------------- |
  | - `bemiddelingspecificatieID` | - `bemiddelingspecificatieID` |
  | - `uitvoerendZorgkantoor`     | - `uitvoerendZorgkantoor`     |
  | - `toewijzingIngangsdatum`    | - `toewijzingIngangsdatum`    |
  | - `vaststellingMoment`        | - `vaststellingMomemnt`       |
  | - `DagVaststellingMoment`     | - `DagVaststellingMoment`     |
  | - `toewijzingEinddatum`       |                               |

- **Toegangsvoorwaarde:**  Er is alleen toegang als aan alle volgende voorwaarden is voldaan:
  - De parameters zoals hierboven zijn aanwezig
  - De **access-token** bevat een geldige `uzovicode` van het zorgkantoor;
  - De `uzovicode` van de in de query meegegeven `uitvoerendZorgkantoor` komt overeen met de `uzovicode` in de access-token;
  - Voor contactgegevens en contactpersonen geldt toegang tot en met EinddatumToewijzing + 2 jaar;
  - Voor Bemiddelingspecificaties geldt toegang tot en met Einddatum + 31mei.


### Resultaat

> Toegang tot het Bemiddelingsregister via query [`QBR-0005-ZKu.graphql`](/gql-query/zorgkantoor/QBR-0005-ZKu.graphql) of [`QBR-0006-ZKu.graphql`](/gql-query/zorgkantoor/QBR-0006-ZKu.graphql) is **alleen toegestaan** als:
>
> - De relevante parameters aanwezig zijn per query;
> - De access-token bevat een geldige **`uzovicode`**
> - De in de query meegegeven `uzovicode` in `uitvoerendZorgkantoor` komt overeen met de `uzovicode` in de access-token;
> 
>
> Als aan deze voorwaarden is voldaan, mogen de volgende gegevens worden opgevraagd:
> - De `Bemiddelingspecificatie`, de bijbehorende `Bemiddeling` en `Client`;
> - De `Contactpersoon`, `Contactgegevens`, `Regiehouder`, en andere `Bemiddelingspecificaties` binnen dezelfde Bemiddeling, mits deze een periode-overlap hebben met de eigen toewijzing;
> - Voor contactgegevens en contactpersonen geldt toegang tot en met EinddatumToewijzing + 2 jaar;
> - Voor Bemiddelingspecificaties geldt toegang tot en met Einddatum + 31mei.


## Toegangscontrole-flows Zorgkantoor: QBR-0005-ZKu.graphql of QBR-0006-ZKu.graphql

Beschrijving van het autorisatieproces door de PEP.

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
  indienen: Ontvang QBR-0002-ZA of QBR-003-ZA + Access token
  validerenT: Valideer access token
  validerenR: Valideer Request
  checkInput01:Check  verplichte input aanwezig?

  checkInput02:Check
  checkInput02:input Instelling matcht met
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
| 3. |De **PDP** controleert op:<br/>1. Of het request voldoet aan de template en er geen ongeoorloofde gegevens worden opgevraagd.<br/>2. Aanwezigheid van de verplichte parameters in het request;<br/>3. Of de **`uzovicode`** in request overeenkomt met de waarde in de **`access-token`**;<br/>4. Of indien contactgegevens en Contactpersoon onderdeel zijn van het request, de datum van het request kleiner dan of gelijk is aan ToewijzingEinddatum + 2 jaar;<br/>5. Of indien Bemiddelingspecificatie onderdeel is van het request, de datum van het request kleiner dan of gelijk is aan ToewijzingEinddatum + 31 mei <br/><br/>Is aan alle voorwaarden voldaan?<br/> - **Ja** →  Ga verder naar stap 4<br/>- **Nee** → *Einde proces (geen toegang.)*   |
| 4. | Het zorgkantoor krijgt toegang tot het bemiddelingsregister.|
| 5. | *Einde* |


## Toegangscontrole PIP:
```gql
nvt

```


---
Ga naar [UC beschrijving raadplegen](UCBR-0005_6-raadplegen.md) -- Terug naar [Raadplegen](/raadplegen/README.md)
