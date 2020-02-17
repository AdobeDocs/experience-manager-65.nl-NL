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
source-git-commit: 27a054cc5d502d95c664c3b414d0066c6c120b65

---


# Geneste groepen ontwerpen{#authoring-nested-groups}

## Groepen maken op auteur {#creating-groups-on-author}

Op een instantie van AEM-auteur, van globale navigatie:

* Selecteer** Gemeenschappen, sites.**
* Selecteer **Inlogmap** om deze te openen.
* Selecteer de kaart voor de **Engelstalige website Aan de slag voor zelfstudie** .

   * Selecteer de kaartafbeelding.
   * Selecteer *geen* pictogram.

Het resultaat moet de console [van](/help/communities/groups.md)Groepen bereiken:

![chlimage_1-91](assets/chlimage_1-91.png)

De groepfunctie wordt weergegeven als een map waarin instanties van groepen worden gemaakt. Selecteer de map Groepen om deze te openen. De groep die bij publicatie wordt gemaakt, is zichtbaar.

![chlimage_1-92](assets/chlimage_1-92.png)

## Hoofdartgroep maken {#create-main-arts-group}

Deze groep kan worden gemaakt omdat de sitestructuur voor de verbinding een groepfunctie bevat. De configuratie van de functie in de `Reference Template` standaardinstellingen van de site staat de selectie van een ingeschakelde groepssjabloon toe. De sjabloon die voor deze nieuwe groep is gekozen, is dus de `Reference Group`.

Deze consoles zijn gelijkaardig aan de console van Plaatsen van Gemeenschappen.

* Selecteer Groep **maken.**
* **Template** voor communautaire groep:

   * Titel van communautaire groep: Kunst.
   * Omschrijving van de communautaire groep: Een bovenliggende groep voor verschillende kunstgroepen.
   * Hoofdmap van communautaire groep: Standaard *laten.*
   * Aanvullende beschikbare talen van de communautaire groep: gebruikt u het keuzemenu om de beschikbare taal of talen van groepen in de gemeenschap te selecteren. In het menu worden alle talen weergegeven waarin de bovenliggende communitysite is gemaakt. Gebruikers kunnen in deze ene stap uit deze talen kiezen om groepen te maken in meerdere landinstellingen. De zelfde groep wordt gecreeerd in veelvoudige gespecificeerde talen in de console van Groepen van de respectieve communautaire plaatsen.
   * Naam communautaire groep: kunst.
   * Sjabloon: vervolgkeuzelijst selecteren `Reference Group.`
   * `Select Next.`

![Geneste groepen van gemeenschappen](assets/parent-to-nestedgroup.png)

Doorloop de andere deelvensters met deze instellingen:

* **Ontwerp**

   * Het ontwerp wijzigen of het ontwerp van de standaard bovenliggende site toestaan.
   * Selecteer **Volgende.**

* **Instellingen**

   * **Moderatie**

      * leeg laten (overerven van bovenliggende site).
   * **Lidmaatschap**

      * default gebruiken `Optional Membership.`
   * **Miniatuur**

      * `*optional.*`
   * `Select Next.`




* Selecteer **Maken.**

### Groepen nesten binnen tekengroep {#nesting-groups-within-arts-group}

De `groups` map bevat nu twee groepen (de pagina vernieuwen).

![Groepen nesten](assets/create-community-group.png)

#### Groep publiceren {#publish-group}

Voordat u groepen maakt die in de `arts`groep zijn genest, houdt u de muisaanwijzer boven de `arts` kaart en selecteert u het publicatiepictogram om deze te publiceren.

![chlimage_1-93](assets/chlimage_1-93.png)

Wacht op bevestiging dat de groep is gepubliceerd.

![chlimage_1-94](assets/chlimage_1-94.png)

De `arts` groep moet ook een `groups` map bevatten, maar een map die leeg is en waarin nieuwe groepen kunnen worden gemaakt. Navigeer naar de map met kunstgroepen en maak drie geneste groepen, elk met een andere lidmaatschapsinstelling:

1. Zichtbaar

   * Titel: `Visual Arts`
   * Naam: `visual`
   * Sjabloonmodel: `Reference Group`
   * Lidmaatschap: selecteert `Optional Membership`een openbare groep die voor alle leden open is

1. Controleur

   * Titel: `Auditory Arts`
   * Naam: `auditory`
   * Sjabloonmodel: `Reference Group`
   * Lidmaatschap: selecteer `Required Membership`een open groep, beschikbaar voor leden om zich bij te voegen

1. Historie

   * Titel: `Art History`
   * Naam: `history`
   * Sjabloonmodel: `Reference Group`
   * Lidmaatschap: Selecteer `Restricted Membership`een geheime groep, die alleen zichtbaar is voor uitgenodigde leden als voorbeeld, nodig [demogebruiker](/help/communities/tutorials.md#demo-users) uit `emily.andrews@mailinator.com`

Vernieuw de pagina om alle drie geneste groepen (subgemeenschappen) weer te geven.

Om aan de genestelde groepen van de console van Plaatsen van Gemeenschappen te navigeren:

* Selecteer een map voor deelname
* Selecteer Aan de slag-zelfstudiekaart
* map Groepen selecteren
* illustratiekaart selecteren
* map Groepen selecteren

![chlimage_1-95](assets/chlimage_1-95.png)

## Groepen publiceren {#publishing-groups}

![chlimage_1-96](assets/chlimage_1-96.png)

Na publicatie van de hoofdsite van de community:

* elke groep afzonderlijk publiceren

   * wachten op bevestiging dat de groep is gepubliceerd

* bovenliggende groep publiceren voordat groepen worden gepubliceerd die zijn genest binnen

   * alle groepen moeten van boven naar beneden worden gepubliceerd.

![chlimage_1-97](assets/chlimage_1-97.png)

## Ervaring met publiceren {#experience-on-publish}

Het is mogelijk om de verschillende groepen te ervaren wanneer u zich aanmeldt, bijvoorbeeld met de [demo-gebruikers](/help/communities/tutorials.md#demo-users) die worden gebruikt voor

* Groepslid illustratie/geschiedenis: emily.andrews@mailinator.com/password

   * de beperkte (geheime) groep, kunst/geschiedenis, zichtbaar is
   * kan optionele (openbare) groepen zien
   * kan zich bij beperkte (open) groepen aansluiten

* Groepsbeheer: aaron.mcdonald@mailinator.com/password

   * kan optionele (openbare) groepen zien
   * kan zich bij beperkte (open) groepen aansluiten
   * kan geen beperkte (geheime) groepen zien

Toegang tot de [leden en de Groepen van Gemeenschappen consoles](/help/communities/members.md) op auteur om andere gebruikers aan diverse lidgroepen toe te voegen die aan de communautaire groepen beantwoorden.

