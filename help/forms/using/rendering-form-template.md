---
title: Formuliersjabloon weergeven voor HTML5-formulieren
seo-title: Formuliersjabloon weergeven voor HTML5-formulieren
description: HTML5-formulierprofielen zijn gekoppeld aan profielrenderingen. Profielrendering zijn JSP-pagina's die verantwoordelijk zijn voor het genereren van HTML-representatie van het formulier door het aanroepen van de Forms OSGi-service.
seo-description: HTML5-formulierprofielen zijn gekoppeld aan profielrenderingen. Profielrendering zijn JSP-pagina's die verantwoordelijk zijn voor het genereren van HTML-representatie van het formulier door het aanroepen van de Forms OSGi-service.
uuid: 34daed78-0611-4355-9698-0d7f758e6b61
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: hTML5_forms
discoiquuid: cb75b826-d044-44be-b364-790c046513e0
translation-type: tm+mt
source-git-commit: 1343cc33a1e1ce26c0770a3b49317e82353497ab
workflow-type: tm+mt
source-wordcount: '568'
ht-degree: 1%

---


# Formuliersjabloon weergeven voor HTML5-formulieren {#rendering-form-template-for-html-forms}

## Eindpunt {#render-endpoint} renderen

HTML5-formulieren hebben het idee van **Profielen** die als REST-eindpunten worden weergegeven om de mobiele weergave van formuliersjablonen mogelijk te maken. Deze profielen hebben **Profielrenderer** gekoppeld. Het zijn JSP-pagina&#39;s die verantwoordelijk zijn voor het genereren van HTML-representatie van het formulier door de Forms OSGi-service aan te roepen. Het JCR-pad van het knooppunt Profile bepaalt de URL van het eindpunt van de renderbewerking. Het standaardrendereindpunt van het formulier dat verwijst naar het standaardprofiel ziet er als volgt uit:

https://&lt;*host*:&lt;*port*>/content/xfaforms/profiles/default.html?contentRoot=&lt;*pad van de map met het formulier xdp*>&amp;template=&lt;*naam van de xdp*>>

Bijvoorbeeld, `http://localhost:4502/content/xfaforms/profiles/default.html?contentRoot=c:/xdps&template=sampleForm.xdp`

Voor een douaneprofiel, verandert het eindpunt dienovereenkomstig. Het eindpunt voor het aangepaste profiel met de naam Transform is bijvoorbeeld:

`http://localhost:4502/content/xfaforms/profiles/hrforms.html?contentRoot=c:/xdps&template=sampleForm.xdp`

Als uw sjabloon zich in de AEM opslagplaats bevindt in een toepassing met de naam FormSubmission, is de URI:

```http
http://localhost:4502/content/xfaforms/profiles/default.html?
 contentRoot=crx:///content/dam/formsanddocuments/FormSubmission/1.0
 &template=sampleForm.xdp
```

## Parameters {#render-parameters} renderen

De volgende aanvraagparameters worden ondersteund bij het weergeven van formulier als HTML:

<table>
 <tbody>
  <tr>
   <th><strong>Parameter </strong></th>
   <th><strong>Beschrijving</strong></th>
  </tr>
  <tr>
   <td>template<br /> </td>
   <td>Deze parameter specificeert de naam van het malplaatjedossier.<br /> </td>
  </tr>
  <tr>
   <td>contentRoot<br /> </td>
   <td>Deze parameter specificeert de weg waar het malplaatje en de bijbehorende middelen verblijven. Dit pad kan het systeempad van het serverbestand of een opslagpad zijn, of http of een FTP-pad.<br /> </td>
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
| dataRef | Deze parameter specificeert **absolute weg** van het gegevensdossier dat met het malplaatje wordt samengevoegd. Deze parameter kan een URL zijn naar een andere service die de gegevens retourneert in XML-indeling. |
| gegevens | Deze parameter geeft de UTF-8-gecodeerde gegevensbytes aan die met de sjabloon worden samengevoegd. Als deze parameter is opgegeven, negeert het HTML5-formulier de parameter dataRef. |

### De renderparameter {#passing-the-render-parameter} doorgeven

HTML5-formulieren ondersteunen drie methoden voor het doorgeven van de renderparameters. U kunt parameters doorgeven via URL&#39;s, sleutel-waardeparen en profielknooppunten. In de renderparameter heeft sleutelwaardepaar de hoogste prioriteit gevolgd door het profielknooppunt. De URL-verzoekparameter heeft de minste prioriteit.

* **Parameters** voor URL-aanvragen: U kunt de renderparameters opgeven in de URL. In de URL-aanvraagparameters zijn de parameters zichtbaar voor de eindgebruiker. De volgende verzendings-URL bevat bijvoorbeeld een sjabloonparameter in de URL: `http://localhost:4502/content/xfaforms/profiles/default.html?contentRoot=/Applications/FormSubmission/1.0&template=sampleForm.xdp`

* **SetAttribute request parameters**: U kunt de renderparameters opgeven als sleutelwaardepaar. In de SetAttribute- verzoekparameters, zijn de parameters niet zichtbaar aan het eind - gebruiker. U kunt een verzoek van een andere JSP naar HTML5-formulierprofielrenderer JSP doorsturen en *setAttribute* op aanvraagobject gebruiken om alle renderparameters door te geven. Deze methode heeft de hoogste prioriteit.

* **Parameters voor profielknooppuntaanvraag:** u kunt de renderparameters opgeven als knoopeigenschappen van een profielknooppunt. In de parameters van het profielknooppuntverzoek, zijn de parameters niet zichtbaar aan het eind - gebruiker. Profielknooppunt is het knooppunt waarnaar de aanvraag wordt verzonden. Gebruik de CRXDE-lijst om parameters op te geven als knoopeigenschappen.

### Parameters {#submit-parameters} verzenden

HTML5-formulieren verzenden gegevens; serverscripts en webservices uitvoeren op AEM servers. Zie [HTML5 Forms Service Proxy](/help/forms/using/service-proxy.md) voor gedetailleerde informatie over parameters die worden gebruikt voor het uitvoeren van serverscripts en webservices op AEM servers.
