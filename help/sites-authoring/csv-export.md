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
role: User,Admin,Architect,Developer
source-git-commit: 9a3008553b8091b66c72e0b6c317573b235eee24
workflow-type: tm+mt
source-wordcount: '192'
ht-degree: 6%

---

# Exporteren naar CSV{#export-to-csv}

**CSV-rapport maken** kunt u informatie over uw pagina&#39;s naar een CSV-bestand op uw lokale systeem exporteren.

* Het gedownloade bestand wordt `export.csv`
* De inhoud is afhankelijk van de eigenschappen die u selecteert.
* U kunt het pad samen met de diepte van het exporteren definiëren.

>[!NOTE]
>
>De downloadfunctie en de standaardbestemming van uw browser worden gebruikt.

De **CSV-export maken** de tovenaar laat u selecteren:

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

Het resultaat `export.csv` kan worden geopend in Excel of een andere compatibele toepassing.

![etc-01](assets/etc-01.png)

Het maken **CSV-rapport** Deze optie is beschikbaar wanneer u in het dialoogvenster **Sites** console (in lijstweergave): dit is een optie van de **Maken** vervolgkeuzelijst:

![etc-02](assets/etc-02.png)

Een CSV-export maken:

1. Open de **Sites** navigeer indien nodig naar de gewenste locatie.
1. Selecteer op de werkbalk de optie **Maken** en vervolgens **CSV-rapport** om de wizard te openen:

   ![etc-03](assets/etc-03.png)

1. Selecteer de eigenschappen die u wilt exporteren.
1. Selecteren **Maken**.
