# Kodstil
Jag har försökt skriva i en pragmatisk funktionell stil med support av ramda (motsvarar underscore/lodash), ramda-fantasy eller folktale (användbara funktorer och monader som Maybe, Either/Result och Task), samt most.js (monadic streams).

## Rena funktioner
* Använd implied return.
* Använd bara expressions.
* Ternery expression, inte if statements.
* Gärna point free.
* Föredra compose snarare än pipe vid funktionskomposition.

## Effektfulla funktioner
* En funktion med sidoeffekter bör alltid omringas med måsvingar och använda if istället för ternary-operator. Detta för att indikera att funktionen innehåller statements snarare än expressions.
* Föredra pipe snarare än compose för funktionskomposition.

I pipes med ramdas pipe samt i streams kan man med fördel använda funktionen `tap` för att visa att det görs en sidoeffekt.
