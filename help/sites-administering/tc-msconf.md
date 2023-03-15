---
title: Verbinding maken met Microsoft Translator
seo-title: Connecting to Microsoft Translator
description: Leer hoe u verbinding maakt AEM met Microsoft Translator.
seo-description: Learn how to connect AEM to Microsoft Translator.
uuid: 5e3916ec-36a0-4d31-94ff-c340a462411a
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: site-features
content-type: reference
discoiquuid: a7958411-b509-428e-bbe2-42efe8fd1add
feature: Language Copy
exl-id: ca575a30-fc3e-4f38-9aa7-dbecbc089f87
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '604'
ht-degree: 0%

---

# Verbinding maken met Microsoft Translator{#connecting-to-microsoft-translator}

Maak een configuratie voor de Microsoft Translator Cloud Service om uw Microsoft Translation-account te gebruiken voor het vertalen van AEM pagina-inhoud, community-inhoud of middelen.

| Eigenschap | Beschrijving |
|---|---|
| Vertaallabel | De weergavenaam voor de vertaalservice. |
| Vertaalkenmerk | (Optioneel) Voor door de gebruiker gegenereerde inhoud wordt bijvoorbeeld de toewijzing naast vertaalde tekst weergegeven `Translations by Microsoft`. |
| Werkruimte-id | (Optioneel) De id van de aangepaste Microsoft Translator-engine die u wilt gebruiken. |
| Subscription Key | Je Microsoft Subscription Key voor Microsoft Translator. |

Nadat u de configuratie creeert, moet u [activeren](/help/sites-administering/tc-msconf.md#activating-the-translator-service-configurations).

In de volgende procedure wordt gebruikgemaakt van de geoptimaliseerde gebruikersinterface voor het maken van een Microsoft Translator-configuratie.

1. Klik of tik op Gereedschappen > Cloud Services.
1. Klik of tik op Configuraties tonen in het gebied Microsoft Translator.
1. Klik op de koppeling + naast Beschikbare configuraties.

   ![chlimage_1-382](assets/chlimage_1-382.png)

1. Typ een titel voor de configuratie. De titel identificeert de configuratie in de console van Cloud Services evenals in de drop-down lijsten van het paginabezit. De standaardnaam is gebaseerd op de titel. Typ desgewenst een naam die u wilt gebruiken voor het knooppunt in de opslagplaats dat de configuratie opslaat. U zou de standaardwaarde voor het bezit van de Configuratie van de Ouder moeten gebruiken dat de weg van de gegevensopslaggegevensopslagknoop is.
1. Klik op Maken.
1. Typ in het dialoogvenster dat wordt weergegeven waarden voor de eigenschappen en klik op OK.

## Voorbeeld van configuraties voor Microsoft Translator Cloud Service {#sample-microsoft-translator-cloud-service-configurations}

De volgende Microsoft Translator-cloudserviceconfiguraties worden samen met de Geometrixx-voorbeelden geïnstalleerd. Sommige voorbeeldconfiguraties maken gebruik van een proefaccount voor Microsoft Translation, waarbij maximaal 2 000 000 gratis vertaalde tekens per maand zijn toegestaan.

### Proeflicentie voor Microsoft Translator {#microsoft-translator-trial-license}

De Microsoft Translator-testlicentieconfiguratie is een voorbeeldconfiguratie die wordt geïnstalleerd met het voorbeeldpakket voor Geometrixx Outdoors. In deze configuratie wordt een Microsoft Translator-account gebruikt met een gratis abonnement dat 2 000 000 vertaalde tekens per maand toestaat.

### Microsoft Vergunning voor proefversie - Geometrixx-outdoor {#microsoft-translator-trial-license-geometrixx-outdoors}

De Microsoft Translator-proeflicentie - configuratie voor Geometrixx-buitenshuis is is een voorbeeldconfiguratie die is geïnstalleerd met Geometrixx Outdoors. Deze configuratie gebruikt dezelfde gratis Microsoft Translator-account als de configuratie voor proefversies van Microsoft Translator. Het account heeft een gratis abonnement dat 2 000 000 vertaalde tekens per maand toestaat.

Deze Microsoft Translator-configuratie is geoptimaliseerd voor gebruik met het type inhoud van de voorbeeldsite voor Geometrixx Outdoors.

### De Microsoft Translator-licentieconfiguratie voor proefversies bijwerken {#upgrading-the-microsoft-translator-trial-license-configuration}

Microsoft-vertaalconfiguratiepagina&#39;s bieden een handige koppeling naar de Microsoft-website voor het verkrijgen van een accountabonnement dat geschikt is voor productiesystemen.

1. Klik of tik op Gereedschappen > Bewerkingen > Wolk > Cloud Services.
1. Klik of tik in het gedeelte Microsoft Translator op Configurations tonen en klik of tik op Microsoft Translator Trial License (Microsoft Translation Configuration).

   ![chlimage_1-383](assets/chlimage_1-383.png)

1. Voor de configuratiepagina, klik de Abonnement van de Verbetering. Gebruik de Microsoft-webpagina die wordt geopend om uw account te configureren.

   ![chlimage_1-384](assets/chlimage_1-384.png)

### De Microsoft Translator Engine aanpassen {#customizing-your-microsoft-translator-engine}

Microsoft Translation Configuration-pagina&#39;s bieden een handige koppeling naar de Microsoft-website om uw Microsoft Translator-engine aan te passen. ([https://hub.microsofttranslator.com](https://hub.microsofttranslator.com/))

1. Klik of tik op Gereedschappen > Bewerkingen > Wolk > Cloud Services.
1. Klik of tik op Configuraties tonen in het gebied Microsoft Translator en klik op de configuratie die u wilt aanpassen.
1. Klik op Vertaler aanpassen op de configuratiepagina. Gebruik de Microsoft-webpagina die wordt geopend om uw service aan te passen.

## De configuraties van de vertaalservice activeren {#activating-the-translator-service-configurations}

U moet uw configuraties van de wolkendienst activeren om vertaalde inhoud te steunen die aan de publicatie instantie wordt herhaald. Gebruik de methode [een volledige sectie activeren (boomstructuur)](/help/sites-authoring/publishing-pages.md#publishing-and-unpublishing-a-tree) om de knooppunten in de opslagplaats te activeren die de configuraties van de Microsoft Translator of de cloudservice van derden opslaan. De knooppunten bevinden zich onder de volgende bovenliggende knooppunten:

* Microsoft-vertaalservice: /libs/settings/cloudconfigs/vertaling/msft-vertaling
* Vertaling door derden: /etc/cloudservices/machine-vertaling
