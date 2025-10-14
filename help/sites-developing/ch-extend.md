---
title: ContextHub uitbreiden
description: Bepaal nieuwe types van opslag ContextHub en modules wanneer de verstrekte niet aan uw oplossingsvereisten voldoen
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: personalization
content-type: reference
exl-id: 41898fa7-a369-4c63-8ccb-69eb3fa146a1
solution: Experience Manager, Experience Manager Sites
feature: Developing,Personalization
role: Developer
source-git-commit: 305227eff3c0d6414a5ae74bcf3a74309dccdd13
workflow-type: tm+mt
source-wordcount: '637'
ht-degree: 0%

---

# ContextHub uitbreiden{#extending-contexthub}

Bepaal nieuwe types van opslag ContextHub en modules wanneer de verstrekte niet aan uw oplossingsvereisten voldoen.

## Aangepaste winkelkandidaten maken {#creating-custom-store-candidates}

ContextHub-winkels worden gemaakt van geregistreerde winkelkandidaten. Als u een aangepaste winkel wilt maken, maakt en registreert u een winkelkandidaat.

Het dossier van JavaScript dat de code omvat die leidt en registreert de opslagkandidaat moet in de omslag van de a [&#x200B; cliëntbibliotheek &#x200B;](/help/sites-developing/clientlibs.md#creating-client-library-folders) worden omvat. De categorie van de map moet overeenkomen met het volgende patroon:

```xml
contexthub.store.[storeType]
```

Het `[storeType]` -gedeelte van de categorie is de `storeType` waarmee de winkelkandidaat is geregistreerd. (Zie [&#x200B; registrerend een Kandidaat van de Winkel ContextHub &#x200B;](/help/sites-developing/ch-extend.md#registering-a-contexthub-store-candidate)). Voor het storeType van `contexthub.mystore` moet de categorie van de clientbibliotheekmap bijvoorbeeld `contexthub.store.contexthub.mystore` zijn.

### Een ContextHub Store-kandidaat maken {#creating-a-contexthub-store-candidate}

Als u een winkelkandidaat wilt maken, gebruikt u de functie [`ContextHub.Utils.inheritance.inherit`](/help/sites-developing/contexthub-api.md#inherit-child-parent) om een van de basiswinkels uit te breiden:

* [` ContextHub.Store.PersistedStore`](/help/sites-developing/contexthub-api.md#contexthub-store-persistedstore)
* [` ContextHub.Store.SessionStore`](/help/sites-developing/contexthub-api.md#contexthub-store-sessionstore)
* [` ContextHub.Store.JSONPStore`](/help/sites-developing/contexthub-api.md#contexthub-store-jsonpstore)
* [` ContextHub.Store.PersistedJSONPStore`](/help/sites-developing/contexthub-api.md#contexthub-store-persistedjsonpstore)

Elke basisopslag breidt de [`ContextHub.Store.Core`](/help/sites-developing/contexthub-api.md#contexthub-store-core) store uit.

In het volgende voorbeeld wordt de eenvoudigste extensie van de opslagkandidaat van `ContextHub.Store.PersistedStore` gemaakt:

```
myStoreCandidate = function(){};
ContextHub.Utils.inheritance.inherit(myStoreCandidate,ContextHub.Store.PersistedStore);
```

Realistisch, bepalen uw kandidaten van de douaneopslag extra functies of treden de aanvankelijke configuratie van de opslag met voeten. Verscheidene [&#x200B; de kandidaten van de steekproefopslag &#x200B;](/help/sites-developing/ch-samplestores.md) zijn geïnstalleerd in de bewaarplaats hieronder `/libs/granite/contexthub/components/stores`. Als u van deze voorbeelden wilt leren, opent u de JavaScript-bestanden met CRXDE Lite.

### Registreren van een ContextHub Store-kandidaat {#registering-a-contexthub-store-candidate}

Registreer een opslagkandidaat om het met het kader te integreren ContextHub en opslag toe te laten om van het worden gecreeerd. Gebruik de functie [`registerStoreCandidate`](/help/sites-developing/contexthub-api.md#registerstorecandidate-store-storetype-priority-applies) van de `ContextHub.Utils.storeCandidates` -klasse om een winkelkandidaat te registreren.

Wanneer u een opslagkandidaat registreert, geeft u een naam voor het type winkel op. Wanneer het creëren van een opslag van de kandidaat, gebruikt u het opslagtype om de kandidaat te identificeren waarop het is gebaseerd.

Wanneer u een winkelkandidaat registreert, geeft u de prioriteit aan. Wanneer een opslagkandidaat wordt geregistreerd gebruikend het zelfde archieftype zoals een reeds-geregistreerde opslagkandidaat, wordt de kandidaat met de hogere prioriteit gebruikt. Daarom kunt u bestaande opslagkandidaten met nieuwe implementaties met voeten treden.

```
ContextHub.Utils.storeCandidates.registerStoreCandidate(myStoreCandidate,
                                'contexthub.mystorecandidate', 0);
```

Gewoonlijk is slechts één kandidaat nodig en kan de prioriteit worden ingesteld op `0` . Maar als u geinteresseerd bent, kunt u over [&#x200B; geavanceerdere registraties leren, &#x200B;](/help/sites-developing/contexthub-api.md#registerstorecandidate-store-storetype-priority-applies) die één van weinig opslagimplementaties om toestaat worden gekozen gebaseerd op de voorwaarde van JavaScript (`applies`) en kandidaatprioriteit.

## ContextHub UI-moduletypen maken {#creating-contexthub-ui-module-types}

Creeer de moduletypes van douane UI wanneer degenen die [&#x200B; met ContextHub &#x200B;](/help/sites-developing/ch-samplemodules.md) worden geïnstalleerd niet aan uw vereisten voldoen. Als u een type UI-module wilt maken, maakt u een renderer voor een UI-module door de klasse `ContextHub.UI.BaseModuleRenderer` uit te breiden en deze vervolgens te registreren bij `ContextHub.UI` .

Als u een renderer voor een UI-module wilt maken, maakt u een `Class` -object dat de logica bevat die de UI-module rendert. De klasse moet minimaal de volgende handelingen uitvoeren:

* Breid de `ContextHub.UI.BaseModuleRenderer` -klasse uit. Deze klasse is de basisimplementatie voor alle UI modulerenderers. Het object `Class` definieert een eigenschap met de naam `extend` die u gebruikt om deze klasse een naam te geven als de klasse die wordt uitgebreid.

* Geef een standaardconfiguratie op. Maak een eigenschap `defaultConfig` . Deze eigenschap is een object dat de eigenschappen bevat die zijn gedefinieerd voor de module [`contexthub.base`](/help/sites-developing/ch-samplemodules.md#contexthub-base-ui-module-type) UI en andere eigenschappen die u nodig hebt.

De bron voor `ContextHub.UI.BaseModuleRenderer` is /libs/granite/contexthub/code/ui/container/js/ContextHub.UI.BaseModuleRenderer.js. Gebruik de methode [`registerRenderer`](/help/sites-developing/contexthub-api.md#registerrenderer-moduletype-renderer-dontrender) van de `ContextHub.UI` -klasse om de renderer te registreren. Geef een naam op voor het moduletype. Wanneer beheerders een UI-module maken op basis van deze renderer, geven ze deze naam op.

Maak en registreer de rendererklasse in een automatisch uitgevoerde anonieme functie. Het volgende voorbeeld is gebaseerd op de broncode voor de module van contexthub.browserinfo UI. Deze UI-module is een eenvoudige uitbreiding van de klasse `ContextHub.UI.BaseModuleRenderer` .

```xml
;(function() {

    var SurferinfoRenderer = new Class({
        extend: ContextHub.UI.BaseModuleRenderer,

        defaultConfig: {
            icon: 'coral-Icon--globe',
            title: 'Browser/OS Information',

            storeMapping: {
                surferinfo: 'surferinfo'
            },

            template:
                '<p>{{surferinfo.browser.family}} {{surferinfo.browser.version}}</p>' +
                '<p>{{surferinfo.os.name}} {{surferinfo.os.version}}</p>'
        }
    });

    ContextHub.UI.registerRenderer('contexthub.browserinfo', new SurferinfoRenderer());

}());
```

Het dossier van JavaScript dat de code omvat die tot en registreert renderer moet in de omslag van de a [&#x200B; cliëntbibliotheek &#x200B;](/help/sites-developing/clientlibs.md#creating-client-library-folders) worden omvat. De categorie van de map moet overeenkomen met het volgende patroon:

```xml
contexthub.module.[moduleType]
```

Het `[moduleType]` -gedeelte van de categorie is de `moduleType` waarmee de modulerenderer is geregistreerd. Voor `moduleType` of `contexthub.browserinfo` moet de categorie van de clientbibliotheekmap bijvoorbeeld `contexthub.module.contexthub.browserinfo` zijn.
