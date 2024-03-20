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
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '2328'
ht-degree: 0%

---

# HTML Forms renderen met CustomToolbars {#rendering-html-forms-with-customtoolbars}

**Voorbeelden en voorbeelden in dit document gelden alleen voor AEM Forms in JEE-omgeving.**

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

fscJS is het Java-script dat aan elk knooppunt is gekoppeld. Er moet een `div#fscmenu` knooppunt en optioneel voor `ul#fscmenuItem` knooppunten. De JS-bestanden implementeren de kernfuncties van de werkbalk en de standaardbestanden werken.

fscCSS is een stijlpagina die aan een bepaalde knoop wordt geassocieerd. De stijlen in de CSS-bestanden geven de werkbalkweergave aan. *fscVCSS* Dit is een stijlpagina voor een verticale werkbalk, die links van het weergegeven HTML formulier wordt weergegeven. *fscIECSS* is een stijlpagina die wordt gebruikt voor HTML-formulieren die worden weergegeven in Internet Explorer.

Controleer of naar alle bovenstaande bestanden wordt verwezen in het bestand fscmenu.xml. Dat wil zeggen dat u in het bestand fscmenu.xml URI-locaties opgeeft die naar deze bestanden verwijzen, zodat de Forms-service ze kan vinden. Deze bestanden zijn standaard beschikbaar op URI-locaties die beginnen met interne trefwoorden `FSWebRoot` of `ApplicationWebRoot`.

Als u de werkbalk wilt aanpassen, vervangt u de trefwoorden met het externe trefwoord `FSToolBarURI`. Dit sleutelwoord vertegenwoordigt URI die aan de dienst van Forms in runtime wordt overgegaan (deze benadering wordt getoond later in deze sectie).

U kunt ook de absolute locaties van deze JS- en CSS-bestanden opgeven, zoals https://www.mycompany.com/scripts/misc/fscmenu.js. In deze situatie hoeft u de `FSToolBarURI` trefwoord.

>[!NOTE]
>
>Het wordt afgeraden om de manier waarop naar deze bestanden wordt verwezen, door elkaar te gebruiken. Er moet dus naar alle URI&#39;s worden verwezen door een van de `FSToolBarURI` of een absolute locatie.

U kunt de JS- en CSS-bestanden verkrijgen door de adobe-forms te openen&lt;appserver>.ear-bestand. Open het bestand adobe-forms-res.war in dit bestand. Al deze bestanden staan in het WAR-bestand. De adobe-formulieren&lt;appserver>.ear-bestand bevindt zich in de installatiemap voor AEM formulieren (C:\ is de installatiemap). U kunt de adobe-formulieren openen&lt;appserver>.ear die een hulpmiddel van de dossierextractie zoals WinRAR gebruikt.

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

* De waarden wijzigen van `fscJS`, `fscCSS`, `fscVCSS`, `fscIECSS` attributen (in het fscmenu.xml- dossier) om op de douaneplaatsen van de referenced dossiers door één van de methodes te wijzen die in deze sectie worden beschreven (bijvoorbeeld `fscJS="FSToolBarURI/scripts/fscmenu.js"`).
* Alle CSS- en JS-bestanden moeten worden opgegeven. Als geen van de bestanden wordt gewijzigd, geeft u de standaardmap op de aangepaste locatie op. U kunt de standaardbestanden verkrijgen door verschillende bestanden te openen, zoals in deze sectie wordt beschreven.
* Een absolute verwijzing (bijvoorbeeld https://www.example.com/scripts/custom-vertical-fscmenu.css) voor elk bestand is toegestaan.
* De JS- en CSS-bestanden `div#fscmenu` knooppunt is essentieel voor werkbalkfunctionaliteit. Individueel `ul#fscmenuItem` knooppunten kunnen al dan niet ondersteunende JS- of CSS-bestanden hebben.

**De lokale waarde wijzigen**

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

Geef ook een geldige waarde voor de landinstelling op door het dialoogvenster `HTMLRenderSpec` object `setLocale` en het doorgeven van een tekenreekswaarde die de waarde van de landinstelling opgeeft. Geef bijvoorbeeld `fr_FR` om Frans aan te geven. De Forms-service wordt geleverd met gelokaliseerde werkbalken.

>[!NOTE]
>
>Voordat u een HTML-formulier genereert dat gebruikmaakt van een aangepaste werkbalk, moet u weten hoe HTML-formulieren worden gegenereerd. (Zie [Forms renderen als HTML](/help/forms/developing/rendering-forms-html.md).)

Voor meer informatie over de Forms-service raadpleegt u [Services Reference for AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Overzicht van de stappen {#summary-of-steps}

Voer de volgende taken uit om een HTML-formulier te genereren dat een aangepaste werkbalk bevat:

1. Inclusief projectbestanden.
1. Maak een Forms Java API-object.
1. Verwijs naar een aangepast fsmenu-XML-bestand.
1. Een HTML-formulier weergeven.
1. Schrijf de gegevensstroom van het formulier naar de webbrowser van de client.

**Projectbestanden opnemen**

Neem de benodigde bestanden op in uw ontwikkelingsproject. Als u een clienttoepassing maakt met Java, neemt u de benodigde JAR-bestanden op. Als u webservices gebruikt, neemt u de proxybestanden op.

**Een Forms Java API-object maken**

Voordat u via programmacode een bewerking kunt uitvoeren die door de Forms-service wordt ondersteund, moet u een Forms-clientobject maken.

**Verwijzen naar een aangepast XML-bestand met een fsmenu**

Als u een HTML-formulier wilt weergeven dat een aangepaste werkbalk bevat, verwijst u naar een XML-bestand met fsmenu&#39;s dat de werkbalk beschrijft. (Deze sectie bevat twee voorbeelden van een fsmenu-XML-bestand.) Zorg er ook voor dat het bestand fscmenu.xml de locaties van alle bestanden waarnaar wordt verwezen correct opgeeft. Zoals eerder in deze sectie is vermeld, moet u ervoor zorgen dat naar alle bestanden wordt verwezen door de `FSToolBarURI` sleutelwoord of hun absolute plaatsen.

**Een HTML-formulier renderen**

Als u een HTML-formulier wilt genereren, geeft u een formulierontwerp op dat in Designer is gemaakt en als XDP-bestand is opgeslagen. Selecteer ook een transformatietype HTML. U kunt bijvoorbeeld het transformatietype HTML opgeven waarmee een dynamische HTML wordt weergegeven voor Internet Explorer 5.0 of hoger.

Voor het weergeven van een HTML-formulier zijn ook waarden nodig, zoals URI-waarden, voor het weergeven van andere formuliertypen.

**De formuliergegevensstroom naar de webbrowser van de client schrijven**

Wanneer de Forms-service een HTML-formulier weergeeft, wordt een formuliergegevensstroom geretourneerd die u naar de webbrowser van de client moet schrijven om het HTML-formulier zichtbaar te maken voor gebruikers.

**Zie ook**

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

   * Een `ServiceClientFactory` object dat verbindingseigenschappen bevat.
   * Een `FormsServiceClient` object door de constructor ervan te gebruiken en de `ServiceClientFactory` object.

1. Verwijzen naar een aangepast XML-bestand met een fsmenu

   * Een `HTMLRenderSpec` object met behulp van de constructor.
   * Als u een HTML-formulier wilt weergeven met een werkbalk, roept u de opdracht `HTMLRenderSpec` object `setHTMLToolbar` methode en een `HTMLToolbar` enum value. Als u bijvoorbeeld een verticale werkbalk HTML wilt weergeven, geeft u door `HTMLToolbar.Vertical`.
   * Geef de locatie van het fsmenu-XML-bestand op door het `HTMLRenderSpec` object `setToolbarURI` methode en het overgaan van een koordwaarde die de plaats van URI van het dossier van XML specificeert.
   * Stel, indien van toepassing, de waarde van de landinstelling in door de `HTMLRenderSpec` object `setLocale` en het doorgeven van een tekenreekswaarde die de waarde van de landinstelling opgeeft. De standaardwaarde is Engels.

   >[!NOTE]
   >
   >Met de snelstarthandleidingen die aan deze sectie zijn gekoppeld, wordt deze waarde ingesteld op `fr_FR`*.*

1. Een HTML-formulier renderen

   De `FormsServiceClient` object `renderHTMLForm` en geeft de volgende waarden door:

   * Een tekenreekswaarde die de naam van het formulierontwerp opgeeft, inclusief de bestandsnaamextensie. Als u naar een formulierontwerp verwijst dat deel uitmaakt van een Forms-toepassing, moet u het volledige pad opgeven, zoals `Applications/FormsApplication/1.0/FormsFolder/Loan.xdp`.
   * A `TransformTo` Enum value that specifies the HTML preferences type. Als u bijvoorbeeld een HTML-formulier wilt genereren dat compatibel is met dynamic HTML voor Internet Explorer 5.0 of hoger, geeft u `TransformTo.MSDHTML`.
   * A `com.adobe.idp.Document` object dat gegevens bevat die met het formulier moeten worden samengevoegd. Als u geen gegevens wilt samenvoegen, geeft u een lege waarde door `com.adobe.idp.Document` object.
   * De `HTMLRenderSpec` -object waarin HTML-runtime-opties zijn opgeslagen.
   * Een tekenreekswaarde die de `HTTP_USER_AGENT` koptekstwaarde, zoals `Mozilla/4.0 (compatible; MSIE 6.0; Windows NT 5.1; SV1; .NET CLR 1.1.4322)`.
   * A `URLSpec` object dat URI-waarden opslaat die vereist zijn om een HTML-formulier te genereren.
   * A `java.util.HashMap` object waarin bestandsbijlagen zijn opgeslagen. Dit is een optionele parameter en u kunt `null` als u geen bestanden aan het formulier wilt koppelen.

   De `renderHTMLForm` methode retourneert een `FormsResult` object dat een formuliergegevensstroom bevat die naar de webbrowser van de client moet worden geschreven.

1. De formuliergegevensstroom naar de webbrowser van de client schrijven

   * Een `com.adobe.idp.Document` door het object aan te roepen `FormsResult` object &#39;s `getOutputContent` methode.
   * Hiermee wordt het inhoudstype van het dialoogvenster `com.adobe.idp.Document` object aanroepen `getContentType` methode.
   * Stel de `javax.servlet.http.HttpServletResponse` inhoudstype van object door het aan te roepen `setContentType` en geeft u het inhoudstype van de `com.adobe.idp.Document` object.
   * Een `javax.servlet.ServletOutputStream` object dat wordt gebruikt om de formuliergegevensstroom naar de webbrowser van de client te schrijven door het aanroepen van de `javax.servlet.http.HttpServletResponse` object `getOutputStream` methode.
   * Een `java.io.InputStream` door het object aan te roepen `com.adobe.idp.Document` object `getInputStream` methode.
   * Maak een bytearray en vul deze met de formuliergegevensstroom door de `InputStream` object `read` en de bytearray doorgeven als een argument.
   * De `javax.servlet.ServletOutputStream` object `write` methode om de formuliergegevensstroom naar de webbrowser van de client te verzenden. Geef de bytearray door aan de `write` methode.

**Zie ook**

[Snel starten (SOAP-modus): een HTML-formulier weergeven met een aangepaste werkbalk met de Java API](/help/forms/developing/forms-service-api-quick-starts.md#quick-start-soap-mode-rendering-an-html-form-with-a-custom-toolbar-using-the-java-api)

[Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Een HTML-formulier met een aangepaste werkbalk weergeven met de webservice-API {#rendering-an-html-form-with-a-custom-toolbar-using-the-web-service-api}

Een HTML-formulier met een aangepaste werkbalk weergeven met de Forms Service API (webservice):

1. Projectbestanden opnemen

   * Maak Java-proxyklassen die gebruikmaken van de Forms-service WSDL.
   * Neem de Java-proxyklassen op in het klassenpad.

1. Een Forms Java API-object maken

   Een `FormsService` -object en stel verificatiewaarden in.

1. Verwijzen naar een aangepast XML-bestand met een fsmenu

   * Een `HTMLRenderSpec` object met behulp van de constructor.
   * Als u een HTML-formulier wilt weergeven met een werkbalk, roept u de opdracht `HTMLRenderSpec` object `setHTMLToolbar` methode en een `HTMLToolbar` enum value. Als u bijvoorbeeld een verticale werkbalk HTML wilt weergeven, geeft u door `HTMLToolbar.Vertical`.
   * Geef de locatie van het fsmenu-XML-bestand op door het `HTMLRenderSpec` object `setToolbarURI` methode en het overgaan van een koordwaarde die de plaats van URI van het dossier van XML specificeert.
   * Stel, indien van toepassing, de waarde van de landinstelling in door de `HTMLRenderSpec` object `setLocale` en het doorgeven van een tekenreekswaarde die de waarde van de landinstelling opgeeft. De standaardwaarde is Engels.

   >[!NOTE]
   >
   >Met de snelstarthandleidingen die aan deze sectie zijn gekoppeld, wordt deze waarde ingesteld op `fr_FR`*.*

1. Een HTML-formulier renderen

   De `FormsService` object `renderHTMLForm` en geeft de volgende waarden door:

   * Een tekenreekswaarde die de naam van het formulierontwerp opgeeft, inclusief de bestandsnaamextensie. Als u naar een formulierontwerp verwijst dat deel uitmaakt van een Forms-toepassing, moet u het volledige pad opgeven, zoals `Applications/FormsApplication/1.0/FormsFolder/Loan.xdp`.
   * A `TransformTo` Enum value that specifies the HTML preferences type. Als u bijvoorbeeld een HTML-formulier wilt genereren dat compatibel is met dynamic HTML voor Internet Explorer 5.0 of hoger, geeft u `TransformTo.MSDHTML`.
   * A `BLOB` object dat gegevens bevat die met het formulier moeten worden samengevoegd. Als u geen gegevens wilt samenvoegen, geeft u `null`.
   * De `HTMLRenderSpec` -object waarin HTML-runtime-opties zijn opgeslagen.
   * Een tekenreekswaarde die de `HTTP_USER_AGENT` koptekstwaarde, zoals `Mozilla/4.0 (compatible; MSIE 6.0; Windows NT 5.1; SV1; .NET CLR 1.1.4322`). U kunt een lege tekenreeks doorgeven als u deze waarde niet wilt instellen.
   * A `URLSpec` object dat URI-waarden opslaat die vereist zijn om een HTML-formulier te genereren.
   * A `java.util.HashMap` object waarin bestandsbijlagen zijn opgeslagen. Deze parameter is optioneel en u kunt `null` als u geen bestanden aan het formulier wilt toevoegen.
   * Een leeg `com.adobe.idp.services.holders.BLOBHolder` object dat wordt gevuld door het `renderHTMLForm` methode. Met deze parameterwaarde wordt het gerenderde formulier opgeslagen.
   * Een leeg `com.adobe.idp.services.holders.BLOBHolder` object dat wordt gevuld door het `renderHTMLForm` methode. In deze parameter worden de XML-uitvoergegevens opgeslagen.
   * Een leeg `javax.xml.rpc.holders.LongHolder` object dat wordt gevuld door het `renderHTMLForm` methode. In dit argument wordt het aantal pagina&#39;s in het formulier opgeslagen.
   * Een leeg `javax.xml.rpc.holders.StringHolder` object dat wordt gevuld door het `renderHTMLForm` methode. In dit argument wordt de waarde van de landinstelling opgeslagen.
   * Een leeg `javax.xml.rpc.holders.StringHolder` object dat wordt gevuld door het `renderHTMLForm` methode. In dit argument wordt de gebruikte HTML-renderwaarde opgeslagen.
   * Een leeg `com.adobe.idp.services.holders.FormsResultHolder` -object dat de resultaten van deze bewerking zal bevatten.

   De `renderHTMLForm` wordt de `com.adobe.idp.services.holders.FormsResultHolder` object dat wordt doorgegeven als de laatste argumentwaarde met een formuliergegevensstroom die naar de webbrowser van de client moet worden geschreven.

1. De formuliergegevensstroom naar de webbrowser van de client schrijven

   * Een `FormResult` object door de waarde van het object op te halen `com.adobe.idp.services.holders.FormsResultHolder` object `value` lid.
   * Een `BLOB` object dat formuliergegevens bevat door het `FormsResult` object `getOutputContent` methode.
   * Hiermee wordt het inhoudstype van het dialoogvenster `BLOB` object aanroepen `getContentType` methode.
   * Stel de `javax.servlet.http.HttpServletResponse` inhoudstype van object door het aan te roepen `setContentType` en geeft u het inhoudstype van de `BLOB` object.
   * Een `javax.servlet.ServletOutputStream` object dat wordt gebruikt om de formuliergegevensstroom naar de webbrowser van de client te schrijven door het aanroepen van de `javax.servlet.http.HttpServletResponse` object `getOutputStream` methode.
   * Maak een bytearray en vul deze door het `BLOB` object `getBinaryData` methode. Deze taak wijst de inhoud van toe `FormsResult` object naar de bytearray.
   * De `javax.servlet.http.HttpServletResponse` object `write` methode om de formuliergegevensstroom naar de webbrowser van de client te verzenden. Geef de bytearray door aan de `write` methode.

**Zie ook**

[AEM Forms aanroepen met Base64-codering](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-base64-encoding)
