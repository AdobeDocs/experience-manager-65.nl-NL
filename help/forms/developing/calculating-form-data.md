---
title: Formuliergegevens berekenen
seo-title: Formuliergegevens berekenen
description: 'null'
seo-description: 'null'
uuid: ccd85bc7-8ccc-44d9-9424-dfc1f603e688
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/rendering_forms
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: operations
discoiquuid: b4f57e42-60a6-407d-9764-15a11615827d
translation-type: tm+mt
source-git-commit: 2e4b8ee13257758cba6b76012fed4958f7eabbd7

---


# Formuliergegevens berekenen {#calculating-form-data}

De service Forms kan de waarden berekenen die een gebruiker in een formulier invoert en de resultaten weergeven. Als u formuliergegevens wilt berekenen, moet u twee taken uitvoeren. Eerst maakt u een formulierontwerpscript waarmee formuliergegevens worden berekend. Een formulierontwerp ondersteunt drie typen scripts. Één manuscripttype loopt op de cliënt, een andere looppas op de server, en het derde type loopt op zowel de server als de cliënt. Het manuscripttype dat in dit onderwerp wordt besproken loopt op de server. Berekeningen aan de serverzijde worden ondersteund voor transformaties in HTML, PDF en de formulierhulplijn (afgekeurd).

Tijdens het ontwerpen van formulieren kunt u berekeningen en scripts gebruiken om gebruikers een rijkere ervaring te bieden. Berekeningen en scripts kunnen aan de meeste formuliervelden en objecten worden toegevoegd. U moet een formulierontwerpscript maken om rekenbewerkingen uit te voeren op gegevens die een gebruiker in een interactief formulier invoert.

De gebruiker voert waarden in het formulier in en klikt op de knop Berekenen om de resultaten weer te geven. In het volgende proces wordt een voorbeeldtoepassing beschreven waarmee een gebruiker gegevens kan berekenen:

* De gebruiker heeft toegang tot een HTML-pagina met de naam StartLoan.html die fungeert als startpagina van de webtoepassing. Deze pagina roept een Java-server met de naam `GetLoanForm`.
* De `GetLoanForm` servlet geeft een leningsformulier weer. Dit formulier bevat een script, interactieve velden, een knop Berekenen en een knop Verzenden.
* De gebruiker voert waarden in de velden van het formulier in en klikt op de knop Berekenen. Het formulier wordt verzonden naar de `CalculateData` Java-server waar het script wordt uitgevoerd. Het formulier wordt teruggestuurd naar de gebruiker met de berekeningsresultaten die in het formulier worden weergegeven.
* De gebruiker gaat verder met het invoeren en berekenen van waarden totdat een bevredigend resultaat wordt weergegeven. Als de gebruiker tevreden is, klikt u op de knop Verzenden om het formulier te verwerken. Het formulier wordt verzonden naar een andere Java-server met de naam `ProcessForm` die verantwoordelijk is voor het ophalen van verzonden gegevens. (Zie [Verstuurde formulieren](/help/forms/developing/rendering-forms.md#handling-submitted-forms)verwerken.)


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
   <td><p>De <code>GetLoanForm</code> Java Server wordt aangeroepen vanaf de HTML-startpagina. </p></td>
  </tr>
  <tr>
   <td><p>2</p></td>
   <td><p>De <code>GetLoanForm</code> Java Server gebruikt de API van de de dienstcliënt van de Dienst van Vormen om het leningsformulier aan cliëntbrowser terug te geven. Het verschil tussen het weergeven van een formulier met een script dat is geconfigureerd om op de server te worden uitgevoerd en het weergeven van een formulier dat geen script bevat, is dat u de doellocatie moet opgeven die wordt gebruikt om het script uit te voeren. Als geen doellocatie is opgegeven, wordt een script dat is geconfigureerd om op de server te worden uitgevoerd, niet uitgevoerd. Neem bijvoorbeeld de toepassing die in deze sectie is geïntroduceerd. De <code>CalculateData</code> Java Server is de doellocatie waar het script wordt uitgevoerd.</p></td>
  </tr>
  <tr>
   <td><p>3</p></td>
   <td><p>De gebruiker voert gegevens in interactieve gebieden in en klikt de Calculate knoop. Het formulier wordt verzonden naar de <code>CalculateData</code> Java Server waar het script wordt uitgevoerd. </p></td>
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

Een formulier dat als PDF-inhoud wordt verzonden, bevat doorgaans scripts die op de client worden uitgevoerd. Aan de serverzijde kunnen echter ook berekeningen worden uitgevoerd. Een knop Verzenden kan niet worden gebruikt om scripts te berekenen. In dit geval worden berekeningen niet uitgevoerd omdat de service Forms de interactie als voltooid beschouwt.

In deze sectie wordt een eenvoudig interactief formulier met een script dat is geconfigureerd om op de server te worden uitgevoerd, onderzocht om het gebruik van een formulierontwerpscript te illustreren. In het volgende diagram ziet u een formulierontwerp met een script waarmee waarden worden toegevoegd die een gebruiker invoert in de eerste twee velden en het resultaat wordt weergegeven in het derde veld.

![cf_cf_caldata](assets/cf_cf_caldata.png)

**A.** Een veld met de naam NumericField1 **B.** Een veld met de naam NumericField2 **C.** Een veld met de naam NumericField3

De syntaxis van het script in dit formulierontwerp is als volgt:

```as3
     NumericField3 = NumericField2 + NumericField1
```

In dit formulierontwerp is de knop Berekenen een opdrachtknop en bevindt het script zich in de `Click` gebeurtenis van deze knop. Wanneer een gebruiker waarden invoert in de eerste twee velden (NumericField1 en NumericField2) en op de knop Berekenen klikt, wordt het formulier verzonden naar de service Forms, waar het script wordt uitgevoerd. De service Forms geeft het formulier terug naar het clientapparaat met de resultaten van de berekening die in het veld NumericField3 wordt weergegeven.

>[!NOTE]
>
>Zie [Formulierontwerper](https://www.adobe.com/go/learn_aemforms_designer_63)voor informatie over het maken van een formulierontwerpscript.

>[!NOTE]
>
>Voor meer informatie over de dienst van Vormen, zie de Verwijzing van de [Diensten voor Vormen](https://www.adobe.com/go/learn_aemforms_services_63)AEM.

## Overzicht van de stappen {#summary-of-steps}

Voer de volgende taken uit om formuliergegevens te berekenen:

1. Inclusief projectbestanden.
1. Maak een Forms Client API-object.
1. Hiermee wordt een formulier met een berekeningsscript opgehaald.
1. De formuliergegevensstroom terugschrijven naar de webbrowser van de client

**Projectbestanden opnemen**

Neem de benodigde bestanden op in uw ontwikkelingsproject. Als u een clienttoepassing maakt met Java, neemt u de benodigde JAR-bestanden op. Als u webservices gebruikt, dient u de proxybestanden op te nemen.

**Een Forms Client API-object maken**

Voordat u een API-bewerking voor Forms-service programmatisch kunt uitvoeren, moet u een Forms-service-client maken. Als u de Java API gebruikt, maakt u een `FormsServiceClient` object. Als u de API voor webservices van Forms gebruikt, maakt u een `FormsServiceService` object.

**Een formulier ophalen dat een berekeningsscript bevat**

Met de API voor Forms Service Client kunt u toepassingslogica maken die een formulier afhandelt dat een script bevat dat is geconfigureerd om op de server te worden uitgevoerd. Het proces is vergelijkbaar met het verwerken van een verzonden formulier. (Zie [Verstuurde formulieren](/help/forms/developing/handling-submitted-forms.md)verwerken.)

Controleer of de verwerkingsstatus van het verzonden formulier `1` `(Calculate)`correct is. Dit betekent dat de service Forms een berekening uitvoert voor de formuliergegevens en dat de resultaten naar de gebruiker moeten worden teruggeschreven. In deze situatie, wordt een manuscript dat wordt gevormd om op de server in werking te stellen automatisch uitgevoerd.

**De formuliergegevensstroom terugschrijven naar de webbrowser van de client**

Nadat u hebt gecontroleerd welke verwerkingsstatus aan een verzonden formulier is gekoppeld, moet u de resultaten terugschrijven naar de webbrowser van de client. `1` Wanneer het formulier wordt weergegeven, wordt de berekende waarde weergegeven in het (de) desbetreffende veld(en).

**Zie ook**

[Met inbegrip van AEM-formulieren Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)[Formuliergegevens berekenen met de Java API](/help/forms/developing/calculating-form-data.md#calculate-form-data-using-the-java-api)[Formuliergegevens berekenen met behulp van de webservice API](/help/forms/developing/calculating-form-data.md#calculate-form-data-using-the-web-service-api)[Verbindingseigenschappen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)[Formulierservice-API Snelle start](/help/forms/developing/forms-service-api-quick-starts.md#forms-service-api-quick-starts)[](/help/forms/developing/rendering-interactive-pdf-forms.md)[Interactieve PDF-formulierenRenderingCreëren van webtoepassingen die formulieren genereren](/help/forms/developing/creating-web-applications-renders-forms.md)

## Formuliergegevens berekenen met de Java API {#calculate-form-data-using-the-java-api}

Formuliergegevens berekenen met de API voor formulieren (Java):

1. Projectbestanden opnemen

   Neem client-JAR-bestanden, zoals adobe-forms-client.jar, op in het klassenpad van uw Java-project.

1. Een Forms Client API-object maken

   * Maak een `ServiceClientFactory` object dat verbindingseigenschappen bevat.
   * Maak een `FormsServiceClient` object door de constructor ervan te gebruiken en het `ServiceClientFactory` object door te geven.

1. Een formulier ophalen dat een berekeningsscript bevat

   * Als u formuliergegevens wilt ophalen die een berekeningsscript bevatten, maakt u een `com.adobe.idp.Document` object met behulp van de constructor van het object en roept u de `javax.servlet.http.HttpServletResponse` `getInputStream` methode van het object aan vanuit de constructor.
   * Roep de methode van het `FormsServiceClient` `processFormSubmission` object aan en geef de volgende waarden door:

      * Het `com.adobe.idp.Document` object dat de formuliergegevens bevat.
      * Een tekenreekswaarde die omgevingsvariabelen opgeeft, inclusief alle relevante HTTP-headers. U moet het inhoudstype specificeren om te behandelen door één of meerdere waarden voor de `CONTENT_TYPE` omgevingsvariabele te specificeren. Als u bijvoorbeeld XML- en PDF-gegevens wilt verwerken, geeft u de volgende tekenreekswaarde op voor deze parameter: `CONTENT_TYPE=application/xml&CONTENT_TYPE=application/pdf`
      * Een tekenreekswaarde die de `HTTP_USER_AGENT` koptekstwaarde opgeeft; bijvoorbeeld `Mozilla/4.0 (compatible; MSIE 6.0; Windows NT 5.1; SV1; .NET CLR 1.1.4322)`.
      * Een `RenderOptionsSpec` object dat uitvoeringsopties opslaat.
      De `processFormSubmission` methode retourneert een `FormsResult` object dat de resultaten van het verzenden van het formulier bevat.

   * Controleer of de verwerkingsstatus die aan een verzonden formulier is gekoppeld, `1` door de `FormsResult` methode van het `getAction` object aan te roepen. Als deze methode de waarde retourneert `1`, is de berekening uitgevoerd en kunnen de gegevens worden teruggeschreven naar de webbrowser van de client.


1. De formuliergegevensstroom terugschrijven naar de webbrowser van de client

   * Maak een `javax.servlet.ServletOutputStream` object dat wordt gebruikt om een formuliergegevensstroom naar de webbrowser van de client te verzenden.
   * Maak een `com.adobe.idp.Document` object door de `FormsResult` methode van het `getOutputContent` object aan te roepen.
   * Maak een `java.io.InputStream` object door de `com.adobe.idp.Document` methode van het `getInputStream` object aan te roepen.
   * Maak een bytearray en vul deze met de formuliergegevensstroom door de methode van het `InputStream` `read` object aan te roepen en de bytearray als een argument door te geven.
   * Roep de `javax.servlet.ServletOutputStream` methode van het `write` object aan om de formuliergegevensstroom naar de webbrowser van de client te verzenden. Geef de bytearray door aan de `write` methode.

**Zie ook**


[Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

## Formuliergegevens berekenen met de API voor webservices {#calculate-form-data-using-the-web-service-api}

Formuliergegevens berekenen met de API voor formulieren (webservice):

1. Projectbestanden opnemen

   * Maak Java-proxyklassen die de Forms service WSDL gebruiken.
   * Neem de Java-proxyklassen op in het klassepad.

1. Een Forms Client API-object maken

   Maak een `FormsService` object en stel verificatiewaarden in.

1. Een formulier ophalen dat een berekeningsscript bevat

   * Als u formuliergegevens wilt ophalen die naar een Java Server zijn gepost, maakt u een `BLOB` object met de constructor ervan.
   * Maak een `java.io.InputStream` object met de `javax.servlet.http.HttpServletResponse` methode van het `getInputStream` object.
   * Maak een `java.io.ByteArrayOutputStream` object door de constructor ervan te gebruiken en de lengte van het `java.io.InputStream` object door te geven.
   * Kopieer de inhoud van het `java.io.InputStream` object naar het `java.io.ByteArrayOutputStream` object.
   * Maak een bytearray door de `java.io.ByteArrayOutputStream` methode van het `toByteArray` object aan te roepen.
   * Vul het `BLOB` `setBinaryData` object door de methode ervan aan te roepen en de bytearray als een argument door te geven.
   * Maak een `RenderOptionsSpec` object met de constructor ervan. Stel de waarde van de landinstelling in door de methode van het `RenderOptionsSpec` `setLocale` object aan te roepen en een tekenreekswaarde door te geven die de waarde van de landinstelling opgeeft.
   * Roep de methode van het `FormsServiceClient` `processFormSubmission` object aan en geef de volgende waarden door:

      * Het `BLOB` object dat de formuliergegevens bevat.
      * Een tekenreekswaarde die omgevingsvariabelen opgeeft die alle relevante HTTP-headers bevatten. U kunt bijvoorbeeld de volgende tekenreekswaarde opgeven: `HTTP_REFERER=referrer&HTTP_CONNECTION=keep-alive&CONTENT_TYPE=application/xml`
      * Een tekenreekswaarde die de `HTTP_USER_AGENT` koptekstwaarde opgeeft; bijvoorbeeld `Mozilla/4.0 (compatible; MSIE 6.0; Windows NT 5.1; SV1; .NET CLR 1.1.4322)`.
      * Een `RenderOptionsSpec` object dat uitvoeringsopties opslaat. Voor meer informatie, .
      * Een leeg `BLOBHolder` object dat door de methode wordt gevuld.
      * Een leeg `javax.xml.rpc.holders.StringHolder` object dat door de methode wordt gevuld.
      * Een leeg `BLOBHolder` object dat door de methode wordt gevuld.
      * Een leeg `BLOBHolder` object dat door de methode wordt gevuld.
      * Een leeg `javax.xml.rpc.holders.ShortHolder` object dat door de methode wordt gevuld.
      * Een leeg `MyArrayOf_xsd_anyTypeHolder` object dat door de methode wordt gevuld. Met deze parameter worden bestandsbijlagen opgeslagen die samen met het formulier worden verzonden.
      * Een leeg `FormsResultHolder` object dat door de methode wordt gevuld met het formulier dat wordt verzonden.
      De `processFormSubmission` methode vult de `FormsResultHolder` parameter met de resultaten van het verzenden van het formulier. De `processFormSubmission` methode retourneert een `FormsResult` object dat de resultaten van het verzenden van het formulier bevat.

   * Controleer of de verwerkingsstatus die aan een verzonden formulier is gekoppeld, `1` door de `FormsResult` methode van het `getAction` object aan te roepen. Als deze methode de waarde retourneert `1`, is de berekening uitgevoerd en kunnen de gegevens worden teruggeschreven naar de webbrowser van de client.


1. De formuliergegevensstroom terugschrijven naar de webbrowser van de client

   * Maak een `javax.servlet.ServletOutputStream` object dat wordt gebruikt om een formuliergegevensstroom naar de webbrowser van de client te verzenden.
   * Maak een `BLOB` object dat formuliergegevens bevat door de `FormsResult` methode van het `getOutputContent` object aan te roepen.
   * Maak een bytearray en vul deze door de `BLOB` methode van het `getBinaryData` object aan te roepen. Hierdoor wordt de inhoud van het `FormsResult` object toegewezen aan de bytearray.
   * Roep de `javax.servlet.http.HttpServletResponse` methode van het `write` object aan om de formuliergegevensstroom naar de webbrowser van de client te verzenden. Geef de bytearray door aan de `write` methode.

**Zie ook** AEM-formulieren[aanroepen met Base64-codering](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-base64-encoding)
