---
title: AEM kernconcepten
seo-title: De basisbeginselen
description: Een overzicht van de kernconcepten van hoe AEM gestructureerd is en hoe zich bovenop het te ontwikkelen met inbegrip van het begrijpen van JCR, Sling, OSGi, de verzender, de werkschema's, en MSM
seo-description: Een overzicht van de kernconcepten van hoe AEM gestructureerd is en hoe zich bovenop het te ontwikkelen met inbegrip van het begrijpen van JCR, Sling, OSGi, de verzender, de werkschema's, en MSM
uuid: e49f29db-a5d6-48a0-af32-f8785156746e
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: introduction
content-type: reference
discoiquuid: 6e913190-be92-4862-a8b9-517f8bde0044
exl-id: f6f32290-422e-4037-89d8-d9f414332e8e
translation-type: tm+mt
source-git-commit: 78e28636eec331314c2f29c93d516215b1572f20
workflow-type: tm+mt
source-wordcount: '3367'
ht-degree: 0%

---

# Core Concepten AEM {#aem-core-concepts}

>[!NOTE]
>
>Alvorens in de kernconcepten van AEM te duiken, adviseert Adobe de Leergids van WKND in [Aan de slag het Ontwikkelen van AEM Sites](/help/sites-developing/getting-started.md) document voor een overzicht van het AEM ontwikkelingsproces en inleiding aan kernconcepten te voltooien.

## Vereisten voor ontwikkeling op AEM {#prerequisites-for-developing-on-aem}

U hebt de volgende vaardigheden nodig om zich bovenop AEM te ontwikkelen:

* Basiskennis van webtoepassingstechnieken, waaronder:

   * het verzoek-antwoord (XMLHttpRequest / XMLHttpResponse)-cyclus
   * HTML
   * CSS
   * JavaScript

* De werkkennis van de Server van de Ervaring (CRX), met inbegrip van de Ontdekkingsreiziger van de Inhoud
* Voor het ontwikkelen in klassieke UI, wordt de basiskennis van JSP (de Pagina&#39;s van JavaServer) met inbegrip van de capaciteit om eenvoudige JSP voorbeelden te begrijpen en te wijzigen ook vereist.

Het wordt ook geadviseerd dat u [Richtlijnen en Beste Praktijken ](/help/sites-developing/dev-guidelines-bestpractices.md) leest en volgt.

## Java Content Repository {#java-content-repository}

De JCR-standaard (Java Content Repository), [JSR 283](https://docs.adobe.com/content/docs/en/spec/jcr/2.0/index.html), geeft een leveranciersonafhankelijke en implementatievrije manier aan om inhoud bidirectioneel te benaderen op granulair niveau in een inhoudsopslagplaats.

Specificatie lead wordt gehouden door Adobe Research (Zwitserland) AG.

Het [JCR API 2.0](https://docs.adobe.com/docs/en/spec/javax.jcr/javadocs/jcr-2.0/index.html)-pakket, javax.jcr.&amp;ast; wordt gebruikt voor directe toegang tot en manipulatie van inhoud in de repository.

## Experience Server (CRX) en Jackrabbit {#experience-server-crx-and-jackrabbit}

De Server van de Ervaring verstrekt de Diensten van de Ervaring die AEM worden voortgebouwd, en die kunnen worden gebruikt om douanetoepassingen te bouwen, en het sluit de Inhoudsbewaarplaats van de Inhoud op Jackrabbit in.

[Apache ](https://jackrabbit.apache.org/) Jackrabbitis is een open-source, volledig conform, implementatie van de JCR API 2.0.

## Verwerking verzoek tot verzending {#sling-request-processing}

### Inleiding tot Sling {#introduction-to-sling}

AEM wordt gebouwd gebruikend [Sling](https://sling.apache.org/site/index.html), een de toepassingskader van het Web dat op de principes van REST wordt gebaseerd die gemakkelijke ontwikkeling van inhoud-georiënteerde toepassingen verstrekken. Bij Sling wordt een JCR-opslagplaats gebruikt, zoals Apache Jackrabbit, of in het geval van AEM de CRX Content Repository, als gegevensopslagruimte. Sling is toegevoegd aan de Apache Software Foundation - meer informatie is te vinden op Apache.

Met Verschuiving is het type inhoud dat moet worden gerenderd niet de eerste verwerkingsoverweging. De belangrijkste overweging is in plaats daarvan of de URL wordt omgezet in een inhoudsobject waarvoor vervolgens een script kan worden gevonden om de rendering uit te voeren. Dit biedt uitstekende ondersteuning voor auteurs van webinhoud om pagina&#39;s samen te stellen die eenvoudig aan hun vereisten kunnen worden aangepast.

De voordelen van deze flexibiliteit worden duidelijk in toepassingen met een groot aantal verschillende inhoudselementen, of wanneer u pagina&#39;s nodig hebt die gemakkelijk kunnen worden aangepast. Met name wanneer het uitvoeren van een systeem van het Beheer van de Inhoud van het Web zoals WCM in de AEM oplossing.

Zie [Sling binnen 15 minuten detecteren](https://sling.apache.org/documentation/getting-started/discover-sling-in-15-minutes.html) voor de eerste stappen voor het ontwikkelen met Sling.

In het volgende diagram wordt de resolutie van het script Sling uitgelegd: het toont hoe te om van HTTP- verzoek aan inhoudsknoop, van inhoudsknoop aan middeltype, van middeltype aan manuscript te krijgen en welke scripting variabelen beschikbaar zijn.

![Scriptresolutie voor Apache Sling](assets/sling-cheatsheet-01.png)

Het volgende diagram verklaart alle verborgen, maar krachtige, verzoekparameters u kunt gebruiken wanneer het behandelen van SlingPostServlet, de standaardmanager voor alle verzoeken van de POST die u eindeloze opties voor het creëren, het wijzigen, het schrappen, het kopiëren en het bewegen van knopen in de bewaarplaats geeft.

![De SlingPostServlet gebruiken](assets/sling-cheatsheet-02.png)

### Verdelen is inhoud centraal {#sling-is-content-centric}

Sling is *inhoudcentric*. Dit betekent dat de verwerking wordt geconcentreerd op de inhoud aangezien elk (HTTP) verzoek op inhoud in de vorm van een middel JCR (een gegevensopslagplaats knoop) in kaart wordt gebracht:

* het eerste doel is de bron (JCR-knooppunt) die de inhoud in zijn bezit heeft
* ten tweede, wordt de vertegenwoordiging, of het manuscript, gevestigd van de middeleigenschappen in combinatie met bepaalde delen van het verzoek (b.v. selecteurs en/of de uitbreiding)

### RESTful Sling {#restful-sling}

Vanwege de inhoudgerichte filosofie implementeert Sling een REST-georiënteerde server en biedt Sling dus een nieuw concept in een webtoepassingsframework. De voordelen zijn:

* zeer RESTful, niet alleen op het oppervlak; bronnen en representaties zijn op de juiste wijze gemodelleerd binnen de server
* verwijdert een of meer gegevensmodellen

   * voorheen waren de volgende maatregelen nodig : URL-structuur, zakelijke objecten, DB-schema;
   * dit is nu beperkt tot : URL = resource = JCR-structuur

### URL-decompositie {#url-decomposition}

Bij Sling wordt de verwerking gestuurd door de URL van de gebruikersaanvraag. Dit bepaalt de inhoud die door de aangewezen manuscripten moet worden getoond. Hiervoor wordt informatie opgehaald uit de URL.

Als we de volgende URL analyseren:

```xml
https://myhost/tools/spy.printable.a4.html/a/b?x=12
```

We kunnen het opsplitsen in samengestelde delen:

| protocol | host | inhoudspad | kiezer(s) | extension |  | achtervoegsel |  | param(en) |
|---|---|---|---|---|---|---|---|---|
| https:// | myhost | gereedschappen/spion | .printable.a4. | html | / | a/b | ? | x=12 |

**** protocolHTTP

**** hostName van de website.

**content** pathPath specifying the content to be rendered. wordt gebruikt in combinatie met de extensie; in dit voorbeeld vertalen ze naar tools/spy.html.

**kiezer(s)** gebruikt voor alternatieve methoden om de inhoud te renderen; in dit voorbeeld een printervriendelijke versie in A4-indeling.

**** extensionContent-indeling; geeft ook het script op dat moet worden gebruikt voor rendering.

**** suffixCan be used to specify additional information.

**param(en)** Alle parameters die vereist zijn voor dynamische inhoud.

#### Van URL naar inhoud en scripts {#from-url-to-content-and-scripts}

Op basis van deze beginselen:

* de afbeelding gebruikt het inhoudspad dat uit de aanvraag is geëxtraheerd om de bron te zoeken
* wanneer het aangewezen middel wordt gevestigd, wordt het sling middeltype gehaald, en gebruikt om van het manuscript de plaats te bepalen dat voor het teruggeven van de inhoud moet worden gebruikt

De onderstaande afbeelding illustreert het gebruikte mechanisme, dat in de volgende secties nader zal worden besproken.

![chlimage_1-86](assets/chlimage_1-86a.png)

Met Sling, specificeert u welk manuscript een bepaalde entiteit teruggeeft (door het `sling:resourceType` bezit in de knoop te plaatsen JCR). Dit mechanisme biedt meer vrijheid dan één waarin het script de gegevensentiteiten benadert (zoals een SQL-instructie in een PHP-script zou doen) omdat een resource meerdere uitvoeringen kan hebben.

#### Aanvragen toewijzen aan bronnen {#mapping-requests-to-resources}

Het verzoek wordt uitgesplitst en de nodige informatie wordt ingewonnen. De repository wordt gezocht naar de gevraagde resource (content node):

* first Sling controleert of een knooppunt bestaat op de locatie die in de aanvraag is opgegeven; bijv. `../content/corporate/jobs/developer.html`
* als er geen knooppunt wordt gevonden, wordt de extensie verwijderd en wordt de zoekopdracht herhaald; bijv. `../content/corporate/jobs/developer`
* Als er geen knooppunt wordt gevonden, retourneert Sling de http-code 404 (Not Found).

Met Sling kunnen andere zaken dan JCR-knooppunten ook bronnen zijn, maar dit is een geavanceerde functie.

### Script {#locating-the-script} zoeken

Wanneer de aangewezen bron (inhoudsknoop) wordt gevestigd, wordt **sling middeltype** gehaald. Dit is een pad dat zoekt naar het script dat moet worden gebruikt voor het renderen van de inhoud.

Het pad dat wordt opgegeven door `sling:resourceType` kan als volgt zijn:

* absoluut
* relatief, ten opzichte van een configuratieparameter

   Relatieve paden worden aanbevolen door Adobe omdat ze de draagbaarheid verhogen.

Alle Sling-scripts worden opgeslagen in submappen van `/apps` of `/libs`, die in deze volgorde worden doorzocht (zie [Componenten en andere elementen aanpassen](/help/sites-developing/dev-guidelines-bestpractices.md#customizing-components-and-other-elements)).

Een paar andere punten die u kunt opmerken zijn:

* Wanneer de methode (GET, POST) vereist is, wordt deze in hoofdletters opgegeven volgens de HTTP-specificatie, bijvoorbeeld job.POST.esp (zie hieronder).
* verschillende scriptengines worden ondersteund :

   * HTML (HTML Template Language - voorkeur van Adobe Experience Manager en aanbevolen sjabloonsysteem voor de server voor HTML): `.html`
   * ECMAScript (JavaScript) Pages (uitvoering op de server): `.esp, .ecma`
   * Java Server Pages (serveruitvoering): `.jsp`
   * Java Servlet Compiler (uitvoering op de server): `.java`
   * JavaScript-sjablonen (uitvoering op de client): `.jst`

De lijst van manuscriptmotoren die door de bepaalde instantie van AEM worden gesteund zijn vermeld op de Console van het Beheer van de Felix ( `http://<host>:<port>/system/console/slingscripting`).

Daarnaast ondersteunt Apache Sling integratie met andere populaire scriptengines (zoals Groovy, JRuby, Freemarker) en biedt Apache Sling een manier om nieuwe scriptengines te integreren.

Met behulp van het bovenstaande voorbeeld, als `sling:resourceType` `hr/jobs` dan is voor:

* GET/HEAD-aanvragen en URL&#39;s die eindigen op .html (standaardaanvraagtypen, standaardindeling)

   Het script zal /apps/hr/jobs/jobs.esp zijn; het laatste gedeelte van de tekenreeks:resourceType vormt de bestandsnaam.

* POST-aanvragen (alle aanvraagtypen behalve GET/HEAD, de methodenaam moet in hoofdletters staan)

   POST wordt gebruikt in de scriptnaam.

   Het script is `/apps/hr/jobs/jobs.POST.esp`.

* URL&#39;s in andere indelingen, niet eindigend met .html

   Bijvoorbeeld `../content/corporate/jobs/developer.pdf`

   Het script is `/apps/hr/jobs/jobs.pdf.esp`; het achtervoegsel wordt toegevoegd aan de manuscriptnaam.

* URL&#39;s met kiezers

   Kiezers kunnen worden gebruikt om dezelfde inhoud in een andere indeling weer te geven. Bijvoorbeeld een printervriendelijke versie, een rss-feed of een overzicht.

   Als we naar een printervriendelijke versie kijken waarin de kiezer *print* kan zijn; zoals in `../content/corporate/jobs/developer.print.html`

   Het script is `/apps/hr/jobs/jobs.print.esp`; de kiezer wordt toegevoegd aan de scriptnaam.

* Als er geen sling:resourceType is gedefinieerd, dan:

   * het inhoudspad wordt gebruikt om naar een geschikt script te zoeken (als het op pad gebaseerde ResourceTypeProvider actief is).

      Het script voor `../content/corporate/jobs/developer.html` genereert bijvoorbeeld een zoekopdracht in `/apps/content/corporate/jobs/`.

   * het primaire knooppunttype zal worden gebruikt.

* Als er helemaal geen script wordt gevonden, wordt het standaardscript gebruikt.

   De standaardvertoning wordt momenteel ondersteund als normale tekst (.txt), HTML (.html) en JSON (.json), die allemaal de eigenschappen van het knooppunt (correct opgemaakt) vermelden. De standaardvertoning voor de extensie .res, of aanvragen zonder een aanvraagextensie, is de bron te spool (waar mogelijk).
* Voor http-foutafhandeling (codes 403 of 404) wordt met Sling gezocht naar een script op:

   * de locatie /apps/sling/servlet/errorhandler voor [aangepaste scripts](/help/sites-developing/customizing-errorhandler-pages.md)
   * of de locatie van de standaardscripts /libs/sling/servlet/errorhandler/403.esp of 404.esp.

Als er meerdere scripts van toepassing zijn voor een bepaalde aanvraag, wordt het script met de beste overeenkomst geselecteerd. Hoe specifieker een match is, hoe beter dat is; met andere woorden, de meer selecteur past beter aan, ongeacht om het even welke verzoekuitbreiding of methodenamen.

Neem bijvoorbeeld een verzoek om toegang tot de bron
`/content/corporate/jobs/developer.print.a4.html`
van het type
`sling:resourceType="hr/jobs"`

Ervan uitgaande dat de volgende lijst met scripts op de juiste locatie staat:

1. `GET.esp`
1. `jobs.esp`
1. `html.esp`
1. `print.esp`
1. `print.html.esp`
1. `print/a4.esp`
1. `print/a4/html.esp`
1. `print/a4.html.esp`

Vervolgens zou de volgorde van voorkeur (8) - (7) - (6) - (5) - (4) - (3) - (2) - (1) zijn.

Naast de middeltypes (hoofdzakelijk die door het `sling:resourceType` bezit worden bepaald) is er ook het middel super type. Dit wordt over het algemeen vermeld door het `sling:resourceSuperType` bezit. Deze super types worden ook overwogen wanneer het proberen om een manuscript te vinden. Het voordeel van hulpmiddelsuper types is dat zij een hiërarchie van middelen kunnen vormen waar het standaardmiddeltype `sling/servlet/default` (dat door standaardservlets wordt gebruikt) effectief de wortel is.

Het resource super type van een middel kan op twee manieren worden bepaald:

* door de eigenschap `sling:resourceSuperType` van de bron.
* door de eigenschap `sling:resourceSuperType` van het knooppunt waarnaar `sling:resourceType` wijst.

Bijvoorbeeld:

* /

   * a
   * b

      * sling:resourceSuperType = a
   * c

      * sling:resourceSuperType = b
   * x

      * sling:resourceType = c
   * y

      * sling:resourceType = c
      * sling:resourceSuperType = a




De typehiërarchie van:

* `/x`
   * is `[ c, b, a, <default>]`
* while for `/y`
   * de hiërarchie is `[ c, a, <default>]`

Dit komt doordat `/y` de eigenschap `sling:resourceSuperType` heeft, terwijl `/x` dit niet doet en daarom wordt het supertype ervan ontleend aan het type resource.

#### Sling-scripts kunnen niet rechtstreeks {#sling-scripts-cannot-be-called-directly} worden aangeroepen

Binnen Verschuiving, kunnen de manuscripten niet direct worden geroepen aangezien dit het strikte concept van een REST server zou breken; u zou middelen en vertegenwoordiging mengen.

Als u de vertegenwoordiging (het manuscript) direct roept u het middel binnen uw manuscript verbergt, zodat weet het kader (het Schrapen) niet meer over het. Zo verliest u bepaalde eigenschappen:

* automatische afhandeling van andere http-methoden dan GET, waaronder:

   * POST, PUT, DELETE die met een sling standaardimplementatie worden behandeld
   * het `POST.jsp`-script in uw sling:resourceType-locatie

* uw codearchitectuur niet meer zo schoon en zo duidelijk gestructureerd is als zou moeten zijn; van primordiaal belang voor grootschalige ontwikkeling

### Verschuivende API {#sling-api}

Dit gebruikt het Sling API-pakket, org.apache.sling.&amp;ast; en tagbibliotheken.

### Verwijzen naar bestaande elementen met sling:include {#referencing-existing-elements-using-sling-include}

Een laatste overweging is de noodzaak om naar bestaande elementen in de scripts te verwijzen.

Complexere scripts (samengevoegde scripts) moeten mogelijk toegang krijgen tot meerdere bronnen (bijvoorbeeld navigatie, zijbalk, voettekst, elementen van een lijst) en dit doen door de *resource* op te nemen.

Hiervoor kunt u de sling gebruiken:include(&quot;/&lt;path>/&lt;resource>&quot;) opdracht. Dit omvat in feite de definitie van de resource waarnaar wordt verwezen, zoals in de volgende instructie die verwijst naar een bestaande definitie voor het renderen van afbeeldingen:

```xml
%><sling:include resourceType="geometrixx/components/image/img"/><%
```

## OSGI {#osgi}

OSGi bepaalt een architectuur voor het ontwikkelen en het opstellen van modulaire toepassingen en bibliotheken (het is ook genoemd geworden het Dynamische Systeem van de Module voor Java). De containers OSGi staan u toe om uw toepassing in individuele modules (zijn jar dossiers met extra meta-informatie en geroepen bundels in terminologie OSGi) te breken en de onderlinge afhankelijkheden te beheren met:

* diensten die binnen de container worden uitgevoerd
* een contract tussen de container en uw toepassing

Deze diensten en contracten verstrekken een architectuur die individuele elementen toelaat om elkaar voor samenwerking dynamisch te ontdekken.

Een OSGi-framework biedt u vervolgens dynamisch laden/verwijderen, configureren en beheren van deze bundels, zonder dat u opnieuw moet starten.

>[!NOTE]
>
>Volledige informatie over OSGi-technologie is te vinden op de [OSGi-website](https://www.osgi.org).
>
>De pagina Basisonderwijs bevat met name een verzameling presentaties en zelfstudies.

Deze architectuur staat u toe om het Verkopen met toepassing specifieke modules uit te breiden. Sling, en daarom CQ5, gebruikt [Apache Felix](https://felix.apache.org/) implementatie van OSGI (Open Services Gateway-initiatief) en is gebaseerd op de specificaties van versie 4.2 van het Platform OSGi Service. Het zijn beide inzamelingen van bundels OSGi die binnen een kader OSGi lopen.

Hierdoor kunt u de volgende handelingen uitvoeren op elk van de pakketten in uw installatie:

* installeren
* start
* stoppen
* update
* verwijderen
* zie de huidige status
* toegang tot meer gedetailleerde informatie (bv. symbolische naam, versie, locatie, enz.) over de specifieke bundels

Zie [de Webconsole](/help/sites-deploying/web-console.md), [OSGI-configuratie](/help/sites-deploying/configuring-osgi.md) en [OSGi Configuration Settings](/help/sites-deploying/osgi-configuration-settings.md) voor meer informatie.

## Ontwikkelingsobjecten in AEM omgeving {#development-objects-in-the-aem-environment}

De volgende zaken zijn van belang voor ontwikkeling:

**** ItemAn punt is of een knoop of een bezit.

Voor gedetailleerde informatie over het manipuleren van voorwerpen van het Punt, verwijs naar [Javadocs](https://docs.adobe.com/docs/en/spec/javax.jcr/javadocs/jcr-2.0/javax/jcr/Item.html) van de Interface javax.jcr.Item

**Node (en de bijbehorende eigenschappen)** Nodes en hun eigenschappen worden gedefinieerd in de JCR API 2.0-specificatie (JSR 283). Ze slaan inhoud, objectdefinities, scripts en andere gegevens op.

Met knooppunten wordt de inhoudsstructuur gedefinieerd en in de eigenschappen ervan worden de feitelijke inhoud en metagegevens opgeslagen.

Inhoudsknooppunten sturen de rendering. Bij Sling wordt het inhoudsknooppunt van de binnenkomende aanvraag opgehaald. The property sling:resourceType of this node points to the Sling rendering component to be used.

Een knooppunt, dat een JCR-naam is, wordt ook wel een resource genoemd in de Sling-omgeving.

Als u bijvoorbeeld de eigenschappen van het huidige knooppunt wilt ophalen, kunt u de volgende code in uw script gebruiken:

`PropertyIterator properties = currentNode.getProperties();`

Met currentNode als het huidige knoopvoorwerp.

Raadpleeg [Javadocs](https://docs.adobe.com/docs/en/spec/javax.jcr/javadocs/jcr-2.0/javax/jcr/Node.html) voor meer informatie over het manipuleren van Node-objecten.

**** WidgetIn AEM alle gebruikersinvoer wordt beheerd door widgets. Deze worden vaak gebruikt om het bewerken van een stuk inhoud te besturen.

Dialoogvensters worden samengesteld door Widgets te combineren.

AEM is ontwikkeld met behulp van de ExtJS-bibliotheek met widgets.

**DialogA-** dialoogvenster is een speciaal type widget.

Voor het bewerken van inhoud gebruikt AEM dialoogvensters die zijn gedefinieerd door de ontwikkelaar van de toepassing. In deze sjablonen wordt een reeks widgets gecombineerd, zodat de gebruiker alle velden en handelingen krijgt die nodig zijn om de gerelateerde inhoud te bewerken.

Dialoogvensters worden ook gebruikt voor het bewerken van metagegevens en door verschillende beheergereedschappen.

**De** softwarecomponent ComponentA is een systeemelement dat een vooraf bepaalde dienst of een gebeurtenis aanbiedt, en met andere componenten kan communiceren.

Binnen AEM wordt een component vaak gebruikt om de inhoud van een middel terug te geven. Wanneer de bron een pagina is, wordt de component die de bron rendert, een component op hoofdniveau of een component Pagecomponent genoemd. Een component hoeft echter geen inhoud te renderen en hoeft niet te zijn gekoppeld aan een specifieke bron. een navigatiecomponent geeft bijvoorbeeld informatie over meerdere bronnen weer.

De definitie van een component omvat:,

* de code die wordt gebruikt om de inhoud te renderen
* een dialoogvenster voor de gebruikersinvoer en de configuratie van de resulterende inhoud.

**** TemplateA malplaatje is de basis voor een specifiek type van pagina. Wanneer u een pagina maakt op het tabblad Websites, moet de gebruiker een sjabloon selecteren. De nieuwe pagina wordt dan gecreeerd door dit malplaatje te kopiëren.

Een sjabloon is een hiërarchie van knooppunten die dezelfde structuur heeft als de pagina die moet worden gemaakt, maar zonder daadwerkelijke inhoud.

Hiermee worden de paginacomponent gedefinieerd die wordt gebruikt om de pagina en de standaardinhoud (primaire inhoud op hoofdniveau) weer te geven. De inhoud definieert hoe deze wordt gerenderd als AEM inhoudcentrisch is.

**Component Pagina (bovenste component)** De component die moet worden gebruikt om de pagina weer te geven.

**Pagina** A is een &#39;exemplaar&#39; van een sjabloon.

Een pagina heeft een hiërarchieknooppunt van het type cq:Page en een inhoudsknooppunt van het type cq:PageContent. De eigenschap sling:resourceType van de inhoudnode wijst naar de paginacomponent die wordt gebruikt voor het weergeven van de pagina.

Als u bijvoorbeeld de naam van de huidige pagina wilt ophalen, kunt u de volgende code in uw script gebruiken:

S`tring pageName = currentPage.getName();`

Met currentPage wordt het huidige paginaobject. Raadpleeg [Javadocs](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/day/cq/wcm/api/Page.html) voor meer informatie over het bewerken van paginaobjecten.

**Page** ManagerHet paginabeheer is een interface die methoden biedt voor bewerkingen op paginaniveau.

Bijvoorbeeld, om de bevattende pagina van een middel te krijgen, kunt u de volgende code in uw manuscript gebruiken:

Page myPage = pageManager.getConcontainingPage(myResource);

Met pageManager die het voorwerp van de paginamanager en myResource zijn een middelvoorwerp. Raadpleeg [Javadocs](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/day/cq/wcm/api/PageManager.html) voor meer informatie over de methoden die worden geleverd door de paginabeheerder.

## Structuur in de opslagplaats {#structure-within-the-repository}

De volgende lijst geeft een overzicht van de structuur die u in de repository zult zien.

>[!CAUTION]
>
>Wijzigingen in deze structuur, of in de bestanden daarin, moeten met de nodige voorzichtigheid worden aangebracht.
>
>Wijzigingen zijn nodig tijdens de ontwikkeling, maar zorg ervoor dat u de gevolgen van alle wijzigingen volledig begrijpt.

>[!CAUTION]
>
>U mag niets in de `/libs` weg veranderen. Voor configuratie en andere veranderingen kopieer het punt van `/libs` aan `/apps` en breng om het even welke veranderingen binnen `/apps` aan.

* `/apps`

   Toepassingsgerelateerd; bevat componentdefinities die specifiek zijn voor uw website. De componenten die u ontwikkelt kunnen op uit de dooscomponenten worden gebaseerd beschikbaar bij `/libs/foundation/components`.

* `/content`

   Inhoud die voor uw website is gemaakt.

* `/etc`

* `/home`

   Informatie over gebruiker en groep.

* `/libs`

   Bibliotheken en definities die tot de kern van AEM behoren. De submappen in `/libs` vertegenwoordigen de functies die buiten het vak AEM, zoals zoeken of replicatie. De inhoud in `/libs` zou niet moeten worden gewijzigd aangezien het de manier beïnvloedt AEM werkt. Functies die specifiek zijn voor uw website, moeten worden ontwikkeld onder `/apps` (zie [Componenten en andere elementen aanpassen](/help/sites-developing/dev-guidelines-bestpractices.md#customizing-components-and-other-elements)).

* `/tmp`

   Tijdelijke werkruimte.

* `/var`

   bestanden die door het systeem worden gewijzigd en bijgewerkt; zoals auditlogboeken, statistieken, gebeurtenisafhandeling.

## Omgevingen {#environments}

Met AEM bestaat een productieomgeving vaak uit twee verschillende typen instanties: en [Auteur- en publicatieinstanties](/help/sites-deploying/deploy.md#author-and-publish-installs).

## De verzender {#the-dispatcher}

De Dispatcher is een Adobe voor zowel caching als/of taakverdeling. Meer informatie vindt u onder [Dispatcher](https://helpx.adobe.com/experience-manager/dispatcher/user-guide.html).

## FileVault (bronrevisiesysteem) {#filevault-source-revision-system}

FileVault biedt uw JCR-opslagplaats van bestandssysteemtoewijzing en versiebeheer. Het kan worden gebruikt om AEM ontwikkelingsprojecten met volledige steun voor het opslaan van en het versioning van projectcode, inhoud, configuraties etc., in standaardversiecontrolesystemen (bijvoorbeeld, Subversion) te beheren.

Raadpleeg de documentatie [FileVault](/help/sites-developing/ht-vlttool.md) voor gedetailleerde informatie.

## Workflows {#workflows}

Uw inhoud is vaak onderhevig aan organisatorische processen, waaronder stappen zoals goedkeuring en aftekening door verschillende deelnemers. Deze processen kunnen als werkschema&#39;s worden vertegenwoordigd, [bepaald en ontwikkeld binnen AEM](/help/sites-developing/workflows-models.md), dan toegepast op [aangewezen inhoudspagina&#39;s](/help/sites-administering/workflows.md) of [digitale activa](/help/assets/assets-workflow.md) zoals vereist.

De Workflow Engine wordt gebruikt om de implementatie van uw workflows en de daarop volgende toepassing op uw inhoud te beheren.

## Beheer van meerdere sites {#multi-site-management}

Met MSM (Multi Site Manager) kunt u eenvoudig meerdere websites beheren die gemeenschappelijke inhoud delen. Met MSM kunt u relaties tussen de sites definiëren, zodat wijzigingen in de inhoud van de ene site automatisch worden gerepliceerd in andere sites.

Websites worden bijvoorbeeld vaak in meerdere talen aangeboden voor internationaal publiek. Wanneer het aantal sites in dezelfde taal laag is (drie tot vijf), is een handmatig proces voor het synchroniseren van inhoud over sites mogelijk. Zodra het aantal sites echter toeneemt of wanneer meerdere talen bij het proces betrokken zijn, wordt het efficiënter om het proces te automatiseren.

* U kunt op efficiënte wijze verschillende taalversies van een website beheren.
* Een of meer sites automatisch bijwerken op basis van een bronsite:

   * Een algemene basisstructuur afdwingen en gemeenschappelijke inhoud op meerdere sites gebruiken.
   * Maximaliseer het gebruik van beschikbare middelen.
   * Houd een algemeen uiterlijk.
   * De inspanningen concentreren op het beheren van de inhoud die tussen de plaatsen verschilt.

Zie [Beheer van meerdere sites](/help/sites-administering/msm.md) voor meer informatie.
