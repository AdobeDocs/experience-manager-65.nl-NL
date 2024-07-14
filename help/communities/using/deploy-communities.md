---
title: Gemeenschappen inzetten
description: AEM Communities implementeren
content-type: reference
topic-tags: deploying
source-git-commit: 3bcdbfc17efe1f4c6069fd97fd6a16ec41d0579e
workflow-type: tm+mt
source-wordcount: '1705'
ht-degree: 0%

---


# Gemeenschappen inzetten{#deploying-communities}

## Vereisten {#prerequisites}

* [AEM 6.5 Platform](/help/sites-deploying/deploy.md)

* AEM Communities-licentie

* Optionele licenties voor:

   * [Functies van Adobe Analytics for Communities](/help/communities/analytics.md)
   * [MongoDB voor MSRP](/help/communities/msrp.md)
   * [Adobe Cloud voor ASRP](/help/communities/asrp.md)

## Controlelijst voor installatie {#installation-checklist}

**voor het [ AEM platform](/help/sites-deploying/deploy.md#what-is-aem)**:

* Installeer de recentste [ AEM 6.5 Updates ](#aem64updates).

* Als het gebruiken van niet de standaardhavens (4502, 4503), dan [ vormt replicatieagenten ](#replication-agents-on-author).
* [cryptosleutel repliceren](#replicate-the-crypto-key)
* Als het steunen van globalization, [ opstelling geautomatiseerde vertaling ](/help/sites-administering/translation.md)
(voorbeeldinstelling is beschikbaar voor ontwikkeling).

**voor het [ vermogen van Gemeenschappen](/help/communities/overview.md)**:

* Als het opstellen van a [ landbouwbedrijf ](/help/sites-deploying/recommended-deploys.md#tarmk-farm) publiceert, [ identificeer de primaire uitgever ](#primary-publisher)

* [De tunnelservice inschakelen](#tunnel-service-on-author)
* [Sociale aanmelding inschakelen](/help/communities/social-login.md#adobe-granite-oauth-authentication-handler)
* [Adobe Analytics configureren](/help/communities/analytics.md)
* Opstelling a [ standaard e-maildienst ](/help/communities/email.md)
* Identificeer de keus voor [ gedeelde opslag UGC ](/help/communities/working-with-srp.md) (**SRP**)

   * Als MongoDB SRP [ (MSRP) ](/help/communities/msrp.md)

      * [MongoDB installeren en configureren](/help/communities/msrp.md#mongodb-configuration)
      * [Solr configureren](/help/communities/solr.md)
      * [Selecteer MSRP](/help/communities/srp-config.md)

   * Als relationele database SRP [ (DSRP) ](/help/communities/dsrp.md)

      * [Installeer het JDBC-stuurprogramma voor MySQL](#jdbc-driver-for-mysql)
      * [Installeer en vorm MySQL voor DSRP](/help/communities/dsrp-mysql.md)
      * [Solr configureren](/help/communities/solr.md)
      * [DSRP selecteren](/help/communities/srp-config.md)

   * Als Adobe SRP [ (ASRP) ](/help/communities/asrp.md)

      * Werk voor provisioning met uw accountvertegenwoordiger.
      * [Selecteer ASRP](/help/communities/srp-config.md)

   * Als JCR SRP [ (JSRP) ](/help/communities/jsrp.md)

      * Geen gedeeld UGC-archief (door de gebruiker gegenereerde inhoud):

         * UGC wordt nooit herhaald.
         * UGC is alleen zichtbaar op een AEM instantie of cluster waarin het is ingevoerd.

      * De standaardwaarde is JSRP


## Laatste releases {#latest-releases}

AEM 6.5 Communautaire algemene vergadering omvat het communautaire pakket. Meer over updates aan AEM 6.5 [ Gemeenschappen ](/help/release-notes/release-notes.md#experiencemanagercommunities) weten, zie [ AEM 6.5 de Nota&#39;s van de Versie ](/help/release-notes/release-notes.md#communities-release-notes.html).

### AEM 6.5 Updates {#aem-updates}

Vanaf AEM 6.4 worden updates aan de Gemeenschappen geleverd als onderdeel van AEM Cumulative Fix Packs en Service Packs.

Voor de recentste updates aan AEM 6.5, zie [ Adobe Experience Manager 6.4 Cumulatieve Packs en de Packs van de Dienst ](https://helpx.adobe.com/experience-manager/aem-releases-updates.html) bevestigen.

### Versiehistorie {#version-history}

Net als bij AEM 6.4 en hoger maken AEM Communities-functies en hotfixes deel uit van AEM Communities-pakketten voor cumulatieve probleemoplossingen en servicepacks. Er zijn dus geen aparte kenmerkpakketten.

### JDBC-stuurprogramma voor MySQL {#jdbc-driver-for-mysql}

De functie Eén Gemeenschappen gebruikt een MySQL-database:

* Voor [ DSRP ](/help/communities/dsrp.md): het opslaan van UGC

De MySQL-connector moet afzonderlijk worden opgehaald en geïnstalleerd.

De noodzakelijke stappen zijn:

1. Download het archief van het PIT van [ https://dev.mysql.com/downloads/connector/j/](https://dev.mysql.com/downloads/connector/j/)

   * Versie moet >= 5.1.38 zijn

1. Extraheren `mysql-connector-java-&lt;version&gt;-bin.jar (bundle) from the archive`
1. Gebruik de webconsole om de bundel te installeren en te starten:

   * Bijvoorbeeld https://localhost:4502/system/console/bundles
   * Selecteren **`Install/Update`**
   * Blader naar.. om de bundel te selecteren die u uit het gedownloade ZIP-archief hebt opgehaald
   * Controle dat {de Bestuurder JDBC van het Bedrijf van 0} Oracle voor MySQLcom.mysql.jdbc *actief is, en het begint als niet (of controleert de logboeken)*

1. Als het installeren op een bestaande plaatsing nadat JDBC is gevormd, dan opnieuw bindt JDBC aan de nieuwe schakelaar door de configuratie JDBC van de Webconsole op te slaan:

   * Bijvoorbeeld https://localhost:4502/system/console/configMgr
   * Zoek `Day Commons JDBC Connections Pool` -configuratie en selecteer deze om de configuratie te openen.
   * Selecteer `Save` .

1. Herhaal stap 3 en 4 op alle auteur en publiceer instanties.

De verdere informatie bij het installeren van bundels wordt gevonden op de [ pagina van de Console van het Web ](/help/sites-deploying/web-console.md#bundles).

#### Voorbeeld: geïnstalleerde MySQL-connectorbundel {#example-installed-mysql-connector-bundle}

![ Adobe Experience Manager Web Console MySQL Connector Bundle ](../assets/mysql-connector.png)

### Geavanceerde MLS AEM {#aem-advanced-mls}

Voor de inzameling SRP (MSRP of DSRP) om geavanceerde meertalige onderzoek (MLS) te steunen, worden nieuwe stop-ins Solr vereist naast een douaneschema en de configuratie Solr. Alle vereiste items worden verpakt in een ZIP-bestand dat kan worden gedownload.

De geavanceerde MLS-download (ook wel &#39;phasetwo&#39; genoemd) is beschikbaar in de gegevensopslagruimte van de Adobe:

* [ AEM-SOLR-MLS-phasetwo ](https://repo1.maven.org/maven2/com/adobe/tat/AEM-SOLR-MLS-phasetwo/1.2.40/)

   * Versie 1.2.40, 6 april 2016
   * Download AEM-SOLR-MLS-phasetwo-1.2.40.zip

Voor details en installatieinformatie, bezoek ](/help/communities/solr.md) Configuratie 0} Solr voor SRP.[

### Info over Koppelingen naar pakket delen {#about-links-to-package-share}

**Pakketten Zichtbaar in Adobe AEM Wolk**

Voor de koppelingen naar pakketten op deze pagina is geen actieve versie van AEM vereist, omdat deze op `adobeaemcloud.com` Delen in pakketten moeten plaatsen. De pakketten kunnen wel worden weergegeven, maar de knop `Install` is bedoeld voor de installatie van de pakketten op een door de Adobe gehoste site. Als u `Install` selecteert wanneer u op een lokale AEM wilt installeren, treedt er een fout op.

**hoe te op Lokale AEMInstantie installeren**

Als u de pakketten die zichtbaar zijn in `adobeaemcloud.com` op een lokale AEM-instantie wilt installeren, moet het pakket eerst naar een lokale schijf worden gedownload:

* Selecteer het **Assets** lusje
* Selecteer **download aan schijf**

Voor de lokale AEM instantie, gebruik een Manager van het Pakket (bijvoorbeeld, [ https://localhost:4502/crx/packmgr/ ](https://localhost:4502/crx/packmgr/)), om aan de lokale AEM pakketbewaarplaats te uploaden.

Alternatief, die tot het pakket toegang hebben gebruikend het Aandeel van het Pakket van de lokale AEM instantie (bijvoorbeeld, [ https://localhost:4502/crx/packageshare/ ](https://localhost:4502/crx/packageshare/)), `Download` knoop downloadt aan de lokale het pakketbewaarplaats van de AEM instantie.

Eenmaal in de pakketopslagplaats van de lokale AEM gebruikt u Package Manager om het pakket te installeren.

Voor meer informatie, bezoek [ hoe te met Pakketten ](/help/sites-administering/package-manager.md#package-share) werken.

## Aanbevolen implementaties {#recommended-deployments}

In AEM Communities, wordt een gemeenschappelijke opslag gebruikt om UGC op te slaan en vaak bedoeld als [ leverancier van het opslagmiddel (SRP) ](/help/communities/working-with-srp.md). De geadviseerde plaatsingscentra bij het kiezen van een optie SRP voor de gemeenschappelijke opslag.

De gemeenschappelijke opslag steunt matiging van, en analyses op, UGC in het publiceer milieu terwijl het elimineren van de behoefte aan [ replicatie ](/help/communities/sync.md) van UGC.

* [ Community Content Store ](/help/communities/working-with-srp.md) : bespreekt de opslagopties SRP voor AEM Communities

* [ Geadviseerde Topologieën ](/help/communities/topologies.md) : bespreekt de topologie om afhankelijk van gebruiksgeval en keus te gebruiken SRP

## Bijwerken {#upgrading}

Wanneer bevordering aan AEM 6.5 platform van vorige versies van AEM, is het belangrijk om [ te lezen Bevorderend aan AEM 6.5 ](/help/sites-deploying/upgrade.md).

Naast de bevordering van het platform, lees [ Bevorderend aan AEM Communities 6.5 ](/help/communities/upgrade.md) om over de veranderingen van Gemeenschappen te leren.

## Configuraties {#configurations}

### Primaire uitgever {#primary-publisher}

Wanneer de gekozen plaatsing a [ landbouwbedrijf ](/help/communities/topologies.md#tarmk-publish-farm) is publiceert, dan moet één AEM instantie als **`primary publisher`** voor activiteiten worden geïdentificeerd die niet op alle instanties zouden moeten voorkomen. Bijvoorbeeld, eigenschappen die op **berichten** of **Adobe Analytics** vertrouwen.

Door gebrek, wordt de `AEM Communities Publisher Configuration` configuratie OSGi gevormd met het **`Primary Publisher`** gecontroleerde controlevakje, zodat alle publiceer instanties in een publicatielandbouwbedrijf zich als primair zou identificeren.

Daarom is het noodzakelijk om **de configuratie op alle secundaire publiceer instanties** uit te geven om het **`Primary Publisher`** controlevakje los te maken.

![ de dialoogdoos die van de Configuratie van de Uitgever van AEM Communities het Primaire de controlevakje van de Uitgever toont ](../assets/primary-publisher.png)

Voor alle andere (secundaire) publiceer instanties in publiceer landbouwbedrijf:

* Aanmelden met beheerdersrechten
* Heb toegang tot de [ Webconsole ](/help/sites-deploying/configuring-osgi.md)

   * Bijvoorbeeld, [ https://localhost:4503/system/console/configMgr](https://localhost:4503/system/console/configMgr)

* Zoek de `AEM Communities Publisher Configuration`
* Het bewerkingspictogram selecteren
* Oncontroleer **Primaire Uitgever** controlevakje
* Selecteer **sparen**

### Replicatieagents op auteur {#replication-agents-on-author}

De replicatie wordt gebruikt voor plaatsinhoud die in het publicatiemilieu, zoals communautaire groepen wordt gecreeerd, en het leiden leden en lidgroepen van het auteursmilieu gebruikend de [ tunneldienst ](#tunnel-service-on-author).

Voor de primaire uitgever, verzeker [ Configuratie van de Agent van de Replicatie ](/help/sites-deploying/replication.md) correct identificeert publiceer server en erkende gebruiker. De standaard geautoriseerde gebruiker, `admin` , heeft al de juiste machtigingen (lid van `Communities Administrators` ).

Andere gebruikers hebben alleen de juiste machtigingen als ze lid zijn van de gebruikersgroep van `administrators` (ook lid van `Communities Administrators` ).

Er zijn twee replicatieagenten in het auteursmilieu die de vervoerconfiguratie nodig hebben correct worden gevormd.

* De console van de Replicatie van de toegang op auteur

   * Van globale navigatie: **Hulpmiddelen, Plaatsing, Replicatie, Agenten op auteur**

* Volg dezelfde procedure voor beide agenten:

   * **StandaardAgent (publiceert)**
   * **Omgekeerde Agent van de Replicatie (publiceer omgekeerde)**

      1. Selecteer de agent.
      1. Selecteer **uitgeven**.
      1. Selecteer het **Vervoer** lusje
      1. Als het geen haven `4503` is, geef **URI** uit om de correcte haven te specificeren.

      1. Als het geen gebruiker `admin` is, geef **Gebruiker** en **Wachtwoord** uit om een lid van de `administrators` gebruikersgroep te specificeren.

In de volgende afbeeldingen ziet u de resultaten van het wijzigen van de poort van 4503 in 6103 door:

#### Standaardagent (publiceren) {#default-agent-publish}

![ vorm-grenzen ](../assets/default-agent-publish.png)

#### Reverse Replication Agent (publiceren reverse) {#reverse-replication-agent-publish-reverse}

![ omgekeerde Agent van de Replicatie (publiceer revers) die tonen dat het wordt aangezet of toegelaten.](../assets/reverse-replication-agent.png)

### Tunnelservice op auteur {#tunnel-service-on-author}

Wanneer het gebruiken van het auteursmilieu om plaatsen ](/help/communities/sites-console.md) te creëren, [ wijzig plaatseigenschappen ](/help/communities/sites-console.md#modifying-site-properties) of [ beheer communautaire leden ](/help/communities/members.md), is het noodzakelijk om tot leden (gebruikers) toegang te hebben die in het publicatiemilieu worden geregistreerd, niet gebruikers die bij auteur worden geregistreerd.[

De tunneldienst verleent deze toegang gebruikend de replicatieagent op auteur.

Om de tunneldienst toe te laten:

* Voor **auteur**, teken binnen met administratieve voorrechten.
* Als de uitgever niet localhost is:4503 of de vervoergebruiker niet `admin` is,
dan [ vorm de replicatieagent ](#replication-agents-on-author).

* Heb toegang tot de [ Console van het Web ](/help/sites-deploying/configuring-osgi.md)

   * Bijvoorbeeld, [ https://localhost:4502/system/console/configMgr](https://localhost:4502/system/console/configMgr)

* Zoek de `AEM Communities Publish Tunnel Service`
* Het bewerkingspictogram selecteren
* Selecteer **toelaten** controledoos
* selecteren **sparen**

![ de Dienst van de Tunnel van AEM Communities Publish die &quot;toelaat&quot;controledoos toont, selecteerde of gecontroleerd.](../assets/tunnel-service.png)

### De cryptosleutel dupliceren {#replicate-the-crypto-key}

Er zijn twee eigenschappen van AEM Communities die alle AEM serverinstanties vereisen om de zelfde encryptiesleutels te gebruiken. Dit zijn [ Analytics ](/help/communities/analytics.md) en [ ASRP ](/help/communities/asrp.md).

Vanaf AEM 6.3 wordt het sleutelmateriaal opgeslagen in het bestandssysteem en niet langer in de gegevensopslagruimte.

Om het belangrijkste materiaal van Auteur aan alle andere instanties te kopiëren, is het noodzakelijk:

* Toegang krijgen tot de AEM instantie-typisch een instantie-Auteur die het belangrijkste te kopiëren materiaal bevat

   * Zoek de `com.adobe.granite.crypto.file` -bundel in het lokale bestandssysteem

     Bijvoorbeeld:

      * `<author-aem-install-dir>/crx-quickstart/launchpad/felix/bundle21`
      * Het bestand `bundle.info` identificeert de bundel

   * Navigeren in de gegevensmap
bijvoorbeeld:

      * `<author-aem-install-dir>/crx-quickstart/launchpad/felix/bundle21/data`

   * Kopieer de hoofd- en primaire knoopdossiers.

* Voor elke AEM

   * Navigeren in de gegevensmap
bijvoorbeeld:

      * `<publish-aem-install-dir>/crx-quickstart/launchpad/felix/bundle21/data`

   * Plak de twee eerder gekopieerde bestanden
   * Het is noodzakelijk om [ te verfrissen granite Crypto bundel ](#refresh-the-granite-crypto-bundle) als de AEM instantie loopt.

>[!CAUTION]
>
>Als een andere veiligheidseigenschap reeds is gevormd die op de crypto sleutels gebaseerd is, dan het herhalen van de crypto sleutels kon de configuratie beschadigen. Voor hulp, [ de zorg van de contactklant ](https://experienceleague.adobe.com/?support-solution=General&amp;support-tab=home#support).

#### Replicatie opslagplaats {#repository-replication}

Het bewaren van het sleutelmateriaal in de opslagplaats, zoals het geval was voor AEM 6.2 en eerder, kan worden behouden. Geef de volgende systeemeigenschap op bij het eerste opstarten van elke AEM instantie (die de initiële opslagplaats maakt):

* `-Dcom.adobe.granite.crypto.file.disable=true`

>[!NOTE]
>
>Het is belangrijk om te verifiëren dat de [ replicatieagent op Auteur ](#replication-agents-on-author) correct wordt gevormd.

Met het zeer belangrijke materiaal dat in de bewaarplaats wordt opgeslagen, is de manier om de crypto sleutel van auteur aan andere instanties te herhalen als volgt:

Gebruikend [ CRXDE Lite ](/help/sites-developing/developing-with-crxde-lite.md):

* Blader naar [ https://&lt;server>:&lt;port>/crx/de ](https://localhost:4502/crx/de)
* Selecteren `/etc/key`
* Tabblad Openen `Replication`
* Selecteren `Replicate`

* [De Granite Crypto-bundel vernieuwen](#refresh-the-granite-crypto-bundle)

![ CRXDE Lite die de weg /etc/sleutel op het linkerpaneel en het lusje van de Replicatie tonen in het laag-juiste paneel wordt geselecteerd.](../assets/replicare-repository.png)

#### De graniet-cryptobundel vernieuwen {#refresh-the-granite-crypto-bundle}

* Op elke publiceer instantie, heb toegang tot de [ Console van het Web ](/help/sites-deploying/configuring-osgi.md)

   * Bijvoorbeeld, [ https://&lt;server>:&lt;port>/system/console/bundles ](https://localhost:4503/system/console/bundles)

* `Adobe Granite Crypto Support` bundle (com.adobe.granite.crypto) zoeken
* Selecteer **vernieuwen**

![ Verfrissend de bundel van de Steun van Granite Crypto van de Adobe.](../assets/refresh-granite-bundle.png)

* Na een ogenblik, zou de dialoog van het Succes van a **moeten verschijnen:**
  `Operation completed successfully.`

### Apache HTTP Server {#apache-http-server}

Als u de Apache HTTP-server gebruikt, moet u ervoor zorgen dat u de juiste servernaam gebruikt voor alle relevante vermeldingen.

Let vooral op dat u de juiste servernaam gebruikt, niet `localhost` in de map `RedirectMatch` .

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

* AEM [ Dispatcher ](https://experienceleague.adobe.com/docs/experience-manager-dispatcher/using/dispatcher.html) documentatie
* [ Installerend Dispatcher ](https://experienceleague.adobe.com/docs/experience-manager-dispatcher/using/getting-started/dispatcher-install.html)
* [Dispatcher for Communities configureren](/help/communities/dispatcher.md)
* [Bekende problemen](/help/communities/troubleshooting.md#dispatcher-refetch-fails)

## Verwante documentatie van Gemeenschappen {#related-communities-documentation}

* Bezoek [ het Beheer Plaatsen van Gemeenschappen ](/help/communities/administer-landing.md) om over het creëren van een communautaire plaats te leren, vormend communautaire plaatssjablonen, het modereren van communautaire inhoud, het beheren van leden, en het vormen overseinen.

* Bezoek [ het Ontwikkelen van Gemeenschappen ](/help/communities/communities.md) waar u over het sociale componentenkader (SCF) en het aanpassen van de componenten en de eigenschappen van Gemeenschappen kunt leren.

* Bezoek [ Authoring Communities Components ](/help/communities/author-communities.md) waar u kunt leren hoe u met componenten van Gemeenschappen ontwerpt en deze configureert.

