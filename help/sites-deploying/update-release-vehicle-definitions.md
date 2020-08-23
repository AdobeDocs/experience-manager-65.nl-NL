---
title: Definities van releasevoertuig bijwerken
seo-title: Definities van releasevoertuig bijwerken
description: Dit artikel detailleert de diverse types van AEM versies, met inbegrip van volledige versies, eigenschapspakken, en de dienstenpakketten.
seo-description: Dit artikel detailleert de diverse types van AEM versies, met inbegrip van volledige versies, eigenschapspakken, en de dienstenpakketten.
uuid: 388fb6f5-0249-41e2-a460-1bb4cd0f8494
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: deploying
discoiquuid: 32695db5-d62d-4959-8a24-3d56b4a19904
translation-type: tm+mt
source-git-commit: 80b8571bf745b9e7d22d7d858cff9c62e9f8ed1e
workflow-type: tm+mt
source-wordcount: '768'
ht-degree: 2%

---


# Definities van releasevoertuig AEM bijwerken{#update-release-vehicle-definitions}

Dit document bevat details over de verschillende typen Adobe Experience Manager (AEM)-releases, waaronder volledige releases, functiepakketten en servicepakketten die Adobe aan klanten levert.

>[!NOTE]
>
>Voor versieschema van AEM update-releases raadpleegt u het stappenplan voor [AEM update-releases](https://helpx.adobe.com/experience-manager/update-releases-roadmap.html)

## Volledige release {#full-release}

<table>
 <tbody>
  <tr>
   <td><strong>Definitie</strong></td>
   <td>
    <ul>
     <li>Geplande release</li>
     <li>Steunt verbeteringspaden voor specifieke versies, die in de versienota's worden bepaald</li>
    </ul> </td>
  </tr>
  <tr>
   <td><strong>Naamgeving</strong></td>
   <td>
    <ul>
     <li>De aantallen van de versie voor belangrijke versies stijgen gebaseerd op de formule X+1.Y.Z. </li>
     <li>De aantallen van de versie voor minder belangrijke versieverhoging gebaseerd op formule X.Y+1.Z</li>
    </ul> <p>Waar X het primaire versienummer is, is Y het secundaire versienummer, en Z het flardaantal.</p> </td>
  </tr>
  <tr>
   <td><strong>Inclusies</strong></td>
   <td>
    <ul>
     <li>Nieuwe functies</li>
     <li>Verbeteringen</li>
     <li>Bugfixes</li>
    </ul> </td>
  </tr>
  <tr>
   <td><strong>Documentatie</strong></td>
   <td>
    <ul>
     <li>Opmerkingen bij de release zijn beschikbaar op het documentatieportaal</li>
     <li>Documentatie over functies, verbeteringen en foutoplossingen is beschikbaar op het documentatieportaal</li>
    </ul> </td>
  </tr>
  <tr>
   <td><strong>Cadence</strong></td>
   <td>Jaarlijks</td>
  </tr>
  <tr>
   <td><strong>Beschikbaarheid en installatie</strong></td>
   <td>
    <ul>
     <li>Wordt geleverd als een zelfstandig productinstallatieprogramma</li>
     <li>Beschikbaar op de website voor licentieverlening en de website voor Managed Services-licenties</li>
     <li>Vereist mogelijk migratie naar opslagplaats voor inhoud</li>
    </ul> </td>
  </tr>
  <tr>
   <td><strong>Testniveau</strong></td>
   <td>Volledig gevalideerd door QA</td>
  </tr>
 </tbody>
</table>

## Service Pack {#service-pack}

<table>
 <tbody>
  <tr>
   <td><strong>Definitie</strong></td>
   <td>
    <ul>
     <li>Geplande release</li>
     <li>Kan momenteel niet terugdraaien</li>
    </ul> </td>
  </tr>
  <tr>
   <td><strong>Naamgeving</strong></td>
   <td>
    <ul>
     <li>Reparatienummer is een getal van één cijfer</li>
     <li>Na installatie zal het geïnstalleerde de flardcijfer van het versieaantal verhogen, die op formule X.Y.Z.SPx wordt gebaseerd</li>
     <li>Waar X het primaire versienummer is, is Y het secundaire versienummer, en Z het flardaantal. x is het aantal van het de dienstpak.</li>
    </ul> </td>
  </tr>
  <tr>
   <td><strong>Inclusies</strong></td>
   <td>
    <ul>
     <li>Nieuwe functies</li>
     <li>Verbeteringen</li>
     <li>Bugfixes</li>
     <li>Pakketten met kenmerken van algemeen belang (indien aanwezig)</li>
    </ul> </td>
  </tr>
  <tr>
   <td><strong>Documentatie</strong></td>
   <td>
    <ul>
     <li>Opmerkingen bij de release beschikbaar op het documentatieportaal</li>
     <li>Documentatie over functies, verbeteringen en foutoplossingen op het documentatieportaal</li>
    </ul> </td>
  </tr>
  <tr>
   <td><strong>Cadence</strong></td>
   <td>Driemaandelijks</td>
  </tr>
  <tr>
   <td><strong>Beschikbaarheid en installatie</strong></td>
   <td>
    <ul>
     <li>Geleverd als pakket</li>
     <li>Beschikbaar voor delen van pakket</li>
     <li>Vereist bestaande functionele installatie</li>
    </ul> </td>
  </tr>
  <tr>
   <td><strong>Testniveau</strong></td>
   <td>
    <ul>
     <li>Alle oplossingen voor gevalideerde kwaliteitscontrole</li>
     <li>Algemene saniteit van pakketten met automatiseringsprestaties</li>
    </ul> </td>
  </tr>
 </tbody>
</table>

## Cumulatief reparatiepakket  {#cumulative-fix-pack-aem}

<table>
 <tbody>
  <tr>
   <td><strong>Definitie</strong></td>
   <td>
    <ul>
     <li>Single Deliasing Model of releasing fixes</li>
     <li>Aggregator-inhoudspakket met inhoudspakket van afzonderlijke componenten</li>
     <li>GFP's zijn rollover van hotfixes en er zijn geen verbeteringen in opgenomen.</li>
    </ul> </td>
  </tr>
  <tr>
   <td><strong>Naamgeving</strong></td>
   <td><p>X.Y.Z.CFPx</p> <p>Waar X het primaire versienummer is, is Y het secundaire versienummer, en Z het flardaantal. x is het cumulatieve aantal van het de dienstpak.</p> </td>
  </tr>
  <tr>
   <td><strong>Inclusies</strong></td>
   <td><p>GFP is cumulatieve fixpack die fixes van alle componenten door gespecificeerde data bevat. Bijvoorbeeld, als een klant GVB3 toepast, dan GFP3 = GFP1 + GFP2.</p> </td>
  </tr>
  <tr>
   <td><strong>Documentatie</strong></td>
   <td>Opmerkingen bij de release beschikbaar op het documentatieportaal</td>
  </tr>
  <tr>
   <td><strong>Cadence</strong></td>
   <td>viermaal</td>
  </tr>
  <tr>
   <td><strong>Beschikbaarheid en installatie</strong></td>
   <td>
    <ul>
     <li>Geleverd als pakket</li>
     <li>Beschikbaar voor delen van pakket</li>
     <li>Afhankelijk van het nieuwste servicepakket dat wordt uitgebracht</li>
     <li>Het GVB is onafhankelijk. Klanten hoeven zich geen zorgen te maken over het vinden/oplossen van afhankelijkheden. GFP zou op recentste vrijgegeven Service Pack moeten worden geïnstalleerd.</li>
     <li>GFP kan als één enkel pakket worden geïnstalleerd, dat klantenervaring verbetert.</li>
    </ul> </td>
  </tr>
  <tr>
   <td><strong>Testniveau</strong></td>
   <td>QA gevalideerd op integratieniveau en regressietests</td>
  </tr>
 </tbody>
</table>

## Bedekking {#overlay}

<table>
 <tbody>
  <tr>
   <td><strong>Definitie</strong></td>
   <td> </td>
  </tr>
  <tr>
   <td><strong>Naamgeving</strong></td>
   <td>bedekking-&lt;ticket-id&gt;</td>
  </tr>
  <tr>
   <td><strong>Inclusies</strong></td>
   <td>Opgeloste problemen voor een JS- of JSP-bestand</td>
  </tr>
  <tr>
   <td><strong>Documentatie</strong></td>
   <td>Geen</td>
  </tr>
  <tr>
   <td><strong>Cadence</strong></td>
   <td>Indien nodig</td>
  </tr>
  <tr>
   <td><strong>Beschikbaarheid en installatie</strong></td>
   <td>
    <ul>
     <li>Door AEM klantenservice als pakket geleverd</li>
     <li>Niet noodzakelijk inbegrepen in de dienstpakken of volledige versies</li>
    </ul> </td>
  </tr>
  <tr>
   <td><strong>Testniveau</strong></td>
   <td>Gevalideerd door de klantenservice</td>
  </tr>
 </tbody>
</table>

## Functiepakket {#feature-pack}

<table>
 <tbody>
  <tr>
   <td><strong>Definitie</strong></td>
   <td>
    <ul>
     <li>De Pakken van de eigenschap zijn toevoegings-functionaliteit en worden geleverd via de Pakken van de Dienst. Als een AEM versie zijn laatste de dienstpak heeft vrijgegeven, zal Adobe geen eigenschapspak voor het in de toekomst leveren.</li>
     <li>FPs bevatten die voor een volgende productversie, maar op het besluit van het Beheer van het Product van de Adobe vroeg worden gepland geleverd.</li>
     <li>Functies worden altijd samengevoegd met de volgende grote release en vervolgens teruggezet naar de AEM versie die de klant nodig heeft</li>
     <li>De gemeenschappelijke belangen en de eigenschapspakketten van GA worden samengevoegd in het volgende de dienstpak</li>
    </ul> </td>
  </tr>
  <tr>
   <td><strong>Naamgeving</strong></td>
   <td>cq-&lt;Release Version&gt;-feature-pack-&lt;featurepack ID&gt;-&lt;featurepack version&gt;</td>
  </tr>
  <tr>
   <td><strong>Inclusies</strong></td>
   <td>
    <ul>
     <li>Nieuwe functies</li>
     <li>Verbeteringen</li>
     <li>Bugfixes (incrementele productupdates)</li>
    </ul> </td>
  </tr>
  <tr>
   <td><strong>Documentatie</strong></td>
   <td>Documentatie is beschikbaar op helpx.adobe.com.</td>
  </tr>
  <tr>
   <td><strong>Cadence</strong></td>
   <td>Varieert met het gebied van het Product</td>
  </tr>
  <tr>
   <td><strong>Beschikbaarheid en installatie</strong></td>
   <td>
    <ul>
     <li>Wordt geleverd via servicepacks</li>
     <li>Beschikbaar op Delen van pakket. Klanten accepteren Adobe en voorwaarden delen via pakket.</li>
    </ul> </td>
  </tr>
  <tr>
   <td><strong>Testniveau</strong></td>
   <td>Algemene de eigenschapspakketten van de Beschikbaarheid zijn gevalideerd QA</td>
  </tr>
 </tbody>
</table>

* [1]: OAK-correcties worden niet als afzonderlijke hotfixes geleverd. Zij worden echter wel opgenomen in de daaropvolgende Cumulatieve oak-hotfix. Indien nodig kan een diagnostische build boven op de nieuwste COFP beschikbaar worden gesteld. Voorwaarde is dat de klant de nieuwste COFP heeft die wordt uitgevoerd. Diagnostische builds bieden alleen dezelfde kwaliteitsgarantie als een hotfix. Daarom verstrekken zij niet het zelfde niveau van kwaliteitsgarantie zoals een cumulatief fixpack, de dienstpak, of productversie. De laatste oplossing wordt geleverd bij het volgende GVB.

