---
title: Bestaande domeinen bewerken en converteren
description: Leer hoe u de instellingen voor bestaande domeinen wijzigt via de pagina Domeinbeheer. Zet een bestaand ondernemingsdomein in een hybride domein om of omgekeerd.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/setting_up_and_managing_domains
products: SG_EXPERIENCEMANAGER/6.5/FORMS
exl-id: 34ac5f8b-f209-4f99-ad71-4df6f2c88c1e
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
role: User, Developer
source-git-commit: 6a9806d8f40f711a610c130c63d9ab9b2460d075
workflow-type: tm+mt
source-wordcount: '321'
ht-degree: 0%

---

# Bestaande domeinen bewerken en converteren{#editing-and-converting-existing-domains}

>[!NOTE]
> 
> Zorg ervoor dat de gebruiker beheerdersrechten heeft om toegang te krijgen tot de beheerdersconsole.

U kunt de montages voor bestaande domeinen van de pagina van het Beheer van het Domein veranderen. U kunt een bestaand ondernemingsdomein ook omzetten in een hybride domein.

## Een bestaand domein bewerken {#edit-an-existing-domain}

1. Klik in de beheerconsole op Instellingen > Gebruikersbeheer > Domeinbeheer.
1. Klik op de naam van het domein dat u wilt bewerken.
1. Als u de domeinnaam wilt wijzigen, wijzigt u de tekst in het vak Naam.
1. Om de authentificatieinformatie voor een onderneming of hybride domein te veranderen, klik de aangewezen authentificatienaam bij de bodem van de pagina. Wijzig desgewenst de instellingen op de pagina Verificatie bewerken. (Zie [ montages van de Authentificatie ](/help/forms/using/admin-help/configuring-authentication-providers.md#authentication-settings).)
1. Als u de mapinformatie voor een ondernemingsdomein wilt wijzigen, klikt u op de juiste mapnaam onder aan de pagina. Wijzig desgewenst de instellingen op de pagina Directory bewerken. (Zie [ Toevoegend folders of douaneSPIs ](/help/forms/using/admin-help/configuring-directories.md#adding-directories-or-custom-spis).)
1. Klik op OK als u de wijzigingen hebt aangebracht.

## Een ondernemingsdomein omzetten in een hybride domein {#convert-an-enterprise-domain-to-a-hybrid-domain}

1. Klik in de beheerconsole op Instellingen > Gebruikersbeheer > Domeinbeheer.
1. Klik op de naam van het ondernemingsdomein dat u wilt converteren.
1. Klik op Omzetten in hybride domein.
1. Controleer de informatie die wordt weergegeven met betrekking tot gebruikers- en groepsgegevens en verificatie van gebruikers en klik op OK.
1. Bewerk de instellingen voor het hybride domein en klik op OK.

>[!NOTE]
>
>Als het ondernemingsdomein dat u omzet geen foldermontages bevat, worden om het even welke montages van de authentificatie LDAP verloren.

## Een hybride domein omzetten in een ondernemingsdomein {#convert-a-hybrid-domain-to-an-enterprise-domain}

1. Klik in de beheerconsole op Instellingen > Gebruikersbeheer > Domeinbeheer.
1. Klik op de naam van het hybride domein dat u wilt omzetten.
1. Klik op Omzetten in Enterprise-domein.
1. Controleer de informatie die wordt weergegeven met betrekking tot gebruikers- en groepsgegevens en verificatie van gebruikers en klik op OK.
1. Klik toevoegen Folder en vormen de vereiste folderinformatie. (Zie [ Toevoegend folders of douaneSPIs ](/help/forms/using/admin-help/configuring-directories.md#adding-directories-or-custom-spis).)
