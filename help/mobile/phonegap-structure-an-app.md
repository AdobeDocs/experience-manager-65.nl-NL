---
title: Een app structureren
description: Volg deze pagina voor meer informatie over het maken van een structuur van een app. Op deze pagina wordt beschreven hoe u sjablonen en componenten kunt structureren, samen met informatie over JavaScript en CSS-clips.
contentOwner: User
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/MOBILE
topic-tags: developing-adobe-phonegap-enterprise
exl-id: f37f239f-065b-44f8-acb1-93485b713b49
source-git-commit: 9d497413d0ca72f22712581cf7eda1413eb8d643
workflow-type: tm+mt
source-wordcount: '871'
ht-degree: 0%

---

# Een app structureren{#structure-an-app}

>[!NOTE]
>
>De Adobe adviseert het gebruiken van de SPARedacteur voor projecten die op kader-gebaseerde cliënt-zijteruggeven van enige paginatoepassing (bijvoorbeeld, Reageren) vereisen. [Meer informatie](/help/sites-developing/spa-overview.md).

Een AEM Mobile-project omvat een aantal verschillende inhoudstypen, zoals pagina&#39;s, JavaScript- en CSS-clientbibliotheken, herbruikbare AEM componenten, configuraties van Content Sync en inhoud van de shell van de PhoneGap-app. Baseer uw nieuwe AEM Mobile-app op de [Starter Kit](https://github.com/Adobe-Marketing-Cloud-Apps/aem-phonegap-starter-kit) is een goede manier om alle verschillende soorten inhoud in onze aanbevolen structuur te krijgen om zowel draagbaarheid als onderhoudsgemak op lange termijn te verlichten.

## Pagina-inhoud {#page-content}

De pagina&#39;s van uw toepassing moeten zich onder /content/mobileapps bevinden, anders worden ze niet herkend door de AEM Mobile-console.

![chlimage_1-52](assets/chlimage_1-52.png)

Volgens AEM conventie moet de eerste pagina van uw app een omleiding zijn naar een van de onderliggende items die als standaardtaal van de app fungeren (en in zowel de gevallen Geometrixx als Starter Kit). De landinstellingspagina op hoofdniveau overerft doorgaans de &#39;splash-page&#39;-component (/libs/mobileapps/components/splash-page) die zorgt voor de initialisatie die nodig is voor de installatie van updates voor de synchronisatie van over-the-air inhoud (contentInit-code vindt u op /etc/clientlibs/mobile/content-sync/js/contentInit.js).

## Sjablonen en componenten {#templates-and-components}

De sjabloon- en componentcode voor uw app moeten in /apps/ staan&lt;brand name=&quot;&quot;>/&lt;app name=&quot;&quot;>. Conform de conventie moet u de sjabloon en de componentcode in /apps/ plaatsen&lt;brand name=&quot;&quot;>/&lt;app name=&quot;&quot;>. Dit patroon is bekend bij ontwikkelaars die al in AEM met Site hebben gewerkt. Dit wordt meestal gevolgd wanneer /apps/ standaard is vergrendeld op anonieme toegang in publicatieinstanties. Uw onbewerkte JSP-code is dus verborgen achter potentiële aanvallers.

Toepassingsspecifieke sjablonen kunnen alleen worden geconfigureerd om te worden weergegeven met de `allowedPaths` eigenschapknooppunt op de sjabloon zelf en de waarde ervan instellen op &#39;/content/mobileapps(/.&amp;ast;)?&#39; - of zelfs iets specifiekers als de sjabloon slechts voor één app bruikbaar mag zijn. De `allowedParents` en `allowedChildren` De eigenschappen kunnen ook voor fijnkorrelige controle worden gebruikt waarvan malplaatjes aan een auteur beschikbaar zijn die op waar wordt gebaseerd de nieuwe pagina wordt gecreeerd.

Als u een geheel nieuwe app-paginacomponent maakt, is het raadzaam de component `sling:resourceSuperType` eigenschap naar &#39;mobileapps/components/angular/ng-page&#39;. Hierdoor wordt uw pagina ingesteld voor zowel ontwerp als rendering als een app van één pagina, en kunt u .jsp-bestanden bedekken die mogelijk door de component moeten worden gewijzigd. Aangezien ng-page helemaal geen UI-framework bevat, eindigt een ontwikkelaar gewoonlijk met het bedekken van (ten minste) &#39;template.jsp&#39; (bedekt door /libs/mobileapps/components/angular/ng-page/template.jsp).

Aanvaardbare pagina-componenten die AngularJS willen gebruiken, hebben een equivalent `sling:resourceSuperType` component bij /libs/mobileapps/components/angular/ng-component die op dezelfde manier kan worden bedekt en aangepast.

## JavaScript- en CSS-clips {#javascript-and-css-clientlibs}

In clientbibliotheken zijn er een paar opties beschikbaar voor de ontwikkelaar van waar deze in de opslagplaats moeten worden geplaatst. Het volgende patroon wordt ter begeleiding aangeboden, maar is geen harde eis.

Als uw clientcode zelfstandig kan staan en geen betrekking heeft op een specifieke component van uw toepassing (dit betekent dat de code opnieuw kan worden gebruikt in andere toepassingen), raadt de Adobe aan de code op te slaan in /etc/clientlibs/&lt;brand name=&quot;&quot;>/&lt;lib name=&quot;&quot;>. Als de clientlib echter specifiek is voor één toepassing, kunt u deze nesten als een onderliggend element van het ontwerpknooppunt van uw app; /etc/designs/phonegap/&lt;brand name=&quot;&quot;>/&lt;app name=&quot;&quot;>/clientlibs. Gebruik de categorie van deze client niet met andere bibliotheken, maar sluit indien nodig andere bibliotheken in. Als u dit patroon volgt, hoeft de ontwikkelaar niet telkens nieuwe configuraties voor Content Sync toe te voegen wanneer een clientbibliotheek aan de app wordt toegevoegd, maar werkt u gewoon de eigenschap &#39;embeds&#39; van de ontwerpclient van de app bij. Kijk bijvoorbeeld naar het configuratieknooppunt voor Geometrixx clientlibs-all Content Sync op /content/phonegap/geometrixx-outdoor/en/jcr:content/pge-app/app-config/clientlibs-all.

Als uw clientcode nauw aan een specifieke component is gekoppeld, plaatst u die code in een clientbibliotheek die onder de locatie van de component is genest in /apps/ en sluit u de categorie in de client lib &#39;design&#39; van uw app in.

## PhoneGap-configuratie {#phonegap-configuration}

Elke AEM Mobile-app bevat een map die fungeert als host voor de configuratiebestanden die worden gebruikt door PhoneGap [opdrachtregelinterface](https://github.com/phonegap/phonegap-cli) en PhoneGap-build op `https://build.phonegap.com/` om van uw webinhoud een uitvoerbare toepassing te maken. In het voorbeeld Geometrixx bevindt deze map (content/content/phonegap/geometrixx-outdoor/shell/jcr:content/page-app/app-content) zich als onderdeel van de Shell; een ontwerpbeslissing omdat deze alleen inhoud bevat die niet via de lucht kan worden bijgewerkt, zoals plug-ins die betrekking hebben op apparaat-API&#39;s en de configuratie van de app zelf.

In deze map vindt u ook een aantal [Cordova hooks](https://cordova.apache.org/docs/en/dev/guide/appdev/hooks/index.html#Hooks%20Guide) die kunnen worden gebruikt om insteekmodules te installeren, bronbestanden op hun platformspecifieke locaties te plaatsen en andere acties die als onderdeel van de build moeten worden uitgevoerd. Opmerking: als alternatief voor het downloaden van elke insteekmodule als onderdeel van de build kunt u het patroon van de Kitchen Sink-app volgen en broncode voor de insteekmodule opnemen<!-- THIS URL IS 404 (https://github.com/blefebvre/aem-phonegap-kitchen-sink/tree/master/content/src/main/content/jcr_root/content/phonegap/kitchen-sink/shell/_jcr_content/pge-app/app-content/phonegap/plugins) --> met de rest van uw app-project.

## De volgende stappen {#the-next-steps}

Nadat u meer hebt geleerd over de structuur van de app, raadpleegt u [Apps maken en bewerken met App Console](/help/mobile/phonegap-apps-console.md).
