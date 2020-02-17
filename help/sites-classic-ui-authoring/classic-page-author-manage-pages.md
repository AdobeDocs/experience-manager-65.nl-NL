---
title: Pagina's maken en ordenen
seo-title: Pagina's maken en ordenen
description: In deze sectie wordt beschreven hoe u pagina's kunt maken en beheren met AEM, zodat u vervolgens inhoud op die pagina's kunt maken.
seo-description: In deze sectie wordt beschreven hoe u pagina's kunt maken en beheren met AEM, zodat u vervolgens inhoud op die pagina's kunt maken.
uuid: 47ce137a-7a85-4b79-b4e0-fdf08a9e77bd
contentOwner: Chris Bohnert
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: page-authoring
content-type: reference
discoiquuid: 14b8758b-f164-429a-b299-33b0703f8bec
translation-type: tm+mt
source-git-commit: a3c303d4e3a85e1b2e794bec2006c335056309fb

---


# Pagina&#39;s maken en ordenen{#creating-and-organizing-pages}

In deze sectie wordt beschreven hoe u pagina&#39;s kunt maken en beheren met Adobe Experience Manager (AEM), zodat u vervolgens inhoud [op die pagina&#39;s kunt](/help/sites-classic-ui-authoring/classic-page-author-edit-content.md) maken.

>[!NOTE]
>
>Uw account heeft de [juiste toegangsrechten](/help/sites-administering/security.md) en [machtigingen](/help/sites-administering/security.md#permissions) nodig om actie te ondernemen op pagina&#39;s, bijvoorbeeld, maken, kopiëren, verplaatsen, bewerken, verwijderen.
>
>Als u om het even welke problemen ontmoet wij adviseren u uw systeembeheerder contacteert.

## Uw website ordenen {#organizing-your-website}

Als auteur moet u uw website organiseren binnen AEM. Dit betekent dat u inhoudspagina&#39;s maakt en een naam geeft, zodat:

* u kunt ze gemakkelijk vinden in de ontwerpomgeving
* bezoekers van uw site kunnen deze gemakkelijk in de publicatieomgeving bekijken

U kunt ook [mappen](#creating-a-new-folder) gebruiken om uw inhoud te ordenen.

De structuur van een website kan worden beschouwd als een *boomstructuur* die uw inhoudspagina&#39;s bevat. De namen van deze inhoudspagina&#39;s worden gebruikt om URLs te vormen, terwijl de titel wordt getoond wanneer de paginainhoud wordt bekeken.

Hieronder ziet u een extract van de Geometrixx-locatie; waar bijvoorbeeld de `Triangle` pagina wordt geopend:

* Auteursomgeving

   `http://localhost:4502/cf#/content/geometrixx/en/products/triangle.html`

* Publicatie-omgeving

   `http://localhost:4503/content/geometrixx/en/products/triangle.html`

   Afhankelijk van de configuratie van uw instantie, `/content` zou het gebruik van facultatief op het publiceren milieu kunnen zijn.

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

Deze structuur kan van de console van Websites worden bekeken, die u kunt gebruiken om door de boomstructuur [te](/help/sites-classic-ui-authoring/author-env-basic-handling.md#main-pars-text-15)navigeren.

![chlimage_1-151](assets/chlimage_1-151.png)

### Naamgevingsconventies voor pagina&#39;s {#page-naming-conventions}

Bij het maken van een nieuwe pagina zijn er twee sleutelvelden:

* **[Titel](#title)**:

   * Dit wordt aan de gebruiker getoond in de console en bij het uitgeven bij de bovenkant van de paginainhoud getoond.
   * Dit veld is verplicht.

* **[Naam](#name)**:

   * Hiermee wordt de URI gegenereerd.
   * Gebruikersinvoer voor dit veld is optioneel. Indien niet opgegeven, wordt de naam afgeleid van de titel.

Bij het maken van een nieuwe pagina [valideert AEM de paginanaam volgens de conventies](/help/sites-developing/naming-conventions.md) die door AEM en JCR worden opgelegd.

De implementatie en de lijst met toegestane tekens verschillen enigszins afhankelijk van de gebruikersinterface (deze is uitgebreider voor de interface met aanraakbediening), maar het minimaal toegestane aantal is:

* &#39;a&#39; tot en met &#39;z&#39;
* &#39;A&#39; tot en met &#39;Z&#39;
* 0 tot en met 9
* _ (onderstrepingsteken)
* `-` (afbreekstreepje/minteken)

Gebruik alleen deze tekens als u er zeker van wilt zijn dat deze worden geaccepteerd/gebruikt (zie [de naamgevingsconventies](/help/sites-developing/naming-conventions.md)als u alle gegevens over alle toegestane tekens wilt zien).

#### Titel {#title}

Als u bij het maken van een nieuwe pagina alleen een paginatitel **opgeeft, leidt AEM de** paginanaam **af van deze tekenreeks en** valideert AEM de naam volgens de conventies [](/help/sites-developing/naming-conventions.md) die door AEM en JCR worden opgelegd. In beide UI&#39;s wordt een veld **Titel** met ongeldige tekens geaccepteerd, maar voor de afgeleide naam worden de ongeldige tekens vervangen. Bijvoorbeeld:

| Titel | Afgeleide naam |
|---|---|
| Schön | schoen.html |
| SC%&amp;&amp;ast;ç+ | sc—c-.html |

#### Naam {#name}

Als u bij het maken van een nieuwe pagina een **paginanaam** opgeeft, zal AEM de naam [valideren volgens de conventies](/help/sites-developing/naming-conventions.md) die door AEM en JCR zijn opgelegd.

In de klassieke gebruikersinterface **kunt u geen ongeldige tekens** invoeren in het veld **Naam** .

>[!NOTE]
>In de interface met aanraakbediening **kunt u geen ongeldige tekens** verzenden in het veld **Naam** . Wanneer AEM ongeldige tekens detecteert, wordt het veld gemarkeerd en wordt een verklarende melding weergegeven om aan te geven welke tekens moeten worden verwijderd/vervangen.

>[!NOTE]
>
>Gebruik geen tweelettercode zoals gedefinieerd door ISO-639-1, tenzij het een hoofdtaalcode is.
>
>See [Preparing Content for Translation](/help/sites-administering/tc-prep.md) for more information.

### Templates {#templates}

In AEM, specificeert een malplaatje een gespecialiseerd type van pagina. Een sjabloon wordt gebruikt als basis voor elke nieuwe pagina die wordt gemaakt.

De sjabloon definieert de structuur van een pagina. inclusief een miniatuurafbeelding en andere eigenschappen. U hebt bijvoorbeeld aparte sjablonen voor productpagina&#39;s, sitemaps en contactgegevens. Sjablonen bestaan uit [componenten](#components).

AEM wordt geleverd met verschillende sjablonen die u kunt vinden. De aangeboden sjablonen zijn afhankelijk van de afzonderlijke website en de informatie die moet worden verschaft (wanneer u de nieuwe pagina maakt) is afhankelijk van de gebruikte interface. De belangrijkste velden zijn:

* **Titel** De titel die op de resulterende webpagina wordt weergegeven.

* **Naam** die wordt gebruikt bij de naamgeving van de pagina.

* **Template** A lijst van malplaatjes beschikbaar voor gebruik wanneer het produceren van de nieuwe pagina.

### Componenten {#components}

Componenten zijn de elementen die door AEM worden geleverd, zodat u specifieke typen inhoud kunt toevoegen. AEM wordt geleverd met een reeks out-of-the-box componenten die uitgebreide functionaliteit bieden; deze omvatten :

* Tekst
* Afbeelding
* Presentatie
* Video
* veel meer

Nadat u een pagina hebt gemaakt en geopend, kunt u inhoud [toevoegen met behulp van de componenten](/help/sites-classic-ui-authoring/classic-page-author-edit-content.md#insertinganewparagraph)die beschikbaar zijn in het [zijpaneel](/help/sites-classic-ui-authoring/classic-page-author-env-tools.md#sidekick).

## Pagina&#39;s beheren {#managing-pages}

### Een nieuwe pagina maken {#creating-a-new-page}

Tenzij alle pagina&#39;s vooraf voor u zijn gemaakt, moet u een pagina maken voordat u inhoud kunt gaan maken:

1. Selecteer in de **websiteconsole** het niveau waarop u een nieuwe pagina wilt maken.

   In het volgende voorbeeld maakt u een pagina onder het niveau **Producten** - weergegeven in het linkervenster. In het rechterdeelvenster ziet u pagina&#39;s die al op het niveau onder **Producten** staan.

   ![screen_shot_2012-02-15at114413am](assets/screen_shot_2012-02-15at114413am.png)

1. **** In het dialoogvenster **Nieuw... (klik op de pijl naast** Nieuw...**) en selecteer** Nieuwe pagina... . Het venster Pagina **** maken wordt geopend.

   **** Klikken op **Nieuw... Deze zelf fungeert ook als een snelkoppeling naar de** nieuwe pagina... optie.

1. In het dialoogvenster Pagina **** maken kunt u:

   * Geef een **titel**; dit wordt aan de gebruiker getoond.
   * Geef een **naam** op; this wordt gebruikt om URI te genereren. Als deze niet wordt opgegeven, wordt de naam afgeleid van de titel.

      * Als u bij het maken van een nieuwe pagina een **paginanaam** opgeeft, zal AEM de naam [valideren volgens de conventies](/help/sites-developing/naming-conventions.md) die door AEM en JCR zijn ingesteld.
      * In de klassieke UI **kunt u geen ongeldige karakters** op het gebied van de **Naam** ingaan.
   * Klik op de sjabloon die u wilt gebruiken om de nieuwe pagina te maken.

      De template wordt gebruikt als basis voor de nieuwe pagina; bijvoorbeeld om de basislay-out van een inhoudspagina te bepalen.
   >[!NOTE]
   >
   >Zie conventies voor [paginanamen](#page-naming-conventions).

   De minimale informatie die nodig is om een nieuwe pagina te maken, is de **titel** en de vereiste sjabloon.

   ![screen_shot_2012-02-15at114845am](assets/screen_shot_2012-02-15at114845am.png)

   >[!NOTE]
   >
   >Als u Unicode-tekens in de URL&#39;s wilt gebruiken, stelt u de eigenschap Alias ( `sling:alias`) ([pagina-eigenschappen](/help/sites-classic-ui-authoring/classic-page-author-edit-page-properties.md)) in.

1. Klik op **Maken** om de pagina te maken. U keert aan de console van **Websites** terug waar u een ingang voor de nieuwe pagina kunt zien.

   De console verstrekt informatie over de pagina (bijvoorbeeld wanneer het laatst werd uitgegeven en door wie) die zonodig wordt bijgewerkt.

   >[!NOTE]
   >
   >U kunt ook een pagina maken wanneer u een bestaande pagina bewerkt. Als u **Onderliggende pagina maken **vanaf het tabblad **Pagina** van het zijpaneel gebruikt, wordt een nieuwe pagina direct onder de pagina gemaakt die wordt bewerkt.

### Een pagina openen voor bewerken {#opening-a-page-for-editing}

U kunt de pagina die u wilt [bewerken](/help/sites-classic-ui-authoring/classic-page-author-edit-content.md#editing-a-component-content-and-properties) op een van de volgende manieren openen:

* Vanuit de **websiteconsole** kunt u **dubbelklikken** op de pagina-ingang om deze te openen en te bewerken.

* Vanuit de **websiteconsole** kunt u met de **rechtermuisknop op het pagina-item klikken** (contextmenu) en vervolgens **Openen** in het menu kiezen.

* Nadat u een pagina hebt geopend, kunt u naar andere pagina&#39;s binnen de site navigeren (om deze te bewerken) door op hyperlinks te klikken.

### Pagina&#39;s kopiëren en plakken {#copying-and-pasting-a-page}

Tijdens het kopiëren kunt u een van de volgende twee documenten kopiëren:

* één pagina
* een pagina samen met alle subpagina&#39;s

1. Selecteer in de **websiteconsole** de pagina die u wilt kopiëren.

   >[!NOTE]
   >
   >In dit stadium is het irrelevant of u één pagina of de onderliggende subpagina&#39;s wilt kopiëren.

1. Klik op **Kopiëren**.

1. Navigeer naar de nieuwe locatie en klik op:

   * **Plakken** - om de pagina samen met alle subpagina&#39;s te plakken
   * **Shift + Plakken** - alleen de geselecteerde pagina plakken
   De pagina(&#39;s) worden op de nieuwe locatie geplakt.

   >[!NOTE]
   >
   >De paginanaam kan automatisch worden aangepast als een bestaande pagina al dezelfde naam heeft.

   >[!NOTE]
   >
   >U kunt ook Pagina **** kopiëren vanaf het tabblad **Pagina** van het hulpwerkgebied gebruiken. Hiermee wordt een dialoogvenster geopend waarin u het doel kunt opgeven, enzovoort.

### Pagina verplaatsen of hernoemen {#moving-or-renaming-page}

>[!NOTE]
>
>Als u de naam van een pagina wijzigt, gelden de naamgevingsconventies [voor de](#page-naming-conventions) pagina ook voor het opgeven van de nieuwe paginanaam.

De procedure voor het verplaatsen of hernoemen van een pagina is hetzelfde. Met dezelfde handeling kunt u:

* een pagina naar een nieuwe locatie verplaatsen
* de naam van een pagina op dezelfde locatie wijzigen
* een pagina naar een nieuwe locatie verplaatsen en tegelijkertijd de naam ervan wijzigen

Met AEM kunt u interne koppelingen bijwerken naar de pagina waarvan de naam wordt gewijzigd of die wordt verplaatst. Dit kan per pagina worden gedaan om volledige flexibiliteit te bieden.

Een pagina verplaatsen of de naam ervan wijzigen:

1. Er zijn verschillende methoden om een verplaatsing te activeren:

   * Klik in de **websiteconsole** om de pagina te selecteren en selecteer vervolgens **Verplaatsen...**
   * In de **websiteconsole** kunt u ook het pagina-item selecteren, vervolgens met de **rechtermuisknop klikken** en **Verplaatsen selecteren...**
   * Wanneer u een pagina bewerkt, kunt u Pagina **** verplaatsen selecteren op het tabblad **Pagina** van het hulpstuk.

1. Het venster **Verplaatsen** wordt geopend. Hier kunt u een nieuwe locatie, een nieuwe naam voor de pagina of beide opgeven.

   ![screen_shot_2012-02-15at121336pm](assets/screen_shot_2012-02-15at121336pm.png)

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

      Werk de koppelingen op de pagina bij die naar de verplaatste pagina verwijzen: Als pagina A bijvoorbeeld koppelingen naar pagina B bevat, past AEM de koppelingen op pagina A aan voor het geval u pagina B verplaatst.

      Dit kan voor elke afzonderlijke verwijzende pagina worden geselecteerd/worden geschrapt.

   * **Opnieuw publiceren**

      De verwijzende pagina opnieuw publiceren; ook dit kan voor elke afzonderlijke pagina worden geselecteerd.
   >[!NOTE]
   >
   >Als de pagina al is geactiveerd, wordt deze automatisch gedeactiveerd wanneer u de pagina verplaatst. De functie wordt standaard opnieuw geactiveerd wanneer de verplaatsing is voltooid, maar dit kan veranderen door het veld **Opnieuw** publiceren voor de pagina in het venster **Verplaatsen** uit te schakelen.

1. Klik op **Verplaatsen**. Bevestiging is vereist. Klik op **OK** om te bevestigen.

   >[!NOTE]
   >
   >De paginatitel wordt niet bijgewerkt.

### Een pagina verwijderen {#deleting-a-page}

1. U kunt een pagina van diverse plaatsen schrappen:

   * Klik in de **websiteconsole** om de pagina te selecteren, klik met de rechtermuisknop en selecteer **Verwijderen** in het resulterende menu.
   * Klik in de **websiteconsole** om de pagina te selecteren en selecteer vervolgens **Verwijderen** in het werkbalkmenu.
   * Kies in de assistent het tabblad **Pagina** om Pagina **** verwijderen te selecteren. Hiermee verwijdert u de pagina die momenteel is geopend.

1. Nadat u hebt geselecteerd om een pagina te verwijderen, moet u de aanvraag bevestigen - aangezien de actie niet ongedaan kan worden gemaakt.

   >[!NOTE]
   >
   >Als de pagina na verwijdering is gepubliceerd, kunt u de nieuwste (of een specifieke) versie herstellen, maar deze heeft mogelijk niet precies dezelfde inhoud als de laatste versie als er verdere wijzigingen zijn aangebracht. Zie [Pagina](/help/sites-classic-ui-authoring/classic-page-author-work-with-versions.md#restoringpages) &#39;sherstellen voor meer informatie.

>[!NOTE]
>
>Als een pagina al is geactiveerd, wordt deze automatisch gedeactiveerd voordat de pagina wordt verwijderd.

### Een pagina vergrendelen {#locking-a-page}

U kunt een pagina [](/help/sites-classic-ui-authoring/classic-page-author-edit-content.md#locking-a-page) vergrendelen/ontgrendelen vanuit een console of wanneer u een afzonderlijke pagina bewerkt. Informatie over het feit of een pagina is vergrendeld, wordt ook op beide locaties weergegeven.

### Nieuwe map maken {#creating-a-new-folder}

>[!NOTE]
>
>Mappen zijn ook onderworpen aan de conventies voor [paginanamen](#page-naming-conventions) wanneer u de nieuwe mapnaam opgeeft.

1. Open de **websiteconsole** en navigeer naar de gewenste locatie.
1. **** In het dialoogvenster **Nieuw... (klik op de pijl naast** Nieuw...**) en selecteer** Nieuwe map... .
1. Het dialoogvenster Map **** maken wordt geopend. Hier kunt u de **naam** en de **titel** invoeren:

   ![chlimage_1-152](assets/chlimage_1-152.png)

1. Selecteer **Maken** om de map te maken.

