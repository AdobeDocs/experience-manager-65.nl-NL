---
title: Hoe hCaptcha&amp gebruiken;reg; in een AEM 6.5 Forms?
description: Verbeter de formulierbeveiliging met hCaptcha&reg; service zonder problemen. Stap-voor-stap gids binnen!
feature: Adaptive Forms, Foundation Components
role: User, Developer
source-git-commit: a4e155de8a4f60d3746cecea110466b1d5d44dbb
workflow-type: tm+mt
source-wordcount: '828'
ht-degree: 0%

---

# Sluit uw AEM Forms-omgeving aan met hCaptcha® {#connect-your-forms-environment-with-hcaptcha-service}

<!--

<span class="preview"> This feature is under the Early Adopter Program. You can write to aem-forms-ea@adobe.com from your official email id to join the early adopter program and request access to the capability. </span>

-->

<span class="preview"> Deze functie valt onder het programma voor vroege adoptie. Als u interesse hebt in deelname aan ons programma voor vroege toegang tot deze functie, stuurt u een e-mail van uw officiële adres naar aem-forms-ea@adobe.com om toegang aan te vragen </span>

CAPTCHA (Complete Automated Public Turing test to tell Computers and Humans Apart) is een programma dat vaak wordt gebruikt bij online transacties om onderscheid te maken tussen mensen en geautomatiseerde programma&#39;s of bots. Het stelt een uitdaging en evalueert de reactie van de gebruiker om te bepalen of het een mens of bot is die met de site communiceert. Het verhindert de gebruiker om te werk te gaan als de test ontbreekt en de hulp maakt online transacties veilig door bots te houden spam of kwaadwillige doeleinden posten.

Naast hCaptcha® biedt AEM Forms 6.5 ondersteuning voor de volgende CAPTCHA-oplossingen:

* [Google reCAPTCHA](/help/forms/using/captcha-adaptive-forms.md)
* [Cloudflare Turnstile](/help/forms/using/integrate-adaptive-forms-turnstile.md)

## AEM Forms-omgeving integreren met hCaptcha®

De service Captcha® beschermt uw formulieren tegen bots, spam en automatisch misbruik. Er wordt een widget selectievakje ingesteld en de reactie van de gebruiker geëvalueerd om te bepalen of het een mens of bot is die met het formulier communiceert. Het verhindert de gebruiker om te werk te gaan als de test ontbreekt en de hulp maakt online transacties veilig door bots te houden spam of kwaadwillige activiteiten posten.

AEM 6.5 Adaptieve Forms biedt ondersteuning voor hCaptcha&amp;reg. U kunt dit gebruiken om een widget-uitdaging voor selectievakjes weer te geven bij het verzenden van een formulier.

<!-- ![hCaptcha&reg;](assets/hCaptcha&reg;-challenge.png)-->


### Vereisten om de AEM Forms-omgeving te integreren met hCaptcha® {#prerequisite}

Om hCaptcha® met AEM Forms te vormen, moet u [ hCaptcha® plaatsleutel en geheime sleutel ](https://docs.hcaptcha.com/switch/#get-your-hcaptcha-sitekey-and-secret-key) van de website hCaptcha® verkrijgen.

### Captcha® configureren {#steps-to-configure-hcaptcha}

Voer de volgende stappen uit om AEM Forms te integreren met de service hCaptcha®:

1. Maak een configuratiecontainer op uw AEM Forms-omgeving, die cloudconfiguraties bevat waarmee AEM verbinding maken met externe services. Een configuratiecontainer maken:
   1. Open uw AEM Forms-omgeving.
   1. Ga naar **[!UICONTROL Tools > General > Configuration Browser]** .
   1. In Browser van de Configuratie, kunt u een bestaande omslag selecteren of een nieuwe omslag creëren:
      * Een nieuwe map maken en Cloud Configurations inschakelen:
         1. Klik op **[!UICONTROL Create]** in de Configuration Browser.
         1. Geef in het dialoogvenster Configuratie maken een naam, titel en controle op **[!UICONTROL Cloud Configurations]** .
         1. Klik op **[!UICONTROL Create]**.
      * Cloud Configuration inschakelen voor een bestaande map:
         1. Selecteer de map in de Configuration Browser en selecteer **[!UICONTROL Properties]** .
         1. Schakel in het dialoogvenster Configuration Properties **[!UICONTROL Cloud Configurations]** in.
         1. Klik op **[!UICONTROL Save & Close]** om de configuratie op te slaan en het dialoogvenster af te sluiten.

1. Configureer uw Cloud Servicen:
   1. Op uw AEM auteursinstantie, ga ![ hulpmiddelen-1 ](assets/tools-1.png) > **[!UICONTROL Cloud Services]** en klik **[!UICONTROL hCaptcha®]**.
      ![ hCaptcha® in ui ](assets/hcaptcha-in-ui.png)
   1. Selecteer een configuratiecontainer, gecreeerd of bijgewerkt, zoals die in de vorige sectie wordt beschreven. Selecteer **[!UICONTROL Create]** .
      ![ Configuratie hCaptcha® ](assets/config-hcaptcha.png)
   1. Opgeven **[!UICONTROL Title]**, <!--**[!UICONTROL Name]**--> **[!UICONTROL Site Key]**, en **[!UICONTROL Secret Key]** voor de dienst hCaptcha® [ die in Vereiste ](#prerequisite) wordt verkregen.
   1. Klik op **[!UICONTROL Create]**.

      ![ vorm de Cloud Service om uw milieu van AEM Forms met hCaptcha® ](assets/create-hcaptcha-config.png) te verbinden

   >[!NOTE]
   > De gebruikers moeten niet [ cliënt-zijbevestiging URL van JavaScript ](https://docs.hcaptcha.com/#add-the-hcaptcha-widget-to-your-webpage) en [ server-zijbevestiging URL ](https://docs.hcaptcha.com/#verify-the-user-response-server-side) wijzigen aangezien zij reeds voor bevestiging hCaptcha® worden voorgevuld.

   Zodra de hCAPTCHA-service is geconfigureerd, is deze beschikbaar voor gebruik in uw adaptieve vorm.

## hCaptcha® gebruiken in een adaptieve Forms {#using-hCaptcha-in-aem-6.5}

1. Open uw AEM Forms-omgeving.
1. Ga naar **[!UICONTROL Forms]** > **[!UICONTROL Forms and Documents]** .
1. Selecteer een adaptief formulier en klik op **[!UICONTROL Properties]** .
1. Selecteer in het **[!UICONTROL Configuration Container]** de Cloud Configuration for hCaptcha®.
1. Klik op **[!UICONTROL Save & Close]**.

   Als u geen dergelijke Container van de Configuratie hebt, zie sectie [ uw milieu van AEM Forms met hCaptcha® ](#connect-your-forms-environment-with-hcaptcha-service) verbinden om te begrijpen hoe te om een Container van de Configuratie tot stand te brengen.

   ![ Uitgezochte Container van de Configuratie ](/help/forms/using/assets/captcha-properties.png)

1. Selecteer een adaptief formulier en klik op **[!UICONTROL Edit]** om het formulier in de editor te openen.
1. Sleep vanuit de browser van de component de component **[!UICONTROL Adaptive Form hCaptcha®]** naar het adaptieve formulier of voeg deze toe.
1. Selecteer de **[!UICONTROL Adaptive Form hCaptcha®]** component, en klik eigenschappen ![ pictogram van Eigenschappen ](assets/configure-icon.svg) om de eigenschappendialoog te openen. Geef de volgende eigenschappen op:

   ![ hCaptcha® v1 ](assets/config-hcaptcha-v1-img.png)

   * **[!UICONTROL Title]:** specificeer de titel voor uw component Captcha.
   * **[!UICONTROL Validation Message]:** Geef een validatiebericht op voor uw Captcha-validatie bij het verzenden van formulieren of bij een gebruikersactie.
   * **[!UICONTROL Captcha Service]:** Selecteer de CAPTCHA-service voor het verzenden van uw formulier, hier selecteert u hCaptcha®.
   * **[!UICONTROL Configuration Settings]:** selecteer uw Configuratie van de Wolk die voor hCaptcha® wordt gevormd.
     >[!NOTE]
     >U kunt voor een vergelijkbaar doel meerdere Cloud Configurations in uw omgeving gebruiken. Kies de service dus zorgvuldig. Als geen dienst vermeld is, zie [ uw milieu van AEM Forms met hCaptcha® ](#connect-your-forms-environment-with-hcaptcha-service) verbinden om te leren hoe te om een Cloud Service tot stand te brengen die uw milieu van AEM Forms met de dienst hCaptcha® verbindt.
   * **Bericht van de Fout:** verstrek het foutenbericht aan vertoning aan de gebruiker wanneer de voorlegging Captcha ontbreekt.
   * **Grootte Captcha:** U kunt de vertoningsgrootte van de hCaptcha® uitdagingsdialoog selecteren. Gebruik de optie **[!UICONTROL Compact]** om een klein formaat weer te geven en **[!UICONTROL Normal]** om een relatief groot hCaptcha®-provocatiedialoogvenster weer te geven of **[!UICONTROL Invisible]** om hCaptcha® te valideren zonder de widget selectievakje expliciet in de gebruikersinterface weer te geven.

1. Selecteer **[!UICONTROL Done]** .


Alleen legitieme formulieren waarin de invuller van het formulier de uitdaging van de hCaptcha®-service met succes heeft verholpen, kunnen nu worden verzonden. hCaptcha®

**hCaptcha® is een geregistreerd handelsmerk van de Machines van de Intusie, Inc.**


## Veelgestelde vragen

* **Q: Kan ik meer dan één component Captcha in een Aangepaste Vorm gebruiken?**
* **Ans:** het gebruiken van meer dan één component Captcha in een AanpassingsVorm wordt niet gesteund. Het wordt ook afgeraden een Captcha-component te gebruiken in een fragment of een deelvenster dat is gemarkeerd voor wazig laden.

## Zie ook {#see-also}

* [CAPTCHA gebruiken in aangepaste vormen](/help/forms/using/captcha-adaptive-forms.md)
* [Turnstile Captcha gebruiken in adaptieve vormen](/help/forms/using/integrate-adaptive-forms-turnstile.md)
