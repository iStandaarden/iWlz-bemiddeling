# GraphQL-query templates
Een vraag wordt gesteld door een actor als deelnemer van het netwerk. Deze deelnemer stelt de vraag vanuit een bepaalde rol. Afhankelijk van de rol zijn gegevens wel of niet (direct) raadpleegbaar. 

Het moment waarop een actor een rol heeft is afhankelijk van een notificatie. 

_De lijst is nog niet volledig._

Op dit moment zijn de volgende rollen onderkent:
| Deelnemer | rol | toelichting |
| :-- | :-- |:-- |
| Zorgaanbieder | uitvoerend | Een zorgaanbieder die betrokken is bij de uitvoering van zorg |
| Zorgaanbieder | dossierhouder | Een zorgaanbieder die verantwoordelijk is voor de uitvoering van verblijfszorg |
| Zorgaanbieder | coordinator zorg thuis | Een zorgaanbieder die verantwoordelijk is voor de uitvoering van zorg thuis (mpt) | 
| Zorgkantoor | verantwoordelijk | Een zorgkantoor die verantwoordelijk is van de client (i.c.m. de Wlz Indicatie) en zorgt voor de registratie van die gegevens in het bemiddelingsregister | 
| Zorgkantoor | uitvoerend | Een zorgkantoor dat uitvoerend is betrokken bij de uitvoering van zorg i.v.m. zorg uit een andere regio | 
| Zorgkantoor | nieuw verantwoordelijk | Het zorgkantoor dat de client krijgt overgedragen van het huidige verantwoordelijk zorgkantoor |

< documentatie aanvullen >

## Beschikbare templates per rol

### Zorgaanbieder - uitvoerend
Na ontvangst van de notificatie: _NIEUWE_BEMIDDELINGSPECIFICATIE_ZORGAANBIEDER_

| **Query ID** | **Beschrijving** | **Verplichte input** | **resultaat** | **Autorisatie** |
|---|---|---|---|---|
| [QBR-0001-ZA](/gql-query/QBR-0001-ZA.graphql) | Op basis van de (ontvangen) bemiddelingspecificatieID en eigen identificatie, de bijbehorende Bemiddelingspecificatie, Bemiddeling en Cliënt gegevens raadplegen | bemiddelingspecificatieID (V),  AGBcode (V) | Bemiddelingspecificatie Bemiddeling Client | BRA0001 |
| [QBR-0002-ZA](/gql-query/QBR-0002-ZA.graphql) | Op basis van de bemiddelingsspecificatieID, eigen identificatie, ingang- en einddatum, de (overlappende) Bemiddelingspecificatie(s), Bemiddeling, Client, Dossierhouder, CoordinatorZorgThuis, Contactpersoon en Contactgegevens raadplegen | bemiddelingspecificatieID (V),  AGBcode (V), Ingangsdatum bemiddelingsspecificatie (V), Einddatum (O) | Bemiddelingspecificatie Bemiddeling Client Dossierhouder Coordinator zorg thuis Contactgegevens | BRA0002, BRA0004, BRA0005 |

### Zorgaanbieder - dossierhouder
Na ontvangst van de notificatie: _ROL_DOSSIERHOUDER_ZORGAANBIEDER_

| **Query ID** | **Beschrijving** | **Verplichte input** | **resultaat** | **Autorisatie** |
|---|---|---|---|---|

### Zorgaanbieder - coordinator zorg thuis
Na ontvangst van de notificatie: _ROL_COORDINATORZORGTHUIS_ZORGAANBIEDER_

| **Query ID** | **Beschrijving** | **Verplichte input** | **resultaat** | **Autorisatie** |
|---|---|---|---|---|

