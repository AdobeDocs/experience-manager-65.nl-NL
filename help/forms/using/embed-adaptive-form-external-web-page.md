---
title: Aangepast formulier insluiten in externe webpagina
description: Leer hoe u een adaptief formulier insluit in een externe webpagina
products: SG_EXPERIENCEMANAGER/6.3/FORMS
topic-tags: author
docset: aem65
feature: Adaptive Forms,Foundation Components
exl-id: 2a237f74-fdfc-4e28-841c-f69afb7b99cf
solution: Experience Manager, Experience Manager Forms
role: User, Developer
source-git-commit: d7b9e947503df58435b3fee85a92d51fae8c1d2d
workflow-type: tm+mt
source-wordcount: '1028'
ht-degree: 0%

---

# Aangepast formulier insluiten in externe webpagina{#embed-adaptive-form-in-external-web-page}

<span class="preview"> de Adobe adviseert gebruikend de moderne en verlengbare gegevens vangen [ Componenten van de Kern ](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/introduction.html) voor [ het creëren van nieuwe Aangepaste Forms ](/help/forms/using/create-an-adaptive-form-core-components.md) of [ het toevoegen van Aangepaste Forms aan de pagina&#39;s van AEM Sites ](/help/forms/using/create-or-add-an-adaptive-form-to-aem-sites-page.md). Deze componenten betekenen een aanzienlijke vooruitgang in de aanmaak van Adaptive Forms en zorgen voor indrukwekkende gebruikerservaring. In dit artikel wordt een oudere aanpak beschreven voor het ontwerpen van Adaptive Forms met behulp van stichtingscomponenten. </span>

U kunt [ aangepaste vormen in een pagina van AEM Sites ](/help/forms/using/embed-adaptive-form-aem-sites.md) of een Web-pagina inbedden die buiten AEM wordt ontvangen. Het ingesloten adaptieve formulier is volledig functioneel en gebruikers kunnen het formulier invullen en verzenden zonder de pagina te verlaten. Hierdoor kan de gebruiker in de context van andere elementen op de webpagina blijven en tegelijkertijd met het formulier communiceren.

## Vereisten {#prerequisites}

Voer de volgende stappen uit voordat u een adaptief formulier insluit op een externe website

* Publish het adaptieve formulier dat moet worden ingesloten in het Publish-exemplaar van de AEM Forms Server.
* Maak of identificeer een webpagina op uw website waarop u het adaptieve formulier kunt hosten. Zorg ervoor dat webpage jQuery- dossiers van CDN [ kan ](https://ajax.googleapis.com/ajax/libs/jquery/3.3.1/jquery.min.js) lezen of een lokaal exemplaar van ingebedde jQuery heeft. jQuery is vereist om een adaptief formulier te genereren.
* Wanneer de AEM server en de Web-pagina op verschillende domeinen zijn, voer de stappen in sectie worden vermeld uit, [ laat AEM Forms toe om adaptieve vormen aan een dwars-domeinplaats ](#cross-site) te dienen.

## Aangepast formulier insluiten {#embed-adaptive-form}

U kunt een adaptief formulier insluiten door een paar regels JavaScript op de webpagina in te voegen. De API in de code verzendt een HTTP-aanvraag naar de AEM server voor adaptieve formulierbronnen en injecteert het adaptieve formulier in de opgegeven formuliercontainer.

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
           // options.path refers to the path of the adaptive form
           // For Example: /content/forms/af/ABC, where ABC is the adaptive form
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

   * Verander de waarde van de {*variabele 0} options.path met de weg van publiceren URL van de adaptieve vorm.* Als de AEM server op een contextweg loopt, zorg ervoor dat URL het contextweg omvat. Vermeld altijd de volledige naam van het adaptieve formulier, inclusief de extensie. De bovenstaande code en het adaptieve formulier zijn bijvoorbeeld aanwezig op dezelfde AEM Forms Server, zodat in het voorbeeld het contextpad van het adaptieve formulier `/content/forms/af/locbasic.html` wordt gebruikt.
   * Vervang *options.dataRef* met attributen om met URL over te gaan. U kunt de dataref variabele gebruiken aan [ vooraf instelt een adaptieve vorm ](/help/forms/using/prepopulate-adaptive-form-fields.md).
   * Vervang *options.themePath* met de weg aan een thema buiten het thema dat in de adaptieve vorm wordt gevormd. U kunt ook het themapad opgeven met het aanvraagkenmerk.
   * CSS_Selector is de CSS-kiezer van de formuliercontainer waarin het adaptieve formulier is ingesloten. De CSS-kiezer in het bovenstaande voorbeeld is bijvoorbeeld de CSS-klasse .customafsection css.

Het adaptieve formulier is ingesloten in de webpagina. Bekijk het volgende in het ingesloten adaptieve formulier:

* De kop- en voettekst in het oorspronkelijke adaptieve formulier worden niet opgenomen in het ingesloten formulier.
* Concepten en verzonden formulieren zijn beschikbaar op het tabblad Concepten en verzendingen in de Forms Portal.
* De handeling Verzenden die op het oorspronkelijke adaptieve formulier is geconfigureerd, blijft behouden in het ingesloten formulier.
* Aangepaste formulierregels blijven behouden en werken volledig in het ingesloten formulier.
* Gericht op ervaring en A/B-tests geconfigureerd in het oorspronkelijke adaptieve formulier werken niet in het ingesloten formulier.
* Als Adobe Analytics op het oorspronkelijke formulier is geconfigureerd, worden de analysegegevens vastgelegd door de Adobe Analytics-server. Het is echter niet beschikbaar in het analyserapport van Forms.

## Voorbeeldtopologie {#sample-topology}

De externe webpagina die het adaptieve formulier insluit, verzendt aanvragen naar de AEM server, die zich doorgaans achter de firewall in een privénetwerk bevindt. Om ervoor te zorgen dat de verzoeken veilig aan de AEM server worden geleid, wordt het geadviseerd aan opstelling een omgekeerde volmachtsserver.

Laten we een voorbeeld bekijken van hoe u een Apache 2.4 reverse-proxyserver zonder Dispatcher kunt instellen. In dit voorbeeld host u de AEM server met `/forms` contextpad en -toewijzing `/forms` voor de reverse-proxy. Zo zorgt u ervoor dat aanvragen voor `/forms` op de Apache-server naar de AEM-instantie worden gestuurd. Deze topologie helpt om het aantal regels op de laag van Dispatcher te verminderen aangezien al verzoek met `/forms` route aan de AEM server vooraf bepaald.

1. Open het configuratiebestand van `httpd.conf` en verwijder de commentaarmarkering voor de volgende coderegels. U kunt deze coderegels ook toevoegen aan het bestand.

   ```text
   LoadModule proxy_html_module modules/mod_proxy_html.so
   LoadModule proxy_http_module modules/mod_proxy_http.so
   ```

1. Stel proxyregels in door de volgende coderegels toe te voegen in het configuratiebestand van `httpd-proxy.conf` .

   ```text
   ProxyPass /forms https://[AEM_Instance]/forms
   ProxyPassReverse /forms https://[AEM_Instance]/forms
   ```

   Vervang `[AEM_Instance]` door de publicatie-URL van de AEM server in de regels.

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
>Als u opstelling een andere topologie, ervoor zorgt dat u verzend toevoegt, vooraf instelt, en andere URLs aan de lijst van gewenste personen bij de laag van Dispatcher.

## Aanbevolen procedures {#best-practices}

Houd bij het insluiten van een adaptief formulier in een webpagina rekening met de volgende aanbevolen procedures:

* Zorg ervoor dat de opmaakregels die zijn gedefinieerd in de CSS van de webpagina geen conflict veroorzaken met de CSS van het formulierobject. Om conflicten te voorkomen, kunt u de CSS van de webpagina in het adaptieve formulierthema hergebruiken met de AEM clientbibliotheek. Voor informatie over het gebruiken van de cliëntbibliotheek in adaptieve vormthema&#39;s, zie [ Thema&#39;s in AEM Forms ](../../forms/using/themes.md).
* Zorg dat de formuliercontainer op de webpagina de volledige vensterbreedte gebruikt. Hiermee zorgt u ervoor dat de CSS-regels die voor mobiele apparaten zijn geconfigureerd, zonder wijzigingen werken. Als de formuliercontainer niet de volledige vensterbreedte heeft, moet u aangepaste CSS schrijven om het formulier aan te passen aan verschillende mobiele apparaten.
* Gebruik `[getData](https://helpx.adobe.com/experience-manager/6-3/forms/javascript-api/GuideBridge.html)` API om de XML- of JSON-weergave van formuliergegevens op de client op te halen.
* Gebruik de `[unloadAdaptiveForm](https://helpx.adobe.com/experience-manager/6-3/forms/javascript-api/GuideBridge.html)` -API om het adaptieve formulier van HTML DOM te verwijderen.
* Opstelling de toegang-controle-oorsprong kopbal wanneer het verzenden van een reactie van een AEM server.

## AEM Forms toestaan om adaptieve formulieren te gebruiken voor een interdomeinsite {#cross-site}

1. Ga bij AEM publicatieexemplaar naar AEM Web Console Configuration Manager op `https://'[server]:[port]'/system/console/configMgr` .
1. Zoek en open de **configuratie van de Filter van de Verwijzing van 0} Apache het Verdelen.**
1. Geef in het veld Toegestane gastheren het domein op waar de webpagina zich bevindt. Het laat de gastheer toe om POST verzoeken aan de AEM server te doen. U kunt ook de reguliere expressie gebruiken om een reeks externe toepassingsdomeinen op te geven.
