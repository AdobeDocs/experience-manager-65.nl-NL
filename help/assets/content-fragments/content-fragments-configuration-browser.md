---
title: Inhoudsfragmenten - Configuratiebrowser
description: Leer hoe te om bepaalde functionaliteit van het Fragment van de Inhoud in Browser van de Configuratie toe te laten om AEM krachtige koploze leveringseigenschappen te gebruiken.
feature: Content Fragments
role: User
exl-id: a9990b0c-56c7-4e61-bae9-98e19a7f364e
source-git-commit: ad0f0bd8b0c230e002c734adca87da22bfa3a7cd
workflow-type: tm+mt
source-wordcount: '271'
ht-degree: 19%

---

# Inhoudsfragmenten - Configuratiebrowser{#content-fragments-configuration-browser}

Leer hoe te om bepaalde functionaliteit van het Fragment van de Inhoud in Browser van de Configuratie toe te laten om AEM krachtige koploze leveringseigenschappen te gebruiken.

## Functionaliteit van inhoudsfragment inschakelen voor uw instantie {#enable-content-fragment-functionality-instance}

Voordat u Inhoudsfragmenten kunt gebruiken, moet u de opdracht **Configuratiebrowser** inschakelen:

* **Modellen van inhoudsfragmenten** - verplicht
* **Blijvende GraphQL-query&#39;s** - facultatief

>[!CAUTION]
>
>Als u deze optie niet inschakelt **Modellen van inhoudsfragmenten**:
>
>* de **Maken** Deze optie is niet beschikbaar voor het maken van nieuwe modellen.
>* u kunt niet [Selecteer de configuratie van Plaatsen om het verwante eindpunt tot stand te brengen](/help/sites-developing/headless/graphql-api/graphql-endpoint.md#enabling-graphql-endpoint).


Voor het inschakelen van de functionaliteit voor inhoudsfragmenten moet u:

* Het gebruik van de functionaliteit voor inhoudsfragmenten inschakelen via de configuratiesbrowser
* De configuratie toepassen op de map Middelen

### Functionaliteit van inhoudsfragment inschakelen in configuratievenster {#enable-content-fragment-functionality-in-configuration-browser}

Naar [bepaalde functionaliteit van inhoudsfragmenten gebruiken](#creating-a-content-fragment-model) u **moet** ze eerst via de **Configuratiebrowser**:

>[!NOTE]
>
>Zie ook voor meer informatie [Configuratiebrowser:](/help/sites-administering/configurations.md#using-configuration-browser).

1. Ga naar **Tools**, **Algemeen** en open vervolgens de **Browserconfiguratie**.

1. Gebruiken **Maken** om het dialoogvenster te openen, waarin u:

   1. Geef een **Titel**.
   1. Selecteer
      * **Modellen van contentfragmenten**
      * **Blijvende GraphQL-query&#39;s**

      ![Configuratie definiëren](assets/cfm-conf-01.png)


1. Selecteren **Maken** om de definitie op te slaan.

<!-- 1. Select the location appropriate to your website. -->

### De configuratie toepassen op de middelenmap {#apply-the-configuration-to-your-assets-folder}

Wanneer de configuratie **globaal** is ingeschakeld voor de functionaliteit van inhoudsfragmenten en wordt vervolgens toegepast op elke map Middelen.

Als u andere configuraties (dat wil zeggen exclusief globaal) wilt gebruiken met een vergelijkbare map met assets, moet u de verbinding definiëren. U doet dit door de juiste **Configuratie** te selecteren op het tabblad **Cloud Services** van de **Mapeigenschappen** van de juiste map.

![Configuratie toepassen](assets/cfm-conf-02.png)
