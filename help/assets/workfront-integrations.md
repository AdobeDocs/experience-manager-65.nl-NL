---
title: '[!DNL Experience Manager Assets] integratie met  [!DNL Adobe Workfront]'
description: Inleiding aan integratie tussen  [!DNL Assets]  en  [!DNL Workfront]
role: Admin,Leader,Architect
feature: Workfront Integrations and Apps
exl-id: 57e2bffe-8094-4557-99c8-7b482681687e
hide: true
solution: Experience Manager, Workfront
source-git-commit: 5ccac0aadce3971e66da052d393cbd33b61e94f7
workflow-type: tm+mt
source-wordcount: '1174'
ht-degree: 0%

---

# [!DNL Adobe Experience Manager Assets] integratie met [!DNL Adobe Workfront] {#assets-integration-overview}

| Versie | Artikelkoppeling |
| -------- | ---------------------------- |
| AEM as a Cloud Service | [&#x200B; klik hier &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/assets/integrations/workfront-integrations.html?lang=nl-NL) |
| AEM 6,5 | Dit artikel |

[!DNL Adobe Workfront] is een werkbeheertoepassing waarmee u de volledige levenscyclus van het werk op één locatie kunt beheren. Dankzij de integratie tussen [!DNL Workfront] en [!DNL Adobe Experience Manager Assets] kunnen organisaties de snelheid en tijd-aan-markt van inhoud verbeteren door het werk en het beheer van digitale elementen intrinsiek met elkaar te verbinden. In het kader van het beheer van hun werk in Workfront hebben gebruikers toegang tot de vereiste documenten en afbeeldingen.

De [!DNL Workfront for Experience Manager enhanced connector] maakt verbeterde bedrijfsprocessen mogelijk met end-to-end workflows en biedt persoonlijke end-to-end clientervaringen en centrale opslag. De Adobe biedt een standaardschakelaar en een verbeterde schakelaar aan om de twee oplossingen te integreren. Zie de gesteunde eigenschappen hieronder voor een vergelijking en zie [&#x200B; wat in  [!DNL enhanced connector] &#x200B;](https://one.workfront.com/s/csh?context=2467&pubname=the-new-workfront-experience) nieuw is.

[!DNL Workfront for Experience Manage enhanced connector] biedt uw organisatie de volgende mogelijkheden:

* Maak automatisch gekoppelde mappen voor Experience Managers in Workfront en deel de mappen in op basis van Workfront-Portfolio&#39;s, -programma&#39;s en -projecten.
* Metagegevens van Workfront-projecten synchroniseren met mappen voor gekoppelde Experience Managers.
* Metagegevens van de Experience Manager worden bijgewerkt met nieuwe versies.
* Stel Workfront-objectstatussen in op basis van configureerbare omstandigheden met behulp van workflows voor Experience Managers.
* Publish-middelen om de publicatieomgeving te Experience Managers of naar Brand Portal.

Zie de platformsteun en [&#x200B; eerste vereisten voor de verbeterde schakelaar &#x200B;](https://one.workfront.com/s/csh?context=2467&pubname=the-new-workfront-experience).

>[!IMPORTANT]
>
>* Voor Adobe is implementatie en configuratie van de [!DNL Adobe Workfront for Experience Manager enhanced connector] alleen via gecertificeerde partners of [!DNL Adobe Professional Services] vereist. Indien opgesteld en gevormd zonder een verklaarde partner of [!DNL Adobe Professional Services], wordt het niet gesteund door Adobe.
>
>* Adobe kan updates aan [!DNL Adobe Workfront] en [!DNL Adobe Experience Manager] vrijgeven die deze schakelaar overtollig maken; als dit voorkomt, kunnen klanten worden vereist om van het gebruik van deze schakelaar over te gaan.
>
>* Adobe ondersteunt verbeterde connectorversies 1.7.4 en hoger. Eerdere pre-release en aangepaste versies worden niet ondersteund. Om de verbeterde schakelaarversie te controleren, navigeer aan de `digital.hoodoo` groep beschikbaar in de linkerruit in [&#x200B; Manager van het Pakket &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-65/administering/contentmanagement/package-manager.html?lang=nl-NL).
>
>* Zie [&#x200B; de certificatieexamen van de Partner voor Workfront voor Experience Manager Assets verbeterde schakelaar &#x200B;](https://solutionpartners.adobe.com/solution-partners/home/applications/experience_cloud/workfront/journey/dev_core.html). Voor informatie over het examen, zie {de Gids van het 0} Examen [&#128279;](https://express.adobe.com/page/Tc7Mq6zLbPFy8/).

## Verschillende integraties tussen [!DNL Assets] en [!DNL Workfront] vergelijken {#feature-parity-matrix}

Hieronder vindt u een overzicht van de functies die beschikbaar zijn via verschillende soorten integratie tussen [!DNL Assets] en [!DNL Workfront] .

| Functie | Beschrijving | [!DNL Workfront] en [!DNL Assets Essentials] *Geen Schakelaar (uit-van-de-doos)* | [!DNL Workfront for Experience Manager enhanced connector] *vereist Schakelaar* | Workfront en [!DNL Experience Manager as a Cloud Service] *Geen Schakelaar (uit-van-de-doos)* |
|----|----|----|-----|-----|
| Implementatiemethoden | Geschikt voor de [!DNL Assets] -aanbieding. | Assets Essentials | Adobe Managed Services, op locatie | Cloud Service |
| **Algemeen** |
| Digitale bestanden verzenden van [!DNL Workfront] naar [!DNL Assets] | De nieuwste versie van een WF-document kan worden geüpload naar AEM Assets, dat is gekoppeld als een nieuwe versie van het document. | ✓ | ✓ | ✓ |
| Mappen handmatig koppelen AEM aan Workfront-objecten | Bestaande AEM mappen kunnen worden gekoppeld als een Workfront-map en de onderliggende elementen ervan worden gekoppeld als nieuwe Workfront-documenten. | ✓ | ✓ | ✓ |
| Koppelen [!DNL Assets] aan Workfront-objecten | Bestaande elementen in AEM kunnen worden gekoppeld aan een nieuw Workfront-document of als een nieuwe versie van een bestaand document. | ✓ | ✓ | ✓ |
| Assets dat aan gekoppelde mappen is toegevoegd, wordt automatisch verzonden naar AEM | Als het document wordt toegevoegd aan een gekoppelde map, wordt het bijbehorende element automatisch geüpload naar AEM Assets als een nieuw element. | ✓ | ✓ | ✓ |
| Gekoppelde AEM Assets downloaden vanuit Workfront | Wanneer een element in Workfront is gekoppeld, kan de gebruiker de bytes van het element downloaden. | ✓ | ✓ | ✓ |
| Zoeken naar AEM Assets vanuit Workfront | Met de AEM Assets-kiezer in Workfront kunt u zoeken in volledige tekst naar elementen. | ✓ | ✓ | ✓ |
| Zoeken naar AEM mappen vanuit Workfront | Met de AEM Assets-kiezer in Workfront kunt u in volledige tekst zoeken naar mappen. | ✓ | ✓ | ✓ |
| AEM maphiërarchie weergeven en navigeren vanuit Workfront | Met de AEM Assets-kiezer in Workfront kunt u bladeren in de AEM Assets-hiërarchie die wordt beperkt door de   de bijbehorende toegangscontroles en de toestemmingen van de gebruiker die in AEM worden geplaatst. | ✓ | ✓ | ✓ |
| Elementversies bijhouden in AEM tijdlijnen | Documentversiehistorie bijhouden tussen Workfront en AEM. | ✓ | ✓ | ✓ |
| Assets loskoppelen van AEM Assets in Workfront | Een bestaand gekoppeld element van AEM kan worden losgekoppeld van het bijbehorende Workfront-document. Hierdoor wordt het oorspronkelijke element in AEM niet verwijderd. | ✓ | ✓ | ✓ |
| Nieuw versioned element toevoegen aan AEM Assets vanuit Workfront | Wanneer een nieuw toegevoegde versie aan een document in Workfront wordt toegevoegd, kan een gebruiker de nieuwe versie naar AEM sturen om de bestaande versie te vervangen. | ✓ | ✓ | ✓ |
| Assets Gekoppeld in Workfront wanneer op Direct door gebruiker AEM wordt geklikt | Gebruikers worden doorgestuurd naar AEM om een voorvertoning van een gekoppeld element weer te geven vanuit Workfront. | ✓ | ✓ | Binnenkort |
| Automatisch gekoppelde AEM mappen maken in Workfront | Maak automatisch gekoppelde AEM mappen in Workfront met behulp van projectstatussen. Configureer automatisch AEM mappen op basis van Workfront-Portfolio&#39;s, -programma&#39;s en -projecten. | Nee | ✓ | Nee |
| Navigeer rechtstreeks naar AEM opslagplaatsen vanuit Workfront | Gebruikers toestaan te navigeren naar beschikbare AEM opslagruimten die in Workfront zijn geconfigureerd. | ✓ | Nee | ✓ |
| Gekoppelde AEM maken in Workfront | Maak handmatig gekoppelde AEM mappen in Workfront met de optie die beschikbaar is op het tabblad Documenten. | ✓ | Nee | ✓ |
| Commentaar synchroniseren | Opmerkingen voor elementen automatisch synchroniseren van [!DNL Workfront] naar [!DNL Assets] | Nee | ✓ | Nee |
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
| **Werkstromen (uit-van-de-doos)** |
| Nieuwe proefversie maken op gekoppelde Assets | Na het koppelen van een element in Workfront kan automatisch een bewijs worden gegenereerd. | Nee | Aangepast | Nee |
| Status instellen voor Workfront-objecten | Workfront-objectstatussen instellen op basis van configureerbare voorwaarden met behulp van AEM workflows | Nee | ✓ | Binnenkort |
| Publish Assets AEM Publish Environment of Brand Portal | Workfront-gebruikers de optie geven om gekoppelde elementen automatisch te publiceren naar een AEM Publish-omgeving of Brand Portal. | Nee | ✓ | Binnenkort |
