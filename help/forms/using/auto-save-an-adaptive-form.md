---
title: Een adaptief formulier automatisch opslaan
description: U kunt een adaptief formulier zodanig configureren dat de inhoud automatisch wordt opgeslagen op basis van een gebeurtenis of een vooraf gedefinieerd tijdsinterval
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: author
feature: Adaptive Forms,Foundation Components
exl-id: ff9bf466-228d-40e6-9389-15c1f2ed1d2e
solution: Experience Manager, Experience Manager Forms
role: User, Developer
source-git-commit: d7b9e947503df58435b3fee85a92d51fae8c1d2d
workflow-type: tm+mt
source-wordcount: '693'
ht-degree: 0%

---

# Een adaptief formulier automatisch opslaan {#auto-save-an-adaptive-form}

<span class="preview"> de Adobe adviseert gebruikend de moderne en verlengbare gegevens vangen [ Componenten van de Kern ](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/introduction.html) voor [ het creëren van nieuwe Aangepaste Forms ](/help/forms/using/create-an-adaptive-form-core-components.md) of [ het toevoegen van Aangepaste Forms aan de pagina&#39;s van AEM Sites ](/help/forms/using/create-or-add-an-adaptive-form-to-aem-sites-page.md). Deze componenten betekenen een aanzienlijke vooruitgang in de aanmaak van Adaptive Forms en zorgen voor indrukwekkende gebruikerservaring. In dit artikel wordt een oudere aanpak beschreven voor de auteur Adaptive Forms die gebruikmaakt van stichtingscomponenten. </span>

U kunt een adaptief formulier zodanig configureren dat de inhoud automatisch wordt opgeslagen op basis van een gebeurtenis of een vooraf gedefinieerd tijdsinterval. Standaard wordt de inhoud van een adaptief formulier opgeslagen op een handeling van de gebruiker, bijvoorbeeld wanneer u op de knop Opslaan drukt. De optie Automatisch opslaan is handig in:

* De inhoud automatisch opslaan voor anonieme en aangemelde gebruikers
* De inhoud van een formulier opslaan zonder minimale tussenkomst van de gebruiker
* Inhoud van een formulier opslaan op basis van een gebruikersgebeurtenis
* De inhoud van een formulier herhaaldelijk opslaan na een opgegeven tijdsinterval

## Automatisch opslaan inschakelen voor een adaptief formulier {#enable-autosave-for-an-adaptive-form}

Voor een adaptief formulier is de optie voor automatisch opslaan niet uit het vak ingeschakeld. U kunt de auto sparen optie van **Auto toelaten sparen** sectie in de eigenschappen van een adaptieve vorm. De **Auto sparen** sectie verstrekt ook verscheidene andere configuratieopties. Voer de volgende stappen uit om de optie Automatisch opslaan in te schakelen en te configureren voor een adaptief formulier:

1. Om tot de auto-sparen sectie in de eigenschappen toegang te hebben, selecteer een component, dan ![ gebied-niveau ](assets/field-level.png) > **[!UICONTROL Adaptive Form Container]**, en selecteer dan ![ cmp ](assets/cmppr.png).
1. In de **[!UICONTROL Auto Save]** sectie, **[!UICONTROL Enable]** de auto-sparen optie.
1. Geef in het vak **[!UICONTROL Adaptive Form Event]** 1 of TRUE op om het formulier automatisch op te slaan wanneer het formulier in de browser wordt geladen. U kunt ook een voorwaardelijke expressie opgeven voor een gebeurtenis die, wanneer deze wordt geactiveerd en waar wordt geretourneerd, de inhoud van het formulier opslaat.
1. Geef de trigger op. Automatisch opslaan wordt geactiveerd op basis van uw configuratie. U kunt kiezen uit de volgende opties:

   * **[!UICONTROL Time based:]** Selecteer de optie om de inhoud op te slaan op basis van een specifiek tijdsinterval.
   * **[!UICONTROL Event based:]** Selecteer de optie om de inhoud op te slaan op basis van de gebeurtenis die wordt gestart.

   Wanneer u een trigger selecteert, wordt het vak Strategieconfiguratie ingeschakeld. Met het vak Strategieconfiguratie kunt u:

   * Geef een tijdsinterval op als u **[!UICONTROL Time based]** trigger selecteert.
   * Geef een gebeurtenisnaam op als u **[!UICONTROL Event based]** trigger selecteert.

   U kunt ook uw eigen aangepaste strategie aan de lijst toevoegen. Voor details, zie [ een douanestrategie uitvoeren om de vormen ](/help/forms/using/auto-save-an-adaptive-form.md#p-implement-a-custom-strategy-to-enable-autosave-for-adaptive-forms-p) automatisch te bewaren.

1. (Alleen op tijd gebaseerde automatische opslag) Voer de volgende stappen uit om opties voor op tijd gebaseerde automatische opslag te configureren.

   1. Geef in het vak **[!UICONTROL Auto save on this interval]** het tijdsinterval in seconden op. Het formulier wordt herhaaldelijk opgeslagen nadat het aantal seconden is verstreken dat in het intervalvak is opgegeven.

1. (Alleen op gebeurtenissen gebaseerde automatische opslag) Voer de volgende stappen uit om opties voor automatisch opslaan op basis van gebeurtenissen te configureren.

   1. In de **Auto sparen na deze gebeurtenis** doos, specificeer a [ GuideBridge ](https://helpx.adobe.com/aem-forms/6/javascript-api/GuideBridge.html) gebeurtenis. Het formulier wordt opgeslagen telkens wanneer de expressie de waarde TRUE oplevert.

1. (Facultatief) om de inhoud voor anonieme gebruikers automatisch te bewaren, **laat Autosave voor anonieme gebruikers** optie toe, en klik **[!UICONTROL OK]**.

   >[!NOTE]
   >
   >Als u de optie Automatisch opslaan wilt gebruiken voor anonieme gebruikers, moet u de Forms Common Configuration Service zodanig configureren dat alle gebruikers formulieren kunnen bekijken, verifiëren en ondertekenen.
   >
   >Als u de service wilt configureren, gaat u naar AEM webconsoleconfiguratie op `https://server:port/system/console/configMgr` en bewerkt u **[!UICONTROL Forms Common Configuration Service]** om de optie **[!UICONTROL All Users]** in het veld **[!UICONTROL Allow]** te kiezen en slaat u de configuratie op.

## Een aangepaste strategie implementeren om automatisch opslaan van aangepaste formulieren in te schakelen {#implement-a-custom-strategy-to-enable-autosave-for-adaptive-forms}

U kunt een aangepaste gebeurtenis implementeren om de functie voor automatisch opslaan te activeren. Voer de volgende stappen uit om de aangepaste gebeurtenis te maken en te implementeren:

1. Maak clientbibliotheek en clientbibliotheekmappen. Voor gedetailleerde stappen, zie [ Gebruikend Cliënt-Kant het document van Bibliotheken ](/help/sites-developing/clientlibs.md).

   Bijvoorbeeld, gebruikt het volgende manuscript de douane `emailFocusChange` gebeurtenis om de autosave functionaliteit teweeg te brengen:

   ```javascript
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

1. Op geef wijze uit, selecteer een component, dan uitgezocht ![ gebied-niveau ](assets/field-level.png) > **[!UICONTROL Adaptive Form Container]**, en selecteer dan ![ cmp ](assets/cmppr.png).
1. Open de sectie **[!UICONTROL Basic]** in de eigenschappen. Voer in het vak **[!UICONTROL Client Library Category]** de waarde in van de categorie-eigenschap die is gedefinieerd tijdens het maken van de clientbibliotheekmappen.
1. Open de sectie Automatisch opslaan. Geef in het vak **[!UICONTROL Auto save after this event]** een aangepaste gebeurtenis op die al in de clientbibliotheek is gedefinieerd. Klik op **[!UICONTROL OK]**.
