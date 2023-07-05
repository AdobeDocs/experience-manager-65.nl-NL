---
title: Authoring - het milieu en de instrumenten
description: Met de websiteconsole kunt u uw website beheren en navigeren. Met behulp van twee deelvensters kan de structuur van uw website worden uitgebreid en kunnen er acties worden uitgevoerd op de vereiste elementen.
uuid: 0a9ce725-042a-4697-81fe-ac86cbab0398
contentOwner: Chris Bohnert
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: page-authoring
content-type: reference
discoiquuid: 67625e62-7035-4eb5-8dd5-6840d775a547
docset: aem65
exl-id: 5d7b6b2e-d1d8-4efe-b9ff-c9542b4e67d7
source-git-commit: 75c6bb87bb06c5ac9378ccebf193b5416c080bb1
workflow-type: tm+mt
source-wordcount: '902'
ht-degree: 0%

---

# Authoring - het milieu en de instrumenten {#authoring-the-environment-and-tools}

De ontwerpomgeving van AEM biedt verschillende mechanismen voor het organiseren en bewerken van uw inhoud. De beschikbare gereedschappen zijn toegankelijk via de verschillende consoles en pagina-editors.

## Sitebeheer {#site-administration}

De **Websites** Met de console kunt u uw website beheren en navigeren. Met behulp van de twee deelvensters kan de structuur van uw website worden uitgebreid en kunt u handelingen uitvoeren op het vereiste element:

![chlimage_1-108](assets/chlimage_1-108.png)

## De pagina-inhoud bewerken {#editing-your-page-content}

Er is een afzonderlijke pagina-editor met de klassieke UI, waarbij de zoeker van de inhoud en de hulpwerkplaats worden gebruikt:

`https://localhost:4502/cf#/content/geometrixx/en/products/triangle.html`

![chlimage_1-109](assets/chlimage_1-109.png)

## Toegang tot Help {#accessing-help}

Diversen **Help** bronnen zijn rechtstreeks toegankelijk vanuit AEM:

en toegang tot [Help van de werkbalken van de console](/help/sites-classic-ui-authoring/author-env-basic-handling.md#accessing-help), kunt u tot de hulp van sidekick ook toegang hebben (gebruikend ? pictogram) bij het bewerken van een pagina:

![Sidekick samengevouwen](do-not-localize/sidekick-collapsed-2.png)

Of door **Help** in het dialoogvenster voor bewerken van specifieke componenten; dit zal contextgevoelige hulp tonen .

## Sidetrap {#sidekick}

De **Componenten** kunt u door de beschikbare componenten bladeren die aan de huidige pagina moeten worden toegevoegd. De vereiste groep kan worden uitgevouwen, waarna een component naar de gewenste locatie op de pagina wordt gesleept.

![chlimage_1-110](assets/chlimage_1-110.png)

## De Inhoudszoeker {#the-content-finder}

De zoekfunctie voor inhoud is een snelle en eenvoudige manier om tijdens het bewerken van een pagina elementen en/of inhoud te zoeken in de opslagplaats.

Met de zoekfunctie voor inhoud kunt u een reeks bronnen zoeken. U kunt desgewenst een item naar een alinea op de pagina slepen:

* [Afbeeldingen](#finding-images)
* [Documenten](#finding-documents)
* [Films](#finding-movies)
* [Dynamic Media-browser](/help/sites-administering/scene7.md#scene7contentbrowser)
* [Pagina&#39;s](#finding-pages)

* [Alinea&#39;s](#referencing-paragraphs-from-other-pages)
* [Producten](#products)
* Of naar [door de website bladeren op de structuur van de gegevensopslagruimte](#the-content-finder)

Met alle opties kunt u [zoeken naar specifieke items](#the-content-finder).

### Afbeeldingen zoeken {#finding-images}

Dit tabblad bevat een overzicht van alle afbeeldingen in de opslagplaats.

Nadat u een afbeeldingsalinea op de pagina hebt gemaakt, kunt u een item naar de alinea slepen.

![chlimage_1-111](assets/chlimage_1-111.png)

### Documenten zoeken {#finding-documents}

Op dit tabblad worden alle documenten in de opslagplaats weergegeven.

Nadat u een alinea Downloaden op de pagina hebt gemaakt, kunt u een item naar de alinea slepen.

![chlimage_1-112](assets/chlimage_1-112.png)

### Films zoeken {#finding-movies}

Op dit tabblad worden films (bijvoorbeeld Flash-items) in de opslagplaats weergegeven.

Nadat u een geschikte alinea (bijvoorbeeld Flash) op de pagina hebt gemaakt, kunt u een item naar de alinea slepen.

![chlimage_1-113](assets/chlimage_1-113.png)

### Producten {#products}

Op dit tabblad worden alle producten weergegeven. Nadat u een geschikte alinea (bijvoorbeeld Product) op de pagina hebt gemaakt, kunt u een item naar de alinea slepen.

![chlimage_1-114](assets/chlimage_1-114.png)

### Pagina&#39;s zoeken {#finding-pages}

Op dit tabblad worden alle pagina&#39;s weergegeven. Dubbelklik op een pagina om deze te openen voor bewerking.

![chlimage_1-115](assets/chlimage_1-115.png)

### Verwijzen naar alinea&#39;s van andere pagina&#39;s {#referencing-paragraphs-from-other-pages}

Op dit tabblad kunt u naar een andere pagina zoeken. Alle alinea&#39;s van die pagina worden weergegeven. Vervolgens kunt u een alinea naar de huidige pagina slepen, waarna een verwijzing naar de oorspronkelijke alinea ontstaat.

![chlimage_1-116](assets/chlimage_1-116.png)

### De weergave Volledige opslagplaats gebruiken {#using-the-full-repository-view}

Op dit tabblad worden alle bronnen in de opslagplaats weergegeven.

![chlimage_1-117](assets/chlimage_1-117.png)

### Zoeken gebruiken met de Inhoudsbrowser {#using-search-with-the-content-browser}

Op alle opties kunt u naar specifieke punten zoeken. Alle tags en bronnen die overeenkomen met het zoekpatroon worden weergegeven:

![screen_shot_2012-02-08at100746am](assets/screen_shot_2012-02-08at100746am.png)

U kunt ook jokertekens gebruiken om te zoeken. Ondersteunde jokertekens zijn:

* `*`
komt overeen met een reeks van nul of meer tekens.

* `?`
komt overeen met één teken.

>[!NOTE]
>
>Er is een pseudo-eigenschap &#39;name&#39; die moet worden gebruikt om een zoekopdracht met jokertekens uit te voeren.

Als er bijvoorbeeld een afbeelding met de naam beschikbaar is:

`ad-nmvtis.jpg`

in de volgende zoekpatronen vindt u het patroon (en alle andere afbeeldingen die overeenkomen met het patroon):

* `name:*nmv*`
* `name:AD*`
overeenkomende tekens *niet* hoofdlettergevoelig.

* `name:ad?nm??is.*`
u kunt om het even welk aantal vervangingen in een vraag gebruiken.

>[!NOTE]
>
>U kunt ook [SQL2](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/org/apache/jackrabbit/commons/query/sql2/package-summary.html) zoeken.

## Referenties weergeven {#showing-references}

AEM kunt u bekijken welke pagina&#39;s zijn gekoppeld aan de pagina waaraan u momenteel werkt.

Verwijzingen naar directe pagina&#39;s weergeven:

1. Selecteer in het zijpaneel de optie **Pagina** tabpictogram.

   ![screen_shot_2012-02-16at83127pm](assets/screen_shot_2012-02-16at83127pm.png)

1. Selecteren **Referenties tonen...** AEM opent het venster Verwijzingen en geeft aan welke pagina&#39;s naar de geselecteerde pagina verwijzen, inclusief de paden.

   ![screen_shot_2012-02-16at83311pm](assets/screen_shot_2012-02-16at83311pm.png)

In bepaalde situaties zijn verdere acties beschikbaar bij de Sidekick, waaronder:

* [Lanceringen](/help/sites-classic-ui-authoring/classic-launches.md)
* [Actieve kopieën](/help/sites-administering/msm.md)

* [Blauwdruk](/help/sites-administering/msm-best-practices.md)

Overige [inter-page verhoudingen kunnen in de console van Websites worden gezien](/help/sites-classic-ui-authoring/author-env-basic-handling.md#page-information-on-the-websites-console).

## Controlelogboek {#audit-log}

De **Controlelogboek** kan worden benaderd vanuit de **Informatie** tabblad van het hulpwerkje. In het verslag worden de recente acties vermeld die op de huidige pagina zijn ondernomen; bijvoorbeeld:

![chlimage_1-118](assets/chlimage_1-118.png)

## Pagina-informatie {#page-information}

De websiteconsole [biedt informatie over de huidige status van de pagina](/help/sites-classic-ui-authoring/author-env-basic-handling.md#page-information-on-the-websites-console) zoals publicatie, wijziging, vergrendeld, livecopy, enz.

## Paginamodi {#page-modes}

Wanneer u een pagina bewerkt met de klassieke UI, zijn er verschillende modi die kunnen worden geopend met de pictogrammen onder aan het zijpaneel:

![Paginamodi](do-not-localize/chlimage_1-12.png)

De rij met pictogrammen onder aan de Sidekick wordt gebruikt voor het schakelen tussen modi voor het werken met de pagina&#39;s:

* [Bewerken](/help/sites-classic-ui-authoring/classic-page-author-edit-mode.md)
Dit is de standaardmodus, waarmee u de pagina kunt bewerken, componenten kunt toevoegen of verwijderen en andere wijzigingen kunt aanbrengen.

* [Voorvertoning](/help/sites-classic-ui-authoring/classic-page-author-edit-content.md#previewing-pages)
In deze modus kunt u een voorvertoning van de pagina weergeven alsof deze in de uiteindelijke vorm op uw website wordt weergegeven.

* [Ontwerp](/help/sites-classic-ui-authoring/classic-page-author-design-mode.md#main-pars-procedure-0)
In deze modus kunt u het ontwerp van de pagina bewerken door de toegankelijke componenten te configureren.

>[!NOTE]
>
>Er zijn ook andere opties beschikbaar:
>
>* [Basisstructuur](/help/sites-classic-ui-authoring/classic-feature-scaffolding.md)
>* [Clientcontext](/help/sites-administering/client-context.md)
>* Websites - hiermee opent u de websiteconsole.
>* Opnieuw laden - De pagina wordt vernieuwd.

## Sneltoetsen {#keyboard-shortcuts}

Diversen [sneltoetsen](/help/sites-classic-ui-authoring/classic-page-author-keyboard-shortcuts.md) zijn beschikbaar.
