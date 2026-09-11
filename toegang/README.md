# Toegang tot de informatie

De toegang tot de informatie in een register is geregeld door **Autorisatieregels** en de **Autorisatiematrix**.

De **Autorisatieregel** is van toepassing op één register en beschrijft per (organisatie)rol onder welke voorwaarde(n) en voor welke periode toegang tot gegevens geldt. In de regel staat:

- wie de gegevens mag raadplegen (wie);
- over welke gegevens het gaat (wat);
- onder welke voorwaarden of voor welk doel raadplegen is toegestaan (waarvoor of waarom);
- voor welke periode de toegang geldt (wanneer). 

In de **Autorisatiematrix** is per autorisatieregel de toegang op attribuutniveau vastgelegd.

De volledige beschrijving van de autorisatieregels op het Bemiddelingsregister is te vinden in het [Informatiemodel](https://informatiemodel.istandaarden.nl/index.html) onder *iWlz Bemiddelingsregister > Regels > Autorisatieregel*

De autorisatiematrix staat [hier](../raadplegen/autorisatiematrix_bemiddelingsregister.md) bij de Koppelvlakspecificatie van het Bemiddelingsregister onder *Raadplegen > Autorisatiematrix*.

De beschrijvingen hieronder zijn ter verduidelijking in de relatie tussen het *moment van raadplegen*, de *samenhang met andere informatie*, in het register, de rol van de raadpleger en het *effect* daarvan op het *resultaat* van een raadpleging. 

De beschrijving is voor de helderheid telkens beredeneerd vanuit één afzonderlijke autorisatieregel, maar het kan zijn dat er sprake is van een stapeling van regels. In dat geval zal dat worden aangegeven middels een verwijzing. 

# Toegangsbeschrijvingen

In alle gevallen is de *BRONHOUDER* een Zorgkantoor. Dit zorgkantoor is verantwoordelijk voor de client en registreert de gegevens in het Bemiddelingsregister. De *RAADPLEGER* is op dit moment het CIZ, een Zorgaanbieder of een ander (bovenregionaal uitvoerend) Zorgkantoor dan het Zorgkantoor die de bronhouder is.

| **Regel** |
|---|
| [BRA0001: Een zorgaanbieder mag voor het leveren van zorg aan een cliënt de eigen toewijzing raadplegen.](./bra0001.md) |
| [BRA0002: Een zorgaanbieder mag voor het leveren van zorg aan een cliënt de (informatieve) toewijzingen raadplegen die niet van deze zorgaanbieder zijn.](./bra0002.md) |
| BRA0004: Een zorgaanbieder mag voor het leveren van zorg aan een cliënt de contactgegevens en contactpersonen van de cliënt raadplegen. |
| BRA0005: Een zorgaanbieder mag voor het leveren van zorg aan een cliënt de regierol van andere zorgaanbieders raadplegen. |
| BRA0006: Een uitvoerend zorgkantoor mag voor het toeleiden van een cliënt de eigen toewijzing raadplegen. |
| BRA0007: Een uitvoerend zorgkantoor mag voor het toeleiden van een cliënt de (informatieve) toewijzingen van andere zorgkantoren raadplegen. |
| BRA0008: Een uitvoerend zorgkantoor mag voor het toeleiden van een cliënt de contactgegevens en contactpersonen van de cliënt raadplegen. |
| BRA0009: Een uitvoerend zorgkantoor mag voor het toeleiden van een cliënt de Regiehouders raadplegen. |
| BRA0010: Een nieuw verantwoordelijk zorgkantoor mag voor het toeleiden van een cliënt de dossieroverdracht van de cliënt raadplegen. |
| BRA0011: Het CIZ mag het Bemiddelingsregister raadplegen om de verantwoordelijke zorgkantoren te informeren over wijzigingen in de Wlz-indicatie van een cliënt. |
| BRA0012: Een zorgaanbieder mag voor het leveren van zorg aan een cliënt de eigen regierol raadplegen. |
| BRA0013: Een nieuw verantwoordelijk zorgkantoor mag voor het toeleiden van een cliënt de contactgegevens, contactpersonen en regiehouders van de overgedragen cliënt raadplegen. |
| BRA0014: Het CIZ mag het Bemiddelingsregister raadplegen om de uitvoerende zorgkantoren te informeren over een nieuwe, gewijzigde of verwijderde VervallenGeldigheid van de Wlz-indicatie van een cliënt. |