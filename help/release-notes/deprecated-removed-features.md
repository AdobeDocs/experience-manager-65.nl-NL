---
title: Vervangen en verwijderde functies in Adobe Experience Manager 6.5-release.
description: Opmerkingen bij de release die specifiek betrekking hebben op vervangen en verwijderde functies in Adobe Experience Manager 6.5.
exl-id: d9b6140a-c37d-4b90-a60c-01f471d65621
solution: Experience Manager
feature: Release Information
role: User,Admin,Architect,Developer
source-git-commit: bd29ae46ead836e16362ad3a9a63bb31548415ff
workflow-type: tm+mt
source-wordcount: '1760'
ht-degree: 2%

---

# Verouderde en verwijderde functies {#deprecated-and-removed-features}

<!-- Search&Promote is end-of-life September 1, 2022 | Assets | If a user does not have sufficient (read and write) permissions on `/content/dam/collections`, the user cannot create a Collection. | Honor the access control setup of user and ensure appropriate permissions. ||
|Adobe Search & Promote|The integration with Adobe Search & Promote is deprecated. Adobe does not plan to make further enhancements to the Search & Promote integration. Adobe Search & Promote integration remains fully supported while being deprecated.||| -->

Adobe evalueert continu de productfuncties, zodat oudere functies na verloop van tijd kunnen worden bijgewerkt of vervangen door modernere alternatieven om de algehele waarde voor de klant te verbeteren. Hierbij wordt altijd zorgvuldig gekeken naar compatibiliteit met oudere versies.

Om de aanstaande verwijdering of vervanging van Adobe Experience Manager (AEM) mogelijkheden mee te delen, zijn de volgende regels van toepassing:

1. Aankondiging van afkeuring komt voorop. Hoewel afgekeurd, zijn de mogelijkheden nog beschikbaar maar niet verder verbeterd.
1. Het verwijderen van verouderde mogelijkheden komt in de volgende belangrijkste versie op zijn vroegst voor. De werkelijke streefdatum voor verwijdering wordt later bekendgemaakt.

Dit proces biedt klanten minstens één releasecyclus om hun implementatie aan een nieuwe versie of opvolger van een vervangen capaciteit aan te passen, alvorens daadwerkelijke verwijdering.

## Verouderde functies {#deprecated-features}

Deze sectie bevat een lijst met functies en mogelijkheden die zijn gemarkeerd als verouderd in AEM 6.5. In het algemeen worden functies die in een toekomstige versie moeten worden verwijderd, eerst vervangen, met een alternatief dat beschikbaar is.

Klanten wordt aangeraden na te gaan of zij de functie/functionaliteit in hun huidige implementatie gebruiken en plannen te maken om hun implementatie te wijzigen en het meegeleverde alternatief te gebruiken.

| Gebied | Functie | Vervanging | Versie (SP) |
|---|---|---|---|
| Sites | [&#x200B; Redacteur van het KUUROORD &#x200B;](/help/sites-developing/spa-editor-deprecation.md) | Voor hoofdloze gebruiksgevallen, hefboomwerking de [&#x200B; Universele Redacteur &#x200B;](/help/sites-developing/universal-editor/introduction.md) voor het visuele uitgeven of de [&#x200B; Redacteur van het Fragment van de Inhoud &#x200B;](/help/sites-developing/universal-editor/introduction.md) voor op vorm-gebaseerde het uitgeven. | 6.5.23. |
| Sites | De **dienst van de Configuratie van de Opiniepeiling van 0&rbrace; Adobe AEM Beheerde: `com.day.cq.polling.importer.impl.ManagedPollConfigImpl`** | De **dienst van het Rapport Sling Importer van de Analyse van Adobe AEM**. Zie Verbinden met Adobe Analytics en Creërend Kader - [&#x200B; Vormend het Interval van de Invoer &#x200B;](/help/sites-administering/adobeanalytics-connect.md#configuring-the-import-interval) | 6.5.19.0 |
| Screens | ActiveMQ in Adobe Experience Manager (AEM). ActiveMQ is gebruikt voor communicatie tussen twee publicatie-instanties van AEM. | Adobe raadt klanten aan een taakverdelingsmechanisme te gebruiken. | 6.5.18.0 |
| De eigenschappen van Fragmenten van de ervaring voor **Sociale Status van Media**. |   | 6.5.11.0 |
| [!DNL Sites] | Inhoudsfragmentsjablonen voor het maken van eenvoudige inhoudsfragmenten. | [&#x200B; Model-Gebaseerde gestructureerde inhoudsfragmenten &#x200B;](/help/assets/content-fragments/content-fragments-models.md) nu. | 6.5.11.0 |
| Creative Cloud-integratie | AEM to Creative Cloud Folder Sharing werd geïntroduceerd in AEM 6.2. Op deze manier kunnen creatieve gebruikers toegang krijgen tot middelen van AEM, zodat ze deze kunnen openen in [!DNL Creative Cloud] -toepassingen en nieuwe bestanden kunnen uploaden of wijzigingen kunnen opslaan in AEM. Een nieuwe functie die wordt vrijgegeven in de Creative Cloud-toepassing, Adobe Asset Link, biedt een betere gebruikerservaring en krachtigere toegang tot middelen van AEM, rechtstreeks vanuit Photoshop, InDesign en Illustrator. Adobe is niet van plan de integratie van AEM naar Creative Cloud Mappen delen verder te verbeteren. Hoewel de functie in AEM is inbegrepen, wordt klanten aangeraden vervangende oplossingen te gebruiken. | Klanten wordt aangeraden over te schakelen op nieuwe Creative Cloud-integratiemogelijkheden, waaronder Adobe Asset Link of AEM desktop app. |  |
| Assets | `AssetDownloadServlet` is standaard uitgeschakeld voor de publicatie-instanties. Voor meer details, zie [&#x200B; de veiligheidscontrolelijst van AEM &#x200B;](/help/sites-administering/security-checklist.md). | De configuratie die bij [&#x200B; wordt beschreven checklist van de Veiligheid van AEM &#x200B;](/help/sites-administering/security-checklist.md). |  |
| Integrations | Het scherm **[!UICONTROL Experience Manager Cloud Services Opt-In]** is verouderd omdat de [!DNL Experience Manager] - en [!DNL Adobe Target] -integratie is bijgewerkt in [!DNL Experience Manager] 6.5. De integratie ondersteunt de Adobe Target Standard API. De API gebruikt verificatie via Adobe IMS en [!DNL Adobe I/O Runtime] . De wizard ondersteunt de groeiende rol van Adobe Launch om [!DNL Experience Manager] -pagina&#39;s te instrumenteren voor analyses en personalisatie. De wizard Optie is functioneel niet relevant. | Configureer systeemverbindingen, Adobe IMS-verificatie en [!DNL Adobe I/O Runtime] -integratie via de respectievelijke [!DNL Experience Manager] -cloudservices. | 6.5.7.0 |
| Aansluitingen | De Adobe JCR Connector voor Microsoft® SharePoint 2010 en Microsoft® SharePoint 2013 is vervangen voor [!DNL Experience Manager] 6.5. | NVT |  |
| Dynamisch tagbeheer (DTM) | De integratie met DTM is afgekeurd. | Schakel over om Adobe Experience Platform Launch te gebruiken als tagbeheer. |   |
| Adobe Target | Als u AEM de mogelijkheid biedt verbinding te maken met de Adobe Target-service met behulp van de [!DNL Adobe I/O] gebaseerde Adobe Target Standard API (Rest API) in AEM 6.5, is de wijze van de Target Classic API (XML) afgekeurd. | Herconfigureer de integratie aan [&#x200B; gebruik nieuwe API &#x200B;](/help/sites-administering/target.md). |  |
| Adobe Target | Het gebruik van de op `mbox.js` gebaseerde integratie met Adobe Target in AEM is afgekeurd. | Schakel over naar `at.js` 1.x. |  |
| Commerce | [&#x200B; CIF REST &#x200B;](https://github.com/adobe/commerce-cif-api) werd verstrekt in 2018 als reeks van microdiensten om integratie tussen AEM en handelsmotoren toe te laten. Nadat Adobe medio 2018 Adobe Commerce (voorheen Magento) had overgenomen, besloot Adobe om twee redenen haar aanpak te wijzigen. Commerce heeft een eigen set Commerce API&#39;s (REST en GraphQL) en het is niet aan te raden twee sets API&#39;s te onderhouden. De markttendensen wezen erop dat de klanten naar GraphQL gingen omdat het een efficiëntere manier is om gegevens te vragen. In 2019 heeft Adobe de nieuwe Commerce integration framework gepubliceerd met Commerce GraphQL API&#39;s als bron van waarheid. Adobe is niet van plan verdere investeringen in CIF REST te doen. Klanten wordt aangeraden de vervangende oplossing te gebruiken. | Voor integratie AEM-Commerce, schakelaar aan [&#x200B; CIF Archetype van AEM &#x200B;](https://github.com/adobe/aem-cif-project-archetype) en [&#x200B; de Componenten van de Kern van AEM CIF &#x200B;](https://github.com/adobe/aem-core-cif-components). Zie AEM en de integratie van Adobe Commerce [&#x200B; gebruikend Commerce integration framework &#x200B;](/help/commerce/cif/integrating/magento.md). Steun voor integratie van derden (anders dan Commerce) met de nieuwe aanpak is op de routekaart van Adobe. |  |
| Componenten (AEM Sites) | Adobe is niet van plan om de meeste Foundation Components die in `/libs/foundation/components` zijn opgeslagen, verder te verbeteren. Zoek de eigenschappen `cq:deprecated` en `cq:deprecatedReason` in de componentmap. AEM 6.5 heeft inbegrepen de Componenten van de Stichting, en de klanten die van vroegere versies worden bevorderd kunnen hen blijven gebruiken zoals is. Verder, wordt de Componenten van de Stichting gesteund alhoewel afgekeurd. | Adobe raadt u aan de Core Components (Basiscomponenten) te gebruiken voor toekomstige projecten. De bestaande plaatsen kunnen ongewijzigd blijven of [&#x200B; AEM Moderniseren Reeks van Hulpmiddelen &#x200B;](https://github.com/adobe/aem-modernize-tools) gebruiken om de plaats te weerspiegelen om de Componenten van de Kern te gebruiken. |  |
| Componenten (AEM Sites) | Componenten van Design Importer `/libs/wcm/designimporter/components` zijn vanaf 6.5 gemarkeerd als afgekeurd. Adobe is niet van plan om die implementatie van de ontwerpimporteur verder te verbeteren. | Adobe is van plan een alternatieve implementatie van het gebruiksgeval in toekomstige releases te bieden. |  |
| Stichting | Granite Offloading Framework. Adobe is niet van plan het offloading-kader dat in CQ 5.6.1 is geïntroduceerd, verder te verbeteren om de verwerking van activa te externaliseren. | Adobe werkt aan een &#39;cloud-native offloading&#39;-framework van de volgende generatie. |  |
| Ontwikkelaars | `Hobbes.js`. Adobe is niet van plan het testframework voor de gebruikersinterface van `hobbes.js` verder te verbeteren. | Adobe raadt klanten aan seleniumautomatisering te gebruiken. |  |
| Ontwikkelaars | jQuery UI-clientbibliotheek. Adobe is niet van plan om de jQuery UI-clientbibliotheek die als onderdeel van de distributie (QuickStart) wordt verzonden, verder te onderhouden en bij te werken. | Adobe raadt klanten aan die nog jQuery UI voor hun code nodig hebben om deze aan hun projectcodebasis toe te voegen. |  |
| Ontwikkelaars | jQuery Animation-clientbibliotheek (`granite.jquery.animation`). Adobe is niet van plan de jQuery Animation-clientbibliotheek die als onderdeel van de distributie (QuickStart) wordt verzonden, verder te onderhouden en bij te werken. | Adobe raadt klanten aan die nog jQuery-animaties voor hun code nodig hebben om deze toe te voegen aan hun projectcodebasis. |  |
| Ontwikkelaars | Handlebars cliëntbibliotheek. Adobe is niet van plan de clientbibliotheek van de Handlebar die als onderdeel van de distributie (QuickStart) wordt verzonden, verder te onderhouden en bij te werken. | Adobe raadt klanten die nog steeds `Handlebars` voor hun code nodig hebben, aan deze toe te voegen aan hun projectcodebasis. |  |
| Ontwikkelaars | Lawnstoel clientbibliotheek. Adobe is niet van plan om de Lawnstoel-clientbibliotheek die als onderdeel van de distributie (QuickStart) wordt verzonden, verder te onderhouden en bij te werken. | Adobe raadt klanten aan die nog steeds Lawnstoel nodig hebben voor hun code om deze toe te voegen aan hun basis met projectcode. |  |
| Ontwikkelaars | `Granite.Sling.js` clientbibliotheek. Adobe is niet van plan om de clientbibliotheek Granite.Sling.js die als onderdeel van de distributie (QuickStart) wordt verzonden, verder te verbeteren. | Adobe raadt klanten aan die op de mogelijkheid van de bibliotheek vertrouwen om hun code te vernieuwen om deze niet meer te gebruiken. |  |
| Ontwikkelaars | Met YUI JavaScript-clientbibliotheken comprimeren/miniaturen maken. Adobe is niet van plan de YUI-bibliotheek verder bij te werken. Tot AEM 6.4 was YUI standaard in staat om JavaScript te miniaturen met de optie om over te schakelen op Google Closure Compiler (GCC). Vanaf AEM 6.5 is GCC standaard. | Adobe raadt klanten aan een upgrade naar AEM 6.5 uit te voeren om over te schakelen naar GCC voor hun implementatie |  |
| Ontwikkelaars | Klassieke UI Dialog Editor in CRXDE Lite. Adobe is niet van plan om de Klassieke Redacteur van de Dialoog UI verder te verbeteren die als deel van de distributie (QuickStart) wordt verscheept | Er is geen vervanging beschikbaar. |  |
| Forms | AEM Forms-integratie met AEM Mobile is afgekeurd. | Er is geen vervanging beschikbaar. |
| Ontwikkelaars | Klassieke UI Dialog Editor in CRXDE Lite. Adobe is niet van plan om de Klassieke Redacteur van de Dialoog UI verder te verbeteren die als deel van de distributie (QuickStart) wordt verscheept | Er is geen vervanging beschikbaar. |  |
| Ontwikkelaars | Lodash-/onderstrepingsclientbibliotheek. Adobe is niet van plan de Lodash/underscore-clientbibliotheek die als onderdeel van de distributie (QuickStart) wordt verzonden, verder te onderhouden en bij te werken. | Adobe raadt klanten aan die nog steeds een liggend streepje/onderstrepingsteken voor hun code nodig hebben om dit aan hun basis voor projectcode toe te voegen. |  |

## Verwijderde functies {#removed-features}

Deze sectie bevat een lijst met functies en mogelijkheden die uit AEM 6.5 zijn verwijderd. In eerdere versies waren deze mogelijkheden gemarkeerd als afgekeurd.

| Gebied | Functie | Vervanging | Versie (SP) |
|--- |--- |--- |--- |
| Commerce | AEM CIF Classic is verwijderd. | U zou aan [&#x200B; AEM CIF &#x200B;](/help/commerce/cif/migration.md) moeten migreren. Als u nog CIF Klassiek nodig hebt, is een verenigbaarheidspakket gecreeerd, gelieve [&#x200B; de Klantenondersteuning van Adobe &#x200B;](https://experienceleague.adobe.com/nl?support-solution=General#support) te contacteren. | 6.5.22.0 |
| Integratie met [!DNL Experience Cloud] | U kunt uw elementen synchroniseren met [!DNL Experience Cloud] door ze te configureren via [!DNL Adobe I/O] . [!DNL Adobe Experience Cloud] werd voorheen [!DNL Adobe Experience Cloud] genoemd. | Als u om het even welke vragen hebt, [&#x200B; contacteer de Klantenondersteuning van Adobe &#x200B;](https://experienceleague.adobe.com/nl?support-solution=General#support). |  |
| Analytics Activity Map | De versie van de Activity Map die in AEM is opgenomen. | Vanwege beveiligingswijzigingen in de Adobe Analytics API is het niet langer mogelijk om de versie van Activity Map te gebruiken die in AEM is opgenomen. Gebruik het [&#x200B; elektrisch toestel ActivityMap dat door Adobe Analytics &#x200B;](https://experienceleague.adobe.com/docs/analytics/analyze/activity-map/getting-started/get-started-users/activitymap-install.html?lang=nl-NL) wordt verstrekt. |  |
| Integrations | De integratie ExactTarget is verwijderd uit de standaarddistributie (QuickStart) en het is niet meer beschikbaar. | Geen vervanging. |  |
| Integrations | De integratie van de Kracht API van Salesforce is verwijderd uit de standaarddistributie (QuickStart) en is nu een extra pakket van [&#x200B; Distributie van de Software &#x200B;](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html) te installeren. | De functie is nog steeds beschikbaar. |
| Forms | De ondersteuning voor Adobe Central Migration Bridge Service is verwijderd omdat het Adobe Central-product niet meer wordt ondersteund. | Geen vervanging. |  |
| Forms | `com.adobe.fd.df.fdinternal.model.ConfigurationInstance` | Geen vervanging. |  |
| Forms | `com.adobe.fd.ccm.channels.print.fdinternal.api.service.PrintDataTransformer` | Geen vervanging |  |
| Forms | Upgrade van één hop van LiveCycle ES4 SP1 naar AEM 6.5 Forms op JEE is niet beschikbaar | Zie [&#x200B; beschikbare verbeteringspaden &#x200B;](../forms/using/upgrade.md) in de verbeteringsdocumentatie van AEM Forms. |  |
| Forms | Ondersteuning voor clustering via UPD is verwijderd uit AEM Forms op JEE | U kunt slechts op TCP-Gebaseerde groepering in AEM Forms op JEE gebruiken. Als u een UDP multicast server van een vorige versie aan AEM 5.5 Forms op JEE bevordert, voer handconfiguraties uit om op op TCP-Gebaseerde gemfire zich groeperen. Voor gedetailleerde instructies, zie [&#x200B; Verbetering aan AEM 6.5 vormen op JEE &#x200B;](../forms/using/upgrade-forms-jee.md) |  |
| Ontwikkelaars | Firebug Lite is verwijderd uit de standaarddistributie (QuickStart) | De ingebouwde browserconsoles voor ontwikkelaars gebruiken |
| Ontwikkelaars | Verwijder `customJavaScriptPath` -ondersteuning in HTML Client Library Manager. | Geen vervanging |  |
| [!DNL Assets] | De functie voor het ontladen van elementen wordt verwijderd uit [!DNL Adobe Experience Manager] 6.5. | Er is geen vervanging beschikbaar. |  |
| Cache | `system/console/slingjsp` wordt verwijderd en is niet meer beschikbaar in AEM 6.5. | Klassen en de cache wordt iets opgeslagen onder de bundel FileSystem ClassLoader van Apache Sling Commons. U kunt het bundelnummer controleren in de AEM Web Console en de cachemap rechtstreeks verwijderen uit het bestandssysteem (`crx-quickstart/launchpad/felix/bundle<ID>`). |  |
| Screens | Ondersteuning voor activeremq-bundels en de bijbehorende configuraties zijn verwijderd. |  |  |

<!-- ## Pre-announcement for next release {#pre-announcement-for-next-release}

This section is used to pre-announce the upcoming changes in the future releases. The announced changes are not yet effective but will impact customers. For example, the features are not yet deprecated but impacts the users after deprecation. These updates are provided for planning purpose.

|Area|Feature|Announcement|
|--- |--- |--- |
|Foundation|UI Framework|Adobe is planning to deprecate the Coral UI 2 components in 2019. Coral UI 3 was introduced with AEM 6.2, and AEM 6.5 is fully based on Coral 3. Adobe recommends customers and partners that have build custom UIs with Coral 2 to refactored them to Coral 3. Adobe is providing a tool to convert Coral 2 dialogs to Coral 3 - [Read more](/help/sites-developing/modernization-tools.md).|
-->
