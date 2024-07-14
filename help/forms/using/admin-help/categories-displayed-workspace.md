---
title: De categorieën beheren die in Workspace worden weergegeven
description: In Workspace worden de processen die een gebruiker kan starten, weergegeven in categorieën in het linkernavigatievenster. Leer hoe je deze rubrieken kunt beheren die in Workspace worden weergegeven.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_workspace
products: SG_EXPERIENCEMANAGER/6.5/FORMS
exl-id: 62621fe9-f69f-4bc0-aecc-d7bcc3064516
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
role: User, Developer
source-git-commit: e821be5233fd5f6688507096790d219d25903892
workflow-type: tm+mt
source-wordcount: '482'
ht-degree: 0%

---

# De categorieën beheren die in Workspace worden weergegeven {#managing-the-categories-displayed-in-workspace}

In Workspace worden de processen die een gebruiker kan starten, weergegeven in categorieën in het linkernavigatievenster. U kunt de categorieën instellen in de beheerconsole of procesontwerpers kunnen deze instellen in Workbench. Wanneer procesontwerpers processen creëren, wijzen zij hen aan categorieën toe.

Als u categorienamen opgeeft, maakt u deze zo dat ze op de juiste wijze worden weergegeven in het navigatievenster van Workspace. Standaard heeft het linkernavigatievenster een vaste breedte van 210 pixels (ongeveer 24 tekens). Als de opgegeven categorienaam te lang is om binnen de vaste breedte van het linkernavigatievenster te passen, wordt deze afgekapt. De volledige naam wordt alleen weergegeven wanneer de muisaanwijzer erop wordt gepauzeerd. Vermijd categorienamen die worden afgekapt. De volgende voorbeelden illustreren categorienamen die passen en categorienamen die worden afgekapt:

**Naam van de Categorie die past:** Aanwezigheid &amp; Verlof

**naam van de Categorie die wordt beknot:** Aanwezigheid &amp; Verlof (Verenigde Staten)

In Workspace worden processen in een categorie doorgaans als kaarten weergegeven op de pagina Proces starten. Over het algemeen kunnen zes kaarten op het scherm voor een categorie worden weergegeven voordat de gebruiker moet schuiven om de resterende kaarten te bekijken. Omdat het scrollen het moeilijker maakt om een proces te vinden, denk na beperkt elke categorie tot zes processen of, afhankelijk van uw resolutie, het aantal processen dat op het scherm kan worden getoond zonder het vereisen van om het even welk scrollen.

Als u MySQL als uw AEM formulierdatabase gebruikt, kan de beheerconsole geen onderscheid maken tussen twee categorienamen die alleen verschillen in het gebruik van uitgebreide tekens. Als u bijvoorbeeld een categorie maakt met de naam abcde en een categorie met de naam âbcdè, worden deze als hetzelfde beschouwd.

## Een categorie toevoegen {#add-a-category}

1. Klik in de beheerconsole op Services > Toepassingen en services > Categoriebeheer.
1. Klik toevoegen. Als u een subcategorie wilt toevoegen, selecteert u een categorie en klikt u op Toevoegen.
1. Typ in het vak Naam een naam voor de categorie en typ in het vak Beschrijving een beschrijving van de categorie.
1. Klik toevoegen. De categorie wordt getoond op de pagina van het Beheer van de Categorie.

   ***nota **: U kunt slechts tot vijf niveaus van hiërarchie toevoegen wanneer het creëren van categorieën.*

## Een categorie bewerken {#edit-a-category}

1. Klik in de beheerconsole op Services > Toepassingen en services > Categoriebeheer.
1. Selecteer de categorie die u wilt bewerken en klik op Bewerken. U kunt ook dubbelklikken op een categorie die u wilt bewerken.
1. Bewerk de naam van de categorie in het vak Naam.

## Een categorie verwijderen {#remove-a-category}

U kunt alleen de categorieën verwijderen die niet in gebruik zijn.

1. Klik in de beheerconsole op Services > Toepassingen en services > Categoriebeheer.
1. Selecteer op de pagina Categoriebeheer het selectievakje voor de categorie die u wilt verwijderen en klik op Verwijderen. De categorie wordt niet meer weergegeven.
