---
title: Een voorbeeld van een formulier bekijken
seo-title: Een voorbeeld van een formulier bekijken
description: U kunt een voorbeeld van uw formulieren bekijken voordat u het publiceert of activeert. Zo kunt u controleren of het formulier aan de verwachtingen voldoet. Voorvertoningsopties kunnen per ondersteund formuliertype verschillen.
seo-description: U kunt een voorbeeld van uw formulieren bekijken voordat u het publiceert of activeert. Zo kunt u controleren of het formulier aan de verwachtingen voldoet. Voorvertoningsopties kunnen per ondersteund formuliertype verschillen.
uuid: 9ec359ea-f518-441c-9c3d-e3c1ea07a532
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: author
discoiquuid: 377d804d-4a75-4c93-8125-d2660cf56418
translation-type: tm+mt
source-git-commit: a3c303d4e3a85e1b2e794bec2006c335056309fb

---


# Een voorbeeld van een formulier bekijken {#previewing-a-form}

## Overzicht {#overview}

In AEM Forms kunt u een voorbeeld bekijken van de formulieren en documenten in de opslagplaats. Met Voorvertoning kunt u precies zien hoe de formulieren eruitzien en zich gedragen wanneer ze worden vrijgegeven aan de eindgebruikers.

Als u een voorbeeld van formulieren bekijkt, worden deze weergegeven in een interactieve interface en kan de gebruiker de formulieren invullen met gegevens. Als u documenten voorvertoont, worden deze in een niet-interactieve modus weergegeven en kan de gebruiker het document alleen bekijken. Voor formulieren is een extra optie voor Aangepaste voorvertoning beschikbaar. Met deze optie kunt u een voorbeeld van het formulier weergeven aan de hand van gegevens uit een XML-bestand. De gegevens vullen enkele of alle velden van het formulier waarvan een voorbeeld wordt weergegeven.

In de volgende tabel worden de voorbeeldopties weergegeven die beschikbaar zijn voor verschillende typen ondersteunde formulieren:

<table>
 <tbody>
  <tr>
   <td><strong>Type element</strong><br /> </td>
   <td><strong>Beschikbare voorvertoningsopties</strong><br /> </td>
  </tr>
  <tr>
   <td>Document</td>
   <td>PDF-voorbeeld</td>
  </tr>
  <tr>
   <td>PDF-formulier</td>
   <td>PDF-voorbeeld en Voorvertoning met gegevens<br /> </td>
  </tr>
  <tr>
   <td>adaptieve vorm</td>
   <td>HTML-voorvertoning en HTML-voorvertoning met gegevens</td>
  </tr>
  <tr>
   <td>Formuliersjabloon</td>
   <td>PDF-voorvertoning, PDF-voorvertoning met gegevens, HTML-voorvertoning, HTML-voorvertoning met gegevens<br /> </td>
  </tr>
 </tbody>
</table>

## Een voorbeeld van een formulier bekijken {#previewing-a-form-1}

1. Selecteer een element waarvan u een voorvertoning wilt weergeven en klik op Voorvertoning van ![naam6forms_preview](assets/aem6forms_preview.png) op de werkbalk Handelingen.

   >[!NOTE]
   >
   >Als u een element wilt selecteren, schakelt u over naar de lijstweergave in de standaardkaartweergave. Klik op ![em6forms_viewlist](assets/aem6forms_viewlist.png) of ![aem6forms_viewcard](assets/aem6forms_viewcard.png) om te schakelen tussen weergaven.

1. Klik op Voorvertoning om de mogelijke voorvertoningsopties weer te geven die van toepassing zijn op het geselecteerde elementtype. Klik op de gewenste optie om het geselecteerde element op een nieuw tabblad weer te geven.

   U kunt kiezen uit de volgende opties:

   * Voorvertonen als HTML
   * Voorvertonen met gegevens
   * Voorvertonen als PDF (beschikbaar voor formuliersjablonen)

## Voorvertonen met gegevens {#preview-with-data}

Wanneer u **Voorvertonen met gegevens** selecteert, kunt u zien hoe het formulier eruitziet met de werkelijke gegevens die erin zijn ingevoerd. Met de optie Voorvertonen met gegevens kunt u een XML uploaden die voorbeeldgebruikersgegevens bevat. De voorbeeldgebruikersgegevens worden gebruikt om het voorbeeldformulier in de door u gekozen indeling in te vullen.

1. Selecteer een element, klik op Voorvertoning ![aem6forms_preview](assets/aem6forms_preview.png)en selecteer **Voorvertonen met gegevens**.
1. Geef in het dialoogvenster Formulier voorvertonen de formuliergegevens op als een XML-bestand. Klik op Voorbeeld om het formulier te genereren met de samengevoegde gegevens van XML.

