---
title: Tagbibliotheken
description: Met de tagbibliotheken Granite, CQ en Sling hebt u toegang tot specifieke functies voor gebruik in het JSP-script van uw sjablonen en componenten
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: platform
content-type: reference
exl-id: 50e608d5-951f-4a3f-bed4-9e92ff5d7bd4
solution: Experience Manager, Experience Manager Sites
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '2452'
ht-degree: 0%

---

# Tagbibliotheken{#tag-libraries}

Met de tagbibliotheken Granite, CQ en Sling hebt u toegang tot specifieke functies voor gebruik in het JSP-script van uw sjablonen en componenten.

## Graniet-tagbibliotheek {#granite-tag-library}

De tagbibliotheek Granite bevat nuttige functies.

Wanneer u het jsp manuscript van een component van Granite UI ontwikkelt, wordt het geadviseerd om volgende code bij de bovenkant van het manuscript te omvatten:

```xml
<%@include file="/libs/granite/ui/global.jsp"%>
```

De globale code declareert ook de [Verkoopbibliotheek](/help/sites-developing/taglib.md#sling-tag-library).

```xml
<%@taglib prefix="sling" uri="https://sling.apache.org/taglibs/sling" %>
```

### &lt;ui:includeClientLib> {#ui-includeclientlib}

De `<ui:includeClientLib>` tag Bevat een AEM HTML-clientbibliotheek, die een js, css of een themabibliotheek kan zijn. Voor meerdere inclusies van verschillende typen, bijvoorbeeld js en css, moet deze tag meerdere keren worden gebruikt in de jsp. Deze tag is handig om de ` [com.adobe.granite.ui.clientlibs.HtmlLibraryManager](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/adobe/granite/ui/clientlibs/HtmlLibraryManager.html)` service interface.

Deze heeft de volgende kenmerken:

**categorieën** - Een lijst met door komma&#39;s gescheiden clientbibliotheekcategorieën. Dit omvat alle JavaScript- en CSS-bibliotheken voor de opgegeven categorieën. De themanaam wordt uit de aanvraag geëxtraheerd.

Equivalent met: `com.adobe.granite.ui.clientlibs.HtmlLibraryManager#writeIncludes`

**thema** - Een lijst met door komma&#39;s gescheiden clientbibliotheekcategorieën. Dit omvat alle themabibliotheken (zowel CSS als JS) voor de opgegeven categorieën. De themanaam wordt uit de aanvraag geëxtraheerd.

Equivalent met: `com.adobe.granite.ui.clientlibs.HtmlLibraryManager#writeThemeInclude`

**js** - Een lijst met door komma&#39;s gescheiden clientbibliotheekcategorieën. Dit omvat alle JavaScript-bibliotheken voor de opgegeven categorieën.

Equivalent met: `com.adobe.granite.ui.clientlibs.HtmlLibraryManager#writeJsInclude`

**css** - Een lijst met door komma&#39;s gescheiden clientbibliotheekcategorieën. Dit omvat alle CSS-bibliotheken voor de opgegeven categorieën.

Equivalent met: `com.adobe.granite.ui.clientlibs.HtmlLibraryManager#writeCssInclude`

**thema** - Een vlag die alleen verwijst naar bibliotheken met of zonder thema. Als deze waarde wordt weggelaten, worden beide sets opgenomen. Alleen van toepassing op zuivere JS- of CSS-include-bestanden (niet voor categorieën of thema-include-bestanden).

De `<ui:includeClientLib>` tag kan als volgt worden gebruikt in een jsp :

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

De CQ-tagbibliotheek bevat nuttige functies.

Als u de CQ-tagbibliotheek in uw script wilt gebruiken, moet het script beginnen met de volgende code:

```xml
<%@taglib prefix="cq" uri="https://www.day.com/taglibs/cq/1.0" %>
```

>[!NOTE]
>
>Wanneer de `/libs/foundation/global.jsp` wordt opgenomen in het script, wordt de taglib automatisch gedeclareerd.

Wanneer u het Jsp manuscript van een AEM component ontwikkelt, wordt het geadviseerd om volgende code bij de bovenkant van het manuscript te omvatten:

```xml
<%@include file="/libs/foundation/global.jsp"%>
```

De tags sling, CQ en jstl worden gedeclareerd en de regelmatig gebruikte scriptobjecten die door de [`<cq:defineObjects />`](#amp-lt-cq-defineobjects) -tag. Hierdoor wordt de jsp-code van uw component verkort en vereenvoudigd.

### &lt;cq:text> {#cq-text}

De `<cq:text>` -tag is een gebruikstag die de tekst van een component in een JSP uitvoert.

Het heeft de volgende optionele kenmerken:

**eigenschap** - Naam van de te gebruiken eigenschap. De naam is relatief ten opzichte van de huidige bron.

**value** - Waarde die voor uitvoer moet worden gebruikt. Als dit kenmerk aanwezig is, wordt het gebruik van het eigenschapkenmerk overschreven.

**oldValue** - Waarde die moet worden gebruikt voor diff-uitvoer. Als dit kenmerk aanwezig is, wordt het gebruik van het eigenschapkenmerk overschreven.

**escapeXml** - Definieert of de tekens &lt;, >, &amp;, &#39; en &quot; in de resulterende tekenreeks moeten worden omgezet in de corresponderende tekeneenheidcodes. De standaardwaarde is false. De escaping wordt toegepast na de optionele opmaak.

**format** - Optionele java.text.Format voor het opmaken van de tekst.

**noDiff** - Onderdrukt de berekening van een diff output, zelfs als een diff info aanwezig is.

**tagClass** - CSS-klassenaam van een element dat een niet-lege uitvoer omsluit. Als dit leeg is, wordt geen element toegevoegd.

**tagName** - Naam van het element dat een niet-lege uitvoer omsluit. De standaardwaarde is DIV.

**plaatsaanduiding** - Standaardwaarde die moet worden gebruikt voor lege of null-tekst in de bewerkingsmodus, dat wil zeggen de tijdelijke aanduiding. De standaardcontrole wordt uitgevoerd na de optionele opmaak en escape, d.w.z. dat deze ongewijzigd naar de uitvoer wordt geschreven. De standaardwaarde is:

`<div><span class="cq-text-placeholder">&para;</span></div>`

**default** - Standaardwaarde voor lege of null-tekst. De standaardcontrole wordt uitgevoerd na de optionele opmaak en escape, dat wil zeggen dat deze ongewijzigd naar de uitvoer wordt geschreven.

In sommige voorbeelden wordt getoond hoe de `<cq:text>` -tag kan worden gebruikt in een JSP:

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

### &lt;cq:setContentBundle> {#cq-setcontentbundle}

De `<cq:setContentBundle>` -tag maakt een i18n-lokalisatiecontext en slaat deze op in de `javax.servlet.jsp.jstl.fmt.localizationContext` configuratievariabele.

Deze heeft de volgende kenmerken:

**taal** - De taal van de landinstelling waarvoor de resourcepakket moet worden opgehaald.

**bron** - De bron waaruit de landinstelling moet worden opgehaald. Deze kan op een van de volgende waarden worden ingesteld:

* **static** - de landinstelling wordt overgenomen van de `language` kenmerk indien beschikbaar, anders van de standaardlandinstelling van de server.

* **page** - de landinstelling wordt ontleend aan de taal van de huidige pagina of bron, indien beschikbaar, anders aan de `language` kenmerk indien beschikbaar, anders van de standaardlandinstelling van de server.

* **verzoek** - de landinstelling wordt overgenomen uit de landinstelling van het verzoek ( `request.getLocale()`).

* **auto** - de landinstelling wordt overgenomen van de `language` attribuut indien beschikbaar, anders van de taal van de huidige pagina of bron indien beschikbaar, anders van het verzoek.

Als de `source` attribute is not set:

* Als de `language` kenmerk is ingesteld, de `source` kenmerk is standaard ingesteld op &quot; `static`.

* Als de `language` het kenmerk is niet ingesteld, het `source` kenmerk standaard ingesteld op `auto`.

De &quot;inhoudsbundel&quot; kan worden gebruikt door standaard-JSTL `<fmt:message>` -tags. De zoekopdracht van berichten via sleutels is tweeledig:

1. Ten eerste worden de JCR-eigenschappen van de onderliggende resource die wordt gerenderd, doorzocht op vertalingen. Hiermee kunt u een dialoogvenster met eenvoudige componenten definiëren waarin u deze waarden kunt bewerken.
1. Als het knooppunt geen eigenschap bevat die exact dezelfde naam heeft als de sleutel, moet de fallback een resourcepakket laden vanuit de sling request ( `SlingHttpServletRequest.getResourceBundle(Locale)`). De taal of landinstelling voor deze bundel wordt gedefinieerd door de taal- en bronkenmerken van de `<cq:setContentBundle>` -tag.

De `<cq:setContentBundle>` tag kan als volgt worden gebruikt in een jsp.

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

De `<cq:include>` -tag bevat een bron op de huidige pagina.

Deze heeft de volgende kenmerken:

**flush**

* Een Booleaanse waarde die definieert of de uitvoer moet worden verwijderd voordat het doel wordt opgenomen.

**pad**

* De weg aan het middelvoorwerp dat in de huidige verzoekverwerking moet worden omvat. Als dit pad relatief is, wordt het toegevoegd aan het pad van de huidige bron waarvan het script de opgegeven bron bevat. Of weg en resourceType, of manuscript moet worden gespecificeerd.

**resourceType**

* The resource type of the resource to be included. Als het middeltype wordt geplaatst, moet de weg de nauwkeurige weg aan een middelvoorwerp zijn: in dit geval, wordt het toevoegen van parameters, selecteurs, en uitbreidingen aan de weg niet gesteund.
* Als de bron die moet worden opgenomen, wordt opgegeven met het padkenmerk dat niet kan worden omgezet naar een bron, maakt de tag mogelijk een synthetisch bronobject uit het pad en dit resourcetype.
* Of weg en resourceType, of manuscript moet worden gespecificeerd.

**script**

* Het JSP-script dat moet worden opgenomen. Of weg en resourceType, of manuscript moet worden gespecificeerd.

**ignoreComponentHierarchy**

* Een Booleaanse waarde die bepaalt of de componenthiërarchie moet worden genegeerd voor scriptresolutie. Indien waar (true), worden alleen de zoekpaden gebruikt.

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

Gebruik `<%@ include file="myScript.jsp" %>` of `<cq:include script="myScript.jsp" %>` om een script op te nemen?

* De `<%@ include file="myScript.jsp" %>` wordt de JSP-compiler geïnformeerd dat een volledig bestand in het huidige bestand moet worden opgenomen. Het is alsof de inhoud van het ingesloten bestand rechtstreeks in het oorspronkelijke bestand is geplakt.
* Met de `<cq:include script="myScript.jsp">` -tag, wordt het bestand bij uitvoering opgenomen.

Gebruik `<cq:include>` of `<sling:include>`?

* Wanneer het ontwikkelen van AEM componenten, adviseert de Adobe dat u gebruikt `<cq:include>`.
* `<cq:include>` Hiermee kunt u scriptbestanden direct op naam opnemen wanneer u het scriptkenmerk gebruikt. Dit neemt component en middeltypeovererving in overweging, en is vaak eenvoudiger dan strikte naleving van het manuscriptresolutie van het Sling gebruikend selecteurs en uitbreidingen.

### &lt;cq:includeClientLib> {#cq-includeclientlib}

>[!CAUTION]
>
>`<cq:includeClientLib>` Vervangen vanaf AEM 5.6. [`<ui:includeClientLib>`](/help/sites-developing/taglib.md#ui-includeclientlib) moet worden gebruikt.

De `<cq:includeClientLib>` tag Bevat een AEM HTML-clientbibliotheek, die een js, css of een themabibliotheek kan zijn. Voor meerdere inclusies van verschillende typen, bijvoorbeeld js en css, moet deze tag meerdere keren worden gebruikt in de jsp. Deze tag is handig om de `com.day.cq.widget.HtmlLibraryManager` service interface.

Deze heeft de volgende kenmerken:

**categorieën** - Een lijst met door komma&#39;s gescheiden clientbibliotheekcategorieën. Dit omvat alle JavaScript- en CSS-bibliotheken voor de opgegeven categorieën. De themanaam wordt uit de aanvraag geëxtraheerd.

Equivalent met: `com.day.cq.widget.HtmlLibraryManager#writeIncludes`

**thema** - Een lijst met door komma&#39;s gescheiden clientbibliotheekcategorieën. Dit omvat alle themabibliotheken (zowel CSS als JS) voor de opgegeven categorieën. De themanaam wordt uit de aanvraag geëxtraheerd.

Equivalent met: `com.day.cq.widget.HtmlLibraryManager#`writeThemeInclude

**js** - Een lijst met door komma&#39;s gescheiden clientbibliotheekcategorieën. Dit omvat alle JavaScript-bibliotheken voor de opgegeven categorieën.

Equivalent met: `com.day.cq.widget.HtmlLibraryManager#writeJsInclude`

**css** - Een lijst met door komma&#39;s gescheiden clientbibliotheekcategorieën. Dit omvat alle CSS-bibliotheken voor de opgegeven categorieën.

Equivalent met: `com.day.cq.widget.HtmlLibraryManager#writeCssInclude`

**thema** - Een vlag die alleen verwijst naar bibliotheken met of zonder thema. Als deze waarde wordt weggelaten, worden beide sets opgenomen. Alleen van toepassing op zuivere JS- of CSS-include-bestanden (niet voor categorieën of thema-include-bestanden).

De `<cq:includeClientLib>` tag kan als volgt worden gebruikt in een jsp :

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

### &lt;cq:defineObjects> {#cq-defineobjects}

De `<cq:defineObjects>` tag stelt de volgende, regelmatig gebruikte scriptobjecten beschikbaar waarnaar de ontwikkelaar kan verwijzen. Ook worden de objecten weergegeven die door de [`<sling:defineObjects>`](#amp-lt-sling-defineobjects) -tag.

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
>Wanneer de `/libs/foundation/global.jsp` het bestand is opgenomen in het script, `<cq:defineObjects />` -tag wordt automatisch opgenomen.

### &lt;cq:requestURL> {#cq-requesturl}

De `<cq:requestURL>` -tag schrijft de huidige aanvraag-URL naar de JspWriter. De twee tags [`<cq:addParam>`](#amp-lt-cq-addparam) en [`<cq:removeParam>`](#amp-lt-cq-removeparam) en kan binnen de tekst van deze tag worden gebruikt om de huidige aanvraag-URL te wijzigen voordat deze wordt geschreven.

Hiermee kunt u koppelingen met verschillende parameters maken naar de huidige pagina. Zo kunt u bijvoorbeeld de aanvraag transformeren:

`mypage.html?mode=view&query=something` in `mypage.html?query=something`.

Het gebruik van `addParam` of `removeParam` alleen de instantie van de opgegeven parameter wordt gewijzigd, blijven alle andere parameters ongewijzigd.

`<cq:requestURL>` heeft geen kenmerk.

Voorbeelden:

```xml
<a href="<cq:requestURL><cq:removeParam name="language"/></cq:requestURL>">remove filter</a>
```

```xml
<a title="filter results" href="<cq:requestURL><cq:addParam name="language" value="${bucket.value}"/></cq:requestURL>">${label} (${bucket.count})</a>
```

### &lt;cq:addParam> {#cq-addparam}

De `<cq:addParam>` tag voegt een aanvraagparameter met de opgegeven naam en waarde toe aan de omsluitende tag [`<cq:requestURL>`](#amp-lt-cq-requesturl) -tag.

Deze heeft de volgende kenmerken:

**name**

* naam van de parameter die moet worden toegevoegd

**value**

* waarde van de toe te voegen parameter

**Voorbeeld:**

```xml
<a title="filter results" href="<cq:requestURL><cq:addParam name="language" value="${bucket.value}"/></cq:requestURL>">${label} (${bucket.count})</a>
```

### &lt;cq:removeParam> {#cq-removeparam}

De `<cq:removeParam>` tag verwijdert een aanvraagparameter met de opgegeven naam en waarde uit de insluitende tag [`<cq:requestURL>`](#amp-lt-cq-requesturl) -tag. Wanneer geen waarde is opgegeven, worden alle parameters met de opgegeven naam verwijderd.

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
>Wanneer de `/libs/foundation/global.jsp` wordt opgenomen in het script, wordt de sling-taglib automatisch gedeclareerd.

### &lt;sling:include> {#sling-include}

De `<sling:include>` -tag bevat een bron op de huidige pagina.

Deze heeft de volgende kenmerken:

**flush**

* Een Booleaanse waarde die definieert of de uitvoer moet worden verwijderd voordat het doel wordt opgenomen.

**resource**

* Het bronobject dat moet worden opgenomen in de huidige aanvraagverwerking. resource of pad moet worden opgegeven. Als beide zijn opgegeven, heeft de bron voorrang.

**pad**

* De weg aan het middelvoorwerp dat in de huidige verzoekverwerking moet worden omvat. Als dit pad relatief is, wordt het toegevoegd aan het pad van de huidige bron waarvan het script de opgegeven bron bevat. resource of pad moet worden opgegeven. Als beide zijn opgegeven, heeft de bron voorrang.

**resourceType**

* The resource type of the resource to be included. Als het middeltype wordt geplaatst, moet de weg de nauwkeurige weg aan een middelvoorwerp zijn: in dit geval, wordt het toevoegen van parameters, selecteurs, en uitbreidingen aan de weg niet gesteund.
* Als de bron die moet worden opgenomen, wordt opgegeven met het padkenmerk dat niet kan worden omgezet naar een bron, maakt de tag mogelijk een synthetisch bronobject uit het pad en dit resourcetype.

**replaceSelectors**

* Bij het verzenden worden de kiezers vervangen door de waarde van dit kenmerk.

**addSelectors**

* Tijdens het verzenden wordt de waarde van dit kenmerk toegevoegd aan de kiezers.

**replaceSuffix**

* Bij het verzenden wordt het achtervoegsel vervangen door de waarde van dit kenmerk.

>[!NOTE]
>
>De resolutie van de resource en het script dat is opgenomen in de `<sling:include>` -tag is hetzelfde als bij een normale sling-URL-resolutie. Standaard worden de kiezers, de extensie enzovoort uit de huidige aanvraag ook gebruikt voor het opgenomen script. Ze kunnen worden gewijzigd via de tagkenmerken: bijvoorbeeld `replaceSelectors="foo.bar"` Hiermee kunt u de kiezers overschrijven.

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

### &lt;sling:defineObjects> {#sling-defineobjects}

De `<sling:defineObjects>` tag stelt de volgende, regelmatig gebruikte scriptobjecten beschikbaar waarnaar de ontwikkelaar kan verwijzen:

**slingRequest**

* Het voorwerp SlingHttpServletRequest, dat toegang tot de informatie van de HTTP- verzoekkopbal verleent - breidt standaardHttpServletRequest uit - en verleent toegang tot het splitsen-specifieke dingen zoals middel, weginfo, en selecteur.

**slingResponse**

* SlingHttpServletResponse-object, dat toegang biedt voor de HTTP-reactie die door de server wordt gemaakt. Dit is het zelfde als HttpServletResponse waarvan het zich uitbreidt.**verzoek**
* Het standaard JSP verzoekvoorwerp dat een zuivere HttpServletRequest is.**reactie**
* Het standaard JSP-responsobject dat een zuivere HttpServletResponse is.

**resourceResolver**

* Het huidige ResourceResolver-object. Dit is hetzelfde als slingRequest.getResourceResolver()

.**slingeren**

* Een SlingScriptHelper-object, dat gebruiksvriendelijke methoden voor scripts bevat, voornamelijk sling.include(&#39;/some/other/resource&#39;) voor het opnemen van de reacties van andere bronnen in deze reactie (bijvoorbeeld HTML-fragmenten voor de insluiting van header) en sling.getService(foo.bar.Service.class) voor het ophalen van OSGi-services die beschikbaar zijn in Sling (Class-notatie afhankelijk van scripttaal).

**resource**

* het huidige Resource-object dat moet worden afgehandeld, afhankelijk van de URL van de aanvraag. Dit is hetzelfde als slingRequest.getResource().

**currentNode**

* Als de huidige bron naar een JCR-knooppunt verwijst (wat normaal gesproken het geval is bij Sling), geeft dit directe toegang tot het Node-object. Anders is dit object niet gedefinieerd.

**log**

* Verstrekt een Logger van SLF4J voor het registreren aan het het Verspreiden logboeksysteem van binnen manuscripten, bijvoorbeeld, log.info (&quot;Uitvoerend mijn manuscript&quot;).

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

De [JavaServer Pages Standard-tagbibliotheek](https://www.oracle.com/java/technologies/java-server-tag-library.html) bevat veel nuttige en standaardcodes. De kern-, opmaak- en functietags worden gedefinieerd door de `/libs/foundation/global.jsp` zoals weergegeven in het volgende fragment.

### Extraheren van /libs/foundation/global.jsp {#extract-of-libs-foundation-global-jsp}

```xml
<%@taglib prefix="c" uri="https://java.sun.com/jsp/jstl/core" %>
<%@taglib prefix="fmt" uri="https://java.sun.com/jsp/jstl/fmt" %>
<%@taglib prefix="fn" uri="https://java.sun.com/jsp/jstl/functions" %>
```

Na het importeren van de `/libs/foundation/global.jsp` zoals eerder beschreven, kunt u de opdracht `c`, `fmt` en `fn` voorvoegsels voor toegang tot deze tags. De officiële documentatie van de JSTL is beschikbaar op [De Java™ EE 5-zelfstudie - JavaServer Pages Standard-tagbibliotheek](https://docs.oracle.com/javaee/5/tutorial/doc/bnakc.html).
