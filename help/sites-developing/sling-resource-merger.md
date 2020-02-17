---
title: Het gebruiken van de Verschuivende Samenvoeging van het Middel in AEM
seo-title: Het gebruiken van de Verschuivende Samenvoeging van het Middel in AEM
description: De het Verdelen Samenvoeging van het Middel verleent de diensten om tot middelen toegang te hebben en samen te voegen
seo-description: De het Verdelen Samenvoeging van het Middel verleent de diensten om tot middelen toegang te hebben en samen te voegen
uuid: 0a28fdc9-caea-490b-8f07-7c4a6b802e09
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: platform
content-type: reference
discoiquuid: ec712ba0-0fd6-4bb8-93d6-07d09127df58
translation-type: tm+mt
source-git-commit: 5128a08d4db21cda821de0698b0ac63ceed24379

---


# Het gebruiken van de Verschuivende Samenvoeging van het Middel in AEM{#using-the-sling-resource-merger-in-aem}

## Doel {#purpose}

Sling Resource Merger verleent de diensten om tot middelen toegang te hebben en samen te voegen. Het verstrekt afdiff (differentiërende) mechanismen voor allebei:

* **[Bedekkingen](/help/sites-developing/overlays.md)**van bronnen die de[geconfigureerde zoekpaden](/help/sites-developing/overlays.md#configuring-the-search-paths)gebruiken.

* **Overschrijft** de componentdialoogvensters voor de interface met aanraakbediening (`cq:dialog`) met behulp van de hiërarchie van het middeltype (via de eigenschap `sling:resourceSuperType`).

Met de Verschuivende Fusie van het Middel, worden de bedekking/met voeten getreden middelen en/of de eigenschappen samengevoegd met de originele middelen/eigenschappen:

* De inhoud van de aangepaste definitie heeft een hogere prioriteit dan die van het origineel (d.w.z. het *bedekt* of treedt *het met voeten* ).

* Indien nodig, geven de [eigenschappen](#properties) die in de aanpassing worden gedefinieerd aan hoe de inhoud die van het origineel is samengevoegd, moet worden gebruikt.

>[!CAUTION]
>
>De Sling Resource Merger en verwante methodes kunnen slechts met [Granite](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/granite-ui/api/index.html)worden gebruikt. Dit betekent ook dat het alleen geschikt is voor de standaardinterface met aanraakbediening. met name overschrijvingen die op deze manier worden gedefinieerd, zijn alleen van toepassing op het aanraakdialoogvenster van een component.
>
>Bij overlays/overschrijvingen voor andere gebieden (waaronder andere aspecten van een aanraakcomponent of de klassieke UI) worden het juiste knooppunt en de juiste structuur van het origineel naar waar de aanpassing wordt gedefinieerd, gekopieerd.

### Doelen voor AEM {#goals-for-aem}

De doelstellingen voor het gebruiken van de Verschuivende Fusie van het Middel in AEM zijn:

* ervoor zorgen dat er geen wijzigingen in de aanpassing worden aangebracht `/libs`.
* vermindert de structuur waarvan wordt gerepliceerd `/libs`.

   Wanneer het gebruiken van de Verzameling van het Middel wordt het niet geadviseerd om de volledige structuur van te kopiëren `/libs` aangezien dit in teveel informatie zou resulteren die in de aanpassing (gewoonlijk `/apps`) wordt gehouden. Het dupliceren van informatie vergroot onnodig de kans op problemen wanneer het systeem op om het even welke manier wordt verbeterd.

>[!NOTE]
>
>Overschrijvingen zijn niet afhankelijk van de zoekpaden. Ze gebruiken de eigenschap `sling:resourceSuperType` om de verbinding te maken.
>
>Overschrijvingen worden echter vaak gedefinieerd in het kader van `/apps`AEM, aangezien de beste praktijken in AEM aanpassingen onder `/apps`moeten bepalen; dat komt omdat je niets moet veranderen onder `/libs`.

>[!CAUTION]
>
>U ***mag*** niets in het `/libs` pad wijzigen.
>
>De reden hiervoor is dat de inhoud van `/libs` de volgende keer dat u een upgrade uitvoert van uw exemplaar, wordt overschreven (en dat deze inhoud ook kan worden overschreven wanneer u een hotfix- of functiepakket toepast).
>
>De aanbevolen methode voor configuratie en andere wijzigingen is:
>
>1. Het vereiste item opnieuw maken (d.w.z. zoals het in `/libs`) `/apps`
   >
   >
1. Breng wijzigingen aan in `/apps`
>



### Eigenschappen {#properties}

De resourcefusie biedt de volgende eigenschappen:

* `sling:hideProperties` ( `String` of `String[]`)

   Geeft de eigenschap op, of een lijst met eigenschappen, die moet worden verborgen.

   Alle jokertekens `*` worden verborgen.

* `sling:hideResource` ( `Boolean`)

   Geeft aan of de bronnen volledig verborgen moeten zijn, inclusief de onderliggende elementen.

* `sling:hideChildren` ( `String` of `String[]`)

   Bevat het onderliggende knooppunt of de lijst met onderliggende knooppunten die moet worden verborgen. De eigenschappen van het knooppunt blijven behouden.

   Alle jokertekens `*` worden verborgen.

* `sling:orderBefore` ( `String`)

   Bevat de naam van de sibling knoop die de huidige knoop voor van zou moeten worden geplaatst.

Deze eigenschappen beïnvloeden hoe de overeenkomstige/originele middelen/eigenschappen (van `/libs`) door de bekleding/de opheffing (vaak in `/apps`) worden gebruikt.

### De structuur maken {#creating-the-structure}

Als u een bedekking wilt maken of overschrijven, moet u het oorspronkelijke knooppunt opnieuw maken, met de equivalente structuur, onder het doel (gewoonlijk `/apps`). Bijvoorbeeld:

* Bedekking

   * De definitie van het navigatie-item voor de Sites-console, zoals weergegeven in de spoorstaaf, is gedefinieerd op:

      `/libs/cq/core/content/nav/sites/jcr:title`

   * Als u dit wilt bedekken, maakt u het volgende knooppunt:

      `/apps/cq/core/content/nav/sites`

      Werk de eigenschap vervolgens `jcr:title` naar wens bij.

* Negeren

   * De definitie van het aanraakdialoogvenster voor de tekstconsole is als volgt:

      `/libs/foundation/components/text/cq:dialog`

   * Als u dit wilt overschrijven, maakt u het volgende knooppunt, bijvoorbeeld:

      `/apps/the-project/components/text/cq:dialog`

Als u een van deze opties wilt maken, hoeft u alleen de skeletstructuur opnieuw te maken. Om de recreatie van de structuur te vereenvoudigen kunnen alle intermediaire knopen van type zijn `nt:unstructured` (zij moeten niet het originele knooptype weerspiegelen; bijvoorbeeld in `/libs`).

In het bovenstaande overlayvoorbeeld zijn dus de volgende knooppunten nodig:

```shell
/apps
  /cq
    /core
      /content
        /nav
          /sites
```

>[!NOTE]
>
>Wanneer het gebruiken van de Verzameling van het Middel (d.w.z. wanneer het behandelen van de norm, aanraking-toegelaten UI) wordt het niet geadviseerd om de volledige structuur van te kopiëren `/libs` aangezien het in teveel informatie zou resulteren die in wordt gehouden `/apps`. Dit kan problemen veroorzaken wanneer het systeem op om het even welke manier wordt bevorderd.

### Gevallen gebruiken {#use-cases}

Deze, samen met standaardfunctionaliteit, laten u toe:

* **Een eigenschap toevoegen**

   De eigenschap bestaat niet in de `/libs` definitie, maar is vereist in de `/apps` overlay/overschrijving.

   1. Maak het corresponderende knooppunt binnen `/apps`
   1. Maak de nieuwe eigenschap op dit knooppunt &quot;

* **Een eigenschap opnieuw definiëren (geen automatisch gemaakte eigenschappen)**

   De eigenschap is gedefinieerd in `/libs`, maar er is een nieuwe waarde vereist in de `/apps` overlay/overschrijving.

   1. Maak het corresponderende knooppunt binnen `/apps`
   1. De overeenkomende eigenschap op dit knooppunt maken (onder / `apps`)

      * Het bezit zal een prioriteit hebben die op de het Verspreiden configuratie van de Resolver van het Middel wordt gebaseerd.
      * Het wijzigen van het type eigenschap wordt ondersteund.

         Als u een type eigenschap gebruikt dat verschilt van het type dat wordt gebruikt in, `/libs`wordt het type eigenschap gebruikt dat u definieert.
   >[!NOTE]
   >
   >Het wijzigen van het type eigenschap wordt ondersteund.

* **Een automatisch gemaakte eigenschap opnieuw definiëren**

   Standaard zijn automatisch gemaakte eigenschappen (zoals `jcr:primaryType`) niet onderhevig aan een overlay/overschrijving om ervoor te zorgen dat het knooppunttype dat momenteel onder `/libs` deze instelling valt, wordt gerespecteerd. Als u een bedekking/overschrijving wilt toepassen, moet u het knooppunt opnieuw maken in `/apps`, moet u de eigenschap expliciet verbergen en opnieuw definiëren:

   1. Maak het corresponderende knooppunt onder `/apps` de gewenste `jcr:primaryType`
   1. Maak de eigenschap `sling:hideProperties` op dat knooppunt, met de waarde ingesteld op die van de eigenschap auto-created; bijvoorbeeld: `jcr:primaryType`

      Deze eigenschap, gedefinieerd onder `/apps`2, krijgt nu voorrang boven de eigenschap gedefinieerd onder `/libs`

* **Een knooppunt en de onderliggende knooppunten opnieuw definiëren**

   De knoop en zijn kinderen worden bepaald in `/libs`, maar een nieuwe configuratie wordt vereist in de `/apps` overlay/de opheffing.

   1. Combineer de handelingen van:

      1. Onderliggende items van een knooppunt verbergen (de eigenschappen van het knooppunt behouden)
      1. Eigenschappen opnieuw definiëren

* **Een eigenschap verbergen**

   De eigenschap wordt gedefinieerd in, maar is niet vereist in de `/libs``/apps` overlay/overschrijving.

   1. Maak het corresponderende knooppunt binnen `/apps`
   1. Maak een eigenschap `sling:hideProperties` van het type `String` of `String[]`. Met deze optie geeft u de eigenschappen op die moeten worden verborgen of genegeerd. Jokertekens kunnen ook worden gebruikt. Bijvoorbeeld:

      * `*`
      * `["*"]`
      * `jcr:title`
      * `["jcr:title", "jcr:description"]`

* **Een knooppunt en de onderliggende knooppunten verbergen**

   Het knooppunt en de onderliggende knooppunten worden gedefinieerd in, maar niet vereist in de `/libs``/apps` overlay/overschrijving.

   1. Het corresponderende knooppunt maken onder /apps
   1. Een eigenschap maken `sling:hideResource`

      * type: `Boolean`
      * value: `true`

* **Onderliggende items van een knooppunt verbergen (terwijl de eigenschappen van het knooppunt behouden blijven)**

   Het knooppunt, zijn eigenschappen en de onderliggende knooppunten worden gedefinieerd in `/libs`. Het knooppunt en zijn eigenschappen zijn vereist in de `/apps` bedekking/overschrijving, maar sommige of alle onderliggende knooppunten zijn niet vereist in de `/apps` bedekking/overschrijving.

   1. Maak het corresponderende knooppunt onder `/apps`
   1. Maak de eigenschap `sling:hideChildren`:

      * type: `String[]`
      * waarde: een lijst met onderliggende knooppunten (zoals gedefinieerd in `/libs`) die moeten worden verborgen of genegeerd
      Jokerteken&amp;ast; kan worden gebruikt om alle onderliggende knooppunten te verbergen/te negeren.


* **Knooppunten opnieuw ordenen**

   De knoop en zijn siblings worden bepaald in `/libs`. Een nieuwe positie wordt vereist zodat wordt de knoop opnieuw gemaakt in de `/apps` overlay/de opheffing, waar de nieuwe positie in verwijzing naar de aangewezen sibling knoop in wordt bepaald `/libs`.

   * Gebruik de `sling:orderBefore` eigenschap:

      1. Maak het corresponderende knooppunt onder `/apps`
      1. Maak de eigenschap `sling:orderBefore`:

         This specifies the node (as in `/libs`) that the current node should be positioned before:

         * type: `String`
         * value: `<before-SiblingName>`

### Het aanroepen van de Verschuivende Fusie van het Middel van uw code {#invoking-the-sling-resource-merger-from-your-code}

De samenvoeging van het Verspreide Middel omvat twee leveranciers van douanemiddel - voor bekledingen en een andere voor met voeten treedt. Elk van deze kan binnen uw code worden aangehaald door een koppelingspunt te gebruiken:

>[!NOTE]
>
>Wanneer het toegang tot van uw middel wordt het geadviseerd om het aangewezen koppelingspunt te gebruiken.
>
>Dit zorgt ervoor dat de Verschuivende Fusie van het Middel wordt aangehaald en het volledig samengevoegde middel teruggekeerd (verminderend de structuur die van moet worden herhaald `/libs`).

* Bedekking:

   * doel: bronnen samenvoegen op basis van zoekpad
   * koppelpunt: `/mnt/overlay`
   * usage: `mount point + relative path`
   * voorbeeld:

      * `getResource('/mnt/overlay' + '<relative-path-to-resource>');`

* Overschrijven:

   * doel: samenvoegbronnen op basis van hun supertype
   * koppelpunt: `/mnt/overide`
   * usage: `mount point + absolute path`
   * voorbeeld:

      * `getResource('/mnt/override' + '<absolute-path-to-resource>');`

### Voorbeeld van gebruik {#example-of-usage}

Enkele voorbeelden worden behandeld:

* Bedekking:

   * [De consoles aanpassen](/help/sites-developing/customizing-consoles-touch.md)
   * [Paginaontwerp aanpassen](/help/sites-developing/customizing-page-authoring-touch.md)

* Overschrijven:

   * [De pagina-eigenschappen configureren](/help/sites-developing/page-properties-views.md#configuring-your-page-properties)

