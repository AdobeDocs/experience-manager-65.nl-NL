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
feature: Adaptive Forms,Document Services,APIs & Integrations
source-git-commit: d7b9e947503df58435b3fee85a92d51fae8c1d2d
workflow-type: tm+mt
source-wordcount: '2455'
ht-degree: 0%

---

# Interactieve PDF forms renderen {#rendering-interactive-pdf-forms}

**de Steekproeven en de voorbeelden in dit document zijn slechts voor AEM Forms op milieu JEE.**

De Forms-service rendert interactieve PDF forms naar clientapparaten, meestal webbrowsers, om informatie van gebruikers te verzamelen. Nadat een interactief formulier is gegenereerd, kan een gebruiker gegevens invoeren in formuliervelden en op een verzendknop op het formulier klikken om informatie terug te sturen naar de Forms-service. Adobe Reader of Acrobat moet zijn geïnstalleerd op de computer die als host fungeert voor de webbrowser van de client om een interactief PDF-formulier zichtbaar te maken.

>[!NOTE]
>
>Voordat u een formulier kunt genereren met de Forms-service, moet u eerst een formulierontwerp maken. Doorgaans wordt een formulierontwerp gemaakt in Designer en opgeslagen als een XDP-bestand. Voor informatie over het creëren van een vormontwerp, zie [&#x200B; Forms Designer &#x200B;](https://www.adobe.com/go/learn_aemforms_designer_63).

**de lentetoepassing van de steekproef**

Er wordt een voorbeeldtoepassing voor leningen geïntroduceerd om aan te tonen hoe de Forms-service interactieve formulieren gebruikt om informatie van gebruikers te verzamelen. Met deze toepassing kan een gebruiker een formulier invullen met gegevens die nodig zijn om een lening te beveiligen en vervolgens gegevens verzenden naar de Forms-service. In het volgende diagram wordt de logische stroom van de toepassing van de lening weergegeven.

![&#x200B; ri_ri_finsrv_loanapp_v1 &#x200B;](assets/ri_ri_finsrv_loanapp_v1.png)

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
   <td><p>De Java Server van <code>GetLoanForm</code> wordt aangehaald van een pagina van de HTML. </p></td>
  </tr>
  <tr>
   <td><p>2</p></td>
   <td><p>De <code>GetLoanForm</code> Java Server gebruikt de Forms Service Client API om het leningformulier te genereren naar de clientwebbrowser. (Zie <a href="#render-an-interactive-pdf-form-using-the-java-api"> een interactieve vorm van PDF teruggeven gebruikend Java API </a>.)</p></td>
  </tr>
  <tr>
   <td><p>3</p></td>
   <td><p>Nadat de gebruiker het leningformulier heeft ingevuld en op de verzendknop klikt, worden gegevens verzonden naar de <code>HandleData</code> Java Server. (Zie <i> "Vorm van de Lening"</i>.)</p></td>
  </tr>
  <tr>
   <td><p>4</p></td>
   <td><p>De <code>HandleData</code> Java Server gebruikt de Forms Service Client API om de formulierverzending te verwerken en formuliergegevens op te halen. De gegevens worden dan opgeslagen in een ondernemingsgegevensbestand. (Zie <a href="/help/forms/developing/handling-submitted-forms.md#handling-submitted-forms"> Behandelend Voorgelegde Forms </a>.)</p></td>
  </tr>
  <tr>
   <td><p>5</p></td>
   <td><p>Een bevestigingsformulier wordt teruggestuurd naar de webbrowser. Gegevens zoals de voor- en achternaam van de gebruiker worden samengevoegd met het formulier voordat het wordt gegenereerd. (Zie <a href="/help/forms/developing/prepopulating-forms-flowable-layouts.md"> Prepopulating Forms met Stroombare Lay-outs </a>.)</p></td>
  </tr>
 </tbody>
</table>

**vorm van de Lening**

Dit interactieve leningformulier wordt gegenereerd door de Java Servlet van de voorbeeldtoepassing. `GetLoanForm`

![&#x200B; ri_ri_loanform &#x200B;](assets/ri_ri_loanform.png)

**Bevestigingsvorm**

Dit formulier wordt gegenereerd door de Java Servlet van de voorbeeldtoepassing. `HandleData`

![&#x200B; ri_ri_confirm &#x200B;](assets/ri_ri_confirm.png)

Met de Java Server `HandleData` wordt dit formulier vooraf ingevuld met de voor- en achternaam en de hoeveelheid van de gebruiker. Nadat het formulier vooraf is ingevuld, wordt het naar de webbrowser van de client verzonden. (Zie [&#x200B; Prepopulating Forms met Stroombare Lay-outs &#x200B;](/help/forms/developing/prepopulating-forms-flowable-layouts.md))

**Servlets Java**

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

Normaal gesproken plaatst u de Forms Service Client API-code niet in een Java Server-methode `doGet` of `doPost` . Het is beter om deze code in een afzonderlijke klasse te plaatsen, de klasse vanuit de methode `doPost` (of methode `doGet` ) te instantiëren en de juiste methoden aan te roepen. Voor de beknoptheid van code worden de codevoorbeelden in deze sectie echter tot een minimum beperkt en worden codevoorbeelden in de methode `doPost` geplaatst.

>[!NOTE]
>
>Voor meer informatie over de dienst van Forms, zie [&#x200B; Verwijzing van de Diensten voor AEM Forms &#x200B;](https://www.adobe.com/go/learn_aemforms_services_63).

**Samenvatting van stappen**

Voer de volgende taken uit om een interactief PDF-formulier te genereren:

1. Inclusief projectbestanden.
1. Maak een Forms Client API-object.
1. Geef URI-waarden op.
1. Bestanden aan het formulier koppelen (optioneel).
1. Een interactief PDF-formulier weergeven.
1. Schrijf de gegevensstroom van het formulier naar de webbrowser van de client.

**omvat projectdossiers**

Neem de benodigde bestanden op in uw ontwikkelingsproject. Als u een clienttoepassing maakt met Java, neemt u de benodigde JAR-bestanden op. Als u webservices gebruikt, dient u de proxybestanden op te nemen.

**creeer een voorwerp van Forms Cliënt API**

Voordat u een Forms Service Client API-bewerking programmatisch kunt uitvoeren, moet u een Forms Client API-object maken. Maak een `FormsServiceClient` -object als u de Java API gebruikt. Maak een `FormsService` -object als u de Forms-API voor webservices gebruikt.

**specificeer de waarden van URI**

U kunt URI-waarden opgeven die de Forms-service nodig heeft om een formulier te genereren. Naar een formulierontwerp dat is opgeslagen als onderdeel van een Forms-toepassing, kan worden verwezen met de URI-waarde van de inhoudsbasis `repository:///` . Bijvoorbeeld, overweeg het volgende vormontwerp genoemd *Loan.xdp* binnen een toepassing van Forms genoemd *FormsApplication* wordt gevestigd:

![&#x200B; ri_ri_formrepository &#x200B;](assets/ri_ri_formrepository.png)

Als u toegang wilt tot dit formulierontwerp, geeft u `Applications/FormsApplication/1.0/FormsFolder/Loan.xdp` op als de formuliernaam (de eerste parameter die aan de methode `renderPDFForm` wordt doorgegeven) en `repository:///` als de URI-waarde van de inhoudsbasis.

>[!NOTE]
>
>Voor informatie over het creëren van een toepassing van Forms die Workbench gebruikt, zie [&#x200B; Hulp Workbench &#x200B;](https://www.adobe.com/go/learn_aemforms_workbench_63).

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

Als u een formulier hebt dat een verzendknop en een berekeningsknop bevat (met een overeenkomstig script dat op de server wordt uitgevoerd), kunt u de URL programmatisch definiëren waarnaar het formulier wordt verzonden om het script uit te voeren. Met de knop Verzenden op het formulierontwerp geeft u de URL op waarnaar de formuliergegevens worden verzonden. (Zie [&#x200B; Berekend de Gegevens van de Vorm &#x200B;](/help/forms/developing/calculating-form-data.md).)

>[!NOTE]
>
>In plaats van een URL-waarde op te geven die naar een XDP-bestand verwijst, kunt u ook een `com.adobe.idp.Document` -instantie doorgeven aan de Forms-service. Het `com.adobe.idp.Document` -exemplaar bevat een formulierontwerp. (Zie [&#x200B; het overgaan van Documenten tot de Dienst van Forms &#x200B;](/help/forms/developing/passing-documents-forms-service.md).)

**maak dossiers aan de vorm** vast

U kunt bestanden aan een formulier koppelen. Wanneer u een PDF-formulier met bestandsbijlagen genereert, kunnen gebruikers de bestandsbijlagen in Acrobat ophalen via het venster Bestandsbijlage. U kunt verschillende bestandstypen aan een formulier koppelen, zoals een tekstbestand, of aan een binair bestand, zoals een JPG-bestand.

>[!NOTE]
>
>Het koppelen van bestandsbijlagen aan een formulier is optioneel.

**geef een interactieve vorm van PDF** terug

Als u een formulier wilt genereren, gebruikt u een formulierontwerp dat in Designer is gemaakt en als XDP- of PDF-bestand is opgeslagen. U kunt ook een formulier genereren dat is gemaakt met Acrobat en is opgeslagen als een PDF-bestand. Als u een interactief PDF-formulier wilt renderen, roept u de methode `renderPDFForm` of `renderPDFForm2` van het `FormsServiceClient` -object aan.

In `renderPDFForm` wordt een `URLSpec` -object gebruikt. De hoofdmap van de inhoud wordt aan het XDP-bestand doorgegeven aan de Forms-service met de methode `setContentRootURI` van het object `URLSpec` . De naam van het formulierontwerp ( `formQuery` ) wordt doorgegeven als een afzonderlijke parameterwaarde. De twee waarden worden samengevoegd om de absolute verwijzing naar het formulierontwerp te verkrijgen.

De methode `renderPDFForm2` accepteert een instantie `com.adobe.idp.Document` die het te renderen XDP- of PDF-document bevat.

>[!NOTE]
>
>De runtime voor gelabelde PDF kan niet worden ingesteld als het invoerdocument een PDF-document is. Als het invoerbestand een XDP-bestand is, kunt u de optie voor gecodeerde PDF instellen.

## Een interactief PDF-formulier renderen met de Java API {#render-an-interactive-pdf-form-using-the-java-api}

Een interactief PDF-formulier renderen met de Forms API (Java):

1. Projectbestanden opnemen

   Neem client-JAR-bestanden, zoals adobe-forms-client.jar, op in het klassepad van uw Java-project.

1. Een Forms Client API-object maken

   * Maak een `ServiceClientFactory` -object dat verbindingseigenschappen bevat.
   * Maak een `FormsServiceClient` -object door de constructor ervan te gebruiken en het `ServiceClientFactory` -object door te geven.

1. URI-waarden opgeven

   * Maak een `URLSpec` -object dat URI-waarden opslaat met behulp van de constructor.
   * Roep de methode `setApplicationWebRoot` van het object `URLSpec` aan en geef een tekenreekswaarde door die de hoofdmap van de toepassing vertegenwoordigt.
   * Roep de methode `setContentRootURI` van het `URLSpec` -object aan en geef een tekenreekswaarde door die de URI-waarde van de inhoudsbasis opgeeft. Zorg ervoor dat het formulierontwerp zich in de URI van de inhoudsbasis bevindt. Als niet, werpt de dienst van Forms een uitzondering. Geef `repository:///` op om naar de gegevensopslagruimte te verwijzen.
   * Roep de methode `setTargetURL` van het `URLSpec` -object aan en geef een tekenreekswaarde door die de doel-URL-waarde opgeeft waarnaar de formuliergegevens worden gepost. Als u de doel-URL in het formulierontwerp definieert, kunt u een lege tekenreeks doorgeven. U kunt ook de URL opgeven waarnaar een formulier wordt verzonden om berekeningen uit te voeren.

1. Bestanden aan het formulier koppelen

   * Maak een `java.util.HashMap` -object om bestandsbijlagen op te slaan met behulp van de constructor.
   * Roep de methode `put` van het object `java.util.HashMap` aan voor elk bestand dat aan het gegenereerde formulier moet worden gekoppeld. Geef de volgende waarden door aan deze methode:

      * Een tekenreekswaarde die de naam van de bestandsbijlage opgeeft, inclusief de bestandsnaamextensie.

   * Een `com.adobe.idp.Document` -object dat de bestandsbijlage bevat.

   >[!NOTE]
   >
   >Herhaal deze stap voor elk bestand dat u aan het formulier wilt koppelen. Deze stap is optioneel en u kunt `null` doorgeven als u geen bestandsbijlagen wilt verzenden.

1. Een interactief PDF-formulier renderen

   Roep de methode `renderPDFForm` van het object `FormsServiceClient` aan en geef de volgende waarden door:

   * Een tekenreekswaarde die de naam van het formulierontwerp opgeeft, inclusief de bestandsnaamextensie. Als u verwijst naar een formulierontwerp dat deel uitmaakt van een Forms-toepassing, moet u het volledige pad opgeven, bijvoorbeeld `Applications/FormsApplication/1.0/FormsFolder/Loan.xdp` .
   * Een `com.adobe.idp.Document` -object dat gegevens bevat die met het formulier moeten worden samengevoegd. Wanneer u geen gegevens wilt samenvoegen, geeft u een leeg `com.adobe.idp.Document` -object door.
   * Een `PDFFormRenderSpec` -object dat uitvoeringsopties opslaat. Dit is een optionele parameter en u kunt `null` opgeven als u geen runtime-opties wilt opgeven.
   * Een `URLSpec` -object dat URI-waarden bevat die door de Forms-service worden vereist.
   * Een `java.util.HashMap` -object dat bestandsbijlagen opslaat. Dit is een optionele parameter en u kunt `null` opgeven als u geen bestanden aan het formulier wilt koppelen.

   De methode `renderPDFForm` retourneert een `FormsResult` -object dat een formuliergegevensstroom bevat die naar de webbrowser van de client moet worden geschreven.

1. De formuliergegevensstroom naar de webbrowser van de client schrijven

   * Maak een `com.adobe.idp.Document` -object door de methode `FormsResult` object `getOutputContent` aan te roepen.
   * Haal het inhoudstype van het object `com.adobe.idp.Document` op door de methode `getContentType` ervan aan te roepen.
   * Stel het inhoudstype van het `javax.servlet.http.HttpServletResponse` -object in door de methode `setContentType` ervan aan te roepen en het inhoudstype van het `com.adobe.idp.Document` -object door te geven.
   * Maak een `javax.servlet.ServletOutputStream` -object dat wordt gebruikt om de formuliergegevensstroom naar de webbrowser van de client te schrijven door de methode `javax.servlet.http.HttpServletResponse` object `getOutputStream` aan te roepen.
   * Maak een `java.io.InputStream` -object door de methode `com.adobe.idp.Document` object `getInputStream` aan te roepen.
   * Maak een bytearray en vul deze met de formuliergegevensstroom door de methode `read` van het object `InputStream` aan te roepen en de bytearray als een argument door te geven.
   * Roep de methode `write` van het object `javax.servlet.ServletOutputStream` aan om de gegevensstroom van het formulier naar de webbrowser van de client te verzenden. Geef de bytearray door aan de methode `write` .

## Een interactief PDF-formulier renderen met de webservice-API {#render-an-interactive-pdf-form-using-the-web-service-api}

Een interactief PDF-formulier renderen met de Forms API (webservice):

1. Projectbestanden opnemen

   * Maak Java-proxyklassen die gebruikmaken van de Forms-service WSDL.
   * Neem de Java-proxyklassen op in het klassepad.

1. Een Forms Client API-object maken

   Maak een `FormsService` -object en stel de verificatiewaarden in.

1. URI-waarden opgeven

   * Maak een `URLSpec` -object dat URI-waarden opslaat met behulp van de constructor.
   * Roep de methode `setApplicationWebRoot` van het object `URLSpec` aan en geef een tekenreekswaarde door die de hoofdmap van de toepassing vertegenwoordigt.
   * Roep de methode `setContentRootURI` van het `URLSpec` -object aan en geef een tekenreekswaarde door die de URI-waarde van de inhoudsbasis opgeeft. Zorg ervoor dat het formulierontwerp zich in de URI van de inhoudsbasis bevindt. Als niet, werpt de dienst van Forms een uitzondering. Geef `repository:///` op om naar de gegevensopslagruimte te verwijzen.
   * Roep de methode `setTargetURL` van het `URLSpec` -object aan en geef een tekenreekswaarde door die de doel-URL-waarde opgeeft waarnaar de formuliergegevens worden gepost. Als u de doel-URL in het formulierontwerp definieert, kunt u een lege tekenreeks doorgeven. U kunt ook de URL opgeven waarnaar een formulier wordt verzonden om berekeningen uit te voeren.

1. Bestanden aan het formulier koppelen

   * Maak een `java.util.HashMap` -object om bestandsbijlagen op te slaan met behulp van de constructor.
   * Roep de methode `put` van het object `java.util.HashMap` aan voor elk bestand dat aan het gegenereerde formulier moet worden gekoppeld. Geef de volgende waarden door aan deze methode:

      * Een tekenreekswaarde die de naam van de bestandsbijlage opgeeft, inclusief de bestandsextensie

   * Een `BLOB` -object dat de bestandsbijlage bevat

   >[!NOTE]
   >
   >Herhaal deze stap voor elk bestand dat u aan het formulier wilt koppelen.

1. Een interactief PDF-formulier renderen

   Roep de methode `renderPDFForm` van het object `FormsService` aan en geef de volgende waarden door:

   * Een tekenreekswaarde die de naam van het formulierontwerp opgeeft, inclusief de bestandsnaamextensie. Als u verwijst naar een formulierontwerp dat deel uitmaakt van een Forms-toepassing, moet u het volledige pad opgeven, bijvoorbeeld `Applications/FormsApplication/1.0/FormsFolder/Loan.xdp` .
   * Een `BLOB` -object dat gegevens bevat die met het formulier moeten worden samengevoegd. Geef `null` door als u geen gegevens wilt samenvoegen.
   * Een `PDFFormRenderSpec` -object dat uitvoeringsopties opslaat. Dit is een optionele parameter en u kunt `null` opgeven als u geen runtime-opties wilt opgeven.
   * Een `URLSpec` -object dat URI-waarden bevat die door de Forms-service worden vereist.
   * Een `java.util.HashMap` -object dat bestandsbijlagen opslaat. Dit is een optionele parameter en u kunt `null` opgeven als u geen bestanden aan het formulier wilt koppelen.
   * Een leeg `com.adobe.idp.services.holders.BLOBHolder` -object dat door de methode wordt gevuld. Hiermee slaat u het gerenderde PDF formulier op.
   * Een leeg `javax.xml.rpc.holders.LongHolder` -object dat door de methode wordt gevuld. (In dit argument wordt het aantal pagina&#39;s in het formulier opgeslagen.)
   * Een leeg `javax.xml.rpc.holders.StringHolder` -object dat door de methode wordt gevuld. (In dit argument wordt de waarde van de landinstelling opgeslagen.)
   * Een leeg `com.adobe.idp.services.holders.FormsResultHolder` -object dat de resultaten van deze bewerking bevat.

   Met de methode `renderPDFForm` wordt het `com.adobe.idp.services.holders.FormsResultHolder` -object dat als laatste argumentwaarde wordt doorgegeven, gevuld met een formuliergegevensstroom die naar de webbrowser van de client moet worden geschreven.

1. De formuliergegevensstroom naar de webbrowser van de client schrijven

   * Maak een `FormResult` -object door de waarde van het gegevenslid van het `com.adobe.idp.services.holders.FormsResultHolder` object `value` op te halen.
   * Maak een `BLOB` -object dat formuliergegevens bevat door de methode `FormsResult` object `getOutputContent` aan te roepen.
   * Haal het inhoudstype van het object `BLOB` op door de methode `getContentType` ervan aan te roepen.
   * Stel het inhoudstype van het `javax.servlet.http.HttpServletResponse` -object in door de methode `setContentType` ervan aan te roepen en het inhoudstype van het `BLOB` -object door te geven.
   * Maak een `javax.servlet.ServletOutputStream` -object dat wordt gebruikt om de formuliergegevensstroom naar de webbrowser van de client te schrijven door de methode `javax.servlet.http.HttpServletResponse` object `getOutputStream` aan te roepen.
   * Maak een bytearray en vul deze door de methode `getBinaryData` van het object `BLOB` aan te roepen. Hierdoor wordt de inhoud van het `FormsResult` -object toegewezen aan de bytearray.
   * Roep de methode `write` van het object `javax.servlet.http.HttpServletResponse` aan om de gegevensstroom van het formulier naar de webbrowser van de client te verzenden. Geef de bytearray door aan de methode `write` .

**schrijf de stroom van vormgegevens aan cliëntWeb browser**

Wanneer de Forms-service een formulier genereert, wordt een formuliergegevensstroom geretourneerd die u naar de webbrowser van de client moet schrijven. Wanneer het formulier naar de webbrowser van de client wordt geschreven, is het zichtbaar voor de gebruiker.
