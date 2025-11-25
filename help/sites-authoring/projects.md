---
title: Projecten
description: Met projecten kunt u bronnen groeperen in één entiteit waarvan de gemeenschappelijke, gedeelde omgeving het eenvoudig maakt om uw projecten te beheren.
exl-id: 632c0608-2ab8-4a5b-8251-cd747535449b
solution: Experience Manager, Experience Manager Sites
feature: Authoring,Projects
role: User,Admin,Developer
source-git-commit: c77849740fab51377ce60aff5f611e0408dca728
workflow-type: tm+mt
source-wordcount: '1360'
ht-degree: 1%

---


# Projecten {#projects}

Met projecten kunt u resources groeperen in één entiteit. Een gemeenschappelijke, gedeelde omgeving maakt het gemakkelijk om uw projecten te beheren. De soorten middelen u met een project kunt associëren worden bedoeld in AEM als Tegels. De tegels kunnen project en teaminformatie, activa, werkschema&#39;s, en andere die soorten informatie omvatten, zoals in detail in [ wordt beschreven de Tegels van het Project.](#project-tiles)

Als gebruiker kunt u:

* Projecten maken en verwijderen
* Inhoud- en middelenmappen koppelen aan een project
* Inhoudskoppelingen uit project verwijderen

## Toegangsvereisten {#access-requirements}

Projecteert een standaard AEM-functie en vereist geen extra installatie.

Gebruikers in projecten kunnen echter andere gebruikers/groepen zien terwijl ze projecten gebruiken, zoals bij het maken van projecten, het maken van taken/workflows of het weergeven en beheren van het team, als deze gebruikers leestoegang moeten hebben op `/home/users` en `/home/groups` .

De gemakkelijkste manier om dit te doen is de **project-gebruikers** groep te geven leest toegang tot `/home/users` en `/home/groups`.

## Projectconsole {#projects-console}

In de projectenconsole hebt u toegang tot en beheert u uw projecten in AEM.

![ de Console van Projecten ](assets/screen-shot_2019-03-05at125110.png)

De console van Projecten is gelijkaardig aan andere consoles in AEM, staat verscheidene acties op individuele projecten toe en past uw mening van de projecten aan.

### Modus schakelen {#modes}

U kunt de spoorselecteur gebruiken om tussen consolemodi te veranderen.

![ de selecteur van het spoorspoor ](assets/projects-rail.png)

#### Alleen inhoud {#content-only}

Alleen inhoud is de standaardmodus bij het openen van de console. Het zal al uw projecten tonen.

#### Tijdlijn {#timeline}

In de tijdlijnweergave kunt u een afzonderlijk project selecteren en er activiteiten op weergeven. Gebruik de railkiezer of de sneltoets `alt+1` om naar deze weergave te gaan.

![ wijze van de Chronologie ](assets/project-timeline.png)

### Weergave schakelen {#views}

U kunt de weergavekiezer gebruiken om projecten als grote tegels weer te geven (de standaardinstelling), om ze als een lijst of op een kalender weer te geven.

![ Weergaven ](assets/projects-views.png)

### De weergave filteren {#filter}

U kunt het filter gebruiken om tussen alle projecten en slechts die van een knevel te voorzien die actief zijn.

![ Filter ](assets/projects-filter.png)

### Projecten selecteren en weergeven {#selecting}

Selecteer een project door de muis boven de projecttegel te plaatsen en op het vinkje te klikken.

U kunt de details van een project weergeven door erop te klikken en naar de details van het project te gaan.

### Nieuwe projecten maken {#creating}

Klik **creëren** om een nieuw project toe te voegen.

## Projectblokken {#project-tiles}

Projecten bestaan uit verschillende soorten informatie die u samen wilt beheren. Deze informatie wordt vertegenwoordigd door verschillende **Tegels**.

Aan uw project kunnen de volgende tegels zijn gekoppeld.

* [Assets](#assets)
* [Asset Collections](#asset-collections)
* [Ervaringen](#experiences)
* [Koppelingen](#links)
* [Projectinformatie](#project-info)
* [Team](#team)
* [Openingspagina&#39;s](#landing-pages)
* [E-mails](#emails)
* [Workflows](#workflows)
* [Lanceringen](#launches)
* [Taken](#tasks)

Klik op het vervolgkeuzemenu rechtsboven in een tegel om meer gegevens aan de tegel toe te voegen.

Klik op de ellipsknop rechtsonder in een tegel om de gegevens van de tegel te openen in de bijbehorende console.

### Assets {#assets}

In de **tegel van 0} Assets {, kunt u alle activa verzamelen die u voor een bepaald project gebruikt.**

![ de tegel van Assets ](assets/project-tile-assets.png)

U uploadt elementen rechtstreeks in de tegel.

### Asset Collections {#asset-collections}

Gelijkaardig aan activa, kunt u [ activa inzamelingen ](/help/assets/manage-collections.md) direct aan uw project toevoegen. U definieert verzamelingen in Assets.

![ de inzamelingspijl van Activa ](assets/project-tile-asset-collection.png)

Voeg een verzameling toe door op **Verzameling toevoegen** te klikken en de juiste verzameling in de lijst te selecteren.

### Ervaringen {#experiences}

De **tegel van de Ervaring 0} laat u een mobiele app, een website, of een publicatie aan het project toevoegen.**

![ de tegel van Ervaring ](assets/project-tile-experiences.png)

De pictogrammen geven aan welke ervaring wordt weergegeven.

* Website
* Mobiele toepassing

### Koppelingen {#links}

De **tegel van Verbindingen** laat u externe verbindingen met uw project associëren.

![ de tegel van Verbindingen ](assets/project-tile-links.png)

U kunt de koppeling een naam geven die gemakkelijk herkenbaar is en de miniatuur wijzigen.

### Projectinfo {#project-info}

De **tegel van de Informatie van het 0} Project {verstrekt algemene informatie over het project met inbegrip van een beschrijving, projectstatus (inactief of actief), een vervaldatum, en leden.** Bovendien kunt u een projectduimnagel toevoegen, die op de belangrijkste pagina van Projecten wordt getoond.

![ de informatietegel van het Project ](assets/project-tile-info.png)

### Vertaaltaak {#translation-job}

De **tegel van de Baan van 0} Vertaling {is waar u een vertaling begint en ook waar u het statuut van uw vertalingen ziet.**

![ de baantegel van de Vertaling ](assets/project-tile-translation.png)

Aan opstelling uw vertaling, zie het document [ Creërend Vertaalprojecten.](/help/assets/translation-projects.md)

### Team {#team}

In deze tegel, kunt u de leden van het projectteam specificeren. Wanneer het uitgeven, kunt u de naam van het teamlid ingaan en de gebruikersrol toewijzen.

![ de tegel van het Team ](assets/project-tile-team.png)

U kunt teamleden toevoegen en verwijderen uit het team. Bovendien kunt u de [ gebruikersrol ](#userroles) uitgeven die aan het teamlid wordt toegewezen.

### Openingspagina&#39;s {#landing-pages}

De **het Bestaan van Pagina&#39;s** tegel laat u om een nieuwe het landen pagina verzoeken.

![ het Bestaan paginatielijn ](assets/project-tile-landing.png)

Dit werkschema wordt beschreven in het document [ creeer een het Bestaan werkschema van de Pagina.](/help/sites-authoring/projects-with-workflows.md#request-landing-page-workflow)

### E-mails {#emails}

De **Emails** tegelhulp u verzoeken voor e-mail beheert. Het begint het **Verzoek voor E-mail** werkschema.

![ E-mailtegel ](assets/project-tile-email.png)

Meer informatie wordt beschreven in het [ E-mailwerkschema van het Verzoek.](/help/sites-authoring/projects-with-workflows.md#request-email-workflow)

### Workflows {#workflows}

U kunt workflows voor uw project starten. Als om het even welke werkschema&#39;s lopen, hun statusvertoningen in de **tegel van de Werkschema&#39;s**.

![ de tegel van Werkschema&#39;s ](assets/project-tile-workflows.png)

Afhankelijk van welk project u creeert zijn er verschillende beschikbare werkschema&#39;s.

Deze worden beschreven in [ Werkend met de Werkschema&#39;s van het Project.](/help/sites-authoring/projects-with-workflows.md)

### Lanceringen {#launches}

De **tegel van 0} Lanceringen {toont om het even welke lanceringen die met het werkschema van de Lancering van het a** Verzoek zijn gevraagd.[](/help/sites-authoring/projects-with-workflows.md)

![ de tegel van Lanceringen ](assets/project-tile-launches.png)

### Taken {#tasks}

Met Taken kunt u de status van projectgerelateerde taken, waaronder workflows, controleren. De taken worden behandeld in detail bij [ het Werken met Taken ](/help/sites-authoring/task-content.md).

![ de tegel van Taken ](assets/project-tile-tasks.png)

## Projectsjablonen {#project-templates}

Sjablonen dienen als basis voor het starten van uw project. AEM biedt deze standaardprojectsjablonen.

* **Project van Media** - dit is een project van de verwijzingssteekproef voor media-verwante activiteiten. Het omvat verscheidene media verwante projectrollen en omvat ook werkschema&#39;s met betrekking tot media inhoud.
* **[Project van de Opname van de Foto van het Product](/help/sites-authoring/managing-product-information.md)** - dit is een verwijzingssteekproef voor het beheren van eCommerce verwante productfotografie.
* **[Vertaal project](/help/sites-administering/translation.md)** - dit is een verwijzingssteekproef voor het beheren van vertaling verwante activiteiten. Het omvat basisrollen en omvat werkschema&#39;s voor het beheren van vertaling.
* **Eenvoudig Project** - dit is een verwijzingssteekproef voor om het even welke projecten die niet in andere categorieën passen. Deze omvat drie basisrollen en vier algemene AEM-workflows.

Gebaseerd op het malplaatje u selecteert, hebt u verschillende opties beschikbaar aan u binnen het project zoals de gebruikersrollen en de geleverde werkschema&#39;s.

## Gebruikersrollen in een project {#user-roles-in-a-project}

De verschillende gebruikersrollen worden bepaald in het projectmalplaatje en om twee primaire redenen gebruikt:

1. Machtigingen: de gebruikersrollen behoren tot een van de drie vermelde categorieën: waarnemer, editor, eigenaar. Een fotograaf of copywriter heeft bijvoorbeeld dezelfde rechten als een editor. De toestemmingen bepalen wat een gebruiker met inhoud in een project kan doen.
1. Workflows: de workflows bepalen wie taken in een project krijgt toegewezen. De taken kunnen met een projectrol worden geassocieerd. U kunt bijvoorbeeld een taak toewijzen aan fotografen, zodat alle teamleden die de rol van fotograaf hebben deze taak krijgen.

Alle projecten steunen de volgende standaardrollen om u veiligheid en controletoestemmingen te laten beheren.

| Rol | Beschrijving | Machtigingen | Groepslidmaatschap |
|---|---|---|---|
| Waarnemer | Een gebruiker in deze rol kan projectdetails, met inbegrip van de projectstatus bekijken. | Alleen-lezen machtigingen voor een project | `workflow-users` groep |
| Editor | Een gebruiker met deze rol kan de inhoud van een project uploaden en bewerken. | Lees en schrijf toegang op een project, bijbehorende meta-gegevens, en verwante activa <br> Bevoegdheden om een ontsproten lijst te uploaden, fotoontspruit, en activa <br> goed te keuren schrijven toestemming op `/etc/commerce`<br> wijzigt toestemming op een specifiek project | `workflow-users` groep |
| Eigenaar | Een gebruiker met deze rol kan een project tot stand brengen, het werk in een project in werking stellen, en goedgekeurde activa naar de productiemap verplaatsen. Alle andere taken in het project kunnen ook door de eigenaar worden bekeken en worden uitgevoerd. | Schrijfmachtigingen op `/etc/commerce` | `dam-users` groep om een project <br>`projects-administrators` groep te kunnen tot stand brengen om een project te kunnen tot stand brengen en activa te bewegen |

Voor creatieve projecten worden ook extra rollen zoals fotografen verstrekt. U kunt deze rollen gebruiken om douanerollen voor een specifiek project af te leiden.

### Automatische groep maken {#auto-group-creation}

Wanneer u het project creeert en gebruikers aan de diverse rollen toevoegt, worden de groepen verbonden aan het project automatisch gecreeerd om bijbehorende toestemmingen te beheren.

Bijvoorbeeld, zou een project genoemd Mijn project drie groepen **Myproject Eigenaars**, **Mijnproject Editors**, **Myproject Waarnemers** hebben.

Als het project wordt geschrapt, worden die groepen slechts geschrapt als u de aangewezen optie [ wanneer het schrappen van het project selecteert.](/help/sites-authoring/touch-ui-managing-projects.md#deleting-a-project) Een beheerder kan de groepen in **Hulpmiddelen** ook manueel schrappen > **Veiligheid** > **Groepen**.

## Aanvullende bronnen {#additional-resources}

Raadpleeg de volgende aanvullende documenten voor meer informatie over het gebruik van projecten:

* [Projecten beheren](/help/sites-authoring/touch-ui-managing-projects.md)
* [Werken met taken](/help/sites-authoring/task-content.md)
* [Werken met projectworkflows](/help/sites-authoring/projects-with-workflows.md)
* [Creative Project- en PIM-integratie](/help/sites-authoring/managing-product-information.md)
