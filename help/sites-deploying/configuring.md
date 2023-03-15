---
title: Basisconfiguratieconcepten
seo-title: Basic Configuration Concepts
description: Leer hoe te om AEM te vormen.
seo-description: Learn how to configure AEM.
uuid: edcdd4bd-5917-417e-8913-40d488383ea9
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: configuring
content-type: reference
discoiquuid: 2673ea92-1651-4b1b-9aac-f4ba8b36782e
feature: Configuring
exl-id: 3777a1ba-cc4e-41b9-9098-236f8141925f
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '2124'
ht-degree: 0%

---

# Basisconfiguratieconcepten{#basic-configuration-concepts}

Adobe Experience Manager (AEM) wordt geïnstalleerd met standaardinstellingen voor alle parameters, zodat deze &quot;buiten het vak&quot; kan worden uitgevoerd. Nochtans, kunt u AEM voor uw eigen specifieke vereisten vormen.

Er zijn vele aspecten van AEM die kunnen worden gevormd:

* Sommige zijn [algemeen gevormd voor elke projectinstallatie](#primary-configuration-considerations) en moet worden herzien om te bevestigen of zij op uw project van toepassing zijn of niet.
* [Andere configuraties](#further-configuration-considerations) kunnen algemeen zijn, maar niet noodzakelijk; gerelateerd aan functies, of systeemprestaties en stabiliteit.
* Andere functies zijn alleen vereist voor bepaalde optionele functies van AEM (deze worden samen met de desbetreffende functie beschreven).

Afhankelijk van de specifieke configuratie kunnen deze veranderingen door één van beide worden aangebracht:

* **Adobe CQ-webconsole**

   Dit is een standaardplaats voor het vormen van bundels OSGi en de diensten.

   Zie [OSGi configureren](/help/sites-deploying/configuring-osgi.md) voor meer details en aanbevolen praktijken.

* **Bewaarplaats**

   Een subset van OSGi configuraties is beschikbaar in de bewaarplaats. Dit zorgt ervoor dat het kopiëren, of het repliceren, de inhoud van de bewaarplaats identieke configuraties ontspannen. U kunt ook uw eigen configuraties, afhankelijk van de uitvoeringsmodus, aan de opslagplaats toevoegen.

   Zie [OSGi-configuratie in de opslagplaats](/help/sites-deploying/configuring-osgi.md#osgi-configuration-in-the-repository) en met name [Een nieuwe configuratie toevoegen aan de opslagplaats](/help/sites-deploying/configuring-osgi.md#adding-a-new-configuration-to-the-repository) voor nadere bijzonderheden.

* **Bestandssysteem**

   Enkele configuratiebestanden bevinden zich in het bestandssysteem.

* **AEM WCM**

   Diverse aspecten kunnen binnen AEM WCM zelf worden gevormd, velen die gebruiken [Gereedschappen](/help/sites-administering/tools-consoles.md) console; bijvoorbeeld, replicatieagenten.

>[!NOTE]
>
>Wanneer het werken met Adobe Experience Manager, zijn er verscheidene methodes om de configuratiemontages voor de diensten OSGi (console of bewaargegevensknooppunten) te beheren.
>
>Zie [OSGi configureren](/help/sites-deploying/configuring-osgi.md) voor volledige informatie.

>[!NOTE]
>
>Het vormen AEM is duidelijk, maar u moet zich ervan bewust zijn dat:
>
>Bepaalde wijzigingen kunnen grote gevolgen hebben voor de toepassing(en). Om deze reden, verzeker u de noodzakelijke ervaring en de kennis alvorens u begint AEM te vormen, en slechts de veranderingen aan te brengen die u weet worden vereist. Alle wijzigingen die via de OSGi-console zijn aangebracht, zijn **onmiddellijk** toegepast op het actieve systeem (opnieuw opstarten is niet vereist).

## Belangrijkste overwegingen voor configuratie {#primary-configuration-considerations}

Deze lijst detailleert de primaire gebieden die algemeen voor elk nieuw project worden gevormd. Niet alles is nodig, maar de lijst moet gelezen en herzien worden om te zien wat op uw project van toepassing is.

De lijst geeft een kort overzicht van elk configuratieaspect, samen met verbindingen aan de pagina&#39;s die volledige details verstrekken.

### Beveiligingscontrolelijst {#security-checklist}

Verschillende belangrijke configuratieproblemen worden vermeld in het dialoogvenster [Beveiligingscontrolelijst](/help/sites-administering/security-checklist.md). Lees dit door en voer de benodigde actie voor de installatie uit.

### De standaardinterface configureren - geoptimaliseerd voor aanraking of Klassiek {#configuring-the-default-ui-touch-optimized-or-classic}

Er zijn twee UIs beschikbaar voor gebruik in AEM:

* De interface met aanraakfuncties
* De klassieke gebruikersinterface

U kunt UI vormen u het gebruiken vereist [Hoofdtoewijzing](/help/sites-deploying/osgi-configuration-settings.md).

>[!NOTE]
>
>Meer informatie over de keuze van de interface is beschikbaar onder [Gebruikersinterface selecteren](/help/sites-authoring/select-ui.md).

### IPv4 en IPv6 {#ipv-and-ipv}

Alle elementen van AEM (bijvoorbeeld de opslagplaats, de Dispatcher, enz.) kunnen in zowel IPv4- als IPv6-netwerken worden geïnstalleerd.

De verrichting is naadloos aangezien geen speciale configuratie wordt vereist, wanneer nodig kunt u een IP adres eenvoudig specificeren gebruikend het formaat dat aan uw netwerktype aangewezen is.

Dit betekent dat wanneer een IP adres moet worden gespecificeerd u (zoals vereist) van kunt selecteren:

* een IPv6-adres

   bijvoorbeeld `https://[ab12::34c5:6d7:8e90:1234]:4502`

* een IPv4-adres

   bijvoorbeeld `https://123.1.1.4:4502`

* een servernaam

   bijvoorbeeld: `https://www.yourserver.com:4502`

* het standaardgeval van `localhost` zal voor zowel IPv4 als IPv6 netwerkinstallaties worden geïnterpreteerd

   bijvoorbeeld: `http://localhost:4502`

### Versie leegmaken {#version-purging}

In een standaardinstallatie maakt AEM een nieuwe versie van een pagina of knooppunt wanneer u een pagina activeert (nadat u de inhoud hebt bijgewerkt). U kunt ook op verzoek extra versies maken met de opdracht **Versioning** tabblad van het hulpwerkje. Al deze versies worden opgeslagen in de opslagplaats en kunnen indien nodig worden hersteld.

Deze versies worden nooit gewist, zodat de grootte van de opslagplaats na verloop van tijd zal groeien en daarom moet worden beheerd.

Zie [Versie leegmaken](/help/sites-deploying/version-purging.md) voor volledige informatie, met name [Versiebeheer](/help/sites-deploying/version-purging.md#version-manager) voor details van hoe te om AEM te vormen om oudere versies te zuiveren wanneer een nieuwe versie wordt gecreeerd.

### Logboekregistratie {#logging}

AEM biedt u de mogelijkheid om te vormen:

* globale parameters voor de centrale houtkapdienst
* verzoeken om registratie van gegevens; een gespecialiseerde registrerenconfiguratie voor verzoekinformatie
* specifieke instellingen voor de afzonderlijke diensten; bijvoorbeeld een afzonderlijk logbestand en een indeling voor de logberichten

Zie [Logboekregistratie](/help/sites-deploying/configure-logging.md) voor volledige informatie.

### Modi uitvoeren {#run-modes}

Met de uitvoermodi kunt u uw AEM instellen voor een bepaald doel. bijvoorbeeld auteur of publicatie, test, ontwikkeling of intranet, enz.

Dit wordt gedaan door inzamelingen van configuratieparameters voor elke looppaswijze te bepalen. Een basisreeks configuratieparameters wordt toegepast voor alle looppaswijzen, kunt u extra reeksen aan het doel van uw specifiek milieu dan stemmen. Deze worden vervolgens naar wens toegepast.

Alle configuratie-instellingen worden opgeslagen in de ene opslagplaats en geactiveerd door de instelling van de **Run-modus**.

Zie [Modi uitvoeren](/help/sites-deploying/configure-runmodes.md) voor volledige informatie.

### Single Sign On {#single-sign-on}

Met Single Sign On (SSO) heeft een gebruiker toegang tot meerdere systemen nadat hij de verificatiegegevens (zoals een gebruikersnaam en wachtwoord) eenmaal heeft opgegeven. Een afzonderlijk systeem (dat als vertrouwde op authentiek wordt bekend) voert de authentificatie uit en verstrekt Experience Manager de gebruikersgeloofsbrieven. De Experience Manager controleert en handhaaft de toegangstoestemmingen voor de gebruiker (d.w.z. bepaalt welke middelen de gebruiker wordt toegestaan om toegang te hebben).

Zie [Single Sign On](/help/sites-deploying/single-sign-on.md) voor nadere bijzonderheden.

### Brontoewijzing {#resource-mapping}

De afbeelding van het middel wordt gebruikt om omleidingen, ijdelheid URLs en virtuele gastheren voor AEM te bepalen.

U kunt bijvoorbeeld de volgende toewijzingen gebruiken:

* Alle aanvragen vooraf bevestigen met `/content` zodat de interne structuur verborgen is voor de bezoekers van uw website.
* Definieer een omleiding, zodat alle verzoeken aan de `/content/en/gateway` pagina van uw website wordt omgeleid naar `https://gbiv.com/`.

Zie [Brontoewijzing](/help/sites-deploying/resource-mapping.md) voor nadere bijzonderheden.

### Replicatie-, omgekeerde replicatie- en replicatie-agents {#replication-reverse-replication-and-replication-agents}

De agenten van de replicatie zijn centraal aan AEM als mechanisme dat wordt gebruikt om:

* [Publiceren (activeren)](/help/sites-authoring/publishing-pages.md) inhoud van een auteur naar een publicatieomgeving.
* Inhoud expliciet uit de Dispatcher-cache verwijderen.
* Hiermee wordt gebruikersinvoer (bijvoorbeeld formulierinvoer) vanuit de publicatieomgeving geretourneerd naar de auteursomgeving (onder controle van de auteursomgeving).

Zie voor meer informatie [Replicatie](/help/sites-deploying/replication.md).

### OSGi-configuratie-instellingen {#osgi-configuration-settings}

[OSGi](https://www.osgi.org/) is een fundamenteel element in de technologiestapel van AEM. Het wordt gebruikt om de samengestelde bundels van AEM en hun configuratie te controleren.

Zie [OSGi-configuratie-instellingen](/help/sites-deploying/osgi-configuration-settings.md) voor een lijst van de verschillende bundels die relevant zijn voor de uitvoering van het project (vermeld volgens bundel). Niet alle instellingen in de lijst hoeven te worden aangepast. Sommige instellingen worden vermeld om u te helpen begrijpen hoe AEM werkt.

Wanneer het werken met AEM zijn er verscheidene methodes om de configuratiemontages voor dergelijke diensten te beheren; zie [OSGi configureren](/help/sites-deploying/configuring-osgi.md) voor meer details en de aanbevolen werkwijzen.

### LDAP configureren {#configuring-ldap}

LDAP-verificatie is vereist voor verificatie van gebruikers die zijn opgeslagen in een (centrale) LDAP-directory, zoals Active Directory. Dit helpt de inspanning te verminderen die wordt vereist om gebruikersrekeningen te beheren.

LDAP-verificatie vindt plaats op het niveau van de gegevensopslagruimte, zodat deze rechtstreeks door de gegevensopslagruimte wordt afgehandeld. Zie voor meer informatie [LDAP configureren met AEM](/help/sites-administering/ldap-config.md).

Voor gebruikersbeheer binnen AEM (inclusief toewijzing van toegangsrechten) raadpleegt u [Gebruikersbeheer en beveiliging](/help/sites-administering/security.md).

### De Dispatcher configureren {#configuring-the-dispatcher}

Dispatcher is een Adobe Experience Manager-programma voor caching en/of taakverdeling dat kan worden gebruikt in combinatie met een webserver op bedrijfsniveau.

Zie [Dispatcher](https://helpx.adobe.com/experience-manager/dispatcher/using/dispatcher.html) voor volledige informatie, met name [De Dispatcher configureren](https://helpx.adobe.com/experience-manager/dispatcher/using/dispatcher-configuration.html) voor meer configuratiedetails.

### AEM LiveCycle Connector configureren {#configuring-aem-livecycle-connector}

Met de versie van de AEM Doc Services en de Veiligheid van AEM Doc, hebben wij nu het vermogen om de documentdiensten van LiveCycle aan te halen om een XFA vorm terug te geven, een document in PDF om te zetten en beleid te beschermen een document. Lees [AEM LiveCycle Connector](https://helpx.adobe.com/livecycle/help/aem/aem-livecycle-connector.html) voor meer informatie .

### Het Verschuiven van de baan en het Beleid van de Topologie {#job-offloading-and-topology-administration}

[Verschuiven](/help/sites-deploying/offloading.md) distribueert verwerkingstaken die instanties van de Experience Manager in een topologie. Met offloading kunt u specifieke instanties van Experience Managers gebruiken voor het uitvoeren van specifieke typen verwerking. Met gespecialiseerde verwerking kunt u het gebruik van beschikbare serverbronnen maximaliseren.

De technologieën zijn losjes-verbonden clusters van de Experience Manager die aan het ontladen deelnemen. Een cluster bestaat uit een of meer serverinstanties van de Experience Manager (één instantie wordt beschouwd als een cluster).

Voor meer informatie over om topologielidmaatschap te bekijken of te wijzigen, raadpleeg [Onderwerptechnologieën beheren](/help/sites-deploying/offloading.md#administering-topologies) sectie.

### De welkomstconsole configureren {#configuring-the-welcome-console}

De welkomstconsole van de klassieke UI biedt een lijst met koppelingen naar de verschillende consoles en functionaliteit binnen AEM.

Het is mogelijk om de verbindingen te vormen die zichtbaar zijn, zie [De welkomstconsole configureren](/help/sites-developing/customizing-the-welcome-console.md) voor nadere bijzonderheden.

### Configureren voor prestaties {#configuring-for-performance}

[Prestaties](/help/sites-deploying/configuring-performance.md) is de sleutel tot uw project. Bepaalde aspecten van AEM (en/of de onderliggende opslagplaats) kunnen worden geconfigureerd om de prestaties te optimaliseren.

Zie [Configureren voor prestaties](/help/sites-deploying/configuring-performance.md#configuring-for-performance) voor nadere bijzonderheden.

<!--delete ### Scaling {#scaling}

Scaling a CQ installation correctly depends greatly on the details of your particular use case. A detailed discussion of solution patterns for various situations can be found in [Scaling CQ](/help/sites-deploying/scaling.md).-->

### Gedeelde gegevensopslag {#shared-data-store}

De gegevensopslagplaats van de opslagplaats wordt gebruikt om de opslag van grote binaire bestanden van de opslagplaats zelf naar een afzonderlijk gebied te offloaden, zodat meerdere instanties van hetzelfde binaire (bijvoorbeeld een afbeelding) binnen de opslagplaats slechts eenmaal worden opgeslagen.

Deze &quot;store-once, reference-many-times&quot;eigenschap kan worden uitgebreid om niet alleen één enkele opslagplaats maar volledig afzonderlijke bewaarplaatsen te dienen, door de gegevensopslag van elk te vormen om naar de zelfde gedeelde plaats van het dossiersysteem te verwijzen.

Een dergelijke gegevensopslag kan worden gedeeld tussen verschillende knooppunten in dezelfde cluster, verschillende publicatie- en/of auteurinstanties in dezelfde installatie of zelfs geheel afzonderlijke instanties in verschillende installaties.

Zie voor meer informatie [Gegevensopslag en knooppuntopslag configureren](/help/sites-deploying/data-store-config.md).

## Meer configuratieoverwegingen {#further-configuration-considerations}

### HTTP inschakelen via SSL {#enabling-http-over-ssl}

U kunt HTTP via SSL inschakelen om veiligere verbindingen met uw servers te gebruiken.

Zie [HTTP inschakelen via SSL](/help/sites-administering/ssl-by-default.md) voor nadere bijzonderheden.

### AEM en portlets {#aem-portals-and-portlets}

Een portal is een webtoepassing die verpersoonlijking, één aanmelding, integratie van inhoud uit verschillende bronnen en de presentatielaag van informatiesystemen host. Met de portletcomponent kunt u ook een portlet op de pagina insluiten. Als u toegang wilt krijgen tot inhoud van de CQ5 WCM, kan de portalserver worden uitgerust met de CQ5 Portal Director Portlet. U kunt dit doen door portlet te installeren, te vormen en toe te voegen aan de portlet pagina.

Zie [Portaal en portlets](/help/sites-administering/aem-as-portal.md) voor nadere bijzonderheden.

### Verlopen van statische objecten {#expiration-of-static-objects}

Statische objecten (bijvoorbeeld pictogrammen) veranderen niet. Daarom moet het systeem zo worden geconfigureerd dat zij niet (gedurende een redelijke periode) verlopen en zo onnodig verkeer verminderen.

Zie [Verlopen van statische objecten](/help/sites-deploying/expiration-static-objects.md) voor nadere bijzonderheden.

### FI&#39;s openen in het Java-proces {#open-files-in-the-java-process}

Elk Java-proces heeft toegang tot bestanden - hiervoor zijn systeembronnen vereist. Daarom wordt een bovengrens gedefinieerd voor het aantal bestanden dat elk proces gelijktijdig mag openen. Als dit wordt overschreden, kan een uitzonderingsfout voorkomen.

Als het AEM dit maximum overschrijdt, verschijnt het bericht &quot; `too many open files`&quot; wordt weergegeven in `error.log`.

Om dergelijke uitzonderingen te vermijden, moet u:

1. Controleer hoeveel geopende bestanden uw AEM gebruikt.

   Hoe u deze controle uitvoert, is afhankelijk van het platform waarop uw instantie wordt uitgevoerd. U kunt hulpprogramma&#39;s gebruiken, zoals Lay of (Unix) of Procesverkenner (Windows).

   Deze waarde moet tijdens de ontwikkeling en het testen worden gecontroleerd op:

   * bevestigen dat bestanden naar wens worden gesloten
   * om de vereiste maximumwaarde te bepalen (onder verschillende omstandigheden)

1. Stel het toegestane maximum in.

   De nieuwe waarde moet rekening houden met zowel de huidige als de toekomstige behoeften, zodat het raadzaam is de huidige behoeften te verdubbelen.

   Standaard, `serverctl` vormen `CQ_MAX_OPEN_FILES` tot `8192`; dit zou voor de meeste scenario &#39; s voldoende moeten zijn .

### De Rich Text Editor configureren {#configuring-the-rich-text-editor}

De **RTF-editor** (**RTE**) biedt auteurs een groot aantal [functionaliteit](/help/sites-authoring/rich-text-editor.md) voor het bewerken van hun tekstinhoud; hen voorzien van pictogrammen, selectiekaders en menu&#39;s voor een ervaring WYSIWYG.

Zie [De Rich Text Editor configureren](/help/sites-administering/rich-text-editor.md) voor nadere bijzonderheden.

### Ongedaan maken configureren voor paginabewerking {#configuring-undo-for-page-editing}

Er zijn diverse eigenschappen die het gedrag bepalen van de opdrachten Ongedaan maken en Opnieuw voor het bewerken van pagina&#39;s. Deze kunnen worden gevormd, zie [Ongedaan maken configureren voor paginabewerking](/help/sites-administering/config-undo.md) voor nadere bijzonderheden.

### De videocomponent configureren {#configuring-the-video-component}

De [Video-component](/help/sites-authoring/default-components-foundation.md#video) kunt u een vooraf gedefinieerd, out-of-the-box video-element op uw pagina plaatsen.

Voor een juiste transcodering moet uw beheerder [Mpeg installeren](/help/sites-administering/config-video.md#install-ffmpeg) afzonderlijk. Zij kunnen ook [Uw videoprofielen configureren](/help/sites-administering/config-video.md#configure-video-profiles) voor gebruik met html5-elementen.

### Rapporten configureren en aanpassen {#configuring-and-customizing-reports}

Om u te helpen de staat van uw instantie controleren en analyseren, verstrekt CQ een selectie van standaardrapporten, die voor uw individuele vereisten kunnen worden gevormd:

Zie de [Basisbeginselen van de aanpassing van rapporten](/help/sites-administering/reporting.md#the-basics-of-report-customization) voor nadere bijzonderheden.

### E-mailmelding configureren {#configuring-email-notification}

CQ stuurt e-mailmeldingen naar gebruikers die:

* Hebt u zich op paginagebeurtenissen geabonneerd, bijvoorbeeld aanpassing of replicatie.
* Hebt u zich geabonneerd op forumgebeurtenissen.
* Een stap in een werkstroom uitvoeren.

Zie [E-mailmelding configureren](/help/sites-administering/notification.md) voor nadere bijzonderheden.

### Paginaafdrukken inschakelen {#enabling-page-impressions}

Paginaafbeeldingen worden weergegeven in het dialoogvenster **Impressies** kolom van de klassieke UI-sitadmin-console. Om het vangen van paginamonpressies toe te laten moet u vormen:

* Op de publicatie-instantie:

   * [Dag CQ WCM Pagina Statistieken](/help/sites-deploying/osgi-configuration-settings.md)

* In de instantie van de auteur:

   * [Adobe-paginamruitingen, overtreklijn](/help/sites-deploying/osgi-configuration-settings.md)

>[!CAUTION]
>
>Bij de configuratie van Adobe Page Impressions Tracker in de auteursomgeving zijn anonieme aanvragen voor de volgende service mogelijk.
