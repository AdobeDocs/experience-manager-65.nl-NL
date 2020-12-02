---
title: Ervaringsfragmenten
seo-title: Ervaringsfragmenten
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
workflow-type: tm+mt
source-wordcount: '1667'
ht-degree: 0%

---


# Ervaringsfragmenten{#experience-fragments}

## De basisbeginselen {#the-basics}

Een [Experience Fragment](/help/sites-authoring/experience-fragments.md) is een groep van een of meer componenten, inclusief inhoud en lay-out, waarnaar op pagina&#39;s kan worden verwezen.

Een ervaringsfragment dat Master en/of variant wordt gebruikt:

* `sling:resourceType` : `/libs/cq/experience-fragments/components/xfpage`

Aangezien er geen `/libs/cq/experience-fragments/components/xfpage/xfpage.html` is, keert het terug naar

* `sling:resourceSuperType` :  `wcm/foundation/components/page`

## De normale HTML-uitvoering {#the-plain-html-rendition}

Met de kiezer `.plain.` in de URL hebt u toegang tot de normale HTML-uitvoering.

Dit is beschikbaar in de browser, maar het primaire doel is om andere toepassingen (bijvoorbeeld webapps van derden, aangepaste mobiele implementaties) rechtstreeks toegang te geven tot de inhoud van het Experience Fragment door alleen de URL te gebruiken.

De normale HTML-uitvoering voegt het protocol-, host- en contextpad toe aan paden die:

* van het type: `src`, `href` of `action`

* of eindigen met: `-src`, of `-href`

Bijvoorbeeld:

`.../brooklyn-coat/master.plain.html`

>[!NOTE]
>
>Koppelingen verwijzen altijd naar de publicatie-instantie. Ze zijn bedoeld om door derden te worden gebruikt, dus de koppeling wordt altijd aangeroepen vanuit het publicatieexemplaar, niet vanuit de auteur.

![xf-12](assets/xf-14.png)

De selector voor normale uitvoering gebruikt een transformator in plaats van aanvullende scripts. de [Sling Rewriter](https://sling.apache.org/documentation/bundles/output-rewriting-pipelines-org-apache-sling-rewriter.html) wordt gebruikt als transformator. Dit wordt gevormd bij

* `/libs/experience-fragments/config/rewriter/experiencefragments`

## Sociale variaties {#social-variations}

Sociale varianten kunnen op sociale media (tekst en afbeelding) worden geplaatst. AEM deze sociale varianten componenten kunnen bevatten; bijvoorbeeld tekstcomponenten, afbeeldingscomponenten.

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
>***Alleen*** [bewerkbare ](/help/sites-developing/page-templates-editable.md) sjablonen worden ondersteund voor Experience Fragments.

Wanneer het ontwikkelen van een nieuw malplaatje voor de Fragmenten van de Ervaring kunt u de standaardpraktijken voor een [editable malplaatje](/help/sites-developing/page-templates-editable.md) volgen.

Om een malplaatje van het ervaringsfragment tot stand te brengen dat door **Create de tovenaar van het Fragment van de Ervaring** wordt ontdekt, moet u één van deze regelreeksen volgen:

1. Beide:

   1. Het middeltype van het malplaatje (de aanvankelijke knoop) moet erven van:
      `cq/experience-fragments/components/xfpage`

   1. De naam van de sjabloon moet beginnen met:
      `experience-fragments`
Hierdoor kunnen gebruikers ervaringsfragmenten maken in /content/experience-fragments als de 
`cq:allowedTemplates` Deze eigenschap bevat alle sjablonen met namen die beginnen met  `experience-fragment`. Klanten kunnen deze eigenschap bijwerken en hun eigen naamgevingsschema of sjabloonlocaties opnemen.

1. [Toegestane ](/help/sites-authoring/experience-fragments.md#configure-allowed-templates-folder) sjablonen kunnen worden geconfigureerd in de console van Experience Fragments.

<!--
1. Add the template details manually in `cq:allowedTemplates` on the `/content/experience-fragment` node.
-->

<!-- >[!NOTE]
>
>[Allowed templates](/help/sites-authoring/experience-fragments.md#configuring-allowed-templates) can be configured in the Experience Fragments console.
-->

## Componenten voor ervaringsfragmenten {#components-for-experience-fragments}

[Het ontwikkelen van ](/help/sites-developing/components.md) componenten voor gebruik met/in de Fragmenten van de Ervaring volgt standaardpraktijken.

De enige extra configuratie moet ervoor zorgen dat de componenten [toegestaan op het malplaatje zijn, wordt dit bereikt met het Beleid van de Inhoud](/help/sites-developing/page-templates-editable.md#content-policies).

## De Experience Fragment Link Rewriter Provider - HTML {#the-experience-fragment-link-rewriter-provider-html}

In AEM hebt u de mogelijkheid om ervaringsfragmenten te maken. Een ervaringsfragment:

* bestaat uit een groep componenten samen met een lay-out;
* kan onafhankelijk van een AEM pagina bestaan.

Een van de gebruiksgevallen voor dergelijke groepen is het insluiten van inhoud in aanraakpunten van derden, zoals Adobe Target.

### Standaardkoppeling bij herschrijven van {#default-link-rewriting}

Met de functie [Exporteren naar doel](/help/sites-administering/experience-fragments-target.md) kunt u:

* een fragment van de Ervaring tot stand brengen,
* er componenten aan toevoegen,
* en exporteer het vervolgens als een Adobe Target-aanbieding in HTML-indeling of in JSON-indeling.

Deze functie kan [worden toegelaten op een auteursinstantie van AEM](/help/sites-administering/experience-fragments-target.md#Prerequisites). Het vereist een geldige Configuratie van Adobe Target, en configuraties voor de Verbinding Externalzer.

De Link Externalzer wordt gebruikt om te bepalen welke URL&#39;s correct zijn wanneer de HTML-versie van het Target Offer wordt gemaakt. Deze versie wordt vervolgens naar Adobe Target verzonden. Dit is nodig omdat Adobe Target vereist dat alle koppelingen binnen de HTML-doelaanbieding openbaar toegankelijk zijn; dit betekent dat alle bronnen waarnaar de koppelingen verwijzen, en het ervaringsfragment zelf, moeten worden gepubliceerd voordat ze kunnen worden gebruikt.

Wanneer u een HTML-doelaanbieding samenstelt, wordt standaard een aanvraag verzonden naar een aangepaste Sling-kiezer in AEM. Deze kiezer wordt `.nocloudconfigs.html` genoemd. Zoals de naam al aangeeft, wordt er een gewone HTML-rendering van een Experience-fragment gemaakt, maar worden er geen cloudconfiguraties in opgenomen (wat overbodige informatie zou zijn).

Nadat u de HTML-pagina hebt gegenereerd, brengt de Sling Rewriter-pijplijn wijzigingen aan in de uitvoer:

1. De `html`-, `head`- en `body`-elementen worden vervangen door `div`-elementen. De `meta`-, `noscript`- en `title`-elementen worden verwijderd (het zijn onderliggende elementen van het oorspronkelijke `head`-element en worden niet meegenomen wanneer dit wordt vervangen door het `div`-element).

   Dit wordt gedaan om ervoor te zorgen dat het HTML- Doelaanbod in de Activiteiten van het Doel kan worden omvat.

1. AEM wijzigt alle interne koppelingen in de HTML, zodat deze verwijzen naar een gepubliceerde bron.

   Als u wilt bepalen welke koppelingen moeten worden gewijzigd, AEM u dit patroon voor kenmerken van HTML-elementen volgt:

   1. `src` attributes
   1. `href` attributes
   1. `*-src` kenmerken (zoals data-src, custom-src, enz.)
   1. `*-href` kenmerken (zoals  `data-href`,  `custom-href`,  `img-href`enz.)

   >[!NOTE]
   >
   >In de meeste gevallen zijn de interne koppelingen in de HTML relatieve koppelingen, maar het kan voorkomen dat aangepaste componenten volledige URL&#39;s in de HTML bevatten. Standaard worden deze volledige URL&#39;s genegeerd en worden geen wijzigingen aangebracht.

   De verbindingen in deze attributen worden in werking gesteld door AEM Verbinding Externalzer `publishLink()` om URL opnieuw te creëren alsof het op een gepubliceerde instantie was, en als dusdanig, openbaar beschikbaar.

Als u een implementatie buiten de doos gebruikt, moet het hierboven beschreven proces voldoende zijn om het doelaanbod te genereren op basis van het ervaringsfragment en het vervolgens te exporteren naar Adobe Target. Er zijn echter enkele gebruiksgevallen die in dit proces niet in aanmerking worden genomen; deze omvatten :

* Sling Mapping beschikbaar op de publicatie-instantie
* Omleiding van Dispatcher

Voor deze gebruiksgevallen AEM verstrekt de Interface van de Leverancier van de Verbinding Rewriter.

### Interface van Rewriter-provider koppelen {#link-rewriter-provider-interface}

>[!NOTE]
>
>Deze interface werd geïntroduceerd in [AEM 6.5 SP1 (6.5.1.0)](/help/release-notes/sp-release-notes.md).

Voor complexere gevallen, die niet door [gebrek](#default-link-rewriting) worden behandeld, AEM biedt de Interface van de Leverancier van de Verbinding Rewriter aan. Dit is een `ConsumerType` interface die u in uw bundels, als dienst kunt uitvoeren. De wijzigingen die AEM uitvoeren op interne koppelingen van een HTML-aanbieding worden overgeslagen zoals deze worden weergegeven op basis van een Experience Fragment. Met deze interface kunt u het herschrijven van interne HTML-koppelingen aanpassen aan uw bedrijfsbehoeften.

Voorbeelden van gebruiksgevallen om deze interface als dienst uit te voeren omvatten:

* Sling Mappings worden ingeschakeld op de publicatie-instanties, maar niet op de auteurinstantie
* Een verzender of vergelijkbare technologie wordt gebruikt om URL&#39;s intern om te leiden
* Er zijn `sling:alias mechanisms` voor bronnen

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
The 
`String` een weergave van de koppeling die momenteel wordt verwerkt. Dit is meestal een relatieve URL die naar de bron op de auteurinstantie verwijst.

* `tag`
De naam van het HTML-element dat momenteel wordt verwerkt.

* `attribute`
De exacte kenmerknaam.

Als het systeem Exporteren naar doel bijvoorbeeld dit element momenteel verwerkt, kunt u `CSSInclude` als volgt definiëren:

```java
<link rel="stylesheet" href="/etc.clientlibs/foundation/clientlibs/main.css" type="text/css">
```

De vraag aan de `rewriteLink()` methode wordt gedaan gebruikend deze parameters:

```java
rewriteLink(link="/etc.clientlibs/foundation/clientlibs/main.css", tag="link", attribute="href" )
```

Wanneer u de dienst creeert kunt u besluiten nemen die op de bepaalde input worden gebaseerd, en dan de verbinding dienovereenkomstig herschrijven.

Voor ons voorbeeld, zouden wij het `/etc.clientlibs` deel van URL willen verwijderen en het aangewezen externe domein toevoegen. Om dingen eenvoudig te houden, zullen wij overwegen dat wij toegang tot een Resolver van het Middel voor uw dienst, zoals in `rewriteLinkExample2` hebben:

>[!NOTE]
>
>Voor meer informatie over hoe te om een middeloplosser door een de dienstgebruiker te krijgen zie [Gebruikers van de Dienst in AEM](/help/sites-administering/security-service-users.md).

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
>Als de bovengenoemde methode `null` terugkeert, dan zal de Uitvoer aan het systeem van het Doel de verbinding zoals het is, een relatieve verbinding aan een middel verlaten.

#### Prioriteiten - getPriority {#priorities-getpriority}

Het is niet ongebruikelijk om verscheidene diensten te nodig om voor verschillende soorten Fragments van de Ervaring te behandelen, of zelfs om een Generische Dienst te hebben die het externaliseren en in kaart brengen voor alle Fragments van de Ervaring behandelt. In deze gevallen kunnen conflicten ontstaan over de service die moet worden gebruikt, zodat AEM de mogelijkheid biedt **Prioriteiten** voor verschillende services te definiëren. De prioriteiten worden bepaald volgens de methode:

* `getPriority()`

Deze methode staat het gebruik van verscheidene diensten toe waar de `shouldRewrite()` methode waar voor het zelfde Fragment van de Ervaring terugkeert. De dienst die het hoogste aantal van zijn `getPriority()`methode terugkeert is de dienst die de Variatie van het Fragment van de Ervaring behandelt.

Als voorbeeld, kunt u `GenericLinkRewriterProvider` hebben die de basisafbeelding voor alle Fragmenten van de Ervaring behandelt en wanneer de `shouldRewrite()` methode `true` voor alle Variaties van het Fragment van de Ervaring terugkeert. Voor verscheidene specifieke Fragments van de Ervaring, kunt u speciale behandeling willen, zodat in dit geval, kunt u `SpecificLinkRewriterProvider` verstrekken waarvoor de `shouldRewrite()` methode waar slechts voor sommige Variaties van het Fragment van de Ervaring terugkeert. Om ervoor te zorgen dat `SpecificLinkRewriterProvider` wordt gekozen om die Variaties van het Fragment van de Ervaring te behandelen, moet het in zijn `getPriority()` methode een hoger aantal dan terugkeren `GenericLinkRewriterProvider.`
