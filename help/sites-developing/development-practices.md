---
title: Ontwikkelspraktijken
description: Aanbevolen procedures voor ontwikkeling op Adobe Experience Manager.
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: best-practices
exl-id: 65b2029e-03c9-4df4-8579-2b15dbee1035
solution: Experience Manager, Experience Manager Sites
feature: Developing
role: Developer
source-git-commit: 66db4b0b5106617c534b6e1bf428a3057f2c2708
workflow-type: tm+mt
source-wordcount: '617'
ht-degree: 0%

---

# Ontwikkelspraktijken{#development-practices}

## Werken volgens de definitie van Gereed (DoD) {#work-according-to-a-definition-of-done}

Elk team heeft een andere definitie van wat &quot;gedaan&quot;betekent, maar het is belangrijk om te hebben en ervoor te zorgen dat een verhaal aan de bepaalde criteria alvorens wordt goedgekeurd voldoet.

Sommige criteria die algemeen door teams worden gespecificeerd omvatten:

* Code voor opmaak gecontroleerd
* Opmerkingen/Javadoc toegevoegd
* Voldoet aan de vereiste dekkingsniveaus van de test
* Eenheids- en integratietests
* Gevalideerd in de milieu QA
* Lokalisatie geïmplementeerd

Zonder een welomschreven DoD is het gemakkelijk om in een situatie te belanden waarin veel dingen halverwege worden gedaan en niets echt compleet is.

### Coderings- en opmaakconventies definiëren en naleven {#define-and-adhere-to-coding-and-formatting-conventions}

Dingen als inspringingsniveaus en witruimte lijken misschien niet belangrijk, maar als de code juist is opgemaakt, gaat het veel verder in de richting van leesbaarheid en onderhoudsgemak. Conventies moeten als team worden besproken en overeengekomen en vervolgens in de code worden gevolgd.

### Doel van hoge testdekking  {#aim-for-high-test-coverage}

Naarmate een projectimplementatie groter wordt, neemt ook de tijd die nodig is om deze te testen toe. Zonder goede testdekking, kan het testteam niet schrapen en de ontwikkelaars uiteindelijk begraven in insecten.

Ontwikkelaars moeten tests op &#39;Test Driven Development&#39; (TDD) uitvoeren, waarbij defecte eenheidstests worden geschreven voordat de productiecode aan hun vereisten voldoet. QA zou een geautomatiseerde reeks goedkeuringstests moeten tot stand brengen om ervoor te zorgen dat het systeem zoals verwacht van een hoog niveau werkt.

Er zijn aangepaste frameworks beschikbaar, zoals Jackalope en Prosper, om het kopiëren van JCR API&#39;s eenvoudiger te maken om de productiviteit van ontwikkelaars te garanderen terwijl ze eenheidstests schrijven.

### Demo gereed houden {#stay-demo-ready}

Het systeem zou aan het eind van elke herhaling voor demo aan de zaken moeten beschikbaar zijn. Door het systeem in een demo-klaar staat te houden, zal het team altijd binnen een herhaling van klaar zijn voor productie en kan de technische schuld op een houdbaar niveau worden gehouden.

### Een ononderbroken integratieomgeving implementeren en gebruiken {#implement-a-continuous-integration-environment-and-use-it}

Door een ononderbroken integratieomgeving te implementeren kunt u eenvoudig en herhaaldelijk eenheidstests en integratietests uitvoeren. Het ontkoppelt ook plaatsingen van het ontwikkelingsteam, dat de andere delen van het team machtigt om efficiënter te zijn en voor stabielere en voorspelbaardere plaatsingen te maken.

### Houd de ontwikkelingscyclus snel door de buildtijden laag te houden {#keep-the-development-cycle-fast-by-keeping-build-times-low}

Als de eenheidstests lang duren, zullen de ontwikkelaars vermijden lopend hen en zij zullen hun waarde verliezen. Als het lang duurt om de code te bouwen en op te stellen, zullen de mensen dit minder vaak doen. Het maken van korte bouwstijl tijden een prioriteit verzekert dat de tijd die u in testdekking en infrastructuur van CI hebt geïnvesteerd het team productiever blijft maken.

### Sonar en andere statische hulpmiddelen van de codeanalyse verfijnen en op hun rapporten handelen {#fine-tune-sonar-and-other-static-code-analysis-tools-and-act-on-their-reports}

De instrumenten van de codeanalyse kunnen waardevol zijn, maar slechts als hun rapporten tot actie van de kant van het ontwikkelingsteam leiden. Zonder de analyse die deze instrumenten opleveren te verfijnen, worden de aanbevelingen die ze genereren irrelevant en verliezen ze hun waarde.

### Volg de Scout voor de jongen {#follow-the-boy-scout-rule}

De Scouten van de Jongen hebben een regel: &quot;Laat het beter dan je vond.&quot; Zolang alle leden van het ontwikkelingsteam zich aan deze regel houden en iets opruimen wanneer ze een puinhoop tegenkomen, zal de code voortdurend verbeteren.

### Gebruik geen YAGNI-functies {#avoid-implementing-yagni-features}

YAGNI (U zult het niet nodig hebben) zijn kenmerken die worden geïmplementeerd wanneer we verwachten dat we in de toekomst iets nodig hebben, ook al hebben we het nu niet nodig. In het ideale geval moeten we het eenvoudigste ding implementeren dat vandaag werkt en ononderbroken refactoring gebruiken om ervoor te zorgen dat de architectuur van het systeem in de loop der tijd evolueert met de vereisten. Hierdoor kunnen we ons concentreren op wat er belangrijk is en codeblok en functieschepping voorkomen.
