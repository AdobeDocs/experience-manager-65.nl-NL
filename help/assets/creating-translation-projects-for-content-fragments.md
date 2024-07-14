---
title: Vertaalprojecten maken voor inhoudsfragmenten
description: Leer hoe u inhoudsfragmenten in Adobe Experience Manager vertaalt.
contentOwner: AEM Docs
products: SG_EXPERIENCEMANAGER/6.5/ASSETS
topic-tags: managing-assets
content-type: reference
feature: Content Fragments
role: User, Admin
exl-id: 19bb58da-8220-404e-bddb-34be94a3a7d7
solution: Experience Manager, Experience Manager Assets
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '926'
ht-degree: 0%

---

# Vertaalprojecten maken voor inhoudsfragmenten {#creating-translation-projects-for-content-fragments}

Naast activa, steunt Adobe Experience Manager (AEM) Assets de werkschema&#39;s van het taalexemplaar voor [ inhoudsfragmenten ](/help/assets/content-fragments/content-fragments.md) (met inbegrip van variaties). Er is geen extra optimalisatie vereist voor het uitvoeren van workflows voor het kopiëren van talen op inhoudsfragmenten. In elke werkstroom wordt het volledige inhoudsfragment verzonden voor vertaling.

De typen workflows die u op inhoudsfragmenten kunt uitvoeren, lijken precies op de typen werkstromen die u voor elementen uitvoert. Bovendien komen de opties die beschikbaar zijn binnen elk workflowtype overeen met de opties die beschikbaar zijn onder de corresponderende workflowtypen voor elementen.

U kunt de volgende typen werkstromen voor het kopiëren van talen uitvoeren op inhoudsfragmenten:

**creeer en vertaal**

In deze workflow worden inhoudsfragmenten die moeten worden vertaald, gekopieerd naar de hoofdmap van de taal waarnaar u wilt vertalen. Bovendien wordt, afhankelijk van de opties u kiest, een vertaalproject gecreeerd voor de inhoudsfragmenten in de console van Projecten. Afhankelijk van de instellingen kan het vertaalproject handmatig worden gestart of automatisch worden uitgevoerd zodra het vertaalproject is gemaakt.

**de taalexemplaren van de Update**

Wanneer het broninhoudsfragment wordt bijgewerkt of gewijzigd, moet het bijbehorende taalspecifieke inhoudsfragment opnieuw worden vertaald. De workflow voor het kopiëren van de updatetaal zet een extra groep inhoudsfragmenten om en neemt deze op in een taalkopie voor een bepaalde landinstelling. In dit geval worden de vertaalde inhoudsfragmenten toegevoegd aan de doelmap die al vertaalde inhoudsfragmenten bevat.

## Workflow maken en vertalen {#create-and-translate-workflow}

De workflow Maken en vertalen bevat de volgende opties. De procedurele stappen die aan elke optie zijn gekoppeld, zijn vergelijkbaar met die welke aan de overeenkomstige optie voor activa zijn gekoppeld.

* Creeer slechts structuur: Voor procedurestappen, zie [ structuur slechts voor activa ](translation-projects.md#create-structure-only) creëren.
* Creeer een vertaalproject: Voor procedurestappen, zie [ een vertaalproject voor activa ](translation-projects.md#create-a-new-translation-project) creëren.
* Voeg aan bestaand vertaalproject toe: Voor procedurestappen, zie [ aan bestaand vertaalproject voor activa ](translation-projects.md#add-to-existing-translation-project) toevoegen.

## Workflow voor het kopiëren van talen bijwerken {#update-language-copies-workflow}

De workflow voor het kopiëren van de taal Bijwerken bevat de volgende opties. De procedurele stappen die aan elke optie zijn gekoppeld, zijn vergelijkbaar met die welke aan de overeenkomstige optie voor activa zijn gekoppeld.

* Creeer een vertaalproject: Voor procedurestappen, zie [ een vertaalproject voor activa ](translation-projects.md#create-a-new-translation-project) (updatewerkschema) creëren.
* Voeg aan bestaand vertaalproject toe: Voor procedurestappen, zie [ aan bestaand vertaalproject voor activa ](translation-projects.md#add-to-existing-translation-project) (updatewerkschema) toevoegen.

U kunt ook tijdelijke-taalkopieën maken voor fragmenten, vergelijkbaar met de manier waarop u tijdelijke kopieën maakt voor elementen. Voor details, zie [ Creërend tijdelijke taalexemplaren voor activa ](translation-projects.md#creating-temporary-language-copies).

## Gemengde-mediafragmenten omzetten {#translating-mixed-media-fragments}

Met AEM kunt u inhoudsfragmenten vertalen die verschillende typen media-elementen en -verzamelingen bevatten. Als u een inhoudsfragment vertaalt dat inline-elementen bevat, worden de vertaalde kopieën van deze elementen opgeslagen onder de hoofdmap van de doeltaal.

Als het inhoudsfragment een verzameling bevat, worden de elementen in de verzameling samen met het inhoudsfragment vertaald. De vertaalde exemplaren van de activa worden opgeslagen binnen de aangewezen wortel van de doeltaal bij een plaats die de fysieke plaats van de bronactiva onder de wortel van de brontaal aanpast.

Als u inhoudsfragmenten met gemengde media wilt kunnen vertalen, bewerkt u eerst het standaardvertaalframework om de vertaling van inline-elementen en -verzamelingen met betrekking tot inhoudsfragmenten mogelijk te maken.

1. Klik op het AEM logo en navigeer naar **[!UICONTROL Tools > Deployment > Cloud Services]** .
1. Zoek **[!UICONTROL Translation Integration]** onder **[!UICONTROL Adobe Marketing Cloud]** en klik op **[!UICONTROL Show Configurations]** .

   ![ chlimage_1-444 ](assets/chlimage_1-444.png)

1. Klik in de lijst met beschikbare configuraties op **[!UICONTROL Default configuration (Translation Integration configuration)]** om de pagina **[!UICONTROL Default configuration]** te openen.

   ![ chlimage_1-445 ](assets/chlimage_1-445.png)

1. Klik op **[!UICONTROL Edit]** op de werkbalk om het dialoogvenster **[!UICONTROL Translation Config]** weer te geven.

   ![ chlimage_1-446 ](assets/chlimage_1-446.png)

1. Navigeer naar de tab **[!UICONTROL Assets]** en kies **[!UICONTROL Inline Media Assets and Associated Collections]** in de lijst **[!UICONTROL Translate Content Fragment Assets]** . Klik op **[!UICONTROL OK]** om de wijzigingen op te slaan.

   ![ chlimage_1-447 ](assets/chlimage_1-447.png)

1. Open vanuit de hoofdmap in het Engels een inhoudsfragment.

   ![ chlimage_1-448 ](assets/chlimage_1-448.png)

1. Klik op het pictogram **[!UICONTROL Insert Asset]** .

   ![ chlimage_1-449 ](assets/chlimage_1-449.png)

1. Voeg een element in het inhoudsfragment in.

   ![ neem binnen activa op aan inhoudsfragment ](assets/column-view.png)

1. Klik op het pictogram **[!UICONTROL Associate Content]** .

   ![ chlimage_1-451 ](assets/chlimage_1-451.png)

1. Klik op **[!UICONTROL Associate Content]**.

   ![ chlimage_1-452 ](assets/chlimage_1-452.png)

1. Selecteer een verzameling en neem deze op in het inhoudsfragment. Klik op **[!UICONTROL Save]**.

   ![ chlimage_1-453 ](assets/chlimage_1-453.png)

1. Selecteer het inhoudsfragment en klik op het pictogram **[!UICONTROL GlobalNav]** .
1. Selecteer **[!UICONTROL References]** in het menu om het deelvenster **[!UICONTROL References]** weer te geven.

   ![ chlimage_1-454 ](assets/chlimage_1-454.png)

1. Klik op **[!UICONTROL Language Copies]** onder **[!UICONTROL Copies]** om de taalkopieën weer te geven.

   ![ chlimage_1-455 ](assets/chlimage_1-455.png)

1. Klik onder in het deelvenster op **[!UICONTROL Create & Translate]** om het dialoogvenster **[!UICONTROL Create & Translate]** weer te geven.

   ![ chlimage_1-456 ](assets/chlimage_1-456.png)

1. Selecteer de doeltaal in de lijst **[!UICONTROL Target Languages]** .

   ![ chlimage_1-457 ](assets/chlimage_1-457.png)

1. Selecteer het type vertaalproject in de lijst **[!UICONTROL Project]** .

   ![ chlimage_1-458 ](assets/chlimage_1-458.png)

1. Specificeer de titel van het project in de **[!UICONTROL Project Title]** doos en klik dan **creeer**.

   ![ chlimage_1-459 ](assets/chlimage_1-459.png)

1. Navigeer naar de **[!UICONTROL Projects]** -console en open de projectmap voor het vertaalproject dat u hebt gemaakt.

   ![ chlimage_1-460 ](assets/chlimage_1-460.png)

1. Klik de projectegel om de pagina van projectdetails te openen.

   ![ chlimage_1-461 ](assets/chlimage_1-461.png)

1. Verifieer vanuit de tegel Vertaaltaak het aantal elementen dat moet worden vertaald.
1. Start de vertaaltaak vanaf de tegel **[!UICONTROL Translation Job]** .

   ![ chlimage_1-462 ](assets/chlimage_1-462.png)

1. Klik op de ovalen onder aan de tegel Vertaal-taak om de status van de vertaaltaak weer te geven.

   ![ chlimage_1-463 ](assets/chlimage_1-463.png)

1. Klik op het inhoudsfragment om het pad van de vertaalde gekoppelde elementen te controleren.

   ![ chlimage_1-464 ](assets/chlimage_1-464.png)

1. Herzie de taalexemplaar voor de inzameling in de console van Inzamelingen.

   ![ chlimage_1-465 ](assets/chlimage_1-465.png)

   U ziet dat alleen de inhoud van de verzameling wordt vertaald. De verzameling zelf is niet vertaald.

1. Navigeer naar het pad van het vertaalde gekoppelde element. Merk op dat het vertaalde element wordt opgeslagen onder de wortel van de doeltaal.

   ![ chlimage_1-466 ](assets/chlimage_1-466.png)

1. Navigeer naar de elementen in de verzameling die samen met het inhoudsfragment zijn vertaald. Merk op dat de vertaalde exemplaren van de activa bij de aangewezen doeltaalwortel worden opgeslagen.

   ![ chlimage_1-467 ](assets/chlimage_1-467.png)

   >[!NOTE]
   >
   >De procedures voor het toevoegen van een inhoudsfragment aan een bestaand project of voor het uitvoeren van updatewerkstromen zijn gelijkaardig aan de overeenkomstige procedures voor activa. Zie de voor activa beschreven procedures voor richtsnoeren over deze procedures.
