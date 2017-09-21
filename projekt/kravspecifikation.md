# Kravspecifikation Dbstream

## Bakgrund

### Produkt
En realtids dashboard över kommunikationskanaler inom dbwebb.

För slutanvändaren skall produkten bestå av en dashboard som kan vara ett flöde av händelser i dbwebbs kommunikationskanaler. Alternativt kan det vara en dashboard som även delar upp kommunikationskanaler i separata flöden. I alla varianter syftar dbstream till att samla dbwebbs kommunikationskanaler, som spänner över flera olika tjänster och sociala medier, till ett enda flöde.

Dbstream-projektet är dock inte bara en dashboard. För att kunna presentera kommunikationsflöden från flera olika kanaler skall det finnas en backend som står för insamlandet från olika flöden. Detta ska presenteras på ett lättkonsumerat sätt för en frontend.

Projektet skall vara ett opensource-projekt med MIT-licens.

Se även [projektbeskrivning](projektbeskrivning.md).

### Användare
Produkten riktar sig både till slutanvändare av dashboard och till utvecklare som vill utöka produkten eller använda dess tjänster i befintlig sajt.

Kraven från de två tänkta användargrupper är olika, slutanvändaren förväntar sig en enkel och välfungerande dashboard medan en utvecklare förväntar sig dokumentation och utbyggbarhet. Tanken är att tillgodose bägge dessa användargrupper med en viss övervikt på utvecklare.

Se även [projektbeskrivning](projektbeskrivning.md).

### Projektfokus
Projektets fokus är backend och specifikt att implementera en arkitektur att bygga på. Tanken med microarkitekturen är att delarna skall vara små och utbytbara. Underhåll kan med fördel ske genom att helt förkasta en äldre implementationen och ersätta med en ny.

### Öppenhet och säkerhet
I arkitekturen kan tänkas att man bygger in autentisering av microtjänster osv. I detta projekt kommer detta inte att implementeras. Den tänkta arkitekturen är skapad så att detta kan läggas till progressivt i efterhand.

Vad gäller den flödesförenande frontservern måste denna ha autentisering om man implementerar att kunna lägga till och administrera tjänster. För att komma runt detta kommer frontservern i sin första implementation att konfigureras med config-filer och därigenom skyddas med sedvanlig server autentisering.

Streamen från frontservern skall, med tanke att denna kommer att vara öppen och fri att konsumera, bara innehålla flöden från öppna kanaler.

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
5. Projektet skall vara uppbyggt av fristående microtjänster. Detta isolerar tjänsterna vilket kan underlätta i skrivandet av nya tjänster. Det medför också att interna implementationsdetaljer för nya tjänster blir helt upp till utvecklaren av den tjänsten.
6. En samlingsserver finnas framför microtjänsterna för att samla flera flöden till ett flöde.

### Optionella arkitekturkrav
1. En samlingsserver bör logga flödet.
2. Det vore bra om samlingsservern har ett administrationsinterface för att lägga till nya tjänster.
3. Det vore bra om en samlingsserver hade ett REST-api för att kunna leverera information från loggen.

#### Optionella krav
1. Det vore vore bra om flöden från twitter, instagram, facebook, youtube och github issues ingick.
2. Det vore bra om dashboarden hämtade de senaste händelserna från en logg.
3. Det vore bra att ha uppdelade flöden och kunna se historik ur ett enskilt flöde.

### Leverans
Vid leverans skall produkten finnas som githubrepo och skall vara uppsatt och körandes på en server.

### Delleveranser
Tänkta delleveranser.

1. IRC-flödestjänst med egen log.
2. Samlingsserver.
3. Gitter-flödestjänst.
4. Slutleverans inklusive dashboard.

## Teknikval, översikt
* Javascript på frontend och backend.
* Node med express js.
* React+Redux, Vue eller inget ramverk för dashboard.
* Kommunikation via websockets.
* Socket.io som abstraktion över websockets på frontend och backend.
* Sqlite som databas för loggar.

```
Dokumentversioner:
v0.0.5 - Lagt till projektfokus och säkerhet.
v0.0.4 - Högre prioritet på microtjänstarkitektur.
v0.0.3 - Ändrade leveransvillkor. Utförligare inledning.
v0.0.2 - Numrerade krav, optionella krav i egen sektion.
v0.0.1 - Första versionen
```
