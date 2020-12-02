---
title: Ondersteuning voor contentfragmenten in HTTP-API van AEM Assets
seo-title: Ondersteuning voor contentfragmenten in HTTP-API van AEM Assets
description: Meer informatie over ondersteuning voor inhoudsfragmenten in de HTTP-API van AEM Assets.
seo-description: Meer informatie over ondersteuning voor inhoudsfragmenten in de HTTP-API van AEM Assets.
uuid: c500d71e-ceee-493a-9e4d-7016745c544c
contentOwner: aheimoz
products: SG_EXPERIENCEMANAGER/6.5/ASSETS
content-type: reference
topic-tags: extending-assets
discoiquuid: 03502b41-b448-47ab-9729-e0a66a3389fa
docset: aem65
translation-type: tm+mt
source-git-commit: 74f259d579bcf8d7a9198f93ef667288787a4493
workflow-type: tm+mt
source-wordcount: '1859'
ht-degree: 2%

---


# Ondersteuning voor contentfragmenten in HTTP-API van AEM Assets{#content-fragments-support-in-aem-assets-http-api}

## Overzicht {#overview}

>[!NOTE]
>
>De [Elementen HTTP API](/help/assets/mac-api-assets.md) omvat het volgende:
>
>* REST-API voor middelen
>* inclusief ondersteuning voor inhoudsfragmenten

>
>
De huidige implementatie van AEM Assets HTTP API is REST.

Met de Adobe Experience Manager (AEM) [Assets REST API](/help/assets/mac-api-assets.md) hebben ontwikkelaars via CRUD-bewerkingen (Maken, Lezen, Bijwerken, Verwijderen) rechtstreeks toegang tot inhoud (opgeslagen in AEM) via de HTTP-API.

Met de API kunt u AEM werken als een CMS zonder kop (Content Management System) door Content Services aan te bieden aan een JavaScript front-end toepassing. Of elke andere toepassing die HTTP-aanvragen kan uitvoeren en JSON-reacties kan verwerken.

Toepassingen voor één pagina (SPA), die zijn gebaseerd op een framework of die zijn aangepast, vereisen bijvoorbeeld inhoud die via de HTTP-API wordt aangeboden, vaak in de JSON-indeling.

Terwijl AEM de Componenten van de Kern een zeer uitvoerige, flexibele en klantgerichte API verstrekken die vereiste Gelezen verrichtingen voor dit doel kan dienen, en de waarvan output JSON kan worden aangepast, vereisen zij AEM WCM (het Beheer van de Inhoud van het Web) knowhow voor implementatie aangezien zij in (API) pagina&#39;s moeten worden ontvangen die op specifieke AEM malplaatjes gebaseerd zijn. Niet elke SPA ontwikkelingsorganisatie heeft toegang tot dergelijke middelen.

Dit is wanneer de REST API van Activa kan worden gebruikt. Ontwikkelaars hebben direct toegang tot elementen (bijvoorbeeld afbeeldingen en inhoudsfragmenten), zonder dat ze eerst in een pagina moeten worden ingesloten en hun inhoud in geserialiseerde JSON-indeling moeten leveren. (Het is niet mogelijk JSON-uitvoer van de REST API voor middelen aan te passen.) Met de REST API voor middelen kunnen ontwikkelaars ook inhoud wijzigen door nieuwe elementen, inhoudsfragmenten en mappen te maken, bij te werken of te verwijderen.

De REST-API voor middelen:

* volgt het [HATEOAS-beginsel](https://en.wikipedia.org/wiki/HATEOAS)

* implementeert de [SIREN-indeling](https://github.com/kevinswiber/siren)

## Vereisten {#prerequisites}

De REST-API voor middelen is beschikbaar voor elke installatie van een recente AEM.

## Belangrijke concepten {#key-concepts}

De REST API van Activa biedt [REST](https://en.wikipedia.org/wiki/Representational_state_transfer)-stijl toegang tot activa die binnen een AEM instantie worden opgeslagen. Het gebruikt het `/api/assets` eindpunt en vereist de weg van de activa om tot het (zonder het leiden `/content/dam`) toegang te hebben.

De HTTP-methode bepaalt de uit te voeren bewerking:

* **GET** - om een JSON-representatie van een element of map op te halen
* **POST** - om nieuwe elementen of mappen te maken
* **PUT** - om de eigenschappen van een middel of een omslag bij te werken
* **DELETE** - om een middel of een omslag te schrappen

>[!NOTE]
>
>De verzoeklichaam en/of parameters URL kunnen worden gebruikt om sommige van deze verrichtingen te vormen; Stel bijvoorbeeld dat een map of een element moet worden gemaakt door een **POST**-verzoek.

De exacte indeling van ondersteunde aanvragen wordt gedefinieerd in de [API-naslaggids](/help/assets/assets-api-content-fragments.md#api-reference)-documentatie.

### Transactioneel gedrag {#transactional-behavior}

Alle verzoeken zijn atomisch.

Dit betekent dat de verdere (`write`) verzoeken niet in één enkele transactie kunnen worden gecombineerd die als één enkele entiteit zou kunnen slagen of ontbreken.

### AEM (Middelen) REST API versus AEM componenten {#aem-assets-rest-api-versus-aem-components}

<table>
 <tbody>
  <tr>
   <td>Verhouding</td>
   <td>Elementen REST API<br /> </td>
   <td>AEM Component<br /> (componenten die Sling Models gebruiken)</td>
  </tr>
  <tr>
   <td>Ondersteunde gebruikscase(s)</td>
   <td>Algemeen doel.</td>
   <td><p>Geoptimaliseerd voor gebruik in een toepassing voor één pagina (SPA) of in een andere (content consuming) context.</p> <p>Kan ook lay-outgegevens bevatten.</p> </td>
  </tr>
  <tr>
   <td>Ondersteunde bewerkingen</td>
   <td><p>Maken, lezen, bijwerken, verwijderen.</p> <p>Met extra bewerkingen afhankelijk van het type entiteit.</p> </td>
   <td>Alleen-lezen.</td>
  </tr>
  <tr>
   <td>Toegang</td>
   <td><p>Kan rechtstreeks worden benaderd.</p> <p>Gebruikt het <code>/api/assets </code>eindpunt, toegewezen aan <code>/content/dam</code> (in de bewaarplaats).</p> <p>Bijvoorbeeld om toegang te krijgen tot:<code class="code">
       /content/dam/we-retail/en/experiences/arctic-surfing-in-lofoten</code><br /> verzoek:<br /> <code>/api/assets/we-retail/en/experiences/arctic-surfing-in-lofoten.model.json</code></p> </td>
   <td><p>Moet door een AEM component op een AEM pagina worden van verwijzingen voorzien.</p> <p>Gebruikt de <code>.model</code> selecteur om de vertegenwoordiging tot stand te brengen JSON.</p> <p>Een voorbeeld-URL ziet er als volgt uit:<br /> <code>https://localhost:4502/content/we-retail/language-masters/en/experience/arctic-surfing-in-lofoten.model.json</code></p> </td>
  </tr>
  <tr>
   <td>Beveiliging</td>
   <td><p>Er zijn meerdere opties mogelijk.</p> <p>OAuth wordt voorgesteld; kan los van standaardopstelling worden gevormd.</p> </td>
   <td>Gebruikt AEM standaardinstallatie.</td>
  </tr>
  <tr>
   <td>Architecten</td>
   <td><p>Schrijftoegang richt zich gewoonlijk tot een auteurinstantie.</p> <p>Lees kan ook naar een publicatie-instantie worden gestuurd.</p> </td>
   <td>Aangezien deze benadering read-only is, zal het typisch voor publiceer instanties worden gebruikt.</td>
  </tr>
  <tr>
   <td>Uitvoer</td>
   <td>Op JSON gebaseerde SIREN-uitvoer: uitgebreid, maar krachtig. Hiermee kunt u navigeren binnen de inhoud.</td>
   <td>op JSON gebaseerde eigen output; configureerbaar via Sling Models. Navigeren door de inhoudsstructuur is moeilijk te implementeren (maar niet noodzakelijkerwijs onmogelijk).</td>
  </tr>
 </tbody>
</table>

### Beveiliging {#security}

Als de REST API van Middelen binnen een milieu zonder specifieke authentificatievereisten wordt gebruikt, moet AEM filter CORS correct worden gevormd.

>[!NOTE]
>
>Zie voor meer informatie:
>
>* [CORS/AEM toegelicht](https://helpx.adobe.com/experience-manager/kt/platform-repository/using/cors-security-article-understand.html)
>* [Video - Ontwikkelen voor CORS met AEM](https://helpx.adobe.com/experience-manager/kt/platform-repository/using/cors-security-technical-video-develop.html)

>



In omgevingen met specifieke verificatievereisten wordt OAuth aanbevolen.

## Beschikbare functies {#available-features}

Inhoudsfragmenten zijn een specifiek type element. Zie [Werken met inhoudfragmenten](/help/assets/content-fragments/content-fragments.md).

Zie voor meer informatie over functies die beschikbaar zijn via de API:

* [Beschikbare ](/help/assets/mac-api-assets.md#assets) functies van de REST API voor middelen
* [Typen entiteiten](/help/assets/assets-api-content-fragments.md#entity-types)

### {#paging} pagineren

De REST API voor middelen ondersteunt paginering (voor GET-aanvragen) via de URL-parameters:

* `offset` - het nummer van de eerste (onderliggende) entiteit die moet worden opgehaald
* `limit` - het maximumaantal geretourneerde entiteiten

De reactie zal het pagineren informatie als deel van `properties` sectie van de output bevatten SIREN. Deze `srn:paging` eigenschap bevat het totale aantal (onderliggende) entiteiten ( `total`), de verschuiving en de limiet ( `offset`, `limit`) zoals opgegeven in de aanvraag.

>[!NOTE]
>
>Paginering wordt doorgaans toegepast op containerentiteiten (d.w.z. mappen of elementen met uitvoeringen), aangezien deze betrekking hebben op de onderliggende elementen van de aangezochte entiteit.

#### Voorbeeld: {#example-paging} pagineren

`GET /api/assets.json?offset=2&limit=3`

```
...
"properties": {
    ...
    "srn:paging": {
        "total": 7,
        "offset": 2,
        "limit": 3
    }
    ...
}
...
```

## Typen entiteiten {#entity-types}

### Mappen {#folders}

Mappen fungeren als containers voor elementen en andere mappen. Ze weerspiegelen de structuur van de AEM-inhoudsopslagplaats.

De REST API van Middelen stelt toegang tot de eigenschappen van een omslag bloot; bijvoorbeeld naam, titel, enz. Elementen worden weergegeven als onderliggende entiteiten van mappen.

>[!NOTE]
>
>Afhankelijk van het type element kan de lijst met onderliggende entiteiten al de volledige reeks eigenschappen bevatten die de desbetreffende onderliggende entiteit definieert. Alternatief, slechts kan een beperkte reeks eigenschappen voor een entiteit in deze lijst van kindentiteiten worden blootgesteld.

### Assets {#assets}

Als een element wordt gevraagd, zal de reactie zijn meta-gegevens terugkeren; zoals titel, naam en andere informatie zoals gedefinieerd in het desbetreffende schema voor elementen.

De binaire gegevens van een element worden blootgesteld als een verbinding SIREN van type `content` (ook genoemd als `rel attribute`).

Elementen kunnen meerdere uitvoeringen hebben. Deze worden doorgaans weergegeven als onderliggende entiteiten, waarbij één uitzondering een miniatuuruitvoering is die wordt weergegeven als een koppeling van het type `thumbnail` ( `rel="thumbnail"`).

### Contentfragmenten {#content-fragments}

Een [inhoudsfragment](/help/assets/content-fragments/content-fragments.md) is een speciaal type element. Ze kunnen worden gebruikt om onder andere toegang te krijgen tot gestructureerde gegevens, zoals teksten, getallen, datums.

Aangezien er verschillende verschillen zijn met *standard* elementen (zoals afbeeldingen of audio), zijn er enkele aanvullende regels van toepassing op de afhandeling ervan.

#### Weergave {#representation}

Inhoudsfragmenten:

* Maak geen binaire gegevens beschikbaar.
* Deze bevinden zich volledig in de JSON-uitvoer (binnen de eigenschap `properties`).

* Wordt ook als atomisch beschouwd, d.w.z. de elementen en variaties worden blootgesteld als onderdeel van de eigenschappen van het fragment ten opzichte van als koppelingen of onderliggende entiteiten. Op deze manier hebt u efficiënt toegang tot de lading van een fragment.

#### Content Models and Content Fragments {#content-models-and-content-fragments}

De modellen die de structuur van een inhoudsfragment definiëren, worden momenteel niet via een HTTP-API weergegeven. Daarom moet de *consument* op de hoogte zijn van het model van een fragment (ten minste een minimum) - hoewel de meeste informatie kan worden afgeleid uit de lading; als gegevenstypen, enz. maken deel uit van de definitie.

Als u een nieuw inhoudsfragment wilt maken, moet u het pad (interne gegevensopslagruimte) opgeven.

#### Gekoppelde inhoud {#associated-content}

Gekoppelde inhoud wordt momenteel niet weergegeven.

## {#using} gebruiken

Het gebruik kan verschillen afhankelijk van of u een AEM auteur of publicatieomgeving gebruikt, samen met uw specifieke gebruiksscenario.

* Creatie is strikt gebonden aan een auteurinstantie ([en momenteel is er geen middel om een fragment te herhalen om te publiceren gebruikend dit API](/help/assets/assets-api-content-fragments.md#limitations)).
* De levering is mogelijk van beide, aangezien AEM gevraagde inhoud in formaat slechts JSON dient.

   * Opslag en levering vanuit een AEM auteur-instantie zouden voldoende moeten zijn voor toepassingen achter de firewall, in de mediabibliotheek.
   * Voor live webweergave wordt een AEM-publicatie-instantie aanbevolen.

>[!CAUTION]
>
>De configuratie van de verzender op AEM wolkeninstanties zou toegang tot `/api` kunnen blokkeren.

>[!NOTE]
>
>Zie [API Reference](/help/assets/assets-api-content-fragments.md#api-reference) voor meer informatie. Met name [Adobe Experience Manager Assets API - Content Fragments](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/assets-api-content-fragments/index.html).

### {#read-delivery} lezen/leveren

Gebruik gebeurt via:

`GET /{cfParentPath}/{cfName}.json`

Bijvoorbeeld:

`https://localhost:4502/api/assets/we-retail/en/experiences/arctic-surfing-in-lofoten.json`

De reactie is geserialiseerd met JSON met de inhoud gestructureerd zoals in het inhoudsfragment. Referenties worden als referentie-URL&#39;s geleverd.

Er zijn twee typen leesbewerkingen mogelijk:

* Als u een specifiek inhoudsfragment leest per pad, wordt hiermee de JSON-representatie van het inhoudsfragment geretourneerd.
* Een map met inhoudsfragmenten lezen op pad: Hiermee worden de JSON-representaties van alle inhoudsfragmenten in de map geretourneerd.

### Maken {#create}

Gebruik gebeurt via:

`POST /{cfParentPath}/{cfName}`

De hoofdtekst moet een JSON-representatie bevatten van het inhoudsfragment dat moet worden gemaakt, inclusief de initiële inhoud die moet worden ingesteld op de elementen van het inhoudsfragment. Het is verplicht om de eigenschap `cq:model` in te stellen en deze moet verwijzen naar een geldig inhoudsfragmentmodel. Als u dit niet doet, treedt er een fout op. Er moet ook een koptekst `Content-Type` worden toegevoegd die is ingesteld op `application/json`.

### {#update} bijwerken

Gebruik is via

`PUT /{cfParentPath}/{cfName}`

De hoofdtekst moet een JSON-representatie bevatten van wat voor het opgegeven inhoudsfragment moet worden bijgewerkt.

Dit kan gewoon de titel of beschrijving zijn van een inhoudsfragment, of één element, of alle elementwaarden en/of metagegevens. Het is ook verplicht een geldige `cq:model`-eigenschap voor updates op te geven.

### Verwijderen {#delete}

Gebruik gebeurt via:

`DELETE /{cfParentPath}/{cfName}`

## Beperkingen {#limitations}

Er zijn enkele beperkingen:

* **Variaties kunnen niet worden geschreven en bijgewerkt.** Als deze variaties aan een lading worden toegevoegd (bijvoorbeeld voor updates) zullen zij worden genegeerd. De variatie zal echter worden aangeboden via levering ( `GET`).

* **Inhoudsfragmentmodellen worden momenteel niet ondersteund**: ze kunnen niet worden gelezen of gemaakt. Ontwikkelaars moeten het juiste pad naar het inhoudsfragmentmodel weten om een nieuw inhoudsfragment te kunnen maken of een bestaand inhoudsfragment bij te werken. Momenteel is de enige methode om een overzicht van deze te krijgen door het beleid UI.
* **Verwijzingen worden genegeerd**. Er wordt momenteel niet gecontroleerd of naar een bestaand inhoudsfragment wordt verwezen. Daarom kan het verwijderen van een inhoudsfragment bijvoorbeeld resulteren in problemen op een pagina die een verwijzing bevat.

## Statuscodes en foutberichten {#status-codes-and-error-messages}

De volgende statuscodes kunnen in de relevante omstandigheden worden gezien:

* **200 (OK)**

   Geretourneerd wanneer:

   * een inhoudsfragment aanvragen via `GET`

   * een inhoudsfragment bijwerken via `PUT`

* **201 (gemaakt)**

   Geretourneerd wanneer:

   * een inhoudsfragment maken via `POST`

* **404 (Niet gevonden)**

   Geretourneerd wanneer:

   * het gewenste inhoudsfragment bestaat niet

* **500 (Interne serverfout)**

   >[!NOTE]
   >
   >Deze fout wordt geretourneerd:
   >
   >
   >
   >    * wanneer een fout is opgetreden die niet met een specifieke code kan worden geïdentificeerd
   >    * wanneer de opgegeven lading niet geldig was


   In het volgende voorbeeld worden algemene scenario&#39;s weergegeven wanneer deze foutstatus wordt geretourneerd, samen met het gegenereerde foutbericht (monospace):

   * Bovenliggende map bestaat niet (wanneer u een inhoudsfragment maakt via `POST`)
   * Er is geen model voor inhoudsfragmenten opgegeven (null-waarde), de bron is null (mogelijk een machtigingsprobleem) of de bron is geen geldige fragmentsjabloon:

      * `No content fragment model specified`
      * `Cannot create a resource of given model '/foo/bar/qux'`
      * `Cannot adapt the resource '/foo/bar/qux' to a content fragment template`
   * Het inhoudsfragment kan niet worden gemaakt (mogelijk een probleem met de machtigingen):

      * `Could not create content fragment`
   * Titel en/of beschrijving kunnen niet worden bijgewerkt:

      * `Could not set value on content fragment`
   * Kan metagegevens niet instellen:

      * `Could not set metadata on content fragment`
   * Het element Content kan niet worden gevonden of kan niet worden bijgewerkt

      * `Could not update content element`
      * `Could not update fragment data of element`

   De gedetailleerde foutberichten worden meestal als volgt geretourneerd:

   ```xml
   {
     "class": "core/response",
     "properties": {
       "path": "/api/assets/foo/bar/qux",
       "location": "/api/assets/foo/bar/qux.json",
       "parentLocation": "/api/assets/foo/bar.json",
       "status.code": 500,
       "status.message": "...{error message}.."
     }
   }
   ```

## API-referentie {#api-reference}

Zie hier voor gedetailleerde API-referenties:

* [Adobe Experience Manager Assets API - Inhoudsfragmenten](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/assets-api-content-fragments/index.html)
* [HTTP-API voor assets](/help/assets/mac-api-assets.md)

   * [Beschikbare functies](/help/assets/mac-api-assets.md#assets)

## Aanvullende bronnen {#additional-resources}

Zie voor meer informatie:

* [Elementen HTTP API-documentatie](/help/assets/mac-api-assets.md)
* [AEM Gem-sessie: OAuth](https://helpx.adobe.com/experience-manager/kt/eseminars/gems/aem-oauth-server-functionality-in-aem.html)

