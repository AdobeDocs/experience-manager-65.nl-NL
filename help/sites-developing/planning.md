---
title: Planning
description: Leer wat je moet weten om te plannen voor het testen van Adobe Experience Manager.
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: testing
content-type: reference
exl-id: ed662279-0679-4ba3-b744-6649fb8dda17
solution: Experience Manager, Experience Manager Sites
feature: Developing
role: Developer
source-git-commit: 66db4b0b5106617c534b6e1bf428a3057f2c2708
workflow-type: tm+mt
source-wordcount: '979'
ht-degree: 0%

---

# Planning{#planning}

In dit document wordt beschreven wat u moet weten om uw test te plannen. Bovendien moet u deze vragen beantwoorden voordat u de tests uitvoert:

* [Welke testomgevingen zijn nodig?](/help/sites-developing/test-environments.md)
* [De testcase definiëren](/help/sites-developing/test-cases.md)
* [Testen - wanneer en met wie?](/help/sites-developing/when-who.md)

## Voordat u begint {#before-you-start}

Voordat u begint met de eigenlijke analyse en definitie van tests, bekijkt u de volgende informatie:

**AEM Architectuur** - zie Basisconcepten om zich aan de architectuur en basisbeginselen van AEM te introduceren.

**Documentatie** - zie om het even welke documentatiesecties, of hoe te artikelen, voor verdere informatie.

**BasisBeginselen van het Testen** - u zou van de basisbeginselen van het Testen van de Software en de Verzekering van de Kwaliteit bewust moeten zijn. U hebt bij voorkeur ervaring met het testen van projecten.

Er zijn veel websites, boeken en cursussen die met dergelijke beginselen te maken hebben en die zullen dus niet in dit document in detail worden behandeld.

**Veronderstellingen om te vermijden** - de grootste veronderstelling is dat uw website miljoenen verzoeken elke dag moet onderhouden. In bepaalde omstandigheden kan dit waar zijn, maar het kan niet worden aangenomen.

Hoewel toekomstige getallen niet met 100% nauwkeurigheid kunnen worden voorspeld, geeft het observeren van uw bestaande site en het ervaren verkeer een goede indicatie. U kunt ramingen dan afhankelijk maken van de factor waardoor u verwacht/hoopt het verkeer zal stijgen.

**Bevestiging aan Kwaliteit** - het is van het grootste belang dat iedereen die test neutraal blijft en eenvoudig de resultaten van gemaakte tests meldt.

Het is de verantwoordelijkheid van de projectbeheerder om afhankelijk van de resultaten een besluit te nemen over een actie of acties.

**wordt Betrokken** - hoewel het de verantwoordelijkheid van de Projectleider is om ervoor te zorgen dat alle partijen volledig bij om het even welke vergaderingen (status, workshops, etc.) worden betrokken u zou ook moeten proberen om zo vroeg mogelijk in de projectcyclus, met inbegrip van de informatieinzameling en vereiste analyseprocessen te worden betrokken.

**betreed de Klant** - op een gelijkaardig thema, probeer om de klant (waar mogelijk) te betrekken wanneer het bepalen van uw testgevallen en plan.

## Typen tests {#types-of-tests}

Er zijn verschillende standaardclassificaties van tests die geschikt zijn voor gebruik bij het testen van een AEM project. U zou met deze moeten vertrouwd zijn om te beslissen welke u zult gebruiken:

>[!NOTE]
>
>Deze worden vermeld in chronologische volgorde van toepassing.

**de Tests van Eenheden** - Tests (gewoonlijk) die door het ontwikkelingsteam worden gemaakt om ervoor te zorgen dat de individuele elementen correct - zij in isolatie gedragen.

**de Tests van de Integratie** - Test modules wanneer gecombineerd. Deze tests worden uitgevoerd na het testen van de eenheid, maar vóór het testen van het systeem.

**de Tests van de Rook** - Dit zijn snelle en vuile tests die worden gebruikt om te bewijzen dat de software loopt en de functionaliteit op hoog niveau beschikbaar is. De details worden niet getest.

**Functionele Tests** - Deze worden gebruikt om de functionaliteit van de software te testen. Er wordt een serie tests ontworpen om alle functionele details te bestrijken, zowel met verwachte als met onverwachte en/of onjuiste input.

Zwartboxtests zijn functionele tests van een complete eenheid/onderdeel/module, uitgevoerd zonder kennis van de interne werking van het element in kwestie.

**Tests van het Systeem** - Deze test het volledige systeem zodra het volledig is geïntegreerd en op een geschikt platform geïnstalleerd.

Ze testen de functionaliteit op een black-box basis.

**Tests van Prestaties** - De tests van Prestaties zijn essentieel wanneer het testen van AEM.

Deze worden gebruikt om de prestaties onder verschillende omstandigheden te illustreren:

* Normaal

  Voorwaarden die de locatie zal ervaren, zijn bijvoorbeeld 90% van de tijd. Bijvoorbeeld wanneer slechts een deel van de auteurs het systeem gebruikt.

* Piek

  Voorwaarden die proportioneel kort zullen worden ervaren als gevolg van speciale omstandigheden, bijvoorbeeld wanneer alle auteurs het systeem gelijktijdig gebruiken of wanneer nieuwe inhoud wordt gepubliceerd en een groter aantal bezoekers uw site bekijken.

* Extreem

  Kan worden gebruikt om de voorspelling van de prestaties na te bootsen wanneer er nieuwe, bijzonder interessante inhoud op uw website wordt gepubliceerd. Dan kan een extreme piek worden gezien - hoewel dit niet altijd volledig voorspelbaar is.

  Deze omstandigheden worden soms waargenomen wanneer tickets voor specifieke gebeurtenissen beschikbaar worden gesteld, of wanneer voor het eerst een veelverwachte website wordt gepubliceerd.

De resultaten worden vervolgens gebruikt om de toepassing af te stemmen.

**de Tests van de Stress** - de tests van de Stress worden gemaakt om te bevestigen hoe een component of een toepassing zich onder extreme omstandigheden gedraagt. Deze tests worden met name gebruikt om aan te tonen hoe het gedrag verslechtert, wanneer het element zal mislukken - en hoe.

**Tests van de Regressie** - de tests van de Regressie worden gebruikt om te bevestigen dat de functionaliteit reeds in een vorige versie van de software wordt bewezen nog correct werkt.

Regressietests zijn (indien mogelijk) goede kandidaten voor automatisering om ervoor te zorgen dat ze snel en consistent kunnen worden herhaald.

**Tests van de Aanvaarding** - de Tests van de Aanvaarding zijn een speciale categorie aangezien zij worden gebruikt om op de aanvaarding van de klant van het project te wijzen.

De lijst met acceptatietests kan een combinatie van tests uit de bovenstaande categorieën bevatten en wordt geselecteerd om te controleren of het project aan de vereisten van de klant voldoet

Zie [ Aanvaarding en Teken-weg ](/help/sites-developing/acceptance-signoff.md) voor meer details.

## Aan de slag {#getting-started}

Voordat u begint met uw gedetailleerde testcase en testplan, kunt u:

**bepaal de doelstellingen** - bepaal uw doelstellingen op hoog niveau om als uitgangspunt voor verfijnen te handelen aangezien het testen te werk gaat. U wilt:

* Test de functionaliteit volgens de gedetailleerde specificaties.
* De Prestaties van de test volgens de [ Metriek van het Doel ](/help/managing/best-practices-further-reference.md#key-performance-indicators-and-target-metrics).

onder andere.

**verzamel verkeersstatistieken van de bestaande website** - Deze informatie kan uit de logboekdossiers worden gehaald - zie de Controle van Prestaties voor meer details.

Deze cijfers geven een indicatie van het huidige verkeer (volume en spread) op de bestaande website en kunnen worden gebruikt om een uitgangspunt te vormen voor de nieuwe website.

**verzamel verkeersstatistieken van externe websites** - als mogelijk u verkeersstatistieken van andere websites voor vergelijking kunt proberen te verzamelen, maar deze cijfers worden niet altijd gepubliceerd.

**bevestig de Metriek van het Doel** - de Metriek worden gebruikt om kwantitatieve metingen voor de kwaliteit van de website te bepalen, aangezien zij de prestatiedoelstellingen vertegenwoordigen die moeten worden bereikt.

Zij zouden aan het begin van het project, samen met de klant moeten worden bepaald. Zie [ Metriek van het Doel ](/help/sites-developing/planning.md) voor meer informatie.
