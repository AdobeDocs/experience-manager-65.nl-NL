---
title: De toegang van de regelredacteur van de subsidie tot uitgezochte gebruikersgroepen
seo-title: De toegang van de regelredacteur van de subsidie tot uitgezochte gebruikersgroepen
description: Verleen beperkte toegang tot regelredacteur om gebruikersgroepen te selecteren.
seo-description: Verleen beperkte toegang tot regelredacteur om gebruikersgroepen te selecteren.
uuid: efa2570a-20ac-4b43-8a0e-38247f84d02f
content-type: reference
topic-tags: develop
products: SG_EXPERIENCEMANAGER/6.5/FORMS
discoiquuid: ab694a93-00d2-44d7-8ded-68ab2ad50693
docset: aem65
translation-type: tm+mt
source-git-commit: 44eb94b917fe88b7c90c29ec7da553e15be391db

---


# De toegang van de regelredacteur van de subsidie tot uitgezochte gebruikersgroepen{#grant-rule-editor-access-to-select-user-groups}

## Overzicht {#overview}

U kunt verschillende typen gebruikers hebben met verschillende vaardigheden die werken met Adaptieve formulieren. Hoewel ervaren gebruikers de juiste kennis hebben om met scripts en complexe regels te werken, kunnen er gebruikers op basisniveau zijn die alleen met de indeling en basiseigenschappen van adaptieve formulieren moeten werken.

Met AEM Forms kunt u de toegang tot regeleditors beperken tot gebruikers op basis van hun rol of functie. In de Adaptive montages van de Dienst van de Configuratie van Vormen, kunt u de [gebruikersgroepen](/help/sites-administering/security.md) specificeren die tot regelredacteur kunnen bekijken en toegang hebben.

## Geef gebruikersgroepen op die toegang kunnen krijgen tot de regeleditor {#specify-user-groups-that-can-access-rule-editor}

1. Meld u als beheerder aan bij AEM Forms.
1. Klik in de auteurinstantie op ![](assets/adobeexperiencemanager.png)adobeexperienceManagerAdobe Experience Manager > Tools ![hammer](assets/hammer.png) > Operations > Web Console. De webconsole wordt in een nieuw venster geopend.

   ![1-2](assets/1-2.png)

1. Zoek en klik op **Adaptieve formulierconfiguratieservice** in het venster Webconsole. **Het dialoogvenster Adaptive Form Configuration Service** wordt weergegeven. Wijzig geen waarde en klik op **Opslaan**.

   Het leidt tot een dossier /apps/system/config/com.adobe.aemds.guide.service.impl.AdaptiveFormConfigurationServiceImpl.config in CRX-bewaarplaats.

1. Meld u als beheerder aan bij CRXDE. Open het bestand /apps/system/config/com.adobe.aemds.guide.service.impl.AdaptiveFormConfigurationServiceImpl.config voor bewerking.
1. Gebruik het volgende bezit om de naam van een groep te specificeren die tot regelredacteur (bijvoorbeeld, RuleEditorsUserGroup) kan toegang hebben en klik **sparen allen**.

   `af.ruleeditor.custom.groups=["RuleEditorsUserGroup"]`

   Als u toegang voor meerdere groepen wilt inschakelen, geeft u een lijst op met door komma&#39;s gescheiden waarden:

   `af.ruleeditor.custom.groups=["RuleEditorsUserGroup", "PermittedUserGroup"]`

   ![Gebruiker maken](assets/create_user_new.png)

   Nu, wanneer een gebruiker die geen deel van een gespecificeerde gebruikersgroep (hier RuleEditorsUserGroup) uitmaakt een gebied tikt, is het Edit pictogram van de Regel ( ![geef-rules1](assets/edit-rules1.png)) niet beschikbaar voor haar in de componententoolbar:

   ![componentstoolbarwither](assets/componentstoolbarwithre.png)

   De toolbar van componenten zoals zichtbaar aan een gebruiker met de toegang van de regelredacteur

   ![componentstoolbarwithouding](assets/componentstoolbarwithoutre.png)

   De toolbar van Componenten zoals zichtbaar aan een gebruiker zonder de toegang van de regelredacteur

   Voor instructies bij het toevoegen van gebruikers aan groepen, zie het Beleid van de [Gebruiker en Veiligheid](/help/sites-administering/security.md).

