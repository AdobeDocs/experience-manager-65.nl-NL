---
title: Een adaptief formulier maken
seo-title: Een adaptief formulier maken
description: Een adaptief formulier maken met AEM Forms. Adaptieve formulieren zijn responsieve HTML5-formulieren die het verzamelen en verwerken van informatie stroomlijnen.
seo-description: Een adaptief formulier maken met AEM Forms. Adaptieve formulieren zijn responsieve HTML5-formulieren die het verzamelen en verwerken van informatie stroomlijnen.
uuid: 444f461a-9e88-4385-b5ee-e985067ab7bc
content-type: reference
topic-tags: author
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: f06b8cb2-6f98-465f-beec-1e91e3f45707
translation-type: tm+mt
source-git-commit: 3cbcd23254e16231a199276aa2f9e70d6ff39b34
workflow-type: tm+mt
source-wordcount: '1953'
ht-degree: 0%

---


# Een adaptief formulier maken {#creating-an-adaptive-form}

## <strong>Een adaptief formulier maken</strong> {#strong-create-an-adaptive-form-strong}

Ga als volgt te werk om een adaptief formulier te maken.

1. AEM Forms-auteur openen op `https://'[server]:[port]'/<custom-context-if-any>.`

1. Voer uw referenties in op de aanmeldingspagina van de AEM.

   Tik in de linkerbovenhoek op **[!UICONTROL Adobe Experience Manager]** > **[!UICONTROL Forms]** > **[!UICONTROL Forms & Documents]**.

   >[!NOTE]
   >
   >Voor een standaardinstallatie, login is `admin` en het wachtwoord is `admin`.

1. Tik **[!UICONTROL Create]** en selecteer **[!UICONTROL Adaptive Form]**.
1. Er verschijnt een optie voor het selecteren van een sjabloon. Zie [Aangepaste formuliersjablonen](/help/forms/using/creating-adaptive-form.md#p-adaptive-form-templates-p)voor meer informatie over sjablonen. Tik op een sjabloon om deze te selecteren en tik op Volgende.
1. Er wordt een optie voor &#39;Eigenschappen toevoegen&#39; weergegeven. Geef de waarden op voor de volgende eigenschapvelden. De velden Titel en Naam zijn verplicht:

   * **[!UICONTROL Title:]** Hier geeft u de weergavenaam van het formulier op. Met de titel kunt u het formulier identificeren in de gebruikersinterface van AEM Forms.
   * **[!UICONTROL Name:]** Hier geeft u de naam van het formulier op. Er wordt een knooppunt met de opgegeven naam gemaakt in de repository. Wanneer u een titel begint te typen, wordt automatisch een waarde voor het naamveld gegenereerd. U kunt de voorgestelde waarde wijzigen. Het naamveld mag alleen alfanumerieke tekens, afbreekstreepjes en onderstrepingstekens bevatten. Alle ongeldige invoer wordt vervangen door een afbreekstreepje.
   * **[!UICONTROL Description:]** Hier geeft u gedetailleerde informatie over het formulier op.
   * **[!UICONTROL Tags:]** Hiermee geeft u codes op om het adaptieve formulier op unieke wijze te identificeren. Tags helpen u bij het zoeken naar het formulier. Als u tags wilt maken, typt u nieuwe tagnamen in het vak **Codes** .

1. U kunt een adaptief formulier maken op basis van een van de volgende formuliermodellen:

   * [Formuliergegevensmodel](#fdm)
   * [XFA-formuliersjabloon](/help/forms/using/creating-adaptive-form.md#p-create-an-adaptive-form-based-on-an-xfa-form-template-p)
   * [XML- of JSON-schema](/help/forms/using/creating-adaptive-form.md#p-create-an-adaptive-form-based-on-xml-or-json-schema-p)
   * Geen of geen formuliermodel

   U kunt deze configureren via het **[!UICONTROL Form Model]** tabblad op de **[!UICONTROL Add Properties]** pagina. Standaard is het geselecteerde formuliermodel **[!UICONTROL None]**.

1. Tik op **Maken**. Er wordt een adaptief formulier gemaakt en er wordt een dialoogvenster weergegeven om het formulier te openen voor bewerking.

   Als u alle eigenschappen hebt opgegeven, klikt u op **[!UICONTROL Create]**. Er wordt een adaptief formulier gemaakt en er wordt een dialoogvenster weergegeven om het formulier te openen voor bewerking.

   Als u alle eigenschappen hebt opgegeven, klikt u op **[!UICONTROL Create]**. Er wordt een adaptief formulier gemaakt en er wordt een dialoogvenster weergegeven om het formulier te openen voor bewerking.

1. Tik **[!UICONTROL Open]** om het nieuwe formulier te openen op een nieuw tabblad. Het formulier wordt geopend voor bewerking en geeft de inhoud weer die beschikbaar is in de sjabloon. De zijbalk wordt ook weergegeven om het nieuwe formulier aan te passen aan de behoeften.

   Op basis van het type adaptief formulier worden de formulierelementen in de bijbehorende XFA-formuliersjabloon, het XML-schema of het JSON-schema weergegeven op het **[!UICONTROL Data Model Objects]** tabblad van de **[!UICONTROL Content Browser]** zijbalk. U kunt deze elementen ook slepen en neerzetten om het aangepaste formulier samen te stellen.

   Zie [Inleiding tot het ontwerpen van adaptieve formulieren](/help/forms/using/introduction-forms-authoring.md)voor informatie over de adaptieve ontwerpinterface en de beschikbare componenten.

   >[!NOTE]
   >
   >Laat pop-upvensters in uw browser het nieuwe formulier openen op een nieuw tabblad.

## Een adaptief formulier maken op basis van een formuliergegevensmodel {#fdm}

[Met AEM Forms-gegevensintegratie](/help/forms/using/data-integration.md) kunt u meerdere gegevensbronnen integreren en hun entiteiten en services samenbrengen om een formuliergegevensmodel te maken. Het is een uitbreiding van het JSON-schema. U kunt een formuliergegevensmodel gebruiken om een adaptief formulier te maken. De entiteiten of gegevensmodelobjecten die in een formuliergegevensmodel zijn geconfigureerd, zijn beschikbaar als gegevensmodelobjecten voor het ontwerpen van formulieren. Zij zijn gebonden aan de respectieve gegevensbronnen en worden gebruikt om een formulier vooraf in te vullen en ingediende gegevens terug te schrijven naar de respectieve gegevensbronnen. U kunt services die zijn geconfigureerd in een formuliergegevensmodel ook aanroepen met behulp van adaptieve formulierregels.

Een formuliergegevensmodel gebruiken voor het maken van een adaptief formulier:

1. Selecteer op het tabblad Formuliermodel in het scherm Eigenschappen toevoegen **[!UICONTROL Form Data Model]** de optie in de **[!UICONTROL Select From]** vervolgkeuzelijst.

   ![create-af-1-1](assets/create-af-1-1.png)

1. Tik om uit te breiden **[!UICONTROL Select Form Data Model]**. Alle beschikbare formuliergegevensmodellen worden weergegeven.

   Selecteer een gegevensmodel.

   ![create-af-2-1](assets/create-af-2-1.png)

>[!NOTE]
>
>U kunt ook het gegevensmodel van het formulier wijzigen voor een adaptief formulier. Zie Formuliermodeleigenschappen van een adaptief formulier [bewerken voor gedetailleerde stappen](#edit-form-model).

## Een adaptief formulier maken op basis van een XFA-formuliersjabloon {#create-an-adaptive-form-based-on-an-xfa-form-template}

U kunt uw XFA-formuliersjablonen opnieuw gebruiken om adaptieve formulieren te maken. Als u een XFA-formuliersjabloon opnieuw wilt gebruiken, uploadt en koppelt u dit aan een adaptief formulier. De elementen van het formuliersjabloon (XFA-formulier) worden beschikbaar gesteld voor gebruik in de zoekfunctie voor inhoud op het moment dat het formulier wordt aangepast. Vanuit de Inhoudszoeker kunt u de formuliersjabloonelementen naar het formulier slepen en neerzetten.

>[!NOTE]
>
>[Upload de XFA-formuliersjabloon](/help/forms/using/get-xdp-pdf-documents-aem.md) naar AEM Forms voordat u een adaptief formulier maakt op basis van de formuliersjabloon.

Ga als volgt te werk om een XFA-formuliersjabloon te gebruiken als formuliermodel voor uw adaptieve formulier:

1. Open het **[!UICONTROL Add Properties]** tabblad op de **[!UICONTROL Form Model]** pagina.
1. Selecteer op het tabblad Formuliermodel in de vervolgkeuzelijst de optie **[!UICONTROL Form Templates]**. Alle formuliersjablonen die via de gebruikersinterface van AEM Forms naar de gegevensopslagruimte worden geüpload, worden weergegeven voor selectie. Selecteer een sjabloon in de lijst.

   ![XFA-formuliersjabloon koppelen aan een adaptief formulier](assets/form_model_xfa_associate.png)
   **Afbeelding:** *Een formuliersjabloon selecteren*

   >[!NOTE]
   >
   >U kunt ook de formuliersjabloon wijzigen voor een adaptief formulier. Zie Formuliermodeleigenschappen van een adaptief formulier [bewerken voor gedetailleerde stappen](#edit-form-model).

## Een adaptief formulier maken op basis van het XML- of JSON-schema {#create-an-adaptive-form-based-on-xml-or-json-schema}

De schema&#39;s van XML en JSON vertegenwoordigen de structuur waarin de gegevens door het achterste deelsysteem in uw organisatie worden geproduceerd of worden verbruikt. U kunt een schema aan een adaptief formulier koppelen en de elementen ervan gebruiken om dynamische inhoud aan het aangepaste formulier toe te voegen. De elementen van het schema zijn beschikbaar op het tabblad Gegevensmodel van de inhoudbrowser voor het ontwerpen van adaptieve formulieren. U kunt de schema-elementen slepen en neerzetten om het formulier samen te stellen.

Zie de volgende documenten voor informatie over het ontwerpen van XML- of JSON-schema&#39;s voor het ontwerpen van adaptieve formulieren.

* [Aangepaste formulieren maken met XML-schema](/help/forms/using/adaptive-form-xml-schema-form-model.md)
* [Aangepaste formulieren maken met JSON-schema](/help/forms/using/adaptive-form-json-schema-form-model.md)

Ga als volgt te werk om het XML- of JSON-schema als formuliermodel voor een adaptief formulier te gebruiken:

1. Tik in de **[!UICONTROL Add Properties]** stap voor het maken van het aangepaste formulier op het **[!UICONTROL Form Model]** tabblad.
1. Selecteer op het tabblad Formuliermodel **[!UICONTROL Schema]** in de **[!UICONTROL Select From]** vervolgkeuzelijst de optie.

1. Tik op een van de volgende opties **[!UICONTROL Select Schema]** en voer een van de volgende handelingen uit:

   * **[!UICONTROL Upload from disk]** - Selecteer deze optie en tik op Schemadefinitie uploaden om een XML-schema of JSON-schema te zoeken en te uploaden vanuit uw bestandssysteem. Het geüploade schemabestand bevindt zich bij het formulier en is niet toegankelijk voor andere adaptieve formulieren.
   * **[!UICONTROL Search in repository]** - Selecteer deze optie om een keuze te maken uit de lijst met schemadefinitiebestanden in de gegevensopslagruimte. Selecteer het XML- of JSON-schemabestand als formuliermodel. Het geselecteerde schema wordt via verwijzing aan het formulier gekoppeld en is toegankelijk voor gebruik in andere adaptieve formulieren.

   >[!CAUTION]
   >
   >Zorg ervoor dat de bestandsnaam van het JSON-schema eindigt met **.schema.json**. Bijvoorbeeld: mySchema.schema.json

   ![XML- of JSON-schema selecteren](assets/upload-schema.png)
   **Afbeelding:** *XML- of JSON-schema selecteren*

1. (Alleen voor het XML-schema) Nadat u een XML-schema hebt geselecteerd of geüpload, geeft u een hoofdelement op van het geselecteerde XSD-bestand dat u wilt toewijzen met het aangepaste formulier.

   ![XSD-hoofdelement selecteren](assets/xsd-root-element.png)
   **Afbeelding:** *XSD-hoofdelement selecteren*

>[!NOTE]
>
>U kunt het schema ook wijzigen voor een adaptief formulier. Zie Formuliermodeleigenschappen van een adaptief formulier [bewerken voor gedetailleerde stappen](#edit-form-model).

## Aangepaste formuliersjablonen {#adaptive-form-templates}

Een sjabloon biedt een basisstructuur en definieert de vormgeving (lay-outs en stijlen) van een adaptief formulier. Het heeft vooraf opgemaakte componenten die bepaalde eigenschappen en inhoudsstructuur bevatten. AEM Forms beschikt over enkele aanpasbare formuliersjablonen. Als u het volledige sjabloonpakket inclusief geavanceerde sjablonen wilt ophalen, moet u het invoegpakket voor AEM Forms installeren. Zie Het invoegpakket [voor AEM Forms](/help/forms/using/installing-configuring-aem-forms-osgi.md)installeren voor meer informatie.

Daarnaast kunt u de sjablooneditor gebruiken om uw eigen sjablonen te maken. Zie [Aangepaste formuliersjablonen](/help/forms/using/template-editor.md)voor meer informatie over het werken met sjablonen.

>[!NOTE]
>
>Als u een adaptief formulier opent dat is gemaakt met de geavanceerde sjabloon voor bewerken, wordt een foutbericht weergegeven. De geavanceerde sjabloon heeft een Signature Step-component en Adobe Sign is er standaard voor ingeschakeld. Maak en selecteer een [Adobe Sign-cloudconfiguratie](/help/forms/using/adobe-sign-integration-adaptive-forms.md) en [configureer een ondertekenaar](working-with-adobe-sign.md#addsignerstoanadaptiveform) om de fout op te lossen.

## Eigenschappen van een formuliermodel bewerken in een adaptief formulier {#edit-form-model}

Aangepaste formulieren worden gemaakt zonder formuliermodel (met de optie Geen voor formuliermodel) of met een formuliermodel zoals een formuliersjabloon, XML-schema of JSON-schema of formuliergegevensmodel. U kunt het formuliermodel voor een adaptief formulier wijzigen van Geen in een ander formuliermodel. Voor een adaptief formulier op basis van een formuliermodel kunt u een andere formuliersjabloon, een XML-schema, een JSON-schema of een formuliergegevensmodel kiezen voor hetzelfde formuliermodel. U kunt echter niet van het ene formuliermodel naar het andere gaan.

1. Selecteer het aangepaste formulier en tik op het pictogram **Eigenschappen** .
1. Open het **[!UICONTROL Form Model]** tabblad en voer een van de volgende handelingen uit.

   * Als het adaptieve formulier geen formuliermodel heeft, kunt u een ander formuliermodel kiezen en dienovereenkomstig een formuliersjabloon, XML- of JSON-schema of formuliergegevensmodel selecteren.
   * Als het adaptieve formulier is gebaseerd op een formuliermodel, kunt u een andere formuliersjabloon, een XML- of JSON-schema of een formuliergegevensmodel kiezen voor hetzelfde formuliermodel.

1. Tik **[!UICONTROL Save]** om de eigenschappen op te slaan.

## Een adaptief formulier automatisch opslaan {#auto-save-an-adaptive-form}

Standaard wordt de inhoud van een adaptief formulier opgeslagen op een handeling van de gebruiker, bijvoorbeeld wanneer u op de knop Opslaan drukt. U kunt ook een adaptief formulier configureren, zodat de inhoud automatisch wordt opgeslagen op basis van een gebeurtenis of tijdsinterval. De optie Automatisch opslaan is handig in:

* De inhoud automatisch opslaan voor anonieme en aangemelde gebruikers
* De inhoud van een formulier opslaan zonder minimale tussenkomst van de gebruiker
* Inhoud van een formulier opslaan op basis van een gebruikersgebeurtenis
* De inhoud van een formulier herhaaldelijk opslaan na een opgegeven tijdsinterval

### Automatisch opslaan inschakelen voor een adaptief formulier {#enable-auto-save-for-an-adaptive-form}

De optie Automatisch opslaan is standaard niet ingeschakeld. U kunt de optie Automatisch opslaan inschakelen op het tabblad Automatisch opslaan van een adaptief formulier. Het tabblad Automatisch opslaan bevat ook diverse andere configuratieopties. Voer de volgende stappen uit om de optie Automatisch opslaan in te schakelen en te configureren voor een adaptief formulier:

1. Als u de sectie Automatisch opslaan wilt openen in de eigenschappen, selecteert u een component en tikt u op ![veldniveau](assets/field-level.png) > **[!UICONTROL Adaptive Form Container]** en vervolgens op ![cmp](assets/cmppr.png).
1. In de **[!UICONTROL Auto Save]** sectie kiest u **[!UICONTROL Enable]** de optie Automatisch opslaan.
1. Geef in het **[!UICONTROL Adaptive Form Event]** vak 1 of TRUE op om het formulier automatisch op te slaan wanneer het formulier in de browser wordt geladen. U kunt ook een voorwaardelijke expressie opgeven voor een gebeurtenis die, wanneer deze wordt geactiveerd en waar wordt geretourneerd, de inhoud van het formulier opslaat.
1. Geef de trigger op. Automatisch opslaan wordt geactiveerd op basis van uw configuratie. U kunt kiezen uit de volgende opties:

   * **[!UICONTROL Time based:]** Selecteer de optie om de inhoud op te slaan op basis van een specifiek tijdsinterval.
   * **[!UICONTROL Event based:]** Selecteer de optie om de inhoud op te slaan op basis van een gebeurtenis die wordt gestart.

   Wanneer u een trigger selecteert, wordt het vak Strategieconfiguratie ingeschakeld. Met het vak Strategieconfiguratie kunt u:

   * Geef een tijdsinterval op als u een **[!UICONTROL Time based]** trigger selecteert.
   * Geef een naam op voor de gebeurtenis als u **[!UICONTROL Event based]** trigger selecteert.

   U kunt ook uw eigen aangepaste strategie maken en aan de lijst toevoegen. Zie Een aangepaste strategie [implementeren om de formulieren](/help/forms/using/auto-save-an-adaptive-form.md#p-implement-a-custom-strategy-to-enable-autosave-for-adaptive-forms-p)automatisch op te slaan voor meer informatie.

1. (Alleen op tijd gebaseerde automatische opslag) Voer de volgende stappen uit om opties voor op tijd gebaseerde automatische opslag te configureren.

   1. Geef in het **[!UICONTROL Auto save on this interval]** vak het tijdsinterval in seconden op. Het formulier wordt herhaaldelijk opgeslagen nadat het aantal seconden is verstreken dat in het intervalvak is opgegeven.

1. (Alleen op gebeurtenissen gebaseerde automatische opslag) Voer de volgende stappen uit om opties voor automatisch opslaan op basis van gebeurtenissen te configureren.

   1. Geef in het vak **Automatisch opslaan na deze gebeurtenis** een [GuideBridge](https://helpx.adobe.com/aem-forms/6/javascript-api/GuideBridge.html) -gebeurtenis op. Het formulier wordt opgeslagen telkens wanneer de expressie de waarde TRUE oplevert.

1. (Optioneel) Als u de inhoud automatisch wilt opslaan voor anonieme gebruikers, selecteert u de optie Automatisch opslaan **inschakelen voor anonieme gebruikers** en klikt u op **[!UICONTROL OK]**.

   >[!NOTE]
   >
   >Als u de optie Automatisch opslaan wilt gebruiken voor anonieme gebruikers, moet u de Forms Common Configuration Service zodanig configureren dat alle gebruikers formulieren kunnen bekijken, verifiëren en ondertekenen.
   >
   >Om de dienst te vormen, ga naar AEM configuratie van de Console van het Web bij `https://'[server]:[port]'system/console/configMgr` en geef **[!UICONTROL Forms Common Configuration Service]** uit om de **[!UICONTROL All Users]** optie op het **[!UICONTROL Allow]** gebied te kiezen, en sparen de configuratie.