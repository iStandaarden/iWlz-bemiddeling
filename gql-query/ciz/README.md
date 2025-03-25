# CIZ
| Deelnemer | rol | toelichting |
| :-- | :-- |:-- |
| CIZ | [notificatie](#ciz---notificatie) | Het CIZ raadpleegt het Bemiddelingsregister voor het informeren van alle betrokken verantwoordelijk zorgkantoren van wijzigingen op een Wlz Indicatie | 

## CIZ - notificatie 


**Schematisch:**
```mermaid
---
config:
  theme: neutral
  look: classic
---
stateDiagram
  [*] --> raadplegen
  raadplegen --> QBR0010CIZiq
  QBR0010CIZiq --> QBR0010CIZ
  QBR0010CIZ --> [*]

  raadplegen: Raadplegen Bemiddelingsregister voor verantwoordelijk zorgkantoor
  QBR0010CIZiq: Gebruik wlzIndicatieID
  QBR0010CIZ: Gebruik template QBR-0010-CIZ

  style notifyWait fill:#FFD600
  style raadplegen fill:#BBDEFB,color:none
  style QBR0010CIZiq fill:#C8E6C9
  style QBR0010CIZ fill:#00C853

```

| **Query ID** | **Beschrijving** | **Verplichte input** | **resultaat** | **Autorisatie** |
|---|---|---|---|---|
| [QBR-0010-CIZ](/gql-query/ciz/QBR-0010-CIZ.graphql) | Raadplegen bij Wlz Indicatie betrokken verantwoordelijke zorgkantoren | wlzIndicatieID | Alle bij een Wlz Indicatie betrokken verantwoordelijke zorgkantoren | [BRA0011](https://informatiemodel.istandaarden.nl/informatiemodel/iwlz/netwerk/bemiddelingsregister-1/regels/autorisatieregel/bra0011/)