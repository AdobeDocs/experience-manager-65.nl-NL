---
title: Overzicht van componenten
seo-title: Componenten
description: Componenten zijn modulaire eenheden die specifieke functionaliteit realiseren om uw inhoud op uw website weer te geven
seo-description: Componenten zijn modulaire eenheden die specifieke functionaliteit realiseren om uw inhoud op uw website weer te geven
uuid: fb39aeb8-8f43-4091-8083-ebfab89e6e63
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: components
content-type: reference
discoiquuid: 45efff93-2fe5-4313-83a0-0e23a540da93
translation-type: tm+mt
source-git-commit: 5597fb39500ac1f85d03263bfa1e5239d35d2a2c

---


# Overzicht van componenten{#components-overview}

Deze pagina bevat een overzicht van Adobe Experience Manager-componenten, zoals de componenten die [worden gebruikt voor het ontwerpen](/help/sites-authoring/default-components-foundation.md)van pagina&#39;s.

## Wat zijn componenten? {#what-exactly-is-a-component}

* Modulaire eenheden die specifieke functionaliteit realiseren om uw inhoud op uw website te presenteren.
* Herbruikbaar.
* Ontwikkeld als zelfstandige eenheden in één map van de opslagplaats.
* Geen verborgen configuratiebestanden hebben.
* Kan andere componenten bevatten.
* Kan overal in elk AEM-systeem worden uitgevoerd. Ze kunnen ook beperkt zijn tot bepaalde onderdelen.
* Een gestandaardiseerde gebruikersinterface hebben.
* Heb bewerkingsgedrag dat kan worden gevormd.
* Dialoogvensters gebruiken die zijn gebouwd met subelementen op basis van graniet UI-componenten
* Ontwikkeld met [HTL](https://docs.adobe.com/content/help/en/experience-manager-htl/using/overview.html) (aanbevolen) of JSP.
* Kan worden ontwikkeld om aangepaste componenten te maken die de standaardfunctionaliteit uitbreiden.

Omdat componenten modulair zijn, kunt u:

* Ontwikkel een nieuwe component op uw lokale instantie.
* Implementeer deze in de testomgeving.
* Implementeer deze in uw live ontwerpomgeving, waar auteurs en/of beheerders inhoud kunnen toevoegen en configureren.
* Implementeer deze in uw live publicatieomgeving(en), waar ze worden gebruikt om inhoud te renderen voor bezoekers van uw website. Bepaalde componenten, bijvoorbeeld voor Communities, accepteren ook invoer van uw gebruikers.

Elke AEM-component:

* Is een middeltype.
* Is een inzameling van manuscripten die een specifieke functie volledig realiseren.
* Kan *afzonderlijk* functioneren, wat ofwel binnen AEM ofwel een portaal betekent.

## Buiten-de-box componenten binnen AEM {#out-of-the-box-components-within-aem}

AEM wordt geleverd met verschillende [kant-en-klare componenten](/help/sites-authoring/default-components.md) die uitgebreide functionaliteit bieden, waaronder:

* Alineasysteem ( `parsys`)
* Pagina ( `responsivegrid` - alleen interface met aanraakbediening)
* Tekst
* Afbeelding, met bijbehorende tekst
*  Werkbalk

De verstrekte componenten en hun gebruik binnen de [steekproefWeb.Retail websites](/help/sites-developing/we-retail.md) illustreren hoe te om componenten uit te voeren en te gebruiken. De componenten worden voorzien van al broncode en kunnen als zijn of als uitgangspunt voor gewijzigde of uitgebreide componenten worden gebruikt.

### Basiscomponenten en basiscomponenten {#core-components-and-foundation-components}

Er zijn twee door Adobe geleverde AEM-componenten beschikbaar:

* [Kernonderdelen](https://docs.adobe.com/content/help/en/experience-manager-core-components/using/introduction.html)
* [Elementaire componenten](/help/sites-authoring/default-components-foundation.md)

**De Componenten** van de kern werden geïntroduceerd met AEM 6.3 en bieden flexibele en eigenschap-rijke auteursfunctionaliteit. De [Wij.Retail verwijzingsplaats](/help/sites-developing/we-retail.md) illustreert hoe de kerncomponenten kunnen worden gebruikt en de huidige beste praktijken van componentenontwikkeling vertegenwoordigen.

**De Componenten** van de stichting zijn beschikbaar met AEM voor vele versies en zijn beschikbaar uit-van-de-doos in een standaardAEM installatie. Hoewel nog steeds ondersteund, zijn de meeste vervangen, worden ze niet meer uitgebreid en zijn ze gebaseerd op oudere technologieën.

>[!NOTE]
>
>[De Componenten](https://docs.adobe.com/content/help/en/experience-manager-core-components/using/introduction.html) van de kern vertegenwoordigen de huidige beste praktijken voor componentenontwerp en ontwikkeling en dienen als verwijzingsimplementaties.
>
>[De modernisering van AEM-tools](modernization-tools.md) kan de migratie naar kerncomponenten vergemakkelijken.

### Beschikbare componenten weergeven {#viewing-available-components}

Voor een overzicht van alle beschikbare componenten in uw instantie AEM, gebruik de Console [van](/help/sites-authoring/default-components-console.md)Componenten.

Alternatief, kunt u CRXDE Lite ook gebruiken om een lijst van alle componenten beschikbaar in de bewaarplaats te krijgen.

1. In **[!UICONTROL CRXDE Lite]**, uitgezochte **[!UICONTROL Hulpmiddelen]** van de toolbar, toen **[!UICONTROL Vraag]**, die de **[!UICONTROL Vraag]** tabel opent.

1. Selecteer op het tabblad **[!UICONTROL Query]** de optie `XPath` Type ****.

1. Voer in het veld **[!UICONTROL Query]** -invoer de volgende tekenreeks in:

   `//element(*, cq:Component)`

1. Klik op **[!UICONTROL Uitvoeren]** en de componenten worden weergegeven.

## Aanvullende bronnen {#further-reading}

De volgende pagina&#39;s verstrekken meer gedetailleerde informatie over het ontwikkelen van deze-en ander-componenten:

* [AEM-componenten - De basisbeginselen](/help/sites-developing/components-basics.md)
* [AEM-componenten ontwikkelen](/help/sites-developing/developing-components.md)
* [AEM-componenten ontwikkelen - Codevoorbeelden](/help/sites-developing/developing-components-samples.md)
* [Meerdere lokale editors configureren](/help/sites-developing/multiple-inplace-editors.md)
* [Ontwerpmodus](/help/sites-developing/developer-mode.md)
* [Uw gebruikersinterface testen](/help/sites-developing/hobbes.md)
* [Componenten voor inhoudsfragmenten](/help/sites-developing/components-content-fragments.md)
* [Pagina-informatie ophalen in JSON-indeling](/help/sites-developing/pageinfo.md)
* [Internationaliserende componenten](/help/sites-developing/i18n.md)
* [Kernonderdelen](https://docs.adobe.com/content/help/en/experience-manager-core-components/using/introduction.html)
* [Voorwaarden verbergen gebruiken](/help/sites-developing/hide-conditions.md)
* Klassieke interface

   * [AEM-componenten (klassieke gebruikersinterface)](/help/sites-developing/developing-components-classic.md)
   * [Widgets gebruiken en uitbreiden (klassieke UI)](/help/sites-developing/widgets.md)
   * [xtypes gebruiken (klassieke UI)](/help/sites-developing/xtypes.md)
   * [Formulieren ontwikkelen (klassieke gebruikersinterface)](/help/sites-developing/developing-forms.md)

