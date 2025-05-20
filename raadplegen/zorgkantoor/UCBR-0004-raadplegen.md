# Raadplegen van de **eigen** Bemiddelingspecificatie door het (bovenregionaal) uitvoerend zorgkantoor (UCBR-0004) 

```mermaid
---
config:
  theme: mc
  look: classic
  layout: elk
---
flowchart LR
 subgraph s1["Bemiddelingsregister"]
          B["Raadplegen eigen Bemiddelingspecificatie"]
  end
    A["Zorgkantoor<br>(uitvoerend)"] --> B
    B@{ shape: terminal}
    A@{ shape: rounded}
    style s1 fill:#FFF9C4,stroke:#FFF9C4
```


## **Use Case Beschrijving**  
**Titel:** Raadplegen van **eigen** Bemiddelingspecificatie door een (bovenregionaal) uitvoerend zorgkantoor.  
**Actoren:** Zorgkantoor dat contract heeft met de zorgaanbieder die betrokken is bij de levering van zorg aan een client.  

### Precondities:
- De Bemiddelingspecificatie is opgenomen in het Bemiddelingsregister.
- Het zorgkantoor is betrokken bij de levering van zorg aan de client door de registratie van een bemiddelingspecificatie door het verantwoordelijk zorgkantoor.


### Autorisatie:
Het zorgkantoor mag de toewijzing raadplegen. 
- Volledige autorisatieregel: [BRA0006](https://informatiemodel.istandaarden.nl/informatiemodel/iwlz/netwerk/bemiddelingsregister-1/regels/autorisatieregel/bra0006/)
- Autorisatiematrix: [BRA0006](https://github.com/iStandaarden/iWlz-Autorisatiematrix/blob/main/autorisatiematrix_bemiddelingsregister.md)

**Trigger:**
- Een zorgkantoor wil de bemiddelingspecificatie raadplegen waarin het is geregistreerd als uitvoerend zorgkantoor.


## Query-template beschrijving

| **Query ID** | **Beschrijving** | **Verplichte input** | **resultaat** |
|---|---|---|---|
| [**QBR-0004-ZKu**](/gql-query/zorgkantoor/QBR-0004-ZKu.graphql) | Op basis van de (ontvangen) bemiddelingspecificatieID en eigen identificatie, de Bemiddelingspecificatie, Bemiddeling en Cliënt gegevens raadplegen | `bemiddelingspecificatieID`, `uzoviCode` | Bemiddelingspecificatie /  Bemiddeling /  Client |

## **Proces raadplegen**

Een zorgaanbieder wordt bij de zorg van een client betrokken door het zorgkantoor. Het zorgkantoor registreert een bemiddelingspecificatie (toewijzing) voor het leveren van zorg door de zorgaanbieder. Als de zorgaanbieder contract heeft bij een zorgkantoor uit een andere regio (bovenregionaal) dan het verantwoordelijke zorgkantoor, ontvangt dat bovenregionale zorgkantoor de notificatie [`NIEUWE_BEMIDDELINGSPECIFICATIE_ZORGKANTOOR](/notificaties/nieuwe_bemiddelingspecificatie_zorgkantoor.md). Op basis van deze notificatie kan het zorgkantoor de informatie in het bemiddelingsregister raadplegen. 

> [!NOTE]
> Voor een volledige beeld moeten er altijd 2 bevragingen worden uitgevoerd.
> Te beginnen met de hier beschreven raadpleging, voor het ophalen van de eigen toewijzing periode. Vervolgens één van de twee andere queries voor de overlappende zorgtoewijzingen. Die use-case is beschreven in [UCBR-0005_6-raadplegen](UCBR-0005_6-raadplegen.md).

### Schematisch:

```mermaid
---
config:
  theme: neutral
  look: classic
---
stateDiagram
  direction TB

  [*] --> raadplegen
  raadplegen --> welke
  welke --> idAvailable:eigen
  
  idAvailable --> notifyWait:nee
  idAvailable --> QBR0001ZAiq:ja
  notifyWait --> notifyReceive
  notifyReceive --> QBR0001ZAiq
  QBR0001ZAiq --> QBR0001ZA
    state andere {
    direction TB
    anderequery
  }
  welke --> andere:eigen + overige + contactgegevens
  QBR0001ZA --> PEP
  PEP --> [*]:geen toegang
  PEP --> resource:toegang
  resource --> [*]
  andere:Eigen, andere toewijzingen, regiehouder en contact raadplegen
  anderequery:Ga naar de andere beschrijving
  anderequery: UCBR-0005_6-raadplegen
  raadplegen:Raadplegen Bemiddelingsregister voor toewijzing(en)
  welke:Eigen toewijzing of ook overlappende toewijzing(en) en contactgegevens
  idAvailable:bemiddelingspecificatieID bekend?
  notifyWait:Wacht op notificatie
  QBR0001ZAiq:Gebruik bemiddelingspecificatieID + UzoviCode
  notifyReceive:notificatie NIEUWE_BEMIDDELINGSPECIFICATIE_ZORGKANTOOR ontvangen
  QBR0001ZA:Gebruik template QBR-0004-ZKu
  PEP:Toegangscontrole PEP
  style raadplegen fill:#BBDEFB,color:none
  style notifyWait fill:#FFD600
  style notifyReceive fill:#C8E6C9
  style QBR0001ZA fill:#00C853

```


| # | Toelichting |
| --: | :-- |
| 1. | *Start* raadplegen **eigen** bemiddelingspecificatie | 
| 2. | Is de **`bemiddelingspecificatieID`** bekend? <br/> - **Ja** →  Ga verder naar stap 6 <br/> - **Nee** → Wacht op notificatie [**`NIEUWE_BEMIDDELINGSPECIFICATIE_ZORGKANTOOR`**](/notificaties/nieuwe_bemiddelingspecificatie_zorgkantoor.md)  | 
| 4. | Notificatie is ontvangen | 
| 5. | Gebruik de informatie uit de notificatie voor het raadplegen van het bemiddelingsregister |
| 6. | Het zorgkantoor vult de verplichte **`bemiddelingspecificatieID`** in query-template [QBR-0004-ZKu.graphql](/gql-query/zorgkantoor/QBR-0004-ZKu.graphql) en initieert een raadpleging van de bemiddelingspecificatie in het Bemiddelingsregister. | 
| 7. | Het zorgkantoor stuurt Graphql-request + Access-token naar het Policy Enforcement Point (PEP) |
| 8. | De PEP voert de [toegangscontrole](UCBR-0004-toegangscontrole.md) uit en stuurt bij toegang het request door naar het Bemiddelingsregister. |
| 9. | Het zorgkantoor ontvangt response van de PEP (bij ongeldig verzoek) of vanuit het Bemiddelingsregister (resource) |
| 10. | *Einde proces* | 


---

Ga naar beschrijving van de bijbehorende [toegangscontrole](UCBR-0004-toegangscontrole.md) | Ga naar [UCBR-0005_6-raadplegen](UCBR-0005_6-raadplegen.md) voor de beschrijving van het raadplegen van de overlappende toewijzingen |  Terug naar [Raadplegen](/raadplegen/README.md)
