---
title: Opmerkingen bij de release van AEM Sites
description: Opmerkingen bij de release die specifiek zijn voor Adobe Experience Manager 6.5 Sites.
translation-type: tm+mt
source-git-commit: 8d60e064ab50f24016c049c8d5d0fceb784c99a3
workflow-type: tm+mt
source-wordcount: '856'
ht-degree: 0%

---


# Opmerkingen bij de release van AEM Sites {#aem-sites-release-notes}

Zie het volgende voor AEM Sites 6.5-verbeteringen in detail:

## Component- en sjabloonontwikkeling {#component-amp-template-development}

* Maven Project Archetype 18+ voor nieuwe projecten, zie [Github voor versienota](https://github.com/Adobe-Marketing-Cloud/aem-project-archetype/releases).
* App Maven Project Archetype 1.0.6+ voor nieuwe projecten van één pagina, zie [Github voor versienota](https://github.com/adobe/aem-spa-project-archetype/releases).
* HTL versie 1.4, zie [Github voor versienota&#39;s](https://github.com/adobe/htl-spec/releases/tag/1.4).

   * operator &quot;in&quot; voor tekenreeksen, arrays en objecten:

      ```html
      ${'a' in 'abc’}
      ${100 in myArray}
      ${'a' in myObject}
      ```

   * Declaraties van variabelen met subset van gegevens:
      `<sly data-sly-set.title="${currentPage.title}"/>${title}`

   * Controleparameters weergeven en herhalen: begin, stap, einde:
      `<h2 data-sly-repeat="${currentPage.listChildren @ begin = 1, step=2}">${item.title}</h2>`

   * Id&#39;s voor terugloop van gegevensdoorhaling:

      ```html
      <div data-sly-unwrap.isUnwrapped="${myCondition || myOtherCondition}">
      text <span data-sly-test="${isUnwrapped}>is unwrapped</code>
      </div>
      ```

   * Ondersteuning voor negatieve getallen

* Core Components 2.3.2+, zie [Github voor versienota&#39;s](https://github.com/Adobe-Marketing-Cloud/aem-core-wcm-components/releases).
* Het Systeem van het net voor de Container van de Lay-out, zie [Github](https://github.com/Adobe-Marketing-Cloud/aem-responsivegrid).
* Clientlib Manager: Google Closure Compiler standaard ingesteld op minificatie van JavaScript-clientlibs (de oude standaard was Yahoo YUI) en heeft Google Closure Compiler bijgewerkt naar versie v20190121
* Sjablooneditor en beleidsregels

   * Sjablonen maken en bewerken voor apps van één pagina die de JS SDK gebruiken (ook wel SPA Editor genoemd)

* Referentiesite We.Retail 4.0, zie [Github voor releaseopmerkingen](https://github.com/Adobe-Marketing-Cloud/aem-sample-we-retail/releases).
* Toolkit om bestaande sites te upgraden zodat de nieuwste editormogelijkheden worden benut, raadpleegt u [Github repository](https://github.com/adobe/aem-modernize-tools)

>[!CAUTION]
>
>AEM bevat versie 1.12.4 van de jQuery-bibliotheek voor maximale compatibiliteit met bestaande aangepaste code. Adobe heeft wijzigingen aangebracht om bekende beveiligingsproblemen aan te pakken.

## Sitebeheer {#site-administration}

* De [Reference](/help/sites-authoring/author-environment-tools.md#references) spoorlijn heeft een nieuwe sectie om van interne verbindingen een lijst te maken die aan de geselecteerde pagina richten. Dit is handig wanneer u een pagina offline of verwijderd wilt maken. Zo kunt u zien welke pagina&#39;s moeten worden aangepast voordat u de pagina&#39;s offline plaatst.
* De [lijstweergave](/help/sites-authoring/basic-handling.md#list-view) heeft een nieuwe werkschemakolom die de status toont wanneer de pagina momenteel in een werkschema is.
* In [pagina-eigenschappen](/help/sites-authoring/editing-page-properties.md) is het nu mogelijk om naar bestaande elementen te bladeren wanneer u een miniatuur aan de pagina toewijst (tabblad Miniatuur).

## Pagina-editor {#page-editor}

* In-context bewerken en samenstellen van app-ervaringen van één pagina toestaan die zijn opgebouwd met React en Angular clientcomponenten die gebruikmaken van de JS SDK (ook wel SPA Editor genoemd)
* De modus Basisstructuur wordt alleen weergegeven als op de pagina een basispagina is geconfigureerd.

## Inhoudsfragmenten en -editor {#content-fragments-amp-editor}

* Nieuwe [Annotaties](/help/assets/content-fragments/content-fragments-variations.md#viewing-editing-deleting-annotations) rail in de Inhoudsfragmenteditor om algemene opmerkingen te maken en opmerkingen in de tekst te bekijken (ook weergegeven in de tijdlijntrack)
* Mogelijkheid om het standaardinhoudstype van een tekstelement met meerdere regels in een [Inhoudsfragmentmodel](/help/assets/content-fragments/content-fragments-models.md) in te stellen op eenvoudige tekst, tekst met opmaak of opmaak
* Voeg [commentaar/annotaties](/help/assets/content-fragments/content-fragments-variations.md#annotating-a-content-fragment) toe door tekst in RTE (volledig-schermmening) te selecteren
* [Vergelijk ](/help/assets/content-fragments/content-fragments-managing.md#comparing-fragment-versions) versies van een inhoudsfragment naast elkaar via referentieslegel
* In het rapport Downloaden van middelen worden nu inhoudsfragmenten dienovereenkomstig weergegeven
* Voeg [Ondersteuning voor inhoudsfragmenten toe aan de HTTP-API](/help/assets/assets-api-content-fragments.md) van Elementen via /api.json. Er zijn API&#39;s voor het maken, bijwerken, lezen en verwijderen van inhoudsfragmenten.

## Ervaringsfragmenten {#experience-fragments}

* Verbeterde indexering van [Experience Fragments](/help/sites-authoring/experience-fragments.md), zodat wordt hun inhoud gevonden in onderzoek naar pagina&#39;s waar zij worden gebruikt
* Met de optie [Exporteren naar doel](/help/sites-administering/experience-fragments-target.md) kunt u het ervaringsfragment nu verzenden als JSON (standaard is HTML) of beide

## Vertaling {#translation}

* Vereenvoudig het creëren van OmzettingsProjecten door de Stramienen van het Project te gebruiken
* Vereenvoudig het uitvoeren van vertaalprojecten door vertaalbanen aan goedgekeurde status door gebrek te plaatsen
* Het bijwerken van vertaalde pagina&#39;s met wijzigingen in het vertaalgeheugen van derden toestaan
* Vertaaltaken in JSON-indeling exporteren toestaan
* Integratie van Microsoft Translation bijwerken naar gebruik van V3 API

## Meersitebeheer (MSM) {#multi-site-management-msm}

* Voor roll-out vormen die PushOnModify gebruiken, betere behandeling van pagina bewegingsverrichting om inconsistente staat te vermijden
* Als u een nieuwe pagina maakt in de bibliotheekstructuur, wordt standaard een zelfstandige pagina gemaakt
* Gebruik MSM-functies in apps van één pagina die de JS SDK gebruiken (ook wel SPA Editor genoemd)

## Lanceringen {#launches}

* Nieuwe revisie- en goedkeuringswerkstroom voor introducties en de mogelijkheid om alleen goedgekeurde startpagina&#39;s te promoten
* Optie [toegevoegd in UI om de Lancering recht na promotiestap te schrappen](/help/sites-authoring/launches-promoting.md#promoting-launch-pages)

## Inhoud richten en simuleren {#content-targeting-simulation}

* De de gegevenslaag van ContextHub en cliënt-zijregelingsmotor JavaScript is bijgewerkt om jQuery 3 door gebrek te gebruiken.

## AEM en Adobe Target {#aem-amp-adobe-target}

>[!CAUTION]
>
>at.js 2.x wordt niet ondersteund met AEM op het punt van de AEM 6.5-release. Gebruik de nieuwste versie van at.js 1.x

* Adobe Target-integratie kan nu de standaard-API van het doel gebruiken. Eerdere versies van AEM gebruiken de Classic HTTP-API van Target, die nu is afgekeurd.
* Adobe Target `mbox.js` versie 63 is inbegrepen. Adobe beveelt ten zeerste aan om over te schakelen op `at.js` v1.x.
* `at.js` versie 1.5.0 is nu inbegrepen. Adobe raadt u aan [Adobe Experience Platform Launch](https://www.adobe.com/experience-platform/launch.html) te gebruiken om `at.js` v1.x op de site te plaatsen.

## AEM en Adobe Analytics {#aem-amp-adobe-analytics}

* `s_code.js` H.27.5 is inbegrepen. Adobe adviseert dat u implementatie aan `AppMeasurement.js` schakelt
* `AppMeasurement.js` v1.8.0 is inbegrepen. Adobe raadt aan om [Adobe Experience Platform Launch](https://www.adobe.com/experience-platform/launch.html) te gebruiken om AppMeasurement.js op de site te plaatsen.

## AEM en handel {#aem-commerce}

De verbeteringen aan het Kader van de Integratie van de Handel zijn op een snellere versiecyclus sinds AEM 6.4. [Meer informatie hier](https://www.adobe.io/apis/experiencecloud/commerce-integration-framework/docs.html).

## Invoegtoepassing Gemeenschappen {#communities-add-on}

Zie [pagina Opmerkingen bij de release van Gemeenschappen](../release-notes/communities-release-notes.md)

## Scherminvoegtoepassing {#screens-add-on}

* Het gebruiken van Lanceringen om toekomstige inhoudsveranderingen voor signaalinhoud te plannen
* Metered playback in een opeenvolgingskanaal
* Automatisch een projectstructuur maken met behulp van een bronbestand, bijvoorbeeld Excel-werkblad

Voor meer details over veranderingen in AEM Screens - zie de Nota&#39;s van de Versie in [de Gids van de Gebruiker van AEM Screens](https://docs.adobe.com/content/help/en/experience-manager-screens/user-guide/aem-screens-introduction.html).
