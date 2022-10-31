---
title: Multi-Store-installatie voor handel
description: Leer hoe u meerdere winkelweergaven van Adobe Commerce aan AEM koppelt. Hierdoor kunnen projecten ondersteuning bieden voor meertalige en meertalige gebruiksgevallen.
sub-product: Commerce
doc-type: technical-video
activity: setup
audience: administrator
feature: Commerce Integration Framework
kt: 3046
thumbnail: 28952.jpg
exl-id: 1d4e9b7b-848b-4007-b884-dd48682d62e8
source-git-commit: a5f3e33a6abe7ac1bbd610a8528fd599d1ffd2aa
workflow-type: tm+mt
source-wordcount: '385'
ht-degree: 0%

---

# Multi-Store-installatie voor handel {#multi-store}

De AEM CIF Core-componenten kunnen worden gebruikt op meerdere AEM-sitestructuren en de onderliggende GraphQL-clientimplementatie kan verbinding maken met verschillende Adobe Commerce-winkels/winkelweergaven. Hierdoor kunnen projecten complexe multistore-/multisite-instellingen implementeren.

In een video wordt een overzicht gegeven van de opties voor het integreren van meerdere Adobe Commerce Store Views met Adobe Experience Manager Sites.

>[!VIDEO](https://video.tv.adobe.com/v/28952/?quality=12)

AEM functies voor beheer van meerdere sites van Live Copy en Language Copy worden in combinatie met het Commerce Integration Framework gebruikt om sites wereldwijd te beheren in verschillende regio&#39;s en regio&#39;s.

De aanbevolen setup bestaat uit het gebruik van een 1:1-relatie tussen AEM site en de Adobe Commerce-winkelweergave.

Voer de onderstaande stappen uit om een AEM-site aan te sluiten en CIF Core-componenten te AEM aan een speciale winkelweergave:

## Configuratie {#configuration}

1. Meerdere winkels configureren en weergaven opslaan volgens het in [Adobe Commerce-websites, -winkels en -weergaven](https://docs.magento.com/m2/ce/user_guide/stores/websites-stores-views.html)

2. Controleer of de verbinding tussen AEM en Adobe Commerce werkt.

3. Creeer een kindconfiguratie van CIF Cloud Service config die deze stappen volgt:

   * Ga AEM naar Gereedschappen -> Algemeen -> [Configuratiebrowser](/help/sites-administering/configurations.md#using-configuration-browser)
   * Selecteer de basisconfiguratie die u hebt gemaakt
   * Een nieuwe configuratie maken met de stappen die hierboven in punt 2 worden beschreven

   Deze nieuwe configuratie zal als kindconfiguratie van de basis worden gecreeerd. U kunt nu naar Extra -> Algemeen -> Browser van de Configuratie gaan en de configuratiemontages creëren.

   >[!TIP]
   >
   >Commerciële catalogi kunnen worden benaderd met behulp van id&#39;s of UID&#39;s. UID&#39;s zijn geïntroduceerd in Adobe Commerce 2.4.2. Laat slechts dit toe als uw handels achterkant een schema GraphQL van versie 2.4.2 of later steunt.

4. Wijs de kindconfiguratie aan een AEM plaats toe

   * Ga naar AEM Sites-console
   * Navigeer naar het gebied of de taalhoofdmap van de sitestructuur, bijvoorbeeld /content/venia/us _of_ /content/venia/us/nl voor de voorbeeldpagina van Venia
   * Pagina-eigenschappen selecteren en pagina-eigenschappen openen
   * Selecteer het tabblad Geavanceerd
   * In de `Configuration` de sectie selecteert de configuratie u bij stap creeerde

## Aanvullende bronnen

* [Adobe Commerce-websites, -winkels en -weergaven](https://docs.magento.com/m2/ce/user_guide/stores/websites-stores-views.html)
* [AEM CIF Core-componenten - Configuratie van meerdere winkels/sites](https://github.com/adobe/aem-core-cif-components/wiki/configuration#multi-store--site-configuration)
* [Beheer van meerdere sites gebruiken](https://experienceleague.adobe.com/docs/experience-manager-learn/sites/translation/multi-site-manager-feature-video-use.html)
* [Inhoud opnieuw gebruiken: Beheer van meerdere sites en Live Copy](/help/sites-administering/msm.md)
