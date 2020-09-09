---
title: Vervangen en verwijderde functies in Adobe Experience Manager 6.5-release.
description: Opmerkingen bij de release die specifiek betrekking hebben op vervangen en verwijderde functies in Adobe Experience Manager 6.5.
translation-type: tm+mt
source-git-commit: f0dc620926a3ba2558313153f7a0fd3f8cd3c712
workflow-type: tm+mt
source-wordcount: '1722'
ht-degree: 2%

---


# Verouderde en verwijderde functies {#deprecated-and-removed-features}

Adobe evalueert continu de productfuncties, zodat oudere functies na verloop van tijd kunnen worden bijgewerkt of vervangen door modernere alternatieven om de algehele waarde voor de klant te verbeteren. Hierbij wordt altijd zorgvuldig gekeken naar compatibiliteit met oudere versies.

Om de aanstaande verwijdering of vervanging van AEM mogelijkheden mee te delen, zijn de volgende regels van toepassing:

1. Aankondiging van afkeuring komt voorop. Hoewel afgekeurd, zijn de mogelijkheden nog beschikbaar maar niet verder verbeterd.
1. Het verwijderen van verouderde mogelijkheden komt in de volgende belangrijkste versie op zijn vroegst voor. De werkelijke streefdatum voor verwijdering wordt bekendgemaakt.

Dit proces biedt klanten minstens één releasecyclus om hun implementatie aan een nieuwe versie of opvolger van een vervangen capaciteit aan te passen, alvorens daadwerkelijke verwijdering.

## Deprecated features {#deprecated-features}

Deze sectie maakt een lijst van eigenschappen en mogelijkheden die als verouderd met AEM 6.5 zijn gemerkt. In het algemeen worden functies die in een toekomstige versie moeten worden verwijderd, eerst vervangen door een alternatief.

Klanten wordt aangeraden na te gaan of zij in hun huidige implementatie gebruik maken van de functie/mogelijkheid en plannen te maken om hun implementatie te wijzigen en het geboden alternatief te gebruiken.

| Gebied | Functie | Vervanging |
|---|---|---|
| Creative Cloud-integratie | AEM naar het delen van mappen in Creative Cloud is in AEM 6.2 geïntroduceerd als een manier om creatieve gebruikers toegang te geven tot middelen van AEM, zodat ze ze kunnen openen in CC-toepassingen en nieuwe bestanden kunnen uploaden of wijzigingen in AEM kunnen opslaan. Een nieuwe mogelijkheid die wordt vrijgegeven in de Creative Cloud-toepassing, de Adobe Asset Link, biedt een veel betere gebruikerservaring en een krachtigere toegang tot middelen van AEM rechtstreeks vanuit Photoshop, InDesign en Illustrator. Adobe is niet van plan om verdere verbeteringen aan te brengen in de AEM voor het delen van mappen in Creative Cloud. Hoewel de functie in AEM is opgenomen, wordt klanten sterk aangeraden vervangende oplossingen te gebruiken. | Klanten wordt aangeraden over te schakelen op nieuwe integratiemogelijkheden voor Creative Cloud, waaronder Adobe Asset Link of AEM desktop app. De beste praktijken van de Integratie van het overzicht AEM en van de Creative Cloud voor meer details. |
| Assets | `AssetDownloadServlet` is standaard uitgeschakeld voor de publicatie-instanties. Zie [AEM checklist](/help/sites-administering/security-checklist.md)voor beveiliging voor meer informatie. | Configuratie beschreven in [AEM checklist](/help/sites-administering/security-checklist.md)voor beveiliging. |
| Assets | Als een gebruiker onvoldoende (lees- en schrijfrechten) rechten heeft op `/content/dam/collections`, kan de gebruiker geen verzameling maken. | De instelling van de toegangscontrole van de gebruiker respecteren en de juiste machtigingen garanderen. |
| Adobe Search &amp; Promote | De integratie met Adobe Search &amp; Promote is afgekeurd. Adobe is niet van plan om verdere verbeteringen aan te brengen in de integratie van Zoeken en bevorderen. De integratie van Zoeken en bevorderen wordt nog steeds volledig ondersteund wanneer deze wordt vervangen. |  |
| DTM-tagbeheer | De integratie met DTM (Dynamic Tag Manager) is afgekeurd. | Schakel over om Adobe Experience Platform Launch te gebruiken als tagbeheer. |
| Adobe Target | Door de mogelijkheid voor AEM om verbinding te maken met de Adobe Target-service toe te voegen met behulp van de op Adobe I/O gebaseerde Adobe Target Standard API (Rest API) in AEM 6.5, is de wijze van doel-klassieke API (XML) afgekeurd. | Configureer de integratie opnieuw om de nieuwe API [te](https://helpx.adobe.com/experience-manager/kt/sites/using/aem-sites-target-standard-technical-video-understand.html)gebruiken. |
| Adobe Target | Het gebruik van de `mbox.js` gebaseerde integratie met Adobe Target in AEM is afgekeurd. | Schakel over naar gebruik `at.js` 1.x. |
| Handel | [CIF REST](https://github.com/adobe/commerce-cif-api) werd in 2018 verstrekt als een reeks microdiensten om integratie tussen AEM- en handelsmotoren mogelijk te maken. Nadat Adobe medio 2018 Magento had verworven, besloot Adobe om twee redenen haar aanpak te wijzigen. Magento heeft zijn eigen reeks Handel APIs (REST en GraphQL) en het is geen goede praktijk om twee reeksen APIs te handhaven. Markttendensen wezen erop dat klanten zich op GraphQL richtten, omdat het een efficiëntere manier is om gegevens te vragen. In 2019, heeft Adobe het nieuwe Kader van de Integratie van de Handel vrijgegeven gebruikend Magento CommhQL APIs als bron van waarheid. Adobe is niet van plan nog meer te investeren in CIF REST. De klanten worden sterk geadviseerd om de vervangingsoplossing te gebruiken. | Voor AEM-Magento integratie, schakelaar aan [AEM Archetype](https://github.com/adobe/aem-cif-project-archetype) CIF en [AEM de Componenten](https://github.com/adobe/aem-core-cif-components)van de Kern van CIF. Zie AEM en Magento integratie [gebruikend het Kader](https://www.adobe.io/apis/experiencecloud/commerce-integration-framework/integrations.html#!AdobeDocs/commerce-cif-documentation/master/integrations/02-AEM-Magento.md)van de Integratie van de Handel. Steun voor integratie van derden (anders dan Magento) met de nieuwe aanpak staat op ons stappenplan. |
| Componenten (AEM Sites) | Adobe is niet van plan om verdere verhogingen aan de meeste die Componenten van de Stichting te maken in worden opgeslagen `/libs/foundation/components`. Zoek naar het `cq:deprecated` en het `cq:deprecatedReason` bezit in de componentenomslag. AEM 6.5 heeft inbegrepen de Componenten van de Stichting, en de klanten die van vroegere versies worden bevorderd kunnen hen blijven gebruiken zoals is. Verder, wordt de Componenten van de Stichting volledig gesteund alhoewel afgekeurd. | Adobe raadt u aan de Core Components (Basiscomponenten) te gebruiken voor toekomstige projecten. Bestaande sites kunnen ongewijzigd blijven of de [AEM Tools Suite](https://github.com/adobe/aem-modernize-tools) moderniseren gebruiken om de site te vernieuwen en Core Components te gebruiken. |
| Componenten (AEM Sites) | Componenten ontwerpimportmodule `/libs/wcm/designimporter/components` zijn vanaf 6.5 gemarkeerd als afgekeurd. Adobe is niet van plan om die implementatie van de ontwerpimporteur verder te verbeteren. | Adobe is van plan een alternatieve uitvoering van het gebruiksgeval in toekomstige releases te bieden. |
| Stichting | Granite Offloading Framework. Adobe is niet van plan het offloading-kader dat in CQ 5.6.1 is geïntroduceerd, verder te verbeteren om de verwerking van activa te externaliseren. | Adobe werkt aan een &#39;cloud-native offloading&#39;-framework van de volgende generatie. |
| Ontwikkelaars | `Hobbes.js`. Adobe is niet van plan het testframework voor de `hobbes.js` gebruikersinterface verder te verbeteren. | Adobe raadt klanten aan seleniumautomatisering te gebruiken. |
| Ontwikkelaars | jQuery UI-clientbibliotheek. Adobe is niet van plan om de jQuery UI-clientbibliotheek die als onderdeel van de distributie wordt verzonden, verder te onderhouden en bij te werken (QuickStart) | Adobe raadt klanten aan die nog jQuery UI voor hun code vereisen om het in hun basis van de projectcode toe te voegen. |
| Ontwikkelaars | jQuery Animation-clientbibliotheek (`granite.jquery.animation`). Adobe is niet van plan de jQuery Animation-clientbibliotheek die als onderdeel van de distributie wordt verzonden, verder te onderhouden en bij te werken (QuickStart) | Adobe raadt klanten aan die nog jQuery-animaties voor hun code nodig hebben om deze toe te voegen aan hun projectcodebasis. |
| Ontwikkelaars | Handlebars cliëntbibliotheek. Adobe is niet van plan om de de cliëntbibliotheek van Handlebar verder te onderhouden en bij te werken die als deel van de distributie (QuickStart) wordt verscheept | Adobe raadt klanten aan die nog handvatten voor hun code vereisen om het in hun basis van de projectcode toe te voegen. |
| Ontwikkelaars | Lawnstoel clientbibliotheek. Adobe is niet van plan de Lawnstoel-clientbibliotheek die als onderdeel van de distributie wordt verzonden, verder te onderhouden en bij te werken (QuickStart) | Adobe raadt klanten aan die nog steeds een Lawnstoel nodig hebben voor hun code om deze toe te voegen aan hun projectcodebasis. |
| Ontwikkelaars | `Granite.Sling.js` clientbibliotheek. Adobe is niet van plan om de clientbibliotheek Granite.Sling.js die als onderdeel van de distributie wordt verzonden, verder te verbeteren (Quickstart) | Adobe raadt klanten aan die op de mogelijkheid van de bibliotheek vertrouwen om hun code te vernieuwen om deze niet meer te gebruiken. |
| Ontwikkelaars | JavaScript-clientbibliotheken comprimeren/beperken met YUI. Adobe is niet van plan de YUI-bibliotheek verder bij te werken. Tot AEM 6.4 was YUI standaard ingesteld op het minimaliseren van JavaScript met de optie om over te schakelen op Google Closure Compiler (GCC). Vanaf AEM 6.5 is GCC standaard. | Adobe raadt klanten die een upgrade naar AEM 6.5 uitvoeren aan om over te schakelen naar GCC voor hun implementatie |
| Ontwikkelaars | De Klassieke Redacteur van de Dialoog van de UI in CRXDE lijst. Adobe is niet van plan om de Klassieke Redacteur van de Dialoog UI verder te verbeteren die als deel van de distributie (QuickStart) wordt verscheept | Er is geen vervanging beschikbaar. |
| Forms | AEM Forms-integratie met AEM Mobile is afgekeurd. | Er is geen vervanging beschikbaar. |  | Ontwikkelaars | De Klassieke Redacteur van de Dialoog van de UI in CRXDE lijst. Adobe is niet van plan om de Klassieke Redacteur van de Dialoog UI verder te verbeteren die als deel van de distributie (QuickStart) wordt verscheept | Er is geen vervanging beschikbaar. |
| Forms | Lodash-/onderstrepingsclientbibliotheek. Adobe is niet van plan om de Lodash/underscore-clientbibliotheek die als onderdeel van de distributie wordt verzonden, verder te onderhouden en bij te werken (Quickstart) | Adobe raadt klanten aan die nog steeds Lodash/onderstrepingsteken voor hun code nodig hebben om het in hun basis van de projectcode toe te voegen. |

## Verwijderde functies {#removed-features}

Deze sectie bevat een lijst met functies en mogelijkheden die zijn verwijderd uit AEM 6.5. In eerdere versies waren deze mogelijkheden gemarkeerd als afgekeurd.

| Gebied | Functie | Vervanging |
|--- |--- |--- |
| Activity Map Analytics | De versie van de Activity Map die in AEM is opgenomen. | Vanwege beveiligingswijzigingen in de Adobe Analytics API is het niet langer mogelijk om de versie van de Activity Map te gebruiken die in AEM is opgenomen. Gebruik de plug-in [ActivityMap van Adobe Analytics](https://docs.adobe.com/content/help/en/analytics/analyze/activity-map/getting-started/get-started-users/activitymap-install.html). |
| Integrations | De integratie ExactTarget is verwijderd uit de standaarddistributie (QuickStart) en het is niet meer beschikbaar. | Geen vervanging. |
| Integrations | De integratie van de Salesforce-API is verwijderd uit de standaarddistributie (QuickStart) en is nu een extra pakket dat u kunt installeren bij [Softwaredistributie](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html). | De functie is nog steeds beschikbaar. |
| Forms | De ondersteuning voor de Adobe Central Migration Bridge-service is verwijderd omdat het Adobe Central-product niet meer wordt ondersteund. | Geen vervanging. |
| Forms | `com.adobe.fd.df.fdinternal.model.ConfigurationInstance` | Geen vervanging. |
| Forms | `com.adobe.fd.ccm.channels.print.fdinternal.api.service.PrintDataTransformer` | Geen vervanging |
| Forms | Single-hop verbetering van LiveCycle ES4 SP1 aan AEM 6.5 Forms op JEE is niet beschikbaar | Zie de [beschikbare upgradepaden](../forms/using/upgrade.md) in de upgradedocumentatie van AEM Forms. |
| Forms | Ondersteuning voor clustering via UPD is verwijderd uit AEM Forms op JEE | U kunt slechts op TCP-Gebaseerde groepering in AEM Forms op JEE gebruiken. Als u een UDP multicast server van een vorige versie aan AEM 5.5 Forms op JEE bevordert, voer handconfiguraties uit om op TCP gebaseerde gemfire zich het groeperen over te schakelen. Zie [Upgrade naar AEM 6.5-formulieren op JEE voor gedetailleerde instructies](../forms/using/upgrade-forms-jee.md) |
| Ontwikkelaars | Firebug Lite is verwijderd uit de standaarddistributie (QuickStart) | De ingebouwde browserconsoles voor ontwikkelaars gebruiken |
| Ontwikkelaars | Verwijder `customJavaScriptPath` ondersteuning in HTML Client Library Manager. | Geen vervanging |
| [!DNL Assets] | De functie voor het offloaden van elementen wordt verwijderd in [!DNL Adobe Experience Manager] 6.5. | Er is geen vervanging beschikbaar. |
| Cache | `system/console/slingjsp` is verwijderd, is niet meer beschikbaar in AEM 6.5. | Klassen en de cache wordt iets opgeslagen onder de bundel FileSystem ClassLoader van Apache Sling Commons. U kunt het bundelnummer in de AEM webconsole controleren en de cachemap rechtstreeks uit het bestandssysteem (`crx-quickstart/launchpad/felix/bundle<ID>`) verwijderen. |

## Vooraankondiging voor volgende release {#pre-announcement-for-next-release}

Deze sectie wordt gebruikt om de aanstaande veranderingen in de toekomstige versies aan te kondigen. De aangekondigde wijzigingen zijn nog niet effectief, maar zullen gevolgen hebben voor klanten. De functies zijn bijvoorbeeld nog niet verouderd, maar hebben invloed op de gebruikers na de veroudering. Deze updates worden verstrekt voor planningsdoel.

| Gebied | Functie | Aankondiging |
|--- |--- |--- |
| Stichting | UI Framework | Adobe is van plan om de Coral UI 2 componenten in 2019 te schrappen. Coral UI 3 werd geïntroduceerd met AEM 6.2 en AEM 6.5 is volledig gebaseerd op koraal 3. Adobe raadt klanten en partners aan die douane UIs met Koraal 2 hebben gebouwd om hen aan Koraal 3 te refactored. Adobe is een hulpmiddel om de dialogen van Koraal 2 om te zetten in Koraal 3 - [Lees meer](/help/sites-developing/dialog-conversion.md). |
