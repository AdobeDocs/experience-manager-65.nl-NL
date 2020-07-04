---
title: Vervangen en Verwijderde Eigenschappen in Adobe Experience Manager 6.5 versie.
description: Opmerkingen bij de release die specifiek betrekking hebben op vervangen en verwijderde functies in Adobe Experience Manager 6.5.
translation-type: tm+mt
source-git-commit: 29f8e59e3fc9d3c089ee3b78c24638cd3cd2e96b
workflow-type: tm+mt
source-wordcount: '1642'
ht-degree: 2%

---


# Verouderde en verwijderde functies {#deprecated-and-removed-features}

Adobe evalueert continu de productfuncties, zodat oudere functies na verloop van tijd kunnen worden bijgewerkt of vervangen door modernere alternatieven om de algehele waarde voor de klant te verbeteren. Hierbij wordt altijd zorgvuldig gekeken naar compatibiliteit met oudere versies.

Om de aanstaande verwijdering of vervanging van de mogelijkheden van AEM mee te delen, zijn de volgende regels van toepassing:

1. Aankondiging van afkeuring komt voorop. Hoewel afgekeurd, zijn de mogelijkheden nog beschikbaar maar niet verder verbeterd.
1. Het verwijderen van verouderde mogelijkheden komt in de volgende belangrijkste versie op zijn vroegst voor. De werkelijke streefdatum voor verwijdering wordt bekendgemaakt.

Dit proces biedt klanten minstens één releasecyclus om hun implementatie aan een nieuwe versie of opvolger van een vervangen capaciteit aan te passen, alvorens daadwerkelijke verwijdering.

## Verouderde functies {#deprecated-features}

Deze sectie bevat een lijst met functies en mogelijkheden die zijn gemarkeerd als verouderd in AEM 6.5. In het algemeen worden functies die in een toekomstige release verwijderd moeten worden, eerst vervangen, met een alternatief dat beschikbaar is.

Klanten wordt aangeraden na te gaan of zij in hun huidige implementatie gebruik maken van de functie/mogelijkheid en plannen te maken om hun implementatie te wijzigen en het geboden alternatief te gebruiken.

| Gebied | Functie | Vervanging |
|---|---|---|
| Creative Cloud-integratie | AEM naar Creative Cloud Mappen delen is geïntroduceerd in AEM 6.2 als een manier om creatieve gebruikers toegang te geven tot middelen van AEM, zodat ze deze kunnen openen in CC-toepassingen en nieuwe bestanden kunnen uploaden of wijzigingen in AEM kunnen opslaan. Een nieuwe functie die wordt vrijgegeven in de Creative Cloud-toepassing Adobe Asset Link, biedt een veel betere gebruikerservaring en krachtigere toegang tot middelen van AEM, rechtstreeks vanuit Photoshop, InDesign en Illustrator. Adobe is niet van plan verdere verbeteringen aan te brengen in de integratie van AEM voor het delen van Creative Cloud-mappen. Hoewel de functie in AEM is opgenomen, wordt klanten sterk aangeraden vervangende oplossingen te gebruiken. | Klanten wordt aangeraden over te schakelen op nieuwe mogelijkheden voor Creative Cloud-integratie, waaronder Adobe Asset Link of AEM-bureaubladtoepassing. Lees de beste praktijken voor AEM- en Creative Cloud-integratie voor meer informatie. |
| Assets | `AssetDownloadServlet` is standaard uitgeschakeld voor de publicatie-instanties. Zie de [AEM-beveiligingscontrolelijst](/help/sites-administering/security-checklist.md)voor meer informatie. | Configuratie beschreven op [AEM Security checklist](/help/sites-administering/security-checklist.md). |
| Assets | Als een gebruiker onvoldoende (lees- en schrijfrechten) rechten heeft op `/content/dam/collections`, kan de gebruiker geen verzameling maken. | De instelling van de toegangscontrole van de gebruiker respecteren en de juiste machtigingen garanderen. |
| Adobe Search &amp; Promote | De integratie met Adobe Search &amp; Promote is afgekeurd. Adobe is niet van plan verdere verbeteringen aan te brengen in de Search &amp; Promote-integratie. Merk op dat de integratie van de Search &amp; Promote volledig gesteund blijft terwijl wordt afgekeurd. |  |
| DTM-tagbeheer | De integratie met DTM (Dynamic Tag Manager) is afgekeurd. | Schakel over om Adobe Experience Platform starten te gebruiken als tagbeheer. |
| Adobe Target | Door de mogelijkheid voor AEM om verbinding te maken met de Adobe Target-service toe te voegen met de Adobe I/O-gebaseerde Adobe Target Standard API (Rest API) in AEM 6.5, is de manier van Target Classic API (XML) afgekeurd. | Configureer de integratie opnieuw om de nieuwe API [te](https://helpx.adobe.com/experience-manager/kt/sites/using/aem-sites-target-standard-technical-video-understand.html)gebruiken. |
| Adobe Target | Het gebruik van de `mbox.js` gebaseerde integratie met Adobe Target in AEM is afgekeurd. | Schakel over naar gebruik `at.js` 1.x. |
| Handel | [CIF REST](https://github.com/adobe/commerce-cif-api) werd in 2018 verstrekt als een reeks microdiensten om integratie tussen AEM- en handelsmotoren mogelijk te maken. Nadat Adobe Magento medio 2018 had aangeschaft, besloot Adobe om twee redenen zijn aanpak te wijzigen. Magento heeft zijn eigen reeks Handel APIs (REST en GraphQL) en het is geen goede praktijk om twee reeksen APIs te handhaven. Markttendensen wezen erop dat klanten zich op GraphQL richtten, omdat het een efficiëntere manier is om gegevens te vragen. In 2019 heeft Adobe het nieuwe Commerce Integration Framework uitgebracht met behulp van de GraphQL API&#39;s van Magento als bron van de waarheid. Adobe is niet van plan meer te investeren in CIF REST. De klanten worden sterk geadviseerd om de vervangingsoplossing te gebruiken. | Schakel voor AEM-Magento-integratie over naar [AEM CIF Archetype](https://github.com/adobe/aem-cif-project-archetype) en [AEM CIF Core Components](https://github.com/adobe/aem-core-cif-components). Zie integratie AEM en Magento [gebruikend het Kader](https://www.adobe.io/apis/experiencecloud/commerce-integration-framework/integrations.html#!AdobeDocs/commerce-cif-documentation/master/integrations/02-AEM-Magento.md)van de Integratie van de Handel. Steun voor integratie van derden (andere dan Magento) met de nieuwe aanpak staat op onze routekaart. |
| Onderdelen (AEM Sites) | Adobe is niet van plan om de meeste Foundation Components die in zijn opgeslagen, verder te verbeteren `/libs/foundation/components`. Zoek naar het `cq:deprecated` en het `cq:deprecatedReason` bezit in de componentenomslag. AEM 6.5 heeft de inbegrepen Componenten van de Stichting, en de klanten die van vroegere versies bevorderen kunnen blijven gebruiken hen zoals is. Verder, wordt de Componenten van de Stichting volledig gesteund alhoewel afgekeurd. | Adobe raadt u aan de kerncomponenten voor toekomstige projecten te gebruiken. Bestaande sites kunnen ongewijzigd blijven of met de [AEM Modernize Tools Suite](https://github.com/adobe/aem-modernize-tools) de site vernieuwen en Core Components gebruiken. |
| Onderdelen (AEM Sites) | Componenten ontwerpimportmodule `/libs/wcm/designimporter/components` zijn vanaf 6.5 gemarkeerd als afgekeurd. Adobe is niet van plan verdere verbeteringen aan te brengen in die implementatie van de ontwerpimportmodule. | Adobe is van plan een alternatieve implementatie van het gebruiksgeval in toekomstige versies te bieden. |
| Stichting | Granite Offloading Framework. Adobe is niet van plan het offloading-framework, dat is geïntroduceerd in CQ 5.6.1, verder te verbeteren om de verwerking van bedrijfsmiddelen extern te maken. | Adobe werkt aan een &#39;cloud-native offloading&#39;-framework van de volgende generatie. |
| Ontwikkelaars | `Hobbes.js`. Adobe is niet van plan het testframework voor de `hobbes.js` gebruikersinterface verder te verbeteren. | Adobe raadt klanten aan seleniumautomatisering te gebruiken. |
| Ontwikkelaars | jQuery UI-clientbibliotheek. Adobe is niet van plan de jQuery UI-clientbibliotheek die als onderdeel van de distributie wordt verzonden, verder te onderhouden en bij te werken (QuickStart) | Adobe raadt klanten aan die nog jQuery-gebruikersinterface voor hun code nodig hebben om deze aan hun projectcodebasis toe te voegen. |
| Ontwikkelaars | jQuery Animation-clientbibliotheek (`granite.jquery.animation`). Adobe is niet van plan de jQuery Animation-clientbibliotheek die als onderdeel van de distributie wordt verzonden, verder te onderhouden en bij te werken (QuickStart) | Adobe raadt klanten aan die nog jQuery-animaties nodig hebben voor hun code, deze toe te voegen aan hun projectcodebasis. |
| Ontwikkelaars | Handlebars cliëntbibliotheek. Adobe is niet van plan de clientbibliotheek van de Handlebar die als onderdeel van de distributie wordt verzonden, verder te onderhouden en bij te werken (QuickStart) | Adobe raadt klanten aan die nog steeds Handlebars voor hun code nodig hebben om deze aan hun projectcodebasis toe te voegen. |
| Ontwikkelaars | Lawnstoel clientbibliotheek. Adobe is niet van plan de clientbibliotheek van Lawnstoel die als onderdeel van de distributie wordt verzonden, verder te onderhouden en bij te werken (QuickStart) | Adobe raadt klanten die nog steeds een Lawnstoel-code nodig hebben aan om deze code toe te voegen aan hun projectcodebasis. |
| Ontwikkelaars | `Granite.Sling.js` clientbibliotheek. Adobe is niet van plan de clientbibliotheek Granite.Sling.js die wordt verzonden als onderdeel van de distributie, verder te verbeteren (QuickStart) | Adobe raadt klanten aan die op de mogelijkheid van de bibliotheek vertrouwen om hun code te vernieuwen om deze niet meer te gebruiken. |
| Ontwikkelaars | JavaScript-clientbibliotheken comprimeren/beperken met YUI. Adobe is niet van plan de YUI-bibliotheek verder bij te werken. Tot en met AEM 6.4 was YUI standaard ingesteld op het minimaliseren van JavaScript met de optie om over te schakelen op Google Closure Compiler (GCC). Vanaf AEM 6.5 is GCC standaard. | Adobe raadt klanten aan een upgrade naar AEM 6.5 uit te voeren om over te schakelen naar GCC voor hun implementatie |
| Ontwikkelaars | De Klassieke Redacteur van de Dialoog van de UI in CRXDE lijst. Adobe is niet van plan om de Klassieke Redacteur van de Dialoog UI verder te verbeteren die als deel van de distributie (QuickStart) wordt verscheept | Er is geen vervanging beschikbaar. |
| Formulieren | De integratie van AEM Forms met AEM Mobile is afgekeurd. | Er is geen vervanging beschikbaar. |

## Verwijderde functies {#removed-features}

Deze sectie bevat een lijst met functies en mogelijkheden die zijn verwijderd uit AEM 6.5. In eerdere versies waren deze mogelijkheden gemarkeerd als afgekeurd.

| Gebied | Functie | Vervanging |
|--- |--- |--- |
| Analytics Activity Map | De versie van de Activity Map die in AEM is opgenomen. | Vanwege beveiligingswijzigingen in de Adobe Analytics API is het niet langer mogelijk de versie van de Activity Map te gebruiken die in AEM is opgenomen. Gebruik de plug-in [ActivityMap van Adobe Analytics](https://docs.adobe.com/content/help/en/analytics/analyze/activity-map/getting-started/get-started-users/activitymap-install.html). |
| Integrations | De integratie ExactTarget is verwijderd uit de standaarddistributie (QuickStart) en het is niet meer beschikbaar. | Geen vervanging. |
| Integrations | De integratie van de Salesforce-API is verwijderd uit de standaarddistributie (QuickStart) en is nu een extra pakket dat u kunt installeren bij [Softwaredistributie](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html). | De functie is nog steeds beschikbaar. |
| Formulieren | De ondersteuning voor de Adobe Central Migration Bridge-service is verwijderd omdat het Adobe Central-product niet meer wordt ondersteund. | Geen vervanging. |
| Formulieren | `com.adobe.fd.df.fdinternal.model.ConfigurationInstance` | Geen vervanging. |
| Formulieren | `com.adobe.fd.ccm.channels.print.fdinternal.api.service.PrintDataTransformer` | Geen vervanging |
| Formulieren | Single-hop verbetering van S4 SP1 aan Vormen AEM 6.5 op JEE is niet beschikbaar | Zie [beschikbare verbeteringspaden](../forms/using/upgrade.md) in de de verbeteringsdocumentatie van AEM Forms. |
| Formulieren | Op UPD gebaseerde clusterondersteuning is verwijderd uit AEM Forms op JEE | U kunt slechts op TCP-Gebaseerd groeperen in AEM Forms op JEE gebruiken. Als u een UDP multicast server van een vorige versie aan Vormen AEM 5.5 op JEE bevordert, voer handconfiguraties uit om op TCP gebaseerde gemfire zich het groeperen over te schakelen. Zie [Upgrade naar AEM 6.5-formulieren op JEE voor gedetailleerde instructies](../forms/using/upgrade-forms-jee.md) |
| Ontwikkelaars | Firebug Lite is verwijderd uit de standaarddistributie (QuickStart) | De ingebouwde browserconsoles voor ontwikkelaars gebruiken |
| Ontwikkelaars | Verwijder `customJavaScriptPath` ondersteuning in HTML Client Library Manager. | Geen vervanging |
| [!DNL Assets] | De functie voor het offloaden van elementen wordt verwijderd in [!DNL Adobe Experience Manager] 6.5. | Er is geen vervanging beschikbaar. |
| Cache | `system/console/slingjsp` is verwijderd, is niet meer beschikbaar in AEM 6.5. | Klassen en de cache wordt iets opgeslagen onder de bundel FileSystem ClassLoader van Apache Sling Commons. U kunt het bundelnummer controleren in de AEM-webconsole en de cachemap rechtstreeks uit het bestandssysteem (`crx-quickstart/launchpad/felix/bundle<ID>`) verwijderen. |

## Vooraankondiging voor volgende release {#pre-announcement-for-next-release}

Deze sectie wordt gebruikt om de aanstaande veranderingen in de toekomstige versies aan te kondigen. De aangekondigde wijzigingen zijn nog niet effectief, maar zullen gevolgen hebben voor klanten. De functies zijn bijvoorbeeld nog niet verouderd, maar hebben invloed op de gebruikers na de veroudering. Deze updates worden verstrekt voor planningsdoel.

| Gebied | Functie | Aankondiging |
|--- |--- |--- |
| Stichting | UI Framework | Adobe is van plan de Coral UI 2-componenten in 2019 te vervangen. Koraal UI 3 werd geïntroduceerd met AEM 6.2, en AEM 6.5 is volledig gebaseerd op Koraal 3. Adobe raadt klanten en partners die aangepaste UI&#39;s met Coral 2 hebben gemaakt aan om deze opnieuw te bemonsteren naar Coral 3. Adobe biedt een programma voor het converteren van de dialoogvensters Koraal 2 naar koraal 3 - [Meer](/help/sites-developing/dialog-conversion.md)informatie. |
