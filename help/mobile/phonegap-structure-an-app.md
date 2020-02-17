---
title: Een app structureren
seo-title: Een app structureren
description: Volg deze pagina voor meer informatie over het maken van een structuur van een app. Op deze pagina wordt beschreven hoe u sjablonen en componenten kunt structureren, samen met informatie over JavaScript en CSS-clips.
seo-description: Volg deze pagina voor meer informatie over het maken van een structuur van een app. Op deze pagina wordt beschreven hoe u sjablonen en componenten kunt structureren, samen met informatie over JavaScript en CSS-clips.
uuid: bf0e8b0c-a075-4847-b56d-de458715027c
contentOwner: User
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/MOBILE
topic-tags: developing-adobe-phonegap-enterprise
discoiquuid: c614a7ff-0d13-4407-bda0-c0a402a13dcd
translation-type: tm+mt
source-git-commit: a3c303d4e3a85e1b2e794bec2006c335056309fb

---


# Een app structureren{#structure-an-app}

>[!NOTE]
>
>Adobe adviseert gebruikend de Redacteur van het KUUROORD voor projecten die op kader-gebaseerde cliënt-zijteruggeven van enige paginatoepassing (b.v. Reageren) vereisen. [Meer](/help/sites-developing/spa-overview.md)informatie.

Een AEM Mobile-project omvat een uiteenlopende set inhoudstypen, zoals pagina&#39;s, JavaScript- en CSS-clientbibliotheken, herbruikbare AEM-componenten, configuraties voor inhoudssynchronisatie en inhoud van de PhoneGap-app-shell. Het baseren van uw nieuwe AEM Mobile-app op de [Starter Kit](https://github.com/Adobe-Marketing-Cloud-Apps/aem-phonegap-starter-kit) is een goede manier om alle verschillende typen inhoud in onze aanbevolen structuur te krijgen, zodat u op de lange termijn zowel draagbaarheid als onderhoudsgemak krijgt.

## Pagina-inhoud {#page-content}

De pagina&#39;s van uw toepassing moeten zich allemaal onder /content/mobileapps bevinden, anders worden ze niet herkend door de AEM Mobile-console.

![chlimage_1-52](assets/chlimage_1-52.png)

Volgens de AEM-conventie moet de eerste pagina van uw app een omleiding zijn naar een van de onderliggende items van de app die als standaardtaal voor de app fungeert (en in zowel de gevallen Geometrixx als Starter Kit). De landinstellingspagina op het hoogste niveau neemt doorgaans de elementen over van de stichting &#39;splash-page&#39; (/libs/mobileapps/components/splash-page) die zorg dragen voor de initialisatie die nodig is om de installatie van updates voor de synchronisatie van over-the-air inhoud te ondersteunen (contentInit-code vindt u op /etc/clientlibs/mobile/content-sync/js/contentInit.js).

## Sjablonen en componenten {#templates-and-components}

De sjabloon- en componentcode voor uw app moet zich bevinden in /apps/&lt;merknaam>/&lt;toepassingsnaam>. Conform de conventies moet u de sjabloon en de componentcode in /apps/&lt;merknaam>/&lt;toepassingsnaam> plaatsen. Dit patroon is bekend bij ontwikkelaars die al met Site in AEM hebben gewerkt. Dit wordt meestal gevolgd wanneer /apps/ standaard is vergrendeld op anonieme toegang in publicatieinstanties. Uw onbewerkte JSP-code is dan ook verborgen achter potentiële aanvallers.

Toepassingsspecifieke sjablonen kunnen alleen worden geconfigureerd om te worden weergegeven door het `allowedPaths` eigenschapknooppunt in de sjabloon zelf te gebruiken en de waarde ervan in te stellen op &#39;/content/mobileapps(/.&amp;ast;)?&#39; - of zelfs iets specifiekers als de sjabloon slechts voor één app bruikbaar mag zijn. De `allowedParents` en `allowedChildren` eigenschappen kunnen ook worden gebruikt voor zeer fijnkorrelige controle waarvan de malplaatjes aan een auteur beschikbaar zullen zijn die op wordt gebaseerd waar de nieuwe pagina wordt gecreeerd.

Als u een geheel nieuwe app-paginacomponent maakt, is het raadzaam de `sling:resourceSuperType` eigenschap ervan in te stellen op &#39;mobileapps/components/angular/ng-page&#39;. Hierdoor wordt de pagina ingesteld voor zowel ontwerpen als weergeven als een app van één pagina, en kunt u .jsp-bestanden bedekken die mogelijk door de component moeten worden gewijzigd. Aangezien ng-page helemaal geen UI-framework bevat, zal een ontwikkelaar gewoonlijk &#39;template.jsp&#39; (bedekt door /libs/mobileapps/components/angular/ng-page/template.jsp) bedekken.

Authorable page components, die gebruik willen maken van AngularJS, hebben een equivalente `sling:resourceSuperType` component die zich op /libs/mobileapps/components/angular/ng-component bevindt en die op dezelfde manier kan worden bedekt en aangepast.

## JavaScript- en CSS-clips {#javascript-and-css-clientlibs}

Wanneer het over cliëntbibliotheken komt, zijn er een paar opties beschikbaar aan de ontwikkelaar van waar te om hen in de bewaarplaats te plaatsen. Het volgende patroon wordt ter begeleiding aangeboden, maar is geen harde eis.

Als uw clientside-code zelfstandig kan staan en geen betrekking heeft op een specifieke component van uw toepassing (dit kan worden hergebruikt in andere toepassingen), raden we u aan deze code op te slaan in /etc/clientlibs/&lt;merknaam>/&lt;lib name>. Als de clientlib echter specifiek is voor één toepassing, kunt u deze nesten als een onderliggend knooppunt van het ontwerpknooppunt van uw app. /etc/designs/phonegap/&lt;merknaam>/&lt;toepassingsnaam>/clientlibs. De categorie van deze clientlib mag niet door andere bibliotheken worden gebruikt en moet zo nodig worden gebruikt om andere bibliotheken in te sluiten. Als u deze patronen volgt, hoeft de ontwikkelaar niet telkens nieuwe configuraties voor Content Sync toe te voegen wanneer een clientbibliotheek aan de app wordt toegevoegd, maar werkt u gewoon de eigenschap &#39;embeds&#39; van de ontwerpclient van de app bij. Neem bijvoorbeeld een blik op het configuratieknooppunt Geometrixx clientlibs-all Content Sync op /content/phonegap/geometrixx-outdoor/en/jcr:content/pge-app/app-config/clientlibs-all.

Als uw clientcode nauw aan een specifieke component is gekoppeld, plaatst u die code in een clientbibliotheek die onder de locatie van de component is genest in /apps/ en sluit u de categorie in de client lib &#39;design&#39; van uw app in.

## PhoneGap-configuratie {#phonegap-configuration}

Elke AEM Mobile-app bevat een directory die de configuratiebestanden host die worden gebruikt door de PhoneGap- [opdrachtregelinterface](https://github.com/phonegap/phonegap-cli) en de [PhoneGap-build](https://build.phonegap.com/) om van uw webinhoud een uitvoerbare toepassing te maken. In het Geometrixx-voorbeeld bevindt deze map (content/content/phonegap/geometrixx-outdoor/shell/jcr:content/pge-app/app-content) zich als onderdeel van de Shell. een ontwerpbesluit dat is genomen omdat het alleen inhoud bevat die niet via de lucht kan worden bijgewerkt, zoals plug-ins die betrekking hebben op apparaat-API&#39;s en de configuratie van de app zelf.

In deze directory vindt u ook een aantal [Cordova-haken](https://cordova.apache.org/docs/en/edge/guide_appdev_hooks_index.md.html#Hooks%20Guide) die kunnen worden gebruikt om insteekmodules te installeren, bronbestanden op hun platformspecifieke locaties te plaatsen en andere acties die als onderdeel van de build moeten worden uitgevoerd. Opmerking: als alternatief voor het downloaden van elke insteekmodule als onderdeel van de build, kunt u het patroon van de Kitchen Sink-app volgen en broncode [voor de insteekmodule](https://github.com/blefebvre/aem-phonegap-kitchen-sink/tree/master/content/src/main/content/jcr_root/content/phonegap/kitchen-sink/shell/_jcr_content/pge-app/app-content/phonegap/plugins) opnemen bij de rest van uw app-project.

## De volgende stappen {#the-next-steps}

Als u meer hebt geleerd over de structuur van de app, raadpleegt u [Apps maken en bewerken met App Console](/help/mobile/phonegap-apps-console.md).
