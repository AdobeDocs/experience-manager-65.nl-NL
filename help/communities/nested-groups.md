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

* Selecteer **[!UICONTROL Communities]** > **[!UICONTROL Sites]** .
* Selecteer **[!UICONTROL engage folder]** om het te openen.
* Selecteer de kaart voor de **[!UICONTROL Getting Started Tutorial]** Engelse site.

   * Selecteer de kaartafbeelding.
   * Selecteer ** geen pictogram.

Het resultaat moet de [ console van Groepen ](/help/communities/groups.md) bereiken:

![ creeer-groep ](assets/create-group.png)

De groepfunctie wordt weergegeven als een map waarin instanties van groepen worden gemaakt. Selecteer de map Groepen om deze te openen. De groep die op Publish is gemaakt, is zichtbaar.

![ creeer-new-group ](assets/create-new-group.png)

## Hoofdartgroep maken {#create-main-arts-group}

Deze groep kan worden gemaakt omdat de sitestructuur voor engaging de functie van een groep bevat. De configuratie van de functie in de site `Reference Template` staat standaard de selectie van een ingeschakelde groepssjabloon toe. De sjabloon die voor deze nieuwe groep is gekozen, is dus de `Reference Group` .

Deze consoles zijn gelijkaardig aan de console van Plaatsen van Gemeenschappen.

* Selecteren **[!UICONTROL Create Group]**

* **Malplaatje van de Groep van de Gemeenschap**:

   * **[!UICONTROL Community Group Title]**: illustraties
   * **[!UICONTROL Community Group Description]**: Een bovenliggende groep voor verschillende kunstgroepen
   * **[!UICONTROL Community Group Root]**: *verlaat als gebrek*
   * **[!UICONTROL Additional Available Community Group Language(s)]** : gebruik het keuzemenu om de beschikbare talen voor groepen in de gebruikersgemeenschap te selecteren. In het menu worden alle talen weergegeven waarin de bovenliggende communitysite is gemaakt. Gebruikers kunnen in deze ene stap uit deze talen kiezen om groepen te maken in meerdere landinstellingen. De zelfde groep wordt gecreeerd in veelvoudige gespecificeerde talen in de console van Groepen van de respectieve communautaire plaatsen.
   * **[!UICONTROL Community Group Name]**: kunsten
   * **[!UICONTROL Template]**: vervolgkeuzelijst om te selecteren `Reference Group`
   * Selecteren **[!UICONTROL Next]**

![ Geneste communautaire groepen ](assets/parent-to-nestedgroup.png)

Doorloop de andere deelvensters met deze instellingen:

* **[!UICONTROL Design]**

   * Het ontwerp wijzigen of het ontwerp van de standaard bovenliggende site toestaan.
   * Selecteer **[!UICONTROL Next]** .

* **[!UICONTROL Settings]**

   * **[!UICONTROL Moderation]**

      * Leeg laten (overerven van bovenliggende site).

   * **[!UICONTROL Membership]**

      * Standaard gebruiken `Optional Membership.`

      * **[!UICONTROL Thumbnail]**
         * `optional.*`

      * **[!UICONTROL Select Next]**.

* Selecteer **[!UICONTROL Create]** .

### Groepen nesten binnen tekengroep {#nesting-groups-within-arts-group}

De map `groups` bevat nu twee groepen (de pagina vernieuwen).

![ Nesten van de groepen ](assets/create-community-group.png)

#### Publish-groep {#publish-group}

Voordat u groepen maakt die in de `arts` -groep zijn genest, plaatst u de aanwijzer boven de `arts` -kaart en selecteert u het publicatiepictogram om deze te publiceren.

![ publiceren-plaats ](assets/publish-site.png)

Wacht op bevestiging dat de groep is gepubliceerd.

![ groep-gepubliceerde ](assets/group-published.png)

De `arts` -groep moet ook een `groups` -map bevatten, maar een map die leeg is en waarin nieuwe groepen kunnen worden gemaakt. Navigeer naar de map met kunstgroepen en maak drie geneste groepen, elk met een andere lidmaatschapsinstelling:

1. **[!UICONTROL Visual]**

   * Titel: `Visual Arts`
   * Naam: `visual`
   * Sjabloon: `Reference Group`
   * Lidmaatschap: selecteer `Optional Membership`, een openbare groep, die voor alle leden open is.

1. **[!UICONTROL Auditory]**

   * Titel: `Auditory Arts`
   * Naam: `auditory`
   * Sjabloon: `Reference Group`
   * Lidmaatschap: selecteer `Required Membership`, een open groep, beschikbaar voor leden om zich bij te voegen.

1. **[!UICONTROL History]**

   * Titel: `Art History`
   * Naam: `history`
   * Sjabloon: `Reference Group`
   * Lidmaatschap: selecteer `Restricted Membership` , een geheime groep die alleen zichtbaar is voor uitgenodigde leden. Als voorbeeld, nodig [ demogebruiker ](/help/communities/tutorials.md#demo-users) `emily.andrews@mailinator.com` uit.

Vernieuw de pagina zodat u alle drie geneste groepen (subgemeenschappen) kunt zien.

Om aan de genestelde groepen van de console van Plaatsen van Gemeenschappen te navigeren:

* Selecteer de **[!UICONTROL engage folder]**
* Selecteren **[!UICONTROL Getting Started Tutorial card]**
* Selecteer de map **[!UICONTROL Groups]**
* Selecteren **[!UICONTROL arts card]**
* Selecteer de map **[!UICONTROL Groups]**

![ create-new-group2 ](assets/create-new-group2.png)

## Groepen publiceren {#publishing-groups}

![ publiceren-plaats ](assets/publish-site.png)

Na publicatie van de hoofdsite van de community:

* Publish elke groep afzonderlijk:

   * Wachtend op bevestiging dat de groep is gepubliceerd.

* Publish de bovenliggende groep voordat u geneste groepen publiceert:

   * Alle groepen moeten van boven naar beneden worden gepubliceerd.

![ groep-gepubliceerde ](assets/group-published.png)

## Ervaring met Publish {#experience-on-publish}

Het is mogelijk om de verschillende groepen te ervaren wanneer binnen ondertekend, bijvoorbeeld, met de [ demogebruikers ](/help/communities/tutorials.md#demo-users) die voor worden gebruikt:

* Lidmaatschap van illustratie/historiegroep: `emily.andrews@mailinator.com/password`
   * De beperkte (geheime) groep, kunst/geschiedenis, is zichtbaar:
   * Mogelijkheid om optionele (openbare) groepen te zien.
   * Deelnemen aan beperkte (open) groepen.

* Groepsbeheer: `aaron.mcdonald@mailinator.com/password`

   * Mogelijkheid om optionele (openbare) groepen te zien.
   * Deelnemen aan beperkte (open) groepen.
   * Kan beperkte (geheime) groepen niet zien.

Heb toegang tot de leden van Gemeenschappen [ en Groepen consoles ](/help/communities/members.md) op auteur om andere gebruikers aan diverse lidgroepen toe te voegen die aan de communautaire groepen beantwoorden.
