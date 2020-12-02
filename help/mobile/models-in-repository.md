---
title: Modellen in opslagplaats
seo-title: Modellen in opslagplaats
description: 'null'
seo-description: 'null'
uuid: 54f81180-4178-4e33-a6f0-e9e6ea50798e
contentOwner: User
content-type: reference
discoiquuid: ae1a72f4-d8c1-4c75-ba2c-7322f3743b17
noindex: true
redirecttarget: /content/help/en/experience-manager/6-4/mobile/using/administer-mobile-apps
translation-type: tm+mt
source-git-commit: 5120bbdefea528ad6d07a9c99df565555b6a8444
workflow-type: tm+mt
source-wordcount: '1332'
ht-degree: 0%

---


# Modellen in gegevensopslagruimte{#models-in-repository}

>[!NOTE]
>
>Adobe raadt aan de SPA Editor te gebruiken voor projecten die renderen op basis van één pagina voor toepassingsframework op de client-side vereisen (bijvoorbeeld Reageren). [Meer](/help/sites-developing/spa-overview.md) informatie.

Een model bevat een reeks gegevenstypen die de eigenschappen bepalen die uiteindelijk door inhoudsdiensten zullen worden teruggegeven. Een model bepaalt ook de verhoudingen tussen andere modellen om gegevensintegriteit af te dwingen.

Als ontwikkelaar zou u met de Modelstructuur in bewaarplaats vertrouwd moeten zijn. U kunt uw eigen modellen en entiteiten maken volgens de vereisten voor uw app.

## Modeltypen maken {#creating-model-types}

Er zijn twee modeltypen voor het systeem onder */libs/settings/mobileapps/model-types*. Als u de types van systeemmodel wilt met voeten treden zal een *mobileapps/model-types* knoop onder de configuratieknoop moeten worden gecreeerd u wenst dat de opheffing voorkomt.

Als u bijvoorbeeld configuraties op */conf/myconf1* en */conf/myconf2* hebt gemaakt en u de systeemmodeltypen alleen op *conf1* wilt overschrijven, maakt u een *mobileapps/model-types* onder de instellingen van *conf1*.

Als u gegevenstypen aan een model wilt toevoegen, moet het modeltype een onderliggende node hebben met de naam &#39;scaffolding&#39; van het type &#39;cq:Page&#39; en een resourcepype van *wcm/scaffolding/components/scaffolding*.

De basispagina moet ook een eigenschap *dataTypesConfig* op het knooppunt PageContent bevatten die aangeeft welke gegevenstypemodellen van dit type mogen worden gebruikt.

>[!NOTE]
>
>Een **Basisstructuur** is een pagina die de gegevenstypen definieert die kunnen worden bewerkt door een entiteit op basis van het model. Elk gegevenstype kan ook worden gevormd om te bepalen hoe het gebied in UI zal worden voorgesteld evenals hoe de gegevenswaarde zal worden voortgeduurd.

### Config {#data-types-config} voor gegevenstypen

De gegevenstypes config knoop bevat een lijst van gegevenstypepunten. Elk gegevenstype punt specificeert hoe een gegevenstype in de modelredacteur zal verschijnen evenals hoe het voor uiteindelijke het teruggeven door een entiteit moet worden voortgeduurd.

| **Eigenschapnaam** | **Beschrijving** |
|---|---|
| fieldIcon | klasse van het CoralUI-pictogram dat het gegevenstype vertegenwoordigt |
| fieldPropResourceType | component die alle eigenschappen voor het vormen van het gegevenstype zal teruggeven |
| fieldProperties | lijst met meerdere waarden van eigenschapcomponenten die worden gebruikt wanneer fieldPropResourceType *mobileapps/caas/gui/components/models/editor/datatypes/field* is |
| fieldResourceType | resourceType van de persisted knoop voor het gegevenstype (namelijk de component die het bezit in de entiteitredacteur zal teruggeven) |
| fieldViewResourceType | component voor het teruggeven van gegevenstype in modelredacteursmening (fieldResourceType zal worden gebruikt als dit bezit wordt weggelaten) |
| fieldTitle | naam van het gegevenstype dat in de modelredacteur zal worden getoond |
| multiFieldResourceType | middeltype aan gebruik op persisted knoop wanneer multi-value wordt geselecteerd |
| renderType | weergeven, aanwijzing voor renderen op de client |

### Config-overlay gegevenstypen {#data-types-config-overlay}

De eigenschap &#39;dataTypesConfig&#39; ondersteunt samenvoeging van resources splitsen. Dit betekent de gegevenstypes die door de types van systeemmodel (of zelfs de types van douanemodel) worden gebruikt kunnen worden aangepast door bedekkingsknopen te gebruiken.

Een overlay van */libs/settings/mobileapps/models/formbuilderconfig/datatypes* moet worden gemaakt en vervolgens naar wens worden aangepast.

Een bedekking voor het gegevenstype String kan bijvoorbeeld worden toegevoegd om het fieldResourceType te wijzigen in een aangepaste component.

Voor meer informatie bij het Verzenden van Middel zie samenvoegen, [Gebruikend het Verschuiven Samenvoegen van het Middel in AEM](/help/sites-developing/sling-resource-merger.md).

![chlimage_1-7](assets/chlimage_1-7.png)

### Gegevenstypen {#data-types}

Een gegevenstype van een model is een formuliercomponent die gegevens kan bevatten die moeten worden opgenomen wanneer een formulier wordt gepost. De component van het gegevenstype kan zo gecompliceerd zijn als gewenst. Een voorbeeld van een type van douanegegevens zou een adresblok voor een bepaald land kunnen zijn om te vermijden hebbend het moeten altijd opnieuw creëren gebruikend de primitieve gegevenstypes.

Zie &#39;/libs/mobileapps/caas/components/form/contentReference&#39; als voorbeeld van een aangepast gegevenstype.

Alle primitieve gegevenstypen maken gebruik van bestaande Granite-formuliercomponenten. Zie: [https://docs.adobe.com/docs/en/aem/6-3/develop/ref/granite-ui/api/jcr_root/libs/granite/ui/components/coral/foundation/form/index.html](https://docs.adobe.com/docs/en/aem/6-3/develop/ref/granite-ui/api/jcr_root/libs/granite/ui/components/coral/foundation/form/index.html)

Om het even welk type van douanegegevens kan dan aan een gegevenstype config voor gebruik door de modelredacteur worden toegevoegd.

## Modellen maken {#creating-models}

U kunt beginnen modellen te creëren zodra alle gewenste modeltypes en gegevenstypes zijn ontwikkeld. De auteurs zullen uiteindelijk modellen gebruiken om entiteiten te creëren waarvan de inhoudsdiensten gebruiken om zijn gegevens van terug te geven.

Het creëren van een model bestaat uit het plukken van een toegestaan modeltype dat op de huidige configuratie wordt gebaseerd en dan het verstrekken van een titel en een beschrijving.

Zie [Een model maken](/help/mobile/administer-mobile-apps.md) onder ontwerpsectie voor mobiele apps voor meer informatie over het maken en beheren van een model op het dashboard.

### Eigenschappen van een model {#properties-of-a-model}

In de volgende tabel worden de eigenschappen weergegeven die voor een model zijn gedefinieerd:

| **Eigenschapnaam** | **Beschrijving** |
|---|---|
| Modeltitel | naam van het model |
| Beschrijving | beschrijving van het model |
| Miniatuur | miniatuurafbeelding van het model |
| Modeltype | type van het model (dit kan een eenvoudige tekenreeks zijn of een pad naar een werkelijke component) |
| Toegestane kinderen | pad van een sjabloon die een onderliggend element van deze sjabloon mag zijn |
| Toegestane bovenliggende elementen | pad van een sjabloon dat bovenliggend element van deze sjabloon mag zijn |

>[!NOTE]
>
>De *toegestane onderliggende elementen* en *toegestane bovenliggende elementen* volgen dezelfde regels als paginasjablonen. Zie [Paginasjablonen](/help/sites-developing/page-templates-static.md) voor meer informatie.
>
>Met betrekking tot de *eigenschap Model Type* moeten alle modellen een supertype van *mobileapps/caas/components/data/entity* hebben, maar kunnen zij een subtype hebben dat het mogelijk maakt de levering van de inhoud aan te passen. Als u ervoor zorgt dat alle modeltypen uniek zijn, kunnen clients van inhoudsservices ook een onderscheid maken tussen objecten in de gegevens.

### Een model bewerken {#editing-a-model}

Als u een model bewerkt, opent u het basisdialoogvenster dat is gekoppeld aan een model en kunt u het bewerken. Over het algemeen is de basisstructuur een onderliggend knooppunt van het model, maar kan deze buiten het model worden geplaatst als dat gewenst is door het pad ervan op te geven met de eigenschap &#39;cq:scaffolding&#39;. Dit is nuttig als u dezelfde basisstructuur wilt delen tussen meerdere modellen die verschillende eigenschappen moeten hebben.

Wanneer het basiselement voor het model wordt gevonden, zal de modeleditor alles renderen wat zich onder &#39;jcr:content/cq:dialog/content&#39; bevindt. Momenteel wordt alleen een vaste indeling met maximaal drie kolommen ondersteund door de instelprogramma-engine voor de client-side versie. Rechts van het weergegeven formulierdialoogvenster ziet u een lijst met alle gegevenstypen die zijn opgegeven in de configuratie van de gegevenstypen. U kunt gegevenstypen bewerken door erop te klikken. De rechterspoorstaaf zal dan op het eigenschappen lusje voor het geselecteerde gegevenstype schakelen. U kunt nieuwe gegevenstypen toevoegen door deze naar het voorvertoningscanvas te slepen. Klik op Opslaan om de wijzigingen door te geven aan de server. Klik op Annuleren om de modeleditor te sluiten.

>[!NOTE]
>
>Alle modellen zijn Malplaatjes, zodat volgen zij alle AEM regels van het Malplaatje. Dit staat het gebruiken van eigenschappen zoals *allowedParents* en *allowedChildren* eigenschappen toe. Deze zijn effectief bij het maken van nieuwe entiteiten op basis van een model. De sjabloonregels zorgen ervoor dat entiteiten alleen op bepaalde modellen kunnen worden gebaseerd, afhankelijk van hun hiërarchie.
>
>Zie [Creating a Model](/help/mobile/administer-mobile-apps.md) under authoring section for Mobile Apps voor meer informatie over het bewerken van een model op het dashboard.

### Systeemmodellen {#system-models}

Er zijn twee typen vooraf gedefinieerde systeemmodellen beschikbaar voor eenvoudig hergebruik van inhoud. Deze modellen kunnen niet worden bewerkt.

**Het** model Pagina&#39;sHet model Pagina&#39;s biedt een snelle methode voor het hergebruiken van bestaande inhoud van sites voor levering door inhoudsservices.

Het resourceType van entiteiten die op het model van Pagina&#39;s worden gebaseerd is: mobileapps/cas/components/data/pages

Pad: Pad naar een sitepagina. Inhoud van dit pad (en de onderliggende elementen) wordt weergegeven door inhoudsservicehandlers.

**Assets** ModelHet middelenmodel biedt een snelle methode voor het hergebruiken van bestaande inhoud van Elementen voor levering door inhoudsservices.

Het resourceType van entiteiten die op het model van Pagina&#39;s worden gebaseerd is: *mobileapps/caas/components/data/assets.*

Lijst met elementen: Lijst met paden van elementen. Elk element wordt toegevoegd als een onderliggende entiteitsknooppunt met een resourceType van *wcm/foundation/components/image*.

>[!NOTE]
>
>Meer over het gebruiken van deze malplaatjes voor het creëren van modellen van het dashboard, zie [Creërend een Model](/help/mobile/administer-mobile-apps.md) onder auteurssectie voor Mobiele Apps.
