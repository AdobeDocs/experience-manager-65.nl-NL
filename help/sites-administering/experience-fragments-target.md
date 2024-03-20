---
title: Exporteren van ervaringsfragmenten naar Adobe Target
description: Leer hoe u Adobe Experience Manager (AEM) Experience Fragments exporteert naar Adobe Target.
contentOwner: carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: integration
content-type: reference
docset: aem65
exl-id: f2921349-de8f-4bc1-afa2-aeace99cfc5c
solution: Experience Manager, Experience Manager Sites
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '1513'
ht-degree: 0%

---

# Exporteren van ervaringsfragmenten naar Adobe Target{#exporting-experience-fragments-to-adobe-target}

>[!CAUTION]
>
>Voor bepaalde functionaliteit op deze pagina is de toepassing van AEM 6.5.3.0 (of hoger) vereist.
>
>6.5.3.0:
>
>* **ExternalAlizer-domeinen** kan nu worden geselecteerd.
>  **Opmerking:** De Domeinen van de externalizer zijn slechts relevant voor de inhoud van het Fragment van de Ervaring dat naar Doel wordt verzonden, en niet meta-gegevens zoals de Inhoud van de Aanbieding van de Mening.
>
>6.5.2.0:
>
>* De Fragmenten van de ervaring kunnen worden uitgevoerd naar:
>
>   * de standaardwerkruimte.
>   * een benoemde werkruimte, opgegeven in de Cloud Configuration.
>   * **Opmerking:** Voor het exporteren naar specifieke werkruimten is Adobe Target Premium vereist.
>
>* AEM moet [geïntegreerd met Adobe Target met IMS](/help/sites-administering/integration-target-ims.md).
>
>AEM 6.5.0.0 en 6.5.1.0:
>
>* De fragmenten AEM Ervaring worden geëxporteerd naar de standaardwerkruimte van Adobe Target.
>* AEM moet in Adobe Target worden geïntegreerd volgens de instructies in [Integreren met Adobe Target](/help/sites-administering/target.md).

U kunt exporteren [Ervaar fragmenten](/help/sites-authoring/experience-fragments.md), gemaakt in Adobe Experience Manager (AEM), naar Adobe Target (Target). Zij kunnen dan als aanbiedingen in de activiteiten van het Doel worden gebruikt, om, ervaringen op schaal te testen en te personaliseren.

Er zijn drie formaatopties beschikbaar voor het uitvoeren van een Fragment van de Ervaring naar Adobe Target:

* HTML (standaard): ondersteuning voor web en hybride inhoud
* JSON: ondersteuning voor levering van inhoud zonder kop
* HTML en JSON

AEM Experience Fragments kunnen worden geëxporteerd naar de standaardwerkruimte in Adobe Target of naar door de gebruiker gedefinieerde werkruimten voor Adobe Target. Dit doet u met de Adobe Developer-console, waarvoor AEM [geïntegreerd met Adobe Target met IMS](/help/sites-administering/integration-target-ims.md).

>[!NOTE]
>
>De Adobe Target-werkruimten bestaan niet in Adobe Target zelf. Deze worden gedefinieerd en beheerd in Adobe IMS (Identity Management System) en vervolgens geselecteerd voor gebruik in alle oplossingen met behulp van integratie in de Adobe Developer Console.

>[!NOTE]
>
>De werkruimten van Adobe Target kunnen worden gebruikt om leden van een organisatie (groep) toe te staan om aanbiedingen en activiteiten voor deze organisatie slechts tot stand te brengen en te beheren; zonder toegang tot andere gebruikers te verlenen. Bijvoorbeeld landspecifieke organisaties binnen een wereldwijd bereik.

>[!NOTE]
>
>Zie ook voor meer informatie:
>
>* [Adobe Target-ontwikkeling](https://developers.adobetarget.com/)
>* [Kernonderdelen - Ervaar fragmenten](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/wcm-components/experience-fragment.html)
>

## Vereisten {#prerequisites}

>[!CAUTION]
>
>Voor bepaalde functies op deze pagina is de toepassing van AEM 6.5.3.0 vereist.

Er zijn verschillende acties vereist:

1. U moet [AEM integreren met Adobe Target met IMS](/help/sites-administering/integration-target-ims.md).
2. De Fragmenten van de ervaring worden uitgevoerd van de AEM auteurinstantie zodat moet u [Vorm AEM Verbinding Externalzer](/help/sites-administering/target-requirements.md#configuring-the-aem-link-externalizer) op de auteurinstantie om ervoor te zorgen dat om het even welke verwijzingen binnen het Fragment van de Ervaring voor Weblevering worden geexternaliseerd.

   >[!NOTE]
   >
   >Voor het herschrijven van koppelingen die niet door de standaardwaarde worden gedekt, wordt de [Experience Fragment Link Rewriter Provider](/help/sites-developing/experience-fragments.md#the-experience-fragment-link-rewriter-provider-html) is beschikbaar. Met dit, kunnen de aangepaste regels voor uw geval worden ontwikkeld.

## Cloudconfiguratie toevoegen {#add-the-cloud-configuration}

Voordat u een fragment exporteert, moet u de opdracht **Cloud Configuration** for **Adobe Target** naar het fragment of de map. Hierdoor kunt u ook:

* Geef de indelingsopties op die voor het exporteren moeten worden gebruikt
* een doelwerkruimte selecteren als doel
* Selecteer een externalizer-domein voor het herschrijven van verwijzingen in het ervaringsfragment (optioneel)

U kunt de vereiste opties selecteren in **Pagina-eigenschappen** van de vereiste map en/of het vereiste fragment; de specificatie wordt indien nodig overgeërfd.

1. Ga naar de **Ervaar fragmenten** console.

1. Openen **Pagina-eigenschappen** voor de juiste map of het juiste fragment.

   >[!NOTE]
   >
   >Als u de wolkenconfiguratie aan de ouderomslag van het Fragment van de Ervaring toevoegt, wordt de configuratie geërft door alle kinderen.
   >
   >
   >Als u de wolkenconfiguratie aan het Fragment van de Ervaring zelf toevoegt, wordt de configuratie geërft door alle variaties.

1. Selecteer de **Cloud Servicen** tab.

1. Onder **Configuratie Cloud Service**, selecteert u **Adobe Target** in de vervolgkeuzelijst.

   >[!NOTE]
   >
   >De JSON-indeling van een Experience Fragment-aanbieding kan worden aangepast. Hiertoe definieert u een componentervaringsfragmentcomponent en noteert u vervolgens hoe u de eigenschappen ervan in het deelstijlmodel exporteert.
   >
   >Zie de kerncomponent:
   >
   >[Kernonderdelen - Ervaar fragmenten](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/wcm-components/experience-fragment.html)

   Onder **Adobe Target** selecteren:

   * de juiste configuratie
   * de optie voor de vereiste indeling
   * een Adobe Target-werkruimte
   * indien nodig - het Externalalizer-domein

   >[!CAUTION]
   >
   >Het ExternalAlizer-domein is optioneel.
   >
   >Er is een AEM-externalizer geconfigureerd wanneer u wilt dat de geëxporteerde inhoud naar een specifieke instantie verwijst *publish* domein. Zie voor meer informatie [Het vormen van de AEM Verbinding Externalzer](/help/sites-administering/target-requirements.md#configuring-the-aem-link-externalizer).
   >
   >Houd er ook rekening mee dat Externe domeinen alleen relevant zijn voor de inhoud van het ervaringsfragment dat naar Doel wordt verzonden, en niet voor metagegevens zoals Inhoud weergaveaanbod.

   Bijvoorbeeld voor een map:

   ![Map - Cloud Servicen](assets/xf-target-integration-01.png "Map - Cloud Servicen")

1. **Opslaan en sluiten**.

## Een ervaringsfragment exporteren naar Adobe Target {#exporting-an-experience-fragment-to-adobe-target}

>[!CAUTION]
>
>Voor media-elementen, zoals afbeeldingen, wordt alleen een verwijzing naar Doel geëxporteerd. Het element zelf blijft opgeslagen in AEM Assets en wordt geleverd via de AEM-publicatie-instantie.
>
>Daarom moet het Experience Fragment, met alle gerelateerde elementen, worden gepubliceerd voordat het naar Target wordt geëxporteerd.

Een ervaringsfragment van AEM naar doel exporteren (nadat u de Cloud-configuratie hebt opgegeven):

1. Navigeer naar de Experience Fragment-console.
1. Selecteer het ervaringsfragment dat u naar doel wilt exporteren.

   >[!NOTE]
   >
   >Het moet een variant van het Web van het Fragment van de Ervaring zijn.

1. Klikken **Exporteren naar Adobe Target**.

   >[!NOTE]
   >
   >Als het Experience Fragment al is geëxporteerd, selecteert u **Bijwerken in Adobe Target**.

1. Klikken **Exporteren zonder publiceren** of **Publiceren** zoals vereist.

   >[!NOTE]
   >
   >Selecteren **Publiceren** publiceert het Experience Fragment meteen en verzendt het naar Target.

1. Klikken **OK** in het bevestigingsdialoogvenster.

   Het ervaringsfragment moet nu Doel zijn.

   >[!NOTE]
   >
   >[Diverse details](/help/sites-authoring/experience-fragments.md#details-of-your-experience-fragment) van de uitvoer **Lijstweergave** van de console en **Eigenschappen**.

   >[!NOTE]
   >
   >Als u een Experience Fragment weergeeft in Adobe Target, kunt u *laatst gewijzigd* De datum die wordt weergegeven, is de datum waarop het fragment voor het laatst is gewijzigd in AEM, niet de datum waarop het fragment voor het laatst is geëxporteerd naar Adobe Target.

>[!NOTE]
>
>U kunt het exporteren ook vanuit de paginaeditor uitvoeren met behulp van vergelijkbare opdrachten in het dialoogvenster [Pagina-informatie](/help/sites-authoring/author-environment-tools.md#page-information) -menu.

## Uw ervaringsfragmenten in Adobe Target gebruiken {#using-your-experience-fragments-in-adobe-target}

Nadat u de voorgaande taken hebt uitgevoerd, wordt het Experience Fragment weergegeven op de pagina Offers in Adobe Target. Kijk naar de [specifieke doeldocumentatie](https://experienceleague.adobe.com/docs/target/using/experiences/offers/aem-experience-fragments.html) voor meer informatie over wat je daar kunt bereiken.

>[!NOTE]
>
>Als u een Experience Fragment weergeeft in Adobe Target, kunt u *laatst gewijzigd* De datum die wordt weergegeven, is de datum waarop het fragment voor het laatst is gewijzigd in AEM, niet de datum waarop het fragment voor het laatst is geëxporteerd naar Adobe Target.

## Een ervaringsfragment verwijderen dat al naar Adobe Target is geëxporteerd {#deleting-an-experience-fragment-already-exported-to-adobe-target}

Als u een ervaringsfragment verwijdert dat al naar Target is geëxporteerd, kan dit problemen veroorzaken als het fragment al in een aanbieding in Adobe Target wordt gebruikt. Als u het fragment verwijdert, wordt de aanbieding onbruikbaar omdat de fragmentinhoud door AEM wordt geleverd.

Om dergelijke situaties te voorkomen:

* Als het ervaringsfragment momenteel niet wordt gebruikt in een activiteit, AEM kan de gebruiker het fragment zonder een waarschuwingsbericht verwijderen.
* Als het ervaringsfragment in gebruik is door een activiteit in Adobe Target, wordt de AEM gebruiker een foutbericht gegeven over de mogelijke gevolgen die het verwijderen van het fragment kan hebben voor de activiteit.

  Het foutbericht in AEM belet de gebruiker niet (geforceerd) het ervaringsfragment te verwijderen. Als het ervaringsfragment wordt verwijderd:

   * De aanbieding van het Doel met AEM Fragment van de Ervaring kan ongewenste gedrag tonen

      * Het aanbod wordt waarschijnlijk nog steeds weergegeven, aangezien de HTML van het ervaringsfragment naar Target is geduwd
      * Eventuele verwijzingen in het ervaringsfragment werken mogelijk niet correct als middelen waarnaar wordt verwezen ook in AEM worden verwijderd.

   * Eventuele verdere wijzigingen in het ervaringsfragment zijn onmogelijk omdat het ervaringsfragment niet meer in AEM bestaat.


## ClientLibs verwijderen uit Experience Fragments geëxporteerd naar Target {#removing-clientlibs-from-fragments-exported-target}

De Fragmenten van de ervaring bevatten volledige HTML- markeringen en alle noodzakelijke Bibliotheken van de Cliënt (CSS/JS) om het fragment precies terug te geven aangezien het door de Inhoudsauteur van het Fragment van de Ervaring werd gecreeerd. Dit is bijontwerp.

Wanneer u een Experience Fragment-aanbieding met Adobe Target gebruikt op een pagina die door AEM wordt geleverd, bevat de doelpagina al alle benodigde clientbibliotheken. Bovendien is de externe html in de Geniet van het Fragment van de Ervaring ook niet nodig (zie [Overwegingen](#considerations)).

Hier volgt een pseudo-voorbeeld van de HTML in een Experience Fragment-aanbieding:

```html
<!DOCTYPE>
<html>
   <head>
      <title>…</title>
      <!-- all the client libraries (css/js) -->
      …
   </head>
   <body>
        <!--/* Actual XF Offer content would appear here... */-->
   </body>
</html>
```

Op een hoog niveau doet AEM een Ervaringsfragment naar Adobe Target exporteren dit met behulp van verschillende extra Sling Selectors. De URL voor het geëxporteerde ervaringsfragment ziet er bijvoorbeeld als volgt uit (opmerking) `nocloudconfigs.atoffer`):

* http://www.your-aem-instance.com/content/experience-fragments/my-offers/my-xf-offer.nocloudconfigs.atoffer.html

De `nocloudconfigs` kiezer wordt gedefinieerd met HTML en kan worden bedekt door deze te kopiëren uit:

* /libs/cq/experience-fragments/components/xfpage/nocloudconfigs.html

De `atoffer` kiezer is na verwerking toegepast met [Sling Rewriter](/help/sites-developing/experience-fragments.md#the-experience-fragment-link-rewriter-provider-html). Of kan worden gebruikt om de Bibliotheken van de Cliënt te verwijderen.

### Voorbeeld {#example}

Laten we hier illustreren hoe u dit kunt doen `nocloudconfigs`.

>[!NOTE]
>
>Zie [Bewerkbare sjablonen](/help/sites-developing/templates.md#editable-templates) voor nadere bijzonderheden.

#### Bedekkingen {#overlays}

In dit specifieke voorbeeld wordt [bedekkingen](/help/sites-developing/overlays.md) die worden opgenomen, verwijdert de clientbibliotheken *en* de vreemde html. Aangenomen wordt dat u al het Sjabloontype voor fragmenten uit ervaring hebt gemaakt. De benodigde bestanden die moeten worden gekopieerd `/libs/cq/experience-fragments/components/xfpage/` omvatten:

* `nocloudconfigs.html`
* `head.nocloudconfigs.html`
* `body.nocloudconfigs.html`

#### Sjabloonoverlays {#template-type-overlays}

In dit voorbeeld is dit de volgende structuur:

![Sjabloonoverlays](assets/xf-target-integration-02.png "Sjabloonoverlays")

De inhoud van deze bestanden is als volgt:

* `body.nocloudconfigs.html`

  ![body.nocloudconfigs.html](assets/xf-target-integration-03.png "body.nocloudconfigs.html")

* `head.nocloudconfigs.html`

  ![head.nocloudconfigs.html](assets/xf-target-integration-04.png "head.nocloudconfigs.html")

* `nocloudconfigs.html`

  ![nocloudconfigs.html](assets/xf-target-integration-05.png "nocloudconfigs.html")

>[!NOTE]
>
>Te gebruiken `data-sly-unwrap` als u de tag body wilt verwijderen, moet u `nocloudconfigs.html`.

### Overwegingen {#considerations}

Als u zowel AEM plaatsen als niet AEM plaatsen moet steunen gebruikend de Aanbiedingen van het Fragment van de Ervaring in Adobe Target, moet u twee Fragments van de Ervaring (twee verschillende malplaatjetypes) tot stand brengen:

* Eén met de overlay om clientlibs/extra html te verwijderen

* Een die niet de overlay heeft en daarom de vereiste clientlibs bevat