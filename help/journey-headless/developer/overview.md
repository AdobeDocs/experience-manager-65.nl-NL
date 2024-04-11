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
* Begrijp AEM functies zonder kop en hoe ze samenwerken om een eindeloze ervaring te bieden.
* Heb de capaciteit om de eerste stappen uit te voeren die uw eerste AEM hoofdloze project uitvoeren.

## AEM Documentenreizen {#documentation-journeys}

[Een documentatiereis](/help/journey-documentation/home.md) verbindt vele verschillende en misschien ingewikkelde onderwerpen en eigenschappen met elkaar door een verhaal te verstrekken dat de lezer helpt, die nieuw kan zijn om een bedrijfsprobleem van begin tot eind te AEM, te begrijpen en op te lossen, terwijl het veronderstellen van minimale voorafgaand onderwerp of AEM kennis.

Documentatiereizen zijn gebaseerd op de beginselen van best practices, op basis van het meest recente onderzoek van de Adobe, bewezen ervaring met de implementatie door consultants van de Adobe en feedback van klantprojecten.

Als u wilt weten hoe de Adobe adviseert om zaken zonder kop met AEM op te lossen, [AEM zonder kop reizen](/help/journey-headless/overview.md) zijn waar te beginnen.

>[!TIP]
>
>Als u liever **leren door te doen** en technisch gezien zijn, gaat u naar de AEM headless lesbestanden, die zijn georganiseerd door API en framework en beschikbaar zijn in het [Sectie Aanvullende bronnen](#additional-resources) aan het einde van dit document.

## Publiek {#audience}

Deze reis wordt ontworpen voor de ontwikkelaar persoonlijkheid, die de vereisten, de stappen, en de benadering van een AEM Zwaardeloos project vanuit het perspectief van de ontwikkelaar beschrijft. De reis bepaalt extra mensen waarmee de ontwikkelaar voor een succesvol project moet in wisselwerking staan, maar het punt van mening voor de reis is dat van de ontwikkelaar.

Het volgende is de persoon die in deze reis interactie heeft.

| Persona | Beschrijving | Rol in deze reis |
|---|---|---|
| Ontwikkelaar (doelgroep) | Heeft ervaring met het ontwikkelen van toepassingen zonder kop die inhoud uit verschillende bronnen gebruiken | Doelgroep van deze reis |
| Inhoudsauteur | Hiermee maakt en beheert u inhoud die zonder kop wordt geleverd | Inhoudsauteurs maken inhoud die de ontwikkelaar zonder kop levert. |
| Beheerder | Beheert de basisopstelling en configuratie van AEM | De ontwikkelaar werkt met de beheerder om configuratieveranderingen nodig voor ontwikkeling aan te brengen. |
| Content Architect | Analyseert de vereisten voor de gegevens die zonder kop moeten worden geleverd en bepaalt de structuur voor deze gegevens | Ontwikkelaars werken samen met de inhoudarchitect om de structuur van de gegevens en de vereisten voor het leveren van de inhoud te begrijpen. |

De informatie in deze reis kan voor alle mensen nuttig zijn, maar sommige informatie kan aan bepaalde rollen overbodig zijn. Blijf op de hoogte voor [komende reizen die bijkomende rollen bestrijken.](/help/journey-documentation/home.md#journeys)

## De headless Developer Journey {#the-journey}

U zult vele onderwerpen in deze reis onderzoeken. In de volgende artikelen wordt u op basis van uw kennis van de kop in AEM en een link naar gedetailleerde technische documentatie weergegeven.

Hoewel u rechtstreeks naar een bepaald gedeelte van de reis kunt gaan, bouwen vele concepten op degenen in vorige artikelen. Daarom als u in AEM nieuw bent zonder kop, adviseert de Adobe dat u bij het begin begint en opeenvolgend vordert.

| Aantal | Artikel | Beschrijving |
|---|---|---|
| 0 | AEM Headless Developer Journey | Dit document |
| 1 | [Meer informatie over CMS Headless Development](learn-about.md) | Meer informatie over Headless Technology en wanneer u deze gebruikt. |
| 2 | [Aan de slag met AEM headless](getting-started.md) | Meer informatie over AEM vereisten voor headless |
| 3 | [Pad naar uw eerste ervaring met AEM zonder kop](path-to-first-experience.md) | Stel uw ontwikkelomgeving in en leer hoe u een eenvoudige app kunt integreren met AEM Headless |
| 4 | [Uw inhoud modelleren](model-your-content.md) | Leer hoe u uw inhoudsstructuur kunt modelleren. Dan realiseer die structuur voor Adobe Experience Manager (AEM) gebruikend de Modellen van de Fragmenten van de Inhoud en de Fragmenten van de Inhoud, voor hergebruik over kanalen. |
| 5 | [Toegang krijgen tot uw inhoud via AEM API&#39;s voor levering](access-your-content.md) | Leer hoe u GraphQL-query&#39;s gebruikt om toegang te krijgen tot inhoud van Content Fragments. |
| 6 | [Inhoud bijwerken via AEM Assets API&#39;s](update-your-content.md) | Leer hoe u REST API kunt gebruiken om de inhoud van Content Fragments te openen en bij te werken. |
| 7 | [Alles bij elkaar zetten - uw app en uw inhoud in AEM headless](put-it-all-together.md) | Leer hoe u uw AEM Project neemt en voorbereidt voor live gaan met de AEM Headless SDK. |
| 8 | [Live gaan met uw toepassing zonder kop](go-live.md) | Leer hoe u de toepassing live kunt implementeren en uw lokale code in Git kunt plaatsen en deze kunt verplaatsen naar Cloud Manager Git voor CI/CD-pijplijn. |
| 9 | [Optioneel - Hoe kunt u toepassingen voor één pagina maken (SPA) met AEM](create-spa.md) | Als u AEM functies zonder kop begrijpt, kunt u experimenteren met een combinatie van een krachtige en koploze levering en leren hoe u bewerkbare SPA kunt maken met AEM SPA Editor-framework. |

## Volgende functies {#what-is-next}

U bent nu klaar om aan de slag te gaan met uw Adobe Headless reis. We raden u aan door te gaan naar het volgende deel van de reis en het artikel te lezen [Meer informatie over CMS Headless Development.](learn-about.md)

### Kies uw eigen avontuur {#choose-your-path}

Nochtans, wil de Adobe u slagen aangezien u met uw AEM Headless project, ongeacht uw het leren stijl begint. Bekijk deze twee opties.

* Als u liever wilt doorgaan **meer informatie over concepten zonder kop en AEM technologieën zonder kop**, moet u doorgaan met uw AEM zonder kop, zoals wordt aanbevolen door het document opnieuw te bekijken [Hoe te om Uw Inhoud als Modellen van de Inhoud te modelleren AEM](model-your-content.md) waar u leert hoe u de inhoudsstructuur in AEM modelleert.
* Als u liever **leren door te doen**, kunt u naar de [Aan de slag met AEM praktische zelfstudie zonder hoofd](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-with-aem-headless/graphql/multi-step/overview.html) waar u rechtstreeks in AEM Zwaardeloze ontwikkeling door een eenvoudig project zult springen om AEM inhoud zonder kop bloot te stellen.

## Aanvullende bronnen {#additional-resources}

Documentatiereizen tonen u hoe AEM een bedrijfsprobleem oplost door een verhaal te verstrekken dat u door complexe, onderling samenhangende processen en eigenschappen begeleidt. Een reis illustreert hoe de veelvoudige eigenschappen samenwerken om één enkele bedrijfsbehoefte te dienen.

Als zodanig zijn reizen zodanig ontworpen dat ze op zichzelf staan. Verschillende kunnen echter aan elkaar zijn gerelateerd. Bekijk deze extra reizen voor meer informatie over hoe AEM krachtige functies samenwerken.

* [Zelfstudies zonder koppen AEM](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-with-aem-headless/overview.html) - Als u liever wilt leren door te doen en technisch georiënteerd bent, neemt u onze praktische zelfstudies die zijn georganiseerd door API en framework, die het maken en gebruiken van toepassingen die zijn gebaseerd op AEM Headless onderzoeken.
* [AEM doorsnedenloze vertaalreis](/help/journey-headless/translation/overview.md) - Deze documentatietraject geeft u een ruim inzicht in technologie zonder kop, hoe AEM inhoud zonder kop dient en hoe u deze kunt vertalen.
* [Papierreis zonder koppen](/help/journey-headless/author/overview.md) - Begin hier voor een geleide reis door de krachtige en flexibele headless eigenschappen van AEM, hun mogelijkheden, en hoe te om uw inhoud op uw eerste headless project te modelleren.
* [Architect zonder hoofd](/help/journey-headless/architect/overview.md) - Begin hier voor een introductie van de krachtige, flexibele, eindeloze functies van Adobe Experience Manager en hoe u inhoud voor uw project kunt modelleren.
* [AEM technische documentatie](https://experienceleague.adobe.com/docs/experience-manager-65.html) - Als u al een duidelijk inzicht hebt in AEM en technologieën zonder kop, kunt u onze diepgaande technische documenten direct raadplegen.

   * An [Inleiding tot AEM als een headless CMS](/help/sites-developing/headless/introduction.md)

* De [AEM Developer Portal](https://experienceleague.adobe.com/landing/experience-manager/headless/developer.html)
