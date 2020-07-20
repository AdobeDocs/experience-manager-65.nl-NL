---
title: Contentfragmenten aanpassen en uitbreiden
seo-title: Contentfragmenten aanpassen en uitbreiden
description: Een inhoudsfragment breidt een standaardelement uit.
seo-description: Een inhoudsfragment breidt een standaardelement uit.
uuid: f72c3a23-9b0d-4fab-a960-bb1350f01175
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: extending-aem
content-type: reference
discoiquuid: d0770bee-4be5-4a6a-8415-70fdfd75015c
docset: aem65
translation-type: tm+mt
source-git-commit: afed13a2f832b91d0df825d1075852cc84443646
workflow-type: tm+mt
source-wordcount: '2749'
ht-degree: 1%

---


# Contentfragmenten aanpassen en uitbreiden{#customizing-and-extending-content-fragments}

Een inhoudsfragment breidt een standaardelement uit; zie:

* [Inhoudsfragmenten](/help/assets/content-fragments/content-fragments.md) en [paginascripts maken en beheren met inhoudsfragmenten](/help/sites-authoring/content-fragments.md) voor meer informatie over inhoudsfragmenten.

* [Elementen](/help/assets/managing-assets-touch-ui.md) beheren en Elementen [aanpassen en uitbreiden](/help/assets/extending-assets.md) voor meer informatie over standaardelementen.

## Architectuur {#architecture}

De basisonderdelen [van een inhoudsfragment](/help/assets/content-fragments/content-fragments.md#constituent-parts-of-a-content-fragment) zijn:

* Een *inhoudsfragment,*
* bestaande uit een of meer *inhoudselementen*;
* en die een of meer *inhoudvariaties* kunnen hebben.

Afhankelijk van het type fragment worden ook modellen of sjablonen gebruikt:

>[!CAUTION]
>
>[Inhoudsfragmentmodellen](/help/assets/content-fragments/content-fragments-models.md) worden nu aanbevolen voor het maken van al uw fragmenten.
>
>De fragmentmodellen van de inhoud worden gebruikt voor alle voorbeelden in Wij.Retail.

* Modellen van contentfragmenten:

   * Wordt gebruikt voor het definiëren van inhoudsfragmenten die gestructureerde inhoud bevatten.
   * Inhoudsfragmentmodellen definiëren de structuur van een inhoudsfragment wanneer dit wordt gemaakt.
   * Een fragment verwijst naar het model; wijzigingen in het model kunnen/zullen dus gevolgen hebben voor afhankelijke fragmenten.
   * Modellen zijn samengesteld uit gegevenstypen.
   * Functies om nieuwe variaties toe te voegen, enz., moeten het fragment dienovereenkomstig bijwerken.

   >[!CAUTION]
   >
   >Wijzigingen in een bestaand inhoudsfragmentmodel kunnen van invloed zijn op afhankelijke fragmenten. dit kan leiden tot weeseigenschappen in die fragmenten .

* Sjablonen voor inhoudsfragmenten:

   * Wordt gebruikt voor het definiëren van eenvoudige inhoudsfragmenten.
   * Sjablonen definiëren de (basis-, alleen-tekst) structuur van een inhoudsfragment wanneer dit wordt gemaakt.
   * De sjabloon wordt naar het fragment gekopieerd wanneer het wordt gemaakt. verdere wijzigingen van de sjabloon worden dus niet weerspiegeld in bestaande fragmenten.
   * Functies om nieuwe variaties toe te voegen, enz., moeten het fragment dienovereenkomstig bijwerken.
   * [Sjablonen](/help/sites-developing/content-fragment-templates.md) voor inhoudsfragmenten werken op een andere manier dan andere sjablonen in het AEM-ecosysteem (bijvoorbeeld paginasjablonen, enz.). Daarom moeten zij afzonderlijk worden beschouwd.
   * Indien gebaseerd op een sjabloon wordt het MIME-type van de inhoud beheerd op de feitelijke inhoud; dit betekent dat elk element en elke variatie een ander MIME-type kunnen hebben.

### Integratie met middelen {#integration-with-assets}

CFM (Content Fragment Management) maakt deel uit van AEM Assets als:

* Inhoudsfragmenten zijn elementen.
* Ze gebruiken de bestaande functionaliteit Elementen.
* Ze zijn volledig geïntegreerd met Elementen (beheerconsoles, enz.).

#### Gestructureerde inhoudsfragmenten toewijzen aan elementen {#mapping-structured-content-fragments-to-assets}

![fragment-aan-activa-gestructureerd](assets/fragment-to-assets-structured.png)

Inhoudsfragmenten met gestructureerde inhoud (d.w.z. gebaseerd op een inhoudsfragmentmodel) worden toegewezen aan één element:

* Alle inhoud wordt opgeslagen onder het `jcr:content/data` knooppunt van het element:

   * De elementgegevens worden opgeslagen onder het master subknooppunt:
      `jcr:content/data/master`

   * Variaties worden opgeslagen onder een subknooppunt met de naam van de variatie:
bijv. `jcr:content/data/myvariation`

   * De gegevens van elk element worden in het desbetreffende subknooppunt opgeslagen als een eigenschap met de elementnaam:
De inhoud van het element `text` wordt bijvoorbeeld opgeslagen als eigenschap `text` op `jcr:content/data/master`

* Metagegevens en bijbehorende inhoud worden hieronder opgeslagen `jcr:content/metadata`Met uitzondering van de titel en beschrijving, die niet als traditionele metagegevens worden beschouwd en die worden opgeslagen op 
`jcr:content`

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

Zie [Inhoudsfragment - Overwegingen](/help/assets/content-fragments/content-fragments-delete.md)verwijderen voor meer informatie.

#### Functieintegratie {#feature-integration}

* De functie CFM (Content Fragment Management) is gebaseerd op de kern Elementen, maar moet zo onafhankelijk mogelijk zijn.
* CFM biedt zijn eigen implementaties voor items in de kaart-, kolom- of lijstweergaven; Deze plug-in de bestaande implementaties voor het renderen van de inhoud van Elementen.
* Verschillende middelencomponenten zijn uitgebreid om rekening te houden met inhoudsfragmenten.

### Inhoudsfragmenten op pagina&#39;s gebruiken {#using-content-fragments-in-pages}

>[!CAUTION]
>
>Het wordt nu aanbevolen om de kerncomponent [van het](https://helpx.adobe.com/experience-manager/core-components/using/content-fragment-component.html) inhoudsfragment te gebruiken. Zie [Core Components](https://helpx.adobe.com/experience-manager/core-components/using/developing.html) ontwikkelen voor meer informatie.

Vanuit AEM-pagina&#39;s kan naar inhoudsfragmenten worden verwezen, net als met elk ander elementtype. AEM biedt de kerncomponent [**van het **inhoudsfragment](https://helpx.adobe.com/experience-manager/core-components/using/content-fragment-component.html)- een[component waarmee u inhoudsfragmenten op uw pagina](/help/sites-authoring/content-fragments.md#adding-a-content-fragment-to-your-page)&#39;s kunt opnemen. U kunt ook de kerncomponent van dit** inhoudsfragment **uitbreiden.

* De component gebruikt de `fragmentPath` eigenschap om naar het daadwerkelijke inhoudsfragment te verwijzen. De `fragmentPath` onroerende goederen worden op dezelfde wijze afgehandeld als soortgelijke eigendommen van andere soorten activa; bijvoorbeeld wanneer het inhoudsfragment naar een andere locatie wordt verplaatst.

* Met de component kunt u de variatie selecteren die moet worden weergegeven.
* Bovendien kan een reeks alinea&#39;s worden geselecteerd om de uitvoer te beperken; Dit kan bijvoorbeeld worden gebruikt voor uitvoer met meerdere kolommen.
* De component staat [tussen inhoud](/help/sites-developing/components-content-fragments.md#in-between-content)toe:

   * Hier kunt u andere elementen (afbeeldingen, enz.) plaatsen tussen de alinea&#39;s van het fragment waarnaar wordt verwezen.
   * Voor tussenliggende inhoud moet u:

      * zich bewust zijn van de mogelijkheid van onstabiele referenties; tussenliggende inhoud (toegevoegd tijdens het ontwerpen van een pagina) heeft geen vaste relatie met de alinea die naast de inhoud wordt geplaatst, waarbij een nieuwe alinea (in de inhoudfragmenteditor) wordt ingevoegd voordat de positie van de tussenliggende inhoud de relatieve positie kan verliezen
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

De back-endimplementatie van inhoudsfragmenten is bijvoorbeeld verantwoordelijk voor het maken van instanties van een fragment dat wordt gebruikt op een pagina die kan worden doorzocht, of voor het beheren van gemengde media-inhoud. Deze implementatie moet weten welke componenten worden gebruikt voor het renderen van fragmenten en hoe de rendering wordt geparametriseerd.

De parameters voor dit kunnen in de Console [van het](/help/sites-deploying/configuring-osgi.md#osgi-configuration-with-the-web-console)Web, voor de OSGi configuratie **van de Component van het Fragment van de** Inhoud van de bundel worden gevormd.

* **Brontypen** Een lijst met 
`sling:resourceTypes` kan worden opgegeven om componenten te definiëren die worden gebruikt voor het renderen van inhoudsfragmenten en waar de achtergrondverwerking moet worden toegepast.

* **Referentie-eigenschappen** Een lijst met eigenschappen kan worden geconfigureerd om op te geven waar de verwijzing naar het fragment wordt opgeslagen voor de desbetreffende component.

>[!NOTE]
>
>Er is geen directe toewijzing tussen eigenschap en componenttype.
>
>AEM gebruikt gewoon de eerste eigenschap die op een alinea kan worden gevonden. U moet de eigenschappen dus zorgvuldig kiezen.

![screenshot_2019-03-18at100941](assets/screenshot_2019-03-18at100941.png)

Er zijn nog enkele richtlijnen die u moet volgen om ervoor te zorgen dat de component compatibel is met de achtergrondverwerking van het inhoudsfragment:

* De naam van de eigenschap waar het element of de elementen worden gerenderd, moet of `element` of `elementNames`zijn.

* De naam van de eigenschap waar de te renderen variatie is gedefinieerd, moet ofwel `variation` ofwel `variationName`zijn.

* Als de uitvoer van meerdere elementen wordt ondersteund (door meerdere elementen op `elementNames` te geven), wordt de werkelijke weergavemodus gedefinieerd door eigenschap `displayMode`:

   * Als de waarde is `singleText` (en er slechts één element is geconfigureerd), wordt het element gerenderd als tekst met tussenliggende inhoud, layoutondersteuning, enz. Dit is de standaardinstelling voor fragmenten waarbij slechts één element wordt gerenderd.
   * Anders wordt een veel eenvoudigere aanpak gebruikt (deze kan &#39;formulierweergave&#39; worden genoemd), waarbij geen tussenliggende inhoud wordt ondersteund en de fragmentinhoud &#39;zoals deze is&#39; wordt weergegeven.

* Als het fragment voor `displayMode` == `singleText` (impliciet of expliciet) wordt gerenderd, worden de volgende aanvullende eigenschappen in spel gezet:

   * `paragraphScope` definieert of alle alinea&#39;s, of alleen een reeks alinea&#39;s, moeten worden gerenderd (waarden: `all` vs `range`)

   * if `paragraphScope` == `range` `paragraphRange` , definieert de eigenschap het bereik van alinea&#39;s die moeten worden gerenderd

### Integratie met andere frameworks {#integration-with-other-frameworks}

Inhoudsfragmenten kunnen worden geïntegreerd met:

* **Vertalingen**

   Inhoudsfragmenten zijn volledig geïntegreerd met de [AEM-vertaalworkflow](/help/sites-administering/tc-manage.md). Op architectonisch niveau betekent dit:

   * De afzonderlijke vertalingen van een inhoudsfragment zijn eigenlijk afzonderlijke fragmenten. bijvoorbeeld:

      * zij bevinden zich in verschillende taalgebieden :

         `/content/dam/<path>/en/<to>/<fragment>`

         vs

         `/content/dam/<path>/de/<to>/<fragment>`

      * maar ze delen exact hetzelfde relatieve pad onder de hoofdmap van de taal :

         `/content/dam/<path>/en/<to>/<fragment>`

         vs

         `/content/dam/<path>/de/<to>/<fragment>`
   * Naast de op regel gebaseerde paden bestaat er geen verdere verbinding tussen de verschillende taalversies van een inhoudsfragment. ze worden behandeld als twee afzonderlijke fragmenten, hoewel de interface de mogelijkheid biedt om tussen de taalvarianten te navigeren.
   >[!NOTE]
   >
   >De AEM-vertaalworkflow werkt met `/content`:
   >
   >    * Aangezien de modellen van het inhoudsfragment in verblijven `/conf`, zijn deze niet inbegrepen in dergelijke vertalingen. U kunt de UI-tekenreeksen [internationaliseren](/help/sites-developing/i18n-dev.md).
      >
      >    
   * Sjablonen worden gekopieerd om het fragment te maken, zodat dit impliciet is.


* **Metagegevensschema&#39;s**

   * Inhoudsfragmenten (opnieuw) gebruiken de [metagegevensschema](/help/assets/metadata-schemas.md)&#39;s die met standaardelementen kunnen worden gedefinieerd.
   * CFM biedt een eigen, specifiek schema:

      `/libs/dam/content/schemaeditors/forms/contentfragment`

      dit kan zo nodig worden verlengd .

   * Het respectievelijke schema-formulier is geïntegreerd met de fragmenteditor.

## De API voor contentfragmentbeheer - Server-kant {#the-content-fragment-management-api-server-side}

U kunt de server-kant API gebruiken om tot uw inhoudsfragmenten toegang te hebben; zie:

[com.adobe.cq.dam.cfm](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/adobe/cq/dam/cfm/package-summary.html)

>[!CAUTION]
>
>Het wordt ten zeerste aanbevolen de server-side API te gebruiken in plaats van rechtstreeks toegang te krijgen tot de inhoudsstructuur.

### Belangrijke interfaces {#key-interfaces}

De volgende drie interfaces kunnen als ingangspunten dienen:

* **Fragmentsjabloon** ([FragmentTemplate](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/adobe/cq/dam/cfm/FragmentTemplate.html))

   Gebruiken `FragmentTemplate.createFragment()` voor het maken van een nieuw fragment.

   ```
   Resource templateOrModelRsc = resourceResolver.getResource("...");
   FragmentTemplate tpl = templateOrModelRsc.adaptTo(FragmentTemplate.class);
   ContentFragment newFragment = tpl.createFragment(parentRsc, "A fragment name", "A fragment description.");
   ```

   Deze interface vertegenwoordigt:

   * een inhoudsfragmentmodel of een inhoudsfragmentsjabloon op basis waarvan een inhoudsfragment moet worden gemaakt,
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






* **Inhoudsfragment** ([ContentFragment](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/adobe/cq/dam/cfm/ContentFragment.html))

   Met deze interface kunt u op abstracte wijze werken met een inhoudsfragment.

   >[!CAUTION]
   >
   >Het wordt sterk geadviseerd om tot een fragment door deze interface toegang te hebben. Het rechtstreeks wijzigen van de inhoudsstructuur moet worden vermeden.

   De interface voorziet u van de middelen:

   * Basisgegevens beheren (bijvoorbeeld naam ophalen; get/set titel/beschrijving)
   * Toegang tot metagegevens
   * Toegangselementen:

      * Lijstelementen
      * Elementen op naam ophalen
      * Nieuwe elementen maken (zie [Voorzorgsmaatregelen](#caveats))

      * Gegevens over toegangselementen (zie `ContentElement`)
   * Variaties weergeven die zijn gedefinieerd voor het fragment
   * Nieuwe variaties wereldwijd maken
   * Gekoppelde inhoud beheren:

      * Lijstverzamelingen
      * Verzamelingen toevoegen
      * Verzamelingen verwijderen
   * Open het model of de sjabloon van het fragment

   De interfaces die de belangrijkste elementen van een fragment vertegenwoordigen zijn:

   * **Content Element** ([ContentElement](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/adobe/cq/dam/cfm/ContentElement.html))

      * Basisgegevens ophalen (naam, titel, beschrijving)
      * Inhoud ophalen/instellen
      * Toegang tot variaties van een element:

         * Variaties weergeven
         * Variaties ophalen op naam
         * Nieuwe variaties maken (zie [Voorkeuren](#caveats))
         * Variaties verwijderen (zie [Voorwerpen](#caveats))
         * Toegang tot variatiegegevens (zie `ContentVariation`)
      * Sneltoets voor het oplossen van variaties (door een aanvullende, implementatiespecifieke fallback-logica toe te passen als de opgegeven variatie niet beschikbaar is voor een element)
   * **Inhoudsvariatie** ([ContentVariation](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/adobe/cq/dam/cfm/ContentVariation.html))

      * Basisgegevens ophalen (naam, titel, beschrijving)
      * Inhoud ophalen/instellen
      * Eenvoudige synchronisatie, gebaseerd op laatst gewijzigde informatie

   Alle drie interfaces ( `ContentFragment`, `ContentElement`, `ContentVariation`) breiden de `Versionable` interface uit, die versiemogelijkheden toevoegt, die voor inhoudsfragmenten worden vereist:

   * Nieuwe versie van het element maken
   * Versies van het element weergeven
   * Hiermee wordt de inhoud opgehaald van een specifieke versie van het element met versiebeheer







### Aanpassen - Using adjustTo() {#adapting-using-adaptto}

Het volgende kan worden aangepast:

* `ContentFragment` kan worden aangepast aan:

   * `Resource` - de onderliggende sloopbron; Let erop dat u het `Resource` object opnieuw moet opbouwen wanneer u de onderliggende waarde `ContentFragment` rechtstreeks bijwerkt.

   * `Asset` - de DAM- `Asset` abstractie die het inhoudsfragment vertegenwoordigt; Let erop dat u het `Asset` object opnieuw moet opbouwen wanneer u het `ContentFragment` rechtstreeks bijwerkt.

* `ContentElement` kan worden aangepast aan:

   * `ElementTemplate` - voor toegang tot de structurele informatie van het element.

* `FragmentTemplate` kan worden aangepast aan:

   * `Resource` - het `Resource` bepalen van het model waarnaar wordt verwezen of de oorspronkelijke sjabloon die is gekopieerd;

      * de wijzigingen die via het `Resource` formulier zijn aangebracht, worden niet automatisch doorgevoerd in het `FragmentTemplate`document.

* `Resource` kan worden aangepast aan:

   * `ContentFragment`
   * `FragmentTemplate`

### Caveats {#caveats}

Er zij op gewezen dat:

* De API is geïmplementeerd om functionaliteit te bieden die door de UI wordt ondersteund.
* De gehele API is zo ontworpen dat wijzigingen **niet** automatisch worden voortgezet (tenzij anders vermeld in de API JavaDoc). Zo zult u altijd de middeloplosser van het respectieve verzoek (of resolver moeten begaan u eigenlijk gebruikt).
* Taken die extra inspanning zouden kunnen vereisen:

   * Door nieuwe elementen te maken/verwijderen wordt de gegevensstructuur van eenvoudige fragmenten (op basis van een fragmentsjabloon) niet bijgewerkt.
   * Door nieuwe variaties te maken van `ContentElement` wordt de gegevensstructuur niet bijgewerkt (maar `ContentFragment` wordt deze globaal gemaakt op basis van wens).

   * Als u bestaande variaties verwijdert, wordt de gegevensstructuur niet bijgewerkt.

## De API voor contentfragmentbeheer - Client-kant {#the-content-fragment-management-api-client-side}

>[!CAUTION]
>
>Voor AEM 6.5 is de client-side API intern.

### Additional Information {#additional-information}

Zie het volgende:

* `filter.xml`

   De methode `filter.xml` voor het beheer van inhoudsfragmenten is zo geconfigureerd dat deze niet overlapt met het inhoudspakket voor de kernelementen.

## Sessies bewerken {#edit-sessions}

Er wordt een bewerkingssessie gestart wanneer de gebruiker een inhoudsfragment opent in een van de editorpagina&#39;s. De bewerkingssessie is voltooid wanneer de gebruiker de editor verlaat door **Opslaan** of **Annuleren** te selecteren.

### Vereisten {#requirements}

Vereisten voor het besturen van een bewerkingssessie zijn:

* Het bewerken van een inhoudsfragment, dat meerdere weergaven kan beslaan (= HTML-pagina&#39;s), moet atomisch zijn.
* De bewerking moet ook *transactioneel* zijn; aan het einde van de bewerkingssessie moeten de wijzigingen worden vastgelegd (opgeslagen) of teruggedraaid (geannuleerd).
* Randgevallen moeten op de juiste wijze worden afgehandeld; Dit zijn bijvoorbeeld situaties waarin de gebruiker de pagina verlaat door handmatig een URL in te voeren of door globale navigatie te gebruiken.
* Om gegevensverlies te voorkomen, moet er regelmatig automatisch worden opgeslagen (elke x minuten).
* Als een inhoudsfragment tegelijkertijd door twee gebruikers wordt bewerkt, mogen deze de wijzigingen van elkaar niet overschrijven.

#### Processen {#processes}

Het gaat om de volgende processen:

* Een sessie starten

   * Er wordt een nieuwe versie van het inhoudsfragment gemaakt.
   * Automatisch opslaan is gestart.
   * Cookies worden ingesteld; Deze definiëren het momenteel bewerkte fragment en geven aan dat er een bewerkingssessie geopend is.

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
   * Deze wijzigingen worden daarom direct weerspiegeld op AEM-pagina&#39;s die verwijzen naar het desbetreffende inhoudsfragment

#### Acties {#actions}

De mogelijke acties zijn:

* Pagina&#39;s invoeren

   * Controleren of er al een bewerksessie aanwezig is; door de betreffende cookie te controleren.

      * Als er een bestaat, controleert u of de bewerkingssessie is gestart voor het inhoudsfragment dat momenteel wordt bewerkt

         * Als het huidige fragment, herstelt u de sessie.
         * Als dat niet het geval is, probeert u het bewerken voor het eerder bewerkte inhoudsfragment te annuleren en cookies te verwijderen (er is geen bewerkingssessie daarna aanwezig).
      * Als er geen bewerkingssessie bestaat, wacht u op de eerste wijziging die de gebruiker heeft aangebracht (zie hieronder).
   * Controleer of er al naar het inhoudsfragment wordt verwezen op een pagina en geef zo ja de juiste informatie weer.



* Inhoud wijzigen

   * Wanneer de gebruiker inhoud wijzigt en er geen bewerksessie aanwezig is, wordt een nieuwe bewerksessie gemaakt (zie Een sessie [starten](#processes)).

* Pagina&#39;s verlaten

   * Als een bewerkingssessie aanwezig is en de wijzigingen niet zijn doorgevoerd, wordt een modaal bevestigingsdialoogvenster weergegeven waarin de gebruiker op de hoogte wordt gebracht van mogelijk verloren inhoud en waarin hij of zij op de pagina kan blijven.

## Voorbeelden {#examples}

### Voorbeeld: Een bestaand inhoudsfragment openen {#example-accessing-an-existing-content-fragment}

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

### Voorbeeld: Een nieuw inhoudsfragment maken {#example-creating-a-new-content-fragment}

Als u programmatisch een nieuw inhoudsfragment wilt maken, moet u het volgende gebruiken:

`com.adobe.cq.dam.cfm.ContentFragmentManager#create`

Bijvoorbeeld:

```java
Resource templateOrModelRsc = resourceResolver.getResource("...");
FragmentTemplate tpl = templateOrModelRsc.adaptTo(FragmentTemplate.class);
ContentFragment newFragment = tpl.createFragment(parentRsc, "A fragment name", "A fragment description.");
```

### Voorbeeld: Het interval voor automatisch opslaan opgeven {#example-specifying-the-auto-save-interval}

Het interval voor automatisch opslaan (gemeten in seconden) kan worden gedefinieerd met behulp van configuratiebeheer (ConfMgr):

* Knooppunt: `<*conf-root*>/settings/dam/cfm/jcr:content`
* Naam eigenschap: `autoSaveInterval`
* Type: `Long`

* Standaard: `600` (10 minuten); dit is gedefinieerd op `/libs/settings/dam/cfm/jcr:content`

Als u een auto sparen interval van 5 minuten wilt plaatsen moet u het bezit op uw knoop bepalen; bijvoorbeeld:

* Knooppunt: `/conf/global/settings/dam/cfm/jcr:content`
* Naam eigenschap: `autoSaveInterval`

* Type: `Long`

* Waarde: `300` (5 minuten komt overeen met 300 seconden)

## Sjablonen voor inhoudsfragmenten {#content-fragment-templates}

Zie Sjablonen voor [inhoudsfragmenten](/help/sites-developing/content-fragment-templates.md) voor volledige informatie.

## Componenten voor paginaontwerp {#components-for-page-authoring}

Zie voor meer informatie

* [Core Components - Content Fragment Component](https://helpx.adobe.com/experience-manager/core-components/using/content-fragment-component.html) (aanbevolen)
* [Componenten van inhoudsfragment - Componenten voor paginaontwerp](/help/sites-developing/components-content-fragments.md#components-for-page-authoring)
