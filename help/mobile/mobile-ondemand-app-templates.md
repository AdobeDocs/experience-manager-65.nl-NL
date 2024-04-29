---
title: Sjablonen en componenten maken en toevoegen
description: Volg deze pagina voor meer informatie over het maken en toevoegen van sjablonen en componenten aan uw app. De pagina gebruikt Geometrixx Unlimited App als app die een sjabloon en paginasjablonen voor de voorbeeldapp bevat.
contentOwner: User
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/MOBILE
exl-id: 5f050baa-fe10-4acc-ad32-de20793edc13
solution: Experience Manager
feature: Mobile
role: User
source-git-commit: 1f56c99980846400cfde8fa4e9a55e885bc2258d
workflow-type: tm+mt
source-wordcount: '1151'
ht-degree: 0%

---

# Sjablonen en componenten maken en toevoegen {#creating-and-adding-templates-and-components}

>[!NOTE]
>
>De Adobe adviseert het gebruiken van de SPARedacteur voor projecten die op kader-gebaseerde cliënt-zijteruggeven van enige paginatoepassing (bijvoorbeeld, Reageren) vereisen. [Meer informatie](/help/sites-developing/spa-overview.md).

AEM Mobile On-Demand biedt een volledig geconfigureerde toepassingssjabloon, een artikelsjabloon en artikelcomponenten.

We.Unlimited App is een voorbeeldsjabloon die de shell van een volledig configureerbare en beheerbare AEM Mobile On-Demand-toepassing vertegenwoordigt.

Als u deze voorbeeldsjabloon selecteert wanneer u een app maakt, wordt een dashboard met uitgebreide AEM Mobile-functies weergegeven.

![chlimage_1-70](assets/chlimage_1-70.png)

>[!NOTE]
>
>Als u uw toepassing en inhoud voor mobiele apps wilt beheren vanuit AEM Mobile Apps Control Center, raadpleegt u de [AEM Mobile-toepassingsdashboard](/help/mobile/mobile-apps-ondemand-application-dashboard.md).

## App-sjablonen maken {#creating-app-templates}

Een App-sjabloon wordt gebruikt om een app te maken en fungeert als een verzameling paginasjablonen en -componenten die een basislijn of basis van een app vormen. De sjabloon stempt enkele fundamentele eigenschappen uit om de app op de juiste manier te leiden. Over het algemeen zou een klant niet te veel apps maken.

Toepassingssjablonen bieden een eenvoudige manier om bestaande ontwerpen te gebruiken die door ontwikkelaars zijn gemaakt en die worden gebruikt voor het maken van nieuwe apps in AEM.

Wanneer u een app maakt op basis van de sjabloon van een andere app, krijgt u een app met een beginpunt dat representatief is voor de app waarin deze is gemaakt.

Stappen voor het maken van een app op basis van een toepassingssjabloon:

1. Ga naar de AEM Mobile-toepassingscatalogus: *&lt;server-url>/aem/apps.html/content/mobileapps*
1. Selecteren **Maken** > **App** zoals hieronder weergegeven

Nadat u een app hebt gemaakt met deze sjabloon, kunt u artikelen, banners en verzamelingen toevoegen aan uw app. Als u artikelen, banners en verzamelingen opnieuw wilt bekijken, gaat u naar [Handelingen voor inhoudsbeheer](/help/mobile/mobile-apps-ondemand-manage-content-ondemand.md).

>[!NOTE]
>
>U kunt ook een voorbeeldtoepassingssjabloon selecteren, bijvoorbeeld **Wij.Onbeperkt** , beschikbaar gesteld door een AEM ontwikkelaar. Als u deze voorbeeldsjabloon voor uw app gebruikt, kunt u bepaalde voorbeeldartikelen en verzamelingen bewerken. U kunt de voorbeeldsjablonen en -componenten gebruiken, de bestaande sjablonen en componenten aanpassen of nieuwe sjablonen voor uw app maken.

>[!CAUTION]
>
>Instelling ***redirectTarget*** eigenschap
>
>Tijdens het gebruik van een van de toepassingssjablonen definieert de ontwikkelaar de inhoud van de toepassing. De ontwikkelaar moet zich echter bewust zijn van de plaats waar de toepassing wordt gemaakt in de jcr en de waarde van ***redirectTarget*** eigenschap.
>
>De ***redirectTarget*** wordt berekend als onderdeel van het maken van de app en probeert een pad op te lossen als er een eigenschap redirectTarget beschikbaar is als onderdeel van de toepassingssjabloon en de waarde van redirectTarget wordt gedefinieerd als relatief. Wanneer tijdens het maken van de app een relatieve waarde voor redirectTarget wordt gevonden in de toepassingssjabloon, wordt de waarde toegevoegd aan de opgeloste locatie waar de app is gemaakt.
>
>Als een toepassingssjabloon bijvoorbeeld een ***redirectTarget*** met de waarde &quot;*lantaarnstramienen/nl*&quot;, en de app is gemaakt in &quot;*/content/mobileapps/fooApp*&quot;, is de uiteindelijke waarde voor redirectTarget nadat de app is gemaakt &quot;*/content/mobileapps/fooApp/language-masters/nl*&quot;.
>

## Inhoudssjablonen maken {#creating-content-templates}

Elk eenheidstype heeft twee out-of-the-box malplaatjes. Deze zijn:

* **Standaardsjablonen:** gebruikt voor het maken van inhoud met de toepasselijke standaardeigenschappen/structuur
* **Geïmporteerde sjablonen:** gebruikt voor het importeren van inhoud uit AEM Mobile met de toepasselijke standaardeigenschappen/structuur

### Artikelsjablonen {#article-templates}

Het artikel Onbeperkt is een voorbeeldsjabloon die een gebruikelijke lay-out van AEM Mobile On-Demand-artikelen vertegenwoordigt.

1. In **Artikelen beheren**, selecteert u **+**  om een artikel te maken. U kunt een van de **Onbeperkt artikel** of **Rich Text Article**. In de onderstaande afbeelding ziet u de optie waarmee u een van deze twee artikelsjablonen kunt kiezen.

1. Klikken **Volgende** om metagegevens van artikelen te definiëren, zoals artikelnaam/titel, beschrijving, auteur, abstract, afdeling, miniatuurafbeelding, artikeltoegang, enzovoort.
1. Klikken **Volgende** om de Advertentie-eigenschappen in te vullen.
1. Klikken **Volgende** om artikelafbeelding of afbeelding van sociale media in te voeren
1. Klikken **Volgende** om een verzamelingskoppeling naar dit nieuwe artikel te kiezen.
1. Klikken **Volgende** om de details voor sociaal delen in te voeren.
1. Klikken **Maken** om het maken van een artikel met het voorbeeld te voltooien. U klikt op **Gereed** of **Artikel bewerken** om de eigenschappen van dit artikel te bewerken.

![chlimage_1-71](assets/chlimage_1-71.png)

### Componenten toevoegen aan artikel {#adding-components-to-article}

Nadat een auteur is gemaakt, kan hij of zij de inhoud van een artikel bewerken door componenten zoals tekst en afbeeldingen toe te voegen. Artikelen zijn een uitbreiding van AEM paginasjablonen.

Selecteer een artikel dat u wilt bewerken en klik op **Bewerken** om componenten aan het artikel toe te voegen.

![chlimage_1-72](assets/chlimage_1-72.png) ![chlimage_1-73](assets/chlimage_1-73.png)

Kies de &#39;**+**&#39; in het linkerdeelvenster om componenten aan uw artikel toe te voegen.

![chlimage_1-74](assets/chlimage_1-74.png)

### Sjablonen voor gebruik buiten de box maken {#creating-out-of-the-box-templates}

Er zijn geen out-of-the-box de Malplaatjes van het Artikel, nochtans is er een standaardmalplaatje dat de douanesjablonen zouden moeten uitbreiden, zie Geometrixx Unlimited App [Voorbeeld van een artikelsjabloon](http://localhost:4502/crx/de/index.jsp#/apps/geometrixx-unlimited-app/templates/article).

De belangrijkste eigenschappen buiten de normale AEM vereiste eigenschappen omvatten;

***dps-resourceType=&quot;dps:Article&quot;***

Deze eigenschap zorgt ervoor dat de AEM pagina wordt herkend als een voor AEM Mobile bedoelde artikelpagina.

Net als AEM sjablonen kunt u standaardeigenschappen of onderliggende knooppunten toevoegen aan de sjablonen ***jcr:inhoud***.

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
>

U kunt componenten aan uw pagina toevoegen. Elke component kan in een AEM Mobile-toepassing worden gebruikt, maar bij toepassing wordt de rendering mogelijk niet correct uitgevoerd.

Aangepaste componenten kunnen echter niet correct naar AEM Mobile On-demand Services worden geëxporteerd en geüpload zonder een aangepaste handler voor het synchroniseren van exportinhoud die in AEM wordt weergegeven.

Wanneer de component al op een AEM pagina is opgenomen, kunt u samen met enkele andere bouwsteencomponenten een andere component aan de pagina toevoegen of een bestaande component bewerken.

**Een andere component aan de pagina toevoegen:**

1. Kies die pagina en controleer of u in de modus Bewerken werkt. Ga hiervoor naar het vervolgkeuzemenu rechtsboven in de koptekst van de Editor.
1. Zijpaneel in-/uitschakelen met het pictogram uiterst links in de koptekst van de Editor
1. Selecteer de **Componenten** tab
1. Sleep een van de beschikbare componenten naar de pagina

![chlimage_1-75](assets/chlimage_1-75.png)

**Een bestaande component bewerken:**

1. Kies die pagina en zorg ervoor dat u zich in **Bewerken** en selecteert u de component
1. Selecteer het moersleutelpictogram om de component te configureren

>[!NOTE]
>
>U kunt een component maken in AEM en hetzelfde aanpassen met [Ontwikkelen met CRXDE Lite](/help/sites-developing/developing-with-crxde-lite.md). Nadat u de bestaande component naar wens hebt aangepast, kunt u deze op de pagina toevoegen met de opdracht **Bewerken** optie onder **Artikelen beheren** zoals aangegeven in bovenstaande figuur.

>[!NOTE]
>
>Zie [Beste praktijken voor de Ontwikkeling van Malplaatjes en Componenten](/help/mobile/best-practices-aem-mobile.md) in AEM Mobile.

### De volgende stappen {#the-next-steps}

* [Inhoud-eigenschappen gebruiken om inhoud te exporteren](/help/mobile/on-demand-content-properties-exporting.md)
* [Mobiel met inhoudssynchronisatie](/help/mobile/mobile-ondemand-contentsync.md)
