---
title: AEM Forms aanroepen met REST-verzoeken
seo-title: AEM Forms aanroepen met REST-verzoeken
description: Roep in Workbench gemaakte processen aan met behulp van REST-aanvragen.
seo-description: Roep in Workbench gemaakte processen aan met behulp van REST-aanvragen.
uuid: 3a19a296-f3fe-4e50-9143-b68aed37f9ef
contentOwner: admin
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: coding
discoiquuid: df7b60bb-4897-479e-a05e-1b1e9429ed87
role: Developer
translation-type: tm+mt
source-git-commit: 48726639e93696f32fa368fad2630e6fca50640e
workflow-type: tm+mt
source-wordcount: '2521'
ht-degree: 0%

---


# AEM Forms aanroepen met REST-verzoeken {#invoking-aem-forms-using-rest-requests}

**Voorbeelden en voorbeelden in dit document gelden alleen voor AEM Forms in JEE-omgeving.**

De processen die in Workbench worden gecreeerd kunnen worden gevormd zodat u hen door de verzoeken van de Overdracht van de Staat van de Vertegenwoordiging (REST) kunt aanhalen. REST-aanvragen worden verzonden vanuit HTML-pagina&#39;s. Met andere woorden, u kunt een Forms-proces rechtstreeks vanaf een webpagina oproepen met behulp van een REST-aanvraag. U kunt bijvoorbeeld een nieuw exemplaar van een webpagina openen. Vervolgens kunt u een Forms-proces aanroepen en een gerenderd PDF-document laden met gegevens die in een HTTP-POST-aanvraag zijn verzonden.

Er zijn twee typen HTML-clients. De eerste HTML-client is een AJAX client die in JavaScript is geschreven. De tweede client is een HTML-formulier met een verzendknop. Een HTML-gebaseerde clienttoepassing is niet de enige mogelijke REST-client. Om het even welke cliënttoepassing die HTTP- verzoeken steunt kan de dienst aanhalen gebruikend een Oproepen van het REST. U kunt bijvoorbeeld een service oproepen met behulp van een REST-aanroep vanuit een PDF-formulier. (Zie [Het MyApplication/EncryptDocument-proces aanroepen vanuit Acrobat](#rest-invocation-examples).)

Als u REST-verzoeken gebruikt, wordt u aangeraden Forms-services niet rechtstreeks aan te roepen. In plaats daarvan, haal processen aan die in Workbench werden gecreeerd. Wanneer het creëren van een proces dat voor de Oproepen van het HERSTEL wordt bedoeld, gebruik een programmatic beginpunt. In deze situatie, wordt het REST eindpunt automatisch toegevoegd. Zie [Workbench gebruiken](https://www.adobe.com/go/learn_aemforms_workbench_63) voor informatie over het maken van processen in Workbench.

Wanneer u een service aanroept met REST, wordt u gevraagd om een gebruikersnaam en wachtwoord voor AEM formulieren. Als u echter geen gebruikersnaam en wachtwoord wilt opgeven, kunt u de servicebeveiliging uitschakelen.

Om de dienst van Forms aan te halen (een proces wordt de dienst wanneer het proces) gebruikend REST wordt geactiveerd, vorm een REST eindpunt. (Zie &quot;Eindpunten beheren&quot; in [administration help](https://www.adobe.com/go/learn_aemforms_admin_63).)

Nadat een REST eindpunt wordt gevormd, kunt u de dienst van Forms aanhalen door een methode van de GET van HTTP of een methode van de POST te gebruiken.

```java
 action="https://hiro-xp:8080/rest/services/[ServiceName]/[OperationName]:[ServiceVersion]" method="post" enctype="multipart/form-data"
```

De verplichte waarde `ServiceName` is de naam van de Forms-service die moet worden aangeroepen. De optionele waarde `OperationName` is de naam van de bewerking van de service. Als deze waarde niet wordt gespecificeerd, blijft deze naam aan `invoke` in gebreke, die de verrichtingsnaam is die het proces begint. De optionele waarde `ServiceVersion` is de versie die is gecodeerd in de indeling X.Y. Als deze waarde niet wordt opgegeven, wordt de meest recente versie gebruikt. De waarde `enctype` kan ook `application/x-www-form-urlencoded` zijn.

## Ondersteunde gegevenstypen {#supported-data-types}

De volgende gegevenstypen worden ondersteund wanneer AEM Forms-services worden aangeroepen met REST-verzoeken:

* Primitieve Java-gegevenstypen, zoals tekenreeksen en gehele getallen
* `com.adobe.idp.Document` gegevenstype
* XML-gegevenstypen zoals `org.w3c.Document` en `org.w3c.Element`
* Inzamelingsobjecten zoals `java.util.List` en `java.util.Map`

   Deze gegevenstypen worden doorgaans geaccepteerd als invoerwaarden voor processen die in Workbench zijn gemaakt.

   Als de dienst van Forms met de methode van de POST van HTTP wordt aangehaald, worden de argumenten overgegaan binnen het aanvraaglichaam van HTTP. Als de handtekening van de AEM Forms-service een parameter voor tekenreeksinvoer bevat, kan de aanvraaghoofdtekst de tekstwaarde van de invoerparameter bevatten. Als de handtekening van de service meerdere tekenreeksparameters definieert, kan de aanvraag de HTTP-notatie `application/x-www-form-urlencoded` volgen met de namen van de parameter die als veldnamen van het formulier worden gebruikt.

   Als een Forms-service een tekenreeksparameter retourneert, is het resultaat een tekstuele representatie van de uitvoerparameter. Als de dienst veelvoudige koordparameters terugkeert, is het resultaat een document van XML die de outputparameters in het volgende formaat coderen:
   ` <result> <output-paramater1>output-parameter-value-as-string</output-paramater1> . . . <output-paramaterN>output-parameter-value-as-string</output-paramaterN> </result>`

   >[!NOTE]
   >
   >De waarde `output-paramater1` vertegenwoordigt de naam van de outputparameter.

   Als een Forms-service een parameter `com.adobe.idp.Document` vereist, kan de service alleen worden aangeroepen met de methode HTTP-POST. Als voor de service één `com.adobe.idp.Document`-parameter vereist is, wordt de HTTP-aanvraaginstantie de inhoud van het invoerobject Document.

   Als een dienst van AEM Forms veelvoudige inputparameters vereist, moet het HTTP- verzoeklichaam een meerdelig MIME- bericht zijn zoals die door RFC 1867 wordt bepaald. (RFC 1867 is een standaard die door webbrowsers wordt gebruikt om bestanden naar websites te uploaden.) Elke invoerparameter moet als afzonderlijk deel van het multipart-bericht worden verzonden en in de `multipart/form-data`-indeling worden gecodeerd. De naam van elk onderdeel moet overeenkomen met de naam van de parameter.

   Lijsten en kaarten worden ook gebruikt als invoerwaarden voor AEM Forms-processen die in Workbench zijn gemaakt. Dientengevolge, kunt u deze gegevenstypes gebruiken wanneer het gebruiken van een REST verzoek. Java-arrays worden niet ondersteund omdat ze niet worden gebruikt als invoerwaarde voor een AEM Forms-proces.

   Als een invoerparameter een lijst is, kan een REST-client deze verzenden door de parameter meerdere keren op te geven (één keer voor elk item in de lijst). Als A bijvoorbeeld een lijst met documenten is, moet de invoer een meerdelig bericht zijn dat uit meerdere delen bestaat met de naam A. In dit geval wordt elk onderdeel met de naam A een item in de invoerlijst. Als B een lijst met tekenreeksen is, kan de invoer een `application/x-www-form-urlencoded`-bericht zijn dat uit meerdere velden met de naam B bestaat. In dit geval wordt elk formulierveld met de naam B een item in de invoerlijst.

   Als een inputparameter een kaart is en het de diensten slechts inputparameter is, dan wordt elk deel/gebied van het inputbericht een zeer belangrijk/waardeverslag in de kaart. De naam van elk onderdeel/veld wordt de sleutel van de record. De inhoud van elk onderdeel/veld wordt de waarde van de record.

   Als een inputkaart niet de diensten slechts inputparameter is, dan kan elk zeer belangrijk/waardeverslag dat tot de kaart behoort worden verzonden gebruikend een parameter die als aaneenschakeling van de parameternaam en de sleutel van het verslag wordt genoemd. Een invoerkaart met de naam `attributes` kan bijvoorbeeld worden verzonden met een lijst van de volgende sleutel-/waardeparen:

   `attributesColor=red`

   `attributesShape=box`

   `attributesWidth=5`

   Dit vertaalt zich in een kaart van drie verslagen: `Color=red`, `Shape=box` en `Width=5`.

   De uitvoerparameters van de lijst- en kaarttypen maken deel uit van het resulterende XML-bericht. De uitvoerlijst wordt in XML vertegenwoordigd als een reeks elementen van XML met één element voor elk punt in de lijst. Elk element krijgt dezelfde naam als de uitvoerlijstparameter. De waarde van elk XML-element bestaat uit twee dingen:

* Een tekstrepresentatie van het item in de lijst (als de lijst uit tekenreekstypen bestaat)
* Een URL die naar de inhoud van Document wijst (als de lijst uit `com.adobe.idp.Document` voorwerpen bestaat)

   Het volgende voorbeeld is een XML-bericht dat wordt geretourneerd door een service met één uitvoerparameter met de naam *list*. Dit is een lijst met gehele getallen.
   ` <result>   <list>12345</list>   . . .   <list>67890</list>  </result>`Een parameter van de outputkaart wordt vertegenwoordigd in het resulterende bericht van XML als reeks elementen van XML met één element voor elke verslag in de kaart. Elk element krijgt dezelfde naam als de sleutel van de kaartrecord. De waarde van elk element is een tekstrepresentatie van de waarde van de kaartrecord (als de kaart bestaat uit records met een tekenreekswaarde) of een URL die naar de inhoud van het document wijst (als de kaart uit records met de waarde `com.adobe.idp.Document` bestaat). Hieronder ziet u een voorbeeld van een XML-bericht dat wordt geretourneerd door een service met één uitvoerparameter met de naam `map`. Deze parameterwaarde is een kaart die uit verslagen bestaat die brieven met `com.adobe.idp.Document` voorwerpen associëren.
   ` <result>   http://localhost:8080/DocumentManager/docm123/4567   . . .   <Z>http://localhost:8080/DocumentManager/docm987/6543</Z>  </result>  `

## Asynchrone aanroepen {#asynchronous-invocations}

Sommige AEM Forms-diensten, zoals menselijke-centrische langlevende processen, hebben lange tijd nodig om te voltooien. Deze diensten kunnen asynchroon op een niet-blokkerende manier worden aangehaald. (Zie [Langdurige processen aanroepen vanuit menselijk-centraal systeem](/help/forms/developing/invoking-human-centric-long-lived.md#invoking-human-centric-long-lived-processes).)

Een AEM Forms-service kan asynchroon worden aangeroepen door `services` te vervangen door `async_invoke` in de oproepings-URL, zoals in het volgende voorbeeld wordt getoond.

```java
 http://localhost:8080/rest/async_invoke/SomeService. SomeOperation?integer_input_variable=123&string_input_variable=abc
```

Deze URL retourneert de id-waarde (in &quot;text/plain&quot;-indeling) van de taak die verantwoordelijk is voor deze aanroep.

De status van de asynchrone aanroep kan worden opgehaald door een aanroepings-URL te gebruiken, waarbij `services` wordt vervangen door `async_status`. De URL moet een `job_id`-parameter bevatten die de id-waarde opgeeft van de taak die aan deze aanroep is gekoppeld. Bijvoorbeeld:

```java
 http://localhost:8080/rest/async_status/SomeService.SomeOperation?job_id=2345353443366564
```

Deze URL retourneert een geheel getal (in de notatie &quot;text/plain&quot;) waarmee de taakstatus wordt gecodeerd volgens de specificaties van Taakbeheer (2 betekent bijvoorbeeld dat de taak wordt uitgevoerd, 3 betekent voltooid, 4 betekent mislukt, enzovoort.)

Als de taak is voltooid, retourneert de URL hetzelfde resultaat als wanneer de service synchroon is aangeroepen.

Nadat de taak is voltooid en het resultaat is opgehaald, kan de taak worden verwijderd door een aanroepings-URL te gebruiken waarbij `services` wordt vervangen door `async_dispose`. De URL moet ook een `job_id`-parameter bevatten die de id-waarde van de taak opgeeft. Bijvoorbeeld:

```java
 http://localhost:8080/rest/async_dispose/SomeService.SomeOperation?job_id=2345353443366564
```

Als de taak is verwijderd, retourneert deze URL een leeg bericht.

## Foutmelding {#error-reporting}

Als een synchrone of asynchrone aanroepingsaanvraag niet kan worden voltooid wegens een uitzondering die op de server wordt geworpen, wordt de uitzondering gerapporteerd als deel van het HTTP- antwoordbericht. Als de oproepings-URL (of de `async_result`-URL in het geval van een asynchrone aanroep) geen .xml-achtervoegsel heeft, retourneert de REST-provider de HTTP-code `500 Internal Server Error` gevolgd door een uitzonderingsbericht.

Als de oproepings-URL (of de `async_result`-URL in het geval van een asynchrone aanroep) wel het .xml-achtervoegsel heeft, retourneert de REST-provider de HTTP-code `200 OK`gevolgd door een XML-document waarin de uitzondering in de volgende indeling wordt beschreven.

```xml
 <exception>
       <exception_class_name>[
       <DSCError>
          <componentUID>component_UUD</componentUID>
         <errorCode>error_code</errorCode>
         <minorCode>minor_code</minorCode>
         <message>error_message</message>
       </DSCError>
 ]
       <message>exception_message</message>
     <stackTrace>exception_stack_trace</stackTrace>
       </exception_class_name>
     <exception>
       </exception>
 </exception>
```

Het element `DSCError` is optioneel en is alleen aanwezig als de uitzondering een instantie van `com.adobe.idp.dsc.DSCException` is.

## Beveiliging en verificatie {#security-and-authentication}

Om REST-aanroepen te voorzien van een beveiligd transport, kan een beheerder van AEM formulieren het HTTPS-protocol inschakelen op de J2EE-toepassingsserver die als host fungeert voor AEM Forms. Deze configuratie is specifiek voor de J2EE toepassingsserver; maakt geen deel uit van de configuratie van de formulierserver.

>[!NOTE]
>
>Als ontwikkelaar Workbench die uw processen door een eindpunt van REST wil blootstellen, houd in mening de XSS kwetsbaarheidskwestie. XSS-kwetsbaarheden kunnen worden gebruikt om cookies te stelen of te manipuleren, de presentatie van inhoud te wijzigen en vertrouwelijke informatie te compromitteren. Als een XSS-kwetsbaarheid een probleem is, wordt u aangeraden de proceslogica uit te breiden met de extra regels voor de validatie van invoer- en uitvoergegevens.

## AEM Forms-services die REST-oproeping ondersteunen {#aem-forms-services-that-support-rest-invocation}

Hoewel u aangeraden processen aan te roepen die u met Workbench hebt gemaakt in plaats van rechtstreeks services, zijn er sommige AEM Forms-services die ondersteuning bieden voor het aanroepen van REST. De reden waarom het wordt geadviseerd dat u een proces in tegenstelling tot de dienst direct aanhaalt is omdat het efficiënter is om een proces aan te halen. Overweeg het volgende scenario. Veronderstel dat u een beleid van een cliënt van REST wilt tot stand brengen. Dat wil zeggen dat u wilt dat de REST-client waarden definieert zoals de naam van het beleid, de offline leaseperiode.

Als u een beleid wilt maken, moet u complexe gegevenstypen definiëren, zoals een `PolicyEntry`-object. Een `PolicyEntry` voorwerp bepaalt attributen zoals toestemmingen verbonden aan het beleid. (Zie [Beleid maken](/help/forms/developing/protecting-documents-policies.md#creating-policies).)

In plaats van een REST-verzoek te verzenden om een beleid te maken (dat het definiëren van complexe gegevenstypen zoals een `PolicyEntry`-object omvat), maakt u een proces dat een beleid maakt met Workbench. Definieer het proces voor het accepteren van primitieve invoervariabelen, zoals een tekenreekswaarde die de procesnaam definieert of een geheel getal dat de offline leaseperiode definieert.

Op deze manier hoeft u geen REST-oproepverzoek te maken dat complexe gegevenstypen bevat die door de bewerking worden vereist. Het proces bepaalt de complexe gegevenstypes en alles u van de cliënt van REST doet haalt het proces aan en gaat primitieve gegevenstypes over. Voor informatie over het aanhalen van een proces die REST gebruiken, zie [Invoking van het proces MyApplication/EncryptDocument gebruikend REST](#rest-invocation-examples).

In de volgende lijsten worden de AEM Forms-services opgegeven die directe Oproepen tot REST ondersteunen.

* Distiller-service
* Rights Management
* GeneratePDF-service
* Genereren3dPDF-service
* FormDataIntegration

## Voorbeelden {#rest-invocation-examples} van oproepen HERSTELLEN

De volgende voorbeelden van REST-oproepen worden gegeven:

* Booleaanse waarden doorgeven aan een AEM Forms-proces
* Datumwaarden doorgeven aan een AEM Forms-proces
* Documenten doorgeven aan een AEM Forms-proces
* Document- en tekstwaarden doorgeven aan een AEM Forms-proces
* Opsommingswaarden doorgeven aan een AEM Forms-proces
* Het MyApplication/EncryptDocument-proces aanroepen met REST
* Het MyApplication/EncryptDocument-proces aanroepen vanuit Acrobat

   In elk voorbeeld wordt getoond hoe verschillende gegevenstypen worden doorgegeven aan een AEM Forms-proces

**Booleaanse waarden doorgeven aan een proces**

In het volgende HTML-voorbeeld worden twee `Boolean`-waarden doorgegeven aan een AEM Forms-proces met de naam `RestTest2`. De naam van de aanroepingsmethode is `invoke` en de versie is 1.0. De methode HTML Post wordt gebruikt.

```html
 <html>
 <body>
 
 <form name="input" action="http://localhost:9080/rest/services/RestTest2/invoke/1.0" method="post">
 
 Boolean 1: <input type="text" name="inBooleanList" value="true">
 Boolean 2: <input type="text" name="inBooleanList" value="false">
 <input type="submit" value="Submit">
 
 </form>
 
 </body>
 </html>
```

**Datumwaarden doorgeven aan een proces**

In het volgende HTML-voorbeeld wordt een datumwaarde doorgegeven aan een AEM Forms-proces met de naam `SOAPEchoService`. De naam van de aanroepingsmethode is `echoCalendar`. De methode HTML `Post` wordt gebruikt.

```html
 <html>
 <body>
 
 <form name="input" action="http://localhost:9080/rest/services/SOAPEchoService/echoCalendar" method="post">
 
 Date: <input type="text" name="value-to-echo" value="2009-01-02T12:15:30Z">
 <input type="submit" value="Submit">
 
 </form>
 
 </body>
 </html>
```

**Documenten doorgeven aan een proces**

In het volgende HTML-voorbeeld wordt een AEM Forms-proces met de naam `MyApplication/EncryptDocument` aangeroepen waarvoor een PDF-document is vereist. Zie [AEM Forms aanroepen met MTOM](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom) voor informatie over dit proces.

```html
 <html>
 <body>
 
 <form name="input" action="http://localhost:9080/rest/services/MyApplication/EncryptDocument/invoke" method="post"
          enctype="multipart/form-data">
 
 File: <input type="file" name="value-to-echo">
 <input type="submit" value="Submit"/>
 
 </form>
 
 </body>
 </html>
```

**Document- en tekstwaarden doorgeven aan een proces**

In het volgende HTML-voorbeeld wordt een AEM Forms-proces met de naam `RestTest3` aangeroepen waarvoor een document en twee tekstwaarden zijn vereist. De methode HTML Post wordt gebruikt.

```html
 <html>
 <body>
 
 <form name="input" action="http://localhost:9080/rest/services/RestTest3" method="post"
          enctype="multipart/form-data">
 
 Doc: <input type="file" name="inDoc">
 String 1: <input type="text" name="inListOfStrings" value="hello">
 String 2: <input type="text" name="inListOfStrings" value="privet">
 <input type="submit" value="Submit"/>
 
 </form>
 
 </body>
 </html>
```

**Opsommingswaarden doorgeven aan een proces**

In het volgende HTML-voorbeeld wordt een AEM Forms-proces met de naam `SOAPEchoService` aangeroepen waarvoor een opsommingswaarde is vereist. De methode HTML Post wordt gebruikt.

```html
 <html>
 <body>
 
 <form name="input" action="https://hiro-xp:8080/rest/services/SOAPEchoService/echoEnum" method="post">
 
 Color Enum Value: <input type="text" name="value-to-echo" value="green">
 <input type="submit" value="Submit">
 
 </form>
 
 </body>
 </html>
```

**Het MyApplication/EncryptDocument-proces aanroepen met REST**

U kunt een kort-levend proces van AEM Forms roepen genoemd *MyApplication/EncryptDocument* door REST te gebruiken.

>[!NOTE]
>
>Dit proces is niet gebaseerd op een bestaand AEM Forms-proces. Om samen met het codevoorbeeld te volgen, creeer een proces genoemd `MyApplication/EncryptDocument` gebruikend workbench. (Zie [Workbench](https://www.adobe.com/go/learn_aemforms_workbench_63) gebruiken.)

Wanneer dit proces wordt aangeroepen, worden de volgende handelingen uitgevoerd:

1. Hiermee verkrijgt u het onbeveiligde PDF-document dat aan het proces wordt doorgegeven. Deze actie is gebaseerd op de `SetValue` verrichting. De inputparameter voor dit proces is een `document` procesvariabele genoemd `inDoc`.
1. Hiermee versleutelt u het PDF-document met een wachtwoord. Deze actie is gebaseerd op de `PasswordEncryptPDF` verrichting. Het met wachtwoord gecodeerde PDF-document wordt geretourneerd in een procesvariabele met de naam `outDoc`.

   Wanneer dit proces wordt aangeroepen met een REST-aanvraag, wordt het gecodeerde PDF-document weergegeven in de webbrowser. Voordat u het PDF-document weergeeft, geeft u het wachtwoord op (tenzij de beveiliging is uitgeschakeld). De volgende HTML-code vertegenwoordigt een REST-aanroepingsverzoek voor het `MyApplication/EncryptDocument`-proces.

   ```html
    <html>
    <body>
    <form action="https://hiro-xp:8080/rest/services/MyApplication/EncryptDocument" method="post" enctype="multipart/form-data">
         <p>Chose a PDF file (.pdf) to send to the EncryptDocument process.</p>
         <p>file:
           <input type="file" name="inDoc" />
         </p>
         <p>
           <input type="submit"/>
         </p>
    </form>
    </body>
   ```

**Het MyApplication/EncryptDocument-proces aanroepen vanuit Acrobat** {#invoke-process-acrobat}

U kunt een Forms-proces aanroepen vanuit Acrobat met behulp van een REST-aanvraag. U kunt bijvoorbeeld het proces *MyApplication/EncryptDocument* aanroepen. Als u een Forms-proces vanuit Acrobat wilt aanroepen, plaatst u een verzendknop in een XDP-bestand in Designer. (Zie [Designer Help](https://www.adobe.com/go/learn_aemforms_designer_63).)

Geef de URL op om het proces binnen het veld *Verzenden naar URL* van de knop aan te roepen, zoals in de volgende afbeelding wordt getoond.

De volledige URL om het proces aan te roepen is https://hiro-xp:8080/rest/services/MyApplication/EncryptDocument.

Als voor het proces een PDF-document nodig is als invoerwaarde, moet u ervoor zorgen dat het formulier als PDF wordt verzonden, zoals in de vorige afbeelding wordt getoond. Als u een proces wilt activeren, moet het proces ook een PDF-document retourneren. Anders kan Acrobat de geretourneerde waarde niet verwerken en treedt er een fout op. U hoeft de naam van de invoerprocesvariabele niet op te geven. Het proces *MyApplication/EncryptDocument* heeft bijvoorbeeld een invoervariabele met de naam `inDoc`. U hoeft niet in Doc op te geven, zolang het formulier als PDF wordt verzonden.

U kunt ook formuliergegevens als XML verzenden naar een Forms-proces. Als u XML-gegevens wilt verzenden, moet u ervoor zorgen dat in de vervolgkeuzelijst `Submit As` XML wordt opgegeven. Omdat de geretourneerde waarde van het proces een PDF-document moet zijn, wordt het PDF-document weergegeven in Acrobat.
