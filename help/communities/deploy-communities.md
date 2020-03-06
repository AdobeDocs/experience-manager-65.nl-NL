---
title: Gemeenschappen implementeren
seo-title: Gemeenschappen implementeren
description: AEM-gemeenschappen implementeren
seo-description: AEM-gemeenschappen implementeren
uuid: 18d9b424-004d-43b2-968a-318e27a93759
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
content-type: reference
topic-tags: deploying
discoiquuid: c8d7355f-5a70-40d1-bf22-62fab8002ea0
docset: aem65
translation-type: tm+mt
source-git-commit: 5035c9630b5e861f4386e1b5ab4f4ae7a8d26149

---


# Gemeenschappen implementeren{#deploying-communities}

## Voorwaarden {#prerequisites}

* [AEM 6.5-platform](/help/sites-deploying/deploy.md)

* AEM Communities-licentie

* Facultatieve vergunningen voor:

   * [Adobe Analytics voor de eigenschappen van Gemeenschappen](/help/communities/analytics.md)
   * [MongoDB voor MSRP](/help/communities/msrp.md)
   * [Adobe Cloud for ASRP](/help/communities/asrp.md)

## Controlelijst voor installatie {#installation-checklist}

**Voor het[AEM-platform](/help/sites-deploying/deploy.md#what-is-aem)**

* installeer recentste Updates [AEM 6.5](#aem64updates)

* als het gebruiken van niet de standaardhavens (4502, 4503), dan [vorm replicatieagenten](#replication-agents-on-author)
* [repliceer de crypto sleutel](#replicate-the-crypto-key)
* als het ondersteunen van globalization, [opstelling geautomatiseerde vertaling](/help/sites-administering/translation.md)(de steekproefopstelling wordt verstrekt voor ontwikkeling)

**Voor het vermogen van de[Gemeenschappen](/help/communities/overview.md)**

* als het opstellen van een [publiceer landbouwbedrijf](/help/sites-deploying/recommended-deploys.md#tarmk-farm), [identificeer de primaire uitgever](#primary-publisher)

* [de tunneldienst](#tunnel-service-on-author)
* [sociale aanmelding mogelijk maken](/help/communities/social-login.md#adobe-granite-oauth-authentication-handler)
* [Adobe Analytics configureren](/help/communities/analytics.md)
* een [standaard e-mailservice instellen](/help/communities/email.md)
* identificeer de keus voor [gedeelde opslag](/help/communities/working-with-srp.md) UGC (**SRP**)

   * als MongoDB SRP [(MSRP)](/help/communities/msrp.md)

      * [MongoDB installeren en configureren](/help/communities/msrp.md#mongodb-configuration)
      * [Solr configureren](/help/communities/solr.md)
      * [selecteer MSRP](/help/communities/srp-config.md)
   * als relationele gegevensbank SRP [(DSRP)](/help/communities/dsrp.md)

      * [installeer de bestuurder JDBC voor MySQL](#jdbc-driver-for-mysql)
      * [installeer en vorm MySQL voor DSRP](/help/communities/dsrp-mysql.md)
      * [Solr configureren](/help/communities/solr.md)
      * [selecteer DSRP](/help/communities/srp-config.md)
   * als Adobe SRP [(ASRP)](/help/communities/asrp.md)

      * met uw accountvertegenwoordiger samenwerken voor provisioning
      * [selecteer ASRP](/help/communities/srp-config.md)
   * indien JCR SRP [(JSRP)](/help/communities/jsrp.md)

      * geen gedeelde opslag UGC:

         * UGC wordt nooit gerepliceerd
         * UGC slechts zichtbaar op AEM instantie of cluster waarin het werd ingegaan
      * standaard is JSRP
   Voor de **[enablement eigenschap](/help/communities/overview.md#enablement-community)**

   * [Setup installeren en configureren](/help/communities/ffmpeg.md)
   * [installeer de bestuurder JDBC voor MySQL](#jdbc-driver-for-mysql)
   * [AEM Communities SCORM-engine installeren](#scorm-package)
   * [installeer en vorm MySQL voor enablement](/help/communities/mysql.md)






## Recentste versies {#latest-releases}

AEM 6.5 Communautaire GA-schepen met het communautaire pakket. Om over updates aan AEM 6.5 [Gemeenschappen](/help/release-notes/release-notes.md#experiencemanagercommunities)te weten te komen, verwijs [AEM 6.5 de Nota&#39;s](/help/release-notes/release-notes.md#communities-release-notes.html)van de Versie.

### AEM 6.5-updates {#aem-updates}

Beginnend in AEM 6.4, worden de updates aan Gemeenschappen geleverd als deel van AEM Cumulatieve Pakken van de Moeilijke situatie en de Pakken van de Dienst.

Voor de recentste updates aan AEM 6.5, zie Manager 6.4 van de Ervaring van [Adobe Cumulatieve de Pakken van de Moeilijke situatie en de Pakken van de Dienst](https://helpx.adobe.com/experience-manager/aem-releases-updates.html).

### Versiegeschiedenis {#version-history}

Zoals op AEM 6.4 en verder, maken de eigenschappen en de hotfixes van de Gemeenschappen AEM deel uit van cumulatieve vaste pakketten en de dienstpakken van AEM Gemeenschappen. Er zijn dus geen aparte functiepakketten.

### JDBC-stuurprogramma voor MySQL {#jdbc-driver-for-mysql}

Twee eigenschappen van Gemeenschappen gebruiken een gegevensbestand MySQL:

* voor [inschakeling](/help/communities/enablement.md) : SCORM-activiteiten registreren en lerenden
* voor [DSRP](/help/communities/dsrp.md) : het opslaan van gebruiker geproduceerde inhoud (UGC)

De verbinding MySQL moet afzonderlijk worden verkregen en worden geïnstalleerd.

De noodzakelijke stappen zijn :

1. download het ZIP archief van [https://dev.mysql.com/downloads/connector/j/](https://dev.mysql.com/downloads/connector/j/)

   * moet de versie >= 5.1.38 zijn

1. extract mysql-connector-java-&lt;version>-bin.jar (bundel) uit het archief
1. gebruik de Webconsole om de bundel te installeren en te beginnen:

   * bijvoorbeeld https://localhost:4502/system/console/bundles
   * select **`Install/Update`**
   * Bladeren... om de bundel te selecteren die uit het gedownloade ZIP-archief is gehaald
   * Controleer of* de JDBC Driver van Oracle Corporation voor MySQLcom.mysql.jdbc* actief is, en start deze indien niet (of controleer de logs)

1. als het installeren op een bestaande plaatsing nadat JDBC is gevormd, dan verbind JDBC aan de nieuwe schakelaar opnieuw door de configuratie JDBC van de Webconsole te resazen:

   * bijvoorbeeld https://localhost:4502/system/console/configMgr
   * bepaal de plaats `Day Commons JDBC Connections Pool` van configuratie
   * selecteren om te openen
   * select `Save`

1. herhaling stappen 3 en 4 op alle auteur en publiceer instanties

Verdere informatie over het installeren van bundels wordt gevonden op de pagina van de Console [van het](/help/sites-deploying/web-console.md) Web.

#### Voorbeeld : Pakket MySQL Connector geïnstalleerd {#example-installed-mysql-connector-bundle}

![](/help/communities/assets/chlimage_1-125.png)

### SCORM-pakket {#scorm-package}

Het Aandeelbare Model van de Verwijzing van Objecten van de Inhoud (SCORM) is een inzameling van normen en specificaties voor e-leren. SCORM bepaalt ook hoe de inhoud in een overdraagbaar dossier van het PIT kan worden verpakt.

De motor van SCORM van de Gemeenschappen AEM wordt vereist voor de [enablement](/help/communities/overview.md#enablement-community) eigenschap. Scorepakketten ondersteund op AEM 6.5-gemeenschappen:

* [cq-social-scorm-pakket, versie 2.3.7](https://www.adobeaemcloud.com/content/marketplace/marketplaceProxy.html?packagePath=/content/companies/public/adobe/packages/cq650/social/scorm/cq-social-scorm-pkg) met inbegrip van de [SCORM 2017.1](https://rusticisoftware.com/blog/scorm-engine-2017-released/) -motor.

**Om een pakket te installeren SCORM**

1. Installeer [cq-sociaal-vorm-pakket, versie 2.3.7](https://www.adobeaemcloud.com/content/marketplace/marketplaceProxy.html?packagePath=/content/companies/public/adobe/packages/cq650/social/scorm/cq-social-scorm-pkg) van het Aandeel van het Pakket.
1. De download `/libs/social/config/scorm/database_scormengine_data.sql` van instantie cq en voert het in mysql server uit om een bevorderd schema te creëren scormEngineDB.
1. Voeg `/content/communities/scorm/RecordResults` in het Uitgesloten bezit van Wegen in filter CSRF van `https://<hostname>:<port>/system/console/configMgr` op uitgevers toe.


#### SCORM-logboekregistratie {#scorm-logging}

Zoals geïnstalleerd, wordt al enablement activiteit uitgebreid geregistreerd aan de systeemconsole.

Indien gewenst, kan het logboekniveau aan WARN voor het `RusticiSoftware.*` pakket worden geplaatst.

Voor het werken met logboeken, zie het [Werken met de Verslagen van de Controle en de Dossiers](/help/sites-deploying/monitoring-and-maintaining.md#working-with-audit-records-and-log-files)van het Logboek.

### AEM Advanced MLS {#aem-advanced-mls}

Voor de inzameling SRP (MSRP of DSRP) om gevorderd meertalig onderzoek (MLS) te steunen, worden nieuwe Solr stop-ins vereist naast een douaneschema en een Solr configuratie. Alle vereiste punten worden verpakt in een downloadbaar postdossier.

De geavanceerde die download MLS (ook als &quot;phasetwo&quot;wordt bekend) is beschikbaar bij de bewaarplaats van Adobe:

* [AEM-SOLR-MLS-phasetwo](https://repo.adobe.com/nexus/content/repositories/releases/com/adobe/tat/AEM-SOLR-MLS-phasetwo/1.2.40/)

   * versie 1.2.40, 6 april 2016
   * AEM-SOLR-MLS-phasetwo-1.2.40.zip downloaden

Voor details en installatieinformatie, bezoek [Solr Configuratie](/help/communities/solr.md) voor SRP.

### Ongeveer Verbindingen aan het Aandeel van het Pakket {#about-links-to-package-share}

**Pakketten zichtbaar in Adobe AEM Cloud**

De verbindingen aan pakketten op deze pagina vereisen geen lopend geval van AEM aangezien zij aandeel op moeten verpakken `adobeaemcloud.com`. Terwijl de pakketten viewable zijn, is de `Install`knoop voor het installeren van de pakketten in Adobe ontvangen plaats. Als het voornemen om op een lokale instantie te installeren AEM, `Install`zal het selecteren in een fout resulteren.

**Hoe te op Lokale AEM Instantie installeren**

Om de pakketten te installeren zichtbaar in `adobeaemcloud.com` op een lokale instantie AEM, moet het pakket eerst aan een lokale schijf worden gedownload:

* selecteer het tabblad **Activa**
* selecteer **downloaden naar schijf**

Voor de lokale instantie AEM, gebruik pakketmanager (bijvoorbeeld [https://localhost:4502/crx/packmgr/](https://localhost:4502/crx/packmgr/)), om aan de lokale pakketbewaarplaats van AEM te uploaden.

Als u het pakket opent met pakketshare van de lokale AEM-instantie (bijvoorbeeld [https://localhost:4502/crx/packageshare/](https://localhost:4502/crx/packageshare/)), wordt de `Download`knop naar de pakketrepository van de lokale AEM-instantie gedownload.

Zodra in de pakketbewaarplaats van de lokale AEM-instantie, gebruiks pakketmanager om het pakket te installeren.

Voor meer informatie, bezoek [hoe te met Pakketten](/help/sites-administering/package-manager.md#package-share)te werken.

## Aanbevolen implementaties {#recommended-deployments}

In Gemeenschappen AEM, wordt een gemeenschappelijke opslag gebruikt om gebruiker geproduceerde inhoud (UGC) op te slaan en vaak bedoeld als leverancier van het [opslagmiddel (SRP)](/help/communities/working-with-srp.md). De geadviseerde plaatsingscentra bij het kiezen van een optie SRP voor de gemeenschappelijke opslag.

De gemeenschappelijke opslag steunt matiging van, en analysen op, UGC in publiceert milieu terwijl het elimineren van de behoefte aan [replicatie](/help/communities/sync.md) van UGC.

* [Opslag](/help/communities/working-with-srp.md) van communautaire content : bespreekt de SRP opslagopties voor AEM-gemeenschappen

* [Aanbevolen topologieën](/help/communities/topologies.md) : bespreekt de topologie om afhankelijk van gebruiksgeval en keus te gebruiken SRP

## Verbetering {#upgrading}

Wanneer u van eerdere versies van AEM naar het AEM 6.5-platform upgradt, is het belangrijk om [Upgraden naar AEM 6.5 te lezen](/help/sites-deploying/upgrade.md).

Naast het verbeteren van het platform, lees [Bevordering aan Gemeenschappen AEM 6.5](/help/communities/upgrade.md) om over de veranderingen van Gemeenschappen te leren.

## Configuraties {#configurations}

### Primaire uitgever {#primary-publisher}

Wanneer de gekozen plaatsing een [publiceer landbouwbedrijf](/help/communities/topologies.md#tarmk-publish-farm)is, dan publiceert één AEM instantie moet als **`primary publisher`** voor activiteiten worden geïdentificeerd die niet op alle instanties, zoals eigenschappen zouden moeten voorkomen die zich op **berichten baseren **of de Analyse **van** Adobe.

Door gebrek, wordt de configuratie `AEM Communities Publisher Configuration` OSGi gevormd met gecontroleerde **`Primary Publisher`** checkbox, dusdanig dat allen instanties in publiceren landbouwbedrijf zich als primair zou identificeren.

Daarom is het noodzakelijk om de configuratie op alle secundair uit te **geven publiceren instanties** om **`Primary Publisher`** checkbox uncheck te.

![](/help/communities/assets/chlimage_1-126.png)

Voor alle andere (secundaire) publiceren instanties in een publiceer landbouwbedrijf:

* inloggen met beheerdersrechten
* toegang hebben tot de [Webconsole](/help/sites-deploying/configuring-osgi.md)

   * bijvoorbeeld [https://localhost:4503/system/console/configMgr](https://localhost:4503/system/console/configMgr)

* bepaal de plaats van `AEM Communities Publisher Configuration`
* selecteer het bewerkingspictogram
* Schakel het selectievakje **Primaire uitgever** uit
* selecteren **Opslaan**

### Replicatieagents op auteur {#replication-agents-on-author}

De replicatie wordt gebruikt voor plaatsinhoud die in wordt gecreeerd publiceert milieu, zoals communautaire groepen, evenals het leiden leden en lidgroepen van het auteursmilieu gebruikend de [tunneldienst](#tunnel-service-on-author).

Voor de primaire uitgever, zorg ervoor de Agent Config [van de](/help/sites-deploying/replication.md) Replicatie correct identificeert publiceer server en erkende gebruiker. De standaard gemachtigde gebruiker, heeft `admin,` reeds de aangewezen toestemmingen (is een lid van `Communities Administrators`).

Opdat één of andere andere gebruiker de aangewezen toestemmingen heeft, moeten zij als lid aan de `administrators` gebruikersgroep (ook een lid van `Communities Administrators`) worden toegevoegd.

Er zijn twee replicatieagenten in het auteursmilieu die de vervoerconfiguratie nodig hebben om correct worden gevormd.

* heb toegang tot de console van de Replicatie op auteur

   * van de mondiale navigatie : **Hulpmiddelen, Plaatsing, Replicatie, Agenten op auteur**

* dezelfde procedure volgen voor beide agentia :

   * **Standaard Agent (publiceren)**
   * **De omgekeerde Agent van de Replicatie (publiceer omgekeerd)**

      1. selecteer de agent
      1. selecteren **bewerken**
      1. selecteer het **lusje van het Vervoer**
      1. als niet haven `4503`, geef **URI** uit om de correcte haven te specificeren

      1. als niet gebruiker `admin`, geef de **Gebruiker** en het **Wachtwoord** uit om een lid van de `administrators` gebruikersgroep te specificeren

De volgende beelden tonen de resultaten van het veranderen van de haven van 4503 in 6103 door:

#### Standaard Agent (publiceren) {#default-agent-publish}

![](/help/communities/assets/chlimage_1-127.png)

#### De omgekeerde Agent van de Replicatie (publiceer omgekeerd) {#reverse-replication-agent-publish-reverse}

![](/help/communities/assets/chlimage_1-128.png)

### De Dienst van de tunnel op Auteur {#tunnel-service-on-author}

Wanneer het gebruiken van het auteursmilieu om plaatsen [te](/help/communities/sites-console.md)creëren, [plaatseigenschappen](/help/communities/sites-console.md#modifying-site-properties) te wijzigen of communautaire leden [te](/help/communities/members.md)beheren, is het noodzakelijk om tot leden (gebruikers) toegang te hebben die in publiceren milieu worden geregistreerd, niet gebruikers die op auteur worden geregistreerd.

De tunneldienst verleent deze toegang gebruikend de replicatieagent op auteur.

Om de tunneldienst mogelijk te maken:

* over de **auteur**
* inloggen met beheerdersrechten
* als de uitgever geen localhost is:4503 of de vervoergebruiker niet is `admin`, dan [vorm de replicatieagent](#replication-agents-on-author)

* toegang hebben tot de [Console van het Web](/help/sites-deploying/configuring-osgi.md)

   * bijvoorbeeld [https://localhost:4502/system/console/configMgr](https://localhost:4502/system/console/configMgr)

* bepaal de plaats van `AEM Communities Publish Tunnel Service`
* selecteer het bewerkingspictogram
* controleer **enable **doos
* selecteren **Opslaan**

![](/help/communities/assets/chlimage_1-129.png)

### Repliceer de crypto-sleutel {#replicate-the-crypto-key}

Er zijn twee eigenschappen van Gemeenschappen AEM die alle AEM serverinstanties vereisen om de zelfde encryptiesleutels te gebruiken. Dit zijn [Analytics](/help/communities/analytics.md) en [ASRP](/help/communities/asrp.md).

Vanaf AEM 6.3 wordt het sleutelmateriaal opgeslagen in het bestandssysteem en niet meer in de repository.

Om het belangrijkste materiaal van auteur aan alle andere instanties te kopiëren, is het noodzakelijk om:

* heb toegang tot de instantie AEM, typisch een auteursinstantie, die het belangrijkste materiaal bevat om te kopiëren

   * bepaal de plaats van de `com.adobe.granite.crypto.file` bundel in het lokale dossiersysteem bijvoorbeeld,

      * `<author-aem-install-dir>/crx-quickstart/launchpad/felix/bundle21`
      * het `bundle.info` dossier zal de bundel identificeren
   * navigeer in de gegevensomslag bijvoorbeeld,

      * `<author-aem-install-dir>/crx-quickstart/launchpad/felix/bundle21/data`
   * kopieer de foto en hoofddossiers



* voor elke AEM-doelinstantie

   * navigeer in de gegevensomslag bijvoorbeeld,

      * `<publish-aem-install-dir>/crx-quickstart/launchpad/felix/bundle21/data`
   * plak de twee eerder gekopieerde dossiers
   * het is noodzakelijk om de bundel van Granite Crypto te [verfrissen](#refresh-the-granite-crypto-bundle) als de doelAEM instantie momenteel loopt


>[!CAUTION]
>
>Als een andere veiligheidseigenschap reeds is gevormd die op de crypto sleutels gebaseerd is, dan kon het herhalen van de crypto sleutels de configuratie beschadigen. Voor hulp, [contacteer klantenzorg](https://helpx.adobe.com/marketing-cloud/contact-support.html).

#### Repository Replication {#repository-replication}

Het hebben van het belangrijkste materiaal dat in de bewaarplaats wordt opgeslagen, zoals het geval voor AEM 6.2 en vroeger was, kan worden bewaard door het volgende systeembezit bij eerste opstarten van elke instantie van AEM te specificeren (die tot de aanvankelijke bewaarplaats leidt):

* `-Dcom.adobe.granite.crypto.file.disable=true`

>[!NOTE]
>
>Het is belangrijk om te verifiëren dat de [replicatieagent op auteur](#replication-agents-on-author) correct wordt gevormd.

Met het belangrijkste materiaal dat in de bewaarplaats wordt opgeslagen, is de manier om de crypto sleutel van auteur aan andere instanties te herhalen als volgt:

Het gebruiken van [CRXDE Lite](/help/sites-developing/developing-with-crxde-lite.md) :

* bladeren naar [https://&lt;server>:&lt;port>/crx/de](https://localhost:4502/crx/de)
* select `/etc/key`
* open `Replication` tabblad
* select `Replicate`

* [verfrist de Granite Crypto bundel](#refresh-the-granite-crypto-bundle)

![](/help/communities/assets/chlimage_1-130.png)

#### Verfris de Granite Crypto Bundel {#refresh-the-granite-crypto-bundle}

* op elke publiceer instantie, heb toegang tot de Console van het [Web](/help/sites-deploying/configuring-osgi.md)

   * bijvoorbeeld [https://&lt;server>:&lt;port>/systeem/console/bundels](https://localhost:4503/system/console/bundles)

* bepaal de plaats van `Adobe Granite Crypto Support` bundel (com.adobe.granite.crypto)
* selecteren **Vernieuwen**

![](/help/communities/assets/chlimage_1-131.png)

* na een ogenblik, zou een **Succes **dialoog moeten verschijnen:
   `Operation completed successfully.`

### Apache HTTP Server {#apache-http-server}

Als het gebruiken van de server van HTTP Apache, zorg ervoor dat u de correcte servernaam voor alle relevante ingangen gebruikt.

In het bijzonder, ben zorgvuldig om de correcte servernaam, niet `localhost`, in te gebruiken `RedirectMatch`.

#### httpd.conf-monster {#httpd-conf-sample}

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

### Verzender {#dispatcher}

Als het gebruiken van een Verzender, zie:

* AEM&#39;s [Dispatcher](https://helpx.adobe.com/experience-manager/dispatcher/using/dispatcher.html) -documentatie
* [Dispatcher installeren](https://helpx.adobe.com/experience-manager/dispatcher/using/dispatcher-install.html)
* [Dispatcher configureren voor Gemeenschappen](/help/communities/dispatcher.md)
* [Bekende problemen](/help/communities/troubleshooting.md#dispatcher-refetch-fails)

## Verwante documentatie van Gemeenschappen {#related-communities-documentation}

* Bezoek de [Beheerderende Plaatsen](/help/communities/administer-landing.md) van Gemeenschappen om over het creëren van een communautaire plaats te leren, vormend communautaire plaatsmalplaatjes, het modereren van communautaire inhoud, het leiden leden, en het vormen overseinen.

* Bezoek de [Ontwikkelende Gemeenschappen](/help/communities/communities.md) om over het sociale componentenkader (SCF) te leren en het aanpassen van de componenten en de eigenschappen van Gemeenschappen.

* Bezoek de Componenten [van de Gemeenschappen van de](/help/communities/author-communities.md) Auteurs om te leren hoe te auteur met en de componenten van Gemeenschappen te vormen.

