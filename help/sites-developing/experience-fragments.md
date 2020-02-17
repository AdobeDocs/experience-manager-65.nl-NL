---
title: Ervaar fragmenten
seo-title: Ervaar fragmenten
description: Leer hoe u Experience Fragments aanpast.
seo-description: Leer hoe u Experience Fragments aanpast.
uuid: fc9f7e59-bd7c-437a-8c63-de8559b5768d
contentOwner: aheimoz
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: extending-aem
content-type: reference
discoiquuid: c02e713e-15f3-408b-879a-d5eb014aef02
docset: aem65
translation-type: tm+mt
source-git-commit: 25eff10d4be811774e7a25cebf7e0506acfd5b0b

---


# Ervaar fragmenten{#experience-fragments}

## De basisbeginselen {#the-basics}

Een fragment [van de](/help/sites-authoring/experience-fragments.md) Ervaring is een groep van één of meerdere componenten met inbegrip van inhoud en lay-out die binnen pagina&#39;s van verwijzingen kunnen worden voorzien.

Een Master- en/of varianttoepassing van het fragment van de ervaring:

* `sling:resourceType` : `/libs/cq/experience-fragments/components/xfpage`

Aangezien er geen `/libs/cq/experience-fragments/components/xfpage/xfpage.html` is, wordt het opnieuw

* `sling:resourceSuperType` : `wcm/foundation/components/page`

## De normale HTML-uitvoering {#the-plain-html-rendition}

Met de `.plain.` kiezer in de URL hebt u toegang tot de onbewerkte HTML-uitvoering.

Dit is beschikbaar in de browser, maar het primaire doel is om andere toepassingen (bijvoorbeeld webapps van derden, aangepaste mobiele implementaties) rechtstreeks toegang te geven tot de inhoud van het Experience Fragment door alleen de URL te gebruiken.

De normale HTML-uitvoering voegt het protocol-, host- en contextpad toe aan paden die:

* van het type: `src`, `href`of `action`

* of eindigen met: `-src`, of `-href`

Bijvoorbeeld:

`.../brooklyn-coat/master.plain.html`

>[!NOTE]
>
>Koppelingen verwijzen altijd naar de publicatie-instantie. Ze zijn bedoeld om door derden te worden gebruikt, dus de koppeling wordt altijd aangeroepen vanuit het publicatieexemplaar, niet vanuit de auteur.

![xf-14](assets/xf-14.png)

De selector voor normale uitvoering gebruikt een transformator in plaats van aanvullende scripts. de [Sling Rewriter](https://sling.apache.org/documentation/bundles/output-rewriting-pipelines-org-apache-sling-rewriter.html) wordt gebruikt als transformator. Dit wordt gevormd bij

* `/libs/experience-fragments/config/rewriter/experiencefragments`

## Sociale variaties {#social-variations}

Sociale varianten kunnen op sociale media (tekst en afbeelding) worden geplaatst. In AEM kunnen deze sociale varianten componenten bevatten; bijvoorbeeld tekstcomponenten, afbeeldingscomponenten.

De afbeelding en de tekst voor de sociale post kunnen van elk type afbeeldingsbron of tekstresource op elk diepteniveau (in de bouwsteen of de lay-outcontainer) worden genomen.

Sociale variaties maken bouwstenen ook mogelijk en houden er rekening mee bij het nemen van sociale maatregelen (op het gebied van de publicatieomgeving).

Om de correcte tekst en het beeld aan het sociale media netwerk te posten, moeten sommige overeenkomsten worden geëerbiedigd als u uw eigen aangepaste componenten ontwikkelt.

Hiervoor moeten de volgende eigenschappen worden gebruikt:

* Voor het extraheren van de afbeelding

   * `fileReference`
   * `fileName`

* Voor het uitnemen van de tekst

   * `text`

Componenten die deze conventie niet gebruiken, worden niet in aanmerking genomen.

## Sjablonen voor ervaringsfragmenten {#templates-for-experience-fragments}

>[!CAUTION]
>
>***Alleen*** [bewerkbare sjablonen](/help/sites-developing/page-templates-editable.md) worden ondersteund voor Experience Fragments.

Bij het ontwikkelen van een nieuwe sjabloon voor Experience Fragments kunt u de standaardwerkwijzen voor een [bewerkbare sjabloon](/help/sites-developing/page-templates-editable.md)volgen.

Als u een ervaringsfragmentsjabloon wilt maken die wordt gedetecteerd door de wizard **Experience Fragment** maken, moet u een van de volgende regelsets volgen:

1. Beide:

   1. Het middeltype van het malplaatje (de aanvankelijke knoop) moet erven van:
      `cq/experience-fragments/components/xfpage`

   1. De naam van de sjabloon moet beginnen met:
      `experience-fragments`
Hierdoor kunnen gebruikers ervaringsfragmenten maken in /content/experience-fragments, aangezien de `cq:allowedTemplates` eigenschap van deze map alle sjablonen bevat die namen hebben die beginnen met `experience-fragment`. Klanten kunnen deze eigenschap bijwerken en hun eigen naamgevingsschema of sjabloonlocaties opnemen.

1. [De toegelaten malplaatjes](/help/sites-authoring/experience-fragments.md#configure-allowed-templates-folder) kunnen in de console van de Fragmenten van de Ervaring worden gevormd.
<!--
1. Add the template details manually in `cq:allowedTemplates` on the `/content/experience-fragment` node.
-->

<!-- >[!NOTE]
>
>[Allowed templates](/help/sites-authoring/experience-fragments.md#configuring-allowed-templates) can be configured in the Experience Fragments console.
-->

## Componenten voor ervaringsfragmenten {#components-for-experience-fragments}

[Het ontwikkelen van componenten](/help/sites-developing/components.md) voor gebruik met/in de Fragmenten van de Ervaring volgt standaardpraktijken.

De enige extra configuratie moet ervoor zorgen dat de componenten op het malplaatje worden [toegestaan, wordt dit bereikt met het Beleid](/help/sites-developing/page-templates-editable.md#content-policies)van de Inhoud.

## De Experience Fragment Link Rewriter Provider - HTML {#the-experience-fragment-link-rewriter-provider-html}

In AEM kunt u ervaringsfragmenten maken. Een ervaringsfragment:

* bestaat uit een groep componenten met een lay-out;
* kan onafhankelijk van een AEM-pagina bestaan.

Een van de gebruiksgevallen voor dergelijke groepen is het insluiten van inhoud in aanraakpunten van derden, zoals Adobe Target.

### Standaardkoppeling herschrijven {#default-link-rewriting}

Met de functie [Exporteren naar doel](/help/sites-administering/experience-fragments-target.md) kunt u:

* een fragment van de Ervaring tot stand brengen,
* er componenten aan toevoegen,
* en exporteer het vervolgens als een Adobe Target-aanbieding in HTML-indeling of in JSON-indeling.

Deze functie kan worden [ingeschakeld voor een auteur-instantie van AEM](/help/sites-administering/experience-fragments-target.md#Prerequisites). Hiervoor is een geldige Adobe Target-configuratie en configuratie voor de Link Externalzer vereist.

De Link Externalzer wordt gebruikt om te bepalen welke URL&#39;s correct zijn wanneer de HTML-versie van het Target Offer wordt gemaakt. Deze versie wordt vervolgens naar Adobe Target verzonden. Dit is nodig omdat Adobe Target vereist dat alle koppelingen binnen de HTML-doelaanbieding voor iedereen toegankelijk zijn. dit betekent dat alle bronnen waarnaar de koppelingen verwijzen, en het ervaringsfragment zelf, moeten worden gepubliceerd voordat ze kunnen worden gebruikt.

Wanneer u een HTML-doelaanbieding samenstelt, wordt standaard een aanvraag verzonden naar een aangepaste Sling-kiezer in AEM. Deze kiezer wordt aangeroepen `.nocloudconfigs.html`. Zoals de naam al aangeeft, wordt er een gewone HTML-rendering van een Experience-fragment gemaakt, maar worden er geen cloudconfiguraties in opgenomen (wat overbodige informatie zou zijn).

Nadat u de HTML-pagina hebt gegenereerd, brengt de Sling Rewriter-pijplijn wijzigingen aan in de uitvoer:

1. De `html`, `head`en `body` elementen worden vervangen door `div` elementen. De `meta`, `noscript` en `title` elementen worden verwijderd (het zijn onderliggende elementen van het oorspronkelijke `head` element en worden niet meegenomen wanneer dit wordt vervangen door het `div` element).

   Dit wordt gedaan om ervoor te zorgen dat het HTML- Doelaanbod in de Activiteiten van het Doel kan worden omvat.

1. AEM wijzigt alle interne koppelingen in de HTML, zodat deze verwijzen naar een gepubliceerde bron.

   Om te bepalen welke koppelingen moeten worden gewijzigd, volgt AEM dit patroon voor kenmerken van HTML-elementen:

   1. `src` attributes
   1. `href` attributes
   1. `*-src` kenmerken (zoals data-src, custom-src, enz.)
   1. `*-href` kenmerken (zoals `data-href`, `custom-href`, `img-href`enz.)
   >[!NOTE]
   >
   >In de meeste gevallen zijn de interne koppelingen in de HTML relatieve koppelingen, maar het kan voorkomen dat aangepaste componenten volledige URL&#39;s in de HTML bevatten. Standaard negeert AEM deze volledige URL&#39;s en worden er geen wijzigingen aangebracht.

   De koppelingen in deze kenmerken worden uitgevoerd via de AEM Link Externalzer om de URL opnieuw te maken alsof deze op een gepubliceerde instantie staat en als zodanig openbaar beschikbaar is. `publishLink()`

Als u een out-of-the-box-implementatie gebruikt, moet het hierboven beschreven proces voldoende zijn om het doelaanbod te genereren uit het ervaringsfragment en het vervolgens te exporteren naar Adobe Target. Er zijn echter enkele gebruiksgevallen die in dit proces niet in aanmerking worden genomen; deze omvatten :

* Sling Mapping beschikbaar op de publicatie-instantie
* Omleiding van Dispatcher

Voor deze gebruiksgevallen verstrekt AEM de Interface van de Leverancier van de Verbinding Rewriter.

### Interface Rewriter-provider koppelen {#link-rewriter-provider-interface}

>[!NOTE]
>
>Deze interface werd geïntroduceerd in [AEM 6.5 SP1 (6.5.1.0)](/help/release-notes/sp-release-notes.md).

Voor complexere gevallen, die niet door het [gebrek](#default-link-rewriting)worden behandeld, biedt AEM de Interface van de Leverancier van de Verbinding Rewriter aan. Dit is een `ConsumerType` interface die u in uw bundels, als dienst kunt uitvoeren. Het omzeilt de wijzigingen die AEM uitvoert op interne koppelingen van een HTML-aanbieding zoals deze worden weergegeven op basis van een Experience Fragment. Met deze interface kunt u het herschrijven van interne HTML-koppelingen aanpassen aan uw bedrijfsbehoeften.

Voorbeelden van gebruiksgevallen om deze interface als dienst uit te voeren omvatten:

* Sling Mappings worden ingeschakeld op de publicatie-instanties, maar niet op de auteurinstantie
* Een verzender of vergelijkbare technologie wordt gebruikt om URL&#39;s intern om te leiden
* Er zijn middelen `sling:alias mechanisms` beschikbaar

>[!NOTE]
>
>Deze interface verwerkt alleen de interne HTML-koppelingen van het gegenereerde doelaanbod.

De interface van de Leverancier van de Verbinding Rewriter ( `ExperienceFragmentLinkRewriterProvider`) is als volgt:

```java
public interface ExperienceFragmentLinkRewriterProvider {

    String rewriteLink(String link, String tag, String attribute);

    boolean shouldRewrite(ExperienceFragmentVariation experienceFragment);

    int getPriority();

}
```

### Hoe te om de Interface van de Leverancier van de Verbinding te gebruiken Rewriter {#how-to-use-the-link-rewriter-provider-interface}

Om de interface te gebruiken moet u eerst een bundel tot stand brengen die een nieuwe de dienstcomponent bevat die de interface van de Leverancier van Rewriter van de Verbinding uitvoert.

Deze service wordt gebruikt om de functie Exporteren naar doel van fragment uit ervaring in te sluiten voor toegang tot de verschillende koppelingen.

Bijvoorbeeld, `ComponentService`:

```java
import com.adobe.cq.xf.ExperienceFragmentLinkRewriterProvider;
import com.adobe.cq.xf.ExperienceFragmentVariation;
import org.osgi.service.component.annotations.Service;
import org.osgi.service.component.annotations.Component;

@Component
@Service
public class GeneralLinkRewriter implements ExperienceFragmentLinkRewriterProvider {

    @Override
    public String rewriteLink(String link, String tag, String attribute) {
        return null;
    }

    @Override
    public boolean shouldRewrite(ExperienceFragmentVariation experienceFragment) {
        return false;
    }

    @Override
    public int getPriority() {
        return 0;
    }

}
```

Voor de dienst aan het werk, zijn er nu drie methodes die binnen de dienst moeten worden uitgevoerd:

* ` [shouldRewrite](#shouldrewrite)`
* ` [rewriteLink](#rewritelink)`

   * `rewriteLinkExample2`

* ` [getPriority](#priorities-getpriority)`

#### shouldRewrite {#shouldrewrite}

U moet aan het systeem erop wijzen of het de verbindingen moet herschrijven wanneer een vraag voor de Uitvoer aan Doel op een bepaalde wijziging van het Fragment van de Ervaring wordt gemaakt. U doet dit door de methode uit te voeren:

`shouldRewrite(ExperienceFragmentVariation experienceFragment);`

Bijvoorbeeld:

```java
@Override
public boolean shouldRewrite(ExperienceFragmentVariation experienceFragment) {
    return experienceFragment.getPath().equals("/content/experience-fragment/master");
}
```

Deze methode ontvangt, als parameter, de Variatie van het Fragment van de Ervaring die de Uitvoer naar systeem van het Doel momenteel herschrijft.

In het bovenstaande voorbeeld willen we het volgende herschrijven:

* koppelingen aanwezig in `src`

* `href` alleen kenmerken

* voor een specifiek ervaringsfragment:
   `/content/experience-fragment/master`

Eventuele andere Erviteitsfragmenten die door het systeem Exporteren naar doel worden doorgegeven, worden genegeerd en niet beïnvloed door wijzigingen die in deze service worden geïmplementeerd.

#### rewriteLink {#rewritelink}

Voor de wijziging van het Fragment van de Ervaring die door het herschrijven proces wordt beïnvloed, zal het dan te werk gaan om de de diensthandvat de verbinding te laten herschrijven. Telkens wanneer een koppeling wordt aangetroffen in de interne HTML, wordt de volgende methode aangeroepen:

`rewriteLink(String link, String tag, String attribute)`

De methode ontvangt de parameters als invoer:

* `link`
De `String` representatie van de koppeling die momenteel wordt verwerkt. Dit is meestal een relatieve URL die naar de bron op de auteurinstantie verwijst.

* `tag`
De naam van het HTML-element dat momenteel wordt verwerkt.

* `attribute`
De exacte kenmerknaam.

Als dit element momenteel bijvoorbeeld wordt verwerkt door het systeem Exporteren naar doel, kunt u het definiëren `CSSInclude` als:

```java
<link rel="stylesheet" href="/etc.clientlibs/foundation/clientlibs/main.css" type="text/css">
```

De vraag aan de `rewriteLink()` methode wordt gedaan gebruikend deze parameters:

```java
rewriteLink(link="/etc.clientlibs/foundation/clientlibs/main.css", tag="link", attribute="href" )
```

Wanneer u de dienst creeert kunt u besluiten nemen die op de bepaalde input worden gebaseerd, en dan de verbinding dienovereenkomstig herschrijven.

Wij willen bijvoorbeeld het `/etc.clientlibs` deel van de URL verwijderen en het juiste externe domein toevoegen. Om dingen eenvoudig te houden, zullen wij van mening zijn dat wij toegang tot een Resolver van het Middel voor uw dienst, zoals in `rewriteLinkExample2`: hebben:

>[!NOTE]
>
>Voor meer informatie over hoe te om een middeloplosser door een de dienstgebruiker te krijgen zie de Gebruikers van de [Dienst in AEM](/help/sites-administering/security-service-users.md).

```java
private ResourceResolver resolver;

private Externalizer externalizer;

@Override
public String rewriteLink(String link, String tag, String attribute) {

    // get the externalizer service
    externalizer = resolver.adaptTo(Externalizer.class);
    if(externalizer == null) {
        // if there was an error, then we do not modify the link
        return null;
    }

    // remove leading /etc.clientlibs from resource link before externalizing
    link = link.replaceAll("/etc.clientlibs", "");

    // considering that we configured our publish domain, we directly apply the publishLink() method
    link = externalizer.publishLink(resolver, link);

    return link;
}
```

>[!NOTE]
>
>Als de bovengenoemde methode terugkeert `null`, dan zal de Uitvoer naar het systeem van het Doel de verbinding zoals het is, een relatieve verbinding aan een middel verlaten.

#### Prioriteiten - getPriority {#priorities-getpriority}

Het is niet ongebruikelijk om verscheidene diensten te nodig om voor verschillende soorten Fragments van de Ervaring te behandelen, of zelfs om een Generische Dienst te hebben die het externaliseren en in kaart brengen voor alle Fragments van de Ervaring behandelt. In deze gevallen kunnen conflicten ontstaan over de dienst die moet worden gebruikt, zodat AEM de mogelijkheid biedt om **prioriteiten** voor verschillende diensten te definiëren. De prioriteiten worden bepaald volgens de methode:

* `getPriority()`

Deze methode staat het gebruik van verscheidene diensten toe waar de `shouldRewrite()` methode waar voor het zelfde Fragment van de Ervaring terugkeert. De dienst die het hoogste aantal van zijn `getPriority()`methode terugkeert is de dienst die de Variatie van het Fragment van de Ervaring behandelt.

Als voorbeeld, kunt u een hebben `GenericLinkRewriterProvider` die de basisafbeelding voor alle Fragmenten van de Ervaring behandelt en wanneer de `shouldRewrite()` methode `true` voor alle Variaties van het Fragment van de Ervaring terugkeert. Voor verscheidene specifieke Fragments van de Ervaring, kunt u speciale behandeling willen, zodat in dit geval, kunt u een verstrekken `SpecificLinkRewriterProvider` waarvoor de `shouldRewrite()` methode waar slechts voor sommige Variaties van het Fragment van de Ervaring terugkeert. Om ervoor te zorgen dat `SpecificLinkRewriterProvider` `getPriority()` wordt gekozen om die Variaties van het Fragment van de Ervaring te behandelen, moet het in zijn methode een hoger aantal terugkeren dan `GenericLinkRewriterProvider.`
