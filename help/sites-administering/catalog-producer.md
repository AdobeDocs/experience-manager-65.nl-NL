---
title: Catalogusproducent
seo-title: Catalog Producer
seo-description: Learn how to use Catalog Producer in AEM Assets to generate product catalogs using your digital assets.
uuid: da822d83-8b99-4089-ae1b-11d897d4044e
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: integration
content-type: reference
discoiquuid: 90e36522-3af1-4a8a-b044-1c828c52974e
description: Catalogusproducent
exl-id: 76a46c62-d47d-4970-8a3a-d56015639548
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '882'
ht-degree: 0%

---

# Catalogusproducent{#catalog-producer}

Leer hoe u met Catalog Producer in AEM Assets productcatalogi kunt genereren met behulp van uw digitale middelen.

Met de Adobe Experience Manager (AEM) Assets Catalog Producer, kunt u catalogi voor uw merkproducten tot stand brengen gebruikend InDesign malplaatjes die uit een InDesign toepassing worden ingevoerd. Als u InDesign-sjablonen wilt importeren, moet u eerst AEM Assets integreren met een InDesign-server.

## Integreren met InDesign-server {#integrating-with-indesign-server}

Als onderdeel van het integratieproces, configureert u de **DAM Update-element** workflow, die geschikt is voor integratie met InDesign. Daarnaast configureert u een proxyworker voor de InDesign-server. Zie voor meer informatie [AEM Assets integreren met InDesign Server](/help/assets/indesign.md).

>[!NOTE]
>
>U kunt InDesign-sjablonen genereren op basis van InDesign-bestanden voordat u ze importeert in AEM Assets. Zie voor meer informatie [Werken met bestanden en sjablonen](https://helpx.adobe.com/indesign/using/files-templates.html).
>
>U kunt de elementen in uw sjablonen van InDesign toewijzen aan XML-labels. De toegewezen labels worden als eigenschappen weergegeven wanneer u in Catalog Producer producteigenschappen toewijst aan sjablooneigenschappen. Zie voor meer informatie over XML-labels in InDesign-bestanden [Inhoud labelen voor XML](https://helpx.adobe.com/indesign/using/tagging-content-xml.html).

>[!NOTE]
>
>Alleen InDesign-bestanden (.indd) worden gebruikt als sjablonen. Bestanden met de extensie .indt worden niet ondersteund.

## Een catalogus maken {#creating-a-catalog}

De Producent van de Catalogus gebruikt de gegevens van het productinformatiebeheer (PIM) om producteigenschappen met de eigenschappen in kaart te brengen van XML die in het malplaatje worden getoond. Voer de volgende stappen uit om een catalogus te maken:

1. Tik in de gebruikersinterface Middelen op de knop **AEM** en ga naar **Middelen > Catalogi**.
1. In de **Catalogi** pagina, tikken/klikken **Maken** op de werkbalk en selecteer vervolgens **Catalogus** in de lijst.
1. In de **Catalogus maken** voert u een naam en beschrijving (optioneel) voor de catalogus in en geeft u eventueel tags op. U kunt ook een miniatuurafbeelding toevoegen voor de catalogus.

   ![create_catalog](assets/create_catalog.png)

1. Tikken/klikken **Opslaan**. Er verschijnt een bevestigingsvenster met de melding dat de catalogus is gemaakt. Tikken/klikken **Gereed** om het dialoogvenster te sluiten.
1. Als u de gemaakte catalogus wilt openen, tikt u erop of klikt u erop in het dialoogvenster **Catalogi** pagina.

   >[!NOTE]
   >
   >Als u de catalogus wilt openen, kunt u ook tikken of erop klikken **Openen** in het bevestigingsdialoogvenster dat in de vorige stap is vermeld.

1. Tik op pagina&#39;s of klik op **Maken** in de werkbalk en kies vervolgens de optie **Nieuwe pagina** optie.
1. Selecteer in de wizard een InDesign-sjabloon voor uw pagina. Tik vervolgens/klik op **Volgende**.
1. Geef een naam voor de pagina en een optionele beschrijving op. Geef eventueel tags op.
1. Tik/klik op de knop **Maken** op de werkbalk. Tik vervolgens/klik op **Openen** in het dialoogvenster. De eigenschappen van het product worden weergegeven in het linkerdeelvenster. De vooraf gedefinieerde eigenschappen voor de sjabloon InDesign worden weergegeven in het rechterdeelvenster.
1. Sleep vanuit het linkerdeelvenster de producteigenschappen naar de InDesign-sjablooneigenschappen en maak een koppeling tussen deze eigenschappen.

   Tik op de knop **Voorvertoning** in het rechterdeelvenster.

1. Herhaal stap 6-9 om meer pagina&#39;s te maken. Als u vergelijkbare pagina&#39;s voor andere producten wilt maken, selecteert u de pagina en tikt u op de knop **Vergelijkbare pagina&#39;s maken** op de werkbalk.

   ![create_similar_pages](assets/create_similar_pages.png)

   >[!NOTE]
   >
   >U kunt alleen vergelijkbare pagina&#39;s maken voor producten met een vergelijkbare structuur.

   Tik/klik op het pictogram Toevoegen, selecteer producten in de productkiezer en tik/klik op **Selecteren** op de werkbalk.

   ![select_product](assets/select_product.png)

1. Klik/tik vanuit de werkbalk **Maken**. Tikken/klikken **Gereed** om het dialoogvenster te sluiten. Vergelijkbare pagina&#39;s worden opgenomen in uw catalogus.
1. Tik/klik op een bestaand InDesign-bestand om het toe te voegen aan uw catalogus **Maken** in de werkbalk en kiest u de optie **Toevoegen aan bestaande pagina** optie.
1. Selecteer het InDesign-bestand en tik/klik op **Toevoegen** op de werkbalk. Tik vervolgens/klik op **OK** om het dialoogvenster te sluiten.

   Als de metagegevens van de producten waarnaar u verwijst in de cataloguspagina&#39;s worden gewijzigd, worden de wijzigingen niet automatisch doorgevoerd in de cataloguspagina&#39;s. Een banner met het label **Stale** wordt weergegeven op de productafbeeldingen in de cataloguspagina&#39;s waarnaar wordt verwezen, om aan te geven dat de metagegevens voor de producten waarnaar wordt verwezen niet up-to-date zijn.

   ![chlimage_1-117](assets/chlimage_1-117a.png)

   Om ervoor te zorgen dat de productafbeeldingen de recentste meta-gegevensveranderingen weerspiegelen, selecteer de pagina in de console van de Catalogus en klik/tik **Pagina bijwerken** op de werkbalk.

   ![chlimage_1-118](assets/chlimage_1-118a.png)

   >[!NOTE]
   >
   >Als u de metagegevens voor een product waarnaar wordt verwezen wilt wijzigen, navigeert u naar de Producten-console (**Logo AEM** > **Handel** > **Producten**) en selecteert u het product. Klik vervolgens op **Eigenschappen weergeven** op de werkbalk en bewerk de metagegevens op de pagina Eigenschappen van het element.

1. Tik op of klik op de knop **Maken** pictogram in de werkbalk en kies vervolgens **Samenvoegen** in het menu. Met de carrousel bovenaan in de wizard kunt u pagina&#39;s opnieuw ordenen door ze te slepen. U kunt ook pagina&#39;s verwijderen.

1. Tikken/klikken **Volgende**. Tik/klik op een bestaand InDesign-bestand om het als voorblad toe te voegen **Bladeren** naast de **Voorblad kiezen** en geeft u het pad op voor de sjabloon voor de omslagpagina.
1. Tikken/klikken **Opslaan** en tikken/klikken **Gereed** om het bevestigingsvenster te sluiten.
Bij het selecteren van de **Gereed** wordt een dialoogvenster geopend waarin u kunt opgeven of de PDF-weergave moet worden uitgevoerd.
   ![exporteren naar pdf](assets/CatalogPDF.png)
Als de optie Acrobat(PDF) is geselecteerd, wordt een PDF-uitvoering gemaakt in  **/jcr:content/renditions** naast indesign-uitvoering. U kunt alle uitvoeringen downloaden door het selectievakje Uitvoeringen te selecteren in het dialoogvenster Downloaden.

1. Als u een voorvertoning wilt genereren voor de catalogus die u hebt gemaakt, selecteert u deze in het dialoogvenster **Catalogi** en klikt u op de knop **Voorvertoning** op de werkbalk.

   ![chlimage_1-119](assets/chlimage_1-119a.png)

   Bekijk de pagina&#39;s in de catalogus in de voorvertoning. Tikken/klikken **Sluiten** om de voorvertoning te sluiten.
