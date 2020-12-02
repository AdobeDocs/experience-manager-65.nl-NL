---
title: Aan de slag met Process Reporting
seo-title: Aan de slag met Process Reporting
description: De stappen die u moet volgen om aan de slag te gaan met AEM Forms over JEE Process Reporting
seo-description: De stappen die u moet volgen om aan de slag te gaan met AEM Forms over JEE Process Reporting
uuid: 685cad39-da2c-411d-a0b0-201917438bcf
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: process-reporting
discoiquuid: 7c1fcde0-b983-4b24-bc19-fcee1d4f096b
docset: aem65
translation-type: tm+mt
source-git-commit: 56c6cfd437ef185336e81373bd5f758205b96317
workflow-type: tm+mt
source-wordcount: '1727'
ht-degree: 0%

---


# Aan de slag met Process Reporting{#getting-started-with-process-reporting}

De Rapportering van het proces geeft de gebruikers van AEM Forms de capaciteit om informatie over de processen van AEM Forms te vragen die momenteel in de implementatie van AEM Forms worden bepaald. Procesrapportage heeft echter niet rechtstreeks toegang tot gegevens van de AEM Forms-opslagplaats. De gegevens worden eerst gepubliceerd naar de Process Reporting repository op een geplande basis (*door de ProcessDataPublisher &amp; ProcessDataStorage service* s). De rapporten en vragen in de Rapportering van het Proces worden dan geproduceerd uit het Proces Meldend gegevens die aan de bewaarplaats worden gepubliceerd. De Rapportering van het proces is geïnstalleerd als deel van de module van de Forms Workflow.

In dit artikel worden de stappen beschreven die het publiceren van AEM Forms-gegevens naar de Process Reporting repository mogelijk maken. Daarna, zult u het Rapport van het Proces kunnen gebruiken om rapporten en vragen in werking te stellen. Het artikel behandelt ook de opties beschikbaar om de diensten van de Rapportering van het Proces te vormen.

## Voorwaarden {#process-reporting-pre-requisites} voor procesrapportage

### Niet-essentiële processen zuiveren {#purge-non-essential-processes}

Als u momenteel Forms Workflow gebruikt, kan de AEM Forms-database mogelijk een grote hoeveelheid gegevens bevatten

De publicatieservices voor Process Reporting publiceren alle AEM Forms-gegevens die momenteel in de database beschikbaar zijn. Dit houdt in dat als de database verouderde gegevens bevat waarop u geen rapporten en query&#39;s wilt uitvoeren, alle gegevens ook naar de gegevensopslagruimte worden gepubliceerd, ook al is dit niet vereist voor rapportage. U wordt aangeraden deze gegevens te wissen voordat u de services uitvoert om de gegevens naar de Process Reporting-opslagplaats te publiceren. Dit zal de prestaties van zowel de uitgeversdienst als de dienst verbeteren die de gegevens voor rapportering vraagt.

Zie [Procesgegevens wissen](https://help.adobe.com/en_US/livecycle/11.0/AdminHelp/WS92d06802c76abadb-5145d5d12905ce07e7-7cb2.2.html) voor meer informatie over het wissen van AEM Forms-procesgegevens.

>[!NOTE]
>
>Zie het Adobe Developer Connection-artikel over [Opschoonprocessen en taken](https://www.adobe.com/content/dam/Adobe/en/devnet/livecycle/pdfs/purging_processes_jobs.pdf) voor de tips en trucs van het hulpprogramma Leegmaken.

## Services {#configuring-process-reporting-services} voor procesrapportage configureren

### Publicatie van procesgegevens plannen {#schedule-process-data-publishing}

De Process Reporting Services publiceren op geregelde basis gegevens van de AEM Forms-database naar de Process Reporting repository.

Deze bewerking kan bronintensief zijn en de prestaties van de AEM Forms-servers beïnvloeden. U wordt aangeraden dit buiten de bezige tijdsleuven van de AEM Forms-server te plannen.

Door gebrek, is het publiceren van gegevens planning om elke dag om 2:00 uur in werking te stellen.

Voer de volgende stappen uit om het publicatieschema te wijzigen:

>[!NOTE]
>
>Als u uw AEM Forms-implementatie uitvoert in een cluster, voert u de volgende stappen uit op elk knooppunt van de cluster.

1. Stop de AEM Forms-serverinstantie.
1. &#x200B;

   * (Voor Vensters) open het `[JBoss root]/bin/run.conf.bat` dossier in een redacteur.
   * (Voor Linux, AIX en Solaris) `[JBoss root]/bin/run.conf.sh` dossier in een redacteur.

1. Het JVM-argument `-Dreporting.publisher.cron = <expression>.` toevoegen

   Voorbeeld: Met de volgende uitsnijdexpressie worden bij Process Reporting om de vijf uur AEM Forms-gegevens naar de Process Reporting-opslagplaats gepubliceerd:

   * `-Dreporting.publisher.cron = 0_0_0/5_*_*_?`

1. Sla het `run.conf.bat`-bestand op en sluit het.

1. Start de AEM Forms-serverinstantie opnieuw.

1. Stop de AEM Forms-serverinstantie.
1. Meld u aan bij de beheerconsole van WebSphere. Klik in de navigatiestructuur op **Servers** > **Toepassingsservers** en klik vervolgens in het rechterdeelvenster op de servernaam.

1. Klik onder Serverinfrastructuur op **Java en Process Management** > **Process Definition**.

1. Klik onder Extra eigenschappen op **Java Virtual Machine**.

   Voeg in het vak Algemene JVM-argumenten het argument `-Dreporting.publisher.cron = <expression>.` toe

   **Voorbeeld**: Met de volgende uitsnijdexpressie worden bij Process Reporting om de vijf uur AEM Forms-gegevens naar de Process Reporting-opslagplaats gepubliceerd:

   * `-Dreporting.publisher.cron = 0_0_0/5_*_*_?`

1. Klik **Toepassen**, klik O.K., en klik dan **sparen direct aan de master configuratie**.
1. Start de AEM Forms-serverinstantie opnieuw.
1. Stop de AEM Forms-serverinstantie.
1. Meld u aan bij de WebLogic-beheerconsole. Het standaardadres van de Console van het Beleid WebLogic is `https://[hostname]:[port]/console`.
1. Klik onder Wijzigen midden op **Vergrendelen en bewerken**.
1. Klik onder Domeinstructuur op **Omgeving** > **Servers** en klik in het rechterdeelvenster op de naam van de beheerde server.
1. Klik in het volgende scherm op de tab **Configuration** > **Server Start**.
1. Voeg in het tekstvak Argumenten het JVM-argument `-Dreporting.publisher.cron = <expression>` toe.

   **Voorbeeld**: Met de volgende uitsnijdexpressie worden bij Process Reporting om de vijf uur AEM Forms-gegevens naar de Process Reporting-opslagplaats gepubliceerd:

   `-Dreporting.publisher.cron = 0_0_0/5_*_*_?`

1. Klik **Opslaan** en klik vervolgens op **Wijzigingen activeren**.
1. Start de AEM Forms-serverinstantie opnieuw.

![processdatapublisherservice](assets/processdatapublisherservice.png)

### ProcessDataStorage-service {#processdatastorage-service}

De dienst ProcessDataStorageProvider ontvangt procesgegevens van de dienst ProcessDataPublisher en bewaart de gegevens aan de bewaarplaats van de Rapportering van het Proces.

Bij elke publicatiecyclus worden de gegevens opgeslagen in submappen van een vooraf gedefinieerde hoofdmap.

U kunt de console van het Beleid gebruiken om de wortel (**default** te vormen: `/content/reporting/pm`) locatie en submap (**default**: `/yyyy/mm/dd/hh/mi/ss`) hiërarchie-indeling waarin de procesgegevens worden opgeslagen.

#### De locaties van de Process Reporting repository configureren {#to-configure-the-process-reporting-repository-locations}

1. Meld u aan bij **Beheerconsole** met beheerdersreferenties. De standaard-URL van de beheerconsole is `https://'[server]:[port]'/adminui`
1. Navigeer naar **Home** > **Services** > **Toepassingen en services** >**Servicebeheer** en open de service **ProcessDataStorageProvider**.

   ![process-data-storage-service](assets/process-data-storage-service.png)

   **RootFolder**

   De CRX-locatie waarin de procesgegevens worden opgeslagen voor rapportage.

   `Default`: `/content/reporting/pm`

   **Maphiërarchie**

   De mappenhiërarchie waarin de procesgegevens worden opgeslagen op basis van de aanmaaktijd van het proces.

   `Default`:  `/yyyy/mm/dd/hh/mi/ss`

1. Klik **Opslaan**.

### ReportConfiguration-service {#reportconfiguration-service}

De dienst ReportConfiguration wordt gebruikt door Proces dat voor het vormen van het proces meldt de vraagdienst.

#### Om de dienst te vormen ReportingConfiguration {#to-configure-the-reportingconfiguration-service}

1. Meld u aan bij **Configuratiebeheer** met CRX-beheerdersreferenties. De standaard-URL van Configuration Manager is `https://'[server]:[port]'/lc/system/console/configMgr`
1. Open de **ReportingConfiguration** dienst.
1. **Aantal records**

   Wanneer het runnen van een vraag op de bewaarplaats, kan een resultaat een groot aantal verslagen potentieel bevatten. Als de resultaatreeks groot is, kan de vraaguitvoering servermiddelen verbruiken.

   Om grote resultaatsets te behandelen, splitst de dienst ReportConfiguration de vraagverwerking in partijen verslagen. Hierdoor wordt de systeembelasting verminderd.

   `Default`:  `1000`

   **CRX-opslagpad**

   De CRX-locatie waarin de procesgegevens moeten worden opgeslagen voor rapportage.

   `Default`:  `/content/reporting/pm`

   >[!NOTE]
   >
   >Dit is dezelfde locatie als opgegeven in de configuratieoptie **Hoofdmap** ProcessDataStorage.
   >
   >
   >Als u de optie van de Omslag van de Wortel in de configuratie ProcessDataStorage bijwerkt, moet u de plaats van de Weg van de Opslag CRX in de dienst ReportConfiguration bijwerken.

1. Klik **Opslaan** en sluit **CQ Configuration Manager**.

### ProcessDataPublisher-service {#processdatapublisher-service}

De service ProcessDataPublisher importeert procesgegevens uit de AEM Forms-database en publiceert de gegevens naar de ProcessDataStorageProvider-service voor opslag.

#### De service ProcessDataPublisher configureren   {#to-configure-processdatapublisher-service-nbsp}

1. Meld u aan bij **Beheerconsole** met beheerdersreferenties.

   De standaard-URL is `https://'server':port]/adminui/`.

1. Navigeer naar **Home** > **Services** > **Toepassingen en services** >**Servicebeheer** en open de service **ProcessDataPublisher**.

![processdatapublisherservice-1](assets/processdatapublisherservice-1.png)

**Gegevens publiceren**

Schakel deze optie in om te beginnen met het publiceren van procesgegevens. De optie is standaard uitgeschakeld.

Schakel Process Reporting alleen in als alle configuraties met betrekking tot Process Reporting-componenten op de juiste wijze zijn ingesteld.

U kunt deze optie ook gebruiken om het publiceren van procesgegevens uit te schakelen wanneer dit niet langer verplicht is.

`Default`:  `Off`

**Batchinterval (sec)**

Telkens als de dienst ProcessDataPublisher loopt, verdeelt de dienst eerst de tijd sinds de laatste looppas van de dienst door het Interval van de Partij. De dienst verwerkt dan elk interval van de gegevens van AEM Forms afzonderlijk.

Zo kunt u de grootte bepalen van de gegevens die de uitgever verwerkt tijdens elke uitvoering (batch) binnen een cyclus.

Bijvoorbeeld, als de uitgever elke dag in werking stelt, dan in plaats van het verwerken van de volledige gegevens één dag in één enkele looppas, door gebrek, wordt het de verwerking in 24 partijen van elk één uur verdeeld.

`Default`:  `3600`

`Unit`:  `Seconds`

**Time-out vergrendelen (sec)**

De uitgeversservice verkrijgt een vergrendeling wanneer de verwerking van gegevens wordt gestart, zodat meerdere exemplaren van de uitgever niet gelijktijdig met het uitvoeren en verwerken van gegevens beginnen.

Als een uitgeversdienst die een slot heeft verworven, nutteloos voor het aantal seconden is die door de waarde van de Onderbreking van het Slot wordt bepaald, dan wordt zijn slot vrijgegeven zodat andere instanties van de uitgeversdienst kunnen blijven verwerken.

`Default`:  `3600`

`Unit`:  `Seconds`

**Gegevens publiceren vanuit**

De AEM Forms-omgeving bevat gegevens uit de tijd dat de omgeving werd ingesteld.

Standaard importeert de ProcessDataPublisher-service alle gegevens uit de AEM Forms-database.

Afhankelijk van uw rapporteringsbehoeften, als u van plan bent om rapporten en vragen over gegevens na een bepaalde datum en een tijd in werking te stellen, adviseert men dat u de datum en de tijd specificeert. De publicatieservice publiceert vervolgens de datum vanaf die datum.

`Default`:  `01-01-1970 00:00:00`

`Format`:  `dd-MM-yyyy HH:mm:ss`

## Toegang tot de gebruikersinterface van de Rapportering van het Proces {#accessing-the-process-reporting-user-interface}

De gebruikersinterface voor Process Reporting is browsergebaseerd.

Nadat u de Rapportering van het Proces van de opstelling hebt, kunt u beginnen met het Proces Meldend bij de volgende plaats in uw installatie van AEM Forms te werken:

`https://<server>:<port>/lc/pr`

### Aanmelden bij procesrapportage {#log-in-to-process-reporting}

Wanneer u naar de URL voor Process Reporting (https://&lt;server>:&lt;port>/lc/pr) navigeert, wordt het aanmeldingsscherm weergegeven.

Specificeer uw geloofsbrieven aan login aan de module van de Rapportering van het Proces.

>[!NOTE]
>
>Als u zich wilt aanmelden bij de gebruikersinterface Process Reporting, hebt u de volgende AEM Forms-machtiging nodig:
>
>`PERM_PROCESS_REPORTING_USER`

![Aanmelden bij Process Reporting](assets/capture1_new.png)

Als u zich aanmeldt bij Process Reporting, wordt het scherm **[!UICONTROL Home]** weergegeven.

### Rapportagescherm {#process-reporting-home-screen} verwerken

![proces-reporting-home-screen](assets/process-reporting-home-screen.png)

**De het Melden van het proces boommening:** de boommening op de linkerkant van het scherm van het Huis bevat de punten voor het Proces Meldend modules.

De boomstructuurweergave bestaat uit de volgende items op hoofdniveau:

**Rapporten:** Dit punt bevat de uit-van-de-doos rapporten die met het Rapporteren van het Proces verschepen.

Zie [Vooraf gedefinieerde rapporten in Process Reporting](/help/forms/using/process-reporting/pre-defined-reports-in-process-reporting.md) voor meer informatie over de vooraf gedefinieerde rapporten.

**Adhoc Vragen:** Dit punt bevat opties om op filter-gebaseerd onderzoek naar processen en taken uit te voeren.

Voor details op ad-hoc vragen, zie [Ad-hoc Vragen in Proces het Melden](/help/forms/using/process-reporting/adhoc-queries-in-process-reporting.md).

**Aangepast:** het knooppunt Aangepast toont aangepaste rapporten die u maakt.

Voor de procedure om douanerapporten tot stand te brengen en te tonen, zie [Eigen Rapporten in Proces het Melden](/help/forms/using/process-reporting/process-reporting-custom-reports.md).

**De titelbar van de Rapportering van het proces:** De bar van de Titel van de Rapportering van het Proces bevat sommige generische opties die u kunt gebruiken wanneer het werken in het gebruikersinterface.

**Titel Process Reporting:** De titel Process Reporting wordt in de linkerhoek van de titelbalk weergegeven.

Klik op de titel om terug te keren naar het scherm Home.

**Tijdstip laatste update:** De procesgegevens worden op geplande basis gepubliceerd vanuit de AEM Forms-database naar de Process Reporting repository.

De laatste tijd van de Update toont de laatste datum en de tijd tot waarvan de gegevensupdates aan de bewaarplaats van de Rapportering van het Proces werden geduwd.

Zie [Procesgegevens publiceren plannen](/help/forms/using/process-reporting/install-start-process-reporting.md#p-schedule-process-data-publishing-p) in het artikel Getting Started with Process Reporting voor meer informatie over de service voor het publiceren van gegevens en het plannen van deze service.

**Procesrapporteringsgebruiker:** De aangemelde gebruikersnaam wordt rechts van de laatste update weergegeven.

**Verwerkt het drop-down lijst van de Titel van de Rapportering van het Proces:** De drop-down lijst bij de juiste hoek van de de titelbar van de Rapportering van het Proces bevat de volgende opties:

* **[!UICONTROL Sync]**: Synchroniseer de ingesloten Process Reporting-opslagplaats met de AEM Forms-database.
* **[!UICONTROL Help]**: Raadpleeg de Help-documentatie bij Process Reporting.
* **[!UICONTROL Logout]**: Afmelden bij procesrapportage
