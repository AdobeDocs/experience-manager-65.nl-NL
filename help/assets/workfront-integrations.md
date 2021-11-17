---
title: '[!DNL Experience Manager Assets] integration with [!DNL Adobe Workfront]'
description: Inleiding tot integratie tussen [!DNL Assets] en [!DNL Workfront]
role: Admin,Leader,Architect
feature: Integrations
source-git-commit: 468a8d96153c67232524eea6f180c9ceb364d60a
workflow-type: tm+mt
source-wordcount: '966'
ht-degree: 1%

---


# [!DNL Adobe Experience Manager Assets] integratie met [!DNL Adobe Workfront] {#assets-integration-overview}

[!DNL Adobe Workfront] is een werkbeheertoepassing waarmee u de volledige levenscyclus van het werk op één locatie kunt beheren. De integratie tussen [!DNL Workfront] en [!DNL Adobe Experience Manager Assets] kunnen organisaties de snelheid van de inhoud en de tijd-aan-markt verbeteren door het werk en het beheer van digitale activa intrinsiek met elkaar te verbinden. In het kader van het beheer van hun werk in Workfront hebben gebruikers toegang tot de vereiste documenten en afbeeldingen.

Adobe biedt twee verschillende schakelaars aan om beide oplossingen te integreren. De schakelaars laten complexe ondernemingsautomatisering, configuratie, en verlengbare werkschema&#39;s tussen toe [!DNL Assets] en [!DNL Workfront]. Daarnaast [!DNL Assets Essentials] is beschikbaar als een invoegtoepassing die nieuw is [!DNL Workfront] klanten kunnen afzonderlijk aanschaffen. Zie voor meer informatie [[!DNL Workfront] and [!DNL Assets Essentials] integratie](https://experienceleague.adobe.com/docs/experience-manager-assets-essentials/help/integration.html).

[!DNL Workfront for Experience Manage enhanced connector] stelt uw organisatie in staat om:

* Eenvoudig samenwerken. Creatieve teams kunnen zich minder zorgen maken. Wanneer het werk klaar is, kunnen ze het met een klik op een knop naar AEM Assets sturen
* Verrijk elementen bij elke stap. Verzamel nieuwe gegevens in elke fase van de levenscyclus van het element. Van ideatie tot levering, kan uw organisatie zeer belangrijke metriek vangen om meer geïnformeerde bedrijfsbesluiten over toekomstige activaontwikkeling te nemen.
* Verwijzing naar bestaande activa. Zoek en hergebruik eenvoudig bestaande middelen in productie en voeg deze toe aan nieuwe projecten als referentie-items.
* Synchroniseer al uw metagegevens. Verbeter uw metagegevens door het toevoegen zo eenvoudig mogelijk te maken. Met de connector worden metagegevens bidirectioneel gesynchroniseerd tussen Workfront en AEM Assets
* Hefboomwerking [!DNL Experience Manager Assets] mogelijkheden voor digitaal beheer. Toegang tot al uw digitale middelen rechtstreeks in uw favoriet [!DNL Creative Cloud] toepassingen. Slim labelen en uitsnijden met AI-functies, zoekgereedschappen, dynamische weergave via [!DNL Dynamic Media]en nog veel meer.

Raadpleeg de platformondersteuning en andere [eerste vereisten voor de verbeterde aansluiting](https://one.workfront.com/s/csh?context=2467&amp;pubname=the-new-workfront-experience).

>[!IMPORTANT]
>
>Adobe vereist plaatsing en configuratie van [!DNL Adobe Workfront for Experience Manager enhanced connector] alleen via gecertificeerde partners of [!DNL Adobe Professional Services]. Indien opgesteld en gevormd zonder een verklaarde partner of [!DNL Adobe Professional Services], wordt deze niet ondersteund door Adobe.
>
>Adobe kan updates voor [!DNL Adobe Workfront] en [!DNL Adobe Experience Manager] dat deze schakelaar overtollig maakt; als dit voorkomt, kunnen de klanten worden vereist om van het gebruik van deze schakelaar over te gaan.

## Verschillende integraties vergelijken tussen [!DNL Assets] en [!DNL Workfront] {#feature-parity-matrix}

Hieronder volgen de details van de functies die beschikbaar zijn via verschillende soorten integratie tussen [!DNL Assets] en [!DNL Workfront].

| Functie | Beschrijving | [!DNL Workfront] and [!DNL Assets Essentials] | [!DNL Workfront] for [!DNL Experience Manager] connector | [!DNL Workfront for Experience Manager enhanced connector] |
|----|----|----|------|-----|
| Implementatiemethoden | Geschikt voor [!DNL Assets] aanbieden. | Assets Essentials | Cloud Service, beheerde services van Adobe, op locatie | Cloud Service, beheerde services van Adobe, op locatie |
| Digitale bestanden verzenden vanuit [!DNL Workfront] tot [!DNL Assets] | De nieuwste versie van een WF-document kan worden geüpload naar AEM Assets, dat als een nieuwe versie van het document wordt gekoppeld. | ✓ | ✓ | ✓ |
| Mappen handmatig koppelen AEM aan Workfront-objecten | Bestaande AEM mappen kunnen worden gekoppeld als een Workfront-map en de onderliggende elementen ervan worden gekoppeld als nieuwe Workfront-documenten. | ✓ | ✓ | ✓ |
| Koppeling [!DNL Assets] naar Workfront-objecten | Bestaande elementen in AEM kunnen worden gekoppeld aan een nieuw Workfront-document of als een nieuwe versie van een bestaand document. | ✓ | ✓ | ✓ |
| Middelen die aan gekoppelde mappen worden toegevoegd, worden automatisch naar AEM verzonden | Als het document wordt toegevoegd aan een gekoppelde map, wordt het bijbehorende element automatisch geüpload naar AEM Assets als een nieuw element. | ✓ | ✓ | ✓ |
| Gekoppelde AEM Assets downloaden vanuit Workfront | Wanneer een element in Workfront is gekoppeld, kan de gebruiker de bytes van het element downloaden. | ✓ | ✓ | ✓ |
| Zoeken naar AEM Assets vanuit Workfront | Met de AEM Assets-kiezer in Workfront kunt u zoeken in volledige tekst naar elementen. | ✓ | ✓ | ✓ |
| AEM maphiërarchie weergeven en navigeren vanuit Workfront | Met de AEM Assets-kiezer in Workfront kan door de AEM Assets-hiërarchie worden gebladerd. Dit wordt beperkt door de toegangsbesturingselementen en machtigingen die de gebruiker in AEM heeft ingesteld. | ✓ | ✓ | ✓ |
| Middelen ontkoppelen van AEM Assets in Workfront | Een bestaand gekoppeld element van AEM kan worden losgekoppeld van het bijbehorende Workfront-document. Hierdoor wordt het oorspronkelijke element in AEM niet verwijderd. | ✓ | ✓ | ✓ |
| Nieuw versioned element toevoegen aan AEM Assets vanuit Workfront | Wanneer een nieuw toegevoegde versie aan een document in Workfront wordt toegevoegd, kan een gebruiker de nieuwe versie naar AEM sturen om de bestaande versie te vervangen. | ✓ | ✓ | ✓ |
| In Workfront gekoppelde middelen wanneer op Direct door gebruiker AEM wordt geklikt | Gebruikers worden doorgestuurd naar AEM om een voorvertoning van een gekoppeld element weer te geven vanuit Workfront. | ✓ | ✓ | Aangepast |
| Automatisch gekoppelde AEM mappen maken in Workfront | Maak automatisch gekoppelde AEM mappen in Workfront met objectstatussen. Organiseer automatisch AEM mappen op basis van Workfront-Portfolio, -programma&#39;s en -projecten. | Nee | Nee | ✓ |
| Commentaar synchroniseren | Automatisch opmerkingen synchroniseren voor elementen van [!DNL Workfront] tot [!DNL Assets] | Nee | ✓ | ✓ |
| Metagegevens Workfront-element toewijzen aan AEM Assets | Workfront-object en aangepaste formuliereigenschappen kunnen worden toegewezen aan AEM eigenschappen van metagegevens van elementen. Waarden worden geduwd op eerste upload/verbinding. | ✓ | ✓ | ✓ |
| Automatisch aangepaste Forms voor documenten maken in Workfront | Voeg aangepaste formulieren toe aan Workfront-documenten, -taken en -problemen met behulp van AEM workflows. | Nee | Voeg handmatig het aangepaste formulier toe en synchroniseer vervolgens automatisch | ✓ |
| Automatisch in twee richtingen bijwerken van metagegevens tussen AEM Assets en Workfront | Metagegevens automatisch bijwerken tussen AEM Assets en Workfront. | Nee | ✓ | ✓ |
| Workfront-metagegevens toewijzen aan AEM Assets-mappen | Metagegevens van Workfront-projecten synchroniseren met gekoppelde AEM. | Nee | Nee | ✓ |
| Metagegevensupdates AEM met nieuwe versies | U kunt een configuratie in AEM maken om te bepalen of een nieuw versioned element in Workfront ook wijzigingen in de metagegevens doorvoert. | Nee | Nee | ✓ |
| AEM metagegevens automatisch bijwerken bij wijzigingen in Aangepast Forms in Workfront | Workfront is zodanig geconfigureerd dat de opgegeven eigenschappen van metagegevens van AEM elementen worden toegewezen aan een aangepast document. Wanneer een element voor het eerst wordt gekoppeld of wanneer een element wordt bijgewerkt, worden de waarden van deze metagegevenseigenschappen gekopieerd naar het overeenkomstige aangepaste formulierveld van het Workfront-document. Er moet op worden toegezien dat de AEM niet naar AEM worden teruggestuurd alsof het een wijziging betreft die in Workfront is ontstaan. | Nee | ✓ | ✓ |
| Nieuwe proefversie maken op gekoppelde elementen | Na het koppelen van een element in Workfront kan automatisch een bewijs worden gegenereerd. | Nee | ✓ | Aangepast |
| Status instellen voor Workfront-objecten | Workfront-objectstatussen instellen op basis van configureerbare voorwaarden met behulp van AEM workflows | Nee | Nee | ✓ |
| Middelen publiceren naar AEM Publish Environment of Brand Portal | Workfront-gebruikers de optie geven om gekoppelde elementen automatisch te publiceren naar een AEM-publicatieomgeving of Brand Portal. | Nee | Nee | ✓ |
