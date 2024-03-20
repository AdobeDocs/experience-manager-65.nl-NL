---
title: Een adaptief formulier automatisch opslaan
description: U kunt een adaptief formulier zodanig configureren dat de inhoud automatisch wordt opgeslagen op basis van een gebeurtenis of een vooraf gedefinieerd tijdsinterval
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: author
feature: Adaptive Forms, Foundation Components
exl-id: ff9bf466-228d-40e6-9389-15c1f2ed1d2e
solution: Experience Manager, Experience Manager Forms
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '693'
ht-degree: 0%

---

# Een adaptief formulier automatisch opslaan {#auto-save-an-adaptive-form}

<span class="preview"> Adobe beveelt aan moderne en uitbreidbare gegevensvastlegging te gebruiken [Kernonderdelen](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/introduction.html) for [nieuwe Adaptieve Forms maken](/help/forms/using/create-an-adaptive-form-core-components.md) of [Aangepaste Forms toevoegen aan AEM Sites-pagina&#39;s](/help/forms/using/create-or-add-an-adaptive-form-to-aem-sites-page.md). Deze componenten betekenen een aanzienlijke vooruitgang in de aanmaak van Adaptive Forms en zorgen voor indrukwekkende gebruikerservaring. In dit artikel wordt een oudere aanpak beschreven voor de auteur Adaptive Forms die gebruikmaakt van stichtingscomponenten. </span>

U kunt een adaptief formulier zodanig configureren dat de inhoud automatisch wordt opgeslagen op basis van een gebeurtenis of een vooraf gedefinieerd tijdsinterval. Standaard wordt de inhoud van een adaptief formulier opgeslagen op een handeling van de gebruiker, bijvoorbeeld wanneer u op de knop Opslaan drukt. De optie Automatisch opslaan is handig in:

* De inhoud automatisch opslaan voor anonieme en aangemelde gebruikers
* De inhoud van een formulier opslaan zonder minimale tussenkomst van de gebruiker
* Inhoud van een formulier opslaan op basis van een gebruikersgebeurtenis
* De inhoud van een formulier herhaaldelijk opslaan na een opgegeven tijdsinterval

## Automatisch opslaan inschakelen voor een adaptief formulier {#enable-autosave-for-an-adaptive-form}

Voor een adaptief formulier is de optie voor automatisch opslaan niet uit het vak ingeschakeld. U kunt de optie Automatisch opslaan inschakelen in het dialoogvenster **Automatisch opslaan** in de eigenschappen van een adaptief formulier. De **Automatisch opslaan** biedt ook diverse andere configuratieopties. Voer de volgende stappen uit om de optie Automatisch opslaan in te schakelen en te configureren voor een adaptief formulier:

1. Als u de sectie Automatisch opslaan wilt openen in de eigenschappen, selecteert u een component en selecteert u vervolgens ![op veldniveau](assets/field-level.png) > **[!UICONTROL Adaptive Form Container]** en selecteer vervolgens ![cmppr](assets/cmppr.png).
1. In de **[!UICONTROL Auto Save]** deel **[!UICONTROL Enable]** de optie voor automatisch opslaan.
1. In de **[!UICONTROL Adaptive Form Event]** geeft u 1 of TRUE op om het formulier automatisch op te slaan wanneer het formulier in de browser wordt geladen. U kunt ook een voorwaardelijke expressie opgeven voor een gebeurtenis die, wanneer deze wordt geactiveerd en waar wordt geretourneerd, de inhoud van het formulier opslaat.
1. Geef de trigger op. Automatisch opslaan wordt geactiveerd op basis van uw configuratie. U kunt kiezen uit de volgende opties:

   * **[!UICONTROL Time based:]** Selecteer de optie om de inhoud op te slaan op basis van een specifiek tijdsinterval.
   * **[!UICONTROL Event based:]** Selecteer de optie om de inhoud op te slaan op basis van een gebeurtenis die wordt gestart.

   Wanneer u een trigger selecteert, wordt het vak Strategieconfiguratie ingeschakeld. Met het vak Strategieconfiguratie kunt u:

   * Geef een tijdsinterval op als u **[!UICONTROL Time based]** trigger.
   * Geef een gebeurtenisnaam op als u **[!UICONTROL Event based]** trigger.

   U kunt ook uw eigen aangepaste strategie aan de lijst toevoegen. Zie voor meer informatie [Een aangepaste strategie implementeren om de formulieren automatisch op te slaan](/help/forms/using/auto-save-an-adaptive-form.md#p-implement-a-custom-strategy-to-enable-autosave-for-adaptive-forms-p).

1. (Alleen op tijd gebaseerde automatische opslag) Voer de volgende stappen uit om opties voor op tijd gebaseerde automatische opslag te configureren.

   1. In de **[!UICONTROL Auto save on this interval]** geeft u het tijdsinterval in seconden op. Het formulier wordt herhaaldelijk opgeslagen nadat het aantal seconden is verstreken dat in het intervalvak is opgegeven.

1. (Alleen op gebeurtenissen gebaseerde automatische opslag) Voer de volgende stappen uit om opties voor automatisch opslaan op basis van gebeurtenissen te configureren.

   1. In **Automatisch opslaan na deze gebeurtenis** vak, geef een [GuideBridge](https://helpx.adobe.com/aem-forms/6/javascript-api/GuideBridge.html) gebeurtenis. Het formulier wordt opgeslagen telkens wanneer de expressie de waarde TRUE oplevert.

1. (Optioneel) Als u de inhoud automatisch wilt opslaan voor anonieme gebruikers, selecteert u de optie **Automatisch opslaan inschakelen voor anonieme gebruikers** en klik op **[!UICONTROL OK]**.

   >[!NOTE]
   >
   >Als u de optie Automatisch opslaan wilt gebruiken voor anonieme gebruikers, moet u de Forms Common Configuration Service zodanig configureren dat alle gebruikers formulieren kunnen bekijken, verifiëren en ondertekenen.
   >
   >Om de dienst te vormen, ga naar AEM configuratie van de Console van het Web bij `https://server:port/system/console/configMgr` en bewerkt u de **[!UICONTROL Forms Common Configuration Service]** om de **[!UICONTROL All Users]** in de **[!UICONTROL Allow]** en sla de configuratie op.

## Een aangepaste strategie implementeren om automatisch opslaan van aangepaste formulieren in te schakelen {#implement-a-custom-strategy-to-enable-autosave-for-adaptive-forms}

U kunt een aangepaste gebeurtenis implementeren om de functie voor automatisch opslaan te activeren. Voer de volgende stappen uit om de aangepaste gebeurtenis te maken en te implementeren:

1. Maak clientbibliotheek en clientbibliotheekmappen. Voor gedetailleerde stappen raadpleegt u de [Clientzijbibliotheken gebruiken, document](/help/sites-developing/clientlibs.md).

   Het volgende script gebruikt bijvoorbeeld de aangepaste versie `emailFocusChange`gebeurtenis die de functie voor automatisch opslaan activeert:

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

1. Selecteer in de bewerkingsmodus een component en selecteer vervolgens ![op veldniveau](assets/field-level.png) > **[!UICONTROL Adaptive Form Container]** en selecteer vervolgens ![cmppr](assets/cmppr.png).
1. In de eigenschappen opent u de knop **[!UICONTROL Basic]** sectie. In de **[!UICONTROL Client Library Category]** voert u de waarde in van de categorie-eigenschap die is gedefinieerd tijdens het maken van de clientbibliotheekmappen.
1. Open de sectie Automatisch opslaan. In de **[!UICONTROL Auto save after this event]** geeft u een aangepaste gebeurtenis op die al in de clientbibliotheek is gedefinieerd. Klik op **[!UICONTROL OK]**.
