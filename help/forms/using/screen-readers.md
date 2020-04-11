---
title: Schermlezers voor HTML5-formulieren
seo-title: Schermlezers voor HTML5-formulieren
description: Hier worden de schermlezers weergegeven die met HTML5-formulieren worden ondersteund.
seo-description: Hier worden de schermlezers weergegeven die met HTML5-formulieren worden ondersteund.
uuid: 035354e2-957f-4eb6-bc16-4ca96ec7ac74
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: hTML5_forms
discoiquuid: 53c57180-7004-4534-9146-603f7770a6fe
translation-type: tm+mt
source-git-commit: 56c6cfd437ef185336e81373bd5f758205b96317

---


# Schermlezers voor HTML5-formulieren {#screen-readers-for-html-forms}

Met HTML5-formuliercomponenten wordt XFA-formuliersjablonen weergegeven in de HTML5-indeling. Deze formulieren kunnen worden weergegeven in alle standaardbrowsers die HTML5 ondersteunen. Ter ondersteuning van vergelijkbare ervaringen met het vastleggen van gegevens in PDF- en HTML5-formulieren, blijft de indeling van PDF-formulieren behouden in HTML5-formulieren.

HTML5-formulieren maken gebruik van standaard HTML-constructies die het gebruik van gewone toegankelijkheidsgereedschappen voor HTML in deze formulieren mogelijk maken. Als een formulier is ontworpen volgens de aanbevolen procedures voor toegankelijke formulieren, werkt het met alle ondersteunde schermlezers. Bovendien worden dergelijke formulieren ingeschakeld voor toetsenbordnavigatie.

## Toegankelijkheidsnormen {#accessibility-standards}

HTML5-formulieren voldoen aan sectie 508 voor toegankelijkheid, met bekende uitzonderingen. Zie [VPAT voor HTML5-formulieren](https://www.adobe.com/mena_en/accessibility/compliance/livecycle-mobile-forms-es4-section-508-vpat.html) voor meer informatie.

## Gecertificeerde schermlezers voor HTML5-formulieren {#certified-screen-readers-for-html-forms}

* JAWS 14.0 op Microsoft Windows
* VoiceOver op Mac OS X en iPad

### JAWS {#jaws}

Alle standaardtoetsaanslagen en -sneltoetsen werken voor HTML5-formulieren. Ga naar [https://www.freedomscientific.com/jaws-hq.asp](https://www.freedomscientific.com/jaws-hq.asp)voor meer informatie over het gebruik van JAWS.

### VoiceOver {#voiceover}

HTML5-formulieren ondersteunen alle standaardtoetsaanslagen en -bewegingen van Voice over. Voor meer informatie bij vestiging en het gebruiken van VoiceOver, zie [https://www.apple.com/accessibility/voiceover/](https://www.apple.com/accessibility/voiceover/).

## Known issues {#known-issues}

* **(Alleen interne Verkenner 9)** In HTML5-formulieren worden de pagina&#39;s op aanvraag geladen (dynamisch). Bij het laden van pagina&#39;s op aanvraag kunnen er problemen optreden met de werking van schermlezers. Wanneer de schermlezer de focus heeft op het laatste veld van de pagina en de gebruiker op de tab drukt in plaats van de focus in te stellen op het eerste veld van de volgende pagina, keert de schermlezer de focus terug naar het eerste veld van de eerste pagina van het formulier.
* **(Alleen in interne Verkenner 9)** Het besturingselement Datumkiezer in HTML5-formulieren is niet volledig toegankelijk met het toetsenbord. Als u in het besturingselement Datumkiezer meerdere keren op de toets Omhoog/Omlaag drukt, wordt het besturingselement Datumkiezer gesloten en gaat de focus naar het volgende/laatste veld.

* VoiceOver kan geen pijltoetsen detecteren op de datumwidget in iPad safari.
