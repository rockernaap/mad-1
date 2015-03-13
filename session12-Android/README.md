# Session 12: Android (inhalen van Session 8 en session 10)

Deze les bespreken we session 8 en session 10. Hieronder staat de voorbereiding van deze sessions

# Session 8: Android
## Voorbereiding 1: Video’s kijken

Bekijk de eerste verzameling video’s van de Lynda.com serie Android-SDK Essential Training. Let op: Deze cursus is in december 2013 helemaal vernieuwd. Zorg ervoor dat je niet naar de verouderde versie zit te kijken!

Kijk, voor de komende les de volgende hoofdstukken:
* Introduction
* 1. About Android
* 2. Getting Started
* 3. Development Fundamentals

Beantwoord, na ieder hoofdfstuk, de volgende kijkvragen:
[https://docs.google.com/forms/d/1PiOteh5bVHqofTlA9FnZ0RD518yrhLVArMyD6JCH4Yg/viewform?usp=send_form]
(https://docs.google.com/forms/d/1PiOteh5bVHqofTlA9FnZ0RD518yrhLVArMyD6JCH4Yg/viewform?usp=send_form)
Let op: dit formulier heeft meerdere pagina’s. Klik op de doorgaan-knop

# Voorbereiding 2: ADT installeren

Download en installeer de meest recente versie van de Android Developer Toolkit.
En maak een gewone (ARM gebaseerde) virtual device, en test ‘m door ‘m op te starten.

# Voorbereiding 3: Betere virtuele telefoon

In de video’s wordt Intel’s HAXM uitgelegd. Een vergelijkbaar product, maar toch weer wat sneller en confortabeler in Genymotion.

  * Check de system requirements voor HAXM en Genymotion (ze zijn vergelijkbaar).
  * Controleer of je systeem voldoet aan die requirements.
  * Let specifiek op de eisen die aan je microprocessor worden gesteld
  * Kijk of je Genymotion of HAXM aan het werk kunt krijgen voor je.

# Voorbereiding 4: Heb je een echte Android?

Als je een Android-apparaat hebt, kijk of je die aan het werk kunt krijgen.
Drivers kun je het beste installeren door de software van de fabrikant van je apparaat te installeren. Kies dan voor de meest complete versie van de software. Vaak levert een fabrikant ook een klein driverpakketje, maar de ervaring is dat daar de ADB-drivers vaak niet in zitten. Dus Samsung-eigenaren moet toch maar die vervelende “Kies” software met lle toeters en bellen installeren. Voor HTC en Motorola geldt hetzelfde.
Let op: Check heel specifiek dat je de software installeert die hoort bij jouw telefoon-type. Sommige fabrikanten hebben verschillende downloads voor verschillende telefoons, en de goede driver zit alleen in het goede pakket.
Opdracht 5: Maak Hello World

Maak de “Hello World”-applicatie uit de video’s na.
Test ‘m op:

* Je trage ARM AVD
* Je snelle HAXM of Genymotion virtuele telefoon
* Je echte Android-apparaat

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
Field[] afbeeldingResources = R.mipmap.class.getFields(); //of R.drawable.class.getFields(); 
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


## Lesprogramma
* Kijkvragen bespreken
* Android problemen oplossen
* iOS Assignment 2 assessments
