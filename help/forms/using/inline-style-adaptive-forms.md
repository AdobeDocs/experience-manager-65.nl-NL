---
title: Inline styling van adaptieve formuliercomponenten
seo-title: Inline CSS-eigenschappen voor adaptieve formuliercomponenten
description: U kunt aangepaste stijlen toepassen op een adaptief formulier, maar u kunt ook inline CSS-eigenschappen toepassen op afzonderlijke componenten van een adaptief formulier.
seo-description: U kunt aangepaste stijlen toepassen op een adaptief formulier, maar u kunt ook inline CSS-eigenschappen toepassen op afzonderlijke componenten van een adaptief formulier.
uuid: e863780e-2250-4bea-9569-22be5638d54e
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: author
discoiquuid: 21dec713-c76d-408b-baea-fc585377b429
docset: aem65
translation-type: tm+mt
source-git-commit: 33f73225fbb2c48353c1f34db3339c0bb79d4236

---


# Inline styling van adaptieve formuliercomponenten {#inline-styling-of-adaptive-form-components}

U kunt de algemene weergave en stijl van een adaptief formulier definiëren door stijlen op te geven met de [themaeditor](../../forms/using/themes.md). Bovendien kunt u inline CSS-stijlen toepassen op afzonderlijke adaptieve formuliercomponenten en deze direct bekijken. Inline stijlen overschrijven de opmaak die in het thema is opgenomen.

## Inline CSS-eigenschappen toepassen {#apply-inline-css-properties}

Inline stijlen toevoegen aan een component:

1. Open het formulier in de formuliereditor en wijzig de modus in opmaakmodus. Tik op de paginaboolbalk op ![canvas-vervolgkeuzelijst](assets/canvas-drop-down.png) > **Stijl** om de modus te wijzigen in de opmaakmodus.
1. Selecteer een component op de pagina en tik op de ![bewerkknop](assets/edit-button.png). Stijleigenschappen worden geopend in de zijbalk.

   U kunt ook componenten selecteren in de boomstructuur van de formulierhiërarchie in het zijpaneel. De boomstructuur in de formulierhiërarchie is beschikbaar als formulierobjecten op de zijbalk.

   U kunt ook een component selecteren in de zijbalk. In de modus Stijl worden componenten weergegeven onder Formulierobjecten. In de lijst Formulierobjecten in het zijpaneel worden echter componenten zoals velden en deelvensters vermeld. Velden en deelvensters zijn algemene componenten die componenten kunnen bevatten, zoals tekstvak en keuzerondjes.

   Wanneer u een component selecteert in het zijpaneel, ziet u alle vermelde subcomponenten en de eigenschappen van de geselecteerde component. U kunt een specifieke subcomponent selecteren en deze opmaken.

1. Klik op een tabblad in de zijbalk om CSS-eigenschappen op te geven. U kunt eigenschappen opgeven, zoals:

   * Dimensies en positie (weergave-instelling, opvulling, hoogte, breedte, marge, positie, z-index, zwevend, wissen, overloop)
   * Tekst (lettertypefamilie, dikte, kleur, grootte, lijnhoogte en uitlijning)
   * Achtergrond (afbeelding en verloop, achtergrondkleur)
   * Rand (breedte, stijl, kleur, straal)
   * Effecten (schaduw, dekking)
   * Geavanceerd (hiermee kunt u aangepaste CSS voor de component schrijven)

1. Op dezelfde manier kunt u stijlen toepassen op andere delen van een component, zoals Widget, Bijschrift en Help.
1. Tik op **Gereed** om de wijzigingen te bevestigen of **Annuleren** om de wijzigingen te verwijderen.

## Voorbeeld: inline stijlen voor een veldcomponent {#example-inline-styles-for-a-field-component}

In de volgende afbeeldingen wordt een tekstveld weergegeven voor- en nadat er inline stijlen op zijn toegepast.

![Component van tekstvak voordat inline-opmaak wordt toegepast](assets/no-style.png)

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
   <td><p>Hiermee wijzigt u de achtergrondkleur in CornflowerBlue (#6495ED)</p> <p>Opmerking: U kunt een kleurnaam of de hexadecimale code opgeven in het waardeveld.</p> </td>
  </tr>
  <tr>
   <td><p>Label</p> </td>
   <td><p>Afmetingen en positie &gt; breedte</p> </td>
   <td><p>100px</p> </td>
   <td><p>Hiermee stelt u de breedte in op 100 px voor het label</p> </td>
  </tr>
  <tr>
   <td>Pictogram Help-veld</td>
   <td>Tekst &gt; Lettertypekleur</td>
   <td>#2ECC40</td>
   <td>Hiermee wijzigt u de kleur van het gezicht van het Help-pictogram.</td>
  </tr>
  <tr>
   <td><p>Lange beschrijving</p> </td>
   <td><p>text-align</p> </td>
   <td><p>center</p> </td>
   <td><p>Lijnt de lange beschrijving voor het centreren uit</p> </td>
  </tr>
 </tbody>
</table>

![Stijl van tekstvak nadat inline-opmaak is toegepast](assets/applied-style.png)

Component van tekstvak na toepassen van inline-stijleigenschappen

Na de bovenstaande stappen kunt u andere componenten selecteren en opmaken, zoals deelvensters, verzendknoppen en keuzerondjes.

>[!NOTE]
>
>De stijleigenschappen variëren op basis van de component die u selecteert.

