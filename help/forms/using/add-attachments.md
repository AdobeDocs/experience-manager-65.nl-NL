---
title: Bijlagen toevoegen
description: Foto's en scriptnotities als annotaties toevoegen aan uw taak in de AEM Forms-app
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: forms-app
docset: aem65
exl-id: 82282e2d-63a1-47e9-b2ec-f50a4bd32bd3
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
role: User, Developer
source-git-commit: 539da06db98395ae6eaee8103a3e4b31204abbb8
workflow-type: tm+mt
source-wordcount: '562'
ht-degree: 0%

---

# Bijlagen toevoegen{#adding-attachments}

## Bijlagen toevoegen in formulieren die zijn gesynchroniseerd met AEM Forms Workflow Server (AEM Forms in JEE) {#adding-annotations}

Met de AEM Forms-app kunt u afbeeldingen, gekrabde notities en tekstnotities toevoegen aan uw formulier dat is gesynchroniseerd met de AEM Forms JEE-server. Als uw formulier wordt geladen vanaf een AEM Forms Workflow-server, worden uw bijlagen toegevoegd aan het formulier. U kunt de gehechtheidsknoop ![ gehechtheid-app ](assets/attachments-app.png) selecteren om alle gehechtheid in een vorm samen te zien. In het rode bericht wordt het aantal bijlagen in het formulier aangegeven. Als het formulier geen bijlagen bevat, ziet u de knop Rode meldingen niet. Als er geen gehechtheid in de vorm zijn, wanneer u de knoop van gehechtheid ![ ](assets/attch.png) selecteert, krijgt u opties om foto&#39;s of krabbels vast te maken.

U kunt kiezen uit de volgende opties:

* **Galerij**: Laat u een beeld van de beelden toevoegen die op uw apparaat worden bewaard.

* **Camera**: Laat u een beeld nemen en het toevoegen aan de vorm.

* **Nota&#39;s**: Laat u een manuscript of een tekstnota toevoegen. Het manuscript van het gebruik ![ ](assets/scribble.png) om een krabbels toe te voegen, en ![ toetsenbord ](assets/keyboard.png) om een tekstnota toe te voegen.

>[!NOTE]
>
>Bijlagen die door een gebruiker zijn toegevoegd, zijn zichtbaar voor andere gebruikers van de AEM Forms-app. Andere gebruikers kunnen geen bijlagen verwijderen die door een gebruiker zijn toegevoegd.
>

### Het scherm Bijlagen {#the-attachments-screen}

Om alle gehechtheid in een plaats te zien, selecteer ![ gehechtheid-app ](assets/attachments-app.png). U kunt bijlagen hier toevoegen, een andere naam geven en verwijderen.

![ Alle gehechtheid in een plaats ](assets/attachments-screen.png)

Met de knop **+** in het venster Bijlagen kunt u een ander beeld, krabbel of tekst toevoegen.

### Een foto toevoegen {#adding-a-photograph}

U kunt de camera van uw mobiele apparaat of opgeslagen afbeeldingen op uw apparaat gebruiken om een afbeelding aan het formulier te koppelen.

1. Selecteer de gehechtheidsknoop ![ trek ](assets/attch.png) bij de bodem van het venster.
1. Selecteer **Galerij** of **Camera** in pop-up die verschijnt.
1. Op basis van de optie die u selecteert, voert u het volgende uit:

   1. Als u **Camera** selecteert.

      Neem een foto. Dan selecteer het **gebruik** ![ gebruiken-pic ](assets/use-pic.png) knoop.

      Of selecteer **herhaal** ![ herneem ](assets/retake.png) knoop om de foto opnieuw te nemen.

   1. Als u **Galerij** selecteert.

      De afbeeldingsbrowser van het apparaat wordt weergegeven. Selecteer in de afbeeldingsbrowser van het apparaat de afbeelding die u wilt bijvoegen.

### Een notitie toevoegen {#adding-a-note}

De **Nota&#39;s** optie laat u uit de vrije hand krabbels en tekstgehechtheid in uw vorm toevoegen.

1. Selecteer de gehechtheidsknoop ![ trek ](assets/attch.png) bij de bodem van het venster.
1. Selecteer **Nota&#39;s** in pop-up die verschijnt.
1. Leg in de gebruikersinterface Notities die wordt gestart een vrij krabbeltje vast.

   ![ Krabbelinterface ](assets/scribble-ui.png)

   Krabbelen

   U kunt de volgende opties in de interface van het Krabbelen gebruiken:

   * **Duidelijk**: Wist het scherm.
   * **Gedaan knoop**: Verbindt het huidige krabbelen.
   * **annuleert knoop**: Keert het huidige krabbelen weg het Krabbelgebruikersinterface weg.
   * ![ toetsenbord ](assets/keyboard.png): ontruimt het manuscript en laat u een tekstnota toevoegen.

   ![ Toetsenbord in AEM Forms app krabble ](assets/keyboard-inapp.png)

## Bijlagen in formulieren gesynchroniseerd met de AEM Forms-servers zonder AEM Forms Workflow (AEM Forms op OSGi) {#attachments-in-forms-synced-with-the-aem-forms-servers-without-aem-forms-workflow-aem-forms-on-osgi}

Bijlagen voor mobiele formulieren die zijn gesynchroniseerd met AEM Forms OSGi-servers werken vergelijkbaar met de AEM Forms JEE-servers.

Bijlagen op formulierniveau worden niet ondersteund voor adaptieve formulieren die in de app worden geladen vanaf een AEM Forms OSGi-server. Als u afbeeldingen of tekstnotities wilt bijvoegen, schakelt u bijlagen op veldniveau in het formulier in wanneer u het maakt. Sleep de component voor bestandsbijlagen vanuit de browser met componenten in het veld.

Als er adaptieve formulieren zijn, kunt u de bijgevoegde bestanden bekijken in het document of record (DoR). Zie, [ produceer Document van Verslag voor niet-XFA aanpassende vormen ](../../forms/using/generate-document-of-record-for-non-xfa-based-adaptive-forms.md).
