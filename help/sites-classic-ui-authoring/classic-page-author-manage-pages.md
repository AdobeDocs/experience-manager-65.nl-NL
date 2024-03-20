---
title: Pagina's maken en ordenen
description: In deze sectie wordt beschreven hoe u pagina's met AEM kunt maken en beheren, zodat u vervolgens inhoud op die pagina's kunt maken.
contentOwner: Chris Bohnert
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: page-authoring
content-type: reference
exl-id: bd2636d1-6f13-4c6c-b8cd-3bed9e83a101
solution: Experience Manager, Experience Manager Sites
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '1895'
ht-degree: 0%

---

# Pagina&#39;s maken en ordenen{#creating-and-organizing-pages}

In deze sectie wordt beschreven hoe u pagina&#39;s kunt maken en beheren met Adobe Experience Manager (AEM), zodat u vervolgens [inhoud maken](/help/sites-classic-ui-authoring/classic-page-author-edit-content.md) op die pagina&#39;s.

>[!NOTE]
>
>Uw account heeft de [passende toegangsrechten](/help/sites-administering/security.md) en [machtigingen](/help/sites-administering/security.md#permissions) handelingen uit te voeren op pagina&#39;s, bijvoorbeeld maken, kopiëren, verplaatsen, bewerken, verwijderen.
>
>Als u om het even welke problemen ontmoet wij adviseren u uw systeembeheerder contacteert.

## Uw website ordenen {#organizing-your-website}

Als auteur moet u uw website binnen AEM organiseren. Dit betekent dat u inhoudspagina&#39;s maakt en een naam geeft, zodat:

* u kunt ze gemakkelijk vinden in de ontwerpomgeving
* bezoekers van uw site kunnen deze gemakkelijk in de publicatieomgeving bekijken

U kunt ook [mappen](#creating-a-new-folder) om uw inhoud beter in te delen.

De structuur van een website kan als een *boomstructuur* die uw inhoudspagina&#39;s bevat. De namen van deze inhoudspagina&#39;s worden gebruikt om URLs te vormen, terwijl de titel wordt getoond wanneer de paginainhoud wordt bekeken.

In het volgende voorbeeld wordt een extract getoond van de locatie Geometrixx, waarbij bijvoorbeeld de `Triangle` pagina wordt geopend:

* Auteursomgeving

  `http://localhost:4502/cf#/content/geometrixx/en/products/triangle.html`

* Publicatie-omgeving

  `http://localhost:4503/content/geometrixx/en/products/triangle.html`

  Afhankelijk van de configuratie van uw instantie, gebruik van `/content` kan optioneel zijn in de publicatieomgeving.

```xml
  /content
    /geometrixx
      /en
        /toolbar...
        /products
          /triangle
            /overview
            /features
          /square...
          /circle...
          /...
        /...
      /fr...
      /de...
      /es...
      /...
    /...
```

Deze structuur kan van de console van Websites worden bekeken, die u kunt gebruiken aan [navigeren door de boomstructuur](/help/sites-classic-ui-authoring/author-env-basic-handling.md#main-pars-text-15).

![chlimage_1-151](assets/chlimage_1-151.png)

### Naamgevingsconventies voor pagina {#page-naming-conventions}

Bij het maken van een pagina zijn er twee sleutelvelden:

* **[Titel](#title)**:

   * Dit wordt aan de gebruiker getoond in de console en bij het uitgeven bij de bovenkant van de paginainhoud getoond.
   * Dit veld is verplicht.

* **[Naam](#name)**:

   * Hiermee wordt de URI gegenereerd.
   * Gebruikersinvoer voor dit veld is optioneel. Indien niet opgegeven, wordt de naam afgeleid van de titel.

Wanneer u een pagina maakt, AEM [valideert de paginanaam volgens de conventies](/help/sites-developing/naming-conventions.md) opgelegd door AEM en JCR.

De implementatie en de lijst met toegestane tekens verschillen enigszins afhankelijk van de gebruikersinterface (deze is uitgebreider voor de interface met aanraakbediening), maar het minimaal toegestane aantal is:

* &#39;a&#39; tot en met &#39;z&#39;
* &#39;A&#39; tot en met &#39;Z&#39;
* 0 tot en met 9
* _ (onderstrepingsteken)
* `-` (afbreekstreepje/minteken)

Gebruik alleen deze tekens als u zeker wilt weten dat deze worden geaccepteerd/gebruikt (als u alle gegevens over alle toegestane tekens wilt raadplegen, raadpleegt u [naamconventies](/help/sites-developing/naming-conventions.md)).

#### Titel {#title}

Als u alleen een pagina opgeeft **Titel** wanneer u een pagina maakt, wordt AEM de pagina afgeleid **Naam** van deze tekenreeks en [De naam valideren volgens de conventies](/help/sites-developing/naming-conventions.md) opgelegd door AEM en JCR. In beide UI&#39;s **Titel** veld met ongeldige tekens wordt geaccepteerd, maar voor de afgeleide naam worden de ongeldige tekens vervangen. Bijvoorbeeld:

| Titel | Afgeleide naam |
|---|---|
| Schön | schoen.html |
| SC%&amp;&amp;ast;ç+ | sc---c-.html |

#### Naam {#name}

Als u een pagina **Naam** bij het maken van een pagina, AEM [valideert de naam volgens de conventies](/help/sites-developing/naming-conventions.md) opgelegd door AEM en JCR.

In de klassieke gebruikersinterface **kan geen ongeldige tekens invoeren** in de **Naam** veld.

>[!NOTE]
>In de interface met aanraakbediening kunt u **kan geen ongeldige tekens verzenden** in de **Naam** veld. Wanneer AEM ongeldige tekens detecteert, wordt het veld gemarkeerd en wordt een verklarende melding weergegeven om aan te geven welke tekens moeten worden verwijderd/vervangen.

>[!NOTE]
>
>Gebruik geen tweelettercode zoals gedefinieerd in ISO-639-1, tenzij het een hoofdtaalcode is.
>
>Zie [Inhoud voorbereiden voor vertaling](/help/sites-administering/tc-prep.md) voor meer informatie .

### Sjablonen {#templates}

In AEM geeft een sjabloon een speciaal type pagina op. Een sjabloon wordt gebruikt als basis voor elke nieuwe pagina die wordt gemaakt.

De sjabloon definieert de structuur van een pagina, inclusief een miniatuurafbeelding en andere eigenschappen. U hebt bijvoorbeeld aparte sjablonen voor productpagina&#39;s, sitemaps en contactgegevens. Sjablonen bestaan uit [componenten](#components).

AEM wordt geleverd met verschillende sjablonen die buiten de box zijn geplaatst. De aangeboden sjablonen zijn afhankelijk van de afzonderlijke website en de informatie die moet worden verschaft (wanneer u de nieuwe pagina maakt) is afhankelijk van de gebruikte interface. De belangrijkste velden zijn:

* **Titel**
De titel die op de resulterende webpagina wordt weergegeven.

* **Naam**
Wordt gebruikt bij de naamgeving van de pagina.

* **Sjabloon**
Een lijst met sjablonen die u kunt gebruiken bij het genereren van de nieuwe pagina.

### Onderdelen {#components}

Componenten zijn de elementen die worden verschaft door AEM, zodat u specifieke typen inhoud kunt toevoegen. AEM wordt geleverd met een reeks kant-en-klare componenten die uitgebreide functionaliteit bieden, zoals:

* Tekst
* Afbeelding
* Presentatie
* Video
* veel meer

Als u eenmaal een pagina hebt gemaakt en geopend, kunt u [inhoud toevoegen met de componenten](/help/sites-classic-ui-authoring/classic-page-author-edit-content.md#insertinganewparagraph), beschikbaar op [sidekick](/help/sites-classic-ui-authoring/classic-page-author-env-tools.md#sidekick).

## Pagina&#39;s beheren {#managing-pages}

### Een nieuwe pagina maken {#creating-a-new-page}

Tenzij alle pagina&#39;s vooraf voor u zijn gemaakt, moet u een pagina maken voordat u inhoud kunt gaan maken:

1. Van de **Websites** selecteert u het niveau waarop u een pagina wilt maken.

   In het volgende voorbeeld maakt u een pagina onder het niveau **Producten** - weergegeven in het linkervenster; in het rechtervenster worden pagina&#39;s weergegeven die al op het niveau onder **Producten**.

   ![screen_shot_2012-02-15at114413am](assets/screen_shot_2012-02-15at114413am.png)

1. In de **Nieuw...** menu (klik op de pijl naast **Nieuw...**), selecteert u **Nieuwe pagina..**. De **Pagina maken** wordt geopend.

   Klikken **Nieuw...** zelf fungeert ook als een sneltoets voor de **Nieuwe pagina..** -optie.

1. De **Pagina maken** kunt u:

   * Geef een **Titel**; dit wordt weergegeven aan de gebruiker.
   * Geef een **Naam**; dit wordt gebruikt om de URI te genereren. Als deze niet wordt opgegeven, wordt de naam afgeleid van de titel.

      * Als u een pagina **Naam** bij het maken van een pagina, AEM [valideert de naam volgens de conventies](/help/sites-developing/naming-conventions.md) opgelegd door AEM en JCR.
      * In de klassieke gebruikersinterface **kan geen ongeldige tekens invoeren** in de **Naam** veld.

   * Klik op de sjabloon die u wilt gebruiken om de nieuwe pagina te maken.

     De sjabloon wordt gebruikt als basis voor de nieuwe pagina, bijvoorbeeld om de basislay-out van een inhoudspagina te bepalen.

   >[!NOTE]
   >
   >Zie [Naamgevingsconventies voor pagina](#page-naming-conventions).

   De minimale informatie die nodig is om een pagina te maken, is de **Titel** en de vereiste template.

   ![screen_shot_2012-02-15at114845am](assets/screen_shot_2012-02-15at114845am.png)

   >[!NOTE]
   >
   >Als u Unicode-tekens in de URL&#39;s wilt gebruiken, stelt u de alias in ( `sling:alias`), eigenschap ([pagina-eigenschappen](/help/sites-classic-ui-authoring/classic-page-author-edit-page-properties.md)).

1. Klikken **Maken** om de pagina te maken. U keert terug naar de **Websites** console waar u een ingang voor de nieuwe pagina kunt zien.

   De console verstrekt informatie over de pagina (bijvoorbeeld, toen het laatst werd uitgegeven en door wie) die zonodig wordt bijgewerkt.

   >[!NOTE]
   >
   >U kunt ook een pagina maken wanneer u een bestaande pagina bewerkt. Gebruiken **Onderliggende pagina maken** van de **Pagina** van het zijpaneel maakt een pagina direct onder de pagina die wordt bewerkt.

### Een pagina openen voor bewerken {#opening-a-page-for-editing}

U kunt de pagina openen die u wilt [bewerkt](/help/sites-classic-ui-authoring/classic-page-author-edit-content.md#editing-a-component-content-and-properties) op een van de volgende wijzen:

* Van **Websites** console, kunt u **dubbelklikken** het pagina-item dat moet worden geopend voor bewerking.

* Van **Websites** console, kunt u **rechtsklikken** (contextmenu) het pagina-item, selecteer vervolgens **Openen** in het menu.

* Nadat u een pagina hebt geopend, kunt u naar andere pagina&#39;s binnen de site navigeren (om deze te bewerken) door op hyperlinks te klikken.

### Pagina&#39;s kopiëren en plakken {#copying-and-pasting-a-page}

Tijdens het kopiëren kunt u een van de volgende twee documenten kopiëren:

* één pagina
* een pagina samen met alle subpagina&#39;s

1. Van de **Websites** de pagina die u wilt kopiëren.

   >[!NOTE]
   >
   >In dit stadium is het irrelevant of u één pagina of de onderliggende subpagina&#39;s wilt kopiëren.

1. Klikken **Kopiëren**.

1. Ga naar de nieuwe locatie en klik op:

   * **Plakken** - om de pagina samen met alle subpagina&#39;s te plakken
   * **Shift + Plakken** - alleen de geselecteerde pagina plakken

   De pagina&#39;s worden op de nieuwe locatie geplakt.

   >[!NOTE]
   >
   >De paginanaam kan automatisch worden aangepast als een bestaande pagina al dezelfde naam heeft.

   >[!NOTE]
   >
   >U kunt ook **Pagina kopiëren** van de **Pagina** tabblad van het hulpwerkje. Hiermee wordt een dialoogvenster geopend waarin u het doel kunt opgeven, enzovoort.

### Pagina verplaatsen of hernoemen {#moving-or-renaming-page}

>[!NOTE]
>
>De naam van een pagina wijzigen is ook afhankelijk van de instelling [Naamgevingsconventies voor pagina](#page-naming-conventions) wanneer u de nieuwe paginanaam opgeeft.

De procedure voor het verplaatsen of hernoemen van een pagina is hetzelfde. Met dezelfde handeling kunt u:

* een pagina naar een nieuwe locatie verplaatsen
* de naam van een pagina op dezelfde locatie wijzigen
* een pagina naar een nieuwe locatie verplaatsen en deze tegelijk een andere naam geven

AEM biedt u de functionaliteit om interne koppelingen bij te werken naar de pagina waarvan de naam wordt gewijzigd of die wordt verplaatst. Dit kan per pagina worden gedaan om volledige flexibiliteit te bieden.

Een pagina verplaatsen of hernoemen:

1. Er zijn verschillende methoden om een verplaatsing te activeren:

   * Van de **Websites** console, klik om de pagina te selecteren, dan selecteren **Verplaatsen...**
   * Van de **Websites** -console, kunt u ook het pagina-item selecteren en vervolgens **rechtsklikken** en selecteert u **Verplaatsen...**
   * Als u een pagina bewerkt, kunt u **Pagina verplaatsen** van de **Pagina** tabblad van het hulpwerkje.

1. De **Verplaatsen** wordt geopend. Hier kunt u een nieuwe locatie, een nieuwe naam voor de pagina of beide opgeven.

   ![screen_shot_2012-02-15at12133pm](assets/screen_shot_2012-02-15at121336pm.png)

   De pagina bevat ook pagina&#39;s die verwijzen naar de verplaatste pagina. Afhankelijk van de status van de pagina waarnaar wordt verwezen, kunt u deze koppelingen aanpassen op de pagina&#39;s en/of deze opnieuw publiceren.

1. Vul de volgende velden in, al naar het geval:

   * **Doel**

     Gebruik de sitemap (beschikbaar via de keuzelijst) om de locatie te selecteren waarnaar de pagina moet worden verplaatst.

     Als u alleen de naam van de pagina wijzigt, negeert u dit veld.

   * **Verplaatsen**

     Geef de pagina op die u wilt verplaatsen. Deze wordt gewoonlijk standaard ingevuld, afhankelijk van de manier waarop en de plaats waar u de verplaatsingsactie hebt gestart.

   * **Naam wijzigen in**

     Het huidige paginalabel wordt standaard weergegeven. Geef indien nodig het nieuwe paginalabel op.

   * **Aanpassen**

     Werk de koppelingen op de pagina bij die naar de verplaatste pagina verwijzen. Als pagina A bijvoorbeeld koppelingen naar pagina B bevat, past AEM de koppelingen op pagina A aan voor het geval u pagina B verplaatst.

     Dit kan voor elke afzonderlijke verwijzende pagina worden geselecteerd/worden geschrapt.

   * **Opnieuw publiceren**

     Herpubliceer de verwijzende pagina; opnieuw kan dit voor elke individuele pagina worden geselecteerd.

   >[!NOTE]
   >
   >Als de pagina al is geactiveerd, wordt deze automatisch gedeactiveerd wanneer u de pagina verplaatst. De functie wordt standaard opnieuw geactiveerd wanneer de bewerking is voltooid, maar dit kan veranderen door de optie **Opnieuw publiceren** veld voor de pagina in het dialoogvenster **Verplaatsen** venster.

1. Klikken **Verplaatsen**. Bevestiging is vereist. Klikken **OK** ter bevestiging.

   >[!NOTE]
   >
   >De paginatitel wordt niet bijgewerkt.

### Een pagina verwijderen {#deleting-a-page}

1. U kunt een pagina van diverse plaatsen schrappen:

   * Binnen de **Websites** -console, klikt u om de pagina te selecteren, klikt u met de rechtermuisknop en selecteert u **Verwijderen** in het resulterende menu.
   * Binnen de **Websites** console, klik om de pagina te selecteren, dan selecteren **Verwijderen** in het werkbalkmenu.
   * Gebruik in sidekick de **Pagina** te selecteren tab **Pagina verwijderen** - Hiermee verwijdert u de pagina die momenteel is geopend.

1. Nadat u hebt geselecteerd om een pagina te verwijderen, moet u de aanvraag bevestigen - aangezien de actie niet ongedaan kan worden gemaakt.

   >[!NOTE]
   >
   >Als de pagina na verwijdering is gepubliceerd, kunt u de nieuwste (of een specifieke) versie herstellen, maar deze heeft mogelijk niet precies dezelfde inhoud als de laatste versie als er verdere wijzigingen zijn aangebracht. Zie [Pagina&#39;s herstellen](/help/sites-classic-ui-authoring/classic-page-author-work-with-versions.md#restoringpages) voor nadere bijzonderheden.

>[!NOTE]
>
>Als een pagina al is geactiveerd, wordt deze automatisch gedeactiveerd voordat de pagina wordt verwijderd.

### Een pagina vergrendelen {#locking-a-page}

U kunt [Een pagina vergrendelen/ontgrendelen](/help/sites-classic-ui-authoring/classic-page-author-edit-content.md#locking-a-page) vanuit een console of wanneer u een afzonderlijke pagina bewerkt. Informatie over vergrendelde pagina&#39;s wordt ook op beide locaties weergegeven.

### Een nieuwe map maken {#creating-a-new-folder}

>[!NOTE]
>
>Mappen zijn ook onderworpen aan de [Naamgevingsconventies voor pagina](#page-naming-conventions) wanneer u de nieuwe mapnaam opgeeft.

1. Open de **Websites** en navigeer naar de gewenste locatie.
1. In de **Nieuw...** menu (klik op de pijl naast **Nieuw...**), selecteert u **Nieuwe map..**.
1. De **Map maken** wordt geopend. Hier kunt u de **Naam** en **Titel**:

   ![chlimage_1-152](assets/chlimage_1-152.png)

1. Selecteren **Maken** om de map te maken.
