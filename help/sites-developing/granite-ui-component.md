---
title: Een nieuwe graniet-UI-veldcomponent maken
description: Granite UI biedt een reeks componenten die zijn ontworpen voor gebruik in formulieren, velden genaamd.
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: platform
content-type: reference
exl-id: e4820330-2ee6-4eca-83fd-462aa0b83647
solution: Experience Manager, Experience Manager Sites
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '498'
ht-degree: 0%

---

# Een nieuwe graniet-UI-veldcomponent maken{#creating-a-new-granite-ui-field-component}

De graniet UI verstrekt een waaier van componenten die worden ontworpen om in vormen worden gebruikt; deze worden genoemd *velden* in de woordenlijst van de gebruikersinterface van Granite. De standaardcomponenten voor graniet-formulieren zijn beschikbaar onder:

`/libs/granite/ui/components/foundation/form/*`

>[!NOTE]
>
>Deze formuliervelden van de graniet-interface zijn van bijzonder belang omdat ze worden gebruikt voor [componentdialoogvensters](/help/sites-developing/developing-components.md).

>[!NOTE]
>
>Voor volledige informatie over velden raadpleegt u de [Granite UI-documentatie](https://developer.adobe.com/experience-manager/reference-materials/6-5/granite-ui/api/jcr_root/libs/granite/ui/index.html).

Gebruik het granite UI Foundation-framework om granitecomponenten te ontwikkelen en/of uit te breiden. Dit heeft twee elementen:

* server:

   * een verzameling stichtingscomponenten

      * stichting - modulair, composable, laagbaar, herbruikbaar
      * componenten - Sling-componenten

   * hulpverleners voor de ontwikkeling van toepassingen

* clientzijde:

   * een verzameling clientlibs die een woordenschat (dat wil zeggen een uitbreiding van de HTML-taal) biedt om generieke interactiepatronen te bereiken via een gebruikersinterface die met hypermedia werkt.

De generische graniet UI-component `field` bestaat uit twee belangstellende bestanden:

* `init.jsp`Met : wordt de algemene verwerking afgehandeld; de labels, beschrijving en de formulierwaarde die u nodig hebt bij het weergeven van het veld.
* `render.jsp`: dit is de plaats waar de daadwerkelijke rendering van het veld wordt uitgevoerd en moet worden overschreven voor uw aangepaste veld; wordt opgenomen door `init.jsp`.

Zie [Granite UI-documentatie - Veld](https://developer.adobe.com/experience-manager/reference-materials/6-5/granite-ui/api/jcr_root/libs/granite/ui/components/foundation/form/field/index.html) voor meer informatie.

Zie voor voorbeelden:

* `cqgems/customizingfield/components/colorpicker`

   * door de [Codevoorbeeld](/help/sites-developing/developing-components-samples.md#code-sample-how-to-customize-dialog-fields)

* `granite/ui/components/foundation/form`

>[!NOTE]
>
>Aangezien dit mechanisme JSP gebruikt, worden i18n en XSS niet gegeven out-of-the-box. Dit betekent dat je je tekenreeksen moet internationaliseren en ontlopen. De volgende map bevat de generieke velden van een standaardinstantie. U kunt deze als referentie gebruiken:
>
>`/libs/granite/ui/components/foundation/form` directory

## Het serverscript voor de component maken {#creating-the-server-side-script-for-the-component}

Het aangepaste veld mag alleen het `render.jsp` script, waar u de markering voor uw component opgeeft. U kunt JSP (namelijk het teruggevende manuscript) als omslag voor uw prijsverhoging beschouwen.

1. Een component maken die de opdracht `sling:resourceSuperType` over te nemen eigenschap van:

   `/libs/granite/ui/components/foundation/form/field`

1. Overschrijf het script:

   `render.jsp`

   In dit script genereert u de hypermediamarkering (verrijkte markering met de hypermedia-betaalbaarheid), zodat de client weet hoe de interactie met het gegenereerde element tot stand moet worden gebracht. Dit zou de server-zijstijl van Granite UI van codering moeten volgen.

   Het enige contract dat u tijdens het aanpassen *moet* fulfill moet de formulierwaarde lezen (geïnitialiseerd in `init.jsp`) van het verzoek met:

   ```
   // Delivers the value of the field (read from the content)
   ValueMap vm = (ValueMap) request.getAttribute(Field.class.getName());
   vm.get("value, String.class");
   ```

   Voor meer details, zie de implementatie van uit-de-doos gebieden van de Vergroting UI; bijvoorbeeld `/libs/granite/ui/components/foundation/form/textfield`.

   >[!NOTE]
   >
   >Op dit moment is JSP de voorkeursscriptmethode, aangezien het niet gemakkelijk is om informatie door te geven van de ene component naar de andere (die vaak voorkomt in de context van formulier/velden) in HTML.

## De clientbibliotheek voor de component maken {#creating-the-client-library-for-the-component}

Specifiek gedrag aan de clientzijde toevoegen aan de component:

1. Een clientlib van een categorie maken `cq.authoring.dialog`.
1. Een clientlib van een categorie maken `cq.authoring.dialog` en definieert u uw `JS`/ `CSS` erin.

   Definieer uw `JS`/ `CSS` in de client.

   >[!NOTE]
   >
   >Op dit moment biedt de graniet-interface geen out-of-the-box listeners of haken die u rechtstreeks kunt gebruiken om JS-gedrag toe te voegen. Zo, om extra gedrag JS aan uw component toe te voegen, moet u een haak JS aan een douaneklasse uitvoeren die u dan aan uw component tijdens de prijsverhogingsgeneratie toewijst.
