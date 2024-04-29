---
title: Geneste groepen ontwerpen
description: Leer hoe u geneste groepsbestanden voor een Adobe Experience Manager Communities-site maakt.
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: introduction
content-type: reference
docset: aem65
exl-id: 55803b7a-9064-4392-9cc2-9f113fa8dc29
solution: Experience Manager
feature: Communities
role: Admin
source-git-commit: 1f56c99980846400cfde8fa4e9a55e885bc2258d
workflow-type: tm+mt
source-wordcount: '548'
ht-degree: 0%

---

# Geneste groepen ontwerpen{#authoring-nested-groups}

## Groepen maken op auteur {#creating-groups-on-author}

Op AEM instantie Auteur, van globale navigatie:

* Selecteren **[!UICONTROL Communities]** > **[!UICONTROL Sites]**.
* Selecteren **[!UICONTROL engage folder]** om het te openen.
* Selecteer de kaart voor de **[!UICONTROL Getting Started Tutorial]** Engelse site.

   * Selecteer de kaartafbeelding.
   * Do *niet* Selecteer een pictogram.

Het resultaat is dat de [Groepsconsole](/help/communities/groups.md):

![createGroup](assets/create-group.png)

De groepfunctie wordt weergegeven als een map waarin instanties van groepen worden gemaakt. Selecteer de map Groepen om deze te openen. De groep die bij Publiceren is gemaakt, is zichtbaar.

![create-new-group](assets/create-new-group.png)

## Hoofdartgroep maken {#create-main-arts-group}

Deze groep kan worden gemaakt omdat de sitestructuur voor engaging de functie van een groep bevat. De configuratie van de functie in de site `Reference Template` staat standaard de selectie van een ingeschakelde groepssjabloon toe. De voor deze nieuwe groep gekozen sjabloon is dus de `Reference Group`.

Deze consoles zijn gelijkaardig aan de console van Plaatsen van Gemeenschappen.

* Selecteren **[!UICONTROL Create Group]**

* **Template voor communautaire groep**:

   * **[!UICONTROL Community Group Title]**: Kunst
   * **[!UICONTROL Community Group Description]**: Een bovenliggende groep voor verschillende kunstgroepen
   * **[!UICONTROL Community Group Root]**: *standaard verlaten*
   * **[!UICONTROL Additional Available Community Group Language(s)]**: gebruik het keuzemenu om de beschikbare talen van de groep van de gemeenschap te selecteren. In het menu worden alle talen weergegeven waarin de bovenliggende communitysite is gemaakt. Gebruikers kunnen in deze ene stap uit deze talen kiezen om groepen te maken in meerdere landinstellingen. De zelfde groep wordt gecreeerd in veelvoudige gespecificeerde talen in de console van Groepen van de respectieve communautaire plaatsen.
   * **[!UICONTROL Community Group Name]**: kunsten
   * **[!UICONTROL Template]**: te selecteren vervolgkeuzelijst `Reference Group`
   * Selecteren **[!UICONTROL Next]**

![Geneste groepen van gemeenschappen](assets/parent-to-nestedgroup.png)

Doorloop de andere deelvensters met deze instellingen:

* **[!UICONTROL Design]**

   * Het ontwerp wijzigen of het ontwerp van de standaard bovenliggende site toestaan.
   * Selecteren **[!UICONTROL Next]**.

* **[!UICONTROL Settings]**

   * **[!UICONTROL Moderation]**

      * Leeg laten (overerven van bovenliggende site).

   * **[!UICONTROL Membership]**

      * Standaard gebruiken `Optional Membership.`

      * **[!UICONTROL Thumbnail]**
         * `optional.*`

      * **[!UICONTROL Select Next]**.

* Selecteren **[!UICONTROL Create]**.

### Groepen nesten binnen tekengroep {#nesting-groups-within-arts-group}

De `groups` Deze map bevat nu twee groepen (vernieuwen de pagina).

![Groepen nesten](assets/create-community-group.png)

#### Groep publiceren {#publish-group}

Voordat u groepen maakt die in het dialoogvenster `arts` groep, boven de `arts` en selecteer het publicatiepictogram om deze te publiceren.

![publicatiesite](assets/publish-site.png)

Wacht op bevestiging dat de groep is gepubliceerd.

![in groep gepubliceerd](assets/group-published.png)

De `arts` groep moet ook een `groups` , maar een map die leeg is en waarin nieuwe groepen kunnen worden gemaakt. Navigeer naar de map met kunstgroepen en maak drie geneste groepen, elk met een andere lidmaatschapsinstelling:

1. **[!UICONTROL Visual]**

   * Titel: `Visual Arts`
   * Naam: `visual`
   * Template: `Reference Group`
   * Lidmaatschap: selecteren `Optional Membership`, een openbare groep, open voor alle leden.

1. **[!UICONTROL Auditory]**

   * Titel: `Auditory Arts`
   * Naam: `auditory`
   * Template: `Reference Group`
   * Lidmaatschap: selecteren `Required Membership`, een open groep, beschikbaar voor leden om zich bij te voegen.

1. **[!UICONTROL History]**

   * Titel: `Art History`
   * Naam: `history`
   * Template: `Reference Group`
   * Lidmaatschap: selecteren `Restricted Membership`, een geheime groep, die alleen zichtbaar is voor uitgenodigde leden. U kunt bijvoorbeeld uitnodigen [demo-gebruiker](/help/communities/tutorials.md#demo-users) `emily.andrews@mailinator.com`.

Vernieuw de pagina zodat u alle drie geneste groepen (subgemeenschappen) kunt zien.

Om aan de genestelde groepen van de console van Plaatsen van Gemeenschappen te navigeren:

* Selecteer de **[!UICONTROL engage folder]**
* Selecteren **[!UICONTROL Getting Started Tutorial card]**
* Selecteer de **[!UICONTROL Groups]** map
* Selecteren **[!UICONTROL arts card]**
* Selecteer de **[!UICONTROL Groups]** map

![create-new-group2](assets/create-new-group2.png)

## Groepen publiceren {#publishing-groups}

![publicatiesite](assets/publish-site.png)

Na publicatie van de hoofdsite van de community:

* Elke groep afzonderlijk publiceren:

   * Wachtend op bevestiging dat de groep is gepubliceerd.

* Publiceer de bovenliggende groep voordat u groepen publiceert die zijn genest in:

   * Alle groepen moeten van boven naar beneden worden gepubliceerd.

![in groep gepubliceerd](assets/group-published.png)

## Ervaring met publiceren {#experience-on-publish}

U kunt de verschillende groepen ervaren wanneer u zich bijvoorbeeld aanmeldt bij de [demo-gebruikers](/help/communities/tutorials.md#demo-users) gebruikt voor:

* Groepslid illustratie/geschiedenis: `emily.andrews@mailinator.com/password`
   * De beperkte (geheime) groep, kunst/geschiedenis, is zichtbaar:
   * Mogelijkheid om optionele (openbare) groepen te zien.
   * Deelnemen aan beperkte (open) groepen.

* Groepsbeheer: `aaron.mcdonald@mailinator.com/password`

   * Mogelijkheid om optionele (openbare) groepen te zien.
   * Deelnemen aan beperkte (open) groepen.
   * Kan beperkte (geheime) groepen niet zien.

Toegang tot de Gemeenschappen [Samenstellingen van leden en groepen](/help/communities/members.md) auteur om andere gebruikers toe te voegen aan verschillende lidgroepen die overeenkomen met de groepen van de gemeenschap.
