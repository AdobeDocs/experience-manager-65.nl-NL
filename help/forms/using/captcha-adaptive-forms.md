---
title: CAPTCHA gebruiken in aangepaste vormen
description: Leer hoe u AEM CAPTCHA- of Google reCAPTCHA-service configureert in adaptieve formulieren.
contentOwner: vishgupt
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: adaptive_forms, author
docset: aem65
feature: Adaptive Forms,Foundation Components
exl-id: 9b4219b8-d5eb-4099-b205-d98d84e0c249
solution: Experience Manager, Experience Manager Forms
role: Admin, User, Developer
source-git-commit: d7b9e947503df58435b3fee85a92d51fae8c1d2d
workflow-type: tm+mt
source-wordcount: '1755'
ht-degree: 0%

---

# CAPTCHA gebruiken in aangepaste vormen{#using-captcha-in-adaptive-forms}

| Versie | Artikelkoppeling |
| -------- | ---------------------------- |
| AEM as a Cloud Service | [ klik hier ](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/adaptive-forms-authoring/authoring-adaptive-forms-foundation-components/add-components-to-an-adaptive-form/captcha-adaptive-forms.html) |
| AEM 6,5 | Dit artikel |


<span class="preview"> de Adobe adviseert gebruikend de moderne en verlengbare gegevens vangen [ Componenten van de Kern ](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/introduction.html) voor [ het creëren van nieuwe Aangepaste Forms ](/help/forms/using/create-an-adaptive-form-core-components.md) of [ het toevoegen van Aangepaste Forms aan de pagina&#39;s van AEM Sites ](/help/forms/using/create-or-add-an-adaptive-form-to-aem-sites-page.md). Deze componenten betekenen een aanzienlijke vooruitgang in de aanmaak van Adaptive Forms en zorgen voor indrukwekkende gebruikerservaring. In dit artikel wordt een oudere aanpak beschreven voor de auteur Adaptive Forms die gebruikmaakt van stichtingscomponenten. </span>

CAPTCHA (Complete Automated Public Turing test to tell Computers and Humans Apart) is een programma dat vaak wordt gebruikt bij online transacties om onderscheid te maken tussen mensen en geautomatiseerde programma&#39;s of bots. Het stelt een uitdaging en evalueert de reactie van de gebruiker om te bepalen of het een mens of bot is die met de site communiceert. Het verhindert de gebruiker om te werk te gaan als de test ontbreekt en de hulp maakt online transacties veilig door bots te houden spam of kwaadwillige doeleinden posten.

AEM Forms ondersteunt CAPTCHA in adaptieve vormen. U kunt de reCAPTCHA-service van Google gebruiken om CAPTCHA te implementeren.

>[!NOTE]
>
>* AEM Forms biedt ondersteuning voor reCAPTCHA v2 en Enterprise. Andere versies worden niet ondersteund.
>* CAPTCHA in adaptieve formulieren wordt niet ondersteund in de offlinemodus van de AEM Forms-app.

## De reCAPTCHA-service van Google configureren voor Adaptive Forms {#google-reCAPTCHA}

AEM Forms-gebruikers kunnen de reCAPTCHA-service van Google gebruiken om CAPTCHA in adaptieve formulieren te implementeren. Het biedt geavanceerde CAPTCHA-mogelijkheden om uw site te beschermen. Voor meer informatie over hoe reCAPTCHA werkt, zie [ Google reCAPTCHA ](https://developers.google.com/recaptcha/). De reCAPTCHA-service, inclusief reCAPTCHA v2 en reCAPTCHA Enterprise, is geïntegreerd in AEM Forms. Gebaseerd op uw vereiste kunt u de dienst vormen reCAPTCHA om toe te laten:

* [reCAPTCHA Enterprise in AEM Forms](#steps-to-implement-reCAPTCHA-enterprise-in-forms)
* [reCAPTCHA v2 in AEM Forms](#steps-to-implement-reCAPTCHA-v2-in-forms)

![ reCAPTCHA ](/help/forms/using/assets/recaptcha_new.png)

### reCAPTCHA Enterprise configureren  {#steps-to-implement-reCAPTCHA-enterprise-in-forms}

1. Creeer het project van de Onderneming van a [ reCAPTCHA ](https://cloud.google.com/recaptcha-enterprise/docs/set-up-non-google-cloud-environments-api-keys#before-you-begin) toegelaten met [ reCAPTCHA Onderneming API ](https://cloud.google.com/recaptcha-enterprise/docs/set-up-non-google-cloud-environments-api-keys#enable-the-recaptcha-enterprise-api).
1. [ verkrijg ](https://support.google.com/googleapi/answer/7014113?hl=en#:~:text=To%20locate%20your%20project%20ID,a%20member%20of%20are%20displayed) identiteitskaart van het Project.
1. Creeer een [ API sleutel ](https://cloud.google.com/recaptcha-enterprise/docs/set-up-non-google-cloud-environments-api-keys#create_an_api_key) en de sleutel van de a [ plaats voor websites ](https://cloud.google.com/recaptcha-enterprise/docs/create-key#create-key).
1. Configuratiecontainer maken voor cloudservices.

   1. Ga naar **[!UICONTROL Tools > General > Configuration Browser]** . Zie Browser van de Configuratie ](/help/sites-administering/configurations.md) documentatie 0} {voor meer informatie.[
   1. Ga als volgt te werk om de algemene map voor cloudconfiguraties in te schakelen of sla deze stap over om een andere map voor cloudserviceconfiguraties te maken en te configureren.
      1. Selecteer de map **[!UICONTROL global]** in de Configuration Browser en selecteer **[!UICONTROL Properties]** .
      1. Schakel in het dialoogvenster Configuration Properties **[!UICONTROL Cloud Configurations]** in.
      1. Selecteer **[!UICONTROL Save & Close]** om de configuratie op te slaan en het dialoogvenster af te sluiten.

   1. Selecteer **[!UICONTROL Create]** in de Configuration Browser.
   1. Geef in het dialoogvenster Configuratie maken een titel op voor de map en schakel **[!UICONTROL Cloud Configurations]** in.
   1. Selecteer **[!UICONTROL Create]** om de map te maken die is ingeschakeld voor cloudserviceconfiguraties.
1. Configureer de cloudservice voor reCAPTCHA Enterprise.

   1. Op uw de auteursinstantie van de Experience Manager, ga ![ hulpmiddelen-1 ](assets/tools-1.png) > **[!UICONTROL Cloud Services]**.
   1. Selecteer **[!UICONTROL reCAPTCHA]**. De pagina Configurations wordt geopend. Selecteer de configuratiecontainer die in de vorige stap is gemaakt en selecteer **[!UICONTROL Create]** .
   1. Selecteer versie als reCAPTCHA Enterprise en geef Naam; Project ID, Site Key en API-sleutel (verkregen in stap 2 en 3) op voor de reCAPTCHA Enterprise-service.
   1. Selecteer zeer belangrijk type, zou het zeer belangrijke type als plaats sleutel moeten zijn die in het google wolkenproject wordt gevormd, bijvoorbeeld, **of** Score-based plaatstoets **van 0} Checkbox.**
   1. Specificeer een drempelscore in waaier 0-1 ([ klik om meer over score ](https://cloud.google.com/recaptcha-enterprise/docs/interpret-assessment#interpret_scores) te weten te komen). Scores groter dan of gelijk aan de drempelscores identificeren menselijke interactie, anders beschouwd als beide interactie.

      > Opmerking:
      >
      > * Formulierauteurs kunnen een score opgeven in het bereik dat geschikt is voor ononderbroken formulierverzending.

   1. Selecteer **[!UICONTROL Create]** om de configuratie van de cloudservice te maken.

   1. Geef in het dialoogvenster Component bewerken de naam, de project-id, de sitetoets en de API-sleutel op (verkregen in stap 2 en 3), selecteer het toetstype en voer de drempelscore in. Selecteer **[!UICONTROL Save Settings]** en selecteer vervolgens **[!UICONTROL OK]** om de configuratie te voltooien.

Zodra de reCAPTCHA Enterprise-service is ingeschakeld, is deze beschikbaar voor gebruik in adaptieve formulieren. Zie [ gebruikend CAPTCHA in adaptieve vormen ](#using-reCAPTCHA).

![ reCAPTCHA Onderneming ](/help/forms/using/assets/recaptcha1-enterprise.png)


### Google reCAPTCHA v2 configureren {#steps-to-implement-reCAPTCHA-v2-in-forms}

1. Verkrijg [ reCAPTCHA API zeer belangrijk paar ](https://www.google.com/recaptcha/admin) van Google. Het omvat a **plaats sleutel** en a **geheime sleutel**.
1. Configuratiecontainer maken voor cloudservices.
   1. Ga naar **[!UICONTROL Tools > General > Configuration Browser]** . Zie Browser van de Configuratie ](/help/sites-administering/configurations.md) documentatie 0} {voor meer informatie.[
   1. Ga als volgt te werk om de algemene map voor cloudconfiguraties in te schakelen of sla deze stap over om een andere map voor cloudserviceconfiguraties te maken en te configureren.

      1. Selecteer de map **[!UICONTROL global]** in de Configuration Browser en selecteer **[!UICONTROL Properties]** .

      1. Schakel in het dialoogvenster Configuration Properties **[!UICONTROL Cloud Configurations]** in.
      1. Selecteer **[!UICONTROL Save & Close]** om de configuratie op te slaan en het dialoogvenster af te sluiten.

   1. Selecteer **[!UICONTROL Create]** in de Configuration Browser.
   1. Geef in het dialoogvenster Configuratie maken een titel op voor de map en schakel **[!UICONTROL Cloud Configurations]** in.
   1. Selecteer **[!UICONTROL Create]** om de map te maken die is ingeschakeld voor cloudserviceconfiguraties.

1. Configureer de cloudservice voor reCAPTCHA v2.

   1. Op uw AEM auteursinstantie, ga ![ hulpmiddelen-1 ](assets/tools-1.png) > **Cloud Servicen**.
   1. Selecteer **[!UICONTROL reCAPTCHA]**. De pagina Configurations wordt geopend. Selecteer de configuratiecontainer die in de vorige stap is gemaakt en selecteer **[!UICONTROL Create]** .
   1. Selecteer versie als reCAPTCHA v2, geef Naam, Sitesleutel en Geheime sleutel voor de service reCAPTCHA op (verkregen in stap 1) en selecteer **[!UICONTROL Create]** om de configuratie van de cloudservice te maken.
   1. Geef in het dialoogvenster Component bewerken de site en de geheime sleutels op die in stap 1 zijn verkregen. Selecteer **[!UICONTROL Save Settings]** en selecteer dan **O.K.** om de configuratie te voltooien.

   Zodra de reCAPTCHA-service is geconfigureerd, is deze beschikbaar voor gebruik in adaptieve formulieren. Voor meer informatie, zie [ gebruikend CAPTCHA in adaptieve vormen ](#using-captcha).

![ reCAPTCHA v2 ](/help/forms/using/assets/recaptcha-v2.png)


## reCAPTCHA gebruiken in adaptieve formulieren {#using-reCAPTCHA}

ReCAPTCHA in adaptieve vorm gebruiken:

1. Open een adaptief formulier in de bewerkingsmodus.

   >[!NOTE]
   >
   >Zorg ervoor dat de configuratiecontainer die is geselecteerd bij het maken van het adaptieve formulier, de reCAPTCHA-cloudservice bevat. U kunt ook adaptieve formuliereigenschappen bewerken om de configuratiecontainer te wijzigen die aan het formulier is gekoppeld.

1. Van componentenbrowser, sleep-daling de **component Captcha** op de adaptieve vorm.

   >[!NOTE]
   >
   >Het gebruik van meer dan één Captcha-component in een adaptieve vorm wordt niet ondersteund. Het wordt ook afgeraden om CAPTCHA te gebruiken in een deelvenster dat is gemarkeerd voor wazig laden of in een fragment.

   >[!NOTE]
   >
   >Captcha is tijdgevoelig en verloopt over ongeveer een minuut. Daarom wordt aangeraden de component Captcha vlak voor de knop Verzenden in het aangepaste formulier te plaatsen.

1. Selecteer de component Captcha die u toevoegde en ![ cmp ](assets/cmppr.png) selecteert om zijn eigenschappen uit te geven.
1. Geef een titel op voor de CAPTCHA-widget. De standaardwaarde is **Captcha**. Selecteer **titel van de Verbergen** als u geen titel wilt verschijnen.
1. Van de **dienst Captcha** drop-down, uitgezochte **reCAPTCHA** om de dienst reCAPTCHA toe te laten als u het zoals die in [ wordt beschreven reCAPTCHA dienst door Google ](#google-reCAPTCHA) vormde.
1. Selecteer een configuratie in het keuzemenu Instellingen.
1. **als de geselecteerde configuratie versie reCAPTCHA Onderneming** heeft:
   1. U kunt reCAPTCHA wolkenconfiguratie met **zeer belangrijk type** als **checkbox** selecteren. In checkbox zeer belangrijk type verschijnt het aangepaste foutenbericht als gealigneerd bericht als de bevestiging captcha ontbreekt. U kunt grootte selecteren als **[!UICONTROL Normal]** en **[!UICONTROL Compact]** .
   1. U kunt reCAPTCHA wolkenconfiguratie met **zeer belangrijk type** als **gebaseerde score** selecteren. In op score gebaseerde sleuteltype toont het aangepaste foutbericht als pop-upbericht als de validatie van captcha mislukt.
   1. Wanneer u een **[!UICONTROL Bind Reference]** selecteert, zijn de verzonden gegevens gebonden, anders zijn het niet-gebonden gegevens. Hieronder volgen XML-voorbeelden van niet-gebonden gegevens en gebonden gegevens (met bind verwijzing als SSN), wanneer een formulier wordt verzonden.

      ```xml
          <?xml version="1.0" encoding="UTF-8" standalone="no"?>
          <afData>
          <afUnboundData>
              <data>
                  <captcha16820607953761>
                      <captchaType>reCAPTCHAEnterprise</captchaType>
                      <captchaScore>0.9</captchaScore>
                  </captcha16820607953761>
              </data>
          </afUnboundData>
          <afBoundData>
              <Root
                  xmlns:xfa="http://www.xfa.org/schema/xfa-data/1.0/"
                  xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">
                  <PersonalDetails>
                      <SSN>371237912</SSN>
                      <FirstName>Sarah </FirstName>
                      <LastName>Smith</LastName>
                  </PersonalDetails>
                  <OtherInfo>
                      <City>California</City>
                      <Address>54 Residency</Address>
                      <State>USA</State>
                      <Zip>123112</Zip>
                  </OtherInfo>
              </Root>
          </afBoundData>
          <afSubmissionInfo>
              <stateOverrides/>
              <signers/>
              <afPath>/content/dam/formsanddocuments/captcha-form</afPath>
              <afSubmissionTime>20230608034928</afSubmissionTime>
          </afSubmissionInfo>
          </afData>
      ```


      ```xml
          <?xml version="1.0" encoding="UTF-8" standalone="no"?>
          <afData>
          <afUnboundData>
              <data/>
          </afUnboundData>
          <afBoundData>
              <Root
                  xmlns:xfa="http://www.xfa.org/schema/xfa-data/1.0/"
                  xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">
                  <PersonalDetails>
                      <SSN>
                          <captchaType>reCAPTCHAEnterprise</captchaType>
                          <captchaScore>0.9</captchaScore>
                      </SSN>
                      <FirstName>Sarah</FirstName>
                      <LastName>Smith</LastName>
                  </PersonalDetails>
                  <OtherInfo>
                      <City>California</City>
                      <Address>54 Residency</Address>
                      <State>USA</State>
                      <Zip>123112</Zip>
                  </OtherInfo>
              </Root>
          </afBoundData>
          <afSubmissionInfo>
              <stateOverrides/>
              <signers/>
              <afPath>/content/dam/formsanddocuments/captcha-form</afPath>
              <afSubmissionTime>20230608035111</afSubmissionTime>
          </afSubmissionInfo>
          </afData>
      ```


   **als de geselecteerde configuratie versie reCAPTCHA v2** heeft:
   1. Selecteer de grootte als **[!UICONTROL Normal]** of **[!UICONTROL Compact]** voor de reCAPTCHA-widget. U kunt de optie **[!UICONTROL Invisible]** ook selecteren om de CAPTCHA-uitdaging alleen weer te geven als er sprake is van verdachte activiteit. **die door reCAPTCHA** wordt beschermd badge, hieronder wordt getoond, wordt getoond op de beschermde vormen.

      ![ Google die door reCAPTCHA badge ](/help/forms/using/assets/google-recaptcha-v2.png) wordt beschermd


   De reCAPTCHA-service is ingeschakeld op het adaptieve formulier. U kunt een voorbeeld van het formulier bekijken en de CAPTCHA bekijken.

1. Sla de eigenschappen op.

>[!NOTE]
> 
> Selecteer **[!UICONTROL Default]** niet in het vervolgkeuzemenu Captcha-service omdat de standaard AEM CAPTCHA-service is vervangen.

### CAPTCHA-component tonen of verbergen op basis van regels {#show-hide-captcha}

U kunt de component CAPTCHA weergeven of verbergen op basis van de regels die u toepast op een component in een adaptief formulier. Selecteer de component, uitgezocht ![ geef regels ](assets/edit-rules-icon.svg) uit, en selecteer **[!UICONTROL Create]** om een regel tot stand te brengen. Voor meer informatie bij het creëren van regels, zie [ Redacteur van de Regel ](rule-editor.md).

De component CAPTCHA moet bijvoorbeeld alleen in een adaptief formulier worden weergegeven als het veld Waarde valuta in het formulier een waarde heeft van meer dan 25000.

Selecteer het veld **[!UICONTROL Currency Value]** in het formulier en stel de volgende regels in:

![ toon of verberg regels ](assets/rules-show-hide-captcha.png)

>[!NOTE]
>
> * Als u de v2-configuratie reCAPTCHA met de grootte **[!UICONTROL Invisible]** of reCAPTCHA Enterprise score selecteert, is de optie show/hide niet van toepassing.

### CAPTCHA valideren {#validate-captcha}

U kunt CAPTCHA valideren in een adaptief formulier wanneer u het formulier verzendt of de CAPTCHA-validatie baseert op gebruikersacties en -voorwaarden.

#### CAPTCHA valideren bij het verzenden van formulieren {#validation-form-submission}

Een CAPTCHA automatisch valideren wanneer u een adaptief formulier verzendt:

1. Selecteer de component CAPTCHA en selecteer ![ cmp ](assets/configure-icon.svg) om de componenteneigenschappen te bekijken.
1. Selecteer **[!UICONTROL Validate CAPTCHA at form submission]** in de sectie **[!UICONTROL Validate CAPTCHA]** .
1. Selecteer ![ Gedaan ](assets/save_icon.svg) om de componenteneigenschappen te bewaren.

#### CAPTCHA bij gebruikershandelingen en -voorwaarden valideren {#validate-captcha-user-action}

Een CAPTCHA valideren op basis van voorwaarden en gebruikersacties:

1. Selecteer de component CAPTCHA en selecteer ![ cmp ](assets/configure-icon.svg) om de componenteneigenschappen te bekijken.
1. Selecteer **[!UICONTROL Validate CAPTCHA on a user action]** in de sectie **[!UICONTROL Validate CAPTCHA]** .
1. Selecteer ![ Gedaan ](assets/save_icon.svg) om de componenteneigenschappen te bewaren.

   >[!NOTE]
   >
   >
   > Als u de v2-configuratie reCAPTCHA met de grootte **[!UICONTROL Invisible]** of reCAPTCHA Enterprise score selecteert, is Geldig Captcha voor een gebruikersactie niet van toepassing.

[!DNL Experience Manager Forms] biedt `ValidateCAPTCHA` API om CAPTCHA te valideren met behulp van vooraf gedefinieerde voorwaarden. U kunt de API aanroepen met behulp van een aangepaste verzendactie of door regels voor componenten in een adaptief formulier te definiëren.

Hieronder ziet u een voorbeeld van een API van het type `ValidateCAPTCHA` voor het valideren van CAPTCHA met behulp van vooraf gedefinieerde voorwaarden:

```javascript
if (slingRequest.getParameter("numericbox1614079614831").length() >= 5) {
        GuideCaptchaValidatorProvider apiProvider = sling.getService(GuideCaptchaValidatorProvider.class);
        String formPath = slingRequest.getResource().getPath();
        String captchaData = slingRequest.getParameter(GuideConstants.GUIDE_CAPTCHA_DATA);
        if (!apiProvider.validateCAPTCHA(formPath, captchaData).isCaptchaValid()){
            response.setStatus(400);
            return;
        }
    }
```

In het voorbeeld wordt aangegeven dat de API van `ValidateCAPTCHA` de CAPTCHA alleen in het formulier valideert als het aantal cijfers in het numerieke vak dat de gebruiker heeft opgegeven tijdens het invullen van het formulier groter is dan 5.

**Optie 1: Gebruik [!DNL Experience Manager Forms] ValidateCAPTCHA API om CAPTCHA te bevestigen gebruikend een douane verzendt Actie**

Voer de volgende stappen uit om de API `ValidateCAPTCHA` te gebruiken om CAPTCHA te valideren met behulp van een aangepaste handeling Verzenden:

1. Voeg het script dat de `ValidateCAPTCHA` API bevat toe aan de aangepaste verzendactie. Voor meer op douane verzend Acties, zie [ een douane creëren legt Actie voor Aanpassings Forms ](custom-submit-action-form.md) voor.
1. Selecteer de naam van de aangepaste handeling Verzenden in de vervolgkeuzelijst **[!UICONTROL Submit Action]** in de **[!UICONTROL Submission]** -eigenschappen van een adaptief formulier.
1. Selecteer **[!UICONTROL Submit]**. De CAPTCHA wordt gevalideerd op basis van de voorwaarden die zijn gedefinieerd in de `ValidateCAPTCHA` API van de aangepaste verzendactie.

**Optie 2: Gebruik [!DNL Experience Manager Forms] ValidateCAPTCHA API om CAPTCHA op een gebruikersactie te bevestigen alvorens de vorm** voor te leggen

U kunt de `ValidateCAPTCHA` API ook aanroepen door regels toe te passen op een component in een adaptief formulier.

U voegt bijvoorbeeld een knop **[!UICONTROL Validate CAPTCHA]** toe aan een adaptief formulier en maakt een regel om een service aan te roepen bij het klikken op een knop.

In de volgende afbeelding ziet u hoe u een service kunt aanroepen wanneer u op een knop **[!UICONTROL Validate CAPTCHA]** klikt:

![ bevestigt CAPTCHA ](assets/captcha-validation1.gif)

U kunt de aangepaste servlet die `ValidateCAPTCHA` API omvat aanroepen gebruikend de regelredacteur en de verzendknoop van het Aangepaste Vorm toelaten of onbruikbaar maken die op het bevestigingsresultaat wordt gebaseerd.

Op dezelfde manier kunt u regeleditor gebruiken om een aangepaste methode op te nemen om CAPTCHA in een adaptief formulier te valideren.

<!--
### Add custom CAPTCHA services {#add-custom-captcha-service}

[!DNL Experience Manager Forms] provides reCAPTCHA as the CAPTCHA service. However, you can add a custom service to display in the **[!UICONTROL CAPTCHA Service]** drop-down list.  

The following is a sample implementation of the interface to add additional CAPTCHA service to your Adaptive Form:

```javascript
package com.adobe.aemds.guide.service;

import org.osgi.annotation.versioning.ConsumerType;

/**
 * An interface to provide captcha validation at server side in Adaptive Form
 * This interface can be used to provide custom implementation for different captcha services.
 */
@ConsumerType
public interface GuideCaptchaValidator {
    /**
     * This method should define the actual validation logic of the captcha
     * @param captchaPropertyNodePath path to the node with CAPTCHA configurations inside form container
     * @param userResponseToken  The user response token provided by the CAPTCHA from client-side
     *
     * @return  {@link GuideCaptchaValidationResult} validation result of the captcha
     */
     GuideCaptchaValidationResult validateCaptcha(String captchaPropertyNodePath, String userResponseToken);

    /**
     * Returns the name of the captcha validator. This should be unique among the different implementations
     * @return  name of the captcha validator
     */
     String getCaptchaValidatorName();
}
```

`captchaPropertyNodePath` Refers to the resource path of the CAPTCHA component in the Sling repository. Use this property to include details specific to the CAPTCHA component. For example, `captchaPropertyNodePath` includes information for the reCAPTCHA cloud configuration configured on the CAPTCHA component. The cloud configuration information provides **[!UICONTROL Site Key]** and **[!UICONTROL Secret Key]** settings for implementing the reCAPTCHA service.

`userResponseToken` Refers to the `g_reCAPTCHA_response` that gets generated after solving a CAPTCHA in a form. -->
