---
title: Veelgestelde vragen over AEM
seo-title: AEM 6.4 veelgestelde vragen
description: Gebruik deze veelgestelde vragen om algemene workflows of problemen in AEM te begrijpen, te configureren en op te lossen.
seo-description: Gebruik deze veelgestelde vragen om algemene workflows of problemen in AEM te begrijpen, te configureren en op te lossen.
uuid: 17d34923-f1ce-463b-8e9d-a713edcce51b
contentOwner: jsyal
discoiquuid: a3bb5695-6593-413d-9c2f-4c164e663b15
docset: aem65
translation-type: tm+mt
source-git-commit: bc042696506bf1691c2eeffc6ab941be85fa274c

---


# Veelgestelde vragen over AEM {#aem-faqs}

De antwoorden op sommige problemen met AEM-probleemoplossing en -configuratie kennen.

## Sites {#sites}

### Hoe vorm ik binair-minder distributie? {#how-do-i-configure-binary-less-distribution}

Binaire distributie zonder beperkingen wordt ondersteund voor implementaties via een gedeelde gegevensopslag en betreft agents die gebruikmaken van de exportfunctie van het Vault Distribution Package (factory PID: `org.apache.sling.distribution.serialization.impl.vlt.VaultDistributionPackageBuilderFactory`) package builder.

Met binair-geen toegelaten wijze, bevatten de verdeelde inhoudspakketten verwijzingen naar binaire getallen eerder dan de daadwerkelijke binaire getallen.

#### Hoe laat ik binair-minder distributie toe? {#how-do-i-enable-binary-less-distribution}

Om binair-minder distributie toe te laten, stel met een gedeelde blob opslag op.
Controleer het `useBinaryReferences` bezit in de configuratie OSGI met fabriek PID ( `org.apache.sling.distribution.serialization.impl.vlt.VaultDistributionPackageBuilderFactory`*)*die uw agent gebruikt.

#### Hoe kan ik de foutenmeldingen aanpassen terwijl het navigeren van paginahiërarchie in AEM plaatsenconsole? {#how-can-i-customize-the-error-messages-while-navigating-page-hierarchy-in-aem-sites-console}

Controleer het deelvenster Netwerk (van de Chrome-browser) waar een persoonlijke setup (JS) niet is geminiateerd.

Bekijk de `Initiator` kolom om te bepalen wat de initiatiefnemer van een verzoek was. Het verstrekt de dossiers en de lijnaantallen van waar de vraag AJAX wordt gemaakt. Later kunt u de functie voor foutafhandeling overtrekken en het foutbericht naar wens wijzigen.

#### Hoe te om toestemmingen toe te laten terwijl het creëren van het Exemplaar van de Taal voor tevreden-Auteurs in AEM? {#how-to-enable-permissions-while-creating-language-copy-for-content-authors-in-aem}

Voor het maken van een functie voor het kopiëren van talen hebben inhoudsauteurs machtigingen op hun `/content/projects` locatie nodig.

Als de auteurs ook projecten moeten beheren, moet u de auteur aan de `project-administrators` groep toevoegen.

#### Hoe te om het formaat te veranderen terwijl het creëren van het Exemplaar van de Taal voor een project? {#how-to-change-the-format-while-creating-language-copy-for-a-project}

Creeer een taalwortel en taalexemplaar binnen de wortel, alvorens een vertaalproject tot stand te brengen.

Maak bijvoorbeeld een hoofdmap van een taal `/content/geometrixx` met de naam `fr_LU` (en een titel als Frans (Luxemburg)). Maak vervolgens een taalkopie van de pagina in het venster Referenties en navigeer naar de `Create structure only` optie in `Create & Translate`. Tot slot creeer een vertaalproject en voeg dan de taalexemplaar aan de vertaalbaan toe.

Raadpleeg de volgende aanvullende bronnen voor meer informatie:

* [Inhoud voorbereiden voor vertaling](/help/sites-administering/tc-prep.md)
* [Vertaalprojecten beheren](/help/sites-administering/tc-manage.md)

#### Hoe te om mogelijkheden AEM zoals, login pogingen en ACL of toestemmingsveranderingen te controleren? {#how-to-audit-aem-capabilities-such-as-login-attempts-and-acl-or-permission-changes}

AEM heeft de capaciteit geïntroduceerd om administratieve veranderingen voor betere het oplossen van problemen en controle te registreren. Standaard wordt de informatie in het `error.log` bestand aangemeld. Om controle gemakkelijker te maken, adviseert men dat zij aan een afzonderlijk logboekdossier worden opnieuw gericht.
Om de output aan een afzonderlijk logboekdossier om te leiden, zie [hoe te de verrichtingen van het gebruikersbeheer in AEM](/help/sites-administering/audit-user-management-operations.md)controleren.

#### Hoe te om SSL door gebrek toe te laten? {#how-to-enable-ssl-by-default}

Adobe Experience Manager (AEM) 6.4 wordt geleverd met de SSL-wizard en biedt een gebruikersinterface voor het configureren van Jetty- en Granite Jetty SSL-ondersteuning.

Als u standaard SSL wilt inschakelen, raadpleegt u [standaard](/help/sites-administering/ssl-by-default.md)SSL.

#### Wat is de aanbevolen architectuur wanneer u AEM&#39;s Content Services vanuit een mobiele app gebruikt, bij voorkeur React Native? {#what-is-the-recommended-architecture-when-using-aem-s-content-services-from-a-mobile-app-ideally-react-native}

De diensten van de Inhoud zijn gebaseerd op de het Verdelen Modellen en de ontwikkelaars AEM moeten een het Verdelen Model pojo voor elke component verstrekken die wordt uitgevoerd.

Als u wilt weten hoe u AEM-inhoudsservices kunt gebruiken vanuit een React-toepassing, raadpleegt u de zelfstudie [Aan de slag met AEM Content Services](https://helpx.adobe.com/experience-manager/kt/sites/using/content-services-tutorial-use.html) .

Ook, als de ontwikkelaars een boom van componenten willen uitvoeren kunnen zij `ComponentExporter` en `ContainerExporter` `ModelFactory` interfaces ook uitvoeren evenals gebruiken om over de kindcomponenten te herhalen en hun modelvertegenwoordiging terug te keren. Zie de volgende bronnen:

[1] [Adobe-Marketing-Cloud/aem-core-wcm-componenten](https://github.com/Adobe-Marketing-Cloud/aem-core-wcm-components/blob/master/bundles/core/src/main/java/com/adobe/cq/wcm/core/components/internal/models/v1/PageImpl.java#L245)

[2] [Apache Sling:Verkoopmodellen](https://sling.apache.org/documentation/bundles/models.html)

#### Hoe kan ik pop-up voor AEM 6.4-enquêtes uitschakelen? {#how-to-disable-aem-survey-pop-up}

U kunt in de inzameling van gebruiksstatistieken door of Touch UI of de Console van het Web te gebruiken kiezen. Voor gedetailleerde instructies, zie [Opting in de inzameling](/help/sites-deploying/opt-in-aggregated-usage-statistics.md)van de samengevoegde gebruiksstatistieken.

#### Is er een goede bron die de belangrijkste eigenschappen voor verbetering aan AEM 6.4 benadrukt? {#is-there-a-good-resource-that-highlights-the-key-features-for-upgrading-to-aem}

Raadpleeg de [Redenen voor het upgraden van AEM](https://helpx.adobe.com/experience-manager/kt/platform-repository/using/upgrade-aem-article-understand.html) voor een overzicht van de belangrijkste functies op hoog niveau voor klanten die een upgrade naar de nieuwste versie van Adobe Experience Manager overwegen.

## Activa {#assets}

### Waarom wordt de middelenworkflow zichzelf herhaald tijdens het uploaden van MP4-bestanden (bijvoorbeeld met slepen en neerzetten)? {#why-the-assets-workflow-repeats-itself-while-uploading-mp-files-for-example-using-drag-and-drop-method}

Als de gebruiker, die de filmdossiers uploadt geen toestemmingen onder activaknoop schrapt, ontbreken de schrappingsbrokkenknopen en uploadt opnieuw begint.

#### Wat is het maximumaantal digitale activa dat met AEM 6.4 tegelijkertijd kan worden in werking gesteld? {#what-is-the-maximum-number-of-digital-assets-that-can-be-operated-with-aem-at-a-time}

Met Adobe Experience Manager (AEM) 6.5 kunt u momenteel maximaal 2 GB aan middelen tegelijk uploaden.

Zie voor meer informatie over het maximumaantal activa dat met AEM 6.5 kan worden geëxploiteerd de gids voor [middelengrootte](/help/assets/assets-sizing-guide.md).

#### Wat zijn de standaardmontages voor configuraties OTB terwijl het creëren van het Exemplaar van de Taal? {#what-are-the-default-settings-for-ootb-configurations-while-creating-language-copy}

Wanneer u taalkopieën maakt via een klassieke UI, worden Elementen niet onder de nieuwe taalhiërarchie geplaatst, maar vanuit de hoofdtaal gebruikt.

Wanneer u een taalkopie maakt via Touch UI (**References** -> **Update Language Copy**), wordt er een nieuwe DAM-map gemaakt onder de nieuwe taal en wordt er naar de nieuwe elementen verwezen.

Dit is de standaardinstelling voor OOTB-configuraties. U kunt **Vertaalpagina-elementen** = **Niet vertalen** in vertaalconfiguraties instellen.
Voor AEM 6.4: **Gereedschappen** > **Cloud Services** > **Cloud-services** voor vertaling.

#### Hoe te om een component onbruikbaar te maken AEM die exponentiële groei voor AEM SegmentStore (AEM 6.3.1.1) veroorzaakt? {#how-to-disable-an-aem-component-causing-exponential-growth-for-the-aem-segmentstore-aem}

U kunt de Disabler van de Component OSGi onbruikbaar maken. Om deze dienst te gebruiken, zie [Component Disabler](https://adobe-consulting-services.github.io/acs-aem-commons/features/osgi-disablers/component-disabler/index.html)OSGi.

Als tussenoplossing kunt u de component ook handmatig uitschakelen via de gebruikersinterface of via een `curl` opdracht (voorbeeld hieronder), nadat elke AEM opnieuw is gestart.

`curl -u admin:$(pass CQ_Admin) 'https://localhost:4502/system/console/components/com.day.cq.analytics.sitecatalyst.impl.importer.ReportImporter' --data 'action=disable'`

#### Hoe te om de Inzichten van Activa met AEM 6.5 instantie te vormen? {#how-to-configure-asset-insights-with-aem-instance}

Als u Asset Insights wilt instellen en configureren voor Experience Manager die wordt geïmplementeerd via Adobe Activation (DTM), raadpleegt u [Asset Insights instellen met AEM Assets](https://helpx.adobe.com/experience-manager/kt/assets/using/asset-insights-tutorial-setup.html).

#### Hoe te om admin consoles aan te passen? {#how-to-customize-admin-consoles}

AEM biedt verschillende mechanismen waarmee u de consoles en de functionaliteit voor het schrijven van pagina&#39;s van uw ontwerpinstantie kunt aanpassen. Leer hoe te om een douaneconsole tot stand te brengen en een standaardmening voor een console aan te passen, gelieve te verwijzen naar het [Aanpassen van de Consoles](/help/sites-developing/customizing-consoles-touch.md).

#### Wat is het verschil tussen CoralUI 2 en CoralUI op 3-Gebaseerde componenten? {#what-is-the-difference-between-coralui-and-coralui-based-components}

Er wordt een nieuwe set Sling-componenten van Granite UI Foundation gemaakt voor Coral3 en deze bevindt zich onder [/libs/granite/ui/components/koral/foundation.](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/granite-ui/api/jcr_root/libs/granite/ui/components/coral/foundation/server.html) Er is één set voor op CoralUI 2 gebaseerde componenten en één set voor op CoralUI 3 gebaseerde componenten. De nieuwe set is niet alleen een kopie-plakbewerking van de oude set, maar wordt opgeschoond (bijvoorbeeld het stroomlijnen, verwijderen van vervangen functies). Daarom wordt aanbevolen dat een pagina alleen gebruik maakt van op CoralUI 3 gebaseerde of op CoralUI 2 gebaseerde sets.

Raadpleeg de [Migratiehandleiding naar CoralUI 3 voor meer informatie](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/granite-ui/api/jcr_root/libs/granite/ui/components/legacy/coral2/migration.html).

#### Hoe kan de zoekcomponent in AEM Assets worden aangepast? {#how-to-customize-the-search-component-in-aem-assets}

Raadpleeg de handleiding voor [eenvoudige implementatie van zoekopdrachten voor meer informatie over zoekresultaten/rangschikking en verdere implementatiegegevens](https://helpx.adobe.com/experience-manager/kt/sites/using/search-tutorial-develop.html).

De Eenvoudige onderzoeksimplementatie is de materialen van het laboratorium AEM van de Top van 2017 Gedetailleerd Onderzoek van het laboratorium van de Top.

#### Wat is het verschil tussen AEM Assets en AEM MediaLibrary? {#what-is-the-difference-between-aem-assets-and-aem-medialibrary}

AEM Assets is een toepassing op het AEM Platform waarmee onze klanten hun digitale middelen (afbeeldingen, video&#39;s, documenten en audioclips) kunnen beheren in een webopslagplaats, terwijl AEM Media Library een aangewezen onderdeel is van de AEM WCM-inhoudsopslagruimte waar afbeeldingen en andere gedeelde bronnen worden opgeslagen.

Raadpleeg [AEM Assets vs. AEM MediaLibrary](/help/assets/medialibrary.md) voor meer informatie.

#### Kan een insteekmodule voor WordPress worden gemaakt waarmee een klant toegang krijgt tot de Adobe Asset Picker om afbeeldingen te selecteren? {#is-it-possible-to-build-plugin-for-wordpress-that-allows-a-customer-to-access-adobe-asset-picker-to-select-images}

Ja, een klant die WordPress gebruikt, kan de Adobe Asset Picker gebruiken om afbeeldingen van zijn AEM Assets-server te selecteren en toe te voegen aan advertenties op zijn WordPress-site.

Raadpleeg [Asset Selector](../assets/search-assets.md#assetselector) voor meer informatie.

#### Is het mogelijk om de zoekfacetten in activa AEM uit te breiden om extra predikaten toe te voegen? {#is-it-possible-to-extend-the-search-facets-in-aem-assets-to-add-additional-predicates}

Een bedrijfsbrede implementatie van Adobe Experience Manager (AEM)-middelen biedt de mogelijkheid om veel middelen op te slaan. U kunt voorspelden toevoegen aan het standaardformulier of een aangepast formulier gebruiken dat bepaalde facetten van uw keuze bevat.

Raadpleeg [Zoekfacetten](/help/assets/search-facets.md) voor meer informatie.
