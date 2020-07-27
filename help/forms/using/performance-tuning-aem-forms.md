---
title: Prestaties afstemmen van AEM Forms-server
seo-title: Prestaties afstemmen van AEM Forms-server
description: Voor AEM Forms die optimaal kunnen presteren, kunt u de geheim voorgeheugenmontages en parameters verfijnen JVM. Ook, kan het gebruiken van een Webserver de prestaties van de plaatsing van AEM Forms verbeteren.
seo-description: Voor AEM Forms die optimaal kunnen presteren, kunt u de geheim voorgeheugenmontages en parameters verfijnen JVM. Ook, kan het gebruiken van een Webserver de prestaties van de plaatsing van AEM Forms verbeteren.
uuid: bf23b62c-7559-4726-8f4e-cc8b1457e501
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: Configuration
discoiquuid: 38c0ec46-5686-4656-bfb4-7125ec194673
docset: aem65
translation-type: tm+mt
source-git-commit: 1343cc33a1e1ce26c0770a3b49317e82353497ab
workflow-type: tm+mt
source-wordcount: '927'
ht-degree: 0%

---


# Prestaties afstemmen van AEM Forms-server{#performance-tuning-of-aem-forms-server}

Dit artikel bespreekt strategieën en beste praktijken u kunt uitvoeren om knelpunten te verminderen en de prestaties van uw plaatsing van AEM Forms te optimaliseren.

## Cacheinstellingen {#cache-settings}

U kunt de caching strategie voor AEM Forms vormen en controleren gebruikend de **Mobiele component van Configuraties** van Vormen in de Console van de Configuratie van het Web AEM bij:

* (AEM Forms over OSGi) `https://'[server]:[port]'/system/console/configMgr`
* (AEM Forms JEE) `https://'[server]:[port]'/lc/system/console/configMgr`

De beschikbare opties voor caching zijn als volgt:

* **Geen**: Verdwingt om geen artefact in de cache op te slaan. Dit zal in de praktijk de prestaties vertragen en hoge geheugenbeschikbaarheid wegens het ontbreken van geheim voorgeheugen vereist.
* **Conservatief**: Hiermee worden alleen de tussenliggende artefacten in cache geplaatst die zijn gegenereerd voordat het formulier wordt gegenereerd, zoals een sjabloon met inline-fragmenten en -afbeeldingen.
* **Agressief**: Hiermee wordt geforceerd om bijna alles in cache te plaatsen dat in cache kan worden geplaatst, inclusief gerenderde HTML-inhoud, behalve alle artefacten van het niveau Conservative Cching. Het resulteert in de beste prestaties maar verbruikt ook meer geheugen voor het opslaan van artefacten in cache. Met een agressieve cachestrategie krijgt u constante prestaties bij het weergeven van een formulier terwijl de weergegeven inhoud in de cache wordt geplaatst.

De standaardinstellingen voor de cache van AEM Forms zijn mogelijk niet geschikt voor optimale prestaties. Daarom wordt aangeraden de volgende instellingen te gebruiken:

* **Cachestrategie**: Agressief
* **Cachegrootte** (in aantal formulieren): Vereist
* **Max. objectgrootte**: Vereist

![Configuraties van mobiele formulieren](assets/snap.png)

>[!NOTE]
>
>Als u AEM Dispatcher gebruikt om adaptieve formulieren in cache te plaatsen, wordt ook het adaptieve formulier in cache geplaatst dat formulieren met voorgevulde gegevens bevat. Als dergelijke formulieren worden aangeboden in de AEM Dispatcher-cache, kan dit ertoe leiden dat voorgevulde of opgevulde gegevens worden weergegeven aan de gebruikers. Gebruik dus AEM Dispatcher om adaptieve formulieren die geen voorgevulde gegevens gebruiken in cache op te slaan. Bovendien maakt een verzendercache cachefragmenten in de cache niet automatisch ongeldig. Gebruik het dus niet om formulierfragmenten in de cache op te slaan. Gebruik voor dergelijke formulieren en fragmenten de cache [Adaptieve formulieren](../../forms/using/configure-adaptive-forms-cache.md).

## JVM-parameters {#jvm-parameters}

Voor optimale prestaties wordt aangeraden de volgende JVM- `init` argumenten te gebruiken om de `Java heap` en `PermGen`.

```shell
set CQ_JVM_OPTS=%CQ_JVM_OPTS% -Xms8192m
set CQ_JVM_OPTS=%CQ_JVM_OPTS% -Xmx8192m
set CQ_JVM_OPTS=%CQ_JVM_OPTS% -XX:PermSize=256m
set CQ_JVM_OPTS=%CQ_JVM_OPTS% -XX:MaxPermSize=1024m
```

>[!NOTE]
>
>De aanbevolen instellingen zijn voor Windows 2008 R2 8 Core en Oracle HotSpot 1.7 (64-bits) JDK en moeten worden vergroot of verkleind volgens de systeemconfiguratie.

## Een webserver gebruiken {#using-a-web-server}

Adaptieve formulieren en HTML5-formulieren worden weergegeven in HTML5-indeling. De resulterende uitvoer kan groot zijn, afhankelijk van factoren zoals de formuliergrootte en afbeeldingen in het formulier. Om de gegevensoverdracht te optimaliseren, is de geadviseerde benadering de reactie van HTML te comprimeren gebruikend de Webserver waarvan het verzoek wordt gediend. Deze benadering vermindert de reactiegrootte, het netwerkverkeer, en de tijd die wordt vereist om gegevens tussen server en cliëntmachines te stromen.

Voer bijvoorbeeld de volgende stappen uit om compressie op Apache Web Server 2.0 32-bits met JBoss in te schakelen:

>[!NOTE]
>
>De volgende instructies zijn niet van toepassing op andere servers dan Apache Web Server 2.0 32-bits. Zie de bijbehorende productdocumentatie voor stappen die specifiek zijn voor andere servers.

De volgende stappen tonen wijzigingen aan die vereist zijn om compressie met Apache Web Server mogelijk te maken

**Vraag de Apache-webserversoftware aan die van toepassing is op uw besturingssysteem**

* Windows: Download de Apache-webserver van de Apache HTTP Server Project-site.
* Solaris 64-bits: Download de Apache-webserver van de website Sunfreeware for Solaris.
* Linux: De Apache-webserver is vooraf geïnstalleerd op een Linux-systeem.

Apache kan met behulp van het HTTP-protocol communiceren met CRX. De configuraties zijn bedoeld voor optimalisatie met gebruik van HTTP.

1. Verwijder de commentaarmarkering van de volgende moduleconfiguraties in `APACHE_HOME/conf/httpd.conf` dossier.

   ```shell
   LoadModule proxy_balancer_module modules/mod_proxy.so
   LoadModule proxy_balancer_module modules/mod_proxy_http.so
   LoadModule deflate_module modules/mod_deflate.so
   ```

   >[!NOTE]
   >
   >Voor Linux `APACHE_HOME` is de standaardwaarde `/etc/httpd/`.

1. Vorm de volmacht op haven 4502 van crx.
Voeg volgende configuratie in `APACHE_HOME/conf/httpd.conf` configuratiedossier toe.

   ```shell
   ProxyPass / https://<server>:4502/
   ProxyPassReverse / https://<server>:4502/
   ```

1. Compressie inschakelen. Voeg volgende configuratie in `APACHE_HOME/conf/httpd.conf` configuratiedossier toe.

   **Voor HTML5-formulieren**

   ```xml
   <Location /content/xfaforms>
       <IfModule mod_deflate.c>
           SetOutputFilter DEFLATE
           #Don’t compress
           SetEnvIfNoCase Request_URI \.(?:gif|jpe?g|png)$ no-gzip dont-vary
           SetEnvIfNoCase Request_URI \.(?:exe|t?gz|zip|bz2|sit|rar)$ no-gzip dont-vary
           #Dealing with proxy servers
               <IfModule mod_headers.c>
                   Header append Vary User-Agent
               </IfModule>
       </IfModule>
   </Location>
   ```

   **Voor adaptieve formulieren**

   ```xml
   <Location /content/forms/af>
       <IfModule mod_deflate.c>
           SetOutputFilter DEFLATE
           #Don’t compress
           SetEnvIfNoCase Request_URI \.(?:gif|jpe?g|png)$ no-gzip dont-vary
           SetEnvIfNoCase Request_URI \.(?:exe|t?gz|zip|bz2|sit|rar)$ no-gzip dont-vary
           #Dealing with proxy servers
               <IfModule mod_headers.c>
                   Header append Vary User-Agent
               </IfModule>
       </IfModule>
   </Location>
   ```

   Als u toegang wilt krijgen tot de crx-server, gebruikt u `https://'server':80``server` hier de naam van de server waarop de Apache-server wordt uitgevoerd.

## Een antivirus gebruiken op een server waarop AEM Forms worden uitgevoerd {#using-an-antivirus-on-server-running-aem-forms}

U kunt trage prestaties ervaren op de servers die een antivirussoftware uitvoeren. Een programma dat altijd antivirussoftware gebruikt (voor scannen op toegang) scant alle bestanden van een systeem. Het kan de server vertragen en de prestaties van de AEM Forms worden beïnvloed.

Om de prestaties te verbeteren, kunt u de antivirussoftware opdracht geven om de volgende AEM Forms bestanden en mappen uit te sluiten van altijd (on-access) scannen:

* AEM-installatiemap. Als het niet mogelijk is de volledige map uit te sluiten, sluit u het volgende uit:

   * [AEM-installatiemap]\crx-repository\temp
   * [AEM-installatiemap]\crx-repository\repository
   * [AEM-installatiemap]\crx-repository\launchpad

* Tijdelijke map toepassingsserver. De standaardlocatie is:

   * (Jreliëf) [AEM-installatiemap]\jboss\standalone\tmp
   * (Weblogic) \Oracle\Middleware\user_projects\domains\LCDomain\servers\LCServer1\tmp
   * (Websphere) \Program Files\IBM\WebSphere\AppServer\profiles\AppSrv01\temp

* **(Alleen AEM Forms in JEE)** GDS-map (Global Document Storage). De standaardlocatie is:

   * (JBoss) [appserver root]/server/&#39;server&#39;/svcnative/DocumentStorage
   * (WebLogic) [appserverdomain]/&#39;server&#39;/adobe/LiveCycleServer/DocumentStorage
   * (WebSphere) [appserver root]/installedApps/adobe/&#39;server&#39;/DocumentStorage

* **(Alleen AEM Forms op JEE)** AEM Forms serverlogboeken en tijdelijke directory. De standaardlocatie is:

   * Serverlogboeken - [AEM Forms installatiemap]\Adobe\AEM forms\[app-server]\server\all\logs
   * Temp-map - [installatiemap]AEM Forms\temp

>[!NOTE]
>
>* Als u een andere locatie voor GDS en een tijdelijke map gebruikt, opent u AdminUI op `https://'[server]:[port]'/adminui`, navigeert u naar **Home > Instellingen > Core System Settings > Core Configurations** om de gebruikte locatie te bevestigen.

* Als de server van AEM Forms langzaam uitvoert zelfs nadat het uitsluiten van de voorgestelde folders, dan sluit ook het uitvoerbare dossier van Java (java.exe) uit.



