---
title: Enterprise DevOps
seo-title: Enterprise DevOps
description: Leer over de processen, methoden en communicatie die zijn vereist om implementatie en samenwerking te vereenvoudigen.
seo-description: Leer over de processen, methoden en communicatie die zijn vereist om implementatie en samenwerking te vereenvoudigen.
uuid: ca4806d2-c845-4c18-9498-4b66f0980a5e
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.5/MANAGING
topic-tags: managing
content-type: reference
discoiquuid: 934eda2a-bd3b-4018-86dc-dbb01d246386
translation-type: tm+mt
source-git-commit: a3c303d4e3a85e1b2e794bec2006c335056309fb
workflow-type: tm+mt
source-wordcount: '1005'
ht-degree: 93%

---


# Enterprise DevOps{#enterprise-devops}

DevOps omvat de processen, methoden en communicatie die nodig zijn voor de volgende stappen:

* Eenvoudige implementatie van uw software in verschillende omgevingen.
* Eenvoudige samenwerking tussen de ontwikkelings-, test- en implementatieteams.

DevOps heeft als doel om de onderstaande problemen te voorkomen:

* Handmatige fouten.
* Vergeten elementen; bijvoorbeeld bestanden, configuratiegegevens.
* Discrepanties; bijvoorbeeld tussen de lokale omgeving van een ontwikkelaar en andere omgevingen.

## Omgevingen {#environments}

Een Adobe Experience Manager-implementatie (AEM) bestaat gewoonlijk uit meerdere omgevingen die voor verschillende doeleinden op verschillende niveaus worden gebruikt:

* [Ontwikkeling](#development)
* [Kwaliteitsborging](#quality-assurance)
* [Staging](#staging)
* [Productie](#production-author-and-publish)

>[!NOTE]
>
>De productieomgeving moet minstens één auteur en één publicatieomgeving hebben.
>
>Het wordt aanbevolen dat alle andere omgevingen ook bestaan uit een auteur- en publicatieomgeving, zodat de productieomgeving wordt weerspiegeld en vroege tests mogelijk zijn.

### Ontwikkeling {#development}

Ontwikkelaars zijn verantwoordelijk voor het ontwikkelen en aanpassen van het voorgestelde project (website, mobiele apps, DAM-implementatie, enz.) met alle vereiste functionaliteit. Ontwikkelaars:

* ontwikkelen alle benodigde elementen en maken deze op maat, bijvoorbeeld sjablonen, componenten, workflows, applicaties
* realiseren het ontwerp
* ontwikkelen de services en scripts die nodig zijn voor de implementatie van de vereiste functionaliteit

De configuratie van de [ontwikkelomgeving](/help/sites-developing/best-practices.md) is afhankelijk van verschillende factoren, hoewel deze meestal bestaat uit:

* Een geïntegreerd ontwikkelingssysteem met versiebeheer dat dient als een geïntegreerde codebasis. Dit systeem wordt gebruikt om de code van de individuele ontwikkelomgevingen van de verschillende ontwikkelaars samen te voegen en te consolideren.
* Een persoonlijke omgeving voor elke ontwikkelaar; gewoonlijk op hun lokale machine. Op geplande tijdstippen wordt de code gesynchroniseerd met het versiebeheersysteem

Afhankelijk van de schaal van uw systeem kan de ontwikkelomgeving beschikken over zowel auteur- als publicatie-instanties.

### Kwaliteitsborging {#quality-assurance}

Deze omgeving wordt door het kwaliteitsbewakingsteam gebruikt om uw nieuwe systeem volledig [test](/help/sites-developing/test-plan.md); zowel ontwerp als functie. De omgeving moet beschikken over auteur- en publicatieomgevingen met geschikte content. Ook moet het alle noodzakelijke services bieden om een volledige reeks tests mogelijk te maken.

### Staging {#staging}

De stagingomgeving moet een spiegel zijn van de productieomgeving: configuratie, code en content:

* In deze omgeving worden scripts getest waarmee de daadwerkelijke implementatie wordt uitgevoerd.
* Deze omgeving kan worden toegepast voor definitieve tests (ontwerp, functionaliteit en interfaces) voorafgaand aan de implementatie op productieomgevingen.
* Hoewel de stagingomgeving nooit identiek kan zijn aan de productieomgeving, moet deze zo dicht mogelijk bij de uiteindelijk gewenste niveaus voor prestaties en belasting liggen.

### Productie - Auteur en Publicatie {#production-author-and-publish}

De productieomgeving bestaat uit de omgevingen die nodig zijn om uw implementatie daadwerkelijk te [ontwerpen en te publiceren](/help/sites-authoring/author.md#concept-of-authoring-and-publishing).

Een productieomgeving bestaat uit ten minste één auteurinstantie en één publicatie-instantie:

* Een [auteurinstantie](#author) voor de invoer van content.
* Een [publicatie-instantie](#publish) voor content die aan uw bezoekers/gebruikers ter beschikking wordt gesteld.

Afhankelijk van de schaal van het project, bestaat een project vaak uit verscheidene auteur- en/of publicatie-instanties. Op een lager niveau kan de repository ook naar meerdere instanties worden geclusterd.

#### Auteur {#author}

Auteurinstanties bevinden zich gewoonlijk achter de interne firewall. Dit is de omgeving waarin u en uw collega&#39;s ontwerptaken uitvoeren, zoals:

* het volledige systeem beheren
* uw content invoeren
* de lay-out en het ontwerp van uw content configureren
* uw content activeren voor de publicatieomgeving

Content die is geactiveerd, wordt in een pakket geplaatst en naar de replicatiewachtrij van de auteuromgeving verzonden. Het replicatieproces verplaatst de content dan naar de publicatieomgeving.

Om gegevens die in een publicatieomgeving zijn geproduceerd te repliceren en terug te sturen naar de auteuromgeving, moet een replicatielistener in de auteuromgeving pollingbewerkingen uitvoeren in de publicatieomgeving en dergelijke content ophalen uit het postvak UIT voor omgekeerde replicatie van de publicatieomgeving.

#### Publicatie {#publish}

Een publicatieomgeving bevindt zich gewoonlijk in de &#39;gedemilitariseerde zone&#39; (DMZ). In deze omgeving hebben bezoekers toegang tot uw content (bijvoorbeeld via een website of in de vorm van een mobiele app) en kunnen ze met de content aan de slag, ofwel via een openbaar netwerk, of binnen uw intranet. Een publicatieomgeving:

* bevat content die is gerepliceerd vanuit de auteuromgeving
* stelt die content ter beschikking van de bezoekers
* slaat gebruikersgegevens op die door uw bezoekers worden gegenereerd, zoals opmerkingen of andere formulierverzendingen
* kan worden geconfigureerd zodat dergelijke gebruikersgegevens via een postvak UIT voor omgekeerde replicatie kan worden teruggestuurd naar de auteuromgeving

De publicatieomgeving genereert uw content dynamisch in realtime. Ook kan de content voor elke gebruiker afzonderlijk worden aangepast.

## Codeverplaatsing {#code-movement}

Code moet altijd van beneden naar boven worden doorgegeven:

* de code wordt aanvankelijk ontwikkeld op de lokale omgeving en vervolgens geïntegreerd in de ontwikkelomgevingen
* gevolgd door grondig testen van de kwaliteitscontroleomgeving(en)
* vervolgens opnieuw getest op testomgevingen
* en pas hierna kan de code worden geïmplementeerd in de productieomgevingen

De code (bijvoorbeeld aangepaste functionaliteit van webapplicaties en ontwerpsjablonen) wordt meestal overgedragen door pakketten te exporteren en te importeren tussen de verschillende content-repository&#39;s. Waar zinvol kan deze replicatie als automatisch proces worden geconfigureerd.

AEM projecten activeren vaak de implementatie van code:

* Automatisch: voor overdracht naar de ontwikkelings- en kwaliteitscontroleomgevingen.
* Handmatig: implementaties in de staging- en productieomgevingen gebeurt op een meer beheerste en vaak handmatige manier; automatisering is echter mogelijk als dat nodig is.

![chlimage_1](assets/chlimage_1.png)

## Content verplaatsen {#content-movement}

Content die is bedoeld voor productie, moet **altijd** worden geschreven op de productieauteurinstantie.

Content mag geen code volgen die van een lagere naar een hogere omgeving gaat. Als dit zou gebeuren, en auteurs content maken op lokale computers of lagere omgevingen en de content vervolgens overbrengen naar de productieomgeving, is de kans groot dat er fouten en inconsistenties ontstaan.

Productiecontent moet van de productieomgeving naar de stagingomgeving worden verplaatst. Zo biedt de stagingomgeving een efficiënte en nauwkeurige testomgeving.

>[!NOTE]
>
>Dit betekent niet dat stagingcontent voortdurend moet worden gesynchroniseerd met productiecontent (regelmatige updates zijn voldoende), maar met name voordat een nieuwe code-iteratie wordt getest. Content in de kwaliteitscontrole- en ontwikkelingsomgevingen hoeft niet zo vaak te worden bijgewerkt, maar moet alleen een goede representatie van de productiecontent zijn.

Content kan worden overgedragen:

* Tussen de verschillende omgevingen: door pakketten te exporteren en te importeren.
* Tussen verschillende instanties - door ([AEM replicatie](/help/sites-deploying/replication.md)) de inhoud (gebruikend een HTTP, of HTTPS, verbinding) direct te herhalen.

![chlimage_1-1](assets/chlimage_1-1.png)