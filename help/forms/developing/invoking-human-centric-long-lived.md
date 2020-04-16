---
title: Het aanhalen van mens-Centric langlevende Processen
seo-title: Het aanhalen van mens-Centric langlevende Processen
description: 'null'
seo-description: 'null'
uuid: 42269d41-a90f-4ea1-aeb9-d61337bcfa54
contentOwner: admin
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: coding
discoiquuid: 18a320b4-dce6-4c50-8864-644b0b2d6644
translation-type: tm+mt
source-git-commit: f9389a06f9c2cd720919486765cee76257f272c3

---


# Het aanhalen van mens-Centric langlevende Processen {#invoking-human-centric-long-lived-processes}

U kunt mens-centric langlevende processen programmatically aanhalen die in Workbench gebruikend deze cliënttoepassingen werden gecreeerd:

* Een Java-clienttoepassing op het web die de Invocation-API gebruikt. (Zie [AEM-formulieren aanroepen met de Java API](/help/forms/developing/invoking-aem-forms-using-java.md)(/help/forms/developing/invoking-aem-forms-using-java.md#invoking-aem-forms-using-the-java-api).)
* Een toepassing ASP.NET die de Webdiensten gebruikt. (Zie [AEM-formulieren aanroepen met behulp van webservices](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-web-services).)
* Een clienttoepassing die is gebouwd met Flex en Verwijderen gebruikt. (Zie AEM-formulieren [aanroepen met (Verouderd voor AEM-formulieren) AEM-formulieren verwijderen](/help/forms/developing/invoking-aem-forms-using-remoting.md#invoking-aem-forms-using-remoting).)

Het langlevende proces dat wordt aangehaald wordt genoemd *FirstAppSolution/PreLoanProcess*. U kunt dit proces maken door de zelfstudie te volgen die is opgegeven in [Uw eerste AEM-formuliertoepassing](https://www.adobe.com/go/learn_aemforms_firstapp_ds_63)maken.

Een mens-centrisch proces impliceert een taak die een gebruiker kan antwoorden aan door Werkruimte te gebruiken. Met Workbench kunt u bijvoorbeeld een proces maken waarmee een bankmanager een leningtoepassing kan goedkeuren of weigeren. In de volgende afbeelding ziet u het proces *FirstAppSolution/PreLoanProcess*.

Het *proces FirstAppSolution/PreLoanProcess* accepteert een invoerparameter met de naam *formData* waarvan het gegevenstype XML is. De XML-gegevens worden samengevoegd met een formulierontwerp met de naam *PreLoanForm.xdp*. In de volgende afbeelding ziet u een formulier dat een taak vertegenwoordigt die aan een gebruiker is toegewezen om een leningtoepassing goed te keuren of te weigeren. De gebruiker keurt of ontkent de toepassing door Workspace te gebruiken. De gebruiker van de Werkruimte kan het leningsverzoek goedkeuren door de knoop van Goedkeuren te klikken die in de volgende illustratie wordt getoond. Op dezelfde manier kan de gebruiker het verzoek om een lening weigeren door op de knop Weigeren te klikken.

Een proces van lange duur wordt asynchroon aangehaald en kan niet synchroon wegens de volgende factoren worden aangehaald:

* Een proces kan veel tijd in beslag nemen.
* Een proces kan organisatorische grenzen overspannen.
* Een proces heeft externe input nodig om het te voltooien. Neem bijvoorbeeld een situatie waarin een formulier wordt verzonden naar een manager die zich buiten het kantoor bevindt. In dit geval is het proces niet volledig totdat de manager het formulier retourneert en invult.

Wanneer een langdurig proces wordt aangeroepen, maakt AEM Forms een waarde voor de aanroepings-id als onderdeel van het maken van een record. De record houdt de status van het langlevende proces bij en wordt opgeslagen in de AEM Forms-database. Met de waarde voor de oproepings-id kunt u de status van het langlevende proces volgen. Bovendien kunt u de waarde van de proces aanroepings herkenningsteken gebruiken om verrichtingen van de Manager van het Proces uit te voeren zoals het beëindigen van een lopende procesinstantie.

>[!NOTE]
>
>In AEM Forms wordt geen waarde voor de oproepings-id of een record gemaakt wanneer een kortstondig proces wordt aangeroepen.

Het `FirstAppSolution/PreLoanProcess` proces wordt opgeroepen wanneer een aanvrager een aanvraag indient, die wordt weergegeven als XML-gegevens. De naam van de invoerprocesvariabele is `formData` en het gegevenstype is XML. In deze beschrijving wordt ervan uitgegaan dat de volgende XML-gegevens worden gebruikt als invoer voor het `FirstAppSolution/PreLoanProcess` proces.

```as3
 <?xml version="1.0" encoding="UTF-8"?>
 <LoanApp>
 <Name>Sam White</Name>
 <LoanAmount>250000</LoanAmount>
 <PhoneOrEmail>(555)555-5555</PhoneOrEmail>
 <ApprovalStatus>PENDING APPROVAL</ApprovalStatus>
 </LoanApp>
```

XML-gegevens die aan een proces worden doorgegeven, moeten overeenkomen met de velden in het formulier dat in het proces wordt gebruikt. Anders worden de gegevens niet weergegeven in het formulier. Alle toepassingen die het `FirstAppSolution/PreLoanProcess` proces aanroepen, moeten deze XML-gegevensbron doorgeven. De toepassingen die in het *Aanhalen van mens-Centric Lange-Levende Processen* worden gecreeerd creëren dynamisch de gegevensbron van XML van waarden die een gebruiker in een Webcliënt inging.

Met behulp van een clienttoepassing kunt u de *FirstAppSolution/PreLoanProcess* verzenden om de vereiste XML-gegevens te verwerken. Een langlevend proces retourneert een waarde voor de oproepings-id als geretourneerde waarde. De volgende illustratie toont cliënttoepassingen die het*FirstAppSolution/PreLoanProcess langdurig proces aanhalen. De clienttoepassingen verzenden XML-gegevens en krijgen een tekenreekswaarde die de waarde van de aanroepings-id vertegenwoordigt.

**Zie ook**

[Een Java-webtoepassing maken die een menselijk-centrisch proces van lange duur oproept](invoking-human-centric-long-lived.md#creating-a-java-web-application-that-invokes-a-human-centric-long-lived-process)

[Creërend een Asp.net- Webtoepassing die een mens-centric langlevend proces aanhaalt](invoking-human-centric-long-lived.md#creating-an-asp-net-web-application-that-invokes-a-human-centric-long-lived-process)

[Een clienttoepassing maken die is gebouwd met Flex en die een menselijk-centrisch proces van lange duur aanroept](invoking-human-centric-long-lived.md#creating-a-client-application-built-with-flex-that-invokes-a-human-centric-long-lived-process)

## Een Java-webtoepassing maken die een menselijk-centrisch proces van lange duur oproept {#creating-a-java-web-application-that-invokes-a-human-centric-long-lived-process}

U kunt een webtoepassing maken die een Java-servlet gebruikt om het `FirstAppSolution/PreLoanProcess` proces aan te roepen. Als u dit proces vanuit een Java-servlet wilt aanroepen, gebruikt u de API voor aanroepen in de Java-servlet. (Zie [AEM-formulieren aanroepen met de Java API](/help/forms/developing/invoking-aem-forms-using-java.md#invoking-aem-forms-using-the-java-api).)

In de volgende afbeelding ziet u een clienttoepassing op het web waarmee de naam, telefoon (of e-mail) en waarden worden gepost. Deze waarden worden naar de Java-server verzonden wanneer de gebruiker op de knop Toepassing verzenden klikt.

Java servlet voert de volgende taken uit:

* Haalt de waarden op die vanuit de HTML-pagina naar het Java-servlet zijn gepost.
* Hiermee wordt dynamisch een XML-gegevensbron gemaakt die wordt doorgegeven aan het *proces FirstAppSolution/PreLoanProcess* . De naam, telefoon (of e-mail) en de waarden voor de hoeveelheid worden opgegeven in de XML-gegevensbron.
* Roept het *proces FirstAppSolution/PreLoanProcess* aan met de API voor het oproepen van AEM-formulieren.
* Hiermee wordt de waarde van de oproepings-id geretourneerd aan de webbrowser van de client.

### Overzicht van de stappen {#summary-of-steps}

Voer de volgende stappen uit om een Java-webtoepassing te maken die het `FirstAppSolution/PreLoanProcess` proces oproept:

1. [Maak een webproject](invoking-human-centric-long-lived.md#create-a-web-project).
1. [Maak Java-toepassingslogica voor de servlet](invoking-human-centric-long-lived.md#create-java-application-logic-for-the-servlet).
1. [De webpagina voor de webtoepassing maken](invoking-human-centric-long-lived.md#create-the-web-page-for-the-web-application)
1. [Verpak de webtoepassing naar een WAR-bestand](invoking-human-centric-long-lived.md#package-the-web-application-to-a-war-file).
1. [Implementeer het WAR-bestand op de J2EE-toepassingsserver die als host fungeert voor AEM-formulieren](invoking-human-centric-long-lived.md#deploy-the-war-file-to-the-j2ee-application-server-hosting-aem-forms).
1. [Test uw webtoepassing](invoking-human-centric-long-lived.md#test-your-web-application).

>[!NOTE]
>
>Sommige van deze stappen zijn afhankelijk van de J2EE-toepassing waarop AEM Forms is geïmplementeerd. De methode die u bijvoorbeeld gebruikt om een WAR-bestand te implementeren, is afhankelijk van de J2EE-toepassingsserver die u gebruikt. Aangenomen wordt dat AEM Forms wordt geïmplementeerd op JBoss®.

### Een webproject maken {#create-a-web-project}

De eerste stap voor het maken van een webtoepassing is het maken van een webproject. De Java-IDE waarop dit document is gebaseerd, is Eclipse 3.3. Gebruikend IDE van de Verduistering, creeer een Webproject en voeg de vereiste JAR dossiers aan uw project toe. Voeg een HTML-pagina met de naam *index.html* en een Java-servlet toe aan uw project.

In de volgende lijst worden de JAR-bestanden weergegeven die in uw webproject moeten worden opgenomen:

* adobe-livecycle-client.jar
* adobe-usermanager-client.jar
* J2EE.jar

Zie [Including AEM Forms Java library files](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)voor de locatie van deze JAR-bestanden.

>[!NOTE]
>
>Het bestand J2EE.jar definieert gegevenstypen die door een Java-servlet worden gebruikt. U kunt dit JAR-bestand verkrijgen van de J2EE-toepassingsserver waarop AEM Forms is geïmplementeerd.

**Een webproject maken**

1. Start Eclipse en klik op **Bestand** > **Nieuw project**.
1. Selecteer in het dialoogvenster **Nieuw project** de optie **Web** > **Dynamisch webproject**.
1. Typ `InvokePreLoanProcess` de naam van het project en klik op **Voltooien**.

**Vereiste JAR-bestanden toevoegen aan uw project**

1. Van het venster van de Ontdekkingsreiziger van het Project, klik het `InvokePreLoanProcess` project met de rechtermuisknop aan en selecteer **Eigenschappen**.
1. Klik op **Java-bouwpad** en klik vervolgens op het tabblad **Bibliotheken** .
1. Klik op de knop Externe JAR&#39;s **toevoegen** en blader naar de JAR-bestanden die u wilt opnemen.

**Een Java-servlet toevoegen aan uw project**

1. Van het venster van de Ontdekkingsreiziger van het Project, klik het `InvokePreLoanProcess` project met de rechtermuisknop aan en selecteer **Nieuw** > **Andere**.
1. Vouw de **webmap** uit, selecteer **Servlet** en klik op **Volgende**.
1. Typ in het dialoogvenster Servlet maken `SubmitXML` de naam van de servlet en klik op **Voltooien**.

**Een HTML-pagina toevoegen aan uw project**

1. Van het venster van de Ontdekkingsreiziger van het Project, klik het `InvokePreLoanProcess` project met de rechtermuisknop aan en selecteer **Nieuw** > **Andere**.
1. Vouw de map **Web** uit, selecteer **HTML** en klik op **Volgende**.
1. Typ in het dialoogvenster Nieuwe HTML `index.html` de bestandsnaam en klik op **Voltooien**.

>[!NOTE]
>
>Zie De webpagina [maken voor de webtoepassing](invoking-human-centric-long-lived.md#create-the-web-page-for-the-web-application)voor informatie over het maken van HTML-inhoud die de SubmitXML Java-servlet activeert.

### Java-toepassingslogica voor de servlet maken {#create-java-application-logic-for-the-servlet}

Maak Java-toepassingslogica die het `FirstAppSolution/PreLoanProcess` proces aanroept vanuit de Java-servlet. De volgende code toont de syntaxis van `SubmitXML` Java Servlet:

```as3
     public class SubmitXML extends HttpServlet implements Servlet {
         public void doGet(HttpServletRequest req, HttpServletResponse resp
         throws ServletException, IOException {
         doPost(req,resp);
 
         }
         public void doPost(HttpServletRequest req, HttpServletResponse resp
         throws ServletException, IOException {
             //Add code here to invoke the FirstAppSolution/PreLoanProcess process
             }
```

Normaal gesproken plaatst u geen clientcode in een Java-servlet `doGet` of - `doPost` methode. Een betere programmeerpraktijk is deze code binnen een afzonderlijke klasse te plaatsen. Instantieer vervolgens de klasse vanuit de `doPost` methode (of `doGet` methode) en roep de juiste methoden aan. Voor codebeknoptheid worden codevoorbeelden echter tot een minimum beperkt en in de `doPost` methode geplaatst.

Voer de volgende taken uit om het `FirstAppSolution/PreLoanProcess` proces aan te roepen met de API voor aanroepen:

1. Neem client-JAR-bestanden, zoals adobe-livecycle-client.jar, op in het klassenpad van uw Java-project. Zie [Including AEM Forms Java library files](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)voor informatie over de locatie van deze bestanden.
1. Haal de naam, de telefoon, en de bedragen op die van de HTML- pagina worden voorgelegd. Gebruik deze waarden om dynamisch een XML-gegevensbron te maken die naar het `FirstAppSolution/PreLoanProcess` proces wordt verzonden. U kunt `org.w3c.dom` klassen gebruiken om de gegevensbron van XML tot stand te brengen (deze toepassingslogica wordt getoond in het volgende codevoorbeeld).
1. Maak een `ServiceClientFactory` object dat verbindingseigenschappen bevat. (Zie Verbindingseigenschappen [instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties).)
1. Maak een `ServiceClient` object door de constructor ervan te gebruiken en het `ServiceClientFactory` object door te geven. Met een `ServiceClient` object kunt u een servicebewerking aanroepen. Het behandelt taken zoals het lokaliseren van, het verzenden van, en het verpletteren van oproepingsverzoeken.
1. Maak een `java.util.HashMap` object met de constructor ervan.
1. Roep de `java.util.HashMap` methode van het `put` object aan voor elke invoerparameter die aan het langlevende proces wordt doorgegeven. Zorg ervoor dat u de naam van de invoerparameters van het proces opgeeft. Omdat voor het `FirstAppSolution/PreLoanProcess` proces één invoerparameter van het type `XML` (genaamd `formData`) vereist is, hoeft u de `put` methode slechts eenmaal aan te roepen.

   ```as3
    //Get the XML to pass to the FirstAppSolution/PreLoanProcess process
    org.w3c.dom.Document inXML = GetDataSource(name,phone,amount);
    
    //Create a Map object to store the parameter value
    Map params = new HashMap();
    params.put("formData", inXML);
   ```

1. Maak een `InvocationRequest` object door de methode van het `ServiceClientFactory` `createInvocationRequest` object aan te roepen en de volgende waarden door te geven:

   * Een tekenreekswaarde die de naam aangeeft van het proces met een lange levensduur dat moet worden aangeroepen. Om het `FirstAppSolution/PreLoanProcess` proces aan te halen, specificeer `FirstAppSolution/PreLoanProcess`.
   * Een tekenreekswaarde die staat voor de naam van de procesbewerking. De naam van de langdurige procesbewerking is `invoke`.
   * Het `java.util.HashMap` object dat de parameterwaarden bevat die de servicebewerking vereist.
   * Een Booleaanse waarde die opgeeft `false`, die een asynchrone aanvraag maakt (deze waarde is van toepassing om een langlevend proces aan te roepen).
   >[!NOTE]
   >
   >*Een proces van korte duur kan worden aangeroepen door de waarde true door te geven als de vierde parameter van de methode createInvocationRequest. Als u de waarde waar doorgeeft, wordt een synchrone aanvraag gemaakt.*

1. Verzend de aanroepingsaanvraag naar AEM Forms door de methode van het `ServiceClient` object aan te roepen en het `invoke` `InvocationRequest` object door te geven. De `invoke` methode retourneert een `InvocationReponse` object.
1. Een langlevend proces retourneert een tekenreekswaarde die een aanroepende-identificatiewaarde vertegenwoordigt. Haal deze waarde op door de `InvocationReponse` methode van het `getInvocationId` object aan te roepen.

   ```as3
    //Send the invocation request to the long-lived process and
    //get back an invocation response object
    InvocationResponse lcResponse = myServiceClient.invoke(lcRequest);
    String invocationId = lcResponse.getInvocationId();
   ```

1. Schrijf de waarde voor de oproepidentificatie naar de webbrowser van de client. U kunt een `java.io.PrintWriter` instantie gebruiken om deze waarde naar de browser van het cliëntWeb te schrijven.

### Snel starten: Een langdurig proces aanroepen met de API voor aanroepen {#quick-start-invoking-a-long-lived-process-using-the-invocation-api}

In het volgende Java-codevoorbeeld wordt de Java-servlet weergegeven die het `FirstAppSolution/PreLoanProcess` proces oproept.

```as3
 /*
     * This Java Quick Start uses the following JAR files
     * 1. adobe-livecycle-client.jar
     * 2. adobe-usermanager-client.jar
     *
     * (Because this  quick start is implemented as a Java servlet, it is
     * not necessary to include J2EE specific JAR files - the Java project
     * that contains this quick start is exported as a WAR file which
     * is deployed to the J2EE application server)
     *
     * These JAR files are located in the following path:
     * <install directory>/sdk/client-libs/common
     *
     * For complete details about the location of these JAR files,
     * see "Including AEM Forms library files" in Programming with AEM forms
     * */
 import java.io.ByteArrayOutputStream;
 import java.io.File;
 import java.io.IOException;
 import java.io.PrintWriter;
 
 import javax.servlet.ServletException;
 import javax.servlet.http.HttpServletRequest;
 import javax.servlet.http.HttpServletResponse;
 import java.util.*;
 import com.adobe.idp.dsc.clientsdk.ServiceClientFactory;
 import com.adobe.idp.dsc.clientsdk.ServiceClientFactoryProperties;
 import javax.xml.parsers.DocumentBuilder;
 import javax.xml.parsers.DocumentBuilderFactory;
 import javax.xml.transform.Transformer;
 import javax.xml.transform.TransformerFactory;
 import javax.xml.transform.dom.DOMSource;
 import javax.xml.transform.stream.StreamResult;
 
 import com.adobe.idp.dsc.InvocationRequest;
 import com.adobe.idp.dsc.InvocationResponse;
 import com.adobe.idp.dsc.clientsdk.ServiceClient;
 import org.w3c.dom.Element;
 
     public class SubmitXML extends javax.servlet.http.HttpServlet implements javax.servlet.Servlet {
       static final long serialVersionUID = 1L;
 
        public SubmitXML() {
         super();
     }
 
 
     protected void doGet(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
         // TODO Auto-generated method stub
         doPost(request,response);
     }
 
     protected void doPost(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
 
         try{
             //Set connection properties required to invoke AEM Forms
             Properties connectionProps = new Properties();
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_DEFAULT_EJB_ENDPOINT, "jnp://localhost:1099");
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_TRANSPORT_PROTOCOL,ServiceClientFactoryProperties.DSC_EJB_PROTOCOL);
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_SERVER_TYPE, "JBoss");
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_CREDENTIAL_USERNAME, "administrator");
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_CREDENTIAL_PASSWORD, "password");
 
             //Create a ServiceClientFactory object
             ServiceClientFactory myFactory = ServiceClientFactory.createInstance(connectionProps);
 
             //Create a ServiceClient object
             ServiceClient myServiceClient = myFactory.getServiceClient();
 
             //Get the values that are passed from the Loan HTML page
             String name = (String)request.getParameter("name");
             String phone = (String)request.getParameter("phone");
             String amount = (String)request.getParameter("amount");
 
             //Create XML to pass to the FirstAppSolution/PreLoanProcess process
             org.w3c.dom.Document inXML = GetDataSource(name,phone,amount);
 
             //Create a Map object to store the XML input parameter value
             Map params = new HashMap();
             params.put("formData", inXML);
 
             //Create an InvocationRequest object
             InvocationRequest lcRequest =  myFactory.createInvocationRequest(
                 "FirstAppSolution/PreLoanProcess", //Specify the long-lived process name
                     "invoke",           //Specify the operation name
                     params,               //Specify input values
                     false);               //Create an asynchronous request
 
             //Send the invocation request to the long-lived process and
             //get back an invocation response object
             InvocationResponse lcResponse = myServiceClient.invoke(lcRequest);
             String invocationId = lcResponse.getInvocationId();
 
             //Create a PrintWriter instance
             PrintWriter pp = response.getWriter();
 
             //Write the invocation identifier value back to the client web browser
             pp.println("The job status identifier value is: " +invocationId);
 
         }catch (Exception e) {
              System.out.println("The following exception occurred: "+e.getMessage());
       }
     }
 
 
      //Create XML data to pass to the long-lived process
      private static org.w3c.dom.Document GetDataSource(String name, String phone, String amount)
      {
             org.w3c.dom.Document document = null;
 
             try
             {
                 //Create DocumentBuilderFactory and DocumentBuilder objects
                 DocumentBuilderFactory factory = DocumentBuilderFactory.newInstance();
                 DocumentBuilder builder = factory.newDocumentBuilder();
 
                 //Create a new Document object
                 document = builder.newDocument();
 
                 //Create MortgageApp - the root element in the XML
                 Element root = (Element)document.createElement("LoanApp");
                 document.appendChild(root);
 
                 //Create an XML element for Name
                 Element nameElement = (Element)document.createElement("Name");
                 nameElement.appendChild(document.createTextNode(name));
                 root.appendChild(nameElement);
 
                 //Create an XML element for Phone
                 Element phoneElement = (Element)document.createElement("PhoneOrEmail");
                 phoneElement.appendChild(document.createTextNode(phone));
                 root.appendChild(phoneElement);
 
                 //Create an XML element for amount
                 Element loanElement = (Element)document.createElement("LoanAmount");
                 loanElement.appendChild(document.createTextNode(amount));
                 root.appendChild(loanElement);
 
                 //Create an XML element for ApprovalStatus
                 Element approveElement = (Element)document.createElement("ApprovalStatus");
                 approveElement.appendChild(document.createTextNode("PENDING APPROVAL"));
                 root.appendChild(approveElement);
 
               }
          catch (Exception e) {
                   System.out.println("The following exception occurred: "+e.getMessage());
                }
         return document;
          }
         }
```

### De webpagina voor de webtoepassing maken {#create-the-web-page-for-the-web-application}

De *index.html* -webpagina biedt een ingangspunt voor de Java-servlet die het `FirstAppSolution/PreLoanProcess` proces aanroept. Deze webpagina is een basis-HTML-formulier dat een HTML-formulier en een verzendknop bevat. Wanneer de gebruiker op de verzendknop klikt, worden de formuliergegevens naar de `SubmitXML` Java-server verzonden.

De Java-servlet legt de gegevens vast die vanuit de HTML-pagina zijn gepost met de volgende Java-code:

```as3
 //Get the values that are passed from the Loan HTML page
 String name = request.getParameter("name");
 String phone = request.getParameter("phone");
 String amount = request.getParameter("amount");
```

De volgende HTML-code vertegenwoordigt het bestand index.html dat tijdens de installatie van de ontwikkelomgeving is gemaakt. (Zie [Een webproject](invoking-human-centric-long-lived.md#create-a-web-project)maken.)

```as3
 <!DOCTYPE html PUBLIC "-//W3C//DTD HTML 4.01 Transitional//EN" "https://www.w3.org/TR/html4/loose.dtd">
 <html>
 <head>
 <meta http-equiv="Content-Type" content="text/html; charset=ISO-8859-1">
 <title>Insert title here</title>
 </head>
 <body>
 <table>
     <TBODY>
         <TR>
             <td><img src="financeCorpLogo.jpg" width="172" height="62"></TD>
             <td><FONT size="+2"><strong>Java Loan Application Page</strong></FONT></TD>
             <td> </TD>
             <td> </TD>
         </TR>
 
     </TBODY>
 </TABLE>
     <FORM action="https://hiro-xp:8080/PreLoanProcess/SubmitXML" method="post">
        <table>
          <TBODY>
                <TR>
                      <td><LABEL for="name">Name: </LABEL></TD>
                  <td><INPUT type="text" name="name"></TD>
                  <td><input type="submit" value="Submit Application"></TD>
                  </TR>
            <TR>
                  <td> <LABEL for="phone">Phone/Email: </LABEL></TD>
              <td><INPUT type="text" name="phone"></TD>
                  <td></TD>
              </TR>
 
            <TR>
                  <td><LABEL for="amount">Amount: </LABEL></TD>
              <td><INPUT type="text" name="amount"></TD>
                 <td></TD>
             </TR>
          </TBODY>
 </TABLE>
       </FORM>
 </body>
 </html>
```

### De webtoepassing verpakken naar een WAR-bestand {#package-the-web-application-to-a-war-file}

Als u het Java-servlet wilt implementeren dat het `FirstAppSolution/PreLoanProcess` proces oproept, moet u uw webtoepassing verpakken naar een WAR-bestand. Zorg ervoor dat externe JAR-bestanden waarvan de bedrijfslogica van de component afhankelijk is, zoals adobe-livecycle-client.jar en adobe-usermanager-client.jar, ook in het WAR-bestand worden opgenomen.

De volgende illustratie toont de inhoud van het project Eclipse, die aan een dossier van WAR wordt verpakt.

>[!NOTE]
>
>In de vorige afbeelding kan het JPG-bestand worden vervangen door elk JPG-afbeeldingsbestand.

**Een webtoepassing verpakken naar een WAR-bestand:**

1. Klik in het venster **Projectverkenner** met de rechtermuisknop op het `InvokePreLoanProcess` project en selecteer **Exporteren** > **WAR-bestand**.
1. Typ in het tekstvak van de module **** Web de naam `InvokePreLoanProcess` van het Java-project.
1. Typ in het tekstvak **Doel** de bestandsnaam `PreLoanProcess.war`**voor **de bestandsnaam, geef de locatie voor het WAR-bestand op en klik op Voltooien.

### WAR-bestand implementeren op de J2EE-toepassingsserver die als host fungeert voor AEM-formulieren {#deploy-the-war-file-to-the-j2ee-application-server-hosting-aem-forms}

Implementeer het WAR-bestand op de J2EE-toepassingsserver waarop AEM Forms is geïmplementeerd. Als u het WAR-bestand wilt implementeren op de J2EE-toepassingsserver, kopieert u het WAR-bestand van het exportpad naar `[AEM Forms Install]\Adobe\Adobe Experience Manager Forms\jboss\server\lc_turnkey\deploy`.

>[!NOTE]
>
>als AEM Forms niet op JBoss wordt opgesteld, dan moet u het dossier van WAR in overeenstemming met de J2EE toepassingsserver opstellen die AEM Vormen ontvangt.

### Uw webtoepassing testen {#test-your-web-application}

Nadat u de webtoepassing hebt geïmplementeerd, kunt u deze testen met een webbrowser. Ervan uitgaande dat u dezelfde computer gebruikt als die waarop AEM Forms wordt gehost, kunt u de volgende URL opgeven:

* http://localhost:8080/PreLoanProcess/index.html

   Voer waarden in de HTML-formuliervelden in en klik op de knop Toepassing verzenden. Als er problemen optreden, raadpleegt u het logbestand van de J2EE-toepassingsserver.

>[!NOTE]
>
>Als u wilt bevestigen dat de Java-toepassing het proces heeft aangeroepen, start u Workspace en accepteert u de lening.

## Creërend een Asp.net- Webtoepassing die een mens-centric langlevend proces aanhaalt {#creating-an-asp-net-web-application-that-invokes-a-human-centric-long-lived-process}

U kunt een toepassing tot stand brengen ASP.NET die het `FirstAppSolution/PreLoanProcess` proces aanhaalt. Om dit proces van een toepassing aan te halen ASP.NET, gebruik de Webdiensten. (Zie [AEM-formulieren aanroepen met behulp van webservices](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-web-services).)

De volgende illustratie toont een ASP.NET cliënttoepassing die gegevens van een eind verkrijgen - gebruiker. De gegevens worden in een XML-gegevensbron geplaatst en naar het `FirstAppSolution/PreLoanProcess` proces verzonden wanneer de gebruiker op de knop Toepassing verzenden klikt.

Nadat het proces is aangeroepen, wordt een waarde voor de aanroepings-id weergegeven. Een waarde voor de oproepings-id wordt gemaakt als onderdeel van een record die de status van het proces met een lange levensduur bijhoudt.

De toepassing ASP.NET voert de volgende taken uit:

* Haalt de waarden op die de gebruiker op de webpagina heeft ingevoerd.
* Creeert dynamisch een gegevensbron van XML die tot* FirstAppSolution/PreLoanProcess *process wordt overgegaan. De drie waarden worden opgegeven in de XML-gegevensbron.
* Roept het* FirstAppSolution/PreLoanProcess *process aan door de Webdiensten te gebruiken.
* Retourneert de aanroepings-id-waarde en de status van de langdurige bewerking naar de webbrowser van de client.

### Overzicht van de stappen {#summary_of_steps-1}

Om een toepassing tot stand te brengen ASP.NET die het proces kan aanhalen FirstAppSolution/PreLoanProcess, voer de volgende stappen uit:

1. [Maak een ASP.NET-webtoepassing](invoking-human-centric-long-lived.md#create-an-asp-net-web-application).
1. [Maak een ASP-pagina die FirstAppSolution/PreLoanProcess](invoking-human-centric-long-lived.md#create-an-asp-page-that-invokes-firstappsolution-preloanprocess)aanroept.
1. [Voer de toepassing](invoking-human-centric-long-lived.md#run-the-asp-net-application)ASP.NET uit.

### Een ASP.NET-webtoepassing maken {#create-an-asp-net-web-application}

Creeer een toepassing van het Web van Microsoft .NET C# ASP.NET. De volgende illustratie toont de inhoud van het project ASP.NET genoemd *InvokePreLoanProcess*.

Bericht onder de Verwijzingen van de Dienst, zijn er twee punten. Het eerste item heeft de naam* JobManager*. Deze verwijzing laat de toepassing ASP.NET toe om de dienst van de Manager van de Baan aan te halen. Deze dienst keert informatie over het statuut van een lang-levend proces terug. Als het proces bijvoorbeeld op dat moment wordt uitgevoerd, retourneert deze service een numerieke waarde die aangeeft dat het proces momenteel wordt uitgevoerd. De tweede verwijzing heeft de *naam PreLoanProcess*. Deze serviceverwijzing vertegenwoordigt de verwijzing naar het *process* FirstAppSolution/PreLoanProcess. Nadat u een Verwijzing van de Dienst creeert, zijn de gegevenstypes verbonden aan de dienst van Vormen AEM beschikbaar voor gebruik binnen uw .NET project.

**Maak een ASP.NET-project:**

1. Start Microsoft Visual Studio 2008.
1. Selecteer **Nieuw** , **website** in het menu **Bestand**.
1. In de lijst van **Malplaatjes** , uitgezochte **Asp.net- Website**.
1. Selecteer een locatie voor uw project in het vak **Locatie** . Geef uw project een naam *InvokePreLoanProcess*.
1. In het vakje van de **Taal** , uitgezochte Visuele C#
1. Klik op OK.

**Serviceverwijzingen toevoegen:**

1. Selecteer Serviceverwijzing **** toevoegen in het menu Project.
1. Geef in het dialoogvenster **Adres** de WSDL op voor de service Taakbeheer.

   ```as3
    https://hiro-xp:8080/soap/services/JobManager?WSDL&lc_version=9.0.1
   ```

1. Typ in het veld Namespace `JobManager`.
1. Click **Go** and then click **OK**.
1. Selecteer in het menu **Project** de optie **Serviceverwijzing** toevoegen.
1. Geef in het dialoogvenster **Adres** de WSDL op voor het proces FirstAppSolution/PreLoanProcess.

   ```as3
    https://hiro-xp:8080/soap/services/FirstAppSolution/PreLoanProcess?WSDL&lc_version=9.0.1
   ```

1. Typ in het veld Namespace `PreLoanProcess`.
1. Click **Go** and then click **OK**.

>[!NOTE]
>
>Vervangen `hiro-xp` door het IP-adres van de J2EE-toepassingsserver die als host fungeert voor AEM Forms. De `lc_version` optie zorgt ervoor dat de functionaliteit van Vormen AEM, zoals MTOM, beschikbaar is. U kunt AEM-formulieren niet aanroepen met MTOM zonder de `lc_version`optie op te geven. (Zie AEM-formulieren [aanroepen met MTOM](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom).)

### Maak een ASP-pagina die FirstAppSolution/PreLoanProcess aanroept {#create-an-asp-page-that-invokes-firstappsolution-preloanprocess}

Voeg binnen het ASP.NET-project een webformulier (een ASPX-bestand) toe dat verantwoordelijk is voor de weergave van een HTML-pagina in de aanvrager van de lening. Het webformulier is gebaseerd op een klasse die is afgeleid van `System.Web.UI.Page`. De C# toepassingslogica die aanhaalt `FirstAppSolution/PreLoanProcess` wordt gevestigd in de `Button1_Click` methode (deze knoop vertegenwoordigt de Submit knoop van de Toepassing).

De volgende illustratie toont de toepassing ASP.NET

De volgende lijst maakt een lijst van de controles die deel van deze toepassing ASP.NET uitmaken.

<table>
 <thead>
  <tr>
   <th><p>Naam besturingselement</p></th>
   <th><p>Beschrijving</p></th>
  </tr>
 </thead>
 <tbody>
  <tr>
   <td><p>TextBoxName</p></td>
   <td><p>Geeft de voor- en achternaam van de klant op. </p></td>
  </tr>
  <tr>
   <td><p>TextBoxPhone</p></td>
   <td><p>Specificeert de telefoon of e-mailadres van de klant. </p></td>
  </tr>
  <tr>
   <td><p>TextBoxAmount</p></td>
   <td><p>Geeft het bedrag van de lening aan.</p></td>
  </tr>
  <tr>
   <td><p>Button1</p></td>
   <td><p>Vertegenwoordigt de Submit knoop van de Toepassing.</p></td>
  </tr>
  <tr>
   <td><p>LabelJobID</p></td>
   <td><p>Een besturingselement Label dat de waarde van de waarde van de aanroepings-id opgeeft.</p></td>
  </tr>
  <tr>
   <td><p>LabelStatus</p></td>
   <td><p>Een besturingselement Label dat de waarde van de taakstatus opgeeft. Deze waarde wordt opgehaald door de service Taakbeheer aan te roepen. </p></td>
  </tr>
 </tbody>
</table>

De toepassingslogica die deel van de toepassing ASP.NET uitmaakt moet dynamisch tot een gegevensbron van XML leiden om tot het `FirstAppSolution/PreLoanProcess` proces over te gaan. De waarden die de aanvrager op de HTML-pagina heeft ingevoerd, moeten in de XML-gegevensbron worden opgegeven. Deze gegevenswaarden worden in het formulier samengevoegd wanneer het formulier wordt weergegeven in Workspace. De klassen in de `System.Xml` naamruimte worden gebruikt om de XML-gegevensbron te maken.

Wanneer het aanhalen van een proces dat de gegevens van XML van een toepassing ASP.NET vereist, is een gegevenstype van XML beschikbaar voor u aan gebruik. U kunt dus geen `System.Xml.XmlDocument` instantie aan het proces doorgeven. De volledig gekwalificeerde naam van deze XML-instantie die aan het proces moet worden doorgegeven, is `InvokePreLoanProcess.PreLoanProcess.XML`. Zet de `System.Xml.XmlDocument` instantie om in `InvokePreLoanProcess.PreLoanProcess.XML`. U kunt deze taak uitvoeren door de volgende code te gebruiken.

```as3
 //Create the XML to pass to the FirstAppSolution/PreLoanProcess process
 XmlDocument myXML = CreateXML(userName, phone, amount);
 
 //Convert the XML to a InvokePreLoanProcess.PreLoanProcess.XML instance
 StringWriter sw = new StringWriter();
 XmlTextWriter xw = new XmlTextWriter(sw);
 myXML.WriteTo(xw);
 
 InvokePreLoanProcess.PreLoanProcess.XML inXML = new XML();
 inXML.document = sw.ToString();
```

Als u een ASP-pagina wilt maken die het `FirstAppSolution/PreLoanProcess` proces oproept, voert u de volgende taken uit in de `Button1_Click` methode:

1. Maak een `FirstAppSolution_PreLoanProcessClient` object met de standaardconstructor.
1. Maak een `FirstAppSolution_PreLoanProcessClient.Endpoint.Address` object met de `System.ServiceModel.EndpointAddress` constructor. Geef een tekenreekswaarde door die de WSDL opgeeft voor de service AEM Forms en het coderingstype:

   ```as3
    https://hiro-xp:8080/soap/services/FirstAppSolution/PreLoanProcess?blob=mtom
   ```

   U hoeft het `lc_version` kenmerk niet te gebruiken. Dit kenmerk wordt gebruikt wanneer u een serviceverwijzing maakt. Zorg er echter voor dat u opgeeft `?blob=mtom`.

   >[!NOTE]
   >
   >Vervang `hiro-xp`* door het IP-adres van de J2EE-toepassingsserver die als host fungeert voor AEM Forms. *

1. Maak een `System.ServiceModel.BasicHttpBinding` object door de waarde van het `FirstAppSolution_PreLoanProcessClient.Endpoint.Binding` gegevenslid op te halen. Kiezen naar de geretourneerde waarde `BasicHttpBinding`.
1. Stel het `System.ServiceModel.BasicHttpBinding` gegevenslid van het object in op `MessageEncoding` `WSMessageEncoding.Mtom`. Deze waarde zorgt ervoor dat MTOM wordt gebruikt.
1. Laat basisauthentificatie van HTTP door de volgende taken uit te voeren toe:

   * Wijs de gebruikersnaam voor AEM-formulieren toe aan het gegevenslid `FirstAppSolution_PreLoanProcessClient.ClientCredentials.UserName.UserName`.
   * Wijs de overeenkomstige wachtwoordwaarde aan het gegevenslid toe `FirstAppSolution_PreLoanProcessClient.ClientCredentials.UserName.Password`.
   * Wijs de constante waarde toe `HttpClientCredentialType.Basic` aan het gegevenslid `BasicHttpBindingSecurity.Transport.ClientCredentialType`.
   * Wijs de constante waarde toe `BasicHttpSecurityMode.TransportCredentialOnly` aan het gegevenslid `BasicHttpBindingSecurity.Security.Mode`.
   In het volgende codevoorbeeld worden deze taken getoond.

   ```as3
    //Enable BASIC HTTP authentication
    BasicHttpBinding b = (BasicHttpBinding)mortgageClient.Endpoint.Binding;
    b.MessageEncoding = WSMessageEncoding.Mtom;
    mortgageClient.ClientCredentials.UserName.UserName = "administrator";
    mortgageClient.ClientCredentials.UserName.Password = "password";
    b.Security.Transport.ClientCredentialType = HttpClientCredentialType.Basic;
    b.Security.Mode = BasicHttpSecurityMode.TransportCredentialOnly;
    b.MaxReceivedMessageSize = 2000000;
    b.MaxBufferSize = 2000000;
    b.ReaderQuotas.MaxArrayLength = 2000000;
   ```

1. Haal de naam, de telefoon, en de bedragen op die de gebruiker in de Web-pagina inging. Gebruik deze waarden om dynamisch een XML-gegevensbron te maken die naar het `FirstAppSolution/PreLoanProcess` proces wordt verzonden. Maak een formulier `System.Xml.XmlDocument` dat staat voor de XML-gegevensbron die aan het proces moet worden doorgegeven (deze toepassingslogica wordt in het volgende codevoorbeeld getoond).
1. Zet de `System.Xml.XmlDocument` instantie om in `InvokePreLoanProcess.PreLoanProcess.XML` (deze toepassingslogica wordt getoond in het volgende codevoorbeeld).
1. Roep het `FirstAppSolution/PreLoanProcess` proces aan door de `FirstAppSolution_PreLoanProcessClient` methode van het `invoke_Async` object aan te roepen. Deze methode retourneert een tekenreekswaarde die de aanroepende-id-waarde van het langlevende proces vertegenwoordigt.
1. Maak een object `JobManagerClient` met behulp van constructor. (Controleer of u een serviceverwijzing hebt ingesteld naar de service Taakbeheer.)
1. Herhaal stap 1-5. Geef de volgende URL op voor stap 2: `https://hiro-xp:8080/soap/services/JobManager?blob=mtom`.
1. Maak een `JobId` object met de constructor ervan.
1. Stel het `JobId` gegevenslid van het `id` object in met de geretourneerde waarde van de `FirstAppSolution_PreLoanProcessClient` methode van het `invoke_Async` object.
1. Wijs de waarde `value` true toe aan het `JobId` gegevenslid van het object `persistent` .
1. Maak een `JobStatus` object door de methode van het `JobManagerService` object aan te roepen `getStatus` en het `JobId` object door te geven.
1. Haal de statuswaarde op door de waarde van het `JobStatus` gegevenslid van het `statusCode` object op te halen.
1. Wijs de waarde van de aanroepings-id toe aan het `LabelJobID.Text` veld.
1. Wijs de statuswaarde toe aan het `LabelStatus.Text` veld.

### Snel starten: Een langdurig proces aanroepen met de webservice-API {#quick-start-invoking-a-long-lived-process-using-the-web-service-api}

Het volgende C# codevoorbeeld roept het `FirstAppSolution/PreLoanProcess`proces aan.

```as3
 ???/**
     * Ensure that you create a .NET project that uses
     * MS Visual Studio 2008 and version 3.5 of the .NET
     * framework. This is required to invoke a
     * AEM Forms service using MTOM.
 
 
 using System;
 using System.Collections;
 using System.Configuration;
 using System.Data;
 using System.Linq;
 using System.Web;
 using System.ServiceModel;
 using System.Web.Security;
 using System.Web.UI;
 using System.Web.UI.HtmlControls;
 using System.Web.UI.WebControls;
 using System.Web.UI.WebControls.WebParts;
 using System.Xml.Linq;
 using System.Xml;
 using System.IO;
 
 //A reference to FirstAppSolution/PreLoanProcess
 using InvokePreLoanProcess.PreLoanProcess;
 
 //A reference to JobManager service
 using InvokePreLoanProcess.JobManager;
 
 
 namespace InvokePreLoanProcess
 {
        public partial class _Default : System.Web.UI.Page
        {
            //This method is called when the Submit Application button is
            //Clicked
            protected void Button1_Click(object sender, EventArgs e)
            {
                //Create a FirstAppSolution_PreLoanProcessClient object
                FirstAppSolution_PreLoanProcessClient mortgageClient = new FirstAppSolution_PreLoanProcessClient();
                mortgageClient.Endpoint.Address = new System.ServiceModel.EndpointAddress("https://hiro-xp:8080/soap/services/FirstAppSolution/PreLoanProcess?blob=mtom");
 
                //Enable BASIC HTTP authentication
                BasicHttpBinding b = (BasicHttpBinding)mortgageClient.Endpoint.Binding;
                b.MessageEncoding = WSMessageEncoding.Mtom;
                mortgageClient.ClientCredentials.UserName.UserName = "administrator";
                mortgageClient.ClientCredentials.UserName.Password = "password";
                b.Security.Transport.ClientCredentialType = HttpClientCredentialType.Basic;
                b.Security.Mode = BasicHttpSecurityMode.TransportCredentialOnly;
                b.MaxReceivedMessageSize = 2000000;
                b.MaxBufferSize = 2000000;
                b.ReaderQuotas.MaxArrayLength = 2000000;
 
                //Retrieve values that user entered into the web page
                String userName = TextBoxName.Text;
                String phone = TextBoxPhone.Text;
                String amount = TextBoxAmount.Text;
 
                //Create the XML to pass to the FirstAppSolution/PreLoanProcess process
                XmlDocument myXML = CreateXML(userName, phone, amount);
 
                StringWriter sw = new StringWriter();
                XmlTextWriter xw = new XmlTextWriter(sw);
                myXML.WriteTo(xw);
 
                InvokePreLoanProcess.PreLoanProcess.XML inXML = new XML();
                inXML.document = sw.ToString();
 
                //INvoke the FirstAppSolution/PreLoanProcess process
                String invocationID =  mortgageClient.invoke_Async(inXML);
 
                //Create a JobManagerClient object to obtain the status of the long-lived operation
                JobManagerClient jobManager = new JobManagerClient();
                jobManager.Endpoint.Address = new System.ServiceModel.EndpointAddress("https://hiro-xp:8080/soap/services/JobManager?blob=mtom");
 
                //Enable BASIC HTTP authentication
                BasicHttpBinding b1 = (BasicHttpBinding)jobManager.Endpoint.Binding;
                b1.MessageEncoding = WSMessageEncoding.Mtom;
                jobManager.ClientCredentials.UserName.UserName = "administrator";
                jobManager.ClientCredentials.UserName.Password = "password";
                b1.Security.Transport.ClientCredentialType = HttpClientCredentialType.Basic;
                b1.Security.Mode = BasicHttpSecurityMode.TransportCredentialOnly;
                b1.MaxReceivedMessageSize = 2000000;
                b1.MaxBufferSize = 2000000;
                b1.ReaderQuotas.MaxArrayLength = 2000000;
 
 
                //Create a JobID object that represents the status of the
                //long-lived operation
                JobId jobId = new JobId();
                jobId.id = invocationID;
                jobId.persistent = true;
                JobStatus jobStatus = jobManager.getStatus(jobId);
                System.Int16 val2 = jobStatus.statusCode;
                LabelJobID.Text = "The job status identifier value is " + invocationID;
                LabelStatus.Text = "The status of the long-lived operation is " + getJobDescription(val2);
 
            }
 
            private static XmlDocument CreateXML(String name, String phone, String amount)
            {
                //This method dynamically creates a DDX document
                //to pass to the FirstAppSolution/PreLoanProcess process
                XmlDocument xmlDoc = new XmlDocument();
 
                //Create the root element and append it to the XML DOM
                System.Xml.XmlElement root = xmlDoc.CreateElement("LoanApp");
                xmlDoc.AppendChild(root);
 
                //Create the Name element
                XmlElement nameElement = xmlDoc.CreateElement("Name");
                nameElement.AppendChild(xmlDoc.CreateTextNode(name));
                root.AppendChild(nameElement);
 
                //Create the LoanAmount element
                XmlElement LoanAmount = xmlDoc.CreateElement("LoanAmount");
                LoanAmount.AppendChild(xmlDoc.CreateTextNode(amount));
                root.AppendChild(LoanAmount);
 
                //Create the PhoneOrEmail element
                XmlElement PhoneOrEmail = xmlDoc.CreateElement("PhoneOrEmail");
                PhoneOrEmail.AppendChild(xmlDoc.CreateTextNode(phone));
                root.AppendChild(PhoneOrEmail);
 
                //Create the ApprovalStatus element
                XmlElement ApprovalStatus = xmlDoc.CreateElement("ApprovalStatus");
                ApprovalStatus.AppendChild(xmlDoc.CreateTextNode("PENDING APPROVAL"));
                root.AppendChild(ApprovalStatus);
 
                //Return the XmlElement instance
                return xmlDoc;
            }
 
 
            //Returns the String value of the Job Manager status code
            private String getJobDescription(int val)
            {
                switch(val)
                {
                    case 0:
                        return "JOB_STATUS_UNKNOWN";
 
                    case 1:
                        return "JOB_STATUS_QUEUED";
 
                    case 2:
                        return "JOB_STATUS_RUNNING";
 
                    case 3:
                        return "JOB_STATUS_COMPLETED";
 
                    case 4:
                        return "JOB_STATUS_FAILED";
 
                     case 5:
                        return "JOB_STATUS_COMPLETED";
 
                    case 6:
                        return "JOB_STATUS_SUSPENDED";
 
                    case 7:
                        return "JOB_STATUS_COMPLETE_REQUESTED";
 
                    case 8:
                        return "JOB_STATUS_TERMINATE_REQUESTED";
 
                     case 9:
                        return "JOB_STATUS_SUSPEND_REQUESTED";
 
                       case 10:
                        return "JOB_STATUS_RESUME_REQUESTED";
                }
 
                return "";
            }
       }
 }
 
```

>[!NOTE]
>
>De waarden in de door de gebruiker gedefinieerde getJobDescription-methode komen overeen met de waarden die door de service Taakbeheer worden geretourneerd.

### De toepassing ASP.NET uitvoeren {#run-the-asp-net-application}

Nadat u uw toepassing ASP.NET compileert en opstelt, kunt u het uitvoeren gebruikend Webbrowser. Ervan uitgaande dat de naam van het ASP.NET-project *InvokePreLoanProcess* is, geeft u de volgende URL op in een webbrowser:

*http://localhost:1629/InvokePreLoanProcess/*Default.aspx

waarbij localhost de naam is van de webserver die als host fungeert voor het ASP.NET-project en 1629 het poortnummer. Wanneer u compileert en uw toepassing ASP.NET bouwt, stelt Microsoft Visual Studio automatisch het op.

>[!NOTE]
>
>Om te bevestigen dat de toepassing ASP.NET het proces aanhaalde, begin Werkruimte en keur de lening goed.

## Een clienttoepassing maken die is gebouwd met Flex en die een menselijk-centrisch proces van lange duur aanroept {#creating-a-client-application-built-with-flex-that-invokes-a-human-centric-long-lived-process}

U kunt een clienttoepassing maken die met Flex is gebouwd om het *proces FirstAppSolution/PreLoanProcess* aan te roepen. Deze toepassing gebruikt Remoting om het proces *FirstAppSolution/PreLoanProcess* aan te roepen. (Zie AEM-formulieren [aanroepen met (Verouderd voor AEM-formulieren) AEM-formulieren verwijderen](/help/forms/developing/invoking-aem-forms-using-remoting.md#invoking-aem-forms-using-remoting).)

In de volgende afbeelding ziet u een clienttoepassing die is gebouwd met Flex en gegevens van een eindgebruiker verzamelt. De gegevens worden in een XML-gegevensbron geplaatst en naar het proces verzonden.

Nadat het proces is aangeroepen, wordt een waarde voor de aanroepings-id weergegeven. Een waarde voor de oproepings-id wordt gemaakt als onderdeel van een record die de status van het proces met een lange levensduur bijhoudt.

De clienttoepassing die met Flex is gebouwd, voert de volgende taken uit:

* Haalt de waarden op die de gebruiker op de webpagina heeft ingevoerd.
* Maakt dynamisch een XML-gegevensbron die wordt doorgegeven aan het *proces FirstAppSolution/PreLoanProcess* . De drie waarden worden opgegeven in de XML-gegevensbron.
* Roept het *proces FirstAppSolution/PreLoanProcess* aan door Remoting te gebruiken.
* Retourneert de aanroepings-id-waarde van het langlevende proces.

### Overzicht van de stappen {#summary_of_steps-2}

Voer de volgende stappen uit om een clienttoepassing te maken die is gebouwd met Flex en het proces FirstAppSolution/PreLoanProcess kan aanroepen:

1. Start een nieuw Flex-project.
1. Neem het bestand adobe-remoting-provider.swc op in het klassenpad van uw project. (Zie [Inclusief het Flex-bibliotheekbestand](/help/forms/developing/invoking-aem-forms-using-remoting.md#including-the-aem-forms-flex-library-file)voor AEM-formulieren.)
1. Maak een `mx:RemoteObject` instantie via ActionScript of MXML. (Zie [Een instantie](/help/forms/developing/invoking-aem-forms-using-remoting.md)mx:RemoteObject maken)
1. Stel een `ChannelSet` instantie in voor communicatie met AEM Forms en koppel deze aan de `mx:RemoteObject` instantie. (Zie [Een kanaal naar AEM-formulieren](/help/forms/developing/invoking-aem-forms-using-remoting.md)maken.)
1. Roep de `login` methode van ChannelSet of de `setCredentials` methode van de dienst aan om de waarde en het wachtwoord van het gebruikersherkenningsteken te specificeren. (Zie Single Sign-On [gebruiken](/help/forms/developing/invoking-aem-forms-using-remoting.md#using-single-sign-on).)
1. Maak de XML-gegevensbron die u aan het `FirstAppSolution/PreLoanProcess` proces wilt doorgeven door een XML-instantie te maken. (Deze toepassingslogica wordt getoond in het volgende codevoorbeeld.)
1. Maak een object van het type Object met behulp van de constructor. Wijs XML aan het voorwerp toe door de naam van de de inputparameter van het proces, zoals aangetoond in de volgende code te specificeren:

   ```as3
    //Get the XML data to pass to the AEM Forms process
    var xml:XML = createXML();
    var params:Object = new Object();
    params["formData"]=xml;
   ```

1. Roep het `FirstAppSolution/PreLoanProcess` proces aan door de `mx:RemoteObject` methode van de `invoke_Async` instantie aan te roepen. Geef door `Object` welke invoerparameter bevat. (Zie [Invoerwaarden](/help/forms/developing/invoking-aem-forms-using-remoting.md)doorgeven.)
1. Haal de aanroepings-identificatiewaarde op die door een langdurig proces wordt geretourneerd, zoals in de volgende code wordt getoond:

   ```as3
    // Handles async call that invokes the long-lived process
    private function resultHandler(event:ResultEvent):void
    {
    ji = event.result as JobId;
    jobStatusDisplay.text = "Job Status ID: " + ji.jobId as String;
    }
   ```

### Een langdurig proces aanroepen met Verwijderen {#invoking-a-long-lived-process-using-remoting}

Het volgende Flex codevoorbeeld roept het `FirstAppSolution/PreLoanProcess` proces aan.

```as3
 <?xml version="1.0" encoding="utf-8"?>
 
 <mx:Application  xmlns="*" backgroundColor="#FFFFFF"
      creationComplete="initializeChannelSet();">
 
 <mx:Script>
          <![CDATA[
 
             import mx.controls.Alert;
             import mx.rpc.events.FaultEvent;
             import mx.rpc.events.ResultEvent;
             import flash.net.navigateToURL;
             import mx.messaging.ChannelSet;
             import mx.messaging.channels.AMFChannel;
             import mx.collections.ArrayCollection;
             import mx.rpc.livecycle.JobId;
             import mx.rpc.livecycle.JobStatus;
             import mx.rpc.livecycle.DocumentReference;
             import mx.formatters.NumberFormatter;
 
             // Holds the job ID returned by LC.JobManager
             private var ji:JobId;
 
             private function initializeChannelSet():void
              {
              var cs:ChannelSet= new ChannelSet();
         cs.addChannel(new AMFChannel("remoting-amf", "https://hiro-xp:8080/remoting/messagebroker/amf"));
         LC_MortgageApp.setCredentials("tblue", "password");
         LC_MortgageApp.channelSet = cs;
              }
 
            private function submitApplication():void
             {
             //Get the XML data to pass to the AEM Forms process
             var xml:XML = createXML();
             var params:Object = new Object();
             params["formData"]=xml;
             LC_MortgageApp.invoke_Async(params);
             }
 
             // Handles async call that invokes the long-lived process
             private function resultHandler(event:ResultEvent):void
             {
                ji = event.result as JobId;
                jobStatusDisplay.text = "Job Status ID: " + ji.jobId as String;
             }
 
             private function createXML():XML
             {
                //Calculate the Mortgage value to place in the XML data
                var propertyPrice:String = txtAmount.text ;
                var name:String = txtName.text ;
                var phone:String = txtPhone.text ;;
 
                var model:XML =
 
                  <LoanApp>
                           <Name>{name}</Name>
                           <LoanAmount>{propertyPrice}</LoanAmount>
                           <PhoneOrEmail>{phone}</PhoneOrEmail>
                           <ApprovalStatus>PENDING APPROVAL</ApprovalStatus>
                  </LoanApp>
 
              return model;
             }
 
 
          ]]>
       </mx:Script>
 
       <!-- Declare the RemoteObject and set its destination to the mortgage-app remoting endpoint defined in AEM Forms. -->
       <mx:RemoteObject id="LC_MortgageApp" destination="FirstAppSolution/PreLoanProcess" result="resultHandler(event);">
          <mx:method name="invoke_Async" result="resultHandler(event)"/>
      </mx:RemoteObject>
 
 
     <mx:Grid x="229" y="186">
         <mx:GridRow width="100%" height="100%">
             <mx:GridItem width="100%" height="100%">
                 <mx:Image>
                     <mx:source>file:///D|/LiveCycle_9/FirstApp/financeCorpLogo.jpg</mx:source>
                 </mx:Image>
             </mx:GridItem>
             <mx:GridItem width="100%" height="100%">
                 <mx:Label text="Flex Loan Application Page" fontSize="20"/>
             </mx:GridItem>
             <mx:GridItem width="100%" height="100%">
             </mx:GridItem>
         </mx:GridRow>
         <mx:GridRow width="100%" height="100%">
             <mx:GridItem width="100%" height="100%">
                 <mx:Label text="Name:" fontSize="12" fontWeight="bold"/>
             </mx:GridItem>
             <mx:GridItem width="100%" height="100%">
                 <mx:TextInput id="txtName"/>
             </mx:GridItem>
             <mx:GridItem width="100%" height="100%">
                 <mx:Button label="Submit Application" click="submitApplication()"/>
             </mx:GridItem>
         </mx:GridRow>
         <mx:GridRow width="100%" height="100%">
             <mx:GridItem width="100%" height="100%">
                 <mx:Label text="Phone/Email:" fontSize="12" fontWeight="bold"/>
             </mx:GridItem>
             <mx:GridItem width="100%" height="100%">
                 <mx:TextInput id="txtPhone"/>
             </mx:GridItem>
             <mx:GridItem width="100%" height="100%">
             </mx:GridItem>
         </mx:GridRow>
         <mx:GridRow width="100%" height="100%">
             <mx:GridItem width="100%" height="100%">
                 <mx:Label text="Amount:" fontSize="12" fontWeight="bold"/>
             </mx:GridItem>
             <mx:GridItem width="100%" height="100%">
                 <mx:TextInput id="txtAmount"/>
             </mx:GridItem>
             <mx:GridItem width="100%" height="100%">
             </mx:GridItem>
         </mx:GridRow>
         <mx:GridRow width="100%" height="100%">
             <mx:GridItem width="100%" height="100%">
             </mx:GridItem>
             <mx:GridItem width="100%" height="100%">
                 <mx:Label text="Label" id="jobStatusDisplay" enabled="true" fontSize="12" fontWeight="bold"/>
             </mx:GridItem>
             <mx:GridItem width="100%" height="100%">
             </mx:GridItem>
         </mx:GridRow>
     </mx:Grid>
 
 </mx:Application>
 
```

