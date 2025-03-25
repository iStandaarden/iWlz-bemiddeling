# VERWIJDERDE_BEMIDDELINGSPECIFICATIE_ZORGAANBIEDER

## Documentatie

Notificatie aan de zorgaanbieder als het verantwoordelijke zorgkantoor een Bemiddelingspecificatie van deze zorgaanbieder heeft verwijderd.

De zorgaanbieder is daarmee geïnformeerd over een verwijdering van een bemiddelingsspecificatie voor het leveren van zorg aan een client. 

## Aanleiding
**De trigger voor de notificatie is:** 

> de verwijdering van een Bemiddelingspecificatie in het Bemiddelingsregister

## Instructie
**Stel notificatie op voor:** 
> de zorgaanbieder die geregistreerd is onder instelling in de Bemiddelingspecificatie.

## Type
Het type-notificatie: 
> VERPLICHT

## Schematisch

```mermaid
---
config:
  theme: neutral
  look: classic
---
stateDiagram
  direction LR
  state verzender {
    direction TB
    trigger --> opstellen
    opstellen --> verstuur
    trigger
    opstellen
    verstuur
  }
  state ontvanger {
    direction TB
    ontvang --> verwerk
    ontvang
    verwerk
  }
  [*] --> trigger
  verstuur --> ontvang
  verwerk --> [*]
  verzender:Verantwoordelijk zorgkantoor
  trigger:Trigger
trigger:- Verwijdering van een
trigger:- Bemiddelingspecificatie
  opstellen:Stel notificatie
opstellen:- VERWIJDERDE_BEMIDDELINGSPECIFICATIE_ZORGAANBIEDER
opstellen:- voor de zorgaanbieder
opstellen:- in de bemiddelingspecificatie
  verstuur:Verstuur 
  verstuur: notificatie
  ontvanger: Zorgaanbieder
  ontvang:Ontvang 
  ontvang:notificatie
  verwerk:Verwerk 
  verwerk:notificatie

```


## Inhoud van de notificatie

| Variabele | Waarde | Voorbeeld | 
| :-- | :-- | :-- |
| timestamp | {timestamp} | ```"timestamp": "2024-07-02T00:00:00Z"``` | 
| afzenderIDType | "UZOVI" | ```"afzenderIDType": "UZOVI"``` |
| afzenderID | {uzovi-code ontvanger} | ```"afzenderID": "5050"``` |
| ontvangerIDType | "AGBCODE" | ```"ontvangerIDType": "AGBCODE"``` |
| ontvangerID | {uzovi-code ontvanger} | ```"ontvangerID": "12345678"``` |
| ontvangerKenmerk | NULL | |
| eventType | "VERWIJDERDE_BEMIDDELINGSPECIFICATIE_ZORGAANBIEDER" | ```"eventType": "VERWIJDERDE_BEMIDDELINGSPECIFICATIE_ZORGAANBIEDER"``` |
| subjectList |  | ```"subjectList": [{```|
| ../subject | "Bemiddeling/{bemiddelingID}" | "subject": "Bemiddeling/ef88ce35-58fa-4e6d-ac7a-6e298dd211d6"|
| ../recordID | "Bemiddelingspecificatie/{bemiddelingspecificatieID}" | "recordID": "Bemiddelingspecificatie/ef88ce35-58fa-4e6d-ac7a-6e298dd211d6" |
| | | ```}]``` | 



## Andere notificaties Bemiddelingsregister
[Andere notificaties Bemiddelingsregister](README.md)

## Meer informatie over Notificaties

Meer informatie over notificeren in het [Afsprakenstelsel iWlz](https://wlz.atlassian.net/wiki/x/5AlgAQ?atlOrigin=eyJpIjoiNzMyN2E3MjM3YjQwNGQ4MmFkZDgwNWY0ZmE0MDIzMGEiLCJwIjoiYyJ9): [link](https://wlz.atlassian.net/wiki/x/5AlgAQ?atlOrigin=eyJpIjoiNzMyN2E3MjM3YjQwNGQ4MmFkZDgwNWY0ZmE0MDIzMGEiLCJwIjoiYyJ9)
