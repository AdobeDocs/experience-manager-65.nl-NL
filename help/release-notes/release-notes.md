---
title: Opmerkingen bij de release [!DNL Adobe Experience Manager] 6,5
description: Zoek naar releasegegevens, wat is nieuw, installeer hoe kan worden gewijzigd en een gedetailleerde wijzigingslijst voor [!DNL Adobe Experience Manager] 6.5
mini-toc-levels: 3
source-git-commit: 85189a4c35d1409690cbb93946369244e8848340
workflow-type: tm+mt
source-wordcount: '3816'
ht-degree: 0%

---

# [!DNL Adobe Experience Manager] 6.5 Laatste Opmerkingen bij de release Service Pack {#aem-service-pack-release-notes}

<!-- For an itemized list of all issues found in these release notes, see the following spreadsheet: https://adobe-my.sharepoint.com/:x:/r/personal/anujkapo_adobe_com/_layouts/15/Doc.aspx?sourcedoc=%7B3ea81ae4-e605-4153-b132-f2698c86f84e%7D&action=edit&wdinitialsession=d8c7b903-87fc-4f2d-9ef2-542a82169570&wdrldsc=3&wdrldc=1&wdrldr=SessionMemoryQuotaExceededDuringSession&cid=a915e87c-369a-480c-9daf-d13efc766798 -->

## Gegevens vrijgeven {#release-information}

| Product | [!DNL Adobe Experience Manager] 6,5 |
| -------- | ---------------------------- |
| Versie | 6.5.15.0. <!-- UPDATE FOR EACH NEW RELEASE --> |
| Type | Service Pack-release |
| Date | 24 november 2022 <!-- UPDATE FOR EACH NEW RELEASE --> |
| URL downloaden | [Softwaredistributie](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/servicepack/aem-service-pkg-6.5.15.0.zip) <!-- UPDATE FOR EACH NEW RELEASE --> |

## Wat is inbegrepen in [!DNL Experience Manager] 6.5.15.0. {#what-is-included-in-aem-6515}

[!DNL Experience Manager] 6.5.15.0 omvat nieuwe eigenschappen, zeer belangrijke klant-gevraagde verhogingen, insectenmoeilijke situaties, en prestaties, stabiliteit, en veiligheidsverbeteringen, die sinds de aanvankelijke beschikbaarheid van 6.5 in April 2019 worden vrijgegeven. [Dit servicepack installeren](#install) op [!DNL Experience Manager] 6.5 <!-- UPDATE FOR EACH NEW RELEASE -->

<!-- Some of the key features and improvements are the following:

* _REVIEWERS: WHAT ARE THE KEY FEATURES AND ENHANCEMENTS YOU WANT TO HIGHLIGHT IN THIS RELEASE?_

* Added support for password reset for Dynamic Media Classic users within Experience Manager. (ASSETS-10298) -->

<!-- UPDATE BELOW FOR EACH NEW RELEASE -->

## [!DNL Assets] {#assets-6515}

* Als de verplaatsing van een actief in Experience Manager mislukt, kan de naam van het element nog steeds worden gewijzigd. (NPR-38753)
* Tijdens het weergeven van de elementen in een [!UICONTROL List View], ontbreken enkele titels. (CQ-4345746)
* De schermlezer kondigt het submenu van het dialoogvenster [!UICONTROL Relate] op het tabblad Standaard op de pagina Eigenschappen van element. (ACTIVA-6938)
* Schermlezer detecteert de mappictogrammen op de elementennavigatiepagina onjuist met de lijst met mappen. (ACTIVA-6936)
* Tijdens het kopiëren van een verzameling ontbreekt een lege afbeelding `alt` attribute or role=&quot;presentation&quot;. Hierdoor wordt de afbeelding beschikbaar gemaakt voor de gebruikers van de schermlezer. (ACTIVA-6932)
* De tekst die wordt weergegeven terwijl u een element annoteert, heeft geen 4:5:1 contrastverhouding in vergelijking met de achtergrondkleur. (ACTIVA-6931)
* Als u de paginabreedte aanpast op het tabblad IPTC van de pagina-eigenschappen, past de pagina-inhoud niet goed en wordt horizontaal schuiven toegepast. (ACTIVA-6929)
* Wanneer u elementen filtert, wordt de filtertekst in het dialoogvenster [!UICONTROL min] en [!UICONTROL max] de velden verdwijnen nadat een waarde is ingevoerd. (ACTIVA-6925)
* In Experience Manager Collections kondigt de schermlezer het [!UICONTROL email] op het scherm Downloaden. (ACTIVA-6923)
* Er ontbreekt een alternatieve tekst bij het annoteren van de elementen. (ACTIVA-6922)
* Als de tekst in het veld Uren en Minuten in de datumkiezer is geschreven, wordt er geen tekstfoutbericht weergegeven. De fout wordt alleen geïdentificeerd met de rode kleur. (ACTIVA-6852, ACTIVA-6921, ACTIVA-6920, ACTIVA-6907)
* De alternatieve tekst in `[role='img']` in het filter Bestanden ontbreekt. (ACTIVA-6919)
* Onjuiste schermlezeraankondiging voor de [!UICONTROL Create] submenu. (ACTIVA-6916)
* In de Verzamelingen van de Experience Manager, verwijdert knoop `X` heeft geen tekst om aan te kondigen voor schermlezers. (ACTIVA-6912)
* Bij gebruik van Kleurcontrastanalyse in Experience Manager is er geen kleuronderscheid tussen de huidige datum en de gekozen datum in de datumkiezer van de kalenderwidget. Het gebrek aan een contrastverhouding van minstens 3:1 in tegenstelling tot de aangrenzende kleuren. (ACTIVA-6911)
* In de Dossiers van de Experience Manager, terwijl het selecteren van één van de opties van [!UICONTROL Scheduling] keuzerondje in Publicatie beheren. De naam en status van de keuzerondjes worden door de schermlezer aangekondigd. De **Planning** label wordt niet aangekondigd. (ACTIVA-6908, ACTIVA-6906)
* De alternatieve tekst ontbreekt voor het pictogram Sorteren. (ACTIVA-6904)
* Op de pagina met eigenschappen van elementen wordt de veldnaam `Person` in IPTC-extensie worden de labels niet door de schermlezers aangekondigd. De schermlezer kondigt alleen het bewerkbare en momenteel lege veld aan, maar niet de labelnaam. (ACTIVA-6903, ACTIVA-6848)
* Het gereedschap Annotatie kan niet worden weergegeven met het toetsenbord. Er wordt een muis gebruikt om een afbeelding te tekenen om het gereedschap Annotatie weer te geven. (ACTIVA-6899)
* In Experience Manager Collections, een leeg gebied op **Geavanceerd** wordt een onjuiste contrastverhouding tussen de grens en een aangrenzende kleur weergegeven. (ACTIVA-6895)
* Onjuiste ARIA-kenmerkwaarden voor sommige elementen tijdens het bewerken van elementen. (ACTIVA-6894)
* De schermlezer herkent de kop niet correct tijdens het maken van een workflow. (ACTIVA-6892)
* Tijdens het kopiëren van een verzameling verwijdert de SVG-afbeelding de knop `X` met role=&quot;img&quot; mist een role=&quot;presentation&quot;. Hierdoor wordt de afbeelding beschikbaar gemaakt voor de gebruikers van de schermlezer. (ACTIVA-6890)
* In de **Basis** met de eigenschappen van Elementen, kondigt de schermlezer niet op de juiste wijze de toestand van het veld Codes uit- of samenvouwen aan. (ACTIVA-6889)
* De **Basis** onder Eigenschappen van element bevat pagina&#39;s met een dubbele id. (ACTIVA-6888)
* Het label van het tekstveld voor het definiëren van een titel tijdens het maken van een werkstroom verdwijnt wanneer u een waarde opgeeft in het tekstvak. (ACTIVA-6887)
* De lijst met ontvangers tijdens het delen van een koppeling wordt weergegeven als een gegevenstabel met koppen, maar wordt niet semantisch geïdentificeerd als een gegevenstabel voor de gebruikers van de schermlezer. (ACTIVA-6886)
* Er wordt geen foutbericht weergegeven voor een leeg veld in `Add Email Address` veld. De fout wordt alleen met een kleur weergegeven. (ACTIVA-6885, ACTIVA-6843)
* Plaatsaanduidingsteksten, paden en Alt-tekst hebben niet ten minste een contrastverhouding van 4,5:1 ten opzichte van de achtergrondkleur. (ACTIVA-6884, ACTIVA-6865)
* Ongeldige waarden voor sommige ARIA-kenmerken bij het opslaan van een slimme verzameling. (ACTIVA-6882)
* Wanneer u een slimme verzameling opslaat, worden sommige labels niet op de juiste wijze gekoppeld aan de schermlezer. (ACTIVA-6881)
* Op het tabblad IPTC van de eigenschappen van het element wordt het label voor de trefwoordformuliervelden niet door de schermlezer aangekondigd. (ACTIVA-6879)
* In de Verzamelingen van de Experience Manager, [!UICONTROL Email] Het veld wordt niet geïdentificeerd als verplicht veld en er wordt geen foutbericht weergegeven als u geen waarde opgeeft. (ACTIVA-6877)
* In Experience Manager Files, geen foutenmelding in **Koppeling delen** scherm wordt weergegeven in `Add Email Address`. De fout wordt alleen geïdentificeerd bij het gebruik van een kleur. (ACTIVA-6876, ACTIVA-6875)
* [!UICONTROL Crop and Map] opties hebben niet de programmatische namen terwijl het uitgeven van activa. (ACTIVA-6874)
* In de filtertekst ontbreekt een contractverhouding van 4,5:1 ten opzichte van de achtergrondkleur. (ACTIVA-6873)
* De tekst voor de mapnaam op de hoofdnavigatiepagina heeft geen contrastverhouding van 4,5:1 ten opzichte van de achtergrondkleur. (ACTIVA-6872)
* Tijdens het uitvoeren van de [!UICONTROL Copy] bewerking voor verzamelingen, de **[!UICONTROL Add User]** formulierbesturingselement voor keuzelijst met invoervak is niet correct gekoppeld aan het zichtbare label ervan. (ACTIVA-6870)
* De schermlezer kondigt het [!UICONTROL Create] submenuopties voor knoppen. (ACTIVA-6869)
* De opties Bereik, Workflows en Tijdzone hebben geen contrastverhouding van 4,5:1 in vergelijking met de achtergrondkleur. (ACTIVA-6868)
* De schermlezer kondigt ten onrechte de status voor samenvouwen van het dialoogvenster **Tijdlijn** kolom. (ACTIVA-6864)
* Ontbrekende onderliggende elementen voor sommige ARIA-rollen terwijl een slimme verzameling wordt opgeslagen. (ACTIVA-6862)
* Tijdens het delen van een element zijn ARIA-kenmerken vereist voor `Search/Add Email Address` worden niet opgegeven. (ACTIVA-6860)
* De **map** kan niet worden weergegeven met het toetsenbord. In plaats daarvan is een muisklik vereist om het dialoogvenster voor kaart weer te geven. (ACTIVA-6859)
* Ontbrekende onderliggende elementen voor sommige ARIA-rollen op het tabblad Standaard van de pagina Eigenschappen van element. (ACTIVA-6858)
* De lege tekstinvoervelden, die beschikbaar zijn op het IPTC-tabblad van de eigenschappen Asset, hebben geen contrastverhouding van 3:1 in vergelijking met de aangrenzende kleuren. (ACTIVA-6854, ACTIVA-6847)
* De profielpictogrammen in het dialoogvenster **Tijdlijn** worden niet goed gedetecteerd door de schermlezers. (ACTIVA-6850)
* Schermlezer geeft niet aan dat het keuzemenu Revisiestatus, dat beschikbaar is op het tabblad Standaard van de eigenschappen van middelen, een alleen-lezen veld is. (ACTIVA-6849)
* De schermlezer kondigt het label van de selectievakjes Alles selecteren en Annotatie niet correct aan. (ACTIVA-6846)
* De toetsenbordfocus slaat de `About Adobe Experience Manager` beschikbaar in het dialoogvenster **Help weergeven** -menu. (ACTIVA-6845)
* Schermlezers geven de geselecteerde mappen niet correct door terwijl ze door de lijst met mappen navigeren met de pijltoetsen op het toetsenbord in de kaartweergave. (ACTIVA-6844)
* Tijdens het uploaden van een PDF naar de Experience Manager neemt het geheugengebruik voortdurend toe. (ACTIVA-16889)
* Wanneer een werkstroom een .ZIP dossier in een omslagnaam in Middelen omzet, behoudt het niet het omhulsel van het .ZIP dossier - naam. (ACTIVA-16712)
* Bij het schakelen van Brand Portal naar Experience Manager 6.5 geeft het filter voor de gebruikersvoorspelling niet de juiste resultaten weer wanneer u het filter voor het eerst toepast. (ACTIVA-15932)
* Kan geen notitie van een video maken. (ACTIVA-15217)
* **Publicatie beheren** deze optie verdwijnt voor een gebruiker zonder replicatietoegang en `READ` en `WRITE` toegang tot `ETC` en `VAR`. (ACTIVA-15007)
* De laadtijd voor de eigenschappenpagina neemt toe voor een element met meerdere verwijzingen. (ACTIVA-14182)
* Wanneer een afbeelding niet in Brand Portal is gepubliceerd, maakt Experience Manager de publicatie ervan vanuit Dynamic Media ongedaan en wordt er daarom geen afbeelding weergegeven op de live website. (ACTIVA-14118)
* XSS-problemen met SmartCrop-kaarten in Dynamic Media. (ACTIVA-14212, ACTIVA-14208, ACTIVA-13704)
* XSS-probleem in viewervoorinstellingen in Dynamic Media. (ACTIVA-13822)
* Valideer gebruikerstoegang terwijl het previewing van de activa van DM op AEM. (CQ-4314757)


## Handel {#commerce-6515}

* Het maken van een winkelpagina is mislukt. Het volledige uitrolproces van de catalogus wordt gestopt. (CQ-4347181)

## [!DNL Forms] {#forms-6515}

### Belangrijkste kenmerken {#keyfeatures}

* AEM Forms Designer is nu beschikbaar in de landinstelling Spaans. (LC-3920051)
* U kunt OAuth2 nu gebruiken om met de protocollen van de de postserver van Microsoft Office 365 (SMTP en IMAP) voor authentiek te verklaren. (NPR-35177)
* U kunt instellen [Revalidate op server](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/create-an-adaptive-form/configure-submit-actions-and-metadata-submission/configuring-submit-actions.html?lang=en#server-side-revalidation-in-adaptive-form-server-side-revalidation-in-adaptive-form) eigenschap in op true om de verborgen velden te identificeren voor uitsluiting van een document of record op de server. (NPR-38149)
* AEM Forms Designer vereist een 32-bits versie van Visual C++ 2019 Redistributable (x86).  (NPR-36690)

### Oplossingen {#fixes}

* Wanneer de eigenschap data-disabled van een adaptief formulier wordt geschakeld, verandert de weergave van keuzerondjes en selectievakjes niet. (NPR-39368)
* Wanneer een adaptief formulier wordt vertaald, worden sommige vertalingen overgeslagen en niet correct weergegeven. (NPR-39367)
* Wanneer de eigenschap van een pagina is ingesteld op verborgen, wordt de pagina niet verwijderd uit de formulierset. (NPR-39325)
* In een Document of Record is de dynamische voetnootsectie aan het einde van de pagina niet aanwezig. (NPR-39322)
* Wanneer een Document of Record wordt gegenereerd voor een adaptief formulier, is alleen de verticale uitlijning toegestaan voor keuzerondjes en selectievakjes. De gebruiker kan de horizontale uitlijning voor keuzerondjes en selectievakjes niet instellen. (NPR-39321)
* Als meerdere gebruikers na de implementatie van Correspondence Management toegang proberen te krijgen tot een formulier, wordt org.apache.sling.i18n.impl.JcrResourceBundle.loadPotentialLanguageRoots een knelpunt en wordt een meerderheid van de threads geraakt. Diverse paginaverzoeken voor formulieren duurden vaak langer dan 1 minuut om elke pagina te laden, zelfs als de server een zeer lage belasting heeft. (NPR-39176, CQ-4347710)
* Wanneer u in een adaptief formulier een veld met RTF-opmaak gebruikt in een lazy geladen adaptief formulierfragment, worden enkele van de volgende fouten aangetroffen:
   * U kunt de inhoud niet bewerken en niets toevoegen aan het veld RTF.
   * Het weergavepatroon dat op de RTF-tekst wordt toegepast, wordt niet toegepast. 
   * Het foutbericht voor de minimale veldlengte wordt niet weergegeven bij het verzenden van het formulier.
   * De inhoud van dit rijke-tekstgebied is inbegrepen verscheidene tijden in geproduceerde voorlegt-XML. (NPR-39168)
* Wanneer de optie Datumkiezer wordt gebruikt in een adaptief formulier, wordt de waarde niet geconverteerd naar de juiste notatie. (NPR-39156)
* Een adaptief formulier wordt tijdens de voorbeeldweergave als een HTML-formulier niet correct weergegeven, omdat sommige subformulieren overlappen met het bovenliggende formulier. (NPR-39046)
* Als het deelvenster een tabel heeft verborgen en het aangepaste formulier wordt weergegeven in de tabelweergave, worden de velden op het eerste tabblad niet correct weergegeven. (NPR-39025)
* De `Body` -tag ontbreekt voor de sjabloon OOTB (Out-of-the-Box). (NPR-39022)
* Het document met records wordt niet gegenereerd in de taal van het adaptieve formulier. Het wordt altijd gegenereerd in het Engels. (NPR-39020)
* Als een adaptief formulier meerdere deelvensters heeft en in sommige deelvensters de optie Out-of-the-box wordt gebruikt **Bestandsbijlage** de `Error occurred while draft saving` Er is een fout opgetreden. (NPR-38978)
* Wanneer `=` wordt gebruikt in het selectievakje, de vervolgkeuzelijst of de keuzerondjesvelden van een adaptief formulier en het document of record wordt gegenereerd. `=` Het teken is niet zichtbaar in het gegenereerde document of record.(NPR-38859)
* Er is een veelvoudige verhoging van het aantal fouten van de Verwerking van de Partij van de Bericht na de verbetering van het de dienstpak van 6.5.11.0. (NPR-39636)
* Wanneer u geen testgegevens verstrekt, kunnen de brieven van het Beheer van de Correspondentie niet in de Agent UI laden. (CQ-4348702)
* Wanneer de gebruiker AEM Forms Service Pack 14 (SP14) van AEM Forms toepast die gebruikend IBM® WebSphere® wordt opgesteld, ontbreekt bootstrapping terwijl het initialiseren van een gegevensbestand en `java.lang.NoClassDefFoundError:org/apache/log4j/Logger` fout treedt op.(NPR-39414)
* Op een AEM Form op OSGi server, wanneer u de Dienst API van het Document gebruikt om PDF te verklaren, ontbreekt het met fout: com.adobe.fd.signatures.truststore.errors.exception.CredentialRetrievalException: AEM-DSS-311-003. (NPR-38855)
* Wanneer de gebruiker de wrapperservice probeert te gebruiken voor het renderen van letters met AEM 6.3 Forms, wordt `java.lang.reflect.UndeclaredThrowableException` fout treedt op. (CQ-4347259)
* Wanneer een XDP wordt weergegeven als een HTML5-formulier, wordt de inhoud van de master pagina eerst gerenderd, ongeacht de plaatsing van de objecten in een adaptief formulier. (CQ-4345218)
* De configuratie van de toepassing bij de bestemmingsserver verandert in de montages die bij de bronserver worden bepaald alhoewel **Configuratie overschrijven wanneer het importeren is voltooid** Deze optie is niet ingeschakeld op het moment dat de toepassing wordt geïmporteerd. (NPR-39044)
* Wanneer een gebruiker probeert om schakelaarconfiguratie bij te werken gebruikend de Manager van de Configuratie, ontbreekt het.(CQ-4347077)
* Wanneer de gebruiker een AEM Forms op JEE flard na het veranderen van het standaardwachtwoord van de beheerdergebruiker probeert in werking te stellen, een uitzondering `com.adobe.livecycle.lcm.core.LCMException[ALC-LCM-200-003]: Failed to whitelist the classes` voorkomt. (CQ-4348277)
* In AEM Designer worden formuliervelden zonder bijschriften in tabelcellen geplaatst, inclusief selectievakjes.(LC-3920410)
* Wanneer de gebruiker de Help probeert te openen in AEM Forms Designer, wordt deze niet correct weergegeven. (CQ-434/1996)

## [!DNL Sites] {#sites-6515}

* Experience Manager Sites Launches-console is leeg. (NPR-39188)
* De verwijzingen zijn niet aangepast wanneer de pagina waarop de verwijzing staat, tijdens het verplaatsen van de pagina moest worden geactiveerd. (NPR-39061)
* Wanneer een container Layout niet verborgen is met behulp van de bovenliggende container, worden de layoutwijzigingen niet toegepast op alle componenten in de geneste container. (NPR-39041)
* De inhoud overlapt nu niet meer met andere inhoud met een breedte van 320 pixels. (SITES-8885)
* Focus toegevoegd nadat een dialoogvenster is gesloten. (SITES-8885)

### Toegankelijkheid {#access-6515}

<!-- REMOVED FROM TOTAL RELEASE CANDIDATE LIST * The scrollable region of the Page Editor did not have keyboard access. (SITES-2936) -->
<!-- REMOVED FROM TOTAL RELEASE CANDIDATE LIST * The color input field of the Page Editor is not labeled or visible on the screen. (SITES-2925) -->
<!-- REMOVED FROM TOTAL RELEASE CANDIDATE LIST * The iframe in the Page Editor is missing a title attribute; it must have an accessible name. (SITES-2894) -->
* De **[!UICONTROL Annotation]** de toegankelijkheidsnaam van de knop ontbreekt. (SITES-2892)
* De status van een actieve gebruikersinterfacecomponent (**[!UICONTROL Cut]**, **[!UICONTROL Copy]**, **[!UICONTROL Paste]**, **[!UICONTROL Insert Components]**, **[!UICONTROL Group]**, enzovoort) heeft niet ten minste een drie tot één lichtsterktecontrastverhouding met de binnen- of buitenste aangrenzende achtergrond. (SITES-8889, SITES-8756, SITES-8885)
* Statusbericht niet automatisch aangekondigd. (SITES-8889, SITES-8756, SITES-8885)
* Tekstinhoud heeft geen contrastverhouding van 4,5:1. (SITES-8756, SITES-8885)
* Bij koppelings- of knoptekst ontbreekt de contrastverhouding van 4,5:1 bij aanwijzen of focus. (SITES-8756, SITES-8885)

### [!DNL Content Fragments] {#sites-contentfragments-6515}

* GraphQL heft een uitzondering op. U kunt bijvoorbeeld geen variatietags ophalen uit een inhoudsfragment. Er is geen variatie met de naam &#39;elektrisch&#39;. Dit probleem is te wijten aan het aanroepen van `getVariationTags` voor een niet-bestaande wijziging die een uitzondering doet ontstaan. (SITES-8898)
* Bezig met het sorteren van titelorders in de lijstweergave, zowel oplopend als aflopend, van de titels met de volgorde A, C, B. (SITES-7585)
* Ondersteuning voor extra tags voor variaties van inhoudsfragmenten. (SITES-8168)
* Identificeerde en verwijderde Odin-specifieke code uit Experience Manager 6.5 die onnodig was. (SITES-3574)
* Bij het publiceren van een taalexemplaarfragment uit de gebruikersinterface van de Inhoudsfragmenteditor werden de bijbehorende verwijzingen gepubliceerd in de Engelse map. (NPR-39182)
* Datumvelden worden vooraf ingevuld met een datum. (NPR-39124)
* Tags verdwijnen de tweede keer dat u de optie Keuzerondje selecteert. (NPR-39071)

### Fluid XP {#sites-fluidxp-6515}

* Ondersteuning voor ES6-compilatie inschakelen voor de clientbibliotheek `/libs/cq/gui/components/siteadmin/admin/restoretree/clientlibs/restoretree.js`. (NPR-39067)
* Het multiveld in een inhoudsfragmentmodel kan niet worden geleegd en opgeslagen, omdat de validatie ook plaatsvindt als **[!UICONTROL Required]** is niet geselecteerd. (NPR-39063)
* In of **[!UICONTROL Copy]** of **[!UICONTROL Livecopy]** de `cq:targetMetadata` gegevens worden onjuist gedupliceerd. Deze functionaliteit veroorzaakte twee of meer Fragments van de Ervaring in Experience Manager om aan de zelfde aanbieding te richten die in doel wordt uitgevoerd. (NPR-38970)
* Na een actie van de herstelstructuur verschijnt het bericht `Un-publication pending. #0 in the queue` wordt weergegeven in de gebruikersinterface van een pagina die nooit in de eerste plaats is gepubliceerd. (NPR-38847)

### Pagina-editor {#sites-pageeditor-6515}

* Ongedaan maken heeft niet de laatste wijziging verwijderd die is aangebracht in de tekst die is toegevoegd aan de component. In plaats daarvan, toen de pagina werd verfrist, werd de volledige component geschrapt. (SITES-8597)
* Bijwerken `jquery-ui` naar de meest recente versie heeft geleid dat de Pagina-editor niet correct werkte. (NPR-38596)
* De inhoud overlapt nu niet meer met andere inhoud met een breedte van 320 pixels. (SITES-8756)
* extra focus na het sluiten van het dialoogvenster (SITES-8756)

## Sling {#sling-6515}

* `Repoinit` ondersteunt het maken of beheren van groepen met witruimte in de hoofdnaam niet omdat de groepsnaam als een tekenreeks is behandeld en geen ondersteuning biedt voor het aanhalen van een citaat. (SLING-10952)
* Logbestanden worden per ongeluk gevuld met foutberichten en uitzonderingen. (NPR-39024)

## Vertaalprojecten {#translation-6515}

* De doelpagina werd via het deelvenster Projecten toegevoegd aan de vertaaltaak voor bijgewerkte taalkopieën. bronpagina is niet bijgewerkt. (NPR-39278)
* Het vertaalproces is mislukt tijdens het genereren van een voorvertoning voor alle pagina&#39;s in een vertaalproject. (NPR-39059)
* Als de taallandinstelling niet bestaat, wordt deze nog steeds in een landinstellingsmap gemaakt wanneer de regels voor verwijzingen voor een gebeurtenis zijn geconfigureerd. (NPR-39054)

## Gebruikersinterface {#ui-6515}

* JavaScript-fouten treden op in het bestand `multifield.js` voor bepaalde gebieden in het model van het Fragment van de Inhoud in de modelredacteur van het Fragmentvan de Inhoud en ook in de redacteur van het Fragment van de Inhoud. (NPR-39350)

## Workflow {#workflow-6515}

* Workflow&#39;s die succesvol werden uitgevoerd op Experience Manager 6.5.11, werden niet consistent uitgevoerd op 6.5.13 van Experience Manager. (NPR-39023)

## Installeren [!DNL Experience Manager] 6.5.15.0. {#install}

<!-- Remaining content from here to bottom stays the same except for version updating as needed as per update team feedback. -->

* [!DNL Experience Manager] 6.5.15.0 vereist [!DNL Experience Manager] 6.5 Zie [upgradedocumentatie](/help/sites-deploying/upgrade.md) voor gedetailleerde instructies. <!-- UPDATE FOR EACH NEW RELEASE -->
* De download van het de dienstpak is beschikbaar op Adobe [Softwaredistributie](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html).
* Bij een implementatie met MongoDB en meerdere exemplaren, installeert u [!DNL Experience Manager] 6.5.15.0 op één van de instanties van de Auteur die de Manager van het Pakket gebruiken.<!-- UPDATE FOR EACH NEW RELEASE -->

>[!IMPORTANT]
>
>Adobe raadt u niet aan de [!DNL Experience Manager] 6.5.15.0-pakket. Voordat u het pakket installeert, moet u daarom een back-up maken van het `crx-repository` voor het geval u het terug moet rollen. <!-- UPDATE FOR EACH NEW RELEASE -->

### Installeer het de dienstpak op [!DNL Experience Manager] 6,5 {#install-service-pack}

1. Start de instantie opnieuw vóór de installatie als de updatemodus voor de instantie is geactiveerd (wanneer de instantie is bijgewerkt vanaf een eerdere versie). Adobe raadt aan de toepassing opnieuw te starten als de huidige uptime voor een instantie hoog is.

1. Maak voordat u gaat installeren een momentopname of een nieuwe back-up van uw [!DNL Experience Manager] -instantie.

1. Download het servicepack van [Softwaredistributie](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/servicepack/aem-service-pkg-6.5.15.0.zip). <!-- UPDATE FOR EACH NEW RELEASE -->

1. Pakketbeheer openen en vervolgens selecteren **[!UICONTROL Upload Package]** om het pakket te uploaden. Zie voor meer informatie [Pakketbeheer](/help/sites-administering/package-manager.md).

1. Selecteer het pakket en selecteer vervolgens **[!UICONTROL Install]**.

1. Om de S3 schakelaar bij te werken, stop de instantie na installatie van het Service Pack, vervang de bestaande schakelaar met een nieuw binair dossier dat in de installatiemap wordt verstrekt, en begin de instantie opnieuw. Zie [Amazon S3 Data Store](/help/sites-deploying/data-store-config.md#upgrading-to-a-new-version-of-the-s-connector).

>[!NOTE]
>
>De dialoog over de Manager UI van het Pakket bestaat soms tijdens de installatie van het de dienstpak. Adobe raadt aan dat u op foutenlogboeken wacht om zich te stabiliseren alvorens tot de plaatsing toegang te hebben. Wacht op de specifieke logboeken met betrekking tot het verwijderen van de updaterbundel alvorens wordt verzekerd dat de installaties succesvol zijn. Dit probleem treedt meestal op in [!DNL Safari] browser, maar kan soms voorkomen op om het even welke browser.

**Automatische installatie**

Er zijn twee verschillende methoden die u automatisch kunt installeren [!DNL Experience Manager] 6.5.15.0.<!-- UPDATE FOR EACH NEW RELEASE -->

* Plaats het pakket in `../crx-quickstart/install` als de server online beschikbaar is. Het pakket wordt automatisch geïnstalleerd.
* Gebruik de [HTTP-API van Package Manager](/help/sites-administering/package-manager.md#package-share). Gebruiken `cmd=install&recursive=true` zodat de geneste pakketten worden geïnstalleerd.

>[!NOTE]
>
>Experience Manager 6.5.15.0 ondersteunt geen Bootstrap-installatie. <!-- UPDATE FOR EACH NEW RELEASE -->

**De installatie valideren**

Als u wilt weten welke platformen gecertificeerd zijn voor deze release, raadpleegt u de [technische voorschriften](/help/sites-deploying/technical-requirements.md).

1. De pagina met productinformatie (`/system/console/productinfo`) geeft de bijgewerkte versietekenreeks weer `Adobe Experience Manager (6.5.15.0)` krachtens [!UICONTROL Installed Products]. <!-- UPDATE FOR EACH NEW RELEASE -->

1. Alle OSGi-bundels zijn **[!UICONTROL ACTIVE]** of **[!UICONTROL FRAGMENT]** in de Console OSGi (de Console van het Gebruik: `/system/console/bundles`).

1. De OSGi-bundel `org.apache.jackrabbit.oak-core` is versie 1.22.13 of hoger (webconsole gebruiken: `/system/console/bundles`). <!-- NPR-39436 for 6.5.15.0 --> <!-- OAK VERSION -MAY- NEED TO BE UPDATED FOR EACH NEW RELEASE -->

### Installeren [!DNL Experience Manager] Forms-invoegtoepassing {#install-aem-forms-add-on-package}

>[!NOTE]
>
>Overslaan als u dit niet gebruikt [!DNL Experience Manager] Forms.

<!-- 
Fixes in [!DNL Experience Manager] Forms are delivered through a separate add-on package a week after the scheduled [!DNL Experience Manager] Service Pack release.
-->

1. Controleer of u de [!DNL Experience Manager] Service Pack.
1. Download het overeenkomstige Forms-add-on-pakket dat is vermeld op [AEM Forms-releases](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/forms-updates/aem-forms-releases.html#forms-updates) voor uw besturingssysteem.
1. Het Forms-invoegtoepassingspakket installeren zoals beschreven in [AEM Forms-add-onpakketten installeren](/help/forms/using/installing-configuring-aem-forms-osgi.md#install-aem-forms-add-on-package).
1. Als u letters gebruikt in Experience Manager 6.5 Forms, installeert u de [nieuwste AEMFD-compatibiliteitspakket](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/forms-updates/aem-forms-releases.html#forms-updates).

### Installeren [!DNL Experience Manager] Forms op JEE {#install-aem-forms-jee-installer}

>[!NOTE]
>
>Sla dit over als u AEM Forms niet gebruikt op JEE. Oplossingen in [!DNL Experience Manager] Forms op JEE wordt via een afzonderlijk installatieprogramma geleverd.

Voor informatie over het installeren van het cumulatieve installatieprogramma voor [!DNL Experience Manager] Forms op JEE en configuratie na implementatie, zie [releaseopmerkingen](jee-patch-installer-65.md).

>[!NOTE]
>
>Na installatie van het cumulatieve installatieprogramma voor [!DNL Experience Manager] Forms on JEE, installeer het nieuwste Forms add-on pakket, verwijder het Forms add-on pakket uit het `crx-repository\install` en start de server opnieuw op.

### UberJar {#uber-jar}

The UberJar for [!DNL Experience Manager] 6.5.15.0 is beschikbaar in de [Maven Central-opslagplaats](https://repo.maven.apache.org/maven2/com/adobe/aem/uber-jar/6.5.15/). <!-- CHECK FOR UPDATE EACH NEW RELEASE -->

Om UberJar in een Geweven project te gebruiken, zie [gebruiken van UberJar](/help/sites-developing/ht-projects-maven.md) en neem het volgende gebiedsdeel in uw project POM op: <!-- CHECK FOR UPDATE EACH NEW RELEASE -->

```shell
<dependency>
     <groupId>com.adobe.aem</groupId>
     <artifactId>uber-jar</artifactId>
     <version>6.5.15</version>
     <scope>provided</scope>
</dependency>
```

>[!NOTE]
>
>UberJar en de andere verwante artefacten zijn beschikbaar op de Centrale Bewaarplaats van de Adobe Openbare Maven bewaarplaats (`repo.adobe.com`). De naam van het hoofdbestand van UberJar wordt gewijzigd in `uber-jar-<version>.jar`. Er is dus geen `classifier`, met `apis` als de waarde voor de `dependency` tag.

## Verouderde functies {#removed-deprecated-features}

Hieronder vindt u een lijst met functies en mogelijkheden die zijn gemarkeerd als verouderd met [!DNL Experience Manager] 6.5.7.0. Functies worden in eerste instantie gemarkeerd als afgekeurd en in een toekomstige versie verwijderd. Er is een alternatieve optie opgegeven.

Herzie als u een eigenschap of een vermogen in een plaatsing gebruikt. Ook, ben van plan om de implementatie te veranderen om een afwisselende optie te gebruiken.

| Gebied | Functie | Vervanging |
|---|---|---|
| Integrations | De **[!UICONTROL AEM Cloud Services Opt-In]** het scherm is verouderd sinds [!DNL Experience Manager] en [!DNL Adobe Target] integratie wordt bijgewerkt in [!DNL Experience Manager] 6.5 De integratie ondersteunt de Adobe Target Standard API. De API gebruikt verificatie via Adobe IMS en [!DNL Adobe I/O Runtime]. Het ondersteunt de groeiende rol van Adobe Launch naar instrument [!DNL Experience Manager] De optiewizard is functioneel niet relevant op pagina&#39;s voor analyse en personalisatie. | Systeemverbindingen, Adobe IMS-verificatie en [!DNL Adobe I/O Runtime] integratie via de respectieve [!DNL Experience Manager] cloudservices. |
| Connectors | De Adobe JCR Connector voor Microsoft® SharePoint 2010 en Microsoft® SharePoint 2013 is vervangen voor [!DNL Experience Manager] 6.5 | N.v.t. |

## Bekende problemen {#known-issues}

<!-- THESE KNOWN ISSUES CARRY OVER EACH RELEASE. THE "PRODUCT UPDATES TEAM" IS SUPPOSED TO VERIFY EACH ISSUE AND LET YOU KNOW IF ANYTHING NEEDS TO BE ADDED, DELETED, OR CHANGED IN THIS LIST.
 -->

* [Inhoudsfragment AEM met GraphQL Index Package 1.0.5](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=%2Fcontent%2Fsoftware-distribution%2Fen%2Fdetails.html%2Fcontent%2Fdam%2Faem%2Fpublic%2Fadobe%2Fpackages%2Fcq650%2Ffeaturepack%2Fcfm-graphql-index-def-1.0.5.zip)
Dit pakket is nodig voor klanten die GraphQL gebruiken; hierdoor kunnen ze de vereiste indexdefinitie toevoegen op basis van de functies die ze daadwerkelijk gebruiken.

* Als [!DNL Microsoft® Windows Server 2019] ondersteunt niet [!DNL MySQL 5.7] en [!DNL JBoss® EAP 7.1], [!DNL Microsoft® Windows Server 2019] ondersteunt geen kant-en-klare installaties voor [!DNL AEM Forms 6.5.10.0].

* Als u een upgrade uitvoert op uw [!DNL Experience Manager] van 6.5 tot 6.5.10.0 versie, kunt u bekijken `RRD4JReporter` uitzonderingen in de `error.log` bestand. Start de instantie opnieuw om het probleem op te lossen.

* Als u [!DNL Experience Manager] 6.5 Service Pack 10 of een vorig de dienstpak op [!DNL Experience Manager] 6.5, de runtime kopie van het aangepaste workflowmodel voor uw middelen (gemaakt in `/var/workflow/models/dam`) wordt geschrapt.
Om uw runtime exemplaar terug te winnen, adviseert Adobe om het ontwerp-tijd exemplaar van het model van het douanewerkschema met zijn runtime exemplaar te synchroniseren gebruikend HTTP API:
   `<designModelPath>/jcr:content.generate.json`.

* Gebruikers kunnen de naam wijzigen van een map in een hiërarchie in [!DNL Assets] en publiceer een geneste map naar [!DNL Brand Portal]. De titel van de map wordt echter niet bijgewerkt in [!DNL Brand Portal] totdat de hoofdmap opnieuw wordt gepubliceerd.

* Wanneer een gebruiker een veld voor het eerst in een adaptief formulier configureert, wordt de optie voor het opslaan van een configuratie niet weergegeven in de eigenschappenbrowser. Als u een ander veld van het adaptieve formulier in dezelfde editor selecteert, wordt het probleem opgelost.

* De volgende fouten en waarschuwingsberichten kunnen tijdens de installatie van [!DNL Experience Manager] 6.5.x.x:
   * &quot;Wanneer de Adobe Target-integratie is geconfigureerd in [!DNL Experience Manager] Als u de standaard-API (IMS-verificatie) van het doel gebruikt, leidt het exporteren van ervaringsfragmenten naar Doel tot onjuiste aanbiedingstypen die worden gemaakt. In plaats van het type &quot;Experience Fragment&quot;/bron &quot;Adobe Experience Manager&quot; maakt Target verschillende aanbiedingen met het type &quot;HTML&quot;/bron &quot;Adobe Target Classic&quot;.
   * `com.adobe.granite.maintenance.impl.TaskScheduler`: Geen onderhoudsvensters gevonden bij graniet/bediening/onderhoud.
   * De validatie aan de adaptieve formulierserver-side mislukt wanneer statistische functies zoals SUM, MAX en MIN worden gebruikt (CQ-4274424).
   * `com.adobe.granite.maintenance.impl.TaskScheduler` - Geen onderhoudsvensters gevonden bij graniet/bediening/onderhoud.
   * Hotspot in een interactieve Dynamic Media-afbeelding is niet zichtbaar wanneer u een voorvertoning van het element weergeeft via de Shopable Banner-viewer.
   * `com.adobe.cq.social.cq-social-jcr-provider bundle com.adobe.cq.social.cq-social-jcr-provider:1.3.5 (395)[com.adobe.cq.social.provider.jcr.impl.SpiSocialJcrResourceProviderImpl(2302)]` : Time-out bij wachten op wijziging van register is niet-geregistreerd.

* Wanneer u probeert inhoudsfragmenten of sites/pagina&#39;s te verplaatsen/verwijderen/publiceren, is er een probleem wanneer verwijzingen naar inhoudsfragmenten worden opgehaald, omdat de achtergrondquery mislukt. De functionaliteit werkt dus niet.
Om correcte verrichting te verzekeren, moet u de volgende eigenschappen aan de knoop van de indexdefinitie toevoegen `/oak:index/damAssetLucene` (opnieuw indexeren is niet vereist):

   ```xml
   "tags": [
       "visualSimilaritySearch"
     ]
   "refresh": true
   ```

## OSGi-bundels en inhoudspakketten inbegrepen {#osgi-bundles-and-content-packages-included}

De volgende tekstdocumenten maken een lijst van de bundels OSGi en de Pakketten van de Inhoud inbegrepen in [!DNL Experience Manager] 6.5.15.0: <!-- UPDATE FOR EACH NEW RELEASE -->

* [Lijst van OSGi-bundels opgenomen in Experience Manager 6.5.15.0](/help/release-notes/assets/65150_bundles.txt) <!-- UPDATE FOR EACH NEW RELEASE -->
* [Lijst van inhoudspakketten opgenomen in Experience Manager 6.5.15.0](/help/release-notes/assets/65150_packages.txt) <!-- UPDATE FOR EACH NEW RELEASE -->

## Beperkte websites {#restricted-sites}

Deze websites zijn alleen beschikbaar voor klanten. Als u een klant bent en toegang nodig hebt, neemt u contact op met uw Adobe-accountmanager.

* [Productdownload op licensing.adobe.com](https://licensing.adobe.com/)
* [Contact opnemen met de Adobe Klantenondersteuning](https://experienceleague.adobe.com/docs/customer-one/using/home.html).

>[!MORELIKETHIS]
>
>* [[!DNL Experience Manager] productpagina](https://business.adobe.com/products/experience-manager/adobe-experience-manager.html)
>* [[!DNL Experience Manager] 6.5 Documentatie](https://experienceleague.adobe.com/docs/experience-manager-65.html)
>* [Abonneren op updates van prioritaire Adobe-producten](https://www.adobe.com/subscription/priority-product-update.html)

