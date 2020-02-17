---
title: Planning
seo-title: Planning
description: Wat u moet weten om voor uw test te plannen
seo-description: Wat u moet weten om voor uw test te plannen
uuid: 29b1127a-da85-46ed-98e7-1c983eb40cfe
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: testing
content-type: reference
discoiquuid: 12268c43-93f9-42c1-8dd7-f17f9ae2219b
translation-type: tm+mt
source-git-commit: a3c303d4e3a85e1b2e794bec2006c335056309fb

---


# Planning{#planning}

In dit document wordt beschreven wat u moet weten om uw test te plannen. Bovendien moet u deze vragen beantwoorden voordat u de tests uitvoert:

* [Welke testomgevingen zijn nodig?](/help/sites-developing/test-environments.md)
* [De testcase definiëren](/help/sites-developing/test-cases.md)
* [Testen - wanneer en met wie?](/help/sites-developing/when-who.md)

## Before You Start {#before-you-start}

Voordat u begint met de eigenlijke analyse en definitie van tests, bekijkt u de volgende informatie:

**AEM Architectuur** - zie Basisconcepten om zich aan de architectuur en de basisbeginselen van AEM voor te stellen.

**Documentatie** - Zie om het even welke documentatiesecties, of hoe te artikelen, voor verdere informatie.

**Basisprincipes van tests** - U moet op de hoogte zijn van de basisbeginselen van softwaretests en kwaliteitsborging. U hebt bij voorkeur ervaring met het testen van projecten.

Er zijn veel websites, boeken en cursussen die met dergelijke beginselen te maken hebben en die zullen dus niet in dit document in detail worden behandeld.

**Veronderstellingen om te vermijden** - De grootste veronderstelling (die regelmatig wordt gemaakt) is dat uw website miljoenen verzoeken elke dag zal moeten onderhouden. In bepaalde omstandigheden kan dit waar zijn, maar het kan niet worden aangenomen.

Hoewel toekomstige getallen niet met 100% nauwkeurigheid kunnen worden voorspeld, geeft het observeren van uw bestaande site en het ervaren verkeer een goede indicatie. U kunt ramingen dan afhankelijk maken van de factor waardoor u verwacht/hoopt het verkeer zal stijgen.

**Toezegging aan kwaliteit** - Het is van het grootste belang dat iedereen die test neutraal blijft en simpelweg de resultaten van uitgevoerde tests rapporteert.

Het is de verantwoordelijkheid van de projectbeheerder om afhankelijk van de resultaten een besluit te nemen over een actie of acties.

**Betrokken** worden - Hoewel het de verantwoordelijkheid van de projectbeheerder is om ervoor te zorgen dat alle partijen volledig betrokken zijn bij alle vergaderingen (status, workshops, enz.), moet u ook proberen om zo vroeg mogelijk in de projectcyclus betrokken te raken, inclusief de processen voor het verzamelen van informatie en het analyseren van de vereisten.

**De klant** erbij betrekken - Bij een vergelijkbaar thema probeert u de klant (waar mogelijk) te betrekken bij het definiëren van uw testcase en -plan.

## Typen tests {#types-of-tests}

Er zijn verschillende standaardclassificaties van tests die geschikt zijn voor gebruik bij het testen van een AEM-project. U zou met deze moeten vertrouwd zijn om te beslissen welke u zult gebruiken:

>[!NOTE]
>
>Deze worden vermeld in chronologische volgorde van toepassing.

**Eenheden Tests** - Tests (gewoonlijk) die door het ontwikkelingsteam worden uitgevoerd om ervoor te zorgen dat de afzonderlijke elementen zich correct gedragen - zij het afzonderlijk.

**Integratietests** - Tests modules indien gecombineerd. Deze tests worden uitgevoerd na het testen van de eenheid, maar vóór het testen van het systeem.

**Rooktests** : dit zijn snelle en vuile tests die worden gebruikt om te bewijzen dat de software actief is en dat functionaliteit op hoog niveau beschikbaar is. De details worden niet getest.

**Functionele tests** - Deze worden gebruikt om de functionaliteit van de software te testen. Er wordt een serie tests ontworpen om alle functionele details te bestrijken, zowel met verwachte als met onverwachte en/of onjuiste input.

Zwartboxtests zijn functionele tests van een complete eenheid/onderdeel/module, uitgevoerd zonder kennis van de interne werking van het element in kwestie.

**Systeemtests** : deze testen het hele systeem nadat het volledig is geïntegreerd en op een geschikt platform is geïnstalleerd.

Ze testen de functionaliteit op een black-box-basis.

**Prestatietests** - Prestatietests zijn cruciaal bij het testen van AEM.

Deze worden gebruikt om de prestaties onder verschillende omstandigheden te illustreren:

* Normaal

   Voorwaarden die de locatie zal ervaren, zijn bijvoorbeeld 90% van de tijd. Bijvoorbeeld wanneer slechts een deel van de auteurs het systeem gebruikt.

* Piek

   Voorwaarden die in verband met bijzondere omstandigheden voor een verhoudingsgewijs korte tijd zullen worden gehanteerd; bijvoorbeeld wanneer alle auteurs het systeem gelijktijdig gebruiken of wanneer nieuwe inhoud wordt gepubliceerd en een groter aantal bezoekers uw site bekijken.

* Extreem

   Kan worden gebruikt om de voorspelling van de prestaties na te bootsen wanneer er nieuwe, bijzonder interessante inhoud op uw website wordt gepubliceerd. Dan kan een extreme piek worden gezien - hoewel dit niet altijd volledig voorspelbaar is.

   Deze omstandigheden worden soms waargenomen wanneer tickets voor specifieke gebeurtenissen beschikbaar worden gesteld, of wanneer voor het eerst een veelverwachte website wordt gepubliceerd.

De resultaten worden vervolgens gebruikt om de toepassing af te stemmen.

**Stresstests** - Stresstests worden uitgevoerd om te bevestigen hoe een onderdeel of toepassing zich gedraagt onder extreme omstandigheden. Deze tests worden met name gebruikt om aan te tonen hoe het gedrag verslechtert, wanneer het element zal mislukken - en hoe.

**Regressietests** - Regressietests worden gebruikt om te bevestigen dat de functionaliteit die al in een vorige versie van de software is bewezen, nog steeds correct werkt.

Regressietests zijn (indien mogelijk) goede kandidaten voor automatisering om ervoor te zorgen dat ze snel en consistent kunnen worden herhaald.

**Acceptatietests** - Acceptatietests zijn een speciale categorie omdat ze worden gebruikt om aan te geven dat de klant het project accepteert.

De lijst van goedkeuringstests kan een combinatie van tests van de diverse hierboven vermelde categorieën bevatten, en wordt geselecteerd om te verifiëren dat het project aan de vereisten van de klant voldoet

Zie [Acceptatie en afmelding](/help/sites-developing/acceptance-signoff.md) voor meer informatie.

## Aan de slag {#getting-started}

Voordat u begint met uw gedetailleerde testcase en testplan, kunt u:

**Bepaal de doelstellingen** - bepaal uw doelstellingen op hoog niveau om als uitgangspunt voor verfijning te handelen aangezien het testen te werk gaat. U wilt:

* Test de functionaliteit volgens de gedetailleerde specificaties.
* Testprestaties volgens de [doelwaarden](/help/managing/best-practices-further-reference.md#key-performance-indicators-and-target-metrics).

onder andere.

**Verzamel verkeersstatistieken van de bestaande website** - Deze informatie kan uit de logboekdossiers worden gehaald - zie de Controle van Prestaties voor meer details.

Deze cijfers geven een indicatie van het huidige verkeer (volume en spread) op de bestaande website en kunnen worden gebruikt om een uitgangspunt te vormen voor de nieuwe website.

**Verzamel verkeersstatistieken van externe websites** - Indien mogelijk kunt u proberen om verkeersstatistieken van andere websites voor vergelijking te verzamelen, maar deze cijfers worden niet altijd gepubliceerd.

**Bevestig de Metriek** van het Doel - De metriek wordt gebruikt om kwantitatieve metingen voor de kwaliteit van de website te bepalen, aangezien zij de prestatiedoelstellingen vertegenwoordigen die moeten worden bereikt.

Zij zouden aan het begin van het project, samen met de klant moeten worden bepaald. Zie [Doelwaarden](/help/sites-developing/planning.md) voor meer informatie.
