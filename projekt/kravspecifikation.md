# Kravspecifikation Dbstream

## Bakgrund

### Produkt
En realtids dashboard/flöda över kommunikationskanaler inom dbwebb.

För slutanvändaren skall produkten bestå av en dashboard som kan vara ett flöde av händelser i dbwebbs kommunikationskanaler. Alternativt kan det vara en dashboard som delar upp kommunikationskanaler i separata flöden. I alla varianter syftar dbstream till att samla dbwebbs kommunikationskanaler, som spänner över flera olika tjänster och sociala medier, till ett enda flöde.

Dbstream-projektet är dock inte bara en dashboard. För att kunna presentera kommunikationsflöden från flera olika kanaler skall det finnas en backend som står för insamlandet av olika flöden och presenterar detta på ett lättkonsumerat sätt för en frontend.

Projektet skall vara ett opensource-projekt med MIT-licens.

Se även [projektbeskrivning](projektbeskrivning.md).

### Användare
Produkten riktar sig både till slutanvändare av dashboard och till utvecklare som vill utöka produkten eller använda dess tjänster i befintlig sajt.

Kraven från de två tänkta användargrupper är olika, slutanvändaren förväntar sig en enkel och välfungerande dashboard medan en utvecklare förväntar sig dokumentation och utbyggbarhet. Tanken är att tillgodose bägge dessa användargrupper med en viss övervikt på utvecklare.

Se även [projektbeskrivning](projektbeskrivning.md).

### Organisation
Projektet förlöper inom en kurs på Blekinge Tekniska Högskola. Utvecklingen sker öppet på github och projektet organiseras som ett eller flera github-repon.

## Krav

### Funktionella krav
1. En slutanvändaren skall kunna gå in på en hemsida för att få upp en dashboard/flöde som uppdateras i realtid.
2. Realtidsflöden IRC och gitter-kanaler skall ingå.
3. Flödet skall loggas. Speciellt viktigt är IRC-flödet som beroende på implementation kan behöva loggas separat.
4. Utvecklare skall kunna integrera backendtjänsten i en befintlig hemsida.
5. Utvecklare skall kunna bygga ut backendtjänsten så att den lyssnar på nya kommunikationskanaler.

### Ickefunktionella krav
1. Dashboarden skall fungera utan vidare konfigurering för slutanvändaren.
2. För att underlätta för integration i befintliga hemsidor skall API:et vara dokumenterat.
3. I projektet skall man sträva mot att modularisera flödeslyssnartjänsterna för att underlätta tilläggande av nya tjänster.
4. Flöden skall loggas till en databas.

### Optionella arkitekturkrav
1. Projektet bör vara uppbyggt av fristående microtjänster. Detta isolerar tjänsterna vilket kan underlätta i skrivandet av nya tjänster. Det medför också att interna implementationsdetaljer för nya tjänster blir helt upp till utvecklaren av den tjänsten.
2. Om projektet byggs som microtjänster bör en samlingsserver finnas framför dess mot frontend för att samla flera flöden till ett flöde.
3. En samlingsserver skall i så fall logga flödet.
4. Samlingsservern bör ha ett administrationsinterface för att lägga till nya tjänster.
5. Det vore bra om en samlingsserver hade ett REST-api för att kunna leverera information från loggen.

#### Optionella krav
1. Det vore vore bra om flöden från twitter, instagram, facebook och github issues ingick.
2. Det vore bra om dashboarden hämtade de senaste händelserna från en logg.
3. Det vore bra att ha uppdelade flöden och kunna se historik ur ett enskilt flöde.

### Leverans
Vid leverans skall produkten finnas som githubrepo och skall vara uppsatt och körandes på en server.

### Delleveranser
Tänkta delleveranser vid implementation av microarkitektur.

1. IRC-flödestjänst.
2. Gitter-flödestjänst.
3. Samlingsserver med logger.
4. Slutleverans inklusive dashboard.

## Teknikval, översikt
* Javascript på frontend och backend.
* Node med express js
* React+Redux, Vue eller inget ramverk.
* Kommunikation via websockets.
* Socket.io som abstraktion över websockets på frontend och backend.
* Sqlite som databas för loggar.

```
Dokumentversioner:
v0.0.3 - Ändrade leveransvillkor. Utförligare inledning.
v0.0.2 - Numrerade krav, optionella krav i egen sektion.
v0.0.1 - Första versionen
```
