---
title: Code en aanpassingen bijwerken
description: Meer informatie over het upgraden van code en aanpassingen in AEM.
contentOwner: sarchiz
topic-tags: upgrading
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
docset: aem65
targetaudience: target-audience upgrader
feature: Upgrading
exl-id: a36a310d-5943-4ff5-8ba9-50eaedda98c5
solution: Experience Manager, Experience Manager Sites
role: Admin
source-git-commit: f30decf0e32a520dcda04b89c5c1f5b67ab6e028
workflow-type: tm+mt
source-wordcount: '2140'
ht-degree: 0%

---

# Code en aanpassingen bijwerken{#upgrading-code-and-customizations}

Bij het plannen van een upgrade moeten de volgende onderdelen van een implementatie worden onderzocht en aangepakt.

* [De basiscode bijwerken](#upgrade-code-base)
* [Uitlijnen met 6.5 Repository Structure](#align-repository-structure)
* [AEM](#aem-customizations)
* [Testprocedure](#testing-procedure)

## Overzicht {#overview}

1. **de Detector van het Patroon** - stel de Detector van het Patroon zoals die in verbeterings planning wordt beschreven in werking, en beschreven in detail op [ die de Complexiteit van de Verbetering met de pagina van de Detector van het Patroon ](/help/sites-deploying/pattern-detector.md) beoordelen. Er wordt een patroondetectorrapport weergegeven met meer informatie over gebieden die moeten worden opgelost naast de niet-beschikbare API&#39;s/bundels in de doelversie van AEM. Het rapport Patroondetectie geeft een indicatie van incompatibiliteiten in de code. Als er geen installatie bestaat, is uw implementatie al compatibel met versie 6.5. U kunt er nog steeds voor kiezen om de 6.5-functionaliteit nieuw te ontwikkelen, maar dit is niet nodig voor het behoud van de compatibiliteit. Als er incompatibiliteiten worden gemeld, kunt u kiezen in de compatibiliteitsmodus en uw ontwikkeling uitstellen voor nieuwe 6.5-functies of compatibiliteit. U kunt ook besluiten om de ontwikkeling na de upgrade uit te voeren en naar stap 2 te gaan. Zie [ Achterwaartse Verenigbaarheid in AEM 6.5 ](/help/sites-deploying/backward-compatibility.md) voor meer details.

1. **Ontwikkelen de Basis van de Code voor 6.5 &#x200B;** - creeer een specifieke tak of bewaarplaats voor de codebasis voor de versie van het Doel. Gebruik info van Compatibiliteit vóór upgrade om gebieden met code te plannen die moeten worden bijgewerkt.
1. **Compileer met 6.5 Uber jar &#x200B;** - werk code basis POMs aan punt aan 6.5 uber jar en compileer code tegen het.
1. **Update AEM Aanpassingen*** - *Om het even welke aanpassingen of uitbreidingen aan AEM zouden moeten worden bijgewerkt/worden bevestigd om in 6.5 te werken en aan de 6.5 codebasis toe te voegen. Inclusief UI Search Forms, Assets Customizations, alles wat /mnt/overlay gebruikt

1. **stelt aan 6.5 Milieu** op - een schoon geval van AEM 6.5 (Auteur + Publish) zou in een milieu moeten worden omhoog Dev/QA. De bijgewerkte codebasis en een representatieve steekproef van inhoud (van huidige productie) zouden moeten worden opgesteld.
1. **QA- Bevestiging en Bug bevestigen** - QA zou de toepassing op zowel de Instantie van de Auteur als van Publish instanties van 6.5 moeten bevestigen. Alle gevonden fouten moeten worden gecorrigeerd en toegewezen aan de basis van de 6.5-code. Herhaal indien nodig de Dev-Cycle totdat alle bugs zijn opgelost.

Voordat u verdergaat met een upgrade, moet u beschikken over een stabiele basis voor toepassingscode die grondig is getest op basis van de doelversie van AEM. Op basis van opmerkingen die tijdens het testen zijn gemaakt, kunnen er manieren zijn om de aangepaste code te optimaliseren. Het kan bijvoorbeeld het vernieuwen van de code omvatten om te voorkomen dat de gegevensopslagruimte wordt doorgedraaid, aangepaste indexering om de zoekopdracht te optimaliseren of het gebruik van niet-geordende knooppunten in onder andere JCR.

Naast naar keuze het bevorderen van uw codebasis en aanpassingen om met de nieuwe AEM versie te werken, helpt 6.5 ook uw aanpassingen efficiënter met de Achterwaartse eigenschap van de Verenigbaarheid beheren zoals die op [ Achterwaartse Verenigbaarheid in AEM 6.5 ](/help/sites-deploying/backward-compatibility.md) wordt beschreven.

Zoals hierboven vermeld en in het hieronder diagram getoond, die de [ Detector van het Patroon ](/help/sites-deploying/pattern-detector.md) in de eerste stap in werking stellen kan u helpen de algemene ingewikkeldheid van de verbetering beoordelen. Het kan u ook helpen besluiten of u op verenigbaarheidswijze wilt lopen of uw aanpassingen bijwerken om alle nieuwe AEM 6.5 eigenschappen te gebruiken. Zie de [ Achterwaartse Verenigbaarheid in AEM 6.5 ](/help/sites-deploying/backward-compatibility.md) pagina voor meer details.
[![ opt_cropped ](assets/opt_cropped.png)](assets/upgrade-code-base-highlevel.png)

## De basiscode bijwerken {#upgrade-code-base}

### Een specifieke vertakking maken voor 6.5-code in Versiebeheer {#create-a-dedicated-branch-for-6.5-code-in-version-control}

Alle code en configuraties die voor uw AEM implementatie worden vereist, moeten worden beheerd met een of andere vorm van versiecontrole. Een specifieke tak in versiecontrole zou voor het beheren van om het even welke veranderingen nodig voor de codebasis in de doelversie van AEM moeten worden gecreeerd. Het iteratieve testen van de codebasis tegen de doelversie van AEM en verdere insectenmoeilijke situaties wordt beheerd in deze tak.

### De versie AEM Uber Jar bijwerken {#update-the-aem-uber-jar-version}

De AEM Uber jar omvat alle AEM APIs als één enkele gebiedsdeel in uw Maven project `pom.xml`. Het is altijd aan te raden de Uber Jar op te nemen als één afhankelijkheid in plaats van individuele AEM API-afhankelijkheden op te nemen. Wanneer het bevorderen van de codebasis, verander de versie van Uber Jar om aan de doelversie van AEM te richten. Als uw project op een versie van AEM vóór het bestaan van Uber Jar werd ontwikkeld, verwijder alle individuele AEM API gebiedsdelen. Vervang deze door één invoeging van Uber Jar voor de doelversie van AEM. Compileer de codebasis opnieuw tegen de nieuwe versie van Uber Jar. Vervangen API&#39;s of methoden bijwerken zodat deze compatibel zijn met de doelversie van AEM.

```
<dependency>
    <groupId>com.adobe.aem</groupId>
    <artifactId>uber-jar</artifactId>
    <version>6.5.0</version>
    <classifier>apis</classifier>
    <scope>provided</scope>
</dependency>
```

### Fase-out gebruik van de Administratieve Resolver van Middelen {#phase-out-use-of-administrative-resource-resolver}

Het gebruik van een beheersessie tot en met `SlingRepository.loginAdministrative()` en `ResourceResolverFactory.getAdministrativeResourceResolver()` vond plaats in de codebasis vóór AEM 6.0. Deze methoden zijn om veiligheidsredenen afgekeurd, omdat ze te ruim zijn voor toegang. [ in toekomstige versies van het Verdelen, zullen deze methodes worden verwijderd ](https://sling.apache.org/documentation/the-sling-engine/service-authentication.html#deprecation-of-administrative-authentication). Het wordt ten zeerste aangeraden om code te vervangen en in plaats daarvan servicegebruikers te gebruiken. Voor informatie over de Gebruikers van de Dienst en hoe te om administratieve zittingen uit te faseren zie [ Gebruikers van de Dienst in Adobe Experience Manager (AEM) ](/help/sites-administering/security-service-users.md#how-to-phase-out=admin-sessions).

### Vragen en Oak-indexen {#queries-and-oak-indexes}

Om het even welk gebruik van vragen in de codebasis moet grondig worden getest als deel van het bevorderen van de codebasis. Voor klanten die vanaf Jackrabbit 2 (versies van AEM ouder dan 6.0) een upgrade uitvoeren, is dit testen vooral belangrijk omdat Oak inhoud niet automatisch indexeert en er aangepaste indexen moeten worden gemaakt. Als de bevordering van een versie van AEM 6.x, uit de doosOak indexdefinities kan veranderd zijn en bestaande vragen kon beïnvloeden.

De volgende hulpmiddelen zijn beschikbaar voor het analyseren van en het inspecteren van vraagprestaties:

* [AEM indexgereedschappen](/help/sites-deploying/queries-and-indexing.md)

* [Operationele diagnosetools - Query-prestaties](/help/sites-administering/operations-dashboard.md#diagnosis-tools)

<!-- URL is 404 as of 04/24/23; commenting out * [Oak Utils](https://oakutils.appspot.com/). This is an open source tool that is not maintained by Adobe. -->

### Klassieke UI Authoring {#classic-ui-authoring}

Klassieke UI-authoring is nog steeds beschikbaar in AEM 6.5, maar wordt afgekeurd. Zie [ Vervangen en verwijderde eigenschappen ](/help/release-notes/deprecated-removed-features.md#pre-announcement-for-next-release) voor meer informatie. Als uw toepassing op het Klassieke UI auteursmilieu loopt, wordt het geadviseerd om aan AEM 6.5 te bevorderen en het gebruik van Klassieke UI voort te zetten. De migratie naar Touch UI kan dan als afzonderlijk project worden gepland om over verscheidene ontwikkelingscycli te voltooien. Om Klassieke UI in AEM 6.5 te gebruiken, moeten verscheidene configuraties OSGi aan de codebasis worden geëngageerd. Meer details op hoe te om de configuratie te doen kunnen onder [ worden gevonden toelatend Toegang tot Klassieke UI ](/help/sites-administering/enable-classic-ui.md).

## Uitlijnen met 6.5 Repository Structure {#align-repository-structure}

Om upgrades eenvoudiger te maken en ervoor te zorgen dat configuraties niet tijdens een upgrade worden overschreven, wordt de opslagplaats in 6.4 geherstructureerd om inhoud van configuratie te scheiden.

Daarom moeten verschillende instellingen worden verplaatst, zodat deze niet langer onder `/etc` staan, zoals in het verleden het geval was. Om de volledige reeks problemen van de bewaarplaatsherstructurering te herzien die in bijgewerkt aan AEM 6.4 moeten worden herzien en worden behandeld, zie [ Herstructurering van de Bewaarplaats in AEM 6.4 ](/help/sites-deploying/repository-restructuring.md).

## AEM  {#aem-customizations}

Alle aanpassingen aan de AEM ontwerpomgeving in de bronversie van AEM moeten worden geïdentificeerd. Nadat elke aanpassing is geïdentificeerd, wordt aanbevolen deze in versiebeheer op te slaan of er minimaal een back-up van te maken als onderdeel van een inhoudspakket. Alle aanpassingen moeten worden geïmplementeerd en gevalideerd in een QA- of Staging-omgeving waarin de doelversie van AEM wordt uitgevoerd vóór een productieupgrade.

### Bedekkingen in het algemeen {#overlays-in-general}

Het is gebruikelijk om AEM uit de boxfunctionaliteit uit te breiden door knooppunten en/of bestanden onder /libs te bedekken met extra knooppunten onder /apps. Deze overlays moeten worden bijgehouden in versiebeheer en worden getest op basis van de doelversie van AEM. Als een bestand (zoals JS, JSP, HTL) wordt overlapt, wordt u door de Adobe aangeraden een opmerking te achterlaten over de functionaliteit die is verbeterd om de regressietests in de doelversie van AEM te vereenvoudigen. Zie [ Bedekkingen ](/help/sites-developing/overlays.md) voor generische informatie. Hieronder vindt u instructies voor specifieke AEM-overlays.

### Aangepast zoeken in Forms bijwerken {#upgrading-custom-search-forms}

Aangepaste zoekfactoren vereisen enkele handmatige aanpassingen na de upgrade om correct te werken. Voor meer details, zie [ Bevorderend het Onderzoek van de Douane Forms ](/help/sites-deploying/upgrading-custom-search-forms.md).

### Assets UI-aanpassingen {#assets-ui-customizations}

>[!NOTE]
>
>Deze procedure is alleen vereist voor upgrades vanaf versies ouder dan AEM 6.2.

Exemplaren die aangepaste Assets-implementaties hebben, moeten worden voorbereid voor de upgrade. Deze actie is noodzakelijk om ervoor te zorgen dat alle aangepaste inhoud compatibel is met de nieuwe 6.4 knooppuntenstructuur.

U kunt aanpassingen aan Assets UI voorbereiden door het volgende te doen:

1. Voor de instantie die wordt bevorderd, open CRXDE Lite door *https://server:port/crx/de/index.jsp* te gaan

1. Ga naar het volgende knooppunt:

   * `/apps/dam/content`

1. Wijzig de naam van de inhoudsknoop aan **content_backup** door de ontdekkingsruit in de linkerkant van het venster met de rechtermuisknop aan te klikken, en **te kiezen anders noemt**.

1. Zodra de knoop anders is genoemd, creeer een knoop genoemd inhoud onder `/apps/dam` genoemd **inhoud** en plaats zijn knooptype aan **het slingeren:Omslag**.

1. Verplaats alle kindknopen van **content_backup** naar de pas gecreëerde inhoudsknoop door elke kindknoop in de ontdekkingsruit met de rechtermuisknop aan te klikken en **Beweging** te selecteren.

1. Schrap de **content_backup** knoop.

1. De bijgewerkte knooppunten onder `/apps/dam` met het juiste knooppunttype van `sling:Folder` moeten idealiter in versiecontrole worden opgeslagen en worden geïmplementeerd met de codebasis of minimaal worden opgeslagen als inhoudspakket.

### Element-id&#39;s genereren voor bestaande Assets {#generating-asset-ids-for-existing-assets}

Als u element-id&#39;s voor bestaande elementen wilt genereren, moet u de elementen upgraden wanneer u uw AEM-instantie upgradet naar AEM 6.5. Deze stap wordt vereist om de [ eigenschap van de Inzichten van Assets ](/help/assets/asset-insights.md) toe te laten. Voor meer details, zie [ inbedden code ](/help/assets/use-page-tracker.md#add-embed-code) toevoegen.

Als u elementen wilt bijwerken, configureert u het pakket Id&#39;s van bijbehorende elementen in de JMX-console. Afhankelijk van het aantal elementen in de gegevensopslagruimte kan `migrateAllAssets` lang duren. De interne tests van de Adobe schatten ongeveer een uur voor 125000 activa op TarMK.

![ 1487758945977 ](assets/1487758945977.png)

Gebruik de API `migrateAssetsAtPath` als u id&#39;s van elementen nodig hebt voor een subset van uw gehele elementen.

Voor alle andere doeleinden gebruikt u de `migrateAllAssets()` API.

### Scriptaanpassingen InDesign {#indesign-script-customizations}

Adobe raadt u aan aangepaste scripts op `/apps/settings/dam/indesign/scripts` -locatie te plaatsen. Meer informatie over de aanpassingen van het Manuscript van het InDesign kan onder [ worden gevonden integreer Adobe Experience Manager Assets met Adobe InDesign Server ](/help/assets/indesign.md#configuring-the-aem-assets-workflow).

### ContextHub-configuraties herstellen {#recovering-contexthub-configurations}

De configuraties van ContextHub worden beïnvloed door een verbetering. Zie [ het Vormen ContextHub ](/help/sites-developing/ch-configuring.md#recovering-contexthub-configurations-after-upgrading) voor instructies op hoe te om bestaande configuraties terug te krijgen ContextHub.

### Workflowaanpassingen {#workflow-customizations}

Het is gebruikelijk om werkstromen uit het vak te bewerken om overbodige functionaliteit toe te voegen of te verwijderen. Een algemene workflow die wordt aangepast, is de [!UICONTROL DAM Update Asset] -workflow. Van alle workflows die vereist zijn voor een aangepaste implementatie, moet een back-up worden gemaakt en worden opgeslagen in versiebeheer, aangezien deze tijdens een upgrade kunnen worden overschreven.

### Bewerkbare sjablonen {#editable-templates}

>[!NOTE]
>
>Deze procedure is alleen vereist voor Sites-upgrades die Bewerkbare sjablonen uit AEM 6.2 gebruiken

De structuur voor bewerkbare sjablonen is gewijzigd tussen AEM 6.2 en 6.3. Als u van 6.2 of vroeger bevordert, en als uw plaatsinhoud gebruikend editable malplaatjes wordt gebouwd, moet u het [ Responsieve Hulpmiddel van de Opruimen van Knoop gebruiken ](https://github.com/Adobe-Marketing-Cloud/aem-sites-template-migration). Het hulpmiddel moet **in werking stellen na** een verbetering om inhoud op te schonen. Voer de bewerking uit op zowel Auteur- als Publish-lagen.

### Wijzigingen in CUG-implementatie {#cug-implementation-changes}

De implementatie van Gesloten Gebruikersgroepen is aanzienlijk gewijzigd om de beperkingen van prestaties en schaalbaarheid in eerdere versies van AEM aan te pakken. De vorige versie van CUG is afgekeurd in 6.3 en de nieuwe implementatie wordt alleen ondersteund in de aanraakinterface.

## Testprocedure {#testing-procedure}

Er moet een uitgebreid testplan worden opgesteld voor het testen van upgrades. Het testen van de geüpgrade codebasis en de toepassing moet eerst in lagere omgevingen worden uitgevoerd. Eventuele fouten moeten op iteratieve wijze worden gecorrigeerd totdat de basis van de code stabiel is. Dit geldt alleen als omgevingen op een hoger niveau worden bijgewerkt.

### De upgradeprocedure testen {#testing-the-upgrade-procedure}

De verbeteringsprocedure zoals die hier wordt geschetst zou op Dev en milieu&#39;s QA zoals die in uw aangepast in werking gesteld boek worden gedocumenteerd (zie [ plannend Uw Verbetering ](/help/sites-deploying/upgrade-planning.md)). De verbeteringsprocedure zou moeten worden herhaald tot alle stappen in het verbeteringsloopboek worden gedocumenteerd en het verbeteringsproces is vlot.

### Testgebieden voor de implementatie  {#implementation-test-areas-}

Hieronder volgen enkele belangrijke gebieden van elke AEM implementatie die onder uw testplan moeten vallen zodra de omgeving is bijgewerkt en de geüpgrade codebasis is geïmplementeerd.

<table>
 <tbody>
  <tr>
   <td><strong>Functioneel testgebied</strong></td>
   <td><strong>Beschrijving</strong></td>
  </tr>
  <tr>
   <td>Gepubliceerde sites</td>
   <td>Het testen van de AEM implementatie en bijbehorende code op publiceren rij <br /> door Dispatcher. Neem criteria op voor pagina-updates en <br /> cachevalidatie.</td>
  </tr>
  <tr>
   <td>Authoring</td>
   <td>Testen van de AEM implementatie en de bijbehorende code op de laag Auteur. Dit moet pagina, componentontwerp en dialoogvensters bevatten.</td>
  </tr>
  <tr>
   <td>Integratie met Experience Cloud-oplossingen</td>
   <td>Integraties met producten als Analytics, DTM en Target valideren.</td>
  </tr>
  <tr>
   <td>Integraties met systemen van derden</td>
   <td>Valideer om het even welke derdeconcentraties op zowel Auteur als Publish niveaus.</td>
  </tr>
  <tr>
   <td>Verificatie, beveiliging en machtigingen</td>
   <td>Eventuele verificatiemechanismen zoals LDAP/SAML moeten worden gevalideerd.<br /> De toestemmingen en de groepen zouden op zowel Auteur als Publish <br /> lijsten moeten worden getest.</td>
  </tr>
  <tr>
   <td>Zoekopdrachten</td>
   <td>De indexen en de vragen van de douane zouden samen met vraagprestaties moeten worden getest.</td>
  </tr>
  <tr>
   <td>UI-aanpassingen</td>
   <td>Extensies of aanpassingen van de AEM-gebruikersinterface in de ontwerpomgeving.</td>
  </tr>
  <tr>
   <td>Workflows</td>
   <td>Aangepast en/of uit de vakworkflows en -functionaliteit.</td>
  </tr>
  <tr>
   <td>Prestatietesten</td>
   <td>Het testen van de lading zou op zowel auteur als Publish lagen moeten worden uitgevoerd die real-world scenario's simuleren.</td>
  </tr>
 </tbody>
</table>

### Testplan en resultaten document {#document-test-plan-and-results}

Er moet een testplan worden opgesteld dat de bovengenoemde testgebieden voor de implementatie bestrijkt. Het is vaak zinvol om het testplan te scheiden van de taaklijsten van Auteur en Publish. Dit testplan zou op Dev, QA, en de milieu&#39;s van het Stadium moeten worden uitgevoerd alvorens de milieu&#39;s van de Productie te bevorderen. Testresultaten en prestatiemetriek moeten in lagere omgevingen worden vastgelegd om vergelijkingen te kunnen maken bij het upgraden van de Stage- en Production-omgeving.
