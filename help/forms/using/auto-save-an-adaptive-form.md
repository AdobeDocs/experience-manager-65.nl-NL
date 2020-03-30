---
title: Een adaptief formulier automatisch opslaan
seo-title: Een adaptief formulier automatisch opslaan
description: U kunt een adaptief formulier zodanig configureren dat de inhoud automatisch wordt opgeslagen op basis van een gebeurtenis of een vooraf gedefinieerd tijdsinterval
seo-description: U kunt een adaptief formulier zodanig configureren dat de inhoud automatisch wordt opgeslagen op basis van een gebeurtenis of een vooraf gedefinieerd tijdsinterval
uuid: 0fe9a389-269b-438a-9489-d9d1d09558a1
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: author
discoiquuid: d519ac4e-6d29-4a69-874e-792acabe87ff
translation-type: tm+mt
source-git-commit: 317fadfe48724270e59644d2ed9a90fbee95cf9f

---


# Een adaptief formulier automatisch opslaan {#auto-save-an-adaptive-form}

U kunt een adaptief formulier zodanig configureren dat de inhoud automatisch wordt opgeslagen op basis van een gebeurtenis of een vooraf gedefinieerd tijdsinterval. Standaard wordt de inhoud van een adaptief formulier opgeslagen op een handeling van de gebruiker, bijvoorbeeld wanneer u op de knop Opslaan drukt. De optie Automatisch opslaan is handig in:

* De inhoud automatisch opslaan voor anonieme en aangemelde gebruikers
* De inhoud van een formulier opslaan zonder minimale tussenkomst van de gebruiker
* Inhoud van een formulier opslaan op basis van een gebruikersgebeurtenis
* De inhoud van een formulier herhaaldelijk opslaan na een opgegeven tijdsinterval

## Automatisch opslaan inschakelen voor een adaptief formulier {#enable-autosave-for-an-adaptive-form}

Voor een adaptief formulier is de optie voor automatisch opslaan niet uitgeschakeld. U kunt de optie Automatisch opslaan inschakelen in de sectie **Automatisch opslaan** in de eigenschappen van een adaptief formulier. De sectie **Automatisch opslaan** bevat ook diverse andere configuratieopties. Voer de volgende stappen uit om de optie Automatisch opslaan in te schakelen en te configureren voor een adaptief formulier:

1. Als u de sectie Automatisch opslaan wilt openen in de eigenschappen, selecteert u een component en tikt u op ![veldniveau](assets/field-level.png) > **[!UICONTROL Aangepaste formuliercontainer]**. Tik vervolgens op ![cmp](assets/cmppr.png).
1. In de sectie **[!UICONTROL Automatisch opslaan]** **[!UICONTROL schakelt]** u de optie Automatisch opslaan in.
1. Geef in het vak **[!UICONTROL Adaptieve formuliergebeurtenis]** 1 of TRUE op om het formulier automatisch op te slaan wanneer het formulier in de browser wordt geladen. U kunt ook een voorwaardelijke expressie opgeven voor een gebeurtenis die, wanneer deze wordt geactiveerd en waar wordt geretourneerd, de inhoud van het formulier opslaat.
1. Geef de trigger op. Automatisch opslaan wordt geactiveerd op basis van uw configuratie. U kunt kiezen uit de volgende opties:

   * **[!UICONTROL Gebaseerd op tijd:]** Selecteer de optie om de inhoud op te slaan op basis van een specifiek tijdsinterval.
   * **[!UICONTROL Gebaseerd op gebeurtenis:]** Selecteer de optie om de inhoud op te slaan op basis van een gebeurtenis die wordt gestart.
   Wanneer u een trigger selecteert, wordt het vak Strategieconfiguratie ingeschakeld. Met het vak Strategieconfiguratie kunt u:

   * Geef een tijdsinterval op als u **[!UICONTROL Op tijd gebaseerde]** trigger selecteert.
   * Geef een naam voor de gebeurtenis op als u een trigger op basis van **[!UICONTROL gebeurtenissen]** selecteert.
   U kunt ook uw eigen aangepaste strategie maken en aan de lijst toevoegen. Zie Een aangepaste strategie [implementeren om de formulieren](/help/forms/using/auto-save-an-adaptive-form.md#p-implement-a-custom-strategy-to-enable-autosave-for-adaptive-forms-p)automatisch op te slaan voor meer informatie.

1. (Alleen op tijd gebaseerde automatische opslag) Voer de volgende stappen uit om opties voor op tijd gebaseerde automatische opslag te configureren.

   1. Geef in het vak **[!UICONTROL Automatisch opslaan op dit interval]** het tijdsinterval in seconden op. Het formulier wordt herhaaldelijk opgeslagen nadat het aantal seconden is verstreken dat in het intervalvak is opgegeven.

1. (Alleen op gebeurtenissen gebaseerde automatische opslag) Voer de volgende stappen uit om opties voor automatisch opslaan op basis van gebeurtenissen te configureren.

   1. Geef in het vak **Automatisch opslaan na deze gebeurtenis** een [GuideBridge](https://helpx.adobe.com/aem-forms/6/javascript-api/GuideBridge.html) -gebeurtenis op. Het formulier wordt opgeslagen telkens wanneer de expressie de waarde TRUE oplevert.

1. (Optioneel) Als u de inhoud automatisch wilt opslaan voor anonieme gebruikers, selecteert u de optie Automatisch opslaan **inschakelen voor anonieme gebruikers** en klikt u op **[!UICONTROL OK]**.

   >[!NOTE]
   >
   >Als u de optie Automatisch opslaan wilt gebruiken voor anonieme gebruikers, moet u de Forms Common Configuration Service zodanig configureren dat alle gebruikers formulieren kunnen bekijken, verifiëren en ondertekenen.
   >
   >Om de dienst te vormen, ga naar de configuratie van de Console van het Web AEM bij `https://server:port/system/console/configMgr` en geef de Gemeenschappelijke Dienst **[!UICONTROL van de Configuratie van]** Vormen uit om de optie **[!UICONTROL Alle Gebruikers]** op het **[!UICONTROL Allow]** gebied te kiezen, en sparen de configuratie.

## Een aangepaste strategie implementeren om automatisch opslaan van aangepaste formulieren in te schakelen {#implement-a-custom-strategy-to-enable-autosave-for-adaptive-forms}

U kunt een aangepaste gebeurtenis implementeren om de functie voor automatisch opslaan te activeren. Voer de volgende stappen uit om de aangepaste gebeurtenis te maken en te implementeren:

1. Maak clientbibliotheek en clientbibliotheekmappen. Zie het document [Client-Side Libraries](/help/sites-developing/clientlibs.md)gebruiken voor gedetailleerde stappen.

   In het volgende script wordt bijvoorbeeld de aangepaste `emailFocusChange`gebeurtenis gebruikt om de functie voor automatisch opslaan te activeren:

   ```
   window.addEventListener("bridgeInitializeStart", function (){
       guideBridge.connect(function () { guideBridge.on("elementFocusChanged", function (event,data) {
           if(data.target.name === 'Email') {
               guideBridge.trigger("emailFocusChange");
           }
       });
      });
   });
   ```

   >[!NOTE]
   >
   >Een categorie-eigenschap wordt gedefinieerd tijdens het maken van de clientbibliotheekmappen. Houd de waarde die aan categorie-eigenschap is toegewezen, bij de hand.

1. Open het adaptieve formulier in de modus Schrijven.

1. Selecteer in de bewerkingsmodus een component, tik vervolgens op ![veldniveau](assets/field-level.png) > **[!UICONTROL Aangepaste formuliercontainer]** en tik vervolgens op ![cmr](assets/cmppr.png).
1. Open in de eigenschappen de sectie **[!UICONTROL Standaard]** . Voer in het vak **** Clientbibliotheek de waarde in van de categorie-eigenschap die is gedefinieerd tijdens het maken van de clientbibliotheekmappen.
1. Open de sectie Automatisch opslaan. Geef in het vak **[!UICONTROL Automatisch opslaan na deze gebeurtenis]** een aangepaste gebeurtenis op die al in de clientbibliotheek is gedefinieerd. Click **[!UICONTROL OK]**.

