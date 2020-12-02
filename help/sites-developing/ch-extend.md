---
title: ContextHub uitbreiden
seo-title: ContextHub uitbreiden
description: Bepaal nieuwe types van opslag ContextHub en modules wanneer de verstrekte niet aan uw oplossingsvereisten voldoen
seo-description: Bepaal nieuwe types van opslag ContextHub en modules wanneer de verstrekte niet aan uw oplossingsvereisten voldoen
uuid: 1d80c01d-ec5d-4e76-849d-bec0e1c3941a
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: personalization
content-type: reference
discoiquuid: 13a908ae-6965-4438-96d0-93516b500884
translation-type: tm+mt
source-git-commit: ed34f2200f4ff4f407f7b92165685af390f5f7e3
workflow-type: tm+mt
source-wordcount: '666'
ht-degree: 0%

---


# Uitbreiden ContextHub{#extending-contexthub}

Bepaal nieuwe types van opslag ContextHub en modules wanneer de verstrekte niet aan uw oplossingsvereisten voldoen.

## Aangepaste winkelkandidaten {#creating-custom-store-candidates} maken

ContextHub-winkels worden gemaakt van geregistreerde winkelkandidaten. Als u een aangepast archief wilt maken, moet u een winkelkandidaat maken en registreren.

Het javascript-bestand dat de code bevat waarmee de opslagkandidaat wordt gemaakt en geregistreerd, moet worden opgenomen in een [clientbibliotheekmap](/help/sites-developing/clientlibs.md#creating-client-library-folders). De categorie van de map moet overeenkomen met het volgende patroon:

```xml
contexthub.store.[storeType]
```

Het `[storeType]` deel van de categorie is `storeType` waarmee de opslagkandidaat wordt geregistreerd. (Zie [Registrerend een kandidaat van de Winkel ContextHub](/help/sites-developing/ch-extend.md#registering-a-contexthub-store-candidate)). Voor het storeType van `contexthub.mystore` moet de categorie van de map met de clientbibliotheek bijvoorbeeld `contexthub.store.contexthub.mystore` zijn.

### Een ContextHub Store-kandidaat {#creating-a-contexthub-store-candidate} maken

Om een opslagkandidaat tot stand te brengen, gebruikt u de [`ContextHub.Utils.inheritance.inherit`](/help/sites-developing/contexthub-api.md#inherit-child-parent) functie om één van de basisopslag uit te breiden:

* [`ContextHub.Store.PersistedStore`](/help/sites-developing/contexthub-api.md#contexthub-store-persistedstore)
* [`ContextHub.Store.SessionStore`](/help/sites-developing/contexthub-api.md#contexthub-store-sessionstore)
* [`ContextHub.Store.JSONPStore`](/help/sites-developing/contexthub-api.md#contexthub-store-jsonpstore)
* [`ContextHub.Store.PersistedJSONPStore`](/help/sites-developing/contexthub-api.md#contexthub-store-persistedjsonpstore)

Merk op dat elke basisopslag [`ContextHub.Store.Core`](/help/sites-developing/contexthub-api.md#contexthub-store-core) opslag uitbreidt.

In het volgende voorbeeld wordt de eenvoudigste extensie van de opslagkandidaat `ContextHub.Store.PersistedStore` gemaakt:

```
myStoreCandidate = function(){};
ContextHub.Utils.inheritance.inherit(myStoreCandidate,ContextHub.Store.PersistedStore);
```

Realistisch, zullen uw kandidaten van de douaneopslag extra functies bepalen of zullen de aanvankelijke configuratie van de opslag met voeten treden. Verschillende [voorbeeldopslagkandidaten](/help/sites-developing/ch-samplestores.md) worden in de opslagplaats onder `/libs/granite/contexthub/components/stores` geïnstalleerd. Als u van deze voorbeelden wilt leren, gebruikt u CRXDE Lite om de JavaScript-bestanden te openen.

### Registreren van een kandidaat van de Opslag ContextHub {#registering-a-contexthub-store-candidate}

Registreer een opslagkandidaat om het met het kader te integreren ContextHub en opslag toe te laten om van het worden gecreeerd. Als u een winkelkandidaat wilt registreren, gebruikt u de functie [`registerStoreCandidate`](/help/sites-developing/contexthub-api.md#registerstorecandidate-store-storetype-priority-applies) van de klasse `ContextHub.Utils.storeCandidates`.

Wanneer u een opslagkandidaat registreert, geeft u een naam voor het type winkel op. Wanneer het creëren van een opslag van de kandidaat, gebruikt u het opslagtype om de kandidaat te identificeren waarop het is gebaseerd.

Wanneer u een winkelkandidaat registreert, geeft u de prioriteit aan. Wanneer een opslagkandidaat wordt geregistreerd gebruikend het zelfde archieftype zoals een reeds-geregistreerde opslagkandidaat, wordt de kandidaat met de hogere prioriteit gebruikt. Daarom kunt u bestaande opslagkandidaten met nieuwe implementaties met voeten treden.

```
ContextHub.Utils.storeCandidates.registerStoreCandidate(myStoreCandidate,
                                'contexthub.mystorecandidate', 0);
```

In de meeste gevallen is slechts één kandidaat noodzakelijk en de prioriteit kan aan `0` worden geplaatst, maar als u geinteresseerd bent kunt u over [geavanceerdere registraties leren,](/help/sites-developing/contexthub-api.md#registerstorecandidate-store-storetype-priority-applies) die één van weinige opslagimplementaties toelaat worden gekozen gebaseerd op javascript voorwaarde (`applies`) en kandidaatprioriteit.

## ContextHub UI-moduletypen maken {#creating-contexthub-ui-module-types}

Creeer de types van de douanemodule UI wanneer degenen die [geïnstalleerd met ContextHub](/help/sites-developing/ch-samplemodules.md) zijn niet aan uw vereisten voldoen. Als u een type UI-module wilt maken, maakt u een nieuwe UI-modulerenderer door de klasse `ContextHub.UI.BaseModuleRenderer` uit te breiden en deze vervolgens te registreren met `ContextHub.UI`.

Als u een UI-modulerrenderer wilt maken, maakt u een `Class`-object dat de logica bevat die de UI-module rendert. De klasse moet minimaal de volgende handelingen uitvoeren:

* Breid de `ContextHub.UI.BaseModuleRenderer` klasse uit. Deze klasse is de basisimplementatie voor alle UI modulerenderers. Met het object `Class` wordt een eigenschap met de naam `extend` gedefinieerd die u gebruikt om deze klasse een naam te geven als de klasse die wordt uitgebreid.

* Geef een standaardconfiguratie op. Maak een eigenschap `defaultConfig`. Deze eigenschap is een object dat de eigenschappen bevat die zijn gedefinieerd voor de UI-module [`contexthub.base`](/help/sites-developing/ch-samplemodules.md#contexthub-base-ui-module-type) en andere eigenschappen die u nodig hebt.

De bron voor `ContextHub.UI.BaseModuleRenderer` bevindt zich in /libs/granite/contexthub/code/ui/container/js/ContextHub.UI.BaseModuleRenderer.js.  Gebruik de methode [`registerRenderer`](/help/sites-developing/contexthub-api.md#registerrenderer-moduletype-renderer-dontrender) van de klasse `ContextHub.UI` om de renderer te registreren. U moet een naam voor het moduletype verstrekken. Wanneer beheerders een UI-module maken op basis van deze renderer, geven ze deze naam op.

Maak en registreer de rendererklasse in een automatisch uitgevoerde anonieme functie. Het volgende voorbeeld is gebaseerd op de broncode voor de module van contexthub.browserinfo UI. Deze UI-module is een eenvoudige uitbreiding van de klasse `ContextHub.UI.BaseModuleRenderer`.

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

Het javascript-bestand dat de code bevat die de renderer maakt en registreert, moet worden opgenomen in een [clientbibliotheekmap](/help/sites-developing/clientlibs.md#creating-client-library-folders). De categorie van de map moet overeenkomen met het volgende patroon:

```xml
contexthub.module.[moduleType]
```

Het `[moduleType]` deel van de categorie is `moduleType` waarmee modulerenderer wordt geregistreerd. Voor de `moduleType` van `contexthub.browserinfo` moet de categorie van de clientbibliotheekmap bijvoorbeeld `contexthub.module.contexthub.browserinfo` zijn.
