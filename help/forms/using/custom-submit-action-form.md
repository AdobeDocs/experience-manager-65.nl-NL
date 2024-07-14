---
title: Aangepaste verzendactie schrijven voor adaptieve formulieren
description: Met AEM Forms kunt u aangepaste verzendactie maken voor adaptieve formulieren. In dit artikel wordt de procedure beschreven voor het toevoegen van aangepaste verzendactie voor adaptieve formulieren.
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: customization
docset: aem65
exl-id: 7c3d0dac-4e19-4eb3-a43d-909d526acd55
solution: Experience Manager, Experience Manager Forms
role: User, Developer
feature: Adaptive Forms,Foundation Components,Form Data Model
source-git-commit: 8a77756e8ba771c8de9950c2323bef8f23cc59b4
workflow-type: tm+mt
source-wordcount: '1541'
ht-degree: 0%

---

# Aangepaste verzendactie schrijven voor adaptieve formulieren{#writing-custom-submit-action-for-adaptive-forms}

| Versie | Artikelkoppeling |
| -------- | ---------------------------- |
| AEM as a Cloud Service | [ klik hier ](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/adaptive-forms-authoring/authoring-adaptive-forms-foundation-components/configure-submit-actions-and-metadata-submission/custom-submit-action-form.html) |
| AEM 6,5 | Dit artikel |

Voor adaptieve formulieren moeten handelingen worden verzonden om door de gebruiker opgegeven gegevens te verwerken. Een handeling Verzenden bepaalt de taak die wordt uitgevoerd voor de gegevens die u verzendt met behulp van een adaptief formulier. Adobe Experience Manager (AEM) omvat [ uit-van-de-doos acties ](../../forms/using/configuring-submit-actions.md) voorleggen die douanetaken tonen u het gebruiken van de user-submitted gegevens kunt uitvoeren. U kunt bijvoorbeeld taken uitvoeren, zoals het verzenden van e-mail of het opslaan van de gegevens.

## Workflow voor een handeling Verzenden {#workflow-for-a-submit-action}

Het stroomschema geeft de workflow weer voor een handeling Verzenden die wordt geactiveerd wanneer u op de knop **[!UICONTROL Submit]** klikt in een adaptief formulier. De bestanden in de component Bestandsbijlage worden geüpload naar de server en de formuliergegevens worden bijgewerkt met de URL&#39;s van de geüploade bestanden. Binnen de client worden de gegevens opgeslagen in de JSON-indeling. De client verzendt een Ajax-aanvraag naar een interne servlet die de opgegeven gegevens in massa neemt en deze in XML-indeling retourneert. De client sorteert deze gegevens met actievelden. De gegevens worden via een handeling Formulier verzenden verzonden naar de uiteindelijke servlet (Guide verzendt servlet). Dan, door:sturen servlet de controle aan de Submit actie. De handeling Verzenden kan het verzoek doorsturen naar een andere kiesbron of de browser omleiden naar een andere URL.

![ Stroomschema die het werkschema voor Submit actie ](assets/diagram1.png) afbeelden

### XML-gegevensindeling {#xml-data-format}

De XML-gegevens worden naar de servlet verzonden met behulp van de aanvraagparameter **`jcr:data`** . Verzendhandelingen hebben toegang tot de parameter om de gegevens te verwerken. In de volgende code wordt de indeling van de XML-gegevens beschreven. De velden die aan het formuliermodel zijn gebonden, worden weergegeven in de sectie **`afBoundData`** . De niet verbindende gebieden verschijnen in de `afUnoundData` sectie. Voor meer informatie over het formaat van het `data.xml` dossier, zie [ Inleiding aan prepopulating adaptieve vormgebieden ](../../forms/using/prepopulate-adaptive-form-fields.md).

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

Een voorlegt actie kan verborgen inputgebieden (gebruikend de HTML [ input ](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/Input) markering) aan teruggegeven vorm HTML toevoegen. Deze verborgen velden kunnen waarden bevatten die nodig zijn tijdens de verwerking van formulierverzendingen. Bij het verzenden van het formulier worden deze veldwaarden teruggeplaatst als aanvraagparameters die de handeling Verzenden kan gebruiken tijdens het verzenden. De invoervelden worden actievelden genoemd.

Met een handeling Verzenden die ook de tijd vastlegt die nodig is om een formulier in te vullen, kunt u bijvoorbeeld de verborgen invoervelden `startTime` en `endTime` toevoegen.

Een script kan de waarden van de velden `startTime` en `endTime` opgeven wanneer het formulier wordt gerenderd en vóór het verzenden van het formulier. Het ActionScript Verzenden `post.jsp` heeft vervolgens toegang tot deze velden met behulp van aanvraagparameters en kan de totale tijd berekenen die nodig is om het formulier in te vullen.

### Bestandsbijlagen {#file-attachments}

Verzendhandelingen kunnen ook de bestandsbijlagen gebruiken die u uploadt met de component Bestandsbijlage. Verzend actiemanuscripten tot deze dossiers kunnen toegang hebben gebruikend de het laten van [ RequestParameter API ](https://sling.apache.org/apidocs/sling5/org/apache/sling/api/request/RequestParameter.html). De [ isFormField ](https://sling.apache.org/apidocs/sling5/org/apache/sling/api/request/RequestParameter.html#isFormField()) methode van de API hulp identificeert zich of de verzoekparameter een dossier of een vormgebied is. U kunt de parameters van het Verzoek in een Submit actie herhalen om de parameters van de Bijlage van het Dossier te identificeren.

De volgende voorbeeldcode identificeert de bestandsbijlagen in de aanvraag. Daarna, leest het de gegevens in het dossier gebruikend [ krijg API ](https://sling.apache.org/apidocs/sling5/org/apache/sling/api/request/RequestParameter.html#get()). Ten slotte wordt een object Document gemaakt met behulp van de gegevens en toegevoegd aan een lijst.

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
>Een auteur verstrekt Redirect URL (gebruikend de Dank u Configuratie van de Pagina). [ uit-van-de-doos verzendt Acties ](../../forms/using/configuring-submit-actions.md) gebruik Redirect URL om browser van het middel om te leiden dat de voorwaartse wegverwijzingen.
>
>U kunt een douane schrijven voorlegt actie die een verzoek aan een middel of servlet door:sturen. De Adobe adviseert dat het manuscript dat middelbehandeling voor de voorwaartse weg uitvoert het verzoek aan Redirect URL opnieuw richt wanneer de verwerking voltooit.

## Handeling verzenden {#submit-action}

Een handeling Verzenden is een tekenreeks:Map die het volgende bevat:

* **addfields.jsp**: Dit manuscript verstrekt de actievelden die aan het dossier van de HTML tijdens vertoning worden toegevoegd. Gebruik dit script om verborgen invoerparameters toe te voegen die zijn vereist tijdens verzending in het script post.POST.jsp.
* **dialog.xml**: Dit manuscript is gelijkaardig aan de dialoog van de Component CQ. Het verstrekt configuratieinformatie die de auteur aanpast. De velden worden weergegeven op het tabblad Handelingen verzenden in het dialoogvenster Formulier bewerken Adaptief wanneer u de handeling Verzenden selecteert.
* **post.POST.jsp**: Submit servlet roept dit manuscript met de gegevens die u en de extra gegevens in de vorige secties voorlegt. Elke vermelding van het uitvoeren van een handeling op deze pagina houdt in dat het script post.POST.jsp wordt uitgevoerd. Als u de handeling Verzenden wilt registreren met de adaptieve formulieren die u wilt weergeven in het dialoogvenster Formulier bewerken, voegt u de volgende eigenschappen toe aan de `sling:Folder` :

   * **guideComponentType** van typeKoord en waarde **fd/af/components/guidesubmittype**
   * **guideDataModel** van typeKoord dat het type van adaptieve vorm specificeert waarvoor de Submit actie van toepassing is. **xfa** wordt gesteund voor op XFA-Gebaseerde adaptieve vormen terwijl **xsd** voor op XSD-Gebaseerde adaptieve vormen wordt gesteund. **basis** wordt gesteund voor adaptieve vormen die geen XDP of XSD gebruiken. Voeg de corresponderende tekenreeksen toe om de handeling weer te geven op meerdere typen adaptieve formulieren. Scheid elke tekenreeks door een komma. Bijvoorbeeld, om een actie op op XFA en op XSD-Gebaseerde adaptieve vormen zichtbaar te maken, specificeer de waarden **xfa** en **xsd** respectievelijk.

   * **jcr:beschrijving** van typeKoord. De waarde van deze eigenschap wordt weergegeven in de actielijst Verzenden op het tabblad Handelingen verzenden van het dialoogvenster Formulier bewerken Adaptief. De acties buiten de box zijn aanwezig in de bewaarplaats van CRX bij de plaats **/libs/fd/af/components/guidesubmittype**.

## Een aangepaste verzendhandeling maken {#creating-a-custom-submit-action}

Voer de volgende stappen uit om een aangepaste verzendactie te maken die de gegevens opslaat in de CRX-opslagplaats en u vervolgens een e-mail stuurt. Het adaptieve formulier bevat de handeling Verzenden uit de doos Winkelinhoud (afgekeurd) die de gegevens opslaat in de CRX-opslagplaats. Bovendien verstrekt CQ a [ Post ](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/previous-updates/aem-previous-versions.html?lang=en) API die kan worden gebruikt om e-mails te verzenden. Alvorens de Post API te gebruiken, [ vorm ](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/previous-updates/aem-previous-versions.html?lang=en&amp;wcmmode=disabled) de dienst van de Post van Dag CQ door de systeemconsole. U kunt de actie Store Content (afgekeurd) opnieuw gebruiken om de gegevens in de opslagplaats op te slaan. De actie Store Content (afgekeurd) is beschikbaar op de locatie /libs/fd/af/components/guidesubmittype/store in de CRX-opslagplaats.

1. Meld u aan bij CRXDE Lite op de URL https://&lt;server>:&lt;port>/crx/de/index.jsp. Maak een knooppunt met de eigenschap sling:Folder en name store_and_mail in de map /apps/custom_submit_action. Maak de map custom_submit_action als deze nog niet bestaat.

   ![ Scherenshot die de verwezenlijking van een knoop met het bezit toont:Omslag ](assets/step1.png)

1. **verstrek de verplichte configuratiegebieden.**

   Voeg de configuratie toe die de winkelactie vereist. Kopieer **cq:dialoog** knoop van de actie van de Opslag van /libs/fd/af/components/guidesubmittype/store aan de actiemap bij /apps/custom_submit_action/store_and_email.

   ![ Schermafbeelding die het kopiëren van de dialoogknoop aan de actiemap tonen ](assets/step2.png)

1. **verstrek configuratiegebieden om de auteur voor e-mailconfiguratie te veroorzaken.**

   Het adaptieve formulier bevat ook een e-mailactie die e-mailberichten naar gebruikers verzendt. Pas deze actie aan op basis van uw vereisten. Ga naar /libs/fd/af/components/guidesubmittype/email/dialog. Kopieer de knooppunten in het cq:dialog-knooppunt naar cq:dialog-knooppunt van de handeling Verzenden (/apps/custom_submit_action/store_and_email/dialog).

   ![ Aanpassen van de e-mailactie ](assets/step3.png)

1. **maak de actie beschikbaar in de Aangepaste Vorm geeft dialoog uit.**

   Voeg de volgende eigenschappen in de store_and_email knoop toe:

   * **guideComponentType** van type **Koord** en waarde **fd/af/components/guidesubmittype**

   * **guideDataModel** van type **Koord** en waarde **xfa, xsd, basis**

   * **jcr:beschrijving** van type **Koord** en waarde **Slag en E-mailActie**

1. Open een adaptief formulier. Klik **uitgeven** knoop naast **Begin** om de **te openen geef** dialoog van de adaptieve vormcontainer uit. De nieuwe actie wordt getoond in **legt Acties** Lusje voor. Het selecteren van de **Opslag en E-mailActie** toont de configuratie die in de dialoogdoos wordt toegevoegd.

   ![ voorlegt de dialoog van de actieconfiguratie ](assets/store_and_email_submit_action_dialog.jpg)

1. **gebruik de actie om een taak te voltooien.**

   Voeg het script post.POST.jsp toe aan uw handeling. (/apps/custom_submit_action/store_and_mail/).

   Voer de handeling uit van de winkel (het script post.POST.jsp). Gebruik [ FormsHelper.runAction ](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/previous-updates/aem-previous-versions.html?lang=en) (java.lang.String, java.lang.String, org.apache.sling.api.resource.Resource, org.apache.sling.api.SlingHttpServletRequest, org.apache.sling.api.SlingHttpServletResponse) API die CQ verstrekt Je code om de actie Winkel uit te voeren. Voeg de volgende code in uw JSP dossier toe:

   `FormsHelper.runAction("/libs/fd/af/components/guidesubmittype/store", "post", resource, slingRequest, slingResponse);`

   Om e-mail te verzenden, leest de code het e-mailadres van de ontvanger van de configuratie. Om de configuratiewaarde in het manuscript van de actie te halen, lees de eigenschappen van het huidige middel gebruikend de volgende code. Op dezelfde manier kunt u de andere configuratiedossiers lezen.

   `ValueMap properties = ResourceUtil.getValueMap(resource);`

   `String mailTo = properties.get("mailTo");`

   Tot slot gebruikt u de CQ Mail-API om de e-mail te verzenden. Gebruik de [ klasse SimpleEmail ](https://commons.apache.org/proper/commons-email/apidocs/org/apache/commons/mail/SimpleEmail.html) om het E-mailVoorwerp tot stand te brengen zoals hieronder afgebeeld:

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
