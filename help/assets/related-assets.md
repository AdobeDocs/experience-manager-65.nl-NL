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

[!DNL Adobe Experience Manager Assets] Hiermee kunt u elementen handmatig koppelen op basis van de behoeften van uw organisatie met behulp van de functie voor gerelateerde elementen. U kunt bijvoorbeeld een licentiebestand koppelen aan een element of aan een afbeelding/video over een vergelijkbaar onderwerp. U kunt elementen die bepaalde algemene kenmerken delen, aan elkaar koppelen. U kunt de eigenschap ook gebruiken om bron/afgeleide verhoudingen tussen activa tot stand te brengen. Als u bijvoorbeeld een PDF-bestand hebt dat is gegenereerd vanuit een INDD-bestand, kunt u het PDF-bestand koppelen aan het INDD-bronbestand.

Met deze functie kunt u een PDF- of JPG-bestand met een lage resolutie delen met leveranciers of instanties en het INDD-bestand met een hoge resolutie alleen op verzoek beschikbaar maken.

>[!NOTE]
>
>Alleen gebruikers met bewerkingsmachtigingen voor elementen kunnen de elementen releren en de relatie tussen de elementen verbreken.

## Relatieve elementen {#relating-assets}

1. Van de [!DNL Experience Manager] interface, open **[!UICONTROL Properties]** pagina voor een element dat u wilt koppelen.

   ![de eigenschappenpagina van een element openen om het element te koppelen](assets/asset-properties-relate-assets.png)

   *Afbeelding: [!DNL Assets] [!UICONTROL Properties] pagina voor het koppelen van elementen.*

   U kunt ook het element selecteren in de lijstweergave.

   ![chlimage_1-273](assets/chlimage_1-273.png)

   U kunt het element ook selecteren in een verzameling.

   ![chlimage_1-274](assets/chlimage_1-274.png)

1. Als u een ander element wilt koppelen aan het geselecteerde element, klikt u op **[!UICONTROL Relate]** ![gerelateerde activa](assets/do-not-localize/link-relate.png) op de werkbalk.
1. Voer een van de volgende handelingen uit:

   * Selecteer **[!UICONTROL Source]** in de lijst.
   * Als u een afgeleid bestand wilt koppelen, selecteert u **[!UICONTROL Derived]** in de lijst.
   * Als u een relatie in twee richtingen wilt maken tussen de elementen, selecteert u **[!UICONTROL Others]** in de lijst.

1. Van de **[!UICONTROL Select Asset]** , navigeert u naar de locatie van het element dat u wilt koppelen en selecteert u het.

   ![chlimage_1-277](assets/chlimage_1-277.png)

1. Klik op **[!UICONTROL Confirm]**.
1. Klikken **[!UICONTROL OK]** het dialoogvenster sluiten. Afhankelijk van uw keuze voor relatie in stap 3 wordt het gerelateerde actief vermeld onder een geschikte categorie in de categorie **[!UICONTROL Related]** sectie. Als het element dat u hebt verwant bijvoorbeeld het bronbestand voor het huidige element is, wordt het onder **[!UICONTROL Source]**.

   ![chlimage_1-278](assets/chlimage_1-278.png)

1. Als u een element niet wilt koppelen, klikt u op **[!UICONTROL Unrelate]** ![ongekoppelde elementen](assets/do-not-localize/link-unrelate-icon.png) op de werkbalk.

1. Selecteer de elementen die u niet wilt koppelen in het menu **[!UICONTROL Remove Relations]** en klikken **[!UICONTROL Unrelate]**.

   ![chlimage_1-280](assets/chlimage_1-280.png)

1. Klikken **[!UICONTROL OK]** het dialoogvenster sluiten. De activa waarvoor u betrekkingen schrapte worden geschrapt van de lijst van verwante activa onder **[!UICONTROL Related]** sectie.

## Gerelateerde elementen vertalen {#translating-related-assets}

Het maken van bron-/afgeleide relaties tussen elementen met behulp van de functie voor gerelateerde elementen is ook handig in vertaalworkflows. Wanneer u een vertaalworkflow uitvoert op een afgeleid middel, [!DNL Experience Manager Assets] haalt automatisch om het even welk middel op dat het brondossier verwijzingen en omvat het voor vertaling. Op deze manier wordt het element waarnaar door het bronelement wordt verwezen, samen met de bron en afgeleide elementen omgezet. Neem bijvoorbeeld een scenario waarin uw Engelse taalkopie een afgeleid element en het bronbestand van dat element bevat, zoals wordt weergegeven.

![chlimage_1-281](assets/chlimage_1-281.png)

Als het bronbestand verwant is aan een ander element, [!DNL Experience Manager Assets] Hiermee wordt het element waarnaar wordt verwezen opgehaald en opgenomen voor vertaling.

![De pagina met eigenschappen van elementen bevat het bronbestand van het verwante element dat moet worden opgenomen voor vertaling](assets/asset-properties-source-asset.png)

*Afbeelding: Bronelement van de gerelateerde elementen die moeten worden opgenomen voor vertaling.*

1. Vertaal de elementen in de bronmap naar een doeltaal door de stappen in [Een vertaalproject maken](translation-projects.md#create-a-new-translation-project). In dit geval vertaalt u uw middelen bijvoorbeeld naar het Frans.

1. Van de [!UICONTROL Projects] pagina, opent u de vertaalmap.

1. Klik op de projecttegel om de detailpagina te openen.

   ![chlimage_1-284](assets/chlimage_1-284.png)

1. Klik op de ovalen onder de Vertaal-taakkaart om de vertaalstatus weer te geven.

   ![chlimage_1-285](assets/chlimage_1-285.png)

1. Selecteer het element en klik op **[!UICONTROL Reveal in Assets]** op de werkbalk om de vertaalstatus voor het element weer te geven.

   ![chlimage_1-286](assets/chlimage_1-286.png)

1. Klik op het bronelement om te controleren of de aan de bron gerelateerde elementen zijn omgezet.

1. Selecteer het element dat verwant is aan de bron en klik op **[!UICONTROL Reveal in Assets]**. Het vertaalde gerelateerde element wordt weergegeven.
