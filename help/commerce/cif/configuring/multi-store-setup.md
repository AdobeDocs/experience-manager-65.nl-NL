---
title: Multi-Store-installatie voor handel
description: Leer hoe u meerdere winkelweergaven van Magento tot AEM kunt toewijzen. Hierdoor kunnen projecten ondersteuning bieden voor meertalige en meertalige gebruiksgevallen.
sub-product: Handel
doc-type: technical-video
activity: setup
audience: administrator
feature: Kader voor integratie in de handel
kt: 3046
thumbnail: 28952.jpg
translation-type: tm+mt
source-git-commit: d92a635d41cf1b14e109c316bd7264cf7d45a9fe
workflow-type: tm+mt
source-wordcount: '382'
ht-degree: 0%

---

# Commerce Multi-Store Setup {#multi-store}

De AEM CIF Core Componenten kunnen op veelvoudige AEM plaatsstructuren worden gebruikt en de onderliggende cliënt GraphQL implementatie kan met verschillende Magento opslag/opslagmeningen verbinden. Hierdoor kunnen projecten complexe multistore-/multisite-instellingen implementeren.

In een video wordt een overzicht gegeven van de opties voor het integreren van meerdere Magento Store Views met Adobe Experience Manager Sites.

>[!VIDEO](https://video.tv.adobe.com/v/28952/?quality=12)

AEM functies voor beheer van meerdere sites van Live Copy en Language Copy worden in combinatie met het Commerce Integration Framework gebruikt om sites wereldwijd te beheren in verschillende regio&#39;s en regio&#39;s.

De geadviseerde opstelling is een 1:1 verhouding tussen AEM plaats en de opslagmening van de Magento te gebruiken.

Volg onderstaande stappen om een AEM-site aan te sluiten en CIF Core-componenten te AEM zodat ook deze kunnen worden gekoppeld aan een toegewijde winkelweergave:

## Configuratie {#configuration}

1. Meerdere winkels configureren en weergaven opslaan volgens het patroon dat wordt beschreven in [Magento Websites, Winkels en weergaven](https://docs.magento.com/m2/ce/user_guide/stores/websites-stores-views.html)

2. Zorg ervoor dat de verbinding tussen AEM &amp; Magento werkt.

3. Creeer een kindconfiguratie van CIF Cloud Service config die deze stappen volgt:

   * Ga in AEM naar Extra -> Algemeen -> [Configuratiebrowser](/help/sites-administering/configurations.md#using-configuration-browser)
   * Selecteer de basisconfiguratie die u hebt gemaakt
   * Een nieuwe configuratie maken met de stappen die hierboven in punt 2 worden beschreven

   Deze nieuwe configuratie zal als kindconfiguratie van de basis worden gecreeerd. U kunt nu naar Extra -> Algemeen -> Browser van de Configuratie gaan en de configuratiemontages creëren.

   >[!TIP]
   >
   > Commerciële catalogi kunnen worden geadresseerd met behulp van id&#39;s of UID&#39;s. UID&#39;s zijn geïntroduceerd in Magento 2.4.2. Laat slechts dit toe als uw handels achterkant een schema GraphQL van versie 2.4.2 of later steunt.

4. Wijs de kindconfiguratie aan een AEM plaats toe

   * Ga naar AEM Sites-console
   * Navigeer naar het gebied of de hoofdtaal van uw sitestructuur, bijvoorbeeld /content/venia/us _of_ /content/venia/us/nl
   * Pagina-eigenschappen selecteren en pagina-eigenschappen openen
   * Selecteer het tabblad Geavanceerd
   * Selecteer in de sectie `Configuration` de configuratie die u stapsgewijs hebt gemaakt

## Aanvullende bronnen

* [Magento-websites, -winkels en -weergaven](https://docs.magento.com/m2/ce/user_guide/stores/websites-stores-views.html)
* [AEM CIF Core-componenten - Configuratie van meerdere winkels/sites](https://github.com/adobe/aem-core-cif-components/wiki/configuration#multi-store--site-configuration)
* [Beheer van meerdere sites gebruiken](https://docs.adobe.com/content/help/en/experience-manager-learn/sites/translation/multi-site-manager-feature-video-use.html)
* [Inhoud opnieuw gebruiken: Beheer van meerdere sites en Live Copy](/help/sites-administering/msm.md)
