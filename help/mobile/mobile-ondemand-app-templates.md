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
source-git-commit: 2dae56dc9ec66f1bf36bbb24d6b0315a5f5040bb
workflow-type: tm+mt
source-wordcount: '1130'
ht-degree: 0%

---

# Sjablonen en componenten maken en toevoegen {#creating-and-adding-templates-and-components}

{{ue-over-mobile}}

AEM Mobile On-Demand biedt een volledig geconfigureerde toepassingssjabloon, een artikelsjabloon en artikelcomponenten.

We.Unlimited App is een voorbeeldsjabloon die de shell van een volledig configureerbare en beheerbare AEM Mobile On-Demand-toepassing vertegenwoordigt.

Als u deze voorbeeldsjabloon selecteert wanneer u een app maakt, wordt een dashboard met uitgebreide AEM Mobile-functies weergegeven.

![ chlimage_1-70 ](assets/chlimage_1-70.png)

>[!NOTE]
>
>Om uw toepassing en mobiele toepassingsinhoud van het Centrum van de Controle van de Apps van AEM Mobile te beheren, zie het [ dashboard van de Toepassing van AEM Mobile ](/help/mobile/mobile-apps-ondemand-application-dashboard.md).

## App-sjablonen maken {#creating-app-templates}

Een App-sjabloon wordt gebruikt om een app te maken en fungeert als een verzameling paginasjablonen en -componenten die een basislijn of basis van een app vormen. De sjabloon stempt enkele fundamentele eigenschappen uit om de app op de juiste manier te leiden. Over het algemeen zou een klant niet te veel apps maken.

Toepassingssjablonen bieden een eenvoudige manier om bestaande ontwerpen te gebruiken die door ontwikkelaars zijn gemaakt en die worden gebruikt voor het maken van nieuwe apps in AEM.

Wanneer u een app maakt op basis van de sjabloon van een andere app, krijgt u een app met een beginpunt dat representatief is voor de app waarin deze is gemaakt.

Stappen voor het maken van een app op basis van een toepassingssjabloon:

1. Ga naar de AEM Mobile-app-catalogus: *&lt;server-url>/aem/apps.html/content/mobileapps*
1. Selecteer **creëren** > **app** zoals hieronder getoond

Nadat u een app hebt gemaakt met deze sjabloon, kunt u artikelen, banners en verzamelingen toevoegen aan uw app. Om, verwezenlijking van artikelen, banners, en inzamelingen opnieuw te bezoeken, zie {de Acties van het Beheer van de Inhoud 0} [&#128279;](/help/mobile/mobile-apps-ondemand-manage-content-ondemand.md).

>[!NOTE]
>
>Alternatief, kunt u ook een malplaatje van de steekproefapp selecteren, bijvoorbeeld, **Wij.Unlimited** app, die aan u door een AEM ontwikkelaar ter beschikking wordt gesteld. Als u deze voorbeeldsjabloon voor uw app gebruikt, kunt u bepaalde voorbeeldartikelen en verzamelingen bewerken. U kunt de voorbeeldsjablonen en -componenten gebruiken, de bestaande sjablonen en componenten aanpassen of nieuwe sjablonen voor uw app maken.

>[!CAUTION]
>
>Het plaatsen ***redirectTarget*** bezit
>
>Tijdens het gebruik van een van de toepassingssjablonen definieert de ontwikkelaar de inhoud van de toepassing. Nochtans, moet de ontwikkelaar zich bewust zijn waar de toepassing in jcr en de waarde van ***wordt gecreeerd redirectTarget*** bezit.
>
>***redirectTarget*** wordt berekend als deel van creeer app verrichting en pogingen om een weg op te lossen, als er een redirectTarget bezit beschikbaar als deel van het toepassingsmalplaatje is, en de waarde van redirectTarget wordt bepaald als met betrekking tot. Wanneer tijdens het maken van de app een relatieve waarde voor redirectTarget wordt gevonden in de toepassingssjabloon, wordt de waarde toegevoegd aan de opgeloste locatie waar de app is gemaakt.
>
>Bijvoorbeeld, als een toepassingsmalplaatje a ***redirectTarget*** met een waarde van &quot;*taal-masters/en*&quot;bepaalt, en app werd gecreeerd in &quot;*/content/mobileapps/fooApp*&quot;, zal de definitieve waarde voor redirectTarget na app zoals gecreeerd &quot;*/content/mobileapps/fooApp/language-zijn stramienen/nl*&quot;.
>

## Inhoudssjablonen maken {#creating-content-templates}

Elk eenheidstype heeft twee out-of-the-box malplaatjes. Deze zijn:

* **Standaard malplaatjes:** wordt gebruikt voor inhoudsverwezenlijking met toepasselijke standaardeigenschappen/structuur
* **Geïmporteerde malplaatjes:** gebruikt voor het invoeren van inhoud van AEM Mobile met toepasselijke standaardeigenschappen/structuur

### Artikelsjablonen {#article-templates}

Het artikel Onbeperkt is een voorbeeldsjabloon die een gebruikelijke lay-out van AEM Mobile On-Demand-artikelen vertegenwoordigt.

1. In **beheert Artikelen**, uitgezocht **+** om een artikel tot stand te brengen. U kunt of een **Onbeperkt Artikel** of a **Rich Text Artikel** kiezen. In de onderstaande afbeelding ziet u de optie waarmee u een van deze twee artikelsjablonen kunt kiezen.

1. Klik **daarna** om artmeta gegevens zoals de Naam/Titel van het Artikel, Beschrijving, Auteur, Abstract, Afdeling, het Beeld van de Duimnagel, de Toegang van het Artikel, etc. te bepalen.
1. Klik **daarna** om de Eigenschappen van de Reclame in te vullen.
1. Klik **daarna** om het Beeld van het Artikel of het Beeld van Sociale Media in te gaan
1. Klik **daarna** om een inzamelingsverbinding te kiezen dit nieuwe artikel aan.
1. Klik **daarna** om de details voor sociaal het delen in te gaan.
1. Klik **creëren** om het proces te beëindigen om een artikel te creëren gebruikend de steekproef. U of klikt **Gedaan** of **geeft Artikel** uit om de eigenschappen van dit artikel uit te geven.

![ chlimage_1-71 ](assets/chlimage_1-71.png)

### Componenten toevoegen aan artikel {#adding-components-to-article}

Nadat een auteur is gemaakt, kan hij of zij de inhoud van een artikel bewerken door componenten zoals tekst en afbeeldingen toe te voegen. Artikelen zijn een uitbreiding van AEM paginasjablonen.

Selecteer een artikel u wilt uitgeven, dan klik **uitgeven** om componenten aan het artikel toe te voegen.

![ chlimage_1-72 ](assets/chlimage_1-72.png) ![ chlimage_1-73 ](assets/chlimage_1-73.png)

Kies &quot;**+**&quot;op het linkerpaneel om componenten aan uw artikel toe te voegen.

![ chlimage_1-74 ](assets/chlimage_1-74.png)

### Sjablonen voor gebruik buiten de box maken {#creating-out-of-the-box-templates}

Er zijn geen uit-van-de-doos de Malplaatjes van het Artikel, nochtans is er een standaardmalplaatje dat de douanemalplaatjes zouden moeten uitbreiden, zie het malplaatjesteekproef van het Artikel van de Toepassing van het Geometrixx Unlimited [&#128279;](http://localhost:4502/crx/de/index.jsp#/apps/geometrixx-unlimited-app/templates/article).

De belangrijkste eigenschappen buiten de normale AEM vereiste eigenschappen omvatten;

***dps-resourceType= &quot;dps:Artikel&quot;***

Deze eigenschap zorgt ervoor dat de AEM pagina wordt herkend als een voor AEM Mobile bedoelde artikelpagina.

Zoals per AEM malplaatjes, kunt u om het even welke standaardeigenschappen of kindknopen aan jcr van het malplaatje ***toevoegen:inhoud***.

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

**om een andere component aan de pagina toe te voegen:**

1. Kies die pagina en controleer of u in de modus Bewerken werkt. Ga hiervoor naar het vervolgkeuzemenu rechtsboven in de koptekst van de Editor.
1. Zijpaneel in-/uitschakelen met het pictogram uiterst links in de koptekst van de Editor
1. Selecteer het **lusje van Componenten**
1. Sleep een van de beschikbare componenten naar de pagina

![ chlimage_1-75 ](assets/chlimage_1-75.png)

**om een bestaande component uit te geven:**

1. Kies die pagina en zorg ervoor u op **bent geef** wijze uit en selecteer de component
1. Selecteer het moersleutelpictogram om de component te configureren

>[!NOTE]
>
>U kunt tot een component in AEM leiden en het zelfde aanpassen gebruikend [ Ontwikkelen met CRXDE Lite ](/help/sites-developing/developing-with-crxde-lite.md). Zodra u de bestaande component als uw vereisten hebt aangepast, kunt u het in uw pagina toevoegen gebruikend **uitgeeft** optie onder **leidt Artikelen** zoals aangetoond in het cijfer hierboven.

>[!NOTE]
>
>Verwijs naar [ Beste praktijken voor de Ontwikkeling van Malplaatjes en van Componenten ](/help/mobile/best-practices-aem-mobile.md) in AEM Mobile.

### De volgende stappen {#the-next-steps}

* [Inhoud-eigenschappen gebruiken om inhoud te exporteren](/help/mobile/on-demand-content-properties-exporting.md)
* [Mobiel met inhoudssynchronisatie](/help/mobile/mobile-ondemand-contentsync.md)
