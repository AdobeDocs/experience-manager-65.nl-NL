---
title: CAPTCHA gebruiken in aangepaste vormen
seo-title: CAPTCHA gebruiken in aangepaste vormen
description: Leer hoe u AEM CAPTCHA- of Google reCAPTCHA-service configureert in adaptieve formulieren.
seo-description: Leer hoe u AEM CAPTCHA- of Google reCAPTCHA-service configureert in adaptieve formulieren.
uuid: 0e11e98a-12ac-484c-b77f-88ebdf0f40e5
contentOwner: vishgupt
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: adaptive_forms, author
discoiquuid: 4c53dfc0-25ca-419d-abfe-cf31fc6ebf61
docset: aem65
translation-type: tm+mt
source-git-commit: 46f2ae565fe4a8cfea49572eb87a489cb5d9ebd7
workflow-type: tm+mt
source-wordcount: '647'
ht-degree: 0%

---


# CAPTCHA gebruiken in aangepaste vormen{#using-captcha-in-adaptive-forms}

CAPTCHA (Complete Automated Public Turing test to tell Computers and Humans Apart) is een programma dat vaak wordt gebruikt bij online transacties om onderscheid te maken tussen mensen en geautomatiseerde programma&#39;s of bots. Het stelt een uitdaging en evalueert de reactie van de gebruiker om te bepalen of het een mens of bot is die met de site communiceert. Het verhindert de gebruiker om te werk te gaan als de test ontbreekt en de hulp maakt online transacties veilig door bots te houden spam of kwaadwillige doeleinden posten.

AEM Forms ondersteunt CAPTCHA in adaptieve vormen. U kunt de reCAPTCHA-service van Google gebruiken om CAPTCHA te implementeren.

>[!NOTE]
>
>* AEM Forms biedt alleen ondersteuning voor reCaptcha v2. Andere versies worden niet ondersteund.
>* CAPTCHA in adaptieve formulieren wordt niet ondersteund in de offlinemodus van de AEM Forms-app.

>



## De ReCAPTCHA-service van Google configureren {#google-recaptcha}

Auteurs van formulieren kunnen de reCAPTCHA-service van Google gebruiken om CAPTCHA in adaptieve formulieren te implementeren. Het biedt geavanceerde CAPTCHA-mogelijkheden om uw site te beschermen. Zie [Google reCAPTCHA voor meer informatie over hoe reCAPTCHA werkt](https://developers.google.com/recaptcha/).

![Recaptcha](assets/recaptcha_new.png)

De reCAPTCHA-service implementeren in AEM Forms:

1. Haal [reCAPTCHA API sleutelpaar](https://www.google.com/recaptcha/admin) op van Google. De site bevat een sleutel en een geheim.
1. Configuratiecontainer maken voor cloudservices.

   1. Go to **[!UICONTROL Tools > General > Configuration Browser]**.
   1. Ga als volgt te werk om de algemene map voor cloudconfiguraties in te schakelen of sla deze stap over om een andere map voor cloudserviceconfiguraties te maken en te configureren.

      1. Selecteer de **[!UICONTROL global]** map in de configuratiegrowser en tik op **[!UICONTROL Properties]**.

      1. Schakel in het dialoogvenster Configuration Properties de optie **[!UICONTROL Cloud Configurations]**.
      1. Tik **[!UICONTROL Save & Close]** om de configuratie op te slaan en het dialoogvenster af te sluiten.
   1. Tik in de configuratievenster op **[!UICONTROL Create]**.
   1. Geef in het dialoogvenster Configuratie maken een titel op voor de map en schakel deze in **[!UICONTROL Cloud Configurations]**.
   1. Tik **[!UICONTROL Create]** om de map te maken die geschikt is voor configuraties van de cloudservice.


1. Configureer de cloudservice voor reCAPTCHA.

   1. Ga voor de AEM auteur naar ![tools-1](assets/tools-1.png) > **Cloud Services**.
   1. Tik op **[!UICONTROL reCAPTCHA]**. De pagina Configurations wordt geopend. Selecteer de configuratiecontainer die in de vorige stap is gemaakt en tik op **[!UICONTROL Create]**.
   1. Geef Naam, Sitecode en Geheime sleutel voor de service reCAPTCHA op en tik **[!UICONTROL Create]** om de configuratie van de cloudservice te maken.
   1. Geef in het dialoogvenster Component bewerken de site en de geheime sleutels op die in stap 1 zijn verkregen. Tik op Instellingen **** opslaan en tik vervolgens op **OK** om de configuratie te voltooien.

   Zodra de reCAPTCHA-service is geconfigureerd, is deze beschikbaar voor gebruik in adaptieve formulieren. Zie CAPTCHA [gebruiken in adaptieve vormen](#using-captcha)voor meer informatie.

## CAPTCHA gebruiken in aangepaste vormen {#using-captcha}

CAPTCHA in adaptieve vorm gebruiken:

1. Open een adaptief formulier in de bewerkingsmodus.

   >[!NOTE]
   >
   >Zorg ervoor dat de configuratiecontainer die is geselecteerd bij het maken van het adaptieve formulier, de reCAPTCHA-cloudservice bevat. U kunt ook adaptieve formuliereigenschappen bewerken om de configuratiecontainer te wijzigen die aan het formulier is gekoppeld.

1. Sleep de component **Captcha** vanuit de deelbrowser naar het aangepaste formulier.

   >[!NOTE]
   >
   >Het gebruik van meer dan één Captcha-component in een adaptieve vorm wordt niet ondersteund. Het wordt ook afgeraden om CAPTCHA te gebruiken in een deelvenster dat is gemarkeerd voor wazig laden of in een fragment.

   >[!NOTE]
   >
   >Captcha is tijdgevoelig en verloopt over ongeveer een minuut. Daarom wordt aangeraden de component Captcha vlak voor de knop Verzenden in het aangepaste formulier te plaatsen.

1. Selecteer de Captcha-component die u hebt toegevoegd en tik op ![cmp](assets/cmppr.png) om de eigenschappen ervan te bewerken.
1. Geef een titel op voor de CAPTCHA-widget. The default value is **Captcha**. Selecteer Titel **** verbergen als u de titel niet wilt weergeven.
1. Selecteer in het vervolgkeuzemenu **Captcha** de optie **reCaptcha** om de service reCAPTCHA in te schakelen als u deze hebt geconfigureerd zoals beschreven in de [ReCAPTCHA-service van Google](#google-recaptcha). Selecteer een configuratie in het keuzemenu Instellingen. Selecteer ook de grootte als **Normaal** of **Compact** voor de reCAPTCHA-widget.

   >[!NOTE]
   >
   >Selecteer geen **[!UICONTROL Default]** uit de de dienstdrop-down Captcha aangezien de standaard AEM dienst CAPTCHA wordt afgekeurd.

1. Sla de eigenschappen op.

De reCAPTCHA-service is ingeschakeld op het adaptieve formulier. U kunt een voorbeeld van het formulier bekijken en de CAPTCHA bekijken.
