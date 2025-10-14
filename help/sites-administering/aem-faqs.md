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

Distributie zonder binding wordt ondersteund voor implementaties via een gedeelde gegevensopslagruimte en betreft agents die gebruikmaken van de PID-pakketbuilder (factory PID: `org.apache.sling.distribution.serialization.impl.vlt.VaultDistributionPackageBuilderFactory`) op basis van vault.

Met binair-geen toegelaten wijze, bevatten de verdeelde inhoudspakketten verwijzingen naar binaire getallen eerder dan de daadwerkelijke binaire getallen.

#### Hoe laat ik binair-minder distributie toe? {#how-do-i-enable-binary-less-distribution}

Om binair-minder distributie toe te laten, stel met een gedeelde blob opslag op.
Controleer het `useBinaryReferences` bezit in de configuratie OSGI met fabriekPID ( `org.apache.sling.distribution.serialization.impl.vlt.VaultDistributionPackageBuilderFactory`*)* dat uw agent gebruikt.

#### Hoe te om toestemmingen toe te laten terwijl het creëren van het Exemplaar van de Taal voor tevreden-Auteurs in AEM? {#how-to-enable-permissions-while-creating-language-copy-for-content-authors-in-aem}

Voor het maken van een functie voor het kopiëren van talen hebben inhoudsauteurs machtigingen nodig op de locatie `/content/projects` .

Als u wilt dat de auteurs ook projecten beheren, kunt u dit omzeilen door de auteur toe te voegen aan de groep `projects-administrators` .

#### Hoe te om het formaat te veranderen terwijl het creëren van het Exemplaar van de Taal voor een project? {#how-to-change-the-format-while-creating-language-copy-for-a-project}

Creeer een taalwortel en taalexemplaar binnen de wortel, alvorens een vertaalproject tot stand te brengen.

Bijvoorbeeld:
Maak een hoofdmap in `/content/geometrixx` met de naam `fr_LU` (en een titel als Frans (Luxemburg)). Maak vervolgens een taalkopie van de pagina in het venster Referenties en navigeer naar de optie `Create structure only` in `Create & Translate` . Tot slot creeer een vertaalproject en voeg dan de taalexemplaar aan de vertaalbaan toe.

Zie de volgende aanvullende bronnen voor meer informatie:

* [Inhoud voorbereiden voor vertaling](/help/sites-administering/tc-prep.md)
* [Vertaalprojecten beheren](/help/sites-administering/tc-manage.md)

#### Hoe te om AEM mogelijkheden zoals, login pogingen en ACL of toestemmingsveranderingen te controleren? {#how-to-audit-aem-capabilities-such-as-login-attempts-and-acl-or-permission-changes}

AEM heeft de capaciteit geïntroduceerd om administratieve veranderingen voor betere het oplossen van problemen en controle te registreren. Standaard wordt de informatie in het `error.log` -bestand aangemeld. Om controle gemakkelijker te maken, adviseert men dat zij aan een afzonderlijk logboekdossier worden opnieuw gericht.
Om de output aan een afzonderlijk logboekdossier opnieuw te richten, zie [&#x200B; hoe te de verrichtingen van het gebruikersbeheer in AEM &#x200B;](/help/sites-administering/audit-user-management-operations.md) controleren.

#### Hoe te om SSL door gebrek toe te laten? {#how-to-enable-ssl-by-default}

Adobe Experience Manager (AEM) 6.4 wordt geleverd met de SSL-wizard en biedt een gebruikersinterface voor het configureren van Jetty- en Granite Jetty SSL-ondersteuning.

Om SSL door gebrek toe te laten, zie [&#x200B; SSL door gebrek &#x200B;](/help/sites-administering/ssl-by-default.md).

#### Wat is de aanbevolen architectuur wanneer u AEM Content Services gebruikt vanuit een mobiele app, idealiter React Native? {#what-is-the-recommended-architecture-when-using-aem-s-content-services-from-a-mobile-app-ideally-react-native}

De diensten van de Inhoud zijn gebaseerd op de het Verdelen Modellen en de AEM ontwikkelaars moeten een het Verdelen Model pojo voor elke component verstrekken die wordt uitgevoerd.

Om te begrijpen hoe te om AEM inhoudsdiensten van een React toepassing te verbruiken, zie [&#x200B; Begonnen krijgen met AEM inhoudsdiensten &#x200B;](https://helpx.adobe.com/experience-manager/kt/sites/using/content-services-tutorial-use.html) leerprogramma.

Als ontwikkelaars een structuur met componenten willen exporteren, kunnen ze ook de interfaces `ComponentExporter` en `ContainerExporter` implementeren en `ModelFactory` gebruiken om de onderliggende componenten te doorlopen en hun modelrepresentatie te retourneren. Zie de volgende bronnen:

[ 1 ] [&#x200B; Adobe-marketing-Wolk/aem-kern-wcm-componenten &#x200B;](https://github.com/Adobe-Marketing-Cloud/aem-core-wcm-components/blob/master/bundles/core/src/main/java/com/adobe/cq/wcm/core/components/internal/models/v1/PageImpl.java#L245)

[&#x200B; [ ]  Apache die: Het verdelen Modellen &#x200B;](https://sling.apache.org/documentation/bundles/models.html)

#### Hoe te om AEM 6.4 enquête pop-up onbruikbaar te maken? {#how-to-disable-aem-survey-pop-up}

U kunt in de inzameling van gebruiksstatistieken door of Touch UI of de Console van het Web te gebruiken kiezen. Voor gedetailleerde instructies, zie [&#x200B; Opting in de inzameling van de bijeengevoegde gebruiksstatistieken &#x200B;](/help/sites-deploying/opt-in-aggregated-usage-statistics.md).

#### Is er een goede bron die de belangrijkste eigenschappen voor bevordering aan AEM 6.4 benadrukt? {#is-there-a-good-resource-that-highlights-the-key-features-for-upgrading-to-aem}

Zie [&#x200B; Begrijpend Redenen om AEM &#x200B;](https://helpx.adobe.com/experience-manager/kt/platform-repository/using/upgrade-aem-article-understand.html) te bevorderen die de hoogniveaumislukking van zeer belangrijke eigenschappen voor klanten het overwegen van bevordering aan de recentste versie van Adobe Experience Manager beschrijft.

## Assets {#assets}

### Waarom wordt de Assets-workflow zichzelf herhaald tijdens het uploaden van MP4-bestanden (bijvoorbeeld via slepen en neerzetten)? {#why-the-assets-workflow-repeats-itself-while-uploading-mp-files-for-example-using-drag-and-drop-method}

Als de gebruiker, die de filmdossiers uploadt geen toestemmingen onder activaknoop schrapt, ontbreken de schrappingsbrokkenknopen en uploadt opnieuw begint.

#### Wat zijn de standaardmontages voor uit-van-de-doos configuraties terwijl het creëren van het Exemplaar van de Taal? {#what-are-the-default-settings-for-ootb-configurations-while-creating-language-copy}

Wanneer u een taalexemplaar door Touch UI (**Verwijzingen** > **het Exemplaar van de Taal van de Update**) creeert, wordt een nieuwe omslag DAM gecreeerd onder de nieuwe taal en de activa van daar van verwijzingen voorzien.

Dit is standaard het plaatsen voor uit-van-de-doos configuraties. U kunt **Vertaalpagina Assets** plaatsen = **vertaal** niet in Vertaalconfiguraties.
Voor AEM 6.4, **Hulpmiddelen** > **Cloud Servicen** > **de diensten van de Wolk van de Vertaling**.

#### Hoe te om een AEM component onbruikbaar te maken die exponentiële groei voor AEM SegmentStore (AEM 6.3.1.1) veroorzaakt? {#how-to-disable-an-aem-component-causing-exponential-growth-for-the-aem-segmentstore-aem}

U kunt de Component onbruikbaar maken OSGi. Om deze dienst te gebruiken, zie {de Disabler van de Component 0} OSGi [&#128279;](https://adobe-consulting-services.github.io/acs-aem-commons/features/osgi-disablers/component-disabler/index.html).

Als tussenoplossing kunt u de component ook handmatig uitschakelen via de gebruikersinterface of via een opdracht `curl` (voorbeeld hieronder), na elke AEM opnieuw opstarten.

`curl -u admin:$(pass CQ_Admin) 'https://localhost:4502/system/console/components/com.day.cq.analytics.sitecatalyst.impl.importer.ReportImporter' --data 'action=disable'`

#### Hoe te om admin consoles aan te passen? {#how-to-customize-admin-consoles}

AEM biedt verschillende mechanismen waarmee u de consoles en de functionaliteit voor het schrijven van pagina&#39;s van de ontwerpinstantie kunt aanpassen. Leren hoe te om een douaneconsole tot stand te brengen en een standaardmening voor een console aan te passen, zie [&#x200B; Aanpassen van de Consoles &#x200B;](/help/sites-developing/customizing-consoles-touch.md).

#### Wat is het verschil tussen CoralUI 2 en CoralUI op 3-Gebaseerde componenten? {#what-is-the-difference-between-coralui-and-coralui-based-components}

Er wordt een nieuwe set Sling-componenten van de Granite UI Foundation gemaakt voor Coral3 en deze bevindt zich onder [&#x200B; /libs/granite/ui/components/koral/foundation.](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/granite-ui/api/jcr_root/libs/granite/ui/components/coral/foundation/server.html) Er is één set voor op CoralUI 2 gebaseerde componenten en één set voor op CoralUI 3 gebaseerde componenten. De nieuwe set is niet alleen een kopie-plakbewerking van de oude set, maar wordt opgeschoond (bijvoorbeeld het stroomlijnen, verwijderen van vervangen functies). Daarom wordt aanbevolen dat een pagina alleen gebruik maakt van op CoralUI 3 gebaseerde of op CoralUI 2 gebaseerde sets.

Meer in detail leren, zie [&#x200B; Gids van de Migratie aan CoralUI 3-Gebaseerde &#x200B;](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/granite-ui/api/jcr_root/libs/granite/ui/components/legacy/coral2/migration.html).

#### Hoe kan ik de zoekcomponent in AEM Assets aanpassen? {#how-to-customize-the-search-component-in-aem-assets}

Om over onderzoeksverhoging/het rangschikken en verdere implementatieinformatie te leren, zie [&#x200B; Eenvoudige gids van de onderzoeksimplementatie &#x200B;](https://helpx.adobe.com/experience-manager/kt/sites/using/search-tutorial-develop.html).

De Eenvoudige onderzoeksimplementatie is de materialen van het laboratorium van de Top van 2017 AEM Gedetailleerd Onderzoek.

#### Is het mogelijk om insteekmodule voor WordPress te bouwen die een klant toestaat om tot de Plukker van Activa van de Adobe toegang te hebben om beelden te selecteren? {#is-it-possible-to-build-plugin-for-wordpress-that-allows-a-customer-to-access-adobe-asset-picker-to-select-images}

Ja, een klant die WordPress gebruikt, kan de Adobe Asset Picker gebruiken om afbeeldingen van zijn AEM Assets-server te selecteren en toe te voegen aan advertenties op zijn WordPress-site.

Verwijs naar [&#x200B; de Selecteur van Activa &#x200B;](../assets/search-assets.md#assetpicker) voor meer informatie.
