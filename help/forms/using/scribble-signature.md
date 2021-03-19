---
title: Scripthandtekening gebruiken in HTML5-formulieren
seo-title: Scripthandtekening gebruiken in HTML5-formulieren
description: HTML5-formulieren worden steeds vaker gebruikt op aanraakapparaten en handtekeningen worden vaak ondersteund. Het ondertekenen van documenten op mobiele apparaten wordt een geaccepteerde manier om formulieren te ondertekenen op mobiele apparaten.
seo-description: HTML5-formulieren worden steeds vaker gebruikt op aanraakapparaten en handtekeningen worden vaak ondersteund. Het ondertekenen van documenten op mobiele apparaten wordt een geaccepteerde manier om formulieren te ondertekenen op mobiele apparaten.
uuid: 163dd55a-971a-4dd4-93a7-a14e80184d9b
contentOwner: robhagat
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: designer
discoiquuid: ecd7f538-9c24-48e7-8450-596851e99cff
docset: aem65
feature: Designer
translation-type: tm+mt
source-git-commit: 48726639e93696f32fa368fad2630e6fca50640e
workflow-type: tm+mt
source-wordcount: '697'
ht-degree: 0%

---


# Scripthandtekening gebruiken in HTML5-formulieren{#using-scribble-signature-in-html-forms}

HTML5-formulieren worden steeds vaker gebruikt op aanraakapparaten. Handtekeningen worden vaak ondersteund. Scripts (schrijven met een stift of vinger) worden een geaccepteerde manier om formulieren te ondertekenen op mobiele apparaten. Met HTML5-formulieren en Forms Designer kunt u nu een scripthandtekeningveld instellen op het formulier. Wanneer het formulier in de browser wordt weergegeven, kunt u zich in deze velden aanmelden met een stift, muis of touch.

## Een formulier ontwerpen met het veld Krabbelhandtekening {#how-to-design-a-form-using-scribble-signature-field}

1. Open een formulier in Forms Designer.
1. Sleep het veld Signature Scribble naar de pagina.

   ![designer_scribble](assets/designer_scribble.png)

   >[!NOTE]
   >
   >Dimension van het veld dat is geselecteerd in Forms Designer, worden weergegeven wanneer het veld wordt weergegeven. De afmeting van het weergegeven handtekeningvak wordt echter berekend op basis van de hoogte-breedteverhouding van het veld en niet op basis van de afmeting die is opgegeven in Forms Designer.

1. Configureer het veld Ondertekeningskrabbelen.

   In het veld Ondertekeningskrabbelveld wordt informatie over de geolocatie standaard gemarkeerd als verplicht tijdens het ondertekeningsproces op de iPad (en optioneel voor andere apparaten). Dit standaardgedrag kan worden met voeten getreden door de waarde van het `geoLocMandatoryOnIpad` bezit te veranderen. Deze eigenschap wordt als extra&#39;s weergegeven in het veld Ondertekeningskrabbelen. De volgende stappen moeten worden gewijzigd:

   1. Selecteer in het formulier het veld Scripting handtekening.
   1. Selecteer het tabblad **XML-bron**.

      >[!NOTE]
      >
      >Als u het tabblad XML-bron wilt openen, klikt u op **Weergave** > **XML-bron**.

   1. Zoek de tag `<ui>` in de tag `<field>` en wijzig de broncode om er als volgt uit te zien:

      ```xml
      <extras name="x-scribble-add-on">
      <boolean name="geoLocMandatoryOnIpad">0</boolean>
      </extras>
      ```

   1. Selecteer het tabblad **Ontwerpweergave**. Klik in het bevestigingsvak op **Ja**.
   1. Sla het formulier op.

1. Het formulier weergeven op een ondersteund apparaat/desktopbrowser.

## Interfaces met de Krabbelhandtekeningen {#interfacing-with-the-scribble-signatures}

### Ondertekenen {#signing}

Nadat een veld Handtekeningenkrabbels aan het formulier is toegevoegd en het is gegenereerd, wordt een dialoogvenster geopend wanneer u op het veld klikt of erop tikt. De gebruiker kan met een muis, vinger of stift een handtekening krabbelen in het tekengebied dat wordt aangegeven door een gestippelde rechthoek.

![geolocatie](assets/geolocation.png)

**A.** Brush  **B.** Eraser  **C.** Geolocation  **D.** Geolocation information

### Geo-tagging {#geo-tagging}

Wanneer u tijdens het maken van de krabbelmodule op het pictogram voor de geolocatie klikt, worden geografische locatie- en tijdgegevens in het veld ingesloten.

>[!NOTE]
Op de iPad is het standaard verplicht om geolocatiegegevens in te sluiten.

Op de iPad wordt het geolocatiepictogram niet standaard weergegeven. De geolocatiegegevens worden automatisch ingesloten wanneer u op **OK** klikt.

Voor iPads kan deze instelling worden gewijzigd door de waarde van de parameter `geoLocManadatoryOnIpad` in de init-parameters van het veld te wijzigen in `0`.

* Wanneer informatie over de geolocatie verplicht is, krijgt de gebruiker een kleiner tekengebied te zien. Geolocatietekst wordt toegevoegd wanneer de gebruiker **OK** pictogram op het resterende gebied klikt.
* In andere gevallen krijgt de gebruiker een volledig te tekenen gebied te zien. Als de gebruiker geolocatiegegevens insluit, wordt de grootte van dit gebied aangepast aan de tekst van de geolocatie.

### Een handtekening wissen {#clearing-a-signature}

Wanneer u deze functie gebruikt, kan een gebruiker op het pictogram **Gummetje** klikken om het veld te wissen en opnieuw te beginnen. Als er geolocatiegegevens zijn toegevoegd, wordt deze ook gewist.

### Een handtekening opslaan {#saving-a-signature}

Als u op het pictogram **OK** klikt, wordt het script als een afbeelding in het veld opgeslagen. Het beeld en de waarden kunnen aan server voor verdere verwerking worden voorgelegd. Nadat een gebruiker op **OK** heeft geklikt, is het krabbelveld vergrendeld. De handtekening kan niet opnieuw worden bewerkt met de krabbelwidget.

Als u op het veld Krabbelen tikt of erop klikt, wordt het dialoogvenster geopend in de modus Alleen-lezen.

![3](assets/3.png)

### Pengrootte {#selecting-pen-size} selecteren

Klik op het pictogram **Penselen** om een lijst met beschikbare penformaten weer te geven. Klik of tik op een pengrootte om de bijbehorende pen te gebruiken.

### Handtekeningen verwijderen uit het formulier {#delete-signatures-from-the-form}

De handtekeningen uit het formulier verwijderen:

* (Mobiele apparaten) Druk lang op het handtekeningveld en tik **Ja** in het bevestigingsvenster.
* (Desktop) Beweeg over het handtekeningveld, klik **Cancel** pictogram, en klik **Yes** op het bevestigingsvenster.
