---
title: Soorten publiek beheren
description: Met de console Soorten publiek kunt u soorten publiek voor uw Adobe Target-account maken, organiseren en beheren of segmenten voor ContextHub of Client beheren
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: personalization
docset: aem65
exl-id: 97e02986-049f-4747-a67a-6aa0677b281e
solution: Experience Manager, Experience Manager Sites
feature: Authoring,Personalization
role: User,Admin,Architect,Developer
source-git-commit: 9a3008553b8091b66c72e0b6c317573b235eee24
workflow-type: tm+mt
source-wordcount: '903'
ht-degree: 7%

---

# Soorten publiek beheren{#managing-audiences}

Met de console Soorten publiek kunt u soorten publiek voor uw Adobe Target-account maken, organiseren en beheren of segmenten voor ContextHub- of Client-context beheren:

* Voeg Soorten publiek toe - of Adobe Target publiek of segmenten ContextHub.
* Het publiek beheren.

Een publiek, genoemd *segment* in ContextHub en de Context van de Cliënt, is een klasse van bezoekers die door specifieke criteria worden bepaald, die dan bepaalt wie een gerichte activiteit ziet. Wanneer u een activiteit richt, kunt u of publiek direct in het Doelproces selecteren of meer in de console van het Publiek creëren.

In de console van het publiek, worden de soorten publiek georganiseerd door merk.

Soorten publiek is beschikbaar in de modus Doel voor [ontwerpen, doelinhoud](/help/sites-authoring/content-targeting-touch.md), waarin u ook soorten publiek kunt maken (maar u moet een Adobe Target-publiek maken in de console Soorten publiek). De soorten publiek dat u op het richten wijze creeert verschijnen in de console van het Soorten publiek.

Het publiek wordt weergegeven met een label waarin wordt beschreven welk soort publiek wordt gedefinieerd:

* CH - ContextHub-segment
* CC - Clientcontextsegment
* AT - Adobe Target-publiek

## Het creëren van een Segment ContextHub in de Console van het publiek {#creating-a-contexthub-segment-in-the-audiences-console}

U kunt een segment ContextHub of in de console van het publiek of tijdens het het richten proces tot stand brengen.

Om een segment ContextHub in de console van het publiek tot stand te brengen:

1. Klik in de navigatieconsole op **Personalisatie**. Klikken **Soorten publiek**.
1. Klikken **ContextHub-segment maken**.

   ![screen-shot_2019-03-05at124034](assets/screen-shot_2019-03-05at124034.png)

1. In de **Nieuw ContextHub-segment** voert u een titel in, past u de boost aan en klikt u op **Maken**. Uw nieuw segment ContextHub verschijnt in de publiekslijst.

   >[!NOTE]
   >
   >U kunt de gewijzigde lijst sorteren door op **Gewijzigd** te tikken of te klikken om in aflopende volgorde te sorteren om de nieuwe doelgroep te zien.

Voor meer detail over het creëren van segmenten die ContextHub gebruiken, zie [Het vormen Segmentatie met ContextHub](/help/sites-administering/segmentation.md) documentatie.

## Een Adobe Target-publiek maken met de Audience Console {#creating-an-adobe-target-audience-using-the-audience-console}

U kunt een Adobe Target-publiek rechtstreeks in AEM maken met behulp van de console Soorten publiek.

Het publiek wordt bepaald door regels die bepalen wie in een doelactiviteit inbegrepen is. Een publieksdefinitie kan veelvoudige regels omvatten en elke regel kan veelvoudige parameters omvatten.

Wanneer u meer dan één regel gebruikt, worden deze regels gecombineerd door de exploitant van Boole EN, wat betekent dat om het even welk potentieel publiekslid aan alle bepaalde voorwaarden moet voldoen om in de activiteit worden omvat. Als u bijvoorbeeld een OS-regel EN een browserregel definieert, worden alleen bezoekers die zowel het gedefinieerde besturingssysteem ALS de gedefinieerde browser gebruiken, opgenomen in de activiteit.

>[!NOTE]
>
>Als **Doelpubliek maken **niet wordt weergegeven in het dialoogvenster **Maken** , hebt u niet de benodigde machtigingen om een publiek te maken. U hebt schrijfmachtigingen nodig onder **/etc/segmentatie** om een publiek te kunnen creëren. De makers van groepscontent hebben standaard schrijfmachtigingen.

Een Adobe Target-publiek maken:

1. Klik in de navigatieconsole op **Personalisatie**. Klikken **Soorten publiek**.

   ![screen-shot_2019-03-05at124139](assets/screen-shot_2019-03-05at124139.png)

1. Klik in de console Soorten publiek op **Maken** en vervolgens** Doelpubliek maken**.

   ![chlimage_1-168](assets/chlimage_1-168.png)

1. In de **Adobe Target-configuratie** de doelconfiguratie selecteren en klikken **OK**.
1. In het gebied Rule#1, klik het attributentype en ga om het even welke attributeninformatie op de gebieden in die beschikbaar zijn. Als u klaar bent, selecteert u het vinkje rechts van het kenmerk om het op te slaan. Zie [Kenmerken en de bijbehorende opties](#attributes-and-their-options) voor informatie over alle kenmerken.
1. Klik op **Regel toevoegen** om nog een regel toe te voegen. Voer zoveel regels in als nodig is. De regels worden gecombineerd met de booleaanse operator AND, wat betekent dat de doelgroep aan alle vereisten van elke regel moet voldoen om voor een activiteit in aanmerking te komen.
1. Klik op **Next**.
1. Voer een naam in voor het publiek en klik op **Opslaan**.
1. Klikken **Opslaan**. Uw publiek wordt vermeld in de lijst van het Publiek.

### Kenmerken en hun opties {#attributes-and-their-options}

U kunt het richten regels voor elk van de volgende attributen tot stand brengen:

| **Kenmerk** | **Beschrijving** | **Voor meer informatie** |
|---|---|---|
| **Mobiel** | Het doel mobiele apparaten die op parameters zoals mobiel apparaat, type van apparaat, apparatenverkoper, het schermafmetingen (door pixel) worden gebaseerd, en meer. | Zie [Mobiele documentatie](https://experienceleague.adobe.com/docs/target/using/audiences/create-audiences/categories-audiences/mobile.html) in Adobe Target. |
| **Aangepast** | Aangepaste parameters zijn parameters mbox. Als u om het even welke mbox parameters tot dozen, of de targetPageParams functie doorgeeft, verschijnen die parameters hier voor gebruik in publiek. | Zie [Documentatie voor aangepaste parameters](https://experienceleague.adobe.com/docs/target/using/audiences/create-audiences/categories-audiences/custom-parameters.html) in Adobe Target. |
| **OS** | U kunt zich richten op bezoekers die een bepaald besturingssysteem gebruiken. | Doelgebruikers die Linux®, Macintosh of Windows gebruiken. |
| **Sitepagina&#39;s** | Doelbezoekers die zich op een specifieke pagina bevinden of een specifieke parameter mbox hebben. | Zie [Documentatie over sitepagina&#39;s](https://experienceleague.adobe.com/docs/target/using/audiences/create-audiences/categories-audiences/site-pages.html) in Adobe Target. |
| **Browser** | U kunt zich richten op gebruikers die een specifieke browser of specifieke browseropties gebruiken wanneer zij uw pagina bezoeken. | Zie [Documentatie voor browseropties](https://experienceleague.adobe.com/docs/target/using/audiences/create-audiences/categories-audiences/browser.html) in Adobe Target. |
| **Bezoekerprofiel** | Doelbezoekers die voldoen aan specifieke profielparameters. | Zie [Documentatie bezoekersprofiel](https://experienceleague.adobe.com/docs/target/using/audiences/visitor-profiles/visitor-profile.html) in Adobe Target. |
| **verkeersbronnen** | Doelbezoekers op basis van het zoekprogramma of de bestemmingspagina die hen naar uw site verwijst. | Zie [Documentatie verkeersbronnen](https://experienceleague.adobe.com/docs/target/using/audiences/create-audiences/categories-audiences/traffic-sources.html) in Adobe Target. |

## Een publiek wijzigen in de console Soorten publiek {#modifying-an-audience-in-the-audiences-console}

>[!NOTE]
>
>U kunt alleen Adobe Target-soorten publiek bewerken die zijn gemaakt in hetzelfde AEM waarin u bewerkt. Doelpubliek dat in verschillende AEM is gemaakt, kan niet worden bewerkt.

U kunt om het even welk Contextpubliek van ContextHub of van de Cliënt van de console van het publiek uitgeven. U kunt ook het Adobe Target-publiek bewerken, maar alleen het publiek dat is gemaakt in AEM:

1. Klik in de navigatieconsole op **Personalisatie**. Klikken **Soorten publiek**.
1. Klik het pictogram naast het segment van de ContextHub of van de Cliënt Context u uitgeven, en klik **Bewerken**.
1. Breng om het even welke veranderingen in de segmentredacteur aan. Zie [Clientcontext](/help/sites-administering/campaign-segmentation.md) of [ContextHub](/help/sites-developing/ch-configuring.md) documentatie.
