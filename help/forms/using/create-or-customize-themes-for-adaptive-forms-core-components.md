---
title: Hoe kunt u Aangepaste formulierthema's maken of aanpassen?
description: Leer om thema's voor Adaptive Forms Core Components te maken of aan te passen met BEM-specificaties
keywords: thema's maken voor adaptieve formulieren, kerncomponenten maken, nieuw thema maken, thema aanpassen, nieuw thema uploaden, thema gebruiken in formulieren, een thema verwijderen, een thema maken in AEM 6.5-formulieren
contentOwner: Khushwant Singh
topic-tags: Adaptive Forms
docset: aem65
role: Admin, Developer
feature: Adaptive Forms,Core Components
exl-id: 9f9b35a3-0479-4179-9fad-994a482c96b6
solution: Experience Manager, Experience Manager Forms
source-git-commit: d7b9e947503df58435b3fee85a92d51fae8c1d2d
workflow-type: tm+mt
source-wordcount: '1933'
ht-degree: 0%

---

# Een adaptief formulierthema maken of aanpassen {#introduction-to-theme}

| Versie | Artikelkoppeling |
| -------- | ---------------------------- |
| AEM as a Cloud Service | [ klik hier ](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/adaptive-forms-authoring/authoring-adaptive-forms-core-components/create-an-adaptive-form-on-forms-cs/using-themes-in-core-components.html?lang=nl-NL) |
| AEM 6,5 | Dit artikel |


<!--**Applies to:** ✅ Adaptive Form Core Components ❎ [Adaptive Form Foundation Components](/help/forms/using/create-adaptive-form.md).-->

In AEM Forms 6.5 is een thema een AEM clientbibliotheek waarmee u de stijlen (look and feel) voor een adaptief formulier kunt definiëren. Een thema bevat opmaakgegevens voor de componenten en deelvensters. Stijlen omvatten eigenschappen zoals achtergrondkleuren, statuskleuren, transparantie, uitlijning en grootte. Wanneer u een thema toepast, weerspiegelt de opgegeven stijl de corresponderende componenten. Een thema wordt onafhankelijk beheerd zonder verwijzing naar een adaptief formulier en kan opnieuw worden gebruikt in meerdere Adaptieve Forms.

## Beschikbare thema&#39;s {#available-theme}

AEM 6.5-omgeving biedt de onderstaande thema&#39;s voor op Core Components gebaseerde Adaptive Forms:

* [ het thema van Canvas ](https://github.com/adobe/aem-forms-theme-canvas)
* [ WKND thema ](https://github.com/adobe/aem-forms-theme-wknd)
* [ EASEL thema ](https://github.com/adobe/aem-forms-theme-easel)
* [ het thema van FSI ](https://github.com/adobe/aem-forms-theme-fsi)
* [ thema van de Gezondheidszorg ](https://github.com/adobe/aem-forms-theme-healthcare)
* [ Openbaar thema ](https://github.com/adobe/aem-forms-theme-public)
* [ het thema van de Productie ](https://github.com/adobe/aem-forms-theme-manufacturing)

## Werken met de structuur van de thema&#39;s {#understanding-structure-of-theme}

Een thema is een pakket dat het CSS-bestand, JavaScript-bestanden en bronnen (zoals pictogrammen) omvat die de stijl van uw Adaptieve Forms definiëren. Het thema Adaptief formulier volgt op een specifieke organisatie, die bestaat uit de volgende onderdelen:

* `src/theme.scss`: Deze map bevat het CSS-bestand dat een grote invloed heeft op het hele thema. Het fungeert als een gecentraliseerde locatie voor het definiëren en beheren van de opmaak en het gedrag van uw thema. Door dit bestand te bewerken, kunt u wijzigingen aanbrengen die overal in het thema worden toegepast. Zo kunt u de vormgeving en functionaliteit van zowel de adaptieve Forms- als AEM Sites-pagina&#39;s wijzigen.

* `src/site`: Deze map bevat CSS-bestanden die worden toegepast op de gehele pagina van AEM site. Deze bestanden bestaan uit code en stijlen die van invloed zijn op de algemene functionaliteit en lay-out van de pagina van de AEM. Alle wijzigingen die u hier aanbrengt, worden doorgevoerd op alle pagina&#39;s van uw site.

* `src/components`: De CSS-bestanden in deze map zijn ontworpen voor afzonderlijke AEM kerncomponenten. Elke toegewijde map voor een component bevat een `.scss` -bestand waarmee die component in een adaptief formulier wordt geformatteerd. Het bestand `/src/components/button/_button.scss` bevat bijvoorbeeld stijlinformatie voor de component Adaptive Forms Button.

  ![ Structuur van het Thema van Canvas ](/help/forms/using/assets/component-based-theme-folder-structure.png)

* `src/resources`: deze map bevat statische bestanden, zoals pictogrammen, logo&#39;s en lettertypen. Deze bronnen worden gebruikt om de visuele elementen en het algehele ontwerp van uw thema te verbeteren.

## Een thema maken

AEM Forms 6.5 biedt de onderstaande thema&#39;s voor Core Components based Adaptive Forms.

* [ het thema van Canvas ](https://github.com/adobe/aem-forms-theme-canvas)
* [ WKND thema ](https://github.com/adobe/aem-forms-theme-wknd)
* [ EASEL thema ](https://github.com/adobe/aem-forms-theme-easel)
* [ Openbaar thema ](https://github.com/adobe/aem-forms-theme-public)
* [ het thema van de Productie ](https://github.com/adobe/aem-forms-theme-manufacturing)

U kunt [ om het even welk van deze thema&#39;s aanpassen om een thema ](#customize-a-theme-core-components) tot stand te brengen.

## Een thema aanpassen {#customize-a-theme-core-components-based-adaptive-forms}

Wanneer u een thema aanpast, wordt hiermee verwezen naar het wijzigen en aanpassen van de weergave van een thema. Wanneer u een thema aanpast, wijzigt u de ontwerpelementen, lay-out, kleuren, typografie en soms de onderliggende code. Zo kunt u een unieke en op maat gemaakte vormgeving voor uw website of toepassing maken met behoud van de basisstructuur en -functionaliteit die door het thema worden geboden.

>[!NOTE]
>
> * Gebruik de Manager van het Pakket om een thema op alle instanties van de Auteur en van Publish op te stellen.
> * Net als elk ander pakket wordt via Package Manager een themacliotheek geïmporteerd of geëxporteerd.

### Vereisten om een thema aan te passen {#prerequisites}

* [ laat de Aangepaste Componenten van de Kern van Forms ](/help/forms/using/enable-adaptive-forms-core-components.md) voor uw milieu toe.

* Installeer de recentste versie van [ Apache Maven.](https://maven.apache.org/download.cgi) Apache Maven is een tool voor automatisering van build dat veel wordt gebruikt voor Java™-projecten. De installatie van de recentste versie verzekert u de noodzakelijke gebiedsdelen voor themaaanpassing.

* Leer hoe te om a [ cliëntbibliotheek in Adobe Experience Manager ](https://experienceleague.adobe.com/docs/experience-manager-65/developing/introduction/clientlibs.html?lang=nl-NL) tot stand te brengen. AEM biedt clientbibliotheken, waarmee u uw code aan de clientzijde in de opslagplaats kunt opslaan, in categorieën kunt indelen en kunt bepalen wanneer en hoe elke categorie code aan de client moet worden aangeboden.

* Installeer een teksteditor zonder opmaak. Bijvoorbeeld Microsoft® Visual Studio Code. Het gebruiken van een gewone tekstredacteur zoals de Code van Microsoft® Visual Studio verstrekt een gebruikersvriendelijk milieu voor het uitgeven en het wijzigen van themadossiers.

* Zorg ervoor dat de AEM Forms-omgeving in gebruik is.

### Overwegingen om een thema aan te passen {#consideration}

* Zorg ervoor dat u [ het project gebruikt Archetype om de Aangepaste Componenten van de Kern van Forms ](/help/forms/using/enable-adaptive-forms-core-components.md) op uw milieu toe te laten om uw thema&#39;s aan te passen.

* Wanneer u een adaptief formulier publiceert, worden de clientbibliotheken niet automatisch gepubliceerd in de Publish-instantie. Zorg ervoor dat u de clientbibliotheek waarnaar wordt verwezen in een adaptief formulier, handmatig publiceert naar uw Publish-omgeving.

* Adobe raadt aan de klassenamen van clientbibliotheken niet te wijzigen.

### Een thema aanpassen {#customize-a-theme-core-components}

Het maken of aanpassen van een thema is een proces met meerdere stappen. Voer de stappen in de lijst uit om het thema te maken/aan te passen:

1. [Een thema klonen](#clone-git-repo-of-theme)
1. [ pas de verschijning van het thema ](#customize-the-theme) aan
1. [ Klaar het thema voor lokale plaatsing ](#generate-the-clientlib)
1. [ stel het thema op een lokaal milieu ](#deploy-the-theme-on-a-local-environment) op
1. [Het thema inzetten in de productieomgeving](#5-deploy-a-theme-on-your-production-environment)

<!--
 ![Theme Customization workflow](/help/forms/using/assets/custom-theme-steps.png)
-->

De voorbeelden die in het document worden verstrekt zijn gebaseerd op het **&#x200B;**&#x200B;thema van het Canvas, maar u kunt om het even welk thema klonen en het aanpassen gebruikend de zelfde instructies. Deze instructies zijn van toepassing op elk thema, zodat u thema&#39;s kunt aanpassen aan uw specifieke behoeften.

#### 1. Kloont de Git-gegevensopslagruimte van het thema {#clone-git-repo-of-theme}

Kies een van de volgende thema&#39;s om een thema voor op Core Components gebaseerde Adaptieve Forms te klonen:

* [ het thema van Canvas ](https://github.com/adobe/aem-forms-theme-canvas)
* [ WKND thema ](https://github.com/adobe/aem-forms-theme-wknd)
* [ EASEL thema ](https://github.com/adobe/aem-forms-theme-easel)

Voer de volgende instructies uit om een thema te klonen:

1. Open de opdrachtprompt of het terminalvenster in uw lokale ontwikkelomgeving.

1. Voer de opdracht `git clone` uit om een thema te klonen.

   ```
      git clone [Path of Git Repository of the theme]
   ```

   Vervang het [ Weg van de Bewaarplaats van het Git van het thema ] met daadwerkelijke URL van de overeenkomstige Bewaarplaats van het Git van het thema

   Als u bijvoorbeeld het thema Canvas wilt klonen, voert u de volgende opdracht uit:

   ```
      git clone https://github.com/adobe/aem-forms-theme-canvas
   ```

1. Selecteer **Vertrouwen de auteurs van alle dossiers in de ouderomslag** en klik **ja, ik vertrouw de auteurs**.

Nadat de opdracht is uitgevoerd, beschikt u over een lokale kopie van het thema op uw computer in de map `aem-forms-theme-canvas` .

#### 2. Het thema aanpassen {#customize-the-theme}

U hebt de flexibiliteit om individuele componenten aan te passen of thema-vlakke veranderingen aan te brengen gebruikend de globale variabelen van een thema. Het wijzigen van algemene variabelen heeft een trapsgewijs effect op alle afzonderlijke componenten. U kunt bijvoorbeeld algemene variabelen gebruiken om de randkleur van alle componenten in een adaptief formulier te wijzigen of een levendige vulkleur toe te passen op de knop Oproepen naar handeling (CTA). U kunt:

* [Stijlen voor themaniveau instellen](#theme-customization-global-level)

* [Stijlen op componentniveau instellen](#component-based-customization)

##### Stijlen voor themaniveau instellen {#theme-customization-global-level}

Het bestand `variable.scss` bevat de algemene variabelen van het thema. Door deze variabelen bij te werken, kunt u op themaniveau op stijl betrekking hebbende veranderingen aanbrengen. Voer de volgende stappen uit om stijlen op themaniveau toe te passen:

1. Open het `<your-theme-sources>/src/site/_variables.scss` -bestand om het te bewerken.
1. Wijzig de waarde van een willekeurige eigenschap. De standaardfoutkleur is bijvoorbeeld rood. Om de foutenkleur van rood in blauw te veranderen, verander de code van de kleurenhexuitdraai van de `$error` variabele. Bijvoorbeeld `$error: #196ee5` .

   ![ Voorbeeld: De kleur van de fout die aan blauw wordt geplaatst ](/help/forms/using/assets/theme-level-changes.png)

1. Sla het bestand op en sluit het.


Op dezelfde manier kunt u het bestand `variable.scss` gebruiken om lettertypefamilie en -type, thema- en lettertypekleuren, lettergrootte, themaspatiëring, foutpictogram, themarand en meer variabele in te stellen die van invloed zijn op meerdere componenten van het adaptieve formulier.

##### Stijlen op componentniveau instellen {#component-based-customization}

U kunt ook het lettertype, de kleur, de grootte en andere CSS-eigenschappen aanpassen van specifieke kerncomponenten van Adaptief formulier, zoals knoppen, selectievakjes, containers, voetteksten en nog veel meer. Door het CSS-bestand te bewerken dat aan de specifieke component is gekoppeld, kunt u de stijl ervan uitlijnen met de branding van uw organisatie. Ga als volgt te werk om de stijl van een component aan te passen:

1. Open het bestand `<your-theme-sources>/src/components/<component>/<component.scss>` voor bewerking. Als u bijvoorbeeld de lettertypekleur van de knopcomponent wilt wijzigen, opent u het bestand `<your-theme-sources>/src/components/button/button.scss` .
1. Wijzig desgewenst de waarde van een object. Als u bijvoorbeeld de kleur van de knopcomponent bij de muisaanwijzer wilt wijzigen in Groen, wijzigt u de waarde van de eigenschap `color: $white` in de klasse `cmp-adaptiveform-button__widget:hover` in hexadecimale code #12b453 of een andere groene tint. De uiteindelijke code ziet er als volgt uit:

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

>[!NOTE]
>
> Wanneer een stijl zowel op thema als componentenniveau wordt bepaald, krijgt de stijl die op het componentenniveau wordt bepaald prioriteit.

#### 3. Bereid het thema voor plaatsing {#generate-the-clientlib}

Om een thema in een AEM instantie op te stellen, moet het in een Bibliotheek van de Cliënt worden omgezet. Ga als volgt te werk om het thema om te zetten in een clientbibliotheek:

1. Open de opdrachtprompt of het terminalvenster.
1. Navigeer naar de map `<your-theme-sources>` . Bijvoorbeeld: `C:\aem-forms-theme-canvas`
1. Voer de volgende opdracht uit:

   ```
      npm run create-clientlib --category=adaptiveform.theme.[yourtheme]
   ```

   Vervang `[yourtheme]` door de naam van het aangepaste thema. Als het aangepaste thema bijvoorbeeld `customcanvastheme` heet, voert u de volgende opdracht uit

   ```
       npm run create-clientlib --category=adaptiveform.theme.customcanvastheme
   ```

   Wanneer de opdracht met succes is uitgevoerd, wordt een clientbibliotheekmap gemaakt op `themerepo\theme-clientlibs\[yourtheme]` .

   ![ De Generatie van de Bibliotheek van de Cliënt ](/help/forms/using/assets/clientlib_created.png)


   ![ plaats van de Bibliotheek van de Cliënt ](/help/forms/using/assets/adaptiveform.theme.easel.png)

#### 4. Gebruik het thema in een lokale omgeving {#deploy-the-theme-on-a-local-environment}

Voer de volgende stappen uit om het thema in te zetten in uw lokale ontwikkelings- of testomgeving:

1. Kopieer de clientbibliotheek die u in de vorige sectie hebt gemaakt naar het project Archetype op het volgende pad:

   `/ui.apps/src/main/content/jcr_root/apps/[AEM Archetype Project Folder]/clientlibs/<yourtheme>`

1. Open de Herinnering van het Bevel of Terminal.
1. Navigeer aan de wortelfolder van uw project van Archetype van de AEM, het project dat wordt gebruikt om de Aangepaste Componenten van de Kern van de Vorm toe te laten.
1. Voer de volgende opdracht uit om het aangepaste thema in uw omgeving in te stellen:

   `mvn clean install`

   ![ Bibliotheek van de Cliënt bouwt ](/help/forms/using/assets/mvndeploy.png)

<!--

#### 5. Test the theme with a local Adaptive Form {#test-the-theme-with-a-local-adaptive-form}

To apply and test the customized theme with an Adaptive Form:

**Apply theme while creating an Adaptive Form**

1. Log in to your AEM Forms author instance. 

1. Select **Adobe Experience Manager** > **Forms** > **Forms & Documents**.

1. Click **Create** > **Adaptive Forms**. The wizard for creating Adaptive Form opens.

1. Select the core component template in the **Source** tab.
1. Select the theme in the **Style** tab.
1. Click **Create**.

An Adaptive Form with the selected theme is created. 

**Apply theme to an existing Adaptive Form**

1. Log in to your AEM Forms author instance. 

1. Select **Adobe Experience Manager** > **Forms** > **Forms & Documents**.

1. Select an Adaptive Form and click Properties. 

1. For the **Theme Client Library** option, select the theme. 

1. Click **Save & Close**.

The selected theme is applied to the Adaptive Form. 
-->

#### 5. Een thema distribueren in uw productieomgeving {#deploy-theme}

Nadat u het thema hebt getest in uw lokale ontwikkelomgeving, kunt u doorgaan met de implementatie van het thema in uw productieomgeving, inclusief de instanties van Auteur en Publish. Voer de volgende stappen uit om het thema in uw productieomgevingen te implementeren:

1. Meld u aan bij uw AEM.
1. Open Pakketbeheer. De standaard-URL is `https://localhost:4502/crx/packmgr/index.jsp` .
1. Klik **uploaden Pakket** en klik **doorbladeren**.
1. Navigeer naar en selecteer `[AEM Archetype Project Folder]\all\target[appid].all-[version].zip` . Klik **Open**.
1. Klik op Installeren. Herhaal deze stap in alle productieomgevingen.


Nadat het pakket is geïnstalleerd, is het thema beschikbaar voor selectie.

![ de Bibliotheek van de Cliënt van het Thema ](/help/forms/using/assets/themeclientlibrary.png)

>[!NOTE]
>
>
> Als u problemen ondervindt bij het openen van het aanmeldingsvenster op een publicatieexemplaar om het pakket te installeren via Package Manager, kunt u zich aanmelden via de volgende URL: `http://[Publish Server URL]:[PORT]/system/console` . Hierdoor hebt u toegang tot aanmelding bij een Publish-instantie, zodat u verder kunt gaan met het installatieproces.

## Een thema toepassen op een adaptief formulier {#using-theme-in-adaptive-form}

De stappen voor het toepassen van een thema op een adaptief formulier zijn:

1. Meld u aan bij de lokale AEM auteur.
1. Ga uw geloofsbrieven op de Experience Manager login pagina in. Selecteer **Adobe Experience Manager** > **Forms** > **Forms &amp; Documenten**.
1. Klik **creëren** > **Aanpassings Forms**.
1. Selecteer een Adaptief malplaatje van de Componenten van de Kern van Forms en klik **daarna**. **voegt Eigenschappen** toe verschijnt
1. Specificeer de **Naam** voor uw AanpassingsVorm.


   >[!NOTE]
   >
   > * Standaard is het thema `adaptiveform.theme.canvas3` geselecteerd.
   > * U kunt een verschillend thema van het **drop-down menu van de Bibliotheek van de Cliënt van het Thema** kiezen.

1. Klik **creëren**.

De thema&#39;s Adaptief formulier worden gebruikt als onderdeel van een adaptieve formuliersjabloon om opmaak te definiëren terwijl u een adaptief formulier maakt.

## Een thema verwijderen {#delete-a-theme}

Ongebruikte of ongewenste thema&#39;s verwijderen:

1. Meld u aan bij de instantie Auteur.
1. Openen `http://[Publish Server URL]:[PORT]/crx/de/index.jsp`
1. Navigeer naar `apps/[AEM Archetype Project Folder]/clientlibs/[yourtheme]` .
1. Verwijder de themamap en sla de wijzigingen op.


## Veelgestelde vraag {#faq}

**Q:** Welke aanpassing neemt prioriteit wanneer het maken van aanpassingen in een themamap op zowel het globale niveau als componentenniveau?

**Ans:** wanneer een stijl op zowel het thema als componentenniveaus wordt bepaald, neemt de stijl die op het componentenniveau wordt bepaald belangrijkheid.

**Q:** Welke stappen zouden moeten worden genomen als het douanethema niet zichtbaar in **[!UICONTROL Theme Client Library]** is?

**Ans:** als uw douanethema niet in **[!UICONTROL Theme Client Library]** drop-down verschijnt, volg deze stappen:

1. Navigeer naar de locatie waar u de aangepaste thematclient-bibliotheek hebt toegevoegd. Het aanbevolen pad is `/ui.apps/src/main/content/jcr_root/apps[AEM Archetype Project Folder]/clientlibs/<yourtheme>` .

1. Open het `.content.xml` -bestand en neem de volgende metagegevens op:

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
* [ de themasjablonen van de Steekproef en modellen van vormgegevens ](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/sample-themes-templates-form-data-models-core-components.html?lang=nl-NL)
