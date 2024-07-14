---
title: Elektronische handtekeningen toepassen op een formulier met scripthandtekeningen
description: Leer hoe u AEM Adaptive Forms ondertekent met de krabbelhandtekening. U kunt de handtekening en de handtekening van het krabbelteken gebruiken om de handtekening op een formulier te tekenen.
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: author
docset: aem65
feature: Adaptive Forms,Foundation Components
exl-id: 096f61b0-59f4-4699-9093-8fb1ed81fded
solution: Experience Manager, Experience Manager Forms
role: User, Developer
source-git-commit: d7b9e947503df58435b3fee85a92d51fae8c1d2d
workflow-type: tm+mt
source-wordcount: '717'
ht-degree: 0%

---

# Elektronische handtekeningen toepassen op een formulier met scripthandtekeningen{#apply-electronic-signatures-to-a-form-using-deprecated-scribble-signatures}

<span class="preview"> de Adobe adviseert gebruikend de moderne en verlengbare gegevens vangen [ Componenten van de Kern ](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/introduction.html) voor [ het creëren van nieuwe Aangepaste Forms ](/help/forms/using/create-an-adaptive-form-core-components.md) of [ het toevoegen van Aangepaste Forms aan de pagina&#39;s van AEM Sites ](/help/forms/using/create-or-add-an-adaptive-form-to-aem-sites-page.md). Deze componenten betekenen een aanzienlijke vooruitgang in de aanmaak van Adaptive Forms en zorgen voor indrukwekkende gebruikerservaring. In dit artikel wordt een oudere aanpak beschreven voor de auteur Adaptive Forms die gebruikmaakt van stichtingscomponenten. </span>


| Versie | Artikelkoppeling |
| -------- | ---------------------------- |
| AEM as a Cloud Service | [ klik hier ](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/adaptive-forms-authoring/authoring-adaptive-forms-foundation-components/add-components-to-an-adaptive-form/signing-forms-using-scribble.html) |
| AEM 6,5 | Dit artikel |


U kunt de **component van de Handtekening van 0} Krabbelen en** component van de Stap van de Handtekening **gebruiken om (Krabbelen) handtekening op een adaptieve vorm te trekken.** De component Handtekeningstap geeft een PDF-versie van het adaptieve formulier weer. U hebt een optie Document of Record ingeschakeld of op een formuliersjabloon gebaseerde adaptieve formulieren nodig om de component Handtekeningstap te kunnen gebruiken.

![ Scripttekendialoog ](/help/forms/using/assets/scribble-signature.png)

## Verschillende opties beschikbaar in het venster Handtekening

* **A:** klik het **pictogram van de Borstel van de Verf** om uw handtekening op canvas te trekken.
* **B:** klik het **Duidelijke** pictogram om de handtekening op canvas te ontruimen.
* **C:** klik het **Geolocation** pictogram om geolocation samen met de handtekening toe te voegen.
* **D:** klik het **pictogram van het Toetsenbord** om uw naam op canvas te typen.

Zodra u het Gedaan ![ a_6_3_forms_save ](assets/aem_6_3_forms_save.png) pictogram in het Krabbelhandtekeningsvenster selecteert, kunt u niet de handtekening uitgeven. Als u de handtekening wilt bewerken, moet u de huidige handtekening negeren en opnieuw ondertekenen met de bovenstaande optie Penseel/toetsenbord.

U kunt **selecteren vormt** ![ ](assets/configure.png) pictogram om de aspectverhouding van het Krabbelcanvas van de Handtekening te plaatsen.
* Als de hoogte-breedteverhouding van het canvas voor Krabbelhandtekeningen kleiner is dan 1, worden de gegevens over de geolocatie toegevoegd onder aan het canvas voor Krabbelhandtekeningen.

* Wanneer de hoogte-breedteverhouding van het canvas voor Krabbelhandtekeningen groter is dan 1, wordt de informatie over de geolocatie toegevoegd aan de rechterkant van het canvas voor Krabbelhandtekeningen.

![ krabbelhandtekening-bodem ](/help/forms/using/assets/scribble-signature-aspectratio.PNG)


>[!NOTE]
>
>Handtekeningen worden altijd opgeslagen in de PNG-indeling.
>

## Een adaptief formulier configureren voor het gebruik van de Krabbelhandtekening {#configure-an-adaptive-form-to-use-scribble-signature}

1. Maak een Document of Record-optie ingeschakeld of een adaptief formulier op basis van een formuliersjabloon. Voor geleidelijke informatie, zie [ Creërend een adaptieve vorm ](../../forms/using/creating-adaptive-form.md).
1. De belemmering-en-daling de **component van de Handtekening van 0} Krabbelen {van componentenbrowser aan de adaptieve vorm.**
1. Selecteer **vormen** ![ ](assets/configure.png) pictogram. De eigenschappenbrowser wordt geopend en de eigenschappen van de component Krabbelen handtekening worden weergegeven. Configureer eigenschappen van de component Krabbelhandtekening.
1. Sleep de component Signature Step van de componentbrowser naar het aangepaste formulier.

   >[!NOTE]
   >
   >De component voor de stap Handtekening gebruikt de volledige breedte die beschikbaar is voor het formulier. Het wordt aanbevolen geen andere component op te nemen in de sectie die de component voor de stap Handtekening bevat.
   >

1. In browser van de Inhoud, de uitgezochte **Container van de Vorm**, en selecteert **** ![ vormt ](/help/forms/using/assets/configure.png) pictogram. De eigenschappenbrowser wordt geopend en de eigenschappen van de container Adaptief formulier worden weergegeven. Navigeer aan **Aangepaste Container van de Vorm** > **Elektronische Ondertekening** en schrap **toelaten Adobe Sign** optie. Selecteer het Gedaan ![ a_6_3_forms_save ](assets/aem_6_3_forms_save.png) pictogram om de veranderingen te bewaren.

   >[!NOTE]
   >
   >Wanneer u een component Handtekeningstap toevoegt aan een adaptief formulier, wordt de optie Adobe Sign inschakelen automatisch geselecteerd.
   >

1. Selecteer **vormen** ![ ](assets/configure.png) pictogram. De eigenschappenbrowser wordt geopend en de eigenschappen voor stap Handtekening worden weergegeven. Configureer de volgende eigenschappen:

   * **Naam van het Element**: specificeer naam van de component.

   * **Titel:** specificeer unieke titel van de component.
   * **bericht van het Malplaatje:** specificeer het bericht dat moet worden getoond terwijl de handtekening PDF wordt geladen. Adobe Sign-services hebben enige tijd nodig om de PDF van de handtekening voor te bereiden en te laden.
   * **Ondertekenende Dienst:** selecteer de **Krabbelen optie van de Ondertekening**.

   * **CSS Klasse**: specificeer CSS klasse van de cliëntbibliotheek, als om het even welk. Gebruik [ thema&#39;s ](../../forms/using/themes.md) en [ in-lijn stijlen ](../../forms/using/inline-style-adaptive-forms.md) in plaats van CSS Klasse.

   Selecteer het Gedaan ![ a_6_3_forms_save ](assets/aem_6_3_forms_save.png) pictogram om de veranderingen te bewaren. De handtekening is geconfigureerd.

   Wanneer u nu een formulier invult, wordt een PDF-versie van het aangepaste formulier weergegeven en worden opties voor de ondertekening van het PDF-document weergegeven. Voor gedetailleerde informatie, zie [ een adaptieve vorm ondertekenen gebruikend de Krabbelhandtekening ](../../forms/using/signing-forms-using-scribble.md#sign-an-adaptive-form-using-scribble-signature).

## Een adaptief formulier ondertekenen met de Krabbelhandtekening {#sign-an-adaptive-form-using-scribble-signature}

1. Nadat u een adaptief formulier hebt ingevuld en de pagina Stap handtekening hebt bereikt, wordt het handtekeningscherm weergegeven.

   ![ Scripttekendialoog ](/help/forms/using/assets/esignscribblesign.jpg)

1. Klik op **[!UICONTROL Sign]**. Het dialoogvenster Scriptteken wordt weergegeven. Onderteken de vorm en klik het Gedaan ![ aem_6_3_forms_save ](assets/aem_6_3_forms_save.png) pictogram om de handtekening te bewaren.

   ![ Scripttekendialoog ](/help/forms/using/assets/scribblewidget.png)

1. Klik op Voltooien om het ondertekeningsproces te voltooien.

   ![ voltooi het het ondertekenen proces ](/help/forms/using/assets/scribblecomplete.jpg)

De handtekeningen worden toegevoegd aan het formulier en het formulierbesturingselement gaat naar het volgende venster.
