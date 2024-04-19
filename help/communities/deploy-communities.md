---
title: Gemeenschappen inzetten
description: Leer hoe u Communityfuncties en community-functies kunt implementeren in Adobe Experience Manager.
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
content-type: reference
topic-tags: deploying
docset: aem65
exl-id: 5b3d572d-e73d-4626-b664-c985949469c9
source-git-commit: a28883778c5e8fb90cbbd0291ded17059ab2ba7e
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

**Voor de [AEM](/help/sites-deploying/deploy.md#what-is-aem)**

* Nieuwste installeren [AEM 6.5 Updates](#aem64updates)

* Als u de standaardpoorten niet gebruikt (4502, 4503), dan [replicatieagents configureren](#replication-agents-on-author)
* [De cryptotoets dupliceren](#replicate-the-crypto-key)
* Als we de globalisering ondersteunen, [geautomatiseerde omzetting instellen](/help/sites-administering/translation.md)
(voorbeeldinstelling is beschikbaar voor ontwikkeling)

**Voor de [Mogelijkheid van Gemeenschappen](/help/communities/overview.md)**

* Indien het opstellen van een [uitgeverij](/help/sites-deploying/recommended-deploys.md#tarmk-farm), [de primaire uitgever identificeren](#primary-publisher)

* [De tunnelservice inschakelen](#tunnel-service-on-author)
* [Sociale aanmelding inschakelen](/help/communities/social-login.md#adobe-granite-oauth-authentication-handler)
* [Adobe Analytics configureren](/help/communities/analytics.md)
* Een [standaard e-mailservice](/help/communities/email.md)
* Identificeer de keuze voor [gedeelde UGC-opslag](/help/communities/working-with-srp.md) (**SRP**)

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

      * Met uw accountvertegenwoordiger samenwerken voor provisioning
      * [Selecteer ASRP](/help/communities/srp-config.md)

   * Als JCR SRP [(JSRP)](/help/communities/jsrp.md)

      * Geen gedeeld UGC-archief (door de gebruiker gegenereerde inhoud):

         * UGC wordt nooit herhaald
         * UGC is alleen zichtbaar op de AEM instantie of cluster waarin het is ingevoerd

         * De standaardwaarde is JSRP

## Laatste releases {#latest-releases}

AEM 6.5 Communautaire algemene vergadering omvat het communautaire pakket. Meer informatie over updates van AEM 6.5 [Gemeenschappen](/help/release-notes/release-notes.md#experiencemanagercommunities), zie de [AEM 6.5 Opmerkingen bij de release](/help/release-notes/release-notes.md#communities-release-notes.html).

### AEM 6.5 Updates {#aem-updates}

Vanaf AEM 6.4 worden updates aan de Gemeenschappen geleverd als onderdeel van AEM Cumulative Fix Packs en Service Packs.

Voor de meest recente updates van AEM 6.5 raadpleegt u [Adobe Experience Manager 6.4 Cumulatief repareren van pakketten en servicepacks](https://experienceleague.adobe.com/en/docs/experience-manager-release-information/aem-release-updates/aem-releases-updates).

### Versiehistorie {#version-history}

Net als bij AEM 6.4 en hoger maken AEM Communities-functies en hotfixes deel uit van AEM Communities-pakketten voor cumulatieve probleemoplossingen en servicepacks. Er zijn dus geen aparte kenmerkpakketten.

### JDBC-stuurprogramma voor MySQL {#jdbc-driver-for-mysql}

De functie Eén Gemeenschappen gebruikt een MySQL-database:

* Voor [DSRP](/help/communities/dsrp.md): UGC opslaan

De MySQL-connector moet afzonderlijk worden opgehaald en geïnstalleerd.

De noodzakelijke stappen zijn:

1. Download het ZIP-archief van [https://dev.mysql.com/downloads/connector/j/](https://dev.mysql.com/downloads/connector/j/)

   * Versie moet >= 5.1.38 zijn

1. mysql-connector-java-&lt;version>-bin.jar (bundel) uit het archief
1. Gebruik de webconsole om de bundel te installeren en te starten:

   * Bijvoorbeeld https://localhost:4502/system/console/bundles
   * Selecteren **`Install/Update`**
   * Blader naar.. om de bundel te selecteren die u uit het gedownloade ZIP-archief hebt opgehaald
   * Controleren of *JDBC-stuurprogramma van oracle Corporation voor MySQLcom.mysql.jdbc* is actief en start deze als dit niet het geval is (of controleer de logboeken)

1. Als het installeren op een bestaande plaatsing nadat JDBC is gevormd, dan opnieuw bindt JDBC aan de nieuwe schakelaar door de configuratie JDBC van de Webconsole op te slaan:
   * Bijvoorbeeld https://localhost:4502/system/console/configMgr
   * Zoeken `Day Commons JDBC Connections Pool` configuratie
   * Selecteren om te openen
   * Selecteren `Save`

1. De stappen 3 en 4 op alle auteur herhalen en instanties publiceren

Meer informatie over het installeren van bundels vindt u op de [Webconsole](/help/sites-deploying/web-console.md) pagina.

#### Voorbeeld: geïnstalleerde MySQL-connectorbundel {#example-installed-mysql-connector-bundle}

![connector-bundle](assets/connector-bundle.png)



### Geavanceerde MLS AEM {#aem-advanced-mls}

Voor de inzameling SRP (MSRP of DSRP) om geavanceerde meertalige onderzoek (MLS) te steunen, worden nieuwe stop-ins Solr vereist naast een douaneschema en de configuratie Solr. Alle vereiste items worden verpakt in een ZIP-bestand dat kan worden gedownload.

De geavanceerde MLS-download (ook wel bekend als `phasetwo`) is beschikbaar bij de gegevensbank van de Adobe:

* AEM-SOLR-MLS-fasetwo

  Ga voor het geavanceerde MLS-pakket naar [Geavanceerde MLS AEM](deploy-communities.md#aem-advanced-mls) in de op te stellen sectie van de documentatie.

   * Versie 1.2.40, 6 april 2016
   * Download AEM-SOLR-MLS-phasetwo-1.2.40.zip

Ga voor meer informatie en installatie-informatie naar [Solr-configuratie](/help/communities/solr.md) voor SRP.

### Info over Koppelingen naar pakket delen {#about-links-to-package-share}

**Pakketten zichtbaar in Adobe AEM cloud**

Voor de koppelingen naar pakketten op deze pagina is geen actieve versie van AEM vereist, aangezien deze bestemd zijn voor Delen in pakket op `adobeaemcloud.com`. Als de pakketten kunnen worden weergegeven, worden de `Install` -knop is voor het installeren van de pakketten in een door de Adobe gehoste site. Als u van plan bent op een lokale AEM te installeren, selecteert u `Install` resulteert in een fout.

**Installeren op lokale AEM**

De pakketten installeren die zichtbaar zijn in `adobeaemcloud.com` op een lokale AEM moet het pakket eerst naar een lokale schijf worden gedownload:

* Selecteer de **Activa** tab
* Selecteren **downloaden naar schijf**

Gebruik in de lokale AEM Package Manager (bijvoorbeeld [https://localhost:4502/crx/packmgr/](https://localhost:4502/crx/packmgr/)), om te uploaden naar de lokale AEM.

U kunt het pakket ook openen met Package Share van de lokale AEM-instantie (bijvoorbeeld [https://localhost:4502/crx/packageshare/](https://localhost:4502/crx/packageshare/)), `Download` wordt gedownload naar de pakketopslagplaats van de lokale AEM.

Eenmaal in de pakketopslagplaats van de lokale AEM gebruikt u Package Manager om het pakket te installeren.

Ga voor meer informatie naar [Werken met pakketten](/help/sites-administering/package-manager.md#package-share).

## Aanbevolen implementaties {#recommended-deployments}

In AEM Communities wordt een gemeenschappelijke winkel gebruikt om UGC op te slaan en wordt deze vaak de [Storage Resource Provider (SRP)](/help/communities/working-with-srp.md). De geadviseerde plaatsingscentra bij het kiezen van een optie SRP voor de gemeenschappelijke opslag.

De gemeenschappelijke opslag steunt matiging van, en analyses op UGC in het het publiceren milieu terwijl het elimineren van de behoefte aan [replicatie](/help/communities/sync.md) van UGC.

* [Community Content Store](/help/communities/working-with-srp.md) : bespreekt de opslagopties voor SRP voor AEM Communities

* [Aanbevolen topologieën](/help/communities/topologies.md) : bespreekt de topologie om afhankelijk van gebruiksgeval en keus te gebruiken SRP

## Bijwerken {#upgrading}

Wanneer u vanaf eerdere versies van AEM een upgrade uitvoert naar het AEM 6.5-platform, is het belangrijk dat u [Upgrade uitvoeren naar AEM 6.5](/help/sites-deploying/upgrade.md).

Naast het upgraden van het platform, leest u [Upgrade uitvoeren naar AEM Communities 6.5](/help/communities/upgrade.md) voor meer informatie over wijzigingen in de Gemeenschappen.

## Configuraties {#configurations}

### Primaire uitgever {#primary-publisher}

Wanneer de gekozen implementatie een [publicatiebedrijf](/help/communities/topologies.md#tarmk-publish-farm)moet vervolgens één AEM publicatieexemplaar worden geïdentificeerd als de **`primary publisher`** voor activiteiten die niet in alle gevallen mogen plaatsvinden. Bijvoorbeeld, eigenschappen die zich baseren op **meldingen** of **Adobe Analytics**.

Standaard worden de `AEM Communities Publisher Configuration` De configuratie OSGi wordt gevormd met **`Primary Publisher`** checkbox controleerde, dusdanig dat alle publiceer instanties in een publicatielandbouwbedrijf zich als primair zou identificeren.

Daarom moet **bewerk de configuratie op alle secundaire publicatieinstanties** om de controle van **`Primary Publisher`** selectievakje.

![primaire uitgever](assets/primary-publisher.png)

Voor alle andere (secundaire) publiceer instanties in publiceer landbouwbedrijf:

* Aanmelden met beheerdersrechten
* Toegang krijgen tot de [webconsole](/help/sites-deploying/configuring-osgi.md)

   * Bijvoorbeeld: [https://localhost:4503/system/console/configMgr](https://localhost:4503/system/console/configMgr)

* Zoek de `AEM Communities Publisher Configuration`
* Het bewerkingspictogram selecteren
* Schakel het selectievakje **Primaire uitgever** box
* Selecteren **Opslaan**

### Replicatieagents op auteur {#replication-agents-on-author}

De replicatie wordt gebruikt voor plaatsinhoud die in het publicatiemilieu, zoals communautaire groepen wordt gecreeerd en het leiden leden en lidgroepen van het auteursmilieu gebruikend [tunneldienst](#tunnel-service-on-author).

Voor de primaire uitgever zorg ervoor [Replication Agent Config](/help/sites-deploying/replication.md) geeft de publicatieserver en de geautoriseerde gebruiker correct aan. De standaard geoorloofde gebruiker, `admin,` beschikt al over de juiste machtigingen (is lid van `Communities Administrators`).

Voor wat andere gebruiker om de aangewezen toestemmingen te hebben, moeten zij als lid aan worden toegevoegd `administrators` gebruikersgroep (ook lid van `Communities Administrators`).

Er zijn twee replicatieagenten in het auteursmilieu die de vervoerconfiguratie nodig hebben correct worden gevormd.

* De console van de Replicatie van de toegang op auteur

   * Navigeer van globale navigatie naar **[!UICONTROL Tools]** > **[!UICONTROL Deployment]** > **[!UICONTROL Replication]** > **[!UICONTROL Agents on author]**

* Volg dezelfde procedure voor beide agenten:

   * **Standaardagent (publiceren)**
   * **Reverse Replication Agent (publiceren reverse)**

      1. Selecteer de agent
      1. Selecteren **bewerken**
      1. Selecteer de **Vervoer** tab
      1. Als het geen poort is `4503`, bewerkt u de **URI** om de juiste poort op te geven

      1. Als het geen gebruiker is `admin`, bewerkt u de **Gebruiker** en **Wachtwoord** om een lid van de `administrators` gebruikersgroep

In de volgende afbeeldingen ziet u de resultaten van het wijzigen van de poort van 4503 in 6103 door:

#### Standaardagent (publiceren) {#default-agent-publish}

![default-agent-publish](assets/default-agent-publish.png)

#### Reverse Replication Agent (publiceren reverse) {#reverse-replication-agent-publish-reverse}

![reverse-replication-agent](assets/reverse-replication-agent.png)

### Tunnelservice op auteur {#tunnel-service-on-author}

Wanneer u de ontwerpomgeving gebruikt voor [sites maken](/help/communities/sites-console.md), [site-eigenschappen wijzigen](/help/communities/sites-console.md#modifying-site-properties) of [leden van de gemeenschap beheren](/help/communities/members.md), is het noodzakelijk om toegang te krijgen tot leden (gebruikers) die zijn geregistreerd in de publicatieomgeving, niet tot gebruikers die zijn geregistreerd bij de auteur.

De tunneldienst verleent deze toegang gebruikend de replicatieagent op auteur.

Om de tunneldienst toe te laten:

* Meld u aan met beheerdersrechten voor de auteur.
* Als de uitgever niet localhost is:4503 of de vervoergebruiker niet `admin`vervolgens [vorm de replicatieagent](#replication-agents-on-author)

* Toegang krijgen tot de [Webconsole](/help/sites-deploying/configuring-osgi.md)

   * Bijvoorbeeld: [https://localhost:4502/system/console/configMgr](https://localhost:4502/system/console/configMgr)

* Zoek de `AEM Communities Publish Tunnel Service`
* Het bewerkingspictogram selecteren
* Controleer de **enable** box
* Selecteren **Opslaan**

  ![tunneldienst](assets/tunnel-service.png)

### De cryptosleutel dupliceren {#replicate-the-crypto-key}

Er zijn twee eigenschappen van AEM Communities die alle AEM serverinstanties vereisen om de zelfde encryptiesleutels te gebruiken. Dit zijn [Analyse](/help/communities/analytics.md) en [ASRP](/help/communities/asrp.md).

Vanaf AEM 6.3 wordt het sleutelmateriaal opgeslagen in het bestandssysteem en niet langer in de gegevensopslagruimte.

Om het belangrijkste materiaal van Auteur aan alle andere instanties te kopiëren, is het noodzakelijk:

* Toegang krijgen tot de AEM instantie-typisch een instantie-Auteur die het belangrijkste te kopiëren materiaal bevat

   * Zoek de `com.adobe.granite.crypto.file` in het lokale bestandssysteem, bijvoorbeeld

      * `<author-aem-install-dir>/crx-quickstart/launchpad/felix/bundle21`
      * De `bundle.info` bestand identificeert de bundel

   * Navigeer bijvoorbeeld naar de gegevensmap

      * `<author-aem-install-dir>/crx-quickstart/launchpad/felix/bundle21/data`

      * Kopieer de hoofdknoopdossiers

* Voor elke AEM

   * Navigeer bijvoorbeeld naar de gegevensmap

      * `<publish-aem-install-dir>/crx-quickstart/launchpad/felix/bundle21/data`

   * Plak de twee eerder gekopieerde bestanden
   * Het is noodzakelijk [De Granite Crypto-bundel vernieuwen](#refresh-the-granite-crypto-bundle) als de AEM-doelinstantie actief is

>[!CAUTION]
>
>Als een andere veiligheidseigenschap reeds is gevormd die op de crypto sleutels gebaseerd is, dan het herhalen van de crypto sleutels kon de configuratie beschadigen. Voor hulp, [contact opnemen met de klantenservice](https://experienceleague.adobe.com/?support-solution=General&amp;support-tab=home#support).

#### Replicatie opslagplaats {#repository-replication}

Het bewaren van het sleutelmateriaal in de opslagplaats, zoals het geval was voor AEM 6.2 en eerder, kan worden behouden. De eigenschap system opgeven `-Dcom.adobe.granite.crypto.file.disable=true` bij het eerste opstarten van elke AEM instantie (die de eerste opslagplaats maakt).

>[!NOTE]
>
>Controleer of de [replicatieagent op auteur](#replication-agents-on-author) correct is geconfigureerd.

Met het belangrijkste materiaal dat in de bewaarplaats wordt opgeslagen, is de manier om de crypto sleutel van auteur aan andere instanties te herhalen als volgt:

Gebruiken [CRXDE Lite](/help/sites-developing/developing-with-crxde-lite.md):

* Bladeren naar [https://&lt;server>:&lt;port>/crx/de](https://localhost:4502/crx/de)
* Selecteren `/etc/key`
* Openen `Replication` tab
* Selecteren `Replicate`

* [De graniet-cryptobundel vernieuwen](#refresh-the-granite-crypto-bundle)

  ![replicare-opslagplaats](assets/replicare-repository.png)

#### De graniet-cryptobundel vernieuwen {#refresh-the-granite-crypto-bundle}

* Ga bij elke publicatie-instantie naar de knop [Webconsole](/help/sites-deploying/configuring-osgi.md)

   * Bijvoorbeeld: [https://&lt;server>:&lt;port>/systeem/console/bundels](https://localhost:4503/system/console/bundles)

* Zoeken `Adobe Granite Crypto Support` bundle (com.adobe.granite.crypto)
* Selecteren **Vernieuwen**

  ![graniet-crypto](assets/granite-crypto.png)

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

* AEM [Dispatcher](https://experienceleague.adobe.com/en/docs/experience-manager-release-information/aem-release-updates/aem-releases-updates) documentatie
* [Dispatcher installeren](https://experienceleague.adobe.com/en/docs/experience-manager-dispatcher/using/getting-started/dispatcher-install)
* [Dispatcher configureren voor Gemeenschappen](/help/communities/dispatcher.md)
* [Bekende problemen](/help/communities/troubleshooting.md#dispatcher-refetch-fails)

## Verwante documentatie van Gemeenschappen {#related-communities-documentation}

* Bezoek [Communitysites beheren](/help/communities/administer-landing.md) om over het creëren van een communautaire plaats te leren, vormend communautaire plaatssjablonen, het modereren van communautaire inhoud, het leiden van leden, en het vormen overseinen.

* Bezoek [Ontwikkelingsgemeenschappen](/help/communities/communities.md) waar u over het sociale componentenkader (SCF) en het aanpassen van de componenten en de eigenschappen van de Gemeenschappen kunt leren.

* Bezoek [Componenten van Gemeenschappen ontwerpen](/help/communities/author-communities.md) waar u kunt leren om met te schrijven en de componenten van de Gemeenschappen te vormen.
