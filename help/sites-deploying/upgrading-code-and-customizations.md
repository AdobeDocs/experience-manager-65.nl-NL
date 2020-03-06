---
title: Code en aanpassingen bijwerken
seo-title: Code en aanpassingen bijwerken
description: Meer weten over het bijwerken van aangepaste code in AEM?
seo-description: Meer weten over het bijwerken van aangepaste code in AEM?
uuid: dec11ef0-bf85-4e4e-80ac-dcb94cc3c256
contentOwner: sarchiz
topic-tags: upgrading
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
discoiquuid: 59780112-6a9b-4de2-bf65-f026c8c74a31
docset: aem65
targetaudience: target-audience upgrader
translation-type: tm+mt
source-git-commit: 5035c9630b5e861f4386e1b5ab4f4ae7a8d26149

---


# Code en aanpassingen bijwerken{#upgrading-code-and-customizations}

Bij het plannen van een verbetering moeten de volgende gebieden van een implementatie worden onderzocht en worden behandeld.

* [De codebasis bijwerken](#upgrade-code-base)
* [Uitlijnen met 6.5 Repositorstructuur](#align-repository-structure)
* [AEM-aanpassingen](#aem-customizations)
* [Testprocedure](#testing-procedure)

## Overzicht {#overview}

1. **Patroondetector** - Stel de Patroondetector in werking zoals beschreven in upgradeplanning en in detail beschreven in [deze pagina](/help/sites-deploying/pattern-detector.md) om een patroondetectorrapport te krijgen dat meer details bevat over gebieden die moeten worden behandeld naast de niet-beschikbare API&#39;s/bundels in de doelversie van AEM. Het rapport van de Opsporing van het Patroon zou u een aanwijzing van om het even welke onverenigbaarheden in uw code moeten geven, als er geen toen zijn uw plaatsing reeds 6.5 compatibel is, kunt u nog verkiezen om nieuwe ontwikkeling te doen voor het gebruiken van functionaliteit 6.5, maar u hebt het niet enkel voor het handhaven van verenigbaarheid nodig. Als er gemelde onverenigbaarheden zijn dan kunt u aan of a) Looppas op verenigbaarheidswijze verkiezen en uw ontwikkeling voor nieuwe 6.5 eigenschappen of verenigbaarheid uitstellen, b) besluit om ontwikkeling na verbetering te doen, en zich aan stap 2 te bewegen. Raadpleeg [Achterwaartse compatibiliteit in AEM 6.5](/help/sites-deploying/backward-compatibility.md) voor meer informatie.

1. **Ontwikkel de Basis van de Code voor 6.5 **- creeer een specifieke tak of bewaarplaats voor de codebasis voor de versie van het Doel. Info van het gebruik van Verenigbaarheid van de pre-Verbetering om gebieden van code te plannen om bij te werken.
1. **Compileer met 6.5 Uber jar ** - de basis POMs van de Update om aan 6.5 uber jar te richten en code tegen dit samen te stellen.
1. **AEM-aanpassingen*** bijwerken - *Eventuele aanpassingen of uitbreidingen van AEM moeten worden bijgewerkt/gevalideerd om in 6.5 te werken en aan de 6.5-codebasis worden toegevoegd. Omvat de Vormen van het Onderzoek UI, de Aanpassingen van Activa, om het even wat die /mnt/bekleding gebruiken

1. **Implementeren in 6.5-omgeving** - Een schoon geval van AEM 6.5 (Auteur + publiceren) moet in een ontwikkelings-/kwaliteitscontroleomgeving worden weergegeven. De bijgewerkte codebasis en een representatieve steekproef van inhoud (van huidige productie) zouden moeten worden opgesteld.
1. **De Bevestiging van QA en de moeilijke situatie** van de insect - QA zou de toepassing op zowel Auteur moeten bevestigen als instanties van 6.5 publiceren. Alle gevonden insecten moeten worden bevestigd en aan de 6.5 codebasis worden gecommitteerd. Herhaal Dev-Cycle zonodig tot alle insecten worden bevestigd.

Alvorens met een verbetering te werk te gaan zou u een stabiele basis van de toepassingscode moeten hebben die grondig tegen de doelversie van AEM is getest. Gebaseerd op observaties die in het testen worden gemaakt zouden er manieren kunnen zijn om de douanecode te optimaliseren. Dit zou het refactoring van de code kunnen omvatten vermijden overbrengend de bewaarplaats, douane het indexeren om onderzoek te optimaliseren, of gebruik van ongeordende knopen in JCR, onder andere.

Naast de optie om uw codebasis en aanpassingen te bevorderen om met de nieuwe versie te werken AEM, helpt 6.5 ook uw aanpassingen efficiënter beheren met de Achterwaartse eigenschap van de Verenigbaarheid zoals die op [deze pagina](/help/sites-deploying/backward-compatibility.md)wordt beschreven.

Zoals hierboven vermeld en aangetoond in het hieronder diagram, zal het runnen van de Detector [van het](/help/sites-deploying/pattern-detector.md) Patroon in de eerste stap u helpen de algemene ingewikkeldheid van de verbetering beoordelen en of u op verenigbaarheidswijze wilt lopen of uw aanpassingen bijwerken om alle nieuwe eigenschappen te gebruiken AEM 6.5. Zie de [Achterwaartse Verenigbaarheid in AEM 6.5](/help/sites-deploying/backward-compatibility.md) pagina voor meer details.
[ ![opt_cropped](assets/opt_cropped.png)](assets/upgrade-code-base-highlevel.png)

## De codebasis bijwerken {#upgrade-code-base}

### Creeer een Specifieke Tak voor 6.5 Code in de Controle van de Versie {#create-a-dedicated-branch-for-6.5-code-in-version-control}

Alle die code en configuraties voor uw implementatie worden vereist AEM zouden moeten worden beheerd gebruikend één of andere vorm van versiecontrole. Een specifieke tak in versiecontrole zou voor het beheren van om het even welke veranderingen moeten worden gecreeerd nodig voor de codebasis in de doelversie van AEM. Het internationale testen van de codebasis tegen de doelversie van AEM en verdere insectenmoeilijke situaties zullen in deze tak worden beheerd.

### De AEM Uber Jar-versie bijwerken {#update-the-aem-uber-jar-version}

De ingang AEM Uber omvat al AEM APIs als één enkel gebiedsdeel in uw Maven project `pom.xml`. Het is altijd een beste praktijk om de Jar van de Uber als één enkel gebiedsdeel te omvatten in plaats van het omvatten van individuele AEM API gebiedsdelen. Wanneer het bevorderen van de codebasis zou de versie van de Jar van de Uber moeten worden veranderd om aan de doelversie van AEM te richten. Als uw project op een versie van AEM voorafgaand aan het bestaan van Uber Jar werd ontwikkeld zouden alle individuele AEM API gebiedsdelen moeten worden verwijderd en door één enkele opneming van Uber Jar voor de doelversie van AEM worden vervangen. De codebasis zou dan tegen de nieuwe versie van Uber Jar opnieuw moeten worden samengesteld. Om het even welke afgekeurde APIs of methodes zouden moeten worden bijgewerkt om met de doelversie van AEM compatibel te zijn.

```
<dependency>
    <groupId>com.adobe.aem</groupId>
    <artifactId>uber-jar</artifactId>
    <version>6.5.0</version>
    <classifier>apis</classifier>
    <scope>provided</scope>
</dependency>
```

### Fase uit gebruik van de Oplossing van het Administratieve Middel {#phase-out-use-of-administrative-resource-resolver}

Het gebruik van een administratieve zitting door `SlingRepository.loginAdministrative()` en `ResourceResolverFactory.getAdministrativeResourceResolver()` was vrij gangbaar in codebases voorafgaand aan AEM 6.0. Deze methodes zijn afgekeurd om veiligheidsredenen aangezien zij te breed van een niveau van toegang geven. [In toekomstige versies van het Verdelen zullen deze methodes worden verwijderd](https://sling.apache.org/documentation/the-sling-engine/service-authentication.html#deprecation-of-administrative-authentication). Het wordt hoogst geadviseerd om om het even welke code te refactoreren om de Gebruikers van de Dienst in plaats daarvan te gebruiken. Meer informatie over de Gebruikers van de Dienst en [hoe te om administratieve zittingen uit te faseren kan hier]worden gevonden (/help/sites-administering/security-service-users.md#how om admin zittingen geleidelijk te elimineren).

### Vragen en eiken indexen {#queries-and-oak-indexes}

Om het even welk gebruik van vragen in de codebasis moet grondig worden getest als deel van het bevorderen van de codebasis. Voor klanten die van Jackrabbit 2 (versies van AEM ouder dan 6.0) bevorderen is dit vooral belangrijk aangezien Oak automatisch geen inhoud indexeert en de douaneindexen kunnen moeten worden gecreeerd. Als de bevordering van een versie AEM 6.x uit de de indexdefinities van het Eak van de doos kan veranderd zijn en bestaande vragen kon beïnvloeden.

Verscheidene hulpmiddelen voor hulpmiddelen om vraagprestaties te analyseren en te inspecteren zijn beschikbaar:

* [AEM-indextools](/help/sites-deploying/queries-and-indexing.md)

* [Operations Diagnostic Tools - Query Performance](/help/sites-administering/operations-dashboard.md#diagnosis-tools)

* [Oak Utils](https://oakutils.appspot.com/). Dit is een open bronhulpmiddel dat niet door Adobe wordt gehandhaafd.

### Klassieke UI-ontwerpfunctie {#classic-ui-authoring}

De klassieke creatie UI is nog beschikbaar in AEM 6.5 maar wordt afgekeurd. Meer informatie vindt u [hier](/help/release-notes/deprecated-removed-features.md#pre-announcement-for-next-release). Als uw toepassing momenteel op het Klassieke UI auteursmilieu loopt wordt het geadviseerd om aan AEM 6.5 te bevorderen en verder gebruikend Klassieke UI te blijven. De migratie aan Touch UI kan dan als afzonderlijk project worden gepland dat over verscheidene ontwikkelingscycli moet worden voltooid. om Klassieke UI in AEM 6.5 te gebruiken zijn verscheidene configuraties OSGi nodig om aan de codebasis worden begaan. Meer details over hoe te om dit te vormen kunnen [hier](/help/sites-administering/enable-classic-ui.md)worden gevonden.

## Uitlijnen met 6.5 Repositorstructuur {#align-repository-structure}

Om verbeteringen gemakkelijker te maken en ervoor te zorgen dat de configuraties niet tijdens een verbetering worden beschreven, wordt de bewaarplaats geherstructureerd in 6.4 om inhoud van configuratie te scheiden.

Daarom moet een aantal montages worden verplaatst naar niet meer verblijf onder `/etc` zoals in het verleden het geval was geweest. Om de volledige reeks problemen met betrekking tot de herstructurering van de opslagplaats te beoordelen, die in de bijgewerkte versie aan AEM 6.4 moeten worden beoordeeld en opgenomen, zie [Repository Restructuring in AEM 6.4](/help/sites-deploying/repository-restructuring.md).

## AEM-aanpassingen {#aem-customizations}

Alle aanpassingen aan de AEM-ontwerpomgeving in de bronversie van AEM moeten worden geïdentificeerd. Zodra geïdentificeerd, wordt het geadviseerd dat elke aanpassingen in versiecontrole of bij een minimum worden opgeslagen file als deel van een inhoudspakket. Alle aanpassingen zouden in een QA of het Opvoeren van een milieu moeten worden opgesteld en worden bevestigd dat de doelversie van AEM in werking stelt voorafgaand aan een productieverbetering.

### Algemene kosten {#overlays-in-general}

Het is een gemeenschappelijke praktijk om AEM uit de doosfunctionaliteit uit te breiden door knopen en/of dossiers onder /libs met extra knopen onder /apps te bedekken. Deze bekledingen zouden in versiecontrole moeten worden gevolgd en tegen de doelversie van AEM moeten worden getest. Als een dossier (of het JS, JSP, HTL) wordt overladen, adviseert men om een commentaar te verlaten op welke functionaliteit voor het gemakkelijkere regressietests op de doelversie van AEM is uitgebreid. Meer informatie over bekledingen in het algemeen is [hier](/help/sites-developing/overlays.md)te vinden. De instructies voor specifieke bekledingen van AEM zijn hieronder te vinden.

### De bevorderende Vormen van het Onderzoek van de Douane {#upgrading-custom-search-forms}

De Facets van het Onderzoek van de douane vereisen sommige handaanpassingen na de verbetering om behoorlijk te functioneren. Voor meer details, zie de Bevordering van de Vormen [](/help/sites-deploying/upgrading-custom-search-forms.md)van het Onderzoek van de Douane.

### Aanpassingen van elementen-UI {#assets-ui-customizations}

>[!NOTE]
>
>Deze procedure wordt vereist slechts voor verbeteringen van versies ouder dan AEM 6.2.

De instanties die aangepaste plaatsingen van Activa hebben moeten voor de verbetering worden voorbereid. Dit is nodig om ervoor te zorgen dat alle aangepaste inhoud compatibel is met de nieuwe 6.4 knoopstructuur.

U kunt aanpassingen aan de Activa UI voorbereiden door het volgende te doen:

1. Voor de instantie die moet worden bevorderd, open CRXDE Lite door naar *https://server:port/crx/de/index.jsp te gaan*

1. Ga naar de volgende node:

   * `/apps/dam/content`

1. Noem de inhoudsknoop aan **content_backup** anders. U kunt dit doen door de exploratorruit in de linkerkant van het venster met de rechtermuisknop te klikken en te kiezen **anders noemt**.

1. Zodra de knoop is anders genoemd, creeer een nieuwe knoop genoemd inhoud onder `/apps/dam` genoemde **inhoud** en plaats zijn knooptype aan **sling:Omslag**.

1. Verplaats alle kindknopen van **content_backup** naar de pas gecreëerde inhoudsknoop. U kunt dit doen door elke kindknoop in de exploratorruit met de rechtermuisknop aan te klikken en **Beweging** te selecteren.

1. Schrap de **content_backup** knoop.

1. De bijgewerkte knopen onder `/apps/dam` met het correcte knooptype van `sling:Folder` zouden idealiter in versiecontrole moeten worden bewaard en met de codebasis of bij een minimum gesteund als inhoudspakket worden opgesteld.

### Het genereren van ID&#39;s voor bestaande activa {#generating-asset-ids-for-existing-assets}

Om activa-IDs voor bestaande activa te produceren, bevorder de activa wanneer u uw AEM instantie bevordert om AEM 6.5 in werking te stellen. Dit is nodig om de functie [Activa-inzichten](/help/assets/touch-ui-asset-insights.md)mogelijk te maken. Voor meer details, zie [toevoegen bedt code](/help/assets/touch-ui-using-page-tracker.md#add-embed-code)in.

Om activa te bevorderen, vorm het Associate pakket van identiteitskaarts van Activa in de console JMX. Afhankelijk van het aantal activa in de bewaarplaats, `migrateAllAssets` kan een lange tijd vergen. Onze interne tests schatten ruwweg een uur voor 125.000 activa op TarMK.

![1487758945977](assets/1487758945977.png)

Als u activa IDs voor een ondergroep van uw volledige activa vereist, gebruik `migrateAssetsAtPath` API.

Voor alle andere doeleinden, gebruik `migrateAllAssets()` API.

### Aanpassingen in InDesign Script {#indesign-script-customizations}

Adobe adviseert zettend douanemanuscripten bij `/apps/settings/dam/indesign/scripts` plaats. Meer informatie over de aanpassingen van het Manuscript InDesign kan [hier](/help/assets/indesign.md#configuring-the-aem-assets-workflow)worden gevonden.

### Het terugkrijgen van Configuraties ContextHub {#recovering-contexthub-configurations}

De configuraties van ContextHub worden uitgevoerd door een verbetering. De instructies op hoe te om bestaande configuraties terug te krijgen ContextHub kunnen [hier](/help/sites-administering/contexthub-config.md#recovery ing contexthub configuraties na bevordering) worden gevonden.

### Workflowaanpassingen {#workflow-customizations}

Het is een gemeenschappelijke praktijk om zich uit de dooswerkschema&#39;s bij te werken wijzigen om niet-noodzakelijke functionaliteit toe te voegen of te verwijderen. Een gemeenschappelijk werkschema dat wordt aangepast is het werkschema van de Activa van de Update van DAM. Alle die werkschema&#39;s voor een douanetoepassing worden vereist zouden in versiecontrole moeten worden gesteund en worden opgeslagen aangezien zij tijdens een verbetering kunnen worden beschreven.

### Bewerkbare sjablonen {#editable-templates}

>[!NOTE]
>
>Deze procedure wordt vereist slechts voor de verbeteringen van Plaatsen die Malplaatjes Editable van AEM 6.2 gebruiken

De structuur voor malplaatjes Editable veranderde tussen AEM 6.2 en 6.3. Als u van 6.2 of vroeger bevordert en als uw plaatsinhoud gebruikend editable malplaatjes wordt gebouwd zult u het [Reagerende Hulpmiddel](https://github.com/Adobe-Marketing-Cloud/aem-sites-template-migration)van de Schoonmaak van Knopen moeten gebruiken. Het hulpmiddel moet **na** een verbetering lopen om inhoud schoon te maken. Het zal op zowel Auteur als Publish rijen moeten worden in werking gesteld.

### Wijzigingen in implementatie CUG {#cug-implementation-changes}

De implementatie van Gesloten Gebruikersgroepen is aanzienlijk gewijzigd om de beperkingen van prestaties en schaalbaarheid in eerdere versies van AEM aan te pakken. De vorige versie van CUG werd afgekeurd in 6.3 en de nieuwe implementatie wordt slechts gesteund in Touch UI. Als u van 6.2 of vroeger bevordert dan kunnen de Instructies om aan de nieuwe implementatie van de CUG te migreren [hier](/help/sites-administering/closed-user-groups.md#upgradetoaem63)worden gevonden.

## Testprocedure {#testing-procedure}

Er moet een uitgebreid testplan worden opgesteld voor het testen van upgrades. Het testen van de promotiecodebasis en de toepassing zullen eerst in lagere milieu&#39;s moeten worden gedaan. Om het even welke gevonden insecten zouden op een iteratieve manier moeten worden bevestigd tot de codebasis stabiel is, slechts dan zou de hogere niveaumilieu&#39;s moeten worden bevorderd.

### De upgradeprocedure testen {#testing-the-upgrade-procedure}

De verbeteringsprocedure zoals hier geschetst zou op de milieu&#39;s moeten worden getest Dev en QA zoals die in uw aangepast looppasboek worden gedocumenteerd (zie de [Planning van Uw Verbetering](/help/sites-deploying/upgrade-planning.md)). De verbeteringsprocedure zou moeten worden herhaald tot alle stappen in het boek van de verbeteringslooppas worden gedocumenteerd en het verbeteringsproces is vlot.

### Testgebieden voor de uitvoering {#implementation-test-areas-}

Hieronder zijn kritieke gebieden van om het even welke implementatie AEM die door uw testplan zou moeten worden behandeld zodra de milieu is bevorderd en de promotiecodebasis is opgesteld.

<table>
 <tbody>
  <tr>
   <td><strong>Functioneel testgebied</strong></td>
   <td><strong>Beschrijving</strong></td>
  </tr>
  <tr>
   <td>Gepubliceerde sites</td>
   <td>Het testen van de implementatie AEM en de bijbehorende code op publiceren rij<br /> door de verzender. De criteria voor paginaupdates en<br /> geheim voorgeheugenongeldigverklaring zouden moeten omvatten.</td>
  </tr>
  <tr>
   <td>Authoring</td>
   <td>Het testen van de implementatie AEM en bijbehorende code op de rij van de Auteur. Pagina-, componentcreatie- en dialoogvensters moeten bevatten.</td>
  </tr>
  <tr>
   <td>Integratie met oplossingen voor marketingcloud</td>
   <td>Bevestiging van integratie met producten zoals Analytics, DTM, en Doel.</td>
  </tr>
  <tr>
   <td>Integratie met systemen van andere leveranciers</td>
   <td>Om het even welke derdeintegraties zouden op zowel Auteur als Publish rijen moeten worden bevestigd.</td>
  </tr>
  <tr>
   <td>Authentificatie, Veiligheid en Toestemmingen</td>
   <td>Om het even welke authentificatiemechanismen zoals LDAP/SAML zouden moeten worden bevestigd.<br /> De toestemmingen en de groepen zouden op zowel Auteur als Publish<br /> rijen moeten worden getest.</td>
  </tr>
  <tr>
   <td>Vragen</td>
   <td>De indexen en de vragen van de douane zouden samen met vraagprestaties moeten worden getest.</td>
  </tr>
  <tr>
   <td>UI-aanpassingen</td>
   <td>Om het even welke uitbreidingen of aanpassingen aan AEM UI in het auteursmilieu.</td>
  </tr>
  <tr>
   <td>Workflows</td>
   <td>Aangepast en/of uit de workflows en functionaliteit van de doos.</td>
  </tr>
  <tr>
   <td>Prestatietests</td>
   <td>Het testen van de lading zou op zowel Auteur als Publish rijen moeten worden uitgevoerd die real-world scenario's simuleren.</td>
  </tr>
 </tbody>
</table>

### Plan en resultaten documenttest {#document-test-plan-and-results}

Er moet een testplan worden opgesteld dat de bovengenoemde testgebieden voor de uitvoering bestrijkt. In veel gevallen zal het steek houden om het testplan door Auteur te scheiden en taaklijsten te publiceren. Dit testplan zou op Dev, QA, en de milieu&#39;s van het Stadium voorafgaand aan de bevordering van de milieu&#39;s van de Productie moeten worden uitgevoerd. De resultaten van de test en de prestatiesmetriek zouden op lagere milieu&#39;s moeten worden gevangen om vergelijking te verstrekken wanneer het bevorderen van de milieu&#39;s van het Stadium en van de Productie.
