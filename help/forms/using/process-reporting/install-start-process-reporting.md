---
title: Aan de slag met Process Reporting
description: De stappen om aan de slag te gaan met AEM Forms over JEE Process Reporting
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: process-reporting
docset: aem65
exl-id: 1272e854-fa64-4bfd-b073-8fbcf210e9b5
solution: Experience Manager, Experience Manager Forms
role: User, Developer
source-git-commit: f6771bd1338a4e27a48c3efd39efe18e57cb98f9
workflow-type: tm+mt
source-wordcount: '1706'
ht-degree: 0%

---

# Aan de slag met Process Reporting{#getting-started-with-process-reporting}

De Rapportering van het proces geeft de gebruikers van AEM Forms de capaciteit om informatie over de processen van AEM Forms te vragen die momenteel in de implementatie van AEM Forms worden bepaald. Procesrapportage heeft echter niet rechtstreeks toegang tot gegevens van de AEM Forms-opslagplaats. De gegevens worden voor het eerst gepubliceerd naar de Process Reporting repository (*door de ProcessDataPublisher &amp; ProcessDataStorage-service* s). De rapporten en vragen in de Rapportering van het Proces worden dan geproduceerd uit het Proces Meldend gegevens die aan de bewaarplaats worden gepubliceerd. De Rapportering van het proces is geïnstalleerd als deel van de module van de Forms Workflow.

In dit artikel worden de stappen beschreven die het publiceren van AEM Forms-gegevens naar de Process Reporting repository mogelijk maken. Daarna, zult u het Rapport van het Proces kunnen gebruiken om rapporten en vragen in werking te stellen. Het artikel behandelt ook de opties beschikbaar om de diensten van de Rapportering van het Proces te vormen.

## Voorwaarden voor procesrapportage {#process-reporting-pre-requisites}

### Niet-essentiële processen zuiveren {#purge-non-essential-processes}

Als u momenteel Forms Workflow gebruikt, kan de AEM Forms-database mogelijk een grote hoeveelheid gegevens bevatten

Met de publicatieservices Process Reporting worden alle AEM Forms-gegevens gepubliceerd die momenteel in de database beschikbaar zijn. Het impliceert dat als het gegevensbestand erfenisgegevens bevat waarover u geen rapporten en vragen wilt in werking stellen, al die gegevens ook aan de bewaarplaats zouden worden gepubliceerd hoewel het niet voor rapportering wordt vereist. U wordt aangeraden deze gegevens te wissen voordat u de services uitvoert om de gegevens naar de Process Reporting-opslagplaats te publiceren. Dit verbetert de prestaties van zowel de uitgeversdienst als de dienst die de gegevens voor rapportering vraagt.

Zie voor meer informatie over het wissen van AEM Forms-procesgegevens [Procesgegevens wissen](/help/forms/using/admin-help/purging-process-data.md).

>[!NOTE]
>
>Raadpleeg het Adobe Developer Connection-artikel over het gebruik van het gereedschap Leegmaken voor tips en trucs [Leegmaken en banen](/help/forms/using/admin-help/purging-process-data.md).

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

   * (Voor Windows) Open het dialoogvenster `[JBoss root]/bin/run.conf.bat` in een editor.
   * (Voor Linux®, AIX® en Solaris™) `[JBoss root]/bin/run.conf.sh` in een editor.

1. Het JVM-argument toevoegen `-Dreporting.publisher.cron = <expression>.`

   Voorbeeld: met de volgende uitsnijdexpressie worden bij Process Reporting om de vijf uur AEM Forms-gegevens naar de Process Reporting repository gepubliceerd:

   * `-Dreporting.publisher.cron = 0_0_0/5_*_*_?`

1. Opslaan en het dialoogvenster sluiten `run.conf.bat` bestand.

1. Start de AEM Forms Server-instantie opnieuw.

1. Stop de AEM Forms Server-instantie.
1. Meld u aan bij de beheerconsole van WebSphere®. Klik in de navigatiestructuur op **Servers** > **Toepassingsservers** en klik vervolgens in het rechterdeelvenster op de servernaam.

1. Klik onder Serverinfrastructuur op **Java™ en Process Management** > **Procesdefinitie**.

1. Klik onder Extra eigenschappen op **Java™ Virtual Machine**.

   Voeg het argument toe in het vak Generic JVM-argumenten `-Dreporting.publisher.cron = <expression>.`

   **Voorbeeld**: Met de volgende uitsnijdexpressie worden AEM Forms-gegevens om de vijf uur door Process Reporting (Procesrapportage) naar de Process Reporting repository gepubliceerd:

   * `-Dreporting.publisher.cron = 0_0_0/5_*_*_?`

1. Klikken **Toepassen**, klikt u op OK en vervolgens op **Direct opslaan in de hoofdconfiguratie**.
1. Start de AEM Forms Server-instantie opnieuw.
1. Stop de AEM Forms Server-instantie.
1. Meld u aan bij de WebLogic-beheerconsole. Het standaardadres van de WebLogic-beheerconsole is `https://[hostname]:[port]/console`.
1. Klik onder Wijzigen in midden op **Vergrendelen en bewerken**.
1. Klik onder Domeinstructuur op **Omgeving** > **Servers** en klik in het rechterdeelvenster op de naam van de beheerde server.
1. Klik in het volgende scherm op de knop **Configuratie** tab > **Start server** tab.
1. Voeg in het tekstvak Argumenten het JVM-argument toe `-Dreporting.publisher.cron = <expression>`.

   **Voorbeeld**: Met de volgende uitsnijdexpressie worden AEM Forms-gegevens om de vijf uur door Process Reporting (Procesrapportage) naar de Process Reporting repository gepubliceerd:

   `-Dreporting.publisher.cron = 0_0_0/5_*_*_?`

1. Klikken **Opslaan** en klik vervolgens op **Wijzigingen activeren**.
1. Start de AEM Forms Server-instantie opnieuw.

![processdatapublisherservice](assets/processdatapublisherservice.png)

>[!NOTE]
>
> Het wordt aanbevolen de SDK opnieuw te starten met de opdracht &#39;Ctrl + C&#39;. Het opnieuw opstarten van de AEM SDK met behulp van alternatieve methoden, bijvoorbeeld het stoppen van Java-processen, kan leiden tot inconsistenties in de AEM ontwikkelomgeving.

### Procesgegevensopslagservice {#processdatastorage-service}

De dienst ProcessDataStorageProvider ontvangt procesgegevens van de dienst ProcessDataPublisher en bewaart de gegevens aan de bewaarplaats van de Rapportering van het Proces.

Bij elke publicatiecyclus worden de gegevens opgeslagen in submappen van een vooraf gedefinieerde hoofdmap.

U kunt de console van het Beleid gebruiken om de wortel te vormen (**default**: `/content/reporting/pm`) locatie en submap (**default**: `/yyyy/mm/dd/hh/mi/ss`) hiërarchieopmaak waarin de procesgegevens worden opgeslagen.

#### De locaties van de Process Reporting repository configureren {#to-configure-the-process-reporting-repository-locations}

1. Aanmelden bij **Beheerconsole** met beheerdersreferenties. De standaard-URL van de beheerconsole is `https://'[server]:[port]'/adminui`
1. Navigeren naar **Home** > **Services** > **Toepassingen en services** >**Servicebeheer** en opent u de **ProcessDataStorageProvider** service.

   ![process-data-storage-service](assets/process-data-storage-service.png)

   **RootFolder**

   De CRX-locatie waarin de procesgegevens worden opgeslagen voor rapportage.

   `Default`: `/content/reporting/pm`

   **Maphiërarchie**

   De mappenhiërarchie waarin de procesgegevens worden opgeslagen op basis van de aanmaaktijd van het proces.

   `Default`: `/yyyy/mm/dd/hh/mi/ss`

1. Klikken **Opslaan**.

### ReportConfiguration-service {#reportconfiguration-service}

De dienst ReportConfiguration wordt gebruikt door Proces dat voor het vormen van het proces meldt de vraagdienst.

#### Om de dienst te vormen ReportingConfiguration {#to-configure-the-reportingconfiguration-service}

1. Aanmelden bij **Configuratiebeheer** met CRX-beheerdersreferenties. De standaard-URL van Configuration Manager is `https://'[server]:[port]'/lc/system/console/configMgr`
1. Open de **ReportingConfiguration** service.
1. **Aantal records**

   Wanneer het runnen van een vraag op de bewaarplaats, kan een resultaat vele verslagen potentieel bevatten. Als de resultaatreeks groot is, kan de vraaguitvoering servermiddelen verbruiken.

   Om grote resultaatsets te behandelen, splitst de dienst ReportConfiguration de vraagverwerking in partijen verslagen. Dit vermindert de belasting van het systeem.

   `Default`: `1000`

   **CRX-opslagpad**

   De CRX-locatie waarin de procesgegevens moeten worden opgeslagen voor rapportage.

   `Default`: `/content/reporting/pm`

   >[!NOTE]
   >
   >Deze locatie is dezelfde als die is opgegeven in de configuratieoptie ProcessDataStorage **Hoofdmap**.
   >
   >
   >Als u de optie van de Omslag van de Wortel in de configuratie ProcessDataStorage bijwerkt, moet u de plaats van de Weg van de Opslag CRX in de dienst ReportConfiguration bijwerken.

1. Klikken **Opslaan** en sluiten **Configuratiebeheer van CQ**.

### ProcessDataPublisher-service {#processdatapublisher-service}

De service ProcessDataPublisher importeert procesgegevens uit de AEM Forms-database en publiceert de gegevens naar de ProcessDataStorageProvider-service voor opslag.

#### De service ProcessDataPublisher configureren   {#to-configure-processdatapublisher-service-nbsp}

1. Aanmelden bij **Beheerconsole** met beheerdersreferenties.

   De standaard-URL is `https://'server':port]/adminui/`.

1. Navigeren naar **Home** > **Services** > **Toepassingen en services** >**Servicebeheer** en opent u de **ProcessDataPublisher** service.

![processdatapublisherservice-1](assets/processdatapublisherservice-1.png)

**Gegevens publiceren**

Schakel deze optie in om te beginnen met het publiceren van procesgegevens. De optie is standaard uitgeschakeld.

Schakel Process Reporting alleen in als alle configuraties met betrekking tot Process Reporting-componenten op de juiste wijze zijn ingesteld.

U kunt deze optie ook gebruiken om het publiceren van procesgegevens uit te schakelen wanneer dit niet langer verplicht is.

`Default`: `Off`

**Batchinterval (sec)**

Telkens als de dienst ProcessDataPublisher loopt, verdeelt de dienst eerst de tijd sinds de laatste looppas van de dienst door het Interval van de Partij. De dienst verwerkt dan elk interval van de gegevens van AEM Forms afzonderlijk om de grootte van gegevens te controleren de uitgever van begin tot eind tijdens elke looppas (partij) binnen een cyclus verwerkt.

Bijvoorbeeld, als de uitgever elke dag in werking stelt, dan in plaats van het verwerken van de volledige gegevens één dag in één enkele looppas, door gebrek, wordt het de verwerking in 24 partijen van elk één uur verdeeld.

`Default`: `3600`

`Unit`: `Seconds`

**Time-out vergrendelen (sec)**

De uitgeversservice verkrijgt een vergrendeling wanneer de verwerking van gegevens wordt gestart, zodat meerdere exemplaren van de uitgever niet gelijktijdig met het uitvoeren en verwerken van gegevens beginnen.

Als een uitgeversdienst die een slot heeft verworven, nutteloos voor het aantal seconden is die door de waarde van de Onderbreking van het Slot wordt bepaald, dan wordt zijn slot vrijgegeven zodat andere instanties van de uitgeversdienst kunnen blijven verwerken.

`Default`: `3600`

`Unit`: `Seconds`

**Gegevens publiceren vanuit**

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

Wanneer u naar de URL voor procesrapportage navigeert (https://&lt;server>:&lt;port>/lc/pr), wordt het aanmeldingsscherm weergegeven.

Om aan login aan de module van de Rapportering van het Proces, specificeer uw geloofsbrieven.

>[!NOTE]
>
>Als u zich wilt aanmelden bij de gebruikersinterface Process Reporting, hebt u de volgende AEM Forms-machtiging nodig:
>
>`PERM_PROCESS_REPORTING_USER`

![Aanmelden bij Process Reporting](assets/capture1_new.png)

Wanneer u zich bij het Proces meldt, **[!UICONTROL Home]** schermweergaven.

### Process Reporting Home-scherm {#process-reporting-home-screen}

![proces-reporting-home-screen](assets/process-reporting-home-screen.png)

**De mening van de boom van de Rapportering van het proces:** De boomstructuurweergave aan de linkerkant van het Homescherm bevat de items voor de modules Procesrapportage.

De boomstructuurweergave bestaat uit de volgende items op hoofdniveau:

**Rapporten:** Dit item bevat de out-of-the-box rapporten die worden verzonden met Process Reporting.

Zie voor meer informatie over de vooraf gedefinieerde rapporten [Vooraf gedefinieerde rapporten in procesrapportage](/help/forms/using/process-reporting/pre-defined-reports-in-process-reporting.md).

**Ad-hocquery&#39;s:** Dit item bevat opties voor het uitvoeren van op filters gebaseerde zoekopdrachten naar processen en taken.

Voor meer informatie over ad-hocquery&#39;s raadpleegt u [Ad hoc Vragen in Proces het Melden](/help/forms/using/process-reporting/adhoc-queries-in-process-reporting.md).

**Aangepast:** Het knooppunt Aangepast geeft aangepaste rapporten weer die u maakt.

Voor de procedure om douanerapporten te creëren en te tonen, zie [Aangepaste rapporten in procesrapportage](/help/forms/using/process-reporting/process-reporting-custom-reports.md).

**Procesrapportage, titelbalk:** De de titelbar van de Rapportering van het Proces bevat sommige generische opties die u wanneer het werken in het gebruikersinterface kunt gebruiken.

**Titel van procesrapportage:** De titel Procesrapportage wordt in de linkerhoek van de titelbalk weergegeven.

Klik op de titel om terug te keren naar het scherm Home.

**Tijd laatste update:** De procesgegevens worden op een geplande basis gepubliceerd van de AEM Forms-database naar de Process Reporting repository.

De laatste tijd van de Update toont de laatste datum en de tijd tot waarvan de gegevensupdates aan de bewaarplaats van de Rapportering van het Proces werden geduwd.

Voor meer informatie over de service voor het publiceren van gegevens en hoe u deze service wilt plannen, raadpleegt u [Publiceren van procesgegevens plannen](/help/forms/using/process-reporting/install-start-process-reporting.md#p-schedule-process-data-publishing-p) in het artikel Aan de slag met Process Reporting.

**Gebruiker voor procesrapportage:** De aangemelde gebruikersnaam wordt rechts van de laatste update weergegeven.

**Verwerking van vervolgkeuzelijst titelbalk rapportage:** De vervolgkeuzelijst in de rechterhoek van de titelbalk van Procesrapportage bevat de volgende opties:

* **[!UICONTROL Sync]**: Synchroniseer de ingesloten Process Reporting-opslagplaats met de AEM Forms-database.
* **[!UICONTROL Help]**: Bekijk de Help-documentatie over Process Reporting.
* **[!UICONTROL Logout]**: Afmelden van procesrapportage


