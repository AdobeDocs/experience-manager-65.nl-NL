---
title: Formuliergegevens berekenen
description: Met de Forms-service kunt u waarden berekenen die een gebruiker in een formulier invoert en de resultaten weergeven. De dienst van Forms berekent de waarden gebruikend Java API en de Dienst API van het Web.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/rendering_forms
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: operations
role: Developer
exl-id: 28abf044-6c8e-4578-ae2e-54cdbd694c5f
solution: Experience Manager, Experience Manager Forms
source-git-commit: 872e2de411f51b5f0b26a2ff47cb49f01313d39f
workflow-type: tm+mt
source-wordcount: '1858'
ht-degree: 0%

---

# Formuliergegevens berekenen {#calculating-form-data}

**Voorbeelden en voorbeelden in dit document gelden alleen voor AEM Forms in JEE-omgeving.**

De Forms-service kan de waarden berekenen die een gebruiker in een formulier invoert en de resultaten weergeven. Als u formuliergegevens wilt berekenen, moet u twee taken uitvoeren. Eerst maakt u een formulierontwerpscript waarmee formuliergegevens worden berekend. Een formulierontwerp ondersteunt drie typen scripts. Één manuscripttype loopt op de cliënt, een andere looppas op de server, en het derde type loopt op zowel de server als de cliënt. Het manuscripttype dat in dit onderwerp wordt besproken loopt op de server. Berekeningen aan de serverzijde worden ondersteund voor (afgekeurde) transformaties van HTML, PDF en Form Guide.

Tijdens het ontwerpen van formulieren kunt u berekeningen en scripts gebruiken om gebruikers een rijkere ervaring te bieden. Berekeningen en scripts kunnen aan de meeste formuliervelden en objecten worden toegevoegd. Maak een formulierontwerpscript om rekenbewerkingen uit te voeren op gegevens die een gebruiker in een interactief formulier invoert.

De gebruiker voert waarden in het formulier in en klikt op de knop Berekenen om de resultaten weer te geven. In het volgende proces wordt een voorbeeldtoepassing beschreven waarmee een gebruiker gegevens kan berekenen:

* De gebruiker heeft toegang tot een HTML-pagina met de naam StartLoan.html die fungeert als startpagina van de webtoepassing. Deze pagina roept een Java-server aan met de naam `GetLoanForm`.
* De `GetLoanForm` servlet geeft een leningformulier weer . Dit formulier bevat een script, interactieve velden, een knop Berekenen en een knop Verzenden.
* De gebruiker voert waarden in de velden van het formulier in en klikt op de knop Berekenen. Het formulier wordt verzonden naar de `CalculateData` Java Server waar het script wordt uitgevoerd. Het formulier wordt teruggestuurd naar de gebruiker met de berekeningsresultaten die in het formulier worden weergegeven.
* De gebruiker gaat verder met het invoeren en berekenen van waarden totdat een bevredigend resultaat wordt weergegeven. Als de gebruiker tevreden is, klikt u op de knop Verzenden om het formulier te verwerken. Het formulier wordt verzonden naar een andere Java-server met de naam `ProcessForm` die verantwoordelijk is voor het ophalen van de verzonden gegevens. (Zie [Verzendde Forms afhandelen](/help/forms/developing/rendering-forms.md#handling-submitted-forms).)


Het volgende diagram toont de logische stroom van de toepassing.

![cf_cf_finsrv_loancalcapp_v1](assets/cf_cf_finsrv_loancalcapp_v1.png)

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
   <td><p>De <code>GetLoanForm</code> Java Servlet wordt aangeroepen vanaf de startpagina HTML. </p></td>
  </tr>
  <tr>
   <td><p>2</p></td>
   <td><p>De <code>GetLoanForm</code> Java Servlet gebruikt de Forms Service Client API om het leningformulier te genereren naar de webbrowser van de client. Het verschil tussen het weergeven van een formulier met een script dat is geconfigureerd om op de server te worden uitgevoerd en het weergeven van een formulier dat geen script bevat, is dat u de doellocatie moet opgeven die wordt gebruikt om het script uit te voeren. Als er geen doellocatie is opgegeven, wordt een script dat is geconfigureerd om op de server te worden uitgevoerd, niet uitgevoerd. Neem bijvoorbeeld de toepassing die in deze sectie is geïntroduceerd. De <code>CalculateData</code> Java Servlet is de doellocatie waar het script wordt uitgevoerd.</p></td>
  </tr>
  <tr>
   <td><p>3</p></td>
   <td><p>De gebruiker voert gegevens in interactieve gebieden in en klikt de Calculate knoop. Het formulier wordt verzonden naar de <code>CalculateData</code> Java Server, waar het script wordt uitgevoerd. </p></td>
  </tr>
  <tr>
   <td><p>4</p></td>
   <td><p>Het formulier wordt teruggestuurd naar de webbrowser met de berekeningsresultaten die in het formulier worden weergegeven. </p></td>
  </tr>
  <tr>
   <td><p>5</p></td>
   <td><p>De gebruiker klikt de Submit knoop wanneer de waarden bevredigend zijn. Het formulier wordt verzonden naar een andere Java-server met de naam <code>ProcessForm</code>.</p></td>
  </tr>
 </tbody>
</table>

Een formulier dat als PDF-inhoud wordt verzonden, bevat doorgaans scripts die op de client worden uitgevoerd. Aan de serverzijde kunnen echter ook berekeningen worden uitgevoerd. Een knop Verzenden kan niet worden gebruikt om scripts te berekenen. In deze situatie worden de berekeningen niet uitgevoerd omdat de Forms-service de interactie als voltooid beschouwt.

In deze sectie wordt een eenvoudig interactief formulier met een script dat is geconfigureerd om op de server te worden uitgevoerd, onderzocht om het gebruik van een formulierontwerpscript te illustreren. In het volgende diagram ziet u een formulierontwerp met een script waarmee waarden worden toegevoegd die een gebruiker invoert in de eerste twee velden en het resultaat wordt weergegeven in het derde veld.

![cf_cf_caldata](assets/cf_cf_caldata.png)

**A.** Een veld met de naam NumericField1 **B.** Een veld met de naam NumericField2 **C.** Een veld met de naam NumericField3

De syntaxis van het script in dit formulierontwerp is als volgt:

```javascript
     NumericField3 = NumericField2 + NumericField1
```

In dit formulierontwerp is de knop Berekenen een opdrachtknop en bevindt het script zich in de knoppen `Click` gebeurtenis. Wanneer een gebruiker waarden in de eerste twee velden invoert (NumericField1 en NumericField2) en op de knop Berekenen klikt, wordt het formulier verzonden naar de Forms-service waar het script wordt uitgevoerd. De Forms-service geeft het formulier terug naar het clientapparaat met de resultaten van de berekening die in het veld NumericField3 worden weergegeven.

>[!NOTE]
>
>Zie voor informatie over het maken van een formulierontwerpscript: [Forms Designer](https://www.adobe.com/go/learn_aemforms_designer_63).

>[!NOTE]
>
>Voor meer informatie over de Forms-service raadpleegt u [Services Reference for AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

## Overzicht van de stappen {#summary-of-steps}

Voer de volgende taken uit om formuliergegevens te berekenen:

1. Inclusief projectbestanden.
1. Maak een Forms Client API-object.
1. Hiermee wordt een formulier met een berekeningsscript opgehaald.
1. De formuliergegevensstroom terugschrijven naar de webbrowser van de client

**Projectbestanden opnemen**

Neem de benodigde bestanden op in uw ontwikkelingsproject. Als u een clienttoepassing maakt met Java, neemt u de benodigde JAR-bestanden op. Als u webservices gebruikt, dient u de proxybestanden op te nemen.

**Een Forms Client API-object maken**

Voordat u programmatisch een client-API-bewerking voor Forms-services kunt uitvoeren, moet u een Forms-serviceclient maken. Als u de Java API gebruikt, maakt u een `FormsServiceClient` object. Als u de Forms-webservice-API gebruikt, maakt u een `FormsServiceService` object.

**Een formulier ophalen dat een berekeningsscript bevat**

U gebruikt de Forms Service Client API om toepassingslogica te maken die een formulier afhandelt dat een script bevat dat is geconfigureerd om op de server te worden uitgevoerd. Het proces is vergelijkbaar met het verwerken van een verzonden formulier. (Zie [Verzendde Forms afhandelen](/help/forms/developing/handling-submitted-forms.md).)

Controleren of de verwerkingsstatus die aan het verzonden formulier is gekoppeld, `1` `(Calculate)`, wat betekent dat de Forms-service een berekening uitvoert voor de formuliergegevens en dat de resultaten moeten worden teruggeschreven naar de gebruiker. In deze situatie, wordt een manuscript dat wordt gevormd om op de server in werking te stellen automatisch uitgevoerd.

**De formuliergegevensstroom terugschrijven naar de webbrowser van de client**

Nadat u hebt gecontroleerd of de verwerkingsstatus van een verzonden formulier `1`, moet u de resultaten terugschrijven naar de clientwebbrowser. Wanneer het formulier wordt weergegeven, wordt de berekende waarde weergegeven in het juiste veld of de juiste velden.

**Zie ook**

[Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)
[Formuliergegevens berekenen met de Java API](/help/forms/developing/calculating-form-data.md#calculate-form-data-using-the-java-api)
[Formuliergegevens berekenen met de API voor webservices](/help/forms/developing/calculating-form-data.md#calculate-form-data-using-the-web-service-api)
[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)
[Forms Service API Quick Start](/help/forms/developing/forms-service-api-quick-starts.md#forms-service-api-quick-starts)
[Interactieve PDF forms renderen](/help/forms/developing/rendering-interactive-pdf-forms.md)
[Webtoepassingen maken die Forms renderen](/help/forms/developing/creating-web-applications-renders-forms.md)

## Formuliergegevens berekenen met de Java API {#calculate-form-data-using-the-java-api}

Formuliergegevens berekenen met de Forms API (Java):

1. Projectbestanden opnemen

   Neem client-JAR-bestanden, zoals adobe-forms-client.jar, op in het klassepad van uw Java-project.

1. Een Forms Client API-object maken

   * Een `ServiceClientFactory` object dat verbindingseigenschappen bevat.
   * Een `FormsServiceClient` object door de constructor ervan te gebruiken en de `ServiceClientFactory` object.

1. Een formulier ophalen dat een berekeningsscript bevat

   * Als u formuliergegevens wilt ophalen die een berekeningsscript bevatten, maakt u een `com.adobe.idp.Document` object door de constructor ervan te gebruiken en de `javax.servlet.http.HttpServletResponse` object `getInputStream` methode vanuit de constructor.
   * De `FormsServiceClient` object `processFormSubmission` en geeft de volgende waarden door:

      * De `com.adobe.idp.Document` object dat de formuliergegevens bevat.
      * Een tekenreekswaarde die omgevingsvariabelen opgeeft, inclusief alle relevante HTTP-headers. Geef het inhoudstype op dat u wilt afhandelen door een of meer waarden voor de `CONTENT_TYPE` omgevingsvariabele. Als u bijvoorbeeld XML- en PDF-gegevens wilt verwerken, geeft u de volgende tekenreekswaarde op voor deze parameter: `CONTENT_TYPE=application/xml&CONTENT_TYPE=application/pdf`
      * Een tekenreekswaarde die de `HTTP_USER_AGENT` koptekstwaarde, bijvoorbeeld `Mozilla/4.0 (compatible; MSIE 6.0; Windows NT 5.1; SV1; .NET CLR 1.1.4322)`.
      * A `RenderOptionsSpec` -object dat uitvoeringsopties opslaat.

     De `processFormSubmission` methode retourneert een `FormsResult` object met de resultaten van het verzenden van het formulier.

   * Controleren of de verwerkingsstatus van een verzonden formulier `1` door de `FormsResult` object `getAction` methode. Als deze methode de waarde retourneert `1`, is de berekening uitgevoerd en kunnen de gegevens worden teruggeschreven naar de webbrowser van de client.

1. De formuliergegevensstroom terugschrijven naar de webbrowser van de client

   * Een `javax.servlet.ServletOutputStream` object dat wordt gebruikt om een formuliergegevensstroom naar de webbrowser van de client te verzenden.
   * Een `com.adobe.idp.Document` door het object aan te roepen `FormsResult` object `getOutputContent` methode.
   * Een `java.io.InputStream` door het object aan te roepen `com.adobe.idp.Document` object `getInputStream` methode.
   * Maak een bytearray en vul deze met de formuliergegevensstroom door de `InputStream` object `read` en de bytearray doorgeven als een argument.
   * De `javax.servlet.ServletOutputStream` object `write` methode om de formuliergegevensstroom naar de webbrowser van de client te verzenden. Geef de bytearray door aan de `write` methode.

**Zie ook**


[Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)
[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

## Formuliergegevens berekenen met de API voor webservices {#calculate-form-data-using-the-web-service-api}

Formuliergegevens berekenen met de Forms API (webservice):

1. Projectbestanden opnemen

   * Maak Java-proxyklassen die gebruikmaken van de Forms-service WSDL.
   * Neem de Java-proxyklassen op in het klassepad.

1. Een Forms Client API-object maken

   Een `FormsService` -object en stel verificatiewaarden in.

1. Een formulier ophalen dat een berekeningsscript bevat

   * Als u formuliergegevens wilt ophalen die naar een Java Server zijn gepost, maakt u een `BLOB` object met behulp van de constructor.
   * Een `java.io.InputStream` object door het `javax.servlet.http.HttpServletResponse` object `getInputStream` methode.
   * Een `java.io.ByteArrayOutputStream` object door de constructor ervan te gebruiken en de lengte van het object door te geven `java.io.InputStream` object.
   * Kopieer de inhoud van het dialoogvenster `java.io.InputStream` in het `java.io.ByteArrayOutputStream` object.
   * Maak een bytearray door de `java.io.ByteArrayOutputStream` object `toByteArray` methode.
   * Vul de `BLOB` object aanroepen `setBinaryData` en de bytearray doorgeven als een argument.
   * Een `RenderOptionsSpec` object met behulp van de constructor. Stel de waarde van de landinstelling in door de `RenderOptionsSpec` object `setLocale` en het doorgeven van een tekenreekswaarde die de waarde van de landinstelling opgeeft.
   * De `FormsServiceClient` object `processFormSubmission` en geeft de volgende waarden door:

      * De `BLOB` object dat de formuliergegevens bevat.
      * Een tekenreekswaarde die omgevingsvariabelen opgeeft die alle relevante HTTP-headers bevatten. U kunt bijvoorbeeld de volgende tekenreekswaarde opgeven: `HTTP_REFERER=referrer&HTTP_CONNECTION=keep-alive&CONTENT_TYPE=application/xml`
      * Een tekenreekswaarde die de `HTTP_USER_AGENT` koptekstwaarde, bijvoorbeeld `Mozilla/4.0 (compatible; MSIE 6.0; Windows NT 5.1; SV1; .NET CLR 1.1.4322)`.
      * A `RenderOptionsSpec` -object dat uitvoeringsopties opslaat. Voor meer informatie, .
      * Een leeg `BLOBHolder` object dat door de methode wordt gevuld.
      * Een leeg `javax.xml.rpc.holders.StringHolder` object dat door de methode wordt gevuld.
      * Een leeg `BLOBHolder` object dat door de methode wordt gevuld.
      * Een leeg `BLOBHolder` object dat door de methode wordt gevuld.
      * Een leeg `javax.xml.rpc.holders.ShortHolder` object dat door de methode wordt gevuld.
      * Een leeg `MyArrayOf_xsd_anyTypeHolder` object dat door de methode wordt gevuld. Met deze parameter worden bestandsbijlagen opgeslagen die samen met het formulier worden verzonden.
      * Een leeg `FormsResultHolder` object dat door de methode is gevuld met het formulier dat wordt verzonden.

     De `processFormSubmission` wordt de `FormsResultHolder` met de resultaten van het verzenden van het formulier. De `processFormSubmission` methode retourneert een `FormsResult` object met de resultaten van het verzenden van het formulier.

   * Controleren of de verwerkingsstatus van een verzonden formulier `1` door de `FormsResult` object `getAction` methode. Als deze methode de waarde retourneert `1`, is de berekening uitgevoerd en kunnen de gegevens worden teruggeschreven naar de webbrowser van de client.

1. De formuliergegevensstroom terugschrijven naar de webbrowser van de client

   * Een `javax.servlet.ServletOutputStream` object dat wordt gebruikt om een formuliergegevensstroom naar de webbrowser van de client te verzenden.
   * Een `BLOB` object dat formuliergegevens bevat door het `FormsResult` object `getOutputContent` methode.
   * Maak een bytearray en vul deze door het `BLOB` object `getBinaryData` methode. Deze taak wijst de inhoud van toe `FormsResult` object naar de bytearray.
   * De `javax.servlet.http.HttpServletResponse` object `write` methode om de formuliergegevensstroom naar de webbrowser van de client te verzenden. Geef de bytearray door aan de `write` methode.

**Zie ook**
[AEM Forms aanroepen met Base64-codering](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-base64-encoding)
