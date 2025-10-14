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

Voor meer informatie, zie de [&#x200B; Documentatie van het Dashboard van Verrichtingen &#x200B;](/help/sites-administering/operations-dashboard.md).

Er zijn drie typen opties voor het opschonen van controlelogbestanden:

1. [Pagina-auditlogboek leegmaken](/help/sites-administering/operations-audit-log.md#configure-page-audit-log-purging)
1. [DAM-controlelogbestand leegmaken](/help/sites-administering/operations-audit-log.md#configure-dam-audit-log-purging)
1. [Controlelogboek replicatie](/help/sites-administering/operations-audit-log.md#configure-replication-audit-log-purging)

Elk kan worden gevormd door regels in de Console van het AEM te creëren. Nadat zij zijn gevormd, kunt u hen teweegbrengen door naar **Hulpmiddelen - Verrichtingen - Onderhoud - het Venster van het Weekonderhoud** te gaan en de **Taak van het Onderhoud AuditLog** in werking te stellen.

## Logbestand voor controle van pagina configureren {#configure-page-audit-log-purging}

Voer de volgende stappen uit om het opschonen van controlelogbestanden te configureren:

1. Ga naar de webconsolebeheerder door uw browser naar `http://localhost:4502/system/console/configMgr/` te wijzen

1. Zoek naar een punt genoemd **de regel van de Woorden van het Logboek van de controle van Pagina&#39;s** en klik het.

   ![&#x200B; chlimage_1-365 &#x200B;](assets/chlimage_1-365.png)

1. Vervolgens configureert u de zuiveringsplanner op basis van uw vereisten. De beschikbare opties zijn:

   * **Naam van de Regel:** de naam van de regel van het controlebeleid;
   * **weg van de Inhoud:** de weg van de inhoud de regel zal toepassen op;
   * **Minimale leeftijd:** de tijd in dagen de controlelogboeken moeten worden gehouden;
   * **het logboektype van de Controle:** het type van controlelogboek dat zou moeten worden gezuiverd.

   >[!NOTE]
   >
   >Het inhoudspad is alleen van toepassing op onderliggende items van het knooppunt `/var/audit/com.day.cq.wcm.core.page` in de opslagplaats.

1. Sla de regel op.
1. De regel u creeerde moet in het Dashboard van Verrichtingen worden blootgesteld opdat het wordt uitgevoerd. Om dit te doen, ga **Hulpmiddelen - Verrichtingen - Onderhoud** van het AEM Welkome scherm.

1. Druk de **kaart van het Venster van het Weekonderhoud**.

1. U zult de onderhoudstaak reeds aanwezig onder de **kaart van het Onderhoud van AuditLog** vinden.

   ![&#x200B; chlimage_1-366 &#x200B;](assets/chlimage_1-366.png)

1. U kunt of de datum van de volgende uitvoering inspecteren, het vormen, of het manueel uitvoeren door de spelknoop te drukken.

In AEM 6.3, als het geplande onderhoudsvenster sluit alvorens de taak van het Logboek van de Controle kan voltooien, houdt de taak automatisch op. Het wordt hervat wanneer het volgende onderhoudsvenster wordt geopend.

**met AEM 6.5**, kunt u een lopende Taak van de Wrijving van het Logboek van de Controle manueel tegenhouden door het **pictogram van het Einde** te klikken. Bij de volgende uitvoering wordt de taak veilig hervat.

>[!NOTE]
>
>Om een einde te maken aan de onderhoudstaak, moet de uitvoering worden opgeschort zonder dat het spoor van de reeds in uitvoering zijnde baan verloren gaat.

## DAM-controlelogbestand opschonen {#configure-dam-audit-log-purging}

1. Navigeer aan de Console van het Systeem in *https://&lt;serveraddress>:&lt;serverport>/system/console/configMgr*
1. Onderzoek naar **DAM de regel van het de controlelogboek van het de controlelogboek zuivert** en klikt het resultaat.
1. In het volgende venster, vorm dienovereenkomstig uw regel. De opties zijn:

   * **Naam van de Regel:** de naam van de regel van het controlebeleid;
   * **weg van de Inhoud:** de weg van de inhoud de regel op zal toepassen
   * **Minimale leeftijd:** de tijd in dagen de controlelogboeken moeten worden gehouden
   * **de gebeurtenistypen van het Logboek van de Controle:** de types van de controlegebeurtenissen van DAM die zouden moeten worden gezuiverd.

1. Klik **sparen** om uw configuratie te bewaren

## Logboek voor replicatiecontrole configureren  {#configure-replication-audit-log-purging}

1. Navigeer aan de Console van het Systeem in *https://&lt;serveraddress>:&lt;serverport>/system/console/configMgr*
1. Onderzoek naar **de controleplank van het Logboek van de Replicatie** en klik het resultaat
1. In het volgende venster, vorm dienovereenkomstig uw regel. De opties zijn:

   * **Naam van de Regel:** de naam van de regel van het controlebeleid
   * **weg van de Inhoud:** de weg van de inhoud de regel op zal toepassen
   * **Minimale leeftijd:** de tijd in dagen de controlelogboeken moeten worden gehouden
   * **de gebeurtenistypen van de Replicatie van het Logboek van de Controle van de Controle:** de types van de controlegebeurtenissen van de Replicatie die zouden moeten worden ontladen

1. Klik **sparen** om uw configuratie te bewaren.
