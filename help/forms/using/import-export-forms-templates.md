---
title: Elementen importeren en exporteren naar AEM Forms
description: U kunt adaptieve formulieren en sjablonen importeren en exporteren vanuit en in naar AEM instanties. Zo kunt u formulieren migreren of verplaatsen naar andere systemen.
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: forms-manager
docset: aem65
role: Admin,User
exl-id: b5f6a54e-92d1-4631-a1d1-184f37d174b6
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms,Foundation Components
source-git-commit: d7b9e947503df58435b3fee85a92d51fae8c1d2d
workflow-type: tm+mt
source-wordcount: '2492'
ht-degree: 0%

---

# Elementen importeren en exporteren naar AEM Forms{#importing-and-exporting-assets-to-aem-forms}

U kunt formulieren en gerelateerde elementen, thema&#39;s, gegevenswoordenboeken, documentfragmenten en letters verplaatsen tussen verschillende AEM Forms-instanties. Een dergelijke verplaatsing is vereist wanneer u systemen migreert of formulieren verplaatst van een werkgebiedserver naar een productieserver. Voor die elementen waarvoor uploaden en importeren via de gebruikersinterface van AEM Forms wordt ondersteund, is het gebruik van de gebruikersinterface van Forms de aanbevolen manier voor exporteren of importeren. Het wordt niet aanbevolen om AEM pakketbeheer te gebruiken voor het exporteren of importeren van dergelijke elementen.

>[!NOTE]
>
>* In AEM 6.4 Forms zijn de structuur en paden van de crx-repository veranderd. Als u elementen uit een vorige versie importeert naar AEM 6.4 Forms en het formulier afhankelijk is van de oudere structuur, moet u de afhankelijkheden handmatig exporteren. Zie voor meer informatie over wijzigingen in de structuur en paden van de gegevensopslagruimte [Herstructurering van AEM](/help/sites-deploying/repository-restructuring.md).
>

## Forms- en documentmiddelen downloaden of uploaden {#download-or-upload-forms-amp-documents-assets}

Met de AEM Forms-gebruikersinterface kunt u elementen van een AEM-instantie exporteren door deze te downloaden als een AEM CRX-pakket of binaire bestanden. U kunt het gedownloade AEM CRX-pakket of het binaire bestand vervolgens importeren in een andere AEM.

Exporteren en importeren via de gebruikersinterface van AEM Forms wordt ondersteund voor alle elementen, behalve voor adaptieve formuliersjablonen en beleid voor adaptieve formulierinhoud. Bij het exporteren van een adaptief formulier uit de gebruikersinterface van AEM Forms worden de gerelateerde aangepaste formuliersjabloon en het inhoudsbeleid daarom niet automatisch geëxporteerd als andere gerelateerde elementen.

Voor deze elementtypen moet u AEM Package Manager gebruiken om een CRX-pakket te maken op de bron- AEM server en het pakket op de doelserver te installeren. Zie voor informatie over het maken en installeren van pakketten [Werken met pakketten](/help/sites-administering/package-manager.md).

### Forms- en Documenten downloaden {#download-forms-amp-documents-assets}

Forms en Documenten downloaden:

1. Meld u aan bij de AEM Forms-instantie.
1. Experience Manager selecteren ![adobeexperienceManager](assets/adobeexperiencemanager.png) pictogram > navigatie ![kompas](assets/compass.png) pictogram> Forms > Forms &amp; Documents.
1. Selecteer de formulierelementen en selecteer de **Downloaden** pictogram.
1. Kies in het (de) downloadmiddel(en) een van de volgende opties en selecteer **Downloaden**.

   * **Downloaden als CRX-pakket:** Gebruik de optie om alle geselecteerde elementen en gerelateerde afhankelijkheden te downloaden van een AEM Forms-instantie en naar een andere instantie te verplaatsen. Alle elementen en mappen worden als crx-pakket gedownload. Alle formulierelementen, zoals de formulieren die zijn geschreven in AEM (adaptieve formulieren, interactieve communicatie en adaptieve formulierfragmenten), formuliersets, formuliersjablonen, PDF-documenten en bronnen (XSD&#39;s, XFS, afbeeldingen) kunnen als pakket worden gedownload vanuit de gebruikersinterface van AEM Forms.
Het voordeel van het downloaden van elementen als pakket is dat ook elementen worden gedownload die door het geselecteerde element zijn gebruikt om te downloaden. Als u bijvoorbeeld een adaptief formulier hebt waarin een formuliersjabloon, XSD en een afbeelding worden gebruikt. Wanneer u dit adaptieve formulier selecteert en het als pakket downloadt, bevat het gedownloade pakket ook de formuliersjabloon, XSD en de afbeelding. Alle metagegevenseigenschappen (inclusief aangepaste eigenschappen) die aan het element zijn gekoppeld, worden ook gedownload.

   * **Elementen downloaden als binaire bestanden:** Gebruik de optie om alleen formuliersjablonen (XDP), PDF forms (PDF), documenten (PDF) en bronnen (afbeeldingen, schema&#39;s, opmaakmodellen) te downloaden. U kunt deze elementen bewerken met externe toepassingen. De formulierbestanden met binaire bestanden, zoals XSD&#39;s, XDP&#39;s, afbeeldingen, PDF en XDP&#39;s, worden gedownload als ZIP-bestand.
U kunt geen adaptieve formulieren, interactieve communicatie, adaptieve formulierfragmenten, thema&#39;s en formuliersets downloaden met **Elementen downloaden als binaire bestanden** -optie. Als u deze middelen wilt downloaden, kunt u het beste **Downloaden als CRX-pakket** -optie.

   De geselecteerde elementen worden gedownload als een archief (.zip-bestand).

   >[!NOTE]
   >
   >Zowel AEM pakket- als binaire bestanden worden gedownload als een archief (.zip-bestand). De sjablonen voor de elementen worden niet samen met de elementen gedownload. U moet de elementsjablonen afzonderlijk exporteren.

### Forms- en documentmiddelen uploaden {#upload-forms-amp-documents-assets}

Forms en Documenten uploaden:

<!--[!VIDEO](https://vimeo.com/)-->

1. Meld u aan bij de AEM Forms-instantie.
1. Experience Manager selecteren ![adobeexperienceManager](assets/adobeexperiencemanager.png) pictogram > navigatie ![kompas](assets/compass.png) pictogram> Forms> Forms &amp; Documents.
1. Selecteren **Maken** >**Bestand uploaden**. Er wordt een dialoogvenster voor het uploaden of verpakken weergegeven.
1. Blader in het dialoogvenster naar het pakket of het archief dat u wilt importeren en selecteer dit. U kunt ook PDF-documenten, XSD&#39;s, afbeeldingen, stijlpagina&#39;s en XDP-formulieren selecteren. Selecteren **Openen**. De map of de bestandsnaam die u selecteert, mag geen speciale tekens bevatten.

   Controleer in het dialoogvenster de details van de elementen die worden geüpload en selecteer **Uploaden**.

   Als u een bestaand formulierelement uploadt, wordt het element bijgewerkt.

   >[!NOTE]
   >
   >Het uploaden van een pakket vervangt de bestaande maphiërarchie niet. Als u bijvoorbeeld een adaptief formulier hebt met de naam &#39;Training&#39; op de locatie /content/dam/formsanddocuments op één server. U downloadt het adaptieve formulier en uploadt het formulier naar een andere server. De tweede server heeft ook een map met de naam &#39;Training&#39; op dezelfde locatie/content/dam/formsanddocuments. Het uploaden mislukt.

## Een thema downloaden of uploaden {#downloading-or-uploading-a-theme}

Met AEM Forms kunt u thema&#39;s maken, downloaden of uploaden. Net als andere elementen, zoals formulieren, documenten en letters, wordt een thema gemaakt. U kunt een thema maken, dit downloaden en uploaden naar een aparte versie om het opnieuw te gebruiken. Zie voor meer informatie over thema&#39;s [Thema&#39;s in AEM Forms](../../forms/using/themes.md).

### Een thema downloaden {#downloading-a-theme}

U kunt thema&#39;s in AEM Forms exporteren die u kunt gebruiken in andere projecten of instanties. AEM kunt u thema downloaden als een ZIP-bestand dat u kunt uploaden op het exemplaar.

Een thema downloaden:

1. Meld u aan bij de AEM Forms-instantie.
1. Experience Manager selecteren ![adobeexperienceManager](assets/adobeexperiencemanager.png) pictogram > navigatie ![kompas](assets/compass.png) pictogram> Forms> Thema&#39;s.
1. Selecteer het thema en selecteer **Downloaden**. Het thema wordt gedownload als een archief (.zip-bestand).

### Een thema uploaden {#uploading-a-theme}

U kunt gemaakte thema&#39;s gebruiken met voorinstellingen voor stijlen voor uw project. U kunt themapakketten die anderen maken, importeren door deze te uploaden naar uw project.

Een thema uploaden:

1. Navigeer in Experience Manager naar **Forms > Thema&#39;s**.
1. Klik op de pagina Thema&#39;s op **Maken > Bestand uploaden**.
1. Blader in de vraag Bestand uploaden naar en selecteer een themapakket op uw computer en klik op **Uploaden**.
Het geüploade thema is beschikbaar op de themapagina.

1. Meld u aan bij de AEM Forms-instantie.
1. Experience Manager selecteren ![adobeexperienceManager](assets/adobeexperiencemanager.png) pictogram > navigatie ![kompas](assets/compass.png) pictogram> Forms> Thema&#39;s.
1. klikken **Maken** > **Bestand uploaden**. Blader in de vraag Bestand uploaden naar en selecteer een themapakket op uw computer en klik op **Uploaden**. Het thema wordt geüpload.

## Importeren en exporteren van activa in Correspondentenbeheer {#import-and-export-assets-in-correspondence-management}

Als u elementen, zoals gegevenswoordenboeken, letters en documentfragmenten, wilt delen tussen twee verschillende implementaties van Correspondence Management, kunt u .cmp-bestanden maken en delen. Een .cmp-bestand kan een of meer gegevenswoordenboeken, letters, documentfragmenten en formulieren bevatten.

### Documentfragmenten, letters en/of gegevenswoordenboeken exporteren {#export-document-fragments-letters-and-or-data-dictionaries}

1. In de brieven, documentfragmenten, of de pagina&#39;s van het gegevenswoordenboek, selecteer en selecteer de activa u naar één enkel pakket wilt uitvoeren, en dan Rij voor Download selecteren. De elementen zijn in een voor export geschikte indeling geplaatst.
1. Herhaal indien nodig de bovenstaande stap om letters, documentfragmenten en gegevenswoordenboeken toe te voegen.
1. Selecteren **Downloaden**.
1. Correspondentiebeheer geeft het dialoogvenster Asset(s) downloaden weer met een lijst met elementen in de exportlijst.

   ![export](assets/export.png)

1. Om de gebiedsdelen te bekijken die worden uitgevoerd, uitgezocht los op. Of ga naar de volgende stap. Zelfs als u geen oplossing selecteert, worden de gebiedsdelen nog uitgevoerd.
1. Selecteer **OK**.
1. Correspondentiebeheer downloadt een .cmp-bestand naar de computer.

   Het .cmp- dossier omvat de uitgevoerde activa. U kunt het .cmp- dossier met anderen delen. Andere gebruikers kunnen het .cmp- dossier in een verschillende server invoeren om alle activa in de nieuwe server te krijgen.

### Alle Correspondentenbeheermiddelen als een pakket exporteren {#export-all-the-correspondence-management-assets-as-a-package}

Gebruik deze optie om alle Correspondence Management-elementen en gerelateerde afhankelijkheden als een pakket te downloaden van een AEM formulierexemplaar.

Als Correspondence Management bijvoorbeeld een brief heeft waarin een afbeelding en tekst worden gebruikt, bevat het gedownloade pakket ook de afbeelding en de tekst die betrekking hebben op de brief. Alle metagegevenseigenschappen (inclusief aangepaste eigenschappen) die aan het element zijn gekoppeld, worden ook gedownload. Nadat u het pakket (.cmp) hebt gedownload, kunt u [het pakket importeren naar een andere AEM Forms-instantie](../../forms/using/import-export-forms-templates.md#p-upload-forms-documents-assets-p).

Voer de volgende stappen uit om alle Correspondence Management-elementen en gerelateerde afhankelijkheden als een pakket te downloaden:

1. Meld u aan bij de AEM Forms-server als gebruiker van een formulier.
1. Selecteren **Adobe Experience Manager** in de algemene navigatiebalk.
1. Gereedschappen selecteren ( ![gereedschappen](assets/tools.png)) en selecteer vervolgens **Forms**.
1. Selecteren **Correspondentenbeheermiddelen exporteren**.

   ![publish-cmp-assets-1](assets/publish-cmp-assets-1.png)

   ( &quot;De pagina Alle correspondentiebeheermiddelen exporteren wordt weergegeven. Deze pagina bevat de informatie over de laatste keer dat het exportproces is gestart en een koppeling om het laatst geëxporteerde pakket te downloaden.

   ![export-last-run-details](assets/export-last-run-details.png)

1. Selecteren **Exporteren** en, in het bevestigingsbericht, selecteer **OK**.

   Nadat een batchproces is voltooid, worden de laatste uitvoergegevens en de koppeling om het pakket te downloaden bijgewerkt. Dit omvat informatie zoals de login van de Beheerder en als de partij met succes of ontbrak. De elementen worden geëxporteerd naar een pakket en de koppeling Exported Package downloaden wordt weergegeven.

   >[!NOTE]
   >
   >Het proces Alle elementen exporteren kan niet worden geannuleerd nadat het is gestart. Zorg er tijdens het exporteren van alle bewerkingen voor dat u geen elementen maakt, verwijdert, wijzigt of publiceert, en start het proces Alle elementen publiceren.a

1. Selecteer de **Geëxporteerd pakket downloaden** koppeling gebruiken om het pakketbestand te downloaden.

   Om de activa in het pakket aan een ander geval van Correspondence Management toe te voegen, [het pakket importeren naar een AEM Forms-instantie](../../forms/using/import-export-forms-templates.md#p-upload-forms-documents-assets-p).

### Documentfragmenten, letters en/of gegevenswoordenboeken importeren in Correspondentenbeheer {#import-document-fragments-letters-and-or-data-dictionaries-into-correspondence-management}

U kunt elementen importeren die naar een .cmp-bestand worden geëxporteerd. Een .cmp- dossier kan één of meerdere brieven, gegevenswoordenboeken, documentfragmenten, en afhankelijke activa hebben.

>[!NOTE]
>
>Meld u aan met een beheerdersaccount wanneer u oude Correspondence Management-middelen importeert voor migratie. Voor meer informatie over het migreren van oude Correspondentenbeheermiddelen, zie [Correspondentenbeheermiddelen migreren naar AEM 6.1-formulieren](/help/forms/using/migration-utility.md).

1. Selecteer op de pagina Gegevenswoordenboek, letters of documentfragmenten de optie **Maken > Bestand uploaden** en selecteer het .cmp- dossier.
1. In het dialoogvenster Elementen importeren wordt het dialoogvenster Correspondentiebeheer weergegeven met de lijst met geïmporteerde elementen. Selecteren **Importeren**.

   Na het importeren van de elementen worden de volgende eigenschappen van de elementen bijgewerkt, terwijl de andere eigenschappen ongewijzigd blijven:

   * Auteur: geeft de id weer van de gebruiker die het element naar de server heeft geïmporteerd
   * Gewijzigd: De tijd waarop het element naar de server is geïmporteerd

   >[!NOTE]
   >
   >Als u XDP&#39;s wilt uploaden (als onderdeel van het cmp-bestand of anderszins), moet u deel uitmaken van een gebruikersgroep voor formulieren. Neem contact op met de beheerder voor toegangsrechten.

## Een workflowtoepassing exporteren {#export-a-workflow-application}

U kunt AEM pakketbeheer gebruiken om workflowtoepassingen te exporteren. De procedure is als volgt:

1. Open AEM Forms-pakketbeheer. URL van pakketbeheer is https://&lt;server>:&lt;port>/crx/packmgr.
1. Klik op **[!UICONTROL Create Package]**. De **[!UICONTROL New Package]** wordt weergegeven.
1. Geef een naam, versie en groep voor het pakket op. Klik op **[!UICONTROL OK]**.
1. Klikken **[!UICONTROL Edit]** en opent u de **[!UICONTROL Filters]** tab. Klik op **[!UICONTROL Add Filter]**. Geef het pad van de workflowtoepassing op. Bijvoorbeeld /etc/fd/dashboard/startpoints/homemortgauge. Klik op **[!UICONTROL Add rule]**.

1. Open de **[!UICONTROL Advanced]** tab. Selecteren **[!UICONTROL Merge]** of **[!UICONTROL Overwrite]** in ACL Behandelend gebied. Klik op **[!UICONTROL Save]**.
1. Klikken **[!UICONTROL Build]** om het pakket te maken.

   Nadat het pakket is gemaakt, kunt u het pakket downloaden en naar de andere server importeren. De workflowtoepassing wordt weergegeven op de server waarop het pakket is geüpload.

   >[!NOTE]
   >
   >De workflowtoepassing werkt alleen naar behoren als u het bijbehorende adaptieve formulier- en workflowmodel exporteert met de werktoepassing.

## Mappen en elementen ordenen {#folders-and-organizing-assets}

De gebruikersinterface van AEM Forms gebruikt omslagen om activa te schikken. Deze mappen worden gebruikt voor het rangschikken van elementen die zijn gemaakt in de gebruikersinterface van AEM Forms. U kunt de naam van submappen wijzigen, submappen maken en elementen en documenten in deze mappen opslaan. Door documenten en elementen in een map te ordenen, kunt u de bestanden groeperen voor eenvoudig beheer. U kunt een map selecteren en deze downloaden of verwijderen.

Voer de volgende stappen uit om een map te maken:

### Een map maken {#create-a-folder}

1. Meld u aan bij de gebruikersinterface van AEM Forms op `https://<server>:<port>/aem/forms.html`.
1. Navigeer naar de locatie waaronder u een map wilt maken.
1. Selecteer Maken > Map.
1. Voer de volgende gegevens in:

   * **Titel:** Naam voor de map weergeven
   * **Naam:** *(Verplicht)* De knooppuntnaam waaronder u de map in de opslagplaats wilt opslaan

   >[!NOTE]
   >
   >Standaard wordt de waarde van het naamveld automatisch ingevuld vanuit de titel. De naam mag alleen alfanumerieke tekens bevatten of speciale tekens voor het koppelteken (-) en het onderstrepingsteken (_). Eventuele andere speciale tekens die in de titel worden ingevoerd, worden automatisch vervangen door een afbreekstreepje en u wordt gevraagd de nieuwe naam te bevestigen. U kunt doorgaan met de voorgestelde naam of deze verder bewerken.

1. Er wordt een nieuwe map met de door u gedefinieerde titel weergegeven op de huidige locatie in de lijst met elementen.

   Als een map met de opgegeven naam bestaat, mislukt het verzenden met een fout. U kunt het foutbericht weergeven door de muisaanwijzer op de fout te plaatsen ![aem6forms_error_alert](assets/aem6forms_error_alert.png) pictogram dat naast het naamveld wordt weergegeven.

   U kunt de nieuwe map selecteren en naar de map gaan en elementen of mappen in de map maken. Bovendien kunt u een map selecteren en ervoor kiezen deze in de wachtrij te plaatsen voor downloaden, te verwijderen of de naam ervan te bewerken.

   ![editdeletedownloadafolder](assets/editdeletedownloadafolder.png)

### Kopieën maken van een of meer elementen of letters {#create-copies-of-one-or-more-assets-or-letters}

Met bestaande elementen en letters kunt u snel elementen en letters maken met vergelijkbare eigenschappen, inhoud en overgeërfde elementen. U kunt gegevenswoordenboeken, documentfragmenten en letters kopiëren en plakken.

Voer de volgende stappen uit om kopieën van elementen en letters te maken:

1. Selecteer een of meer elementen/letters op de relevante pagina Elementen of Letters. In de gebruikersinterface wordt het pictogram Kopiëren weergegeven.
1. Selecteer Copy. In de gebruikersinterface wordt het pictogram Plakken weergegeven. U kunt er ook voor kiezen om in een map te navigeren voordat u gaat plakken. Verschillende mappen kunnen elementen met dezelfde naam bevatten. Zie voor meer informatie over mappen [Mappen en elementen ordenen](#folders-and-organizing-assets).
1. Selecteer Plakken. Het dialoogvenster Plakken wordt geopend. Het systeem genereert automatisch namen en titels voor de nieuwe kopieën van elementen/letters, maar u kunt de titels en namen van de elementen/letters bewerken.

   Als u de elementen/letters op dezelfde plaats kopieert en plakt, wordt het achtervoegsel &quot;-CopyXX&quot; toegevoegd aan de bestaande naam van het element/de letter. Als er geen titel voor het gekopieerde element/de gekopieerde letter bestond, blijft het automatisch gegenereerde titelveld leeg.

1. Bewerk indien nodig de titel en de naam waarmee u de kopie van het element/de letter wilt opslaan.
1. Selecteer Plakken. Er worden nieuwe kopieën van de gekopieerde elementen gemaakt.

## Zoeken {#search-forms}

Met de gebruikersinterface van AEM Forms kunt u zoeken in uw inhoud. Met de bovenste balk kunt u Zoeken selecteren **[A]** om uw inhoud te zoeken naar bronnen zoals elementen en documenten.

Wanneer u naar elementen zoekt, geeft AEM Forms het zijpaneel weer. U kunt ook ![assets-browser-content-only](assets/assets-browser-content-only.png) > Filter **[B]** om het zijpaneel aan te roepen. Met de verschillende filters in het zijpaneel kunt u de zoekopdracht beperken. In het zijpaneel kunt u ook uw zoekopdrachten opslaan.

![search_topbar](assets/search_topbar.png)

**A.** Zoeken **B.** Filter

![Zijpaneel - Filters](assets/search_sidepanel.png)

Zijpaneel - Filters

In het zijpaneel kunt u de volgende opties gebruiken om de zoekresultaten te beperken:

* Zoekdirectory
* Tags
* Zoekcriteria; bijvoorbeeld Gewijzigde datums, Publicatiestatus en LiveCopy-status.

In het zijpaneel kunt u ook uw zoekinstellingen opslaan met namen van uw keuze.

Ga voor meer informatie en instructies over het gebruik van zoekopdrachten, filters, opgeslagen zoekopdrachten en het zijpaneel naar [Zoeken](/help/sites-authoring/search.md).
