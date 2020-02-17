---
title: Ontwikkelingspraktijken
seo-title: Ontwikkelingspraktijken
description: Aanbevolen werkwijzen voor ontwikkeling op AEM
seo-description: Aanbevolen werkwijzen voor ontwikkeling op AEM
uuid: 27a75f7f-6e2c-4113-9e9f-c5013a4594c2
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: best-practices
discoiquuid: 8b0297a1-d922-410f-9aaf-3a6b87e11dc0
translation-type: tm+mt
source-git-commit: a3c303d4e3a85e1b2e794bec2006c335056309fb

---


# Ontwikkelingspraktijken{#development-practices}

## Werken volgens een definitie van Gereed {#work-according-to-a-definition-of-done}

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

### Doel van hoge testdekking {#aim-for-high-test-coverage}

Naarmate een projectimplementatie groter wordt, zal ook de tijd die nodig is om deze te testen, toenemen. Zonder goede testdekking, zal het testteam niet kunnen schrapen en de ontwikkelaars zullen uiteindelijk begraven in insecten worden.

Ontwikkelaars zouden TDD moeten gebruiken en ontbrekende eenheidstests vóór de productiecode schrijven die aan hun vereisten zal voldoen. QA zou een geautomatiseerde reeks goedkeuringstests moeten tot stand brengen om ervoor te zorgen dat het systeem zoals verwacht van een hoog niveau werkt.

Er zijn aangepaste frameworks beschikbaar, zoals Jackalope en Prosper, om het kopiëren van JCR API&#39;s eenvoudiger te maken om de productiviteit van ontwikkelaars te garanderen terwijl ze eenheidstests schrijven.

### Demo gereed houden {#stay-demo-ready}

Het systeem zou aan het eind van elke herhaling voor demo aan de zaken moeten beschikbaar zijn. Door het systeem in een demo-klaar staat te houden, zal het team altijd binnen een herhaling van klaar zijn voor productie en kan de technische schuld op een houdbaar niveau worden gehouden.

### Een ononderbroken integratieomgeving implementeren en gebruiken {#implement-a-continuous-integration-environment-and-use-it}

Het uitvoeren van een ononderbroken integratiemilieu zal u toestaan om eenheidstests en integratietests gemakkelijk en herhaalbaar in werking te stellen. Het zal ook plaatsingen van het ontwikkelingsteam loskoppelen, die de andere delen van het team om efficiënter en makend voor stabielere en voorspelbaardere plaatsingen toelaat te zijn.

### Houd de ontwikkelingscyclus snel door de buildtijden laag te houden {#keep-the-development-cycle-fast-by-keeping-build-times-low}

Als de eenheidstests lang duren, zullen de ontwikkelaars vermijden lopend hen en zij zullen hun waarde verliezen. Als het lang duurt om de code te bouwen en op te stellen, zullen de mensen dit minder vaak doen. Het maken van korte bouwtijden een prioriteit verzekert dat de tijd wij in onze testdekking en infrastructuur van CI hebben geïnvesteerd het team productiever zal blijven maken.

### Sonar en andere statische hulpmiddelen van de codeanalyse nauwkeurig afstemmen en op hun rapporten handelen {#fine-tune-sonar-and-other-static-code-analysis-tools-and-act-on-their-reports}

De instrumenten van de codeanalyse kunnen waardevol zijn, maar slechts als hun rapporten tot actie van de kant van het ontwikkelingsteam leiden. Zonder de analyse die deze instrumenten opleveren te verfijnen, zullen de aanbevelingen die ze genereren niet relevant zijn en zullen ze hun waarde verliezen.

### Volg de scout van de jongen {#follow-the-boy-scout-rule}

De Jongen sokken hebben een regel: &quot;Laat het beter staan dan u het hebt gevonden.&quot; Zolang alle leden van het ontwikkelingsteam zich aan deze regel houden en iets opschonen wanneer ze een puinhoop tegenkomen, zal de code voortdurend verbeteren.

### Gebruik geen YAGNI-functies {#avoid-implementing-yagni-features}

YAGNI-functies (of u hebt het niet nodig) worden geïmplementeerd wanneer we verwachten dat we in de toekomst iets nodig hebben, ook al hebben we het nu niet nodig. In het ideale geval moeten we het eenvoudigste ding implementeren dat vandaag werkt en ononderbroken refactoring gebruiken om ervoor te zorgen dat de architectuur van het systeem in de loop der tijd evolueert met de vereisten. Hierdoor kunnen we ons concentreren op wat belangrijk is en codeblok en eigenschapscrupules voorkomen.
