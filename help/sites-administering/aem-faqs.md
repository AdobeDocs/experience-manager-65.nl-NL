---
title: Veelgestelde vragen AEM
seo-title: AEM 6.4 veelgestelde vragen
description: Gebruik deze veelgestelde vragen om algemene workflows of problemen in AEM te begrijpen, te configureren en op te lossen.
seo-description: Gebruik deze veelgestelde vragen om algemene workflows of problemen in AEM te begrijpen, te configureren en op te lossen.
uuid: 17d34923-f1ce-463b-8e9d-a713edcce51b
contentOwner: jsyal
discoiquuid: a3bb5695-6593-413d-9c2f-4c164e663b15
docset: aem65
exl-id: 182c464a-ff7a-467b-9eb5-8ffac335a87a
source-git-commit: 68c36d4e3a14567a4d115ee64a4474bcaf9aa386
workflow-type: tm+mt
source-wordcount: '1114'
ht-degree: 0%

---

# Veelgestelde vragen AEM {#aem-faqs}

De antwoorden op sommige problemen met AEM problemen met probleemoplossing en configuratie kennen.

## Sites {#sites}

### Hoe vorm ik binair-minder distributie? {#how-do-i-configure-binary-less-distribution}

Binaire distributie zonder beperkingen wordt ondersteund voor implementaties via een gedeelde gegevensopslag en betreft agents die gebruikmaken van de exportfunctie van het Vault Distribution Package (factory PID: `org.apache.sling.distribution.serialization.impl.vlt.VaultDistributionPackageBuilderFactory`) package builder.

Met binair-geen toegelaten wijze, bevatten de verdeelde inhoudspakketten verwijzingen naar binaire getallen eerder dan de daadwerkelijke binaire getallen.

#### Hoe laat ik binair-minder distributie toe? {#how-do-i-enable-binary-less-distribution}

Om binair-minder distributie toe te laten, stel met een gedeelde blob opslag op.
Controleer `useBinaryReferences` bezit in de configuratie OSGI met fabriek PID ( `org.apache.sling.distribution.serialization.impl.vlt.VaultDistributionPackageBuilderFactory`*)* die uw agent gebruikt.

#### Hoe kan ik de foutenmeldingen aanpassen terwijl het navigeren van paginahiërarchie in AEM plaatsenconsole? {#how-can-i-customize-the-error-messages-while-navigating-page-hierarchy-in-aem-sites-console}

Controleer het deelvenster Netwerk (van de Chrome-browser) waar een persoonlijke setup (JS) niet is geminiateerd.

Bekijk `Initiator` kolom om te bepalen wat de initiatiefnemer van een verzoek was. Het verstrekt de dossiers en de lijnaantallen van waar de AJAX vraag wordt gemaakt. Later kunt u de functie voor foutafhandeling overtrekken en het foutbericht naar wens wijzigen.

#### Hoe te om toestemmingen toe te laten terwijl het creëren van het Exemplaar van de Taal voor tevreden-Auteurs in AEM? {#how-to-enable-permissions-while-creating-language-copy-for-content-authors-in-aem}

Voor het maken van de functie voor het kopiëren van talen hebben inhoudsauteurs machtigingen nodig op de locatie `/content/projects`.

Als de auteurs ook projecten moeten beheren, dan moet de oplossing de auteur aan `project-administrators` groep toevoegen.

#### Hoe te om het formaat te veranderen terwijl het creëren van het Exemplaar van de Taal voor een project? {#how-to-change-the-format-while-creating-language-copy-for-a-project}

Creeer een taalwortel en taalexemplaar binnen de wortel, alvorens een vertaalproject tot stand te brengen.

Bijvoorbeeld:
Creeer een taalwortel bij `/content/geometrixx` met naam als `fr_LU` (en titel als Frans (Luxemburg)). Maak vervolgens een taalkopie van de pagina in het venster Referenties en navigeer naar de optie `Create structure only` in `Create & Translate`. Tot slot creeer een vertaalproject en voeg dan de taalexemplaar aan de vertaalbaan toe.

Raadpleeg de volgende aanvullende bronnen voor meer informatie:

* [Inhoud voorbereiden voor vertaling](/help/sites-administering/tc-prep.md)
* [Vertaalprojecten beheren](/help/sites-administering/tc-manage.md)

#### Hoe te om AEM mogelijkheden zoals, login pogingen en ACL of toestemmingsveranderingen te controleren? {#how-to-audit-aem-capabilities-such-as-login-attempts-and-acl-or-permission-changes}

AEM heeft de capaciteit geïntroduceerd om administratieve veranderingen voor betere het oplossen van problemen en controle te registreren. Standaard wordt de informatie in het bestand `error.log` aangemeld. Om controle gemakkelijker te maken, adviseert men dat zij aan een afzonderlijk logboekdossier worden opnieuw gericht.
Om de output aan een afzonderlijk logboekdossier om te leiden, zie [Hoe te de verrichtingen van het gebruikersbeheer in AEM](/help/sites-administering/audit-user-management-operations.md) controleren.

#### Hoe te om SSL door gebrek toe te laten? {#how-to-enable-ssl-by-default}

Adobe Experience Manager (AEM) 6.4 wordt geleverd met de SSL-wizard en biedt een gebruikersinterface voor het configureren van Jetty- en Granite Jetty SSL-ondersteuning.

Om SSL door gebrek toe te laten, zie [SSL door gebrek](/help/sites-administering/ssl-by-default.md).

#### Wat is de aanbevolen architectuur wanneer de Diensten van de Inhoud van AEM van een mobiele app, ideaal React Inheems gebruikt? {#what-is-the-recommended-architecture-when-using-aem-s-content-services-from-a-mobile-app-ideally-react-native}

De diensten van de Inhoud zijn gebaseerd op de het Verdelen Modellen en de AEM ontwikkelaars moeten een het Verdelen Model pojo voor elke component verstrekken die wordt uitgevoerd.

Zie [Aan de slag met AEM Content Services](https://helpx.adobe.com/experience-manager/kt/sites/using/content-services-tutorial-use.html) zelfstudie voor meer informatie over hoe u AEM inhoudsservices kunt gebruiken vanuit een React-toepassing.

Ook, als de ontwikkelaars een boom van componenten willen uitvoeren kunnen zij `ComponentExporter` en `ContainerExporter` interfaces ook uitvoeren evenals `ModelFactory` gebruiken om over de kindcomponenten te herhalen en hun modelvertegenwoordiging terug te keren. Zie de volgende bronnen:

[1] [Adobe-Marketing-Cloud/aem-core-wcm-componenten](https://github.com/Adobe-Marketing-Cloud/aem-core-wcm-components/blob/master/bundles/core/src/main/java/com/adobe/cq/wcm/core/components/internal/models/v1/PageImpl.java#L245)

[2] [Apache Sling: Verkoopmodellen](https://sling.apache.org/documentation/bundles/models.html)

#### Hoe te om AEM 6.4 enquête pop-up onbruikbaar te maken? {#how-to-disable-aem-survey-pop-up}

U kunt in de inzameling van gebruiksstatistieken door of Touch UI of de Console van het Web te gebruiken kiezen. Voor gedetailleerde instructies, zie [Opting in de inzameling van de samengevoegde gebruiksstatistieken](/help/sites-deploying/opt-in-aggregated-usage-statistics.md).

#### Is er een goede bron die de belangrijkste eigenschappen voor bevordering aan AEM 6.4 benadrukt? {#is-there-a-good-resource-that-highlights-the-key-features-for-upgrading-to-aem}

Raadpleeg [Redenen voor upgrade AEM](https://helpx.adobe.com/experience-manager/kt/platform-repository/using/upgrade-aem-article-understand.html) voor een overzicht van de belangrijkste functies op hoog niveau voor klanten die een upgrade naar de nieuwste versie van Adobe Experience Manager overwegen.

## Assets {#assets}

### Waarom wordt de middelenworkflow zichzelf herhaald tijdens het uploaden van MP4-bestanden (bijvoorbeeld met slepen en neerzetten)? {#why-the-assets-workflow-repeats-itself-while-uploading-mp-files-for-example-using-drag-and-drop-method}

Als de gebruiker, die de filmdossiers uploadt geen toestemmingen onder activaknoop schrapt, ontbreken de schrappingsbrokkenknopen en uploadt opnieuw begint.

#### Wat zijn de standaardmontages voor configuraties OTB terwijl het creëren van het Exemplaar van de Taal? {#what-are-the-default-settings-for-ootb-configurations-while-creating-language-copy}

Wanneer u een taalexemplaar door Touch UI (**References** -> **Update Language Copy**) creeert, wordt een nieuwe omslag DAM gecreeerd onder de nieuwe taal en de activa worden van daar van verwijzingen voorzien.

Dit is de standaardinstelling voor OOTB-configuraties. U kunt **Paginaelementen omzetten** = **Niet vertalen** in vertaalconfiguraties instellen.
Voor AEM 6.4 **Tools** > **Cloud Services** > **Translation Cloud services**.

#### Hoe te om een AEM component onbruikbaar te maken die exponentiële groei voor AEM SegmentStore (AEM 6.3.1.1) veroorzaakt? {#how-to-disable-an-aem-component-causing-exponential-growth-for-the-aem-segmentstore-aem}

U kunt de Disabler van de Component OSGi onbruikbaar maken. Zie [OSGi Component Disabler](https://adobe-consulting-services.github.io/acs-aem-commons/features/osgi-disablers/component-disabler/index.html) om deze service te gebruiken.

Als tussenoplossing kunt u de component ook handmatig uitschakelen via de gebruikersinterface of via een opdracht `curl` (voorbeeld hieronder), na elke AEM herstart.

`curl -u admin:$(pass CQ_Admin) 'https://localhost:4502/system/console/components/com.day.cq.analytics.sitecatalyst.impl.importer.ReportImporter' --data 'action=disable'`

#### Hoe te om admin consoles aan te passen? {#how-to-customize-admin-consoles}

AEM biedt verschillende mechanismen waarmee u de consoles en de functionaliteit voor het schrijven van pagina&#39;s van de ontwerpinstantie kunt aanpassen. Leer hoe te om een douaneconsole tot stand te brengen en een standaardmening voor een console aan te passen, gelieve te verwijzen naar [het Aanpassen van Consoles](/help/sites-developing/customizing-consoles-touch.md).

#### Wat is het verschil tussen CoralUI 2 en CoralUI op 3-Gebaseerde componenten? {#what-is-the-difference-between-coralui-and-coralui-based-components}

Er wordt een nieuwe set Sling-componenten van Granite UI Foundation gemaakt voor Coral3 en bevindt zich onder [/libs/granite/ui/components/koral/foundation.](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/granite-ui/api/jcr_root/libs/granite/ui/components/coral/foundation/server.html) Er is één set voor op CoralUI 2 gebaseerde componenten en één set voor op CoralUI 3 gebaseerde componenten. De nieuwe set is niet alleen een kopie-plakbewerking van de oude set, maar wordt opgeschoond (bijvoorbeeld het stroomlijnen, verwijderen van vervangen functies). Daarom wordt aanbevolen dat een pagina alleen gebruik maakt van op CoralUI 3 gebaseerde of op CoralUI 2 gebaseerde sets.

Raadpleeg [Migratiehandleiding naar CoralUI 3-gebaseerd](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/granite-ui/api/jcr_root/libs/granite/ui/components/legacy/coral2/migration.html) voor meer informatie.

#### Hoe kan ik de zoekcomponent in AEM Assets aanpassen? {#how-to-customize-the-search-component-in-aem-assets}

Raadpleeg [Eenvoudige handleiding voor zoekfuncties](https://helpx.adobe.com/experience-manager/kt/sites/using/search-tutorial-develop.html) voor meer informatie over zoekresultaten/rangschikking en verdere implementatiegegevens.

De Eenvoudige onderzoeksimplementatie is de materialen van het laboratorium van de Top van 2017 AEM Gedetailleerd Onderzoek.

#### Is het mogelijk om insteekmodule voor WordPress te bouwen die een klant toestaat om tot de Plukker van Activa van Adobe toegang te hebben om beelden te selecteren? {#is-it-possible-to-build-plugin-for-wordpress-that-allows-a-customer-to-access-adobe-asset-picker-to-select-images}

Ja, een klant die WordPress gebruikt, kan de Adobe Asset Picker gebruiken om afbeeldingen van zijn AEM Assets-server te selecteren en toe te voegen aan advertenties op zijn WordPress-site.

Raadpleeg [Asset Selector](../assets/search-assets.md#assetpicker) voor meer informatie.
