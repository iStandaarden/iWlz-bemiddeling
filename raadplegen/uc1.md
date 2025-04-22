# Use Case: UC-IR0001: Raadplegen van Wlz-indicatie door initieel Zorgkantoor

**Scenario:**  
Een zorgkantoor mag voor het toeleiden van een cliënt de Wlz-indicatie raadplegen waarvoor dat zorgkantoor op de afgiftedatum verantwoordelijk is.

---

### **Use Case Beschrijving**  
**Titel:** Raadplegen van Wlz-indicatie door initieel Zorgkantoor  
**Actoren:** Zorgkantoor  
**Precondities:**
- De Wlz-indicatie is opgenomen in het Indicatieregister.
- Het zorgkantoor was op de afgiftedatum van de Wlz-indicatie verantwoordelijk.

**Autorisatie**
- Autorisatieregel: 
- Autorisatiematrixt: [IRA0001](https://github.com/iStandaarden/iWlz-Autorisatiematrix/blob/main/autorisatiematrix_indicatieregister.md)

**Trigger:**
- Het zorgkantoor wil de Wlz-indicatie raadplegen ter ondersteuning van het toeleidingsproces van een cliënt.

### **Stroomdiagram**
1. **Start**
2. Het zorgkantoor initieert een raadpleging van de Wlz-indicatie in het Indicatieregister.
3. Het systeem controleert of het zorgkantoor als **initieelVerantwoordelijkZorgkantoor** is opgenomen in de Wlz-indicatie:
   - **Ja** → Ga verder naar stap 4.
   - **Nee** → Beëindig proces (geen toegang).
4. Het zorgkantoor krijgt toegang tot alle entiteiten die bij de Wlz-indicatie horen.
5. Het systeem controleert de Contactgegevens en Contactpersonen:
   - Alleen de Contactgegevens en Contactpersonen die niet zijn beëindigd op het opvraagmoment worden getoond.
6. Het zorgkantoor heeft toegang vanaf het moment dat de Wlz-indicatie in het register is geplaatst.
7. Het zorgkantoor behoudt toegang zolang de Wlz-indicatie beschikbaar is in het register.
8. Het systeem controleert de einddatum van de Wlz-indicatie en de laatst vastgestelde vervaldatum:
   - **Indien een vervaldatum is vastgesteld en deze is verstreken** → Geen toegang meer tot Contactpersonen en Contactgegevens.
   - **Indien de Wlz-indicatie een einddatum heeft en deze is verstreken** → Geen toegang meer tot Contactpersonen en Contactgegevens.
9. **Einde**

### **Business Rules**
- Een zorgkantoor mag enkel Wlz-indicaties raadplegen waarvoor het op de afgiftedatum verantwoordelijk was.
- Het zorgkantoor mag alle entiteiten inzien die horen bij de Wlz-indicatie.
- Contactpersonen en Contactgegevens mogen alleen worden ingezien als ze op het moment van opvragen nog geldig zijn.
- Toegang tot de Wlz-indicatie blijft bestaan zolang deze beschikbaar is in het register.
- Toegang tot Contactpersonen en Contactgegevens vervalt na de laatst vastgestelde vervaldatum of einddatum van de Wlz-indicatie.

### **Exceptions**
1. **Zorgkantoor niet bevoegd:**
   - Het systeem blokkeert toegang indien het zorgkantoor niet als **initieelVerantwoordelijkZorgkantoor** is geregistreerd.
2. **Contactgegevens of Contactpersonen beëindigd:**
   - Het systeem toont geen Contactgegevens of Contactpersonen als deze op het opvraagmoment niet meer geldig zijn.
3. **Wlz-indicatie verlopen:**
   - Toegang tot Contactpersonen en Contactgegevens wordt automatisch ingetrokken na de vervaldatum of einddatum.

### **Resultaat**
- Het zorgkantoor heeft op legitieme wijze toegang tot de relevante Wlz-indicatiegegevens en kan de cliënt effectief toeleiden naar de juiste zorg.

---
|     IRA0001(A)     (Scenario):    |     Een zorgkantoor mag voor het   toeleiden van een cliënt de Wlz-indicatie raadplegen waarvoor dat zorgkantoor   op de afgiftedatum verantwoordelijk is.    |
|---|---|
|     Gegeven:    |     Een zorgkantoor wil voor het   toeleiden van de cliënt de Wlz-indicatie raadplegen waarvoor dat zorgkantoor   op de afgiftedatum verantwoordelijk is.    |
|     Als:    |     dat zorgkantoor in het   Indicatieregister de WlzIndicatie raadpleegt    |
|     Dan:    |     moet dat zorgkantoor als   initieelVerantwoordelijkZorgkantoor zijn opgenomen in deze WlzIndicatie     |
|     En:    |     mag dat zorgkantoor alle entiteiten   inzien die bij deze WlzIndicatie horen    |
|     Maar:    |     mag dat zorgkantoor alleen de   Contactgegevens en Contactpersonen inzien die op opvraagmoment niet zijn   beëindigd    |
|     En:       |     heeft dat zorgkantoor toegang vanaf   het moment dat de WlzIndicatie in het register is geplaatst    |
|     En:    |     geldt de toegang zolang die WlzIndicatie   beschikbaar is in het register    |
|     Maar:    |     heeft het zorgkantoor geen toegang   meer tot de Contactpersonen en Contactgegevens na de laatst vastgestelde   vervaldatum of na de einddatum van de WlzIndicatie (als er geen vervaldatum   is).    |



|     IRA0001(B)     (Scenario):    |     Een zorgkantoor mag voor het   toeleiden van een cliënt de Wlz-indicatie raadplegen waarvoor dat zorgkantoor   door dossieroverdracht verantwoordelijk geworden is.    |
|---|---|
|     Gegeven:    |     Een zorgkantoor wil voor het   toeleiden van de cliënt de Wlz-indicatie raadplegen waarvoor dat zorgkantoor door   dossieroverdracht verantwoordelijk geworden is.    |
|     Als:    |     dat zorgkantoor in het   Indicatieregister de WlzIndicatie raadpleegt    |
|     Dan:    |     moet dat zorgkantoor in het   Bemiddelingsregister als verantwoordelijkZorgkantoor in een Overdracht zijn die   hoort bij deze WlzIndicatie     |
|     En:    |     mag dat zorgkantoor alle entiteiten   inzien die bij deze WlzIndicatie horen    |
|     Maar:    |     mag dat zorgkantoor alleen de   Contactgegevens en Contactpersonen inzien die op opvraagmoment niet zijn   beëindigd    |
|     En:       |     heeft dat zorgkantoor toegang vanaf   het moment dat de Overdracht in het register is geplaatst    |
|     En:    |     geldt de toegang zolang die   WlzIndicatie beschikbaar is in het register    |
|     Maar:    |     heeft het zorgkantoor geen toegang   meer tot de Contactpersonen en Contactgegevens na de laatst vastgestelde   vervaldatum of na de einddatum van de WlzIndicatie (als er geen vervaldatum   is).    |

