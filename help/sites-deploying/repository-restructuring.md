---
title: Repositoregeling herstructurering in AEM 6.5
seo-title: Repositoregeling herstructurering in AEM 6.5
description: Meer informatie over de grondbeginselen en de redenering achter de herstructurering van de opslagplaats in AEM 6.5
seo-description: Meer informatie over de grondbeginselen en de redenering achter de herstructurering van de opslagplaats in AEM 6.5
uuid: e9cd3e88-e352-44a8-9b97-69488d3267cb
contentOwner: chaikels
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: repo_restructuring
discoiquuid: fc879b0b-823b-4bdc-aaa6-36f53a33fb22
translation-type: tm+mt
source-git-commit: 97b2da315fac6f84fcba6d4464bf8dd1d690cfd1

---


# Repositoregeling herstructurering in AEM 6.5{#repository-restructuring-in-aem}

## Inleiding {#introduction}

Vóór AEM 6.4, werd de klantencode opgesteld in onvoorspelbare gebieden van JCR die onderhevig waren aan verandering op verbeteringen. Daarom was het gebruikelijk voor formele AEM-versies om aangepaste code, configuratie of inhoud te overschrijven. Bovendien overschrijven wijzigingen door klanten soms de AEM-productcode of -inhoud, waardoor de productfunctionaliteit wordt verbroken.

Door hiërarchieën voor AEM productcode en klantencode duidelijk te bepalen, kunnen deze conflicten worden vermeden.

Te dien einde wordt, vanaf AEM 6.4 en om in toekomstige versies te worden voortgezet, de inhoud van /etc naar andere mappen in de opslagplaats geherstructureerd, samen met richtlijnen over waar de inhoud naartoe gaat, met inachtneming van de volgende regels op hoog niveau:

* AEM-productcode wordt altijd in /libs geplaatst, die niet door aangepaste code mag worden overschreven
* De aangepaste code moet worden geplaatst in /apps, /content en /conf

## Effect op upgrades van 6,5 graden {#impact-on-upgrades}

Wanneer u een upgrade uitvoert naar AEM 6.5, wordt een grote subset van de inhoud onder /etc. gedupliceerd in andere mappen in de opslagplaats. Deze nieuwe locaties zijn de voorkeurslocaties voor de inhoud. Nochtans, is elke poging gemaakt om AEM 6.5 verbetering achterwaarts compatibel met de vorige plaatsen in de /etc omslag te zijn en zo in de meeste gevallen zullen de oude plaatsen door AEM code blijven worden van verwijzingen voorzien tot de veranderingen actief — en in veel gevallen manueel — in de toepassing van een klant worden gemaakt. Vanuit een tijdlijnperspectief zijn er twee categorieën wijzigingen:

* Met 6.5 Verbetering - een handvol van de /etc-herstructureringsveranderingen zijn niet achterwaarts compatibel en daarom zouden de aanpassingen als deel van de verbetering van AEM 6.5 moeten worden gepland en worden uitgevoerd.
* Voorafgaand aan de toekomstige upgrade: het overgrote deel van de wijzigingen in de herstructurering /etc. kan worden uitgesteld tot enige tijd in de toekomstige upgrade. Zoals eerder vermeld, zal de code AEM 6.5 de oude plaatsen blijven van verwijzingen voorzien tot de wijzigingen als deel van een klantenversie worden uitgevoerd. Hoewel er geen geforceerde tijdlijn is waarvoor de veranderingen zouden moeten worden aangebracht, wordt geadviseerd dat zij vóór de toekomstige verbetering worden gemaakt aangezien de toekomstige eigenschappen op de nieuwe plaatsen kunnen baseren die worden van verwijzingen voorzien. Bovendien zal de documentatie voor een bepaalde eigenschap door conventie naar de nieuwe plaatsen verwijzen en het zou daarom verwarrend kunnen zijn als de oude plaatsen nog worden gebruikt.

### Herstructureringsrichtsnoeren {#restructuring-guidance}

Bij de planning voor een upgrade naar AEM 6.5 moet naar de volgende pagina&#39;s per oplossing worden verwezen om de werkinspanning te beoordelen:

* [Herstructurering van de opslagplaats, gemeenschappelijk voor alle AEM-oplossingen](/help/sites-deploying/all-repository-restructuring-in-aem-6-5.md)
* [Herstructurering van de AEM-sitecentra](/help/sites-deploying/sites-repository-restructuring-in-aem-6-5.md)
* [Herstructurering van de AEM Assets-opslagplaats](/help/sites-deploying/assets-repository-restructuring-in-aem-6-5.md)
* [Herstructurering van de opslagplaats van AEM Assets Dynamic Media](/help/sites-deploying/dynamicmedia-repository-restructuring-in-aem-6-5.md)
* [Herstructurering van de opslagplaats van AEM Forms](/help/sites-deploying/forms-repository-restructuring-in-aem-6-5.md)
* [Herstructurering van de opslagplaats van AEM](/help/sites-deploying/communities-repository-restructuring-in-aem-6-5.md)
* [Herstructurering van de opslagplaats van AEM](/help/sites-deploying/ecommerce-repository-restructuring-in-aem-6-5.md)

Elke pagina bevat twee secties die overeenkomen met de urgentie van de noodzakelijke wijzigingen. Om het even wat onder de &quot;Met 6.5 Verbetering&quot;sectie zou als deel van het AEM 6.5 verbeteringsproject moeten worden behandeld. Alles onder de &quot;Voorafgaande aan toekomstige upgrade&quot; kan optioneel worden uitgesteld tot na de upgrade.

Elke vermelding op de pagina bevat een veld &quot;Herstructureringshulplijnen&quot;, waarin de aanbevolen technische strategie voor het uitlijnen op het nieuwe model van de opslagplaats 6.5 wordt beschreven, zodat naar de nieuwe locaties wordt verwezen voor inhoud die zich eerder in de map /etc bevond. Een extra veld Notities biedt een extra handige context.
