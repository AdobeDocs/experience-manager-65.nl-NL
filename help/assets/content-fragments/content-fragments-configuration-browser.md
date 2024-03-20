---
title: Inhoudsfragmenten - Configuratiebrowser
description: Leer hoe u bepaalde functionaliteit voor inhoudsfragmenten in de configuratiegrowser kunt inschakelen voor het gebruik van Adobe Experience Manager-functies voor krachtige koploze levering.
feature: Content Fragments
role: User
exl-id: a9990b0c-56c7-4e61-bae9-98e19a7f364e
solution: Experience Manager, Experience Manager Assets
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '272'
ht-degree: 12%

---

# Inhoudsfragmenten - Configuratiebrowser{#content-fragments-configuration-browser}

Leer hoe u bepaalde functionaliteit voor inhoudsfragmenten in de configuratiegrowser kunt inschakelen voor het gebruik van de krachtige functies voor koploze weergave van Adobe Experience Manager (AEM).

## Functionaliteit van inhoudsfragment inschakelen voor uw instantie {#enable-content-fragment-functionality-instance}

Gebruik voordat u Inhoudsfragmenten gebruikt de opdracht **Configuratiebrowser** om het volgende in te schakelen:

* **Modellen van inhoudsfragmenten** - verplicht
* **Blijvende GraphQL-query&#39;s** - facultatief

>[!CAUTION]
>
>Als u niet inschakelt **Modellen van inhoudsfragmenten**:
>
>* de **Maken** is niet beschikbaar voor het maken van modellen.
>* u kunt [Selecteer de configuratie van Plaatsen om het verwante eindpunt tot stand te brengen](/help/sites-developing/headless/graphql-api/graphql-endpoint.md#enabling-graphql-endpoint).

U moet het volgende doen om de functionaliteit van inhoudsfragmenten in te schakelen:

* Het gebruik van de functionaliteit voor inhoudsfragmenten inschakelen via de configuratiebrowser
* De configuratie toepassen op de map Middelen

### Functionaliteit van inhoudsfragment inschakelen in configuratievenster {#enable-content-fragment-functionality-in-configuration-browser}

Naar [bepaalde functionaliteit van inhoudsfragmenten gebruiken](#creating-a-content-fragment-model), u **moet** eerst de **Configuratiebrowser**:

>[!NOTE]
>
>Zie voor meer informatie [Configuratiebrowser:](/help/sites-administering/configurations.md#using-configuration-browser).

1. Ga naar **Tools**, **Algemeen** en open vervolgens de **Browserconfiguratie**.

1. Gebruiken **Maken** om het dialoogvenster te openen, waarin u:

   1. Geef een **Titel**.
   1. Om hun gebruik toe te laten selecteer
      * **Modellen van contentfragmenten**
      * **Blijvende GraphQL-query&#39;s**

      ![Configuratie definiëren](assets/cfm-conf-01.png)

1. Selecteren **Maken** om de definitie op te slaan.

<!-- 1. Select the location appropriate to your website. -->

### De configuratie toepassen op de middelenmap {#apply-the-configuration-to-your-assets-folder}

Wanneer de configuratie **globaal** is ingeschakeld voor de functionaliteit van inhoudsfragmenten en wordt vervolgens toegepast op elke map Middelen.

Als u andere configuraties (dus niet globaal) wilt gebruiken in een vergelijkbare map Elementen, moet u de verbinding definiëren. U doet dit door de juiste **Configuratie** te selecteren op het tabblad **Cloud Services** van de **Mapeigenschappen** van de juiste map.

![Configuratie toepassen](assets/cfm-conf-02.png)
