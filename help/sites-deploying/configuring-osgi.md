---
title: OSGi configureren
seo-title: OSGi configureren
description: OSGi is een fundamenteel element in de technologiestapel van de Manager van de Ervaring van Adobe (AEM). Het wordt gebruikt om de samengestelde bundels van AEM en hun configuratie te controleren. In dit artikel wordt beschreven hoe u de configuratie-instellingen voor dergelijke bundels kunt beheren.
seo-description: OSGi is een fundamenteel element in de technologiestapel van de Manager van de Ervaring van Adobe (AEM). Het wordt gebruikt om de samengestelde bundels van AEM en hun configuratie te controleren. In dit artikel wordt beschreven hoe u de configuratie-instellingen voor dergelijke bundels kunt beheren.
uuid: b39059a5-dd61-486a-869a-0d7a732c3a47
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: configuring
content-type: reference
discoiquuid: d701e4ba-417f-4b57-b103-27fd25290736
translation-type: tm+mt
source-git-commit: a3c303d4e3a85e1b2e794bec2006c335056309fb

---


# OSGi configureren{#configuring-osgi}

[OSGi](https://www.osgi.org/) is een fundamenteel element in de technologiestapel van de Manager van de Ervaring van Adobe (AEM). Het wordt gebruikt om de samengestelde bundels van AEM en hun configuratie te controleren.

OSGi &quot;*verstrekt de gestandaardiseerde primitieven die toepassingen toelaten om van kleine, herbruikbare en samenwerkende componenten worden gebouwd. Deze componenten kunnen in een toepassing worden samengesteld en worden opgesteld*&quot;.

Hierdoor kunt u eenvoudig bundels beheren, aangezien deze kunnen worden gestopt, geïnstalleerd en afzonderlijk kunnen worden gestart. De onderlinge afhankelijkheden worden automatisch verwerkt. Elke component OSGi (zie de Specificatie [](https://www.osgi.org/Specifications/HomePage)OSGi) is bevat in één van de diverse bundels.

U kunt de configuratie-instellingen voor dergelijke bundels beheren door:

* met de [Adobe CQ-webconsole](#osgi-configuration-with-the-web-console)
* gebruiken, [configuratiebestanden](#osgi-configuration-with-configuration-files)
* configureren van [inhoudknooppunten ( `sling:OsgiConfig`content-nodes) in de repository](#osgi-configuration-in-the-repository)

Beide methoden kunnen worden gebruikt, hoewel er subtiele verschillen zijn, vooral met betrekking tot [Run-modi](/help/sites-deploying/configure-runmodes.md):

* [Adobe CQ-webconsole](#osgi-configuration-with-the-web-console)

   * De console van het Web is de standaardinterface voor configuratie OSGi. Deze interface biedt een interface voor het bewerken van de verschillende eigenschappen, waarbij mogelijke waarden uit vooraf gedefinieerde lijsten kunnen worden geselecteerd.

      Als zodanig is het de eenvoudigste methode.

   * Om het even welke configuraties die met de Console van het Web worden aangebracht worden onmiddellijk toegepast en van toepassing op de huidige instantie, ongeacht de huidige looppaswijze, of om het even welke verdere veranderingen in de looppaswijze.

* [configuratiebestanden](#osgi-configuration-with-configuration-files)

   * Bevat instellingen die zijn gedefinieerd in de webconsole.
   * Kan worden opgenomen in inhoudspakketten voor gebruik op andere instanties.

* [content-nodes (sling:osgiConfig) in de repository](#osgi-configuration-in-the-repository)

   * Dit vereist handconfiguratie gebruikend CRXDE Lite.
   * Vanwege de naamgevingsconventies van de `sling:OsgiConfig` knooppunten kunt u de configuratie koppelen aan een specifieke [uitvoermodus](/help/sites-deploying/configure-runmodes.md). U kunt zelfs configuraties voor meer dan één uitvoeringswijze in de zelfde bewaarplaats opslaan.
   * Eventuele geschikte configuraties worden direct toegepast (afhankelijk van de uitvoeringsmodus).

Welke methode u ook gebruikt, al deze configuratiemethoden:

* Zorg ervoor dat bij het kopiëren of repliceren van de inhoud van de opslagplaats identieke configuraties worden hersteld.
* Hiermee kunt u configuraties uitchecken naar FileVault of Subversion. voor beveiliging of verdere updates.
* Kan in pakketten worden opgeslagen voor gebruik bij het instellen van andere instanties.
* Sta u toe om configuratierolouts uit te voeren gebruikend manuscripten om de configuratiedetails voor te stellen.

>[!NOTE]
>
>De details van bepaalde belangrijke montages zijn vermeld onder de Montages van de Configuratie [OSGi.](/help/sites-deploying/osgi-configuration-settings.md)

## OSGi Configuratie met de Console van het Web {#osgi-configuration-with-the-web-console}

De [webconsole](/help/sites-deploying/web-console.md) in AEM biedt een gestandaardiseerde interface voor het configureren van de bundels. Het lusje van de **Configuratie** wordt gebruikt voor het vormen van de bundels OSGi, en is daarom het onderliggende mechanisme voor het vormen van AEM systeemparameters.

Eventuele aangebrachte wijzigingen worden onmiddellijk toegepast op de relevante OSGi-configuratie. Er is geen herstart nodig.

>[!NOTE]
>
>Wijzigingen die in de webconsole worden aangebracht, worden in de opslagplaats opgeslagen als [configuratiebestanden](#osgi-configuration-with-configuration-files). Deze kunnen worden opgenomen in inhoudspakketten voor hergebruik in verdere installaties.

>[!NOTE]
>
>Op de console van het Web om het even welke beschrijvingen die standaardmontages vermelden hebben op het Verschuiven gebreken.
>
>Adobe Experience Manager heeft zijn eigen standaardinstellingen en de ingestelde standaardinstellingen kunnen afwijken van de op de console gedocumenteerde waarden.

Een configuratie bijwerken met de webconsole:

1. Heb toegang tot het lusje van de **Configuratie** van de Console van het Web door één van beiden:

   * De webconsole openen via de koppeling **Gereedschap -> Bewerkingen** . Na het registreren in de console kunt u het drop-down menu gebruiken van:

      **OSGi >**

   * De directe URL; bijvoorbeeld:

      `http://localhost:4502/system/console/configMgr`
   Er wordt een lijst weergegeven.

1. Selecteer de bundel die u door één van beiden wilt vormen:

   * klikken op het pictogram **Bewerken** voor die bundel
   * klikken op de **naam** van de bundel

1. Er wordt een dialoogvenster geopend. Hier kunt u desgewenst bewerken. Stel bijvoorbeeld het **logniveau** in op `INFO`:

   ![chlimage_1-140](assets/chlimage_1-140.png)

   >[!NOTE]
   >
   >Updates worden in de opslagplaats opgeslagen als [configuratiebestanden](#osgi-configuration-with-configuration-files). Als u deze achteraf wilt zoeken (bijvoorbeeld om de inhoud op te nemen in een inhoudspakket voor gebruik op een andere instantie), moet u een notitie maken van de blijvende identiteit ( `PID`).

1. Click **Save**.

   Uw veranderingen worden onmiddellijk toegepast op de relevante configuratie OSGi van het lopende systeem, wordt geen nieuw begin vereist.

   >[!NOTE]
   >
   >U kunt nu de verwante [configuratiebestanden zoeken](#osgi-configuration-with-configuration-files); bijvoorbeeld om op te nemen in een inhoudspakket voor gebruik op een andere instantie.

## OSGi-configuratie met configuratiebestanden {#osgi-configuration-with-configuration-files}

De veranderingen van de configuratie die worden aangebracht gebruikend de Console van het Web worden voortgeduurd in de bewaarplaats als configuratiedossiers ( `.config`) onder:

`/apps`

Deze kunnen in inhoudspakketten worden opgenomen en op andere instanties worden hergebruikt.

>[!NOTE]
>
>De indeling van de configuratiebestanden is zeer specifiek. Raadpleeg de documentatie [van](https://sling.apache.org/documentation/development/slingstart.html#default-configuration-format) Sling Apache voor meer informatie.
>
>Daarom wordt aangeraden het configuratiebestand te maken en te onderhouden door werkelijke wijzigingen aan te brengen in de webconsole.

De console van het Web toont geen aanwijzing van waar in de bewaarplaats uw veranderingen zijn bewaard, maar zij kunnen gemakkelijk worden gevestigd:

1. Maak het configuratiebestand door een eerste wijziging [aan te brengen in de webconsole](#osgi-configuration-with-the-web-console).
1. Open CRXDE Lite.
1. **Selecteer** Query in het menu **Gereedschappen**.. .
1. Verzend een vraag van **Type** `SQL` aan onderzoek naar PID van de configuratie die u hebt bijgewerkt.

   Zo heeft **Apache Felix OSGi Management Console** bijvoorbeeld de persistente id (PID) van:

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

Deze configuraties worden gemaakt door knooppunten in de opslagplaats te maken waarnaar het systeem kan verwijzen. `sling:OsgiConfig` Deze knopen weerspiegelen de configuraties OSGi, en vormen een gebruikersinterface aan hen. Om de configuratiegegevens bij te werken werkt u de knoopeigenschappen bij.

Als u de configuratiegegevens in de bewaarplaats wijzigt worden de veranderingen onmiddellijk toegepast op de relevante configuratie OSGi alsof de veranderingen gebruikend de console van het Web, met de aangewezen bevestiging en consistentiecontroles waren aangebracht. Dit geldt ook voor het kopiëren van een configuratie van `/libs/` naar `/apps/`.

Aangezien de zelfde configuratieparameter in verscheidene plaatsen kan worden gevestigd, kan het systeem:

* zoekopdrachten naar alle knooppunten van het type `sling:OsgiConfig`
* filters volgens de dienstnaam
* filters volgens de uitvoermodus

>[!NOTE]
>
>Lees ook [hoe u een op gegevensopslagruimte gebaseerde configuratie alleen](https://helpx.adobe.com/experience-manager/kb/RunModeDependentConfigAndInstall.html)voor een specifieke instantie definieert.

### Een nieuwe configuratie toevoegen aan de opslagplaats {#adding-a-new-configuration-to-the-repository}

#### Wat u moet weten {#what-you-need-to-know}

Om een nieuwe configuratie aan de bewaarplaats toe te voegen moet u het volgende weten:

1. The **Persistent Identity** (PID) of the service.

   Verwijs naar het gebied van **Configuraties** in de console van het Web. De naam wordt tussen haakjes weergegeven na de bundelnaam (of in de **configuratiegegevens** onder aan de pagina).

   Maak bijvoorbeeld een knooppunt `com.day.cq.wcm.core.impl.VersionManagerImpl.` om **AEM WCM Version Manager** te configureren.

   ![chlimage_1-141](assets/chlimage_1-141.png)

1. Of een specifieke [looppaswijze](/help/sites-deploying/configure-runmodes.md) wordt vereist. Maak de map:

   * `config` - voor alle uitvoeringsmodi
   * `config.author` - voor de auteursomgeving
   * `config.publish` - voor de publicatieomgeving
   * `config.<run-mode>` - in voorkomend geval

1. Of een **Configuratie** of een Configuratie **van de** Fabriek noodzakelijk is.
1. de afzonderlijke parameters die moeten worden geconfigureerd; met inbegrip van bestaande parameterdefinities die opnieuw moeten worden gemaakt.

   Verwijs het individuele parametergebied in de console van het Web. De naam wordt tussen haakjes weergegeven voor elke parameter.

   Maak bijvoorbeeld een eigenschap
   `versionmanager.createVersionOnActivation` om versie **maken bij activering** te configureren.

   ![chlimage_1-142](assets/chlimage_1-142.png)

1. Bestaat er al een configuratie in `/libs`? Als u alle configuraties in uw instantie wilt weergeven, gebruikt u het gereedschap **Query** in CRXDE Lite om de volgende SQL-query te verzenden:

   `select * from sling:OsgiConfig`

   Als zo, kan deze configuratie aan worden gekopieerd ` /apps/<yourProject>/`, dan in de nieuwe plaats worden aangepast.

#### De configuratie maken in de opslagplaats {#creating-the-configuration-in-the-repository}

Om de nieuwe configuratie aan de bewaarplaats eigenlijk toe te voegen:

1. Gebruik CRXDE Lite om te navigeren naar:

   ` /apps/<yourProject>`

1. Als deze nog niet bestaat, maakt u de `config` map ( `sling:Folder`):

   * `config` - van toepassing op alle uitvoeringsmodi
   * `config.<run-mode>` - specifiek voor een bepaalde uitvoeringsmodus

1. Maak in deze map een knooppunt:

   * Type: `sling:OsgiConfig`
   * Naam: de persistente identiteit (PID);

      bijvoorbeeld het gebruik van AEM WCM Version Manager `com.day.cq.wcm.core.impl.VersionManagerImpl`
   >[!NOTE]
   >
   >Wanneer het maken van een Configuratie van de Fabriek voegt `-<identifier>` aan de naam toe.
   >
   >Zoals in: `org.apache.sling.commons.log.LogManager.factory.config-<identifier>`
   >
   >Waar `<identifier>` wordt vervangen door vrije tekst die u (moet) invoeren om het exemplaar te identificeren (u kunt deze informatie niet weglaten); bijvoorbeeld:
   >
   >`org.apache.sling.commons.log.LogManager.factory.config-MINE`

1. Voor elke parameter die u wilt vormen, creeer een bezit op deze knoop:

   * Naam: de parameternaam zoals aangetoond in de console van het Web; de naam wordt tussen haakjes weergegeven aan het einde van de veldbeschrijving. Bijvoorbeeld voor `Create Version on Activation` gebruik `versionmanager.createVersionOnActivation`
   * Type: in voorkomend geval.
   * Waarde: zoals vereist.
   U hoeft alleen eigenschappen te maken voor de parameters die u wilt configureren, anderen gebruiken nog steeds de standaardwaarden die door AEM zijn ingesteld.

1. Sla alle wijzigingen op.

   De veranderingen worden toegepast zodra de knoop door de dienst (zoals met veranderingen die in de console van het Web worden aangebracht) opnieuw te beginnen wordt bijgewerkt.

>[!CAUTION]
>
>U mag niets in het `/libs` pad wijzigen.

>[!CAUTION]
>
>De volledige weg van een configuratie moet correct zijn om het bij opstarten te lezen.

## Configuratiedetails {#configuration-details}

### Volgorde resolutie bij opstarten {#resolution-order-at-startup}

De volgende rangorde wordt gebruikt:

1. Opslagknooppunten `/apps/*/config...`.met type- `sling:OsgiConfig` of eigenschapsbestanden.

1. Opslagknooppunten met type `sling:OsgiConfig` onder `/libs/*/config...`. (definities buiten de box).

1. Alle `.config` bestanden van `<*cq-installation-dir*>/crx-quickstart/launchpad/config/...`. op het lokale bestandssysteem.

Dit betekent dat een generische configuratie binnen door een project specifieke configuratie in `/libs` kan worden gemaskeerd `/apps`.

### Volgorde van resolutie bij uitvoering {#resolution-order-at-runtime}

De veranderingen van de configuratie die worden aangebracht terwijl het systeem loopt teweegbrengen een herlading met de gewijzigde configuratie.

Dan is de volgende orde van belangrijkheid van toepassing:

1. Het wijzigen van een configuratie in de console van het Web zal onmiddellijk van kracht worden aangezien het belangrijkheid bij runtime neemt.
1. Het wijzigen van een configuratie in `/apps` zal onmiddellijk van kracht worden.
1. Het wijzigen van een configuratie binnen `/libs` zal onmiddellijk van kracht worden, tenzij het door een configuratie binnen wordt gemaskeerd `/apps`.

### Resolutie van meerdere uitvoermodi {#resolution-of-multiple-run-modes}

Voor configuraties die specifiek zijn voor de uitvoermodus, kunnen meerdere uitvoermodi worden gecombineerd. U kunt bijvoorbeeld configuratiemappen in de volgende stijl maken:

`/apps/*/config.<runmode1>.<runmode2>/`

Configuraties in dergelijke mappen worden toegepast als alle uitvoermodi overeenkomen met een uitvoeringsmodus die bij het opstarten is gedefinieerd.

Bijvoorbeeld, als een instantie met de looppaswijzen was begonnen `author,dev,emea`, zullen de configuratieknopen in `/apps/*/config.emea`, `/apps/*/config.author.dev/` en `/apps/*/config.author.emea.dev/` worden toegepast, terwijl de configuratieknopen in `/apps/*/config.author.asean/` en `/config/author.dev.emea.noldap/` niet zullen worden toegepast.

Als meerdere configuraties voor dezelfde PID van toepassing zijn, wordt de configuratie met het hoogste aantal overeenkomende uitvoeringsmodi toegepast.

Bijvoorbeeld, als een instantie met de looppaswijzen was begonnen `author,dev,emea`, en zowel `/apps/*/config.author/` en een configuratie voor `/apps/*/config.emea.author/` bepaalt, zal de configuratie binnen`com.day.cq.wcm.core.impl.VersionManagerImpl``/apps/*/config.emea.author/` worden toegepast.

De granulariteit van deze regel staat op een PID-niveau.
U kunt bepaalde eigenschappen voor dezelfde PID niet definiëren in `/apps/*/config.author/` `/apps/*/config.emea.author/` en meer specifieke eigenschappen voor dezelfde PID.
De configuratie met het hoogste aantal passende looppaswijzen zal voor volledige PID efficiënt zijn.

### Standaardconfiguraties {#standard-configurations}

In de volgende lijst ziet u een kleine selectie van de configuraties die beschikbaar zijn (in een standaardinstallatie) in de opslagplaats:

* Auteur - AEM WCM-filter:

   `libs/wcm/core/config.author/com.day.cq.wcm.core.WCMRequestFilter`

* Publiceren - AEM WCM-filter:

   `libs/wcm/core/config.publish/com.day.cq.wcm.core.WCMRequestFilter`

* Publiceren - AEM WCM-paginatistieken:

   `libs/wcm/core/config.publish/com.day.cq.wcm.core.stats.PageViewStatistics`

>[!NOTE]
>
>Aangezien deze configuraties zich in `/libs` deze configuraties bevinden, moeten ze niet direct worden bewerkt, maar worden gekopieerd naar het toepassingsgebied ( `/apps`) voordat ze worden aangepast.

Om van alle configuratieknooppunten in uw instantie een lijst te maken, gebruik de functionaliteit van de **Vraag** in CRXDE Lite om de volgende SQL vraag voor te leggen:

`select * from sling:OsgiConfig`

### Configuratievolstand {#configuration-persistence}

* Als u een configuratie door de console van het Web verandert, wordt het (gewoonlijk) geschreven in de bewaarplaats bij:

   `/apps/{somewhere}`

   * Standaard `{somewhere}` is dit `system/config` de configuratie waarnaar wordt geschreven

      `/apps/system/config`

   * Als u echter een configuratie bewerkt die oorspronkelijk van elders in de opslagplaats afkomstig was: bijvoorbeeld:

      /libs/foo/config/someconfig

      Dan wordt de bijgewerkte configuratie geschreven onder de originele plaats; bijvoorbeeld:

      `/apps/foo/config/someconfig`

* Instellingen die worden gewijzigd door, worden opgeslagen in `admin` `*.config` bestanden onder:

   ```
      /crx-quickstart/launchpad/config
   ```

   * Dit is het privé gegevensgebied van OSGi configuratieadmin en houdt alle configuratiedetails die door worden gespecificeerd, ongeacht hoe zij het systeem inging. `admin`
   * Dit is een implementatiedetails en u moet deze folder niet direct uitgeven.
   * Het is echter handig om de locatie van deze configuratiebestanden te kennen, zodat u kopieën kunt maken voor back-up en/of meerdere installaties:

      * Apache Felix OSGi Management Console

         `../crx/org/apache/felix/webconsole/internal/servlet/OsgiManager.config`

      * CRX Sling Client Repository

         `../com/day/crx/sling/client/impl/CRXSlingClientRepository/<pid-nr>.config`

>[!CAUTION]
>
>U mag de mappen of bestanden ***nooit*** bewerken onder:
>
>`/crx-quickstart/launchpad/config`

