---
title: Pagina-inhoud bewerken
description: Inhoud wordt toegevoegd met componenten die naar de pagina kunnen worden gesleept. Deze kunnen vervolgens worden bewerkt, verplaatst of verwijderd.
contentOwner: Chris Bohnert
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: page-authoring
content-type: reference
docset: aem65
exl-id: e1b5aea0-983c-4e7b-9d35-d7beeee45dc7
solution: Experience Manager, Experience Manager Sites
feature: Authoring
role: User
source-git-commit: 66db4b0b5106617c534b6e1bf428a3057f2c2708
workflow-type: tm+mt
source-wordcount: '1829'
ht-degree: 0%

---

# Pagina-inhoud bewerken{#editing-page-content}

Nadat u de pagina hebt gemaakt (nieuw of als onderdeel van een opstart of live kopie), kunt u de inhoud bewerken en de gewenste updates uitvoeren.

Inhoud wordt toegevoegd met [componenten](/help/sites-classic-ui-authoring/classic-page-author-default-components.md) (van toepassing op het inhoudstype) dat naar de pagina kan worden gesleept. Deze kunnen vervolgens worden bewerkt, verplaatst of verwijderd.

>[!NOTE]
>
>Uw account heeft de [passende toegangsrechten](/help/sites-administering/security.md) en [machtigingen](/help/sites-administering/security.md#permissions) om pagina&#39;s te bewerken, bijvoorbeeld om componenten toe te voegen, te bewerken of te verwijderen, notities toe te voegen, te ontgrendelen.
>
>Als u om het even welke problemen ontmoet wij adviseren u uw systeembeheerder contacteert.

## Sidekick {#sidekick}

De assistent is een belangrijk hulpmiddel bij het ontwerpen van pagina&#39;s. Het zweeft wanneer het ontwerpen van een pagina, zodat is het altijd zichtbaar.

Er zijn verschillende tabbladen en pictogrammen beschikbaar, waaronder:

* Onderdelen
* Pagina
* Informatie
* Versioning
* Workflow
* Modi
* Basisstructuur
* Clientcontext
* Websites

![chlimage_1-71](assets/chlimage_1-71.png)

Deze bieden toegang tot een breed scala aan functies, waaronder:

* [selecteren, componenten](/help/sites-classic-ui-authoring/classic-page-author-env-tools.md#sidekick)
* [verwijzingen tonen](/help/sites-classic-ui-authoring/classic-page-author-env-tools.md#showing-references)
* [toegang tot het auditlogboek](/help/sites-classic-ui-authoring/classic-page-author-env-tools.md#audit-log)
* [schakelmodi](/help/sites-classic-ui-authoring/classic-page-author-env-tools.md#page-modes)
* [maken](/help/sites-classic-ui-authoring/classic-page-author-work-with-versions.md#creating-a-new-version), [herstellen](/help/sites-classic-ui-authoring/classic-page-author-work-with-versions.md#restoring-a-page-version-from-sidekick) en [vergelijking](/help/sites-classic-ui-authoring/classic-page-author-work-with-versions.md#comparing-with-a-previous-version) versies

* [publiceren](/help/sites-classic-ui-authoring/classic-page-author-publish-pages.md#publishing-a-page), [unpublishing](/help/sites-classic-ui-authoring/classic-page-author-publish-pages.md#unpublishing-a-page) een pagina

* [bewerken, pagina-eigenschappen](/help/sites-classic-ui-authoring/classic-page-author-edit-page-properties.md)

* [steigers](/help/sites-authoring/scaffolding.md)

* [clientcontext](/help/sites-administering/client-context.md)

## Een component invoegen {#inserting-a-component}

### Een component invoegen {#inserting-a-component-1}

Nadat u de pagina hebt geopend, kunt u beginnen met het toevoegen van inhoud. U doet dit door componenten (ook wel alinea&#39;s genoemd) toe te voegen.

Een nieuwe component invoegen:

1. Er zijn verschillende methoden om het type alinea te selecteren dat u wilt invoegen:

   * Dubbelklik op het gebied met het label **Componenten of elementen hierheen slepen...** - de **Nieuwe component invoegen** wordt geopend. Selecteer een component en klik op **OK**.

   * Sleep een component van de zwevende werkbalk (sidekick genoemd) om een nieuwe alinea in te voegen.
   * Klik met de rechtermuisknop op een bestaande alinea en selecteer **Nieuw...** - De werkbalk Nieuwe component invoegen wordt geopend. Selecteer een component en klik op **OK**.

   ![screen_shot_2012-02-15at115605am](assets/screen_shot_2012-02-15at115605am.png)

1. In zowel de sidekick als de **Nieuwe component invoegen** op de werkbalk ziet u een lijst met de beschikbare componenten (alineatypen). Deze secties kunnen worden gesplitst in verschillende secties (bijvoorbeeld Algemeen, Kolommen, enzovoort), die naar behoefte kunnen worden uitgebreid.

   Afhankelijk van uw productieomgeving kunnen deze opties afwijken. Voor volledige informatie over componenten raadpleegt u [Standaardcomponenten](/help/sites-classic-ui-authoring/classic-page-author-default-components.md).

1. Voeg de gewenste component op de pagina in. Dubbelklik vervolgens op de alinea en er wordt een venster geopend waarin u de alinea kunt configureren en inhoud kunt toevoegen.

### Een component invoegen met de Inhoudszoeker {#inserting-a-component-using-the-content-finder}

U kunt ook een nieuwe component aan de pagina toevoegen door een element van de [Inhoudzoeker](/help/sites-classic-ui-authoring/classic-page-author-env-tools.md#the-content-finder). Hierdoor wordt automatisch een component van het juiste type gemaakt die het element bevat.

Dit is geldig voor de volgende elementtypen (sommige zijn afhankelijk van het pagina-/alineasysteem):

| Elementtype | Resulterend componenttype |
|---|---|
| Afbeelding | Afbeelding |
| Document | Downloaden |
| Product | Product |
| Video | Flash |

>[!NOTE]
>
>Dit gedrag kan voor uw installatie worden gevormd. Zie [Een alineasysteem configureren, zodat een componentinstantie wordt gemaakt wanneer u een element sleept](/help/sites-developing/developing-components.md#configuring-a-paragraph-system-so-that-dragging-an-asset-creates-a-component-instance) voor nadere bijzonderheden.

Een component maken door een van de bovenstaande elementtypen te slepen:

1. Zorg ervoor dat de pagina zich bevindt in [**Bewerken** mode](/help/sites-classic-ui-authoring/classic-page-author-env-tools.md#page-modes).
1. Open de [Inhoudzoeker](/help/sites-classic-ui-authoring/classic-page-author-env-tools.md#the-content-finder).
1. Sleep het vereiste element naar de gewenste positie. De [tijdelijke aanduiding voor onderdeel](#componentplaceholder) Hiermee kunt u zien waar de component wordt geplaatst.

   Een component die geschikt is voor het type element, wordt op de vereiste locatie gemaakt. De component bevat het geselecteerde element.

1. [Bewerken](#editmovecopypastedelete) het onderdeel, indien nodig.

## Een component bewerken (inhoud en eigenschappen) {#editing-a-component-content-and-properties}

Voer een van de volgende handelingen uit om een bestaande alinea te bewerken:

* **Dubbelklikken** de alinea die u wilt openen. U ziet hetzelfde venster als wanneer u de alinea met de bestaande inhoud hebt gemaakt. Breng uw veranderingen aan en klik **OK**.

* **Klikken met rechtermuisknop** de alinea en klik op **Bewerken**.

* **Klikken** twee keer op de alinea (een langzame dubbelklik) om naar de bewerkingsmodus op de plaats te gaan. U kunt de tekst op de pagina rechtstreeks bewerken in plaats van in een dialoogvenster. In deze modus krijgt u een werkbalk boven aan de pagina. Breng gewoon uw wijzigingen aan en deze worden automatisch opgeslagen.

## Een component verplaatsen {#moving-a-component}

Een alinea verplaatsen:

>[!NOTE]
>
>U kunt ook [Knippen en plakken](#cut-copy-paste-a-component) een component verplaatsen.

1. Selecteer de alinea die u wilt verplaatsen:

   ![screen_shot_2012-02-15at115855am](assets/screen_shot_2012-02-15at115855am.png)

1. Sleep de alinea naar de nieuwe locatie - AEM geeft aan waar de alinea naartoe kan worden verplaatst met een groen vinkje. Zet het neer op de gewenste plaats.
1. Uw alinea wordt verplaatst:

   ![screen_shot_2012-02-15at120030pm](assets/screen_shot_2012-02-15at120030pm.png)

## Een component verwijderen {#deleting-a-component}

Een alinea verwijderen:

1. Selecteer de alinea en **rechtsklikken**:

   ![screen_shot_2012-02-15at120220pm](assets/screen_shot_2012-02-15at120220pm.png)

1. Selecteren **Verwijderen** in het menu. AEM WCM vraagt om bevestiging dat u de paragraaf wilt schrappen aangezien deze actie niet ongedaan kan worden gemaakt.
1. Klikken **OK**.

>[!NOTE]
>
>Als u uw [Gebruikerseigenschappen om de algemene bewerkingswerkbalk weer te geven](/help/sites-classic-ui-authoring/author-env-user-props.md) u kunt ook bepaalde handelingen op de alinea&#39;s uitvoeren met de opdracht **Kopiëren**, **Knippen**, **Plakken**, **Verwijderen** beschikbare knoppen.
>
>Diversen [sneltoetsen](/help/sites-classic-ui-authoring/classic-page-author-keyboard-shortcuts.md) zijn ook beschikbaar.

## Een component knippen/kopiëren/plakken {#cut-copy-paste-a-component}

Als wanneer [Een component verwijderen](#deleting-a-component) u kunt het contextmenu gebruiken om een component te kopiëren, te knippen en/of te plakken

>[!NOTE]
>
>Als u uw [Gebruikerseigenschappen om de algemene bewerkingswerkbalk weer te geven](/help/sites-classic-ui-authoring/author-env-user-props.md) u kunt ook bepaalde handelingen op de alinea&#39;s uitvoeren met de opdracht **Kopiëren**, **Knippen**, **Plakken**, **Verwijderen** beschikbare knoppen.
>
>Diversen [sneltoetsen](/help/sites-classic-ui-authoring/classic-page-author-keyboard-shortcuts.md) zijn ook beschikbaar.

>[!NOTE]
>
>Inhoud knippen, kopiëren en plakken wordt alleen op dezelfde pagina ondersteund.

## Overgenomen componenten {#inherited-components}

Overerfde componenten kunnen het product van diverse scenario&#39;s zijn, die omvatten:

* [Beheer van meerdere sites](/help/sites-administering/msm.md), ook in combinatie met [steigers](/help/sites-classic-ui-authoring/classic-feature-scaffolding.md#scaffolding-with-msm-inheritance).

* [Starten](/help/sites-classic-ui-authoring/classic-launches.md) (op basis van livecopy).
* Specifieke componenten, bijvoorbeeld het Overgenomen alineasysteem in Geometrixx.

U kunt de overerving annuleren (en vervolgens opnieuw inschakelen). Afhankelijk van de component, kan dit beschikbaar zijn bij:

1. **Live kopie**

   Als een component deel uitmaakt van een livecopy of lancering, wordt het aangegeven met een hangslotpictogram. U kunt op het hangslot klikken om de overerving te annuleren.

   * Het hangslotpictogram wordt weergegeven wanneer de component is geselecteerd, bijvoorbeeld:

   ![chlimage_1-72](assets/chlimage_1-72.png)

   * Het hangslot wordt ook weergegeven in het dialoogvenster met componenten, bijvoorbeeld:

   ![chlimage_1-73](assets/chlimage_1-73.png)

1. **Een overerfd alineasysteem**

   Het configuratiedialoogvenster. Bijvoorbeeld, zoals met het Overgenomen Systeem van de Paragraaf binnen Geometrixx:

   ![chlimage_1-74](assets/chlimage_1-74.png)

## Annotaties toevoegen {#adding-annotations}

[Annotaties](/help/sites-classic-ui-authoring/classic-page-author-annotations.md) andere auteurs toestaan feedback over uw inhoud te geven. Dit wordt vaak gebruikt voor evaluatie- en validatiedoeleinden.

## Pagina&#39;s voorvertonen {#previewing-pages}

Er zijn twee pictogrammen in de onderrand van het hulpstuk die belangrijk zijn voor het voorvertonen van pagina&#39;s:

![De onderrand van het hulpje met een horizontale rij van zeven pictogrammen. Twee van de pictogrammen aan het begin van de rij, het bewerkingspictogram en het pictogram van de voorvertoningsmodus, worden aangegeven met respectievelijk een potloodsymbool en een vergrootglassymbool.](do-not-localize/chlimage_1-5.png)

* Met het potloodpictogram kunt u zien dat u in de bewerkingsmodus werkt waar u inhoud kunt toevoegen, wijzigen, verplaatsen of verwijderen.

  ![Het pictogram Bewerken dat wordt aangegeven door een potloodsymbool.](do-not-localize/chlimage_1-6.png)

* Met het vergrootglaspictogram kunt u de voorbeeldmodus selecteren waarin de pagina wordt weergegeven zoals deze wordt weergegeven in de publicatieomgeving (pagina&#39;s moeten soms ook worden vernieuwd):

  ![Voorvertoningsmoduspictogram dat wordt aangeduid door een vergrootglassymbool.](do-not-localize/chlimage_1-7.png)

  In de voorvertoningsmodus wordt het hulpgereedschap kleiner, klikt u op het pijlpictogram omlaag om terug te keren naar de bewerkingsmodus:

  ![Staaf met AEM als titel en pictogram van de bewerkingsmodus rechts van de titel die wordt aangegeven door een pijl-omlaag.](do-not-localize/chlimage_1-8.png)

## Zoeken en vervangen {#find-replace}

Voor grootschaliger bewerkingen van dezelfde zin als a **[Zoeken en vervangen](/help/sites-classic-ui-authoring/author-env-search.md#find-and-replace)** met de menuoptie kunt u zoeken naar meerdere instanties van een tekenreeks in een sectie van de website en deze vervangen.

## Een pagina vergrendelen {#locking-a-page}

AEM kunt u een pagina vergrendelen, zodat niemand anders de inhoud kan wijzigen. Dit is handig wanneer u meerdere bewerkingen uitvoert op een bepaalde pagina of wanneer u een pagina even wilt stilzetten.

>[!CAUTION]
>
>Het vergrendelen van een pagina moet voorzichtig worden toegepast, aangezien de enige persoon die een pagina kan ontgrendelen de persoon is die deze heeft vergrendeld (of een account met beheerdersrechten).

Een pagina vergrendelen:

1. In de **Websites** selecteert u de pagina die u wilt vergrendelen.
1. Dubbelklik op de pagina om deze te openen voor bewerking.
1. In de **Pagina** tab of sidekick, selecteer **Pagina vergrendelen**:

   ![screen_shot_2012-02-08at15750pm](assets/screen_shot_2012-02-08at15750pm.png)

   Een bericht geeft aan dat de pagina is vergrendeld voor andere gebruikers. Bovendien in de juiste ruit van **Websites** , AEM WCM de pagina als vergrendeld weergeeft en aangeeft welke gebruiker de pagina heeft vergrendeld.

   ![screen_shot_2012-02-08at20657pm](assets/screen_shot_2012-02-08at20657pm.png)

## Een pagina ontgrendelen {#unlocking-a-page}

Een pagina ontgrendelen:

1. In de **Websites** selecteert u de pagina die u wilt ontgrendelen.
1. Dubbelklik op de pagina om deze te openen.
1. In de **Pagina** tab of sidekick, selecteer **Pagina ontgrendelen**.

## Paginabewerkingen ongedaan maken en opnieuw uitvoeren {#undoing-and-redoing-page-edits}

Gebruik de volgende sneltoetsen terwijl het inhoudsframe van de pagina de focus heeft:

* Ongedaan maken: Ctrl+Z (Windows) of Cmd+Z (Mac)
* Opnieuw: Ctrl+Y (Windows) of Cmd+Y (Mac)

Wanneer u het verwijderen, optellen of verplaatsen van een of meer alinea&#39;s ongedaan maakt of opnieuw uitvoert, geven opvlammende (standaardgedrag) markeringen de desbetreffende alinea&#39;s aan.

>[!NOTE]
>
>Zie [Paginabewerkingen ongedaan maken en opnieuw uitvoeren - De theorie](#undoing-and-redoing-page-edits-the-theory) voor de volledige details van wat mogelijk is wanneer het ongedaan maken van en het opnieuw doen van paginaedetingen.

## Paginabewerkingen ongedaan maken en opnieuw uitvoeren - De theorie {#undoing-and-redoing-page-edits-the-theory}

>[!NOTE]
>
>Uw systeembeheerder kan [Verschillende aspecten van de functies Ongedaan maken/Opnieuw configureren](/help/sites-administering/config-undo.md) volgens de vereisten voor uw exemplaar.

AEM slaat een geschiedenis op van acties die u uitvoert en de opeenvolging waarin u hen uitvoerde. U maakt dus verschillende handelingen ongedaan in de volgorde waarin u deze hebt uitgevoerd. Vervolgens kunt u de opdracht Opnieuw uitvoeren gebruiken om een of meer handelingen opnieuw toe te passen.

Als een element op de inhoudspagina wordt geselecteerd, is het ongedaan maken en opnieuw doen bevel op het geselecteerde punt, zoals een tekstcomponent van toepassing.

Het gedrag van de opdrachten Ongedaan maken en Opnieuw is vergelijkbaar met dat van andere softwareprogramma&#39;s. Gebruik de opdrachten om de recente status van uw webpagina te herstellen terwijl u beslissingen neemt over de inhoud. Als u bijvoorbeeld een tekstalinea naar een andere locatie op de pagina verplaatst, kunt u de opdracht Ongedaan maken gebruiken om de alinea terug te verplaatsen. Als u vervolgens nogmaals besluit de alinea te verplaatsen, gebruikt u de opdracht Opnieuw uitvoeren.

>[!NOTE]
>
>U kunt:
>
>* Voer handelingen opnieuw uit zolang u geen paginabewerking hebt uitgevoerd nadat u de handeling Ongedaan maken hebt gebruikt.
>* U kunt maximaal 20 bewerkhandelingen ongedaan maken (standaardinstelling).
>* ook gebruiken [Sneltoetsen](/help/sites-classic-ui-authoring/classic-page-author-keyboard-shortcuts.md) voor ongedaan maken en opnieuw uitvoeren.
>

U kunt de volgende typen paginawijzigingen ongedaan maken en opnieuw uitvoeren:

* Alinea&#39;s toevoegen, bewerken, verwijderen en verplaatsen
* Lokaal bewerken van alinea-inhoud
* Items op een pagina kopiëren, knippen en plakken
* Items op pagina&#39;s kopiëren, knippen en plakken
* Bestanden en afbeeldingen toevoegen, verwijderen en wijzigen
* Annotaties en schetsen toevoegen, verwijderen en wijzigen
* Wijzigingen in Vet
* Referenties toevoegen en verwijderen
* Eigenschapswaarden wijzigen in dialoogvensters van componenten.

Formuliervelden die door formuliercomponenten worden gerenderd, mogen geen waarden hebben die zijn opgegeven tijdens het ontwerpen van pagina&#39;s. De opdrachten Ongedaan maken en Opnieuw hebben daarom geen invloed op wijzigingen die u aanbrengt in de waarden van die typen componenten. U kunt bijvoorbeeld het selecteren van een waarde in een vervolgkeuzelijst niet ongedaan maken.

>[!NOTE]
>
>Er zijn speciale machtigingen vereist voor het ongedaan maken en opnieuw uitvoeren van wijzigingen in bestanden en afbeeldingen. De historie voor het ongedaan maken van wijzigingen in bestanden en afbeeldingen duurt bovendien minimaal uren. Na deze tijd is het ongedaan maken van de wijzigingen echter niet gegarandeerd. Uw beheerder kan toestemmingen verstrekken en de standaardtijd van tien uren veranderen.
