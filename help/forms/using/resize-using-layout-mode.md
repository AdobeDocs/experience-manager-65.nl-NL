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

<span class="preview"> de Adobe adviseert gebruikend de moderne en verlengbare gegevens vangen [ Componenten van de Kern ](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/introduction.html) voor [ het creëren van nieuwe Aangepaste Forms ](/help/forms/using/create-an-adaptive-form-core-components.md) of [ het toevoegen van Aangepaste Forms aan de pagina&#39;s van AEM Sites ](/help/forms/using/create-or-add-an-adaptive-form-to-aem-sites-page.md). Deze componenten betekenen een aanzienlijke vooruitgang in de aanmaak van Adaptive Forms en zorgen voor indrukwekkende gebruikerservaring. In dit artikel wordt een oudere aanpak beschreven voor de auteur Adaptive Forms die gebruikmaakt van stichtingscomponenten. </span>

| Versie | Artikelkoppeling |
| -------- | ---------------------------- |
| AEM as a Cloud Service | [ klik hier ](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/adaptive-forms-authoring/authoring-adaptive-forms-foundation-components/configure-layout-of-an-adaptive-form/resize-using-layout-mode.html?) |
| AEM 6,5 | Dit artikel |


Met de adaptieve interface voor formulierontwerp kunt u de grootte van componenten aanpassen in de modus Indeling. Sleep blauwe stippen in kolommen om de begin- en eindpunten voor de positiecomponenten te definiëren. De blauwe stippen worden weergegeven nadat u op de component in het responsieve raster hebt getikt. Het responsieve raster bestaat uit twaalf gelijke kolommen. Met de witte en blauwe kleurschaduw in alternatieve kolommen wordt de ene kolom onderscheiden van de andere.

U kunt de modus Lay-out gebruiken om het formaat van componenten te wijzigen voor alle apparaattypen, zoals bureaublad, tablet, telefoon en andere kleinere apparaten. De tablet leidt automatisch de lay-outconfiguratie van de Desktopversie af en de kleinere apparaten leiden lay-outconfiguratie van telefoon af. Nochtans, kunt u de automatisch afgeleide configuraties met voeten treden om een verschillende configuratie voor elk apparatentype te bepalen.

## Modus Toegang tot layout {#access-layout-mode}

Selecteer **Lay-out** van de drop-down lijst die bij de bovenkant van de adaptieve vorm auteursinterface naast de **3&rbrace; optie van de Voorproef &lbrace;verschijnt.** Het formulier wordt weergegeven in de modus Indeling.

1. Login aan de AEM auteursinstantie en navigeer aan **Adobe Experience Manager** > **Forms** > **Forms &amp; Documenten**.
1. Creeer een [ adaptieve vorm ](../../forms/using/creating-adaptive-form.md) of open bestaande.
1. Selecteer **Lay-out** van de drop-down lijst die bij de bovenkant naast de **3&rbrace; optie van de Voorproef &lbrace;verschijnt.** Het formulier wordt weergegeven in de modus Indeling.

   ![ wijze van de Lay-out ](assets/layout_mode_ic_new.png)

## Formaat van componenten wijzigen {#resize-components}

1. Selecteer in de modus Lay-out de component waarvan u het formaat wilt wijzigen. De blauwe stippen worden weergegeven aan het begin en einde van het responsieve raster.
1. Sleep de blauwe stippen om de positie van de component in het responsieve raster te definiëren.

   ![ het Vergroten van formaat gebruikend de wijze van de Lay-out ](assets/layout_mode_resize_new_updated1.png)

   De werkbalk die wordt weergegeven nadat u op componenten hebt getikt, bestaat uit de volgende opties:

   * **[!UICONTROL Parent]**: selecteer het bovenliggende element van een component.
   * **[!UICONTROL Revert breakpoint layout]**: maak alle wijzigingen in de grootte ongedaan en pas de standaardlay-out toe op de component.
   * **[!UICONTROL Float to new line]**: verplaats de component naar de volgende regel als er meerdere componenten binnen dezelfde regel zijn.

   U kunt **[!UICONTROL Revert breakpoint layout]** ( ![ gebruiken terugkeert Breekpunt ](assets/reverttopreviouslypublishedversion.png)) optie op het paneel-niveau om alle het resizing veranderingen ongedaan te maken.

   >[!NOTE]
   >
   >U kunt de grootte van tabelkolommen, werkbalkknop, en doelgebiedcomponenten niet wijzigen in de modus Indeling. Gebruik de modus Stijl om het formaat van deze componenten te wijzigen.

### Voorbeeld {#example}

**Doel:** u een lijstcomponent en een component van het Beeld wilt opnemen en hen parallel aan elkaar in een adaptieve vorm plaatsen.

1. Voeg de tabel- en afbeeldingscomponenten in met de modus Bewerken in het adaptieve formulier. De component image wordt weergegeven na de tabelcomponent.
1. Schakel over naar de modus Lay-out en selecteer de component Tabel. De blauwe stippen om het formaat van de componentweergave te wijzigen in kolom 1 en 12.
1. Sleep de blauwe stip in kolom 12 naar kolom 6 van het responsieve raster en zet deze neer.

   ![ bepaalt het eindpunt van de lijst ](assets/layout_mode_end_point_table_new.png)

1. Selecteer op dezelfde manier de component Image en sleep de blauwe stip in kolom 1 tot kolom 7 van het responsieve raster. De tabel- en afbeeldingscomponenten worden parallel met elkaar weergegeven.

   ![ Lijst en het beeld parallel op de wijze van de Lay-out ](assets/table_image_parallel_new.png)

   U kunt de component van het Beeld selecteren en **Vloeiend aan nieuwe lijn** optie beschikbaar in de toolbar selecteren om de component van het Beeld naar de volgende lijn te verschuiven.

## Deelvensters vergroten/verkleinen {#resize-panels-layout-mode}

Voer de volgende stappen uit als u het formaat van het hele deelvenster wilt wijzigen in plaats van de afzonderlijke componenten:

1. Selecteer om het even welke componenten in het paneel dat u wilt resize, ![ Uitgezochte Ouder ](assets/select_parent_icon.svg) selecteren, en de eerste optie in de drop-down lijst selecteren, als het paneel de directe ouder van de component is.

   De blauwe stippen worden weergegeven aan het begin en einde van het responsieve raster.

1. Sleep de blauwe stippen om de positie van het deelvenster in het responsieve raster te definiëren.
U kunt stappen 1 en 2 herhalen en ![ selecteren Uitgezochte Ouder ](assets/float_to_new_line_icon.svg) om het resized paneel aan de volgende lijn te verschuiven.

## Meerdere kolommen voor een deelvenster definiëren

Voer de volgende stappen uit om het aantal kolommen voor een deelvenster te definiëren:

1. Op **[!UICONTROL Edit]** wijze, selecteer het paneel, selecteer ![ vormen ](assets/configure_icon.png), en selecteer **[!UICONTROL Responsive - everything on the page without navigation]** optie van de **[!UICONTROL Panel Layout]** drop-down lijst.

1. Selecteer ![ sparen ](assets/save_icon.svg) om de eigenschappen te bewaren.

1. Op de **[!UICONTROL Layout]** wijze, selecteer om het even welke componenten in het paneel, selecteer ![ Uitgezochte Ouder ](assets/select_parent_icon.svg), en selecteer het paneel.

1. Selecteer ![ multi-column ](assets/multi-column.svg) en selecteer het aantal kolommen van de drop-down lijst. Het aantal kolommen kan variëren van 1 tot 12. Het deelvenster wordt verdeeld in een lay-out met meerdere kolommen.

![ meerdere kolom op lay-outwijze ](assets/multi-column-layout.png)

## Het nieuwe responsieve raster inschakelen voor oude responsieve layouts {#enableresponsivegrid}

Schakel het nieuwe responsieve raster in voor formulieren die u maakt met AEM Forms 6.4 of lager om het formaat van componenten te wijzigen.

>[!NOTE]
>
>Als u overschakelt naar het nieuwe responsieve raster, worden de lay-outeigenschappen verwijderd die al zijn gedefinieerd voor componenten die in het formulier worden gebruikt.

Voer de volgende stappen uit om het nieuwe responsieve raster in te schakelen:

1. Selecteer **Lay-out** van de drop-down lijst die bij de bovenkant naast de **3&rbrace; optie van de Voorproef &lbrace;verschijnt.** Er wordt een bevestiging weergegeven om de modus Lay-out in te schakelen.
1. Selecteer **ja** om de **3&rbrace; wijze van de Lay-out &lbrace;voor de vorm toe te laten.**

### Een oud fragment insluiten in een adaptief formulier met nieuwe responsieve indeling {#embed-an-old-fragment-in-an-adaptive-form-with-new-responsive-layout}

Met de nieuwe responsieve indeling voor het adaptieve formulier kunt u een adaptief formulierfragment met de oude responsieve indeling aan het formulier toevoegen. In de nieuwe indeling worden echter de lay-outeigenschappen verwijderd die al zijn gedefinieerd voor componenten die in het fragment worden gebruikt. U kunt overschakelen naar de modus Lay-out om de eigenschappen voor de lay-out te definiëren van de componenten die in het fragment worden gebruikt.

### Een fragment met een nieuwe responsieve indeling insluiten in een oud adaptief formulier {#embed-a-fragment-with-new-responsive-layout-in-an-old-adaptive-form}

Als u een fragment met de nieuwe responsieve indeling insluit in een adaptief formulier met een oude responsieve indeling, wordt u gevraagd de modus Indeling in te schakelen voor het formulier en het fragment opnieuw in te sluiten.

Om de wijze van de Lay-out toe te laten, uitgezochte **Lay-out** van de drop-down lijst die bij de bovenkant naast de **3&rbrace; optie van de Voorproef &lbrace;verschijnt en selecteert** ja **om te bevestigen.** Selecteer **uitgeven** wijze om het fragment opnieuw in te bedden.

## Lay-outmodus uitschakelen voor formulieren met oude responsieve indeling {#disable-layout-mode-for-forms-with-old-responsive-layout}

U kunt de modus Indeling uitschakelen voor formulieren met een oude responsieve indeling door eigenschappen te bewerken voor de sjabloon die in het formulier wordt gebruikt.

Voer de volgende stappen uit om de modus Lay-out uit te schakelen:

1. Selecteer **[!UICONTROL Tools]** > **[!UICONTROL General]** > **[!UICONTROL Templates]** en open de sjabloon in het formulier in de modus **[!UICONTROL Edit]** .
1. Selecteer de Documentcontainer in het linkerdeelvenster en selecteer **[!UICONTROL Policy.]**

   ![ maak wijze van de Lay-out ](assets/policy_disable_layout_mode.png) onbruikbaar

1. Selecteer de tab **[!UICONTROL Layout Settings]** en selecteer **[!UICONTROL Disable Layout Mode]** .
1. Selecteer ![ sparen veranderingen ](assets/save_icon.png) om de malplaatjeeigenschappen te bewaren.
