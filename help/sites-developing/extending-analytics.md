---
title: Gebeurtenistracking uitbreiden
description: Met AEM Analytics kunt u gebruikersinteractie op uw website volgen
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: extending-aem
content-type: reference
exl-id: a71d20e6-0321-4afb-95fe-6de8b7b37245
solution: Experience Manager, Experience Manager Sites
feature: Integration
role: Developer
source-git-commit: eae057caed533ef16bb541b4ad41b8edd7aaa1c7
workflow-type: tm+mt
source-wordcount: '477'
ht-degree: 0%

---

# Gebeurtenistracking uitbreiden{#extending-event-tracking}

Met AEM Analytics kunt u gebruikersinteractie op uw website volgen. Als ontwikkelaar moet u mogelijk:

* Houd bij hoe bezoekers uw componenten gebruiken. Dit kan met [ gebeurtenissen van de Douane worden gedaan.](#custom-events)
* [ waarden van de Toegang in ContextHub ](/help/sites-developing/extending-analytics.md#accessing-values-in-the-contexthub).
* [ voegt verslagcallbacks ](#adding-record-callbacks) toe.

>[!NOTE]
>
>Deze informatie is fundamenteel generisch, maar het gebruikt [ Adobe Analytics ](/help/sites-administering/adobeanalytics.md) voor specifieke voorbeelden.
>
>Voor algemene informatie bij het ontwikkelen van componenten en dialoogdozen, zie [ het Ontwikkelen Componenten ](/help/sites-developing/components.md).

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

Bij het laden van de pagina worden alle `data-tracking` -kenmerken verzameld en toegevoegd aan de gebeurteniswinkel van de ContextHub, waar ze kunnen worden toegewezen aan Adobe Analytics-gebeurtenissen. Gebeurtenissen die niet zijn toegewezen, worden niet bijgehouden door Adobe Analytics. Zie [ Verbindend met Adobe Analytics ](/help/sites-administering/adobeanalytics.md) voor meer details over kaartgebeurtenissen.

### Aangepaste gebeurtenissen bijhouden na laden van pagina {#tracking-custom-events-after-page-load}

Als u gebeurtenissen wilt bijhouden die plaatsvinden nadat een pagina is geladen (zoals gebruikersinteracties), gebruikt u de functie `CQ_Analytics.record` JavaScript:

* `CQ_Analytics.record({event: 'eventName', values: { valueName: 'VALUE' }, collect: false, options: { obj: this, defaultLinkType: 'X' }, componentPath: '<%=resource.getResourceType()%>'})`

Wanneer

* `events` is een tekenreeks of een tekenreeks-array (voor meerdere gebeurtenissen).

* `values` bevat alle waarden die moeten worden bijgehouden
* `collect` is optioneel en retourneert een array met de gebeurtenis en het gegevensobject.
* `options` is optioneel en bevat opties voor het bijhouden van koppelingen, zoals HTML-element `obj` en ` [defaultLinkType](https://microsite.omniture.com/t2/help/en_US/sc/implement/index.html#linkType)` .

* `componentPath` is een noodzakelijk kenmerk en het wordt aanbevolen dit in te stellen op `<%=resource.getResourceType()%>`

Bijvoorbeeld, met de volgende definitie, zal een gebruiker die **Jump aan top** verbinding klikt de twee gebeurtenissen, `jumptop` en `headlineclick` veroorzaken om worden in brand gestoken:

```xml
<h1 data-tracking="{event: 'headline', values: {level:'1'}, componentPath: '<%=resource.getResourceType()%>'}">
  My Headline <a href="#" onclick="CQ_Analytics.record({event: ['jumptop','headlineclick'],  values: {level:'1'}, componentPath: '<%=resource.getResourceType()%>'})">Jump to top</a>
</h1>
```

## Toegang tot Waarden in ContextHub {#accessing-values-in-the-contexthub}

De ContextHub JavaScript API heeft een `getStore(name)` functie die de gespecificeerde opslag, indien beschikbaar terugkeert. De opslag heeft een `getItem(key)` functie die de waarde van de gespecificeerde sleutel, indien beschikbaar terugkeert. Met de functie `getKeys()` kunt u een array met gedefinieerde sleutels voor de specifieke opslag ophalen.

U kunt op de hoogte worden gesteld van waardewijzigingen in een winkel door een functie te binden met de functie `ContextHub.getStore(name).eventing.on(ContextHub.Constants.EVENT_STORE_UPDATED, handler, selector, triggerForPastEvents)` .

De beste manier om van aanvankelijke beschikbaarheid van ContextHub op de hoogte te worden gebracht is de `ContextHub.eventing.on(ContextHub.Constants.EVENT_ALL_STORES_READY, handler, selector, triggerForPastEvents);` functie te gebruiken.

**Extra gebeurtenissen voor ContextHub:**

Alle winkels klaar:

`ContextHub.eventing.on(ContextHub.Constants.EVENT_ALL_STORES_READY, handler, selector, triggerForPastEvents);`

Opslagspecifiek:

`ContextHub.getStore(store).eventing.on(ContextHub.Constants.EVENT_STORE_READY, handler, selector, triggerForPastEvents)`

>[!NOTE]
>
>Zie ook de volledige [ Verwijzing van ContextHub API ](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/contexthub-api.html#ContextHubJavascriptAPIReference)

## Recordcallbacks toevoegen {#adding-record-callbacks}

Voor en na callbacks worden geregistreerd met de functies `CQ_Analytics.registerBeforeCallback(callback,rank)` en `CQ_Analytics.registerAfterCallback(callback,rank)` .

Beide functies nemen een functie als eerste argument en een rang als tweede argument, die de orde dicteert dat callbacks worden uitgevoerd.

Als uw callback vals terugkeert, zullen de callbacks die in de uitvoeringsketen volgen niet worden uitgevoerd.
