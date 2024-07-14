---
title: Extensie AEM
description: Leer hoe u de Adobe Experience Manager-extensie voor haakjes gebruikt.
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: development-tools
content-type: reference
exl-id: 829d8256-b415-4a44-a353-455ac16950f3
solution: Experience Manager, Experience Manager Sites
feature: Developing,Developer Tools
role: Developer
source-git-commit: 305227eff3c0d6414a5ae74bcf3a74309dccdd13
workflow-type: tm+mt
source-wordcount: '913'
ht-degree: 0%

---

# Extensie AEM{#aem-brackets-extension}

## Overzicht {#overview}

De AEM Uitbreiding van de Brackets verstrekt een vlotte werkstroom om AEM componenten en cliëntbibliotheken uit te geven, en gebruikt de macht van de ](https://brackets.io/) coderedacteur 0} Brackets {, die toegang van binnen de coderedacteur aan de dossiers en de lagen van Photoshop geeft. [ De eenvoudige synchronisatie die wordt geboden door de extensie (geen Maven of File Vault vereist) verhoogt de efficiëntie van de ontwikkelaar en helpt ontwikkelaars met beperkte AEM kennis ook om aan projecten deel te nemen. Deze uitbreiding verleent ook wat steun voor de [ Taal van het Malplaatje van de HTML (HTML) ](https://experienceleague.adobe.com/docs/experience-manager-htl/content/overview.html), die de ingewikkeldheid van JSP wegneemt om componentenontwikkeling gemakkelijker en veiliger te maken.

![ chlimage_1-53 ](assets/chlimage_1-53a.png)

### Functies {#features}

De hoofdkenmerken van de extensie AEM Brackets zijn:

* Geautomatiseerde synchronisatie van gewijzigde bestanden naar de AEM-ontwikkelingsinstantie.
* Handmatige tweerichtingssynchronisatie van bestanden en mappen.
* Volledige tevreden-pakket synchronisatie van het project.
* HTML-codevoltooiing voor expressies en `data-sly-*` blokinstructies.

Bovendien zijn er veel handige functies voor AEM ontwikkelaars van lettertypen:

* Photoshop-bestandsondersteuning voor het ophalen van gegevens uit een PSD-bestand, zoals lagen, metingen, kleuren, lettertypen, tekst, enzovoort.
* Coderingstips van de PSD om deze geëxtraheerde informatie in de code eenvoudig te hergebruiken.
* Ondersteuning voor CSS-preprocessor, zoals LESS en SCSS.
* En honderden extra extensies die meer specifieke behoeften dekken.

## Installatie {#installation}

### Haakjes {#brackets}

De extensie AEM Brackets ondersteunt versie 1.0 of hoger.

Download de recentste versie van Brackets van [ brackets.io ](https://brackets.io/).

### De extensie {#the-extension}

Ga als volgt te werk om de extensie te installeren:

1. Open haakjes. In menu **Dossier**, uitgezochte **Extension Manager...**
1. Ga **AEM** in de onderzoeksbar in en zoek **AEM de Uitbreiding van de Brekken**.

   ![ chlimage_1-54 ](assets/chlimage_1-54a.png)

1. Klik **installeren**.
1. Sluit het dialoogvenster en de Extension Manager nadat de installatie is voltooid.

## Aan de slag {#getting-started}

### Het content-package project {#the-content-package-project}

Nadat de extensie is geïnstalleerd, kunt u beginnen met het ontwikkelen van AEM componenten door een inhoudspakketmap te openen vanuit uw bestandssysteem met haakjes.

Het project moet ten minste het volgende bevatten:

1. a `jcr_root` map (bijvoorbeeld `myproject/jcr_root` )

1. a `filter.xml` dossier (bijvoorbeeld, `myproject/META-INF/vault/filter.xml`); voor meer details over de structuur van het `filter.xml` dossier zie de [ definitie van de Filter van Workspace ](https://jackrabbit.apache.org/filevault/filter.html).

In het 1} menu van het Dossier van de Brackets {**, kies** Open Omslag... **en kies of de `jcr_root` omslag, of de ouderprojectomslag.**

>[!NOTE]
>
>Als u niet van uw eigen een project met een inhoud-pakket hebt, kunt u het [ Voorbeeld van HTML proberen TodoMVC ](https://github.com/Adobe-Marketing-Cloud/aem-sightly-sample-todomvc). Voor GitHub, klik **ZIP van de Download**, haalt de dossiers plaatselijk, en zoals hierboven geïnstrueerd, open de `jcr_root` omslag in Brackets. Dan volg de stappen hieronder aan opstelling de **Montages van het Project**, en upload definitief het volledige pakket aan uw AEM ontwikkelingsinstantie door een **Pakket van de Inhoud van de Uitvoer** zoals verder onderwezen in de Volledige inhoud-Pakket sectie van de Synchronisatie te doen.
>
>Na deze stappen, zou u tot `/content/todo.html` URL op uw AEM ontwikkelingsinstantie moeten kunnen toegang hebben en u kunt wijzigingen aan de code in Brackets beginnen en zien hoe, na te doen verfrist zich in Webbrowser, de veranderingen onmiddellijk aan de AEM server werden gesynchroniseerd.

### Projectinstellingen {#project-settings}

Als u de inhoud wilt synchroniseren van en naar een AEM-ontwikkelingsinstantie, moet u de projectinstellingen definiëren. Dit kan worden gedaan door naar het **AEM** menu te gaan en **Montages van het Project te kiezen..**

![ chlimage_1-55 ](assets/chlimage_1-55a.png)

Met de projectinstellingen kunt u het volgende definiëren:

1. De server-URL (bijvoorbeeld `http://localhost:4502`)
1. Of servers worden getolereerd die geen geldig HTTPS-certificaat hebben (niet ingeschakeld houden, tenzij vereist)
1. De gebruikersnaam die wordt gebruikt voor het synchroniseren van inhoud (bijvoorbeeld `admin`)
1. Het wachtwoord van de gebruiker (bijvoorbeeld `admin` )

## Inhoud synchroniseren {#synchronizing-content}

De extensie AEM Brackets biedt de volgende typen inhoudsynchronisatie voor bestanden en mappen die zijn toegestaan door de filterregels die zijn gedefinieerd in `filter.xml` :

### Geautomatiseerde synchronisatie van gewijzigde bestanden {#automated-synchronization-of-changed-files}

Hiermee worden wijzigingen alleen gesynchroniseerd van haakjes naar de AEM-instantie, maar nooit andersom.

### Handmatige tweerichtingssynchronisatie {#manual-bidirectional-synchronization}

In de Ontdekkingsreiziger van het Project, open het contextafhankelijke menu door op om het even welk dossier of omslag met de rechtermuisknop te klikken, en de **Uitvoer aan Server** of **Invoer van Server** opties kan worden betreden.

![ chlimage_1-56 ](assets/chlimage_1-56a.png)

>[!NOTE]
>
>Als de geselecteerde ingang buiten de `jcr_root` omslag is, wordt de **Uitvoer naar Server** en **Invoer van Server** contextafhankelijke menuingangen onbruikbaar gemaakt.

### Volledige synchronisatie van inhoudspakketten {#full-content-package-synchronization}

In het **AEM** menu, laat het **Pakket van de Inhoud van de Uitvoer** of **de opties van het Pakket van de Inhoud van de Invoer** u het volledige project met de server synchroniseren.

![ chlimage_1-57 ](assets/chlimage_1-57a.png)

### Synchronisatiestatus {#synchronization-status}

De extensie AEM Brackets heeft een waarschuwingspictogram op de werkbalk rechts van het venster Brackets, waarmee de status van de laatste synchronisatie wordt aangegeven:

* groen - alle bestanden zijn gesynchroniseerd
* blauw - een synchronisatiebewerking wordt uitgevoerd
* geel - sommige bestanden zijn niet gesynchroniseerd
* rood - geen van de bestanden is gesynchroniseerd

Wanneer u op het meldingspictogram klikt, wordt het dialoogvenster Synchronisatie-statusrapport geopend met een lijst van alle status voor elk gesynchroniseerd bestand.

![ chlimage_1-58 ](assets/chlimage_1-58a.png)

>[!NOTE]
>
>Alleen inhoud die is gemarkeerd als opgenomen in de filterregels van `filter.xml` , wordt gesynchroniseerd, ongeacht de gebruikte synchronisatiemethode.
>
>Daarnaast worden `.vltignore` -bestanden ondersteund voor het uitsluiten van inhoud van en naar de opslagplaats.

## HTML-code bewerken {#editing-htl-code}

De extensie AEM Brackets beschikt ook over enkele automatische aantekeningen waarmee het schrijven van HTML-kenmerken en -expressies wordt vergemakkelijkt.

### Kenmerk automatisch voltooid {#attribute-auto-completion}

1. Typ `sly` in een HTML-kenmerk. Het kenmerk wordt automatisch aangevuld naar `data-sly-` .
1. Selecteer het HTML-kenmerk in de vervolgkeuzelijst.

### Uitdrukking automatisch voltooid {#expression-auto-completion}

In een expressie `${}` worden veelvoorkomende variabelenamen automatisch aangevuld.

## Meer informatie {#more-information}

De AEM Uitbreiding van de Brackets is een open-bronproject, dat op GitHub door de [ wordt ontvangen Adobe Marketing Cloud ](https://github.com/Adobe-Marketing-Cloud) organisatie, onder de Vergunning Apache, versie 2.0:

* Opslagplaats van de code: [ https://github.com/Adobe-Marketing-Cloud/aem-sightly-brackets-extension](https://github.com/Adobe-Marketing-Cloud/aem-sightly-brackets-extension)
* Apache-licentie, versie 2.0: [ https://www.apache.org/licenses/LICENSE-2.0.html](https://www.apache.org/licenses/LICENSE-2.0.html)

De de coderedacteur van Brackets is ook een open-bronproject, dat op GitHub door de [ Adobe Systems Incorporated ](https://github.com/adobe) organisatie wordt ontvangen:

* Opslagplaats van de code: [ https://github.com/adobe/brackets](https://github.com/adobe/brackets)

Voel je vrij om bij te dragen!
