# INFORMATIEVE_GEWIJZIGDE_BEMIDDELINGSPECIFICATIE_ZORGKANTOOR

## Documentatie

Notificatie aan het uitvoerende zorgkantoor als het verantwoordelijke zorgkantoor een  Bemiddelingspecificatie heeft gewijzigd, die niet voor dat uitvoerende zorgkantoor is of voor het verantwoordelijke zorgkantoor zelf. 

Het uitvoerende (bovenregionale) zorgkantoor is daarmee informatief geïnformeerd over een wijziging van een bemiddelingsspecificatie, naast een overlappende bemiddelingspecificatie van dat zorgkantoor zelf.

De notificatie bevat informatie waarmee dat zorgkantoor de Bemiddelingspecificatie kan raadplegen. 

## Aanleiding
**De trigger voor de notificatie is:** 

> de wijziging van een Bemiddelingspecificatie in het Bemiddelingsregister

## Instructie
**Stel notificatie op voor:** 
elk uitvoerende zorgkantoor (`Bemiddelingspecificatie.uitvoerendZorgkantoor`) met een Bemiddelingspecificatie waarvan op het moment van wijziging van een Bemiddelingspecificatie: 
- de toewijzingIngangsdatum (of eerder vaststellingMoment) van de eigen Bemiddelingspecificatie voor of gelijk is aan de toewijzingEinddatum (of later vaststellingMoment) van de gewijzigde Bemiddelingspecificatie en 
- de toewijzingEinddatum van de eigen Bemiddelingspecificatie na of gelijk is aan de toewijzingIngangsdatum (of eerder vaststellingMoment) van de gewijzigde Bemiddelingspecificatie.
- en de toewijzingEinddatum van de eigen Bemiddelingspecificatie kleiner of gelijk is aan  31 mei van het jaar dat volgt op de einddatum van die eigen Bemiddelingspecificatie.

## Type
Het type-notificatie: 
> VERPLICHT (*zolang er geen abonnementenregistratie beschikbaar is*)

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
trigger:- Wijziging van
trigger:- Bemiddelingspecificatie
  opstellen:Stel notificatie
  opstellen:- INFORMATIEVE_GEWIJZIGDE_BEMIDDELINGSPECIFICATIE_ZORGKANTOOR
    opstellen: - voor het uitvoerendZorgkantoor
    opstellen: - met een met de gewijzigde bemiddelingspecificatie
    opstellen: - overlappende bemiddelingspecificatie
    opstellen: - als dit een ander is dan het verantwoordelijke zorgkantoor
    opstellen: - en niet hetzelfde als het uitvoerende zorgkantoor van de 
    opstellen: - gewijzigde bemiddelingspecificatie zelf
  verstuur:Verstuur 
  verstuur:notificatie
  ontvanger:Uitvoerend zorgkantoor
  ontvang:Ontvang 
  ontvang:notificatie
  verwerk:Verwerk 
  verwerk:notificatie
```


## Inhoud van de notificatie

| Variabele | Waarde | Voorbeeld | 
| :-- | :-- | :-- |
| timestamp | {timestamp} | ```"timestamp": "2024-07-02T00:00:00.000Z"``` | 
| afzenderIDType | "UZOVI" | ```"afzenderIDType": "UZOVI"``` |
| afzenderID | {uzovi-code afzender} | ```"afzenderID": "5050"``` |
| ontvangerIDType | "UZOVI" | ```"ontvangerIDType": "UZOVI"``` |
| ontvangerID | {uzovi-code ontvanger} | ```"ontvangerID": "5151"``` |
| ontvangerKenmerk | NULL | |
| eventType | "INFORMATIEVE_GEWIJZIGDE_BEMIDDELINGSPECIFICATIE_ZORGKANTOOR" | ```"eventType": "INFORMATIEVE_GEWIJZIGDE_BEMIDDELINGSPECIFICATIE_ZORGKANTOOR"``` |
| subjectList |  | ```"subjectList": [{```|
| ../subject | "Bemiddeling/{bemiddelingID}" | "subject": "Bemiddeling/ef88ce35-58fa-4e6d-ac7a-6e298dd211d6"|
| ../recordID | "Bemiddelingspecificatie/{bemiddelingspecificatieID}" | "recordID": "Bemiddelingspecificatie/ef88ce35-58fa-4e6d-ac7a-6e298dd211d6" |
| | | ```}]``` | 



## Andere notificaties Bemiddelingsregister
[Andere notificaties Bemiddelingsregister](README.md)

## Meer informatie over Notificaties

Meer informatie over notificeren in het [Afsprakenstelsel iWlz](https://wlz.atlassian.net/wiki/x/5AlgAQ?atlOrigin=eyJpIjoiNzMyN2E3MjM3YjQwNGQ4MmFkZDgwNWY0ZmE0MDIzMGEiLCJwIjoiYyJ9): [link](https://wlz.atlassian.net/wiki/x/5AlgAQ?atlOrigin=eyJpIjoiNzMyN2E3MjM3YjQwNGQ4MmFkZDgwNWY0ZmE0MDIzMGEiLCJwIjoiYyJ9)
