---
title: Softwarearchitectuur
seo-title: Softwarearchitectuur
description: Aanbevolen procedures voor het ontwerpen van uw software
seo-description: Aanbevolen procedures voor het ontwerpen van uw software
uuid: a557f6ca-c3f1-486e-a45e-6e1f986fab41
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: best-practices
discoiquuid: 92971747-1c74-4917-b5a0-7b79b3ae1e68
exl-id: cd4f3b4c-5488-4ca7-9c1e-b4c819fda8e8
translation-type: tm+mt
source-git-commit: 423e17dadf2e506eb68b37851dde5e68ed950866
workflow-type: tm+mt
source-wordcount: '622'
ht-degree: 0%

---

# Softwarearchitectuur{#software-architecture}

## Ontwerpen voor upgrades {#design-for-upgrades}

Bij het uitbreiden van OTB-gedrag is het belangrijk om upgrades in gedachten te houden. Pas altijd aanpassingen in de /apps folder en of bedekking bovenop de overeenkomstige knopen in de /libs folder toe of gebruik het gooien:resourceSuperType om uit het doosgedrag uit te breiden. Hoewel sommige wijzigingen nodig kunnen zijn om een nieuwe AEM te ondersteunen, mag de nieuwe versie uw aanpassingen niet overschrijven als deze praktijk wordt gevolgd.

### Sjabloon en componenten indien mogelijk opnieuw gebruiken {#reuse-template-and-components-when-possible}

Hierdoor kan de site een consistentere look en feel behouden en het onderhoud van de code vereenvoudigen. Wanneer een nieuw malplaatje nodig is, zorg ervoor om van een gedeeld basissjabloon uit te breiden zodat de globale vereisten zoals cliëntlib opneming op één plaats kunnen worden gecodeerd. Wanneer een nieuwe component nodig is, zoekt u naar mogelijkheden om zich uit te breiden van een bestaande component.

### Ontwerpsjabloonontwerpen {#design-template-designs}

Door te bepalen welke componenten in elk parsys op de pagina kunnen worden omvat, kan de consistentie van de blik/het gevoel van de plaats worden gecontroleerd. Door de toegang tot het ontwerp op pagina&#39;s te beperken, kan &quot;super auteurs&quot;worden toegestaan om de toegestane componenten per pagina zonder ontwikkelaarsinterventie te wijzigen terwijl het ervoor zorgen dat de andere auteurs de collectieve normen volgen.

### Een SOLID-architectuur ontwikkelen {#develop-a-solid-architecture}

SOLID is een acroniem dat vijf architecturale principes beschrijft die zouden moeten worden nageleefd:

* **** Eén verantwoordelijkheidsbeginsel - elke module, klasse, methode, enz. moet maar één verantwoordelijkheid hebben.
* **** Open/Gesloten Beginsel - modules moeten voor verlenging openstaan en voor wijziging worden gesloten.
* **Beginsel van** vervanging door Liskov - soorten moeten door hun subtypes kunnen worden vervangen.
* **Beginsel van** interfacesegregatie - geen enkele cliënt mag worden gedwongen af te hangen van methoden die hij niet gebruikt.
* **Beginsel van** inversie van afhankelijkheid - Modules op hoog niveau mogen niet afhangen van modules op laag niveau. Beide moeten afhankelijk zijn van abstracties. Abstracties mogen niet afhankelijk zijn van details. Details moeten afhankelijk zijn van abstracties.

Het streven naar naleving van deze vijf beginselen moet resulteren in een systeem dat een strikte scheiding van zorgen heeft.

>[!TIP]
>
>SOLID is een algemeen gebruikt concept in object-oriented programmering en elk element wordt uitgebreid besproken in de industrie literatuur.
>
>Dit is slechts een korte samenvatting die wordt gepresenteerd voor bewustwording en u wordt aangespoord om meer vertrouwd te raken met deze concepten.

### Volg het Robustness-beginsel {#follow-the-robustness-principle}

In het Robustness-beginsel staat dat we conservatief moeten zijn in wat we sturen, maar liberaal moeten zijn in wat we accepteren. Met andere woorden, wanneer we berichten naar derden sturen, moeten we ons volledig aan de specificaties houden, maar wanneer we berichten van derden ontvangen, moeten we niet-conforme berichten accepteren zolang de betekenis van het bericht duidelijk is.

### Sikten implementeren in hun eigen modules {#implement-spikes-in-their-own-modules}

Spikes en testcode maken integraal deel uit van elke Agile-software-implementatie, maar we willen ervoor zorgen dat ze niet in onze productiecode terechtkomen zonder het juiste niveau van toezicht. Daarom wordt aangeraden om punten in hun eigen module te maken.

### Scripts voor gegevensmigratie in hun eigen module {#implement-data-migration-scripts-in-their-own-module} implementeren

Scripts voor gegevensmigratie, maar productiecode, worden doorgaans slechts eenmaal uitgevoerd bij de eerste keer dat een site wordt gestart. Zodra de site live is, wordt dit dus dode code. Om ervoor te zorgen dat we geen implementatiecode bouwen die afhankelijk is van de migratiescripts, moeten ze in hun eigen module worden geïmplementeerd. Hierdoor kunnen we deze code ook direct na het starten verwijderen en verwijderen, zodat dode code uit het systeem wordt verwijderd.

### Gepubliceerde gemaakte conventies volgen in POM-bestanden {#follow-published-maven-conventions-in-pom-files}

Apache heeft stijlconventies gepubliceerd op [https://maven.apache.org/developers/conventions/code.html](https://maven.apache.org/developers/conventions/code.html). Het is het beste om deze conventies te volgen, aangezien het voor nieuwe middelen gemakkelijker wordt om snel aan de slag te gaan.
