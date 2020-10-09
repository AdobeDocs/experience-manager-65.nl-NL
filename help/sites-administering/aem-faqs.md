---
title: Veelgestelde vragen AEM
seo-title: AEM 6.4 veelgestelde vragen
description: Gebruik deze veelgestelde vragen om algemene workflows of problemen in AEM te begrijpen, te configureren en op te lossen.
seo-description: Gebruik deze veelgestelde vragen om algemene workflows of problemen in AEM te begrijpen, te configureren en op te lossen.
uuid: 17d34923-f1ce-463b-8e9d-a713edcce51b
contentOwner: jsyal
discoiquuid: a3bb5695-6593-413d-9c2f-4c164e663b15
docset: aem65
translation-type: tm+mt
source-git-commit: 117208c634613559bb13556e12f094add70006e2
workflow-type: tm+mt
source-wordcount: '1356'
ht-degree: 0%

---


# Veelgestelde vragen AEM {#aem-faqs}

De antwoorden op sommige problemen met AEM problemen met probleemoplossing en configuratie kennen.

## Sites {#sites}

### Hoe vorm ik binair-minder distributie? {#how-do-i-configure-binary-less-distribution}

Binaire distributie zonder beperkingen wordt ondersteund voor implementaties via een gedeelde gegevensopslag en betreft agents die gebruikmaken van de exportfunctie van het Vault Distribution Package (factory PID: `org.apache.sling.distribution.serialization.impl.vlt.VaultDistributionPackageBuilderFactory`).

Met binair-geen toegelaten wijze, bevatten de verdeelde inhoudspakketten verwijzingen naar binaire getallen eerder dan de daadwerkelijke binaire getallen.

#### Hoe laat ik binair-minder distributie toe? {#how-do-i-enable-binary-less-distribution}

Om binair-minder distributie toe te laten, stel met een gedeelde blob opslag op.
Controleer het `useBinaryReferences` bezit in de configuratie OSGI met fabriek PID ( `org.apache.sling.distribution.serialization.impl.vlt.VaultDistributionPackageBuilderFactory`*)* die uw agent gebruikt.

#### Hoe kan ik de foutenmeldingen aanpassen terwijl het navigeren van paginahiërarchie in AEM plaatsenconsole? {#how-can-i-customize-the-error-messages-while-navigating-page-hierarchy-in-aem-sites-console}

Controleer het deelvenster Netwerk (van de Chrome-browser) waar een persoonlijke setup (JS) niet is geminiateerd.

Bekijk de `Initiator` kolom om te bepalen wat de initiatiefnemer van een verzoek was. Het verstrekt de dossiers en de lijnaantallen van waar de AJAX vraag wordt gemaakt. Later kunt u de functie voor foutafhandeling overtrekken en het foutbericht naar wens wijzigen.

#### Hoe te om toestemmingen toe te laten terwijl het creëren van het Exemplaar van de Taal voor tevreden-Auteurs in AEM? {#how-to-enable-permissions-while-creating-language-copy-for-content-authors-in-aem}

Voor het maken van een functie voor het kopiëren van talen hebben inhoudsauteurs machtigingen op hun `/content/projects` locatie nodig.

Als de auteurs ook projecten moeten beheren, moet u de auteur aan de `project-administrators` groep toevoegen.

#### Hoe te om het formaat te veranderen terwijl het creëren van het Exemplaar van de Taal voor een project? {#how-to-change-the-format-while-creating-language-copy-for-a-project}

Creeer een taalwortel en taalexemplaar binnen de wortel, alvorens een vertaalproject tot stand te brengen.

Maak bijvoorbeeld een hoofdmap van een taal `/content/geometrixx` met de naam `fr_LU` (en een titel als Frans (Luxemburg)). Maak vervolgens een taalkopie van de pagina in het venster Referenties en navigeer naar de `Create structure only` optie in `Create & Translate`. Tot slot creeer een vertaalproject en voeg dan de taalexemplaar aan de vertaalbaan toe.

Raadpleeg de volgende aanvullende bronnen voor meer informatie:

* [Inhoud voorbereiden voor vertaling](/help/sites-administering/tc-prep.md)
* [Vertaalprojecten beheren](/help/sites-administering/tc-manage.md)

#### Hoe te om AEM mogelijkheden zoals, login pogingen en ACL of toestemmingsveranderingen te controleren? {#how-to-audit-aem-capabilities-such-as-login-attempts-and-acl-or-permission-changes}

AEM heeft de capaciteit geïntroduceerd om administratieve veranderingen voor betere het oplossen van problemen en controle te registreren. Standaard wordt de informatie in het `error.log` bestand aangemeld. Om controle gemakkelijker te maken, adviseert men dat zij aan een afzonderlijk logboekdossier worden opnieuw gericht.
Om de output aan een afzonderlijk logboekdossier om te leiden, zie [hoe te de verrichtingen van het gebruikersbeheer in AEM](/help/sites-administering/audit-user-management-operations.md)controleren.

#### Hoe te om SSL door gebrek toe te laten? {#how-to-enable-ssl-by-default}

Adobe Experience Manager (AEM) 6.4 wordt geleverd met de SSL-wizard en biedt een gebruikersinterface voor het configureren van Jetty- en Granite Jetty SSL-ondersteuning.

Als u standaard SSL wilt inschakelen, raadpleegt u [standaard](/help/sites-administering/ssl-by-default.md)SSL.

#### Wat is de aanbevolen architectuur wanneer de Diensten van de Inhoud van AEM van een mobiele app, ideaal React Inheems gebruikt? {#what-is-the-recommended-architecture-when-using-aem-s-content-services-from-a-mobile-app-ideally-react-native}

De diensten van de Inhoud zijn gebaseerd op de het Verdelen Modellen en de AEM ontwikkelaars moeten een het Verdelen Model pojo voor elke component verstrekken die wordt uitgevoerd.

Om te begrijpen hoe te om AEM inhoudsdiensten van een React toepassing te verbruiken, zie [Begonnen met de AEM Zelfstudie van de Diensten](https://helpx.adobe.com/experience-manager/kt/sites/using/content-services-tutorial-use.html) van de Inhoud.

Ook, als de ontwikkelaars een boom van componenten willen uitvoeren kunnen zij `ComponentExporter` en `ContainerExporter` `ModelFactory` interfaces ook uitvoeren evenals gebruiken om over de kindcomponenten te herhalen en hun modelvertegenwoordiging terug te keren. Zie de volgende bronnen:

[1] - [Adobe-Marketing-Cloud/aem-core-wcm-componenten](https://github.com/Adobe-Marketing-Cloud/aem-core-wcm-components/blob/master/bundles/core/src/main/java/com/adobe/cq/wcm/core/components/internal/models/v1/PageImpl.java#L245)

[2] [Apache Sling: Verkoopmodellen](https://sling.apache.org/documentation/bundles/models.html)

#### Hoe te om AEM 6.4 enquête pop-up onbruikbaar te maken? {#how-to-disable-aem-survey-pop-up}

U kunt in de inzameling van gebruiksstatistieken door of Touch UI of de Console van het Web te gebruiken kiezen. Voor gedetailleerde instructies, zie [Opting in de inzameling](/help/sites-deploying/opt-in-aggregated-usage-statistics.md)van de samengevoegde gebruiksstatistieken.

#### Is er een goede bron die de belangrijkste eigenschappen voor bevordering aan AEM 6.4 benadrukt? {#is-there-a-good-resource-that-highlights-the-key-features-for-upgrading-to-aem}

Raadpleeg de [Redenen voor upgrade-AEM](https://helpx.adobe.com/experience-manager/kt/platform-repository/using/upgrade-aem-article-understand.html) die een overzicht geven van de belangrijkste functies op hoog niveau voor klanten die een upgrade naar de nieuwste versie van Adobe Experience Manager overwegen.

## Assets {#assets}

### Waarom wordt de middelenworkflow zichzelf herhaald tijdens het uploaden van MP4-bestanden (bijvoorbeeld met slepen en neerzetten)? {#why-the-assets-workflow-repeats-itself-while-uploading-mp-files-for-example-using-drag-and-drop-method}

Als de gebruiker, die de filmdossiers uploadt geen toestemmingen onder activaknoop schrapt, ontbreken de schrappingsbrokkenknopen en uploadt opnieuw begint.

#### Wat is het maximumaantal digitale activa dat met AEM 6.4 tegelijk kan worden geëxploiteerd? {#what-is-the-maximum-number-of-digital-assets-that-can-be-operated-with-aem-at-a-time}

Met Adobe Experience Manager (AEM) 6.5 kunt u momenteel maximaal 2 GB aan middelen tegelijk uploaden.

Zie voor meer informatie over het maximumaantal activa dat kan worden gebruikt met AEM 6.5 de [gids](/help/assets/assets-sizing-guide.md)voor middelengrootte.

#### Wat zijn de standaardmontages voor configuraties OTB terwijl het creëren van het Exemplaar van de Taal? {#what-are-the-default-settings-for-ootb-configurations-while-creating-language-copy}

Wanneer u taalkopieën maakt via een klassieke UI, worden Elementen niet onder de nieuwe taalhiërarchie geplaatst, maar vanuit de master taal gebruikt.

Wanneer u een taalkopie maakt via Touch UI (**References** -> **Update Language Copy**), wordt er een nieuwe DAM-map gemaakt onder de nieuwe taal en wordt er naar de nieuwe elementen verwezen.

Dit is de standaardinstelling voor OOTB-configuraties. U kunt **Vertaalpagina-elementen** = **Niet vertalen** in vertaalconfiguraties instellen.
Voor AEM 6.4: **Gereedschappen** > **Cloud Services** > **Cloudservices** voor vertaling.

#### Hoe te om een AEM component onbruikbaar te maken die exponentiële groei voor AEM SegmentStore (AEM 6.3.1.1) veroorzaakt? {#how-to-disable-an-aem-component-causing-exponential-growth-for-the-aem-segmentstore-aem}

U kunt de Disabler van de Component OSGi onbruikbaar maken. Om deze dienst te gebruiken, zie [Component Disabler](https://adobe-consulting-services.github.io/acs-aem-commons/features/osgi-disablers/component-disabler/index.html)OSGi.

Als tussenoplossing kunt u de component ook handmatig uitschakelen via de gebruikersinterface of via een `curl` opdracht (voorbeeld hieronder), na elke AEM herstart.

`curl -u admin:$(pass CQ_Admin) 'https://localhost:4502/system/console/components/com.day.cq.analytics.sitecatalyst.impl.importer.ReportImporter' --data 'action=disable'`

#### Hoe te om de Inzichten van Activa met AEM 6.5 instantie te vormen? {#how-to-configure-asset-insights-with-aem-instance}

Als u Asset Insights voor Experience Manager via Adobe Activation (DTM) wilt instellen en configureren, kunt u bekijken hoe u Asset Insights voor AEM Assets [kunt](https://docs.adobe.com/content/help/en/experience-manager-learn/assets/advanced/asset-insights-launch-tutorial.html)instellen.

#### Hoe te om admin consoles aan te passen? {#how-to-customize-admin-consoles}

AEM biedt verschillende mechanismen waarmee u de consoles en de functionaliteit voor het schrijven van pagina&#39;s van de ontwerpinstantie kunt aanpassen. Leer hoe te om een douaneconsole tot stand te brengen en een standaardmening voor een console aan te passen, gelieve te verwijzen naar het [Aanpassen van de Consoles](/help/sites-developing/customizing-consoles-touch.md).

#### Wat is het verschil tussen CoralUI 2 en CoralUI op 3-Gebaseerde componenten? {#what-is-the-difference-between-coralui-and-coralui-based-components}

Er wordt een nieuwe set Sling-componenten van Granite UI Foundation gemaakt voor Coral3 en deze bevindt zich onder [/libs/granite/ui/components/koral/foundation.](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/granite-ui/api/jcr_root/libs/granite/ui/components/coral/foundation/server.html) Er is één set voor op CoralUI 2 gebaseerde componenten en één set voor op CoralUI 3 gebaseerde componenten. De nieuwe set is niet alleen een kopie-plakbewerking van de oude set, maar wordt opgeschoond (bijvoorbeeld het stroomlijnen, verwijderen van vervangen functies). Daarom wordt aanbevolen dat een pagina alleen gebruik maakt van op CoralUI 3 gebaseerde of op CoralUI 2 gebaseerde sets.

Raadpleeg de [Migratiehandleiding naar CoralUI 3 voor meer informatie](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/granite-ui/api/jcr_root/libs/granite/ui/components/legacy/coral2/migration.html).

#### Hoe kan ik de zoekcomponent in AEM Assets aanpassen? {#how-to-customize-the-search-component-in-aem-assets}

Raadpleeg de handleiding voor [eenvoudige implementatie van zoekopdrachten voor meer informatie over zoekresultaten/rangschikking en verdere implementatiegegevens](https://helpx.adobe.com/experience-manager/kt/sites/using/search-tutorial-develop.html).

De Eenvoudige onderzoeksimplementatie is de materialen van het laboratorium van de Top van 2017 AEM Gedetailleerd Onderzoek.

#### Wat is het verschil tussen AEM Assets en AEM MediaLibrary? {#what-is-the-difference-between-aem-assets-and-aem-medialibrary}

AEM Assets is een toepassing op het AEM-Platform waarmee onze klanten hun digitale middelen (afbeeldingen, video&#39;s, documenten en audioclips) kunnen beheren in een op het web gebaseerde opslagplaats, terwijl AEM Mediabibliotheek een aangewezen onderdeel is van de AEM WCM-inhoudsruimte waar afbeeldingen en andere gedeelde bronnen worden opgeslagen.

Raadpleeg [AEM Assets vs. AEM MediaLibrary](/help/assets/medialibrary.md) voor meer informatie.

#### Is het mogelijk om insteekmodule voor WordPress te bouwen die een klant toestaat om tot de Plukker van Activa van Adobe toegang te hebben om beelden te selecteren? {#is-it-possible-to-build-plugin-for-wordpress-that-allows-a-customer-to-access-adobe-asset-picker-to-select-images}

Ja, een klant die WordPress gebruikt, kan de Adobe Asset Picker gebruiken om afbeeldingen van zijn AEM Assets-server te selecteren en toe te voegen aan advertenties op zijn WordPress-site.

Raadpleeg [Asset Selector](../assets/search-assets.md#assetpicker) voor meer informatie.

#### Is het mogelijk om de zoekfacetten in AEM Assets uit te breiden om extra voorspellingen toe te voegen? {#is-it-possible-to-extend-the-search-facets-in-aem-assets-to-add-additional-predicates}

Een bedrijfsbrede implementatie van Adobe Experience Manager (AEM) Assets heeft de capaciteit om vele activa op te slaan. U kunt voorspelden toevoegen aan het standaardformulier of een aangepast formulier gebruiken dat bepaalde facetten van uw keuze bevat.

Raadpleeg [Zoekfacetten](/help/assets/search-facets.md) voor meer informatie.
