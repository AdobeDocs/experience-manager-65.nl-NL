---
title: Aanbevolen werkwijzen voor vertaling
description: Zoek naar beste praktijken die door Adobe engineering en consultancyteams worden samengesteld om u te helpen met vertaalprojecten in gebruik worden genomen.
feature: Language Copy
exl-id: 01a81c4b-cb30-4f7e-b281-7194ebb5fc70
solution: Experience Manager, Experience Manager Sites
role: Admin
source-git-commit: eae057caed533ef16bb541b4ad41b8edd7aaa1c7
workflow-type: tm+mt
source-wordcount: '837'
ht-degree: 0%

---

# Aanbevolen werkwijzen voor vertaling{#translation-best-practices}

## Algemeen {#general}

Het maken of uitbreiden van een wereldwijde aanwezigheid op het web kan een complex proces zijn, maar met goede voorspelling en goede planning kunnen AEM uw inspanningen vereenvoudigen en uw wereldwijde bedrijfsdoelstellingen ondersteunen.

* **Plan voor globale uitbreiding** alvorens uw eerste plaats uit te voeren. Het aanpassen van een bestaande site voor wereldwijde dekking op het moment dat de site op korte termijn werd geïmplementeerd, is doorgaans moeilijker dan aan het begin plannen voor wereldwijde uitbreiding:

   * Evalueer de huidige staat van de de localisatierijpheid van uw organisatie. Bepaal of u de **hulpmiddelen** hebt, **processen** en **middelen** op zijn plaats om globale uitbreiding te steunen.
   * Ben zich bewust van **globale verordeningen** en **regionale taalvoorkeur**. Ontwerp flexibele inhoudsstructuren en processen die een veranderende globale bedrijfsomgeving kunnen aanpassen.

* Bepaal a **governance** model dat uw globale zaken steunt en AEM mechanismen zoals MSM en gebruikerstoestemmingen gebruikt om uw gekozen model af te dwingen. Bepaal bijvoorbeeld of inhoud centraal wordt geschreven en naar regio&#39;s/landen wordt &quot;geduwd&quot; of &quot;getrokken&quot;. Bepaal welke inhoud in de geografische gebieden kan worden ontgrendeld en gewijzigd. Bepaal wie verantwoordelijk is voor het initiëren en beheren van vertalingen.
* Als de middelen toestaan, is het best om vertaalactiviteit van een centraal team te beheren dat deskundigheid in de noodzakelijke hulpmiddelen, processen en verkopersverhoudingen kan ontwikkelen.
* **Plan**, **prototype** en **test** uw globale structuur en processen om ervoor te zorgen dat zij de zaken steunen en dat u de vereiste steun van belanghebbenden in de geographies hebt.

## Sitestructuur {#site-structure}

* Wanneer u de sitestructuur ontwerpt, moet u eerst de inhoud bekijken en bepalen waar en in welke taal de inhoud is geschreven. Deze locatie moet het hoogste niveau van uw site zijn.
* De beste praktijk is a **op taal-gebaseerde structuur** met niet meer dan 3 niveaus tussen de top-level auteurs en landplaatsen.
* Gebruik een taal/landsite noemende overeenkomst die **normen W3C** volgt.
* Bepaal hoe inhoud wordt verdeeld over regio&#39;s en landen. Bedenk welke landen talen delen. U wordt aangeraden om taalstramienen te maken, een laag van niet-geactiveerde pagina&#39;s, waarin vertaalde inhoud kan worden gecontroleerd en gewijzigd en vervolgens kan worden geduwd of naar een landsite met dezelfde taal kan worden gesleept.
* Er zijn twee manieren om taalmeesters te maken: het gebruiken van taalexemplaren, en het gebruiken van MSM/levende exemplaren.

   * De taalkopieeraanpak wordt gebruikt door het integratiekader voor vertalen buiten de box te AEM en is daarom de eenvoudigste manier om aan de slag te gaan. Het framework biedt een gebruikersinterface waarmee u in eerste instantie gemakkelijk inhoudwijzigingen van de hoofdtaal (bijvoorbeeld het Engels) kunt doorgeven en vertalen naar de hoofdtaal. Naarmate het project groeit, wordt workflowautomatisering echter steeds noodzakelijker om de vertaling van het toegenomen aantal pagina&#39;s en/of talen te beheren.
   * De MSM/levende exemplaarbenadering kan een alternatief voor geavanceerde gebruiksgevallen zijn, waar de plaatsen groter en complexer zijn. Sterk bestuur en automatisering van de workflow zijn van meet af aan nodig om de complexe overervingsrelaties tussen Engelse en taalmeesters aan te pakken en om het risico van het overschrijven van bestaande vertalingen te verminderen. Deze behandeling kan met de hulp van sommige vertaalschakelaars worden verwezenlijkt. Zie [ MSM en Meertalige Plaatsen ](/help/sites-administering/msm-best-practices.md#msm-and-multilingual-websites) voor meer informatie.

* Als uw hoofdtaal globale variaties heeft, is een optie MSM te gebruiken om een levende kopie van het globale stramien tot stand te brengen voor vertaling. Als bijvoorbeeld wereldwijd schrijven wordt uitgevoerd in een Amerikaanse Engelse master, maakt u een internationale Engelse master als een live kopie en basis voor vertaling naar andere talen.
* Gebruik MSM om landsites te maken van de vertaalde taalstramienen en om inhoud te implementeren voor sites die dezelfde taal delen. De Franse taalmaster kan bijvoorbeeld worden uitgerold naar sites in Frankrijk, België en Zwitserland.
* Plan, prototype en test eerst, alvorens implementatie te beginnen.

## Vertaalprocessen en -methoden {#translation-processes-and-methods}

* Neem de dienstverlener van de a **localisatiedienst (LSP)** met deskundigheid in vertaling en verwante localisatieactiviteiten in dienst. LSPs kan helpen om uw globale zaken te schrapen door een breedte van middelen en technologieën te verstrekken om efficiency te verbeteren en vertaalkosten te besparen:

   * Sommige LSPs is zowel dienst als technologieleveranciers. Er zijn ook standalone technologieleveranciers die vele LSPs toestaan om aan hun vertaalplatforms deel te nemen.
   * Het **AEM Kader van de Vertaling** steunt integratie met een verscheidenheid van leveranciers van vertaaltechnologie voor zowel machine als menselijke vertaling.
   * Leer hoe te [ LSP schakelaars in uw AEM systeem ](/help/sites-administering/translation.md) integreren om inhoudsomzetting te automatiseren, of hoe te om de Projecten van de Vertaling manueel tot stand te brengen, uit te voeren en in te voeren voor het testen en in gevallen waar er geen LSP of vertaaltechnologieleverancier is.

* Kies de methode van de a **vertaling** die het best de inhoud aanpast.

   * **de Menselijke vertaling** is best-geschikt voor inhoud waar het overseinen en de kwaliteitsverwachtingen hoog zijn en de inhoud voor wat tijd op de plaats, zoals de pagina&#39;s van de Marketing zal leven.
   * **de vertaling van de Machine** kan een goede keus voor massavolumes van vertaling zijn wanneer de tijd om te publiceren kritiek is, kwaliteitsverwachtingen worden versoepeld, of de menselijke vertaalkosten zijn belemmerend. De kennisbasis van de steun en door de gebruiker geproduceerde inhoud worden algemeen machine-vertaald.

* Vertrouw op de expertise van lokalisatieserviceproviders, Adobe Consulting en System Integrators om uw meertalige sitestructuur te plannen, te maken en te testen.
