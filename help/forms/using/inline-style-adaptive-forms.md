---
title: Inline styling van adaptieve formuliercomponenten
description: U kunt aangepaste stijlen toepassen op een adaptief formulier, maar u kunt ook inline CSS-eigenschappen toepassen op afzonderlijke componenten van een adaptief formulier.
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: author
docset: aem65
feature: Adaptive Forms,Foundation Components
exl-id: 67cfecb8-c31d-4192-904d-7bfaa1a31ea5
solution: Experience Manager, Experience Manager Forms
role: User, Developer
source-git-commit: d7b9e947503df58435b3fee85a92d51fae8c1d2d
workflow-type: tm+mt
source-wordcount: '592'
ht-degree: 0%

---

# Inline styling van adaptieve formuliercomponenten {#inline-styling-of-adaptive-form-components}

<span class="preview"> de Adobe adviseert gebruikend de moderne en verlengbare gegevens vangen [ Componenten van de Kern ](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/introduction.html?lang=nl-NL) voor [ het creëren van nieuwe Aangepaste Forms ](/help/forms/using/create-an-adaptive-form-core-components.md) of [ het toevoegen van Aangepaste Forms aan de pagina&#39;s van AEM Sites ](/help/forms/using/create-or-add-an-adaptive-form-to-aem-sites-page.md). Deze componenten betekenen een aanzienlijke vooruitgang in de aanmaak van Adaptive Forms en zorgen voor indrukwekkende gebruikerservaring. In dit artikel wordt een oudere aanpak beschreven voor de auteur Adaptive Forms die gebruikmaakt van stichtingscomponenten. </span>

| Versie | Artikelkoppeling |
| -------- | ---------------------------- |
| AEM as a Cloud Service | [ klik hier ](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/adaptive-forms-authoring/authoring-adaptive-forms-foundation-components/configure-layout-of-an-adaptive-form/inline-style-adaptive-forms.html?lang=nl-NL) |
| AEM 6,5 | Dit artikel |

U kunt de algemene verschijning en de stijl van een adaptieve vorm bepalen door stijlen te specificeren gebruikend [ themaredacteur ](../../forms/using/themes.md). Bovendien kunt u inline CSS-stijlen toepassen op afzonderlijke adaptieve formuliercomponenten en deze direct bekijken. Inline stijlen overschrijven de opmaak die in het thema is opgenomen.

## Inline CSS-eigenschappen toepassen {#apply-inline-css-properties}

Inline stijlen toevoegen aan een component:

1. Open het formulier in de formuliereditor en wijzig de modus in opmaakmodus. Om de wijze te veranderen aan het stileren wijze, op de paginakoolbar, uitgezocht ![ canvas-drop-down ](assets/canvas-drop-down.png) > **Stijl**.
1. Selecteer een component in de pagina, en selecteer uitgeven knoop ![ uitgeven-knoop ](assets/edit-button.png). Stijleigenschappen worden geopend in de zijbalk.

   U kunt ook componenten selecteren in de boomstructuur van de formulierhiërarchie in het zijpaneel. De boomstructuur in de formulierhiërarchie is beschikbaar als formulierobjecten op de zijbalk.

   U kunt ook een component selecteren in de zijbalk. In de modus Stijl worden componenten weergegeven onder Formulierobjecten. In de lijst Formulierobjecten in het zijpaneel worden echter componenten zoals velden en deelvensters vermeld. Velden en deelvensters zijn algemene componenten die componenten kunnen bevatten, zoals tekstvak en keuzerondjes.

   Wanneer u een component selecteert in het zijpaneel, ziet u alle vermelde subcomponenten en de eigenschappen van de geselecteerde component. U kunt een specifieke subcomponent selecteren en deze opmaken.

1. Klik op een tabblad in de zijbalk om CSS-eigenschappen op te geven. U kunt eigenschappen opgeven, zoals:

   * Dimensionen en positie (weergave-instelling, opvulling, hoogte, breedte, marge, positie, z-index, zwevend, wissen, overloop)
   * Tekst (lettertypefamilie, dikte, kleur, grootte, lijnhoogte en uitlijning)
   * Achtergrond (afbeelding en verloop, achtergrondkleur)
   * Rand (breedte, stijl, kleur, straal)
   * Effecten (schaduw, dekking)
   * Geavanceerd (hiermee kunt u aangepaste CSS voor de component schrijven)

1. Op dezelfde manier kunt u stijlen toepassen op andere delen van een component, zoals Widget, Bijschrift en Help.
1. Selecteer **Gedaan** om de veranderingen te bevestigen of **annuleert** om de veranderingen te verwerpen.

## Voorbeeld: inline stijlen voor een veldcomponent {#example-inline-styles-for-a-field-component}

In de volgende afbeeldingen wordt een tekstveld weergegeven voor- en nadat er inline stijlen op zijn toegepast.

![ de vakje van de Tekst component alvorens het gealigneerde stileren wordt toegepast ](assets/no-style.png)

Component van tekstvak voordat inline-stijleigenschappen worden toegepast

Let op de wijziging in de stijl van het tekstvak zoals wordt getoond in de volgende afbeelding na het toepassen van de volgende CSS-eigenschappen.

<table>
 <tbody>
  <tr>
   <td><p>Kiezer</p> </td>
   <td><p>CSS-eigenschap</p> </td>
   <td><p>Waarde</p> </td>
   <td><p>Effect</p> </td>
  </tr>
  <tr>
   <td><p>Veld</p> </td>
   <td><p>border</p> </td>
   <td><p>Randbreedte =2 px</p> <p>Randstijl=Effen</p> <p>Randkleur=#1111</p> </td>
   <td><p>Hiermee maakt u een zwarte rand van 2 px breed rond het veld</p> </td>
  </tr>
  <tr>
   <td><p>Tekstvak</p> </td>
   <td><p>background-color</p> </td>
   <td><p>#6495ED</p> </td>
   <td><p>Hiermee wijzigt u de achtergrondkleur in CornflowerBlue (#6495ED)</p> <p>Opmerking: u kunt een kleurnaam of de hexadecimale code opgeven in het waardeveld.</p> </td>
  </tr>
  <tr>
   <td><p>Label</p> </td>
   <td><p>Afmetingen en positie &gt; breedte</p> </td>
   <td><p>100 px</p> </td>
   <td><p>Hiermee stelt u de breedte in op 100 px voor het label</p> </td>
  </tr>
  <tr>
   <td>Help-pictogram Veld</td>
   <td>Tekst &gt; Tekstkleur</td>
   <td>#2ECC40</td>
   <td>Hiermee wijzigt u de kleur van het Help-pictogram.</td>
  </tr>
  <tr>
   <td><p>Lange beschrijving</p> </td>
   <td><p>text-align</p> </td>
   <td><p>midden</p> </td>
   <td><p>Lijnt de lange beschrijving voor het centreren uit</p> </td>
  </tr>
 </tbody>
</table>

![ het vakje van de Tekst stijl na het gealigneerde stileren wordt toegepast ](assets/applied-style.png)

Component van tekstvak na toepassen van inline-stijleigenschappen

Na de bovenstaande stappen kunt u andere componenten selecteren en opmaken, zoals deelvensters, verzendknoppen en keuzerondjes.

>[!NOTE]
>
>De stijleigenschappen variëren op basis van de component die u selecteert.
