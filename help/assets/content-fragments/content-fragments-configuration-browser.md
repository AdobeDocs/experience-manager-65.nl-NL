---
title: Inhoudsfragmenten - Configuratiebrowser
description: Leer hoe te om bepaalde functionaliteit van het Fragment van de Inhoud in Browser van de Configuratie toe te laten om AEM krachtige koploze leveringseigenschappen te gebruiken.
feature: Content Fragments
role: User
source-git-commit: 94145c6428f61e31f6784a3d6ea67aa8d81cedd6
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# Inhoudsfragmenten - Configuratiebrowser{#content-fragments-configuration-browser}

Leer hoe te om bepaalde functionaliteit van het Fragment van de Inhoud in Browser van de Configuratie toe te laten om AEM krachtige koploze leveringseigenschappen te gebruiken.

## Functionaliteit van inhoudsfragment inschakelen voor uw instantie {#enable-content-fragment-functionality-instance}

Alvorens Inhoudsfragmenten te gebruiken moet u **Browser van de Configuratie** gebruiken om toe te laten:

* **Modellen**  voor inhoudsfragmenten - verplicht
* **GrafiekQL Blijvende query** &#39;s - optioneel

>[!CAUTION]
>
>Als u **Inhoudsfragmentmodellen** niet inschakelt:
>
>* De optie **Maken** is niet beschikbaar voor het maken van nieuwe modellen.
>* u zult niet de configuratie van Plaatsen kunnen [selecteren om het verwante eind-punt](/help/assets/content-fragments/graphql-api-content-fragments.md#enabling-graphql-endpoint) tot stand te brengen.


Voor het inschakelen van de functionaliteit voor inhoudsfragmenten moet u:

* Het gebruik van de functionaliteit voor inhoudsfragmenten inschakelen via de configuratiesbrowser
* De configuratie toepassen op de map Middelen

### Functionaliteit van inhoudsfragment inschakelen in configuratievenster {#enable-content-fragment-functionality-in-configuration-browser}

Als u [bepaalde functionaliteit voor inhoudsfragmenten wilt gebruiken](#creating-a-content-fragment-model), moet u **must** eerst inschakelen via de **Configuratiebrowser**:

>[!NOTE]
>
>Zie ook [Configuration Browser:](/help/sites-administering/configurations.md#using-configuration-browser) voor meer informatie.

>[!CAUTION]
>
>Subconfiguraties (een configuratie die in een configuratie is genest) worden niet ondersteund voor gebruik met Content Fragments.

1. Ga naar **Tools**, **Algemeen** en open vervolgens de **Browserconfiguratie**.

1. Gebruik **Maken** om het dialoogvenster te openen, waarin u:

   1. Geef een **Titel** op.
   1. Selecteer
      * **Modellen van contentfragmenten**
      * **GrafiekQL blijvende vragen**

      ![Configuratie definiëren](assets/cfm-conf-01.png)


1. Selecteer **Maken** om de definitie op te slaan.

<!-- 1. Select the location appropriate to your website. -->

### De configuratie toepassen op de middelenmap {#apply-the-configuration-to-your-assets-folder}

Wanneer de configuratie **global** is ingeschakeld voor de functionaliteit van inhoudsfragmenten, wordt deze vervolgens toegepast op elke map Assets.

Als u andere configuraties (dat wil zeggen exclusief globaal) wilt gebruiken met een vergelijkbare map met assets, moet u de verbinding definiëren. U doet dit door de juiste **Configuratie** te selecteren op het tabblad **Cloud Services** van de **Mapeigenschappen** van de juiste map.

![Configuratie toepassen](assets/cfm-conf-02.png)
