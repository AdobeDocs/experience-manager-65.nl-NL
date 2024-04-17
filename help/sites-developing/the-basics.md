---
title: AEM kernconcepten
description: Een overzicht van de kernconcepten van hoe Adobe Experience Manager (AEM) gestructureerd is en hoe zich bovenop het te ontwikkelen met inbegrip van het begrijpen van JCR, Sling, OSGi, de Verzender, werkschema's, en MSM.
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: introduction
content-type: reference
exl-id: f6f32290-422e-4037-89d8-d9f414332e8e
solution: Experience Manager, Experience Manager Sites
feature: Developing
role: Developer
source-git-commit: 66db4b0b5106617c534b6e1bf428a3057f2c2708
workflow-type: tm+mt
source-wordcount: '3251'
ht-degree: 0%

---

# AEM kernconcepten {#aem-core-concepts}

>[!NOTE]
>
>Alvorens in de kernconcepten van Adobe Experience Manager (AEM) te gaan, beveelt de Adobe aan de WKND-zelfstudie in te vullen in de [Aan de slag met het ontwikkelen van AEM Sites](/help/sites-developing/getting-started.md) document. Het omvat een overzicht van het AEM ontwikkelingsproces en een inleiding tot kernconcepten.

## Vereisten voor ontwikkeling op AEM {#prerequisites-for-developing-on-aem}

U hebt de volgende vaardigheden nodig om zich bovenop AEM te ontwikkelen:

* Basiskennis van webtoepassingstechnieken, waaronder:

   * het verzoek-antwoord (XMLHttpRequest / XMLHttpResponse)-cyclus
   * HTML
   * CSS
   * JavaScript

* De werkkennis van de Server van de Ervaring (CRX), met inbegrip van de Ontdekkingsreiziger van de Inhoud
* Voor het ontwikkelen in klassieke UI, wordt de basiskennis van JSP (de Pagina&#39;s van JavaServer) met inbegrip van de capaciteit om eenvoudige JSP voorbeelden te begrijpen en te wijzigen ook vereist.

U wordt ook aangeraden de [Richtlijnen en beste praktijken](/help/sites-developing/dev-guidelines-bestpractices.md).

## Java™ Content Repository {#java-content-repository}

De JCR-standaard (Java™ Content Repository), [JSR 283](https://developer.adobe.com/experience-manager/reference-materials/spec/jcr/2.0/index.html), geeft een leveranciersonafhankelijke en implementatieonafhankelijke manier aan om inhoud bidirectioneel te benaderen op granulair niveau in een inhoudsopslagplaats.

Specificatie lead is in handen van Adobe Research (Zwitserland) AG.

De [JCR API 2.0](https://developer.adobe.com/experience-manager/reference-materials/spec/javax.jcr/javadocs/jcr-2.0/index.html) pakket, javax.jcr.&amp;ast; wordt gebruikt voor directe toegang tot en bewerking van inhoud in de opslagplaats.

## Experience Server (CRX) en Jackrabbit {#experience-server-crx-and-jackrabbit}

De Server van de Ervaring verstrekt de Diensten van de Ervaring die AEM worden voortgebouwd, en die kunnen worden gebruikt om douanetoepassingen te bouwen, en het sluit de Inhoudsbewaarplaats in van de Inhoud op Jackrabbit wordt gebaseerd.

[Apache Jackrabbit](https://jackrabbit.apache.org/jcr/index.html) is een open bron, volledig conform, implementatie van JCR API 2.0.

## Verwerking van aanvraag voor verzending {#sling-request-processing}

### Inleiding tot verkoop {#introduction-to-sling}

AEM is gemaakt met [Sling](https://sling.apache.org/index.html), een Web-toepassing kader-gebaseerd op de principes van REST die gemakkelijke ontwikkeling van inhoud-georiënteerde toepassingen verstrekken. Bij Sling wordt als gegevensopslagruimte een JCR-opslagplaats gebruikt, zoals Apache Jackrabbit of, indien AEM, de CRX Content Repository. Sling is toegevoegd aan de Apache Software Foundation - meer informatie is te vinden op Apache.

Met Verschuiving is het type inhoud dat moet worden gerenderd niet de eerste verwerkingsoverweging. De belangrijkste overweging is in plaats daarvan of de URL wordt omgezet in een inhoudsobject waarvoor vervolgens een script kan worden gevonden om de rendering uit te voeren. Dit biedt uitstekende ondersteuning voor auteurs van webinhoud om pagina&#39;s samen te stellen die eenvoudig aan hun vereisten kunnen worden aangepast.

De voordelen van deze flexibiliteit worden duidelijk in toepassingen met een groot aantal verschillende inhoudselementen, of wanneer u pagina&#39;s nodig hebt die gemakkelijk kunnen worden aangepast. Met name wanneer het uitvoeren van een systeem van het Beheer van de Inhoud van het Web zoals WCM in de AEM oplossing.

Zie [Ontdek de verkoop binnen 15 minuten](https://sling.apache.org/documentation/getting-started/discover-sling-in-15-minutes.html) voor de eerste stappen voor het ontwikkelen met Sling.

In het volgende diagram wordt de resolutie van het script Sling uitgelegd. Het toont hoe te om van HTTP- verzoek aan inhoudsknoop, van inhoudsknoop aan middeltype, van middeltype aan manuscript te krijgen, en welke scripting variabelen beschikbaar zijn.

![Scriptresolutie voor Apache Sling](assets/sling-cheatsheet-01.png)

Het volgende diagram verklaart alle verborgen, maar krachtige, verzoekparameters die u wanneer het behandelen van SlingPostServlet kunt gebruiken. Het omvat de standaardmanager voor alle verzoeken van de POST die u eindeloze opties voor het creëren van, het wijzigen van, het schrappen van, het kopiëren van, en het bewegen van knopen in de bewaarplaats geeft.

![De SlingPostServlet gebruiken](assets/sling-cheatsheet-02.png)

### Verdelen is Content Centric {#sling-is-content-centric}

Verkopen is *inhoudgericht*. Dit betekent dat de verwerking wordt geconcentreerd op de inhoud aangezien elk (HTTP) verzoek op inhoud in de vorm van een middel JCR (een gegevensopslagplaats knoop) in kaart wordt gebracht:

* het eerste doel is de bron (JCR-knooppunt) die de inhoud in zijn bezit heeft
* ten tweede bevindt de representatie, of het script, zich in de eigenschappen resource die worden gecombineerd met bepaalde delen van de aanvraag (bijvoorbeeld kiezers en/of de extensie)

### RESTful Sling {#restful-sling}

Vanwege de inhoudgerichte filosofie implementeert Sling een REST-georiënteerde server en biedt Sling dus een nieuw concept in een webtoepassingsframework. De voordelen zijn:

* RESTful, niet alleen op de oppervlakte; de middelen en de vertegenwoordiging worden correct gemodelleerd binnen de server
* verwijdert een of meer gegevensmodellen

   * voorheen was het volgende nodig: URL-structuur, zakelijke objecten, DB-schema;
   * dit is nu beperkt tot: URL = resource = JCR-structuur

### URL-decompositie {#url-decomposition}

Bij Sling wordt de verwerking aangedreven door de URL van het gebruikersverzoek. Dit bepaalt de inhoud die door de aangewezen manuscripten moet worden getoond. Hiervoor wordt informatie opgehaald uit de URL.

Als u de volgende URL analyseert:

```xml
https://myhost/tools/spy.printable.a4.html/a/b?x=12
```

U kunt het onderverdelen in zijn samengestelde delen:

| protocol | host | inhoudspad | kiezers | extension |  | achtervoegsel |  | param |
|---|---|---|---|---|---|---|---|---|
| https:// | myhost | gereedschappen/spion | .printable.a4. | html | / | a/b | ? | x=12 |

**protocol** HTTP

**host** Naam van de website.

**inhoudspad** Pad waarin de inhoud wordt opgegeven die moet worden weergegeven. Wordt gebruikt met de extensie. In dit voorbeeld worden ze vertaald naar `tools/spy.html`.

**kiezers** Wordt gebruikt voor alternatieve methoden om de inhoud weer te geven; in dit voorbeeld een printervriendelijke versie in A4-indeling.

**extension** Indeling van inhoud; geeft ook het script op dat moet worden gebruikt voor rendering.

**achtervoegsel** Kan worden gebruikt om aanvullende informatie op te geven.

**param** Alle parameters die vereist zijn voor dynamische inhoud.

#### Van URL naar inhoud en scripts {#from-url-to-content-and-scripts}

Op basis van deze beginselen:

* de afbeelding gebruikt het inhoudspad dat uit de aanvraag is geëxtraheerd om de bron te zoeken
* wanneer het aangewezen middel wordt gevestigd, wordt het sling middeltype gehaald, en gebruikt om van het manuscript te bepalen dat voor het teruggeven van de inhoud moet worden gebruikt

De onderstaande afbeelding illustreert het gebruikte mechanisme, dat in de volgende secties nader wordt beschreven.

![chlimage_1-86](assets/chlimage_1-86a.png)

Met Verschuiven geeft u op welk script een bepaalde entiteit wordt gerenderd (door het dialoogvenster `sling:resourceType` eigenschap in het knooppunt JCR). Dit mechanisme biedt meer vrijheid dan één waarin het script de gegevensentiteiten benadert (zoals een SQL-instructie in een PHP-script zou doen) omdat een resource meerdere uitvoeringen kan hebben.

#### Verzoeken om toewijzing aan bronnen {#mapping-requests-to-resources}

Het verzoek wordt uitgesplitst en de nodige informatie wordt ingewonnen. De repository wordt gezocht naar de gevraagde resource (content node):

* First Sling controleert of een knooppunt bestaat op de locatie die in de aanvraag is opgegeven, bijvoorbeeld `../content/corporate/jobs/developer.html`
* als er geen knooppunt wordt gevonden, wordt de extensie verwijderd en wordt de zoekopdracht herhaald, bijvoorbeeld `../content/corporate/jobs/developer`
* Als er geen knooppunt wordt gevonden, retourneert Sling de http-code 404 (Not Found).

Met Sling kunnen andere zaken dan JCR-knooppunten ook bronnen zijn, maar dit is een geavanceerde functie.

### Script zoeken {#locating-the-script}

Wanneer de juiste resource (content node) is gevonden, wordt de **slingermiddeltype** wordt geëxtraheerd. Dit is een pad dat zoekt naar het script dat moet worden gebruikt voor het renderen van de inhoud.

Het pad dat wordt opgegeven door de `sling:resourceType` kunnen:

* absoluut
* ten opzichte van een configuratieparameter

  Relatieve paden worden door de Adobe aanbevolen omdat ze de draagbaarheid verhogen.

Alle verkoopscripts worden opgeslagen in submappen van `/apps` of `/libs`, die in deze volgorde wordt doorzocht (zie [Componenten en andere elementen aanpassen](/help/sites-developing/dev-guidelines-bestpractices.md#customizing-components-and-other-elements)).

Een paar andere punten die u kunt opmerken zijn:

* Wanneer de methode (GET, POST) wordt vereist, wordt deze in hoofdletters opgegeven zoals in de HTTP-specificatie, bijvoorbeeld job.POST.esp (zie hieronder).
* verschillende scriptengines worden ondersteund :

   * HTL (Sjabloontaal HTML - Adobe Experience Manager heeft het voorkeur en aanbevolen Sjabloonsysteem aan serverzijde voor HTML): `.html`
   * ECMAScript (JavaScript) Pages (serveruitvoering): `.esp, .ecma`
   * Java™ Server Pages (serveruitvoering): `.jsp`
   * Java™ Servlet Compiler (serveruitvoering): `.java`
   * JavaScript-sjablonen (uitvoering op de client): `.jst`

De lijst met scriptengines die door de opgegeven AEM worden ondersteund, wordt weergegeven in de Felix Management Console ( `http://<host>:<port>/system/console/slingscripting`).

Apache Sling ondersteunt ook integratie met andere populaire scriptengines (bijvoorbeeld Groovy, JRuby, Freemarker) en biedt een manier om nieuwe scriptengines te integreren.

Met het bovenstaande voorbeeld, als `sling:resourceType` is `hr/jobs` vervolgens voor:

* GET/HEAD-aanvragen en URL&#39;s die eindigen op .html (standaardaanvraagtypen, standaardindeling)

  Het script is /apps/hr/jobs/jobs.esp. Het laatste gedeelte van de tekenreeks:resourceType vormt de bestandsnaam.

* Aanvragen voor POSTEN (alle aanvraagtypen behalve GET/HEAD, de naam van de methode moet in hoofdletters staan)

  POST wordt gebruikt in de manuscriptnaam.

  Het script is `/apps/hr/jobs/jobs.POST.esp`.

* URL&#39;s in andere indelingen, niet eindigend met .html

  Bijvoorbeeld: `../content/corporate/jobs/developer.pdf`

  Het script is `/apps/hr/jobs/jobs.pdf.esp`; het achtervoegsel wordt toegevoegd aan de scriptnaam.

* URL&#39;s met kiezers

  Kiezers kunnen worden gebruikt om dezelfde inhoud in een andere indeling weer te geven. Bijvoorbeeld een printervriendelijke versie, een rss feed of een samenvatting.

  Als u een printervriendelijke versie bekijkt waarin de kiezer mogelijk *afdrukken*, zoals in `../content/corporate/jobs/developer.print.html`

  Het script is `/apps/hr/jobs/jobs.print.esp`; de kiezer wordt aan de scriptnaam toegevoegd.

* Als er geen sling:resourceType is gedefinieerd, dan:

   * het inhoudspad wordt gebruikt om naar een aangewezen manuscript (als op weg-gebaseerde ResourceTypeProvider actief is) te zoeken.

     Het script voor bijvoorbeeld `../content/corporate/jobs/developer.html` zou een zoekopdracht genereren in `/apps/content/corporate/jobs/`.

   * het primaire knooppunttype wordt gebruikt.

* Als er geen script wordt gevonden, wordt het standaardscript gebruikt.

  De standaardvertoning wordt ondersteund als normale tekst (.txt), HTML (.html) en JSON (.json), die allemaal de eigenschappen van het knooppunt vermelden (correct opgemaakt). De standaardvertoning voor de extensie .res, of aanvragen zonder een aanvraagextensie, is de bron te spool (waar mogelijk).
* Bij http-foutafhandeling (codes 403 of 404) zoekt Sling naar een script op:

   * de locatie /apps/sling/servlet/errorhandler voor [aangepaste scripts](/help/sites-developing/customizing-errorhandler-pages.md)
   * of de locatie van de standaardscripts /libs/sling/servlet/errorhandler/403.esp of 404.esp.

Als er meerdere scripts van toepassing zijn voor een bepaalde aanvraag, wordt het script met de beste overeenkomst geselecteerd. Hoe specifieker een overeenkomst is, des te beter deze is. Met andere woorden, hoe meer kiezer het beste aanpast, ongeacht of de aanvraagextensie of methodenamen overeenkomen.

Neem bijvoorbeeld een verzoek om toegang tot de bron
`/content/corporate/jobs/developer.print.a4.html`
van het type
`sling:resourceType="hr/jobs"`

Ervan uitgaande dat u de volgende lijst met scripts op de juiste locatie hebt:

1. `GET.esp`
1. `jobs.esp`
1. `html.esp`
1. `print.esp`
1. `print.html.esp`
1. `print/a4.esp`
1. `print/a4/html.esp`
1. `print/a4.html.esp`

Vervolgens zou de volgorde van voorkeur (8) - (7) - (6) - (5) - (4) - (3) - (2) - (1) zijn.

Naast de typen bronnen (die voornamelijk worden gedefinieerd door de `sling:resourceType` eigenschap), is er ook het resource super type. Dit wordt aangegeven door de `sling:resourceSuperType` eigenschap. Deze super types worden ook overwogen wanneer het proberen om een manuscript te vinden. Het voordeel van resource super types is dat zij een hiërarchie van middelen kunnen vormen waar het standaardmiddeltype `sling/servlet/default` (wordt gebruikt door de standaardservlets) is in feite de wortel.

Het resource super type van een middel kan op twee manieren worden bepaald:

* door de `sling:resourceSuperType` eigenschap van de bron.
* door de `sling:resourceSuperType` eigenschap van het knooppunt waaraan de `sling:resourceType` punten.

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
   * de hiërarchie `[ c, a, <default>]`

Dit komt omdat `/y` heeft de `sling:resourceSuperType` onroerend goed `/x` niet en daarom wordt zijn supertype genomen van zijn middeltype.

#### Sling-scripts kunnen niet rechtstreeks worden aangeroepen {#sling-scripts-cannot-be-called-directly}

Binnen Verschuiven, kunnen de manuscripten niet direct worden geroepen aangezien dit het strikte concept van een server van het SPEL zou breken; u zou middelen en vertegenwoordiging mengen.

Als u de vertegenwoordiging (het manuscript) direct roept u het middel binnen uw manuscript verbergt, zodat weet het kader (het Schrapen) niet meer over het. Zo verliest u bepaalde eigenschappen:

* automatische afhandeling van andere http-methoden dan GET, waaronder:

   * POST, PUT, DELETE die met een sling standaardimplementatie wordt behandeld
   * de `POST.jsp` script in uw tekenreeks:resourceType-locatie

* uw codearchitectuur is niet meer zo schoon en zo duidelijk gestructureerd als het zou moeten zijn; van primordiaal belang voor grootschalige ontwikkeling

### Verkopen-API {#sling-api}

Dit gebruikt het Sling API-pakket, org.apache.sling.&amp;ast; en tagbibliotheken.

### Verwijzen naar bestaande elementen met gebruik van sling:include {#referencing-existing-elements-using-sling-include}

Een laatste overweging is de noodzaak om naar bestaande elementen in de scripts te verwijzen.

Complexere scripts (samengevoegde scripts) moeten toegang hebben tot meerdere bronnen (navigatie, zijbalk, voettekst, elementen van een lijst, bijvoorbeeld) en dit doen door de *resource*.

Hiervoor gebruikt u de sling:include(&quot;/&lt;path>/&lt;resource>&quot;). Dit omvat in feite de definitie van de resource waarnaar wordt verwezen, zoals in de volgende instructie die verwijst naar een bestaande definitie voor het renderen van afbeeldingen:

```xml
%><sling:include resourceType="geometrixx/components/image/img"/><%
```

## OSGI {#osgi}

OSGi bepaalt een architectuur voor het ontwikkelen en het opstellen van modulaire toepassingen en bibliotheken (het is ook genoemd geworden het Dynamische Systeem van de Module voor Java™). De containers OSGi laten u uw toepassing in individuele modules (die jar dossiers met extra meta-informatie zijn en geroepen bundels in terminologie OSGi) breken en de onderlinge afhankelijkheden beheren met:

* diensten die binnen de container worden uitgevoerd
* een contract tussen de container en uw toepassing

Deze diensten en contracten verstrekken een architectuur die individuele elementen toelaat om elkaar voor samenwerking dynamisch te ontdekken.

Een OSGi-framework biedt u vervolgens dynamisch laden/verwijderen, configureren en beheren van deze bundels, zonder dat u opnieuw moet starten.

>[!NOTE]
>
>Volledige informatie over OSGi-technologie is te vinden op de website [OSGi-website](https://www.osgi.org).
>
>De pagina Basisonderwijs bevat met name een verzameling presentaties en zelfstudies.

Deze architectuur laat u het Verkopen met toepassing-specifieke modules uitbreiden. Bij Sling, en dus bij CQ5, wordt de optie [Apache Felix](https://felix.apache.org/documentation/index.html) implementatie van OSGI (Open Services Gateway-initiatief) en is gebaseerd op de specificaties van versie 4.2 van het OSGi Service Platform Release 4. Het zijn beide inzamelingen van bundels OSGi die binnen een kader OSGi lopen.

Hierdoor kunt u de volgende handelingen uitvoeren op elk van de pakketten in uw installatie:

* installeren
* start
* stoppen
* update
* verwijderen
* zie de status
* toegang tot meer gedetailleerde informatie (bijvoorbeeld symbolische naam, versie en locatie) over de specifieke bundels

Zie [de webconsole](/help/sites-deploying/web-console.md), [OSGI-configuratie](/help/sites-deploying/configuring-osgi.md), en [OSGi-configuratie-instellingen](/help/sites-deploying/osgi-configuration-settings.md) voor meer informatie .

## Ontwikkelingsobjecten in de AEM {#development-objects-in-the-aem-environment}

De volgende zaken zijn van belang voor ontwikkeling:

**Item** Een item is een knooppunt of een eigenschap.

Voor gedetailleerde informatie over het manipuleren van voorwerpen van het Punt, zie [Java™-documenten](https://developer.adobe.com/experience-manager/reference-materials/spec/javax.jcr/javadocs/jcr-2.0/javax/jcr/Item.html) van de interface javax.jcr.Item

**Knooppunt (en de eigenschappen ervan)** Knooppunten en hun eigenschappen worden gedefinieerd in de JCR API 2.0-specificatie (JSR 283). Ze slaan inhoud, objectdefinities, scripts en andere gegevens op.

Met knooppunten wordt de inhoudsstructuur gedefinieerd en in de eigenschappen ervan worden de feitelijke inhoud en metagegevens opgeslagen.

Inhoudsknooppunten sturen de rendering. Bij Sling wordt het inhoudsknooppunt van de binnenkomende aanvraag opgehaald. The property sling:resourceType of this node points to the Sling rendering component to be used.

Een knooppunt, dat een JCR-naam is, wordt ook wel een resource genoemd in de Sling-omgeving.

Als u bijvoorbeeld de eigenschappen van het huidige knooppunt wilt ophalen, kunt u de volgende code in uw script gebruiken:

`PropertyIterator properties = currentNode.getProperties();`

The currentNode being the current node object.

Voor meer informatie over het manipuleren van voorwerpen van de Knoop, zie [Java™-documenten](https://developer.adobe.com/experience-manager/reference-materials/spec/javax.jcr/javadocs/jcr-2.0/javax/jcr/Node.html).

**Widget** In AEM wordt alle gebruikersinvoer beheerd door widgets. Deze worden vaak gebruikt om het bewerken van een stuk inhoud te besturen.

Dialoogvensters worden samengesteld door Widgets te combineren.

AEM is ontwikkeld met de ExtJS-bibliotheek met widgets.

**Dialoog** Een dialoogvenster is een speciaal type widget.

Voor het bewerken van inhoud gebruikt AEM dialoogvensters die zijn gedefinieerd door de ontwikkelaar van de toepassing. In deze sjablonen wordt een reeks widgets gecombineerd, zodat de gebruiker alle velden en handelingen krijgt die nodig zijn om de gerelateerde inhoud te bewerken.

Dialoogvensters worden ook gebruikt voor het bewerken van metagegevens en door verschillende beheergereedschappen.

**Component** Een softwarecomponent is een systeemelement dat een vooraf bepaalde dienst of een gebeurtenis aanbiedt, en met andere componenten kan communiceren.

Binnen AEM, wordt een component vaak gebruikt om de inhoud van een middel terug te geven. Wanneer de bron een pagina is, wordt de component die de bron rendert, een Bovenste component of een component Pagina genoemd. Een component hoeft echter geen inhoud te renderen en hoeft niet te zijn gekoppeld aan een specifieke bron. Een navigatiecomponent geeft bijvoorbeeld informatie weer over meerdere bronnen.

De definitie van een component omvat het volgende:

* de code die wordt gebruikt om de inhoud te renderen
* een dialoogvenster voor de gebruikersinvoer en de configuratie van de resulterende inhoud.

**Sjabloon** Een sjabloon is de basis voor een specifiek type pagina. Wanneer de gebruiker een pagina op het tabblad Websites maakt, moet deze een sjabloon selecteren. De nieuwe pagina wordt dan gecreeerd door dit malplaatje te kopiëren.

Een sjabloon is een hiërarchie van knooppunten die dezelfde structuur heeft als de pagina die moet worden gemaakt, maar zonder daadwerkelijke inhoud.

Hiermee worden de paginacomponent gedefinieerd die wordt gebruikt om de pagina en de standaardinhoud (primaire inhoud op hoofdniveau) weer te geven. De inhoud definieert hoe deze wordt gerenderd als AEM inhoudcentrisch is.

**Paginacomponent (bovenste component)** De component die moet worden gebruikt om de pagina weer te geven.

**Pagina** Een pagina is een &#39;exemplaar&#39; van een sjabloon.

Een pagina heeft een hiërarchieknooppunt van het type cq:Page en een inhoudsknooppunt van het type cq:PageContent. The property sling:resourceType of the content node points to the Page Component used for rendering the page.

Als u bijvoorbeeld de naam van de huidige pagina wilt ophalen, kunt u de volgende code in uw script gebruiken:

S`tring pageName = currentPage.getName();`

TcurrentPage is het huidige paginaobject. Zie de klasse [Java™-documenten](https://developer.adobe.com/experience-manager/reference-materials/6-5/javadoc/com/day/cq/wcm/api/Page.html).

**Paginabeheer** Het paginabeheer is een interface die methoden biedt voor bewerkingen op paginaniveau.

Bijvoorbeeld, om de bevattende pagina van een middel te krijgen, kunt u de volgende code in uw manuscript gebruiken:

Page myPage = pageManager.getConcontainingPage(myResource);

De pageManager die het voorwerp van de paginamanager zijn, en myResource een middelvoorwerp. Zie voor meer informatie over de methoden die worden geleverd door de paginabeheerder de [Java™-documenten](https://developer.adobe.com/experience-manager/reference-materials/6-5/javadoc/com/day/cq/wcm/api/PageManager.html).

## Structuur in de opslagplaats {#structure-within-the-repository}

De volgende lijst geeft een overzicht van de structuur die u in de repository ziet.

>[!CAUTION]
>
>Wijzigingen in deze structuur, of in de bestanden daarin, moeten met de nodige voorzichtigheid worden aangebracht.
>
>Wijzigingen zijn nodig tijdens de ontwikkeling, maar zorg ervoor dat u de gevolgen van alle wijzigingen volledig begrijpt.

>[!CAUTION]
>
>Wijzig niets in de `/libs` pad. Voor configuratie en andere veranderingen, kopieer het punt van `/libs` tot `/apps` en brengt alle wijzigingen aan in `/apps`.

* `/apps`

  Toepassingsgerelateerd; bevat componentdefinities die specifiek zijn voor uw website. De componenten die u ontwikkelt kunnen op uit de vakcomponenten worden gebaseerd beschikbaar bij `/libs/foundation/components`.

* `/content`

  Inhoud die voor uw website is gemaakt.

* `/etc`

* `/home`

  Informatie over gebruiker en groep.

* `/libs`

  Bibliotheken en definities die tot de kern van AEM behoren. De submappen in `/libs` vertegenwoordigen de uit-van-de-doos AEM eigenschappen zoals onderzoek of replicatie. De inhoud in `/libs` mogen niet worden gewijzigd omdat dit van invloed is op de manier waarop AEM werkt. Functies die specifiek zijn voor uw website, moeten worden ontwikkeld onder `/apps` (zie [Componenten en andere elementen aanpassen](/help/sites-developing/dev-guidelines-bestpractices.md#customizing-components-and-other-elements)).

* `/tmp`

  Tijdelijke werkruimte.

* `/var`

  Bestanden die door het systeem worden gewijzigd en bijgewerkt, zoals auditlogboeken, statistieken, gebeurtenisafhandeling.

## Omgevingen {#environments}

Met AEM bestaat een productieomgeving vaak uit twee verschillende typen instanties: en [Auteur- en publicatie-instanties](/help/sites-deploying/deploy.md#author-and-publish-installs).

## De verzender {#the-dispatcher}

De Dispatcher is het gereedschap van de Adobe voor zowel caching als/of taakverdeling. Nadere informatie is te vinden onder [de verzender](https://experienceleague.adobe.com/docs/experience-manager-dispatcher/using/dispatcher.html).

## FileVault (systeem voor bronrevisie) {#filevault-source-revision-system}

FileVault biedt uw JCR-opslagplaats van bestandssysteemtoewijzing en versiebeheer. Het kan worden gebruikt om AEM ontwikkelingsprojecten met volledige steun voor het opslaan van en het versioning van projectcode, inhoud, configuraties, etc., in standaardversiecontrolesystemen (bijvoorbeeld, Subversion) te beheren.

Zie de [FileVault](/help/sites-developing/ht-vlttool.md) documentatie voor gedetailleerde informatie.

## Workflows {#workflows}

Uw inhoud is vaak onderhevig aan organisatorische processen, waaronder stappen zoals goedkeuring en aftekening door verschillende deelnemers. Deze processen kunnen als werkschema&#39;s worden vertegenwoordigd, [gedefinieerd en ontwikkeld binnen AEM](/help/sites-developing/workflows-models.md)en vervolgens toegepast op de [juiste inhoudspagina&#39;s](/help/sites-administering/workflows.md) of [digitale middelen](/help/assets/assets-workflow.md) zoals vereist.

De Workflow Engine wordt gebruikt om de implementatie van uw workflows en de daarop volgende toepassing op uw inhoud te beheren.

## Beheer van meerdere sites {#multi-site-management}

Met MSM (Multi Site Manager) kunt u eenvoudig meerdere websites beheren die gemeenschappelijke inhoud delen. Met MSM kunt u relaties tussen de sites definiëren, zodat wijzigingen in de inhoud van de ene site automatisch worden gerepliceerd in andere sites.

Websites worden bijvoorbeeld vaak in meerdere talen aangeboden voor internationaal publiek. Wanneer het aantal sites in dezelfde taal laag is (drie tot vijf), is een handmatig proces voor het synchroniseren van inhoud over sites mogelijk. Nochtans, wanneer het aantal plaatsen groeit of wanneer de veelvoudige talen betrokken zijn, wordt het efficiënter om het proces te automatiseren.

* Beheer efficiënt verschillende taalversies van een website.
* Een of meer sites automatisch bijwerken op basis van een bronsite:

   * Een algemene basisstructuur afdwingen en gemeenschappelijke inhoud op meerdere sites gebruiken.
   * Maximaliseer het gebruik van beschikbare middelen.
   * Houd een algemeen uiterlijk.
   * De inspanningen concentreren op het beheren van de inhoud die tussen de plaatsen verschilt.

Zie voor meer informatie [Beheer van meerdere sites](/help/sites-administering/msm.md).
