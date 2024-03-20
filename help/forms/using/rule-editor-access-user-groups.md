---
title: De toegang van de regelredacteur van de subsidie tot uitgezochte gebruikersgroepen
description: Verleen beperkte toegang tot de regelredacteur om gebruikersgroepen te selecteren.
content-type: reference
topic-tags: adaptive_forms, develop
products: SG_EXPERIENCEMANAGER/6.5/FORMS
docset: aem65
feature: Adaptive Forms, Foundation Components
exl-id: a1a2b277-3133-404b-a7fc-337cedddb12c
solution: Experience Manager, Experience Manager Forms
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '357'
ht-degree: 0%

---

# De toegang van de regelredacteur van de subsidie tot uitgezochte gebruikersgroepen{#grant-rule-editor-access-to-select-user-groups}

<span class="preview"> Adobe beveelt aan moderne en uitbreidbare gegevensvastlegging te gebruiken [Kernonderdelen](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/introduction.html) for [nieuwe Adaptieve Forms maken](/help/forms/using/create-an-adaptive-form-core-components.md) of [Aangepaste Forms toevoegen aan AEM Sites-pagina&#39;s](/help/forms/using/create-or-add-an-adaptive-form-to-aem-sites-page.md). Deze componenten betekenen een aanzienlijke vooruitgang in de aanmaak van Adaptive Forms en zorgen voor indrukwekkende gebruikerservaring. In dit artikel wordt een oudere aanpak beschreven voor het ontwerpen van Adaptive Forms met behulp van stichtingscomponenten. </span>

## Overzicht {#overview}

U kunt verschillende typen gebruikers hebben met verschillende vaardigheden die werken met Adaptive Forms. Hoewel ervaren gebruikers de juiste kennis hebben om met scripts en complexe regels te werken, kunnen er gebruikers op basisniveau zijn die alleen met de indeling en basiseigenschappen van adaptieve formulieren moeten werken.

Met AEM Forms kunt u op basis van hun rol of functie de toegang tot regeleditors beperken. In de instellingen van de Adaptive Forms Configuration Service kunt u de [gebruikersgroepen](/help/sites-administering/security.md) die tot de regelredacteur kunnen bekijken en toegang hebben.

## Geef gebruikersgroepen op die toegang kunnen krijgen tot de regeleditor {#specify-user-groups-that-can-access-rule-editor}

1. Meld u als beheerder aan bij AEM Forms.
1. Klik in de auteur-instantie op ![adobeexperienceManager](assets/adobeexperiencemanager.png)Adobe Experience Manager > Gereedschappen ![hamer](assets/hammer.png) > Bewerkingen > Webconsole. De webconsole wordt in een nieuw venster geopend.

   ![1-2](assets/1-2.png)

1. Zoek en klik in het venster Webconsole op **[!UICONTROL Adaptive Form and Interactive Communication Web Channel Configuration]**. **[!UICONTROL Adaptive Form and Interactive Communication Web Channel Configuration]** wordt weergegeven. Wijzig geen waarde en klik op **Opslaan**.

   Het leidt tot een dossier /apps/system/config/com.adobe.aemds.guide.service.impl.AdaptiveFormConfigurationServiceImpl.config in CRX-bewaarplaats.

1. Meld u als beheerder aan bij CRXDE. Open het bestand /apps/system/config/com.adobe.aemds.guide.service.impl.AdaptiveFormConfigurationServiceImpl.config voor bewerking.
1. Gebruik het volgende bezit om de naam van een groep te specificeren die tot regelredacteur (bijvoorbeeld, RuleEditorsUserGroup) kan toegang hebben en klik **Alles opslaan**.

   `af.ruleeditor.custom.groups=["RuleEditorsUserGroup"]`

   Als u toegang voor meerdere groepen wilt inschakelen, geeft u een lijst met door komma&#39;s gescheiden waarden op:

   `af.ruleeditor.custom.groups=["RuleEditorsUserGroup", "PermittedUserGroup"]`

   ![Gebruiker maken](assets/create_user_new.png)

   Nu, wanneer een gebruiker die geen deel van de gespecificeerde gebruikersgroep (hier RuleEditorsUserGroup) uitmaakt een gebied tikt, geeft het Edit pictogram van de Regel ( ![edit-rules1](assets/edit-rules1.png)) is niet beschikbaar voor deze componenten op de werkbalk Componenten:

   ![componentstoolbarwither](assets/componentstoolbarwithre.png)

   De toolbar van componenten zoals zichtbaar aan een gebruiker met de toegang van de regelredacteur

   ![componentstoolbarwithouding](assets/componentstoolbarwithoutre.png)

   De toolbar van Componenten zoals zichtbaar aan een gebruiker zonder de toegang van de regelredacteur

   Zie voor instructies over het toevoegen van gebruikers aan groepen [Gebruikersbeheer en beveiliging](/help/sites-administering/security.md).
