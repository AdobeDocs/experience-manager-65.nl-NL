---
title: Gemeenschappen inzetten
description: Leer hoe u Communityfuncties en community-functies kunt implementeren in Adobe Experience Manager.
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
content-type: reference
topic-tags: deploying
docset: aem65
exl-id: 5b3d572d-e73d-4626-b664-c985949469c9
solution: Experience Manager
feature: Communities
role: Admin
source-git-commit: 1f56c99980846400cfde8fa4e9a55e885bc2258d
workflow-type: tm+mt
source-wordcount: '1652'
ht-degree: 0%

---

# Gemeenschappen inzetten {#deploying-communities}

## Vereisten {#prerequisites}

* [AEM 6.5 Platform](/help/sites-deploying/deploy.md)

* AEM Communities-licentie

* Optionele licenties voor:

   * [Functies van Adobe Analytics for Communities](/help/communities/analytics.md)
   * [MongoDB voor MSRP](/help/communities/msrp.md)
   * [Adobe Cloud voor ASRP](/help/communities/asrp.md)

## Controlelijst voor installatie {#installation-checklist}

**voor het [&#x200B; AEM platform](/help/sites-deploying/deploy.md#what-is-aem)**

* Installeer recentste [&#x200B; AEM 6.5 Updates &#x200B;](#aem64updates)

* Als het gebruiken van niet de standaardhavens (4502, 4503), dan [&#x200B; vormt replicatieagenten &#x200B;](#replication-agents-on-author)
* [De cryptotoets dupliceren](#replicate-the-crypto-key)
* Als het steunen van globalization, [&#x200B; opstelling geautomatiseerde vertaling &#x200B;](/help/sites-administering/translation.md)
(voorbeeldinstelling is beschikbaar voor ontwikkeling)

**voor het [&#x200B; vermogen van Gemeenschappen](/help/communities/overview.md)**

* Als het opstellen van a [&#x200B; het publiceren landbouwbedrijf &#x200B;](/help/sites-deploying/recommended-deploys.md#tarmk-farm), [&#x200B; de primaire uitgever &#x200B;](#primary-publisher) identificeert

* [De tunnelservice inschakelen](#tunnel-service-on-author)
* [Sociale aanmelding inschakelen](/help/communities/social-login.md#adobe-granite-oauth-authentication-handler)
* [Adobe Analytics configureren](/help/communities/analytics.md)
* Opstelling a [&#x200B; standaard e-maildienst &#x200B;](/help/communities/email.md)
* Identificeer de keus voor [&#x200B; gedeelde opslag UGC &#x200B;](/help/communities/working-with-srp.md) (**SRP**)

   * Als MongoDB SRP [&#x200B; (MSRP) &#x200B;](/help/communities/msrp.md)

      * [MongoDB installeren en configureren](/help/communities/msrp.md#mongodb-configuration)
      * [Solr configureren](/help/communities/solr.md)
      * [Selecteer MSRP](/help/communities/srp-config.md)

   * Als relationele database SRP [&#x200B; (DSRP) &#x200B;](/help/communities/dsrp.md)

      * [Installeer het JDBC-stuurprogramma voor MySQL](#jdbc-driver-for-mysql)
      * [Installeer en vorm MySQL voor DSRP](/help/communities/dsrp-mysql.md)
      * [Solr configureren](/help/communities/solr.md)
      * [DSRP selecteren](/help/communities/srp-config.md)

   * Als Adobe SRP [&#x200B; (ASRP) &#x200B;](/help/communities/asrp.md)

      * Met uw accountvertegenwoordiger samenwerken voor provisioning
      * [Selecteer ASRP](/help/communities/srp-config.md)

   * Als JCR SRP [&#x200B; (JSRP) &#x200B;](/help/communities/jsrp.md)

      * Geen gedeeld UGC-archief (door de gebruiker gegenereerde inhoud):

         * UGC wordt nooit herhaald
         * UGC is alleen zichtbaar op de AEM instantie of cluster waarin het is ingevoerd

         * De standaardwaarde is JSRP

## Laatste releases {#latest-releases}

AEM 6.5 Communautaire algemene vergadering omvat het communautaire pakket. Meer over updates aan AEM 6.5 [&#x200B; Gemeenschappen &#x200B;](/help/release-notes/release-notes.md#experiencemanagercommunities) weten, zie [&#x200B; AEM 6.5 de Nota&#39;s van de Versie &#x200B;](/help/release-notes/release-notes.md#communities-release-notes.html).

### AEM 6.5 Updates {#aem-updates}

Vanaf AEM 6.4 worden updates aan de Gemeenschappen geleverd als onderdeel van AEM Cumulative Fix Packs en Service Packs.

Voor de recentste updates aan AEM 6.5, zie [&#x200B; Adobe Experience Manager 6.4 Cumulatieve Packs en de Packs van de Dienst &#x200B;](https://experienceleague.adobe.com/nl/docs/experience-manager-release-information/aem-release-updates/aem-releases-updates) bevestigen.

### Versiehistorie {#version-history}

Net als bij AEM 6.4 en hoger maken AEM Communities-functies en hotfixes deel uit van AEM Communities-pakketten voor cumulatieve probleemoplossingen en servicepacks. Er zijn dus geen aparte kenmerkpakketten.

### JDBC-stuurprogramma voor MySQL {#jdbc-driver-for-mysql}

De functie Eén Gemeenschappen gebruikt een MySQL-database:

* Voor [&#x200B; DSRP &#x200B;](/help/communities/dsrp.md): het opslaan van UGC

De MySQL-connector moet afzonderlijk worden opgehaald en geïnstalleerd.

De noodzakelijke stappen zijn:

1. Download het archief van het PIT van [&#x200B; https://dev.mysql.com/downloads/connector/j/](https://dev.mysql.com/downloads/connector/j/)

   * Versie moet >= 5.1.38 zijn

1. Extraheer mysql-connector-java-&lt;version>-bin.jar (bundel) uit het archief
1. Gebruik de webconsole om de bundel te installeren en te starten:

   * Bijvoorbeeld https://localhost:4502/system/console/bundles
   * Selecteren **`Install/Update`**
   * Blader naar.. om de bundel te selecteren die u uit het gedownloade ZIP-archief hebt opgehaald
   * Controle dat {de Bestuurder JDBC van het Bedrijf van 0} Oracle voor MySQLcom.mysql.jdbc *actief is, en het begint als niet (of controleert de logboeken)*

1. Als het installeren op een bestaande plaatsing nadat JDBC is gevormd, dan opnieuw bindt JDBC aan de nieuwe schakelaar door de configuratie JDBC van de Webconsole op te slaan:
   * Bijvoorbeeld https://localhost:4502/system/console/configMgr
   * `Day Commons JDBC Connections Pool` -configuratie zoeken
   * Selecteren om te openen
   * Selecteren `Save`

1. De stappen 3 en 4 op alle auteur herhalen en instanties publiceren

De verdere informatie bij het installeren van bundels wordt gevonden op de [&#x200B; pagina van de Console van het Web &#x200B;](/help/sites-deploying/web-console.md).

#### Voorbeeld: geïnstalleerde MySQL-connectorbundel {#example-installed-mysql-connector-bundle}

![&#x200B; schakelaar-bundel &#x200B;](assets/connector-bundle.png)



### Geavanceerde MLS AEM {#aem-advanced-mls}

Voor de inzameling SRP (MSRP of DSRP) om geavanceerde meertalige onderzoek (MLS) te steunen, worden nieuwe stop-ins Solr vereist naast een douaneschema en de configuratie Solr. Alle vereiste items worden verpakt in een ZIP-bestand dat kan worden gedownload.

De geavanceerde MLS-download (ook wel `phasetwo` genoemd) is beschikbaar in de gegevensopslagruimte van de Adobe:

* AEM-SOLR-MLS-fasetwo

  Om het Geavanceerde pakket te verkrijgen MLS, zie [&#x200B; AEM Geavanceerde MLS &#x200B;](deploy-communities.md#aem-advanced-mls) in opstellen sectie van de documentatie.

   * Versie 1.2.40, 6 april 2016
   * Download AEM-SOLR-MLS-phasetwo-1.2.40.zip

Voor details en installatieinformatie, bezoek [&#128279;](/help/communities/solr.md) Configuratie 0&rbrace; Solr voor SRP.

### Info over Koppelingen naar pakket delen {#about-links-to-package-share}

**Pakketten Zichtbaar in Adobe AEM Wolk**

Voor de koppelingen naar pakketten op deze pagina is geen actieve versie van AEM vereist, omdat deze op `adobeaemcloud.com` Delen in pakketten moeten plaatsen. De pakketten kunnen wel worden weergegeven, maar de knop `Install` is bedoeld voor de installatie van de pakketten op een door de Adobe gehoste site. Als u `Install` selecteert wanneer u op een lokale AEM wilt installeren, treedt er een fout op.

**hoe te op Lokale AEMInstantie installeren**

Als u de pakketten die zichtbaar zijn in `adobeaemcloud.com` op een lokale AEM-instantie wilt installeren, moet het pakket eerst naar een lokale schijf worden gedownload:

* Selecteer het **Assets** lusje
* Selecteer **download aan schijf**

Voor de lokale AEM instantie, gebruik de Manager van het Pakket (bijvoorbeeld, [&#x200B; https://localhost:4502/crx/packmgr/ &#x200B;](https://localhost:4502/crx/packmgr/)), om aan de lokale AEM pakketbewaarplaats te uploaden.

Alternatief, die tot het pakket toegang hebben gebruikend het Aandeel van het Pakket van de lokale AEM instantie (bijvoorbeeld, [&#x200B; https://localhost:4502/crx/packageshare/ &#x200B;](https://localhost:4502/crx/packageshare/)), `Download` knoop downloadt aan de lokale het pakketbewaarplaats van de AEM instantie.

Eenmaal in de pakketopslagplaats van de lokale AEM gebruikt u Package Manager om het pakket te installeren.

Voor meer informatie, bezoek [&#x200B; hoe te met Pakketten &#x200B;](/help/sites-administering/package-manager.md#package-share) werken.

## Aanbevolen implementaties {#recommended-deployments}

In AEM Communities, wordt een gemeenschappelijke opslag gebruikt om UGC op te slaan en vaak bedoeld als [&#x200B; leverancier van het opslagmiddel (SRP) &#x200B;](/help/communities/working-with-srp.md). De geadviseerde plaatsingscentra bij het kiezen van een optie SRP voor de gemeenschappelijke opslag.

De gemeenschappelijke opslag steunt matiging van, en analyses op, UGC in het het publiceren milieu terwijl het elimineren van de behoefte aan [&#x200B; replicatie &#x200B;](/help/communities/sync.md) van UGC.

* [&#x200B; Community Content Store &#x200B;](/help/communities/working-with-srp.md) : bespreekt de opslagopties SRP voor AEM Communities

* [&#x200B; Geadviseerde Topologieën &#x200B;](/help/communities/topologies.md) : bespreekt de topologie om afhankelijk van gebruiksgeval en keus te gebruiken SRP

## Bijwerken {#upgrading}

Wanneer bevordering aan AEM 6.5 platform van vorige versies van AEM, is het belangrijk om [&#x200B; te lezen Bevorderend aan AEM 6.5 &#x200B;](/help/sites-deploying/upgrade.md).

Naast de bevordering van het platform, lees [&#x200B; Bevorderend aan AEM Communities 6.5 &#x200B;](/help/communities/upgrade.md) om over de veranderingen van Gemeenschappen te leren.

## Configuraties {#configurations}

### Primaire uitgever {#primary-publisher}

Wanneer de gekozen plaatsing a [&#x200B; landbouwbedrijf &#x200B;](/help/communities/topologies.md#tarmk-publish-farm) is publiceert, dan moet één AEM instantie als **`primary publisher`** voor activiteiten worden geïdentificeerd die niet op alle instanties zouden moeten voorkomen. Bijvoorbeeld, eigenschappen die op **berichten** of **Adobe Analytics** vertrouwen.

Door gebrek, wordt de `AEM Communities Publisher Configuration` configuratie OSGi gevormd met **`Primary Publisher`** gecontroleerd checkbox, zodat alle publiceer instanties in een publicatielandbouwbedrijf zich als primair zou identificeren.

Daarom is het noodzakelijk om **de configuratie op alle secundaire publiceer instanties** uit te geven om **`Primary Publisher`** checkbox uncheck.

![&#x200B; primair-uitgever &#x200B;](assets/primary-publisher.png)

Voor alle andere (secundaire) publiceer instanties in publiceer landbouwbedrijf:

* Aanmelden met beheerdersrechten
* Heb toegang tot de [&#x200B; Webconsole &#x200B;](/help/sites-deploying/configuring-osgi.md)

   * Bijvoorbeeld, [&#x200B; https://localhost:4503/system/console/configMgr](https://localhost:4503/system/console/configMgr)

* Zoek de `AEM Communities Publisher Configuration`
* Het bewerkingspictogram selecteren
* Oncontrole de **Primaire Uitgever** doos
* Selecteer **sparen**

### Replicatieagents op auteur {#replication-agents-on-author}

De replicatie wordt gebruikt voor plaatsinhoud die in het publicatiemilieu, zoals communautaire groepen wordt gecreeerd, en het leiden leden en lidgroepen van het auteursmilieu gebruikend de [&#x200B; tunneldienst &#x200B;](#tunnel-service-on-author).

Voor de primaire uitgever, verzeker [&#x200B; Configuratie van de Agent van de Replicatie &#x200B;](/help/sites-deploying/replication.md) correct de publicatieserver en erkende gebruiker identificeert. De standaard geautoriseerde gebruiker, `admin,` , heeft al de juiste machtigingen (lid van `Communities Administrators` ).

Andere gebruikers hebben alleen de juiste machtigingen als ze lid zijn van de gebruikersgroep van `administrators` (ook lid van `Communities Administrators` ).

Er zijn twee replicatieagenten in het auteursmilieu die de vervoerconfiguratie nodig hebben correct worden gevormd.

* De console van de Replicatie van de toegang op auteur

   * Navigeer vanuit de globale navigatie naar **[!UICONTROL Tools]** > **[!UICONTROL Deployment]** > **[!UICONTROL Replication]** > **[!UICONTROL Agents on author]**

* Volg dezelfde procedure voor beide agenten:

   * **StandaardAgent (publiceert)**
   * **Omgekeerde Agent van de Replicatie (publiceer omgekeerde)**

      1. Selecteer de agent
      1. Selecteer **uitgeven**
      1. Selecteer het **Vervoer** lusje
      1. Als het niet haven `4503` is, geef **URI** uit om de correcte haven te specificeren

      1. Als het geen gebruiker `admin` is, geef **Gebruiker** en **Wachtwoord** uit om een lid van de `administrators` gebruikersgroep te specificeren

In de volgende afbeeldingen ziet u de resultaten van het wijzigen van de poort van 4503 in 6103 door:

#### Standaardagent (publiceren) {#default-agent-publish}

![&#x200B; gebrek-agent-publiceren &#x200B;](assets/default-agent-publish.png)

#### Reverse Replication Agent (publiceren reverse) {#reverse-replication-agent-publish-reverse}

![&#x200B; omgekeerde-replicatie-agent &#x200B;](assets/reverse-replication-agent.png)

### Tunnelservice op auteur {#tunnel-service-on-author}

Wanneer het gebruiken van het auteursmilieu om plaatsen [&#128279;](/help/communities/sites-console.md) te creëren, [&#x200B; wijzig plaatseigenschappen &#x200B;](/help/communities/sites-console.md#modifying-site-properties) of [&#x200B; beheer communautaire leden &#x200B;](/help/communities/members.md), is het noodzakelijk om tot leden (gebruikers) toegang te hebben die in het publicatiemilieu worden geregistreerd, niet gebruikers die bij auteur worden geregistreerd.

De tunneldienst verleent deze toegang gebruikend de replicatieagent op auteur.

Om de tunneldienst toe te laten:

* Meld u aan met beheerdersrechten voor de auteur.
* Als de uitgever niet localhost is:4503 of de vervoergebruiker niet `admin` is,
dan [&#x200B; vorm de replicatieagent &#x200B;](#replication-agents-on-author)

* Heb toegang tot de [&#x200B; Console van het Web &#x200B;](/help/sites-deploying/configuring-osgi.md)

   * Bijvoorbeeld, [&#x200B; https://localhost:4502/system/console/configMgr](https://localhost:4502/system/console/configMgr)

* Zoek de `AEM Communities Publish Tunnel Service`
* Het bewerkingspictogram selecteren
* Controle **laat** vakje toe
* Selecteer **sparen**

  ![&#x200B; tunnel-dienst &#x200B;](assets/tunnel-service.png)

### De cryptosleutel dupliceren {#replicate-the-crypto-key}

Er zijn twee eigenschappen van AEM Communities die alle AEM serverinstanties vereisen om de zelfde encryptiesleutels te gebruiken. Dit zijn [&#x200B; Analytics &#x200B;](/help/communities/analytics.md) en [&#x200B; ASRP &#x200B;](/help/communities/asrp.md).

Vanaf AEM 6.3 wordt het sleutelmateriaal opgeslagen in het bestandssysteem en niet langer in de gegevensopslagruimte.

Om het belangrijkste materiaal van Auteur aan alle andere instanties te kopiëren, is het noodzakelijk:

* Toegang krijgen tot de AEM instantie-typisch een instantie-Auteur die het belangrijkste te kopiëren materiaal bevat

   * Zoek de `com.adobe.granite.crypto.file` -bundel in het lokale bestandssysteem.
bijvoorbeeld:

      * `<author-aem-install-dir>/crx-quickstart/launchpad/felix/bundle21`
      * Het bestand `bundle.info` identificeert de bundel

   * Navigeer in de gegevensmap,
bijvoorbeeld:

      * `<author-aem-install-dir>/crx-quickstart/launchpad/felix/bundle21/data`

      * Kopieer de hoofdknoopdossiers

* Voor elke AEM

   * Navigeer in de gegevensmap,
bijvoorbeeld:

      * `<publish-aem-install-dir>/crx-quickstart/launchpad/felix/bundle21/data`

   * Plak de twee eerder gekopieerde bestanden
   * Het is noodzakelijk om [&#x200B; te verfrissen granite Crypto bundel &#x200B;](#refresh-the-granite-crypto-bundle) als de AEM instantie van het doel loopt

>[!CAUTION]
>
>Als een andere veiligheidseigenschap reeds is gevormd die op de crypto sleutels gebaseerd is, dan het herhalen van de crypto sleutels kon de configuratie beschadigen. Voor hulp, [&#x200B; de zorg van de contactklant &#x200B;](https://experienceleague.adobe.com/nl?support-solution=General&support-tab=home#support).

#### Replicatie opslagplaats {#repository-replication}

Het bewaren van het sleutelmateriaal in de opslagplaats, zoals het geval was voor AEM 6.2 en eerder, kan worden behouden. Geef de systeemeigenschap `-Dcom.adobe.granite.crypto.file.disable=true` op bij het eerste opstarten van elke AEM instantie (die de eerste opslagplaats maakt).

>[!NOTE]
>
>Verifieer dat de [&#x200B; replicatieagent op Auteur &#x200B;](#replication-agents-on-author) correct wordt gevormd.

Met het belangrijkste materiaal dat in de bewaarplaats wordt opgeslagen, is de manier om de crypto sleutel van auteur aan andere instanties te herhalen als volgt:

Gebruikend [&#x200B; CRXDE Lite &#x200B;](/help/sites-developing/developing-with-crxde-lite.md):

* Blader naar [&#x200B; https://&lt;server>:&lt;port>/crx/de &#x200B;](https://localhost:4502/crx/de)
* Selecteren `/etc/key`
* Tabblad Openen `Replication`
* Selecteren `Replicate`

* [De graniet-cryptobundel vernieuwen](#refresh-the-granite-crypto-bundle)

  ![&#x200B; replicare-bewaarplaats &#x200B;](assets/replicare-repository.png)

#### De graniet-cryptobundel vernieuwen {#refresh-the-granite-crypto-bundle}

* Op elke publiceer instantie, heb toegang tot de [&#x200B; Console van het Web &#x200B;](/help/sites-deploying/configuring-osgi.md)

   * Bijvoorbeeld, [&#x200B; https://&lt;server>:&lt;port>/system/console/bundles &#x200B;](https://localhost:4503/system/console/bundles)

* `Adobe Granite Crypto Support` bundle (com.adobe.granite.crypto) zoeken
* Selecteer **vernieuwen**

  ![&#x200B; graniet-crypto &#x200B;](assets/granite-crypto.png)

* Na een ogenblik, zou de dialoog van het Succes van a **&#x200B;**&#x200B;moeten verschijnen:
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

* AEM [&#x200B; Dispatcher &#x200B;](https://experienceleague.adobe.com/nl/docs/experience-manager-release-information/aem-release-updates/aem-releases-updates) documentatie
* [&#x200B; Installerend Dispatcher &#x200B;](https://experienceleague.adobe.com/nl/docs/experience-manager-dispatcher/using/getting-started/dispatcher-install)
* [Dispatcher for Communities configureren](/help/communities/dispatcher.md)
* [Bekende problemen](/help/communities/troubleshooting.md#dispatcher-refetch-fails)

## Verwante documentatie van Gemeenschappen {#related-communities-documentation}

* Bezoek [&#x200B; het Beheer Plaatsen van Gemeenschappen &#x200B;](/help/communities/administer-landing.md) om over het creëren van een communautaire plaats te leren, vormend communautaire plaatssjablonen, het modereren van communautaire inhoud, het beheren van leden, en het vormen overseinen.

* Bezoek [&#x200B; het Ontwikkelen van Gemeenschappen &#x200B;](/help/communities/communities.md) waar u over het sociale componentenkader (SCF) en het aanpassen van de componenten en de eigenschappen van Gemeenschappen kunt leren.

* Bezoek [&#x200B; Authoring Communities Components &#x200B;](/help/communities/author-communities.md) waar u kunt leren hoe u met componenten van Gemeenschappen ontwerpt en deze configureert.
