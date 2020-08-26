---
title: Gedeelde wachtrijen configureren
seo-title: Gedeelde wachtrijen configureren
description: Leer hoe u gedeelde wachtrijen kunt gebruiken voor Forms-centric workflows op AEM Forms op OSGi.
seo-description: Leer hoe u gedeelde wachtrijen kunt gebruiken voor Forms-centric workflows op AEM Forms op OSGi.
uuid: null
topic-tags: process
products: SG_EXPERIENCEMANAGER/6.5/FORMS
discoiquuid: null
docset: aem65
translation-type: tm+mt
source-git-commit: 2c8220aab9215efba2e4568961a2a6a544803920
workflow-type: tm+mt
source-wordcount: '817'
ht-degree: 0%

---


# Deel en verzoek toegang tot Inbox punten van een gebruiker {#share-and-request-access}

Een wachtrij is een lijst met items in AEM Postvak IN van een gebruiker. Dit kunnen punten zijn die aan een gebruiker of punten worden toegewezen aan de groep wordt gedeeld een gebruiker is een lid van. U kunt uw Postvak IN openen om het Postvak IN-item weer te geven en actie te ondernemen. Deel bijvoorbeeld een item met een andere gebruiker.

U kunt uw Postvak IN-items ook met een andere gebruiker delen. Zodra een andere gebruiker toegang heeft tot uw Inbox-items, kan de gebruiker een claim indienen en de juiste actie ondernemen voor gedeelde items. Op dezelfde manier kunt u andere gebruikers om toegang tot Inbox-items verzoeken.

## Voorwaarden {#pre-requisites}

De het programma geopende gebruiker moet een lid van de `workflow-users` groep zijn. De gebruiker kan punten delen of om toegang tot punten slechts van de gebruikers verzoeken de het programma geopende gebruiker heeft gelezen toestemmingen op of slechts van de gebruikers die openbare profiel hebben toegelaten.

## Eén of alle items van uw Postvak IN delen met een andere gebruiker

AEM Met Inbox kunt u een enkele of alle items in uw Postvak IN delen met een andere gebruiker.

### Alle postvakitems delen

Voer de volgende stappen uit om alle items in een Postvak IN te delen met een andere gebruiker:

1. Meld u aan bij uw AEM. Tik op het pictogram ![Inbox](assets/bell.svg) en tik op **[!UICONTROL View All]**. Er wordt een lijst met je postvak-items weergegeven.
1. Tik op het pictogram ![Weergavekiezer](assets/viewlist.svg) of ![Weergavekiezer](assets/calendar.svg) naast de **[!UICONTROL Create]** knop en tik op **[!UICONTROL Settings]**. Het dialoogvenster Instellingen wordt weergegeven.
1. Open het **[!UICONTROL Share]** tabblad in het dialoogvenster Instellingen.
1. Typ de naam van een gebruiker in het **[!UICONTROL Grant access of your Inbox items]** tekstvak en tik op **[!UICONTROL Grant]**. Herhaal deze stap om meer gebruikers toe te voegen. Alle gebruikers met toegang tot uw items worden weergegeven onder de sectie **Gebruikersnaam** .
1. Tik op **[!UICONTROL Save]**.

>[!NOTE]
>
>(Alleen voor Forms-centrische workflowitems) Schakel de optie **[Toestaan dat een gebruiker zijn of haar gegevens kan delen via Postvak IN-delen](aem-forms-workflow-step-reference.md)** in van de stap Taak **** toewijzen in de workflow. Alleen items waarvoor de bovenstaande optie is ingeschakeld, worden weergegeven aan andere gebruikers.

### Afzonderlijke items delen

Voer de volgende stappen uit om een Inbox-item met een andere gebruiker te delen:

1. Meld u aan bij uw AEM. Tik op het pictogram ![Inbox](assets/bell.svg) en tik op **[!UICONTROL View All]**. Er wordt een lijst met je postvak-items weergegeven.
1. Selecteer een item en tik op **[!UICONTROL Share]**. Er wordt een dialoogvenster weergegeven.
1. Typ de naam van een gebruiker in het tekstvak Gebruikers toevoegen om dit item te delen en tik op **[!UICONTROL Add]**. Herhaal deze stap om meer gebruikers toe te voegen. Alle gebruikers met toegang tot je objecten worden onder de **[!UICONTROL Username]** sectie weergegeven.
1. Tik op **[!UICONTROL Save]**.


>[!NOTE]
>
>(Alleen voor workflowitems die op Forms zijn gericht) Schakel de optie Toegewezen **[toestaan in om expliciet te delen in Postvak](aem-forms-workflow-step-reference.md)** van de stap Taak **** toewijzen in de workflow in. Alleen items waarvoor de bovenstaande optie is ingeschakeld, worden weergegeven aan andere gebruikers.

## Toegang aanvragen tot postvakken {#request-access}

U kunt toegang tot de items in het Postvak IN van een andere gebruiker aanvragen. Zodra de toegang wordt verleend, kunt u bekijken, eisen, en aangewezen acties op gedeelde punten nemen. Voer de volgende stappen uit om toegang tot Inbox-items van een andere gebruiker aan te vragen:

1. Meld u aan bij uw AEM. Tik op het pictogram ![Weergavekiezer](assets/bell.svg) en tik op **[!UICONTROL View All]**.
1. Tik op het pictogram ![Weergavekiezer](assets/viewlist.svg) of ![Weergavekiezer](assets/calendar.svg) naast de **[!UICONTROL Create]** knop en tik op **[!UICONTROL Settings]**. Het dialoogvenster Instellingen wordt weergegeven.
1. Typ de naam van een gebruiker in het **[!UICONTROL Request access to Inbox items of the user]** tekstvak en tik op **[!UICONTROL Request]**. Een verzoek wordt verzonden naar de gebruiker en de status van het verzoek wordt getoond tegen de naam van de gebruiker. Herhaal deze stap om meer gebruikers toe te voegen.
1. Tik op **[!UICONTROL Save]**. Het verzoek wordt verzonden als Inbox punt aan de gebruikers. De gebruiker kan het item selecteren en op Goedkeuren of Afwijzen tikken om de toegang te verlenen of af te wijzen.


## Items claimen die door andere gebruikers worden gedeeld {#claim-items}

U kunt pas aan een gedeeld item gaan werken nadat u dit hebt opgeëist. Hiermee voorkomt u dat meerdere gebruikers aan één item werken. Voer de volgende stappen uit om een object te claimen:

1. Meld u aan bij uw AEM. Tik op het pictogram Inbox ![Inbox](assets/bell.svg) en tik op **[!UICONTROL View All]**.
1. Tik op het pictogram Alleen ![](assets/railleft.svg) inhoud om de filterkiezer te openen.
1. Tik op de **[!UICONTROL Select Assignee]** vervolgkeuzelijst om gebruikers weer te geven en te selecteren die hun Postvak IN-items met u hebben gedeeld.
1. Selecteer een item en tik op **[!UICONTROL Claim]**. Het item wordt toegevoegd aan je Postvak IN.

## Opgevraagde items vrijgeven {#release-items}

U kunt alleen aan een gedeeld item werken nadat u dit hebt opgeëist. Andere gebruikers kunnen een door u geclaimd object niet zien of bewerken. Als u niet aan een punt kunt blijven werken, kunt u het terug naar de pool vrijgeven.   Nadat je het object hebt uitgebracht, kunnen anderen een claim indienen en aan het object werken:

Voer de volgende stappen uit om een item vrij te geven:

1. Meld u aan bij uw AEM. Tik op het pictogram Inbox ![Inbox](assets/bell.svg) en tik op **[!UICONTROL View All]**. Er wordt een lijst met je postvak-items weergegeven.
1. Selecteer het item dat u wilt loslaten en tikken **[!UICONTROL UnClaim]**. Het item wordt weer aan de pool toegevoegd. Anderen kunnen nu het object aanvragen.

## Beperkingen {#limitations}

* Het delen van items met een groep wordt niet ondersteund.
* Het delen van projecttaken wordt niet ondersteund.
