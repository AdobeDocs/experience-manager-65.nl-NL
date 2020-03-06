---
title: Het invoeren van en het uitvoeren van activa naar de Vormen van AEM
seo-title: Het invoeren van en het uitvoeren van activa naar de Vormen van AEM
description: U kunt adaptieve formulieren en sjablonen importeren en exporteren vanuit en naar AEM-instanties. Dit helpt bij het migreren van vormen of het verplaatsen ervan over systemen.
seo-description: U kunt adaptieve formulieren en sjablonen importeren en exporteren vanuit en naar AEM-instanties. Dit helpt bij het migreren van vormen of het verplaatsen ervan over systemen.
uuid: 937daedd-56f3-4e02-b695-b194b494d9bf
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: forms-manager
discoiquuid: 69210727-dde3-495a-87b7-2e8173e6b664
docset: aem65
translation-type: tm+mt
source-git-commit: 5035c9630b5e861f4386e1b5ab4f4ae7a8d26149

---


# Het invoeren van en het uitvoeren van activa naar de Vormen van AEM{#importing-and-exporting-assets-to-aem-forms}

U kunt vormen en verwante activa, thema&#39;s, gegevenswoordenboeken, documentfragmenten, en brieven tussen verschillende instanties van Vormen bewegen AEM. Een dergelijke beweging is vereist wanneer het migreren van systemen of het bewegen van vormen van een stadiumserver aan een productieserver. Voor die activa waarvoor upload en de invoer via de Vormen UI van AEM wordt gesteund, is het gebruiken van de Vormen UI de geadviseerde manier voor de uitvoer of de invoer. Het gebruik van AEM Package Manager voor het exporteren of importeren van dergelijke bedrijfsmiddelen wordt niet aanbevolen.

>[!NOTE]
>
>* In AEM 6.4 vormen, zijn de structuur en de wegen van crx-bewaarplaats veranderd. Als u activa van een vorige versie aan Vormen AEM 6.4 invoert en de vorm sommige gebiedsdelen op de oudere structuur heeft, moet u de gebiedsdelen manueel uitvoeren. Zie voor meer informatie over wijzigingen in de structuur en de paden van de opslagplaats de [Repository Restructuring in AEM](/help/sites-deploying/repository-restructuring.md).
>



## Download of upload de Vormen &amp; de activa van Documenten {#download-or-upload-forms-amp-documents-assets}

Het gebruikersinterface van de Vormen AEM staat u toe om activa van een instantie uit te voeren AEM door hen te downloaden als CRX-Pakket AEM of binaire dossiers. U kunt het gedownloade AEM CRX-pakket of het binaire dossier in een andere instantie dan invoeren AEM.

De uitvoer en de invoer via AEM vormt gebruikersinterface wordt gesteund voor alle activa behalve de Aanpassings malplaatjes van de Vorm en het Aanpassings de inhoudsbeleid van de Vorm. Daarom bij het uitvoeren van een adaptieve vorm van de Vormen UI van AEM, worden het verwante adaptieve vormmalplaatje en inhoudsbeleid niet automatisch uitgevoerd zoals andere verwante activa.

Voor deze activatypes, moet u de Manager van het Pakket van AEM gebruiken om een CRX pakket op de bronAEM server tot stand te brengen en het pakket op de bestemmingsserver te installeren. Voor informatie over het creëren van en het installeren van pakketten, zie het [Werken met pakketten](/help/sites-administering/package-manager.md).

### Vormen en documenten downloaden {#download-forms-amp-documents-assets}

Om Vormen &amp; de activa van Documenten te downloaden:

1. Login aan de instantie van Vormen AEM.
1. Het pictogram van de Manager van de Ervaring van het lusje ![adobeexperience](assets/adobeexperiencemanager.png) > navigatie ![compass](assets/compass.png) pictogram> Vormen > Vormen &amp; Documenten.
1. Selecteer de vormenactiva en tik het pictogram van de **Download** .
1. Kies in de downloadmiddelen een van de volgende opties en tik op **Downloaden**.

   * **Download als CRX-pakket:** Gebruik de optie om alle geselecteerde bedrijfsmiddelen en bijbehorende afhankelijkheden te downloaden en te verplaatsen van een AEM-instantie Formulieren naar een andere. Het downloadt alle activa en omslagen als crx pakket. Om het even welke vormactiva met inbegrip van de vormen authored in AEM (adaptieve vormen, Interactieve Mededelingen, en adaptieve vormfragmenten), vormreeksen, vormmalplaatjes, Pdf- documenten, en middelen (XSDs, XFS, beelden) kunnen als pakket van Vormen UI worden gedownload AEM.
Het voordeel van het downloaden van activa als pakket is dat het ook activa downloadt die door de activa zijn gebruikt die aan download worden geselecteerd. Bijvoorbeeld, als u een adaptieve vorm hebt die een vormmalplaatje, XSD, en een beeld gebruikt. Wanneer u dit adaptieve formulier selecteert en het als pakket downloadt, bevat het gedownloade pakket ook het formuliersjabloon XSD en de afbeelding. Alle meta-gegevenseigenschappen (met inbegrip van douaneeigenschappen) verbonden aan de activa worden ook gedownload.

   * **Activa downloaden als binaire bestanden:** Gebruik de optie om slechts vormmalplaatjes (XDP), vormen PDF (PDF), document (PDF), en middelen (beelden, schema&#39;s, stylesheets) te downloaden. U kunt deze activa met externe toepassingen uitgeven. Het downloadt de vormenactiva die binaire getallen, zoals XSDs, XDPs, beelden, PDFs, en XDPs als .zip dossier hebben.
U kunt geen adaptieve vormen, Interactieve Mededelingen, adaptieve vormfragmenten, thema&#39;s, en vormreeksen met de activa van de **Download downloaden als binaire dossieroptie** downloaden. Om deze activa te downloaden, zou u **Download als optie van het Pakket** van CRX moeten gebruiken.
   De geselecteerde elementen worden gedownload als een archief (.zip-bestand).

   >[!NOTE]
   >
   >Zowel het pakket van AEM als de binaire dossiers worden gedownload als archief (.zip- dossier). De malplaatjes voor de activa worden niet gedownload samen met de activa. U moet de activamalplaatjes afzonderlijk uitvoeren.

### Vormen en documenten uploaden {#upload-forms-amp-documents-assets}

Om Vormen &amp; de activa van Documenten te uploaden:

>[!VIDEO](https://vimeo.com/)

1. Login aan de instantie van Vormen AEM.
1. Het pictogram van de Manager van de Ervaring van het lusje ![adobeexperience](assets/adobeexperiencemanager.png) > van de navigatie ![kompas](assets/compass.png) pictogram> Vormen> Vormen &amp; Documenten.
1. Tik **maken** >**Bestand uploaden**. Upload formulieren of het dialoogvenster Pakket.
1. In de dialoogdoos, doorblader en selecteer het pakket of het archief aan de invoer. U kunt Pdf- document, XSDs, beelden, stylesheets, en vormen ook selecteren XDP. Tik **open**. De omslag of het dossier - de naam die uitgezocht u moet geen speciale karakters omvatten.

   Voor de dialoogdoos, verifieer de details van activa die worden geupload, en de kraan **uploadt**.

   In het geval, uploadt u een bestaande vormenactiva, wordt de activa bijgewerkt.

   >[!NOTE]
   >
   >Het uploaden van een pakket vervangt geen bestaande omslaghiërarchie. Bijvoorbeeld, als u een adaptieve vorm genoemd &quot;Opleiding&quot;bij plaats /content/dam/formsanddocuments op één server hebt. U downloadt het adaptieve formulier en uploadt het formulier op een andere server. De tweede server heeft ook een omslag met naam &quot;Opleiding&quot;bij de zelfde plaats /content/dam/formsanddocuments. Uploaden mislukt.

## Een thema downloaden of uploaden {#downloading-or-uploading-a-theme}

Met Vormen AEM, kunt u, thema&#39;s tot stand brengen downloaden of uploaden. Een thema wordt gecreeerd zoals andere activa zoals vormen, documenten, en brieven. U kunt een thema tot stand brengen, het downloaden, en het uploaden op een afzonderlijke instantie om het opnieuw te gebruiken. Voor meer informatie over thema&#39;s, zie [Thema&#39;s in Vormen](../../forms/using/themes.md)AEM.

### Een thema downloaden {#downloading-a-theme}

U kunt thema&#39;s in Vormen uitvoeren AEM die u in andere projecten of instanties kunt gebruiken. Met AEM kunt u thema downloaden als zip-bestand, dat u op de instantie kunt uploaden.

Om een thema te downloaden:

1. Login aan de instantie van Vormen AEM.
1. Het pictogram van de Manager van de Ervaring van de ![adobeexperience](assets/adobeexperiencemanager.png) > van de navigatie ![kompas](assets/compass.png) pictogram> Vormen> Thema&#39;s.
1. Selecteer het thema en tik op **Download**. Het thema wordt gedownload als archief (.zip dossier).

### Een thema uploaden {#uploading-a-theme}

U kunt gecreeerde thema&#39;s met het stileren gebruiken vooraf instelt op uw project. U kunt themapakketten invoeren die anderen door hen op uw project te uploaden creëren.

Om een thema te uploaden:

1. In de Manager van de Ervaring, navigeer aan **Vormen > Thema**.
1. In de pagina van Thema&#39;s, leidt de klik **tot > Dossier uploadt**.
1. In het Dossier upload snel, doorblader en selecteer een themapakket op uw computer en de klik **uploadt**.
Het geüploade thema is beschikbaar in de themapagina.

1. Login aan de instantie van Vormen AEM.
1. Het pictogram van de Manager van de Ervaring van de ![adobeexperience](assets/adobeexperiencemanager.png) > van de navigatie ![kompas](assets/compass.png) pictogram> Vormen> Thema&#39;s.
1. Klik **creëren** > **Dossier uploaden**. In het Dossier upload snel, doorblader en selecteer een themapakket op uw computer en de klik **uploadt**. Het thema wordt geüpload.

## In- en uitvoeractiva in correspondentiebeheer {#import-and-export-assets-in-correspondence-management}

Om activa, zoals gegevenswoordenboeken, brieven, en documentfragmenten, tussen twee verschillende implementaties van het Beheer van de Correspondentie te delen, kunt u .cmp- dossiers tot stand brengen en delen. Een .cmp- dossier kan één of meerdere gegevenswoordenboeken, brieven, documentfragmenten, en vormen omvatten.

### De Fragmenten van het Document van de uitvoer, Brieven, en/of de Woordenboeken van Gegevens {#export-document-fragments-letters-and-or-data-dictionaries}

1. In de brieven, documentfragmenten, of de pagina&#39;s van het gegevenswoordenboek, tik en selecteer de activa u naar één enkel pakket wilt uitvoeren, en dan Rij voor Download tikken. De activa zijn in de rij voor de uitvoer.
1. Zoals vereist, herhaal de bovengenoemde stap om brieven, documentfragmenten, en gegevenswoordenboeken toe te voegen.
1. Tik op **Downloaden**.
1. Correspondentiebeheer toont een dialoog over de downloadmiddelen met een lijst van activa in de exportlijst.

   ![exporteren](assets/export.png)

1. Om de gebiedsdelen te bekijken die worden uitgevoerd, lost het Lusje op. Of ga naar de volgende stap. Zelfs als u niet tikt lost op, worden de gebiedsdelen nog uitgevoerd.
1. Om het .cmp- dossier te downloaden, **O.K**. te tikken.
1. Het Beheer van de correspondentie downloadt een .cmp- dossier aan uw computer.

   Het .cmp- dossier omvat de uitgevoerde activa. U kunt het .cmp- dossier met anderen delen. Andere gebruikers kunnen het .cmp- dossier in een verschillende server invoeren om alle activa in de nieuwe server te krijgen.

### Alle activa van het Beheer van de Correspondentie als pakket uitvoeren {#export-all-the-correspondence-management-assets-as-a-package}

Gebruik deze optie om alle activa van het Beheer van de Correspondentie en verwante gebiedsdelen als pakket van een AEM vormeninstantie te downloaden.

Bijvoorbeeld, als het Beheer van de Correspondentie een brief heeft die een beeld en een tekst gebruikt, bevat het gedownloade pakket ook het beeld en de tekst met betrekking tot de brief. Alle meta-gegevenseigenschappen (met inbegrip van douaneeigenschappen) verbonden aan de activa worden ook gedownload. Zodra u het pakket (.cmp) hebt gedownload, kunt u het pakket in een verschillende instantie [van Vormen](../../forms/using/import-export-forms-templates.md#p-upload-forms-documents-assets-p)invoeren AEM.

Om alle activa van het Beheer van de Correspondentie en verwante gebiedsdelen als pakket te downloaden, voltooi de volgende stappen:

1. Login aan de server van Vormen AEM als vormengebruiker.
1. De Manager **van de Ervaring van** Adobe van het lusje in de Globale bar van de Navigatie.
1. De hulpmiddelen van het tikje ( ![hulpmiddelen](assets/tools.png)) en toen de **Vormen** van de kraan.
1. Tik op **Correspondentiebeheermiddelen** exporteren.

   ![publiceren-cmp-activa-1](assets/publish-cmp-assets-1.png)

   ( &quot;De Uitvoer Al pagina van de Activa van het Beheer van de Correspondentie verschijnt en toont de informatie over de laatste keer het proces van de Uitvoer werd geprobeerd en een verbinding om het laatste met succes uitgevoerde pakket te downloaden.

   ![details over de laatste uitvoering van de export](assets/export-last-run-details.png)

1. Tik op **Exporteren** en tik in het bevestigingsbericht op **OK**.

   Nadat een partijproces volledig is, worden de laatste looppasdetails en de verbinding om het pakket te downloaden bijgewerkt. Dit omvat informatie zoals login van de Beheerder en als de partijlooppas met succes of ontbrak. De activa worden uitgevoerd naar een pakket en de Download Uitgevoerde verbinding van het Pakket verschijnt.

   >[!NOTE]
   >
   >Het proces van alle activa exporteren kan niet worden geannuleerd zodra het is gestart. Ook, terwijl de uitvoer al verrichting in proces is, creeer, schrap niet, wijzig of publiceer geen activa of stel in werking publiceren Al Activa proces.a in werking

1. Tik op de link **Downloaden geëxporteerd pakket** om het pakketbestand te downloaden.

   Om de activa in het pakket aan een andere instantie van het Beheer van de Correspondentie toe te voegen, [voer het pakket in een instantie](../../forms/using/import-export-forms-templates.md#p-upload-forms-documents-assets-p)van Vormen AEM in.

### Documentfragmenten, letters en/of gegevenswoordenboeken importeren in Correspondentiebeheer {#import-document-fragments-letters-and-or-data-dictionaries-into-correspondence-management}

U kunt activa invoeren die in een .cmp- dossier worden uitgevoerd. Een .cmp- dossier kan één of meerdere brieven, gegevenswoordenboeken, documentfragmenten, en afhankelijke activa hebben.

>[!NOTE]
>
>Terwijl het invoeren van de oude activa van het Beheer van de Correspondentie voor migratie, login gebruikend een rekening Admin. Voor meer informatie over het Migreren van de oude activa van het Beheer van de Correspondentie, zie de activa van het Beheer van de Correspondentie [migreren aan AEM 6.1 vormen](/help/forms/using/migration-utility.md).

1. Voor het gegevenswoordenboek, de brieven, of de pagina van documentfragmenten, **leiden de Tik tot > Dossier uploadt** en selecteert het .cmp dossier.
1. Het Beheer van de correspondentie toont de dialoog van de Activa van de Invoer met de lijst van activa die worden ingevoerd. Tik op **importeren**.

   Na het invoeren van de activa, worden de volgende eigenschappen van de activa bijgewerkt terwijl de andere eigenschappen het zelfde blijven:

   * Auteur: Toont identiteitskaart van de gebruiker die de activa aan de server invoerde
   * Gewijzigd: De tijd toen de activa in de server werden ingevoerd
   >[!NOTE]
   >
   >Voor u om XDPs (als deel van het cmp- dossier of anders) te kunnen uploaden, moet u een deel van vorm-macht-gebruikersgroep zijn. Voor toegangsrechten, contacteer de beheerder.

## Een werkstroomtoepassing exporteren {#export-a-workflow-application}

U kunt AEM pakketmanager gebruiken om werkschematoepassingen uit te voeren. De procedure is als volgt:

1. Open AEM Formuliermanager. URL van pakketmanager is https://&lt;server>:&lt;port>/crx/packmgr.
1. Klik op **[!UICONTROL Pakket]** maken. The **[!UICONTROL New Package]** dialog box appears.
1. Specificeer naam, versie, en groep voor het pakket. Click **[!UICONTROL OK]**.
1. Klik **[!UICONTROL uitgeven]** en openen de **[!UICONTROL Filters]** tabel. Klik **[!UICONTROL toevoegen Filter]**. Specificeer de weg van de werkschematoepassing. Bijvoorbeeld /etc/fd/dashboard/startpoints/homemortgage. Klik **[!UICONTROL toevoegen regel]**.

1. Open het tabblad **[!UICONTROL Geavanceerd]** . Selecteer **[!UICONTROL Fusie]** of **[!UICONTROL beschrijven]** op ACL het Behandelend gebied. Click **[!UICONTROL Save]**.
1. Klik **[!UICONTROL Bouwstijl]** om het pakket tot stand te brengen.

   Nadat het pakket is gemaakt, kunt u het pakket downloaden en importeren naar de andere server. De werkschematoepassing verschijnt op de server waar het pakket wordt geupload.

   >[!NOTE]
   >
   >Om de werkstroomtoepassing goed te laten werken, exporteert u ook het bijbehorende adaptieve formulier- en werkstroommodel met de werkapplicatie.

## Omslagen en organisatieactiva {#folders-and-organizing-assets}

Het gebruikersinterface van Vormen AEM gebruikt omslagen om activa te schikken. Deze omslagen worden gebruikt voor het schikken van activa die binnen AEM worden gecreeerd vormt gebruikersinterface. U kunt de naam, subfolders, en opslagactiva en documenten in deze omslagen anders creëren. Het organiseren van documenten en activa in een omslag staat u toe om de dossiers samen voor gemakkelijk beheer te groeperen. U kunt een omslag selecteren en verkiezen om het te downloaden of te schrappen.

Voer de volgende stappen uit om een map te maken:

### Een map maken {#create-a-folder}

1. Login aan het gebruikersinterface van Vormen AEM bij `https://<server>:<port>/aem/forms.html`.
1. Navigeer aan de plaats waaronder u een omslag wilt tot stand brengen.
1. Tik maken > Map.
1. Voer de volgende gegevens in:

   * **Titel:** De naam van de vertoning voor de omslag
   * **Naam:** *(Verplicht)* De knoopnaam waaronder u de map in de repository wilt opslaan
   >[!NOTE]
   >
   >Door gebrek, is de waarde van naamgebied automatisch bevolkt van de titel. De naam kan alfanumerieke karakters, of het koppelteken (-) en onderstreepteken (_) speciale karakters slechts bevatten. Andere speciale karakters die in de titel zijn ingegaan worden automatisch vervangen met een koppelteken en u wordt ertoe aangezet om de nieuwe naam te bevestigen. U kunt verkiezen om met voorgestelde naam verder te gaan of het uit te geven verder.

1. Een nieuwe omslag met de titel u bepaalde wordt getoond bij de huidige plaats in de activalijst.

   Als een omslag met de gespecificeerde naam bestaat, ontbreekt de voorlegging met een fout. U kunt de foutenmelding bekijken door over het fout ![aem6forms_error_alert](assets/aem6forms_error_alert.png) pictogram te hangen dat naast het naamgebied verschijnt.

   U kunt de pas gecreëerde omslag tikken om binnen de omslag te gaan en activa of omslagen te creëren binnen de omslag. Verder, kunt u een omslag selecteren en verkiezen om het voor download een rij te vormen, het te schrappen, of zijn naam uit te geven.

   ![editdeletedownloadafster](assets/editdeletedownloadafolder.png)

### Kopieën maken van een of meer elementen of letters {#create-copies-of-one-or-more-assets-or-letters}

U kunt bestaande activa en brieven gebruiken om activa en brieven met gelijkaardige eigenschappen, inhoud, en geërfte activa snel tot stand te brengen. U kunt gegevenswoordenboeken, documentfragmenten, en brieven kopiëren en kleven.

Voltooi de volgende stappen om exemplaren van activa en brieven tot stand te brengen:

1. Selecteer in de desbetreffende pagina Activa of letters een of meer elementen/letters. UI toont het pictogram van het Exemplaar.
1. Tik kopiëren. UI toont het pictogram van het Deeg. U kunt ook verkiezen om binnen een omslag te gaan/te navigeren alvorens u kleeft. De verschillende omslagen kunnen activa met de zelfde namen bevatten. Voor meer informatie over omslagen, zie [Omslagen en het organiseren van activa](#folders-and-organizing-assets).
1. Tik op Plakken. Het dialoogvenster Plakken verschijnt. De systeemauto produceert namen en titels aan de nieuwe exemplaren van activa/brieven, maar u kunt de titels en de namen van de activa/de brieven uitgeven.

   Als u de elementen/letters op dezelfde plaats kopieert en plakt, wordt een achtervoegsel &quot;-CopyXX&quot;toegevoegd aan de bestaande naam van de activa/de brief. Als geen titel voor de gekopieerde activa/de brief bestond, blijft het auto geproduceerde titelgebied leeg.

1. Indien nodig, geef de Titel en de Naam uit waarmee u het exemplaar van de activa/de brief wilt bewaren.
1. Tik op Plakken. Nieuwe exemplaren van de gekopieerde activa worden gecreeerd.

## Zoeken {#search-forms}

De Vormen UI van AEM staat u toe om uw inhoud te zoeken. Gebruikend de hoogste bar, kunt u Onderzoek **[A]** tikken om uw inhoud naar middelen zoals activa en documenten te zoeken.

Wanneer u naar activa zoekt, toont de Vormen AEM het zijpaneel. U kunt ![activa-browser-inhoud-slechts](assets/assets-browser-content-only.png) > de Filter **[B]** ook tikken om het zijpaneel aan te halen. Gebruikend de diverse filters in het zijpaneel, kunt u onderaan uw onderzoek versmallen. Het zijpaneel staat u ook toe om uw onderzoeken te bewaren.

![search_topbar](assets/search_topbar.png)

**A.** Zoeken **B.** Filteren

![Zijpaneel - Filters](assets/search_sidepanel.png)

Zijpaneel - Filters

Op het zijpaneel, kunt u het volgende gebruiken om onderaan uw onderzoeksresultaten te versmallen:

* Zoekmap
* Tags
* zoekcriteria; bijvoorbeeld, Gewijzigde Data, publiceer Status, Status LiveCopy.

Het zijpaneel staat u ook toe om uw onderzoeksmontages met namen van uw keus te bewaren.

Voor meer informatie en instructies bij het gebruiken van onderzoek, zien de filters, het bewaarde onderzoek, en het zijpaneel, [Onderzoek](/help/sites-authoring/search.md).
