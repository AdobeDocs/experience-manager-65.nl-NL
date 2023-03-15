---
title: Lazy Content Migration
seo-title: Lazy Content Migration
description: Meer informatie over Lazy Content Migration in AEM 6.4.
seo-description: Learn about Lazy Content Migration in AEM 6.4.
uuid: f5b0aa84-5638-4708-9da2-89964d394632
contentOwner: sarchiz
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: upgrading
discoiquuid: d72b8844-d782-4b5b-8999-338217dbefb9
docset: aem65
feature: Upgrading
exl-id: 946c7c2a-806b-4461-a38b-9c2e5ef1e958
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '694'
ht-degree: 3%

---

# Lazy Content Migration {#lazy-content-migration}

Omwille van achterwaartse compatibiliteit, inhoud en configuratie in **/etc** en **/content** vanaf AEM 6.3 wordt de upgrade niet onmiddellijk aangeraakt of getransformeerd. Dit wordt gedaan om ervoor te zorgen dat de gebiedsdelen van klantentoepassingen op die structuren intact blijven. De functionaliteit met betrekking tot deze inhoudsstructuren is nog steeds hetzelfde, ook al wordt de inhoud in een gedeelte van het vak AEM 6.5 op een andere plaats gehost.

Hoewel niet al deze locaties automatisch kunnen worden getransformeerd, zijn er enkele vertragingen `CodeUpgradeTasks` ook wel Lazy Content Migration genoemd. Hierdoor kunnen klanten deze automatische transformaties activeren door de instantie opnieuw te starten met deze systeemeigenschap:

```shell
-Dcom.adobe.upgrade.forcemigration=true
```

Dit leidt tot `CodeUpgradeTasks` die tijdens de migratie moeten worden uitgevoerd.

Hoewel het doel een efficiënte uitvoering is, is dit upgradeproces synchroon en heeft het daarom een downtime afhankelijk van de hoeveelheid inhoud die moet worden verwerkt. Het wordt aanbevolen de uitvoeringstijden in een werkgebiedomgeving vóór een productiesysteem te evalueren om een onderhoudsvenster te plannen.

Aangezien dit typisch ook het aanpassen van toepassing vereist zou deze activiteit samen met de overeenkomstige toepassingsplaatsing moeten worden uitgevoerd.

Hieronder ziet u de volledige lijst van `CodeUpgradeTasks` toegevoegd in punt 6.5:

| **Naam** | **Relevant** **voor AEM versies vóór** | **Migratie** **Type** | **Details** |
|---|---|---|---|
| `Cq561ProjectContentUpgrade` | &lt; 5.6.1 | Meteen |  |
| `Cq60MSMContentUpgrade` | &lt; 6.0 | Meteen | Alles wordt gedetecteerd `LiveRelationShips` van `VersionStorage` die zijn verwijderd en uitsluitingseigenschap aan het bovenliggende element toevoegen |
| `Cq61CloudServicesContentUpgrade` | &lt; 6.1 | Meteen | Hiermee herstructureert u cloudservices voor beveiligen door standaardinstelling |
| `Cq62ConfContentUpgrade` | &lt; 6.2 | Meteen | Verwijdert op eigenschap gebaseerde koppeling uit **/content** tot **/conf** (vervangen door het OSGi mechanisme), produceert overeenkomstige configuratie OSGi |
| `Cq62FormsContentUpgrade` | &lt; 6.2 | Meteen | wegens merge_preserve behandeling veilig door gebrek ontkent regeloverschrijvingen gegeven toestemmingen die tot de behoefte aan reorder bij verbetering leiden |
| `CQ62Html5SmartFileUpgrade` | &lt; 6.2 | Meteen | Detecteert componenten die de widget Html5SmartFile gebruiken, zoekt naar gebruik van de component in de inhoud en herstructureert persistentie, effectief bewegend het binaire a niveau neer en bewaar het niet op componentenniveau. |
| `Cq62ProjectsCodeUpgrade` | &lt; 6.2 | Meteen | Verplaatst oude stijlprojecten van **/etc/projects** tot **/content/projects** |
| `Cq62TargetCampaignsContentUpgrade` | &lt; 6.2 | Meteen | Introduceert een containerlaag tot hiërarchie (Gebieden) en past verwijzingen aan. |
| `Cq62TargetContentUpgrade` | &lt; 6.2 | Meteen | Stelt vaste locatienamen in op doelcomponenten. |
| `Cq62WorkflowContentUpgrade` | &lt; 6.2 | Meteen | Complexe transformatie van workflowmodellen die ouder zijn dan 6.2 structuren, instanties, meldingen en vervolgens van de back-uplocatie samenvoegen vanuit **/var/backup** |
| `CQ63AssetsMetadataFormsUpdate` | &lt; 6.3 | Meteen | Hiermee verplaatst u elementen, aangepaste metagegevensschema&#39;s en verwerkingsprofielen van **/apps** tot **/conf** en zet het metagegevensschema en de metagegevensprofielen van koraal2 om in koral3. |
| `CQ63AssetsSearchFacetsUpdate` | &lt; 6.3 | Meteen | Hiermee verplaatst u elementen en aangepaste zoekfacetten van **/apps** tot **/conf** en zet het metagegevensschema en de metagegevensprofielen van koraal2 om in koral3. |
| `CQ63InboxItemsUpgrade` | &lt; 6.3 | Meteen | Updates InboxItems voor het ordenen van items in het Postvak IN (metagegevens aanpassen voor efficiënt sorteren) |
| `CQ63MetadataSchemaConfigUpdate` | &lt; 6.3 | Meteen | Past de eigenschap metadataSchema in de map aan door relatieve paden te vervangen in **/conf** in plaats van **/apps** |
| `CQ63MobileAppsNavUpgrade` | &lt; 6.3 | Meteen | Navigatiestructuur aanpassen |
| `CQ63MonitoringDashboardsConfigUpdate` | &lt; 6.3 | Meteen | Hiermee verplaatst u aangepaste configuraties voor de monitoringdashboards van **/libs** en **/apps** |
| `CQ63ProcessingProfileConfigUpdate` | &lt; 6.3 | Meteen | Zet de processingProfile-eigenschap (gebruikt tot en met 6.1) om in Elementen, zodat deze overeenkomt met de structuur 6.3 en hoger. Hiermee past u ook de relatieve paden van het profiel aan **/conf** in plaats van **/apps**. |
| `CQ63ToolsMenuEntriesContentUpgrade` | &lt; 6.3 | Meteen | De taak van de verbetering die verouderde CRXDE Lite en het menuingangen van de Console van het Web in het geval van een verbetering verwijdert. |
| `CQ64CommunitiesConfigsCleanupTask` | &lt; 6.3 | Vertraagd | Bewegende SRP wolkenconfiguraties, de configuraties van de communautaire watchwords, ontruimt omhoog **/etc/social** en **/etc/enablement** (alle referenties en gegevens moeten worden aangepast wanneer de migratie lui wordt uitgevoerd - geen enkel toepassingsonderdeel mag meer afhankelijk zijn van deze structuur). |
| `CQ64LegacyCloudSettingsCleanupTask` | &lt; 6.4 | Vertraagd | Opschonen **/etc/cloudsettings** (die Configuratie ContextHub bevat). De configuratie wordt automatisch gemigreerd bij eerste toegang. Als de migratie van lazy-inhoud samen met de upgrade van deze inhoud is gestart in **/etc/cloudsettings** moet vóór de upgrade via een pakket worden bewaard en opnieuw worden geïnstalleerd zodat de impliciete transformatie begint, samen met het verwijderen van het pakket na voltooiing. |
| `CQ64UsersTitleFixTask` | &lt; 6.4 | Vertraagd | Past oude titelstructuur aan titel in de knoop van het gebruikersprofiel aan. |
| `CQ64CommerceMigrationTask` | &lt; 6.4 | Vertraagd | Commerciële inhoud migreren uit **/etc/commerce** tot **/var/commerce**. Tijdens migratie wordt inhoud verplaatst en worden verwijzingen naar verplaatste inhoud bijgewerkt met de nieuwe locatie. |
| `CQ65DMMigrationTask` | &lt; 6.5 | Vertraagd | Instellingen van oudere catalogi en Dynamic Media-Cloud Services migreren uit **/etc** tot **/conf** |
| `CQ65LegacyClientlibsCleanupTask` | &lt; 6.5 | Vertraagd | Oudere clientlibs opruimen die onder **/etc/clientlibs** |
