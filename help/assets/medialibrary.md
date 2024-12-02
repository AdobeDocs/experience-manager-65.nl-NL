---
title: Media Library gebruiken voor elementair beheer van digitale middelen
description: '[!DNL Experience Manager Assets] en Media Library voor middelenbeheer.'
contentOwner: AG
role: Architect, Leader
feature: Asset Management
exl-id: e10d632d-1d90-4f28-8617-95ee41602997
hide: true
solution: Experience Manager, Experience Manager Assets
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '553'
ht-degree: 0%

---


# Media Library gebruiken voor elementair middelenbeheer {#manage-assets-using-media-library}

| Versie | Artikelkoppeling |
| -------- | ---------------------------- |
| AEM as a Cloud Service | [ klik hier ](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/assets/admin/medialibrary.html?lang=en) |
| AEM 6,5 | Dit artikel |

[!DNL Adobe Experience Manager] biedt verschillende mogelijkheden om elementen te beheren. Met Media Library kunnen gebruikers een klein aantal elementen uploaden naar de opslagplaats, zoeken en gebruiken in de webpagina&#39;s en eenvoudige taken voor middelenbeheer uitvoeren op de middelen.

Media Library is een lichte DAM-oplossing (Digital Asset Management) die gratis wordt geleverd met [!DNL Adobe Experience Manager Sites] -licentie. [!DNL Sites] is een WCM-service (Web Content Management). Media Library werkt met alle mogelijkheden van Experience Manager.

[!DNL Adobe Experience Manager Assets] -licentie is apart verkrijgbaar. [!DNL Experience Manager Assets] biedt een robuuste verwerking van bedrijfsmiddelen via praktijkgevallen, aanpassingen voor metagegevens, schema&#39;s, zoekopdrachten en gebruikersinterface en vele andere functies die verder gaan dan Media Library biedt.

## Vergunningsvereisten {#avail-media-library-license}

Klanten met een [!DNL Sites] -licentie hebben het recht om Media Library te gebruiken. Het werkt met alle componenten van [!DNL Experience Manager].

Media Library wordt geïnstalleerd als onderdeel van Sites. Naast de licentie en installatie van Sites is geen extra licentie of pakket vereist.

## [!DNL Assets] versus Media Library {#assets-and-media-library}

Experience Manager Assets biedt DAM-functionaliteit op bedrijfsniveau. Assets-functionaliteit wordt geleverd met [!DNL Experience Manager] in één pakket. Gebruikers die geen Assets-licentie hebben aangeschaft, mogen de geavanceerde DAM-functies echter niet gebruiken. Zonder de vergunning van Assets, slechts zijn de [ eigenschappen van Media Library ](#use-media-library) beschikbaar.

Als u wilt voorkomen dat [!DNL Assets] -functies waarvoor u geen licentie hebt, onbedoeld worden gebruikt, verwijdert u alle [!DNL Assets] -specifieke workflows, componenten, taxonomieën, opties en de [!DNL Assets] -beheerder uit [!DNL Experience Manager] . Zo voorkomt u dat uw gebruikers per ongeluk [!DNL Assets] -functies gebruiken waarvoor u geen licentie hebt verleend.

## Media Library gebruiken {#use-media-library}

Media Library biedt standaard DAM-functies voor de volgende gebruiksgevallen:

* Webpagina&#39;s die zijn gemaakt met [!DNL Adobe Experience Manager Sites] .
* Adaptieve formulieren en communicatie die zijn gemaakt met [!DNL Adobe Experience Manager Forms] .
* Ervaring met digitaal scherm die is gemaakt met [!DNL Adobe Experience Manager Screens] .
* [!DNL Assets] HTTP REST-API&#39;s voor bewerkingen zonder kop.

<!--
 TBD: Remove this after confirmation. May need to merge this list with the list provided by PMs.
* Static renditions

-->

Als u de Media Library-functionaliteit wilt gebruiken, kunt u de standaardgebruikersinterface van [!DNL Experience Manager] gebruiken. Media Library maakt deel uit van de installatie van [!DNL Experience Manager Sites] en er is geen aparte interface of invoegtoepassing vereist. Met behulp van de bestaande interface kunnen Media Library-gebruikers de volgende taken uitvoeren:

* Maak mappen om elementen te ordenen.
* Elementen uploaden.
* Publish assets.
* Elementen bewerken, verplaatsen en kopiëren.
* Blader naar de elementen die u wilt gebruiken, filter en zoek (inclusief zoeken op basis van gelijkenis).
* Voeg waarden toe aan en bewerk de waarden in de metagegevensvelden, behalve het veld Slimme tags, die standaard beschikbaar zijn op het tabblad [!UICONTROL Basic] van de pagina [!UICONTROL Properties] van een element.
* Statische vertoningen toevoegen en verwijderen.
* Download mappen, elementen en elementenuitvoeringen.
* Elementversies maken.
* Revisietaken voor elementen maken en uitvoeren.
* Annoteer elementen.
* Voeg elementen aan [!DNL Sites] pagina&#39;s toe via de Inhoudszoeker.
* Gebruik [!DNL Content Fragments] .
* Gebruik HTTP REST- en GraphQL-API&#39;s voor [!DNL Content Fragments] en media-elementen waarnaar wordt verwezen, onder Sites-licentie.
* integratie van de Marketing Cloud.
* Gebruikersinterface voor middelenbeheer aanpassen en uitbreiden.
* Heb toegang tot de Bouwer van de Vraag (API) om de onderzoeksfunctionaliteit uit te breiden.
* Statische tags maken.
* Projecten en taken van auteurs.
* Activiteitsstroom (tijdlijn).
* Opmerkingen en annotaties.

<!-- TBD: Define exactly which basic Assets workflow are available for use with Media Library?

As per PM, we must avoid stating such a list, as we do not have a list that makes sense in Cloud Service.
-->

>[!IMPORTANT]
>
>Vele geavanceerde gevallen van gebruik door DAM worden vervuld door [!DNL Experience Manager Assets]. Met Media Library-licentie kunt u alleen de vermelde gebruiksgevallen met Media Library afhandelen. Als een gebruiksgeval niet wordt vermeld, gebruik het niet met de vergunning van Media Library. Neem contact op met de Klantenondersteuning van de Adobe als u vragen hebt.

U kunt geen slimme tags, [!DNL Asset] koppelingen, [!DNL Asset] kiezer, bulksgewijs labelen, workflows van elementen of de standaard [!DNL Adobe Experience Manager] gebruikersinterface gebruiken om Media Library te openen zonder [!DNL Assets] licentie.

<!-- TBD: Add a CTA - how to contact Adobe for queries. -->

>[!MORELIKETHIS]
>
>* [ DAM eigenschappen in  [!DNL Experience Manager Assets] ](https://experienceleague.adobe.com/docs/experience-manager-65/assets/home.html)
>* [[!DNL Experience Manager]  6.5 het productbeschrijving van Managed Services ](https://helpx.adobe.com/legal/product-descriptions/adobe-experience-manager-managed-services.html)
>* [[!DNL Experience Manager]  6.5 on-premise productbeschrijving ](https://helpx.adobe.com/legal/product-descriptions/adobe-experience-manager-on-premise.html)
