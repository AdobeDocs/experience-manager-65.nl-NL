---
title: Vorm de Dynamiek 365 van Microsoft voor het huishypotheekwerkschema van de Web.Finance verwijzingsplaats
seo-title: Vorm de Dynamiek 365 van Microsoft voor het huishypotheekwerkschema van de Web.Finance verwijzingsplaats
description: Leer hoe u de Microsoft® Dynamics 365-services kunt gebruiken door adaptieve formulieren te maken voor de workflow voor hypotheken thuis op de website Web.Finance Reference
seo-description: Leer hoe u de Microsoft® Dynamics 365-services kunt gebruiken door adaptieve formulieren te maken voor de workflow voor hypotheken thuis op de website Web.Finance Reference
uuid: a0656d90-84c7-46d1-9a16-dadcc19ff9ef
products: SG_EXPERIENCEMANAGER/6.3/FORMS
topic-tags: Configuration
discoiquuid: 6b31397a-fb06-4043-9368-59fb4fce8afa
translation-type: tm+mt
source-git-commit: af326f2d2b278fe36df05afc8c172f74c99a064c
workflow-type: tm+mt
source-wordcount: '432'
ht-degree: 0%

---


# Vorm de Dynamiek 365 van Microsoft voor het huishypotheekwerkschema van de Web.Finance verwijzingsplaats {#configure-microsoft-dynamics-for-the-home-mortgage-workflow-of-the-we-finance-reference-site}

Leer hoe u de Microsoft® Dynamics 365-services kunt gebruiken door adaptieve formulieren te maken voor de workflow voor hypotheken thuis op de website Web.Finance Reference

## Overzicht {#overview}

Microsoft® Dynamics 365 is een software van het Beheer van de Verhouding van de Klant (CRM) en van de Planning van het Middel van de Onderneming (ERP) die ondernemingsoplossingen voor het creëren van en het beheren van klantenrekeningen, contacten, lood, kansen, en gevallen verstrekt.

AEM Forms biedt een cloudservice om Dynamics 365 te integreren met de module [Forms Data Integration](/help/forms/using/data-integration.md) . Alvorens u de de toepassingsanalyse van de Kortere meetkunde van het Huis met het scenario van de Dynamiek van Microsoft® kunt gebruiken, moet u de Dynamica 365 vormen Microsoft® die met de Web.Finance verwijzingsplaats moet worden gebruikt.

## Vereisten {#prerequisites}

Alvorens u begint opstelling en Dynamica 365 te vormen, zorg ervoor dat u hebt:

* AEM 6.3 Forms Service Pack 1 en hoger
* Microsoft® Dynamics 365-account
* Geregistreerde toepassing voor Dynamics 365-service met Microsoft® Azure Active Directory
* Client-id en clientgeheim voor de geregistreerde toepassing

## Koppel de hypotheekcalculator voor woninghypotheken aan de homepage van uw site {#link-the-home-mortgage-calculator-with-your-site-home-page}

1. Ga in de auteurinstantie naar de volgende pagina:

   `https://[server]:[port]/editor.html/content/we-finance/global/en/loan-landing-page.html`

1. Schuif omlaag naar de rekenmachine voor de beginmeter.
1. Markeer het deelvenster van de rechterkolom (rekenmachine) en tik om het pop-upmenu weer te geven. Tik in het pop-upmenu op Configureren. Het dialoogvenster AEM Forms-container bewerken wordt geopend.

   ![calculatorConfigurpanel](assets/calculatorconfigurepanel.png)

1. Blader in het dialoogvenster AEM Forms-container bewerken door het middelenpad en selecteer de hypothecaire calculator voor thuisgebruik op het volgende pad en tik op **Bevestigen**:

   formsanddocuments/We.Finance/MS Dynamics/

   ![selectassetpath](assets/selectassetpath.png)

1. Tik **op Gereed**.
1. De bewerkte pagina publiceren.

   >[!NOTE]
   >
   >De band van de calculatorgebieden met FDM wordt preconfigured door het Wij.Finance pakket van de verwijzingsplaats. Als u de binding wilt weergeven, opent u het formulier in de ontwerpmodus en ziet u het veld binden verwijzingen.

1. Als u een aangepaste entiteit wilt maken voor het opslaan van de aanvraagrecord voor hypotheektoepassing op woningen, importeert u het pakket AEMFormsFSIRefsite_1_0.zip-oplossing naar uw Microsoft® Dynamics-instantie:

   1. Download het pakket van:

      `https://'[server]:[port]'/content/aemforms-refsite-collaterals/we-finance/home-mortgage/ms-dynamics/AEMFormsFSIRefsite_1_0.zip`

   1. Importeer het oplossingspakket naar de Microsoft® Dynamics-instantie. Ga in de instantie Microsoft® Dynamics naar **Instellingen** > **Oplossingen** en tik op **Importeren**.

1. Als u de contactgegevens van de gebruiker wilt instellen die worden gebruikt in de terugzetsite, importeert u het pakket Sarah Rose Contact.CSV in uw Microsoft® Dynamics-instantie:

   1. Download het pakket van:

      `https://'[server]:[port]'/content/aemforms-refsite-collaterals/we-finance/home-mortgage/ms-dynamics/Sarah%20Rose%20Contact.csv`

   1. Importeer het pakket naar de instantie Microsoft® Dynamics. Ga in uw Microsoft® Dynamics-instantie naar **Verkoop** > **Contacten** en tik vervolgens op **Gegevens** importeren.

