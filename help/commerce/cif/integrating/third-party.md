---
title: AEM en Commerce Integration van derden die Commerce integration framework gebruiken
description: Ondernemingen kunnen aanvullende commerciële oplossingen van derden nodig hebben om hun winkel te bedienen. Het Commerce integration framework (CIF) kan in dergelijke integratiescenario's worden gebruikt om een derdehandelsoplossing met Adobe Experience Manager te verbinden gebruikend I/O Runtime.
thumbnail: cif-third-party-architecture.jpg
exl-id: e99899a4-df86-4108-991a-8b30d303a279
solution: Experience Manager,Commerce
feature: Commerce Integration Framework
role: Admin, Developer
source-git-commit: 10268f617b8a1bb22f1f131cfd88236e7d5beb47
workflow-type: tm+mt
source-wordcount: '489'
ht-degree: 0%

---

# AEM en Commerce-integratie van derden met behulp van Commerce integration framework {#aem-third-party}

De integratie van niet-Adobe Commerce-oplossingen is een algemeen scenario voor CIF. Oplossingen van derden met verschillende API&#39;s en schema&#39;s worden verbonden via een integratielaag.

## Architectuur {#architecture}

De architectuur ziet er als volgt uit:

![&#x200B; AEM niet-Magento/het Overzicht van de Architectuur van de derde partij &#x200B;](../assets//AEM_nonMagento_Architecture.png)

Het doel van deze integratielaag is om API&#39;s en schema&#39;s van derden toe te wijzen aan de ondersteunde Adobe Commerce GraphQL API&#39;s en schema&#39;s buiten de Experience Manager. Dankzij deze inkapseling kunnen de integratielogica en de systemen worden bijgewerkt zonder code in de Experience Manager te wijzigen.

## Oplossingsvereisten voor integratie

Als de Experience Manager op aanvraag gegevens ophaalt, zijn real-time API&#39;s voor de productcatalogus vereist.

>[!TIP]
>
>Als er geen real-time API&#39;s beschikbaar zijn, moet een externe productcache met API&#39;s worden gebruikt voor de integratie. Voorbeeld [&#x200B; Magento open-source &#x200B;](https://business.adobe.com/nl/products/magento/open-source.html).

Het is niet nodig om het volledige schema van GraphQL uit te voeren, enkel de voorwerpen van het schema om de gewenste gebruik-gevallen toe te laten.

## Gebruiksscenario&#39;s voor backend

CIF breidt de Experience Manager uit met realtime toegang tot productcatalogi en tools voor het beheer van productervaring. Deze naadloze integratie laat auteurs toe om tot handelsgegevens toegang te hebben gebruikend ingebedde UIs wanneer nodig zonder de inhoudscontext te verlaten.

De integratie van de API&#39;s van de productcatalogus is vereist om deze gebruiksgevallen te ontgrendelen.

## Voorste gebruikscenario&#39;s

[&#x200B; AEM CIF de Componenten van de Kern &#x200B;](https://github.com/adobe/aem-core-cif-components) wint en ruilt gegevens via de CIF gesteunde Adobe Commerce APIs terug. Om componenten opnieuw te gebruiken, moeten de respectieve APIs worden uitgevoerd.

De aanbeveling voor prestaties kritieke cliënt-zijcomponenten moet direct met de derdeoplossing communiceren om latentie te vermijden.

## Ontwikkeling van integratie {#develop-integration}

De Adobe adviseert gebruikend [&#x200B; Adobe I/O Runtime &#x200B;](https://developer.adobe.com/apis/experienceplatform/runtime.html) voor de integratielaag. Het is opgenomen in de CIF invoegtoepassing voor derden. Aangezien het met een microdienst-als benadering werkt, is het geschikt om gemakkelijk veelvoudige oplossingen te integreren.

De [&#x200B; verwijzingsimplementatie &#x200B;](https://github.com/adobe/commerce-cif-graphql-integration-reference) is een groot uitgangspunt om de integratie aan uw handelsoplossing te bouwen. Hoewel deze functie GraphQL ondersteunt, kan deze ook worden geïntegreerd met elk ander type API, zoals REST.

Deze integratielaag wordt niet vereist als een derdelaag (zoals Mulesoft) beschikbaar is of de integratie bovenop de derdeoplossing wordt gebouwd.

## Vooraf gebouwde connectors {#connectors}

De schakelaars verstrekken een goede aanvang voor projecten. Zij komen met een handel oplossing-specifieke verbinding en gebrek API afbeelding. Deze schakelaars worden gebouwd door derden en niet door Adobe gehandhaafd. Neem contact op met de desbetreffende partner voor meer informatie.

* [&#x200B; SAP Commerce &#x200B;](https://github.com/diconium/commerce-cif-graphql-integration-hybris), die door Diconium wordt gebouwd
* [&#x200B; Commercetools &#x200B;](https://github.com/diconium/commerce-cif-graphql-integration-commercetool), die door Diconium worden gebouwd

>[!TIP]
>
>Terwijl de schakelaars projecten helpen om de handelsintegratie te versnellen, zijn zij niet stop-in-spel. De commerciële oplossingen van de onderneming zijn sterk aangepast en vereisen een douaneintegratie. Goede kennis van het handelsplatform, Adobe Commerce GraphQL-schema&#39;s en Adobe I/O Runtime is vereist.
