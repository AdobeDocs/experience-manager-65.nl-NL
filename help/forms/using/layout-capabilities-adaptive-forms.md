---
title: Indelingsmogelijkheden van adaptieve formulieren
seo-title: Indelingsmogelijkheden van adaptieve formulieren
description: De indeling en vormgeving van adaptieve formulieren op verschillende apparaten worden bepaald door de indelingsinstellingen. Begrijp de verschillende lay-outs en hoe te om hen toe te passen.
seo-description: De indeling en vormgeving van adaptieve formulieren op verschillende apparaten worden bepaald door de indelingsinstellingen. Begrijp de verschillende lay-outs en hoe te om hen toe te passen.
uuid: 79022ac2-1aa3-47c5-b094-cbe83334ea62
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: author
discoiquuid: 9459c414-eac9-4bd9-a773-cceaeb736c56
docset: aem65
translation-type: tm+mt
source-git-commit: 1343cc33a1e1ce26c0770a3b49317e82353497ab
workflow-type: tm+mt
source-wordcount: '1155'
ht-degree: 0%

---


# Indelingsmogelijkheden van adaptieve formulieren{#layout-capabilities-of-adaptive-forms}

Met Adobe Experience Manager (AEM) kunt u gebruiksvriendelijke adaptieve formulieren maken die eindgebruikers een dynamische ervaring bieden. De formulierindeling bepaalt hoe items of componenten in een adaptief formulier worden weergegeven.

## Vereiste kennis {#prerequisite-knowledge}

Lees de volgende artikelen voor meer informatie over adaptieve formulieren voordat u meer leert over de verschillende lay-outmogelijkheden van adaptieve formulieren.

[Inleiding tot AEM Forms](../../forms/using/introduction-aem-forms.md)

[Inleiding tot ontwerpformulieren](../../forms/using/introduction-forms-authoring.md)

## Typen lay-outs {#types-of-layouts}

Een adaptief formulier biedt u de volgende typen indelingen:

**Layout** van deelvenster bepaalt hoe items of componenten in een deelvenster op een apparaat worden weergegeven.

**Mobiele indeling** bepaalt de navigatie van een formulier op een mobiel apparaat. Als de apparaatbreedte 768 pixels of meer is, wordt de lay-out beschouwd als een mobiele lay-out en geoptimaliseerd voor een mobiel apparaat.

**Met Werkbalkindeling** bepaalt u de plaatsing van de knoppen Handeling op de werkbalk of op de werkbalk van het deelvenster in een formulier.

Al deze paneellay-outs worden bepaald in de volgende plaats:

`/libs/fd/af/layouts`.

>[!NOTE]
>
>Als u de indeling van een adaptief formulier wilt wijzigen, gebruikt u de ontwerpmodus in AEM.

![Locatie van lay-outs in CRX-opslagplaats](assets/layouts_location_in_crx.png)

## Deelvensterlay-out {#panel-layout}

Een auteur van een formulier kan een indeling koppelen aan elk deelvenster van een adaptief formulier, inclusief het hoofddeelvenster.

De schermindelingen van het deelvenster zijn beschikbaar op de `/libs/fd/af/layouts/panel` locatie.

![Lijst met deelvensterindelingen voor het hoofdvenster van een adaptief formulier](assets/layouts.png)

Lijst met deelvensterindelingen in adaptieve formulieren

### Responsief - alles op één pagina zonder navigatie {#responsive-everything-on-one-page-without-navigation-br}

Met deze deelvensterlay-out maakt u een responsieve lay-out die zich aanpast aan de schermgrootte van uw apparaat zonder dat u hiervoor speciale navigatie nodig hebt.

Met deze lay-out kunt u meerdere **[!UICONTROL Panel adaptive form]** componenten achter elkaar in het deelvenster plaatsen.

![Een formulier met een responsieve indeling zoals wordt weergegeven op een klein scherm](assets/responsive_layout_seen_on_small_screen.png)

Een formulier met een responsieve indeling zoals wordt weergegeven op een klein scherm

![Een formulier met een responsieve indeling zoals weergegeven op een groot scherm](assets/responsive_layout_seen_on_large_screen.png)

Een formulier met een responsieve indeling zoals weergegeven op een groot scherm

### Wizard - Een formulier dat uit meerdere stappen bestaat en één stap tegelijk weergeeft {#wizard-a-multi-step-form-showing-one-step-at-a-time}

Met deze deelvensterindeling kunt u navigatie met instructies in een formulier bieden. Gebruik deze indeling bijvoorbeeld wanneer u verplichte gegevens in een formulier wilt vastleggen en gebruikers stapsgewijs wilt begeleiden.

Gebruik de `Panel adaptive form` component om stapsgewijze navigatie in een deelvenster te bieden. Als u deze lay-out gebruikt, gaat een gebruiker pas naar de volgende stap nadat de huidige stap is voltooid

```javascript
window.guideBridge.validate([], this.panel.navigationContext.currentItem.somExpression)
```

![De voltooiingsuitdrukking van de stap in de lay-out van de Tovenaar voor een multi-step vorm](assets/layout-sidebar.png)

De voltooiingsuitdrukking van de stap in de lay-out van de Tovenaar voor een multi-step vorm

![Een formulier met wizardindeling](assets/wizard-layout.png)

Een formulier met wizard

### Layout voor accordeonontwerp {#layout-for-accordion-design}

Met deze lay-out kunt u de `Panel adaptive form` component in een deelvenster plaatsen met accordeonstijlnavigatie. Met deze indeling kunt u ook herhaalbare deelvensters maken. Met herhalende deelvensters kunt u, indien nodig, deelvensters dynamisch toevoegen of verwijderen. U kunt het minimum en het maximum aantal keren bepalen dat een paneel herhaalt. De titel van het deelvenster kan ook dynamisch worden bepaald op basis van de informatie in de deelvensteritems.

De summiere uitdrukking kan worden gebruikt om de waarden te tonen die door de eindgebruiker in de titel van het geminimaliseerde paneel worden verstrekt.

![Herhaalbare deelvensters met de indeling Accordeon in adaptieve formulieren](assets/repeatable_panels_using_accordion_layout.png)

Herhaalbare deelvensters die zijn gemaakt met de accordeonindeling

### Lay-out met tabs - links worden tabs weergegeven {#tabbed-layout-tabs-appear-on-the-left}

Met deze indeling kunt u de `Panel adaptive form` component in een deelvenster met tabnavigatie plaatsen. De tabbladen worden links van de inhoud van het deelvenster geplaatst.

![In de lay-out Tabbed, verschijnen de lusjes op de linkerzijde](assets/tabbed_layout_left.png)

Tabs die links van een deelvenster worden weergegeven

### Lay-out met tabs - tabs worden boven aan het scherm weergegeven {#tabbed-layout-tabs-appear-on-the-top}

Met deze indeling kunt u de `Panel adaptive form` component in een deelvenster met tabnavigatie plaatsen. De tabbladen worden boven op de inhoud van het deelvenster geplaatst.

![Lay-out met tabs in adaptieve formulieren met bovenaan tabs](assets/tabbed_layout_top.png)

Tabs die boven in een deelvenster worden weergegeven

## Mobiele lay-outs {#mobile-layouts}

Mobiele lay-outs maken gebruikersvriendelijke navigatie op mobiele apparaten met relatief kleinere schermen mogelijk. Mobiele lay-outs maken gebruik van tabbladen of wizards voor formuliernavigatie. Als u een mobiele indeling toepast, beschikt u over één indeling voor het hele formulier.

Deze indeling bepaalt de navigatie met behulp van een navigatiebalk en een navigatiemenu. Op de navigatiebalk wordt het pictogram **&lt;** en **>** weergegeven om **volgende** en **vorige** navigatiestappen in het formulier aan te geven.

De mobiele lay-outs zijn beschikbaar op `/libs/fd/af/layouts/mobile/` locatie. De volgende mobiele lay-outs zijn standaard beschikbaar in adaptieve formulieren.

![Lijst met mobiele indelingen in adaptieve formulieren](assets/mobile-navigation.png)

Lijst met mobiele indelingen in adaptieve formulieren

Als u een mobiele indeling gebruikt, kunt u het formuliermenu gebruiken om toegang te krijgen tot verschillende formulierdeelvensters. U kunt hiertoe tikken op ![het pictogram em6forms_form_menu](assets/aem6forms_form_menu.png) .

### Indeling met titels van deelvensters in de formulierkoptekst {#layout-with-panel-titles-in-the-form-header}

In deze indeling worden, zoals in de naam wordt gesuggereerd, deelvenstertitels weergegeven, samen met het navigatiemenu en de navigatiebalk. Deze indeling biedt ook de pictogrammen Volgende en Vorige voor navigatie.

![Mobiele lay-outs met titels van deelvensters in de formulierkoppen](assets/mobile_layout_with.png)

Mobiele lay-outs met titels van deelvensters in de formulierkoppen

### Indeling zonder deelvenstertitels in de koptekst van het formulier {#layout-without-panel-titles-in-the-form-header}

In deze indeling worden, zoals in de naam wordt gesuggereerd, alleen het navigatiemenu en de navigatiebalk zonder venstertitels weergegeven. Deze indeling biedt ook de pictogrammen Volgende en Vorige voor navigatie.

![Mobiele lay-outs zonder titels in de formulierkoppen](assets/mobile_layout_without.png)

Mobiele lay-outs zonder titels in de formulierkoppen

## Werkbalklay-outs {#toolbar-layouts}

Met een werkbalkindeling bepaalt u de positie en weergave van alle actieknoppen die u toevoegt aan uw aangepaste formulieren. De indeling kan op formulierniveau of deelvensterniveau worden toegevoegd.

![Een lijst met werkbalkindelingen in aangepaste formulieren om de indeling van knoppen te bepalen](assets/toolbar-layouts.png)

Een lijst met werkbalkindelingen in adaptieve formulieren

De schermindelingen van de werkbalk zijn beschikbaar op de `/libs/fd/af/layouts/toolbar` locatie. Aangepaste formulieren bieden standaard de volgende werkbalkopmaak.

### Standaardindeling voor werkbalk {#default-layout-for-toolbar}

Deze indeling wordt geselecteerd als de standaardindeling wanneer u actieknoppen toevoegt in een adaptief formulier. Als u deze lay-out selecteert, wordt dezelfde lay-out weergegeven voor zowel mobiele als desktopapparaten.

U kunt ook meerdere werkbalken toevoegen die actieknoppen bevatten die zijn geconfigureerd met deze indeling. Een actieknop is gekoppeld aan een formulierbesturingselement. U kunt de werkbalken configureren voor of na een deelvenster.

![Standaardweergave voor werkbalk](assets/toolbar_layout_default.png)

Standaardweergave voor werkbalk

### Vaste mobiele lay-out voor werkbalk {#mobile-fixed-layout-for-toolbar}

Selecteer deze lay-out om alternatieve lay-outs voor desktop- en mobiele apparaten te bieden.

Voor de computerlay-out kunt u knoppen Handeling toevoegen met behulp van bepaalde labels. Met deze indeling kan slechts één werkbalk worden geconfigureerd. Als er meerdere werkbalken zijn geconfigureerd met deze lay-out, is er een overlapping voor mobiele apparaten en is er slechts één werkbalk zichtbaar. U kunt bijvoorbeeld een werkbalk boven of onder aan het formulier of deelvensters na of voor het formulier weergeven.

Voor de mobiele lay-out kunt u actieknoppen toevoegen met behulp van pictogrammen.

![Vaste mobiele lay-out voor werkbalk](assets/toolbar_layout_mobile_fixed.png)

Vaste mobiele lay-out voor werkbalk

