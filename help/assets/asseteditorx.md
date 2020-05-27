---
title: Editor van element uitbreiden
description: Leer hoe u de mogelijkheden van de Asset Editor uitbreidt met behulp van aangepaste componenten.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 566add37d6dd7efe22a99fc234ca42878f050aee
workflow-type: tm+mt
source-wordcount: '695'
ht-degree: 13%

---


# Extend Asset Editor {#extending-asset-editor}

De Asset Editor is de pagina die wordt geopend wanneer op een element wordt geklikt dat via Asset Share wordt gevonden, zodat de gebruiker deze aspecten van het element kan bewerken, zoals metagegevens, miniaturen, titels en tags.

De configuratie van de redacteur die de vooraf bepaalde het uitgeven componenten gebruikt wordt behandeld in het [Creëren van en het Vormen van een Pagina](assets-finder-editor.md#creating-and-configuring-an-asset-editor-page)van de Redacteur van Activa.

Naast het gebruik van reeds bestaande editorcomponenten, kunnen de ontwikkelaars van de Manager van de Ervaring van Adobe ook hun eigen componenten tot stand brengen.

## Een sjabloon voor de Asset Editor maken {#creating-an-asset-editor-template}

De volgende voorbeeldpagina&#39;s worden opgenomen in Geometrixx:

* Voorbeeldpagina voor Geometrixx: `/content/geometrixx/en/press/asseteditor.html`
* Voorbeeldsjabloon: `/apps/geometrixx/templates/asseteditor`
* Voorbeeld van paginacomponent: `/apps/geometrixx/components/asseteditor`

### Clientlib configureren {#configuring-clientlib}

Elementen gebruiken een extensie van de WCM-bewerkingsclient. De clientlibs worden meestal in geladen `init.jsp`.

Vergeleken met het standaard clientlib laden (in kern `init.jsp`), moet een malplaatje van Activa het volgende hebben:

* De sjabloon moet de `cq.dam.edit` clientlib bevatten (in plaats van `cq.wcm.edit`).

* De clientbibliotheek moet ook in de uitgeschakelde WCM-modus (bijvoorbeeld, geladen op **publiceren**) worden opgenomen om de predicaten, de acties, en de lenzen weer te geven.

In de meeste gevallen moet het kopiëren van het bestaande monster `init.jsp` (`/apps/geometrixx/components/asseteditor/init.jsp`) aan deze behoeften voldoen.

### JS-handelingen configureren {#configuring-js-actions}

Voor sommige elementen worden JS-functies gedefinieerd in `component.js`. Kopieer dit bestand naar de map met componenten en koppel deze.

```javascript
<script type="text/javascript" src="<%= component.getPath() %>/component.js"></script>
```

In het voorbeeld wordt deze javascript-bron geladen in `head.jsp`(`/apps/geometrixx/components/asseteditor/head.jsp`).

### Aanvullende stijlbladen {#additional-style-sheets}

Sommige middelencomponenten gebruiken de widgetbibliotheek. Om correct in de inhoudscontext te worden teruggegeven, moet een extra stijlblad worden geladen. Voor de component Handeling tag is nog een component vereist.

```css
<link href="/etc/designs/geometrixx/ui.widgets.css" rel="stylesheet" type="text/css">
```

### Geometrixx stijlblad {#geometrixx-style-sheet}

Voor de voorbeeldpaginacomponenten is het vereist dat alle kiezers beginnen met `.asseteditor` van `static.css` (`/etc/designs/geometrixx/static.css`). Beste praktijken: Kopieer alle `.asseteditor` kiezers naar de stijlpagina en pas de regels naar wens aan.

### FormChooser: Aanpassingen voor uiteindelijk geladen bronnen {#formchooser-adjustments-for-eventually-loaded-resources}

De Asset Editor gebruikt de Formulierkiezer, waarmee u bronnen (in dit geval elementen) op dezelfde formulierpagina kunt bewerken door gewoon een formulierkiezer en het pad van het formulier toe te voegen aan de URL van het element.

Bijvoorbeeld:

* Onbewerkte formulierpagina: [http://localhost:4502/content/geometrixx/en/press/asseteditor.html](http://localhost:4502/content/geometrixx/en/press/asseteditor.html)
* In de formulierpagina geladen element: [http://localhost:4502/content/dam/geometrixx/icons/diamond.png.form.html/content/geometrixx/en/press/asseteditor.html](http://localhost:4502/content/dam/geometrixx/icons/diamond.png.form.html/content/geometrixx/en/press/asseteditor.html)

De voorbeeldhandgrepen in `head.jsp` (`/apps/geometrixx/components/asseteditor/head.jsp`) doen het volgende:

* Ze detecteren of een element is geladen of dat het normale formulier moet worden weergegeven.
* Als een element wordt geladen, schakelen zij WCM wijze als parsys slechts op een gewone vormpagina uit.
* Als een element is geladen, gebruiken deze de titel in plaats van de titel op de formulierpagina.

```javascript
 List<Resource> resources = FormsHelper.getFormEditResources(slingRequest);
    if (resources != null) {
        if (resources.size() == 1) {
            // single resource
            FormsHelper.setFormLoadResource(slingRequest, resources.get(0));
        } else if (resources.size() > 1) {
            // multiple resources
            // not supported by CQ 5.3
        }
    }
    Resource loadResource = (Resource) request.getAttribute("cq.form.loadresource");
    String title;
    if (loadResource != null) {
        // an asset is loaded: disable WCM
        WCMMode.DISABLED.toRequest(request);

        String path = loadResource.getPath();
        Asset asset = loadResource.adaptTo(Asset.class);
        try {
            // it might happen that the adobe xmp lib creates an array
            Object titleObj = asset.getMetadata("dc:title");
            if (titleObj instanceof Object[]) {
                Object[] titleArray = (Object[]) titleObj;
                title = (titleArray.length > 0) ? titleArray[0].toString() : "";
            } else {
                title = titleObj.toString();
            }
        }
        catch (NullPointerException e) {
            title = path.substring(path.lastIndexOf("/") + 1);
        }
    }
    else {
        title = currentPage.getTitle() == null ? currentPage.getName() : currentPage.getTitle();
    }
```

Gebruik in het HTML-onderdeel de voorafgaande titelset (element- of paginatitel):

```html
<title><%= title %></title>
```

## Een eenvoudige component voor een formulierveld maken {#creating-a-simple-form-field-component}

In dit voorbeeld wordt beschreven hoe u een component kunt maken die de metagegevens van een geladen element weergeeft en weergeeft.

1. Maak bijvoorbeeld een componentmap in de projectmap `/apps/geometrixx/components/samplemeta`.
1. Toevoegen `content.xml` met het volgende fragment:

   ```xml
   <?xml version="1.0" encoding="UTF-8"?>
   <jcr:root xmlns:sling="https://sling.apache.org/jcr/sling/1.0" xmlns:cq="https://www.day.com/jcr/cq/1.0" xmlns:jcr="https://www.jcp.org/jcr/1.0"
       jcr:primaryType="cq:Component"
       jcr:title="Image Dimension"
       sling:resourceSuperType="foundation/components/parbase"
       allowedParents="[*/parsys]"
       componentGroup="Asset Editor"/>
   ```

1. Toevoegen `samplemeta.jsp` met het volgende fragment:

   ```javascript
   <%--
   
     Sample metadata field component
   
   --%><%@ page import="com.day.cq.dam.api.Asset,
                    java.security.AccessControlException" %><%
   %><%@include file="/libs/foundation/global.jsp"%><%
   
       String value = "";
       String name = "dam:sampleMetadata";
       boolean readOnly = false;
   
       // If the form page is requested for an asset loadResource will be the asset.
       Resource loadResource = (Resource) request.getAttribute("cq.form.loadresource");
   
       if (loadResource != null) {
   
           // Determine if the loaded asset is read only.
           Session session = slingRequest.getResourceResolver().adaptTo(Session.class);
           try {
               session.checkPermission(loadResource.getPath(), "set_property");
               readOnly = false;
           }
           catch (AccessControlException ace) {
               // checkPermission throws exception if asset is read only
               readOnly = true;
           }
           catch (RepositoryException re) {}
   
           // Get the value of the metadata.
           Asset asset = loadResource.adaptTo(Asset.class);
           try {
               value = asset.getMetadata(name).toString();
           }
           catch (NullPointerException npe) {
               // no metadata dc:description available
           }
       }
   %>
   <div class="form_row">
       <div class="form_leftcol">
           <div class="form_leftcollabel">Sample Metadata</div>
       </div>
       <div class="form_rightcol">
           <%
           if (readOnly) {
               %><c:out value="<%= value %>"/><%
           }
           else {
               %><input class="text" type="text" name="./jcr:content/metadata/<%= name %>" value="<c:out value="<%= value %>" />"><%
           }%>
       </div>
   </div>
   ```

1. Als u de component beschikbaar wilt maken, moet u deze kunnen bewerken. To make a component editable, in CRXDE Lite, add a node `cq:editConfig` of primary type `cq:EditConfig`. U kunt alinea&#39;s verwijderen door een eigenschap met meerdere waarden `cq:actions` met één waarde van `DELETE` toe te voegen.

1. Navigeer naar de browser en schakel op de voorbeeldpagina (bijvoorbeeld `asseteditor.html`) over naar de ontwerpmodus en schakel de nieuwe component in voor het alineasysteem.

1. In de modus **Bewerken** is de nieuwe component (bijvoorbeeld **Voorbeeldmetadata**) nu beschikbaar in de sidekick (in de groep **Asset-editor**). Voeg de component in. Als u de metadata wilt opslaan, moet u deze toevoegen aan het metadataformulier.

## Opties voor metagegevens wijzigen {#modifying-metadata-options}

U kunt de naamruimten wijzigen die beschikbaar zijn in het [metagegevensformulier](assets-finder-editor.md#metadata-form-and-text-field-configuring-the-view-metadata-component).

De momenteel beschikbare metagegevens worden gedefinieerd in `/libs/dam/options/metadata`:

* Het eerste niveau in deze map bevat de naamruimten.
* De items binnen elke naamruimte vertegenwoordigen metagegevens, zoals de resultaten in een lokaal onderdeel.
* De inhoud van de metagegevens bevat de informatie voor het type en de opties voor meerdere waarden.

De opties kunnen worden overschreven in `/apps/dam/options/metadata`:

1. Kopieer de map van `/libs` naar `/apps`.

1. Items verwijderen, wijzigen of toevoegen.

>[!NOTE]
>
>Als u nieuwe naamruimten toevoegt, moeten deze worden geregistreerd in uw gegevensopslagruimte/CRX. Anders leidt het verzenden van het metagegevensformulier tot een fout.
