---
title: OSGi-configuratie-instellingen
seo-title: OSGi-configuratie-instellingen
description: Dit artikel detailleert de OSGi configuratiemontages (die volgens bundel worden vermeld) die voor projectimplementatie relevant zijn. De lijst dient als richtsnoer en is niet limitatief.
seo-description: Dit artikel detailleert de OSGi configuratiemontages (die volgens bundel worden vermeld) die voor projectimplementatie relevant zijn. De lijst dient als richtsnoer en is niet limitatief.
uuid: 192d3287-ec99-403b-bab0-45721e4e3abd
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: configuring
content-type: reference
discoiquuid: ed3a858c-7a43-4515-a2ff-43ca465c7d7d
docset: aem65
feature: Configureren
exl-id: 19eedcf2-140a-452d-aa8f-6fd7f219e5f8
source-git-commit: ca66c0655bcd878644e275fc8f7a41b38110beae
workflow-type: tm+mt
source-wordcount: '3561'
ht-degree: 0%

---

# OSGi-configuratie-instellingen{#osgi-configuration-settings}

[](https://www.osgi.org/) OSGiis een fundamenteel element in de technologiestapel van AEM. Het wordt gebruikt om de samengestelde bundels van AEM en hun configuratie te controleren.

OSGi &quot;*verstrekt de gestandaardiseerde primitieven die toepassingen toestaan om van kleine, herbruikbare en samenwerkende componenten worden geconstrueerd. Deze componenten kunnen in een toepassing worden samengesteld en worden opgesteld*&quot;.

Hierdoor kunt u eenvoudig bundels beheren, aangezien deze kunnen worden gestopt, geïnstalleerd en afzonderlijk kunnen worden gestart. De onderlinge afhankelijkheden worden automatisch verwerkt. Elke Component OSGi (zie [OSGi Specification](https://www.osgi.org/Specifications/HomePage)) is bevat in één van de diverse bundels. Bij AEM zijn er verschillende methoden om de configuratie-instellingen voor dergelijke bundels te beheren. zie [Het vormen OSGi](/help/sites-deploying/configuring-osgi.md) voor meer details en de geadviseerde praktijken.

De volgende OSGi configuratiemontages (die volgens bundel worden vermeld) zijn relevant voor projectimplementatie. Niet alle instellingen in de lijst hoeven te worden aangepast. Sommige instellingen worden vermeld om u te helpen begrijpen hoe AEM werkt.

>[!CAUTION]
>
>De lijst is bedoeld als richtsnoer en is niet limitatief. Niet alle bundels worden vermeld, noch alle parameters voor sommige bundels die zijn.
>
>De noodzakelijke configuratie zal van project tot project variëren.
>
>Gelieve te zien de console van het Web voor gebruikte waarden en gedetailleerde informatie over parameters.

>[!NOTE]
>
>Het hulpmiddel van Diff van de Configuratie OSGi, een deel van [AEM Tools](https://helpx.adobe.com/experience-manager/kb/tools/aem-tools.html), kan worden gebruikt om van de standaardOSGi configuraties een lijst te maken.

>[!NOTE]
>
>Voor specifieke onderdelen van de functionaliteit binnen AEM kunnen aanvullende bundels nodig zijn. In deze gevallen vindt u configuratiegegevens op de pagina die betrekking heeft op de juiste functionaliteit.

**AEM Replication Event** ListenerConfigure:

* De **Run-modi**, waarin replicatiegebeurtenissen naar listeners worden gedistribueerd. Bijvoorbeeld, als bepaald als auteur, dan is dit het systeem dat de replicatie &quot;&quot;in werking zal stellen.

* De looppaswijze **publish** moet worden toegevoegd als de projectcode replicatiegebeurtenissen (omgekeerde replicatie) in publicatiemilieu verwerkt. Bijvoorbeeld wanneer de verzender wordt gebruikt om van het publicatiemilieu te spoelen of wanneer de standaardreplicatie aan andere publicatieinstanties voorkomt.

**AEM** listener voor wijziging opslagplaatsConfigureren:

* De **Paden**, locaties om te luisteren naar gebeurtenissen in de opslagplaats klaar voor distributie.

**CRX Sling Client** RepositoryToegang tot de onderliggende inhoudopslagplaats configureren.

* Het **Admin Wachtwoord** zou na installatie moeten worden veranderd om [veiligheid](/help/sites-administering/security-checklist.md) van uw instantie te verzekeren.
* Andere wijzigingen zouden niet nodig moeten zijn en er moet zorgvuldig op worden gelet dat ze de toegang tot de opslagplaats kunnen beïnvloeden.

**Wiki Mail** ServiceConfigureer de e-mailinstellingen voor e-mailberichten die door een wiki worden verzonden.

**Apache Felix OSGi Management** ConsoleConfigure:

* **Plugins**, de belangrijkste navigatie-items (consoleplug-ins) die beschikbaar zijn in de  **Apache Felix Web Management** Consoleas menu-items op hoofdniveau. Schakel een optie uit die u niet nodig hebt omdat voor elke optie ruimte en bronnen vereist zijn.

>[!CAUTION]
>
>Ben zeker om het volgende te vormen:
>
>**Gebruikersnaam** en  **wachtwoord**, de referenties voor toegang tot de Apache Felix Web Management Console zelf.
>Het wachtwoord moet na de eerste installatie worden gewijzigd om de [beveiliging](/help/sites-administering/security-checklist.md) van uw exemplaar te garanderen.

>[!NOTE]
>
>Deze configuratie moet worden gemaakt met de Felix Console zoals dat bij het opstarten nodig is - voordat de opslagplaats beschikbaar is.

**Apache Sling Customizable Request Data** LoggerConfigure:

* **De naam** en de  **Logboek** Formatteren van de registreermachine om de plaats en het formaat van verzoek en toegangsregistreren te vormen (gebrek:  `request.log`). Dit logbestand is van essentieel belang voor het analyseren van de prestaties of foutopsporingsfunctionaliteit in verband met de webketen.
Dit wordt gecombineerd met [Apache Sling Request Logger](#apacheslingrequestlogger).

Zie [AEM Logboekregistratie](/help/sites-deploying/configure-logging.md) en [Logboekregistratie](https://sling.apache.org/site/logging.html) voor meer informatie.

**Apache Sling Event Thread** PoolConfigure:

* **Min Pool** Sizeand  **Max Pool Size**, de grootte van de pool die wordt gebruikt om gebeurtenisdraden te houden.

* **De Grootte** van de rij, de maximumgrootte van de draadrij als de pool uitgeput is.
De aanbevolen waarde is `-1` omdat de wachtrij op onbeperkt wordt ingesteld. als een limiet wordt vastgesteld , kunnen verliezen optreden wanneer deze worden overschreden .

* Het veranderen van deze montages kan prestaties in scenario&#39;s met een hoog aantal gebeurtenissen helpen; bijvoorbeeld zwaar AEM DAM- of workflowgebruik.
* De waarden specifiek voor uw scenario zouden moeten worden bepaald gebruikend tests.
* Deze instellingen kunnen van invloed zijn op de prestaties van uw instantie. Wijzig deze instellingen dus niet zonder reden en met gepaste aandacht.

**Apache Sling GET** ServletConfigureer enkele aspecten van rendering:

* **Automatische** indexering om het renderen van mappen voor bladeren in- en uit te schakelen.
* **Hiermee kunt u standaarduitvoeringen inschakelen**  (of uitschakelen), zoals  **HTML**,  **Onbewerkte tekst**,  **** JSONof  **XML**.
U moet JSON niet uitschakelen.

>[!NOTE]
>
>Deze instelling wordt automatisch geconfigureerd voor productieinstanties als u AEM uitvoert in [Productie Ready Mode](/help/sites-administering/production-ready.md).

**Apache Sling Java Script** HandlerConfigureer instellingen voor de compilatie van .java-bestanden als scripts (servlets).

Bepaalde instellingen kunnen van invloed zijn op de prestaties. Deze instellingen moeten waar mogelijk worden uitgeschakeld, met name voor een productie-instantie.

* S **bron-VM** en **doel-VM**, definieert de JDK-versie als de JDK-versie die wordt gebruikt als de JVM voor de runtime

* voor productiegevallen:

   * uitschakelen **Foutopsporingsinfo genereren**

**Apache Sling JCR** InstallerDeze parameters hebben waarschijnlijk geen configuratie nodig, maar kunnen nuttig zijn om te weten wanneer het ontwikkelen of het zuiveren. De installatiemap(s) kan (kunnen) bijvoorbeeld handig zijn voor het in- en uitchecken of voor het maken van een pakket.

* **Naam van installatiemappen** regextenderen en  **Maximale diepte van installatiemappen**  - geef op waar en tot welke diepte opslagmappen worden gezocht naar bronnen die moeten worden geïnstalleerd. Wanneer een jokerteken wordt gebruikt (zoals in.*/install) alle geschikte overeenkomsten worden doorzocht, bijvoorbeeld `/libs/sling/install` en `/libs/cq/core/install`.

* **Zoekpad**, lijst met paden die in de installatie worden gezocht naar bronnen die moeten worden geïnstalleerd, samen met een getal dat de wegingsfactor voor dat pad aangeeft.

**Apache Sling Job Event** HandlerConfigureer parameters voor het beheren van taakplanning:

* **Herhaal interval**,  **Maximale pogingen**,  **Maximum Parallelle Banen**,  **bevestig wachttijd**, onder andere.

* Als u deze instellingen wijzigt, kunnen de prestaties in scenario&#39;s met een groot aantal taken worden verbeterd. Bijvoorbeeld, zwaar gebruik van AEM DAM en Workflows.
* De waarden specifiek voor uw scenario zouden moeten worden bepaald gebruikend tests.
* Wijzig deze instellingen niet zonder reden en pas na zorgvuldige afweging aan.

**Apache Sling JSP Script** HandlerConfigure prestaties relevante montages voor de JSP manuscriptmanager. Als u de prestaties wilt verbeteren, moet u deze zoveel mogelijk uitschakelen.

Met name voor productiegevallen:

* uitschakelen **Foutopsporingsinfo genereren**
* **Gegenereerde Java behouden** uitschakelen
* uitschakelen **Toegewezen inhoud**
* uitschakelen **Bronfragmenten weergeven**

>[!NOTE]
>
>Deze instelling wordt automatisch geconfigureerd voor productieinstanties als u AEM uitvoert in [Productie Ready Mode](/help/sites-administering/production-ready.md).

**Logboekconfiguratie Apache Sling-** configuratieConfigureren:

* **Logbestand** Leveland  **Log File**, om de locatie en het logniveau van de centrale logboekconfiguratie (error.log) te definiëren. Het niveau kan worden ingesteld op een van `DEBUG`, `INFO`, `WARN`, `ERROR` en `FATAL`.

* **Aantal logbestanden** en  **logbestandsdrempel** om de grootte en versierotatie van het logbestand te bepalen.

* **Het** Patroon van het bericht bepaalt het formaat van de logboekberichten.

Zie [AEM Logboekregistratie](/help/sites-deploying/configure-logging.md#global-logging) en [Logboekregistratie](https://sling.apache.org/site/logging.html) voor meer informatie.

**Configuratie van Apache Sling Logging Logger (fabrieksconfiguratie)** Configureren:

* **Logniveau**,  **logbestand** en  **berichtindeling** om details van het logbestand en berichten te definiëren.

* **** Loggerto-definitie van de categorie; bijvoorbeeld alleen log voor com.day.cq.

* Door **Factory Configurations** te gebruiken, kan om het even welk aantal extra configuraties worden toegevoegd om met de diverse vereiste logboekniveaus en categorieën rekening te houden.
* Dergelijke configuraties zijn nuttig tijdens de ontwikkeling; bijvoorbeeld om TRACE-berichten voor een specifieke service in een specifiek logbestand te registreren.
* Dergelijke configuraties zijn nuttig in een productieomgeving; bijvoorbeeld, om berichten over de specifieke dienst te hebben die aan een individueel logboekdossier voor gemakkelijkere controle wordt geregistreerd.

Zie [AEM Logboekregistratie](/help/sites-deploying/configure-logging.md) en [Logboekregistratie](https://sling.apache.org/site/logging.html) voor meer informatie.

**Configuratie van Apache Sling Logging Writer (fabrieksconfiguratie)** configureren:

* **Logbestand** om het bestaan van een logbestand te definiëren.
* **Aantal logbestanden** om de versierotatie te definiëren.

* De schrijver kan door een configuratie **Apache Sling Logging Logger Configuration** worden gebruikt.

* Dergelijke configuraties zijn nuttig tijdens de ontwikkeling; bijvoorbeeld om TRACE-berichten voor een specifieke service in een specifiek logbestand te registreren.
* Dergelijke configuraties zijn nuttig in een productieomgeving; bijvoorbeeld, om berichten over de specifieke dienst te hebben die aan een individueel logboekdossier voor gemakkelijkere controle wordt geregistreerd.

Zie [AEM Logboekregistratie](/help/sites-deploying/configure-logging.md) en [Logboekregistratie](https://sling.apache.org/site/logging.html) voor meer informatie.

**Apache Sling Main** ServletConfigure:

* **Aantal Vraag per** Vraag en  **Terugkerende** Depthet om uw systeem tegen oneindige recursie en bovenmatige manuscriptvraag te beschermen.

**Apache Sling MIME Type** ServiceConfigure:

* **MIME** Typesto voegt de vereiste waarden voor uw project toe aan het systeem. Hierdoor kan een `GET`-verzoek op een bestand de juiste header van het inhoudstype instellen voor het koppelen van het bestandstype en de toepassing.

**Apache Sling Reference** FilterTo behandelt bekende beveiligingsproblemen met CSRF-bestanden (Cross-Site Request Smeedery) in CRX WebDAV en Apache Sling. U moet het filter Referrer configureren.

De dienst van de verwijzingsfilter is de dienst OSGi die u toestaat om te vormen:

* welke http-methoden moeten worden gefilterd
* Geeft aan of een lege verwijzingskoptekst is toegestaan
* en een lijst met servers die naast de serverhost zijn toegestaan.

Zie [Beveiligingschecklist - Problemen met de zogeheten Cross-Site Request-vervalsing](/help/sites-administering/security-checklist.md#protect-against-cross-site-request-forgery) voor meer informatie.

>[!NOTE]
>
>Het filter Apache Sling Referrer is afhankelijk van de installatie van een snel reparatiepakket.

**Apache Sling Request** LoggerConfigure:

* diverse parameters om te bepalen hoe de verzoeken worden geregistreerd.
* **Schakel Aanvraaglogbestand** in of uit.

* **Schakel Toegangslogboek** in of uit.

Dit wordt gecombineerd met het [Aanpasbare Apache Sling Request Data Logger](#apacheslingcustomizablerequestdatalogger).

Zie [AEM Logboekregistratie](/help/sites-deploying/configure-logging.md) en [Logboekregistratie](https://sling.apache.org/site/logging.html) voor meer informatie.

**Apache Sling Resource Resolver** FactoryConfigureer centrale aspecten van de oplossing van verkoopbronnen:

* **Zoekpad**(en) voor bronnen toevoegen, specifieke paden voor projecten toevoegen (maar niet verwijderen  `/libs` of  `/apps`).

* **Virtuele** URLstv om uw vanity URL-toewijzingen te bepalen.

* **URL-** toewijzingen om aliassen te definiëren; bijvoorbeeld van  `/content` tot  `/`.

* **Toewijzingslocatie**, de mapconfiguratie extern geïmplementeerd in  `/etc/map`.

* Gebruik uw lokale installatie (bijvoorbeeld, gebruik `https://localhost:4502/system/console/jcrresolver`) om te bepalen welke Resolver van het Middel actief is.

Zie voor meer informatie: [https://cwiki.apache.org/confluence/display/SLING/Flexible+Resource+Resolution](https://cwiki.apache.org/confluence/display/SLING/Flexible+Resource+Resolution).

>[!CAUTION]
>
>Deze opties moeten met name in de opslagplaats worden geconfigureerd.
>
>Anders zouden de veranderingen die aan **URL Mappings** gebruikend de console van Felix worden aangebracht door AEM bij de volgende opstarten kunnen worden beschreven.

**Apache Sling Servlet/Script Resolver en Error** HandlerDe Sling Servlet en de Oplossen van het Manuscript hebben veelvoudige taken:

1. Het wordt gebruikt als `ServletResolver` om de Servlet of het Manuscript te selecteren om te roepen om het verzoek te behandelen.

1. Het werkt als `SlingScriptResolver`.

1. Het beheert fout behandeling door de `ErrorHandler` interface uit te voeren die het zelfde algoritme gebruikt om fout behandelende servers en manuscripten te selecteren zoals wordt gebruikt om verzoekverwerkingsservlets en manuscripten op te lossen.

Er kunnen verschillende parameters worden ingesteld, waaronder:

* **Met Uitvoering** worden de paden getransformeerd die moeten worden gezocht naar uitvoerbare scripts. door specifieke paden te configureren kunt u beperken welke scripts kunnen worden uitgevoerd. Als geen weg dan wordt gevormd wordt het gebrek gebruikt ( `/` = wortel), staat dit de uitvoering van alle manuscripten toe.
Als een gevormde wegwaarde met een schuine streep beëindigt, wordt de volledige subboom gezocht. Zonder een dergelijke slash wordt het script alleen uitgevoerd als het exact overeenkomt.

* **Scriptgebruiker**  - deze optionele eigenschap kan de gegevensopslaggebruikersaccount opgeven die wordt gebruikt voor het lezen van de scripts. Als er geen account is opgegeven, wordt de `admin`-gebruiker standaard gebruikt.

* **Standaardextensies:** de lijst met extensies waarvoor het standaardgedrag wordt gebruikt. Dit betekent dat het laatste wegsegment van het middeltype als manuscriptnaam kan worden gebruikt.

**Day Commons GFX Font** HelperBij het renderen van afbeeldingen kunt u DrawText gebruiken om tekst in te sluiten. Hiervoor kunt u ook uw eigen lettertypen installeren:

* Definieer het **Fontpad** dat moet worden doorzocht naar projectspecifieke lettertypen.
Bijvoorbeeld, `/apps/myapp/fonts`.

**Apache HTTP Components Proxy** ConfigurationProxy-configuratie voor alle code die de Apache HTTP-client gebruikt, wordt gebruikt wanneer een HTTP-bestand wordt gemaakt. bijvoorbeeld bij replicatie.

Wanneer het creëren van een nieuwe configuratie, breng geen veranderingen in de fabrieksconfiguratie aan maar creeer in plaats daarvan een nieuwe fabrieksconfiguratie voor deze component gebruikend de hier beschikbare configuratiemanager: **https://localhost:4502/system/console/configMgr/**. De proxyconfiguratie is beschikbaar in **org.apache.http.proxyconfigurator.**

>[!NOTE]
>
>In AEM 6.0 en vroegere versies werd de volmacht gevormd in de Cliënt van HTTP van de Kommunnen van de Dag. Vanaf AEM 6.1 en later versies is de proxyconfiguratie verplaatst naar de &quot;Apache HTTP Components Proxy Configuration&quot; in plaats van de &#39;Day Commons HTTP Client&#39;-configuratie.

**Dag CQ** AntispamConfigureer de gebruikte anti-spamservice (Akismet). Hiervoor moet u het volgende registreren:

* **Provider**
* **API-sleutel**
* **Geregistreerde URL**

**Adobe granite HTML Library** ManagerConfigureer dit om de verwerking van clientbibliotheken (css of js) te beheren; bijvoorbeeld hoe de onderliggende structuur wordt gezien.

* Voor productiegevallen:

   * Schakel **Minify** in (om CRLF- en spatietekens te verwijderen).
   * Schakel **Gzip** in (om bestanden in staat te stellen om te worden gecomprimeerd en geopend met één aanvraag).
   * uitschakelen **Foutopsporing**
   * **Timing** uitschakelen

* Voor JS-ontwikkeling (vooral bij foutopsporing/foutopsporing):

   * uitschakelen **Minify**
   * Schakel **Foutopsporing** in om de bestanden te scheiden voor foutopsporing en gebruik met firebug.
   * **Timing** inschakelen in geval van interesse in timing.
   * Schakel **Debug**-console in om logboekberichten voor de JS-console weer te geven.

>[!CAUTION]
>
>Wanneer u de instelling voor **Minify** of **Gzip** wijzigt, moet u ook de inhoud van `/var/clientlibs` verwijderen. Dit is een cacheversie van de clientlibs die op verzoek opnieuw wordt samengesteld.

>[!NOTE]
>
>Deze instelling wordt automatisch geconfigureerd voor productieinstanties als u AEM uitvoert in [Productie Ready Mode](/help/sites-administering/production-ready.md).

**De** montages van de Authentificatie HandlerSystem van de Kopbal van dag CQ HTTP voor de basisauthentificatiemethode van het HTTP- verzoek.

Wanneer u [gesloten gebruikersgroepen](/help/sites-administering/cug.md) gebruikt, kunt u (onder andere) het volgende configureren:

* **HTTP Realm**
* De **Standaardaanmeldingspagina**

**Day CQ Link Checker** ServiceCheck en indien nodig configureren:

* **Planner** Periodto definieert het interval waarmee externe koppelingen automatisch moeten worden gecontroleerd.

* Controleer **Onjuist Interval van de Tolerantie van de Verbinding** voor de periode waarna een onsuccesvolle externe verbinding als slecht wordt beschouwd.
* **Koppelingcontrole Patronen** overschrijven om paden te definiëren die van koppelingencontrole moeten worden uitgesloten.

**De Controle van de Verbinding van CQ van de dag** TaskConfigure montages voor één enkele taak van de verbindingscontrole (een taak die een externe verbinding controleert):

* Controleer de intervallen die zijn gedefinieerd in **Good Link Test Interval** en **Bad Link Test Interval**

* De verschillende parameters met betrekking tot proxy&#39;s voor internettoegang en NTLM die nodig zijn voor externe toegang bij het controleren van een koppeling.

**CQ-mailservice** op de dagConfigureer hostnaam en toegangsgegevens voor de mailserver. Gelieve te verwijzen naar het Vormen de sectie van de Dienst van de Post.

**Dag CQ MCM-** nieuwsbriefConfigureer de verschillende instellingen die worden gebruikt met de nieuwsbrief.

**Uur CQ-** hoofdtoewijzingConfigureren:

* **Doelpad** bepaalt waar een aanvraag naar &quot;  `/`&quot; wordt omgeleid.

Er zijn twee UIs beschikbaar in AEM:

* de interface met aanraakbediening is de standaardinterface
* en de vervangen klassieke interface nog volledig operationeel is

Met AEM hoofdmaptoewijzing kunt u de interface configureren die u als standaard voor uw instantie wilt gebruiken:

* Als u de interface met aanraakbediening als de standaardinterface wilt gebruiken, moet **Doelpad** naar het volgende verwijzen:

   ```
      /projects.html
   ```

* Om klassieke UI als gebrek UI te hebben **zou de Weg van het Doel** moeten richten aan:

   ```
      /welcome.html
   ```

>[!NOTE]
>
>Op een standaardinstallatie is de interface met aanraakoptimalisatie de standaardinterface.

**Adobe granite SSO Authentication** HandlerConfigure Single Sign On (SSO) details; Deze zijn vaak nodig in instellingen van de ondernemingsauteur, vaak in combinatie met LDAP.

Er zijn verschillende configuratie-eigenschappen beschikbaar:

* ****
PathPath waarvoor deze authentificatiemanager actief is. Als deze parameter leeg wordt gelaten, is de authentificatiemanager gehandicapt. Het pad/zorgt er bijvoorbeeld voor dat de verificatiehandler wordt gebruikt voor de gehele gegevensopslagruimte.

* **Service**
RankingOSGi Framework Service Ranking value wordt gebruikt om de volgorde aan te geven die wordt gebruikt om deze service aan te roepen. Dit is een 
`int` waarde waarbij hogere waarden een hogere prioriteit aangeven.
De standaardwaarde is `0`.

* **Namen**
van koptekstDe naam of namen van kopteksten die een gebruikers-id kunnen bevatten.

* **Cookie-**
namenDe naam of namen van cookies die een gebruikers-id kunnen bevatten.

* **ParameternamenDe**
naam of namen van aanvraagparameters die de gebruikersnaam kunnen bevatten.

* **User**
MapFor selected users, the user name extracted from the HTTP request can be replace with a different one in the credentials object. De toewijzing wordt hier gedefinieerd. Als de gebruikersnaam 
`admin` aan beide zijden van de kaart wordt de toewijzing genegeerd. Houd er rekening mee dat het teken &quot;=&quot; moet worden voorafgegaan door &quot;\&quot;.

* ****
FormatGeeft de indeling aan waarin de gebruikers-id wordt opgegeven. Gebruiken:

   * `Basic` als de gebruikers-id is gecodeerd in de indeling HTTP Basic Authentication
   * `AsIs` als de gebruiker-id wordt opgegeven in onbewerkte tekst of als een toegepaste waarde voor een reguliere expressie moet worden gebruikt zoals deze is of een reguliere expressie

**CQ-foutopsporingsfilter van de dag (WCM)** Dit is handig bij het ontwikkelen omdat achtervoegsels zoals ?debug=layout kunnen worden gebruikt bij het openen van een pagina. Bijvoorbeeld, zal https://localhost:4502/cf#/content/geometrixx/en/support.html?debug=layout lay-outinformatie verstrekken die van belang voor de ontwikkelaar kan zijn.

* Schakel deze optie uit op productieexemplaren om prestaties en beveiliging te garanderen.

**Dag CQ WCM-** filterConfigureren:

* **WCM-modus **om de standaardmodus te definiëren.
* Voor een auteurinstantie zou dit `edit`, `disable,preview` of `analytics` kunnen zijn.
De andere modi zijn toegankelijk vanaf het zijpaneel of het achtervoegsel `?wcmmode=disabled` kan worden gebruikt om een productieomgeving te emuleren.

* Op een publicatie-instantie moet dit worden ingesteld op `disabled` om ervoor te zorgen dat geen andere modus toegankelijk is.

>[!NOTE]
>
>Deze instelling wordt automatisch geconfigureerd voor productieinstanties als u AEM uitvoert in [Productie Ready Mode](/help/sites-administering/production-ready.md).

**Day CQ WCM Link Checker** ConfiguratorConfigurator:

* **Lijst met herschrijfconfiguraties** om een lijst met locaties voor op inhoud gebaseerde koppelingencontroleerconfiguraties op te geven. De configuraties kunnen op runtime wijze worden gebaseerd; dit is belangrijk om onderscheid te maken tussen auteur- en publicatieomgevingen, omdat de instellingen voor koppelingencontrole kunnen verschillen.

**Day CQ WCM Page** ProcessorConfigureren:

* **Paden**, een lijst met locaties waar het systeem luistert naar paginawijzigingen voordat een wijziging wordt geactiveerd  `jcr:Event`.

**Adobe Page Impressions** TrackerVoor een auteurinstantie configureert u:

* **sling.auth.requirements**: Stel de waarde van deze eigenschap in op  `-/libs/wcm/stats/tracker`

>[!CAUTION]
>
>Deze configuratie zal anonieme verzoeken aan de volgende dienst toestaan.

>[!NOTE]
>
>Zie [Paginafdruk](/help/sites-deploying/configuring.md#enabling-page-impressions) voor meer informatie.

**CQ-** paginatiestatistieken op dagVoor een publicatieinstantie configureert u:

* **URL om** gegevens te verzenden vormt URL die wordt gebruikt om paginatistieken te volgen (is essentieel als een trackerverzoek door de verzender gaat); De standaardwaarde is bijvoorbeeld  `https://localhost:4502/libs/wcm/stats/tracker`.

* **Het volgen script** is ingeschakeld om het opnemen van het volgende script op de pagina&#39;s in te schakelen ( `true`) of uit te schakelen ( `false`). De standaardwaarde is `false`.

>[!NOTE]
>
>Zie [Paginafdruk](/help/sites-deploying/configuring.md#enabling-page-impressions) voor meer informatie.

**Day CQ WCM Version** ManagerBesturing als en hoe versies in uw systeem worden beheerd:

* **Versie maken bij activering**, ingeschakeld in een standaardinstallatie
* **Leegmaken inschakelen**

* **Paden** wissen, de paden die met een zoekactie worden doorzocht
* **Impliciete versioning-paden**, de paden waar impliciete versioning actief is.

* **Maximale versieleeftijd**, de maximumleeftijd (in dagen) van een versie

* **Max. aantal versies**, het maximumaantal versies dat behouden moet blijven

Zie [Versieopruiming](/help/sites-deploying/version-purging.md) voor meer informatie.

**Day CQ Workflow Email Notification** ServiceConfigureer de e-mailinstellingen voor meldingen die door een workflow worden verzonden.

**CQ Rewriter HTML Parser Factory**

Controls the HTML Parser for the CQ rewriter.

* **Extra te verwerken**  tags: u kunt HTML-tags toevoegen of verwijderen die door de parser moeten worden verwerkt. Standaard worden de volgende codes verwerkt: A,IMG,GEBIED,FORMULIER,BASE,KOPPELING,SCRIPT,BODY,HEAD.
* **Camel-hoofdletters**  behouden - Standaard worden kenmerken in camel-hoofdletters (bijv. eBay) door de HTML-parser omgezet in kleine letters (bijv. eBay). U kunt dit uitschakelen om de kenmerken van het kamelenhoofdlettergebruik te behouden. Dit is nuttig wanneer het gebruiken van frontend kaders zoals Angular 2.

**Day Commons JDBC Connections** PoolConfigure toegang tot een externe database die als bron voor inhoud wordt gebruikt.

Dit is een Configuratie van de Fabriek, zodat kunnen de veelvoudige instanties worden gevormd.

**Adobe CQ Media DPS-sessies** ServiceDPS-sessies beheren voor gebruik met publicaties.

Met name kunt u de `dps.session.service.url.name` definiëren: default is set to [https://dpsapi2.digitalpublishing.acrobat.com/webservices/sessions](https://dpsapi2.digitalpublishing.acrobat.com/webservices/sessions)

**CDN** RewriterCommunication tussen AEM en een CDN moet worden gewaarborgd zodat de activa/binaire getallen aan eind - gebruiker op een veilige manier worden geleverd. Dit omvat twee taken:

* De bron wordt voor het eerst via de CDN benaderd via AEM (of nadat deze in cache is verlopen).
* Toegang hebbend tot het middel in CDN veilig caching aangezien zodra het middel in CDN in het voorgeheugen wordt opgeslagen, zal het verzoek niet naar AEM gaan en alle gebruikers die toegang tot dat middel hebben zouden van CDN moeten worden gediend.

AEM biedt een herschrijver voor het herschrijven van interne elementen-URL&#39;s naar externe CDN-URL&#39;s. Het herschrijft verbindingen die tot CDN met inbegrip van een handtekening JWS moeten worden overgegaan en verloopt tijd om de activa toe te staan om veilig worden betreden. Deze functie moet worden gebruikt op auteur-instanties.

De totale stroom is als volgt:

1. Gebruiker verifieert met AEM en vraagt een pagina met elementen aan.
1. Aangevraagde pagina bevat een element dat lijkt op `/content/dam/geometrixx-media/articles/paladin_trailer.jpg/jcr:content/renditions/cq5dam.thumbnail.319.319.png`
1. Rewriter transformeert de koppeling naar een CDN-URL die een JWS-handtekening bevat:
   `CDN_domain/content/dam/geometrixx-media/articles/paladin_trailer.jpg/_jcr_content/renditions/cq5dam.thumbnail.319.319.png?cdn_sign=JWS_SIGNATURE`

1. De browser van de gebruiker stuurt het elementverzoek vervolgens door naar de CDN-server
1. CDN zou moeten worden gevormd om het verzoek aan AEM samen met de `cdn_sign` parameter door:sturen.
1. Een manager van de Authentificatie bevestigt de `cdn_sign` parameter en keert de activa aan CDN terug die dan aan gebruiker wordt geleverd

De stroom tussen browser van de gebruiker, CDN, en AEM kan als volgt worden visualiseerd.

![chlimage_1-8](assets/chlimage_1-8.png)

>[!NOTE]
>
>Deze functie is momenteel alleen ingeschakeld voor AEM auteur-instanties.

**** CDNConfigServiceImplVerschaft CDN-configuraties

De CDN-herschrijffunctie kan worden ingeschakeld door **CDN-domeinnaam voor distributie** op te geven in de configuratie voor com.adobe.cq.cdn.rewriter.impl.CDNConfigServiceImpl.

De service bevat ook andere configuratieopties, zoals het opnieuw schrijven van CDN in- en uitschakelen, padvoorvoegsels waarvoor CDN wordt herschreven, TTL-waarden en protocol (HTTP of HTTPS).

**** CDNRewriterA opnieuw schrijven voor het herschrijven van interne afbeeldings-URL&#39;s naar CDN-URL&#39;s

De waarde **Tagkenmerken** in com.adobe.cq.cdn.rewriter.impl.CDNRewriter kan worden bepaald zodat slechts de selectieve beeldverbindingen worden herschreven.
