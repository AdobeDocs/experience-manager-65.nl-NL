---
title: Mobiel met inhoudssynchronisatie
seo-title: Mobiel met inhoudssynchronisatie
description: Volg deze pagina voor meer informatie over Inhoud synchroniseren. Pagina's die in AEM zijn gemaakt, kunnen als toepassingsinhoud worden gebruikt, zelfs als het apparaat offline is. Omdat AEM pagina's zijn gebaseerd op webstandaarden, werken ze bovendien op verschillende platforms, zodat u ze in elke native wrapper kunt insluiten. Deze strategie beperkt de ontwikkelingsinspanningen en stelt u in staat om toepassingsinhoud eenvoudig bij te werken.
seo-description: Volg deze pagina voor meer informatie over Inhoud synchroniseren. Pagina's die in AEM zijn gemaakt, kunnen als toepassingsinhoud worden gebruikt, zelfs als het apparaat offline is. Omdat AEM pagina's zijn gebaseerd op webstandaarden, werken ze bovendien op verschillende platforms, zodat u ze in elke native wrapper kunt insluiten. Deze strategie beperkt de ontwikkelingsinspanningen en stelt u in staat om toepassingsinhoud eenvoudig bij te werken.
uuid: 11f74cc5-99a5-4186-9b60-b19351305432
contentOwner: User
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/MOBILE
topic-tags: developing-on-demand-services-app
discoiquuid: 8fb70ca4-86fc-477d-9773-35b84d5e85a8
translation-type: tm+mt
source-git-commit: a3c303d4e3a85e1b2e794bec2006c335056309fb
workflow-type: tm+mt
source-wordcount: '3057'
ht-degree: 0%

---


# Mobiel met contentsynchronisatie{#mobile-with-content-sync}

>[!NOTE]
>
>Adobe raadt aan de SPA Editor te gebruiken voor projecten die renderen op basis van één pagina voor toepassingsframework op de client-side vereisen (bijvoorbeeld Reageren). [Meer](/help/sites-developing/spa-overview.md) informatie.

Gebruik Content Sync om inhoud te verpakken zodat deze kan worden gebruikt in systeemeigen mobiele toepassingen. Pagina&#39;s die in AEM zijn gemaakt, kunnen als toepassingsinhoud worden gebruikt, zelfs als het apparaat offline is. Omdat AEM pagina&#39;s zijn gebaseerd op webstandaarden, werken ze bovendien op verschillende platforms, zodat u ze in elke native wrapper kunt insluiten. Deze strategie beperkt de ontwikkelingsinspanningen en stelt u in staat om toepassingsinhoud eenvoudig bij te werken.

Met het raamwerk van Content Sync wordt een archiefbestand gemaakt dat de webinhoud bevat. De inhoud kan van alles zijn, variërend van eenvoudige pagina&#39;s, afbeeldingen en PDF-bestanden of volledige webtoepassingen. De API voor het synchroniseren van inhoud biedt toegang tot het archiefbestand via mobiele apps of om processen te maken zodat de inhoud kan worden opgehaald en opgenomen in de app.

De volgende reeks stappen illustreert een typisch geval van gebruik voor de Synchronisatie van de Inhoud:

1. De AEM ontwikkelaar maakt een configuratie voor inhoudssynchronisatie waarmee de inhoud wordt opgegeven die moet worden opgenomen.
1. Met het raamwerk voor inhoudssynchronisatie wordt de inhoud verzameld en in cache opgeslagen.
1. Op een mobiel apparaat wordt de mobiele toepassing gestart en wordt inhoud van de server opgevraagd. Deze inhoud wordt in een ZIP-bestand geleverd.
1. De client pakt de ZIP-inhoud uit in het lokale bestandssysteem. De mapstructuur in het ZIP-bestand simuleert de paden die een client (bijvoorbeeld een browser) normaal gesproken van de server zou aanvragen.
1. De client opent de inhoud in een ingesloten browser of gebruikt deze op een andere manier.
1. Later vraagt de client bijgewerkte inhoud op de server aan. Het Content Sync-framework biedt incrementele updates om de downloadgrootte en -tijd te beperken. Dit kan belangrijk zijn voor mobiele apparaten vanwege beperkte bandbreedte of gegevensvolumes.

## Het ontwikkelen van de Handlers van de Synchronisatie van de Inhoud {#developing-the-content-sync-handlers}

Enkele richtlijnen voor het ontwikkelen van Inhoud synchroniseren-handlers zijn als volgt:

* Handlers moeten *com.day.cq.contentsync.handler.ContentUpdateHandler* implementeren (rechtstreeks of een klasse uitbreiden die dat doet)
* Handlers kunnen *com.adobe.cq.mobile.platform.impl.contentsync.handler.AbstractSlingResourceUpdateHandler* uitbreiden
* Handler mag alleen true rapporteren als deze de cache ContentSync bijwerkt. Bij onjuist rapporteren van true AEM een update worden gemaakt die niet daadwerkelijk werd uitgevoerd.
* De manager zou slechts het geheime voorgeheugen moeten bijwerken als de inhoud werkelijk veranderde. Schrijf niet naar de cache als een wit niet nodig is. Hierdoor wordt een onnodige update gemaakt.

>[!NOTE]
>
>Schakel *Foutopsporingslogbestand met ContentSync* via OSGI-loggerconfiguraties in op pakket *com.day.cq.contentsync*. Dit staat toe om te volgen welke managers in werking stelden en of zij het geheime voorgeheugen bijwerkten en het bijwerken van het geheime voorgeheugen rapporteerden.

## Inhoud voor inhoudssynchronisatie configureren {#configuring-the-content-sync-content}

Maak een configuratie voor Content Sync om de inhoud op te geven van het ZIP-bestand dat aan de client wordt geleverd. U kunt een willekeurig aantal configuraties voor Content Sync maken. Elke configuratie heeft een naam voor identificatiedoeleinden.

Om een configuratie van de Synchronisatie van de Inhoud te creëren, voeg een `cq:ContentSyncConfig` knoop aan de bewaarplaats toe, met het `sling:resourceType` bezit dat aan `contentsync/config` wordt geplaatst. Het `cq:ContentSyncConfig` knooppunt kan overal in de opslagplaats worden gevonden, maar het knooppunt moet toegankelijk zijn voor gebruikers op de AEM-publicatie-instantie. Daarom zou u de knoop onder `/content` moeten toevoegen.

Voeg onderliggende knooppunten toe aan het knooppunt cq:ContentSyncConfig om de inhoud van het ZIP-bestand voor het synchroniseren van inhoud op te geven. De volgende eigenschappen van elk onderliggend knooppunt identificeren een inhoudsitem dat moet worden opgenomen en hoe dit wordt verwerkt wanneer het wordt toegevoegd:

* `path`: De locatie van de inhoud.
* `type`: De naam van het configuratietype dat voor de verwerking van de inhoud moet worden gebruikt. Verschillende typen zijn beschikbaar en worden beschreven in sectie *Configuratietypen*.

Zie *Voorbeeldconfiguratie van de Synchronisatie van de Inhoud* voor meer informatie.

Nadat u de configuratie van de Synchronisatie van de Inhoud creeert, verschijnt het in de console van de Synchronisatie van de Inhoud.

>[!NOTE]
>
>Het raamwerk van Content Sync controleert niet of afhankelijkheden van elementen en ontwerpgerelateerde bestanden zijn opgenomen in pakketten voor inhoudssynchronisatie. Zorg ervoor dat u alle vereiste bestanden opneemt in het ZIP-bestand.

### Toegang tot downloads voor inhoudssynchronisatie configureren {#configuring-access-to-content-sync-downloads}

Geef een gebruiker of groep op die kan worden gedownload van Content Sync. U kunt de standaardgebruiker of de groep vormen die van alle geheime voorgeheugens van de Synchronisatie van de Inhoud kan downloaden, en u kunt het gebrek met voeten treden en toegang voor een specifieke configuratie van de Synchronisatie van de Inhoud vormen.

Wanneer AEM is geïnstalleerd, kunnen leden van de beheerdersgroep standaard downloaden van Content Sync.

#### Standaardtoegang voor downloaden van inhoudssynchronisatie instellen {#setting-the-default-access-for-content-sync-downloads}

Met de Day CQ Content Sync Manager-service hebt u toegang tot Content Sync. Configureer deze service om de gebruiker of groep op te geven die standaard kan downloaden van Content Sync.

Als u [de dienst gebruikend de Console van het Web](/help/sites-deploying/configuring-osgi.md#osgi-configuration-with-the-web-console) vormt, typ de naam van de gebruiker of de groep als waarde van het Toegelaten bezit van het Geheime voorgeheugen van de Terugval.

Als u [configureert in de repository](/help/sites-deploying/configuring-osgi.md#osgi-configuration-in-the-repository), gebruikt u de volgende informatie over de service:

* PID: com.day.cq.contentsync.impl.ContentSyncManagerImpl
* Naam eigenschap: contentSync.fallback.authorizable

#### Download Access negeren voor een Content Sync Cache {#overriding-download-access-for-a-content-sync-cache}

Om downloadtoegang voor een specifieke configuratie van de Synchronisatie van de Inhoud te vormen, voeg het volgende bezit aan de `cq:ContentSyncConfig` knoop toe:

* Naam: toegestaan
* Type: String
* Waarde: De naam van de gebruiker of groep die kan worden gedownload.

Met uw app kunnen gebruikers bijvoorbeeld updates rechtstreeks installeren via Content Sync. Om alle gebruikers in staat te stellen de update te downloaden, stelt u de waarde van de machtigbare eigenschap in op `everyone`.

Als de `cq:ContentSyncConfig` knoop geen autorisable bezit heeft, bepaalt de standaardgebruiker of de groep die voor het Toegelaten bezit van het Geheime voorgeheugen van de Dienst van de Manager van de Synchronisatie van de Inhoud van CQ van de Dag wordt gevormd wie kan downloaden.

### De gebruiker configureren voor het bijwerken van een cache voor inhoudssynchronisatie {#configuring-the-user-for-updating-a-content-sync-cache}

Wanneer een gebruiker een update uitvoert naar de cache van Content Sync, voert een specifieke gebruikersaccount de actie uit namens de gebruiker. De anonieme gebruiker werkt standaard alle cache voor Content Sync bij.

U kunt de standaardgebruiker overschrijven en een gebruiker of groep opgeven die een specifieke cache voor inhoudssynchronisatie bijwerkt.

Als u de standaardgebruiker wilt overschrijven, geeft u een gebruiker of groep op die updates uitvoert voor een specifieke configuratie van Content Sync door de volgende eigenschap toe te voegen aan de node cq:ContentSyncConfig:

* Naam: `updateuser`
* Type: `String`
* Waarde: De naam van de gebruiker of groep die de updates kan uitvoeren.

Als de `cq:ContentSyncConfig` knoop geen `updateuser` bezit heeft, werkt het gebrek `anonymous` gebruiker het geheime voorgeheugen bij.

### Configuratietypen {#configuration-types}

Verwerking kan variëren van het renderen van eenvoudige JSON tot volledige rendering van pagina&#39;s, inclusief de elementen waarnaar wordt verwezen. Deze sectie maakt een lijst van de beschikbare configuratietypen en hun specifieke parameters:

**Kopieer gewoon bestanden en mappen.** 

* **pad**  - Als het pad naar één bestand wijst, wordt alleen het bestand gekopieerd. Als de map naar een map verwijst (inclusief paginaknooppunten), worden alle onderstaande bestanden en mappen gekopieerd.

**** contentRender-inhoud met gebruik van de standaard  [Sling request-verwerking](/help/sites-developing/the-basics.md#sling-request-processing).

* **path**  - Path to resource die output zou moeten zijn.
* **extensie** : extensie die moet worden gebruikt in de aanvraag. Veelvoorkomende voorbeelden zijn *html* en *json*, maar elke andere extensie is mogelijk.

* **kiezer**  - Optionele kiezers, gescheiden door punt. Algemene voorbeelden zijn *touch* voor het renderen van mobiele versies van een pagina of *infinity* voor JSON-uitvoer.

**** clientPackage een Javascript- of CSS-clientbibliotheek.

* **pad** : pad naar de hoofdmap van de clientbibliotheek.
* **extension**  - Type clientbibliotheek. Deze moet op dit moment worden ingesteld op *js* of *css*.

**elementen**

Oorspronkelijke uitvoeringen van elementen verzamelen.

* **path**  - Path to an asset folder below /content/dam.

**** imageCollect een afbeelding.

* **pad**  - pad naar een afbeeldingsbron.

Het afbeeldingstype wordt gebruikt om het We Retail-logo op te nemen in het ZIP-bestand.

**Pagina&#39;s** Renderen AEM pagina&#39;s en verzamelen de middelen waarnaar wordt verwezen.

* **pad**  - Pad naar pagina.
* **extensie** : extensie die moet worden gebruikt in de aanvraag. Voor pagina&#39;s is dit bijna altijd *html*, maar andere zijn nog mogelijk.

* **kiezer**  - Optionele kiezers, gescheiden door punt. Algemene voorbeelden zijn *touch* voor het renderen van mobiele versies van een pagina.

* **deep**  - Optional boolean property determines whether child pages should be included, eveneens. De standaardwaarde is *true.*

* **includeImages**  - Optionele Booleaanse eigenschap die bepaalt of afbeeldingen moeten worden opgenomen. De standaardwaarde is *true*.

   Standaard worden alleen afbeeldingscomponenten met een type basis/componenten/afbeelding als opname beschouwd. U kunt meer middeltypes toevoegen door **De Handler van de Update van de Pagina&#39;s van CQ WCM van de Pagina&#39;s** in de console van het Web te vormen.

**** rewriteHet knooppunt rewrite definieert hoe de koppelingen in de geëxporteerde pagina worden herschreven. De herschreven koppelingen kunnen verwijzen naar de bestanden in het ZIP-bestand of naar de bronnen op de server.

De `rewrite` knoop moet onder `page` knoop worden gevestigd.

De `rewrite` knoop kan één of meerdere van de volgende eigenschappen hebben:

* `clientlibs`: herschrijft clientlibs paden.

* `images`: herschrijft afbeeldingspaden.
* `links`: herschrijft koppelingen paden.

Elke eigenschap kan een van de volgende waarden hebben:

* `REWRITE_RELATIVE`: herschrijft het pad met een relatieve positie ten opzichte van het bestand page.html op het bestandssysteem.

* `REWRITE_EXTERNAL`: herschrijft de weg door aan het middel op de server te richten, gebruikend de AEM  [dienst](/help/sites-developing/externalizer.md) ExternalAlizer.

Met de AEM service **PathRewriterTransformerFactory** kunt u de specifieke HTML-kenmerken configureren die opnieuw worden geschreven. De dienst kan in de console van het Web worden gevormd en heeft een configuratie voor elk bezit van de `rewrite` knoop: `clientlibs`, `images` en `links`.

Deze functie is toegevoegd in AEM 5.5.

### Configuratie {#example-content-sync-configuration} van voorbeeldsynchronisatie

Hieronder ziet u een voorbeeldconfiguratie voor Content Sync.

```xml
+ weretail_go [cq:ContentSyncConfig]
  - sling:resourceType = "contentsync/config"

  + etc.designs.default [nt:unstructured]
    - path = "/etc/designs/default"
    - type = "copy"

  + etc.designs.mobile [nt:unstructured]
    - path = "/etc/designs/mobile"
    - type = "copy"

  + events.plist [nt:unstructured]
    - path = "/content/weretail_mobile/en/events/jcr:content/par/events"
    - type = "content"
    - extension = "plist"

  + events.touch.html [nt:unstructured]
    - path = "/content/weretail_mobile/en/events"
    - type = "pages"
    - extension = "html"
    - selector = "touch"

  + logo [nt:unstructured]
    - path = "/etc/designs/mobile/jcr:content/mobilecontentpage/logo"
    - type = "logo"

  + manifest [nt:unstructured]
    - indexPage = "/content/weretail_mobile/en/events.touch.html"
    - metadataPlist = "/content/weretail_mobile/en/events/_jcr_content/par/events.plist"

  + ...
```

**etc.designs.default en etc.designs.** mobileDe eerste twee ingangen van de configuratie zouden heel duidelijk moeten zijn. Aangezien wij een aantal mobiele pagina&#39;s gaan omvatten, hebben wij de verwante ontwerpdossiers hieronder /etc/designs nodig. En omdat er geen extra verwerkingstijd nodig is, volstaat een kopie.

**events.** plistDit item is een beetje speciaal. Zoals vermeld in de inleiding, zou de toepassing een kaartweergave van tellers van de plaatsen van de gebeurtenissen moeten verstrekken. De benodigde locatie-informatie wordt als een afzonderlijk bestand in PLIST-indeling verstrekt. Dit werkt alleen wanneer de component met de gebeurtenislijst die op de indexpagina wordt gebruikt, een script heeft met de naam plist.jsp. Dit manuscript wordt uitgevoerd wanneer het middel van de component met de .plist uitbreiding wordt gevraagd. Zoals gebruikelijk, wordt de componentenweg gegeven in het wegbezit en het type wordt geplaatst aan inhoud, omdat wij hefboomwerking [het Verschuiven verzoekverwerking](/help/sites-developing/the-basics.md#sling-request-processing) willen.

**events.touch.** htmlNext komt de pagina&#39;s die daadwerkelijk in de app worden weergegeven. De eigenschap path wordt ingesteld op de hoofdpagina van de gebeurtenis. Alle gebeurtenispagina&#39;s onder die pagina worden ook opgenomen, omdat de eigenschap deep standaard op true wordt ingesteld. Pagina&#39;s worden gebruikt als configuratietype, zodat alle afbeeldingen of andere bestanden waarnaar kan worden verwezen vanuit een afbeelding of downloadcomponent op een pagina, worden opgenomen. Bovendien geeft het instellen van de aanraakkiezer ons een mobiele versie van de pagina&#39;s. De configuratie in het eigenschappak bevat meer ingangen van dit type, maar zij worden verlaten hier voor eenvoud.

**** logoHet configuratietype van het logo is tot dusverre niet vermeld en het is geen van de ingebouwde types. Het raamwerk voor het synchroniseren van inhoud kan echter tot op zekere hoogte worden uitgebreid. Dit is een voorbeeld hiervan, dat in de volgende sectie zal worden behandeld.

**** manifestHet is vaak gewenst dat het ZIP-bestand metagegevens bevat, zoals bijvoorbeeld de startpagina van de inhoud. Door dergelijke gegevens te coderen voorkomt u echter dat u deze later gemakkelijk kunt wijzigen. Het kader van de Synchronisatie van de Inhoud steunt dit gebruiksgeval door een duidelijke knoop in de configuratie te zoeken, die eenvoudig door naam wordt geïdentificeerd en geen configuratietype vereist. Elke eigenschap die op dat knooppunt is gedefinieerd, wordt toegevoegd aan een bestand dat ook wel manifest wordt genoemd en dat zich in de hoofdmap van het ZIP-bestand bevindt.

In het voorbeeld moet de pagina met gebeurtenislijsten de startpagina zijn. Deze informatie wordt verstrekt in het **indexPage** bezit en kan zo gemakkelijk op elk ogenblik worden veranderd. Een tweede eigenschap definieert het pad van het bestand *events.plist*. Aangezien wij later zullen zien, kan de cliënttoepassing manifest nu lezen en volgens het handelen.

Zodra de configuratie is ingesteld, kan de inhoud worden gedownload met een browser of een andere HTTP-client, of als u zich ontwikkelt voor iOS, kunt u de speciale WAppKitSync-clientbibliotheek gebruiken. De downloadlocatie bestaat uit het pad van de configuratie en de extensie *.zip*, bijvoorbeeld wanneer u werkt met een lokale AEM: *http://localhost:4502/content/weretail_go.zip*

### De Content Sync Console {#the-content-sync-console}

De console van de Synchronisatie van de Inhoud maakt een lijst van alle configuraties van de Synchronisatie van de Inhoud in de bewaarplaats (alle knopen van type `cq:ContentSyncConfig`) en voor elke configuratie staat u toe om het volgende te doen:

* De cache bijwerken.
* Wis de cache.
* Download een volledig postvak.
* Download een diff zip tussen nu en een specifieke datum en tijd.

Het kan nuttig zijn voor ontwikkeling en het oplossen van problemen.

De console is toegankelijk op:

`http://localhost:4502/libs/cq/contentsync/content/console.html`

Het ziet er als volgt uit:

![chlimage_1-50](assets/chlimage_1-50.png)

### Uitbreiding van het raamwerk voor inhoudssynchronisatie {#extending-the-content-sync-framework}

Hoewel het aantal configuratieopties reeds vrij uitgebreid is, kan het niet alle vereisten van uw specifiek gebruiksgeval behandelen. In deze sectie worden de extensiepunten van het Content Sync-framework beschreven en hoe u aangepaste configuratietypen kunt maken.

Voor elk configuratietype, is er een *Handler van de Update van de Inhoud*, die een OSGi componentenfabriek is die voor dat specifieke type wordt geregistreerd. Deze handlers verzamelen inhoud, verwerken deze en voegen deze toe aan een cache die door het Content Sync-framework wordt onderhouden. Implementeer de volgende interface of abstracte basisklasse:

* `com.day.cq.contentsync.handler.ContentUpdateHandler` - Interface die alle updatemanagers moeten uitvoeren
* `com.day.cq.contentsync.handler.AbstractSlingResourceUpdateHandler` - Een abstracte klasse die het teruggeven van middelen gebruikend Sling vereenvoudigt

Registreer uw klasse als OSGi componentenfabriek en stel het in de container OSGi in een bundel op. Dit kan worden gedaan gebruikend [Gemaakt SCR plugin](https://felix.apache.org/site/apache-felix-maven-scr-plugin.html) of gebruikend markeringen JavaDoc of annotaties. In het volgende voorbeeld wordt de JavaDoc-versie getoond:

```java
/*
 * @scr.component metatype="no"
 * factory="com.day.cq.contentsync.handler.ContentUpdateHandler/customtype"
 */
public class CustomTypeUpdateHandler implements ContentUpdateHandler {
    // add your code here
}

/*
 * @scr.component metatype="no" inherit="true"
 * factory="com.day.cq.contentsync.handler.ContentUpdateHandler/othertype"
 */
public class OtherTypeUpdateHandler extends AbstractSlingResourceUpdateHandler {
    // add your code here
}
```

De definitie *factory* bevat de algemene interface en het aangepaste type, gescheiden door slash. Deze strategie laat het kader van de Synchronisatie van de Inhoud toe om een geval van uw douaneklasse te vinden en tot stand te brengen aangezien het het douanetype in een configuratieingang erkent. In de volgende sectie ziet u een concreet voorbeeld van een aangepaste update-handler.

>[!CAUTION]
>
>Wanneer het bouwen op de AbstractSlingResourceUpdateHandler basisklasse, moet u *inherit* definitie toevoegen. Anders zal de container OSGi niet de vereiste verwijzingen plaatsen die in de basisklasse worden verklaard.

### Een aangepaste updatehandler {#implementing-a-custom-update-handler} implementeren

Elke pagina Web.Retail Mobile bevat een logo in de linkerbovenhoek dat we natuurlijk in het ZIP-bestand willen opnemen. Voor het optimaliseren van het cachegeheugen verwijst AEM echter niet naar de werkelijke locatie van het afbeeldingsbestand in de opslagplaats, waardoor we niet gewoon het configuratietype **copy** kunnen gebruiken. Wat wij in plaats daarvan moeten doen is ons eigen **logo** configuratietype verstrekken dat het beeld bij de plaats beschikbaar maakt die door AEM wordt gevraagd. In het volgende codevoorbeeld wordt de volledige implementatie van de logo-updatehandler getoond:

#### LogoUpdateHandler.java {#logoupdatehandler-java}

```java
package com.day.cq.wcm.apps.weretail.impl;

import javax.jcr.Node;
import javax.jcr.RepositoryException;
import javax.jcr.Session;

import org.apache.sling.api.resource.Resource;
import org.apache.sling.api.resource.ResourceResolver;
import org.apache.sling.jcr.resource.JcrResourceResolverFactory;

import com.day.cq.commons.jcr.JcrUtil;
import com.day.cq.contentsync.config.ConfigEntry;
import com.day.cq.contentsync.handler.ContentUpdateHandler;
import com.day.cq.wcm.foundation.Image;
import com.day.text.Text;

/**
 * The <code>LogoUpdateHandler</code> is used to update the content sync cache
 * with a page logo added using a logo component.
 *
 * @scr.component metatype="no"
 * factory="com.day.cq.contentsync.handler.ContentUpdateHandler/logo"
 */
public class LogoUpdateHandler implements ContentUpdateHandler {

    private static final Logger log = LoggerFactory.getLogger(LogoUpdateHandler.class);

    /** @scr.reference policy="static" */
    protected JcrResourceResolverFactory resolverFactory;

    public boolean updateCacheEntry(ConfigEntry configEntry, Long lastUpdated, String configCacheRoot, Session admin, Session session) {
        ResourceResolver resolver = resolverFactory.getResourceResolver(admin);
        Resource resource = resolver.getResource(configEntry.getContentPath());

        Image img = new Image(resource);
        img.setItemName(Image.NN_FILE, "image");
        img.setItemName(Image.PN_REFERENCE, "imageReference");
        img.setSelector("img");

        try {
            if(img.getLastModified() == null || lastUpdated < img.getLastModified().getTime().getTime()) {
                String src = img.getSrc();
                String parentPath = configCacheRoot + Text.getRelativeParent(src, 1);

                Node parent = JcrUtil.createPath(parentPath, "sling:Folder", admin);
                Node image = resolver.getResource(resource.getPath() + "/image").adaptTo(Node.class);
                JcrUtil.copy(image, parent, Text.getName(src));

                admin.save();

                return true;
            }
        } catch (RepositoryException e) {
            log.error("Unexpected error while updating logo: ", e);
        }

        return false;
    }
}
```

De `LogoUpdateHandler` klasse voert de `ContentUpdateHandler` methode `updateCacheEntry(ConfigEntry, Long, String, Session, Session)` van de interface uit, die een aantal argumenten neemt:

* Een `ConfigEntry` instantie die toegang tot de configuratieingang verleent, waarvoor deze manager, en zijn eigenschappen wordt geroepen.
* Een `lastUpdated` tijdstempel die aangeeft wanneer de Content Sync voor het laatst de cache heeft bijgewerkt. Inhoud die na die tijdstempel niet is gewijzigd, moet niet door de handler worden bijgewerkt.
* Een argument `configCacheRoot` dat de wortelweg van het geheime voorgeheugen specificeert. Alle bijgewerkte bestanden moeten onder dit pad worden opgeslagen om aan het ZIP-bestand te worden toegevoegd.
* Een beheersessie die moet worden gebruikt voor alle bewerkingen in de opslagplaats die betrekking hebben op cache.
* Een gebruikerssessie die kan worden gebruikt om inhoud bij te werken in de context van een bepaalde gebruiker en zo een soort gepersonaliseerde inhoud te verstrekken.

Om de douanemanager uit te voeren, creeer eerst een geval van de klasse van het Beeld die op het middel wordt gebaseerd dat in de configuratieingang wordt gegeven. Dit is eigenlijk dezelfde procedure als de eigenlijke logocomponent op onze pagina&#39;s. Het zorgt ervoor dat het doelpad van de afbeelding hetzelfde is als het pad waarnaar op een pagina wordt verwezen.

Controleer vervolgens of de bron is gewijzigd sinds de laatste update. De implementaties van de douane zouden onnodige updates van het geheime voorgeheugen moeten vermijden en zouden vals terugkeren als niets verandert. Als de bron is gewijzigd, kopieert u de afbeelding naar de verwachte doellocatie ten opzichte van de cachroot. Ten slotte wordt `true` geretourneerd om aan te geven dat de cache is bijgewerkt.

## De inhoud op de client gebruiken {#using-the-content-on-the-client}

Als u inhoud wilt gebruiken in een mobiele toepassing die wordt geleverd door Content Sync, moet u inhoud aanvragen via een HTTP- of HTTPS-verbinding. Hierdoor kan opgehaalde inhoud (verpakt in een ZIP-bestand) lokaal worden uitgepakt en opgeslagen op het mobiele apparaat. De inhoud heeft niet alleen betrekking op gegevens, maar ook op logica, d.w.z. volledige webtoepassingen; en de mobiele gebruiker in staat te stellen opgehaalde webtoepassingen en de bijbehorende gegevens uit te voeren, zelfs zonder netwerkconnectiviteit.

Content Sync levert inhoud op intelligente wijze: Alleen gegevenswijzigingen sinds de laatste geslaagde gegevenssynchronisatie worden geleverd, waardoor de vereiste tijd voor gegevensoverdracht afneemt. Bij de eerste uitvoering van een toepassing worden gegevenswijzigingen aangevraagd sinds 1 januari 1970, en daarna worden alleen gegevens gevraagd die zijn gewijzigd sinds de laatste succesvolle synchronisatie. AEM maakt gebruik van een communicatieframework voor iOS om de communicatie en overdracht van gegevens te vereenvoudigen, zodat een minimale hoeveelheid native code vereist is om een iOS-gebaseerde webtoepassing in te schakelen.

Alle overgedragen gegevens kunnen in dezelfde mappenstructuur worden geëxtraheerd, er zijn geen extra stappen (bijvoorbeeld afhankelijkheidscontroles) vereist voor het ophalen van gegevens. In het geval van iOS worden alle gegevens opgeslagen in een submap in de map Documents van de iOS-app.

Typisch uitvoeringspad van een AEM Mobile-app op iOS:

* De gebruiker start de toepassing op een iOS-apparaat.
* App probeert verbinding te maken met AEM back-end en vraagt om gegevenswijzigingen sinds de laatste uitvoering.
* De server haalt de gegevens in kwestie op en zet ze in een bestand neer.
* De gegevens worden geretourneerd naar het clientapparaat waar ze worden uitgepakt in de documentenmap.
* De component UIWebView start/vernieuwt.

Als er geen verbinding kon worden gemaakt, worden eerder gedownloade gegevens weergegeven.

### Aanvullende bronnen {#additional-resources}

Zie de volgende bronnen voor meer informatie over de rollen en verantwoordelijkheden van een beheerder en een auteur:

* [Authoring AEM inhoud voor AEM Mobile On-demand Services](/help/mobile/mobile-apps-ondemand.md)
* [Inhoud beheren voor gebruik van AEM Mobile On-demand Services](/help/mobile/aem-mobile.md)

