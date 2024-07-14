---
title: Lazy Content Migration
description: Meer informatie over Lazy Content Migration in Adobe Experience Manager 6.4.
contentOwner: sarchiz
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: upgrading
docset: aem65
feature: Upgrading
exl-id: 946c7c2a-806b-4461-a38b-9c2e5ef1e958
solution: Experience Manager, Experience Manager Sites
role: Admin
source-git-commit: 48d12388d4707e61117116ca7eb533cea8c7ef34
workflow-type: tm+mt
source-wordcount: '693'
ht-degree: 0%

---

# Lazy Content Migration {#lazy-content-migration}

Voor achterwaartse verenigbaarheid, zullen de inhoud en de configuratie in **/etc** en **/content** die met Adobe Experience Manager (AEM) beginnen 6.3 niet onmiddellijk met de verbetering worden aangeraakt of worden getransformeerd. Dit wordt gedaan om ervoor te zorgen dat de gebiedsdelen van klantentoepassingen op die structuren intact blijven. De functionaliteit met betrekking tot deze inhoudsstructuren is nog steeds hetzelfde, ook al wordt de inhoud in een gedeelte van het vak AEM 6.5 op een andere plaats gehost.

Niet al deze locaties kunnen automatisch worden getransformeerd, maar er zijn een paar vertraagde `CodeUpgradeTasks` die ook wel Lazy Content Migration wordt genoemd. Hierdoor kunnen klanten deze automatische transformaties activeren door de instantie opnieuw te starten met deze systeemeigenschap:

```shell
-Dcom.adobe.upgrade.forcemigration=true
```

Hierdoor wordt `CodeUpgradeTasks` tijdens de migratie uitgevoerd.

Hoewel het doel een efficiënte uitvoering is, is dit upgradeproces synchroon en heeft het daarom een downtime afhankelijk van de hoeveelheid inhoud die moet worden verwerkt. De Adobe beveelt aan om de uitvoeringstijden in een gefaseerde omgeving vóór een productiesysteem te evalueren om een onderhoudsvenster te plannen.

Aangezien dit typisch ook het aanpassen van toepassing vereist, zou deze activiteit samen met de overeenkomstige toepassingsplaatsing moeten worden uitgevoerd.

Hieronder ziet u de volledige lijst met `CodeUpgradeTasks` die in 6.5 is geïntroduceerd:

| **Naam** | **Relevant** **voor AEM versies vóór** | **Migratie** **Type** | **Details** |
|---|---|---|---|
| `Cq561ProjectContentUpgrade` | &lt; 5.6.1 | Meteen |  |
| `Cq60MSMContentUpgrade` | &lt; 6,0 | Meteen | Detecteert alle `LiveRelationShips` uit `VersionStorage` die zijn verwijderd en uitsluitingseigenschappen aan het bovenliggende element toevoegen |
| `Cq61CloudServicesContentUpgrade` | &lt; 6,1 | Meteen | Hiermee herstructureert u cloudservices voor beveiligen door standaardinstelling |
| `Cq62ConfContentUpgrade` | &lt; 6,2 | Meteen | Verwijdert bezit gebaseerd het verbinden van **/content** aan **/conf** (die door het mechanisme OSGi wordt vervangen), produceert overeenkomstige configuratie OSGi |
| `Cq62FormsContentUpgrade` | &lt; 6,2 | Meteen | wegens merge_preserve behandeling, ontkent veilig door gebrek regel met voeten treedt gegeven toestemmingen die tot de behoefte leiden om op verbetering opnieuw in orde te brengen |
| `CQ62Html5SmartFileUpgrade` | &lt; 6,2 | Meteen | Detecteert componenten met behulp van de widget HTML5SmartFile, zoekt naar gebruik van de component in de inhoud en herstructureert de persistentie, waardoor het binaire niveau lager wordt en niet op componentniveau wordt opgeslagen. |
| `Cq62ProjectsCodeUpgrade` | &lt; 6,2 | Meteen | Verplaatst oude stijlprojecten van **/etc/projects** naar **/content/projects** |
| `Cq62TargetCampaignsContentUpgrade` | &lt; 6,2 | Meteen | Introduceert een containerlaag tot hiërarchie (Gebieden) en past verwijzingen aan. |
| `Cq62TargetContentUpgrade` | &lt; 6,2 | Meteen | Stelt vaste locatienamen in op doelcomponenten. |
| `Cq62WorkflowContentUpgrade` | &lt; 6,2 | Meteen | Complexe transformatie van workflowmodellen die ouder zijn dan 6.2 structuren, instanties, meldingen en vervolgens teruggaan van de back-uplocatie vanuit **/var/backup** |
| `CQ63AssetsMetadataFormsUpdate` | &lt; 6,3 | Meteen | Verplaatst activa, schema&#39;s van douanemetagegevens, en verwerkingsprofielen van **/apps** naar **/conf** en vertaalt de vormen van het meta-gegevensschema en van meta-gegevensprofielen van koral2 aan koral3. |
| `CQ63AssetsSearchFacetsUpdate` | &lt; 6,3 | Meteen | Verplaatst elementen en de facetten van het douaneonderzoek van **/apps** naar **/conf** en vertaalt de vormen van het meta-gegevensschema en van meta-gegevensprofielen van koral2 aan koral3. |
| `CQ63InboxItemsUpgrade` | &lt; 6,3 | Meteen | Updates InboxItems voor het ordenen van items in het Postvak IN (metagegevens aanpassen voor efficiënt sorteren) |
| `CQ63MetadataSchemaConfigUpdate` | &lt; 6,3 | Meteen | Past het metadataSchema bezit op omslag door relatieve wegen aan **/conf** in plaats van **te vervangen/apps** |
| `CQ63MobileAppsNavUpgrade` | &lt; 6,3 | Meteen | Navigatiestructuur aanpassen |
| `CQ63MonitoringDashboardsConfigUpdate` | &lt; 6,3 | Meteen | Verplaatst douaneconfiguraties voor de controledashboards van **/libs** en **/apps** |
| `CQ63ProcessingProfileConfigUpdate` | &lt; 6,3 | Meteen | Zet de processingProfile-eigenschap (gebruikt tot en met 6.1) in Assets om deze aan te passen aan de structuur 6.3 en hoger. Past ook de relatieve wegen van het profiel aan **/conf** in plaats van **/apps** aan. |
| `CQ63ToolsMenuEntriesContentUpgrade` | &lt; 6,3 | Meteen | De taak van de verbetering die verouderde CRXDE Lite en het menuingangen van de Console van het Web verwijdert als er een verbetering is. |
| `CQ64CommunitiesConfigsCleanupTask` | &lt; 6,3 | Uitgesteld | Bewegend SRP wolkenconfiguraties, de configuraties van de communautaire watchwords, schoonmaakt omhoog **/etc/social** en **/etc/enablement** (om het even welke verwijzingen en gegevens moeten worden aangepast wanneer de luie migratie wordt in werking gesteld - geen toepassingsdeel zou afhankelijk van deze structuur meer moeten zijn). |
| `CQ64LegacyCloudSettingsCleanupTask` | &lt; 6,4 | Uitgesteld | Maakt **/etc/cloudsettings** (die Configuratie ContextHub bevatten) op. De configuratie wordt automatisch gemigreerd bij eerste toegang. Als Lazy Content Migration wordt gestart samen met een upgrade van deze inhoud in **/ etc/cloudsettings** , moet deze inhoud worden behouden via pakket voordat de upgrade wordt uitgevoerd en opnieuw worden geïnstalleerd voordat de impliciete transformatie wordt gestart, samen met een volgende verwijdering van het pakket na voltooiing. |
| `CQ64UsersTitleFixTask` | &lt; 6,4 | Uitgesteld | Past oude titelstructuur aan titel in de knoop van het gebruikersprofiel aan. |
| `CQ64CommerceMigrationTask` | &lt; 6,4 | Uitgesteld | Migreer commerciële inhoud van **/etc/commerce** aan **/var/commerce**. Tijdens migratie wordt inhoud verplaatst en worden verwijzingen naar verplaatste inhoud bijgewerkt met de nieuwe locatie. |
| `CQ65DMMigrationTask` | &lt; 6,5 | Uitgesteld | De instellingen van de oude catalogus en de Dynamic Media-Cloud Servicen migreren van **/etc** naar **/conf** |
| `CQ65LegacyClientlibsCleanupTask` | &lt; 6,5 | Uitgesteld | Oudere clientlibs opruimen die onder **/etc/clientlibs** bestaan |
