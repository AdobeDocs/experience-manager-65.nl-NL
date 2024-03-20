---
title: Authoring
description: Concepten van ontwerpen en publiceren in Adobe Experience Manager 6.5.
exl-id: dcda537a-1bb2-4ce3-9904-40d158b47556
solution: Experience Manager, Experience Manager Sites
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '547'
ht-degree: 0%

---

# Authoring{#authoring}

## Concept of Authoring (en publicatie) {#concept-of-authoring-and-publishing}

AEM biedt u twee omgevingen:

* Auteur
* Publiceren

Met deze interacties kunt u inhoud op uw website beschikbaar maken, zodat uw bezoekers de inhoud kunnen lezen.

De auteursomgeving verstrekt de mechanismen om, deze inhoud tot stand te brengen bij te werken en te herzien alvorens het daadwerkelijk te publiceren:

* Een auteur maakt en beoordeelt de inhoud (dit kan van verschillende typen zijn, bijvoorbeeld pagina&#39;s, middelen, publicaties, enzovoort)
* die op een gegeven moment op uw website worden gepubliceerd.

![Overzicht van omgevingen](assets/chlimage_1-132.png)

Op het auteursmilieu, wordt de functionaliteit van AEM ter beschikking gesteld door twee UIs. Voor het publicatiemilieu, ontwerpt u het volledige blik-en-gevoel van de interface die aan uw gebruikers ter beschikking wordt gesteld.

### Auteursomgeving {#author-environment}

De auteur werkt in wat als **auteursomgeving**. Dit verstrekt een makkelijk te gebruiken interface (grafische gebruikersinterface (GUI of UI)) voor het creëren van de inhoud. Het wordt gevestigd achter de firewall van een bedrijf die volledige bescherming biedt en de auteur vereist om zich aan te melden, gebruikend een rekening die de aangewezen toegangsrechten is toegewezen.

>[!NOTE]
>
>Uw account heeft de juiste toegangsrechten nodig om inhoud te maken, bewerken of publiceren.

Afhankelijk van hoe uw instantie en uw persoonlijke toegangsrechten worden gevormd kunt u vele taken op uw inhoud, met inbegrip van (onder anderen) uitvoeren:

* nieuwe inhoud genereren of bestaande inhoud bewerken op een pagina
* vooraf gedefinieerde sjablonen gebruiken om nieuwe inhoudspagina&#39;s te maken
* uw elementen en verzamelingen maken, bewerken en beheren
* uw publicaties maken, bewerken en beheren
* uw campagnes en de bijbehorende bronnen ontwikkelen
* gemeenschapssites ontwikkelen en beheren
* inhoudspagina&#39;s, elementen, enzovoort verplaatsen, kopiëren of verwijderen
* pagina&#39;s, elementen, enzovoort publiceren (of de publicatie ervan ongedaan maken)

Bovendien zijn er beheertaken die u helpen uw inhoud te beheren:

* workflows die bepalen hoe wijzigingen worden beheerd; bijvoorbeeld een revisie vóór publicatie afdwingen
* projecten die individuele taken coördineren

>[!NOTE]
>
>AEM [toegediend](/help/sites-administering/home.md) (voor de meeste taken) uit de auteursomgeving.

#### Publicatie-omgeving {#publish-environment}

Als de inhoud van de AEM-site gereed is, wordt deze gepubliceerd naar de **publicatieomgeving**. Hier worden de pagina&#39;s van de website beschikbaar gemaakt voor het beoogde publiek, in overeenstemming met de vormgeving van de ontworpen interface.

Meestal bevindt de publicatieomgeving zich in de gedemilitariseerde zone, met andere woorden beschikbaar voor het internet, maar niet langer onder volledige bescherming van het interne netwerk.

Wanneer de AEM-site een [community-site](/help/communities/overview.md), of omvat [Community-componenten](/help/communities/author-communities.md), kunnen bezoekers (leden) die zich hebben aangemeld, communiceren met de kenmerken van de Gemeenschappen. Ze kunnen bijvoorbeeld posten naar een forum, een opmerking plaatsen of andere leden volgen. Leden kunnen toestemming krijgen om activiteiten uit te voeren die gewoonlijk beperkt zijn tot de auteursomgeving, zoals het maken van nieuwe pagina&#39;s (groepen van gemeenschappen), blogartikelen en gematigde posten van andere leden.

>[!NOTE]
>
>Helaas is er soms sprake van een overlapping in de gebruikte terminologie. Dit kan gebeuren met:
>
>* **Publiceren/Publiceren ongedaan maken**
>  Dit zijn de belangrijkste termen voor de acties die uw inhoud openbaar maken in uw publicatieomgeving (of niet).
>
>* **Activeren/deactiveren**
>  Deze termen zijn synoniem met publiceren/verwijderen.
>
>* **Replicatie/replicatie**
>  Dit zijn de technische termen die worden gebruikt om de beweging van gegevens (bijvoorbeeld pagina-inhoud, bestanden, code, gebruikerscommentaren) aan te geven van de ene omgeving naar de andere, dat wil zeggen bij het publiceren of omgekeerde replicatie van gebruikersopmerkingen.
>

#### Dispatcher {#dispatcher}

Om de prestaties voor bezoekers van uw website te optimaliseren, **[Dispatcher](https://experienceleague.adobe.com/docs/experience-manager-dispatcher/using/dispatcher.html)** implementeert taakverdeling en caching.
