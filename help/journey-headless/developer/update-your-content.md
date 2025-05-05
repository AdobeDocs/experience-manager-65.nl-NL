---
title: Uw inhoud bijwerken via AEM Assets API's
description: In dit deel van de AEM Headless Developer Journey leert u hoe u de REST API kunt gebruiken om toegang te krijgen tot de inhoud van de Content Fragments en deze bij te werken.
exl-id: af29cb77-0210-4fc4-8d86-2a833d19b49f
solution: Experience Manager, Experience Manager Sites
feature: Headless,Content Fragments,GraphQL,Persisted Queries,Developing
role: Admin, Developer
source-git-commit: 9a3008553b8091b66c72e0b6c317573b235eee24
workflow-type: tm+mt
source-wordcount: '1029'
ht-degree: 0%

---

# Uw inhoud bijwerken via AEM Assets API&#39;s {#update-your-content}

In dit deel van de [ AEM Zwaardeloze Reis van de Ontwikkelaar, ](overview.md) leert hoe te om REST API te gebruiken om tot de inhoud van uw Fragments van de Inhoud toegang te hebben en bij te werken.

## Het verhaal tot nu toe {#story-so-far}

In het vorige document van de AEM headless reis, [ hoe te om tot Uw Inhoud via AEM levering APIs toegang te hebben ](access-your-content.md) leerde u hoe te om tot uw inhoud zonder kop in AEM via GraphQL API toegang te hebben en u zou nu moeten:

* Een goed begrip van GraphQL.
* Begrijp hoe de AEM GraphQL API werkt.
* Begrijp sommige praktische steekproefvragen.

Dit artikel bouwt verder op deze basisbeginselen, zodat u begrijpt hoe u bestaande inhoud zonder kop in AEM kunt bijwerken via de REST API.

## Doelstelling {#objective}

* **Publiek**: Geavanceerd
* **Doelstelling**: Leer hoe te om REST API te gebruiken om tot de inhoud van uw Fragments van de Inhoud toegang te hebben en bij te werken:
   * Introduceer de AEM Assets HTTP API.
   * Introduceer en bespreek de ondersteuning voor inhoudsfragmenten in de API.
   * Details van de API illustreren.

<!--
  * Look at sample code to see how things work in practice.
-->

## Waarom hebt u de Assets HTTP API voor inhoudsfragmenten nodig? {#why-http-api}

In de vorige fase van de Headless Journey hebt u geleerd hoe u de AEM GraphQL API kunt gebruiken om uw inhoud op te halen met behulp van query&#39;s.

Waarom is er dus nog een API nodig?

De HTTP API van Assets laat u **&#x200B;**&#x200B;lezen uw inhoud, maar het laat u ook **&#x200B;**&#x200B;creëren, **Update** en **schrapt** inhoud - acties die niet met GraphQL API mogelijk zijn.

De Assets REST-API is beschikbaar voor elke installatie van een recente Adobe Experience Manager-versie die buiten de box valt.

## ASSETS HTTP API {#assets-http-api}

De Assets HTTP-API omvat:

* ASSETS REST API
* inclusief ondersteuning voor inhoudsfragmenten

De huidige implementatie van Assets HTTP API is gebaseerd op de **REST** architecturale stijl en laat u toe om tot inhoud toegang te hebben (die in AEM wordt opgeslagen) via **CRUD** verrichtingen (creeer, Gelezen, Update, Schrapping).

Met deze bewerking kunt u met de API Adobe Experience Manager gebruiken als een headless CMS (Content Management System) door Content Services aan te bieden aan een JavaScript front-end toepassing. Of elke andere toepassing die HTTP-aanvragen kan uitvoeren en JSON-reacties kan verwerken. Toepassingen voor één pagina (SPA), die zijn gebaseerd op een framework of die zijn aangepast, vereisen bijvoorbeeld inhoud die via een API wordt aangeboden, vaak in JSON-indeling.

<!--
>[!NOTE]
>
>It is not possible to customize JSON output from the Assets REST API. 

The Assets REST API:

* follows the HATEOAS principle
* implements the SIREN format

## Key Concepts {#key-concepts}

The Assets REST API offers REST-style access to assets stored within an AEM instance. 

It uses the `/api/assets` endpoint and requires the path of the asset to access it (without the leading `/content/dam`). 

* This means that to access the asset at:
  * `/content/dam/path/to/asset`
* You need to request:
  * `/api/assets/path/to/asset` 

For example, to access `/content/dam/wknd/en/adventures/cycling-tuscany`, request `/api/assets/wknd/en/adventures/cycling-tuscany.json` 

>[!NOTE]
>Access over:
>
>* `/api/assets` **does not** need the use of the `.model` selector.
>* `/content/path/to/page` **does** require the use of the `.model` selector.

The HTTP method determines the operation to be executed:

* **GET** - to retrieve a JSON representation of an asset or a folder
* **POST** - to create new assets or folders
* **PUT** - to update the properties of an asset or folder
* **DELETE** - to delete an asset or folder

>[!NOTE]
>
>The request body and/or URL parameters can be used to configure some of these operations; for example, define that a folder or an asset should be created by a **POST** request.

The exact format of supported requests is defined in the API Reference documentation. 

### Transactional Behavior {#transactional-behavior}

All requests are atomic.

This means that subsequent (`write`) requests cannot be combined into a single transaction that could succeed or fail as a single entity.

### Security {#security}

If the Assets REST API is used within an environment without specific authentication requirements, AEM's CORS filter needs to be configured correctly.

>[!NOTE]
>
>For further information see:
>
>* CORS/AEM explained
>* Video - Developing for CORS with AEM

In environments with specific authentication requirements, OAuth is recommended.

## Available Features {#available-features}

Content Fragments are a specific type of Asset, see Working with Content Fragments.

For further information about features available through the API see:

* The Assets REST API (Additional Resources) 
* Entity Types, where the features specific to each supported type (as relevant to Content Fragments) are explained 

### Paging {#paging}

The Assets REST API supports paging (for GET requests) via the URL parameters:

* `offset` - the number of the first (child) entity to retrieve
* `limit` - the maximum number of entities returned

The response will contain paging information as part of the `properties` section of the SIREN output. This `srn:paging` property contains the total number of (child) entities ( `total`), the offset and the limit ( `offset`, `limit`) as specified in the request.

>[!NOTE]
>
>Paging is typically applied on container entities (that is, folders or assets with renditions), as it relates to the children of the requested entity.

#### Example: Paging {#example-paging}

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

## Entity Types {#entity-types}

### Folders {#folders}

Folders act as containers for assets and other folders. They reflect the structure of the AEM content repository.

The Assets REST API exposes access to the properties of a folder; for example, its name, title, and so on. Assets are exposed as child entities of folders, and sub-folders.

>[!NOTE]
>
>Depending on the asset type of the child assets and folders the list of child entities may already contain the full set of properties that defines the respective child entity. Alternatively, only a reduced set of properties may be exposed for an entity in this list of child entities.

### Assets {#assets}

If an asset is requested, the response will return its metadata; such as title, name and other information as defined by the respective asset schema.

The binary data of an asset is exposed as a SIREN link of type `content`.

Assets can have multiple renditions. These are typically exposed as child entities, one exception being a thumbnail rendition, which is exposed as a link of type `thumbnail` ( `rel="thumbnail"`).
-->

## Assets HTTP API- en inhoudsfragmenten {#assets-http-api-content-fragments}

Inhoudsfragmenten worden gebruikt voor levering zonder kop en een inhoudsfragment is een speciaal type element. Ze worden gebruikt om onder andere toegang te krijgen tot gestructureerde gegevens, zoals teksten, getallen, datums.

<!--
As there are several differences to *standard* assets (such as images or audio), some additional rules apply to handling them.

### Representation {#representation}

Content fragments:

* Do not expose any binary data.
* Are completely contained in the JSON output (within the `properties` property).

* Are also considered atomic, that is, the elements and variations are exposed as part of the fragment's properties vs. as links or child entities. This allows for efficient access to the payload of a fragment.

### Content Models and Content Fragments {#content-models-and-content-fragments}

Currently the models that define the structure of a content fragment are not exposed through an HTTP API. Therefore the *consumer* needs to know about the model of a fragment (at least a minimum) - although most information can be inferred from the payload; as data types, and so on. are part of the definition.

To create a content fragment, the (internal repository) path of the model has to be provided.

### Associated Content {#associated-content}

Associated content is currently not exposed.
-->

## De Assets REST API gebruiken {#using-aem-assets-rest-api}

### Toegang {#access}

De Assets REST-API gebruikt het `/api/assets` -eindpunt en vereist het pad van het element om het te openen (zonder de regelafstand `/content/dam` ).

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

### Bewerking {#operation}

De HTTP-methode bepaalt de uit te voeren bewerking:

* **GET** - om een vertegenwoordiging JSON van activa of een omslag terug te winnen
* **POST** - om nieuwe activa of omslagen te creëren
* **PUT** - om de eigenschappen van een activa of een omslag bij te werken
* **DELETE** - om activa of een omslag te schrappen

>[!NOTE]
>
>De verzoeklichaam en/of parameters URL kunnen worden gebruikt om sommige van deze verrichtingen te vormen; bijvoorbeeld, bepaal dat een omslag of een activa door a **POST** verzoek zou moeten worden gecreeerd.

De exacte indeling van ondersteunde aanvragen wordt gedefinieerd in de API-naslagdocumentatie.

Het gebruik kan verschillen afhankelijk van of u een AEM auteur of publicatieomgeving gebruikt, samen met uw specifieke gebruiksscenario.

* Het wordt sterk aanbevolen dat het maken is gebonden aan een instantie van de auteur (en momenteel is er geen manier om een fragment te repliceren om te publiceren met behulp van deze API).
* De levering is mogelijk van beide, aangezien AEM gevraagde inhoud in formaat slechts JSON dient.

   * Opslag en levering vanuit een AEM auteur-instantie zouden voldoende moeten zijn voor toepassingen achter de firewall, in de mediabibliotheek.

   * Voor live webweergave wordt een AEM-publicatie-instantie aanbevolen.

>[!CAUTION]
>
>De configuratie van de verzender voor AEM instanties kan de toegang tot `/api` blokkeren.

>[!NOTE]
>
>Zie de API-naslaggids voor meer informatie. In het bijzonder, [ Adobe Experience Manager Assets API - de Fragmenten van de Inhoud ](https://www.adobe.io/experience-manager/reference-materials/6-5/assets-api-content-fragments/index.html).

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

Voor meer informatie over het gebruik van de AEM Assets REST API kunt u verwijzen naar:

* Adobe Experience Manager Assets HTTP API (extra bronnen)
* Ondersteuning voor inhoudsfragmenten in AEM Assets HTTP API (extra bronnen)

## Volgende functies {#whats-next}

Nu u dit deel van de AEM Headless Developer Journey hebt voltooid, moet u:

* Begrijp de basisbeginselen van de AEM Assets HTTP API.
* Begrijp hoe de Fragments van de Inhoud in deze API worden gesteund.

<!--
* Have experience with sample code and know how the API works in practice.
-->

<!-- The "How to put it all together" page is not going to be published until the first public release of the Headless SDK. Temporarily commenting out the reference below. -->

<!--You should continue your AEM headless journey by next reviewing the document [How to Put It All Together - Your App and Your Content in AEM Headless](put-it-all-together.md) where you learn how to take your AEM Headless project and prepare it for going live.-->

U zou uw AEM headless reis door het document [ te herzien moeten voortzetten hoe te met Uw Zwaarloze Toepassing ](go-live.md) gaan waar u eigenlijk uw AEM Zwaardeloos project neemt levend!

## Aanvullende bronnen {#additional-resources}

* [ASSETS HTTP API](/help/assets/mac-api-assets.md)
* [Content Fragments REST API](/help/assets/assets-api-content-fragments.md)
   * [API-naslag](/help/assets/assets-api-content-fragments.md#api-reference)
* [ Adobe Experience Manager Assets API - de Fragmenten van de Inhoud ](https://www.adobe.io/experience-manager/reference-materials/6-5/assets-api-content-fragments/index.html)
* [Werken met inhoudsfragmenten](/help/assets/content-fragments/content-fragments.md)
* [ AEM de Componenten van de Kern ](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/introduction.html?lang=nl-NL)
* [ verklaarde CORS/AEM ](https://helpx.adobe.com/experience-manager/kt/platform-repository/using/cors-security-article-understand.html)
* [ Video - het Ontwikkelen voor CORS met AEM ](https://helpx.adobe.com/experience-manager/kt/platform-repository/using/cors-security-technical-video-develop.html)
* Een [ Inleiding aan AEM als Zwaartepunt CMS ](/help/sites-developing/headless/introduction.md)
* Het [ AEM Portaal van de Ontwikkelaar ](https://experienceleague.adobe.com/landing/experience-manager/headless/developer.html?lang=nl-NL)
* [ Tutorials voor Zwaartepunt in AEM ](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-with-aem-headless/overview.html?lang=nl-NL)
