---
title: Lokale referenties beheren
seo-title: Lokale referenties beheren
description: Leer hoe u lokale gegevens beheert.
seo-description: Leer hoe u lokale gegevens beheert.
uuid: 3c4358e0-aaff-4e94-a6b2-04b463fca260
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/managing_certificates_and_credentials
products: SG_EXPERIENCEMANAGER/6.5/FORMS
discoiquuid: 598a9a03-3773-4620-8867-1f754d8ca031
translation-type: tm+mt
source-git-commit: a3c303d4e3a85e1b2e794bec2006c335056309fb

---


# Lokale referenties beheren {#managing-local-credentials}

Lokale referenties zijn persoonlijke sleutelgegevens die worden gehost in Betrouwbaarheidsbeheer. Een *lokale referentie* identificeert waar de DES van een gebruiker referentie wordt opgeslagen. Met Betrouwbaarheidsbeheer kunt u uw lokale gegevens importeren en beheren door bijvoorbeeld bestaande PFX-bestanden te gebruiken, zodat u lokale gegevens kunt importeren, bewerken en verwijderen.

AEM-formulieren ondersteunen RSA- en DSA-referenties van maximaal 4096 bits in de standaard PKCS12-indeling (.pfx- en .p12-bestanden).

U kunt elk gewenst aantal referenties importeren en exporteren. Als u een verlopen referentie wilt vervangen met dezelfde alias, verwijdert u de referentie en importeert u de nieuwe referentie met dezelfde alias.

Zie [Referenties configureren voor gebruik met Acrobat Reader DC-extensies](/help/forms/using/admin-help/configuring-credentials-acrobat-reader-dc.md#configuring-credentials-for-use-with-acrobat-reader-dc-extensions)voor informatie en instructies met betrekking tot Acrobat Reader DC-extensies.

## Een referentie importeren {#import-a-credential}

1. Klik in de beheerconsole op Instellingen > Betrouwbaarheidsopslagbeheer > Lokale referenties.
1. Klik op Importeren. Selecteer onder Type vertrouwde winkel een van de volgende opties:

   * **** Referentie voor documenthandtekening: Een referentie die wordt gebruikt voor het uitgeven van een digitale handtekening op een document.
   * **** Referentie voor Acrobat Reader DC-extensies: Een digitaal certificaat dat specifiek is voor Acrobat Reader DC-extensies waarmee gebruiksrechten van Adobe Reader kunnen worden geactiveerd in de geproduceerde PDF-documenten.
   * **** Standaard: Geeft aan dat dit de standaardreferentie is die wordt gebruikt met Acrobat Reader DC-extensies.
   Zie [Voorbereiden op het installeren van AEM-formulieren](https://www.adobe.com/go/learn_aemforms_prepareInstallsingle_63)voor informatie over het verkrijgen van referenties.

1. Typ in het vak Alias een id voor de referentie. Deze id wordt gebruikt als weergavenaam voor de referentie in Acrobat Reader DC-extensies en de service Handtekening. Deze alias wordt ook gebruikt om toegang te krijgen tot de referentie via programmacode met de AEM-formulieren SDK.

   >[!NOTE]
   >
   >De naam van de alias wordt automatisch omgezet in hoofdletters voor weergavedoeleinden. De naam van de alias is niet hoofdlettergevoelig wanneer u er in een proces naar verwijst.

1. Klik op Bladeren om de referentie te zoeken, typ het wachtwoord van de referentie en klik op OK.

   Als het foutbericht &quot;Kan referentie niet importeren vanwege een onjuiste bestandsindeling of een onjuist wachtwoord&quot; wordt weergegeven, controleert u of het wachtwoord geldig is.

## Een referentie exporteren {#export-a-credential}

Referenties worden geëxporteerd als P12-bestanden in de PKCS#12-indeling.

1. Klik in de beheerconsole op Instellingen > Betrouwbaarheidsopslagbeheer > Lokale referenties.
1. Klik op de naam van de alias van de referentie die u wilt exporteren en klik vervolgens op Exporteren.
1. Typ het wachtwoord in het vak Wachtwoord. Dit wachtwoord is nieuw en wordt gebruikt om de geëxporteerde referentie te coderen.
1. Klik op Exporteren, volg de aanwijzingen om de referentie te exporteren en klik op OK.

## Alias of vertrouwenswinkeltype van een referentie bewerken {#edit-a-credential-s-alias-or-trust-store-type}

Nadat een referentie is geïmporteerd, kunt u de naam van de alias en het type vertrouwde opslagruimte bewerken.

1. Klik in de beheerconsole op Instellingen > Betrouwbaarheidsopslagbeheer > Lokale referenties.
1. Klik op de naam van de alias van de referentie die u wilt bewerken.
1. Klik op Referentie bijwerken.
1. Bewerk de naam van de alias en het type vertrouwde winkel naar wens en klik op OK.

## Een referentie verwijderen {#delete-a-credential}

1. Klik in de beheerconsole op Instellingen > Betrouwbaarheidsopslagbeheer > Lokale referenties.
1. Schakel de selectievakjes in waarin u de gegevens wilt verwijderen.
1. Klik op Verwijderen en vervolgens op OK.

