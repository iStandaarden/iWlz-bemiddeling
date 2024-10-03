# iWlz bemiddeling 1

**iWlz-bemiddeling bevat de [Graphql-schema](/gql-specificatie) koppelvlak specificatie en voorgeschreven [GraphQL-query templates](/gql-query/) voor het raadplegen van Wlz Bemiddelinggegevens in het bemiddelingsregister.**

Het bemiddelingsregister is in beheer bij de zorgkantoren en is onderdeel van het iWlz-netwerkmodel.

**Inhoud**
- [iWlz bemiddeling 1](#iwlz-bemiddeling-1)
  - [Onderdelen](#onderdelen)
    - [Schematisch](#schematisch)
    - [Graphql-schema](#graphql-schema)
    - [Graphql-query](#graphql-query)
    - [Open Agent Policy](#open-agent-policy)
  - [Versies en Status](#versies-en-status)
  - [Documentatie](#documentatie)
    - [Informatiemodel](#informatiemodel)
    - [GraphQL](#graphql)
    - [Open Agent Policy](#open-agent-policy-1)
  - [Meer informatie](#meer-informatie)
  - [Contactpersonen:](#contactpersonen)


## Onderdelen
Deze specificaties van het Bemiddelingsregister maken onderdeel uit van de **iStandaard iWlz**. De specificaties van de andere onderdelen, zoals ERD, regels, procesbeschrijving, autorisatieregels, notificatie-typen staan in het [Informatiemodel iWlz](https://informatiemodel.istandaarden.nl/) dat te vinden is via de website: [https://informatiemodel.istandaarden.nl/iWlz-Bemiddeling-1/](https://informatiemodel.istandaarden.nl/iWlz-Bemiddeling-1/)

### Schematisch
![onderdelen](/src/Onderdelen_Netwerk.png)
v.l.n.r. Raadpleger doet via GraphQL-query een raadpleging. Open Policy agent controleert of query voldoet aan autorisatie-regels van dat register. GraphQL-schema definieert het data-schema van het register.

### Graphql-schema 
De [Graphql-schema specificatie](/gql-specificatie/) is bedoelt voor implementatie door de bronhouder en beschrijft hoe de data aan elkaar is gerelateerd. De specificatie is te vinden in de folder [/gql-specificatie](/gql-specificatie/). 

### Graphql-query
De [Graphql-queries](/gql-query/) beschrijven het template hoe een raadpleger vanuit zijn rol informatie kan raadplegen. Deze template volgt altijd het GraphQL-schema maar moet op bepaalde momenten aan vaste patronen voldoen vanwege de geldende autorisatie. Gaat een raadpleger buiten dit patroon dan zal de vraag worden afgekeurd en krijgt de raadpleger geen inzicht in de data. 

In de folder [/gql-query](/gql-query/) staat een overzicht van de beschikbare templates inclusief een toelichting voor welke partij de template is.

### Open Agent Policy
De Open Agent Policy controleert of een query voldoet aan de daarvoor afgesproken template. De policy is gebaseerd op de autorisatieregels van dat register. 

De policy is beschikbaar in: @@@ nog te bepalen.


## Versies en Status 

Er zijn altijd minimaal twee versies actueel. Een versie die in productie is, status is *Lopend* en een versie die in ontwikkeling is, status is *In ontwikkeling*.


| iWlz Informatiemodel | Status | versie koppelvlak |
|:-- |:-- | :-- |
| *nvt* | *Lopend* | *nvt* |
| **Bemiddelingsregister 1** | In ontwikkeling | v1.1.0 (03-10-2024) |

Volledig versie overzicht zie: [Changelog](CHANGELOG.md)

> 
> **Status Koppelvlakspecificatie:** *In Ontwikkeling Bemiddeingsregister 1* 
>
> Het Bemiddelingsregister is nog in ontwikkeling. Momenteel is er nog geen versie in productie en ontbreekt er daarom een versie lopend.
> 

## Documentatie

### Informatiemodel

![informatiemodel](/src/Informatiemodel-sml.png)

Ondersteunende documentatie is te vinden in het Informatiemodel, via de website [https://informatiemodel.istandaarden.nl/](https://informatiemodel.istandaarden.nl/) en daar de gewenste versie te selecteren (zie ook in de tabel hierboven voor een directe verwijzing).

### GraphQL
![GraphQL](/src/GraphQL-logo-sml.png) 

zie [GraphQL.org](https://graphql.org) 

### Open Agent Policy
![OPA](/src/OPA-logo-sml.png) 

zie [Open Agent Policy](https://www.openpolicyagent.org) en [documentatie](https://www.openpolicyagent.org/docs/latest/)


## Meer informatie
* Actieprogramma iWlz: van keten naar netwerk: [het Actieprogramma iWlz](https://www.istandaarden.nl/iwlz/actieprogramma/index "Over Actieprogramma iWlz")
* Informatiemodel iStandaarden iWlz: [Informatiemodellen](https://informatiemodel.istandaarden.nl)
* Portaal voor iStandaarden in de
Zorg en Ondersteuning: [homepagina iStandaarden](https://www.istandaarden.nl)

## Contactpersonen:
* Dennis de Gouw - [@dennisdegouw](http://github.com/dennisdegouw)
* Remo van Rest - [@rvanrest](https://github.com/rvanrest)