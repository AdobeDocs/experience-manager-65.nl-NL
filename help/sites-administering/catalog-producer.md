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

---


# Catalogusproducent{#catalog-producer}

Leer hoe u met Catalog Producer in AEM Assets productcatalogi kunt genereren met behulp van uw digitale middelen.

Met de Adobe Experience Manager (AEM) Assets Catalog Producer, kunt u catalogi voor uw merkproducten maken met InDesign-sjablonen die uit een InDesign-toepassing zijn geïmporteerd. Als u InDesign-sjablonen wilt importeren, moet u eerst AEM-elementen integreren met een InDesign-server.

## Integreren met InDesign-server {#integrating-with-indesign-server}

Configureer als onderdeel van het integratieproces de workflow **DAM Update Asset** , die geschikt is voor integratie met InDesign. Configureer bovendien een proxy-worker voor de InDesign-server. Zie AEM-elementen [integreren met InDesign Server](/help/assets/indesign.md)voor meer informatie.

>[!NOTE]
>
>U kunt InDesign-sjablonen genereren vanuit InDesign-bestanden voordat u deze importeert in AEM-elementen. Zie [Werken met bestanden en sjablonen](https://helpx.adobe.com/indesign/using/files-templates.html)voor meer informatie.
>
>U kunt de elementen in uw InDesign-sjablonen toewijzen aan XML-labels. De toegewezen labels worden als eigenschappen weergegeven wanneer u in Catalog Producer producteigenschappen toewijst aan sjablooneigenschappen. Zie Inhoud [labelen voor XML](https://helpx.adobe.com/indesign/using/tagging-content-xml.html)voor meer informatie over XML-labels in InDesign-bestanden.

>[!NOTE]
>
>Alleen InDesign-bestanden (.indd) worden gebruikt als sjablonen. Bestanden met de extensie .indt worden niet ondersteund.

## Een catalogus maken {#creating-a-catalog}

De Producent van de Catalogus gebruikt de gegevens van het productinformatiebeheer (PIM) om producteigenschappen met de eigenschappen in kaart te brengen van XML die in het malplaatje worden getoond. Voer de volgende stappen uit om een catalogus te maken:

1. Tik in de gebruikersinterface Middelen op het **AEM-logo** of klik erop en ga naar **Middelen > Catalogi**.
1. Tik op de pagina **Catalogi** of klik op **Maken** op de werkbalk en selecteer vervolgens **Catalogus** in de lijst.
1. Voer op de pagina Catalogus **** maken een naam en beschrijving (optioneel) voor de catalogus in en geef eventueel tags op. U kunt ook een miniatuurafbeelding toevoegen voor de catalogus.

   ![create_catalog](assets/create_catalog.png)

1. Tik/klik op **Opslaan**. Er verschijnt een bevestigingsvenster met de melding dat de catalogus is gemaakt. Tik/klik op **Gereed** om het dialoogvenster te sluiten.
1. Tik of klik op de pagina **Catalogi om de gemaakte catalogus te openen** .

   >[!NOTE]
   >
   >Als u de catalogus wilt openen, tikt u ook op **Openen** in het bevestigingsvenster dat in de vorige stap is vermeld.

1. Tik op of klik op **Maken** op de werkbalk en kies vervolgens de optie **Nieuwe pagina** om pagina&#39;s aan de catalogus toe te voegen.
1. Selecteer in de wizard een InDesign-sjabloon voor uw pagina. Tik vervolgens op **Volgende** of klik op Volgende.
1. Geef een naam voor de pagina en een optionele beschrijving op. Geef eventueel tags op.
1. Tik/klik op de werkbalk op **Maken** . Tik vervolgens op **Openen** of klik op Openen in het dialoogvenster. De eigenschappen van het product worden weergegeven in het linkerdeelvenster. De vooraf gedefinieerde eigenschappen voor de InDesign-sjabloon worden in het rechterdeelvenster weergegeven.
1. Sleep vanuit het linkerdeelvenster de producteigenschappen naar de InDesign-sjablooneigenschappen en maak een koppeling tussen deze eigenschappen.

   Tik of klik op het tabblad **Voorvertoning** in het rechterdeelvenster om te zien hoe de pagina in real-time wordt weergegeven.

1. Herhaal stap 6-9 om meer pagina&#39;s te maken. Als u vergelijkbare pagina&#39;s voor andere producten wilt maken, selecteert u de pagina en tikt u op het pictogram Gelijksoortige pagina&#39;s **** maken of klikt u op de werkbalk.

   ![create_similar_pages](assets/create_similar_pages.png)

   >[!NOTE]
   >
   >U kunt alleen vergelijkbare pagina&#39;s maken voor producten met een vergelijkbare structuur.

   Tik/klik op het pictogram Toevoegen, selecteer producten in de productkiezer en tik op **Selecteren** of klik op de werkbalk.

   ![select_product](assets/select_product.png)

1. Klik/tik op **Maken** op de werkbalk. Tik/klik op **Gereed** om het dialoogvenster te sluiten. Vergelijkbare pagina&#39;s worden opgenomen in uw catalogus.
1. Als u een bestaand InDesign-bestand aan uw catalogus wilt toevoegen, tikt u op **Maken** of klikt u op de werkbalk en kiest u de optie **Toevoegen aan bestaande pagina** .
1. Selecteer het InDesign-bestand en tik/klik op **Toevoegen** op de werkbalk. Tik vervolgens op **OK** of klik op OK om het dialoogvenster te sluiten.

   Als de metagegevens van de producten waarnaar u verwijst in de cataloguspagina&#39;s worden gewijzigd, worden de wijzigingen niet automatisch doorgevoerd in de cataloguspagina&#39;s. Er wordt een banner met het label **Stale** weergegeven op de productafbeeldingen in de cataloguspagina&#39;s waarnaar wordt verwezen, om aan te geven dat de metagegevens voor de producten waarnaar wordt verwezen niet up-to-date zijn.

   ![chlimage_1-117](assets/chlimage_1-117a.png)

   Om ervoor te zorgen dat de productbeelden op de recentste meta-gegevensveranderingen wijzen, selecteer de pagina in de console van de Catalogus en klik/tik het **Update paginapictogram** van de toolbar.

   ![chlimage_1-118](assets/chlimage_1-118a.png)

   >[!NOTE]
   >
   >Als u de metagegevens voor een product waarnaar wordt verwezen wilt wijzigen, navigeert u naar de Products console (**AEM-logo** > **Handel** > **Producten**) en selecteert u het product. Klik vervolgens op het pictogram **Weergave-eigenschappen** of tik erop op de werkbalk en bewerk de metagegevens op de pagina Eigenschappen van het element.

1. Als u de pagina&#39;s in de catalogus opnieuw wilt rangschikken, tikt u op het pictogram **Maken** op de werkbalk en kiest u **Samenvoegen** in het menu. Met de carrousel bovenaan in de wizard kunt u pagina&#39;s opnieuw ordenen door ze te slepen. U kunt ook pagina&#39;s verwijderen.

1. Tik/klik op **Volgende**. Als u een bestaand InDesign-bestand als voorblad wilt toevoegen, tikt u op **Bladeren** of klikt u naast het vak Voorblad **** kiezen en geeft u het pad voor de sjabloon van de omslagpagina op.
1. Tik/klik op **Opslaan** en tik/klik op **Gereed** om het bevestigingsvenster te sluiten.
Als u de optie **Gereed** selecteert, wordt een dialoogvenster geopend waarin u kunt opgeven of de PDF-uitvoering moet worden uitgevoerd.
   ![exporteren naar PDF](assets/CatalogPDF.png)Als de optie Acrobat(PDF) is geselecteerd, wordt naast de indesign-uitvoering een PDF-uitvoering gemaakt in **/jcr:content/renditions** . U kunt alle uitvoeringen downloaden door het selectievakje Uitvoeringen te selecteren in het dialoogvenster Downloaden.

1. Als u een voorvertoning wilt genereren voor de catalogus die u hebt gemaakt, selecteert u deze in de **Catalogusconsole** en klikt u op het pictogram **Voorvertoning** op de werkbalk.

   ![chlimage_1-119](assets/chlimage_1-119a.png)

   Bekijk de pagina&#39;s in de catalogus in de voorvertoning. Tik/klik op **Sluiten** om de voorvertoning te sluiten.

