---
title: Veroudering van SPA-editor
description: Alhoewel de Redacteur van het KUUROORD door Adobe wordt gesteund, leer wat zijn veroudering aan uw project betekent en welke opties u voor toekomstige projecten hebt.
feature: Developing
role: Admin, Architect, Developer
exl-id: ea6e46ee-4a90-4236-8d93-292a4dda4dc0
source-git-commit: d619c969604119a8686050fdc34d77c0ffee33cf
workflow-type: tm+mt
source-wordcount: '910'
ht-degree: 0%

---


# Veroudering van SPA-editor {#spa-editor-deprecation}

Alhoewel de Redacteur van het KUUROORD door Adobe wordt gesteund, leer wat zijn veroudering aan uw project betekent en welke opties u voor toekomstige projecten hebt.

## Samenvatting {#summary}

Adobe verwierp de Redacteur van het KUUROORD met [&#x200B; versie 6.5.23 van AEM 6.5, &#x200B;](/help/release-notes/release-notes.md#spa-editor) betekenend dat geen verdere verhogingen of updates aan zijn SDKs zullen worden aangebracht. Adobe moedigt u aan om de [&#x200B; Universele Redacteur &#x200B;](/help/sites-developing/universal-editor/introduction.md) voor om het even welke nieuwe projecten zonder kop te gebruiken om uit de recentste innovaties van AEM voordeel te halen.

## Details van de depressie {#details}

De veroudering van de Redacteur van het KUUROORD **betekent geen directe verwijdering**, en als u bestaande implementaties hebt, **kunt u het blijven gebruiken zolang het aan uw behoeften voldoet.** Houd er echter rekening mee dat deze afgekeurd is.

* Adobe gaat verder en lost alleen P1- en P2-problemen en beveiligingskwetsbaarheden op.
* Er worden geen verdere ontwikkelingen, verbeteringen of updates in de SDK&#39;s van de SDK&#39;s doorgevoerd.

De veroudering houdt in dat de volgende SDK&#39;s nu in de vastzetbewerking zijn.

* [&#x200B; Archetype van het Project van AEM &#x200B;](https://github.com/adobe/aem-project-archetype/)
* [&#x200B; Kern van het Project van AEM SPA SPA &#x200B;](https://github.com/adobe/aem-spa-project-core)
* [&#x200B; AEM SPA ModelManager van de Pagina &#x200B;](https://github.com/adobe/aem-spa-page-model-manager)
* [&#x200B; AEM SPA Component Mapping &#x200B;](https://github.com/adobe/aem-spa-component-mapping)
* [&#x200B; AEM SPA React Editable Componenten &#x200B;](https://github.com/adobe/aem-react-editable-components)
   * [&#x200B; AEM React de Componenten van de Kern &#x200B;](https://github.com/adobe/aem-react-core-wcm-components)
   * [&#x200B; AEM React de Basis van de Componenten van de Kern &#x200B;](https://github.com/adobe/aem-react-core-wcm-components-base)
   * [&#x200B; AEM React de Componenten SPA van de Kern &#x200B;](https://github.com/adobe/aem-react-core-wcm-components-spa)
   * [&#x200B; AEM React de Voorbeelden van de Componenten van de Kern &#x200B;](https://github.com/adobe/aem-react-core-wcm-components-examples)
* [&#x200B; AEM SPA Angular Bewerkbare Componenten &#x200B;](https://github.com/adobe/aem-angular-editable-components)
   * [&#x200B; de Componenten van de Kern van AEM Angular &#x200B;](https://github.com/adobe/aem-angular-core-wcm-components)
   * [&#x200B; AEM Angular Core Components Base &#x200B;](https://github.com/adobe/aem-angular-core-wcm-components-base)
   * [&#x200B; AEM Angular Core Components SPA &#x200B;](https://github.com/adobe/aem-angular-core-wcm-components-spa)
   * [&#x200B; AEM Angular Core Components Voorbeelden &#x200B;](https://github.com/adobe/aem-angular-core-wcm-components-examples)
* [&#x200B; de Bewerkbare Componenten van de Waarde van AEM SPA &#x200B;](https://github.com/mavicellc/aem-vue-editable-components)

## Alternatieven voor de redacteur van het KUUROORD {#alternatives}

De meest geschikte vervanging voor de Redacteur van het KUUROORD hangt van uw projectbehoeften af.

* **[de Universele Redacteur](/help/sites-developing/universal-editor/introduction.md)** is de beste directe vervanging voor de Redacteur van het KUUROORD.
   * De Universele Redacteur is ook een visuele redacteur en werd ontworpen specifiek voor losgemaakte implementaties, die alle ervaring van Adobe van de Redacteur van het KUUROORD opnemen.
   * De Universele Redacteur is ook [&#x200B; vrijgegeven voor AEM as a Cloud Service &#x200B;](https://experienceleague.adobe.com/nl/docs/experience-manager-cloud-service/content/implementing/developing/universal-editor/introduction) en steunt daarom AMS en gebruiksgevallen op prem naast de Diensten van de Wolk.
* **[de Redacteur van het Fragment van de Inhoud](/help/sites-developing/universal-editor/introduction.md)** is een alternatief voor hen die een op vorm-gebaseerde redacteur verkiezen.
   * De Inhoudsfragmenteditor is het meest geschikt wanneer de inhoud is gestructureerd als Inhoudsfragmenten en niet als pagina&#39;s.

Het structureren van inhoud met Content Fragments sluit het gebruik van de Universal Editor als visuele editor niet uit en beide editors kunnen samen worden gebruikt.

## Migreren naar de Universal Editor {#migrate-ue}

De Universele Redacteur biedt vele voordelen aan, die migratie tot het een grote oplossing voor nieuwe projecten maken.

* **Visuele het Uitgeven:** als voor de Redacteur van het KUUROORD, kunnen de auteurs inhoud direct binnen de voorproef uitgeven en onmiddellijk zien hoe hun veranderingen de bezoekerservaring beïnvloeden.
* **Toekomst-Bewijs:** roadmap van AEM geeft voorrang aan de Universele Redacteur als visuele redacteur. Als u het aanneemt, hebt u toegang tot de nieuwste innovaties en verbeteringen.
* **Eenvoudigere Integratie:** Geen AEM-specifieke SDK wordt vereist om de Universele Redacteur te gebruiken, verminderend technologiestapelslot-binnen.
* **breng Uw Eigen Toepassing:** De Universele Redacteur steunt om het even welk Webkader of architectuur, die goedkeuring toestaat zonder het vereisen van complex refactoring.
* **Uitbreidbaarheid:** de Universele Redacteur profiteert van een robuust [&#x200B; uitbreidingskader, &#x200B;](https://experienceleague.adobe.com/nl/docs/experience-manager-cloud-service/content/implementing/developing/universal-editor/extending) met inbegrip van integratie met GenAI, Workfront, en meer.

Er is geen directe migratieweg van de Redacteur van het KUUROORD aan de Universele Redacteur. Dit is te wijten aan fundamentele verschillen in de twee technologieën.

* De Universal Editor introduceert geen functies zoals Sjablooneditor, Stijlsysteem of Responsief raster.
   * Deze gebruiksgevallen kunnen nu efficiënter worden afgehandeld met CSS en JS aan de voorzijde in Edge Delivery Services of projecten zonder kop.
* Aangezien de Universele Redacteur redacteur-a-dienst is, kan het uitvoerders niet toestaan om CSS of JS in de componentendialogen te injecteren.
   * Zo voorkomt u dat dialoogvensters van componenten automatisch worden geconverteerd vanuit de Pagina-editor.
   * Dit is van invloed op veel gebieden in de dialoogvensters, zoals aangepaste widgets, veldvalidatie, tonen/verbergen van regels en op een sjabloon gebaseerde aanpassingen.

Met het oog op deze technische verschillen is de aanbeveling van Adobe:

* Behoud de bestaande plaatsen van de Redacteur van het KUUROORD zoals zij zijn, aangezien de steun verdergaat.
* De universele editor goedkeuren voor alle nieuwe ontwikkelingen, waaronder nieuwe sites, secties of pagina&#39;s.

Houd in mening dat alhoewel er geen directe implementatie van bepaalde eigenschappen van de Redacteur van het KUUROORD in de Universele Redacteur is, er nieuwe manieren zijn om de zelfde problemen op te lossen gebruikend de nieuwe flexibiliteit van de Universele Redacteur.

## Het vergelijken van de Redacteur van het KUUROORD en de Universele Redacteur {#spa-vs-ue}

De Universal Editor biedt veel meer vrijheid aan implementatoren van webapps, zoals in dit diagram wordt geïllustreerd.

![&#x200B; Universele Vergeleek de architecturen van de Redacteur en van het KUUROORD &#x200B;](assets/spa-editor-vs-ue.png)

|  | SPA-editor | Universele editor |
|---|---|---|
| **Thema** | App moet layout implementeren met AEM-raster-CSS. | App kan elke moderne CSS-techniek voor lay-out gebruiken. |
| **teruggevend** | App moet de verpletterende structuur van de Redacteur van het KUUROORD volgen. | App kan vrij worden uitgevoerd, zonder opgelegde regels of te volgen patronen. |
| **SDK** | De implementatie moet de SDK nauw integreren. | Op de auteurslaag, laadt de toepassing enkel `corlib.js` en instrueert de Universele Redacteur via de aantekeningen van HTML. |
| **Kader** | App moet een ondersteunde versie van React of Angular gebruiken. | App kan elk framework of elke architectuur gebruiken. |
| **Hosting** | App moet worden gehost op een AEM-domein. | App kan overal volledig worden ontkoppeld en gehost. |
| **API** | App moet inhoud ophalen van de `model.json` API. | App kan alle API&#39;s gebruiken, ook aangepaste. |
| **persistentie** | De Redacteur van het KUUROORD steunt slechts paginainhoud voor visueel het uitgeven. | De Universal Editor ondersteunt native visuele bewerking van pagina&#39;s en inhoudsfragmenten. |
|  |  | De Universal Editor kan worden uitgebreid om externe inhoud met dezelfde visuele mogelijkheden te bewerken. |
|  | Ontwikkelaars moeten Sling Models en `cq:Dialog` s in AEM implementeren. | Ontwikkelaars hebben weinig tot geen AEM-ervaring nodig en hoeven geen Java te schrijven. |
