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
>* In AEM 6.4 Forms zijn de structuur en paden van de crx-repository veranderd. Als u elementen uit een vorige versie importeert naar AEM 6.4 Forms en het formulier afhankelijk is van de oudere structuur, moet u de afhankelijkheden handmatig exporteren. Voor details van veranderingen in de structuur en de wegen van de bewaarplaats, zie [ Herstructurering van de Bewaarplaats in AEM ](/help/sites-deploying/repository-restructuring.md).
>

## Forms- en documentmiddelen downloaden of uploaden {#download-or-upload-forms-amp-documents-assets}

Met de AEM Forms-gebruikersinterface kunt u elementen van een AEM instantie exporteren door deze als een AEM CRX-pakket of binaire bestanden te downloaden. U kunt het gedownloade AEM CRX-pakket of het binaire bestand vervolgens importeren in een andere AEM.

Exporteren en importeren via de gebruikersinterface van AEM Forms wordt ondersteund voor alle elementen, behalve voor adaptieve formuliersjablonen en beleid voor adaptieve formulierinhoud. Bij het exporteren van een adaptief formulier uit de gebruikersinterface van AEM Forms worden de gerelateerde aangepaste formuliersjabloon en het inhoudsbeleid daarom niet automatisch geëxporteerd als andere gerelateerde elementen.

Voor deze elementtypen moet u AEM Package Manager gebruiken om een CRX-pakket te maken op de bron- AEM server en het pakket op de doelserver te installeren. Voor informatie over het creëren van en het installeren van pakketten, zie [ Werkend met pakketten ](/help/sites-administering/package-manager.md).

### Forms- en Documenten downloaden {#download-forms-amp-documents-assets}

Forms en Documenten downloaden:

1. Meld u aan bij de AEM Forms-instantie.
1. Selecteer Experience Manager ![ adobeexperienceManager ](assets/adobeexperiencemanager.png) pictogram > navigatie ![ kompas ](assets/compass.png) pictogram> Forms > Forms &amp; Documenten.
1. Selecteer de vormactiva en selecteer het **pictogram van de Download**.
1. In de Activa(s) van de Download, kies één van de volgende opties, en selecteer **Download**.

   * **Download als Pakket van CRX:** gebruik de optie om alle geselecteerde activa en verwante gebiedsdelen van een instantie van AEM Forms aan een andere te downloaden en te bewegen. Alle elementen en mappen worden als crx-pakket gedownload. Alle formulierelementen, zoals de formulieren die zijn geschreven in AEM (adaptieve formulieren, interactieve communicatie en adaptieve formulierfragmenten), formuliersets, formuliersjablonen, PDF-documenten en bronnen (XSD&#39;s, XFS, afbeeldingen) kunnen als pakket worden gedownload vanuit de gebruikersinterface van AEM Forms.
Het voordeel van het downloaden van elementen als pakket is dat ook elementen worden gedownload die door het geselecteerde element zijn gebruikt om te downloaden. Als u bijvoorbeeld een adaptief formulier hebt waarin een formuliersjabloon, XSD en een afbeelding worden gebruikt. Wanneer u dit adaptieve formulier selecteert en het als pakket downloadt, bevat het gedownloade pakket ook de formuliersjabloon, XSD en de afbeelding. Alle metagegevenseigenschappen (inclusief aangepaste eigenschappen) die aan het element zijn gekoppeld, worden ook gedownload.

   * **de activa van de Download (s) als binaire dossiers:** gebruik de optie om slechts vormmalplaatjes (XDP), PDF forms (PDF), document (PDF), en middelen (beelden, schema&#39;s, stijlheets) te downloaden. U kunt deze elementen bewerken met externe toepassingen. De formulierbestanden met binaire bestanden, zoals XSD&#39;s, XDP&#39;s, afbeeldingen, PDF en XDP&#39;s, worden gedownload als ZIP-bestand.
U kunt geen adaptieve vormen, Interactieve Mededelingen, adaptieve vormfragmenten, thema&#39;s, en vormreeksen met **Download activa(s) als binaire dossiers** optie downloaden. Om deze activa te downloaden, zou u **Download als het Pakket van CRX** optie moeten gebruiken.

   De geselecteerde elementen worden gedownload als een archief (.zip-bestand).

   >[!NOTE]
   >
   >Zowel AEM pakket- als binaire bestanden worden gedownload als een archief (.zip-bestand). De sjablonen voor de elementen worden niet samen met de elementen gedownload. U moet de elementsjablonen afzonderlijk exporteren.

### Forms- en documentmiddelen uploaden {#upload-forms-amp-documents-assets}

Forms en Documenten uploaden:

<!--[!VIDEO](https://vimeo.com/)-->

1. Meld u aan bij de AEM Forms-instantie.
1. Selecteer Experience Manager ![ adobeexperienceManager ](assets/adobeexperiencemanager.png) pictogram > navigatie ![ kompas ](assets/compass.png) pictogram> Forms> Forms &amp; Documenten.
1. Selecteer **creëren** > **Dossier uploadt**. Er wordt een dialoogvenster voor het uploaden of verpakken weergegeven.
1. Blader in het dialoogvenster naar het pakket of het archief dat u wilt importeren en selecteer dit. U kunt ook PDF-documenten, XSD&#39;s, afbeeldingen, stijlpagina&#39;s en XDP-formulieren selecteren. Selecteer **Open**. De map of de bestandsnaam die u selecteert, mag geen speciale tekens bevatten.

   Voor de dialoogdoos, verifieer de details van activa die worden geupload, en selecteer **uploaden**.

   Als u een bestaand formulierelement uploadt, wordt het element bijgewerkt.

   >[!NOTE]
   >
   >Het uploaden van een pakket vervangt de bestaande maphiërarchie niet. Als u bijvoorbeeld een adaptief formulier hebt met de naam &#39;Training&#39; op de locatie /content/dam/formsanddocuments op één server. U downloadt het adaptieve formulier en uploadt het formulier naar een andere server. De tweede server heeft ook een map met de naam &#39;Training&#39; op dezelfde locatie/content/dam/formsanddocuments. Het uploaden mislukt.

## Een thema downloaden of uploaden {#downloading-or-uploading-a-theme}

Met AEM Forms kunt u thema&#39;s maken, downloaden of uploaden. Net als andere elementen, zoals formulieren, documenten en letters, wordt een thema gemaakt. U kunt een thema maken, dit downloaden en uploaden naar een aparte versie om het opnieuw te gebruiken. Voor meer informatie over thema&#39;s, zie [ Thema&#39;s in AEM Forms ](../../forms/using/themes.md).

### Een thema downloaden {#downloading-a-theme}

U kunt thema&#39;s in AEM Forms exporteren die u kunt gebruiken in andere projecten of instanties. AEM kunt u thema downloaden als een ZIP-bestand dat u kunt uploaden op het exemplaar.

Een thema downloaden:

1. Meld u aan bij de AEM Forms-instantie.
1. Selecteer Experience Manager ![ adobeexperienceManager ](assets/adobeexperiencemanager.png) pictogram > navigatie ![ kompas ](assets/compass.png) pictogram> Forms> Thema&#39;s.
1. Selecteer het thema en selecteer **Download**. Het thema wordt gedownload als een archief (.zip-bestand).

### Een thema uploaden {#uploading-a-theme}

U kunt gemaakte thema&#39;s gebruiken met voorinstellingen voor stijlen voor uw project. U kunt themapakketten die anderen maken, importeren door deze te uploaden naar uw project.

Een thema uploaden:

1. In Experience Manager, navigeer aan **Forms > Thema&#39;s**.
1. In de pagina van Thema&#39;s, klik **creëren > Dossier uploadt**.
1. In het Dossier uploadt herinnering, doorblader en selecteer een themapakket op uw computer en klik **uploadt**.
Het geüploade thema is beschikbaar op de themapagina.

1. Meld u aan bij de AEM Forms-instantie.
1. Selecteer Experience Manager ![ adobeexperienceManager ](assets/adobeexperiencemanager.png) pictogram > navigatie ![ kompas ](assets/compass.png) pictogram> Forms> Thema&#39;s.
1. Klik **creëren** > **Dossier uploadt**. In het Dossier uploadt herinnering, doorblader en selecteer een themapakket op uw computer en klik **uploadt**. Het thema wordt geüpload.

## Importeren en exporteren van activa in Correspondentenbeheer {#import-and-export-assets-in-correspondence-management}

Als u elementen, zoals gegevenswoordenboeken, letters en documentfragmenten, wilt delen tussen twee verschillende implementaties van Correspondence Management, kunt u .cmp-bestanden maken en delen. Een .cmp-bestand kan een of meer gegevenswoordenboeken, letters, documentfragmenten en formulieren bevatten.

### Documentfragmenten, letters en/of gegevenswoordenboeken exporteren {#export-document-fragments-letters-and-or-data-dictionaries}

1. In de brieven, documentfragmenten, of de pagina&#39;s van het gegevenswoordenboek, selecteer en selecteer de activa u naar één enkel pakket wilt uitvoeren, en dan Rij voor Download selecteren. De elementen zijn in een voor export geschikte indeling geplaatst.
1. Herhaal indien nodig de bovenstaande stap om letters, documentfragmenten en gegevenswoordenboeken toe te voegen.
1. Selecteer **Download**.
1. Correspondentiebeheer geeft het dialoogvenster Asset(s) downloaden weer met een lijst met elementen in de exportlijst.

   ![ uitvoer ](assets/export.png)

1. Om de gebiedsdelen te bekijken die worden uitgevoerd, uitgezocht los op. Of ga naar de volgende stap. Zelfs als u geen oplossing selecteert, worden de gebiedsdelen nog uitgevoerd.
1. Om het .cmp- dossier te downloaden, uitgezochte **O.K.**.
1. Correspondentiebeheer downloadt een .cmp-bestand naar de computer.

   Het .cmp- dossier omvat de uitgevoerde activa. U kunt het .cmp- dossier met anderen delen. Andere gebruikers kunnen het .cmp- dossier in een verschillende server invoeren om alle activa in de nieuwe server te krijgen.

### Alle Correspondentenbeheermiddelen als een pakket exporteren {#export-all-the-correspondence-management-assets-as-a-package}

Gebruik deze optie om alle Correspondence Management-elementen en gerelateerde afhankelijkheden als een pakket te downloaden van een AEM formulierexemplaar.

Als Correspondence Management bijvoorbeeld een brief heeft waarin een afbeelding en tekst worden gebruikt, bevat het gedownloade pakket ook de afbeelding en de tekst die betrekking hebben op de brief. Alle metagegevenseigenschappen (inclusief aangepaste eigenschappen) die aan het element zijn gekoppeld, worden ook gedownload. Zodra u het pakket (.cmp) hebt gedownload, kunt u [ het pakket in een verschillende instantie van AEM Forms invoeren ](../../forms/using/import-export-forms-templates.md#p-upload-forms-documents-assets-p).

Voer de volgende stappen uit om alle Correspondence Management-elementen en gerelateerde afhankelijkheden als een pakket te downloaden:

1. Meld u aan bij de AEM Forms-server als gebruiker van een formulier.
1. Selecteer **Adobe Experience Manager** in de Globale bar van de Navigatie.
1. Selecteer hulpmiddelen ( ![ hulpmiddelen ](assets/tools.png)) en selecteer dan **Forms**.
1. Selecteer **het Beheer Assets van de Correspondentie van de Uitvoer**.

   ![ publiceren-cmp-activa-1 ](assets/publish-cmp-assets-1.png)

   ( &quot;De pagina Exporteren naar alle correspondentiebeheerpagina van Assets wordt weergegeven. Deze pagina bevat de informatie over de laatste keer dat het exportproces is gestart en een koppeling om het laatst geëxporteerde pakket te downloaden.

   ![ export-last-looppas-details ](assets/export-last-run-details.png)

1. Selecteer **Uitvoer** en, in het bevestig bericht, uitgezochte **O.K.**.

   Nadat een batchproces is voltooid, worden de laatste uitvoergegevens en de koppeling om het pakket te downloaden bijgewerkt. Dit omvat informatie zoals de login van de Beheerder en als de partij met succes of ontbrak. De elementen worden geëxporteerd naar een pakket en de koppeling Exported Package downloaden wordt weergegeven.

   >[!NOTE]
   >
   >Het exportproces voor alle Assets-bestanden kan niet worden geannuleerd nadat het is gestart. Zorg er tijdens het exporteren van alle bewerkingen voor dat u geen elementen maakt, verwijdert, wijzigt of publiceert, en start Publish All Assets process.a

1. Selecteer de **Uitgevoerde Verbinding van het Pakket van de Download** om het pakketdossier te downloaden.

   Om de activa in het pakket aan een andere instantie van het Beheer van de Correspondentie toe te voegen, [ voer het pakket in een instantie van AEM Forms ](../../forms/using/import-export-forms-templates.md#p-upload-forms-documents-assets-p) in.

### Documentfragmenten, letters en/of gegevenswoordenboeken importeren in Correspondentenbeheer {#import-document-fragments-letters-and-or-data-dictionaries-into-correspondence-management}

U kunt elementen importeren die naar een .cmp-bestand worden geëxporteerd. Een .cmp- dossier kan één of meerdere brieven, gegevenswoordenboeken, documentfragmenten, en afhankelijke activa hebben.

>[!NOTE]
>
>Meld u aan met een beheerdersaccount wanneer u oude Correspondence Management-middelen importeert voor migratie. Voor meer informatie over het Migreren van oude activa van het Beheer van de Correspondentie, zie [ de activa van het Beheer van de Correspondentie aan AEM 6.1 vormen ](/help/forms/using/migration-utility.md) migreren.

1. Voor het gegevenswoordenboek, de brieven, of de pagina van documentfragmenten, uitgezochte **leidt tot > het Dossier uploadt** en selecteert het .cmp- dossier.
1. Het Correspondentiebeheer geeft het dialoogvenster Assets importeren weer met de lijst met geïmporteerde elementen. Selecteer **Invoer**.

   Na het importeren van de elementen worden de volgende eigenschappen van de elementen bijgewerkt, terwijl de andere eigenschappen ongewijzigd blijven:

   * Auteur: geeft de id weer van de gebruiker die het element naar de server heeft geïmporteerd
   * Gewijzigd: De tijd waarop het element naar de server is geïmporteerd

   >[!NOTE]
   >
   >Als u XDP&#39;s wilt uploaden (als onderdeel van het cmp-bestand of anderszins), moet u deel uitmaken van een gebruikersgroep voor formulieren. Neem contact op met de beheerder voor toegangsrechten.

## Een workflowtoepassing exporteren {#export-a-workflow-application}

U kunt AEM pakketbeheer gebruiken om workflowtoepassingen te exporteren. De procedure is als volgt:

1. Open AEM Forms-pakketbeheer. URL van pakketbeheer is https://&lt;server>:&lt;port>/crx/packmgr.
1. Klik op **[!UICONTROL Create Package]**. Het dialoogvenster **[!UICONTROL New Package]** wordt weergegeven.
1. Geef een naam, versie en groep voor het pakket op. Klik op **[!UICONTROL OK]**.
1. Klik op **[!UICONTROL Edit]** en open het tabblad **[!UICONTROL Filters]** . Klik op **[!UICONTROL Add Filter]**. Geef het pad van de workflowtoepassing op. Bijvoorbeeld /etc/fd/dashboard/startpoints/homemortgauge. Klik op **[!UICONTROL Add rule]**.

1. Open de tab **[!UICONTROL Advanced]** . Selecteer **[!UICONTROL Merge]** of **[!UICONTROL Overwrite]** in het veld ACL-verwerking. Klik op **[!UICONTROL Save]**.
1. Klik op **[!UICONTROL Build]** om het pakket te maken.

   Nadat het pakket is gemaakt, kunt u het pakket downloaden en naar de andere server importeren. De workflowtoepassing wordt weergegeven op de server waarop het pakket is geüpload.

   >[!NOTE]
   >
   >De workflowtoepassing werkt alleen naar behoren als u het bijbehorende adaptieve formulier- en workflowmodel exporteert met de werktoepassing.

## Mappen en elementen ordenen {#folders-and-organizing-assets}

De gebruikersinterface van AEM Forms gebruikt omslagen om activa te schikken. Deze mappen worden gebruikt voor het rangschikken van elementen die zijn gemaakt in de gebruikersinterface van AEM Forms. U kunt de naam van submappen wijzigen, submappen maken en elementen en documenten in deze mappen opslaan. Door documenten en elementen in een map te ordenen, kunt u de bestanden groeperen voor eenvoudig beheer. U kunt een map selecteren en deze downloaden of verwijderen.

Voer de volgende stappen uit om een map te maken:

### Een map maken {#create-a-folder}

1. Meld u aan bij de gebruikersinterface van AEM Forms op `https://<server>:<port>/aem/forms.html` .
1. Navigeer naar de locatie waaronder u een map wilt maken.
1. Selecteer Maken > Map.
1. Voer de volgende gegevens in:

   * **Titel:** de naam van de vertoning voor de omslag
   * **Naam:** *(Verplicht)* De knoopnaam waaronder u de omslag in de bewaarplaats wilt opslaan

   >[!NOTE]
   >
   >Standaard wordt de waarde van het naamveld automatisch ingevuld vanuit de titel. De naam mag alleen alfanumerieke tekens bevatten of speciale tekens voor het koppelteken (-) en het onderstrepingsteken (_). Eventuele andere speciale tekens die in de titel worden ingevoerd, worden automatisch vervangen door een afbreekstreepje en u wordt gevraagd de nieuwe naam te bevestigen. U kunt doorgaan met de voorgestelde naam of deze verder bewerken.

1. Er wordt een nieuwe map met de door u gedefinieerde titel weergegeven op de huidige locatie in de lijst met elementen.

   Als een map met de opgegeven naam bestaat, mislukt het verzenden met een fout. U kunt het foutenbericht bekijken door over het fout ![ aem6forms_error_alert ](assets/aem6forms_error_alert.png) pictogram te bewegen dat naast het naamgebied verschijnt.

   U kunt de nieuwe map selecteren en naar de map gaan en elementen of mappen in de map maken. Bovendien kunt u een map selecteren en ervoor kiezen deze in de wachtrij te plaatsen voor downloaden, te verwijderen of de naam ervan te bewerken.

   ![ editdeletedownloadafolder ](assets/editdeletedownloadafolder.png)

### Kopieën maken van een of meer elementen of letters {#create-copies-of-one-or-more-assets-or-letters}

Met bestaande elementen en letters kunt u snel elementen en letters maken met vergelijkbare eigenschappen, inhoud en overgeërfde elementen. U kunt gegevenswoordenboeken, documentfragmenten en letters kopiëren en plakken.

Voer de volgende stappen uit om kopieën van elementen en letters te maken:

1. Selecteer een of meer elementen/letters op de betreffende pagina Assets of Letters. In de gebruikersinterface wordt het pictogram Kopiëren weergegeven.
1. Selecteer Copy. In de gebruikersinterface wordt het pictogram Plakken weergegeven. U kunt er ook voor kiezen om in een map te navigeren voordat u gaat plakken. Verschillende mappen kunnen elementen met dezelfde naam bevatten. Voor meer informatie over omslagen, zie [ Omslagen en het organiseren van activa ](#folders-and-organizing-assets).
1. Selecteer Plakken. Het dialoogvenster Plakken wordt geopend. Het systeem genereert automatisch namen en titels voor de nieuwe kopieën van elementen/letters, maar u kunt de titels en namen van de elementen/letters bewerken.

   Als u de elementen/letters op dezelfde plaats kopieert en plakt, wordt het achtervoegsel &quot;-CopyXX&quot; toegevoegd aan de bestaande naam van het element/de letter. Als er geen titel voor het gekopieerde element/de gekopieerde letter bestond, blijft het automatisch gegenereerde titelveld leeg.

1. Bewerk indien nodig de titel en de naam waarmee u de kopie van het element/de letter wilt opslaan.
1. Selecteer Plakken. Er worden nieuwe kopieën van de gekopieerde elementen gemaakt.

## Zoeken {#search-forms}

Met de gebruikersinterface van AEM Forms kunt u zoeken in uw inhoud. Gebruikend de hoogste bar, kunt u Onderzoek **[A]** selecteren om uw inhoud naar middelen zoals activa en documenten te zoeken.

Wanneer u naar elementen zoekt, geeft AEM Forms het zijpaneel weer. U kunt ook selecteren ![ activa-browser-inhoud-slechts ](assets/assets-browser-content-only.png) > filter **[B]** om het zijpaneel aan te halen. Met de verschillende filters in het zijpaneel kunt u de zoekopdracht beperken. In het zijpaneel kunt u ook uw zoekopdrachten opslaan.

![ search_topbar ](assets/search_topbar.png)

**A.** Onderzoek **B.** Filter

![ Kant paneel - Filters ](assets/search_sidepanel.png)

Zijpaneel - Filters

In het zijpaneel kunt u de volgende opties gebruiken om de zoekresultaten te beperken:

* Zoekdirectory
* Tags
* Zoekcriteria; bijvoorbeeld Gewijzigde datums, Publish-status, LiveCopy-status.

In het zijpaneel kunt u ook uw zoekinstellingen opslaan met namen van uw keuze.

Voor meer informatie en instructies bij het gebruiken van onderzoek, filters, bewaard onderzoek, en zijpaneel, zie [ Onderzoek ](/help/sites-authoring/search.md).
