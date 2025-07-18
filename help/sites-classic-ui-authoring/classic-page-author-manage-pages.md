---
title: Pagina's maken en ordenen
description: In deze sectie wordt beschreven hoe u pagina's kunt maken en beheren met AEM, zodat u vervolgens inhoud op die pagina's kunt maken.
contentOwner: Chris Bohnert
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: page-authoring
content-type: reference
exl-id: bd2636d1-6f13-4c6c-b8cd-3bed9e83a101
solution: Experience Manager, Experience Manager Sites
feature: Authoring
role: User
source-git-commit: 25bf0d64b6839afec0112ea8c9fde0510e56ccf4
workflow-type: tm+mt
source-wordcount: '1898'
ht-degree: 0%

---

# Pagina&#39;s maken en ordenen{#creating-and-organizing-pages}

Deze sectie beschrijft om pagina&#39;s met Adobe Experience Manager (AEM) tot stand te brengen en te beheren zodat u inhoud [ op die pagina&#39;s kunt dan ](/help/sites-classic-ui-authoring/classic-page-author-edit-content.md) tot stand brengen.

>[!NOTE]
>
>Uw rekening vereist de [ aangewezen toegangsrechten ](/help/sites-administering/security.md) en [ toestemmingen ](/help/sites-administering/security.md#permissions) om actie op pagina&#39;s te voeren, bijvoorbeeld, creeer, kopieer, bewerk, schrap.
>
>Als u om het even welke problemen ontmoet wij adviseren u uw systeembeheerder contacteert.

## Uw website ordenen {#organizing-your-website}

Als auteur moet u uw website organiseren binnen AEM. Dit betekent dat u inhoudspagina&#39;s maakt en een naam geeft, zodat:

* u kunt ze gemakkelijk vinden in de ontwerpomgeving
* bezoekers van uw site kunnen deze gemakkelijk in de publicatieomgeving bekijken

U kunt [ omslagen ](#creating-a-new-folder) ook gebruiken helpen uw inhoud organiseren.

De structuur van een website kan van als a *boomstructuur* worden gedacht die uw inhoudspagina&#39;s houdt. De namen van deze inhoudspagina&#39;s worden gebruikt om URLs te vormen, terwijl de titel wordt getoond wanneer de paginainhoud wordt bekeken.

In het volgende voorbeeld ziet u een extract van de Geometrixx-site, waar bijvoorbeeld de pagina `Triangle` wordt geopend:

* Auteursomgeving

  `http://localhost:4502/cf#/content/geometrixx/en/products/triangle.html`

* Publicatie-omgeving

  `http://localhost:4503/content/geometrixx/en/products/triangle.html`

  Afhankelijk van de configuratie van uw instantie kan het gebruik van `/content` optioneel zijn in de publicatieomgeving.

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

Deze structuur kan van de console van Websites worden bekeken, die u kunt gebruiken om [ door de boomstructuur ](/help/sites-classic-ui-authoring/author-env-basic-handling.md#main-pars-text-15) te navigeren.

![ chlimage_1-151 ](assets/chlimage_1-151.png)

### Naamgevingsconventies voor pagina {#page-naming-conventions}

Bij het maken van een pagina zijn er twee sleutelvelden:

* **[Titel](#title)**:

   * Dit wordt aan de gebruiker getoond in de console en bij het uitgeven bij de bovenkant van de paginainhoud getoond.
   * Dit veld is verplicht.

* **[Naam](#name)**:

   * Hiermee wordt de URI gegenereerd.
   * Gebruikersinvoer voor dit veld is optioneel. Indien niet opgegeven, wordt de naam afgeleid van de titel.

Wanneer het creëren van een pagina, bevestigt AEM [ de paginanaam volgens de overeenkomsten ](/help/sites-developing/naming-conventions.md) die door AEM en JCR worden opgelegd.

De implementatie en de lijst met toegestane tekens verschillen enigszins afhankelijk van de gebruikersinterface (deze is uitgebreider voor de interface met aanraakbediening), maar het minimaal toegestane aantal is:

* &#39;a&#39; tot en met &#39;z&#39;
* &#39;A&#39; tot en met &#39;Z&#39;
* 0 tot en met 9
* _ (onderstrepingsteken)
* `-` (afbreekstreepje/minteken)

Gebruik enkel deze karakters als u zeker van hen wilt zijn die worden goedgekeurd/worden gebruikt (als u volledige details van alle toegelaten karakters nodig hebt, zie [ de noemende overeenkomsten ](/help/sites-developing/naming-conventions.md)).

#### Titel {#title}

Als u slechts een pagina **Titel** wanneer het creëren van een pagina verstrekt, leidt AEM de pagina **Naam** van dit koord af en [ bevestigt de naam volgens de overeenkomsten ](/help/sites-developing/naming-conventions.md) die door AEM en JCR worden opgelegd. In beide UIs zal het gebied van de Titel van de a **&#x200B;**&#x200B;dat ongeldige karakters bevat worden goedgekeurd, maar de afgeleide naam zal de ongeldige karakters vervangen hebben. Bijvoorbeeld:

| Titel | Afgeleide naam |
|---|---|
| Schön | schoen.html |
| SC%&amp;&ast;ç+ | sc---c-.html |

#### Naam {#name}

Als u een pagina **Naam** wanneer het creëren van een pagina levert, bevestigt AEM [ de naam volgens de overeenkomsten ](/help/sites-developing/naming-conventions.md) die door AEM en JCR worden opgelegd.

In Klassieke UI kunt u **geen ongeldige karakters** op het **3&rbrace; gebied van de Naam &lbrace;ingaan.**

>[!NOTE]
>In aanraking-toegelaten UI kunt u **geen ongeldige karakters** op het **3&rbrace; gebied van de Naam &lbrace;voorleggen.** Wanneer AEM ongeldige tekens detecteert, wordt het veld gemarkeerd en wordt een verklarende melding weergegeven om aan te geven welke tekens moeten worden verwijderd/vervangen.

>[!NOTE]
>
>Gebruik geen tweelettercode zoals gedefinieerd in ISO-639-1, tenzij het een hoofdtaalcode is.
>
>Zie [ Voorbereidend Inhoud voor Vertaling ](/help/sites-administering/tc-prep.md) voor meer informatie.

### Sjablonen {#templates}

In AEM geeft een sjabloon een speciaal type pagina op. Een sjabloon wordt gebruikt als basis voor elke nieuwe pagina die wordt gemaakt.

De sjabloon definieert de structuur van een pagina, inclusief een miniatuurafbeelding en andere eigenschappen. U hebt bijvoorbeeld aparte sjablonen voor productpagina&#39;s, sitemaps en contactgegevens. De malplaatjes worden samengesteld uit [ componenten ](#components).

AEM wordt geleverd met verschillende sjablonen die u kunt vinden. De aangeboden sjablonen zijn afhankelijk van de afzonderlijke website en de informatie die moet worden verschaft (wanneer u de nieuwe pagina maakt) is afhankelijk van de gebruikte interface. De belangrijkste velden zijn:

* **Titel**
De titel die op de resulterende webpagina wordt weergegeven.

* **Naam**
Wordt gebruikt bij de naamgeving van de pagina.

* **Malplaatje**
Een lijst met sjablonen die u kunt gebruiken bij het genereren van de nieuwe pagina.

### Onderdelen {#components}

Componenten zijn de elementen die door AEM worden geleverd, zodat u specifieke typen inhoud kunt toevoegen. AEM wordt geleverd met een reeks kant-en-klare componenten die uitgebreide functionaliteit bieden, zoals:

* Tekst
* Afbeelding
* Presentatie
* Video
* veel meer

Zodra u hebt gecreeerd en een pagina geopend kunt u [ inhoud toevoegen gebruikend de componenten ](/help/sites-classic-ui-authoring/classic-page-author-edit-content.md#insertinganewparagraph), beschikbaar bij [ hulpdekick ](/help/sites-classic-ui-authoring/classic-page-author-env-tools.md#sidekick).

## Pagina&#39;s beheren {#managing-pages}

### Een nieuwe pagina maken {#creating-a-new-page}

Tenzij alle pagina&#39;s vooraf voor u zijn gemaakt, moet u een pagina maken voordat u inhoud kunt gaan maken:

1. Van de **console Websites**, selecteer het niveau waarbij u een pagina wilt creëren.

   In het volgende voorbeeld, creeert u een pagina onder het niveau **Producten** - getoond in de linkerruit; de juiste ruit toont pagina&#39;s die reeds op het niveau onder **Producten** bestaan.

   ![ screen_shot_2012-02-15at114413am ](assets/screen_shot_2012-02-15at114413am.png)

1. In **Nieuw...** menu (klik de pijl naast **Nieuw..**), uitgezochte **Nieuwe Pagina...**. Het **leidt tot venster van de Pagina** opent.

   Het klikken **Nieuw..** handelt zelf ook als kortere weg aan de **Nieuwe Pagina...** optie.

1. Het **leidt tot de dialoog van de Pagina** laat u:

   * Verstrek a **Titel**; dit wordt getoond aan de gebruiker.
   * Verstrek a **Naam**; dit wordt gebruikt om URI te produceren. Als deze niet wordt opgegeven, wordt de naam afgeleid van de titel.

      * Als u een pagina **Naam** wanneer het creëren van een pagina levert, bevestigt AEM [ de naam volgens de overeenkomsten ](/help/sites-developing/naming-conventions.md) die door AEM en JCR worden opgelegd.
      * In klassieke UI kunt u **geen ongeldige karakters** op het **3&rbrace; gebied van de Naam &lbrace;ingaan.**

   * Klik op de sjabloon die u wilt gebruiken om de nieuwe pagina te maken.

     De sjabloon wordt gebruikt als basis voor de nieuwe pagina, bijvoorbeeld om de basislay-out van een inhoudspagina te bepalen.

   >[!NOTE]
   >
   >Zie [ Pagina noemende Conventies ](#page-naming-conventions).

   De minimuminformatie die wordt vereist om een pagina tot stand te brengen is de **Titel** en het vereiste malplaatje.

   ![ screen_shot_2012-02-15at114845am ](assets/screen_shot_2012-02-15at114845am.png)

   >[!NOTE]
   >
   >Als u unicode karakters in URLs zou willen gebruiken, plaats het bezit van de Alias ( `sling:alias`) ([ pagina eigenschappen ](/help/sites-classic-ui-authoring/classic-page-author-edit-page-properties.md)).

1. Klik **creëren** om de pagina tot stand te brengen. U keert aan de **console van Websites** terug waar u een ingang voor de nieuwe pagina kunt zien.

   De console verstrekt informatie over de pagina (bijvoorbeeld, toen het laatst werd uitgegeven en door wie) die zonodig wordt bijgewerkt.

   >[!NOTE]
   >
   >U kunt ook een pagina maken wanneer u een bestaande pagina bewerkt. Gebruikend **creeer de Pagina van het Kind** van het **Pagina** lusje van sidekick leidt direct tot een pagina onder de pagina die wordt uitgegeven.

### Een pagina openen voor bewerken {#opening-a-page-for-editing}

U kunt de pagina openen om [ worden uitgegeven ](/help/sites-classic-ui-authoring/classic-page-author-edit-content.md#editing-a-component-content-and-properties) door één van verscheidene methodes:

* Van **Websites** console, kunt u **tweemaal klikken** de paginaingang om het voor het uitgeven te openen.

* Van **Websites** console, kunt u **met de rechtermuisknop aanklikken** (contextmenu) het paginapunt, dan selecteren **Open** van het menu.

* Nadat u een pagina hebt geopend, kunt u naar andere pagina&#39;s binnen de site navigeren (om deze te bewerken) door op hyperlinks te klikken.

### Pagina&#39;s kopiëren en plakken {#copying-and-pasting-a-page}

Tijdens het kopiëren kunt u een van de volgende twee documenten kopiëren:

* één pagina
* een pagina samen met alle subpagina&#39;s

1. Van de **console Websites**, selecteer de pagina u wilt kopiëren.

   >[!NOTE]
   >
   >In dit stadium is het irrelevant of u één pagina of de onderliggende subpagina&#39;s wilt kopiëren.

1. Klik **Exemplaar**.

1. Ga naar de nieuwe locatie en klik op:

   * **Deeg** - om de pagina samen met alle subpages te kleven
   * **verschuiving + Deeg** - om de geselecteerde pagina slechts te kleven

   De pagina&#39;s worden op de nieuwe locatie geplakt.

   >[!NOTE]
   >
   >De paginanaam kan automatisch worden aangepast als een bestaande pagina al dezelfde naam heeft.

   >[!NOTE]
   >
   >U kunt **Pagina van het Exemplaar** van het **Pagina** lusje van sidekick ook gebruiken. Hiermee wordt een dialoogvenster geopend waarin u het doel kunt opgeven, enzovoort.

### Pagina verplaatsen of hernoemen {#moving-or-renaming-page}

>[!NOTE]
>
>Het anders noemen van een pagina is ook onderworpen aan de [ Pagina noemende Conventies ](#page-naming-conventions) wanneer het specificeren van de nieuwe paginanaam.

De procedure voor het verplaatsen of hernoemen van een pagina is hetzelfde. Met dezelfde handeling kunt u:

* een pagina naar een nieuwe locatie verplaatsen
* de naam van een pagina op dezelfde locatie wijzigen
* een pagina naar een nieuwe locatie verplaatsen en deze tegelijk een andere naam geven

AEM biedt u de functionaliteit om interne koppelingen bij te werken naar de pagina waarvan de naam wordt gewijzigd of die wordt verplaatst. Dit kan per pagina worden gedaan om volledige flexibiliteit te bieden.

Een pagina verplaatsen of hernoemen:

1. Er zijn verschillende methoden om een verplaatsing te activeren:

   * Van de **console Websites**, klik om de pagina te selecteren, dan **Beweging...**
   * Van de **console van Websites**, kunt u het paginapunt ook selecteren, dan **klik** met de rechtermuisknop aan en selecteer **Beweging..**
   * Wanneer het uitgeven van een pagina kunt u **Pagina van de Beweging** van de **Pagina** tabel van sidekick selecteren.

1. Het **venster van de Beweging** opent; hier kunt u of een nieuwe plaats, een nieuwe naam voor de pagina, of allebei specificeren.

   ![ screen_shot_2012-02-15at121336pm ](assets/screen_shot_2012-02-15at121336pm.png)

   De pagina bevat ook pagina&#39;s die direct of indirect verwijzen naar de pagina die wordt verplaatst. Afhankelijk van de status van de pagina waarnaar wordt verwezen, kunt u deze koppelingen aanpassen op de pagina&#39;s en/of deze opnieuw publiceren.

1. Vul de volgende velden in, al naar het geval:

   * **Doel**

     Gebruik de sitemap (beschikbaar via de keuzelijst) om de locatie te selecteren waarnaar de pagina moet worden verplaatst.

     Als u alleen de naam van de pagina wijzigt, negeert u dit veld.

   * **Beweging**

     Geef de pagina op die u wilt verplaatsen. Deze wordt gewoonlijk standaard ingevuld, afhankelijk van de manier waarop en de plaats waar u de verplaatsingsactie hebt gestart.

   * **anders noemen aan**

     Het huidige paginalabel wordt standaard weergegeven. Geef indien nodig het nieuwe paginalabel op.

   * **pas** aan

     Werk de koppelingen op de pagina bij die naar de verplaatste pagina verwijzen. Als pagina A bijvoorbeeld koppelingen naar pagina B bevat, past AEM de koppelingen op pagina A aan voor het geval u pagina B verplaatst.

     Dit kan voor elke afzonderlijke verwijzende pagina worden geselecteerd/worden geschrapt.

   * **opnieuw publiceren**

     Herpubliceer de verwijzende pagina; opnieuw kan dit voor elke individuele pagina worden geselecteerd.

   >[!NOTE]
   >
   >Als de pagina al is geactiveerd, wordt deze automatisch gedeactiveerd wanneer u de pagina verplaatst. Door gebrek, zal het worden opnieuw geactiveerd wanneer de beweging volledig is, maar dit kan worden veranderd door het **&#x200B;**&#x200B;gebied voor de pagina in het **&#x200B;**&#x200B;venster van de Beweging ongedaan te maken.

1. Klik **Beweging**. Bevestiging is vereist. Klik **O.K.** om te bevestigen.

   >[!NOTE]
   >
   >De paginatitel wordt niet bijgewerkt.

### Een pagina verwijderen {#deleting-a-page}

1. U kunt een pagina van diverse plaatsen schrappen:

   * Binnen de **console van Websites**, klik om de pagina te selecteren, dan met de rechtermuisknop te klikken en **Schrapping** van het resulterende menu te selecteren.
   * Binnen de **console van Websites**, klik om de pagina te selecteren, dan **Schrapping** van het toolbarmenu te selecteren.
   * Binnen sidekick gebruik het **lusje van de Pagina** om **Pagina van de Schrapping** te selecteren - dit schrapt de pagina die momenteel open is.

1. Nadat u hebt geselecteerd om een pagina te verwijderen, moet u de aanvraag bevestigen - aangezien de actie niet ongedaan kan worden gemaakt.

   >[!NOTE]
   >
   >Als de pagina na verwijdering is gepubliceerd, kunt u de nieuwste (of een specifieke) versie herstellen, maar deze heeft mogelijk niet precies dezelfde inhoud als de laatste versie als er verdere wijzigingen zijn aangebracht. Zie [ hoe te Pagina&#39;s ](/help/sites-classic-ui-authoring/classic-page-author-work-with-versions.md#restoringpages) voor verdere details herstellen.

>[!NOTE]
>
>Als een pagina al is geactiveerd, wordt deze automatisch gedeactiveerd voordat de pagina wordt verwijderd.

### Een pagina vergrendelen {#locking-a-page}

U kunt [ vergrendelen/ontgrendelen een pagina ](/help/sites-classic-ui-authoring/classic-page-author-edit-content.md#locking-a-page) van of een console of wanneer het uitgeven van een individuele pagina. Informatie over vergrendelde pagina&#39;s wordt ook op beide locaties weergegeven.

### Een nieuwe map maken {#creating-a-new-folder}

>[!NOTE]
>
>De omslagen zijn ook onderworpen aan de [ Pagina noemende Conventies ](#page-naming-conventions) wanneer het specificeren van de nieuwe omslagnaam.

1. Open de **console van Websites** en navigeer aan de vereiste plaats.
1. In **Nieuw...** menu (klik de pijl naast **Nieuw..**), uitgezochte **Nieuwe Omslag...**.
1. Het **Create de dialoogvakje van de Omslag** opent. Hier kunt u de **Naam** ingaan en **Titel**:

   ![ chlimage_1-152 ](assets/chlimage_1-152.png)

1. Selecteer **creeer** om de omslag tot stand te brengen.
