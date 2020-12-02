---
title: Gemeenschappen inzetten
seo-title: Gemeenschappen inzetten
description: AEM Communities implementeren
seo-description: AEM Communities implementeren
uuid: 18d9b424-004d-43b2-968a-318e27a93759
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
content-type: reference
topic-tags: deploying
discoiquuid: c8d7355f-5a70-40d1-bf22-62fab8002ea0
docset: aem65
translation-type: tm+mt
source-git-commit: b29945dc73e85504cd42102eafb9e2bf6198c9cc
workflow-type: tm+mt
source-wordcount: '1892'
ht-degree: 0%

---


# Gemeenschappen{#deploying-communities} implementeren

## Vereisten {#prerequisites}

* [AEM 6,5 Platform](/help/sites-deploying/deploy.md)

* AEM Communities-licentie

* Optionele licenties voor:

   * [Functies van Adobe Analytics for Communities](/help/communities/analytics.md)
   * [MongoDB voor MSRP](/help/communities/msrp.md)
   * [Adobe Cloud voor ASRP](/help/communities/asrp.md)

## Controlelijst voor installatie {#installation-checklist}

**Voor het  [AEM](/help/sites-deploying/deploy.md#what-is-aem)**

* De nieuwste [AEM 6.5-updates installeren](#aem64updates)

* Als het gebruiken van niet de standaardhavens (4502, 4503), dan [vorm replicatieagenten](#replication-agents-on-author)
* [De cryptotoets dupliceren](#replicate-the-crypto-key)
* Bij ondersteuning van globalization [installatie van geautomatiseerde vertaling](/help/sites-administering/translation.md)
(voorbeeldinstelling is beschikbaar voor ontwikkeling)

**Voor het vermogen van de  [Gemeenschappen](/help/communities/overview.md)**

* Als het opstellen van [publiceer landbouwbedrijf](/help/sites-deploying/recommended-deploys.md#tarmk-farm), [identificeer de primaire uitgever](#primary-publisher)

* [De tunnelservice inschakelen](#tunnel-service-on-author)
* [Sociale aanmelding inschakelen](/help/communities/social-login.md#adobe-granite-oauth-authentication-handler)
* [Adobe Analytics configureren](/help/communities/analytics.md)
* Stel een [standaard e-mailservice](/help/communities/email.md) in
* Identificeer de keus voor [gedeelde opslag UGC](/help/communities/working-with-srp.md) (**SRP**)

   * Als MongoDB SRP [(MSRP)](/help/communities/msrp.md)

      * [MongoDB installeren en configureren](/help/communities/msrp.md#mongodb-configuration)
      * [Solr configureren](/help/communities/solr.md)
      * [Selecteer MSRP](/help/communities/srp-config.md)
   * Als relationele database SRP [(DSRP)](/help/communities/dsrp.md)

      * [Installeer het JDBC-stuurprogramma voor MySQL](#jdbc-driver-for-mysql)
      * [Installeer en vorm MySQL voor DSRP](/help/communities/dsrp-mysql.md)
      * [Solr configureren](/help/communities/solr.md)
      * [DSRP selecteren](/help/communities/srp-config.md)
   * Als Adobe SRP [(ASRP)](/help/communities/asrp.md)

      * Met uw accountvertegenwoordiger samenwerken voor provisioning
      * [Selecteer ASRP](/help/communities/srp-config.md)
   * Indien JCR SRP [(JSRP)](/help/communities/jsrp.md)

      * Geen gedeelde UGC-opslag:

         * UGC wordt nooit gerepliceerd
         * UGC is alleen zichtbaar op AEM instantie of cluster waarin de UGC is ingevoerd

         * Standaard is JSRP
   Voor de **[enablement-functie](/help/communities/overview.md#enablement-community)**

   * [Mpeg installeren en configureren](/help/communities/ffmpeg.md)
   * [Installeer het JDBC-stuurprogramma voor MySQL](#jdbc-driver-for-mysql)
   * [AEM Communities SCORM-engine installeren](#scorm-package)
   * [MySQL voor activering installeren en configureren](/help/communities/mysql.md)





## Laatste releases {#latest-releases}

AEM 6.5 Communautaire algemene vergadering omvat het communautaire pakket. Raadpleeg [AEM 6.5 Release Notes](/help/release-notes/release-notes.md#communities-release-notes.html) voor informatie over updates van AEM 6.5 [Communities](/help/release-notes/release-notes.md#experiencemanagercommunities).

### AEM 6.5 Updates {#aem-updates}

Vanaf AEM 6.4 worden updates aan de Gemeenschappen geleverd als onderdeel van AEM Cumulative Fix Packs en Service Packs.

Voor de recentste updates van AEM 6.5, zie [Adobe Experience Manager 6.4 Cumulative Fix Packs and Service Packs](https://helpx.adobe.com/experience-manager/aem-releases-updates.html).

### Versiehistorie {#version-history}

Net als bij AEM 6.4 en hoger maken AEM Communities-functies en hotfixes deel uit van AEM Communities-pakketten voor cumulatieve probleemoplossingen en servicepacks. Er zijn dus geen aparte kenmerkpakketten.

### JDBC-stuurprogramma voor MySQL {#jdbc-driver-for-mysql}

Twee eigenschappen van Gemeenschappen gebruiken een gegevensbestand MySQL:

* Voor [enablement](/help/communities/enablement.md): SCORM-activiteiten en -studenten opnemen
* Voor [DSRP](/help/communities/dsrp.md): door de gebruiker gegenereerde inhoud opslaan (UGC)

De MySQL-connector moet afzonderlijk worden opgehaald en geïnstalleerd.

De noodzakelijke stappen zijn:

1. Download het ZIP-archief van [https://dev.mysql.com/downloads/connector/j/](https://dev.mysql.com/downloads/connector/j/)

   * Versie moet >= 5.1.38 zijn

1. Extraheer mysql-connector-java-&lt;version>-bin.jar (bundel) uit het archief
1. Gebruik de webconsole om de bundel te installeren en te starten:

   * Bijvoorbeeld https://localhost:4502/system/console/bundles
   * Selecteer **`Install/Update`**
   * Bladeren... om de bundel te selecteren die uit het gedownloade ZIP-archief is geëxtraheerd
   * Controleer of het JDBC-stuurprogramma van *Oracle Corporation voor MySQLcom.mysql.jdbc* actief is en start het programma als dat niet het geval is (of controleer de logboeken)

1. Als het installeren op een bestaande plaatsing nadat JDBC is gevormd, dan opnieuw bindt JDBC aan de nieuwe schakelaar door de configuratie JDBC van de Webconsole op te slaan:
   * Bijvoorbeeld https://localhost:4502/system/console/configMgr
   * `Day Commons JDBC Connections Pool`-configuratie zoeken
   * Selecteren om te openen
   * Selecteer `Save`

1. De stappen 3 en 4 op alle auteur herhalen en instanties publiceren

Meer informatie over het installeren van bundels vindt u op de pagina [Webconsole](/help/sites-deploying/web-console.md).

#### Voorbeeld: Pakket MySQL-connector geïnstalleerd {#example-installed-mysql-connector-bundle}

![wisselbundels](assets/chlimage-bundles.png)

### SCORM-pakket {#scorm-package}

Shareable Content Object Reference Model (SCORM) is een verzameling standaarden en specificaties voor e-learning. SCORM definieert ook hoe inhoud kan worden verpakt in een overdraagbaar ZIP-bestand.

De AEM Communities SCORM-engine is vereist voor de functie [enablement](/help/communities/overview.md#enablement-community). Scorepakketten ondersteund op AEM 6.5-gemeenschappen:

* [cq-social-scorm-package, versie 2.3.7](https://www.adobeaemcloud.com/content/marketplace/marketplaceProxy.html?packagePath=/content/companies/public/adobe/packages/cq650/social/scorm/cq-social-scorm-pkg) die de  [SCORM 2017.1-](https://rusticisoftware.com/blog/scorm-engine-2017-released/) engine bevat.

**Een SCORM-pakket installeren**

1. Installeer [cq-social-scorm-package, versie 2.3.7](https://www.adobeaemcloud.com/content/marketplace/marketplaceProxy.html?packagePath=/content/companies/public/adobe/packages/cq650/social/scorm/cq-social-scorm-pkg) van het Delen van het Pakket.
1. Download `/libs/social/config/scorm/database_scormengine_data.sql` van cq instantie en voer het in mysql server uit om een bevorderd schema te creëren scormEngineDB.
1. Voeg `/content/communities/scorm/RecordResults` in Uitgesloten bezit van Wegen in filter CSRF van `https://<hostname>:<port>/system/console/configMgr` op uitgevers toe.


#### SCORM-registratie {#scorm-logging}

Zoals geïnstalleerd, wordt al enablement activiteit uitgebreid geregistreerd aan de systeemconsole.

Indien gewenst, kan het logboekniveau aan WARN voor het `RusticiSoftware.*` pakket worden geplaatst.

Voor het werken met logboeken, zie [Werken met de Verslagen van de Controle en de Dossiers van het Logboek](/help/sites-deploying/monitoring-and-maintaining.md#working-with-audit-records-and-log-files).

### Geavanceerde MLS AEM {#aem-advanced-mls}

Voor de inzameling SRP (MSRP of DSRP) om geavanceerde meertalige onderzoek (MLS) te steunen, worden nieuwe stop-ins Solr vereist naast een douaneschema en de configuratie Solr. Alle vereiste items worden verpakt in een ZIP-bestand dat kan worden gedownload.

De geavanceerde MLS-download (ook wel &#39;phasetwo&#39; genoemd) is beschikbaar in de gegevensopslagruimte van de Adobe:

* [AEM-SOLR-MLS-fasetwo](https://repo.adobe.com/nexus/content/repositories/releases/com/adobe/tat/AEM-SOLR-MLS-phasetwo/1.2.40/)

   * Versie 1.2.40, 6 april 2016
   * Download AEM-SOLR-MLS-phasetwo-1.2.40.zip

Voor details en installatieinformatie, bezoek [Solr Configuratie](/help/communities/solr.md) voor SRP.

### Info over Koppelingen naar pakket delen {#about-links-to-package-share}

**Pakketten zichtbaar in Adobe AEM Cloud**

Voor de koppelingen naar pakketten op deze pagina is geen actieve versie van AEM vereist, aangezien deze bestemd zijn om gedeelde pakketten op `adobeaemcloud.com` te plaatsen. Terwijl de pakketten zichtbaar zijn, is de `Install` knoop voor het installeren van de pakketten in een op Adobe ontvangen plaats. Als u `Install` selecteert als u van plan bent te installeren op een lokale AEM, treedt er een fout op.

**Installeren op lokale AEM**

Als u de pakketten die zichtbaar zijn in `adobeaemcloud.com` op een lokale AEM-instantie wilt installeren, moet het pakket eerst naar een lokale schijf worden gedownload:

* Selecteer het tabblad **Middelen**
* Selecteer **downloaden naar schijf**

Gebruik in de lokale AEM-instantie pakketbeheer (bijvoorbeeld [https://localhost:4502/crx/packmgr/](https://localhost:4502/crx/packmgr/)) om te uploaden naar de lokale AEM pakketopslagplaats.

Als u het pakket ook opent via pakketshare van de lokale AEM-instantie (bijvoorbeeld [https://localhost:4502/crx/packageshare/](https://localhost:4502/crx/packageshare/)), wordt de knop `Download` gedownload naar de pakketopslagplaats van de lokale AEM-instantie.

Eenmaal in de pakketopslagplaats van de lokale AEM-instantie, gebruikt u pakketbeheer om het pakket te installeren.

Voor meer informatie, bezoek [Hoe te met Pakketten](/help/sites-administering/package-manager.md#package-share) te werken.

## Aanbevolen implementaties {#recommended-deployments}

In AEM Communities, wordt een gemeenschappelijke opslag gebruikt om gebruiker geproduceerde inhoud (UGC) op te slaan en vaak bedoeld als [opslagmiddelleverancier (SRP)](/help/communities/working-with-srp.md). De geadviseerde plaatsingscentra bij het kiezen van een optie SRP voor de gemeenschappelijke opslag.

De gemeenschappelijke opslag steunt moderatie van, en analytische op, UGC in het publicatiemilieu terwijl het elimineren van de behoefte aan [replicatie](/help/communities/sync.md) van UGC.

* [Community Content Store](/help/communities/working-with-srp.md) : bespreekt de opslagopties SRP voor AEM gemeenschappen

* [Aanbevolen technologieën](/help/communities/topologies.md) : bespreekt de topologie om afhankelijk van gebruiksgeval en keus te gebruiken SRP

## {#upgrading} bijwerken

Wanneer u een upgrade uitvoert naar het AEM 6.5-platform van eerdere versies van AEM, is het belangrijk [Upgraden naar AEM 6.5](/help/sites-deploying/upgrade.md) te lezen.

Lees [Upgraden naar AEM Communities 6.5](/help/communities/upgrade.md) om meer te weten te komen over de wijzigingen in de Gemeenschappen, naast het upgraden van het platform.

## Configuraties {#configurations}

### Primaire uitgever {#primary-publisher}

Wanneer de gekozen implementatie een [publicatiecentrum](/help/communities/topologies.md#tarmk-publish-farm) is, moet één AEM publicatieexemplaar worden geïdentificeerd als **`primary publisher`** voor activiteiten die niet in alle gevallen zouden moeten voorkomen, zoals eigenschappen die op **meldingen** of **Adobe Analytics** baseren.

Door gebrek, wordt de `AEM Communities Publisher Configuration` configuratie OSGi gevormd met **`Primary Publisher`** gecontroleerd checkbox, zodat alle publiceer instanties in een publicatielandbouwbedrijf zich als primair zou identificeren.

Daarom is het noodzakelijk om **de configuratie op alle secundaire publicatieinstanties** uit te geven om **`Primary Publisher`** checkbox uit te schakelen.

![chlimage_1-411](assets/chlimage_1-411.png)

Voor alle andere (secundaire) publiceer instanties in publiceer landbouwbedrijf:

* Aanmelden met beheerdersrechten
* Toegang tot de [webconsole](/help/sites-deploying/configuring-osgi.md)

   * Bijvoorbeeld [https://localhost:4503/system/console/configMgr](https://localhost:4503/system/console/configMgr)

* `AEM Communities Publisher Configuration` zoeken
* Het bewerkingspictogram selecteren
* Schakel het selectievakje **Primaire uitgever** uit
* Selecteer **Opslaan**

### Replicatieagents op auteur {#replication-agents-on-author}

Replicatie wordt gebruikt voor site-inhoud die in de publicatieomgeving is gemaakt, zoals groepen uit de gebruikersgemeenschap, en voor het beheren van leden en lidgroepen vanuit de auteursomgeving met de [tunnelservice](#tunnel-service-on-author).

Voor de primaire uitgever, zorg ervoor [Replication Agent Config](/help/sites-deploying/replication.md) correct de publicatieserver en geautoriseerde gebruiker identificeert. De standaard gemachtigde gebruiker, `admin,` heeft reeds de aangewezen toestemmingen (is een lid van `Communities Administrators`).

Als een andere gebruiker over de juiste machtigingen beschikt, moet hij of zij als lid worden toegevoegd aan de gebruikersgroep `administrators` (ook een lid van `Communities Administrators`).

Er zijn twee replicatieagenten in het auteursmilieu die de vervoerconfiguratie nodig hebben correct worden gevormd.

* De console van de Replicatie van de toegang op auteur

   * Navigeer vanuit globale navigatie naar **[!UICONTROL Tools]** > **[!UICONTROL Deployment]** > **[!UICONTROL Replication]** > **[!UICONTROL Agents on author]**

* Volg de zelfde procedure voor beide agenten:

   * **Standaardagent (publiceren)**
   * **Reverse Replication Agent (publiceren reverse)**

      1. Selecteer de agent
      1. Selecteer **edit**
      1. Selecteer de **tab Transport**
      1. Als geen poort `4503` is, bewerkt u **URI** om de juiste poort op te geven

      1. Als geen gebruiker `admin`, geef **Gebruiker** en **Wachtwoord** uit om een lid van `administrators` gebruikersgroep te specificeren

In de volgende afbeeldingen ziet u de resultaten van het wijzigen van de poort van 4503 in 6103 door:

#### Standaardagent (publiceren) {#default-agent-publish}

![chlimage_1-412](assets/chlimage_1-412.png)

#### Reverse Replication Agent (publish reverse) {#reverse-replication-agent-publish-reverse}

![chlimage_1-413](assets/chlimage_1-413.png)

### Tunnelservice op auteur {#tunnel-service-on-author}

Wanneer u de auteursomgeving gebruikt om [sites te maken](/help/communities/sites-console.md), [site-eigenschappen te wijzigen](/help/communities/sites-console.md#modifying-site-properties) of [leden van de gebruikersgemeenschap te beheren](/help/communities/members.md), is het nodig om leden (gebruikers) te benaderen die in de publicatieomgeving zijn geregistreerd, niet gebruikers die bij de auteur zijn geregistreerd.

De tunneldienst verleent deze toegang gebruikend de replicatieagent op auteur.

Om de tunneldienst toe te laten:

* Meld u aan met beheerdersrechten voor de auteur.
* Als de uitgever niet localhost:4503 is of de vervoergebruiker niet `admin` is,
dan [vorm de replicatieagent](#replication-agents-on-author)

* Toegang tot de [webconsole](/help/sites-deploying/configuring-osgi.md)

   * Bijvoorbeeld [https://localhost:4502/system/console/configMgr](https://localhost:4502/system/console/configMgr)

* `AEM Communities Publish Tunnel Service` zoeken
* Het bewerkingspictogram selecteren
* Schakel het selectievakje **enable** in
* Selecteer **Opslaan**

   ![chlimage_1-414](assets/chlimage_1-414.png)

### Repliceer de Crypto Sleutel {#replicate-the-crypto-key}

Er zijn twee eigenschappen van AEM Communities die alle AEM serverinstanties vereisen om de zelfde encryptiesleutels te gebruiken. Dit zijn [Analytics](/help/communities/analytics.md) en [ASRP](/help/communities/asrp.md).

Vanaf AEM 6.3 wordt het sleutelmateriaal opgeslagen in het bestandssysteem en niet langer in de gegevensopslagruimte.

Om het belangrijkste materiaal van auteur aan alle andere instanties te kopiëren is het noodzakelijk:

* Toegang krijgen tot de AEM instantie, doorgaans een instantie van de auteur, die het te kopiëren toetsmateriaal bevat

   * Zoek de `com.adobe.granite.crypto.file`-bundel in het lokale bestandssysteem,
bijvoorbeeld:

      * `<author-aem-install-dir>/crx-quickstart/launchpad/felix/bundle21`
      * In het `bundle.info`-bestand wordt de bundel geïdentificeerd
   * Navigeer in de gegevensmap,
bijvoorbeeld:

      * `<author-aem-install-dir>/crx-quickstart/launchpad/felix/bundle21/data`

      * Kopieer de hoofd- en primaire knoopdossiers


* Voor elke AEM

   * Navigeer in de gegevensmap,
bijvoorbeeld:

      * `<publish-aem-install-dir>/crx-quickstart/launchpad/felix/bundle21/data`
   * Plak de twee eerder gekopieerde bestanden
   * Het is noodzakelijk om [de graniet Crypto-bundel](#refresh-the-granite-crypto-bundle) te vernieuwen als de doel-AEM momenteel wordt uitgevoerd


>[!CAUTION]
>
>Als een andere veiligheidseigenschap reeds is gevormd die op de crypto sleutels gebaseerd is, dan het herhalen van de crypto sleutels kon de configuratie beschadigen. Neem voor hulp [contact op met de klantenservice](https://helpx.adobe.com/marketing-cloud/contact-support.html).

#### Replicatie opslagplaats {#repository-replication}

Als het sleutelmateriaal in de bewaarplaats wordt opgeslagen, zoals het geval was voor AEM 6.2 en vroeger, kan het worden bewaard door het volgende systeembezit bij eerste opstarten van elke AEM instantie te specificeren (die tot de aanvankelijke bewaarplaats leidt):

* `-Dcom.adobe.granite.crypto.file.disable=true`

>[!NOTE]
>
>Het is belangrijk om te verifiëren dat [replicatieagent op auteur](#replication-agents-on-author) correct wordt gevormd.

Met het belangrijkste materiaal dat in de bewaarplaats wordt opgeslagen, is de manier om de crypto sleutel van auteur aan andere instanties te herhalen als volgt:

Met [CRXDE Lite](/help/sites-developing/developing-with-crxde-lite.md):

* Bladeren naar [https://&lt;server>:&lt;port>/crx/de](https://localhost:4502/crx/de)
* Selecteer `/etc/key`
* Tabblad `Replication` openen
* Selecteer `Replicate`

* [De graniet-cryptobundel vernieuwen](#refresh-the-granite-crypto-bundle)

   ![chlimage_1-415](assets/chlimage_1-415.png)

#### De graniet-cryptobundel vernieuwen {#refresh-the-granite-crypto-bundle}

* Voor elke publicatieinstantie, heb toegang tot [Webconsole](/help/sites-deploying/configuring-osgi.md)

   * Bijvoorbeeld [https://&lt;server>:&lt;port>/system/console/bundles](https://localhost:4503/system/console/bundles)

* `Adobe Granite Crypto Support`-bundel zoeken (com.adobe.granite.crypto)
* Selecteer **Vernieuwen**

   ![chlimage_1-416](assets/chlimage_1-416.png)

* Na een ogenblik, zou een **Succes** dialoog moeten verschijnen:
   `Operation completed successfully.`

### Apache HTTP Server {#apache-http-server}

Als u de Apache HTTP-server gebruikt, moet u ervoor zorgen dat u de juiste servernaam gebruikt voor alle relevante vermeldingen.

Wees vooral voorzichtig met het gebruik van de juiste servernaam, niet `localhost`, in de `RedirectMatch`.

#### httpd.conf sample {#httpd-conf-sample}

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

### Verzending {#dispatcher}

Als u een Dispatcher gebruikt, raadpleegt u:

* AEM [Dispatcher](https://helpx.adobe.com/experience-manager/dispatcher/using/dispatcher.html) documentatie
* [Dispatcher installeren](https://helpx.adobe.com/experience-manager/dispatcher/using/dispatcher-install.html)
* [Dispatcher configureren voor Gemeenschappen](/help/communities/dispatcher.md)
* [Bekende problemen](/help/communities/troubleshooting.md#dispatcher-refetch-fails)

## Documentatie van verwante gemeenschappen {#related-communities-documentation}

* Bezoek [Communitysites beheren](/help/communities/administer-landing.md) voor meer informatie over het maken van een communitysite, het configureren van sjablonen voor communitysites, het moderniseren van community-inhoud, het beheren van leden en het configureren van berichten.

* Bezoek [Developing Communities](/help/communities/communities.md) voor meer informatie over het SCF (Social Component Framework) en het aanpassen van onderdelen en functies van Gemeenschappen.

* Bezoek [Authoring Communities Components](/help/communities/author-communities.md) voor meer informatie over het schrijven en configureren van Community-componenten.

