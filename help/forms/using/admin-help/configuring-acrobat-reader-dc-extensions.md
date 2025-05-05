---
title: Acrobat Reader DC-extensies configureren voor gegevensvastlegging
description: Leer hoe u Acrobat Reader DC Extensions configureert voor het vastleggen van gegevens.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_acrobat_reader_dc_extensions
products: SG_EXPERIENCEMANAGER/6.5/FORMS
exl-id: 0f8e1e46-4fc5-43f6-abb1-19a3f20e1f1d
solution: Experience Manager, Experience Manager Forms
role: User, Developer
feature: Adaptive Forms,Document Services,Reader Extensions
source-git-commit: 6a9806d8f40f711a610c130c63d9ab9b2460d075
workflow-type: tm+mt
source-wordcount: '327'
ht-degree: 0%

---

# Acrobat Reader DC-extensies configureren voor gegevensvastlegging {#configuring-acrobat-reader-dc-extensions-for-data-capture}

>[!NOTE]
> 
> Zorg ervoor dat de gebruiker beheerdersrechten heeft om toegang te krijgen tot de beheerdersconsole.

Als gebruikers van uw installatie van AEM formulieren de functie voor het vastleggen van gegevens van Content Services (Afgekeurd) gebruiken, wordt u aangeraden een rol te maken met alleen-lezen toegang voor deze gebruikers.

***Nota &#x200B;**: Adobe® de Diensten van de Inhoud van de LiveCycle® ES (Vervangen) is een inhoudsbeheersysteem dat met LiveCycle wordt geïnstalleerd. Hiermee kunnen gebruikers processen ontwerpen, beheren, bewaken en optimaliseren die op mensen zijn gericht. De ondersteuning voor Content Services (Afgekeurd) eindigt op 31-12-2014. Zie &lbrace;het document van de de levenscyclus van het product van de Adobe [&#128279;](https://helpx.adobe.com/nl/support/programs/eol-matrix.html).*

Voor het vastleggen van gegevens moet u een gebruikersrol toewijzen om toegang te krijgen tot de SampleReaderExtensionsCredential. U kunt de standaardrol Beheerder van het Vertrouwen toewijzen. Houd er echter rekening mee dat deze rol algemene, niet-beheerdersrechten voor gebruikers geeft die de PKI-instellingen voor vertrouwen beheren en PKI-referenties beheren. Dit kan de beveiliging van de installatie van AEM formulieren in een productieomgeving in gevaar brengen. Het wordt aanbevolen dat de beheerder van het AEM-formuliersysteem een rol maakt die alleen alleen-lezen toegang biedt tot de Trust Store en deze nieuwe rol toewijst aan niet-beheerders die gegevens vastleggen gebruiken.

## Een rol maken voor gebruikers die gegevens vastleggen {#create-a-role-for-data-capture-users}

1. Klik in de beheerconsole op Instellingen > Gebruikersbeheer > Rolbeheer en klik vervolgens op Nieuwe rol.
1. Voer de rolnaam (bijvoorbeeld Gebruiker van gegevensvastlegging) en beschrijving in de desbetreffende velden in en klik op Volgende.
1. Voor het scherm van de Toestemmingen van de Rol, klik de Toestemmingen van de Vondst, dan uitgezochte Gelezen van de Referentie van de lijst van beschikbare toestemmingen.
1. Klik op OK en vervolgens op Voltooien.

## De rol voor het vastleggen van gegevens toewijzen {#assign-the-data-capture-role}

1. Klik in de beheerconsole op Instellingen > Gebruikersbeheer > Rolbeheer en klik vervolgens op Zoeken.
1. Klik op de gebruikersrol voor gegevensvastlegging die u hebt gemaakt.
1. Klik op Gebruikers/groepen zoeken op het tabblad Rolgebruikers/groepen.
1. Klik in het scherm Gebruikers en groepen zoeken op Zoeken, selecteer de gebruikers die de gebruikersrol voor het vastleggen van gegevens nodig hebben en klik op OK.
1. Klik in het scherm Rol bewerken op Opslaan.
