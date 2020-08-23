---
title: Aangepast formulier insluiten in externe webpagina
seo-title: Aangepast formulier insluiten in externe webpagina
description: Leer hoe u een adaptief formulier insluit in een externe webpagina
seo-description: Leer hoe u een adaptief formulier insluit in een externe HTML-webpagina
uuid: d81032dd-af80-4f4b-a717-ee1b89fd3d3d
products: SG_EXPERIENCEMANAGER/6.3/FORMS
topic-tags: author
discoiquuid: d739c6da-3b41-4452-8728-d7cd1a3ae20b
docset: aem65
translation-type: tm+mt
source-git-commit: 80b8571bf745b9e7d22d7d858cff9c62e9f8ed1e
workflow-type: tm+mt
source-wordcount: '979'
ht-degree: 0%

---


# Aangepast formulier insluiten in externe webpagina{#embed-adaptive-form-in-external-web-page}

U kunt adaptieve formulieren [insluiten in een AEM Sites-pagina](/help/forms/using/embed-adaptive-form-aem-sites.md) of een webpagina die buiten AEM wordt gehost. Het ingesloten adaptieve formulier is volledig functioneel en gebruikers kunnen het formulier invullen en verzenden zonder de pagina te verlaten. Hierdoor kan de gebruiker in de context van andere elementen op de webpagina blijven en tegelijkertijd met het formulier communiceren.

## Vereisten {#prerequisites}

Voer de volgende stappen uit voordat u een adaptief formulier insluit op een externe website

* Publiceer het adaptieve formulier dat moet worden ingesloten op de publicatieversie van de AEM Forms-server.
* Maak of identificeer een webpagina op uw website om het adaptieve formulier te hosten. Zorg ervoor dat de webpagina jQuery-bestanden kan [lezen vanaf een CDN](https://ajax.googleapis.com/ajax/libs/jquery/3.3.1/jquery.min.js) of dat er een lokale kopie van de jQuery is ingesloten. jQuery is vereist om een adaptief formulier te genereren.
* Wanneer AEM server en de webpagina zich op verschillende domeinen bevinden, voert u de stappen uit die in sectie worden vermeld, [zodat AEM Forms adaptieve formulieren kan leveren aan een interdomeinsite](#cross-site).

## Aangepast formulier insluiten {#embed-adaptive-form}

U kunt een adaptief formulier insluiten door een paar regels JavaScript in de webpagina in te voegen. De API in de code verzendt een HTTP-aanvraag naar de AEM server voor adaptieve formulierbronnen en injecteert het adaptieve formulier in de opgegeven formuliercontainer.

Het adaptieve formulier insluiten:

1. Maak een webpagina op uw website met de volgende code:

   ```html
   <!doctype html>
   <html>
     <head>
       <title>This is the title of the webpage!</title>
       <script src="https://ajax.googleapis.com/ajax/libs/jquery/3.3.1/jquery.min.js"></script>
     </head>
     <body>
     <div class="customafsection"/>
       <p>This section is replaced with the adaptive form.</p>
   
    <script>
    var options = {path:"/content/forms/af/locbasic.html", dataRef:"", themepath:"", CSS_Selector:".customafsection"};
    alert(options.path);
    var loadAdaptiveForm = function(options){
    //alert(options.path);
       if(options.path) {
           // options.path refers to the publish URL of the adaptive form
           // For Example: https:myserver:4503/content/forms/af/ABC, where ABC is the adaptive form
           // Note: If AEM server is running on a context path, the adaptive form URL must contain the context path
           var path = options.path;
           path += "/jcr:content/guideContainer.html";
           $.ajax({
               url  : path ,
               type : "GET",
               data : {
                   // Set the wcmmode to be disabled
                   wcmmode : "disabled"
                   // Set the data reference, if any
                  // "dataRef": options.dataRef
                   // Specify a different theme for the form object
                 //  "themeOverride" : options.themepath
               },
               async: false,
               success: function (data) {
                   // If jquery is loaded, set the inner html of the container
                   // If jquery is not loaded, use APIs provided by document to set the inner HTML but these APIs would not evaluate the script tag in HTML as per the HTML5 spec
                   // For example: document.getElementById().innerHTML
                   if(window.$ && options.CSS_Selector){
                       // HTML API of jquery extracts the tags, updates the DOM, and evaluates the code embedded in the script tag.
                       $(options.CSS_Selector).html(data);
                   }
               },
               error: function (data) {
                   // any error handler
               }
           });
       } else {
           if (typeof(console) !== "undefined") {
               console.log("Path of Adaptive Form not specified to loadAdaptiveForm");
           }
       }
    }(options);
   
    </script>
     </body>
   </html>
   ```

1. In de ingesloten code:

   * Wijzig de waarde van de variabele *options.path* met het pad van de publicatie-URL van het adaptieve formulier. Als de AEM server op een contextweg loopt, zorg ervoor dat URL het contextweg omvat. De bovenstaande code en het aanpassen van de locatie op dezelfde naamformulierserver zijn bijvoorbeeld gebaseerd op het contextpad van het adaptieve formulier /content/forms/af/locbasic.html.
   * Vervang *options.dataRef* met attributen om met URL over te gaan. Met de variabele dataref kunt u een adaptief formulier [](/help/forms/using/prepopulate-adaptive-form-fields.md)vooraf invullen.
   * Vervang *options.themePath* door het pad naar een ander thema dan het thema dat in het adaptieve formulier is geconfigureerd. U kunt ook het themapad opgeven met het aanvraagkenmerk.
   * CSS_Selector is de CSS-kiezer van de formuliercontainer waarin het adaptieve formulier is ingesloten. De CSS-kiezer in het bovenstaande voorbeeld is bijvoorbeeld de CSS-klasse .customafsection css.

Het adaptieve formulier is ingesloten in de webpagina. Bekijk het volgende in het ingesloten adaptieve formulier:

* Koptekst en voettekst in het oorspronkelijke adaptieve formulier worden niet opgenomen in het ingesloten formulier.
* Concepten en verzonden formulieren zijn beschikbaar op het tabblad Concepten en verzendingen in de Forms Portal.
* Verzendactie die is geconfigureerd op het oorspronkelijke adaptieve formulier, blijft behouden in het ingesloten formulier.
* Aangepaste formulierregels blijven behouden en werken volledig in het ingesloten formulier.
* De in het oorspronkelijke adaptieve formulier geconfigureerde ervaringstips en A/B-tests werken niet in het ingesloten formulier.
* Als Adobe Analytics op het oorspronkelijke formulier is geconfigureerd, worden de analysegegevens vastgelegd op de Adobe Analytics-server. Het is echter niet beschikbaar in het analyserapport van Forms.

## Voorbeeldtopologie {#sample-topology}

De externe webpagina die het adaptieve formulier insluit, verzendt aanvragen naar de AEM server, die zich doorgaans achter de firewall in een privénetwerk bevindt. Om ervoor te zorgen dat de verzoeken veilig aan de AEM server worden geleid, wordt het geadviseerd aan opstelling een omgekeerde volmachtsserver.

Laten we een voorbeeld bekijken van hoe u een Apache 2.4 reverse-proxyserver zonder verzender kunt instellen. In dit voorbeeld host u de AEM server met `/forms` contextpad en een kaart `/forms` voor de reverse-proxy. Het zorgt ervoor dat elke aanvraag voor `/forms` Apache-server naar de AEM-instantie wordt gestuurd. Deze topologiehulp vermindert het aantal regels bij de verzender laag aangezien al verzoek met `/forms` route aan de AEM server vooraf bepaald.

1. Open het `httpd.conf` configuratiebestand en verwijder de commentaarmarkering voor de volgende coderegels. U kunt deze coderegels ook toevoegen aan het bestand.

   ```text
   LoadModule proxy_html_module modules/mod_proxy_html.so
   LoadModule proxy_http_module modules/mod_proxy_http.so
   ```

1. Stel proxyregels in door de volgende coderegels in het `httpd-proxy.conf` configuratiebestand toe te voegen.

   ```text
   ProxyPass /forms https://[AEM_Instance]/forms
   ProxyPassReverse /forms https://[AEM_Instance]/forms
   ```

   Vervangen `[AEM_Instance]` door de publicatie-URL van de AEM server in de regels.

Als u de AEM server niet koppelt op een contextpad, gelden de proxyregels op de Apache-laag als volgt:

```text
ProxyPass /content https://<AEM_Instance>/content
ProxyPass /etc https://<AEM_Instance>/etc
ProxyPass /etc.clientlibs https://<AEM_Instance>/etc.clientlibs
# CSRF Filter
ProxyPass /libs/granite/csrf/token.json https://<AEM_Instance>/libs/granite/csrf/token.json

ProxyPassReverse /etc https://<AEM_Instance>/etc
ProxyPassReverse /etc.clientlibs https://<AEM_Instance>/etc.clientlibs
# written for thank you page and other URL present in AF during redirect
ProxyPassReverse /content https://<AEM_Instance>/content
```

>[!NOTE]
>
>Als u opstelling een andere topologie, ervoor zorgt dat u verzend toevoegt, vooraf instelt, en andere URLs aan de lijst van gewenste personen bij de verzender laag.

## Best practices {#best-practices}

Houd bij het insluiten van een adaptief formulier in een webpagina rekening met de volgende aanbevolen procedures:

* Zorg ervoor dat de opmaakregels die zijn gedefinieerd in de CSS van de webpagina geen conflict veroorzaken met de CSS van het formulierobject. Om conflicten te voorkomen, kunt u de CSS van de webpagina in het adaptieve formulierthema opnieuw gebruiken met AEM clientbibliotheek. Zie [Thema&#39;s in AEM Forms](../../forms/using/themes.md)voor informatie over het gebruik van de clientbibliotheek in adaptieve formulierthema&#39;s.
* Zorg dat de formuliercontainer op de webpagina de volledige vensterbreedte gebruikt. Hiermee zorgt u ervoor dat de CSS-regels die voor mobiele apparaten zijn geconfigureerd, zonder wijzigingen werken. Als de formuliercontainer niet de volledige vensterbreedte heeft, moet u aangepaste CSS schrijven om het formulier aan te passen aan verschillende mobiele apparaten.
* Gebruik `[getData](https://helpx.adobe.com/experience-manager/6-3/forms/javascript-api/GuideBridge.html)` API om de XML- of JSON-weergave van formuliergegevens op de client op te halen.
* Gebruik de API `[unloadAdaptiveForm](https://helpx.adobe.com/experience-manager/6-3/forms/javascript-api/GuideBridge.html)` om het adaptieve formulier te verwijderen uit HTML DOM.
* Opstelling de toegang-controle-oorsprong kopbal wanneer het verzenden van reactie van AEM server.

## AEM Forms toestaan om aangepaste formulieren te gebruiken voor een interdomeinsite {#cross-site}

1. Voor AEM auteurinstantie, ga naar AEM Manager van de Configuratie van de Console van het Web bij `https://'[server]:[port]'/system/console/configMgr`.
1. Zoek en open de **configuratie van het filter** Apache Sling Referrer.
1. Geef in het veld Toegestane gastheren het domein op waar de webpagina zich bevindt. Het laat de gastheer toe om POST verzoeken aan de AEM server te doen. U kunt ook de reguliere expressie gebruiken om een reeks externe toepassingsdomeinen op te geven.

