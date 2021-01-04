---
title: Interactieve PDF forms renderen
seo-title: Interactieve PDF forms renderen
description: Met de Forms-service kunt u interactieve PDF forms renderen naar clientapparaten, meestal webbrowsers, om informatie van gebruikers te verzamelen. U kunt de dienst van Forms gebruiken om interactieve vormen terug te geven gebruikend Java API en de Dienst API van het Web.
seo-description: Met de Forms-service kunt u interactieve PDF forms renderen naar clientapparaten, meestal webbrowsers, om informatie van gebruikers te verzamelen. U kunt de dienst van Forms gebruiken om interactieve vormen terug te geven gebruikend Java API en de Dienst API van het Web.
uuid: df2a4dc8-f19e-49de-850f-85a204102631
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/rendering_forms
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: operations
discoiquuid: 3cb307ec-9b7b-4f03-b860-48553ccee746
translation-type: tm+mt
source-git-commit: 07889ead2ae402b5fb738ca08c7efe076ef33e44
workflow-type: tm+mt
source-wordcount: '2514'
ht-degree: 0%

---


# Interactieve PDF forms renderen {#rendering-interactive-pdf-forms}

De Forms-service rendert interactieve PDF forms naar clientapparaten, meestal webbrowsers, om informatie van gebruikers te verzamelen. Nadat een interactief formulier is gegenereerd, kan een gebruiker gegevens invoeren in formuliervelden en op een verzendknop op het formulier klikken om informatie terug te sturen naar de Forms-service. Een interactief PDF-formulier is alleen zichtbaar als Adobe Reader of Acrobat is geïnstalleerd op de computer die als host fungeert voor de webbrowser van de client.

>[!NOTE]
>
>Voordat u een formulier kunt genereren met de Forms-service, moet u eerst een formulierontwerp maken. Doorgaans wordt een formulierontwerp gemaakt in Designer en opgeslagen als een XDP-bestand. Zie [Forms Designer](https://www.adobe.com/go/learn_aemforms_designer_63) voor informatie over het maken van een formulierontwerp.

**Voorbeeldtoepassing van een lening**

Er wordt een voorbeeldtoepassing voor leningen geïntroduceerd om aan te tonen hoe de Forms-service interactieve formulieren gebruikt om informatie van gebruikers te verzamelen. Met deze toepassing kan een gebruiker een formulier invullen met gegevens die nodig zijn om een lening te beveiligen en vervolgens gegevens verzenden naar de Forms-service. In het volgende diagram wordt de logische stroom van de toepassing van de lening weergegeven.

![ri_ri_finsrv_loanapp_v1](assets/ri_ri_finsrv_loanapp_v1.png)

In de volgende tabel worden de stappen in dit diagram beschreven.

<table>
 <thead>
  <tr>
   <th><p>Stap</p></th>
   <th><p>Beschrijving</p></th>
  </tr>
 </thead>
 <tbody>
  <tr>
   <td><p>1</p></td>
   <td><p>De Java Server <code>GetLoanForm</code> wordt aangeroepen vanuit een HTML-pagina. </p></td>
  </tr>
  <tr>
   <td><p>2</p></td>
   <td><p>De Java Server <code>GetLoanForm</code> gebruikt de Forms Service Client API om het leningformulier te genereren naar de clientwebbrowser. (Zie <a href="#render-an-interactive-pdf-form-using-the-java-api">Een interactief PDF-formulier renderen met de Java API</a>.)</p></td>
  </tr>
  <tr>
   <td><p>3</p></td>
   <td><p>Nadat de gebruiker het leningformulier heeft ingevuld en op de verzendknop klikt, worden de gegevens verzonden naar de Java Server. <code>HandleData</code> (Zie <i>"Vormgeving van leningen"</i>.)</p></td>
  </tr>
  <tr>
   <td><p>4</p></td>
   <td><p>De Java Server <code>HandleData</code> gebruikt de Forms Service Client API om de formulierverzending te verwerken en formuliergegevens op te halen. De gegevens worden dan opgeslagen in een ondernemingsgegevensbestand. (Zie <a href="/help/forms/developing/handling-submitted-forms.md#handling-submitted-forms">Ingediende Forms verwerken</a>.)</p></td>
  </tr>
  <tr>
   <td><p>5</p></td>
   <td><p>Een bevestigingsformulier wordt teruggestuurd naar de webbrowser. Gegevens zoals de voor- en achternaam van de gebruiker worden met het formulier samengevoegd voordat het wordt gegenereerd. (Zie <a href="/help/forms/developing/prepopulating-forms-flowable-layouts.md">Forms vooraf vullen met stroombare layouts</a>.)</p></td>
  </tr>
 </tbody>
</table>

**Lijnformulier**

Dit interactieve leningformulier wordt gegenereerd door Java Servlet van de voorbeeldtoepassing.`GetLoanForm`

![ri_ri_lanform](assets/ri_ri_loanform.png)

**Bevestigingsformulier**

Dit formulier wordt gegenereerd door de Java Servlet van de voorbeeldtoepassing.`HandleData`

![ri_ri_confirm](assets/ri_ri_confirm.png)

Met de Java Server `HandleData` wordt dit formulier vooraf ingevuld met de voor- en achternaam van de gebruiker en met de hoeveelheid. Nadat het formulier vooraf is ingevuld, wordt het naar de webbrowser van de client verzonden. (Zie [Forms vooraf vullen met stroombare layouts](/help/forms/developing/prepopulating-forms-flowable-layouts.md))

**Java Servlets**

De voorbeeldtoepassing voor leningen is een voorbeeld van een Forms-servicetoepassing die als Java Servlet bestaat. Een Java Server is een Java-programma dat wordt uitgevoerd op een J2EE-toepassingsserver, zoals WebSphere, en bevat Forms Service Client API-code.

De volgende code toont de syntaxis van een Java-server met de naam GetLoanForm:

```java
     public class GetLoanForm extends HttpServlet implements Servlet {
         public void doGet(HttpServletRequest req, HttpServletResponse resp
         throws ServletException, IOException {

         }
         public void doPost(HttpServletRequest req, HttpServletResponse resp
         throws ServletException, IOException {

             }
```

Normaal gesproken plaatst u geen Forms Service Client API-code binnen een Java Server `doGet`- of `doPost`-methode. Het is beter programmeringspraktijk om deze code binnen een afzonderlijke klasse te plaatsen, de klasse van binnen de `doPost` methode (of `doGet` methode) te concretiseren, en de aangewezen methodes te roepen. Voor de beknoptheid van de code worden de codevoorbeelden in deze sectie echter tot een minimum beperkt en worden codevoorbeelden in de methode `doPost` geplaatst.

>[!NOTE]
>
>Zie [Referentiehandleiding voor services voor AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63) voor meer informatie over de Forms-service.

**Overzicht van de stappen**

Voer de volgende taken uit om een interactief PDF-formulier te genereren:

1. Inclusief projectbestanden.
1. Maak een Forms Client API-object.
1. Geef URI-waarden op.
1. Bestanden aan het formulier koppelen (optioneel).
1. Een interactief PDF-formulier renderen.
1. Schrijf de gegevensstroom van het formulier naar de webbrowser van de client.

**Projectbestanden opnemen**

Neem de benodigde bestanden op in uw ontwikkelingsproject. Als u een clienttoepassing maakt met Java, neemt u de benodigde JAR-bestanden op. Als u webservices gebruikt, dient u de proxybestanden op te nemen.

**Een Forms Client API-object maken**

Voordat u een Forms Service Client API-bewerking programmatisch kunt uitvoeren, moet u een Forms Client API-object maken. Als u de Java API gebruikt, maakt u een `FormsServiceClient`-object. Als u de Forms-API voor webservices gebruikt, maakt u een `FormsService`-object.

**URI-waarden opgeven**

U kunt URI-waarden opgeven die de Forms-service nodig heeft om een formulier te genereren. Er kan naar een formulierontwerp worden verwezen dat is opgeslagen als onderdeel van een Forms-toepassing met de URI-waarde `repository:///` van de inhoudsbasis. Neem bijvoorbeeld het volgende formulierontwerp met de naam *Loan.xdp* in een Forms-toepassing met de naam *FormsApplication*:

![ri_ri_formrepository](assets/ri_ri_formrepository.png)

Als u toegang wilt krijgen tot dit formulierontwerp, geeft u `Applications/FormsApplication/1.0/FormsFolder/Loan.xdp` op als de formuliernaam (de eerste parameter die is doorgegeven aan de methode `renderPDFForm`) en `repository:///` als de URI-waarde van de inhoudsbasis.

>[!NOTE]
>
>Zie [Workbench Help](https://www.adobe.com/go/learn_aemforms_workbench_63) voor informatie over het maken van een Forms-toepassing met Workbench.

Het pad naar een bron in een Forms-toepassing is:

`Applications/Application-name/Application-version/Folder.../Filename`

De volgende waarden tonen enkele voorbeelden van URI-waarden:

* Applications/AppraisalReport/1.0/Forms/FullForm.xdp
* Applications/AnotherApp/1.1/Assets/picture.jpg
* Applications/SomeApp/2.0/Resources/Data/XSDs/MyData.xsd

Wanneer u een interactief formulier genereert, kunt u URI-waarden definiëren, zoals de doel-URL waarnaar de formuliergegevens worden gepost. De doel-URL kan op een van de volgende manieren worden gedefinieerd:

* Op de knop Verzenden tijdens het ontwerpen van het formulierontwerp in Designer
* Door de Forms Service Client API te gebruiken

Als de doel-URL is gedefinieerd in het formulierontwerp, mag u deze niet overschrijven met de Forms Service Client API. Met andere woorden, als u de doel-URL instelt met de Forms API, wordt de opgegeven URL in het formulierontwerp teruggezet naar de URL die is opgegeven met de API. Als u het PDF-formulier wilt verzenden naar de doel-URL die in het formulierontwerp is opgegeven, stelt u de doel-URL programmatisch in op een lege tekenreeks.

Als u een formulier hebt dat een verzendknop en een berekeningsknop bevat (met een overeenkomstig script dat op de server wordt uitgevoerd), kunt u de URL programmatisch definiëren waarnaar het formulier wordt verzonden om het script uit te voeren. Met de knop Verzenden op het formulierontwerp geeft u de URL op waarnaar de formuliergegevens worden verzonden. (Zie [Formuliergegevens berekenen](/help/forms/developing/calculating-form-data.md).)

>[!NOTE]
>
>In plaats van een URL-waarde op te geven die naar een XDP-bestand verwijst, kunt u ook een `com.adobe.idp.Document`-instantie doorgeven aan de Forms-service. Het `com.adobe.idp.Document`-exemplaar bevat een formulierontwerp. (Zie [Documenten doorgeven aan de Forms Service](/help/forms/developing/passing-documents-forms-service.md).)

**Bestanden aan het formulier koppelen**

U kunt bestanden aan een formulier koppelen. Wanneer u een PDF-formulier met bestandsbijlagen genereert, kunnen gebruikers de bestandsbijlagen in Acrobat ophalen via het venster Bestandsbijlage. U kunt verschillende bestandstypen aan een formulier koppelen, zoals een tekstbestand, of aan een binair bestand, zoals een JPG-bestand.

>[!NOTE]
>
>Het koppelen van bestandsbijlagen aan een formulier is optioneel.

**Een interactief PDF-formulier renderen**

Als u een formulier wilt genereren, gebruikt u een formulierontwerp dat in Designer is gemaakt en als XDP- of PDF-bestand is opgeslagen. U kunt ook een formulier genereren dat met Acrobat is gemaakt en als PDF-bestand is opgeslagen. Als u een interactief PDF-formulier wilt genereren, roept u de methode `FormsServiceClient` of `renderPDFForm` van het object aan.`renderPDFForm2`

`renderPDFForm` gebruikt een `URLSpec` voorwerp. De inhoudsbasis wordt aan het XDP-bestand doorgegeven aan de Forms-service met behulp van de methode `URLSpec` van het object. `setContentRootURI` De naam van het formulierontwerp ( `formQuery`) wordt doorgegeven als een afzonderlijke parameterwaarde. De twee waarden worden samengevoegd om de absolute verwijzing naar het formulierontwerp te verkrijgen.

De methode `renderPDFForm2` accepteert een `com.adobe.idp.Document`-instantie die het XDP- of PDF-document bevat dat moet worden gerenderd.

>[!NOTE]
>
>De runtime-optie voor gecodeerde PDF kan niet worden ingesteld als het invoerdocument een PDF-document is. Als het invoerbestand een XDP-bestand is, kunt u de optie Gecodeerde PDF instellen.

## Een interactief PDF-formulier renderen met de Java API {#render-an-interactive-pdf-form-using-the-java-api}

Een interactief PDF-formulier renderen met de Forms API (Java):

1. Projectbestanden opnemen

   Neem client-JAR-bestanden, zoals adobe-forms-client.jar, op in het klassenpad van uw Java-project.

1. Een Forms Client API-object maken

   * Maak een `ServiceClientFactory`-object dat verbindingseigenschappen bevat.
   * Maak een `FormsServiceClient`-object door de constructor ervan te gebruiken en het object `ServiceClientFactory` door te geven.

1. URI-waarden opgeven

   * Maak een object `URLSpec` waarin URI-waarden worden opgeslagen met behulp van de constructor.
   * Roep de methode `URLSpec` van het object `setApplicationWebRoot` aan en geef een tekenreekswaarde door die de hoofdmap van de toepassing vertegenwoordigt.
   * Roep de methode `setContentRootURI` van het object `URLSpec` aan en geef een tekenreekswaarde door die de URI-waarde van de inhoudsbasis opgeeft. Zorg ervoor dat het formulierontwerp zich in de URI van de inhoudsbasis bevindt. Als niet, werpt de dienst van Forms een uitzondering. Geef `repository:///` op om naar de gegevensopslagruimte te verwijzen.
   * Roep de methode `setTargetURL` van het object `URLSpec` aan en geef een tekenreekswaarde door die de doel-URL-waarde opgeeft waar de formuliergegevens worden gepost. Als u de doel-URL in het formulierontwerp definieert, kunt u een lege tekenreeks doorgeven. U kunt ook de URL opgeven waarnaar een formulier wordt verzonden om berekeningen uit te voeren.

1. Bestanden aan het formulier koppelen

   * Maak een `java.util.HashMap`-object om bestandsbijlagen op te slaan met behulp van de constructor.
   * Roep de methode `java.util.HashMap` van het object `put` aan voor elk bestand dat aan het gerenderde formulier moet worden gekoppeld. Geef de volgende waarden door aan deze methode:

      * Een tekenreekswaarde die de naam van de bestandsbijlage opgeeft, inclusief de bestandsnaamextensie.
   * Een `com.adobe.idp.Document`-object dat de bestandsbijlage bevat.

   >[!NOTE]
   >
   >Herhaal deze stap voor elk bestand dat u aan het formulier wilt koppelen. Deze stap is optioneel en u kunt `null` doorgeven als u geen bestandsbijlagen wilt verzenden.

1. Een interactief PDF-formulier renderen

   Roep de methode `renderPDFForm` van het object `FormsServiceClient` aan en geef de volgende waarden door:

   * Een tekenreekswaarde die de naam van het formulierontwerp opgeeft, inclusief de bestandsnaamextensie. Als u naar een formulierontwerp verwijst dat deel uitmaakt van een Forms-toepassing, moet u het volledige pad opgeven, bijvoorbeeld `Applications/FormsApplication/1.0/FormsFolder/Loan.xdp`.
   * Een object `com.adobe.idp.Document` dat gegevens bevat die met het formulier moeten worden samengevoegd. Als u geen gegevens wilt samenvoegen, geeft u een leeg `com.adobe.idp.Document`-object door.
   * Een `PDFFormRenderSpec`-object dat uitvoeringsopties opslaat. Dit is een optionele parameter en u kunt `null` specificeren als u runtime geen opties wilt specificeren.
   * Een object `URLSpec` dat URI-waarden bevat die door de Forms-service worden vereist.
   * Een `java.util.HashMap`-object dat bestandsbijlagen opslaat. Dit is een optionele parameter en u kunt `null` opgeven als u geen bestanden aan het formulier wilt koppelen.

   De methode `renderPDFForm` retourneert een `FormsResult`-object dat een formuliergegevensstroom bevat die naar de webbrowser van de client moet worden geschreven.

1. De formuliergegevensstroom naar de webbrowser van de client schrijven

   * Maak een `com.adobe.idp.Document`-object door de methode `getOutputContent` van het object aan te roepen.`FormsResult`
   * Hiermee wordt het inhoudstype van het object `com.adobe.idp.Document` opgehaald door de methode `getContentType` ervan aan te roepen.
   * Stel het inhoudstype van het object `javax.servlet.http.HttpServletResponse` in door de methode `setContentType` ervan aan te roepen en het inhoudstype van het object `com.adobe.idp.Document` door te geven.
   * Maak een `javax.servlet.ServletOutputStream`-object dat wordt gebruikt om de formuliergegevensstroom naar de webbrowser van de client te schrijven door de methode `javax.servlet.http.HttpServletResponse` van het object `getOutputStream` aan te roepen.
   * Maak een `java.io.InputStream`-object door de methode `getInputStream` van het object `com.adobe.idp.Document` aan te roepen.
   * Maak een bytearray en vul deze met de formuliergegevensstroom door de methode `read` van het object `InputStream` aan te roepen en de bytearray als een argument door te geven.
   * Roep de methode `javax.servlet.ServletOutputStream` van het object `write` aan om de gegevensstroom van het formulier naar de webbrowser van de client te verzenden. Geef de bytearray door aan de methode `write`.

## Een interactief PDF-formulier renderen met de webservice-API {#render-an-interactive-pdf-form-using-the-web-service-api}

Een interactief PDF-formulier renderen met de Forms API (webservice):

1. Projectbestanden opnemen

   * Maak Java-proxyklassen die gebruikmaken van de Forms-service WSDL.
   * Neem de Java-proxyklassen op in het klassepad.

1. Een Forms Client API-object maken

   Maak een `FormsService`-object en stel de verificatiewaarden in.

1. URI-waarden opgeven

   * Maak een object `URLSpec` waarin URI-waarden worden opgeslagen met behulp van de constructor.
   * Roep de methode `URLSpec` van het object `setApplicationWebRoot` aan en geef een tekenreekswaarde door die de hoofdmap van de toepassing vertegenwoordigt.
   * Roep de methode `setContentRootURI` van het object `URLSpec` aan en geef een tekenreekswaarde door die de URI-waarde van de inhoudsbasis opgeeft. Zorg ervoor dat het formulierontwerp zich in de URI van de inhoudsbasis bevindt. Als niet, werpt de dienst van Forms een uitzondering. Geef `repository:///` op om naar de gegevensopslagruimte te verwijzen.
   * Roep de methode `setTargetURL` van het object `URLSpec` aan en geef een tekenreekswaarde door die de doel-URL-waarde opgeeft waar de formuliergegevens worden gepost. Als u de doel-URL in het formulierontwerp definieert, kunt u een lege tekenreeks doorgeven. U kunt ook de URL opgeven waarnaar een formulier wordt verzonden om berekeningen uit te voeren.

1. Bestanden aan het formulier koppelen

   * Maak een `java.util.HashMap`-object om bestandsbijlagen op te slaan met behulp van de constructor.
   * Roep de methode `java.util.HashMap` van het object `put` aan voor elk bestand dat aan het gerenderde formulier moet worden gekoppeld. Geef de volgende waarden door aan deze methode:

      * Een tekenreekswaarde die de naam van de bestandsbijlage opgeeft, inclusief de bestandsextensie
   * Een `BLOB`-object dat de bestandsbijlage bevat

   >[!NOTE]
   >
   >Herhaal deze stap voor elk bestand dat u aan het formulier wilt koppelen.

1. Een interactief PDF-formulier renderen

   Roep de methode `renderPDFForm` van het object `FormsService` aan en geef de volgende waarden door:

   * Een tekenreekswaarde die de naam van het formulierontwerp opgeeft, inclusief de bestandsnaamextensie. Als u naar een formulierontwerp verwijst dat deel uitmaakt van een Forms-toepassing, moet u het volledige pad opgeven, bijvoorbeeld `Applications/FormsApplication/1.0/FormsFolder/Loan.xdp`.
   * Een object `BLOB` dat gegevens bevat die met het formulier moeten worden samengevoegd. Als u geen gegevens wilt samenvoegen, geeft u `null` door.
   * Een `PDFFormRenderSpec`-object dat uitvoeringsopties opslaat. Dit is een optionele parameter en u kunt `null` specificeren als u runtime geen opties wilt specificeren.
   * Een object `URLSpec` dat URI-waarden bevat die door de Forms-service worden vereist.
   * Een `java.util.HashMap`-object dat bestandsbijlagen opslaat. Dit is een optionele parameter en u kunt `null` opgeven als u geen bestanden aan het formulier wilt koppelen.
   * Een leeg object `com.adobe.idp.services.holders.BLOBHolder` dat door de methode is gevuld. Hiermee slaat u het gerenderde PDF-formulier op.
   * Een leeg object `javax.xml.rpc.holders.LongHolder` dat door de methode is gevuld. (In dit argument wordt het aantal pagina&#39;s in het formulier opgeslagen.)
   * Een leeg object `javax.xml.rpc.holders.StringHolder` dat door de methode is gevuld. (In dit argument wordt de waarde van de landinstelling opgeslagen.)
   * Een leeg `com.adobe.idp.services.holders.FormsResultHolder`-object dat de resultaten van deze bewerking zal bevatten.

   Met de methode `renderPDFForm` wordt het object `com.adobe.idp.services.holders.FormsResultHolder` dat als laatste argumentwaarde is doorgegeven, gevuld met een formuliergegevensstroom die naar de webbrowser van de client moet worden geschreven.

1. De formuliergegevensstroom naar de webbrowser van de client schrijven

   * Maak een `FormResult`-object door de waarde op te halen van het `com.adobe.idp.services.holders.FormsResultHolder`-gegevenslid van het object.`value`
   * Maak een `BLOB`-object dat formuliergegevens bevat door de methode `getOutputContent` van het object `FormsResult` aan te roepen.
   * Hiermee wordt het inhoudstype van het object `BLOB` opgehaald door de methode `getContentType` ervan aan te roepen.
   * Stel het inhoudstype van het object `javax.servlet.http.HttpServletResponse` in door de methode `setContentType` ervan aan te roepen en het inhoudstype van het object `BLOB` door te geven.
   * Maak een `javax.servlet.ServletOutputStream`-object dat wordt gebruikt om de formuliergegevensstroom naar de webbrowser van de client te schrijven door de methode `javax.servlet.http.HttpServletResponse` van het object `getOutputStream` aan te roepen.
   * Maak een bytearray en vul deze door de methode `getBinaryData` van het object `BLOB` aan te roepen. Deze taak wijst de inhoud van het `FormsResult` voorwerp aan de byteserie toe.
   * Roep de methode `javax.servlet.http.HttpServletResponse` van het object `write` aan om de gegevensstroom van het formulier naar de webbrowser van de client te verzenden. Geef de bytearray door aan de methode `write`.

**De formuliergegevensstroom naar de webbrowser van de client schrijven**

Wanneer de Forms-service een formulier genereert, wordt een formuliergegevensstroom geretourneerd die u naar de webbrowser van de client moet schrijven. Wanneer het formulier naar de webbrowser van de client wordt geschreven, is het zichtbaar voor de gebruiker.
