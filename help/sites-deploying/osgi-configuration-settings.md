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
translation-type: tm+mt
source-git-commit: 474fc122f557f32d34fddd9d35a113431f6ce491
workflow-type: tm+mt
source-wordcount: '3805'
ht-degree: 0%

---


# OSGi-configuratie-instellingen{#osgi-configuration-settings}

[OSGi](https://www.osgi.org/) is een fundamenteel element in de technologiestapel van AEM. Het wordt gebruikt om de samengestelde bundels van AEM en hun configuratie te controleren.

OSGi &quot;*verstrekt de gestandaardiseerde primitieven die toepassingen toelaten om van kleine, herbruikbare en samenwerkende componenten worden gebouwd. Deze componenten kunnen in een toepassing worden samengesteld en worden opgesteld*&quot;.

Hierdoor kunt u eenvoudig bundels beheren, aangezien deze kunnen worden gestopt, geïnstalleerd en afzonderlijk kunnen worden gestart. De onderlinge afhankelijkheden worden automatisch verwerkt. Elke component OSGi (zie de Specificatie [](https://www.osgi.org/Specifications/HomePage)OSGi) is bevat in één van de diverse bundels. Bij AEM zijn er verschillende methoden om de configuratie-instellingen voor dergelijke bundels te beheren. zie het [Vormen OSGi](/help/sites-deploying/configuring-osgi.md) voor meer details en de geadviseerde praktijken.

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
>Het hulpmiddel van Diff van de Configuratie OSGi, een deel van de [AEM Hulpmiddelen](https://helpx.adobe.com/experience-manager/kb/tools/aem-tools.html), kan worden gebruikt om van de standaardOSGi configuraties een lijst te maken.

>[!NOTE]
>
>Voor specifieke onderdelen van de functionaliteit binnen AEM kunnen aanvullende bundels nodig zijn. In deze gevallen vindt u configuratiegegevens op de pagina die betrekking heeft op de juiste functionaliteit.

**Listener voor replicatiegebeurtenissen** configureren:

* De **Wijzen** van de Looppas, waarin de replicatiegebeurtenissen aan luisteraars zullen worden verdeeld. Bijvoorbeeld, als bepaald als auteur, dan is dit het systeem dat de replicatie &quot;&quot;in werking zal stellen.

* De looppaswijze **publiceert** moet worden toegevoegd als de projectcode replicatiegebeurtenissen (omgekeerde replicatie) in publicatiemilieu verwerkt. Bijvoorbeeld wanneer de verzender wordt gebruikt om van het publicatiemilieu te spoelen of wanneer de standaardreplicatie aan andere publicatieinstanties voorkomt.

**AEM wijzigingslistener voor opslagplaats** configureren:

* De **Paden**, locaties om te luisteren naar opslagplaats-gebeurtenissen die gereed zijn voor verspreiding.

**CRX Sling Client Repository** configureren toegang tot de onderliggende content repository.

* Het **beheerderswachtwoord** moet na de installatie worden gewijzigd om de [beveiliging](/help/sites-administering/security-checklist.md) van uw instantie te garanderen.
* Andere wijzigingen zouden niet nodig moeten zijn en er moet zorgvuldig op worden gelet dat ze de toegang tot de opslagplaats kunnen beïnvloeden.

**Wiki Mail Service** Configureer de e-mailinstellingen voor e-mailberichten die door een wiki worden verzonden.

**Apache Felix OSGi Management Console** configureren:

* **Plugins**, de belangrijkste navigatie-items (consolelinsteekmodules) die beschikbaar zijn in de **Apache Felix Web Management Console** als menu-items op het hoogste niveau. Schakel een optie uit die u niet nodig hebt omdat voor elke optie ruimte en bronnen vereist zijn.

>[!CAUTION]
>
>Ben zeker om het volgende te vormen:
>
>**Gebruikersnaam** en **wachtwoord**, de referenties voor toegang tot de Apache Felix Web Management Console zelf.
>Het wachtwoord moet na de eerste installatie worden gewijzigd om de [beveiliging](/help/sites-administering/security-checklist.md) van uw exemplaar te garanderen.

>[!NOTE]
>
>Deze configuratie moet worden gemaakt met de Felix Console zoals dat bij het opstarten nodig is - voordat de opslagplaats beschikbaar is.

**Apache Sling Customizable Request Data Logger** Configure:

* **De Naam** van het registreerapparaat en het Formaat **van het** Logboek om de plaats en het formaat van verzoek en toegangsregistreren te vormen (gebrek: `request.log`). Dit logbestand is van essentieel belang voor het analyseren van de prestaties of foutopsporingsfunctionaliteit in verband met de webketen.
Dit wordt gecombineerd met het [Apache Sling Request Logger](#apacheslingrequestlogger).

Zie [AEM Logging](/help/sites-deploying/configure-logging.md) en [Sling Logging](https://sling.apache.org/site/logging.html)voor meer informatie.

**Apache Sling Event Thread Pool** Configure:

* **Min. groepsgrootte** en **Max. groepsgrootte**, de grootte van de pool die wordt gebruikt om gebeurtenisdraden te houden.

* **De Grootte**van de rij, de maximumgrootte van de draadrij als de pool uitgeput is.
De aanbevolen waarde is `-1` omdat de wachtrij op onbeperkt wordt ingesteld. als een limiet wordt vastgesteld , kunnen verliezen optreden wanneer deze worden overschreden .

* Het veranderen van deze montages kan prestaties in scenario&#39;s met een hoog aantal gebeurtenissen helpen; bijvoorbeeld zwaar AEM DAM- of workflowgebruik.
* De waarden specifiek voor uw scenario zouden moeten worden bepaald gebruikend tests.
* Deze instellingen kunnen van invloed zijn op de prestaties van uw instantie. Wijzig deze instellingen dus niet zonder reden en met gepaste aandacht.

**Apache Sling GET Servlet** Configureer enkele aspecten van rendering:

* **Automatische index** om het renderen van mappen voor bladeren in- en uit te schakelen.
* **Standaardovergaven inschakelen** (of uitschakelen), zoals **HTML**, **Onbewerkte tekst**, **JSON** of **XML**.
U moet JSON niet uitschakelen.

>[!NOTE]
>
>Deze instelling wordt automatisch geconfigureerd voor productieinstanties als u AEM uitvoert in de [productieklaar](/help/sites-administering/production-ready.md).

**Apache Sling Java Script Handler** Configureer instellingen voor de compilatie van .java-bestanden als scripts (servlets).

Bepaalde instellingen kunnen van invloed zijn op de prestaties. Deze instellingen moeten waar mogelijk worden uitgeschakeld, met name voor een productie-instantie.

* De **bron-VM** en **doel-VM** definiëren de JDK-versie als de JVM-versie van de runtime

* voor productiegevallen:

   * uitschakelen **Foutopsporingsinfo genereren**

**Apache Sling JCR Installer** Deze parameters hebben waarschijnlijk geen configuratie nodig, maar kunnen nuttig zijn om te weten wanneer het ontwikkelen of het zuiveren. De installatiemap(s) kan (kunnen) bijvoorbeeld handig zijn voor het in- en uitchecken of voor het maken van een pakket.

* **Installatiemappen noemen regexp** en **Max. hiërarchiediepte van installatiemappen** - geef op waar en tot welke diepte opslagmappen worden gezocht naar bronnen die moeten worden geïnstalleerd. Wanneer een jokerteken wordt gebruikt (zoals in.*/install) alle geschikte overeenkomsten worden doorzocht, bijvoorbeeld `/libs/sling/install` en `/libs/cq/core/install`.

* **Zoekpad**, lijst met paden die in de installatie worden gezocht naar bronnen die moeten worden geïnstalleerd, samen met een getal dat de wegingsfactor voor dat pad aangeeft.

**Apache Sling Job Event Handler** Configureer parameters voor het beheren van taakplanning:

* **Herhaal interval**, **Maximale pogingen**, **Maximum Parallelle Banen**, **bevestig wachttijd**, onder andere.

* Als u deze instellingen wijzigt, kunnen de prestaties in scenario&#39;s met een groot aantal taken worden verbeterd. Bijvoorbeeld, zwaar gebruik van AEM DAM en Workflows.
* De waarden specifiek voor uw scenario zouden moeten worden bepaald gebruikend tests.
* Wijzig deze instellingen niet zonder reden en pas na zorgvuldige afweging aan.

**Apache Sling JSP Script-handler** Configureer de instellingen die relevant zijn voor de prestaties van de JSP-scripthandler. Als u de prestaties wilt verbeteren, moet u deze zoveel mogelijk uitschakelen.

Met name voor productiegevallen:

* uitschakelen **Foutopsporingsinfo genereren**
* Schakel Gegenereerde Java **behouden uit**
* toegewezen **inhoud uitschakelen**
* Bronfragmenten **weergeven uitschakelen**

>[!NOTE]
>
>Deze instelling wordt automatisch geconfigureerd voor productieinstanties als u AEM uitvoert in de [productieklaar](/help/sites-administering/production-ready.md).

**Configuratie** Apache Sling Logging-aanmelding configureren:

* **Logniveau** en **logbestand** om de locatie en het logniveau van de centrale logboekconfiguratie (error.log) te definiëren. Het niveau kan worden ingesteld op een van `DEBUG`, `INFO`, `WARN`, `ERROR` en `FATAL`.

* **Aantal logbestanden** en **logboekbestandsdrempel** om de grootte en de rotatie van de versie van het logbestand te bepalen.

* **Het Patroon van het bericht** bepaalt het formaat van de logboekberichten.

Zie [AEM Logging](/help/sites-deploying/configure-logging.md#global-logging) en [Sling Logging](https://sling.apache.org/site/logging.html)voor meer informatie.

**Configuratie van Apache Sling Logging Logger (fabrieksconfiguratie)** configureren:

* **Logniveau**, **logbestand** en **berichtindeling** om details van het logbestand en berichten te definiëren.

* **Logger** om de categorie te definiëren; bijvoorbeeld alleen log voor com.day.cq.

* Met behulp van **fabrieksconfiguraties** kan een willekeurig aantal aanvullende configuraties worden toegevoegd om rekening te houden met de verschillende logniveaus en -categorieën die nodig zijn.
* Dergelijke configuraties zijn nuttig tijdens de ontwikkeling; bijvoorbeeld om TRACE-berichten voor een specifieke service in een specifiek logbestand te registreren.
* Dergelijke configuraties zijn nuttig in een productieomgeving; bijvoorbeeld, om berichten over de specifieke dienst te hebben die aan een individueel logboekdossier voor gemakkelijkere controle wordt geregistreerd.

Zie [AEM Logging](/help/sites-deploying/configure-logging.md) en [Sling Logging](https://sling.apache.org/site/logging.html)voor meer informatie.

**Configuratie van Apache Sling Logging Writer (fabrieksconfiguratie)** configureren:

* **Logbestand** om het bestaan van een logbestand te definiëren.
* **Aantal logbestanden** dat de rotatie van de versie moet definiëren.

* De schrijver kan door een configuratie van de Logger van de Registratie **** van het Logboekregistratie van Apache Sling worden gebruikt.

* Dergelijke configuraties zijn nuttig tijdens de ontwikkeling; bijvoorbeeld om TRACE-berichten voor een specifieke service in een specifiek logbestand te registreren.
* Dergelijke configuraties zijn nuttig in een productieomgeving; bijvoorbeeld, om berichten over de specifieke dienst te hebben die aan een individueel logboekdossier voor gemakkelijkere controle wordt geregistreerd.

Zie [AEM Logging](/help/sites-deploying/configure-logging.md) en [Sling Logging](https://sling.apache.org/site/logging.html)voor meer informatie.

**Apache Sling Main Servlet** Configure:

* **Aantal Vraag per Verzoek** en Diepte **van de** Recursie om uw systeem tegen oneindige recursie en bovenmatige manuscriptvraag te beschermen.

**Apache Sling MIME Type Service** configureren:

* **MIME Types** om die toe te voegen die door uw project aan het systeem worden vereist. Hierdoor kan een `GET` aanvraag voor een bestand de juiste header van het inhoudstype instellen voor het koppelen van het bestandstype en de toepassing.

**Apache Sling Reference Filter** Om bekende beveiligingsproblemen aan te pakken met CSRF (Cross-Site Request Smeedery) in CRX WebDAV en Apache Sling moet u het filter Referrer configureren.

De dienst van de verwijzingsfilter is de dienst OSGi die u toestaat om te vormen:

* welke http-methoden moeten worden gefilterd
* Geeft aan of een lege verwijzingskoptekst is toegestaan
* en een lijst met servers die naast de serverhost zijn toegestaan.

Zie Controlelijst voor [beveiliging - Problemen met de smederij](/help/sites-administering/security-checklist.md#protect-against-cross-site-request-forgery) voor aanvragen voor meerdere sites voor meer informatie.

>[!NOTE]
>
>Het filter Apache Sling Referrer is afhankelijk van de installatie van een snel reparatiepakket.

**Apache Sling Request Logger** Configure:

* diverse parameters om te bepalen hoe de verzoeken worden geregistreerd.
* **Schakel Aanvraaglogbestand** in of uit.

* **Schakel Toegangslogboek** in of uit.

Dit is gekoppeld aan het aanpasbare [Apache Sling-aanvraaggegevenslogger](#apacheslingcustomizablerequestdatalogger).

Zie [AEM Logging](/help/sites-deploying/configure-logging.md) en [Sling Logging](https://sling.apache.org/site/logging.html)voor meer informatie.

**Apache Sling Resource Resolver Factory** Configureer centrale aspecten van de oplossing van verkoopbronnen:

* **Zoekpad**(en) voor bronnen toevoegen, specifieke paden voor projecten toevoegen (maar niet verwijderen `/libs` of `/apps`).

* **Virtuele URL&#39;s** om uw vanity URL-toewijzingen te definiëren.

* **URL Mappings** om om het even welke aliassen te bepalen; bijvoorbeeld van `/content` tot `/`.

* **Toewijzingslocatie**, de mapconfiguratie extern geïmplementeerd in `/etc/map`.

* Gebruik uw lokale installatie (bijvoorbeeld, gebruik `https://localhost:4502/system/console/jcrresolver`) om te bepalen welke Resolver van het Middel actief is.

Zie voor meer informatie: [https://cwiki.apache.org/confluence/display/SLING/Flexible+Resource+Resolution](https://cwiki.apache.org/confluence/display/SLING/Flexible+Resource+Resolution).

>[!CAUTION]
>
>Deze opties moeten met name in de opslagplaats worden geconfigureerd.
>
>Anders zouden de veranderingen die in **Toewijzingen** URL gebruikend de console van Felix worden aangebracht door AEM bij de volgende opstarten kunnen worden beschreven.

**Apache Sling Servlet/Script Resolver en de manager** van de Fout Sling Servlet en de Besloeiing van het Manuscript heeft veelvoudige taken:

1. Het wordt gebruikt als `ServletResolver` om de Servlet of het Manuscript te selecteren om te roepen om het verzoek te behandelen.

1. Het werkt als de `SlingScriptResolver`.

1. Het beheert fout behandeling door de `ErrorHandler` interface uit te voeren die het zelfde algoritme gebruikt om fout behandelende servlets en manuscripten te selecteren zoals wordt gebruikt om verzoekverwerkingsservlets en manuscripten op te lossen.

Er kunnen verschillende parameters worden ingesteld, waaronder:

* **Uitvoeringspaden** bevatten de paden die moeten worden gezocht naar uitvoerbare scripts. door specifieke paden te configureren kunt u beperken welke scripts kunnen worden uitgevoerd. Als geen weg dan wordt gevormd wordt het gebrek gebruikt ( `/` = wortel), staat dit de uitvoering van alle manuscripten toe.
Als een gevormde wegwaarde met een schuine streep beëindigt, wordt de volledige subboom gezocht. Zonder een dergelijke slash wordt het script alleen uitgevoerd als het exact overeenkomt.

* **Scriptgebruiker** - deze optionele eigenschap kan de gegevensopslaggebruikersaccount opgeven die wordt gebruikt voor het lezen van de scripts. Als er geen account is opgegeven, wordt de `admin` gebruiker standaard gebruikt.

* **Standaardextensies** De lijst met extensies waarvoor het standaardgedrag wordt gebruikt. Dit betekent dat het laatste wegsegment van het middeltype als manuscriptnaam kan worden gebruikt.

**Met dagmenu&#39;s kunt u tekst insluiten met behulp van DrawText wanneer u afbeeldingen rendert** . Hiervoor kunt u ook uw eigen lettertypen installeren:

* Definieer het **lettertypepad** dat u wilt doorzoeken naar projectspecifieke lettertypen.
Bijvoorbeeld, `/apps/myapp/fonts`.

**Apache HTTP Components Proxy Configuration** Proxy configuration voor alle code die de Apache HTTP client gebruikt, wordt gebruikt wanneer een HTTP wordt gemaakt. bijvoorbeeld bij replicatie.

Wanneer het creëren van een nieuwe configuratie, breng geen veranderingen in de fabrieksconfiguratie aan maar creeer in plaats daarvan een nieuwe fabrieksconfiguratie voor deze component gebruikend de hier beschikbare configuratiemanager: **https://localhost:4502/system/console/configMgr/**. De proxyconfiguratie is beschikbaar in **org.apache.http.proxyconfigurator.**

>[!NOTE]
>
>In AEM 6.0 en vroegere versies werd de volmacht gevormd in de Cliënt van HTTP van de Kommunnen van de Dag. Vanaf AEM 6.1 en later versies is de proxyconfiguratie verplaatst naar de &quot;Apache HTTP Components Proxy Configuration&quot; in plaats van de &#39;Day Commons HTTP Client&#39;-configuratie.

**Dag CQ Antispam** vormt de anti-spamdienst (Akismet) gebruikt. Hiervoor moet u het volgende registreren:

* **Provider**
* **API-sleutel**
* **Geregistreerde URL**

**Adobe Granite HTML Library Manager** Configureer dit om de verwerking van clientbibliotheken (css of js) te beheren; bijvoorbeeld hoe de onderliggende structuur wordt gezien.

* Voor productiegevallen:

   * Schakel **Minify** in (om CRLF- en whitespace-tekens te verwijderen).
   * Schakel **Gzip** in (als u wilt dat bestanden met één aanvraag kunnen worden gecomprimeerd en geopend).
   * debug **uitschakelen**
   * uitschakelen **Timing**

* Voor JS-ontwikkeling (vooral bij foutopsporing/foutopsporing):

   * Schakelen **Miniatuur**
   * Schakel **Foutopsporing** in om de bestanden te scheiden voor foutopsporing en gebruik met foutopsporing.
   * de **Timing** mogelijk te maken in geval van belangstelling voor timing.
   * laat **Debug** console toe om de berichten van het JS consolelogboek te zien.

>[!CAUTION]
>
>Wanneer u de instelling voor **Minify** of **Gzip** wijzigt, moet u ook de inhoud van `/var/clientlibs`. Dit is een cacheversie van de clientlibs die op verzoek opnieuw wordt samengesteld.

>[!NOTE]
>
>Deze instelling wordt automatisch geconfigureerd voor productieinstanties als u AEM uitvoert in de [productieklaar](/help/sites-administering/production-ready.md).

**Dag CQ HTTP Header Authentication Handler** System wide settings for the basic authentication method of the HTTP request.

Wanneer u [gesloten gebruikersgroepen](/help/sites-administering/cug.md) gebruikt, kunt u (onder andere) het volgende configureren:

* **HTTP Realm**
* De **standaardaanmeldingspagina**

**De Controle van de Dienst** van de Controle van de Verbinding van CQ van de dag en vormt indien nodig:

* **De Periode** van de planner om het interval te bepalen waarbij de externe verbindingen automatisch moeten worden gecontroleerd.

* Controleer **het Onjuiste Interval** van de Tolerantie van de Verbinding voor de periode waarna een onsuccesvolle externe verbinding als slecht wordt beschouwd.
* **Koppelingcontrole Patronen** overschrijven om paden te definiëren die van koppelingencontrole moeten worden uitgesloten.

**De Taak** van de Controle van de Verbinding van CQ van de dag vormt montages voor één enkele taak van de verbindingscontrole (een taak die een externe verbinding controleert):

* Controleer de intervallen die in het Interval **van de Test van de Verbinding van de** Goede en Interval van de Test van de Verbinding van de **Verkeer worden bepaald**

* De verschillende parameters met betrekking tot proxy&#39;s voor internettoegang en NTLM die nodig zijn voor externe toegang bij het controleren van een koppeling.

**CQ-mailservice** op de dag Configureer hostnaam en toegangsgegevens voor de mailserver. Gelieve te verwijzen naar het Vormen de sectie van de Dienst van de Post.

**CQ MCM-nieuwsbrief** op de dag Configureer de verschillende instellingen die worden gebruikt met de nieuwsbrief.

**Uur CQ-hoofdtoewijzing** configureren:

* **Doelpad** om te bepalen waar een aanvraag naar &quot; `/`&quot; wordt omgeleid.

Er zijn twee UIs beschikbaar in AEM:

* de interface met aanraakbediening is de standaardinterface
* en de vervangen klassieke interface nog volledig operationeel is

Met AEM hoofdmaptoewijzing kunt u de interface configureren die u als standaard voor uw instantie wilt gebruiken:

* Als u de interface met aanraakbediening wilt instellen als de standaardinterface, moet het **doelpad** verwijzen naar:

   ```
      /projects.html
   ```

* Om klassieke UI als gebrek UI te hebben zou het Weg **van het** Doel moeten richten aan:

   ```
      /welcome.html
   ```

>[!NOTE]
>
>Op een standaardinstallatie is de interface met aanraakoptimalisatie de standaardinterface.

**Adobe granite SSO Authentication Handler** Configure Single Sign On (SSO) details; Deze zijn vaak nodig in instellingen van de ondernemingsauteur, vaak in combinatie met LDAP.

Er zijn verschillende configuratie-eigenschappen beschikbaar:

* **Pad** waarvoor deze verificatiehandler actief is. Als deze parameter leeg wordt gelaten, is de authentificatiemanager gehandicapt. Het pad/zorgt er bijvoorbeeld voor dat de verificatiehandler wordt gebruikt voor de gehele gegevensopslagruimte.

* **De Rangschikkende** waarde van de Dienst van het Kader van de dienst OSGi wordt gebruikt om op de orde te wijzen die voor het roepen van deze dienst wordt gebruikt. Dit is een 
`int` waarde waarbij hogere waarden een hogere prioriteit aangeven.
De standaardwaarde is `0`.

* **Koptekstnamen** De naam of namen van kopteksten die een gebruikers-id kunnen bevatten.

* **Cookie-namen** De naam of namen van cookies die een gebruikers-id kunnen bevatten.

* **Parameternamen** De namen van aanvraagparameters die de gebruikers-id kunnen bevatten.

* **Gebruikersoverzicht** Voor geselecteerde gebruikers kan de gebruikersnaam die uit de HTTP-aanvraag is geëxtraheerd, worden vervangen door een andere naam in het object credentials. De toewijzing wordt hier gedefinieerd. Als de gebruikersnaam 
`admin` aan beide zijden van de kaart wordt de toewijzing genegeerd. Houd er rekening mee dat het teken &quot;=&quot; moet worden voorafgegaan door &quot;\&quot;.

* **De indeling** geeft de indeling aan waarin de gebruikers-id wordt opgegeven. Gebruiken:

   * `Basic` als de gebruikers-id is gecodeerd in de indeling HTTP Basic Authentication
   * `AsIs` als de gebruiker-id wordt opgegeven in onbewerkte tekst of als een toegepaste waarde voor een reguliere expressie moet worden gebruikt zoals deze is of een reguliere expressie

**De dag CQ zuivert filter** WCM Dit is nuttig wanneer het ontwikkelen aangezien het het gebruik van achtervoegsels zoals ?debug=layout toestaat wanneer het toegang tot van een pagina. Bijvoorbeeld, zal https://localhost:4502/cf#/content/geometrixx/en/support.html?debug=layout lay-outinformatie verstrekken die van belang voor de ontwikkelaar kan zijn.

* Schakel deze optie uit op productieexemplaren om prestaties en beveiliging te garanderen.

**Day CQ WCM-filter** configureren:

* **WCM-modus **om de standaardmodus te definiëren.
* Op een auteurinstantie zou dit `edit`, `disable,preview` of `analytics`kunnen zijn.
De andere modi zijn toegankelijk vanaf het zijpaneel of het achtervoegsel `?wcmmode=disabled` kan worden gebruikt om een productieomgeving te emuleren.

* Op een publicatie-instantie moet dit zo worden ingesteld dat er geen andere modus toegankelijk is. `disabled`

>[!NOTE]
>
>Deze instelling wordt automatisch geconfigureerd voor productieinstanties als u AEM uitvoert in de [productieklaar](/help/sites-administering/production-ready.md).

**De configuratiebeheerfunctie voor WCM-koppelingencontrole** op dag:

* **Lijst met herschrijfconfiguraties** om een lijst met locaties voor op inhoud gebaseerde koppelingencontroleerconfiguraties op te geven. De configuraties kunnen op runtime wijze worden gebaseerd; dit is belangrijk om onderscheid te maken tussen auteur- en publicatieomgevingen, omdat de instellingen voor koppelingencontrole kunnen verschillen.

**Day CQ WCM Page Processor** configureren:

* **Paden**, een lijst met locaties waar het systeem luistert naar paginawijzigingen voordat een wijziging wordt geactiveerd `jcr:Event`.

**Adobe Page Impressions Tracker** voor het configureren van een auteurinstantie:

* **sling.auth.requirements**: Stel de waarde van deze eigenschap in op `-/libs/wcm/stats/tracker`

>[!CAUTION]
>
>Deze configuratie zal anonieme verzoeken aan de volgende dienst toestaan.

>[!NOTE]
>
>Zie [Paginaafdrukken](/help/sites-deploying/configuring.md#enabling-page-impressions) voor meer informatie.

**Day CQ WCM Page Statistics** For a publish instance configure:

* **URL om gegevens** te verzenden om URL te vormen die wordt gebruikt om paginatistieken te volgen (is essentieel als een trackerverzoek door de verzender gaat); De standaardwaarde is bijvoorbeeld `https://localhost:4502/libs/wcm/stats/tracker`.

* **Script bijhouden is ingeschakeld** om de opname van het volgende script op de pagina&#39;s in te schakelen ( `true`) of uit te schakelen ( `false`). De standaardwaarde is `false`.

>[!NOTE]
>
>Zie [Paginaafdrukken](/help/sites-deploying/configuring.md#enabling-page-impressions) voor meer informatie.

**De Controle van het Manager** van de Versie van WCM van de dag CQ als, en hoe, de versies in uw systeem worden beheerd:

* **Versie maken bij activering**, ingeschakeld in een standaardinstallatie
* **Leegmaken inschakelen**

* **Paden** wissen, de paden die met een zoekactie worden doorzocht
* **Impliciete versioning-paden**, de paden waar impliciete versioning actief is.

* **Maximale versieleeftijd**, de maximumleeftijd (in dagen) van een versie

* **Max. aantal versies**, het maximumaantal versies dat behouden moet blijven

Zie [Versie leegmaken](/help/sites-deploying/version-purging.md) voor meer informatie.

**Day CQ Workflow Email Notification Service** Configureer de e-mailinstellingen voor meldingen die door een workflow worden verzonden.

**Dag CQSE HTTP Service** bepaalt de CQ Servlet Engine:

* **NIO voor HTTP, **Of om NIO voor HTTP al dan niet te gebruiken. Heeft als standaardwaarde true. Wordt alleen gebruikt als HTTP is ingeschakeld.
* **Time-out verbinding, **Time-out verbinding in milliseconden. Deze eigenschap is van toepassing op zowel HTTP- als HTTPS-verbindingen. Wordt standaard ingesteld op 60 seconden.

* **HTTPS inschakelen,** ongeacht of HTTPS is ingeschakeld. De standaardwaarde is false.
* **Time-out** sessie, standaardlevensduur van een HTTP-sessie opgegeven in minuten. Als de time-out 0 of minder is, wordt er nooit een time-out voor de sessies uitgevoerd. Wordt standaard ingesteld op 10 minuten.
* **Debug Logging**, Of om DEBUG niveauberichten of niet te schrijven. De standaardwaarde is false.
* **Buffergrootte** aanvragen, grootte van de buffer voor aanvragen in bytes. De standaardwaarde is 8 kB.
* **Maximum aantal draden**, Maximum aantal draden om verzoeken te gebruiken te behandelen. De standaardwaarde is 200.

De volgende eigenschappen zijn alleen van toepassing als HTTPS is ingeschakeld.

* **HTTPS-poort**, poort om te luisteren naar HTTPS-aanvraag. De standaardwaarde is 433.
* **NIO voor HTTPS**, Al dan niet om NIO voor HTTP te gebruiken. Wordt standaard ingesteld op de waarde van de eigenschap NIO for HTTP.
* **Keystore**, absoluut pad naar het sleutelarchief voor gebruik bij HTTPS. Vereist als HTTPS is ingeschakeld.
* **Wachtwoord** sleutelarchief, Wachtwoord voor toegang tot sleutelarchief.
* **Sleutelalias**, alias van de geheime sleutel in het sleutelarchief.
* **Sleutelwachtwoord**, Wachtwoord om de geheime sleutel in Keystore te ontgrendelen.
* **Clientcertificaat**, vereist dat de client een geldig certificaat levert. Heeft als standaardwaarde geen.

Zie ook [HTTP via SSL](/help/sites-administering/ssl-by-default.md) inschakelen voor meer informatie over de SSL-gerelateerde opties en een volledige beschrijving van het inschakelen van HTTPS voor CQSE.

**CQ Rewriter HTML Parser Factory**

Controls the HTML Parser for the CQ rewriter.

* **Extra te verwerken** tags - U kunt HTML-tags toevoegen of verwijderen die door de parser moeten worden verwerkt. Standaard worden de volgende codes verwerkt: A,IMG,GEBIED,FORMULIER,BASE,KOPPELING,SCRIPT,BODY,HEAD.
* **Camel-hoofdletters** behouden - standaard worden kenmerken in kamelenhoofdletters (bijv. eBay) door de HTML-parser omgezet in kleine letters (bijv. eBay). U kunt dit uitschakelen om de kenmerken van het kamelenhoofdlettergebruik te behouden. Dit is handig wanneer u frontend frameworks zoals Angular 2 gebruikt.

**De Pool** van Verbindingen van de Commons JDBC van de dag vormt toegang tot een extern gegevensbestand dat als bron voor inhoud wordt gebruikt.

Dit is een Configuratie van de Fabriek, zodat kunnen de veelvoudige instanties worden gevormd.

**Adobe CQ Media DPS-sessieservice** DPS-sessies beheren voor gebruik met publicaties.

U kunt met name de volgende `dps.session.service.url.name`elementen definiëren: default is set to [https://dpsapi2.digitalpublishing.acrobat.com/webservices/sessions](https://dpsapi2.digitalpublishing.acrobat.com/webservices/sessions)

**CDN herschrijver** Communicatie tussen AEM en een CDN moet worden gewaarborgd zodat de activa/binaire getallen aan eind - gebruiker op een veilige manier worden geleverd. Dit omvat twee taken:

* De bron wordt voor het eerst via de CDN benaderd via AEM (of nadat deze in cache is verlopen).
* Toegang hebbend tot het middel in CDN veilig caching aangezien zodra het middel in CDN in het voorgeheugen wordt opgeslagen, zal het verzoek niet naar AEM gaan en alle gebruikers die toegang tot dat middel hebben zouden van CDN moeten worden gediend.

AEM biedt een herschrijver voor het herschrijven van interne elementen-URL&#39;s naar externe CDN-URL&#39;s. Het herschrijft verbindingen die tot CDN met inbegrip van een handtekening JWS moeten worden overgegaan en verloopt tijd om de activa toe te staan om veilig worden betreden. Deze functie moet worden gebruikt op auteur-instanties.

De totale stroom is als volgt:

1. Gebruiker verifieert met AEM en vraagt een pagina met elementen aan.
1. Aangevraagde pagina bevat een element dat vergelijkbaar is met `/content/dam/geometrixx-media/articles/paladin_trailer.jpg/jcr:content/renditions/cq5dam.thumbnail.319.319.png`
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

**CDNConfigServiceImpl** biedt CDN-configuraties

De CDN die eigenschap herschrijft kan worden toegelaten door **CDN naam** van het distributiedomein in de configuratie voor com.adobe.cq.cdn.rewriter.impl.CDNConfigServiceImpl te verstrekken.

De service bevat ook andere configuratieopties, zoals het opnieuw schrijven van CDN in- en uitschakelen, padvoorvoegsels waarvoor CDN wordt herschreven, TTL-waarden en protocol (HTTP of HTTPS).

**CDNRewriter** A rewriter for rewriting internal image URLs to CDN URLs

De waarde van de Attributen **van de** Markering in com.adobe.cq.cdn.rewriter.impl.CDNRewriter kan worden bepaald zodat slechts de selectieve beeldverbindingen worden herschreven.
