---
title: Een nieuwe graniet-UI-veldcomponent maken
description: Granite UI biedt een reeks componenten die zijn ontworpen voor gebruik in formulieren, velden genaamd.
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: platform
content-type: reference
exl-id: e4820330-2ee6-4eca-83fd-462aa0b83647
solution: Experience Manager, Experience Manager Sites
feature: Developing
role: Developer
source-git-commit: 66db4b0b5106617c534b6e1bf428a3057f2c2708
workflow-type: tm+mt
source-wordcount: '498'
ht-degree: 0%

---

# Een nieuwe graniet-UI-veldcomponent maken{#creating-a-new-granite-ui-field-component}

Graniet UI verstrekt een waaier van componenten die worden ontworpen om in vormen worden gebruikt; deze worden genoemd *gebieden* in de verklarende woordenlijst UI. De standaardcomponenten voor graniet-formulieren zijn beschikbaar onder:

`/libs/granite/ui/components/foundation/form/*`

>[!NOTE]
>
>Deze graniet UI vormgebieden zijn van bijzonder belang aangezien zij voor [ componentendialogen ](/help/sites-developing/developing-components.md) worden gebruikt.

>[!NOTE]
>
>Voor volledige details over gebieden, zie de [ documentatie van graniet UI ](https://developer.adobe.com/experience-manager/reference-materials/6-5/granite-ui/api/jcr_root/libs/granite/ui/index.html).

Gebruik het granite UI Foundation-framework om granitecomponenten te ontwikkelen en/of uit te breiden. Dit heeft twee elementen:

* server:

   * een verzameling stichtingscomponenten

      * stichting - modulair, composable, laagbaar, herbruikbaar
      * componenten - Sling-componenten

   * hulpverleners voor de ontwikkeling van toepassingen

* clientzijde:

   * een verzameling clientlibs die een woordenschat (dat wil zeggen een uitbreiding van de HTML-taal) biedt om generieke interactiepatronen te bereiken via een gebruikersinterface die met hypermedia werkt.

De generieke graniet UI-component `field` bestaat uit twee belangwekkende bestanden:

* `init.jsp` : verwerkt de algemene verwerking, de labels, beschrijving en de formulierwaarde die u nodig hebt bij het weergeven van het veld.
* `render.jsp`: dit is de plaats waar de werkelijke rendering van het veld wordt uitgevoerd en moet worden overschreven voor uw aangepaste veld; wordt opgenomen door `init.jsp` .

Zie {de documentatie van 0} granite UI - Gebied ](https://developer.adobe.com/experience-manager/reference-materials/6-5/granite-ui/api/jcr_root/libs/granite/ui/components/foundation/form/field/index.html) voor details.[

Zie voor voorbeelden:

* `cqgems/customizingfield/components/colorpicker`

   * verstrekt door de [ Steekproef van de Code ](/help/sites-developing/developing-components-samples.md#code-sample-how-to-customize-dialog-fields)

* `granite/ui/components/foundation/form`

>[!NOTE]
>
>Aangezien dit mechanisme JSP gebruikt, worden i18n en XSS niet gegeven out-of-the-box. Dit betekent dat je je tekenreeksen moet internationaliseren en ontlopen. De volgende map bevat de generieke velden van een standaardinstantie. U kunt deze als referentie gebruiken:
>
>`/libs/granite/ui/components/foundation/form` directory

## Het serverscript voor de component maken {#creating-the-server-side-script-for-the-component}

Het aangepaste veld mag alleen het script `render.jsp` overschrijven, waar u de markering voor de component opgeeft. U kunt JSP (namelijk het teruggevende manuscript) als omslag voor uw prijsverhoging beschouwen.

1. Maak een component die de eigenschap `sling:resourceSuperType` gebruikt om over te nemen van:

   `/libs/granite/ui/components/foundation/form/field`

1. Overschrijf het script:

   `render.jsp`

   In dit script genereert u de hypermediamarkering (verrijkte markering met de hypermedia-betaalbaarheid), zodat de client weet hoe de interactie met het gegenereerde element tot stand moet worden gebracht. Dit zou de server-zijstijl van Granite UI van codering moeten volgen.

   Wanneer het aanpassen, moet het enige contract dat u ** moet vervullen de vormwaarde (die in `init.jsp` wordt geïnitialiseerd) van het verzoek lezen gebruikend:

   ```
   // Delivers the value of the field (read from the content)
   ValueMap vm = (ValueMap) request.getAttribute(Field.class.getName());
   vm.get("value, String.class");
   ```

   Zie voor meer informatie de implementatie van de velden voor graniet-UI buiten de box, bijvoorbeeld `/libs/granite/ui/components/foundation/form/textfield` .

   >[!NOTE]
   >
   >Op dit moment is JSP de voorkeursscriptmethode, aangezien het niet gemakkelijk is om informatie door te geven van de ene component naar de andere (die vaak voorkomt in de context van formulier/velden) in HTML.

## De clientbibliotheek voor de component maken {#creating-the-client-library-for-the-component}

Specifiek gedrag aan de clientzijde toevoegen aan de component:

1. Maak een clientlib van de categorie `cq.authoring.dialog` .
1. Maak een clientlib van de categorie `cq.authoring.dialog` en definieer de categorie `JS`/ `CSS` in de client.

   Definieer uw `JS`/ `CSS` in de clientlib.

   >[!NOTE]
   >
   >Op dit moment biedt de graniet-interface geen out-of-the-box listeners of haken die u rechtstreeks kunt gebruiken om JS-gedrag toe te voegen. Zo, om extra gedrag JS aan uw component toe te voegen, moet u een haak JS aan een douaneklasse uitvoeren die u dan aan uw component tijdens de prijsverhogingsgeneratie toewijst.
