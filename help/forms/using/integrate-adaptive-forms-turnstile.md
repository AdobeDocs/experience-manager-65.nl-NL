---
title: Hoe wordt Turnstile gebruikt in een AEM adaptieve vorm 6.5?
description: Verbeter de formulierbeveiliging met de Turnstile-service zonder moeite. Stap-voor-stap gids binnen!
feature: Adaptive Forms, Foundation Components
role: User, Developer
source-git-commit: a4e155de8a4f60d3746cecea110466b1d5d44dbb
workflow-type: tm+mt
source-wordcount: '806'
ht-degree: 0%

---

# Verbind uw AEM Forms-omgeving met Turnstift {#connect-your-forms-environment-with-turnstile-service}

<!--

<span class="preview"> This feature is under the Early Adopter Program. You can write to aem-forms-ea@adobe.com from your official email id to join the early adopter program and request access to the capability. </span>

-->

<span class="preview"> Deze functie valt onder het programma voor vroege adoptie. Als u interesse hebt in deelname aan ons programma voor vroege toegang tot deze functie, stuurt u een e-mail van uw officiële adres naar aem-forms-ea@adobe.com om toegang aan te vragen </span>

CAPTCHA (Complete Automated Public Turing test to tell Computers and Humans Apart) is een programma dat vaak wordt gebruikt bij online transacties om onderscheid te maken tussen mensen en geautomatiseerde programma&#39;s of bots. Het stelt een uitdaging en evalueert de reactie van de gebruiker om te bepalen of het een mens of bot is die met de site communiceert. Het verhindert de gebruiker om te werk te gaan als de test ontbreekt en de hulp maakt online transacties veilig door bots te houden spam of kwaadwillige doeleinden posten.

AEM Forms 6.5 ondersteunt de volgende CAPTCHA-oplossingen:

* [Turnstile Captcha](/help/forms/using/integrate-adaptive-forms-turnstile.md)
* [Google reCAPTCHA](/help/forms/using/captcha-adaptive-forms.md)
* [ hCaptcha ](/help/forms/using/integrate-adaptive-forms-hcaptcha.md)


<!-- ![Turnstile](assets/Turnstile-challenge.png)-->

## AEM Forms-omgeving integreren met Turnstile Captcha

Cloudflare Turnstile Captcha is een veiligheidsmaatregel die tot doel heeft formulieren en sites te beschermen tegen geautomatiseerde bots, kwaadaardige aanvallen, spam en ongewenst geautomatiseerd verkeer. Er wordt een selectievakje weergegeven bij het verzenden van formulieren om te controleren of het formulier menselijk is, voordat het formulier kan worden verzonden.

### Vereisten om de AEM Forms-omgeving te integreren met Turnstile Captcha {#prerequisite}

Om Turnstile voor AEM Forms te vormen, moet u [ Turnstile sitekey en geheime sleutel ](https://developers.cloudflare.com/turnstile/get-started/) van de Website van Turnstile verkrijgen.

### Draaien configureren {#steps-to-configure-hcaptcha}

Voer de volgende stappen uit om AEM Forms te integreren met de Turnstile-service:

1. Maak een configuratiecontainer op uw AEM Forms-omgeving. Een configuratiecontainer bevat cloudconfiguraties waarmee AEM Forms wordt verbonden met externe services. Een configuratiecontainer maken:
   1. Open uw AEM Forms-omgeving.
   1. Ga naar **[!UICONTROL Tools > General > Configuration Browser]** .
   1. In Browser van de Configuratie, selecteert u een bestaande omslag of creeert een nieuwe omslag:
      * Om a **nieuwe omslag** tot stand te brengen en de Configuraties van de Wolk toe te laten:
         1. Klik op **[!UICONTROL Create]** in de Configuration Browser.
         1. Geef in het dialoogvenster Configuratie maken een naam, titel en controle op **[!UICONTROL Cloud Configurations]** .
         1. Klik op **[!UICONTROL Create]**.
      * Om de Configuratie van de Wolk voor een **bestaande omslag** toe te laten:
         1. Selecteer de map in de Configuration Browser en klik op **[!UICONTROL Properties]** .
         1. Schakel in het dialoogvenster Configuration Properties **[!UICONTROL Cloud Configurations]** in.
         1. Klik op **[!UICONTROL Save & Close]** om de configuratie op te slaan.

1. Configureer uw Cloud Servicen:
   1. Op uw AEM auteursinstantie, ga ![ hulpmiddelen-1 ](assets/tools-1.png) > **[!UICONTROL Cloud Services]** en klik **[!UICONTROL Turnstile]**.
      ![ Draai in Cloud Servicen ](assets/turnstile-in-ui.png)
   1. Selecteer een configuratiecontainer, gecreeerd of bijgewerkt, zoals die in de vorige sectie wordt beschreven. Klik op **[!UICONTROL Create]**.
      ![ Turnstile van de Configuratie ](assets/config-hcaptcha.png)
   1. Geef **[!UICONTROL Widget Type]** op als beheerd, niet-interactief of onzichtbaar.
   1. Geef andere gegevens op, zoals **[!UICONTROL Title]** , **[!UICONTROL Name]** .
   1. Specificeer **[!UICONTROL Site Key]**, en **[!UICONTROL Secret Key]** voor de Dienst van de Draai [ in voorwaarde wordt verkregen die ](#prerequisite).
   1. Klik op **[!UICONTROL Create]**.

      ![ vorm de Cloud Service om uw milieu van AEM Forms met Turnstile te verbinden ](assets/config-turntstile.png)

   >[!NOTE]
   > Gebruikers hoeven de URL voor JavaScript-validatie aan de clientzijde en de URL voor validatie aan de serverzijde niet aan te passen, omdat deze al zijn voorgevuld voor Microsoft-validatie.

   Zodra de Turnstile Captcha dienst wordt gevormd, is het beschikbaar voor gebruik in uw AanpassingsVorm.

## Draaien in een adaptieve vorm gebruiken {#using-turnstile-aem-6.5}

1. Open uw AEM Forms-omgeving.
1. Ga naar **[!UICONTROL Forms]** > **[!UICONTROL Forms and Documents]** .
1. Selecteer een adaptief formulier en klik op **[!UICONTROL Properties]** . Selecteer in **[!UICONTROL Configuration Container]** de Cloud Configuration for Turnstile®.
1. Klik op **[!UICONTROL Save & Close]**.

   Als u geen dergelijke Container van de Configuratie hebt, zie sectie [ uw milieu van AEM Forms met Draaien ](#connect-your-forms-environment-with-turnstile-service) verbinden om te leren hoe te om een Container van de Configuratie tot stand te brengen.

   ![ Uitgezochte Container van de Configuratie ](assets/captcha-properties.png)

1. Selecteer een adaptief formulier en klik op **[!UICONTROL Edit]** om het aangepaste formulier te openen in de editor.
1. Sleep vanuit de browser van de component de component **[!UICONTROL Adaptive Form Turnstile]** naar het adaptieve formulier of voeg deze toe.
1. Selecteer de **[!UICONTROL Adaptive Form Turnstile]** component en klik eigenschappen ![ pictogram van Eigenschappen ](assets/configure-icon.svg). Hiermee wordt het dialoogvenster met eigenschappen geopend. Geef de volgende eigenschappen op:

   <!--![Turnstile v2](assets/turnstile-settings-v2.png)-->
   ![ de Draai van de Wolk v1 ](assets/turnstile-setting-v1.png)

   * **[!UICONTROL Title]:** specificeer de titel voor uw component Captcha. U kunt een formuliercomponent gemakkelijk herkennen met de unieke titel ervan, zowel in het formulier als in de regeleditor.
   * **[!UICONTROL Configuration Settings]:** selecteer een Cloud-configuratie die voor Turnstile is geconfigureerd.
   * **[!UICONTROL Validation Message]:** Geef een validatiebericht op voor het valideren van Captcha bij het verzenden van formulieren of voor een gebruikersactie.
   * **[!UICONTROL Captcha Service]:** Selecteer de CAPTCHA-service voor het verzenden van uw formulier, hier selecteert u Turnstile®.
   * **[!UICONTROL Configuration Settings]:** selecteer uw Configuratie van de Wolk die voor Turnstile® wordt gevormd.
     >[!NOTE]
     >U kunt voor een vergelijkbaar doel meerdere Cloud Configurations in uw omgeving gebruiken. Kies de service dus zorgvuldig. Als geen de dienst vermeld is, zie [ uw milieu van AEM Forms met Turnstile ](#connect-your-forms-environment-with-turnstile-service) verbinden om te leren hoe te om een Cloud Service tot stand te brengen die uw milieu van AEM Forms met de Dienst van de Draai verbindt.
   * **Bericht van de Fout:** verstrek het foutenbericht aan vertoning aan de gebruiker wanneer de voorlegging Captcha ontbreekt.
   * **Grootte Captcha:** U kunt de vertoningsgrootte van de hCaptcha® uitdagingsdialoog selecteren. Gebruik de optie **[!UICONTROL Compact]** om een klein formaat weer te geven en de optie **[!UICONTROL Normal]** om een relatief groot hCaptcha®-uitdagingsdialoogvenster weer te geven.

1. Selecteer **[!UICONTROL Done]** .


Alleen legitieme formulieren waarin de invuller van het formulier de uitdaging van de Turnstile-service met succes heeft verholpen, kunnen nu worden verzonden.

![ Veranderlijke Uitdaging ](assets/turnstile-challenge.png)


## Veelgestelde vragen

* **Q: Kan ik meer dan één component Captcha in een Aangepaste Vorm gebruiken?**
* **Ans:** het gebruiken van meer dan één component Captcha in een AanpassingsVorm wordt niet gesteund. Het wordt ook afgeraden een Captcha-component te gebruiken in een fragment of een deelvenster dat is gemarkeerd voor wazig laden.

## Zie ook {#see-also}

* [CAPTCHA gebruiken in aangepaste vormen](/help/forms/using/captcha-adaptive-forms.md)
* [Captcha gebruiken in adaptieve vormen](/help/forms/using/integrate-adaptive-forms-hcaptcha.md)