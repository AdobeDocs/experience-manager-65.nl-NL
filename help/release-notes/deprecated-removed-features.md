---
title: Vervangen en verwijderde functies in Adobe Experience Manager 6.5-release.
description: Opmerkingen bij de release die specifiek betrekking hebben op vervangen en verwijderde functies in Adobe Experience Manager 6.5.
exl-id: d9b6140a-c37d-4b90-a60c-01f471d65621
solution: Experience Manager
feature: Release Information
role: User,Admin,Architect,Developer
source-git-commit: 191c4b02274ca7e3e9d4622b72cd585870581f47
workflow-type: tm+mt
source-wordcount: '1742'
ht-degree: 2%

---

# Verouderde en verwijderde functies {#deprecated-and-removed-features}

<!-- Search&Promote is end-of-life September 1, 2022 | Assets | If a user does not have sufficient (read and write) permissions on `/content/dam/collections`, the user cannot create a Collection. | Honor the access control setup of user and ensure appropriate permissions. ||
|Adobe Search & Promote|The integration with Adobe Search & Promote is deprecated. Adobe does not plan to make further enhancements to the Search & Promote integration. Adobe Search & Promote integration remains fully supported while being deprecated.||| -->

Adobe evalueert continu de productfuncties, zodat oudere functies na verloop van tijd kunnen worden bijgewerkt of vervangen door modernere alternatieven om de algehele waarde voor de klant te verbeteren. Hierbij wordt altijd zorgvuldig gekeken naar compatibiliteit met oudere versies.

Om de aanstaande verwijdering of vervanging van de mogelijkheden van Adobe Experience Manager (AEM) mee te delen, zijn de volgende regels van toepassing:

1. Aankondiging van afkeuring komt voorop. Hoewel afgekeurd, zijn de mogelijkheden nog beschikbaar maar niet verder verbeterd.
1. Het verwijderen van verouderde mogelijkheden komt in de volgende belangrijkste versie op zijn vroegst voor. De werkelijke streefdatum voor verwijdering wordt later bekendgemaakt.

Dit proces biedt klanten minstens één releasecyclus om hun implementatie aan een nieuwe versie of opvolger van een vervangen capaciteit aan te passen, alvorens daadwerkelijke verwijdering.

## Verouderde functies {#deprecated-features}

Deze sectie maakt een lijst van eigenschappen en mogelijkheden die als verouderd met AEM 6.5 zijn gemerkt. In het algemeen worden functies die in een toekomstige versie moeten worden verwijderd, eerst vervangen, met een alternatief dat beschikbaar is.

Klanten wordt aangeraden na te gaan of zij de functie/functionaliteit in hun huidige implementatie gebruiken en plannen te maken om hun implementatie te wijzigen en het meegeleverde alternatief te gebruiken.

| Gebied | Functie | Vervanging | Versie (SP) |
|---|---|---|---|
|   |   |   |   |
| Sites | De **Adobe AEM Beheerde 1} dienst van de Configuratie van de Opiniepeiling: `com.day.cq.polling.importer.impl.ManagedPollConfigImpl`** | De **Adobe AEM Analytics Report Sling Importer** dienst. Zie Verbinden met Adobe Analytics en Creërend Kader - [ Vormend het Interval van de Invoer ](/help/sites-administering/adobeanalytics-connect.md#configuring-the-import-interval) | 6.5.19,0 |
| Screens | ActiveMQ in Adobe Experience Manager (AEM). ActiveMQ is gebruikt voor communicatie tussen twee AEM Publish-instanties. | Adobe raadt klanten aan een taakverdelingsmechanisme te gebruiken. | 6.5.18.0. |
| De eigenschappen van Fragmenten van de ervaring voor **Sociale Status van Media**. |   | 6.5.11.0. |
| [!DNL Sites] | Inhoudsfragmentsjablonen voor het maken van eenvoudige inhoudsfragmenten. | [ Model-Gebaseerde gestructureerde inhoudsfragmenten ](/help/assets/content-fragments/content-fragments-models.md) nu. | 6.5.11.0. |
| Integratie van Creative Cloud | AEM naar het Delen van de Omslag van het Creative Cloud werd geïntroduceerd in AEM 6.2. Het biedt een manier om creatieve gebruikers toegang te geven tot middelen van AEM, zodat ze deze kunnen openen in [!DNL Creative Cloud] -toepassingen en nieuwe bestanden kunnen uploaden of wijzigingen in AEM kunnen opslaan. Een nieuw vermogen dat in de toepassing van het Creative Cloud, de Verbinding van de Activa van de Adobe wordt vrijgegeven, verstrekt een betere gebruikerservaring en krachtigere toegang tot activa van AEM direct van binnen Photoshop, InDesign, en Illustrator. De Adobe is niet van plan om verdere verhogingen aan de AEM aan het Delen van de Omslag van het Creative Cloud te maken. Terwijl de eigenschap in AEM inbegrepen is, worden de klanten geadviseerd om vervangingsoplossingen te gebruiken. | Klanten wordt aangeraden over te schakelen op nieuwe integratiemogelijkheden voor Creatives Cloud, waaronder Adobe Asset Link of AEM desktop app. |  |
| Assets | `AssetDownloadServlet` is standaard uitgeschakeld voor de publicatie-instanties. Voor meer details, zie [ AEM veiligheid controlelijst ](/help/sites-administering/security-checklist.md). | Configuratie die bij [ wordt beschreven AEM checklist van de Veiligheid ](/help/sites-administering/security-checklist.md). |  |
| Integrations | Het scherm **[!UICONTROL Experience Manager Cloud Services Opt-In]** is verouderd omdat de [!DNL Experience Manager] - en [!DNL Adobe Target] -integratie is bijgewerkt in [!DNL Experience Manager] 6.5. De integratie ondersteunt de Adobe Target Standard API. De API gebruikt verificatie via Adobe IMS en [!DNL Adobe I/O Runtime] . De wizard ondersteunt de groeiende rol van Adobe Launch om [!DNL Experience Manager] -pagina&#39;s te instrumenteren voor analyses en personalisatie. De wizard Optie is functioneel niet relevant. | Configureer systeemverbindingen, Adobe IMS-verificatie en [!DNL Adobe I/O Runtime] -integratie via de respectievelijke [!DNL Experience Manager] -cloudservices. | 6.5.7.0 |
| Aansluitingen | De Adobe JCR Connector voor Microsoft® SharePoint 2010 en Microsoft® SharePoint 2013 is vervangen voor [!DNL Experience Manager] 6.5. | NVT |  |
| Dynamisch tagbeheer (DTM) | De integratie met DTM is afgekeurd. | Schakel over om Adobe Experience Platform Launch te gebruiken als tagbeheer. |   |
| Adobe Target | Door de mogelijkheid voor AEM om verbinding te maken met de Adobe Target-service toe te voegen met behulp van de [!DNL Adobe I/O] gebaseerde Adobe Target Standard API (Rest API) in AEM 6.5, is de wijze van doel-klassieke API (XML) afgekeurd. | Herconfigureer de integratie aan [ gebruik nieuwe API ](/help/sites-administering/target.md). |  |
| Adobe Target | Het gebruik van de op `mbox.js` gebaseerde integratie met Adobe Target in AEM is afgekeurd. | Schakel over naar `at.js` 1.x. |  |
| Commerce | [ CIF REST ](https://github.com/adobe/commerce-cif-api) werd verstrekt in 2018 als reeks microdiensten om integratie tussen AEM en handelmotoren toe te laten. Nadat de Adobe Adobe Commerce (voorheen Magento) medio 2018 had verworven, besloot de Adobe om twee redenen haar aanpak te wijzigen. Commerce heeft een eigen set Commerce API&#39;s (REST en GraphQL) en het is niet aan te raden twee sets API&#39;s te onderhouden. De markttendensen wezen erop dat de klanten naar GraphQL gingen omdat het een efficiëntere manier is om gegevens te vragen. In 2019 heeft Adobe het nieuwe Commerce integration framework gepubliceerd met Commerce GraphQL API&#39;s als bron van waarheid. Adobe is niet van plan verdere investeringen in CIF REST te doen. Klanten wordt aangeraden de vervangende oplossing te gebruiken. | Voor integratie AEM-Commerce, schakelaar aan [ AEM Archetype ](https://github.com/adobe/aem-cif-project-archetype) en [ AEM de Componenten van de Kern ](https://github.com/adobe/aem-core-cif-components). Zie AEM en de integratie van Adobe Commerce [ gebruikend Commerce integration framework ](/help/commerce/cif/integrating/magento.md). Ondersteuning van integratie van derden (anders dan Commerce) met de nieuwe aanpak ligt op de routekaart van de Adobe. |  |
| Componenten (AEM Sites) | De Adobe is niet van plan om verdere verhogingen aan de meeste die Componenten van de Stichting aan te brengen in `/libs/foundation/components` worden opgeslagen. Zoek de eigenschappen `cq:deprecated` en `cq:deprecatedReason` in de componentmap. AEM 6.5 heeft inbegrepen de Componenten van de Stichting, en de klanten die van vroegere versies worden bevorderd kunnen hen blijven gebruiken zoals is. Verder, wordt de Componenten van de Stichting gesteund alhoewel afgekeurd. | Adobe raadt u aan de Core Components (Basiscomponenten) te gebruiken voor toekomstige projecten. De bestaande plaatsen kunnen blijven zoals is of [ gebruiken AEM de Reeks van Hulpmiddelen ](https://github.com/adobe/aem-modernize-tools) moderniseren om de plaats te weerspiegelen om de Componenten van de Kern te gebruiken. |  |
| Componenten (AEM Sites) | Componenten van Design Importer `/libs/wcm/designimporter/components` zijn vanaf 6.5 gemarkeerd als afgekeurd. De Adobe is niet van plan om die implementatie van de ontwerpimporteur verder te verbeteren. | De Adobe is van plan een alternatieve uitvoering van het gebruiksgeval in toekomstige introducties te bieden. |  |
| Stichting | Granite Offloading Framework. De Adobe is niet van plan het offloading-kader dat in CQ 5.6.1 is geïntroduceerd, verder te verbeteren om de verwerking van activa te externaliseren. | Adobe werkt aan een &#39;cloud-native offloading&#39;-framework van de volgende generatie. |  |
| Ontwikkelaars | `Hobbes.js`. Adobe is niet van plan het testframework voor de gebruikersinterface van `hobbes.js` verder te verbeteren. | Adobe raadt klanten aan seleniumautomatisering te gebruiken. |  |
| Ontwikkelaars | jQuery UI-clientbibliotheek. De Adobe is niet van plan om de jQuery UI-clientbibliotheek die als onderdeel van de distributie (QuickStart) wordt verzonden, verder te onderhouden en bij te werken. | De Adobe raadt klanten aan die nog jQuery UI voor hun code vereisen om het in hun basis van de projectcode toe te voegen. |  |
| Ontwikkelaars | jQuery Animation-clientbibliotheek (`granite.jquery.animation`). De Adobe is niet van plan om de jQuery Animation-clientbibliotheek die als onderdeel van de distributie (QuickStart) wordt verzonden, verder te onderhouden en bij te werken. | De Adobe raadt klanten aan die nog jQuery Animaties voor hun code vereisen om het in hun basis van de projectcode toe te voegen. |  |
| Ontwikkelaars | Handlebars cliëntbibliotheek. De Adobe is niet van plan om de de cliëntbibliotheek van Handlebar verder te onderhouden en bij te werken die als deel van de distributie (QuickStart) wordt verscheept. | Adobe raadt klanten die nog steeds `Handlebars` voor hun code nodig hebben, aan deze toe te voegen aan hun projectcodebasis. |  |
| Ontwikkelaars | Lawnstoel clientbibliotheek. De Adobe is niet van plan de clientbibliotheek van Lawnstoel die als onderdeel van de distributie (QuickStart) wordt verzonden, verder te onderhouden en bij te werken. | De Adobe raadt klanten aan die nog altijd de Lay-out voor hun code vereisen om het in hun basis van de projectcode toe te voegen. |  |
| Ontwikkelaars | `Granite.Sling.js` clientbibliotheek. De Adobe is niet van plan om de clientbibliotheek Granite.Sling.js die als onderdeel van de distributie (QuickStart) wordt verzonden, verder te verbeteren. | Adobe raadt klanten die vertrouwen op de mogelijkheid van de bibliotheek om hun code te vernieuwen aan om deze niet meer te gebruiken. |  |
| Ontwikkelaars | Met YUI JavaScript-clientbibliotheken comprimeren/miniaturen maken. Adobe is niet van plan de YUI-bibliotheek verder bij te werken. Tot AEM 6.4 was YUI standaard om JavaScript te minificeren met de optie om over te schakelen naar Google Closure Compiler (GCC). Vanaf AEM 6.5 is GCC standaard. | Adobe raadt klanten aan die een upgrade naar AEM 6.5 uitvoeren om voor hun implementatie over te schakelen op GCC |  |
| Ontwikkelaars | Klassieke UI Dialog Editor in CRXDE Lite. De Adobe is niet van plan om de Klassieke Redacteur van de Dialoog UI verder te verbeteren die als deel van de distributie (QuickStart) wordt verscheept | Er is geen vervanging beschikbaar. |  |
| Forms | AEM Forms-integratie met AEM Mobile is afgekeurd. | Er is geen vervanging beschikbaar. |
| Ontwikkelaars | Klassieke UI Dialog Editor in CRXDE Lite. De Adobe is niet van plan om de Klassieke Redacteur van de Dialoog UI verder te verbeteren die als deel van de distributie (QuickStart) wordt verscheept | Er is geen vervanging beschikbaar. |  |
| Ontwikkelaars | Lodash-/onderstrepingsclientbibliotheek. De Adobe is niet van plan de Lodash/underscore-clientbibliotheek die als onderdeel van de distributie (QuickStart) wordt verzonden, verder te onderhouden en bij te werken. | De Adobe adviseert klanten die nog Lodash/onderstrepingsteken voor hun code vereisen om het in hun basis van de projectcode toe te voegen. |  |

## Verwijderde functies {#removed-features}

Deze sectie bevat een lijst met functies en mogelijkheden die zijn verwijderd uit AEM 6.5. In eerdere versies waren deze mogelijkheden gemarkeerd als afgekeurd.

| Gebied | Functie | Vervanging | Versie (SP) |
|--- |--- |--- |--- |
| Commerce | AEM Classic is verwijderd. | U zou aan [ moeten migreren AEM CIF ](/help/commerce/cif/migration.md). Als u nog CIF Klassiek nodig hebt, is een verenigbaarheidspakket gecreeerd, gelieve [ de Steun van de Klant van de Adobe ](https://experienceleague.adobe.com/?support-solution=General#support) te contacteren. | 6.5.22.0. |
| Integratie met [!DNL Experience Cloud] | U kunt uw elementen synchroniseren met [!DNL Experience Cloud] door ze te configureren via [!DNL Adobe I/O] . [!DNL Adobe Experience Cloud] werd voorheen [!DNL Adobe Experience Cloud] genoemd. | Als u om het even welke vragen hebt, [ contacteer de Steun van de Klant van de Adobe ](https://experienceleague.adobe.com/?support-solution=General#support). |  |
| Activity Map Analytics | De versie van de Activity Map die in AEM is opgenomen. | Vanwege beveiligingswijzigingen in de Adobe Analytics API is het niet langer mogelijk om de versie van de Activity Map te gebruiken die in AEM is opgenomen. Gebruik het [ elektrisch toestel ActivityMap dat door Adobe Analytics ](https://experienceleague.adobe.com/docs/analytics/analyze/activity-map/getting-started/get-started-users/activitymap-install.html) wordt verstrekt. |  |
| Integrations | De integratie ExactTarget is verwijderd uit de standaarddistributie (QuickStart) en het is niet meer beschikbaar. | Geen vervanging. |  |
| Integrations | De integratie van de Kracht API van Salesforce is verwijderd uit de standaarddistributie (QuickStart) en is nu een extra pakket van [ Distributie van de Software ](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html) te installeren. | De functie is nog steeds beschikbaar. |
| Forms | De ondersteuning voor de Adobe Central Migration Bridge service is verwijderd omdat het Adobe Central product niet meer wordt ondersteund. | Geen vervanging. |  |
| Forms | `com.adobe.fd.df.fdinternal.model.ConfigurationInstance` | Geen vervanging. |  |
| Forms | `com.adobe.fd.ccm.channels.print.fdinternal.api.service.PrintDataTransformer` | Geen vervanging |  |
| Forms | Single-hop verbetering van LiveCycle ES4 SP1 aan AEM 6.5 Forms op JEE is niet beschikbaar | Zie [ beschikbare verbeteringspaden ](../forms/using/upgrade.md) in de verbeteringsdocumentatie van AEM Forms. |  |
| Forms | Ondersteuning voor clustering via UPD is verwijderd uit AEM Forms op JEE | U kunt slechts op TCP-Gebaseerde groepering in AEM Forms op JEE gebruiken. Als u een UDP multicast server van een vorige versie aan AEM 5.5 Forms op JEE bevordert, voer handconfiguraties uit om op op TCP-Gebaseerde gemfire zich groeperen. Voor gedetailleerde instructies, zie [ Verbetering aan AEM 6.5 vormen op JEE ](../forms/using/upgrade-forms-jee.md) |  |
| Ontwikkelaars | Firebug Lite is verwijderd uit de standaarddistributie (QuickStart) | De ingebouwde browserconsoles voor ontwikkelaars gebruiken |
| Ontwikkelaars | Verwijder `customJavaScriptPath` -ondersteuning in HTML Client Library Manager. | Geen vervanging |  |
| [!DNL Assets] | De functie voor het ontladen van elementen wordt verwijderd uit [!DNL Adobe Experience Manager] 6.5. | Er is geen vervanging beschikbaar. |  |
| Cache | `system/console/slingjsp` wordt verwijderd en is niet meer beschikbaar in AEM 6.5. | Klassen en de cache wordt iets opgeslagen onder de bundel FileSystem ClassLoader van Apache Sling Commons. U kunt het bundelaantal in de AEM Console van het Web controleren en de geheim voorgeheugenomslag van het dossiersysteem (`crx-quickstart/launchpad/felix/bundle<ID>`) direct verwijderen. |  |
| Screens | Ondersteuning voor activeremq-bundels en de bijbehorende configuraties zijn verwijderd. |  |  |

<!-- ## Pre-announcement for next release {#pre-announcement-for-next-release}

This section is used to pre-announce the upcoming changes in the future releases. The announced changes are not yet effective but will impact customers. For example, the features are not yet deprecated but impacts the users after deprecation. These updates are provided for planning purpose.

|Area|Feature|Announcement|
|--- |--- |--- |
|Foundation|UI Framework|Adobe is planning to deprecate the Coral UI 2 components in 2019. Coral UI 3 was introduced with AEM 6.2, and AEM 6.5 is fully based on Coral 3. Adobe recommends customers and partners that have build custom UIs with Coral 2 to refactored them to Coral 3. Adobe is providing a tool to convert Coral 2 dialogs to Coral 3 - [Read more](/help/sites-developing/modernization-tools.md).|
-->
