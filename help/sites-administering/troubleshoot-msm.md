---
title: Problemen met MSM en veelgestelde vragen oplossen
description: Kom te weten hoe te om de gemeenschappelijkste MSM-verwante kwesties problemen op te lossen en antwoorden te krijgen de gemeenschappelijkste MSM-verwante vragen.
feature: Multi Site Manager
role: Admin
exl-id: 23f3391b-5ce3-48e1-ab27-a37737778089
source-git-commit: 289c4644063504ec3c8e02d930933ad7260600f0
workflow-type: tm+mt
source-wordcount: '758'
ht-degree: 0%

---

# Problemen met MSM en veelgestelde vragen oplossen {#troubleshooting-msm}

## Eerste stappen voor probleemoplossing {#first-steps}

Als u ervaart wat u denkt is onjuist gedrag of een fout in MSM, alvorens en het gedetailleerde oplossen van problemen zeker te zijn:

* Controleer de [Veelgestelde vragen over MSM](#faq) aangezien uw problemen of vragen daar reeds kunnen worden opgelost.
* Controleer de [MSM Best practices-artikel](msm-best-practices.md) daar wordt een aantal tips gegeven , samen met een aantal misvattingen .

## Geavanceerde informatie over uw blauwdruk en status van Live Copy zoeken {#advanced-info}

MSM registreert verscheidene servers die met selecteurs op middel URLs kunnen worden gevraagd. Deze worden gebruikt door UI maar kunnen ook direct worden gevraagd om direct extra gecomputeriseerde MSM statussen voor uw pagina&#39;s te zien:

1. `http://<host>:<port>/content/path/to/bluprint/page.blueprint.json?&maxSize=500&advancedStatus=true&returnRelationships=true&msm%3Atrigger=ROLLOUT`
   * Gebruik deze optie op een blauwdrukpagina om de lijst op te halen met alle Live-kopieën die eraan zijn gekoppeld, met extra statusinformatie voor Live Copy.
1. `http://<host>:<port>/content/path/to/livecopy/page.msm.json`
   * Gebruik deze optie op Live Copy-pagina&#39;s om geavanceerde informatie op te halen over de verbinding met de bijbehorende pagina&#39;s. Als de pagina geen live kopie is, wordt er niets geretourneerd.

Deze servers genereren FOUTOPSPORING-logberichten via de `com.day.cq.wcm.msm` registreerapparaat dat ook nuttig kan zijn.

## MSM-specifieke informatie in de gegevensopslagruimte controleren {#checking-repo}

De vroegere servlets teruggekeerde gegevens verwerkte die informatie op de MSM-specifieke knopen en de mixins wordt gebaseerd. De informatie wordt op de volgende manier in de opslagplaats opgeslagen.

* `cq:LiveSync` mixintype
   * Deze is ingesteld op `jcr:content` knooppunten en definieer de basis van Live Copy-pagina&#39;s.
   * Deze pagina&#39;s bevatten een `cq:LiveSyncConfig` onderliggende node van type `cq:LiveCopy` die standaard- en verplichte informatie over Live Copy zal bevatten via de volgende eigenschappen:
      * `cq:master` verwijst naar de pagina met de blauwdruk van de Live kopie.
      * `cq:rolloutConfigs` Hiermee worden actieve rollout-configuraties aangegeven die zijn toegepast op Live Copy.
      * `cq:isDeep` is true als de onderliggende pagina&#39;s van deze hoofdpagina van Live Copy zijn opgenomen in de Live Copy.
* `cq:LiveRelationship` mixintype
   * Op elke Live Copy-pagina staat een dergelijk mixtype `jcr:content` knooppunt.
   * Als dit niet het geval is, is de pagina op een bepaald punt losgekoppeld of handmatig gemaakt via de ontwerpinterface buiten een actie Live Copy (maken of rollout).
* `cq:LiveSyncCancelled` mixintype
   * Toegevoegd aan `jcr:content` knooppunten van Live Copy-pagina&#39;s die zijn opgeschort.
   * Als de suspensie ook voor onderliggende pagina&#39;s effectief is, moet u `cq:isCancelledForChildren` eigenschap wordt ingesteld op true op hetzelfde knooppunt.

De informatie aanwezig in deze eigenschappen zou in UI moeten worden weerspiegeld, nochtans wanneer het oplossen van problemen het kan nuttig zijn om gedrag MSM direct in de bewaarplaats waar te nemen aangezien de acties MSM voorkomen.

Kennis van die eigenschappen kan ook nuttig zijn om een query uit te voeren op uw opslagplaats en om te kijken welke paginasets zich in bepaalde staten bevinden. Bijvoorbeeld:

* `select * from cq:LiveSync` Hiermee worden alle hoofdpagina&#39;s van Live Copy geretourneerd.

## Veelgestelde vragen {#faq}

Hier volgen enkele veelgestelde vragen over MSM en Live Copy.

### Waarom worden sommige eigenschappen (bijvoorbeeld titel, annotaties) niet bijgewerkt tijdens een MSM-rollout? {#missing-properties}

De acties van de synchronisatie MSM zijn hoogst configureerbaar. Welke eigenschappen of componenten tijdens rollouts worden gewijzigd hangt direct van eigenschappen van die configuraties af.

Zie [dit artikel](msm-best-practices.md) voor meer informatie over dit onderwerp.

### Hoe kan ik rollout toestemmingen voor een groep auteurs verwijderen? {#remove-rollout-permissions}

Er is geen **rollout** bevoegdheden die kunnen worden ingesteld of verwijderd voor AEM hoofden (gebruikers of groepen).

Als alternatief kunt u:

* Pas het product UI aan om de acties van de Output voor een bepaalde principal te verbergen.
* Verwijder schrijfrechten uit de Live Copy-structuur voor auteurs die niet mogen uitrollen.

### Waarom zie ik Live Copy-pagina&#39;s met het achtervoegsel &quot;_msm_moving&quot;? {#moved-pages}

Als een blauwdrukpagina wordt uitgevouwen, wordt de pagina Live kopie bijgewerkt of wordt er een nieuwe pagina Live kopie gemaakt als deze nog niet bestond (bijvoorbeeld wanneer de pagina voor de eerste keer wordt uitgevouwen of wanneer de pagina Live kopie handmatig is verwijderd).

In dit laatste geval echter, indien een pagina zonder `cq:LiveRelationship` Er bestaat al een eigenschap met dezelfde naam. De naam van deze pagina wordt overeenkomstig gewijzigd voordat de pagina Live Copy wordt gemaakt.

Standaard wordt bij de rollout een gekoppelde Live Copy-pagina verwacht, waarop de updates van de blauwdrukken worden uitgevoerd, of geen pagina bij, wanneer een Live Copy-pagina wordt gemaakt.

Als er een &quot;zelfstandige&quot; pagina wordt gevonden, kiest MSM ervoor de naam van deze pagina te wijzigen en een aparte, gekoppelde Live Copy-pagina te maken.

Een dergelijke zelfstandige pagina in een substructuur van Live Copy is doorgaans het resultaat van een **Loskoppelen** of de voormalige pagina Live Copy is handmatig verwijderd door een auteur en vervolgens opnieuw gemaakt met dezelfde naam.

Als u dit wilt vermijden, gebruikt u de Live kopie **Onderbreken** in plaats van **Loskoppelen**. Meer informatie over de **Loskoppelen** handeling in [dit artikel.](msm-livecopy.md)
