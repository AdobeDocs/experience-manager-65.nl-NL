---
title: Webtoepassingen maken die formulieren renderen
seo-title: Webtoepassingen maken die formulieren renderen
description: 'null'
seo-description: 'null'
uuid: 00de10c5-79bd-4d8a-ae18-32f1fd2623bf
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/rendering_forms
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: operations
discoiquuid: f29b089e-8902-4744-81c5-15ee41ba8069
translation-type: tm+mt
source-git-commit: 1343cc33a1e1ce26c0770a3b49317e82353497ab
workflow-type: tm+mt
source-wordcount: '1831'
ht-degree: 0%

---


# Webtoepassingen maken die formulieren renderen {#creating-web-applications-thatrenders-forms}

## Webtoepassingen maken die formulieren renderen {#creating-web-applications-that-renders-forms}

U kunt een webtoepassing maken die Java-servlets gebruikt om de Forms-service aan te roepen en formulieren te genereren. Een voordeel van het gebruik van een Java™ servlet is dat u de terugkeerwaarde van het proces aan cliëntbrowser kunt schrijven. Een Java-servlet kan dus worden gebruikt als de koppeling tussen de service Forms die een formulier retourneert en een webbrowser van de client.

>[!NOTE]
>
>In deze sectie wordt beschreven hoe u een webtoepassing maakt die een Java-servlet gebruikt die de service Forms aanroept en op fragmenten gebaseerde formulieren weergeeft. (Zie Formulieren [renderen op basis van fragmenten](/help/forms/developing/rendering-forms-based-fragments.md).)

Met behulp van een Java-servlet kunt u een formulier naar een clientwebbrowser schrijven, zodat een klant gegevens in het formulier kan bekijken en invoeren. Nadat de webgebruiker het formulier met gegevens heeft gevuld, klikt hij op een verzendknop op het formulier om informatie terug te sturen naar de Java-server waar de gegevens kunnen worden opgehaald en verwerkt. De gegevens kunnen bijvoorbeeld naar een ander proces worden verzonden.

In deze sectie wordt besproken hoe u een webtoepassing kunt maken waarmee de gebruiker op Amerika gebaseerde formuliergegevens of op Canada gebaseerde formuliergegevens kan selecteren, zoals in de volgende afbeelding wordt getoond.

![cw_cw_fragmentwebclient](assets/cw_cw_fragmentwebclient.png)

Het weergegeven formulier is een formulier dat is gebaseerd op fragmenten. Als de gebruiker Amerikaanse gegevens selecteert, gebruikt het geretourneerde formulier fragmenten op basis van Amerikaanse gegevens. De voettekst van het formulier bevat bijvoorbeeld een Amerikaans adres, zoals in de volgende afbeelding wordt getoond.

![cw_cw_fragementformfooter](assets/cw_cw_fragementformfooter.png)

Als de gebruiker Canadese gegevens selecteert, bevat het geretourneerde formulier ook een Canadees adres, zoals in de volgende afbeelding wordt getoond.

![cw_cw_fragementformfootercnd](assets/cw_cw_fragementformfootercnd.png)

>[!NOTE]
>
>Zie [Forms Designer](https://www.adobe.com/go/learn_aemforms_designer_63)voor informatie over het maken van formulierontwerpen op basis van fragmenten.

**Voorbeeldbestanden**

In deze sectie worden voorbeeldbestanden gebruikt die zich op de volgende locatie bevinden:

&lt;*Forms Designer-installatiemap*>/Samples/Forms/Purchase Order/Form Fragments

waarbij &lt;*install directory*> het installatiepad is. Ten behoeve van de clienttoepassing is het bestand Purchase Order Dynamic.xdp gekopieerd van deze installatielocatie en geïmplementeerd in een Forms-toepassing met de naam *Applications/FormsApplication*. Het bestand Purchase Order Dynamic.xdp wordt in een map met de naam FormsFolder geplaatst. Op dezelfde manier worden de fragmenten in de map Fragments geplaatst, zoals in de volgende afbeelding wordt getoond.

![cw_cw_fragmentsrepository](assets/cw_cw_fragmentsrepository.png)

Als u toegang wilt krijgen tot het formulierontwerp Purchase Order Dynamic.xdp, geeft u `Applications/FormsApplication/1.0/FormsFolder/Purchase Order Dynamic.xdp` de naam van het formulier op (de eerste parameter die aan de `renderPDFForm` methode is doorgegeven) en `repository:///` de URI-waarde van de basisinhoud.

De XML-gegevensbestanden die door de webtoepassing worden gebruikt, zijn verplaatst van de map Data naar `C:\Adobe`(het bestandssysteem dat hoort bij de J2EE-toepassingsserver die als host fungeert voor AEM Forms). De bestandsnamen zijn Purchase Order *Canada.xml* en Purchase Order *US.xml*.

>[!NOTE]
>
>Zie de Help bij [Workbench voor informatie over het maken van een Forms-toepassing met Workbench](https://www.adobe.com/go/learn_aemforms_workbench_63).

### Overzicht van de stappen {#summary-of-steps}

Voer de volgende stappen uit om een webtoepassing te maken die formulieren weergeeft op basis van fragmenten:

1. Maak een nieuw webproject.
1. Maak Java-toepassingslogica die de Java-servlet vertegenwoordigt.
1. Maak de webpagina voor de webtoepassing.
1. Verpak de Webtoepassing aan een dossier van WAR.
1. Implementeer het WAR-bestand op de J2EE-toepassingsserver.
1. Test uw webtoepassing.

>[!NOTE]
>
>Sommige van deze stappen hangen van de toepassing J2EE af waarop AEM Forms wordt opgesteld. De methode die u bijvoorbeeld gebruikt om een WAR-bestand te implementeren, is afhankelijk van de J2EE-toepassingsserver die u gebruikt. In deze sectie wordt ervan uitgegaan dat AEM Forms worden geïmplementeerd op JBoss®.

### Een webproject maken {#creating-a-web-project}

De eerste stap voor het maken van een webtoepassing die een Java-servlet bevat die de service Forms kan aanroepen, is het maken van een nieuw webproject. De Java-IDE waarop dit document is gebaseerd, is Eclipse 3.3. Gebruikend IDE van de Verduistering, creeer een Webproject en voeg de vereiste JAR dossiers aan uw project toe. Voeg ten slotte een HTML-pagina met de naam *index.html* en een Java-servlet toe aan uw project.

In de volgende lijst worden de JAR-bestanden weergegeven die u aan uw webproject moet toevoegen:

* adobe-forms-client.jar
* adobe-livecycle-client.jar
* adobe-usermanager-client.jar
* adobe-utilities.jar

Zie [Including AEM Forms Java library files](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)voor de locatie van deze JAR-bestanden.

**Een webproject maken:**

1. Start Eclipse en klik op **Bestand** > **Nieuw project**.
1. Selecteer in het dialoogvenster **Nieuw project** de optie **Web** > **Dynamisch webproject**.
1. Typ `FragmentsWebApplication` de naam van het project en klik op **Voltooien**.

**U voegt als volgt vereiste JAR-bestanden toe aan uw project:**

1. Van het venster van de Ontdekkingsreiziger van het Project, klik het `FragmentsWebApplication` project met de rechtermuisknop aan en selecteer **Eigenschappen**.
1. Klik op **Java-bouwpad** en klik vervolgens op het tabblad **Bibliotheken** .
1. Klik op de knop Externe JAR&#39;s **toevoegen** en blader naar de JAR-bestanden die u wilt opnemen.

**Een Java-servlet toevoegen aan uw project:**

1. Van het venster van de Ontdekkingsreiziger van het Project, klik het `FragmentsWebApplication` project met de rechtermuisknop aan en selecteer **Nieuw** > **Andere**.
1. Vouw de **webmap** uit, selecteer **Servlet** en klik op **Volgende**.
1. Typ in het dialoogvenster Servlet maken `RenderFormFragment` de naam van de servlet en klik op **Voltooien**.

**Een HTML-pagina toevoegen aan uw project:**

1. Van het venster van de Ontdekkingsreiziger van het Project, klik het `FragmentsWebApplication` project met de rechtermuisknop aan en selecteer **Nieuw** > **Andere**.
1. Vouw de map **Web** uit, selecteer **HTML** en klik op **Volgende**.
1. Typ in het dialoogvenster Nieuwe HTML `index.html` de bestandsnaam en klik op **Voltooien**.

>[!NOTE]
>
>Zie `RenderFormFragment` Webpagina[maken voor informatie over het maken van de HTML-pagina die het](/help/forms/developing/rendering-forms.md#creating-the-web-page)Java-servlet activeert.

### Java-toepassingslogica voor de servlet maken {#creating-java-application-logic-for-the-servlet}

U maakt Java-toepassingslogica waarmee de service Forms wordt geactiveerd vanuit het Java-servlet. De volgende code toont de syntaxis van `RenderFormFragment` Java Servlet:

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

Normaal gesproken plaatst u geen clientcode in een Java-servlet `doGet` of - `doPost` methode. Een betere programmeerpraktijk is deze code binnen een afzonderlijke klasse te plaatsen, de klasse van binnen de `doPost` methode (of `doGet` methode) te concretiseren, en de aangewezen methodes te roepen. Voor de beknoptheid van code worden de codevoorbeelden in deze sectie echter tot een minimum beperkt en worden codevoorbeelden in de `doPost` methode geplaatst.

Als u een formulier wilt genereren op basis van fragmenten met de API van de Forms-service, voert u de volgende taken uit:

1. Neem client-JAR-bestanden, zoals adobe-forms-client.jar, op in het klassenpad van uw Java-project. Zie [Including AEM Forms Java library files](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)voor informatie over de locatie van deze bestanden.
1. Haal de waarde op van het keuzerondje dat vanuit het HTML-formulier wordt verzonden en geef aan of Amerikaanse of Canadese gegevens moeten worden gebruikt. Als er een Amerikaans bestand wordt verzonden, maakt u een `com.adobe.idp.Document` waarin de gegevens worden opgeslagen die zich bevinden in het bestand *Purchase Order US.xml*. Op dezelfde manier maakt u, indien Canadees, een `com.adobe.idp.Document` bestand waarin de gegevens in het bestand *Purchase Order Canada.xml* zijn opgeslagen.
1. Maak een `ServiceClientFactory` object dat verbindingseigenschappen bevat. (Zie Verbindingseigenschappen [instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties).)
1. Maak een `FormsServiceClient` object door de constructor ervan te gebruiken en het `ServiceClientFactory` object door te geven.
1. Maak een `URLSpec` object dat URI-waarden opslaat met de constructor ervan.
1. Roep de `URLSpec` methode van het `setApplicationWebRoot` object aan en geef een tekenreekswaarde door die de hoofdmap van de toepassing vertegenwoordigt.
1. Roep de `URLSpec` methode van het `setContentRootURI` object aan en geef een tekenreekswaarde door die de URI-waarde van de inhoudshoofdmap opgeeft. Zorg ervoor dat het formulierontwerp en de fragmenten zich in de URI van de inhoudsbasis bevinden. Als niet, werpt de dienst van Vormen een uitzondering. Geef een verwijzing op naar de gegevensopslagruimte van AEM Forms `repository://`.
1. Roep de `URLSpec` methode van het `setTargetURL` object aan en geef een tekenreekswaarde door die de doel-URL-waarde opgeeft waarnaar formuliergegevens worden gepost. Als u de doel-URL in het formulierontwerp definieert, kunt u een lege tekenreeks doorgeven. U kunt ook de URL opgeven waarnaar een formulier wordt verzonden om berekeningen uit te voeren.
1. Roep de methode van het `FormsServiceClient` `renderPDFForm` object aan en geef de volgende waarden door:

   * Een tekenreekswaarde die de naam van het formulierontwerp opgeeft, inclusief de bestandsnaamextensie.
   * Een `com.adobe.idp.Document` object dat gegevens bevat die met het formulier moeten worden samengevoegd (gemaakt in stap 2).
   * Een `PDFFormRenderSpec` object dat uitvoeringsopties opslaat. Zie [AEM Forms API Reference](https://www.adobe.com/go/learn_aemforms_javadocs_63_en)voor meer informatie.
   * Een `URLSpec` object dat URI-waarden bevat die vereist zijn voor de Forms-service om een formulier te genereren op basis van fragmenten.
   * Een `java.util.HashMap` object dat bestandsbijlagen opslaat. Dit is een optionele parameter en u kunt opgeven `null` of u geen bestanden aan het formulier wilt koppelen.

   De `renderPDFForm` methode retourneert een `FormsResult` object dat een formuliergegevensstroom bevat die naar de webbrowser van de client moet worden geschreven.

1. Maak een `com.adobe.idp.Document` object door de `FormsResult` methode van het `getOutputContent` object aan te roepen.
1. Haal het inhoudstype van het `com.adobe.idp.Document` object op door de `getContentType` methode ervan aan te roepen.
1. Stel het inhoudstype van het `javax.servlet.http.HttpServletResponse` object in door de bijbehorende `setContentType` methode op te roepen en het inhoudstype van het `com.adobe.idp.Document` object door te geven.
1. Maak een `javax.servlet.ServletOutputStream` object dat wordt gebruikt om de gegevensstroom van het formulier naar de webbrowser van de client te schrijven door de `javax.servlet.http.HttpServletResponse` methode van het `getOutputStream` object aan te roepen.
1. Maak een `java.io.InputStream` object door de `com.adobe.idp.Document` methode van het `getInputStream` object aan te roepen.
1. Maak een bytearray die deze met de formuliergegevensstroom vult door de `InputStream` `read`methode van het object aan te roepen en de bytearray als een argument door te geven.
1. Roep de `javax.servlet.ServletOutputStream` methode van het `write` object aan om de formuliergegevensstroom naar de webbrowser van de client te verzenden. Geef de bytearray door aan de `write` methode.

In het volgende codevoorbeeld ziet u het Java-servlet dat de service Forms aanroept en een formulier genereert op basis van fragmenten.

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
     * These JAR files are located in the following path:
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

De webpagina index.html biedt een ingangspunt voor de Java-server en roept de service Forms aan. Deze webpagina is een standaard-HTML-formulier dat twee keuzerondjes en een verzendknop bevat. De naam van de keuzerondjes is keuzerondjes. Wanneer de gebruiker op de verzendknop klikt, worden de formuliergegevens naar de `RenderFormFragment` Java-server verzonden.

De Java-servlet legt de gegevens vast die vanuit de HTML-pagina zijn gepost met de volgende Java-code:

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

De volgende HTML-code bevindt zich in het bestand index.html dat tijdens de installatie van de ontwikkelomgeving is gemaakt. (Zie [Een webproject](/help/forms/developing/rendering-forms.md#creating-a-web-project)maken.)

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

Als u de Java-servlet wilt implementeren die de service Forms aanroept, moet u uw webtoepassing verpakken naar een WAR-bestand. Zorg ervoor dat externe JAR-bestanden waarvan de bedrijfslogica van de component afhankelijk is, zoals adobe-livecycle-client.jar en adobe-forms-client.jar, ook worden opgenomen in het WAR-bestand.

**Een webtoepassing verpakken naar een WAR-bestand:**

1. Klik in het venster **Projectverkenner** met de rechtermuisknop op het `FragmentsWebApplication` project en selecteer **Exporteren** > **WAR-bestand**.
1. Typ in het tekstvak van de module **** Web de naam `FragmentsWebApplication` van het Java-project.
1. Typ in het tekstvak **Doel** de bestandsnaam, geef de locatie van het WAR-bestand op `FragmentsWebApplication.war`****en klik op Voltooien.

### WAR-bestand implementeren op de J2EE-toepassingsserver {#deploying-the-war-file-to-the-j2ee-application-server}

U kunt het dossier van WAR aan de J2EE toepassingsserver opstellen waarop AEM Forms wordt opgesteld. Nadat het WAR-bestand is geïmplementeerd, kunt u de HTML-webpagina openen met een webbrowser.

**Het WAR-bestand implementeren op de J2EE-toepassingsserver:**

* Kopieer het WAR-bestand van het exportpad naar `[Forms Install]\Adobe\Adobe Experience Manager Forms\jboss\server\all\deploy`.

### Uw webtoepassing testen {#testing-your-web-application}

Nadat u de webtoepassing hebt geïmplementeerd, kunt u deze testen met een webbrowser. Ervan uitgaande dat u dezelfde computer gebruikt als die waarop AEM Forms worden gehost, kunt u de volgende URL opgeven:

* http://localhost:8080/FragmentsWebApplication/index.html

   Selecteer een keuzerondje en klik op Verzenden. Een formulier dat is gebaseerd op fragmenten, wordt weergegeven in de webbrowser. Als er problemen optreden, raadpleegt u het logbestand van de J2EE-toepassingsserver.

