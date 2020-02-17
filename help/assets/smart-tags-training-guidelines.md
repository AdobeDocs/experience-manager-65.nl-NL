---
title: Richtlijnen voor training in Smart Content Service
description: Leer de AI-service van Adobe Sensei om slimme tags toe te passen op elementen
products: SG_EXPERIENCEMANAGER/6.5/ASSETS
contentOwner: AG
translation-type: tm+mt
source-git-commit: a39ee0f435dc43d2c2830b2947e91ffdcf11c7f6

---


# Richtlijnen voor training in Smart Content Service {#smart-content-service-training-guidelines}

De Smart Content Service vereist dat de trainingsafbeeldingen aan bepaalde richtlijnen voldoen om uw merkafbeeldingen effectief te kunnen labelen.

## Richtsnoeren voor opleiding {#guidelines-for-training}

Voor de beste resultaten moeten de afbeeldingen in de trainingsset voldoen aan de volgende richtlijnen:

**** Hoeveelheid en grootte: Minimaal 30 afbeeldingen per tag. Minimaal 500 pixels aan de langere zijde.

**Coherentie**: Afbeeldingen voor een tag moeten visueel op elkaar lijken.

Het is bijvoorbeeld geen goed idee om al deze afbeeldingen als `my-party` (voor training) te labelen, omdat ze er anders uitzien.

![Illustratieve afbeeldingen ter illustratie van de richtlijnen voor training](/help/assets/assets/do-not-localize/coherence.png)

**Dekking**: De beelden in de training moeten voldoende uiteenlopend zijn. Het is de bedoeling om enkele maar redelijk uiteenlopende voorbeelden te geven, zodat AEM leert zich te richten op de juiste zaken. Als u dezelfde tag toepast op visueel verschillende afbeeldingen, moet u ten minste vijf voorbeelden van elke soort opnemen.

Neem voor het vervolgkeuzemodel ** van het label bijvoorbeeld meer trainingsafbeeldingen op, vergelijkbaar met de gemarkeerde afbeelding hieronder, zodat de service vergelijkbare afbeeldingen nauwkeuriger kan identificeren tijdens het labelen.

![Illustratieve afbeeldingen ter illustratie van de richtlijnen voor training](/help/assets/assets/do-not-localize/coverage_1.png)

**Vervorming/obstructie**: De dienst rijdt beter op beelden die minder afleiding hebben (vooraanstaande achtergronden, niet-verwante begeleiding, zoals voorwerpen/personen met het hoofdonderwerp).

Voor de tag *casual-shoe* is de tweede afbeelding bijvoorbeeld geen goede trainingskandidaat.

![Illustratieve afbeeldingen ter illustratie van de richtlijnen voor training](/help/assets/assets/do-not-localize/distraction.png)

**** Volledigheid: Als een afbeelding in aanmerking komt voor meer dan één tag, voegt u alle relevante tags toe voordat u de afbeelding opneemt voor training. Voor bijvoorbeeld tags, zoals `raincoat` en `model-side-view`, voegt u beide tags toe aan het desbetreffende element voordat u dit opneemt voor training.

![Illustratieve afbeeldingen ter illustratie van de richtlijnen voor training](/help/assets/assets/do-not-localize/completeness.png)

## Beperkingen {#limitations}

Verbeterde slimme tags zijn gebaseerd op leermodellen van afbeeldingen en hun tags. Deze modellen zijn niet altijd perfect bij het identificeren van tags. De huidige versie van de Smart Content Service heeft de volgende beperkingen:

* Kan subtiele verschillen in afbeeldingen niet herkennen. Bijvoorbeeld dunne en standaard gemonteerde hemden.
* Kan geen tags identificeren op basis van kleine patronen/delen van een afbeelding. Bijvoorbeeld logo&#39;s op T-shirts.
* Tags worden ondersteund in de landinstellingen waarin AEM wordt ondersteund. Zie Opmerkingen bij de release [Smart Content Services voor een lijst met talen](https://docs.adobe.com/content/help/en/experience-manager-64/release-notes/smart-content-service-release-notes.html).

Als u wilt zoeken naar elementen met slimme tags (normaal of uitgebreid), gebruikt u de opdracht Middelen zoeken (zoeken in volledige tekst). Er is geen afzonderlijke zoekvoorspelling voor slimme tags.

>[!NOTE]
>
>Of de Smart Content Service uw tags kan trainen en deze op andere afbeeldingen kan toepassen, hangt af van de kwaliteit van de afbeeldingen die u voor de training gebruikt. Voor de beste resultaten raadt Adobe aan visueel vergelijkbare afbeeldingen te gebruiken om de service voor elke tag op te leiden.
