---
title: Interactieve PDF forms renderen
seo-title: Interactieve PDF forms renderen
description: 'null'
seo-description: 'null'
uuid: df2a4dc8-f19e-49de-850f-85a204102631
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/rendering_forms
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: operations
discoiquuid: 3cb307ec-9b7b-4f03-b860-48553ccee746
translation-type: tm+mt
source-git-commit: 1343cc33a1e1ce26c0770a3b49317e82353497ab
workflow-type: tm+mt
source-wordcount: '2442'
ht-degree: 0%

---


# Interactieve PDF forms renderen {#rendering-interactive-pdf-forms}

De service Forms geeft interactieve PDF forms weer naar clientapparaten, meestal webbrowsers, om informatie van gebruikers te verzamelen. Nadat een interactief formulier is gegenereerd, kan een gebruiker gegevens invoeren in formuliervelden en op een verzendknop op het formulier klikken om informatie terug te sturen naar de service Forms. Een interactief PDF-formulier is alleen zichtbaar als Adobe Reader of Acrobat is geïnstalleerd op de computer die als host fungeert voor de webbrowser van de client.

>[!NOTE]
>
>Voordat u een formulier kunt genereren met de service Forms, moet u een formulierontwerp maken. Doorgaans wordt een formulierontwerp gemaakt in Designer en opgeslagen als een XDP-bestand. Zie [Formulierontwerper](https://www.adobe.com/go/learn_aemforms_designer_63)voor informatie over het maken van een formulierontwerp.

**Voorbeeldtoepassing van een lening**

Er wordt een voorbeeldtoepassing voor leningen geïntroduceerd om aan te tonen hoe de service Forms interactieve formulieren gebruikt om informatie van gebruikers te verzamelen. Met deze toepassing kan een gebruiker een formulier invullen met gegevens die nodig zijn om een lening te beveiligen en vervolgens gegevens verzenden naar de service Forms. In het volgende diagram wordt de logische stroom van de toepassing van de lening weergegeven.

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
   <td><p>De <code>GetLoanForm</code> Java Server wordt aangeroepen vanuit een HTML-pagina. </p></td>
  </tr>
  <tr>
   <td><p>2</p></td>
   <td><p>De <code>GetLoanForm</code> Java Server gebruikt de API van de de dienstcliënt van de Dienst van Vormen om het leningsformulier aan cliëntbrowser terug te geven. (Zie Een interactief PDF-formulier <a href="#render-an-interactive-pdf-form-using-the-java-api">renderen met de Java API</a>.)</p></td>
  </tr>
  <tr>
   <td><p>3</p></td>
   <td><p>Nadat de gebruiker het leningsformulier heeft ingevuld en op de verzendknop klikt, worden de gegevens naar <code>HandleData</code> Java Servlet verzonden. (Zie <i>"Lijnformulier"</i>.)</p></td>
  </tr>
  <tr>
   <td><p>4</p></td>
   <td><p>De <code>HandleData</code> Java-server gebruikt de API van de Forms Service Client om de formulierverzending te verwerken en formuliergegevens op te halen. De gegevens worden dan opgeslagen in een ondernemingsgegevensbestand. (Zie <a href="/help/forms/developing/handling-submitted-forms.md#handling-submitted-forms">Verstuurde formulieren</a>verwerken.)</p></td>
  </tr>
  <tr>
   <td><p>5</p></td>
   <td><p>Een bevestigingsformulier wordt teruggestuurd naar de webbrowser. Gegevens zoals de voor- en achternaam van de gebruiker worden met het formulier samengevoegd voordat het wordt gegenereerd. (Zie Formulieren <a href="/help/forms/developing/prepopulating-forms-flowable-layouts.md">vooraf invullen met stroombare indelingen</a>.)</p></td>
  </tr>
 </tbody>
</table>

**Lijnformulier**

Dit interactieve leningformulier wordt gegenereerd door de Java Servlet van de voorbeeldtoepassing voor `GetLoanForm` leningen.

![ri_ri_lanform](assets/ri_ri_loanform.png)

**Bevestigingsformulier**

Dit formulier wordt gegenereerd door de `HandleData` Java Servlet van de voorbeeldtoepassing.

![ri_ri_confirm](assets/ri_ri_confirm.png)

De `HandleData` Java Server vult dit formulier vooraf in met de voor- en achternaam van de gebruiker en het bedrag. Nadat het formulier vooraf is ingevuld, wordt het naar de webbrowser van de client verzonden. (Zie Formulieren [vooraf invullen met stroombare indelingen](/help/forms/developing/prepopulating-forms-flowable-layouts.md))

**Java Servlets**

De voorbeeldtoepassing voor leningen is een voorbeeld van een Forms-servicetoepassing die als Java Servlet bestaat. Een Java Servlet is een programma van Java dat op een J2EE toepassingsserver, zoals WebSphere loopt, en bevat de code van de de dienstcliënt van de Dienst van Vormen API.

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

Normaal gesproken plaatst u geen API-code van Forms Service Client binnen een Java Server `doGet` of een `doPost` methode. Het is beter programmeren om deze code binnen een afzonderlijke klasse te plaatsen, de klasse vanuit de `doPost` methode (of `doGet` methode) te instantiëren en de aangewezen methodes te roepen. Voor de beknoptheid van code worden de codevoorbeelden in deze sectie echter tot een minimum beperkt en worden codevoorbeelden in de `doPost` methode geplaatst.

>[!NOTE]
>
>Voor meer informatie over de dienst van Vormen, zie de Verwijzing van de [Diensten voor AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

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

Voordat u een API-bewerking voor Forms Service kunt uitvoeren, moet u een API-object voor Forms Client maken. Als u de Java API gebruikt, maakt u een `FormsServiceClient` object. Als u de API voor webservices van Forms gebruikt, maakt u een `FormsService` object.

**URI-waarden opgeven**

U kunt URI-waarden opgeven die de Forms-service nodig heeft om een formulier te genereren. Naar een formulierontwerp dat is opgeslagen als onderdeel van een Forms-toepassing, kan worden verwezen met de URI-waarde van de inhoudsbasis `repository:///`. Neem bijvoorbeeld het volgende formulierontwerp met de naam *Loan.xdp* in een Forms-toepassing met de naam *FormsApplication*:

![ri_ri_formrepository](assets/ri_ri_formrepository.png)

Geef voor toegang tot dit formulierontwerp de naam van het formulier op (de eerste parameter die aan de `Applications/FormsApplication/1.0/FormsFolder/Loan.xdp` methode is doorgegeven) en `renderPDFForm` `repository:///` de URI-waarde van de basisinhoud.

>[!NOTE]
>
>Zie [Workbench Help](https://www.adobe.com/go/learn_aemforms_workbench_63)voor informatie over het maken van een Forms-toepassing met Workbench.

Het pad naar een bron in een Forms-toepassing is:

`Applications/Application-name/Application-version/Folder.../Filename`

De volgende waarden tonen enkele voorbeelden van URI-waarden:

* Applications/AppraisalReport/1.0/Forms/FullForm.xdp
* Applications/AnotherApp/1.1/Assets/picture.jpg
* Applications/SomeApp/2.0/Resources/Data/XSDs/MyData.xsd

Wanneer u een interactief formulier genereert, kunt u URI-waarden definiëren, zoals de doel-URL waarnaar de formuliergegevens worden gepost. De doel-URL kan op een van de volgende manieren worden gedefinieerd:

* Op de knop Verzenden tijdens het ontwerpen van het formulierontwerp in Designer
* Door de Forms Service Client API te gebruiken

Als de doel-URL is gedefinieerd in het formulierontwerp, moet u deze niet overschrijven met de API voor de Forms Service Client. Met andere woorden, als u de doel-URL instelt met de API voor formulieren, wordt de opgegeven URL in het formulierontwerp teruggezet naar de URL die is opgegeven met de API. Als u het PDF-formulier wilt verzenden naar de doel-URL die in het formulierontwerp is opgegeven, stelt u de doel-URL programmatisch in op een lege tekenreeks.

Als u een formulier hebt dat een verzendknop en een berekeningsknop bevat (met een overeenkomstig script dat op de server wordt uitgevoerd), kunt u de URL programmatisch definiëren waarnaar het formulier wordt verzonden om het script uit te voeren. Met de knop Verzenden op het formulierontwerp geeft u de URL op waarnaar de formuliergegevens worden verzonden. (Zie Formuliergegevens [berekenen](/help/forms/developing/calculating-form-data.md).)

>[!NOTE]
>
>In plaats van een URL-waarde op te geven die naar een XDP-bestand verwijst, kunt u ook een `com.adobe.idp.Document` instantie aan de service Forms doorgeven. Het `com.adobe.idp.Document` exemplaar bevat een formulierontwerp. (Zie Documenten [doorgeven aan de Forms Service](/help/forms/developing/passing-documents-forms-service.md).)

**Bestanden aan het formulier koppelen**

U kunt bestanden aan een formulier koppelen. Wanneer u een PDF-formulier met bestandsbijlagen genereert, kunnen gebruikers de bestandsbijlagen in Acrobat ophalen met het venster Bestandsbijlage. U kunt verschillende bestandstypen aan een formulier koppelen, zoals een tekstbestand, of aan een binair bestand, zoals een JPG-bestand.

>[!NOTE]
>
>Het koppelen van bestandsbijlagen aan een formulier is optioneel.

**Een interactief PDF-formulier renderen**

Als u een formulier wilt genereren, gebruikt u een formulierontwerp dat in Designer is gemaakt en als XDP- of PDF-bestand is opgeslagen. U kunt ook een formulier genereren dat is gemaakt met Acrobat en is opgeslagen als PDF-bestand. Als u een interactief PDF-formulier wilt genereren, roept u de `FormsServiceClient` methode of `renderPDFForm` `renderPDFForm2` methode van het object aan.

De `renderPDFForm` operator gebruikt een `URLSpec` object. De hoofdmap van de inhoud wordt aan het XDP-bestand doorgegeven aan de service Forms met behulp van de `URLSpec` methode van het `setContentRootURI` object. De naam van het formulierontwerp ( `formQuery`) wordt doorgegeven als een afzonderlijke parameterwaarde. De twee waarden worden samengevoegd om de absolute verwijzing naar het formulierontwerp te verkrijgen.

De `renderPDFForm2` methode accepteert een `com.adobe.idp.Document` instantie die het te renderen XDP- of PDF-document bevat.

>[!NOTE]
>
>De runtime-optie voor gecodeerde PDF kan niet worden ingesteld als het invoerdocument een PDF-document is. Als het invoerbestand een XDP-bestand is, kunt u de optie Gecodeerde PDF instellen.

## Een interactief PDF-formulier renderen met de Java API {#render-an-interactive-pdf-form-using-the-java-api}

Een interactief PDF-formulier renderen met de API voor formulieren (Java):

1. Projectbestanden opnemen

   Neem client-JAR-bestanden, zoals adobe-forms-client.jar, op in het klassenpad van uw Java-project.

1. Een Forms Client API-object maken

   * Maak een `ServiceClientFactory` object dat verbindingseigenschappen bevat.
   * Maak een `FormsServiceClient` object door de constructor ervan te gebruiken en het `ServiceClientFactory` object door te geven.

1. URI-waarden opgeven

   * Maak een `URLSpec` object dat URI-waarden opslaat met de constructor ervan.
   * Roep de `URLSpec` methode van het `setApplicationWebRoot` object aan en geef een tekenreekswaarde door die de hoofdmap van de toepassing vertegenwoordigt.
   * Roep de `URLSpec` methode van het `setContentRootURI` object aan en geef een tekenreekswaarde door die de URI-waarde van de inhoudshoofdmap opgeeft. Zorg ervoor dat het formulierontwerp zich in de URI van de inhoudsbasis bevindt. Als niet, werpt de dienst van Vormen een uitzondering. Geef een verwijzing op naar de gegevensopslagruimte `repository:///`.
   * Roep de `URLSpec` methode van het `setTargetURL` object aan en geef een tekenreekswaarde door die de doel-URL-waarde opgeeft waarnaar formuliergegevens worden gepost. Als u de doel-URL in het formulierontwerp definieert, kunt u een lege tekenreeks doorgeven. U kunt ook de URL opgeven waarnaar een formulier wordt verzonden om berekeningen uit te voeren.

1. Bestanden aan het formulier koppelen

   * Maak een `java.util.HashMap` object om bestandsbijlagen op te slaan met behulp van de constructor.
   * Roep de `java.util.HashMap` methode van het `put` object aan voor elk bestand dat aan het gerenderde formulier moet worden gekoppeld. Geef de volgende waarden door aan deze methode:

      * Een tekenreekswaarde die de naam van de bestandsbijlage opgeeft, inclusief de bestandsnaamextensie.
   * Een `com.adobe.idp.Document` object dat de bestandsbijlage bevat.

   >[!NOTE]
   >
   >Herhaal deze stap voor elk bestand dat u aan het formulier wilt koppelen. Deze stap is optioneel en u kunt doorgeven `null` als u geen bestandsbijlagen wilt verzenden.

1. Een interactief PDF-formulier renderen

   Roep de methode van het `FormsServiceClient` `renderPDFForm` object aan en geef de volgende waarden door:

   * Een tekenreekswaarde die de naam van het formulierontwerp opgeeft, inclusief de bestandsnaamextensie. Als u verwijst naar een formulierontwerp dat deel uitmaakt van een Forms-toepassing, moet u controleren of u het volledige pad opgeeft, bijvoorbeeld `Applications/FormsApplication/1.0/FormsFolder/Loan.xdp`.
   * Een `com.adobe.idp.Document` object dat gegevens bevat die met het formulier moeten worden samengevoegd. Geef een leeg `com.adobe.idp.Document` object door als u geen gegevens wilt samenvoegen.
   * Een `PDFFormRenderSpec` object dat uitvoeringsopties opslaat. Dit is een optionele parameter en u kunt opgeven `null` of u geen runtime-opties wilt opgeven.
   * Een `URLSpec` object dat URI-waarden bevat die door de service Forms worden vereist.
   * Een `java.util.HashMap` object dat bestandsbijlagen opslaat. Dit is een optionele parameter en u kunt opgeven `null` of u geen bestanden aan het formulier wilt koppelen.

   De `renderPDFForm` methode retourneert een `FormsResult` object dat een formuliergegevensstroom bevat die naar de webbrowser van de client moet worden geschreven.

1. De formuliergegevensstroom naar de webbrowser van de client schrijven

   * Maak een `com.adobe.idp.Document` object door de `FormsResult` methode van het `getOutputContent` object aan te roepen.
   * Haal het inhoudstype van het `com.adobe.idp.Document` object op door de `getContentType` methode ervan aan te roepen.
   * Stel het inhoudstype van het `javax.servlet.http.HttpServletResponse` object in door de bijbehorende `setContentType` methode op te roepen en het inhoudstype van het `com.adobe.idp.Document` object door te geven.
   * Maak een `javax.servlet.ServletOutputStream` object dat wordt gebruikt om de gegevensstroom van het formulier naar de webbrowser van de client te schrijven door de `javax.servlet.http.HttpServletResponse` methode van het `getOutputStream` object aan te roepen.
   * Maak een `java.io.InputStream` object door de `com.adobe.idp.Document` methode van het `getInputStream` object aan te roepen.
   * Maak een bytearray en vul deze met de formuliergegevensstroom door de methode van het `InputStream` `read` object aan te roepen en de bytearray als een argument door te geven.
   * Roep de `javax.servlet.ServletOutputStream` methode van het `write` object aan om de formuliergegevensstroom naar de webbrowser van de client te verzenden. Geef de bytearray door aan de `write` methode.

## Een interactief PDF-formulier renderen met de webservice-API {#render-an-interactive-pdf-form-using-the-web-service-api}

Een interactief PDF-formulier renderen met de Forms API (webservice):

1. Projectbestanden opnemen

   * Maak Java-proxyklassen die de Forms service WSDL gebruiken.
   * Neem de Java-proxyklassen op in het klassepad.

1. Een Forms Client API-object maken

   Maak een `FormsService` object en stel verificatiewaarden in.

1. URI-waarden opgeven

   * Maak een `URLSpec` object dat URI-waarden opslaat met de constructor ervan.
   * Roep de `URLSpec` methode van het `setApplicationWebRoot` object aan en geef een tekenreekswaarde door die de hoofdmap van de toepassing vertegenwoordigt.
   * Roep de `URLSpec` methode van het `setContentRootURI` object aan en geef een tekenreekswaarde door die de URI-waarde van de inhoudshoofdmap opgeeft. Zorg ervoor dat het formulierontwerp zich in de URI van de inhoudsbasis bevindt. Als niet, werpt de dienst van Vormen een uitzondering. Geef een verwijzing op naar de gegevensopslagruimte `repository:///`.
   * Roep de `URLSpec` methode van het `setTargetURL` object aan en geef een tekenreekswaarde door die de doel-URL-waarde opgeeft waarnaar formuliergegevens worden gepost. Als u de doel-URL in het formulierontwerp definieert, kunt u een lege tekenreeks doorgeven. U kunt ook de URL opgeven waarnaar een formulier wordt verzonden om berekeningen uit te voeren.

1. Bestanden aan het formulier koppelen

   * Maak een `java.util.HashMap` object om bestandsbijlagen op te slaan met behulp van de constructor.
   * Roep de `java.util.HashMap` methode van het `put` object aan voor elk bestand dat aan het gerenderde formulier moet worden gekoppeld. Geef de volgende waarden door aan deze methode:

      * Een tekenreekswaarde die de naam van de bestandsbijlage opgeeft, inclusief de bestandsextensie
   * Een `BLOB` object dat de bestandsbijlage bevat

   >[!NOTE]
   >
   >Herhaal deze stap voor elk bestand dat u aan het formulier wilt koppelen.

1. Een interactief PDF-formulier renderen

   Roep de methode van het `FormsService` `renderPDFForm` object aan en geef de volgende waarden door:

   * Een tekenreekswaarde die de naam van het formulierontwerp opgeeft, inclusief de bestandsnaamextensie. Als u verwijst naar een formulierontwerp dat deel uitmaakt van een Forms-toepassing, moet u controleren of u het volledige pad opgeeft, bijvoorbeeld `Applications/FormsApplication/1.0/FormsFolder/Loan.xdp`.
   * Een `BLOB` object dat gegevens bevat die met het formulier moeten worden samengevoegd. Geef door als u geen gegevens wilt samenvoegen. `null`
   * Een `PDFFormRenderSpec` object dat uitvoeringsopties opslaat. Dit is een optionele parameter en u kunt opgeven `null` of u geen runtime-opties wilt opgeven.
   * Een `URLSpec` object dat URI-waarden bevat die door de service Forms worden vereist.
   * Een `java.util.HashMap` object dat bestandsbijlagen opslaat. Dit is een optionele parameter en u kunt opgeven `null` of u geen bestanden aan het formulier wilt koppelen.
   * Een leeg `com.adobe.idp.services.holders.BLOBHolder` object dat door de methode wordt gevuld. Hiermee slaat u het gerenderde PDF-formulier op.
   * Een leeg `javax.xml.rpc.holders.LongHolder` object dat door de methode wordt gevuld. (In dit argument wordt het aantal pagina&#39;s in het formulier opgeslagen.)
   * Een leeg `javax.xml.rpc.holders.StringHolder` object dat door de methode wordt gevuld. (In dit argument wordt de waarde van de landinstelling opgeslagen.)
   * Een leeg `com.adobe.idp.services.holders.FormsResultHolder` object dat de resultaten van deze bewerking zal bevatten.

   De `renderPDFForm` methode vult het `com.adobe.idp.services.holders.FormsResultHolder` object dat als laatste argumentwaarde wordt doorgegeven, met een formuliergegevensstroom die naar de webbrowser van de client moet worden geschreven.

1. De formuliergegevensstroom naar de webbrowser van de client schrijven

   * Maak een `FormResult` object door de waarde van het `com.adobe.idp.services.holders.FormsResultHolder` `value` gegevenslid van het object op te halen.
   * Maak een `BLOB` object dat formuliergegevens bevat door de `FormsResult` methode van het `getOutputContent` object aan te roepen.
   * Haal het inhoudstype van het `BLOB` object op door de `getContentType` methode ervan aan te roepen.
   * Stel het inhoudstype van het `javax.servlet.http.HttpServletResponse` object in door de bijbehorende `setContentType` methode op te roepen en het inhoudstype van het `BLOB` object door te geven.
   * Maak een `javax.servlet.ServletOutputStream` object dat wordt gebruikt om de gegevensstroom van het formulier naar de webbrowser van de client te schrijven door de `javax.servlet.http.HttpServletResponse` methode van het `getOutputStream` object aan te roepen.
   * Maak een bytearray en vul deze door de `BLOB` methode van het `getBinaryData` object aan te roepen. Hierdoor wordt de inhoud van het `FormsResult` object toegewezen aan de bytearray.
   * Roep de `javax.servlet.http.HttpServletResponse` methode van het `write` object aan om de formuliergegevensstroom naar de webbrowser van de client te verzenden. Geef de bytearray door aan de `write` methode.

**De formuliergegevensstroom naar de webbrowser van de client schrijven**

Wanneer de service Forms een formulier genereert, wordt een formuliergegevensstroom geretourneerd die u naar de webbrowser van de client moet schrijven. Wanneer het formulier naar de webbrowser van de client wordt geschreven, is het zichtbaar voor de gebruiker.
