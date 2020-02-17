---
title: Authoring
seo-title: Authoring
description: Concepten van ontwerpen in AEM
seo-description: Concepten van ontwerpen in AEM
uuid: eaa5f613-a138-4215-8f84-dfc962fe7fa7
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: introduction
content-type: reference
discoiquuid: 81ff6f6f-11b3-4f8e-80e6-b3e104158394
docset: aem65
translation-type: tm+mt
source-git-commit: 44eb94b917fe88b7c90c29ec7da553e15be391db

---


# Authoring{#authoring}

## Concept of Authoring (en publicatie) {#concept-of-authoring-and-publishing}

AEM biedt u twee omgevingen:

* Author
* Publiceren

Met deze interacties kunt u inhoud op uw website beschikbaar maken, zodat uw bezoekers deze kunnen lezen.

De auteursomgeving verstrekt de mechanismen om deze inhoud tot stand te brengen, bij te werken en te herzien alvorens het daadwerkelijk te publiceren:

* Een auteur maakt en beoordeelt de inhoud (dit kan van verschillende typen zijn). bijvoorbeeld pagina&#39;s, middelen, publicaties, enz.)
* die op een gegeven moment op uw website worden gepubliceerd.

![chlimage_1-132](assets/chlimage_1-132.png)

Op de auteursomgeving wordt de functionaliteit van AEM ter beschikking gesteld door twee UIs. Voor het publicatiemilieu ontwerpt u de volledige blik-en-gevoel van de interface die aan uw gebruikers ter beschikking wordt gesteld.

>[!NOTE]
>
>AEM zelf wordt gebruikt om de documentatie van AEM te ontwerpen.
>
>Samen met de Dispatcher wordt het ook gebruikt voor het publiceren.

### Auteursomgeving {#author-environment}

De auteur werkt in wat als het **auteursmilieu** wordt bekend. Dit verstrekt een makkelijk te gebruiken interface (grafische gebruikersinterface (GUI of UI)) voor het creëren van de inhoud. Het wordt gewoonlijk gevestigd achter de firewall van een bedrijf die volledige bescherming biedt en de auteur aan login vereist, gebruikend een rekening die de aangewezen toegangsrechten is toegewezen.

>[!NOTE]
>
>Uw account heeft de juiste toegangsrechten nodig om inhoud te maken, bewerken of publiceren.

Afhankelijk van hoe uw instantie en uw persoonlijke toegangsrechten worden gevormd kunt u vele taken op uw inhoud, met inbegrip van (onder andere) uitvoeren:

* nieuwe inhoud genereren of bestaande inhoud bewerken op een pagina
* vooraf gedefinieerde sjablonen gebruiken om nieuwe inhoudspagina&#39;s te maken
* uw elementen en verzamelingen maken, bewerken en beheren
* uw publicaties maken, bewerken en beheren
* uw campagnes en de bijbehorende bronnen ontwikkelen
* gemeenschapssites ontwikkelen en beheren
* inhoudspagina&#39;s, elementen, enz. verplaatsen, kopiëren of verwijderen
* pagina&#39;s, elementen, enz. publiceren (of de publicatie ervan ongedaan maken)

Daarnaast zijn er beheertaken die u helpen uw inhoud te beheren:

* workflows die bepalen hoe wijzigingen worden beheerd; bijvoorbeeld. een toetsing vóór publicatie afdwingen
* projecten die individuele taken coördineren

>[!NOTE]
>
>AEM wordt (voor het merendeel van de taken) ook [beheerd](/help/sites-administering/home.md) vanuit de auteursomgeving.

#### Publicatie-omgeving {#publish-environment}

Als de inhoud van de AEM-site gereed is, wordt deze gepubliceerd naar de **publicatieomgeving**. Hier worden de pagina&#39;s van de website beschikbaar gemaakt voor het beoogde publiek, in overeenstemming met de vormgeving van de ontworpen interface.

Meestal bevindt de publicatieomgeving zich in de gedemilitariseerde zone. met andere woorden , beschikbaar voor het internet , maar niet langer onder volledige bescherming van het interne netwerk .

Wanneer de AEM-site een [gemeenschapssite](/help/communities/overview.md)is of onderdelen [van de](/help/communities/author-communities.md)Community bevat, kunnen bezoekers (leden) die zich bij de AEM-site hebben aangemeld, communiceren met de kenmerken van de Community. Ze kunnen bijvoorbeeld posten naar een forum, een opmerking plaatsen of andere leden volgen. Leden kunnen toestemming krijgen om activiteiten uit te voeren die normaal gesproken beperkt zijn tot de auteursomgeving, zoals het maken van nieuwe pagina&#39;s (groepen van gemeenschappen), blogartikelen en gematigde posten van andere leden.

>[!NOTE]
>
>Helaas is er soms sprake van een overlapping in de gebruikte terminologie. Dit kan gebeuren met:
>
>* **Publiceren/Publiceren ongedaan maken**
   >  Dit zijn de belangrijkste termen voor de acties die uw inhoud openbaar maken in uw publicatieomgeving (of niet).
   >
   >
* **Activeren/deactiveren**
   >  Deze termen zijn synoniem met publiceren/verwijderen.
   >
   >
* **Replicatie/replicatie**
   >  Dit zijn de technische termen die worden gebruikt om de verplaatsing van gegevens (bijvoorbeeld pagina-inhoud, bestanden, code, gebruikersopmerkingen) van de ene omgeving naar de andere aan te geven; d.w.z. bij het publiceren of omgekeerd repliceren van gebruikersopmerkingen.
>



#### Dispatcher {#dispatcher}

Om de prestaties voor bezoekers van uw website te optimaliseren, implementeert de **[verzender](https://helpx.adobe.com/experience-manager/dispatcher/user-guide.html)**taakverdeling en caching.
