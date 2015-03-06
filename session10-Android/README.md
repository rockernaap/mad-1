# Session 10: Android 

## Voorbereiding 1: Video’s kijken

Bekijk hoofdstukken 4 en 5 van de Lynda.com serie Android-SDK Essential Training.

Kijk, voor de komende les de volgende hoofdstukken:

* 4. Defining Activities
    Zeven video’s, samen een dikke drie kwartier.
* 5. Debugging Android AppsVier video’s, 23 minuten.

Beantwoord, na ieder hoofdfstuk, onderstaande kijkvragen:
[https://docs.google.com/forms/d/1cSvs8D1Vx1SSuVgwi9G_1PsS_fPgmiY_oNOdgwPPCXQ/viewform?usp=send_form]
(https://docs.google.com/forms/d/1cSvs8D1Vx1SSuVgwi9G_1PsS_fPgmiY_oNOdgwPPCXQ/viewform?usp=send_form)
(let op: dit formulier heeft meerdere pagina’s. Klik op de doorgaan-knop)

## Voorbereiding 2: Android Research

Gebruik de officiële Android documentatie op http://developer.android.com/develop om 
wat onderzoek te doen naar de View-klasse, scalable points, context en radiobuttons. 
Geef bij ieder vraag 1 of 2 links naar de officiele Android-docs waarin je het antwoord 
gevonden hebt.

[https://docs.google.com/forms/d/1ZDBp14iM9X36oPkkjThDVVIEKFykEen9v7X50udVDgw/viewform?usp=send_form]
(https://docs.google.com/forms/d/1ZDBp14iM9X36oPkkjThDVVIEKFykEen9v7X50udVDgw/viewform?usp=send_form)

## Voorbereiding 3: Android Appie

We gaan een appie maken dat het beginscherm van de eindopdracht kan zijn. 
De eindopdracht is een schuifpuzzel-app. De gebruiker kiest een 
moeilijkheidsgraad (makkelijk = 3×3, normaal = 4×4, moeilijk = 5×5) en een afbeelding vor de puzzel.
De schuifpuzzel zelf maken we later, nu alleen het startscherm. Laat dat er ongeveer zo uitzien:


![Image of n-puzzle start](https://github.com/HANICA/mad-1/blob/master/assets/n-puzzle-start-menu-168x300.png)

Instructies:

* Beslis zelf of je LinearLayout(s) of RelativeLayout(s) of een combinatie gebruikt voor dit scherm.
* Zorg ervoor dat de Radio-buttons correct werken (ze deselecteren elkaar).
* Gebruik voor de foto’s een ImageView, en zet er een gewone knop naast.
* Gebruik padding om wat witruimte te maken om de layout prettig en overzichtelijk te maken.
* Gebruik resources voor alle strings en bitmaps.
* Kies zelf geschikte plaatjes.

## Bonusopdracht: dynamisch resources uitlezen

Hieronder een stukje code dat je kunt toevoegen aan de onCreate methode van je Activity:

```java
Field[] afbeeldingResources = R.drawable.class.getFields();
for (Field f : afbeeldingResources) {
   try {
      String name = f.getName();
      int resourceId = f.getInt(null);
      Log.d("MAD","### afbeelding resource naam:" + name + ", id:"+resourceId);
   } catch (Exception e) {
      Log.e("MAD","### OOPS", e);
   }
}
```

Om deze code te laten werken heb je deze import nodig voor het type Field:

```	
import java.lang.reflect.Field;
```

De code leest (run-time) uit welke plaatjes er beschikbaar zijn als resources.

Opdracht: Gebruik deze code als startpunt om het menu van afbeeldingen dynamischer te maken.

* De afbeeldinkjes met bijbehorende knop worden nu niet meer in de layout-xml-file opgenomen, maar vanuit java-code toegevoegd.
* Als de programmeur een extra plaatje toevoegt aan de res/drawable map (of een zusje daarvan), dan komt dat plaatje automatisch in het menu terecht. Zonder dat daarvoor Java- of XML-code hoeft te worden aangepast.
* Het maakt de Javacode niet uit hoeveel afbeeldingen er beschikbaar zijn; de code verwerkt ze allemaal…
*  … op het icoontje van de applicatie na.
