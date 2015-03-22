# Session 13: Android — Activity Navigation & Lists

## Tip:
Voor iedereen die verantwoord kleurgebruik leuk vindt en geen tijd:
een Material Design palette generator [www.materialpalette.com/](http://www.materialpalette.com/)

## Voorbereiding 1: Video’s kijken

Bekijk, van de Lynda.com serie Android-SDK Essential Training, de volgende hoofdstukken:

  * 6. Managing Navigation. Zes video’s, samen een dik half uur.
  * 11. Working with Data. Zes video’s, samen een kleine drie kwartier.

Hoofdstukken 7,8 en 9 stellen we uit naar de volgende week. Op deze manier kunnen we eerder samen nadenken over de opzet van de Android eindopdracht.

Beantwoord, na ieder hoofdfstuk, onderstaande kijkvragen:
[http://goo.gl/forms/of4SbUA2it](http://goo.gl/forms/of4SbUA2it)

## Voorbereiding 2: ListActivities zijn niet nodig

In de video laat David Gassner zijn Activity-klasse erven van ListActivity (i.p.v. gewoon Activity). Dat is niet nodig, en levert eigenlijk niet zoveel voordelen op.
Maak een applicatie die wel met een ListView werkt, maar die ListView in een gewone Activity heeft zitten, in plaats van in een ListActivity.

* Gebruik een ArrayList van Strings (met zelfbedachte inhoud) als bron van data voor de lijst. David Gassner gebruikt nog een Flower-klasse en een FlowerData-klasse, maar dat soort klassen heb je nu helemaal niet nodig.
* Gebruik, net als Gassner, een Layout-file die de opmaak voor ieder item bepaalt. Maak daarin een layout die net iets interessanter is dan alleen een enkel textveld.
* Je moet dus wel een eigen subklasse van ArrayAdapter maken. Laat je daarvoor inspireren door het voorbeeld van video 11.6.
* Als er op een item wordt geklikt, vertoon dan een “Toast”-berichtje met daarin zowel de positie als de tekst van het aangeklikte item. Je hoeft dus geen nieuwe Activity te starten.
* De manier waarop je nu een event-handler methode koppelt aan een klik op een lijst-item wordt wat ingewikkelder dan in de video’s. Gebruik de Android-documentatie voor ListView om uit te zoeken hoe je daar een onItemClickListener aan kunt koppelen, die de code voor de eventhandler bevat.

## Voorbereiding 3: GridView is (eigenlijk) een ListView die op een tabel lijkt.

Bouw je code van opdracht 2 om zodat-ie een GridView gebruikt, en de data in meerdere kolommen toont.

* Zorg ervoor dat je data nu bestaat uit vrij korte stukjes text.
* Sloop de code om een Layout-file per item te “inflaten” en aan te passen eruit.
* In plaats daarvan moet je Adapter-klasse nu een nieuwe TextView in Java-code creëren, en die vullen met de text die getoond moet worden. Die TextView is nu de returnwaarde voor de getView methode in je Adapter-klasse.
* Toon de data in drie of vier kolommen.
* Voor de bonus: Toon, in plaats van text, afbeeldingen. Je ArrayList kan nu een lijst van ResourceId’s zijn (ints, dus), en in plaats van een TextView, lever je een ImageView op.

## Bonusopdracht: Data veranderen

Deze opdracht kun je doen met de code voor opdracht 2 als uitgangspunt, maar opdracht 3 kan ook.

Maak je applicatie zo dat er onderin het scherm een knopje staat. Als de gebruiker op dat knopje klikt, dan wordt er een item toegevoegd aan de datastructuur voor de list (je ArrayList dus).

* Check de documentatie van de methode notifyDataSetChanged () van de klasse ArrayAdapter om te ontdekken hoe je ervoor zorgt dat een toevoeging aan de ArrayList ook getoond gaat worden door de ListView.
* Als de gebruiker op een item in de lijst (of het grid) klikt, dan wordt dat item verwijderd. Implementeer ook dit door de verwijdering in de ArrayList door te voeren, en daarna de ListView zichzelf te laten updaten.
