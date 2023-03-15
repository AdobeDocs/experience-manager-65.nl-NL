---
title: Configureer Microsoft Dynamics 365 voor de workflow voor hypothecair thuis van de website Web.Finance
seo-title: Configure Microsoft Dynamics 365 for the home mortgage workflow of the We.Finance reference site
description: Leer hoe u de Microsoft® Dynamics 365-services kunt gebruiken door adaptieve formulieren te maken voor de workflow voor hypotheken thuis op de website Web.Finance Reference
seo-description: Learn how to leverage the Microsoft® Dynamics 365 services through adaptive forms for the home mortgage workflow of the We.Finance Reference site
uuid: a0656d90-84c7-46d1-9a16-dadcc19ff9ef
products: SG_EXPERIENCEMANAGER/6.3/FORMS
topic-tags: develop, Configuration
discoiquuid: 6b31397a-fb06-4043-9368-59fb4fce8afa
exl-id: 2ac37dc5-d88d-4f98-8576-cd2ca6f0ea3a
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '398'
ht-degree: 0%

---

# Configureer Microsoft Dynamics 365 voor de workflow voor hypothecair thuis van de website Web.Finance {#configure-microsoft-dynamics-for-the-home-mortgage-workflow-of-the-we-finance-reference-site}

Leer hoe u de Microsoft® Dynamics 365-services kunt gebruiken door adaptieve formulieren te maken voor de workflow voor hypotheken thuis op de website Web.Finance Reference

## Overzicht {#overview}

Microsoft® Dynamics 365 is een ERP-software (Customer Relationship Management) en een ERP-software (Customer Relationship Management) die bedrijfsoplossingen biedt voor het maken en beheren van klantaccounts, contactpersonen, leads, mogelijkheden en gevallen.

AEM Forms biedt een cloudservice voor de integratie van Dynamics 365 met [Forms-gegevensintegratie](/help/forms/using/data-integration.md) module. Alvorens u de de toepassingsanalyse van de Kortere meetkunde van het Huis met het scenario van de Dynamiek Microsoft® kunt gebruiken, moet u de Dynamica 365 vormen Microsoft® die met de Web.Finance verwijzingsplaats moet worden gebruikt.

## Vereisten {#prerequisites}

Alvorens u begint opstelling en Dynamica 365 te vormen, zorg ervoor dat u hebt:

* AEM 6.3 Forms Service Pack 1 en hoger
* Microsoft® Dynamics 365 account
* Geregistreerde toepassing voor Dynamics 365-service met Microsoft® Azure Active Directory
* Client-id en clientgeheim voor de geregistreerde toepassing

## Koppel de hypotheekcalculator voor woninghypotheken aan de homepage van uw site {#link-the-home-mortgage-calculator-with-your-site-home-page}

1. Ga in de auteurinstantie naar de volgende pagina:

   `https://[server]:[port]/editor.html/content/we-finance/global/en/loan-landing-page.html`

1. Schuif omlaag naar de rekenmachine voor de beginmeter.
1. Markeer het deelvenster van de rechterkolom (rekenmachine) en tik om het pop-upmenu weer te geven. Tik in het pop-upmenu op Configureren. Het dialoogvenster AEM Forms-container bewerken wordt geopend.

   ![calculatorConfigurpanel](assets/calculatorconfigurepanel.png)

1. Blader in het dialoogvenster AEM Forms-container bewerken door het middelenpad en selecteer Home-hypotheekcalculator op het volgende pad en tik **Bevestigen**:

   formsanddocuments/We.Finance/MS Dynamics/

   ![selectassetpath](assets/selectassetpath.png)

1. Tikken **Gereed**.
1. De bewerkte pagina publiceren.

   >[!NOTE]
   >
   >De band van de calculatorgebieden met FDM wordt preconfigured door het Wij.Finance pakket van de verwijzingsplaats. Als u de binding wilt weergeven, opent u het formulier in de ontwerpmodus en ziet u het veld binden verwijzingen.

1. Als u een aangepaste entiteit wilt maken voor het opslaan van de aanvraagrecord voor hypotheektoepassing op woningen, importeert u het pakket AEMFormsFSIRefsite_1_0.zip-oplossing naar uw Microsoft® Dynamics-instantie:

   1. Download het pakket van:

      `https://'[server]:[port]'/content/aemforms-refsite-collaterals/we-finance/home-mortgage/ms-dynamics/AEMFormsFSIRefsite_1_0.zip`

   1. Importeer het oplossingspakket naar de Microsoft® Dynamics-instantie. Ga in je Microsoft® Dynamics-instantie naar **Instellingen** > **Oplossingen** en tik vervolgens op **Importeren**.

1. Als u de contactgegevens van de gebruiker wilt instellen die worden gebruikt in de terugzetsite, importeert u het pakket Sarah Rose Contact.CSV naar de instantie Microsoft® Dynamics:

   1. Download het pakket van:

      `https://'[server]:[port]'/content/aemforms-refsite-collaterals/we-finance/home-mortgage/ms-dynamics/Sarah%20Rose%20Contact.csv`

   1. Importeer het pakket naar de Microsoft® Dynamics-instantie. Ga in je Microsoft® Dynamics-instantie naar **Verkoop** > **Contactpersonen** en tik vervolgens op **Gegevens importeren**.
