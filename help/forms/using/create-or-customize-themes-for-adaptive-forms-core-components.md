---
title: Hoe kunt u Aangepaste formulierthema's maken of aanpassen?
seo-title: How to create a theme for Adaptive Forms Core Components?
description: Leer om thema's voor Adaptive Forms Core Components te maken of aan te passen met BEM-specificaties
seo-description: Learn to create or customize themes for Adaptive Forms Core Components using BEM specifications
keywords: thema's maken voor adaptieve formulieren, kerncomponenten maken, nieuw thema maken, thema aanpassen, nieuw thema uploaden, thema gebruiken in formulieren, een thema verwijderen, een thema maken in AEM 6.5-formulieren
contentOwner: Khushwant Singh
topic-tags: Adaptive Forms
docset: aem65
role: Admin, Developer
source-git-commit: daf97f3d5c5f3c92ff5caeccff583e54f3f57364
workflow-type: tm+mt
source-wordcount: '2066'
ht-degree: 0%

---


# Inleiding tot thema {#introduction-to-theme}

| Versie | Artikelkoppeling |
| -------- | ---------------------------- |
| AEM 6,5 | Dit artikel |
| AEM as a Cloud Service | [Klik hier](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/adaptive-forms-authoring/authoring-adaptive-forms-core-components/create-an-adaptive-form-on-forms-cs/using-themes-in-core-components.html) |

In AEM Forms 6.5 is een thema een AEM clientbibliotheek waarmee u de stijlen (look and feel) voor een adaptief formulier kunt definiëren. Een thema bevat opmaakgegevens voor de componenten en deelvensters. Stijlen omvatten eigenschappen zoals achtergrondkleuren, statuskleuren, transparantie, uitlijning en grootte. Wanneer u een thema toepast, weerspiegelt de opgegeven stijl de corresponderende componenten. Een thema wordt onafhankelijk beheerd zonder verwijzing naar een adaptief formulier en kan opnieuw worden gebruikt in meerdere Adaptieve Forms.

## Beschikbare referentiethema&#39;s {#available-reference-theme}

AEM 6.5-omgeving biedt de onderstaande referentiethema&#39;s voor op Core Components gebaseerde Adaptive Forms:

* [Canvasthema](https://github.com/adobe/aem-forms-theme-canvas)
* [WKND-thema](https://github.com/adobe/aem-forms-theme-wknd)
* [EASEL-thema](https://github.com/adobe/aem-forms-theme-easel)

## Werken met de structuur van de thema&#39;s {#understanding-structure-of-theme}

Een thema is een pakket dat het CSS-bestand, JavaScript-bestanden en bronnen (zoals pictogrammen) omvat die de stijl van uw Adaptieve Forms definiëren. Het thema Adaptief formulier volgt op een specifieke organisatie, die bestaat uit de volgende onderdelen:

* `src/theme.scss`: Deze map bevat het CSS-bestand dat een grote invloed heeft op het hele thema. Het fungeert als een gecentraliseerde locatie voor het definiëren en beheren van de opmaak en het gedrag van uw thema. Door dit bestand te bewerken, kunt u wijzigingen aanbrengen die overal in het thema worden toegepast. Zo kunt u de vormgeving en functionaliteit van zowel de adaptieve Forms- als AEM Sites-pagina&#39;s wijzigen.

* `src/site`: Deze map bevat CSS-bestanden die worden toegepast op de gehele AEM sitepagina. Deze bestanden bestaan uit code en stijlen die van invloed zijn op de algemene functionaliteit en lay-out van de pagina van de AEM. Alle wijzigingen die u hier aanbrengt, worden doorgevoerd op alle pagina&#39;s van uw site.

* `src/components`: De CSS-bestanden in deze map zijn ontworpen voor afzonderlijke AEM kerncomponenten. Elke specifieke map voor een component bevat een `.scss` bestand dat die component in een adaptief formulier opmaakt. Bijvoorbeeld de `/src/components/button/_button.scss` Dit bestand bevat stijlinformatie voor de adaptieve Forms Button-component.

  ![Structuur van canvasthema](/help/forms/using/assets/component-based-theme-folder-structure.png)

* `src/resources`: Deze map bevat statische bestanden, zoals pictogrammen, logo&#39;s en lettertypen. Deze bronnen worden gebruikt om de visuele elementen en het algehele ontwerp van uw thema te verbeteren.

## Een thema maken

AEM Forms 6.5 biedt de onderstaande referentiethema&#39;s voor Core Components based Adaptive Forms.

* [Canvasthema](https://github.com/adobe/aem-forms-theme-canvas)
* [WKND-thema](https://github.com/adobe/aem-forms-theme-wknd)
* [EASEL-thema](https://github.com/adobe/aem-forms-theme-easel)

U kunt [al deze referentiethema&#39;s aanpassen om een thema te maken](#customize-a-theme-core-components).

## Een thema aanpassen {#customize-a-theme-core-components-based-adaptive-forms}

Wanneer u een thema aanpast, wordt hiermee verwezen naar het wijzigen en aanpassen van de weergave van een thema. Wanneer u een thema aanpast, brengt u wijzigingen aan in de ontwerpelementen, lay-out, kleuren, typografie en soms in de onderliggende code. Op deze manier kunt u een unieke en op maat gemaakte look voor uw website of toepassing maken met behoud van de basisstructuur en -functionaliteit die door het thema worden geboden.

>[!NOTE]
>
> * Gebruik de Manager van het Pakket om een thema op alle Auteur op te stellen en instanties te publiceren.
> * Net als elk ander pakket wordt via Package Manager een themaclient geïmporteerd of geëxporteerd.

### Vereisten om een thema aan te passen {#prerequisites}

* [Adaptieve Forms Core-componenten inschakelen](/help/forms/using/enable-adaptive-forms-core-components.md) voor uw omgeving.

* Installeer de nieuwste versie van [Apache Maven.](https://maven.apache.org/download.cgi) Apache Maven is een &#39;build automation tool&#39; die veel wordt gebruikt voor Java™-projecten. De installatie van de recentste versie verzekert u de noodzakelijke gebiedsdelen voor themaaanpassing.

* Leer hoe u een [clientbibliotheek in Adobe Experience Manager](https://experienceleague.adobe.com/docs/experience-manager-65/developing/introduction/clientlibs.html). AEM biedt clientbibliotheken, waarmee u uw code aan de clientzijde in de opslagplaats kunt opslaan, in categorieën kunt indelen en kunt bepalen wanneer en hoe elke categorie code aan de client moet worden aangeboden.

* Installeer een teksteditor zonder opmaak. Bijvoorbeeld Microsoft® Visual Studio Code. Het gebruiken van een gewone tekstredacteur zoals de Code van Microsoft® Visual Studio verstrekt een gebruikersvriendelijk milieu voor het uitgeven en het wijzigen van themadossiers.

* Zorg ervoor dat de AEM Forms-omgeving in gebruik is.

### Overwegingen om een thema aan te passen {#consideration}

* Zorg ervoor dat u [het project Archetype dat wordt gebruikt om Adaptive Forms Core Components in te schakelen](/help/forms/using/enable-adaptive-forms-core-components.md) in uw omgeving om uw thema&#39;s aan te passen.

* Wanneer u een adaptief formulier publiceert, worden de clientbibliotheken niet automatisch gepubliceerd in de instantie Publiceren. Zorg ervoor dat u de clientbibliotheek waarnaar wordt verwezen in een adaptief formulier, handmatig publiceert naar uw publicatieomgeving.

* Adobe raadt aan de klassenamen van clientbibliotheken niet te wijzigen.

### Een thema aanpassen {#customize-a-theme-core-components}

Het maken of aanpassen van een thema is een proces dat uit meerdere stappen bestaat. Voer de stappen in de lijst uit om het thema te maken/aan te passen:

1. [Een referentiethema klonen](#clone-git-repo-of-theme)
1. [De weergave van het thema aanpassen](#customize-the-theme)
1. [Bereid het thema voor lokale plaatsing](#generate-the-clientlib)
1. [Het thema implementeren in een lokale testomgeving](#deploy-the-theme-on-a-local-testing-environment)
1. [Het thema testen met een lokaal adaptief formulier](#test-the-theme-with-a-local-adaptive-form)
1. Het thema inzetten in de productieomgeving

![Workflow voor aanpassen van thema&#39;s](/help/forms/using/assets/custom-theme-steps.png)

De voorbeelden in het document zijn gebaseerd op de **Canvas** thema, maar u kunt elk verwijzingsthema klonen en dit aanpassen aan de hand van dezelfde instructies. Deze instructies zijn van toepassing op elk thema, zodat u thema&#39;s kunt aanpassen aan uw specifieke behoeften.

#### 1. De Git-opslagplaats van thema klonen {#clone-git-repo-of-theme}

Kies een van de volgende referentiethema&#39;s om een referentiethema voor op Core Components gebaseerde Adaptieve Forms te klonen:

* [Canvasthema](https://github.com/adobe/aem-forms-theme-canvas)
* [WKND-thema](https://github.com/adobe/aem-forms-theme-wknd)
* [EASEL-thema](https://github.com/adobe/aem-forms-theme-easel)

Voer de volgende instructies uit om een verwijzingsthema te klonen:

1. Open de opdrachtprompt of het terminalvenster in uw lokale ontwikkelomgeving.

1. Voer de `git clone` om een thema te klonen.

   ```
      git clone [Path of Git Repository of the theme]
   ```

   Vervang de [Pad van Git Repository van het thema] met de werkelijke URL van de overeenkomstige Git Repository van het thema

   Als u bijvoorbeeld het thema Canvas wilt klonen, voert u de volgende opdracht uit:

   ```
      git clone https://github.com/adobe/aem-forms-theme-canvas
   ```

1. Selecteren **De auteurs van alle bestanden in de bovenliggende map vertrouwen** en klik op **Ja, ik vertrouw de auteurs**.

Nadat de opdracht is uitgevoerd, beschikt u over een lokale kopie van het thema op uw computer in het dialoogvenster  `aem-forms-theme-canvas` map.

#### 2. Het thema aanpassen {#customize-the-theme}

U hebt de flexibiliteit om individuele componenten aan te passen of thema-vlakke veranderingen aan te brengen gebruikend de globale variabelen van een thema. Het wijzigen van algemene variabelen heeft een trapsgewijs effect op alle afzonderlijke componenten. U kunt bijvoorbeeld algemene variabelen gebruiken om de randkleur van alle componenten in een adaptief formulier te wijzigen of een levendige vulkleur toe te passen op de knop Oproepen naar handeling (CTA). U kunt:

* [Stijlen voor themaniveau instellen](#theme-customization-global-level)

* [Stijlen op componentniveau instellen](#component-based-customization)

##### Stijlen voor themaniveau instellen {#theme-customization-global-level}

De `variable.scss` bevat de algemene variabelen van het thema. Door deze variabelen bij te werken, kunt u op themaniveau op stijl betrekking hebbende veranderingen aanbrengen. Voer de volgende stappen uit om stijlen op themaniveau toe te passen:

1. Open de `<your-theme-sources>/src/site/_variables.scss` bestand voor bewerking.
1. Wijzig de waarde van een willekeurige eigenschap. De standaardfoutkleur is bijvoorbeeld rood. Als u de kleur van de fout wilt wijzigen van rood in blauw, wijzigt u de hexadecimale kleurcode van het dialoogvenster `$error`variabele. Bijvoorbeeld, `$error: #196ee5`.

   ![Voorbeeld: Foutkleur ingesteld op blauw](/help/forms/using/assets/theme-level-changes.png)

1. Sla het bestand op en sluit het.


U kunt ook de opdracht `variable.scss` bestand voor het instellen van lettertypefamilie en -type, thema- en lettertypekleuren, lettergrootte, themaspatiëring, foutpictogram, themarand en meer variabele die van invloed zijn op meerdere componenten van Adaptief formulier.

##### Stijlen op componentniveau instellen {#component-based-customization}

U kunt ook het lettertype, de kleur, de grootte en andere CSS-eigenschappen aanpassen van specifieke kerncomponenten van Adaptief formulier, zoals knoppen, selectievakjes, containers, voetteksten en nog veel meer. Door het CSS-bestand te bewerken dat aan de specifieke component is gekoppeld, kunt u de stijl ervan uitlijnen met de branding van uw organisatie. Ga als volgt te werk om de stijl van een component aan te passen:

1. Het bestand openen `<your-theme-sources>/src/components/<component>/<component.scss>` voor bewerken. Als u bijvoorbeeld de lettertypekleur van de knopcomponent wilt wijzigen, opent u de knop `<your-theme-sources>/src/components/button/button.scss`, bestand.
1. Wijzig desgewenst de waarde van een object. Als u bijvoorbeeld de kleur van de knopcomponent wilt wijzigen als u de muisaanwijzer op groen plaatst, wijzigt u de waarde van de optie `color: $white` eigenschap in de `cmp-adaptiveform-button__widget:hover` klasse aan hexadecimale code #12b453 of een andere groene tint. De uiteindelijke code ziet er als volgt uit:

   ```
    .cmp-adaptiveform-button__widget:hover {
    background: $dark-gray;
    color: #12b453;
    }
   ```


1. Sla het bestand op en sluit het.

<!--

   ![Example: Hover color set to green](/help/forms/using/assets/button-customization.png)

-->

>
>
> Wanneer een stijl zowel op thema als componentenniveau wordt bepaald, krijgt de stijl die op het componentenniveau wordt bepaald prioriteit.


#### 3. Maak het thema klaar voor implementatie {#generate-the-clientlib}

Om een thema in een AEM instantie op te stellen, moet het in een Bibliotheek van de Cliënt worden omgezet. Ga als volgt te werk om het thema om te zetten in een clientbibliotheek:

1. Open de opdrachtprompt of het terminalvenster.
1. Ga naar de `<your-theme-sources>` map. Bijvoorbeeld, `C:\aem-forms-theme-canvas`
1. Voer de volgende opdracht uit:

   ```
      npm run create-clientlib --category=adaptiveform.theme.[yourtheme]
   ```

   Vervangen `[yourtheme]` met de naam van uw aangepaste thema. Als het aangepaste thema bijvoorbeeld een naam heeft `customcanvastheme`, voert u de volgende opdracht uit

   ```
       npm run create-clientlib --category=adaptiveform.theme.customcanvastheme
   ```

   Wanneer de opdracht met succes is uitgevoerd, wordt een clientbibliotheekmap gemaakt op `themerepo\theme-clientlibs\[yourtheme]`.

   ![Client Library Generation](/help/forms/using/assets/clientlib_created.png)


   ![Locatie van clientbibliotheek](/help/forms/using/assets/adaptiveform.theme.easel.png)

#### 4. Het thema implementeren in een lokale testomgeving {#deploy-the-theme-on-a-local-testing-environment}

Voer de volgende stappen uit om het thema in te zetten in uw lokale ontwikkelings- of testomgeving:

1. Kopieer de clientbibliotheek die u in de vorige sectie hebt gemaakt naar het project Archetype op het volgende pad:

   `/ui.apps/src/main/content/jcr_root/apps/[AEM Archetype Project Folder]/clientlibs/<yourtheme>`

1. Open de Herinnering van het Bevel of Terminal.
1. Navigeer aan de wortelfolder van uw project van Archetype van de AEM, het project dat wordt gebruikt om de Aangepaste Componenten van de Kern van de Vorm toe te laten.
1. Voer de volgende opdracht uit om het aangepaste thema in uw omgeving in te stellen:

   `mvn clean install`

   ![Client Library Build](/help/forms/using/assets/mvndeploy.png)

#### 5. Het thema testen met een lokaal adaptief formulier {#test-the-theme-with-a-local-adaptive-form}

Het aangepaste thema toepassen en testen met een adaptief formulier:

**Thema toepassen tijdens het maken van een adaptief formulier**

1. Meld u aan bij de AEM Forms-auteur.

1. Tikken **Adobe Experience Manager** > **Forms** > **Forms &amp; Documenten**.

1. Klikken **Maken** > **Adaptieve Forms**. De wizard voor het maken van adaptief formulier wordt geopend.

1. Selecteer de sjabloon voor de kerncomponent in het dialoogvenster **Bron** tab.
1. Selecteer het thema in het dialoogvenster **Stijl** tab.
1. Klikken **Maken**.

Er wordt een adaptief formulier met het geselecteerde thema gemaakt.

**Thema toepassen op een bestaand adaptief formulier**

1. Meld u aan bij de AEM Forms-auteur.

1. Tikken **Adobe Experience Manager** > **Forms** > **Forms &amp; Documenten**.

1. Selecteer een adaptief formulier en klik op Eigenschappen.

1. Voor de **Thema-clientbibliotheek** selecteert u het thema.

1. Klikken **Opslaan en sluiten**.

Het geselecteerde thema wordt toegepast op het adaptieve formulier.


#### 5. Een thema implementeren in uw productieomgeving {#deploy-theme}

Nadat u het thema hebt getest in uw lokale ontwikkelomgeving, kunt u doorgaan met de implementatie van het thema in uw productieomgeving, inclusief de instanties Auteur en Publiceren. Voer de volgende stappen uit om het thema in uw productieomgevingen te implementeren:

1. Meld u aan bij uw AEM.
1. Open Package Manager. De standaard-URL is `https://localhost:4502/crx/packmgr/index.jsp`.
1. Klikken **Pakket uploaden** en klik op **Bladeren**.
1. Navigeren naar en selecteren `[AEM Archetype Project Folder]\all\target[appid].all-[version].zip`. Klikken **Openen**.
1. Klik op Installeren. Herhaal deze stap in alle productieomgevingen.


Nadat het pakket is geïnstalleerd, is het thema beschikbaar voor selectie.

![Thema-clientbibliotheek](/help/forms/using/assets/themeclientlibrary.png)

>
>
>Als u problemen ondervindt bij het openen van het aanmeldingsvenster op een publicatieexemplaar om het pakket te installeren via Package Manager, kunt u zich aanmelden via de volgende URL: `http://[Publish Server URL]:[PORT]/system/console`. Dit verleent toegang tot login aan Publish instantie, toestaand u om met het installatieproces te werk te gaan.

## Een thema toepassen op een adaptief formulier {#using-theme-in-adaptive-form}

De stappen voor het toepassen van een thema op een adaptief formulier zijn:

1. Meld u aan bij de AEM Forms-auteur.

1. Tikken **Adobe Experience Manager** > **Forms** > **Forms &amp; Documenten**.

1. Klikken **Maken** > **Adaptieve Forms**. De wizard voor het maken van adaptief formulier wordt geopend.

1. Selecteer de sjabloon voor de kerncomponent in het dialoogvenster **Bron** tab.
1. Selecteer het thema in het dialoogvenster **Stijl** tab.
1. Klikken **Maken**.

De thema&#39;s Adaptief formulier worden gebruikt als onderdeel van een adaptieve formuliersjabloon om opmaak te definiëren terwijl u een adaptief formulier maakt.

## Een thema verwijderen {#delete-a-theme}

Ongebruikte of ongewenste thema&#39;s verwijderen:

1. Meld u aan bij de instantie Auteur.
1. Open `http://[Publish Server URL]:[PORT]/crx/de/index.jsp`
1. Ga naar `apps/[AEM Archetype Project Folder]/clientlibs/[yourtheme]`.
1. Verwijder de themamap en sla de wijzigingen op.


## Veelgestelde vraag {#faq}

**V:** Welke aanpassing neemt prioriteit wanneer het maken van aanpassingen in een themamap op zowel het globale niveau als componentenniveau?

**Ans:** Wanneer een stijl op zowel het thema- als componentenniveau wordt bepaald, neemt de stijl die op het componentenniveau wordt bepaald belangrijkheid.

**V:** Welke stappen moeten worden ondernomen als het aangepaste thema niet zichtbaar is in het dialoogvenster **[!UICONTROL Theme Client Library]**?

**Ans:**  Als uw aangepaste thema niet wordt weergegeven in het dialoogvenster **[!UICONTROL Theme Client Library]** vervolgkeuzelijst, voer de volgende stappen uit:

1. Navigeer naar de locatie waar u de aangepaste thematclient-bibliotheek hebt toegevoegd. Het aanbevolen pad is `/ui.apps/src/main/content/jcr_root/apps[AEM Archetype Project Folder]/clientlibs/<yourtheme>`.

1. Open de `.content.xml` en neemt de volgende metagegevens op:

   ```
       formstheme:true
       allowproxy:true
   ```

1. Sla het bestand op en wijzig het thema.

## Zie ook

* [Een adaptief formulier op basis van kerncomponenten maken](create-an-adaptive-form-core-components.md)
* [Regeleditor gebruiken om dynamisch gedrag aan formulier toe te voegen](rule-editor.md)
* [Thema&#39;s maken of aanpassen voor adaptieve Forms op basis van Core Components](create-or-customize-themes-for-adaptive-forms-core-components.md)
* [Een sjabloon maken voor Adaptief Forms op basis van Core Components](template-editor.md)
* [Een adaptief formulier maken of toevoegen aan een AEM Sites-pagina of -ervaringsfragment](create-or-add-an-adaptive-form-to-aem-sites-page.md)

