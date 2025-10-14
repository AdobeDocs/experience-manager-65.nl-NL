---
title: Gebruik de modus Lay-out om het formaat van componenten voor interactieve communicatie te wijzigen
description: De positie van componenten bepalen met behulp van het responsieve raster dat beschikbaar is in de modus Lay-out
feature: Interactive Communication
exl-id: 9534fcb2-4260-4dd0-9f7e-779b10fd3a22
solution: Experience Manager, Experience Manager Forms
role: User, Developer
source-git-commit: f6771bd1338a4e27a48c3efd39efe18e57cb98f9
workflow-type: tm+mt
source-wordcount: '854'
ht-degree: 0%

---

# Gebruik de modus Lay-out om het formaat van componenten te wijzigen {#use-layout-mode-to-resize-components}

De interactieve Communicatie het kanaal van het Web auteursinterface laat u toe om componenten te resize gebruikend de wijze van de Lay-out. Sleep blauwe stippen in kolommen om de begin- en eindpunten voor de positiecomponenten te definiëren. De blauwe stippen worden weergegeven nadat u op de component in het responsieve raster hebt getikt. Het responsieve raster bestaat uit twaalf gelijke kolommen. Met de witte en blauwe kleurschaduw in alternatieve kolommen wordt de ene kolom onderscheiden van de andere.

U kunt de modus Lay-out gebruiken om het formaat van componenten te wijzigen voor alle apparaattypen, zoals bureaublad, tablet, telefoon en andere kleinere apparaten. De tablet leidt automatisch de lay-outconfiguratie van de Desktopversie af en de kleinere apparaten leiden lay-outconfiguratie van telefoon af. Nochtans, kunt u de automatisch afgeleide configuraties met voeten treden om een verschillende configuratie voor elk apparatentype te bepalen.

>[!NOTE]
>
>Als u het kanaal van het Web creeert gebruikend [&#x200B; het kanaal van de Druk als meester &#x200B;](../../forms/using/create-interactive-communication.md) voor een Interactieve Mededeling, omvatten de componenten beschikbaar voor het resizing ook subforms en gebieden die in het kanaal van het Web gebruikend het kanaal van de Druk auto-geproduceerd zijn. Het kanaal van het Web behoudt de lay-out voor de het kanaalelementen van de Druk op de wijze van de Lay-out.

## Modus Toegang tot layout {#access-layout-mode}

Selecteer **Lay-out** van de drop-down lijst die bij de bovenkant van de Interactieve Communicatie auteursinterface naast de **3&rbrace; optie van de Voorproef &lbrace;verschijnt.** Het formulier wordt weergegeven in de modus Indeling.

1. Login aan de AEM auteursinstantie en navigeer aan **Adobe Experience Manager** > **Forms** > **Forms &amp; Documenten**.
1. Creeer een [&#x200B; Interactieve Communicatie &#x200B;](../../forms/using/create-interactive-communication.md) of open bestaande.
1. Selecteer **Lay-out** van de drop-down lijst die bij de bovenkant naast de **3&rbrace; optie van de Voorproef &lbrace;verschijnt.** Het formulier wordt weergegeven in de modus Indeling.

   ![&#x200B; wijze van de Lay-out voor Interactieve Mededelingen &#x200B;](assets/layout_mode_ic_new.png)

## Formaat van componenten wijzigen {#resize-components}

1. Selecteer in de modus Lay-out de component waarvan u het formaat wilt wijzigen. De blauwe stippen worden weergegeven aan het begin en einde van het responsieve raster.
1. Sleep de blauwe stippen om de positie van de component in het responsieve raster te definiëren.

   ![&#x200B; het Vergroten van formaat gebruikend de wijze van de Lay-out &#x200B;](assets/layout_mode_resize_new_updated.png)

   De werkbalk die wordt weergegeven nadat u op componenten hebt getikt, bestaat uit de volgende opties:

   * **Ouder:** selecteer de ouder van een component.
   * **Vloeiend aan nieuwe lijn:** Verplaats de component aan de volgende lijn als er veelvoudige componenten binnen de zelfde lijn zijn.

   U kunt alle het resizing veranderingen ongedaan maken en standaardlay-out op het paneel toepassen dat resized componenten gebruikend **[!UICONTROL Revert breakpoint layout]** ( ![&#x200B; terugkeren Breekpunt &#x200B;](assets/reverttopreviouslypublishedversion.png)) optie. Selecteer het bovenliggende element van de component waarvan de grootte is gewijzigd om de optie weer te geven.

   >[!NOTE]
   >
   >U kunt de grootte van tabelkolommen, werkbalkknop, en doelgebiedcomponenten niet wijzigen in de modus Indeling. Gebruik de modus Stijl om het formaat van deze componenten te wijzigen.

### Voorbeeld {#example}

**Doel:** u een lijstcomponent en een component van het Beeld wilt opnemen en hen parallel aan elkaar in een Interactieve Mededeling plaatsen.

1. Voeg de tabel- en afbeeldingscomponenten in met de modus Bewerken in het webkanaal van een interactieve communicatie. De component image wordt weergegeven na de tabelcomponent.
1. Schakel over naar de modus Lay-out en selecteer de component Tabel. De blauwe stippen om het formaat van de componentweergave te wijzigen in kolom 1 en 12.
1. Sleep de blauwe stip in kolom 12 naar kolom 6 van het responsieve raster en zet deze neer.

   ![&#x200B; bepaalt het eindpunt van de lijst &#x200B;](assets/layout_mode_end_point_table_new.png)

1. Selecteer op dezelfde manier de component Image en sleep de blauwe stip in kolom 1 tot kolom 7 van het responsieve raster. De tabel- en afbeeldingscomponenten worden parallel met elkaar weergegeven.

   ![&#x200B; Lijst en het beeld parallel op de wijze van de Lay-out &#x200B;](assets/table_image_parallel_new.png)

   U kunt de component van het Beeld selecteren en **Vloeiend aan nieuwe lijn** optie beschikbaar in de toolbar selecteren om de component van het Beeld naar de volgende lijn te verschuiven.

## Deelvensters vergroten/verkleinen {#resize-panels-layout-mode}

Voer de volgende stappen uit als u het formaat van het hele deelvenster wilt wijzigen in plaats van de afzonderlijke componenten:

1. Selecteer om het even welke componenten in het paneel dat u wilt resize, ![&#x200B; Uitgezochte Ouder &#x200B;](assets/select_parent_icon.svg) selecteren, en de eerste optie in de drop-down lijst selecteren, als het paneel de directe ouder van de component is.

   De blauwe stippen worden weergegeven aan het begin en einde van het responsieve raster.

1. Sleep de blauwe stippen om de positie van het deelvenster in het responsieve raster te definiëren.
U kunt stappen 1 en 2 herhalen en ![&#x200B; selecteren Uitgezochte Ouder &#x200B;](assets/float_to_new_line_icon.svg) om het resized paneel aan de volgende lijn te verschuiven.

## Meerdere kolommen voor een deelvenster definiëren

Voer de volgende stappen uit om het aantal kolommen voor een deelvenster te definiëren:

1. Op **[!UICONTROL Edit]** wijze, selecteer het paneel, selecteer ![&#x200B; vormen &#x200B;](assets/configure_icon.png), en selecteer **[!UICONTROL Responsive - everything on the page without navigation]** optie van de **[!UICONTROL Panel Layout]** drop-down lijst.

1. Selecteer ![&#x200B; sparen &#x200B;](assets/save_icon.svg) om de eigenschappen te bewaren.

1. Op de **[!UICONTROL Layout]** wijze, selecteer om het even welke componenten in het paneel, selecteer ![&#x200B; Uitgezochte Ouder &#x200B;](assets/select_parent_icon.svg), en selecteer het paneel.

1. Selecteer ![&#x200B; multi-column &#x200B;](assets/multi-column.svg) en selecteer het aantal kolommen van de drop-down lijst. Het aantal kolommen kan variëren van 1 tot 12. Het deelvenster wordt verdeeld in een lay-out met meerdere kolommen.

![&#x200B; meerdere kolom op lay-outwijze &#x200B;](assets/multi-column-layout.png)

## Lay-outmodus uitschakelen voor formulieren met oude responsieve indeling {#disable-layout-mode-for-forms-with-old-responsive-layout}

U kunt de modus Indeling uitschakelen voor formulieren met een oude responsieve indeling door eigenschappen te bewerken voor de sjabloon die in het formulier wordt gebruikt.

Voer de volgende stappen uit om de modus Lay-out uit te schakelen:

1. Selecteer **[!UICONTROL Tools]** > **[!UICONTROL General]** > **[!UICONTROL Templates]** en open de sjabloon in het formulier in de modus **[!UICONTROL Edit]** .
1. Selecteer de Documentcontainer in het linkerdeelvenster en selecteer **[!UICONTROL Policy.]**

   ![&#x200B; maak wijze van de Lay-out &#x200B;](assets/policy_disable_layout_mode.png) onbruikbaar

1. Selecteer de tab **[!UICONTROL Layout Settings]** en selecteer **[!UICONTROL Disable Layout Mode]** .
1. Selecteer ![&#x200B; sparen veranderingen &#x200B;](assets/save_icon.png) om de malplaatjeeigenschappen te bewaren.
