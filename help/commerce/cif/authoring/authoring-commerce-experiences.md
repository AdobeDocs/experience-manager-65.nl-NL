---
title: Commerce Ervaringen ontwerpen
description: De CIF add-on breidt Adobe Experience Manager-authoring uit met specifieke handelsmogelijkheden.
exl-id: 2db51bd7-8fc7-4ae8-8d6f-e5035fbe954d
solution: Experience Manager,Commerce
feature: Commerce Integration Framework
role: Admin, Developer
source-git-commit: 10268f617b8a1bb22f1f131cfd88236e7d5beb47
workflow-type: tm+mt
source-wordcount: '713'
ht-degree: 0%

---

# Commerce Ervaringen ontwerpen {#authoring-commerce-experiences}

## Overzicht {#overview}

De CIF toe:voegen-on breidt AEM het schrijven met handel-specifieke mogelijkheden uit. Dit laat auteurs toe om handel-verwante ervaringen efficiënt te bouwen en te beheren door toegang tot productgegevens en inhoud te krijgen zonder de context te verlaten.

## Kaarten {#pickers}

Producten en categoriekiezers zijn modale UI-dialoogvensters die AEM auteurs een comfortabele manier bieden om producten of categorieën te zoeken en te selecteren wanneer dat nodig is. De Componenten van de kern, inhoudskoppeling en productmalplaatjes zijn de typische gebieden met configuraties die productcatalogusgegevens vereisen. Kiezers ondersteunen diverse configuratieopties, zoals meerkeuzevragen, variatie-selectie en voorselectie van waarden.

### Productkiezer {#product-picker}

Deze kiezer kan bladeren door de catalogusstructuur of zoeken in volledige tekst om het product te zoeken. Producten met variatie bieden een mappictogram in de kolom &#39;Type&#39;. Als u op het mappictogram klikt, worden de variaties van het geselecteerde product geopend.

![ de plukker van het Product ](/help/commerce/cif/assets/authoring/product-picker.png)

Als u op de bovenliggende categorie klikt, gaat de auteur terug naar het productniveau.

![ de plukker van het Product ](/help/commerce/cif/assets/authoring/product-picker-variation.png)

**het productmeetapparaat van het Voorbeeld**

![ component van de Taser zonder selectie ](/help/commerce/cif/assets/authoring/teaser_component_without_selection.png)

Het configuratiedialoogvenster van deze component vereist een product. CIF gebruikt SKU als product-id. Auteurs kunnen de skin handmatig invoeren of op het mappictogram klikken om de productkiezer te openen. Nadat u de kiezer hebt geselecteerd en gesloten, wordt in het dialoogvenster met componenten de naam van het geselecteerde product weergegeven

![ component van de Taser met selectie ](/help/commerce/cif/assets/authoring/teaser_component_with_selection.png)

### Categoriekiezer {#category-picker}

Deze kiezer kan bladeren door de catalogusstructuur om de categorie te zoeken.

![ de plukker van de Categorie ](/help/commerce/cif/assets/authoring/category-picker.png)

**de categorie carrousel van het Voorbeeld**

![ component Carousel zonder selectie ](/help/commerce/cif/assets/authoring/carousel_component_without_selection.png)

Het configuratiedialoogvenster van deze component vereist 1 : n-categorieën. CIF gebruikt de UID /-id als de categorie-id. Auteurs kunnen de id handmatig invoeren of op het mappictogram klikken om de categoriekiezer te openen. Nadat u de kiezer hebt geselecteerd en gesloten, wordt in het dialoogvenster dat de component bevat de naam van de geselecteerde categorie weergegeven.

![ component Carousel met selectie ](/help/commerce/cif/assets/authoring/carousel_component_with_selection.png)

## Universele editor {#universal-editor}

De Universele Redacteur wordt uitgebreid met mogelijkheden om tot de productgegevens in real time en bijbehorende productinhoud toegang te hebben.

### Toegang tot productgegevens {#access-product-data}

Het tabblad &#39;Assets&#39; in het zijpaneel van de editor biedt toegang tot productgegevens door het type &#39;Producten&#39; te selecteren. De gegevens worden opgehaald levend van het gevormde handelseindpunt. Het filter is een full-text onderzoek op het handelseindpunt om specifieke producten te vinden.

![ het gegevenszijpaneel van het Product ](/help/commerce/cif/assets/authoring/products-side-panel.png)

Analoog aan activa, kunnen de producten op een pagina worden toegevoegd (die tot een product teaser component als gebrek) of componenten (momenteel gesteund zijn productschouder en productcarrousel) leidt.

### Koppelingen toevoegen in tekstvelden met RTE {#rte}

CIF productcataloguspagina&#39;s zijn virtuele pagina&#39;s die direct worden weergegeven. Het is dus niet mogelijk hyperlinks in te sluiten, zoals bij gewone AEM pagina&#39;s. CIF voegt een nieuwe actie &quot;de Verbindingen van Commerce&quot;aan RTE (Rich Text Editor) toe. Deze actie werkt precies zoals de gewone &quot;Hyperlink&quot;actie, maar staat auteurs toe om of een product of een categorie te selecteren gebruikend de plukkers.

![ RTE ](/help/commerce/cif/assets/authoring/RTE.png)

    >[!NOTA] 
    > 
    >Als zowel de categorie als het product wordt geselecteerd, zal het product worden genomen.

Hierdoor wordt een koppeling voor plaatsaanduidingen gemaakt die wordt vervangen door een echte koppeling wanneer de pagina wordt weergegeven.

### Gekoppelde productinhoud openen {#associated-content}

Als de Universal Editor 1:n-producten op een pagina herkent, wordt in het zijpaneel automatisch het tabblad &quot;Gekoppelde Commerce-inhoud&quot; weergegeven. Dit lusje staat auteurs toe om tot AEM inhoud snel toegang te hebben die met het product werd geëtiketteerd (zie [ productgegevens met bijbehorende AEM inhoud ](./enrich-product-associated-content.md) voor meer informatie verrijken). Op dit tabblad kunt u vervolgkeuzelijsten gebruiken om te filteren op inhoudstype en specifieke producten als er meerdere producten op de pagina staan. Het gebruik van de inhoud werkt precies hetzelfde als het gebruik van inhoud op het tabblad &quot;Assets&quot;.

![ het gegevenszijpaneel van het Product ](/help/commerce/cif/assets/authoring/associated-commerce-content-tab.png)

### Voorvertoning nog niet verwerkte productgegevens {#staged-data}

In de modus Tijdlijn verdraaien in de editor kunnen auteurs een voorvertoning weergeven van en bladeren door een AEM ervaring met gegevens uit de gefaseerde productcatalogus op basis van de datum Tijdlijn verdraaien.

![ Timewarp ](/help/commerce/cif/assets/authoring/timewarp.png)

Componenten geven een visuele indicator weer als de gebruikte datum gefaseerd is.

![ Gesprekte indicator ](/help/commerce/cif/assets/authoring/staged-indicator.png)

## Omnissearch {#omnisearch}

Het gebruik van Omnissearch is een gemakkelijke manier voor artsen om AEM inhoud en productcatalogusgegevens te zoeken aan de hand van full-text zoekopdrachten. In het kader van Omnissearch worden full-text zoekopdrachten uitgevoerd in AEM en de commerceback om de productcatalogusobjecten te zoeken in de commerceback en AEM inhoud. AEM resultaten hebben ook betrekking op inhoud die is gelabeld met product-/categoriegegevens.

![ Omnissearch ](/help/commerce/cif/assets/authoring/omnisearch.png)

Het resultaat wordt gegroepeerd op type.

    >[!NOTE] 
    > 
    >Het full-text onderzoek in Onderzoek steunt geen bijbehorende Fragments van de Inhoud. SKU of UID van het gebruik om bijbehorende Fragments van de Inhoud te vinden.
