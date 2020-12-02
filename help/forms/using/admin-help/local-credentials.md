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
workflow-type: tm+mt
source-wordcount: '510'
ht-degree: 0%

---


# Lokale referenties beheren {#managing-local-credentials}

Lokale referenties zijn persoonlijke sleutelgegevens die worden gehost in Betrouwbaarheidsbeheer. Een *lokale referentie* identificeert waar de DES van een gebruiker referentie wordt opgeslagen. Met Betrouwbaarheidsbeheer kunt u uw lokale gegevens importeren en beheren door bijvoorbeeld bestaande PFX-bestanden te gebruiken, zodat u lokale gegevens kunt importeren, bewerken en verwijderen.

AEM formulieren ondersteunen RSA- en DSA-referenties van maximaal 4096 bits in de standaard PKCS12-indeling (.pfx- en .p12-bestanden).

U kunt elk gewenst aantal referenties importeren en exporteren. Als u een verlopen referentie wilt vervangen met dezelfde alias, verwijdert u de referentie en importeert u de nieuwe referentie met dezelfde alias.

Zie [Referenties configureren voor gebruik met Acrobat Reader DC-extensies](/help/forms/using/admin-help/configuring-credentials-acrobat-reader-dc.md#configuring-credentials-for-use-with-acrobat-reader-dc-extensions) voor informatie en instructies met betrekking tot Acrobat Reader DC-extensies.

## Een referentie {#import-a-credential} importeren

1. Klik in de beheerconsole op Instellingen > Betrouwbaarheidsopslagbeheer > Lokale referenties.
1. Klik op Importeren. Selecteer onder Type vertrouwde winkel een van de volgende opties:

   * **Document Signing Credential:** Een referentie die wordt gebruikt voor het uitgeven van een digitale handtekening op een document.
   * **Acrobat Reader DC extensions Credential:** Een digitaal certificaat dat specifiek is voor Acrobat Reader DC-extensies en waarmee Adobe Reader-gebruiksrechten kunnen worden geactiveerd in de geproduceerde PDF-documenten.
   * **Standaard:** geeft aan dat dit de standaardreferentie is voor gebruik met Acrobat Reader DC-extensies.

   Zie [Voorbereiden op installatie van AEM formulieren](https://www.adobe.com/go/learn_aemforms_prepareInstallsingle_63) voor informatie over het verkrijgen van referentie.

1. Typ in het vak Alias een id voor de referentie. Deze id wordt gebruikt als de weergavenaam voor de referentie in Acrobat Reader DC-extensies en de service Handtekening. Deze alias wordt ook gebruikt om de referentie via programmacode te benaderen met de SDK voor AEM formulieren.

   >[!NOTE]
   >
   >De naam van de alias wordt automatisch omgezet in hoofdletters voor weergavedoeleinden. De naam van de alias is niet hoofdlettergevoelig wanneer u er in een proces naar verwijst.

1. Klik op Bladeren om de referentie te zoeken, typ het wachtwoord van de referentie en klik op OK.

   Als het foutbericht &quot;Kan referentie niet importeren vanwege een onjuiste bestandsindeling of een onjuist wachtwoord&quot; wordt weergegeven, controleert u of het wachtwoord geldig is.

## Een referentie {#export-a-credential} exporteren

Referenties worden geëxporteerd als P12-bestanden in de PKCS#12-indeling.

1. Klik in de beheerconsole op Instellingen > Betrouwbaarheidsopslagbeheer > Lokale referenties.
1. Klik op de naam van de alias van de referentie die u wilt exporteren en klik vervolgens op Exporteren.
1. Typ het wachtwoord in het vak Wachtwoord. Dit wachtwoord is nieuw en wordt gebruikt om de geëxporteerde referentie te coderen.
1. Klik op Exporteren, volg de aanwijzingen om de referentie te exporteren en klik op OK.

## Alias of vertrouwenswinkeltype van referenties bewerken {#edit-a-credential-s-alias-or-trust-store-type}

Nadat een referentie is geïmporteerd, kunt u de naam van de alias en het type vertrouwde opslagruimte bewerken.

1. Klik in de beheerconsole op Instellingen > Betrouwbaarheidsopslagbeheer > Lokale referenties.
1. Klik op de naam van de alias van de referentie die u wilt bewerken.
1. Klik op Referentie bijwerken.
1. Bewerk de naam van de alias en het type vertrouwde winkel naar wens en klik op OK.

## Een referentie {#delete-a-credential} verwijderen

1. Klik in de beheerconsole op Instellingen > Betrouwbaarheidsopslagbeheer > Lokale referenties.
1. Schakel de selectievakjes in waarin u de gegevens wilt verwijderen.
1. Klik op Verwijderen en vervolgens op OK.

