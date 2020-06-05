---
title: Opmerkingen bij de release AEM 6.5 Service Pack
description: Opmerkingen bij de release specifiek voor Adobe Experience Manager 6.5 Service Pack 5.
docset: aem65
mini-toc-levels: 1
translation-type: tm+mt
source-git-commit: 46f28926af6cbf3999a4c81cb1f1297b09c07f9f
workflow-type: tm+mt
source-wordcount: '4374'
ht-degree: 0%

---


# Opmerkingen bij de release Adobe Experience Manager 6.5 Service Pack {#aem-service-pack-release-notes}

## Geen informatie {#release-information}

| Producten | **Adobe Experience Manager 6.5** |
|---|---|
| Versie | 6.5.5.0 |
| Type | Service Pack-release |
| Date | 4 juni 2020 |
| URL downloaden | [Delen](https://www.adobeaemcloud.com/content/marketplace/marketplaceProxy.html?packagePath=/content/companies/public/adobe/packages/cq650/servicepack/AEM-6.5.5.0)van pakketten, [softwaredistributie ](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/servicepack/aem-service-pkg-6.5.5.zip) |

## Wat is inbegrepen in de Manager van de Ervaring van Adobe 6.5.5.0 {#what-s-included-in-aem}

Adobe Experience Manager 6.5.5.0 is een belangrijke update met nieuwe functies, belangrijke verbeteringen en prestaties die door de klant zijn aangevraagd, stabiliteit en verbeteringen op het gebied van beveiliging, die zijn uitgebracht sinds de algemene beschikbaarheid van de release van 6.5 in **april 2019**. Het bestand kan boven op Adobe Experience Manager (AEM) 6.5 worden geïnstalleerd.

Enkele belangrijke functies en verbeteringen die in AEM 6.5.5.0 zijn geïntroduceerd, zijn:

* De kolomnamen aanpassen die in AEM Inbox worden weergegeven.

* Het verbeteren van toegankelijkheid op diverse gebieden in het Beheer van de Inhoud van het Web AEM (WCM) zoals de Redacteur van de Pagina, de Componenten van de Kern, RTE, en gebruikersinterface Admin.

* Een interactieve communicatie opslaan als concept.

* Ondersteuning voor [!DNL Oracle WebLogic 12] AEM Forms on JEE.

* Uitzonderingsafhandeling is nu verbeterd in de stroom van de gebruikersinterface van [!DNL Adobe Experience Manager] Elementen.

* Een nieuwe methode `getRemoteAssetPublishURL` wordt toegevoegd aan `com.day.cq.dam.api.s7dam.scene7.ImageUrlApi` interface om te krijgen publiceer URL voor Dynamische Media Scene7.

* [Verbeteringen](#assets-6550-changes) in de toegankelijkheid van [!DNL Adobe Experience Manager] middelen in overeenstemming met de Web Content Accessibility Guidelines (WCAG).

* Integratie van pakket delen met Adobe Experience Manager is verwijderd.

* De ingebouwde opslagplaats (Apache Jackrabbit Oak) wordt bijgewerkt naar versie 1.22.3.

Voor een volledige lijst van eigenschappen, zeer belangrijke hoogtepunten, zeer belangrijke eigenschappen die in AEM 6.5 de dienstpak 5 worden geïntroduceerd, zie [Nieuw in de Manager van de Ervaring van Adobe 6.5 Service Pack 5](new-features-latest-service-pack.md) .

Hier volgt een lijst met oplossingen uit de release van [!DNL Experience Manager] 6.5.5.0.

### Sites {#sites-6550}

* AEM-sites bieden een optie voor het publiceren of ongedaan maken van de publicatie van een pagina vanuit de alias. De optie werkt niet (NPR-33415).
* Wanneer een lay-outcontainer wordt verwijderd uit een sjabloon met meerdere sjablonen, wordt de sjabloon niet correct weergegeven (NPR-33347).
* Wanneer een pagina met AEM-sites deel uitmaakt van een grote inhoudenset met meerdere live-kopieën, kan de voorvertoning van de paginaversie niet worden geladen (NPR-33311).
* Wanneer u de opdracht Verplaatsen gebruikt om de naam van een pagina met AEM-sites te wijzigen, wordt de paginatitel niet bijgewerkt (NPR-33264).
* Wanneer u pagina&#39;s door de kolommening beweegt, verdwijnen de kolommen (NPR-33216).
* Wanneer de naam van een lokale component in een taalkopie identiek is aan de naam van een component in het concept en de component uit blauwdruk wordt opgerold, wordt de term _msm_moving niet toegevoegd aan de naam van de lokale component (NPR-33208).
* De server voor omleiding van pagina voegt .html toe aan een URL voor AEM-sites waar ResourceType niet cq:Page is (NPR-33176).
* Wanneer u een substructuur plakt, is er geen optie om te bepalen of corresponderende subpagina&#39;s moeten worden geplakt (NPR-33149).
* Het aantal resultaten in levend gebruik van een component is beperkt tot nummer 49 (NPR-33058).
* Wanneer u een inhoudsfragment baseert op een schema en het een verplicht tekstgebied of een weggebied bevat, kan het inhoudsfragment niet opslaan (NPR-33007).
* Wanneer u een aangepaste component maakt met de fragmentcomponent voor out-of-the-box-ervaring en deze gebruikt op pagina&#39;s van AEM-sites, geeft AEM geen referenties (gebruik) weer voor de aangepaste component (NPR-32852).
* Wanneer u de naam van een map wijzigt met een groot aantal verwijzingen, worden veel verwijzingen naar de map niet bijgewerkt (NPR-32765).
* Wanneer u de optie voor bronbewerking inschakelt, wordt deze beschikbaar voor inlineopties voor volledig scherm, maar blijft deze beschikbaar voor opties voor het bewerken van het dialoogvenster en het volledige scherm van de RTF-editor (NPR-32763).
* Als u een veld met meerdere velden hebt en een vereist veld (zoals een vervolgkeuzelijst of een padveld) in de pagina-eigenschappen van een blauwdruk bevat, worden de pagina-eigenschappen van de live kopie niet opgeslagen wanneer een pagina met een dergelijk veld wordt opgerold. (NPR-32751)
* Schermlezers kunnen niet door de kopstructuur van een pagina navigeren. Bovendien heeft het tabblad Componenten het verkeerde label (NPR-32648).
* Wanneer de paginering begint, laadt de Plukker van de Fragmenten van de Ervaring niet alle punten (NPR-32605).
* Auteurmachtigingen voor het lezen, wijzigen, maken en verwijderen van live kopieën worden ingetrokken. Elke auteur moest lees- en wijzigingstoestemmingen uitdrukkelijk verstrekken om pagina&#39;s binnen een Blauwdruk (NPR-32550) te bewegen.
* Inhoudsauteurs kunnen de functie Starten niet maken voor een pagina die is geïntegreerd met Adobe Analytics (NPR-32548).
* Wanneer een gebruiker de overerving met synchronisatie hervat, synchroniseert de live kopie van de bovenliggende pagina niet met de blauwdruk en geeft deze een onjuiste status weer (NPR-32500).
* Het laden van de pagina voor de AEM-editor voor sites duurt meer dan 15 seconden (NPR-32413).
* In bepaalde velden wordt de optie Overerving annuleren niet weergegeven (NPR-32362).
* Wanneer u een pad selecteert voor een ervaringsfragmentcomponent en het selectievakje Dialoogvenster Selectie openen inschakelt, wordt niet naar het geselecteerde pad genavigeerd in de padbrowser (NPR-32308).
* Wanneer u van AEM 6.2 aan AEM 6.5 bevordert, toont de component Parsys van statische malplaatjes niet correct. De hoogte van de component Parsys wordt geplaatst aan 0 en de componenten binnen het zijn niet zichtbaar. (NPR-33663).
* Wanneer een gebruiker een Layout Container op dezelfde pagina kopieert en plakt, worden componenten in een Layout Container niet weergegeven (NPR-33648).
* Met de health check van de verzender wordt een `Invalid cookie header` waarschuwingsbericht weergegeven in de logbestanden (NPR-33629).

### Assets {#assets-6550-changes}

**Verbeterde toegankelijkheid in Experience Manager-elementen**

* Het is nu mogelijk om de toetsenbordfocus op de [!UICONTROL Comments] lijst te plaatsen en op [!UICONTROL Create] versieopmerkingen te klikken [!UICONTROL Create new version] in het [!UICONTROL Timeline] middelenpaneel (NPR-33424).

* Het is nu mogelijk om [!UICONTROL View Settings] optie voor activa te bereiken en montages in [!UICONTROL View Settings] dialoog te veranderen gebruikend toetsenbordsleutels (NPR-33420).

* De keuzelijst met keuzelijsten met invoervak (in verschillende velden op verschillende pagina&#39;s) bevat nu items als een lijst met opties die door schermlezers kunnen worden aangekondigd (NPR-33516).

* De sorteerfunctionaliteit van sorteerbare koppen (in lijstweergave, [!UICONTROL Timeline] weergave en [!UICONTROL Manage Publication] pagina) wordt nu door schermlezers aangekondigd en sorteerbesturingselementen op kolomkoppen zijn toegankelijk via het toetsenbord (NPR-32979).

* De aanklikbare elementen (zoals commentaarkaarten, versie-updates, keuzelijsten met invoervak en menupictogrammen) zijn nu brandbaar en kunnen worden geactiveerd met het toetsenbord (NPR-33514).

* De functionaliteit (of het doel van de actie) van inzichtspictogrammen (voor gebruik, indrukkingen en klikken) op [!UICONTROL Insights View] worden nu correct aangekondigd door schermlezers (NPR-33513).

* Alleen-lezen formuliervelden (bijvoorbeeld uitgeschakelde velden op [!UICONTROL Basic tab] element [!UICONTROL Properties]) kunnen nu met het toetsenbord worden gebruikt (NPR-33493, CQ-4273031).

* Labels in verschillende invoervelden zijn nu permanente labels (dus toegankelijk) en niet alleen plaatsaanduidingslabels, die zijn verdwenen bij het invoeren van tekst (NPR-33475).

* Verschillende kopniveaus (zoals paginatitels en sectiekoppen) worden nu gezien als koppen met verschillende niveaus voor schermlezers (NPR-33471).

* Interactieve elementen in de gebruikersinterface, zoals koppelingen en opties (op koptekst- en zoomopties van de elementenpagina, mapnavigatie), zijn nu toegankelijk via een toetsenbord (NPR-33468, CQ-4271412).

* De indicatoren [!UICONTROL Options], [!UICONTROL Scope]en [!UICONTROL Workflows] progress op de [!UICONTROL Manage Publication] pagina worden nu correct door schermlezers weergegeven als voortgangsindicatoren in plaats van tabbladen (NPR-33416).

* De kleur van sterrenbeoordelingspictogrammen (zoals in de [!UICONTROL Rating] sectie van het [!UICONTROL Advanced] tabblad in de asset- [!UICONTROL Properties] of kaartweergave) wordt gewijzigd, zodat het juiste contrast zichtbaar is voor gebruikers met een beperkt gezichtsvermogen en zonder kleurperceptie (NPR-33414).

* De pijl-omhoog naast de pagina met gegevens over [!UICONTROL Comment] velden op assets kan nu worden geopend met behulp van toetsenbordtoetsen (NPR-33397).

* De uitgebreide en samengevouwen staten van de [!UICONTROL Tags] dialoog over de navigatie tussen de elementen [!UICONTROL Properties] en de linkerspoorstaaf (op de gebruikersinterface van de middelen) worden nu correct door schermlezers aangekondigd (NPR-33396).

* De titels van alle gebrowste pagina&#39;s op [!DNL Adobe Experience Manager] Elementen zijn nu uniek (NPR-33343).

* Tijdens het navigeren door boomstructuur worden verschillende elementen van het besturingselement voor de structuurweergave nu correct aangekondigd door schermlezers (NPR-33304).

* Verschillende versies van elementen in de [!UICONTROL Timeline] weergave op de pagina met informatie over elementen zijn nu toegankelijk met behulp van toetsenbordtoetsen (NPR-33283).

* Namen van zoeksuggesties die worden weergegeven in de keuzelijst Omnzoekopdracht worden nu door schermlezers aangekondigd tijdens het gebruik van de zoekfunctie (NPR-33280).

* Klikbare elementen en [!UICONTROL Go to link] in [!UICONTROL References rail] worden nu door schermlezers aangekondigd als klikbare elementen (NPR-33278).

* Informatie over de tabelstructuur (zoals rij 1, cel 1, tabel) van het [!UICONTROL Share Link] dialoogvenster wordt niet meer door schermlezers aangekondigd wanneer het dialoogvenster wordt geopend (NPR-33268).

* Het doel van verschillende keuzelijstelementen (zoals het veld Pad en de optie om het dialoogvenster Selectie te openen op het tabblad Standaard van Eigenschappen van element) worden nu correct aangekondigd door schermlezers (NPR-33235).

* De informatie dat de rijen in de lijst van de lijstmening selecteerbaar zijn wordt nu meegedeeld aan de gebruikers van de schermlezer wanneer toetsenbordnadruk op hen is. Deze informatie wordt bekendgemaakt wanneer de muis op de rijen wordt gehouden (NPR-33234).

* Opties (voor [!UICONTROL x]) het verwijderen van alle geselecteerde codes onder het [!UICONTROL Tags] veld op het [!UICONTROL Basic] tabblad [!UICONTROL Properties] zijn nu toegankelijk voor schermlezers (NPR-33206).

* Datumkiezer voor kalenderdatums kan nu worden geactiveerd en geactiveerd met het toetsenbord van schermlezers en gebruikers van waargenomen toetsenborden (NPR-33200).

* Als u schakelt tussen de lijstweergave en de kaartweergave, wordt de functionaliteit (van het aanpassen van weergaven) nu correct weergegeven voor schermlezers (NPR-33069).

* Het menu in de linkerrail is nu toegankelijk. Functionaliteit en doel van het uitbreiden van het menu worden door schermlezers op de juiste wijze aangekondigd (NPR-33068).

* De keuzelijst en veel andere gebruikersinterface-elementen zijn nu toegankelijk voor gebruikers met een niet-visuele schermlezer. De volgende informatie hierover wordt door schermlezers aangekondigd (NPR-33040):

   * of gebruikersinvoer op een element is vereist voordat het formulier wordt verzonden.
   * of een element niet bewerkbaar is.
   * of een widget is geselecteerd of niet.

* De optie om filterzijbalk te openen kan nu met het toetsenbord worden geopend (NPR-32842, CQ-4273018).

* Het besturingselement voor selectievakjes in de kolomkop van de lijstweergave is nu toegankelijk en het doel van het gebruik van het besturingselement wordt door schermlezers aangekondigd (NPR-32722, NPR-33005).

* Labels voor uren (HH) en minuten (mm) velden in de datumkiezer voor de kalenderdatum zijn nu permanente labels in plaats van plaatsaanduidingslabels en verdwijnen niet wanneer de gebruiker tekst in deze velden invoert (NPR-32720).

* De koppelingstekst van berichten (die wordt weergegeven nadat op het belpictogram is geklikt) wordt nu aangekondigd voor gebruikers van schermlezers die met Tab toegang krijgen tot elke koppeling (NPR-32645).

* [!UICONTROL Select], [!UICONTROL Download], [!UICONTROL Properties]en [!UICONTROL More Actions] opties op assetkaarten in [!UICONTROL Insights View] zijn nu toegankelijk via het toetsenbord (NPR-32609).

* Visueel verborgen inhoud (zoals de inhoud van de menubalk van de header op zoekresultaten) wordt niet meer aangekondigd door schermlezers wanneer deze toegang krijgen met het toetsenbord (NPR-32606).

* Het doel van de etiketten op besturingselementen om naar volgende en vorige maanden in een kalenderdatumkiezer te gaan, worden nu door schermlezers bekendgemaakt (NPR-32604).

* Sterrenclassificatiepictogrammen zijn nu brandbaar en kunnen worden geactiveerd met behulp van toetsenbordtoetsen (NPR-32513).

* Functionaliteit voor het regelen van het videovolume is nu toegankelijk via de Tab-toets (om de volumeschuifregelaar te activeren) en de pijltoetsen (om het volume aan te passen) op het toetsenbord (NPR-32065).

* Het doel van ondergebonden ([!UICONTROL From]) en bovengebonden ([!UICONTROL To]) invoervelden van het filter Bestandsgrootte wordt nu bekendgemaakt aan gebruikers van niet-zichtbare schermlezers (NPR-32064).

* Het [!UICONTROL Languages] [!UICONTROL Create and Translate] formuliermenu is nu toegankelijk voor schermlezers in de bladermodus (CQ-4293906).

* Het [!UICONTROL References] paneel is nu toegankelijk met de volgende verbeteringen (NPR-33261, CQ-4293798):

   * In de modus Bladeren wordt de focus van schermlezers niet meer verplaatst naar verborgen bewerkingsvelden met meerdere regels onder [!UICONTROL Site References], [!UICONTROL Asset References], [!UICONTROL Copies]en [!UICONTROL Form References] secties.

   * Schermlezers geven nu de rol van [!UICONTROL Site References] en [!UICONTROL Language Copies] elementen aan.

   * De focus van schermlezers in de modus Bladeren verschuift in een betekenisvolle volgorde naar verschillende elementen.

* [!UICONTROL Metadata Schema Editor] De pagina en de elementen ervan zijn nu toegankelijk met het toetsenbord en zijn gebruiksvriendelijk voor schermlezers (CQ-4290962, CQ-4272953).

* Het doel van het [!UICONTROL x] pictogram op de optie om momenteel geselecteerde tags te verwijderen, wordt ook bekendgemaakt samen met het aantal geselecteerde tags (CQ-4273017).

* Decoratieve pictogrammen en afbeeldingen worden nu genegeerd door schermlezers om verwarring te voorkomen voor niet-zichtbare gebruikers die een schermlezer gebruiken (CQ-4272944).

**Problemen die zijn verholpen met middelen van Experience Manager**

[!DNL Adobe Experience Manager] 6.5.5.0 Middelen bieden oplossingen voor de volgende problemen:

* [!UICONTROL Start] optie op [!UICONTROL Create Workflow] dialoog voor activa in een inzameling wordt onbruikbaar gemaakt, daardoor verhinderend werkschema om worden teweeggebracht (NPR-32471).

* Bij het gebruik van trapsgewijze vervolgkeuzelijsten in metagegevensschema&#39;s verdwijnt bij het selecteren en opslaan van een vervolgkeuzelijst met een apostrof (uit de vervolgkeuzelijst met onderliggende elementen) de geselecteerde optie apostrof na het opnieuw openen van het element [!UICONTROL Properties] (NPR-32649).

* [!UICONTROL Asset Insights Sync Job] stopt en mislukt als er ongeldige items worden aangetroffen (aan de zijde Analytics) in plaats van naar de volgende vermelding te gaan (NPR-32674).

* Gyroscoop werkt niet omdat bewegingssensoren standaard zijn uitgeschakeld in mobiele browsers in panoramische viewer (CQ-4272937).

* [!UICONTROL Connected Assets Configuration] De wizard werkt niet met een fout van 404 bij de installatie van versie 6.5.3 op 6.5.1 (NPR-32730).

* Tijdens het XMP-schrijfproces veranderen alle eigenschappen van aangepaste naamruimte-metagegevens het aangepaste naamruimtevoorvoegsel in ns2 in tegenstelling tot het naamruimtevoorvoegsel dat is geconfigureerd (NPR-32748).

* Lazy loading wordt niet geactiveerd en er worden slechts 100 assets weergegeven bij het selecteren om de taken te bekijken vanuit de berichten in het Postvak IN (NPR-32750).

* `NullPointerException` wordt waargenomen omdat voorkeuren voor ontbrekende knooppunten ontbreken in het nieuwe gebruikersprofiel (SAML/SSO). Deze fout verhindert nieuw het programma geopende gebruikers om [!DNL Adobe Experience Manager Stock] integratie (NPR-32777) te gebruiken.

* Traversale waarschuwingen worden waargenomen in logboeken bij het openen van een slimme verzameling die meer dan 10.000 activa bevat (NPR-32980).

* De namen van activa worden veranderd in kleine letters wanneer het bewegen van activa van één omslag aan een andere in het [!DNL Adobe Experience Manager] werken op Dynamische Strijwijze van Media Scene7 (NPR-32995).

* Een doorzocht middel kan niet worden geschrapt nadat aan zijn eigenschappen van de onderzoeksresultaten navigeert en dan naar onderzoeksresultaten teruggaat om het te schrappen (NPR-32998).

* [!UICONTROL Next] blijft uitgeschakeld bij het selecteren van een doelmap in de [!UICONTROL Move Assets] interface (NPR-33356).

* [!UICONTROL Next] Deze optie is niet ingeschakeld bij het selecteren van het bovenliggende knooppunt (waar één onderliggende map zichtbaar is) en het selecteren van de onderliggende map (NPR-33275).

* Het in- en uitchecken van machtigingen is uitgeschakeld in Adobe Asset Link (AAL) voor gebruikers met verwijderingsmachtigingen, zelfs als andere machtigingen zoals lezen, maken of wijzigen aan hen zijn toegestaan (NPR-33272).

* Smart Crop-uitvoeringen zijn niet beschikbaar in het dialoogvenster voor het downloaden van bestanden (NPR-33167).

* Uitzondering wordt waargenomen in logboeken bij het openen van uitvoeringen per spoor voor een PDF onder een map met profiel voor slimme uitsnijdingen (CQ-4294201).

* Voorinstellingen voor afbeeldingen publiceren niet als deze standaard [!UICONTROL Dynamic Media sync mode] is uitgeschakeld in AEM met de runmode Dynamic Media Scene7 (CQ-4294200).

* De verwerking van bedrijfsmiddelen tijdens bulkupload blijft vastzitten en de werkstroominstantie toont vastgelopen instanties van update DAM-middelen (CQ-4293916).

* Het creëren van een Dynamische configuratie van Media op AEM werkt, maar op het gebruikersinterface gebeurt niets bij het selecteren van sparen (CQ-4292442).

* Voorvertoning van f4v-video-elementen werkt niet in progressief afspelen op Safari/Mac (CQ-4289844).

* Er wordt een extra map gemaakt bij het slim uitsnijden van middelen in een bovenliggende map met een puntteken in de naam (CQ-4289337). `.`

* De miniatuur wordt verbroken en de videoverwerkingsbanner wordt niet weergegeven wanneer een video wordt gekopieerd (CQ-4284125).

* In de DIG-viewer worden in Firefox voor sommige modellen met lege cameraweergaven ten onrechte lege miniaturen weergegeven (CQ-4283447).

* De prestatieproblemen die zijn vastgelegd in 6.5.5.0 zijn (CQ-4279206):

   * Het uploaden van grote binaire bestanden naar Dynamic Media Image Processing-servers duurt te lang.

   * De tijd van de duimnagelgeneratie op AEM stijgt wegens Dynamische architectuur van Media Scene7.

* De dynamische de migratiekwesties van Media Scene7 ontbreken voor klanten met groot aantal activa (CQ-4279206).

* De lay-out van de video 360-viewer wordt verbroken wanneer deze `setVideo` wordt gebruikt en de video wordt bij gebruik afgebroken `video= modifier` (CQ-4263201).

* Er wordt een foutbericht weergegeven tijdens de installatie van het AEM SDL-pakket (NPR-33175).

### Platform {#platform-6550}

* Het [!DNL Sling] filter wordt niet aangeroepen als het `sling:match` kaartitem wordt gemaakt onder `/etc/maps` (NPR-33362).
* AEM loopt vast als gevolg van een segmentatiefout met [!DNL Apache Lucene] (NPR-32988).
* [!DNL Jackson] kernpakket ontbreekt in AEM uber jar-bestand (NPR-32848).
* CRXDE Lite laadt geen inhoud voor gebruikers zonder LEZEN toestemming op het `jcr:primaryType` bezit voor een knoop (NPR-32611).
* [!DNL Granite] De onderhoudstaakplanner wordt te vaak opnieuw geïnitialiseerd tijdens AEM-implementaties (CQ-4294627).
* Wanneer een SQL vraag langere tijd, bijvoorbeeld 7 uren loopt, houdt op met antwoorden (NPR-33044).

### User Interface {#ui-6550}

* Selectie van keuzerondjes blijft niet behouden in een multiveld (NPR-33309).
* Lazy loading limit werkt niet voor de lijstweergave (NPR-33124).
* De resultatenpagina van het onderzoek toont geen bericht als er geen gelijken (NPR-32974) zijn.
* Het filter van Onderzoek keert alle gelijken onder `/content` knoop terug die de geselecteerde plaats (NPR-32849) negeren.

### Integrations {#integrations-6550}

* De interne cache wordt gewist wanneer een pagina met een Adobe Target-component wordt gepubliceerd (NPR-33162).
* Integratie met Adobe Target werkt niet op [!DNL Windows Internet Explorer] 11 (NPR-33111).
* Wanneer u Adobe Target configureert, worden de [!UICONTROL Company] [!UICONTROL Report Suite] velden en de velden niet weergegeven bij het selecteren van een rapportbron (NPR-32502).
* Wanneer u fragmenten exporteert met Adobe I/O, worden metagegevens zoals het bronproduct niet geëxporteerd naar Adobe Target (NPR-32159).
* Erkende IMS-gebruikers in lokale AEM-beheergroep kunnen geen IMS-configuraties maken of wijzigen (NPR-33045).
* Op de pagina met Adobe Launch-configuraties worden niet alle records weergegeven (NPR-33011).
* Gebruikers in een groep van inhoudsauteurs kunnen vanwege een JavaScript-fout (NPR-32996) de eigenschappen van een Adobe Target-component niet bewerken.

### Omzettingsprojecten {#translation-6550}

* Vertaalde tags worden niet geïmporteerd in AEM van vertaalservices van derden (NPR-33154).
* Op de pagina voor vertaalconfiguratie wordt een onjuiste vertaalprovider weergegeven dan de provider die wordt gebruikt voor de vertaling (NPR-32971).
* Als u een ervaringsfragmentmap toevoegt aan een bestaand vertaalproject, wordt een nieuw project gemaakt (NPR-32843).
* Er is een `NullPointerException` fout opgetreden in de logboeken met een vertaaltaak (NPR-32628).

### WCM {#wcm-6550}

* Pagina-editor - De [!DNL Sites] Pagina-editor staat gebruikers met alleen het toetsenbord niet toe de hoofdinhoud over te slaan in plaats van de tabfocus te verplaatsen via alle opties in de koptekst (CQ-4293883).
* Pagina-editor - Deelvensters die de component Well gebruiken en opgeslagen gegevens bevatten, worden niet weergegeven vanwege updates in [!DNL Chrome] en [!DNL Firefox] versies (CQ-4292995).
* MSM - Als u een component van de pagina verwijdert, wordt de component niet verwijderd uit de gepubliceerde versie van de pagina (CQ-4292360).

### Brand Portal {#assets-brand-portal-6550}

* Als u een gepubliceerd metagegevensschema verwijdert uit [!DNL Brand Portal] resultaten, treedt er een fout op (CQ-429/2063).
* Als een beheerder [!DNL Experience Manager Assets] 6.5.4 configureert met Brand Portal via Adobe Developer Console, kan de [!DNL Brand Portal] gebruiker de middelen van een bijdragemap niet van [!DNL Brand Portal] naar [!DNL Experience Manager]. (NPR-33046).
* Dubbele replicatie van de bovenliggende mappen die conflicten veroorzaken (NPR-33001).

### Gemeenschappen {#communities-6550}

* Kan een kaart in moderatieconsole niet verwijderen met de snelmenuoptie (NPR-33117).
* Er treedt een fout op bij het openen van de [!UICONTROL Activity Stream] pagina (NPR-33146).
* Groepen die op een instantie van de auteur worden verwijderd, worden niet uit alle publicatie-instanties verwijderd (NPR-33199).
* Auteurs worden na het maken van een nieuwe groep niet doorgestuurd naar de [!UICONTROL Community Group] sectie op [!DNL Internet Explorer] 11 (NPR-33205).
* Het openen van een bericht in AEM Inbox verandert niet de status van het bericht aan Gelezen (NPR-32764).
* Als u een [!DNL Communities] groep bewerkt en de miniatuurafbeelding wijzigt, wordt de groepminiatuurafbeelding niet bijgewerkt (NPR-32599).
* Een gebruiker kan geen e-mail naar een andere gebruiker in een gemeenschap (NPR-32598) verzenden.
* Een verzonden blog wordt pas weergegeven wanneer de gebruiker de pagina vernieuwt (NPR-32391).
* Tijdens het maken van een versie van meldingen en abonnementen op door gebruikers gegenereerde inhoud (UGC) wordt een onjuiste id van de bronpagina opgeslagen (CQ-4279355, CQ-4289703).

### Workflow {#workflow-6550}

* De [!UICONTROL Timeline] optie in de linkerspoorstaaf neemt meer tijd om te laden dan verwacht (NPR-32851).
* Nadat u een AEM-instantie opnieuw hebt gestart, bevat de e-mail voor de overzichtstaak voor een verzameling een onjuiste payload-koppeling (NPR-32774).

### Formulieren {#forms-6550}

>[!NOTE]
>
>AEM Service Pack bevat geen oplossingen voor AEM-formulieren. Ze worden geleverd met behulp van een apart Forms add-on pakket. Daarnaast wordt een cumulatief installatieprogramma uitgebracht dat oplossingen voor AEM Forms in JEE bevat. Zie [Invoegtoepassing](#install-aem-forms-add-on-package) van AEM-formulieren installeren en AEM-formulieren [installeren in JEE](#install-aem-forms-jee-installer)voor meer informatie.

* Correspondentenbeheer: De volgorde van de activa in een doelgebied verandert na indiening van een brief (NPR-33359, NPR-33153).
* Adaptieve formulieren: Wanneer een gebruiker een adaptief formulier bewerkt, werkt de [!UICONTROL Start Workflow] optie in het [!UICONTROL Page Information] menu niet (NPR-33004).
* Adaptieve formulieren: De gebruiker kan geen adaptief formulier opslaan met meer dan één bijlage (NPR-32997).
* Adaptieve formulieren: Als u de indeling van het deelvenster wijzigt in een adaptief formulier, treedt er een fout op (CQ-4293880).
* Adaptieve formulieren: Een nieuwe regel naar een tekenreeks in een woordenboek voor adaptieve formulieren voegt `&#xa;` tekens toe aan het woordenboek (NPR-33266).
* Toegankelijkheid van adaptieve formulieren: Wanneer een gebruiker een adaptief formulier weergeeft als HTML-formulier, kan het [!UICONTROL Scribble Signature] veld de tabfocus niet behouden (NPR-33159).
* Toegankelijkheid van adaptieve formulieren: De foutberichten die worden weergegeven bij het verzenden van een adaptief formulier, zijn niet gekoppeld aan een `aria-describedBy` kenmerk (NPR-33071).
* Toegankelijkheid van adaptieve formulieren: Velden die verplicht zijn gemarkeerd in een adaptief formulier, hebben niet het verplichte kenmerk ingesteld op Waar in het ARIA-toegankelijkheidsschema (NPR-33070).
* PDFG-service: Wanneer een gebruiker een tekstbestand naar een PDF converteert, worden Japanse tekens niet correct weergegeven (NPR-33238).
* PDFG-service: `CreatePDF` kan een PDF-bestand niet converteren naar de OCR-indeling van PDF (NPR-32994).
* PDFG-service: PDF-conversie mislukt voor de 200e instantie van een [!DNL OpenOffice] document (NPR-32766).
* BackendIntegration: De verzoeken van het het gegevensmodel van de vorm ontbreken aangezien verfrist teken wegens onjuiste inactieve staat (NPR-33169) verloopt.
* Designer: Schermlezers voeren de tabvolgorde uit op basis van de standaard geografische volgorde in plaats van de aangepaste tabvolgorde die is gedefinieerd in het XDP-bestand (NPR-32160).
* Designer: Als de optie Tags toevoegen is ingeschakeld, verdwijnt de rand van het subformulier in de gegenereerde PDF-uitvoer (NPR-32778).

## Installeer 6.5.5.0 {#install}

**Installatievereisten**

* AEM 6.5.5.0 vereist AEM 6.5. Raadpleeg de [upgradedocumentatie](/help/sites-deploying/upgrade.md) voor gedetailleerde instructies.
* De download van het Service Pack is beschikbaar op het Aandeel van het Pakket van Adobe, dat u direct van AEM 6.5 instantie kunt toegang hebben.
* Voor een plaatsing met MongoDB en veelvoudige instanties, installeer AEM 6.5.5.0 op één van de instanties van de Auteur gebruikend de Manager van het Pakket.
* Maak voordat u gaat installeren een momentopname of een nieuwe back-up van uw AEM-instantie.
* Start de instantie opnieuw voor de installatie. Hoewel dat alleen nodig is wanneer de instantie zich nog in de updatemodus bevindt (en dit is het geval wanneer de instantie uit een eerdere versie is bijgewerkt), wordt aangeraden of de instantie langer actief was.

>[!NOTE]
>
>Adobe raadt u niet aan het pakket AEM 6.5.5.0 te verwijderen of te verwijderen.

### Het Service Pack installeren {#install-service-pack}

Voer de volgende stappen uit om het Service Pack op een bestaande AEM 6.5 instantie te installeren:

1. Klik op de koppeling [Pakket delen](https://www.adobeaemcloud.com/content/marketplace/marketplaceProxy.html?packagePath=/content/companies/public/adobe/packages/cq650/servicepack/AEM-6.5.5.0) of [Softwaredistributie](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/servicepack/aem-service-pkg-6.5.5.zip) om het pakket te downloaden.

1. Open [Package Manager](http://localhost:4502/crx/packmgr/index.jsp) en klik op **Upload Package** om het pakket te uploaden.

1. Selecteer de pakketnaam en klik op **Installeren**.

>[!NOTE]
>
>**Dialoogvenster over de UI van de Manager van het Pakket sluit soms ongeschikt tijdens installatie van 6.5.5.0**
>
>Daarom wordt aangeraden te wachten totdat de foutenlogboeken zich stabiliseren voordat u de instantie opent. De gebruiker moet op specifieke logboeken met betrekking tot het verwijderen van updaterbundel wachten alvorens wordt gewaarborgd dat de installaties succesvol zijn. Het gebeurt meestal in Safari, maar kan af en toe in elke browser gebeuren.

**Automatische installatie**

Er zijn twee manieren om AEM 6.5.5.0 in een lopende instantie automatisch te installeren:

A. Plaats het pakket in de `../crx-quickstart/install ` map terwijl de server online beschikbaar is. Het pakket wordt automatisch geïnstalleerd.

B. Gebruik de [HTTP API van de Manager](https://docs.adobe.com/content/docs/en/crx/2-3/how_to/package_manager.html) van het Pakket - zorg ervoor dat u gebruikt `cmd=install&recursive=true` - zodat worden de genestelde pakketten geïnstalleerd.

>[!NOTE]
>
>AEM 6.5.5.0 ondersteunt geen Bootstrap-installatie.

**Installatie valideren**

1. Op de pagina Productinformatie (/system/console/productinfo) wordt de bijgewerkte versietekenreeks weergegeven `Adobe Experience Manager, Version 6.5.5.0` onder Geïnstalleerde producten.

1. Alle bundels OSGi zijn of **[!UICONTROL ACTIVE]** of **[!UICONTROL FRAGMENT]** in de Console OSGi (de Console van het Web van het Gebruik: /systeem/console/bundels).
1. De bundel OSGI `org.apache.jackrabbit.oak-core` is versie 1.10.6 of hoger (de Console van het Gebruik: `/system/console/bundles`).

Raadpleeg de [technische vereisten](/help/sites-deploying/technical-requirements.md)om te zien welke platforms zijn gecertificeerd voor uitvoering met deze release.

### AEM Forms add-on-pakket installeren {#install-aem-forms-add-on-package}

>[!NOTE]
>
>Sla dit over als u geen AEM-formulieren gebruikt. Correcties in AEM Forms worden geleverd via een afzonderlijk invoegpakket.

1. Controleer of u het AEM Service Pack hebt geïnstalleerd.
1. Download het overeenkomstige Forms add-on-pakket dat in de [AEM Forms-releases](https://helpx.adobe.com/aem-forms/kb/aem-forms-releases.html) voor uw besturingssysteem wordt vermeld.
1. Installeer het add-on pakket Formulieren zoals beschreven in de [invoegpakketten](../forms/using/installing-configuring-aem-forms-osgi.md#install-aem-forms-add-on-package)voor AEM Forms.

### AEM-formulieren installeren op JEE {#install-aem-forms-jee-installer}

>[!NOTE]
>
>Sla dit over als u AEM Forms niet gebruikt op JEE. Correcties in AEM Forms on JEE worden geleverd via een afzonderlijk installatieprogramma.

Voor informatie over het installeren van de cumulatieve installateur voor Vormen AEM op JEE en de configuratie na-plaatsing, zie de [versienota&#39;s voor flard 0014](https://helpx.adobe.com/aem-forms/quick-fixes/6-5/jee-patch-0014.html).

### UberJar {#uber-jar}

De UberJar voor AEM 6.5.5.0 is beschikbaar in de [openbare gegevensopslagplaats](https://repo.adobe.com/nexus/content/groups/public/com/adobe/aem/uber-jar/6.5.5/)van Adobe.

Om UberJar in een Geweven project te gebruiken, verwijs naar het artikel, [hoe te UberJar](/help/sites-developing/ht-projects-maven.md) gebruiken en de volgende gebiedsdeel in uw projectPOM omvatten:

```shell
<dependency>
      <groupId>com.adobe.aem</groupId>
      <artifactId>uber-jar</artifactId>
      <version>6.5.5</version>
      <classifier>apis</classifier>
      <scope>provided</scope>
</dependency>
```

## Verouderde functies {#removed-deprecated-features}

Deze sectie bevat een lijst met functies en mogelijkheden die zijn gemarkeerd als verouderd in AEM 6.5.5.0. Functies die volgens plan in een toekomstige versie zullen worden verwijderd, worden eerst op afgekeurd ingesteld, met een andere optie die moet worden gebruikt.

Klanten wordt aangeraden na te gaan of zij in hun huidige implementatie gebruik maken van de functie of het vermogen en plannen maken om hun implementatie te wijzigen en de alternatieve optie te gebruiken.

| Gebied | Functie | Vervanging |
|---|---|---|
| Integrations | Het **[!UICONTROL AEM Cloud Services Opt-In]** scherm is afgekeurd. Met de integratie van AEM en Doel bijgewerkt in AEM 6.5 ter ondersteuning van de standaard-API van het Doel, die verificatie via Adobe IMS en I/O gebruikt, en de groeiende rol van Adobe Launch voor het van instrumenten voorzien van AEM-pagina&#39;s voor analyses en personalisatie, is de Opt-In-wizard functioneel irrelevant geworden. | Systeemverbindingen, Adobe IMS-verificatie en Adobe I/O-integratie configureren via de respectievelijke AEM-cloudservices |

## Known issues {#known-issues}

* Als u [!DNL Experience Manager] 6.5.5.0 met [!DNL Java] 11 installeert, begin de server na het installeren van Service Pack opnieuw. U hoeft het Service Pack niet opnieuw te starten als u het Service Pack met [!DNL Java] 8 installeert.

* Als de naam van een map in de hiërarchie wordt gewijzigd [!DNL Experience Manager Assets] en de geneste map met een element wordt gepubliceerd naar [!DNL Brand Portal], wordt de titel van de map pas bijgewerkt [!DNL Brand Portal] als de hoofdmap opnieuw wordt gepubliceerd.

* Tijdens de installatie van AEM 6.5.5.0, veroorzaakt de update van [!DNL Chrome] versie 83 een probleem in bouwpakketten. Gebruik andere beschikbare browsers, zoals [!DNL Internet Explorer] en [!DNL Firefox], of andere AEM-standaardopties voor het installeren van pakketten om het probleem op te lossen. Het probleem wordt opgelost na de installatie van AEM 6.5.5.0.

* Kan geen e-mail naar de externe SMTP-server verzenden met de standaard e-mailafzender van AEM, omdat communicatie met TLS v1.2 alleen is toegestaan. Verwijder de bundel `javax.mail:mail:1.5.0-b01` uit `system/console` en vernieuw de bundels om het probleem op te lossen.

* Wanneer een gebruiker een veld voor het eerst in een adaptief formulier configureert, wordt de optie voor het opslaan van een configuratie niet weergegeven in de eigenschappenbrowser. Als u een ander veld van het adaptieve formulier in dezelfde editor selecteert, wordt het probleem opgelost.

* Als de [!UICONTROL Connected assets configuration] tovenaar een 404 foutenmelding na installatie terugkeert, installeer manueel de `cq-remotedam-client-ui-content` en de `cq-remotedam-client-ui-components` pakketten opnieuw gebruikend de Manager van het Pakket.

* De volgende fouten en waarschuwingsberichten kunnen tijdens de installatie van AEM 6.5.x.x worden weergegeven:
   * &quot;Wanneer de integratie van het Doel in AEM gebruikend de StandaardAPI van het Doel (authentificatie IMS) wordt gevormd, dan leidt het uitvoeren van de Fragmenten van de Ervaring naar Doel in verkeerde aanbiedingstypes die worden gecreeerd. In plaats van het type &quot;Experience Fragment&quot;/bron &quot;Adobe Experience Manager&quot;, creëert Target verschillende aanbiedingen met het type &quot;HTML&quot;/source &quot;Adobe Target Classic&quot;.
   * `com.adobe.granite.maintenance.impl.TaskScheduler`: Geen onderhoudsvensters gevonden bij graniet/bediening/onderhoud.
   * De adaptieve servervalidatie van het formulier mislukt wanneer statistische functies zoals SUM, MAX en MIN worden gebruikt. CQ-4274424
   * `com.adobe.granite.maintenance.impl.TaskScheduler` - Geen onderhoudsvensters gevonden bij graniet/bediening/onderhoud.
   * Hotspot in een interactieve afbeelding van dynamische media is niet zichtbaar tijdens een voorvertoning van het element via de Shopable Banner-viewer.

## OSGi-bundels en inhoudspakketten inbegrepen {#osgi-bundles-and-content-packages-included}

De volgende tekstdocumenten maken een lijst van de bundels OSGi en de Pakketten van de Inhoud inbegrepen in AEM 6.5.5.0:

* [Lijst van OSGi-bundels opgenomen in AEM 6.5.5.0](assets/6550_bundles.txt)

* [Lijst met inhoudspakketten die zijn opgenomen in AEM 6.5.5.0](assets/6550_packages.txt)

## Beperkte locaties {#restricted-sites}

Deze sites zijn alleen beschikbaar voor klanten. Neem contact op met uw accountmanager van Adobe als u een klant bent en toegang nodig hebt.

* [Productdownload op licensing.adobe.com](https://licensing.adobe.com/)
* [Neem contact op met de klantenondersteuning](https://docs.adobe.com/content/help/en/customer-one/using/home.html)Voor meer informatie over de toegang tot het ondersteuningsportaal raadpleegt u [Toegang tot het ondersteuningsportal](https://helpx.adobe.com/experience-manager/kb/accessing-aem-support-portal.html).

>[!MORELIKETHIS]
>
>* [Opmerkingen bij de release AEM 6.5](/help/release-notes/release-notes.md)
>* [AEM-productpagina](https://www.adobe.com/solutions/web-experience-management.html)
>* [AEM 6.5-documentatie](https://helpx.adobe.com/nl/support/experience-manager/6-5.html)
>* Abonneren op [Adobe-productupdates met prioriteit](https://www.adobe.com/subscription/priority-product-update.html)

