---
title: Onderhoud controlelogbestand in AEM 6
description: Meer informatie over het onderhoud van controlelogbestanden in Adobe Experience Manager (AEM).
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: operations
content-type: reference
exl-id: 1e05faf5-619a-4ea3-acbf-2fd37c71e6d2
feature: Operations
solution: Experience Manager, Experience Manager Sites
role: Admin
source-git-commit: 48d12388d4707e61117116ca7eb533cea8c7ef34
workflow-type: tm+mt
source-wordcount: '605'
ht-degree: 0%

---

# Onderhoud controlelogbestand in AEM 6{#audit-log-maintenance-in-aem}

AEM gebeurtenissen die in aanmerking komen voor accountlogboekregistratie, genereren veel gearchiveerde gegevens. Deze gegevens kunnen na verloop van tijd snel groeien als gevolg van replicaties, het uploaden van bedrijfsmiddelen en andere systeemactiviteiten.

Het onderhoud van het controlelogboek omvat verscheidene delen van functionaliteit die de capaciteit toelaat om het onderhoud van het controlelogboek onder specifiek beleid te automatiseren.

Het wordt uitgevoerd als configureerbare wekelijkse onderhoudstaak en is toegankelijk via de de monitorconsole van het Dashboard van Verrichtingen.

Zie de klasse [Documentatie van het bewerkingsdashboard](/help/sites-administering/operations-dashboard.md).

Er zijn drie typen opties voor het opschonen van controlelogbestanden:

1. [Pagina-auditlogboek leegmaken](/help/sites-administering/operations-audit-log.md#configure-page-audit-log-purging)
1. [DAM-controlelogbestand leegmaken](/help/sites-administering/operations-audit-log.md#configure-dam-audit-log-purging)
1. [Controlelogboek replicatie](/help/sites-administering/operations-audit-log.md#configure-replication-audit-log-purging)

Elk kan worden gevormd door regels in de Console van het AEM te creëren. Nadat zij zijn gevormd, kunt u hen teweegbrengen door naar te gaan **Gereedschappen - Bewerkingen - Onderhoud - Wekelijks venster Onderhoud** en de **AuditLog-onderhoudstaak**.

## Logbestand voor controle van pagina configureren {#configure-page-audit-log-purging}

Voer de volgende stappen uit om het opschonen van controlelogbestanden te configureren:

1. Ga naar de webconsolebeheerder door uw browser naar `http://localhost:4502/system/console/configMgr/`

1. Zoeken naar een opgevraagd item **Regel voor het verwijderen van controlelogbestanden voor pagina&#39;s** en klik erop.

   ![chlimage_1-365](assets/chlimage_1-365.png)

1. Vervolgens configureert u de zuiveringsplanner op basis van uw vereisten. De beschikbare opties zijn:

   * **Naam regel:** de naam van de regel inzake controlebeleid;
   * **Inhoudspad:** het pad van de inhoud waarop de regel van toepassing is;
   * **Minimumleeftijd:** de tijd in dagen waarop de auditlogs moeten worden bewaard;
   * **Type controlelogboek:** het type controlelogboek dat moet worden gezuiverd.

   >[!NOTE]
   >
   >Het inhoudspad is alleen van toepassing op onderliggende elementen van het dialoogvenster `/var/audit/com.day.cq.wcm.core.page` in de repository.

1. Sla de regel op.
1. De regel u creeerde moet in het Dashboard van Verrichtingen worden blootgesteld opdat het wordt uitgevoerd. Ga als volgt te werk om dit te doen **Gereedschappen - Operaties - Onderhoud** in het welkomstscherm AEM.

1. Druk op **Wekelijks onderhoudvenster** kaart.

1. U zult de onderhoudstaak vinden die reeds onder **AuditLog-onderhoudstaak** kaart.

   ![chlimage_1-366](assets/chlimage_1-366.png)

1. U kunt of de datum van de volgende uitvoering inspecteren, het vormen, of het manueel uitvoeren door de spelknoop te drukken.

In AEM 6.3, als het geplande onderhoudsvenster sluit alvorens de taak van het Logboek van de Controle kan voltooien, houdt de taak automatisch op. Het wordt hervat wanneer het volgende onderhoudsvenster wordt geopend.

**Met AEM 6.5**, kunt u een actieve Taak van de Weigering van het Logboek van de Controle manueel tegenhouden door te klikken **Stoppen** pictogram. Bij de volgende uitvoering wordt de taak veilig hervat.

>[!NOTE]
>
>Om een einde te maken aan de onderhoudstaak, moet de uitvoering worden opgeschort zonder dat het spoor van de reeds in uitvoering zijnde baan verloren gaat.

## DAM-controlelogbestand opschonen {#configure-dam-audit-log-purging}

1. Ga naar de systeemconsole op *https://&lt;serveraddress>:&lt;serverport>/system/console/configMgr*
1. Zoeken naar **DAM-controlelogbestand leegmaken** en klik op het resultaat.
1. In het volgende venster, vorm dienovereenkomstig uw regel. De opties zijn:

   * **Naam regel:** de naam van de regel inzake controlebeleid;
   * **Inhoudspad:** het pad van de inhoud waarop de regel van toepassing is
   * **Minimumleeftijd:** de tijd in dagen dat de auditlogboeken moeten worden bewaard
   * **Typen auditlogbestandgebeurtenissen:** de typen DAM-auditgebeurtenissen die moeten worden gewist.

1. Klikken **Opslaan** om uw configuratie te bewaren

## Logboek voor replicatiecontrole configureren  {#configure-replication-audit-log-purging}

1. Ga naar de systeemconsole op *https://&lt;serveraddress>:&lt;serverport>/system/console/configMgr*
1. Zoeken naar **Replicatieauditlogboek leegmaken planner** en klik op het resultaat
1. In het volgende venster, vorm dienovereenkomstig uw regel. De opties zijn:

   * **Naam regel:** de naam van de regel van het controlebeleid
   * **Inhoudspad:** het pad van de inhoud waarop de regel van toepassing is
   * **Minimumleeftijd:** de tijd in dagen dat de auditlogboeken moeten worden bewaard
   * **Gebeurtenistypen van het Logboek van de controle:** de soorten de controlegebeurtenissen van de Replicatie die zouden moeten worden gezuiverd

1. Klikken **Opslaan** om uw configuratie op te slaan.
