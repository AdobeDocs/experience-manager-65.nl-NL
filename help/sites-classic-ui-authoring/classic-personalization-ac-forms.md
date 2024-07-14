---
title: Adobe Campaign Forms maken in AEM
description: Met AEM kunt u formulieren maken en gebruiken die op uw website met Adobe Campaign werken. U kunt specifieke velden invoegen in uw formulieren en toewijzen aan de Adobe Campaign-database.
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: personalization
content-type: reference
exl-id: 3f9ed24e-c54b-4bd4-9212-eabc67bb540e
solution: Experience Manager, Experience Manager Sites
feature: Authoring,Personalization
role: User
source-git-commit: 305227eff3c0d6414a5ae74bcf3a74309dccdd13
workflow-type: tm+mt
source-wordcount: '1227'
ht-degree: 0%

---

# Adobe Campaign Forms maken in AEM{#creating-adobe-campaign-forms-in-aem}

Met AEM kunt u formulieren maken en gebruiken die op uw website met Adobe Campaign werken. U kunt specifieke velden invoegen in uw formulieren en toewijzen aan de Adobe Campaign-database.

U kunt nieuwe contactabonnementen, unsubscriptions, en gegevens van het gebruikersprofiel beheren, allen terwijl het integreren van hun gegevens in uw gegevensbestand van Adobe Campaign.

Als u Adobe Campaign-formulieren wilt gebruiken in AEM, moet u de volgende stappen uitvoeren, zoals beschreven in dit document:

1. Een sjabloon beschikbaar maken.
1. Maak een formulier.
1. Formulierinhoud bewerken.

Standaard zijn er drie typen formulieren beschikbaar, specifiek voor Adobe Campaign:

* Een profiel opslaan
* Abonneren op een service
* Abonnement op een service opzeggen

Deze formulieren definiëren een URL-parameter die de gecodeerde primaire sleutel van een Adobe Campaign-profiel accepteert. Op basis van deze URL-parameter werkt het formulier de gegevens van het gekoppelde Adobe Campaign-profiel bij.

Hoewel u deze formulieren onafhankelijk maakt, genereert u doorgaans een gepersonaliseerde koppeling naar een formulierpagina in de nieuwsbrief, zodat ontvangers de koppeling kunnen openen en hun profielgegevens kunnen aanpassen (of ze zich niet abonneren, zich abonneren of hun profiel bijwerken).

Het formulier wordt automatisch bijgewerkt op basis van de gebruiker. Zie [ het Uitgeven van de Inhoud van de Vorm ](#editing-form-content) voor meer informatie.

## Een sjabloon beschikbaar maken {#making-a-template-available}

Voordat u formulieren kunt maken die specifiek zijn voor Adobe Campaign, moet u de verschillende sjablonen beschikbaar stellen in de AEM toepassing.

Om dit te doen, zie de [ documentatie van Malplaatjes ](/help/sites-developing/page-templates-static.md#templateavailability).

Eerst en vooral, controleer de verbinding tussen de auteur en publiceer instanties en Adobe Campaign werkt. Zie [ Integrerend met Adobe Campaign Standard ](/help/sites-administering/campaignstandard.md) of [ Integrerend met Adobe Campaign 6.1 ](/help/sites-administering/campaignonpremise.md).

>[!NOTE]
>
>Zorg ervoor het **acMapping** bezit op jcr van de pagina **:content** knoop wordt geplaatst aan **mapRecipient** of **profiel** wanneer het gebruiken van Adobe Campaign 6.1.x of Adobe Campaign Standard, respectievelijk
>

### Een formulier maken {#creating-a-form}

1. Starten in sitebeheerder.
1. Blader door de boomstructuur om naar de plaats te gaan waar u het formulier op de gekozen website wilt maken.
1. Selecteer **Nieuw** > **Nieuwe pagina...**.
1. Selecteer één van beide **Adobe Campaign Profiel (AC 6.1)** of **het Profiel van Adobe Campaign (ACS)** malplaatje en ga de paginaeigenschappen in.

   >[!NOTE]
   >
   >Als het malplaatje niet beschikbaar is, zie [ het Maken van een malplaatje beschikbaar ](/help/sites-classic-ui-authoring/classic-personalization-ac.md#activatingatemplate) sectie.

1. Klik **creëren** om de vorm tot stand te brengen.

   ![ chlimage_1-187 ](assets/chlimage_1-187.png)

   U kunt dan [ uitgeven en de inhoud van uw vorm vormen ](#editing-form-content).

## Formulierinhoud bewerken {#editing-form-content}

Forms gewijd aan Adobe Campaign heeft specifieke componenten. Deze componenten hebben een optie waarmee u elk veld van het formulier kunt koppelen aan een veld in de Adobe Campaign-database.

>[!NOTE]
>
>Als het gewenste malplaatje niet beschikbaar is, zie [ het Maken van een malplaatje beschikbaar ](/help/sites-classic-ui-authoring/classic-personalization-ac.md#activatingatemplate).

In deze sectie worden alleen specifieke koppelingen naar Adobe Campaign beschreven. Voor meer informatie over een meer algemeen overzicht van hoe te om vormen in Adobe Experience Manager te gebruiken, zie [ componenten Editmode ](/help/sites-classic-ui-authoring/classic-page-author-edit-mode.md).

1. Navigeer naar het formulier dat u wilt bewerken.
1. In toolbox, gaat de uitgezochte **Pagina** > **Eigenschappen van de Pagina..** dan naar het **Cloud Servicen** lusje van het pop-up venster.
1. Voeg de dienst van Adobe Campaign toe door **te klikken voegt de dienst** toe, en dan het selecteren van de configuratie die aan uw instantie van Adobe Campaign in de drop-down lijst van de dienst beantwoordt. Deze configuratie wordt uitgevoerd wanneer vestiging de verbinding tussen uw instanties. Voor meer informatie, zie [ Verbindend AEM met Adobe Campaign ](/help/sites-administering/campaignonpremise.md#connecting-aem-to-adobe-campaign).

   >[!NOTE]
   >
   >Ontgrendel zo nodig de configuratie door op het hangslotpictogram te klikken om de Adobe Campaign-service toe te voegen.

1. Heb toegang tot de algemene parameters van de vorm gebruikend **uitgeeft** knoop die bij het begin van de vorm wordt gevonden. Het **lusje van de Vorm** laat u een dank u pagina selecteren waaraan de gebruiker na het bevestigen van de vorm opnieuw zal worden gericht.

   Het **Geavanceerde** vorm laat u het type van vorm selecteren. Het **gebied van Opties van 0} Post {geeft u de keus tussen drie types van de vormen van Adobe Campaign:**

   * **Adobe Campaign: sparen profiel**: laat u tot een ontvanger in Adobe Campaign (standaardwaarde) leiden of bijwerken.
   * **Adobe Campaign: Abonneer aan de Diensten**: laat u de abonnementen van een ontvanger in Adobe Campaign beheren.
   * **Adobe Campaign: Unsubscribe van de Diensten**: laat u de abonnementen van een ontvanger in Adobe Campaign annuleren.

   Het **gebied van de Configuratie van de Actie** laat u specificeren al dan niet u het ontvankelijke profiel in het gegevensbestand van Adobe Campaign zou willen tot stand brengen als het nog niet bestaat. Om dit te doen, controleer **creeer gebruiker als niet bestaande** optie.

1. Voeg de geselecteerde componenten toe door deze vanuit de gereedschapset te slepen en neer te zetten op het formulier. Voor meer informatie over de beschikbare specifieke componenten van Adobe Campaign, zie {de Componenten van de Vorm van 0} Adobe ](/help/sites-classic-ui-authoring/classic-personalization-ac-components.md).[

   ![ chlimage_1-188 ](assets/chlimage_1-188.png)

1. Configureer de toegevoegde velden door erop te dubbelklikken. Het **Adobe Campaign** lusje laat u het gebied met een gebied in de ontvankelijke lijst van Adobe Campaign verbinden. U kunt ook opgeven of het veld deel uitmaakt van de afstemmingssleutel waarmee ontvangers die al in de Adobe Campaign-database aanwezig zijn, kunnen worden herkend.

   >[!CAUTION]
   >
   >De **Naam van het Element** moet voor elk vormgebied verschillend zijn. Wijzig deze indien nodig.
   >
   >Elk formulier moet een **Gecodeerde Primaire Zeer belangrijke** component bevatten om ontvangers in het gegevensbestand van Adobe Campaign correct te beheren.

1. Activeer de pagina door **Pagina** te selecteren > **activeer Pagina** in toolbox. De pagina wordt geactiveerd op uw site. U kunt het bekijken door naar uw AEM publicatieexemplaar te gaan. De gegevens in de Adobe Campaign-database worden bijgewerkt nadat een formulier is gevalideerd.

## Een formulier testen {#testing-a-form}

Nadat u een formulier hebt gemaakt en formulierinhoud hebt bewerkt, wilt u mogelijk handmatig testen of het formulier naar behoren werkt.

>[!NOTE]
>
>U moet een **Erkende Primaire Belangrijkste** component op elke vorm hebben. Selecteer in Componenten de optie Adobe Campaign, zodat alleen de componenten zichtbaar zijn.
>
>Hoewel u in deze procedure het epknummer handmatig invoert, krijgen gebruikers in de praktijk een koppeling naar deze pagina (om uw abonnement op te zeggen, in te schrijven of uw profiel bij te werken) binnen een nieuwsbrief. De epk wordt op basis van de gebruiker automatisch bijgewerkt.
>
>Om die verbinding tot stand te brengen, gebruikt u het veranderlijke **Belangrijkste middelherkenningsteken** (Adobe Campaign Standard) of **Gecodeerde herkenningsteken** (Adobe Campaign 6.1) (bijvoorbeeld, in a **Tekst &amp; Personalization (Campagne)** component), die met epk in Adobe Campaign verbindt.

Hiervoor moet u handmatig de EPK van een Adobe Campaign-profiel ophalen en dit vervolgens toevoegen aan de URL:

1. De gecodeerde primaire sleutel (EPK) van een Adobe Campaign-profiel ophalen:

   * In Adobe Campaign Standard - navigeer aan **Profielen en Soorten publiek** > **Profielen**, die van de bestaande profielen een lijst maken. Zorg ervoor de lijst het **Belangrijkste Herkenningsteken van het Middel** in een kolom toont (dit kan worden gevormd door te klikken/te tikken **vormt lijst**). Kopieer de belangrijkste resource-id van het gewenste profiel.
   * In Adobe Campaign 6.11, ga naar **Profielen en Doelen** > **Ontvangers**, die van de bestaande profielen een lijst maken. Zorg ervoor de lijst het **Gecodeerde herkenningsteken** gebied in een kolom toont (dit kan worden gevormd door op een ingang met de rechtermuisknop te klikken en **te selecteren vormt lijst...**). Kopieer de gecodeerde id van het gewenste profiel.

1. Open AEM de formulierpagina in het publicatieexemplaar en voeg de EPK vanuit stap 1 toe als een URL-parameter: gebruik dezelfde naam die u eerder in de EPK-component hebt gedefinieerd bij het ontwerpen van het formulier (bijvoorbeeld: `?epk=...`)
1. Het formulier kan nu worden gebruikt om de gegevens en abonnementen voor het gekoppelde Adobe Campaign-profiel te wijzigen. Nadat u een aantal velden hebt gewijzigd en het formulier hebt verzonden, kunt u in Adobe Campaign controleren of de desbetreffende gegevens zijn bijgewerkt.

De gegevens in de Adobe Campaign-database worden bijgewerkt nadat een formulier is gevalideerd.
