---
title: Het aanhalen van mens-Centric langlevende Processen
description: Programmaticaal roep mens-centric langlevende processen aan die in Workbench worden gecreeerd gebruikend een Web-based Java cliënttoepassing die de Inroeping API, een ASP.NET toepassing gebruikt die de Webdiensten, en een cliënttoepassing gebruikt die met Flex wordt gebouwd die het Verwijderen gebruikt.
contentOwner: admin
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: coding
role: Developer
exl-id: c9ebad8b-b631-492d-99a3-094e892b2ddb
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms,APIs & Integrations,AEM Forms on JEE
source-git-commit: d7b9e947503df58435b3fee85a92d51fae8c1d2d
workflow-type: tm+mt
source-wordcount: '3674'
ht-degree: 0%

---

# Het aanhalen van mens-Centric langlevende Processen {#invoking-human-centric-long-lived-processes}

U kunt mens-centric langlevende processen programmatically aanhalen die in Workbench gebruikend deze cliënttoepassingen werden gecreeerd:

* Een Java-clienttoepassing op het web die de Invocation-API gebruikt. (Zie [&#x200B; het Aanhalen AEM Forms gebruikend Java API &#x200B;](/help/forms/developing/invoking-aem-forms-using-java.md) (/help/forms/developing/invoking-aem-forms-using-java.md#invoking-aem-forms-using-the-java-api).)
* Een ASP.NET-toepassing die webservices gebruikt. (Zie [&#x200B; het aanhalen van AEM Forms die de Diensten van het Web gebruiken &#x200B;](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-web-services).)
* Een clienttoepassing die is gebouwd met Flex die Remoting gebruikt. (Zie [&#x200B; het Aanhalen van AEM Forms die (voor AEM vormen) AEM Forms verwijdert &#x200B;](/help/forms/developing/invoking-aem-forms-using-remoting.md#invoking-aem-forms-using-remoting) gebruikt.)

Het proces met lange duur dat wordt aangehaald wordt genoemd *FirstAppSolution/PreLoanProcess*. U kunt dit proces tot stand brengen door het leerprogramma te volgen dat in [&#x200B; wordt gespecificeerd Creërend Uw Eerste Toepassing van AEM Forms &#x200B;](https://www.adobe.com/go/learn_aemforms_firstapp_ds_63).

Een mens-centric proces impliceert een taak die een gebruiker kan antwoorden aan door Workspace te gebruiken. Met Workbench kunt u bijvoorbeeld een proces maken waarmee een bankmanager een leningtoepassing kan goedkeuren of weigeren. De volgende illustratie toont het proces *FirstAppSolution/PreLoanProcess*.

Het *FirstAppSolution/PreLoanProcess* proces keurt een inputparameter genoemd *formData* goed het waarvan gegevenstype XML is. De gegevens van XML worden samengevoegd met een vormontwerp genoemd *PreLoanForm.xdp*. In de volgende afbeelding ziet u een formulier dat een taak vertegenwoordigt die aan een gebruiker is toegewezen om een leningtoepassing goed te keuren of te weigeren. De gebruiker keurt of ontkent de toepassing door Workspace te gebruiken. De Workspace-gebruiker kan de aanvraag voor een lening goedkeuren door op de knop Goedkeuren in de volgende afbeelding te klikken. Op dezelfde manier kan de gebruiker het verzoek om een lening weigeren door op de knop Weigeren te klikken.

Een proces van lange duur wordt asynchroon aangehaald en kan niet synchroon wegens de volgende factoren worden aangehaald:

* Een proces kan veel tijd in beslag nemen.
* Een proces kan organisatorische grenzen overspannen.
* Een proces heeft externe input nodig om het te voltooien. Neem bijvoorbeeld een situatie waarin een formulier wordt verzonden naar een manager die zich buiten het kantoor bevindt. In dit geval is het proces niet volledig totdat de manager het formulier retourneert en invult.

Wanneer een langdurig proces wordt aangeroepen, maakt AEM Forms een waarde voor de aanroepings-id als onderdeel van het maken van een record. De record houdt de status van het langlevende proces bij en wordt opgeslagen in de AEM Forms-database. Met de waarde voor de oproepings-id kunt u de status van het langlevende proces volgen. Bovendien kunt u de waarde van de proces aanroepings herkenningsteken gebruiken om verrichtingen van de Manager van het Proces uit te voeren zoals het beëindigen van een lopende procesinstantie.

>[!NOTE]
>
>AEM Forms maakt geen aanroepings-id-waarde of record wanneer een kortstondig proces wordt aangeroepen.

Het `FirstAppSolution/PreLoanProcess` -proces wordt opgeroepen wanneer een aanvrager een toepassing indient, die wordt weergegeven als XML-gegevens. De naam van de invoerprocesvariabele is `formData` en het gegevenstype is XML. In deze beschrijving wordt ervan uitgegaan dat de volgende XML-gegevens worden gebruikt als invoer voor het `FirstAppSolution/PreLoanProcess` -proces.

```xml
 <?xml version="1.0" encoding="UTF-8"?>
 <LoanApp>
 <Name>Sam White</Name>
 <LoanAmount>250000</LoanAmount>
 <PhoneOrEmail>(555)555-5555</PhoneOrEmail>
 <ApprovalStatus>PENDING APPROVAL</ApprovalStatus>
 </LoanApp>
```

XML-gegevens die aan een proces worden doorgegeven, moeten overeenkomen met de velden in het formulier dat in het proces wordt gebruikt. Anders worden de gegevens niet weergegeven in het formulier. Alle toepassingen die het `FirstAppSolution/PreLoanProcess` -proces aanroepen, moeten deze XML-gegevensbron doorgeven. De toepassingen die in *worden gecreeerd aanroepend mens-Centric langlevende Processen* creëren dynamisch de gegevensbron van XML van waarden die een gebruiker in een Webcliënt inging.

Gebruikend een cliënttoepassing, kunt u *FirstAppSolution/PreLoanProcess* verzenden verwerken de vereiste gegevens van XML. Een langlevend proces retourneert een waarde voor de oproepings-id als geretourneerde waarde. De volgende illustratie toont cliënttoepassingen die het*FirstAppSolution/PreLoanProcess langdurig proces aanhalen. De clienttoepassingen verzenden XML-gegevens en krijgen een tekenreekswaarde die de waarde van de aanroepings-id vertegenwoordigt.

**zie ook**

[Een Java-webtoepassing maken die een menselijk-centrisch proces van lange duur oproept](invoking-human-centric-long-lived.md#creating-a-java-web-application-that-invokes-a-human-centric-long-lived-process)

[Een ASP.NET-webtoepassing maken die een menselijk-centrisch proces van lange duur oproept](invoking-human-centric-long-lived.md#creating-an-asp-net-web-application-that-invokes-a-human-centric-long-lived-process)

[Een clienttoepassing maken die is gebouwd met Flex en die een menselijk-centrisch proces van lange duur aanroept](invoking-human-centric-long-lived.md#creating-a-client-application-built-with-flex-that-invokes-a-human-centric-long-lived-process)

## Een Java-webtoepassing maken die een menselijk-centrisch proces van lange duur oproept {#creating-a-java-web-application-that-invokes-a-human-centric-long-lived-process}

U kunt een webtoepassing maken die een Java-servlet gebruikt om het `FirstAppSolution/PreLoanProcess` -proces aan te roepen. Als u dit proces vanuit een Java-servlet wilt aanroepen, gebruikt u de API voor aanroepen in de Java-servlet. (Zie [&#x200B; het Aanhalen van AEM Forms gebruikend Java API &#x200B;](/help/forms/developing/invoking-aem-forms-using-java.md#invoking-aem-forms-using-the-java-api).)

In de volgende afbeelding ziet u een clienttoepassing op het web waarmee de naam, telefoon (of e-mail) en waarden worden gepost. Deze waarden worden naar de Java-server verzonden wanneer de gebruiker op de knop Toepassing verzenden klikt.

Java servlet voert de volgende taken uit:

* Haalt de waarden op die van de pagina HTML naar het Java-servlet zijn gepost.
* Creeert dynamisch een gegevensbron van XML om tot het *FirstAppSolution/PreLoanProcess* proces over te gaan. De naam, telefoon (of e-mail) en de waarden voor de hoeveelheid worden opgegeven in de XML-gegevensbron.
* Roept het *FirstAppSolution/PreLoanProcess* proces door AEM Forms Invocation API te gebruiken aan.
* Hiermee wordt de waarde van de oproepings-id geretourneerd aan de webbrowser van de client.

### Overzicht van de stappen {#summary-of-steps}

Voer de volgende stappen uit om een Java-webtoepassing te maken die het `FirstAppSolution/PreLoanProcess` -proces oproept:

1. [&#x200B; creeer een Webproject &#x200B;](invoking-human-centric-long-lived.md#create-a-web-project).
1. [&#x200B; creeer de toepassingslogica van Java voor servlet &#x200B;](invoking-human-centric-long-lived.md#create-java-application-logic-for-the-servlet).
1. [De webpagina voor de webtoepassing maken](invoking-human-centric-long-lived.md#create-the-web-page-for-the-web-application)
1. [&#x200B; verpak de Webtoepassing aan een dossier van WAR &#x200B;](invoking-human-centric-long-lived.md#package-the-web-application-to-a-war-file).
1. [&#x200B; stel het dossier van WAR aan de J2EE toepassingsserver op die AEM Forms &#x200B;](invoking-human-centric-long-lived.md#deploy-the-war-file-to-the-j2ee-application-server-hosting-aem-forms) ontvangen.
1. [&#x200B; Test uw Webtoepassing &#x200B;](invoking-human-centric-long-lived.md#test-your-web-application).

>[!NOTE]
>
>Sommige van deze stappen zijn afhankelijk van de J2EE-toepassing waarop AEM Forms wordt geïmplementeerd. De methode die u bijvoorbeeld gebruikt om een WAR-bestand te implementeren, is afhankelijk van de J2EE-toepassingsserver die u gebruikt. Aangenomen wordt dat AEM Forms wordt geïmplementeerd op JBoss®.

### Een webproject maken {#create-a-web-project}

De eerste stap voor het maken van een webtoepassing is het maken van een webproject. De Java-IDE waarop dit document is gebaseerd, is Eclipse 3.3. Gebruikend IDE van de Verduistering, creeer een Webproject en voeg de vereiste JAR dossiers aan uw project toe. Voeg een HTML pagina genoemd *index.html* en een servlet van Java aan uw project toe.

In de volgende lijst worden de JAR-bestanden weergegeven die in uw webproject moeten worden opgenomen:

* adobe-livecycle-client.jar
* adobe-usermanager-client.jar
* J2EE.jar

Voor de plaats van deze JAR dossiers, zie [&#x200B; Inclusief de bibliotheekdossiers van AEM Forms Java &#x200B;](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files).

>[!NOTE]
>
>Het bestand J2EE.jar definieert gegevenstypen die door een Java-servlet worden gebruikt. U kunt dit JAR-bestand verkrijgen van de J2EE-toepassingsserver waarop AEM Forms is geïmplementeerd.

**creeer een Webproject**

1. Begin Eclipse en klik **Dossier** > **Nieuw Project**.
1. In het **Nieuwe de dialoogvakje van het Project**, uitgezochte **Web** > **Dynamisch Project van het Web**.
1. Het type `InvokePreLoanProcess` voor de naam van uw project en klikt dan **Afwerking**.

**voeg vereiste JAR dossiers aan uw project toe**

1. Van het venster van de Ontdekkingsreiziger van het Project, klik het `InvokePreLoanProcess` project met de rechtermuisknop aan en selecteer **Eigenschappen**.
1. Klik **Java bouwt weg** en klik dan de **Bibliotheken** tabel.
1. Klik **toevoegen Externe JARs** knoop en doorblader aan de JAR dossiers om te omvatten.

**voeg een servlet van Java aan uw project toe**

1. Van het venster van de Ontdekkingsreiziger van het Project, klik het `InvokePreLoanProcess` project met de rechtermuisknop aan en selecteer **Nieuw** > **Andere**.
1. Breid de **omslag van het Web** uit, selecteer **Servlet**, en klik dan **daarna**.
1. In Create Servlet dialoogdoos, type `SubmitXML` voor de naam van servlet en klik dan **Afwerking**.

**voeg een pagina van de HTML aan uw project** toe

1. Van het venster van de Ontdekkingsreiziger van het Project, klik het `InvokePreLoanProcess` project met de rechtermuisknop aan en selecteer **Nieuw** > **Andere**.
1. Breid de **omslag van het Web** uit, selecteer **HTML**, en klik **daarna**.
1. In het Nieuwe de dialoogvakje van de HTML, type `index.html` voor filename en klik dan **Afwerking**.

>[!NOTE]
>
>Voor informatie over het creëren van HTML inhoud die SubmitXML Java servlet aanhaalt, zie [&#x200B; de Web-pagina voor de Webtoepassing &#x200B;](invoking-human-centric-long-lived.md#create-the-web-page-for-the-web-application) creëren.

### Java-toepassingslogica voor de servlet maken {#create-java-application-logic-for-the-servlet}

Maak Java-toepassingslogica die het `FirstAppSolution/PreLoanProcess` -proces aanroept vanuit de Java-servlet. De volgende code toont de syntaxis van de `SubmitXML` Java Server:

```java
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

Normaal gesproken plaatst u geen clientcode in een Java-servlet- `doGet` of `doPost` -methode. Een betere programmeerpraktijk is deze code binnen een afzonderlijke klasse te plaatsen. Instantieer vervolgens de klasse vanuit de methode `doPost` (of de methode `doGet` ) en roep de juiste methoden aan. Voor codebeknoptheid worden codevoorbeelden echter tot een minimum beperkt en in de methode `doPost` geplaatst.

Als u het `FirstAppSolution/PreLoanProcess` -proces wilt aanroepen met de API voor aanroepen, voert u de volgende taken uit:

1. Neem client-JAR-bestanden, zoals adobe-livecycle-client.jar, op in het klassenpad van uw Java-project. Voor informatie over de plaats van deze dossiers, zie [&#x200B; Inclusief de bibliotheekdossiers van AEM Forms Java &#x200B;](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files).
1. Haal de naam, de telefoon, en de waardewaarden op van de HTML pagina die worden voorgelegd. Gebruik deze waarden om dynamisch een XML-gegevensbron te maken die naar het `FirstAppSolution/PreLoanProcess` -proces wordt verzonden. U kunt `org.w3c.dom` -klassen gebruiken om de XML-gegevensbron te maken (deze toepassingslogica wordt in het volgende codevoorbeeld getoond).
1. Maak een `ServiceClientFactory` -object dat verbindingseigenschappen bevat. (Zie [&#x200B; Plaatsende verbindingseigenschappen &#x200B;](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties).)
1. Maak een `ServiceClient` -object door de constructor ervan te gebruiken en het `ServiceClientFactory` -object door te geven. Met een `ServiceClient` -object kunt u een servicebewerking aanroepen. Het behandelt taken zoals het lokaliseren van, het verzenden van, en het verpletteren van oproepingsverzoeken.
1. Maak een `java.util.HashMap` -object met behulp van de constructor.
1. Roep de methode `put` van het `java.util.HashMap` object aan voor elke invoerparameter die wordt doorgegeven aan het langlevende proces. Zorg ervoor dat u de naam van de invoerparameters van het proces opgeeft. Omdat voor het `FirstAppSolution/PreLoanProcess` -proces één invoerparameter van het type `XML` (genaamd `formData` ) vereist is, hoeft u de methode `put` slechts eenmaal aan te roepen.

   ```java
    //Get the XML to pass to the FirstAppSolution/PreLoanProcess process
    org.w3c.dom.Document inXML = GetDataSource(name,phone,amount);
    
    //Create a Map object to store the parameter value
    Map params = new HashMap();
    params.put("formData", inXML);
   ```

1. Maak een `InvocationRequest` -object door de methode `ServiceClientFactory` object `createInvocationRequest` aan te roepen en de volgende waarden door te geven:

   * Een tekenreekswaarde die de naam aangeeft van het proces met een lange levensduur dat moet worden aangeroepen. Geef `FirstAppSolution/PreLoanProcess` op om het `FirstAppSolution/PreLoanProcess` -proces op te roepen.
   * Een tekenreekswaarde die staat voor de naam van de procesbewerking. De naam van de langlevende procesbewerking is `invoke` .
   * Het `java.util.HashMap` -object dat de parameterwaarden bevat die de servicebewerking vereist.
   * Een Booleaanse waarde die `false` opgeeft en die een asynchrone aanvraag maakt (deze waarde is van toepassing om een langlevend proces aan te roepen).

   >[!NOTE]
   >
   >*Een kortstondig proces kan worden aangehaald door de waarde waar als vierde parameter van de createInvocationRequest methode over te gaan. Het overgaan van de waarde waar leidt tot een synchrone aanvraag.*

1. Verzend de aanroepingsaanvraag naar AEM Forms door de methode `invoke` van het object `ServiceClient` aan te roepen en het object `InvocationRequest` door te geven. De methode `invoke` retourneert een `InvocationReponse` -object.
1. Een langlevend proces retourneert een tekenreekswaarde die een aanroepende-identificatiewaarde vertegenwoordigt. Haal deze waarde op door de methode `getInvocationId` van het object `InvocationReponse` aan te roepen.

   ```java
    //Send the invocation request to the long-lived process and
    //get back an invocation response object
    InvocationResponse lcResponse = myServiceClient.invoke(lcRequest);
    String invocationId = lcResponse.getInvocationId();
   ```

1. Schrijf de waarde voor de oproepidentificatie naar de webbrowser van de client. U kunt een `java.io.PrintWriter` -instantie gebruiken om deze waarde naar de webbrowser van de client te schrijven.

### Snel starten: Een langdurig proces aanroepen met de API voor aanroepen {#quick-start-invoking-a-long-lived-process-using-the-invocation-api}

In het volgende Java-codevoorbeeld ziet u het Java-servlet dat het `FirstAppSolution/PreLoanProcess` -proces aanroept.

```java
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
     * These JAR files are in the following path:
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
 
                 //Create a Document object
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

De {*Web-pagina 0} index.html verstrekt een ingangspunt aan Java servlet die het `FirstAppSolution/PreLoanProcess` proces aanhaalt.* Deze webpagina is een basisformulier voor HTML dat een HTML-formulier en een verzendknop bevat. Wanneer de gebruiker op de verzendknop klikt, worden formuliergegevens naar de Java-server van `SubmitXML` verzonden.

De Java-servlet legt de gegevens vast die vanuit de HTML-pagina zijn gepost met behulp van de volgende Java-code:

```java
 //Get the values that are passed from the Loan HTML page
 String name = request.getParameter("name");
 String phone = request.getParameter("phone");
 String amount = request.getParameter("amount");
```

De volgende HTML code vertegenwoordigt het bestand index.html dat tijdens de installatie van de ontwikkelomgeving is gemaakt. (Zie [&#x200B; tot een Webproject &#x200B;](invoking-human-centric-long-lived.md#create-a-web-project) leiden.)

```xml
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

Als u het Java-servlet wilt implementeren dat het `FirstAppSolution/PreLoanProcess` -proces oproept, moet u uw webtoepassing verpakken naar een WAR-bestand. Zorg ervoor dat externe JAR-bestanden waarvan de bedrijfslogica van de component afhankelijk is, zoals adobe-livecycle-client.jar en adobe-usermanager-client.jar, ook in het WAR-bestand worden opgenomen.

De volgende illustratie toont de inhoud van het project Eclipse, die aan een dossier van WAR wordt verpakt.

>[!NOTE]
>
>In de vorige afbeelding kan het JPG-bestand worden vervangen door een JPG afbeeldingsbestand.

**Pakket een Webtoepassing aan een dossier van WAR:**

1. Van het **venster van de Ontdekkingsreiziger van het Project**, klik het `InvokePreLoanProcess` project met de rechtermuisknop aan en selecteer **Uitvoer** > **dossier van WAR**.
1. In het **tekstvakje van de module van het Web**, type `InvokePreLoanProcess` voor de naam van het project van Java.
1. In het **tekstvakje van de Bestemming**, type `PreLoanProcess.war`**voor** filename, specificeer de plaats voor uw dossier van WAR, en klik dan Afwerking.

### WAR-bestand implementeren op de J2EE-toepassingsserver die als host fungeert voor AEM Forms {#deploy-the-war-file-to-the-j2ee-application-server-hosting-aem-forms}

Implementeer het WAR-bestand op de J2EE-toepassingsserver waarop AEM Forms is geïmplementeerd. Als u het WAR-bestand wilt implementeren op de J2EE-toepassingsserver, kopieert u het WAR-bestand van het exportpad naar `[AEM Forms Install]\Adobe\Adobe Experience Manager Forms\jboss\server\lc_turnkey\deploy` .

>[!NOTE]
>
>als AEM Forms niet wordt geïmplementeerd op JBoss, moet u het WAR-bestand implementeren in overeenstemming met de J2EE-toepassingsserver die als host fungeert voor AEM Forms.

### Uw webtoepassing testen {#test-your-web-application}

Nadat u de webtoepassing hebt geïmplementeerd, kunt u deze testen met een webbrowser. Ervan uitgaande dat u dezelfde computer gebruikt als die waarop AEM Forms wordt gehost, kunt u de volgende URL opgeven:

* http://localhost:8080/PreLoanProcess/index.html

  Voer waarden in de formuliervelden HTML in en klik op de knop Toepassing verzenden. Zie het logbestand van de J2EE-toepassingsserver als er zich problemen voordoen.

>[!NOTE]
>
>Als u wilt bevestigen dat de Java-toepassing het proces heeft aangeroepen, start u Workspace en accepteert u de lening.

## Een ASP.NET-webtoepassing maken die een menselijk-centrisch proces van lange duur oproept {#creating-an-asp-net-web-application-that-invokes-a-human-centric-long-lived-process}

U kunt een ASP.NET-toepassing maken die het `FirstAppSolution/PreLoanProcess` -proces oproept. Gebruik webservices om dit proces aan te roepen vanuit een ASP.NET-toepassing. (Zie [&#x200B; het Aanhalen van AEM Forms gebruikend de Diensten van het Web &#x200B;](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-web-services).)

In de volgende afbeelding ziet u een ASP.NET-clienttoepassing die gegevens van een eindgebruiker heeft opgehaald. De gegevens worden in een XML-gegevensbron geplaatst en naar het `FirstAppSolution/PreLoanProcess` -proces verzonden wanneer de gebruiker op de knop Toepassing verzenden klikt.

Nadat het proces is aangeroepen, wordt een waarde voor de aanroepings-id weergegeven. Een waarde voor de oproepings-id wordt gemaakt als onderdeel van een record die de status van het proces met een lange levensduur bijhoudt.

De toepassing ASP.NET voert de volgende taken uit:

* Haalt de waarden op die de gebruiker op de webpagina heeft ingevoerd.
* Creeert dynamisch een gegevensbron van XML die tot* FirstAppSolution/PreLoanProcess *process wordt overgegaan. De drie waarden worden opgegeven in de XML-gegevensbron.
* Roept het* FirstAppSolution/PreLoanProcess *process aan door de Webdiensten te gebruiken.
* Retourneert de aanroepings-id-waarde en de status van de langdurige bewerking naar de webbrowser van de client.

### Overzicht van de stappen {#summary_of_steps-1}

Voer de volgende stappen uit om een ASP.NET-toepassing te maken die het proces FirstAppSolution/PreLoanProcess kan aanroepen:

1. [&#x200B; creeer een ASP.NET Webtoepassing &#x200B;](invoking-human-centric-long-lived.md#create-an-asp-net-web-application).
1. [&#x200B; creeer een pagina van het ASPIS die FirstAppSolution/PreLoanProcess &#x200B;](invoking-human-centric-long-lived.md#create-an-asp-page-that-invokes-firstappsolution-preloanprocess) aanhaalt.
1. [&#x200B; stel de toepassing ASP.NET &#x200B;](invoking-human-centric-long-lived.md#run-the-asp-net-application) in werking.

### Een ASP.NET-webtoepassing maken {#create-an-asp-net-web-application}

Creeer een Microsoft .NET C# ASP.NET Webtoepassing. De volgende illustratie toont de inhoud van het ASP.NET project genoemd *InvokePreLoanProcess*.

Bericht onder de Verwijzingen van de Dienst, zijn er twee punten. Het eerste item heeft de naam* JobManager*. Deze verwijzing laat de toepassing ASP.NET toe om de dienst van de Manager van de Baan te halen. Deze dienst keert informatie over het statuut van een langdurig proces terug. Als het proces bijvoorbeeld op dat moment wordt uitgevoerd, retourneert deze service een numerieke waarde die aangeeft dat het proces op dat moment wordt uitgevoerd. De tweede verwijzing wordt genoemd *PreLoanProcess*. Deze serviceverwijzing vertegenwoordigt de verwijzing naar het *process* FirstAppSolution/PreLoanProcess. Nadat u een Verwijzing van de Dienst creeert, zijn de gegevenstypes verbonden aan de dienst van AEM Forms beschikbaar voor gebruik binnen uw .NET project.

**creeer een ASP.NET project:**

1. Start Microsoft Visual Studio 2008.
1. Van het **menu van het Dossier**, uitgezochte **Nieuw**, **Website**.
1. In de **lijst van Malplaatjes**, uitgezochte **ASP.NET** Website.
1. In het **vakje van de Plaats**, selecteer een plaats voor uw project. Noem uw project *InvokePreLoanProcess*.
1. In de **Taal** doos, uitgezochte Visuele C#
1. Klik op OK.

**voegt de dienstverwijzingen toe:**

1. In het menu van het Project, voegt de uitgezochte **Verwijzing van de Dienst** toe.
1. In het **de dialoogvakje van het Adres**, specificeer WSDL aan de dienst van de Manager van de Baan.

   ```java
    https://hiro-xp:8080/soap/services/JobManager?WSDL&lc_version=9.0.1
   ```

1. Typ `JobManager` in het veld Namespace.
1. Klik **gaan** en klik dan **O.K.**.
1. In het **menu van het Project**, uitgezocht **voeg de Verwijzing van de Dienst** toe.
1. In het **de dialoogvakje van het Adres**, specificeer WSDL aan het proces FirstAppSolution/PreLoanProcess.

   ```java
    https://hiro-xp:8080/soap/services/FirstAppSolution/PreLoanProcess?WSDL&lc_version=9.0.1
   ```

1. Typ `PreLoanProcess` in het veld Namespace.
1. Klik **gaan** en klik dan **O.K.**.

>[!NOTE]
>
>Vervang `hiro-xp` door het IP-adres van de J2EE-toepassingsserver die als host fungeert voor AEM Forms. De optie `lc_version` zorgt ervoor dat AEM Forms-functionaliteit, zoals MTOM, beschikbaar is. Zonder de `lc_version` optie te specificeren, kunt u geen AEM Forms aanhalen gebruikend MTOM. (Zie [&#x200B; het Aanhalen AEM Forms gebruikend MTOM &#x200B;](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom).)

### Maak een ASP-pagina die FirstAppSolution/PreLoanProcess aanroept {#create-an-asp-page-that-invokes-firstappsolution-preloanprocess}

Voeg in het ASP.NET-project een webformulier (een ASPX-bestand) toe dat verantwoordelijk is voor de weergave van een HTML-pagina bij de aanvrager van de lening. Het webformulier is gebaseerd op een klasse die is afgeleid van `System.Web.UI.Page` . De C# toepassingslogica die `FirstAppSolution/PreLoanProcess` aanhaalt is in de `Button1_Click` methode (deze knoop vertegenwoordigt de Submit knoop van de Toepassing).

In de volgende afbeelding ziet u de toepassing ASP.NET

De volgende lijst maakt een lijst van de controles die deel van deze ASP.NET toepassing uitmaken.

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
   <td><p>Knop1</p></td>
   <td><p>Geeft de knop Toepassing verzenden aan.</p></td>
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

De toepassingslogica die deel uitmaakt van de ASP.NET-toepassing moet dynamisch een XML-gegevensbron maken om door te geven aan het `FirstAppSolution/PreLoanProcess` -proces. De waarden die de aanvrager op de pagina HTML heeft ingevoerd, moeten in de XML-gegevensbron worden opgegeven. Deze gegevenswaarden worden in het formulier samengevoegd wanneer het formulier in Workspace wordt weergegeven. De klassen in de naamruimte `System.Xml` worden gebruikt om de XML-gegevensbron te maken.

Wanneer u een proces oproept waarvoor XML-gegevens van een ASP.NET-toepassing nodig zijn, kunt u een XML-gegevenstype gebruiken. U kunt dus geen `System.Xml.XmlDocument` -instantie aan het proces doorgeven. De volledig gekwalificeerde naam van deze XML-instantie die aan het proces moet worden doorgegeven, is `InvokePreLoanProcess.PreLoanProcess.XML` . Zet de instantie `System.Xml.XmlDocument` om in `InvokePreLoanProcess.PreLoanProcess.XML` . U kunt deze taak uitvoeren door de volgende code te gebruiken.

```java
 //Create the XML to pass to the FirstAppSolution/PreLoanProcess process
 XmlDocument myXML = CreateXML(userName, phone, amount);
 
 //Convert the XML to a InvokePreLoanProcess.PreLoanProcess.XML instance
 StringWriter sw = new StringWriter();
 XmlTextWriter xw = new XmlTextWriter(sw);
 myXML.WriteTo(xw);
 
 InvokePreLoanProcess.PreLoanProcess.XML inXML = new XML();
 inXML.document = sw.ToString();
```

Als u een ASP-pagina wilt maken die het `FirstAppSolution/PreLoanProcess` -proces oproept, voert u de volgende taken uit in de `Button1_Click` -methode:

1. Maak een `FirstAppSolution_PreLoanProcessClient` -object met de standaardconstructor.
1. Maak een `FirstAppSolution_PreLoanProcessClient.Endpoint.Address` -object met de `System.ServiceModel.EndpointAddress` -constructor. Geef een tekenreekswaarde die de WSDL opgeeft door aan de AEM Forms-service en het coderingstype:

   ```java
    https://hiro-xp:8080/soap/services/FirstAppSolution/PreLoanProcess?blob=mtom
   ```

   U hoeft het attribuut `lc_version` niet te gebruiken. Dit kenmerk wordt gebruikt wanneer u een serviceverwijzing maakt. Zorg er echter voor dat u `?blob=mtom` opgeeft.

   >[!NOTE]
   >
   >Vervang `hiro-xp`* door het IP-adres van de J2EE-toepassingsserver die als host fungeert voor AEM Forms. *

1. Maak een `System.ServiceModel.BasicHttpBinding` -object door de waarde van het `FirstAppSolution_PreLoanProcessClient.Endpoint.Binding` -gegevenslid op te halen. De geretourneerde waarde wordt gecast naar `BasicHttpBinding` .
1. Stel het gegevenslid `MessageEncoding` van het `System.ServiceModel.BasicHttpBinding` -object in op `WSMessageEncoding.Mtom` . Deze waarde zorgt ervoor dat MTOM wordt gebruikt.
1. Laat basisauthentificatie van HTTP door de volgende taken uit te voeren toe:

   * Wijs de gebruikersnaam van het AEM aan het gegevenslid `FirstAppSolution_PreLoanProcessClient.ClientCredentials.UserName.UserName` toe.
   * Wijs de overeenkomstige wachtwoordwaarde toe aan het gegevenslid `FirstAppSolution_PreLoanProcessClient.ClientCredentials.UserName.Password`.
   * Wijs de constante waarde `HttpClientCredentialType.Basic` toe aan het gegevenslid `BasicHttpBindingSecurity.Transport.ClientCredentialType` .
   * Wijs de constante waarde `BasicHttpSecurityMode.TransportCredentialOnly` toe aan het gegevenslid `BasicHttpBindingSecurity.Security.Mode` .

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

1. Haal de naam, de telefoon, en de bedragen op die de gebruiker in de Web-pagina inging. Gebruik deze waarden om dynamisch een XML-gegevensbron te maken die naar het `FirstAppSolution/PreLoanProcess` -proces wordt verzonden. Maak een `System.Xml.XmlDocument` die staat voor de XML-gegevensbron die aan het proces moet worden doorgegeven (deze toepassingslogica wordt in het volgende codevoorbeeld getoond).
1. Zet de instantie `System.Xml.XmlDocument` om in `InvokePreLoanProcess.PreLoanProcess.XML` (deze toepassingslogica wordt getoond in het volgende codevoorbeeld).
1. Roep het `FirstAppSolution/PreLoanProcess` -proces aan door de methode `FirstAppSolution_PreLoanProcessClient` object `invoke_Async` aan te roepen. Deze methode retourneert een tekenreekswaarde die de aanroepende-id-waarde van het langlevende proces vertegenwoordigt.
1. Maak een `JobManagerClient` met behulp van constructor. (Controleer of u een serviceverwijzing hebt ingesteld naar de service Taakbeheer.)
1. Herhaal stap 1-5. Geef de volgende URL op voor stap 2: `https://hiro-xp:8080/soap/services/JobManager?blob=mtom` .
1. Maak een `JobId` -object met behulp van de constructor.
1. Stel het gegevenslid `id` van het `JobId` -object in met de geretourneerde waarde van de methode `FirstAppSolution_PreLoanProcessClient` van het object `invoke_Async` .
1. Wijs `value` true toe aan het gegevenslid van het `JobId` object `persistent` .
1. Maak een `JobStatus` -object door de methode `JobManagerService` object `getStatus` aan te roepen en het object `JobId` door te geven.
1. Haal de statuswaarde op door de waarde van het gegevenslid `statusCode` van het `JobStatus` -object op te halen.
1. Wijs de waarde van de aanroepings-id toe aan het veld `LabelJobID.Text` .
1. Wijs de statuswaarde toe aan het veld `LabelStatus.Text` .

### Snel starten: Een langdurig proces aanroepen met de webservice-API {#quick-start-invoking-a-long-lived-process-using-the-web-service-api}

Het volgende C# codevoorbeeld roept het `FirstAppSolution/PreLoanProcess` proces aan.

```csharp
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

Nadat u de ASP.NET-toepassing hebt gecompileerd en geïmplementeerd, kunt u deze uitvoeren met een webbrowser. Veronderstellend de naam van het ASP.NET project *InvokePreLoanProcess* is, specificeer volgende URL binnen Webbrowser:

*http://localhost:1629/InvokePreLoanProcess/*Default.aspx

waarbij localhost de naam is van de webserver die als host fungeert voor het ASP.NET-project en 1629 het poortnummer. Wanneer u compileert en uw toepassing bouwt ASP.NET, stelt Microsoft Visual Studio automatisch het op.

>[!NOTE]
>
>Als u wilt bevestigen dat de toepassing ASP.NET het proces heeft aangeroepen, start u Workspace en accepteert u de lening.

## Een clienttoepassing maken die is gebouwd met Flex en die een menselijk-centrisch proces van lange duur aanroept {#creating-a-client-application-built-with-flex-that-invokes-a-human-centric-long-lived-process}

U kunt een cliënttoepassing tot stand brengen die met Flex wordt gebouwd om het *FirstAppSolution/PreLoanProcess* proces aan te halen. Deze toepassing gebruikt het Verwijderen om het *FirstAppSolution/PreLoanProcess* proces aan te halen. (Zie [&#x200B; het Aanhalen van AEM Forms die (voor AEM vormen) AEM Forms verwijdert &#x200B;](/help/forms/developing/invoking-aem-forms-using-remoting.md#invoking-aem-forms-using-remoting) gebruikt.)

In de volgende afbeelding ziet u een clienttoepassing die is gebouwd met Flex en die gegevens van een eindgebruiker verzamelt. De gegevens worden in een XML-gegevensbron geplaatst en naar het proces verzonden.

Nadat het proces is aangeroepen, wordt een waarde voor de aanroepings-id weergegeven. Een waarde voor de oproepings-id wordt gemaakt als onderdeel van een record die de status van het proces met een lange levensduur bijhoudt.

De clienttoepassing die met Flex is gebouwd, voert de volgende taken uit:

* Haalt de waarden op die de gebruiker op de webpagina heeft ingevoerd.
* Creeert dynamisch een gegevensbron van XML die tot het *FirstAppSolution/PreLoanProcess* proces wordt overgegaan. De drie waarden worden opgegeven in de XML-gegevensbron.
* Roept het *FirstAppSolution/PreLoanProcess* proces door het Verwijderen te gebruiken aan.
* Retourneert de aanroepings-id-waarde van het langlevende proces.

### Overzicht van de stappen {#summary_of_steps-2}

Voer de volgende stappen uit om een clienttoepassing te maken die met Flex is gebouwd en het proces FirstAppSolution/PreLoanProcess kan aanroepen:

1. Start een nieuw Flex-project.
1. Neem het bestand adobe-remoting-provider.swc op in het klassenpad van uw project. (Zie [&#x200B; Met inbegrip van het de bibliotheekdossier van AEM Forms Flex &#x200B;](/help/forms/developing/invoking-aem-forms-using-remoting.md#including-the-aem-forms-flex-library-file).)
1. Maak een `mx:RemoteObject` -instantie via ActionScript of MXML. (Zie [&#x200B; Creërend mx:instantie RemoteObject &#x200B;](/help/forms/developing/invoking-aem-forms-using-remoting.md))
1. Stel een `ChannelSet` -instantie in om te communiceren met AEM Forms en koppel deze aan de `mx:RemoteObject` -instantie. (Zie [&#x200B; een Kanaal tot AEM Forms &#x200B;](/help/forms/developing/invoking-aem-forms-using-remoting.md) leiden.)
1. Roep de methode `login` van de ChannelSet of de methode `setCredentials` van de service aan om de waarde en het wachtwoord van de gebruikersidentificatie op te geven. (Zie [&#x200B; Gebruikend enig teken-op &#x200B;](/help/forms/developing/invoking-aem-forms-using-remoting.md#using-single-sign-on).)
1. Maak de XML-gegevensbron die u aan het `FirstAppSolution/PreLoanProcess` -proces wilt doorgeven door een XML-instantie te maken. (Deze toepassingslogica wordt getoond in het volgende codevoorbeeld.)
1. Maak een object van het type Object met behulp van de constructor. Wijs XML aan het voorwerp toe door de naam van de de inputparameter van het proces, zoals aangetoond in de volgende code te specificeren:

   ```csharp
    //Get the XML data to pass to the AEM Forms process
    var xml:XML = createXML();
    var params:Object = new Object();
    params["formData"]=xml;
   ```

1. Roep het `FirstAppSolution/PreLoanProcess` -proces aan door de methode `mx:RemoteObject` van de instantie `invoke_Async` aan te roepen. Geef `Object` door die de invoerparameter bevat. (Zie [&#x200B; het overgaan inputwaarden &#x200B;](/help/forms/developing/invoking-aem-forms-using-remoting.md).)
1. Haal de aanroepings-identificatiewaarde op die door een langdurig proces wordt geretourneerd, zoals in de volgende code wordt getoond:

   ```csharp
    // Handles async call that invokes the long-lived process
    private function resultHandler(event:ResultEvent):void
    {
    ji = event.result as JobId;
    jobStatusDisplay.text = "Job Status ID: " + ji.jobId as String;
    }
   ```

### Een langdurig proces aanroepen met Verwijderen {#invoking-a-long-lived-process-using-remoting}

In het volgende Flex-codevoorbeeld wordt het `FirstAppSolution/PreLoanProcess` -proces aangeroepen.

```java
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
