---
title: Verbinding maken met Microsoft Translator
description: Leer hoe u AEM kunt verbinden met Microsoft Translator vanuit de verpakking om uw vertaalworkflow te automatiseren.
feature: Language Copy
role: Admin
exl-id: ca575a30-fc3e-4f38-9aa7-dbecbc089f87
solution: Experience Manager, Experience Manager Sites
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '452'
ht-degree: 0%

---

# Verbinding maken met Microsoft Translator {#connecting-to-microsoft-translator}

Creeer een configuratie voor de ](https://www.microsoft.com/en-us/translator/business/) de wolkendienst van de Vertaler van Microsoft 0} {om uw rekening van de Vertaling van Microsoft voor het vertalen van AEM pagina inhoud of activa te gebruiken.[

>[!NOTE]
>
>AEM levert een proefaccount voor Microsoft-vertaling, waarbij maximaal 2 000 000 gratis vertaalde tekens per maand zijn toegestaan. Om een rekeningsabonnement te verkrijgen dat voor productiesystemen adequaat is, zie [ Bevorderend de Configuratie van de Vergunning van de Vergunning van de Vertaling van Microsoft Vertaler ](#upgrading-the-microsoft-translator-trial-license-configuration).

| Eigenschap | Beschrijving |
|---|---|
| Vertaallabel | De weergavenaam voor de vertaalservice |
| Vertaalkenmerk | (Optioneel) Voor door de gebruiker gegenereerde inhoud wordt de toewijzing naast vertaalde tekst weergegeven, bijvoorbeeld `Translations by Microsoft` |
| Workspace-id | (Optioneel) De id van de aangepaste Microsoft Translator-engine die u wilt gebruiken |
| Subscription Key | Je Microsoft Subscription Key voor Microsoft Translator |

Nadat u de configuratie creeert, moet u het [ activeren ](#activating-the-translator-service-configurations).

De volgende procedure leidt tot een configuratie van de Vertaler van Microsoft.

1. In het [ navigatievenster, ](/help/sites-authoring/basic-handling.md#first-steps) klik **Hulpmiddelen** > **Cloud Servicen** > **Cloud Servicen van de Vertaling**.
1. Navigeer naar de locatie waar u de configuratie wilt maken. Normaal gesproken bevindt dit zich in de hoofdmap van de site of kan het een algemene standaardconfiguratie zijn.
1. Klik **creeer** knoop.
1. Definieer uw configuratie.
   1. Selecteer **Vertaler van Microsoft** in drop-down.
   1. Typ een titel voor de configuratie. De titel identificeert de configuratie in de console van Cloud Servicen en in de drop-down lijsten van het paginabezit.
   1. Typ desgewenst een naam die u wilt gebruiken voor het knooppunt in de opslagplaats dat de configuratie opslaat.

   ![ creeer vertaalconfiguratie ](assets/create-translation-config.png)

1. Klik **creëren**.
1. In **geef het venster van de Configuratie** uit, verstrek de waarden voor de vertaaldienst die in de vorige lijst wordt beschreven.

   ![ geef vertaalconfiguratie ](assets/edit-translation-config.png) uit

1. Klik **verbinden** om de verbinding te verifiëren.
1. Klik **sparen &amp; Sluiten**.

## De Microsoft Translator-licentieconfiguratie voor proefversies bijwerken {#upgrading-the-microsoft-translator-trial-license-configuration}

Microsoft-vertaalconfiguratiepagina&#39;s bieden een handige koppeling naar de Microsoft-website voor het verkrijgen van een accountabonnement dat geschikt is voor productiesystemen.

1. In het [ navigatievenster, ](/help/sites-authoring/basic-handling.md#first-steps) klik **Hulpmiddelen** > **Cloud Servicen** > **Cloud Servicen van de Vertaling**.
1. Klik op de bestaande Microsoft Translator-configuratie.
1. Klik **uitgeven**.
1. In **geef het venster van de Configuratie** uit, klik **Abonnement van de Verbetering**. Er wordt een Microsoft-webpagina met meer informatie over de service geopend.

## De Microsoft Translator Engine aanpassen {#customizing-your-microsoft-translator-engine}

Microsoft Translation Configuration-pagina&#39;s bieden een handige koppeling naar de Microsoft-website om uw Microsoft Translator-engine aan te passen.

1. In het [ navigatievenster, ](/help/sites-authoring/basic-handling.md#first-steps) klik **Hulpmiddelen** > **Cloud Servicen** > **Cloud Servicen van de Vertaling**.
1. Klik op de bestaande Microsoft Translator-configuratie.
1. Klik **uitgeven**.
1. In **geef het venster van de Configuratie** uit, klik **pas Vertaler** aan. Gebruik de Microsoft-webpagina die wordt geopend om uw service aan te passen.

## De configuraties van de vertaalservice activeren {#activating-the-translator-service-configurations}

U moet uw configuraties van de wolkendienst activeren om vertaalde inhoud te steunen die aan de publicatie instantie wordt herhaald. Gebruik de methode van [ het publiceren van een boom ](/help/sites-authoring/publishing-pages.md#publishing-and-unpublishing-a-tree) om de gegevensopslagknopen te activeren die de configuraties van de Vertaler van Microsoft opslaan. De knooppunten bevinden zich onder de volgende bovenliggende knooppunten:

* `/libs/settings/cloudconfigs/translation/msft-translation`
