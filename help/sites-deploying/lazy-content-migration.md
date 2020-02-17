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
source-git-commit: 7d93df515bf98f0a947428b8093e059d63b21a34

---


# Lazy Content Migration {#lazy-content-migration}

Omwille van achterwaartse compatibiliteit worden de inhoud en configuratie in **/etc** en **/inhoud** die begint met AEM 6.3 niet onmiddellijk met de upgrade gewijzigd of aangeraakt. Dit wordt gedaan om ervoor te zorgen dat de gebiedsdelen van klantentoepassingen op die structuren intact blijven. De functionaliteit met betrekking tot deze inhoudsstructuren is nog steeds hetzelfde, ook al wordt de inhoud in een gedeelte van het tekstvak AEM 6.5 op een andere plaats gehost.

Hoewel niet al deze locaties automatisch kunnen worden getransformeerd, wordt een aantal vertragingen `CodeUpgradeTasks` ook wel Lazy Content Migration genoemd. Hierdoor kunnen klanten deze automatische transformaties activeren door de instantie opnieuw te starten met deze systeemeigenschap:

```shell
-Dcom.adobe.upgrade.forcemigration=true
```

Hierdoor wordt de migratie `CodeUpgradeTasks` uitgevoerd.

Hoewel het doel een efficiënte uitvoering is, is dit upgradeproces synchroon en heeft het daarom een downtime afhankelijk van de hoeveelheid inhoud die moet worden verwerkt. Het wordt aanbevolen de uitvoeringstijden in een werkgebiedomgeving vóór een productiesysteem te evalueren om een onderhoudsvenster te plannen.

Aangezien dit typisch ook het aanpassen van toepassing vereist zou deze activiteit samen met de overeenkomstige toepassingsplaatsing moeten worden uitgevoerd.

Hieronder vindt u de volledige lijst van de in punt 6.5 `CodeUpgradeTasks` opgenomen gegevens:

| **Naam** | **Relevant** **voor AEM-versies vóór** | **Migratietype** **** | **Details** |
|---|---|---|---|
| `Cq561ProjectContentUpgrade` | &lt; 5.6.1 | Meteen |  |
| `Cq60MSMContentUpgrade` | &lt; 6.0 | Meteen | Detecteert alle `LiveRelationShips` items `VersionStorage` die zijn verwijderd en voegt uitsluitingseigenschap toe aan het bovenliggende element |
| `Cq61CloudServicesContentUpgrade` | &lt; 6.1 | Meteen | Hiermee herstructureert u cloudservices voor beveiligen door standaardinstelling |
| `Cq62ConfContentUpgrade` | &lt; 6.2 | Meteen | Verwijdert bezit gebaseerd die verbinding van **/inhoud** aan **/conf** (door het mechanisme OSGi wordt vervangen), produceert overeenkomstige configuratie OSGi |
| `Cq62FormsContentUpgrade` | &lt; 6.2 | Meteen | wegens merge_preserve behandeling veilig door gebrek ontkent regeloverschrijvingen gegeven toestemmingen die tot de behoefte aan reorder bij verbetering leiden |
| `CQ62Html5SmartFileUpgrade` | &lt; 6.2 | Meteen | Detecteert componenten die de widget Html5SmartFile gebruiken, zoekt naar gebruik van de component in de inhoud en herstructureert persistentie, effectief bewegend het binaire a niveau neer en bewaar het niet op componentenniveau. |
| `Cq62ProjectsCodeUpgrade` | &lt; 6.2 | Meteen | Verplaatst oude stijlprojecten van **/etc/projecten** naar **/content/projecten** |
| `Cq62TargetCampaignsContentUpgrade` | &lt; 6.2 | Meteen | Introduceert een containerlaag tot hiërarchie (Gebieden) en past verwijzingen aan. |
| `Cq62TargetContentUpgrade` | &lt; 6.2 | Meteen | Stelt vaste locatienamen in op doelcomponenten. |
| `Cq62WorkflowContentUpgrade` | &lt; 6.2 | Meteen | Complexe transformatie van workflowmodellen die ouder zijn dan 6.2 structuren, instanties, meldingen en vervolgens van de back-uplocatie samenvoegen vanuit **/var/backup** |
| `CQ63AssetsMetadataFormsUpdate` | &lt; 6.3 | Meteen | Verplaatst elementen, aangepaste schema&#39;s voor metagegevens en verwerkingsprofielen van **/apps** naar **/conf** en zet het metagegevensschema en de metagegevensprofielen om van koraal2 naar koraal3. |
| `CQ63AssetsSearchFacetsUpdate` | &lt; 6.3 | Meteen | Verplaatst elementen en aangepaste zoekfacetten van **/apps** naar **/conf** en zet het metagegevensschema en de metagegevensprofielen om van koraal2 naar koraal3. |
| `CQ63InboxItemsUpgrade` | &lt; 6.3 | Meteen | Updates InboxItems voor het ordenen van items in het Postvak IN (metagegevens aanpassen voor efficiënt sorteren) |
| `CQ63MetadataSchemaConfigUpdate` | &lt; 6.3 | Meteen | Past de eigenschap metadataSchema in de map aan door relatieve paden naar **/conf** te vervangen in plaats van **/apps** |
| `CQ63MobileAppsNavUpgrade` | &lt; 6.3 | Meteen | Navigatiestructuur aanpassen |
| `CQ63MonitoringDashboardsConfigUpdate` | &lt; 6.3 | Meteen | Hiermee verplaatst u aangepaste configuraties voor de monitoringdashboards van **/libs** en **/apps** |
| `CQ63ProcessingProfileConfigUpdate` | &lt; 6.3 | Meteen | Zet de processingProfile-eigenschap (gebruikt tot en met 6.1) om in Elementen, zodat deze overeenkomt met de structuur 6.3 en hoger. Past ook de relatieve paden van het profiel aan **/conf** in plaats van **/apps** aan. |
| `CQ63ToolsMenuEntriesContentUpgrade` | &lt; 6.3 | Meteen | De taak van de verbetering die verouderde CRXDE Lite en het menuingangen van de Console van het Web in het geval van een verbetering verwijdert. |
| `CQ64CommunitiesConfigsCleanupTask` | &lt; 6.3 | Vertraagd | SRP-cloudconfiguraties verplaatsen, configuraties van watchwords voor de gebruikersgemeenschap, opruimen **/etc/social** en **/etc/enablement** (alle referenties en gegevens moeten worden aangepast wanneer lui de migratie wordt uitgevoerd; geen enkel toepassingsonderdeel mag meer afhankelijk zijn van deze structuur). |
| `CQ64LegacyCloudSettingsCleanupTask` | &lt; 6.4 | Vertraagd | Schoont omhoog **/etc/cloudsettings** (die Configuratie ContextHub bevatten). De configuratie wordt automatisch gemigreerd bij eerste toegang. Als Lazy Content Migration wordt gestart samen met een upgrade van deze inhoud in **/etc/cloudsettings** , moet deze inhoud worden behouden via pakket voordat de upgrade wordt uitgevoerd en opnieuw worden geïnstalleerd voordat de impliciete transformatie wordt gestart, samen met een volgende verwijdering van het pakket na voltooiing. |
| `CQ64UsersTitleFixTask` | &lt; 6.4 | Vertraagd | Past oude titelstructuur aan titel in de knoop van het gebruikersprofiel aan. |
| `CQ64CommerceMigrationTask` | &lt; 6.4 | Vertraagd | Migreer commerciële inhoud van **/etc/commerce** aan **/var/commerce**. Tijdens migratie wordt inhoud verplaatst en worden verwijzingen naar verplaatste inhoud bijgewerkt met de nieuwe locatie. |
| `CQ65DMMigrationTask` | &lt; 6.5 | Vertraagd | Verouderde catalogusinstellingen en instellingen voor dynamische mediawolkenservices migreren van **/enz** naar **/conf** |
| `CQ65LegacyClientlibsCleanupTask` | &lt; 6.5 | Vertraagd | Oudere clientlibs opruimen die onder **/etc/clientlibs bestaan** |
