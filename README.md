# Regex
Diverse regexpar...

## 📅 Datum
Matchar datum i den svenska kalendern i formatet `YYYY-MM-DD`, från år 0000-01-01 till år 9999-12-31.

Möstret matchar borttagandet av dagarna 18-28 februari år 1753 samt tar höjd för skottdagar:
* både i den Julianska och den Greorianska kalendern
* det första försöket till kalenderbyte (stöket med skottdagar) år 1700-1708
* tillökningsdagen (för att komma till rätta med stöket) år 1712

```regex
^(?!1753[.\/\- ]?02[.\/\- ]?(1[89]|2[0-8]))(([2468][048]00|[3579][26]00|\d\d0[48]|\d\d[13579][26]|\d\d[2468][048]|[01][0-6]00)[.\/\- ]?(02)[.\/\- ]?(29))|((1712)[.\/\- ]?(02)[.\/\- ]?(30))|((\d{4})[.\/\- ]?(0[135789]|1[02])[.\/\- ]?(0[1-9]|1\d|2\d|3[01]))|((\d{4})[.\/\- ]?(0[469]|11)[.\/\- ]?(0[1-9]|1\d|2\d|30))|((\d{4})[.\/\- ]?(02)[.\/\- ]?(0[1-9]|1\d|2[0-8]))$
```

Förenklad variant som endast tar höjd för skottår:
```regex
^((([02468][048]|[13579][26])00|\d\d(0[48]|[2468][048]|[13579][26]))\-02\-29)|(\d{4}\-((0[135789]|1[02])\-(0[1-9]|[12]\d|3[01])|(0[469]|11)\-(0[1-9]|[12]\d|30)|(02\-(0[1-9]|1\d|2[0-8]))))$
```

## Personnummer & samordningsnummer
Validering av 12-siffriga person- och samordningsnummer i formatet `YYYYMMDDXXXX`.
* Matchar datum för skottdagar
* Matchar dagar/datum med +60 dagar för samordningsnummer
* Validerar INTE kontrollsiffra
```regex
^(((([02468][048]|[13579][26])00|\d\d(0[48]|[2468][048]|[13579][26]))02[28]9)|(\d{4}((0[135789]|1[02])([06][1-9]|[1278]\d|[39][01])|(0[469]|11)([06][1-9]|[1278]\d|[39]0)|(02([06][1-9]|[17]\d|[28][0-8])))))\d{4}$
```

## E-postadress
Matchar e-postadresser. Rätt.
```regex
^([^<>()\[\]\\.,;:\s@"]+(\.[^<>()\[\]\\.,;:\s@"]+)*)@([^<>()\[\]\\.,;:\s@"]+(\.[^<>()\[\]\\.,;:\s@"]+)*)\.([a-zA-Z0-9]{2,})$
```

## 📱 Mobiltelefonnummer
Matchar oformaterade svenska mobiltelefonnummer i möstrena `+467*xxxxxxx`, `00467*xxxxxxx` och `07*xxxxxxx`.

```regex
^((\+|00)46|0)7[02369][0-9]{7}$
```

## Svenska registreringsnummer
Matchar oformaterade registreringsnummer för svenska fordon, i mönstret `ABC123` och `ABC12A`.
- [Nu har de nya registreringsnumrena lanserats](https://www.transportstyrelsen.se/sv/vagtrafik/Fordon/Intressenter/nu-har-de-nya-registreringsnumrena-lanserats) (Transportstyrelsen)
- [Spärrade bokstavskombinationer](https://www.transportstyrelsen.se/sv/vagtrafik/fordon/aga-kopa-eller-salja-fordon/registreringsskyltar/byte-av-registreringsnummer/Sparrade-bokstavskombinationer) (Transportstyrelsen)

```regex
^(?!APA|ARG|ASS|BAJ|BSS|CUC|CUK|CUM|DUM|ETA|ETT|FAG|FAN|FEG|FEL|FEM|FES|FET|FNL|FUC|FUK|FUL|GAM|GAY|GEJ|GEY|GHB|GUD|GYN|HAT|HBT|HKH|HOR|HOT|KGB|KKK|KUC|KUF|KUG|KUK|KYK|LAM|LAT|LEM|LOJ|LSD|LUS|MAD|MAO|MEN|MES|MLB|MUS|NAZ|NRP|NSF|NYP|OND|OOO|ORM|PAJ|PKK|PLO|PMS|PUB|RAP|RAS|ROM|RPS|RUS|SEG|SEX|SJU|SOS|SPY|SUG|SUP|SUR|TBC|TOA|TOK|TRE|TYP|UFO|USA|WAM|WAR|WWW|XTC|XTZ|XXL|XXX|ZEX|ZOG|ZPY|ZUG|ZUP|ZOO)[ABCDEFGHJKLMNOPRSTUWXYZ]{3}(\d{3}|\d\d[ABCDEFGHJKLMNPRSTUWXYZ])$
```

## MAC-adresser
`01:23:45:67:89:ab`
```regex
^([0-9aA-fF][0-9aA-fF]:){5}[0-9aA-fF][0-9aA-fF]$
```
