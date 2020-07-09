---
title: Aangepaste verzendactie schrijven voor adaptieve formulieren
seo-title: Aangepaste verzendactie schrijven voor adaptieve formulieren
description: Met AEM Forms kunt u een aangepaste handeling Verzenden maken voor adaptieve formulieren. In dit artikel wordt de procedure beschreven voor het toevoegen van aangepaste verzendactie voor adaptieve formulieren.
seo-description: Met AEM Forms kunt u een aangepaste handeling Verzenden maken voor adaptieve formulieren. In dit artikel wordt de procedure beschreven voor het toevoegen van aangepaste verzendactie voor adaptieve formulieren.
uuid: fd8e1dac-b997-4e86-aaf6-3507edcb3070
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: customization
discoiquuid: 2a2e1156-4a54-4b0a-981c-d527fe22a27e
docset: aem65
translation-type: tm+mt
source-git-commit: a399b2cb2e0ae4f045f7e0fddf378fdcd80bb848
workflow-type: tm+mt
source-wordcount: '1660'
ht-degree: 0%

---


# Aangepaste verzendactie schrijven voor adaptieve formulieren{#writing-custom-submit-action-for-adaptive-forms}

Voor adaptieve formulieren moeten handelingen worden verzonden om door de gebruiker opgegeven gegevens te verwerken. Een handeling Verzenden bepaalt de taak die wordt uitgevoerd voor de gegevens die u verzendt met behulp van een adaptief formulier. Adobe Experience Manager (AEM) bevat [OOTB-verzendacties](../../forms/using/configuring-submit-actions.md) die aangepaste taken demonstreren die u kunt uitvoeren met behulp van door de gebruiker verzonden gegevens. U kunt bijvoorbeeld taken uitvoeren, zoals het verzenden van e-mail of het opslaan van de gegevens.

## Workflow voor een handeling Verzenden {#workflow-for-a-submit-action}

Het stroomschema geeft de workflow weer voor een handeling Verzenden die wordt geactiveerd wanneer u op de **[!UICONTROL Submit]** knop klikt in een adaptief formulier. De bestanden in de component Bestandsbijlage worden geüpload naar de server en de formuliergegevens worden bijgewerkt met de URL&#39;s van de geüploade bestanden. Binnen de client worden de gegevens opgeslagen in de JSON-indeling. De client verzendt een Ajax-aanvraag naar een interne servlet die de opgegeven gegevens in massa neemt en deze in XML-indeling retourneert. De client sorteert deze gegevens met actievelden. De gegevens worden via een handeling Formulier verzenden verzonden naar de uiteindelijke servlet (Guide verzendt servlet). Dan, door:sturen servlet de controle aan de Submit actie. De handeling Verzenden kan het verzoek doorsturen naar een andere kiesbron of de browser omleiden naar een andere URL.

![Stroomdiagram dat de workflow voor een verzendactie weergeeft](assets/diagram1.png)

### XML-gegevensindeling {#xml-data-format}

De XML-gegevens worden naar de servlet verzonden met behulp van de **`jcr:data`** aanvraagparameter. Verzendhandelingen hebben toegang tot de parameter om de gegevens te verwerken. In de volgende code wordt de indeling van de XML-gegevens beschreven. De velden die aan het formuliermodel zijn gebonden, worden weergegeven in de **`afBoundData`** sectie. Niet-gebonden velden worden weergegeven in de `afUnoundData`sectie. Zie `data.xml` Inleiding tot het vooraf invullen van aangepaste formuliervelden [voor meer informatie over de indeling van het](../../forms/using/prepopulate-adaptive-form-fields.md)bestand.

```xml
<?xml ?>
<afData>
<afUnboundData>
<data>
<field1>value</field2>
<repeatablePanel>
    <field2>value</field2>
</repeatablePanel>
<repeatablePanel>
    <field2>value</field2>
</repeatablePanel>
</data>
</afUnboundData>
<afBoundData>
<!-- xml corresponding to the Form Model /XML Schema -->
</afBoundData>
</afData>
```

### Actievelden {#action-fields}

Met een handeling Verzenden kunt u verborgen invoervelden (met de HTML- [invoertag](https://developer.mozilla.org/en/docs/Web/HTML/Element/Input) ) toevoegen aan het gerenderde formulier HTML. Deze verborgen velden kunnen waarden bevatten die nodig zijn tijdens de verwerking van formulierverzendingen. Bij het verzenden van het formulier worden deze veldwaarden teruggeplaatst als aanvraagparameters die de handeling Verzenden kan gebruiken tijdens het verzenden. De invoervelden worden actievelden genoemd.

Met een handeling Verzenden die ook de tijd vastlegt die nodig is om een formulier in te vullen, kunt u bijvoorbeeld verborgen invoervelden `startTime` en `endTime`.

Een script kan de waarden van de velden `startTime` `endTime` en de velden opgeven wanneer het formulier wordt gerenderd en vóór het verzenden van het formulier. Met het handelingsscript Verzenden `post.jsp` kunt u deze velden vervolgens openen met behulp van aanvraagparameters en de totale tijd berekenen die nodig is om het formulier in te vullen.

### Bestandsbijlagen {#file-attachments}

Verzendhandelingen kunnen ook de bestandsbijlagen gebruiken die u uploadt met de component Bestandsbijlage. Submit-handelingsscripts hebben toegang tot deze bestanden met behulp van de sling [RequestParameter-API](https://sling.apache.org/apidocs/sling5/org/apache/sling/api/request/RequestParameter.html). Met [de methode isFormField](https://sling.apache.org/apidocs/sling5/org/apache/sling/api/request/RequestParameter.html#isFormField()) van de API kunt u gemakkelijker vaststellen of de aanvraagparameter een bestand of een formulierveld is. U kunt de parameters van het Verzoek in een Submit actie herhalen om de parameters van de Bijlage van het Dossier te identificeren.

De volgende voorbeeldcode identificeert de bestandsbijlagen in de aanvraag. Vervolgens worden de gegevens in het bestand gelezen met de API [](https://sling.apache.org/apidocs/sling5/org/apache/sling/api/request/RequestParameter.html#get())Get. Ten slotte wordt een object Document gemaakt met behulp van de gegevens en toegevoegd aan een lijst.

```java
RequestParameterMap requestParameterMap = slingRequest.getRequestParameterMap();
for (Map.Entry<String, RequestParameter[]> param : requestParameterMap.entrySet()) {
    RequestParameter rpm = param.getValue()[0];
    if(!rpm.isFormField()) {
        fileAttachments.add(new Document(rpm.get()));
    }
}
```

### Pad doorsturen en URL omleiden {#forward-path-and-redirect-url}

Nadat de vereiste actie is uitgevoerd, stuurt de Submit servlet de aanvraag door naar het voorwaartse pad. Een handeling gebruikt de setForwardPath API om het voorwaartse pad in te stellen in de Guide Submit servlet.

Als de handeling geen voorwaarts pad biedt, leidt de verzendserver de browser om met de Redirect URL. De auteur configureert de omleidings-URL met behulp van de configuratie Bedankt voor de pagina in het dialoogvenster Formulier bewerken. U kunt de Redirect URL ook configureren via de handeling Verzenden of de setRedirectUrl-API in het dialoogvenster Guide Verzenden. U kunt de parameters van het Verzoek die naar Redirect URL worden verzonden ook vormen gebruikend setRedirectParameters API in de Gids Submit servlet.

>[!NOTE]
>
>Een auteur verstrekt Redirect URL (gebruikend de Dank u Configuratie van de Pagina). [OOTB verzendt Acties](../../forms/using/configuring-submit-actions.md) gebruikt Redirect URL om browser van het middel om te leiden dat de voorwaartse weg verwijzingen.
>
>U kunt een douane schrijven voorlegt actie die een verzoek aan een middel of servlet door:sturen. Adobe raadt aan dat het script dat de verwerking van bronnen uitvoert voor het voorwaartse pad, de aanvraag omleidt naar de Redirect URL wanneer de verwerking is voltooid.

## Handeling verzenden {#submit-action}

Een handeling Verzenden is een tekenreeks:Map die het volgende bevat:

* **addfields.jsp**: Dit script bevat de actievelden die tijdens de uitvoering aan het HTML-bestand worden toegevoegd. Gebruik dit script om verborgen invoerparameters toe te voegen die vereist zijn tijdens verzending in het script post.POST.jsp.
* **dialog.xml**: Dit script is vergelijkbaar met het dialoogvenster CQ-component. Het verstrekt configuratieinformatie die de auteur aanpast. De velden worden weergegeven op het tabblad Handelingen verzenden in het dialoogvenster Formulier bewerken Adaptief wanneer u de handeling Verzenden selecteert.
* **post.POST.jsp**: Het Submit servlet roept dit manuscript met de gegevens die u en de extra gegevens in de vorige secties indient. Elke vermelding van het uitvoeren van een handeling op deze pagina houdt in dat het script post.POST.jsp wordt uitgevoerd. Als u de handeling Verzenden wilt registreren met de adaptieve formulieren die u wilt weergeven in het dialoogvenster Formulier bewerken, voegt u de volgende eigenschappen toe aan de lijst:Map:

   * **guideComponentType** van type String en value **fd/af/components/guidesubmittype**
   * **guideDataModel** van het type String die het type adaptief formulier opgeeft waarvoor de handeling Verzenden van toepassing is. **xfa** wordt ondersteund voor op XFA gebaseerde adaptieve formulieren, terwijl **xsd** wordt ondersteund voor op XSD gebaseerde adaptieve formulieren. **basic** wordt ondersteund voor adaptieve formulieren die geen XDP of XSD gebruiken. Voeg de corresponderende tekenreeksen toe om de handeling weer te geven op meerdere typen adaptieve formulieren. Scheid elke tekenreeks door een komma. Als u bijvoorbeeld een handeling zichtbaar wilt maken op op XFA- en XSD-gebaseerde adaptieve formulieren, geeft u de waarden **xfa** en **xsd** op.

   * **jcr:beschrijving** van het type String. De waarde van deze eigenschap wordt weergegeven in de actielijst Verzenden op het tabblad Handelingen verzenden van het dialoogvenster Formulier bewerken Adaptief. De OOTB-acties zijn aanwezig in de CRX-opslagplaats op de locatie **/libs/fd/af/components/guidesubmittype**.

## Een aangepaste verzendhandeling maken {#creating-a-custom-submit-action}

Voer de volgende stappen uit om een aangepaste handeling Verzenden te maken die de gegevens opslaat in de CRX-opslagplaats en u vervolgens een e-mail stuurt. Het adaptieve formulier bevat de OOTB-actie Store Content (afgekeurd) waarmee de gegevens worden opgeslagen in de CRX-opslagplaats. Daarnaast biedt CQ een [e-mailAPI](https://docs.adobe.com/docs/en/cq/current/javadoc/com/day/cq/mailer/package-summary.html) die kan worden gebruikt voor het verzenden van e-mails. Voordat u de e-mail-API gebruikt, [configureert]u (https://docs.adobe.com/docs/en/cq/current/administering/notification.html?wcmmode=disabled#Configuring de e-mailservice) de Day CQ Mail-service via de systeemconsole. U kunt de actie Store Content (afgekeurd) opnieuw gebruiken om de gegevens in de opslagplaats op te slaan. De actie Store Content (afgekeurd) is beschikbaar op de locatie /libs/fd/af/components/guidesubmittype/store in de CRX-opslagruimte.

1. Meld u aan bij CRXDE Lite op de URL https://&lt;server>:&lt;port>/crx/de/index.jsp. Maak een knooppunt met de eigenschap sling:Folder en name store_and_mail in de map /apps/custom_submit_action. Maak de map custom_submit_action als deze nog niet bestaat.

   ![Screenshot die het maken van een knooppunt met de eigenschap sling:Folder weergeeft](assets/step1.png)

1. **Geef de verplichte configuratievelden op.**

   Voeg de configuratie toe die de winkelactie vereist. Kopieer het knooppunt **cq:dialog** van de actie Store van /libs/fd/af/components/guidesubmittype/store naar de map action op /apps/custom_submit_action/store_and_email.

   ![Screenshot met het kopiëren van het dialoogvenster naar de map action.](assets/step2.png)

1. **Geef configuratievelden op om de auteur te vragen of er een e-mailconfiguratie nodig is.**

   Het adaptieve formulier bevat ook een e-mailactie die e-mailberichten naar gebruikers verzendt. Pas deze actie aan op basis van uw vereisten. Navigeer naar /libs/fd/af/components/guidesubmittype/email/dialog. Kopieer de knooppunten in het cq:dialog-knooppunt naar cq:dialog-knooppunt van de handeling Verzenden (/apps/custom_submit_action/store_and_email/dialog).

   ![De e-mailactie aanpassen](assets/step3.png)

1. **De handeling beschikbaar stellen in het dialoogvenster Formulier bewerken Adaptief.**

   Voeg de volgende eigenschappen in store_and_email knoop toe:

   * **guideComponentType** van type **String** en value **fd/af/components/guidesubmittype**

   * **guideDataModel** van het type **String** en value **xfa, xsd, basic**

   * **jcr:beschrijving** van het type **String** en value **Store en Email Action**

1. Open een adaptief formulier. Klik op de knop **Bewerken** naast **Start** om het dialoogvenster **Bewerken** van de adaptieve formuliercontainer te openen. De nieuwe handeling wordt weergegeven op het tabblad **Handelingen** verzenden. Als u de handeling **Winkel en E-mail** selecteert, wordt de configuratie weergegeven die in het dialoogvenster is toegevoegd.

   ![Dialoogvenster Handelingsconfiguratie verzenden](assets/store_and_email_submit_action_dialog.jpg)

1. **Gebruik de handeling om een taak te voltooien.**

   Voeg het script post.POST.jsp toe aan uw handeling. (/apps/custom_submit_action/store_and_mail/).

   Voer de actie OOTB Store uit (script post.POST.jsp). Gebruik de [FormsHelper.runAction](https://docs.adobe.com/docs/en/cq/current/javadoc/com/day/cq/wcm/foundation/forms/FormsHelper.html#runAction(java.lang.String, java.lang.String, org.apache.sling.api.resource.Resource, org.apache.sling.api.SlingHttpServletRequest, org.apache.sling.api.SlingHttpServletResponse) API die CQ in uw code verstrekt om de opslag in werking te stellen handeling. Voeg de volgende code in uw JSP dossier toe:

   `FormsHelper.runAction("/libs/fd/af/components/guidesubmittype/store", "post", resource, slingRequest, slingResponse);`

   Om e-mail te verzenden, leest de code het e-mailadres van de ontvanger van de configuratie. Om de configuratiewaarde in het manuscript van de actie te halen, lees de eigenschappen van het huidige middel gebruikend de volgende code. Op dezelfde manier kunt u de andere configuratiedossiers lezen.

   `ValueMap properties = ResourceUtil.getValueMap(resource);`

   `String mailTo = properties.get("mailTo");`

   Tot slot gebruikt u de CQ Mail-API om de e-mail te verzenden. Gebruik de [klasse SimpleEmail](https://commons.apache.org/proper/commons-email/apidocs/org/apache/commons/mail/SimpleEmail.html) om het E-mailobject te maken zoals hieronder wordt weergegeven:

   >[!NOTE]
   >
   >Zorg ervoor dat het JSP-bestand de naam post.POST.jsp heeft.

   ```java
   <%@include file="/libs/fd/af/components/guidesglobal.jsp" %>
   <%@page import="com.day.cq.wcm.foundation.forms.FormsHelper,
          org.apache.sling.api.resource.ResourceUtil,
          org.apache.sling.api.resource.ValueMap,
                   com.day.cq.mailer.MessageGatewayService,
     com.day.cq.mailer.MessageGateway,
     org.apache.commons.mail.Email,
                   org.apache.commons.mail.SimpleEmail" %>
   <%@taglib prefix="sling"
                   uri="https://sling.apache.org/taglibs/sling/1.0" %>
   <%@taglib prefix="cq"
                   uri="https://www.day.com/taglibs/cq/1.0"
   %>
   <cq:defineObjects/>
   <sling:defineObjects/>
   <%
           String storeContent =
                       "/libs/fd/af/components/guidesubmittype/store";
           FormsHelper.runAction(storeContent, "post", resource,
                                   slingRequest, slingResponse);
    ValueMap props = ResourceUtil.getValueMap(resource);
    Email email = new SimpleEmail();
    String[] mailTo = props.get("mailto", new String[0]);
    email.setFrom((String)props.get("from"));
           for (String toAddr : mailTo) {
               email.addTo(toAddr);
      }
    email.setMsg((String)props.get("template"));
    email.setSubject((String)props.get("subject"));
    MessageGatewayService messageGatewayService =
                       sling.getService(MessageGatewayService.class);
    MessageGateway messageGateway =
                   messageGatewayService.getGateway(SimpleEmail.class);
    messageGateway.send(email);
   %>
   ```

   Selecteer de handeling in het adaptieve formulier. De actie verzendt een e-mail en slaat de gegevens op.

