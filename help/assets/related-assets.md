---
title: Verwante activa
description: Leer hoe u digitale elementen die gemeenschappelijke kenmerken delen, koppelt. Maak ook bronafhankelijke relaties tussen digitale elementen.
contentOwner: AG
role: User
feature: Collaboration,Asset Management
exl-id: ddb69727-74a0-4a4d-a14e-7d3bb5ceea2a
solution: Experience Manager, Experience Manager Assets
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '615'
ht-degree: 0%

---

# Verwante activa {#related-assets}

Met [!DNL Adobe Experience Manager Assets] kunt u elementen handmatig koppelen op basis van de behoeften van uw organisatie met behulp van de functie voor verwante elementen. U kunt bijvoorbeeld een licentiebestand koppelen aan een element of aan een afbeelding/video over een vergelijkbaar onderwerp. U kunt elementen die bepaalde algemene kenmerken delen, aan elkaar koppelen. U kunt de eigenschap ook gebruiken om bron/afgeleide verhoudingen tussen activa tot stand te brengen. Als u bijvoorbeeld een PDF-bestand hebt dat is gegenereerd vanuit een INDD-bestand, kunt u het PDF-bestand koppelen aan het INDD-bronbestand.

Met deze functie kunt u een PDF-bestand met een lage resolutie of JPG-bestand delen met leveranciers of agentschappen en het INDD-bestand met een hoge resolutie alleen op verzoek beschikbaar maken.

>[!NOTE]
>
>Alleen gebruikers met bewerkingsmachtigingen voor elementen kunnen de elementen releren en de relatie tussen de elementen verbreken.

## Relatieve elementen {#relating-assets}

1. Open vanuit de interface [!DNL Experience Manager] de pagina **[!UICONTROL Properties]** voor een element dat u wilt koppelen.

   ![ open de pagina van de Eigenschappen van activa om de activa ](assets/asset-properties-relate-assets.png) met elkaar in verband te brengen

   *Cijfer: [!DNL Assets] [!UICONTROL Properties] pagina om activa met elkaar in verband te brengen.*

   U kunt ook het element selecteren in de lijstweergave.

   ![ chlimage_1-273 ](assets/chlimage_1-273.png)

   U kunt het element ook selecteren in een verzameling.

   ![ chlimage_1-274 ](assets/chlimage_1-274.png)

1. Om andere activa met de activa te relateren u selecteerde, klik **[!UICONTROL Relate]** ![ met elkaar verband houden activa ](assets/do-not-localize/link-relate.png) van de toolbar.
1. Voer een van de volgende handelingen uit:

   * Als u het bronbestand voor het element wilt koppelen, selecteert u **[!UICONTROL Source]** in de lijst.
   * Selecteer **[!UICONTROL Derived]** in de lijst als u een afgeleid bestand wilt koppelen.
   * Selecteer **[!UICONTROL Others]** in de lijst om een relatie in twee richtingen tussen de elementen te maken.

1. Navigeer in het **[!UICONTROL Select Asset]** -scherm naar de locatie van het element dat u wilt koppelen en selecteer het.

   ![ chlimage_1-277 ](assets/chlimage_1-277.png)

1. Klik op **[!UICONTROL Confirm]**.
1. Klik op **[!UICONTROL OK]** om het dialoogvenster te sluiten. Afhankelijk van uw keuze voor relatie in stap 3 wordt het gerelateerde element weergegeven onder een van de juiste categorieën in de sectie **[!UICONTROL Related]** . Als het element dat u hebt verwant bijvoorbeeld het bronbestand voor het huidige element is, wordt het weergegeven onder **[!UICONTROL Source]** .

   ![ chlimage_1-278 ](assets/chlimage_1-278.png)

1. Om een activa niet-met elkaar in verband te brengen, klik **[!UICONTROL Unrelate]** ![ losse activa ](assets/do-not-localize/link-unrelate-icon.png) van de toolbar.

1. Selecteer de elementen die u niet wilt koppelen in het dialoogvenster **[!UICONTROL Remove Relations]** en klik op **[!UICONTROL Unrelate]** .

   ![ chlimage_1-280 ](assets/chlimage_1-280.png)

1. Klik op **[!UICONTROL OK]** om het dialoogvenster te sluiten. De elementen waarvoor u relaties hebt verwijderd, worden verwijderd uit de lijst met verwante elementen onder de sectie **[!UICONTROL Related]** .

## Gerelateerde elementen vertalen {#translating-related-assets}

Het maken van bron-/afgeleide relaties tussen elementen met behulp van de functie voor gerelateerde elementen is ook handig in vertaalworkflows. Wanneer u een vertaalworkflow uitvoert op een afgeleid element, haalt [!DNL Experience Manager Assets] automatisch elk element op waarnaar het bronbestand verwijst en dat het voor vertaling bevat. Op deze manier wordt het element waarnaar door het bronelement wordt verwezen, samen met de bron en afgeleide elementen omgezet. Neem bijvoorbeeld een scenario waarin uw Engelse taalkopie een afgeleid element en het bronbestand van dat element bevat, zoals wordt weergegeven.

![ chlimage_1-281 ](assets/chlimage_1-281.png)

Als het bronbestand verwant is aan een ander element, haalt [!DNL Experience Manager Assets] het element waarnaar wordt verwezen op en wordt het opgenomen voor vertaling.

![ pagina van de Eigenschappen van activa toont brondossier van de verwante activa om voor vertaling ](assets/asset-properties-source-asset.png) te omvatten

*Cijfer: Source activa van de verwante activa om voor vertaling te omvatten.*

1. Vertaal de activa in de bronomslag aan een doeltaal door de stappen in [ te volgen creeer een vertaalproject ](translation-projects.md#create-a-new-translation-project). In dit geval vertaalt u uw middelen bijvoorbeeld naar het Frans.

1. Open vanaf de pagina [!UICONTROL Projects] de vertaalmap.

1. Klik op de projecttegel om de detailpagina te openen.

   ![ chlimage_1-284 ](assets/chlimage_1-284.png)

1. Klik op de ovalen onder de Vertaal-taakkaart om de vertaalstatus weer te geven.

   ![ chlimage_1-285 ](assets/chlimage_1-285.png)

1. Selecteer het element en klik vervolgens op **[!UICONTROL Reveal in Assets]** op de werkbalk om de vertaalstatus voor het element weer te geven.

   ![ chlimage_1-286 ](assets/chlimage_1-286.png)

1. Klik op het bronelement om te controleren of de aan de bron gerelateerde elementen zijn omgezet.

1. Selecteer het element dat betrekking heeft op de bron en klik op **[!UICONTROL Reveal in Assets]** . Het vertaalde gerelateerde element wordt weergegeven.
