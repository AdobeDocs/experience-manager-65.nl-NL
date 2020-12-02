---
title: Modellen van contentfragmenten
seo-title: Modellen van contentfragmenten
description: Inhoudsfragmentmodellen worden gebruikt om inhoudsfragmenten met gestructureerde inhoud te maken.
seo-description: Inhoudsfragmentmodellen worden gebruikt om inhoudsfragmenten met gestructureerde inhoud te maken.
uuid: 73e38629-37c6-4f68-97a9-62f9783cc3d4
content-type: reference
topic-tags: content-fragments
products: SG_EXPERIENCEMANAGER/6.5/ASSETS
discoiquuid: 9da10294-2dc8-4e82-8d32-f034e6a5aeeb
docset: aem65
translation-type: tm+mt
source-git-commit: ce64b148ba96cc64670aaf96c1b201bafa282b98
workflow-type: tm+mt
source-wordcount: '745'
ht-degree: 20%

---


# Modellen van contentfragmenten{#content-fragment-models}

Met Inhoudsfragmentmodellen wordt de inhoudsstructuur gedefinieerd voor uw [inhoudsfragmenten](/help/assets/content-fragments/content-fragments.md).

## Modellen van inhoudsfragmenten {#enable-content-fragment-models} inschakelen

>[!CAUTION]
>
>Als u **Content Fragment Models** niet inschakelt, is de optie **Create** niet beschikbaar voor het maken van nieuwe modellen.

Als u modellen van inhoudsfragmenten wilt inschakelen, moet u:

* Het gebruik van modellen van inhoudsfragmenten inschakelen in de [Configuration Browser](/help/sites-administering/configurations.md)
* De configuratie toepassen op de map Middelen

### Modellen van inhoudsfragmenten inschakelen in Configuratiebeheer {#enable-content-fragment-models-in-configuration-manager}

Om [een nieuw Model van het Fragment van de Inhoud te creëren ](#creating-a-content-fragment-model) u **moet** eerst hen toelaten gebruikend de Manager van de Configuratie:

1. Ga naar **Tools**, **Algemeen** en open vervolgens de **Browserconfiguratie**.
1. Selecteer de locatie die geschikt is voor uw website.
1. Gebruik **Maken** om het dialoogvenster te openen, waarin u:

   1. Geef een **Titel** op.
   1. Selecteer **Modellen van inhoudsfragmenten** om het gebruik ervan in te schakelen.

   ![cfm-6420-09](assets/cfm-6420-09.png)

1. Selecteer **Maken** om de definitie op te slaan.

### Pas de Configuratie op uw Omslag van Activa {#apply-the-configuration-to-your-assets-folder} toe

Wanneer de configuratie **global** is ingeschakeld voor modellen van inhoudsfragmenten, kunnen modellen die gebruikers maken, worden gebruikt in elke map Middelen.

Als u andere configuraties (dat wil zeggen exclusief globaal) wilt gebruiken met een vergelijkbare map met assets, moet u de verbinding definiëren. U doet dit met behulp van **Configuratie** op het tabblad **Cloud Services** van de **Mapeigenschappen** van de juiste map.

## Een inhoudsfragmentmodel maken {#creating-a-content-fragment-model}

1. Navigeer naar **Tools**, **Assets** en open **Content Fragment Models**.
1. Navigeer naar de map die geschikt is voor uw [configuratie](#enable-content-fragment-models).
1. Gebruik **Create** om de wizard te openen.

   >[!CAUTION]
   >
   >Als het [gebruik van inhoudsfragmentmodellen niet is ingeschakeld](#enable-content-fragment-models), is de optie **Maken** niet beschikbaar.

1. Geef de **modeltitel** op. U kunt desgewenst ook een **beschrijving** toevoegen.

   ![cfm-6420-10](assets/cfm-6420-10.png)

1. Gebruik **Maken** om het lege model op te slaan. Een bericht zal op het succes van de actie wijzen, kunt u **Open** selecteren om het model onmiddellijk uit te geven, of **Done** om aan de console terug te keren.

## Het inhoudsfragmentmodel {#defining-your-content-fragment-model} definiëren

Het inhoudsfragmentmodel definieert in feite de structuur van de resulterende inhoudsfragmenten. Gebruikend de modelredacteur kunt u, de vereiste gebieden toevoegen en vormen:

>[!CAUTION]
>
>Het bewerken van een bestaand inhoudsfragmentmodel kan invloed hebben op afhankelijke fragmenten.

1. Navigeer naar **Tools**, **Assets** en open **Content Fragment Models**.

1. Navigeer naar de map met het fragmentmodel van de inhoud.
1. Open het vereiste model voor **Edit**; gebruik de snelle actie of selecteer het model en de actie op de werkbalk.

   Zodra open de modelredacteur toont:

   * links: velden al gedefinieerd
   * rechts: **datatypen** voor het maken van velden (en **eigenschappen** voor gebruik als er velden zijn gemaakt)

   >[!NOTE]
   >
   >Als een veld **Vereist** is, wordt het **label** in het linkerdeelvenster gemarkeerd met een sterretje (*****).

   ![cfm-6420-12](assets/cfm-6420-12.png)

1. **Een veld toevoegen**

   * Sleep een vereist gegevenstype naar de vereiste locatie voor een veld:

   ![cfm-6420-11](assets/cfm-6420-11.png)

   * Nadat een veld aan het model is toegevoegd, wordt in het rechterdeelvenster **Eigenschappen** weergegeven die voor dat specifieke gegevenstype kunnen worden gedefinieerd. Hier kunt u definiëren wat voor dat veld is vereist. Bijvoorbeeld:

   ![cfm-6420-13](assets/cfm-6420-13.png)

   >[!NOTE]
   Voor het datatype **Tekst met meerdere regels** is het mogelijk het **standaardtype** als volgt te definiëren:
   * **RTF**

   * **Markering**

   * **Onbewerkte tekst**

   Indien niet opgegeven, wordt de standaardwaarde **RTF-tekst** gebruikt voor dit veld.
   Het wijzigen van het **standaardtype** in een contentfragmentmodel heeft alleen effect op een bestaand, gerelateerd contentfragment nadat dat fragment is geopend in de editor en opgeslagen.

1. **Een veld verwijderen**

   Selecteer het gewenste veld en klik op het pictogram van de prullenbak of tik erop. U wordt gevraagd de actie te bevestigen.

   ![cf-32](assets/cf-32.png)

1. Nadat u alle vereiste velden hebt toegevoegd en de eigenschappen hebt gedefinieerd, gebruikt u **Opslaan** om de definitie te behouden. Bijvoorbeeld:

   ![cfm-6420-14](assets/cfm-6420-14.png)

## Een inhoudsfragmentmodel {#deleting-a-content-fragment-model} verwijderen

>[!CAUTION]
Het verwijderen van een inhoudsfragmentmodel kan invloed hebben op afhankelijke fragmenten.

Een inhoudsfragmentmodel verwijderen:

1. Navigeer naar **Tools**, **Assets** en open **Content Fragment Models**.

1. Navigeer naar de map met het fragmentmodel van de inhoud.
1. Selecteer het model, gevolgd door **Delete** op de werkbalk.

   >[!NOTE]
   Als naar het model wordt verwezen, wordt een waarschuwing gegeven. Voer de juiste actie uit.

## Een inhoudsfragmentmodel {#publishing-a-content-fragment-model} publiceren

Inhoudsfragmentmodellen moeten worden gepubliceerd wanneer/voordat afhankelijke inhoudsfragmenten worden gepubliceerd.

Een fragmentmodel voor inhoud publiceren:

1. Navigeer naar **Tools**, **Assets** en open **Content Fragment Models**.

1. Navigeer naar de map met het fragmentmodel van de inhoud.
1. Selecteer het model, gevolgd door **Publiceren** op de werkbalk.

   >[!NOTE]
   Als u een inhoudsfragment publiceert waarvoor het model nog niet is gepubliceerd, wordt dit in een selectielijst aangegeven en wordt het model met het fragment gepubliceerd.

