# GraphQL-query templates Bemiddelingsregister
Hier staan de query templates die een raadpleger kan gebruiken voor het raadplegen van gegevens in het Bemiddelingsregister. De templates dienen als voorbeeld hoe de query opgebouwd moet worden. De structuur en bepaalde verplichte parameters zijn nodig om te voldoen aan de autorisatie-policies. Doet een raadpleger dat niet dan kan de vraag niet afgehandeld worden. Bijvoorbeeld doordat de raadpleger benodigde input vergeet mee te geven, gegevens wil raadplegen die niet horen bij de raadpleger of omdat er meer gegevens worden geraadpleegd dan is toegestaan op dat moment. 

Een vraag wordt gesteld door een actor als deelnemer van het netwerk. Deze deelnemer stelt de vraag vanuit een bepaalde autorisatie. Afhankelijk van de autorisatie zijn gegevens wel of niet (direct) raadpleegbaar. 

## Beschikbare templates per rol
Op dit moment zijn de volgende rollen onderkent:
| Deelnemer | rol | toelichting |
| :-- | :-- |:-- |
| [Zorgaanbieder](/gql-query/zorgaanbieder/README.md) | [uitvoerend](/gql-query/zorgaanbieder/README.md#zorgaanbieder---uitvoerend) | Een zorgaanbieder die betrokken is bij de uitvoering van zorg |
| [Zorgaanbieder](/gql-query/zorgaanbieder/README.md) | [regiehouder](/gql-query/zorgaanbieder/README.md#zorgaanbieder---regiehouder) | Een zorgaanbieder die verantwoordelijk is voor de uitvoering van de zorg |
| [Zorgkantoor](/gql-query/zorgkantoor/README.md) | [verantwoordelijk](/gql-query/zorgkantoor/README.md#zorgkantoor---verantwoordelijk) | Een zorgkantoor die verantwoordelijk is van de client (i.c.m. de Wlz Indicatie) en zorgt voor de registratie van die gegevens in het bemiddelingsregister | 
| [Zorgkantoor](/gql-query/zorgkantoor/README.md) | [uitvoerend](/gql-query/zorgkantoor/README.md#zorgkantoor---uitvoerend) | Een zorgkantoor dat uitvoerend is betrokken bij de uitvoering van zorg i.v.m. zorg uit een andere regio | 
| [Zorgkantoor](/gql-query/zorgkantoor/README.md) | [nieuw verantwoordelijk](/gql-query/zorgkantoor/README.md#zorgkantoor---nieuw-verantwoordelijk) | Het zorgkantoor dat de client krijgt overgedragen van het huidige verantwoordelijk zorgkantoor |
| [CIZ](/gql-query/ciz/README.md) | [informerend](/gql-query/ciz/README.md#ciz---notificatie) | Het CIZ informeert betrokken zorgkantoren over wijzigingen van een Wlz Indicatie |


