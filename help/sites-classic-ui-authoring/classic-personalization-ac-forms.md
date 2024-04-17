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

Het formulier wordt automatisch bijgewerkt op basis van de gebruiker. Zie [Formulierinhoud bewerken](#editing-form-content) voor meer informatie .

## Een sjabloon beschikbaar maken {#making-a-template-available}

Voordat u formulieren kunt maken die specifiek zijn voor Adobe Campaign, moet u de verschillende sjablonen beschikbaar stellen in de AEM toepassing.

Zie voor meer informatie de [Documentatie voor sjablonen](/help/sites-developing/page-templates-static.md#templateavailability).

Eerst en vooral, controleer de verbinding tussen de auteur en publiceer instanties en Adobe Campaign werkt. Zie [Integreren met Adobe Campaign Standard](/help/sites-administering/campaignstandard.md) of [Integratie met Adobe Campaign 6.1](/help/sites-administering/campaignonpremise.md).

>[!NOTE]
>
>Zorg ervoor dat de **acMapping** eigenschap op de pagina **jcr:inhoud** node is ingesteld op **mapRecipient** of **profiel** bij gebruik van respectievelijk Adobe Campaign 6.1.x of Adobe Campaign Standard
>

### Een formulier maken {#creating-a-form}

1. Starten in sitebeheerder.
1. Blader door de boomstructuur om naar de plaats te gaan waar u het formulier op de gekozen website wilt maken.
1. Selecteren **Nieuw** > **Nieuwe pagina...**.
1. Selecteer een van beide **Adobe Campaign-profiel (AC 6.1)** of **Adobe Campaign-profiel (ACS)** en voert u de pagina-eigenschappen in.

   >[!NOTE]
   >
   >Als de sjabloon niet beschikbaar is, raadpleegt u de [Een sjabloon beschikbaar maken](/help/sites-classic-ui-authoring/classic-personalization-ac.md#activatingatemplate) sectie.

1. Klikken **Maken** om het formulier te maken.

   ![chlimage_1-187](assets/chlimage_1-187.png)

   U kunt vervolgens [de inhoud van uw formulier bewerken en configureren](#editing-form-content).

## Formulierinhoud bewerken {#editing-form-content}

Forms gewijd aan Adobe Campaign heeft specifieke componenten. Deze componenten hebben een optie waarmee u elk veld van het formulier kunt koppelen aan een veld in de Adobe Campaign-database.

>[!NOTE]
>
>Als de gewenste sjabloon niet beschikbaar is, raadpleegt u [Een sjabloon beschikbaar maken](/help/sites-classic-ui-authoring/classic-personalization-ac.md#activatingatemplate).

In deze sectie worden alleen specifieke koppelingen naar Adobe Campaign beschreven. Ga voor meer informatie over een meer algemeen overzicht van het gebruik van formulieren in Adobe Experience Manager naar [Editmode-componenten](/help/sites-classic-ui-authoring/classic-page-author-edit-mode.md).

1. Navigeer naar het formulier dat u wilt bewerken.
1. Selecteer in de gereedschapset **Pagina** > **Pagina-eigenschappen...** ga vervolgens naar de **Cloud Servicen** van het pop-upvenster.
1. De Adobe Campaign-service toevoegen door op **Service toevoegen** en selecteert u vervolgens de configuratie die overeenkomt met uw Adobe Campaign-instantie in de vervolgkeuzelijst van de service. Deze configuratie wordt uitgevoerd wanneer vestiging de verbinding tussen uw instanties. Zie voor meer informatie [AEM verbinden met Adobe Campaign](/help/sites-administering/campaignonpremise.md#connecting-aem-to-adobe-campaign).

   >[!NOTE]
   >
   >Ontgrendel zo nodig de configuratie door op het hangslotpictogram te klikken om de Adobe Campaign-service toe te voegen.

1. De algemene parameters van het formulier openen met de **Bewerken** aan het begin van het formulier gevonden. De **Formulier** kunt u een pagina voor bedankt selecteren waarnaar de gebruiker wordt omgeleid nadat hij het formulier heeft gevalideerd.

   De **Geavanceerd** kunt u het type formulier selecteren. De **Post-opties** U kunt kiezen uit drie typen Adobe Campaign-formulieren:

   * **Adobe Campaign: profiel opslaan**: hiermee kunt u een ontvanger maken of bijwerken in Adobe Campaign (standaardwaarde).
   * **Adobe Campaign: abonneren op services**: Hiermee kunt u de abonnementen van een ontvanger in Adobe Campaign beheren.
   * **Adobe Campaign: Abonnement op services opzeggen**: Hiermee kunt u de abonnementen van een ontvanger in Adobe Campaign annuleren.

   De **Configuratie van handelingen** in het veld kunt u opgeven of u het ontvangende profiel in de Adobe Campaign-database wilt maken als dit nog niet bestaat. Controleer de **Gebruiker maken indien niet bestaand** -optie.

1. Voeg de geselecteerde componenten toe door deze vanuit de gereedschapset te slepen en neer te zetten op het formulier. Zie voor meer informatie over de beschikbare specifieke Adobe Campaign-componenten [Formuliercomponenten Adoben](/help/sites-classic-ui-authoring/classic-personalization-ac-components.md).

   ![chlimage_1-188](assets/chlimage_1-188.png)

1. Configureer de toegevoegde velden door erop te dubbelklikken. De **Adobe Campaign** kunt u het veld koppelen aan een veld in de tabel voor ontvangers van Adobe Campaign. U kunt ook opgeven of het veld deel uitmaakt van de afstemmingssleutel waarmee ontvangers die al in de Adobe Campaign-database aanwezig zijn, kunnen worden herkend.

   >[!CAUTION]
   >
   >De **Elementnaam** moet voor elk formulierveld anders zijn. Wijzig deze indien nodig.
   >
   >Elk formulier moet een **Gecodeerde primaire sleutel** om ontvangers in de Adobe Campaign-database correct te beheren.

1. De pagina activeren door **Pagina** > **Pagina activeren** in de gereedschapset. De pagina wordt geactiveerd op uw site. U kunt het bekijken door naar uw AEM publicatieexemplaar te gaan. De gegevens in de Adobe Campaign-database worden bijgewerkt nadat een formulier is gevalideerd.

## Een formulier testen {#testing-a-form}

Nadat u een formulier hebt gemaakt en formulierinhoud hebt bewerkt, wilt u mogelijk handmatig testen of het formulier naar behoren werkt.

>[!NOTE]
>
>U moet een **Primaire sleutel in afbeelding** op elk formulier. Selecteer in Componenten de optie Adobe Campaign, zodat alleen de componenten zichtbaar zijn.
>
>Hoewel u in deze procedure het epknummer handmatig invoert, krijgen gebruikers in de praktijk een koppeling naar deze pagina (om uw abonnement op te zeggen, in te schrijven of uw profiel bij te werken) binnen een nieuwsbrief. De epk wordt op basis van de gebruiker automatisch bijgewerkt.
>
>Als u die koppeling wilt maken, gebruikt u de variabele **Hoofdresource-id**(Adobe Campaign Standard) of **Gecodeerde id** (Adobe Campaign 6.1) (bijvoorbeeld in **Tekst en persoonlijke voorkeur (campagne)** ), die een koppeling vormt naar het epk in Adobe Campaign.

Hiervoor moet u handmatig de EPK van een Adobe Campaign-profiel ophalen en dit vervolgens toevoegen aan de URL:

1. De gecodeerde primaire sleutel (EPK) van een Adobe Campaign-profiel ophalen:

   * In Adobe Campaign Standard - navigeer naar **Profielen en publiek** > **Profielen**, waarin de bestaande profielen worden vermeld. Zorg ervoor dat de tabel de **Hoofd Resource Identifier** veld in een kolom (dit kan worden geconfigureerd door te klikken/tikken **Lijst configureren**). Kopieer de belangrijkste resource-id van het gewenste profiel.
   * Ga in Adobe Campaign 6.1 naar **Profielen en doelen** >  **Ontvangers**, waarin de bestaande profielen worden vermeld. Zorg ervoor dat de tabel de **Gecodeerde id** veld in een kolom (dit kan worden geconfigureerd door met de rechtermuisknop op een item te klikken en **Lijst configureren...**). Kopieer de gecodeerde id van het gewenste profiel.

1. Open AEM de formulierpagina op het publicatieexemplaar en voeg de EPK vanuit stap 1 toe als een URL-parameter: gebruik dezelfde naam die u eerder in de EPK-component hebt gedefinieerd bij het ontwerpen van het formulier (bijvoorbeeld: `?epk=...`)
1. Het formulier kan nu worden gebruikt om de gegevens en abonnementen voor het gekoppelde Adobe Campaign-profiel te wijzigen. Nadat u een aantal velden hebt gewijzigd en het formulier hebt verzonden, kunt u in Adobe Campaign controleren of de desbetreffende gegevens zijn bijgewerkt.

De gegevens in de Adobe Campaign-database worden bijgewerkt nadat een formulier is gevalideerd.
