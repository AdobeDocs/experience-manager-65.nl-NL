---
title: Aan de slag met Process Reporting
description: De stappen om aan de slag te gaan met AEM Forms over JEE Process Reporting
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: process-reporting
docset: aem65
exl-id: 1272e854-fa64-4bfd-b073-8fbcf210e9b5
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
role: User, Developer
source-git-commit: e821be5233fd5f6688507096790d219d25903892
workflow-type: tm+mt
source-wordcount: '1706'
ht-degree: 0%

---

# Aan de slag met Process Reporting{#getting-started-with-process-reporting}

De Rapportering van het proces geeft de gebruikers van AEM Forms de capaciteit om informatie over de processen van AEM Forms te vragen die momenteel in de implementatie van AEM Forms worden bepaald. Procesrapportage heeft echter niet rechtstreeks toegang tot gegevens van de AEM Forms-opslagplaats. Het gegeven wordt eerst gepubliceerd aan het Proces dat bewaarplaats op een geplande basis meldt (*door de dienst ProcessDataPublisher &amp; ProcessDataStorage* s). De rapporten en vragen in de Rapportering van het Proces worden dan geproduceerd uit het Proces Meldend gegevens die aan de bewaarplaats worden gepubliceerd. De Rapportering van het proces is geïnstalleerd als deel van de module van de Forms Workflow.

In dit artikel worden de stappen beschreven die het publiceren van AEM Forms-gegevens naar de Process Reporting repository mogelijk maken. Daarna, zult u het Rapport van het Proces kunnen gebruiken om rapporten en vragen in werking te stellen. Het artikel behandelt ook de opties beschikbaar om de diensten van de Rapportering van het Proces te vormen.

## Voorwaarden voor procesrapportage {#process-reporting-pre-requisites}

### Niet-essentiële processen zuiveren {#purge-non-essential-processes}

Als u momenteel Forms Workflow gebruikt, kan de AEM Forms-database mogelijk een grote hoeveelheid gegevens bevatten

Met de publicatieservices Process Reporting worden alle AEM Forms-gegevens gepubliceerd die momenteel in de database beschikbaar zijn. Het impliceert dat als het gegevensbestand erfenisgegevens bevat waarover u geen rapporten en vragen wilt in werking stellen, al die gegevens ook aan de bewaarplaats zouden worden gepubliceerd hoewel het niet voor rapportering wordt vereist. U wordt aangeraden deze gegevens te wissen voordat u de services uitvoert om de gegevens naar de Process Reporting-opslagplaats te publiceren. Dit verbetert de prestaties van zowel de uitgeversdienst als de dienst die de gegevens voor rapportering vraagt.

Voor details bij het zuiveren van het procesgegevens van AEM Forms, zie [ het Schrappen Gegevens van het Proces ](/help/forms/using/admin-help/purging-process-data.md).

>[!NOTE]
>
>Voor de uiteinden en de trucs van het Nut van de Zuivering, zie het artikel van Adobe Developer Connection op [ het Schrappen processen en banen ](/help/forms/using/admin-help/purging-process-data.md).

## Services voor Process Reporting configureren {#configuring-process-reporting-services}

### Publiceren van procesgegevens plannen {#schedule-process-data-publishing}

De Process Reporting Services publiceren op geregelde basis gegevens van de AEM Forms-database naar de Process Reporting repository.

Deze bewerking kan bronintensief zijn en de prestaties van de AEM Forms-servers beïnvloeden. U wordt aangeraden dit buiten de bezige tijdsleuven van de AEM Forms-server te plannen.

Door gebrek, is het publiceren van gegevens planning om elke dag om 2:00 uur in werking te stellen.

Voer de volgende stappen uit om het publicatieschema te wijzigen:

>[!NOTE]
>
>Als u uw AEM Forms-implementatie uitvoert in een cluster, voert u de volgende stappen uit op elk knooppunt van de cluster.

1. Stop de AEM Forms Server-instantie.
1. &#x200B;

   * (Voor Windows) Open het `[JBoss root]/bin/run.conf.bat` -bestand in een editor.
   * (Voor Linux®, AIX® en Solaris™) `[JBoss root]/bin/run.conf.sh` in een editor.

1. Het JVM-argument toevoegen `-Dreporting.publisher.cron = <expression>.`

   Voorbeeld: met de volgende uitsnijdexpressie worden bij Process Reporting om de vijf uur AEM Forms-gegevens naar de Process Reporting repository gepubliceerd:

   * `-Dreporting.publisher.cron = 0_0_0/5_*_*_?`

1. Sla het `run.conf.bat` -bestand op en sluit het.

1. Start de AEM Forms Server-instantie opnieuw.

1. Stop de AEM Forms Server-instantie.
1. Meld u aan bij de beheerconsole van WebSphere®. In de navigatieboom, klik **Servers** > **de servers van de Toepassing** en dan, in de juiste ruit, klik de servernaam.

1. Onder de Infrastructuur van de Server, klik **Java™ en het Beheer van het Proces** > **Definitie van het Proces**.

1. Onder Extra Eigenschappen, klik **Virtuele Machine Java™**.

   Voeg het argument toe in het vak Generic JVM-argumenten `-Dreporting.publisher.cron = <expression>.`

   **Voorbeeld**: De volgende kroonuitdrukking veroorzaakt het Rapport van het Proces om de gegevens van AEM Forms aan de Opslagplaats van de Rapportering van het Proces om de vijf uur te publiceren:

   * `-Dreporting.publisher.cron = 0_0_0/5_*_*_?`

1. Klik **toepassen**, klik O.K., en klik dan **direct sparen aan de hoofdconfiguratie**.
1. Start de AEM Forms Server-instantie opnieuw.
1. Stop de AEM Forms Server-instantie.
1. Meld u aan bij de WebLogic-beheerconsole. Het standaardadres van de WebLogic-beheerconsole is `https://[hostname]:[port]/console` .
1. Onder het Centrum van de Verandering, klik **Slot &amp; geef** uit.
1. Onder de Structuur van het Domein, klik **Milieu** > **Servers** en, in de juiste ruit, klik de beheerde servernaam.
1. Voor het volgende scherm, klik het **lusje van de Configuratie** {> **Begin van de Server** tabel.
1. Voeg in het vak Argumenten het JVM-argument `-Dreporting.publisher.cron = <expression>` toe.

   **Voorbeeld**: De volgende kroonuitdrukking veroorzaakt het Rapport van het Proces om de gegevens van AEM Forms aan de Opslagplaats van de Rapportering van het Proces om de vijf uur te publiceren:

   `-Dreporting.publisher.cron = 0_0_0/5_*_*_?`

1. Klik **sparen** en klik dan **activeren Veranderingen**.
1. Start de AEM Forms Server-instantie opnieuw.

![ verwerkdatapublisherservice ](assets/processdatapublisherservice.png)

>[!NOTE]
>
> Het wordt aanbevolen de SDK opnieuw te starten met de opdracht &#39;Ctrl + C&#39;. Het opnieuw opstarten van de AEM SDK met behulp van alternatieve methoden, bijvoorbeeld het stoppen van Java-processen, kan leiden tot inconsistenties in de AEM ontwikkelomgeving.

### Procesgegevensopslagservice {#processdatastorage-service}

De dienst ProcessDataStorageProvider ontvangt procesgegevens van de dienst ProcessDataPublisher en bewaart de gegevens aan de bewaarplaats van de Rapportering van het Proces.

Bij elke publicatiecyclus worden de gegevens opgeslagen in submappen van een vooraf gedefinieerde hoofdmap.

U kunt de console van het Beleid gebruiken om de wortel (**gebrek** te vormen: `/content/reporting/pm`) plaats en subfolder (**gebrek**: `/yyyy/mm/dd/hh/mi/ss`) hiërarchieformaat waar de procesgegevens zouden worden opgeslagen.

#### De locaties van de Process Reporting repository configureren {#to-configure-the-process-reporting-repository-locations}

1. Login aan **Console van het Beleid** met beheerdergeloofsbrieven. De standaard-URL van de beheerconsole is `https://'[server]:[port]'/adminui`
1. Navigeer aan **Huis** > **de Diensten** > **Toepassingen en de Diensten** > **het Beheer van de Dienst** en open de **dienst ProcessDataStorageProvider**.

   ![ proces-gegeven-opslag-dienst ](assets/process-data-storage-service.png)

   **RootFolder**

   De CRX-locatie waar de procesgegevens voor rapportage worden opgeslagen.

   `Default`: `/content/reporting/pm`

   **Hiërarchie van de Omslag**

   De mappenhiërarchie waarin de procesgegevens worden opgeslagen op basis van de aanmaaktijd van het proces.

   `Default`: `/yyyy/mm/dd/hh/mi/ss`

1. Klik **sparen**.

### ReportConfiguration-service {#reportconfiguration-service}

De dienst ReportConfiguration wordt gebruikt door Proces dat voor het vormen van het proces meldt de vraagdienst.

#### Om de dienst te vormen ReportingConfiguration {#to-configure-the-reportingconfiguration-service}

1. Login aan **Manager van de Configuratie** met de beheerdergeloofsbrieven van CRX. De standaard-URL van Configuration Manager is `https://'[server]:[port]'/lc/system/console/configMgr`
1. Open de **ReportingConfiguration** dienst.
1. **Aantal Verslagen**

   Wanneer het runnen van een vraag op de bewaarplaats, kan een resultaat vele verslagen potentieel bevatten. Als de resultaatreeks groot is, kan de vraaguitvoering servermiddelen verbruiken.

   Om grote resultaatsets te behandelen, splitst de dienst ReportConfiguration de vraagverwerking in partijen verslagen. Dit vermindert de belasting van het systeem.

   `Default`: `1000`

   **de Weg van de Opslag van CRX**

   De CRX-locatie waarin de procesgegevens moeten worden opgeslagen voor rapportage.

   `Default`: `/content/reporting/pm`

   >[!NOTE]
   >
   >Deze plaats is het zelfde zoals die in de de configuratieoptie van ProcessDataStorage **de Omslag van de Wortel** wordt gespecificeerd.
   >
   >
   >Als u de optie van de Omslag van de Wortel in de configuratie ProcessDataStorage bijwerkt, moet u de plaats van de Weg van de Opslag van CRX in de dienst ReportConfiguration bijwerken.

1. Klik **sparen** en sluit **Manager van de Configuratie CQ**.

### ProcessDataPublisher-service {#processdatapublisher-service}

De service ProcessDataPublisher importeert procesgegevens uit de AEM Forms-database en publiceert de gegevens naar de ProcessDataStorageProvider-service voor opslag.

#### De service ProcessDataPublisher configureren   {#to-configure-processdatapublisher-service-nbsp}

1. Login aan **Console van het Beleid** met beheerdergeloofsbrieven.

   De standaard-URL is `https://'server':port]/adminui/` .

1. Navigeer aan **Huis** > **de Diensten** > **Toepassingen en de Diensten** > **het Beheer van de Dienst** en open de **ProcessDataPublisher** dienst.

![ verwerkdatapublisherservice-1 ](assets/processdatapublisherservice-1.png)

**Gegevens van Publish**

Schakel deze optie in om te beginnen met het publiceren van procesgegevens. De optie is standaard uitgeschakeld.

Schakel Process Reporting alleen in als alle configuraties met betrekking tot Process Reporting-componenten op de juiste wijze zijn ingesteld.

U kunt deze optie ook gebruiken om het publiceren van procesgegevens uit te schakelen wanneer dit niet langer verplicht is.

`Default`: `Off`

**Interval van de Partij (sec)**

Telkens als de dienst ProcessDataPublisher loopt, verdeelt de dienst eerst de tijd sinds de laatste looppas van de dienst door het Interval van de Partij. De dienst verwerkt dan elk interval van de gegevens van AEM Forms afzonderlijk om de grootte van gegevens te controleren de uitgever van begin tot eind tijdens elke looppas (partij) binnen een cyclus verwerkt.

Bijvoorbeeld, als de uitgever elke dag in werking stelt, dan in plaats van het verwerken van de volledige gegevens één dag in één enkele looppas, door gebrek, wordt het de verwerking in 24 partijen van elk één uur verdeeld.

`Default`: `3600`

`Unit`: `Seconds`

**Onderbreking van het Slot (sec)**

De uitgeversservice verkrijgt een vergrendeling wanneer de verwerking van gegevens wordt gestart, zodat meerdere exemplaren van de uitgever niet gelijktijdig met het uitvoeren en verwerken van gegevens beginnen.

Als een uitgeversdienst die een slot heeft verworven, nutteloos voor het aantal seconden is die door de waarde van de Onderbreking van het Slot wordt bepaald, dan wordt zijn slot vrijgegeven zodat andere instanties van de uitgeversdienst kunnen blijven verwerken.

`Default`: `3600`

`Unit`: `Seconds`

**de Gegevens van Publish van**

De AEM Forms-omgeving bevat gegevens uit de tijd dat de omgeving werd ingesteld.

Standaard importeert de ProcessDataPublisher-service alle gegevens uit de AEM Forms-database.

Afhankelijk van uw rapporteringsbehoeften, als u van plan bent om rapporten en vragen over gegevens na een bepaalde datum en een tijd in werking te stellen, adviseert men dat u de datum en de tijd specificeert. De publicatieservice publiceert vervolgens de datum vanaf die tijd.

`Default`: `01-01-1970 00:00:00`

`Format`: `dd-MM-yyyy HH:mm:ss`

## Toegang tot de gebruikersinterface Process Reporting {#accessing-the-process-reporting-user-interface}

De gebruikersinterface voor Process Reporting is browsergebaseerd.

Nadat u Procesrapportage hebt ingesteld, kunt u beginnen te werken met Process Reporting op de volgende locatie in uw AEM Forms-installatie:

`https://<server>:<port>/lc/pr`

### Aanmelden bij procesrapportage {#log-in-to-process-reporting}

Wanneer u naar de URL voor Process Reporting (https://&lt;server>:&lt;port>/lc/pr) navigeert, wordt het aanmeldingsscherm weergegeven.

Om aan login aan de module van de Rapportering van het Proces, specificeer uw geloofsbrieven.

>[!NOTE]
>
>Als u zich wilt aanmelden bij de gebruikersinterface Process Reporting, hebt u de volgende AEM Forms-machtiging nodig:
>
>`PERM_PROCESS_REPORTING_USER`

![ Login aan Proces Meldend ](assets/capture1_new.png)

Wanneer u zich aanmeldt bij Process Reporting, wordt het scherm **[!UICONTROL Home]** weergegeven.

### Process Reporting Home-scherm {#process-reporting-home-screen}

![ proces-rapporterend-huis-scherm ](assets/process-reporting-home-screen.png)

**Proces Meldend boommening:** de boommening op de linkerkant van het scherm van het Huis bevat de punten voor het Proces Meldend modules.

De boomstructuurweergave bestaat uit de volgende items op hoofdniveau:

**Rapporten:** Dit punt bevat de uit-van-de-doos rapporten die met het Melden van het Proces verschepen.

Voor details op de vooraf bepaalde rapporten, zie [ Vooraf bepaalde Rapporten in Proces Meldend ](/help/forms/using/process-reporting/pre-defined-reports-in-process-reporting.md).

**Adhoc Vragen:** Dit punt bevat opties om op filter-gebaseerd onderzoek naar processen en taken uit te voeren.

Voor details op ad-hoc vragen, zie [ Ad-hoc Vragen in Proces Meldend ](/help/forms/using/process-reporting/adhoc-queries-in-process-reporting.md).

**Douane:** de knoopvertoningen van de Douane douanerapporten die u creeert.

Voor de procedure om douanerapporten tot stand te brengen en te tonen, zie [ de Rapporten van de Douane in Proces Meldend ](/help/forms/using/process-reporting/process-reporting-custom-reports.md).

**Proces Meldend titelbar:** de bar van de Titel van het Rapport van het Proces bevat sommige generische opties die u kunt gebruiken wanneer het werken in het gebruikersinterface.

**Meldende titel van het Proces:** De de titelvertoningen van de Rapportering van het Proces op de linkerhoek van de titelbar.

Klik op de titel om terug te keren naar het scherm Home.

**Laatste Tijd van de Update:** De procesgegevens worden gepubliceerd van het gegevensbestand van AEM Forms aan de Opslagplaats van de Rapportering van het Proces op een geplande basis.

De laatste tijd van de Update toont de laatste datum en de tijd tot waarvan de gegevensupdates aan de bewaarplaats van de Rapportering van het Proces werden geduwd.

Voor details op de gegevens het publiceren dienst en hoe te om deze dienst te plannen, zie [ het procesgegevens van het Programma het publiceren ](/help/forms/using/process-reporting/install-start-process-reporting.md#p-schedule-process-data-publishing-p) in het artikel dat met het Melden van het Proces begonnen wordt.

**Proces Meldend gebruiker:** de het programma geopende vertoningen van de gebruikersnaam rechts van de Laatste tijd van de Update.

**Proces Meldend titelbar drop-down lijst:** de drop-down lijst bij de juiste hoek van de de titelbar van de Rapportering van het Proces bevat de volgende opties:

* **[!UICONTROL Sync]**: Synchroniseer de ingesloten Process Reporting-opslagplaats met de AEM Forms-database.
* **[!UICONTROL Help]**: bekijk de Help-documentatie over Process Reporting.
* **[!UICONTROL Logout]**: Afmelden van procesrapportage


