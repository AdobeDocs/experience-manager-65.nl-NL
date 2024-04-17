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

Momenteel ondersteunen alle implementaties van het Java-platform [TrueType](https://en.wikipedia.org/wiki/Truetype) lettertypen.

1. Open CRXDE Lite en navigeer naar de projecttoepassingsmap:

   `/apps/<your-project>/`

1. Onder `/apps/<your-project>/` een knooppunt maken:

   * **Naam**: `fonts`
   * **Type**: `sling:Folder`

   Sla alle wijzigingen op.

1. Kopieer de lettertypebestanden naar deze map, bijvoorbeeld met WebDAV.

   >[!NOTE]
   >
   >Fontbestanden in de opslagplaats moeten het achtervoegsel hebben `*.ttf` of `*.TTF`.

1. Werk de [OSGi-configuratie](/help/sites-deploying/configuring-osgi.md) van [Day Commons GFX Font Helper](/help/sites-deploying/osgi-configuration-settings.md). Voeg het pad toe aan de map met lettertypen, dat wil zeggen: `/apps/<your-project>/fonts`.

1. Terug naar CRXDE Lite. U moet nu een `.fontlist` in uw map met de naam van de geïmporteerde lettertypen.

   Deze lettertypen kunnen nu worden gebruikt in de Java API.

Zie voor meer informatie over het gebruik van de lettertypen met de Java API de [documentatie voor de klasse Font van de Java API](https://download.oracle.com/javase/6/docs/api/java/awt/Font.html).
