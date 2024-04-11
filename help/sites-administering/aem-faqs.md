---
title: Veelgestelde vragen AEM
description: Gebruik deze veelgestelde vragen om algemene workflows of problemen in AEM te begrijpen, te configureren en op te lossen.
exl-id: 182c464a-ff7a-467b-9eb5-8ffac335a87a
solution: Experience Manager, Experience Manager Sites
feature: Configuring
role: Admin
source-git-commit: eae057caed533ef16bb541b4ad41b8edd7aaa1c7
workflow-type: tm+mt
source-wordcount: '936'
ht-degree: 0%

---

# Veelgestelde vragen AEM {#aem-faqs}

De antwoorden op sommige problemen met AEM problemen met probleemoplossing en configuratie kennen.

## Sites {#sites}

### Hoe vorm ik binair-minder distributie? {#how-do-i-configure-binary-less-distribution}

Binaire distributie zonder beperkingen wordt ondersteund voor implementaties via een gedeelde gegevensopslag en betreft agents die gebruikmaken van de vault-based Distribution Package Exporter (factory PID: `org.apache.sling.distribution.serialization.impl.vlt.VaultDistributionPackageBuilderFactory`) pakketbuilder.

Met binair-geen toegelaten wijze, bevatten de verdeelde inhoudspakketten verwijzingen naar binaire getallen eerder dan de daadwerkelijke binaire getallen.

#### Hoe laat ik binair-minder distributie toe? {#how-do-i-enable-binary-less-distribution}

Om binair-minder distributie toe te laten, stel met een gedeelde blob opslag op.
Controleer de `useBinaryReferences` eigenschap in de OSGI-configuratie met de fabriek-PID ( `org.apache.sling.distribution.serialization.impl.vlt.VaultDistributionPackageBuilderFactory`*)* dat uw agent gebruikt.

#### Hoe te om toestemmingen toe te laten terwijl het creëren van het Exemplaar van de Taal voor tevreden-Auteurs in AEM? {#how-to-enable-permissions-while-creating-language-copy-for-content-authors-in-aem}

Voor het maken van een functie voor het kopiëren van talen hebben inhoudsauteurs machtigingen nodig op `/content/projects` locatie.

Als de auteurs ook projecten moeten beheren, moet u de auteur aan `projects-administrators` groep.

#### Hoe te om het formaat te veranderen terwijl het creëren van het Exemplaar van de Taal voor een project? {#how-to-change-the-format-while-creating-language-copy-for-a-project}

Creeer een taalwortel en taalexemplaar binnen de wortel, alvorens een vertaalproject tot stand te brengen.

U kunt bijvoorbeeld een hoofdmap maken op `/content/geometrixx` met naam als `fr_LU` (en de titel Frans (Luxemburg)). Maak vervolgens een taalkopie van de pagina in het venster Referenties en navigeer naar `Create structure only` optie in `Create & Translate`. Tot slot creeer een vertaalproject en voeg dan de taalexemplaar aan de vertaalbaan toe.

Zie de volgende aanvullende bronnen voor meer informatie:

* [Inhoud voorbereiden voor vertaling](/help/sites-administering/tc-prep.md)
* [Vertaalprojecten beheren](/help/sites-administering/tc-manage.md)

#### Hoe te om AEM mogelijkheden zoals, login pogingen en ACL of toestemmingsveranderingen te controleren? {#how-to-audit-aem-capabilities-such-as-login-attempts-and-acl-or-permission-changes}

AEM heeft de capaciteit geïntroduceerd om administratieve veranderingen voor betere het oplossen van problemen en controle te registreren. Standaard wordt de informatie aangemeld bij de `error.log` bestand. Om controle gemakkelijker te maken, adviseert men dat zij aan een afzonderlijk logboekdossier worden opnieuw gericht.
Als u de uitvoer wilt omleiden naar een afzonderlijk logbestand, raadpleegt u [Hoe kan ik gebruikersbeheerbewerkingen in AEM controleren?](/help/sites-administering/audit-user-management-operations.md).

#### Hoe te om SSL door gebrek toe te laten? {#how-to-enable-ssl-by-default}

Adobe Experience Manager (AEM) 6.4 wordt geleverd met de SSL-wizard en biedt een gebruikersinterface voor het configureren van Jetty- en Granite Jetty SSL-ondersteuning.

Ga als volgt te werk om SSL standaard in te schakelen [Standaard SSL](/help/sites-administering/ssl-by-default.md).

#### Wat is de aanbevolen architectuur wanneer u AEM Content Services van een mobiele app gebruikt, idealiter React Native? {#what-is-the-recommended-architecture-when-using-aem-s-content-services-from-a-mobile-app-ideally-react-native}

De diensten van de Inhoud zijn gebaseerd op de het Verdelen Modellen en de AEM ontwikkelaars moeten een het Verdelen Model pojo voor elke component verstrekken die wordt uitgevoerd.

Als u wilt begrijpen hoe AEM inhoudsservices van een React-toepassing kunnen worden gebruikt, raadpleegt u [Aan de slag met AEM Content Services](https://helpx.adobe.com/experience-manager/kt/sites/using/content-services-tutorial-use.html) zelfstudie.

Ook, als de ontwikkelaars een boom van componenten willen uitvoeren kunnen zij ook uitvoeren `ComponentExporter` en `ContainerExporter` interfaces en gebruiken `ModelFactory` om de onderliggende componenten te doorlopen en hun modelrepresentatie te retourneren. Zie de volgende bronnen:

[1] [Adobe-marketing-Cloud/aem-core-wcm-componenten](https://github.com/Adobe-Marketing-Cloud/aem-core-wcm-components/blob/master/bundles/core/src/main/java/com/adobe/cq/wcm/core/components/internal/models/v1/PageImpl.java#L245)

[2] [Apache Sling : verkoopmodellen](https://sling.apache.org/documentation/bundles/models.html)

#### Hoe te om AEM 6.4 enquête pop-up onbruikbaar te maken? {#how-to-disable-aem-survey-pop-up}

U kunt in de inzameling van gebruiksstatistieken door of Touch UI of de Console van het Web te gebruiken kiezen. Zie voor gedetailleerde instructies [Opteren in de verzameling van geaggregeerde gebruiksstatistieken](/help/sites-deploying/opt-in-aggregated-usage-statistics.md).

#### Is er een goede bron die de belangrijkste eigenschappen voor bevordering aan AEM 6.4 benadrukt? {#is-there-a-good-resource-that-highlights-the-key-features-for-upgrading-to-aem}

Zie [Redenen voor upgrade-AEM begrijpen](https://helpx.adobe.com/experience-manager/kt/platform-repository/using/upgrade-aem-article-understand.html) Hierin wordt een overzicht gegeven van de belangrijkste functies op hoog niveau voor klanten die een upgrade naar de nieuwste versie van Adobe Experience Manager overwegen.

## Assets {#assets}

### Waarom wordt de middelenworkflow zichzelf herhaald tijdens het uploaden van MP4-bestanden (bijvoorbeeld met slepen en neerzetten)? {#why-the-assets-workflow-repeats-itself-while-uploading-mp-files-for-example-using-drag-and-drop-method}

Als de gebruiker, die de filmdossiers uploadt geen toestemmingen onder activaknoop schrapt, ontbreken de schrappingsbrokkenknopen en uploadt opnieuw begint.

#### Wat zijn de standaardmontages voor uit-van-de-doos configuraties terwijl het creëren van het Exemplaar van de Taal? {#what-are-the-default-settings-for-ootb-configurations-while-creating-language-copy}

Wanneer u een taalkopie maakt via de aanraakinterface (**Verwijzingen** > **Taalkopie bijwerken**), wordt er een nieuwe DAM-map gemaakt onder de nieuwe taal en er wordt naar elementen verwezen.

Dit is standaard het plaatsen voor uit-van-de-doos configuraties. U kunt instellen **Pagina-elementen vertalen** = **Niet vertalen** in vertaalconfiguraties.
Voor AEM 6.4: **Gereedschappen** > **Cloud Servicen** > **Cloudservices voor vertaling**.

#### Hoe te om een AEM component onbruikbaar te maken die exponentiële groei voor AEM SegmentStore (AEM 6.3.1.1) veroorzaakt? {#how-to-disable-an-aem-component-causing-exponential-growth-for-the-aem-segmentstore-aem}

U kunt de Component onbruikbaar maken OSGi. Als u deze service wilt gebruiken, raadpleegt u [OSGi Component Disabler](https://adobe-consulting-services.github.io/acs-aem-commons/features/osgi-disablers/component-disabler/index.html).

Als tussenoplossing kunt u de component ook handmatig uitschakelen via de gebruikersinterface of via een `curl` (voorbeeld hieronder), na elke AEM opnieuw beginnen.

`curl -u admin:$(pass CQ_Admin) 'https://localhost:4502/system/console/components/com.day.cq.analytics.sitecatalyst.impl.importer.ReportImporter' --data 'action=disable'`

#### Hoe te om admin consoles aan te passen? {#how-to-customize-admin-consoles}

AEM biedt verschillende mechanismen waarmee u de consoles en de functionaliteit voor het schrijven van pagina&#39;s van de ontwerpinstantie kunt aanpassen. Zie voor meer informatie over het maken van een aangepaste console en het aanpassen van een standaardweergave voor een console [De consoles aanpassen](/help/sites-developing/customizing-consoles-touch.md).

#### Wat is het verschil tussen CoralUI 2 en CoralUI op 3-Gebaseerde componenten? {#what-is-the-difference-between-coralui-and-coralui-based-components}

Een nieuwe reeks het Verdelen componenten van de Stichting van Granite UI wordt gecreeerd voor Coral3 en onder gevestigd [/libs/granite/ui/components/koral/foundation.](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/granite-ui/api/jcr_root/libs/granite/ui/components/coral/foundation/server.html) Er is één set voor op CoralUI 2 gebaseerde componenten en één set voor op CoralUI 3 gebaseerde componenten. De nieuwe set is niet alleen een kopie-plakbewerking van de oude set, maar wordt opgeschoond (bijvoorbeeld het stroomlijnen, verwijderen van vervangen functies). Daarom wordt aanbevolen dat een pagina alleen gebruik maakt van op CoralUI 3 gebaseerde of op CoralUI 2 gebaseerde sets.

Ga voor meer informatie naar [Migratiegids voor CoralUI 3](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/granite-ui/api/jcr_root/libs/granite/ui/components/legacy/coral2/migration.html).

#### Hoe kan ik de zoekcomponent in AEM Assets aanpassen? {#how-to-customize-the-search-component-in-aem-assets}

Ga voor meer informatie over zoekresultaten/beoordelingen en verdere implementatiegegevens naar [Eenvoudige gids voor implementatie van zoekopdrachten](https://helpx.adobe.com/experience-manager/kt/sites/using/search-tutorial-develop.html).

De Eenvoudige onderzoeksimplementatie is de materialen van het laboratorium van de Top van 2017 AEM Gedetailleerd Onderzoek.

#### Is het mogelijk om insteekmodule voor WordPress te bouwen die een klant toestaat om tot de Plukker van Activa van de Adobe toegang te hebben om beelden te selecteren? {#is-it-possible-to-build-plugin-for-wordpress-that-allows-a-customer-to-access-adobe-asset-picker-to-select-images}

Ja, een klant die WordPress gebruikt, kan de Adobe Asset Picker gebruiken om afbeeldingen van zijn AEM Assets-server te selecteren en toe te voegen aan advertenties op zijn WordPress-site.

Zie [Asset Selector](../assets/search-assets.md#assetpicker) voor meer informatie .
