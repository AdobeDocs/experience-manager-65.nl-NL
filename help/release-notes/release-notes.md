---
title: Opmerkingen bij de release [!DNL Adobe Experience Manager] 6,5
description: Zoek naar releasegegevens, wat is nieuw, installeer hoe kan worden gewijzigd en een gedetailleerde wijzigingslijst voor [!DNL Adobe Experience Manager] 6.5
mini-toc-levels: 4
exl-id: cac14ac1-9cda-46ae-8aa3-94674bb79157
source-git-commit: 6b24067c1808475044a612f21d5d4d2793c13e17
workflow-type: tm+mt
source-wordcount: '4205'
ht-degree: 0%

---

# [!DNL Adobe Experience Manager] 6.5 Laatste Opmerkingen bij de release Service Pack {#aem-service-pack-release-notes}

<!-- For an itemized list of all issues found in these release notes, see the following spreadsheet: https://adobe-my.sharepoint.com/:x:/r/personal/anujkapo_adobe_com/_layouts/15/Doc.aspx?sourcedoc=%7B3ea81ae4-e605-4153-b132-f2698c86f84e%7D&action=edit&wdinitialsession=d8c7b903-87fc-4f2d-9ef2-542a82169570&wdrldsc=3&wdrldc=1&wdrldr=SessionMemoryQuotaExceededDuringSession -->

<!-- DO NOT DELETE THIS HIDDEN NOTE      DO NOT DELETE THIS HIDDEN NOTE
>[!NOTE]
>
>Fixes in [!DNL Experience Manager] Forms are delivered through a separate add-on package one week after the scheduled [!DNL Experience Manager] Service Pack release date. In this case, the add-on packages release Thursday, November 30, 2023. In addition, a list of Forms fixes and enhancements is added to this section. -->

## Gegevens vrijgeven {#release-information}

| Product | [!DNL Adobe Experience Manager] 6,5 |
| -------- | ---------------------------- |
| Versie | 6.5.19,0 <!-- UPDATE FOR EACH NEW RELEASE --> |
| Type | Service Pack-release |
| Datum | Donderdag 7 december 2023 <!-- UPDATE FOR EACH NEW RELEASE --> |
| URL downloaden | [Softwaredistributie](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/servicepack/aem-service-pkg-6.5.19.0.zip) <!-- UPDATE FOR EACH NEW RELEASE --> |

## Wat is inbegrepen in [!DNL Experience Manager] 6.5.19,0 {#what-is-included-in-aem-6519}

[!DNL Experience Manager] 6.5.19.0 omvat nieuwe eigenschappen, zeer belangrijke klant-gevraagde verhogingen, insectenmoeilijke situaties, en prestaties, stabiliteit, en veiligheidsverbeteringen die sinds de aanvankelijke beschikbaarheid van 6.5 in April 2019 zijn vrijgegeven. [Dit servicepack installeren](#install) op [!DNL Experience Manager] 6.5

<!-- UPDATE FOR EACH NEW RELEASE -->

<!-- Some of the key features and improvements are the following:

* _REVIEWERS: WHAT ARE THE KEY FEATURES AND ENHANCEMENTS YOU WANT TO HIGHLIGHT IN THIS RELEASE?_ -->

## Belangrijke functies en verbeteringen

Enkele belangrijke functies en verbeteringen in deze release zijn onder andere:

* Gebruikers van de Pagina-editor/afbeeldingscomponent van Sites konden naar elementen van de Cloud Service voor externe middelen verwijzen. (SITES-13448, SITES-13433)
* AEM ondersteunt nu sorteren op de server voor snellere projectnavigatie in de lijstweergave. Projectknooppunten worden gesorteerd op basis van de door de gebruiker geselecteerde kolom voordat ze in de interface worden weergegeven.

### [!DNL Forms]

* **Nieuwe adaptieve Core-componenten van het formulier**: De verticale tabbladen, Algemene voorwaarden en Selectievakje worden toegevoegd om de schaalbaarheid van formulieren te verbeteren.
   * **[Component CheckBox](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/checkbox.html)**: Adaptieve Forms op basis van Core Components kan nu een component checkbox bevatten. Hiermee kunnen gebruikers binaire keuzes maken door een bepaalde optie te selecteren of te deselecteren. De optie wordt meestal weergegeven als een klein vak waarop u kunt klikken of tikken om te schakelen tussen twee statussen: ingeschakeld en uitgeschakeld. Het selectievakje is een veelgebruikt formulierelement voor een ja/nee- of waar/onwaar-keuze.

   * **[Component Voorwaarden en bepalingen](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/terms-and-conditions.html)**: Adaptieve Forms op basis van kerncomponenten kan nu een component Voorwaarden en Voorwaarden bevatten. Hiermee kunnen auteurs van formulieren een specifieke sectie in het formulier invoeren waarin gebruikers de voorwaarden, juridische overeenkomsten of het gebruik van een service, product of platform krijgen aangeboden. Deze component is bedoeld om gebruikers te informeren over de regels, regels en verplichtingen waarmee zij instemmen door het formulier in te dienen.

     ![Verticale tabbladen, Algemene voorwaarden en componenten Selectievakje](/help/forms/using/assets/forms-components.png)

   * **[De component Verticale tabbladen](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/vertical-tabs.html)**: Adaptieve Forms op basis van Core Components kan nu formulierinhoud ordenen in een verticale lijst met tabbladen, zodat u over een gestructureerde en navigeerbare indeling beschikt. Het gebruik van verticale tabbladen in een formulier kan de algehele gebruikerservaring verbeteren door de navigatie te vereenvoudigen en de organisatie van formulierinhoud te verbeteren, met name in situaties waarin een formulier meerdere secties of complexe informatie bevat.

* **[64-bits versie van AEM Forms Designer](/help/forms/using/installing-configuring-designer.md)**: De 64-bits versie van AEM Forms Designer biedt verbeterde prestaties, schaalbaarheid en geheugenbeheer, zodat u meer mogelijkheden hebt om formulieren te maken. Met de 64-bits architectuur kunt u nog grotere en complexere projecten eenvoudig aanpakken, zodat u kunt zorgen voor naadloze ontwerpworkflows en geoptimaliseerde efficiëntie. Verhoog uw mogelijkheden voor formulierontwerp en omarm de toekomst van AEM Forms Designer met deze geavanceerde release.

* **[Een adaptieve Forms verbinden met de Microsoft® SharePoint List](/help/forms/using/configuring-submit-actions.md#submit-to-microsoft&reg;-sharepoint-list)**: AEM Forms biedt een OOTB-integratie voor het rechtstreeks verzenden van formuliergegevens naar de SharePoint List, zodat u de mogelijkheden van SharePoint List kunt gebruiken. U kunt de Microsoft SharePoint-lijst configureren als gegevensbron voor een formuliergegevensmodel en de verzendactie Verzenden met het formuliergegevensmodel gebruiken om een adaptief formulier te verbinden met de SharePoint-lijst.

* **[Ondersteuning voor het configureren van Document of Record-eigenschappen voor adaptieve formulierfragmenten](/help/forms/using/generate-document-of-record-for-non-xfa-based-adaptive-forms.md)**: U kunt de fragmenten van het adaptieve formulier en de bijbehorende velden nu gemakkelijk aanpassen in de Adaptieve formuliereditor.


**Verouderde functie**

* ActiveMQ in AEM is vervangen. ActiveMQ is gebruikt voor communicatie tussen twee AEM Publish-instanties. Adobe raadt klanten aan een taakverdelingsmechanisme te gebruiken.

<!-- UPDATE BELOW FOR EACH NEW RELEASE -->

## Opgeloste problemen in Service Pack 19 {#fixed-issues}

### [!DNL Sites]{#sites-6519}

#### Toegankelijkheid{#sites-accessibility-6519}

* Als u op een AEM Sites-pagina 200% inzoomt op de pagina, worden de koppelingen **[!UICONTROL Language Copy]** en **[!UICONTROL CSV Report]** in de References verdwijnen. (SITES-11011)

#### Gebruikersinterface Admin{#sites-adminui-6519}

* AEM Screens Channel **[!UICONTROL Preview]** werkt niet en wordt niet weergegeven op het dashboard. (SITES-15730)
* Tijdens het verplaatsen van een pagina worden de verwijzingen, als de gebruikersinterface de verwijzingen niet kan tonen maar verklaart dat deze automatisch opnieuw worden gepubliceerd, zij *niet* opnieuw gepubliceerd. (SITES-16435)
* In AEM 6.5 met Service Pack 16 of 17, wanneer in de mening van de Lijst van plaatsen met de toegelaten kolom van het &quot;Werkschema&quot;, kunt u niet de lijst sorteren die op de punten in die kolom wordt gebaseerd. Er vindt geen sortering plaats. (SITES-15385)
* Voor een paginasjabloon voor omleiding is het veld voor omleiding verplicht gesteld. De validatie voor het vereiste veld wordt echter niet toegepast en werkt niet in deze twee scenario&#39;s: wanneer een pagina wordt gemaakt zonder verplichte omleidingswaarde; u kunt geen omleidingspagina maken. De validatie werkt niet wanneer u met sneltoetsen navigeert en wanneer het veld is gemarkeerd als ongeldig, wordt niet verder gegaan. (SITES-15903)
* Sommige **Binnenkomende koppelingen** werden niet opgenomen in het weergegeven aantal in het dialoogvenster **Verwijzingen** deelvenster. Het deelvenster werd bijvoorbeeld weergegeven **Binnenkomende koppelingen (6)** maar er waren eigenlijk negen binnenkomende links . (SITES-14816)

#### Klassieke interface{#sites-classicui-6519}

* Nadat u hotfix hebt geïnstalleerd in SITES-15827, werden dialoogvenstertitels met witruimte tussen woorden vervangen door `" "`. Er werden ook regeleinden verwijderd. (SITES-16089)
* Titels van gecodeerde dialoogvensters resulteren nu in een dubbele codering van de titel. (SITES-15841)
* De update van AEM servers van de dienstpak 6.5.16 tot 6.5.17 resulteerde in een dubbele codering van Klassieke de dialoogvaktitels van de UI. (SITES-15634)

#### [!DNL Content Fragments]{#sites-contentfragments-6519}

* Er verschijnt een bericht Interne serverfout in de Inhoudsfragmenteditor. (SITES-13550)
* De bijwerking van de `org.json` bibliotheek door middel van NPR-41291 heeft geleid tot conversies van gegevensfouten in de `DefaultDataTypeConverter` van de `cfm-impl` bundel. Conversie van gegevenstypen moet flexibeler zijn. (SITES-16473)
* Het pop-upbericht &#39;Deze versie van het inhoudsfragment kan vanwege incompatibele inhoud niet worden vergeleken met de huidige versie.&#39; Inhoudsfragmenten moeten vergelijkbaar zijn, maar niet. (SITES-16317)
* De JS-URL van de elementkiezer is gewijzigd van
  `https://experience.adobe.com/solutions/CQ-assets-selectors/assets/resources/assets-selectors.js`
tot
  `https://experience.adobe.com/solutions/CQ-assets-selectors/static-assets/resources/assets-selectors.js` (SITES-16068)
* Pas het nieuwe API-responsschema voor metagegevens van Polaris aan voor CFM-Polaris-integratie. (SITES-15166)
* Alle inhoudsfragmenten moeten worden vermeld op de plaats waar naar het geselecteerde inhoudsfragment wordt verwezen. In plaats daarvan bevatten elementverwijzingen in het referentievenster voor inhoudsfragmenten 0 (nul) verwijzingen. (SITES-15036)

#### Core Backend{#sites-core-backend-6519}

* Verbeteren `StyleImpl`. (SITES-15164)
* Verbeter de versie/650 tak van de pijpleiding WCM om integratietests voor zijn modules in werking te kunnen stellen. (SITES-12938)

<!--#### Core Components{#sites-core-components-6519}

* A -->

#### Campagne-integratie{#sites-campaign-integration-6519}

* Op de component signature (`/apps/fpl/components/campaign/signature`) werkt de koppeling ExternalAlizer niet. Het domein wordt niet toegevoegd aan de afbeeldingsbron als de HTML-opmerking boven de afbeeldingstag is verwijderd. Dit probleem is alleen gevonden met de handtekeningcomponent in de productieomgeving, niet met de testomgeving. (SITES-16120)

<!--#### Experience Fragments{#sites-experiencefragments-6519}

* A -->

#### Elementaire componenten (verouderd){#sites-foundation-components-legacy-6519}

* Adobe Experience Manager (AEM) Sites Search component verbreekt de gebruikersinterface. (SITES-15087)

#### GraphQL Query Editor{#sites-graphql-query-editor-6519}

* In de gebruikersinterface van GraphQL Editor kunt u niet door alle voortgezette query&#39;s bladeren wanneer er een groot aantal query&#39;s is (bijvoorbeeld meer dan 25). (SITES-16008)
* De GraphQL Editor slaat de publicatiestatus van doorlopende query&#39;s niet op. De knop Publiceren ongedaan maken wordt weergegeven in de GraphQL Editor, maar het pictogram dat aangeeft dat de voortgezette query is gepubliceerd, wordt niet weergegeven. Als u de pagina vernieuwt, ziet u dat de voortgezette query niet eens wordt gepubliceerd. (SITES-15858)

#### Lanceringen{#sites-launches-6519}

* Wijzigingen in de opslagplaats worden niet opgeslagen vanwege `Oak0001` veroorzaakt een conflict wanneer meerdere pagina&#39;s worden bewerkt of de inhoud wordt geschreven. Het is normaal dat u in een dergelijke gebeurtenis opnieuw probeert, maar dit gebeurt niet. (SITES-14840)

#### MSM - Actieve kopieën{#sites-msm-live-copies-6519}

* MSM-uitrolknop werkt niet in de grafische gebruikersinterface met aanraakbediening. (SITES-16991)
* De Verwijzing van de verbinding wordt niet bijgewerkt binnen het Fragment van de Ervaring wanneer het creëren van een levende exemplaar of het opstellen van een Fragment van de Ervaring. (SITES-15460)

#### Pagina-editor{#sites-pageeditor-6519}

* Als u in Forms > Thema&#39;s een thema hebt geopend in de themaeditor en enkele wijzigingen hebt aangebracht en vervolgens op Voorvertoning hebt geklikt, wordt een pictogram voor het laden weergegeven, maar wordt de werkelijke voorvertoning niet geladen. (SITES-17164)
* De selectie van meerdere documentfiletypen op het filter voor elementtype werkt niet op de paginaconsole. Er worden geen resultaten gevonden, zelfs niet als de resultaten van een bepaald bestandstype beschikbaar zijn. Auteurs kunnen daarom niet meerdere documenten filteren. Zij moeten veelvoudige documenttypes gebruiken en zij moeten het tegelijkertijd filtreren. (SITES-14047)
* Nadat u een exemplaar van AEM 6.5.17 en AEM 6.5.18 hebt bijgewerkt, vanuit de Pagina-editor, indien u deze optie hebt geselecteerd **[!UICONTROL Publish Page]**, wordt u omgeleid naar een URL die niet bestaat. De gebruiker moet worden omgeleid naar de wizard Publiceren. (SITES-15856)
* Overbodige kopie van AEM klembord tijdens plakken vanaf het klembord van het besturingssysteem. (SITES-15704)
* In elementen selecteren **[!UICONTROL Documents]** vervolgens onder **[!UICONTROL Filtertype]**, selecteren **[!UICONTROL Microsoft® Word]** of **[!UICONTROL Microsoft® Excel]** geeft geen resultaten weer, ook al bestaan er bestanden van beide typen. (SITES-14837)

### [!DNL Assets]{#assets-6519}

* Wanneer u een openbare map maakt of opslaat, worden drie groepen gemaakt in een beheerdashboard. (ACTIVA-26700)
* Kan geen onderscheid maken tussen publicatiemiddelen en Experience Manager of Brand Portal. (NPR-41320)
* Wanneer u in het zoekvenster selectievakjes selecteert en een van deze selectievakjes uitschakelt, zijn alle selectievakjes uitgeschakeld. (ACTIVA-26377)

#### [!DNL Dynamic Media]{#assets-dm-6519}

* Nadat een element naar AEM is geüpload, `update_asset` de workflow wordt geactiveerd. De workflow wordt nooit voltooid. Wanneer u de workflowinstanties bekijkt, wordt de workflow voltooid tot de uploadstap voor het product. De volgende stap is het uploaden van Scene7-batches. De gebruiker kan zien dat het middel zich in Scene7 bevindt vanuit de Dynamic Media Classic-app. (ACTIVA-30443)
* Een aangepast servereindpunt (API-eindpunt) retourneert een onjuiste Dynamic Media-bestandsnaam (Scene7). Dit gebeurt wanneer een element wordt verwijderd en vervangen door een element met dezelfde naam. De aangepaste servlet retourneert de oude Dynamic Media-bestandsnaam (Scene7), terwijl een JCr-API-aanroep de juiste bestandsnaam retourneert. (ACTIVA-29476)
* Zelfs nadat Sync is uitgeschakeld op mapniveau, wordt in het logbestand de trigger &quot;Scene7 ReplicateOnModifyListener&quot; weergegeven. De `ReplicateOnModifyListener/Worker` moet verwerking op niet-Dynamic Media-mapelementen en inhoudsfragmenten overslaan. (ACTIVA-26705)
* Mensen met een laag gezichtsvermogen worden beïnvloed als de focus niet zichtbaar is in vervolgkeuzemenu&#39;s (Alleen inhoud, Weergave, Meer opties) in zwart-witmodi met hoog contrast. (ACTIVA-25759)
* Mensen met een laag gezichtsvermogen worden beïnvloed als de lichtsterktecontrastverhouding voor tekst op een pagina minder dan 4,5:1 is. (ACTIVA-25756)
* Schermlezers vertellen het weergegeven pop-upbericht niet nadat ze de gegevens hebben verzonden. (ACTIVA-25755)
* Schermlezers herkennen geen markeringen op de pagina (Dynamic Media; maken van een videocoderingsprofiel) wanneer ze navigeren met een vaste-kommasleutel/regiosneltoets `D/R`. (ACTIVA-25752)
* Schermlezers herkennen niet meerdere markeringen op de pagina (Dynamic Media; interactieve video maken) wanneer ze navigeren met behulp van een sneltoets voor liggend/regionaal `D/R`. (ACTIVA-25750)
* Schermlezers (NVDA/JAWS/Narrator) herkennen de Landmarkeringen niet in **Element bewerken** pagina tijdens navigeren met de sneltoetsen `D/R`. (ACTIVA-25744)
* De gebruiker krijgt een leeg/vals asynchroon baanbericht maar het aangesloten middel wordt met succes gepubliceerd. (ACTIVA-29342)

### [!DNL Forms]{#forms-6519}

#### [!DNL Adaptive Forms]

<!-- Fixes in [!DNL Experience Manager] Forms are delivered through a separate add-on package one week after the scheduled [!DNL Experience Manager] Service Pack release date. In this case, the AEM 6.5.19.0 Forms add-on package release is scheduled for Thursday, November 30, 2023. A list of Forms fixes and enhancements would be added to this section post the release.-->

<!--* Adding Access Control List for `fd-cloudservice` user to be able to read or update the Microsoft&reg; configurations under `cloudconfigs/microsoftoffice`. (FORMS-11142) -->

<!--LEFT BULLET LIST HERE IN CASE OF REUSE BY FORMS IN THE FUTURE 
* **Document Services**
  * text
* **Adaptive Forms** 
  * text
* **Accessibility**
  * text
* **Interactive Communications**
  * text -->

<!--### Commerce{#commerce-6519}

* A -->

* Wanneer een gebruiker een werkbalk toevoegt aan Adaptief formulier, vertoont het Label van de formuliercontainer een onjuist gedrag omdat dit niet verandert in de voorkeurstaal die de auteur voor Forms heeft geselecteerd. (FORMS-11371)
* In AEM Forms Workspace selecteert het vervolgkeuzeveld standaard de eerste optie in de gebruikersinterface. (FORMS-11346)
* De taalconfiguratie in AEM lijkt geen effect te hebben als u landinstellingen met vijf tekens gebruikt en het decimale scheidingsteken niet correct in de letter wordt weergegeven. (FORMS-11344)
* Wanneer een gebruiker de XML-uitvoer genereert met behulp van het workbench-proces, mislukt dit voor een aantal bestanden. (FORMS-11314)
* Wanneer een gebruiker voorvertoning voor Document of Record (DOR) genereert in andere talen dan Engels, werkt dit niet. (FORMS-11106)
* Wanneer een gebruiker sommige afbeeldingsbestanden met PDFG omzet in een OSGI-instantie op basis van Linux met JDK11, wordt deze niet omgezet. (FORMS-11105)
* Wanneer de gebruiker de invoegtoepassing AEM Forms installeert, wordt het deelvenster voor de inhoudsstructuur in AEM Sites verbroken. (FORMS-10912)
* Wanneer een gebruiker datums kopieert met gebruik van de NVDA-schermlezer van de Date Picker-component, wordt deze niet correct gelezen. (FORMS-10805) 
* In de Forms-regeleditor kan de gebruiker de waarde van het keuzerondje/selectievakje niet instellen wanneer het gegevenstype Boolean is. (FORMS-10713)
* Wanneer een gebruiker items toevoegt aan een adaptief formulier, wordt deze in omgekeerde volgorde toegevoegd aan een vervolgkeuzelijst. (FORMS-10456)
* Wanneer een dropdown gebruikend de regelredacteur wordt ontruimd, verschijnt de eerste verstrekte waarde nog alhoewel de waarde is ontruimd. (FORMS-9963) 
* Gebruikers hebben geen toegang tot de functie Formulier Titel met behulp van schermlezers, zoals NVDA. (FORMS-8815) 
* Gebruikers hebben met schermlezers, zoals NVDA, geen toegang tot de subtitel in een formulier. (FORMS-8814) 
* In de paginabron van het HTML-formulier is het kenmerk access key leeg en werkt het niet. (FORMS-5753) 
* In het dialoogvenster Info over werkruimte wordt de tekst &quot;Adobe Experience Manager - Forms&quot; weergegeven als tekst. (FORMS-5748)

#### [!DNL Forms Designer]{#forms-designer-6519}

* Wanneer een gebruiker niet-interactieve PDF forms probeert te lezen via schermlezers, worden sommige lijstitems niet gelezen of overgeslagen. (LC-3921645) 
* Wanneer een gebruiker met de Tab-toets door de bewerkbare velden gaat, worden niet alle PDF-formuliervelden consistent doorlopen. (LC-3921631) 
* De volgorde van de labels wordt willekeurig gewijzigd in PDF, zelfs als de labels in Forms Designer zijn ingesteld, is juist. (LC-3921313) 
* Een lijst wordt niet correct weergegeven in de tags in Adobe Acrobat Reader of Adobe Acrobat DC. (LC-3921306)
* Kop-niveaus die correct zijn toegewezen in Forms Designer, worden willekeurig gewijzigd in een `<P>` -tag in Adobe Acrobat. (LC-3921305) 
* In een tabel kan de id van een object niet worden gewijzigd nadat deze is toegewezen. (LC-3921134) 
* Als samengevoegde cellen in de tabel staan, is er geen GUI beschikbaar voor het instellen van het bereik (rij en kolom) en het bereik in een complexe tabel in AEM Forms Designer. (LC-3919532) 

### Stichting{#foundation-6519}

* Als u een taalkopie maakt op het hoofdniveau van de taal, worden de paden op de pagina niet aangepast. In het geval waarin de taalkopie is gemaakt, is het pad niet correct gewijzigd voor de hoofdtaal, maar voor de pagina&#39;s eronder. (NPR-41364)
* De knopinfo &#39;Relatieve datumpresentatie&#39; kan alleen worden gesloten door op het toetsenbord op Escape (ESC) te drukken. De knopinfo moet worden gesloten wanneer de gebruiker een gedeelte van de gebruikersinterface selecteert. (NPR-41394)
* Niet-gelokaliseerde tekenreeks `Something went wrong while adding the private key.` wanneer u het onjuiste bestand met de persoonlijke sleutel toevoegt in **Gebruiker bewerken** > **Keystore**. (NPR-41366)
* Er zijn pictogrammen nodig voor Microsoft® SharePoint en Microsoft® One Drive in de AEM 6.5-omgeving. (NPR-41354)
* Niet-gelokaliseerde fout in gebruikersnaam/wachtwoord. tekenreeks in **Beveiliging** > **Gebruiker** > **Maken** in. (NPR-41245)
* Popover code en de managers van de Gebeurtenis worden tweemaal geladen, die user-created Koral3-Gebaseerde gebruikersinterfaces breken. (NPR-41171)
* Het uitschakelen werkt niet correct nadat u Alles selecteren hebt gebruikt in de AEM Sites-console. (NPR-41304)

<!--#### Content distribution{#foundation-content-distribution-6519}

* T -->

#### Integrations{#integrations-6519}

* De verbindingen van SMS in een AEM e-mailcampagne worden niet correct geschreven; zij bevatten een HTML ankerelement. (NPR-41211)
* Woorden die op het scherm van de rekeningsconfiguratie worden gebruikt zouden geen nieuw credentieel type moeten gebruiken. (NPR-41210)
* De het rapportinvoerplanner van de Analyse van de beweging van `ManagedPollConfig` op banen te verliezen. Wanneer twee verschillende analytische kaders met verschillende rapportagesets aan twee verschillende plaatsen werden vastgemaakt, `ManagedPollConfig` maar één van hen is opiniepeild . (NPR-41209)
* Wanneer de standaardwaarde wordt hersteld, blijft de eerder geselecteerde tijdframeknop ingeschakeld. In het inzichtelijke dashboard van de inhoud van AEM, door gebrek wordt het tijdkader geplaatst bij de week en toont inzichten van de inhoud als wekelijkse gegevens. Als de gebruiker nu andere tijdframeopties selecteert, zoals uur, dag, maand en jaar, veranderen de gegevens volgens de geselecteerde waarde. Als de waarden echter standaard opnieuw worden ingesteld, is het zichtbare tijdframe week, maar is de eerder geselecteerde tijdframeoptie nog steeds geselecteerd. (NPR-41246)

#### Eik{#oak-6519}

* Het nut van de steun aan tariefgrens schrijft aan AEM in het geval dat de async indexering wordt vertraagd. (NPR-40985)

#### Platform{#foundation-platform-6519}

* QueryBuilder-query&#39;s met vierkante haakjes worden onjuist vertaald naar xpath. (NPR-41298)

<!--#### Replication{#foundation-replication-6519}

* R -->

<!--#### Sling{#foundation-sling-6519}

* W -->

#### Vertaalprojecten{#foundation-translation-6519}

* Tijdens het maken van de taalkopie van pagina &quot;A&quot;, moet deze automatisch de taalkopieën maken van de pagina&#39;s waarnaar wordt verwezen, fragmenten, fragmenten voor inhoud en elementen. Bovendien moet de nieuwe taalkopie van pagina &quot;A&quot; op het nieuwe pad de referenties hebben die zijn ingesteld voor de zojuist gemaakte taalkopieën van de pagina&#39;s, ervaringsfragmenten, inhoudsfragmenten en elementen. (NPR-41076)

<!--#### User interface{#foundation-ui-6519}

* A -->

<!--#### WCM{#wcm-6519}

* A -->

#### Workflow{#foundation-workflow-6519}

* Kan een taak in het Postvak IN niet voltooien. Er wordt alleen een &quot;ongedefinieerde&quot; waarde waargenomen in het keuzemenu wanneer wordt geprobeerd de taak te voltooien en een actie te selecteren. Dit betekent dat de gebruikers niet het AEM 6.5.18 de dienstpak kunnen toepassen. (NPR-41402 en NPR-41473)
* Kan de taken in Postvak IN niet voltooien. De vervolgkeuzelijst bevat geen waarde (alleen &quot;ongedefinieerd&quot;) wanneer wordt geprobeerd de taak te voltooien voor ZIP-bestanden, Asset-rapporten, verplaatsen (geslaagd of mislukt) of het vervallen van middelen. (NPR-41305)
* Wanneer een gebruiker **[!UICONTROL Tools]** > **[!UICONTROL Workflow]** > instanties, selecteert u vervolgens de actieve workflow en selecteert u **[!UICONTROL View Payload]** resulteert dit in een pagina met 500 fouten. (NPR-41325)

## Installeren [!DNL Experience Manager] 6.5.19,0{#install}

<!-- Remaining content from here to bottom stays the same except for version updating as needed as per update team feedback. -->

* [!DNL Experience Manager] 6.5.19.0 vereist [!DNL Experience Manager] 6.5. Zie [upgradedocumentatie](/help/sites-deploying/upgrade.md) voor gedetailleerde instructies. <!-- UPDATE FOR EACH NEW RELEASE -->
* De download van het de dienstpak is beschikbaar op Adobe [Softwaredistributie](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/servicepack/aem-service-pkg-6.5.19.0.zip).
* Bij een implementatie met MongoDB en meerdere exemplaren, installeert u [!DNL Experience Manager] 6.5.19.0 op één van de instanties van de Auteur die de Manager van het Pakket gebruiken.<!-- UPDATE FOR EACH NEW RELEASE -->

>[!IMPORTANT]
>
> Adobe raadt u niet aan de [!DNL Experience Manager] 6.5.19.0-pakket. Voordat u het pakket installeert, moet u daarom een back-up maken van het `crx-repository` voor het geval u het terug moet rollen. <!-- UPDATE FOR EACH NEW RELEASE -->
<!-- For instructions to install Service Pack for Experience Manager Forms, see [Experience Manager Forms Service Pack installation instructions](/help/release-notes/aem-forms-current-service-pack-installation-instructions.md). -->


### Installeer het de dienstpak op [!DNL Experience Manager] 6,5{#install-service-pack}

1. Start de instantie opnieuw vóór de installatie als de updatemodus voor de instantie is geactiveerd (wanneer de instantie is bijgewerkt vanaf een eerdere versie). Adobe raadt aan de toepassing opnieuw te starten als de huidige uptime voor een instantie hoog is.

1. Maak een momentopname of een nieuwe back-up van uw [!DNL Experience Manager] -instantie.

1. Download het servicepack van [Softwaredistributie](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/servicepack/aem-service-pkg-6.5.19.0.zip). <!-- UPDATE FOR EACH NEW RELEASE -->

1. Pakketbeheer openen en vervolgens selecteren **[!UICONTROL Upload Package]** om het pakket te uploaden. Zie voor meer informatie [Pakketbeheer](/help/sites-administering/package-manager.md).

1. Selecteer het pakket en selecteer **[!UICONTROL Install]**.

1. Om de S3 schakelaar bij te werken, stop de instantie na installatie van het Service Pack, vervang de bestaande schakelaar met een nieuw binair dossier dat in de installatiemap wordt verstrekt, en begin de instantie opnieuw. Zie [Amazon S3 Data Store](/help/sites-deploying/data-store-config.md#upgrading-to-a-new-version-of-the-s-connector).

>[!NOTE]
>
>De dialoog over de Manager UI van het Pakket bestaat soms tijdens de installatie van het de dienstpak. De Adobe adviseert dat u op foutenlogboeken wacht om zich te stabiliseren alvorens tot de plaatsing toegang te hebben. Wacht op de specifieke logboeken met betrekking tot het verwijderen van de updaterbundel alvorens wordt verzekerd dat de installatie succesvol is. Dit probleem treedt meestal op in het dialoogvenster [!DNL Safari] browser, maar kan soms voorkomen op om het even welke browser.

**Automatische installatie**

Er zijn twee verschillende methoden die u automatisch kunt installeren [!DNL Experience Manager] 6.5.19.0.<!-- UPDATE FOR EACH NEW RELEASE -->

* Plaats het pakket in `../crx-quickstart/install` als de server online beschikbaar is. Het pakket wordt automatisch geïnstalleerd.
* Gebruik de [HTTP-API van Package Manager](/help/sites-administering/package-manager.md#package-share). Gebruiken `cmd=install&recursive=true` zodat de geneste pakketten worden geïnstalleerd.

>[!NOTE]
>
>Experience Manager 6.5.19.0 ondersteunt geen installatie van Bootstrappen. <!-- UPDATE FOR EACH NEW RELEASE -->

**De installatie valideren**

Als u wilt weten welke platformen gecertificeerd zijn voor deze release, raadpleegt u de [technische voorschriften](/help/sites-deploying/technical-requirements.md).

1. De pagina met productinformatie (`/system/console/productinfo`) geeft de bijgewerkte versietekenreeks weer `Adobe Experience Manager (6.5.19.0)` krachtens [!UICONTROL Installed Products]. <!-- UPDATE FOR EACH NEW RELEASE -->

1. Alle OSGi-pakketten zijn **[!UICONTROL ACTIVE]** of **[!UICONTROL FRAGMENT]** in de Console OSGi (de Console van het Gebruik: `/system/console/bundles`).

1. De OSGi-bundel `org.apache.jackrabbit.oak-core` is versie 1.22.17 of hoger (webconsole gebruiken: `/system/console/bundles`). <!-- NPR-41292 for 6.5.19.0 --> <!-- OAK Oak oak VERSION -MAY- NEED TO BE UPDATED FOR EACH NEW RELEASE -->

### Service Pack installeren voor [!DNL Experience Manager] Forms{#install-aem-forms-add-on-package}

Voor instructies voor het installeren van het servicepakket op Experience Manager Forms raadpleegt u [Installatie-instructies voor Experience Manager Forms Service Pack](/help/release-notes/aem-forms-current-service-pack-installation-instructions.md).

>[!NOTE]
>
>De functie Adaptive Forms is beschikbaar in [AEM 6.5 QuickStart](https://experienceleague.adobe.com/docs/experience-manager-65/deploying/deploying/deploy.html), is uitsluitend ontworpen voor exploratie en evaluatie. Voor productiegebruik is het van essentieel belang een geldige licentie voor AEM Forms te verkrijgen, aangezien voor de adaptieve Forms-functionaliteit een correcte licentie vereist is.

### GraphQL-indexpakket voor Experience Manager-inhoudsfragmenten installeren{#install-aem-graphql-index-add-on-package}

Klanten die GraphQL gebruiken, moeten de [Experience Manager-inhoudsfragment met GraphQL Index-pakket 1.1.1](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/featurepack/cfm-graphql-index-def-1.1.1.zip).

Zo kunt u de vereiste indexdefinitie toevoegen op basis van de functies die ze daadwerkelijk gebruiken.

Als u dit pakket niet installeert, kan dit leiden tot trage of mislukte GraphQL-query&#39;s.

>[!NOTE]
>
>Installeer dit pakket slechts eenmaal per instantie; het hoeft niet opnieuw te worden geïnstalleerd met elk Service Pack.

### UberJar{#uber-jar}

The UberJar for [!DNL Experience Manager] 6.5.19.0 is beschikbaar in [Maven Central-opslagplaats](https://repo.maven.apache.org/maven2/com/adobe/aem/uber-jar/6.5.19/). <!-- CHECK FOR UPDATE EACH NEW RELEASE -->

Om UberJar in een Geweven project te gebruiken, zie [gebruiken van UberJar](/help/sites-developing/ht-projects-maven.md) en neem het volgende gebiedsdeel in uw project POM op: <!-- CHECK FOR UPDATE EACH NEW RELEASE -->

```shell
<dependency>
     <groupId>com.adobe.aem</groupId>
     <artifactId>uber-jar</artifactId>
     <version>6.5.19</version>
     <scope>provided</scope>
</dependency>
```

>[!NOTE]
>
>UberJar en de andere verwante artefacten zijn beschikbaar op Maven Central Repository in plaats van Adobe Public Maven repository (`repo.adobe.com`). De naam van het hoofdbestand van UberJar wordt gewijzigd in `uber-jar-<version>.jar`. Er is dus geen `classifier`, met `apis` als de waarde voor de `dependency` -tag.

## Verouderde en verwijderde functies{#removed-deprecated-features}

Zie [Verouderde en verwijderde functies](/help/release-notes/deprecated-removed-features.md/).

## Bekende problemen{#known-issues}

<!-- THESE KNOWN ISSUES CARRY OVER EACH RELEASE. THE "PRODUCT UPDATES TEAM" IS SUPPOSED TO VERIFY EACH ISSUE AND LET YOU KNOW IF ANYTHING NEEDS TO BE ADDED, DELETED, OR CHANGED IN THIS LIST.-->

<!-- * **Page publishing not working in Page Editor after upgrading to Service Pack 18 (6.5.18.0)** -->

<!-- https://jira.corp.adobe.com/browse/SITES-15856 REMOVE FOR 6.5.19.0 -->
<!-- After you upgrade an instance of AEM 6.5.0.0&mdash;6.5.17.0 to AEM 6.5.19.0, when you click **Publish Page** inside the Page Editor, you are redirected to a URL that does not exist.

  To work around this issue, do one of the following:

  * Remove the following "path" property.

       `/libs/wcm/core/content/editor/jcr:content/content/items/content/header/items/headerbar/items/pageinfopopover/items/list/items/publish/granite:data`

  * Paste the correct URL directly into the browser.

       `http://localhost:4504/editor.html/libs/wcm/core/content/sites/publishpagewizard.html?item=/content/we-retail/language-masters/en/about-us.html` -->



* **Verwant aan eikenhout**
Van Service Pack 13 en hierboven, is het volgende foutenlogboek begonnen te verschijnen dat het persistentiegeheime voorgeheugen beïnvloedt:

  ```shell
  org.h2.mvstore.MVStoreException: The write format 1 is smaller than the supported format 2 [2.0.202/5]
  at org.h2.mvstore.DataUtils.newMVStoreException(DataUtils.java:1004)
      at org.h2.mvstore.MVStore.getUnsupportedWriteFormatException(MVStore.java:1059)
      at org.h2.mvstore.MVStore.readStoreHeader(MVStore.java:878)
      at org.h2.mvstore.MVStore.<init>(MVStore.java:455)
      at org.h2.mvstore.MVStore$Builder.open(MVStore.java:4052)
      at org.h2.mvstore.db.Store.<init>(Store.java:129)
  ```

  of

  ```shell
  org.h2.mvstore.MVStoreException: The write format 1 is smaller than the supported format 2 [2.1.214/5].
  ```

  U kunt deze uitzondering als volgt oplossen:

   1. De volgende twee mappen verwijderen uit `crx-quickstart/repository/`

      * `cache`
      * `diff-cache`

   1. Installeer het Service Pack of start de Experience Manager as a Cloud Service opnieuw.
Nieuwe mappen van `cache` en `diff-cache` automatisch worden gemaakt en er is geen uitzondering meer die betrekking heeft op `mvstore` in de `error.log`.

* Werk uw GraphQL-query&#39;s bij die mogelijk een aangepaste API-naam voor uw inhoudsmodel hebben gebruikt om in plaats daarvan de standaardnaam van het inhoudsmodel te gebruiken.

* Een GraphQL-query kan de opdracht `damAssetLucene` index in plaats van de `fragments` index. Deze handeling kan resulteren in GraphQL-query&#39;s die mislukken of die lang duren.

  Om het probleem te verhelpen, `damAssetLucene` moet worden geconfigureerd om de volgende twee eigenschappen op te nemen onder `/indexRules/dam:Asset/properties`:

   * `contentFragment`
      * `jcr:primaryType="nt:unstructured"`
      * `name="jcr:content/contentFragment"`
      * `propertyIndex="{Boolean}true"`
      * `type="Boolean"`
   * `model`
      * `jcr:primaryType="nt:unstructured"`
      * `name="jcr:content/data/cq:model"`
      * `ordered="{Boolean}true"`
      * `propertyIndex="{Boolean}true"`
      * `type="String"`

  Nadat de indexdefinitie is gewijzigd, is opnieuw indexeren vereist (`reindex` = `true`).

  Na deze stappen zouden de vragen van GraphQL sneller moeten presteren.

* Wanneer u probeert inhoudsfragmenten, sites of pagina&#39;s te verplaatsen, te verwijderen of te publiceren, is er een probleem wanneer verwijzingen naar inhoudsfragmenten worden opgehaald, omdat de achtergrondquery mislukt. De functionaliteit werkt dus niet.
Om correcte verrichting te verzekeren, moet u de volgende eigenschappen aan de knoop van de indexdefinitie toevoegen `/oak:index/damAssetLucene` (opnieuw indexeren is niet vereist):

  ```xml
  "tags": [
      "visualSimilaritySearch"
    ]
  "refresh": true
  ```

* Als u uw [!DNL Experience Manager] -exemplaar van 6.5.0 - 6.5.4 naar het nieuwste servicepakket op Java™ 11, zie `RRD4JReporter` uitzonderingen in de `error.log` bestand. Als u de uitzonderingen wilt stoppen, start u de instantie van [!DNL Experience Manager]. <!-- THIS BULLET POINT WAS UPDATED AS PER CQDOC-20021, JANUARY 23, 2023 -->

* Gebruikers kunnen de naam wijzigen van een map in een hiërarchie in [!DNL Assets] en publiceer een geneste map naar [!DNL Brand Portal]. De maptitel wordt echter niet bijgewerkt in [!DNL Brand Portal] totdat de hoofdmap opnieuw wordt gepubliceerd.

* De volgende fouten en waarschuwingsberichten kunnen tijdens de installatie van [!DNL Experience Manager] 6.5.x.x:
   * &quot;Wanneer de Adobe Target-integratie is geconfigureerd in [!DNL Experience Manager] Als u de standaard-API (IMS-verificatie) van het doel gebruikt, leidt het exporteren van ervaringsfragmenten naar Doel tot onjuiste aanbiedingstypen die worden gemaakt. In plaats van het type &quot;Experience Fragment&quot;/bron &quot;Adobe Experience Manager&quot; maakt Target verschillende aanbiedingen met het type &quot;HTML&quot;/bron &quot;Adobe Target Classic&quot;.
   * `com.adobe.granite.maintenance.impl.TaskScheduler`: Geen onderhoudsvensters gevonden bij graniet/bediening/onderhoud.
   * De validatie aan de adaptieve formulierserver-side mislukt wanneer statistische functies zoals SUM, MAX en MIN worden gebruikt (CQ-4274424).
   * `com.adobe.granite.maintenance.impl.TaskScheduler` - Geen onderhoudsvensters gevonden bij graniet/bediening/onderhoud.
   * De hotspot in een interactieve Dynamic Media-afbeelding is niet zichtbaar wanneer u een voorvertoning van het element weergeeft via de Shopable Banner-viewer.
   * `com.adobe.cq.social.cq-social-jcr-provider bundle com.adobe.cq.social.cq-social-jcr-provider:1.3.5 (395)[com.adobe.cq.social.provider.jcr.impl.SpiSocialJcrResourceProviderImpl(2302)]` : Time-out bij wachten op wijziging register is niet-geregistreerd.

* Vanaf AEM 6.5.15 wordt de Rhino JavaScript Engine geleverd door de ```org.apache.servicemix.bundles.rhino``` bundle heeft een nieuw hoistinggedrag. Scripts die de strikte modus gebruiken (```use strict;```) moeten hun variabelen correct declareren, anders worden ze niet uitgevoerd, maar wordt er een runtimefout gegenereerd.

### Bekende problemen voor AEM Forms

#### Ondersteunde platforms

* JDK 11.0.20 wordt niet ondersteund voor de installatie van AEM Forms op JEE Installer. Alleen JDK 11.0.19 of eerdere versies worden ondersteund voor de installatie van AEM Forms op JEE Installer. (FORMS-10659)

#### Installatie

* Op het JBoss® 7.1.4-platform, wanneer de gebruiker Experience Manager 6.5.16.0 of hoger servicepack installeert, `adobe-livecycle-jboss.ear` implementatie mislukt. (CQ-4351522, CQDOC-20159)
* Na de upgrade naar de AEM Forms 6.5.18.0 JBoss® Turnkey-omgeving met volledig installatieprogramma op Windows Server 2022 kan bij het compileren van de code voor de Output client-toepassing met behulp van Java™ 11 de volgende compilatiefout optreden:

  ```
  error: error reading [AEM_Forms_Installation_dir]\sdk\client-libs\common\adobe-output-client.jar; java.net.URISyntaxException: 
  Illegal character in path at index 70: file:/[AEM_Forms_Installation_dir]/sdk/client-libs/common/${clover.jar.name} 1 error
  ```

  Voer de volgende stappen uit om het probleem op te lossen:
   1. Navigeren naar `[AEM_Forms_Installation_dir]\sdk\client-libs\common\` en unzip `adobe-output-client.jar` om de `Manifest.mf` bestand.
   1. Werk de `Manifest.mf` bestand verwijderen door het item te verwijderen `${clover.jar.name}` uit het kenmerk class-path.

      >[!NOTE]
      >
      > U kunt ook een programma voor het op locatie bewerken gebruiken, bijvoorbeeld 7-zip, om het dialoogvenster `Manifest.mf` bestand.

   1. Sla de bijgewerkte versie van de `Manifest.mf` in de `adobe-output-client.jar` archief.
   1. De gewijzigde versie opslaan `adobe-output-client.jar` en voer de installatie opnieuw uit. (CQDOC-20878)
* Nadat u AEM Service Pack 6.5.19.0 volledig installatieprogramma hebt geïnstalleerd, mislukt de EAR-implementatie op JEE met JBoss® Turnkey.
Als u het probleem wilt oplossen, zoekt u de `<AEM_Forms_Installation_dir>\jboss\bin\standalone.bat` bestand en update `Adobe_Adobe_JAVA_HOME` tot `Adobe_JAVA_HOME` voor alle instanties alvorens de configuratiemanager in werking te stellen. (CQDOC-20803)

#### Installeer het serverfragment (AEM Service Pack 6.5.14.0 of eerder)

* Als u een upgrade uitvoert naar AEM Service Pack 6.5.15.0 of hoger en uw AEM-instantie werkt op Tomcat 8.5.88, is het verplicht het servletfragment te installeren *voor* u gaat verder met de installatie van Service Pack 6.5.15.0 of hoger.
* Het is verplicht het servletfragment te installeren voor alle toepassingsservers behalve voor servers die op JBoss® EAP 7.4.0 worden uitgevoerd.

**U installeert als volgt het servletfragment:**

1. Het serverfragment downloaden van [Softwaredistributie](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/featurepack/org.apache.felix.http.servlet-api-1.2.0_fragment_full.jar).
1. Start de toepassingsserver.
1. Wacht tot de logbestanden zijn gestabiliseerd en controleer de toestand van de bundel.
1. Open Web Console-bundels. De standaard-URL is `http://[Server]:[Port]/system/console/bundles`.
1. Selecteren **[!UICONTROL Install]** of **[!UICONTROL Update]**.
1. Het gedownloade fragment selecteren
   `org.apache.felix.http.servlet-api-1.2.0_fragment_full.jar`
1. Selecteren **[!UICONTROL Install]** of **[!UICONTROL Update]**.
1. Wacht tot de toepassingsserver is gestabiliseerd.
1. Stop de toepassingsserver.

#### Adaptieve Forms

* Wanneer een adaptief formulier wordt gepubliceerd, worden alle afhankelijkheden, inclusief het beleid, opnieuw gepubliceerd, zelfs als er geen wijzigingen in zijn aangebracht. (FORMS-10454)
* Wanneer een gebruiker een veld voor het eerst in een adaptief formulier configureert, wordt de optie voor het opslaan van een configuratie niet weergegeven in de eigenschappenbrowser. Als u een ander veld van het adaptieve formulier in dezelfde editor selecteert, wordt het probleem opgelost.
* Wanneer gebruikers de verzendactie uitvoeren, mislukt de verzending met een fout:
  ` javax.servlet.ServletException: java.lang.NoSuchMethodError`
Om het probleem op te lossen, [Compileer de Sling-scripts, zoals JSP, Java en Sright opnieuw](https://experienceleague.adobe.com/docs/experience-cloud-kcs/kbarticles/KA-16543.html?lang=en#resolution). (FORMS-8542)


## OSGi-bundels en inhoudspakketten inbegrepen{#osgi-bundles-and-content-packages-included}

In de volgende tekstdocumenten worden de OSGi-bundels en Content Packages weergegeven die zijn opgenomen in [!DNL Experience Manager] 6.5.19.0: <!-- UPDATE FOR EACH NEW RELEASE -->

* [Lijst van OSGi-bundels opgenomen in Experience Manager 6.5.19.0](/help/release-notes/assets/65190_bundles.txt) <!-- UPDATE FOR EACH NEW RELEASE -->
* [Lijst van inhoudspakketten opgenomen in Experience Manager 6.5.19.0](/help/release-notes/assets/65190_packages.txt) <!-- UPDATE FOR EACH NEW RELEASE -->

## Beperkte websites{#restricted-sites}

Deze websites zijn alleen beschikbaar voor klanten. Als u een klant bent en toegang nodig hebt, neemt u contact op met uw accountmanager van de Adobe.

* [Productdownload op licensing.adobe.com](https://licensing.adobe.com/)
* [Contact opnemen met de klantenondersteuning van de Adobe](https://experienceleague.adobe.com/docs/customer-one/using/home.html).

>[!MORELIKETHIS]
>
>* [[!DNL Experience Manager] productpagina](https://business.adobe.com/products/experience-manager/adobe-experience-manager.html)
>* [[!DNL Experience Manager] 6.5 Documentatie](https://experienceleague.adobe.com/docs/experience-manager-65.html)
>* [Abonneren op Adobe prioritaire productupdates](https://www.adobe.com/subscription/priority-product-update.html)
