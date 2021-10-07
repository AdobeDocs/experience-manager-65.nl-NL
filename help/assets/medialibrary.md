---
title: Media Library gebruiken voor elementair beheer van digitale middelen
description: '[!DNL Experience Manager Assets] en Media Library voor middelenbeheer.'
contentOwner: AG
role: Architect, Leader
feature: Asset Management
exl-id: e10d632d-1d90-4f28-8617-95ee41602997
source-git-commit: 64ac790579db921aa16f32c51592f0b701237df9
workflow-type: tm+mt
source-wordcount: '531'
ht-degree: 0%

---


# Media Library gebruiken voor elementair beheer van bedrijfsmiddelen {#manage-assets-using-media-library}

[!DNL Adobe Experience Manager] platform biedt verschillende mogelijkheden om elementen te beheren. Met Media Library kunnen gebruikers een klein aantal elementen uploaden naar de opslagplaats, zoeken en gebruiken in de webpagina&#39;s en eenvoudige taken voor middelenbeheer uitvoeren op de middelen.

Media Library is een lichte DAM-oplossing (Digital Asset Management) die gratis wordt geleverd met een [!DNL Adobe Experience Manager Sites]-licentie. [!DNL Sites] is een Web Content Management (WCM)-aanbieding. Media Library werkt met alle mogelijkheden van Experience Manager.

[!DNL Adobe Experience Manager Assets] licentie is apart verkrijgbaar. [!DNL Experience Manager Assets] maakt een robuuste verwerking van bedrijfsmiddelen mogelijk via gevallen voor bedrijfsgebruik, aanpassingen voor metagegevens, schema&#39;s, zoekopdrachten en gebruikersinterface, en vele andere functies die verder gaan dan wat Media Library biedt.

## Vergunningsvereisten {#avail-media-library-license}

Klanten met een [!DNL Sites]-licentie hebben het recht om Media Library te gebruiken. Het werkt met alle componenten van [!DNL Experience Manager].

Media Library wordt geïnstalleerd als onderdeel van Sites. Naast de licentie en installatie van Sites is geen extra licentie of pakket vereist.

## [!DNL Assets] versus Media Library {#assets-and-media-library}

Experience Manager Assets biedt DAM-functionaliteit op bedrijfsniveau. Elementenfunctionaliteit wordt geleverd met [!DNL Experience Manager] in één pakket. Gebruikers die geen middelenlicentie hebben aangeschaft, hebben echter geen recht op het gebruik van de geavanceerde DAM-functies. Zonder middelenlicentie zijn alleen [Media Library-functies](#use-media-library) beschikbaar.

Als u onbedoeld gebruik van [!DNL Assets] eigenschappen wilt verhinderen die u geen vergunning hebt gegeven, dan verwijder alle [!DNL Assets]-specifieke werkschema&#39;s, componenten, taxonomieën, opties en [!DNL Assets] admin van [!DNL Experience Manager]. Zo voorkomt u dat uw gebruikers per ongeluk [!DNL Assets] functies gebruiken waarvoor u geen licentie hebt verleend.

## Media Library gebruiken {#use-media-library}

Media Library biedt standaard DAM-functies voor de volgende gebruiksgevallen:

* Webpagina&#39;s die zijn gemaakt met [!DNL Adobe Experience Manager Sites].
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

Als u de Media Library-functionaliteit wilt gebruiken, kunt u de standaardgebruikersinterface [!DNL Experience Manager] gebruiken. Media Library maakt deel uit van de [!DNL Experience Manager Sites]-installatie en er is geen aparte interface of invoegtoepassing vereist. Met behulp van de bestaande interface kunnen Media Library-gebruikers de volgende taken uitvoeren:

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
* Gebruik HTTP REST- en GraphQL API&#39;s voor [!DNL Content Fragments] en media-elementen waarnaar wordt verwezen, onder Sites-licentie.
* integratie van de Marketing Cloud.
* Gebruikersinterface voor middelenbeheer aanpassen en uitbreiden.
* Heb toegang tot de Bouwer van de Vraag (API) om de onderzoeksfunctionaliteit uit te breiden.
* Statische tags maken.

<!-- TBD: Define exactly which basic Assets workflow are available for use with Media Library?

As per PM, we must avoid stating such a list, as we don't have a list that makes sense in Cloud Service.
-->

>[!IMPORTANT]
>
>Veel geavanceerde DAM-gebruiksgevallen worden vervuld door [!DNL Experience Manager Assets]. Met Media Library-licentie kunt u alleen de vermelde gebruiksgevallen met Media Library afhandelen. Als een gebruiksgeval niet wordt vermeld, gebruik het niet met de vergunning van Media Library. Neem contact op met de Klantenondersteuning van Adobe als u vragen hebt.

Let op: u kunt geen slimme tags, [!DNL Asset]-koppeling, [!DNL Asset]-kiezer, bulksgewijs labelen, workflows van elementen wijzigen zonder [!DNL Assets]-licentie.

<!-- TBD: Add a CTA - how to contact Adobe for queries. -->

>[!MORELIKETHIS]
>
>* [DAM-functies in [!DNL Experience Manager Assets]](https://experienceleague.adobe.com/docs/experience-manager-65/assets/home.html)
>* [[!DNL Experience Manager] 6.5 Managed Services-productbeschrijving](https://helpx.adobe.com/legal/product-descriptions/adobe-experience-manager-managed-services.html)
>* [[!DNL Experience Manager] 6.5 Productbeschrijving op locatie](https://helpx.adobe.com/legal/product-descriptions/adobe-experience-manager-on-premise.html)

