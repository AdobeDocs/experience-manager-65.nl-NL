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
workflow-type: tm+mt
source-wordcount: '501'
ht-degree: 0%

---


# GebeurtenissenreeksspatiĆ«ring uitbreiden{#extending-event-tracking}

Met AEM Analytics kunt u gebruikersinteractie op uw website volgen. Als ontwikkelaar moet u mogelijk:

* Houd bij hoe bezoekers uw componenten gebruiken. Dit kan worden gedaan met [Aangepaste gebeurtenissen.](#custom-events)
* [De waarden van de toegang in ContextHub](/help/sites-developing/extending-analytics.md#accessing-values-in-the-contexthub).
* [Voeg recordcallbacks](#adding-record-callbacks) toe.

>[!NOTE]
>
>Deze informatie is eigenlijk algemeen, maar het gebruikt [Adobe Analytics](/help/sites-administering/adobeanalytics.md) voor specifieke voorbeelden.
>
>Zie [Componenten ontwikkelen](/help/sites-developing/components.md) voor algemene informatie over het ontwikkelen van componenten en dialoogvensters.

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

Bij paginading, zullen alle `data-tracking` attributen worden verzameld en aan de gebeurtenisopslag van ContextHub toegevoegd, waar zij aan de gebeurtenissen van Adobe Analytics kunnen worden in kaart gebracht. Gebeurtenissen die niet zijn toegewezen, worden niet bijgehouden door Adobe Analytics. Zie [Verbinding maken met Adobe Analytics](/help/sites-administering/adobeanalytics.md) voor meer informatie over toewijzingsgebeurtenissen.

### Aangepaste gebeurtenissen bijhouden na laden van pagina {#tracking-custom-events-after-page-load}

Als u gebeurtenissen wilt bijhouden die plaatsvinden nadat een pagina is geladen (zoals gebruikersinteracties), gebruikt u de JavaScript-functie `CQ_Analytics.record`:

* `CQ_Analytics.record({event: 'eventName', values: { valueName: 'VALUE' }, collect: false, options: { obj: this, defaultLinkType: 'X' }, componentPath: '<%=resource.getResourceType()%>'})`

Wanneer

* `events` is een tekenreeks of een tekenreeks-array (voor meerdere gebeurtenissen).

* `values` bevat alle waarden die moeten worden bijgehouden
* `collect` is optioneel en retourneert een array met de gebeurtenis en het gegevensobject.
* `options` is optioneel en bevat opties voor het bijhouden van koppelingen, zoals HTML-element  `obj` en  ` [defaultLinkType](https://microsite.omniture.com/t2/help/en_US/sc/implement/index.html#linkType)`.

* `componentPath` is een noodzakelijk attribuut en het wordt geadviseerd om het te plaatsen aan  `<%=resource.getResourceType()%>`

Als een gebruiker bijvoorbeeld op de koppeling **Springen naar boven** klikt, worden de twee gebeurtenissen `jumptop` en `headlineclick` geactiveerd:

```xml
<h1 data-tracking="{event: 'headline', values: {level:'1'}, componentPath: '<%=resource.getResourceType()%>'}">
  My Headline <a href="#" onclick="CQ_Analytics.record({event: ['jumptop','headlineclick'],  values: {level:'1'}, componentPath: '<%=resource.getResourceType()%>'})">Jump to top</a>
</h1>
```

## Toegang tot van Waarden in ContextHub {#accessing-values-in-the-contexthub}

De JavaScript-API van ContextHub heeft een functie `getStore(name)` die de opgegeven opslag retourneert, indien beschikbaar. De opslag heeft een functie `getItem(key)` die de waarde van de gespecificeerde sleutel, indien beschikbaar terugkeert. Met de functie `getKeys()` kunt u een array met gedefinieerde sleutels voor de specifieke opslag ophalen.

U kunt op de hoogte worden gesteld van waardeveranderingen op een opslag door een functie te binden gebruikend de `ContextHub.getStore(name).eventing.on(ContextHub.Constants.EVENT_STORE_UPDATED, handler, selector, triggerForPastEvents)` functie.

De beste manier om van aanvankelijke beschikbaarheid van ContextHub op de hoogte te worden gebracht is de `ContextHub.eventing.on(ContextHub.Constants.EVENT_ALL_STORES_READY, handler, selector, triggerForPastEvents);` functie te gebruiken.

**Aanvullende gebeurtenissen voor ContextHub:**

Alle winkels klaar:

`ContextHub.eventing.on(ContextHub.Constants.EVENT_ALL_STORES_READY, handler, selector, triggerForPastEvents);`

Opslagspecifiek:

`ContextHub.getStore(store).eventing.on(ContextHub.Constants.EVENT_STORE_READY, handler, selector, triggerForPastEvents)`

>[!NOTE]
>
>Zie ook de volledige [ContextHub API Reference](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/contexthub-api.html#ContextHubJavascriptAPIReference)

## Recordcallbacks {#adding-record-callbacks} toevoegen

Voor en na callbacks worden geregistreerd gebruikend de functies `CQ_Analytics.registerBeforeCallback(callback,rank)` en `CQ_Analytics.registerAfterCallback(callback,rank)`.

Beide functies nemen een functie als eerste argument en een rang als tweede argument, die de orde dicteert dat callbacks worden uitgevoerd.

Als uw callback vals terugkeert, zullen de callbacks die in de uitvoeringsketen volgen niet worden uitgevoerd.
