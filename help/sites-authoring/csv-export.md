---
title: Exporteren naar CSV
seo-title: Export to CSV
description: Informatie over uw pagina's exporteren naar een CSV-bestand op uw lokale systeem
seo-description: Export information about your pages to a CSV file on your local system
uuid: 6eee607b-3510-4f6a-ba82-b27480a4fbe1
contentOwner: Chris Bohnert
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: page-authoring
content-type: reference
discoiquuid: 7be506fb-f5c4-48dd-bec2-a3ea3ea19397
docset: aem65
exl-id: 18910143-f2f2-4cfe-88b9-651df90d9cb9
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '191'
ht-degree: 22%

---

# Exporteren naar CSV{#export-to-csv}

**CSV-rapport maken** kunt u informatie over uw pagina&#39;s naar een CSV-bestand op uw lokale systeem exporteren.

* Het gedownloade bestand wordt aangeroepen `export.csv`
* De inhoud is afhankelijk van de eigenschappen die u selecteert.
* U kunt het pad samen met de diepte van het exporteren definiëren.

>[!NOTE]
>
>De downloadfunctie en de standaardbestemming van uw browser worden gebruikt.

Met de wizard **CSV-export maken** kunt u het volgende selecteren:

* Te exporteren eigenschappen
   * Metagegevens
      * Naam
      * Gewijzigd
      * Gepubliceerd
      * Sjabloonmodel
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

Maak **CSV-rapport** Deze optie is beschikbaar wanneer u in het dialoogvenster **Sites** console (in lijstweergave): het is een optie van **Maken** vervolgkeuzemenu:

![etc-02](assets/etc-02.png)

Een CSV-export maken:

1. Open de **Sites**-console en ga indien nodig naar de gewenste locatie.
1. Selecteer op de werkbalk de optie **Maken** en vervolgens **CSV-rapport** om de wizard te openen:

   ![etc-03](assets/etc-03.png)

1. Selecteer de eigenschappen die u wilt exporteren.
1. Selecteer **Maken**.
