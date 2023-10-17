---
title: Verbinding maken met Microsoft&reg; Vertaler
description: Leer hoe u Adobe Experience Manager verbindt met Microsoft&reg; Vertaler.
contentOwner: Guillaume Carlino
feature: Language Copy
exl-id: ca575a30-fc3e-4f38-9aa7-dbecbc089f87
source-git-commit: eaffc71c23c18d26ec5cbb2bbb7524790c4826fe
workflow-type: tm+mt
source-wordcount: '608'
ht-degree: 0%

---

# Verbinding maken met Microsoft® Translator{#connecting-to-microsoft-translator}

Maak een configuratie voor de Microsoft® Translator Cloud Service om uw Microsoft® Translation-account te gebruiken voor het vertalen van AEM pagina-inhoud, community-inhoud of middelen.

| Eigenschap | Beschrijving |
|---|---|
| Vertaallabel | De weergavenaam voor de vertaalservice. |
| Vertaalkenmerk | (Optioneel) Voor door de gebruiker gegenereerde inhoud wordt bijvoorbeeld de toewijzing naast vertaalde tekst weergegeven `Translations by Microsoft`. |
| Werkruimte-id | (Optioneel) De id van de aangepaste Microsoft® Translator-engine die u wilt gebruiken. |
| Subscription Key | Uw Microsoft® Subscription Key voor Microsoft® Translator. |

Nadat u de configuratie creeert, moet u [activeren](/help/sites-administering/tc-msconf.md#activating-the-translator-service-configurations).

In de volgende procedure wordt gebruikgemaakt van de geoptimaliseerde gebruikersinterface voor het maken van een Microsoft® Translator-configuratie.

1. Klik of tik op Gereedschappen > Cloud Servicen op de rails.
1. Selecteer Configuraties tonen in het gebied Microsoft® Translator.
1. Klik op de koppeling + naast Beschikbare configuraties.

   ![chlimage_1-382](assets/chlimage_1-382.png)

1. Typ een titel voor de configuratie. De titel identificeert de configuratie in de console van Cloud Servicen en in de drop-down lijsten van het paginabezit. De standaardnaam is gebaseerd op de titel. Typ desgewenst een naam die u wilt gebruiken voor het knooppunt in de opslagplaats dat de configuratie opslaat. Gebruik de standaardwaarde voor het bezit van de Configuratie van de Ouder dat de weg van de gegevensopslaggegevensopslagknoop is.
1. Klik op Maken.
1. Typ in het dialoogvenster dat wordt weergegeven waarden voor de eigenschappen en klik op OK.

## Voorbeeld van configuraties voor Microsoft® Translator Cloud Service {#sample-microsoft-translator-cloud-service-configurations}

De volgende Microsoft® Translator Cloud Service-configuraties worden geïnstalleerd met de Geometrixx voorbeelden. Sommige voorbeeldconfiguraties maken gebruik van een proefaccount voor Microsoft® Translation, waarmee maximaal 2 000 000 gratis vertaalde tekens per maand kunnen worden gebruikt.

### Proeflicentie voor Microsoft® Translator {#microsoft-translator-trial-license}

De Microsoft® Translator Trial-licentieconfiguratie is een voorbeeldconfiguratie die wordt geïnstalleerd met het voorbeeldpakket voor Geometrixx Outdoors. Deze configuratie gebruikt een Microsoft® Translator-account met een gratis abonnement waarmee 2 000 000 vertaalde tekens per maand kunnen worden gebruikt.

### Proeflicentie voor Microsoft® Translator - Geometrixx-outdoor {#microsoft-translator-trial-license-geometrixx-outdoors}

De Microsoft® Translator-proeflicentie - Geometrixx-outconfiguratie is een voorbeeldconfiguratie die met Geometrixx Outdoors is geïnstalleerd. Deze configuratie gebruikt dezelfde gratis Microsoft® Translator-account als de Microsoft® Translator-licentieconfiguratie voor proefversies. Het account heeft een gratis abonnement dat 2 000 000 vertaalde tekens per maand toestaat.

Deze Microsoft® Translator-configuratie is geoptimaliseerd voor gebruik met het type inhoud van de voorbeeldsite voor Geometrixx Outdoors.

### De Microsoft® Translator-configuratie voor proefversies van licenties bijwerken {#upgrading-the-microsoft-translator-trial-license-configuration}

Microsoft® Translation Configuration-pagina&#39;s bieden een handige koppeling naar de Microsoft®-website voor het verkrijgen van een accountabonnement dat geschikt is voor productiesystemen.

1. Klik of tik op Gereedschappen > Bewerkingen > Wolk > Cloud Servicen.
1. Klik of tik in het gedeelte Microsoft® Translator op Configuraties tonen en klik of tik op Microsoft® Translator Trial License (Microsoft® Translation Configuration).

   ![chlimage_1-383](assets/chlimage_1-383.png)

1. Voor de configuratiepagina, klik de Abonnement van de Verbetering. Gebruik de Microsoft®-webpagina die wordt geopend om uw account te configureren.

   ![chlimage_1-384](assets/chlimage_1-384.png)

### De Microsoft® Translator Engine aanpassen {#customizing-your-microsoft-translator-engine}

Microsoft® Translation configuratiepagina&#39;s bieden een handige koppeling naar de Microsoft® website om uw Microsoft® Translator-engine aan te passen. ([https://www.microsoft.com/en-us/research/project/microsoft-translator-hub/](https://www.microsoft.com/en-us/research/project/microsoft-translator-hub/))

1. Klik of tik op Gereedschappen > Bewerkingen > Wolk > Cloud Servicen.
1. Klik of tik in het gedeelte Microsoft® Translator op Configuraties tonen en klik of tik vervolgens op de configuratie die u wilt aanpassen.
1. Klik op Vertaler aanpassen op de configuratiepagina. Gebruik de Microsoft®-webpagina die wordt geopend om uw service aan te passen.

## De configuraties van de vertaalservice activeren {#activating-the-translator-service-configurations}

Activeer uw cloudserviceconfiguraties om vertaalde inhoud te ondersteunen die naar de publicatie-instantie wordt gerepliceerd. Als u de knooppunten in de opslagplaats wilt activeren die de Microsoft® Translator of configuraties van cloudservices van derden opslaan, gebruikt u de methode van [een volledige sectie activeren (boomstructuur)](/help/sites-authoring/publishing-pages.md#publishing-and-unpublishing-a-tree). De knooppunten bevinden zich onder de volgende bovenliggende knooppunten:

* Microsoft® Translation Service: /libs/settings/cloudconfigs/translatie/msft-vertaling
* Vertaling door derden: /etc/cloudservices/machine-vertaling
