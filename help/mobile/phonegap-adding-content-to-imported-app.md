---
title: Is uw hybride app gereed voor AEM Mobile?
seo-title: Is uw hybride app gereed voor AEM Mobile?
description: Volg deze pagina om meer te weten te komen over hrybrid-apps. Een toepassing in AEM bestaat meestal uit twee delen. De 'shell' en 'content' en deze pagina bieden meer inzicht in deze onderwerpen.
seo-description: Volg deze pagina om meer te weten te komen over hrybrid-apps. Een toepassing in AEM bestaat meestal uit twee delen. De 'shell' en 'content' en deze pagina bieden meer inzicht in deze onderwerpen.
uuid: cbcce3fa-9100-46ea-9f24-931b42666709
contentOwner: User
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/MOBILE
topic-tags: developing-adobe-phonegap-enterprise
discoiquuid: b7fd7954-f2a5-402d-b259-e18b5a618be9
pagetitle: Is your hybrid app ready for AEM Mobile?
translation-type: tm+mt
source-git-commit: a3c303d4e3a85e1b2e794bec2006c335056309fb

---


# Is uw hybride app gereed voor AEM Mobile?{#is-your-hybrid-app-ready-for-aem-mobile}

>[!NOTE]
>
>Adobe adviseert gebruikend de Redacteur van het KUUROORD voor projecten die op kader-gebaseerde cliënt-zijteruggeven van enige paginatoepassing (b.v. Reageren) vereisen. [Meer](/help/sites-developing/spa-overview.md)informatie.

Dus u hebt uw Hybride PhoneGap- of Cordova-app geïmporteerd in AEM, wat nu? Waarschijnlijk zult u authorable inhoud aan uw app willen toevoegen. Hiervoor hebt u een algemeen inzicht in de structuur van een AEM-app nodig. Een toepassing in AEM bestaat meestal uit twee delen. De &#39;shell&#39; en &#39;content&#39;. De &#39;shell&#39; bestaat uit de statische delen van uw app. zoals de PhoneGap-configuratiebestanden, het app-framework en de navigatiebesturingselementen. De inhoud van het archief dat u hebt geïmporteerd, wordt opgeslagen als onderdeel van de shell. In de context van dit document is de shell alle niet-AEM authored inhoud van uw Hybrid PhoneGap app die door de toepassingsontwikkelaar wordt gebouwd.

Inhoud verwijst naar de componenten, sjablonen en geschreven pagina&#39;s die zijn gemaakt in AEM die door de AEM Developer zijn gemaakt. Inhoud wordt gecategoriseerd als inhoud voor ontwikkelaars of als geschreven inhoud. Componenten, ontwerpen en paginasjablonen worden beschouwd als ontwikkelinhoud omdat ze zijn gemaakt door een ontwikkelaar. auteur-inhoud zijn pagina&#39;s die met de componenten en de malplaatjes zijn gebouwd. Deze worden typisch gedaan door een ontwerper of een telleraar.

Voor het toevoegen van authored AEM-pagina&#39;s aan uw Hybride-app is coördinatie tussen de ontwikkelaar van de app en de AEM-ontwikkelaar vereist. Overal in de app waar u geschreven inhoud wilt toevoegen, moet de ontwikkelaar van de app deze pagina&#39;s ordenen in een structuur die kan worden overschreven in AEM. De ontwikkelaar van de app moet de AEM-ontwikkelaar de paden kunnen geven naar de plaats waar de AEM-geschreven inhoud moet worden toegevoegd en vervolgens een tijdelijke aanduiding in de Hybride-app kunnen opgeven die wordt vervangen nadat de AEM-ontwikkelaar de pagina-inhoud heeft geschreven.

We gebruiken de AEM Marketing Cloud om de uitleg te kunnen volgen: AEM Mobile Hybrid Reference om de concepten uit te leggen. De Hybride Reference-app bestaat uit een welkomstpagina met een zijmenu.

![chlimage_1-76](assets/chlimage_1-76.png)

In dit voorbeeld gaan we de welkomstpagina van de toepassing schrijven. Bekijk de bron [https://github.com/Adobe-Marketing-Cloud-Apps/aem-mobile-hybrid-reference/blob/master/hybrid-app/www/js/app.js#L75](https://github.com/Adobe-Marketing-Cloud-Apps/aem-mobile-hybrid-reference/blob/master/hybrid-app/www/js/app.js#L75). We zien dat de ontwikkelaar van de app een welkomstpagina heeft gedefinieerd en een sjabloon heeft verschaft voor de pagina die door de app wordt weergegeven. Hiervoor moeten de ontwikkelaar van de app en de AEM-ontwikkelaar coördineren. Het pad naar de welkomstpaginasjabloon in de Hybride Reference App is gedefinieerd als &#39;&#39;content/mobileapps/hybrid-reference-app/en/welcome.template.html&#39;&#39;. Dit pad is uiterst belangrijk omdat de AEM-ontwikkelaar zijn welkomstpagina in de AEM-opslagplaats met hetzelfde pad zal samenstellen.

![chlimage_1-77](assets/chlimage_1-77.png)

Het is belangrijk dat de hybride app en de inhoud die in AEM is gemaakt hetzelfde pad gebruiken, omdat we afhankelijk zijn van de mogelijkheid om inhoud te bedekken met Content Sync om nieuwe pagina&#39;s toe te voegen aan de Hybride app. Wanneer de hybride app in AEM wordt geïmporteerd als onderdeel van het importproces, worden de configuraties Content Sync ingesteld.

![chlimage_1-78](assets/chlimage_1-78.png)

Wanneer u Bron downloaden vanaf het dashboard van de app gebruikt, worden deze ContentSync-scripts uitgevoerd om een archief van uw hybride app samen te stellen.

![chlimage_1-79](assets/chlimage_1-79.png)

ContentSync wordt eerst in &#39;shell&#39; van de app opgehaald, waar alle toepassingen die inhoud van de Hybrid-app hebben ontwikkeld, worden opgeslagen en vervolgens in de &#39;content&#39; van de app worden opgehaald. Als er nu pagina&#39;s in de shell zijn die hetzelfde pad hebben als in &#39;content&#39;, worden de pagina&#39;s onder &#39;shell&#39; (vervangen) door de pagina&#39;s onder &#39;content&#39;. Met andere woorden in het voorbeeld voor de hybride referentie-app als we in AEM een pagina maken die hetzelfde pad heeft als &#39;&#39;content/mobileapps/hybrid-reference-app/en/welcome.template.html&#39;&#39; wanneer ContentSync wordt uitgevoerd, wordt deze pagina bedekt die deel uitmaakte van de Hybride Reference-app met wat zich op die locatie in AEM bevindt. De overlay wordt verzorgd door ContentSync, zodat de updates voor de app met inhoud die in AEM is geschreven, er naadloos uitzien en er geen nieuwe build van de app nodig is. Als u de app uitvoert, wordt de welkomstpagina als volgt weergegeven:

![chlimage_1-80](assets/chlimage_1-80.png)
