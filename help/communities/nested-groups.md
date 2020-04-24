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
source-git-commit: 22e853ecaf2696c7329a81bb9d375b1dbc74452c

---


# Geneste groepen ontwerpen{#authoring-nested-groups}

## Groepen maken op auteur {#creating-groups-on-author}

Op een instantie van AEM-auteur, van globale navigatie:

* Selecteer **[!UICONTROL Communities] > **[!UICONTROL Sites]**.
* Selecteer **[!UICONTROL Inlogmap]** om deze te openen.
* Selecteer de kaart voor de **[!UICONTROL Engelstalige website Aan de slag voor zelfstudie]** .

   * Selecteer de kaartafbeelding.
   * Selecteer *geen* pictogram.

Het resultaat moet de console [van](/help/communities/groups.md)Groepen bereiken:

![chlimage_1-91](assets/chlimage_1-91.png)

De groepfunctie wordt weergegeven als een map waarin instanties van groepen worden gemaakt. Selecteer de map Groepen om deze te openen. De groep die bij publicatie wordt gemaakt, is zichtbaar.

![chlimage_1-92](assets/chlimage_1-92.png)

## Hoofdartgroep maken {#create-main-arts-group}

Deze groep kan worden gemaakt omdat de sitestructuur voor de verbinding een groepfunctie bevat. De configuratie van de functie in de `Reference Template` standaardinstellingen van de site staat de selectie van een ingeschakelde groepssjabloon toe. De sjabloon die voor deze nieuwe groep is gekozen, is dus de `Reference Group`.

Deze consoles zijn gelijkaardig aan de console van Plaatsen van Gemeenschappen.

* Selecteer Groep **** maken.

* **Template** voor communautaire groep:

   * **[!UICONTROL Titel]** van communautaire groep: Kunst.
   * **[!UICONTROL Omschrijving]** van communautaire groep: Een bovenliggende groep voor verschillende kunstgroepen.
   * **[!UICONTROL Hoofdmap]** van communautaire groep: Standaard *laten*.
   * **[!UICONTROL Aanvullende beschikbare talen van de communautaire groep]**: gebruikt u het keuzemenu om de beschikbare taal of talen van groepen in de gemeenschap te selecteren. In het menu worden alle talen weergegeven waarin de bovenliggende communitysite is gemaakt. Gebruikers kunnen in deze ene stap uit deze talen kiezen om groepen te maken in meerdere landinstellingen. De zelfde groep wordt gecreeerd in veelvoudige gespecificeerde talen in de console van Groepen van de respectieve communautaire plaatsen.
   * **[!UICONTROL Naam]** communautaire groep: kunst.
   * **[!UICONTROL Sjabloon]**: keuzelijst selecteren `Reference Group.`
   * Selecteer **[!UICONTROL Volgende]**.

![Geneste groepen van gemeenschappen](assets/parent-to-nestedgroup.png)

Doorloop de andere deelvensters met deze instellingen:

* **[!UICONTROL Ontwerp]**

   * Het ontwerp wijzigen of het ontwerp van de standaard bovenliggende site toestaan.
   * Selecteer **[!UICONTROL Volgende]**.

* **[!UICONTROL Instellingen]**

   * **[!UICONTROL Moderatie]**

      * Leeg laten (overerven van bovenliggende site).
   * **[!UICONTROL Lidmaatschap]**

      * Standaard gebruiken `Optional Membership.`

      * **[!UICONTROL Miniatuur]**
         * `optional.*`
      * **[!UICONTROL Selecteer Volgende]**.



* Selecteer **[!UICONTROL Maken]**.

### Groepen nesten binnen tekengroep {#nesting-groups-within-arts-group}

De `groups` map bevat nu twee groepen (de pagina vernieuwen).

![Groepen nesten](assets/create-community-group.png)

#### Groep publiceren {#publish-group}

Voordat u groepen maakt die in de `arts` groep zijn genest, houdt u de muisaanwijzer boven de `arts` kaart en selecteert u het publicatiepictogram om deze te publiceren.

![chlimage_1-93](assets/chlimage_1-93.png)

Wacht op bevestiging dat de groep is gepubliceerd.

![chlimage_1-94](assets/chlimage_1-94.png)

De `arts` groep moet ook een `groups` map bevatten, maar een map die leeg is en waarin nieuwe groepen kunnen worden gemaakt. Navigeer naar de map met kunstgroepen en maak drie geneste groepen, elk met een andere lidmaatschapsinstelling:

1. **[!UICONTROL Zichtbaar]**

   * Titel: `Visual Arts`
   * Naam: `visual`
   * Sjabloonmodel: `Reference Group`
   * Lidmaatschap: selecteer `Optional Membership`, een openbare groep, open aan alle leden.

1. **[!UICONTROL Controleur]**

   * Titel: `Auditory Arts`
   * Naam: `auditory`
   * Sjabloonmodel: `Reference Group`
   * Lidmaatschap: Selecteer `Required Membership`, een open groep, beschikbaar voor leden om zich bij te voegen.

1. **[!UICONTROL Historie]**

   * Titel: `Art History`
   * Naam: `history`
   * Sjabloonmodel: `Reference Group`
   * Lidmaatschap: select `Restricted Membership`, een geheime groep, alleen zichtbaar voor uitgenodigde leden. U kunt bijvoorbeeld een [demogebruiker](/help/communities/tutorials.md#demo-users) uitnodigen `emily.andrews@mailinator.com`.

Vernieuw de pagina om alle drie geneste groepen (subgemeenschappen) weer te geven.

Om aan de genestelde groepen van de console van Plaatsen van Gemeenschappen te navigeren:

* Selecteer een **[!UICONTROL toegewijde map]**
* Zelfstudiekaart **[!UICONTROL Aan de slag selecteren]**
* Map **[!UICONTROL Groepen]** selecteren
* Tekenkaart **[!UICONTROL selecteren]**
* Map **[!UICONTROL Groepen]** selecteren

![chlimage_1-95](assets/chlimage_1-95.png)

## Groepen publiceren {#publishing-groups}

![chlimage_1-96](assets/chlimage_1-96.png)

Na publicatie van de hoofdsite van de community:

* Elke groep afzonderlijk publiceren:

   * Wachtend op bevestiging dat de groep is gepubliceerd.

* Publiceer bovenliggende groep voordat u groepen publiceert die zijn genest in:

   * Alle groepen moeten van boven naar beneden worden gepubliceerd.

![chlimage_1-97](assets/chlimage_1-97.png)

## Ervaring met publiceren {#experience-on-publish}

U kunt de verschillende groepen ervaren wanneer u zich aanmeldt, bijvoorbeeld met de [demo-gebruikers](/help/communities/tutorials.md#demo-users) die worden gebruikt voor:

* Groepslid illustratie/geschiedenis: emily.andrews@mailinator.com/password
   * De beperkte (geheime) groep, kunst/geschiedenis, is zichtbaar:
   * Kan optionele (openbare) groepen zien.
   * Kan beperkte (open) groepen samenvoegen.

* Groepsbeheer: aaron.mcdonald@mailinator.com/password

   * Kan optionele (openbare) groepen zien.
   * Kan beperkte (open) groepen samenvoegen.
   * Kan beperkte (geheime) groepen niet zien.

Toegang tot de [leden en de Groepen van Gemeenschappen consoles](/help/communities/members.md) op auteur om andere gebruikers aan diverse lidgroepen toe te voegen die aan de communautaire groepen beantwoorden.

