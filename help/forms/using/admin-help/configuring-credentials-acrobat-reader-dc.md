---
title: Referenties configureren voor gebruik met Acrobat Reader DC-extensies
seo-title: Referenties configureren voor gebruik met Acrobat Reader DC-extensies
description: Leer hoe u referenties configureert voor gebruik met Acrobat Reader DC-extensies.
seo-description: Leer hoe u referenties configureert voor gebruik met Acrobat Reader DC-extensies.
uuid: 9210e6c9-6f5c-402d-b355-b104cdffd5eb
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_acrobat_reader_dc_extensions
products: SG_EXPERIENCEMANAGER/6.5/FORMS
discoiquuid: 5bb32fb1-4b6e-412f-aa16-f60db9dcaba1
translation-type: tm+mt
source-git-commit: a3c303d4e3a85e1b2e794bec2006c335056309fb

---


# Referenties configureren voor gebruik met Acrobat Reader DC-extensies{#configuring-credentials-for-use-with-acrobat-reader-dc-extensions}

Als u gebruiksrechten wilt toepassen op PDF-documenten, configureert u AEM-formulieren met een geldige referentie voor Acrobat Reader DC-extensies. Tijdens de installatie van AEM-formulieren kan een referentie zijn geconfigureerd. Als u de referentiegegevens voor Acrobat Reader DC-extensies niet hebt geconfigureerd tijdens het uitvoeren van Configuration Manager of als u een nieuwe of vervangende referentie moet importeren, kunt u dit doen met de pagina&#39;s Betrouwbaarheidsopslagbeheer.

Als u een evaluatiereferentie gebruikt, vervang het met een productieleferentie wanneer het bewegen aan uw productiemilieu. Als u een verlopen referentie of evaluatiereferentie wilt bijwerken, verwijdert u eerst de oude referentie voor Acrobat Reader DC-extensies.

Voor informatie over het verkrijgen van een referentie, zie het [Voorbereiden van het installeren van AEM- vormen (Één enkele Server)](https://www.adobe.com/go/learn_aemforms_prepareInstallsingle_63).

De Trust Store kan meer dan één referentie voor Acrobat Reader DC-extensies bevatten. U moet een van deze referenties aanwijzen als de standaardreferentie voor Reader Extensions. De standaardreferentie wordt gebruikt wanneer een Workbench-gebruiker niet kan bepalen welke referentie moet worden gebruikt tijdens het maken van processen. Deze regels zijn van toepassing op standaardreferenties:

* Als u een referentie voor Acrobat Reader DC-extensies importeert en het vertrouwensarchief geen andere referenties voor Acrobat Reader DC-extensies bevat, wordt dit als de standaardinstelling ingesteld.
* Als u een referentie voor Acrobat Reader DC-extensies importeert terwijl de optie Standaard is geselecteerd, wordt het standaardtype verwijderd uit een bestaande standaardreferentie. De geïmporteerde referentie wordt de standaardinstelling.
* U kunt een standaardreferentie voor Acrobat Reader DC-extensies niet verwijderen. Als u de standaardreferentie wilt verwijderen, stelt u eerst een andere referentie in als de standaardreferentie. Een uitzondering op deze regel is dat als er slechts één referentie is, u het kunt schrappen alhoewel het het gebrek is.
* U kunt een standaardreferentie voor Acrobat Reader DC-extensies niet bijwerken.

>[!NOTE]
>
>U kunt geloofsbrieven ook invoeren en schrappen programmatically. (Zie [Programmeren met AEM-formulieren](https://www.adobe.com/go/learn_aemforms_programming_63).)

## Een referentie voor Acrobat Reader DC-extensies importeren {#import-a-acrobat-reader-dc-extensions-credential}

1. Klik in de beheerconsole op Instellingen > Betrouwbaarheidsopslagbeheer > Lokale referenties.
1. Klik op Importeren en selecteer Acrobat Reader DC extensions Credential onder Type vertrouwde opslag.
1. (Optioneel) Selecteer Standaard om aan te geven dat deze referentie de standaardreferentie is voor gebruik met Acrobat Reader DC-extensies.
1. Typ in het vak Alias een id voor de referentie. Deze id wordt gebruikt als de weergavenaam voor de referentie in Acrobat Reader DC-extensies. Deze alias wordt ook gebruikt om toegang te krijgen tot de referentie via programmacode met de AEM-formulieren SDK.

   >[!NOTE]
   >
   >De naam van de alias wordt automatisch omgezet in hoofdletters voor weergavedoeleinden. De naam van de alias is niet hoofdlettergevoelig wanneer u er in een proces naar verwijst.

1. Klik op Bestand kiezen om de referentie te zoeken, typ het wachtwoord van de referentie en klik op OK.

   Als het foutbericht &quot;Kan referentie niet importeren vanwege een onjuiste bestandsindeling of een onjuist wachtwoord&quot; wordt weergegeven, controleert u of het wachtwoord geldig is.

## Een referentie voor Acrobat Reader DC-extensies verwijderen {#remove-a-acrobat-reader-dc-extensions-credential}

1. Klik in de beheerconsole op Instellingen > Betrouwbaarheidsopslagbeheer > Lokale referenties.
1. Selecteer de referentie en klik op Verwijderen.

## Referentie voor Acrobat Reader DC-extensies vervangen {#replace-a-acrobat-reader-dc-extensions-credential}

1. Klik in de beheerconsole op Instellingen > Betrouwbaarheidsopslagbeheer > Lokale referenties.
1. Noteer de alias van de bestaande referentie, selecteer deze en klik op Verwijderen.
1. Importeer de nieuwe referentie met exact dezelfde aliasnaam.

