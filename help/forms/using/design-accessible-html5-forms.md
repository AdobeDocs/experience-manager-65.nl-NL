---
title: Toegankelijke HTML5-formulieren ontwerpen
seo-title: Toegankelijke HTML5-formulieren ontwerpen
description: HTML5-formulieren gebruiken de toegankelijkheidsstandaard van ARIA HTML5. Deze formulieren ondersteunen navigatie met tabbladen en zijn gecertificeerd voor compatibiliteit met algemene schermlezers.
seo-description: HTML5-formulieren gebruiken de toegankelijkheidsstandaard van ARIA HTML5. Deze formulieren ondersteunen navigatie met tabbladen en zijn gecertificeerd voor compatibiliteit met algemene schermlezers.
uuid: 1ce5ba39-69ea-4d0e-96ea-e2a38b21d6b7
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: hTML5_forms
discoiquuid: 8711ad33-396b-4572-b2ee-71e9f45f4ebe
docset: aem65
translation-type: tm+mt
source-git-commit: 56c6cfd437ef185336e81373bd5f758205b96317

---


# Toegankelijke HTML5-formulieren ontwerpen {#designing-accessible-html-forms}

HTML5-formulieren gebruiken de toegankelijkheidsstandaard van ARIA HTML5 om toegankelijke HTML-formulieren te genereren. Deze formulieren ondersteunen navigatie met tabbladen (behalve Mozilla FireFox) en zijn gecertificeerd voor compatibiliteit met algemene schermlezers. Als u een HTML5-formulier met goede toegankelijkheidsfuncties wilt genereren, ontwerpt u de XFA-formuliersjabloon op basis van een aantal eenvoudige ontwerprichtlijnen. De ontwerprichtlijnen omvatten het vormen van de correcte lusjeorde en het verstrekken van de inhoud van de Tekst van de Spreek voor elke vormcontrole. AEM Forms Designer ondersteunt het instellen van deze formulierbesturingskenmerken om een toegankelijk PDF- en HTML5-formulier te genereren.

*Opmerking:navigatie met tabbladen geldt niet voor beveiligde velden, zoals berekeningsvelden waarin de som van waarden wordt weergegeven. Als u wilt dat de schermlezer de waarde van een beveiligd veld kan lezen, plaatst u een leeg veld Alleen-lezen boven of naast het beveiligde veld. Wijs de waarde van het beveiligde veld toe aan het nieuwe veld Alleen-lezen. De schermlezer of navigatie met tabs kan dit alleen-lezen veld selecteren en dit uitlezen als de waarde van het beveiligde veld.*

AEM Forms Designer bevat een aantal opties voor spraaktekst die aan schermlezers kunnen worden doorgegeven. Voor elk object in een formulier kan de gebruiker een van de volgende instellingen opgeven voor de schermlezertekst:

* Aangepaste schermlezertekst, die kan worden ingesteld met het palet Toegankelijkheid. Auteurs kunnen notities aanbrengen bij de namen van knoppen en velden en bij het doel ervan.
* Knopinfo, die u kunt instellen in het palet Toegankelijkheid.
* Bijschriften voor velden op het formulier.
* Namen van objecten, zoals opgegeven in de optie Naam op het tabblad Binding.

![toegankelijkheid](assets/accessibility.png)

Als er meerdere opties beschikbaar zijn op een formulierbesturingselement, zoals knopinfo, schermlezertekst en bijschrift, gebruikt de schermlezer slechts een van deze eigenschappen. De standaardvolgorde is Aangepaste schermlezertekst, knopinfo, Bijschrift en Naam. You can override the default order using the Screen Reader **Precedence** option in the Accessibility palette.
