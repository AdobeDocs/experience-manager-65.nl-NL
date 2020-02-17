---
title: Sjablonen en componenten maken en toevoegen
seo-title: Sjablonen en componenten maken en toevoegen
description: Volg deze pagina voor meer informatie over het maken en toevoegen van sjablonen en componenten aan uw app. De pagina gebruikt Geometrixx Unlimited App als de app die een voorbeeld-app-sjabloon en paginasjablonen bevat.
seo-description: Volg deze pagina voor meer informatie over het maken en toevoegen van sjablonen en componenten aan uw app. De pagina gebruikt Geometrixx Unlimited App als de app die een voorbeeld-app-sjabloon en paginasjablonen bevat.
uuid: 3a93017c-8094-413f-a01c-9b72025a2b20
contentOwner: User
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/MOBILE
discoiquuid: ec4ada04-e429-4ad4-a060-2dccac847cf0
translation-type: tm+mt
source-git-commit: a3c303d4e3a85e1b2e794bec2006c335056309fb

---


# Sjablonen en componenten maken en toevoegen {#creating-and-adding-templates-and-components}

>[!NOTE]
>
>Adobe adviseert gebruikend de Redacteur van het KUUROORD voor projecten die op kader-gebaseerde cliënt-zijteruggeven van enige paginatoepassing (b.v. Reageren) vereisen. [Meer](/help/sites-developing/spa-overview.md)informatie.

AEM Mobile On-Demand biedt een volledig geconfigureerde toepassingssjabloon, een artikelsjabloon en artikelcomponenten.

De wij.Unlimited App is een steekproefmalplaatje dat shell van een volledig configureerbare en handelbare mobiele toepassing AEM op bestelling vertegenwoordigt.

Als u deze voorbeeldsjabloon selecteert wanneer u een nieuwe app maakt, beschikt u over een dashboard met uitgebreide AEM Mobile-functies.

![chlimage_1-70](assets/chlimage_1-70.png)

>[!NOTE]
>
>Raadpleeg het [AEM Mobile Application Dashboard](/help/mobile/mobile-apps-ondemand-application-dashboard.md)voor informatie over het beheer van uw toepassing en mobiele toepassingsinhoud vanuit het AEM Mobile Apps Control Center.

## App-sjablonen maken {#creating-app-templates}

Een App-sjabloon wordt gebruikt om een nieuwe app te maken en fungeert als een verzameling paginasjablonen en -componenten die een basislijn of basis van een app vormen. De sjabloon stempelt enkele fundamentele eigenschappen uit om de app op de juiste manier te leiden. Over het algemeen zou een klant niet te veel apps maken.

App-sjablonen bieden een eenvoudige manier om gebruik te maken van bestaande ontwerpen die zijn gemaakt door ontwikkelaars en die worden gebruikt voor het maken van nieuwe apps in AEM.

Wanneer u een nieuwe app maakt op basis van de sjabloon van een andere app, krijgt u een app met een beginpunt dat representatief is voor de app waarin deze is gemaakt.

Stappen voor het maken van een nieuwe app op basis van een toepassingssjabloon:

1. Ga naar de AEM Mobile-app-catalogus: *&lt;server-url>/aem/apps.html/content/mobileapps*
1. Selecteer **Maken** —> **App** zoals hieronder wordt weergegeven

Nadat u een app hebt gemaakt met deze sjabloon, kunt u artikelen, banners en verzamelingen toevoegen aan uw app. Zie Handelingen voor [inhoudsbeheer voor meer informatie over het opnieuw bezoeken, maken van artikelen, banners en verzamelingen](/help/mobile/mobile-apps-ondemand-manage-content-ondemand.md).

>[!NOTE]
>
>U kunt ook een voorbeeld-app-sjabloon selecteren, bijvoorbeeld **We.Unlimited** -app, die u ontvangt van een AEM-ontwikkelaar. Als u deze voorbeeldsjabloon voor uw app gebruikt, kunt u bepaalde voorbeeldartikelen en verzamelingen bewerken. U kunt de voorbeeldsjablonen en -componenten gebruiken, de bestaande sjablonen en componenten aanpassen of nieuwe sjablonen voor uw app maken.

>[!CAUTION]
>
>Setting ***redirectTarget*** property
>
>Tijdens het gebruik van een van de toepassingssjablonen definieert de ontwikkelaar de inhoud van de toepassing. Nochtans, moet de ontwikkelaar zich bewust zijn waar de toepassing in jcr en de waarde van ***redirectTarget*** bezit wordt gecreeerd.
>
>Het ***redirectTarget*** wordt berekend als deel van creeer app verrichting en probeert om een weg op te lossen, als er een eigenschap redirectTarget beschikbaar als deel van het toepassingsmalplaatje is, en de waarde van redirectTarget wordt bepaald als met betrekking. Wanneer tijdens het maken van de app een relatieve waarde voor redirectTarget wordt gevonden in de toepassingssjabloon, wordt de waarde toegevoegd aan de opgeloste locatie waar de app is gemaakt.
>
>Als een toepassingssjabloon bijvoorbeeld een ***redirectTarget*** definieert met de waarde &quot;*lanugage-masters/nl*&quot; en de app is gemaakt in &quot;*/content/mobileapps/fooApp*&quot;, is de uiteindelijke waarde voor redirectTarget nadat de app is gemaakt &quot;*/content/mobileapps/fooApp/language-masters/nl*&quot;.


## Inhoudssjablonen maken {#creating-content-templates}

Elk eenheidstype heeft twee out-of-the-box malplaatjes. Dit zijn:

* **** Standaardsjablonen: gebruikt voor het maken van inhoud met de toepasselijke standaardeigenschappen/structuur
* **** Geïmporteerde sjablonen: gebruikt voor het importeren van inhoud van AEM Mobile met de toepasselijke standaardeigenschappen/structuur

### Artikelsjablonen {#article-templates}

Het onbeperkte artikel is een voorbeeldsjabloon die een typische AEM Mobile On-Demand-artikellay-out vertegenwoordigt.

1. Klik op **+** in **Artikelen** beheren om een nieuw artikel te maken. U kunt een **Onbeperkt artikel** of een **RTF-artikel** kiezen. In de onderstaande afbeelding ziet u de optie waarmee u een van deze twee artikelsjablonen kunt kiezen.

1. Klik op **Volgende** om metagegevens van artikelen te definiëren, zoals Naam/titel van artikel, Beschrijving, Auteur, Abstract, Afdeling, Miniatuurafbeelding, Toegang tot artikel, enzovoort.
1. Klik op **Volgende** om de Advertentie-eigenschappen in te vullen.
1. Klik op **Volgende** om de afbeelding voor artikelen of sociale media in te voeren
1. Klik op **Volgende** om een verzamelingskoppeling voor dit nieuwe artikel te kiezen.
1. Klik op **Volgende** om de gegevens voor sociaal delen in te voeren.
1. Klik op **Maken** om het maken van een artikel met het voorbeeld te voltooien. Klik op **Gereed** of Artikel **** bewerken om de eigenschappen van dit artikel te bewerken.

![chlimage_1-71](assets/chlimage_1-71.png)

### Componenten toevoegen aan artikel {#adding-components-to-article}

Nadat een auteur is gemaakt, kan hij of zij de inhoud van een artikel bewerken door componenten zoals tekst en afbeeldingen toe te voegen. Artikelen zijn een uitbreiding van AEM-paginasjablonen.

Selecteer een artikel dat u wilt bewerken en klik op **Bewerken** om componenten aan het artikel toe te voegen.

![chlimage_1-72](assets/chlimage_1-72.png) ![chlimage_1-73](assets/chlimage_1-73.png)

Kies &#39;**+**&#39; in het linkerdeelvenster om componenten aan uw artikel toe te voegen.

![chlimage_1-74](assets/chlimage_1-74.png)

### Sjablonen voor gebruik buiten de box maken {#creating-out-of-the-box-templates}

Er zijn geen out-of-the-box malplaatjes van het Artikel, nochtans is er een standaardmalplaatje dat de douanemalplaatjes zouden moeten uitbreiden, zie de malplaatjesteekproef [van het](http://localhost:4502/crx/de/index.jsp#/apps/geometrixx-unlimited-app/templates/article)Artikel van de Onbeperkte app van Geometrixx.

De belangrijkste eigenschappen buiten de normale vereiste eigenschappen van het AEM malplaatje omvatten;

***dps-resourceType=&quot;dps:Article&quot;***

Deze eigenschap zorgt ervoor dat de AEM-pagina wordt herkend als een doelpagina voor artikel met AEM Mobile.

Net als voor AEM-sjablonen kunt u standaardeigenschappen of onderliggende knooppunten toevoegen aan de ***jcr:content*** van de sjabloon.

### Banner- en verzamelingssjablonen {#banner-and-collection-templates}

>[!CAUTION]
>
>Banners en verzamelingen hebben geen inhoud, dus het maken ervan ondersteunt geen aangepaste sjablonen.

## Componenten maken en toevoegen {#creating-and-adding-components}

Componenten gebruiken en verlenen toegang tot widgets. Deze worden gebruikt om de inhoud te renderen.

Een eenvoudige component is inbegrepen in de codebewaarplaats, waarvan de bron in AEM kan worden gevonden. Vervolgens kan het ook lokaal worden geopend in CRXDE Lite.

>[!NOTE]
>
>Er zijn momenteel geen out-of-the-box-componenten beschikbaar voor AEM Mobile.


U kunt componenten aan uw pagina toevoegen. Elke component kan in een AEM Mobile-app worden gebruikt, maar wordt bij toepassing mogelijk niet correct gerenderd.

Aangepaste componenten kunnen echter niet correct worden geëxporteerd en geüpload naar AEM Mobile On-Demand Services zonder een aangepaste handler voor het synchroniseren van exportinhoud die in AEM wordt weergegeven.

Wanneer de component al is opgenomen in een AEM-pagina, samen met enkele andere bouwsteencomponenten, kunt u een andere component aan de pagina toevoegen of een bestaande component bewerken.

**Een andere component aan de pagina toevoegen:**

1. Kies die pagina en controleer of u in de modus Bewerken werkt. Ga hiervoor naar het vervolgkeuzemenu rechtsboven in de koptekst van de Editor.
1. Zijpaneel in-/uitschakelen met het pictogram uiterst links in de koptekst van de Editor
1. Selecteer het tabblad **Componenten**
1. Sleep een van de beschikbare componenten naar de pagina

![chlimage_1-75](assets/chlimage_1-75.png)

**Een bestaande component bewerken:**

1. Kies die pagina en controleer of u in de modus **Bewerken** werkt en selecteer de component
1. Tik op het moersleutelpictogram om de component te configureren

>[!NOTE]
>
>U kunt een component tot stand brengen in AEM en het zelfde aanpassen gebruikend het [Ontwikkelen met CRXDE Lite](/help/sites-developing/developing-with-crxde-lite.md). Als u de bestaande component naar wens hebt aangepast, kunt u deze aan uw pagina toevoegen met de optie **Bewerken** onder Artikelen **** beheren, zoals in de bovenstaande afbeelding wordt getoond.

>[!NOTE]
>
>Raadpleeg de [aanbevolen procedures voor het ontwikkelen](/help/mobile/best-practices-aem-mobile.md) van sjablonen en componenten in AEM Mobile.

### De volgende stappen {#the-next-steps}

* [Inhoud-eigenschappen gebruiken om inhoud te exporteren](/help/mobile/on-demand-content-properties-exporting.md)
* [Mobiel met inhoudssynchronisatie](/help/mobile/mobile-ondemand-contentsync.md)