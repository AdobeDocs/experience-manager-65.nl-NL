---
title: Gebeurtenistracking uitbreiden
seo-title: Gebeurtenistracking uitbreiden
description: Met AEM Analytics kunt u gebruikersinteractie op uw website volgen
seo-description: Met AEM Analytics kunt u gebruikersinteractie op uw website volgen
uuid: 722798ac-4043-4918-a6df-9eda2c85020b
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: extending-aem
content-type: reference
discoiquuid: e0372f4a-fe7b-4526-8391-5bb345b51d70
translation-type: tm+mt
source-git-commit: 5128a08d4db21cda821de0698b0ac63ceed24379

---


# Gebeurtenistracking uitbreiden{#extending-event-tracking}

Met AEM Analytics kunt u gebruikersinteractie op uw website volgen. Als ontwikkelaar moet u mogelijk:

* Houd bij hoe bezoekers uw componenten gebruiken. Dit kan met gebeurtenissen van de [Douane worden gedaan.](#custom-events)
* [De waarden van de toegang in ContextHub](/help/sites-developing/extending-analytics.md#accessing-values-in-the-contexthub).
* [Voeg recordcallbacks](#adding-record-callbacks)toe.

>[!NOTE]
>
>Deze informatie is in principe algemeen, maar gebruikt [Adobe Analytics](/help/sites-administering/adobeanalytics.md) voor specifieke voorbeelden.
>
>Zie [Componenten](/help/sites-developing/components.md)ontwikkelen voor algemene informatie over het ontwikkelen van componenten en dialoogvensters.

## Aangepaste gebeurtenissen {#custom-events}

Aangepaste gebeurtenissen volgen alles wat afhankelijk is van de beschikbaarheid van een specifieke component op de pagina. Dit omvat ook gebeurtenissen die sjabloonspecifiek zijn, aangezien de pagina-component als een andere component wordt behandeld.

### Aangepaste gebeurtenissen bijhouden bij laden van pagina {#tracking-custom-events-on-page-load}

Dit kan worden gedaan gebruikend pseudo-attribuut `data-tracking` (het oudere verslagattribuut wordt nog gesteund voor achterwaartse verenigbaarheid). U kunt dit toevoegen aan elke HTML-tag.

De syntaxis voor `data-tracking` is

* `data-tracking="{'event': ['eventName'], 'values': {'key': 'value', 'nextKey': 'nextValue'}, componentPath: 'myapp/component/mycomponent'}"`

U kunt elk aantal sleutel-waardeparen als tweede parameter overgaan, die nuttige lading wordt genoemd.

Een voorbeeld zou als kunnen kijken:

```xml
<span data-tracking="{event:'blogEntryView',
                                values:{
                                   'blogEntryContentType': 'blog',
                                   'blogEntryUniqueID': '<%= xssAPI.encodeForJSString(entry.getId()) %>',
                                   'blogEntryTitle': '<%= xssAPI.encodeForJSString(entry.getTitle()) %>',
                                   'blogEntryAuthor':'<%= xssAPI.encodeForJSString(entry.getAuthor()) %>',
                                   'blogEntryPageLanguage':'<%= currentPage.getLanguage(true) %>'
                                },
                                componentPath:'myapp/component/mycomponent'}">
</span>
```

Bij het laden van de pagina worden alle `data-tracking` kenmerken verzameld en toegevoegd aan de gebeurtenisopslag van de ContextHub, waar ze kunnen worden toegewezen aan Adobe Analytics-gebeurtenissen. Gebeurtenissen die niet worden toegewezen, worden niet bijgehouden door Adobe Analytics. Zie [Verbinding maken met Adobe Analytics](/help/sites-administering/adobeanalytics.md) voor meer informatie over toewijzingsgebeurtenissen.

### Aangepaste gebeurtenissen bijhouden na laden van pagina {#tracking-custom-events-after-page-load}

Als u gebeurtenissen wilt bijhouden die plaatsvinden nadat een pagina is geladen (zoals gebruikersinteracties), gebruikt u de `CQ_Analytics.record` JavaScript-functie:

* `CQ_Analytics.record({event: 'eventName', values: { valueName: 'VALUE' }, collect: false, options: { obj: this, defaultLinkType: 'X' }, componentPath: '<%=resource.getResourceType()%>'})`

Wanneer

* `events` is een tekenreeks of een tekenreeks-array (voor meerdere gebeurtenissen).

* `values` bevat alle waarden die moeten worden bijgehouden
* `collect` is optioneel en retourneert een array met de gebeurtenis en het gegevensobject.
* `options` is optioneel en bevat opties voor het bijhouden van koppelingen, zoals HTML-element `obj` en ` [defaultLinkType](https://microsite.omniture.com/t2/help/en_US/sc/implement/index.html#linkType)`.

* `componentPath` is een noodzakelijk attribuut en het wordt geadviseerd om het te plaatsen aan `<%=resource.getResourceType()%>`

Met de volgende definitie zorgt een gebruiker die op de koppeling **Springen naar bovenkant** klikt er bijvoorbeeld voor dat de twee gebeurtenissen `jumptop` en `headlineclick`, worden geactiveerd:

```xml
<h1 data-tracking="{event: 'headline', values: {level:'1'}, componentPath: '<%=resource.getResourceType()%>'}">
  My Headline <a href="#" onclick="CQ_Analytics.record({event: ['jumptop','headlineclick'],  values: {level:'1'}, componentPath: '<%=resource.getResourceType()%>'})">Jump to top</a>
</h1>
```

## Toegang tot Waarden in ContextHub {#accessing-values-in-the-contexthub}

De JavaScript-API van ContextHub heeft een `getStore(name)` functie die de opgegeven opslag retourneert, indien beschikbaar. De opslag heeft een `getItem(key)` functie die de waarde van de gespecificeerde sleutel, indien beschikbaar terugkeert. Met behulp van de `getKeys()` functie is het mogelijk een array met gedefinieerde sleutels voor de specifieke winkel op te halen.

U kunt op de hoogte worden gesteld van waardewijzigingen in een winkel door een functie te binden met de `ContextHub.getStore(name).eventing.on(ContextHub.Constants.EVENT_STORE_UPDATED, handler, selector, triggerForPastEvents)` functie.

De beste manier om van aanvankelijke beschikbaarheid van ContextHub op de hoogte te worden gebracht is de `ContextHub.eventing.on(ContextHub.Constants.EVENT_ALL_STORES_READY, handler, selector, triggerForPastEvents);` functie te gebruiken.

**Aanvullende gebeurtenissen voor ContextHub:**

Alle winkels klaar:

`ContextHub.eventing.on(ContextHub.Constants.EVENT_ALL_STORES_READY, handler, selector, triggerForPastEvents);`

Opslagspecifiek:

`ContextHub.getStore(store).eventing.on(ContextHub.Constants.EVENT_STORE_READY, handler, selector, triggerForPastEvents)`

>[!NOTE]
>
>Zie ook de volledige [ContextHub API-naslaggids](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/contexthub-api.html#ContextHubJavascriptAPIReference)

## Recordcallbacks toevoegen {#adding-record-callbacks}

Voor en na callbacks worden geregistreerd gebruikend de functies `CQ_Analytics.registerBeforeCallback(callback,rank)` en `CQ_Analytics.registerAfterCallback(callback,rank)`.

Beide functies nemen een functie als eerste argument en een rang als tweede argument, die de orde dicteert dat callbacks worden uitgevoerd.

Als uw callback vals terugkeert, zullen de callbacks die in de uitvoeringsketen volgen niet worden uitgevoerd.
