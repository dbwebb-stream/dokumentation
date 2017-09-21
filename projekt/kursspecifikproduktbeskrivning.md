# Kravspecifikation Dbstream

## Kund
Namn: dbwebb
Kontaktperson: Mikael Roos
E-mail: mos@dbwebb.se

## Leverantör/elev:
Namn: Anders Nygren
Akronym: anng15
 Webbprogrammering 120p, distans

## Bakgrund

På dbwebb:s hemsida version 1 fanns en region på förstasidan som visade den senaste IRC-loggen. Det gav liv åt hemsidan att man fick en inblick i kommunikationen som ständigt sker mellan dbwebbare. Möjligen ger en sådan inblick i communityn även ett sug efter att själv engagera sig och ta kontakt.

Dbwebb har många kanaler för kommunikation mellan lärare-elever och mellan elever. Olika tekniker, till exempel forum, IRC och gitter, används. Forumet är integrerat med IRC på så sätt att en bot, marvin, lägger notiser om nya foruminlägg. Gitter ligger däremot utanför och har inte heller någon integrering mellan gitterkanaler. Det finns ingen översikt över samtliga kanaler.

Dbwebb-stream projektet är tänkt att ge en sådan översikt. Att i realtid kunna få se flödet av kommunikation som sker inom dbwebb. Dbwebb-stream är tänkt att både kunna användas på en befintlig hemsida samt kunna fungera på en fristående sida för den som vill ha en översikt.

### Produkt
En realtids dashboard över kommunikationskanaler inom dbwebb.

För slutanvändaren skall produkten bestå av en dashboard som kan vara ett flöde av händelser i dbwebbs kommunikationskanaler. Alternativt kan det vara en dashboard som även delar upp kommunikationskanaler i separata flöden. I alla varianter syftar dbstream till att samla dbwebbs kommunikationskanaler, som spänner över flera olika tjänster och sociala medier, till ett enda flöde.

Dbstream-projektet är dock inte bara en dashboard. För att kunna presentera kommunikationsflöden från flera olika kanaler skall det finnas en backend som står för insamlandet från olika flöden. Detta ska presenteras på ett lättkonsumerat sätt för en frontend.

Projektet skall vara ett opensource-projekt med MIT-licens.

### Användare
Produkten riktar sig både till slutanvändare av dashboard och till utvecklare som vill utöka produkten eller använda dess tjänster i befintlig sajt.

Kraven från de två tänkta användargrupper är olika, slutanvändaren förväntar sig en enkel och fungerande dashboard medan en utvecklare förväntar sig dokumentation och utbyggbarhet. Tanken är att tillgodose bägge dessa användargrupper med en viss övervikt på utvecklare.

### Projektfokus
Projektets fokus är backend och specifikt att implementera en arkitektur att bygga på. Tanken med microarkitekturen är att delarna skall vara små och utbytbara. Underhåll kan med fördel ske genom att helt förkasta en äldre implementationen och ersätta med en ny.

### Organisation
Projektet förlöper inom en kurs på Blekinge Tekniska Högskola. Utvecklingen sker öppet på github och projektet organiseras som ett eller flera github-repon.

## Krav

### Funktionella krav
1. En slutanvändaren skall kunna gå in på en hemsida för att få upp en dashboard/flöde som uppdateras i realtid.
2. Realtidsflöden från IRC och gitter-kanaler skall ingå.
3. IRC-flödet skall loggas.
4. Utvecklare skall kunna integrera backendtjänsten i en befintlig hemsida.
5. Utvecklare skall kunna bygga ut backendtjänsten så att den lyssnar på nya kommunikationskanaler.

### Ickefunktionella krav
1. Dashboarden skall fungera utan vidare konfigurering för slutanvändaren.
2. För att underlätta för integration i befintliga hemsidor skall API:et vara dokumenterat.
3. I projektet skall man sträva mot att modularisera flödeslyssnartjänsterna för att underlätta tilläggande av nya tjänster.
4. IRC-flöde skall loggas till en databas.
5. Projektet skall vara uppbyggt av fristående microtjänster. Detta isolerar tjänsterna vilket kan underlätta i skrivandet av nya tjänster. Det medför också att interna implementationsdetaljer för nya tjänster blir helt upp till utvecklaren av den tjänsten.
6. En samlingsserver finnas framför microtjänsterna för att samla flera flöden till ett flöde.

### Optionella arkitekturkrav
1. En samlingsserver bör logga det samlade flödet.
2. Det vore bra om samlingsservern har ett administrationsinterface för att lägga till nya tjänster.
3. Det vore bra om en samlingsserver hade ett REST-api för att kunna leverera information från loggen.

#### Optionella krav
1. Det vore vore bra om flöden från twitter, instagram, facebook, youtube och github issues ingick.
2. Det vore bra om dashboarden hämtade de senaste händelserna från en logg.
3. Det vore bra att ha uppdelade flöden och kunna se historik ur ett enskilt flöde.

### Öppenhet och säkerhet
I arkitekturen kan tänkas att man bygger in autentisering av microtjänster osv. I detta projekt kommer detta inte att implementeras. Den tänkta arkitekturen är skapad så att detta kan läggas till progressivt i efterhand.

Vad gäller den flödesförenande frontservern måste denna ha autentisering om man implementerar att kunna lägga till och administrera tjänster. För att komma runt detta kommer frontservern i sin första implementation att konfigureras med config-filer och därigenom skyddas med sedvanlig server autentisering.

Streamen från frontservern skall, med tanke att denna kommer att vara öppen och fri att konsumera, bara innehålla flöden från öppna kanaler.

### Leverans
Vid leverans skall produkten finnas som ett eller flera githubrepo och skall vara uppsatt och körandes på en server.

Kunden skall innan leverans tillhandahålla en server med node.js > 8.0.0 för att möjliggöra driftsättning. Om kunden inte tillhandahållit en server för drift i god tid innan projektets leverans kommer ett demo att sättas upp på annan server. Demouppsättningen kommer i så fall att tas ner efter att kund och skola har presenterats för projektet.

## Produkt backlog
| Feature | Beskrivning                               | Prio | Kostnad |
|---------|-------------------------------------------|------|---------|
| F1      | IRC-lyssnare                              | 1    | 20h     |
| F2      | Front-server                              | 1    | 30h     |
| F3      | Dashboard                                 | 1    | 30h     |
| F4      | Gitter-lyssnare                           | 1    | 30h     |
| F5      | IRC databaslogg                           | 1    | 10h     |
| F6      | Komplett flödeslogg                       | 2    | 8h      |
| F7      | REST-api för att komma åt loggar          | 3    | 10h     |
| F8      | Dashboard hämtar historik vid sidladdning | 3    | 5h      |
| F9      | Fler flödestjänster, Twitter              | 3    | 5h      |
| F10     | Onlinekonfigurering frontserver           | 4    | 30h     |
| F11     | Avancerad dashboard                       | 4    | 20h     |

Det är tydligt att den estimerade kostnaden för samtliga features överstiger budgeten på ca 150h varför fokus på grund och prio 1 är viktigt.

## Delleveranser
1. IRC-flödestjänst med egen log.
2. Samlingsserver.
3. Gitter-flödestjänst.
4. Slutleverans inklusive dashboard.

## Teknikval, översikt
* Javascript på frontend och backend.
* Node med express js.
* React+Redux, Vue eller inget ramverk för dashboard.
* Kommunikation via websockets mellan microtjänster.
* Socket.io som abstraktion över websockets på frontend och backend.
* Sqlite som databas för loggar.

## Kunderbjudande
Jag kommer att leverera ett system för att samla flöden från olika sociala medier till ett flöde som presenteras på en enkel dashboard. Systemet är byggt med en arkitektur som skall vara utbyggbar. I sin första, och föreliggande, version kommer systemet att inkludera flöden för IRC och Gitter.

Leverans kommer att ske senast den 20/10 -17. Leveransen sker som githubrepo samt med systemet i drift. Om du som kund till mig har levererat en möjlig driftsmiljö med node.js > 8.0.0 installerat kommer systemet att tas i drift där. Annars kommer ett demo att sättas upp. I leveransen ingår inte att konfigurera eventuella befintliga webbservrar för att dirigera trafik genom dessa.

Delleveranser kommer att ske löpande med 1-2v mellanrum från och med 21/9 -17.

För detaljerad kravlista se https://github.com/litemerafrukt/dbstream_dokumentation/blob/master/projekt/kravspecifikation.md


```
Dokumentversioner:
v1.0.0 - Första versionen.
```

