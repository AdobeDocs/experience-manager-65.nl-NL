---
title: Definities van releasevoertuig bijwerken
seo-title: Definities van releasevoertuig bijwerken
description: Dit artikel detailleert de diverse types van versies AEM, met inbegrip van volledige versies, eigenschapspakken, en de dienstenpakketten.
seo-description: Dit artikel detailleert de diverse types van versies AEM, met inbegrip van volledige versies, eigenschapspakken, en de dienstenpakketten.
uuid: 388fb6f5-0249-41e2-a460-1bb4cd0f8494
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: deploying
discoiquuid: 32695db5-d62d-4959-8a24-3d56b4a19904
translation-type: tm+mt
source-git-commit: b827c8acb1db158060d209c819fc72ffbfeca65f

---


# Definities van releasevoertuig voor AEM-update{#update-release-vehicle-definitions}

Dit document bevat informatie over de verschillende typen Adobe Experience Manager (AEM)-releases, zoals volledige releases, functiepakketten en servicepakketten die Adobe aan klanten levert.

>[!Nofferte]
>
>Raadpleeg het stappenplan voor [AEM-updateversies voor een releaseschema van de AEM-updateversies](https://helpx.adobe.com/experience-manager/update-releases-roadmap.html)

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
     <li>Beschikbaar op de website voor licentieverlening en de website voor beheerde services</li>
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

## Cumulatief reparatiepakket {#cumulative-fix-pack-aem}

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

## Eak Cumulative Fix Pack {#oak-cumulative-fix-pack}

<table>
 <tbody>
  <tr>
   <td><strong>Definitie</strong></td>
   <td>
    <ul>
     <li>Vergelijkbaar met een standaard-GVB, maar bevat alleen correcties voor eiken</li>
     <li>COFP is onafhankelijk (geen gebiedsdelen). Klanten hoeven zich geen zorgen te maken over het vinden/oplossen van afhankelijkheden. [1]</li>
    </ul> </td>
  </tr>
  <tr>
   <td><strong>Naamgeving</strong></td>
   <td>&lt;version&gt; wissen</td>
  </tr>
  <tr>
   <td><strong>Inclusies</strong></td>
   <td>COFP is cumulatief fixpack dat moeilijke situaties van alle componenten Oak voor een specifieke versie 1.x bevat. Als de klant bijvoorbeeld COHF 1.x.3 toepast, dan COHF 1.x.3. = COHF 1.x.1 + COHF 1.x.2.</td>
  </tr>
  <tr>
   <td><strong>Documentatie</strong></td>
   <td> </td>
  </tr>
  <tr>
   <td><strong>Cadence</strong></td>
   <td><p>Indien nodig</p> </td>
  </tr>
  <tr>
   <td><strong>Beschikbaarheid en installatie</strong></td>
   <td>
    <ul>
     <li>Het COFP-installatieproces is vereenvoudigd om de gebruikerservaring te verbeteren. (Klanten kunnen slechts één pakket installeren voor alle componenten).</li>
    </ul> </td>
  </tr>
  <tr>
   <td><strong>Testniveau</strong></td>
   <td><p>QA gevalideerd</p> </td>
  </tr>
 </tbody>
</table>

## Hot Fix {#hot-fix}

<table>
 <tbody>
  <tr>
   <td><strong>Definitie</strong></td>
   <td><p>Pakket met een of meer bestanden die zijn gemaakt om een productfout op te lossen die essentiële services aanzienlijk verslechteert of het bedrijfsgebruik aanzienlijk beïnvloedt. </p> </td>
  </tr>
  <tr>
   <td><strong>Naamgeving</strong></td>
   <td>cq-&lt;Release-versie&gt;-hotfix-&lt;hotfix-id&gt;-&lt;hotfix-versie&gt;</td>
  </tr>
  <tr>
   <td><strong>Inclusies</strong></td>
   <td>Bevat oplossingen voor een specifiek probleem</td>
  </tr>
  <tr>
   <td><strong>Documentatie</strong></td>
   <td>Opmerkingen bij de release van de openbare hotfixes zijn alleen beschikbaar op basis van een verzoek van de klant via het AEM Support Portal.</td>
  </tr>
  <tr>
   <td><strong>Cadence</strong></td>
   <td>Indien nodig</td>
  </tr>
  <tr>
   <td><strong>Beschikbaarheid en installatie</strong></td>
   <td>
    <ul>
     <li>Geleverd als pakket</li>
     <li>Beschikbaar voor delen van pakket</li>
     <li>Afhankelijk van het nieuwste servicepakket dat wordt uitgebracht</li>
     <li>De meeste hotfixes zijn zelfstandig, tenzij opgegeven. Kan in willekeurige volgorde worden geïnstalleerd. Kan worden gecontroleerd door het lusje van de Details van het Aandeel van het Pakket van het element van Afhankelijkheden.</li>
    </ul> </td>
  </tr>
  <tr>
   <td><strong>Testniveau</strong></td>
   <td>
    <ul>
     <li>Gevalideerd door de klantenservice</li>
     <li>Voor hotfixes voor AEM geldt niet hetzelfde kwaliteitsniveau als voor servicepacks of productreleases. Daarom moeten zij eerst op een het opvoeren milieu als deel van de processen van de kwaliteitsplaatsing worden bevestigd.</li>
    </ul> </td>
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
     <li>Als pakket geleverd door AEM-klantenservice</li>
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
     <li>De Pakken van de eigenschap zijn toevoegings-functionaliteit en worden geleverd via de Pakken van de Dienst. Als een AEM-versie zijn laatste servicepack heeft uitgebracht, levert Adobe in de toekomst geen functiepakket voor dit pakket.</li>
     <li>FP's bevatten productverbeteringen die zijn gepland voor een volgende productrelease, maar die op basis van de beslissing van het productbeheer van Adobe vroeg worden geleverd.</li>
     <li>Functies worden altijd samengevoegd met de volgende grote release en vervolgens teruggezet naar de AEM-versie die de klant nodig heeft</li>
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
     <li>Beschikbaar op Delen van pakket. Klanten accepteren de Algemene voorwaarden van Adobe via Delen van pakketten.</li>
    </ul> </td>
  </tr>
  <tr>
   <td><strong>Testniveau</strong></td>
   <td>Algemene de eigenschapspakketten van de Beschikbaarheid zijn gevalideerd QA</td>
  </tr>
 </tbody>
</table>

* [1]: OAK-correcties worden niet als afzonderlijke hotfixes geleverd. Zij worden echter wel opgenomen in de daaropvolgende Cumulatieve oak-hotfix. Indien nodig kan een diagnostische build boven op de nieuwste COFP beschikbaar worden gesteld. Voorwaarde is dat de klant de nieuwste COFP heeft die wordt uitgevoerd. Diagnostische builds bieden alleen dezelfde kwaliteitsgarantie als een hotfix. Daarom verstrekken zij niet het zelfde niveau van kwaliteitsgarantie zoals een cumulatief fixpack, de dienstpak, of productversie. De laatste oplossing wordt geleverd bij het volgende GVB.

