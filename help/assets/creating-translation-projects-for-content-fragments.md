---
title: Vertaalprojecten maken voor inhoudsfragmenten
seo-title: Vertaalprojecten maken voor inhoudsfragmenten
description: Leer hoe u inhoudsfragmenten vertaalt.
seo-description: Leer hoe u inhoudsfragmenten vertaalt.
uuid: 23176e70-4003-453c-af25-6499a5ed3f6d
contentOwner: heimoz
products: SG_EXPERIENCEMANAGER/6.5/ASSETS
topic-tags: managing-assets
content-type: reference
discoiquuid: d2decc31-a04b-4a8e-bb19-65f21cf7107e
translation-type: tm+mt
source-git-commit: 48fd5ddb386d69795291e560fa7b21da6edf5979

---


# Vertaalprojecten maken voor inhoudsfragmenten {#creating-translation-projects-for-content-fragments}

Naast elementen ondersteunt AEM-middelen (Adobe Experience Manager) workflows voor het kopiëren van talen voor [inhoudsfragmenten](content-fragments.md) (inclusief variaties). Er is geen extra optimalisatie vereist voor het uitvoeren van workflows voor het kopiëren van talen op inhoudsfragmenten. In elke werkstroom wordt het volledige inhoudsfragment verzonden voor vertaling.

De typen workflows die u op inhoudsfragmenten kunt uitvoeren, lijken precies op de typen werkstromen die u voor elementen uitvoert. Bovendien komen de opties die beschikbaar zijn binnen elk workflowtype overeen met de opties die beschikbaar zijn onder de corresponderende workflowtypen voor elementen.

U kunt de volgende typen werkstromen voor het kopiëren van talen uitvoeren op inhoudsfragmenten:

**Maken en vertalen**

In deze workflow worden inhoudsfragmenten die moeten worden vertaald, gekopieerd naar de hoofdmap van de taal waarnaar u wilt vertalen. Bovendien wordt, afhankelijk van de opties u kiest, een vertaalproject gecreeerd voor de inhoudsfragmenten in de console van Projecten. Afhankelijk van de instellingen kan het vertaalproject handmatig worden gestart of automatisch worden uitgevoerd zodra het vertaalproject is gemaakt.

**Taalkopieën bijwerken**

Wanneer het broninhoudsfragment wordt bijgewerkt of gewijzigd, moet het bijbehorende taalspecifieke inhoudsfragment opnieuw worden vertaald. De workflow voor het kopiëren van de updatetaal zet een extra groep inhoudsfragmenten om en neemt deze op in een taalkopie voor een bepaalde landinstelling. In dit geval worden de vertaalde inhoudsfragmenten toegevoegd aan de doelmap die al eerder vertaalde inhoudsfragmenten bevat.

## Workflow maken en vertalen {#create-and-translate-workflow}

De workflow Maken en vertalen bevat de volgende opties. De procedurele stappen die aan elke optie zijn gekoppeld, zijn vergelijkbaar met die welke aan de overeenkomstige optie voor activa zijn gekoppeld.

* Alleen structuur maken: Zie Structuur alleen [maken voor elementen](translation-projects.md#create-structure-only)voor procedurestappen.
* Een nieuw vertaalproject maken: Zie Een nieuw vertaalproject [maken voor elementen](translation-projects.md#create-a-new-translation-project)voor procedurestappen.
* Toevoegen aan bestaand vertaalproject: Voor procedurestappen, zie [toevoegen aan bestaand vertaalproject voor activa](translation-projects.md#add-to-existing-translation-project).

## Workflow voor het kopiëren van talen bijwerken {#update-language-copies-workflow}

De workflow voor het kopiëren van de taal Bijwerken bevat de volgende opties. De procedurele stappen die aan elke optie zijn gekoppeld, zijn vergelijkbaar met die welke aan de overeenkomstige optie voor activa zijn gekoppeld.

* Een nieuw vertaalproject maken: Zie [Een nieuw vertaalproject voor elementen](translation-projects.md#create-a-new-translation-project) maken (updateworkflow) voor procedurestappen.
* Toevoegen aan bestaand vertaalproject: Zie [Toevoegen aan bestaand vertaalproject voor elementen](translation-projects.md#add-to-existing-translation-project) (update-workflow) voor procedurestappen.

U kunt ook tijdelijke-taalkopieën maken voor fragmenten, vergelijkbaar met de manier waarop u tijdelijke kopieën maakt voor elementen. Zie [Tijdelijke taalkopieën maken voor elementen](translation-projects.md#creating-temporary-language-copies)voor meer informatie.

## Gemengde-mediafragmenten omzetten {#translating-mixed-media-fragments}

Met AEM kunt u inhoudsfragmenten vertalen die verschillende typen media-elementen en -verzamelingen bevatten. Als u een inhoudsfragment vertaalt dat inline-elementen bevat, worden de vertaalde kopieën van deze elementen opgeslagen onder de hoofdmap van de doeltaal.

Als het inhoudsfragment een verzameling bevat, worden de elementen in de verzameling samen met het inhoudsfragment vertaald. De vertaalde exemplaren van de activa worden opgeslagen binnen de aangewezen wortel van de doeltaal bij een plaats die de fysieke plaats van de bronactiva onder de wortel van de brontaal aanpast.

Als u inhoudsfragmenten met gemengde media wilt kunnen vertalen, bewerkt u eerst het standaardvertaalframework om de vertaling van inline-elementen en -verzamelingen met betrekking tot inhoudsfragmenten mogelijk te maken.

1. Klik op of tik op het AEM-logo en navigeer naar **[!UICONTROL Extra > Implementatie > Cloud Services]**.
1. Zoek de **[!UICONTROL vertaalintegratie]** onder **[!UICONTROL Adobe Marketing Cloud]** en klik/tik op **[!UICONTROL Configuraties]** tonen.

   ![chlimage_1-444](assets/chlimage_1-444.png)

1. Klik in de lijst met beschikbare configuraties op **[!UICONTROL Standaardconfiguratie (configuratie vertaalintegratie)]** of tik hierop om de pagina **[!UICONTROL Standaardconfiguratie]** te openen.

   ![chlimage_1-445](assets/chlimage_1-445.png)

1. Klik op **[!UICONTROL Bewerken]** op de werkbalk om het dialoogvenster **[!UICONTROL Vertaalconfiguratie]** weer te geven.

   ![chlimage_1-446](assets/chlimage_1-446.png)

1. Navigeer naar het tabblad **[!UICONTROL Middelen]** en kies **[!UICONTROL Inline-media-elementen en bijbehorende verzamelingen]** in de lijst Elementen **[!UICONTROL van]** inhoudsfragment omzetten. Klik op **[!UICONTROL OK]** of tik op OK om de wijzigingen op te slaan.

   ![chlimage_1-447](assets/chlimage_1-447.png)

1. Open vanuit de hoofdmap in het Engels een inhoudsfragment.

   ![chlimage_1-448](assets/chlimage_1-448.png)

1. Klik op het pictogram Element **** invoegen of tik erop.

   ![chlimage_1-449](assets/chlimage_1-449.png)

1. Voeg een element in het inhoudsfragment in.

   ![element invoegen in inhoudsfragment](assets/column-view.png)

1. Klik op het pictogram **[!UICONTROL Inhoud]** koppelen of tik erop.

   ![chlimage_1-451](assets/chlimage_1-451.png)

1. Klik/tik op Inhoud **[!UICONTROL koppelen]**.

   ![chlimage_1-452](assets/chlimage_1-452.png)

1. Selecteer een verzameling en neem deze op in het inhoudsfragment. Klik op **[!UICONTROL Opslaan]** of tik op Opslaan.

   ![chlimage_1-453](assets/chlimage_1-453.png)

1. Selecteer het inhoudsfragment en klik/tik op het pictogram **[!UICONTROL GlobalNav]** .
1. Selecteer **[!UICONTROL Verwijzingen]** in het menu om het deelvenster **[!UICONTROL Verwijzingen]** weer te geven.

   ![chlimage_1-454](assets/chlimage_1-454.png)

1. Klik/tik **[!UICONTROL Exemplaren]** van de Taal onder **[!UICONTROL Exemplaren]** om de taalexemplaren te tonen.

   ![chlimage_1-455](assets/chlimage_1-455.png)

1. Klik op **[!UICONTROL Maken en vertalen]** onder in het deelvenster om het dialoogvenster **[!UICONTROL Maken en vertalen]** weer te geven.

   ![chlimage_1-456](assets/chlimage_1-456.png)

1. Selecteer de doeltaal in de lijst **[!UICONTROL Doeltalen]** .

   ![chlimage_1-457](assets/chlimage_1-457.png)

1. Selecteer het type vertaalproject in de lijst **[!UICONTROL Project]** .

   ![chlimage_1-458](assets/chlimage_1-458.png)

1. Geef de titel van het project op in het vak **[!UICONTROL Projecttitel]** en klik of tik op **Maken**.

   ![chlimage_1-459](assets/chlimage_1-459.png)

1. Navigeer aan de console van **[!UICONTROL Projecten]** , en open de projectomslag voor het vertaalproject u creeerde.

   ![chlimage_1-460](assets/chlimage_1-460.png)

1. Klik of tik op de projecttegel om de pagina met projectdetails te openen.

   ![chlimage_1-461](assets/chlimage_1-461.png)

1. Verifieer vanuit de tegel Vertaaltaak het aantal te vertalen middelen.
1. Start de vertaaltaak vanaf het **[!UICONTROL onderdeel Vertaaltaak]** .

   ![chlimage_1-461](assets/chlimage_1-462.png)

1. Klik op de ovalen onder aan de tegel Vertaal-taak om de status van de vertaaltaak weer te geven.

   ![chlimage_1-463](assets/chlimage_1-463.png)

1. Klik of tik op het inhoudsfragment om het pad van de vertaalde gekoppelde elementen te controleren.

   ![chlimage_1-464](assets/chlimage_1-464.png)

1. Herzie de taalexemplaar voor de inzameling in de console van Inzamelingen.

   ![chlimage_1-465](assets/chlimage_1-465.png)

   U ziet dat alleen de inhoud van de verzameling wordt vertaald. De verzameling zelf is niet vertaald.

1. Navigeer naar het pad van het vertaalde gekoppelde element. Merk op dat het vertaalde element wordt opgeslagen onder de wortel van de doeltaal.

   ![chlimage_1-466](assets/chlimage_1-466.png)

1. Navigeer naar de elementen in de verzameling die samen met het inhoudsfragment zijn vertaald. Merk op dat de vertaalde exemplaren van de activa bij de aangewezen doeltaalwortel worden opgeslagen.

   ![chlimage_1-468](assets/chlimage_1-467.png)

   >[!NOTE]
   >
   >De procedures voor het toevoegen van een inhoudsfragment aan een bestaand project of voor het uitvoeren van updatewerkstromen zijn gelijkaardig aan de overeenkomstige procedures voor activa. Zie voor leidraden voor deze procedures de voor activa beschreven procedures.

