---
title: Lazy Content Migration
seo-title: Lazy Content Migration
description: Meer informatie over Lazy Content Migration in AEM 6.4.
seo-description: Meer informatie over Lazy Content Migration in AEM 6.4.
uuid: f5b0aa84-5638-4708-9da2-89964d394632
contentOwner: sarchiz
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: upgrading
discoiquuid: d72b8844-d782-4b5b-8999-338217dbefb9
docset: aem65
translation-type: tm+mt
source-git-commit: 4090b1641467c6fb02b2fcce4df97b9fd5da4e2f
workflow-type: tm+mt
source-wordcount: '704'
ht-degree: 3%

---


# Lazy Content Migration {#lazy-content-migration}

Met het oog op achterwaartse compatibiliteit worden de inhoud en configuratie in **/etc** en **/content** die beginnen met AEM 6.3, niet direct aangeraakt of getransformeerd met de upgrade. Dit wordt gedaan om ervoor te zorgen dat de gebiedsdelen van klantentoepassingen op die structuren intact blijven. De functionaliteit met betrekking tot deze inhoudsstructuren is nog steeds hetzelfde, ook al wordt de inhoud in een gedeelte van het vak AEM 6.5 op een andere plaats gehost.

Hoewel niet al deze locaties automatisch kunnen worden getransformeerd, worden enkele vertraagde `CodeUpgradeTasks` ook wel Lazy Content Migration genoemd. Hierdoor kunnen klanten deze automatische transformaties activeren door de instantie opnieuw te starten met deze systeemeigenschap:

```shell
-Dcom.adobe.upgrade.forcemigration=true
```

Hierdoor wordt `CodeUpgradeTasks` tijdens de migratie uitgevoerd.

Hoewel het doel een efficiënte uitvoering is, is dit upgradeproces synchroon en heeft het daarom een downtime afhankelijk van de hoeveelheid inhoud die moet worden verwerkt. Het wordt aanbevolen de uitvoeringstijden in een werkgebiedomgeving vóór een productiesysteem te evalueren om een onderhoudsvenster te plannen.

Aangezien dit typisch ook het aanpassen van toepassing vereist zou deze activiteit samen met de overeenkomstige toepassingsplaatsing moeten worden uitgevoerd.

Hieronder ziet u de volledige lijst van `CodeUpgradeTasks` die in 6.5 is geïntroduceerd:

| **Naam** | **** **Relevant voor AEM versies voorafgaand aan** | **** **MigrationType** | **Details** |
|---|---|---|---|
| `Cq561ProjectContentUpgrade` | &lt; 5=&quot;&quot;> | Meteen |  |
| `Cq60MSMContentUpgrade` | &lt; 6.0 | Meteen | Detecteert alle `LiveRelationShips` van `VersionStorage` die zijn verwijderd en uitsluitingseigenschap toevoegen aan het bovenliggende element |
| `Cq61CloudServicesContentUpgrade` | &lt; 6=&quot;&quot;> | Meteen | Hiermee herstructureert u cloudservices voor beveiligen door standaardinstelling |
| `Cq62ConfContentUpgrade` | &lt; 6=&quot;&quot;> | Meteen | Verwijdert eigenschap gebaseerd koppelen van **/content** naar **/conf** (vervangen door het OSGi mechanisme), genereert corresponderende OSGi configuratie |
| `Cq62FormsContentUpgrade` | &lt; 6=&quot;&quot;> | Meteen | wegens merge_preserve behandeling veilig door gebrek ontkent regeloverschrijvingen gegeven toestemmingen die tot de behoefte aan reorder bij verbetering leiden |
| `CQ62Html5SmartFileUpgrade` | &lt; 6=&quot;&quot;> | Meteen | Detecteert componenten die de widget Html5SmartFile gebruiken, zoekt naar gebruik van de component in de inhoud en herstructureert persistentie, effectief bewegend het binaire a niveau neer en bewaar het niet op componentenniveau. |
| `Cq62ProjectsCodeUpgrade` | &lt; 6=&quot;&quot;> | Meteen | Verplaatst oude stijlprojecten van **/etc/projects** naar **/content/projects** |
| `Cq62TargetCampaignsContentUpgrade` | &lt; 6=&quot;&quot;> | Meteen | Introduceert een containerlaag tot hiërarchie (Gebieden) en past verwijzingen aan. |
| `Cq62TargetContentUpgrade` | &lt; 6=&quot;&quot;> | Meteen | Stelt vaste locatienamen in op doelcomponenten. |
| `Cq62WorkflowContentUpgrade` | &lt; 6=&quot;&quot;> | Meteen | Complexe transformatie van workflowmodellen die ouder zijn dan 6.2 structuren, instanties, meldingen en vervolgens van de back-uplocatie samenvoegen vanaf **/var/backup** |
| `CQ63AssetsMetadataFormsUpdate` | &lt; 6=&quot;&quot;> | Meteen | Hiermee verplaatst u elementen, aangepaste metagegevensschema&#39;s en verwerkingsprofielen van **/apps** naar **/conf** en zet u het metagegevensschema en de metagegevensprofielen om van koraal2 naar koral3. |
| `CQ63AssetsSearchFacetsUpdate` | &lt; 6=&quot;&quot;> | Meteen | Hiermee verplaatst u elementen en aangepaste zoekfacetten van **/apps** naar **/conf** en zet u het metagegevensschema en de metagegevensprofielen om van koraal2 naar koral3. |
| `CQ63InboxItemsUpgrade` | &lt; 6=&quot;&quot;> | Meteen | Updates InboxItems voor het ordenen van items in het Postvak IN (metagegevens aanpassen voor efficiënt sorteren) |
| `CQ63MetadataSchemaConfigUpdate` | &lt; 6=&quot;&quot;> | Meteen | Past de eigenschap metadataSchema op map aan door relatieve paden naar **/conf** te vervangen in plaats van **/apps** |
| `CQ63MobileAppsNavUpgrade` | &lt; 6=&quot;&quot;> | Meteen | Navigatiestructuur aanpassen |
| `CQ63MonitoringDashboardsConfigUpdate` | &lt; 6=&quot;&quot;> | Meteen | Hiermee verplaatst u aangepaste configuraties voor de monitoringdashboards van **/libs** en **/apps** |
| `CQ63ProcessingProfileConfigUpdate` | &lt; 6=&quot;&quot;> | Meteen | Zet de processingProfile-eigenschap (gebruikt tot en met 6.1) om in Elementen, zodat deze overeenkomt met de structuur 6.3 en hoger. Past ook de relatieve wegen van het profiel aan **/conf** in plaats van **/apps** aan. |
| `CQ63ToolsMenuEntriesContentUpgrade` | &lt; 6=&quot;&quot;> | Meteen | De taak van de verbetering die verouderde CRXDE Lite en het menuingangen van de Console van het Web in het geval van een verbetering verwijdert. |
| `CQ64CommunitiesConfigsCleanupTask` | &lt; 6=&quot;&quot;> | Vertraagd | Bewegende SRP-cloudconfiguraties, configuraties van gemeenschapswatchwords, schoont **/etc/social** en **/etc/enablement** op (verwijzingen en gegevens moeten worden aangepast wanneer lui migratie wordt uitgevoerd - geen toepassingsonderdeel mag meer afhankelijk zijn van deze structuur). |
| `CQ64LegacyCloudSettingsCleanupTask` | &lt; 6=&quot;&quot;> | Vertraagd | Schoont **/etc/cloudsettings** (die Configuratie ContextHub bevatten) op. De configuratie wordt automatisch gemigreerd bij eerste toegang. Als Lazy Content Migration wordt gestart samen met een upgrade van deze inhoud in **/etc/cloudsettings** moet worden bewaard via pakket voor de upgrade en opnieuw worden geïnstalleerd om de impliciete transformatie te starten, samen met een volgende verwijdering van het pakket na voltooiing. |
| `CQ64UsersTitleFixTask` | &lt; 6=&quot;&quot;> | Vertraagd | Past oude titelstructuur aan titel in de knoop van het gebruikersprofiel aan. |
| `CQ64CommerceMigrationTask` | &lt; 6=&quot;&quot;> | Vertraagd | Migreer commerciële inhoud van **/etc/commerce** aan **/var/commerce**. Tijdens migratie wordt inhoud verplaatst en worden verwijzingen naar verplaatste inhoud bijgewerkt met de nieuwe locatie. |
| `CQ65DMMigrationTask` | &lt; 6=&quot;&quot;> | Vertraagd | Verouderde catalogusinstellingen en Dynamic Media-Cloud Services migreren van **/etc** naar **/conf** |
| `CQ65LegacyClientlibsCleanupTask` | &lt; 6=&quot;&quot;> | Vertraagd | Oudere clientlibs opruimen onder **/etc/clientlibs** |
