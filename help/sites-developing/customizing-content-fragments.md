---
title: Inhoudsfragmenten aanpassen en uitbreiden
description: Een inhoudsfragment breidt een standaardelement uit. Leer hoe u ze kunt aanpassen.
topic-tags: extending-aem
content-type: reference
docset: aem65
exl-id: 08c88e70-4df9-4627-8a66-1fabe3aee50b
solution: Experience Manager, Experience Manager Sites
feature: Content Fragments
role: Developer
source-git-commit: eae057caed533ef16bb541b4ad41b8edd7aaa1c7
workflow-type: tm+mt
source-wordcount: '2728'
ht-degree: 0%

---


# Inhoudsfragmenten aanpassen en uitbreiden{#customizing-and-extending-content-fragments}

Een inhoudsfragment breidt een standaardelement uit. Zie:

* [ Creërend en het Leiden de Fragmenten van de Inhoud ](/help/assets/content-fragments/content-fragments.md) en [ Pagina Authoring met de Fragmenten van de Inhoud ](/help/sites-authoring/content-fragments.md) voor verdere informatie over inhoudsfragmenten.

* [ het Leiden Assets ](/help/assets/manage-assets.md) en [ het Aanpassen en het Uitbreiden van Assets ](/help/assets/extending-assets.md) voor verdere informatie over standaardactiva.

## Architectuur {#architecture}

De basis [ samenstellende delen ](/help/assets/content-fragments/content-fragments.md#constituent-parts-of-a-content-fragment) van een inhoudsfragment zijn:

* A *het Fragment van de Inhoud,*
* die uit één of meerdere *InhoudElement* s bestaan,
* en die één of meerdere *Variatie van de Inhoud* s kunnen hebben.

Afhankelijk van het type fragment worden ook modellen of sjablonen gebruikt:

>[!CAUTION]
>
>[ de fragmentmodellen van de Inhoud ](/help/assets/content-fragments/content-fragments-models.md) worden geadviseerd voor het creëren van alle nieuwe fragmenten.
>
>Modellen van inhoudsfragmenten worden gebruikt voor alle voorbeelden in WKND.

>[!NOTE]
>
>Voorafgaand aan AEM 6.3 werden de Fragments van de Inhoud gecreeerd gebaseerd op malplaatjes in plaats van modellen.
>
>Sjablonen voor inhoudsfragmenten zijn nu afgekeurd. Ze kunnen nog steeds worden gebruikt voor het maken van fragmenten, maar het gebruik van Content Fragment Models wordt aangeraden. Er worden geen nieuwe functies toegevoegd aan fragmentsjablonen en deze worden in een toekomstige versie verwijderd.

* Modellen van inhoudsfragmenten:

   * Wordt gebruikt voor het definiëren van inhoudsfragmenten die gestructureerde inhoud bevatten.
   * Inhoudsfragmentmodellen definiëren de structuur van een inhoudsfragment wanneer dit wordt gemaakt.
   * Een fragment verwijst naar het model. Wijzigingen in het model kunnen/zullen daarom van invloed zijn op afhankelijke fragmenten.
   * Modellen zijn opgebouwd uit gegevenstypen.
   * Functies om nieuwe variaties toe te voegen, enzovoort, moeten het fragment overeenkomstig bijwerken.

  >[!CAUTION]
  >
  >Wijzigingen in een bestaand inhoudsfragmentmodel kunnen van invloed zijn op afhankelijke fragmenten. Dit kan leiden tot weeseigenschappen in die fragmenten.

* Sjablonen voor inhoudsfragmenten:

   * Wordt gebruikt voor het definiëren van eenvoudige inhoudsfragmenten.
   * Sjablonen definiëren de (basis-, alleen-tekst) structuur van een inhoudsfragment wanneer dit wordt gemaakt.
   * De sjabloon wordt naar het fragment gekopieerd wanneer het wordt gemaakt. Verdere wijzigingen in de sjabloon worden dus niet weerspiegeld in bestaande fragmenten.
   * Functies om nieuwe variaties toe te voegen, enzovoort, moeten het fragment overeenkomstig bijwerken.
   * [ het fragmentmalplaatjes van de Inhoud ](/help/sites-developing/content-fragment-templates.md) werken op een verschillende manier aan dat van andere het malplaatjes binnen het AEM ecosysteem (bijvoorbeeld, paginasjablonen, etc.). Daarom moeten zij afzonderlijk worden beschouwd.
   * Wanneer gebaseerd op een malplaatje wordt het MIME type van de inhoud beheerd op de daadwerkelijke inhoud; dit betekent dat elk element en elke variatie een verschillend MIME type kunnen hebben.

### Integratie met Assets {#integration-with-assets}

CFM (Content Fragment Management) maakt deel uit van AEM Assets als:

* Inhoudsfragmenten zijn elementen.
* Ze gebruiken de bestaande Assets-functionaliteit.
* Ze zijn volledig geïntegreerd met Assets (beheerconsoles, enzovoort).

#### Gestructureerde inhoudsfragmenten toewijzen aan Assets {#mapping-structured-content-fragments-to-assets}

![ fragment-aan-activa-gestructureerd ](assets/fragment-to-assets-structured.png)

Inhoudsfragmenten met gestructureerde inhoud (gebaseerd op een inhoudsfragmentmodel) worden toegewezen aan één element:

* Alle inhoud wordt opgeslagen onder het knooppunt `jcr:content/data` van het element:

   * De elementgegevens worden opgeslagen onder het hoofdsubknooppunt:

     `jcr:content/data/master`

   * Variaties worden opgeslagen onder een subknooppunt met de naam van de variatie:
bijvoorbeeld, `jcr:content/data/myvariation`

   * De gegevens van elk element worden in het desbetreffende subknooppunt opgeslagen als een eigenschap met de elementnaam:
De inhoud van element `text` wordt bijvoorbeeld opgeslagen als eigenschap `text` on `jcr:content/data/master` .

* Metagegevens en bijbehorende inhoud worden opgeslagen onder `jcr:content/metadata`
Met uitzondering van de titel en beschrijving, die niet als traditionele metagegevens worden beschouwd en worden opgeslagen op `jcr:content`

#### Eenvoudige inhoudsfragmenten toewijzen aan Assets {#mapping-simple-content-fragments-to-assets}

![ chlimage_1-90 ](assets/chlimage_1-90.png)

Eenvoudige inhoudsfragmenten (gebaseerd op een sjabloon) worden toegewezen aan een samenstelling die bestaat uit een hoofdelement en (optionele) subelementen:

* Alle niet-inhoudinformatie van een fragment (zoals titel, beschrijving, metagegevens, structuur) wordt uitsluitend beheerd op het hoofdelement.
* De inhoud van het eerste element van een fragment wordt toegewezen aan de oorspronkelijke uitvoering van het hoofdelement.

   * De variaties (indien aanwezig) van het eerste element worden toegewezen aan andere uitvoeringen van het hoofdelement.

* Aanvullende elementen (indien aanwezig) worden toegewezen aan subactiva van het hoofdactief.

   * De belangrijkste inhoud van deze aanvullende elementen is gekoppeld aan de oorspronkelijke uitvoering van het respectieve subactief.
   * Andere variaties (indien van toepassing) van eventuele aanvullende elementen die zijn toegewezen aan andere uitvoeringen van het desbetreffende subactief.

#### Locatie van element {#asset-location}

Net als bij standaardelementen wordt een inhoudsfragment opgeslagen onder:

`/content/dam`

#### Elementmachtigingen {#asset-permissions}

Voor verdere details zie [ het Fragment van de Inhoud - Schrap Overwegingen ](/help/assets/content-fragments/content-fragments-delete.md).

#### Functie-integratie {#feature-integration}

* De functie CFM (Content Fragment Management) is gebaseerd op de Assets-kern, maar moet zo onafhankelijk mogelijk zijn.
* CFM biedt zijn eigen implementaties voor items in de kaart-/kolom-/lijstweergaven; deze plug-in de bestaande Assets-implementaties voor het renderen van inhoud.
* Verschillende Assets-componenten zijn uitgebreid om rekening te houden met inhoudsfragmenten.

### Inhoudsfragmenten op pagina&#39;s gebruiken {#using-content-fragments-in-pages}

>[!CAUTION]
>
>De [ Component van de Kern van het Fragment van de Inhoud ](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/components/content-fragment-component.html) wordt nu geadviseerd. Zie [ het Ontwikkelen van de Componenten van de Kern ](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/overview.html) voor meer details.

Vanuit AEM pagina&#39;s kan naar inhoudsfragmenten worden verwezen, net als met elk ander elementtype. AEM verstrekt de **kerncomponent van het Fragment van de Inhoud[*&#128279;*](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/components/content-fragment-component.html) - a [ component die u inhoudsfragmenten op uw pagina&#39;s ](/help/sites-authoring/content-fragments.md#adding-a-content-fragment-to-your-page) laat omvatten. U kunt ook uitbreiden, dit &#x200B;** kerncomponent van het Fragment van 0&rbrace; Inhoud &lbrace;.**

* De component gebruikt de eigenschap `fragmentPath` om naar het daadwerkelijke inhoudsfragment te verwijzen. De eigenschap `fragmentPath` wordt op dezelfde manier afgehandeld als soortgelijke eigenschappen van andere elementtypen, bijvoorbeeld wanneer het inhoudsfragment naar een andere locatie wordt verplaatst.

* Met de component kunt u de variatie selecteren die moet worden weergegeven.
* Bovendien kunt u een reeks alinea&#39;s selecteren om de uitvoer te beperken. Deze alinea kan bijvoorbeeld worden gebruikt voor uitvoer met meerdere kolommen.
* De component staat [ binnen-tussen inhoud ](/help/sites-developing/components-content-fragments.md#in-between-content) toe:

   * Hier kunt u met de component andere elementen (afbeeldingen, enzovoort) tussen de alinea&#39;s van het fragment waarnaar wordt verwezen plaatsen.
   * Voor tussenliggende inhoud moet u:

      * Houd rekening met de mogelijkheid van instabiele verwijzingen. Tussen de inhoud (die bij het ontwerpen van een pagina wordt toegevoegd) bestaat geen vaste relatie met de alinea die naast de inhoud wordt geplaatst. Er wordt een nieuwe alinea (in de fragmenteditor van de inhoud) ingevoegd voordat de positie van de inliggende inhoud de relatieve positie kan verliezen
      * extra parameters (zoals variatie- en alineasofilters) in overweging nemen om verkeerde positieven in zoekresultaten te voorkomen

>[!NOTE]
>
>**Model van het Fragment van de Inhoud:**
>
>Wanneer u een inhoudsfragment gebruikt dat is gebaseerd op een inhoudsfragmentmodel op een pagina, wordt naar het model verwezen. Dit betekent dat als het model niet is gepubliceerd op het moment dat u de pagina publiceert, dit wordt gemarkeerd en het model wordt toegevoegd aan de bronnen die met de pagina moeten worden gepubliceerd.
>
>**Malplaatje van het Fragment van de Inhoud:**
>
>Wanneer u een inhoudsfragment gebruikt dat is gebaseerd op een inhoudsfragmentsjabloon op een pagina, is er geen verwijzing omdat de sjabloon is gekopieerd bij het maken van het fragment.

#### Configuratie met OSGi-console {#configuration-using-osgi-console}

De back-endimplementatie van inhoudsfragmenten is bijvoorbeeld verantwoordelijk voor het maken van instanties van een fragment dat wordt gebruikt op een pagina die kan worden doorzocht, of voor het beheren van gemengde media-inhoud. In deze implementatie moet u weten welke componenten worden gebruikt voor het renderen van fragmenten en hoe de parameters van de rendering worden bepaald.

De parameters voor dit kunnen in de [ Console van het Web ](/help/sites-deploying/configuring-osgi.md#osgi-configuration-with-the-web-console), voor de OSGi bundel **Configuratie van de Component van het Fragment van de Inhoud** worden gevormd.

* **types van Middel**
U kunt een lijst met `sling:resourceTypes` opgeven om componenten te definiëren die worden gebruikt voor het renderen van inhoudsfragmenten en waar de achtergrondverwerking moet worden toegepast.

* **Eigenschappen van de Verwijzing**
Een lijst met eigenschappen kan worden geconfigureerd om op te geven waar de verwijzing naar het fragment wordt opgeslagen voor de desbetreffende component.

>[!NOTE]
>
>Er is geen directe toewijzing tussen eigenschap en componenttype.
>
>AEM gebruikt gewoon de eerste eigenschap die op een alinea staat. U moet de eigenschappen dus zorgvuldig kiezen.

![ screenshot_2019-03-18at100941 ](assets/screenshot_2019-03-18at100941.png)

Er zijn nog enkele richtlijnen die u moet volgen om ervoor te zorgen dat de component compatibel is met de achtergrondverwerking van het inhoudsfragment:

* De naam van de eigenschap waar het te renderen element(en) is gedefinieerd, moet `element` of `elementNames` zijn.

* De naam van de eigenschap waar de te renderen variatie is gedefinieerd, moet `variation` of `variationName` zijn.

* Als de uitvoer van meerdere elementen wordt ondersteund (door `elementNames` te gebruiken om meerdere elementen op te geven), wordt de werkelijke weergavemodus gedefinieerd door de eigenschap `displayMode` :

   * Als de waarde `singleText` is (en er is slechts één element geconfigureerd), wordt het element gerenderd als tekst met tussenliggende inhoud, layoutondersteuning enzovoort. Dit is de standaardinstelling voor fragmenten waarbij slechts één element wordt gerenderd.
   * Anders wordt een veel eenvoudigere aanpak gebruikt (deze kan &#39;formulierweergave&#39; worden genoemd), waarbij geen tussenliggende inhoud wordt ondersteund en de fragmentinhoud &#39;zoals deze is&#39; wordt weergegeven.

* Als het fragment wordt gerenderd voor `displayMode` == `singleText` (impliciet of expliciet), worden de volgende aanvullende eigenschappen afgespeeld:

   * `paragraphScope` definieert of alle alinea&#39;s, of alleen een reeks alinea&#39;s, moeten worden gerenderd (waarden: `all` vs. `range`)

   * als `paragraphScope` == `range` dan definieert de eigenschap `paragraphRange` het bereik van alinea&#39;s dat moet worden gerenderd

### Integratie met andere frameworks {#integration-with-other-frameworks}

Inhoudsfragmenten kunnen worden geïntegreerd met:

* **Vertalingen**

  De Fragmenten van de inhoud zijn volledig geïntegreerd met het [ AEM vertaalwerkschema ](/help/sites-administering/tc-manage.md). Op architectonisch niveau betekent dit:

   * De afzonderlijke vertalingen van een inhoudsfragment zijn eigenlijk afzonderlijke fragmenten, bijvoorbeeld:

      * zij bevinden zich in verschillende taalgebieden :

        `/content/dam/<path>/en/<to>/<fragment>`

        vs

        `/content/dam/<path>/de/<to>/<fragment>`

      * maar ze delen exact hetzelfde relatieve pad onder de hoofdmap van de taal :

        `/content/dam/<path>/en/<to>/<fragment>`

        vs

        `/content/dam/<path>/de/<to>/<fragment>`

   * Naast op regel-gebaseerde wegen, is er geen verdere verbinding tussen de verschillende taalversies van een inhoudsfragment; zij worden behandeld als twee afzonderlijke fragmenten, hoewel UI de middelen verstrekt om tussen de taalvarianten te navigeren.

  >[!NOTE]
  >
  >De AEM vertaalworkflow werkt met `/content` :
  >
  >* Aangezien de modellen van het inhoudsfragment in `/conf` verblijven, zijn deze niet inbegrepen in dergelijke vertalingen. U kunt [ de koorden UI ](/help/sites-developing/i18n-dev.md) internationaliseren.
  >
  >* Sjablonen worden gekopieerd om het fragment te maken, zodat dit impliciet is.

* **schema&#39;s van Meta-gegevens**

   * De fragmenten van de inhoud (re)gebruiken de [ meta-gegevensschema&#39;s ](/help/assets/metadata-schemas.md), die met standaardactiva kunnen worden bepaald.
   * CFM biedt een eigen, specifiek schema:

     `/libs/dam/content/schemaeditors/forms/contentfragment`

     dit kan zo nodig worden verlengd .

   * Het respectievelijke schema-formulier is geïntegreerd met de fragmenteditor.

## De API voor contentfragmentbeheer - Server-kant {#the-content-fragment-management-api-server-side}

U kunt de server-kant API gebruiken om tot uw inhoudsfragmenten toegang te hebben; zie:

[ com.adobe.cq.dam.cfm ](https://www.adobe.io/experience-manager/reference-materials/6-5/javadoc/com/adobe/cq/dam/cfm/package-summary.html)

>[!CAUTION]
>
>Het wordt ten zeerste aanbevolen de server-side API te gebruiken in plaats van rechtstreeks toegang te krijgen tot de inhoudsstructuur.

### Belangrijke interfaces {#key-interfaces}

De volgende drie interfaces kunnen als ingangspunten dienen:

* **Malplaatje van het Fragment** ([ FragmentTemplate ](https://www.adobe.io/experience-manager/reference-materials/6-5/javadoc/com/adobe/cq/dam/cfm/FragmentTemplate.html))

  Gebruik `FragmentTemplate.createFragment()` om een fragment te maken.

  ```
  Resource templateOrModelRsc = resourceResolver.getResource("...");
  FragmentTemplate tpl = templateOrModelRsc.adaptTo(FragmentTemplate.class);
  ContentFragment newFragment = tpl.createFragment(parentRsc, "A fragment name", "A fragment description.");
  ```

  Deze interface vertegenwoordigt:

   * een inhoudsfragmentmodel of een fragmentsjabloon voor inhoud op basis waarvan een inhoudsfragment moet worden gemaakt,
   * en (na het maken) de structuurgegevens van dat fragment

  Deze informatie kan omvatten:

   * Toegang tot basisgegevens (titel, beschrijving)
   * Sjablonen/modellen openen voor de elementen van het fragment:

      * Elementsjablonen weergeven
      * Structuurgegevens voor een bepaald element ophalen
      * Toegang tot de elementsjabloon (zie `ElementTemplate`)

   * Sjablonen openen voor de variaties van het fragment:

      * Wijzigingssjablonen weergeven
      * Structuurgegevens voor een bepaalde wijziging ophalen
      * Toegang tot de variatiesjabloon (zie `VariationTemplate`)

   * Aanvankelijke gekoppelde inhoud ophalen

  Interfaces die belangrijke informatie vertegenwoordigen:

   * `ElementTemplate`

      * Basisgegevens ophalen (naam, titel)
      * Eerste elementinhoud ophalen

   * `VariationTemplate`

      * Basisgegevens ophalen (naam, titel, beschrijving)

* **Fragment van de Inhoud** ([ ContentFragment ](https://www.adobe.io/experience-manager/reference-materials/6-5/javadoc/com/adobe/cq/dam/cfm/ContentFragment.html))

  Met deze interface kunt u op abstracte wijze met een inhoudsfragment werken.

  >[!CAUTION]
  >
  >Het wordt sterk geadviseerd om tot een fragment door deze interface toegang te hebben. Het rechtstreeks wijzigen van de inhoudsstructuur moet worden vermeden.

  De interface voorziet u van de middelen:

   * Standaardgegevens beheren (bijvoorbeeld naam ophalen; titel/beschrijving ophalen/instellen)
   * Toegang tot metagegevens
   * Toegangselementen:

      * Lijstelementen
      * Elementen op naam ophalen
      * Creeer nieuwe elementen (zie [ Gebieden ](#caveats))

      * Gegevens over toegangselementen (zie `ContentElement`)

   * Variaties weergeven die zijn gedefinieerd voor het fragment
   * Nieuwe variaties wereldwijd maken
   * Gekoppelde inhoud beheren:

      * Lijstverzamelingen
      * Verzamelingen toevoegen
      * Verzamelingen verwijderen

   * Open het model of de sjabloon van het fragment

  De interfaces die de belangrijkste elementen van een fragment vertegenwoordigen zijn:

   * **Element van de Inhoud** ([ ContentElement ](https://www.adobe.io/experience-manager/reference-materials/6-5/javadoc/com/adobe/cq/dam/cfm/ContentElement.html))

      * Basisgegevens ophalen (naam, titel, beschrijving)
      * Inhoud ophalen/instellen
      * Toegang tot variaties van een element:

         * Variaties weergeven
         * Variaties ophalen op naam
         * Creeer nieuwe variaties (zie [ Gebieden ](#caveats))
         * Verwijder variaties (zie [ Gebieden ](#caveats))
         * Toegang krijgen tot variatiegegevens (zie `ContentVariation`)

      * Sneltoets voor het oplossen van variaties (door een aanvullende, implementatiespecifieke fallback-logica toe te passen als de opgegeven variatie niet beschikbaar is voor een element)

   * **de Variatie van de Inhoud** ([ ContentVariation ](https://www.adobe.io/experience-manager/reference-materials/6-5/javadoc/com/adobe/cq/dam/cfm/ContentVariation.html))

      * Basisgegevens ophalen (naam, titel, beschrijving)
      * Inhoud ophalen/instellen
      * Eenvoudige synchronisatie, gebaseerd op laatst gewijzigde informatie

  Alle drie de interfaces ( `ContentFragment`, `ContentElement`, `ContentVariation`) breiden de `Versionable` -interface uit, die versiemogelijkheden toevoegt, die vereist zijn voor inhoudsfragmenten:

   * Nieuwe versie van het element maken
   * Versies van het element weergeven
   * Hiermee wordt de inhoud opgehaald van een specifieke versie van het element met versiebeheer

### Aanpassen - Using adjustTo() {#adapting-using-adaptto}

Het volgende kan worden aangepast:

* `ContentFragment` kan worden aangepast aan:

   * `Resource` - de onderliggende Sling-bron. Wanneer u de onderliggende `Resource` rechtstreeks bijwerkt, moet u het `ContentFragment` -object opnieuw opbouwen.

   * `Asset` - De DAM `Asset` -abstractie die het inhoudsfragment vertegenwoordigt. Wanneer u `Asset` rechtstreeks bijwerkt, moet u het `ContentFragment` -object opnieuw opbouwen.

* `ContentElement` kan worden aangepast aan:

   * `ElementTemplate` - voor toegang tot de structuurinformatie van het element.

* `FragmentTemplate` kan worden aangepast aan:

   * `Resource` - het `Resource` bepalen van het model waarnaar wordt verwezen of de oorspronkelijke sjabloon die is gekopieerd;

      * wijzigingen die zijn aangebracht via de `Resource` , worden niet automatisch doorgevoerd in de `FragmentTemplate` .

* `Resource` kan worden aangepast aan:

   * `ContentFragment`
   * `FragmentTemplate`

### Caveats {#caveats}

Er zij op gewezen dat:

* De API is geïmplementeerd om functionaliteit te bieden die door de UI wordt ondersteund.
* Volledige API wordt ontworpen om **niet** veranderingen automatisch te handhaven (tenzij anders vermeld in API JavaDoc). Zo zult u altijd de middeloplosser van het respectieve verzoek (of resolver moeten begaan u eigenlijk gebruikt).
* Taken die extra inspanning zouden kunnen vereisen:

   * Door nieuwe elementen te maken/verwijderen wordt de gegevensstructuur van eenvoudige fragmenten (op basis van een fragmentsjabloon) niet bijgewerkt.
   * Als u nieuwe variaties maakt vanuit `ContentElement` , wordt de gegevensstructuur niet bijgewerkt (maar worden deze globaal gemaakt op basis van `ContentFragment` will).

   * Als u bestaande variaties verwijdert, wordt de gegevensstructuur niet bijgewerkt.

## De API voor contentfragmentbeheer - Client-kant {#the-content-fragment-management-api-client-side}

>[!CAUTION]
>
>Voor AEM 6.5 is de client-side API intern.

### Aanvullende informatie {#additional-information}

Zie het volgende:

* `filter.xml`

  Het `filter.xml` for content fragment management is zo geconfigureerd dat het niet overlapt met het Assets core content package.

## Sessies bewerken {#edit-sessions}

Er wordt een bewerkingssessie gestart wanneer de gebruiker een inhoudsfragment in een van de editorpagina&#39;s opent. De het uitgeven zitting wordt gebeëindigd wanneer de gebruiker de redacteur door of **te selecteren sparen** of **annuleert**.

### Vereisten {#requirements}

Vereisten voor het besturen van een bewerkingssessie zijn:

* Het bewerken van een inhoudsfragment, dat meerdere weergaven kan beslaan (= HTML pagina&#39;s), moet atomisch zijn.
* Het uitgeven zou ook *transactie* moeten zijn; aan het eind van uitgeven zitting moeten de veranderingen of worden toegewijd (bewaard) of worden geannuleerd (geannuleerd).
* Edge-gevallen moeten correct worden afgehandeld. Dit zijn onder andere situaties waarin de gebruiker de pagina verlaat door handmatig een URL in te voeren of door globale navigatie te gebruiken.
* Om gegevensverlies te voorkomen, moet er regelmatig automatisch worden opgeslagen (elke x minuten).
* Als een inhoudsfragment tegelijkertijd door twee gebruikers wordt bewerkt, mogen deze de wijzigingen van elkaar niet overschrijven.

#### Processen {#processes}

Het gaat om de volgende processen:

* Een sessie starten

   * Er wordt een nieuwe versie van het inhoudsfragment gemaakt.
   * Automatisch opslaan is gestart.
   * Cookies worden ingesteld; deze definiëren het momenteel bewerkte fragment en er is een bewerkingssessie geopend.

* Een sessie voltooien

   * Automatisch opslaan wordt gestopt.
   * Bij toewijzen:

      * De laatste gewijzigde informatie wordt bijgewerkt.
      * Cookies worden verwijderd.

   * Bij terugdraaien:

      * De versie van het inhoudsfragment dat is gemaakt toen de bewerkingssessie werd gestart, wordt hersteld.
      * Cookies worden verwijderd.

* Bewerken

   * Alle wijzigingen (automatisch opslaan inbegrepen) worden uitgevoerd op het actieve inhoudsfragment - niet in een gescheiden, beveiligd gebied.
   * Deze wijzigingen worden daarom direct doorgevoerd op AEM pagina&#39;s die naar het desbetreffende inhoudsfragment verwijzen

#### Handelingen {#actions}

De mogelijke acties zijn:

* Pagina&#39;s invoeren

   * Controleer of er al een bewerksessie aanwezig is; door het betreffende cookie te controleren.

      * Als er een bestaat, controleert u of de bewerkingssessie is gestart voor het inhoudsfragment dat momenteel wordt bewerkt

         * Als het huidige fragment, herstelt u de sessie.
         * Als dat niet het geval is, probeert u het bewerken voor het eerder bewerkte inhoudsfragment te annuleren en cookies te verwijderen (er is geen bewerkingssessie daarna aanwezig).

      * Als er geen bewerkingssessie bestaat, wacht u op de eerste wijziging die de gebruiker heeft aangebracht (zie hieronder).

   * Controleer of er al naar het inhoudsfragment wordt verwezen op een pagina en geef zo ja de juiste informatie weer.

* Inhoud wijzigen

   * Wanneer de gebruiker inhoud verandert en er geen is geef zitting aanwezig uit, wordt een nieuwe Edit zitting gecreeerd (zie [ Beginnend een zitting ](#processes)).

* Pagina&#39;s verlaten

   * Als een bewerkingssessie aanwezig is en de wijzigingen niet zijn doorgevoerd, wordt een modaal bevestigingsdialoogvenster weergegeven waarin de gebruiker op de hoogte wordt gebracht van mogelijk verloren inhoud en waarin hij of zij op de pagina kan blijven.

## Voorbeelden {#examples}

### Voorbeeld: een bestaand inhoudsfragment openen {#example-accessing-an-existing-content-fragment}

Hiertoe kunt u de bron die de API vertegenwoordigt aanpassen aan:

`com.adobe.cq.dam.cfm.ContentFragment`

Bijvoorbeeld:

```java
// first, get the resource
Resource fragmentResource = resourceResolver.getResource("/content/dam/fragments/my-fragment");
// then adapt it
if (fragmentResource != null) {
    ContentFragment fragment = fragmentResource.adaptTo(ContentFragment.class);
    // the resource is now accessible through the API
}
```

### Voorbeeld: een inhoudsfragment maken {#example-creating-a-new-content-fragment}

Als u programmatisch een inhoudsfragment wilt maken, moet u het volgende gebruiken:

`com.adobe.cq.dam.cfm.ContentFragmentManager#create`

Bijvoorbeeld:

```java
Resource templateOrModelRsc = resourceResolver.getResource("...");
FragmentTemplate tpl = templateOrModelRsc.adaptTo(FragmentTemplate.class);
ContentFragment newFragment = tpl.createFragment(parentRsc, "A fragment name", "A fragment description.");
```

### Voorbeeld: het interval voor automatisch opslaan opgeven {#example-specifying-the-auto-save-interval}

Het interval voor automatisch opslaan (gemeten in seconden) kan worden gedefinieerd met behulp van configuratiebeheer (ConfMgr):

* Knooppunt: `<*conf-root*>/settings/dam/cfm/jcr:content`
* Eigenschapnaam: `autoSaveInterval`
* Type: `Long`

* Standaard: `600` (10 minuten); dit is gedefinieerd voor `/libs/settings/dam/cfm/jcr:content`

Als u een auto sparen interval van 5 minuten wilt plaatsen moet u het bezit op uw knoop bepalen; bijvoorbeeld:

* Knooppunt: `/conf/global/settings/dam/cfm/jcr:content`
* Eigenschapnaam: `autoSaveInterval`

* Type: `Long`

* Waarde: `300` (5 minuten komt overeen met 300 seconden)

## Sjablonen voor inhoudsfragmenten {#content-fragment-templates}

Zie [ de Malplaatjes van het Fragment van de Inhoud ](/help/sites-developing/content-fragment-templates.md) voor volledige informatie.

## Componenten voor paginaontwerp {#components-for-page-authoring}

Zie voor meer informatie

* [ Componenten van de Kern - de Component van het Fragment van de Inhoud ](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/components/content-fragment-component.html) (geadviseerd)
* [Componenten van inhoudsfragment - Componenten voor paginaontwerp](/help/sites-developing/components-content-fragments.md#components-for-page-authoring)
