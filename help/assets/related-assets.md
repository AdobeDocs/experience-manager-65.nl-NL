---
title: Verwante activa
description: Leer hoe u elementen koppelt die bepaalde algemene kenmerken delen. U kunt de eigenschap ook gebruiken om bron/afgeleide verhoudingen tussen activa tot stand te brengen.
contentOwner: AG
translation-type: tm+mt
source-git-commit: a39ee0f435dc43d2c2830b2947e91ffdcf11c7f6

---


# Verwante activa {#related-assets}

Met de Adobe Experience Manager-middelen (AEM) kunt u elementen handmatig koppelen op basis van de behoeften van uw organisatie met behulp van de functie voor verwante elementen. U kunt bijvoorbeeld een licentiebestand koppelen aan een element of aan een afbeelding/video over een vergelijkbaar onderwerp. U kunt elementen die bepaalde algemene kenmerken delen, aan elkaar koppelen. U kunt de eigenschap ook gebruiken om bron/afgeleide verhoudingen tussen activa tot stand te brengen. Als u bijvoorbeeld een PDF-bestand hebt dat is gegenereerd vanuit een INDD-bestand, kunt u het PDF-bestand koppelen aan het INDD-bronbestand.

Met deze functie hebt u de flexibiliteit om een PDF- of JPG-bestand met lage resolutie te delen met leveranciers of agentschappen en het INDD-bestand met hoge resolutie alleen op verzoek beschikbaar te maken.

## Relatieve elementen {#relating-assets}

1. Open vanuit de AEM-interface de pagina [!UICONTROL Eigenschappen] voor een element dat u wilt koppelen.

   ![chlimage_1-272](assets/chlimage_1-272.png)

   U kunt ook het element selecteren in de lijstweergave.

   ![chlimage_1-273](assets/chlimage_1-273.png)

   U kunt het element ook selecteren in een verzameling.

   ![chlimage_1-274](assets/chlimage_1-274.png)

1. Als u een ander element wilt koppelen aan het element dat u hebt geselecteerd, klikt of tikt u op het pictogram **[!UICONTROL Relate]** op de werkbalk.

   ![chlimage_1-275](assets/chlimage_1-275.png)

1. Voer een van de volgende handelingen uit:

   * Als u het bronbestand voor het element wilt koppelen, selecteert u **[!UICONTROL Bron]** in de lijst.
   * Als u een afgeleid bestand wilt koppelen, selecteert u **[!UICONTROL Afgeleid]** van de lijst.
   * Als u een relatie in twee richtingen wilt maken tussen de elementen, selecteert u **[!UICONTROL Overige]** in de lijst.
   ![chlimage_1-276](assets/chlimage_1-276.png)

1. Navigeer in het scherm **[!UICONTROL Element]** selecteren naar de locatie van het element dat u wilt koppelen en selecteer het.

   ![chlimage_1-277](assets/chlimage_1-277.png)

1. Klik op het pictogram **[!UICONTROL Bevestigen]** of tik erop.
1. Klik op **[!UICONTROL OK]** of tik erop om het dialoogvenster te sluiten. Afhankelijk van uw keuze voor relatie in stap 3 wordt het gerelateerde actief vermeld onder een geschikte categorie in de **[!UICONTROL verwante]** sectie. Als het element dat u hebt verwant bijvoorbeeld het bronbestand voor het huidige element is, wordt het weergegeven onder **[!UICONTROL Bron]**.

   ![chlimage_1-278](assets/chlimage_1-278.png)

1. Als u de koppeling met een element wilt opheffen, klikt u op de werkbalk op **[!UICONTROL Verwant]** maken.

   ![chlimage_1-279](assets/chlimage_1-279.png)

1. Selecteer de elementen die u niet wilt koppelen in het dialoogvenster Relaties **** verwijderen en klik op **[!UICONTROL Onafhankelijk]**.

   ![chlimage_1-280](assets/chlimage_1-280.png)

1. Klik op **[!UICONTROL OK]** of Tik op OK om het dialoogvenster te sluiten. De activa waarvoor u betrekkingen schrapte worden geschrapt van de lijst van verwante activa onder de **[!UICONTROL Verwante]** sectie.

## Verwante elementen vertalen {#translating-related-assets}

Het maken van bron-/afgeleide relaties tussen elementen met de functie Verwante elementen is ook handig in vertaalworkflows. Wanneer u een vertaalworkflow uitvoert op een afgeleid element, haalt AEM Assets automatisch alle elementen op waarnaar het bronbestand verwijst en die het bevat voor vertaling. Op deze manier wordt het element waarnaar door het bronelement wordt verwezen, samen met de bron en afgeleide elementen omgezet. Neem bijvoorbeeld een scenario waarin uw Engelse taalkopie een afgeleid element en het bronbestand van dat element bevat, zoals wordt weergegeven.

![chlimage_1-281](assets/chlimage_1-281.png)

Als het bronbestand is gerelateerd aan een ander element, haalt AEM Assets het element waarnaar wordt verwezen op en neemt het dit voor vertaling op.

![chlimage_1-282](assets/chlimage_1-282.png)

1. Vertaal de elementen in de bronmap naar een doeltaal door de stappen in [Een nieuw vertaalproject](translation-projects.md#create-a-new-translation-project)maken uit te voeren. In dit geval vertaalt u uw middelen bijvoorbeeld naar het Frans.
1. Open vanuit de pagina [!UICONTROL Projecten] de vertaalmap.

   ![chlimage_1-283](assets/chlimage_1-283.png)

1. Klik/Tik de projecttegel om de detailspagina te openen.

   ![chlimage_1-284](assets/chlimage_1-284.png)

1. Klik op of tik op de ovalen onder de Vertaaltaak-kaart om de status van de vertaling weer te geven.

   ![chlimage_1-285](assets/chlimage_1-285.png)

1. Selecteer het element en klik/tik op **[!UICONTROL Tonen in elementen]** op de werkbalk om de vertaalstatus voor het element weer te geven.

   ![chlimage_1-286](assets/chlimage_1-286.png)

1. Klik op het bronelement of tik erop om te controleren of de aan de bron gerelateerde elementen zijn omgezet.

   ![chlimage_1-287](assets/chlimage_1-287.png)

1. Selecteer het element dat betrekking heeft op de bron en klik op **[!UICONTROL Tonen in elementen]**. Het vertaalde gerelateerde element wordt weergegeven.

   ![chlimage_1-288](assets/chlimage_1-288.png)
