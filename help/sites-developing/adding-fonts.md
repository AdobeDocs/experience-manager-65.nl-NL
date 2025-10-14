---
title: Lettertypen toevoegen voor grafisch renderen
description: Met AEM kunt u afbeeldingen genereren waarin tekst dynamisch wordt overgenomen van uw inhoud
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: platform
content-type: reference
exl-id: 725c81d0-0258-4118-8b01-29fd7bcaf9b3
solution: Experience Manager, Experience Manager Sites
feature: Developing
role: Developer
source-git-commit: 66db4b0b5106617c534b6e1bf428a3057f2c2708
workflow-type: tm+mt
source-wordcount: '171'
ht-degree: 0%

---

# Lettertypen toevoegen voor grafisch renderen{#adding-fonts-for-graphic-rendering}

Met AEM kunt u afbeeldingen genereren waarin tekst dynamisch wordt overgenomen van uw inhoud.

Hiervoor kunt u ook uw eigen lettertypen laden en gebruiken.

Momenteel steunen alle implementaties van het Platform van Java [&#128279;](https://en.wikipedia.org/wiki/Truetype) doopvonten TrueType.

1. Open CRXDE Lite en navigeer naar de projecttoepassingsmap:

   `/apps/<your-project>/`

1. Onder `/apps/<your-project>/` maakt u een knooppunt:

   * **Naam**: `fonts`
   * **Type**: `sling:Folder`

   Sla alle wijzigingen op.

1. Kopieer de lettertypebestanden naar deze map, bijvoorbeeld met WebDAV.

   >[!NOTE]
   >
   >Fontbestanden in de gegevensopslagruimte moeten het achtervoegsel `*.ttf` of `*.TTF` hebben.

1. Werk de [&#x200B; configuratie OSGi &#x200B;](/help/sites-deploying/configuring-osgi.md) van [&#x200B; het Fonthelper van de Commons GFX van de Dag &#x200B;](/help/sites-deploying/osgi-configuration-settings.md) bij. Voeg het pad naar de map met lettertypen toe, dat wil zeggen `/apps/<your-project>/fonts` .

1. Terug naar CRXDE Lite. Er wordt nu een knooppunt `.fontlist` in uw map weergegeven met de naam van de geïmporteerde lettertypen.

   Deze lettertypen kunnen nu worden gebruikt in de Java API.

Voor volledige details van hoe te om de doopvonten met Java API te gebruiken, zie de [&#x200B; documentatie voor de klasse van de Doopvont van Java API &#x200B;](https://download.oracle.com/javase/6/docs/api/java/awt/Font.html).
