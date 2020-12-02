---
title: Verwante activa
description: Leer hoe u digitale elementen die gemeenschappelijke kenmerken delen, koppelt. Maak ook bronafhankelijke relaties tussen digitale elementen.
contentOwner: AG
translation-type: tm+mt
source-git-commit: f9f745369ba0fe242dea1e5a5e5af0b8263b1ec0
workflow-type: tm+mt
source-wordcount: '607'
ht-degree: 0%

---


# Verwante activa {#related-assets}

[!DNL Adobe Experience Manager Assets] Hiermee kunt u elementen handmatig koppelen op basis van de behoeften van uw organisatie met behulp van de functie voor gerelateerde elementen. U kunt bijvoorbeeld een licentiebestand koppelen aan een element of aan een afbeelding/video over een vergelijkbaar onderwerp. U kunt elementen die bepaalde algemene kenmerken delen, aan elkaar koppelen. U kunt de eigenschap ook gebruiken om bron/afgeleide verhoudingen tussen activa tot stand te brengen. Als u bijvoorbeeld een PDF-bestand hebt dat is gegenereerd vanuit een INDD-bestand, kunt u het PDF-bestand koppelen aan het INDD-bronbestand.

Met deze functie hebt u de flexibiliteit om een PDF- of JPG-bestand met lage resolutie te delen met leveranciers of agentschappen en het INDD-bestand met hoge resolutie alleen op verzoek beschikbaar te maken.

>[!NOTE]
>
>Alleen gebruikers met bewerkingsmachtigingen voor elementen kunnen de elementen releren en de relatie tussen de elementen verbreken.

## Elementen {#relating-assets} koppelen

1. Open vanuit de interface [!DNL Experience Manager] de pagina **[!UICONTROL Properties]** voor een element dat u wilt koppelen.

   ![de eigenschappenpagina van een element openen om het element te koppelen](assets/asset-properties-relate-assets.png)

   *Afbeelding:  [!DNL Assets] [!UICONTROL Properties] pagina voor het koppelen van elementen.*

   U kunt ook het element selecteren in de lijstweergave.

   ![chlimage_1-273](assets/chlimage_1-273.png)

   U kunt het element ook selecteren in een verzameling.

   ![chlimage_1-274](assets/chlimage_1-274.png)

1. Als u een ander element wilt koppelen aan het element dat u hebt geselecteerd, klikt u op **[!UICONTROL Relate]** ![Relatieve elementen](assets/do-not-localize/link-relate.png) op de werkbalk.
1. Voer een van de volgende handelingen uit:

   * Als u het bronbestand voor het element wilt koppelen, selecteert u **[!UICONTROL Source]** in de lijst.
   * Als u een afgeleid bestand wilt koppelen, selecteert u **[!UICONTROL Derived]** in de lijst.
   * Selecteer **[!UICONTROL Others]** in de lijst om een relatie in twee richtingen tussen de elementen te maken.

1. Navigeer in het scherm **[!UICONTROL Select Asset]** naar de locatie van het element dat u wilt koppelen en selecteer het.

   ![chlimage_1-277](assets/chlimage_1-277.png)

1. Klik op **[!UICONTROL Confirm]**.
1. Klik **[!UICONTROL OK]** om het dialoogvenster te sluiten. Afhankelijk van uw keuze voor relatie in stap 3, wordt het gerelateerde element vermeld onder een geschikte categorie in de sectie **[!UICONTROL Related]**. Als het element dat u hebt verwant bijvoorbeeld het bronbestand voor het huidige element is, wordt het weergegeven onder **[!UICONTROL Source]**.

   ![chlimage_1-278](assets/chlimage_1-278.png)

1. Als u de koppeling met een element wilt opheffen, klikt u op **[!UICONTROL Unrelate]** ![ongerelateerde elementen](assets/do-not-localize/link-unrelate-icon.png) op de werkbalk.

1. Selecteer de elementen die u niet wilt koppelen in het dialoogvenster **[!UICONTROL Remove Relations]** en klik op **[!UICONTROL Unrelate]**.

   ![chlimage_1-280](assets/chlimage_1-280.png)

1. Klik **[!UICONTROL OK]** om het dialoogvenster te sluiten. De elementen waarvoor u relaties hebt verwijderd, worden verwijderd uit de lijst met verwante elementen onder de sectie **[!UICONTROL Related]**.

## Verwante elementen vertalen {#translating-related-assets}

Het maken van bron-/afgeleide relaties tussen elementen met behulp van de functie voor gerelateerde elementen is ook handig in vertaalworkflows. Wanneer u een vertaalwerkstroom op een afgeleid middel in werking stelt, [!DNL Experience Manager Assets] haalt automatisch om het even welk middel dat de brondossierverwijzingen en omvat het voor vertaling. Op deze manier wordt het element waarnaar door het bronelement wordt verwezen, samen met de bron en afgeleide elementen omgezet. Neem bijvoorbeeld een scenario waarin uw Engelse taalkopie een afgeleid element en het bronbestand van dat element bevat, zoals wordt weergegeven.

![chlimage_1-281](assets/chlimage_1-281.png)

Als het bronbestand verwant is aan een ander element, haalt [!DNL Experience Manager Assets] het element waarnaar wordt verwezen op en neemt dit voor vertaling op.

![De pagina met eigenschappen van elementen bevat het bronbestand van het verwante element dat moet worden opgenomen voor vertaling](assets/asset-properties-source-asset.png)

*Afbeelding: Bronactiva van de gerelateerde activa die voor vertaling moeten worden opgenomen.*

1. Vertaal de elementen in de bronmap naar een doeltaal door de stappen in [Een nieuw vertaalproject maken](translation-projects.md#create-a-new-translation-project) te volgen. In dit geval vertaalt u uw middelen bijvoorbeeld naar het Frans.

1. Open op de pagina [!UICONTROL Projects] de vertaalmap.

1. Klik op de projecttegel om de detailpagina te openen.

   ![chlimage_1-284](assets/chlimage_1-284.png)

1. Klik op de ovalen onder de Vertaal-taakkaart om de vertaalstatus weer te geven.

   ![chlimage_1-285](assets/chlimage_1-285.png)

1. Selecteer het element en klik vervolgens op **[!UICONTROL Reveal in Assets]** op de werkbalk om de vertaalstatus voor het element weer te geven.

   ![chlimage_1-286](assets/chlimage_1-286.png)

1. Klik op het bronelement om te controleren of de aan de bron gerelateerde elementen zijn omgezet.

1. Selecteer het element dat betrekking heeft op de bron en klik op **[!UICONTROL Reveal in Assets]**. Het vertaalde gerelateerde element wordt weergegeven.
