---
title: Verbinding maken met Microsoft Translator
seo-title: Verbinding maken met Microsoft Translator
description: Leer hoe u AEM verbindt met Microsoft Translator.
seo-description: Leer hoe u AEM verbindt met Microsoft Translator.
uuid: 5e3916ec-36a0-4d31-94ff-c340a462411a
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: site-features
content-type: reference
discoiquuid: a7958411-b509-428e-bbe2-42efe8fd1add
translation-type: tm+mt
source-git-commit: 8b6801a4efd45fa49e009e1d6876d21c4cded957
workflow-type: tm+mt
source-wordcount: '616'
ht-degree: 0%

---


# Verbinding maken met Microsoft Translator{#connecting-to-microsoft-translator}

Maak een configuratie voor de Microsoft Translator-cloudservice waarmee u uw Microsoft Translation-account kunt gebruiken voor het vertalen van AEM pagina-inhoud, community-inhoud of middelen.

| Eigenschap | Beschrijving |
|---|---|
| Vertaallabel | De weergavenaam voor de vertaalservice. |
| Vertaalkenmerk | (Optioneel) Voor door de gebruiker gegenereerde inhoud, de toewijzing die naast vertaalde tekst wordt weergegeven, bijvoorbeeld `Translations by Microsoft`. |
| Werkruimte-id | (Optioneel) De id van de aangepaste Microsoft Translator-engine die u wilt gebruiken. |
| Subscription Key | Uw Microsoft Subscription Key voor Microsoft Translator. |

Nadat u de configuratie creeert, moet u [het ](/help/sites-administering/tc-msconf.md#activating-the-translator-service-configurations) activeren.

In de volgende procedure wordt gebruikgemaakt van de interface die is geoptimaliseerd voor aanrakingen om een Microsoft Translator-configuratie te maken.

1. Klik of tik op Gereedschappen > Cloud Services.
1. Klik of tik op Configuraties tonen in het gedeelte Microsoft Translator.
1. Klik op de koppeling + naast Beschikbare configuraties.

   ![chlimage_1-382](assets/chlimage_1-382.png)

1. Typ een titel voor de configuratie. De titel identificeert de configuratie in de console van Cloud Services evenals in de drop-down lijsten van het paginabezit. De standaardnaam is gebaseerd op de titel. Typ desgewenst een naam die u wilt gebruiken voor het knooppunt in de opslagplaats dat de configuratie opslaat. U zou de standaardwaarde voor het bezit van de Configuratie van de Ouder moeten gebruiken dat de weg van de gegevensopslaggegevensopslagknoop is.
1. Klik op Maken.
1. Typ in het dialoogvenster dat wordt weergegeven waarden voor de eigenschappen en klik op OK.

## Voorbeeld van Microsoft Translator Cloud Service Configurations {#sample-microsoft-translator-cloud-service-configurations}

De volgende Microsoft Translator-cloudserviceconfiguraties worden samen met de Geometrixx-voorbeelden geïnstalleerd. Sommige voorbeeldconfiguraties gebruiken een proefaccount van Microsoft Translation waarmee maximaal 2 000 000 gratis vertaalde tekens per maand kunnen worden gebruikt.

### Microsoft Translator-proeflicentie {#microsoft-translator-trial-license}

De configuratie van de Vergunning van de Vergunning van de Proefproef van Microsoft is een steekproefconfiguratie die met het de steekproefpakket van Geometrixx Outdoors geïnstalleerd is. Deze configuratie gebruikt een rekening van de Vertaler van Microsoft die een vrij abonnement heeft dat 2 000 000 vertaalde karakters per maand toestaat.

### Licentie voor proefversie van Microsoft Translator - Geometrixx-outdoor {#microsoft-translator-trial-license-geometrixx-outdoors}

De proefvergunning van de Vertaler van Microsoft - Geometrixx-outdoor configuratie is een steekproefconfiguratie die met Geometrixx Outdoors geïnstalleerd is. Deze configuratie gebruikt dezelfde gratis Microsoft Translator-account als de configuratie voor proefversies van Microsoft Translator. Het account heeft een gratis abonnement dat 2 000 000 vertaalde tekens per maand toestaat.

Deze Microsoft Translator-configuratie is geoptimaliseerd voor gebruik met het type inhoud van de voorbeeldsite Geometrixx Outdoors.

### De Microsoft Translator-configuratie voor proefversies van licenties {#upgrading-the-microsoft-translator-trial-license-configuration} bijwerken

De de configuratiepagina&#39;s van de Vertaling van Microsoft verstrekken een geschikte verbinding aan de website van Microsoft voor het verkrijgen van een rekeningsabonnement dat voor productiesystemen adequaat is.

1. Klik of tik op Gereedschappen > Bewerkingen > Wolk > Cloud Services.
1. Klik of tik in het gedeelte Microsoft Translator op Configuraties tonen en klik of tik vervolgens op de proefversie van Microsoft Translator (Microsoft Translation Configuration).

   ![chlimage_1-383](assets/chlimage_1-383.png)

1. Voor de configuratiepagina, klik de Abonnement van de Verbetering. Gebruik de Microsoft-webpagina die wordt geopend om uw account te configureren.

   ![chlimage_1-384](assets/chlimage_1-384.png)

### De Microsoft Translator Engine {#customizing-your-microsoft-translator-engine} aanpassen

De de configuratiepagina&#39;s van de Vertaling van Microsoft verstrekken een gemakkelijke verbinding aan de website van Microsoft voor het aanpassen van uw Vertaalmachine van Microsoft. ([https://hub.microsofttranslator.com](https://hub.microsofttranslator.com/))

1. Klik of tik op Gereedschappen > Bewerkingen > Wolk > Cloud Services.
1. Klik of tik in het gedeelte Microsoft Translator op Configuraties tonen en klik of tik vervolgens op de configuratie die u wilt aanpassen.
1. Klik op Vertaler aanpassen op de configuratiepagina. Gebruik de Microsoft-webpagina die wordt geopend om uw service aan te passen.

## De configuraties van de vertaalservice activeren {#activating-the-translator-service-configurations}

U moet uw configuraties van de wolkendienst activeren om vertaalde inhoud te steunen die aan de publicatie instantie wordt herhaald. Gebruik de methode van [het activeren van een volledige sectie (boom)](/help/sites-authoring/publishing-pages.md#publishing-and-unpublishing-a-tree) om de opslaggegevensopslagknopen te activeren die de configuraties van de Vertaler van Microsoft of van de derdewoldienst opslaan. De knooppunten bevinden zich onder de volgende bovenliggende knooppunten:

* Microsoft Translation Service: /libs/settings/cloudconfigs/vertaling/msft-vertaling
* Vertaling door derden: /etc/cloudservices/machine-vertaling

