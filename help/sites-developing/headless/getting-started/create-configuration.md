---
title: Creërend een Hoofdloze Gids van het Begin van de Configuratie
description: Creeer een configuratie als eerste stap aan het worden begonnen met hoofdloze in AEM 6.5.
exl-id: f1df97a1-164f-4ed4-bb63-34caf35ae27c
solution: Experience Manager, Experience Manager Sites
feature: Headless,Content Fragments,GraphQL,Persisted Queries,Developing
role: Admin,Architect,Data Architect,Developer
source-git-commit: 9a3008553b8091b66c72e0b6c317573b235eee24
workflow-type: tm+mt
source-wordcount: '295'
ht-degree: 1%

---

# Creërend een Hoofdloze Gids van het Begin van de Configuratie {#creating-configuration}

Als eerste stap om met hoofdloos in AEM 6.5 te worden begonnen, moet u een configuratie tot stand brengen.

## Wat is een Configuratie? {#what-is-a-configuration}

Browser van de Configuratie verstrekt een generische configuratie API, inhoudsstructuur, resolutiemechanisme voor configuraties in AEM.

In de context van het beheer van inhoud zonder kop in AEM, denk aan een configuratie als werkplaats binnen AEM waar u uw Modellen van de Inhoud kunt tot stand brengen, die de structuur van uw toekomstige inhoud en de Fragmenten van de Inhoud bepalen. U kunt veelvoudige configuraties hebben om deze modellen te scheiden.

>[!NOTE]
>
>Als u met [&#x200B; paginasjablonen in een volledig-stapel AEM implementatie vertrouwd bent, &#x200B;](/help/sites-authoring/templates.md) is het gebruik van configuraties voor het beheer van Content Models gelijkaardig.

## Hoe te om een Configuratie te creëren {#how-to-create-a-configuration}

Een beheerder zou slechts één keer een configuratie moeten tot stand brengen, of zeer seldomly wanneer een nieuwe werkruimte voor het organiseren van uw Modellen van de Inhoud wordt vereist. Voor deze gids aan de slag, moeten wij slechts één configuratie tot stand brengen.

1. Logboek in AEM en van het belangrijkste menu selecteert **Hulpmiddelen > Algemeen > Browser van de Configuratie**.
1. Verstrek a **Titel** voor uw configuratie.
   * Er wordt automatisch een naam gegenereerd op basis van de titel en deze wordt aangepast volgens de naamgevingsconventies van [AEM .](/help/sites-developing/naming-conventions.md). Het wordt de knooppuntnaam in de repository.
1. Controleer de volgende opties:
   * **Modellen van contentfragmenten**
   * **de Blijvende Vragen van GraphQL**

   ![&#x200B; creeer Configuratie &#x200B;](assets/create-configuration.png)

1. Klik **creëren**

U kunt indien nodig meerdere configuraties maken. Configuraties kunnen ook worden genest.

>[!NOTE]
>
>De opties van de configuratie naast **Modellen van het Fragment van de Inhoud** en **de Blijvende Vragen van GraphQL** kunnen afhankelijk van uw implementatievereisten noodzakelijk zijn.

## Volgende stappen {#next-steps}

Gebruikend deze configuratie, kunt u zich nu op het tweede deel van begonnen gids bewegen en [&#x200B; creeer de Modellen van het Fragment van de Inhoud.](create-content-model.md)

<!--
>[!TIP]
>
>For complete details about the Configuration Browser, [see the Configuration Browser documentation.](/help/sites-developing/configurations.md)
-->
