---
title: Aanbevolen werkwijzen voor vertaling
seo-title: Aanbevolen werkwijzen voor vertaling
description: Zoek naar beste praktijken die door Adobe engineering en adviesteams worden gecompileerd om u te helpen met vertaalprojecten aan de slag te gaan.
seo-description: Zoek naar beste praktijken die door Adobe engineering en adviesteams worden gecompileerd om u te helpen met vertaalprojecten aan de slag te gaan.
uuid: 3bac1d73-9696-4c9b-8bdd-6f00fac40cf7
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: site-features, best-practices
content-type: reference
discoiquuid: 1554010e-a1d1-4edf-b28f-9eead8f83b4a
translation-type: tm+mt
source-git-commit: a929252a13f66da8ac3e52aea0655b12bdd1425f
workflow-type: tm+mt
source-wordcount: '859'
ht-degree: 0%

---


# Aanbevolen werkwijzen voor vertaling{#translation-best-practices}

## Algemeen {#general}

Het maken of uitbreiden van een wereldwijde aanwezigheid op het web kan een complex proces zijn, maar met goede voorspelling en goede planning kunnen AEM uw inspanningen vereenvoudigen en uw wereldwijde bedrijfsdoelstellingen ondersteunen.

* **Plan voor globale uitbreiding** alvorens uw eerste plaats uit te voeren. Het aanpassen van een bestaande site voor wereldwijde dekking op het moment dat de site op korte termijn werd geïmplementeerd, is doorgaans moeilijker dan aan het begin plannen voor wereldwijde uitbreiding:

   * Evalueer de huidige staat van de de localisatierijpheid van uw organisatie. Bepaal of u de **hulpmiddelen**, de **processen** en de **middelen** op zijn plaats hebt om globale uitbreiding te steunen.
   * Wees op de hoogte van **wereldwijde regels** en **regionale taalvoorkeuren**. Ontwerp flexibele inhoudsstructuren en processen die een veranderende globale bedrijfsomgeving kunnen aanpassen.

* Bepaal een **governancemodel** dat uw globale zaken steunt en AEM mechanismen zoals MSM en gebruikerstoestemmingen gebruikt om uw gekozen model af te dwingen. Bepaal bijvoorbeeld of inhoud centraal wordt geschreven en naar regio&#39;s/landen wordt &quot;geduwd&quot; of &quot;getrokken&quot;. Bepaal welke inhoud in de geografische gebieden kan worden ontgrendeld en gewijzigd. Bepaal wie verantwoordelijk is voor het initiëren en beheren van vertalingen.
* Als de middelen toestaan, is het best om vertaalactiviteit van een centraal team te beheren dat deskundigheid in de noodzakelijke hulpmiddelen, processen en verkopersverhoudingen kan ontwikkelen.
* **Plan**, **prototype** en **test** uw globale structuur en processen om ervoor te zorgen dat zij de zaken steunen en dat u de vereiste steun van belanghebbenden in de aardrijkskunde hebt.

## Sitestructuur {#site-structure}

* Wanneer u de sitestructuur ontwerpt, moet u eerst de inhoud bekijken en bepalen waar en in welke taal de inhoud is geschreven. Deze locatie moet het hoogste niveau van uw site zijn.
* De beste praktijken zijn een op **taal-gebaseerde structuur** met niet meer dan drie niveaus tussen de top-level auteurspartij en landplaatsen.
* Gebruik een naamgevingsconventie voor talen/landsites die voldoet aan de **W3C-standaarden**.
* Bepaal hoe inhoud wordt verdeeld over regio&#39;s en landen. Bedenk welke landen talen delen. U wordt aangeraden om taalstramienen te maken, een laag van niet-geactiveerde pagina&#39;s, waarin vertaalde inhoud kan worden gecontroleerd en gewijzigd en vervolgens kan worden geduwd of naar een landsite met dezelfde taal kan worden gesleept.
* Er zijn twee manieren om taalstramienen te maken: het gebruiken van taalexemplaren, en het gebruiken van MSM/levende exemplaren.

   * De taalkopieerbenadering wordt gebruikt door AEM out-of-the-box vertaalintegratieframework, en daarom is het de eenvoudigste manier om aan de slag te gaan. Het framework biedt een gebruikersinterface die het in eerste instantie gemakkelijk maakt om wijzigingen in de inhoud vanuit de hoofdtaal (bijvoorbeeld het Engels) master door te geven en te vertalen naar de taalmeesters. Naarmate het project groeit, wordt workflowautomatisering echter steeds noodzakelijker om de vertaling van het toegenomen aantal pagina&#39;s en/of talen te beheren.
   * De MSM/levende exemplaarbenadering kan een alternatief voor geavanceerde gebruiksgevallen zijn, waar de plaatsen groter en complexer zijn. Sterk bestuur en automatisering van de workflow zijn van meet af aan nodig om de complexe overervingsrelaties tussen Engelse en taalmeesters aan te pakken en het risico van het overschrijven van bestaande vertalingen te verminderen. Deze behandeling kan met de hulp van sommige vertaalschakelaars worden verwezenlijkt. Zie [MSM en Meertalige Plaatsen](/help/sites-administering/msm-best-practices.md#msm-and-multilingual-websites) voor meer informatie.

* Als uw master taal globale variaties heeft, is een optie MSM te gebruiken om een levende kopie van algemeen master tot stand te brengen voor vertaling te gebruiken. Als bijvoorbeeld wereldwijd schrijven wordt uitgevoerd in een Amerikaans master Engels, maakt u een internationaal master Engels als een live kopie en als basis voor vertaling naar andere talen.
* Gebruik MSM om landsites te maken van de vertaalde taalstramienen en om inhoud te implementeren voor sites die dezelfde taal delen. De master Franse taal kan bijvoorbeeld worden uitgerold naar de sites van Frankrijk, België en Zwitserland.
* Plan, prototype en test eerst, alvorens implementatie te beginnen.

## Vertaalprocessen en -methoden {#translation-processes-and-methods}

* Neem een **lokalisatiedienstverlener (LSP)** met deskundigheid op het gebied van vertaling en verwante localisatieactiviteiten in dienst. LSPs kan helpen om uw globale zaken te schrapen door een breedte van middelen en technologieën te verstrekken om efficiency te verbeteren en vertaalkosten te besparen:

   * Sommige LSPs is zowel dienst als technologieleveranciers. Er zijn ook standalone technologieleveranciers die vele LSPs toestaan om aan hun vertaalplatforms deel te nemen.
   * Het **AEM vertaalkader** ondersteunt integratie met een groot aantal aanbieders van vertaaltechnologie voor zowel machines als menselijke vertaling.
   * Leer hoe u LSP-connectors in uw AEM [kunt](/help/sites-administering/translation.md) integreren om content transleren te automatiseren, of hoe u handmatig vertaalprojecten kunt maken, exporteren en importeren voor testdoeleinden en in gevallen waarin er geen LSP- of vertaaltechnologieprovider is.

* Kies een **vertaalmethode** die het beste bij de inhoud past.

   * **De menselijke vertaling** is best-geschikt voor inhoud waar het overseinen en de kwaliteitsverwachtingen hoog zijn en de inhoud zal voor een bepaalde tijd op de plaats, zoals de pagina&#39;s van de Marketing leven.
   * **Machinevertaling** kan een goede keuze zijn voor grote hoeveelheden vertalingen als de tijd om te publiceren kritiek is, de kwaliteitsverwachtingen worden versoepeld of de vertaalkosten voor mensen onbetaalbaar zijn. De kennisbasis van de steun en door de gebruiker geproduceerde inhoud worden algemeen machine-vertaald.

* Vertrouw op expertise van lokalisatieserviceproviders, Adobe Consulting en System Integrators om uw meertalige sitestructuur te plannen, te maken en te testen.

