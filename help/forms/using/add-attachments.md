---
title: Bijlagen toevoegen
seo-title: Bijlagen toevoegen
description: Voeg foto's en krabbelnotities als annotaties toe aan uw taak in de app AEM Forms
seo-description: Voeg foto's en krabbelnotities als annotaties toe aan uw taak in de app AEM Forms
uuid: 3d2738b4-fd43-44ec-8eaf-a2ad4b7e5af5
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: forms-app
discoiquuid: d5976ed2-4482-495c-bf77-6d192379cfef
docset: aem65
translation-type: tm+mt
source-git-commit: 56c6cfd437ef185336e81373bd5f758205b96317

---


# Bijlagen toevoegen{#adding-attachments}

## Bijlagen toevoegen in formulieren die zijn gesynchroniseerd met AEM Forms Workflow Server (AEM Forms on JEE) {#adding-annotations}

Met de app AEM Forms kunt u afbeeldingen, gekrabbelde notities en tekstnotities toevoegen aan uw formulier dat is gesynchroniseerd met de JEE-server voor AEM-formulieren. Als uw formulier wordt geladen vanaf een AEM Forms Workflow-server, worden uw bijlagen toegevoegd aan het formulier. Tik op de ![bijlage-app](assets/attachments-app.png) voor bijlagen om alle bijlagen in een formulier samen te bekijken. In het rode bericht wordt het aantal bijlagen in het formulier aangegeven. Als het formulier geen bijlagen bevat, ziet u de knop Rode meldingen niet. Als het formulier geen bijlagen bevat en u tikt op de ![bijlage bij de knop Bijlagen](assets/attch.png), kunt u opties voor het bijvoegen van foto&#39;s of krabbels kiezen.

U kunt kiezen uit de volgende opties:

* **Galerie**: Hiermee kunt u een afbeelding toevoegen van de afbeeldingen die op uw apparaat zijn opgeslagen.

* **Camera**: Hiermee kunt u een foto maken en toevoegen aan het formulier.

* **Opmerkingen**: Hiermee kunt u een krabbeltje of een tekstnotitie toevoegen. Gebruik ![krabbelen](assets/scribble.png) om een krabbeltje toe te voegen en ![toetsenbord](assets/keyboard.png) om een tekstnotitie toe te voegen.

>[!NOTE]
>
>Bijlagen die door een gebruiker zijn toegevoegd, zijn zichtbaar voor andere gebruikers van de AEM Forms-app. Andere gebruikers kunnen geen bijlagen verwijderen die door een gebruiker zijn toegevoegd.


### Het scherm Bijlagen {#the-attachments-screen}

Tik op ![bijlagen-app](assets/attachments-app.png)om alle bijlagen op een plaats weer te geven. U kunt bijlagen hier toevoegen, hernoemen en verwijderen.

![Alle bijlagen op een plaats](assets/attachments-screen.png)

Met de knop **+** in het venster Bijlagen kunt u een ander beeld, krabbeltje of tekst koppelen.

### Een foto toevoegen {#adding-a-photograph}

U kunt de camera van uw mobiele apparaat of opgeslagen afbeeldingen op uw apparaat gebruiken om een afbeelding aan het formulier te koppelen.

1. Tik op de ![bevestiging](assets/attch.png) onder in het venster.
1. Tik op **Galerie** of **Camera** in het pop-upvenster dat verschijnt.
1. Op basis van de optie die u selecteert, voert u het volgende uit:

   1. Als u **Camera** selecteert.

      Neem een foto. Tik vervolgens op de knop **Use** ![use-pic](assets/use-pic.png) .

      Of tik op de knop **Opnieuw** opnemen ![](assets/retake.png) om de foto opnieuw op te nemen.

   1. Als u **Galerie** selecteert.

      De afbeeldingsbrowser van het apparaat wordt weergegeven. Tik in de afbeeldingsbrowser van het apparaat op de afbeelding die u wilt koppelen.

### Een notitie toevoegen {#adding-a-note}

Met de optie **Notities** kunt u willekeurig gevormde scripts en tekstbijlagen aan een formulier toevoegen.

1. Tik op de ![bevestiging](assets/attch.png) onder in het venster.
1. Tik op **Notities** in het pop-upvenster dat wordt weergegeven.
1. Leg in de gebruikersinterface Notities die wordt gestart een vrij krabbeltje vast.

   ![Krabbelinterface](assets/scribble-ui.png)

   Krabbelen

   U kunt de volgende opties in de interface van het Krabbelen gebruiken:

   * **Wissen**: Wist het scherm.
   * **Gereed, knop**: Hiermee koppelt u het huidige krabbeltje.
   * **Knop** Annuleren: Hiermee wordt het huidige krabbeltje verwijderd en wordt de gebruikersinterface voor Krabbelen afgesloten.
   * ![toetsenbord](assets/keyboard.png): Hiermee wist u het krabbeltje en kunt u een tekstnotitie toevoegen.
   ![Toetsenbord in app-script voor AEM Forms](assets/keyboard-inapp.png)

## Bijlagen in formulieren die zijn gesynchroniseerd met de AEM Forms-servers zonder AEM Forms Workflow (AEM Forms on OSGi) {#attachments-in-forms-synced-with-the-aem-forms-servers-without-aem-forms-workflow-aem-forms-on-osgi}

Bijlagen voor mobiele formulieren die zijn gesynchroniseerd met AEM Forms OSGi-servers werken ongeveer op de JEE-servers van AEM Forms.

Bijlagen op formulierniveau worden niet ondersteund voor adaptieve formulieren die in de app worden geladen vanaf een OSGi-server voor AEM Forms. Als u afbeeldingen of tekstnotities wilt bijvoegen, schakelt u bijlagen op veldniveau in het formulier in wanneer u het maakt. Sleep de component voor bestandsbijlagen vanuit de browser met componenten in het veld.

In het geval van adaptieve formulieren kunt u de bijgevoegde bestanden bekijken in het document of record (DoR). Zie Document met record [genereren voor niet-XFA-adaptieve formulieren](../../forms/using/generate-document-of-record-for-non-xfa-based-adaptive-forms.md).
