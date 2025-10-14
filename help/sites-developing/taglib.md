---
title: Tagbibliotheken
description: Met de tagbibliotheken Granite, CQ en Sling hebt u toegang tot specifieke functies voor gebruik in het JSP-script van uw sjablonen en componenten
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: platform
content-type: reference
exl-id: 50e608d5-951f-4a3f-bed4-9e92ff5d7bd4
solution: Experience Manager, Experience Manager Sites
feature: Developing,Tagging
role: Developer
source-git-commit: 305227eff3c0d6414a5ae74bcf3a74309dccdd13
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

Globaal verklaart ook de [&#x200B; Verschuivende bibliotheek &#x200B;](/help/sites-developing/taglib.md#sling-tag-library).

```xml
<%@taglib prefix="sling" uri="https://sling.apache.org/taglibs/sling" %>
```

### &lt;ui:includeClientLib> {#ui-includeclientlib}

De tag `<ui:includeClientLib>` bevat een AEM HTML-clientbibliotheek, die js, css of een themabibliotheek kan zijn. Voor meerdere inclusies van verschillende typen, bijvoorbeeld js en css, moet deze tag meerdere keren worden gebruikt in de jsp. Deze tag is een handige omslag rond de service-interface van ` [com.adobe.granite.ui.clientlibs.HtmlLibraryManager](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/adobe/granite/ui/clientlibs/HtmlLibraryManager.html)` .

Deze heeft de volgende kenmerken:

**categorieën** - een lijst van komma-gescheiden categorieën van de cliëntbibliotheek. Dit omvat alle JavaScript- en CSS-bibliotheken voor de opgegeven categorieën. De themanaam wordt uit de aanvraag geëxtraheerd.

Equivalent aan: `com.adobe.granite.ui.clientlibs.HtmlLibraryManager#writeIncludes`

**thema** - een lijst van komma-gescheiden categorieën van de cliëntbibliotheek. Dit omvat alle themabibliotheken (zowel CSS als JS) voor de opgegeven categorieën. De themanaam wordt uit de aanvraag geëxtraheerd.

Equivalent aan: `com.adobe.granite.ui.clientlibs.HtmlLibraryManager#writeThemeInclude`

**js** - een lijst van komma-gescheiden categorieën van de cliëntbibliotheek. Dit geldt ook voor alle JavaScript-bibliotheken voor de opgegeven categorieën.

Equivalent aan: `com.adobe.granite.ui.clientlibs.HtmlLibraryManager#writeJsInclude`

**css** - een lijst van komma-gescheiden categorieën van de cliëntbibliotheek. Dit omvat alle CSS-bibliotheken voor de opgegeven categorieën.

Equivalent aan: `com.adobe.granite.ui.clientlibs.HtmlLibraryManager#writeCssInclude`

**thema** - een vlag die van slechts de thema&#39;s of niet-thema bibliotheken wijst zou moeten worden omvat. Als deze waarde wordt weggelaten, worden beide sets opgenomen. Alleen van toepassing op zuivere JS- of CSS-include-bestanden (niet voor categorieën of thema-include-bestanden).

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

De CQ-tagbibliotheek bevat nuttige functies.

Als u de CQ-tagbibliotheek in uw script wilt gebruiken, moet het script beginnen met de volgende code:

```xml
<%@taglib prefix="cq" uri="https://www.day.com/taglibs/cq/1.0" %>
```

>[!NOTE]
>
>Wanneer het `/libs/foundation/global.jsp` -bestand in het script wordt opgenomen, wordt de taglib automatisch gedeclareerd.

Wanneer u het Jsp manuscript van een AEM component ontwikkelt, wordt het geadviseerd om volgende code bij de bovenkant van het manuscript te omvatten:

```xml
<%@include file="/libs/foundation/global.jsp"%>
```

De tags sling, CQ en jstl worden gedeclareerd en de regelmatig gebruikte scriptobjecten die door de tag [`<cq:defineObjects />`](#amp-lt-cq-defineobjects) worden gedefinieerd, worden getoond. Hierdoor wordt de jsp-code van uw component verkort en vereenvoudigd.

### &lt;cq:text> {#cq-text}

De tag `<cq:text>` is een gebruikstag die de componenttekst in een JSP uitvoert.

Het heeft de volgende optionele kenmerken:

**bezit** - Naam van het bezit aan gebruik. De naam is relatief ten opzichte van de huidige bron.

**waarde** - Waarde voor output te gebruiken. Als dit kenmerk aanwezig is, wordt het gebruik van het eigenschapkenmerk overschreven.

**oldValue** - Waarde om voor diff output te gebruiken. Als dit kenmerk aanwezig is, wordt het gebruik van het eigenschapkenmerk overschreven.

**escapeXml** - bepaalt of de karakters &lt;, >, &amp;, &quot; en &quot; in het resulterende koord in hun overeenkomstige codes van de karakterentiteit zouden moeten worden omgezet. De standaardwaarde is false. De escaping wordt toegepast na de optionele opmaak.

**formaat** - Facultatieve java.text.Format aan gebruik voor het formatteren van de tekst.

**noDiff** - onderdrukt de berekening van een diff output, zelfs als diff informatie aanwezig is.

**tagClass** - CSS klassennaam van een element dat een niet lege output zal omringen. Als dit leeg is, wordt geen element toegevoegd.

**tagName** - Naam van het element dat een niet-lege output zal omringen. De standaardwaarde is DIV.

**placeholder** - Standaardwaarde voor ongeldige of lege tekst op geef wijze uit, namelijk placeholder. De standaardcontrole wordt uitgevoerd na de optionele opmaak en escape, d.w.z. dat deze ongewijzigd naar de uitvoer wordt geschreven. De standaardwaarde is:

`<div><span class="cq-text-placeholder">&para;</span></div>`

**gebrek** - Standaardwaarde om voor ongeldige of lege tekst te gebruiken. De standaardcontrole wordt uitgevoerd na de optionele opmaak en escape, dat wil zeggen dat deze ongewijzigd naar de uitvoer wordt geschreven.

Hier volgen enkele voorbeelden van het gebruik van de tag `<cq:text>` in een JSP:

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

De tag `<cq:setContentBundle>` maakt een i18n-lokalisatiecontext en slaat deze op in de configuratievariabele `javax.servlet.jsp.jstl.fmt.localizationContext` .

Deze heeft de volgende kenmerken:

**taal** - de taal van de scène waarvoor om de middelbundel terug te winnen.

**bron** - de bron waar de scène zou moeten worden genomen van. Deze kan op een van de volgende waarden worden ingesteld:

* **statisch** - de scène wordt genomen van het `language` attribuut als beschikbaar, anders van de server standaardscène.

* **pagina** - de scène wordt genomen van de taal van de huidige pagina of het middel als beschikbaar, anders van het `language` attribuut als beschikbaar, anders van de server standaardscène.

* **verzoek** - de scène wordt genomen van de verzoekscène ( `request.getLocale()`).

* **auto** - de scène wordt genomen van het `language` attribuut als beschikbaar, anders van de taal van de huidige pagina of het middel als beschikbaar, anders van het verzoek.

Als het kenmerk `source` niet is ingesteld:

* Als het kenmerk `language` is ingesteld, wordt voor het kenmerk `source` standaard &quot;`static` &quot; ingesteld.

* Als het kenmerk `language` niet is ingesteld, wordt het kenmerk `source` standaard ingesteld op `auto` .

De &quot;inhoudsbundel&quot; kan worden gebruikt door standaard JSTL `<fmt:message>` -tags. De zoekopdracht van berichten via sleutels is tweeledig:

1. Ten eerste worden de JCR-eigenschappen van de onderliggende resource die wordt gerenderd, doorzocht op vertalingen. Hiermee kunt u een dialoogvenster met eenvoudige componenten definiëren waarin u deze waarden kunt bewerken.
1. Als het knooppunt geen eigenschap bevat die exact dezelfde naam heeft als de sleutel, wordt als fallback een resourcepakket geladen uit de sling request ( `SlingHttpServletRequest.getResourceBundle(Locale)` ). De taal of landinstelling voor deze bundel wordt gedefinieerd door de taal- en bronkenmerken van de tag `<cq:setContentBundle>` .

De tag `<cq:setContentBundle>` kan als volgt worden gebruikt in een JPEG-bestand.

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

**weg**

* De weg aan het middelvoorwerp dat in de huidige verzoekverwerking moet worden omvat. Als dit pad relatief is, wordt het toegevoegd aan het pad van de huidige bron waarvan het script de opgegeven bron bevat. Of weg en resourceType, of manuscript moet worden gespecificeerd.

**resourceType**

* The resource type of the resource to be included. Als het middeltype wordt geplaatst, moet de weg de nauwkeurige weg aan een middelvoorwerp zijn: in dit geval, wordt het toevoegen van parameters, selecteurs, en uitbreidingen aan de weg niet gesteund.
* Als de bron die moet worden opgenomen, wordt opgegeven met het padkenmerk dat niet kan worden omgezet naar een bron, maakt de tag mogelijk een synthetisch bronobject uit het pad en dit resourcetype.
* Of weg en resourceType, of manuscript moet worden gespecificeerd.

**manuscript**

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

Moet u `<%@ include file="myScript.jsp" %>` of `<cq:include script="myScript.jsp" %>` gebruiken om een script op te nemen?

* De instructie `<%@ include file="myScript.jsp" %>` informeert de JSP-compiler om een volledig bestand op te nemen in het huidige bestand. Het is alsof de inhoud van het ingesloten bestand rechtstreeks in het oorspronkelijke bestand is geplakt.
* Met de tag `<cq:include script="myScript.jsp">` wordt het bestand bij uitvoering opgenomen.

Moet u `<cq:include>` of `<sling:include>` gebruiken?

* Wanneer het ontwikkelen van AEM componenten, adviseert de Adobe dat u `<cq:include>` gebruikt.
* Met `<cq:include>` kunt u scriptbestanden direct op naam opnemen wanneer u het scriptkenmerk gebruikt. Dit neemt component en middeltypeovererving in overweging, en is vaak eenvoudiger dan strikte naleving van het manuscriptresolutie van het Sling gebruikend selecteurs en uitbreidingen.

### &lt;cq:includeClientLib> {#cq-includeclientlib}

>[!CAUTION]
>
>`<cq:includeClientLib>` Vervangen vanaf AEM 5.6. [`<ui:includeClientLib>`](/help/sites-developing/taglib.md#ui-includeclientlib) moet worden gebruikt.

De tag `<cq:includeClientLib>` bevat een AEM HTML-clientbibliotheek, die kan bestaan uit een JS, een css of een themabibliotheek. Voor meerdere inclusies van verschillende typen, bijvoorbeeld js en css, moet deze tag meerdere keren worden gebruikt in de jsp. Deze tag is een handige omslag rond de service-interface van `com.day.cq.widget.HtmlLibraryManager` .

Deze heeft de volgende kenmerken:

**categorieën** - een lijst van komma-gescheiden categorieën van de cliëntbibliotheek. Dit omvat alle JavaScript- en CSS-bibliotheken voor de opgegeven categorieën. De themanaam wordt uit de aanvraag geëxtraheerd.

Equivalent aan: `com.day.cq.widget.HtmlLibraryManager#writeIncludes`

**thema** - een lijst van komma-gescheiden categorieën van de cliëntbibliotheek. Dit omvat alle themabibliotheken (zowel CSS als JS) voor de opgegeven categorieën. De themanaam wordt uit de aanvraag geëxtraheerd.

Equivalent aan: `com.day.cq.widget.HtmlLibraryManager#` writeThemeInclude

**js** - een lijst van komma-gescheiden categorieën van de cliëntbibliotheek. Dit geldt ook voor alle JavaScript-bibliotheken voor de opgegeven categorieën.

Equivalent aan: `com.day.cq.widget.HtmlLibraryManager#writeJsInclude`

**css** - een lijst van komma-gescheiden categorieën van de cliëntbibliotheek. Dit omvat alle CSS-bibliotheken voor de opgegeven categorieën.

Equivalent aan: `com.day.cq.widget.HtmlLibraryManager#writeCssInclude`

**thema** - een vlag die van slechts de thema&#39;s of niet-thema bibliotheken wijst zou moeten worden omvat. Als deze waarde wordt weggelaten, worden beide sets opgenomen. Alleen van toepassing op zuivere JS- of CSS-include-bestanden (niet voor categorieën of thema-include-bestanden).

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

### &lt;cq:defineObjects> {#cq-defineobjects}

De tag `<cq:defineObjects>` stelt de volgende, regelmatig gebruikte scriptobjecten beschikbaar waarnaar de ontwikkelaar kan verwijzen. De tag stelt ook de objecten beschikbaar die door de tag [`<sling:defineObjects>`](#amp-lt-sling-defineobjects) worden gedefinieerd.

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

**designer**

* het ontwerperobject dat wordt gebruikt voor toegang tot ontwerpinformatie (com.day.cq.wcm.api.designer.Designer interface).

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
>Wanneer het `/libs/foundation/global.jsp` -bestand in het script wordt opgenomen, wordt de tag `<cq:defineObjects />` automatisch opgenomen.

### &lt;cq:requestURL> {#cq-requesturl}

De tag `<cq:requestURL>` schrijft de huidige aanvraag-URL naar de JspWriter. De twee tags [`<cq:addParam>`](#amp-lt-cq-addparam) en [`<cq:removeParam>`](#amp-lt-cq-removeparam) en kunnen binnen de hoofdtekst van deze tag worden gebruikt om de huidige verzoek-URL te wijzigen voordat deze wordt geschreven.

Hiermee kunt u koppelingen met verschillende parameters maken naar de huidige pagina. Zo kunt u bijvoorbeeld de aanvraag transformeren:

`mypage.html?mode=view&query=something` in `mypage.html?query=something` .

Het gebruik van `addParam` of `removeParam` wijzigt alleen de instantie van de opgegeven parameter, dit heeft geen invloed op alle andere parameters.

`<cq:requestURL>` heeft geen kenmerk.

Voorbeelden:

```xml
<a href="<cq:requestURL><cq:removeParam name="language"/></cq:requestURL>">remove filter</a>
```

```xml
<a title="filter results" href="<cq:requestURL><cq:addParam name="language" value="${bucket.value}"/></cq:requestURL>">${label} (${bucket.count})</a>
```

### &lt;cq:addParam> {#cq-addparam}

De tag `<cq:addParam>` voegt een aanvraagparameter met de opgegeven naam en waarde toe aan de omsluitende tag [`<cq:requestURL>`](#amp-lt-cq-requesturl) .

Deze heeft de volgende kenmerken:

**naam**

* naam van de parameter die moet worden toegevoegd

**waarde**

* waarde van de toe te voegen parameter

**Voorbeeld:**

```xml
<a title="filter results" href="<cq:requestURL><cq:addParam name="language" value="${bucket.value}"/></cq:requestURL>">${label} (${bucket.count})</a>
```

### &lt;cq:removeParam> {#cq-removeparam}

De tag `<cq:removeParam>` verwijdert een aanvraagparameter met de opgegeven naam en waarde uit de omsluitende tag [`<cq:requestURL>`](#amp-lt-cq-requesturl) . Wanneer geen waarde is opgegeven, worden alle parameters met de opgegeven naam verwijderd.

Deze heeft de volgende kenmerken:

**naam**

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
>Wanneer het `/libs/foundation/global.jsp` -bestand in het script wordt opgenomen, wordt de taglib van de sling automatisch gedeclareerd.

### &lt;sling:include> {#sling-include}

De tag `<sling:include>` bevat een bron op de huidige pagina.

Deze heeft de volgende kenmerken:

**flush**

* Een Booleaanse waarde die definieert of de uitvoer moet worden verwijderd voordat het doel wordt opgenomen.

**middel**

* Het bronobject dat moet worden opgenomen in de huidige aanvraagverwerking. resource of pad moet worden opgegeven. Als beide zijn opgegeven, heeft de bron voorrang.

**weg**

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
>De resolutie van de bron en het script die in de tag `<sling:include>` zijn opgenomen, is gelijk aan die voor een normale URL-slingerresolutie. Standaard worden de kiezers, de extensie enzovoort uit de huidige aanvraag ook gebruikt voor het opgenomen script. Ze kunnen worden gewijzigd via de tagkenmerken: met `replaceSelectors="foo.bar"` kunt u bijvoorbeeld de kiezers overschrijven.

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

De tag `<sling:defineObjects>` stelt de volgende, regelmatig gebruikte scriptobjecten beschikbaar waarnaar de ontwikkelaar kan verwijzen:

**slingRequest**

* Het voorwerp SlingHttpServletRequest, dat toegang tot de informatie van de HTTP- verzoekkopbal verleent - breidt standaardHttpServletRequest uit - en verleent toegang tot het splitsen-specifieke dingen zoals middel, weginfo, en selecteur.

**slingResponse**

* SlingHttpServletResponse-object, dat toegang biedt voor de HTTP-reactie die door de server wordt gemaakt. Dit is het zelfde als HttpServletResponse waarvan het zich uitbreidt.**verzoek**
* Het standaard JSP verzoekvoorwerp dat een zuivere HttpServletRequest is.**reactie**
* Het standaard JSP-responsobject dat een zuivere HttpServletResponse is.

**resourceResolver**

* Het huidige ResourceResolver-object. Dit is hetzelfde als slingRequest.getResourceResolver()

.**sling**

* Een SlingScriptHelper-object, dat gebruiksvriendelijke methoden voor scripts bevat, voornamelijk sling.include(&#39;/some/other/resource&#39;) voor het opnemen van de reacties van andere bronnen in deze reactie (bijvoorbeeld HTML-fragmenten voor de insluiting van header) en sling.getService(foo.bar.Service.class) voor het ophalen van OSGi-services die beschikbaar zijn in Sling (Class-notatie afhankelijk van scripttaal).

**middel**

* het huidige Resource-object dat moet worden afgehandeld, afhankelijk van de URL van de aanvraag. Dit is hetzelfde als slingRequest.getResource().

**currentNode**

* Als de huidige bron naar een JCR-knooppunt verwijst (wat normaal gesproken het geval is bij Sling), geeft dit directe toegang tot het Node-object. Anders is dit object niet gedefinieerd.

**logboek**

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

De [&#x200B; Bibliotheek van de Markering van de Pagina&#39;s JavaServer Standaard &#x200B;](https://www.oracle.com/java/technologies/java-server-tag-library.html) bevat vele nuttige en standaardmarkeringen. De kern-, opmaak- en functietags worden gedefinieerd door de `/libs/foundation/global.jsp` , zoals in het volgende fragment wordt getoond.

### Extraheren van /libs/foundation/global.jsp {#extract-of-libs-foundation-global-jsp}

```xml
<%@taglib prefix="c" uri="https://java.sun.com/jsp/jstl/core" %>
<%@taglib prefix="fmt" uri="https://java.sun.com/jsp/jstl/fmt" %>
<%@taglib prefix="fn" uri="https://java.sun.com/jsp/jstl/functions" %>
```

Nadat u het `/libs/foundation/global.jsp` -bestand hebt geïmporteerd zoals eerder is beschreven, kunt u de voorvoegsels `c` , `fmt` en `fn` gebruiken om toegang te krijgen tot deze tags. De officiële documentatie van JSTL is beschikbaar bij [&#x200B; het EE 5 Leerprogramma Java™ - de Bibliotheek van de Markering van de Pagina&#39;s JavaServer Standaard &#x200B;](https://docs.oracle.com/javaee/5/tutorial/doc/bnakc.html).
