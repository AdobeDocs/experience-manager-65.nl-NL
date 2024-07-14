---
title: Pakketbeheer
description: Leer de grondbeginselen van AEM pakketbeheer met Package Manager.
feature: Administering
role: Admin
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: content
content-type: reference
docset: aem65
exl-id: e8929d7c-9920-4c02-95a9-6f7f7a365203
solution: Experience Manager, Experience Manager Sites
source-git-commit: c705667e60ccfbc4612ef3212dbe549e6bea66a9
workflow-type: tm+mt
source-wordcount: '3568'
ht-degree: 0%

---


# Pakketbeheer {#working-with-packages}

Pakketten maken het importeren en exporteren van inhoud in de opslagplaats mogelijk. U kunt pakketten gebruiken om nieuwe inhoud te installeren, nieuwe functionaliteit te installeren, inhoud over te brengen tussen instanties, en file bewaarplaats inhoud.

Met Package Manager kunt u pakketten overbrengen tussen uw AEM en uw lokale bestandssysteem voor ontwikkelingsdoeleinden.

## Wat zijn pakketten? {#what-are-packages}

Een pakket is een gecomprimeerd bestand met opslagplaats-inhoud in serialisatie van het bestandssysteem, zogenaamde vault serialization, waarmee bestanden en mappen eenvoudig kunnen worden weergegeven en bewerkt. Inhoud in het pakket wordt met filters gedefinieerd.

Een pakket bevat ook vault meta-informatie, met inbegrip van de filterdefinities en de informatie van de de invoerconfiguratie. Extra eigenschappen van inhoud, die niet worden gebruikt voor het uitpakken van pakketten, kunnen in het pakket worden opgenomen, zoals een beschrijving, een visuele afbeelding of een pictogram. Deze eigenschappen voor extra inhoud zijn alleen bedoeld voor de consument van het inhoudspakket en alleen ter informatie.

>[!NOTE]
>
>Pakketten vertegenwoordigen de huidige versie van de inhoud op het moment dat het pakket wordt gemaakt. Ze bevatten geen vorige versies van de inhoud die AEM in de opslagplaats bewaart.

## Pakketbeheer {#package-manager}

Pakketbeheer beheert de pakketten op de AEM installatie. Nadat u [ de noodzakelijke toestemmingen ](#permissions-needed-for-using-the-package-manager) hebt toegewezen kunt u de Manager van het Pakket voor diverse acties, met inbegrip van het vormen, het bouwen, het downloaden, en het installeren van uw pakketten gebruiken.

### Vereiste machtigingen {#required-permissions}

Gebruikers moeten over de juiste machtigingen beschikken voor het maken, wijzigen, uploaden en installeren van pakketten:

* Volledige rechten behalve verwijderen op `/etc/packages`
* The node that contains the package contents

>[!CAUTION]
>
>Het verlenen van toestemmingen voor pakketten kan tot gevoelige informatieonthulling en gegevensverlies leiden.
>
>Om deze risico&#39;s te beperken, wordt het hoogst geadviseerd om specifieke groepstoestemmingen over specifieke slechts subbomen te verlenen.

### Pakketbeheer openen {#accessing}

U kunt tot de Manager van het Pakket op drie manieren toegang hebben:

1. Van het AEM belangrijkste menu > **Hulpmiddelen** > **Plaatsing** > **Pakketten**
1. Van [ CRXDE Lite ](/help/sites-developing/developing-with-crxde-lite.md) gebruikend de hoogste schakelaarbar
1. Direct via `http://<host>:<port>/crx/packmgr/`

### Gebruikersinterface pakketbeheer {#ui}

Pakketbeheer is verdeeld in vier belangrijke functionele gebieden:

* **Linkerpaneel van de Navigatie** - dit paneel laat u filteren en de lijst van pakketten sorteren.
* **Lijst van het Pakket** - dit is de lijst van pakketten op uw instantie gefiltreerd en gesorteerd per selecties in het Linkerpaneel van de Navigatie.
* **Logboek van de Activiteit** - Dit paneel wordt geminimaliseerd eerst en breidt zich uit om de activiteit van de Manager van het Pakket zoals te detailleren wanneer een pakket wordt gebouwd of geïnstalleerd. Er zijn extra knoppen op het tabblad Activiteitenlog voor:
   * **Duidelijk Logboek**
   * **tonen/verbergen**
* **Toolbar** - de toolbar bevat vernieuwt knopen voor het Linkerpaneel van de Navigatie en de lijst van het Pakket en knopen voor het zoeken, het creëren, en het uploaden van pakketten.

![ UI van de Manager van het Pakket ](assets/package-manager-ui.png)

Wanneer u op een optie in het linkernavigatievenster klikt, wordt de pakketlijst direct gefilterd.

Wanneer u op een pakketnaam klikt, wordt het item in de pakketlijst uitgebreid en worden meer details over het pakket weergegeven.

![ Uitgebreide pakketdetails ](assets/package-expand.png)

Er is een aantal acties dat op een pakket via de beschikbare toolbarknopen kan worden ondernomen wanneer het pakketdetail wordt uitgebreid.

* [Bewerken](#edit-package)
* [Opbouwen](#building-a-package)
* [Opnieuw installeren](#reinstalling-packages)
* [Downloaden](#downloading-packages-to-your-file-system)
* [Delen](#share)

De verdere acties zijn beschikbaar onder **Meer** knoop.

* [Verwijderen](#deleting-packages)
* [Dekking](#package-coverage)
* [Inhoud](#viewing-package-contents-and-testing-installation)
* [Omloop](#rewrapping-a-package)
* [Andere versies](#other-versions)
* [Verwijderen](#uninstalling-packages)
* [Installeren testen](#viewing-package-contents-and-testing-installation)
* [Valideren](#validating-packages)
* [Repliceren](#replicating-packages)

### Pakketstatus {#package-status}

Elk item in de pakketlijst heeft een statusindicator waarmee u in één oogopslag de status van het pakket kunt zien. Als u de muisaanwijzer boven de status houdt, wordt knopinfo met de details van de status weergegeven.

![ status van het Pakket ](assets/package-status.png)

Als het pakket is gewijzigd of nooit is gemaakt, wordt de status weergegeven als een koppeling waarmee u snel actie kunt ondernemen om het pakket opnieuw samen te stellen of te installeren.

## Pakketinstellingen {#package-settings}

Een pakket is in wezen een set filters en de gegevens in de opslagplaats op basis van die filters. Gebruikend de Manager UI van het Pakket, kunt u een pakket klikken en dan **uitgeven** knoop om de details van een pakket met inbegrip van de volgende montages te bekijken.

* [Algemene instellingen](#general-settings)
* [Pakketfilters](#package-filters)
* [Pakketafhankelijke onderdelen](#package-dependencies)
* [Geavanceerde instellingen](#advanced-settings)
* [Schermafbeeldingen verpakken](#package-screenshots)

### Algemene instellingen {#general-settings}

U kunt diverse pakketinstellingen bewerken om informatie te definiëren, zoals de pakketbeschrijving, afhankelijkheden en providerdetails.

De **dialoog van de Montages van het Pakket** is beschikbaar via **geeft** knoop uit wanneer [ creërend ](#creating-a-new-package) of [ uitgevend ](#viewing-and-editing-package-information) een pakket. Nadat om het even welke veranderingen worden aangebracht, klik **sparen**.

![ geef de dialoog van het Pakket uit, algemene montages ](assets/general-settings.png)

| Veld | Beschrijving |
|---|---|
| Naam | De naam van het pakket |
| Groep | Voor het organiseren van pakketten kunt u de naam van een nieuwe groep typen of een bestaande groep selecteren |
| Versie | Te gebruiken tekst voor de versie |
| Beschrijving | Een korte beschrijving van het pakket waarmee HTML-opmaakcodes voor opmaak kunnen worden gebruikt |
| Miniatuur | Het pictogram dat bij de pakketvermelding wordt weergegeven |

#### Miniaturen pakket {#thumbnails}

Een miniatuur geeft snel een visuele referentie van wat het pakket bevat. Dit wordt vervolgens weergegeven in de pakketlijst en kan u helpen het pakket of de klasse van het pakket gemakkelijk te identificeren.

Hieronder volgen voorbeelden van conventies voor officiële pakketten:

Officiële hotfix

![ Officiële hotfix duimnagel ](assets/official-hotfix.png)

Officiële AEM installatie van de extensie

![ Officiële AEM installatie of uitbreidingsduimnagel ](assets/official-installation.png)

Officieel servicepakket

![ Officieel AEM pictogram van het de dienstpak ](assets/official-service-pack.png)

Gebruik een uniek pictogram voor uw pakket. Gebruik een pictogram dat door de Adobe wordt gebruikt niet opnieuw.

### Pakketfilters {#package-filters}

Filters identificeren de knooppunten in de opslagplaats die in het pakket moeten worden opgenomen. A **Definitie van de Filter** specificeert de volgende informatie:

* De **Weg van de Wortel** van de te omvatten inhoud
* **Regels** die specifieke knopen onder de wortelweg omvatten of uitsluiten

Voeg regels toe gebruikend **+** knoop. Verwijder regels met de knop **-** .

De regels worden toegepast volgens hun orde zodat plaats hen zoals vereist gebruikend **Omhoog** en **Omlaag** pijlknopen.

Filters kunnen nul of meer regels bevatten. Als er geen regels zijn gedefinieerd, bevat het pakket alle inhoud onder het hoofdpad.

U kunt een of meer filterdefinities definiëren voor een pakket. Gebruik meerdere filters om inhoud van meerdere hoofdpaden op te nemen.

![ het lusje van Filters ](assets/edit-filter.png)

Wanneer u regels maakt, definieert u een reguliere expressie (ook wel regex, regexp of rationele expressie genoemd) om alle knooppunten op te geven die u wilt opnemen in of uitsluiten.

| Type regel | Beschrijving |
|---|---|
| include | Met Opnemen worden alle bestanden en mappen in de opgegeven map opgenomen die overeenkomen met de reguliere expressie. Omvat **zal** geen andere dossiers of omslagen van onder de gespecificeerde wortelweg omvatten. |
| uitsluiten | Met Uitsluiten worden alle bestanden en mappen uitgesloten die overeenkomen met de reguliere expressie. |

De filters van het pakket worden het vaakst bepaald wanneer u eerst [ het pakket creeert.](#creating-a-new-package) Deze kunnen echter ook later worden bewerkt. Vervolgens moet het pakket opnieuw worden samengesteld om de inhoud bij te werken op basis van de nieuwe filterdefinities.

>[!TIP]
>
>Eén pakket kan meerdere filterdefinities bevatten, zodat knooppunten van verschillende locaties gemakkelijk in één pakket kunnen worden gecombineerd.

>[!TIP]
>
>Voor achtergrondinformatie zie [ Apache Jasrabbit - de documentatie van de Filter van Workspace ](https://jackrabbit.apache.org/filevault/filter.html).

### Afhankelijkheden {#dependencies}

![ Afhankelijkheden tabel ](assets/dependencies.png)

| Veld | Beschrijving | Voorbeeld/details |
|---|---|---|
| Getest met | De productnaam en versie van dit pakket zijn bedoeld voor of zijn compatibel met. | `6.5` |
| Opgeloste problemen | Een tekstveld waarin details kunnen worden weergegeven van fouten die zijn opgelost met dit pakket, één bug per regel | - |
| Afhankelijk van | Vermeldt andere pakketten noodzakelijk zodat het huidige pakket zoals verwacht loopt wanneer geïnstalleerd | `groupId:name:version` |
| Vervangen | Een lijst met vervangen pakketten die door dit pakket worden vervangen | `groupId:name:version` |

### Geavanceerde instellingen {#advanced-settings}

![ Geavanceerde Montages tabel ](assets/advanced-settings.png)

| Veld | Beschrijving | Voorbeeld/details |
|---|---|---|
| Naam | De naam van de aanbieder van het pakket | `WKND Media Group` |
| URL | URL van de provider | `https://wknd.site` |
| Koppeling | Pakketspecifieke koppeling naar een providerpagina | `https://wknd.site/package/` |
| Vereisten | Definieert of er beperkingen zijn bij de installatie van het pakket | **Admin** - het pakket moet slechts met admin voorrechten <br>**opnieuw beginnen** worden geïnstalleerd - AEM moet na het installeren van het pakket opnieuw worden begonnen |
| Wisselstroomverwerking | Hiermee wordt opgegeven hoe de toegangsbeheerinformatie die in het pakket is gedefinieerd, wordt verwerkt wanneer het pakket wordt geïmporteerd | **negeren** - reserve ACLs in de bewaarplaats <br>**overschrijft** - Overschrijf ACLs in de bewaarplaats <br>**Samenvoegen** - fusie beide reeksen ACLs <br>**MergePreserve** - de toegangscontrole van de fusie in de inhoud met het pakket door de toegangsbeheeringangen van hoofden toe te voegen die niet in de inhoud <br>**duidelijk** zijn - ACLs |

### Schermafbeeldingen verpakken {#package-screenshots}

U kunt meerdere schermafbeeldingen aan het pakket toevoegen om een visuele weergave van de weergave van de inhoud te bieden.

![ het lusje van Screenshots ](assets/screenshots.png)

## Pakkethandelingen {#package-actions}

Er zijn vele acties die op een pakket kunnen worden ondernomen.

### Een pakket maken {#creating-a-new-package}

1. [Access Package Manager.](#accessing)

1. Klik **Create Pakket**.

   >[!TIP]
   >
   >Als uw instantie vele pakketten heeft, zou er een omslagstructuur op zijn plaats kunnen zijn. In dergelijke gevallen is het eenvoudiger om naar de vereiste doelmap te navigeren voordat u het nieuwe pakket maakt.

1. In de **Nieuwe dialoog van het Pakket**, ga de volgende gebieden in:

   ![ Nieuwe pakketdialoog ](assets/new-package-dialog.png)

   * **Naam van het Pakket** - selecteer een beschrijvende naam om u (en anderen) gemakkelijk te helpen de inhoud van het pakket identificeren.

   * **Versie** - dit is een tekstgebied voor u om op een versie te wijzen. Deze wordt aan de pakketnaam toegevoegd om de naam van het ZIP-bestand te vormen.

   * **Groep** - dit is de naam van de doelgroep (of omslag). Met groepen kunt u uw pakketten ordenen. Er wordt een map voor de groep gemaakt als deze nog niet bestaat. Als u de groepsnaam leeg laat, wordt het pakket gemaakt in de hoofdpakketlijst.

1. Klik **OK** om het pakket tot stand te brengen.

1. AEM geeft het nieuwe pakket boven aan de lijst met pakketten weer.

   ![ Nieuw pakket ](assets/new-package.png)

1. Klik **uitgeven** om de [ pakketinhoud te bepalen.](#package-contents) klik **sparen** nadat u wordt gebeëindigd het uitgeven van de montages.

1. U kunt [ nu bouwen ](#building-a-package) uw pakket.

Het is niet verplicht om het pakket onmiddellijk na het maken ervan te bouwen. Een ongebouwd pakket bevat geen inhoud en bestaat alleen uit de filtergegevens en andere metagegevens van het pakket.

### Een pakket maken {#building-a-package}

Een pakket wordt vaak gebouwd tezelfdertijd aangezien u [ het pakket ](#creating-a-new-package) creeert, maar u kunt op een recentere punt terugkeren om of het pakket te bouwen of opnieuw te bouwen. Dit kan nuttig zijn als de inhoud in de opslagplaats is gewijzigd of de pakketfilters zijn gewijzigd.

1. [Access Package Manager.](#accessing)

1. Open de pakketdetails uit de pakketlijst door op de pakketnaam te klikken.

1. Klik **bouwen**. Er wordt een dialoogvenster weergegeven waarin u moet bevestigen dat u het pakket wilt maken, aangezien bestaande pakketinhoud wordt overschreven.

1. Klik **OK**. AEM bouwt het pakket en geeft alle inhoud weer die aan het pakket is toegevoegd, zoals dit gebeurt in de lijst met activiteiten. Na voltooiing AEM wordt bevestigd dat het pakket is gemaakt en (wanneer u het dialoogvenster sluit) worden de gegevens in de pakketlijst bijgewerkt.

### Een pakket bewerken {#edit-package}

Nadat een pakket is geüpload naar AEM, kunt u de instellingen wijzigen.

1. [Access Package Manager.](#accessing)

1. Open de pakketdetails uit de pakketlijst door op de pakketnaam te klikken.

1. Klik **uitgeven** en werk de **[Montages van het Pakket](#package-settings)** zoals vereist bij.

1. Klik **sparen** om te bewaren.

U kunt het pakket ](#building-a-package) moeten herbouwen om zijn inhoud bij te werken die op de veranderingen wordt gebaseerd u aanbracht.[

### Een pakket opnieuw inpakken {#rewrapping-a-package}

Nadat een pakket is gemaakt, kan het opnieuw worden verpakt. Wanneer u de pakketgegevens opnieuw inpakt, worden deze zonder miniatuur, beschrijving, enzovoort gewijzigd, zonder dat de pakketinhoud wordt gewijzigd.

1. [Access Package Manager.](#accessing)

1. Open de pakketdetails uit de pakketlijst door op de pakketnaam te klikken.

1. Klik **uitgeven** en werk de **[Montages van het Pakket](#package-settings)** zoals vereist bij.

1. Klik **sparen** om te bewaren.

1. Klik **Meer** > **Terugloop** en een dialoog zal om bevestiging vragen.

### Andere pakketversies weergeven {#other-versions}

Omdat elke versie van een pakket in de lijst verschijnt zoals elk ander pakket, kan de Manager van het Pakket andere versies van een geselecteerd pakket vinden.

1. [Access Package Manager.](#accessing)

1. Open de pakketdetails uit de pakketlijst door op de pakketnaam te klikken.

1. Klik **Meer** > **Andere Versies** en een dialoog opent met een lijst van andere versies van het zelfde pakket met statusinformatie.

### Inhoud van pakket weergeven en installatie testen {#viewing-package-contents-and-testing-installation}

Nadat een pakket is samengesteld, kunt u de inhoud bekijken.

1. [Access Package Manager.](#accessing)

1. Open de pakketdetails uit de pakketlijst door op de pakketnaam te klikken.

1. Om de inhoud te bekijken, klik **Meer** > **Inhoud**, en de Manager van het Pakket maakt een lijst van de volledige inhoud van het pakket in het activiteitenlogboek.

   ![ Inhoud van het Pakket ](assets/package-contents.png)

1. Om een droge looppas van de installatie uit te voeren klik **Meer** > **de Test installeert** en de rapporten van de Manager van het Pakket in het activiteitenlogboek de resultaten alsof de installatie werd uitgevoerd.

   ![ de installatie van de Test ](assets/test-install.png)

### Pakketten naar uw bestandssysteem downloaden {#downloading-packages-to-your-file-system}

1. [Access Package Manager.](#accessing)

1. Open de pakketdetails uit de pakketlijst door op de pakketnaam te klikken.

1. Klik de **knoop van de Download** of de verbonden dossiernaam van het pakket in het gebied van pakketdetails.

1. AEM downloadt het pakket naar uw computer.

### Een pakket delen {#share}

Het Aandeel van het pakket was een gecentraliseerde openbare dienst om inhoudspakketten te verspreiden. Het Aandeel van het pakket is vervangen door [ Distributie van de Software ](#software-distribution) en deze knoop werkt niet meer.

### Pakketten uploaden vanuit uw bestandssysteem {#uploading-packages-from-your-file-system}

1. [Access Package Manager.](#accessing)

1. Selecteer de groepsmap waarin u het pakket wilt uploaden.

1. Klik **uploadt Pakket** knoop.

1. Geef de benodigde informatie over het geüploade pakket.

   ![ Pakket uploadt dialoog ](assets/package-upload-dialog.png)

   * **Pakket** - gebruik **doorbladert..** knoop om het vereiste pakket van uw lokaal dossiersysteem te selecteren.
   * **de Kracht uploadt** - als een pakket met deze naam reeds bestaat, dwingt deze optie uploadt en het bestaande pakket beschrijft.

1. Klik **O.K.** en het geselecteerde pakket wordt geupload en de pakketlijst wordt dienovereenkomstig bijgewerkt.

De pakketinhoud bestaat nu op AEM, maar om de inhoud voor gebruik beschikbaar te maken, ben zeker om het pakket ](#installing-packages) te installeren.[

### Pakketten valideren {#validating-packages}

Omdat pakketten bestaande inhoud kunnen wijzigen, is het vaak handig om deze wijzigingen te valideren voordat u ze installeert.

#### Validatieopties {#validation-options}

Pakketbeheer kan de volgende validaties uitvoeren:

* [OSGi-pakket importeren](#osgi-package-imports)
* [Bedekkingen](#overlays)
* [ACLs](#acls)

##### OSGi-pakketinvoer valideren {#osgi-package-imports}

**wat wordt gecontroleerd**

Deze bevestiging inspecteert het pakket voor alle JAR dossiers (bundels OSGi), haalt hun `manifest.xml` uit (die de versioned gebiedsdelen bevat waarop genoemde bundel OSGi) vertrouwt), en verifieert de AEM instantie uitvoert genoemde gebiedsdelen met de correcte versies.

**hoe het wordt gemeld**

Om het even welke versioned gebiedsdelen die niet door de AEM instantie kunnen worden tevredengesteld zijn vermeld in het Logboek van de Activiteit van de Manager van het Pakket.

**de Staten van de Fout**

Als de gebiedsdelen ontevreden zijn, dan zullen de bundels OSGi in het pakket met die gebiedsdelen niet beginnen. Dit resulteert in een gebroken toepassingsplaatsing aangezien om het even wat die op de unstarted bundel OSGi baseert zal beurtelings niet behoorlijk functioneren.

**Resolutie van de Fout**

Om fouten wegens ontevreden bundels op te lossen OSGi, moet de gebiedsdeelversie in de bundel met ontevreden invoer worden aangepast.

##### Bedekkingen valideren {#overlays}

**wat wordt gecontroleerd**

Deze validatie bepaalt of het pakket dat wordt geïnstalleerd een bestand bevat dat al wordt bedekt in de AEM.

Als u bijvoorbeeld een bestaande overlay van `/apps/sling/servlet/errorhandler/404.jsp` gebruikt, een pakket dat `/libs/sling/servlet/errorhandler/404.jsp` bevat, zodat het bestaande bestand van `/libs/sling/servlet/errorhandler/404.jsp` wordt gewijzigd.

**hoe het wordt uitgevoerd**

Dergelijke overlays worden beschreven in het activiteitenlogboek van Package Manager.

**de Staten van de Fout**

Een foutstatus houdt in dat het pakket probeert een bestand te implementeren dat al is bedekt. De wijzigingen in het pakket worden dus overschreven (en dus &quot;verborgen&quot;) door de bedekking en worden niet van kracht.

**Resolutie van de Fout**

Om dit probleem op te lossen, moet de beheerder van het overlaybestand in `/apps` de wijzigingen in het overlay-bestand in `/libs` controleren en de wijzigingen naar wens opnemen in de overlay ( `/apps` ) en het overlay-bestand opnieuw gebruiken.

>[!NOTE]
>
>Het validatiemechanisme kan niet worden afgestemd op de correcte integratie van de overlay-inhoud in het overlaybestand. Daarom zal deze validatie ook na de nodige wijzigingen over conflicten blijven rapporteren.

##### ACLs bevestigen {#acls}

**wat wordt gecontroleerd**

Deze bevestiging controleert welke toestemmingen worden toegevoegd, hoe zij zullen worden behandeld (samenvoegen/vervangen), en als de huidige toestemmingen zullen worden beïnvloed.

**hoe het wordt gemeld**

De toestemmingen worden beschreven in het Logboek van de Activiteit van de Manager van het Pakket.

**de Staten van de Fout**

Er kunnen geen expliciete fouten worden opgegeven. De bevestiging wijst eenvoudig erop of om het even welke nieuwe ACL toestemmingen zullen worden toegevoegd of beïnvloed door het pakket te installeren.

**Resolutie van de Fout**

Gebruikend de informatie die door de bevestiging wordt verstrekt, kunnen de beïnvloede knopen in CRXDE worden herzien en ACLs kan in het pakket aanpassen zoals nodig.

>[!CAUTION]
>
>Als beste praktijken wordt het geadviseerd dat de pakketten geen AEM-Verstrekte ACLs zouden moeten beïnvloeden aangezien dit in onverwacht gedrag kan resulteren.

#### Validatie uitvoeren {#performing-validation}

De validatie van pakketten kan op twee verschillende manieren worden uitgevoerd:

* [Via de interface van Package Manager](#via-package-manager)
* [Via HTTP-POST request zoals with cURL](#via-post-request)

Validatie moet altijd plaatsvinden na het uploaden van het pakket, maar voordat het wordt geïnstalleerd.

##### Pakketvalidatie via pakketbeheer {#via-package-manager}

1. [Access Package Manager.](#accessing)

1. Open de pakketdetails uit de pakketlijst door op de pakketnaam te klikken.

1. Om het pakket te bevestigen, klik **Meer** > **** bevestigen,

1. In het modale dialoogvakje dat dan verschijnt, gebruik checkboxes om het type (de) bevestiging te selecteren en met de bevestiging te beginnen door **te klikken bevestigt**.

1. De gekozen validatie(s) worden dan uitgevoerd en de resultaten worden weergegeven in het activiteitenlog van Package Manager.

##### Pakketvalidatie via HTTP POST Request {#via-post-request}

Het verzoek van de POST heeft de volgende vorm.

```
https://<host>:<port>/crx/packmgr/service.jsp?cmd=validate&type=osgiPackageImports,overlays,acls
```

De parameter `type` kan elke door komma&#39;s gescheiden, ongeordende lijst zijn die bestaat uit:

* `osgiPackageImports`
* `overlays`
* `acls`

De waarde van `type` wordt standaard ingesteld op `osgiPackageImports` als dit niet expliciet wordt doorgegeven.

Wanneer u cURL gebruikt, voert u een instructie uit die vergelijkbaar is met het volgende:

```shell
curl -v -X POST --user admin:admin -F file=@/Users/SomeGuy/Desktop/core.wcm.components.all-1.1.0.zip 'http://localhost:4502/crx/packmgr/service.jsp?cmd=validate&type=osgiPackageImports,overlays,acls'
```

Bij validatie via een aanvraag voor een POST wordt het antwoord teruggestuurd als een JSON-object.

### Pakketdekking weergeven {#package-coverage}

Pakketten worden gedefinieerd door hun filters. U kunt Package Manager filters van een pakket op uw bestaande opslagplaats inhoud laten toepassen om te tonen welke inhoud van de bewaarplaats door de filterdefinitie van het pakket wordt behandeld.

1. [Access Package Manager.](#accessing)

1. Open de pakketdetails uit de pakketlijst door op de pakketnaam te klikken.

1. Klik **Meer** > **Dekking**.

1. De dekkingsdetails worden vermeld in het activiteitenlog.

### Pakketten installeren {#installing-packages}

Wanneer u een pakket uploadt, wordt alleen de pakketinhoud aan de opslagplaats toegevoegd, maar deze is niet toegankelijk. Installeer het geüploade pakket om de inhoud van het pakket te gebruiken.

>[!CAUTION]
>
>Wanneer u een pakket installeert, kan bestaande inhoud worden overschreven of verwijderd. Upload een pakket alleen als u zeker weet dat de benodigde inhoud niet wordt verwijderd of overschreven.

Voordat u het pakket installeert, maakt Package Manager automatisch een pakket met momentopnamen dat de inhoud bevat die wordt overschreven. Deze momentopname wordt opnieuw geïnstalleerd als u het pakket verwijdert.

>[!CAUTION]
>
>* Als u digitale elementen installeert, moet u:
>  Deactiveer eerst de WorkflowLauncher.
>  Gebruik de het menuoptie van Componenten van de console OSGi om te deactiveren
>  `com.day.cq.workflow.launcher.impl.WorkflowLauncherImpl.`
>* Vervolgens activeert u de WorkflowLauncher opnieuw wanneer de installatie is voltooid.
>
>Als u de WorkflowLauncher deactiveert, zorgt u ervoor dat het Assets-importerframework de elementen niet (onbedoeld) manipuleert tijdens de installatie.

1. [Access Package Manager.](#accessing)

1. Open in de pakketlijst de pakketdetails van het pakket dat u wilt installeren door op de pakketnaam te klikken.

1. Of klik **installeer** knoop in de puntdetails of **installeer** verbinding in de pakketstatus.

1. In een dialoogvenster wordt bevestiging aangevraagd en kunnen aanvullende opties worden opgegeven.

   * **Extraheer slechts** - Extraheer het pakket slechts zodat geen momentopname wordt gecreeerd en daarom zal uninstall niet mogelijk zijn
   * **sparen Drempel** - Aantal transiënte knopen tot de automatische besparing wordt teweeggebracht (verhoging als u gezamenlijke wijzigingsuitzonderingen ontmoet)
   * **trekt Subpackages** - laat automatische extractie van subpakketten toe
   * **Behandeling van het Toegangsbeheer** - specificeert hoe de toegangsbeheerinformatie die in het pakket wordt bepaald wordt behandeld wanneer het pakket geïnstalleerd is (de opties zijn het zelfde als [ geavanceerde pakketmontages ](#advanced-settings))
   * **Afhandeling van Afhankelijkheden** - specificeer hoe de gebiedsdelen tijdens installatie worden behandeld

1. Klik **installeren**.

1. In het activiteitenlog wordt de voortgang van de installatie beschreven.

Zodra de installatie volledig en succesvol is, wordt de pakketlijst bijgewerkt en het woord **Geïnstalleerde** verschijnt in de pakketstatus.

### Pakketten opnieuw installeren {#reinstalling-packages}

Het opnieuw installeren van pakketten voert de zelfde stappen op een reeds geïnstalleerd pakket uit dat wanneer [ eerst het pakket installeert.](#installing-packages)

### Uploaden en installeren op basis van bestandssysteem {#file-system-based-upload-and-installation}

U kunt pakketbeheer volledig verlaten wanneer het installeren van pakketten. AEM kan pakketten detecteren die op een specifieke locatie in het lokale bestandssysteem van de hostcomputer zijn geplaatst en deze automatisch uploaden en installeren.

1. Onder de AEM installatiemap bevindt zich een `crx-quicksart` -map naast de map jar en `license.properties` . Maak een map met de naam `install` onder `crx-quickstart` . Dit leidt tot het pad `<aem-home>/crx-quickstart/install` .

1. Voeg in deze map uw pakketten toe. Deze worden automatisch geüpload en geïnstalleerd op uw exemplaar.

1. Nadat het uploaden en installeren is voltooid, kunt u de pakketten in Package Manager zien alsof u de interface van Package Manager hebt gebruikt om ze te installeren.

Als de instantie actief is, worden het uploaden en de installatie onmiddellijk gestart wanneer u het aan het pakket aan de map `install` toevoegt

Als de instantie niet wordt uitgevoerd, worden pakketten die in de map `install` zijn geplaatst, bij het opstarten in alfabetische volgorde geïnstalleerd.

### Pakketten verwijderen {#uninstalling-packages}

Als u het pakket verwijdert, wordt de inhoud van de opslagplaats teruggezet naar de momentopname die vóór de installatie automatisch door Package Manager is gemaakt.

1. [Access Package Manager.](#accessing)

1. Open de pakketdetails van het pakket dat u uit de pakketlijst wilt verwijderen door op de pakketnaam te klikken.

1. Klik **Meer** > **desinstalleert**, om de inhoud van dit pakket uit de bewaarplaats te verwijderen.

1. In een dialoogvenster wordt bevestiging gevraagd en worden alle aangebrachte wijzigingen vermeld.

1. Het pakket wordt verwijderd en de momentopname wordt toegepast. De voortgang van het proces wordt weergegeven in het activiteitenlog.

### Pakketten verwijderen {#deleting-packages}

Als u een pakket verwijdert, worden alleen de gegevens verwijderd uit Pakketbeheer. Als dit pakket al is geïnstalleerd, wordt de geïnstalleerde inhoud niet verwijderd.

1. [Access Package Manager.](#accessing)

1. Open de pakketdetails van het pakket dat u uit de pakketlijst wilt verwijderen door op de pakketnaam te klikken.

1. Pakketbeheer vraagt om bevestiging dat u het pakket wilt verwijderen. Klik **O.K.** om de schrapping te bevestigen.

1. De pakketinformatie wordt verwijderd en de details worden vermeld in het activiteitenlog.

### Pakketten repliceren {#replicating-packages}

Kopieer de inhoud van een pakket en installeer het op de publicatie-instantie.

1. [Access Package Manager.](#accessing)

1. Open de pakketdetails van het pakket dat u wilt repliceren uit de pakketlijst door op de pakketnaam te klikken.

1. Klik **Meer** > **Herhalen**.

1. Het pakket wordt gerepliceerd en de details worden gerapporteerd in het activiteitenlog.

## Softwaredistributie {#software-distribution}

AEM Pakketten kunnen worden gebruikt om inhoud te creëren en te delen over AEM milieu&#39;s.

[ de Distributie van de Software ](https://downloads.experiencecloud.adobe.com) is de gecentraliseerde dienst die wordt ontworpen om het onderzoek en de download van AEM pakketten te vereenvoudigen.

Voor meer informatie, zie de [ documentatie van de Distributie van de Software.](https://experienceleague.adobe.com/docs/experience-cloud/software-distribution/home.html)

>[!NOTE]
>
>De Manager van het pakket is momenteel niet geïntegreerd met de Distributie van de Software aangezien het met de vroegere dienst van het Aandeel van het Pakket was. Daarom werken de aandeelknopen en andere verbindingen aan het Aandeel van het Pakket binnen de Manager van het Pakket niet meer. U kunt pakketten downloaden naar uw lokale schijf.
