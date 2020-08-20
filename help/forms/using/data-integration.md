---
title: AEM Forms-gegevensintegratie
seo-title: AEM Forms-gegevensintegratie
description: Met gegevensintegratie kunt u AEM Forms integreren met verschillende gegevensbronnen en een formuliergegevensmodel maken voor het maken en gebruiken van adaptieve formulieren en interactieve communicatie.
seo-description: Met gegevensintegratie kunt u AEM Forms integreren met verschillende gegevensbronnen en een formuliergegevensmodel maken voor het maken en gebruiken van adaptieve formulieren en interactieve communicatie.
uuid: 01df045e-1b26-437c-9674-fd223ecd5097
contentOwner: vishgupt
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: integration
discoiquuid: e397c6ce-d73f-4183-8445-1897a8906960
docset: aem65
translation-type: tm+mt
source-git-commit: 4e0709031aca030e50840811a9b3717f3cb20340
workflow-type: tm+mt
source-wordcount: '551'
ht-degree: 0%

---


# [!DNL AEM Forms] Gegevensintegratie {#aem-forms-data-integration}

![](do-not-localize/data-integeration.png)

De infrastructuur van de onderneming omvat verschillende back-end systemen of gegevensbronnen zoals gegevensbestanden, Webdiensten, de diensten van REST, de diensten van OData, en de oplossingen van CRM. Samengesteld, maken zij een informatiesysteem dat gegevens aan ondernemingstoepassingen dient om zaken van dag tot dag uit te voeren. Anderzijds leggen toepassingen gegevens vast en sturen deze terug naar bijgewerkte gegevensbronnen.

[!DNL AEM Forms] toepassingen zoals adaptieve formulieren en interactieve communicatie vereisen integratie met gegevensbronnen om klantgegevens op te halen tijdens het genereren van formulieren en het maken van interactieve communicatie. Er zijn gevallen waarin gegevens worden opgehaald uit gegevensbronnen die zijn gebaseerd op gebruikersinvoer in adaptieve formulieren. Bovendien kunnen de ingediende adaptieve formuliergegevens worden teruggeschreven om de respectieve gegevensbronnen bij te werken.

Terwijl een verdeeld, modulair systeem zijn eigen voordelen heeft, ligt de uitdaging in het integreren van en het creëren van gegevensverenigingen over gegevensbronnen. De integratie van gegevens is de sleutel tot een functionele en efficiënte ondernemingsinfrastructuur met verschillende gegevensbronnen verbonden aan toepassingen voor de uitwisseling van bedrijfsgegevens.

## Overzicht van gegevensintegratie {#data-integration-overview}

![aem-forms-data-integer](assets/aem-forms-data-integeration.png)

[!DNL AEM Forms] Met gegevensintegratie kunt u verschillende gegevensbronnen configureren en verbinden met [!DNL AEM Forms]. Het verstrekt een intuïtieve gebruikersinterface om een verenigd schema van de gegevensvertegenwoordiging van bedrijfsentiteiten en de diensten over verbonden gegevensbronnen tot stand te brengen. De verenigde vertegenwoordiging is genoemd geworden vormgegevensmodel, een uitbreiding van het schema JSON. De entiteiten in een formuliergegevensmodel worden gegevensmodelobjecten genoemd. Met een formuliergegevensmodel kunt u:

* Toegang tot gegevensmodelvoorwerpen, eigenschappen, en de diensten van verbonden gegevensbronnen.
* Objecten en eigenschappen van een aangepast gegevensmodel maken
* Bouw verenigingen tussen de voorwerpen van het gegevensmodel binnen en over gegevensbronnen.
* Roep gegevensmodelobjectservices aan om gegevens van en naar gegevensbronnen te zoeken of te schrijven.

Nadat u een formuliergegevensmodel hebt gemaakt, kunt u het gebruiken in verschillende adaptieve formulier- en interactieve communicatieworkflows, zoals:

* Aangepaste formulieren en interactieve communicatie maken op basis van het formuliergegevensmodel
* Aangepaste formulieren en interactieve communicatie vooraf invullen via geconfigureerde gegevensbronnen
* Gegevensbronservices/-bewerkingen aanroepen met behulp van adaptieve formulierregels
* Verzonden adaptieve formuliergegevens naar gegevensbronnen schrijven

## Aan de slag met gegevensintegratie {#get-started-with-data-integration}

De eerste stap voor het implementeren van gegevensintegratie is het identificeren en configureren van gegevensbronnen die informatie opslaan die u wilt gebruiken in adaptieve formulieren en interactieve-communicatietoepassingen. Vervolgens maakt u een formuliergegevensmodel dat gebruikmaakt van gegevensmodelobjecten, eigenschappen en services van een of meer gegevensbronnen. U kunt adaptieve formulieren en interactieve communicatie maken op basis van een formuliergegevensmodel waarin adaptieve formuliervelden of plaatsaanduidingen in interactieve communicatie zijn gebonden aan de desbetreffende gegevensbroneigenschappen.

[!DNL AEM Forms] Hiermee kunt u ook een formuliergegevensmodel maken dat onafhankelijk is van gegevensbronnen en kunt u later gegevensmodelobjecten en eigenschappen in het formuliergegevensmodel koppelen aan of binden met gegevensbron. Hiermee worden afhankelijkheden van gegevensbronnen verwijderd terwijl u werkt aan een formuliergegevensmodel.

Herzie het volgende om, gegevensintegratie te beginnen te begrijpen en uit te voeren.

* [Gegevensbronnen configureren](../../forms/using/configure-data-sources.md)
* [Formuliergegevensmodel maken](../../forms/using/create-form-data-models.md)
* [Werken met formuliergegevensmodel](../../forms/using/work-with-form-data-model.md)
* [Formuliergegevensmodel gebruiken](../../forms/using/using-form-data-model.md)

