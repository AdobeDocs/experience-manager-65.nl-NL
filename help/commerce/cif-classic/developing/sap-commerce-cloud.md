---
title: Ontwikkeling met SAP-Commerce Cloud
description: Het SAP-integratieframework voor Commerce Cloud bevat een integratielaag met een API.
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: platform
exl-id: b3de1a4a-f334-44bd-addc-463433204c99
solution: Experience Manager,Commerce
source-git-commit: 1751bfb32386685e3a159939113b9667b5e17f0e
workflow-type: tm+mt
source-wordcount: '2303'
ht-degree: 0%

---

# Ontwikkeling met SAP-Commerce Cloud {#developing-with-sap-commerce-cloud}

>[!NOTE]
>
>Het eCommerce-kader kan met elke oplossing voor eCommerce worden gebruikt. Bepaalde specifieke en hier behandelde voorbeelden zijn te vinden in de [hybris](https://www.sap.com/products/crm.html) oplossing.

Het integratieframework bevat een integratielaag met een API. Hiermee kunt u:

* plug-in een eCommerce-systeem en haal productgegevens naar Adobe Experience Manager (AEM)

* bouwen AEM componenten voor handelsmogelijkheden onafhankelijk van de specifieke eCommerce-motor

![chlimage_1-11](/help/sites-developing/assets/chlimage_1-11a.png)

>[!NOTE]
>
>[API-documentatie](/help/commerce/cif-classic/developing/ecommerce.md#api-documentation) is ook beschikbaar.

Verscheidene uit-van-de-doos AEM componenten worden verstrekt om de integratielaag te gebruiken. Deze zijn momenteel:

* een productweergaveonderdeel
* een winkelwagentje
* uitchecken

Voor onderzoek, wordt een integratiehaak verstrekt die u het AEM onderzoek, het onderzoek van het eCommerce systeem, een derdenonderzoek, of een combinatie van daarvan laat gebruiken.

## Selectie van eCommerce-engine {#ecommerce-engine-selection}

Het eCommerce-kader kan bij elke eCommerce-oplossing worden gebruikt; de motor die wordt gebruikt, moet identificeerbaar zijn door AEM:

* eCommerce Engines zijn OSGi-diensten die de `CommerceService` interface

   * Motoren kunnen worden onderscheiden door `commerceProvider` service, eigenschap

* AEM `Resource.adaptTo()` for `CommerceService` en `Product`

   * De `adaptTo` de implementatie zoekt naar een `cq:commerceProvider` eigenschap in de hiërarchie van de bron:

      * Indien gevonden, wordt de waarde gebruikt om de raadpleging van de handelsdienst te filtreren.

      * Indien niet gevonden, wordt de hoogste commerciële dienst gebruikt.

   * A `cq:Commerce` vermenging wordt gebruikt zodat de `cq:commerceProvider` kan aan sterk getypte middelen worden toegevoegd.

* De `cq:commerceProvider` eigenschap wordt ook gebruikt om te verwijzen naar de juiste definitie van de handelsfabriek .

   * Bijvoorbeeld een `cq:commerceProvider` eigenschap met de waarde `hybris` correleert met de OSGi-configuratie voor **Day CQ Commerce Factory voor Hybris** (com.adobe.cq.commerce.hybris.impl.HybrisServiceFactory) - waarbij de parameter `commerceProvider` heeft ook de waarde `hybris`.

   * Hier komen nog andere eigenschappen, zoals **Catalogusversie** kan worden geconfigureerd (indien van toepassing en beschikbaar).

Zie de volgende voorbeelden:

| `cq:commerceProvider = geometrixx` | in een standaard AEM installatie is een specifieke implementatie vereist. Het voorbeeld Geometrixx bevat bijvoorbeeld minimale extensies voor de algemene API |
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

### Ontwikkeling van hybris 4 {#developing-for-hybris}

De hybris-uitbreiding van het eCommerce Integration Framework is bijgewerkt om Hybris 5 te ondersteunen, terwijl achterwaartse compatibiliteit met Hybris 4 behouden blijft.

De standaardinstellingen in de code worden ingesteld voor Hybris 5.

Voor de ontwikkeling van Hybris 4 is het volgende vereist:

* Wanneer het aanhalen van gemaakt, voeg het volgende bevel-lijn argument aan het bevel toe

  `-P hybris4`

  Het downloadt de vooraf geconfigureerde distributie van Hybris 4 en sluit het in de bundel in `cq-commerce-hybris-server`.

* In de OSGi configuratiemanager:

   * Schakel Hybris 5-ondersteuning voor de parser Standaardreactie uit.

   * Zorg ervoor dat de dienst van de Handler van de Authentificatie van Hybris Basis een lagere de dienstrangschikking heeft dan de dienst van de Handler van de Handler van Hybris OAuth.

### Sessieafhandeling {#session-handling}

hybris gebruikt een gebruikerssessie om informatie op te slaan , zoals het winkelwagentje van de klant . De sessie-id wordt geretourneerd door hybris in een `JSESSIONID` cookie die op volgende verzoeken naar hybris moet worden verzonden. Als u wilt voorkomen dat de sessie-id in de opslagplaats wordt opgeslagen, wordt deze gecodeerd in een ander cookie dat in de browser van de winkel wordt opgeslagen. De volgende stappen worden uitgevoerd:

* Op het eerste verzoek, wordt geen koekje geplaatst op het verzoek van de verkoopster; zo wordt een verzoek verzonden naar de hybris instantie om een zitting tot stand te brengen.

* De sessiecookies worden uit de reactie geëxtraheerd en gecodeerd in een nieuwe cookie (bijvoorbeeld `hybris-session-rest`) en wordt ingesteld op het antwoord op de winkels. De codering in een nieuwe cookie is vereist, omdat de oorspronkelijke cookie alleen geldig is voor een bepaald pad en anders niet vanuit de browser wordt teruggestuurd in volgende aanvragen. De padgegevens moeten aan de waarde van het cookie worden toegevoegd.

* Op volgende verzoeken worden de cookies gedecodeerd uit de `hybris-session-<*xxx*>` cookies en ingesteld op de HTTP-client die wordt gebruikt om gegevens van hybris aan te vragen.

>[!NOTE]
>
>Er wordt een nieuwe, anonieme sessie gemaakt wanneer de oorspronkelijke sessie niet meer geldig is.

#### CommerceSession {#commercesession}

* Deze sessie &#39;bezit&#39; de **winkelwagentje**

   * toevoegen/verwijderen/enz. uitvoeren

   * de verschillende berekeningen op het karretje uitvoert;

     `commerceSession.getProductPrice(Product product)`

* Heeft de *opslaglocatie* voor de **bestellen** data

  `CommerceSession.getUserContext()`

* Heeft de **betaling** verwerkingsverbinding

* Heeft de **vervulling** verbinding

### Productsynchronisatie en -publicatie {#product-synchronization-and-publishing}

Productgegevens die in hybris worden bewaard, moeten in AEM beschikbaar zijn. Het volgende mechanisme is geïmplementeerd:

* Een eerste lading id&#39;s wordt geleverd door hybris als voer. Deze feed kan worden bijgewerkt.
* hybris verstrekt via een diervoeder bijgewerkte informatie ( dat AEM opiniepeilingen ) .
* Wanneer AEM productgegevens gebruikt, verzendt het verzoeken terug naar hybris voor de huidige gegevens (voorwaardelijk krijgen verzoek gebruikend laatste gewijzigde datum).
* Bij hybriden is het mogelijk de voederinhoud op declaratieve wijze te specificeren.
* Het toewijzen van de voederstructuur aan het AEM inhoudsmodel gebeurt in de voederadapter aan de AEM kant.

![chlimage_1-12](/help/sites-developing/assets/chlimage_1-12a.png)

* De importer (b) wordt gebruikt voor de initiële installatie van de paginaboomstructuur in AEM voor catalogi.
* Veranderingen in de hybris in de catalogus worden via een diervoeder aan AEM gemeld en vervolgens doorgegeven aan AEM b)

   * Product toegevoegd/verwijderd/gewijzigd met betrekking tot catalogusversie.

   * Goedgekeurd product

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

* De catalogusconfiguratie in AEM herkent **Staand** en **Online** catalogusversies.

* Voor het synchroniseren van producten tussen catalogusversies moet de bijbehorende AEM pagina (a, c) worden geactiveerd of gedeactiveerd.

   * Een product toevoegen aan een **Online** catalogusversie moet op de productpagina worden geactiveerd.

   * Voor het verwijderen van een product is deactivering vereist.

* Voor het activeren van een pagina in AEM (c) is een controle (b) vereist. Dit is alleen mogelijk als

   * Het product bevindt zich in een **Online** catalogusversie voor productpagina&#39;s.

   * De producten waarnaar wordt verwezen, zijn beschikbaar in een **Online** catalogusversie voor andere pagina&#39;s (bijvoorbeeld campagnepagina&#39;s).

* Geactiveerde productpagina&#39;s moeten toegang hebben tot de productgegevens **Online** versie d).

* De AEM instantie Publish vereist toegang tot hybris voor de terugwinning van product en gepersonaliseerde gegevens (d).

### Architectuur {#architecture}

#### Architectuur van product en varianten {#architecture-of-product-and-variants}

Eén product kan meerdere variaties hebben, bijvoorbeeld van kleur en/of grootte. Een product moet bepalen welke eigenschappen variatie drijven; de Adobe bepaalt dit *Alternatieve assen*.

Niet alle eigenschappen zijn echter variantassen. Variaties kunnen ook van invloed zijn op andere eigenschappen. De prijs kan bijvoorbeeld afhankelijk zijn van de grootte. Deze eigenschappen kunnen niet door de verkoopster worden geselecteerd en worden daarom niet als variantassen beschouwd.

Elk product en/of elke variant wordt vertegenwoordigd door een middel, en daarom kaarten 1:1 aan een opslaggegevensopslagknoop. Het gevolg is dat een specifiek product en/of specifieke variant op unieke wijze kan worden geïdentificeerd door het pad ervan.

De product/variant-bron bevat niet altijd de werkelijke productgegevens. Het kan een representatie zijn van gegevens die op een ander systeem (zoals hybris) worden opgeslagen. Productbeschrijvingen en prijzen worden bijvoorbeeld niet opgeslagen in AEM, maar in real-time opgehaald via de eCommerce-engine.

Elke productbron kan worden vertegenwoordigd door een `Product API`. De meeste aanroepen in de product-API zijn variatiespecifiek (hoewel variaties gedeelde waarden van een voorouder kunnen overerven), maar er zijn ook aanroepen die de set variaties weergeven ( `getVariantAxes()`, `getVariants()`, enzovoort).

>[!NOTE]
>
>In feite wordt een variantas bepaald door wat dan ook `Product.getVariantAxes()` retourneert:
>* hybris definieert het voor de implementatie van hybris
>
>Hoewel producten (in het algemeen) vele variantassen kunnen hebben, behandelt de uit-van-de-doos productcomponent slechts twee:
>
>1. `size`
>
>1. plus één of meer
>
>Deze extra variant wordt geselecteerd via `variationAxis` eigenschap van de productreferentie (gewoonlijk `color` voor Geometrixx Outdoors).

#### Productverwijzingen en productgegevens {#product-references-and-product-data}

In het algemeen bevinden de productgegevens zich onder `/etc`en productverwijzingen onder `/content`.

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

Tot slot is er geen verplichting om productgegevens te gebruiken. U kunt alle productgegevens onder de verwijzingen in de catalogus plaatsen; maar u kunt niet echt veelvoudige catalogi hebben zonder alle productgegevens te dupliceren.

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

#### com.adobe.cq.commerce.api.VariantFilter  {#com-adobe-cq-commerce-api-variantfilter}

```java
/**
 * Interface for filtering variants and AxisFilter provided as common implementation
 *
 * The <code>VariantFilter</code> is used to filter variants,
 * for example, when using {@link Product#getVariants(VariantFilter filter)}.
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

   * Een productknooppunt kan zijn:

      * Een verwijzing, met de elders opgeslagen productgegevens:

         * Productverwijzingen bevatten een `productData` eigenschap, die verwijst naar de productgegevens (doorgaans onder `/etc/commerce/products`).

         * De productgegevens zijn hiërarchisch; de productkenmerken worden overgeërfd van de voorouders van een productgegevensknooppunt.

         * De verwijzingen van het product kunnen lokale eigenschappen ook bevatten, die die in hun productgegevens worden gespecificeerd met voeten treden.

      * Een product zelf:

         * Zonder `productData` eigenschap.

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

   * De `CommerceSession` voegt toe of verwijdert, enzovoort.
   * De `CommerceSession` voert ook de verschillende berekeningen op het karretje uit. &quot;

* Hoewel niet rechtstreeks verband houdt met het karretje, `CommerceSession` moet ook prijsinformatie voor catalogi verstrekken (aangezien deze eigenaar is van prijzen)

   * Prijzen kunnen verschillende opties hebben:

      * Kwantiseringen.
      * Andere valuta&#39;s.
      * BTW-plichtig en btw-vrij.

   * De modifiers zijn open-end met de volgende interface:

      * `int CommerceSession.getQuantityBreakpoints(Product product)`
      * `String CommerceSession.getProductPrice(Product product)`

**Opslag**

* Opslag

   * In het hybris-geval is de hybris-server eigenaar van het winkelwagentje.
   * In het geval van AEM generieke geneesmiddelen worden de karretjes van [ClientContext](/help/sites-administering/client-context.md).

**Personalisatie**

* Zorg altijd voor personalisatie via de [ClientContext](/help/sites-administering/client-context.md).
* Een ClientContext `/version/` van het karretje wordt in alle gevallen gecreëerd:

   * De producten moeten worden toegevoegd door `CommerceSession.addCartEntry()` methode.

* In het volgende voorbeeld ziet u een voorbeeld van de informatie over winkelwagentjes in de ClientContext:

![chlimage_1-13](/help/sites-developing/assets/chlimage_1-13a.png)

#### Architectuur van uitchecken {#architecture-of-checkout}

**Gegevens van winkelwagentjes en bestellingen**

De `CommerceSession` eigenaar van de drie elementen:

1. Inhoud winkelwagentje
1. Prijsstelling
1. De orderdetails

1. **Inhoud winkelwagentje**

   Het schema voor de inhoud van het winkelwagentje wordt bepaald door de API:

   ```java
   public void addCartEntry(Product product, int quantity);
   public void modifyCartEntry(int entryNumber, int quantity);
   public void deleteCartEntry(int entryNumber);
   ```

1. **Prijsstelling**

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

   Bestelgegevens zijn echter *niet* vast door de API:

   ```java
   public void updateOrderDetails(Map<String, String> orderDetails);
   public Map<String, String> getOrderDetails();
   public void submitOrder();
   ```

**Verzendberekeningen**

* Orderformulieren moeten vaak meerdere verzendopties (en prijzen) bevatten.
* De prijzen kunnen gebaseerd zijn op artikelen en gegevens van de bestelling, zoals gewicht en/of bezorgadres.
* De `CommerceSession` heeft toegang tot alle afhankelijkheden, zodat het op een vergelijkbare manier kan worden behandeld als productprijzen:

   * De `CommerceSession` is eigenaar van verzendprijs.
   * Kan leveringsdetails ophalen/bijwerken met behulp van `updateOrder(Map<String, Object> delta)`

>[!NOTE]
>
>U kunt een verzendkiezer implementeren, bijvoorbeeld:
>
>`yourProject/commerce/components/shippingpicker`:
>
>* Dit kan in wezen een kopie zijn van `foundation/components/form/radio`, maar met terugverwijzing naar de `CommerceSession` voor:
>
>* Controleren of de methode beschikbaar is
>* Prijsinformatie toevoegen
>* Om kopers in staat te stellen de bestelpagina in AEM bij te werken (met inbegrip van de superset van de verzendmethoden en de beschrijvende tekst), terwijl ze toch de controle hebben om de relevante `CommerceSession` informatie.

**Betalingsverwerking**

* De `CommerceSession` is ook eigenaar van de betalingsverwerkingsverbinding.

* Implementatoren moeten specifieke oproepen (aan hun gekozen betalingsverwerkingsdienst) aan de `CommerceSession` uitvoering.

**Afhandeling bestellen**

* De `CommerceSession` is ook eigenaar van de uitvoeringsverbinding.
* Implementatoren moeten specifieke oproepen (aan hun gekozen betalingsverwerkingsservice) toevoegen aan de `CommerceSession` uitvoering.

### Zoekdefinitie {#search-definition}

Na het standaard dienstAPI model, verstrekt het eCommerce-project een reeks op onderzoek betrekking hebbende APIs die door individuele handelsmotoren kunnen worden uitgevoerd.

>[!NOTE]
>
>Momenteel implementeert alleen de hybris-engine de zoek-API uit-van-de-box.
>
>Nochtans, is het onderzoek API generisch en kan door elke CommerceService individueel worden uitgevoerd.

Het eCommerce-project bevat een standaardzoekcomponent in:

`/libs/commerce/components/search`

![chlimage_1-14](/help/sites-developing/assets/chlimage_1-14a.png)

Dit gebruikt onderzoek API om de geselecteerde handelingsmotor (zie [Selectie van eCommerce-engine](#ecommerce-engine-selection)):

#### Zoeken in API {#search-api}

Het kernproject bevat verschillende algemene klassen/hulpklassen:

1. `CommerceQuery`

   Beschrijft een zoekquery (bevat informatie over de querytekst, de huidige pagina, het paginaformaat, de sortering en de geselecteerde facetten). Alle eCommerce-services die de zoek-API implementeren, ontvangen instanties van deze klasse om hun zoekopdracht uit te voeren. A `CommerceQuery` kan worden geïnstantieerd vanuit een request-object ( `HttpServletRequest`).

1. `FacetParamHelper`

   Is een hulpprogrammaklasse die één statische methode verstrekt - `toParams` - die worden gebruikt voor het genereren van `GET` parametertekenreeksen van een lijst met facetten en één in-/uitschakelen waarde. Dit is nuttig aan de UI kant, waar u een hyperlink voor elke waarde van elk facet moet tonen, zodat wanneer de gebruiker de hyperlink klikt de respectieve waarde van een knevel wordt voorzien. Als deze optie is geselecteerd, wordt deze uit de query verwijderd, anders toegevoegd. Hierbij wordt rekening gehouden met alle logica van het omgaan met meerdere/enkele facetten, het overschrijven van waarden enzovoort.

Het ingangspunt voor de zoekAPI is de `CommerceService#search` methode die een `CommerceResult` object. Zie de [API-documentatie](/help/commerce/cif-classic/developing/ecommerce.md#api-documentation) voor meer informatie over dit onderwerp.

### Gebruikersintegratie {#user-integration}

Er wordt gezorgd voor integratie tussen AEM en verschillende systemen voor e-handel. Hiervoor is een strategie nodig voor het synchroniseren van aankopen tussen de verschillende systemen, zodat AEM specifieke code alleen op de hoogte moet zijn van AEM en omgekeerd:

* Verificatie

  AEM wordt geacht de *alleen* front end en daarom presteert *alles* verificatie.

* Rekeningen in hybriden

  AEM maakt een bijbehorende (ondergeschikte) account in hybris voor elke winkel. De gebruikersnaam van dit account is gelijk aan de AEM gebruikersnaam. Een cryptografisch willekeurig wachtwoord wordt automatisch geproduceerd en (gecodeerd) opgeslagen in AEM.

#### Bestaande gebruikers {#pre-existing-users}

Een AEM front-end kan vóór een bestaande hybris-implementatie worden geplaatst. Ook kan een hybris-engine aan een bestaande AEM-installatie worden toegevoegd. Hiertoe moeten de systemen bestaande gebruikers in elk systeem netjes kunnen verwerken:

* AEM > hybriden

   * Wanneer u zich aanmeldt bij hybris, als de AEM gebruiker niet bestaat:

      * een hybrusgebruiker maken met een cryptografisch willekeurig wachtwoord
      * sla de hybris-gebruikersnaam op in de gebruikersmap van de AEM gebruiker

   * Zie: `com.adobe.cq.commerce.hybris.impl.HybrisSessionImpl#login()`

* hybris > AEM

   * Wanneer het programma openen aan AEM, als het systeem de gebruiker erkent:

      * aanmelden bij hybris met de geleverde gebruikersnaam/pwd
      * Als dit lukt, maakt u de gebruiker AEM met hetzelfde wachtwoord (AEM-specifieke salt resulteert in AEM-specifieke hash).

   * Het bovenstaande algoritme wordt geïmplementeerd in een Sling `AuthenticationInfoPostProcessor`

      * Zie: `com.adobe.cq.commerce.hybris.impl.user.LazyUserImporter.java`

### Het importproces aanpassen {#customizing-the-import-process}

Uw aangepaste importhandler bouwen op bestaande functionaliteit:

* moet de `ImportHandler` interface

* kan de `DefaultImportHandler`.

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
  * @param parentPath    Path of parent category or base path of import if there is a root category
  * @return Path of created category
  */
  public String createCategory(ImporterContext ctx, ValueMap values, String parentCategoryPath) throws Exception;
}
```

Uw aangepaste handler kan alleen door de importer worden herkend als deze de optie `service.ranking`eigenschap met een waarde hoger dan 0, bijvoorbeeld.

```java
@Component
@Service
@Property(name = "service.ranking", value = 100)
public class MyImportHandler extends DefaultImportHandler
{
...
}
```
