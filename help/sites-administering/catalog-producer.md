---
title: Catalogusproducent
seo-title: Catalogusproducent
seo-description: Leer hoe u met Catalog Producer in AEM Assets productcatalogi kunt genereren met behulp van uw digitale middelen.
uuid: da822d83-8b99-4089-ae1b-11d897d4044e
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: integration
content-type: reference
discoiquuid: 90e36522-3af1-4a8a-b044-1c828c52974e
translation-type: tm+mt
source-git-commit: 684d2d5f73d571a15c8155e7870134c28dc892b7
workflow-type: tm+mt
source-wordcount: '899'
ht-degree: 0%

---


# Catalogusproducent{#catalog-producer}

Leer hoe u met Catalog Producer in AEM Assets productcatalogi kunt genereren met behulp van uw digitale middelen.

Met de Adobe Experience Manager (AEM) Assets Catalog Producer, kunt u catalogi voor uw merkproducten tot stand brengen gebruikend InDesign malplaatjes die uit een InDesign toepassing worden ingevoerd. Als u InDesign-sjablonen wilt importeren, moet u eerst AEM Assets integreren met een InDesign-server.

## Integreren met InDesign-server {#integrating-with-indesign-server}

Als onderdeel van het integratieproces, configureert u de **DAM Update Asset**-workflow, die geschikt is voor integratie met InDesign. Daarnaast configureert u een proxyworker voor de InDesign-server. Zie [AEM Assets integreren met InDesign Server](/help/assets/indesign.md) voor meer informatie.

>[!NOTE]
>
>U kunt InDesign-sjablonen genereren op basis van InDesign-bestanden voordat u ze importeert in AEM Assets. Zie [Werken met bestanden en sjablonen](https://helpx.adobe.com/indesign/using/files-templates.html) voor meer informatie.
>
>U kunt de elementen in uw sjablonen van InDesign toewijzen aan XML-labels. De toegewezen labels worden als eigenschappen weergegeven wanneer u in Catalog Producer producteigenschappen toewijst aan sjablooneigenschappen. Zie [Inhoud labelen voor XML](https://helpx.adobe.com/indesign/using/tagging-content-xml.html) voor meer informatie over XML-codering in InDesign-bestanden.

>[!NOTE]
>
>Alleen InDesign-bestanden (.indd) worden gebruikt als sjablonen. Bestanden met de extensie .indt worden niet ondersteund.

## Een catalogus {#creating-a-catalog} maken

De Producent van de Catalogus gebruikt de gegevens van het productinformatiebeheer (PIM) om producteigenschappen met de eigenschappen in kaart te brengen van XML die in het malplaatje worden getoond. Voer de volgende stappen uit om een catalogus te maken:

1. Tik in de gebruikersinterface Middelen op het **AEM logo** en ga naar **Middelen > Catalogi**.
1. Tik op de pagina **Catalogi** of klik op **Maken** op de werkbalk en selecteer vervolgens **Catalogus** in de lijst.
1. Voer op de pagina **Catalogus maken** een naam en beschrijving (optioneel) voor de catalogus in en geef eventueel tags op. U kunt ook een miniatuurafbeelding toevoegen voor de catalogus.

   ![create_catalog](assets/create_catalog.png)

1. Tik/klik **Opslaan**. Er verschijnt een bevestigingsvenster met de melding dat de catalogus is gemaakt. Tik/klik **Done** om het dialoogvenster te sluiten.
1. Tik op de pagina **Catalogs** om de gemaakte catalogus te openen.

   >[!NOTE]
   >
   >Als u de catalogus wilt openen, tikt of klikt u op **Openen** in het bevestigingsvenster dat in de vorige stap is vermeld.

1. Als u pagina&#39;s wilt toevoegen aan de catalogus, tikt u op **Maken** op de werkbalk en kiest u de optie **Nieuwe pagina**.
1. Selecteer in de wizard een InDesign-sjabloon voor uw pagina. Tik vervolgens op **Volgende**.
1. Geef een naam voor de pagina en een optionele beschrijving op. Geef eventueel tags op.
1. Tik/klik op **Maken** van de werkbalk. Tik vervolgens op **Openen** in het dialoogvenster. De eigenschappen van het product worden weergegeven in het linkerdeelvenster. De vooraf gedefinieerde eigenschappen voor de sjabloon InDesign worden weergegeven in het rechterdeelvenster.
1. Sleep vanuit het linkerdeelvenster de producteigenschappen naar de InDesign-sjablooneigenschappen en maak een koppeling tussen deze eigenschappen.

   Tik/klik op het tabblad **Voorvertoning** in het rechterdeelvenster om te zien hoe de pagina in real-time wordt weergegeven.

1. Herhaal stap 6-9 om meer pagina&#39;s te maken. Als u vergelijkbare pagina&#39;s voor andere producten wilt maken, selecteert u de pagina en tikt u op het pictogram **Vergelijkbare pagina&#39;s maken** op de werkbalk.

   ![create_similar_pages](assets/create_similar_pages.png)

   >[!NOTE]
   >
   >U kunt alleen vergelijkbare pagina&#39;s maken voor producten met een vergelijkbare structuur.

   Tik/klik op het pictogram Toevoegen, selecteer producten in de productkiezer en tik/klik op **Selecteren** op de werkbalk.

   ![select_product](assets/select_product.png)

1. Klik/tik op **Maken** op de werkbalk. Tik/klik **Done** om het dialoogvenster te sluiten. Vergelijkbare pagina&#39;s worden opgenomen in uw catalogus.
1. Als u een bestaand InDesign-bestand aan uw catalogus wilt toevoegen, tikt u op **Maken** op de werkbalk en kiest u de optie **Toevoegen aan bestaande pagina**.
1. Selecteer het InDesign-bestand en tik/klik op **Toevoegen** op de werkbalk. Tik vervolgens op **OK** om het dialoogvenster te sluiten.

   Als de metagegevens van de producten waarnaar u verwijst in de cataloguspagina&#39;s worden gewijzigd, worden de wijzigingen niet automatisch doorgevoerd in de cataloguspagina&#39;s. Er wordt een banner met het label **Stale** weergegeven op de productafbeeldingen in de cataloguspagina&#39;s die naar verwijzen, om aan te geven dat de metagegevens voor de producten waarnaar wordt verwezen niet up-to-date zijn.

   ![chlimage_1-117](assets/chlimage_1-117a.png)

   Om ervoor te zorgen dat de productafbeeldingen de recentste meta-gegevensveranderingen weerspiegelen, selecteer de pagina in de console van de Catalogus en klik/tik **pagina van de Update** pictogram van de toolbar.

   ![chlimage_1-118](assets/chlimage_1-118a.png)

   >[!NOTE]
   >
   >Als u de metagegevens voor een product waarnaar wordt verwezen wilt wijzigen, navigeert u naar de productconsole (**AEM Logo** > **Handel** > **Producten**) en selecteert u het product. Klik vervolgens op het pictogram **Eigenschappen weergeven** op de werkbalk en bewerk de metagegevens op de pagina Eigenschappen van het element.

1. Als u de pagina&#39;s in de catalogus opnieuw wilt rangschikken, tikt u op het pictogram **Maken** op de werkbalk en kiest u **Samenvoegen** in het menu. Met de carrousel bovenaan in de wizard kunt u pagina&#39;s opnieuw ordenen door ze te slepen. U kunt ook pagina&#39;s verwijderen.

1. Tik/klik **Volgende**. Als u een bestaand InDesign-bestand als een omslagpagina wilt toevoegen, tikt u op **Bladeren** naast het vak **Voorblad kiezen** en geeft u het pad op voor de sjabloon voor de omslagpagina.
1. Tik/klik op **Opslaan** en tik/klik op **Gereed** om het bevestigingsvenster te sluiten.
Als u de optie **Done** selecteert, wordt een dialoogvenster geopend waarin u kunt opgeven of u .pdf-uitvoering wilt.
   ![exporteren naar ](assets/CatalogPDF.png)
pdfAls de optie Acrobat(PDF) is geselecteerd, wordt naast indesign-uitvoering een PDF-uitvoering gemaakt in   **/jcr:content/** renditions. U kunt alle uitvoeringen downloaden door het selectievakje Uitvoeringen te selecteren in het dialoogvenster Downloaden.

1. Als u een voorvertoning wilt genereren voor de catalogus die u hebt gemaakt, selecteert u deze in de console **Catalogs** en klikt u op het pictogram **Voorvertoning** op de werkbalk.

   ![chlimage_1-119](assets/chlimage_1-119a.png)

   Bekijk de pagina&#39;s in de catalogus in de voorvertoning. Tik/klik **Close** om de voorvertoning te sluiten.

