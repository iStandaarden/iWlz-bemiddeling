# Autorisatiematrix Bemiddelingsregister 1
*Bemiddelingsregister 1 - versie 1.2: 24-06-2026*

In de autorisatiematrix is per autorisatieregel de toegang op attribuutniveau vastgelegd.

[Informatiemodel Bemiddelingsregister 1](https://informatiemodel.istandaarden.nl/informatiemodel/iwlz/netwerk/bemiddelingsregister-1/)

Ga direct naar: - [Autorisatie CIZ](#CIZ) - [Autorisatie Zorgaanbieder](#ZA) - [Autorisatie Zorgkantoor](#ZK)

| **ENTITEIT/ATTRIBUUT** 	| **[BRA0001](https://informatiemodel.istandaarden.nl/informatiemodel/iwlz/netwerk/bemiddelingsregister-1/regels/autorisatieregel/bra0001/)** 	| **[BRA0002](https://informatiemodel.istandaarden.nl/informatiemodel/iwlz/netwerk/bemiddelingsregister-1/regels/autorisatieregel/bra0002/)** 	| **[BRA0004](https://informatiemodel.istandaarden.nl/informatiemodel/iwlz/netwerk/bemiddelingsregister-1/regels/autorisatieregel/bra0004/)** 	| **[BRA0005](https://informatiemodel.istandaarden.nl/informatiemodel/iwlz/netwerk/bemiddelingsregister-1/regels/autorisatieregel/bra0005/)** 	| **[BRA0012](https://informatiemodel.istandaarden.nl/informatiemodel/iwlz/netwerk/bemiddelingsregister-1/regels/autorisatieregel/bra0012/)** 	| **ENTITEIT/ATTRIBUUT** 	| **[BRA0006](https://informatiemodel.istandaarden.nl/informatiemodel/iwlz/netwerk/bemiddelingsregister-1/regels/autorisatieregel/bra0006/)** 	| **[BRA0007](https://informatiemodel.istandaarden.nl/informatiemodel/iwlz/netwerk/bemiddelingsregister-1/regels/autorisatieregel/bra0007/)** 	| **[BRA0008](https://informatiemodel.istandaarden.nl/informatiemodel/iwlz/netwerk/bemiddelingsregister-1/regels/autorisatieregel/bra0008/)** 	| **[BRA0009](https://informatiemodel.istandaarden.nl/informatiemodel/iwlz/netwerk/bemiddelingsregister-1/regels/autorisatieregel/bra0009)** 	| **[BRA0010](https://informatiemodel.istandaarden.nl/informatiemodel/iwlz/netwerk/bemiddelingsregister-1/regels/autorisatieregel/bra0010/)** 	| **[BRA0013](https://informatiemodel.istandaarden.nl/informatiemodel/iwlz/netwerk/bemiddelingsregister-1/regels/autorisatieregel/bra0013/)** 	| **ENTITEIT/ATTRIBUUT** 	| **[BRA0011](https://informatiemodel.istandaarden.nl/informatiemodel/iwlz/netwerk/bemiddelingsregister-1/regels/autorisatieregel/bra0011/)**	| **[BRA0014](https://informatiemodel.istandaarden.nl/informatiemodel/iwlz/netwerk/bemiddelingsregister-1/regels/autorisatieregel/bra0014/)** 	|
|---:	|:---:	|:---:	|:---:	|:---:	|:---:	|---:	|:---:	|:---:	|:---:	|:---:	|:---:	|:---:	|---:	|:---:	|:---: 	|
| <h4>Raadpleger</h4> 	| <h4 id="ZA">Zorgaanbieder</h4> 	| <h4>Zorgaanbieder</h4> 	| <h4>Zorgaanbieder</h4> 	| <h4>Zorgaanbieder</h4>	| <h4>Zorgaanbieder</h4> 	| <h4>Raadpleger</h4> 	| <h4 id="ZK">Zorgkantoor</h4>	| <h4>Zorgkantoor</h4> 	| <h4>Zorgkantoor</h4> 	| <h4>Zorgkantoor</h4> 	| <h4>Zorgkantoor</h4> 	| <h4>Zorgkantoor</h4> 	| <h4>Raadpleger</h4> 	| <h4 id="CIZ">CIZ</h4> 	| <h4>CIZ</h4> |
| **Client** 	|  	|  	|  	|  	|  	| **Client** 	|  	|  	|  	|  	|  	|  	| **Client** 	|	|  	|
| clientID 	| R 	|  	|  	|  	|  	| clientID 	| R 	|  	|  	|  	| R 	|  	| clientID 	|	|  	|
| bsn 	| R 	|  	|  	|  	|  	| bsn 	| R 	|  	|  	|  	| R 	|  	| bsn 	|	|  	|
| leefeenheid 	| R 	|  	|  	|  	|  	| leefeenheid 	| R 	|  	|  	|  	| R 	|  	| leefeenheid 	|	|  	|
| huisarts 	| R 	|  	|  	|  	|  	| huisarts 	| R 	|  	|  	|  	| R 	|  	| huisarts 	|	|  	|
| communicatievorm 	| R 	|  	|  	|  	|  	| communicatievorm 	| R 	|  	|  	|  	| R 	|  	| communicatievorm 	|	|  	|
| taal 	| R 	|  	|  	|  	|  	| taal 	| R 	|  	|  	|  	| R 	|  	| taal 	|	|  	|
|  	|  	|  	|  	|  	|  	|  	|  	|  	|  	|  	|  	|  	|  	|	|  	|
| **Bemiddeling** 	|  	|  	|  	|  	|  	| **Bemiddeling** 	|  	|  	|  	|  	|  	|  	| **Bemiddeling** 	|	|  	|
| bemiddelingID 	| R 	| R 	|  	|  	|  	| bemiddelingID 	| R 	| R 	|  	|  	| R 	|  	| bemiddelingID 	|	| R 	|
| wlzIndicatieID 	| R 	| R 	|  	|  	|  	| wlzIndicatieID 	| R 	| R 	|  	|  	| R 	|  	| wlzIndicatieID 	| R	| R 	|
| verantwoordelijkZorgkantoor 	| R 	| R 	|  	|  	|  	| verantwoordelijkZorgkantoor 	| R 	| R 	|  	|  	| R 	|  	| verantwoordelijkZorgkantoor 	| R	|  	|
| verantwoordelijkheidIngangsdatum 	| R 	| R 	|  	|  	|  	| verantwoordelijkheidIngangsdatum 	| R 	| R 	|  	|  	| R 	|  	| verantwoordelijkheidIngangsdatum 	|	|  	|
| verantwoordelijkheidEinddatum 	| R 	| R 	|  	|  	|  	| verantwoordelijkheidEinddatum 	| R 	| R 	|  	|  	| R 	|  	| verantwoordelijkheidEinddatum 	|	|  	|
|  	|  	|  	|  	|  	|  	|  	|  	|  	|  	|  	|  	|  	|  	|	|  	|
| **Bemiddelingspecificatie** 	|  	|  	|  	|  	|  	| **Bemiddelingspecificatie** 	|  	|  	|  	|  	|  	|  	| **Bemiddelingspecificatie** 	|	|  	|
| bemiddelingspcificatieID 	| R 	| R 	|  	|  	|  	| bemiddelingspcificatieID 	| R 	| R 	|  	|  	| R 	|  	| bemiddelingspcificatieID 	|	|  	|
| leveringsvorm 	| R 	| R 	|  	|  	|  	| leveringsvorm 	| R 	| R 	|  	|  	| R 	|  	| leveringsvorm 	|	|  	|
| zzpCode 	| R 	| R 	|  	|  	|  	| zzpCode 	| R 	| R 	|  	|  	| R 	|  	| zzpCode 	|	|  	|
| toewijzingIngangsdatum 	| R 	| R 	|  	|  	|  	| toewijzingIngangsdatum 	| R 	| R 	|  	|  	| R 	|  	| toewijzingIngangsdatum 	|	|  	|
| instelling 	| R 	| R 	|  	|  	|  	| instelling 	| R 	| R 	|  	|  	| R 	|  	| instelling 	|	|  	|
| uitvoerendZorgkantoor 	| R 	| R 	|  	|  	|  	| uitvoerendZorgkantoor 	| R 	| R 	|  	|  	| R 	|  	| uitvoerendZorgkantoor 	|	| R 	|
| vaststellingMoment 	| R 	| R 	|  	|  	|  	| vaststellingMoment 	| R 	| R 	|  	|  	| R 	|  	| vaststellingMoment 	|	|  	|
| toewijzingEinddatum 	| R 	| R 	|  	|  	|  	| toewijzingEinddatum 	| R 	| R 	|  	|  	| R 	|  	| toewijzingEinddatum 	|	|  	|
| percentage 	| R 	| R 	|  	|  	|  	| percentage 	| R 	| R 	|  	|  	| R 	|  	| percentage 	|	|  	|
| pgbPercentage 	|  	|  	|  	|  	|  	| pgbPercentage 	| R 	| R 	|  	|  	|  	|  	| pgbPercentage 	|	|  	|
| opname 	| R 	| R 	|  	|  	|  	| opname 	| R 	| R 	|  	|  	| R 	|  	| opname 	|	|  	|
| redenIntrekking 	| R 	| R 	|  	|  	|  	| redenIntrekking 	| R 	| R 	|  	|  	| R 	|  	| redenIntrekking 	|	|  	|
| etmalen 	| R 	| R 	|  	|  	|  	| etmalen 	| R 	| R 	|  	|  	| R 	|  	| etmalen 	|	|  	|
| instellingBestemming 	| R 	| R 	|  	|  	|  	| instellingBestemming 	| R 	| R 	|  	|  	| R 	|  	| instellingBestemming 	|	|  	|
| soortToewijzing 	| R 	| R 	|  	|  	|  	| soortToewijzing 	| R 	| R 	|  	|  	| R 	|  	| soortToewijzing 	|	|  	|
|  	|  	|  	|  	|  	|  	|  	|  	|  	|  	|  	|  	|  	|  	|	|  	|
| **Overdracht** 	|  	|  	|  	|  	|  	| **Overdracht** 	|  	|  	|  	|  	|  	|  	| **Overdracht** 	|	|  	|
| overdrachtID 	|  	|  	|  	|  	|  	| overdrachtID 	|  	|  	|  	|  	| R 	|  	| overdrachtID 	|	|  	|
| verantwoordelijkZorgkantoor 	|  	|  	|  	|  	|  	| verantwoordelijkZorgkantoor 	|  	|  	|  	|  	| R 	|  	| verantwoordelijkZorgkantoor 	|	|  	|
| vaststellingMoment 	|  	|  	|  	|  	|  	| vaststellingMoment 	|  	|  	|  	|  	| R 	|  	| vaststellingMoment 	|	|  	|
| overdrachtdatum 	|  	|  	|  	|  	|  	| overdrachtdatum 	|  	|  	|  	|  	| R 	|  	| overdrachtdatum 	|	|  	|
| verhuisdatum 	|  	|  	|  	|  	|  	| verhuisdatum 	|  	|  	|  	|  	| R 	|  	| verhuisdatum 	|	|  	|
|  	|  	|  	|  	|  	|  	|  	|  	|  	|  	|  	|  	|  	|  	|	|  	|
| **Overdrachtspecificatie** 	|  	|  	|  	|  	|  	| **Overdrachtspecificatie** 	|  	|  	|  	|  	|  	|  	| **Overdrachtspecificatie** 	|	|  	|
| overdrachtspecificatieID 	|  	|  	|  	|  	|  	| overdrachtspecificatieID 	|  	|  	|  	|  	| R 	|  	| overdrachtspecificatieID 	|	|  	|
| leveringsstatus 	|  	|  	|  	|  	|  	| leveringsstatus 	|  	|  	|  	|  	| R 	|  	| leveringsstatus 	|	|  	|
| leveringsstatusClassificatie 	|  	|  	|  	|  	|  	| leveringsstatusClassificatie 	|  	|  	|  	|  	| R 	|  	| leveringsstatusClassificatie 	|	|  	|
| oorspronkelijkeToewijzingEinddatum 	|  	|  	|  	|  	|  	| oorspronkelijkeToewijzingEinddatum 	|  	|  	|  	|  	| R 	|  	| oorspronkelijkeToewijzingEinddatum 	|	|  	|
|  	|  	|  	|  	|  	|  	|  	|  	|  	|  	|  	|  	|  	|  	|	|  	|
| **Regiehouder** 	|  	|  	|  	|  	|  	| **Regiehouder** 	|  	|  	|  	|  	|  	|  	| **Regiehouder** 	|	|  	|
| regiehouderID 	|  	|  	|  	| R 	| R 	| regiehouderID 	|  	|  	|  	| R 	|  	| R 	| regiehouderID 	|	|  	|
| instelling 	|  	|  	|  	| R 	| R 	| instelling 	|  	|  	|  	| R 	|  	| R 	| instelling 	|	|  	|
| ingangsdatum 	|  	|  	|  	| R 	| R 	| ingangsdatum 	|  	|  	|  	| R 	|  	| R 	| ingangsdatum 	|	|  	|
| einddatum 	|  	|  	|  	| R 	| R 	| einddatum 	|  	|  	|  	| R 	|  	| R 	| einddatum 	|	|  	|
| regierol 	|  	|  	|  	| R 	| R 	| regierol 	|  	|  	|  	| R 	|  	| R 	| regierol 	|	|  	|
|  	|  	|  	|  	|  	|  	|  	|  	|  	|  	|  	|  	|  	|  	|	|  	|
| **Contactgegevens** 	|  	|  	|  	|  	|  	| **Contactgegevens** 	|  	|  	|  	|  	|  	|  	| **Contactgegevens** 	|	|  	|
| contactgegevensID 	|  	|  	| R 	|  	|  	| contactgegevensID 	|  	|  	| R 	|  	|  	| R 	| contactgegevensID 	|	|  	|
| straatnaam 	|  	|  	| R 	|  	|  	| straatnaam 	|  	|  	| R 	|  	|  	| R 	| straatnaam 	|	|  	|
| huisnummer 	|  	|  	| R 	|  	|  	| huisnummer 	|  	|  	| R 	|  	|  	| R 	| huisnummer 	|	|  	|
| huisletter 	|  	|  	| R 	|  	|  	| huisletter 	|  	|  	| R 	|  	|  	| R 	| huisletter 	|	|  	|
| huisnummertoevoeging 	|  	|  	| R 	|  	|  	| huisnummertoevoeging 	|  	|  	| R 	|  	|  	| R 	| huisnummertoevoeging 	|	|  	|
| aanduidingWoonadres 	|  	|  	| R 	|  	|  	| aanduidingWoonadres 	|  	|  	| R 	|  	|  	| R 	| aanduidingWoonadres 	|	|  	|
| postcode 	|  	|  	| R 	|  	|  	| postcode 	|  	|  	| R 	|  	|  	| R 	| postcode 	|	|  	|
| plaatsnaam 	|  	|  	| R 	|  	|  	| plaatsnaam 	|  	|  	| R 	|  	|  	| R 	| plaatsnaam 	|	|  	|
| land 	|  	|  	| R 	|  	|  	| land 	|  	|  	| R 	|  	|  	| R 	| land 	|	|  	|
| adressoort 	|  	|  	| R 	|  	|  	| adressoort 	|  	|  	| R 	|  	|  	| R 	| adressoort 	|	|  	|
| telefoonnummer01 	|  	|  	| R 	|  	|  	| telefoonnummer01 	|  	|  	| R 	|  	|  	| R 	| telefoonnummer01 	|	|  	|
| landnummer01 	|  	|  	| R 	|  	|  	| landnummer01 	|  	|  	| R 	|  	|  	| R 	| landnummer01 	|	|  	|
| telefoonnummer02 	|  	|  	| R 	|  	|  	| telefoonnummer02 	|  	|  	| R 	|  	|  	| R 	| telefoonnummer02 	|	|  	|
| landnummer02 	|  	|  	| R 	|  	|  	| landnummer02 	|  	|  	| R 	|  	|  	| R 	| landnummer02 	|	|  	|
| emailadres 	|  	|  	| R 	|  	|  	| emailadres 	|  	|  	| R 	|  	|  	| R 	| emailadres 	|	|  	|
| ingangsdatum 	|  	|  	| R 	|  	|  	| ingangsdatum 	|  	|  	| R 	|  	|  	| R 	| ingangsdatum 	|	|  	|
| einddatum 	|  	|  	| R 	|  	|  	| einddatum 	|  	|  	| R 	|  	|  	| R 	| einddatum 	|	|  	|
|  	|  	|  	|  	|  	|  	|  	|  	|  	|  	|  	|  	|  	|  	|	|  	|
| **Contactpersoon** 	|  	|  	|  	|  	|  	| **Contactpersoon** 	|  	|  	|  	|  	|  	|  	| **Contactpersoon** 	|	|  	|
| contactpersoonID 	|  	|  	| R 	|  	|  	| contactpersoonID 	|  	|  	| R 	|  	|  	| R 	| contactpersoonID 	|	|  	|
| relatienummer 	|  	|  	| R 	|  	|  	| relatienummer 	|  	|  	| R 	|  	|  	| R 	| relatienummer 	|	|  	|
| volgorde 	|  	|  	| R 	|  	|  	| volgorde 	|  	|  	| R 	|  	|  	| R 	| volgorde 	|	|  	|
| soortRelatie 	|  	|  	| R 	|  	|  	| soortRelatie 	|  	|  	| R 	|  	|  	| R 	| soortRelatie 	|	|  	|
| rol 	|  	|  	| R 	|  	|  	| rol 	|  	|  	| R 	|  	|  	| R 	| rol 	|	|  	|
| relatie 	|  	|  	| R 	|  	|  	| relatie 	|  	|  	| R 	|  	|  	| R 	| relatie 	|	|  	|
| geslachtsnaam 	|  	|  	| R 	|  	|  	| geslachtsnaam 	|  	|  	| R 	|  	|  	| R 	| geslachtsnaam 	|	|  	|
| voorvoegselGeslachtsnaam 	|  	|  	| R 	|  	|  	| voorvoegselGeslachtsnaam 	|  	|  	| R 	|  	|  	| R 	| voorvoegselGeslachtsnaam 	|	|  	|
| partnernaam 	|  	|  	| R 	|  	|  	| partnernaam 	|  	|  	| R 	|  	|  	| R 	| partnernaam 	|	|  	|
| voorvoegselPartnernaam 	|  	|  	| R 	|  	|  	| voorvoegselPartnernaam 	|  	|  	| R 	|  	|  	| R 	| voorvoegselPartnernaam 	|	|  	|
| voornamen 	|  	|  	| R 	|  	|  	| voornamen 	|  	|  	| R 	|  	|  	| R 	| voornamen 	|	|  	|
| voorletters 	|  	|  	| R 	|  	|  	| voorletters 	|  	|  	| R 	|  	|  	| R 	| voorletters 	|	|  	|
| roepnaam 	|  	|  	| R 	|  	|  	| roepnaam 	|  	|  	| R 	|  	|  	| R 	| roepnaam 	|	|  	|
| naamgebruik 	|  	|  	| R 	|  	|  	| naamgebruik 	|  	|  	| R 	|  	|  	| R 	| naamgebruik 	|	|  	|
| geslacht 	|  	|  	| R 	|  	|  	| geslacht 	|  	|  	| R 	|  	|  	| R 	| geslacht 	|	|  	|
| geboortedatum 	|  	|  	| R 	|  	|  	| geboortedatum 	|  	|  	| R 	|  	|  	| R 	| geboortedatum 	|	|  	|
| geboortedatumgebruik 	|  	|  	| R 	|  	|  	| geboortedatumgebruik 	|  	|  	| R 	|  	|  	| R 	| geboortedatumgebruik 	|	|  	|
| ingangsdatum 	|  	|  	| R 	|  	|  	| ingangsdatum 	|  	|  	| R 	|  	|  	| R 	| ingangsdatum 	|	|  	|
| einddatum 	|  	|  	| R 	|  	|  	| einddatum 	|  	|  	| R 	|  	|  	| R 	| einddatum 	|	|  	|
