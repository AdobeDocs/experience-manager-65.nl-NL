---
title: Automatisch opslaan gebruiken in AEM Forms-app
seo-title: Automatisch opslaan gebruiken in AEM Forms-app
description: Leer hoe u de functie voor automatisch opslaan in de AEM Forms-app kunt gebruiken om gegevensverlies te voorkomen.
seo-description: Leer hoe u de functie voor automatisch opslaan in de AEM Forms-app kunt gebruiken om gegevensverlies te voorkomen.
uuid: 00fe6a10-1a72-443d-a840-0415dc769199
contentOwner: sashanka
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: forms-app
discoiquuid: 2c71cc28-b7c8-4785-9fc2-b47fa80cbd70
docset: aem65
translation-type: tm+mt
source-git-commit: d9975c0dcc02ae71ac64aadb6b4f82f7c993f32c
workflow-type: tm+mt
source-wordcount: '316'
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

1. Meld u aan bij de app en navigeer naar **Instellingen > Algemeen**.
1. Gebruik in het scherm Algemeen de optie **Frequentie automatisch opslaan** om de intervallen te selecteren waarmee u wilt dat de toepassing de ingevoerde gegevens opslaat.
   [ ![Frequentie voor automatisch opslaan instellen](assets/using-autosave-freq-07.png)](assets/using-autosave-freq-07-1.png)

1. Wanneer u de app opnieuw opstart en u bij dezelfde gebruiker aanmeldt, wordt u gevraagd om uw taak te herstellen met het dialoogvenster Niet-opgeslagen taak herstellen. Klik **OK** in het dialoogvenster Niet-opgeslagen taak herstellen om het werken met de opgeslagen taak te hervatten. U kunt **Annuleren** klikken om de opgeslagen gegevens te verwijderen die overeenkomen met de laatst getriggerde automatisch opslaan en beginnen met het werken met een nieuwe taak.

   Wanneer u op **OK** klikt, wordt de taak hersteld met de gegevens die overeenkomen met de meest recente automatisch opgeslagen gegevens die zijn geactiveerd voordat de app is vastgelopen. Het bevat de formuliergegevens en alle bijlagen die bij de taak horen.
   [ ![Een taak ophalen ](assets/autosave-flow.png)](assets/using-autosave-freq-06.png)**teruggekregenA.** A werk-in-uitvoering formulier  **B.** App forcent gesloten  **C.** App opnieuw begonnen met het dialoogvenster Niet-opgeslagen taak herstellen  **D.** Formulier teruggezet met oorspronkelijke gegevens

