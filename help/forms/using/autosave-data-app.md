---
title: Automatisch opslaan gebruiken in AEM Forms-app
description: Leer hoe u de functie voor automatisch opslaan in de AEM Forms-app kunt gebruiken om gegevensverlies te voorkomen.
contentOwner: sashanka
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: forms-app
docset: aem65
exl-id: 1603eef1-d7c8-47d3-8cfa-55ec3eaadd64
solution: Experience Manager, Experience Manager Forms
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '294'
ht-degree: 0%

---

# Automatisch opslaan gebruiken in AEM Forms-app{#using-autosave-in-aem-forms-app}

Wanneer een gebruiker gegevens in de Adobe Experience Manager Forms-app invoert, slaat de functie voor automatisch opslaan deze op regelmatige intervallen op. Met de functie voor automatisch opslaan in de AEM Forms-app kunt u gegevensverlies voorkomen als de app per ongeluk wordt gesloten.

Uw app kan per ongeluk worden gesloten:

* Als het apparaat wordt uitgeschakeld als gevolg van een lage accu
* Als de gebruiker de app heeft gedood
* Als er een onverwachte crash optreedt

U kunt de intervallen opgeven waarna de toepassing de ingevoerde gegevens opslaat.

>[!NOTE]
>
>Selecteer de frequentie voor automatisch opslaan verstandig. De regelmatige autosave verrichtingen kunnen een merkbare invloed op de prestaties van uw apparaat hebben.

Voer de volgende stappen uit om de functie voor automatisch opslaan te gebruiken in de AEM Forms-app:

1. Meld u aan bij de app en ga naar **Instellingen > Algemeen**.
1. Gebruik in het scherm Algemeen de optie **Frequentie automatisch opslaan** Selecteer de intervallen waarmee u de ingevoerde gegevens wilt opslaan in de app.
   [![Frequentie voor automatisch opslaan instellen](assets/using-autosave-freq-07.png)](assets/using-autosave-freq-07-1.png)

1. Wanneer u de app opnieuw opstart en u bij dezelfde gebruiker aanmeldt, wordt u gevraagd om uw taak te herstellen met het dialoogvenster Niet-opgeslagen taak herstellen. Klikken **OK** in het dialoogvenster Niet-opgeslagen taak herstellen om de opgeslagen taak verder uit te voeren. U kunt op **Annuleren** om de opgeslagen gegevens te verwijderen die overeenkomen met de laatst getriggerde automatische opslag en te beginnen met het werken met een nieuwe taak.

   Wanneer u op **OK**, wordt de taak hersteld met de gegevens die overeenkomen met de laatste automatische opslag die is geactiveerd voordat de app is vastgelopen. Het bevat de formuliergegevens en alle bijlagen die bij de taak horen.
   [![Een taak terugkrijgen ](assets/autosave-flow.png)](assets/using-autosave-freq-06.png)**A.** Een werk in uitvoering formulier **B.** App forceerd gesloten **C.** Toepassing opnieuw gestart met dialoogvenster Niet-opgeslagen taak herstellen **D.** Het formulier is hersteld met de oorspronkelijke gegevens
