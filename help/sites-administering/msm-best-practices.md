---
title: Aanbevolen MSM-procedures
seo-title: Aanbevolen MSM-procedures
description: Zoek naar beste praktijken die door Adobe engineering en consultancyteams worden gecompileerd helpen om met de AEM MultiManager van de Plaats in gebruik te worden.
seo-description: Zoek naar beste praktijken die door Adobe engineering en consultancyteams worden gecompileerd helpen om met de AEM MultiManager van de Plaats in gebruik te worden.
uuid: cbb598bb-ec8f-4985-97af-7c87f5891c66
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: site-features, best-practices
content-type: reference
discoiquuid: 04344537-7485-40a9-ad14-804ba448f1e2
translation-type: tm+mt
source-git-commit: a929252a13f66da8ac3e52aea0655b12bdd1425f
workflow-type: tm+mt
source-wordcount: '1530'
ht-degree: 0%

---


# MSM Beste praktijken{#msm-best-practices}

## Algemeen {#general}

MSM is een configureerbaar framework voor het automatiseren van de implementatie van inhoud. Bij implementaties gaat het vaak om grote delen van een website en meerdere organisaties en geografische gebieden. Daarom wordt u ten zeerste aangeraden MSM-implementaties net zo zorgvuldig te plannen als uw website:

* **Plan de structuur en inhoudsstromen** zorgvuldig voordat u de implementatie start.
* **Pas de aanpassingen zoveel als nodig is, maar zo weinig mogelijk.** Hoewel MSM een hoge mate van aanpassing (bijvoorbeeld rollout configuraties) steunt, typisch is de beste praktijken voor de prestaties, de betrouwbaarheid en de upgradeability van uw website aanpassing minimaliseren.
* Stel een **governance** model vroeg in en geef gebruikers de juiste training om succes te garanderen. Een beste manier vanuit bestuurlijk oogpunt is om de autoriteit die lokale inhoudsproducenten hebben, tot een minimum te beperken.**om inhoud toe te wijzen aan/te verbinden met andere lokale gebruikers en hun respectievelijke live kopieën.** Dit komt omdat onbestuurde, geketende overerving de complexiteit van een MSM-structuur aanzienlijk kan verhogen en de prestaties en betrouwbaarheid ervan in gevaar kan brengen.

* Zodra een plan voor uw structuur, inhoudsstromen, automatisering en bestuur - **prototype en grondig uw systeem**, alvorens levende implementatie te beginnen bestaat.
* Onthoud dat **Adobe Consulting en toonaangevende System Integrators** uitgebreide ervaring hebben met het plannen en implementeren van content automatisering met MSM, zodat ze u kunnen helpen zowel aan de slag te gaan met uw MSM-project als tijdens de volledige implementatie ervan.

>[!NOTE]
>
>Meer informatie over het werken met MSM is te vinden in de artikelen in de Knowledge Base:
>
>* [Veelgestelde vragen over MSM](https://helpx.adobe.com/experience-manager/kb/index/msm_faq.html)
>* [Problemen met MSM oplossen](https://helpx.adobe.com/experience-manager/kb/troubleshooting-aem-msm-issues.html)

>



>[!NOTE]
>
>U kunt ook de [Referentiecomponent](/help/sites-authoring/default-components-foundation.md#reference) gebruiken om één pagina of alinea opnieuw te gebruiken. Houd echter rekening met:
>
>* MSM is flexibeler en staat fijnkorrelige controle over toe welke inhoud wordt gesynchroniseerd en wanneer.
>* [De ](https://docs.adobe.com/content/help/en/experience-manager-core-components/using/introduction.html) componenten van de kern worden nu geadviseerd over de stichtingscomponenten.

>



## Live Copy-bronnen en configuraties voor blauwdrukken {#live-copy-sources-and-blueprint-configurations}

Onthoud dat een live kopie kan worden gemaakt met [gewone pagina&#39;s](/help/sites-administering/msm-livecopy.md#creating-a-live-copy-of-a-page) of een [blauwdrukconfiguratie](/help/sites-administering/msm-livecopy.md#creating-a-live-copy-of-a-site-from-a-blueprint-configuration). Beide zijn geldige gebruiksgevallen.

De extra voordelen van het gebruiken van een blauwdrukconfiguratie zijn dat zij:

* Laat de auteur de optie **Uitvoer** op een blauwdruk gebruiken - aan (uitdrukkelijk) duw wijzigingen aan levende exemplaren die van deze blauwdruk erven.
* De auteur toestaan **Site maken/> te gebruiken; hierdoor kan de gebruiker eenvoudig talen selecteren en de structuur van de live kopie configureren .**
* Definieer een standaardrollout-configuratie voor live kopieën die een relatie hebben met de blauwdruk.

Als er niet naar een blauwdrukconfiguratie wordt verwezen, kunnen rollouts alleen worden geïnitieerd vanuit de live kopieën zelf, waarbij inhoud van de bron wordt opgehaald.

Wanneer het creëren van een nieuwe plaats met levende kopie, is het voordelig om blauwdrukconfiguraties tot stand te brengen om de beschikbaarheid van de volledige MSM eigenschapreeks te verzekeren.

## Componenten en containersynchronisatie {#components-and-container-synchronization}

In het algemeen, is de rollout regel in MSM betreffende de synchronisatie van componenten:

* Componenten worden gesynchroniseerd met alle bronnen in de blauwdruk.
* Containers synchroniseren alleen de huidige bron.

Dit betekent dat componenten als aggregaat worden behandeld, en in een rollout worden de component zelf en al zijn kinderen vervangen met die in de blauwdrukken. Dit betekent dat als een bron lokaal aan een dergelijke component wordt toegevoegd, deze bij rollout verloren gaat aan de inhoud van de blauwdruk.

Om het nesten van componenten te steunen zodat de plaatselijk toegevoegde componenten in een rollout worden gehandhaafd, moet de component als container worden verklaard. Als voorbeeld, wordt standaard parsys verklaard als container zodat kan het plaatselijk-toegevoegde inhoud steunen.

>[!NOTE]
>
>Voeg de eigenschap `cq:isContainer` toe aan de component om deze aan te wijzen als een container.

## Site {#create-site} maken

U ziet dat AEM twee hoofdbenaderingen heeft voor het maken van live kopieën:

* Wanneer [een live kopie maken](/help/sites-administering/msm-livecopy.md#creating-a-live-copy-of-a-page)

   Dit kan als generischere benadering worden beschouwd, toestaand u om levende exemplaren van om het even welke pagina tot stand te brengen. De inhoudsstructuur van een live kopie komt exact overeen met de bron.

* Wanneer [een site maken](/help/sites-administering/msm-livecopy.md#creating-a-live-copy-of-a-site-from-a-blueprint-configuration)

   Dit is een meer gespecialiseerde benadering, vooral voor het creëren van websites met een meertalige structuur.

Houd rekening met het volgende wanneer u een site maakt:

* Als u een nieuwe site wilt maken, hebt u een [blauwdrukconfiguratie](/help/sites-administering/msm-livecopy.md#managing-blueprint-configurations) nodig.
* Als u wilt dat de taalpaden op een nieuwe site kunnen worden geselecteerd, moeten de overeenkomstige taalwortels in de blauwdruk (bron) aanwezig zijn.
* Nadat een [nieuwe site is gemaakt als een live kopie](/help/sites-administering/msm-livecopy.md#creating-a-live-copy-of-a-site-from-a-blueprint-configuration) (met **Create** en **Site**), zijn de eerste twee niveaus van deze live kopie *shallow*. Onderliggende items van de pagina behoren niet tot de live-relatie, maar de rollout neemt wel af als een live-relatie wordt gevonden die overeenkomt met de trigger.

   Het helpt voorkomen:

   * handmatig talen toevoegen in de blauwdruk (onder het eerste niveau)
   * handmatig inhoud toevoegen direct onder de hoofdmap van de taal,
   * leidt er niet toe dat deze nieuwe inhoud automatisch bij de rollout naar de live kopie wordt overgedragen.

## MSM- en meertalige websites {#msm-and-multilingual-websites}

MSM kan op twee manieren helpen bij het maken van meertalige websites:

* Bij het maken van taalstramienen.

   * Hoewel MSM zelf **geen inhoudsomzetting** verstrekt, kan het met derdevertaalschakelaars worden geïntegreerd die doen. Houd er rekening mee dat:

      * Met MSM kunt u overerving op pagina- en/of componentniveau annuleren. Zo voorkomt u bij de volgende rollout dat vertaalde inhoud (van een live kopie met nog niet-vertaalde inhoud van een blauwdruk) wordt overschreven.
      * Sommige vertalingsconnectors van derden automatiseren dit beheer van MSM-overerving.

         Neem contact op met uw vertaalserviceprovider voor meer informatie.

      * Een alternatieve benadering voor het maken en vertalen van taalmeesters is het gebruik van taalkopieën in combinatie met AEM kader voor vertaalintegratie buiten de doos.

* Bij het uitrollen van inhoud van taalmeesters.

   * Bijvoorbeeld vanuit de Franse taal die master is voor landspecifieke sites, zoals Frankrijk/Frans, Canada/Frans, Zwitserland/Frans.

Zie [Inhoud vertalen voor meertalige sites](/help/sites-administering/translation.md) en [Aanbevolen procedures voor vertaling](/help/sites-administering/tc-bp.md) voor meer informatie.

## Wijzigingen en rollouts voor structuur {#structure-changes-and-rollouts}

Wijzigingen in de inhoudsstructuur in een blauwdruk-/bronstructuur worden anders weerspiegeld in een live kopie. Dit is afhankelijk van het wijzigingstype:

* **Als u nieuwe** pagina&#39;s maakt in een blauwdruk, worden de bijbehorende pagina&#39;s na de uitrol met de standaardconfiguratie voor uitrollout gemaakt in live kopieën.

* **Als u** pagina&#39;s in een blauwdruk verwijdert, worden de bijbehorende pagina&#39;s na de implementatie met de standaardconfiguratie voor uitrollout uit live kopieën verwijderd.

* **Als u** pagina&#39;s in een blauwdruk verplaatst, worden de corresponderende pagina&#39;s  **** niet in live kopieën verplaatst na rollout met de standaardrollout-configuratie:

   * De reden voor dit gedrag is dat een paginabeweging impliciet een pagina-verwijdering bevat. Dit kan mogelijk leiden tot onverwacht gedrag bij het publiceren, omdat bij het verwijderen van pagina&#39;s bij de auteur de bijbehorende inhoud bij het publiceren automatisch wordt gedeactiveerd. Dit kan ook gevolgen hebben voor verwante punten zoals verbindingen, referenties, en anderen.
   * Inhoudsovererving op de respectievelijke pagina&#39;s met live kopieën wordt bijgewerkt om de nieuwe locatie van de bronnen in de blauwdruk te weerspiegelen.
   * Houd rekening met de volgende aanbevolen procedures om te zorgen dat een pagina van een blauwdruk naar live kopieën wordt verplaatst:

>[!NOTE]
>
>Dit werkt alleen met de [Bij rollout trigger](https://helpx.adobe.com/experience-manager/6-3/sites/administering/using/msm-sync.html#rollout-triggers).

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

MSM-rollout-configuraties zijn in hoge mate aanpasbaar. Het automatiseren van rollouts kan verstrekkende gevolgen hebben. Als beste praktijken, zou u *very* zorgvuldig vóór, bijvoorbeeld moeten plannen:

* het automatiseren van rollouts; bijvoorbeeld met [onModify triggers](#onmodify),
* aanpassen van [knooppunttypen/eigenschappen](#node-types-properties),
* volgende workflows starten,
* en/of inhoud activeren als onderdeel van rollouts.

### onModify {#onmodify}

Wanneer u de [rollout trigger](/help/sites-administering/msm-sync.md#rollout-triggers) `onModify` gebruikt, moet u rekening houden met het volgende:

* Het automatiseren van rollouts met `onModify` triggers kan een negatief effect hebben op de ontwerpprestaties omdat deze rollouts activeren na het wijzigen van *elke* pagina.

* Het rollout-resultaat kan afwijken van het verwachte resultaat:

   * U kunt de volgorde van de resulterende wijzigingsgebeurtenissen niet opgeven.
   * De op gebeurtenis-gebaseerde architectuur kan niet de opeenvolging van de gebeurtenissen waarborgen die tot de Manager van de Uitvoer worden overgegaan.

* Het gebruiken van zulk een rollout configuratie kon tot conflicten leiden als de gezamenlijke updates van het zelfde middel voorkomen.

Daarom wordt aanbevolen *alleen* triggers te gebruiken als de voordelen van automatische implementatieinitiatie opwegen tegen mogelijke prestatieproblemen.`onModify`

### Knooppunttypen/eigenschappen {#node-types-properties}

Houd er rekening mee dat:

* Naast het aanpassen van rollout acties, staat MSM u ook toe om knoopeigenschappen aan te passen die worden uitgerold. De [configuratie MSM OSGi staat u toe om knooptypes](/help/sites-administering/msm-sync.md#excluding-properties-and-node-types-from-synchronization) van het worden gekopieerd van de bron aan het levende exemplaar uit te sluiten.

## Aanvullende informatie {#further-information}

Op deze en de volgende pagina&#39;s worden de gerelateerde kwesties besproken:

* [Actieve kopieën maken en synchroniseren](/help/sites-administering/msm-livecopy.md)
* [Console voor live kopiëren](/help/sites-administering/msm-livecopy-overview.md)
* [Synchronisatie van actieve kopie configureren](/help/sites-administering/msm-sync.md)
* [Conflicten MSM-rollout](/help/sites-administering/msm-rollout-conflicts.md)

