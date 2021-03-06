---
title: OSGi-configuratie-instellingen
seo-title: OSGi Configuration Settings
description: Dit artikel detailleert de OSGi configuratiemontages (die volgens bundel worden vermeld) die voor projectimplementatie relevant zijn. De lijst dient als richtsnoer en is niet limitatief.
seo-description: This article details the OSGi configuration settings (listed according to bundle) that are relevant to project implementation. The list acts as a guideline and it is not exhaustive.
uuid: 192d3287-ec99-403b-bab0-45721e4e3abd
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: configuring
content-type: reference
discoiquuid: ed3a858c-7a43-4515-a2ff-43ca465c7d7d
docset: aem65
feature: Configuring
exl-id: 19eedcf2-140a-452d-aa8f-6fd7f219e5f8
source-git-commit: e8320b1dac681fd2c9e749344e8c126487d840ba
workflow-type: tm+mt
source-wordcount: '3557'
ht-degree: 0%

---

# OSGi-configuratie-instellingen{#osgi-configuration-settings}

[OSGi](https://www.osgi.org/) is een fundamenteel element in de technologiestapel van AEM. Het wordt gebruikt om de samengestelde bundels van AEM en hun configuratie te controleren.

OSGi &quot;*biedt de gestandaardiseerde primitieven die het mogelijk maken toepassingen te maken op basis van kleine, herbruikbare en gezamenlijke onderdelen. Deze componenten kunnen in een toepassing worden samengesteld en worden opgesteld*&quot;.

Hierdoor kunt u eenvoudig bundels beheren, aangezien deze kunnen worden gestopt, geïnstalleerd en afzonderlijk kunnen worden gestart. De onderlinge afhankelijkheden worden automatisch verwerkt. Elke component OSGi (zie [OSGi-specificatie](https://www.osgi.org/Specifications/HomePage)) bevindt zich in een van de verschillende bundels. Bij AEM zijn er verschillende methoden om de configuratie-instellingen voor dergelijke bundels te beheren. zie [OSGi configureren](/help/sites-deploying/configuring-osgi.md) voor meer details en de aanbevolen werkwijzen.

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
>Het hulpprogramma OSGi Configuration Diff, een onderdeel van het [AEM](https://helpx.adobe.com/experience-manager/kb/tools/aem-tools.html), kan worden gebruikt om van de standaardOSGi configuraties een lijst te maken.

>[!NOTE]
>
>Voor specifieke onderdelen van de functionaliteit binnen AEM kunnen aanvullende bundels nodig zijn. In deze gevallen vindt u configuratiegegevens op de pagina die betrekking heeft op de juiste functionaliteit.

**Listener voor replicatiegebeurtenissen AEM** Configureren:

* De **Modi uitvoeren**, waarin replicatiegebeurtenissen naar listeners worden gedistribueerd. Bijvoorbeeld, als bepaald als auteur, dan is dit het systeem dat de replicatie &quot;&quot;in werking zal stellen.

* De uitvoeringsmodus **publish** moet worden toegevoegd als de projectcode replicatiegebeurtenissen (omgekeerde replicatie) in publicatiemilieu verwerkt. Bijvoorbeeld wanneer de verzender wordt gebruikt om van het publicatiemilieu te spoelen of wanneer de standaardreplicatie aan andere publicatieinstanties voorkomt.

**AEM wijzigingslistener voor opslagplaats** Configureren:

* De **Paden**, locaties om te luisteren naar opslagplaats-gebeurtenissen die gereed zijn voor distributie.

**CRX Sling Client Repository** Toegang tot de onderliggende opslagplaats voor inhoud configureren.

* De **Wachtwoord beheerder** moeten na de installatie worden gewijzigd om ervoor te zorgen dat [beveiliging](/help/sites-administering/security-checklist.md) van uw instantie.
* Andere wijzigingen zouden niet nodig moeten zijn en er moet zorgvuldig op worden gelet dat ze de toegang tot de opslagplaats kunnen beïnvloeden.

**Wiki Mail Service** Configureer de e-mailinstellingen voor e-mailberichten die door een wiki worden verzonden.

**Apache Felix OSGi Management Console** Configureren:

* **Plug-ins**, de belangrijkste navigatie-items (consoleplug-ins) die beschikbaar zijn in de **Apache Felix Web Management Console** als menu-items op het hoogste niveau. Schakel een optie uit die u niet nodig hebt omdat voor elke optie ruimte en bronnen vereist zijn.

>[!CAUTION]
>
>Ben zeker om het volgende te vormen:
>
>**Gebruikersnaam** en **Wachtwoord**, de referenties voor toegang tot de Apache Felix Web Management Console zelf.
>Het wachtwoord moet na de eerste installatie worden gewijzigd om ervoor te zorgen dat [beveiliging](/help/sites-administering/security-checklist.md) van uw instantie.

>[!NOTE]
>
>Deze configuratie moet worden gemaakt met de Felix Console zoals dat bij het opstarten nodig is - voordat de opslagplaats beschikbaar is.

**Apache Sling Aanpasbaar Data Logger Aanvraag** Configureren:

* **Logboeknaam** en **Logbestandsindeling** om de plaats en het formaat van verzoek en toegangsregistreren te vormen (gebrek: `request.log`). Dit logbestand is van essentieel belang voor het analyseren van de prestaties of foutopsporingsfunctionaliteit in verband met de webketen.
Dit is gekoppeld aan de [Apache Sling Request Logger](#apacheslingrequestlogger).

Zie voor meer informatie [AEM](/help/sites-deploying/configure-logging.md) en [Logboekregistratie voor verkoop](https://sling.apache.org/site/logging.html).

**Apache Sling Event Thread Pool** Configureren:

* **Min. groepsgrootte** en **Maximale groepsgrootte**, de grootte van de pool die wordt gebruikt om gebeurtenisdraden te houden.

* **Wachtrijgrootte**, de maximumgrootte van de draadrij als de pool uitgeput is.
De aanbevolen waarde is `-1` aangezien dit de rij aan onbeperkt plaatst; als een limiet wordt vastgesteld , kunnen verliezen optreden wanneer deze worden overschreden .

* Het veranderen van deze montages kan prestaties in scenario&#39;s met een hoog aantal gebeurtenissen helpen; bijvoorbeeld zwaar AEM DAM- of workflowgebruik.
* De waarden specifiek voor uw scenario zouden moeten worden bepaald gebruikend tests.
* Deze instellingen kunnen van invloed zijn op de prestaties van uw instantie. Wijzig deze instellingen dus niet zonder reden en met gepaste aandacht.

**Apache Sling GET Servlet** Configureer enkele aspecten van rendering:

* **Automatische index** om het renderen van mappen voor bladeren in- of uit te schakelen.
* **Inschakelen** (of maak onbruikbaar) standaardvertoningen, zoals **HTML**, **Onbewerkte tekst**, **JSON** of **XML**.
U moet JSON niet uitschakelen.

>[!NOTE]
>
>Deze instelling wordt automatisch geconfigureerd voor productieinstanties als u AEM uitvoert [Productie-klaar-modus](/help/sites-administering/production-ready.md).

**Apache Sling Java Script Handler** Configureer instellingen voor de compilatie van .java-bestanden als scripts (servlets).

Bepaalde instellingen kunnen van invloed zijn op de prestaties. Deze instellingen moeten waar mogelijk worden uitgeschakeld, met name voor een productie-instantie.

* **Bron-VM** en **DoelVM**, definieert u de JDK-versie als de versie die wordt gebruikt als de JVM voor de runtime

* voor productiegevallen:

   * disable **Foutopsporingsinfo genereren**

**Apache Sling JCR Installer** Deze parameters vergen waarschijnlijk geen configuratie, maar kunnen nuttig zijn om te weten wanneer het ontwikkelen of het zuiveren. De installatiemap(s) kan (kunnen) bijvoorbeeld handig zijn voor het in- en uitchecken of voor het maken van een pakket.

* **Naam van installatiemappen regexp** en **Maximale hiërarchiediepte van installatiemappen** - opgeven waar en tot welke diepte de opslagplaats naar bronnen zoekt die moeten worden geïnstalleerd. Wanneer een jokerteken wordt gebruikt (zoals in.&#42;/install) alle aangewezen gelijken zullen worden gezocht, bijvoorbeeld, `/libs/sling/install` en `/libs/cq/core/install`.

* **Zoekpad**, een lijst met paden die worden gezocht naar bronnen die moeten worden geïnstalleerd, samen met een nummer dat de wegingsfactor voor dat pad aangeeft.

**Apache Sling Job Event Handler** Parameters configureren die taakplanning beheren:

* **Interval opnieuw proberen**, **Maximale aantal pogingen**, **Maximale parallelle taken**, **Wacht tijd accentueren**, onder andere.

* Als u deze instellingen wijzigt, kunnen de prestaties in scenario&#39;s met een groot aantal taken worden verbeterd. Bijvoorbeeld, zwaar gebruik van AEM DAM en Workflows.
* De waarden specifiek voor uw scenario zouden moeten worden bepaald gebruikend tests.
* Wijzig deze instellingen niet zonder reden en pas na zorgvuldige afweging aan.

**Apache Sling JSP Script Handler** Vorm prestaties relevante montages voor de JSP manuscriptmanager. Als u de prestaties wilt verbeteren, moet u deze zoveel mogelijk uitschakelen.

Met name voor productiegevallen:

* disable **Foutopsporingsinfo genereren**
* disable **Gegenereerde Java behouden**
* disable **Toegewezen inhoud**
* disable **Bronfragmenten weergeven**

>[!NOTE]
>
>Deze instelling wordt automatisch geconfigureerd voor productieinstanties als u AEM uitvoert [Productie-klaar-modus](/help/sites-administering/production-ready.md).

**Configuratie van Apache Sling-logboekregistratie** Configureren:

* **Logboekniveau** en **Logbestand**, om de plaats en het logboekniveau van de centrale registrerenconfiguratie (error.log) te bepalen. Het niveau kan worden ingesteld op een van `DEBUG`, `INFO`, `WARN`, `ERROR` en `FATAL`.

* **Aantal logbestanden** en **Drempel logbestand** om de grootte en versieomwenteling van het logboekdossier te bepalen.

* **Berichtpatroon** bepaalt het formaat van de logboekberichten.

Zie voor meer informatie [AEM](/help/sites-deploying/configure-logging.md#global-logging) en [Logboekregistratie voor verkoop](https://sling.apache.org/site/logging.html).

**Apache Sling Logging Logger Configuration (Fabrieksconfiguratie)** Configureren:

* **Logboekniveau**, **Logbestand** en **Berichtindeling** om details van het logboekdossier en berichten te bepalen.

* **Aanmelder** de categorie te omschrijven; bijvoorbeeld alleen log voor com.day.cq.

* Met **Fabrieksconfiguraties**, kan om het even welk aantal extra configuraties worden toegevoegd om met de diverse nodig logboekniveaus en categorieën te behandelen.
* Dergelijke configuraties zijn nuttig tijdens de ontwikkeling; bijvoorbeeld om TRACE-berichten voor een specifieke service in een specifiek logbestand te registreren.
* Dergelijke configuraties zijn nuttig in een productieomgeving; bijvoorbeeld, om berichten over de specifieke dienst te hebben die aan een individueel logboekdossier voor gemakkelijkere controle wordt geregistreerd.

Zie voor meer informatie [AEM](/help/sites-deploying/configure-logging.md) en [Logboekregistratie voor verkoop](https://sling.apache.org/site/logging.html).

**Configuratie van Apache Sling Logging Writer (fabrieksconfiguratie)** Configureren:

* **Logbestand** om het bestaan van een logboekdossier te bepalen.
* **Aantal logbestanden** om de versieomwenteling te bepalen.

* De schrijver kan door een **Logboekconfiguratie Apache Sling Logging** configuratie.

* Dergelijke configuraties zijn nuttig tijdens de ontwikkeling; bijvoorbeeld om TRACE-berichten voor een specifieke service in een specifiek logbestand te registreren.
* Dergelijke configuraties zijn nuttig in een productieomgeving; bijvoorbeeld, om berichten over de specifieke dienst te hebben die aan een individueel logboekdossier voor gemakkelijkere controle wordt geregistreerd.

Zie voor meer informatie [AEM](/help/sites-deploying/configure-logging.md) en [Logboekregistratie voor verkoop](https://sling.apache.org/site/logging.html).

**Apache Sling Main Servlet** Configureren:

* **Aantal Vraag per Verzoek** en **Recursiediepte** om uw systeem tegen oneindige recursie en bovenmatige manuscriptvraag te beschermen.

**Apache Sling MIME Type Service** Configureren:

* **MIME-typen** om de vereiste gegevens voor uw project aan het systeem toe te voegen. Hierdoor is een `GET` verzoek om een dossier om de correcte inhoud-type kopbal voor het verbinden van het dossiertype en toepassing te plaatsen.

**Filter Apache Sling Referrer** Als u bekende beveiligingsproblemen wilt verhelpen met CSRF-bestanden (Cross-Site Request Smeedery) in CRX WebDAV en Apache Sling, moet u het filter Referrer configureren.

De dienst van de verwijzingsfilter is de dienst OSGi die u toestaat om te vormen:

* welke http-methoden moeten worden gefilterd
* Geeft aan of een lege verwijzingskoptekst is toegestaan
* en een lijst met servers die naast de serverhost zijn toegestaan.

Zie de [Beveiligingscontrolelijst - Problemen met de XSS-functie voor aanvragen voor andere sites](/help/sites-administering/security-checklist.md#protect-against-cross-site-request-forgery) voor nadere bijzonderheden.

>[!NOTE]
>
>Het filter Apache Sling Referrer is afhankelijk van de installatie van een snel reparatiepakket.

**Apache Sling Request Logger** Configureren:

* diverse parameters om te bepalen hoe de verzoeken worden geregistreerd.
* **Aanvraaglogboek inschakelen** in- of uitschakelen.

* **Toegangslogboek inschakelen** in- of uitschakelen.

Dit is gekoppeld aan de [Apache Sling Aanpasbaar Data Logger Aanvraag](#apacheslingcustomizablerequestdatalogger).

Zie voor meer informatie [AEM](/help/sites-deploying/configure-logging.md) en [Logboekregistratie voor verkoop](https://sling.apache.org/site/logging.html).

**Apache Sling Resource Resolver Factory** Centrale aspecten van het oplossen van resources voor splitsen configureren:

* **Zoekpad naar bronnen**(s), voeg om het even welke projectspecifieke wegen toe (maar verwijdert niet `/libs` of `/apps`).

* **Virtuele URL&#39;s** om uw vanity URL-toewijzingen te definiëren.

* **URL-toewijzingen** eventuele aliassen te definiëren; bijvoorbeeld `/content` tot `/`.

* **Toewijzingslocatie**, de mapconfiguratie extern `/etc/map`.

* Gebruik uw lokale installatie (bijvoorbeeld `https://localhost:4502/system/console/jcrresolver`) om te bepalen welke Resolver van het Middel actief is.

Zie voor meer informatie: [https://cwiki.apache.org/confluence/display/SLING/Flexible+Resource+Resolution](https://cwiki.apache.org/confluence/display/SLING/Flexible+Resource+Resolution).

>[!CAUTION]
>
>Deze opties moeten met name in de opslagplaats worden geconfigureerd.
>
>Anders worden wijzigingen aangebracht in **URL-toewijzingen** het gebruiken van de console van Felix zou door AEM op het volgende opstarten kunnen worden beschreven.

**Apache Sling Servlet/Script Resolver en Error Handler** De server Sling en de Oplossen van het Manuscript hebben veelvoudige taken:

1. Het wordt gebruikt als `ServletResolver` om de Servlet of het Manuscript te selecteren om te roepen om het verzoek te behandelen.

1. Het werkt als `SlingScriptResolver`.

1. De toepassing beheert foutafhandeling door de implementatie van de `ErrorHandler` interface die het zelfde algoritme gebruikt om fout behandelende servlets en manuscripten te selecteren zoals wordt gebruikt om verzoekverwerkingsservlets en manuscripten op te lossen.

Er kunnen verschillende parameters worden ingesteld, waaronder:

* **Uitvoerpaden** geeft een lijst van de wegen aan onderzoek naar uitvoerbare manuscripten; door specifieke paden te configureren kunt u beperken welke scripts kunnen worden uitgevoerd. Als geen weg wordt gevormd dan wordt het gebrek gebruikt ( `/` = wortel), staat dit de uitvoering van alle manuscripten toe.
Als een gevormde wegwaarde met een schuine streep beëindigt, wordt de volledige subboom gezocht. Zonder een dergelijke slash wordt het script alleen uitgevoerd als het exact overeenkomt.

* **Scriptgebruiker** - deze optionele eigenschap kan de gegevensopslaggebruikersaccount opgeven die wordt gebruikt voor het lezen van de scripts. Als er geen account is opgegeven, `admin` gebruiker wordt standaard gebruikt.

* **Standaardextensies** De lijst met extensies waarvoor het standaardgedrag wordt gebruikt. Dit betekent dat het laatste wegsegment van het middeltype als manuscriptnaam kan worden gebruikt.

**Day Commons GFX Font Helper** Bij het renderen van afbeeldingen kunt u met DrawText tekst insluiten. Hiervoor kunt u ook uw eigen lettertypen installeren:

* Definieer de **Lettertypepad** om te worden gezocht naar projectspecifieke doopvonten.
Bijvoorbeeld, `/apps/myapp/fonts`.

**Apache HTTP Components Proxy Configuration** Proxyconfiguratie voor alle code die de Apache HTTP-client gebruikt, die wordt gebruikt wanneer een HTTP wordt gemaakt. bijvoorbeeld bij replicatie.

Wanneer het creëren van een nieuwe configuratie, breng geen veranderingen in de fabrieksconfiguratie aan maar creeer in plaats daarvan een nieuwe fabrieksconfiguratie voor deze component gebruikend de hier beschikbare configuratiemanager: **https://localhost:4502/system/console/configMgr/**. De proxyconfiguratie is beschikbaar in **org.apache.http.proxyconfigurator.**

>[!NOTE]
>
>In AEM 6.0 en vroegere versies werd de volmacht gevormd in de Cliënt van HTTP van de Kommunnen van de Dag. Vanaf AEM 6.1 en later versies is de proxyconfiguratie verplaatst naar de &quot;Apache HTTP Components Proxy Configuration&quot; in plaats van de &#39;Day Commons HTTP Client&#39;-configuratie.

**Day CQ Antispam** Configureer de gebruikte anti-spamservice (Akismet). Hiervoor moet u het volgende registreren:

* **Provider**
* **API-sleutel**
* **Geregistreerde URL**

**Adobe Granite HTML Library Manager** Configureer dit om de verwerking van clientbibliotheken (css of js) te beheren; bijvoorbeeld hoe de onderliggende structuur wordt gezien.

* Voor productiegevallen:

   * enable **Minieren** (om CRLF- en spatietekens te verwijderen).
   * enable **Gzip** (zodat bestanden met één aanvraag kunnen worden gecomprimeerd en geopend).
   * disable **Foutopsporing**
   * disable **Timing**

* Voor JS-ontwikkeling (vooral bij foutopsporing/foutopsporing):

   * disable **Minieren**
   * enable **Foutopsporing** om de bestanden te scheiden voor foutopsporing en gebruik met firebug.
   * enable **Timing** in geval van belangstelling voor timing.
   * enable **Foutopsporing** console om JS console logboekberichten te zien.

>[!CAUTION]
>
>Wanneer u de instelling voor een van de **Minieren** of **Gzip** u moet ook de inhoud van `/var/clientlibs`. Dit is een cacheversie van de clientlibs die op verzoek opnieuw wordt samengesteld.

>[!NOTE]
>
>Deze instelling wordt automatisch geconfigureerd voor productieinstanties als u AEM uitvoert [Productie-klaar-modus](/help/sites-administering/production-ready.md).

**Day CQ HTTP Header Authentication Handler** Instellingen voor het hele systeem voor de basisverificatiemethode van de HTTP-aanvraag.

Wanneer u [gesloten gebruikersgroepen](/help/sites-administering/cug.md) u kunt (onder andere) het volgende configureren:

* **HTTP Realm**
* De **Standaardaanmeldingspagina**

**Day CQ Link Checker Service** Controleren en indien nodig configureren:

* **Plannerperiode** om het interval te bepalen waarmee externe verbindingen automatisch moeten worden gecontroleerd.

* Controleren **Ongeldig koppelingsinterval** voor de periode waarna een niet-succesvolle externe verbinding als slecht wordt beschouwd.
* **Patronen voor overschrijven van controle koppelen**, om paden te definiëren die van koppelingencontrole moeten worden uitgesloten.

**Taak voor de controle op de dag-CQ-koppeling** Configureer instellingen voor één koppelingencontrole-taak (een taak die een externe koppeling controleert):

* De intervallen controleren die zijn gedefinieerd in **Testinterval goede koppeling** en **Ongeldig testinterval voor koppeling**

* De verschillende parameters met betrekking tot proxy&#39;s voor internettoegang en NTLM die nodig zijn voor externe toegang bij het controleren van een koppeling.

**CQ-mailservice op dag** Vorm hostname en toegangsdetails voor de postserver. Gelieve te verwijzen naar het Vormen de sectie van de Dienst van de Post.

**Dag CQ MCM-nieuwsbrief** Configureer de verschillende instellingen die worden gebruikt met de nieuwsbrief.

**Uur CQ-hoofdtoewijzing** Configureren:

* **Doelpad** om te bepalen waar een verzoek &quot; `/`&quot; wordt doorgestuurd naar.

Er zijn twee UIs beschikbaar in AEM:

* de interface met aanraakbediening is de standaardinterface
* en de verouderde klassieke interface nog volledig operationeel is

Met AEM hoofdmaptoewijzing kunt u de interface configureren die u als standaard voor uw instantie wilt gebruiken:

* Als u de interface met aanraakbediening wilt instellen als de standaardinterface, gaat u naar **Doelpad** wijzen op:

   ```shell
      /projects.html
   ```

* Om klassieke UI als gebrek UI te hebben **Doelpad** wijzen op:

   ```shell
      /welcome.html
   ```

>[!NOTE]
>
>Op een standaardinstallatie is de interface met aanraakoptimalisatie de standaardinterface.

**Adobe Granite SSO-verificatiehandler** SSO-gegevens (Single Sign On) configureren; Deze zijn vaak nodig in instellingen van de ondernemingsauteur, vaak in combinatie met LDAP.

Er zijn verschillende configuratie-eigenschappen beschikbaar:

* **Pad**
Pad waarvoor deze verificatiehandler actief is. Als deze parameter leeg wordt gelaten, is de authentificatiemanager gehandicapt. Het pad/zorgt er bijvoorbeeld voor dat de verificatiehandler wordt gebruikt voor de gehele gegevensopslagruimte.

* **Servicereeks**
OSGi de Rangschikkende waarde van de Dienst van het Kader wordt gebruikt om op de orde te wijzen die voor het roepen van deze dienst wordt gebruikt. Dit is een 
`int` waarde waarbij hogere waarden een hogere prioriteit aangeven.
De standaardwaarde is `0`.

* **Namen van koptekst**
De namen van kopteksten die een gebruikersnaam kunnen bevatten.

* **Cookie-namen**
De naam of namen van cookies die een gebruikers-id kunnen bevatten.

* **Parameternamen**
De naam of namen van aanvraagparameters die de gebruikers-id kunnen bevatten.

* **Gebruikersoverzicht**
Voor geselecteerde gebruikers kan de gebruikersnaam die uit de HTTP-aanvraag is geëxtraheerd, worden vervangen door een andere naam in het object credentials. De toewijzing wordt hier gedefinieerd. Als de gebruikersnaam 
`admin` aan beide zijden van de kaart wordt de toewijzing genegeerd. Houd er rekening mee dat het teken &quot;=&quot; moet worden voorafgegaan door &quot;\&quot;.

* **Indeling**
Hiermee geeft u de indeling aan waarin de gebruikers-id wordt opgegeven. Gebruiken:

   * `Basic` als de gebruikers-id is gecodeerd in de indeling HTTP Basic Authentication
   * `AsIs` als de gebruiker-id wordt opgegeven in onbewerkte tekst of als een toegepaste reguliere expressie moet worden gebruikt zoals deze is of een reguliere expressie

**Day CQ WCM-foutopsporingsfilter** Dit is handig wanneer u een pagina opent en ontwikkelt, omdat hierdoor achtervoegsels zoals ?debug=layout kunnen worden gebruikt. Bijvoorbeeld, zal https://localhost:4502/cf#/content/geometrixx/en/support.html?debug=layout lay-outinformatie verstrekken die van belang voor de ontwikkelaar kan zijn.

* Schakel deze optie uit op productieexemplaren om prestaties en beveiliging te garanderen.

**Day CQ WCM-filter** Configureren:

* **WCM-modus **om de standaardmodus te definiëren.
* Op een instantie van de auteur kan dit `edit`, `disable,preview` of `analytics`.
De andere modi zijn toegankelijk via het zijpaneel of het achtervoegsel `?wcmmode=disabled` kan worden gebruikt om een productieomgeving te emuleren.

* Bij een publicatie-instantie moet deze instelling zijn ingesteld op `disabled` om ervoor te zorgen dat geen andere modus toegankelijk is.

>[!NOTE]
>
>Deze instelling wordt automatisch geconfigureerd voor productieinstanties als u AEM uitvoert [Productie-klaar-modus](/help/sites-administering/production-ready.md).

**Day CQ WCM Link Checker Configurator** Configureren:

* **Lijst met herschrijfconfiguraties** om een lijst met locaties op te geven voor op inhoud gebaseerde koppelingencontroleerconfiguraties. De configuraties kunnen op runtime wijze worden gebaseerd; dit is belangrijk om onderscheid te maken tussen auteur- en publicatieomgevingen, omdat de instellingen voor koppelingencontrole kunnen verschillen.

**Day CQ WCM Page Manager-fabriek** Configureren:

* **Activeringscontrole van substructuur pagina** voor een gebruiker (zonder replicatiemachtigingen) om pagina&#39;s te verwijderen of te verplaatsen (zelfs als de pagina&#39;s niet zijn geactiveerd).

**Day CQ WCM Page Processor** Configureren:

* **Paden**, een lijst met locaties waar het systeem luistert naar paginawijzigingen voordat het een `jcr:Event`.

**Adobe-paginamonpressiebeheer** Configureer voor een auteurinstantie:

* **sling.auth.requirements**: Stel de waarde van deze eigenschap in op `-/libs/wcm/stats/tracker`

>[!CAUTION]
>
>Deze configuratie zal anonieme verzoeken aan de volgende dienst toestaan.

>[!NOTE]
>
>Zie [Paginaafdrukken](/help/sites-deploying/configuring.md#enabling-page-impressions) voor meer informatie .

**Dag CQ WCM Pagina Statistieken** Configureer voor een publicatie-instantie:

* **URL voor het verzenden van gegevens** om URL te vormen die wordt gebruikt om paginatistieken te volgen (is essentieel als een trackerverzoek door de verzender gaat); De standaardwaarde is bijvoorbeeld `https://localhost:4502/libs/wcm/stats/tracker`.

* **Script bijhouden ingeschakeld** om ( `true`) of uitschakelen ( `false`) de opname van het volgende script op de pagina&#39;s. De standaardwaarde is `false`.

>[!NOTE]
>
>Zie [Paginaafdrukken](/help/sites-deploying/configuring.md#enabling-page-impressions) voor meer informatie .

**Day CQ WCM Version Manager** Bepaal of en hoe versies in uw systeem worden beheerd:

* **Versie maken bij activering**, ingeschakeld in een standaardinstallatie
* **Leegmaken inschakelen**

* **Paden wissen**, de paden die door een zoekactie worden doorzocht
* **Impliciete vergrootpaden**, de paden waar impliciete versioning actief is.

* **Maximale versiefagina**, de maximumleeftijd (in dagen) van een versie

* **Max. aantal versies**, het maximumaantal versies dat behouden mag blijven

Zie [Versie leegmaken](/help/sites-deploying/version-purging.md) voor meer informatie .

**Day CQ Workflow Email Notification Service** Configureer de e-mailinstellingen voor meldingen die via een workflow worden verzonden.

**CQ Rewriter HTML Parser Factory**

Controls the HTML Parser for the CQ rewriter.

* **Aanvullende labels die u wilt verwerken** - U kunt HTML-tags toevoegen of verwijderen die door de parser moeten worden verwerkt. Standaard worden de volgende codes verwerkt: A,IMG,GEBIED,FORMULIER,BASE,KOPPELING,SCRIPT,BODY,HEAD.
* **Camel-hoofdletters behouden** - Standaard zet de parser HTML kenmerken in kamelenhoofdletters (bijvoorbeeld eBay) om in kleine letters (bijvoorbeeld eBay). U kunt dit uitschakelen om de kenmerken van het kamelenhoofdlettergebruik te behouden. Dit is nuttig wanneer het gebruiken van frontend kaders zoals Angular 2.

**Day Commons JDBC-verbindingspool** Vorm toegang tot een extern gegevensbestand dat als bron voor inhoud wordt gebruikt.

Dit is een Configuratie van de Fabriek, zodat kunnen de veelvoudige instanties worden gevormd.

**Adobe CQ Media DPS-sessieservice** DPS-sessies beheren voor gebruik met publicaties.

Met name kunt u de `dps.session.service.url.name`: standaard is ingesteld op [https://dpsapi2.digitalpublishing.acrobat.com/webservices/sessions](https://dpsapi2.digitalpublishing.acrobat.com/webservices/sessions)

**CDN Rewriter** De communicatie tussen AEM en een CDN moet worden gewaarborgd zodat de activa/binaire getallen aan het eind - gebruiker op een veilige manier worden geleverd. Dit omvat twee taken:

* De bron wordt voor het eerst via de CDN benaderd via AEM (of nadat deze in cache is verlopen).
* Toegang hebbend tot het middel in CDN veilig caching aangezien zodra het middel in CDN in het voorgeheugen wordt opgeslagen, zal het verzoek niet naar AEM gaan en alle gebruikers die toegang tot dat middel hebben zouden van CDN moeten worden gediend.

AEM biedt een herschrijver voor het herschrijven van interne elementen-URL&#39;s naar externe CDN-URL&#39;s. Het herschrijft verbindingen die tot CDN met inbegrip van een handtekening JWS moeten worden overgegaan en verloopt tijd om de activa toe te staan om veilig worden betreden. Deze functie moet worden gebruikt op auteur-instanties.

De totale stroom is als volgt:

1. Gebruiker verifieert met AEM en vraagt een pagina met elementen aan.
1. Aangevraagde pagina bevat een element dat vergelijkbaar is met `/content/dam/geometrixx-media/articles/paladin_trailer.jpg/jcr:content/renditions/cq5dam.thumbnail.319.319.png`
1. Rewriter transformeert de koppeling naar een CDN-URL die een JWS-handtekening bevat:
   `CDN_domain/content/dam/geometrixx-media/articles/paladin_trailer.jpg/_jcr_content/renditions/cq5dam.thumbnail.319.319.png?cdn_sign=JWS_SIGNATURE`

1. De browser van de gebruiker stuurt het elementverzoek vervolgens door naar de CDN-server
1. CDN zou moeten worden gevormd om het verzoek aan AEM samen met door:sturen `cdn_sign` parameter.
1. Een verificatiehandler valideert de `cdn_sign` parameter en retourneert het element naar CDN dat vervolgens aan de gebruiker wordt geleverd

De stroom tussen browser van de gebruiker, CDN, en AEM kan als volgt worden visualiseerd.

![chlimage_1-8](assets/chlimage_1-8.png)

>[!NOTE]
>
>Deze functie is momenteel alleen ingeschakeld voor AEM auteur-instanties.

**CDNConfigServiceImpl** Bevat CDN-configuraties

De functie voor het herschrijven van de CDN kan worden ingeschakeld door **Domeinnaam CDN-distributie** in de configuratie voor com.adobe.cq.cdn.rewriter.impl.CDNConfigServiceImpl.

De service bevat ook andere configuratieopties, zoals het opnieuw schrijven van CDN in- en uitschakelen, padvoorvoegsels waarvoor CDN wordt herschreven, TTL-waarden en protocol (HTTP of HTTPS).

**CDNRewriter** Een herschrijver voor het herschrijven van interne afbeeldings-URL&#39;s naar CDN-URL&#39;s

De **Tagkenmerken** De waarde in com.adobe.cq.cdn.rewriter.impl.CDNRewriter kan worden bepaald zodat slechts de selectieve beeldverbindingen worden herschreven.
