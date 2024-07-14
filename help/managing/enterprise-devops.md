---
title: Enterprise DevOps
description: Leer over de processen, de methodes, en de mededeling die worden vereist om plaatsing te verlichten en samenwerking te vereenvoudigen.
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.5/MANAGING
topic-tags: managing
content-type: reference
exl-id: e67f848a-a8cd-4585-a734-e6b1de8a8d74
solution: Experience Manager, Experience Manager 6.5
feature: Compliance
role: Developer,Leader
source-git-commit: 9a3008553b8091b66c72e0b6c317573b235eee24
workflow-type: tm+mt
source-wordcount: '983'
ht-degree: 58%

---

# Enterprise DevOps{#enterprise-devops}

DevOps omvat de processen, de methodes, en de mededeling die worden vereist om:

* Eenvoudige implementatie van uw software in verschillende omgevingen.
* Vereenvoudig de samenwerking tussen de ontwikkelings-, test- en implementatieteams.

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

De ontwikkelaars zijn verantwoordelijk voor het ontwikkelen en aanpassen van het voorgestelde project (website, mobiele toepassingen, DAM-implementatie, enzovoort), met alle vereiste functionaliteit. Ontwikkelaars:

* ontwikkelen alle benodigde elementen en maken deze op maat, bijvoorbeeld sjablonen, componenten, workflows, applicaties
* realiseren het ontwerp
* ontwikkelen de services en scripts die nodig zijn voor de implementatie van de vereiste functionaliteit

De configuratie van het [ ontwikkelings ](/help/sites-developing/best-practices.md) milieu kan van diverse factoren afhangen, hoewel het van wordt samengesteld:

* Een geïntegreerd ontwikkelingssysteem met versiebeheer dat dient als een geïntegreerde codebasis. Dit systeem wordt gebruikt om de code van de individuele ontwikkelomgevingen van de verschillende ontwikkelaars samen te voegen en te consolideren.
* Een persoonlijke omgeving voor elke ontwikkelaar; gewoonlijk op hun lokale machine. Met de juiste intervallen wordt de code gesynchroniseerd met het versiebeheersysteem

Afhankelijk van de schaal van uw systeem kan de ontwikkelomgeving beschikken over zowel auteur- als publicatie-instanties.

### Kwaliteitsborging {#quality-assurance}

Dit milieu wordt gebruikt door het team van de kwaliteitsborging om [ ](/help/sites-developing/test-plan.md) uw nieuw systeem volledig te testen; zowel ontwerp als functie. De omgeving moet beschikken over auteur- en publicatieomgevingen met geschikte content. Ook moet het alle noodzakelijke services bieden om een volledige reeks tests mogelijk te maken.

### Staging {#staging}

De testomgeving moet een spiegel zijn van de productieomgeving - configuratie, code en inhoud:

* In deze omgeving worden scripts getest waarmee de daadwerkelijke implementatie wordt uitgevoerd.
* Het kan voor definitieve tests (ontwerp, functionaliteit, en interfaces) worden gebruikt alvorens aan de productiemilieu&#39;s op te stellen.
* Hoewel de stagingomgeving nooit identiek kan zijn aan de productieomgeving, moet deze zo dicht mogelijk bij de uiteindelijk gewenste niveaus voor prestaties en belasting liggen.

### Productie - Auteur en Publish {#production-author-and-publish}

De productieomgeving bestaat uit de omgevingen die nodig zijn om uw implementatie daadwerkelijk te [ontwerpen en te publiceren](/help/sites-authoring/author.md#concept-of-authoring-and-publishing).

Een productieomgeving bestaat uit ten minste één auteurinstantie en één publicatie-instantie:

* Een [auteurinstantie](#author) voor de invoer van content.
* Een [publicatie-instantie](#publish) voor content die aan uw bezoekers/gebruikers ter beschikking wordt gesteld.

Afhankelijk van de schaal van het project, bestaat het vaak uit verscheidene auteursinstanties, of verscheidene publiceer instanties, of allebei. Op een lager niveau kan de repository ook naar meerdere instanties worden geclusterd.

#### Auteur {#author}

Auteurinstanties bevinden zich gewoonlijk achter de interne firewall. Dit is de omgeving waarin u en uw collega&#39;s ontwerptaken uitvoeren, zoals:

* het volledige systeem beheren
* uw content invoeren
* de lay-out en het ontwerp van uw content configureren
* uw content activeren voor de publicatieomgeving

Content die is geactiveerd, wordt in een pakket geplaatst en naar de replicatiewachtrij van de auteuromgeving verzonden. Het replicatieproces verplaatst de content dan naar de publicatieomgeving.

Als u gegevens die in een publicatieomgeving zijn gegenereerd, wilt terugkeren naar de auteursomgeving, pollt een replicatielistener in de auteuromgeving de publicatieomgeving en haalt u deze inhoud op uit de omgekeerde replicatieoutbox van de publicatieomgeving.

#### Publish {#publish}

Een publicatieomgeving bevindt zich in de gedemilitariseerde zone (DMZ). Dit is de omgeving waarin bezoekers toegang krijgen tot uw inhoud (bijvoorbeeld via een website of in de vorm van een mobiele toepassing) en ermee communiceren, of het nu gaat om een openbare of intranetfunctie. Een publicatieomgeving:

* bevat content die is gerepliceerd vanuit de auteuromgeving
* stelt die content ter beschikking van de bezoekers
* slaat gebruikersgegevens op die door uw bezoekers worden gegenereerd, zoals opmerkingen of andere formulierverzendingen
* kan worden geconfigureerd zodat dergelijke gebruikersgegevens via een postvak UIT voor omgekeerde replicatie kan worden teruggestuurd naar de auteuromgeving

De publicatieomgeving genereert uw content dynamisch in realtime. Ook kan de content voor elke gebruiker afzonderlijk worden aangepast.

## Codeverplaatsing {#code-movement}

Code altijd van beneden naar boven verschuiven:

* de code wordt aanvankelijk ontwikkeld op de lokale omgeving en vervolgens geïntegreerd in de ontwikkelomgevingen
* gevolgd door grondig testen op de QA-omgevingen
* vervolgens opnieuw getest op testomgevingen
* en pas hierna kan de code worden geïmplementeerd in de productieomgevingen

De code (bijvoorbeeld aangepaste functionaliteit van webtoepassingen en ontwerpsjablonen) wordt overgedragen door pakketten te exporteren en te importeren tussen de verschillende opslagplaatsen voor inhoud. Waar zinvol kan deze replicatie als automatisch proces worden geconfigureerd.

AEM Projecten activeren vaak de implementatie van code:

* Automatisch: voor overdracht naar de ontwikkelings- en kwaliteitscontroleomgevingen.
* Handmatig: implementaties in de staging- en productieomgeving worden op een meer beheerste manier uitgevoerd, vaak handmatig; automatisering is echter mogelijk, indien nodig.

![ chlimage_1 ](assets/chlimage_1.png)

## Inhoud verplaatsen {#content-movement}

Content die is bedoeld voor productie, moet **altijd** worden geschreven op de productieauteurinstantie.

Content mag geen code volgen die van een lagere naar een hogere omgeving gaat. Als dit zou gebeuren, en auteurs content maken op lokale computers of lagere omgevingen en de content vervolgens overbrengen naar de productieomgeving, is de kans groot dat er fouten en inconsistenties ontstaan.

Productiecontent moet van de productieomgeving naar de stagingomgeving worden verplaatst. Zo biedt de stagingomgeving een efficiënte en nauwkeurige testomgeving.

>[!NOTE]
>
>Dit betekent niet dat het opvoeren van inhoud voortdurend met productie moet worden gesynchroniseerd, zijn de regelmatige updates voldoende, maar vooral alvorens een nieuwe herhaling van code te testen. Inhoud in de kwaliteitscontrole- en ontwikkelingsomgevingen hoeft niet zo vaak te worden bijgewerkt, maar moet een goede weergave van de productie-inhoud zijn.

Inhoud kan worden overgedragen:

* Tussen de verschillende omgevingen: door pakketten te exporteren en te importeren.
* Tussen verschillende instanties - door ([ AEM replicatie ](/help/sites-deploying/replication.md)) direct te herhalen, de inhoud (gebruikend HTTP, of HTTPS, verbinding).

![ chlimage_1-1 ](assets/chlimage_1-1.png)
