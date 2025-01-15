---
title: Een app structureren
description: Volg deze pagina voor meer informatie over het maken van een structuur van een app. Deze pagina beschrijft hoe u sjablonen en componenten kunt structureren samen met informatie over JavaScript en CSS-clips.
contentOwner: User
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/MOBILE
topic-tags: developing-adobe-phonegap-enterprise
exl-id: f37f239f-065b-44f8-acb1-93485b713b49
solution: Experience Manager
feature: Mobile
role: Admin
source-git-commit: 2dae56dc9ec66f1bf36bbb24d6b0315a5f5040bb
workflow-type: tm+mt
source-wordcount: '850'
ht-degree: 0%

---

# Een app structureren{#structure-an-app}

{{ue-over-mobile}}

Een AEM Mobile-project omvat een aantal verschillende inhoudssoorten, waaronder pagina&#39;s, JavaScript- en CSS-clientbibliotheken, herbruikbare AEM componenten, configuraties voor inhoudssynchronisatie en inhoud van de shell van de PhoneGap-app. Het baseren van uw nieuwe AEM Mobile app op de [ Uitrusting van de Aanzet ](https://github.com/Adobe-Marketing-Cloud-Apps/aem-phonegap-starter-kit) is een goede manier om alle verschillende types van inhoud in onze geadviseerde structuur te krijgen om zowel portabiliteit als onderhoudbaarheid op de lange termijn te verlichten.

## Pagina-inhoud {#page-content}

De pagina&#39;s van uw toepassing moeten zich onder /content/mobileapps bevinden, anders worden ze niet herkend door de AEM Mobile-console.

![ chlimage_1-52 ](assets/chlimage_1-52.png)

Volgens AEM conventie moet de eerste pagina van uw app een omleiding zijn naar een van de onderliggende items die als standaardtaal van de app fungeren (en in zowel de gevallen Geometrixx als Starter Kit). De landinstellingspagina op hoofdniveau overerft doorgaans de &#39;splash-page&#39;-component (/libs/mobileapps/components/splash-page) die zorgt voor de initialisatie die nodig is voor de installatie van updates voor de synchronisatie van over-the-air inhoud (contentInit-code vindt u op /etc/clientlibs/mobile/content-sync/js/contentInit.js).

## Sjablonen en componenten {#templates-and-components}

De sjabloon- en componentcode voor uw app moeten in /apps/&lt;merknaam>/&lt;toepassingsnaam> staan. Conform de conventies moet u de sjabloon en de componentcode in /apps/&lt;merknaam>/&lt;toepassingsnaam> plaatsen. Dit patroon is bekend bij ontwikkelaars die al in AEM met Site hebben gewerkt. Dit wordt meestal gevolgd wanneer /apps/ standaard is vergrendeld op anonieme toegang in publicatieinstanties. Uw onbewerkte JSP-code is dus verborgen achter potentiële aanvallers.

Toepassingsspecifieke sjablonen kunnen alleen worden geconfigureerd om te worden weergegeven met het eigenschapknooppunt `allowedPaths` op de sjabloon zelf en door de waarde ervan in te stellen op &#39;/content/mobileapps(/.&amp;ast;)?&#39; - of zelfs iets specifiekers als de sjabloon slechts voor één app bruikbaar mag zijn. De eigenschappen `allowedParents` en `allowedChildren` kunnen ook worden gebruikt voor fijnkorrelige besturingselementen waarvan sjablonen beschikbaar zijn voor een auteur op basis van de plaats waar de nieuwe pagina wordt gemaakt.

Als u een geheel nieuwe app-paginacomponent maakt, wordt aangeraden de eigenschap `sling:resourceSuperType` ervan in te stellen op &#39;mobileapps/components/angular/ng-page&#39;. Hierdoor wordt uw pagina ingesteld voor zowel ontwerp als rendering als een app van één pagina, en kunt u .jsp-bestanden bedekken die mogelijk door de component moeten worden gewijzigd. Aangezien ng-page helemaal geen UI-framework bevat, eindigt een ontwikkelaar gewoonlijk met het bedekken van (ten minste) &#39;template.jsp&#39; (bedekt door /libs/mobileapps/components/angular/ng-page/template.jsp).

Authorable page components, die AngularJS willen gebruiken, hebben een equivalent `sling:resourceSuperType` -component op /libs/mobileapps/components/angular/ng-component dat op dezelfde manier kan worden bedekt en aangepast.

## JavaScript en CSS-clips {#javascript-and-css-clientlibs}

In clientbibliotheken zijn er een paar opties beschikbaar voor de ontwikkelaar van waar deze in de opslagplaats moeten worden geplaatst. Het volgende patroon wordt ter begeleiding aangeboden, maar is geen harde eis.

Als uw clientside-code zelfstandig kan staan en geen betrekking heeft op een specifieke component van uw toepassing (dit kan in andere toepassingen worden hergebruikt), raadt de Adobe aan de code op te slaan in /etc/clientlibs/&lt;merknaam>/&lt;lib name>. Als de clientlib echter specifiek is voor één toepassing, kunt u deze nesten als een onderliggend element van het ontwerpknooppunt van uw app; /etc/designs/phonegap/&lt;merknaam>/&lt;toepassingsnaam>/clientlibs. Gebruik de categorie van deze client niet met andere bibliotheken, maar sluit indien nodig andere bibliotheken in. Als u dit patroon volgt, hoeft de ontwikkelaar niet telkens nieuwe configuraties voor Content Sync toe te voegen wanneer een clientbibliotheek aan de app wordt toegevoegd, maar werkt u gewoon de eigenschap &#39;embeds&#39; van de ontwerpclient van de app bij. Kijk bijvoorbeeld naar het configuratieknooppunt voor Geometrixx clientlibs-all Content Sync op /content/phonegap/geometrixx-outdoor/en/jcr:content/pge-app/app-config/clientlibs-all.

Als uw clientcode nauw aan een specifieke component is gekoppeld, plaatst u die code in een clientbibliotheek die onder de locatie van de component is genest in /apps/ en sluit u de categorie in de client lib &#39;design&#39; van uw app in.

## PhoneGap-configuratie {#phonegap-configuration}

Elke app van AEM Mobile bevat een folder die gastheren de configuratiedossiers die door de interface van de bevellijn PhoneGap [ ](https://github.com/phonegap/phonegap-cli) worden gebruikt en PhoneGap bouwt bij `https://build.phonegap.com/` om uw Webinhoud in een runnable toepassing te veranderen. In het voorbeeld Geometrixx bevindt deze map (content/content/phonegap/geometrixx-outdoor/shell/jcr:content/page-app/app-content) zich als onderdeel van de Shell; een ontwerpbeslissing omdat deze alleen inhoud bevat die niet via de lucht kan worden bijgewerkt, zoals plug-ins die betrekking hebben op apparaat-API&#39;s en de configuratie van de app zelf.

In deze folder, vindt u ook sommige [ haken Cordova ](https://cordova.apache.org/docs/en/dev/guide/appdev/hooks/index.html#Hooks%20Guide) die kunnen worden gebruikt om stoppen te installeren, middeldossiers in hun platform-specifieke plaatsen, en andere acties te plaatsen die als deel van de bouwstijl zouden moeten worden uitgevoerd. Opmerking: als alternatief voor het downloaden van elke insteekmodule als onderdeel van de build, kunt u het patroon van de Kitchen Sink-app volgen en broncode voor insteekmodules opnemen <!-- THIS URL IS 404 (https://github.com/blefebvre/aem-phonegap-kitchen-sink/tree/master/content/src/main/content/jcr_root/content/phonegap/kitchen-sink/shell/_jcr_content/pge-app/app-content/phonegap/plugins) --> met de rest van uw app-project.

## De volgende stappen {#the-next-steps}

Nadat u over de Structuur van app leert, zie [ Creërend en het Uitgeven van Apps gebruikend de Console van de App ](/help/mobile/phonegap-apps-console.md).
