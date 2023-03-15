---
title: Acrobat Reader DC-extensies configureren voor het vastleggen van gegevens
seo-title: Configuring Acrobat Reader DC extensions for data capture
description: Leer hoe u Acrobat Reader DC-extensies configureert voor het vastleggen van gegevens.
seo-description: Learn how to configure Acrobat Reader DC extensions for data capture.
uuid: af6b3c72-601e-4f54-8343-a323eeee5906
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_acrobat_reader_dc_extensions
products: SG_EXPERIENCEMANAGER/6.5/FORMS
discoiquuid: 8f8367fe-a8e9-46ee-a980-1633be02932d
exl-id: 0f8e1e46-4fc5-43f6-abb1-19a3f20e1f1d
source-git-commit: 0c7dba43dad8608b4a5de271e1e44942c950fb16
workflow-type: tm+mt
source-wordcount: '320'
ht-degree: 0%

---

# Acrobat Reader DC-extensies configureren voor het vastleggen van gegevens {#configuring-acrobat-reader-dc-extensions-for-data-capture}

Als gebruikers van uw installatie van AEM formulieren de functie voor het vastleggen van gegevens van Content Services (Afgekeurd) gebruiken, wordt u aangeraden een rol te maken met alleen-lezen toegang voor deze gebruikers.

***notitie **: Adobe® LiveCycle® Content Services ES (Afgekeurd) is een contentbeheersysteem dat is geïnstalleerd met LiveCycle. Hiermee kunnen gebruikers processen ontwerpen, beheren, bewaken en optimaliseren die op mensen zijn gericht. De ondersteuning voor Content Services (Afgekeurd) eindigt op 31-12-2014. Zie [Adobe-productlevenscyclusdocument](https://www.adobe.com/support/products/enterprise/eol/eol_matrix.html).*

Voor het vastleggen van gegevens moet u een gebruikersrol toewijzen om toegang te krijgen tot de SampleReaderExtensionsCredential. U kunt de standaardrol van de Beheerder van het Vertrouwen toewijzen, maar ben van mening dat deze rol algemene, niet-administratieve gebruikers de krachtige beheerdervoorrechten geeft die de montages van het Vertrouwen PKI controleren en de Credentials van PKI beheren, die de veiligheid van uw AEM vormeninstallatie in een productiemilieu in gevaar zouden kunnen brengen. Het wordt aanbevolen dat de beheerder van het AEM-formuliersysteem een rol maakt die alleen alleen-lezen toegang biedt tot de Trust Store en deze nieuwe rol toewijst aan niet-beheerders die gegevens vastleggen gebruiken.

## Een rol maken voor gebruikers die gegevens vastleggen {#create-a-role-for-data-capture-users}

1. Klik in de beheerconsole op Instellingen > Gebruikersbeheer > Rolbeheer en klik vervolgens op Nieuwe rol.
1. Voer de rolnaam (bijvoorbeeld Gebruiker van gegevensvastlegging) en beschrijving in de desbetreffende velden in en klik op Volgende.
1. Voor het scherm van de Toestemmingen van de Rol, klik de Toestemmingen van de Vondst, dan uitgezochte Gelezen van de Referentie van de lijst van beschikbare toestemmingen.
1. Klik op OK en vervolgens op Voltooien.

## De rol voor het vastleggen van gegevens toewijzen {#assign-the-data-capture-role}

1. Klik in de beheerconsole op Instellingen > Gebruikersbeheer > Rolbeheer en klik vervolgens op Zoeken.
1. Klik op de gebruikersrol voor het vastleggen van gegevens die u hebt gemaakt.
1. Klik op Gebruikers/groepen zoeken op het tabblad Rolgebruikers/groepen.
1. Klik in het scherm Gebruikers en groepen zoeken op Zoeken, selecteer de gebruikers die de gebruikersrol voor het vastleggen van gegevens nodig hebben en klik op OK.
1. Klik in het scherm Rol bewerken op Opslaan.
