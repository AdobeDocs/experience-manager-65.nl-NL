---
title: Inhoudsfragmenten aanpassen en uitbreiden
description: Een inhoudsfragment breidt een standaardelement uit. Leer hoe u ze kunt aanpassen.
topic-tags: extending-aem
content-type: reference
docset: aem65
exl-id: 08c88e70-4df9-4627-8a66-1fabe3aee50b
solution: Experience Manager, Experience Manager Sites
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '2728'
ht-degree: 0%

---


# Inhoudsfragmenten aanpassen en uitbreiden{#customizing-and-extending-content-fragments}

Een inhoudsfragment breidt een standaardelement uit. Zie:

* [Inhoudsfragmenten maken en beheren](/help/assets/content-fragments/content-fragments.md) en [Pagina&#39;s ontwerpen met inhoudsfragmenten](/help/sites-authoring/content-fragments.md) voor meer informatie over inhoudsfragmenten.

* [Elementen beheren](/help/assets/manage-assets.md) en [Elementen aanpassen en uitbreiden](/help/assets/extending-assets.md) voor meer informatie over standaardactiva.

## Architectuur {#architecture}

De basis [samenstellende delen](/help/assets/content-fragments/content-fragments.md#constituent-parts-of-a-content-fragment) van een inhoudsfragment zijn:

* A *Inhoudsfragment*
* bestaande uit een of meer *Inhoud-element* s,
* en die een of meer *Inhoudsvariatie* s.

Afhankelijk van het type fragment worden ook modellen of sjablonen gebruikt:

>[!CAUTION]
>
>[Inhoudsfragmentmodellen](/help/assets/content-fragments/content-fragments-models.md) wordt aangeraden alle nieuwe fragmenten te maken.
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
   * [Sjablonen voor inhoudsfragmenten](/help/sites-developing/content-fragment-templates.md) werken op een andere manier dan andere sjablonen binnen het AEM ecosysteem (bijvoorbeeld paginasjablonen, enzovoort). Daarom moeten zij afzonderlijk worden beschouwd.
   * Wanneer gebaseerd op een malplaatje wordt het MIME type van de inhoud beheerd op de daadwerkelijke inhoud; dit betekent dat elk element en elke variatie een verschillend MIME type kunnen hebben.

### Integratie met middelen {#integration-with-assets}

CFM (Content Fragment Management) maakt deel uit van AEM Assets als:

* Inhoudsfragmenten zijn elementen.
* Ze gebruiken de bestaande functionaliteit Elementen.
* Ze zijn volledig geïntegreerd met Elementen (beheerconsoles, enzovoort).

#### Gestructureerde inhoudsfragmenten toewijzen aan elementen {#mapping-structured-content-fragments-to-assets}

![fragment-aan-activa-gestructureerd](assets/fragment-to-assets-structured.png)

Inhoudsfragmenten met gestructureerde inhoud (gebaseerd op een inhoudsfragmentmodel) worden toegewezen aan één element:

* Alle inhoud wordt opgeslagen onder de `jcr:content/data` knooppunt van het element:

   * De elementgegevens worden opgeslagen onder het hoofdsubknooppunt:
     `jcr:content/data/master`

   * Variaties worden opgeslagen onder een subknooppunt met de naam van de variatie: bijvoorbeeld `jcr:content/data/myvariation`

   * De gegevens van elk element worden in het desbetreffende subknooppunt opgeslagen als een eigenschap met de elementnaam: bijvoorbeeld de inhoud van het element `text` is opgeslagen als eigenschap `text` op `jcr:content/data/master`

* Metagegevens en bijbehorende inhoud worden hieronder opgeslagen `jcr:content/metadata`
Met uitzondering van de titel en de beschrijving, die niet als traditionele metagegevens worden beschouwd en op `jcr:content`

#### Eenvoudige inhoudsfragmenten toewijzen aan elementen {#mapping-simple-content-fragments-to-assets}

![chlimage_1-90](assets/chlimage_1-90.png)

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

Zie voor meer informatie [Inhoudsfragment - Overwegingen verwijderen](/help/assets/content-fragments/content-fragments-delete.md).

#### Functie-integratie {#feature-integration}

* De functie CFM (Content Fragment Management) is gebaseerd op de kern Elementen, maar moet zo onafhankelijk mogelijk zijn.
* CFM biedt zijn eigen implementaties voor items in de kaart-, kolom- of lijstweergaven; deze plug-in de bestaande implementaties voor het renderen van de inhoud van Elementen.
* Verschillende middelencomponenten zijn uitgebreid om rekening te houden met inhoudsfragmenten.

### Inhoudsfragmenten op pagina&#39;s gebruiken {#using-content-fragments-in-pages}

>[!CAUTION]
>
>De [Component Content Fragment Core](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/components/content-fragment-component.html) wordt nu aanbevolen. Zie [Basiscomponenten ontwikkelen](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/overview.html) voor meer informatie .

Vanuit AEM pagina&#39;s kan naar inhoudsfragmenten worden verwezen, net als met elk ander elementtype. AEM biedt de [**Inhoudsfragment** kerncomponent](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/components/content-fragment-component.html) - een [component waarmee u inhoudsfragmenten op uw pagina&#39;s kunt opnemen](/help/sites-authoring/content-fragments.md#adding-a-content-fragment-to-your-page). U kunt ook het volgende uitbreiden: **Inhoudsfragment** kerncomponent.

* De component gebruikt de `fragmentPath` eigenschap om naar het daadwerkelijke inhoudsfragment te verwijzen. De `fragmentPath` Deze eigenschap wordt op dezelfde manier verwerkt als soortgelijke eigenschappen van andere elementtypen, bijvoorbeeld wanneer het inhoudsfragment naar een andere locatie wordt verplaatst.

* Met de component kunt u de variatie selecteren die moet worden weergegeven.
* Bovendien kunt u een reeks alinea&#39;s selecteren om de uitvoer te beperken. Deze alinea kan bijvoorbeeld worden gebruikt voor uitvoer met meerdere kolommen.
* De component staat [tussenliggende inhoud](/help/sites-developing/components-content-fragments.md#in-between-content):

   * Hier kunt u met de component andere elementen (afbeeldingen, enzovoort) tussen de alinea&#39;s van het fragment waarnaar wordt verwezen plaatsen.
   * Voor tussenliggende inhoud moet u:

      * Houd rekening met de mogelijkheid van instabiele verwijzingen. Tussen de inhoud (die bij het ontwerpen van een pagina wordt toegevoegd) bestaat geen vaste relatie met de alinea die naast de inhoud wordt geplaatst. Er wordt een nieuwe alinea (in de fragmenteditor van de inhoud) ingevoegd voordat de positie van de inliggende inhoud de relatieve positie kan verliezen
      * extra parameters (zoals variatie- en alineasofilters) in overweging nemen om verkeerde positieven in zoekresultaten te voorkomen

>[!NOTE]
>
>**Inhoudsfragmentmodel:**
>
>Wanneer u een inhoudsfragment gebruikt dat is gebaseerd op een inhoudsfragmentmodel op een pagina, wordt naar het model verwezen. Dit betekent dat als het model niet is gepubliceerd op het moment dat u de pagina publiceert, dit wordt gemarkeerd en het model wordt toegevoegd aan de bronnen die met de pagina moeten worden gepubliceerd.
>
>**Sjabloon inhoudsfragment:**
>
>Wanneer u een inhoudsfragment gebruikt dat is gebaseerd op een inhoudsfragmentsjabloon op een pagina, is er geen verwijzing omdat de sjabloon is gekopieerd bij het maken van het fragment.

#### Configuratie met OSGi-console {#configuration-using-osgi-console}

De back-endimplementatie van inhoudsfragmenten is bijvoorbeeld verantwoordelijk voor het maken van instanties van een fragment dat wordt gebruikt op een pagina die kan worden doorzocht, of voor het beheren van gemengde media-inhoud. In deze implementatie moet u weten welke componenten worden gebruikt voor het renderen van fragmenten en hoe de parameters van de rendering worden bepaald.

De parameters voor dit kunnen in worden gevormd [Webconsole](/help/sites-deploying/configuring-osgi.md#osgi-configuration-with-the-web-console), voor de OSGi-bundel **Configuratie van inhoudsfragmentcomponent**.

* **Brontypen**
Een lijst van `sling:resourceTypes` kan worden opgegeven om componenten te definiëren die worden gebruikt voor het renderen van inhoudsfragmenten en waar de achtergrondverwerking moet worden toegepast.

* **Referentie-eigenschappen**
Een lijst met eigenschappen kan worden geconfigureerd om op te geven waar de verwijzing naar het fragment wordt opgeslagen voor de desbetreffende component.

>[!NOTE]
>
>Er is geen directe toewijzing tussen eigenschap en componenttype.
>
>AEM gebruikt gewoon de eerste eigenschap die op een alinea staat. U moet de eigenschappen dus zorgvuldig kiezen.

![screenshot_2019-03-18at100941](assets/screenshot_2019-03-18at100941.png)

Er zijn nog enkele richtlijnen die u moet volgen om ervoor te zorgen dat de component compatibel is met de achtergrondverwerking van het inhoudsfragment:

* De naam van de eigenschap waar het element of de elementen die moeten worden gerenderd, moet worden gedefinieerd `element` of `elementNames`.

* De naam van de eigenschap waarin de uit te voeren wijziging is gedefinieerd, moet ofwel `variation` of `variationName`.

* Als de uitvoer van meerdere elementen wordt ondersteund (door `elementNames` om meerdere elementen op te geven), wordt de werkelijke weergavemodus gedefinieerd door de eigenschap `displayMode`:

   * Als de waarde `singleText` (en er is slechts één gevormd element) dan wordt het element teruggegeven als tekst met inhoud tussen, lay-outsteun, etc. Dit is de standaardinstelling voor fragmenten waarbij slechts één element wordt gerenderd.
   * Anders wordt een veel eenvoudigere aanpak gebruikt (deze kan &#39;formulierweergave&#39; worden genoemd), waarbij geen tussenliggende inhoud wordt ondersteund en de fragmentinhoud &#39;zoals deze is&#39; wordt weergegeven.

* Als het fragment voor `displayMode` == `singleText` (impliciet of expliciet) worden de volgende aanvullende eigenschappen toegepast:

   * `paragraphScope` definieert of alle alinea&#39;s, of alleen een reeks alinea&#39;s, moeten worden gerenderd (waarden: `all` vs `range`)

   * indien `paragraphScope` == `range` dan de eigenschap `paragraphRange` definieert het bereik van alinea&#39;s dat moet worden gerenderd

### Integratie met andere frameworks {#integration-with-other-frameworks}

Inhoudsfragmenten kunnen worden geïntegreerd met:

* **Vertalingen**

  Inhoudsfragmenten zijn volledig geïntegreerd met de [AEM vertaalworkflow](/help/sites-administering/tc-manage.md). Op architectonisch niveau betekent dit:

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
  >De AEM vertaalworkflow werkt met `/content`:
  >
  >* Terwijl de modellen van het inhoudsfragment zich bevinden in `/conf`, worden deze niet in dergelijke vertalingen opgenomen. U kunt [UI-tekenreeksen internationaliseren](/help/sites-developing/i18n-dev.md).
  >
  >* Sjablonen worden gekopieerd om het fragment te maken, zodat dit impliciet is.

* **Metagegevensschema&#39;s**

   * Inhoudsfragmenten (opnieuw) gebruiken de [metagegevensschema&#39;s](/help/assets/metadata-schemas.md), die met standaardelementen kunnen worden gedefinieerd.
   * CFM biedt een eigen, specifiek schema:

     `/libs/dam/content/schemaeditors/forms/contentfragment`

     dit kan zo nodig worden verlengd .

   * Het respectievelijke schema-formulier is geïntegreerd met de fragmenteditor.

## De API voor contentfragmentbeheer - Server-kant {#the-content-fragment-management-api-server-side}

U kunt de server-kant API gebruiken om tot uw inhoudsfragmenten toegang te hebben; zie:

[com.adobe.cq.dam.cfm](https://www.adobe.io/experience-manager/reference-materials/6-5/javadoc/com/adobe/cq/dam/cfm/package-summary.html)

>[!CAUTION]
>
>Het wordt ten zeerste aanbevolen de server-side API te gebruiken in plaats van rechtstreeks toegang te krijgen tot de inhoudsstructuur.

### Belangrijke interfaces {#key-interfaces}

De volgende drie interfaces kunnen als ingangspunten dienen:

* **Fragmentsjabloon** ([FragmentTemplate](https://www.adobe.io/experience-manager/reference-materials/6-5/javadoc/com/adobe/cq/dam/cfm/FragmentTemplate.html))

  Gebruiken `FragmentTemplate.createFragment()` voor het maken van een fragment.

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

* **Inhoudsfragment** ([ContentFragment](https://www.adobe.io/experience-manager/reference-materials/6-5/javadoc/com/adobe/cq/dam/cfm/ContentFragment.html))

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
      * Nieuwe elementen maken (zie [Caveats](#caveats))

      * Gegevens over toegangselementen (zie `ContentElement`)

   * Variaties weergeven die zijn gedefinieerd voor het fragment
   * Nieuwe variaties wereldwijd maken
   * Gekoppelde inhoud beheren:

      * Lijstverzamelingen
      * Verzamelingen toevoegen
      * Verzamelingen verwijderen

   * Open het model of de sjabloon van het fragment

  De interfaces die de belangrijkste elementen van een fragment vertegenwoordigen zijn:

   * **Inhoud-element** ([ContentElement](https://www.adobe.io/experience-manager/reference-materials/6-5/javadoc/com/adobe/cq/dam/cfm/ContentElement.html))

      * Basisgegevens ophalen (naam, titel, beschrijving)
      * Inhoud ophalen/instellen
      * Toegang tot variaties van een element:

         * Variaties weergeven
         * Variaties ophalen op naam
         * Nieuwe variaties maken (zie [Caveats](#caveats))
         * Variaties verwijderen (zie [Caveats](#caveats))
         * Gegevens betreffende variatie van de toegang (zie `ContentVariation`)

      * Sneltoets voor het oplossen van variaties (door een aanvullende, implementatiespecifieke fallback-logica toe te passen als de opgegeven variatie niet beschikbaar is voor een element)

   * **Inhoudsvariatie** ([ContentVariation](https://www.adobe.io/experience-manager/reference-materials/6-5/javadoc/com/adobe/cq/dam/cfm/ContentVariation.html))

      * Basisgegevens ophalen (naam, titel, beschrijving)
      * Inhoud ophalen/instellen
      * Eenvoudige synchronisatie, gebaseerd op laatst gewijzigde informatie

  Alle drie de interfaces ( `ContentFragment`, `ContentElement`, `ContentVariation`) de `Versionable` interface, die versiemogelijkheden toevoegt, vereist voor inhoudsfragmenten:

   * Nieuwe versie van het element maken
   * Versies van het element weergeven
   * Hiermee wordt de inhoud opgehaald van een specifieke versie van het element met versiebeheer

### Aanpassen - Using adjustTo() {#adapting-using-adaptto}

Het volgende kan worden aangepast:

* `ContentFragment` kan worden aangepast aan:

   * `Resource` - de onderliggende Sling resource; merk op dat het bijwerken van de onderliggende `Resource` rechtstreeks, moet u de `ContentFragment` object.

   * `Asset` - de DAM `Asset` abstractie die het inhoudsfragment vertegenwoordigt; merk op dat het bijwerken van `Asset` rechtstreeks, moet u de `ContentFragment` object.

* `ContentElement` kan worden aangepast aan:

   * `ElementTemplate` - voor toegang tot de structurele informatie van het element.

* `FragmentTemplate` kan worden aangepast aan:

   * `Resource` - de `Resource` het bepalen van het model waarnaar wordt verwezen of de oorspronkelijke sjabloon die is gekopieerd;

      * wijzigingen aangebracht via de `Resource` worden niet automatisch weerspiegeld in de `FragmentTemplate`.

* `Resource` kan worden aangepast aan:

   * `ContentFragment`
   * `FragmentTemplate`

### Caveats {#caveats}

Er zij op gewezen dat:

* De API is geïmplementeerd om functionaliteit te bieden die door de UI wordt ondersteund.
* De gehele API is ontworpen voor **niet** Wijzigingen automatisch aanhouden (tenzij anders vermeld in de API JavaDoc). Zo zult u altijd de middeloplosser van het respectieve verzoek (of resolver moeten begaan u eigenlijk gebruikt).
* Taken die extra inspanning zouden kunnen vereisen:

   * Door nieuwe elementen te maken/verwijderen wordt de gegevensstructuur van eenvoudige fragmenten (op basis van een fragmentsjabloon) niet bijgewerkt.
   * Nieuwe variaties maken van `ContentElement` werkt de gegevensstructuur niet bij (maar maakt deze globaal op `ContentFragment` zal).

   * Als u bestaande variaties verwijdert, wordt de gegevensstructuur niet bijgewerkt.

## De API voor contentfragmentbeheer - Client-kant {#the-content-fragment-management-api-client-side}

>[!CAUTION]
>
>Voor AEM 6.5 is de client-side API intern.

### Aanvullende informatie {#additional-information}

Zie het volgende:

* `filter.xml`

  De `filter.xml` voor inhoudsfragmentbeheer is zo geconfigureerd dat dit niet overlapt met het elementeninhoudspakket.

## Sessies bewerken {#edit-sessions}

Er wordt een bewerkingssessie gestart wanneer de gebruiker een inhoudsfragment in een van de editorpagina&#39;s opent. De bewerkingssessie is voltooid wanneer de gebruiker de editor verlaat door een van de volgende opties te selecteren **Opslaan** of **Annuleren**.

### Vereisten {#requirements}

Vereisten voor het besturen van een bewerkingssessie zijn:

* Het bewerken van een inhoudsfragment, dat meerdere weergaven kan beslaan (= HTML pagina&#39;s), moet atomisch zijn.
* De bewerking moet ook *transactie*; aan het einde van de bewerkingssessie moeten de wijzigingen worden vastgelegd (opgeslagen) of teruggedraaid (geannuleerd).
* Randgevallen moeten correct worden afgehandeld. Dit zijn onder andere situaties waarin de gebruiker de pagina verlaat door handmatig een URL in te voeren of door globale navigatie te gebruiken.
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

   * Wanneer de gebruiker inhoud wijzigt en er geen bewerksessie aanwezig is, wordt een nieuwe bewerksessie gemaakt (zie [Een sessie starten](#processes)).

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
* Naam eigenschap: `autoSaveInterval`
* Type: `Long`

* Standaard: `600` (10 minuten); dit wordt gedefinieerd op `/libs/settings/dam/cfm/jcr:content`

Als u een auto sparen interval van 5 minuten wilt plaatsen moet u het bezit op uw knoop bepalen; bijvoorbeeld:

* Knooppunt: `/conf/global/settings/dam/cfm/jcr:content`
* Naam eigenschap: `autoSaveInterval`

* Type: `Long`

* Waarde: `300` (5 minuten komt overeen met 300 seconden)

## Sjablonen voor inhoudsfragmenten {#content-fragment-templates}

Zie [Sjablonen voor inhoudsfragmenten](/help/sites-developing/content-fragment-templates.md) voor volledige informatie.

## Componenten voor paginaontwerp {#components-for-page-authoring}

Zie voor meer informatie

* [Kerncomponenten - component Inhoudsfragment](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/components/content-fragment-component.html) (aanbevolen)
* [Componenten van inhoudsfragment - Componenten voor paginaontwerp](/help/sites-developing/components-content-fragments.md#components-for-page-authoring)
