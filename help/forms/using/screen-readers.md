---
title: Schermlezers voor HTML5-formulieren
description: Hier worden de schermlezers weergegeven die met HTML5-formulieren worden ondersteund.
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: hTML5_forms
discoiquuid: 53c57180-7004-4534-9146-603f7770a6fe
feature: HTML5 Forms
exl-id: 07d20c2f-7d13-48ac-8d58-b367eb194558
solution: Experience Manager, Experience Manager Forms
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '305'
ht-degree: 0%

---

# Schermlezers voor HTML5-formulieren {#screen-readers-for-html-forms}

Met HTML5-formuliercomponenten wordt een XFA-formuliersjabloon weergegeven in de HTML5-indeling. Deze formulieren kunnen worden weergegeven in alle standaardbrowsers die HTML5 ondersteunen. Ter ondersteuning van vergelijkbare ervaringen met het vastleggen van gegevens in PDF- en HTML5-formulieren, blijft de indeling van PDF forms behouden in HTML5-formulieren.

HTML5-formulieren maken gebruik van standaardconstructies voor HTML, zodat HTML in deze formulieren met gewone toegankelijkheidsopties kan worden gebruikt. Als een formulier is ontworpen volgens de aanbevolen procedures voor toegankelijke formulieren, werkt het met alle ondersteunde schermlezers. Dergelijke formulieren zijn ook ingeschakeld voor toetsenbordnavigatie.

## Toegankelijkheidsnormen {#accessibility-standards}

HTML5-formulieren voldoen aan sectie 508 voor toegankelijkheid, met bekende uitzonderingen. Zie [VPAT voor HTML5-formulieren](https://www.adobe.com/content/dam/cc1/en/accessibility/compliance/pdfs/adobe-livecycle-es4-section-508-vpat-portfolio.pdf) voor meer informatie.

## Gecertificeerde schermlezers voor HTML5-formulieren {#certified-screen-readers-for-html-forms}

* JAWS 14.0 op Microsoft® Windows
* VoiceOver op macOS X en iPad

### JAWS {#jaws}

Alle standaardtoetsaanslagen en -sneltoetsen werken voor HTML5-formulieren. Ga voor meer informatie over het gebruik van JAWS naar [https://www.freedomscientific.com/jaws-hq.asp](https://www.freedomscientific.com/jaws-hq.asp).

### VoiceOver {#voiceover}

HTML5-formulieren ondersteunen alle standaardtoetsaanslagen en -bewegingen van Voice over. Voor meer informatie bij vestiging en het gebruiken van VoiceOver, zie [https://www.apple.com/accessibility/vision/](https://www.apple.com/accessibility/vision/).

## Bekende problemen {#known-issues}

* **(Alleen interne Verkenner 9)** In HTML5-formulieren worden de pagina&#39;s op aanvraag geladen (dynamisch). Bij het laden van pagina&#39;s op aanvraag kunnen er problemen optreden met de werking van schermlezers. Wanneer de schermlezer de focus heeft op het laatste veld van de pagina en de gebruiker op het tabblad drukt, keert de schermlezer de focus terug naar het eerste veld van de eerste pagina op het formulier.
* **(Alleen interne Verkenner 9)** Het besturingselement Datumkiezer in HTML5-formulieren is niet volledig toegankelijk met het toetsenbord. Als u in het besturingselement Datumkiezer meerdere keren op de toets Omhoog/Omlaag drukt, wordt het besturingselement Datumkiezer gesloten en gaat de focus naar het volgende/laatste veld.

* VoiceOver kan geen pijltoetsen detecteren op de datumwidget in iPad safari.
