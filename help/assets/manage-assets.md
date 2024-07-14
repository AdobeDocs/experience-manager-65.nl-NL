---
title: Uw digitale middelen beheren
description: Leer de taken voor middelenbeheer, zoals het uploaden, downloaden, bewerken, zoeken, verwijderen, notities aanbrengen en de versie van uw digitale middelen.
contentOwner: AG
role: User
feature: Asset Management,Search
mini-toc-levels: 4
exl-id: 158607e6-b4e9-4a3f-b023-4023d60c97d2
hide: true
solution: Experience Manager, Experience Manager Assets
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '9797'
ht-degree: 2%

---

# Uw digitale middelen beheren {#manage-digital-assets}

| Versie | Artikelkoppeling |
| -------- | ---------------------------- |
| AEM as a Cloud Service | [ klik hier ](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/assets/manage/manage-digital-assets.html?lang=en) |
| AEM 6,5 | Dit artikel |

In [!DNL Adobe Experience Manager Assets] kunt u meer doen dan uw elementen opslaan en beheren. [!DNL Experience Manager] biedt mogelijkheden voor bedrijfsmiddelenbeheer. U kunt elementen bewerken en delen, geavanceerde zoekopdrachten uitvoeren en meerdere uitvoeringen van tientallen ondersteunde bestandsindelingen maken. U kunt ook versies en digitale rechten beheren, de verwerking van elementen automatiseren, metagegevens beheren en besturen, samenwerken met annotaties en nog veel meer.

In dit artikel worden de elementaire taken voor middelenbeheer beschreven, zoals maken of uploaden; updates van metagegevens, kopiëren, verplaatsen en verwijderen, publiceren, verwijderen en zoeken naar elementen. Om het gebruikersinterface te begrijpen, zie [ begonnen worden met activa gebruikersinterface ](/help/sites-authoring/basic-handling.md). Om de Fragmenten van de Inhoud te beheren, zie [ de activa van Fragmenten van de Inhoud ](/help/assets/content-fragments/content-fragments-managing.md) beheren.

## Mappen maken {#creating-folders}

Wanneer u een verzameling elementen ordent, bijvoorbeeld alle `Nature` -afbeeldingen, kunt u mappen maken om ze bij elkaar te houden. U kunt mappen gebruiken om uw elementen te categoriseren en in te delen. U hoeft in [!DNL Experience Manager Assets] geen elementen in mappen te ordenen om beter te werken.

>[!NOTE]
>
>* Het delen van een [!DNL Assets] -map van het type `sling:OrderedFolder` wordt niet ondersteund bij het delen naar het Experience Cloud. Als u een map wilt delen, selecteert u [!UICONTROL Ordered] niet wanneer u een map maakt.
>* [!DNL Experience Manager] staat het gebruik van `subassets` -woord als naam voor een map niet toe. Het is een sleutelwoord dat voor een knoop wordt gereserveerd die subassets voor samengestelde activa bevat.

1. Navigeer naar de plaats in de map met digitale elementen waar u een map wilt maken. Klik in het menu op **[!UICONTROL Create]** . Selecteer **[!UICONTROL New Folder]** .
1. Geef in het veld **[!UICONTROL Title]** een mapnaam op. Standaard gebruikt DAM de titel die u als mapnaam hebt opgegeven. Nadat de map is gemaakt, kunt u de standaardinstelling overschrijven en een andere mapnaam opgeven.
1. Klik op **[!UICONTROL Create]**. De map wordt weergegeven in de map met digitale middelen.

De volgende tekens (lijst met door spaties gescheiden tekens) worden niet ondersteund:

* De naam van een elementbestand mag geen van de volgende tekens bevatten: `* / : [ \\ ] | # % { } ? &`
* De naam van een elementmap mag geen van deze tekens bevatten: `* / : [ \\ ] | # % { } ? \" . ^ ; + & \t`

Voeg geen speciale tekens toe aan de extensies van de bestandsnamen van elementen.

## Elementen uploaden {#uploading-assets}

<!-- TBD the following:
Move this section into a new article. CQDOC-14874 ticket is created for this.
In this complete article, replace emphasis with UICONTROL where appropriate.
-->

U kunt verschillende typen elementen (zoals afbeeldingen, PDF-bestanden, RAW-bestanden, enzovoort) uploaden van uw lokale map of een netwerkstation naar [!DNL Experience Manager Assets] .

>[!NOTE]
>
>In de modus Dynamic Media - Scene7 is de standaardbestandsgrootte voor het uploaden van middelen 2 GB of minder. Voor het configureren van het uploaden van middelen groter dan 2 GB tot 15 GB, raadpleegt u [ (Optioneel) Dynamic Media configureren - Scene7-modus voor het uploaden van middelen groter dan 2 GB ](/help/assets/config-dms7.md#optional-config-dms7-assets-larger-than-2gb) .

>[!IMPORTANT]
>
>Assets dat u uploadt naar Experience Manager met een bestandsnaam die groter is dan 100 tekens, heeft een verkorte naam wanneer ze in Dynamic Media worden gebruikt.
>
>De eerste 100 tekens in de bestandsnaam worden als volgt gebruikt. De resterende tekens worden vervangen door een alfanumerieke tekenreeks. Deze methode voor het wijzigen van de naam garandeert een unieke naam wanneer het element in Dynamic Media wordt gebruikt. Het is ook bedoeld om rekening te houden met de maximale lengte voor elementbestanden die in Dynamic Media is toegestaan.

U kunt ervoor kiezen elementen te uploaden naar mappen waaraan al dan niet een verwerkingsprofiel is toegewezen.

Voor mappen waaraan een verwerkingsprofiel is toegewezen, wordt de profielnaam weergegeven op de miniatuur in de kaartweergave. In de lijstmening, verschijnt de profielnaam in de **kolom van het Profiel van de Verwerking**. Zie [ Profielen van de Verwerking ](/help/assets/processing-profiles.md).

Alvorens een activa te uploaden, zorg ervoor dat het in a [ formaat ](/help/assets/assets-formats.md) is dat [!DNL Experience Manager Assets] steunt.

1. Navigeer in de gebruikersinterface van [!DNL Assets] naar de locatie waar u digitale elementen wilt toevoegen.
1. Voer een van de volgende handelingen uit om de elementen te uploaden:

   * Klik op **[!UICONTROL Create]** op de werkbalk. Klik vervolgens op **[!UICONTROL Files]** in het menu. U kunt de naam van het bestand desgewenst wijzigen in het dialoogvenster dat verschijnt.
   * In een browser die HTML5 ondersteunt, sleept u de elementen rechtstreeks naar de gebruikersinterface van [!DNL Assets] . Het dialoogvenster voor het wijzigen van de naam van het bestand wordt niet weergegeven.

   ![ creeer optie om activa ](assets/create-options.png) te uploaden

   Als u meerdere bestanden wilt selecteren, selecteert u de `Ctrl` - of `Command` -toets en selecteert u de elementen in het dialoogvenster Bestandenkiezer. Als u een iPad gebruikt, kunt u slechts één bestand tegelijk selecteren.

   U kunt het uploaden van grote elementen (groter dan 500 MB) pauzeren en later vanaf dezelfde pagina hervatten. Klik op **[!UICONTROL Pause]** naast de voortgangsbalk die wordt weergegeven wanneer het uploaden start.

   ![ uploadt activa voortgangsbar ](assets/upload-progress-bar.png)

De omvang waarboven een actief als een groot actief wordt beschouwd, is configureerbaar. U kunt het systeem bijvoorbeeld zodanig configureren dat elementen van meer dan 1000 MB (in plaats van 500 MB) als grote elementen worden beschouwd. In dit geval wordt **[!UICONTROL Pause]** weergegeven op de voortgangsbalk wanneer bestanden van meer dan 1000 MB worden geüpload.

De optie [!UICONTROL Pause] wordt niet weergegeven als een bestand van meer dan 1000 MB wordt geüpload met een bestand van minder dan 1000 MB. Als u echter het uploaden van bestanden met minder dan 1000 MB annuleert, wordt de optie **[!UICONTROL Pause]** weergegeven.

Als u de formaatlimiet wilt wijzigen, configureert u de eigenschap `chunkUploadMinFileSize` van het knooppunt `fileupload` in de CRX-opslagruimte die beschikbaar is op `/apps/dam/gui/content/assets/jcr:content/actions/secondary/create/items/fileupload` .

Wanneer u op **[!UICONTROL Pause]** klikt, schakelt u over naar de optie **[!UICONTROL Play]** . Klik op **[!UICONTROL Play]** om het uploaden te hervatten.

Als u een actieve upload wilt annuleren, klikt u op Sluiten (`X`) naast de voortgangsbalk. Wanneer u het uploaden annuleert, verwijdert [!DNL Assets] het gedeeltelijk geüploade gedeelte van het element.

De mogelijkheid om het uploaden te hervatten is vooral handig in scenario&#39;s met lage bandbreedte en netwerkstoringen, waarbij het uploaden van een groot element veel tijd in beslag neemt. U kunt het uploaden pauzeren en verdergaan wanneer de situatie verbetert. Wanneer u het document hervat, begint het uploaden vanaf het punt waarop u het hebt gepauzeerd.

Tijdens het uploaden slaat [!DNL Experience Manager] de delen van het element dat wordt geüpload op als stukjes gegevens in de CRX-opslagplaats. Wanneer het uploaden is voltooid, consolideert [!DNL Experience Manager] deze fragmenten in één gegevensblok in de gegevensopslagruimte.

Ga naar `https://[aem_server]:[port]/system/console/configMgr/org.apache.sling.servlets.post.impl.helper.ChunkCleanUpTask` als u de opschoningstaak wilt configureren voor de onvoltooide taken voor het uploaden van taken.

>[!CAUTION]
>
>Het uploaden van de brok wordt teweeggebracht wanneer de standaardwaarde 500 MB is en de brokgrootte 50 MB is. Als u [ Apache Jackrabbit Oak TokenConfiguration ](https://experienceleague.adobe.com/docs/experience-cloud-kcs/kbarticles/KA-16464.html) uitgeeft en `timeout configuration` aan minder dan de tijd plaatst het voor activa aan upload neemt, ontmoet u een situatie van de zittingsonderbreking terwijl de activa uploadt lopend is. Wijzig daarom de `chunkUploadMinFileSize` en `chunksize` zodanig dat elke segmentaanvraag de sessie vernieuwt.
>
>Op basis van de time-out bij verlopen van de referentie, de latentie, de bandbreedte en de verwachte gelijktijdige uploads, is de hoogste waarde waarmee u ervoor kunt zorgen dat het volgende wordt gekozen:
>
>* Om ervoor te zorgen dat het uploaden van brokken is ingeschakeld voor bestanden met grootten die tijdens het uploaden waarschijnlijk resulteren in een vervaldatum van de referentie.
>
>* Om ervoor te zorgen dat elk segment eindigt alvorens de referentie verloopt.

Als u een element uploadt met dezelfde naam als een element dat al beschikbaar is op de locatie waar u het element uploadt, wordt een waarschuwingsvenster weergegeven.

U kunt een bestaand element vervangen, een andere versie maken of beide behouden door de naam van het nieuwe element dat wordt geüpload te wijzigen. Als u een bestaand element vervangt, worden de metagegevens voor het element en eventuele eerdere wijzigingen (bijvoorbeeld notities aanbrengen of uitsnijden) die u in het bestaande element hebt aangebracht, verwijderd. Als u ervoor kiest beide elementen te behouden, wordt de naam van het nieuwe element gewijzigd in het nummer `1` dat aan de naam wordt toegevoegd.

![ de dialoog van het Conflict van de Naam om het conflict van de activanaam op te lossen ](assets/resolve-naming-conflict.png)

>[!NOTE]
>
>Wanneer u **[!UICONTROL Replace]** selecteert in het dialoogvenster [!UICONTROL Name Conflict] , wordt de element-id opnieuw gegenereerd voor het nieuwe element. Deze id verschilt van de id van het vorige element.
>
>Als Assets Insights is ingeschakeld voor het bijhouden van indrukken of klikken met [!DNL Adobe Analytics] , maakt de opnieuw gegenereerde element-id de vastgelegde gegevens voor het element op [!DNL Analytics] ongeldig.

Als het element dat u uploadt, bestaat in [!DNL Assets] , wordt in het dialoogvenster **[!UICONTROL Duplicates Detected]** gewaarschuwd dat u probeert een dubbel element te uploaden. Het dialoogvenster wordt alleen weergegeven als de waarde van de `SHA 1` -controlesom van het binaire element van het bestaande element overeenkomt met de waarde van de controlesom van het element dat u uploadt. In dit geval zijn de namen van de elementen niet van belang.

>[!NOTE]
>
>Het dialoogvenster [!UICONTROL Duplicates Detected] wordt alleen weergegeven wanneer de functie voor dubbele detectie is ingeschakeld. Om de dubbele opsporingseigenschap toe te laten, zie [ toelaten Dubbele Opsporing ](/help/assets/duplicate-detection.md).

![ Dubbele Gedetecteerde dialoog van Activa ](assets/duplicate-asset-detected.png)

Als u het gedupliceerde element wilt behouden in [!DNL Assets] , klikt u op **[!UICONTROL Keep]** . Als u het geüploade dubbele element wilt verwijderen, klikt u op **[!UICONTROL Delete]** .

[!DNL Experience Manager Assets] voorkomt dat u elementen uploadt met de verboden tekens in de bestandsnaam. Als u een element probeert te uploaden met een bestandsnaam die een niet-toegestaan teken of meer bevat, geeft [!DNL Assets] een waarschuwingsbericht weer en wordt het uploaden gestopt totdat u deze tekens verwijdert of uploadt met een toegestane naam.

In het dialoogvenster [!UICONTROL Upload Assets] kunt u lange namen opgeven voor de bestanden die u uploadt, zodat uw organisatie deze gebruiken voor specifieke naamconventies voor bestanden.

De volgende tekens (lijst met door spaties gescheiden tekens) worden echter niet ondersteund:

* de naam van het elementbestand mag niet `* / : [ \\ ] | # % { } ? &` bevatten
* naam van elementmap mag geen `* / : [ \\ ] | # % { } ? \" . ^ ; + & \t` bevatten

Voeg geen speciale tekens toe aan de extensies van de bestandsnamen van elementen.

![ uploadt de voortgangsdialoog toont status van met succes geuploade dossiers en dossiers die er niet in slagen te uploaden ](assets/bulk-upload-progress.png)

Daarnaast wordt in de gebruikersinterface van [!DNL Assets] het element weergegeven dat u het laatst hebt geüpload of de map die u het eerst hebt gemaakt.

Als u het uploaden annuleert voordat de bestanden zijn geüpload, stopt [!DNL Assets] met het uploaden van het huidige bestand en wordt de inhoud vernieuwd. Bestanden die al zijn geüpload, worden echter niet verwijderd.

Het dialoogvenster voor uploadvoortgang in [!DNL Assets] geeft het aantal bestanden weer dat is geüpload en de bestanden die niet zijn geüpload.

### Seriële uploads {#serialuploads}

Het uploaden van talloze assets in bulk verbruikt aanzienlijke I/O-bronnen, wat de prestaties van uw [!DNL Assets] -implementatie nadelig kan beïnvloeden. Met name als u een trage internetverbinding hebt, neemt de uploadtijd drastisch toe als gevolg van een spiek in schijf-I/O. Bovendien kan uw webbrowser extra beperkingen instellen voor het aantal aanvragen van POSTEN dat [!DNL Assets] kan afhandelen voor het uploaden van gelijktijdig gebruikte bestanden. Hierdoor mislukt de uploadbewerking of wordt deze voortijdig beëindigd. Met andere woorden, [!DNL Experience Manager Assets] kan sommige bestanden missen terwijl u een aantal bestanden binnenkrijgt of kan helemaal geen bestand opnemen.

Om deze situatie te verhelpen, voegt [!DNL Assets] één middel tegelijkertijd (periodieke upload) tijdens een bulkupload verrichting in plaats van het tegelijkertijd opnemen van alle activa in.

Seriële uploaden van elementen is standaard ingeschakeld. Als u de functie wilt uitschakelen en het uploaden wilt toestaan, bedekt u het knooppunt `fileupload` in Crx-de en stelt u de waarde van de eigenschap `parallelUploads` in op `true` .

### Elementen uploaden met FTP {#uploading-assets-using-ftp}

Dynamic Media maakt het uploaden van bestanden in batches via FTP-server mogelijk. Als u grote elementen wilt uploaden (>1 GB) of volledige mappen en submappen wilt uploaden, moet u FTP gebruiken. U kunt zelfs instellen dat FTP-upload wordt uitgevoerd op een terugkerende geplande basis.

>[!NOTE]
>
>In de modus Dynamic Media - Scene7 is de standaardbestandsgrootte voor het uploaden van middelen 2 GB of minder. Voor het configureren van het uploaden van middelen groter dan 2 GB tot 15 GB, raadpleegt u [ (Optioneel) Dynamic Media configureren - Scene7-modus voor het uploaden van middelen groter dan 2 GB ](/help/assets/config-dms7.md#optional-config-dms7-assets-larger-than-2gb) .

>[!NOTE]
>
>Als u elementen wilt uploaden via FTP in de modus Dynamic Media - Scene7, installeert u Feature Pack 18912 op de auteur-exemplaren van [!DNL Experience Manager] . De Steun van de Klant van de Adobe van het contact ](https://experienceleague.adobe.com/?support-solution=General#support) om toegang tot FP-18912 te krijgen en de opstelling van uw rekening van FTP te voltooien. [ Voor meer informatie, zie [ eigenschappak 18912 voor bulkactiva migratie ](/help/assets/bulk-ingest-migrate.md) installeren.
>
>Als u FTP gebruikt om elementen te uploaden, worden de uploadinstellingen die in [!DNL Experience Manager] zijn opgegeven, genegeerd. In plaats daarvan worden de regels voor bestandsverwerking gebruikt, zoals gedefinieerd in Dynamic Media Classic.

**om activa te uploaden gebruikend FTP**

1. Meld u met uw keuze voor een FTP-client aan bij de FTP-server met de FTP-gebruikersnaam en -wachtwoord die u van de e-mail met de provisioning hebt ontvangen. Upload in de FTP-client bestanden of mappen naar de FTP-server.

1. Open de [ Desktoptoepassing van Dynamic Media Classic ](https://experienceleague.adobe.com/docs/dynamic-media-classic/using/intro/dynamic-media-classic-desktop-app.html#system-requirements-dmc-app), dan login aan uw rekening.

   Uw aanmeldingsgegevens en aanmelding zijn door de Adobe opgegeven op het moment van levering. Neem contact op met de Klantenondersteuning van de Adobe als u deze informatie niet hebt.

1. Klik op **[!UICONTROL Upload]** op de algemene navigatiebalk.
1. Klik op de pagina Uploaden linksboven op de tab **[!UICONTROL Via FTP]** .
1. Kies links op de pagina een FTP-map waaruit u bestanden wilt uploaden. Kies rechts op de pagina een doelmap.
1. Klik in de rechterbenedenhoek van de pagina op **[!UICONTROL Job Options]** en stel vervolgens de gewenste opties in op basis van de elementen in de map die u hebt geselecteerd.

   Zie [ de Opties van de Baan van uploaden ](#upload-job-options).

   >[!NOTE]
   >
   >Wanneer u elementen uploadt via FTP, hebben de opties voor uploadtaken die u in Dynamic Media Classic (S7) hebt ingesteld, voorrang op de parameters voor middelenverwerking die zijn ingesteld in [!DNL Experience Manager] .

1. Klik in de rechterbenedenhoek van het dialoogvenster Taakopties uploaden op **[!UICONTROL Save]** .
1. Klik in de rechterbenedenhoek van de pagina Uploaden op **[!UICONTROL Submit Upload]** .

   Klik op **[!UICONTROL Jobs]** op de algemene navigatiebalk om de voortgang van het uploaden weer te geven. Op de pagina Taken wordt de voortgang van het uploaden weergegeven. U kunt in [!DNL Experience Manager] blijven werken en op elk gewenst moment terugkeren naar de pagina Taken in Dynamic Media Classic om een actieve taak te controleren.
Als u een uploadtaak die wordt uitgevoerd wilt annuleren, klikt u op **[!UICONTROL Cancel]** naast de duur van de upload.

#### Opties voor uploaden {#upload-job-options}

| Uploaden, optie | Suboption | Beschrijving |
|---|---|---|
| Taaknaam | | De standaardnaam die vooraf in het tekstveld is ingevuld, bevat het door de gebruiker ingevoerde gedeelte van de naam en de datum- en tijdstempel. U kunt de standaardnaam gebruiken of een naam invoeren van uw eigen ontwerp voor deze uploadtaak. <br> de baan en andere upload en het publiceren banen worden geregistreerd op de pagina van Banen, waar u de status van banen kunt controleren. |
| Publish na uploaden | | Hiermee publiceert u automatisch de elementen die u uploadt. |
| Overschrijven in een willekeurige map, dezelfde naam van basiselement, ongeacht de extensie | | Selecteer deze optie als u wilt dat de bestanden die u uploadt, bestaande bestanden met dezelfde naam vervangen. De naam van deze optie kan verschillen, afhankelijk van de instellingen in **[!UICONTROL Application Setup]** > **[!UICONTROL General Settings]** > **[!UICONTROL Upload to Application]** > **[!UICONTROL Overwrite Images]** . |
| ZIP- of Tar-bestanden bij uploaden decomprimeren | | |
| Taakopties | | Klik op **[!UICONTROL Job Options]** zodat u het dialoogvenster [!UICONTROL Upload Job Options] kunt openen en opties kunt kiezen die van invloed zijn op de volledige uploadtaak. Deze opties zijn hetzelfde voor alle bestandstypen.<br> u kunt standaardopties kiezen voor het uploaden van dossiers die op de pagina van de Montages van de Toepassing Algemene beginnen. Kies **[!UICONTROL Setup]** > **[!UICONTROL Application Setup]** om deze pagina te openen. Selecteer de optie **[!UICONTROL Default Upload Options]** om het dialoogvenster [!UICONTROL Upload Job Options] te openen. |
| | Wanneer | Selecteer Eenmalig of Herhalend. Als u een terugkerende taak wilt instellen, kiest u de optie Herhalen (Dagelijks, Wekelijks, Maandelijks of Aangepast) om op te geven wanneer de FTP-uploadtaak moet worden herhaald. Geef vervolgens de gewenste opties op. |
| | Inclusief submappen | Upload alle submappen in de map die u wilt uploaden. De namen van de map en de submappen die u uploadt, worden automatisch ingevoerd in [!DNL Experience Manager Assets] . |
| | Opties voor uitsnijden | Als u handmatig wilt uitsnijden aan weerszijden van een afbeelding, selecteert u het menu Uitsnijden en kiest u Handmatig. Voer vervolgens het aantal pixels in dat u aan elke zijde van de afbeelding wilt uitsnijden. Hoeveel van de afbeelding wordt uitgesneden, is afhankelijk van de ppi-instelling (pixels per inch) in het afbeeldingsbestand. Als de afbeelding bijvoorbeeld 150 ppi weergeeft en u 75 invoert in de tekstvakken Boven, Rechts, Onder en Links, wordt aan beide zijden een halve inch bijgesneden.<br> Als u pixels in witruimte automatisch wilt uitsnijden in een afbeelding, opent u het menu Uitsnijden, kiest u Handmatig en voert u pixelmetingen in in de velden Boven, Rechts, Onder en Links om van de zijkanten uit te snijden. U kunt ook Bijsnijden kiezen op het menu van het Gewas en deze opties kiezen:<br> **weg Verkleinen Gebaseerd op** <ul><li>**Kleur** - kies de optie van de Kleur. Selecteer vervolgens het menu Hoek en kies de hoek van de afbeelding met de kleur die het beste overeenkomt met de kleur voor de witruimte die u wilt uitsnijden.</li><li>**Transparantie** - kies de optie van de Transparantie.<br> **Tolerantie** - sleep de schuif om een tolerantie van 0 door 1 te specificeren. Voor het in orde maken die op kleur wordt gebaseerd, specificeer 0 aan gewassenpixel slechts als zij precies de kleur aanpassen u in de hoek van het beeld selecteerde. De aantallen dichter aan 1 staan voor meer kleurenverschil toe.<br> voor het in orde maken die op transparantie wordt gebaseerd, specificeer 0 aan gewassenpixel slechts als zij transparant zijn. De aantallen dichter aan 1 staan voor meer transparantie toe.</li></ul><br> Deze gewassenopties zijn niet-destructief. |
| | Opties voor kleurprofiel | Kies een kleurconversie wanneer u geoptimaliseerde bestanden maakt die worden gebruikt voor levering:<ul><li>Standaardkleurbehoud: de kleuren van de bronafbeelding blijven behouden wanneer de afbeeldingen kleurruimtegegevens bevatten; er is geen kleuromzetting. In bijna alle afbeeldingen van vandaag is het juiste kleurprofiel al ingesloten. Als een CMYK-bronafbeelding echter geen ingesloten kleurprofiel bevat, worden de kleuren omgezet in de kleurruimte sRGB (standaard rood-groen-blauw). sRGB is de aanbevolen kleurruimte voor het weergeven van afbeeldingen op webpagina&#39;s.</li><li>Oorspronkelijke kleurruimte behouden: de oorspronkelijke kleuren blijven behouden zonder kleuromzetting op het punt. Voor afbeeldingen zonder ingesloten kleurprofiel wordt elke kleurconversie uitgevoerd met de standaardkleurprofielen die zijn geconfigureerd in de Publish-instellingen. De kleurprofielen worden mogelijk niet uitgelijnd met de kleur in de bestanden die met deze optie zijn gemaakt. Daarom wordt u aangeraden de optie Standaardkleurbehoud te gebruiken.</li><li>Met Aangepast van > naar <br> opent u menu&#39;s, zodat u een optie kunt kiezen voor Omzetten van en Omzetten in kleurruimte. Deze geavanceerde optie negeert alle kleurinformatie die in het bronbestand is ingesloten. Selecteer deze optie als alle afbeeldingen die u verzendt, onjuiste of ontbrekende kleurprofielgegevens bevatten.</li></ul> |
| | Opties voor het bewerken van afbeeldingen | U kunt de knipmaskers in afbeeldingen behouden en een kleurprofiel kiezen.<br> zie [ Plaatsende opties voor beeld geeft bij upload ](#setting-image-editing-options-at-upload) uit. |
| | PostScript-opties | U kunt PostScript® rasteren, bestanden uitsnijden, transparante achtergronden behouden, een resolutie kiezen en een kleurruimte kiezen.<br> zie [ Plaatsende PostScript en Illustrator uploadt opties ](#setting-postscript-and-illustrator-upload-options). |
| | Photoshop-opties | U kunt sjablonen maken van Adobe® Photoshop®-bestanden, lagen behouden, opgeven hoe lagen worden genoemd, tekst extraheren en opgeven hoe afbeeldingen in sjablonen worden verankerd.<br> Sjablonen worden niet ondersteund in [!DNL Experience Manager] .<br> zie [ Plaatsend Photoshop uploadt opties ](#setting-photoshop-upload-options). |
| | PDF-opties | U kunt de bestanden rasteren, zoekwoorden en koppelingen extraheren, automatisch een eCatalog genereren, de resolutie instellen en een kleurruimte kiezen.<br> eCatalogs wordt niet gesteund in [!DNL Experience Manager]. <br> zie [ Plaatsende PDF uploadopties ](#setting-pdf-upload-options).<br>**Nota**: Het maximumaantal pagina&#39;s voor een PDF dat voor extractie moet worden overwogen is 5000 voor nieuwe uploads. Deze limiet verandert in 100 pagina&#39;s (voor alle PDF) op 31 december 2022. Zie ook {de beperkingen van 0} Dynamic Media ](/help/assets/limitations.md).[ |
| | Illustrator-opties | U kunt Adobe Illustrator®-bestanden rasteren, transparante achtergronden behouden, een resolutie kiezen en een kleurruimte kiezen.<br> zie [ Plaatsende PostScript en Illustrator uploadt opties ](#setting-postscript-and-illustrator-upload-options). |
| | EVideo-opties | U kunt een videobestand transcoderen door een videovoorinstelling te kiezen.<br> zie [ Plaatsende eVideo uploadt opties ](#setting-evideo-upload-options). |
| | Voorinstellingen batchset | Als u een Afbeeldingsset of Spin-set wilt maken van de geüploade bestanden, klikt u op de kolom Actief voor de voorinstelling die u wilt gebruiken. U kunt meerdere voorinstellingen selecteren. U maakt de voorinstellingen op de pagina Voorinstellingen voor toepassingsinstellingen/batchsets van Dynamic Media Classic.<br> zie [ Vormende Partij plaatsen vooraf instelt aan Auto-produceerde de Reeksen van het Beeld en de Reeksen van de Draai ](config-dms7.md#creating-batch-set-presets-to-auto-generate-image-sets-and-spin-sets) om meer over het creëren van partijreeks te leren vooraf instelt.<br> zie [ Plaatsende Geplaatste Partij vooraf instelt bij upload ](#setting-batch-set-presets-at-upload). |

#### Opties instellen voor afbeeldingsbewerkingen tijdens het uploaden {#setting-image-editing-options-at-upload}

Wanneer u afbeeldingsbestanden uploadt, zoals AI-, EPS- en PSD-bestanden, kunt u de volgende bewerkingen uitvoeren in het dialoogvenster [!UICONTROL Upload Job Options] :

* Witruimte uitsnijden vanaf de rand van afbeeldingen (zie beschrijving in bovenstaande tabel).
* Handmatig uitsnijden vanaf de zijkanten van afbeeldingen (zie beschrijving in bovenstaande tabel).
* Kies een kleurprofiel (zie de beschrijving van de optie in de bovenstaande tabel).
* Maak een masker van een uitknippad.
* Afbeeldingen verscherpen met onscherpe maskeropties
* Achtergrond uitnemen

<!--
| Option | Sub-option | Description |
|---|---|---|
| Create Mask From Clipping Path | | Create a mask for the image based on its clipping path information. This option applies to images created with image-editing applications in which a clipping path was created. |
| Unsharp Masking | | Lets you fine-tune a sharpening filter effect on the final downsampled image, controlling the intensity of the effect, the radius of the effect (as measured in pixels), and a threshold of contrast that is ignored.<br> This effect uses the same options as Photoshop's Unsharp Mask filter. Contrary to what the name suggests, Unsharp Mask is a sharpening filter. Under Unsharp Masking, set the options you want. Setting options are described in the following: |
| | Amount | Controls the amount of contrast that is applied to edge pixels.<br> Think of it as the intensity of the effect. The main difference between the amount values of Unsharp Mask in Dynamic Media and the amount values in Adobe Photoshop, is that Photoshop has an amount range of 1% to 500%. Whereas, in Dynamic Media, the value range is 0.0 to 5.0. A value of 5.0 is the rough equivalent of 500% in Photoshop; a value of 0.9 is the equivalent of 90%, and so on. |
| | Radius | Controls the radius of the effect. The value range is 0-250.<br> The effect is run on all pixels in an image and radiates out from all pixels in all directions. The radius is measured in pixels. For example, to get a similar sharpening effect for a 2000 x 2000 pixel image and 500 x 500 pixel image, you would set a radius of two pixels on the 2000 x 2000 pixel image and a radius value of one pixel on the 500 x 500 pixel image. A larger value is used for an image that has more pixels. |
| | Threshold | Threshold is a range of contrast that is ignored when the Unsharp Mask filter is applied. It is important so that no "noise" is introduced to an image when this filter is used. The value range is 0-255, which is the number of brightness steps in a grayscale image. 0=black, 128=50% gray and 255=white.<br> For example, a threshold value of 12 ignores slight variations is skin tone brightness to avoid adding noise, but still add edge contrast to areas such as where eyelashes meet skin.<br> For example, if you have a photo of someone's face, the Unsharp Mask affects the parts of the image, such as where eyelashes and skin meet to create an obvious area of contrast, and the smooth skin itself. Even the smoothest skin exhibits subtle changes in brightness values. If you do not use a threshold value, the filter accentuates these subtle changes in skin pixels. In turn, a noisy and undesirable effect is created while contrast on the eyelashes is increased, enhancing sharpness.<br> To avoid this issue, a threshold value is introduced that tells the filter to ignore pixels that do not change contrast dramatically, like smooth skin.<br> In the zipper graphic shown earlier, notice the texture next to the zippers. Image noise is exhibited because the threshold values were too low to suppress the noise. |
| | Monochrome | Select to unsharp-mask image brightness (intensity).<br> Deselect to unsharp-mask each color component separately. |
| Knockout Background | | Automatically removes the background of an image when you upload it. This technique is useful to draw attention to a particular object and make it stand out from a busy background. Select to enable or "turn on" the Knockout Background feature and the following sub-options: |
| | Corner | Required.<br> The corner of the image that is used to define the background color to knockout.<br> You can choose from **Upper Left**, **Bottom Left**, **Upper Right**, or **Bottom Right**. |
| | Fill Method | Required.<br> Controls pixel transparency from the Corner location that you set.<br> You can choose from the following fill methods: <ul><li>**Flood Fill** - turns all pixels transparent that match the Corner that you have specified and are connected to it.</li><li>**Match Pixel** - turns all matching pixels transparent, regardless of their location on the image.</li></ul> |
| | Tolerance | Optional.<br> Controls the allowable amount of variation in pixel color matching based on the Corner location that you set.<br> Use a value of 0.0 to match pixel colors exactly or, use a value of 1.0 to allow for the greatest variation. |
-->

#### Uploadopties voor PostScript en Illustrator instellen {#setting-postscript-and-illustrator-upload-options}

Wanneer u PostScript (EPS)- of Illustrator (AI)-afbeeldingsbestanden uploadt, kunt u deze op verschillende manieren opmaken. U kunt de bestanden rasteren, de transparante achtergrond behouden, een resolutie kiezen en een kleurruimte kiezen. Opties voor het opmaken van PostScript- en Illustrator-bestanden zijn beschikbaar in het dialoogvenster [!UICONTROL Upload Job Options] onder [!UICONTROL PostScript Options] en [!UICONTROL Illustrator Options] .

| Optie | Suboption | Beschrijving |
|---|---|---|
| Verwerking | | Kies **[!UICONTROL Rasterize]** om vectorafbeeldingen in het bestand om te zetten in de bitmapindeling. |
| Transparante achtergrond behouden in gerenderde afbeelding | | De achtergrondtransparantie van het bestand behouden. |
| Resolutie | | Hiermee bepaalt u de resolutie-instelling. Deze instelling bepaalt hoeveel pixels per inch in het bestand worden weergegeven. |
| Kleurruimte | | Selecteer het menu Kleurruimte en kies een van de volgende opties voor kleurruimte: |
| | Automatisch detecteren | Hiermee behoudt u de kleurruimte van het bestand. |
| | Krachten als RGB | Hiermee wordt de kleurruimte RGB omgezet. |
| | Inschakelen als CMYK | Zet om in de CMYK-kleurruimte. |
| | Forceren als grijswaarden | Hiermee wordt de grijswaardenkleurruimte omgezet. |

#### Photoshop-upopties instellen {#setting-photoshop-upload-options}

Photoshop Document (PSD)-bestanden worden meestal gebruikt om afbeeldingssjablonen te maken. Wanneer u een PSD-bestand uploadt, kunt u automatisch een afbeeldingssjabloon maken vanuit het bestand (selecteer de optie [!UICONTROL Create Template] in het scherm Uploaden).

Dynamic Media maakt meerdere afbeeldingen van een PSD-bestand met lagen als u het bestand gebruikt om een sjabloon te maken. Voor elke laag wordt één afbeelding gemaakt.

Gebruik [!UICONTROL Crop Options] en [!UICONTROL Color Profile Options], zoals hierboven beschreven, met Photoshop-uploadopties.

>[!NOTE]
>
>Sjablonen worden niet ondersteund in [!DNL Experience Manager] .

| Optie | Suboption | Beschrijving |
|---|---|---|
| Lagen behouden | | Hiermee worden de lagen in de PSD, indien aanwezig, uitgelijnd op afzonderlijke elementen. De elementlagen blijven gekoppeld aan de PSD. U kunt deze weergeven door het PSD-bestand te openen in de gedetailleerde weergave en het deelvenster Lagen te selecteren. |
| Sjabloon maken | | Maakt een sjabloon op basis van de lagen in het PSD-bestand. |
| Tekst extraheren | | Extraheert de tekst zodat gebruikers naar tekst in een viewer kunnen zoeken. |
| Lagen uitbreiden naar achtergrondgrootte | | Hiermee vergroot u de grootte van de uitgesneden afbeeldingslagen tot de grootte van de achtergrondlaag. |
| Laagnaamgeving | | Lagen in het PSD-bestand worden geüpload als aparte afbeeldingen. |
| | Laagnaam | De afbeeldingen krijgen een naam na hun laagnamen in het PSD-bestand. Een laag met de naam Prijscode in het oorspronkelijke PSD-bestand wordt bijvoorbeeld een afbeelding met de naam Prijscode. Als de laagnamen in het PSD-bestand echter standaard Photoshop-laagnamen zijn (Achtergrond, Laag 1, Laag 2, enzovoort), krijgen de afbeeldingen een naam na hun laagnummers in het PSD-bestand. Ze krijgen geen naam achter hun standaardlaagnamen. |
| | Photoshop en Layer Number | De afbeeldingen krijgen een naam na hun laagnummer in het PSD-bestand, waarbij de namen van de oorspronkelijke lagen worden genegeerd. Afbeeldingen krijgen de naam Photoshop en een toegevoegd laagnummer. De tweede laag van een bestand met de naam Voorjaar-Ad.psd krijgt bijvoorbeeld de naam Voorjaar-Ad_2, zelfs als deze in Photoshop een andere naam heeft dan de standaardnaam. |
| | Photoshop- en laagnaam | De afbeeldingen krijgen een naam na het PSD-bestand gevolgd door de naam van de laag of het laagnummer. Het laagnummer wordt gebruikt als de laagnamen in het PSD-bestand standaard Photoshop-laagnamen zijn. Een laag met de naam Price Tag in een PSD-bestand met de naam SpringAd krijgt bijvoorbeeld de naam Spring Ad_Price Tag. Een laag met de standaardnaam Laag 2 wordt genoemd Lente Ad_2. |
| Anker | | Geef op hoe afbeeldingen worden verankerd in sjablonen die worden gegenereerd op basis van de laagsamenstelling die uit het PSD-bestand is samengesteld. Standaard is het anker het middelpunt. Met een middelste anker kunnen vervangende afbeeldingen dezelfde ruimte het beste vullen, ongeacht de hoogte-breedteverhouding van de vervangende afbeelding. Afbeeldingen met een ander aspect dat deze afbeelding vervangt, nemen bij het verwijzen naar de sjabloon en het gebruik van parametervervanging in feite dezelfde ruimte in. Schakel over naar een andere instelling als de vervangende afbeeldingen de toegewezen ruimte in de sjabloon moeten vullen. |

#### Opties voor het uploaden naar PDF instellen {#setting-pdf-upload-options}

Wanneer u een PDF-bestand uploadt, kunt u het op verschillende manieren opmaken. U snijdt zijn pagina&#39;s bij, haalt zoekwoorden op, voert een pixel-per-duimresolutie in, en kiest een kleurenruimte. PDF-bestanden bevatten vaak een snijmarge, snijtekens, registratietekens en andere drukkersmarkeringen. U kunt deze markeringen vanaf de zijkanten van pagina&#39;s bijsnijden wanneer u een PDF-bestand uploadt.

Het maximumaantal pagina&#39;s voor een PDF dat voor extractie in aanmerking komt, is 5000 voor nieuwe uploads. Deze limiet wordt op 31 december 2022 gewijzigd in 100 pagina&#39;s (voor alle PDF). Zie ook {de beperkingen van 0} Dynamic Media ](/help/assets/limitations.md).[

>[!NOTE]
>
>eCatalogs worden niet ondersteund in [!DNL Experience Manager] .

Kies een van de volgende opties:

| Optie | Suboption | Beschrijving |
|---|---|---|
| Verwerking | Rasteren | (Standaard) Hiermee worden de pagina&#39;s in het PDF-bestand weggesneden en worden vectorafbeeldingen omgezet in bitmapafbeeldingen. Kies deze optie als u een eCatalog wilt maken. |
| Extraheren | Woorden zoeken | Extraheert woorden uit het PDF-bestand, zodat het bestand op trefwoord in een eCatalog-viewer kan worden doorzocht. |
| | Koppelingen | Extraheert koppelingen uit de PDF-bestanden en converteert deze naar Afbeeldingen met hyperlinks die worden gebruikt in een eCatalog-viewer. |
| E-catalogus automatisch genereren op basis van PDF van meerdere pagina&#39;s | | Hiermee wordt automatisch een eCatalog gemaakt op basis van het PDF-bestand. De eCatalog wordt genoemd naar het dossier van de PDF u uploadde. (Deze optie is alleen beschikbaar als u het PDF-bestand rastert tijdens het uploaden.) |
| Resolutie | | Hiermee bepaalt u de resolutie-instelling. Deze instelling bepaalt hoeveel pixels per inch in het PDF-bestand worden weergegeven. De standaardwaarde is 150. |
| Kleurruimte | | Selecteer het menu Kleurruimte en kies een kleurruimte voor het PDF-bestand. De meeste PDF-bestanden hebben zowel RGB- als CMYK-kleurenafbeeldingen. De kleurruimte RGB heeft de voorkeur voor onlineweergave. |
| | Automatisch detecteren | Hiermee behoudt u de kleurruimte van het PDF-bestand. |
| | Krachten als RGB | Hiermee wordt de kleurruimte RGB omgezet. |
| | Krachten als CMYK | Zet om in de CMYK-kleurruimte. |
| | Krachtig maken als grijswaarden | Hiermee wordt de grijswaardenkleurruimte omgezet. |

#### Uploadopties voor eVideo instellen {#setting-evideo-upload-options}

U transcodeert een videobestand door een keuze te maken uit verschillende videovoorinstellingen.

| Optie | Suboption | Beschrijving |
|---|---|---|
| Adaptieve video | | Eén coderingsvoorinstelling die met een willekeurige hoogte-breedteverhouding werkt voor het maken van video&#39;s voor levering op mobiele apparaten, tablets en desktops. Geüploade bronvideo&#39;s die met deze voorinstelling zijn gecodeerd, worden ingesteld met een vaste hoogte. De breedte wordt echter automatisch geschaald om de hoogte-breedteverhouding van de video te behouden. <br> beste praktijken moeten het Aangepaste Video coderen gebruiken. |
| Enkele coderingsvoorinstellingen | Voorinstellingen voor codering sorteren | Selecteer **[!UICONTROL Name]** of **[!UICONTROL Size]** als u de coderingsvoorinstellingen die onder Desktop, Mobile en Tablet worden vermeld, wilt sorteren op naam of op resolutiegrootte. |
| | Desktop | Maak een MP4-bestand voor een streaming of progressieve videobeleving op bureaubladcomputers. Selecteer een of meer hoogte-breedteverhoudingen met de gewenste resolutie- en doelgegevenssnelheid. |
| | Mobiel | Maak een MP4-bestand voor levering op mobiele iPhone- of Android™-apparaten. Selecteer een of meer hoogte-breedteverhoudingen met de gewenste resolutie- en doelgegevenssnelheid. |
| | Tablet | Maak een MP4-bestand voor levering op iPad- of Android™-tablets. Selecteer een of meer hoogte-breedteverhoudingen met de gewenste resolutie- en doelgegevenssnelheid. |

#### Voorinstellingen batchset instellen bij uploaden {#setting-batch-set-presets-at-upload}

Als u automatisch een set afbeeldingen of een set rotaties wilt maken van geüploade afbeeldingen, klikt u op de kolom Actief voor de voorinstelling die u wilt gebruiken. U kunt meerdere voorinstellingen selecteren.

Zie [ Vormende Geplaatst vooraf instelt van de Partij om de Reeksen van het Beeld Auto-Genereren en de Reeksen van de Rotatie ](/help/assets/config-dms7.md#creating-batch-set-presets-to-auto-generate-image-sets-and-spin-sets) te leren meer over het creëren van partijreeks vooraf instelt.

### Gestroomde uploads {#streamed-uploads}

Als u veel middelen uploadt naar Adobe Experience Manager, nemen de I/O-verzoeken om de server drastisch toe. Hierdoor neemt de uploadefficiëntie af en kan er zelfs een time-out optreden bij sommige uploadtaken. [!DNL Experience Manager Assets] ondersteunt gestreamd uploaden van elementen. Gestroomd uploaden vermindert de schijf-I/O tijdens het uploaden door opslag van middelen in een tijdelijke map op de server te voorkomen voordat deze naar de opslagplaats wordt gekopieerd. In plaats daarvan worden de gegevens rechtstreeks naar de gegevensopslagruimte overgedragen. Op deze manier wordt de uploadtijd voor grote middelen en de mogelijkheid van time-outs verkort. Uploaden via streaming is standaard ingeschakeld in [!DNL Assets] .

>[!NOTE]
>
>Uploaden naar streaming is uitgeschakeld voor Adobe Experience Manager dat op de JEE-server wordt uitgevoerd met servlet-api-versie lager dan 3.1.

### ZIP-archief met elementen extraheren {#extractzip}

U kunt ZIP-archieven net als alle andere ondersteunde elementen uploaden. Dezelfde regels voor bestandsnaam gelden voor ZIP-bestanden. Met [!DNL Experience Manager] kunt u een ZIP-archief extraheren naar een DAM-locatie. Als de archiefbestanden geen ZIP als extensie bevatten, schakelt u detectie van bestandstypen met inhoud in.

Selecteer één ZIP-archief tegelijk, klik op **[!UICONTROL Extract Archive]** en selecteer een doelmap. Selecteer een optie die u eventueel wilt gebruiken voor het afhandelen van conflicten. Als de elementen in het ZIP-bestand in de doelmap staan, kunt u een van deze opties selecteren: extractie overslaan, bestaande bestanden vervangen, beide elementen behouden door een andere naam te geven of een versie te maken.

Nadat de extractie is voltooid, geeft [!DNL Experience Manager] een melding weer in het systeemvak. Terwijl [!DNL Experience Manager] het ZIP-bestand extraheert, kunt u teruggaan naar uw werk zonder de extractie te onderbreken.

![ Bericht van het dossier van het PIT extractie ](assets/Zip-extraction-notification.png)

Enkele beperkingen van de functie zijn:

* Als er op de bestemming een map met dezelfde naam staat, worden de elementen uit het ZIP-bestand geëxtraheerd naar de bestaande map.
* Als u de extractie annuleert, worden de reeds geëxtraheerde elementen niet verwijderd.
* U kunt niet twee ZIP-bestanden tegelijk selecteren en extraheren. U kunt slechts één ZIP-archief tegelijk extraheren.
* Wanneer het uploaden van een archief van het PIT, als de uploaddialoog een 500 serverfout toont, probeer na het installeren van [ het recentste Pak van de Dienst ](/help/release-notes/release-notes.md) opnieuw.

## Elementen voorvertonen {#previewing-assets}

Voer de volgende stappen uit om een voorvertoning van een element weer te geven.

1. Navigeer in de gebruikersinterface van [!DNL Assets] naar de locatie van het element waarvan u een voorvertoning wilt weergeven.
1. Klik op het gewenste element, zodat u het kunt openen.

1. Op de voorproefwijze, zijn de gezoemopties beschikbaar voor [ gesteunde types van Beeld ](/help/assets/assets-formats.md#supported-raster-image-formats) (met interactieve het uitgeven).

   Als u wilt inzoomen op een element, klikt u op `+` (of klikt u op het vergrootglas van het element). Klik op `-` om uit te zoomen. Wanneer u inzoomt, kunt u elk gebied van de afbeelding nauwkeurig bekijken door te pannen. Met de zoompijl opnieuw instellen keert u terug naar de oorspronkelijke weergave. Om de mening aan de originele grootte terug te stellen, klik **[!UICONTROL Reset]** ![ mening van het Terugstellen ](assets/do-not-localize/revert.png).

**activa van de Voorproef gebruikend toetsenbordsleutels slechts**

Voer de volgende stappen uit om een voorvertoning van een element weer te geven met het toetsenbord:

1. Navigeer vanuit de gebruikersinterface van [!DNL Assets] naar het gewenste element met `Tab` en de pijltoetsen.

1. Druk op de toets `Enter` op het gewenste element, zodat u het kunt openen. In de voorvertoningsmodus kunt u inzoomen op elementen.

1. Inzoomen op het element:
   1. Gebruik de toets `Tab` om de focus naar de inzoomoptie te verplaatsen.
   1. Gebruik de toets `Enter` om in te zoomen op de afbeelding.

   Als u wilt uitzoomen, gebruikt u de toets `Tab` om de focus op de optie Uitzoomen te plaatsen en drukt u op `Enter` .

1. Gebruik de toetsen `Shift` + `Tab` om de focus weer op de afbeelding te plaatsen.

1. Gebruik de pijltoetsen om de ingezoomde afbeelding te verplaatsen.

>[!MORELIKETHIS]
>
>* [ Voorproef Dynamic Media Assets ](/help/assets/previewing-assets.md).
>* [ subassets van de Mening ](managing-linked-subassets.md#viewing-subassets).

## Eigenschappen en metagegevens bewerken {#editing-properties}

1. Navigeer naar de locatie van het element waarvan u de metagegevens wilt bewerken.

1. Selecteer het element op de werkbalk en selecteer vervolgens **[!UICONTROL Properties]** , zodat u de eigenschappen van het element kunt bekijken. U kunt ook de handeling **[!UICONTROL Properties]** Snel op de elementenkaart kiezen.

   ![ Snelle actie van Eigenschappen op de mening van de activakaart ](assets/properties_quickaction.png)

1. Bewerk op de pagina [!UICONTROL Properties] de eigenschappen van de metagegevens onder verschillende tabbladen. Bewerk bijvoorbeeld onder het tabblad **[!UICONTROL Basic]** de titel en beschrijving.

   >[!NOTE]
   >
   >De indeling van de pagina [!UICONTROL Properties] en de beschikbare metagegevenseigenschappen zijn afhankelijk van het onderliggende metagegevensschema. Leren hoe te om de lay-out van de [!UICONTROL Properties] pagina te wijzigen, zie [ Schema&#39;s van Meta-gegevens ](/help/assets/metadata-schemas.md).

1. Gebruik de datumkiezer naast het veld **[!UICONTROL On Time]** om een bepaalde datum/tijd voor de activering van de asset te plannen.

   ![ de tijdplukker van de Datum of gebruikstoetsenbordsleutels op het gebied van de Tijd om datum en tijd voor activa activering toe te voegen ](assets/datepicker.png)

   *Cijfer: Gebruik de datumplukker om activa activering te plannen.*

1. Schakel **[!UICONTROL On/Off Time Reached]** in als u de triggers van de replicatieagent wilt bijwerken in de eigenschappen van metagegevens.
   ![ Montages van de Agent ](assets-dm/Agent-settings.png)

1. Als u het element na een bepaalde duur wilt deactiveren, kiest u de datum/tijd van deactivering in de datumkiezer naast het veld **[!UICONTROL Off Time]** . De deactiveringsdatum moet later zijn dan de activeringsdatum voor een element. Na [!UICONTROL Off Time] zijn een element en de bijbehorende uitvoeringen niet beschikbaar via de [!DNL Assets] -webinterface of via de HTTP-API.

1. Selecteer een of meer tags in het veld **[!UICONTROL Tags]** . Als u een aangepaste tag wilt toevoegen, typt u de naam van de tag in het vak en selecteert u `Enter` . De nieuwe tag wordt opgeslagen in [!DNL Experience Manager] . [!DNL YouTube] vereist dat codes worden gepubliceerd. Zie [ video&#39;s aan YouTube ](video.md#publishing-videos-to-youtube) publiceren.

   >[!NOTE]
   >
   >Als u tags wilt maken, hebt u schrijfmachtigingen nodig op `/content/cq:tags/default` in de CRX-opslagplaats.

1. Als u een waardering voor het element wilt opgeven, klikt u op het tabblad **[!UICONTROL Advanced]** en klikt u vervolgens op de gewenste positie op de ster om de gewenste waardering toe te wijzen.

   ![ Geavanceerd lusje in activaEigenschappen om classificatie ](assets/ratings.png) toe te wijzen

   De beoordelingsscore die u aan het element toewijst, wordt onder **[!UICONTROL Your Ratings]** weergegeven. De gemiddelde score voor waardering die het element heeft ontvangen van gebruikers die het element hebben beoordeeld, wordt weergegeven onder **[!UICONTROL Rating]** . Bovendien wordt de opsplitsing van de beoordelingsscores die bijdragen aan de gemiddelde score weergegeven onder **[!UICONTROL Rating Breakdown]** . U kunt middelen zoeken op basis van gemiddelde score.

1. Klik op het tabblad **[!UICONTROL Insights]** om gebruiksstatistieken voor het element weer te geven.

   De statistieken van het gebruik omvatten het volgende:

   * Aantal keer dat het element is weergegeven of gedownload
   * Kanalen/apparaten waardoor het middel werd gebruikt
   * Creatieve oplossingen waarbij het middel onlangs is gebruikt

   Voor meer details, zie [ de Inzichten van Assets ](/help/assets/asset-insights.md).

1. Klik op **[!UICONTROL Save & Close]**.
1. Navigeer naar de gebruikersinterface van [!DNL Assets] . De bewerkte eigenschappen van metagegevens, zoals titel, beschrijving, waarderingen, enzovoort, worden weergegeven op de elementenkaart in de Kaartweergave en onder de desbetreffende kolommen in de lijstweergave.

## Elementen kopiëren {#copying-assets}

Wanneer u een middel of een omslag kopieert, wordt het volledige middel of de omslag gekopieerd, samen met zijn inhoudsstructuur. Een gekopieerd middel of een omslag wordt gedupliceerd bij de doelplaats. Het element op de bronlocatie wordt niet gewijzigd.

Enkele kenmerken die uniek zijn voor een bepaalde kopie van een element, worden niet overgedragen. Enkele voorbeelden zijn:

* Element-id, aanmaakdatum en -tijd en versies en versiehistorie. Sommige van deze eigenschappen worden aangegeven door de eigenschappen `jcr:uuid` , `jcr:created` en `cq:name` .

* De aanmaaktijd en de paden waarnaar wordt verwezen, zijn uniek voor elk element en elke uitvoering ervan.

De andere eigenschappen en metagegevens blijven behouden. Er wordt geen gedeeltelijke kopie gemaakt wanneer een element wordt gekopieerd.

1. Selecteer een of meer elementen in de interface van [!DNL Assets] en klik op **[!UICONTROL Copy]** op de werkbalk. Alternatief, selecteer de **[!UICONTROL Copy]** ![ optie van het Exemplaar in toolbar in de interface van Assets ](assets/do-not-localize/copy_icon.png) snelle actie van de activakaart.

   >[!NOTE]
   >
   >Als u de snelle handeling van [!UICONTROL Copy] gebruikt, kunt u slechts één element tegelijk kopiëren.

1. Navigeer naar de locatie waar u de elementen wilt kopiëren.

   >[!NOTE]
   >
   >Als u een element op dezelfde locatie kopieert, genereert [!DNL Experience Manager] automatisch een variatie in de naam. Als u bijvoorbeeld een element met de naam `Square` kopieert, genereert [!DNL Experience Manager] automatisch de titel voor de kopie als `Square1` .

1. Klik de **[!UICONTROL Paste]** ![ optie van het Deeg in de werkbalk van Assets ](assets/do-not-localize/paste.png) activaoptie van de toolbar. Assets wordt vervolgens naar deze locatie gekopieerd.

   >[!NOTE]
   >
   >De optie **[!UICONTROL Paste]** is beschikbaar op de werkbalk totdat de plakbewerking is voltooid.

## Elementen verplaatsen en hernoemen {#moving-or-renaming-assets}

Wanneer u elementen (of mappen) naar een andere locatie verplaatst, worden de elementen (of mappen) tijdens het kopiëren van het element niet gedupliceerd. De elementen (of mappen) worden op de doellocatie geplaatst en worden van de bronlocatie verwijderd. U kunt de naam van het element ook wijzigen wanneer u het naar de nieuwe locatie verplaatst.
Als u een gepubliceerd element naar een andere locatie verplaatst, kunt u desgewenst het element opnieuw publiceren. Door gebrek beweeg verrichting op gepubliceerde activa maakt automatisch het ongedaan. Een verplaatst element wordt opnieuw gepubliceerd als de auteur de optie [!UICONTROL Republish] selecteert wanneer het element wordt verplaatst.

![ u kunt reeds gepubliceerd activa opnieuw publiceren wanneer het bewegen van het ](assets/republish-on-move.png)

Elementen of mappen verplaatsen:

1. Navigeer naar de locatie van het element dat u wilt verplaatsen.

1. Selecteer het element en klik op de optie **[!UICONTROL Move]** op de werkbalk.
   ![ optie van de Beweging in de toolbar van Assets ](assets/do-not-localize/move.png)

1. Voer een van de volgende handelingen uit in de wizard [!UICONTROL Move Assets] :

   * Geef de naam voor het element op nadat het is verplaatst. Klik vervolgens op **[!UICONTROL Next]** om door te gaan.

   * Klik op **[!UICONTROL Cancel]** om het proces te stoppen.

   >[!NOTE]
   >
   >* U kunt dezelfde naam opgeven voor het element als er geen element met die naam is op de nieuwe locatie. U moet echter een andere naam gebruiken als u het element verplaatst naar een locatie waar zich een element met dezelfde naam bevindt. Als u dezelfde naam gebruikt, genereert het systeem automatisch een variatie in de naam. Als uw element bijvoorbeeld de naam Vierkant heeft, genereert het systeem de naam Vierkant1 voor de kopie.
   >* Bij het wijzigen van de naam is witruimte niet toegestaan in de bestandsnaam.

1. Voer in het dialoogvenster **[!UICONTROL Select Destination]** een van de volgende handelingen uit:

   * Navigeer naar de nieuwe locatie voor de elementen en klik vervolgens op **[!UICONTROL Next]** om door te gaan.

   * Klik op **[!UICONTROL Back]** om terug te keren naar het **[!UICONTROL Rename]** -scherm.

1. Als de elementen die worden verplaatst, verwijzen naar pagina&#39;s, elementen of verzamelingen, wordt het tabblad **[!UICONTROL Adjust References]** weergegeven naast het tabblad **[!UICONTROL Select Destination]** .

   Voer een van de volgende handelingen uit op het scherm **[!UICONTROL Adjust References]** :

   * Geef op welke verwijzingen op basis van de nieuwe details moeten worden aangepast en klik op **[!UICONTROL Move]** om door te gaan.

   * In de kolom **[!UICONTROL Adjust]** selecteert of deselecteert u verwijzingen naar de elementen.
   * Klik op **[!UICONTROL Back]** om terug te keren naar het **[!UICONTROL Select Destination]** -scherm.

   * Klik op **[!UICONTROL Cancel]** om de verplaatsingsbewerking te stoppen.

   Als u verwijzingen niet bijwerkt, blijven ze naar het vorige pad van het element wijzen. Als u de referenties aanpast, worden deze bijgewerkt naar het nieuwe middelenpad.

### Elementen verplaatsen met behulp van sleepbewerking {#move-using-drag}

U kunt elementen (of mappen) naar een map op hetzelfde niveau verplaatsen door deze naar de doellocatie te slepen in plaats van de optie [!UICONTROL Move] in de gebruikersinterface te gebruiken. Deze bewerking is echter alleen mogelijk in de lijstweergave.

Als u elementen verplaatst door ze te slepen, wordt de wizard [!UICONTROL Move Asset] niet geopend. U krijgt daarom niet de optie om de naam van de elementen te wijzigen wanneer u deze verplaatst. Bovendien worden de reeds gepubliceerde elementen opnieuw gepubliceerd wanneer ze door slepen worden verplaatst, zonder dat de gebruiker toestemming moet vragen om ze opnieuw te publiceren.

![ Beweeg activa in het verwant omslagen door activa ](assets/move-by-drag.gif) te slepen

## Uitvoeringen beheren {#managing-renditions}

1. U kunt uitvoeringen voor een element toevoegen of verwijderen, behalve voor het origineel. Navigeer naar de locatie van het element waaraan u uitvoeringen wilt toevoegen of verwijderen.

1. Klik op het element zodat de bijbehorende pagina wordt geopend.
1. Selecteer **[!UICONTROL Renditions]** in de lijst in de interface Experience Manager.
1. Geef in het deelvenster **[!UICONTROL Renditions]** de lijst weer met uitvoeringen die voor het element zijn gegenereerd.

   ![ het paneel van Uitvoeringen op de pagina van het Detail van Assets ](assets/renditions_panel.png)

   >[!NOTE]
   >
   >Standaard geeft [!DNL Assets] de oorspronkelijke uitvoering van het element niet weer in de voorvertoningsmodus. Beheerders kunnen met overlays [!DNL Assets] originele uitvoeringen weergeven in de voorvertoningsmodus.

1. Selecteer een vertoning om de vertoning weer te geven of te verwijderen.

   **Schrap een vertoning**

   Selecteer een vertoning van het **[!UICONTROL Renditions]** paneel, en klik dan de **[!UICONTROL Delete Rendition]** ![ Optie om een vertoning ](assets/do-not-localize/deleteoutline.png) optie van de toolbar te schrappen. Uitvoeringen kunnen niet bulksgewijs worden verwijderd nadat de verwerking van het element is voltooid. Voor afzonderlijke elementen kunt u uitvoeringen handmatig uit de gebruikersinterface verwijderen. Voor meerdere elementen kunt u de Experience Manager aanpassen om bepaalde vertoningen te verwijderen of om de elementen te verwijderen en de verwijderde elementen opnieuw te uploaden.

   **upload een nieuwe vertoning**

   Navigeer aan de pagina van elementdetails voor de activa, en klik **[!UICONTROL Add Rendition]** ![ voeg vertoningsoptie toe om nieuwe vertoning ](assets/do-not-localize/add.png) optie in de toolbar te uploaden om een nieuwe vertoning voor de activa te uploaden.

   >[!NOTE]
   >
   >Als u een uitvoering selecteert in het deelvenster **[!UICONTROL Renditions]**, verandert de context van de werkbalk en worden alleen die acties weergegeven die relevant zijn voor de uitvoering. Opties, zoals de optie [!UICONTROL Upload Rendition] , worden niet weergegeven. Ga naar de pagina met details voor de asset om deze opties in de werkbalk weer te geven.

   U kunt de afmetingen configureren voor de vertoning die u wilt weergeven op de detailpagina van een afbeelding of video-element. Op basis van de afmetingen die u opgeeft, wordt de vertoning in [!DNL Assets] weergegeven met de exacte of dichtstbijzijnde afmetingen.

   Als u weergaveafmetingen van een afbeelding op het niveau van de assetdetails wilt configureren, overlapt u het knooppunt `renditionpicker` (`libs/dam/gui/content/assets/assetpage/jcr:content/body/content/content/items/assetdetail/items/col1/items/assetview/renditionpicker`) en configureert u de waarde van de breedte-eigenschap. Configureer de eigenschap **[!UICONTROL size (Long) in KB]** in plaats van de breedte, zodat u de uitvoering op de pagina met elementdetails kunt aanpassen op basis van de afbeeldingsgrootte. Voor aanpassing op basis van grootte wijst de eigenschap `preferOriginal` de voorkeur toe aan het origineel als de grootte van de overeenkomstige weergave groter is dan het origineel.

   Op dezelfde manier kunt u de afbeelding van de annotatiepagina aanpassen door `libs/dam/gui/content/assets/annotate/jcr:content/body/content/content/items/content/renditionpicker` te bedekken.

   ![ de knoop van de renditionpicker van de Bedekking in CRXDE om het beeld van de pagina van de Annotatie aan te passen ](assets/renditionpicker-node.png)

   Als u vertoningsafmetingen voor een video-element wilt configureren, navigeert u naar het knooppunt `videopicker` in de CRX-opslagplaats op de locatie `/libs/dam/gui/content/assets/assetpage/jcr:content/body/content/content/items/assetdetail/items/col1/items/assetview/videopicker` , bedekt u het knooppunt en bewerkt u de juiste eigenschap.

   >[!NOTE]
   >
   >Videoannotaties worden alleen ondersteund in browsers met video-indelingen die compatibel zijn met HTML5. Afhankelijk van de browser worden bovendien verschillende video-indelingen ondersteund. De MXF-video-indeling wordt echter nog niet ondersteund met video-annotaties.

Voor meer informatie over het produceren van en het bekijken van subassets, zie [ subassets ](managing-linked-subassets.md#generate-subassets) beheren.

## Elementen verwijderen {#deleting-assets}

Voor het verwijderen van elementen vereist een gebruiker verwijderingsmachtigingen voor `dam/asset` . Als u alleen over wijzigingsmachtigingen beschikt, kunt u alleen de metagegevens van de elementen bewerken en annotaties toevoegen aan het element. U kunt het element of de metagegevens echter niet verwijderen.

Als u de inkomende verwijzingen van andere pagina&#39;s wilt oplossen of verwijderen, werkt u de relevante verwijzingen bij voordat u een element verwijdert. Als u gebruikers niet wilt toestaan om waarnaar wordt verwezen, te verwijderen en verbroken koppelingen te behouden, schakelt u de optie voor het forceren verwijderen uit met behulp van een bedekking.

Middelen of mappen met elementen verwijderen:

1. Navigeer naar de locatie van het element of de map die u wilt verwijderen.

1. Selecteer de activa of de omslag, en klik **[!UICONTROL Delete]** ![ optie van de Schrapping ](assets/do-not-localize/deleteoutline.png) van de toolbar.

   Zodra u de schrapping bevestigt:

   * Als het element geen verwijzingen bevat, wordt het element verwijderd.

   * Als de activa verwijzingen heeft, informeert een fout-bericht u dat **Één of meerdere activa** van verwijzingen worden voorzien. U kunt **[!UICONTROL Force Delete]** of **[!UICONTROL Cancel]** selecteren.

   >[!NOTE]
   >
   >* Als u de inkomende verwijzingen van andere pagina&#39;s wilt oplossen of verwijderen, werkt u de relevante verwijzingen bij voordat u een element verwijdert. Schakel ook de optie voor forceren verwijderen uit met behulp van een overlay, zodat gebruikers geen bestanden waarnaar wordt verwezen kunnen verwijderen en verbroken koppelingen behouden blijven.
   >* Het is mogelijk om a *omslag* te schrappen die uitgecheckte activadossiers bevat. Voordat u een map verwijdert, moet u controleren of er geen digitale elementen zijn uitgecheckt door gebruikers.

>[!NOTE]
>
>Als u een map verwijdert met de bovenstaande methode uit de gebruikersinterface, worden ook de bijbehorende gebruikersgroepen verwijderd.
>
>Bestaande, redundante, ongebruikte en automatisch gegenereerde gebruikersgroepen kunnen echter worden opgeschoond vanuit de opslagplaats met de `clean` -methode in JMX in uw auteurinstantie (`https://[server]:[port]/system/console/jmx/com.day.cq.dam.core.impl.team%3Atype%3DClean+redundant+groups+for+Assets` ).

## Elementen downloaden {#downloading-assets}

Zie [ activa van de Download van Experience Manager ](/help/assets/download-assets-from-aem.md).

## Publish of publiceer elementen {#publish-assets}

Nadat u elementen hebt geüpload, verwerkt of bewerkt op de auteur van [!DNL Experience Manager] , publiceert u het element naar de publicatieserver. Met publicatie wordt het middel openbaar gemaakt. Met de actie Unpublishing is het element van de publicatieserver verwijderd, maar niet van de ontwerpserver.

Voor informatie specifiek voor [!DNL Dynamic Media], zie [ het publiceren  [!DNL Dynamic Media]  activa ](/help/assets/publishing-dynamicmedia-assets.md).

1. Navigeer naar de locatie van het element of de map met middelen die u wilt publiceren of die u uit de publicatieomgeving wilt verwijderen (publicatie ongedaan maken).

1. Selecteer de activa of de omslag die u wilt unpublish, en klik **[!UICONTROL Manage Publication]** ![ leiden publicatieoptie ](assets/do-not-localize/globe-publication.png) optie van de toolbar. Als u snel wilt publiceren, selecteert u de optie **[!UICONTROL Quick Publish]** op de werkbalk. Als de map die u wilt publiceren een lege map bevat, wordt de lege map niet gepubliceerd.

1. Selecteer de optie **[!UICONTROL Publish]** of **[!UICONTROL Unpublish]** naar wens.

   ![ unpublish actie ](assets/unpublish_action.png)
   *Cijfer: Publish en unpublish opties en de het plannen optie.*

1. Selecteer **[!UICONTROL Now]** om direct op het element te reageren of selecteer **[!UICONTROL Later]** om de actie te plannen. Selecteer een datum en tijd als u de optie **[!UICONTROL Later]** kiest. Klik op **[!UICONTROL Next]**.

1. Als een element bij het publiceren naar andere elementen verwijst, worden de bijbehorende verwijzingen in de wizard weergegeven. Alleen die verwijzingen worden weergegeven die niet zijn gepubliceerd of zijn gewijzigd sinds de laatste publicatie. Kies de referenties die u wilt publiceren.

1. Wanneer u de publicatie ongedaan maakt, kiest u de referenties die u ongedaan wilt maken wanneer een element naar andere elementen verwijst. Klik op **[!UICONTROL Unpublish]**. Klik in het bevestigingsdialoogvenster op **[!UICONTROL Cancel]** om de handeling te stoppen of klik op **[!UICONTROL Unpublish]** om te bevestigen dat de elementen op de opgegeven datum niet gepubliceerd moeten worden.

De volgende beperkingen en tips voor het publiceren of verwijderen van middelen of mappen zijn beschikbaar:

* De optie voor [!UICONTROL Manage Publication] is alleen beschikbaar voor gebruikersaccounts die replicatiemachtigingen hebben.
* Verwijder tijdens het verwijderen van de publicatie van een complex element alleen de publicatie van het element. Verwijder de publicatie van de verwijzingen niet omdat mogelijk naar deze verwijzingen wordt verwezen door andere gepubliceerde elementen.
* Lege mappen worden niet gepubliceerd.
* Als u een element publiceert dat wordt verwerkt, wordt alleen de oorspronkelijke inhoud gepubliceerd. De uitvoeringen ontbreken. Wacht tot de verwerking is voltooid en publiceer het element of publiceer het opnieuw nadat de verwerking is voltooid.

## Gesloten gebruikersgroep {#closed-user-group}

Een gesloten gebruikersgroep (CUG) wordt gebruikt om de toegang te beperken tot specifieke elementmappen die vanuit [!DNL Experience Manager] worden gepubliceerd. Als u een CUG maakt voor een map, is de toegang tot de map (inclusief mapelementen en submappen) beperkt tot alleen toegewezen leden of groepen. Om tot de omslag toegang te hebben, moeten zij login gebruikend hun veiligheidsgeloofsbrieven.

CUG&#39;s zijn een extra manier om de toegang tot uw elementen te beperken. U kunt ook een aanmeldingspagina voor de map configureren.

1. Selecteer een map in de interface van [!DNL Assets] en klik op de optie [!UICONTROL Properties] op de werkbalk, zodat u de pagina met eigenschappen kunt weergeven.
1. Voeg leden of groepen toe onder **[!UICONTROL Closed User Group]** op het tabblad **[!UICONTROL Permissions]** .

   ![ voeg gebruiker in gesloten gebruikersgroep ](assets/add_user.png) toe

1. Als u een aanmeldingsscherm wilt weergeven wanneer gebruikers de map openen, selecteert u de optie **[!UICONTROL Enable]** . Selecteer vervolgens het pad naar een aanmeldingspagina in [!DNL Experience Manager] en sla de wijzigingen op.

   ![ laat en selecteert login pagina toe om te tonen wanneer de gebruiker tot omslag ](assets/login_page.png) toegang heeft

   >[!NOTE]
   >
   >Als u het pad naar een aanmeldingspagina niet opgeeft, geeft [!DNL Experience Manager] de standaardaanmeldingspagina weer in de publicatie-instantie.

1. Publish de map en probeer deze te openen vanuit het publicatieexemplaar. Er wordt een aanmeldingsscherm weergegeven.
1. Als u lid van de GECG bent, ga uw veiligheidsgeloofsbrieven in. De map wordt weergegeven nadat [!DNL Experience Manager] u heeft geverifieerd.

## Zoeken in middelen {#assetsearch}

Het zoeken naar middelen staat centraal in het gebruik van een digitaal assetmanagementsysteem. Deze functionaliteit is belangrijk voor creatieve medewerkers, voor een robuust beheer van bedrijfsmiddelen door zakelijke gebruikers en marketeers, of voor beheer door DAM-beheerders.

Voor eenvoudige, geavanceerde, en douaneonderzoeken om de meest aangewezen activa te ontdekken en te gebruiken, zie [ onderzoeksactiva in Experience Manager ](search-assets.md).

## Snelle acties {#quick-actions}

De snelle actiepictogrammen zijn beschikbaar voor één middel tegelijkertijd. Voer afhankelijk van het apparaat de volgende handelingen uit om de snelactiepictogrammen weer te geven:

* Aanraakapparaten: aanraken en vasthouden. Op een iPad kunt u bijvoorbeeld een element selecteren en ingedrukt houden, zodat de snelle acties worden weergegeven.
* Niet-aanraakapparaten: Aanwijzer aanwijzen. Op een bureaubladapparaat wordt bijvoorbeeld de snelle actiebalk weergegeven als u de aanwijzer boven de elementminiatuur houdt.

### Navigeren en elementen selecteren {#navigating-and-selecting-assets}

Met de optie **[!UICONTROL Select]** kunt u elementen weergeven, doorbladeren en selecteren met een van de beschikbare weergaven (Kaart, Kolom en Lijst).

In de lijstweergave en de kolomweergave wordt de optie **[!UICONTROL Select]** weergegeven wanneer u de aanwijzer boven de elementminiatuur plaatst.

In de kaartweergave wordt de optie **[!UICONTROL Select]** als een snelle actie weergegeven.

Wanneer u in de gebruikersinterface van [!DNL Assets] in een browser door een map of verzameling bladert, kunt u alle weergegeven of geladen elementen selecteren met de optie [!UICONTROL Select All] in de rechterbovenhoek. In eerste instantie worden slechts 100 elementen in de kaartweergave geladen en worden 200 in de lijstweergave geladen. Er worden meer elementen in de weergave geladen wanneer u door de pagina met zoekresultaten bladert. Met de optie [!UICONTROL Select All] selecteert u alleen de geladen elementen.

Voor meer informatie, zie [ mening en het selecteren van uw middelen ](/help/sites-authoring/basic-handling.md#viewing-and-selecting-resources).

## Afbeeldingen bewerken {#editing-images}

Met de bewerkingsgereedschappen in de interface van [!DNL Assets] kunt u kleine bewerkingstaken uitvoeren op afbeeldingselementen. U kunt afbeeldingen uitsnijden, roteren, spiegelen en andere bewerkingstaken uitvoeren. U kunt ook afbeeldingen met hyperlinks toevoegen aan elementen.

>[!NOTE]
>
>Voor sommige componenten zijn er extra opties beschikbaar voor de modus Volledig scherm.

1. Voer een van de volgende handelingen uit om een element te openen in de bewerkingsmodus:

   * Selecteer het element en klik op **[!UICONTROL Edit]** op de werkbalk.
   * Klik op de optie **[!UICONTROL Edit]** die op een element in de kaartweergave wordt weergegeven.
   * Klik **[!UICONTROL Edit]** van de toolbar ![ uitgeven optie in toolbar ](assets/do-not-localize/edit_icon.png).

1. Om het beeld uit te snijden, klik **[!UICONTROL Crop]** ![ Optie om een beeld ](assets/do-not-localize/crop.png) uit te snijden.

1. Selecteer de gewenste optie in de lijst. Het uitsnijdgebied wordt op basis van de gekozen optie weergegeven in de afbeelding. Met de optie **Vrije hand** kunt u de afbeelding bijsnijden zonder beperkingen voor de hoogte-breedteverhouding.

1. Selecteer het gebied dat u wilt bijsnijden en wijzig de grootte of de positie van het gebied in de afbeelding.

1. Gebruik **[!UICONTROL Undo]** ![ ongedaan maken werkbalkoptie ](assets/do-not-localize/undo.png) en **[!UICONTROL Redo]** ![ opnieuw doe de opties van de toolbaroptie ](assets/do-not-localize/redo.png) om aan het uncropped beeld terug te keren of het bebouwde beeld, respectievelijk te behouden.
1. Klik op de desbetreffende optie **[!UICONTROL Rotate]** om de afbeelding rechtsom of linksom te roteren.

   ![ de met de klok mee en anti-wijzerzin roteren opties ](assets/do-not-localize/rotate-options.png)

1. Klik de aangewezen **[!UICONTROL Flip]** opties als u het beeld ![ horizontaal wilt omdraaien spiegelen horizontale optie ](assets/do-not-localize/flip-horizontal.png) of ![ verticaal ](assets/do-not-localize/flip-vertical.png) weerspiegelen verticale optie.

1. Om het beeld te voltooien die, **[!UICONTROL Finish]** ![ uitgeeft optie ](assets/do-not-localize/check-ok-done-icon.png) uitgeeft. Het klikken **beëindigt** begint ook de regeneratie van vertoningen.

>[!NOTE]
>
>Beeldbewerking wordt ondersteund voor de bestandsindelingen BMP, GIF, PNG en JPEG.

U kunt ook afbeeldingen met hyperlinks toevoegen met de afbeeldingseditor. Voor details, zie [ Toevoegend de Kaarten van het Beeld ](/help/assets/image-maps.md).

>[!NOTE]
>
>Om een TXT- dossier uit te geven, plaats **Dag CQ Verbinding Externalzer** van de Manager van de Configuratie.

## Tijdlijn {#timeline}

In de tijdlijn kunt u verschillende gebeurtenissen voor een geselecteerd item weergeven, zoals actieve workflows voor een element, opmerkingen/annotaties, activiteitenlogbestanden en versies.

![ de chronologieingangen van de Soort voor activa ](assets/sort_timeline.gif)

*Cijfer: De chronologieingangen van de soort voor een activa.*

>[!NOTE]
>
>In de [ console van Inzamelingen ](/help/assets/manage-collections.md#navigating-the-collections-console), verstrekt de **[!UICONTROL Show All]** lijst opties om commentaren en werkschema&#39;s slechts te bekijken. Bovendien wordt de chronologie getoond slechts voor top-level inzamelingen die in de console vermeld zijn. Deze wordt niet weergegeven als u in een van de verzamelingen navigeert.

>[!NOTE]
>
>De Chronologie bevat verscheidene [ opties specifiek voor inhoudsfragmenten ](/help/assets/content-fragments/content-fragments-managing.md#timeline-for-content-fragments).

## Elementen notities aanbrengen {#annotating}

Annotaties zijn opmerkingen of toelichtingen die aan afbeeldingen of video&#39;s worden toegevoegd. Annotaties bieden marketers de mogelijkheid samen te werken en feedback over middelen te geven.

Videoannotaties worden alleen ondersteund in browsers met video-indelingen die compatibel zijn met HTML5. Welke video-indelingen door [!DNL Assets] worden ondersteund, is afhankelijk van de browser. De MXF-video-indeling wordt echter nog niet ondersteund met video-annotaties.

>[!NOTE]
>
>Voor de Fragmenten van de Inhoud, [ worden de annotaties gecreeerd in de fragmentredacteur ](/help/assets/content-fragments/content-fragments-variations.md#annotating-a-content-fragment).

1. Navigeer naar de locatie van het element waaraan u annotaties wilt toevoegen.
1. Klik op de optie **[!UICONTROL Annotate]** van een van de volgende opties:

   * [Snelle acties](/help/assets/manage-assets.md#quick-actions)
   * Selecteer het element op de werkbalk of navigeer naar de elementpagina.

1. Voeg een opmerking toe in het vak **[!UICONTROL Comment]** onder aan de tijdlijn. U kunt ook een gebied in de afbeelding markeren en een annotatie toevoegen in het dialoogvenster **[!UICONTROL Add Annotation]**.

1. Als u een gebruiker op de hoogte wilt stellen van een aantekening, geeft u het e-mailadres van de gebruiker op en voegt u de opmerking toe. Als u Aaron MacDonald bijvoorbeeld wilt informeren over een annotatie, voert u @aa in. Tips voor alle overeenkomende gebruikers worden weergegeven in een lijst. Selecteer het e-mailadres van Aaron in de lijst zodat u de persoon met de opmerking kunt voorzien van tags. Op dezelfde manier kunt u meer gebruikers overal in de annotatie of ervoor of erna een tag toewijzen.

   ![ specificeer het e-mailadres van de gebruiker en voeg commentaar toe om gebruiker ](assets/annotate-gif.gif) op de hoogte te brengen

   >[!NOTE]
   >
   >Voor een gebruiker zonder beheerder worden de suggesties alleen weergegeven als de gebruiker leesmachtigingen heeft op het pad `/home` in CRXDE.

1. Nadat u de annotatie hebt toegevoegd, klikt u op **[!UICONTROL Add]** om deze op te slaan. Een kennisgeving voor de aantekening wordt verzonden naar Aaron.

   >[!NOTE]
   >
   >U kunt meerdere annotaties toevoegen voordat u ze opslaat.

1. Klik op **[!UICONTROL Close]** om de annotatiemodus te verlaten.
1. Meld u aan bij [!DNL Assets] met de gegevens van Aaron MacDonald en klik op de optie **[!UICONTROL Notifications]** om het bericht weer te geven.

   >[!NOTE]
   >
   >U kunt ook annotaties toevoegen aan video-elementen. Tijdens het annoteren van video&#39;s pauzeert de speler zodat u notities kunt aanbrengen in een frame. Voor details, zie [ het leiden videoactiva ](/help/assets/managing-video-assets.md). MXF-video-indeling wordt nog niet ondersteund met videoannotaties.

1. Als u een andere kleur wilt kiezen, zodat u onderscheid kunt maken tussen gebruikers, klikt u op de optie Profiel en klikt u op **[!UICONTROL My Preferences]** .

   ![ Uitgezochte optie van het gebruikersprofiel en toen Mijn Voorkeur om de Voorkeur van de Gebruiker te openen ](assets/User-profile-preferences.png)

   Geef de gewenste kleur op in het vak **[!UICONTROL Annotation Color]** en klik op **[!UICONTROL Accept]** .

   ![ Uitgezochte annotatiekleur in de Voorkeur van de Gebruiker om de kleur van de Persoon van de Gebruiker te plaatsen ](assets/Annotation-color.png)

>[!NOTE]
>
>U kunt ook annotaties toevoegen aan een verzameling. Als een verzameling onderliggende verzamelingen bevat, kunt u echter alleen annotaties/opmerkingen aan de bovenliggende verzameling toevoegen. De optie Annoteren is niet beschikbaar voor onderliggende verzamelingen.

### Opgeslagen annotaties weergeven {#viewing-saved-annotations}

U kunt slechts één annotatie tegelijk weergeven.

>[!NOTE]
>
>Als u meerdere annotaties selecteert, wordt de laatste annotatie weergegeven in de gebruikersinterface.
>
>Multi-select wordt alleen ondersteund voor het afdrukken van het geannoteerde element als PDF.

**aan mening bewaarde aantekeningen voor een activa:**

1. Ga naar de locatie van het element en open de elementpagina.

1. Kies **[!UICONTROL Timeline]** in de interface Experience Manager.
1. Selecteer in de lijst **[!UICONTROL Show All]** in de tijdlijn de optie **[!UICONTROL Comments]** om de resultaten te filteren op basis van annotaties.

   Klik op een opmerking in het deelvenster **[!UICONTROL Timeline]** als u de bijbehorende annotatie in de afbeelding wilt bekijken.

   ![ paneel van de Chronologie aan meningsaantekening op beeld ](assets/timeline-view-annotations.png)

   Klik op **[!UICONTROL Delete]** om een bepaalde opmerking te verwijderen.

### Annotaties afdrukken {#printing-annotations}

Als een element annotaties heeft of een revisiewerkstroom heeft ondergaan, kunt u het element samen met annotaties afdrukken en de status controleren als een PDF-bestand voor offline revisie.

U kunt ook alleen de annotaties of de revisiestatus afdrukken.

>[!NOTE]
>
>U kunt meerdere annotaties selecteren wanneer u het geannoteerde element afdrukt als PDF.

Als u de annotaties en de revisiestatus wilt afdrukken, klikt u op **[!UICONTROL Print]** en volgt u de instructies in de wizard. De optie **[!UICONTROL Print]** wordt alleen op de werkbalk weergegeven als aan het element ten minste één aantekening of revisiestatus is toegewezen.

1. Open vanuit de interface van [!DNL Assets] de voorvertoningspagina voor een element.
1. Voer een van de volgende handelingen uit:

   * Als u alle annotaties en de revisiestatus wilt afdrukken, slaat u stap 3 over en gaat u rechtstreeks naar stap 4.
   * Om specifieke annotaties en overzichtsstatus te drukken, open de [ chronologie ](/help/assets/manage-assets.md#timeline) en ga dan naar stap 3.

1. Als u specifieke annotaties wilt afdrukken, selecteert u de annotaties in de tijdlijn.

   ![ selecteer een aantekening van Chronologie om het ](assets/timeline-select-annotations.png) te drukken

   Als u alleen de revisiestatus wilt afdrukken, selecteert u deze in de tijdlijn.

1. Klik op **[!UICONTROL Print]** op de werkbalk.

1. Kies in het dialoogvenster Afdrukken de positie waarop u de annotaties/revisiestatus wilt weergeven op de PDF. Bijvoorbeeld, als u de annotaties/status bij het hoogste recht van de pagina wilt worden gedrukt die het gedrukte beeld bevat, gebruik **Top-Left** het plaatsen. Deze optie is standaard geselecteerd.

   U kunt andere instellingen kiezen, afhankelijk van de positie waar u de annotaties/status wilt weergeven in de afgedrukte PDF. Kies **[!UICONTROL Next Page]** als u de annotaties/status wilt weergeven op een pagina die gescheiden is van de afgedrukte asset.

1. Klik op **[!UICONTROL Print]**. Afhankelijk van de optie die u kiest in stap 2, geeft de gegenereerde PDF de annotaties/status op de opgegeven positie weer. Als u bijvoorbeeld zowel annotaties als de revisiestatus wilt afdrukken met de instelling **Linksboven**, lijkt de gegenereerde uitvoer op het PDF-bestand dat hier wordt weergegeven.

   ![ Annotatie en revisiestatus op geproduceerde PDF ](assets/annotation-status-pdf.png)

1. De optie van de Download ![ Download voor PDF ](assets/do-not-localize/download.png) of druk ![ drukopties op PDF ](assets/do-not-localize/print.png) de PDF gebruikend de opties bij top-right.

   >[!NOTE]
   >
   >Als het element subelementen bevat, kunt u alle subelementen samen met de specifieke paginagewijze annotaties afdrukken.

   Als u de weergave van het gerenderde PDF-bestand wilt bewerken, bijvoorbeeld de lettertypekleur, -grootte en -stijl, opent u **[!UICONTROL Annotation PDF configuration]** in Configuration Manager en wijzigt u de gewenste opties. Als u bijvoorbeeld de weergavekleur van de goedgekeurde status wilt wijzigen, wijzigt u de kleurcode in het desbetreffende veld. Voor informatie rond het veranderen van de doopvontkleur van annotaties, zie [ het Annoteren ](/help/assets/manage-assets.md#annotating).

   ![ Configuratie om activaannotatie op het document van PDF ](assets/annotation-print-pdf-config.png) te drukken

   Ga terug naar het gerenderde PDF-bestand en vernieuw het. De vernieuwde PDF geeft de wijzigingen weer die u hebt aangebracht.

Als een element annotaties in vreemde talen bevat (vooral niet-Latijnse talen), moet u eerst de service CQ-DAM-Handler-Gibson Font Manager op de [!DNL Experience Manager] -server configureren om deze annotaties af te drukken. Geef bij het configureren van de service CQ-DAM-Handler-Gibson Font Manager het pad op waar de lettertypen voor de gewenste talen zich bevinden.

1. Open de configuratiepagina CQ-DAM-Handler-Gibson Font Manager Service via de URL `https://[aem_server]:[port]/system/console/configMgr/com.day.cq.dam.handler.gibson.fontmanager.impl.FontManagerServiceImpl` .
1. Voer een van de volgende handelingen uit om CQ-DAM-Handler-Gibson Font Manager Service te configureren:

   * Geef in de directory System Fonts (Systeemlettertypen) het volledige pad naar de map Fonts op uw systeem op. Bijvoorbeeld, als u een gebruiker van Mac bent, kunt u de weg als *specificeren/Bibliotheek/Doopvonten* in de de folderoptie van de Doopvonten van het Systeem. [!DNL Experience Manager] haalt de lettertypen op uit deze map.
   * Maak een map met de naam `fonts` in de map `crx-quickstart` . CQ-DAM-Handler-Gibson Font Manager Service haalt de lettertypen automatisch op de locatie `crx-quickstart/fonts` op. U kunt dit standaardpad overschrijven vanuit de directory Adobe Server Fonts.

   * Maak een map voor lettertypen op uw systeem en sla de gewenste lettertypen op in de map. Geef vervolgens het volledige pad naar die map op in de directory met lettertypen voor klanten.

1. Open de configuratie van de PDF van de Annotatie via de URL `https://[aem_server]:[4502]/system/console/configMgr/com.day.cq.dam.core.impl.annotation.pdf.AnnotationPdfConfig` .
1. Configureer de PDF Annotation met de juiste set lettertypen als volgt:

   * Neem de tekenreeks `<font_family_name_of_custom_font, sans-serif>` op in de optie voor lettertypefamilie. Als u bijvoorbeeld annotaties wilt afdrukken in CJK (Chinees, Japans en Koreaans), neemt u de tekenreeks `Arial Unicode MS, Noto Sans, Noto Sans CJK JP, sans-serif` op in de optie voor lettertypefamilies. Als u annotaties wilt afdrukken in het Hindi, downloadt u het juiste lettertype en configureert u de lettertypefamilie als Arial® Unicode MS®, Noto Sans, Noto Sans CJK JP, Noto Sans Devanagari, sans-serif.

1. Start de [!DNL Experience Manager] -implementatie opnieuw.

Hier volgt een voorbeeld van hoe u [!DNL Experience Manager] kunt configureren voor het afdrukken van annotaties in CJK (Chinees, Japans en Koreaans):

1. Download Google Noto CJK-lettertypen van de volgende koppelingen en sla deze op in de lettertypemap die is geconfigureerd in Font Manager Service.

   * Alles in Één Super CJK doopvont: [ https://fonts.google.com/noto/use](https://fonts.google.com/noto/use)
   * Noto Sans (voor Europese talen): [ https://fonts.google.com/noto](https://fonts.google.com/noto)
   * Noto doopvonten voor een taal van uw keus: [ https://fonts.google.com/noto](https://fonts.google.com/noto)

1. Configureer het PDF-bestand voor annotaties door de parameter font-family in te stellen op `Arial Unicode MS, Noto Sans, Noto Sans CJK JP, sans-serif` . Deze configuratie is standaard beschikbaar en werkt voor alle Europese en CJK-talen.
1. Als de taal van uw keuze afwijkt van de talen die in stap 2 worden genoemd, voegt u een toepasselijke (door komma&#39;s gescheiden) vermelding toe aan de standaardlettertypefamilie.

## Elementversies maken, beheren, voorvertonen en herstellen {#asset-versioning}

Met Versioning maakt u een momentopname van digitale elementen op een bepaald tijdstip. Versioning helpt bij het later herstellen van elementen naar een vorige status. Als u bijvoorbeeld een wijziging in een element ongedaan wilt maken, herstelt u de onbewerkte versie van het element. In [!DNL Experience Manager] kunt u een versie maken, de huidige revisie bekijken, verschillen tussen twee versies van afbeeldingen naast elkaar weergeven en een element terugzetten naar de vorige versie.

In de volgende gevallen kunt u versies maken in [!DNL Experience Manager] :

* Upload een element met dezelfde bestandsnaam die op dezelfde locatie bestaat. Dit kan een nieuw element of een gewijzigde versie van hetzelfde element zijn.
* Bewerk een afbeelding in [!DNL Experience Manager] en sla de wijzigingen op.
* Bewerk de metagegevens van een element.
* Gebruik [!DNL Experience Manager] Desktop app om bestaande activa uit te checken, het uit te geven, en [ uploadt uw veranderingen ](https://experienceleague.adobe.com/docs/experience-manager-desktop-app/using/using.html#edit-assets-upload-updated-assets).

U kunt automatische versioning ook inschakelen via een workflow. Wanneer u een versie voor een element maakt, worden de metagegevens en de uitvoeringen samen met de versie opgeslagen. Uitvoeringen zijn alternatieven voor dezelfde afbeeldingen, bijvoorbeeld een PNG-uitvoering van een geüpload JPEG-bestand.

1. Navigeer naar de locatie van het element waarvoor u een versie wilt maken en klik erop om de voorvertoning te openen. Open in de linkerbovenhoek van de pagina het menu en selecteer **[!UICONTROL Timeline]** .

   ![ van het linkernavigatiemenu, uitgezochte chronologieoptie ](assets/timeline.png)

   *Cijfer: Open menu van upper-left gebied van pagina en selecteer [!UICONTROL Timeline] optie.*

1. Een versie van het element maken:

   * Klik op **[!UICONTROL Actions]** onderaan.
   * Klik op **[!UICONTROL Save as Version]** om een versie voor het element te maken. Voeg desgewenst een label en opmerking toe.
   * Klik op **[!UICONTROL Create]** om een versie te maken.

     ![ creeer activaversie van sidebar ](assets/create-new-version-from-timeline.png)

     *Cijfer: Creeer een versie van een activa van [!UICONTROL Timeline] linkerzijbalk.*

1. Een versie van een element weergeven:

   * Klik op **[!UICONTROL Show All]** in [!UICONTROL Timeline] .
   * Klik op **[!UICONTROL Versions]**. Alle versies die voor een element zijn gemaakt, worden weergegeven in de linkerzijbalk.

   * Selecteer een specifieke versie van het element en klik op **[!UICONTROL Preview Version]** .

1. Ga als volgt te werk om terug te keren naar een oudere versie van het element. Na het terugdraaien wordt deze versie weergegeven in de [!DNL Assets] -interface en is deze beschikbaar voor gebruik.

   * Klik op een versie van het element. Voeg desgewenst een label en een opmerking toe.
   * Klik op **[!UICONTROL Revert to this Version]**.

     ![ Uitgezochte een versie om aan het terug te keren ](assets/select_version.png)

     *Cijfer: Selecteer een versie en keer aan het terug. Het wordt de huidige versie die dan aan de gebruikers DAM beschikbaar is.*

1. Voer de volgende stappen uit om twee versies van een afbeelding te vergelijken:
   * Klik op de versie die u met de huidige versie wilt vergelijken.
   * Sleep de schuifregelaar naar links om deze versie over de huidige versie heen te plaatsen en te vergelijken.

   ![ schuif van het Gebruik om de geselecteerde versies van een activa met de huidige versie ](assets/version-slider.gif) te vergelijken

   *Cijfer: De schuif van het gebruik om de geselecteerde versies van activa met de huidige versie moeiteloos te vergelijken.*

### Een workflow op een element starten {#starting-a-workflow-on-an-asset}

Om een werkschema toe te passen om activa te verwerken, zie [ werkschema beginnen op een activa ](/help/assets/assets-workflow.md#apply-a-workflow-to-an-asset).

## Verzamelingen {#collections}

Een verzameling is een geordende set elementen. Gebruik verzamelingen om gerelateerde elementen te delen tussen gebruikers of om vergelijkbare elementen te groeperen voor eenvoudige detectie.

* Een verzameling kan elementen van verschillende locaties bevatten, omdat deze alleen verwijzingen naar deze elementen bevatten. Bij elke verzameling blijft de referentiële integriteit van de elementen behouden.
* U kunt verzamelingen delen met meerdere gebruikers met verschillende machtigingsniveaus, zoals bewerken, weergeven, enzovoort.

Om details van het beheer van de Inzameling te kennen, zie [ digitale activa inzamelingen ](/help/assets/manage-collections.md) beheren.

## Verlopen elementen verbergen bij weergave van elementen in bureaubladtoepassing of Adobe Asset Link {#hide-expired-assets-via-acp-api}

Met de bureaubladtoepassing [!DNL Experience Manager] hebt u toegang tot de DAM-opslagruimte vanaf een desktopcomputer van Windows of Mac. Met Adobe Asset Link hebt u toegang tot elementen vanuit de ondersteunde [!DNL Creative Cloud] -bureaubladtoepassingen.

Wanneer u elementen bladert vanuit de gebruikersinterface van [!DNL Experience Manager] , worden de verlopen elementen niet weergegeven. Beheerders kunnen de volgende configuratie uitvoeren om te voorkomen dat verlopen middelen worden weergegeven, gezocht en opgehaald wanneer ze middelen zoeken vanuit de bureaubladtoepassing en de Asset Link. De configuratie werkt voor alle gebruikers, ongeacht beheerderrechten.

Voer het volgende bevel CURL uit. Zorg ervoor dat gebruikers die toegang hebben tot elementen, via `/conf/global/settings/dam/acpapi/` toegang hebben tot het bestand. Gebruikers die deel uitmaken van een `dam-user` -groep hebben standaard de juiste machtigingen.

```curl
curl -v -u admin:admin --location --request POST 'http://localhost:4502/conf/global/settings/dam/acpapi/configuration/_jcr_content' \
--header 'Content-Type: application/x-www-form-urlencoded' \
--data-urlencode 'jcr:title=acpapiconfig' \
--data-urlencode 'hideExpiredAssets=true' \
--data-urlencode 'hideExpiredAssets@TypeHint=Boolean' \
--data-urlencode 'jcr:primaryType=nt:unstructured' \
--data-urlencode '../../jcr:primaryType=sling:Folder'
```

Om meer te weten, zie hoe te [ activa doorbladeren DAM gebruikend Desktop app ](https://experienceleague.adobe.com/docs/experience-manager-desktop-app/using/using.html#browse-search-preview-assets) en [ hoe te om de Verbinding van Activa van de Adobe te gebruiken ](https://helpx.adobe.com/nl/enterprise/using/manage-assets-using-adobe-asset-link.html).
