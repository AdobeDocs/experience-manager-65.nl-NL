---
title: Problemen met MSM en veelgestelde vragen oplossen
description: Kom te weten hoe te om de gemeenschappelijkste MSM-verwante kwesties problemen op te lossen en antwoorden op de gemeenschappelijkste MSM-verwante vragen te krijgen.
feature: Multi Site Manager
role: Admin
exl-id: 23f3391b-5ce3-48e1-ab27-a37737778089
solution: Experience Manager, Experience Manager Sites
source-git-commit: 3aa55b88f589749fb49d5ff46340b0912d490157
workflow-type: tm+mt
source-wordcount: '762'
ht-degree: 0%

---

# Problemen met MSM en veelgestelde vragen oplossen {#troubleshooting-msm}

## Eerste stappen voor probleemoplossing {#first-steps}

Als u ervaart wat u denkt is onjuist gedrag of een fout in MSM, alvorens en het gedetailleerde oplossen van problemen zeker te zijn:

* Controleer [ Veelgestelde vragen MSM ](#faq) aangezien uw problemen of vragen daar kunnen reeds worden gericht.
* Controleer het [ MSM beste praktijkartikel ](msm-best-practices.md) aangezien verscheidene uiteinden daar samen met verduidelijkingen van sommige misconcepties worden aangeboden.

## Geavanceerde informatie over uw blauwdruk en status van Live Copy zoeken {#advanced-info}

MSM registreert verscheidene servers die met selecteurs op middel URLs kunnen worden gevraagd. Deze worden gebruikt door UI maar kunnen ook direct worden gevraagd om direct extra gecomputeriseerde MSM statussen voor uw pagina&#39;s te zien:

1. `http://<host>:<port>/content/path/to/bluprint/page.blueprint.json?&maxSize=500&advancedStatus=true&returnRelationships=true&msm%3Atrigger=ROLLOUT`
   * Gebruik deze optie op een blauwdrukpagina om de lijst op te halen met alle Live-kopieën die eraan zijn gekoppeld, met extra statusinformatie voor Live Copy.
   * bijvoorbeeld:
     `http://localhost:4502/content/wknd/language-masters/en.blueprint.json?&maxSize=500&advancedStatus=true&returnRelationships=true&msm%3Atrigger=ROLLOUT`


1. `http://<host>:<port>/content/path/to/livecopy/page.msm.json`
   * Gebruik deze optie op Live Copy-pagina&#39;s om geavanceerde informatie op te halen over de verbinding met de bijbehorende pagina&#39;s. Als de pagina geen live kopie is, wordt er niets geretourneerd.
   * bijvoorbeeld:
     `http://localhost:4502/content/wknd/ca/en.msm.json`

Deze servers genereren FOUTOPSPORING-logberichten via het logbestand `com.day.cq.wcm.msm` dat ook nuttig kan zijn.

## MSM-specifieke informatie in de gegevensopslagruimte controleren {#checking-repo}

De vroegere servlets teruggekeerde gegevens verwerkte die informatie op de MSM-specifieke knopen en de mixins wordt gebaseerd. De informatie wordt op de volgende manier in de opslagplaats opgeslagen.

* `cq:LiveSync` mixintype
   * Deze wordt ingesteld op `jcr:content` -knooppunten en definieert de basis van Live Copy-pagina&#39;s.
   * Deze pagina&#39;s hebben een `cq:LiveSyncConfig` onderliggend knooppunt van het type `cq:LiveCopy` dat standaard- en verplichte informatie over Live Copy bevat via de volgende eigenschappen:
      * `cq:master` verwijst naar de pagina met vervagingen van de Live kopie.
      * `cq:rolloutConfigs` geeft de actieve rollout-configuraties aan die op Live Copy zijn toegepast.
      * `cq:isDeep` is true als de onderliggende pagina&#39;s van deze hoofdpagina van Live Copy zijn opgenomen in de live kopie.
* `cq:LiveRelationship` mixintype
   * Elke Live Copy-pagina heeft een dergelijk mixintype op het `jcr:content` -knooppunt.
   * Als dit niet het geval is, is de pagina op een bepaald punt losgekoppeld of handmatig gemaakt via de ontwerpinterface buiten een actie Live Copy (maken of uitrollen).
* `cq:LiveSyncCancelled` mixintype
   * Toegevoegd aan `jcr:content` knooppunten van Live Copy-pagina&#39;s die zijn opgeschort.
   * Als de opschorting ook van kracht is voor onderliggende pagina&#39;s, wordt een eigenschap `cq:isCancelledForChildren` ingesteld op true op hetzelfde knooppunt.

De informatie aanwezig in deze eigenschappen zou in UI moeten worden weerspiegeld, nochtans wanneer het oplossen van problemen het kan nuttig zijn om gedrag MSM direct in de bewaarplaats waar te nemen aangezien de acties MSM voorkomen.

Kennis van die eigenschappen kan ook nuttig zijn om een query uit te voeren op uw opslagplaats en om te kijken naar sets pagina&#39;s die in bepaalde staten voorkomen. Bijvoorbeeld:

* `select * from cq:LiveSync` retourneert alle hoofdpagina&#39;s van Live Copy.

## Veelgestelde vragen {#faq}

Hier volgen enkele veelgestelde vragen over MSM en Live Copy.

### Waarom worden sommige eigenschappen (bijvoorbeeld titel, annotaties) niet bijgewerkt tijdens een MSM-rollout? {#missing-properties}

De acties van de synchronisatie MSM zijn hoogst configureerbaar. Welke eigenschappen of componenten tijdens rollouts direct worden gewijzigd hangt van de eigenschappen van die configuraties af.

Zie [ MSM Beste praktijken ](msm-best-practices.md) voor meer informatie over dit onderwerp.

### Hoe kan ik rollout toestemmingen voor een groep auteurs verwijderen? {#remove-rollout-permissions}

Er is geen **voorrecht van 0} rollout {dat voor AEM hoofden (gebruikers of groepen) kan worden geplaatst of worden verwijderd.**

Als alternatief kunt u:

* Pas het product UI aan om de acties van de Output voor een bepaalde principal te verbergen.
* Verwijder schrijfrechten uit de Live Copy-structuur voor auteurs die niet mogen uitrollen.

### Waarom zie ik Live Copy-pagina&#39;s met het achtervoegsel &quot;_msm_moving&quot;? {#moved-pages}

Als een pagina met een blauwdruk wordt uitgevouwen, wordt de pagina Live kopie bijgewerkt of wordt een nieuwe pagina Live kopie gemaakt als deze nog niet bestaat. Bijvoorbeeld wanneer het voor de eerste keer wordt uitgerold of de Live Copy-pagina handmatig is verwijderd.

In dit laatste geval echter, als er een pagina zonder de eigenschap `cq:LiveRelationship` met dezelfde naam bestaat, wordt de naam van deze pagina gewijzigd voordat de pagina Live kopie wordt gemaakt.

Standaard wordt bij de rollout een gekoppelde Live Copy-pagina verwacht, waarop de updates van de blauwdrukken worden uitgevoerd. Of er wordt helemaal geen pagina verwacht wanneer er een Live Copy-pagina wordt gemaakt.

Als er een &quot;zelfstandige&quot; pagina wordt gevonden, kiest MSM ervoor de naam van deze pagina te wijzigen en een aparte, gekoppelde Live Copy-pagina te maken.

Zulk een standalone pagina in Levende subtree van het Exemplaar is typisch het resultaat van a **ontkoppel** verrichting, of de vroegere Levende pagina van het Exemplaar werd manueel geschrapt door een auteur en toen opnieuw gecreeerd met de zelfde naam.

Om dit te vermijden, gebruik Levend Exemplaar **Uitstel** eigenschap in plaats van **losmaken**. Meer details op **ontkoppelen** actie kan in [ dit artikel worden gevonden.](msm-livecopy.md)
