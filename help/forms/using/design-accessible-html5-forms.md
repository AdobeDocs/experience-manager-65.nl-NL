---
title: Toegankelijke HTML5-formulieren ontwerpen
description: HTML5-formulieren maken gebruik van de toegankelijkheidsstandaard van ARIA HTML5. Deze formulieren ondersteunen navigatie met tabbladen en zijn gecertificeerd voor compatibiliteit met algemene schermlezers.
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: hTML5_forms
docset: aem65
feature: HTML5 Forms,Mobile Forms
exl-id: fca2f9b2-11a2-4db0-a370-c4046f32be63
solution: Experience Manager, Experience Manager Forms
role: Admin, User, Developer
source-git-commit: d7b9e947503df58435b3fee85a92d51fae8c1d2d
workflow-type: tm+mt
source-wordcount: '343'
ht-degree: 0%

---

# Toegankelijke HTML5-formulieren ontwerpen {#designing-accessible-html-forms}

HTML5-formulieren maken gebruik van de toegankelijkheidsstandaard van ARIA HTML5 om toegankelijke HTML-formulieren te genereren. Deze formulieren ondersteunen navigatie met tabbladen (behalve Mozilla FireFox) en zijn gecertificeerd voor compatibiliteit met algemene schermlezers. Als u een HTML5-formulier met goede toegankelijkheidsfuncties wilt genereren, ontwerpt u de XFA-formuliersjabloon op basis van enkele basisrichtlijnen voor het ontwerpen. De ontwerprichtlijnen omvatten het vormen van de correcte lusjeorde en het verstrekken van de inhoud van de Tekst van de Spreek voor elke vormcontrole. AEM Forms Designer ondersteunt het instellen van deze formulierbesturingskenmerken voor het genereren van een Toegankelijke PDF en HTML5-vorm.

*Nota:De navigatie van labels omvat geen beschermde gebieden zoals berekeningsgebieden die som waarden tonen. Als u wilt dat de schermlezer de waarde van een beveiligd veld kan lezen, plaatst u een leeg veld Alleen-lezen boven of naast het beveiligde veld. Wijs de waarde van het beveiligde veld toe aan het nieuwe veld Alleen-lezen. De het schermlezer of van labels voorzien navigatie kan dit read-only gebied selecteren en het uitspreken als waarde van het beschermde gebied.*

AEM Forms Designer bevat verschillende opties voor spraaktekst die aan schermlezers kunnen worden doorgegeven. Voor elk object in een formulier kan de gebruiker een van de volgende instellingen opgeven voor de schermlezertekst:

* Aangepaste schermlezertekst, die kan worden ingesteld met het palet Toegankelijkheid. Auteurs kunnen notities aanbrengen bij de namen van knoppen en velden en bij het doel ervan.
* Knopinfo, die u kunt instellen in het palet Toegankelijkheid.
* Bijschriften voor velden op het formulier.
* Namen van objecten, zoals opgegeven in de optie Naam op het tabblad Binding.

![ toegankelijkheid ](assets/accessibility.png)

Als er meerdere opties beschikbaar zijn voor een formulierbesturingselement, zoals knopinfo, Reader Tekst en Bijschrift, gebruikt de Reader Scherm slechts een van deze eigenschappen. De standaardvolgorde is Tekst, knopinfo, Bijschrift en Naam van aangepaste Reader voor scherm. U kunt de standaardorde met voeten treden gebruikend de Reader van het Scherm **&#x200B;**&#x200B;optie van de Voorrang in het palet van de Toegankelijkheid.
