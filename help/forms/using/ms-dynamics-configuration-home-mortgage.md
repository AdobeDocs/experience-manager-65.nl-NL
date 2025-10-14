---
title: Configureer Microsoft Dynamics 365 voor de workflow voor hypothecair thuis van de website Web.Finance
description: Leer hoe u Microsoft&amp gebruikt;reg; Dynamics 365 services via adaptieve formulieren voor de hypotheekworkflow op de website Web.Finance Reference.
products: SG_EXPERIENCEMANAGER/6.3/FORMS
topic-tags: develop, Configuration
exl-id: 2ac37dc5-d88d-4f98-8576-cd2ca6f0ea3a
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms,Foundation Components
role: Admin, User, Developer
source-git-commit: d7b9e947503df58435b3fee85a92d51fae8c1d2d
workflow-type: tm+mt
source-wordcount: '410'
ht-degree: 0%

---

# Configureer Microsoft Dynamics 365 voor de workflow voor hypothecair thuis van de website Web.Finance {#configure-microsoft-dynamics-for-the-home-mortgage-workflow-of-the-we-finance-reference-site}

Leer hoe u de Microsoft® Dynamics 365-services kunt gebruiken via adaptieve formulieren voor de hypotheekworkflow op de website Web.Finance

## Overzicht {#overview}

Microsoft® Dynamics 365 is een ERP-software (Customer Relationship Management) en een ERP-software (Customer Relationship Management) die bedrijfsoplossingen biedt voor het maken en beheren van klantaccounts, contactpersonen, leads, mogelijkheden en gevallen.

AEM Forms verleent de wolkendienst om Dynamiek 365 met [&#x200B; de module van de Integratie van Gegevens van Forms &#x200B;](/help/forms/using/data-integration.md) te integreren. Alvorens u de de toepassingsanalyse van de Kortere pas van het Huis met het scenario van de Dynamiek Microsoft® kunt gebruiken, moet u de Dynamica 365 vormen Microsoft® die met de Web.Finance verwijzingsplaats moet worden gebruikt.

## Vereisten {#prerequisites}

Alvorens u begint opstelling en Dynamica 365 te vormen, zorg ervoor dat u hebt:

* AEM 6.3 Forms Service Pack 1 en hoger
* Microsoft® Dynamics 365 account
* Registered application for Dynamics 365 service with Microsoft® Azure Active Directory
* Client-id en clientgeheim voor de geregistreerde toepassing

## Koppel de hypotheekcalculator voor woninghypotheken aan de homepage van uw site {#link-the-home-mortgage-calculator-with-your-site-home-page}

1. Ga in de auteurinstantie naar de volgende pagina:

   `https://[server]:[port]/editor.html/content/we-finance/global/en/loan-landing-page.html`

1. Schuif omlaag naar de rekenmachine voor de beginmeter.
1. Markeer het deelvenster van de rechterkolom (rekenmachine) en selecteer dit om het pop-upmenu weer te geven. Selecteer Configureren in het pop-upmenu. Het dialoogvenster AEM Forms-container bewerken wordt geopend.

   ![&#x200B; calculatorconfigpanel &#x200B;](assets/calculatorconfigurepanel.png)

1. In de Edit dialoog van de Container van AEM Forms, doorblader de activa weg en selecteer huis-hypotheek-calculator bij de volgende weg en selecteer **bevestigen**:

   formsanddocuments/We.Finance/MS Dynamics/

   ![&#x200B; selectassetpath &#x200B;](assets/selectassetpath.png)

1. Selecteer **Gereed**.
1. Publish de bewerkte pagina.

   >[!NOTE]
   >
   >De band van de calculatorgebieden met FDM wordt preconfigured door het Wij.Finance pakket van de verwijzingsplaats. Als u de binding wilt weergeven, opent u het formulier in de ontwerpmodus en ziet u het veld binden verwijzingen.

1. Als u een aangepaste entiteit wilt maken voor het opslaan van de aanvraagrecord voor hypotheektoepassing op woningen, importeert u het pakket AEMFormsFSIRefsite_1_0.zip-oplossing naar uw Microsoft® Dynamics-instantie:

   1. Download het pakket van:

      `https://'[server]:[port]'/content/aemforms-refsite-collaterals/we-finance/home-mortgage/ms-dynamics/AEMFormsFSIRefsite_1_0.zip`

   1. Importeer het oplossingspakket naar de Microsoft® Dynamics-instantie. In uw instantie van de Dynamiek Microsoft®, ga **Montages** > **Oplossingen** en selecteer dan **Invoer**.

1. Als u de contactgegevens van de gebruiker wilt instellen die worden gebruikt in de terugzetsite, importeert u het pakket Sarah Rose Contact.CSV naar de instantie Microsoft® Dynamics:

   1. Download het pakket van:

      `https://'[server]:[port]'/content/aemforms-refsite-collaterals/we-finance/home-mortgage/ms-dynamics/Sarah%20Rose%20Contact.csv`

   1. Importeer het pakket naar de Microsoft® Dynamics-instantie. In uw instantie van de Dynamiek Microsoft®, ga **van de Verkoop** > **Contacten** en selecteer dan de Gegevens van de Invoer **.**
