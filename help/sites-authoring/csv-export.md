---
title: Exporteren naar CSV
description: Informatie over uw pagina's exporteren naar een CSV-bestand op uw lokale systeem
contentOwner: Chris Bohnert
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: page-authoring
content-type: reference
docset: aem65
exl-id: 18910143-f2f2-4cfe-88b9-651df90d9cb9
solution: Experience Manager, Experience Manager Sites
feature: Authoring
role: User,Admin,Developer
source-git-commit: c77849740fab51377ce60aff5f611e0408dca728
workflow-type: tm+mt
source-wordcount: '192'
ht-degree: 6%

---

# Exporteren naar CSV{#export-to-csv}

**creeer CSV Rapport** laat u toe om informatie over uw pagina&#39;s naar een Csv- dossier op uw lokaal systeem uit te voeren.

* Het gedownloade bestand wordt `export.csv` genoemd
* De inhoud is afhankelijk van de eigenschappen die u selecteert.
* U kunt het pad samen met de diepte van het exporteren definiëren.

>[!NOTE]
>
>De downloadfunctie en de standaardbestemming van uw browser worden gebruikt.

**creeer CSV de tovenaar van de Uitvoer** laat u selecteren:

* Te exporteren eigenschappen
   * Metagegevens
      * Naam
      * gewijzigd
      * Gepubliceerd
      * Sjabloon
      * Workflow
   * Vertaling
      * Vertaald
   * Analyse
      * Paginaweergaven
      * Unieke bezoekers
      * Tijd op pagina
* Diepte
   * Bovenliggend pad
   * Alleen directe kinderen
   * Aanvullende niveaus voor kinderen
   * Niveaus

Het resulterende `export.csv` -bestand kan worden geopend in Excel of een andere compatibele toepassing.

![&#x200B; etc-01 &#x200B;](assets/etc-01.png)

Creëer **optie van het Rapport CSV** is beschikbaar wanneer het doorbladeren van de **3&rbrace; console van Plaatsen &lbrace;(in de mening van de Lijst): het is een optie van** creeer **drop-down menu:**

![&#x200B; etc-02 &#x200B;](assets/etc-02.png)

Een CSV-export maken:

1. Open de **console van Plaatsen**, navigeer aan de vereiste plaats indien nodig.
1. Selecteer op de werkbalk de optie **Maken** en vervolgens **CSV-rapport** om de wizard te openen:

   ![&#x200B; etc-03 &#x200B;](assets/etc-03.png)

1. Selecteer de eigenschappen die u wilt exporteren.
1. Selecteer **creeer**.
