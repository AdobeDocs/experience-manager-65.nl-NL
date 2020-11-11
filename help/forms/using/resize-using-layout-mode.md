---
title: Gebruik de modus Indeling om het formaat van componenten voor adaptieve formulieren te wijzigen
description: 'De positie van componenten bepalen met behulp van het responsieve raster dat beschikbaar is in de modus Lay-out '
translation-type: tm+mt
source-git-commit: c62ad355469a95db89db44c34bb6df72d8f4bf77
workflow-type: tm+mt
source-wordcount: '1023'
ht-degree: 0%

---


# Gebruik de modus Lay-out om het formaat van componenten te wijzigen {#use-layout-mode-to-resize-components}

Met de adaptieve interface voor formulierontwerp kunt u de grootte van componenten aanpassen in de modus Indeling. Sleep blauwe stippen in kolommen om de begin- en eindpunten voor de positiecomponenten te definiëren. De blauwe stippen worden weergegeven nadat u op de component in het responsieve raster hebt getikt. Het responsieve raster bestaat uit 12 gelijke kolommen. Met de witte en blauwe kleurschaduw in alternatieve kolommen wordt de ene kolom onderscheiden van de andere.

Met de modus Lay-out kunt u het formaat van componenten wijzigen voor alle apparaattypen, zoals bureaublad, tablet, telefoon en andere kleinere apparaten. De tablet leidt automatisch de lay-outconfiguratie van de Desktopversie af en de kleinere apparaten leiden lay-outconfiguratie van telefoon af. Nochtans, kunt u de automatisch afgeleide configuraties met voeten treden om een verschillende configuratie voor elk apparatentype te bepalen.

## Modus Toegang tot layout {#access-layout-mode}

Selecteer **Indeling** in de vervolgkeuzelijst die boven aan de adaptieve ontwerpinterface naast de optie **Voorvertoning** wordt weergegeven. Het formulier wordt weergegeven in de modus Indeling.

1. Meld u aan bij de AEM auteur en navigeer naar **Adobe Experience Manager** > **Forms** > **Forms &amp; Documents**.
1. Create a new or open an existing [adaptive form](../../forms/using/creating-adaptive-form.md).
1. Selecteer **Lay-out** in de drop-down lijst die bij de bovenkant naast de optie van de **Voorproef** verschijnt. Het formulier wordt weergegeven in de modus Indeling.

   ![Lay-outmodus](assets/layout_mode_ic_new.png)

## Formaat van componenten wijzigen {#resize-components}

1. Tik in de modus Lay-out op de component om de grootte te wijzigen. De blauwe stippen worden weergegeven aan het begin en einde van het responsieve raster.
1. Sleep de blauwe stippen om de positie van de component in het responsieve raster te definiëren.

   ![Vergroten/verkleinen met de modus Lay-out](assets/layout_mode_resize_new_updated.png)

   De werkbalk die wordt weergegeven nadat u op componenten hebt getikt, bestaat uit de volgende opties:

   * **Bovenliggend element:** Selecteer het bovenliggende element van een component.
   * **Zweven naar nieuwe regel:** Verplaats de component naar de volgende regel als er meerdere componenten binnen dezelfde regel zijn.

   U kunt alle wijzigingen in de grootte ongedaan maken en de standaardlay-out toepassen op het deelvenster met de gewijzigde grootte met de optie **[!UICONTROL Revert breakpoint layout]** ( Onderbrekingspunt ![](assets/reverttopreviouslypublishedversion.png)herstellen). Tik op het bovenliggende element van de component waarvan de grootte is gewijzigd om de optie weer te geven.

   >[!NOTE]
   >
   >U kunt de grootte van tabelkolommen, werkbalkknop, en doelgebiedcomponenten niet wijzigen in de modus Indeling. Gebruik de modus Stijl om het formaat van deze componenten te wijzigen.

### Voorbeeld {#example}

**Doel:** U wilt een tabelcomponent en een afbeeldingscomponent invoegen en deze parallel aan elkaar plaatsen in een adaptieve vorm.

1. Voeg de tabel- en afbeeldingscomponenten in de modus Bewerken in het aangepaste formulier in. De component image wordt weergegeven na de tabelcomponent.
1. Schakel over naar de modus Lay-out en tik op de component Tabel. De blauwe stippen om het formaat van de componentweergave te wijzigen in kolom 1 en 12.
1. Sleep de blauwe stip in kolom 12 naar kolom 6 van het responsieve raster en zet deze neer.

   ![Het eindpunt van de tabel definiëren](assets/layout_mode_end_point_table_new.png)

1. Selecteer op dezelfde manier de component Image en sleep de blauwe stip in kolom 1 tot kolom 7 van het responsieve raster. De tabel- en afbeeldingscomponenten worden parallel met elkaar weergegeven.

   ![Tabel en afbeelding parallel in de modus Lay-out](assets/table_image_parallel_new.png)

   U kunt de component Afbeelding selecteren en op de optie **Zweven tikken naar nieuwe regel** in de werkbalk om de component Afbeelding naar de volgende regel te verplaatsen.

## Deelvensters vergroten/verkleinen {#resize-panels-layout-mode}

Voer de volgende stappen uit als u het formaat van het hele deelvenster wilt wijzigen in plaats van de afzonderlijke componenten:

1. Tik op een van de componenten in het deelvenster waarvan u het formaat wilt wijzigen, selecteer Bovenliggend element ![](assets/select_parent_icon.svg)selecteren en selecteer de eerste optie in de vervolgkeuzelijst als het deelvenster het directe bovenliggende element van de component is.

   De blauwe stippen worden weergegeven aan het begin en einde van het responsieve raster.

1. Sleep de blauwe stippen om de positie van het deelvenster in het responsieve raster te definiëren.
U kunt de stappen 1 en 2 herhalen en Bovenliggend element ![](assets/float_to_new_line_icon.svg) selecteren selecteren selecteren om het gewijzigde deelvenster naar de volgende regel te verplaatsen.

## Meerdere kolommen voor een deelvenster definiëren

Voer de volgende stappen uit om het aantal kolommen voor een deelvenster te definiëren:

1. Tik in de **[!UICONTROL Edit]** modus op het deelvenster, selecteer ![Configureren](assets/configure_icon.png)en selecteer **[!UICONTROL Responsive - everything on the page without navigation]** de optie in de **[!UICONTROL Panel Layout]** vervolgkeuzelijst.

1. Tik op ![Opslaan](assets/save_icon.svg) om de eigenschappen op te slaan.

1. Tik in de **[!UICONTROL Layout]** modus op een van de componenten in het deelvenster, selecteer Bovenliggend element ![](assets/select_parent_icon.svg)selecteren en selecteer het deelvenster.

1. Tik op ![meerdere kolommen](assets/multi-column.svg) en selecteer het aantal kolommen in de vervolgkeuzelijst. Het aantal kolommen kan variëren van 1 tot en met 12. Het deelvenster wordt verdeeld in een lay-out met meerdere kolommen.

![meerdere kolommen in de lay-outmodus](assets/multi-column-layout.png)

## Het nieuwe responsieve raster inschakelen voor oude responsieve layouts {#enableresponsivegrid}

Schakel het nieuwe responsieve raster in voor formulieren die u maakt met AEM Forms 6.4 of lager om het formaat van componenten te wijzigen.

>[!NOTE]
>
>Als u overschakelt naar het nieuwe responsieve raster, worden de lay-outeigenschappen verwijderd die al zijn gedefinieerd voor componenten die in het formulier worden gebruikt.

Voer de volgende stappen uit om het nieuwe responsieve raster in te schakelen:

1. Selecteer **Lay-out** in de drop-down lijst die bij de bovenkant naast de optie van de **Voorproef** verschijnt. Er wordt een bevestiging weergegeven om de modus Lay-out in te schakelen.
1. Tik op **Ja** om de modus **Indeling** voor het formulier in te schakelen.

### Een oud fragment insluiten in een adaptief formulier met nieuwe responsieve indeling {#embed-an-old-fragment-in-an-adaptive-form-with-new-responsive-layout}

Met de nieuwe responsieve indeling voor het adaptieve formulier kunt u een adaptief formulierfragment met de oude responsieve indeling aan het formulier toevoegen. De nieuwe indeling verwijdert echter de lay-outeigenschappen die al zijn gedefinieerd voor componenten die in het fragment worden gebruikt. U kunt overschakelen naar de modus Lay-out om de eigenschappen voor de lay-out te definiëren van de componenten die in het fragment worden gebruikt.

### Een fragment met een nieuwe responsieve indeling insluiten in een oud adaptief formulier {#embed-a-fragment-with-new-responsive-layout-in-an-old-adaptive-form}

Als u een fragment met de nieuwe responsieve indeling insluit in een adaptief formulier met een oude responsieve indeling, wordt u gevraagd de modus Indeling in te schakelen voor het formulier en het fragment opnieuw in te sluiten.

Selecteer **Lay-out** in de vervolgkeuzelijst die boven aan de optie **Voorvertoning** wordt weergegeven en tik op **Ja** om de modus Lay-out in te schakelen. Selecteer de modus **Bewerken** om het fragment opnieuw in te sluiten.

## Lay-outmodus uitschakelen voor formulieren met oude responsieve indeling {#disable-layout-mode-for-forms-with-old-responsive-layout}

U kunt de modus Indeling uitschakelen voor formulieren met een oude responsieve indeling door eigenschappen te bewerken voor de sjabloon die in het formulier wordt gebruikt.

Voer de volgende stappen uit om de modus Lay-out uit te schakelen:

1. Selecteer **[!UICONTROL Tools]** > **[!UICONTROL General]** > **[!UICONTROL Templates]** en open de sjabloon die in het formulier wordt gebruikt in de **[!UICONTROL Edit]** modus.
1. Selecteer de documentcontainer in het linkervenster en tik op **[!UICONTROL Policy.]**

   ![Lay-outmodus uitschakelen](assets/policy_disable_layout_mode.png)

1. Tik op de **[!UICONTROL Layout Settings]** tab en selecteer **[!UICONTROL Disable Layout Mode]**.
1. Tik op Wijzigingen ![](assets/save_icon.png) opslaan om de sjablooneigenschappen op te slaan.

