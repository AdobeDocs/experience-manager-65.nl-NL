---
title: Projecten beheren
description: De projecten laten u uw project organiseren door middelen in één entiteit te groeperen die in de console van Projecten kan worden betreden en worden geleid
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: projects
content-type: reference
exl-id: 62586c8e-dab4-4be9-a44a-2c072effe3c0
solution: Experience Manager, Experience Manager Sites
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '965'
ht-degree: 0%

---


# Projecten beheren {#managing-projects}

In de **Projecten** console, hebt u toegang tot en beheert uw projecten.

![De projectenconsole](assets/projects-console.png)

Gebruikend de console, kunt u een project tot stand brengen, middelen met uw project associëren, en ook een project of middelverbindingen schrappen.

## Toegangsvereisten {#access-requirements}

Projecteert een standaard AEM en vereist geen extra opstelling.

Nochtans voor gebruikers in projecten om andere gebruikers/groepen te zien terwijl het gebruiken van Projecten zoals wanneer het creëren van projecten, het creëren van taken/werkschema&#39;s of het bekijken van en het leiden van het team, moeten die gebruikers lees toegang hebben op `/home/users` en `/home/groups`.

De eenvoudigste manier om dit te doen is de **projecten-gebruikers** groep lees toegang tot `/home/users` en `/home/groups`.

## Een project maken {#creating-a-project}

Voer de volgende stappen uit om een project te maken.

1. In de **Projecten** console, klik **Maken** om de **Project maken** wizard.
1. Selecteer een sjabloon en klik op **Volgende**. U kunt meer over de standaardprojectmalplaatjes leren [hier.](/help/sites-authoring/projects.md#project-templates)

   ![Wizard Project maken](assets/create-project-wizard.png)

1. Definieer de **Titel** en **Beschrijving** en voeg een **Miniatuur** afbeelding, indien nodig. U kunt ook gebruikers toevoegen of verwijderen en tot welke groep zij behoren.

   ![stap Eigenschappen van wizard](assets/create-project-wizard-properties.png)

1. Klikken **Maken**. De bevestiging vraagt of wilt u uw nieuw project openen of aan de console terugkeren.

De procedure voor het creëren van een project is het zelfde voor alle projectmalplaatjes. Het verschil tussen de soorten projecten heeft betrekking op de beschikbare [gebruikersrollen](/help/sites-authoring/projects.md) en [workflows.](/help/sites-authoring/projects-with-workflows.md)

### Bronnen koppelen aan uw project {#associating-resources-with-your-project}

Met projecten kunt u resources groeperen in één entiteit om deze als geheel te beheren. Daarom moet u middelen aan uw project associëren. Deze bronnen worden als **Tegels**. De typen bronnen die u kunt toevoegen, worden beschreven in [Projectblokken](/help/sites-authoring/projects.md#project-tiles).

Om middelen met uw project te associëren:

1. Open uw project vanuit de **Projecten** console.
1. Klikken **Tegel toevoegen** en selecteer de tegel die u aan uw project wilt koppelen. U kunt meerdere typen tegels selecteren.

   ![Tegel toevoegen](assets/project-add-tile.png)

1. Klikken **Maken**. Uw bron is gekoppeld aan uw project en vanaf nu hebt u toegang tot deze bron vanuit uw project.

### Items toevoegen aan een tegel {#adding-items-to-a-tile}

In sommige tegels wilt u mogelijk meerdere items toevoegen. U kunt bijvoorbeeld meer dan één workflow tegelijk uitvoeren of meer dan één ervaring.

Items toevoegen aan een tegel:

1. In **Projecten**, navigeert u naar het project en klikt u op het pictogram van de neerwaartse chevron rechtsboven in de tegel waaraan u een item wilt toevoegen en selecteert u de gewenste optie.

   * De optie is afhankelijk van het type tegel. Het kan bijvoorbeeld **Taak maken** voor de **Taken** tegel of **Workflow starten** voor de **Workflows** tegel.

   ![Tile chevron](assets/project-tile-create-task.png)

1. Voeg het item aan de tegel toe zoals u dat zou doen bij het maken van een tegel. Projectelementen worden beschreven [hier.](/help/sites-authoring/projects.md#project-tiles)

## Projectinformatie weergeven {#viewing-project-info}

Het hoofddoel van de projecten is de bijbehorende informatie op één plaats te groeperen om deze toegankelijker en actiever te maken. U kunt deze gegevens op verschillende manieren openen.

### Een tegel openen {#opening-a-tile}

Mogelijk wilt u zien welke items zijn opgenomen in een huidige tegel, of wilt u items wijzigen of verwijderen in de tegel.

Een tegel openen zodat u items kunt weergeven of wijzigen:

1. Klik op het pictogram met ovalen rechtsonder in de tegel.

   ![Taken](assets/project-tile-tasks.png)

1. AEM opent de console voor de types van punten verbonden aan de tegel en filters die op het geselecteerde project worden gebaseerd.

   ![Projecttaken](assets/project-tasks.png)

### Een projecttijdlijn weergeven {#viewing-a-project-timeline}

De projecttijdlijn biedt informatie over wanneer de elementen in het project het laatst zijn gebruikt. Voer de volgende stappen uit om de projecttijdlijn weer te geven.

1. In de **Projecten** console, klik **Tijdlijn** in de spoorkiezer in de linkerbovenhoek van de console.
   ![Tijdlijnmodus selecteren](assets/projects-timeline-rail.png)
2. In de console selecteer het project waarvoor u wenst om zijn chronologie te bekijken.
   ![Tijdlijnweergave van project](assets/project-timeline-view.png)

Elementen worden weergegeven in de spoorstaaf. Gebruik de spoorkiezer om terug te keren naar de normale weergave wanneer u klaar bent.

### Inactieve projecten weergeven {#viewing-active-inactive-projects}

Tussen uw actieve en [inactieve projecten;](#making-projects-inactive-or-active) in de **Projecten** console, klik **Actieve projecten in-/uitschakelen** in de werkbalk.

![Pictogram Actieve projecten in-/uitschakelen](assets/projects-toggle-active.png)

Door gebrek toont de console actieve projecten. Klik op de knop **Actieve projecten in-/uitschakelen** pictogram één keer om naar het bekijken van inactieve projecten over te schakelen. Klik opnieuw het om op actieve projecten terug te schakelen.

## Projecten organiseren {#organizing-projects}

Er zijn verschillende opties beschikbaar waarmee u uw projecten kunt ordenen om de **Projecten** beheerbaar op de console.

### Projectmappen {#project-folders}

U kunt mappen maken in het dialoogvenster **Projecten** console om gelijkaardige projecten te groeperen en te organiseren.

1. In de **Projecten** consoleklik **Maken** en vervolgens **Map maken**.

   ![Map maken](assets/project-create-folder.png)

1. Geef uw map een titel en klik op **Maken**.

1. De map wordt toegevoegd aan de console.

U kunt nu projecten in de map maken. U kunt meerdere mappen maken en ook mappen nesten.

### Projecten activeren {#making-projects-inactive-or-active}

U kunt een project willen inactief merken als het wordt voltooid maar u wilt nog de informatie over het project houden. [Inactieve projecten worden nu weergegeven](#viewing-active-inactive-projects) standaard in de **Projecten** console.

Voer de volgende stappen uit om een project inactief te maken.

1. Open de **Projecteigenschappen** venster van het project.
   * U kunt dit van de console doen door het project of van binnen het project via te selecteren **Projectinfo** tegel.
1. In de **Projecteigenschappen** venster, wijzigen **Projectstatus** schuifregelaar vanaf **Actief** tot **Inactief**.

   ![Projectstatuskiezer in eigenschappenvenster](assets/project-status.png)

1. Klikken **Opslaan en sluiten** om uw wijzigingen op te slaan.

### Projecten verwijderen {#deleting-a-project}

Voer de volgende stappen uit om een project te verwijderen.

1. Ga naar het hoogste niveau van **Projecten** console.
1. Het selecteren van uw project in de console.
1. Klikken **Verwijderen** in de werkbalk.
1. AEM kan bijbehorende projectgegevens verwijderen/wijzigen bij het verwijderen van een project. Selecteer de opties die u nodig hebt in het dialoogvenster **Project verwijderen** in.
   * Projectgroepen en -rollen verwijderen
   * Map Projectelementen verwijderen
   * Projectworkflows beëindigen

   ![Opties voor het verwijderen van projecten](assets/project-delete-options.png)
1. Klikken **Verwijderen** om het project met de geselecteerde opties te schrappen.

Meer informatie over groepen die automatisch door projecten worden gecreeerd zie [Automatische groep maken](/help/sites-authoring/projects.md#auto-group-creation) voor meer informatie.
