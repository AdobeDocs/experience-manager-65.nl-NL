---
title: Bijlagen toevoegen
seo-title: Adding attachments
description: Foto's en scriptnotities als annotaties toevoegen aan uw taak in de AEM Forms-app
seo-description: Add photographs and scribble notes as annotations to your task in the AEM Forms app
uuid: 3d2738b4-fd43-44ec-8eaf-a2ad4b7e5af5
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: forms-app
discoiquuid: d5976ed2-4482-495c-bf77-6d192379cfef
docset: aem65
exl-id: 82282e2d-63a1-47e9-b2ec-f50a4bd32bd3
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '562'
ht-degree: 0%

---

# Bijlagen toevoegen{#adding-attachments}

## Bijlagen toevoegen in formulieren die zijn gesynchroniseerd met AEM Forms Workflow Server (AEM Forms in JEE) {#adding-annotations}

Met de AEM Forms-app kunt u afbeeldingen, gescripte notities en tekstnotities toevoegen aan uw formulier dat is gesynchroniseerd met de AEM Forms JEE-server. Als uw formulier wordt geladen vanaf een AEM Forms Workflow-server, worden uw bijlagen toegevoegd aan het formulier. U kunt op de knop voor bijlagen tikken ![bijlagen-app](assets/attachments-app.png) om alle bijlagen samen in een formulier te bekijken. In het rode bericht wordt het aantal bijlagen in het formulier aangegeven. Als het formulier geen bijlagen bevat, ziet u de knop Rode meldingen niet. Als het formulier geen bijlagen bevat, tikt u op de knop Bijlagen ![aanhalen](assets/attch.png), kunt u opties voor het bijvoegen van foto&#39;s of krabbels gebruiken.

U kunt kiezen uit de volgende opties:

* **Galerie**: Hiermee kunt u een afbeelding toevoegen van de afbeeldingen die op uw apparaat zijn opgeslagen.

* **Camera**: Hiermee kunt u een foto maken en toevoegen aan het formulier.

* **Notities**: Hiermee kunt u een krabbeltje of een tekstnotitie toevoegen. Gebruiken ![krabbelen](assets/scribble.png) om een krabbeltje toe te voegen, en ![toetsenbord](assets/keyboard.png) om een tekstnotitie toe te voegen.

>[!NOTE]
>
>Bijlagen die door een gebruiker zijn toegevoegd, zijn zichtbaar voor andere gebruikers van de AEM Forms-app. Andere gebruikers kunnen geen bijlagen verwijderen die door een gebruiker zijn toegevoegd.

### Het scherm Bijlagen {#the-attachments-screen}

Tik op ![bijlagen-app](assets/attachments-app.png). U kunt bijlagen hier toevoegen, hernoemen en verwijderen.

![Alle bijlagen op een plaats](assets/attachments-screen.png)

U kunt de **+** in het venster Bijlagen om een ander beeld, krabbeltje of tekst toe te voegen.

### Een foto toevoegen {#adding-a-photograph}

U kunt de camera van uw mobiele apparaat of opgeslagen afbeeldingen op uw apparaat gebruiken om een afbeelding aan het formulier te koppelen.

1. Tik op de knop Bijlage ![aanhalen](assets/attch.png) onder aan het venster.
1. Tikken **Galerie** of **Camera** in het pop-upvenster dat wordt weergegeven.
1. Op basis van de optie die u selecteert, voert u het volgende uit:

   1. Als u **Camera**.

      Neem een foto. Tik vervolgens op de knop **Gebruiken** ![use-pic](assets/use-pic.png) knop.

      Of tik op **Opnieuw** ![hernemen](assets/retake.png) om de foto opnieuw op te nemen.

   1. Als u **Galerie**.

      De afbeeldingsbrowser van het apparaat wordt weergegeven. Tik in de afbeeldingsbrowser van het apparaat op de afbeelding die u wilt koppelen.

### Een notitie toevoegen {#adding-a-note}

De **Notities** Met deze optie kunt u uit de vrije hand geschreven scripts en tekstbijlagen toevoegen aan uw formulier.

1. Tik op de knop Bijlage ![aanhalen](assets/attch.png) onder aan het venster.
1. Tikken **Notities** in het pop-upvenster dat wordt weergegeven.
1. Leg in de gebruikersinterface Notities die wordt gestart een vrij krabbeltje vast.

   ![Krabbelinterface](assets/scribble-ui.png)

   Krabbelen

   U kunt de volgende opties in de interface van het Krabbelen gebruiken:

   * **Wissen**: Wist het scherm.
   * **Gereed, knop**: Hiermee koppelt u het huidige krabbeltje.
   * **Knop Annuleren**: Hiermee wordt het huidige krabbeltje verwijderd en wordt de gebruikersinterface voor Krabbelen afgesloten.
   * ![toetsenbord](assets/keyboard.png): Hiermee wist u het krabbeltje en kunt u een tekstnotitie toevoegen.

   ![Toetsenbord in AEM Forms-app-script](assets/keyboard-inapp.png)

## Bijlagen in formulieren gesynchroniseerd met de AEM Forms-servers zonder AEM Forms Workflow (AEM Forms op OSGi) {#attachments-in-forms-synced-with-the-aem-forms-servers-without-aem-forms-workflow-aem-forms-on-osgi}

Bijlagen voor mobiele formulieren die zijn gesynchroniseerd met AEM Forms OSGi-servers werken vergelijkbaar met de AEM Forms JEE-servers.

Bijlagen op formulierniveau worden niet ondersteund voor adaptieve formulieren die in de app worden geladen vanaf een AEM Forms OSGi-server. Als u afbeeldingen of tekstnotities wilt bijvoegen, schakelt u bijlagen op veldniveau in het formulier in wanneer u het maakt. Sleep de component voor bestandsbijlagen vanuit de browser met componenten in het veld.

In het geval van adaptieve formulieren kunt u de bijgevoegde bestanden bekijken in het document of record (DoR). Zie, [Document met record genereren voor niet-XFA-adaptieve formulieren](../../forms/using/generate-document-of-record-for-non-xfa-based-adaptive-forms.md).
