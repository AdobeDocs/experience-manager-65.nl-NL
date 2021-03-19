---
title: Aangepaste formuliersjablonen
seo-title: Aangepaste formuliersjablonen
description: Maak adaptieve formuliersjablonen door de basisstructuur en initiële formulierinhoud te definiëren met de Sjablooneditor.
seo-description: Maak adaptieve formuliersjablonen door de basisstructuur en initiële formulierinhoud te definiëren met de Sjablooneditor.
uuid: 317ca3ab-f809-49a7-a063-9d0c17a35fe4
contentOwner: sashanka
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: develop
discoiquuid: b21a48ba-eccd-4bb5-9b92-3039026ddf2a
docset: aem65
feature: Adaptieve Forms
translation-type: tm+mt
source-git-commit: 48726639e93696f32fa368fad2630e6fca50640e
workflow-type: tm+mt
source-wordcount: '1986'
ht-degree: 0%

---


# Aangepaste formuliersjablonen{#adaptive-form-templates}

Wanneer u een formulier ontwerpt, voegt u velden en componenten toe om de formulierstructuur, inhoud en handelingen in de editor te definiëren. U voegt velden en componenten toe in de `guideRootPanel` van de formuliercontainer. Met de Sjablooneditor kunt u een sjabloon maken met een basisstructuur en eerste inhoud die auteurs kunnen gebruiken om formulieren te maken.

U wilt bijvoorbeeld dat alle formulierauteurs bepaalde tekstvakken, navigatieknoppen en een verzendknop in een inschrijvingsformulier hebben. U kunt een sjabloon maken met de componenten die auteurs kunnen gebruiken om een formulier te maken dat consistent is met andere inschrijvingsformulieren. Wanneer auteurs de sjabloon gebruiken om een adaptief formulier te maken, neemt het nieuwe formulier de structuur en componenten over die u in de sjabloon hebt opgegeven. Met de Sjablooneditor kunt u:

* Voeg kop- en voettekstcomponenten van een formulier toe aan de structuurlaag.
* Geef de initiële inhoud voor het formulier op.
* Geef een thema op en verzend acties.

## Werken met sjablonen {#working-with-templates}

U hebt toegang tot de sjablooneditor via het menu Gereedschappen door te navigeren naar **Adobe Experience Manager > Gereedschappen > Sjablonen**. Hier worden de sjablonen ingedeeld in mappen die zijn ingeschakeld voor bewerkbare sjablonen. AEM biedt een algemene map voor het organiseren van sjablonen. Deze optie is echter niet standaard ingeschakeld. U kunt de beheerder vragen de algemene map in te schakelen of een nieuwe map voor sjablonen te maken. Zie [Sjabloonmappen](/help/sites-developing/page-templates-editable.md) voor meer informatie over het maken van mappen.

Als u eenmaal hebt getikt om een map te openen, verschijnt er een knop Maken waarmee u een nieuwe sjabloon voor adaptieve formulieren kunt maken.

### Een sjabloon maken {#create-template}

Nadat u een map hebt gemaakt, opent u de map en voert u de volgende stappen uit om een sjabloon te maken:

1. Tik in de Sjabloonconsole op **Maken** in de map die u hebt gemaakt.
1. Selecteer **Adaptief formuliersjabloon** in de sectie Sjabloontype kiezen en tik **Volgende**.

1. Geef in de sectie Sjabloondetails een sjabloontitel op en tik **Maken**.
U kunt een beschrijving en miniatuur opgeven die u kunt zien wanneer u de gemaakte sjabloon kunt selecteren tijdens het ontwerpen van het formulier.

1. Tik **Done** om terug te keren naar de console of tik **Open** om de sjabloon te openen in de editor.

### UI voor sjablooneditor {#template-editor-ui}

Wanneer u een sjabloon opent voor bewerking, kunt u de volgende AEM Editor-componenten zien:

* **Pagina-**
werkbalkBevat de volgende opties:

   * **Zijpaneel** in-/uitschakelen: Hiermee kunt u de zijbalk weergeven of verbergen.
   * **Pagina-informatie**: Hier kunt u informatie opgeven, zoals de publicatie-/publicatietijd, miniaturen, bibliotheken aan de clientzijde, het paginabeleid en de clientbibliotheek van het paginaontwerp.
   * **Emulator**: Hiermee kunt u het uiterlijk van verschillende apparaten simuleren en aanpassen.
   * **Laagkiezer:** Hiermee kunt u de laag wijzigen.
U kunt **Structuur** laag of **Eerste inhoud** laag kiezen. Met de structuurlaag kunt u de kop- en voettekst toevoegen en aanpassen. Met de eerste laag Inhoud kunt u de formulierinhoud aanpassen.

   * **Voorvertoning:** Hiermee kunt u een voorvertoning weergeven van de sjabloon wanneer u deze publiceert. U kunt Laagkiezer en Voorvertoning gebruiken om de bewerkings- en voorvertoningsmodi in en uit te schakelen.

* **Sidebar:** verschaft de browsers Inhoud, Eigenschappen, Middelen en Componenten.
* **Component, werkbalk:** wanneer u een component selecteert, ziet u een werkbalk waarmee u de component kunt aanpassen.
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

**A.** Layout-container voor koptekstcomponent  **B.** Layout-container voor voettekstcomponent

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

### Eerste inhoud {#initial-content}

Als de optie Begininhoud is geselecteerd, wordt de container van het adaptieve formulier van de sjabloon geopend als een adaptief formulier voor bewerking. Net als bij het ontwerpen van een adaptief formulier kunt u initiële instellingen opgeven, zoals het selecteren van een thema en het verzenden van handelingen.

Auteurs van formulieren gebruiken het als basis om een formulier te maken. De structuur van de inhoudsstroom wordt opgegeven in de laag Begininhoud van de sjabloon. Als u wilt overschakelen naar het bewerken van de eerste inhoud van de formuliersjabloon, tikt u voor Voorvertoning op de paginaboolbalk op ![canvas-drop-down](assets/canvas-drop-down.png) **> Eerste inhoud**.
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

* U kunt een deelvenster toevoegen door op de knop **+** te tikken wanneer u de optie **Componenten hier slepen** selecteert.

* U kunt de deelvenstercomponent slepen en neerzetten vanuit de deelvensterbrowser in de zijbalk.
* U kunt het kindpaneel van `guideRootPanel` van de componententoolbar toevoegen.

Als u de tabbladen Algemene informatie en Professionele informatie wilt maken, voegt u twee deelvensters toe in het deelvenster Onderliggend item van de `guideRootPanel`. Selecteer de deelvensters en tik ![cmppr](assets/cmppr.png) om de eigenschappen in de zijbalk te openen. Wijzig de elementnamen als `general-info` en `professional-info`, en de titels als respectievelijk Algemene informatie en Professionele informatie. Tik in de zijbalk op inhoud om de inhoudbrowser te openen. Selecteer `guideRootPanel` op het tabblad Formulierobjecten. In de redacteur, wordt guideRootPanel geselecteerd. Tik ![cmp](assets/cmppr.png) in de componentwerkbalk om de eigenschappen ervan te openen. Selecteer **Tabs boven** in het veld Deelvensterlayout en tik **Done**. De sjabloonstructuur met tabs wordt toegepast.

#### Inhoud toevoegen op tabbladen {#adding-content-in-tabs}

![Velden toevoegen aan de aangepaste formuliersjabloon](assets/template-edit-initial-content.png)

Nadat u deelvensters hebt toegevoegd en deze hebt gestructureerd als tabbladen, kunt u velden toevoegen binnen de tabbladen. Wanneer u een lusje in de redacteur selecteert, kunt u **de componenten van de belemmering hier** optie zien. U kunt componenten zoals tekstvakken, lijstitems en knoppen slepen en neerzetten. U kunt componenten slepen-dalingscomponenten van componentenbrowser in sidebar.

Elke component bevat eigenschappen die het vastleggen en bewerken van gegevens verbeteren. U kunt bijvoorbeeld de eigenschap **Required field** van een component inschakelen. Uw auteurs kunnen een bericht specificeren dat uw klanten zien wanneer zij het vullen van een vereist gebied overslaan. Geef het bericht op in **Required Field Message** property.

In de voorbeeldsjabloon worden de velden Naam, Telefoonnummer en Geboortedatum toegevoegd op het tabblad Algemene informatie. Op het tabblad Professionele informatie, momenteel gebruikt, worden het werkgelegenheidstype en de kwalificatievelden voor het onderwijs toegevoegd.

Nadat u velden hebt toegevoegd, kunt u knoppen toevoegen zoals Verzenden en Herstellen.

### Sjabloon {#enabling-the-template} inschakelen

Wanneer u een sjabloon maakt, wordt deze toegevoegd als concept. Schakel de sjabloon in om deze te gebruiken voor het maken van adaptieve formulieren. Een sjabloon inschakelen:

1. Navigeer naar **Adobe Experience Manager > Gereedschappen > Sjablonen** en open de map waarin u de sjabloon hebt gemaakt.

1. De sjabloon die u hebt gemaakt, is gemarkeerd als Concept.
1. Selecteer de sjabloon en tik **Inschakelen** in de werkbalk.
Wanneer u een adaptief formulier maakt, wordt de sjabloon weergegeven wanneer u wordt gevraagd een sjabloon te kiezen.

## Een sjabloon {#importing-or-exporting-a-template} importeren of exporteren

Een formulier werkt met de sjabloon. Wanneer u een adaptief formulier downloadt dat is gemaakt met een aangepaste sjabloon, wordt de sjabloon niet gedownload. Wanneer u het formulier in een ander AEM Forms-exemplaar importeert, wordt het zonder de sjabloon geïmporteerd. Als een formulier wordt geïmporteerd maar de sjabloon ervan niet beschikbaar is, wordt het formulier niet gegenereerd. U kunt de aangepaste sjabloon verpakken vanuit het knooppunt `/conf` in `https://<server>:<port>/crx/packmgr` en het vervolgens porteren in het AEM Forms-exemplaar waar u het formulier wilt uploaden.

## Een adaptief formulier maken met de sjabloon {#creating-an-adaptive-form-using-the-template}

Nadat u een sjabloon hebt gemaakt en ingeschakeld, is deze beschikbaar in formulierbeheer wanneer u een adaptief formulier maakt. Zie [Een adaptief formulier maken](../../forms/using/creating-adaptive-form.md) om een sjabloon te gebruiken en een adaptief formulier te maken.

## Weergaveoptie wijzigen van uit de vaksjablonen {#change-display-option-of-out-of-the-box-templates}

U kunt aangepaste sjablonen maken voor aangepaste formulieren om de basisstructuur en de eerste inhoud te definiëren. AEM Forms biedt ook een set van in de kadersjabloon geplaatste formulieren voor adaptieve formulieren. U kunt de sjablonen weergeven of verbergen.

Voer de volgende stappen uit om sjablonen weer te geven en te verbergen:

1. Meld u aan bij de auteur van AEM Forms en navigeer naar **Tools** > **Operations** > **Webconsole**.

   >[!NOTE]
   >
   >De URL van AEM webconsole is https://&#39;[server]:[poort]&#39;/system/console/configMgr

1. Zoek en open de **FormsManager Configuration**-instellingen:

   * Als u de aangepaste formuliersjabloon voor het vak wilt weergeven of verbergen, schakelt u de optie **Inclusief sjablonen uit het vak AF en AD Templates** in of uit.
   * Als u adaptieve formuliersjablonen uit het vak wilt weergeven of verbergen die zijn toegevoegd in AEM 6.0 Forms- of AEM 6.1 Forms-versies maar die nu zijn vervangen, schakelt u de optie **Inclusief AEM 6.0 AF-sjablonen** in of uit. Als deze optie wordt gecontroleerd, om van kracht te worden, vereist het **omvat uit de doosAF en de configuratie van de Malplaatjes van de ADVERTENTIE** worden toegelaten.

1. Klik **Opslaan**. De weergaveopties voor de out van de vaksjablonen worden gewijzigd.

## Recommendations {#recommendations}

* Wanneer u eigenschappen van het formulier in de sjablooneditor wijzigt, gebruikt u de eigenschap BindReference niet.
* Als u een onderbrekingspunt wilt toevoegen, creeer het wanneer u een adaptieve vormmalplaatje ontwerpt.
Voor meer informatie over breekpunten, zie [Responsieve Lay-out](/help/sites-authoring/responsive-layout.md).

