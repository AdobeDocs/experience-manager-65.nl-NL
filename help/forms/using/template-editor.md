---
title: Aangepaste formuliersjablonen
seo-title: Adaptive Form Templates
description: Maak adaptieve formuliersjablonen door de basisstructuur en initiële formulierinhoud te definiëren met de Sjablooneditor.
seo-description: Create adaptive form templates by defining the basic structure and initial form content using the Template Editor.
uuid: 317ca3ab-f809-49a7-a063-9d0c17a35fe4
contentOwner: sashanka
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: develop
discoiquuid: b21a48ba-eccd-4bb5-9b92-3039026ddf2a
docset: aem65
feature: Adaptive Forms
exl-id: d7287ee7-fb4e-4d47-b37e-0a9260344070
source-git-commit: 1683338f02d01d5d9843368955fa42f309718f26
workflow-type: tm+mt
source-wordcount: '1987'
ht-degree: 0%

---

# Aangepaste formuliersjablonen{#adaptive-form-templates}

| Versie | Artikelkoppeling |
| -------- | ---------------------------- |
| AEM as a Cloud Service | [Klik hier](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/adaptive-forms-authoring/authoring-adaptive-forms-foundation-components/create-an-adaptive-form-on-forms-cs/template-editor.html) |
| AEM 6,5 | Dit artikel |



Wanneer u een formulier ontwerpt, voegt u velden en componenten toe om de formulierstructuur, inhoud en handelingen in de editor te definiëren. U voegt velden en componenten toe in het dialoogvenster `guideRootPanel` van de formuliercontainer. Met de Sjablooneditor kunt u een sjabloon maken met een basisstructuur en eerste inhoud die auteurs kunnen gebruiken om formulieren te maken.

U wilt bijvoorbeeld dat alle formulierauteurs bepaalde tekstvakken, navigatieknoppen en een verzendknop in een inschrijvingsformulier hebben. U kunt een sjabloon maken met de componenten die auteurs kunnen gebruiken om een formulier te maken dat consistent is met andere inschrijvingsformulieren. Wanneer auteurs de sjabloon gebruiken om een adaptief formulier te maken, neemt het nieuwe formulier de structuur en componenten over die u in de sjabloon hebt opgegeven. Met de Sjablooneditor kunt u:

* Voeg kop- en voettekstcomponenten van een formulier toe aan de structuurlaag.
* Geef de initiële inhoud voor het formulier op.
* Geef een thema op en verzend acties.

## Werken met sjablonen {#working-with-templates}

U kunt tot malplaatjeredacteur van het menu van Hulpmiddelen toegang hebben door aan te navigeren **Adobe Experience Manager > Gereedschappen > Sjablonen**. Hier worden de sjablonen ingedeeld in mappen die zijn ingeschakeld voor bewerkbare sjablonen. AEM biedt een algemene map voor het organiseren van sjablonen. Deze optie is echter niet standaard ingeschakeld. U kunt de beheerder vragen de algemene map in te schakelen of een nieuwe map voor sjablonen te maken. Ga voor meer informatie over het maken van mappen naar [Sjabloonmappen](/help/sites-developing/page-templates-editable.md).

Als u eenmaal hebt getikt om een map te openen, verschijnt er een knop Maken waarmee u een nieuwe sjabloon voor adaptieve formulieren kunt maken.

### Een sjabloon maken {#create-template}

Nadat u een map hebt gemaakt, opent u de map en voert u de volgende stappen uit om een sjabloon te maken:

1. Tik in de Sjabloonconsole op **Maken** in de map die u hebt gemaakt.
1. Selecteer in de sectie Sjabloontype kiezen de optie **Adaptief formuliersjabloon** en tikken **Volgende**.

1. Geef in de sectie Sjabloondetails een sjabloontitel op en tik op **Maken**.
U kunt een beschrijving en miniatuur opgeven die u kunt zien wanneer u de gemaakte sjabloon kunt selecteren tijdens het ontwerpen van het formulier.

1. Tikken **Gereed** om terug te keren naar de console, of tikken **Openen** om de sjabloon in de editor te openen.

### UI voor sjablooneditor {#template-editor-ui}

Wanneer u een sjabloon opent voor bewerking, kunt u de volgende AEM Editor-componenten zien:

* **Pagina, werkbalk**
Bevat de volgende opties:

   * **Zijpaneel in-/uitschakelen**: Hiermee kunt u de zijbalk weergeven of verbergen.
   * **Pagina-informatie**: Hier kunt u informatie opgeven, zoals de publicatie-/publicatietijd, miniaturen, bibliotheken aan de clientzijde, het paginabeleid en de clientbibliotheek van het paginaontwerp.
   * **Emulator**: Hiermee kunt u het uiterlijk van verschillende apparaten simuleren en aanpassen.
   * **Laagkiezer:** Hiermee kunt u de laag wijzigen.
U kunt **Structuur** laag of **Oorspronkelijke inhoud** laag. Met de structuurlaag kunt u de kop- en voettekst toevoegen en aanpassen. Met de eerste laag Inhoud kunt u de formulierinhoud aanpassen.

   * **Voorvertoning:** Hiermee kunt u een voorvertoning weergeven van het uiterlijk van de sjabloon wanneer u de sjabloon publiceert. U kunt Laagkiezer en Voorvertoning gebruiken om de bewerkings- en voorvertoningsmodi in en uit te schakelen.

* **Zijbalk:** Verstrekt de Inhoud, Eigenschappen, Activa, en de browsers van Componenten.
* **Component, werkbalk:** Wanneer u een component selecteert, ziet u een werkbalk waarin u de component kunt aanpassen.
* **Pagina**: Het gebied waar u inhoud toevoegt om de sjabloon te maken.

Zie [Inleiding tot het ontwerpen van adaptieve formulieren](../../forms/using/introduction-forms-authoring.md) voor meer informatie over de Touch UI-editor.

### Een sjabloon bewerken {#editing-a-template}

Er wordt een adaptieve formuliersjabloon gemaakt met behulp van twee lagen:

* Structuur
* Oorspronkelijke inhoud

De laagkiezer is beschikbaar naast de optie Voorvertoning in de rechterbovenhoek van het scherm.

### Structuur {#structure}

Wanneer u de structuurlaag selecteert in de Sjablooneditor, ziet u de lay-outcontainers boven en onder de container voor adaptieve formulieren. Auteurs kunnen deze lay-outcontainers voor kopbal en footer gebruiken. U kunt de kop- en voettekst toevoegen, bewerken of aanpassen. Sleep de component Adaptief koptekst van formulier naar de lay-outcontainer boven de container voor adaptieve formulieren om de sjabloonkoptekst aan te passen. Sleep de component Aangepaste formuliervoettekst naar de lay-outcontainer onder de container voor adaptieve formulieren om de sjabloonvoettekst aan te passen.

![Lay-outcontainer in de structuurlaag](assets/header-layer-selector.png)

Lay-outcontainers in de structuurlaag

**A.** Indelingscontainer voor koptekstcomponent **B.** Lay-outcontainer voor voettekstcomponent

Sleep de component Adaptief koptekst van formulier naar de lay-outcontainer boven de container voor adaptieve formulieren. Nadat u de component hebt toegevoegd, kunt u de eigenschappen ervan opgeven waarmee u een logo kunt toevoegen en de titel kunt opgeven.

Op dezelfde manier kunt u de copyrightinformatie en bedrijfsgegevens opgeven wanneer u de voettekstcomponent in de lay-outcontainer onder de container voor adaptieve formulieren sleept.

![Koptekst en voettekst toegevoegd aan de laag Structuur](assets/header-and-footer.png)

Koptekst en voettekst toegevoegd aan de laag Structuur

#### Componenten in de structuurlaag vergrendelen/ontgrendelen {#locking-unlocking-components-in-the-structure-layer}

Wanneer u de sjabloon bewerkt terwijl de structuurlaag is geselecteerd, kunt u de kop- en voettekst van de sjabloon ontgrendelen. Als een component ontgrendeld is in de sjabloon, kunnen formulierauteurs de component bewerken in het adaptieve formulier dat de sjabloon gebruikt. Door een component te vergrendelen voorkomt u dat auteurs van formulieren deze in het aangepaste formulier kunnen bewerken. De optie Vergrendelen is beschikbaar op de werkbalk van de component.

U voegt bijvoorbeeld de koptekstcomponent in de sjabloon toe. Wanneer u de component selecteert, ziet u een vergrendelingsoptie op de werkbalk van de component. Koptekst bevat doorgaans een bedrijfsnaam en een logo en u wilt niet dat auteurs van formulieren het logo en de koptekst in een sjabloon wijzigen. In een adaptief formulier dat is gemaakt met de sjabloon met de koptekstcomponent vergrendeld, kunnen formulierauteurs het logo en de bedrijfsnaam niet wijzigen.

>[!NOTE]
>
>Het wordt niet aanbevolen de afbeelding of het logo in de koptekstcomponent afzonderlijk te vergrendelen of te ontgrendelen. U kunt de koptekstcomponent ontgrendelen.

### Oorspronkelijke inhoud {#initial-content}

Als de optie Begininhoud is geselecteerd, wordt de container van het adaptieve formulier van de sjabloon geopend als een adaptief formulier voor bewerking. Net als bij het ontwerpen van een adaptief formulier kunt u initiële instellingen opgeven, zoals het selecteren van een thema en het verzenden van handelingen.

Auteurs van formulieren gebruiken het als basis om een formulier te maken. De structuur van de inhoudsstroom wordt opgegeven in de laag Begininhoud van de sjabloon. Als u wilt overschakelen naar het bewerken van de eerste inhoud van de formuliersjabloon, tikt u vóór de voorvertoning op de pagina-werkbalk op ![canvas-drop-down](assets/canvas-drop-down.png) **> Oorspronkelijke inhoud**.
![Oorspronkelijke inhoudslaag in de Sjablooneditor](assets/initial-content-layer.png)

Oorspronkelijke inhoudslaag in de Sjablooneditor met de adaptieve formuliercontainer geselecteerd voor het opgeven van eigenschappen.

![initiële inhoud](assets/initial-content-layer-1.png)

In de laag Begininhoud maakt u de adaptieve formuliersjabloon die uw auteurs als basis gebruiken. Het ontwerpen van een sjabloon lijkt op het ontwerpen van een formulier. U gebruikt de opties in de zijbalk. Sidebar verstrekt inhoud, eigenschappen, activa, en componentenbrowsers.

Zie [Zijbalk](../../forms/using/introduction-forms-authoring.md#sidebar).

>[!NOTE]
>
>Wanneer u Inhoud opslaan of PDF opslaan selecteert als Verzendhandeling, kunt u het opslagpad opgeven. Als u een pad opgeeft in een sjabloon, hebben alle formulieren die ermee worden gemaakt hetzelfde pad. U kunt het juiste opslagpad opgeven of formulierauteurs de opslaglocatie laten bijwerken om te voorkomen dat gegevens in elk formulier op dezelfde locatie worden opgeslagen.

#### Een adaptieve formuliersjabloon maken met tabs en deelvensters  {#creating-an-adaptive-form-template-with-tabs-and-panels-nbsp}

U wilt bijvoorbeeld een sjabloon maken met de volgende tabbladen:

* Algemene informatie
* Professionele informatie

U hebt een logo toegevoegd, een titel opgegeven en een voettekst toegevoegd aan de structuurlaag. Vergrendel de kop- en voettekst om te voorkomen dat auteurs van formulieren deze bewerken wanneer ze de sjabloon gebruiken om formulieren te maken.

Wijzig de laag van Structuur in Begininhoud en voeg inhoud toe aan het formulier. Als u een structuur met tabbladen wilt maken, voegt u een onderliggend deelvenster toe in het guideRootPanel van de container van het adaptieve formulier. Een deelvenster toevoegen:

* U kunt een deelvenster toevoegen door te tikken op de knop **+** wanneer u de optie **Componenten hierheen slepen** optie.

* U kunt de deelvenstercomponent slepen en neerzetten vanuit de deelvensterbrowser in de zijbalk.
* U kunt een onderliggend deelvenster van het dialoogvenster `guideRootPanel` op de werkbalk van de component.

Als u de tabbladen Algemene informatie en Professionele informatie wilt maken, voegt u twee deelvensters toe in het deelvenster met onderliggende items van het dialoogvenster `guideRootPanel`. Selecteer de deelvensters en tik op ![cmppr](assets/cmppr.png) om de eigenschappen in de zijbalk te openen. De elementnamen wijzigen als `general-info` en `professional-info`en titels als algemene informatie en beroepsinformatie. Tik in de zijbalk op inhoud om de inhoudbrowser te openen. Selecteer op het tabblad Formulierobjecten de optie `guideRootPanel`. In de redacteur, wordt guideRootPanel geselecteerd. Tikken ![cmppr](assets/cmppr.png) in de componentwerkbalk om de eigenschappen te openen. Selecteer in het veld Indeling van deelvenster de optie **Tabs boven** en tikken **Gereed**. De sjabloonstructuur met tabs wordt toegepast.

#### Inhoud toevoegen op tabbladen {#adding-content-in-tabs}

![Velden toevoegen aan de aangepaste formuliersjabloon](assets/template-edit-initial-content.png)

Nadat u deelvensters hebt toegevoegd en deze hebt gestructureerd als tabbladen, kunt u velden toevoegen binnen de tabbladen. Wanneer u een tabblad selecteert in de editor, kunt u de opties **Componenten hierheen slepen** optie. U kunt componenten zoals tekstvakken, lijstitems en knoppen slepen en neerzetten. U kunt componenten slepen-dalingscomponenten van componentenbrowser in sidebar.

Elke component bevat eigenschappen die het vastleggen en bewerken van gegevens verbeteren. U kunt bijvoorbeeld de opdracht **Vereist veld** eigenschap van een component. Uw auteurs kunnen een bericht specificeren dat uw klanten zien wanneer zij het vullen van een vereist gebied overslaan. Geef het bericht op in **Bericht vereist veld** eigenschap.

In de voorbeeldsjabloon worden de velden Naam, Telefoonnummer en Geboortedatum toegevoegd op het tabblad Algemene informatie. Op het tabblad Professionele informatie, momenteel gebruikt, worden het werkgelegenheidstype en de kwalificatievelden voor het onderwijs toegevoegd.

Nadat u velden hebt toegevoegd, kunt u knoppen toevoegen zoals Verzenden en Herstellen.

### De sjabloon inschakelen {#enabling-the-template}

Wanneer u een sjabloon maakt, wordt deze toegevoegd als concept. Schakel de sjabloon in om deze te gebruiken voor het maken van adaptieve formulieren. Een sjabloon inschakelen:

1. Navigeren naar **Adobe Experience Manager > Gereedschappen > Sjablonen** en opent u de map waarin u de sjabloon hebt gemaakt.

1. De sjabloon die u hebt gemaakt, is gemarkeerd als Concept.
1. Selecteer de sjabloon en tik op **Inschakelen** in de werkbalk.
Wanneer u een adaptief formulier maakt, wordt de sjabloon weergegeven wanneer u wordt gevraagd een sjabloon te kiezen.

## Een sjabloon importeren of exporteren {#importing-or-exporting-a-template}

Een formulier werkt met de sjabloon. Wanneer u een adaptief formulier downloadt dat is gemaakt met een aangepaste sjabloon, wordt de sjabloon niet gedownload. Wanneer u het formulier in een ander AEM Forms-exemplaar importeert, wordt het zonder de sjabloon geïmporteerd. Als een formulier wordt geïmporteerd maar de sjabloon ervan niet beschikbaar is, wordt het formulier niet gegenereerd. U kunt de aangepaste sjabloon verpakken vanuit `/conf` node in `https://<server>:<port>/crx/packmgr`en poort het formulier in het AEM Forms-exemplaar waar u het formulier wilt uploaden.

## Een adaptief formulier maken met behulp van de sjabloon {#creating-an-adaptive-form-using-the-template}

Nadat u een sjabloon hebt gemaakt en ingeschakeld, is deze beschikbaar in formulierbeheer wanneer u een adaptief formulier maakt. Als u een sjabloon wilt gebruiken en een adaptief formulier wilt maken, raadpleegt u [Een adaptief formulier maken](../../forms/using/creating-adaptive-form.md).

## Weergaveoptie wijzigen van uit de vaksjablonen  {#change-display-option-of-out-of-the-box-templates}

U kunt aangepaste sjablonen maken voor aangepaste formulieren om de basisstructuur en de eerste inhoud te definiëren. AEM Forms biedt ook een set van in de kadersjabloon geplaatste formulieren voor adaptieve formulieren. U kunt de sjablonen weergeven of verbergen.

Voer de volgende stappen uit om sjablonen weer te geven en te verbergen:

1. Meld u aan bij de AEM Forms-auteur en navigeer naar **Gereedschappen** > **Bewerkingen** > **Webconsole**.

   >[!NOTE]
   >
   >De URL van AEM webconsole is https://&#39;[server]:[poort]&#39;/system/console/configMgr

1. Zoek en open de **FormsManager-configuratie** instellingen:

   * Als u de aangepaste formuliersjabloon voor het vak wilt weergeven of verbergen, schakelt u het selectievakje **Sjablonen opnemen uit het vak AF en AD** optie.
   * Als u adaptieve formuliersjablonen wilt weergeven of verbergen die zijn toegevoegd in AEM 6.0 Forms of AEM 6.1 Forms-versies maar die nu zijn vervangen, schakelt u de optie **Inclusief AEM 6.0 AF-sjablonen** optie. Als deze optie is ingeschakeld, moet de optie **Sjablonen opnemen uit het vak AF en AD** configuratie die moet worden ingeschakeld.

1. Klikken **Opslaan**. De weergaveopties voor de out van de vaksjablonen worden gewijzigd.

## Recommendations {#recommendations}

* Wanneer u eigenschappen van het formulier in de sjablooneditor wijzigt, gebruikt u de eigenschap BindReference niet.
* Als u een onderbrekingspunt wilt toevoegen, creeer het wanneer u een adaptieve vormmalplaatje ontwerpt.
Voor meer informatie over breekpunten raadpleegt u [Responsieve lay-out](/help/sites-authoring/responsive-layout.md).
