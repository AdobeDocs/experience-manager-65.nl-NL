---
title: Krabbelhandtekening gebruiken in HTML5-formulieren
description: HTML5-formulieren worden steeds vaker gebruikt op aanraakapparaten en handtekeningen worden vaak ondersteund. Het ondertekenen van documenten op mobiele apparaten wordt een geaccepteerde manier om formulieren te ondertekenen op mobiele apparaten.
contentOwner: robhagat
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: designer
docset: aem65
feature: Forms Designer
exl-id: 2025182f-195b-40d0-aee7-67669f55b964
solution: Experience Manager, Experience Manager Forms
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '655'
ht-degree: 0%

---

# Krabbelhandtekening gebruiken in HTML5-formulieren{#using-scribble-signature-in-html-forms}

HTML5-formulieren worden steeds vaker gebruikt op aanraakapparaten en handtekeningen worden vaak ondersteund. Scripts (schrijven met een stift of vinger) worden een geaccepteerde manier om formulieren te ondertekenen op mobiele apparaten. Met HTML5-formulieren en Forms Designer kunt u nu een scripthandtekeningveld instellen op het formulier. Wanneer het formulier in de browser wordt weergegeven, kunt u zich in deze velden aanmelden met een stift, muis of touch.

## Een formulier ontwerpen met het veld Krabbelhandtekening {#how-to-design-a-form-using-scribble-signature-field}

1. Open een formulier in Forms Designer.
1. Sleep het veld Signature Scribble naar de pagina.

   ![designer_scribble](assets/designer_scribble.png)

   >[!NOTE]
   >
   >Dimensionen van het veld dat is geselecteerd in Forms Designer, worden weergegeven wanneer het veld wordt weergegeven. De afmeting van het weergegeven handtekeningvak wordt echter berekend op basis van de hoogte-breedteverhouding van het veld en niet op basis van de afmeting die is opgegeven in Forms Designer.

1. Configureer het veld Ondertekeningskrabbelen.

   In het veld Ondertekeningskrabbelveld wordt informatie over de geolocatie standaard gemarkeerd als verplicht tijdens het ondertekeningsproces op iPad (en is optioneel voor andere apparaten). Dit standaardgedrag kan worden overschreven door de waarde van de optie `geoLocMandatoryOnIpad` eigenschap. Deze eigenschap wordt als extra&#39;s weergegeven in het veld Ondertekeningskrabbelen. De volgende stappen moeten worden gewijzigd:

   1. Selecteer in het formulier het veld Scripting handtekening.
   1. Selecteer de **XML-bron** tab.

      >[!NOTE]
      >
      >Als u het tabblad XML-bron wilt openen, klikt u op **Weergave** > **XML-bron**.

   1. Zoek de `<ui>` in de `<field>` de broncode als volgt labelen en wijzigen:

      ```xml
      <extras name="x-scribble-add-on">
      <boolean name="geoLocMandatoryOnIpad">0</boolean>
      </extras>
      ```

   1. Selecteer de **Ontwerpweergave** tab. Klik in het bevestigingsvak op **Ja**.
   1. Sla het formulier op.

1. Het formulier weergeven op een ondersteund apparaat/desktopbrowser.

## Interfaces maken met de krabbelhandtekeningen {#interfacing-with-the-scribble-signatures}

### Ondertekenen {#signing}

Nadat een veld Handtekeningenkrabbels aan het formulier is toegevoegd en het is gegenereerd, wordt een dialoogvenster geopend wanneer u op het veld klikt of erop tikt. De gebruiker kan met een muis, vinger of stift een handtekening krabbelen in het tekengebied dat wordt aangegeven door een gestippelde rechthoek.

![geolocatie](assets/geolocation.png)

**A.** Penseel **B.** Gummetje **C.** Geolocation **D.** Geolocatie-informatie

### Geo-tagging {#geo-tagging}

Wanneer u tijdens het maken van de krabbelmodule op het pictogram voor de geolocatie klikt, worden geografische locatie- en tijdgegevens in het veld ingesloten.

>[!NOTE]
>
Op de iPad is het standaard verplicht om geolocatiegegevens in te sluiten.

Op de iPad wordt het geolocatiepictogram niet standaard weergegeven en worden de geolocatiegegevens automatisch ingesloten wanneer u op **OK**.

Voor iPads kunt u deze instelling wijzigen door de waarde van `geoLocManadatoryOnIpad` parameter to `0`in de init-parameters van het veld.

* Wanneer informatie over de geolocatie verplicht is, krijgt de gebruiker een kleiner tekengebied te zien. Geolocatietekst wordt toegevoegd wanneer de gebruiker klikt **OK** op het resterende gebied.
* In andere gevallen krijgt de gebruiker een volledig te tekenen gebied te zien. Als de gebruiker geolocatiegegevens insluit, wordt de grootte van dit gebied aangepast aan de tekst van de geolocatie.

### Een handtekening wissen {#clearing-a-signature}

Tijdens het gebruik van deze functie kan een gebruiker op de knop **Gummetje** pictogram om het veld te wissen en opnieuw te beginnen. Als er geolocatiegegevens zijn toegevoegd, wordt deze ook gewist.

### Een handtekening opslaan {#saving-a-signature}

Klik op de knop **OK** het script als een afbeelding in het veld wordt opgeslagen. Het beeld en de waarden kunnen aan server voor verdere verwerking worden voorgelegd. Nadat de gebruiker op de knop heeft geklikt **OK**, is het krabbelveld vergrendeld. De handtekening kan niet opnieuw worden bewerkt met de krabbelwidget.

Als u op het veld Krabbelen tikt of erop klikt, wordt het dialoogvenster geopend in de modus Alleen-lezen.

![3](assets/3.png)

### Pengte selecteren {#selecting-pen-size}

Klik op de knop **Penselen** om een lijst weer te geven met beschikbare penformaten. Klik op een pengrootte om de bijbehorende pen te gebruiken.

### Handtekeningen uit het formulier verwijderen {#delete-signatures-from-the-form}

De handtekeningen uit het formulier verwijderen:

* (Mobiele apparaten) Druk lang op het handtekeningveld en selecteer in het bevestigingsvenster **Ja**.
* (Computer) Houd de muisaanwijzer boven het handtekeningveld en klik op de knop **Annuleren** en klikt u in het bevestigingsvenster op **Ja**.
