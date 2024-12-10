---
title: Functie in-/uitschakelen inschakelen om functies voor vroege adoptie en pre-release te integreren
description: Functieschakeloptie is een functionaliteit in AEM waarmee beheerders nieuwe functies kunnen inschakelen in een runtimeomgeving.
feature: Adaptive Forms, Foundation Components
role: User, Developer
hidefromtoc: true
source-git-commit: 794d93d890ba752f9036a85831f7cbc8391fb545
workflow-type: tm+mt
source-wordcount: '289'
ht-degree: 0%

---

# Functie in Adobe Experience Manager (AEM) 6.5{#enable-feature-toggle-aem-forms-65}

Functieschakeloptie is een functionaliteit in AEM waarmee beheerders specifieke functies dynamisch kunnen in- of uitschakelen. Dit vermogen is met name nuttig om **Vroege eigenschappen van de Ontvanger** en **eigenschappen van de pre-uitgave** te beheren zonder belangrijke plaatsingen of veranderingen in codebase te vereisen. Het verzekert flexibiliteit en controle over welke eigenschappen in een AEM milieu toegankelijk zijn.

## Functie in-/uitschakelen {#enable-feature-toggle-65}

De Toggles van de eigenschap voor vroege adopters of nieuwe eigenschappen kunnen door de **AEM Console van het Web** worden gevormd door de hieronder stappen te volgen:

1. Meld u aan bij uw AEM Forms-exemplaar.
2. Navigeer naar `http://<author-instance-url>:portnumber/system/console/configMgr` .
3. Onderzoek naar **de Dynamische Leverancier van de Toggle van de Adobe Granite** in de Manager van de Configuratie.
4. Klik het pictogram ![ potlood-pictogram ](assets/illustratorcc_penciltool_cur_edit_2_17.png).
5. In de [!UICONTROL Enabled Toggles] sectie, klik ![ potlood-pictogram ](assets/aem6forms_add.png).
6. Voeg de functie-schakelings-id toe voor de functie, zoals in de onderstaande afbeelding wordt getoond.
   ![ voeg knevel ](assets/add_toggle_number_forms.png) toe

   >[!NOTE]
   >
   >U kunt de functie-schakelfunctie vinden in de id in het document die specifiek is voor de functie voor vroege adoptie.

7. Klik op Opslaan.

## Functie in-/uitschakelen {#disable-feature-toggle-65}

Voer de onderstaande stappen uit om de functieschakeloptie(s) uit te schakelen voor functies waarvan de schakeloptie(s) is ingeschakeld:

1. Meld u aan bij uw AEM Forms-exemplaar.
2. Navigeer naar `http://<author-instance-url>:portnumber/system/console/configMgr` .
3. Onderzoek naar **de Dynamische Leverancier van de Toggle van de Adobe Granite** in de Manager van de Configuratie.
4. Klik het pictogram ![ potlood-pictogram ](assets/illustratorcc_penciltool_cur_edit_2_17.png).
5. In de [!UICONTROL Disabled Toggles] sectie, klik ![ potlood-pictogram ](assets/aem6forms_add.png).
6. Voeg het wisselnummer toe voor de functie die moet worden uitgeschakeld.
   ![ verwijdert knevel ](assets/remove_toggle_feature_forms.png)
7. Klik op Opslaan.

## Technische overweging

Functietogboeken zijn specifiek voor de omgeving en worden tijdens runtime beheerd. De server hoeft dus niet opnieuw te worden opgestart. Het is echter mogelijk dat voor bepaalde functies de relevante pagina&#39;s moeten worden vernieuwd of dat de cache moet worden gewist om wijzigingen te weerspiegelen.
Via `http://<author-instance-url>:4502/etc.clientlibs/toggles.json` hebt u toegang tot de lijst met functies die zijn ingeschakeld via de functie voor uw omgeving.