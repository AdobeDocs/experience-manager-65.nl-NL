---
title: '[!DNL Experience Manager Assets] integratie met  [!DNL Adobe Workfront]'
description: Inleiding aan integratie tussen  [!DNL Assets]  en  [!DNL Workfront]
role: Admin,Leader,Developer
feature: Workfront Integrations and Apps
exl-id: 57e2bffe-8094-4557-99c8-7b482681687e
hide: true
solution: Experience Manager, Workfront
source-git-commit: 07289e891399a78568dcac957bc089cc08c7898c
workflow-type: tm+mt
source-wordcount: '1113'
ht-degree: 0%

---

# [!DNL Adobe Experience Manager Assets] integratie met [!DNL Adobe Workfront] {#assets-integration-overview}

| Versie | Artikelkoppeling |
| -------- | ---------------------------- |
| AEM as a Cloud Service | [ klik hier ](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/assets/integrations/workfront-integrations.html?lang=en) |
| AEM 6.5 | Dit artikel |

[!DNL Adobe Workfront] is een werkbeheertoepassing waarmee u de volledige levenscyclus van het werk op één locatie kunt beheren. Dankzij de integratie tussen [!DNL Workfront] en [!DNL Adobe Experience Manager Assets] kunnen organisaties de snelheid en tijd-aan-markt van inhoud verbeteren door het werk en het beheer van digitale elementen intrinsiek met elkaar te verbinden. In het kader van het beheer van hun werk in Workfront hebben gebruikers toegang tot de vereiste documenten en afbeeldingen.

De [!DNL Workfront for Experience Manager enhanced connector] maakt verbeterde bedrijfsprocessen mogelijk met end-to-end workflows en biedt persoonlijke end-to-end clientervaringen en centrale opslag. Adobe biedt een standaardaansluiting en een verbeterde aansluiting om de twee oplossingen te integreren. Zie de gesteunde eigenschappen hieronder voor een vergelijking en zie [ wat in  [!DNL enhanced connector] ](https://one.workfront.com/s/csh?context=2467&pubname=the-new-workfront-experience) nieuw is.

[!DNL Workfront for Experience Manage enhanced connector] biedt uw organisatie de volgende mogelijkheden:

* Maak automatisch gekoppelde Experience Manager-mappen in Workfront en deel de mappen in op basis van Workfront-portfolio&#39;s, -programma&#39;s en -projecten.
* Workfront-projectmetagegevens synchroniseren met gekoppelde Experience Manager-mappen.
* Experience Manager-metagegevens worden bijgewerkt met nieuwe versies.
* Stel Workfront-objectstatussen in op basis van configureerbare voorwaarden met Experience Manager-workflows.
* Publiceer middelen naar de publicatieomgeving van Experience Manager of naar Brand Portal.

Zie de platformsteun en [ eerste vereisten voor de verbeterde schakelaar ](https://one.workfront.com/s/csh?context=2467&pubname=the-new-workfront-experience).

>[!IMPORTANT]
>
>* Adobe vereist implementatie en configuratie van de [!DNL Adobe Workfront for Experience Manager enhanced connector] alleen via gecertificeerde partners of [!DNL Adobe Professional Services] . Indien geïmplementeerd en geconfigureerd zonder een gecertificeerde partner of [!DNL Adobe Professional Services] , wordt dit niet ondersteund door Adobe.
>
>* Adobe kan updates voor [!DNL Adobe Workfront] en [!DNL Adobe Experience Manager] vrijgeven die deze connector redundant maken. Als dit gebeurt, kunnen klanten worden gevraagd over te stappen van het gebruik van deze connector.
>
>* Adobe ondersteunt verbeterde connectorversies 1.7.4 en hoger. Eerdere pre-release en aangepaste versies worden niet ondersteund. Om de verbeterde schakelaarversie te controleren, navigeer aan de `digital.hoodoo` groep beschikbaar in de linkerruit in [ Manager van het Pakket ](https://experienceleague.adobe.com/docs/experience-manager-65/administering/contentmanagement/package-manager.html?lang=en).
>
>* Zie [ de certificatieexamen van de Partner voor Workfront voor Experience Manager Assets verbeterde schakelaar ](https://solutionpartners.adobe.com/solution-partners/home/applications/experience_cloud/workfront/journey/dev_core.html). Voor informatie over het examen, zie {de Gids van het 0} Examen [.](https://express.adobe.com/page/Tc7Mq6zLbPFy8/)

## Verschillende integraties tussen [!DNL Assets] en [!DNL Workfront] vergelijken {#feature-parity-matrix}

Hieronder vindt u een overzicht van de functies die beschikbaar zijn via verschillende soorten integratie tussen [!DNL Assets] en [!DNL Workfront] .

| Functie | Beschrijving | [!DNL Workfront] en [!DNL Assets Essentials] *Geen Schakelaar (uit-van-de-doos)* | [!DNL Workfront for Experience Manager enhanced connector] *vereist Schakelaar* | Workfront en [!DNL Experience Manager as a Cloud Service] *Geen Schakelaar (uit-van-de-doos)* |
|----|----|----|-----|-----|
| Implementatiemethoden | Geschikt voor de [!DNL Assets] -aanbieding. | Grondbeginselen van activa | Adobe Managed Services, On-premise | Cloud Service |
| **Algemeen** |  |  |  |  |
| Digitale bestanden verzenden van [!DNL Workfront] naar [!DNL Assets] | De nieuwste versie van een WF-document kan worden geüpload naar AEM Assets, dat is gekoppeld als een nieuwe versie van het document. | ✓ | ✓ | ✓ |
| AEM-mappen handmatig koppelen aan Workfront-objecten | Bestaande AEM-mappen kunnen worden gekoppeld als een Workfront-map en de onderliggende elementen ervan worden gekoppeld als nieuwe Workfront-documenten. | ✓ | ✓ | ✓ |
| Koppelen [!DNL Assets] aan Workfront-objecten | Bestaande elementen in AEM kunnen worden gekoppeld aan een nieuw Workfront-document of als een nieuwe versie van een bestaand document. | ✓ | ✓ | ✓ |
| Assets dat aan gekoppelde mappen is toegevoegd, wordt automatisch naar AEM verzonden | Als het document wordt toegevoegd aan een gekoppelde map, wordt het bijbehorende element automatisch geüpload naar AEM Assets als een nieuw element. | ✓ | ✓ | ✓ |
| Gekoppelde AEM Assets downloaden vanuit Workfront | Wanneer een element in Workfront is gekoppeld, kan de gebruiker de bytes van het element downloaden. | ✓ | ✓ | ✓ |
| Zoeken naar AEM Assets vanuit Workfront | Met de AEM Assets-kiezer in Workfront kunt u zoeken in volledige tekst naar elementen. | ✓ | ✓ | ✓ |
| Zoeken naar AEM-mappen vanuit Workfront | Met de AEM Assets-kiezer in Workfront kunt u in volledige tekst zoeken naar mappen. | ✓ | ✓ | ✓ |
| AEM-maphiërarchie weergeven en navigeren vanuit Workfront | Met de AEM Assets-kiezer in Workfront kunt u bladeren in de AEM Assets-hiërarchie die wordt beperkt door de   de toegangsbesturingselementen en machtigingen die zijn ingesteld in AEM. | ✓ | ✓ | ✓ |
| Elementversies bijhouden in AEM-tijdlijnen | Documentversiehistorie bijhouden tussen Workfront en AEM. | ✓ | ✓ | ✓ |
| Assets loskoppelen van AEM Assets in Workfront | Een bestaand gekoppeld element uit AEM kan worden losgekoppeld van het bijbehorende Workfront-document. Hiermee verwijdert u het oorspronkelijke element in AEM niet. | ✓ | ✓ | ✓ |
| Nieuw versioned element toevoegen aan AEM Assets vanuit Workfront | Wanneer een nieuwe versie wordt toegevoegd aan een document in Workfront, kan een gebruiker de nieuwe versie naar AEM sturen om de bestaande versie te vervangen. | ✓ | ✓ | ✓ |
| Assets Gekoppeld in Workfront wanneer op Direct-gebruiker naar AEM wordt geklikt | Gebruikers worden naar AEM gestuurd om een voorbeeld van een gekoppeld element te bekijken vanuit Workfront. | ✓ | ✓ | Binnenkort |
| Automatisch gekoppelde AEM-mappen maken in Workfront | Automatisch gekoppelde AEM-mappen maken in Workfront met behulp van projectstatussen. Configureer automatisch AEM-mappen op basis van Workfront-portfolio&#39;s, -programma&#39;s en -projecten. | Nee | ✓ | Nee |
| Ga rechtstreeks naar AEM-opslagruimten vanuit Workfront | Gebruikers toestaan naar beschikbare AEM-opslagruimten te navigeren die in Workfront zijn geconfigureerd. | ✓ | Nee | ✓ |
| Gekoppelde AEM-mappen maken in Workfront | Maak handmatig gekoppelde AEM-mappen in Workfront met de optie die beschikbaar is op het tabblad Documenten. | ✓ | Nee | ✓ |
| Commentaar synchroniseren | Opmerkingen voor elementen automatisch synchroniseren van [!DNL Workfront] naar [!DNL Assets] | Nee | ✓ | Nee |
| Ondersteuning voor meerdere Workfront-omgevingen die verbinding maken met één AEM-omgeving | Gebruikers van meerdere Workfront-omgevingen kunnen verbinding maken met één AEM-omgeving. | ✓ | Nee | ✓ |
| Ondersteuning voor meerdere AEM-omgevingen die verbinding maken met één Workfront-omgeving | Gebruikers in één Workfront-omgeving kunnen middelen verzenden of koppelen tussen meerdere AEM-omgevingen. | ✓ | ✓ | ✓ |
| **Metagegevens** |  |  |  |  |
| Metagegevens Workfront-element toewijzen aan AEM Assets | Workfront-object en aangepaste formuliereigenschappen kunnen worden toegewezen aan eigenschappen van metagegevens van AEM-elementen. Waarden worden geduwd op aanvankelijke upload/verbinding. | ✓ | ✓ | ✓ |
| Automatisch aangepaste Forms voor documenten maken in Workfront | Voeg aangepaste formulieren toe aan Workfront-documenten, -taken en -problemen met AEM-workflows. | Nee | ✓ | Nee |
| Automatisch in twee richtingen bijwerken van metagegevens tussen AEM Assets en Workfront | Metagegevens automatisch bijwerken tussen AEM Assets en Workfront. Het middel moet aanvankelijk van Workfront aan AEM worden geduwd en de activa van Workfront moeten meta-gegevens aan de activa van AEM voor bidirectionele meta-gegevensupdates worden in kaart gebracht om geschikt te werken. | Nee | ✓ | Nee |
| Real-time weergave in Workfront voor toegewezen metagegevens aan AEM | Bekijk de bijgewerkte metagegevens die zijn toegewezen aan AEM in de deelvensters Documentdetails en Documentoverzicht van Workfront. | ✓ | Nee | ✓ |
| Real-time push van bijgewerkte Workfront-metagegevens naar AEM | Werk automatisch de toegewezen Workfront-metagegevens bij naar AEM zonder een element of een nieuwe versie van een element te vernieuwen. | ✓ | Nee | ✓ |
| Workfront-metagegevens toewijzen aan AEM Assets-mappen | Metagegevens van Workfront-projecten synchroniseren met gekoppelde AEM-mappen. | Nee | ✓ | ✓ |
| AEM-metagegevensupdates met nieuwe versies | Er kan een configuratie in AEM worden gemaakt om te bepalen of een nieuw versioned element in Workfront ook wijzigingen aanbrengt in de metagegevens. | Nee | ✓ | Nee |
| AEM-metagegevens automatisch bijwerken bij wijzigingen in Aangepaste Forms in Workfront | Met AEM kunt u zich abonneren op de updates van de documentformulieren in Workfront. Als gevolg hiervan worden bij updates van de metagegevens van het aangepaste Workfront-document de waarden voor de toegewezen AEM-metagegevensvelden bewerkt. | Nee | ✓ | Nee |
| **Werkstromen (uit-van-de-doos)** |  |  |  |  |
| Nieuwe proefversie maken op gekoppelde Assets | Na het koppelen van een element in Workfront kan automatisch een bewijs worden gegenereerd. | Nee | Aangepast | Nee |
| Status instellen voor Workfront-objecten | Workfront-objectstatussen instellen op basis van configureerbare voorwaarden met AEM-workflows | Nee | ✓ | Binnenkort |
| Assets publiceren naar AEM Publish Environment of Brand Portal | Workfront-gebruikers de optie geven om gekoppelde elementen automatisch te publiceren naar een AEM-publicatieomgeving of Brand Portal. | Nee | ✓ | Binnenkort |
