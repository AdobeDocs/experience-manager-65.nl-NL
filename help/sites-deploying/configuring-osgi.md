---
title: OSGi configureren
seo-title: OSGi configureren
description: OSGi is een fundamenteel element in de technologiestapel van Adobe Experience Manager (AEM). Het wordt gebruikt om de samengestelde bundels van AEM en hun configuratie te controleren. In dit artikel wordt beschreven hoe u de configuratie-instellingen voor dergelijke bundels kunt beheren.
seo-description: OSGi is een fundamenteel element in de technologiestapel van Adobe Experience Manager (AEM). Het wordt gebruikt om de samengestelde bundels van AEM en hun configuratie te controleren. In dit artikel wordt beschreven hoe u de configuratie-instellingen voor dergelijke bundels kunt beheren.
uuid: b39059a5-dd61-486a-869a-0d7a732c3a47
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: configuring
content-type: reference
discoiquuid: d701e4ba-417f-4b57-b103-27fd25290736
feature: Configureren
translation-type: tm+mt
source-git-commit: 48726639e93696f32fa368fad2630e6fca50640e
workflow-type: tm+mt
source-wordcount: '2014'
ht-degree: 0%

---


# Het vormen OSGi{#configuring-osgi}

[](https://www.osgi.org/) OSGiis een fundamenteel element in de technologiestapel van Adobe Experience Manager (AEM). Het wordt gebruikt om de samengestelde bundels van AEM en hun configuratie te controleren.

OSGi &quot;*verstrekt de gestandaardiseerde primitieven die toepassingen toestaan om van kleine, herbruikbare en samenwerkende componenten worden geconstrueerd. Deze componenten kunnen in een toepassing worden samengesteld en worden opgesteld*&quot;.

Hierdoor kunt u eenvoudig bundels beheren, aangezien deze kunnen worden gestopt, geïnstalleerd en afzonderlijk kunnen worden gestart. De onderlinge afhankelijkheden worden automatisch verwerkt. Elke Component OSGi (zie [OSGi Specification](https://www.osgi.org/Specifications/HomePage)) is bevat in één van de diverse bundels.

U kunt de configuratie-instellingen voor dergelijke bundels beheren door:

* het gebruiken van [Adobe CQ Webconsole](#osgi-configuration-with-the-web-console)
* gebruiken [configuratiebestanden](#osgi-configuration-with-configuration-files)
* configureren van [content-nodes ( `sling:OsgiConfig`) in de repository](#osgi-configuration-in-the-repository)

Één van beide methode kan worden gebruikt hoewel er subtiele verschillen zijn, hoofdzakelijk met betrekking tot [loopwijze](/help/sites-deploying/configure-runmodes.md):

* [Adobe CQ-webconsole](#osgi-configuration-with-the-web-console)

   * De console van het Web is de standaardinterface voor configuratie OSGi. Deze interface biedt een interface voor het bewerken van de verschillende eigenschappen, waarbij mogelijke waarden uit vooraf gedefinieerde lijsten kunnen worden geselecteerd.

      Als zodanig is het de eenvoudigste methode.

   * Om het even welke configuraties die met de Console van het Web worden aangebracht worden onmiddellijk toegepast en van toepassing op de huidige instantie, ongeacht de huidige looppaswijze, of om het even welke verdere veranderingen in de looppaswijze.

* [configuratiebestanden](#osgi-configuration-with-configuration-files)

   * Bevat instellingen die zijn gedefinieerd in de webconsole.
   * Kan worden opgenomen in inhoudspakketten voor gebruik op andere instanties.

* [content-nodes (sling:osgiConfig) in de repository](#osgi-configuration-in-the-repository)

   * Dit vereist handconfiguratie gebruikend CRXDE Lite.
   * Vanwege de naamgevingsconventies van de `sling:OsgiConfig`-knooppunten kunt u de configuratie koppelen aan een specifieke [uitvoeringsmodus](/help/sites-deploying/configure-runmodes.md). U kunt zelfs configuraties voor meer dan één uitvoeringswijze in de zelfde bewaarplaats opslaan.
   * Eventuele geschikte configuraties worden direct toegepast (afhankelijk van de uitvoeringsmodus).

Welke methode u ook gebruikt, al deze configuratiemethoden:

* Zorg ervoor dat bij het kopiëren of repliceren van de inhoud van de opslagplaats identieke configuraties worden hersteld.
* Hiermee kunt u configuraties uitchecken naar FileVault of Subversion. voor beveiliging of verdere updates.
* Kan in pakketten worden opgeslagen voor gebruik bij het instellen van andere instanties.
* Sta u toe om configuratierolouts uit te voeren gebruikend manuscripten om de configuratiedetails voor te stellen.

>[!NOTE]
>
>De details van bepaalde belangrijke montages zijn vermeld onder [OSGi de Montages van de Configuratie.](/help/sites-deploying/osgi-configuration-settings.md)

## OSGi-configuratie met de webconsole {#osgi-configuration-with-the-web-console}

De [webconsole](/help/sites-deploying/web-console.md) in AEM biedt een gestandaardiseerde interface voor het configureren van de bundels. Het **tabblad Configuration** wordt gebruikt voor het configureren van de OSGi-bundels en is daarom het onderliggende mechanisme voor het configureren van AEM systeemparameters.

Eventuele aangebrachte wijzigingen worden onmiddellijk toegepast op de relevante OSGi-configuratie. Er is geen herstart nodig.

>[!NOTE]
>
>Wijzigingen die in de webconsole worden aangebracht, worden in de opslagplaats opgeslagen als [configuratiebestanden](#osgi-configuration-with-configuration-files). Deze kunnen worden opgenomen in inhoudspakketten voor hergebruik in verdere installaties.

>[!NOTE]
>
>Op de console van het Web om het even welke beschrijvingen die standaardmontages vermelden hebben op het Verschuiven gebreken.
>
>Adobe Experience Manager heeft zijn eigen gebreken en zodat zouden de vastgestelde gebreken van die op de console kunnen verschillen worden gedocumenteerd.

Een configuratie bijwerken met de webconsole:

1. Open het tabblad **Configuration** van de webconsole door:

   * Het openen van de Webconsole van de verbinding op **Hulpmiddel -> Verrichtingen** menu. Na het registreren in de console kunt u het drop-down menu gebruiken van:

      **OSGi >**

   * De directe URL; bijvoorbeeld:

      `http://localhost:4502/system/console/configMgr`
   Er wordt een lijst weergegeven.

1. Selecteer de bundel die u door één van beiden wilt vormen:

   * klikken op het pictogram **Bewerken** voor die bundel
   * klikken op de **Naam** van de bundel

1. Er wordt een dialoogvenster geopend. Hier kunt u desgewenst bewerken. Stel bijvoorbeeld **Logniveau** in op `INFO`:

   ![chlimage_1-140](assets/chlimage_1-140.png)

   >[!NOTE]
   >
   >Updates worden in de opslagplaats opgeslagen als [configuratiebestanden](#osgi-configuration-with-configuration-files). Als u deze naderhand wilt zoeken (bijvoorbeeld om de inhoud op te nemen in een inhoudspakket voor gebruik op een andere instantie), moet u een notitie maken van de blijvende identiteit ( `PID`).

1. Klik **Opslaan**.

   Uw veranderingen worden onmiddellijk toegepast op de relevante configuratie OSGi van het lopende systeem, wordt geen nieuw begin vereist.

   >[!NOTE]
   >
   >U kunt van verwant [configuratiedossier(s)](#osgi-configuration-with-configuration-files) nu de plaats bepalen; bijvoorbeeld om op te nemen in een inhoudspakket voor gebruik op een andere instantie.

## OSGi-configuratie met configuratiebestanden {#osgi-configuration-with-configuration-files}

Wijzigingen in de configuratie die zijn aangebracht met de webconsole blijven in de opslagplaats als configuratiebestanden ( `.config`) onder:

`/apps`

Deze kunnen in inhoudspakketten worden opgenomen en op andere instanties worden hergebruikt.

>[!NOTE]
>
>De indeling van de configuratiebestanden is zeer specifiek. Zie de [Sling Apache-documentatie](https://sling.apache.org/documentation/development/slingstart.html#default-configuration-format) voor meer informatie.
>
>Daarom wordt aangeraden het configuratiebestand te maken en te onderhouden door werkelijke wijzigingen aan te brengen in de webconsole.

De console van het Web toont geen aanwijzing van waar in de bewaarplaats uw veranderingen zijn bewaard, maar zij kunnen gemakkelijk worden gevestigd:

1. Maak het configuratiebestand door een eerste wijziging aan te brengen in de webconsole](#osgi-configuration-with-the-web-console).[
1. Open CRXDE Lite.
1. Selecteer in het menu **Extra** **Query..** .
1. Verzend een vraag van **Type** `SQL` om naar PID van de configuratie te zoeken die u hebt bijgewerkt.

   **Apache Felix OSGi Management Console** heeft bijvoorbeeld de persistente identiteit (PID) van:

   `org.apache.felix.webconsole.internal.servlet.OsgiManager`

   De SQL-query zou dus kunnen zijn:

   ```shell
   select * from nt:base where jcr:path like '/apps/%' and contains(*, 'org.apache.felix.webconsole.internal.servlet.OsgiManager')
   ```

1. De knoop van het configuratiedossier zal worden getoond.

   In het bovenstaande voorbeeld:

   `/apps/system/config/org.apache.felix.webconsole.internal.servlet.OsgiManager.config`

   >[!CAUTION]
   >
   >U kunt dit bestand openen om uw wijzigingen weer te geven, maar om typefouten te voorkomen, is het raadzaam werkelijke wijzigingen aan te brengen met de console.

1. U kunt nu een inhoudspakket maken dat dit knooppunt bevat en dat naar wens op de andere instanties wordt gebruikt.

## OSGi-configuratie in de opslagplaats {#osgi-configuration-in-the-repository}

Naast het gebruik van de webconsole kunt u ook configuratiegegevens definiëren in de opslagplaats. Hierdoor kunt u de verschillende uitvoeringsmodi eenvoudig configureren.

Deze configuraties worden gemaakt door `sling:OsgiConfig` knooppunten in de opslagplaats te maken waarnaar het systeem verwijst. Deze knopen weerspiegelen de configuraties OSGi, en vormen een gebruikersinterface aan hen. Om de configuratiegegevens bij te werken werkt u de knoopeigenschappen bij.

Als u de configuratiegegevens in de bewaarplaats wijzigt worden de veranderingen onmiddellijk toegepast op de relevante configuratie OSGi alsof de veranderingen gebruikend de console van het Web, met de aangewezen bevestiging en consistentiecontroles waren aangebracht. Dit geldt ook voor het kopiëren van een configuratie van `/libs/` naar `/apps/`.

Aangezien de zelfde configuratieparameter in verscheidene plaatsen kan worden gevestigd, kan het systeem:

* zoekopdrachten naar alle knooppunten van het type `sling:OsgiConfig`
* filters volgens de dienstnaam
* filters volgens de uitvoermodus

>[!NOTE]
>
>Lees ook [hoe u een op gegevensopslagruimte gebaseerde configuratie alleen voor een specifieke instantie definieert](https://helpx.adobe.com/experience-manager/kb/RunModeDependentConfigAndInstall.html).

### Een nieuwe configuratie toevoegen aan de opslagplaats {#adding-a-new-configuration-to-the-repository}

#### Wat u moet weten {#what-you-need-to-know}

Om een nieuwe configuratie aan de bewaarplaats toe te voegen moet u het volgende weten:

1. De **Persistent Identity** (PID) van de service.

   Verwijs het **Configurations** gebied in de console van het Web. De naam wordt tussen haakjes weergegeven na de bundelnaam (of in **Configuration Information** naar de onderkant van de pagina).

   Maak bijvoorbeeld een knooppunt `com.day.cq.wcm.core.impl.VersionManagerImpl.` om **AEM WCM Version Manager** te configureren.

   ![chlimage_1-141](assets/chlimage_1-141.png)

1. Of een specifieke [run mode](/help/sites-deploying/configure-runmodes.md) wordt vereist. Maak de map:

   * `config` - voor alle uitvoeringsmodi
   * `config.author` - voor de auteursomgeving
   * `config.publish` - voor de publicatieomgeving
   * `config.<run-mode>` - in voorkomend geval

1. Of een **Configuratie** of **Factory Configuration** noodzakelijk is.
1. de afzonderlijke parameters die moeten worden geconfigureerd; met inbegrip van bestaande parameterdefinities die opnieuw moeten worden gemaakt.

   Verwijs het individuele parametergebied in de console van het Web. De naam wordt tussen haakjes weergegeven voor elke parameter.

   Maak bijvoorbeeld een eigenschap
   `versionmanager.createVersionOnActivation` om versie  **maken bij activering** te configureren.

   ![chlimage_1-142](assets/chlimage_1-142.png)

1. Bestaat er al een configuratie in `/libs`? Als u alle configuraties in uw instantie wilt weergeven, gebruikt u het gereedschap **Query** in CRXDE Lite om de volgende SQL-query te verzenden:

   `select * from sling:OsgiConfig`

   Als zo, kan deze configuratie aan ` /apps/<yourProject>/` worden gekopieerd, dan aangepast in de nieuwe plaats.

#### De configuratie maken in de opslagplaats {#creating-the-configuration-in-the-repository}

Om de nieuwe configuratie aan de bewaarplaats eigenlijk toe te voegen:

1. Gebruik CRXDE Lite om te navigeren naar:

   ` /apps/<yourProject>`

1. Als dit nog niet het geval is, maakt u de `config`-map ( `sling:Folder`):

   * `config` - van toepassing op alle uitvoeringsmodi
   * `config.<run-mode>` - specifiek voor een bepaalde uitvoeringsmodus

1. Maak in deze map een knooppunt:

   * Type: `sling:OsgiConfig`
   * Naam: de persistente identiteit (PID);

      bijvoorbeeld voor AEM WCM Version Manager gebruik `com.day.cq.wcm.core.impl.VersionManagerImpl`
   >[!NOTE]
   >
   >Wanneer het maken van een Configuratie van de Fabriek voegt `-<identifier>` aan de naam toe.
   >
   >Zoals in: `org.apache.sling.commons.log.LogManager.factory.config-<identifier>`
   >
   >waarin `<identifier>` wordt vervangen door vrije tekst die u (moet) invoeren om het exemplaar te identificeren (u kunt deze informatie niet weglaten); bijvoorbeeld:
   >
   >`org.apache.sling.commons.log.LogManager.factory.config-MINE`

1. Voor elke parameter die u wilt vormen, creeer een bezit op deze knoop:

   * Naam: de parameternaam zoals aangetoond in de console van het Web; de naam wordt tussen haakjes weergegeven aan het einde van de veldbeschrijving. Gebruik `versionmanager.createVersionOnActivation` bijvoorbeeld voor `Create Version on Activation`
   * Type: in voorkomend geval.
   * Waarde: zoals vereist.

   U hoeft alleen eigenschappen te maken voor de parameters die u wilt configureren, anderen gebruiken nog steeds de standaardwaarden die door AEM zijn ingesteld.

1. Sla alle wijzigingen op.

   De veranderingen worden toegepast zodra de knoop door de dienst (zoals met veranderingen die in de console van het Web worden aangebracht) opnieuw te beginnen wordt bijgewerkt.

>[!CAUTION]
>
>U mag niets in de `/libs` weg veranderen.

>[!CAUTION]
>
>De volledige weg van een configuratie moet correct zijn om het bij opstarten te lezen.

## Configuratiedetails {#configuration-details}

### Resolutie van volgorde bij opstarten {#resolution-order-at-startup}

De volgende rangorde wordt gebruikt:

1. Opslagknooppunten onder `/apps/*/config...`.met het type `sling:OsgiConfig` of eigenschapsbestanden.

1. Opslagknooppunten met het type `sling:OsgiConfig` onder `/libs/*/config...`. (definities buiten de box).

1. Om het even welke `.config` dossiers van `<*cq-installation-dir*>/crx-quickstart/launchpad/config/...`. op het lokale bestandssysteem.

Dit betekent dat een generische configuratie in `/libs` door een projectspecifieke configuratie in `/apps` kan worden gemaskeerd.

### Resolutie van volgorde bij uitvoering {#resolution-order-at-runtime}

De veranderingen van de configuratie die worden aangebracht terwijl het systeem loopt teweegbrengen een herlading met de gewijzigde configuratie.

Dan is de volgende orde van belangrijkheid van toepassing:

1. Het wijzigen van een configuratie in de console van het Web zal onmiddellijk van kracht worden aangezien het belangrijkheid bij runtime neemt.
1. Het wijzigen van een configuratie in `/apps` zal onmiddellijk van kracht worden.
1. Het wijzigen van een configuratie in `/libs` zal onmiddellijk van kracht worden, tenzij het door een configuratie in `/apps` wordt gemaskeerd.

### Resolutie van meerdere uitvoermodi {#resolution-of-multiple-run-modes}

Voor configuraties die specifiek zijn voor de uitvoermodus, kunnen meerdere uitvoermodi worden gecombineerd. U kunt bijvoorbeeld configuratiemappen in de volgende stijl maken:

`/apps/*/config.<runmode1>.<runmode2>/`

Configuraties in dergelijke mappen worden toegepast als alle uitvoermodi overeenkomen met een uitvoeringsmodus die bij het opstarten is gedefinieerd.

Als een instantie bijvoorbeeld is gestart met de uitvoeringsmodi `author,dev,emea`, worden configuratieknooppunten in `/apps/*/config.emea`, `/apps/*/config.author.dev/` en `/apps/*/config.author.emea.dev/` toegepast, terwijl configuratieknooppunten in `/apps/*/config.author.asean/` en `/config/author.dev.emea.noldap/` niet worden toegepast.

Als meerdere configuraties voor dezelfde PID van toepassing zijn, wordt de configuratie met het hoogste aantal overeenkomende uitvoeringsmodi toegepast.

Als een instantie bijvoorbeeld is gestart met de uitvoeringsmodi `author,dev,emea` en `/apps/*/config.author/` en `/apps/*/config.emea.author/` een configuratie definiëren voor
`com.day.cq.wcm.core.impl.VersionManagerImpl`, wordt de configuratie in `/apps/*/config.emea.author/` toegepast.

De granulariteit van deze regel staat op een PID-niveau.
U kunt geen eigenschappen voor zelfde PID in `/apps/*/config.author/` en specifiekere degenen in `/apps/*/config.emea.author/` voor zelfde PID bepalen.
De configuratie met het hoogste aantal passende looppaswijzen zal voor volledige PID efficiënt zijn.

### Standaardconfiguraties {#standard-configurations}

In de volgende lijst ziet u een kleine selectie van de configuraties die beschikbaar zijn (in een standaardinstallatie) in de opslagplaats:

* Auteur - AEM WCM-filter:

   `libs/wcm/core/config.author/com.day.cq.wcm.core.WCMRequestFilter`

* Publiceren - AEM WCM-filter:

   `libs/wcm/core/config.publish/com.day.cq.wcm.core.WCMRequestFilter`

* Publiceren - AEM WCM-paginatiestatistieken:

   `libs/wcm/core/config.publish/com.day.cq.wcm.core.stats.PageViewStatistics`

>[!NOTE]
>
>Aangezien deze configuraties in `/libs` verblijven moeten zij niet direct worden uitgegeven, maar worden gekopieerd aan uw toepassingsgebied ( `/apps`) alvorens aanpassing.

Als u alle configuratieknooppunten in uw instantie wilt weergeven, gebruikt u de **Query**-functionaliteit in CRXDE Lite om de volgende SQL-query te verzenden:

`select * from sling:OsgiConfig`

### Configuratievolstand {#configuration-persistence}

* Als u een configuratie door de console van het Web verandert, wordt het (gewoonlijk) geschreven in de bewaarplaats bij:

   `/apps/{somewhere}`

   * Standaard is `{somewhere}` `system/config`, dus wordt de configuratie geschreven naar

      `/apps/system/config`

   * Als u echter een configuratie bewerkt die oorspronkelijk van elders in de opslagplaats afkomstig was: bijvoorbeeld:

      /libs/foo/config/someconfig

      Dan wordt de bijgewerkte configuratie geschreven onder de originele plaats; bijvoorbeeld:

      `/apps/foo/config/someconfig`

* Instellingen die worden gewijzigd door `admin` worden opgeslagen in `*.config`-bestanden onder:

   ```
      /crx-quickstart/launchpad/config
   ```

   * Dit is het privé gegevensgebied van OSGi configuratieadmin en houdt alle configuratiedetails die door `admin` worden gespecificeerd, ongeacht hoe zij het systeem inging.
   * Dit is een implementatiedetails en u moet deze folder niet direct uitgeven.
   * Het is echter handig om de locatie van deze configuratiebestanden te kennen, zodat u kopieën kunt maken voor back-up en/of meerdere installaties:

      * Apache Felix OSGi Management Console

         `../crx/org/apache/felix/webconsole/internal/servlet/OsgiManager.config`

      * CRX Sling Client Repository

         `../com/day/crx/sling/client/impl/CRXSlingClientRepository/<pid-nr>.config`

>[!CAUTION]
>
>U moet de mappen of bestanden onder ***nooit*** bewerken:
>
>`/crx-quickstart/launchpad/config`

