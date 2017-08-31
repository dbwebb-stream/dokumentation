# Dbwebb-stream

## Kund
Namn: dbwebb
Kontaktperson: Mikael Roos
E-mail: mos@dbwebb.se

## Projektbeskrivning: Problem
På dbwebb:s hemsida version 1 fanns en region på förstasidan som visade den senaste IRC-loggen. Det gav liv åt hemsidan att man fick en inblick i kommunikationen som ständigt sker mellan dbwebbare. Möjligen ger en sådan inblick i communityn även ett sug efter att själv engagera sig och ta kontakt.
 
Dbwebb har många kanaler för kommunikation mellan lärare-elever och mellan elever. Olika tekniker, till exempel forum, IRC och gitter, används. Forumet är integrerat med IRC på så sätt att en bot, marvin, lägger notiser om nya foruminlägg. Gitter ligger däremot utanför och har inte heller någon integrering mellan gitterkanaler. Det finns ingen översikt över samtliga kanaler.
 
Dbwebb-stream projektet är tänkt att ge en sådan översikt. Att i realtid kunna få se flödet av kommunikation som sker inom dbwebb. Dbwebb-stream är tänkt att både kunna användas på en befintlig hemsida samt kunna fungera på en fristående sida för den som vill ha en översikt.


## Projektbeskrivning: Användare
Dbwebbare, lärare och elever, som vill se ett realtidsflöde över dbwebbs tre mest aktiva kommunikationskanaler.

Projektets tyngd ligger på backend. Med en fungerande backend kan man tänka sig att denna skulle kunna användas till ambitiösare frontend.

## Projektbeskrivning: Tekniker
* Projektet görs med javascript på både backend (Node) och frontend (React-redux, vue eller vanilla javascript).
* Backenden görs primärt som en enda server. Alternativt kan varje lyssnarservice vara sin egen microservice som kommunicerar med en uppsamlande server som presenterar ett förenat flöde.
* Server och klient kommunicerar över websockets.
* Backend är helt öppen för klienter från olika sajter att koppla in sig mot.
* Backenden skall logga flödet i en sqlite-databas för att möjligöra framtida tjänster som använder loggen.
