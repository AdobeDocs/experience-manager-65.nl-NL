---
title: Formulieren met API's op een webpagina weergeven
seo-title: Formulieren met API's op een webpagina weergeven
description: U kunt via programmacode zoeken in Forms Manager om een gefilterde lijst met formulieren op uw eigen webpagina's op te halen.
seo-description: U kunt via programmacode zoeken in Forms Manager om een gefilterde lijst met formulieren op uw eigen webpagina's op te halen.
uuid: e51cb2d4-816f-4e6d-a081-51e4999b00ba
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: publish
discoiquuid: 515ceaf6-c132-4e1a-b3c6-5d2c1ccffa7c
translation-type: tm+mt
source-git-commit: 317fadfe48724270e59644d2ed9a90fbee95cf9f

---


# Formulieren met API&#39;s op een webpagina weergeven {#listing-forms-on-a-web-page-using-apis}

AEM Forms biedt een REST-API voor zoekopdrachten die webontwikkelaars kunnen gebruiken om een set formulieren op te vragen en op te halen die aan de zoekcriteria voldoet. U kunt API&#39;s gebruiken om formulieren te zoeken op basis van verschillende filters. Het reactieobject bevat formulierkenmerken, eigenschappen en renderpunten van formulieren.

Als u formulieren wilt zoeken met de REST API, stuurt u een GET-aanvraag naar de server `https://'[server]:[port]'/libs/fd/fm/content/manage.json` met de hieronder beschreven queryparameters.

## Parameters query {#query-parameters}

<table>
 <tbody>
  <tr>
   <td><strong>Kenmerknaam<br /> </strong></td>
   <td><strong>Beschrijving<br /> </strong></td>
  </tr>
  <tr>
   <td>func<br /> </td>
   <td><p>Geeft de aan te roepen functie op. Als u formulieren wilt zoeken, stelt u de waarde van het <code>func </code>kenmerk in op <code>searchForms</code>.</p> <p>Bijvoorbeeld: <code class="code">
       URLParameterBuilder entityBuilder=new URLParameterBuilder ();
       entityBuilder.add("func", "searchForms");</code></p> <p><strong>Opmerking:</strong> <em>Deze parameter is verplicht.</em><br /> </p> </td>
  </tr>
  <tr>
   <td>appPath<br /> </td>
   <td><p>Hier geeft u het toepassingspad op dat u wilt gebruiken om formulieren te zoeken. Standaard zoekt het kenmerk appPath alle toepassingen die beschikbaar zijn op het niveau van de hoofdnode.<br /> </p> <p>U kunt meerdere toepassingspaden opgeven in één zoekquery. Scheid meerdere paden van elkaar met verticale streep (|). </p> </td>
  </tr>
  <tr>
   <td>cutPoints<br /> </td>
   <td><p>Geeft de eigenschappen aan die met de elementen moeten worden opgehaald. U kunt sterretje (*) gebruiken om alle eigenschappen tegelijk op te halen. Gebruik de verticale operator (|) om meerdere eigenschappen op te geven. </p> <p>Bijvoorbeeld: <code>cutPoints=propertyName1|propertyName2|propertyName3</code></p> <p><strong>Opmerking</strong>: </p>
    <ul>
     <li><em>Eigenschappen zoals id, path en name worden altijd opgehaald. </em></li>
     <li><em>Elk element heeft een andere set eigenschappen. Eigenschappen zoals formUrl, pdfUrl en guideUrl zijn niet afhankelijk van het kenmerk cutpoints. Deze eigenschappen zijn afhankelijk van het type element en worden dienovereenkomstig opgehaald. </em></li>
    </ul> </td>
  </tr>
  <tr>
   <td>relation<br /> </td>
   <td>Hiermee geeft u de verwante elementen op die samen met de zoekresultaten moeten worden opgehaald. U kunt een van de volgende opties kiezen om gerelateerde elementen op te halen:
    <ul>
     <li><strong>NO_RELATION</strong>: Verwante elementen niet ophalen.</li>
     <li><strong>ONMIDDELLIJK</strong>: Hiermee zoekt u elementen die rechtstreeks gerelateerd zijn aan zoekresultaten.</li>
     <li><strong>ALLES</strong>: Rechtstreeks en indirect verband houdende activa ophalen.</li>
    </ul> </td>
  </tr>
  <tr>
   <td>maxSize</td>
   <td>Hiermee geeft u het maximum aantal formulieren op dat moet worden opgehaald.</td>
  </tr>
  <tr>
   <td>offset</td>
   <td>Hier geeft u het aantal formulieren op dat u vanaf het begin wilt overslaan.</td>
  </tr>
  <tr>
   <td>returnCount</td>
   <td>Geeft aan of de zoekresultaten die aan de opgegeven criteria voldoen, moeten worden geretourneerd. </td>
  </tr>
  <tr>
   <td>instructies</td>
   <td><p>Hier geeft u de lijst met instructies op. De query's worden uitgevoerd in de lijst met instructies die in de JSON-indeling zijn opgegeven. </p> <p>Bijvoorbeeld:</p> <p><code class="code">JSONArray statementArray=new JSONArray();
       JSONObject statement=new JSONObject();
       statement.put("name", "title");
       statement.put("value", "SimpleSurveyAF");
       statement.put("operator", "EQ"); statementArray.put(statement);</code></p> <p>In het bovenstaande voorbeeld: </p>
    <ul>
     <li><strong>naam</strong>: Hiermee wordt de naam opgegeven van de eigenschap waarnaar moet worden gezocht.</li>
     <li><strong>waarde</strong>: geeft de waarde aan van de eigenschap waarnaar moet worden gezocht.</li>
     <li><strong>operator</strong>: geeft de operator aan die moet worden toegepast tijdens het zoeken. De volgende operatoren worden ondersteund:
      <ul>
       <li>EQ - Gelijk aan </li>
       <li>NEQ - niet gelijk aan</li>
       <li>GT - Groter dan</li>
       <li>LT - Minder dan</li>
       <li>GTEQ - Groter dan of gelijk aan</li>
       <li>LTEQ - kleiner dan of gelijk aan</li>
       <li>BEVAT - A bevat B als B deel uitmaakt van A</li>
       <li>FULLTEXT - Volledige tekstzoekopdracht</li>
       <li>STARTSWITH - A begint met B als B het eerste deel van A is</li>
       <li>ENDSWITH - A eindigt met B als B het einddeel van A is</li>
       <li>LIKE - Implementeert de operator LIKE</li>
       <li>AND - Meerdere instructies combineren</li>
      </ul> <p><strong>Opmerking:</strong> De operatoren <em>GT, LT, GTEQ en LTEQ zijn van toepassing op eigenschappen van lineair type, zoals LONG, DUBBEL en DATE.</em></p> </li>
    </ul> </td>
  </tr>
  <tr>
   <td>bestellingen<br /> </td>
   <td><p>Hiermee geeft u de volgordecriteria voor de zoekresultaten op. De criteria worden gedefinieerd in de JSON-indeling. U kunt zoekresultaten sorteren op meerdere velden. De resultaten worden gesorteerd in de volgorde waarin de velden in de query worden weergegeven.</p> <p>Bijvoorbeeld:</p> <p>Voeg de volgende parameter toe om queryresultaten op te halen die zijn geordend door eigenschap title in oplopende volgorde: </p> <p><code class="code">JSONArray orderingsArray=new JSONArray();
       JSONObject orderings=new JSONObject();
       orderings.put("name", "title");
       orderings.put("criteria", "ASC");
       orderingsArray.put(orderings);
       entityBuilder.add("orderings", orderingsArray.toString());</code></p>
    <ul>
     <li><strong>naam</strong>: Hiermee geeft u de naam op van de eigenschap die moet worden gebruikt om de zoekresultaten te ordenen.</li>
     <li><strong>criteria</strong>: Hiermee geeft u de volgorde van de resultaten op. Het kenmerk order accepteert de volgende waarden:
      <ul>
       <li>ASC - Gebruik ASC om resultaten in oplopende volgorde te rangschikken.<br /> </li>
       <li>DES - Gebruik DES om resultaten in dalende orde te rangschikken.</li>
      </ul> </li>
    </ul> </td>
  </tr>
  <tr>
   <td>includeXdp</td>
   <td>Geeft aan of de binaire inhoud moet worden opgehaald. Het <code>includeXdp</code> kenmerk is van toepassing op elementen van het type <code>FORM</code>, <code>PDFFORM</code>en <code>PRINTFORM</code>.</td>
  </tr>
  <tr>
   <td>assetType</td>
   <td>Geeft de elementtypen aan die moeten worden opgehaald van alle gepubliceerde elementen. Gebruik de verticale operator (|) om meerdere elementtypen op te geven. Geldige elementtypen zijn FORM, PDFFORM, PRINTFORM, RESOURCE en GUIDE.</td>
  </tr>
 </tbody>
</table>

## Voorbeeldverzoek {#sample-request}

```
func : searchForms
appPath : /content/dam/formsanddocuments/MyApplication23
cutPoints : title|description|author|status|creationDate|lastModifiedDate|activationDate|expiryDate|tags|allowedRenderFormat|formmodel
relation : NO_RELATION
includeXdp : false
maxSize : 10
offset : 0
returnCount : true
statements: [{"name":"name","value":"*Claim.xdp","operator":"CONTAINS"},
                {"name":"","value":"Expense","operator":"FULLTEXT"},
                {"name":"description","value":"ABCD*","operator":"CONTAINS"},
                {"name":"status","value":"false","operator":"EQ"},
                {"name":"lastModifiedDate","value":"01/09/2013","operator":"GTEQ"},
                {"name":"lastModifiedDate","value":"01/18/2013","operator":"LTEQ"}]
orderings:[{"name" :“lastModifiedDate“:”order”:”ASC”}]
```

## Monsterreactie {#sample-response}

```
[
{"resultCount":2},
    {"assetType":"FORM","name":"ExpenseClaim.xdp","id":"509fa2d5-e3c9-407b-b8dc-fa0ba08eb0ce",
       "path":"/content/dam/formsanddocuments/MyApplication23/1.0/ExpenseClaim.xdp",
       "title":"Expense Report","description":"ABCDEFGIJK","author":"Frank Bowman",
       "tags":[],"formUrl":"/content/dam/formsanddocuments/MyApplication23/1.0/ExpenseClaim.xdp/jcr:content",
       "pdfUrl":"/content/dam/formsanddocuments/MyApplication23/1.0/ExpenseClaim.xdp/jcr:content?type=pdf",
       "references":[],"images":[{"assetType":"resource","name":"Image.gif","id":"5477a127-8bbf-4cec-8f81-2689e5cb4a15",
       "path":"/content/dam/formsanddocuments/MyApplication23/1.0/Image.gif","resourceSize":0}],
       "status":false,"creationDate":1358429845623,"lastModifiedDate":1358429846771},
{"assetType":"FORM","name":"ExpenseClaim.xdp","id":"4312239b-b666-4d36-95bc-641b3a39ddd4",
       "path":"/content/dam/formsanddocuments/MyApplication23/ExpenseClaim.xdp",
       "title":"Expense Report","description":"ABCDefghijklm","author":"Frank Bowman",
       "tags":[],"formUrl":"/content/dam/formsanddocuments/MyApplication23/ExpenseClaim.xdp/jcr:content",
       "pdfUrl":"/content/dam/formsanddocuments/MyApplication23/ExpenseClaim.xdp/jcr:content?type=pdf",
       "references":[],"images":[{"assetType":"resource","name":"Image.gif","id":"118a2e3f-7097-4d8c-85d1-651306de284a",
       "path":"/content/dam/formsanddocuments/MyApplication23/Image.gif","resourceSize":0}],"status":false,
       "creationDate":1358429856690,"lastModifiedDate":1358430109023}
]
```

## Verwante artikelen

* [Formulierportonderdelen inschakelen](/help/forms/using/enabling-forms-portal-components.md)
* [Pagina Formulierportal maken](/help/forms/using/creating-form-portal-page.md)
* [Formulieren op een webpagina weergeven met API&#39;s](/help/forms/using/listing-forms-webpage-using-apis.md)
* [Concepten en verzendingscomponent gebruiken](/help/forms/using/draft-submission-component.md)
* [Opslag van concepten en verzonden formulieren aanpassen](/help/forms/using/draft-submission-component.md)
* [Voorbeeld voor het integreren van concepten en verzendingen in de database](/help/forms/using/integrate-draft-submission-database.md)
* [Sjablonen aanpassen voor componenten van een formulierportal](/help/forms/using/customizing-templates-forms-portal-components.md)
* [Inleiding tot het publiceren van formulieren op een portal](/help/forms/using/introduction-publishing-forms.md)