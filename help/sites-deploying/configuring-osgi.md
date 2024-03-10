---
title: OSGi configureren
description: OSGi is een fundamenteel element in de technologiestapel van Adobe Experience Manager (AEM). Het wordt gebruikt om de samengestelde bundels van AEM en hun configuratie te controleren. In dit artikel wordt beschreven hoe u de configuratie-instellingen voor dergelijke bundels kunt beheren.
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: configuring
content-type: reference
feature: Configuring
exl-id: 5ecd09a3-c4be-4361-9816-03106435346f
source-git-commit: f349c8fd9c370ba589d217cd3b1d0521ae5c5597
workflow-type: tm+mt
source-wordcount: '1954'
ht-degree: 0%

---

# OSGi configureren{#configuring-osgi}

[OSGi](https://www.osgi.org/) is een fundamenteel element in de technologiestapel van Adobe Experience Manager (AEM). Het wordt gebruikt om de samengestelde bundels van AEM en hun configuratie te controleren.

OSGi &quot;*biedt de gestandaardiseerde primitieven waarmee toepassingen kunnen worden samengesteld uit kleine, herbruikbare en samenwerkingscomponenten. Deze componenten kunnen in een toepassing worden samengesteld en worden opgesteld*&quot;.

Zo kunt u bundels eenvoudig beheren, aangezien ze kunnen worden gestopt, geïnstalleerd en afzonderlijk kunnen worden gestart. De onderlinge afhankelijkheden worden automatisch verwerkt. Elke component OSGi (zie [OSGi-specificatie](https://docs.osgi.org/specification/)) bevindt zich in een van de verschillende bundels.

U kunt de configuratie-instellingen voor dergelijke bundels beheren door:

* met de [Adobe CQ-webconsole](#osgi-configuration-with-the-web-console)
* gebruiken [configuratiebestanden](#osgi-configuration-with-configuration-files)
* configureren [content-nodes ( `sling:OsgiConfig`) in de opslagplaats](#osgi-configuration-in-the-repository)

Beide methoden kunnen worden gebruikt, hoewel er subtiele verschillen zijn, vooral met betrekking tot [Modi uitvoeren](/help/sites-deploying/configure-runmodes.md):

* [Adobe CQ-webconsole](#osgi-configuration-with-the-web-console)

   * De console van het Web is de standaardinterface voor configuratie OSGi. Deze interface biedt een interface voor het bewerken van de verschillende eigenschappen, waarbij mogelijke waarden uit vooraf gedefinieerde lijsten kunnen worden geselecteerd.

     Als zodanig is het de eenvoudigste methode om te gebruiken.

   * Om het even welke configuraties die met de Console van het Web worden aangebracht worden onmiddellijk toegepast en van toepassing op de huidige instantie, ongeacht de huidige looppaswijze, of om het even welke verdere veranderingen in de looppaswijze.

* [configuratiebestanden](#osgi-configuration-with-configuration-files)

   * Bevat instellingen die zijn gedefinieerd in de webconsole.
   * Kan worden opgenomen in inhoudspakketten voor gebruik op andere instanties.

* [content-nodes (sling:osgiConfig) in de repository](#osgi-configuration-in-the-repository)

   * Vereist handconfiguratie gebruikend CRXDE Lite.
   * Vanwege de naamconventies van de `sling:OsgiConfig` knooppunten, kunt u de configuratie aan een specifieke [uitvoeringsmodus](/help/sites-deploying/configure-runmodes.md). U kunt zelfs configuraties voor meer dan één uitvoeringswijze in de zelfde bewaarplaats opslaan.
   * Eventuele geschikte configuraties worden direct toegepast (afhankelijk van de uitvoeringsmodus).

Welke methode u ook gebruikt, al deze configuratiemethoden:

* Zorg ervoor dat bij het kopiëren of repliceren van de inhoud van de opslagplaats identieke configuraties worden hersteld.
* Hiermee kunt u configuraties uitchecken naar FileVault of Subversion; voor beveiliging of verdere updates.
* Kan in pakketten worden opgeslagen voor gebruik bij het instellen van andere instanties.
* Laat u configuratierolouts uitvoeren gebruikend manuscripten om de configuratiedetails te verspreiden.

>[!NOTE]
>
>Details van bepaalde belangrijke instellingen worden weergegeven onder [OSGi Configuration Settings.](/help/sites-deploying/osgi-configuration-settings.md)

## OSGi Configuratie met de Console van het Web {#osgi-configuration-with-the-web-console}

De [Webconsole](/help/sites-deploying/web-console.md) in AEM biedt een gestandaardiseerde interface voor het configureren van de bundels. De **Configuratie** tab wordt gebruikt voor het vormen van de bundels OSGi, en is daarom het onderliggende mechanisme voor het vormen van AEM systeemparameters.

Eventuele aangebrachte wijzigingen worden onmiddellijk toegepast op de relevante OSGi-configuratie. Er is geen herstart nodig.

>[!NOTE]
>
>Wijzigingen die in de webconsole zijn aangebracht, worden in de opslagplaats opgeslagen als [configuratiebestanden](#osgi-configuration-with-configuration-files). Deze bestanden kunnen worden opgenomen in inhoudspakketten voor hergebruik in verdere installaties.

>[!NOTE]
>
>Voor de console van het Web, hebben om het even welke beschrijvingen die standaardmontages vermelden met het Verschuiven gebreken.
>
>Adobe Experience Manager heeft zijn eigen gebreken en zo zouden de gebreken die worden geplaatst van de gebreken kunnen verschillen die op de console worden gedocumenteerd.

Om een configuratie met de Webconsole bij te werken:

1. Toegang krijgen tot de **Configuratie** tabblad van de webconsole door:

   * De webconsole openen via de koppeling op het tabblad **Gereedschap > Bewerkingen** -menu. Na het registreren in de console, kunt u het drop-down menu gebruiken van:

     **OSGi >**

   * De directe URL, bijvoorbeeld:

     `http://localhost:4502/system/console/configMgr`

   Er wordt een lijst weergegeven.

1. Selecteer de bundel die u door één van beiden wilt vormen:

   * klikken op **Bewerken** pictogram voor die bundel
   * klikken op **Naam** van de bundel

1. Er wordt een dialoogvenster geopend. Hier kunt u desgewenst bewerken. Stel bijvoorbeeld de **Logboekniveau** tot `INFO`:

   ![chlimage_1-140](assets/chlimage_1-140.png)

   >[!NOTE]
   >
   >Updates worden in de opslagplaats opgeslagen als [configuratiebestanden](#osgi-configuration-with-configuration-files). Als u deze bestanden achteraf wilt zoeken en wilt opnemen in een inhoudspakket voor gebruik op een andere instantie, noteert u bijvoorbeeld de blijvende identiteit ( `PID`).

1. Klikken **Opslaan**.

   Uw veranderingen worden onmiddellijk toegepast op de relevante configuratie OSGi van het lopende systeem, wordt geen nieuw begin vereist.

   >[!NOTE]
   >
   >U kunt nu de verwante [configuratiebestanden](#osgi-configuration-with-configuration-files). Bijvoorbeeld om op te nemen in een inhoudspakket voor gebruik op een andere instantie.

## OSGi-configuratie met configuratiebestanden {#osgi-configuration-with-configuration-files}

De veranderingen van de configuratie die worden aangebracht gebruikend de Console van het Web worden voortgeduurd in de bewaarplaats als configuratiedossiers ( `.config`) onder:

`/apps`

Deze bestanden kunnen worden opgenomen in inhoudspakketten en opnieuw worden gebruikt in andere gevallen.

>[!NOTE]
>
>De indeling van de configuratiebestanden is specifiek. Raadpleeg de documentatie bij Sling Apache voor:
>* volledige informatie over [Apache Sling Provisioning Model en Apache SlingStart](https://sling.apache.org/documentation/development/slingstart.html#default-configuration-format).
>* zelfstudies en voorbeelden van [Bronnen en eigenschappen ophalen bij verkoop](https://sling.apache.org/documentation/tutorials-how-tos/getting-resources-and-properties-in-sling.html).
>
>Daarom wordt aangeraden het configuratiebestand te maken en te onderhouden door werkelijke wijzigingen aan te brengen in de webconsole.

De console van het Web toont geen aanwijzing van waar in de bewaarplaats dat uw veranderingen zijn bewaard, maar zij kunnen gemakkelijk worden gevestigd:

1. Maak het configuratiebestand door [een eerste wijziging aanbrengen in de webconsole](#osgi-configuration-with-the-web-console).
1. Open CRXDE Lite.
1. In de **Gereedschappen** menu, selecteert u **Query uitvoeren...** .
1. Om naar PID van de configuratie te zoeken die u hebt bijgewerkt, leg een vraag van voor **Type** `SQL`.

   Bijvoorbeeld: **Apache Felix OSGi Management Console** heeft de persistente identiteit (PID) van:

   `org.apache.felix.webconsole.internal.servlet.OsgiManager`

   De SQL-query zou dus kunnen zijn:

   ```shell
   select * from nt:base where jcr:path like '/apps/%' and contains(*, 'org.apache.felix.webconsole.internal.servlet.OsgiManager')
   ```

1. Het knooppunt voor configuratiebestanden wordt weergegeven.

   In het bovenstaande voorbeeld:

   `/apps/system/config/org.apache.felix.webconsole.internal.servlet.OsgiManager.config`

   >[!CAUTION]
   >
   >U kunt dit bestand openen om uw wijzigingen weer te geven, maar om typefouten te voorkomen, is het raadzaam werkelijke wijzigingen aan te brengen met de console.

1. U kunt nu een inhoudspakket maken dat dit knooppunt bevat en dat naar wens op de andere instanties wordt gebruikt.

## OSGi-configuratie in de opslagplaats {#osgi-configuration-in-the-repository}

Naast het gebruik van de webconsole kunt u ook configuratiegegevens definiëren in de opslagplaats. Zo kunt u de verschillende uitvoeringsmodi eenvoudig configureren.

Deze configuraties worden gemaakt door `sling:OsgiConfig` knooppunten in de opslagplaats waar het systeem naar kan verwijzen. Deze knopen weerspiegelen de configuraties OSGi, en een gebruikersinterface wordt gevormd aan hen. Om de configuratiegegevens bij te werken, werkt u de knoopeigenschappen bij.

Als u de configuratiegegevens in de bewaarplaats wijzigt, worden de veranderingen onmiddellijk toegepast op de relevante configuratie OSGi. Het is alsof de veranderingen gebruikend de console van het Web, met de aangewezen bevestiging en consistentiecontroles waren aangebracht. Deze workflow is ook van toepassing op het kopiëren van een configuratie vanuit `/libs/` tot `/apps/`.

Aangezien de zelfde configuratieparameter op verscheidene plaatsen is, is het systeem:

* zoekopdrachten naar alle knooppunten van het type `sling:OsgiConfig`
* filters volgens de dienstnaam
* filters op basis van de uitvoermodus

>[!NOTE]
>
>Lees ook [hoe te om een op bewaarplaats-gebaseerde configuratie voor een specifiek slechts geval te bepalen](https://experienceleague.adobe.com/docs/experience-cloud-kcs/kbarticles/KA-17500.html).

### Een nieuwe configuratie toevoegen aan de opslagplaats {#adding-a-new-configuration-to-the-repository}

#### Wat u moet weten {#what-you-need-to-know}

Om een configuratie aan de bewaarplaats toe te voegen, moet u het volgende weten:

1. De **Blijvende identiteit** (PID) van de service.

   Verwijs naar de **Configuraties** in de webconsole. De naam wordt tussen haakjes weergegeven na de naam van de bundel (of in de **Configuratiegegevens** onder aan de pagina).

   Maak bijvoorbeeld een knooppunt `com.day.cq.wcm.core.impl.VersionManagerImpl.` om te vormen **AEM WCM-versiebeheer**.

   ![chlimage_1-141](assets/chlimage_1-141.png)

1. Is een specifieke [uitvoeringsmodus](/help/sites-deploying/configure-runmodes.md) vereist? Maak de map:

   * `config` - voor alle uitvoeringsmodi
   * `config.author` - voor de auteursomgeving
   * `config.publish` - voor de publicatieomgeving
   * `config.<run-mode>` - in voorkomend geval

1. Is a **Configuratie** of **Fabrieksconfiguratie** noodzakelijk?
1. De individuele te vormen parameters, met inbegrip van om het even welke bestaande parameterdefinities die moeten worden ontspannen.

   Verwijs het individuele parametergebied in de console van het Web. De naam wordt tussen haakjes weergegeven voor elke parameter.

   Maak bijvoorbeeld een eigenschap
   `versionmanager.createVersionOnActivation` om te vormen **Versie maken bij activering**.

   ![chlimage_1-142](assets/chlimage_1-142.png)

1. Bestaat er een configuratie in `/libs`? Als u alle configuraties in uw exemplaar wilt weergeven, gebruikt u de **Query** in CRXDE Lite om de volgende SQL-query te verzenden:

   `select * from sling:OsgiConfig`

   Als dat het geval is, kan deze configuratie worden gekopieerd naar ` /apps/<yourProject>/`en vervolgens aangepast op de nieuwe locatie.

#### De configuratie maken in de opslagplaats {#creating-the-configuration-in-the-repository}

Om de nieuwe configuratie aan de bewaarplaats eigenlijk toe te voegen:

1. Gebruik CRXDE Lite om te navigeren naar:

   ` /apps/<yourProject>`

1. Als deze niet bestaat, maakt u de `config` map ( `sling:Folder`):

   * `config` - van toepassing op alle uitvoeringsmodi
   * `config.<run-mode>` - specifiek voor een bepaalde uitvoeringsmodus

1. Onder deze map maakt u een knooppunt:

   * Type: `sling:OsgiConfig`
   * Naam: de persistente identiteit (PID);

     bijvoorbeeld voor AEM WCM Version Manager `com.day.cq.wcm.core.impl.VersionManagerImpl`

   >[!NOTE]
   >
   >Bij het toevoegen van een fabrieksconfiguratie `-<identifier>` op de naam.
   >
   >Zoals in: `org.apache.sling.commons.log.LogManager.factory.config-<identifier>`
   >
   >Wanneer `<identifier>` wordt vervangen door vrije tekst die u (moet) invoeren om het exemplaar te identificeren (u kunt deze informatie niet weglaten), bijvoorbeeld:
   >
   >`org.apache.sling.commons.log.LogManager.factory.config-MINE`

1. Voor elke parameter die u wilt vormen, creeer een bezit op deze knoop:

   * Naam: de parameternaam zoals die in de console van het Web wordt getoond; de naam wordt getoond tussen haakjes aan het eind van de gebiedsbeschrijving. Bijvoorbeeld: `Create Version on Activation` gebruiken `versionmanager.createVersionOnActivation`
   * Type: naargelang het geval.
   * Waarde: naar wens.

   U moet eigenschappen voor de parameters slechts tot stand brengen die u wilt vormen, anderen nemen nog de standaardwaarden zoals die door AEM worden geplaatst.

1. Sla alle wijzigingen op.

   De veranderingen worden toegepast wanneer de knoop door de dienst opnieuw te beginnen (zoals met veranderingen die in de console van het Web worden aangebracht) wordt bijgewerkt.

>[!CAUTION]
>
>Wijzig niets in de `/libs` pad.

>[!CAUTION]
>
>De volledige weg van een configuratie moet correct zijn om het bij opstarten te lezen.

## Configuratiedetails {#configuration-details}

### Volgorde resolutie bij opstarten {#resolution-order-at-startup}

De volgende rangorde wordt gebruikt:

1. Opslagknooppunten onder `/apps/*/config...`.either met type `sling:OsgiConfig` of eigenschapsbestanden.

1. Opslagknooppunten met type `sling:OsgiConfig` krachtens `/libs/*/config...`. (definities buiten de box).

1. Alle `.config` bestanden van `<*cq-installation-dir*>/crx-quickstart/launchpad/config/...`. op het lokale bestandssysteem.

Een algemene configuratie in `/libs` kan door een project-specifieke configuratie in worden gemaskeerd `/apps`.

### Volgorde van resolutie bij uitvoering {#resolution-order-at-runtime}

De veranderingen van de configuratie die worden aangebracht terwijl het systeem loopt teweegbrengen een herlading met de gewijzigde configuratie.

Dan is de volgende orde van belangrijkheid van toepassing:

1. Het wijzigen van een configuratie in de console van het Web neemt onmiddellijk effect aangezien het belangrijkheid bij runtime neemt.
1. Een configuratie aanpassen in `/apps` onmiddellijk in werking treedt.
1. Een configuratie aanpassen in `/libs` onmiddellijk van kracht worden, tenzij het door een configuratie wordt gemaskeerd in `/apps`.

### Resolutie van meerdere uitvoermodi {#resolution-of-multiple-run-modes}

Voor configuraties die specifiek zijn voor de uitvoermodus, kunnen meerdere uitvoermodi worden gecombineerd. U kunt bijvoorbeeld configuratiemappen in de volgende stijl maken:

`/apps/*/config.<runmode1>.<runmode2>/`

Configuraties in dergelijke mappen worden toegepast als alle uitvoermodi overeenkomen met een uitvoeringsmodus die bij het opstarten is gedefinieerd.

Als bijvoorbeeld een instantie is gestart met de uitvoermodi `author,dev,emea`, configuratieknooppunten in `/apps/*/config.emea`, `/apps/*/config.author.dev/`, en `/apps/*/config.author.emea.dev/` wordt toegepast, terwijl configuratieknooppunten in `/apps/*/config.author.asean/` en `/config/author.dev.emea.noldap/` niet worden toegepast.

Als meerdere configuraties voor dezelfde PID van toepassing zijn, wordt de configuratie met het hoogste aantal overeenkomende uitvoeringsmodi toegepast.

Als bijvoorbeeld een instantie is gestart met de uitvoermodi `author,dev,emea`en beide `/apps/*/config.author/` en `/apps/*/config.emea.author/` een configuratie definiëren voor
`com.day.cq.wcm.core.impl.VersionManagerImpl`, de configuratie in `/apps/*/config.emea.author/` wordt toegepast.

De granulariteit van deze regel staat op een PID-niveau.
U kunt geen eigenschappen definiëren voor dezelfde PID in `/apps/*/config.author/` en meer specifieke `/apps/*/config.emea.author/` voor dezelfde PID.
De configuratie met het hoogste aantal passende looppaswijzen is effectief voor volledige PID.

### Standaardconfiguraties {#standard-configurations}

De volgende lijst toont een kleine selectie van de configuraties beschikbaar (in een standaardinstallatie) in de bewaarplaats:

* Auteur - AEM WCM-filter:

  `libs/wcm/core/config.author/com.day.cq.wcm.core.WCMRequestFilter`

* Publiceren - AEM WCM-filter:

  `libs/wcm/core/config.publish/com.day.cq.wcm.core.WCMRequestFilter`

* Publiceren - AEM WCM-paginatiestatistieken:

  `libs/wcm/core/config.publish/com.day.cq.wcm.core.stats.PageViewStatistics`

>[!NOTE]
>
>Als deze configuraties zich bevinden in `/libs` ze mogen niet rechtstreeks worden bewerkt, maar moeten wel naar het toepassingsgebied worden gekopieerd ( `/apps`) vóór aanpassing.

Om van alle configuratieknooppunten in uw instantie een lijst te maken, gebruik **Query** functionaliteit in CRXDE Lite om de volgende SQL-query te verzenden:

`select * from sling:OsgiConfig`

### Configuratievolstand {#configuration-persistence}

* Als u een configuratie door de console van het Web verandert, wordt het (gewoonlijk) geschreven in de bewaarplaats bij:

  `/apps/{somewhere}`

   * Standaard `{somewhere}` is `system/config` zodat wordt de configuratie geschreven aan

     `/apps/system/config`

   * Als u echter een configuratie bewerkt die oorspronkelijk van elders in de opslagplaats afkomstig was, bijvoorbeeld:

     /libs/foo/config/someconfig

     Dan wordt de bijgewerkte configuratie geschreven onder de originele plaats; bijvoorbeeld:

     `/apps/foo/config/someconfig`

* Instellingen die worden gewijzigd door `admin` worden opgeslagen in `*.config` bestanden onder:

  ```
     /crx-quickstart/launchpad/config
  ```

   * Dit gebied is de privé gegevens van OSGi configuratie admin en houdt alle configuratiedetails die door worden gespecificeerd `admin`, ongeacht hoe zij het systeem zijn binnengekomen.
   * Dit gebied is een implementatiedetail en u mag deze map nooit rechtstreeks bewerken.
   * Het is echter handig om de locatie van deze configuratiebestanden te kennen, zodat u kopieën kunt maken voor back-up, meerdere installaties of beide:

      * Apache Felix OSGi Management Console

        `../crx/org/apache/felix/webconsole/internal/servlet/OsgiManager.config`

      * CRX Sling Client Repository

        `../com/day/crx/sling/client/impl/CRXSlingClientRepository/<pid-nr>.config`

>[!CAUTION]
>
>Bewerk nooit de mappen of bestanden onder:
>
>`/crx-quickstart/launchpad/config`
