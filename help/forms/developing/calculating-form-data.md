---
title: Formuliergegevens berekenen
seo-title: Formuliergegevens berekenen
description: Gebruik de Forms-service om waarden te berekenen die een gebruiker in een formulier invoert en de resultaten weer te geven. De dienst van Forms berekent de waarden gebruikend Java API en de Dienst API van het Web.
seo-description: Gebruik de Forms-service om waarden te berekenen die een gebruiker in een formulier invoert en de resultaten weer te geven. De dienst van Forms berekent de waarden gebruikend Java API en de Dienst API van het Web.
uuid: ccd85bc7-8ccc-44d9-9424-dfc1f603e688
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/rendering_forms
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: operations
discoiquuid: b4f57e42-60a6-407d-9764-15a11615827d
translation-type: tm+mt
source-git-commit: 9cf46a26d2aa2e41b924a4de89cf8ab5fdeeefc6
workflow-type: tm+mt
source-wordcount: '1916'
ht-degree: 0%

---


# Formuliergegevens berekenen {#calculating-form-data}

**Voorbeelden en voorbeelden in dit document gelden alleen voor AEM Forms in JEE-omgeving.**

De Forms-service kan de waarden berekenen die een gebruiker in een formulier invoert en de resultaten weergeven. Als u formuliergegevens wilt berekenen, moet u twee taken uitvoeren. Eerst maakt u een formulierontwerpscript waarmee formuliergegevens worden berekend. Een formulierontwerp ondersteunt drie typen scripts. Één manuscripttype loopt op de cliënt, een andere looppas op de server, en het derde type loopt op zowel de server als de cliënt. Het manuscripttype dat in dit onderwerp wordt besproken loopt op de server. Berekeningen aan de serverzijde worden ondersteund voor transformaties in HTML, PDF en de formulierhulplijn (afgekeurd).

Tijdens het ontwerpen van formulieren kunt u berekeningen en scripts gebruiken om gebruikers een rijkere ervaring te bieden. Berekeningen en scripts kunnen aan de meeste formuliervelden en objecten worden toegevoegd. U moet een formulierontwerpscript maken om rekenbewerkingen uit te voeren op gegevens die een gebruiker in een interactief formulier invoert.

De gebruiker voert waarden in het formulier in en klikt op de knop Berekenen om de resultaten weer te geven. In het volgende proces wordt een voorbeeldtoepassing beschreven waarmee een gebruiker gegevens kan berekenen:

* De gebruiker heeft toegang tot een HTML-pagina met de naam StartLoan.html die fungeert als startpagina van de webtoepassing. Deze pagina roept een Java Server genoemd `GetLoanForm` aan.
* Met de servlet `GetLoanForm` wordt een leningformulier gegenereerd. Dit formulier bevat een script, interactieve velden, een knop Berekenen en een knop Verzenden.
* De gebruiker voert waarden in de velden van het formulier in en klikt op de knop Berekenen. Het formulier wordt verzonden naar de Java Server `CalculateData` waar het script wordt uitgevoerd. Het formulier wordt teruggestuurd naar de gebruiker met de berekeningsresultaten die in het formulier worden weergegeven.
* De gebruiker gaat verder met het invoeren en berekenen van waarden totdat een bevredigend resultaat wordt weergegeven. Als de gebruiker tevreden is, klikt u op de knop Verzenden om het formulier te verwerken. Het formulier wordt verzonden naar een andere Java-server met de naam `ProcessForm` die verantwoordelijk is voor het ophalen van verzonden gegevens. (Zie [Ingediende Forms verwerken](/help/forms/developing/rendering-forms.md#handling-submitted-forms).)


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
   <td><p>De Java Server <code>GetLoanForm</code> wordt aangeroepen vanaf de HTML-startpagina. </p></td>
  </tr>
  <tr>
   <td><p>2</p></td>
   <td><p>De Java Server <code>GetLoanForm</code> gebruikt de Forms Service Client API om het leningformulier te genereren naar de clientwebbrowser. Het verschil tussen het weergeven van een formulier met een script dat is geconfigureerd om op de server te worden uitgevoerd en het weergeven van een formulier dat geen script bevat, is dat u de doellocatie moet opgeven die wordt gebruikt om het script uit te voeren. Als geen doellocatie is opgegeven, wordt een script dat is geconfigureerd om op de server te worden uitgevoerd, niet uitgevoerd. Neem bijvoorbeeld de toepassing die in deze sectie is geïntroduceerd. De <code>CalculateData</code> Java Server is de doellocatie waar het script wordt uitgevoerd.</p></td>
  </tr>
  <tr>
   <td><p>3</p></td>
   <td><p>De gebruiker voert gegevens in interactieve gebieden in en klikt de Calculate knoop. Het formulier wordt verzonden naar de Java Server <code>CalculateData</code>, waar het script wordt uitgevoerd. </p></td>
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

**A.** Een veld genaamd NumericField1  **B.** A veld genaamd NumericField2  **C.** A veld genaamd NumericField3

De syntaxis van het script in dit formulierontwerp is als volgt:

```javascript
     NumericField3 = NumericField2 + NumericField1
```

In dit formulierontwerp is de knop Berekenen een opdrachtknop en bevindt het script zich in de gebeurtenis `Click` van deze knop. Wanneer een gebruiker waarden in de eerste twee velden invoert (NumericField1 en NumericField2) en op de knop Berekenen klikt, wordt het formulier verzonden naar de Forms-service waar het script wordt uitgevoerd. De Forms-service geeft het formulier terug naar het clientapparaat met de resultaten van de berekening die in het veld NumericField3 worden weergegeven.

>[!NOTE]
>
>Zie [Forms Designer](https://www.adobe.com/go/learn_aemforms_designer_63) voor informatie over het maken van een formulierontwerpscript.

>[!NOTE]
>
>Zie [Referentiehandleiding voor services voor AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63) voor meer informatie over de Forms-service.

## Overzicht van stappen {#summary-of-steps}

Voer de volgende taken uit om formuliergegevens te berekenen:

1. Inclusief projectbestanden.
1. Maak een Forms Client API-object.
1. Hiermee wordt een formulier met een berekeningsscript opgehaald.
1. De formuliergegevensstroom terugschrijven naar de webbrowser van de client

**Projectbestanden opnemen**

Neem de benodigde bestanden op in uw ontwikkelingsproject. Als u een clienttoepassing maakt met Java, neemt u de benodigde JAR-bestanden op. Als u webservices gebruikt, dient u de proxybestanden op te nemen.

**Een Forms Client API-object maken**

Voordat u programmatisch een client-API-bewerking voor Forms-services kunt uitvoeren, moet u een Forms-serviceclient maken. Als u de Java API gebruikt, maakt u een `FormsServiceClient`-object. Als u de Forms-API voor webservices gebruikt, maakt u een `FormsServiceService`-object.

**Een formulier ophalen dat een berekeningsscript bevat**

U gebruikt de Forms Service Client API om toepassingslogica te maken die een formulier afhandelt dat een script bevat dat is geconfigureerd om op de server te worden uitgevoerd. Het proces is vergelijkbaar met het verwerken van een verzonden formulier. (Zie [Ingediende Forms verwerken](/help/forms/developing/handling-submitted-forms.md).)

Controleer of de verwerkingsstatus van het verzonden formulier `1` `(Calculate)` is. Dit betekent dat de Forms-service een rekenbewerking uitvoert op de formuliergegevens en dat de resultaten moeten worden teruggeschreven naar de gebruiker. In deze situatie, wordt een manuscript dat wordt gevormd om op de server in werking te stellen automatisch uitgevoerd.

**De formuliergegevensstroom terugschrijven naar de webbrowser van de client**

Nadat u hebt gecontroleerd dat de verwerkingsstatus van een verzonden formulier `1` is, moet u de resultaten terugschrijven naar de webbrowser van de client. Wanneer het formulier wordt weergegeven, wordt de berekende waarde weergegeven in het (de) desbetreffende veld(en).

**Zie ook**

[Inclusief AEM Forms Java-](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)
[bibliotheekbestandenFormuliergegevens berekenen met de Java ](/help/forms/developing/calculating-form-data.md#calculate-form-data-using-the-java-api)
[APICalculate-formuliergegevens met behulp van de ](/help/forms/developing/calculating-form-data.md#calculate-form-data-using-the-web-service-api)
[APISetting-](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)
[verbindingseigenschappenForms Service API Quick ](/help/forms/developing/forms-service-api-quick-starts.md#forms-service-api-quick-starts)
[StartsRendering Interactive PDF ](/help/forms/developing/rendering-interactive-pdf-forms.md)
[FormsCreating webtoepassingen die Forms renderen](/help/forms/developing/creating-web-applications-renders-forms.md)

## Formuliergegevens berekenen met de Java API {#calculate-form-data-using-the-java-api}

Formuliergegevens berekenen met de Forms API (Java):

1. Projectbestanden opnemen

   Neem client-JAR-bestanden, zoals adobe-forms-client.jar, op in het klassenpad van uw Java-project.

1. Een Forms Client API-object maken

   * Maak een `ServiceClientFactory`-object dat verbindingseigenschappen bevat.
   * Maak een `FormsServiceClient`-object door de constructor ervan te gebruiken en het object `ServiceClientFactory` door te geven.

1. Een formulier ophalen dat een berekeningsscript bevat

   * Als u formuliergegevens wilt ophalen die een berekeningsscript bevatten, maakt u een `com.adobe.idp.Document`-object met de constructor ervan en roept u de methode `javax.servlet.http.HttpServletResponse` van het object `getInputStream` vanuit de constructor aan.
   * Roep de methode `processFormSubmission` van het object `FormsServiceClient` aan en geef de volgende waarden door:

      * Het object `com.adobe.idp.Document` dat de formuliergegevens bevat.
      * Een tekenreekswaarde die omgevingsvariabelen opgeeft, inclusief alle relevante HTTP-headers. U moet het inhoudstype specificeren om te behandelen door één of meerdere waarden voor `CONTENT_TYPE` omgevingsvariabele te specificeren. Als u bijvoorbeeld XML- en PDF-gegevens wilt verwerken, geeft u de volgende tekenreekswaarde op voor deze parameter: `CONTENT_TYPE=application/xml&CONTENT_TYPE=application/pdf`
      * Een tekenreekswaarde die de koptekstwaarde `HTTP_USER_AGENT` opgeeft; bijvoorbeeld `Mozilla/4.0 (compatible; MSIE 6.0; Windows NT 5.1; SV1; .NET CLR 1.1.4322)`.
      * Een `RenderOptionsSpec`-object dat uitvoeringsopties opslaat.

      De methode `processFormSubmission` retourneert een `FormsResult`-object dat de resultaten van het verzenden van het formulier bevat.

   * Controleer of de verwerkingsstatus die is gekoppeld aan een verzonden formulier `1` is door de methode `getAction` van het object `FormsResult` aan te roepen. Als deze methode de waarde `1` retourneert, is de berekening uitgevoerd en kunnen de gegevens naar de webbrowser van de client worden geschreven.


1. De formuliergegevensstroom terugschrijven naar de webbrowser van de client

   * Maak een `javax.servlet.ServletOutputStream`-object dat wordt gebruikt om een formuliergegevensstroom naar de webbrowser van de client te verzenden.
   * Maak een `com.adobe.idp.Document`-object door de methode `getOutputContent` van het object aan te roepen.`FormsResult`
   * Maak een `java.io.InputStream`-object door de methode `getInputStream` van het object `com.adobe.idp.Document` aan te roepen.
   * Maak een bytearray en vul deze met de formuliergegevensstroom door de methode `read` van het object `InputStream` aan te roepen en de bytearray als een argument door te geven.
   * Roep de methode `javax.servlet.ServletOutputStream` van het object `write` aan om de gegevensstroom van het formulier naar de webbrowser van de client te verzenden. Geef de bytearray door aan de methode `write`.

**Zie ook**


[Inclusief AEM Forms Java-bibliotheekbestandenVerbindingseigenschappen ](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)
[instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

## Formuliergegevens berekenen met de API {#calculate-form-data-using-the-web-service-api} van de webservice

Formuliergegevens berekenen met de Forms API (webservice):

1. Projectbestanden opnemen

   * Maak Java-proxyklassen die gebruikmaken van de Forms-service WSDL.
   * Neem de Java-proxyklassen op in het klassepad.

1. Een Forms Client API-object maken

   Maak een `FormsService`-object en stel de verificatiewaarden in.

1. Een formulier ophalen dat een berekeningsscript bevat

   * Als u formuliergegevens wilt ophalen die naar een Java Server zijn gepost, maakt u een `BLOB`-object met de bijbehorende constructor.
   * Maak een `java.io.InputStream`-object met de methode `getInputStream` van het object.`javax.servlet.http.HttpServletResponse`
   * Maak een `java.io.ByteArrayOutputStream`-object door de constructor ervan te gebruiken en de lengte van het object `java.io.InputStream` door te geven.
   * Kopieer de inhoud van het object `java.io.InputStream` naar het object `java.io.ByteArrayOutputStream`.
   * Maak een bytearray door de methode `toByteArray` van het object `java.io.ByteArrayOutputStream` aan te roepen.
   * Vul het object `BLOB` door de methode `setBinaryData` ervan aan te roepen en de bytearray als een argument door te geven.
   * Maak een `RenderOptionsSpec`-object met de constructor ervan. Stel de waarde van de landinstelling in door de methode `setLocale` van het object `RenderOptionsSpec` aan te roepen en een tekenreekswaarde door te geven die de waarde van de landinstelling opgeeft.
   * Roep de methode `processFormSubmission` van het object `FormsServiceClient` aan en geef de volgende waarden door:

      * Het object `BLOB` dat de formuliergegevens bevat.
      * Een tekenreekswaarde die omgevingsvariabelen opgeeft die alle relevante HTTP-headers bevatten. U kunt bijvoorbeeld de volgende tekenreekswaarde opgeven: `HTTP_REFERER=referrer&HTTP_CONNECTION=keep-alive&CONTENT_TYPE=application/xml`
      * Een tekenreekswaarde die de koptekstwaarde `HTTP_USER_AGENT` opgeeft; bijvoorbeeld `Mozilla/4.0 (compatible; MSIE 6.0; Windows NT 5.1; SV1; .NET CLR 1.1.4322)`.
      * Een `RenderOptionsSpec`-object dat uitvoeringsopties opslaat. Voor meer informatie, .
      * Een leeg object `BLOBHolder` dat door de methode is gevuld.
      * Een leeg object `javax.xml.rpc.holders.StringHolder` dat door de methode is gevuld.
      * Een leeg object `BLOBHolder` dat door de methode is gevuld.
      * Een leeg object `BLOBHolder` dat door de methode is gevuld.
      * Een leeg object `javax.xml.rpc.holders.ShortHolder` dat door de methode is gevuld.
      * Een leeg object `MyArrayOf_xsd_anyTypeHolder` dat door de methode is gevuld. Met deze parameter worden bestandsbijlagen opgeslagen die samen met het formulier worden verzonden.
      * Een leeg `FormsResultHolder`-object dat door de methode wordt gevuld met het formulier dat wordt verzonden.

      Met de methode `processFormSubmission` wordt de parameter `FormsResultHolder` gevuld met de resultaten van het verzenden van het formulier. De methode `processFormSubmission` retourneert een `FormsResult`-object dat de resultaten van het verzenden van het formulier bevat.

   * Controleer of de verwerkingsstatus die is gekoppeld aan een verzonden formulier `1` is door de methode `getAction` van het object `FormsResult` aan te roepen. Als deze methode de waarde `1` retourneert, is de berekening uitgevoerd en kunnen de gegevens naar de webbrowser van de client worden geschreven.


1. De formuliergegevensstroom terugschrijven naar de webbrowser van de client

   * Maak een `javax.servlet.ServletOutputStream`-object dat wordt gebruikt om een formuliergegevensstroom naar de webbrowser van de client te verzenden.
   * Maak een `BLOB`-object dat formuliergegevens bevat door de methode `getOutputContent` van het object `FormsResult` aan te roepen.
   * Maak een bytearray en vul deze door de methode `getBinaryData` van het object `BLOB` aan te roepen. Deze taak wijst de inhoud van het `FormsResult` voorwerp aan de byteserie toe.
   * Roep de methode `javax.servlet.http.HttpServletResponse` van het object `write` aan om de gegevensstroom van het formulier naar de webbrowser van de client te verzenden. Geef de bytearray door aan de methode `write`.

**Zie**
[ook AEM Forms aanroepen met Base64-codering](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-base64-encoding)
