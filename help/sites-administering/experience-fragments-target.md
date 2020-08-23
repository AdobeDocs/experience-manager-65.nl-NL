---
title: Exporteren van ervaringsfragmenten naar Adobe Target
seo-title: Exporteren van ervaringsfragmenten naar Adobe Target
description: Exporteren van ervaringsfragmenten naar Adobe Target
seo-description: Exporteren van ervaringsfragmenten naar Adobe Target
uuid: 2df0faab-5d5e-4fc1-93b3-28b7e6f3c306
contentOwner: carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: integration
content-type: reference
discoiquuid: d4152b4d-531b-4b62-8807-a5bc5afe94c6
docset: aem65
translation-type: tm+mt
source-git-commit: 80b8571bf745b9e7d22d7d858cff9c62e9f8ed1e
workflow-type: tm+mt
source-wordcount: '1179'
ht-degree: 0%

---


# Exporteren van ervaringsfragmenten naar Adobe Target{#exporting-experience-fragments-to-adobe-target}

>[!CAUTION]
>
>Voor bepaalde functies op deze pagina is de toepassing van AEM 6.5.3.0 vereist.
>
>6.5.3.0
>
>* **U kunt nu Extern alizer-domeinen** selecteren.
>
>
6.5.2.0:
>
>* De Fragmenten van de ervaring kunnen worden uitgevoerd naar:
   >
   >   
   * de standaardwerkruimte.
   >   * een benoemde werkruimte, opgegeven in de Cloud Configuration.
   >   * **Opmerking:** Voor het exporteren naar specifieke werkruimten is Adobe Target Premium vereist.
>
>* AEM moeten met Adobe Target worden [geïntegreerd met behulp van Adobe I/O](/help/sites-administering/integration-ims-adobe-io.md).

>
>

AEM 6.5.0.0 en 6.5.1.0:
>
>* De fragmenten AEM Experience worden geëxporteerd naar de standaardwerkruimte van Adobe Target.
>* AEM moeten met Adobe Target worden geïntegreerd volgens de instructies in het kader van [Integratie met Adobe Target](/help/sites-administering/target.md).


U kunt [Experience Fragments](/help/sites-authoring/experience-fragments.md), gemaakt in Adobe Experience Manager (AEM), exporteren naar Adobe Target (Doel). Zij kunnen dan als aanbiedingen in de activiteiten van het Doel worden gebruikt, om ervaringen op schaal te testen en te personaliseren.

Er zijn drie formaatopties beschikbaar voor het uitvoeren van een Fragment van de Ervaring naar Adobe Target:

* HTML (standaard): Ondersteuning voor weergave van webinhoud en hybride inhoud
* JSON: Ondersteuning voor levering van inhoud zonder kop
* HTML &amp; JSON

AEM Experience Fragments kunnen worden geëxporteerd naar de standaardwerkruimte in Adobe Target of naar door de gebruiker gedefinieerde werkruimten voor Adobe Target. Dit gebeurt via Adobe I/O, waarvoor AEM met Adobe Target moeten worden [geïntegreerd met behulp van Adobe I/O](/help/sites-administering/integration-ims-adobe-io.md).

>[!NOTE]
>
>De Adobe Target-werkruimten bestaan niet in Adobe Target zelf. Ze worden gedefinieerd en beheerd in Adobe IMS (Identity Management System) en vervolgens geselecteerd voor gebruik in verschillende oplossingen met Adobe I/O-integratie.

>[!NOTE]
>
>De werkruimten van Adobe Target kunnen worden gebruikt om leden van een organisatie (groep) toe te staan om aanbiedingen en activiteiten voor slechts deze organisatie tot stand te brengen en te beheren; zonder andere gebruikers toegang te geven. Bijvoorbeeld landspecifieke organisaties binnen een wereldwijd bereik.

>[!NOTE]
>
>Zie ook voor meer informatie:
>
>* [Adobe Target-ontwikkeling](https://www.adobe.io/apis/experiencecloud/target.html)
>* [Kernonderdelen - Ervaar fragmenten](https://docs.adobe.com/content/help/en/experience-manager-core-components/using/components/experience-fragment.html)

>



## Vereisten {#prerequisites}

>[!CAUTION]
>
>Voor bepaalde functies op deze pagina is de toepassing van AEM 6.5.3.0 vereist.

Er zijn verschillende acties vereist:

1. U moet AEM met Adobe Target [integreren gebruikend Adobe I/O](/help/sites-administering/integration-ims-adobe-io.md).
2. De Fragmenten van de ervaring worden uitgevoerd van de AEM auteurinstantie, zodat moet u AEM Verbinding Externalzer [op de auteursinstantie](/help/sites-administering/target-requirements.md#configuring-the-aem-link-externalizer) vormen om ervoor te zorgen dat om het even welke verwijzingen binnen het Fragment van de Ervaring voor Weblevering worden geexternaliseerd.

   >[!NOTE]
   >
   >Voor verbinding die niet door het gebrek wordt behandeld herschrijft, is de Leverancier [van Rewriter van de Verbinding van het Fragment van de](/help/sites-developing/experience-fragments.md#the-experience-fragment-link-rewriter-provider-html) Ervaring. Met dit, kunnen de aangepaste regels voor uw geval worden ontwikkeld.

## Cloudconfiguratie toevoegen {#add-the-cloud-configuration}

Voordat u een fragment exporteert, moet u de **Cloud Configuration** voor **Adobe Target** toevoegen aan het fragment of de map. Hierdoor kunt u ook:

* de indelingsoptie(s) opgeven die voor de export moet worden gebruikt
* een doelwerkruimte selecteren als doel
* selecteer een extern domein om verwijzingen in het Fragment van de Ervaring te herschrijven (facultatief)

De vereiste opties kunnen worden geselecteerd in **Pagina-eigenschappen** van de vereiste map en/of het vereiste fragment. het productdossier zal zo nodig worden geërfd .

1. Navigeer naar de **console van de Fragmenten** van de Ervaring.

1. Open **Pagina-eigenschappen** voor de juiste map of het juiste fragment.

   >[!NOTE]
   >
   >Als u de wolkenconfiguratie aan de ouderomslag van het Fragment van de Ervaring toevoegt, wordt de configuratie geërft door alle kinderen.
   >
   >
   >Als u de wolkenconfiguratie aan het Fragment van de Ervaring zelf toevoegt, wordt de configuratie geërft door alle variaties.

1. Selecteer het tabblad **Cloud Services** .

1. Selecteer **Adobe Target** in de vervolgkeuzelijst onder Configuratie **Cloud Service** .

   >[!NOTE]
   >
   >De JSON-indeling van een Experience Fragment-aanbieding kan worden aangepast. Hiervoor definieert u een component van het fragment van de klantenervaring en annoteert u hoe u de eigenschappen van de component in het Sling-model van de component exporteert.
   >
   >Zie de kerncomponent:
   >
   >[Kernonderdelen - Ervaar fragmenten](https://docs.adobe.com/content/help/en/experience-manager-core-components/using/components/experience-fragment.html)

   Selecteer onder **Adobe Target** :

   * de juiste configuratie
   * de optie voor de vereiste indeling
   * een Adobe Target-werkruimte
   * indien vereist - het externalizer-domein

   >[!CAUTION]
   >
   >Het externalizer-domein is optioneel. Een AEM externalizer wordt gevormd wanneer u de uitgevoerde inhoud aan een specifiek *publiceer* domein wilt richten. Voor meer details zie het [Vormen van de Verbinding External](/help/sites-administering/target-requirements.md#configuring-the-aem-link-externalizer)van de AEM.

   Bijvoorbeeld voor een map:

   ![Map - Cloud](assets/xf-target-integration-01.png "Services-map - Cloud Services")

1. **Opslaan en sluiten**.

## Een ervaringsfragment exporteren naar Adobe Target {#exporting-an-experience-fragment-to-adobe-target}

>[!CAUTION]
>
>Voor media-elementen, zoals afbeeldingen, wordt alleen een verwijzing naar Doel geëxporteerd. Het element zelf blijft opgeslagen in AEM Assets en wordt geleverd via de AEM-publicatie-instantie.
>
>Daarom moet het ervaringsfragment, met alle gerelateerde elementen, worden gepubliceerd voordat het naar Target kan worden geëxporteerd.

Een ervaringsfragment exporteren van AEM naar doel (na het opgeven van de cloudconfiguratie):

1. Navigeer naar de Experience Fragment-console.
1. Selecteer het ervaringsfragment dat u naar doel wilt exporteren.

   >[!NOTE]
   >
   >Het moet een variant van het Web van het Fragment van de Ervaring zijn.

1. Tik/klik op **Exporteren naar Adobe Target**.

   >[!NOTE]
   >
   >Als het ervaringsfragment al is geëxporteerd, selecteert u **Bijwerken in Adobe Target**.

1. Tik/klik op **Exporteren zonder publiceren** of **Publiceren** naar wens.

   >[!NOTE]
   >
   >Als u **Publiceren** selecteert, wordt het ervaringsfragment meteen gepubliceerd en naar Doel verzonden.

1. Tik/klik op **OK** in het bevestigingsvenster.

   Het ervaringsfragment moet nu in Doel staan.

   >[!NOTE]
   >
   >[Diverse details](/help/sites-authoring/experience-fragments.md#details-of-your-experience-fragment) van de uitvoer kunnen in de Mening **van de** Lijst van de console en de **Eigenschappen** worden gezien.

   >[!NOTE]
   >
   >Wanneer u een Experience Fragment weergeeft in Adobe Target, is de *laatst gewijzigde* datum die wordt weergegeven de datum waarop het fragment voor het laatst is gewijzigd in AEM, niet de datum waarop het fragment voor het laatst is geëxporteerd naar Adobe Target.

>[!NOTE]
>
>U kunt het exporteren ook vanuit de pagina-editor uitvoeren met behulp van vergelijkbare opdrachten in het menu [Pagina-informatie](/help/sites-authoring/author-environment-tools.md#page-information) .

## Uw ervaringsfragmenten in Adobe Target gebruiken {#using-your-experience-fragments-in-adobe-target}

Na het uitvoeren van de voorafgaande taken, toont het ervaringsfragment op de pagina van Aanbiedingen in Doel. Raadpleeg de [specifieke doeldocumentatie](https://experiencecloud.adobe.com/resources/help/en_US/target/target/aem-experience-fragments.html) voor meer informatie over wat u daar kunt bereiken.

>[!NOTE]
>
>Wanneer u een Experience Fragment weergeeft in Adobe Target, is de *laatst gewijzigde* datum die wordt weergegeven de datum waarop het fragment voor het laatst is gewijzigd in AEM, niet de datum waarop het fragment voor het laatst is geëxporteerd naar Adobe Target.

## Een ervaringsfragment verwijderen dat al naar Adobe Target is geëxporteerd {#deleting-an-experience-fragment-already-exported-to-adobe-target}

Als u een ervaringsfragment verwijdert dat al naar Target is geëxporteerd, kan dit problemen veroorzaken als het fragment al in een aanbieding in Target wordt gebruikt. Als u het fragment verwijdert, wordt de aanbieding onbruikbaar omdat de fragmentinhoud door AEM wordt geleverd.

Om dergelijke situaties te voorkomen:

* Als het ervaringsfragment momenteel niet wordt gebruikt in een activiteit, AEM kan de gebruiker het fragment zonder een waarschuwingsbericht verwijderen.
* Als het ervaringsfragment momenteel door een activiteit in Doel wordt gebruikt, wordt de AEM gebruiker een foutbericht gegeven over de mogelijke gevolgen die het verwijderen van het fragment voor de activiteit zal hebben.

   Het foutbericht in AEM belet de gebruiker niet (geforceerd) het ervaringsfragment te verwijderen. Als het ervaringsfragment wordt verwijderd:

   * De aanbieding van het Doel met AEM Fragment van de Ervaring kan ongewenste gedrag tonen

      * De aanbieding wordt waarschijnlijk nog steeds weergegeven, aangezien de Experience Fragment-HTML naar Target werd geduwd
      * Eventuele verwijzingen in het ervaringsfragment werken mogelijk niet correct als middelen waarnaar wordt verwezen ook in AEM worden verwijderd.
   * Uiteraard zijn verdere wijzigingen van het ervaringsfragment niet mogelijk omdat het ervaringsfragment niet meer in AEM bestaat.