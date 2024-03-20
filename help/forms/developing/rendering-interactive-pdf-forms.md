---
title: Interactieve PDF forms renderen
description: Met de Forms-service kunt u interactieve PDF forms renderen naar clientapparaten, meestal webbrowsers, om informatie van gebruikers te verzamelen. U kunt de dienst van Forms gebruiken om interactieve vormen terug te geven gebruikend Java API en de Dienst API van het Web.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/rendering_forms
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: operations
role: Developer
exl-id: d9f32939-c2c0-4531-b15e-f63941c289e3
solution: Experience Manager, Experience Manager Forms
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '2455'
ht-degree: 0%

---

# Interactieve PDF forms renderen {#rendering-interactive-pdf-forms}

**Voorbeelden en voorbeelden in dit document gelden alleen voor AEM Forms in JEE-omgeving.**

De Forms-service rendert interactieve PDF forms naar clientapparaten, meestal webbrowsers, om informatie van gebruikers te verzamelen. Nadat een interactief formulier is gegenereerd, kan een gebruiker gegevens invoeren in formuliervelden en op een verzendknop op het formulier klikken om informatie terug te sturen naar de Forms-service. Adobe Reader of Acrobat moet zijn geïnstalleerd op de computer die als host fungeert voor de webbrowser van de client om een interactief PDF-formulier zichtbaar te maken.

>[!NOTE]
>
>Voordat u een formulier kunt genereren met de Forms-service, moet u eerst een formulierontwerp maken. Doorgaans wordt een formulierontwerp gemaakt in Designer en opgeslagen als een XDP-bestand. Zie voor informatie over het maken van een formulierontwerp [Forms Designer](https://www.adobe.com/go/learn_aemforms_designer_63).

**Voorbeeldleningaanvraag**

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
   <td><p>De <code>GetLoanForm</code> Java Servlet wordt aangeroepen vanaf een HTML-pagina. </p></td>
  </tr>
  <tr>
   <td><p>2</p></td>
   <td><p>De <code>GetLoanForm</code> Java Servlet gebruikt de Forms Service Client API om het leningformulier te genereren naar de webbrowser van de client. (Zie <a href="#render-an-interactive-pdf-form-using-the-java-api">Een interactief PDF-formulier renderen met de Java API</a>.)</p></td>
  </tr>
  <tr>
   <td><p>3</p></td>
   <td><p>Nadat de gebruiker het leningsformulier heeft ingevuld en op de verzendknop klikt, worden gegevens verzonden naar de <code>HandleData</code> Java Servlet (Zie <i>"Leningen"</i>.)</p></td>
  </tr>
  <tr>
   <td><p>4</p></td>
   <td><p>De <code>HandleData</code> Java Servlet gebruikt de Forms Service Client API om de formulierverzending te verwerken en formuliergegevens op te halen. De gegevens worden dan opgeslagen in een ondernemingsgegevensbestand. (Zie <a href="/help/forms/developing/handling-submitted-forms.md#handling-submitted-forms">Verzendde Forms afhandelen</a>.)</p></td>
  </tr>
  <tr>
   <td><p>5</p></td>
   <td><p>Een bevestigingsformulier wordt teruggestuurd naar de webbrowser. Gegevens zoals de voor- en achternaam van de gebruiker worden samengevoegd met het formulier voordat het wordt gegenereerd. (Zie <a href="/help/forms/developing/prepopulating-forms-flowable-layouts.md">Forms vooraf vullen met stroombare indelingen</a>.)</p></td>
  </tr>
 </tbody>
</table>

**Lijnformulier**

Dit interactieve leningformulier wordt gegenereerd door de voorbeeldleningaanvraag `GetLoanForm` Java Servlet

![ri_ri_lanform](assets/ri_ri_loanform.png)

**Bevestigingsformulier**

Dit formulier wordt gegenereerd door de voorbeeldtoepassing van de leningaanvraag `HandleData` Java Servlet

![ri_ri_confirm](assets/ri_ri_confirm.png)

De `HandleData` Java Servlet vult dit formulier vooraf in met de voor- en achternaam en de hoeveelheid van de gebruiker. Nadat het formulier vooraf is ingevuld, wordt het naar de webbrowser van de client verzonden. (Zie [Forms vooraf vullen met stroombare indelingen](/help/forms/developing/prepopulating-forms-flowable-layouts.md))

**Java Server**

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

Normaal gesproken plaatst u geen Forms Service Client API-code in een Java Server `doGet` of `doPost` methode. Het is beter programmeren om deze code in een afzonderlijke klasse te plaatsen, de klasse vanuit de `doPost` of `doGet` methode) en roept de aangewezen methodes aan. Voor de beknoptheid van de code worden de codevoorbeelden in deze sectie echter tot een minimum beperkt en worden codevoorbeelden in de `doPost` methode.

>[!NOTE]
>
>Voor meer informatie over de Forms-service raadpleegt u [Services Reference for AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

**Overzicht van de stappen**

Voer de volgende taken uit om een interactief PDF-formulier te genereren:

1. Inclusief projectbestanden.
1. Maak een Forms Client API-object.
1. Geef URI-waarden op.
1. Bestanden aan het formulier koppelen (optioneel).
1. Een interactief PDF-formulier weergeven.
1. Schrijf de gegevensstroom van het formulier naar de webbrowser van de client.

**Projectbestanden opnemen**

Neem de benodigde bestanden op in uw ontwikkelingsproject. Als u een clienttoepassing maakt met Java, neemt u de benodigde JAR-bestanden op. Als u webservices gebruikt, dient u de proxybestanden op te nemen.

**Een Forms Client API-object maken**

Voordat u een Forms Service Client API-bewerking programmatisch kunt uitvoeren, moet u een Forms Client API-object maken. Als u de Java API gebruikt, maakt u een `FormsServiceClient` object. Als u de Forms-webservice-API gebruikt, maakt u een `FormsService` object.

**URI-waarden opgeven**

U kunt URI-waarden opgeven die de Forms-service nodig heeft om een formulier te genereren. Een formulierontwerp dat is opgeslagen als onderdeel van een Forms-toepassing, kan worden gebruikt door de URI-waarde van de inhoudsbasis te gebruiken `repository:///`. Neem bijvoorbeeld het volgende formulierontwerp met de naam *Lening.xdp* zich bevindt binnen een Forms-toepassing met de naam *FormsApplication*:

![ri_ri_formrepository](assets/ri_ri_formrepository.png)

Als u dit formulierontwerp wilt openen, geeft u `Applications/FormsApplication/1.0/FormsFolder/Loan.xdp` als de formuliernaam (de eerste parameter die aan de `renderPDFForm` methode) en `repository:///` als de URI-waarde van de inhoudsbasis.

>[!NOTE]
>
>Voor informatie over het maken van een Forms-toepassing met Workbench gaat u naar [Workbench Help](https://www.adobe.com/go/learn_aemforms_workbench_63).

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
>In plaats van een URL-waarde op te geven die naar een XDP-bestand verwijst, kunt u ook een `com.adobe.idp.Document` naar de Forms-service. De `com.adobe.idp.Document` -exemplaar bevat een formulierontwerp. (Zie [Documenten doorgeven aan de Forms-service](/help/forms/developing/passing-documents-forms-service.md).)

**Bestanden aan het formulier koppelen**

U kunt bestanden aan een formulier koppelen. Wanneer u een PDF-formulier met bestandsbijlagen genereert, kunnen gebruikers de bestandsbijlagen in Acrobat ophalen via het venster Bestandsbijlage. U kunt verschillende bestandstypen aan een formulier koppelen, zoals een tekstbestand, of aan een binair bestand, zoals een JPG-bestand.

>[!NOTE]
>
>Het koppelen van bestandsbijlagen aan een formulier is optioneel.

**Een interactief PDF-formulier renderen**

Als u een formulier wilt genereren, gebruikt u een formulierontwerp dat in Designer is gemaakt en als XDP- of PDF-bestand is opgeslagen. U kunt ook een formulier genereren dat is gemaakt met Acrobat en is opgeslagen als een PDF-bestand. Als u een interactief PDF-formulier wilt genereren, roept u de `FormsServiceClient` object `renderPDFForm` methode of `renderPDFForm2` methode.

De `renderPDFForm` gebruikt een `URLSpec` object. De inhoudsbasis wordt aan het XDP-bestand doorgegeven via de Forms-service `URLSpec` object `setContentRootURI` methode. De naam van het formulierontwerp ( `formQuery`) wordt doorgegeven als een afzonderlijke parameterwaarde. De twee waarden worden samengevoegd om de absolute verwijzing naar het formulierontwerp te verkrijgen.

De `renderPDFForm2` methode accepteert een `com.adobe.idp.Document` -instantie die het te renderen XDP- of PDF-document bevat.

>[!NOTE]
>
>De runtime voor gelabelde PDF kan niet worden ingesteld als het invoerdocument een PDF-document is. Als het invoerbestand een XDP-bestand is, kunt u de optie voor gecodeerde PDF instellen.

## Een interactief PDF-formulier renderen met de Java API {#render-an-interactive-pdf-form-using-the-java-api}

Een interactief PDF-formulier renderen met de Forms API (Java):

1. Projectbestanden opnemen

   Neem client-JAR-bestanden, zoals adobe-forms-client.jar, op in het klassepad van uw Java-project.

1. Een Forms Client API-object maken

   * Een `ServiceClientFactory` object dat verbindingseigenschappen bevat.
   * Een `FormsServiceClient` object door de constructor ervan te gebruiken en de `ServiceClientFactory` object.

1. URI-waarden opgeven

   * Een `URLSpec` object dat URI-waarden opslaat met de constructor ervan.
   * De `URLSpec` object `setApplicationWebRoot` en geeft een tekenreekswaarde door die de hoofdmap van de toepassing vertegenwoordigt.
   * De `URLSpec` object `setContentRootURI` methode en geef een tekenreekswaarde door die de URI-waarde van de inhoudsbasis opgeeft. Zorg ervoor dat het formulierontwerp zich in de URI van de inhoudsbasis bevindt. Als niet, werpt de dienst van Forms een uitzondering. Als u naar de gegevensopslagruimte wilt verwijzen, geeft u `repository:///`.
   * De `URLSpec` object `setTargetURL` en geeft een tekenreekswaarde door die de doel-URL-waarde opgeeft waarnaar formuliergegevens worden gepost. Als u de doel-URL in het formulierontwerp definieert, kunt u een lege tekenreeks doorgeven. U kunt ook de URL opgeven waarnaar een formulier wordt verzonden om berekeningen uit te voeren.

1. Bestanden aan het formulier koppelen

   * Een `java.util.HashMap` -object om bestandsbijlagen op te slaan met behulp van de constructor.
   * De `java.util.HashMap` object `put` voor elk bestand dat aan het gegenereerde formulier moet worden gekoppeld. Geef de volgende waarden door aan deze methode:

      * Een tekenreekswaarde die de naam van de bestandsbijlage opgeeft, inclusief de bestandsnaamextensie.

   * A `com.adobe.idp.Document` object dat de bestandsbijlage bevat.

   >[!NOTE]
   >
   >Herhaal deze stap voor elk bestand dat u aan het formulier wilt koppelen. Deze stap is optioneel en u kunt `null` als u geen bestandsbijlagen wilt verzenden.

1. Een interactief PDF-formulier renderen

   De `FormsServiceClient` object `renderPDFForm` en geeft de volgende waarden door:

   * Een tekenreekswaarde die de naam van het formulierontwerp opgeeft, inclusief de bestandsnaamextensie. Als u naar een formulierontwerp verwijst dat deel uitmaakt van een Forms-toepassing, moet u het volledige pad opgeven, zoals `Applications/FormsApplication/1.0/FormsFolder/Loan.xdp`.
   * A `com.adobe.idp.Document` object dat gegevens bevat die met het formulier moeten worden samengevoegd. Als u geen gegevens wilt samenvoegen, geeft u een lege waarde door `com.adobe.idp.Document` object.
   * A `PDFFormRenderSpec` -object dat uitvoeringsopties opslaat. Dit is een optionele parameter en u kunt `null` als u geen runtime opties wilt opgeven.
   * A `URLSpec` object dat URI-waarden bevat die door de Forms-service worden vereist.
   * A `java.util.HashMap` object waarin bestandsbijlagen zijn opgeslagen. Dit is een optionele parameter en u kunt `null` als u geen bestanden aan het formulier wilt koppelen.

   De `renderPDFForm` methode retourneert een `FormsResult` object dat een formuliergegevensstroom bevat die naar de webbrowser van de client moet worden geschreven.

1. De formuliergegevensstroom naar de webbrowser van de client schrijven

   * Een `com.adobe.idp.Document` door het object aan te roepen `FormsResult` object `getOutputContent` methode.
   * Hiermee wordt het inhoudstype van het dialoogvenster `com.adobe.idp.Document` object aanroepen `getContentType` methode.
   * Stel de `javax.servlet.http.HttpServletResponse` inhoudstype van object aanroepen `setContentType` en geeft u het inhoudstype van de `com.adobe.idp.Document` object.
   * Een `javax.servlet.ServletOutputStream` object dat wordt gebruikt om de formuliergegevensstroom naar de webbrowser van de client te schrijven door het aanroepen van de `javax.servlet.http.HttpServletResponse` object `getOutputStream` methode.
   * Een `java.io.InputStream` door het object aan te roepen `com.adobe.idp.Document` object `getInputStream` methode.
   * Maak een bytearray en vul deze met de formuliergegevensstroom door de `InputStream` object `read` en de bytearray doorgeven als een argument.
   * De `javax.servlet.ServletOutputStream` object `write` methode om de formuliergegevensstroom naar de webbrowser van de client te verzenden. Geef de bytearray door aan de `write` methode.

## Een interactief PDF-formulier renderen met de webservice-API {#render-an-interactive-pdf-form-using-the-web-service-api}

Een interactief PDF-formulier renderen met de Forms API (webservice):

1. Projectbestanden opnemen

   * Maak Java-proxyklassen die gebruikmaken van de Forms-service WSDL.
   * Neem de Java-proxyklassen op in het klassepad.

1. Een Forms Client API-object maken

   Een `FormsService` -object en stel verificatiewaarden in.

1. URI-waarden opgeven

   * Een `URLSpec` object dat URI-waarden opslaat met de constructor ervan.
   * De `URLSpec` object `setApplicationWebRoot` en geeft een tekenreekswaarde door die de hoofdmap van de toepassing vertegenwoordigt.
   * De `URLSpec` object `setContentRootURI` methode en geef een tekenreekswaarde door die de URI-waarde van de inhoudsbasis opgeeft. Zorg ervoor dat het formulierontwerp zich in de URI van de inhoudsbasis bevindt. Als niet, werpt de dienst van Forms een uitzondering. Als u naar de gegevensopslagruimte wilt verwijzen, geeft u `repository:///`.
   * De `URLSpec` object `setTargetURL` en geeft een tekenreekswaarde door die de doel-URL-waarde opgeeft waarnaar formuliergegevens worden gepost. Als u de doel-URL in het formulierontwerp definieert, kunt u een lege tekenreeks doorgeven. U kunt ook de URL opgeven waarnaar een formulier wordt verzonden om berekeningen uit te voeren.

1. Bestanden aan het formulier koppelen

   * Een `java.util.HashMap` -object om bestandsbijlagen op te slaan met behulp van de constructor.
   * De `java.util.HashMap` object `put` voor elk bestand dat aan het gegenereerde formulier moet worden gekoppeld. Geef de volgende waarden door aan deze methode:

      * Een tekenreekswaarde die de naam van de bestandsbijlage opgeeft, inclusief de bestandsextensie

   * A `BLOB` object dat de bestandsbijlage bevat

   >[!NOTE]
   >
   >Herhaal deze stap voor elk bestand dat u aan het formulier wilt koppelen.

1. Een interactief PDF-formulier renderen

   De `FormsService` object `renderPDFForm` en geeft de volgende waarden door:

   * Een tekenreekswaarde die de naam van het formulierontwerp opgeeft, inclusief de bestandsnaamextensie. Als u naar een formulierontwerp verwijst dat deel uitmaakt van een Forms-toepassing, moet u het volledige pad opgeven, zoals `Applications/FormsApplication/1.0/FormsFolder/Loan.xdp`.
   * A `BLOB` object dat gegevens bevat die met het formulier moeten worden samengevoegd. Als u geen gegevens wilt samenvoegen, geeft u `null`.
   * A `PDFFormRenderSpec` -object dat uitvoeringsopties opslaat. Dit is een optionele parameter en u kunt `null` als u geen runtime opties wilt opgeven.
   * A `URLSpec` object dat URI-waarden bevat die door de Forms-service worden vereist.
   * A `java.util.HashMap` object waarin bestandsbijlagen zijn opgeslagen. Dit is een optionele parameter en u kunt `null` als u geen bestanden aan het formulier wilt koppelen.
   * Een leeg `com.adobe.idp.services.holders.BLOBHolder` object dat door de methode wordt gevuld. Hiermee slaat u het gerenderde PDF formulier op.
   * Een leeg `javax.xml.rpc.holders.LongHolder` object dat door de methode wordt gevuld. (In dit argument wordt het aantal pagina&#39;s in het formulier opgeslagen.)
   * Een leeg `javax.xml.rpc.holders.StringHolder` object dat door de methode wordt gevuld. (In dit argument wordt de waarde van de landinstelling opgeslagen.)
   * Een leeg `com.adobe.idp.services.holders.FormsResultHolder` -object dat de resultaten van deze bewerking zal bevatten.

   De `renderPDFForm` wordt de `com.adobe.idp.services.holders.FormsResultHolder` object dat wordt doorgegeven als de laatste argumentwaarde met een formuliergegevensstroom die naar de webbrowser van de client moet worden geschreven.

1. De formuliergegevensstroom naar de webbrowser van de client schrijven

   * Een `FormResult` object door de waarde van het object op te halen `com.adobe.idp.services.holders.FormsResultHolder` object `value` lid.
   * Een `BLOB` object dat formuliergegevens bevat door het `FormsResult` object `getOutputContent` methode.
   * Hiermee wordt het inhoudstype van het dialoogvenster `BLOB` object aanroepen `getContentType` methode.
   * Stel de `javax.servlet.http.HttpServletResponse` inhoudstype van object aanroepen `setContentType` en geeft u het inhoudstype van de `BLOB` object.
   * Een `javax.servlet.ServletOutputStream` object dat wordt gebruikt om de formuliergegevensstroom naar de webbrowser van de client te schrijven door het aanroepen van de `javax.servlet.http.HttpServletResponse` object `getOutputStream` methode.
   * Maak een bytearray en vul deze door het `BLOB` object `getBinaryData` methode. Deze taak wijst de inhoud van toe `FormsResult` object naar de bytearray.
   * De `javax.servlet.http.HttpServletResponse` object `write` methode om de formuliergegevensstroom naar de webbrowser van de client te verzenden. Geef de bytearray door aan de `write` methode.

**De formuliergegevensstroom naar de webbrowser van de client schrijven**

Wanneer de Forms-service een formulier genereert, wordt een formuliergegevensstroom geretourneerd die u naar de webbrowser van de client moet schrijven. Wanneer het formulier naar de webbrowser van de client wordt geschreven, is het zichtbaar voor de gebruiker.
