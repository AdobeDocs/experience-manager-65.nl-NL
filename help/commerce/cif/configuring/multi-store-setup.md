---
title: Commerce Multi-Store Setup
description: Leer hoe u meerdere winkelweergaven van Adobe Commerce aan AEM kunt toewijzen. Hierdoor kunnen projecten ondersteuning bieden voor meertalige en meertalige gebruiksgevallen.
sub-product: Commerce
doc-type: technical-video
activity: setup
audience: administrator
feature: Commerce Integration Framework
exl-id: 1d4e9b7b-848b-4007-b884-dd48682d62e8
solution: Experience Manager,Commerce
role: Admin, Developer
source-git-commit: 10268f617b8a1bb22f1f131cfd88236e7d5beb47
workflow-type: tm+mt
source-wordcount: '369'
ht-degree: 0%

---

# Commerce Multi-Store Setup {#multi-store}

De AEM CIF Core Components kunnen op meerdere AEM sitestructuren worden gebruikt en de onderliggende GraphQL client-implementatie kan verbinding maken met verschillende Adobe Commerce-winkels/winkelweergaven. Hierdoor kunnen projecten complexe multistore-/multisite-instellingen implementeren.

In een video wordt een overzicht gegeven van de opties voor het integreren van meerdere Adobe Commerce Store Views met Adobe Experience Manager Sites.

>[!VIDEO](https://video.tv.adobe.com/v/28952/?quality=12)

AEM functies voor beheer van meerdere sites van Live Copy en Taal Copy worden samen met het Commerce integration framework gebruikt om sites wereldwijd te beheren in verschillende regio&#39;s en regio&#39;s.

De aanbevolen setup bestaat uit het gebruik van een 1:1-relatie tussen de AEM site en de Adobe Commerce-winkelweergave.

Voer de onderstaande stappen uit om een AEM-site te verbinden en CIF Core Components ook aan een toegewijde winkelweergave te AEM:

## Configuratie {#configuration}

1. Vorm veelvoudige opslag &amp; opslagmeningen volgens het patroon dat in [&#x200B; wordt beschreven Websites van Adobe Commerce, Opslag &amp; Weergaven &#x200B;](https://experienceleague.adobe.com/docs/commerce-admin/start/setup/websites-stores-views.html?lang=nl-NL)

2. Controleer of de verbinding tussen AEM en Adobe Commerce werkt.

3. Creeer een kindconfiguratie van CIF Cloud Service config die deze stappen volgt:

   * In AEM gaan naar Hulpmiddelen > Algemeen > [&#x200B; Browser van de Configuratie &#x200B;](/help/sites-administering/configurations.md#using-configuration-browser)
   * Selecteer de basisconfiguratie die u hebt gemaakt
   * Een configuratie maken met de stappen die hierboven in punt 2 worden beschreven

   Deze nieuwe configuratie wordt gecreeerd als kindconfiguratie van de basis. U kunt nu naar Extra > Algemeen > de Browser van de Configuratie gaan en de configuratiemontages creëren.

   >[!TIP]
   >
   >Commerce-catalogi kunnen worden geadresseerd met behulp van id&#39;s of UID&#39;s. UID&#39;s zijn geïntroduceerd in Adobe Commerce 2.4.2. Schakel deze optie alleen in als uw commerciële backend een GraphQL-schema van versie 2.4.2 of hoger ondersteunt.

4. Wijs de kindconfiguratie aan een AEM plaats toe

   * Ga naar de AEM Sites-console
   * Navigeer aan het gebied of de taalwortel van uw plaatsstructuur, bijvoorbeeld, /content/venia/us _of_ /content/venia/us/nl voor de Venia steekproefpagina
   * Selecteer de pagina en open de pagina-eigenschappen
   * Selecteer het tabblad Geavanceerd
   * Selecteer in de sectie `Configuration` de configuratie die u bij stap hebt gemaakt

## Aanvullende bronnen

* [&#x200B; Websites van Adobe Commerce, Opslag &amp; Mening &#x200B;](https://experienceleague.adobe.com/docs/commerce-admin/start/setup/websites-stores-views.html?lang=nl-NL)
* [&#x200B; AEM CIF de Componenten van de Kern - de Configuratie van de Multistore/van de plaats &#x200B;](https://github.com/adobe/aem-core-cif-components#multi-store--site-configuration)
* [&#x200B; Gebruikend Manager Van meerdere plaatsen &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-learn/sites/translation/multi-site-manager-feature-video-use.html?lang=nl-NL)
* [Inhoud opnieuw gebruiken: Sitebeheer en Live kopiëren](/help/sites-administering/msm.md)
