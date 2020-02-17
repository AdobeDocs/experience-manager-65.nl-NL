---
title: Een nieuwe graniet UI-veldcomponent maken
seo-title: Een nieuwe graniet UI-veldcomponent maken
description: De graniet-interface biedt een aantal componenten die zijn ontworpen voor gebruik in formulieren, velden genaamd
seo-description: De graniet-interface biedt een aantal componenten die zijn ontworpen voor gebruik in formulieren, velden genaamd
uuid: cf26e057-4b0c-45f4-8975-2c658517f20e
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: platform
content-type: reference
discoiquuid: 94b9eeee-aae3-4b28-9d6f-1be0e4acd982
translation-type: tm+mt
source-git-commit: 5128a08d4db21cda821de0698b0ac63ceed24379

---


# Een nieuwe graniet UI-veldcomponent maken{#creating-a-new-granite-ui-field-component}

Graniet UI biedt een reeks componenten die zijn ontworpen voor gebruik in formulieren; Dit worden genoemd *gebieden* in de verklarende woordenlijst UI. De standaardcomponenten voor graniet-formulieren zijn beschikbaar onder:

`/libs/granite/ui/components/foundation/form/*`

>[!NOTE]
>
>Deze formuliervelden in de gebruikersinterface van Granite zijn van bijzonder belang omdat ze worden gebruikt voor [componentdialoogvensters](/help/sites-developing/developing-components.md).

>[!NOTE]
>
>Raadpleeg de documentatie [van de](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/granite-ui/api/index.html)Granite UI voor meer informatie over velden.

Gebruik het granite UI Foundation-framework om granitecomponenten te ontwikkelen en/of uit te breiden. Dit heeft twee elementen:

* server:

   * een verzameling stichtingscomponenten

      * stichting - modulair, composable, laagbaar, herbruikbaar
      * componenten - Sling-componenten
   * hulpverleners voor de ontwikkeling van toepassingen


* clientzijde:

   * een verzameling clientlibs die een woordenschat biedt (bijv. uitbreiding van de HTML-taal) om generieke interactiepatronen te bereiken via een door Hypermedia gestuurde interface

De generieke component van Granite UI `field` bestaat uit twee dossiers van belang:

* `init.jsp`: verwerkt de generieke verwerking; een label, beschrijving en een formulierwaarde die u nodig hebt bij het weergeven van uw veld.
* `render.jsp`: Hier wordt de daadwerkelijke rendering van het veld uitgevoerd en moet deze worden overschreven voor het aangepaste veld. is opgenomen door `init.jsp`.

Raadpleeg de documentatie van de [Granite UI - Veld](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/granite-ui/api/jcr_root/libs/granite/ui/components/foundation/form/field/index.html) als u meer informatie wilt.

Zie voor voorbeelden:

* `cqgems/customizingfield/components/colorpicker`

   * verstrekt door de Steekproef van de [Code](/help/sites-developing/developing-components-samples.md#code-sample-how-to-customize-dialog-fields)

* `granite/ui/components/foundation/form`

>[!NOTE]
>
>Aangezien dit mechanisme JSP gebruikt, worden i18n en XSS niet gegeven out-of-the-box. Dit betekent dat u uw strings moet internationaliseren en er niet bij hoeft te komen. De volgende map bevat de algemene velden van een standaardinstantie. U kunt deze als referentie gebruiken:
>
>`/libs/granite/ui/components/foundation/form` directory

## Het serverscript voor de component maken {#creating-the-server-side-script-for-the-component}

Het aangepaste veld mag alleen het `render.jsp` script overschrijven, waarin u de markering voor de component opgeeft. U kunt JSP (d.w.z. het teruggevende manuscript) als omslag voor uw prijsverhoging beschouwen.

1. Maak een nieuwe component die de `sling:resourceSuperType` eigenschap gebruikt om over te nemen van:

   `/libs/granite/ui/components/foundation/form/field`

1. Overschrijf het script:

   `render.jsp`

   In dit script moet u de hypermediamarkering genereren (verrijkte markering die de hypermediabelelans bevat), zodat de client weet hoe deze moet communiceren met het gegenereerde element. Dit zou de server-zijstijl van Granite UI van codering moeten volgen.

   Bij het aanpassen *moet* u alleen de formulierwaarde (geïnitialiseerd in `init.jsp`) uit de aanvraag lezen met:

   ```
   // Delivers the value of the field (read from the content)
   ValueMap vm = (ValueMap) request.getAttribute(Field.class.getName());
   vm.get("value, String.class");
   ```

   Voor meer informatie, gelieve te verwijzen naar de implementatie van uit-de-doos gebieden van de Vergroting UI; bijvoorbeeld `/libs/granite/ui/components/foundation/form/textfield`.

   >[!NOTE]
   >
   >Op dit moment is JSP de voorkeursscriptmethode, aangezien het niet gemakkelijk is om informatie door te geven van de ene component naar de andere (die in de context van formulier/velden veel voorkomt) in HTML.

## De clientbibliotheek voor de component maken {#creating-the-client-library-for-the-component}

Specifiek gedrag aan de clientzijde toevoegen aan de component:

1. Maak een clientlib van categorie `cq.authoring.dialog`.
1. Maak een clientlib van categorie `cq.authoring.dialog` en definieer uw `JS`/ `CSS` binnenkant.

   Definieer uw `JS`/ `CSS` binnenkant van de clientlib.

   >[!NOTE]
   >
   >Op dit moment biedt de graniet-interface geen out-of-the-box listeners of haken die u rechtstreeks kunt gebruiken om JS-gedrag toe te voegen. Zo, om extra gedrag JS aan uw component toe te voegen, moet u een haak JS aan een douaneklasse uitvoeren die u dan aan uw component tijdens de prijsverhogingsgeneratie toewijst.

