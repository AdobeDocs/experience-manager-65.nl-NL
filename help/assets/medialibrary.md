---
title: Mediabibliotheek gebruiken voor elementair beheer van digitale elementen
description: '[!DNL Experience Manager Assets] en Mediabibliotheek voor middelenbeheer.'
contentOwner: AG
role: Architect, leider
translation-type: tm+mt
source-git-commit: 15c525746a613eb33cd09b7ff476f43aa18b146b
workflow-type: tm+mt
source-wordcount: '482'
ht-degree: 0%

---


<!--

Define Media Lib
Define req for it
Define use cases
Define what is not included

-->

# Mediabibliotheek gebruiken voor elementair middelenbeheer {#manage-assets-using-media-library}

[!DNL Adobe Experience Manager] platform biedt verschillende mogelijkheden om elementen te beheren. Met de mediabibliotheek kunnen gebruikers een klein aantal elementen uploaden naar de opslagplaats, zoeken en gebruiken in de webpagina&#39;s en eenvoudige taken uitvoeren voor middelenbeheer op de middelen.

Mediabibliotheek is een lichte DAM-oplossing (Digital Asset Management) die gratis wordt geleverd met een [!DNL Adobe Experience Manager Sites]-licentie. [!DNL Sites] is een Web Content Management (WCM)-aanbieding. Mediabibliotheek werkt met alle mogelijkheden van Experience Manager.

[!DNL Adobe Experience Manager Assets] licentie is apart verkrijgbaar. [!DNL Experience Manager Assets] maakt een robuuste verwerking van bedrijfsmiddelen mogelijk via de gebruiksscenario&#39;s van de onderneming, aanpassingen voor metagegevens, schema&#39;s, zoekopdrachten en gebruikersinterface, en vele andere functies die verder gaan dan de mediawisselaar.

## Licentievereisten {#avail-media-library-license}

Klanten met een [!DNL Sites]-licentie hebben het recht Mediabibliotheek te gebruiken. Het werkt met alle componenten van [!DNL Experience Manager].

De mediabibliotheek wordt geïnstalleerd als onderdeel van Sites. Naast de licentie en installatie van Sites is geen extra licentie of pakket vereist.

## [!DNL Assets] versus mediabibliotheek  {#assets-and-media-library}

Experience Manager Assets biedt DAM-functionaliteit op bedrijfsniveau. Elementenfunctionaliteit wordt geleverd met [!DNL Experience Manager] in één pakket. Gebruikers die geen middelenlicentie hebben aangeschaft, hebben echter geen recht op het gebruik van de geavanceerde DAM-functies. Zonder middelenlicentie zijn alleen [mediabibliotheekfuncties](#use-media-library) beschikbaar.

Als u onbedoeld gebruik van [!DNL Assets] eigenschappen wilt verhinderen die u geen vergunning hebt gegeven, dan verwijder alle [!DNL Assets]-specifieke werkschema&#39;s, componenten, taxonomieën, opties en [!DNL Assets] admin van [!DNL Experience Manager]. Zo voorkomt u dat uw gebruikers per ongeluk [!DNL Assets] functies gebruiken waarvoor u geen licentie hebt verleend.

## Mediabibliotheek {#use-media-library} gebruiken

De mediabibliotheek omvat in grote lijnen de volgende gebruiksgevallen:

* Basisfuncties voor DAM bieden voor webpagina&#39;s die zijn gemaakt met [!DNL Adobe Experience Manager Sites].
* Aangepaste formulieren en communicatie gemaakt met [!DNL Adobe Experience Manager Forms].
* Ervaringen met digitaal scherm die zijn gemaakt met [!DNL Adobe Experience Manager Screens].
* [!DNL Assets] HTTP REST-API&#39;s voor bewerkingen zonder kop.

<!-- TBD: Remove this after confirmation. May need to merge this list with the list provided by PMs.

* Basic metadata properties
* Tag management
* Version control
* Static renditions
* Projects, tasks, workflow authoring
* Activity stream (timeline)
* Query Builder (API)
* Marketing Cloud integration
* User interface customization and extension
* Comments and annotation
-->

Om de functionaliteit van de Bibliotheek van Media te gebruiken, kunt u het gebrek [!DNL Experience Manager] gebruikersinterface gebruiken. De Bibliotheek van media maakt deel uit van [!DNL Experience Manager Sites] installatie en geen afzonderlijke interface of toe:voegen-op wordt vereist. Met behulp van de bestaande interface hebben de gebruikers van de Mediabibliotheek het recht om de volgende taken uit te voeren:

* Maak mappen om elementen te ordenen.
* Elementen uploaden.
* Elementen publiceren.
* Elementen bewerken, verplaatsen en kopiëren.
* Blader naar de elementen die u wilt gebruiken, filter en zoek (inclusief zoeken op basis van gelijkenis).
* Voeg waarden toe aan en bewerk de waarden in de metagegevensvelden, behalve het veld Slimme tags, die standaard beschikbaar zijn op het tabblad [!UICONTROL Basic] van de pagina [!UICONTROL Properties] van een element.
* Statische vertoningen toevoegen en verwijderen.
* Download mappen, elementen en elementenuitvoeringen.
* Elementversies maken.
* Revisietaken voor elementen maken en uitvoeren.
* Annoteer elementen.
* Voeg elementen toe aan [!DNL Sites] pagina&#39;s via de Inhoudszoeker.
* Gebruik [!DNL Content Fragments].

<!-- TBD: Define exactly which basic Assets workflow are available for use with Media Library?
-->

>[!IMPORTANT]
>
>Veel geavanceerde DAM-gebruiksgevallen worden vervuld door [!DNL Experience Manager Assets]. Met de mediawisselaarlicentie kunt u alleen de vermelde gebruiksgevallen afhandelen via de mediawisselaar. Als een gebruiksgeval niet vermeld is, gebruik het niet met de vergunning van de Bibliotheek van Media. Neem contact op met de klantenservice van Adobe als u vragen hebt.

<!-- TBD: Add a CTA - how to contact Adobe for queries. -->

>[!MORELIKETHIS]
>
>* [DAM-functies in [!DNL Experience Manager Assets]](https://experienceleague.adobe.com/docs/experience-manager-65/assets/home.html)
>* [[!DNL Experience Manager] 6.5 Managed Services-productbeschrijving](https://helpx.adobe.com/legal/product-descriptions/adobe-experience-manager-managed-services.html)
>* [[!DNL Experience Manager] 6.5 Productbeschrijving op locatie](https://helpx.adobe.com/legal/product-descriptions/adobe-experience-manager-on-premise.html)

