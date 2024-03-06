---
title: '[!DNL Experience Manager Assets] integratie met [!DNL Adobe Workfront]'
description: Inleiding tot integratie tussen [!DNL Assets] en [!DNL Workfront]
role: Admin,Leader,Architect
feature: Integrations
exl-id: 57e2bffe-8094-4557-99c8-7b482681687e
hide: true
source-git-commit: 0aa929021aa724e4ec18d49fea26f8c0b0538bdc
workflow-type: tm+mt
source-wordcount: '1174'
ht-degree: 0%

---

# [!DNL Adobe Experience Manager Assets] integratie met [!DNL Adobe Workfront] {#assets-integration-overview}

| Versie | Artikelkoppeling |
| -------- | ---------------------------- |
| AEM as a Cloud Service | [Klik hier](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/assets/integrations/workfront-integrations.html?lang=en) |
| AEM 6,5 | Dit artikel |

[!DNL Adobe Workfront] is een werkbeheertoepassing waarmee u de volledige levenscyclus van het werk op één locatie kunt beheren. De integratie tussen [!DNL Workfront] en [!DNL Adobe Experience Manager Assets] kunnen organisaties de snelheid van de inhoud en de tijd-aan-markt verbeteren door het werk en het beheer van digitale activa intrinsiek met elkaar te verbinden. In het kader van het beheer van hun werk in Workfront hebben gebruikers toegang tot de vereiste documenten en afbeeldingen.

De [!DNL Workfront for Experience Manager enhanced connector] maakt verbeterde bedrijfsprocessen mogelijk met end-to-end workflows en biedt gepersonaliseerde end-to-end clientervaringen en centrale opslag. De Adobe biedt een standaardschakelaar en een verbeterde schakelaar aan om de twee oplossingen te integreren. Zie de ondersteunde functies hieronder voor een vergelijking en zie [wat nieuw is in de [!DNL enhanced connector]](https://one.workfront.com/s/csh?context=2467&amp;pubname=the-new-workfront-experience).

[!DNL Workfront for Experience Manage enhanced connector] stelt uw organisatie in staat om:

* Maak automatisch gekoppelde mappen voor Experience Managers in Workfront en deel de mappen in op basis van Workfront-Portfolio&#39;s, -programma&#39;s en -projecten.
* Metagegevens van Workfront-projecten synchroniseren met mappen voor gekoppelde Experience Managers.
* Metagegevens van de Experience Manager worden bijgewerkt met nieuwe versies.
* Stel Workfront-objectstatussen in op basis van configureerbare omstandigheden met behulp van workflows voor Experience Managers.
* Publiceer elementen naar de publicatieomgeving van de Experience Manager of naar Brand Portal.

Raadpleeg de platformondersteuning en [eerste vereisten voor de verbeterde aansluiting](https://one.workfront.com/s/csh?context=2467&amp;pubname=the-new-workfront-experience).

>[!IMPORTANT]
>
>* Adobe vereist implementatie en configuratie van de [!DNL Adobe Workfront for Experience Manager enhanced connector] alleen via gecertificeerde partners of [!DNL Adobe Professional Services]. Indien opgesteld en gevormd zonder een verklaarde partner of [!DNL Adobe Professional Services], wordt het niet ondersteund door Adobe.
>
>* Adobe kan updates vrijgeven voor [!DNL Adobe Workfront] en [!DNL Adobe Experience Manager] die deze schakelaar overtollig maken; als dit voorkomt, kunnen de klanten aan overgang van het gebruik van deze schakelaar worden vereist.
>
>* Adobe ondersteunt verbeterde connectorversies 1.7.4 en hoger. Eerdere pre-release en aangepaste versies worden niet ondersteund. Navigeer naar de `digital.hoodoo` groep beschikbaar in het linkerdeelvenster in [Pakketbeheer](https://experienceleague.adobe.com/docs/experience-manager-65/administering/contentmanagement/package-manager.html?lang=en).
>
>* Zie [Partnercertificatieexamen voor Workfront voor verbeterde connector voor Experience Manager Assets](https://solutionpartners.adobe.com/solution-partners/home/applications/experience_cloud/workfront/journey/dev_core.html). Voor informatie over het examen, zie [Handleiding voor Examen](https://express.adobe.com/page/Tc7Mq6zLbPFy8/).

## Verschillende integraties vergelijken tussen [!DNL Assets] en [!DNL Workfront] {#feature-parity-matrix}

Hieronder volgen de details van de functies die beschikbaar zijn via verschillende soorten integratie tussen [!DNL Assets] en [!DNL Workfront].

| Functie | Beschrijving | [!DNL Workfront] en [!DNL Assets Essentials] *Geen aansluiting (buiten de box)* | [!DNL Workfront for Experience Manager enhanced connector] *Vereist connector* | Workfront en [!DNL Experience Manager as a Cloud Service] *Geen aansluiting (buiten de box)* |
|----|----|----|-----|-----|
| Implementatiemethoden | Geschikt voor [!DNL Assets] aanbieden. | Assets Essentials | Adobe Managed Services, op locatie | Cloud Service |
| **Algemeen** |
| Digitale bestanden verzenden vanuit [!DNL Workfront] tot [!DNL Assets] | De nieuwste versie van een WF-document kan worden geüpload naar AEM Assets, dat is gekoppeld als een nieuwe versie van het document. | ✓ | ✓ | ✓ |
| Mappen handmatig koppelen AEM aan Workfront-objecten | Bestaande AEM mappen kunnen worden gekoppeld als een Workfront-map en de onderliggende elementen ervan worden gekoppeld als nieuwe Workfront-documenten. | ✓ | ✓ | ✓ |
| Koppeling [!DNL Assets] naar Workfront-objecten | Bestaande elementen in AEM kunnen worden gekoppeld aan een nieuw Workfront-document of als een nieuwe versie van een bestaand document. | ✓ | ✓ | ✓ |
| Middelen die aan gekoppelde mappen worden toegevoegd, worden automatisch naar AEM verzonden | Als het document wordt toegevoegd aan een gekoppelde map, wordt het bijbehorende element automatisch geüpload naar AEM Assets als een nieuw element. | ✓ | ✓ | ✓ |
| Gekoppelde AEM Assets downloaden vanuit Workfront | Wanneer een element in Workfront is gekoppeld, kan de gebruiker de bytes van het element downloaden. | ✓ | ✓ | ✓ |
| Zoeken naar AEM Assets vanuit Workfront | Met de AEM Assets-kiezer in Workfront kunt u zoeken in volledige tekst naar elementen. | ✓ | ✓ | ✓ |
| Zoeken naar AEM mappen vanuit Workfront | Met de AEM Assets-kiezer in Workfront kunt u in volledige tekst zoeken naar mappen. | ✓ | ✓ | ✓ |
| AEM maphiërarchie weergeven en navigeren vanuit Workfront | Met de AEM Assets-kiezer in Workfront kan door de AEM Assets-hiërarchie worden gebladerd. Dit wordt beperkt door de toegangsbesturingselementen en machtigingen die de gebruiker in AEM heeft ingesteld. | ✓ | ✓ | ✓ |
| Elementversies bijhouden in AEM tijdlijnen | Documentversiehistorie bijhouden tussen Workfront en AEM. | ✓ | ✓ | ✓ |
| Middelen ontkoppelen van AEM Assets in Workfront | Een bestaand gekoppeld element van AEM kan worden losgekoppeld van het bijbehorende Workfront-document. Hierdoor wordt het oorspronkelijke element in AEM niet verwijderd. | ✓ | ✓ | ✓ |
| Nieuw versioned element toevoegen aan AEM Assets vanuit Workfront | Wanneer een nieuw toegevoegde versie aan een document in Workfront wordt toegevoegd, kan een gebruiker de nieuwe versie naar AEM sturen om de bestaande versie te vervangen. | ✓ | ✓ | ✓ |
| In Workfront gekoppelde middelen wanneer op Direct door gebruiker AEM wordt geklikt | Gebruikers worden doorgestuurd naar AEM om een voorvertoning van een gekoppeld element weer te geven vanuit Workfront. | ✓ | ✓ | Binnenkort |
| Automatisch gekoppelde AEM mappen maken in Workfront | Maak automatisch gekoppelde AEM mappen in Workfront met behulp van projectstatussen. Configureer automatisch AEM mappen op basis van Workfront-Portfolio&#39;s, -programma&#39;s en -projecten. | Nee | ✓ | Nee |
| Navigeer rechtstreeks naar AEM opslagplaatsen vanuit Workfront | Gebruikers toestaan te navigeren naar beschikbare AEM opslagruimten die in Workfront zijn geconfigureerd. | ✓ | Nee | ✓ |
| Gekoppelde AEM maken in Workfront | Maak handmatig gekoppelde AEM mappen in Workfront met de optie die beschikbaar is op het tabblad Documenten. | ✓ | Nee | ✓ |
| Commentaar synchroniseren | Automatisch opmerkingen synchroniseren voor elementen van [!DNL Workfront] tot [!DNL Assets] | Nee | ✓ | Nee |
| Ondersteuning voor meerdere Workfront-omgevingen die verbinding maken met één AEM | Gebruikers van meerdere Workfront-omgevingen kunnen verbinding maken met één AEM. | ✓ | Nee | ✓ |
| Ondersteuning voor meerdere AEM die verbinding maken met één Workfront-omgeving | Gebruikers in één Workfront-omgeving kunnen middelen verzenden of koppelen tussen meerdere AEM. | ✓ | ✓ | ✓ |
| **Metagegevens** |
| Metagegevens Workfront-element toewijzen aan AEM Assets | Workfront-object en aangepaste formuliereigenschappen kunnen worden toegewezen aan AEM eigenschappen van metagegevens van elementen. Waarden worden geduwd op aanvankelijke upload/verbinding. | ✓ | ✓ | ✓ |
| Automatisch aangepaste Forms voor documenten maken in Workfront | Voeg aangepaste formulieren toe aan Workfront-documenten, -taken en -problemen met behulp van AEM workflows. | Nee | ✓ | Nee |
| Automatisch in twee richtingen bijwerken van metagegevens tussen AEM Assets en Workfront | Metagegevens automatisch bijwerken tussen AEM Assets en Workfront. Het middel moet aanvankelijk van Workfront aan AEM worden geduwd en de activa van Workfront moeten meta-gegevens aan AEM activa voor bidirectionele meta-gegevensupdates worden in kaart gebracht om geschikt te werken. | Nee | ✓ | Nee |
| Real-time weergave in Workfront voor toegewezen metagegevens naar AEM | Bekijk de bijgewerkte metagegevens die zijn toegewezen aan AEM in de deelvensters Documentdetails en Documentoverzicht van Workfront. | ✓ | Nee | ✓ |
| Real-time push van bijgewerkte Workfront-metagegevens naar AEM | Werk automatisch de toegewezen Workfront-metagegevens bij naar AEM zonder een element of een nieuwe versie van een element te herstellen. | ✓ | Nee | ✓ |
| Workfront-metagegevens toewijzen aan AEM Assets-mappen | Metagegevens van Workfront-projecten synchroniseren met gekoppelde AEM. | Nee | ✓ | ✓ |
| Metagegevensupdates AEM met nieuwe versies | Er kan een configuratie in AEM worden gemaakt om te bepalen of een nieuw versioned element in Workfront ook wijzigingen in de metagegevens doorvoert. | Nee | ✓ | Nee |
| AEM metagegevens automatisch bijwerken bij wijzigingen in Aangepast Forms in Workfront | Met AEM kunt u zich abonneren op de updates van de documentformulieren in Workfront. Als gevolg hiervan worden bij updates van de metagegevens van het aangepaste Workfront-document de waarden voor de toegewezen AEM metagegevensvelden bewerkt. | Nee | ✓ | Nee |
| **Workflows (uit-de-box)** |
| Nieuwe proefversie maken op gekoppelde elementen | Na het koppelen van een element in Workfront kan automatisch een bewijs worden gegenereerd. | Nee | Aangepast | Nee |
| Status instellen voor Workfront-objecten | Workfront-objectstatussen instellen op basis van configureerbare voorwaarden met behulp van AEM workflows | Nee | ✓ | Binnenkort |
| Middelen publiceren voor AEM publicatieomgeving of Brand Portal | Workfront-gebruikers de optie geven om gekoppelde elementen automatisch te publiceren naar een AEM publicatieomgeving of Brand Portal. | Nee | ✓ | Binnenkort |
