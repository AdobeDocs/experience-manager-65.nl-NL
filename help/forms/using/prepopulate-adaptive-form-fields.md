---
title: Aangepaste formuliervelden vooraf invullen
seo-title: Aangepaste formuliervelden vooraf invullen
description: Bestaande gegevens gebruiken om velden van een adaptief formulier vooraf in te vullen.
seo-description: Met adaptieve formulieren kunnen gebruikers basisgegevens vooraf invullen in een formulier door u aan te melden met hun sociale profielen. In dit artikel wordt beschreven hoe u dit kunt bereiken.
uuid: 574de83a-7b5b-4a1f-ad37-b9717e5c14f1
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: develop
discoiquuid: 7139a0e6-0e37-477c-9e0b-aa356991d040
docset: aem65
translation-type: tm+mt
source-git-commit: 726163106ddb80600eaa7cc09b1a2e9b035a223e

---


# Aangepaste formuliervelden vooraf invullen{#prefill-adaptive-form-fields}

## Inleiding {#introduction}

U kunt de velden van een adaptief formulier vooraf invullen met bestaande gegevens. Wanneer een gebruiker een formulier opent, worden de waarden voor die velden vooraf ingevuld. Als u gegevens vooraf wilt invullen in een adaptief formulier, maakt u de gebruikersgegevens beschikbaar als een vooraf ingevulde XML/JSON in de indeling die voldoet aan de vooraf ingevulde gegevensstructuur van adaptieve formulieren.

## Structuur van vooraf ingevulde gegevens {#the-prefill-structure}

Een adaptief formulier kan bestaan uit gebonden en niet-gebonden velden. Gebonden velden zijn velden die worden gesleept vanaf het tabblad Inhoudszoeker en die een niet-lege `bindRef` eigenschapswaarde bevatten in het dialoogvenster voor het bewerken van velden. Niet-gebonden velden worden rechtstreeks vanuit de deelbrowser van Sidetrap gesleept en hebben een lege `bindRef` waarde.

U kunt zowel gebonden als niet-gebonden velden van een adaptief formulier vooraf invullen. De vooraf ingevulde gegevens bevatten de secties afBoundData en afUnBoundData om zowel gebonden als niet-gebonden velden van een adaptief formulier vooraf in te vullen. De `afBoundData` sectie bevat de vooraf ingevulde gegevens voor gebonden velden en deelvensters. Deze gegevens moeten voldoen aan het bijbehorende formuliermodelschema:

* Gebruik voor adaptieve formulieren met de [XFA-formuliersjabloon](../../forms/using/prepopulate-adaptive-form-fields.md)de vooraf ingevulde XML-code die compatibel is met het gegevensschema van de XFA-sjabloon.
* Gebruik voor adaptieve formulieren met [XML-schema](#xml-schema-af)de vooraf ingevulde XML-indeling die compatibel is met de XML-schemastructuur.
* Gebruik voor adaptieve formulieren met [JSON-schema](#json-schema-based-adaptive-forms)de Prefill JSON-compatibel met het JSON-schema.
* Gebruik voor adaptieve formulieren met FDM-schema de Prefill JSON die compatibel is met het FDM-schema.
* Voor adaptieve formulieren zonder [formuliermodel](#adaptive-form-with-no-form-model)zijn er geen gebonden gegevens. Elk veld is een niet-gebonden veld en wordt voorgevuld met de niet-gebonden XML.

### Voorbeeld van vooraf ingevulde XML-structuur {#sample-prefill-xml-structure}

```xml
<?xml version="1.0" encoding="UTF-8"?>
<afData>
  <afBoundData>
     <employeeData>
        .
     </employeeData>
  </afBoundData>

  <afUnboundData>
    <data>
      <textbox>Hello World</textbox>
         .
         .
      <numericbox>12</numericbox>
         . 
         .              
    </data>
  </afUnboundData>
</afData>
```

### Voorbeeld van JSON-structuur vooraf invullen {#sample-prefill-json-structure}

```
{
   "afBoundData": {
      "employeeData": { }
   },
   "afUnboundData": {
      "data": {
         "textbox": "Hello World",
         "numericbox": "12"
      }
   }
}
```

Voor gebonden velden met dezelfde bindref- of niet-gebonden velden met dezelfde naam worden de gegevens in de XML-tag of het JSON-object in alle velden ingevuld. Twee velden in een formulier worden bijvoorbeeld toegewezen aan de naam `textbox` in de vooraf ingevulde gegevens. Als tijdens runtime het eerste tekstvak A bevat, wordt A automatisch ingevuld in het tweede tekstvak. Deze koppeling wordt actieve koppeling van adaptieve formuliervelden genoemd.

### Adaptief formulier met XFA-formuliersjabloon {#xfa-based-af}

De structuur van vooraf ingevulde XML en de ingediende XML voor op XFA gebaseerde adaptieve formulieren is als volgt:

* **XML-structuur** vooraf invullen: Het vooraf ingevulde XML-formulier voor op XFA gebaseerde adaptieve formulieren moet voldoen aan het gegevensschema van de XFA-formuliersjabloon. Als u niet-gebonden velden vooraf wilt invullen, plaatst u de vooraf ingevulde XML-structuur in een `/afData/afBoundData` label.

* **Verzonden XML-structuur**: Wanneer geen vooraf ingevulde XML wordt gebruikt, bevat de voorgelegde XML gegevens voor zowel gebonden als niet-gebonden velden in `afData` wrapper tag. Als een vooraf ingevulde XML wordt gebruikt, heeft het voorgelegde XML-bestand dezelfde structuur als de vooraf ingevulde XML. Als de vooraf ingevulde XML begint met de `afData` hoofdtag, heeft de uitvoer-XML ook dezelfde indeling. Als de vooraf ingevulde XML geen `afData/afBoundData`omslag heeft en in plaats daarvan direct van de markering van de schemawortel begint zoals `employeeData`, begint voorgelegde XML ook met de `employeeData` markering.

Prefill-Submit-Data-ContentPackage.zip

[Bestandsvoorbeeld](assets/prefill-submit-data-contentpackage.zip)ophalen met vooraf ingevulde gegevens en verzonden gegevens

### Adaptieve formulieren op basis van een XML-schema {#xml-schema-af}

De structuur van vooraf ingevulde XML en verzonden XML voor adaptieve formulieren op basis van het XML-schema is als volgt:

* **Vooraf ingevulde XML-structuur**: De vooraf ingevulde XML moet compatibel zijn met het bijbehorende XML-schema. Als u niet-gebonden velden vooraf wilt invullen, plaatst u de vooraf ingevulde XML-structuur in de tag /afData/afBoundData.
* **Verzonden XML-structuur**: als er geen vooraf ingevulde XML wordt gebruikt, bevat de verzonden XML gegevens voor zowel gebonden als niet-gebonden velden in de `afData` omvattende tag. Als de vooraf ingevulde XML wordt gebruikt, heeft het voorgelegde XML-bestand dezelfde structuur als de vooraf ingevulde XML. Als de vooraf ingevulde XML begint met de `afData` hoofdtag, heeft de uitvoer-XML dezelfde indeling. Als de vooraf ingevulde XML geen `afData/afBoundData` omslag heeft en in plaats daarvan direct van de markering van de schemawortel begint zoals `employeeData`, begint voorgelegde XML ook met de `employeeData` markering.

```xml
<?xml version="1.0" encoding="utf-8" ?> 
<xs:schema targetNamespace="https://adobe.com/sample.xsd"
            xmlns="https://adobe.com/sample.xsd"
            xmlns:xs="https://www.w3.org/2001/XMLSchema">
 
    <xs:element name="sample" type="SampleType"/>
         
    <xs:complexType name="SampleType">
        <xs:sequence>
            <xs:element name="noOfProjectsAssigned" type="xs:string"/>
        </xs:sequence>
    </xs:complexType>
</xs:schema>
```

Voor velden waarvan het model het XML-schema is, worden de gegevens voorgevuld in de `afBoundData` tag, zoals in de voorbeeld-XML hieronder wordt getoond. Deze kan worden gebruikt voor het vooraf invullen van een adaptief formulier met een of meer niet-gebonden tekstvelden.

```xml
<?xml version="1.0" encoding="UTF-8"?><afData>
  <afUnboundData>
    <data>
      <textbox>Ignorance is bliss :) </textbox>
    </data>
  </afUnboundData>
  <afBoundData>
    <data>
      <noOfProjectsAssigned>twelve</noOfProjectsAssigned>
    </data>
  </afBoundData>
</afData>
```

>[!NOTE]
>
>Het wordt aanbevolen geen niet-gebonden velden te gebruiken in gebonden deelvensters (deelvensters met niet-lege deelvensters `bindRef` die zijn gemaakt door componenten te slepen van het tabblad Sidetrap of Gegevensbronnen). Hierdoor kunnen gegevens van deze niet-gebonden velden verloren gaan. Daarnaast wordt aanbevolen dat de namen van de velden uniek zijn in het formulier, met name voor niet-gebonden velden.

#### Een voorbeeld zonder de omslag afData en afBoundData {#an-example-without-afdata-and-afbounddata-wrapper}

```xml
<?xml version="1.0" encoding="UTF-8"?><config>
 <assignmentDetails descriptionOfAssignment="Some Science Project" durationOfAssignment="34" financeRelatedProject="1" name="Lisa" numberOfMentees="1"/>
 <assignmentDetails descriptionOfAssignment="Kidding, right?" durationOfAssignment="4" financeRelatedProject="1" name="House" numberOfMentees="3"/>
</config>
```

### Adaptieve formulieren op basis van JSON-schema {#json-schema-based-adaptive-forms}

Voor adaptieve formulieren op basis van JSON-schema wordt de structuur van de prefill JSON en de ingediende JSON hieronder beschreven. Zie Aangepaste formulieren [maken met JSON-schema](../../forms/using/adaptive-form-json-schema-form-model.md)voor meer informatie.

* **JSON-structuur** vooraf invullen: De Prefill JSON moet voldoen aan het JSON-schema. Naar keuze, kan het in het /afData/afBoundData Voorwerp worden verpakt als u niet verbindende gebieden eveneens wilt vooraf invullen.
* **Ingediende JSON-structuur**: als er geen Prefill JSON wordt gebruikt, bevat de verzonden JSON gegevens voor zowel gebonden als niet-gebonden velden in de omsluitende tag afData. Als de Prefill JSON wordt gebruikt, heeft de verzonden JSON dezelfde structuur als de Prefill JSON. Als de Prefill JSON begint met het afData-hoofdobject, heeft de uitvoer-JSON dezelfde indeling. Als de prefill JSON geen afData/afBoundData omslag heeft en in plaats daarvan direct van het schemawortelvoorwerp zoals gebruiker begint, begint voorgelegde JSON ook met het gebruikersvoorwerp.

```
{
    "id": "https://some.site.somewhere/entry-schema#",
    "$schema": "https://json-schema.org/draft-04/schema#",
    "type": "object",
    "properties": {
        "address": {
            "type": "object",
            "properties": { 
    "name": {
     "type": "string"
    },
    "age": {
     "type": "integer"
}}}}}
```

Voor velden die het JSON-schemamodel gebruiken, worden de gegevens vooraf ingevuld in het object afBoundData, zoals in het voorbeeld JSON hieronder wordt getoond. Deze kan worden gebruikt voor het vooraf invullen van een adaptief formulier met een of meer niet-gebonden tekstvelden. Hieronder ziet u een voorbeeld van gegevens met `afData/afBoundData` omloop:

```
{
  "afData": {
    "afUnboundData": {
      "data": { "textbox": "Ignorance is bliss :) " }
    },
    "afBoundData": {
      "data": { {
   "user": {
    "address": {
     "city": "Noida",
     "country": "India"
}}}}}}}
```

Hieronder ziet u een voorbeeld zonder `afData/afBoundData` omloop:

```
{
 "user": {
  "address": {
   "city": "Noida",
   "country": "India"
}}}
```

>[!NOTE]
>
>Het gebruik van niet-gebonden velden in gebonden deelvensters (deelvensters met niet-lege bindRef die zijn gemaakt door het slepen van componenten van het tabblad Sidetrap of Gegevensbronnen) wordt **niet** aanbevolen, omdat dit gegevensverlies van de niet-gebonden velden tot gevolg kan hebben. Het wordt aanbevolen unieke veldnamen te hebben in het formulier, vooral voor niet-gebonden velden.

### Adaptief formulier zonder formuliermodel {#adaptive-form-with-no-form-model}

Voor adaptieve formulieren zonder formuliermodel staan de gegevens voor alle velden onder de `<data>` code `<afUnboundData> tag`.

Let ook op het volgende:

De XML-labels voor de gebruikersgegevens die voor verschillende velden worden verzonden, worden gegenereerd met de naam van de velden. De veldnamen moeten daarom uniek zijn.

```xml
<?xml version="1.0" encoding="UTF-8"?><afData>
  <afUnboundData>
    <data>
      <radiobutton>2</radiobutton>
      <repeatable_panel_no_form_model>
        <numericbox>12</numericbox>
      </repeatable_panel_no_form_model>
      <repeatable_panel_no_form_model>
        <numericbox>21</numericbox>
      </repeatable_panel_no_form_model>
      <checkbox>2</checkbox>
      <textbox>Nopes</textbox>
    </data>
  </afUnboundData>
  <afBoundData/>
</afData>
```

## Prefill-service configureren met Configuratiebeheer {#configuring-prefill-service-using-configuration-manager}

Om de prefill dienst toe te laten, specificeer de Standaard Prefill Configuratie van de Dienst in de Configuratie van de Console van AEM Web. Gebruik de volgende stappen om de Prefill dienst te vormen:

>[!NOTE]
>
>Prefill Service Configuration is van toepassing op adaptieve formulieren, HTML5-formulieren en HTML5-formuliersets.

1. Open **[!UICONTROL de Configuratie]** van de Console van de Ervaring van Adobe Manager Web door URL te gebruiken:\
   https://&lt;server>:&lt;port>/system/console/configMgr
1. Zoek en open **[!UICONTROL Standaard Prefill de Configuratie]** van de Dienst.

   ![Configuratie vooraf invullen](assets/prefill_config_new.png)

1. Voer de gegevenslocatie of een regex (reguliere expressie) in voor de locaties **van** gegevensbestanden. Voorbeelden van geldige locaties voor gegevensbestanden zijn:

   * file:///C:/Users/public/Document/Prefill/.*
   * https://localhost:8000/somesamplexmlfile.xml
   >[!NOTE]
   >
   >Standaard is Prefill toegestaan via crx-bestanden voor alle typen adaptieve formulieren (XSD, XDP, JSON, FDM en geen gebaseerd formuliermodel). Vooraf invullen is alleen toegestaan met JSON- en XML-bestanden.

1. De prefill-service is nu geconfigureerd voor uw formulier.

   >[!NOTE]
   >
   >Het crx-protocol zorgt voor de beveiliging van vooraf ingevulde gegevens en is daarom standaard toegestaan. Prefilling via andere protocollen met behulp van generieke regex kan kwetsbaarheid veroorzaken. Geef in de configuratie een veilige URL-configuratie op om uw gegevens te beveiligen.

## Het merkwaardige geval van herhaalbare deelvensters {#the-curious-case-of-repeatable-panels}

Over het algemeen worden gebonden (formulierschema) en niet-gebonden velden gemaakt in dezelfde adaptieve vorm, maar het volgende is een paar uitzonderingen voor het geval de gebonden velden herhaalbaar zijn:

* Niet-gebonden herhaalbare deelvensters worden niet ondersteund voor adaptieve formulieren met de XFA-formuliersjabloon, XSD, JSON-schema of FDM-schema.
* Gebruik geen niet-gebonden velden in gebonden herhaalbare deelvensters.

>[!NOTE]
>
>Als vuistregel geldt dat gebonden en niet-gebonden velden niet door elkaar mogen worden gebruikt als ze doorsnede hebben in gegevens die door de eindgebruiker in niet-gebonden velden worden ingevuld. Indien mogelijk, zou u het schema of het XFA vormmalplaatje moeten wijzigen en een ingang voor niet verbindende gebieden toevoegen, zodat het ook verbindend wordt en zijn gegevens zoals andere gebieden in voorgelegde gegevens beschikbaar zijn.

## Ondersteunde protocollen voor het vooraf invullen van gebruikersgegevens {#supported-protocols-for-prefilling-user-data}

Adaptieve formulieren kunnen worden voorgevuld met gebruikersgegevens in de indeling voor vooraf ingevulde gegevens via de volgende protocollen wanneer ze zijn geconfigureerd met geldige regex:

### Het protocol crx:// {#the-crx-protocol}

```xml
https://localhost:4502/content/forms/af/xml.html?wcmmode=disabled&dataRef=crx:///tmp/fd/af/myassets/sample.xml
```

Het opgegeven knooppunt moet een eigenschap hebben die wordt aangeroepen `jcr:data` en de gegevens bevatten.

### Het protocol file:// {#the-file-protocol-nbsp}

```xml
https://localhost:4502/content/forms/af/someAF.html?wcmmode=disabled&dataRef=file:///C:/Users/form-user/Downloads/somesamplexml.xml
```

Het bestand waarnaar wordt verwezen, moet zich op dezelfde server bevinden.

### Het protocol https:// {#the-http-protocol}

```xml
https://localhost:4502/content/forms/af/xml.html?wcmmode=disabled&dataRef=https://localhost:8000/somesamplexmlfile.xml
```

### Het protocol service:// {#the-service-protocol}

```xml
https://localhost:4502/content/forms/af/abc.html?wcmmode=disabled&dataRef=service://[SERVICE_NAME]/[IDENTIFIER]
```

* SERVICE_NAME verwijst naar de naam van de prefill dienst OSGI. Zie Een vooraf ingevulde service [maken en uitvoeren](../../forms/using/prepopulate-adaptive-form-fields.md#create-and-run-a-prefill-service).
* IDENTIFIER verwijst naar om het even welke meta-gegevens die door de Prefill dienst worden vereist OSGI om de Prefill gegevens te halen. Een id voor de aangemelde gebruiker is een voorbeeld van metagegevens die kunnen worden gebruikt.

>[!NOTE]
>
>Het doorgeven van verificatieparameters wordt niet ondersteund.

### Gegevenskenmerk instellen in slingRequest {#setting-data-attribute-in-slingrequest}

U kunt het `data` kenmerk ook instellen in `slingRequest`, waar het `data` kenmerk een tekenreeks met XML of JSON is, zoals in de voorbeeldcode hieronder wordt getoond (Voorbeeld is voor XML):

```java
<%
           String dataXML="<afData>" +
                            "<afUnboundData>" +
                                "<data>" +
                                    "<first_name>"+ "Tyler" + "</first_name>" +
                                    "<last_name>"+ "Durden " + "</last_name>" +
                                    "<gender>"+ "Male" + "</gender>" +
                                    "<location>"+ "Texas" + "</location>" +
                                    "</data>" +
                            "</afUnboundData>" +
                        "</afData>";
        slingRequest.setAttribute("data", dataXML);
%>
```

U kunt een eenvoudige XML- of JSON-tekenreeks met al uw gegevens schrijven en deze in slingRequest instellen. Dit kan gemakkelijk in uw renderer JSP voor om het even welke component worden gedaan, die u in de pagina wilt omvatten waar u het slingRequest gegevensattribuut kunt plaatsen.

Bijvoorbeeld, waar u een specifiek ontwerp voor uw pagina met een specifiek type van kopbal wilt. Hiervoor kunt u uw eigen code schrijven `header.jsp`, die u kunt opnemen in de paginacomponent en het `data` kenmerk instellen.

Een ander goed voorbeeld is een gebruiksgeval waarin u gegevens over aanmelding via sociale accounts, zoals Facebook, Twitter of LinkedIn, vooraf wilt invullen. In dit geval kunt u een eenvoudige JSP in opnemen `header.jsp`, die gegevens van de gebruikersaccount ophaalt en de gegevensparameter instelt.

prefill-page component.zip

[File](assets/prefill-page-component.zip)Sample prefill.jsp ophalen in paginacomponent

## AEM Forms Custom Prefill Service {#aem-forms-custom-prefill-service}

U kunt de douane vooraf ingevulde dienst voor de scenario&#39;s gebruiken, waar u constant gegevens van een vooraf bepaalde bron leest. De Prefill-service leest gegevens uit gedefinieerde gegevensbronnen en vult de velden van het adaptieve formulier vooraf in met de inhoud van het Prefill-gegevensbestand. Hiermee kunt u ook vooraf ingevulde gegevens permanent koppelen aan een adaptief formulier.

### Een vooraf ingevulde service maken en uitvoeren {#create-and-run-a-prefill-service}

De prefill dienst is de dienst OSGi en door bundel OSGi verpakt. U maakt de OSGi-bundel, uploadt en installeert deze naar AEM Forms-bundels. Voordat u begint met het maken van de bundel:

* [De SDK van de AEM Forms Client downloaden](https://helpx.adobe.com/aem-forms/kb/aem-forms-releases.html)
* [Het tekstbouwsteenpakket downloaden](../../forms/using/prepopulate-adaptive-form-fields.md#main-pars-download-section-711716493)

* Plaats het gegevensbestand (vooraf ingevulde gegevens) in crx-bewaarplaats. U kunt het bestand op elke locatie in de map \contents van de crx-opslagplaats plaatsen.

[Bestand ophalen](assets/prefill-sumbit-xmlsandcontentpackage.zip)

#### Een vooraf ingevulde service maken {#create-a-prefill-service}

Het bouwsteenpakket (voorbeeldenservicepakket) bevat een voorbeeldimplementatie van de Prefill-service AEM Forms. Open het tekstbouwsteenpakket in een code-editor. Open bijvoorbeeld het bouwsteenproject in Eclipse en bewerk het. Nadat u het bouwsteenpakket in een coderedacteur opent, voer de volgende stappen uit om de dienst tot stand te brengen.

1. Open het bestand src\main\java\com\adobe\test\Prefill.java voor bewerking.
1. Stel in de code de waarde in van:

   * `nodePath:` De knooppuntvariabele die naar de crx-gegevensopslagplaats wijst bevat weg van het gegevens (prefill) dossier. Bijvoorbeeld /content/prefilldata.xml
   * `label:` De labelparameter geeft de weergavenaam van de service op. Bijvoorbeeld, de StandaardVooraf ingevulde Dienst

1. Sla het `Prefill.java` bestand op en sluit het.
1. Voeg het `AEM Forms Client SDK` pakket aan de bouwstijlweg van het bouwsteenproject toe.
1. Compileer het project en creeer .jar voor de bundel.

#### De Prefill-service starten en gebruiken {#start-and-use-the-prefill-service}

Als u de Prefill-service wilt starten, uploadt u het JAR-bestand naar de webconsole van AEM Forms en activeert u de service. De service verschijnt nu in de editor voor aangepaste formulieren. Een vooraf ingevulde service koppelen aan een adaptief formulier:

1. Open het aangepaste formulier in de Forms Editor en open het deelvenster Eigenschappen voor de Formuliercontainer.
1. Navigeer in de eigenschappenconsole naar de AEM Forms-container > Basic > Prefill Service.
1. Selecteer de standaardvoorgevulde service en klik op **[!UICONTROL Opslaan]**. De service is gekoppeld aan het formulier.

