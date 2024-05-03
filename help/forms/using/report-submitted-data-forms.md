---
title: API's voor het werken met verzonden formulieren op het formulierportaal
description: AEM Forms biedt API's die u kunt gebruiken om query's uit te voeren en acties uit te voeren voor verzonden formuliergegevens in de formulierportal.
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: publish, developer-reference
feature: Forms Portal
exl-id: a685889e-5d24-471c-926d-dbb096792bc8
solution: Experience Manager, Experience Manager Forms
role: User, Developer
source-git-commit: f6771bd1338a4e27a48c3efd39efe18e57cb98f9
workflow-type: tm+mt
source-wordcount: '539'
ht-degree: 1%

---

# API&#39;s voor het werken met verzonden formulieren op het formulierportaal {#apis-to-work-with-submitted-forms-on-forms-portal}

AEM Forms biedt API&#39;s die u kunt gebruiken voor het zoeken naar formuliergegevens die via de portal Formulieren worden verzonden. Bovendien kunt u opmerkingen plaatsen of eigenschappen van verzonden formulieren bijwerken met de API&#39;s die in dit document worden beschreven.

>[!NOTE]
>
>Gebruikers die de API&#39;s aanroepen, moeten worden toegevoegd aan de groep met revisoren, zoals wordt beschreven in [Verzendrevisoren koppelen aan een formulier](/help/forms/using/adding-reviewers-form.md).

## GET /content/forms/portal/submission.review.json?func=getFormsForSubmissionReview {#get-content-forms-portal-submission-review-json-func-getformsforsubmissionreview-br}

Retourneert een lijst met alle in aanmerking komende formulieren.

### URL-parameters {#url-parameters}

Voor deze API zijn geen aanvullende parameters vereist.

### Antwoord {#response}

Het reactieobject bevat een JSON-array die formuliernamen en het pad naar de opslagplaats bevat. De structuur van de respons is als volgt:

```json
[
 {formName: "<form name>",
 formPath: "<path to the form>" },
 {.....},
 ......]
```

### Voorbeeld {#example}

**Aanvraag-URL**

```http
https://[host]:[port]/content/forms/portal/submission.review.json?func=getFormsForSubmissionReview
```

**Antwoord**

```json
[{"formPath":"/content/dam/formsanddocuments/forms-review/form2","formName":"form2"},{"formPath":"/content/dam/formsanddocuments/forms-review/form1","formName":"form1"}]
```

## GET /content/forms/portal/submission.review.json?func=getAllSubmissions {#get-content-forms-portal-submission-review-json-func-getallsubmissions}

Retourneert details van alle verzonden formulieren. U kunt URL-parameters echter gebruiken om de resultaten te beperken.

### URL-parameters {#url-parameters-1}

Geef de volgende parameters op in de aanvraag-URL:

<table>
 <tbody>
  <tr>
   <th>Parameter</th>
   <th>Beschrijving</th>
  </tr>
  <tr>
   <td><code>formPath</code></td>
   <td>Hiermee geeft u het CRX-opslagpad op waar het formulier zich bevindt. Als u het formulierpad niet opgeeft, wordt een leeg antwoord geretourneerd.<br /> </td>
  </tr>
  <tr>
   <td><code>offset</code><br /> (optioneel)</td>
   <td>Geeft het beginpunt op in de index van de resultaatset. De standaardwaarde is <strong>0</strong>.</td>
  </tr>
  <tr>
   <td><code>limit</code><br /> (optioneel)</td>
   <td>Hiermee beperkt u het aantal resultaten. De standaardwaarde is <strong>30</strong>.</td>
  </tr>
  <tr>
   <td><code>orderby</code> <br /> (optioneel)</td>
   <td>Specifies the property for sorting results. De standaardwaarde is <strong>jcr:lastModified</strong>, die resultaten sorteert op basis van de laatste gewijzigde tijd.</td>
  </tr>
  <tr>
   <td><code>sort</code> <br /> (optioneel)</td>
   <td>Hiermee geeft u de volgorde voor het sorteren van resultaten op. De standaardwaarde is <strong>desc</strong>en sorteert resulteert in aflopende volgorde. U kunt <code>asc</code> om de resultaten in oplopende volgorde te sorteren.</td>
  </tr>
  <tr>
   <td><code>cutPoints</code> <br /> (optioneel)</td>
   <td>Hiermee geeft u een door komma's gescheiden lijst met formuliereigenschappen op die in de resultaten moeten worden opgenomen. De standaardeigenschappen zijn:<br /> <code>formName</code>, <code>formPath</code>, <code>submitID</code>, <code>formType</code>, <code>jcr:lastModified</code>, <code>owner</code></td>
  </tr>
  <tr>
   <td><code>search</code> <br /> (optioneel)</td>
   <td>Zoekt de opgegeven waarde in formuliereigenschappen en retourneert formulieren met overeenkomende waarden. De standaardwaarde is <strong>""</strong>.</td>
  </tr>
 </tbody>
</table>

### Antwoord {#response-1}

Het reactieobject bevat een JSON-array die details van de opgegeven formulieren bevat. De structuur van de respons is als volgt:

```json
{
 total: "<total number of submissions>",
 items: [{ formName: "<name of the form>", formPath: "<path to the form>", owner: "<owner of the form>"},
 ....]}
```

### Voorbeeld {#example-1}

**Aanvraag-URL**

```http
https://[host]:[port]/content/forms/portal/submission.review.json?func=getAllSubmissions&formPath=/content/dam/formsanddocuments/forms-review/form2
```

**Antwoord**

```json
{"total":1,"items":[{"formName":"form2","formPath":"/content/dam/formsanddocuments/forms-review/form2","submitID":"1403037413508500","formType":"af","jcr:lastModified":"2015-11-05T17:52:32.243+05:30","owner":"admin"}]}
```

## POST /content/forms/portal/submission.review.json?func=addComment {#post-content-forms-portal-submission-review-json-func-addcomment-br}

Voegt een opmerking toe aan de opgegeven verzendinstantie.

### URL-parameters {#url-parameters-2}

Geef de volgende parameters op in de aanvraag-URL:

| Parameter | Beschrijving |
|---|---|
| `submitID` | Hiermee wordt de metagegevens-id opgegeven die aan een verzendinstantie is gekoppeld. |
| `Comment` | Geeft de tekst aan voor de opmerking die moet worden toegevoegd aan de opgegeven verzendinstantie. |

### Antwoord {#response-2}

Retourneert een opmerking-id bij het plaatsen van een opmerking.

### Voorbeeld {#example-2}

**Aanvraag-URL**

```http
https://[host:'port'/content/forms/portal/submission.review.json?func=addComment&submitID=1403037413508500&comment=API+test+comment
```

**Antwoord**

```java
1403873422601300
```

## GET /content/forms/portal/submission.review.json?func=getComments   {#get-content-forms-portal-submission-review-json-func-getcomments-nbsp}

Retourneert alle opmerkingen die op het opgegeven verzendexemplaar zijn geplaatst.

### URL-parameters {#url-parameters-3}

Geef de volgende parameter op in de aanvraag-URL:

| Parameter | Beschrijving |
|---|---|
| `submitID` | Hiermee wordt de metagegevens-id van een verzendinstantie opgegeven. |

### Antwoord {#response-3}

Het reactieobject bevat een JSON-array die alle opmerkingen bevat die aan de opgegeven verzendings-id zijn gekoppeld. De structuur van de respons is als volgt:

```json
[{
 owner: "<name of the commenter>",
 comment: "<comment text>",
 time: "<time when the comment was posted>"},
 { }......]
```

### Voorbeeld {#example-3}

**Aanvraag-URL**

```http
https://[host]:'port'/content/forms/portal/submission.review.json?func=getComments&submitID=1403037413508500
```

**Antwoord**

```java
[{"owner":"fr1","comment":"API test comment","time":1446726988250}]
```

## POST /content/forms/portal/submission.review.json?func=updateSubmission {#post-content-forms-portal-submission-review-json-func-updatesubmission-br}

Hiermee wordt de waarde van de opgegeven eigenschap van de opgegeven ingediende formulierinstantie bijgewerkt.

### URL-parameters {#url-parameters-4}

Geef de volgende parameters op in de aanvraag-URL:

| Parameter | Beschrijving |
|---|---|
| `submitID` | Hiermee wordt de metagegevens-id opgegeven die aan een verzendinstantie is gekoppeld. |
| `property` | Hiermee geeft u de formuliereigenschap op die moet worden bijgewerkt. |
| `value` | Specifies the value of the form property to be updated. |

### Antwoord {#response-4}

Retourneert een JSON-object met informatie over de geposte update.

### Voorbeeld {#example-4}

**Aanvraag-URL**

```http
https://[host]:'port'/content/forms/portal/submission.review.json?func=updateSubmission&submitID=1403037413508500&value=sample_value&property=some_new_prop
```

**Antwoord**

```json
{"formName":"form2","owner":"admin","jcr:lastModified":1446727516593,"path":"/content/forms/fp/admin/submit/metadata/1403037413508500.html","submitID":"1403037413508500","status":"submitted"}
```
