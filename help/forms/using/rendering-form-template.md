---
title: Formuliersjabloon weergeven voor HTML5-formulieren
description: HTML5-formulierprofielen zijn gekoppeld aan profielrenderingen. Profielweergave is JSP-pagina's die verantwoordelijk zijn voor het genereren van een HTML-weergave van het formulier door de Forms OSGi-service aan te roepen.
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: hTML5_forms
discoiquuid: cb75b826-d044-44be-b364-790c046513e0
feature: HTML5 Forms,Mobile Forms
exl-id: 022b9953-2d64-473f-87b7-aac1602f6a7e
solution: Experience Manager, Experience Manager Forms
role: Admin, User, Developer
source-git-commit: d7b9e947503df58435b3fee85a92d51fae8c1d2d
workflow-type: tm+mt
source-wordcount: '535'
ht-degree: 0%

---

# Formuliersjabloon weergeven voor HTML5-formulieren {#rendering-form-template-for-html-forms}

## Eindpunt renderen {#render-endpoint}

HTML5-formulieren hebben het begrip **Profielen** die als REST Endpoints worden blootgesteld om het Mobiele Teruggeven van de Malplaatjes van de Vorm toe te laten. Deze profielen zijn gekoppeld **Profielrenderer**. Zij zijn JSP pagina&#39;s verantwoordelijk voor het produceren van HTML vertegenwoordiging van de vorm door de dienst van Forms OSGi te roepen. Het JCR-pad van het knooppunt Profile bepaalt de URL van het eindpunt van de renderbewerking. Het standaardrendereindpunt van het formulier dat verwijst naar het standaardprofiel ziet er als volgt uit:

https://&lt;*host*>:&lt;*poort*>/content/xfaforms/profiles/default.html?contentRoot=&lt;*pad van de map met formulier xdp*>&amp;template=&lt;*naam van het xdp*>

Bijvoorbeeld: `http://localhost:4502/content/xfaforms/profiles/default.html?contentRoot=c:/xdps&template=sampleForm.xdp`

Voor een douaneprofiel, verandert het eindpunt dienovereenkomstig. Het eindpunt voor het aangepaste profiel met de naam Transform is bijvoorbeeld:

`http://localhost:4502/content/xfaforms/profiles/hrforms.html?contentRoot=c:/xdps&template=sampleForm.xdp`

Als uw sjabloon zich in de AEM opslagplaats bevindt in een toepassing met de naam FormSubmission, is de URI:

```http
http://localhost:4502/content/xfaforms/profiles/default.html?
 contentRoot=crx:///content/dam/formsanddocuments/FormSubmission/1.0
 &template=sampleForm.xdp
```

## Renderparameters {#render-parameters}

De volgende aanvraagparameters worden ondersteund bij het weergeven van het formulier als HTML:

<table>
 <tbody>
  <tr>
   <th><strong>Parameter </strong></th>
   <th><strong>Beschrijving</strong></th>
  </tr>
  <tr>
   <td>template<br /> </td>
   <td>Deze parameter geeft de naam van het sjabloonbestand op.<br /> </td>
  </tr>
  <tr>
   <td>contentRoot<br /> </td>
   <td>Deze parameter specificeert de weg waar het malplaatje en de bijbehorende middelen verblijven. Dit pad kan het systeempad van het serverbestand, een opslagpad of http of een FTP-pad zijn.<br /> </td>
  </tr>
  <tr>
   <td>submitUrl<br /> </td>
   <td>Deze parameter geeft de URL aan waarnaar de XML-formuliergegevens worden gepost.<br /> </td>
  </tr>
 </tbody>
</table>

### Gegevens samenvoegen met formuliersjabloon {#merge-data-with-form-template}

| Parameter | Beschrijving |
|---|---|
| dataRef | Deze parameter specificeert **absoluut pad** van het gegevensbestand dat met de sjabloon is samengevoegd. Deze parameter kan een URL zijn naar een andere service die de gegevens retourneert in XML-indeling. |
| data | Deze parameter geeft de UTF-8-gecodeerde gegevensbytes aan die met de sjabloon worden samengevoegd. Als deze parameter wordt opgegeven, negeert de HTML5-vorm de parameter dataRef. |

### De renderparameter doorgeven {#passing-the-render-parameter}

HTML5-formulieren ondersteunen drie methoden voor het doorgeven van renderparameters. U kunt parameters doorgeven via URL&#39;s, sleutel-waardeparen en profielknooppunten. In de renderparameter heeft sleutelwaardepaar de hoogste prioriteit gevolgd door het profielknooppunt. De URL-verzoekparameter heeft de minste prioriteit.

* **Parameters voor URL-aanvragen**: U kunt de renderparameters opgeven in de URL. In de URL-aanvraagparameters zijn de parameters zichtbaar voor de eindgebruiker. De volgende verzendings-URL bevat bijvoorbeeld een sjabloonparameter in de URL: `http://localhost:4502/content/xfaforms/profiles/default.html?contentRoot=/Applications/FormSubmission/1.0&template=sampleForm.xdp`

* **SetAttribute request parameters**: U kunt de renderparameters opgeven als sleutelwaardepaar. In de SetAttribute- verzoekparameters, zijn de parameters niet zichtbaar aan het eind - gebruiker. U kunt een aanvraag van een andere JSP doorsturen naar de JSP-renderer voor het HTML5-formulierprofiel en *setAttribute* op request-object om alle renderparameters door te geven. Deze methode heeft de hoogste prioriteit.

* **Parameters profielknooppuntaanvraag:** U kunt de renderparameters opgeven als knoopeigenschappen van een profielknooppunt. In de parameters van het profielknooppuntverzoek, zijn de parameters niet zichtbaar aan het eind - gebruiker. Profielknooppunt is het knooppunt waarnaar de aanvraag wordt verzonden. Gebruik de CRXDE-lijst om parameters op te geven als knoopeigenschappen.

### Parameters verzenden {#submit-parameters}

HTML5-formulieren verzenden gegevens; uitvoeren serverscripts en webservices op AEM servers. Voor gedetailleerde informatie over parameters die worden gebruikt om serverscripts en webservices uit te voeren op AEM servers, raadpleegt u [HTML5-formulieren Service Proxy](/help/forms/using/service-proxy.md).
