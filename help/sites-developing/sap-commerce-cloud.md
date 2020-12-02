---
title: Ontwikkelen met SAP Commerce Cloud
seo-title: Ontwikkelen met SAP Commerce Cloud
description: Het SAP Commerce Cloud-integratieframework bevat een integratielaag met een API
seo-description: Het SAP Commerce Cloud-integratieframework bevat een integratielaag met een API
uuid: a780dd17-027a-4a61-af8f-3e2f600524c7
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: platform
discoiquuid: 96dc0c1a-b21d-480a-addf-c3d0348bd3ad
translation-type: tm+mt
source-git-commit: 2dad235c94c73c1c624fa05ff86a7260d4d4a01b
workflow-type: tm+mt
source-wordcount: '2329'
ht-degree: 0%

---


# Ontwikkelen met SAP Commerce Cloud {#developing-with-sap-commerce-cloud}

>[!NOTE]
>
>Het eCommerce-kader kan met elke oplossing voor eCommerce worden gebruikt. Bepaalde details en voorbeelden die hier worden besproken, verwijzen naar de [hybris](https://www.hybris.com/)-oplossing.

Het integratieframework bevat een integratielaag met een API. Zo kunt u:

* plug-in een eCommerce-systeem en haal productgegevens naar AEM

* bouwen AEM componenten voor handelsmogelijkheden onafhankelijk van de specifieke eCommerce-motor

![chlimage_1-11](assets/chlimage_1-11a.png)

>[!NOTE]
>
>[API-](/help/sites-developing/ecommerce.md#api-documentation) documentatie is ook beschikbaar.

Een aantal uit-van-de-doos AEM componenten worden verstrekt om de integratielaag te gebruiken. Deze zijn momenteel:

* een productweergaveonderdeel
* een winkelwagentje
* uitchecken

Voor onderzoek wordt een integratiehaak verstrekt die u toestaat om het AEM onderzoek, het onderzoek van het eCommerce systeem, een derdenonderzoek (zoals Search&amp;Promote) of een combinatie daarvan te gebruiken.

## eCommerce Engine Selection {#ecommerce-engine-selection}

Het eCommerce-kader kan worden gebruikt met elke oplossing voor e-handel, waarbij de gebruikte motor moet worden geïdentificeerd aan de hand van AEM:

* eCommerce Engines zijn OSGi-services die de interface `CommerceService` ondersteunen

   * De motoren kunnen door een `commerceProvider` de dienstbezit worden onderscheiden

* AEM ondersteunt `Resource.adaptTo()` voor `CommerceService` en `Product`

   * De `adaptTo`-implementatie zoekt naar een `cq:commerceProvider`-eigenschap in de hiërarchie van de bron:

      * Indien gevonden, wordt de waarde gebruikt om de raadpleging van de handelsdienst te filtreren.

      * Indien niet gevonden, wordt de hoogste commerciële dienst gebruikt.
   * Er wordt een `cq:Commerce`-mix gebruikt, zodat `cq:commerceProvider` aan sterk getypte bronnen kan worden toegevoegd.


* De eigenschap `cq:commerceProvider` wordt ook gebruikt om naar de juiste definitie van de handelsfabriek te verwijzen.

   * Een `cq:commerceProvider`-eigenschap met de waarde `hybris` heeft bijvoorbeeld een correlatie met de OSGi-configuratie voor **Day CQ Commerce Factory for Hybris** (com.adobe.cq.commerce.hybris.impl.HybrisServiceFactory) - waarbij de parameter `commerceProvider` ook de waarde `hybris` heeft.

   * Hier kunnen nog andere eigenschappen worden geconfigureerd, zoals **Catalogusversie** (indien van toepassing en beschikbaar).

Zie de volgende voorbeelden:

| `cq:commerceProvider = geometrixx` | in een standaard AEM installatie is een specifieke implementatie vereist; bijvoorbeeld het geometrixx-voorbeeld, dat minimale extensies voor de algemene API bevat |
|--- |--- |
| `cq:commerceProvider = hybris` | hybrusimplementatie |

### Voorbeeld {#example}

```shell
/content/store
+ cq:commerceProvider = hybris
  + mens
    + polo-shirt-1
    + polo-shirt-2
    + employee
+ cq:commerceProvider = jcr
  + adobe-logo-shirt
    + cq:commerceType = product
    + price = 12.50
  + adobe-logo-shirt_S
    + cq:commerceType = variant
    + size = S
  + adobe-logo-shirt_XL
    + cq:commerceType = variant
    + size = XL
    + price = 14.50
```

>[!NOTE]
>
>Met CRXDE Lite kunt u zien hoe dit wordt verwerkt in de productcomponent voor de hybris-implementatie:
>
>`/apps/geometrixx-outdoors/components/hybris/product/product.jsp`

### Ontwikkeling voor hybris 4 {#developing-for-hybris}

De hybris-uitbreiding van het eCommerce Integration Framework is bijgewerkt om Hybris 5 te ondersteunen, terwijl achterwaartse compatibiliteit met Hybris 4 behouden blijft.

De standaardinstellingen in de code worden ingesteld voor Hybris 5.

Voor de ontwikkeling van Hybris 4 is het volgende vereist:

* Voeg bij het aanroepen van de methode het volgende opdrachtregelargument toe aan de opdracht

   `-P hybris4`

   De vooraf geconfigureerde distributie van Hybris 4 wordt gedownload en in de bundel `cq-commerce-hybris-server` ingesloten.

* In de OSGi configuratiemanager:

   * Schakel Hybris 5-ondersteuning voor de parser Standaardreactie uit.

   * Zorg ervoor dat de dienst van de Handler van de Authentificatie van Hybris Basis een lagere de dienstrangschikking heeft dan de dienst van de Handler van Hybris OAuth.

### Sessieverwerking {#session-handling}

hybris gebruikt een gebruikerssessie om informatie op te slaan , zoals het winkelwagentje van de klant . De sessie-id wordt geretourneerd van hybris in een `JSESSIONID`-cookie die moet worden verzonden bij volgende aanvragen naar hybris. Om te voorkomen dat de sessie-id in de opslagplaats wordt opgeslagen, wordt deze gecodeerd in een ander cookie dat in de browser van de winkels wordt opgeslagen. De volgende stappen worden uitgevoerd:

* Op het eerste verzoek wordt geen cookie ingesteld op verzoek van de klant; er wordt dus een verzoek naar de instantie hybris verzonden om een sessie te maken.

* De sessiecookies worden uit de reactie geëxtraheerd, gecodeerd in een nieuw cookie (bijvoorbeeld `hybris-session-rest`) en ingesteld op de reactie op de gebruiker. De codering in een nieuwe cookie is vereist, omdat de oorspronkelijke cookie alleen geldig is voor een bepaald pad en anders niet vanuit de browser wordt teruggestuurd in volgende aanvragen. De padgegevens moeten ook worden toegevoegd aan de waarde van het cookie.

* Bij volgende aanvragen worden de cookies gedecodeerd uit de `hybris-session-<*xxx*>` cookies en ingesteld op de HTTP-client die wordt gebruikt om gegevens van hybris aan te vragen.

>[!NOTE]
>
>Er wordt een nieuwe, anonieme sessie gemaakt wanneer de oorspronkelijke sessie niet meer geldig is.

#### CommerceSession {#commercesession}

* Deze sessie &quot;bezit&quot; de **winkelwagentje**

   * toevoegen/verwijderen/enz. uitvoeren

   * de verschillende berekeningen op het karretje uitvoert;

      `commerceSession.getProductPrice(Product product)`

* Geeft de *opslaglocatie* voor de **order** gegevens

   `CommerceSession.getUserContext()`

* Is ook eigenaar van de **payment**-verwerkingsverbinding

* Is ook eigenaar van de **fulfillment**-verbinding

### Productsynchronisatie en -publicatie {#product-synchronization-and-publishing}

Productgegevens die in hybris worden bewaard, moeten in AEM beschikbaar zijn. Het volgende mechanisme is ingevoerd:

* Een eerste lading id&#39;s wordt geleverd door hybris als voer. Deze feed kan worden bijgewerkt.
* hybris zal bijgewerkte informatie verstrekken via een feed ( die AEM opiniepeilingen ) .
* Wanneer AEM productgegevens gebruikt, worden aanvragen voor de huidige gegevens teruggestuurd naar hybris (voorwaardelijk verzoek ophalen met de laatst gewijzigde datum).
* Bij hybris is is het mogelijk de voederinhoud op declaratieve wijze te specificeren.
* Het toewijzen van de voederstructuur aan het AEM inhoudsmodel gebeurt in de voederadapter aan de AEM kant.

![chlimage_1-12](assets/chlimage_1-12a.png)

* De importer (b) wordt gebruikt voor de initiële installatie van de paginaboomstructuur in AEM voor catalogi.
* Veranderingen in de hybris in de catalogus worden via een diervoeder aan AEM gemeld en vervolgens doorgegeven aan AEM b)

   * Product toegevoegd/verwijderd/gewijzigd ten opzichte van catalogusversie.

   * Goedgekeurd product.

* De hybris-extensie biedt een pollingimporter (&quot;hybris&quot;-schema), die kan worden geconfigureerd om wijzigingen met een opgegeven interval in AEM te importeren (bijvoorbeeld elke 24 uur waarin het interval in seconden wordt opgegeven):

   ```JavaScript
       http://localhost:4502/content/geometrixx-outdoors/en_US/jcr:content.json
        {
        * "jcr:mixinTypes": ["cq:PollConfig"],
        * "enabled": true,
        * "source": "hybris:outdoors",
        * "jcr:primaryType": "cq:PageContent",
        * "interval": 86400
        }
   ```

* De catalogusconfiguratie in AEM herkent **Staged** en **Online** catalogusversies.

* Voor het synchroniseren van producten tussen catalogusversies moet de bijbehorende AEM (a, c) worden geactiveerd.

   * Als u een product wilt toevoegen aan een catalogusversie **Online**, moet de productpagina worden geactiveerd.

   * Voor het verwijderen van een product is deactivering vereist.

* Voor het activeren van een pagina in AEM (c) is een controle (b) vereist. Dit is alleen mogelijk als

   * Het product bevindt zich in een catalogusversie **Online** voor productpagina&#39;s.

   * De producten waarnaar wordt verwezen, zijn beschikbaar in de catalogusversie **Online** voor andere pagina&#39;s (bijvoorbeeld campagnepagina&#39;s).

* Geactiveerde productpagina&#39;s moeten toegang hebben tot de **Online** versie (d) van de productgegevens.

* De AEM publicatie-instantie vereist toegang tot hybris voor het ophalen van product- en gepersonaliseerde gegevens (d).

### Architectuur {#architecture}

#### Architectuur van product en varianten {#architecture-of-product-and-variants}

Eén product kan meerdere variaties hebben; kan bijvoorbeeld variëren per kleur en/of grootte. Een product moet bepalen welke eigenschappen de variatie aansturen; wij noemen deze *variantassen*.

Niet alle eigenschappen zijn echter variantassen. Variaties kunnen ook andere eigenschappen beïnvloeden; de prijs kan bijvoorbeeld afhankelijk zijn van de omvang . Deze eigenschappen kunnen niet door de verkoopster worden geselecteerd en worden daarom niet beschouwd als variantassen.

Elk product en/of elke variant wordt vertegenwoordigd door een middel, en daarom kaarten 1:1 aan een gegevensopslagknoop. Het gevolg is dat een specifiek product en/of specifieke variant op unieke wijze kan worden geïdentificeerd door het pad ervan.

De product/variant-bron bevat niet altijd de werkelijke productgegevens. Dit kan een representatie zijn van gegevens die daadwerkelijk op een ander systeem worden opgeslagen (zoals hybris). Productbeschrijvingen, prijzen, enz. worden bijvoorbeeld niet in AEM opgeslagen, maar in real-time opgehaald van de eCommerce-engine.

Elke productbron kan worden vertegenwoordigd door een `Product API`. De meeste aanroepen in de product-API zijn variatiespecifiek (hoewel variaties gedeelde waarden kunnen overerven van een voorouder), maar er zijn ook aanroepen die de set variaties vermelden ( `getVariantAxes()`, `getVariants()`, enz.).

>[!NOTE]
>
>In feite wordt een variant as bepaald door wat `Product.getVariantAxes()` retourneert:
>* hybris definieert het voor de implementatie van hybris
>
>
Hoewel producten (in het algemeen) vele variantassen kunnen hebben, behandelt de uit-van-de-doos productcomponent slechts twee:
>
>1. `size`
   >
   >
1. plus één of meer
>
>
Deze extra variant wordt geselecteerd via de `variationAxis` eigenschap van de productverwijzing (gewoonlijk `color` voor Geometrixx Outdoors).

#### Productverwijzingen en productgegevens {#product-references-and-product-data}

In het algemeen:

* productgegevens bevinden zich onder `/etc`

* en productverwijzingen onder `/content`.

Er moet een 1:1-kaart zijn tussen productvariaties en productgegevensknooppunten.

Productverwijzingen moeten ook een knooppunt hebben voor elke gepresenteerde variatie - maar er is geen verplichting om alle variaties weer te geven. Als een product bijvoorbeeld S, M, L-variaties heeft, kunnen de productgegevens als volgt zijn:

```shell
etc
|──commerce
|  |──products
|     |──shirt
|       |──shirt-s
|       |──shirt-m
|       |──shirt-l
```

Een catalogus van het type &quot;Big and Tall&quot; kan alleen het volgende bevatten:

```shell
content
|──big-and-tall
|  |──shirt
|     |──shirt-l
```

Tot slot is er geen verplichting om productgegevens te gebruiken. U kunt alle productgegevens onder de verwijzingen in de catalogus plaatsen; maar dan kunt u niet echt meerdere catalogi hebben zonder alle productgegevens te dupliceren.

**API**

#### com.adobe.cq.commerce.api.Product interface {#com-adobe-cq-commerce-api-product-interface}

```java
public interface Product extends Adaptable {

    public String getPath();            // path to specific variation
    public String getPagePath();        // path to presentation page for all variations
    public String getSKU();             // unique ID of specific variation

    public String getTitle();           // shortcut to getProperty(TITLE)
    public String getDescription();     // shortcut to getProperty(DESCRIPTION)
    public String getImageUrl();        // shortcut to getProperty(IMAGE_URL)
    public String getThumbnailUrl();    // shortcut to getProperty(THUMBNAIL_URL)

    public <T> T getProperty(String name, Class<T> type);

    public Iterator<String> getVariantAxes();
    public boolean axisIsVariant(String axis);
    public Iterator<Product> getVariants(VariantFilter filter) throws CommerceException;
}
```

#### com.adobe.cq.commerce.api.VariantFilter {#com-adobe-cq-commerce-api-variantfilter}

```java
/**
 * Interface for filtering variants and AxisFilter provided as common implementation
 *
 * The <code>VariantFilter</code> is used to filter variants,
 * e.g. when using {@link Product#getVariants(VariantFilter filter)}.
 */
public interface VariantFilter {
    public boolean includes(Product product);
}

/**
 * A {@link VariantFilter} for filtering variants by the given
 * axis and value. The following example returns a list of
 * variant products that have a value of <i>blue</i> on the
 * <i>color</i> axis.
 *
 * <p>
 * <code>product.getVariants(new AxisFilter("color", "blue"));</code>
 */
public class AxisFilter implements VariantFilter {

    private String axis;
    private String value;

    public AxisFilter(String axis, String value) {
        this.axis = axis;
        this.value = value;
    }

    /**
     * {@inheritDoc}
     */
    public boolean includes(Product product) {
        ValueMap values = product.adaptTo(ValueMap.class);

        if(values != null) {
            String v = values.get(axis, String.class);

            return v != null && v == value;
        }

        return false;
    }
}
```

* **Algemeen opslagmechanisme**

   * Productknooppunten zijn `nt:unstructured`.

   * Een productknooppunt kan:

      * Een verwijzing, met de elders opgeslagen productgegevens:

         * De verwijzingen van het product bevatten een `productData` bezit, die aan de productgegevens (typisch onder `/etc/commerce/products`) richt.

         * De productgegevens zijn hiërarchisch; productkenmerken worden overgenomen van de voorouders van een productgegevensknooppunt.

         * De verwijzingen van het product kunnen lokale eigenschappen ook bevatten, die die in hun productgegevens worden gespecificeerd met voeten treden.
      * Een product zelf:

         * Zonder een eigenschap `productData`.

         * Een productknooppunt dat alle eigenschappen lokaal bevat (en geen eigenschap productData bevat), neemt productkenmerken rechtstreeks van zijn eigen voorouders over.


* **AEM-generieke productstructuur**

   * Elke variant moet een eigen bladnode hebben.

   * De interface van het product vertegenwoordigt zowel producten als varianten, maar het verwante gegevensopslagknooppunt is specifiek waarover het is.

   * Het productknooppunt beschrijft de productkenmerken en de variantassen.

#### Voorbeeld {#example-1}

```shell
+ banyan_shirt
    - cq:commerceType = product
    - cq:productAttributes = [jcr:title, jcr:description, size, price, color]
    - cq:productVariantAxes = [color, size]
    - jcr:title = Banyan Shirt
    - jcr:description = Flowery, all-cotton shirt.
    - price = 14.00
    + banyan_shirt_s
        - cq:commerceType = variant
        - size = S
        + banyan_shirt_s_red
            - cq:commerceType = variant
            - color = red
        + banyan_shirt_s_blue
            - cq:commerceType = variant
            - color = blue
    + banyan_shirt_m
        - cq:commerceType = variant
        - size = M
        + banyan_shirt_m_red
            - cq:commerceType = variant
            - color = red
        + banyan_shirt_m_blue
            - cq:commerceType = variant
            - color = blue
    + banyan_shirt_l
        - cq:commerceType = variant
        - size = L
        + banyan_shirt_l_red
            - cq:commerceType = variant
            - color = red
        + banyan_shirt_l_blue
            - cq:commerceType = variant
            - color = blue
    + banyan_shirt_xl
        - cq:commerceType = variant
        - size = XL
        - price = 18.00
```

#### Architectuur van het winkelwagentje {#architecture-of-the-shopping-cart}

**Onderdelen**

* Het winkelwagentje is eigendom van de `CommerceSession:`

   * Met `CommerceSession` worden add/remove/etc. uitgevoerd.
   * De `CommerceSession` voert ook de diverse berekeningen op het karretje uit. &quot;

* Hoewel de `CommerceSession` niet rechtstreeks met een cart te maken heeft, moet de &lt;a0/> ook informatie over catalogusprijzen verstrekken (aangezien deze eigenaar is van prijzen)

   * Prijzen kunnen verschillende opties hebben:

      * Kwantiseringen.
      * Verschillende valuta&#39;s.
      * BTW-plichtig en btw-vrij.
   * De modifiers zijn volledig open-eind met de volgende interface:

      * `int CommerceSession.getQuantityBreakpoints(Product product)`
      * `String CommerceSession.getProductPrice(Product product)`


**Opslag**

* Opslag

   * In het hybris-geval is de hybris-server eigenaar van het winkelwagentje.
   * In de AEM-generieke doosjes van worden opgeslagen in [ClientContext](/help/sites-administering/client-context.md).

**Personalisatie**

* Personalisatie moet altijd door de [ClientContext](/help/sites-administering/client-context.md) worden geleid.
* In alle gevallen wordt een ClientContext `/version/` van het winkelwagentje gemaakt:

   * De producten zouden door de `CommerceSession.addCartEntry()` methode moeten worden toegevoegd.

* In het volgende voorbeeld ziet u een voorbeeld van de informatie over winkelwagentjes in de ClientContext wagen:

![chlimage_1-13](assets/chlimage_1-13a.png)

#### Architectuur van afhandeling {#architecture-of-checkout}

**Gegevens van winkelwagentjes en bestellingen**

`CommerceSession` bezit de drie elementen:

1. Inhoud winkelwagentje
1. Prijzen
1. De orderdetails

1. **Inhoud winkelwagentje**

   Het schema voor de inhoud van het winkelwagentje wordt bepaald door de API:

   ```java
   public void addCartEntry(Product product, int quantity);
   public void modifyCartEntry(int entryNumber, int quantity);
   public void deleteCartEntry(int entryNumber);
   ```

1. **Prijzen**

   Het prijsschema wordt ook bepaald door de API:

   ```java
   public String getCartPreTaxPrice();
   public String getCartTax();
   public String getCartTotalPrice();
   public String getOrderShipping();
   public String getOrderTotalTax();
   public String getOrderTotalPrice();
   ```

1. **Bestelgegevens**

   De ordergegevens zijn echter *niet* vast door de API:

   ```java
   public void updateOrderDetails(Map<String, String> orderDetails);
   public Map<String, String> getOrderDetails();
   public void submitOrder();
   ```

**Verzendberekeningen**

* Vaak moeten bestelformulieren meerdere verzendopties (en prijzen) bieden.
* De prijzen kunnen gebaseerd zijn op artikelen en gegevens van de bestelling, zoals gewicht en/of bezorgadres.
* De `CommerceSession` heeft toegang tot alle gebiedsdelen, zodat kan het op een gelijkaardige manier zoals producttarifering worden behandeld:

   * De `CommerceSession` is eigenaar van de verzendprijs.
   * Kan leveringsdetails ophalen/bijwerken met `updateOrder(Map<String, Object> delta)`

>[!NOTE]
>
>U kunt een verzendkiezer implementeren. bijvoorbeeld:
>
>`yourProject/commerce/components/shippingpicker`:
>
>* In wezen zou dit een kopie van `foundation/components/form/radio` kunnen zijn, maar met callbacks naar `CommerceSession` voor:
   >
   >
* Controleren of de methode beschikbaar is
>* Prijsinformatie toevoegen
>* Om kopers in staat te stellen de bestelpagina in AEM bij te werken (met inbegrip van de superset van verzendmethoden en de tekst die ze beschrijft), terwijl ze toch de controle hebben om de relevante `CommerceSession`-informatie beschikbaar te maken.


**Betalingsverwerking**

* De `CommerceSession` is ook eigenaar van de betalingsverwerkingsverbinding.

* Implementatoren moeten specifieke aanroepen (aan hun gekozen betalingsverwerkingsservice) toevoegen aan de `CommerceSession`-implementatie.

**Afhandeling bestellen**

* `CommerceSession` bezit ook de uitvoeringsverbinding.
* Implementatoren moeten specifieke aanroepen (aan hun gekozen betalingsverwerkingsservice) toevoegen aan de `CommerceSession`-implementatie.

### Zoekdefinitie {#search-definition}

Na het standaard dienstAPI model, verstrekt het eCommerce-project een reeks op onderzoek betrekking hebbende APIs die door individuele handelsmotoren kunnen worden uitgevoerd.

>[!NOTE]
>
>Momenteel implementeert alleen de hybris-engine de API voor zoeken buiten de box.
>
>Nochtans, is het onderzoek API generisch en kan door elke CommerceService individueel worden uitgevoerd.

Het eCommerce-project bevat een standaardzoekcomponent, die zich bevindt in:

`/libs/commerce/components/search`

![chlimage_1-14](assets/chlimage_1-14a.png)

Dit maakt gebruik van onderzoek API om de geselecteerde handelingsmotor (zie [eCommerce Engine Selection](#ecommerce-engine-selection)) te vragen:

#### Zoeken in API {#search-api}

Het kernproject bevat verschillende algemene klassen/hulpklassen:

1. `CommerceQuery`

   Wordt gebruikt om een zoekquery te beschrijven (bevat informatie over de querytekst, de huidige pagina, het paginaformaat, de sortering en de geselecteerde facetten). Alle eCommerce-services die de zoek-API implementeren, ontvangen instanties van deze klasse om hun zoekopdracht uit te voeren. Een `CommerceQuery` kan van een verzoekvoorwerp ( `HttpServletRequest`) worden geconcretiseerd.

1. `FacetParamHelper`

   Is een nutsklasse die één statische methode - `toParams` - verstrekt die voor het produceren van `GET` parameterkoorden van een lijst van facetten en één knevelwaarde wordt gebruikt. Dit is handig aan de UI-zijde, waar u een hyperlink moet weergeven voor elke waarde van elk facet, zodat wanneer de gebruiker op de hyperlink klikt, de desbetreffende waarde wordt in- en uitgeschakeld (als deze is geselecteerd, wordt deze verwijderd uit de query, anders toegevoegd). Hierbij wordt rekening gehouden met alle logica van het omgaan met meerdere/enkele facetten, overschrijvende waarden, enzovoort.

Het ingangspunt voor onderzoek API is de `CommerceService#search` methode die een `CommerceResult` voorwerp terugkeert. Zie [API Documentatie](/help/sites-developing/ecommerce.md#api-documentation) voor meer informatie over dit onderwerp.

### Gebruikersintegratie {#user-integration}

Er wordt gezorgd voor integratie tussen AEM en verschillende systemen voor e-handel. Hiervoor is een strategie nodig voor het synchroniseren van aankopen tussen de verschillende systemen, zodat AEM specifieke code alleen op de hoogte moet zijn van AEM en omgekeerd:

* Verificatie

   AEM wordt verondersteld de *only* Web front-end te zijn en voert daarom *all* authentificatie uit.

* Rekeningen in hybriden

   AEM maakt een bijbehorende (ondergeschikte) account in hybris voor elke winkel. De gebruikersnaam van dit account is gelijk aan de AEM gebruikersnaam. Een cryptografisch-willekeurig wachtwoord wordt auto-geproduceerd en (gecodeerd) opgeslagen in AEM.

#### Bestaande gebruikers {#pre-existing-users}

Een AEM front-end kan vóór een bestaande hybris implementatie worden geplaatst. Ook kan een hybris-engine aan een bestaande AEM-installatie worden toegevoegd. Hiertoe moeten de systemen bestaande gebruikers in elk systeem netjes kunnen verwerken:

* AEM -> hybris

   * Wanneer u zich aanmeldt bij hybris, als de AEM gebruiker nog niet bestaat:

      * een nieuwe hybrusgebruiker maken met een cryptografisch willekeurig wachtwoord
      * sla de hybris-gebruikersnaam op in de gebruikersmap van de AEM gebruiker
   * Zie: `com.adobe.cq.commerce.hybris.impl.HybrisSessionImpl#login()`


* hybris -> AEM

   * Wanneer het programma openen aan AEM, als het systeem de gebruiker erkent:

      * poging om zich aan te melden bij hybris met geleverde gebruikersnaam/pwd
      * als dit lukt, maakt u de nieuwe gebruiker AEM met hetzelfde wachtwoord (AEM-specifieke salt resulteert in AEM-specifieke hash).
   * Het bovenstaande algoritme wordt geïmplementeerd in een Sling `AuthenticationInfoPostProcessor`

      * Zie: `com.adobe.cq.commerce.hybris.impl.user.LazyUserImporter.java`


### Het importproces aanpassen {#customizing-the-import-process}

Uw aangepaste importhandler bouwen op bestaande functionaliteit:

* moet de `ImportHandler` interface uitvoeren

* kan `DefaultImportHandler` uitbreiden.

```java
/**
 * Services implementing the <code>ImportHandler</code> interface are
 * called by the {@link HybrisImporter} to create actual commerce entities
 * such as products.
 */
public interface ImportHandler {

  /**
  * Not used.
  */
  public void createTaxonomie(ImporterContext ctx);

  /**
  * Creates a catalog with the given name.
  * @param ctx   The importer context
  * @param name  The catalog's name
  * @return Path of created catalog
  */
  public String createCatalog(ImporterContext ctx, String name) throws Exception;

  /**
  * Creates a product from the given values.
  * @param ctx                The importer context
  * @param values             The product's properties
  * @param parentCategoryPath The containing category's path
  * @return Path of created product
  */
  public String createProduct(ImporterContext ctx, ValueMap values, String parentCategoryPath) throws Exception;

  /**
  * Creates a variant product from the given values.
  * @param ctx             The importer context
  * @param values          The product's properties
  * @param baseProductPath The base product's path
  * @return Path of created product
  */
  public String createVariantProduct(ImporterContext ctx, ValueMap values, String baseProductPath) throws Exception;

  /**
  * Creates an asset for a product. This is usually a product
  * image.
  * @param ctx             The importer context
  * @param values          The product's properties
  * @param baseProductPath The product's path
  * @return Path of created asset
  */
  public String createAsset(ImporterContext ctx, ValueMap values, String productPath) throws Exception;

  /**
  * Creates a category from the given values.
  * @param ctx           The importer context
  * @param values        The category's properties
  * @param parentPath    Path of parent category or base path of import in case of root category
  * @return Path of created category
  */
  public String createCategory(ImporterContext ctx, ValueMap values, String parentCategoryPath) throws Exception;
}
```

Uw aangepaste handler wordt alleen herkend door de importer als deze de eigenschap `service.ranking`opgeeft met een waarde hoger dan 0; bijvoorbeeld.

```java
@Component
@Service
@Property(name = "service.ranking", value = 100)
public class MyImportHandler extends DefaultImportHandler
{
...
}
```
