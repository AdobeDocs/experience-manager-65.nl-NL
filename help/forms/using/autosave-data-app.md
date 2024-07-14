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
feature: Adaptive Forms
role: User, Developer
source-git-commit: e821be5233fd5f6688507096790d219d25903892
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

1. Login aan app, en navigeer aan **Montages > Algemeen**.
1. In het Algemene scherm, gebruik de **optie van de Frequentie Autosave** om de intervallen te selecteren waarmee u app de ingevoerde gegevens wilt bewaren.
   [![ plaatsend autosave frequentie ](assets/using-autosave-freq-07.png)](assets/using-autosave-freq-07-1.png)

1. Wanneer u de app opnieuw opstart en u bij dezelfde gebruiker aanmeldt, wordt u gevraagd om uw taak te herstellen met het dialoogvenster Niet-opgeslagen taak herstellen. Klik **O.K.** in het Herstellen Unsaved dialoog van de Taak om het werken met de bewaarde taak te hervatten. U kunt **klikken annuleert** om de bewaarde gegevens te schrappen die aan laatste teweeggebracht autosave beantwoorden en beginnen met het werken met een nieuwe taak.

   Wanneer u **O.K.** klikt, wordt de taak hersteld met de gegevens die aan recentste autosave beantwoorden die vóór app wordt teweeggebracht vastliep. Het bevat de formuliergegevens en alle bijlagen die bij de taak horen.
   [![ het krijgen van een taak teruggekregen ](assets/autosave-flow.png)](assets/using-autosave-freq-06.png)**A.** A werk-in-ondergang vorm **B.** App gesloten forcously **C.** App opnieuw begonnen met Herstel Unsaved de dialoog van de Taak **D.** Vorm hersteld met originele gegevens
