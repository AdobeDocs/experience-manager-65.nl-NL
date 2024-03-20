---
title: Webtoepassingen maken die Forms renderen
description: Maak een webtoepassing die Java-servlets gebruikt om de Forms-service aan te roepen en formulieren te genereren. De Java-servlet fungeert als de koppeling tussen de Forms-service die een formulier retourneert en een clientwebbrowser.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/rendering_forms
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: operations
role: Developer
exl-id: 85e00003-8c8b-463a-b728-66af174be295
solution: Experience Manager, Experience Manager Forms
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '1832'
ht-degree: 0%

---

# Webtoepassingen maken die Forms renderen {#creating-web-applications-thatrenders-forms}

**Voorbeelden en voorbeelden in dit document gelden alleen voor AEM Forms in JEE-omgeving.**

## Webtoepassingen maken die Forms renderen {#creating-web-applications-that-renders-forms}

U kunt een webtoepassing maken die Java-servlets gebruikt om de Forms-service aan te roepen en formulieren te genereren. Een voordeel van het gebruik van een Java™ servlet is dat u de terugkeerwaarde van het proces aan cliëntbrowser kunt schrijven. Met andere woorden, een Java-servlet kan worden gebruikt als de koppeling tussen de Forms-service die een formulier retourneert en een clientwebbrowser.

>[!NOTE]
>
>In deze sectie wordt beschreven hoe u een webtoepassing maakt die een Java-servlet gebruikt die de Forms-service aanroept en op fragmenten gebaseerde formulieren weergeeft. (Zie [Forms renderen op basis van fragmenten](/help/forms/developing/rendering-forms-based-fragments.md).)

Met behulp van een Java-servlet kunt u een formulier naar een clientwebbrowser schrijven, zodat een klant gegevens in het formulier kan bekijken en invoeren. Nadat de webgebruiker het formulier met gegevens heeft gevuld, klikt hij op een verzendknop op het formulier om informatie terug te sturen naar de Java-server, waar de gegevens kunnen worden opgehaald en verwerkt. De gegevens kunnen bijvoorbeeld naar een ander proces worden verzonden.

In deze sectie wordt besproken hoe u een webtoepassing kunt maken waarmee de gebruiker op Amerika gebaseerde formuliergegevens of op Canada gebaseerde formuliergegevens kan selecteren, zoals in de volgende afbeelding wordt getoond.

![cw_cw_fragmentwebclient](assets/cw_cw_fragmentwebclient.png)

Het weergegeven formulier is een formulier dat is gebaseerd op fragmenten. Als de gebruiker Amerikaanse gegevens selecteert, gebruikt het geretourneerde formulier fragmenten op basis van Amerikaanse gegevens. De voettekst van het formulier bevat bijvoorbeeld een Amerikaans adres, zoals in de volgende afbeelding wordt getoond.

![cw_cw_fragementformfooter](assets/cw_cw_fragementformfooter.png)

Als de gebruiker Canadese gegevens selecteert, bevat het geretourneerde formulier ook een Canadees adres, zoals in de volgende afbeelding wordt getoond.

![cw_cw_fragementformfootercnd](assets/cw_cw_fragementformfootercnd.png)

>[!NOTE]
>
>Zie voor informatie over het maken van formulierontwerpen op basis van fragmenten [Forms Designer](https://www.adobe.com/go/learn_aemforms_designer_63).

**Voorbeeldbestanden**

In deze sectie worden voorbeeldbestanden gebruikt die zich op de volgende locatie kunnen bevinden:

&lt;*Installatiemap van Forms Designer*>/Samples/Forms/Purchase Order/Form Fragments

waarbij &lt;*installatiemap*> is het installatiepad. Ten behoeve van de clienttoepassing is het bestand Purchase Order Dynamic.xdp gekopieerd van deze installatielocatie en geïmplementeerd in een Forms-toepassing met de naam *Applications/FormsApplication*. Het bestand Purchase Order Dynamic.xdp wordt in een map met de naam FormsFolder geplaatst. Op dezelfde manier worden de fragmenten in de map Fragments geplaatst, zoals in de volgende afbeelding wordt getoond.

![cw_cw_fragmentsrepository](assets/cw_cw_fragmentsrepository.png)

Als u het formulierontwerp Purchase Order Dynamic.xdp wilt openen, geeft u `Applications/FormsApplication/1.0/FormsFolder/Purchase Order Dynamic.xdp` als de formuliernaam (de eerste parameter die aan de `renderPDFForm` methode) en `repository:///` als de URI-waarde van de inhoudsbasis.

De XML-gegevensbestanden die door de webtoepassing worden gebruikt, zijn verplaatst van de map Data naar `C:\Adobe`(het bestandssysteem dat behoort tot de J2EE-toepassingsserver die als host fungeert voor AEM Forms). De bestandsnamen zijn Purchase Order *Canada.xml* en inkooporder *US.xml*.

>[!NOTE]
>
>Voor informatie over het maken van een Forms-toepassing met Workbench gaat u naar [Workbench Help](https://www.adobe.com/go/learn_aemforms_workbench_63).

### Overzicht van de stappen {#summary-of-steps}

Voer de volgende stappen uit om een webtoepassing te maken die formulieren weergeeft op basis van fragmenten:

1. Maak een webproject.
1. Maak Java-toepassingslogica die de Java-servlet vertegenwoordigt.
1. Maak de webpagina voor de webtoepassing.
1. Verpak de Webtoepassing aan een dossier van WAR.
1. Implementeer het WAR-bestand op de J2EE-toepassingsserver.
1. Test uw webtoepassing.

>[!NOTE]
>
>Sommige van deze stappen zijn afhankelijk van de J2EE-toepassing waarop AEM Forms wordt geïmplementeerd. De methode die u bijvoorbeeld gebruikt om een WAR-bestand te implementeren, is afhankelijk van de J2EE-toepassingsserver die u gebruikt. In deze sectie wordt ervan uitgegaan dat AEM Forms wordt geïmplementeerd op JBoss®.

### Een webproject maken {#creating-a-web-project}

De eerste stap voor het maken van een webtoepassing die een Java-servlet bevat die de Forms-service kan aanroepen, is het maken van een webproject. De Java-IDE waarop dit document is gebaseerd, is Eclipse 3.3. Gebruikend IDE van de Verduistering, creeer een Webproject en voeg de vereiste JAR dossiers aan uw project toe. Voeg ten slotte een HTML-pagina met de naam *index.html* en een Java-servlet voor uw project.

In de volgende lijst worden de JAR-bestanden weergegeven die u aan uw webproject moet toevoegen:

* adobe-forms-client.jar
* adobe-livecycle-client.jar
* adobe-usermanager-client.jar
* adobe-utilities.jar

Ga voor de locatie van deze JAR-bestanden naar [Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files).

**Een webproject maken:**

1. Eclipse starten en klikken **Bestand** >  **Nieuw project**.
1. In de **Nieuw project** dialoogvenster selecteert u **Web** > **Dynamisch webproject**.
1. Type `FragmentsWebApplication` voor de naam van uw project en klik dan **Voltooien**.

**U voegt als volgt vereiste JAR-bestanden toe aan uw project:**

1. Van het venster van de Ontdekkingsreiziger van het Project, klik met de rechtermuisknop aan `FragmentsWebApplication` project en selecteer **Eigenschappen**.
1. Klikken **Java-ontwikkelpad** en klik vervolgens op de knop **Bibliotheken** tab.
1. Klik op de knop **Externe JAR&#39;s toevoegen** en blader naar de JAR-bestanden die u wilt opnemen.

**Een Java-servlet toevoegen aan uw project:**

1. Van het venster van de Ontdekkingsreiziger van het Project, klik met de rechtermuisknop aan `FragmentsWebApplication` project en selecteer **Nieuw** >  **Overige**.
1. Breid uit **Web** map, selecteert u **Servlet** en klik vervolgens op **Volgende**.
1. Typ in het dialoogvenster Servlet maken `RenderFormFragment` voor de naam van de servlet en klik vervolgens op **Voltooien**.

**Een HTML-pagina toevoegen aan uw project:**

1. Van het venster van de Ontdekkingsreiziger van het Project, klik met de rechtermuisknop aan `FragmentsWebApplication` project en selecteer **Nieuw** > **Overige**.
1. Breid uit **Web** map, selecteert u **HTML** en klik op **Volgende**.
1. Typ in het dialoogvenster Nieuwe HTML `index.html` voor de bestandsnaam en klik vervolgens op **Voltooien**.

>[!NOTE]
>
>Voor informatie over het maken van de pagina HTML die de `RenderFormFragment` Java servlet, zie [De webpagina maken](/help/forms/developing/rendering-forms.md#creating-the-web-page).

### Java-toepassingslogica voor de servlet maken {#creating-java-application-logic-for-the-servlet}

U maakt Java-toepassingslogica die de Forms-service aanroept vanuit de Java-servlet. De volgende code toont de syntaxis van `RenderFormFragment` Java Server:

```java
     public class RenderFormFragment extends HttpServlet implements Servlet {
         public void doGet(HttpServletRequest req, HttpServletResponse resp
         throws ServletException, IOException {
         doPost(req,resp);
 
         }
         public void doPost(HttpServletRequest req, HttpServletResponse resp
         throws ServletException, IOException {
             //Add code here to invoke the Forms service
             }
```

Normaal gesproken plaatst u geen clientcode in een Java-servlet `doGet` of `doPost` methode. Een betere programmeerpraktijk is deze code binnen een afzonderlijke klasse te plaatsen, de klasse van binnen te concretiseren `doPost` of `doGet` methode) en roept de aangewezen methodes aan. Voor de beknoptheid van de code worden de codevoorbeelden in deze sectie echter tot een minimum beperkt en worden codevoorbeelden in de `doPost` methode.

Als u een formulier wilt genereren op basis van fragmenten met de API van de Forms-service, voert u de volgende taken uit:

1. Neem client-JAR-bestanden, zoals adobe-forms-client.jar, op in het klassenpad van uw Java-project. Voor informatie over de locatie van deze bestanden raadpleegt u [Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files).
1. Hiermee haalt u de waarde op van het keuzerondje dat vanuit het HTML-formulier wordt verzonden en geeft u aan of Amerikaanse of Canadese gegevens moeten worden gebruikt. Als American wordt verzonden, maakt u een `com.adobe.idp.Document` die gegevens in het *Purchase Order US.xml*. En als Canadees, creeer dan `com.adobe.idp.Document` die gegevens in het *Purchase Order Canada.xml* bestand.
1. Een `ServiceClientFactory` object dat verbindingseigenschappen bevat. (Zie [Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties).)
1. Een `FormsServiceClient` object door de constructor ervan te gebruiken en de `ServiceClientFactory` object.
1. Een `URLSpec` object dat URI-waarden opslaat met de constructor ervan.
1. De `URLSpec` object `setApplicationWebRoot` en geeft een tekenreekswaarde door die de hoofdmap van de toepassing vertegenwoordigt.
1. De `URLSpec` object `setContentRootURI` methode en geef een tekenreekswaarde door die de URI-waarde van de inhoudsbasis opgeeft. Zorg ervoor dat het formulierontwerp en de fragmenten zich in de URI van de basisinhoud bevinden. Als niet, werpt de dienst van Forms een uitzondering. Als u naar de AEM Forms-opslagplaats wilt verwijzen, geeft u `repository://`.
1. De `URLSpec` object `setTargetURL` en geeft een tekenreekswaarde door die de doel-URL-waarde opgeeft waarnaar formuliergegevens worden gepost. Als u de doel-URL in het formulierontwerp definieert, kunt u een lege tekenreeks doorgeven. U kunt ook de URL opgeven waarnaar een formulier wordt verzonden om berekeningen uit te voeren.
1. De `FormsServiceClient` object `renderPDFForm` en geeft de volgende waarden door:

   * Een tekenreekswaarde die de naam van het formulierontwerp opgeeft, inclusief de bestandsnaamextensie.
   * A `com.adobe.idp.Document` -object dat gegevens bevat die met het formulier moeten worden samengevoegd (gemaakt in stap 2).
   * A `PDFFormRenderSpec` -object dat uitvoeringsopties opslaat. Zie voor meer informatie [AEM Forms API-naslag](https://www.adobe.com/go/learn_aemforms_javadocs_63_en).
   * A `URLSpec` object dat URI-waarden bevat die door de Forms-service worden vereist om een formulier te genereren op basis van fragmenten.
   * A `java.util.HashMap` object waarin bestandsbijlagen zijn opgeslagen. Dit is een optionele parameter en u kunt `null` als u geen bestanden aan het formulier wilt koppelen.

   De `renderPDFForm` methode retourneert een `FormsResult` object dat een formuliergegevensstroom bevat die naar de webbrowser van de client moet worden geschreven.

1. Een `com.adobe.idp.Document` door het object aan te roepen `FormsResult` object &#39;s `getOutputContent` methode.
1. Hiermee wordt het inhoudstype van het dialoogvenster `com.adobe.idp.Document` object aanroepen `getContentType` methode.
1. Stel de `javax.servlet.http.HttpServletResponse` inhoudstype van object door het aan te roepen `setContentType` en geeft u het inhoudstype van de `com.adobe.idp.Document` object.
1. Een `javax.servlet.ServletOutputStream` object dat wordt gebruikt om de formuliergegevensstroom naar de webbrowser van de client te schrijven door het aanroepen van de `javax.servlet.http.HttpServletResponse` object `getOutputStream` methode.
1. Een `java.io.InputStream` door het object aan te roepen `com.adobe.idp.Document` object `getInputStream` methode.
1. Maak een bytearray die deze met de formuliergegevensstroom vult door de `InputStream` object `read`en de bytearray doorgeven als een argument.
1. De `javax.servlet.ServletOutputStream` object `write` methode om de formuliergegevensstroom naar de webbrowser van de client te verzenden. Geef de bytearray door aan de `write` methode.

In het volgende codevoorbeeld ziet u het Java-servlet dat de Forms-service activeert en een formulier genereert op basis van fragmenten.

```java
 /*
     * This Java Quick Start uses the following JAR files
     * 1. adobe-forms-client.jar
     * 2. adobe-livecycle-client.jar
     * 3. adobe-usermanager-client.jar
     *
     * (Because Forms quick starts are implemented as Java servlets, it is
     * not necessary to include J2EE specific JAR files - the Java project
     * that contains this quick start is exported as a WAR file which
     * is deployed to the J2EE application server)
     *
     * These JAR files are in the following path:
     * <install directory>/sdk/client-libs
     *
     * For complete details about the location of these JAR files,
     * see "Including AEM Forms library files" in Programming with AEM forms
     */
 import java.io.File;
 import java.io.FileInputStream;
 import java.io.IOException;
 import java.io.PrintWriter;
 
 import javax.servlet.Servlet;
 import javax.servlet.ServletException;
 import javax.servlet.ServletOutputStream;
 import javax.servlet.http.HttpServlet;
 import javax.servlet.http.HttpServletRequest;
 import javax.servlet.http.HttpServletResponse;
 import com.adobe.livecycle.formsservice.client.*;
 import java.util.*;
 import java.io.InputStream;
 import java.net.URL;
 
 import com.adobe.idp.Document;
 import com.adobe.idp.dsc.clientsdk.ServiceClientFactory;
 import com.adobe.idp.dsc.clientsdk.ServiceClientFactoryProperties;
 
 public class RenderFormFragment extends HttpServlet implements Servlet {
 
     public void doGet(HttpServletRequest req, HttpServletResponse resp)
         throws ServletException, IOException {
             doPost(req,resp);
 
     }
     public void doPost(HttpServletRequest req, HttpServletResponse resp)
     throws ServletException, IOException {
 
 
 
         try{
             //Set connection properties required to invoke AEM Forms
             Properties connectionProps = new Properties();
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_DEFAULT_SOAP_ENDPOINT, "https://'[server]:[port]'");
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_TRANSPORT_PROTOCOL,ServiceClientFactoryProperties.DSC_SOAP_PROTOCOL);
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_SERVER_TYPE, "JBoss");
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_CREDENTIAL_USERNAME, "administrator");
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_CREDENTIAL_PASSWORD, "password");
 
             //Get the value of selected radio button
             String radioValue = req.getParameter("radio");
 
             //Create an Document object to store form data
             Document oInputData = null;
 
             //The value of the radio button determines the form data to use
             //which determines which fragments used in the form
             if (radioValue.compareTo("AMERICAN") == 0)            {
                 FileInputStream myData = new FileInputStream("C:\\Adobe\Purchase Order US.xml");
                 oInputData = new Document(myData);
             }
             else if (radioValue.compareTo("CANADIAN") == 0)            {
                 FileInputStream myData = new FileInputStream("C:\\Adobe\Purchase Order Canada.xml");
                 oInputData = new Document(myData);
             }
 
             //Create a ServiceClientFactory object
             ServiceClientFactory myFactory = ServiceClientFactory.createInstance(connectionProps);
 
             //Create a FormsServiceClient object
             FormsServiceClient formsClient = new FormsServiceClient(myFactory);
 
             //Set the parameter values for the renderPDFForm method
             String formName = "Applications/FormsApplication/1.0/FormsFolder/Purchase Order Dynamic.xdp";
 
             //Cache the PDF form
             PDFFormRenderSpec pdfFormRenderSpec = new PDFFormRenderSpec();
             pdfFormRenderSpec.setCacheEnabled(new Boolean(true));
 
             //Specify URI values that are required to render a form
             //design based on fragments
             URLSpec uriValues = new URLSpec();
             uriValues.setApplicationWebRoot("https://'[server]:[port]'/RenderFormFragment");
             uriValues.setContentRootURI("repository:///");
             uriValues.setTargetURL("https://'[server]:[port]'/FormsServiceClientApp/HandleData");
 
             //Invoke the renderPDFForm method and write the
             //results to a client web browser
             FormsResult formOut = formsClient.renderPDFForm(
                         formName,               //formQuery
                         oInputData,             //inDataDoc
                         pdfFormRenderSpec,      //PDFFormRenderSpec
                         uriValues,                //urlSpec
                         null                    //attachments
                         );
 
             //Create a Document object that stores form data
             Document myData = formOut.getOutputContent();
 
             //Get the content type of the response and
             //set the HttpServletResponse object’s content type
             String contentType = myData.getContentType();
             resp.setContentType(contentType);
 
             //Create a ServletOutputStream object
             ServletOutputStream oOutput = resp.getOutputStream();
 
             //Create an InputStream object
             InputStream inputStream = myData.getInputStream();
 
             //Write the data stream to the web browser
             byte[] data = new byte[4096];
             int bytesRead = 0;
             while ((bytesRead = inputStream.read(data)) > 0)
             {
                 oOutput.write(data, 0, bytesRead);
             }
 
         }catch (Exception e) {
              System.out.println("The following exception occurred: "+e.getMessage());
       }
     }
 }
```

### De webpagina maken {#creating-the-web-page}

De index.html-webpagina biedt een ingangspunt voor de Java-server en roept de Forms-service aan. Deze webpagina is een basisformulier voor HTML met twee keuzerondjes en een verzendknop. De naam van de keuzerondjes is keuzerondjes. Wanneer de gebruiker op de verzendknop klikt, worden formuliergegevens naar de `RenderFormFragment` Java servlet.

De Java-servlet legt de gegevens vast die vanuit de HTML-pagina zijn gepost met behulp van de volgende Java-code:

```java
             Document oInputData = null;
 
             //Get the value of selected radio button
             String radioValue = req.getParameter("radio");
 
             //The value of the radio button determines the form data to use
             //which determines which fragments used in the form
             if (radioValue.compareTo("AMERICAN") == 0)            {
                 FileInputStream myData = new FileInputStream("C:\\Adobe\Purchase Order US.xml");
                 oInputData = new Document(myData);
             }
             else if (radioValue.compareTo("CANADIAN") == 0)            {
                 FileInputStream myData = new FileInputStream("C:\\Adobe\Purchase Order Canada.xml");
                 oInputData = new Document(myData);
             }
```

De volgende HTML-code bevindt zich in het bestand index.html dat tijdens de installatie van de ontwikkelomgeving is gemaakt. (Zie [Een webproject maken](/help/forms/developing/rendering-forms.md#creating-a-web-project).)

```xml
 <!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN" "https://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">
 <html xmlns="https://www.w3.org/1999/xhtml">
 <head>
 <meta http-equiv="Content-Type" content="text/html; charset=utf-8" />
 <title>Untitled Document</title>
 </head>
 
 <body>
 <form name="myform" action="https://'[server]:[port]'/FragmentsWebApplication/RenderFormFragment" method="post">
      <table>
      <tr>
        <th>Forms Fragment Web Client</th>
      </tr>
      <tr>
        <td>
          <label>
          <input type="radio" name="radio" id="radio_Data" value="CANADIAN" />
          Canadian data<br />
          </label>
          <p>
            <label>
            <input type="radio" name="radio" id="radio_Data" value="AMERICAN" checked/>
            American data</label>
          </p>
        </td>
      </tr>
      <tr>
      <td>
        <label>
          <input type="submit" name="button_Submit" id="button_Submit" value="Submit" />
            </label>
            </td>
         </tr>
        </table>
      </form>
 </body>
 </html>
```

### De webtoepassing verpakken {#packaging-the-web-application}

Als u de Java-servlet wilt implementeren die de Forms-service aanroept, moet u uw webtoepassing verpakken naar een WAR-bestand. Zorg ervoor dat externe JAR-bestanden waarvan de bedrijfslogica van de component afhankelijk is, zoals adobe-livecycle-client.jar en adobe-forms-client.jar, ook worden opgenomen in het WAR-bestand.

**Een webtoepassing verpakken naar een WAR-bestand:**

1. Van de **Project Explorer** venster, klikt u met de rechtermuisknop op de knop `FragmentsWebApplication` project en selecteer **Exporteren** > **WAR-bestand**.
1. In de **Webmodule** tekstvak, tekst `FragmentsWebApplication` voor de naam van het Java-project.
1. In de **Doel** tekstvak, tekst `FragmentsWebApplication.war`**voor de** bestandsnaam, geef de locatie voor het WAR-bestand op en klik op Voltooien.

### WAR-bestand implementeren op de J2EE-toepassingsserver {#deploying-the-war-file-to-the-j2ee-application-server}

U kunt het WAR-bestand implementeren op de J2EE-toepassingsserver waarop AEM Forms is geïmplementeerd. Nadat het WAR-bestand is geïmplementeerd, kunt u de webpagina HTML openen met een webbrowser.

**Het WAR-bestand implementeren op de J2EE-toepassingsserver:**

* Het WAR-bestand kopiëren van het exportpad naar `[Forms Install]\Adobe\Adobe Experience Manager Forms\jboss\server\all\deploy`.

### Uw webtoepassing testen {#testing-your-web-application}

Nadat u de webtoepassing hebt geïmplementeerd, kunt u deze testen met een webbrowser. Ervan uitgaande dat u dezelfde computer gebruikt als die waarop AEM Forms wordt gehost, kunt u de volgende URL opgeven:

* http://localhost:8080/FragmentsWebApplication/index.html

  Selecteer een keuzerondje en klik op Verzenden. Een formulier dat is gebaseerd op fragmenten, wordt weergegeven in de webbrowser. Zie het logbestand van de J2EE-toepassingsserver als er zich problemen voordoen.
