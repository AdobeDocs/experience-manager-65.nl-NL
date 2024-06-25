---
title: Gebruik de modus Indeling om het formaat van componenten voor adaptieve formulieren te wijzigen
description: De positie van componenten bepalen met behulp van het responsieve raster dat beschikbaar is in de modus Lay-out
feature: Adaptive Forms,Foundation Components
exl-id: 5cf76cb1-c92c-4aed-9945-37494fef2d29
solution: Experience Manager, Experience Manager Forms
role: User, Developer
source-git-commit: d7b9e947503df58435b3fee85a92d51fae8c1d2d
workflow-type: tm+mt
source-wordcount: '1090'
ht-degree: 0%

---

# Gebruik de modus Lay-out om het formaat van componenten te wijzigen {#use-layout-mode-to-resize-components}

<span class="preview"> Adobe beveelt aan moderne en uitbreidbare gegevensvastlegging te gebruiken [Kernonderdelen](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/introduction.html) for [nieuwe Adaptieve Forms maken](/help/forms/using/create-an-adaptive-form-core-components.md) of [Aangepaste Forms toevoegen aan AEM Sites-pagina&#39;s](/help/forms/using/create-or-add-an-adaptive-form-to-aem-sites-page.md). Deze componenten betekenen een aanzienlijke vooruitgang in de aanmaak van Adaptive Forms en zorgen voor indrukwekkende gebruikerservaring. In dit artikel wordt een oudere aanpak beschreven voor de auteur Adaptive Forms die gebruikmaakt van stichtingscomponenten. </span>

| Versie | Artikelkoppeling |
| -------- | ---------------------------- |
| AEM as a Cloud Service | [Klik hier](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/adaptive-forms-authoring/authoring-adaptive-forms-foundation-components/configure-layout-of-an-adaptive-form/resize-using-layout-mode.html?) |
| AEM 6,5 | Dit artikel |


Met de adaptieve interface voor formulierontwerp kunt u de grootte van componenten aanpassen in de modus Indeling. Sleep blauwe stippen in kolommen om de begin- en eindpunten voor de positiecomponenten te definiëren. De blauwe stippen worden weergegeven nadat u op de component in het responsieve raster hebt getikt. Het responsieve raster bestaat uit twaalf gelijke kolommen. Met de witte en blauwe kleurschaduw in alternatieve kolommen wordt de ene kolom onderscheiden van de andere.

U kunt de modus Lay-out gebruiken om het formaat van componenten te wijzigen voor alle apparaattypen, zoals bureaublad, tablet, telefoon en andere kleinere apparaten. De tablet leidt automatisch de lay-outconfiguratie van de Desktopversie af en de kleinere apparaten leiden lay-outconfiguratie van telefoon af. Nochtans, kunt u de automatisch afgeleide configuraties met voeten treden om een verschillende configuratie voor elk apparatentype te bepalen.

## Modus Toegang tot layout {#access-layout-mode}

Selecteren **Layout** in de vervolgkeuzelijst die boven aan de aangepaste ontwerpinterface voor formulieren wordt weergegeven naast de **Voorvertoning** -optie. Het formulier wordt weergegeven in de modus Indeling.

1. Meld u aan bij de AEM auteur en navigeer naar **Adobe Experience Manager** > **Forms** > **Forms &amp; Documenten**.
1. Een [adaptieve vorm](../../forms/using/creating-adaptive-form.md) of open een bestaande.
1. Selecteren **Layout** in de vervolgkeuzelijst die boven aan het dialoogvenster **Voorvertoning** -optie. Het formulier wordt weergegeven in de modus Indeling.

   ![Lay-outmodus](assets/layout_mode_ic_new.png)

## Formaat van componenten wijzigen {#resize-components}

1. Selecteer in de modus Lay-out de component waarvan u het formaat wilt wijzigen. De blauwe stippen worden weergegeven aan het begin en einde van het responsieve raster.
1. Sleep de blauwe stippen om de positie van de component in het responsieve raster te definiëren.

   ![Vergroten/verkleinen met de modus Lay-out](assets/layout_mode_resize_new_updated1.png)

   De werkbalk die wordt weergegeven nadat u op componenten hebt getikt, bestaat uit de volgende opties:

   * **[!UICONTROL Parent]**: Selecteer het bovenliggende element van een component.
   * **[!UICONTROL Revert breakpoint layout]**: Alle wijzigingen in de grootte ongedaan maken en de standaardlay-out toepassen op de component.
   * **[!UICONTROL Float to new line]**: Verplaats de component naar de volgende regel als er meerdere componenten binnen dezelfde regel zijn.

   U kunt ook de opdracht **[!UICONTROL Revert breakpoint layout]** ( ![Onderbrekingspunt herstellen](assets/reverttopreviouslypublishedversion.png)) op deelvensterniveau om alle wijzigingen in de grootte ongedaan te maken.

   >[!NOTE]
   >
   >U kunt de grootte van tabelkolommen, werkbalkknop, en doelgebiedcomponenten niet wijzigen in de modus Indeling. Gebruik de modus Stijl om het formaat van deze componenten te wijzigen.

### Voorbeeld {#example}

**Doel:** U wilt een tabelcomponent en een afbeeldingscomponent invoegen en deze parallel aan elkaar plaatsen in een adaptieve vorm.

1. Voeg de tabel- en afbeeldingscomponenten in met de modus Bewerken in het adaptieve formulier. De component image wordt weergegeven na de tabelcomponent.
1. Schakel over naar de modus Lay-out en selecteer de component Tabel. De blauwe stippen om het formaat van de componentweergave te wijzigen in kolom 1 en 12.
1. Sleep de blauwe stip in kolom 12 naar kolom 6 van het responsieve raster en zet deze neer.

   ![Het eindpunt van de tabel definiëren](assets/layout_mode_end_point_table_new.png)

1. Selecteer op dezelfde manier de component Image en sleep de blauwe stip in kolom 1 tot kolom 7 van het responsieve raster. De tabel- en afbeeldingscomponenten worden parallel met elkaar weergegeven.

   ![Tabel en afbeelding parallel in de modus Lay-out](assets/table_image_parallel_new.png)

   U kunt de component Image selecteren en **Zweven naar nieuwe regel** beschikbaar in de werkbalk om de component Afbeelding naar de volgende regel te verplaatsen.

## Deelvensters vergroten/verkleinen {#resize-panels-layout-mode}

Voer de volgende stappen uit als u het formaat van het hele deelvenster wilt wijzigen in plaats van de afzonderlijke componenten:

1. Selecteer de componenten in het deelvenster waarvan u het formaat wilt wijzigen. Selecteer ![Bovenliggend element selecteren](assets/select_parent_icon.svg)en selecteert u de eerste optie in de vervolgkeuzelijst als het deelvenster het directe bovenliggende element van de component is.

   De blauwe stippen worden weergegeven aan het begin en einde van het responsieve raster.

1. Sleep de blauwe stippen om de positie van het deelvenster in het responsieve raster te definiëren.
U kunt de stappen 1 en 2 herhalen en ![Bovenliggend element selecteren](assets/float_to_new_line_icon.svg) om het vergrote of verkleinde deelvenster naar de volgende regel te verplaatsen.

## Meerdere kolommen voor een deelvenster definiëren

Voer de volgende stappen uit om het aantal kolommen voor een deelvenster te definiëren:

1. In **[!UICONTROL Edit]** , selecteert u het deelvenster en selecteert u ![Configureren](assets/configure_icon.png)en selecteert u **[!UICONTROL Responsive - everything on the page without navigation]** van de **[!UICONTROL Panel Layout]** vervolgkeuzelijst.

1. Selecteren ![Opslaan](assets/save_icon.svg) om de eigenschappen op te slaan.

1. In de **[!UICONTROL Layout]** , selecteert u een van de componenten in het deelvenster en selecteert u ![Bovenliggend element selecteren](assets/select_parent_icon.svg)en selecteert u het deelvenster.

1. Selecteren ![meerdere kolommen](assets/multi-column.svg) en selecteert u het aantal kolommen in de vervolgkeuzelijst. Het aantal kolommen kan variëren van 1 tot 12. Het deelvenster wordt verdeeld in een lay-out met meerdere kolommen.

![meerdere kolommen in de lay-outmodus](assets/multi-column-layout.png)

## Het nieuwe responsieve raster inschakelen voor oude responsieve layouts {#enableresponsivegrid}

Schakel het nieuwe responsieve raster in voor formulieren die u maakt met AEM Forms 6.4 of lager om het formaat van componenten te wijzigen.

>[!NOTE]
>
>Als u overschakelt naar het nieuwe responsieve raster, worden de lay-outeigenschappen verwijderd die al zijn gedefinieerd voor componenten die in het formulier worden gebruikt.

Voer de volgende stappen uit om het nieuwe responsieve raster in te schakelen:

1. Selecteren **Layout** in de vervolgkeuzelijst die boven aan het dialoogvenster **Voorvertoning** -optie. Er wordt een bevestiging weergegeven om de modus Lay-out in te schakelen.
1. Selecteren **Ja** de **Layout** voor het formulier.

### Een oud fragment insluiten in een adaptief formulier met nieuwe responsieve indeling {#embed-an-old-fragment-in-an-adaptive-form-with-new-responsive-layout}

Met de nieuwe responsieve indeling voor het adaptieve formulier kunt u een adaptief formulierfragment met de oude responsieve indeling aan het formulier toevoegen. In de nieuwe indeling worden echter de lay-outeigenschappen verwijderd die al zijn gedefinieerd voor componenten die in het fragment worden gebruikt. U kunt overschakelen naar de modus Lay-out om de eigenschappen voor de lay-out te definiëren van de componenten die in het fragment worden gebruikt.

### Een fragment met een nieuwe responsieve indeling insluiten in een oud adaptief formulier {#embed-a-fragment-with-new-responsive-layout-in-an-old-adaptive-form}

Als u een fragment met de nieuwe responsieve indeling insluit in een adaptief formulier met een oude responsieve indeling, wordt u gevraagd de modus Indeling in te schakelen voor het formulier en het fragment opnieuw in te sluiten.

Selecteer **Layout** in de vervolgkeuzelijst die boven aan het dialoogvenster **Voorvertoning** en selecteert u **Ja** ter bevestiging. Selecteren **Bewerken** om het fragment opnieuw in te sluiten.

## Lay-outmodus uitschakelen voor formulieren met oude responsieve indeling {#disable-layout-mode-for-forms-with-old-responsive-layout}

U kunt de modus Indeling uitschakelen voor formulieren met een oude responsieve indeling door eigenschappen te bewerken voor de sjabloon die in het formulier wordt gebruikt.

Voer de volgende stappen uit om de modus Lay-out uit te schakelen:

1. Selecteren **[!UICONTROL Tools]** > **[!UICONTROL General]** > **[!UICONTROL Templates]** en opent u de sjabloon die in het formulier wordt gebruikt **[!UICONTROL Edit]** -modus.
1. Selecteer de Documentcontainer in het linkerdeelvenster en selecteer **[!UICONTROL Policy.]**

   ![Lay-outmodus uitschakelen](assets/policy_disable_layout_mode.png)

1. Selecteer de **[!UICONTROL Layout Settings]** en selecteert u **[!UICONTROL Disable Layout Mode]**.
1. Selecteren ![Wijzigingen opslaan](assets/save_icon.png) de sjablooneigenschappen opslaan.
