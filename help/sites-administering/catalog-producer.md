---
title: Catalogusproducent
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: integration
content-type: reference
description: Catalogusproducent
exl-id: 76a46c62-d47d-4970-8a3a-d56015639548
solution: Experience Manager, Experience Manager Sites
feature: Integration
role: Admin
source-git-commit: 66db4b0b5106617c534b6e1bf428a3057f2c2708
workflow-type: tm+mt
source-wordcount: '847'
ht-degree: 0%

---

# Catalogusproducent{#catalog-producer}

Leer hoe u met Catalog Producer in AEM Assets productcatalogi kunt genereren met behulp van uw digitale middelen.

Met de Adobe Experience Manager (AEM) Assets Catalog Producer, kunt u catalogi voor uw merkproducten tot stand brengen gebruikend InDesign malplaatjes die uit een toepassing van de InDesign worden ingevoerd. Als u sjablonen van InDesigns wilt importeren, moet u eerst AEM Assets integreren met een InDesign-server.

## Integreren met InDesign-server {#integrating-with-indesign-server}

Als deel van het integratieproces, vorm het **DAM de werkschema van de Activa van de Update**, dat voor integratie met InDesign geschikt is. Bovendien vorm een volmachtsarbeider voor de server van het InDesign. Voor details, zie [&#x200B; Integrerend AEM Assets met InDesign Server &#x200B;](/help/assets/indesign.md).

>[!NOTE]
>
>U kunt sjablonen voor InDesigns genereren op basis van InDesigns voordat u ze importeert in AEM Assets. Voor details, zie [&#x200B; Werkend met dossiers en malplaatjes &#x200B;](https://helpx.adobe.com/nl/indesign/using/files-templates.html).
>
>U kunt de elementen in uw sjablonen van InDesigns toewijzen aan XML-labels. De toegewezen labels worden als eigenschappen weergegeven wanneer u in Catalog Producer producteigenschappen toewijst aan sjablooneigenschappen. Om over XML te leren etiketterend in de dossiers van het InDesign, zie [&#x200B; het Etiketteren inhoud voor XML &#x200B;](https://helpx.adobe.com/nl/indesign/using/tagging-content-xml.html).

>[!NOTE]
>
>Alleen InDesign-bestanden (.indd) worden gebruikt als sjablonen. Bestanden met de extensie .indt worden niet ondersteund.

## Een catalogus maken {#creating-a-catalog}

De Producent van de Catalogus gebruikt de gegevens van het productinformatiebeheer (PIM) om producteigenschappen met de eigenschappen in kaart te brengen van XML die in het malplaatje worden getoond. Voer de volgende stappen uit om een catalogus te maken:

1. Van het gebruikersinterface van Assets, klik het **AEM embleem**, en ga naar **Assets > Catalogi**.
1. In de **pagina van Catalogi**, klik **&#x200B;**&#x200B;van de toolbar creëren, en selecteer dan **Catalogus** van de lijst.
1. In **creeer de pagina van de Catalogus**, ga een naam en een beschrijving (facultatief) voor de catalogus in en specificeer markeringen, als om het even welk. U kunt ook een miniatuurafbeelding toevoegen voor de catalogus.

   ![&#x200B; create_catalog &#x200B;](assets/create_catalog.png)

1. Klik **sparen**. Er verschijnt een bevestigingsvenster met de melding dat de catalogus is gemaakt. Klik **Gedaan** om de dialoog te sluiten.
1. Om de catalogus te openen u creeerde, klik het van de **pagina van Catalogi**.

   >[!NOTE]
   >
   >Om de catalogus te openen, kunt u **Open** in de bevestigingsdialoog ook klikken die in de vorige stap wordt vermeld.

1. Om pagina&#39;s aan de catalogus toe te voegen, **creeer** van de toolbar, en kies dan de **Nieuwe pagina** optie.
1. Selecteer in de wizard een sjabloon InDesign voor uw pagina. Dan, klik **daarna**.
1. Geef een naam voor de pagina en een optionele beschrijving op. Geef eventueel tags op.
1. Klik **creëren** van de toolbar. Dan, klik **Open** van de dialoog. De eigenschappen van het product worden weergegeven in het linkerdeelvenster. De vooraf gedefinieerde eigenschappen voor de sjabloon InDesign worden weergegeven in het rechterdeelvenster.
1. Sleep vanuit het linkerdeelvenster de producteigenschappen naar de sjablooneigenschappen van het InDesign en maak een koppeling tussen deze eigenschappen.

   Om te bekijken hoe de pagina in echt - tijd verschijnt, klik het **lusje van de Voorproef** op de juiste ruit.

1. Herhaal stap 6-9 om meer pagina&#39;s te maken. Om gelijkaardige pagina&#39;s voor andere producten tot stand te brengen, selecteer de pagina en klik **creeer gelijkaardige pagina&#39;s** pictogram van de toolbar.

   ![&#x200B; create_similar_pages &#x200B;](assets/create_similar_pages.png)

   >[!NOTE]
   >
   >U kunt alleen vergelijkbare pagina&#39;s maken voor producten met een vergelijkbare structuur.

   Klik het Add pictogram, selecteer producten van de productkiezer, en klik dan **Uitgezocht** van de toolbar.

   ![&#x200B; select_product &#x200B;](assets/select_product.png)

1. Van de toolbar, leidt de klik **tot**. Klik **Gedaan** om de dialoog te sluiten. Vergelijkbare pagina&#39;s worden opgenomen in uw catalogus.
1. Om het even welk bestaand dossier van het InDesign aan uw catalogus toe te voegen, **creeer** van de toolbar, en kies **toevoegen aan bestaande pagina** optie.
1. Selecteer het dossier van het InDesign, en de klik **voegt** van de toolbar toe. Dan, klik O.K. **om de dialoog te sluiten.**

   Als de metagegevens van de producten waarnaar u verwijst in de cataloguspagina&#39;s worden gewijzigd, worden de wijzigingen niet automatisch doorgevoerd in de cataloguspagina&#39;s. Een banner geëtiketteerd **Stale** verschijnt op de productbeelden in de het van verwijzingen voorzien cataloguspagina&#39;s, erop wijzend dat de meta-gegevens voor de referenced producten niet bijgewerkt zijn.

   ![&#x200B; chlimage_1-117 &#x200B;](assets/chlimage_1-117a.png)

   Om ervoor te zorgen dat de productbeelden op de recentste meta-gegevensveranderingen wijzen, selecteer de pagina in de console van de Catalogus en klik het **pagina van de Update** pictogram van de toolbar.

   ![&#x200B; chlimage_1-118 &#x200B;](assets/chlimage_1-118a.png)

   >[!NOTE]
   >
   >Om de meta-gegevens voor een referenced product te veranderen, navigeer aan de console van Producten (**AEM Logo** > **Commerce** > **Producten**), en selecteer het product. Dan, klik het **pictogram van de Eigenschappen van de Mening** van de toolbar en geef de meta-gegevens in de pagina van Eigenschappen van de activa uit.

1. Om de pagina&#39;s in catalogus opnieuw te rangschikken, **creeer** pictogram van de toolbar en kies dan **Samenvoegen** van het menu. In de tovenaar, laat de carrousel op bovenkant u pagina&#39;s opnieuw rangschikken door hen te slepen. U kunt ook pagina&#39;s verwijderen.

1. Klik **daarna**. Om een bestaand dossier van het InDesign als omslagpagina toe te voegen, **doorbladert** naast **kiezen de doos van de Pagina van de Omslag**, en specificeert de weg voor het malplaatje van de omslagpagina.
1. Klik **sparen**, en klik dan **Gedaan** om de bevestigingsdialoog te sluiten.
Bij het selecteren van de **Gereed** optie, opent een dialoogdoos om te selecteren of u.pdf vertoning wilt.
   ![&#x200B; uitvoer naar pdf &#x200B;](assets/CatalogPDF.png)
Als de optie Acrobat(PDF) is geselecteerd, wordt naast indesign-uitvoering een pdf-uitvoering gemaakt in **/jcr:content/renditions** . U kunt alle uitvoeringen downloaden door het selectievakje Uitvoeringen te selecteren in het dialoogvenster Downloaden.

1. Om een voorproef voor de catalogus te produceren u creeerde, het in de **console van Catalogi** te selecteren, en dan het **pictogram van de Voorproef** van de toolbar te klikken.

   ![&#x200B; chlimage_1-119 &#x200B;](assets/chlimage_1-119a.png)

   Bekijk de pagina&#39;s in de catalogus in de voorvertoning. Klik **dicht** om de voorproef te sluiten.
