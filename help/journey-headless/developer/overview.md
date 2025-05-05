---
title: AEM Headless Developer Journey
description: AEM CMS-documentatie zonder kop. Begin hier voor een geleide reis door de krachtige en flexibele headless eigenschappen van AEM, hun mogelijkheden, en hoe te om hen op uw eerste ontwikkelingsproject te gebruiken.
exl-id: f24fb308-daa7-426f-ba45-37a236b5a500
solution: Experience Manager, Experience Manager Sites
feature: Headless,Content Fragments,GraphQL,Persisted Queries,Developing
role: Admin, Developer
source-git-commit: 9a3008553b8091b66c72e0b6c317573b235eee24
workflow-type: tm+mt
source-wordcount: '1204'
ht-degree: 1%

---

# AEM Headless Developer Journey {#aem-headless-developer-journey}

Begin hier voor een geleide reis door de krachtige en flexibele headless eigenschappen van AEM, hun mogelijkheden, en hoe te om hen op uw eerste project zonder titel te gebruiken. Deze reis voorziet u van al AEM Documentatie zonder Titel u uw eerste toepassing zonder titel moet ontwikkelen.

## Inleiding {#introduction}

Bij implementatie zonder kop gaan pagina- en componentbeheer verloren, zoals gebruikelijk is in oplossingen voor volledige stapels. De implementatie is gericht op het maken van kanaalneutrale, herbruikbare fragmenten van inhoud en de levering ervan via meerdere kanalen. Het is een modern en dynamisch ontwikkelingspatroon voor de implementatie van digitale ervaringen.

Deze gids leidt u door de belangrijkste implementatieonderwerpen in AEM zodat u na voltooiing:

* U moet goed begrijpen wat de inhoud zonder kop levert en wat de voordelen ervan zijn.
* Begrijp AEM ontelbare functies en hoe ze samenwerken om een eindeloze ervaring te bieden.
* Heb de capaciteit om de eerste stappen uit te voeren die uw eerste AEM hoofdloze project uitvoeren.

## AEM Documentenreizen {#documentation-journeys}

[ de Reis van de Documentatie van A ](/help/journey-documentation/home.md) verbindt vele verschillende en misschien ingewikkelde onderwerpen en eigenschappen door een verhaal te verstrekken dat de lezer helpt, die nieuw kan zijn om een bedrijfsprobleem van begin tot eind te AEM, te begrijpen en op te lossen, terwijl het veronderstellen van minimale voorafgaand onderwerp of AEM kennis.

Documentatiereizen zijn gebaseerd op de beginselen van best practices, op basis van het meest recente onderzoek van de Adobe, bewezen ervaring met de implementatie door consultants van de Adobe en feedback van klantprojecten.

Als u wilt weten hoe de Adobe adviseert hoe te om hoofdloze zaken met AEM op te lossen, [ AEM de Reizen van de Zetel ](/help/journey-headless/overview.md) zijn waar te beginnen.

>[!TIP]
>
>Als u verkiest om **te leren door** te doen en technisch gegeneerd bent, bezoek de AEM Hoofdloze leerprogramma&#39;s, die door API en kader worden georganiseerd en in de [ Extra sectie van Middelen ](#additional-resources) aan het eind van dit document beschikbaar zijn.

## Publiek {#audience}

Deze reis wordt ontworpen voor de ontwikkelaar persoonlijkheid, die de vereisten, de stappen, en de benadering van een AEM Zwaardeloos project vanuit het perspectief van de ontwikkelaar beschrijft. De reis bepaalt extra mensen waarmee de ontwikkelaar voor een succesvol project moet in wisselwerking staan, maar het punt van mening voor de reis is dat van de ontwikkelaar.

Het volgende is de persoon die in deze reis interactie heeft.

| Persona | Beschrijving | Rol in deze reis |
|---|---|---|
| Ontwikkelaar (doelgroep) | Heeft ervaring met het ontwikkelen van toepassingen zonder kop die inhoud uit verschillende bronnen gebruiken | Doelgroep van deze reis |
| Inhoudsauteur | Hiermee maakt en beheert u inhoud die zonder kop wordt geleverd | Inhoudsauteurs maken inhoud die de ontwikkelaar zonder kop levert. |
| Beheerder | Beheert de basisopstelling en configuratie van AEM | De ontwikkelaar werkt met de beheerder om configuratieveranderingen nodig voor ontwikkeling aan te brengen. |
| Content Architect | Analyseert de vereisten voor de gegevens die zonder kop moeten worden geleverd en bepaalt de structuur voor deze gegevens | Ontwikkelaars werken samen met de inhoudarchitect om de structuur van de gegevens en de vereisten voor het leveren van de inhoud te begrijpen. |

De informatie in deze reis kan voor alle mensen nuttig zijn, maar sommige informatie kan aan bepaalde rollen overbodig zijn. Blijf voor [ aanstaande reizen die extra rollen behandelen.](/help/journey-documentation/home.md#journeys)

## De headless Developer Journey {#the-journey}

U zult vele onderwerpen in deze reis onderzoeken. In de volgende artikelen wordt u op basis van uw kennis van de kop in AEM en een link naar gedetailleerde technische documentatie weergegeven.

Hoewel u rechtstreeks naar een bepaald gedeelte van de reis kunt gaan, bouwen vele concepten op degenen in vorige artikelen. Daarom als u in AEM nieuw bent zonder kop, adviseert de Adobe dat u bij het begin begint en opeenvolgend vordert.

| Aantal | Artikel | Beschrijving |
|---|---|---|
| 0 | AEM Headless Developer Journey | Dit document |
| 1 | [ Leer over CMS Hoofdloze Ontwikkeling ](learn-about.md) | Meer informatie over Headless Technology en wanneer u deze gebruikt. |
| 2 | [ Begonnen het worden met AEM Titel ](getting-started.md) | Meer informatie over AEM vereisten voor headless |
| 3 | [ Weg aan uw eerste ervaring gebruikend AEM Zwaartepunt ](path-to-first-experience.md) | Stel uw ontwikkelomgeving in en leer hoe u een eenvoudige app kunt integreren met AEM Headless |
| 4 | [ hoe te om uw inhoud ](model-your-content.md) te modelleren | Leer hoe u uw inhoudsstructuur kunt modelleren. Dan realiseer die structuur voor Adobe Experience Manager (AEM) gebruikend de Modellen van de Fragmenten van de Inhoud en de Fragmenten van de Inhoud, voor hergebruik over kanalen. |
| 5 | [ hoe te om tot uw inhoud via AEM levering APIs toegang te hebben ](access-your-content.md) | Leer hoe u GraphQL-query&#39;s gebruikt om toegang te krijgen tot inhoud van Content Fragments. |
| 6 | [ hoe te om uw inhoud via AEM Assets APIs bij te werken ](update-your-content.md) | Leer hoe u REST API kunt gebruiken om de inhoud van Content Fragments te openen en bij te werken. |
| 7 | [ hoe te om het allen samen te zetten - uw app en uw inhoud in AEM Zwaartepunt ](put-it-all-together.md) | Leer hoe u uw AEM Project neemt en voorbereidt voor live gaan met de AEM Headless SDK. |
| 8 | [ hoe te om met uw headless toepassing te gaan ](go-live.md) | Leer hoe u de toepassing live kunt implementeren en neem uw lokale code in Git en verplaats deze naar Cloud Manager Git voor CI/CD-pijplijn. |
| 9 | [ Facultatief - hoe te om enige paginatoepassingen (SPA) met AEM tot stand te brengen ](create-spa.md) | Als u eenmaal de AEM functies zonder kop hebt begrepen, kunt u experimenteren met een combinatie van krachtige en koploze levering en leren hoe u bewerkbare SPA kunt maken met AEM SPA Editor-framework. |

## Volgende functies {#what-is-next}

U bent nu klaar om aan de slag te gaan met uw Adobe Headless reis. Wij moedigen u aan om op het volgende deel van de reis voort te gaan en het artikel [ te lezen Leer over CMS Headless Ontwikkeling.](learn-about.md)

### Kies uw eigen avontuur {#choose-your-path}

Nochtans, wil de Adobe u slagen aangezien u met uw AEM Headless project, ongeacht uw het leren stijl begint. Bekijk deze twee opties.

* Als u verkiest om **over headless concepten en AEM te blijven leren zonder kop technologieën**, zou u uw AEM zonder kop reis moeten voortzetten zoals geadviseerd door het document [ opnieuw te bekijken hoe te Uw Inhoud als Modellen van de Inhoud te modelleren ](model-your-content.md) waar u leert hoe te om uw inhoudsstructuur in AEM te modelleren.
* Als u verkiest om **te leren door** te doen, kunt u aan [ springen Begonnen met AEM Hoofdloze hands-on leerprogramma ](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-with-aem-headless/graphql/multi-step/overview.html?lang=nl-NL) waar u direct in AEM Ontwikkelt zonder Titel door een eenvoudig project uit te voeren om AEM inhoud zonder kop bloot te stellen.

## Aanvullende bronnen {#additional-resources}

Documentatiereizen tonen u hoe AEM een bedrijfsprobleem oplost door een verhaal te verstrekken dat u door complexe, onderling samenhangende processen en eigenschappen begeleidt. Een reis illustreert hoe de veelvoudige eigenschappen samenwerken om één enkele bedrijfsbehoefte te dienen.

Als zodanig zijn reizen zodanig ontworpen dat ze op zichzelf staan. Verschillende kunnen echter aan elkaar zijn gerelateerd. Bekijk deze extra reizen voor meer informatie over hoe AEM krachtige functies samenwerken.

* [ AEM Headless leerprogramma&#39;s ](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-with-aem-headless/overview.html?lang=nl-NL) - als u verkiest te leren door te doen en technisch gegeneerd bent, neem onze hands-on leerprogramma&#39;s die door API en kader worden georganiseerd, die het creëren van en het gebruiken van toepassingen onderzoeken die op AEM Headless worden voortgebouwd.
* [ AEM Headless Vertaalreis ](/help/journey-headless/translation/overview.md) - Deze documentatietraject geeft u een breed inzicht in technologie zonder kop, hoe AEM inhoud zonder kop dient, en hoe u het kunt vertalen.
* [ Koploze het Authoring Journey ](/help/journey-headless/author/overview.md) - Begin hier voor een geleide reis door de krachtige en flexibele headless eigenschappen van AEM, hun mogelijkheden, en hoe te om uw inhoud op uw eerste headless project te modelleren.
* [ Eis van de Architect zonder hoofd ](/help/journey-headless/architect/overview.md) - Begin hier voor een inleiding aan de krachtige, en flexibele, headless eigenschappen van Adobe Experience Manager, en hoe te om inhoud voor uw project te modelleren.
* [ AEM technische documentatie ](https://experienceleague.adobe.com/docs/experience-manager-65.html?lang=nl-NL) - als u reeds een stevig inzicht in AEM en headless technologieën hebt, kunt u onze diepgaande technische documenten direct willen raadplegen.

   * Een [ Inleiding aan AEM als Zwaartepunt CMS ](/help/sites-developing/headless/introduction.md)

* Het [ AEM Portaal van de Ontwikkelaar ](https://experienceleague.adobe.com/landing/experience-manager/headless/developer.html?lang=nl-NL)
