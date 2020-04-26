---
title: Verouderde en verwijderde functies
description: Opmerkingen bij de release die specifiek betrekking hebben op vervangen en verwijderde functies in Adobe Experience Manager 6.5.
uuid: 81d9a064-e712-4eff-bd3b-6e15513a5435
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.5
discoiquuid: e8e2e01b-0117-48c3-86d8-609d29a147be
docset: aem65
translation-type: tm+mt
source-git-commit: 33fab976729baa09fdfd3725542f9e6bc7f37eeb

---


# Verouderde en verwijderde functies {#deprecated-and-removed-features}

Adobe evalueert voortdurend de productmogelijkheden, zodat oudere functies na verloop van tijd opnieuw kunnen worden uitgevonden of vervangen door modernere alternatieven om de algehele waarde van de klant te verbeteren, waarbij altijd zorgvuldig moet worden gekeken naar compatibiliteit met oudere versies.

Om de dreigende verwijdering/vervanging van de mogelijkheden van AEM mee te delen, zijn de volgende regels van toepassing:

1. Aankondiging van afkeuring komt voorop. Hoewel deze functie is afgekeurd, zijn de mogelijkheden nog steeds beschikbaar, maar worden ze niet verder uitgebreid.
1. Afgekeurde functies worden ten vroegste bij de volgende grote release verwijderd. De werkelijke streefdatum voor verwijdering wordt bekendgemaakt.

Dit proces biedt klanten minstens één releasecyclus om hun implementatie aan een nieuwe versie of opvolger van een vervangen capaciteit aan te passen, alvorens daadwerkelijke verwijdering.

## Verouderde functies {#deprecated-features}

Deze sectie bevat een lijst met functies en mogelijkheden die zijn gemarkeerd als verouderd in AEM 6.5. In het algemeen worden functies die in een toekomstige release verwijderd moeten worden, eerst vervangen, met een alternatief dat beschikbaar is.

Klanten wordt aangeraden na te gaan of zij in hun huidige implementatie gebruik maken van de functie/mogelijkheid en plannen te maken om hun implementatie te wijzigen en het geboden alternatief te gebruiken.

<table>
 <tbody>
  <tr>
   <td><b>Gebied</b></td>
   <td><b>Functie</b></td>
   <td><b>Vervanging</b></td>
  </tr>
  <tr>
   <td>Creative Cloud-integratie</td>
   <td><p><a href="/help/assets/aem-cc-folder-sharing-best-practices.md">Met AEM naar Creative Cloud voor het delen</a> van mappen is AEM 6.2 geïntroduceerd als een manier om creatieve gebruikers toegang te geven tot middelen van AEM, zodat ze deze kunnen openen in CC-toepassingen en nieuwe bestanden kunnen uploaden of wijzigingen in AEM kunnen opslaan. Een nieuwe functie die wordt vrijgegeven in de Creative Cloud-toepassing Adobe Asset Link, biedt een veel betere gebruikerservaring en krachtigere toegang tot middelen van AEM, rechtstreeks vanuit Photoshop, InDesign en Illustrator.</p> <p>Adobe is niet van plan verdere verbeteringen aan te brengen in de integratie van AEM voor het delen van Creative Cloud-mappen. Hoewel de functie in AEM is opgenomen, wordt klanten sterk aangeraden vervangende oplossingen te gebruiken.</p> </td>
   <td>Klanten wordt aangeraden over te schakelen op nieuwe mogelijkheden voor Creative Cloud-integratie, waaronder Adobe Asset Link of AEM-bureaubladtoepassing. Lees de beste praktijken <a href="/help/assets/aem-cc-integration-best-practices.md"></a> voor AEM- en Creative Cloud Integration voor meer informatie.</td>
  </tr>
  <tr>
   <td>Assets</td>
   <td>
    <ol>
     <li>AssetDownloadServer is standaard uitgeschakeld voor de publicatie-instanties. Zie de <a href="/help/sites-administering/security-checklist.md">AEM-beveiligingscontrolelijst</a>voor meer informatie.</li>
     <li>Als een gebruiker niet voldoende (lees en schrijf) toestemmingen op /content/dam/inzamelingen heeft, kan de gebruiker geen Inzameling tot stand brengen.</li>
    </ol> </td>
   <td>
    <ol>
     <li>Configuratie beschreven op <a href="/help/sites-administering/security-checklist.md">AEM Security checklist</a>.</li>
     <li>De instelling van de toegangscontrole van de gebruiker respecteren en de juiste machtigingen garanderen.<br /> </li>
    </ol> </td>
  </tr>
  <tr>
   <td>Adobe Zoeken en promoten</td>
   <td><p>De integratie met Adobe Search &amp; Promote is afgekeurd.</p> <p>Adobe is niet van plan verdere verbeteringen aan te brengen in de integratie van Zoeken en bevorderen. De integratie van Zoeken en bevorderen wordt nog steeds volledig ondersteund wanneer deze wordt vervangen.</p> </td>
   <td> </td>
  </tr>
  <tr>
   <td>DTM-tagbeheer</td>
   <td>De integratie met DTM (Dynamic Tag Manager) is afgekeurd.</td>
   <td>Overschakelen naar Adobe Experience Platform Launch als tagmanager</td>
  </tr>
  <tr>
   <td>Adobe-doel</td>
   <td>Door de mogelijkheid voor AEM om verbinding te maken met de Adobe I/O-gebaseerde Adobe Target Standard API (Rest API) in AEM 6.5 toe te voegen aan de Adobe Target Classic API (XML) is de manier waarop Doel Classic API (XML) wordt gebruikt, afgekeurd.</td>
   <td><a href="https://helpx.adobe.com/experience-manager/kt/sites/using/aem-sites-target-standard-technical-video-understand.html">De integratie opnieuw configureren voor gebruik van de nieuwe API</a></td>
  </tr>
  <tr>
   <td>Adobe-doel</td>
   <td>Het gebruik van de op mbox.js gebaseerde integratie met Adobe Target in AEM is afgekeurd.</td>
   <td>Overschakelen op gebruik om 1.js</td>
  </tr>
  <tr>
   <td>Handel</td>
   <td><p><a href="https://github.com/adobe/commerce-cif-api" target="_blank">CIF REST</a> werd in 2018 verstrekt als een reeks microdiensten om integratie tussen AEM- en handelsmotoren mogelijk te maken.</p> <p>Nadat Adobe Magento medio 2018 had aangeschaft, besloot Adobe om twee redenen zijn aanpak te wijzigen: </p> <p><strong>1.</strong> Magento heeft zijn eigen reeks Handel APIs (REST en GraphQL) en het is geen goede praktijk om twee reeksen APIs te handhaven </p> <p><strong>2.</strong> Markttendensen wezen erop dat klanten zich op GraphQL richtten, omdat het een efficiëntere manier is om gegevens te vragen. In 2019 heeft Adobe het nieuwe Commerce Integration Framework uitgebracht met behulp van de GraphQL API's van Magento als bron van de waarheid.</p> <p>Adobe is niet van plan meer te investeren in CIF REST. De klanten worden sterk geadviseerd om de vervangingsoplossing te gebruiken.</p> </td>
   <td><p>Voor integratie AEM-Magento, schakelaar aan <a href="https://github.com/adobe/aem-cif-project-archetype" target="_blank">AEM CIF Archetype</a>, en de Componenten van de Kern van <a href="https://github.com/adobe/aem-core-cif-components" target="_blank">AEM CIF</a></p> <p>Heb een blik bij <a href="https://www.adobe.io/apis/experiencecloud/commerce-integration-framework/integrations.html#!AdobeDocs/commerce-cif-documentation/master/integrations/02-AEM-Magento.md" target="_blank">AEM en integratie Magento gebruikend het Kader</a> van de Integratie van de Handel voor meer informatie.</p> <p>Steun voor integratie van derden (andere dan Magento) met de nieuwe aanpak staat op onze routekaart.</p> </td>
  </tr>
  <tr>
   <td>Componenten (AEM-sites)</td>
   <td><p>Adobe is niet van plan om verdere verhogingen aan de meeste die Componenten van de Stichting te maken in /libs/foundation/components worden opgeslagen.</p> <p>Zoek de eigenschap <strong>cq:afgekeurd</strong> en <strong>cq:afgekeurdReason</strong> in de componentmap.</p> <p>AEM 6.5 heeft de inbegrepen Componenten van de Stichting, en de klanten die van vroegere versies bevorderen kunnen blijven gebruiken hen zoals is. Verder, blijven de Componenten van de Stichting volledig gesteund terwijl wordt afgekeurd. </p> </td>
   <td>De klanten worden geadviseerd om de Componenten van de Kern voor toekomstige projecten te gebruiken. Bestaande sites kunnen ongewijzigd blijven of met de <a href="https://github.com/adobe/aem-modernize-tools">AEM Modernize Tools Suite</a> de site vernieuwen en Core Components gebruiken.</td>
  </tr>
  <tr>
   <td>Componenten (AEM-sites)</td>
   <td>Componenten /libs/wcm/Designer/componenten van Design Importer zijn vanaf 6.5 gemarkeerd als afgekeurd. Adobe is niet van plan verdere verbeteringen aan te brengen in die implementatie van de ontwerpimportmodule.</td>
   <td>Adobe is van plan een alternatieve implementatie van het gebruiksgeval in toekomstige versies te bieden.</td>
  </tr>
  <tr>
   <td>Componenten (AEM-formulieren)</td>
   <td><p>Met de stap Handtekening kunnen gebruikers een adaptief formulier verifiëren en ondertekenen. In eerdere versies kon in de handtekeningstap zowel de Adobe-componenten Ondertekenen als Scripthandtekening worden gebruikt als handtekeningvelden. In AEM 6.5-formulieren is de ondertekeningservaring op basis van een scripthandtekening afgekeurd.</p> </td>
   <td>
    <ul>
     <li>Als u een nieuwe installatie hebt uitgevoerd:
      <ul>
       <li>Gebruik de ondertekeningservaring op basis van Adobe-handtekeningen in een adaptieve vorm.</li>
       <li>Gebruik de stand-alone component voor scriptondertekening in een adaptieve vorm, interactieve communicatie en HTML5 Forms.</li>
      </ul> </li>
     <li>Als u een upgrade hebt uitgevoerd van een vorige versie naar AEM 6.5 Forms:<br />
      <ul>
       <li>Ga door met het gebruik van de ondertekeningservaring op basis van Krabbelhandtekeningen in Handtekeningstap voor formulieren die de functie al gebruiken.<br /> </li>
       <li>Wanneer u een formulier maakt, gebruikt u de stand-alone component voor scriptondertekening of de ondertekeningservaring op basis van Adobe-handtekeningen in een stap Handtekening. </li>
      </ul> </li>
    </ul> <p> </p> <p> </p> </td>
  </tr>
  <tr>
   <td>Stichting</td>
   <td><p>Framework Granite Offloading</p> <p>Adobe is niet van plan het offloading-framework, dat in 5.6.1 is geïntroduceerd, verder te verbeteren om de verwerking van bedrijfsmiddelen extern te maken. </p> </td>
   <td>Adobe werkt aan een 'cloud-native offloading'-framework van de volgende generatie.</td>
  </tr>
  <tr>
   <td>Ontwikkelaars</td>
   <td><p>Hobbes.js</p> <p>Adobe is niet van plan het testframework voor de gebruikersinterface hobbes.js verder te verbeteren.</p> </td>
   <td>Adobe raadt klanten aan seleniumautomatisering te gebruiken.</td>
  </tr>
  <tr>
   <td>Ontwikkelaars</td>
   <td><p>jQuery UI-clientbibliotheek</p> <p>Adobe is niet van plan de jQuery UI-clientbibliotheek die als onderdeel van de distributie wordt verzonden, verder te onderhouden en bij te werken (QuickStart)</p> </td>
   <td>Adobe raadt klanten aan die nog jQuery-gebruikersinterface voor hun code nodig hebben om deze aan hun projectcodebasis toe te voegen.</td>
  </tr>
  <tr>
   <td>Ontwikkelaars</td>
   <td><p>jQuery Animation-clientbibliotheek (granite.jquery.animation)</p> <p>Adobe is niet van plan de jQuery Animation-clientbibliotheek die als onderdeel van de distributie wordt verzonden, verder te onderhouden en bij te werken (QuickStart)</p> </td>
   <td>Adobe raadt klanten aan die nog jQuery-animaties nodig hebben voor hun code, deze toe te voegen aan hun projectcodebasis.</td>
  </tr>
  <tr>
   <td>Ontwikkelaars</td>
   <td><p>Handlebars clientbibliotheek</p> <p>Adobe is niet van plan de clientbibliotheek van de Handlebar die als onderdeel van de distributie wordt verzonden, verder te onderhouden en bij te werken (QuickStart)</p> </td>
   <td>Adobe raadt klanten aan die nog steeds Handlebars voor hun code nodig hebben om deze aan hun projectcodebasis toe te voegen.</td>
  </tr>
  <tr>
   <td>Ontwikkelaars</td>
   <td><p>Lawnstoel-clientbibliotheek</p> <p>Adobe is niet van plan de clientbibliotheek van Lawnstoel die als onderdeel van de distributie wordt verzonden, verder te onderhouden en bij te werken (QuickStart)</p> </td>
   <td>Adobe raadt klanten die nog steeds een Lawnstoel-code nodig hebben aan om deze code toe te voegen aan hun projectcodebasis.</td>
  </tr>
  <tr>
   <td>Ontwikkelaars</td>
   <td><p>Granite.Sling.js clientbibliotheek</p> <p>Adobe is niet van plan de clientbibliotheek Granite.Sling.js die wordt verzonden als onderdeel van de distributie, verder te verbeteren (QuickStart)</p> </td>
   <td>Adobe raadt klanten aan die op de mogelijkheid van de bibliotheek vertrouwen om hun code te vernieuwen om deze niet meer te gebruiken.</td>
  </tr>
  <tr>
   <td>Ontwikkelaars</td>
   <td>JavaScript-clientbibliotheken comprimeren/beperken met YUI. Adobe is niet van plan de YUI-bibliotheek verder bij te werken. Tot en met AEM 6.4 was YUI standaard ingesteld op het minimaliseren van JavaScript met de optie om over te schakelen op Google Closure Compiler (GCC). Vanaf AEM 6.5 is GCC standaard.</td>
   <td>Adobe raadt klanten aan een upgrade naar AEM 6.5 uit te voeren om over te schakelen naar GCC voor hun implementatie</td>
  </tr>
  <tr>
   <td>Ontwikkelaars</td>
   <td><p>Klassieke UI Dialog Editor in CRXDE-lijst</p> <p>Adobe is niet van plan om de Klassieke Redacteur van de Dialoog UI verder te verbeteren die als deel van de distributie (QuickStart) wordt verscheept</p> </td>
   <td> </td>
  </tr>
  <tr>
   <td>Formulieren</td>
   <td><p>Integratie van AEM-formulieren met AEM Mobile&lt; is afgekeurd </p> </td>
   <td>Geen vervanging </td>
  </tr>
 </tbody>
</table>

## Verwijderde functies {#removed-features}

Deze sectie bevat een lijst met functies en mogelijkheden die zijn verwijderd uit AEM 6.5. In eerdere versies waren deze mogelijkheden gemarkeerd als afgekeurd.

| Gebied | Functie | Vervanging |
|--- |--- |--- |
| Activiteitenkaart voor analyse | De versie van de activiteitenkaart die in AEM is opgenomen. | Vanwege beveiligingswijzigingen in de API voor Adobe Analytics is het niet langer mogelijk de versie van Activity Map te gebruiken die in AEM is opgenomen. Gebruik de plug-in [ActivityMap van Adobe Analytics](https://docs.adobe.complugin /content/help/en/analytics/analyze/activity-map/getting-started/get-started-users/activitymap-install.html). |
| Integraties | De integratie ExactTarget is verwijderd uit de standaarddistributie (QuickStart) en het is niet meer beschikbaar. | Geen vervanging |
| Integraties | De integratie van de Salesforce-API is verwijderd uit de standaarddistributie (QuickStart) en is nu een extra pakket dat u kunt installeren vanuit PackageShare. | Functie is nog steeds beschikbaar. |
| Formulieren | De ondersteuning voor de Adobe Central Migration Bridge-service is verwijderd omdat het Adobe Central-product niet meer wordt ondersteund. | Geen vervanging |
| Formulieren | `com.adobe.fd.df.fdinternal.model.ConfigurationInstance` | Geen vervanging |
| Formulieren | `com.adobe.fd.ccm.channels.print.fdinternal.api.service.PrintDataTransformer` | Geen vervanging |
| Formulieren | Single-hop verbetering van S4 SP1 aan Vormen AEM 6.5 op JEE is niet beschikbaar | Zie de [beschikbare upgradepaden](../forms/using/upgrade.md) in de upgradedocumentatie van AEM Forms. |
| Formulieren | Ondersteuning voor clustering via UPD is verwijderd uit AEM Forms on JEE | U kunt slechts op TCP-Gebaseerde groepering in Vormen AEM op JEE gebruiken. Als u een UDP multicast server van een vorige versie aan Vormen AEM 5.5 op JEE bevordert, voer handconfiguraties uit om op TCP gebaseerde gemfire zich het groeperen over te schakelen. Zie [Upgrade naar AEM 6.5-formulieren op JEE voor gedetailleerde instructies](../forms/using/upgrade-forms-jee.md) |
| Ontwikkelaars | Firebug Lite is verwijderd uit de standaarddistributie (QuickStart) | De ingebouwde browserconsoles voor ontwikkelaars gebruiken |
| Ontwikkelaars | Verwijder `customJavaScriptPath` ondersteuning in HTML Client Library Manager. | Geen vervanging |
| Assets | De functie voor het offloaden van middelen is verwijderd uit AEM 6.5 | Geen vervanging |
| Cache | `system/console/slingjsp` is verwijderd, is niet meer beschikbaar in AEM 6.5. | Klassen en de cache wordt iets opgeslagen onder de bundel FileSystem ClassLoader van Apache Sling Commons. U kunt het bundelnummer controleren in de AEM-webconsole en de cachemap rechtstreeks uit het bestandssysteem (`crx-quickstart/launchpad/felix/bundle<ID>`) verwijderen. |

## Vooraankondiging voor volgende release {#pre-announcement-for-next-release}

Deze sectie wordt gebruikt om veranderingen in toekomstige versie vooraf aan te kondigen, die niet verouderd zijn, maar klanten zullen beïnvloeden. Deze worden verstrekt voor planningsdoeleinden.

| Gebied | Functie | Aankondiging |
|--- |--- |--- |
| Stichting | UI Framework | Adobe is van plan de Coral UI 2-componenten in 2019 te vervangen. Koraal UI 3 werd geïntroduceerd met AEM 6.2, en AEM 6.5 is volledig gebaseerd op Koraal 3. Adobe raadt klanten en partners die aangepaste UI&#39;s met Coral 2 hebben gemaakt aan om deze opnieuw te bemonsteren naar Coral 3. Adobe biedt een programma voor het converteren van de dialoogvensters Koraal 2 naar koraal 3 - [Meer](/help/sites-developing/dialog-conversion.md)informatie. |
