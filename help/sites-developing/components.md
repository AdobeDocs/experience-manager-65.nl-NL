---
title: Overzicht van componenten
description: Componenten zijn modulaire eenheden die specifieke functionaliteit realiseren om uw inhoud op uw website weer te geven
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: components
content-type: reference
exl-id: 9e30c969-2692-4380-943a-b022ee900ce8
solution: Experience Manager, Experience Manager Sites
feature: Developing
role: Developer
source-git-commit: 66db4b0b5106617c534b6e1bf428a3057f2c2708
workflow-type: tm+mt
source-wordcount: '561'
ht-degree: 0%

---

# Overzicht van componenten{#components-overview}

Deze pagina verstrekt een overzicht van de componenten van Adobe Experience Manager (AEM) zoals die [&#x200B; die voor pagina creatie &#x200B;](/help/sites-authoring/default-components-foundation.md) worden gebruikt.

## Wat zijn componenten? {#what-exactly-is-a-component}

* Modulaire eenheden die specifieke functionaliteit realiseren om uw inhoud op uw website te presenteren.
* Herbruikbaar.
* Ontwikkeld als zelfstandige eenheden in één map van de opslagplaats.
* Geen verborgen configuratiebestanden hebben.
* Kan andere componenten bevatten.
* Kan overal binnen om het even welk AEM systeem lopen. Ze kunnen ook beperkt zijn tot bepaalde onderdelen.
* Een gestandaardiseerde gebruikersinterface hebben.
* Heb bewerkingsgedrag dat kan worden gevormd.
* Dialoogvensters gebruiken die zijn gebouwd met subelementen op basis van graniet UI-componenten
* Wordt ontwikkeld gebruikend [&#x200B; HTML &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-htl/content/overview.html?lang=nl-NL) (geadviseerd) of JSP.
* Kan worden ontwikkeld om aangepaste componenten te maken die de standaardfunctionaliteit uitbreiden.

Omdat componenten modulair zijn, kunt u:

* Ontwikkel een nieuwe component op uw lokale instantie.
* Implementeer deze in de testomgeving.
* Implementeer deze in uw live ontwerpomgeving, waar auteurs en/of beheerders inhoud kunnen toevoegen en configureren.
* Implementeer deze in uw live publicatieomgeving(en), waar ze worden gebruikt om inhoud te renderen voor bezoekers van uw website. Bepaalde componenten, bijvoorbeeld, voor de Gemeenschappen, aanvaarden ook input van uw gebruikers.

Elke AEM component:

* Is een middeltype.
* Is een inzameling van manuscripten die een specifieke functie volledig realiseren.
* Kan in *isolatie* functioneren, betekenend of binnen AEM of een portaal.

## Buiten-de-box Componenten binnen AEM {#out-of-the-box-components-within-aem}

AEM komt met een verscheidenheid van [&#x200B; uit-van-de-doos componenten &#x200B;](/help/sites-authoring/default-components.md) die uitvoerige functionaliteit met inbegrip van verstrekken:

* Alineasysteem ( `parsys`)
* Pagina ( `responsivegrid` - alleen interface met aanraakbediening)
* Tekst
* Afbeelding, met bijbehorende tekst
* Werkbalk

De verstrekte componenten en hun gebruik binnen de [&#x200B; steekproefWij.Retail websites &#x200B;](/help/sites-developing/we-retail.md) tonen hoe te om componenten uit te voeren en te gebruiken. De componenten worden voorzien van al broncode en kunnen als zijn of als uitgangspunt voor gewijzigde of uitgebreide componenten worden gebruikt.

### Basiscomponenten en basiscomponenten {#core-components-and-foundation-components}

Er zijn twee reeksen Adobe-Geleverde AEM beschikbare componenten:

* [&#x200B; Componenten van de Kern &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/introduction.html?lang=nl-NL)
* [Elementaire componenten](/help/sites-authoring/default-components-foundation.md)

{de Componenten van 0} Kern **werden geïntroduceerd met AEM 6.3 en bieden flexibele en eigenschap-rijke auteursfunctionaliteit aan.** De [&#x200B; Wij.Retail verwijzingsplaats &#x200B;](/help/sites-developing/we-retail.md) illustreert hoe de kerncomponenten kunnen worden gebruikt en de huidige best-praktijken van componentenontwikkeling vertegenwoordigen.

**Componenten van de Stichting** zijn beschikbaar met AEM voor vele versies en zijn beschikbaar uit-van-de-doos in een standaard AEM installatie. Hoewel nog steeds ondersteund, zijn de meeste vervangen, worden ze niet meer uitgebreid en zijn ze gebaseerd op oudere technologieën.

>[!NOTE]
>
>[&#x200B; Componenten van de Kern &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/introduction.html?lang=nl-NL) vertegenwoordigen de huidige beste praktijken voor componentenontwerp en ontwikkeling en dienen als verwijzingsimplementaties.
>
>[&#x200B; AEM Moderniseringshulpmiddelen &#x200B;](modernization-tools.md) kan de migratie aan de Componenten van de Kern helpen.

### Beschikbare componenten weergeven {#viewing-available-components}

Voor een overzicht van alle beschikbare componenten in uw AEM instantie, gebruik de [&#x200B; Console van Componenten &#x200B;](/help/sites-authoring/default-components-console.md).

U kunt ook CRXDE Lite gebruiken om een lijst met alle componenten in de opslagplaats op te halen.

1. Selecteer in **[!UICONTROL CRXDE Lite]** eerst **[!UICONTROL Tools]** op de werkbalk en vervolgens **[!UICONTROL Query]** , waarna het tabblad **[!UICONTROL Query]** wordt geopend.

1. Selecteer `XPath` as **[!UICONTROL Type]** op het tabblad **[!UICONTROL Query]** .

1. Voer in het invoerveld **[!UICONTROL Query]** de volgende tekenreeks in:

   `//element(*, cq:Component)`

1. Klik op **[!UICONTROL Execute]** en de componenten worden weergegeven.

## Aanvullende bronnen {#further-reading}

De volgende pagina&#39;s verstrekken meer gedetailleerde informatie over het ontwikkelen van deze-en ander-componenten:

* [Componenten AEM - De basisbeginselen](/help/sites-developing/components-basics.md)
* [Ontwikkelen AEM componenten](/help/sites-developing/developing-components.md)
* [Ontwikkelen AEM componenten - Codevoorbeelden](/help/sites-developing/developing-components-samples.md)
* [Meerdere lokale editors configureren](/help/sites-developing/multiple-inplace-editors.md)
* [Modus voor ontwikkelaars](/help/sites-developing/developer-mode.md)
* [Uw gebruikersinterface testen](/help/sites-developing/hobbes.md)
* [Componenten voor inhoudsfragmenten](/help/sites-developing/components-content-fragments.md)
* [Pagina-informatie ophalen in JSON-indeling](/help/sites-developing/pageinfo.md)
* [Internationaliserende componenten](/help/sites-developing/i18n.md)
* [&#x200B; Componenten van de Kern &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/introduction.html?lang=nl-NL)
* [Voorwaarden verbergen gebruiken](/help/sites-developing/hide-conditions.md)
* Klassieke interface

   * [AEM (klassieke gebruikersinterface)](/help/sites-developing/developing-components-classic.md)
   * [Widgets gebruiken en uitbreiden (klassieke UI)](/help/sites-developing/widgets.md)
   * [xtypes gebruiken (klassieke UI)](/help/sites-developing/xtypes.md)
   * [Forms ontwikkelen (klassieke gebruikersinterface)](/help/sites-developing/developing-forms.md)
