---
title: Adobe Campagneformulieren maken in AEM
seo-title: Adobe Campagneformulieren maken in AEM
description: Met AEM kunt u formulieren maken en gebruiken die op uw website werken met Adobe Campaign. U kunt specifieke velden invoegen in uw formulieren en toewijzen aan de Adobe Campagne-database.
seo-description: Met AEM kunt u formulieren maken en gebruiken die op uw website werken met Adobe Campaign. U kunt specifieke velden invoegen in uw formulieren en toewijzen aan de Adobe Campagne-database.
uuid: 7b1028f3-268a-4d4d-bc9f-acd176f5ef3d
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: personalization
content-type: reference
discoiquuid: 3086a8a1-8d2e-455a-a055-91b07d31ea65
translation-type: tm+mt
source-git-commit: a3c303d4e3a85e1b2e794bec2006c335056309fb

---


# Adobe Campagneformulieren maken in AEM{#creating-adobe-campaign-forms-in-aem}

Met AEM kunt u formulieren maken en gebruiken die op uw website werken met Adobe Campaign. U kunt specifieke velden invoegen in uw formulieren en toewijzen aan de Adobe Campagne-database.

U kunt nieuwe contactabonnementen, abonnementen, en gegevens van het gebruikersprofiel beheren, allen terwijl het integreren van hun gegevens in uw gegevensbestand van de Campagne van Adobe.

Als u Adobe Campagne-formulieren wilt gebruiken in AEM, moet u de volgende stappen uitvoeren, die in dit document worden beschreven:

1. Een sjabloon beschikbaar maken.
1. Maak een formulier.
1. Formulierinhoud bewerken.

Er zijn standaard drie typen formulieren beschikbaar, die specifiek zijn voor Adobe Campagne:

* Een profiel opslaan
* Abonneren op een service
* Abonnement op een service opzeggen

Deze formulieren definiëren een URL-parameter die de gecodeerde primaire sleutel van een Adobe Campagne-profiel accepteert. Op basis van deze URL-parameter werkt het formulier de gegevens van het bijbehorende Adobe Campagne-profiel bij.

Hoewel u deze formulieren onafhankelijk maakt, genereert u doorgaans een gepersonaliseerde koppeling naar een formulierpagina in de nieuwsbrief, zodat ontvangers de koppeling kunnen openen en hun profielgegevens kunnen aanpassen (of ze zich niet abonneren, zich abonneren of hun profiel bijwerken).

Het formulier wordt automatisch bijgewerkt op basis van de gebruiker. Zie [Formulierinhoud](#editing-form-content) bewerken voor meer informatie.

## Een sjabloon beschikbaar maken {#making-a-template-available}

Voordat u formulieren kunt maken die specifiek zijn voor Adobe Campaign, moet u de verschillende sjablonen beschikbaar stellen in uw AEM-toepassing.

Raadpleeg de documentatie bij [Sjablonen om dit te doen](/help/sites-developing/page-templates-static.md#templateavailability).

Controleer eerst de verbinding tussen de auteur en publiceer instanties en Adobe Campaign werkt. Zie [Integreren met Adobe Campagne Standard](/help/sites-administering/campaignstandard.md) of [Integreren met Adobe Campagne 6.1](/help/sites-administering/campaignonpremise.md).

>[!NOTE]
>
>Zorg ervoor dat de eigenschap **acMapping** op het knooppunt **jcr:content** van de pagina is ingesteld op **mapRecipient** of **profiel** bij gebruik van respectievelijk Adobe Campagne 6.1.x of Adobe Campaign Standard


### Een formulier maken {#creating-a-form}

1. Starten in sitebeheerder.
1. Blader door de boomstructuur om naar de plaats te gaan waar u het formulier op de gekozen website wilt maken.
1. **Selecteer** Nieuw **>** Nieuwe pagina... .
1. Selecteer de sjabloon **Adobe Campagneprofiel (AC 6.1)** of **Adobe Campagneprofiel (ACS)** en voer de pagina-eigenschappen in.

   >[!NOTE]
   >
   >Als de sjabloon niet beschikbaar is, raadpleegt u het gedeelte [Een sjabloon beschikbaar](/help/sites-classic-ui-authoring/classic-personalization-ac.md#activatingatemplate) maken.

1. Klik op **Maken** om het formulier te maken.

   ![chlimage_1-187](assets/chlimage_1-187.png)

   U kunt vervolgens de inhoud [van het formulier](#editing-form-content)bewerken en configureren.

## Formulierinhoud bewerken {#editing-form-content}

Formulieren die zijn gewijd aan Adobe Campaign, hebben specifieke componenten. Deze componenten hebben een optie waarmee u elk veld van het formulier kunt koppelen aan een veld in de Adobe Campagne-database.

>[!NOTE]
>
>Zie Een sjabloon beschikbaar [maken als de gewenste sjabloon niet beschikbaar](/help/sites-classic-ui-authoring/classic-personalization-ac.md#activatingatemplate)is.

In deze sectie worden alleen specifieke koppelingen naar Adobe Campaign beschreven. Zie Componenten [van de](/help/sites-classic-ui-authoring/classic-page-author-edit-mode.md)bewerkingsmodus voor meer informatie over een algemeen overzicht van het gebruik van formulieren in Adobe Experience Manager.

1. Navigeer naar het formulier dat u wilt bewerken.
1. **Selecteer** Pagina **>** Pagina-eigenschappen in de gereedschapset.. Ga vervolgens naar het tabblad **Cloud Services** van het pop-upvenster.
1. Voeg de Adobe Campagne-service toe door op de service **** Toevoegen te klikken en vervolgens in de vervolgkeuzelijst van de service de configuratie te selecteren die overeenkomt met uw Adobe Campagne-instantie. Deze configuratie wordt uitgevoerd wanneer vestiging de verbinding tussen uw instanties. Zie AEM [verbinden met Adobe Campagne](/help/sites-administering/campaignonpremise.md#connecting-aem-to-adobe-campaign)voor meer informatie.

   >[!NOTE]
   >
   >Ontgrendel zo nodig de configuratie door op het hangslotpictogram te klikken om de Adobe Campagne-service toe te voegen.

1. Open de algemene parameters van het formulier met de knop **Bewerken** aan het begin van het formulier. Op het tabblad **Formulier** kunt u een pagina voor bedankt selecteren waarnaar de gebruiker wordt omgeleid nadat hij het formulier heeft gevalideerd.

   Met het formulier **Geavanceerd** kunt u het type formulier selecteren. In het veld **Post Options** kunt u kiezen uit drie typen Adobe Campagne-formulieren:

   * **Adobe-campagne: Profiel** opslaan: Hiermee kunt u een ontvanger maken of bijwerken in Adobe Campaign (standaardwaarde).
   * **Adobe-campagne: Abonneren op services**: Hiermee kunt u de abonnementen van een ontvanger beheren in Adobe Campaign.
   * **Adobe-campagne: Abonnement op services** opzeggen: Hiermee kunt u de abonnementen van een ontvanger in Adobe Campaign annuleren.
   In het veld Configuratie **van** handeling kunt u opgeven of u het ontvangende profiel in de Adobe Campagne-database wilt maken als dit nog niet bestaat. Schakel de optie Gebruiker **maken als deze nog niet bestaat** in om dit te doen.

1. Voeg de geselecteerde componenten toe door deze vanuit de gereedschapset te slepen en neer te zetten op het formulier. Zie [Adobe Form Components](/help/sites-classic-ui-authoring/classic-personalization-ac-components.md)voor meer informatie over de beschikbare specifieke componenten van Adobe Campagne.

   ![chlimage_1-188](assets/chlimage_1-188.png)

1. Configureer de toegevoegde velden door erop te dubbelklikken. Op het tabblad **Adobe-campagne** kunt u het veld koppelen aan een veld in de ontvankelijke tabel voor Adobe-campagne. U kunt ook opgeven of het veld deel uitmaakt van de afstemmingssleutel waarmee ontvangers die al aanwezig zijn in de Adobe Campagne-database, kunnen worden herkend.

   >[!CAUTION]
   >
   >De **elementnaam** moet voor elk formulierveld anders zijn. Wijzig deze indien nodig.
   >
   >Elk formulier moet een **gecodeerde primaire sleutel** bevatten om ontvangers correct te kunnen beheren in de Adobe Campagne-database.

1. Activeer de pagina door **Pagina** > Pagina **** activeren te selecteren in de gereedschapset. De pagina wordt geactiveerd op uw site. U kunt het bekijken door naar uw AEM- publicatieexemplaar te gaan. De gegevens in de Adobe Campagne-database worden bijgewerkt nadat een formulier is gevalideerd.

## Een formulier testen {#testing-a-form}

Nadat u een formulier hebt gemaakt en formulierinhoud hebt bewerkt, wilt u mogelijk handmatig testen of het formulier naar behoren werkt.

>[!NOTE]
>
>U moet op elk formulier een **component voor de primaire sleutel** hebben. Selecteer Adobe Campagne in Componenten, zodat alleen de componenten zichtbaar zijn.
>
>Hoewel u in deze procedure het epknummer handmatig invoert, krijgen gebruikers in de praktijk een koppeling naar deze pagina (om uw abonnement op te zeggen, in te schrijven of uw profiel bij te werken) binnen een nieuwsbrief. De epk wordt op basis van de gebruiker automatisch bijgewerkt.
>
>Als u die koppeling wilt maken, gebruikt u de variabele **Hoofd-resource-id**(Adobe Campaign Standard) of de **Versleutelde-id** (Adobe Campagne 6.1) (bijvoorbeeld in een **component Text &amp; Personalization (Campaign)** ) die een koppeling vormt naar de koppeling EPK in Adobe Campaign.

Hiervoor moet u handmatig de EPK van een Adobe Campagneprofiel ophalen en dit vervolgens toevoegen aan de URL:

1. De gecodeerde primaire sleutel (EPK) van een Adobe Campagneprofiel ophalen:

   * In de Standaard van de Campagne van Adobe - navigeer aan **Profielen en Soorten** > **Profielen**, die de bestaande profielen een lijst maken. Zorg ervoor de lijst het **Belangrijkste gebied van het Middel** in een kolom toont (Dit kan worden gevormd door te klikken/het tikken **vormt lijst**). Kopieer de belangrijkste resource-id van het gewenste profiel.
   * Ga in Adobe Campagne 6.11 naar **Profielen en doelen** > **Ontvangers**. Hierin staan de bestaande profielen. Zorg ervoor dat de tabel het veld **Gecodeerde id** in een kolom weergeeft (dit kan worden geconfigureerd door met de rechtermuisknop op een item te klikken en de lijst **Configureren te selecteren...**). Kopieer de gecodeerde id van het gewenste profiel.

1. Open in AEM de formulierpagina op het publicatieexemplaar en voeg de EPK van stap 1 toe als een URL-parameter: dezelfde naam gebruiken die u eerder in de EPK-component hebt gedefinieerd bij het ontwerpen van het formulier (bijvoorbeeld: `?epk=...`)
1. Het formulier kan nu worden gebruikt om de gegevens en abonnementen voor het gekoppelde Adobe Campagne-profiel te wijzigen. Nadat u een aantal velden hebt gewijzigd en het formulier hebt verzonden, kunt u in Adobe Campaign controleren of de desbetreffende gegevens zijn bijgewerkt.

De gegevens in de Adobe Campagne-database worden bijgewerkt nadat een formulier is gevalideerd.
