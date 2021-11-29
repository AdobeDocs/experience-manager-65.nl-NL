---
title: Creërend een Hoofdloze Gids van het Begin van de Configuratie
description: Creeer een configuratie als eerste stap aan het worden begonnen met hoofdloze in AEM 6.5.
exl-id: 48801599-f279-4e55-8033-9c418d2af5bb
source-git-commit: 8ab774b8d21dd16e4873cd39ef0175ead3f2da23
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
>Als u vertrouwd bent met [paginasjablonen in een volledige AEM-implementatie,](/help/sites-authoring/templates.md) het gebruik van configuraties voor het beheer van inhoudsmodellen is vergelijkbaar.

## Hoe te om een Configuratie te creëren {#how-to-create-a-configuration}

Een beheerder zou slechts één keer een configuratie moeten tot stand brengen, of zeer seldomly wanneer een nieuwe werkruimte voor het organiseren van uw Modellen van de Inhoud wordt vereist. Voor deze gids aan de slag, moeten wij slechts één configuratie tot stand brengen.

1. Meld u aan bij AEM en selecteer in het hoofdmenu **Gereedschappen -> Algemeen -> Configuratiebrowser**.
1. Een **Titel** voor uw configuratie.
   * Er wordt automatisch een naam gegenereerd op basis van de titel en aangepast op basis van [AEM naamconventies.](/help/sites-developing/naming-conventions.md). Het wordt de knooppuntnaam in de repository.
1. Controleer de volgende opties:
   * **Modellen van contentfragmenten**
   * **GrafiekQL blijvende vragen**

   ![Configuratie maken](../assets/create-configuration.png)

1. Tik of klik op **Maken**

Indien nodig kunt u meerdere configuraties maken. Configuraties kunnen ook worden genest.

>[!NOTE]
>
>Configuratieopties naast **Modellen van inhoudsfragmenten** en **GrafiekQL blijvende vragen** kan nodig zijn, afhankelijk van uw implementatievereisten.

## Volgende stappen {#next-steps}

Met deze configuratie kunt u nu naar het tweede deel van de gids Aan de slag gaan en [Maak Content Fragment Models.](create-content-model.md)

<!--
>[!TIP]
>
>For complete details about the Configuration Browser, [see the Configuration Browser documentation.](/help/sites-developing/configurations.md)
-->
