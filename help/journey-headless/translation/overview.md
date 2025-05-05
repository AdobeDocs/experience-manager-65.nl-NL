---
title: AEM doorsnedenloze vertaalreis
description: Begin hier voor een begeleide reis door uw inhoud zonder kop te vertalen met behulp van AEM krachtige vertaalhulpmiddelen.
exl-id: 1a9d4c88-b676-4168-a9ef-7d218b39129f
solution: Experience Manager, Experience Manager Sites
feature: Headless,Content Fragments,Language Copy
role: Admin, Architect,Data Architect,Developer,User,Leader
source-git-commit: 9a3008553b8091b66c72e0b6c317573b235eee24
workflow-type: tm+mt
source-wordcount: '1037'
ht-degree: 0%

---

# AEM doorsnedenloze vertaalreis {#aem-headless-translation-journey}

Begin hier voor een begeleide reis door uw inhoud zonder kop te vertalen met behulp van AEM krachtige vertaalhulpmiddelen.

## Inleiding {#introduction}

Implementatie zonder hoofd wordt steeds belangrijker om uw publiek ervaringen te bieden, waar ze zich ook bevinden en ongeacht kanaal, regio of landinstelling.

Bij implementatie zonder kop gaan pagina- en componentbeheer verloren, zoals gebruikelijk is in oplossingen voor volledige stapels. De implementatie is gericht op het maken van kanaalneutrale, herbruikbare fragmenten van inhoud en de levering ervan via meerdere kanalen. Door AEM krachtige vertaalhulpmiddelen te gebruiken, kunnen deze herbruikbare fragmenten gemakkelijk worden vertaald en aan uw publiek worden geleverd waar het kan zijn.

Deze gids leidt u door de belangrijkste hoofdloze vertaalonderwerpen zodat u na voltooiing:

* Heb een overzicht van wat koploze inhoudlevering is.
* U hebt een basiskennis AEM de functies zonder kop.
* Begrijp AEM vertaalfuncties en hoe deze verwant zijn aan inhoud zonder kop.
* De mogelijkheid hebben om uw eigen inhoud zonder kop te vertalen.

Het doel is om u een breed begrip van technologie zonder kop te geven, hoe AEM inhoud zonder kop dient en hoe u het kunt vertalen. Als u met geen van deze onderwerpen vertrouwd bent, is dit uw ideale plaats om te beginnen.

Als u al vertrouwd bent met AEM, zonder kop en vertaling, hebt u wellicht al de grondkennis van deze reis. Overweeg verwijzend naar onze technische documentatie die onder de [ extra hieronder middelensectie wordt verbonden.](#additional-resources)

## AEM Documentenreizen {#documentation-journeys}

[ de Reis van de Documentatie van A ](/help/journey-documentation/home.md) verbindt vele verschillende en misschien ingewikkelde onderwerpen en eigenschappen door een verhaal te verstrekken dat de lezer helpt, die nieuw kan zijn om een bedrijfsprobleem van begin tot eind te AEM, te begrijpen en op te lossen, terwijl het veronderstellen van minimale voorafgaand onderwerp of AEM kennis.

Documentatiereizen zijn gebaseerd op de beginselen van best practices, op basis van het meest recente onderzoek van de Adobe, bewezen ervaring met de implementatie door consultants van de Adobe en feedback van klantprojecten.

Als u wilt weten hoe de Adobe adviseert hoe te om hoofdloze zaken met AEM op te lossen, [ AEM de Reizen van de Zetel ](/help/journey-headless/overview.md) zijn waar te beginnen.

## Publiek {#audience}

Deze reis wordt ontworpen voor de vertaal specialistische persoon, die vaak als de Manager van het Project van de Vertaling of TPM wordt bedoeld. Deze reis beschrijft de vereisten, de stappen, en de benadering om hoofdloze inhoud in AEM te vertalen. De reis kan aanvullende personen definiëren waarmee de vertaalspecialist moet communiceren, maar het gezichtspunt voor de reis is dat van de vertaalspecialist.

Deze reis veronderstelt de lezer ervaring die inhoud op een groot CMS systeem vertaalt, maar veronderstelt geen kennis van technologie zonder kop of AEM.

Het volgende is de persoon die in deze reis interactie heeft.

| Persona | Beschrijving | Rol in reis |
|---|---|---|
| Specialist voor vertaling | Hiermee definieert u welke inhoud moet worden omgezet en beheert u deze workflows | Publiek van deze reis |
| Inhoudsauteur | Creeert en beheert inhoud die zonder kop wordt geleverd | Inhoudsauteurs maken inhoud die de vertaalspecialist moet vertalen. |
| Beheerder | Beheert de basisopstelling en configuratie van AEM | De vertaalspecialist werkt met de beheerder om configuratieveranderingen nodig voor vertaling zoals het installeren van een vertaalschakelaar aan te brengen. |
| Content Architect | Analyseert de vereisten voor de gegevens die zonder kop moeten worden geleverd en bepaalt de structuur voor deze gegevens | Vertaalspecialisten werken samen met de inhoudarchitect om de organisatie van de inhoud te bepalen zodat het gemakkelijk kan worden vertaald. |

De informatie in deze reis kan voor alle mensen nuttig zijn, maar sommige informatie kan aan bepaalde rollen overbodig zijn. Blijf voor [ aanstaande reizen die extra rollen behandelen.](/help/journey-documentation/home.md#journeys)

## De Headless Translation Reis {#the-journey}

U zult vele onderwerpen in deze reis onderzoeken. De volgende artikelen geven u grondkennis van het vertalen van inhoud zonder kop in AEM en koppelen naar gedetailleerde technische documentatie.

Hoewel u rechtstreeks naar een bepaald gedeelte van de reis kunt gaan, bouwen vele concepten op degenen in vorige artikelen. Daarom als u in AEM niet gewend bent aan krantenloze vertaling, adviseert de Adobe dat u bij het begin begint en opeenvolgend vordert.

| Aantal | Artikel | Beschrijving |
|---|---|---|
| 0 | AEM doorsnedenloze vertaalreis | Dit document |
| 1 | [ leer over hoofdloze inhoud en hoe te om het in AEM te vertalen ](learn-about.md) | Ontdek headless-concepten, hoe ze in kaart worden gebracht aan AEM, en de theorie van AEM vertaling. |
| 2 | [ worden begonnen met AEM hoofdloze vertaling ](getting-started.md) | Leer hoe u uw inhoud zonder kop kunt ordenen en hoe AEM vertaalhulpmiddelen werken. |
| 3 | [ vorm de vertaalintegratie ](configure-connector.md) | Leer hoe u verbinding AEM maken met een vertaalservice. |
| 4 | [ vorm vertaalregels ](translation-rules.md) | Leer hoe u vertaalregels definieert om inhoud voor vertaling te identificeren. |
| 5 | [ vertaal inhoud ](translate-content.md) | Gebruik de vertaalintegratie en de regels om uw inhoud zonder kop te vertalen. |
| 6 | [ Publish vertaalde inhoud ](publish-content.md) | Leer hoe u uw vertaalde inhoud publiceert en de vertaling bijwerkt wanneer de onderliggende inhoud wordt bijgewerkt. |

## Volgende functies {#what-is-next}

U bent nu klaar om aan de slag te gaan met uw Adobe zonder hoofd-vertaalreis. Wij moedigen u aan om op het volgende deel van de reis voort te gaan en het artikel [ te lezen Leer over hoofdloze inhoud en hoe te om het in AEM ](learn-about.md) te vertalen

## Aanvullende bronnen {#additional-resources}

Documentatiereizen tonen u hoe AEM een bedrijfsprobleem oplost door een verhaal te verstrekken dat u door complexe, onderling samenhangende processen en eigenschappen begeleidt. Een reis illustreert hoe de veelvoudige eigenschappen samenwerken om één enkele bedrijfsbehoefte te dienen.

Als zodanig zijn reizen zodanig ontworpen dat ze op zichzelf staan. Verschillende kunnen echter aan elkaar zijn gerelateerd. Bekijk deze extra reizen voor meer informatie over hoe AEM krachtige functies samenwerken.

* [ Koploze het Authoring Journey ](/help/journey-headless/author/overview.md) - Begin hier voor een geleide reis door de krachtige en flexibele headless eigenschappen van AEM, hun mogelijkheden, en hoe te om uw inhoud op uw eerste headless project te modelleren.
* [ Eis van de Architect zonder hoofd ](/help/journey-headless/architect/overview.md) - Begin hier voor een inleiding aan de krachtige, en flexibele, headless eigenschappen van Adobe Experience Manager, en hoe te om inhoud voor uw project te modelleren.
* [ AEM Headless Reis van de Ontwikkelaar ](/help/journey-headless/developer/overview.md) - Begin hier voor een geleide reis door de krachtige en flexibele hoofdloze eigenschappen van AEM, hun mogelijkheden, en hoe te om hen op uw eerste ontwikkelingsproject te gebruiken.
* [ AEM technische documentatie ](https://experienceleague.adobe.com/docs/experience-manager-65.html?lang=nl-NL) - als u reeds een stevig inzicht in AEM en headless technologieën hebt, kunt u onze diepgaande technische documenten direct willen raadplegen.
   * Een [ Inleiding aan AEM als Zwaartepunt CMS ](/help/sites-developing/headless/introduction.md)
* [ AEM Headless leerprogramma&#39;s ](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-with-aem-headless/overview.html?lang=nl-NL) - als u verkiest te leren door te doen en technisch gegeneerd bent, neem onze hands-on leerprogramma&#39;s die door API en kader worden georganiseerd, die het creëren van en het gebruiken van toepassingen onderzoeken die op AEM Headless worden voortgebouwd.
* Het [ AEM Portaal van de Ontwikkelaar ](https://experienceleague.adobe.com/landing/experience-manager/headless/developer.html?lang=nl-NL)
