---
title: Adobe Experience Manager Content Fragments Support in Assets HTTP API
description: Leer over steun voor de Fragments van de Inhoud in Assets HTTP API, een belangrijk stuk van het AEM van koploze leveringseigenschap.
feature: Content Fragments,Assets HTTP API
role: Developer
exl-id: 0f9efb47-a8d1-46d9-b3ff-a6c0741ca138
hide: true
solution: Experience Manager, Experience Manager Assets
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '1902'
ht-degree: 0%

---

# Ondersteuning voor inhoudsfragmenten in AEM Assets HTTP API {#content-fragments-support-in-aem-assets-http-api}

| Versie | Artikelkoppeling |
| -------- | ---------------------------- |
| AEM as a Cloud Service | [&#x200B; klik hier &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/assets/admin/assets-api-content-fragments.html?lang=nl-NL) |
| AEM 6,5 | Dit artikel |


## Overzicht {#overview}

Leer over steun voor de Fragments van de Inhoud in Assets HTTP API, een belangrijk stuk van het AEM van koploze leveringseigenschap.

>[!NOTE]
>
>[&#x200B; HTTP API van Assets &#x200B;](/help/assets/mac-api-assets.md) omvat:
>
>* ASSETS REST API
>* inclusief ondersteuning voor inhoudsfragmenten
>
>De huidige implementatie van Assets HTTP API is gebaseerd op de [&#x200B; REST &#x200B;](https://en.wikipedia.org/wiki/Representational_state_transfer) architecturale stijl.

[&#x200B; Assets REST API &#x200B;](/help/assets/mac-api-assets.md) staat ontwikkelaars voor Adobe Experience Manager toe om tot inhoud (die in AEM wordt opgeslagen) direct over HTTP API, via CRUD verrichtingen (creeer, Lees, Update, Schrapping) toegang te hebben.

Met de API kunt u Adobe Experience Manager gebruiken als een CMS zonder kop (Content Management System) door Content Services aan te bieden aan een JavaScript front-end toepassing. Of elke andere toepassing die HTTP-aanvragen kan uitvoeren en JSON-reacties kan verwerken.

Toepassingen voor één pagina (SPA), die zijn gebaseerd op een framework of die zijn aangepast, vereisen bijvoorbeeld inhoud die via de HTTP-API wordt aangeboden, vaak in de JSON-indeling.

Terwijl [&#x200B; AEM de Componenten van de Kern &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/introduction.html?lang=nl-NL) een zeer uitvoerige, flexibele en klantgerichte API verstrekken die vereiste Gelezen verrichtingen voor dit doel kan dienen, en de waarvan output JSON kan worden aangepast, vereisen zij AEM WCM (het Beheer van de Inhoud van het Web) knowhow voor implementatie aangezien zij in pagina&#39;s moeten worden ontvangen die op specifieke AEM malplaatjes gebaseerd zijn. Niet elke SPA ontwikkelingsorganisatie heeft directe toegang tot deze kennis.

Dit is wanneer de Assets REST API kan worden gebruikt. Ontwikkelaars hebben direct toegang tot elementen (bijvoorbeeld afbeeldingen en inhoudsfragmenten), zonder dat ze eerst in een pagina moeten worden ingesloten en hun inhoud in geserialiseerde JSON-indeling moeten leveren.

>[!NOTE]
>
>Het is niet mogelijk JSON-uitvoer van de Assets REST API aan te passen.

Met de Assets REST API kunnen ontwikkelaars ook inhoud wijzigen door nieuwe elementen, inhoudsfragmenten en mappen te maken, bij te werken of te verwijderen.

De Assets REST API:

* volgt het [&#x200B; HATEOAS beginsel &#x200B;](https://en.wikipedia.org/wiki/HATEOAS)

* voert het [&#x200B; formaat SIREN &#x200B;](https://github.com/kevinswiber/siren) uit

## Vereisten {#prerequisites}

De Assets REST API is beschikbaar voor elke installatie van een recente AEM.

## Belangrijke concepten {#key-concepts}

Assets REST API biedt [&#x200B; REST &#x200B;](https://en.wikipedia.org/wiki/Representational_state_transfer) - stijltoegang tot activa aan die binnen een AEM instantie worden opgeslagen.

De methode gebruikt het eindpunt `/api/assets` en vereist het pad van het element om het te openen (zonder de regelafstand `/content/dam` ).

* Dit betekent dat toegang tot het actief moet worden verkregen tegen:
   * `/content/dam/path/to/asset`
* U moet een aanvraag indienen:
   * `/api/assets/path/to/asset`

Als u bijvoorbeeld toegang wilt krijgen tot `/content/dam/wknd/en/adventures/cycling-tuscany` , vraagt u om `/api/assets/wknd/en/adventures/cycling-tuscany.json`

>[!NOTE]
>Toegang over:
>
>* `/api/assets` **&#x200B;**&#x200B;nodig niet het gebruik van `.model` selecteur.
>* `/content/path/to/page` **&#x200B;**&#x200B;vereist het gebruik van `.model` selecteur.

De HTTP-methode bepaalt de uit te voeren bewerking:

* **GET** - om een vertegenwoordiging JSON van activa of een omslag terug te winnen
* **POST** - om nieuwe activa of omslagen te creëren
* **PUT** - om de eigenschappen van een activa of een omslag bij te werken
* **DELETE** - om activa of een omslag te schrappen

>[!NOTE]
>
>De verzoeklichaam en/of parameters URL kunnen worden gebruikt om sommige van deze verrichtingen te vormen; bijvoorbeeld, bepaal dat een omslag of een activa door a **POST** verzoek zou moeten worden gecreeerd.

Het nauwkeurige formaat van gesteunde verzoeken wordt bepaald in de [&#x200B; API documentatie van de Verwijzing &#x200B;](/help/assets/assets-api-content-fragments.md#api-reference).

### Transactioneel gedrag {#transactional-behavior}

Alle verzoeken zijn atomisch.

Dit betekent dat de verdere (`write`) verzoeken niet in één enkele transactie kunnen worden gecombineerd die als één enkele entiteit kon slagen of ontbreken.

### AEM (Assets) REST API versus AEM componenten {#aem-assets-rest-api-versus-aem-components}

<table>
 <thead>
  <tr>
   <td>Verhouding</td>
   <td>Assets REST API <br/> </td>
   <td>AEM Component <br/> (componenten die Sling Models gebruiken)</td>
  </tr>
 </thead>
 <tbody>
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
   <td><p>Kan rechtstreeks worden benaderd.</p> <p>Gebruikt het <code>/api/assets </code> eindpunt, in kaart gebracht aan <code>/content/dam</code> (in de bewaarplaats).</p> 
   <p>Een voorbeeldpad zou er als volgt uitzien: <code>/api/assets/wknd/en/adventures/cycling-tuscany.json</code></p>
   </td>
    <td><p>Moet door een AEM component op een AEM pagina worden van verwijzingen voorzien.</p> <p>Gebruikt de kiezer van <code>.model</code> om de JSON-representatie te maken.</p> <p>Een voorbeeldpad zou er als volgt uitzien:<br/> <code>/content/wknd/language-masters/en/adventures/cycling-tuscany.model.json</code></p> 
   </td>
  </tr>
  <tr>
   <td>Beveiliging</td>
   <td><p>Er zijn meerdere opties mogelijk.</p> <p>OAuth wordt voorgesteld; kan los van standaardopstelling worden gevormd.</p> </td>
   <td>Gebruikt AEM standaard installatie.</td>
  </tr>
  <tr>
   <td>Architecten</td>
   <td><p>Schrijftoegang richt zich gewoonlijk tot een auteurinstantie.</p> <p>Lees kan ook naar een publicatie-instantie worden gestuurd.</p> </td>
   <td>Aangezien deze benadering read-only is, zal het typisch voor publiceer instanties worden gebruikt.</td>
  </tr>
  <tr>
   <td>Uitvoer</td>
   <td>SIREN-uitvoer gebaseerd op JSON: uitgebreid, maar krachtig. Hiermee kunt u navigeren binnen de inhoud.</td>
   <td>Op JSON gebaseerde eigen uitvoer; configureerbaar via Sling Models. Navigeren door de inhoudsstructuur is moeilijk te implementeren (maar niet noodzakelijkerwijs onmogelijk).</td>
  </tr>
 </tbody>
</table>

### Beveiliging {#security}

Als de Assets REST API wordt gebruikt binnen een omgeving zonder specifieke verificatievereisten, moet AEM CORS-filter correct worden geconfigureerd.

>[!NOTE]
>
>Zie voor meer informatie:
>
>* [&#x200B; verklaarde CORS/AEM &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-learn/foundation/security/understand-cross-origin-resource-sharing.html?lang=nl-NL)
>* [&#x200B; Video - het Ontwikkelen voor CORS met AEM &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-learn/foundation/security/develop-for-cross-origin-resource-sharing.html?lang=nl-NL)
>

In omgevingen met specifieke verificatievereisten wordt OAuth aanbevolen.

## Beschikbare functies {#available-features}

De Fragmenten van de inhoud zijn een specifiek type van Activa, zie [&#x200B; Werkend met de Fragmenten van de Inhoud &#x200B;](/help/assets/content-fragments/content-fragments.md).

Zie voor meer informatie over functies die beschikbaar zijn via de API:

* [&#x200B; Assets REST API &#x200B;](/help/assets/mac-api-assets.md)
* [&#x200B; Types van Entiteit &#x200B;](/help/assets/assets-api-content-fragments.md#entity-types), waar de eigenschappen specifiek voor elk gesteund type (zoals relevant voor de Fragmenten van de Inhoud) worden verklaard

### Paginering {#paging}

De Assets REST API ondersteunt paginering (voor GET-aanvragen) via de URL-parameters:

* `offset` - het nummer van de eerste (onderliggende) entiteit die moet worden opgehaald
* `limit` - het maximale aantal geretourneerde entiteiten

De reactie bevat pagineringsinformatie als onderdeel van de sectie `properties` van de SIREN-uitvoer. Deze eigenschap `srn:paging` bevat het totale aantal (onderliggende) entiteiten ( `total` ), de verschuiving en de limiet ( `offset` , `limit` ) zoals opgegeven in de aanvraag.

>[!NOTE]
>
>Pagina&#39;s worden doorgaans toegepast op containerentiteiten (dat wil zeggen mappen of elementen met uitvoeringen), omdat ze betrekking hebben op de onderliggende elementen van de aangezochte entiteit.

#### Voorbeeld: Pagelen {#example-paging}

`GET /api/assets.json?offset=2&limit=3`

```json
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

De Assets REST-API stelt toegang beschikbaar tot de eigenschappen van een map, bijvoorbeeld de naam, titel, enzovoort. Assets wordt weergegeven als onderliggende entiteiten van mappen en submappen.

>[!NOTE]
>
>Afhankelijk van het type element van de onderliggende elementen en mappen bevat de lijst met onderliggende entiteiten mogelijk al de volledige set eigenschappen die de onderliggende entiteit definieert. Alternatief, slechts kan een beperkte reeks eigenschappen voor een entiteit in deze lijst van kindentiteiten worden blootgesteld.

### Assets {#assets}

Als een element wordt aangevraagd, retourneert het antwoord de metagegevens van het element, zoals de titel, de naam en andere informatie, zoals gedefinieerd in het desbetreffende elementschema.

De binaire gegevens van een element worden weergegeven als een SIREN-koppeling van het type `content` .

Assets kan meerdere uitvoeringen hebben. Deze worden doorgaans weergegeven als onderliggende entiteiten, waarbij één uitzondering een miniatuuruitvoering is die wordt weergegeven als een koppeling van het type `thumbnail` ( `rel="thumbnail"` ).

### Inhoudsfragmenten {#content-fragments}

A [&#x200B; inhoudsfragment &#x200B;](/help/assets/content-fragments/content-fragments.md) is een speciaal type van activa. Ze kunnen worden gebruikt om onder andere toegang te krijgen tot gestructureerde gegevens, zoals tekst, getallen, datums.

Aangezien er verscheidene verschillen aan *standaard* activa (zoals beelden of audio) zijn, zijn sommige extra regels van toepassing op de behandeling van hen.

#### Vertegenwoordiging {#representation}

Inhoudsfragmenten:

* Maak geen binaire gegevens beschikbaar.
* Deze bevinden zich volledig in de JSON-uitvoer (binnen de eigenschap `properties` ).

* Wordt ook als atomisch beschouwd, dat wil zeggen dat de elementen en variaties worden blootgesteld als onderdeel van de eigenschappen van het fragment in plaats van als koppelingen of onderliggende entiteiten. Op deze manier hebt u efficiënt toegang tot de lading van een fragment.

#### Inhoudsmodellen en inhoudsfragmenten {#content-models-and-content-fragments}

De modellen die de structuur van een inhoudsfragment definiëren, worden momenteel niet via een HTTP-API weergegeven. Daarom moet de *consument* over het model van een fragment (minstens een minimum) weten - hoewel de meeste informatie van de nuttige lading kan worden afgeleid; als gegevenstypes, etc. maken deel uit van de definitie.

Als u een inhoudsfragment wilt maken, moet u het pad (interne gegevensopslagruimte) van het model opgeven.

#### Gekoppelde inhoud {#associated-content}

Gekoppelde inhoud wordt momenteel niet weergegeven.

## Gebruiken {#using}

Het gebruik kan verschillen afhankelijk van of u een AEM auteur of publicatieomgeving gebruikt, samen met uw specifieke gebruiksscenario.

* Het wordt sterk geadviseerd dat de verwezenlijking aan een auteursinstantie ([&#x200B; verbindend is en momenteel is er geen middel om een fragment te herhalen om te publiceren gebruikend dit API &#x200B;](/help/assets/assets-api-content-fragments.md#limitations)).
* De levering is mogelijk van beide, aangezien AEM gevraagde inhoud in formaat slechts JSON dient.

   * Opslag en levering vanuit een AEM auteur-instantie zouden voldoende moeten zijn voor toepassingen achter de firewall, in de mediabibliotheek.

   * Voor live webweergave wordt een AEM-publicatie-instantie aanbevolen.

>[!CAUTION]
>
>De configuratie van de verzender voor AEM instanties kan de toegang tot `/api` blokkeren.

>[!NOTE]
>
>Voor verdere details, zie de [&#x200B; API Verwijzing &#x200B;](/help/assets/assets-api-content-fragments.md#api-reference). In het bijzonder, [&#x200B; Adobe Experience Manager Assets API - de Fragmenten van de Inhoud &#x200B;](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/assets-api-content-fragments/index.html).

### Lezen/Levering {#read-delivery}

Gebruik gebeurt via:

`GET /{cfParentPath}/{cfName}.json`

Bijvoorbeeld:

`http://<host>/api/assets/wknd/en/adventures/cycling-tuscany.json`

De reactie is geserialiseerd met JSON met de inhoud gestructureerd zoals in het inhoudsfragment. Referenties worden als referentie-URL&#39;s geleverd.

Er zijn twee typen leesbewerkingen mogelijk:

* Als u een specifiek inhoudsfragment leest per pad, wordt hiermee de JSON-representatie van het inhoudsfragment geretourneerd.
* Een map met inhoudsfragmenten lezen op pad: hiermee worden de JSON-representaties van alle inhoudsfragmenten in de map geretourneerd.

### Maken {#create}

Gebruik gebeurt via:

`POST /{cfParentPath}/{cfName}`

De hoofdtekst moet een JSON-representatie bevatten van het inhoudsfragment dat moet worden gemaakt, inclusief de initiële inhoud die moet worden ingesteld op de elementen van het inhoudsfragment. Het is verplicht de eigenschap `cq:model` in te stellen en deze moet verwijzen naar een geldig inhoudsfragmentmodel. Als u dit niet doet, treedt er een fout op. U moet ook een koptekst `Content-Type` toevoegen die is ingesteld op `application/json` .

### Bijwerken {#update}

Gebruik is via

`PUT /{cfParentPath}/{cfName}`

De hoofdtekst moet een JSON-representatie bevatten van wat voor het opgegeven inhoudsfragment moet worden bijgewerkt.

Dit kan gewoon de titel of beschrijving zijn van een inhoudsfragment, of één element, of alle elementwaarden en/of metagegevens.

### Verwijderen {#delete}

Gebruik gebeurt via:

`DELETE /{cfParentPath}/{cfName}`

## Beperkingen {#limitations}

Er zijn een paar beperkingen:

* **de fragmentmodellen van de Inhoud worden momenteel niet gesteund**: zij kunnen niet worden gelezen of worden gecreeerd. Ontwikkelaars moeten het juiste pad naar het fragmentmodel van de inhoud kennen om een inhoudsfragment te kunnen maken of een bestaand fragment bij te werken. Momenteel is de enige methode om een overzicht van deze te krijgen door het beleid UI.
* **Verwijzingen worden genegeerd**. Er wordt momenteel niet gecontroleerd of naar een bestaand inhoudsfragment wordt verwezen. Daarom kan het verwijderen van een inhoudsfragment bijvoorbeeld resulteren in problemen op een pagina die een verwijzing naar het verwijderde inhoudsfragment bevat.
* **JSON gegevenstype** REST API output van het *JSON gegevenstype* is momenteel *koord gebaseerde output*.

## Statuscodes en foutberichten {#status-codes-and-error-messages}

De volgende statuscodes kunnen in de relevante omstandigheden worden gezien:

* **200** (OK)
Geretourneerd wanneer:

   * een inhoudsfragment aanvragen via `GET`
   * een inhoudsfragment bijwerken via `PUT`

* **201** (Gemaakt)
Geretourneerd wanneer:

   * een inhoudsfragment maken via `POST`

* **404** (Niet gevonden)
Geretourneerd wanneer:

   * het gewenste inhoudsfragment bestaat niet

* **500** (Interne serverfout)

  >[!NOTE]
  >
  >Deze fout wordt geretourneerd:
  >
  >* wanneer een fout is opgetreden die niet met een specifieke code kan worden geïdentificeerd
  >* wanneer de opgegeven lading niet geldig was

  In het volgende voorbeeld worden algemene scenario&#39;s weergegeven wanneer deze foutstatus wordt geretourneerd, samen met het gegenereerde foutbericht (monospace):

   * Bovenliggende map bestaat niet (wanneer u een inhoudsfragment maakt via `POST`)
   * Er is geen inhoudsfragmentmodel opgegeven (cq:model ontbreekt), kan niet worden gelezen (vanwege een ongeldig pad of een machtigingsprobleem) of er is geen geldig fragmentmodel:

      * `No content fragment model specified`
      * `Cannot create a resource of given model '/foo/bar/qux'`

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

## API-naslag {#api-reference}

Zie hier voor gedetailleerde API-referenties:

* [&#x200B; Adobe Experience Manager Assets API - de Fragmenten van de Inhoud &#x200B;](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/assets-api-content-fragments/index.html)
* [ASSETS HTTP API](/help/assets/mac-api-assets.md)

   * [Beschikbare functies](/help/assets/mac-api-assets.md#assets)

## Aanvullende bronnen {#additional-resources}

Zie voor meer informatie:

* [Assets HTTP API-documentatie](/help/assets/mac-api-assets.md)
* [&#x200B; AEM de zitting van Gem: OAuth &#x200B;](https://helpx.adobe.com/nl/experience-manager/kt/eseminars/gems/aem-oauth-server-functionality-in-aem.html)
