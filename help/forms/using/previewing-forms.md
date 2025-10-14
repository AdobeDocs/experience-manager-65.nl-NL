---
title: Een voorbeeld van een formulier bekijken
description: U kunt een voorbeeld van uw formulieren bekijken voordat u het publiceert of activeert. Zo kunt u controleren of het formulier aan de verwachtingen voldoet. Voorvertoningsopties kunnen per ondersteund formuliertype verschillen.
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: author
discoiquuid: 377d804d-4a75-4c93-8125-d2660cf56418
feature: Adaptive Forms,Foundation Components
exl-id: aed5703e-4fe6-4839-9657-c660ac48521e
solution: Experience Manager, Experience Manager Forms
role: User, Developer
source-git-commit: d7b9e947503df58435b3fee85a92d51fae8c1d2d
workflow-type: tm+mt
source-wordcount: '406'
ht-degree: 0%

---

# Een voorbeeld van een formulier bekijken {#previewing-a-form}

<span class="preview"> de Adobe adviseert gebruikend de moderne en verlengbare gegevens vangen [&#x200B; Componenten van de Kern &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/introduction.html?lang=nl-NL) voor [&#x200B; het creëren van nieuwe Aangepaste Forms &#x200B;](/help/forms/using/create-an-adaptive-form-core-components.md) of [&#x200B; het toevoegen van Aangepaste Forms aan de pagina&#39;s van AEM Sites &#x200B;](/help/forms/using/create-or-add-an-adaptive-form-to-aem-sites-page.md). Deze componenten betekenen een aanzienlijke vooruitgang in de aanmaak van Adaptive Forms en zorgen voor indrukwekkende gebruikerservaring. In dit artikel wordt een oudere aanpak beschreven voor de auteur Adaptive Forms die gebruikmaakt van stichtingscomponenten. </span>

## Overzicht {#overview}

In AEM Forms kunt u een voorbeeld bekijken van de formulieren en documenten in de opslagplaats. Met Voorvertoning kunt u precies zien hoe de formulieren eruitzien en zich gedragen wanneer ze worden vrijgegeven aan de eindgebruikers.

Als u een voorbeeld van formulieren bekijkt, worden deze weergegeven in een interactieve interface en kan de gebruiker de formulieren invullen met gegevens. Als u documenten voorvertoont, worden deze in een niet-interactieve modus weergegeven en kan de gebruiker het document alleen bekijken. Voor formulieren is een extra optie voor Aangepaste voorvertoning beschikbaar. Met deze optie kunt u een voorbeeld van het formulier weergeven met gegevens uit een XML-bestand. De gegevens vullen enkele of alle velden van het formulier waarvan een voorbeeld wordt weergegeven.

In de volgende tabel worden de voorbeeldopties weergegeven die beschikbaar zijn voor verschillende typen ondersteunde formulieren:

<table>
 <tbody>
  <tr>
   <td><strong> Type van Activa </strong><br /> </td>
   <td><strong> Beschikbare voorproefopties </strong><br /> </td>
  </tr>
  <tr>
   <td>Document</td>
   <td>PDF-voorvertoning</td>
  </tr>
  <tr>
   <td>PDF-formulier</td>
   <td>PDF voorproef en Voorproef met Gegevens <br /> </td>
  </tr>
  <tr>
   <td>adaptieve vorm</td>
   <td>HTML-voorvertoning en HTML-voorvertoning met gegevens</td>
  </tr>
  <tr>
   <td>Formuliersjabloon</td>
   <td>PDF voorproef, PDF voorproef met Gegevens, HTML voorproef, HTML voorproef met Gegevens <br /> </td>
  </tr>
 </tbody>
</table>

## Een voorbeeld van een formulier bekijken {#previewing-a-form-1}

1. Selecteer activa u wilt voorproef, en klik Voorproef ![&#x200B; aem6forms_preview &#x200B;](assets/aem6forms_preview.png) in de actietoolbar.

   >[!NOTE]
   >
   >Als u een element wilt selecteren, schakelt u over naar de lijstweergave in de standaardkaartweergave. Klik ![&#x200B; aem6forms_viewlist &#x200B;](assets/aem6forms_viewlist.png) of ![&#x200B; aem6forms_viewcard &#x200B;](assets/aem6forms_viewcard.png) om meningen te schakelen.

1. Klik op Voorvertoning om de mogelijke voorvertoningsopties weer te geven die van toepassing zijn op het geselecteerde elementtype. Klik op de gewenste optie om het geselecteerde element op een nieuw tabblad weer te geven.

   U kunt kiezen uit de volgende opties:

   * Voorvertonen als HTML
   * Voorvertonen met gegevens
   * Voorvertonen als PDF (beschikbaar voor formuliersjablonen)

## Voorvertonen met gegevens {#preview-with-data}

Wanneer u **Voorproef met Gegevens** selecteert, kunt u zien hoe de vorm met echte gegevens ingegaan in het kijkt. Met de optie Voorvertonen met gegevens kunt u een XML uploaden die voorbeeldgebruikersgegevens bevat. De voorbeeldgebruikersgegevens worden gebruikt om het voorbeeldformulier in de door u gekozen indeling in te vullen.

1. Selecteer een activa, klik Voorproef ![&#x200B; aem6forms_preview &#x200B;](assets/aem6forms_preview.png), en selecteer **Voorproef met Gegevens**.
1. Geef in het dialoogvenster Formulier voorvertonen de formuliergegevens op als een XML-bestand. Klik op Voorbeeld om het formulier te genereren met de samengevoegde gegevens van XML.
