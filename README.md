# iWlz-bemiddeling
Koppelvlak specificatie Bemiddelingsregister

> 
> **Status Koppelvlakspecificatie:** *in ontwikkeling* 
>
> d.d. 23 maart 2023
> 
> Het deel met de witte entiteiten (over de bemiddeling) is meerdere malen besproken in verschillende werkgroepen. **Status:** *STABIEL*
> 
> De roze gemarkeerde entiteiten gaan over de contactgegevens en contactpersoongegevens van een client. **Status:** * REVIEW* 


## Versies
Laatste versie: ![GitHub release (latest by date including pre-releases)](https://img.shields.io/github/v/release/iStandaarden/iWlz-bemiddeling?include_prereleases&style=flat-square)
![GitHub tag (latest by date)](https://img.shields.io/github/v/tag/iStandaarden/iWlz-bemiddeling?style=flat-square)

Versie overzicht zie: [Changelog](CHANGELOG.md)

## Documentatie
De specificaties zijn gebaseerd op het volgende ERD - versie 22-03-2023:
![ERD](ERD-bemiddeling-inclSleutels.png "ERD bemiddeling")

Informatiemodel iStandaarden iWlz 2.4: [Informatiemodellen](https://informatiemodellen.istandaarden.nl/)

## Bronnen
* Actieprogramma iWlz: van keten naar netwerk: [lees hier meer over het Actieprogramma iWlz](https://www.istandaarden.nl/actieprogramma-iwlz "Actieprogramma iWlz")
* Portaal voor iStandaarden in de Zorg en Ondersteuning: [homepagina iStandaarden](https://www.istandaarden.nl)

## Contactpersonen:
* Hilko Jacobse - [@hilkojacobse](https://github.com/HilkoJacobse)
* Remo van Rest - [@rvanrest](https://github.com/rvanrest)

## Licentie
Copyright &copy; iStandaarden 2021
Licensed under the [EUPL]

## nieuwe ERD
```plantuml
@startuml 

note as Versioning
    Diagramversion: 1.1
    Date: 2023-04-24
end note

class Client {
    +{static}clientID: LDT_UUID
    __
    +bsn: LDT_BurgerServicenummer {id}
    leefeenheid: LDT_Leefeenheid
    huisarts: LDT_AgbCode[0..1]
    communicatieVorm: LDT_Communicatievorm[0..1]
    taal: LDT_Taal[0..1]
    }

class Bemiddeling {
    +{static}bemiddelingID: LDT_UUID
    __
    +wlzIndicatieID: LDT_UUID {id}
    besluitnummer: LDT_Besluitnummer
    +verantwoordelijkZorgkantoor: LDT_ZorgkantoorCode {id}
    +verantwoordelijkheidIngangsdatum: LDT_Datum {id}
    verantwoordelijkheidEinddatum: LDT_Datum [0..1]
}

class BemiddeldeInstelling {
    +{static}bemiddeldeInstellingID: LDT_UUID
    __
    +instelling: LDT_AgbCode {id}
    +uitvoerendZorgkantoor: LDT_ZorgkantoorCode {id}
}

class ZorgInNatura {
    +{static}zorgInNaturaID: LDT_UUID
    __
    +leveringsvorm: LDT_Leveringsvorm {id}
    +zzpCode: LDT_ZzpCode {id}
    +toewijzingIngangsdatum: LDT_Datum {id}
    vaststellingsmoment: LDT_Moment
    toewijzingEinddatum: LDT_Datum[0..1]
    percentage: LDT_Percentage
    opname: LDT_JaNee[0..1] 
    redenIntrekking: LDT_RedenIntrekking[0..1]
    etmalen: LDT_Etmalen[0..1]
    instellngBestemming: LDT_iWlzAgbCode[0..1]
    soortToewijzing: LDT_SoortToewijzing
}

class PGB {
    +{static}pgbID: LDT_UUID
    __
    +zzpCode: LDT_ZzpCode {id}
    +toewijzingIngangsdatum: LDT_Datum {id}
    vaststellingsmoment: LDT_Moment
    toewijzingEinddatum: LDT_Datum[0..1]
    percentage: LDT_Percentage
}

class CoordinatorZorgThuis {
    +{static}coordinatorZorgThuisID: LDT_UUID
    __
    +instelling: LDT_iWlzAgbCode {id}
    +ingangsdatum: LDT_Datum {id}
    einddatum: LDT_Datum[0..1]
}

class Dossierhouder {
    +{static}dossierhouderID: LDT_UUID
    __
    +instelling: LDT_iWlzAgbCode {id}
    +ingangsdatum: LDT_Datum {id}
    einddatum: LDT_Datum[0..1]
}

class Overdracht {
    +{static}overdrachtID: LDT_UUID
    __
    +verantwoordelijkZorgkantoor: LDT_ZorgkantoorCode {id}
    overdrachtdatum: LDT_Datum
    verhuisdatum: LDT_Datum
}

class Overdrachtspecificatie {
    +{static}overdrachtspecificatieID: LDT_UUID
    __
    +leveringstatus: LDT_leveringstatus
    leveringstatusClassificatie: LDT_LeveringstatusClassificatie[0..1]
    oorspronkelijkeToewijzingEinddatum: LDT_Datum[0..1]
}

Bemiddeling "1..*" -left- "1" Client
Bemiddeling "1" -- "0..*" BemiddeldeInstelling
Bemiddeling "1" -- "0..*" PGB
BemiddeldeInstelling "1" -- "1..*" ZorgInNatura
Overdracht "0..1" -- "1" Bemiddeling
Overdracht "1" -- "0..*" Overdrachtspecificatie
Overdrachtspecificatie "0..1" -- "1" PGB
Overdrachtspecificatie "0..1" -- "1" ZorgInNatura
Client "1" -- "0..*" Dossierhouder
Client "1" -- "0..*" CoordinatorZorgThuis

@enduml
```