---
title: De toegang van de regelredacteur van de subsidie tot uitgezochte gebruikersgroepen
seo-title: De toegang van de regelredacteur van de subsidie tot uitgezochte gebruikersgroepen
description: Verleen beperkte toegang tot regelredacteur om gebruikersgroepen te selecteren.
seo-description: Verleen beperkte toegang tot regelredacteur om gebruikersgroepen te selecteren.
uuid: efa2570a-20ac-4b43-8a0e-38247f84d02f
content-type: reference
topic-tags: adaptive_forms, develop
products: SG_EXPERIENCEMANAGER/6.5/FORMS
discoiquuid: ab694a93-00d2-44d7-8ded-68ab2ad50693
docset: aem65
feature: Adaptive Forms
translation-type: tm+mt
source-git-commit: 48726639e93696f32fa368fad2630e6fca50640e
workflow-type: tm+mt
source-wordcount: '322'
ht-degree: 0%

---


# De toegang van de regelredacteur van de subsidie tot uitgezochte gebruikersgroepen{#grant-rule-editor-access-to-select-user-groups}

## Overzicht {#overview}

U kunt verschillende typen gebruikers hebben met verschillende vaardigheden die werken met Adaptive Forms. Hoewel ervaren gebruikers de juiste kennis hebben om met scripts en complexe regels te werken, kunnen er gebruikers op basisniveau zijn die alleen met de indeling en basiseigenschappen van adaptieve formulieren moeten werken.

AEM Forms staat u toe om de toegang van de regelredacteur tot gebruikers te beperken die op hun rol of functie wordt gebaseerd. In de Adaptieve montages van de Dienst van de Configuratie van Forms, kunt u [gebruikersgroepen](/help/sites-administering/security.md) specificeren die tot regelredacteur kunnen bekijken en toegang hebben.

## Specificeer gebruikersgroepen die tot regelredacteur {#specify-user-groups-that-can-access-rule-editor} kunnen toegang hebben

1. Meld u als beheerder aan bij AEM Forms.
1. Klik in de auteurinstantie op ![adobeexperienceManager](assets/adobeexperiencemanager.png)Adobe Experience Manager > Extra ![hammer](assets/hammer.png) > Bewerkingen > Webconsole. De webconsole wordt in een nieuw venster geopend.

   ![1-2](assets/1-2.png)

1. Zoek en klik op **[!UICONTROL Adaptive Form and Interactive Communication Web Channel Configuration]** in het venster Webconsole. **[!UICONTROL Adaptive Form and Interactive Communication Web Channel Configuration]** wordt weergegeven. Wijzig geen waarde en klik op **Opslaan**.

   Het leidt tot een dossier /apps/system/config/com.adobe.aemds.guide.service.impl.AdaptiveFormConfigurationServiceImpl.config in CRX-bewaarplaats.

1. Meld u als beheerder aan bij CRXDE. Open het bestand /apps/system/config/com.adobe.aemds.guide.service.impl.AdaptiveFormConfigurationServiceImpl.config voor bewerking.
1. Gebruik het volgende bezit om de naam van een groep te specificeren die tot regelredacteur (bijvoorbeeld, RuleEditorsUserGroup) kan toegang hebben en **sparen allen** klikken.

   `af.ruleeditor.custom.groups=["RuleEditorsUserGroup"]`

   Als u toegang voor meerdere groepen wilt inschakelen, geeft u een lijst op met door komma&#39;s gescheiden waarden:

   `af.ruleeditor.custom.groups=["RuleEditorsUserGroup", "PermittedUserGroup"]`

   ![Gebruiker maken](assets/create_user_new.png)

   Nu, wanneer een gebruiker die geen deel van een gespecificeerde gebruikersgroep (hier RuleEditorsUserGroup) uitmaakt een gebied tikt, is het Edit pictogram van de Regel ( ![edit-rules1](assets/edit-rules1.png)) niet beschikbaar voor haar in de componententoolbar:

   ![componentstoolbarwither](assets/componentstoolbarwithre.png)

   De toolbar van componenten zoals zichtbaar aan een gebruiker met de toegang van de regelredacteur

   ![componentstoolbarwithouding](assets/componentstoolbarwithoutre.png)

   De toolbar van Componenten zoals zichtbaar aan een gebruiker zonder de toegang van de regelredacteur

   Voor instructies bij het toevoegen van gebruikers aan groepen, zie [Gebruikersbeheer en Veiligheid](/help/sites-administering/security.md).

