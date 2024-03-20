---
title: CAPTCHA gebruiken in aangepaste vormen
description: Leer hoe u AEM CAPTCHA- of Google reCAPTCHA-service configureert in adaptieve formulieren.
contentOwner: vishgupt
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: adaptive_forms, author
docset: aem65
feature: Adaptive Forms, Foundation Components
exl-id: 9b4219b8-d5eb-4099-b205-d98d84e0c249
solution: Experience Manager, Experience Manager Forms
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '1755'
ht-degree: 0%

---

# CAPTCHA gebruiken in aangepaste vormen{#using-captcha-in-adaptive-forms}

| Versie | Artikelkoppeling |
| -------- | ---------------------------- |
| AEM as a Cloud Service | [Klik hier](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/adaptive-forms-authoring/authoring-adaptive-forms-foundation-components/add-components-to-an-adaptive-form/captcha-adaptive-forms.html) |
| AEM 6,5 | Dit artikel |


<span class="preview"> Adobe beveelt aan moderne en uitbreidbare gegevensvastlegging te gebruiken [Kernonderdelen](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/introduction.html) for [nieuwe Adaptieve Forms maken](/help/forms/using/create-an-adaptive-form-core-components.md) of [Aangepaste Forms toevoegen aan AEM Sites-pagina&#39;s](/help/forms/using/create-or-add-an-adaptive-form-to-aem-sites-page.md). Deze componenten betekenen een aanzienlijke vooruitgang in de aanmaak van Adaptive Forms en zorgen voor indrukwekkende gebruikerservaring. In dit artikel wordt een oudere aanpak beschreven voor de auteur Adaptive Forms die gebruikmaakt van stichtingscomponenten. </span>

CAPTCHA (Complete Automated Public Turing test to tell Computers and Humans Apart) is een programma dat vaak wordt gebruikt bij online transacties om onderscheid te maken tussen mensen en geautomatiseerde programma&#39;s of bots. Het stelt een uitdaging en evalueert de reactie van de gebruiker om te bepalen of het een mens of bot is die met de site communiceert. Het verhindert de gebruiker om te werk te gaan als de test ontbreekt en de hulp maakt online transacties veilig door bots te houden spam of kwaadwillige doeleinden posten.

AEM Forms ondersteunt CAPTCHA in adaptieve vormen. U kunt de reCAPTCHA-service van Google gebruiken om CAPTCHA te implementeren.

>[!NOTE]
>
>* AEM Forms biedt ondersteuning voor reCAPTCHA v2 en Enterprise. Andere versies worden niet ondersteund.
>* CAPTCHA in adaptieve formulieren wordt niet ondersteund in de offlinemodus van de AEM Forms-app.

## De reCAPTCHA-service van Google configureren voor Adaptive Forms {#google-reCAPTCHA}

AEM Forms-gebruikers kunnen de reCAPTCHA-service van Google gebruiken om CAPTCHA in adaptieve formulieren te implementeren. Het biedt geavanceerde CAPTCHA-mogelijkheden om uw site te beschermen. Voor meer informatie over hoe reCAPTCHA werkt, zie [Google reCAPTCHA](https://developers.google.com/recaptcha/). De reCAPTCHA-service, inclusief reCAPTCHA v2 en reCAPTCHA Enterprise, is geïntegreerd in AEM Forms. Gebaseerd op uw vereiste kunt u de dienst vormen reCAPTCHA om toe te laten:

* [reCAPTCHA Enterprise in AEM Forms](#steps-to-implement-reCAPTCHA-enterprise-in-forms)
* [reCAPTCHA v2 in AEM Forms](#steps-to-implement-reCAPTCHA-v2-in-forms)

![reCAPTCHA](/help/forms/using/assets/recaptcha_new.png)

### reCAPTCHA Enterprise configureren  {#steps-to-implement-reCAPTCHA-enterprise-in-forms}

1. Een [reCAPTCHA Enterprise-project](https://cloud.google.com/recaptcha-enterprise/docs/set-up-non-google-cloud-environments-api-keys#before-you-begin) ingeschakeld met [reCAPTCHA Enterprise API](https://cloud.google.com/recaptcha-enterprise/docs/set-up-non-google-cloud-environments-api-keys#enable-the-recaptcha-enterprise-api).
1. [Verkrijgen](https://support.google.com/googleapi/answer/7014113?hl=en#:~:text=To%20locate%20your%20project%20ID,a%20member%20of%20are%20displayed) de project-id.
1. Een [API-sleutel](https://cloud.google.com/recaptcha-enterprise/docs/set-up-non-google-cloud-environments-api-keys#create_an_api_key) en [sitecode voor websites](https://cloud.google.com/recaptcha-enterprise/docs/create-key#create-key).
1. Configuratiecontainer maken voor cloudservices.

   1. Ga naar **[!UICONTROL Tools > General > Configuration Browser]**. Zie de [Configuratiebrowser](/help/sites-administering/configurations.md) documentatie voor meer informatie.
   1. Ga als volgt te werk om de algemene map voor cloudconfiguraties in te schakelen of sla deze stap over om een andere map voor cloudserviceconfiguraties te maken en te configureren.
      1. In Browser van de Configuratie, selecteer **[!UICONTROL global]** map en selecteer **[!UICONTROL Properties]**.
      1. Schakel in het dialoogvenster Configuratieeigenschappen de optie **[!UICONTROL Cloud Configurations]**.
      1. Selecteren **[!UICONTROL Save & Close]** om de configuratie op te slaan en het dialoogvenster af te sluiten.

   1. In Browser van de Configuratie, selecteer **[!UICONTROL Create]**.
   1. Geef in het dialoogvenster Configuratie maken een titel op voor de map en schakel **[!UICONTROL Cloud Configurations]**.
   1. Selecteren **[!UICONTROL Create]** om de map te maken die is ingeschakeld voor configuraties van de cloudservice.
1. Configureer de cloudservice voor reCAPTCHA Enterprise.

   1. Ga naar de Experience Manager authentieke instantie ![gereedschappen-1](assets/tools-1.png) > **[!UICONTROL Cloud Services]**.
   1. Selecteer **[!UICONTROL reCAPTCHA]**. De pagina Configurations wordt geopend. Selecteer de configuratiecontainer die in de vorige stap is gemaakt en selecteer **[!UICONTROL Create]**.
   1. Selecteer versie als reCAPTCHA Enterprise en geef Naam; Project ID, Site Key en API-sleutel (verkregen in stap 2 en 3) op voor de reCAPTCHA Enterprise-service.
   1. Selecteer sleuteltype, zou het zeer belangrijke type moeten zijn zoals de plaatssleutel die in het Google wolkenproject wordt gevormd, bijvoorbeeld **Sitetoets selectievakje** of **Score-gebaseerde sitesleutel**.
   1. Geef een drempelscore op in het bereik 0-1 ([Klik voor meer informatie over de score](https://cloud.google.com/recaptcha-enterprise/docs/interpret-assessment#interpret_scores)). Scores groter dan of gelijk aan de drempelscores identificeren menselijke interactie, anders beschouwd als beide interactie.

      > Opmerking:
      >
      > * Formulierauteurs kunnen een score opgeven in het bereik dat geschikt is voor ononderbroken formulierverzending.

   1. Selecteren **[!UICONTROL Create]** om de configuratie van de cloudservice te maken.

   1. Geef in het dialoogvenster Component bewerken de naam, de project-id, de sitetoets en de API-sleutel op (verkregen in stap 2 en 3), selecteer het toetstype en voer de drempelscore in. Selecteren **[!UICONTROL Save Settings]** en selecteer vervolgens **[!UICONTROL OK]** de configuratie voltooien.

Zodra de reCAPTCHA Enterprise-service is ingeschakeld, is deze beschikbaar voor gebruik in adaptieve formulieren. Zie [gebruik van CAPTCHA in adaptieve vormen](#using-reCAPTCHA).

![reCAPTCHA Enterprise](/help/forms/using/assets/recaptcha1-enterprise.png)


### Google reCAPTCHA v2 configureren {#steps-to-implement-reCAPTCHA-v2-in-forms}

1. Verkrijgen [reCAPTCHA API-sleutelpaar](https://www.google.com/recaptcha/admin) uit Google. Het omvat een **site-sleutel** en **geheime sleutel**.
1. Configuratiecontainer maken voor cloudservices.
   1. Ga naar **[!UICONTROL Tools > General > Configuration Browser]**. Zie de [Configuratiebrowser](/help/sites-administering/configurations.md) documentatie voor meer informatie.
   1. Ga als volgt te werk om de algemene map voor cloudconfiguraties in te schakelen of sla deze stap over om een andere map voor cloudserviceconfiguraties te maken en te configureren.

      1. In Browser van de Configuratie, selecteer **[!UICONTROL global]** map en selecteer **[!UICONTROL Properties]**.

      1. Schakel in het dialoogvenster Configuratieeigenschappen de optie **[!UICONTROL Cloud Configurations]**.
      1. Selecteren **[!UICONTROL Save & Close]** om de configuratie op te slaan en het dialoogvenster af te sluiten.

   1. In Browser van de Configuratie, selecteer **[!UICONTROL Create]**.
   1. Geef in het dialoogvenster Configuratie maken een titel op voor de map en schakel **[!UICONTROL Cloud Configurations]**.
   1. Selecteren **[!UICONTROL Create]** om de map te maken die is ingeschakeld voor configuraties van de cloudservice.

1. Configureer de cloudservice voor reCAPTCHA v2.

   1. Ga naar de AEM ![gereedschappen-1](assets/tools-1.png) > **Cloud Servicen**.
   1. Selecteer **[!UICONTROL reCAPTCHA]**. De pagina Configurations wordt geopend. Selecteer de configuratiecontainer die in de vorige stap is gemaakt en selecteer **[!UICONTROL Create]**.
   1. Selecteer versie als reCAPTCHA v2, geef Naam, Sitetoets en Geheime sleutel voor de service reCAPTCHA op (verkregen in stap 1) en selecteer **[!UICONTROL Create]** om de configuratie van de cloudservice te maken.
   1. Geef in het dialoogvenster Component bewerken de site en de geheime sleutels op die in stap 1 zijn verkregen. Selecteren **[!UICONTROL Save Settings]** en selecteer vervolgens **OK** de configuratie voltooien.

   Zodra de reCAPTCHA-service is geconfigureerd, is deze beschikbaar voor gebruik in adaptieve formulieren. Zie voor meer informatie [gebruik van CAPTCHA in adaptieve vormen](#using-captcha).

![reCAPTCHA v2](/help/forms/using/assets/recaptcha-v2.png)


## reCAPTCHA gebruiken in adaptieve formulieren {#using-reCAPTCHA}

ReCAPTCHA in adaptieve vorm gebruiken:

1. Open een adaptief formulier in de bewerkingsmodus.

   >[!NOTE]
   >
   >Zorg ervoor dat de configuratiecontainer die is geselecteerd bij het maken van het adaptieve formulier, de reCAPTCHA-cloudservice bevat. U kunt ook adaptieve formuliereigenschappen bewerken om de configuratiecontainer te wijzigen die aan het formulier is gekoppeld.

1. Sleep vanuit de componentbrowser de **Captcha** op het adaptieve formulier.

   >[!NOTE]
   >
   >Het gebruik van meer dan één Captcha-component in een adaptieve vorm wordt niet ondersteund. Het wordt ook afgeraden om CAPTCHA te gebruiken in een deelvenster dat is gemarkeerd voor wazig laden of in een fragment.

   >[!NOTE]
   >
   >Captcha is tijdgevoelig en verloopt over ongeveer een minuut. Daarom wordt aangeraden de component Captcha vlak voor de knop Verzenden in het aangepaste formulier te plaatsen.

1. Selecteer de component Captcha die u hebt toegevoegd en selecteer ![cmppr](assets/cmppr.png) om de eigenschappen te bewerken.
1. Geef een titel op voor de CAPTCHA-widget. De standaardwaarde is **Captcha**. Selecteren **Titel verbergen** als u de titel niet wilt weergeven.
1. Van de **Captcha-service** vervolgkeuzelijst, selecteert u **reCAPTCHA** om de dienst reCAPTCHA toe te laten als u het zoals die in vormde [reCAPTCHA-service van Google](#google-reCAPTCHA).
1. Selecteer een configuratie in het keuzemenu Instellingen.
1. **Als de geselecteerde configuratie een versie reCAPTCHA Enterprise heeft**:
   1. U kunt de reCAPTCHA-cloudconfiguratie selecteren met **sleuteltype** als **selectievakje**. In checkbox zeer belangrijk type verschijnt het aangepaste foutenbericht als gealigneerd bericht als de bevestiging captcha ontbreekt. U kunt de grootte selecteren als **[!UICONTROL Normal]** en **[!UICONTROL Compact]**.
   1. U kunt de reCAPTCHA-cloudconfiguratie selecteren met **sleuteltype** als **op basis van score**. In op score gebaseerde sleuteltype toont het aangepaste foutbericht als pop-upbericht als de validatie van captcha mislukt.
   1. Wanneer u een **[!UICONTROL Bind Reference]** de ingediende gegevens zijn gebonden, anders zijn het niet-gebonden gegevens. Hieronder volgen XML-voorbeelden van niet-gebonden gegevens en gebonden gegevens (met bind verwijzing als SSN), wanneer een formulier wordt verzonden.

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


   **Als de geselecteerde configuratie versie reCAPTCHA v2 heeft**:
   1. De grootte selecteren als **[!UICONTROL Normal]** of **[!UICONTROL Compact]** voor de reCAPTCHA-widget. U kunt ook de optie **[!UICONTROL Invisible]** optie om de CAPTCHA-uitdaging alleen te tonen als er verdachte activiteit is. De **beveiligd door reCAPTCHA** de badge, die hieronder wordt weergegeven, wordt weergegeven op de beveiligde formulieren.

      ![Google beveiligd door reCAPTCHA-badge](/help/forms/using/assets/google-recaptcha-v2.png)


   De reCAPTCHA-service is ingeschakeld op het adaptieve formulier. U kunt een voorbeeld van het formulier bekijken en de CAPTCHA bekijken.

1. Sla de eigenschappen op.

>[!NOTE]
> 
> Niet selecteren **[!UICONTROL Default]** van de de dienstdrop-down Captcha aangezien de standaard AEM dienst CAPTCHA wordt afgekeurd.

### CAPTCHA-component tonen of verbergen op basis van regels {#show-hide-captcha}

U kunt de component CAPTCHA weergeven of verbergen op basis van de regels die u toepast op een component in een adaptief formulier. Selecteer de component ![regels bewerken](assets/edit-rules-icon.svg)en selecteert u **[!UICONTROL Create]** om een regel te maken. Zie voor meer informatie over het maken van regels [Regeleditor](rule-editor.md).

De component CAPTCHA moet bijvoorbeeld alleen in een adaptief formulier worden weergegeven als het veld Waarde valuta in het formulier een waarde heeft van meer dan 25000.

Selecteer de **[!UICONTROL Currency Value]** in het formulier en stel de volgende regels in:

![Regels tonen of verbergen](assets/rules-show-hide-captcha.png)

>[!NOTE]
>
> * Als u de v2-configuratie reCAPTCHA selecteert met de grootte als **[!UICONTROL Invisible]** of reCAPTCHA Enterprise score based keys, dan is de optie show/hide niet van toepassing.

### CAPTCHA valideren {#validate-captcha}

U kunt CAPTCHA valideren in een adaptief formulier wanneer u het formulier verzendt of de CAPTCHA-validatie baseert op gebruikersacties en -voorwaarden.

#### CAPTCHA valideren bij het verzenden van formulieren {#validation-form-submission}

Een CAPTCHA automatisch valideren wanneer u een adaptief formulier verzendt:

1. Selecteer de component CAPTCHA en selecteer ![cmppr](assets/configure-icon.svg) om de componenteigenschappen weer te geven.
1. In de **[!UICONTROL Validate CAPTCHA]** sectie, selecteert u **[!UICONTROL Validate CAPTCHA at form submission]**.
1. Selecteren ![Gereed](assets/save_icon.svg) om de componenteigenschappen op te slaan.

#### CAPTCHA bij gebruikershandelingen en -voorwaarden valideren {#validate-captcha-user-action}

Een CAPTCHA valideren op basis van voorwaarden en gebruikersacties:

1. Selecteer de component CAPTCHA en selecteer ![cmppr](assets/configure-icon.svg) om de componenteigenschappen weer te geven.
1. In de **[!UICONTROL Validate CAPTCHA]** sectie, selecteert u **[!UICONTROL Validate CAPTCHA on a user action]**.
1. Selecteren ![Gereed](assets/save_icon.svg) om de componenteigenschappen op te slaan.

   >[!NOTE]
   >
   >
   > Als u de v2-configuratie reCAPTCHA selecteert met de grootte als **[!UICONTROL Invisible]** of reCAPTCHA Enterprise score based keys, dan is Geldig Captcha voor een gebruikersactie niet van toepassing.

[!DNL Experience Manager Forms] verstrekt `ValidateCAPTCHA` API om CAPTCHA te valideren met behulp van vooraf gedefinieerde voorwaarden. U kunt de API aanroepen met behulp van een aangepaste verzendactie of door regels voor componenten in een adaptief formulier te definiëren.

Hier volgt een voorbeeld van een `ValidateCAPTCHA` API voor validatie van CAPTCHA met behulp van vooraf gedefinieerde voorwaarden:

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

In het voorbeeld wordt aangegeven dat de `ValidateCAPTCHA` API valideert de CAPTCHA alleen in het formulier als het aantal cijfers in het numerieke vak dat door de gebruiker is opgegeven tijdens het invullen van het formulier groter is dan 5.

**Optie 1: gebruiken [!DNL Experience Manager Forms] De API ValidateCAPTCHA om CAPTCHA te valideren met behulp van een aangepaste verzendactie**

Voer de volgende stappen uit om de `ValidateCAPTCHA` API om CAPTCHA te valideren met behulp van een aangepaste verzendhandeling:

1. Voeg het script toe dat het `ValidateCAPTCHA` API voor aangepaste verzendhandeling. Zie voor meer informatie over aangepaste verzendhandelingen [Een aangepaste verzendactie maken voor Adaptieve Forms](custom-submit-action-form.md).
1. Selecteer de naam van de aangepaste handeling Verzenden in het menu **[!UICONTROL Submit Action]** vervolgkeuzelijst in **[!UICONTROL Submission]** eigenschappen van een adaptief formulier.
1. Selecteer **[!UICONTROL Submit]**. De CAPTCHA wordt gevalideerd op basis van de in `ValidateCAPTCHA` API van de aangepaste handeling Verzenden.

**Optie 2: Gebruik [!DNL Experience Manager Forms] De API van ValidateCAPTCHA om CAPTCHA op een gebruikersactie te bevestigen alvorens de vorm voor te leggen**

U kunt ook `ValidateCAPTCHA` API door regels toe te passen op een component in een adaptief formulier.

U voegt bijvoorbeeld een **[!UICONTROL Validate CAPTCHA]** in een adaptief formulier en maak een regel om een service aan te roepen bij het klikken op een knop.

Het volgende cijfer illustreert hoe u de dienst op de klik van een **[!UICONTROL Validate CAPTCHA]** knop:

![CAPTCHA valideren](assets/captcha-validation1.gif)

U kunt de aangepaste servlet die omvat aanroepen `ValidateCAPTCHA` API die de regelredacteur gebruikt en laat of maakt de verzendknoop van het Aangepaste Vorm toe die op het bevestigingsresultaat wordt gebaseerd.

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
