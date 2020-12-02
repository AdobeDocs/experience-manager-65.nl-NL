---
title: Geneste groepen ontwerpen
seo-title: Geneste groepen ontwerpen
description: Geneste groepen maken
seo-description: Geneste groepen maken
uuid: b377dc1b-bbb6-41c9-b0fc-8281e1410685
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: introduction
content-type: reference
discoiquuid: 752235d2-21ac-46d2-82ed-5fec09c645e9
docset: aem65
translation-type: tm+mt
source-git-commit: 5d196d1f6d5f94f2d3ef0d4461cfe38562f8ba8c
workflow-type: tm+mt
source-wordcount: '539'
ht-degree: 3%

---


# Geneste groepen ontwerpen{#authoring-nested-groups}

## Groepen maken op auteur {#creating-groups-on-author}

Op een instantie van AEM-auteur, van globale navigatie:

* Selecteer **[!UICONTROL Communities]** > **[!UICONTROL Sites]**.
* Selecteer **[!UICONTROL engage folder]** om het te openen.
* Selecteer de kaart voor de **[!UICONTROL Getting Started Tutorial]** Engelse site.

   * Selecteer de kaartafbeelding.
   * Selecteer een pictogram *niet*.

Het resultaat is om [Groepenconsole](/help/communities/groups.md) te bereiken:

![createGroup](assets/create-group.png)

De groepfunctie wordt weergegeven als een map waarin instanties van groepen worden gemaakt. Selecteer de map Groepen om deze te openen. De groep die bij publicatie wordt gemaakt, is zichtbaar.

![create-new-group](assets/create-new-group.png)

## Hoofdartgroep maken {#create-main-arts-group}

Deze groep kan worden gemaakt omdat de sitestructuur voor de verbinding een groepfunctie bevat. De configuratie van de functie in de site `Reference Template` staat standaard de selectie van een ingeschakelde groepssjabloon toe. De sjabloon die voor deze nieuwe groep is gekozen, is dus `Reference Group`.

Deze consoles zijn gelijkaardig aan de console van Plaatsen van Gemeenschappen.

* Selecteer **[!UICONTROL Create Group]**.

* **Template** voor communautaire groep:

   * **[!UICONTROL Community Group Title]**: Kunst.
   * **[!UICONTROL Community Group Description]**: Een bovenliggende groep voor verschillende kunstgroepen.
   * **[!UICONTROL Community Group Root]**:  *standaard* laten staan.
   * **[!UICONTROL Additional Available Community Group Language(s)]**: gebruikt u het keuzemenu om de beschikbare taal of talen van groepen in de gemeenschap te selecteren. In het menu worden alle talen weergegeven waarin de bovenliggende communitysite is gemaakt. Gebruikers kunnen in deze ene stap uit deze talen kiezen om groepen te maken in meerdere landinstellingen. De zelfde groep wordt gecreeerd in veelvoudige gespecificeerde talen in de console van Groepen van de respectieve communautaire plaatsen.
   * **[!UICONTROL Community Group Name]**: kunst.
   * **[!UICONTROL Template]**: keuzelijst selecteren  `Reference Group.`
   * Selecteer **[!UICONTROL Next]**.

![Geneste groepen van gemeenschappen](assets/parent-to-nestedgroup.png)

Doorloop de andere deelvensters met deze instellingen:

* **[!UICONTROL Design]**

   * Het ontwerp wijzigen of het ontwerp van de standaard bovenliggende site toestaan.
   * Selecteer **[!UICONTROL Next]**.

* **[!UICONTROL Settings]**

   * **[!UICONTROL Moderation]**

      * Leeg laten (overerven van bovenliggende site).
   * **[!UICONTROL Membership]**

      * Standaard `Optional Membership.` gebruiken

      * **[!UICONTROL Thumbnail]**
         * `optional.*`
      * **[!UICONTROL Select Next]**.



* Selecteer **[!UICONTROL Create]**.

### Groepen nesten in artgroep {#nesting-groups-within-arts-group}

De map `groups` bevat nu twee groepen (vernieuw de pagina).

![Groepen nesten](assets/create-community-group.png)

#### Groep {#publish-group} publiceren

Voordat u groepen maakt die in de groep `arts` zijn genest, plaatst u de aanwijzer op de kaart `arts` en selecteert u het publicatiepictogram om deze te publiceren.

![publicatiesite](assets/publish-site.png)

Wacht op bevestiging dat de groep is gepubliceerd.

![in groep gepubliceerd](assets/group-published.png)

De `arts` groep zou ook een `groups` omslag moeten bevatten, maar die leeg is en waarin de nieuwe groepen kunnen worden gecreeerd. Navigeer naar de map met kunstgroepen en maak drie geneste groepen, elk met een andere lidmaatschapsinstelling:

1. **[!UICONTROL Visual]**

   * Titel: `Visual Arts`
   * Naam: `visual`
   * Sjabloonmodel: `Reference Group`
   * Lidmaatschap: Selecteer `Optional Membership`, een openbare groep, open aan alle leden.

1. **[!UICONTROL Auditory]**

   * Titel: `Auditory Arts`
   * Naam: `auditory`
   * Sjabloonmodel: `Reference Group`
   * Lidmaatschap: Selecteer `Required Membership`, een open groep, beschikbaar voor leden om zich aan te sluiten.

1. **[!UICONTROL History]**

   * Titel: `Art History`
   * Naam: `history`
   * Sjabloonmodel: `Reference Group`
   * Lidmaatschap: Selecteer `Restricted Membership`, een geheime groep, die slechts aan uitgenodigde leden zichtbaar is. Als voorbeeld, nodig [demo gebruiker](/help/communities/tutorials.md#demo-users) `emily.andrews@mailinator.com`.

Vernieuw de pagina om alle drie geneste groepen (subgemeenschappen) weer te geven.

Om aan de genestelde groepen van de console van Plaatsen van Gemeenschappen te navigeren:

* Selecteer **[!UICONTROL engage folder]**
* Selecteer **[!UICONTROL Getting Started Tutorial card]**
* Map **[!UICONTROL Groups]** selecteren
* Selecteer **[!UICONTROL arts card]**
* Map **[!UICONTROL Groups]** selecteren

![create-new-group2](assets/create-new-group2.png)

## Groepen {#publishing-groups} publiceren

![publicatiesite](assets/publish-site.png)

Na publicatie van de hoofdsite van de community:

* Elke groep afzonderlijk publiceren:

   * Wachtend op bevestiging dat de groep is gepubliceerd.

* Publiceer bovenliggende groep voordat u groepen publiceert die zijn genest in:

   * Alle groepen moeten van boven naar beneden worden gepubliceerd.

![in groep gepubliceerd](assets/group-published.png)

## Ervaring met publiceren {#experience-on-publish}

Het is mogelijk om de verschillende groepen te ervaren wanneer u zich aanmeldt, bijvoorbeeld met de [demogebruikers](/help/communities/tutorials.md#demo-users) die worden gebruikt voor:

* Groepslid illustratie/geschiedenis: emily.andrews@mailinator.com/password
   * De beperkte (geheime) groep, kunst/geschiedenis, is zichtbaar:
   * Kan optionele (openbare) groepen zien.
   * Kan beperkte (open) groepen samenvoegen.

* Groepsbeheer: aaron.mcdonald@mailinator.com/password

   * Kan optionele (openbare) groepen zien.
   * Kan beperkte (open) groepen samenvoegen.
   * Kan beperkte (geheime) groepen niet zien.

Open de [Samenstellingen leden en groepen](/help/communities/members.md) op auteur om andere gebruikers aan diverse lidgroepen toe te voegen die aan de communautaire groepen beantwoorden.

