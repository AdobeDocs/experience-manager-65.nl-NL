---
title: Uw digitale middelen beheren
description: Leer de taken voor middelenbeheer, zoals het uploaden, downloaden, bewerken, zoeken, verwijderen, notities aanbrengen en de versie van uw digitale middelen.
contentOwner: AG
mini-toc-levels: 1
translation-type: tm+mt
source-git-commit: 863d1bd3f0f188153fcbbb7256d3ac2e3b247f59
workflow-type: tm+mt
source-wordcount: '9358'
ht-degree: 3%

---


# Uw digitale middelen beheren {#manage-digital-assets}

In [!DNL Adobe Experience Manager Assets] kunt u meer doen dan alleen uw activa opslaan en beheren. [!DNL Experience Manager] biedt mogelijkheden voor middelenbeheer op bedrijfsniveau. U kunt elementen bewerken en delen, geavanceerde zoekopdrachten uitvoeren, meerdere uitvoeringen van tientallen ondersteunde bestandsindelingen maken, versies en digitale rechten beheren, de verwerking van elementen automatiseren, metagegevens beheren en besturen, samenwerken met annotaties en nog veel meer.

In dit artikel worden de basistaken voor middelenbeheer beschreven, zoals het maken of uploaden van bedrijfsmiddelen. updates van metagegevens; kopiëren, verplaatsen en verwijderen; publiceert, publiceert en doorzoekt elementen. Om het gebruikersinterface te begrijpen, zie [begin met activa gebruikersinterface](/help/sites-authoring/basic-handling.md). Zie [Content Fragments](/help/assets/content-fragments/content-fragments-managing.md) assets beheren voor het beheren van inhoudsfragmenten.

## Mappen {#creating-folders} maken

Wanneer u een verzameling elementen ordent, bijvoorbeeld alle `Nature`-afbeeldingen, kunt u mappen maken om deze bij elkaar te houden. U kunt mappen gebruiken om uw elementen te categoriseren en in te delen. [!DNL Experience Manager Assets] vereist niet dat u elementen in mappen ordent om beter te werken.

>[!NOTE]
>
>* Het delen van een [!DNL Assets] omslag van het type `sling:OrderedFolder` wordt niet gesteund wanneer het delen aan Marketing Cloud. Als u een map wilt delen, selecteert u [!UICONTROL Ordered] niet bij het maken van een map.
>* [!DNL Experience Manager] staat het gebruik van  `subassets` woord als naam van een map niet toe. Het is een gereserveerd sleutelwoord voor knoop die subassets voor samengestelde activa bevatten.


1. Navigeer naar de plaats in de map met digitale elementen waar u een nieuwe map wilt maken. Klik in het menu op **[!UICONTROL Create]**. Selecteer **[!UICONTROL New Folder]**.
1. Geef in het veld **[!UICONTROL Title]** een mapnaam op. Standaard gebruikt DAM de titel die u als mapnaam hebt opgegeven. Nadat de map is gemaakt, kunt u de standaardinstelling overschrijven en een andere mapnaam opgeven.
1. Klik op **[!UICONTROL Create]**. De map wordt weergegeven in de map met digitale middelen.

De volgende tekens (lijst met door spaties gescheiden tekens) worden niet ondersteund:

* De naam van een elementbestand mag geen van de volgende tekens bevatten: `* / : [ \\ ] | # % { } ? &`
* De naam van een elementmap mag geen van de volgende tekens bevatten: `* / : [ \\ ] | # % { } ? \" . ^ ; + & \t`

Voeg geen speciale tekens toe aan de extensies van de bestandsnamen van elementen.

## Elementen uploaden {#uploading-assets}

<!-- TBD the following:
Move this section into a new article. CQDOC-14874 ticket is created for this.
In this complete article, replace emphasis with UICONTROL where appropriate.
-->

U kunt verschillende typen elementen (zoals afbeeldingen, PDF-bestanden, RAW-bestanden, enzovoort) uploaden van uw lokale map of een netwerkstation naar [!DNL Experience Manager Assets].

>[!NOTE]
>
>In de modus Dynamic Media - Scene7 kunt u alleen elementen uploaden waarvan de bestandsgrootte 2 GB of minder is.

U kunt ervoor kiezen elementen te uploaden naar mappen waaraan al dan niet een verwerkingsprofiel is toegewezen.

Voor mappen waaraan een verwerkingsprofiel is toegewezen, wordt de profielnaam weergegeven op de miniatuur in de kaartweergave. In de lijstweergave wordt de profielnaam weergegeven in de kolom **Profiel verwerken**. Zie [Profielen verwerken](/help/assets/processing-profiles.md).

Voordat u een element uploadt, moet u ervoor zorgen dat dit zich in de [indeling](/help/assets/assets-formats.md) bevindt die [!DNL Experience Manager Assets] ondersteunt.

1. Navigeer in de gebruikersinterface [!DNL Assets] naar de locatie waar u digitale elementen wilt toevoegen.
1. Voer een van de volgende handelingen uit om de elementen te uploaden:

   * Klik op **[!UICONTROL Create]** op de werkbalk. Klik vervolgens op **[!UICONTROL Files]** in het menu. U kunt de naam van het bestand desgewenst wijzigen in het dialoogvenster dat verschijnt.
   * In browser die HTML5 steunt, sleep de activa direct op [!DNL Assets] gebruikersinterface. Het dialoogvenster voor het wijzigen van de naam van het bestand wordt niet weergegeven.

   ![Optie maken om elementen te uploaden](assets/create-options.png)

   Als u meerdere bestanden wilt selecteren, selecteert u `Ctrl` of `Command` en selecteert u de elementen in het dialoogvenster Bestandenkiezer. Als u een iPad gebruikt, kunt u slechts één bestand tegelijk selecteren.

   U kunt het uploaden van grote elementen (groter dan 500 MB) pauzeren en later vanaf dezelfde pagina hervatten. Klik op **[!UICONTROL Pause]** naast de voortgangsbalk die wordt weergegeven wanneer het uploaden start.

   ![Voortgangsbalk voor elementen uploaden](assets/upload-progress-bar.png)

De omvang waarboven een actief als een groot actief wordt beschouwd, kan worden geconfigureerd. U kunt het systeem bijvoorbeeld zodanig configureren dat elementen boven 1000 MB (in plaats van 500 MB) als grote elementen worden beschouwd. In dit geval wordt **[!UICONTROL Pause]** weergegeven op de voortgangsbalk wanneer bestanden van meer dan 1000 MB worden geüpload.

De optie [!UICONTROL Pause] wordt niet weergegeven als een bestand van meer dan 1000 MB wordt geüpload met een bestand van minder dan 1000 MB. Als u echter de bestandsupload van minder dan 1000 MB annuleert, wordt de optie **[!UICONTROL Pause]** weergegeven.

Als u de formaatlimiet wilt wijzigen, configureert u de eigenschap `chunkUploadMinFileSize` van het `fileupload`knooppunt in de CRX-opslagruimte.

Wanneer u **[!UICONTROL Pause]** klikt, schakelt het aan de **[!UICONTROL Play]** optie van een knevel. Klik op **[!UICONTROL Play]** om het uploaden te hervatten.

![Het gepauzeerde uploaden van elementen hervatten](assets/resume-paused-upload.png)

Als u een actieve upload wilt annuleren, klikt u op Sluiten (`X`) naast de voortgangsbalk. Wanneer u de uploadbewerking annuleert, verwijdert [!DNL Assets] het gedeeltelijk geüploade gedeelte van het element.

De mogelijkheid om het uploaden te hervatten is vooral handig in scenario&#39;s met lage bandbreedte en netwerkstoringen, waarbij het uploaden van een groot element veel tijd in beslag neemt. U kunt het uploaden pauzeren en verdergaan wanneer de situatie verbetert. Wanneer u het document hervat, begint het uploaden vanaf het punt waarop u het hebt gepauzeerd.

Tijdens het uploaden slaat [!DNL Experience Manager] de delen van het element dat wordt geüpload op als stukjes gegevens in de CRX-opslagplaats. Wanneer het uploaden is voltooid, worden deze fragmenten door [!DNL Experience Manager] geconsolideerd in één gegevensblok in de gegevensopslagruimte.

Ga naar `https://[aem_server]:[port]/system/console/configMgr/org.apache.sling.servlets.post.impl.helper.ChunkCleanUpTask` om de opschoningstaak voor de onvoltooide taken voor het uploaden van taken te configureren.

>[!CAUTION]
>
>De standaardwaarde wanneer de brokkenupload wordt teweeggebracht is 500 MB en de brokgrootte is 50 MB. Als u [Apache Jackrabbit Oak TokenConfiguration](https://helpx.adobe.com/experience-manager/kb/How-to-set-token-session-expiration-AEM.html) wijzigt om `timeout configuration` in te stellen op minder dan de tijd die nodig is voor het uploaden van een element, dan kunt u een sessietime-outsituatie tegenkomen terwijl het uploaden van het element bezig is. Daarom moet u `chunkUploadMinFileSize` en `chunksize` veranderen, zodat elk brokkenverzoek de zitting vernieuwt.
>
>Op basis van de time-out bij verlopen van de referentie, de latentie, de bandbreedte en de verwachte gelijktijdige uploads, wordt de hoogste waarde gekozen waarmee u ervoor kunt zorgen dat het volgende wordt gekozen:
>
>* Om ervoor te zorgen dat het uploaden van brokken is ingeschakeld voor bestanden met grootten die tijdens het uploaden waarschijnlijk resulteren in een vervaldatum van de referentie.
   >
   >
* Om ervoor te zorgen dat elk segment eindigt alvorens de referentie verloopt.


Als u een element uploadt met dezelfde naam als een element dat al beschikbaar is op de locatie waar u het element uploadt, wordt een waarschuwingsvenster weergegeven.

U kunt een bestaand element vervangen, een andere versie maken of beide behouden door de naam van het nieuwe element dat wordt geüpload te wijzigen. Als u een bestaand element vervangt, worden de metagegevens voor het element en eventuele eerdere wijzigingen (bijvoorbeeld notities aanbrengen of uitsnijden) die u in het bestaande element hebt aangebracht, verwijderd. Als u ervoor kiest beide elementen te behouden, wordt de naam van het nieuwe element gewijzigd in het nummer `1` dat aan de naam wordt toegevoegd.

![Het dialoogvenster Naam conflict openen om het conflict tussen de namen van elementen op te lossen](assets/resolve-naming-conflict.png)

>[!NOTE]
>
>Als u **[!UICONTROL Replace]** selecteert in het dialoogvenster [!UICONTROL Name Conflict], wordt de element-id opnieuw gegenereerd voor het nieuwe element. Deze id verschilt van de id van het vorige element.
>
>Als Asset Insights is ingeschakeld voor het bijhouden van indrukken/klikken met Adobe Analytics, maakt de opnieuw gegenereerde asset-id de vastgelegde gegevens voor het element op Analytics ongeldig.

Als het element dat u uploadt aanwezig is in [!DNL Assets], wordt in het dialoogvenster **[!UICONTROL Duplicates Detected]** gewaarschuwd dat u probeert een gedupliceerd element te uploaden. Het dialoogvenster wordt alleen weergegeven als de waarde van de controlesom `SHA 1` van de binaire waarde van het bestaande element overeenkomt met de waarde van de controlesom van het element dat u uploadt. In dit geval zijn de namen van elementen niet van belang.

>[!NOTE]
>
>Het dialoogvenster [!UICONTROL Duplicates Detected] wordt alleen weergegeven wanneer de functie voor dubbele detectie is ingeschakeld. Zie [Dubbele detectie inschakelen](/help/assets/duplicate-detection.md) om de functie voor dubbele detectie in te schakelen.

![Dialoogvenster Middelen gedetecteerd dupliceren](assets/duplicate-asset-detected.png)

Als u het gedupliceerde element wilt behouden in [!DNL Assets], klikt u op **[!UICONTROL Keep]**. Als u het geüploade dubbele element wilt verwijderen, klikt u op **[!UICONTROL Delete]**.

[!DNL Experience Manager Assets] Hiermee voorkomt u dat elementen met de verboden tekens in de bestandsnaam worden geüpload. Als u een element probeert te uploaden met een bestandsnaam die een niet-toegestaan teken of meer bevat, wordt een waarschuwingsbericht weergegeven en wordt het uploaden gestopt totdat u deze tekens verwijdert of uploadt met een toegestane naam.[!DNL Assets]

In het dialoogvenster [!UICONTROL Upload Assets] kunt u lange namen opgeven voor de bestanden die u uploadt, zodat u de specifieke conventies voor bestandsnaamgeving voor uw organisatie kunt gebruiken.

De volgende tekens (lijst met door spaties gescheiden tekens) worden echter niet ondersteund:

* elementbestandsnaam mag geen `* / : [ \\ ] | # % { } ? &` bevatten
* elementmapnaam mag geen `* / : [ \\ ] | # % { } ? \" . ^ ; + & \t` bevatten

Voeg geen speciale tekens toe aan de extensies van de bestandsnamen van elementen.

![Het dialoogvenster Uploadvoortgang toont de status van geüploade bestanden en bestanden die niet zijn geüpload](assets/bulk-upload-progress.png)

Daarnaast wordt in de gebruikersinterface [!DNL Assets] het meest recente element weergegeven dat u uploadt of de map die u als eerste hebt gemaakt.

Als u het uploaden annuleert voordat de bestanden zijn geüpload, stopt [!DNL Assets] met het uploaden van het huidige bestand en wordt de inhoud vernieuwd. Bestanden die al zijn geüpload, worden echter niet verwijderd.

Het dialoogvenster voor uploadvoortgang in [!DNL Assets] geeft het aantal bestanden weer dat is geüpload en de bestanden die niet zijn geüpload.

### Seriële uploads {#serialuploads}

Het uploaden van talloze assets in bulk verbruikt aanzienlijke I/O-bronnen, wat de prestaties van uw [!DNL Assets]-implementatie negatief kan beïnvloeden. Met name als u een trage internetverbinding hebt, neemt de uploadtijd drastisch toe als gevolg van een spiek in schijf-I/O. Bovendien kan uw webbrowser extra beperkingen instellen voor het aantal aanvragen voor POSTEN dat [!DNL Assets] kan verwerken voor gelijktijdige uploads van middelen. Hierdoor mislukt de uploadbewerking of wordt deze voortijdig beëindigd. Met andere woorden, [!DNL Experience Manager Assets] kan sommige dossiers missen terwijl het opnemen van een groep dossiers of helemaal geen dossier ineten.

Om deze situatie te verhelpen, [!DNL Assets] neemt één middel tegelijkertijd (periodieke upload) tijdens een bulkupload verrichting op, in plaats van het tegelijkertijd opnemen van alle activa.

Seriële uploaden van elementen is standaard ingeschakeld. Als u de functie wilt uitschakelen en tegelijkertijd uploaden wilt toestaan, bedekt u de `fileupload`-node in Crx-de en stelt u de waarde van de eigenschap `parallelUploads` in op `true`.

### Elementen uploaden met FTP {#uploading-assets-using-ftp}

Dynamic Media maakt het uploaden van bestanden in batches via FTP-server mogelijk. Als u grote bestanden (>1 GB) wilt uploaden of volledige mappen en submappen wilt uploaden, moet u FTP gebruiken. U kunt zelfs instellen dat FTP-upload wordt uitgevoerd op een terugkerende geplande basis.

>[!NOTE]
>
>In de modus Dynamic Media - Scene7 kunt u alleen elementen uploaden waarvan de bestandsgrootte 2 GB of minder is.

>[!NOTE]
>
>Als u elementen wilt uploaden via FTP in de modus Dynamic Media - Scene7, installeert u Feature Pack 18912 op de auteur [!DNL Experience Manager]. Neem contact op met de [Adobe-klantenservice](https://helpx.adobe.com/nl/contact/enterprise-support.ec.html) om toegang te krijgen tot FP-18912 en de installatie van uw FTP-account te voltooien. Voor meer informatie, zie [functiepak 18912 voor bulkmiddelenmigratie installeren](/help/assets/bulk-ingest-migrate.md).
>
>Als u FTP gebruikt voor het uploaden van elementen, worden de uploadinstellingen die zijn opgegeven in [!DNL Experience Manager] genegeerd. In plaats daarvan worden de regels voor bestandsverwerking gebruikt, zoals gedefinieerd in Dynamic Media Classic.

**Elementen uploaden met FTP**

1. Meld u met uw keuze voor een FTP-client aan bij de FTP-server met de FTP-gebruikersnaam en -wachtwoord die u van de e-mail met de provisioning hebt ontvangen. Upload in de FTP-client bestanden of mappen naar de FTP-server.

1. Open [Dynamic Media Classic desktop application](https://experienceleague.adobe.com/docs/dynamic-media-classic/using/intro/dynamic-media-classic-desktop-app.html?lang=en#system-requirements-dmc-app) en meld u vervolgens aan bij uw account.

   Adobe heeft uw aanmeldingsgegevens en aanmeldingsgegevens op het moment van de provisioning opgegeven. Neem contact op met Technische ondersteuning als u deze informatie niet hebt.

1. Klik op **[!UICONTROL Upload]** op de algemene navigatiebalk.
1. Klik op het tabblad **[!UICONTROL Via FTP]** in de linkerbovenhoek van de pagina Uploaden.
1. Kies links op de pagina een FTP-map waaruit u bestanden wilt uploaden. aan de rechterkant van de pagina kiest u een doelmap.
1. Klik in de rechterbenedenhoek van de pagina op **[!UICONTROL Job Options]** en stel vervolgens de gewenste opties in op basis van de elementen in de map die u hebt geselecteerd.

   Zie [Taakopties uploaden](#upload-job-options).

   >[!NOTE]
   >
   >Wanneer u elementen uploadt via FTP, hebben de opties voor uploadtaken die u instelt in Dynamic Media Classic (S7) voorrang op parameters voor middelenverwerking die zijn ingesteld in [!DNL Experience Manager].

1. Klik in de rechterbenedenhoek van het dialoogvenster Taakopties uploaden op **[!UICONTROL Save]**.
1. Klik in de rechterbenedenhoek van de pagina Uploaden op **[!UICONTROL Submit Upload]**.

   Klik op **[!UICONTROL Jobs]** om de voortgang van het uploaden te bekijken. Op de pagina Taken wordt de voortgang van het uploaden weergegeven. U kunt in [!DNL Experience Manager] blijven werken en aan de pagina van Banen in de Klassiek van Dynamic Media op elk ogenblik terugkeren om een lopende baan te herzien.
Als u een actieve uploadtaak wilt annuleren, klikt u op **[!UICONTROL Cancel]** naast de duur van de upload.

#### Opties voor uploaden {#upload-job-options}

| Uploaden, optie | Suboptie | Beschrijving |
|---|---|---|
| Taaknaam |  | De standaardnaam die vooraf in het tekstveld is ingevuld, bevat het door de gebruiker ingevoerde gedeelte van de naam en de datum- en tijdstempel. U kunt de standaardnaam gebruiken of een naam invoeren van uw eigen ontwerp voor deze uploadtaak. <br>De baan en andere upload en het publiceren banen worden geregistreerd op de pagina van Banen, waar u de status van banen kunt controleren. |
| Publiceren na uploaden |  | Hiermee publiceert u automatisch de elementen die u uploadt. |
| Overschrijven in een willekeurige map, dezelfde naam van basiselement, ongeacht de extensie |  | Selecteer deze optie als u wilt dat de bestanden die u uploadt, bestaande bestanden met dezelfde naam vervangen. De naam van deze optie kan verschillen, afhankelijk van de instellingen in **[!UICONTROL Application Setup]** > **[!UICONTROL General Settings]** > **[!UICONTROL Upload to Application]** > **[!UICONTROL Overwrite Images]**. |
| ZIP- of Tar-bestanden bij uploaden decomprimeren |  |  |
| Taakopties |  | Klik **[!UICONTROL Job Options]** om het [!UICONTROL Upload Job Options] dialoogvakje te openen en opties te kiezen die de volledige uploadbaan beïnvloeden. Deze opties zijn hetzelfde voor alle bestandstypen.<br>U kunt standaardopties kiezen voor het uploaden van bestanden die beginnen op de pagina Algemene instellingen van toepassing. Kies **[!UICONTROL Setup]** > **[!UICONTROL Application Setup]** om deze pagina te openen. Selecteer de optie **[!UICONTROL Default Upload Options]** om het dialoogvenster [!UICONTROL Upload Job Options] te openen. |
|  | Wanneer | Selecteer Eenmalig of Herhalend. Als u een terugkerende taak wilt instellen, kiest u de optie Herhalen (Dagelijks, Wekelijks, Maandelijks of Aangepast) om op te geven wanneer de FTP-uploadtaak moet worden herhaald. Geef vervolgens de gewenste planningsopties op. |
|  | Inclusief submappen | Upload alle submappen in de map die u wilt uploaden. De namen van de map en de submappen die u uploadt, worden automatisch ingevoerd in [!DNL Experience Manager Assets]. |
|  | Opties voor uitsnijden | Als u handmatig wilt uitsnijden aan weerszijden van een afbeelding, selecteert u het menu Uitsnijden en kiest u Handmatig. Voer vervolgens het aantal pixels in dat u aan elke zijde van de afbeelding wilt uitsnijden. Hoeveel van de afbeelding wordt uitgesneden, is afhankelijk van de ppi-instelling (pixels per inch) in het afbeeldingsbestand. Als de afbeelding bijvoorbeeld 150 ppi weergeeft en u 75 invoert in de tekstvakken Boven, Rechts, Onder en Links, wordt aan beide zijden een halve inch bijgesneden.<br> Als u pixels in witruimte automatisch wilt uitsnijden in een afbeelding, opent u het menu Uitsnijden, kiest u Handmatig en voert u pixelmetingen in in de velden Boven, Rechts, Onder en Links om van de zijkanten bij te snijden. U kunt ook Bijsnijden kiezen in het menu Uitsnijden en de volgende opties kiezen:<br> **Wegsnijden op basis van** <ul><li>**Kleur**  - Kies de optie Kleur. Selecteer vervolgens het menu Hoek en kies de hoek van de afbeelding met de kleur die het beste overeenkomt met de kleur voor de witruimte die u wilt uitsnijden.</li><li>**Transparantie**  - Kies de optie Transparantie.<br> **Tolerantie**  - Sleep de schuifregelaar om een tolerantie tussen 0 en 1 op te geven. Geef voor bijsnijden op basis van kleur 0 op om alleen pixels bij te snijden als deze exact overeenkomen met de kleur die u in de hoek van de afbeelding hebt geselecteerd. De aantallen dichter aan 1 staan voor meer kleurenverschil toe.<br>Voor het bijsnijden op basis van transparantie geeft u 0 op om alleen pixels bij te snijden als deze transparant zijn. De aantallen dichter aan 1 staan voor meer transparantie toe.</li></ul><br>Deze opties voor uitsnijden zijn niet-destructief. |
|  | Opties voor kleurprofiel | Kies een kleurconversie wanneer u geoptimaliseerde bestanden maakt die worden gebruikt voor levering:<ul><li>Standaardkleurbehoud: De kleuren van de bronafbeelding blijven behouden wanneer de afbeeldingen kleurruimte-informatie bevatten. er is geen kleurconversie. In bijna alle afbeeldingen van vandaag is het juiste kleurprofiel al ingesloten. Als een CMYK-bronafbeelding echter geen ingesloten kleurprofiel bevat, worden de kleuren omgezet in de kleurruimte sRGB (standaard rood-groen-blauw). sRGB is de aanbevolen kleurruimte voor het weergeven van afbeeldingen op webpagina&#39;s.</li><li>Oorspronkelijke kleurruimte behouden: Behoudt de oorspronkelijke kleuren zonder kleurconversie op het punt. Voor afbeeldingen zonder ingesloten kleurprofiel wordt elke kleurconversie uitgevoerd met de standaardkleurprofielen die zijn geconfigureerd in de Publicatie-instellingen. De kleurprofielen worden mogelijk niet uitgelijnd met de kleur in de bestanden die met deze optie zijn gemaakt. Daarom wordt u aangeraden de optie Standaardkleurbehoud te gebruiken.</li><li>Met Aangepast van > Naar<br> opent u menu&#39;s, zodat u een optie kunt kiezen voor Omzetten van en Omzetten in kleurruimte. Deze geavanceerde optie negeert alle kleurinformatie die in het bronbestand is ingesloten. Selecteer deze optie als alle afbeeldingen die u verzendt, onjuiste of ontbrekende kleurprofielgegevens bevatten.</li></ul> |
|  | Beeldbewerkingsopties | U kunt de knipmaskers in afbeeldingen behouden en een kleurprofiel kiezen.<br> Zie Opties voor  [het bewerken van afbeeldingen tijdens het uploaden](#setting-image-editing-options-at-upload) instellen. |
|  | PostScript-opties | U kunt PostScript® rasteren, bestanden uitsnijden, transparante achtergronden behouden, een resolutie kiezen en een kleurruimte kiezen.<br> Zie  [Uploadopties](#setting-postscript-and-illustrator-upload-options) voor PostScript en Illustrator instellen. |
|  | Photoshop-opties | U kunt sjablonen maken van Adobe® Photoshop®-bestanden, lagen behouden, opgeven hoe lagen worden benoemd, tekst extraheren en opgeven hoe afbeeldingen in sjablonen worden verankerd.<br> Sjablonen worden niet ondersteund in  [!DNL Experience Manager].<br> Zie  [Photoshop-uploadopties](#setting-photoshop-upload-options) instellen. |
|  | PDF-opties | U kunt de bestanden rasteren, zoekwoorden en koppelingen extraheren, automatisch een eCatalog genereren, de resolutie instellen en een kleurruimte kiezen.<br> E-catalogi worden niet ondersteund in  [!DNL Experience Manager]. <br> Zie  [Opties voor](#setting-pdf-upload-options) PDF-upload instellen. |
|  | Illustrator-opties | U kunt Adobe Illustrator®-bestanden rasteren, transparante achtergronden behouden, een resolutie kiezen en een kleurruimte kiezen.<br> Zie  [Uploadopties](#setting-postscript-and-illustrator-upload-options) voor PostScript en Illustrator instellen. |
|  | EVideo-opties | U kunt een videobestand transcoderen door een videovoorinstelling te kiezen.<br> Zie  [Opties voor](#setting-evideo-upload-options) eVideo-upload instellen. |
|  | Voorinstellingen batchset | Als u een Afbeeldingsset of Spin-set wilt maken van de geüploade bestanden, klikt u op de kolom Actief voor de voorinstelling die u wilt gebruiken. U kunt meerdere voorinstellingen selecteren. U maakt de voorinstellingen op de pagina Voorinstellingen voor toepassingsinstellingen/batchsets van Dynamic Media Classic.<br> Zie Voorinstellingen voor batchsets  [ ](config-dms7.md#creating-batch-set-presets-to-auto-generate-image-sets-and-spin-sets) configureren voor het automatisch genereren van afbeeldingssets en de instellingen voor centrifugeren voor meer informatie over het maken van voorinstellingen voor batchsets.<br> Zie Voorinstellingen  [voor batchset instellen bij uploaden](#setting-batch-set-presets-at-upload). |

#### Opties voor het bewerken van afbeeldingen tijdens het uploaden instellen {#setting-image-editing-options-at-upload}

Wanneer u afbeeldingsbestanden uploadt, inclusief AI-, EPS- en PSD-bestanden, kunt u de volgende bewerkingen uitvoeren in het dialoogvenster [!UICONTROL Upload Job Options]:

* Witruimte uitsnijden vanaf de rand van afbeeldingen (zie beschrijving in bovenstaande tabel).
* Handmatig uitsnijden vanaf de zijkanten van afbeeldingen (zie beschrijving in bovenstaande tabel).
* Kies een kleurprofiel (zie de beschrijving van de optie in de bovenstaande tabel).
* Maak een masker op basis van een uitknippad.
* Afbeeldingen verscherpen met onscherpe maskeropties
* Achtergrond uitnemen

<!--
| Option | Sub-option | Description |
|---|---|---|
| Create Mask From Clipping Path | | Create a mask for the image based on its clipping path information. This option applies to images created with image-editing applications in which a clipping path was created. |
| Unsharp Masking | | Lets you fine-tune a sharpening filter effect on the final downsampled image, controlling the intensity of the effect, the radius of the effect (as measured in pixels), and a threshold of contrast that is ignored.<br> This effect uses the same options as Photoshop’s Unsharp Mask filter. Contrary to what the name suggests, Unsharp Mask is a sharpening filter. Under Unsharp Masking, set the options you want. Setting options are described in the following: |
| | Amount | Controls the amount of contrast that is applied to edge pixels.<br> Think of it as the intensity of the effect. The main difference between the amount values of Unsharp Mask in Dynamic Media and the amount values in Adobe Photoshop, is that Photoshop has an amount range of 1% to 500%. Whereas, in Dynamic Media, the value range is 0.0 to 5.0. A value of 5.0 is the rough equivalent of 500% in Photoshop; a value of 0.9 is the equivalent of 90%, and so on. |
| | Radius | Controls the radius of the effect. The value range is 0-250.<br> The effect is run on all pixels in an image and radiates out from all pixels in all directions. The radius is measured in pixels. For example, to get a similar sharpening effect for a 2000 x 2000 pixel image and 500 x 500 pixel image, you would set a radius of two pixels on the 2000 x 2000 pixel image and a radius value of one pixel on the 500 x 500 pixel image. A larger value is used for an image that has more pixels. |
| | Threshold | Threshold is a range of contrast that is ignored when the Unsharp Mask filter is applied. It is important so that no "noise" is introduced to an image when this filter is used. The value range is 0-255, which is the number of brightness steps in a grayscale image. 0=black, 128=50% gray and 255=white.<br> For example, a threshold value of 12 ignores slight variations is skin tone brightness to avoid adding noise, but still add edge contrast to areas such as where eyelashes meet skin.<br> For example, if you have a photo of someone’s face, the Unsharp Mask affects the parts of the image, such as where eyelashes and skin meet to create an obvious area of contrast, and the smooth skin itself. Even the smoothest skin exhibits subtle changes in brightness values. If you do not use a threshold value, the filter accentuates these subtle changes in skin pixels. In turn, a noisy and undesirable effect is created while contrast on the eyelashes is increased, enhancing sharpness.<br> To avoid this issue, a threshold value is introduced that tells the filter to ignore pixels that do not change contrast dramatically, like smooth skin.<br> In the zipper graphic shown earlier, notice the texture next to the zippers. Image noise is exhibited because the threshold values were too low to suppress the noise. |
| | Monochrome | Select to unsharp-mask image brightness (intensity).<br> Deselect to unsharp-mask each color component separately. |
| Knockout Background | | Automatically removes the background of an image when you upload it. This technique is useful to draw attention to a particular object and make it stand out from a busy background. Select to enable or “turn on” the Knockout Background feature and the following sub-options: |
| | Corner | Required.<br> The corner of the image that is used to define the background color to knockout.<br> You can choose from **Upper Left**, **Bottom Left**, **Upper Right**, or **Bottom Right**. |
| | Fill Method | Required.<br> Controls pixel transparency from the Corner location that you set.<br> You can choose from the following fill methods: <ul><li>**Flood Fill** - turns all pixels transparent that match the Corner that you have specified and are connected to it.</li><li>**Match Pixel** - turns all matching pixels transparent, regardless of their location on the image.</li></ul> |
| | Tolerance | Optional.<br> Controls the allowable amount of variation in pixel color matching based on the Corner location that you set.<br> Use a value of 0.0 to match pixel colors exactly or, use a value of 1.0 to allow for the greatest variation. |
-->

#### Uploadopties voor PostScript en Illustrator instellen {#setting-postscript-and-illustrator-upload-options}

Wanneer u PostScript- (EPS) of Illustrator-afbeeldingsbestanden (AI) uploadt, kunt u deze op verschillende manieren opmaken. U kunt de bestanden rasteren, de transparante achtergrond behouden, een resolutie kiezen en een kleurruimte kiezen. Opties voor het opmaken van PostScript- en Illustrator-bestanden zijn beschikbaar in het dialoogvenster [!UICONTROL Upload Job Options] onder [!UICONTROL PostScript Options] en [!UICONTROL Illustrator Options].

| Optie | Suboptie | Beschrijving |
|---|---|---|
| Verwerking |  | Kies **[!UICONTROL Rasterize]** om vectorafbeeldingen in het bestand om te zetten in de bitmapindeling. |
| Transparante achtergrond behouden in gerenderde afbeelding |  | De achtergrondtransparantie van het bestand behouden. |
| Resolutie |  | Hiermee bepaalt u de resolutie-instelling. Deze instelling bepaalt hoeveel pixels per inch in het bestand worden weergegeven. |
| Kleurruimte |  | Selecteer het menu Kleurruimte en kies een van de volgende opties voor kleurruimte: |
|  | Automatisch detecteren | Hiermee behoudt u de kleurruimte van het bestand. |
|  | Als RGB forceren | Zet om in de RGB-kleurruimte. |
|  | Inschakelen als CMYK | Zet om in de CMYK-kleurruimte. |
|  | Forceren als grijswaarden | Hiermee wordt de grijswaardenkleurruimte omgezet. |

#### Opties voor Photoshop-upload instellen {#setting-photoshop-upload-options}

PSD-bestanden (Photoshop Document) worden meestal gebruikt om afbeeldingssjablonen te maken. Wanneer u een PSD-bestand uploadt, kunt u automatisch een afbeeldingssjabloon maken vanuit het bestand (selecteer de optie [!UICONTROL Create Template] in het scherm Uploaden).

Dynamic Media maakt meerdere afbeeldingen van een PSD-bestand met lagen als u het bestand gebruikt om een sjabloon te maken. er wordt één afbeelding voor elke laag gemaakt.

Gebruik de [!UICONTROL Crop Options] en [!UICONTROL Color Profile Options], zoals hierboven beschreven, met de uploadopties van Photoshop.

>[!NOTE]
>
>Sjablonen worden niet ondersteund in [!DNL Experience Manager].

| Optie | Suboptie | Beschrijving |
|---|---|---|
| Lagen behouden |  | Hiermee worden de lagen in de PSD (indien aanwezig) naar afzonderlijke elementen verplaatst. De elementlagen blijven gekoppeld aan de PSD. U kunt deze weergeven door het PSD-bestand te openen in de gedetailleerde weergave en het deelvenster Lagen te selecteren. |
| Sjabloon maken |  | Hiermee maakt u een sjabloon op basis van de lagen in het PSD-bestand. |
| Tekst extraheren |  | Extraheert de tekst zodat gebruikers naar tekst in een viewer kunnen zoeken. |
| Lagen uitbreiden naar achtergrondgrootte |  | Hiermee vergroot u de grootte van de uitgesneden afbeeldingslagen tot de grootte van de achtergrondlaag. |
| Laagnaamgeving |  | Lagen in het PSD-bestand worden geüpload als afzonderlijke afbeeldingen. |
|  | Laagnaam | De afbeeldingen krijgen een naam na de namen van de lagen in het PSD-bestand. Een laag met de naam Prijscode in het oorspronkelijke PSD-bestand wordt bijvoorbeeld een afbeelding met de naam Prijscode. Als de laagnamen in het PSD-bestand echter standaard Photoshop-laagnamen zijn (Achtergrond, Laag 1, Laag 2, enzovoort), krijgen de afbeeldingen een naam na hun laagnummers in het PSD-bestand, niet na hun standaardlaagnamen. |
|  | Photoshop en Layer Number | De afbeeldingen krijgen een naam na hun laagnummer in het PSD-bestand, waarbij de namen van de oorspronkelijke lagen worden genegeerd. Afbeeldingen krijgen de naam Photoshop en een toegevoegd laagnummer. De tweede laag van een bestand met de naam Voorjaar-Ad.psd krijgt bijvoorbeeld de naam Voorjaar-Ad_2, zelfs als deze in Photoshop een andere naam heeft dan de standaardnaam. |
|  | Photoshop- en laagnaam | De afbeeldingen krijgen een naam na het PSD-bestand, gevolgd door de laagnaam of het laagnummer. Het laagnummer wordt gebruikt als de laagnamen in het PSD-bestand standaard Photoshop-laagnamen zijn. Een laag met de naam Prijstag in een PSD-bestand met de naam SpringAd krijgt bijvoorbeeld de naam Spring Ad_Price Tag. Een laag met de standaardnaam Laag 2 wordt genoemd Lente Ad_2. |
| Anker |  | Geef op hoe afbeeldingen worden verankerd in sjablonen die worden gegenereerd op basis van de laagcompositie die uit het PSD-bestand is samengesteld. Standaard is het anker het middelpunt. Met een middelste anker kunnen vervangende afbeeldingen dezelfde ruimte het beste vullen, ongeacht de hoogte-breedteverhouding van de vervangende afbeelding. Afbeeldingen met een ander aspect dat deze afbeelding vervangt, nemen bij het verwijzen naar de sjabloon en het gebruik van parametervervanging in feite dezelfde ruimte in. Schakel over naar een andere instelling als de vervangende afbeeldingen de toegewezen ruimte in de sjabloon moeten vullen. |

#### Opties voor PDF-upload instellen {#setting-pdf-upload-options}

Wanneer u een PDF-bestand uploadt, kunt u het op verschillende manieren opmaken. U snijdt zijn pagina&#39;s bij, haalt zoekwoorden op, voert een pixel-per-dun resolutie in, en kiest een kleurenruimte. PDF-bestanden bevatten vaak een snijmarge, snijtekens, registratietekens en andere drukkersmarkeringen. U kunt deze markeringen vanaf de zijkanten van pagina&#39;s bijsnijden terwijl u een PDF-bestand uploadt.

>[!NOTE]
>
>eCatalogi worden niet ondersteund in [!DNL Experience Manager].

Kies een van de volgende opties:

| Optie | Suboptie | Beschrijving |
|---|---|---|
| Verwerking | Rasteren | (Standaard) Hiermee worden de pagina&#39;s in het PDF-bestand weggesneden en worden vectorafbeeldingen naar bitmapafbeeldingen geconverteerd. Kies deze optie om een eCatalog te maken. |
| Extraheren | Woorden zoeken | Extraheert woorden uit het PDF-bestand, zodat het bestand kan worden doorzocht op trefwoord in een eCatalog-viewer. |
|  | Koppelingen | Extraheert koppelingen uit de PDF-bestanden en converteert deze naar Afbeeldingen met hyperlinks die in een eCatalog-viewer worden gebruikt. |
| E-catalogus automatisch genereren op basis van PDF van meerdere pagina&#39;s |  | Er wordt automatisch een eCatalog gemaakt van het PDF-bestand. De eCatalog wordt genoemd naar het Pdf- dossier u uploadde. (Deze optie is alleen beschikbaar als u het PDF-bestand rastert terwijl u het uploadt.) |
| Resolutie |  | Hiermee bepaalt u de resolutie-instelling. Deze instelling bepaalt hoeveel pixels per inch in het PDF-bestand worden weergegeven. De standaardwaarde is 150. |
| Kleurruimte |  | Selecteer het menu Kleurruimte en kies een kleurruimte voor het PDF-bestand. De meeste PDF-bestanden hebben zowel RGB- als CMYK-kleurenafbeeldingen. De RGB-kleurruimte heeft de voorkeur voor onlineweergave. |
|  | Automatisch detecteren | Hiermee behoudt u de kleurruimte van het PDF-bestand. |
|  | Als RGB forceren | Zet om in de RGB-kleurruimte. |
|  | Krachten als CMYK | Zet om in de CMYK-kleurruimte. |
|  | Krachtig maken als grijswaarden | Hiermee wordt de grijswaardenkleurruimte omgezet. |

#### Opties voor het uploaden van eVideo instellen {#setting-evideo-upload-options}

U transcodeert een videobestand door een keuze te maken uit verschillende videovoorinstellingen.

| Optie | Suboptie | Beschrijving |
|---|---|---|
| Adaptieve video |  | Eén coderingsvoorinstelling die met een willekeurige hoogte-breedteverhouding werkt voor het maken van video&#39;s voor levering op mobiele apparaten, tablets en desktops. Geüploade bronvideo&#39;s die met deze voorinstelling zijn gecodeerd, worden ingesteld met een vaste hoogte. De breedte wordt echter automatisch geschaald om de hoogte-breedteverhouding van de video te behouden. <br>Aangepaste videocodering wordt aanbevolen. |
| Enkele coderingsvoorinstellingen | Voorinstellingen voor codering sorteren | Selecteer Naam of Grootte om de coderingsvoorinstellingen onder Desktop, Mobiel en Tablet op naam of op resolutiegrootte te sorteren. |
|  | Desktop | Maak een MP4-bestand voor een streaming of progressieve videobeleving op bureaubladcomputers. Selecteer een of meer hoogte-breedteverhoudingen met de gewenste resolutiegrootte en gegevenssnelheid. |
|  | Mobiel | Maak een MP4-bestand voor levering op mobiele iPhone- of Android-apparaten. Selecteer een of meer hoogte-breedteverhoudingen met de gewenste resolutie- en doelgegevenssnelheid. |
|  | Tablet | Maak een MP4-bestand voor levering op iPad- of Android-tablets. Selecteer een of meer hoogte-breedteverhoudingen met de gewenste resolutie- en doelgegevenssnelheid. |

#### Voorinstellingen batchset instellen bij uploaden {#setting-batch-set-presets-at-upload}

Als u automatisch een set afbeeldingen of een set rotaties wilt maken van geüploade afbeeldingen, klikt u op de kolom Actief voor de voorinstelling die u wilt gebruiken. U kunt meerdere voorinstellingen selecteren.

Zie [Voorinstellingen voor batchsets configureren voor het automatisch genereren van afbeeldingssets en centrifuges](/help/assets/config-dms7.md#creating-batch-set-presets-to-auto-generate-image-sets-and-spin-sets) voor meer informatie over het maken van voorinstellingen voor batchsets.

### Gestroomde uploads {#streamed-uploads}

Als u veel middelen uploadt naar Adobe Experience Manager, nemen de I/O-verzoeken om de server drastisch toe. Hierdoor neemt de uploadefficiëntie af en kan er zelfs een time-out optreden bij sommige uploadtaken. [!DNL Experience Manager Assets] ondersteunt gestreamd uploaden van elementen. Gestroomd uploaden vermindert de schijf-I/O tijdens het uploaden door opslag van middelen in een tijdelijke map op de server te voorkomen voordat deze naar de opslagplaats wordt gekopieerd. In plaats daarvan worden de gegevens rechtstreeks naar de gegevensopslagruimte overgedragen. Op deze manier wordt de uploadtijd voor grote middelen en de mogelijkheid van time-outs verminderd. Gestroomde upload wordt standaard ingeschakeld in [!DNL Assets].

>[!NOTE]
>
>Uploaden naar streaming is uitgeschakeld voor Adobe Experience Manager dat op de JEE-server wordt uitgevoerd en de servlet-api-versie lager is dan 3.1.

### ZIP-archief met elementen uitpakken {#extractzip}

U kunt ZIP-archieven net als alle andere ondersteunde elementen uploaden. Dezelfde regels voor bestandsnaam gelden voor ZIP-bestanden. [!DNL Experience Manager] kunt u een ZIP-archief extraheren naar een DAM-locatie. Als de archiefbestanden geen ZIP als extensie bevatten, schakelt u detectie van bestandstypen met inhoud in.

Selecteer één archief van het PIT tegelijkertijd, klik **[!UICONTROL Extract Archive]**, en selecteer een bestemmingsomslag. Selecteer een optie om eventuele conflicten af te handelen. Als de elementen in het ZIP-bestand al in de doelmap staan, kunt u een van de volgende opties selecteren: extractie overslaan, bestaande bestanden vervangen, beide elementen behouden door een andere naam te geven of een nieuwe versie te maken.

Nadat de extractie is voltooid, [!DNL Experience Manager] brengt u op de hoogte in het systeemvak. Hoewel [!DNL Experience Manager] de ZIP extraheert, kunt u teruggaan naar uw werk zonder de extractie te onderbreken.

![Melding van uitpakken van ZIP-bestanden](assets/Zip-extraction-notification.png)

Enkele beperkingen van de functie zijn:

* Als er op de bestemming een map met dezelfde naam staat, worden de elementen uit het ZIP-bestand geëxtraheerd naar de bestaande map.
* Als u de extractie annuleert, worden de reeds geëxtraheerde elementen niet verwijderd.
* U kunt niet twee ZIP-bestanden tegelijk selecteren en extraheren. U kunt slechts één ZIP-archief tegelijk extraheren.
* Als tijdens het uploaden van een ZIP-archief in het dialoogvenster voor uploaden een serverfout van 500 wordt weergegeven, probeert u het opnieuw nadat u het laatste servicepack hebt geïnstalleerd.

## Elementen voorvertonen {#previewing-assets}

Voer de volgende stappen uit om een voorvertoning van een element weer te geven.

1. Navigeer in de gebruikersinterface [!DNL Assets] naar de locatie van het element waarvan u een voorvertoning wilt weergeven.
1. Klik op het gewenste element om het te openen.

1. In de voorvertoningsmodus zijn zoomopties beschikbaar voor [ondersteunde afbeeldingstypen](/help/assets/assets-formats.md#supported-raster-image-formats) (met interactieve bewerking).

   Als u wilt inzoomen op een element, klikt u op `+` (of klikt u op het vergrootglas van het element). Als u wilt uitzoomen, klikt u op `-`. Wanneer u inzoomt, kunt u elk gebied van de afbeelding nauwkeurig bekijken door te pannen. Met de zoompijl opnieuw instellen keert u terug naar de oorspronkelijke weergave. Als u de weergave wilt herstellen tot de oorspronkelijke grootte, klikt u op **[!UICONTROL Reset]** ![Weergave opnieuw instellen](assets/do-not-localize/revert.png).

**Elementen alleen met toetsenbordtoetsen voorvertonen**

Voer de volgende stappen uit om een voorvertoning van een element weer te geven met het toetsenbord:

1. Navigeer in de gebruikersinterface [!DNL Assets] naar het gewenste element met `Tab` en de pijltoetsen.

1. Selecteer `Enter` op het gewenste element om het te openen. In de voorvertoningsmodus kunt u inzoomen op elementen.

1. Inzoomen op het element:
   1. Gebruik `Tab` om de focus naar de inzoomoptie te verplaatsen.
   1. Gebruik `Enter` om in te zoomen op de afbeelding.

   Als u wilt uitzoomen, gebruikt u `Tab` om de focus naar de uitzoomoptie te verplaatsen en selecteert u `Enter`.

1. Gebruik `Shift` + `Tab` toetsen om de focus weer op de afbeelding te plaatsen.

1. Gebruik de pijltoetsen om de ingezoomde afbeelding te verplaatsen.

>[!MORELIKETHIS]
>
>* [Voorbeeld van Dynamic Media-middelen](/help/assets/previewing-assets.md) bekijken.
>* [Subelementen](managing-linked-subassets.md#viewing-subassets) weergeven.


## Eigenschappen en metagegevens bewerken {#editing-properties}

1. Navigeer naar de locatie van het element om de metagegevens te bewerken.

1. Selecteer het element en klik op **[!UICONTROL Properties]** op de werkbalk om de eigenschappen van het element weer te geven. U kunt ook de snelle handeling **[!UICONTROL Properties]** op de elementenkaart kiezen.

   ![Eigenschappen, snelle actie voor de weergave van de elementenkaart](assets/properties_quickaction.png)

1. Bewerk op de pagina [!UICONTROL Properties] de eigenschappen van de metagegevens onder verschillende tabbladen. Bewerk bijvoorbeeld onder het tabblad **[!UICONTROL Basic]** de titel, beschrijving, enzovoort.

   >[!NOTE]
   >
   >De indeling van de pagina [!UICONTROL Properties] en de beschikbare metagegevenseigenschappen zijn afhankelijk van het onderliggende metagegevensschema. Zie [Metagegevensschema&#39;s](/help/assets/metadata-schemas.md) voor meer informatie over het wijzigen van de indeling van de pagina [!UICONTROL Properties].

1. Gebruik de datumkiezer naast het veld **[!UICONTROL On Time]** om een bepaalde datum/tijd voor de activering van de asset te plannen.

   ![Tijdkiezer op de datum of gebruik de toetsenbordtoetsen in het veld Op tijd om datum en tijd voor activering van het element toe te voegen](assets/datepicker.png)

   *Afbeelding: Gebruik de datumkiezer om activering van middelen te plannen.*

1. Als u het element na een bepaalde duur wilt deactiveren, kiest u de datum/tijd van deactivering in de datumkiezer naast het veld **[!UICONTROL Off Time]**. De deactiveringsdatum moet later zijn dan de activeringsdatum voor een element. Na [!UICONTROL Off Time] zijn een middel en zijn vertoningen niet beschikbaar of via de [!DNL Assets] Webinterface of door HTTP API.

1. Selecteer een of meer tags in het veld **[!UICONTROL Tags]**. Als u een aangepaste tag wilt toevoegen, typt u de naam van de tag in het vak en selecteert u `Enter`. De nieuwe tag wordt opgeslagen in [!DNL Experience Manager]. [!DNL YouTube] vereist dat codes worden gepubliceerd. Zie [video&#39;s publiceren naar YouTube](video.md#publishing-videos-to-youtube).

   >[!NOTE]
   >
   >Als u tags wilt maken, moet u schrijfmachtigingen uitvoeren op `/content/cq:tags/default` in de CRX-opslagplaats.

1. Als u een classificatie voor het element wilt opgeven, klikt u op het tabblad **[!UICONTROL Advanced]** en klikt u vervolgens op de gewenste positie op de ster om de gewenste waardering toe te wijzen.

   ![Geavanceerd tabblad in Eigenschappen van element om een waardering toe te wijzen](assets/ratings.png)

   De beoordelingsscore die u toewijst aan het element, wordt weergegeven onder **[!UICONTROL Your Ratings]**. De gemiddelde ratingscore die het element ontvangt van gebruikers die het element hebben beoordeeld, wordt weergegeven onder **[!UICONTROL Rating]**. Bovendien wordt de opsplitsing van de ratingscores die bijdragen aan de gemiddelde ratingscore weergegeven onder **[!UICONTROL Rating Breakdown]**. U kunt middelen zoeken op basis van gemiddelde score.

1. Klik op het tabblad **[!UICONTROL Insights]** om gebruiksstatistieken voor het element weer te geven.

   De statistieken van het gebruik omvatten het volgende:

   * Aantal keer dat het element is weergegeven of gedownload
   * Kanalen/apparaten waardoor het middel werd gebruikt
   * Creatieve oplossingen waarbij het middel onlangs is gebruikt

   Zie [Asset Insights](/help/assets/asset-insights.md) voor meer informatie.

1. Klik op **[!UICONTROL Save & Close]**.
1. Navigeer naar de [!DNL Assets] gebruikersinterface. De bewerkte eigenschappen van metagegevens, zoals titel, beschrijving, waarderingen, enzovoort, worden weergegeven op de elementenkaart in de Kaartweergave en onder de desbetreffende kolommen in de lijstweergave.

## Elementen {#copying-assets} kopiëren

Wanneer u een middel of een omslag kopieert, wordt het volledige middel of de omslag gekopieerd, samen met zijn inhoudsstructuur. Een gekopieerd middel of een omslag wordt gedupliceerd bij de doelplaats. Het element op de bronlocatie wordt niet gewijzigd.

Enkele kenmerken die uniek zijn voor een bepaalde kopie van een element, worden niet overgedragen. Enkele voorbeelden zijn:

* Element-id, aanmaakdatum en -tijd en versies en versiegeschiedenis. Sommige van deze eigenschappen worden aangegeven door de eigenschappen `jcr:uuid`, `jcr:created` en `cq:name`.

* De aanmaaktijd en de paden waarnaar wordt verwezen, zijn uniek voor elk element en elke uitvoering ervan.

De andere eigenschappen en metagegevens blijven behouden. Er wordt geen gedeeltelijke kopie gemaakt wanneer een element wordt gekopieerd.

1. Selecteer in de interface [!DNL Assets] een of meer elementen en klik op **[!UICONTROL Copy]** op de werkbalk. U kunt ook de optie **[!UICONTROL Copy]** ![Kopiëren op de werkbalk selecteren in de interface Elementen](assets/do-not-localize/copy_icon.png) snelle actie op de elementenkaart.

   >[!NOTE]
   >
   >Als u de snelle handeling [!UICONTROL Copy] gebruikt, kunt u slechts één element tegelijk kopiëren.

1. Navigeer naar de locatie waar u de elementen wilt kopiëren.

   >[!NOTE]
   >
   >Als u een element op dezelfde locatie kopieert, wordt automatisch een variatie in de naam gegenereerd. [!DNL Experience Manager] Als u bijvoorbeeld een element met de naam `Square` kopieert, genereert [!DNL Experience Manager] automatisch de titel voor de kopie als `Square1`.

1. Klik op de optie **[!UICONTROL Paste]** ![Plakken op de werkbalk Elementen](assets/do-not-localize/paste.png) in de werkbalk. Elementen worden vervolgens naar deze locatie gekopieerd.

   >[!NOTE]
   >
   >De optie **[!UICONTROL Paste]** is beschikbaar op de werkbalk totdat de plakbewerking is voltooid.

## Elementen verplaatsen en hernoemen {#moving-or-renaming-assets}

Wanneer u elementen (of mappen) naar een andere locatie verplaatst, worden de elementen (of mappen) tijdens het kopiëren van het element niet gedupliceerd. De elementen (of mappen) worden op de doellocatie geplaatst en worden van de bronlocatie verwijderd. U kunt de naam van het element ook wijzigen wanneer u het naar de nieuwe locatie verplaatst.
Als u een gepubliceerd element naar een andere locatie verplaatst, kunt u het element opnieuw publiceren. Door gebrek beweeg verrichting op gepubliceerde activa maakt automatisch het ongedaan. Een verplaatst element wordt opnieuw gepubliceerd als de auteur de optie [!UICONTROL Republish] selecteert wanneer het element wordt verplaatst.

![U kunt een reeds gepubliceerd element opnieuw publiceren wanneer u het verplaatst](assets/republish-on-move.png)

Elementen of mappen verplaatsen:

1. Navigeer naar de locatie van het element dat u wilt verplaatsen.

1. Selecteer het element en klik op de optie **[!UICONTROL Move]** op de werkbalk.
   ![Optie Verplaatsen op de werkbalk Elementen](assets/do-not-localize/move.png)

1. Voer in de wizard [!UICONTROL Move Assets] een van de volgende handelingen uit:

   * Geef de naam voor het element op nadat het is verplaatst. Klik vervolgens op **[!UICONTROL Next]** om door te gaan.

   * Klik op **[!UICONTROL Cancel]** om het proces te stoppen.
   >[!NOTE]
   >
   >* U kunt dezelfde naam opgeven voor het element als er geen element met die naam is op de nieuwe locatie. U moet echter een andere naam gebruiken als u het element verplaatst naar een locatie waar zich een element met dezelfde naam bevindt. Als u dezelfde naam gebruikt, genereert het systeem automatisch een variatie in de naam. Als uw element bijvoorbeeld de naam Vierkant heeft, genereert het systeem de naam Vierkant1 voor de kopie.
   >* Bij het wijzigen van de naam is witruimte niet toegestaan in de bestandsnaam.


1. Voer in het dialoogvenster **[!UICONTROL Select Destination]** een van de volgende handelingen uit:

   * Navigeer naar de nieuwe locatie voor de elementen en klik vervolgens op **[!UICONTROL Next]** om door te gaan.

   * Klik **[!UICONTROL Back]** om aan het **[!UICONTROL Rename]** scherm terug te keren.

1. Als de elementen die worden verplaatst, verwijzen naar pagina&#39;s, elementen of verzamelingen, wordt het tabblad **[!UICONTROL Adjust References]** naast het tabblad **[!UICONTROL Select Destination]** weergegeven.

   Voer een van de volgende handelingen uit in het scherm **[!UICONTROL Adjust References]**:

   * Geef op welke verwijzingen op basis van de nieuwe details moeten worden aangepast en klik vervolgens op **[!UICONTROL Move]** om door te gaan.

   * Selecteer/maak in de kolom **[!UICONTROL Adjust]** verwijzingen naar de elementen ongedaan.
   * Klik **[!UICONTROL Back]** om aan het **[!UICONTROL Select Destination]** scherm terug te keren.

   * Klik **[!UICONTROL Cancel]** om de verplaatsingsbewerking te stoppen.

   Als u verwijzingen niet bijwerkt, blijven ze naar het vorige pad van het element wijzen. Als u de referenties aanpast, worden deze bijgewerkt naar het nieuwe middelenpad.

### Elementen verplaatsen met behulp van sleepbewerking {#move-using-drag}

U kunt elementen (of mappen) naar een map op hetzelfde niveau verplaatsen door deze naar de doellocatie te slepen in plaats van de optie [!UICONTROL Move] in de gebruikersinterface te gebruiken. Deze bewerking is echter alleen mogelijk in de lijstweergave.

Als u elementen verplaatst door ze te slepen, wordt de wizard [!UICONTROL Move Asset] niet geopend. U krijgt dan ook niet de optie om de naam van de elementen te wijzigen tijdens het verplaatsen. Bovendien worden de reeds gepubliceerde elementen opnieuw gepubliceerd wanneer ze door slepen worden verplaatst, zonder dat de gebruiker toestemming moet vragen om ze opnieuw te publiceren.

![Elementen naar secundaire mappen verplaatsen door elementen te slepen](assets/move-by-drag.gif)

## Uitvoeringen beheren {#managing-renditions}

1. U kunt uitvoeringen voor een element toevoegen of verwijderen, behalve voor het origineel. Navigeer naar de locatie van het element waaraan u uitvoeringen wilt toevoegen of verwijderen.

1. Klik op het element om de bijbehorende pagina te openen.
1. Selecteer **[!UICONTROL Renditions]** in de lijst in de interface Experience Manager.
1. In het **[!UICONTROL Renditions]** paneel, bekijk de lijst van vertoningen die voor het element worden geproduceerd.

   ![Deelvenster Uitvoeringen op de pagina Informatie-details](assets/renditions_panel.png)

   >[!NOTE]
   >
   >[!DNL Assets] geeft standaard niet de oorspronkelijke uitvoering van het element weer in de voorvertoningsmodus. Als beheerder kunt u overlays gebruiken om [!DNL Assets] te configureren voor het weergeven van originele uitvoeringen in de voorvertoningsmodus.

1. Selecteer een vertoning om de vertoning weer te geven of te verwijderen.

   **Een vertoning verwijderen**

   Selecteer een vertoning in het **[!UICONTROL Renditions]**-deelvenster en klik vervolgens op **[!UICONTROL Delete Rendition]** ![Option om een vertoning te verwijderen uit de werkbalk. ](assets/do-not-localize/deleteoutline.png) Uitvoeringen kunnen niet bulksgewijs worden verwijderd nadat de verwerking van het element is voltooid. Voor afzonderlijke elementen kunt u uitvoeringen handmatig uit de gebruikersinterface verwijderen. Voor meerdere elementen kunt u de Experience Manager aanpassen om bepaalde uitvoeringen te verwijderen of om de elementen te verwijderen en de verwijderde elementen opnieuw te uploaden.

   **Een nieuwe uitvoering uploaden**

   Navigeer naar de pagina met elementdetails voor het element en klik op de optie **[!UICONTROL Add Rendition]** ![Weergave toevoegen om nieuwe uitvoering te uploaden](assets/do-not-localize/add.png) op de werkbalk om een nieuwe uitvoering voor het element te uploaden.

   >[!NOTE]
   >
   >Als u een uitvoering selecteert in het deelvenster **[!UICONTROL Renditions]**, verandert de context van de werkbalk en worden alleen die acties weergegeven die relevant zijn voor de uitvoering. Opties, zoals de optie [!UICONTROL Upload Rendition], worden niet weergegeven. Ga naar de pagina met details voor de asset om deze opties in de werkbalk weer te geven.

   U kunt de afmetingen configureren voor de vertoning die u wilt weergeven op de detailpagina van een afbeelding of video-element. Gebaseerd op de afmetingen u specificeert, [!DNL Assets] toont de vertoning met de nauwkeurige of dichtste afmetingen.

   Als u weergaveafmetingen van een afbeelding op het niveau van de assetdetails wilt configureren, overlapt u het knooppunt `renditionpicker` (`libs/dam/gui/content/assets/assetpage/jcr:content/body/content/content/items/assetdetail/items/col1/items/assetview/renditionpicker`) en configureert u de waarde van de breedte-eigenschap. Configureer de eigenschap **[!UICONTROL size (Long) in KB]** in plaats van de breedte om de weergave op de pagina met assetdetails aan te passen op basis van de afbeeldingsgrootte. Voor aanpassing op basis van grootte wijst de eigenschap `preferOriginal` de voorkeur toe aan het origineel als de grootte van de overeenkomstige weergave groter is dan het origineel.

   Op dezelfde manier kunt u de afbeelding van de pagina Annotatie aanpassen door `libs/dam/gui/content/assets/annotate/jcr:content/body/content/content/items/content/renditionpicker` te bedekken.

   ![Het knooppunt Overlay renditionpicker in CRXDE om de afbeelding van de annotatiepagina aan te passen](assets/renditionpicker-node-crxde.png)

   Als u renditiedimensies voor een video-element wilt configureren, navigeert u naar het `videopicker`-knooppunt in de CRX-opslagruimte op de locatie `/libs/dam/gui/content/assets/assetpage/jcr:content/body/content/content/items/assetdetail/items/col1/items/assetview/videopicker`, bedekt u het knooppunt en bewerkt u de juiste eigenschap.

   >[!NOTE]
   >
   >Videoannotaties worden alleen ondersteund in browsers met HTML5-compatibele video-indelingen. Afhankelijk van de browser worden bovendien verschillende video-indelingen ondersteund.

Zie [subassets beheren](managing-linked-subassets.md#generate-subassets) voor meer informatie over het genereren en weergeven van subassets.

## Elementen {#deleting-assets} verwijderen

Voor het verwijderen van elementen vereist een gebruiker verwijderingsmachtigingen op `dam/asset`. Als u alleen over wijzigingsmachtigingen beschikt, kunt u alleen de metagegevens van de elementen bewerken en annotaties toevoegen aan het element. U kunt het element of de metagegevens echter niet verwijderen.

Als u de inkomende verwijzingen van andere pagina&#39;s wilt oplossen of verwijderen, werkt u de relevante verwijzingen bij voordat u een element verwijdert. Als u gebruikers niet wilt toestaan om waarnaar wordt verwezen, te verwijderen en verbroken koppelingen te behouden, schakelt u de optie voor het forceren verwijderen uit met een bedekking.

Middelen of mappen met elementen verwijderen:

1. Navigeer naar de locatie van het element of de map die u wilt verwijderen.

1. Selecteer het middel of de omslag, en klik **[!UICONTROL Delete]** ![optie van de Schrapping](assets/do-not-localize/deleteoutline.png) van de toolbar.

   Zodra u de schrapping bevestigt:

   * Als het element geen verwijzingen bevat, wordt het element verwijderd.

   * Als het element verwijzingen bevat, wordt u via een foutbericht meegedeeld dat naar een of meer elementen wordt verwezen **.** U kunt **[!UICONTROL Force Delete]** of **[!UICONTROL Cancel]** selecteren.
   >[!NOTE]
   >
   >* Als u de inkomende verwijzingen van andere pagina&#39;s wilt oplossen of verwijderen, werkt u de relevante verwijzingen bij voordat u een element verwijdert. Schakel ook de optie voor forceren verwijderen uit met behulp van een overlay, zodat gebruikers geen bestanden waarnaar wordt verwezen kunnen verwijderen en verbroken koppelingen behouden blijven.
   >* Het is mogelijk een *map* te verwijderen die uitgecheckte elementbestanden bevat. Voordat u een map verwijdert, moet u controleren of er geen digitale elementen zijn uitgecheckt door gebruikers.


>[!NOTE]
>
>Als u een map verwijdert met de bovenstaande methode uit de gebruikersinterface, worden ook de bijbehorende gebruikersgroepen verwijderd.
>
>Bestaande redundante, ongebruikte en automatisch gegenereerde gebruikersgroepen kunnen echter worden opgeschoond vanuit de opslagplaats met de methode `clean` in JMX in uw auteurinstantie (`http://[server]:[port]/system/console/jmx/com.day.cq.dam.core.impl.team%3Atype%3DClean+redundant+groups+for+Assets`).

## Elementen {#downloading-assets} downloaden

Zie [Elementen downloaden van Experience Manager](/help/assets/download-assets-from-aem.md).

## Elementen {#publishing-assets} publiceren

>[!NOTE]
>
>Zie [Dynamic Media-middelen publiceren](/help/assets/publishing-dynamicmedia-assets.md) voor meer informatie over Dynamic Media.

1. Navigeer naar de locatie van de middelen/map die u wilt publiceren.

1. Selecteer de handeling **[!UICONTROL Publish]** in de elementenkaart of selecteer het element en klik op de optie **[!UICONTROL Quick Publish]** in de werkbalk.
1. Als het element verwijst naar andere elementen, worden de verwijzingen ervan weergegeven in de wizard. Alleen verwijzingen die niet-gepubliceerd of gewijzigd zijn sinds ze voor het laatst zijn gepubliceerd/niet gepubliceerd, worden weergegeven. Kies de referenties die u wilt publiceren.

   >[!NOTE]
   >
   >Lege mappen, die onderdeel zijn van een map die u hebt gepubliceerd, worden niet gepubliceerd.

1. Klik **[!UICONTROL Publish]** om de activering voor de activa te bevestigen.

>[!CAUTION]
>
>Als u elementen publiceert die worden verwerkt, wordt alleen de oorspronkelijke inhoud gepubliceerd. De uitvoeringen ontbreken. Wacht tot de verwerking is voltooid en publiceer het element of publiceer het opnieuw nadat de verwerking is voltooid.

## Elementen {#unpublishing-assets} verwijderen

1. Navigeer naar de locatie van de map met middelen die u uit de publicatieomgeving wilt verwijderen (publicatie ongedaan maken).

1. Selecteer het middel/de omslag om unpublish, en klik **[!UICONTROL Manage Publication]** ![de optie van de Publicatie ](assets/do-not-localize/globe-publication.png) van de toolbar te beheren.

1. Selecteer de handeling **[!UICONTROL Unpublish]** in de lijst.

   ![Handeling Unpublish](assets/unpublish_action.png)

1. Als u de publicatie van het element later ongedaan wilt maken, selecteert u **[!UICONTROL Unpublish Later]** en selecteert u vervolgens een datum voor het ongedaan maken van de publicatie van het element.
1. Plan een datum waarop het element niet beschikbaar is in de publicatieomgeving.
1. Als het element verwijst naar andere elementen, kiest u de verwijzingen die u ongedaan wilt maken. Klik op **[!UICONTROL Unpublish]**.
1. Klik in het bevestigingsdialoogvenster op:

   * **[!UICONTROL Cancel]** om de handeling te stoppen
   * **[!UICONTROL Unpublish]** om te bevestigen dat de elementen op de opgegeven datum niet gepubliceerd zijn (niet meer beschikbaar in de publicatieomgeving).

   >[!NOTE]
   >
   >Verwijder tijdens het verwijderen van de publicatie van een complex element alleen de publicatie van het element. Verwijder de publicatie van de verwijzingen niet omdat mogelijk naar deze verwijzingen wordt verwezen door andere gepubliceerde elementen.

## Gesloten gebruikersgroep {#closed-user-group}

Een gesloten gebruikersgroep (CUG) wordt gebruikt om toegang tot specifieke middelomslagen te beperken die van [!DNL Experience Manager] worden gepubliceerd. Als u een CUG maakt voor een map, is de toegang tot de map (inclusief mapelementen en submappen) beperkt tot alleen toegewezen leden of groepen. Om tot de omslag toegang te hebben, moeten zij login gebruikend hun veiligheidsgeloofsbrieven.

CUG&#39;s zijn een extra manier om de toegang tot uw elementen te beperken. U kunt ook een aanmeldingspagina voor de map configureren.

1. Selecteer een map in de interface [!DNL Assets] en klik op de optie [!UICONTROL Properties] op de werkbalk om de pagina met eigenschappen weer te geven.
1. Voeg leden of groepen toe onder **[!UICONTROL Closed User Group]** op het tabblad **[!UICONTROL Permissions]**.

   ![Gebruiker toevoegen aan gesloten gebruikersgroep](assets/add_user.png)

1. Als u een aanmeldingsscherm wilt weergeven wanneer gebruikers de map openen, selecteert u de optie **[!UICONTROL Enable]**. Selecteer vervolgens het pad naar een aanmeldingspagina in [!DNL Experience Manager] en sla de wijzigingen op.

   ![Aanmeldingspagina inschakelen en selecteren om weer te geven wanneer de gebruiker toegang krijgt tot de map](assets/login_page.png)

   >[!NOTE]
   >
   >Als u het pad naar een aanmeldingspagina niet opgeeft, wordt de standaardaanmeldingspagina weergegeven in de publicatie-instantie.[!DNL Experience Manager]

1. Publiceer de map en probeer deze vervolgens te openen vanuit de publicatie-instantie. Er wordt een aanmeldingsscherm weergegeven.
1. Als u lid van de GECG bent, ga uw veiligheidsgeloofsbrieven in. De map wordt weergegeven nadat [!DNL Experience Manager] u heeft geverifieerd.

## Assets doorzoeken {#assetsearch}

Het zoeken naar middelen is van cruciaal belang voor het gebruik van een systeem voor het beheer van digitale activa — of het nu gaat om verder gebruik door creatieve ondernemingen, voor een robuust beheer van activa door zakelijke gebruikers en marketeers, of voor beheer door DAM-beheerders.

Voor eenvoudige, geavanceerde, en douaneonderzoeken om de meest aangewezen activa te ontdekken en te gebruiken, zie [onderzoeksactiva in Experience Manager](search-assets.md).

## Snelle handelingen {#quick-actions}

De snelle actiepictogrammen zijn beschikbaar voor één middel tegelijkertijd. Voer afhankelijk van het apparaat de volgende handelingen uit om de snelactiepictogrammen weer te geven:

* Aanraakapparaten: Raak aan en houd de muisknop ingedrukt. Op een iPad kunt u bijvoorbeeld tikken en een element ingedrukt houden, zodat de snelle acties worden weergegeven.
* Niet-aanraakapparaten: Aanwijzer aanwijzen. Op een bureaubladapparaat wordt bijvoorbeeld de snelle actiebalk weergegeven als u de aanwijzer boven de elementminiatuur houdt.

### Navigeren en elementen selecteren {#navigating-and-selecting-assets}

Met de optie **[!UICONTROL Select]** kunt u elementen weergeven, doorbladeren en selecteren met een van de beschikbare weergaven (Kaart, Kolom en Lijst).

In de lijstweergave en de kolomweergave wordt de optie **[!UICONTROL Select]** weergegeven wanneer u de aanwijzer boven de elementminiatuur plaatst.

In de kaartweergave wordt de optie **[!UICONTROL Select]** weergegeven als een snelle actie.

![Snelle actie selecteren in de weergave Kaart](assets/select_quick_action.png)

Wanneer u in de gebruikersinterface van [!DNL Assets] in een browser door een map of verzameling bladert, kunt u alle weergegeven of geladen elementen selecteren met de optie [!UICONTROL Select All] in de rechterbovenhoek. In eerste instantie worden slechts 100 elementen in de kaartweergave geladen en worden 200 in de lijstweergave geladen. Er worden meer elementen in de weergave geladen wanneer u door de pagina met zoekresultaten bladert. Met de optie [!UICONTROL Select All] selecteert u alleen de geladen elementen.

Voor meer informatie, zie [mening en het selecteren van uw middelen](/help/sites-authoring/basic-handling.md#viewing-and-selecting-resources).

## Afbeeldingen bewerken {#editing-images}

Met de bewerkingsgereedschappen in de [!DNL Assets]-interface kunt u kleine bewerkingstaken uitvoeren op afbeeldingselementen. U kunt afbeeldingen uitsnijden, roteren, spiegelen en andere bewerkingstaken uitvoeren. U kunt ook afbeeldingen met hyperlinks toevoegen aan elementen.

>[!NOTE]
>
>Voor sommige componenten zijn er extra opties beschikbaar voor de modus Volledig scherm.

1. Voer een van de volgende handelingen uit om een element te openen in de bewerkingsmodus:

   * Selecteer het element en klik op **[!UICONTROL Edit]** op de werkbalk.
   * Klik op **[!UICONTROL Edit]** optie die op een element in de kaartweergave wordt weergegeven.
   * Klik op **[!UICONTROL Edit]** op de werkbalk ![Optie Bewerken in werkbalk](assets/do-not-localize/edit_icon.png).

1. Als u de afbeelding wilt uitsnijden, klikt u op **[!UICONTROL Crop]** ![Option om een afbeelding uit te snijden.](assets/do-not-localize/crop.png)

1. Selecteer de gewenste optie in de lijst. Het bijsnijdgebied wordt op basis van de gekozen optie weergegeven in de afbeelding. Met de optie **Vrije hand** kunt u de afbeelding bijsnijden zonder beperkingen voor de hoogte-breedteverhouding.

   ![Opties voor uitsnijden](assets/crop-options.png)

1. Selecteer het gebied dat u wilt bijsnijden en wijzig de grootte of de positie van het gebied in de afbeelding.

1. Gebruik de werkbalkoptie **[!UICONTROL Undo]** ![Ongedaan maken](assets/do-not-localize/undo.png) en **[!UICONTROL Redo]** ![Opnieuw uitvoeren werkbalkoptie](assets/do-not-localize/redo.png) om respectievelijk naar de niet-bijgesneden afbeelding terug te keren of de bijgesneden afbeelding te behouden.
1. Klik op de desbetreffende optie **[!UICONTROL Rotate]** om de afbeelding rechtsom of linksom te roteren.

   ![Roteer opties met de klok mee en tegen de klok in](assets/do-not-localize/rotate-options.png)

1. Klik op de desbetreffende **[!UICONTROL Flip]**-opties om de afbeelding horizontaal om te draaien ![spiegelt u de horizontale optie](assets/do-not-localize/flip-horizontal.png) of verticaal ![spiegelt u de verticale optie](assets/do-not-localize/flip-vertical.png).

1. Als u de bewerking van de afbeelding wilt voltooien, klikt u op **[!UICONTROL Finish]** ![Optie voltooien](assets/do-not-localize/check-ok-done-icon.png). Als u op **Voltooien** klikt, wordt ook het opnieuw genereren van uitvoeringen gestart.

>[!NOTE]
>
>Beeldbewerking wordt ondersteund voor de bestandsindelingen BMP, GIF, PNG en JPEG.

U kunt ook afbeeldingen met hyperlinks toevoegen met de afbeeldingseditor. Zie [Afbeeldingskaarten toevoegen](/help/assets/image-maps.md) voor meer informatie.

>[!NOTE]
>
>Om een TXT- dossier uit te geven, plaats **Dag CQ Verbinding Externalzer** van de Manager van de Configuratie.

## Tijdlijn {#timeline}

In de tijdlijn kunt u verschillende gebeurtenissen voor een geselecteerd item weergeven, zoals actieve workflows voor een element, opmerkingen/annotaties, activiteitenlogbestanden en versies.

![Tijdlijnitems voor een element sorteren](assets/sort_timeline.gif)

*Afbeelding: Sorteer de tijdlijnitems voor een element.*

>[!NOTE]
>
>In de [Collections console](/help/assets/manage-collections.md#navigating-the-collections-console) biedt de lijst **[!UICONTROL Show All]** opties om alleen opmerkingen en workflows weer te geven. Bovendien wordt de chronologie getoond slechts voor top-level inzamelingen die in de console vermeld zijn. Deze wordt niet weergegeven als u in een van de verzamelingen navigeert.

>[!NOTE]
>
>De tijdlijn bevat verschillende [opties die specifiek zijn voor inhoudsfragmenten](/help/assets/content-fragments/content-fragments-managing.md#timeline-for-content-fragments).

## Elementen {#annotating} annoteren

Annotaties zijn opmerkingen of toelichtingen die aan afbeeldingen of video&#39;s worden toegevoegd. Annotaties bieden marketers de mogelijkheid samen te werken en feedback over middelen te geven.

Videoannotaties worden alleen ondersteund in browsers met HTML5-compatibele video-indelingen. Video-indelingen die [!DNL Assets] ondersteunt, zijn afhankelijk van de browser.

>[!NOTE]
>
>Voor inhoudsfragmenten worden [annotaties gemaakt in de fragmenteditor](/help/assets/content-fragments/content-fragments-variations.md#annotating-a-content-fragment).

1. Navigeer naar de locatie van het element waaraan u annotaties wilt toevoegen.
1. Klik op de optie **[!UICONTROL Annotate]** van een van de volgende opties:

   * [Snelle acties](/help/assets/manage-assets.md#quick-actions)
   * Selecteer het element op de werkbalk of navigeer naar de elementpagina.

1. Voeg een opmerking toe in het vak **[!UICONTROL Comment]** onder aan de tijdlijn. U kunt ook een gebied in de afbeelding markeren en een annotatie toevoegen in het dialoogvenster **[!UICONTROL Add Annotation]**.

   ![Opmerking in het dialoogvenster Annotatie toevoegen](assets/annotation-comment-box.png)

1. Als u een gebruiker op de hoogte wilt stellen van een aantekening, geeft u het e-mailadres van de gebruiker op en voegt u de opmerking toe. Als u Aaron MacDonald bijvoorbeeld wilt informeren over een annotatie, voert u @aa in. Tips voor alle overeenkomende gebruikers worden weergegeven in een lijst. Selecteer het e-mailadres van Aaron in de lijst om de opmerking aan haar toe te voegen. Op dezelfde manier kunt u meer gebruikers overal in de annotatie of ervoor of erna een tag toewijzen.

   ![Geef het e-mailadres van de gebruiker op en voeg opmerkingen toe om de gebruiker op de hoogte te stellen](assets/annotation-add-user-email.png)

   >[!NOTE]
   >
   >Voor een niet-beheerdergebruiker, verschijnen de suggesties slechts als de gebruiker toestemmingen bij `/home` weg in CRXDE heeft.

1. Nadat u de annotatie hebt toegevoegd, klikt u op **[!UICONTROL Add]** om deze op te slaan. Een kennisgeving voor de aantekening wordt verzonden naar Aaron.

   >[!NOTE]
   >
   >U kunt meerdere annotaties toevoegen voordat u ze opslaat.

1. Klik op **[!UICONTROL Close]** om de annotatiemodus te verlaten.
1. Als u de melding wilt weergeven, meldt u zich aan bij [!DNL Assets] met de gegevens van Aaron MacDonald en klikt u op de optie **[!UICONTROL Notifications]** om de melding weer te geven.

   >[!NOTE]
   >
   >U kunt ook annotaties toevoegen aan video-elementen. Tijdens het annoteren van video&#39;s pauzeert de speler zodat u notities kunt aanbrengen in een frame. Zie [Video-elementen beheren](/help/assets/managing-video-assets.md) voor meer informatie.

1. Als u een andere kleur wilt kiezen, zodat u onderscheid kunt maken tussen gebruikers, klikt u op de optie Profiel en klikt u op **[!UICONTROL My Preferences]**.

   ![Selecteer de optie Gebruikersprofiel en kies Mijn voorkeuren om Gebruikersvoorkeuren te openen](assets/User-profile-preferences.png)

   Geef de gewenste kleur op in het vak **[!UICONTROL Annotation Color]** en klik op **[!UICONTROL Accept]**.

   ![Selecteer een annotatiekleur in de gebruikersvoorkeuren om de persoonlijke kleur van de gebruiker in te stellen](assets/Annotation-color.png)

>[!NOTE]
>
>U kunt ook annotaties toevoegen aan een verzameling. Als een verzameling onderliggende verzamelingen bevat, kunt u echter alleen annotaties/opmerkingen aan de bovenliggende verzameling toevoegen. De optie Annoteren is niet beschikbaar voor onderliggende verzamelingen.

### Opgeslagen annotaties weergeven {#viewing-saved-annotations}

1. Als u opgeslagen annotaties voor een element wilt weergeven, navigeert u naar de locatie van het element en opent u de elementpagina voor het element.

1. Kies **[!UICONTROL Timeline]** in de interface Experience Manager.
1. Selecteer in de lijst **[!UICONTROL Show All]** in de tijdlijn de optie **[!UICONTROL Comments]** om de resultaten te filteren op basis van annotaties.

   Klik op een opmerking in het deelvenster **[!UICONTROL Timeline]** om de bijbehorende annotatie in de afbeelding weer te geven.

   ![Deelvenster Tijdlijn om annotatie in afbeelding weer te geven](assets/timeline-view-annotations.png)

   Klik op **[!UICONTROL Delete]** om een bepaalde opmerking te verwijderen.

### Annotaties {#printing-annotations} afdrukken

Als een element annotaties heeft of aan een revisiewerkstroom is onderworpen, kunt u het element samen met annotaties en revisiestatus als PDF-bestand afdrukken voor offline revisie.

U kunt ook alleen de annotaties of de revisiestatus afdrukken.

Als u de annotaties en de revisiestatus wilt afdrukken, klikt u op **[!UICONTROL Print]** en volgt u de instructies in de wizard. De optie **[!UICONTROL Print]** wordt alleen op de werkbalk weergegeven wanneer aan het element ten minste één aantekening of revisiestatus is toegewezen.

1. Open vanuit de interface [!DNL Assets] de voorvertoningspagina voor een element.
1. Voer een van de volgende handelingen uit:

   * Als u alle annotaties en de revisiestatus wilt afdrukken, slaat u stap 3 over en gaat u rechtstreeks naar stap 4.
   * Als u specifieke annotaties en revisiestatus wilt afdrukken, opent u de [tijdlijn](/help/assets/manage-assets.md#timeline) en gaat u naar stap 3.

1. Als u specifieke annotaties wilt afdrukken, selecteert u de annotaties in de tijdlijn.

   ![Een annotatie selecteren in de tijdlijn om deze af te drukken](assets/timeline-select-annotations.png)

   Als u alleen de revisiestatus wilt afdrukken, selecteert u deze in de tijdlijn.

1. Klik op **[!UICONTROL Print]** op de werkbalk.

1. Kies in het dialoogvenster Afdrukken de positie waar u de annotaties/revisiestatus wilt weergeven in de PDF. Als u bijvoorbeeld wilt dat de annotaties/status rechtsboven op de pagina met de afgedrukte afbeelding worden afgedrukt, gebruikt u de instelling **Linksboven**. Deze optie is standaard geselecteerd.

   ![Positie van annotatie/revisiestatus selecteren en in PDF weergeven vanuit dialoogvenster Afdrukken](assets/Print-annotation-dialog.png)

   U kunt andere instellingen kiezen, afhankelijk van de positie waar u de annotaties/status wilt weergeven in de afgedrukte PDF. Kies **[!UICONTROL Next Page]** als u de annotaties/status wilt weergeven op een pagina die gescheiden is van de afgedrukte asset.

   >[!NOTE]
   >
   >Lengte annotaties worden mogelijk niet correct weergegeven in het PDF-bestand. Voor een optimale rendering raadt Adobe aan om annotaties te beperken tot 50 woorden.

1. Klik op **[!UICONTROL Print]**. Afhankelijk van de optie die u kiest in stap 2, geeft de gegenereerde PDF de annotaties/status op de opgegeven positie weer. Als u bijvoorbeeld zowel annotaties als de revisiestatus wilt afdrukken met de instelling **Linksboven**, lijkt de gegenereerde uitvoer op het PDF-bestand dat hier wordt weergegeven.

   ![Annotatie en revisiestatus in gegenereerde PDF](assets/annotation-status-pdf.png)

1. Download ![Downloadoptie voor PDF](assets/do-not-localize/download.png) of druk ![afdrukopties op PDF](assets/do-not-localize/print.png) PDF gebruikend de opties bij hoogste-juist.

   >[!NOTE]
   >
   >Als het element subelementen bevat, kunt u alle subelementen samen met de specifieke paginagewijze annotaties afdrukken.

   Als u de weergave van het gerenderde PDF-bestand wilt wijzigen, bijvoorbeeld de lettertypekleur, -grootte en -stijl, de achtergrondkleur van de opmerkingen en status, opent u **[!UICONTROL Annotation PDF configuration]** in Configuration Manager en wijzigt u de gewenste opties. Als u bijvoorbeeld de weergavekleur van de goedgekeurde status wilt wijzigen, wijzigt u de kleurcode in het desbetreffende veld. Zie [Annoteren](/help/assets/manage-assets.md#annotating) voor informatie over het wijzigen van de fontkleur van annotaties.

   ![Configuratie om elementannotatie af te drukken op PDF-document](assets/annotation-print-pdf-config.png)

   Ga terug naar het gerenderde PDF-bestand en vernieuw het. De vernieuwde PDF weerspiegelt de wijzigingen die u hebt aangebracht.

Als een middel annotaties in vreemde talen (vooral niet-Latijnse talen) omvat, moet u CQ-DAM-Handler-Gibson de Dienst van de Manager van de Doopvont op de [!DNL Experience Manager] server eerst vormen om deze annotaties te kunnen drukken. Geef bij het configureren van de service CQ-DAM-Handler-Gibson Font Manager het pad op waar de lettertypen voor de gewenste talen zich bevinden.

1. Open de configuratiepagina CQ-DAM-Handler-Gibson Font Manager Service via de URL `https://[aem_server]:[port]/system/console/configMgr/com.day.cq.dam.handler.gibson.fontmanager.impl.FontManagerServiceImpl`.
1. Voer een van de volgende handelingen uit om CQ-DAM-Handler-Gibson Font Manager Service te configureren:

   * Geef in de directory System Fonts (Systeemlettertypen) het volledige pad naar de map Fonts op uw systeem op. Als u bijvoorbeeld een Mac-gebruiker bent, kunt u het pad opgeven als */Library/Fonts* in de optie Systeemlettertypen. [!DNL Experience Manager] haalt de lettertypen op uit deze map.
   * Maak een map met de naam `fonts` in de map `crx-quickstart`. CQ-DAM-Handler-Gibson Font Manager Service haalt de lettertypen automatisch op op de locatie `crx-quickstart/fonts`. U kunt dit standaardpad overschrijven vanuit de directory Adobe Server Fonts.

   * Maak een nieuwe map voor lettertypen op uw systeem en sla de gewenste lettertypen op in de map. Geef vervolgens het volledige pad naar die map op in de directory met lettertypen voor klanten.

1. Open de PDF-configuratie van de annotatie via de URL `https://[aem_server]:[4502]/system/console/configMgr/com.day.cq.dam.core.impl.annotation.pdf.AnnotationPdfConfig`.
1. Configureer de Annotatie-PDF met de juiste set lettertypefamilies als volgt:

   * Neem de tekenreeks `<font_family_name_of_custom_font, sans-serif>` op in de optie font-family. Als u bijvoorbeeld annotaties wilt afdrukken in CJK (Chinees, Japans en Koreaans), neemt u de tekenreeks `Arial Unicode MS, Noto Sans, Noto Sans CJK JP, sans-serif` op in de optie font-family. Als u annotaties wilt afdrukken in het Hindi, downloadt u het juiste lettertype en configureert u de lettertypefamilie als Arial Unicode MS, Noto Sans, Noto Sans CJK JP, Noto Sans Devanagari, sans-serif.

1. Start de [!DNL Experience Manager]-implementatie opnieuw.

Hier is een voorbeeld van hoe u [!DNL Experience Manager] kunt vormen om annotaties in CJK (Chinees, Japans en Koreaans) te drukken:

1. Download Google Noto CJK-lettertypen van de volgende koppelingen en sla deze op in de lettertypemap die is geconfigureerd in Font Manager Service.

   * All in One Super CJK font: [https://www.google.com/get/noto/help/cjk/](https://www.google.com/get/noto/help/cjk/)
   * Noto Sans (voor Europese talen): [https://www.google.com/get/noto/](https://www.google.com/get/noto/)
   * Geen lettertypen voor een taal van uw keuze: [https://www.google.com/get/noto/](https://www.google.com/get/noto/)

1. Configureer het PDF-bestand met annotaties door de parameter font-family in te stellen op `Arial Unicode MS, Noto Sans, Noto Sans CJK JP, sans-serif`. Deze configuratie is standaard beschikbaar en werkt voor alle Europese en CJK-talen.
1. Als de taal van uw keuze afwijkt van de talen die in stap 2 worden genoemd, voegt u een geschikt item (gescheiden door komma&#39;s) toe aan de standaardlettertypefamilie.

## Elementversies {#asset-versioning} maken, beheren, voorvertonen en herstellen

Met Versioning maakt u een momentopname van digitale elementen op een bepaald tijdstip. Versioning helpt bij het terugzetten van elementen naar een vorige status op een later tijdstip. Als u bijvoorbeeld een wijziging in een element ongedaan wilt maken, herstelt u de onbewerkte versie van het element. In [!DNL Experience Manager] kunt u een versie maken, de huidige revisie bekijken, verschillen tussen twee versies van afbeeldingen naast elkaar weergeven en een element terugzetten naar de vorige versie.

U kunt versies in [!DNL Experience Manager] in de volgende scenario&#39;s tot stand brengen:

* Upload een element met dezelfde bestandsnaam die op dezelfde locatie bestaat. Dit kan een nieuw element of een gewijzigde versie van hetzelfde element zijn.
* Bewerk een afbeelding in [!DNL Experience Manager] en sla de wijzigingen op.
* Bewerk de metagegevens van een element.
* Gebruik [!DNL Experience Manager] desktop app om een bestaand element uit te checken, te bewerken en [uw wijzigingen te uploaden](https://experienceleague.adobe.com/docs/experience-manager-desktop-app/using/using.html?lang=en#edit-assets-upload-updated-assets).

U kunt automatische versioning ook inschakelen via een workflow. Wanneer u een versie voor een element maakt, worden de metagegevens en uitvoeringen samen met de versie opgeslagen. Uitvoeringen zijn alternatieven voor dezelfde afbeeldingen, bijvoorbeeld een PNG-uitvoering van een geüpload JPEG-bestand.

1. Navigeer naar de locatie van het element waarvoor u een versie wilt maken en klik erop om de voorvertoning te openen. Open in de linkerbovenhoek van de pagina het menu en selecteer **[!UICONTROL Timeline]**.

   ![Selecteer de optie Tijdlijn in het navigatiemenu aan de linkerkant](assets/timeline.png)

   *Afbeelding: Open het menu in de linkerbovenhoek van de pagina en selecteer de  [!UICONTROL Timeline] optie.*

1. Een versie van het element maken:

   * Klik op **[!UICONTROL Actions]** onderaan.
   * Klik op **[!UICONTROL Save as Version]** om een versie voor het element te maken. Voeg desgewenst een label en opmerking toe.
   * Klik **[!UICONTROL Create]** om een versie tot stand te brengen.

      ![Elementversie maken van zijbalk](assets/create-new-version-from-timeline.png)

      *Afbeelding: Maak een versie van een element op de  [!UICONTROL Timeline] linkerzijbalk.*

1. Een versie van een element weergeven:

   * Klik **[!UICONTROL Show All]** in [!UICONTROL Timeline].
   * Klik op **[!UICONTROL Versions]**. Alle versies die voor een element zijn gemaakt, worden weergegeven in de linkerzijbalk.

   * Selecteer een specifieke versie van het element en klik op **[!UICONTROL Preview Version]**.

1. Ga als volgt te werk om terug te keren naar een oudere versie van het element. Na het terugkeren, wordt deze versie getoond in de [!DNL Assets] interface en is beschikbaar voor gebruik.

   * Klik op een versie van het element. Voeg desgewenst een label en een opmerking toe.
   * Klik op **[!UICONTROL Revert to this Version]**.

      ![Een versie selecteren om naar deze versie terug te keren](assets/select_version.png)

      *Afbeelding: Selecteer een versie en herstel deze. Het wordt de huidige versie die dan beschikbaar aan de gebruikers DAM is.*

1. Voer de volgende stappen uit om twee versies van een afbeelding te vergelijken:
   * Klik op de versie die u met de huidige versie wilt vergelijken.
   * Sleep de schuifregelaar naar links om deze versie over de huidige versie heen te plaatsen en te vergelijken.

   ![Gebruik de schuifregelaar om de geselecteerde versies van een element te vergelijken met de huidige versie](assets/version-slider.gif)

   *Afbeelding: Gebruik de schuifregelaar om de geselecteerde versies van een element eenvoudig te vergelijken met de huidige versie.*

### Een workflow starten op een element {#starting-a-workflow-on-an-asset}

Als u een workflow wilt toepassen om een element te verwerken, raadpleegt u [workflow starten op een element](/help/assets/assets-workflow.md#apply-a-workflow-to-an-asset).

## Verzamelingen {#collections}

Een verzameling is een geordende set elementen. Gebruik verzamelingen om gerelateerde elementen te delen tussen gebruikers of om vergelijkbare elementen te groeperen voor eenvoudige detectie.

* Een verzameling kan elementen van verschillende locaties bevatten, omdat deze alleen verwijzingen naar deze elementen bevatten. Bij elke verzameling blijft de referentiële integriteit van de elementen behouden.
* U kunt verzamelingen delen met meerdere gebruikers met verschillende machtigingsniveaus, zoals bewerken, weergeven, enzovoort.

Zie [Verzamelingen beheren](/help/assets/manage-collections.md) voor meer informatie over verzamelingsbeheer.
