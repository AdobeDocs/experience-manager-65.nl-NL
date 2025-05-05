---
title: Aanbevolen MSM-procedures
description: Zoek naar beste praktijken die door Adobe engineering en adviesteams worden gecompileerd helpen aan de slag met de AEM Multi-Site Manager.
topic-tags: site-features, best-practices
feature: Multi Site Manager
exl-id: 3fedc1ba-64f5-4fbe-9ee5-9b96b75dda58
solution: Experience Manager, Experience Manager Sites
role: Admin
source-git-commit: eae057caed533ef16bb541b4ad41b8edd7aaa1c7
workflow-type: tm+mt
source-wordcount: '1599'
ht-degree: 0%

---

# Aanbevolen MSM-procedures{#msm-best-practices}

## Algemeen {#general}

MSM is een configureerbaar framework voor het automatiseren van de implementatie van inhoud. Bij implementaties gaat het vaak om grote delen van een website en meerdere organisaties en geografische gebieden. Daarom wordt u ten zeerste aangeraden MSM-implementaties net zo zorgvuldig te plannen als uw website:

* Zorgvuldig **planstructuur en inhoudsstromen** alvorens implementatie te beginnen.
* **houd de hoeveelheid levende exemplaren tot een minimum.** Live kopieën verwerken is een resource-intensieve taak. Hoe meer live kopieën er in uw systeem zijn, hoe beter de prestaties kunnen worden beïnvloed: van het verwerken van interne live copy-indexen, van live copy-bewerkingen, zoals rollouts, tot UI-bewerkingen, zoals het weergeven van live copy-relaties in de Sites Admin-naslagenrail. De beste manier is om live kopieën te maken van sites of vertakkingen van een site, waarbij de live-kopieerrelaties worden overgeërfd op pagina&#39;s in de site of vertakking. Vermijd het maken van individuele live kopieën voor pagina&#39;s in een site of vertakking wanneer de volledige structuur in een live kopie kan worden gemaakt.
* **pas zo veel zoals nodig aan, maar zo weinig mogelijk.** Hoewel MSM een hoge mate van aanpassing ondersteunt (bijvoorbeeld rollout-configuraties), kunt u de aanpassing meestal het beste minimaliseren door de prestaties, betrouwbaarheid en upgradebaarheid van uw website te minimaliseren.
* Vestig a **governance** model vroeg, en treed gebruikers dienovereenkomstig, om succes te verzekeren. Een beste praktijk van een governance standpunt moet **minimaliseren het gezag dat de lokale inhoudsproducenten** hebben om inhoud aan andere lokale gebruikers en hun respectieve levende exemplaren toe te wijzen/te verbinden. Dit komt omdat onbestuurde, geketende overerving de complexiteit van een MSM-structuur aanzienlijk kan verhogen en de prestaties en betrouwbaarheid ervan in gevaar kan brengen.

* Zodra een plan voor uw structuur, inhoudsstromen, automatisering en bestuur bestaat - **prototype en test grondig uw systeem**, alvorens levende implementatie te beginnen.
* Houd in mening dat **Adobe Consulting en de belangrijke Integrators van het Systeem** diepe ervaring planning en het uitvoeren van inhoudsautomatisering met MSM hebben, zodat kunnen zij u zowel helpen met uw project MSM en door zijn volledige implementatie begonnen worden.

>[!NOTE]
>
>Meer informatie over het werken met MSM is te vinden in de artikelen in de Knowledge Base:
>
>* [ het Oplossen van problemen MSM en Veelgestelde vragen ](troubleshoot-msm.md)
>

>[!NOTE]
>
>U kunt de [ component van de Verwijzing ](/help/sites-authoring/default-components-foundation.md#reference) ook gebruiken om één enkele pagina of paragraaf opnieuw te gebruiken. Houd echter rekening met:
>
>* MSM is flexibeler en staat fijnkorrelige controle over toe welke inhoud wordt gesynchroniseerd en wanneer.
>* {de componenten van 0} Kern [&#128279;](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/introduction.html?lang=nl-NL) worden nu geadviseerd over de stichtingscomponenten.
>

## Live Copy-bronnen en configuraties voor blauwdrukken {#live-copy-sources-and-blueprint-configurations}

Houd in mening dat een levend exemplaar gebruikend of [ regelmatige pagina&#39;s ](/help/sites-administering/msm-livecopy.md#creating-a-live-copy-of-a-page) of a [ de configuratie van de blauwdruk ](/help/sites-administering/msm-livecopy.md#creating-a-live-copy-of-a-site-from-a-blueprint-configuration) kan worden gecreeerd. Beide zijn geldige gebruiksgevallen.

De extra voordelen van het gebruiken van een blauwdrukconfiguratie zijn dat zij:

* Toestaan de auteur om de **optie van de Uitvoer** op een blauwdruk te gebruiken - aan (uitdrukkelijk) duw wijzigingen aan levende exemplaren die van dit blauwdruk erven.
* Toestaan de auteur om **te gebruiken creeer Plaats**; dit staat de gebruiker toe om talen gemakkelijk te selecteren en de structuur van het levende exemplaar te vormen.
* Definieer een standaardrollout-configuratie voor live kopieën die een relatie hebben met de blauwdruk.

Als er niet naar een blauwdrukconfiguratie wordt verwezen, kunnen rollouts alleen worden geïnitieerd vanuit de live kopieën zelf, waarbij inhoud van de bron wordt opgehaald.

Wanneer het creëren van een plaats met levende kopie, is het voordelig om blauwdrukconfiguraties tot stand te brengen om de beschikbaarheid van de volledige MSM eigenschapreeks te verzekeren.

>[!NOTE]
>
>CUG&#39;s op het tabblad Machtigingen kunnen niet worden geïmplementeerd voor actieve kopieën van blauwdrukken. Plan dit rond wanneer het vormen van Levend Exemplaar.

## Componenten en containersynchronisatie {#components-and-container-synchronization}

In het algemeen, is de rollout regel in MSM betreffende de synchronisatie van componenten:

* Componenten worden gesynchroniseerd met alle bronnen in de blauwdruk.
* Containers synchroniseren alleen de huidige bron.

Dit betekent dat componenten als aggregaat worden behandeld, en in een rollout worden de component zelf en al zijn kinderen vervangen met die in de blauwdrukken. Dit betekent dat als een bron lokaal aan een dergelijke component wordt toegevoegd, deze bij rollout verloren gaat aan de inhoud van de blauwdruk.

Om het nesten van componenten te steunen zodat de plaatselijk toegevoegde componenten in een rollout worden gehandhaafd, moet de component als container worden verklaard. Als voorbeeld, wordt standaard parsys verklaard als container zodat kan het plaatselijk-toegevoegde inhoud steunen.

>[!NOTE]
>
>Voeg de eigenschap `cq:isContainer` toe aan de component om deze aan te wijzen als een container.

## Site maken {#create-site}

U ziet dat AEM twee hoofdbenaderingen heeft voor het maken van live kopieën:

* Wanneer [ creërend een Levend Exemplaar ](/help/sites-administering/msm-livecopy.md#creating-a-live-copy-of-a-page)

  Dit kan als generischere benadering worden beschouwd, toestaand u om levende exemplaren van om het even welke pagina tot stand te brengen. De inhoudsstructuur van een live kopie komt exact overeen met de bron.

* Wanneer [ het creëren van een Plaats ](/help/sites-administering/msm-livecopy.md#creating-a-live-copy-of-a-site-from-a-blueprint-configuration)

  Dit is een meer gespecialiseerde benadering, vooral voor het creëren van websites met een meertalige structuur.

Houd rekening met het volgende wanneer u een site maakt:

* Om een plaats tot stand te brengen, hebt u de configuratie van de a [ blauwdruk ](/help/sites-administering/msm-livecopy.md#managing-blueprint-configurations) nodig.
* Als u wilt dat de taalpaden op een nieuwe site kunnen worden geselecteerd, moeten de overeenkomstige taalwortels in de blauwdruk (bron) aanwezig zijn.
* Zodra a [ nieuwe plaats is gecreeerd als levende exemplaar ](/help/sites-administering/msm-livecopy.md#creating-a-live-copy-of-a-site-from-a-blueprint-configuration) (gebruikend **creeer**, dan **Plaats**), zijn de eerste twee niveaus van dit levende exemplaar *ondiep*. Onderliggende items van de pagina behoren niet tot de live-relatie, maar de rollout neemt wel af als een live-relatie wordt gevonden die overeenkomt met de trigger.

  Het helpt voorkomen:

   * handmatig talen toevoegen in de blauwdruk (onder het eerste niveau)
   * handmatig inhoud toevoegen direct onder de hoofdmap van de taal,
   * leidt er niet toe dat deze nieuwe inhoud automatisch bij de rollout naar de live kopie wordt overgedragen.

## MSM- en meertalige websites {#msm-and-multilingual-websites}

MSM kan op twee manieren helpen bij het maken van meertalige websites:

* Bij het maken van taalstramienen.

   * Terwijl MSM zelf **geen inhoudsomzetting** verstrekt, kan het met derdevertaalschakelaars worden geïntegreerd die doen. Let op:

      * Met MSM kunt u overname op pagina- en/of componentniveau annuleren. Zo voorkomt u bij de volgende rollout dat vertaalde inhoud (van een live kopie met nog niet-vertaalde inhoud van een blauwdruk) wordt overschreven.
      * Sommige vertalingsconnectors van derden automatiseren dit beheer van MSM-overerving.

        Vraag uw vertaalservicebureau om meer informatie.

      * Een alternatieve benadering voor het maken en vertalen van taalmeesters is het gebruik van taalkopieën in combinatie met AEM niet-elektronische vertaalintegratiekader.

* Bij het uitrollen van inhoud van taalmeesters.

   * Bijvoorbeeld, van de Franse taalmeester aan landspecifieke plaatsen, zoals Frankrijk/Frans, Canada/Frans, Zwitserland/Frans.

Voor meer informatie zie [ Vertaal Inhoud voor Meertalige Plaatsen ](/help/sites-administering/translation.md) en [ de Beste praktijken van de Vertaling ](/help/sites-administering/tc-bp.md).

## Structuurwijzigingen en rollouts {#structure-changes-and-rollouts}

Wijzigingen in de inhoudsstructuur in een blauwdruk-/bronstructuur worden anders weerspiegeld in een live kopie. Dit is afhankelijk van het wijzigingstype:

* **Creërend** nieuwe pagina&#39;s in een blauwdruk zullen in overeenkomstige pagina&#39;s resulteren die in levende exemplaren na rollout met de standaardrollout configuratie worden gecreeerd.

* **het Schrappen van** pagina&#39;s in een blauwdruk zal in overeenkomstige pagina&#39;s resulteren die van levende exemplaren na rollout met standaard rollout configuratie worden geschrapt.

* **het bewegen** pagina&#39;s in een blauwdruk zal **&#x200B;**&#x200B;niet in overeenkomstige pagina&#39;s resulteren die in levende exemplaren na rollout met standaard rollout configuratie worden bewogen:

   * De reden voor dit gedrag is dat een paginabeweging impliciet een pagina-verwijdering bevat. Dit kan mogelijk leiden tot onverwacht gedrag bij het publiceren, omdat bij het verwijderen van pagina&#39;s bij de auteur de bijbehorende inhoud bij het publiceren automatisch wordt gedeactiveerd. Dit kan ook een domino-effect hebben op verwante items zoals koppelingen, bladwijzers en andere.
   * Inhoudsovererving op de respectievelijke pagina&#39;s met live kopieën wordt bijgewerkt om de nieuwe locatie van de bronnen in de blauwdruk te weerspiegelen.
   * Houd rekening met de volgende aanbevolen procedures om te zorgen dat een pagina van een blauwdruk naar live kopieën wordt verplaatst:

>[!NOTE]
>
>Dit zal slechts met [ op de trekker van de Output ](/help/sites-administering/msm-sync.md#rollout-triggers) werken.

* Een aangepaste rollout-configuratie maken:

   * Deze nieuwe configuratie moet de actie omvatten:

     `PageMoveAction`

     Voeg geen andere acties aan deze configuratie toe.

* Plaats de nieuwe configuratie:

   * Als u de pagina volledig wilt uitrollen, verplaatst u de pagina&#39;s terwijl u de desbetreffende pagina&#39;s op hun oude locatie in de live kopie verwijdert:

      * Plaats de nieuw gecreëerde configuratie vóór de standaardrollout configuratie.

        De standaardrollout configuratie zal ervoor zorgen om de pagina&#39;s in hun oude plaats te schrappen.

   * Als u de pagina wilt uitrollen, verplaatst u de pagina&#39;s terwijl de respectievelijke pagina&#39;s op hun oude locatie in de live kopieën blijven staan (de inhoud wordt in feite gedupliceerd):

      * Plaats de nieuw gecreëerde configuratie na de standaardrollout configuratie.

        Zo voorkomt u dat inhoud wordt verwijderd uit de live kopie of gedeactiveerd uit publicatie.

## Rollen aanpassen {#customizing-rollouts}

MSM-rollout-configuraties zijn in hoge mate aanpasbaar. Het automatiseren van rollouts kan verreikende gevolgen hebben. Als beste praktijken, zou u ** zorgvuldig vóór, bijvoorbeeld moeten plannen:

* het automatiseren van rollouts; bijvoorbeeld, met [ onModify trekkers ](#onmodify),
* het aanpassen [ knooptypes/eigenschappen ](#node-types-properties),
* volgende workflows starten,
* inhoud activeren als onderdeel van rollouts.

### onModify {#onmodify}

Wanneer het gebruiken van de [ rollout trekker ](/help/sites-administering/msm-sync.md#rollout-triggers) `onModify` zou u moeten overwegen:

* Het automatiseren van rollouts met `onModify` trekkers kan een negatief effect op auteursprestaties hebben aangezien zij rollouts na *elke* pagineringswijziging teweegbrengen.

* Het rollout-resultaat kan afwijken van het verwachte resultaat:

   * U kunt de volgorde van de resulterende wijzigingsgebeurtenissen niet opgeven.
   * De op gebeurtenis-gebaseerde architectuur kan niet de opeenvolging van de gebeurtenissen waarborgen die tot de Manager van de Uitvoer worden overgegaan.

* Het gebruiken van zulk een rollout configuratie kon tot conflicten leiden als de gezamenlijke updates van het zelfde middel voorkomen.

Daarom wordt geadviseerd dat u *slechts* gebruik `onModify` trekkers veroorzaakt als de voordelen van automatische rollout initialisering om het even welke potentiële prestatieskwesties opwegen.

### Knooppunttypen/eigenschappen {#node-types-properties}

Houd er rekening mee dat:

* Naast het aanpassen van rollout acties, laat MSM u knoopeigenschappen ook aanpassen die worden opgesteld. De [ configuratie MSM OSGi laat u knooptypes ](/help/sites-administering/msm-sync.md#excluding-properties-and-node-types-from-synchronization) van het worden gekopieerd uit de bron aan het levende exemplaar uitsluiten.

## Aanvullende informatie {#further-information}

Op deze en de volgende pagina&#39;s worden de gerelateerde kwesties besproken:

* [Actieve kopieën maken en synchroniseren](/help/sites-administering/msm-livecopy.md)
* [Console voor live kopiëren](/help/sites-administering/msm-livecopy-overview.md)
* [Synchronisatie van actieve kopie configureren](/help/sites-administering/msm-sync.md)
* [Conflicten MSM-rollout](/help/sites-administering/msm-rollout-conflicts.md)
