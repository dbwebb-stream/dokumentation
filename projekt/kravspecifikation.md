# Kravspecifikation Dbstream
version 0.0.1

## Bakgrund

### Produkt
En realtids dashboard/flöda över kommunikationskanaler inom dbwebb.

Projektet skall vara ett opensource-projekt med MIT-licens.

Se även [projektbeskrivning](projektbeskrivning.md).

### Användare
Produkten riktar sig både till slutanvändare av dashboard och till utvecklare som vill utöka produkten eller använda dess tjänster i befintlig sajt.

Se även [projektbeskrivning](projektbeskrivning.md).

### Organisation
Projektet förlöper inom en kurs på Blekinge Tekniska Högskola. Utvecklingen sker öppet på github och projektet organiseras som ett eller flera github-repon.

## Krav

### Funktionella krav
En slutanvändaren skall kunna gå in på en hemsida för att få upp en dashboard/flöde som uppdateras i realtid.

Utvecklare skall kunna integrera backendtjänsten i en befintlig hemsida. Utvecklare skall även kunna bygga ut backendtjänsten så att den lyssnar på nya kommunikationskanaler.

I produktens första iteration skall realtidsflöde för IRC och gitter-kanaler ingå. Det vore vore bra om flöden från twitter, instagram, facebook och github issues också ingick.

Flödet skall loggas. Speciellt viktigt är IRC-flödet som beroende på implementation kan behöva loggas separat.

### Ickefunktionella krav
Dashboarden skall fungera utan vidare konfigurering för slutanvändaren. Det vore bra om dashboarden hämtade de senaste händelserna från en logg. Det vore bra att ha uppdelade flöden och kunna se historik ur ett enskilt flöde.

För att underlätta för integration i befintliga hemsidor skall API:et vara dokumenterat.

I projektet skall man sträva mot att modularisera flödeslyssnartjänsterna för att underlätta tilläggande av nya tjänster.

Projektet bör vara uppbyggt av fristående microtjänster. Detta isolerar tjänsterna vilket kan underlätta i skrivandet av nya tjänster. Det medför också att interna implentationsdetaljer för nya tjänster blir helt upp till utvecklaren av den tjänsten.

Om projektet byggs som microtjänster bör en samlingsserver finnas framför dess mot frontend för att samla flöden till ett flöde. En samlingsserver skall logga flödet. Det vore bra om en samlingsserver hade ett REST-api för att kunna plocka information från loggen. Samlingsservern bör ha ett administrationsinterface för att lägga till nya tjänster.

Flöden skall loggas till en databas.

### Leverans
Vid leverans skall produkten finnas som githubrepo och skall kunna demonstreras. Produkten bör vara uppsatt och körandes på en server.

### Delleveranser
Tänkta delleveranser vid implementation av microarkitektur.

1. IRC-flödestjänst.
2. Gitter-flödestjänst.
3. Samlingsserver med logger.
4. Slutleverans inklusive dashboard.

## Appendix

### Punktad kravlista

#### Prio 1
* Realtidsdashboard.
* Ingen nödvändig konfiguration för slutanvändaren.
* Modulär flödestjänstimplementation.
* Möjlighet att utnyttja backendtjänst från tredje part.
* Dbwebbs IRC och gitterflöden ingår.
* Flödes logg och irc logg i form av databas.

#### Prio 2
* Microtjänstarkitektur på backend.
* Samlingsserver mellan microtjänster och fronten
* Administrationsinterface på eventuell samlingsserver.

#### Prio 3
* Dashboarden hämtar de senaste händelserna i flödet.
* Uppdelade flöden med interaktion i form av historik.
* REST api på eventuell samlingsserver.
* Lyssnartjänster för twitter, instagram, facebook, github issues etc.

### Teknikval, översikt
* Javascript på frontend och backend.
* Node med express js
* React+Redux, Vue eller inget ramverk.
* Kommunikation via websockets.
* Socket.io som abstraktion över websockets på frontend och backend.
* Sqlite som databas för loggar.

