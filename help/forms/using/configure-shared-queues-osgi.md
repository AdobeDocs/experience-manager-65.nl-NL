---
title: Gedeelde wachtrijen configureren
description: Leer hoe u gedeelde wachtrijen kunt gebruiken voor Forms-centric workflows op AEM Forms op OSGi.
topic-tags: process
products: SG_EXPERIENCEMANAGER/6.5/FORMS
docset: aem65
exl-id: 72cd0594-8b5e-4d14-bc6f-bca26bae50f2
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms,AEM Forms on OSGi
role: Admin, User, Developer
source-git-commit: d7b9e947503df58435b3fee85a92d51fae8c1d2d
workflow-type: tm+mt
source-wordcount: '799'
ht-degree: 0%

---

# Deel en verzoek toegang tot Inbox punten van een gebruiker {#share-and-request-access}

Een wachtrij is een lijst met items in AEM Postvak IN van een gebruiker. Dit kunnen punten zijn die aan een gebruiker of punten worden toegewezen aan de groep wordt gedeeld een gebruiker is een lid van. U hebt toegang tot uw Postvak IN om het Postvak IN-item weer te geven en actie te ondernemen. Deel bijvoorbeeld een item met een andere gebruiker.

U kunt uw Postvak IN-items ook met een andere gebruiker delen. Zodra een andere gebruiker toegang heeft tot uw Inbox-items, kan de gebruiker een claim indienen en de juiste actie ondernemen voor gedeelde items. Op dezelfde manier kunt u andere gebruikers om toegang tot Inbox-items verzoeken.

## Voorwaarden {#pre-requisites}

De aangemelde gebruiker moet lid zijn van de groep `workflow-users` . De gebruiker kan punten delen of om toegang tot punten slechts van de gebruikers verzoeken de het programma geopende gebruiker heeft gelezen toestemmingen op of slechts van de gebruikers die openbare profiel hebben toegelaten.

## Eén of alle items van uw Postvak IN delen met een andere gebruiker

Met AEM Postvak IN kunt u een enkele of alle items in uw postvak IN delen met een andere gebruiker.

### Alle postvakitems delen

Voer de volgende stappen uit om alle items in een Postvak IN te delen met een andere gebruiker:

1. Meld u aan bij uw AEM. Selecteer het ![ Inbox ](assets/bell.svg) pictogram en selecteer **[!UICONTROL View All]**. Er wordt een lijst met je postvak-items weergegeven.
1. Selecteer het ![ pictogram van de Selecteur van de Mening ](assets/viewlist.svg) of ![ van de Selecteur van de Mening ](assets/calendar.svg) naast de **[!UICONTROL Create]** knoop en selecteer **[!UICONTROL Settings]**. Het dialoogvenster Instellingen wordt weergegeven.
1. Open het tabblad **[!UICONTROL Share]** in het dialoogvenster met instellingen.
1. Voer in het tekstvak **[!UICONTROL Grant access of your Inbox items]** de naam van een gebruiker in en selecteer **[!UICONTROL Grant]** . Herhaal deze stap om meer gebruikers toe te voegen. Alle gebruikers met toegang tot uw punten verschijnen onder de **sectie van de Gebruikersnaam**.
1. Selecteer **[!UICONTROL Save]** .

>[!NOTE]
>
>(Voor Forms-centric werkschemapunten slechts) laat **[toe toewees om via Inbox te delen delend](aem-forms-workflow-step-reference.md)** optie van **toewijs taak** stap in het werkschema toe. Alleen items waarvoor de bovenstaande optie is ingeschakeld, worden weergegeven aan andere gebruikers.

### Afzonderlijke items delen

Voer de volgende stappen uit om een Inbox-item met een andere gebruiker te delen:

1. Meld u aan bij uw AEM. Selecteer het ![ Inbox ](assets/bell.svg) pictogram en selecteer **[!UICONTROL View All]**. Er wordt een lijst met je postvak-items weergegeven.
1. Selecteer een item en selecteer **[!UICONTROL Share]** . Er wordt een dialoogvenster weergegeven.
1. Typ de naam van een gebruiker in het tekstvak Gebruikers toevoegen om dit item te delen en selecteer **[!UICONTROL Add]** . Herhaal deze stap om meer gebruikers toe te voegen. Alle gebruikers met toegang tot uw items worden weergegeven onder de sectie **[!UICONTROL Username]** .
1. Selecteer **[!UICONTROL Save]** .


>[!NOTE]
>
>(Voor Forms-centric werkschemapunten slechts) laat **[toe toegewezen om uitdrukkelijk in Inbox](aem-forms-workflow-step-reference.md)** optie van **te delen taakstap** in het werkschema toewijst. Alleen items waarvoor de bovenstaande optie is ingeschakeld, worden weergegeven aan andere gebruikers.

## Toegang aanvragen tot postvakken {#request-access}

U kunt toegang tot de items in het Postvak IN van een andere gebruiker aanvragen. Zodra de toegang wordt verleend, kunt u bekijken, eisen, en aangewezen acties op gedeelde punten nemen. Voer de volgende stappen uit om toegang tot Inbox-items van een andere gebruiker aan te vragen:

1. Meld u aan bij uw AEM. Selecteer het ![ pictogram van de Selecteur van de Mening ](assets/bell.svg) en selecteer **[!UICONTROL View All]**.
1. Selecteer het ![ pictogram van de Selecteur van de Mening ](assets/viewlist.svg) of ![ van de Selecteur van de Mening ](assets/calendar.svg) naast de **[!UICONTROL Create]** knoop en selecteer **[!UICONTROL Settings]**. Het dialoogvenster Instellingen wordt weergegeven.
1. Voer in het tekstvak **[!UICONTROL Request access to Inbox items of the user]** de naam van een gebruiker in en selecteer **[!UICONTROL Request]** . Een verzoek wordt verzonden naar de gebruiker en de status van het verzoek wordt getoond tegen de naam van de gebruiker. Herhaal deze stap om meer gebruikers toe te voegen.
1. Selecteer **[!UICONTROL Save]**. Het verzoek wordt verzonden als Inbox punt aan de gebruikers. De gebruiker kan het item selecteren en Goedkeuren of Afwijzen selecteren om de toegang te verlenen of af te wijzen.


## Items claimen die door andere gebruikers worden gedeeld {#claim-items}

U kunt pas aan een gedeeld item beginnen te werken nadat u dit hebt opgeëist. Hiermee voorkomt u dat meerdere gebruikers aan één item werken. Voer de volgende stappen uit om een object te claimen:

1. Meld u aan bij uw AEM. Selecteer het Inbox ![ pictogram Inbox ](assets/bell.svg) en selecteer **[!UICONTROL View All]**.
1. Selecteer het ![ slechts Inhoud ](assets/railleft.svg) pictogram om de filterselecteur te openen.
1. Selecteer de vervolgkeuzelijst **[!UICONTROL Select Assignee]** om gebruikers weer te geven en te selecteren die hun Postvak IN-items met u hebben gedeeld.
1. Selecteer een item en selecteer **[!UICONTROL Claim]** . Het item wordt toegevoegd aan je Postvak IN.

## Opgevraagde items vrijgeven {#release-items}

U kunt alleen aan een gedeeld item werken nadat u dit hebt opgeëist. Andere gebruikers kunnen een door u geclaimd object niet zien of bewerken. Als u niet aan een punt kunt blijven werken, kunt u het terug naar de pool vrijgeven.   Nadat je het object hebt uitgebracht, kunnen anderen een claim indienen en aan het object werken:

Voer de volgende stappen uit om een item vrij te geven:

1. Meld u aan bij uw AEM. Selecteer het Inbox ![ pictogram Inbox ](assets/bell.svg) en selecteer **[!UICONTROL View All]**. Er wordt een lijst met je postvak-items weergegeven.
1. Selecteer het item dat u wilt vrijgeven en selecteer **[!UICONTROL UnClaim]** . Het item wordt weer aan de pool toegevoegd. Anderen kunnen nu een claim indienen op het object.

## Beperkingen {#limitations}

* Het delen van items met een groep wordt niet ondersteund.
* Het delen van projecttaken wordt niet ondersteund.
