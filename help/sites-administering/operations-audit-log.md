---
title: Onderhoud controlelogbestand in AEM 6
seo-title: Onderhoud controlelogbestand in AEM 6
description: Meer informatie over onderhoud van controlelogbestanden in AEM.
seo-description: Meer informatie over onderhoud van controlelogbestanden in AEM.
uuid: 212de4df-6bf4-434c-94e1-74186d21945a
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: operations
content-type: reference
discoiquuid: 565d89de-b3ca-41a5-8e1c-d10905c25fb5
translation-type: tm+mt
source-git-commit: 2fc35bfd93585a586cb1d4e3299261611db49ba6
workflow-type: tm+mt
source-wordcount: '615'
ht-degree: 0%

---


# Onderhoud controlelogbestand in AEM 6{#audit-log-maintenance-in-aem}

AEM gebeurtenissen die in aanmerking komen voor accountlogboekregistratie, genereren veel gearchiveerde gegevens. Deze gegevens kunnen na verloop van tijd snel groeien als gevolg van replicaties, het uploaden van bedrijfsmiddelen en andere systeemactiviteiten.

Het onderhoud van het controlelogboek omvat verscheidene delen van functionaliteit die de capaciteit toelaat om het onderhoud van het controlelogboek onder specifiek beleid te automatiseren.

Het wordt uitgevoerd als configureerbare wekelijkse onderhoudstaak en is toegankelijk via de de monitorconsole van het Dashboard van Verrichtingen.

Raadpleeg de [Documentatie van het werkgebied](/help/sites-administering/operations-dashboard.md) voor meer informatie.

Er zijn drie typen opties voor het opschonen van controlelogbestanden:

1. [Pagina-auditlogboek leegmaken](/help/sites-administering/operations-audit-log.md#configure-page-audit-log-purging)
1. [DAM-controlelogbestand leegmaken](/help/sites-administering/operations-audit-log.md#configure-dam-audit-log-purging)
1. [Controlelogboek replicatie](/help/sites-administering/operations-audit-log.md#configure-replication-audit-log-purging)

Elk kan worden gevormd door regels in de Console van het AEM te creëren. Nadat zij zijn gevormd, kunt u hen teweegbrengen door naar **Hulpmiddelen - Verrichtingen - Onderhoud te gaan - Wekelijks Onderhoudsvenster** en de **Taak van het Onderhoud van AuditLog** in werking te stellen.

## Logbestand voor controle van pagina configureren {#configure-page-audit-log-purging}

Voer de volgende stappen uit om het opschonen van controlelogbestanden te configureren:

1. Ga naar de webconsolebeheerder door uw browser naar `http://localhost:4502/system/console/configMgr/` te verwijzen

1. Zoek naar een punt genoemd **Pagina&#39;s controlelogboek zuiveringsregel** en klik het.

   ![chlimage_1-365](assets/chlimage_1-365.png)

1. Vervolgens configureert u de zuiveringsplanner volgens uw vereisten. De beschikbare opties zijn:

   * **Regelnaam:** de naam van de regel van het controlebeleid;
   * **Inhoudspad:** het pad van de inhoud waarop de regel van toepassing is;
   * **minimumleeftijd:** de tijd in dagen die de auditlogs moeten worden bewaard;
   * **Type controlelogboek:** het type controlelogboek dat zou moeten worden gezuiverd.

   >[!NOTE]
   >
   >Het inhoudspad is alleen van toepassing op onderliggende knooppunten van het knooppunt `/var/audit/com.day.cq.wcm.core.page` in de opslagplaats.

1. Sla de regel op.
1. De regel u enkel creeerde moet in het Dashboard van Verrichtingen worden blootgesteld opdat het wordt uitgevoerd. Om dit te doen, ga **Hulpmiddelen - Verrichtingen - Onderhoud** van het AEM Welkome scherm.

1. Druk op de **Wekelijkse onderhoudskaart**.

1. U zult de onderhoudstaak vinden die reeds onder **de Taak van het Onderhoud van AuditLog** kaart aanwezig is.

   ![chlimage_1-366](assets/chlimage_1-366.png)

1. U kunt of de datum van de volgende uitvoering inspecteren, het vormen, of het manueel uitvoeren door de spelknoop te drukken.

In AEM 6.3, als het geplande onderhoudsvenster sluit alvorens de taak van het Logboek van de Controle kan voltooien, houdt de taak automatisch op. Het wordt hervat wanneer het volgende onderhoudsvenster wordt geopend.

**Met AEM 6.5**, kunt u een lopende Taak van de Wrijving van het Logboek van de Controle manueel tegenhouden door de  **** Stopicon te klikken. Bij de volgende uitvoering wordt de taak veilig hervat.

>[!NOTE]
>
>Om een einde te maken aan de onderhoudstaak, moet de uitvoering worden opgeschort zonder dat het spoor van de reeds in uitvoering zijnde baan verloren gaat.

## Fouten in DAM-controlelogbestand {#configure-dam-audit-log-purging} configureren

1. Navigeer naar de systeemconsole op *https://&lt;serveradres>:&lt;serverport>/system/console/configMgr*
1. Zoek naar **DAM de regel van het controlelogboek zuiveren** en klik het resultaat.
1. In het volgende venster, vorm dienovereenkomstig uw regel. De opties zijn:

   * **Regelnaam:** de naam van de regel van het controlebeleid;
   * **Inhoudspad:** het pad van de inhoud waarop de regel wordt toegepast
   * **Minimumleeftijd:** de tijd in dagen dat de auditlogs moeten worden bewaard
   * **De gebeurtenistypen van het Logboek van** de controle:de types van DMA controlegebeurtenissen die zouden moeten worden gezuiverd.

1. Klik **Opslaan** om uw configuratie op te slaan

## Logbestand voor replicatiecontrole configureren {#configure-replication-audit-log-purging}

1. Navigeer naar de systeemconsole op *https://&lt;serveradres>:&lt;serverport>/system/console/configMgr*
1. Zoeken naar **Replication audit Log Purge Scheduler** en klikken op het resultaat
1. In het volgende venster, vorm dienovereenkomstig uw regel. De opties zijn:

   * **Regelnaam:** de naam van de regel van het controlebeleid
   * **Inhoudspad:** het pad van de inhoud waarop de regel wordt toegepast
   * **Minimumleeftijd:** de tijd in dagen dat de auditlogs moeten worden bewaard
   * **De gebeurtenistypen van** de Replicatie van het logboek van de controle:de types van de controlegebeurtenissen van de Replicatie die zouden moeten worden gezuiverd

1. Klik **sparen** om uw configuratie te bewaren.

