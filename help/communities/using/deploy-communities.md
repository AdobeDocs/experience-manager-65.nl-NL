---
title: Gemeenschappen inzetten
seo-title: Deploying Communities
description: AEM Communities implementeren
seo-description: How to deploy AEM Communities
content-type: reference
topic-tags: deploying
source-git-commit: 14a33b14043869614efcdbf8cb413333d0fa644b
workflow-type: tm+mt
source-wordcount: '1881'
ht-degree: 1%

---


# Gemeenschappen inzetten{#deploying-communities}

## Vereisten {#prerequisites}

* [AEM 6,5 Platform](/help/sites-deploying/deploy.md)

* AEM Communities-licentie

* Optionele licenties voor:

   * [Functies van Adobe Analytics for Communities](/help/communities/analytics.md)
   * [MongoDB voor MSRP](/help/communities/msrp.md)
   * [Adobe Cloud voor ASRP](/help/communities/asrp.md)

## Controlelijst voor installatie {#installation-checklist}

**Voor de [AEM](/help/sites-deploying/deploy.md#what-is-aem)**:

* De nieuwste [AEM 6.5 Updates](#aem64updates).

* Als u de standaardpoorten niet gebruikt (4502, 4503), dan [replicatieagents configureren](#replication-agents-on-author).
* [cryptosleutel repliceren](#replicate-the-crypto-key)
* Als we de globalisering ondersteunen, [geautomatiseerde omzetting instellen](/help/sites-administering/translation.md)
(voorbeeldinstelling is beschikbaar voor ontwikkeling).

**Voor de [Gemeenschappen](/help/communities/overview.md)**:

* Indien het opstellen van een [publicatiebedrijf](/help/sites-deploying/recommended-deploys.md#tarmk-farm), [de primaire uitgever identificeren](#primary-publisher)

* [De tunnelservice inschakelen](#tunnel-service-on-author)
* [Sociale aanmelding inschakelen](/help/communities/social-login.md#adobe-granite-oauth-authentication-handler)
* [Adobe Analytics configureren](/help/communities/analytics.md)
* Een [standaard e-mailservice](/help/communities/email.md)
* De keuze voor [gedeelde UGC-opslag](/help/communities/working-with-srp.md) (**SRP**)

   * Indien MongoDB SRP [(MSRP)](/help/communities/msrp.md)

      * [MongoDB installeren en configureren](/help/communities/msrp.md#mongodb-configuration)
      * [Solr configureren](/help/communities/solr.md)
      * [Selecteer MSRP](/help/communities/srp-config.md)
   * Indien relationele database SRP [(DSRP)](/help/communities/dsrp.md)

      * [Installeer het JDBC-stuurprogramma voor MySQL](#jdbc-driver-for-mysql)
      * [Installeer en vorm MySQL voor DSRP](/help/communities/dsrp-mysql.md)
      * [Solr configureren](/help/communities/solr.md)
      * [DSRP selecteren](/help/communities/srp-config.md)
   * Indien Adobe SRP [(ASRP)](/help/communities/asrp.md)

      * Werk voor provisioning met uw accountvertegenwoordiger.
      * [Selecteer ASRP](/help/communities/srp-config.md)
   * Als JCR SRP [(JSRP)](/help/communities/jsrp.md)

      * Geen gedeelde UGC-opslag:

         * UGC wordt nooit gerepliceerd.
         * UGC is alleen zichtbaar op AEM instantie of cluster waarin het is ingevoerd.
      * Standaard is JSRP

   Voor de **[enablement, functie](/help/communities/overview.md#enablement-community)**

   * [Mpeg installeren en configureren](/help/communities/ffmpeg.md)
   * [Installeer het JDBC-stuurprogramma voor MySQL](#jdbc-driver-for-mysql)
   * [AEM Communities SCORM-engine installeren](#scorm-package)
   * [MySQL voor activering installeren en configureren](/help/communities/mysql.md)






## Laatste releases {#latest-releases}

AEM 6.5 Communautaire algemene vergadering omvat het communautaire pakket. Informatie over updates van AEM 6.5 [Gemeenschappen](/help/release-notes/release-notes.md#experiencemanagercommunities), raadpleegt u [AEM 6.5 Opmerkingen bij de release](/help/release-notes/release-notes.md#communities-release-notes.html).

### AEM 6.5 Updates {#aem-updates}

Vanaf AEM 6.4 worden updates aan de Gemeenschappen geleverd als onderdeel van AEM Cumulative Fix Packs en Service Packs.

Voor de meest recente updates van AEM 6.5 raadpleegt u [Adobe Experience Manager 6.4 Cumulatief repareren van pakketten en servicepacks](https://helpx.adobe.com/experience-manager/aem-releases-updates.html).

### Versiehistorie {#version-history}

Net als bij AEM 6.4 en hoger maken AEM Communities-functies en hotfixes deel uit van AEM Communities-pakketten voor cumulatieve probleemoplossingen en servicepacks. Er zijn dus geen aparte kenmerkpakketten.

### JDBC-stuurprogramma voor MySQL {#jdbc-driver-for-mysql}

Twee eigenschappen van Gemeenschappen gebruiken een gegevensbestand MySQL:

* Voor [inschakelen](/help/communities/enablement.md): SCORM-activiteiten en -studenten opnemen
* Voor [DSRP](/help/communities/dsrp.md): door de gebruiker gegenereerde inhoud opslaan (UGC)

De MySQL-connector moet afzonderlijk worden opgehaald en geïnstalleerd.

De noodzakelijke stappen zijn:

1. Download het ZIP-archief van [https://dev.mysql.com/downloads/connector/j/](https://dev.mysql.com/downloads/connector/j/)

   * Versie moet >= 5.1.38 zijn

1. Extraheren `mysql-connector-java-&lt;version&gt;-bin.jar (bundle) from the archive`
1. Gebruik de webconsole om de bundel te installeren en te starten:

   * Bijvoorbeeld https://localhost:4502/system/console/bundles
   * Selecteer **`Install/Update`**
   * Bladeren... om de bundel te selecteren die uit het gedownloade ZIP-archief is geëxtraheerd
   * Controleren of *JDBC-stuurprogramma van oracle Corporation voor MySQLcom.mysql.jdbc* is actief en start deze als dit niet het geval is (of controleer de logboeken)

1. Als het installeren op een bestaande plaatsing nadat JDBC is gevormd, dan opnieuw bindt JDBC aan de nieuwe schakelaar door de configuratie JDBC van de Webconsole op te slaan:

   * Bijvoorbeeld https://localhost:4502/system/console/configMgr
   * Zoeken `Day Commons JDBC Connections Pool` en selecteer deze om de configuratie te openen.
   * Selecteer `Save`.

1. Herhaal stap 3 en 4 op alle auteur en publiceer instanties.

Meer informatie over het installeren van bundels vindt u op de [Webconsole](/help/sites-deploying/web-console.md#bundles) pagina.

#### Voorbeeld: MySQL-connectorbundel is geïnstalleerd {#example-installed-mysql-connector-bundle}

![](../assets/mysql-connector.png)

### SCORM-pakket {#scorm-package}

Shareable Content Object Reference Model (SCORM) is een verzameling standaarden en specificaties voor e-learning. SCORM definieert ook hoe inhoud kan worden verpakt in een overdraagbaar ZIP-bestand.

De AEM Communities SCORM-engine is vereist voor de [inschakelen](/help/communities/overview.md#enablement-community) gebruiken. Scorepakketten ondersteund op AEM 6.5-gemeenschappen:

* [cq-social-scorm-package, versie 2.3.7](https://www.adobeaemcloud.com/content/marketplace/marketplaceProxy.html?packagePath=/content/companies/public/adobe/packages/cq650/social/scorm/cq-social-scorm-pkg) die de [SCORM 2017.1](https://rusticisoftware.com/blog/scorm-engine-2017-released/) motor.

**Een SCORM-pakket installeren**

1. Installeer de [cq-social-scorm-package, versie 2.3.7](https://www.adobeaemcloud.com/content/marketplace/marketplaceProxy.html?packagePath=/content/companies/public/adobe/packages/cq650/social/scorm/cq-social-scorm-pkg) uit het pakket delen
1. Downloaden `/libs/social/config/scorm/database_scormengine_data.sql` van cq instantie en voer het in mysql server uit om een bevorderd schema te creëren scormEngineDB.
1. Toevoegen `/content/communities/scorm/RecordResults` in de eigenschap Uitgesloten paden in het CSRF-filter uit `https://<hostname>:<port>/system/console/configMgr` op uitgevers.

#### SCORM-registratie {#scorm-logging}

Zoals geïnstalleerd, wordt al enablement activiteit uitgebreid geregistreerd aan de systeemconsole.

Indien gewenst, kan het logboekniveau aan WARN voor `RusticiSoftware.*` pakket.

Voor het werken met logboeken, zie [Werken met auditrecords en logbestanden](/help/sites-deploying/monitoring-and-maintaining.md#working-with-audit-records-and-log-files).

### Geavanceerde MLS AEM {#aem-advanced-mls}

Voor de inzameling SRP (MSRP of DSRP) om geavanceerde meertalige onderzoek (MLS) te steunen, worden nieuwe stop-ins Solr vereist naast een douaneschema en de configuratie Solr. Alle vereiste items worden verpakt in een ZIP-bestand dat kan worden gedownload.

De geavanceerde MLS-download (ook wel &#39;phasetwo&#39; genoemd) is beschikbaar in de gegevensopslagruimte van de Adobe:

* [AEM-SOLR-MLS-fasetwo](https://repo1.maven.org/maven2/com/adobe/tat/AEM-SOLR-MLS-phasetwo/1.2.40/)

   * Versie 1.2.40, 6 april 2016
   * Download AEM-SOLR-MLS-phasetwo-1.2.40.zip

Ga voor meer informatie en installatie-informatie naar [Solr-configuratie](/help/communities/solr.md) voor SRP.

### Info over Koppelingen naar pakket delen {#about-links-to-package-share}

**Pakketten zichtbaar in Adobe AEM Cloud**

Voor de koppelingen naar pakketten op deze pagina is geen actieve versie van AEM vereist, aangezien deze zijn bestemd voor het verpakken van delen op `adobeaemcloud.com`. Als de pakketten kunnen worden weergegeven, worden de `Install` -knop is voor het installeren van de pakketten op een door Adobe gehoste site. Als u van plan bent op een lokale AEM te installeren, selecteert u `Install` resulteert in een fout.

**Installeren op lokale AEM**

De pakketten installeren die zichtbaar zijn in `adobeaemcloud.com` op een lokale AEM moet het pakket eerst naar een lokale schijf worden gedownload:

* Selecteer **Activa** tab
* Selecteren **downloaden naar schijf**

Gebruik pakketbeheer in de lokale AEM-instantie (bijvoorbeeld [https://localhost:4502/crx/packmgr/](https://localhost:4502/crx/packmgr/)), om te uploaden naar de lokale AEM.

U kunt het pakket ook openen met het pakket door het lokale AEM te delen (bijvoorbeeld [https://localhost:4502/crx/packageshare/](https://localhost:4502/crx/packageshare/)), de `Download` De knop wordt gedownload naar de pakketdataopslag van de lokale AEM.

Eenmaal in de pakketopslagplaats van de lokale AEM-instantie, gebruikt u pakketbeheer om het pakket te installeren.

Ga voor meer informatie naar [Werken met pakketten](/help/sites-administering/package-manager.md#package-share).

## Aanbevolen implementaties {#recommended-deployments}

In AEM Communities, wordt een gemeenschappelijke opslag gebruikt om gebruiker geproduceerde inhoud (UGC) op te slaan en vaak bedoeld als [Storage Resource Provider (SRP)](/help/communities/working-with-srp.md). De geadviseerde plaatsingscentra bij het kiezen van een optie SRP voor de gemeenschappelijke opslag.

De gemeenschappelijke opslag steunt matiging van, en analyses op UGC in het publicatiemilieu terwijl het elimineren van de behoefte aan [replicatie](/help/communities/sync.md) van UGC.

* [Community Content Store](/help/communities/working-with-srp.md) : bespreekt de opslagopties SRP voor AEM gemeenschappen

* [Aanbevolen topologieën](/help/communities/topologies.md) : bespreekt de topologie om afhankelijk van gebruiksgeval en keus te gebruiken SRP

## Bijwerken {#upgrading}

Wanneer u vanaf eerdere versies van AEM een upgrade uitvoert naar het AEM 6.5-platform, is het belangrijk dat u [Upgrade uitvoeren naar AEM 6.5](/help/sites-deploying/upgrade.md).

Naast het upgraden van het platform, leest u [Upgrade uitvoeren naar AEM Communities 6.5](/help/communities/upgrade.md) voor meer informatie over wijzigingen in de Gemeenschappen.

## Configuraties {#configurations}

### Primaire uitgever {#primary-publisher}

Wanneer de gekozen implementatie een [publicatiebedrijf](/help/communities/topologies.md#tarmk-publish-farm)moet vervolgens één AEM publicatieexemplaar worden geïdentificeerd als de **`primary publisher`** voor activiteiten die niet in alle gevallen moeten plaatsvinden, zoals functies die **meldingen** of **Adobe Analytics**.

Standaard worden de `AEM Communities Publisher Configuration` De configuratie OSGi wordt gevormd met **`Primary Publisher`** selectievakje ingeschakeld, zodat alle publicatieinstanties in een publicatiebedrijf zichzelf als primair herkennen.

Daarom moet **bewerk de configuratie op alle secundaire publicatieinstanties** om de controle van **`Primary Publisher`** selectievakje.

![](../assets/primary-publisher.png)

Voor alle andere (secundaire) publiceer instanties in publiceer landbouwbedrijf:

* Aanmelden met beheerdersrechten
* Toegang krijgen tot [webconsole](/help/sites-deploying/configuring-osgi.md)

   * Bijvoorbeeld: [https://localhost:4503/system/console/configMgr](https://localhost:4503/system/console/configMgr)

* Zoek de `AEM Communities Publisher Configuration`
* Het bewerkingspictogram selecteren
* Schakel het selectievakje **Primaire uitgever** selectievakje
* Selecteren **Opslaan**

### Replicatieagents op auteur {#replication-agents-on-author}

Replicatie wordt gebruikt voor site-inhoud die in de publicatieomgeving is gemaakt, zoals groepen uit de gebruikersgemeenschap, en voor het beheren van leden en lidgroepen vanuit de auteursomgeving met behulp van de [tunneldienst](#tunnel-service-on-author).

Voor de primaire uitgever zorg ervoor [Replication Agent Config](/help/sites-deploying/replication.md) geeft de publicatieserver en de geautoriseerde gebruiker correct aan. De standaard geoorloofde gebruiker, `admin` beschikt al over de juiste machtigingen (is lid van `Communities Administrators`).

Als een andere gebruiker over de juiste machtigingen moet beschikken, moet hij of zij als lid aan de `administrators` gebruikersgroep (ook lid van `Communities Administrators`).

Er zijn twee replicatieagenten in het auteursmilieu die de vervoerconfiguratie nodig hebben correct worden gevormd.

* De console van de Replicatie van de toegang op auteur

   * Van globale navigatie: **Gereedschappen, implementatie, replicatie, agents op auteur**

* Volg de zelfde procedure voor beide agenten:

   * **Standaardagent (publiceren)**
   * **Reverse Replication Agent (publiceren reverse)**

      1. Selecteer de agent.
      1. Selecteren **bewerken**.
      1. Selecteer **Vervoer** tab
      1. Indien niet poort `4503`, bewerkt u de **URI** om de juiste poort op te geven.

      1. Indien niet gebruiker `admin`, bewerkt u de **Gebruiker** en **Wachtwoord** om een lid van de `administrators` gebruikersgroep.

In de volgende afbeeldingen ziet u de resultaten van het wijzigen van de poort van 4503 in 6103 door:

#### Standaardagent (publiceren) {#default-agent-publish}

![configure-Limieten](../assets/default-agent-publish.png)

#### Reverse Replication Agent (publiceren reverse) {#reverse-replication-agent-publish-reverse}

![](../assets/reverse-replication-agent.png)

### Tunnelservice op auteur {#tunnel-service-on-author}

Wanneer u de ontwerpomgeving gebruikt voor [sites maken](/help/communities/sites-console.md), [site-eigenschappen wijzigen](/help/communities/sites-console.md#modifying-site-properties) of [leden van de gemeenschap beheren](/help/communities/members.md), is het noodzakelijk om toegang te krijgen tot leden (gebruikers) die zijn geregistreerd in de publicatieomgeving, niet tot gebruikers die zijn geregistreerd bij de auteur.

De tunneldienst verleent deze toegang gebruikend de replicatieagent op auteur.

Om de tunneldienst toe te laten:

* Aan **auteur**, aanmelden met beheerdersrechten.
* Als de uitgever niet localhost is:4503 of de vervoergebruiker niet `admin`vervolgens [vorm de replicatieagent](#replication-agents-on-author).

* Toegang krijgen tot [Webconsole](/help/sites-deploying/configuring-osgi.md)

   * Bijvoorbeeld: [https://localhost:4502/system/console/configMgr](https://localhost:4502/system/console/configMgr)

* Zoek de `AEM Communities Publish Tunnel Service`
* Het bewerkingspictogram selecteren
* Selecteer **enable** selectievakje
* selecteren **Opslaan**

![](../assets/tunnel-service.png)

### De cryptosleutel dupliceren {#replicate-the-crypto-key}

Er zijn twee eigenschappen van AEM Communities die alle AEM serverinstanties vereisen om de zelfde encryptiesleutels te gebruiken. Dit zijn [Analyse](/help/communities/analytics.md) en [ASRP](/help/communities/asrp.md).

Vanaf AEM 6.3 wordt het sleutelmateriaal opgeslagen in het bestandssysteem en niet langer in de gegevensopslagruimte.

Om het belangrijkste materiaal van auteur aan alle andere instanties te kopiëren is het noodzakelijk:

* Toegang krijgen tot de AEM instantie, doorgaans een instantie van de auteur, die het te kopiëren toetsmateriaal bevat

   * Zoek de `com.adobe.granite.crypto.file` bundelen in het lokale bestandssysteem

      Bijvoorbeeld,

      * `<author-aem-install-dir>/crx-quickstart/launchpad/felix/bundle21`
      * De `bundle.info` bestand zal de bundel identificeren
   * Navigeer bijvoorbeeld naar de gegevensmap

      * `<author-aem-install-dir>/crx-quickstart/launchpad/felix/bundle21/data`
   * Kopieer de hoofd- en primaire knoopdossiers.



* Voor elke AEM

   * Navigeer bijvoorbeeld naar de gegevensmap

      * `<publish-aem-install-dir>/crx-quickstart/launchpad/felix/bundle21/data`
   * Plak de twee eerder gekopieerde bestanden
   * Het is noodzakelijk [De Granite Crypto-bundel vernieuwen](#refresh-the-granite-crypto-bundle) als het doel-AEM momenteel wordt uitgevoerd.


>[!CAUTION]
>
>Als een andere veiligheidseigenschap reeds is gevormd die op de crypto sleutels gebaseerd is, dan het herhalen van de crypto sleutels kon de configuratie beschadigen. Voor hulp, [contact opnemen met de klantenservice](https://helpx.adobe.com/marketing-cloud/contact-support.html).

#### Replicatie opslagplaats {#repository-replication}

Als het sleutelmateriaal in de bewaarplaats wordt opgeslagen, zoals het geval was voor AEM 6.2 en vroeger, kan het worden bewaard door het volgende systeembezit bij eerste opstarten van elke AEM instantie te specificeren (die tot de aanvankelijke bewaarplaats leidt):

* `-Dcom.adobe.granite.crypto.file.disable=true`

>[!NOTE]
>
>Het is belangrijk te controleren of de [replicatieagent bij auteur](#replication-agents-on-author) correct is geconfigureerd.

Met het zeer belangrijke materiaal dat in de bewaarplaats wordt opgeslagen, is de manier om de crypto sleutel van auteur aan andere instanties te herhalen als volgt:

Gebruiken [CRXDE Lite](/help/sites-developing/developing-with-crxde-lite.md) :

* Bladeren naar [https://&lt;server>:&lt;port>/crx/de](https://localhost:4502/crx/de)
* Selecteer `/etc/key`
* Openen `Replication` tab
* Selecteer `Replicate`

* [De Granite Crypto-bundel vernieuwen](#refresh-the-granite-crypto-bundle)

![](../assets/replicare-repository.png)

#### De graniet-cryptobundel vernieuwen {#refresh-the-granite-crypto-bundle}

* Ga bij elke publicatie-instantie naar de knop [Webconsole](/help/sites-deploying/configuring-osgi.md)

   * Bijvoorbeeld: [https://&lt;server>:&lt;port>/systeem/console/bundels](https://localhost:4503/system/console/bundles)

* Zoeken `Adobe Granite Crypto Support` bundle (com.adobe.granite.crypto)
* Selecteren **Vernieuwen**

![](../assets/refresh-granite-bundle.png)

* Na een ogenblik **Succes** wordt weergegeven:
   `Operation completed successfully.`

### Apache HTTP Server {#apache-http-server}

Als u de Apache HTTP-server gebruikt, moet u ervoor zorgen dat u de juiste servernaam gebruikt voor alle relevante vermeldingen.

Wees vooral voorzichtig met het gebruik van de juiste servernaam, niet `localhost`in de `RedirectMatch`.

#### httpd.conf, voorbeeld {#httpd-conf-sample}

```shell
<IfModule alias_module>
     # XAMPP does not have a favicon; this prevents any 404 errors which may arise.
     Redirect 404 /favicon.ico
     <Location /favicon.ico>
         ErrorDocument 404 "No favicon"
     </Location>

    # Return from "Sign Out" generates response header directing you to "/", generating a 404 error
    # The RedirectMatch resolves it correctly when modified for the target Community Site :
    RedirectMatch ^/$ https://[server name]/content/sites/engage/en.html
 ...
 </IfModule>
```

### Dispatcher {#dispatcher}

Als u een Dispatcher gebruikt, raadpleegt u:

* AEM [Dispatcher](https://helpx.adobe.com/experience-manager/dispatcher/using/dispatcher.html) documentatie
* [Dispatcher installeren](https://helpx.adobe.com/experience-manager/dispatcher/using/dispatcher-install.html)
* [Dispatcher configureren voor Gemeenschappen](/help/communities/dispatcher.md)
* [Bekende problemen](/help/communities/troubleshooting.md#dispatcher-refetch-fails)

## Verwante documentatie van Gemeenschappen {#related-communities-documentation}

* Bezoek [Communitysites beheren](/help/communities/administer-landing.md) om over het creëren van een communautaire plaats te leren, vormend communautaire plaatssjablonen, het modereren van communautaire inhoud, het leiden van leden, en het vormen overseinen.

* Bezoek [Ontwikkelingsgemeenschappen](/help/communities/communities.md) voor meer informatie over het raamwerk voor sociale componenten (SCF) en het aanpassen van onderdelen en functies van Gemeenschappen.

* Bezoek [Componenten van Gemeenschappen ontwerpen](/help/communities/author-communities.md) om te leren om met te schrijven en de componenten van de Gemeenschappen te vormen.

