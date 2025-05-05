---
title: Basisconfiguratieconcepten
description: Leer hoe u Adobe Experience Manager configureert voor uw eigen specifieke vereisten.
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: configuring
content-type: reference
feature: Configuring
exl-id: 3777a1ba-cc4e-41b9-9098-236f8141925f
solution: Experience Manager, Experience Manager Sites
role: Admin
source-git-commit: 48d12388d4707e61117116ca7eb533cea8c7ef34
workflow-type: tm+mt
source-wordcount: '2093'
ht-degree: 0%

---

# Basisconfiguratieconcepten{#basic-configuration-concepts}

Adobe Experience Manager (AEM) wordt geïnstalleerd met standaardinstellingen voor alle parameters die het mogelijk maken &#39;out-of-the-box&#39; uit te voeren. Nochtans, kunt u AEM voor uw eigen specifieke vereisten vormen.

Er zijn vele aspecten van AEM die kunnen worden gevormd:

* Sommige zijn [ algemeen gevormd voor elke projectinstallatie ](#primary-configuration-considerations) en moeten worden herzien om te bevestigen of zij op uw project van toepassing zijn.
* [ de verdere configuraties ](#further-configuration-considerations) kunnen gemeenschappelijk maar niet noodzakelijk zijn; met betrekking tot eigenschappen, of systeemprestaties en stabiliteit.
* Andere functies zijn alleen vereist voor bepaalde optionele functies van AEM (deze worden samen met de desbetreffende functie beschreven).

Afhankelijk van de specifieke configuratie, kunnen deze veranderingen worden aangebracht door of te gebruiken:

* **de Console van het Web van Adobe CQ**

  Dit is een standaardplaats voor het vormen van bundels OSGi en de diensten.

  Zie [ Vormend OSGi ](/help/sites-deploying/configuring-osgi.md) voor verdere details en geadviseerde praktijken.

* **Bewaarplaats**

  Een ondergroep van configuraties OSGi is beschikbaar in de bewaarplaats. Dit zorgt ervoor dat het kopiëren, of het repliceren, de inhoud van de bewaarplaats identieke configuraties ontspannen. U kunt ook uw eigen configuraties, afhankelijk van de uitvoeringsmodus, aan de opslagplaats toevoegen.

  Zie {Configuratie 0} OSGi in de Bewaarplaats [&#128279;](/help/sites-deploying/configuring-osgi.md#osgi-configuration-in-the-repository) en in het bijzonder [ Toevoegend een Nieuwe Configuratie aan de Bewaarplaats ](/help/sites-deploying/configuring-osgi.md#adding-a-new-configuration-to-the-repository) voor verdere details.

* **systeem van het Dossier**

  Enkele configuratiebestanden bevinden zich in het bestandssysteem.

* **AEM WCM**

  Diverse aspecten kunnen binnen AEM WCM zelf, velen worden gevormd gebruikend de [ console van Hulpmiddelen ](/help/sites-administering/tools-consoles.md); bijvoorbeeld, replicatieagenten.

>[!NOTE]
>
>Wanneer het werken met Adobe Experience Manager, zijn er verscheidene methodes om de configuratiemontages voor de diensten OSGi (console of bewaargegevensknooppunten) te beheren.
>
>Zie [ Vormend OSGi ](/help/sites-deploying/configuring-osgi.md) voor volledige details.

>[!NOTE]
>
>Het configureren van AEM is eenvoudig. Bepaalde wijzigingen kunnen echter grote gevolgen hebben voor de toepassingen. Om deze reden, verzeker u de noodzakelijke ervaring en de kennis alvorens u begint AEM te vormen, en slechts de veranderingen aan te brengen die u weet worden vereist. Om het even welke veranderingen die via de console OSGi worden aangebracht zijn **onmiddellijk** toegepast op het lopende systeem (geen nieuw begin wordt vereist).

## Primaire overwegingen met betrekking tot configuratie {#primary-configuration-considerations}

Deze lijst detailleert de primaire gebieden die algemeen voor elk nieuw project worden gevormd. Niet alles is nodig, maar de lijst moet gelezen en herzien worden om te zien wat op uw project van toepassing is.

De lijst geeft een kort overzicht van elk configuratieaspect, samen met verbindingen aan de pagina&#39;s die volledige details verstrekken.

### Beveiligingscontrolelijst {#security-checklist}

Verscheidene zeer belangrijke configuratiekwesties worden vermeld in [ Controlelijst van de Veiligheid ](/help/sites-administering/security-checklist.md). Zorg ervoor dat u dit leest en neem de benodigde actie voor de installatie.

### De standaardinterface configureren - geoptimaliseerd voor aanraakgebruik of Klassiek {#configuring-the-default-ui-touch-optimized-or-classic}

Er zijn twee UIs beschikbaar voor gebruik in AEM:

* De interface met aanraakfuncties
* De klassieke gebruikersinterface

U kunt UI vormen u het gebruiken van [ Toewijzing van de Wortel ](/help/sites-deploying/osgi-configuration-settings.md) vereist.

>[!NOTE]
>
>De verdere informatie over het selecteren van UI is beschikbaar onder [ Selecterend uw UI ](/help/sites-authoring/select-ui.md).

### IPv4 en IPv6 {#ipv-and-ipv}

Alle elementen van AEM (bijvoorbeeld de opslagplaats en de Dispatcher) kunnen in zowel IPv4- als IPv6-netwerken worden geïnstalleerd.

De verrichting is naadloos aangezien geen speciale configuratie wordt vereist, wanneer nodig kunt u een IP adres eenvoudig specificeren gebruikend het formaat dat aan uw netwerktype aangewezen is.

Dit betekent dat wanneer een IP adres moet worden gespecificeerd u (zoals vereist) van kunt selecteren:

* een IPv6-adres

  bijvoorbeeld, `https://[ab12::34c5:6d7:8e90:1234]:4502`

* een IPv4-adres

  bijvoorbeeld, `https://123.1.1.4:4502`

* een servernaam

  bijvoorbeeld, `https://www.yourserver.com:4502`

* Het standaardgeval van `localhost` wordt geïnterpreteerd voor zowel IPv4- als IPv6-netwerkinstallaties

  bijvoorbeeld, `http://localhost:4502`

### Versie leegmaken {#version-purging}

AEM maakt in een standaardinstallatie een versie van een pagina of knooppunt wanneer u een pagina activeert (nadat u de inhoud hebt bijgewerkt). U kunt extra versies op verzoek ook tot stand brengen gebruikend het **Versioning** lusje van sidekick. Al deze versies worden opgeslagen in de opslagplaats en kunnen, indien nodig, worden hersteld.

Deze versies worden nooit gewist, zodat de grootte van de opslagplaats in tijd groeit en daarom moet worden beheerd.

Zie [&#128279;](/help/sites-deploying/version-purging.md) het Schrappen van de Versie 1&rbrace; voor volledige details, in het bijzonder [ Manager van de Versie ](/help/sites-deploying/version-purging.md#version-manager) voor details van hoe te om AEM te vormen om oudere versies te zuiveren wanneer een nieuwe versie wordt gecreeerd.

### Logboekregistratie {#logging}

AEM biedt u de mogelijkheid om te vormen:

* globale parameters voor de centrale houtkapdienst
* verzoek gegevensregistreren; een gespecialiseerde registrerenconfiguratie voor verzoekinformatie
* specifieke instellingen voor de afzonderlijke services, bijvoorbeeld een afzonderlijk logbestand en een indeling voor de logberichten

Zie [ het Registreren ](/help/sites-deploying/configure-logging.md) voor volledige details.

### Modi uitvoeren {#run-modes}

Met uitvoeringsmodi kunt u de AEM voor een bepaald doel afstemmen. Bijvoorbeeld, auteur of publiceer, test, ontwikkeling, of Intranet, etc.

Dit wordt gedaan door inzamelingen van configuratieparameters voor elke looppaswijze te bepalen. Een basisreeks configuratieparameters wordt toegepast voor alle looppaswijzen, kunt u extra reeksen aan het doel van uw specifiek milieu dan stemmen. Deze worden vervolgens naar wens toegepast.

Alle configuratiemontages worden opgeslagen in één bewaarplaats en door de **Wijze van de Looppas** te plaatsen geactiveerd.

Zie [ Wijzen van de Looppas ](/help/sites-deploying/configure-runmodes.md) voor volledige details.

### Single Sign On {#single-sign-on}

Met Single Sign On (SSO) heeft een gebruiker toegang tot meerdere systemen nadat hij de verificatiegegevens (zoals een gebruikersnaam en wachtwoord) eenmaal heeft opgegeven. Een afzonderlijk systeem (dat als vertrouwde op authentiek wordt bekend) voert de authentificatie uit en verstrekt Experience Manager de gebruikersgeloofsbrieven. De Experience Manager controleert en dwingt de toegangstoestemmingen voor de gebruiker (namelijk bepaalt welke middelen de gebruiker wordt toegestaan om toegang te hebben) af.

Zie [ Enig Teken ](/help/sites-deploying/single-sign-on.md) voor verdere details.

### Brontoewijzing {#resource-mapping}

De afbeelding van het middel wordt gebruikt om omleidingen, ijdelheid URLs, en virtuele gastheren voor AEM te bepalen.

U kunt bijvoorbeeld de volgende toewijzingen gebruiken:

* Plaats een voorvoegsel voor alle aanvragen bij `/content` , zodat de interne structuur verborgen is voor de bezoekers van uw website.
* Definieer een omleiding zodat alle aanvragen naar de pagina `/content/en/gateway` van uw website worden omgeleid naar `https://gbiv.com/` .

Zie [ Afbeelding van het Middel ](/help/sites-deploying/resource-mapping.md) voor verdere details.

### Replicatie-, reverse Replication- en Replication-agents {#replication-reverse-replication-and-replication-agents}

De agenten van de replicatie zijn centraal aan AEM als mechanisme dat wordt gebruikt om:

* [ Publish (activeer) ](/help/sites-authoring/publishing-pages.md) inhoud van een auteur aan publicatiemilieu.
* Inhoud expliciet uit de Dispatcher-cache verwijderen.
* Hiermee wordt gebruikersinvoer (bijvoorbeeld formulierinvoer) vanuit de publicatieomgeving geretourneerd naar de auteursomgeving (onder controle van de auteursomgeving).

Voor meer details, zie [ Replicatie ](/help/sites-deploying/replication.md).

### OSGi-configuratie-instellingen {#osgi-configuration-settings}

[ OSGi ](https://www.osgi.org/) is een fundamenteel element in de technologiestapel van AEM. Het wordt gebruikt om de samengestelde bundels van AEM en hun configuratie te controleren.

Zie [ OSGi configuratiemontages ](/help/sites-deploying/osgi-configuration-settings.md) voor een lijst van de diverse bundels die voor projectimplementatie (vermeld volgens bundel) relevant zijn. Niet alle instellingen in de lijst hoeven te worden aangepast. Sommige instellingen worden vermeld om u te helpen begrijpen hoe AEM werkt.

Wanneer het werken met AEM, zijn er verscheidene methodes om de configuratiemontages voor dergelijke diensten te beheren; zie [ Vormend OSGi ](/help/sites-deploying/configuring-osgi.md) voor meer details en de geadviseerde praktijken.

### LDAP configureren {#configuring-ldap}

LDAP-verificatie is vereist voor verificatie van gebruikers die zijn opgeslagen in een (centrale) LDAP-directory, zoals Active Directory. Dit helpt de inspanning te verminderen die wordt vereist om gebruikersrekeningen te beheren.

LDAP-verificatie vindt plaats op het niveau van de gegevensopslagruimte, zodat deze rechtstreeks door de gegevensopslagruimte wordt afgehandeld. Voor verdere details, zie [ Vormend LDAP met AEM ](/help/sites-administering/ldap-config.md).

Voor gebruikersbeheer binnen AEM (met inbegrip van toewijzing van toegangsrechten), zie [ Beleid van de Gebruiker en Veiligheid ](/help/sites-administering/security.md).

### De Dispatcher configureren {#configuring-the-dispatcher}

Dispatcher is een Adobe Experience Manager-programma voor caching, taakverdeling of beide. Het kan met een onderneming-klasse Webserver worden gebruikt.

Zie [ Dispatcher ](https://experienceleague.adobe.com/docs/experience-manager-dispatcher/using/dispatcher.html) voor volledige details, in het bijzonder [ Vormend Dispatcher ](https://experienceleague.adobe.com/docs/experience-manager-dispatcher/using/configuring/dispatcher-configuration.html) voor verdere configuratiedetails.

### Configuratie van AEM LiveCycle-connector {#configuring-aem-livecycle-connector}

Met de versie van de AEM Doc Services en AEM Doc Security kan AEM nu de documentservices van het LiveCycle aanroepen om een XFA-formulier te genereren, een document om te zetten in PDF en een document te beschermen door beleid. Zie [ AEM de Schakelaar van het LiveCycle ](https://helpx.adobe.com/livecycle/help/aem/aem-livecycle-connector.html) voor meer details.

### Het Verschuiven van de baan en het Beleid van de Topologie {#job-offloading-and-topology-administration}

[ het Verschuiven ](/help/sites-deploying/offloading.md) verdeelt verwerkingstaken onder de instanties van de Experience Manager in een topologie. Met offloading kunt u specifieke instanties van Experience Managers gebruiken voor het uitvoeren van specifieke typen verwerking. Met gespecialiseerde verwerking kunt u het gebruik van beschikbare serverbronnen maximaliseren.

De technologieën zijn losjes verbonden clusters van de Experience Manager die aan het ontladen deelnemen. Een cluster bestaat uit een of meer serverinstanties van de Experience Manager (één instantie wordt beschouwd als een cluster).

Voor meer informatie over hoe te om topologielidmaatschap te bekijken of te wijzigen, raadpleeg de [ Administering sectie van Topologieën ](/help/sites-deploying/offloading.md#administering-topologies).

### De welkomstconsole configureren {#configuring-the-welcome-console}

De welkomstconsole van de klassieke UI biedt een lijst met koppelingen naar de verschillende consoles en functionaliteit binnen AEM.

Het is mogelijk om de verbindingen te vormen die zichtbaar zijn, zie [ Vormend de Welkome Console ](/help/sites-developing/customizing-the-welcome-console.md) voor verdere details.

### Configureren voor prestaties {#configuring-for-performance}

[ Prestaties ](/help/sites-deploying/configuring-performance.md) is zeer belangrijk aan uw project. Bepaalde aspecten van AEM (en/of de onderliggende opslagplaats) kunnen worden geconfigureerd om de prestaties te optimaliseren.

Zie [ Vormend voor Prestaties ](/help/sites-deploying/configuring-performance.md#configuring-for-performance) voor verdere details.

<!--delete ### Scaling {#scaling}

Scaling a CQ installation correctly depends greatly on the details of your particular use case. A detailed discussion of solution patterns for various situations can be found in [Scaling CQ](/help/sites-deploying/scaling.md).-->

### Gedeelde gegevensopslag {#shared-data-store}

De gegevensopslagplaats van de opslagplaats wordt gebruikt om de opslag van grote binaire bestanden van de opslagplaats zelf naar een afzonderlijk gebied te offloaden, zodat meerdere instanties van hetzelfde binaire (bijvoorbeeld een afbeelding) binnen de opslagplaats slechts eenmaal worden opgeslagen.

Deze &quot;store-once, reference-many-times&quot;eigenschap kan worden uitgebreid om niet alleen één enkele opslagplaats maar volledig afzonderlijke bewaarplaatsen te dienen, door de gegevensopslag van elk te vormen om naar de zelfde gedeelde plaats van het dossiersysteem te verwijzen.

Een dergelijke gegevensopslag kan worden gedeeld tussen verschillende knooppunten in dezelfde cluster, verschillende publicatie- en/of auteurinstanties in dezelfde installatie of zelfs geheel afzonderlijke instanties in verschillende installaties.

Voor meer informatie, zie [ het Vormen de Opslag van Gegevens en de Opslag van de Knoop ](/help/sites-deploying/data-store-config.md).

## Meer configuratieoverwegingen {#further-configuration-considerations}

### HTTP inschakelen via SSL {#enabling-http-over-ssl}

U kunt HTTP via SSL inschakelen om veiligere verbindingen met uw servers te gebruiken.

Zie [ toelatend HTTP over SSL ](/help/sites-administering/ssl-by-default.md) voor verdere details.

### AEM en portlets {#aem-portals-and-portlets}

Een portal is een webtoepassing die verpersoonlijking, eenmalige aanmelding, integratie van inhoud uit verschillende bronnen biedt en de presentatielaag van informatiesystemen host. Met de portletcomponent kunt u ook een portlet op de pagina insluiten. Als u toegang wilt krijgen tot inhoud van de CQ5 WCM, kan de portalserver worden uitgerust met de CQ5 Portal Director Portlet. U kunt dit doen door portlet te installeren, te vormen en toe te voegen aan de portlet pagina.

Zie [ Portaal en Portlets ](/help/sites-administering/aem-as-portal.md) voor verdere details.

### Verlopen van statische objecten {#expiration-of-static-objects}

Statische objecten (bijvoorbeeld pictogrammen) veranderen niet. Daarom moet het systeem zo worden geconfigureerd dat zij niet verlopen (voor een redelijke periode) en zo onnodig verkeer verminderen.

Zie [ Vervalsing van Statische Voorwerpen ](/help/sites-deploying/expiration-static-objects.md) voor verdere details.

### FI&#39;s openen in het Java™-proces {#open-files-in-the-java-process}

Elk Java™-proces heeft mogelijk toegang tot bestanden - hiervoor zijn systeembronnen vereist. Daarom wordt een bovengrens gedefinieerd voor het aantal bestanden dat elk proces gelijktijdig mag openen. Als dit wordt overschreden, kan een uitzonderingsfout voorkomen.

Als het AEM dit maximum overschrijdt, wordt het bericht &quot; `too many open files`&quot; weergegeven in `error.log` .

Ga als volgt te werk om dergelijke uitzonderingen te voorkomen:

1. Controleer hoeveel geopende bestanden uw AEM gebruikt.

   Deze controle is afhankelijk van het platform waarop de instantie wordt uitgevoerd. Hulpprogramma&#39;s zoals de Server (UNIX®) of de Verkenner van het Proces (Vensters) kunnen worden gebruikt.

   Deze waarde moet tijdens de ontwikkeling en het testen worden gecontroleerd op:

   * bevestigen dat bestanden naar wens worden gesloten
   * om de vereiste maximumwaarde te bepalen (onder verschillende omstandigheden)

1. Stel het toegestane maximum in.

   De nieuwe waarde moet rekening houden met zowel de huidige als de toekomstige behoeften, zodat het raadzaam is de huidige behoeften te verdubbelen.

   `serverctl` configureert `CQ_MAX_OPEN_FILES` to `8192` standaard. Dit is voldoende voor de meeste scenario&#39;s.

### De Rich Text Editor configureren {#configuring-the-rich-text-editor}

De **Rijke Redacteur van de Tekst** (**RTE**) voorziet auteurs van een brede waaier van [ functionaliteit ](/help/sites-authoring/rich-text-editor.md) voor het uitgeven van hun tekstuele inhoud; het verstrekken van hen van pictogrammen, selectiekaders, en menu&#39;s voor een ervaring WYSIWYG.

Zie [ Vormend de Rijke Redacteur van de Tekst ](/help/sites-administering/rich-text-editor.md) voor verdere details.

### Ongedaan maken configureren voor paginabewerking {#configuring-undo-for-page-editing}

Er zijn diverse eigenschappen die het gedrag bepalen van de opdrachten Ongedaan maken en Opnieuw voor het bewerken van pagina&#39;s. Deze kunnen worden gevormd, zie [ Vormend ongedaan maken voor het uitgeven van de Pagina ](/help/sites-administering/config-undo.md) voor verdere details.

### De videocomponent configureren {#configuring-the-video-component}

De [ component Video ](/help/sites-authoring/default-components-foundation.md#video) laat u een vooraf bepaald, uit-van-de-doos videoelement op uw pagina plaatsen.

Voor juiste het transcoderen om voor te komen, moet uw beheerder [ Mpeg ](/help/sites-administering/config-video.md#install-ffmpeg) afzonderlijk installeren. Zij kunnen ook [ uw Videoprofielen ](/help/sites-administering/config-video.md#configure-video-profiles) voor gebruik met html5 elementen vormen.

### Rapporten configureren en aanpassen {#configuring-and-customizing-reports}

Om u te helpen de staat van uw instantie controleren en analyseren, verstrekt CQ een selectie van standaardrapporten, die voor uw individuele vereisten kunnen worden gevormd:

Zie de [ Grondbeginselen van de Aanpassing van het Rapport ](/help/sites-administering/reporting.md#the-basics-of-report-customization) voor verdere details.

### E-mailmelding configureren {#configuring-email-notification}

CQ stuurt e-mailmeldingen naar gebruikers die:

* Hebt u zich op paginagebeurtenissen geabonneerd, bijvoorbeeld, wijziging of replicatie.
* Hebt u zich geabonneerd op forumgebeurtenissen.
* Een stap in een werkstroom uitvoeren.

Zie [ Vormend E-mailBericht ](/help/sites-administering/notification.md) voor verdere details.

### Paginaafdrukken inschakelen {#enabling-page-impressions}

De impressies van de pagina worden getoond in de **1&rbrace; kolom van Impressies &lbrace;van de klassieke console van UI plaatsadmin.** U kunt als volgt het vastleggen van pagina-afdrukken inschakelen:

* Op de publicatie-instantie:

   * [Dag CQ WCM Pagina Statistieken](/help/sites-deploying/osgi-configuration-settings.md)

* In de auteurinstantie:

   * [Adobe van pagina-importbeheer](/help/sites-deploying/osgi-configuration-settings.md)

>[!CAUTION]
>
>De configuratie van de Traceur van de Indruk van de Pagina van de Adobe op het auteursmilieu staat anonieme verzoeken aan de volgende dienst toe.
