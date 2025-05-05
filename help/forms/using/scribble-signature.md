---
title: Krabbelhandtekening gebruiken in HTML5-formulieren
description: HTML5-formulieren worden steeds vaker gebruikt op aanraakapparaten en handtekeningen worden vaak ondersteund. Het ondertekenen van documenten op mobiele apparaten wordt een geaccepteerde manier om formulieren te ondertekenen op mobiele apparaten.
contentOwner: robhagat
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: designer
docset: aem65
feature: Forms Designer,Designer
exl-id: 2025182f-195b-40d0-aee7-67669f55b964
solution: Experience Manager, Experience Manager Forms
role: User, Developer
source-git-commit: d7b9e947503df58435b3fee85a92d51fae8c1d2d
workflow-type: tm+mt
source-wordcount: '655'
ht-degree: 0%

---

# Krabbelhandtekening gebruiken in HTML5-formulieren{#using-scribble-signature-in-html-forms}

HTML5-formulieren worden steeds vaker gebruikt op aanraakapparaten en handtekeningen worden vaak ondersteund. Scripts (schrijven met een stift of vinger) worden een geaccepteerde manier om formulieren te ondertekenen op mobiele apparaten. Met HTML5-formulieren en Forms Designer kunt u nu een scripthandtekeningveld instellen op het formulier. Wanneer het formulier in de browser wordt weergegeven, kunt u zich in deze velden aanmelden met een stift, muis of touch.

## Een formulier ontwerpen met het veld Krabbelhandtekening {#how-to-design-a-form-using-scribble-signature-field}

1. Open een formulier in Forms Designer.
1. Sleep het veld Signature Scribble naar de pagina.

   ![ designer_scripbble ](assets/designer_scribble.png)

   >[!NOTE]
   >
   >Dimensionen van het veld dat is geselecteerd in Forms Designer, worden weergegeven wanneer het veld wordt weergegeven. De afmeting van het weergegeven handtekeningvak wordt echter berekend op basis van de hoogte-breedteverhouding van het veld en niet op basis van de afmeting die is opgegeven in Forms Designer.

1. Configureer het veld Ondertekeningskrabbelen.

   In het veld Ondertekeningskrabbelveld wordt informatie over de geolocatie standaard gemarkeerd als verplicht tijdens het ondertekeningsproces op iPad (en is optioneel voor andere apparaten). Dit standaardgedrag kan worden overschreven door de waarde van de eigenschap `geoLocMandatoryOnIpad` te wijzigen. Deze eigenschap wordt als extra&#39;s weergegeven in het veld Ondertekeningskrabbelen. De volgende stappen moeten worden gewijzigd:

   1. Selecteer in het formulier het veld Scripting handtekening.
   1. Selecteer het **Source van XML** lusje.

      >[!NOTE]
      >
      >Om het lusje van Source van XML te openen, klik **Mening** > **Source van XML**.

   1. Zoek de tag `<ui>` in de tag `<field>` en wijzig de broncode om er als volgt uit te zien:

      ```xml
      <extras name="x-scribble-add-on">
      <boolean name="geoLocMandatoryOnIpad">0</boolean>
      </extras>
      ```

   1. Selecteer het **lusje van de Mening van het Ontwerp**. Voor de bevestigingsdoos, klik ja **&#x200B;**.
   1. Sla het formulier op.

1. Het formulier weergeven op een ondersteund apparaat/desktopbrowser.

## Interfaces maken met de krabbelhandtekeningen {#interfacing-with-the-scribble-signatures}

### Ondertekenen {#signing}

Nadat een veld Handtekeningenkrabbels aan het formulier is toegevoegd en het is gegenereerd, wordt een dialoogvenster geopend wanneer u op het veld klikt of erop tikt. De gebruiker kan met een muis, vinger of stift een handtekening krabbelen in het tekengebied dat wordt aangegeven door een gestippelde rechthoek.

![ geolocation ](assets/geolocation.png)

**A.** Penseel **B.** Gummetje **C.** Geolocatie **D.** Geolocatieinformatie

### Geo-tagging {#geo-tagging}

Wanneer u tijdens het maken van de krabbelmodule op het pictogram voor de geolocatie klikt, worden geografische locatie- en tijdgegevens in het veld ingesloten.

>[!NOTE]
>
>Op de iPad is het standaard verplicht om geolocatiegegevens in te sluiten.

Op iPad, wordt het geolocatiepictogram niet getoond door gebrek, en de geolocatieinformatie wordt automatisch ingebed, wanneer u **O.K.** klikt.

Voor iPads kan deze instelling worden gewijzigd door de waarde van de parameter `geoLocManadatoryOnIpad` in de parameter init van het veld in te stellen op `0` .

* Wanneer informatie over de geolocatie verplicht is, krijgt de gebruiker een kleiner tekengebied te zien. De tekst van Geolocation wordt toegevoegd wanneer de gebruiker **O.K.** pictogram op het resterende gebied klikt.
* In andere gevallen krijgt de gebruiker een volledig te tekenen gebied te zien. Als de gebruiker geolocatiegegevens insluit, wordt de grootte van dit gebied aangepast aan de tekst van de geolocatie.

### Een handtekening wissen {#clearing-a-signature}

Terwijl het gebruiken van deze eigenschap, kan een gebruiker het **pictogram van het Gummetje** klikken om het gebied te ontruimen, en opnieuw te beginnen. Als er geolocatiegegevens zijn toegevoegd, wordt deze ook gewist.

### Een handtekening opslaan {#saving-a-signature}

Het klikken van het **O.K.** pictogram bewaart het manuscript als beeld op het gebied. Het beeld en de waarden kunnen aan server voor verdere verwerking worden voorgelegd. Zodra een gebruiker **O.K.** heeft geklikt, is het krabbelgebied gesloten. De handtekening kan niet opnieuw worden bewerkt met de krabbelwidget.

Als u op het veld Krabbelen tikt of erop klikt, wordt het dialoogvenster geopend in de modus Alleen-lezen.

![ 3 ](assets/3.png)

### Pengte selecteren {#selecting-pen-size}

Klik het **pictogram van Borstels** om een lijst van beschikbare pengrootte te tonen. Klik op een pengrootte om de bijbehorende pen te gebruiken.

### Handtekeningen uit het formulier verwijderen {#delete-signatures-from-the-form}

De handtekeningen uit het formulier verwijderen:

* (Mobiele apparaten) Lang druk het handtekeningsgebied, en op de bevestigingsdialoog, uitgezochte **ja**.
* (Desktop) Beweeg over het handtekeningsgebied, klik **annuleer** pictogram, en op de bevestigingsdialoog, klik ja **&#x200B;**.
