---
title: Softwarearchitectuur
description: Leer de beste praktijken voor het ontwerpen van uw software voor Adobe Experience Manager.
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: best-practices
exl-id: cd4f3b4c-5488-4ca7-9c1e-b4c819fda8e8
solution: Experience Manager, Experience Manager Sites
feature: Developing
role: Developer
source-git-commit: a28883778c5e8fb90cbbd0291ded17059ab2ba7e
workflow-type: tm+mt
source-wordcount: '612'
ht-degree: 0%

---

# Softwarearchitectuur{#software-architecture}

## Ontwerpen voor upgrades {#design-for-upgrades}

Wanneer het uitbreiden van uit-van-de-doos gedrag, is het belangrijk om verbeteringen in mening te houden. Pas altijd aanpassingen in de /apps folder en of bedekking bovenop de overeenkomstige knopen in de /libs folder toe of gebruik het gooien:resourceSuperType om uit het doosgedrag uit te breiden. Hoewel sommige wijzigingen nodig kunnen zijn om een nieuwe AEM te ondersteunen, mag de nieuwe versie uw aanpassingen niet overschrijven als deze praktijk wordt gevolgd.

### Sjabloon en componenten waar mogelijk opnieuw gebruiken {#reuse-template-and-components-when-possible}

Hierdoor kan de site een consistentere look behouden en het onderhoud van de code vereenvoudigen. Wanneer een nieuw malplaatje nodig is, zorg ervoor om van een gedeeld basissjabloon uit te breiden zodat de globale vereisten zoals cliëntlib opneming op één plaats kunnen worden gecodeerd. Wanneer een nieuwe component nodig is, zoekt u naar mogelijkheden om zich uit te breiden van een bestaande component.

### Ontwerpsjabloonontwerpen {#design-template-designs}

Door te bepalen welke componenten in elk parsys op de pagina kunnen worden omvat, kan de consistentie van de blik/het gevoel van de plaats worden gecontroleerd. Door de toegang tot het ontwerp op pagina&#39;s te beperken, kan &quot;super auteurs&quot;worden toegestaan om de toegestane componenten per pagina zonder ontwikkelaarsinterventie te wijzigen terwijl het ervoor zorgen dat de andere auteurs de collectieve normen volgen.

### Een SOLID-architectuur ontwikkelen {#develop-a-solid-architecture}

SOLID is een acroniem dat vijf architecturale principes beschrijft die zouden moeten worden nageleefd:

* **S** het Enige Beginsel van de Verantwoordelijkheid - elke module, klasse, methode, etc., zou slechts één verantwoordelijkheid moeten hebben.
* **O** open/Gesloten Beginsel - de modules zouden open voor uitbreiding en gesloten voor wijziging moeten zijn.
* **L** het Beginsel van de Vervanging van iskov - de types zouden vervangbaar door hun subtypes moeten zijn.
* **het Beginsel van de Segregatie van de Interface van I** - geen cliënt zou moeten worden gedwongen om van methodes af te hangen die het niet gebruikt.
* **D** het Beginsel van de Omkering van de Eendentie - de modules op hoog niveau zouden niet van modules op laag niveau moeten afhangen. Beide moeten afhankelijk zijn van abstracties. Abstracties mogen niet afhankelijk zijn van details. Details moeten afhankelijk zijn van abstracties.

Het streven naar naleving van deze vijf beginselen moet resulteren in een systeem dat een strikte scheiding van zorgen heeft.

>[!TIP]
>
>SOLID is een algemeen gebruikt concept in object-oriented programmering en elk element wordt uitgebreid besproken in de industrie literatuur.
>
>Deze informatie is slechts een korte samenvatting die wordt gepresenteerd om u bewust te maken van deze concepten en u wordt aangeraden zich dieper met deze concepten vertrouwd te maken.

### Volg het robuustheidsbeginsel {#follow-the-robustness-principle}

In het Robustness-beginsel staat dat u conservatief moet zijn in wat u verzendt, maar liberaal moet zijn in wat u accepteert. Met andere woorden, wanneer u berichten naar derden verzendt, moet u zich volledig aan de specificaties houden. Wanneer u echter berichten van derden ontvangt, moet u niet-conforme berichten accepteren zolang de betekenis van het bericht duidelijk is.

### Voer pieken in hun eigen modules uit {#implement-spikes-in-their-own-modules}

Spikes en testcode maken deel uit van elke Agile-software-implementatie. U wilt er echter voor zorgen dat ze niet overstappen op de basis van productiecode zonder het juiste niveau van toezicht te hebben. Daarom wordt aangeraden dat spikes in hun eigen module worden gemaakt.

### Scripts voor gegevensmigratie in hun eigen module implementeren {#implement-data-migration-scripts-in-their-own-module}

Scripts voor gegevensmigratie, maar productiecode, worden slechts eenmaal uitgevoerd bij de eerste keer dat een site wordt gestart. Wanneer de site live is, worden de scripts daarom dode code. Om ervoor te zorgen dat u geen implementatiecode bouwt die van de migratiescripts afhangt, zouden zij in hun eigen module moeten worden uitgevoerd. Zo kunnen we deze code direct na het starten verwijderen en verwijderen, zodat dode code uit het systeem wordt verwijderd.

### Gepubliceerde conventies in POM-bestanden volgen {#follow-published-maven-conventions-in-pom-files}

Apache heeft gepubliceerde stijlovereenkomsten in [&#x200B; https://maven.apache.org/developers/conventions/code.html &#x200B;](https://maven.apache.org/developers/conventions/code.html). Het is het beste om deze conventies te volgen, omdat het voor nieuwe middelen gemakkelijker wordt om snel aan de slag te gaan.
