# GraphQL-query templates
Een vraag wordt gesteld door een actor als deelnemer van het netwerk. Deze deelnemer stelt de vraag vanuit een bepaalde rol. Afhankelijk van de rol zijn gegevens wel of niet (direct) raadpleegbaar. 

Het moment waarop een actor een rol heeft is afhankelijk van een notificatie. 

_De lijst is nog niet volledig._


Op dit moment zijn de volgende rollen onderkent:
| Deelnemer | rol | toelichting |
| :-- | :-- |:-- |
| Zorgaanbieder | [uitvoerend](#zorgaanbieder---uitvoerend) | Een zorgaanbieder die betrokken is bij de uitvoering van zorg |
| Zorgaanbieder | [dossierhouder](#zorgaanbieder---dossierhouder) | Een zorgaanbieder die verantwoordelijk is voor de uitvoering van verblijfszorg |
| Zorgaanbieder | [coordinator zorg thuis](#zorgaanbieder---coordinator-zorg-thuis) | Een zorgaanbieder die verantwoordelijk is voor de uitvoering van zorg thuis (mpt) | 
| Zorgkantoor | [verantwoordelijk](#zorgkantoor---verantwoordelijk) | Een zorgkantoor die verantwoordelijk is van de client (i.c.m. de Wlz Indicatie) en zorgt voor de registratie van die gegevens in het bemiddelingsregister | 
| Zorgkantoor | [uitvoerend](#zorgkantoor---uitvoerend) | Een zorgkantoor dat uitvoerend is betrokken bij de uitvoering van zorg i.v.m. zorg uit een andere regio | 
| Zorgkantoor | [nieuw verantwoordelijk](#zorgkantoor---nieuw-verantwoordelijk) | Het zorgkantoor dat de client krijgt overgedragen van het huidige verantwoordelijk zorgkantoor |

< documentatie aanvullen >

## Beschikbare templates per rol

### Zorgaanbieder - uitvoerend
Na ontvangst van de notificatie: *NIEUWE_BEMIDDELINGSPECIFICATIE_ZORGAANBIEDER* of ad-hoc om complete toewijzing te raadplegen.

| **Query ID** | **Beschrijving ** | **Verplichte input** | **resultaat** | **Autorisatie** |
|---|---|---|---|---|
| [**QBR-0001-ZA**](QBR-0001-ZA.graphql) | Op basis van de (ontvangen) bemiddelingspecificatieID en eigen identificatie, de bijbehorende Bemiddelingspecificatie, Bemiddeling en Cliënt gegevens raadplegen | bemiddelingspecificatieID (V),  AGBcode (V) | Bemiddelingspecificatie /  Bemiddeling /  Client | BRA0001 |
| [**QBR-0002-ZA**](QBR-0002-ZA.graphql) | Op basis van de bemiddelingsspecificatieID, eigen identificatie en toewijzingIngangdatum en toewijzingeinddatum, de (overlappende) Bemiddelingspecificatie(s), Bemiddeling, Client, Dossierhouder, CoordinatorZorgThuis, Contactpersoon en Contactgegevens raadplegen | bemiddelingspecificatieID (V),  AGBcode (V), toewijzingIngangsdatum (V), toewijzingEinddatum(V) | Bemiddelingspecificatie /  Bemiddeling /  Client /  Dossierhouder /  Coordinator zorg thuis /  Contactgegevens | BRA0002, BRA0004, BRA0005 |
| [**QBR-0003-ZA**](QBR-0003.graphql) | Op basis van de bemiddelingsspecificatieID, eigen identificatie en toewijzingIngangdatum, de (overlappende) Bemiddelingspecificatie(s), Bemiddeling, Client, Dossierhouder, CoordinatorZorgThuis, Contactpersoon en Contactgegevens raadplegen | bemiddelingspecificatieID (V),  AGBcode (V), toewijzingIngangsdatum (V) | Bemiddelingspecificatie /  Bemiddeling /  Client /  Dossierhouder /  Coordinator zorg thuis /  Contactgegevens | BRA0002, BRA0004, BRA0005 |

![img](../src/Zorgaanbieder_Uitvoerend.png)

### Zorgaanbieder - dossierhouder
Na ontvangst van de notificatie: _ROL_DOSSIERHOUDER_ZORGAANBIEDER_

| **Query ID** | **Beschrijving** | **Verplichte input** | **resultaat** | **Autorisatie** |
|---|---|---|---|---|

### Zorgaanbieder - coordinator zorg thuis
Na ontvangst van de notificatie: _ROL_COORDINATORZORGTHUIS_ZORGAANBIEDER_

| **Query ID** | **Beschrijving** | **Verplichte input** | **resultaat** | **Autorisatie** |
|---|---|---|---|---|

### Zorgkantoor - verantwoordelijk
Na de ontvangst van de notificatie: *NIEUWE_INDICATIE_ZORGKANTOOR*. Deze notificatie is afkomstig van het CIZ en geeft aan dat een client uit de regio van het zorgkantoor een (nieuwe) Wlz Indicatie heeft ontvangen. Met gegevens kan het zorgkantoor de indicatie raadplegen en bemiddeling registreren in het Bemiddelingsregister. Hieruit volgen weer nieuwe notificaties. 

| **Query ID** | **Beschrijving** | **Verplichte input** | **resultaat** | **Autorisatie** |
|---|---|---|---|---|

### Zorgkantoor - uitvoerend
Na ontvangst van de notificatie: *NIEUWE_BEMIDDELINGSPECIFICATIE_ZORGKANTOOR*

| **Query ID** | **Beschrijving** | **Verplichte input** | **resultaat** | **Autorisatie** |
|---|---|---|---|---|

### Zorgkantoor - nieuw verantwoordelijk
Na ontvangst van de notificatie: *OVERDRACHT_ZORGKANTOOR*

| **Query ID** | **Beschrijving** | **Verplichte input** | **resultaat** | **Autorisatie** |
|---|---|---|---|---|