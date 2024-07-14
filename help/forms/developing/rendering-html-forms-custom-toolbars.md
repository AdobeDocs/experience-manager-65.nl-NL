---
title: HTML Forms renderen met CustomToolbars
description: Met de Forms-service kunt u een werkbalk aanpassen die wordt weergegeven met een HTML-formulier. U kunt een HTML-formulier met een aangepaste werkbalk weergeven met de Java API en een webservice-API.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/rendering_forms
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: operations
role: Developer
exl-id: 0b992b1c-3878-447a-bccc-7034aa3e98bc
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms,Document Services,APIs & Integrations
source-git-commit: d7b9e947503df58435b3fee85a92d51fae8c1d2d
workflow-type: tm+mt
source-wordcount: '2328'
ht-degree: 0%

---

# HTML Forms renderen met CustomToolbars {#rendering-html-forms-with-customtoolbars}

**de Steekproeven en de voorbeelden in dit document zijn slechts voor AEM Forms op milieu JEE.**

## HTML Forms renderen met aangepaste werkbalken {#rendering-html-forms-with-custom-toolbars}

Met de Forms-service kunt u een werkbalk aanpassen die wordt weergegeven met een HTML-formulier. Een werkbalk kan worden aangepast om de weergave te wijzigen door standaard CSS-stijlen te overschrijven en dynamisch gedrag toe te voegen door Java-scripts te overschrijven. Een werkbalk wordt aangepast met een XML-bestand met de naam fscmenu.xml. Standaard haalt de Forms-service dit bestand op van een intern opgegeven URI-locatie.

>[!NOTE]
>
>Deze URI-locatie bevindt zich in het bestand adobe-forms-core.jar, dat zich in het bestand adobe-forms-dsc.jar bevindt. Het bestand adobe-forms-dsc.jar staat in de map C:\Adobe\Adobe_Experience_Manager_forms\ (C:\ is de installatiemap). U kunt een hulpprogramma voor het uitpakken van bestanden, zoals Win RAR, gebruiken om de adobe te openen.

U kunt fscmenu.xml van deze plaats kopiëren, het wijzigen om aan uw vereisten te voldoen, en dan het in een plaats van douaneURI plaatsen. Vervolgens stelt u met de Forms Service API uitvoeringsopties in die resulteren in de Forms-service met behulp van het bestand fscmenu.xml van de opgegeven locatie. Deze acties resulteren in de Forms-service die een HTML-formulier met een aangepaste werkbalk weergeeft.

Naast het bestand fscmenu.xml moet u ook de volgende bestanden ophalen:

* fscmenu.js
* fscattachments.js
* fscmenu.css
* fscmenu-v.css
* fscmenu-ie.css
* fscdialog.css

fscJS is het Java-script dat aan elk knooppunt is gekoppeld. U moet er een opgeven voor het knooppunt `div#fscmenu` en optioneel voor `ul#fscmenuItem` -knooppunten. De JS-bestanden implementeren de kernfuncties van de werkbalk en de standaardbestanden werken.

fscCSS is een stijlpagina die aan een bepaalde knoop wordt geassocieerd. De stijlen in de CSS-bestanden geven de werkbalkweergave aan. *fscVCSS* is een stijlblad voor een verticale toolbar, die op de linkerzijde van de teruggegeven vorm van HTML wordt getoond. *fscIECSS* is een stijlblad dat voor HTML vormen wordt gebruikt die in Internet Explorer worden teruggegeven.

Controleer of naar alle bovenstaande bestanden wordt verwezen in het bestand fscmenu.xml. Dat wil zeggen dat u in het bestand fscmenu.xml URI-locaties opgeeft die naar deze bestanden verwijzen, zodat de Forms-service ze kan vinden. Deze bestanden zijn standaard beschikbaar op URI-locaties die beginnen met interne trefwoorden `FSWebRoot` of `ApplicationWebRoot` .

Als u de werkbalk wilt aanpassen, vervangt u de trefwoorden door het externe trefwoord `FSToolBarURI` te gebruiken. Dit sleutelwoord vertegenwoordigt URI die aan de dienst van Forms in runtime wordt overgegaan (deze benadering wordt getoond later in deze sectie).

U kunt ook de absolute locaties van deze JS- en CSS-bestanden opgeven, zoals https://www.mycompany.com/scripts/misc/fscmenu.js. In dit geval hoeft u het trefwoord `FSToolBarURI` niet te gebruiken.

>[!NOTE]
>
>Het wordt afgeraden om de manier waarop naar deze bestanden wordt verwezen, door elkaar te gebruiken. Er moet dus naar alle URI&#39;s worden verwezen door het trefwoord `FSToolBarURI` of een absolute locatie te gebruiken.

U kunt de JS- en CSS-bestanden verkrijgen door het bestand adobe-forms-&lt;appserver>.ear te openen. Open het bestand adobe-forms-res.war in dit bestand. Al deze bestanden staan in het WAR-bestand. Het bestand adobe-forms-&lt;appserver>.ear bevindt zich in de installatiemap voor AEM formulieren (C:\ is de installatiemap). U kunt de adobe-forms-&lt;appserver>.ear openen gebruikend een hulpmiddel van de dossierextractie zoals WinRAR.

De volgende XML-syntaxis toont een voorbeeld van het bestand fscmenu.xml.

```html
 <div id="fscmenu" fscJS="FSToolBarURI/scripts/fscmenu.js" fscCSS="FSToolBarURI/fscmenu.css" fscVCSS="FSToolBarURI/fscmenu-v.css" fscIECSS="FSToolBarURI/fscmenu-ie.css">
         <ul class="fscmenuItem" id="Home">
             <li>
                 <a href="#" fscTarget="_top" tabindex="1">Home</a>
             </li>
         </ul>
         <ul class="fscmenuItem" id="Upload" fscJS="FSToolBarURI/scripts/fscattachments.js" fscCSS="FSToolBarURI/fscdialog.css">
             <li>
                 <a tabindex="2">Upload Attachments</a>
                 <ul class="fscmenuPopup" id="fscUploadAttachments">
                     <li>
                         <a href="javascript:doUploadDialog();" tabindex="3">Add ...</a>
                     </li>
                     <li>
                         <a href="javascript:doDeleteDialog();" tabindex="4">Delete ...</a>
                     </li>
                 </ul>
             </li>
         </ul>
         <ul class="fscmenuItem" id="Download">
             <li>
                 <a tabindex="100">Download Attachments</a>
                 <ul class="fscmenuPopup">
                     <li>
                         <a tabindex="101">None available</a>
                     </li>
                 </ul>
             </li>
         </ul>
     </div>
```

>[!NOTE]
>
>De vette tekst vertegenwoordigt URIs aan de CSS en JS- dossiers die moeten worden van verwijzingen voorzien.

De volgende items beschrijven hoe u een werkbalk kunt aanpassen:

* Wijzig de waarden van de kenmerken `fscJS`, `fscCSS`, `fscVCSS` en `fscIECSS` (in het bestand fscmenu.xml) om de aangepaste locaties van de bestanden waarnaar wordt verwezen, weer te geven met een van de methoden die in deze sectie worden beschreven (bijvoorbeeld `fscJS="FSToolBarURI/scripts/fscmenu.js"`).
* Alle CSS- en JS-bestanden moeten worden opgegeven. Als geen van de bestanden wordt gewijzigd, geeft u de standaardmap op de aangepaste locatie op. U kunt de standaardbestanden verkrijgen door verschillende bestanden te openen, zoals in deze sectie wordt beschreven.
* Een absolute verwijzing (bijvoorbeeld https://www.example.com/scripts/custom-vertical-fscmenu.css) voor elk bestand is toegestaan.
* De JS- en CSS-bestanden die het knooppunt `div#fscmenu` nodig heeft, zijn essentieel voor de werkbalkfunctionaliteit. Afzonderlijke `ul#fscmenuItem` knooppunten kunnen JS- of CSS-bestanden ondersteunen of hebben dit niet.

**Veranderend de lokale waarde**

Als onderdeel van het aanpassen van een werkbalk kunt u de waarde voor de landinstelling van de werkbalk wijzigen. Dat wil zeggen dat u het in een andere taal kunt weergeven. In de volgende afbeelding ziet u een aangepaste werkbalk die in het Frans wordt weergegeven.

>[!NOTE]
>
>Het is niet mogelijk om een aangepaste werkbalk in meer dan één taal te maken. Werkbalken kunnen geen verschillende XML-bestanden gebruiken op basis van de landinstellingen.

Als u de landinstellingswaarde van een werkbalk wilt wijzigen, moet u ervoor zorgen dat het bestand fscmenu.xml de taal bevat die u wilt weergeven. De volgende syntaxis van XML toont het fscmenu.xml- dossier dat wordt gebruikt om een Franse toolbar te tonen.

```html
 <div id="fscmenu" fscJS="FSToolBarURI/scripts/fscmenu.js" fscCSS="FSToolBarURI/fscmenu.css" fscVCSS="FSToolBarURI/fscmenu-v.css" fscIECSS="FSToolBarURI/fscmenu-ie.css">
         <ul class="fscmenuItem" id="Home">
             <li>
                 <a href="#" fscTarget="_top" tabindex="1">Accueil</a>
             </li>
         </ul>
         <ul class="fscmenuItem" id="Upload" fscJS="FSToolBarURI/scripts/fscattachments.js" fscCSS="FSToolBarURI/fscdialog.css">
             <li>
                 <a tabindex="2">Télécharger les pièces jointes</a>
                 <ul class="fscmenuPopup" id="fscUploadAttachments">
                     <li>
                         <a href="javascript:doUploadDialog();" tabindex="3">Ajouter...</a>
                     </li>
                     <li>
                         <a href="javascript:doDeleteDialog();" tabindex="4">Supprimer...</a>
                     </li>
                 </ul>
             </li>
         </ul>
         <ul class="fscmenuItem" id="Download">
             <li>
                 <a tabindex="100">Télécharger les pièces jointes</a>
                 <ul class="fscmenuPopup">
                     <li>
                         <a tabindex="101">Aucune disponible</a>
                     </li>
                 </ul>
             </li>
         </ul>
     </div>
```

>[!NOTE]
>
>De snelstarthandleidingen die aan deze sectie zijn gekoppeld, gebruiken dit XML-bestand om een Franse aangepaste werkbalk weer te geven, zoals in de vorige illustratie wordt getoond.

Geef ook een geldige landinstellingswaarde op door de methode `setLocale` van het object `HTMLRenderSpec` aan te roepen en een tekenreekswaarde door te geven die de waarde van de landinstelling opgeeft. Geef bijvoorbeeld `fr_FR` door om Frans op te geven. De Forms-service wordt geleverd met gelokaliseerde werkbalken.

>[!NOTE]
>
>Voordat u een HTML-formulier genereert dat gebruikmaakt van een aangepaste werkbalk, moet u weten hoe HTML-formulieren worden gegenereerd. (Zie [ teruggevend Forms als HTML ](/help/forms/developing/rendering-forms-html.md).)

Voor meer informatie over de dienst van Forms, zie [ Verwijzing van de Diensten voor AEM Forms ](https://www.adobe.com/go/learn_aemforms_services_63).

### Overzicht van de stappen {#summary-of-steps}

Voer de volgende taken uit om een HTML-formulier te genereren dat een aangepaste werkbalk bevat:

1. Inclusief projectbestanden.
1. Maak een Forms Java API-object.
1. Verwijs naar een aangepast fsmenu-XML-bestand.
1. Een HTML-formulier weergeven.
1. Schrijf de gegevensstroom van het formulier naar de webbrowser van de client.

**omvat projectdossiers**

Neem de benodigde bestanden op in uw ontwikkelingsproject. Als u een clienttoepassing maakt met Java, neemt u de benodigde JAR-bestanden op. Als u webservices gebruikt, neemt u de proxybestanden op.

**creeer een voorwerp van Forms Java API**

Voordat u via programmacode een bewerking kunt uitvoeren die door de Forms-service wordt ondersteund, moet u een Forms-clientobject maken.

**Verwijzing een dossier van douane fsmenuXML**

Als u een HTML-formulier wilt weergeven dat een aangepaste werkbalk bevat, verwijst u naar een XML-bestand met fsmenu&#39;s dat de werkbalk beschrijft. (Deze sectie bevat twee voorbeelden van een fsmenu-XML-bestand.) Zorg er ook voor dat het bestand fscmenu.xml de locaties van alle bestanden waarnaar wordt verwezen correct opgeeft. Zoals eerder in deze sectie is vermeld, moet u ervoor zorgen dat in alle bestanden naar het trefwoord `FSToolBarURI` of naar de absolute locatie wordt verwezen.

**geef een vorm van HTML** terug

Als u een HTML-formulier wilt genereren, geeft u een formulierontwerp op dat in Designer is gemaakt en als XDP-bestand is opgeslagen. Selecteer ook een transformatietype HTML. U kunt bijvoorbeeld het transformatietype HTML opgeven waarmee een dynamische HTML wordt weergegeven voor Internet Explorer 5.0 of hoger.

Voor het weergeven van een HTML-formulier zijn ook waarden nodig, zoals URI-waarden, voor het weergeven van andere formuliertypen.

**schrijf de stroom van vormgegevens aan cliëntWeb browser**

Wanneer de Forms-service een HTML-formulier weergeeft, wordt een formuliergegevensstroom geretourneerd die u naar de webbrowser van de client moet schrijven om het HTML-formulier zichtbaar te maken voor gebruikers.

**zie ook**

[Een HTML-formulier met een aangepaste werkbalk weergeven met de Java API](#render-an-html-form-with-a-custom-toolbar-using-the-java-api)

[Een HTML-formulier met een aangepaste werkbalk weergeven met de webservice-API](#rendering-an-html-form-with-a-custom-toolbar-using-the-web-service-api)

[Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Forms Service API Quick Start](/help/forms/developing/forms-service-api-quick-starts.md#forms-service-api-quick-starts)

[Interactieve PDF forms renderen](/help/forms/developing/rendering-interactive-pdf-forms.md)

[Forms renderen als HTML](/help/forms/developing/rendering-forms-html.md)

[Webtoepassingen maken die Forms renderen](/help/forms/developing/creating-web-applications-renders-forms.md)

### Een HTML-formulier met een aangepaste werkbalk weergeven met de Java API {#render-an-html-form-with-a-custom-toolbar-using-the-java-api}

Een HTML-formulier met een aangepaste werkbalk weergeven met de Forms Service API (Java):

1. Projectbestanden opnemen

   Neem client-JAR-bestanden, zoals adobe-forms-client.jar, op in het klassenpad van uw Java-project.

1. Een Forms Java API-object maken

   * Maak een `ServiceClientFactory` -object dat verbindingseigenschappen bevat.
   * Maak een `FormsServiceClient` -object door de constructor ervan te gebruiken en het `ServiceClientFactory` -object door te geven.

1. Verwijzen naar een aangepast XML-bestand met een fsmenu

   * Maak een `HTMLRenderSpec` -object met behulp van de constructor.
   * Als u een HTML-formulier met een werkbalk wilt weergeven, roept u de methode `setHTMLToolbar` van het object `HTMLRenderSpec` aan en geeft u een waarde `HTMLToolbar` enum door. Als u bijvoorbeeld een verticale werkbalk HTML wilt weergeven, geeft u door `HTMLToolbar.Vertical` .
   * Geef de locatie van het XML-bestand van het fsmenu op door de methode `setToolbarURI` van het object `HTMLRenderSpec` aan te roepen en een tekenreekswaarde door te geven die de URI-locatie van het XML-bestand aangeeft.
   * Stel, indien van toepassing, de waarde van de landinstelling in door de methode van het `HTMLRenderSpec` -object `setLocale` aan te roepen en een tekenreekswaarde door te geven die de waarde van de landinstelling opgeeft. De standaardwaarde is Engels.

   >[!NOTE]
   >
   >Snel aan de slag die aan deze sectie worden geassocieerd plaatst deze waarde aan `fr_FR`*.*

1. Een HTML-formulier renderen

   Roep de methode `renderHTMLForm` van het object `FormsServiceClient` aan en geef de volgende waarden door:

   * Een tekenreekswaarde die de naam van het formulierontwerp opgeeft, inclusief de bestandsnaamextensie. Als u verwijst naar een formulierontwerp dat deel uitmaakt van een Forms-toepassing, moet u het volledige pad opgeven, bijvoorbeeld `Applications/FormsApplication/1.0/FormsFolder/Loan.xdp` .
   * Een `TransformTo` opsommingswaarde die het voorkeurstype HTML aangeeft. Als u bijvoorbeeld een HTML-formulier wilt genereren dat compatibel is met dynamic HTML voor Internet Explorer 5.0 of hoger, geeft u `TransformTo.MSDHTML` op.
   * Een `com.adobe.idp.Document` -object dat gegevens bevat die met het formulier moeten worden samengevoegd. Wanneer u geen gegevens wilt samenvoegen, geeft u een leeg `com.adobe.idp.Document` -object door.
   * Het `HTMLRenderSpec` -object dat HTML-runtime-opties opslaat.
   * Een tekenreekswaarde die de headerwaarde `HTTP_USER_AGENT` opgeeft, zoals `Mozilla/4.0 (compatible; MSIE 6.0; Windows NT 5.1; SV1; .NET CLR 1.1.4322)` .
   * Een `URLSpec` -object dat URI-waarden opslaat die vereist zijn om een HTML-formulier te genereren.
   * Een `java.util.HashMap` -object dat bestandsbijlagen opslaat. Dit is een optionele parameter en u kunt `null` opgeven als u geen bestanden aan het formulier wilt koppelen.

   De methode `renderHTMLForm` retourneert een `FormsResult` -object dat een formuliergegevensstroom bevat die naar de webbrowser van de client moet worden geschreven.

1. De formuliergegevensstroom naar de webbrowser van de client schrijven

   * Maak een `com.adobe.idp.Document` -object door de methode `FormsResult` object &#39;s `getOutputContent` aan te roepen.
   * Haal het inhoudstype van het object `com.adobe.idp.Document` op door de methode `getContentType` ervan aan te roepen.
   * Stel het inhoudstype van het `javax.servlet.http.HttpServletResponse` -object in door de methode `setContentType` ervan aan te roepen en het inhoudstype van het `com.adobe.idp.Document` -object door te geven.
   * Maak een `javax.servlet.ServletOutputStream` -object dat wordt gebruikt om de formuliergegevensstroom naar de webbrowser van de client te schrijven door de methode `javax.servlet.http.HttpServletResponse` object `getOutputStream` aan te roepen.
   * Maak een `java.io.InputStream` -object door de methode `com.adobe.idp.Document` object `getInputStream` aan te roepen.
   * Maak een bytearray en vul deze met de formuliergegevensstroom door de methode `read` van het object `InputStream` aan te roepen en de bytearray als een argument door te geven.
   * Roep de methode `write` van het object `javax.servlet.ServletOutputStream` aan om de gegevensstroom van het formulier naar de webbrowser van de client te verzenden. Geef de bytearray door aan de methode `write` .

**zie ook**

[Snel starten (SOAP modus): Een HTML-formulier weergeven met een aangepaste werkbalk met de Java API](/help/forms/developing/forms-service-api-quick-starts.md#quick-start-soap-mode-rendering-an-html-form-with-a-custom-toolbar-using-the-java-api)

[Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Een HTML-formulier met een aangepaste werkbalk weergeven met de webservice-API {#rendering-an-html-form-with-a-custom-toolbar-using-the-web-service-api}

Een HTML-formulier met een aangepaste werkbalk weergeven met de Forms Service API (webservice):

1. Projectbestanden opnemen

   * Maak Java-proxyklassen die gebruikmaken van de Forms-service WSDL.
   * Neem de Java-proxyklassen op in het klassenpad.

1. Een Forms Java API-object maken

   Maak een `FormsService` -object en stel de verificatiewaarden in.

1. Verwijzen naar een aangepast XML-bestand met een fsmenu

   * Maak een `HTMLRenderSpec` -object met behulp van de constructor.
   * Als u een HTML-formulier met een werkbalk wilt weergeven, roept u de methode `setHTMLToolbar` van het object `HTMLRenderSpec` aan en geeft u een waarde `HTMLToolbar` enum door. Als u bijvoorbeeld een verticale werkbalk HTML wilt weergeven, geeft u door `HTMLToolbar.Vertical` .
   * Geef de locatie van het XML-bestand van het fsmenu op door de methode `setToolbarURI` van het object `HTMLRenderSpec` aan te roepen en een tekenreekswaarde door te geven die de URI-locatie van het XML-bestand aangeeft.
   * Stel, indien van toepassing, de waarde van de landinstelling in door de methode van het `HTMLRenderSpec` -object `setLocale` aan te roepen en een tekenreekswaarde door te geven die de waarde van de landinstelling opgeeft. De standaardwaarde is Engels.

   >[!NOTE]
   >
   >Snel aan de slag die aan deze sectie worden geassocieerd plaatst deze waarde aan `fr_FR`*.*

1. Een HTML-formulier renderen

   Roep de methode `renderHTMLForm` van het object `FormsService` aan en geef de volgende waarden door:

   * Een tekenreekswaarde die de naam van het formulierontwerp opgeeft, inclusief de bestandsnaamextensie. Als u verwijst naar een formulierontwerp dat deel uitmaakt van een Forms-toepassing, moet u het volledige pad opgeven, bijvoorbeeld `Applications/FormsApplication/1.0/FormsFolder/Loan.xdp` .
   * Een `TransformTo` opsommingswaarde die het voorkeurstype HTML aangeeft. Als u bijvoorbeeld een HTML-formulier wilt genereren dat compatibel is met dynamic HTML voor Internet Explorer 5.0 of hoger, geeft u `TransformTo.MSDHTML` op.
   * Een `BLOB` -object dat gegevens bevat die met het formulier moeten worden samengevoegd. Geef `null` door als u geen gegevens wilt samenvoegen.
   * Het `HTMLRenderSpec` -object dat HTML-runtime-opties opslaat.
   * Een tekenreekswaarde die de headerwaarde `HTTP_USER_AGENT` opgeeft, zoals `Mozilla/4.0 (compatible; MSIE 6.0; Windows NT 5.1; SV1; .NET CLR 1.1.4322` . U kunt een lege tekenreeks doorgeven als u deze waarde niet wilt instellen.
   * Een `URLSpec` -object dat URI-waarden opslaat die vereist zijn om een HTML-formulier te genereren.
   * Een `java.util.HashMap` -object dat bestandsbijlagen opslaat. Deze parameter is optioneel en u kunt `null` opgeven als u geen bestanden aan het formulier wilt koppelen.
   * Een leeg `com.adobe.idp.services.holders.BLOBHolder` -object dat door de methode `renderHTMLForm` wordt gevuld. Met deze parameterwaarde wordt het gerenderde formulier opgeslagen.
   * Een leeg `com.adobe.idp.services.holders.BLOBHolder` -object dat door de methode `renderHTMLForm` wordt gevuld. In deze parameter worden de XML-uitvoergegevens opgeslagen.
   * Een leeg `javax.xml.rpc.holders.LongHolder` -object dat door de methode `renderHTMLForm` wordt gevuld. In dit argument wordt het aantal pagina&#39;s in het formulier opgeslagen.
   * Een leeg `javax.xml.rpc.holders.StringHolder` -object dat door de methode `renderHTMLForm` wordt gevuld. In dit argument wordt de waarde van de landinstelling opgeslagen.
   * Een leeg `javax.xml.rpc.holders.StringHolder` -object dat door de methode `renderHTMLForm` wordt gevuld. In dit argument wordt de gebruikte HTML-renderwaarde opgeslagen.
   * Een leeg `com.adobe.idp.services.holders.FormsResultHolder` -object dat de resultaten van deze bewerking bevat.

   Met de methode `renderHTMLForm` wordt het `com.adobe.idp.services.holders.FormsResultHolder` -object dat als laatste argumentwaarde wordt doorgegeven, gevuld met een formuliergegevensstroom die naar de webbrowser van de client moet worden geschreven.

1. De formuliergegevensstroom naar de webbrowser van de client schrijven

   * Maak een `FormResult` -object door de waarde van het gegevenslid van het `com.adobe.idp.services.holders.FormsResultHolder` object `value` op te halen.
   * Maak een `BLOB` -object dat formuliergegevens bevat door de methode `FormsResult` object `getOutputContent` aan te roepen.
   * Haal het inhoudstype van het object `BLOB` op door de methode `getContentType` ervan aan te roepen.
   * Stel het inhoudstype van het `javax.servlet.http.HttpServletResponse` -object in door de methode `setContentType` ervan aan te roepen en het inhoudstype van het `BLOB` -object door te geven.
   * Maak een `javax.servlet.ServletOutputStream` -object dat wordt gebruikt om de formuliergegevensstroom naar de webbrowser van de client te schrijven door de methode `javax.servlet.http.HttpServletResponse` object `getOutputStream` aan te roepen.
   * Maak een bytearray en vul deze door de methode `getBinaryData` van het object `BLOB` aan te roepen. Hierdoor wordt de inhoud van het `FormsResult` -object toegewezen aan de bytearray.
   * Roep de methode `write` van het object `javax.servlet.http.HttpServletResponse` aan om de gegevensstroom van het formulier naar de webbrowser van de client te verzenden. Geef de bytearray door aan de methode `write` .

**zie ook**

[AEM Forms aanroepen met Base64-codering](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-base64-encoding)
