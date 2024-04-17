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

Als onderdeel van het integratieproces, configureert u de **DAM Update-element** workflow, die geschikt is voor integratie met InDesign. Bovendien vorm een volmachtsarbeider voor de server van het InDesign. Zie voor meer informatie [AEM Assets integreren met InDesign Server](/help/assets/indesign.md).

>[!NOTE]
>
>U kunt sjablonen voor InDesigns genereren op basis van InDesigns voordat u ze importeert in AEM Assets. Zie voor meer informatie [Werken met bestanden en sjablonen](https://helpx.adobe.com/indesign/using/files-templates.html).
>
>U kunt de elementen in uw sjablonen van InDesigns toewijzen aan XML-labels. De toegewezen labels worden als eigenschappen weergegeven wanneer u in Catalog Producer producteigenschappen toewijst aan sjablooneigenschappen. Ga voor meer informatie over XML-labels in InDesigns bestanden naar [Inhoud labelen voor XML](https://helpx.adobe.com/indesign/using/tagging-content-xml.html).

>[!NOTE]
>
>Alleen InDesign-bestanden (.indd) worden gebruikt als sjablonen. Bestanden met de extensie .indt worden niet ondersteund.

## Een catalogus maken {#creating-a-catalog}

De Producent van de Catalogus gebruikt de gegevens van het productinformatiebeheer (PIM) om producteigenschappen met de eigenschappen in kaart te brengen van XML die in het malplaatje worden getoond. Voer de volgende stappen uit om een catalogus te maken:

1. Klik in de gebruikersinterface Middelen op de knop **AEM logo** en ga naar **Middelen > Catalogi**.
1. In de **Catalogi** pagina, klikt u **Maken** op de werkbalk en selecteer vervolgens **Catalogus** in de lijst.
1. In de **Catalogus maken** voert u een naam en beschrijving (optioneel) voor de catalogus in en geeft u eventueel tags op. U kunt ook een miniatuurafbeelding toevoegen voor de catalogus.

   ![create_catalog](assets/create_catalog.png)

1. Klikken **Opslaan**. Er verschijnt een bevestigingsvenster met de melding dat de catalogus is gemaakt. Klikken **Gereed** het dialoogvenster sluiten.
1. Als u de gemaakte catalogus wilt openen, klikt u op de catalogus in het **Catalogi** pagina.

   >[!NOTE]
   >
   >Als u de catalogus wilt openen, klikt u ook op **Openen** in het bevestigingsdialoogvenster dat in de vorige stap is vermeld.

1. Als u pagina&#39;s wilt toevoegen aan de catalogus, klikt u op **Maken** in de werkbalk en kies vervolgens de optie **Nieuwe pagina** -optie.
1. Selecteer in de wizard een sjabloon InDesign voor uw pagina. Klik vervolgens op **Volgende**.
1. Geef een naam voor de pagina en een optionele beschrijving op. Geef eventueel tags op.
1. Klik op de knop **Maken** op de werkbalk. Klik vervolgens op **Openen** in het dialoogvenster. De eigenschappen van het product worden weergegeven in het linkerdeelvenster. De vooraf gedefinieerde eigenschappen voor de sjabloon InDesign worden weergegeven in het rechterdeelvenster.
1. Sleep vanuit het linkerdeelvenster de producteigenschappen naar de sjablooneigenschappen van het InDesign en maak een koppeling tussen deze eigenschappen.

   Als u wilt zien hoe de pagina in real-time wordt weergegeven, klikt u op de knop **Voorvertoning** in het rechterdeelvenster.

1. Herhaal stap 6-9 om meer pagina&#39;s te maken. Als u vergelijkbare pagina&#39;s voor andere producten wilt maken, selecteert u de pagina en klikt u op de knop **Vergelijkbare pagina&#39;s maken** op de werkbalk.

   ![create_similar_pages](assets/create_similar_pages.png)

   >[!NOTE]
   >
   >U kunt alleen vergelijkbare pagina&#39;s maken voor producten met een vergelijkbare structuur.

   Klik op het pictogram Toevoegen, selecteer producten in de productkiezer en klik vervolgens op **Selecteren** op de werkbalk.

   ![select_product](assets/select_product.png)

1. Klik op de werkbalk op **Maken**. Klikken **Gereed** het dialoogvenster sluiten. Vergelijkbare pagina&#39;s worden opgenomen in uw catalogus.
1. Als u een bestaand InDesign aan de catalogus wilt toevoegen, klikt u op **Maken** in de werkbalk en kiest u **Toevoegen aan bestaande pagina** -optie.
1. Selecteer het bestand InDesign en klik op **Toevoegen** op de werkbalk. Klik vervolgens op **OK** het dialoogvenster sluiten.

   Als de metagegevens van de producten waarnaar u verwijst in de cataloguspagina&#39;s worden gewijzigd, worden de wijzigingen niet automatisch doorgevoerd in de cataloguspagina&#39;s. Een banner met het label **Stale** wordt weergegeven op de productafbeeldingen in de cataloguspagina&#39;s waarnaar wordt verwezen, om aan te geven dat de metagegevens voor de producten waarnaar wordt verwezen niet up-to-date zijn.

   ![chlimage_1-117](assets/chlimage_1-117a.png)

   Om ervoor te zorgen dat de productbeelden op de recentste meta-gegevensveranderingen wijzen, selecteer de pagina in de console van de Catalogus en klik **Pagina bijwerken** op de werkbalk.

   ![chlimage_1-118](assets/chlimage_1-118a.png)

   >[!NOTE]
   >
   >Als u de metagegevens voor een product waarnaar wordt verwezen wilt wijzigen, navigeert u naar de Producten-console (**AEM** > **Handel** > **Producten**) en selecteert u het product. Klik vervolgens op de knop **Eigenschappen weergeven** op de werkbalk en bewerk de metagegevens op de pagina Eigenschappen van het element.

1. Als u de pagina&#39;s in de catalogus opnieuw wilt rangschikken, klikt u op de knop **Maken** pictogram in de werkbalk en kies **Samenvoegen** in het menu. In de tovenaar, laat de carrousel op bovenkant u pagina&#39;s opnieuw rangschikken door hen te slepen. U kunt ook pagina&#39;s verwijderen.

1. Klikken **Volgende**. Als u een bestaand InDesign wilt toevoegen als omslagpagina, klikt u op **Bladeren** naast de **Voorblad kiezen** en geeft u het pad op voor de sjabloon voor de omslagpagina.
1. Klikken **Opslaan** en klik vervolgens op **Gereed** om het bevestigingsvenster te sluiten.
Bij het selecteren van de **Gereed** wordt een dialoogvenster geopend waarin u kunt opgeven of de PDF-weergave moet worden uitgevoerd.
   ![exporteren naar pdf](assets/CatalogPDF.png)
Als de optie Acrobat(PDF) is geselecteerd, wordt een PDF-uitvoering gemaakt in  **/jcr:content/renditions** naast indesign-uitvoering. U kunt alle uitvoeringen downloaden door het selectievakje Uitvoeringen te selecteren in het dialoogvenster Downloaden.

1. Als u een voorvertoning wilt genereren voor de catalogus die u hebt gemaakt, selecteert u deze in het dialoogvenster **Catalogi** en klikt u op de knop **Voorvertoning** op de werkbalk.

   ![chlimage_1-119](assets/chlimage_1-119a.png)

   Bekijk de pagina&#39;s in de catalogus in de voorvertoning. Klikken **Sluiten** om de voorvertoning te sluiten.
