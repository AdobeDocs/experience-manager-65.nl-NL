---
title: Adobe Campaign Forms maken in Adobe Experience Manager
description: Met Adobe Experience Manager kunt u formulieren maken en gebruiken die met Adobe Campaign werken op uw website
contentOwner: Chris Bohnert
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: personalization
exl-id: 7d60673e-484a-4447-83cf-d62a0d7ad745
solution: Experience Manager, Experience Manager Sites
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '1281'
ht-degree: 0%

---

# Adobe Campaign Forms maken in AEM {#creating-adobe-campaign-forms-in-aem}

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

Zie voor meer informatie de [Documentatie voor sjablonen](/help/sites-developing/templates.md#template-availability).

## Een formulier maken {#creating-a-form}

Eerst en vooral, controleer de verbinding tussen de auteur en publiceer instanties en Adobe Campaign werkt. Zie [Integreren met Adobe Campaign Standard](/help/sites-administering/campaignstandard.md) of [Integreren met Adobe Campaign Classic](/help/sites-administering/campaignonpremise.md).

>[!NOTE]
>
>Zorg ervoor dat de **acMapping** eigenschap op de pagina **jcr:inhoud** node is ingesteld op **mapRecipient** of **profiel** bij gebruik van respectievelijk Adobe Campaign Classic of Adobe Campaign Standard
>

1. Navigeer in Sites AEM naar de plaats waar u een pagina wilt maken.
1. Een pagina maken en selecteren **Adobe Campaign Classic-profiel** of **Adobe Campaign Standard-profiel** en klik op **Volgende**.

   ![chlimage_1-43](assets/chlimage_1-43a.png)

   >[!NOTE]
   >
   >Als de gewenste sjabloon niet beschikbaar is, raadpleegt u [Beschikbaarheid sjabloon](/help/sites-developing/templates.md#template-availability).

1. In de **Naam** , voegt u de naam van de pagina toe. Dit moet een geldige JCR-naam zijn.
1. In de **Titel** veld, voer een titel in en klik op **Maken**.
1. Open de pagina en selecteer **Eigenschappen openen** en in Cloud Servicen de configuratie van Adobe Campaign toevoegen en het vinkje selecteren om uw veranderingen te bewaren.

   ![chlimage_1-44](assets/chlimage_1-44a.png)

1. Op de pagina, in **Begin formulier** -component selecteert u het type formulier dat het is - **Abonneren, Abonnement opzeggen,** of **Profiel opslaan**. U kunt slechts één type per formulier hebben. U kunt nu [de inhoud van het formulier bewerken](#editing-form-content).

## Formulierinhoud bewerken {#editing-form-content}

Forms gewijd aan Adobe Campaign heeft specifieke componenten. Deze componenten hebben een optie waarmee u elk veld van het formulier kunt koppelen aan een veld in de Adobe Campaign-database.

>[!NOTE]
>
>Als de gewenste sjabloon niet beschikbaar is, raadpleegt u [Een sjabloon beschikbaar maken](/help/sites-authoring/adobe-campaign.md).

In deze sectie worden alleen specifieke koppelingen naar Adobe Campaign beschreven. Ga voor meer informatie over een meer algemeen overzicht van het gebruik van formulieren in Adobe Experience Manager naar [Editmode-componenten](/help/sites-authoring/default-components-foundation.md).

1. Selecteren **Eigenschappen openen** en in Cloud Servicen de configuratie van Adobe Campaign toevoegen en het vinkje selecteren om uw veranderingen te bewaren.

   ![chlimage_1-45](assets/chlimage_1-45a.png)

1. Op de pagina, in **Begin formulier** op het configuratiepictogram.

   ![chlimage_1-46](assets/chlimage_1-46a.png)

1. Klik op de knop **Geavanceerd** en selecteert u het type formulier dat het is - **Abonneren, Abonnement opzeggen,** of **Profiel opslaan** en klik op **OK.** U kunt slechts één type per formulier hebben.

   * **Adobe Campaign: profiel opslaan**: hiermee kunt u een ontvanger maken of bijwerken in Adobe Campaign (standaardwaarde).
   * **Adobe Campaign: abonneren op services**: Hiermee kunt u de abonnementen van een ontvanger in Adobe Campaign beheren.
   * **Adobe Campaign: Abonnement op services opzeggen**: Hiermee kunt u de abonnementen van een ontvanger in Adobe Campaign annuleren.

1. U moet een **Gecodeerde primaire sleutel** op elk formulier. Deze component definieert welke URL-parameter wordt gebruikt om de gecodeerde primaire sleutel van een Adobe Campaign-profiel te accepteren. Selecteer in Componenten de optie Adobe Campaign, zodat alleen de componenten zichtbaar zijn.
1. Sleep de component **Gecodeerde primaire sleutel** naar het formulier (overal) en klik op de knop **Configuratie** pictogram. In de **Adobe Campaign** op, geeft u een naam voor de URL-parameter op. Klik op het vinkje om de wijzigingen op te slaan.

   Gegenereerde koppelingen naar dit formulier moeten deze URL-parameter gebruiken en er de gecodeerde primaire sleutel van een Adobe Campaign-profiel aan toewijzen. De gecodeerde primaire sleutel moet correct (percent) gecodeerd zijn URL.

   ![chlimage_1-47](assets/chlimage_1-47a.png)

1. Voeg zo nodig componenten aan het formulier toe, zoals een tekstveld, een datumveld, een veld Selectievakje, een veld Optie enzovoort. Zie [Adobe Campaign-formuliercomponenten](/help/sites-authoring/adobe-campaign-components.md) voor meer informatie over elke component.
1. Klik het pictogram van de Configuratie om de component te openen. Bijvoorbeeld in **Tekstveld (campagne)** , wijzigt u de titel en de tekst.

   Klikken **Adobe Campaign** om het formulierveld toe te wijzen aan een Adobe Campaign-metagegevensvariabele. Wanneer u het formulier verzendt, wordt het toegewezen veld bijgewerkt in Adobe Campaign. Alleen velden met overeenkomende typen zijn beschikbaar in de variabele kiezer (bijvoorbeeld tekenreeksvariabelen voor tekstvelden).

   ![chlimage_1-48](assets/chlimage_1-48a.png)

   >[!NOTE]
   >
   >U kunt velden die in de tabel met ontvangers worden weergegeven, toevoegen of verwijderen door hier de instructies op te volgen: [https://blogs.adobe.com/experiencedelivers/experience-management/aem-campaign-integration/](https://blogs.adobe.com/experiencedelivers/experience-management/aem-campaign-integration/)

1. Klikken **Pagina publiceren**. De pagina wordt geactiveerd op uw site. U kunt het bekijken door naar uw AEM publicatieexemplaar te gaan. U kunt [Een formulier testen](#testing-a-form).

   >[!CAUTION]
   >
   >U moet de anonieme gebruiker leesmachtigingen bieden op de cloudservice om formulieren te kunnen gebruiken tijdens het publiceren. Houd er echter rekening mee dat er beveiligingsproblemen kunnen optreden als u leesmachtigingen verschaft aan de anonieme gebruiker en zorg ervoor dat u dit beperkt door bijvoorbeeld de dispatcher te configureren.

## Een formulier testen {#testing-a-form}

Nadat u een formulier hebt gemaakt en formulierinhoud hebt bewerkt, wilt u mogelijk handmatig testen of het formulier naar behoren werkt.

>[!NOTE]
>
>U moet een **Primaire sleutel in afbeelding** op elk formulier. Selecteer in Componenten de optie Adobe Campaign, zodat alleen de componenten zichtbaar zijn.
>
>Hoewel u in deze procedure het epknummer handmatig invoert, krijgen gebruikers in de praktijk een koppeling naar deze pagina (om uw abonnement op te zeggen, in te schrijven of uw profiel bij te werken) binnen een nieuwsbrief. De epk wordt op basis van de gebruiker automatisch bijgewerkt.
>
>Als u die koppeling wilt maken, gebruikt u de variabele **Hoofdresource-id**(Adobe Campaign Standard) of **Gecodeerde id** (Adobe Campaign Classic) (bijvoorbeeld in **Tekst en persoonlijke voorkeur (campagne)** ), die een koppeling vormt naar het epk in Adobe Campaign.

Hiervoor moet u handmatig de EPK van een Adobe Campaign-profiel ophalen en dit vervolgens toevoegen aan de URL:

1. De gecodeerde primaire sleutel (EPK) van een Adobe Campaign-profiel ophalen:

   * In Adobe Campaign Standard - navigeer naar **Profielen en publiek** > **Profielen**, waarin de bestaande profielen worden vermeld. Zorg ervoor dat de tabel de **Hoofd Resource Identifier** veld in een kolom (dit kan worden geconfigureerd door te klikken/tikken **Lijst configureren**). Kopieer de belangrijkste resource-id van het gewenste profiel.
   * Ga in Adobe Campaign Classic naar **Profielen en doelen** >  **Ontvangers**, waarin de bestaande profielen worden vermeld. Zorg ervoor dat de tabel de **Gecodeerde id** veld in een kolom (dit kan worden geconfigureerd door met de rechtermuisknop op een item te klikken en **Lijst configureren...**). Kopieer de gecodeerde id van het gewenste profiel.

1. Open AEM de formulierpagina op het publicatieexemplaar en voeg de EPK vanuit stap 1 toe als een URL-parameter: gebruik dezelfde naam die u eerder in de EPK-component hebt gedefinieerd bij het ontwerpen van het formulier (bijvoorbeeld: `?epk=...`)
1. Het formulier kan nu worden gebruikt om de gegevens en abonnementen voor het gekoppelde Adobe Campaign-profiel te wijzigen. Nadat u een aantal velden hebt gewijzigd en het formulier hebt verzonden, kunt u in Adobe Campaign controleren of de desbetreffende gegevens zijn bijgewerkt.

De gegevens in de Adobe Campaign-database worden bijgewerkt nadat een formulier is gevalideerd.
