---
title: Adobe Campaign Forms maken in AEM
seo-title: Adobe Campaign Forms maken in AEM
description: Met AEM kunt u formulieren maken en gebruiken die op uw website met Adobe Campaign werken. U kunt specifieke velden invoegen in uw formulieren en toewijzen aan de Adobe Campaign-database.
seo-description: Met AEM kunt u formulieren maken en gebruiken die op uw website met Adobe Campaign werken. U kunt specifieke velden invoegen in uw formulieren en toewijzen aan de Adobe Campaign-database.
uuid: 7b1028f3-268a-4d4d-bc9f-acd176f5ef3d
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: personalization
content-type: reference
discoiquuid: 3086a8a1-8d2e-455a-a055-91b07d31ea65
translation-type: tm+mt
source-git-commit: a3c303d4e3a85e1b2e794bec2006c335056309fb
workflow-type: tm+mt
source-wordcount: '1264'
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

Het formulier wordt automatisch bijgewerkt op basis van de gebruiker. Zie [Formulierinhoud bewerken](#editing-form-content) voor meer informatie.

## Een sjabloon beschikbaar maken {#making-a-template-available}

Voordat u formulieren kunt maken die specifiek zijn voor Adobe Campaign, moet u de verschillende sjablonen beschikbaar stellen in de AEM toepassing.

Hiervoor raadpleegt u de [documentatie van sjablonen](/help/sites-developing/page-templates-static.md#templateavailability).

Eerst en vooral, controleer de verbinding tussen de auteur en publiceer instanties en Adobe Campaign werkt. Zie [Integratie met Adobe Campaign Standard](/help/sites-administering/campaignstandard.md) of [Integratie met Adobe Campaign 6.1](/help/sites-administering/campaignonpremise.md).

>[!NOTE]
>
>Zorg ervoor dat de **acMapping**-eigenschap op het **jcr:content**-knooppunt op **mapRecipient** of **profile** is ingesteld bij gebruik van respectievelijk Adobe Campaign 6.1.x of Adobe Campaign Standard


### Een formulier maken {#creating-a-form}

1. Starten in sitebeheerder.
1. Blader door de boomstructuur om naar de plaats te gaan waar u het formulier op de gekozen website wilt maken.
1. Selecteer **Nieuw** > **Nieuwe pagina..**.
1. Selecteer **Adobe Campaign Profile (AC 6.1)** of **Adobe Campaign Profile (ACS)** sjabloon en voer de pagina-eigenschappen in.

   >[!NOTE]
   >
   >Als de sjabloon niet beschikbaar is, raadpleegt u de sectie [Een sjabloon beschikbaar maken](/help/sites-classic-ui-authoring/classic-personalization-ac.md#activatingatemplate).

1. Klik op **Maken** om het formulier te maken.

   ![chlimage_1-187](assets/chlimage_1-187.png)

   Vervolgens kunt u de inhoud van uw formulier [bewerken en configureren](#editing-form-content).

## Formulierinhoud bewerken {#editing-form-content}

Forms gewijd aan Adobe Campaign heeft specifieke componenten. Deze componenten hebben een optie waarmee u elk veld van het formulier kunt koppelen aan een veld in de Adobe Campaign-database.

>[!NOTE]
>
>Als de gewenste sjabloon niet beschikbaar is, zie [Een sjabloon beschikbaar maken](/help/sites-classic-ui-authoring/classic-personalization-ac.md#activatingatemplate).

In deze sectie worden alleen specifieke koppelingen naar Adobe Campaign beschreven. Zie [Editmode-componenten](/help/sites-classic-ui-authoring/classic-page-author-edit-mode.md) voor meer informatie over een algemeen overzicht van het gebruik van formulieren in Adobe Experience Manager.

1. Navigeer naar het formulier dat u wilt bewerken.
1. Selecteer **Pagina** > **Pagina-eigenschappen..** gaat dan naar **Cloud Services** tabel van het pop-upvenster.
1. Voeg de Adobe Campaign-service toe door te klikken op **Service toevoegen** en vervolgens de configuratie te selecteren die overeenkomt met uw Adobe Campaign-instantie in de vervolgkeuzelijst van de service. Deze configuratie wordt uitgevoerd wanneer vestiging de verbinding tussen uw instanties. Zie [AEM verbinden met Adobe Campaign](/help/sites-administering/campaignonpremise.md#connecting-aem-to-adobe-campaign) voor meer informatie.

   >[!NOTE]
   >
   >Ontgrendel zo nodig de configuratie door op het hangslotpictogram te klikken om de Adobe Campaign-service toe te voegen.

1. Open de algemene parameters van het formulier met de knop **Bewerken** aan het begin van het formulier. Op het tabblad **Formulier** kunt u een pagina voor bedankt selecteren waarnaar de gebruiker wordt omgeleid nadat hij het formulier heeft gevalideerd.

   Met het formulier **Geavanceerd** kunt u het type formulier selecteren. In het veld **Post Options** kunt u kiezen uit drie typen Adobe Campaign-formulieren:

   * **Adobe Campaign: Profiel** opslaan: Hiermee kunt u een ontvanger maken of bijwerken in Adobe Campaign (standaardwaarde).
   * **Adobe Campaign: Abonneren op services**: Hiermee kunt u de abonnementen van een ontvanger in Adobe Campaign beheren.
   * **Adobe Campaign: Abonnement op services** opzeggen: Hiermee kunt u de abonnementen van een ontvanger in Adobe Campaign annuleren.

   Met het veld **Configuratie van handeling** kunt u opgeven of u het ontvangende profiel in de Adobe Campaign-database wilt maken als dit nog niet bestaat. Om dit te doen, controleer **creeer gebruiker als niet bestaand** optie.

1. Voeg de geselecteerde componenten toe door deze vanuit de gereedschapset te slepen en neer te zetten op het formulier. Zie [Formuliercomponenten Adobe](/help/sites-classic-ui-authoring/classic-personalization-ac-components.md) voor meer informatie over de beschikbare specifieke Adobe Campaign-componenten.

   ![chlimage_1-188](assets/chlimage_1-188.png)

1. Configureer de toegevoegde velden door erop te dubbelklikken. Met het tabblad **Adobe Campaign** kunt u het veld koppelen aan een veld in de Adobe Campaign-ontvankelijke tabel. U kunt ook opgeven of het veld deel uitmaakt van de afstemmingssleutel waarmee ontvangers die al in de Adobe Campaign-database aanwezig zijn, kunnen worden herkend.

   >[!CAUTION]
   >
   >De **Elementnaam** moet voor elk formulierveld verschillend zijn. Wijzig deze indien nodig.
   >
   >Elk formulier moet een **gecodeerde primaire sleutel**-component bevatten om ontvangers correct te kunnen beheren in de Adobe Campaign-database.

1. Activeer de pagina door **Pagina** > **Pagina** in toolbox te selecteren. De pagina wordt geactiveerd op uw site. U kunt het bekijken door naar uw AEM publicatieexemplaar te gaan. De gegevens in de Adobe Campaign-database worden bijgewerkt nadat een formulier is gevalideerd.

## Formulieren {#testing-a-form} testen

Nadat u een formulier hebt gemaakt en formulierinhoud hebt bewerkt, wilt u mogelijk handmatig testen of het formulier naar behoren werkt.

>[!NOTE]
>
>U moet op elk formulier een **Encryted Primary Key**-component hebben. Selecteer in Componenten de optie Adobe Campaign, zodat alleen de componenten zichtbaar zijn.
>
>Hoewel u in deze procedure het epknummer handmatig invoert, krijgen gebruikers in de praktijk een koppeling naar deze pagina (om uw abonnement op te zeggen, in te schrijven of uw profiel bij te werken) binnen een nieuwsbrief. De epk wordt op basis van de gebruiker automatisch bijgewerkt.
>
>Om die verbinding tot stand te brengen, gebruikt u veranderlijke **Belangrijkste middelherkenningsteken** (Adobe Campaign Standard) of **Gecodeerde herkenningsteken** (Adobe Campaign 6.1) (bijvoorbeeld, in een **Tekst &amp; Personalisatie (Campagne)** component), die met epk in Adobe Campaign verbindt.

Hiervoor moet u handmatig de EPK van een Adobe Campaign-profiel ophalen en dit vervolgens toevoegen aan de URL:

1. De gecodeerde primaire sleutel (EPK) van een Adobe Campaign-profiel ophalen:

   * In Adobe Campaign Standard - navigeer naar **Profielen en soorten publiek** > **Profielen**, waarin de bestaande profielen worden vermeld. Zorg ervoor de lijst **Belangrijkste Herkenningsteken van het Middel** in een kolom toont (Dit kan worden gevormd door **te klikken/te tikken lijst**). Kopieer de belangrijkste resource-id van het gewenste profiel.
   * Ga in Adobe Campaign 6.11 naar **Profielen en doelen** > **Ontvangers**, die de bestaande profielen opsomt. Zorg ervoor dat de tabel het veld **Encrypted identifier** in een kolom weergeeft (dit kan worden geconfigureerd door met de rechtermuisknop op een item te klikken en de lijst **Configureren te selecteren..**). Kopieer de gecodeerde id van het gewenste profiel.

1. Open AEM de formulierpagina in het publicatieexemplaar en voeg de EPK van stap 1 toe als URL-parameter: dezelfde naam gebruiken die u eerder in de EPK-component hebt gedefinieerd bij het ontwerpen van het formulier (bijvoorbeeld: `?epk=...`)
1. Het formulier kan nu worden gebruikt om de gegevens en abonnementen voor het gekoppelde Adobe Campaign-profiel te wijzigen. Nadat u een aantal velden hebt gewijzigd en het formulier hebt verzonden, kunt u in Adobe Campaign controleren of de desbetreffende gegevens zijn bijgewerkt.

De gegevens in de Adobe Campaign-database worden bijgewerkt nadat een formulier is gevalideerd.
