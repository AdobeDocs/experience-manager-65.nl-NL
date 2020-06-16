---
title: Gemeenschappen inzetten
seo-title: Gemeenschappen inzetten
description: Hoe te om AEM Communities op te stellen
seo-description: Hoe te om AEM Communities op te stellen
uuid: 18d9b424-004d-43b2-968a-318e27a93759
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
content-type: reference
topic-tags: deploying
discoiquuid: c8d7355f-5a70-40d1-bf22-62fab8002ea0
docset: aem65
translation-type: tm+mt
source-git-commit: df59879cfa6b0bc7eba13f679e833fabbcbe92f2
workflow-type: tm+mt
source-wordcount: '1893'
ht-degree: 0%

---


# Gemeenschappen inzetten{#deploying-communities}

## Vereisten {#prerequisites}

* [AEM 6.5-Platform](/help/sites-deploying/deploy.md)

* AEM Communities

* Optionele licenties voor:

   * [Functies van Adobe Analytics for Communities](/help/communities/analytics.md)
   * [MongoDB voor MSRP](/help/communities/msrp.md)
   * [Adobe Cloud voor ASRP](/help/communities/asrp.md)

## Controlelijst voor installatie {#installation-checklist}

**Voor het[AEM-platform](/help/sites-deploying/deploy.md#what-is-aem)**

* nieuwste [AEM 6.5-updates installeren](#aem64updates)

* als het niet gebruiken van de standaardhavens (4502, 4503), dan [vorm replicatieagenten](#replication-agents-on-author)
* [de cryptosleutel repliceren](#replicate-the-crypto-key)
* als ondersteuning wordt geboden voor globalization, [installatie van geautomatiseerde vertaling](/help/sites-administering/translation.md)(voorbeeldinstallatie is beschikbaar voor ontwikkeling)

**Voor het vermogen van de[Gemeenschappen](/help/communities/overview.md)**

* als het opstellen van [publiceer landbouwbedrijf](/help/sites-deploying/recommended-deploys.md#tarmk-farm), [identificeer de primaire uitgever](#primary-publisher)

* [de tunneldienst](#tunnel-service-on-author)
* [aanmelden via sociaal netwerk](/help/communities/social-login.md#adobe-granite-oauth-authentication-handler)
* [Adobe Analytics configureren](/help/communities/analytics.md)
* een [standaard e-mailservice instellen](/help/communities/email.md)
* identificeer de keus voor [gedeelde opslag](/help/communities/working-with-srp.md) UGC (**SRP**)

   * als MongoDB SRP [(MSRP)](/help/communities/msrp.md)

      * [MongoDB installeren en configureren](/help/communities/msrp.md#mongodb-configuration)
      * [configureren Solr](/help/communities/solr.md)
      * [selecteer MSRP](/help/communities/srp-config.md)
   * indien relationele database SRP [(DSRP)](/help/communities/dsrp.md)

      * [Installeer het JDBC-stuurprogramma voor MySQL](#jdbc-driver-for-mysql)
      * [Installeer en vorm MySQL voor DSRP](/help/communities/dsrp-mysql.md)
      * [configureren Solr](/help/communities/solr.md)
      * [selecteer DSRP](/help/communities/srp-config.md)
   * als Adobe SRP [(ASRP)](/help/communities/asrp.md)

      * met uw accountvertegenwoordiger samenwerken voor provisioning
      * [Selecteer ASRP](/help/communities/srp-config.md)
   * if JCR SRP [(JSRP)](/help/communities/jsrp.md)

      * geen gedeelde UGC-opslag:

         * UGC wordt nooit gerepliceerd
         * UGC is alleen zichtbaar op een AEM-instantie of -cluster waarin de UGC is ingevoerd
      * default is JSRP
   Voor de functie **[enablement](/help/communities/overview.md#enablement-community)**

   * [Mpeg installeren en configureren](/help/communities/ffmpeg.md)
   * [Installeer het JDBC-stuurprogramma voor MySQL](#jdbc-driver-for-mysql)
   * [AEM Communities SCORM-Engine installeren](#scorm-package)
   * [Installeer en vorm MySQL voor enablement](/help/communities/mysql.md)






## Latest Releases {#latest-releases}

AEM 6.5 Community GA wordt geleverd met het communautaire pakket. Raadpleeg de opmerkingen bij de release van [AEM 6.5 voor informatie over updates van AEM 6.5](/help/release-notes/release-notes.md#experiencemanagercommunities)Communities [](/help/release-notes/release-notes.md#communities-release-notes.html).

### AEM 6.5-updates {#aem-updates}

Vanaf AEM 6.4 worden updates aan Gemeenschappen geleverd als onderdeel van AEM Cumulative Fix Packs en Service Packs.

Voor de recentste updates van AEM 6.5, zie [Adobe Experience Manager 6.4 Cumulatieve Pakken van de Moeilijke situatie en de Pakken](https://helpx.adobe.com/experience-manager/aem-releases-updates.html)van de Dienst.

### Versiehistorie {#version-history}

Net als in AEM 6.4 en verder, maken de eigenschappen en hotfixes van AEM Communities deel uit van AEM Communities cumulatieve moeilijke fixpakken en de dienstpakken. Er zijn dus geen aparte kenmerkpakketten.

### JDBC-stuurprogramma voor MySQL {#jdbc-driver-for-mysql}

Twee eigenschappen van Gemeenschappen gebruiken een gegevensbestand MySQL:

* voor [activering](/help/communities/enablement.md) : SCORM-activiteiten en -studenten opnemen
* voor [DSRP](/help/communities/dsrp.md) : door de gebruiker gegenereerde inhoud opslaan (UGC)

De MySQL-connector moet afzonderlijk worden opgehaald en geïnstalleerd.

De noodzakelijke stappen zijn:

1. Het ZIP-archief downloaden vanaf [https://dev.mysql.com/downloads/connector/j/](https://dev.mysql.com/downloads/connector/j/)

   * version must be >= 5.1.38

1. mysql-connector-java-&lt;version>-bin.jar (bundel) ophalen uit het archief
1. gebruik de webconsole om de bundel te installeren en te starten:

   * bijvoorbeeld https://localhost:4502/system/console/bundles
   * select **`Install/Update`**
   * Bladeren... om de bundel te selecteren die uit het gedownloade ZIP-archief is geëxtraheerd
   * Controleer of* het JDBC-stuurprogramma van Oracle Corporation voor MySQLcom.mysql.jdbc* actief is en start dit als dit niet het geval is (of controleer de logboeken)

1. als het installeren op een bestaande plaatsing nadat JDBC is gevormd, dan opnieuw bindt JDBC aan de nieuwe schakelaar door de configuratie JDBC van de Webconsole op te slaan:

   * bijvoorbeeld https://localhost:4502/system/console/configMgr
   * locatie van `Day Commons JDBC Connections Pool` configuratie
   * selecteren om te openen
   * select `Save`

1. De stappen 3 en 4 op alle auteur herhalen en instanties publiceren

Meer informatie over het installeren van bundels vindt u op de pagina [Webconsole](/help/sites-deploying/web-console.md#bundles) .

#### Voorbeeld: MySQL-connectorbundel is geïnstalleerd {#example-installed-mysql-connector-bundle}

![](/help/communities/assets/chlimage_1-125.png)

### SCORM-pakket {#scorm-package}

Shareable Content Object Reference Model (SCORM) is een verzameling standaarden en specificaties voor e-learning. SCORM definieert ook hoe inhoud kan worden verpakt in een overdraagbaar ZIP-bestand.

De AEM Communities SCORM-engine is vereist voor de functie [enablement](/help/communities/overview.md#enablement-community) . Scorepakketten ondersteund op AEM 6.5-gemeenschappen:

* [cq-social-scorm-package, versie 2.3.7](https://www.adobeaemcloud.com/content/marketplace/marketplaceProxy.html?packagePath=/content/companies/public/adobe/packages/cq650/social/scorm/cq-social-scorm-pkg) die de [SCORM 2017.1](https://rusticisoftware.com/blog/scorm-engine-2017-released/) -engine bevat.

**Een SCORM-pakket installeren**

1. Installeer het [cq-social-scorm-pakket, versie 2.3.7](https://www.adobeaemcloud.com/content/marketplace/marketplaceProxy.html?packagePath=/content/companies/public/adobe/packages/cq650/social/scorm/cq-social-scorm-pkg)van het Delen van het Pakket
1. Download `/libs/social/config/scorm/database_scormengine_data.sql` van instantie cq en voer het in mysql server uit om een bevorderd schema te creëren scormEngineDB.
1. Voeg `/content/communities/scorm/RecordResults` in Uitgesloten bezit van Wegen in filter CSRF van \ toe https://<hostname>:<port>/system/console/configMgr&#39; op uitgevers.

#### SCORM-registratie {#scorm-logging}

Zoals geïnstalleerd, wordt al enablement activiteit uitgebreid geregistreerd aan de systeemconsole.

Indien gewenst, kan het logboekniveau aan WARN voor het `RusticiSoftware.*` pakket worden geplaatst.

Voor het werken met logboeken, zie het [Werken met de Verslagen van de Controle en de Dossiers](/help/sites-deploying/monitoring-and-maintaining.md#working-with-audit-records-and-log-files)van het Logboek.

### AEM Advanced MLS {#aem-advanced-mls}

Voor de inzameling SRP (MSRP of DSRP) om geavanceerde meertalige onderzoek (MLS) te steunen, worden nieuwe stop-ins Solr vereist naast een douaneschema en de configuratie Solr. Alle vereiste items worden verpakt in een ZIP-bestand dat kan worden gedownload.

De geavanceerde MLS-download (ook wel &#39;phasetwo&#39; genoemd) is beschikbaar in de Adobe-opslagplaats:

* [AEM-SOLR-MLS-fasetwo](https://repo.adobe.com/nexus/content/repositories/releases/com/adobe/tat/AEM-SOLR-MLS-phasetwo/1.2.40/)

   * versie 1.2.40, 6 april 2016
   * download AEM-SOLR-MLS-phasetwo-1.2.40.zip

Voor details en installatieinformatie, bezoek [Solr Configuratie](/help/communities/solr.md) voor SRP.

### Info over Koppelingen naar pakket delen {#about-links-to-package-share}

**Pakketten zichtbaar in Adobe AEM Cloud**

Voor de koppelingen naar pakketten op deze pagina is geen actieve AEM-instantie vereist omdat deze delen in een pakket moet plaatsen op `adobeaemcloud.com`. De pakketten kunnen wel worden weergegeven, maar u `Install`kunt ze wel installeren op een door Adobe gehoste site. Als u van plan bent te installeren op een lokale AEM-instantie, `Install`treedt er een fout op.

**Installeren in lokale AEM-instantie**

Als u de pakketten wilt installeren die zichtbaar zijn in `adobeaemcloud.com` een lokale AEM-instantie, moet het pakket eerst naar een lokale schijf worden gedownload:

* Selecteer het tabblad **Middelen**
* Selecteer **Downloaden naar schijf**

Gebruik in de lokale AEM-instantie pakketbeheer (bijvoorbeeld [https://localhost:4502/crx/packmgr/](https://localhost:4502/crx/packmgr/)) om te uploaden naar de pakketopslagplaats van de lokale AEM.

Als u het pakket ook opent via pakketshare vanuit de lokale AEM-instantie (bijvoorbeeld [https://localhost:4502/crx/packageshare/](https://localhost:4502/crx/packageshare/)), wordt de `Download`knop gedownload naar de pakketopslagplaats van de lokale AEM-instantie.

Eenmaal in de pakketopslagplaats van de lokale AEM-instantie, gebruikt u pakketbeheer om het pakket te installeren.

Voor meer informatie, bezoek [hoe te met Pakketten](/help/sites-administering/package-manager.md#package-share)werken.

## Aanbevolen implementaties {#recommended-deployments}

In AEM Communities, wordt een gemeenschappelijke opslag gebruikt om gebruiker geproduceerde inhoud (UGC) op te slaan en vaak bedoeld als leverancier van [opslagmiddel (SRP)](/help/communities/working-with-srp.md). De geadviseerde plaatsingscentra bij het kiezen van een optie SRP voor de gemeenschappelijke opslag.

De gemeenschappelijke opslag steunt matiging van, en analyses op, UGC in het publicatiemilieu terwijl het elimineren van de behoefte aan [replicatie](/help/communities/sync.md) van UGC.

* [Community Content Store](/help/communities/working-with-srp.md) : bespreekt de opslagopties SRP voor gemeenschappen AEM

* [Aanbevolen topologieën](/help/communities/topologies.md) : bespreekt de topologie om afhankelijk van gebruiksgeval en keus te gebruiken SRP

## Bijwerken {#upgrading}

Wanneer u een upgrade uitvoert naar het AEM 6.5-platform vanuit eerdere versies van AEM, is het belangrijk om [Upgrade naar AEM 6.5](/help/sites-deploying/upgrade.md)te lezen.

Lees naast het upgraden van het platform [Upgrade naar AEM Communities 6.5](/help/communities/upgrade.md) voor meer informatie over de wijzigingen in de Gemeenschappen.

## Configuraties {#configurations}

### Primaire uitgever {#primary-publisher}

Wanneer de gekozen implementatie een [publicatiefarm](/help/communities/topologies.md#tarmk-publish-farm)is, moet één AEM-publicatieexemplaar worden geïdentificeerd als de instantie **`primary publisher`** voor activiteiten die niet overal mogen plaatsvinden, zoals functies die afhankelijk zijn van **meldingen **of **Adobe Analytics**.

Door gebrek, wordt de configuratie `AEM Communities Publisher Configuration` OSGi gevormd met gecontroleerde **`Primary Publisher`** checkbox, zodat alle publiceer instanties in publiceer landbouwbedrijf zich als primair zou identificeren.

Daarom is het noodzakelijk om de configuratie op alle secundaire publiceer instanties **uit te** geven om **`Primary Publisher`** checkbox los te maken.

![](/help/communities/assets/chlimage_1-126.png)

Voor alle andere (secundaire) publiceer instanties in publiceer landbouwbedrijf:

* aanmelden met beheerdersrechten
* toegang tot de [webconsole](/help/sites-deploying/configuring-osgi.md)

   * bijvoorbeeld [https://localhost:4503/system/console/configMgr](https://localhost:4503/system/console/configMgr)

* zoek de `AEM Communities Publisher Configuration`
* Selecteer het bewerkingspictogram
* het selectievakje **Primaire uitgever** uitschakelen
* Selecteer **Opslaan**

### Replicatieagents op auteur {#replication-agents-on-author}

De replicatie wordt gebruikt voor plaatsinhoud die in het publicatiemilieu, zoals communautaire groepen wordt gecreeerd, evenals het leiden van leden en lidgroepen van het auteursmilieu gebruikend de [tunneldienst](#tunnel-service-on-author).

Voor de primaire uitgever, zorg ervoor de Agent Config [van de](/help/sites-deploying/replication.md) Replicatie correct de publicatieserver en erkende gebruiker identificeert. De standaard gemachtigde gebruiker, heeft `admin,` reeds de aangewezen toestemmingen (is een lid van `Communities Administrators`).

Als een andere gebruiker over de juiste machtigingen beschikt, moet hij of zij als lid aan de `administrators` gebruikersgroep (ook een lid van `Communities Administrators`) worden toegevoegd.

Er zijn twee replicatieagenten in het auteursmilieu die de vervoerconfiguratie nodig hebben correct worden gevormd.

* toegang tot de console van de Replicatie op auteur

   * van globale navigatie: **Gereedschappen, implementatie, replicatie, agents op auteur**

* dezelfde procedure volgen voor beide agentia :

   * **Standaardagent (publiceren)**
   * **Reverse Replication Agent (publiceren reverse)**

      1. selecteer de agent
      1. selecteren, **bewerken**
      1. Selecteer het tabblad **Vervoer**
      1. als poort `4503`, bewerk de **URI** om de juiste poort op te geven

      1. als geen gebruiker `admin`, geef de **Gebruiker** en het **Wachtwoord** uit om een lid van de `administrators` gebruikersgroep te specificeren

In de volgende afbeeldingen ziet u de resultaten van het wijzigen van de poort van 4503 in 6103 door:

#### Standaardagent (publiceren) {#default-agent-publish}

![](/help/communities/assets/chlimage_1-127.png)

#### Reverse Replication Agent (publiceren reverse) {#reverse-replication-agent-publish-reverse}

![](/help/communities/assets/chlimage_1-128.png)

### Tunnelservice op auteur {#tunnel-service-on-author}

Wanneer het gebruiken van het auteursmilieu om plaatsen [te](/help/communities/sites-console.md)creëren, [plaatseigenschappen](/help/communities/sites-console.md#modifying-site-properties) te wijzigen of communityleden [te](/help/communities/members.md)beheren, is het noodzakelijk om tot leden (gebruikers) toegang te hebben die in het publicatiemilieu worden geregistreerd, niet gebruikers die bij auteur worden geregistreerd.

De tunneldienst verleent deze toegang gebruikend de replicatieagent op auteur.

Om de tunneldienst toe te laten:

* over **auteur**
* aanmelden met beheerdersrechten
* als de uitgever niet localhost is:4503 of de vervoergebruiker niet is `admin`, dan [vorm de replicatieagent](#replication-agents-on-author)

* toegang tot de [webconsole](/help/sites-deploying/configuring-osgi.md)

   * bijvoorbeeld [https://localhost:4502/system/console/configMgr](https://localhost:4502/system/console/configMgr)

* zoek de `AEM Communities Publish Tunnel Service`
* Selecteer het bewerkingspictogram
* Schakel het selectievakje **enable **box in
* Selecteer **Opslaan**

![](/help/communities/assets/chlimage_1-129.png)

### De cryptosleutel dupliceren {#replicate-the-crypto-key}

Er zijn twee eigenschappen van AEM Communities die alle AEM serverinstanties vereisen om de zelfde encryptiesleutels te gebruiken. Dit zijn [Analytics](/help/communities/analytics.md) en [ASRP](/help/communities/asrp.md).

Vanaf AEM 6.3 wordt het sleutelmateriaal opgeslagen in het bestandssysteem en niet meer in de gegevensopslagruimte.

Om het belangrijkste materiaal van auteur aan alle andere instanties te kopiëren is het noodzakelijk:

* toegang hebben tot de instantie AEM, typisch een auteursinstantie die het belangrijkste te kopiëren materiaal bevat

   * de `com.adobe.granite.crypto.file` bundel bijvoorbeeld zoeken in het lokale bestandssysteem;

      * `<author-aem-install-dir>/crx-quickstart/launchpad/felix/bundle21`
      * in het `bundle.info` bestand wordt de bundel geïdentificeerd
   * navigeer bijvoorbeeld in de gegevensmap,

      * `<author-aem-install-dir>/crx-quickstart/launchpad/felix/bundle21/data`
   * de Mac- en primaire knooppuntbestanden kopiëren



* voor elke AEM-doelinstantie

   * navigeer bijvoorbeeld in de gegevensmap,

      * `<publish-aem-install-dir>/crx-quickstart/launchpad/felix/bundle21/data`
   * plakken de twee eerder gekopieerde bestanden
   * het is noodzakelijk om de granite Crypto-bundel [te](#refresh-the-granite-crypto-bundle) vernieuwen als de doel-AEM-instantie momenteel wordt uitgevoerd


>[!CAUTION]
>
>Als een andere veiligheidseigenschap reeds is gevormd die op de crypto sleutels gebaseerd is, dan het herhalen van de crypto sleutels kon de configuratie beschadigen. Neem voor hulp [contact op met de klantenservice](https://helpx.adobe.com/marketing-cloud/contact-support.html).

#### Replicatie opslagplaats {#repository-replication}

Als het sleutelmateriaal in de opslagplaats wordt opgeslagen, zoals het geval was voor AEM 6.2 en eerder, kan dit worden behouden door de volgende systeemeigenschap op te geven bij het eerste opstarten van elke AEM-instantie (die de eerste opslagplaats maakt):

* `-Dcom.adobe.granite.crypto.file.disable=true`

>[!NOTE]
>
>Het is belangrijk om te verifiëren dat de [replicatieagent op auteur](#replication-agents-on-author) correct wordt gevormd.

Met het zeer belangrijke materiaal dat in de bewaarplaats wordt opgeslagen, is de manier om de crypto sleutel van auteur aan andere instanties te herhalen als volgt:

Met [CRXDE Lite](/help/sites-developing/developing-with-crxde-lite.md) :

* surf naar [https://&lt;server>:&lt;port>/crx/de](https://localhost:4502/crx/de)
* select `/etc/key`
* open `Replication` tabblad
* select `Replicate`

* [De Granite Crypto-bundel vernieuwen](#refresh-the-granite-crypto-bundle)

![](/help/communities/assets/chlimage_1-130.png)

#### De graniet-cryptobundel vernieuwen {#refresh-the-granite-crypto-bundle}

* op elke publicatie-instantie toegang tot de [webconsole](/help/sites-deploying/configuring-osgi.md)

   * bijvoorbeeld [https://&lt;server>:&lt;port>/system/console/bundles](https://localhost:4503/system/console/bundles)

* locate `Adobe Granite Crypto Support` bundle (com.adobe.granite.crypto)
* selecteren **Vernieuwen**

![](/help/communities/assets/chlimage_1-131.png)

* na een ogenblik zou een **Succesdialoog **moeten verschijnen:
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

Zie bij gebruik van een Dispatcher:

* AEM&#39;s [Dispatcher](https://helpx.adobe.com/experience-manager/dispatcher/using/dispatcher.html) -documentatie
* [Dispatcher installeren](https://helpx.adobe.com/experience-manager/dispatcher/using/dispatcher-install.html)
* [Dispatcher for Communities configureren](/help/communities/dispatcher.md)
* [Bekende problemen](/help/communities/troubleshooting.md#dispatcher-refetch-fails)

## Verwante documentatie van Gemeenschappen {#related-communities-documentation}

* Bezoek [De Beheren Plaatsen](/help/communities/administer-landing.md) van Gemeenschappen om over het creëren van een communautaire plaats te leren, vormend communautaire plaatssjablonen, het modereren van communautaire inhoud, het beheren van leden, en het vormen overseinen.

* Bezoek [Ontwikkelingsgemeenschappen](/help/communities/communities.md) voor meer informatie over het sociale-componentframework (SCF) en het aanpassen van onderdelen en functies van Gemeenschappen.

* Bezoek [Authoring Communities Components](/help/communities/author-communities.md) voor meer informatie over het maken en configureren van Community-componenten.

