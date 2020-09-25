---
title: Code en aanpassingen bijwerken
seo-title: Code en aanpassingen bijwerken
description: Meer informatie over het upgraden van aangepaste code in AEM.
seo-description: Meer informatie over het upgraden van aangepaste code in AEM.
uuid: dec11ef0-bf85-4e4e-80ac-dcb94cc3c256
contentOwner: sarchiz
topic-tags: upgrading
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
discoiquuid: 59780112-6a9b-4de2-bf65-f026c8c74a31
docset: aem65
targetaudience: target-audience upgrader
translation-type: tm+mt
source-git-commit: a8ba56849f6bb9f0cf6571fc51f4b5cae71620e0
workflow-type: tm+mt
source-wordcount: '2201'
ht-degree: 0%

---


# Code en aanpassingen bijwerken{#upgrading-code-and-customizations}

Bij de planning van een upgrade moeten de volgende onderdelen van een implementatie worden onderzocht en aangepakt.

* [De basiscode bijwerken](#upgrade-code-base)
* [Uitlijnen met 6.5 Repository Structure](#align-repository-structure)
* [Aanpassingen AEM](#aem-customizations)
* [Testprocedure](#testing-procedure)

## Overzicht {#overview}

1. **Patroondetector** - Voer de patroondetector uit zoals beschreven in upgradeplanning en gedetailleerd beschreven in [deze pagina](/help/sites-deploying/pattern-detector.md) om een patroondetectorrapport te krijgen dat meer details bevat over gebieden die moeten worden behandeld naast de niet-beschikbare API&#39;s/bundels in de doelversie van AEM. Het rapport Patroondetectie moet u een indicatie geven van eventuele incompatibiliteiten in uw code. Als er geen is, is de implementatie al compatibel met 6.5, kunt u er nog steeds voor kiezen om nieuwe ontwikkeling uit te voeren voor het gebruik van 6.5-functionaliteit, maar hebt u deze niet nodig voor het onderhoud van de compatibiliteit. Als er incompatibiliteiten worden gemeld, kunt u kiezen om a) op verenigbaarheidwijze in werking te stellen en uw ontwikkeling voor nieuwe 6.5 eigenschappen of verenigbaarheid uit te stellen, b) besluit om ontwikkeling na verbetering te doen, en zich aan stap 2 te bewegen. Zie [Achterwaartse compatibiliteit in AEM 6.5](/help/sites-deploying/backward-compatibility.md) voor meer informatie.

1. **Ontwikkelen de Basis van de Code voor 6.5 ** - creeer een specifieke tak of bewaarplaats voor de codebasis voor de versie van het Doel. Gebruik info van Compatibiliteit vóór upgrade om gebieden met code te plannen die moeten worden bijgewerkt.
1. **Compileer met 6.5 Uber jar ** - werk code basis POMs aan punt aan 6.5 uber jar en compileer code tegen dit.
1. **Update AEM Aanpassingen*** - *Om het even welke aanpassingen of uitbreidingen aan AEM zouden moeten worden bijgewerkt/worden bevestigd om in 6.5 te werken en aan de 6.5 codebasis worden toegevoegd. Bevat UI Search Forms, Assets Customizations, alles wat gebruikmaakt van /mnt/overlay

1. **Implementeren in 6.5-omgeving** - Een schone versie van AEM 6.5 (Auteur + Publiceren) moet worden gebruikt in een Dev/QA-omgeving. De bijgewerkte codebasis en een representatieve steekproef van inhoud (van huidige productie) zouden moeten worden opgesteld.
1. **QA-validatie en opgeloste** problemen - QA moet de toepassing valideren op zowel auteur- als publicatieinstanties van 6.5. Alle gevonden fouten moeten worden gecorrigeerd en toegewezen aan de basis van de 6.5-code. Herhaal indien nodig de Dev-Cycle totdat alle bugs zijn opgelost.

Voordat u verdergaat met een upgrade, moet u beschikken over een stabiele basis voor toepassingscode die grondig is getest op basis van de doelversie van AEM. Op basis van opmerkingen die tijdens het testen zijn gemaakt, kunnen er manieren zijn om de aangepaste code te optimaliseren. Dit kan onder andere het vernieuwen van de code omvatten om te voorkomen dat de gegevensopslagruimte wordt doorgedraaid, aangepaste indexering om de zoekopdracht te optimaliseren, of het gebruik van niet-geordende knooppunten in onder andere JCR.

Naast de mogelijkheid om uw codebasis en aanpassingen bij te werken met de nieuwe AEM versie, helpt 6.5 ook om uw aanpassingen efficiënter te beheren met de functie Achterwaartse Verenigbaarheid zoals die op [deze pagina](/help/sites-deploying/backward-compatibility.md)wordt beschreven.

Zoals hierboven vermeld en in het diagram hieronder getoond, zal het runnen van de Detector [van het](/help/sites-deploying/pattern-detector.md) Patroon in de eerste stap u helpen de algemene ingewikkeldheid van de verbetering beoordelen en of u op verenigbaarheidswijze wilt lopen of uw aanpassingen bijwerken om alle nieuwe AEM 6.5 eigenschappen te gebruiken. Zie de pagina [Achterwaartse compatibiliteit in AEM 6.5](/help/sites-deploying/backward-compatibility.md) voor meer informatie.
[ ![opt_bijgesneden](assets/opt_cropped.png)](assets/upgrade-code-base-highlevel.png)

## De basiscode bijwerken {#upgrade-code-base}

### Creeer een Specifieke Tak voor Code 6.5 in de Controle van de Versie {#create-a-dedicated-branch-for-6.5-code-in-version-control}

Alle code en configuraties die voor uw AEM implementatie worden vereist, moeten worden beheerd met een of andere vorm van versiecontrole. Een specifieke tak in versiecontrole zou voor het beheren van om het even welke veranderingen nodig voor de codebasis in de doelversie van AEM moeten worden gecreeerd. Het iteratieve testen van de codebasis tegen de doelversie van AEM en verdere insectenmoeilijke situaties zullen in deze tak worden beheerd.

### De versie AEM Uber Jar bijwerken {#update-the-aem-uber-jar-version}

De AEM Uber jar omvat alle AEM APIs als één enkel gebiedsdeel in uw Geweven project `pom.xml`. Het is altijd aan te raden de Uber Jar op te nemen als één afhankelijkheid in plaats van individuele AEM API-afhankelijkheden op te nemen. Wanneer het bevorderen van de codebasis zou de versie van Uber Jar moeten worden veranderd om op de doelversie van AEM te richten. Als uw project op een versie van AEM vóór het bestaan van Uber Jar werd ontwikkeld zouden alle individuele AEM API gebiedsdelen moeten worden verwijderd en door één enkele opneming van Uber Jar voor de doelversie van AEM worden vervangen. De codebasis zou dan tegen de nieuwe versie van Uber Jar opnieuw moeten worden gecompileerd. Vervangen API&#39;s of methoden moeten worden bijgewerkt om compatibel te zijn met de doelversie van AEM.

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

Het gebruik van een administratieve zitting door `SlingRepository.loginAdministrative()` en `ResourceResolverFactory.getAdministrativeResourceResolver()` was vrij wijdverbreid in codebasis voorafgaand aan AEM 6.0. Deze methoden zijn om veiligheidsredenen afgekeurd, omdat ze te ruim zijn voor toegang. [In toekomstige versies van Verkopen worden deze methoden verwijderd](https://sling.apache.org/documentation/the-sling-engine/service-authentication.html#deprecation-of-administrative-authentication). Het wordt ten zeerste aangeraden om code te vervangen en in plaats daarvan servicegebruikers te gebruiken. Meer informatie over de Gebruikers van de Dienst en [hoe te om administratieve zittingen te elimineren kan hier](/help/sites-administering/security-service-users.md#how-to-phase-out=admin-sessions)worden gevonden.

### Vragen en eikindexen {#queries-and-oak-indexes}

Om het even welk gebruik van vragen in de codebasis moet grondig worden getest als deel van het bevorderen van de codebasis. Voor klanten die van Jackrabbit 2 (versies van AEM ouder dan 6.0) bevorderen is dit vooral belangrijk aangezien het Eak inhoud niet automatisch indexeert en de douaneindexen kunnen moeten worden gecreeerd. Als de bevordering van een versie van AEM 6.x uit de de indexdefinities van het Eak van de doos kan veranderd zijn en bestaande vragen kon beïnvloeden.

Er zijn verschillende gereedschappen beschikbaar voor het analyseren en inspecteren van queryprestaties:

* [AEM indexgereedschappen](/help/sites-deploying/queries-and-indexing.md)

* [Operationele diagnosetools - Query-prestaties](/help/sites-administering/operations-dashboard.md#diagnosis-tools)

* [Eik](https://oakutils.appspot.com/). Dit is een opensource hulpmiddel dat niet door Adobe wordt gehandhaafd.

### Klassieke UI Authoring {#classic-ui-authoring}

Klassieke UI-authoring is nog steeds beschikbaar in AEM 6.5, maar wordt afgekeurd. Meer informatie vindt u [hier](/help/release-notes/deprecated-removed-features.md#pre-announcement-for-next-release). Als uw toepassing momenteel op het Klassieke auteursmilieu van UI loopt, wordt het geadviseerd om aan AEM 6.5 te bevorderen en het gebruik van Klassieke UI voort te zetten. De migratie naar Touch UI kan dan als afzonderlijk project worden gepland dat over verscheidene ontwikkelingscycli wordt voltooid. Om Klassieke UI in AEM 6.5 te gebruiken zijn verscheidene configuraties OSGi nodig om aan de codebasis worden geëngageerd. Meer details over hoe te om dit te vormen kunnen [hier](/help/sites-administering/enable-classic-ui.md)worden gevonden.

## Uitlijnen met 6.5 Repository Structure {#align-repository-structure}

Om upgrades eenvoudiger te maken en ervoor te zorgen dat configuraties niet tijdens een upgrade worden overschreven, wordt de opslagplaats in 6.4 geherstructureerd om inhoud van configuratie te scheiden.

Daarom moet een aantal instellingen worden verplaatst om niet langer te verblijven, `/etc` zoals in het verleden het geval was geweest. Zie [Repository Reform in AEM 6.4](/help/sites-deploying/repository-restructuring.md)om de volledige reeks herstructureringsproblemen in de opslagplaats te beoordelen die in de bijgewerkte versie tot AEM 6.4 moeten worden herzien en opgenomen.

## Aanpassingen AEM  {#aem-customizations}

Alle aanpassingen aan de AEM ontwerpomgeving in de bronversie van AEM moeten worden geïdentificeerd. Nadat elke aanpassing is geïdentificeerd, wordt aanbevolen deze in versiebeheer op te slaan of er minimaal een back-up van te maken als onderdeel van een inhoudspakket. Alle aanpassingen moeten worden geïmplementeerd en gevalideerd in een QA- of Staging-omgeving met de doelversie van AEM voorafgaand aan een productieupgrade.

### Bedekkingen in het algemeen {#overlays-in-general}

Het is gebruikelijk om AEM uit de boxfunctionaliteit uit te breiden door knooppunten en/of bestanden onder /libs te bedekken met extra knooppunten onder /apps. Deze overlays moeten worden bijgehouden in versiebeheer en worden getest op basis van de doelversie van AEM. Als een bestand (JS, JSP, HTL) wordt overschreven, wordt aanbevolen om een opmerking te laten over de functionaliteit die is uitgebreid voor het testen van de regressie op de doelversie van AEM. Meer informatie over overlays vindt u [hier](/help/sites-developing/overlays.md). Hieronder vindt u instructies voor specifieke AEM-overlays.

### Aangepast zoeken in Forms bijwerken {#upgrading-custom-search-forms}

Aangepaste zoekfactoren vereisen na de upgrade enkele handmatige aanpassingen om goed te kunnen functioneren. Zie [Aangepaste zoekopdracht in Forms](/help/sites-deploying/upgrading-custom-search-forms.md)upgraden voor meer informatie.

### UI-aanpassingen voor middelen {#assets-ui-customizations}

>[!NOTE]
>
>Deze procedure is alleen vereist voor upgrades vanaf versies ouder dan AEM 6.2.

Voor de upgrade moeten instanties worden voorbereid die aangepaste middelenimplementaties hebben. Dit is nodig om ervoor te zorgen dat alle aangepaste inhoud compatibel is met de nieuwe 6.4-knooppuntstructuur.

U kunt aanpassingen aan de UI van Activa voorbereiden door het volgende te doen:

1. Voor de instantie die moet worden bevorderd, open CRXDE Lite door naar *https://server:port/crx/de/index.jsp te gaan*

1. Ga naar het volgende knooppunt:

   * `/apps/dam/content`

1. Wijzig de naam van het inhoudsknooppunt in **content_backup**. U kunt dit doen door met de rechtermuisknop op het verkennervenster links in het venster te klikken en Naam **wijzigen** te kiezen.

1. Nadat de naam van het knooppunt is gewijzigd, maakt u een nieuw knooppunt met de naam inhoud onder `/apps/dam` benoemde **inhoud** en stelt u het knooppunttype in op **sling:Folder**.

1. Verplaats alle onderliggende knooppunten van **content_backup** naar het nieuwe inhoudsknooppunt. U kunt dit doen door elke kindknoop in de ontdekkingsreiziger ruit met de rechtermuisknop aan te klikken en **Beweging** te selecteren.

1. Verwijder het knooppunt **content_backup** .

1. De bijgewerkte knopen onder `/apps/dam` met het correcte knooptype van `sling:Folder` zouden idealiter in versiecontrole moeten worden bewaard en met de codebasis of bij een minimum gesteund als inhoudspakket worden opgesteld.

### Element-id&#39;s genereren voor bestaande elementen {#generating-asset-ids-for-existing-assets}

Als u element-id&#39;s voor bestaande elementen wilt genereren, moet u de elementen upgraden wanneer u uw AEM-instantie upgradet naar AEM 6.5. Dit is nodig om de functie [Assets Insights](/help/assets/touch-ui-asset-insights.md)in te schakelen. Zie [Insluitcode](/help/assets/touch-ui-using-page-tracker.md#add-embed-code)toevoegen voor meer informatie.

Als u elementen wilt bijwerken, configureert u het pakket Id&#39;s van bijbehorende elementen in de JMX-console. Afhankelijk van het aantal elementen in de gegevensopslagruimte kan het lang duren `migrateAllAssets` . Onze interne tests schatten ruwweg een uur voor 125.000 activa op TarMK.

![1487758945977](assets/1487758945977.png)

Gebruik de `migrateAssetsAtPath` API als u id&#39;s van elementen nodig hebt voor een subset van uw gehele elementen.

Voor alle andere doeleinden gebruikt u de `migrateAllAssets()` API.

### InDesign Script-aanpassingen {#indesign-script-customizations}

Adobe raadt u aan aangepaste scripts op de `/apps/settings/dam/indesign/scripts` locatie te plaatsen. Meer informatie over InDesign Script-aanpassingen vindt u [hier](/help/assets/indesign.md#configuring-the-aem-assets-workflow).

### ContextHub-configuraties herstellen {#recovering-contexthub-configurations}

De configuraties van ContextHub worden beïnvloed door een verbetering. De instructies op hoe te om bestaande configuraties terug te krijgen ContextHub kunnen [hier](/help/sites-developing/ch-configuring.md#recovering-contexthub-configurations-after-upgrading)worden gevonden.

### Workflowaanpassingen {#workflow-customizations}

Het is gebruikelijk om wijzigingen uit de vakworkflows bij te werken om niet-benodigde functionaliteit toe te voegen of te verwijderen. Een algemene workflow die wordt aangepast, is de [!UICONTROL DAM Update Asset] workflow. Van alle workflows die vereist zijn voor een aangepaste implementatie, moet een back-up worden gemaakt en worden opgeslagen in versiebeheer, aangezien deze tijdens een upgrade kunnen worden overschreven.

### Bewerkbare sjablonen {#editable-templates}

>[!NOTE]
>
>Deze procedure is alleen vereist voor Sites-upgrades die Bewerkbare sjablonen uit AEM 6.2 gebruiken

De structuur voor bewerkbare sjablonen is gewijzigd tussen AEM 6.2 en 6.3. Als u een upgrade uitvoert vanaf 6.2 of eerder en als uw site-inhoud is samengesteld met bewerkbare sjablonen, moet u het gereedschap [Opruimen van knooppunten](https://github.com/Adobe-Marketing-Cloud/aem-sites-template-migration)reageren gebruiken. Het gereedschap moet **na** een upgrade worden uitgevoerd om de inhoud op te schonen. Deze moet zowel op Auteur- als op Publish-niveau worden uitgevoerd.

### Wijzigingen in CUG-implementatie {#cug-implementation-changes}

De implementatie van Gesloten Gebruikersgroepen is aanzienlijk gewijzigd om de beperkingen van prestaties en schaalbaarheid in eerdere versies van AEM aan te pakken. De vorige versie van CUG is afgekeurd in 6.3 en de nieuwe implementatie wordt alleen ondersteund in de aanraakinterface. Als u van 6.2 of eerder bevordert, dan kunnen de Instructies om aan de nieuwe implementatie van de CUG [hier](/help/sites-administering/closed-user-groups.md#upgradetoaem63)worden gevonden.

## Testprocedure {#testing-procedure}

Er moet een uitgebreid testplan worden opgesteld voor het testen van upgrades. Het testen van de geüpgraded codebasis en de toepassing zal eerst in lagere milieu&#39;s moeten worden gedaan. Eventuele fouten moeten op iteratieve wijze worden gecorrigeerd totdat de basis van de code stabiel is. Dit geldt alleen als omgevingen op een hoger niveau worden bijgewerkt.

### De upgradeprocedure testen {#testing-the-upgrade-procedure}

De verbeteringsprocedure zoals hier geschetst zou op Dev en milieu&#39;s QA zoals die in uw aangepast loopboek worden gedocumenteerd (zie de [Planning van Uw Verbetering](/help/sites-deploying/upgrade-planning.md)) moeten worden getest. De verbeteringsprocedure zou moeten worden herhaald tot alle stappen in het verbeteringsloopboek worden gedocumenteerd en het verbeteringsproces is vlot.

### Testgebieden voor de implementatie  {#implementation-test-areas-}

Hieronder vindt u een aantal belangrijke onderdelen van een AEM implementatie die onder uw testplan moeten vallen als de omgeving is bijgewerkt en de geüpgrade codebasis is geïmplementeerd.

<table>
 <tbody>
  <tr>
   <td><strong>Functioneel testgebied</strong></td>
   <td><strong>Beschrijving</strong></td>
  </tr>
  <tr>
   <td>Gepubliceerde sites</td>
   <td>De AEM-implementatie en de bijbehorende code op de publicatielaag<br /> testen via de verzender. Neem criteria op voor pagina-updates en<br /> cachevalidatie.</td>
  </tr>
  <tr>
   <td>Authoring</td>
   <td>Testen van de AEM implementatie en de bijbehorende code op de laag Auteur. Dit moet pagina, componentontwerp en dialoogvensters bevatten.</td>
  </tr>
  <tr>
   <td>Integratie met Marketing Cloud-oplossingen</td>
   <td>Integraties met producten als Analytics, DTM en Target valideren.</td>
  </tr>
  <tr>
   <td>Integratie met systemen van derden</td>
   <td>Integraties van derden moeten zowel op Auteur- als op Publish-niveau worden gevalideerd.</td>
  </tr>
  <tr>
   <td>Verificatie, beveiliging en machtigingen</td>
   <td>Eventuele verificatiemechanismen zoals LDAP/SAML moeten worden gevalideerd.<br /> Machtigingen en groepen moeten worden getest op zowel de laag Auteur als de laag Publiceren<br /> .</td>
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
   <td>Het testen van de lading zou op zowel auteur als Publish rijen moeten worden uitgevoerd die real-world scenario's simuleren.</td>
  </tr>
 </tbody>
</table>

### Testplan en resultaten document {#document-test-plan-and-results}

Er moet een testplan worden opgesteld dat de bovengenoemde testgebieden voor de implementatie bestrijkt. In veel gevallen is het zinvol om het testplan te scheiden van de taaklijsten Auteur en Publiceren. Dit testplan moet worden uitgevoerd in ontwikkelings-, QA- en Stage-omgevingen voordat de productieomgevingen worden bijgewerkt. Testresultaten en prestatiemetriek moeten in lagere omgevingen worden vastgelegd om vergelijkingen te kunnen maken bij het upgraden van de Stage- en Production-omgeving.
