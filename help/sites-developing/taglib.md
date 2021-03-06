---
title: Tagbibliotheken
seo-title: Tagbibliotheken
description: Met de tagbibliotheken Granite, CQ en Sling hebt u toegang tot specifieke functies voor gebruik in het JSP-script van uw sjablonen en componenten
seo-description: Met de tagbibliotheken Granite, CQ en Sling hebt u toegang tot specifieke functies voor gebruik in het JSP-script van uw sjablonen en componenten
uuid: e622d47b-cfb3-4b4a-b8e3-e1adee294219
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: platform
content-type: reference
discoiquuid: 6678e3c3-fb0f-4300-8838-38f23f14db07
exl-id: 50e608d5-951f-4a3f-bed4-9e92ff5d7bd4
source-git-commit: de5eb53f6160991ca0718d61afaeed2078a4fa88
workflow-type: tm+mt
source-wordcount: '2509'
ht-degree: 1%

---

# Tagbibliotheken{#tag-libraries}

Met de tagbibliotheken Granite, CQ en Sling hebt u toegang tot specifieke functies voor gebruik in het JSP-script van uw sjablonen en componenten.

## Graniet-tagbibliotheek {#granite-tag-library}

De tagbibliotheek Granite bevat nuttige functies.

Wanneer u het jsp manuscript van een component van Granite UI ontwikkelt, wordt het geadviseerd om volgende code bij de bovenkant van het manuscript te omvatten:

```xml
<%@include file="/libs/granite/ui/global.jsp"%>
```

De algemene instructie declareert ook de [Sling library](/help/sites-developing/taglib.md#sling-tag-library).

```xml
<%@taglib prefix="sling" uri="https://sling.apache.org/taglibs/sling" %>
```

### &lt;ui:includeclientlib> {#ui-includeclientlib}

De tag `<ui:includeClientLib>` bevat een AEM HTML-clientbibliotheek, die een js, css of een themabibliotheek kan zijn. Voor meerdere inclusies van verschillende typen, bijvoorbeeld js en css, moet deze tag meerdere keren worden gebruikt in de jsp. Deze tag is een handige omslag rondom de service-interface ` [com.adobe.granite.ui.clientlibs.HtmlLibraryManager](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/adobe/granite/ui/clientlibs/HtmlLibraryManager.html)`.

Deze heeft de volgende kenmerken:

**Categorie??n**  - Een lijst met door komma&#39;s gescheiden clientcategorie??n. Dit omvat alle JavaScript- en CSS-bibliotheken voor de opgegeven categorie??n. De themanaam wordt uit de aanvraag ge??xtraheerd.

Is gelijk aan: `com.adobe.granite.ui.clientlibs.HtmlLibraryManager#writeIncludes`

**theme**  - A list of comma-separated client lib Categorie??n. Dit omvat alle themabibliotheken (zowel CSS als JS) voor de opgegeven categorie??n. De themanaam wordt uit de aanvraag ge??xtraheerd.

Is gelijk aan: `com.adobe.granite.ui.clientlibs.HtmlLibraryManager#writeThemeInclude`

**js**  - Een lijst met door komma&#39;s gescheiden clientcategorie??n. Dit omvat alle bibliotheken Javascript voor de bepaalde categorie??n.

Is gelijk aan: `com.adobe.granite.ui.clientlibs.HtmlLibraryManager#writeJsInclude`

**css**  - Een lijst met door komma&#39;s gescheiden clientcategorie??n. Dit omvat alle CSS-bibliotheken voor de opgegeven categorie??n.

Is gelijk aan: `com.adobe.granite.ui.clientlibs.HtmlLibraryManager#writeCssInclude`

**thema**  - Een vlag die alleen aangeeft of het alleen om bibliotheken met thema&#39;s of niet-thema&#39;s gaat, moet worden opgenomen. Als deze waarde wordt weggelaten, worden beide sets opgenomen. Alleen van toepassing op zuivere JS- of CSS-include-bestanden (niet voor categorie??n of thema-include-bestanden).

De tag `<ui:includeClientLib>` kan als volgt worden gebruikt in een JSP:

```xml
<%-- all: js + theme (theme-js + css) --%>
<ui:includeClientLib categories="cq.wcm.edit" />

<%-- only js libs --%>
<ui:includeClientLib js="cq.collab.calendar, cq.security" />

<%-- theme only (theme-js + css) --%>
<ui:includeClientLib theme="cq.collab.calendar, cq.security" />

<%-- css only --%>
<ui:includeClientLib css="cq.collab.calendar, cq.security" />
```

## CQ-tagbibliotheek {#cq-tag-library}

De tagbibliotheek CQ bevat nuttige functies.

Als u de CQ-tagbibliotheek in uw script wilt gebruiken, moet het script beginnen met de volgende code:

```xml
<%@taglib prefix="cq" uri="https://www.day.com/taglibs/cq/1.0" %>
```

>[!NOTE]
>
>Als het `/libs/foundation/global.jsp`-bestand in het script wordt opgenomen, wordt de taglib automatisch gedeclareerd.

Wanneer u het Jsp manuscript van een AEM component ontwikkelt, wordt het geadviseerd om volgende code bij de bovenkant van het manuscript te omvatten:

```xml
<%@include file="/libs/foundation/global.jsp"%>
```

De tags sling, CQ en jstl worden gedeclareerd en de regelmatig gebruikte scriptobjecten die worden gedefinieerd door de tag [ `<cq:defineObjects />`](#amp-lt-cq-defineobjects) worden weergegeven. Hierdoor wordt de jsp-code van uw component verkort en vereenvoudigd.

### &lt;cq:text> {#cq-text}

De tag `<cq:text>` is een gebruikstag die de componenttekst in een JSP uitvoert.

Het heeft de volgende optionele kenmerken:

**property**  - Name of the property to use. De naam is relatief ten opzichte van de huidige bron.

**value**  - Value to use for output. Als dit kenmerk aanwezig is, wordt het gebruik van het eigenschapkenmerk overschreven.

**oldValue**  - Waarde voor diff-uitvoer. Als dit kenmerk aanwezig is, wordt het gebruik van het eigenschapkenmerk overschreven.

**escapeXml**  - Definieert of de tekens  &lt;>, &amp;, &#39; en &quot; in de resulterende tekenreeks moeten worden omgezet in de corresponderende tekeneenheidcodes. De standaardwaarde is false. De escaping wordt toegepast na de optionele opmaak.

**format**  - Optional java.text.Format to use for formatting the text.

**noDiff**  - Onderdrukt de berekening van een diff output, zelfs als diff informatie aanwezig is.

**tagClass**  - CSS-klassenaam van een element dat een niet-lege uitvoer omsluit. Als dit leeg is, wordt geen element toegevoegd.

**tagName**  - Naam van het element dat een niet-lege uitvoer omringt. De standaardwaarde is DIV.

**tijdelijke aanduiding**  - Standaardwaarde voor lege of null-tekst in de bewerkingsmodus, dat wil zeggen de tijdelijke aanduiding. De standaardcontrole wordt uitgevoerd na de optionele opmaak en escape, d.w.z. dat deze ongewijzigd naar de uitvoer wordt geschreven. De standaardwaarde is:

`<div><span class="cq-text-placeholder">&para;</span></div>`

**default**  - Default value to use for null or empty text. De standaardcontrole wordt uitgevoerd na de optionele opmaak en escape, d.w.z. dat deze ongewijzigd naar de uitvoer wordt geschreven.

Enkele voorbeelden van hoe de tag `<cq:text>` in een JSP kan worden gebruikt:

```xml
<cq:text property="jcr:title" tagName="h2"/>
<cq:text property="jcr:description" tagName="p"/>

<cq:text value="<%= listItem.getTitle() %>" tagName="h4" placeholder="" />
<cq:text value="<%= listItem.getDescription() %>" tagName="p" placeholder=""/>

<cq:text property="jcr:title" value="<%= title %>" tagName="h3"/><%
    } else if (type.equals("link")) {
        %><cq:text property="jcr:title" value="<%= "\u00bb " + title %>" tagName="p" tagClass="link"/><%
    } else if (type.equals("extralarge")) {
        %><cq:text property="jcr:title" value="<%= title %>" tagName="h1"/><%
    } else {
        %><cq:text property="jcr:title" value="<%= title %>" tagName="h2"/><%

<cq:text property="jcr:description" placeholder="" tagName="small"/>

<cq:text property="tableData"
               escapeXml="false"
               placeholder="<img src=\"/libs/cq/ui/resources/0.gif\" class=\"cq-table-placeholder\" alt=\"\">"
    />

<cq:text property="text"/>

<cq:text property="image/jcr:description" placeholder="" tagName="small"/>
<cq:text property="text" tagClass="text"/>
```

### &lt;cq:setcontentbundle> {#cq-setcontentbundle}

Met de tag `<cq:setContentBundle>` wordt een i18n-lokalisatiecontext gemaakt en opgeslagen in de configuratievariabele `javax.servlet.jsp.jstl.fmt.localizationContext`.

Deze heeft de volgende kenmerken:

**taal**  - De taal van de landinstelling waarvoor de resourcebundel moet worden opgehaald.

**bron**  - De bron waaruit de landinstelling moet worden opgehaald. Deze kan op een van de volgende waarden worden ingesteld:

* **statisch**  - de landinstelling wordt overgenomen uit het  `language` kenmerk, indien beschikbaar, anders uit de standaardlandinstelling van de server.

* **pagina** - de landinstelling wordt overgenomen uit de taal van de huidige pagina of bron, indien beschikbaar, anders uit het  `language` kenmerk indien beschikbaar, anders uit de standaardlandinstelling van de server.

* **request** - de landinstelling wordt overgenomen uit de landinstelling van het verzoek (  `request.getLocale()`).

* **auto** - de sc??ne wordt genomen uit het  `language` attribuut indien beschikbaar, anders van de taal van de huidige pagina of bron indien beschikbaar, anders van het verzoek.

Als het kenmerk `source` niet is ingesteld:

* Als het `language` attribuut wordt geplaatst, `source` gebrek aan &quot;`static`.

* Wanneer het kenmerk `language` niet is ingesteld, wordt het kenmerk `source` standaard ingesteld op `auto`.

De &quot;inhoudsbundel&quot; kan eenvoudig worden gebruikt door standaard JSTL `<fmt:message>`-tags. De zoekopdracht van berichten via sleutels is tweeledig:

1. Ten eerste worden de JCR-eigenschappen van de onderliggende bron die momenteel wordt gerenderd, doorzocht op vertalingen. Op deze manier kunt u een eenvoudig componentdialoogvenster defini??ren om deze waarden te bewerken.
1. Als het knooppunt geen eigenschap bevat die precies dezelfde naam heeft als de sleutel, moet de fallback een resourcepakket laden vanuit het slingverzoek ( `SlingHttpServletRequest.getResourceBundle(Locale)`). De taal of landinstelling voor deze bundel wordt gedefinieerd door de taal- en bronkenmerken van de tag `<cq:setContentBundle>`.

De tag `<cq:setContentBundle>` kan als volgt worden gebruikt in een jsp.

Voor pagina&#39;s die hun taal bepalen:

```xml
... %><cq:setContentBundle source="page"/><%  %>
<div class="error"><fmt:message key="Hello"/>
</div> ...
```

Voor gepersonaliseerde pagina&#39;s van de gebruiker:

```xml
... %><cq:setContentBundle scope="request"/><% %>
<div class="error"><fmt:message key="Hello"/>
</div> ...
```

### &lt;cq:include> {#cq-include}

De tag `<cq:include>` bevat een bron op de huidige pagina.

Deze heeft de volgende kenmerken:

**flush**

* Een Booleaanse waarde die definieert of de uitvoer moet worden verwijderd voordat het doel wordt opgenomen.

**path**

* De weg aan het middelvoorwerp dat in de huidige verzoekverwerking moet worden omvat. Als dit pad relatief is, wordt het toegevoegd aan het pad van de huidige bron waarvan het script de opgegeven bron bevat. Of weg en resourceType, of manuscript moet worden gespecificeerd.

**resourceType**

* The resource type of the resource to be included. Als het middeltype wordt geplaatst, moet de weg de nauwkeurige weg aan een middelvoorwerp zijn: in dit geval wordt het toevoegen van parameters, kiezers en extensies aan het pad niet ondersteund.
* Als de bron die moet worden opgenomen, wordt opgegeven met het padkenmerk dat niet kan worden omgezet naar een bron, maakt de tag mogelijk een synthetisch bronobject uit het pad en dit resourcetype.
* Of weg en resourceType, of manuscript moet worden gespecificeerd.

**script**

* Het JSP-script dat moet worden opgenomen. Of weg en resourceType, of manuscript moet worden gespecificeerd.

**ignoreComponentHierarchy**

* Een Booleaanse waarde die bepaalt of de componenthi??rarchie moet worden genegeerd voor scriptresolutie. Indien waar (true), worden alleen de zoekpaden gebruikt.

**Voorbeeld:**

```xml
<%@taglib prefix="cq" uri="https://www.day.com/taglibs/cq/1.0" %><%
%><div class="center">
    <cq:include path="trail" resourceType="foundation/components/breadcrumb" />
    <cq:include path="title" resourceType="foundation/components/title" />
    <cq:include script="redirect.jsp"/>
    <cq:include path="par" resourceType="foundation/components/parsys" />
</div>
```

Wilt u `<%@ include file="myScript.jsp" %>` of `<cq:include script="myScript.jsp" %>` gebruiken om een script op te nemen?

* De instructie `<%@ include file="myScript.jsp" %>` informeert de JSP-compiler om een volledig bestand in het huidige bestand op te nemen. Het is alsof de inhoud van het ingesloten bestand rechtstreeks in het oorspronkelijke bestand is geplakt.
* Met de tag `<cq:include script="myScript.jsp">` wordt het bestand opgenomen bij uitvoering.

Moet u `<cq:include>` of `<sling:include>` gebruiken?

* Bij het ontwikkelen van AEM componenten, adviseert Adobe dat u `<cq:include>` gebruikt.
* `<cq:include>` kunt u scriptbestanden direct op naam opnemen wanneer u het scriptkenmerk gebruikt. Dit neemt component en middeltypeovererving in overweging, en is vaak eenvoudiger dan strikte naleving van het manuscriptresolutie van het Sling gebruikend selecteurs en uitbreidingen.

### &lt;cq:includeclientlib> {#cq-includeclientlib}

>[!CAUTION]
>
>`<cq:includeClientLib>` is afgekeurd sinds AEM 5.6.  [ `<ui:includeClientLib>`](/help/sites-developing/taglib.md#ui-includeclientlib) moet worden gebruikt.

De tag `<cq:includeClientLib>` bevat een AEM HTML-clientbibliotheek, die een JS, een css of een themabibliotheek kan zijn. Voor meerdere inclusies van verschillende typen, bijvoorbeeld js en css, moet deze tag meerdere keren worden gebruikt in de jsp. Deze tag is een handige omslag rondom de service-interface `com.day.cq.widget.HtmlLibraryManager`.

Deze heeft de volgende kenmerken:

**Categorie??n**  - Een lijst met door komma&#39;s gescheiden clientcategorie??n. Dit omvat alle JavaScript- en CSS-bibliotheken voor de opgegeven categorie??n. De themanaam wordt uit de aanvraag ge??xtraheerd.

Is gelijk aan: `com.day.cq.widget.HtmlLibraryManager#writeIncludes`

**theme**  - A list of comma-separated client lib Categorie??n. Dit omvat alle themabibliotheken (zowel CSS als JS) voor de opgegeven categorie??n. De themanaam wordt uit de aanvraag ge??xtraheerd.

Equivalent met: `com.day.cq.widget.HtmlLibraryManager#`writeThemeInclude

**js**  - Een lijst met door komma&#39;s gescheiden clientcategorie??n. Dit omvat alle bibliotheken Javascript voor de bepaalde categorie??n.

Is gelijk aan: `com.day.cq.widget.HtmlLibraryManager#writeJsInclude`

**css**  - Een lijst met door komma&#39;s gescheiden clientcategorie??n. Dit omvat alle CSS-bibliotheken voor de opgegeven categorie??n.

Is gelijk aan: `com.day.cq.widget.HtmlLibraryManager#writeCssInclude`

**thema**  - Een vlag die alleen aangeeft of het alleen om bibliotheken met thema&#39;s of niet-thema&#39;s gaat, moet worden opgenomen. Als deze waarde wordt weggelaten, worden beide sets opgenomen. Alleen van toepassing op zuivere JS- of CSS-include-bestanden (niet voor categorie??n of thema-include-bestanden).

De tag `<cq:includeClientLib>` kan als volgt worden gebruikt in een JSP:

```xml
<%-- all: js + theme (theme-js + css) --%>
<cq:includeClientLib categories="cq.wcm.edit" />

<%-- only js libs --%>
<cq:includeClientLib js="cq.collab.calendar, cq.security" />

<%-- theme only (theme-js + css) --%>
<cq:includeClientLib theme="cq.collab.calendar, cq.security" />

<%-- css only --%>
<cq:includeClientLib css="cq.collab.calendar, cq.security" />
```

### &lt;cq:defineobjects> {#cq-defineobjects}

Met de tag `<cq:defineObjects>` worden de volgende, regelmatig gebruikte scriptobjecten weergegeven waarnaar de ontwikkelaar kan verwijzen. De code stelt ook de objecten beschikbaar die worden gedefinieerd door de [ `<sling:defineObjects>`](#amp-lt-sling-defineobjects)-tag.

**componentContext**

* het huidige componentcontextobject van de aanvraag (com.day.cq.wcm.api.components.ComponentContext interface).

**component**

* het huidige AEM componentobject van de huidige resource (com.day.cq.wcm.api.components.Component interface).

**currentDesign**

* het huidige ontwerpobject van de huidige pagina (com.day.cq.wcm.api.designer.Design interface).

**currentPage**

* het huidige AEM WCM-paginaobject (com.day.cq.wcm.api.Page interface).

**currentStyle**

* het huidige stijlobject van de huidige cel (com.day.cq.wcm.api.designer.Style interface).

**ontwerper**

* het ontwerperobject dat wordt gebruikt voor toegang tot ontwerpinformatie (com.day.cq.wcm.api.designer.Designer-interface).

**editContext**

* het contextobject edit van de AEM component (com.day.cq.wcm.api.components.EditContext interface).

**pageManager**

* het paginabeheerobject voor bewerkingen op paginaniveau (com.day.cq.wcm.api.PageManager-interface).

**pageProperties**

* het pagina-eigenschappenobject van de huidige pagina (org.apache.sling.api.resource.ValueMap).

**eigenschappen**

* het eigenschapsobject van de huidige bron (org.apache.sling.api.resource.ValueMap).

**resourceDesign**

* het ontwerpobject van de middelpagina (com.day.cq.wcm.api.designer.Design interface).

**resourcePage**

* het resource page-object (com.day.cq.wcm.api.Page-interface).
* Deze heeft de volgende kenmerken:

**requestName**

* overgenomen van sling

**responseName**

* overgenomen van sling

**resourceName**

* overgenomen van sling

**nodeName**

* overgenomen van sling

**logName**

* overgenomen van sling

**resourceResolverName**

* overgenomen van sling

**slingName**

* overgenomen van sling

**componentContextName**

* specifiek voor wcm

**editContextName**

* specifiek voor wcm

**propertiesName**

* specifiek voor wcm

**pageManagerName**

* specifiek voor wcm

**currentPageName**

* specifiek voor wcm

**resourcePageName**

* specifiek voor wcm

**pagePropertiesName**

* specifiek voor wcm

**componentName**

* specifiek voor wcm

**designerName**

* specifiek voor wcm

**currentDesignName**

* specifiek voor wcm

**resourceDesignName**

* specifiek voor wcm

**currentStyleName**

* specifiek voor wcm

**Voorbeeld**

```xml
<%@page session="false" contentType="text/html; charset=utf-8" %><%
%><%@ page import="com.day.cq.wcm.api.WCMMode" %><%
%><%@taglib prefix="cq" uri="https://www.day.com/taglibs/cq/1.0" %><%
%><cq:defineObjects/>
```

>[!NOTE]
>
>Wanneer het `/libs/foundation/global.jsp` dossier in het manuscript wordt omvat, wordt `<cq:defineObjects />` markering automatisch omvat.

### &lt;cq:requesturl> {#cq-requesturl}

Met de tag `<cq:requestURL>` wordt de huidige aanvraag-URL naar de JspWriter geschreven. De twee tags [ `<cq:addParam>`](#amp-lt-cq-addparam) en [ `<cq:removeParam>`](#amp-lt-cq-removeparam) en kunnen binnen de hoofdtekst van deze tag worden gebruikt om de huidige aanvraag-URL te wijzigen voordat deze wordt geschreven.

Hiermee kunt u koppelingen maken naar de huidige pagina met verschillende parameters. Zo kunt u bijvoorbeeld de aanvraag transformeren:

`mypage.html?mode=view&query=something` naar  `mypage.html?query=something`.

Het gebruik van `addParam` of `removeParam` verandert slechts het voorkomen van de bepaalde parameter, zijn alle andere parameters onaangetast.

`<cq:requestURL>` heeft geen kenmerk.

Voorbeelden:

```xml
<a href="<cq:requestURL><cq:removeParam name="language"/></cq:requestURL>">remove filter</a>
```

```xml
<a title="filter results" href="<cq:requestURL><cq:addParam name="language" value="${bucket.value}"/></cq:requestURL>">${label} (${bucket.count})</a>
```

### &lt;cq:addparam> {#cq-addparam}

De tag `<cq:addParam>` voegt een aanvraagparameter met de opgegeven naam en waarde toe aan de omsluitende tag [ `<cq:requestURL>`](#amp-lt-cq-requesturl).

Deze heeft de volgende kenmerken:

**name**

* naam van de parameter die moet worden toegevoegd

**value**

* waarde van de toe te voegen parameter

**Voorbeeld:**

```xml
<a title="filter results" href="<cq:requestURL><cq:addParam name="language" value="${bucket.value}"/></cq:requestURL>">${label} (${bucket.count})</a>
```

### &lt;cq:removeparam> {#cq-removeparam}

De tag `<cq:removeParam>` verwijdert een aanvraagparameter met de opgegeven naam en waarde uit de omsluitende tag [ `<cq:requestURL>`](#amp-lt-cq-requesturl). Als er geen waarde is opgegeven, worden alle parameters met de opgegeven naam verwijderd.

Deze heeft de volgende kenmerken:

**name**

* naam van de te verwijderen parameter

Voorbeeld:

```xml
<a href="<cq:requestURL><cq:removeParam name="language"/></cq:requestURL>">remove filter</a>
```

## Tagbibliotheek verkopen {#sling-tag-library}

De tagbibliotheek Sling bevat handige functies voor verkopers.

Wanneer u de Sling-tagbibliotheek in uw script gebruikt, moet het script beginnen met de volgende code:

```xml
<%@ taglib prefix="sling" uri="https://sling.apache.org/taglibs/sling/1.0" %>
```

>[!NOTE]
>
>Wanneer het `/libs/foundation/global.jsp`-bestand in het script wordt opgenomen, wordt de lablib voor de schuine streep automatisch gedeclareerd.

### &lt;sling:include> {#sling-include}

De tag `<sling:include>` bevat een bron op de huidige pagina.

Deze heeft de volgende kenmerken:

**flush**

* Een Booleaanse waarde die definieert of de uitvoer moet worden verwijderd voordat het doel wordt opgenomen.

**resource**

* Het bronobject dat moet worden opgenomen in de huidige aanvraagverwerking. resource of pad moet worden opgegeven. Als beide zijn opgegeven, heeft de bron voorrang.

**pad**

* De weg aan het middelvoorwerp dat in de huidige verzoekverwerking moet worden omvat. Als dit pad relatief is, wordt het toegevoegd aan het pad van de huidige bron waarvan het script de opgegeven bron bevat. resource of pad moet worden opgegeven. Als beide zijn opgegeven, heeft de bron voorrang.

**resourceType**

* The resource type of the resource to be included. Als het middeltype wordt geplaatst, moet de weg de nauwkeurige weg aan een middelvoorwerp zijn: in dit geval wordt het toevoegen van parameters, kiezers en extensies aan het pad niet ondersteund.
* Als de bron die moet worden opgenomen, wordt opgegeven met het padkenmerk dat niet kan worden omgezet naar een bron, maakt de tag mogelijk een synthetisch bronobject uit het pad en dit resourcetype.

**replaceSelectors**

* Bij het verzenden worden de kiezers vervangen door de waarde van dit kenmerk.

**addSelectors**

* Tijdens het verzenden wordt de waarde van dit kenmerk toegevoegd aan de kiezers.

**replaceSuffix**

* Bij het verzenden wordt het achtervoegsel vervangen door de waarde van dit kenmerk.

>[!NOTE]
>
>De resolutie van de bron en het script die in de tag `<sling:include>` zijn opgenomen, is gelijk aan die voor een normale sling-URL-resolutie. Standaard zijn dit de kiezers, de extensie, enzovoort. van het huidige verzoek worden ook gebruikt voor het inbegrepen manuscript. Ze kunnen worden gewijzigd met de tagkenmerken: Met `replaceSelectors="foo.bar"` kunt u bijvoorbeeld de kiezers overschrijven.

Voorbeelden:

```xml
<div class="item"><sling:include path="<%= pathtoinclude %>"/></div>
```

```xml
<sling:include resource="<%= par %>"/>
```

```xml
<sling:include addSelectors="spool"/>
```

```xml
<sling:include resource="<%= par %>" resourceType="<%= newType %>"/>
```

```xml
<sling:include resource="<%= par %>" resourceType="<%= newType %>"/>
```

```xml
<sling:include replaceSelectors="content" />
```

### &lt;sling:defineobjects> {#sling-defineobjects}

Met de tag `<sling:defineObjects>` worden de volgende, regelmatig gebruikte scriptobjecten weergegeven waarnaar de ontwikkelaar kan verwijzen:

**slingRequest**

* Het voorwerp SlingHttpServletRequest, dat toegang tot de informatie van de HTTP- verzoekkopbal verleent - breidt standaardHttpServletRequest uit - en verleent toegang tot het splitsen-specifieke dingen zoals middel, weginfo, selecteur, enz.

**slingResponse**

* SlingHttpServletResponse-object, dat toegang biedt voor de HTTP-reactie die door de server wordt gemaakt. Dit is momenteel het zelfde als HttpServletResponse waarvan het zich uitbreidt.**verzoek**
* Het standaard JSP verzoekvoorwerp dat een zuivere HttpServletRequest is.**response**
* Het standaard JSP-responsobject dat een zuivere HttpServletResponse is.

**resourceResolver**

* Het huidige ResourceResolver-object. Dit is hetzelfde als slingRequest.getResourceResolver()

.**sling**

* Een SlingScriptHelper-object, dat gebruiksvriendelijke methoden voor scripts bevat, voornamelijk sling.include(&#39;/some/other/resource&#39;) voor het opnemen van de reacties van andere bronnen in deze reactie (bijvoorbeeld het inbedden kopbal (de fragmenten van html) en sling.getService (foo.bar.Service.class) om de diensten OSGi terug te winnen beschikbaar in Sling (de aantekening van de Klasse afhankelijk van scripting taal).

**resource**

* het huidige Resource-object dat moet worden afgehandeld, afhankelijk van de URL van de aanvraag. Dit is hetzelfde als slingRequest.getResource().

**currentNode**

* Als de huidige bron naar een JCR-knooppunt verwijst (wat normaal gesproken het geval is bij Sling), geeft dit directe toegang tot het Node-object. Anders is dit object niet gedefinieerd.

**log**

* Verstrekt een Logger SLF4J voor het registreren aan het het Verdraaien logboeksysteem van binnen manuscripten, b.v. log.info(&quot;Mijn script uitvoeren&quot;).

* Deze heeft de volgende kenmerken:

**requestName**

**responseName**

**nodeName**

l **ogName resourceResolverName**

**slingName**

**Voorbeeld:**

```xml
<%@page session="false" %><%
%><%@page import="com.day.cq.wcm.foundation.forms.ValidationHelper"%><%
%><%@taglib prefix="sling" uri="https://sling.apache.org/taglibs/sling/1.0" %><%
%><sling:defineObjects/>
```

## JSTL-tagbibliotheek {#jstl-tag-library}

De [JavaServer Pages Standard Tag Library](https://www.oracle.com/technetwork/java/index-jsp-135995.html) bevat veel nuttige en standaardtags. De getallen voor de kern, opmaak en functies worden gedefinieerd door de `/libs/foundation/global.jsp`, zoals in het volgende fragment wordt getoond.

### Extraheren van /libs/foundation/global.jsp {#extract-of-libs-foundation-global-jsp}

```xml
<%@taglib prefix="c" uri="https://java.sun.com/jsp/jstl/core" %>
<%@taglib prefix="fmt" uri="https://java.sun.com/jsp/jstl/fmt" %>
<%@taglib prefix="fn" uri="https://java.sun.com/jsp/jstl/functions" %>
```

Nadat u het `/libs/foundation/global.jsp`-bestand hebt ge??mporteerd zoals eerder is beschreven, kunt u de voorvoegsels `c`, `fmt` en `fn` gebruiken om toegang te krijgen tot deze labels. De offici??le documentatie van JSTL is beschikbaar op [De Java EE 5-zelfstudie - JavaServer Pages Standard Tag Library](https://docs.oracle.com/javaee/5/tutorial/doc/bnakc.html).
