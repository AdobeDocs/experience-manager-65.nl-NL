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
workflow-type: tm+mt
source-wordcount: '576'
ht-degree: 0%

---


# Referenties configureren voor gebruik met Acrobat Reader DC-extensies{#configuring-credentials-for-use-with-acrobat-reader-dc-extensions}

Als u gebruiksrechten wilt toepassen op PDF-documenten, configureert u AEM formulieren met een geldige referentie voor Acrobat Reader DC-extensies. Tijdens de installatie van AEM formulieren kan een referentie zijn geconfigureerd. Als u uw Acrobat Reader DC-extensieverantwoording niet hebt geconfigureerd tijdens het uitvoeren van Configuration Manager of als u een nieuwe of vervangende referentie moet importeren, kunt u dit doen met de pagina&#39;s van het Betrouwbaarheidsbeleid voor winkelbeheer.

Als u een evaluatiereferentie gebruikt, vervang het met een productieleferentie wanneer het bewegen aan uw productiemilieu. Als u een verlopen referentie of evaluatiereferentie wilt bijwerken, verwijdert u eerst de oude Acrobat Reader DC-extensieverwijzing.

Voor informatie over het verkrijgen van een referentie, zie [Voorbereiden om AEM formulieren (Single Server)](https://www.adobe.com/go/learn_aemforms_prepareInstallsingle_63) te installeren.

De Trust Store kan meer dan één referentie voor Acrobat Reader DC-extensies bevatten. U moet één van die geloofsbrieven als referentie van de Uitbreidingen van de standaardReader aanwijzen. De standaardreferentie wordt gebruikt wanneer een Workbench-gebruiker niet kan bepalen welke referentie moet worden gebruikt tijdens het maken van processen. Deze regels zijn van toepassing op standaardreferenties:

* Als u een Acrobat Reader DC-extensiereferentie importeert en de Trust Store geen andere Acrobat Reader DC-extensiegegevens bevat, wordt deze als de standaardinstelling ingesteld.
* Als u een Acrobat Reader DC-extensiereferentie importeert terwijl de optie Standaard is geselecteerd, wordt het standaardtype verwijderd uit een bestaande standaardreferentie. De geïmporteerde referentie wordt de standaardinstelling.
* U kunt een standaard Acrobat Reader DC-extensieverwijzing niet verwijderen. Als u de standaardreferentie wilt verwijderen, stelt u eerst een andere referentie in als de standaardreferentie. Een uitzondering op deze regel is dat als er slechts één referentie is, u het kunt schrappen alhoewel het het gebrek is.
* U kunt een standaard Acrobat Reader DC-extensiereferentie niet bijwerken.

>[!NOTE]
>
>U kunt geloofsbrieven ook invoeren en schrappen programmatically. (Zie [Programmeren met AEM formulieren](https://www.adobe.com/go/learn_aemforms_programming_63).)

## Een Acrobat Reader DC-extensiereferentie {#import-a-acrobat-reader-dc-extensions-credential} importeren

1. Klik in de beheerconsole op Instellingen > Betrouwbaarheidsopslagbeheer > Lokale referenties.
1. Klik op Importeren en selecteer Acrobat Reader DC Extension Credential onder Type vertrouwde winkel.
1. (Optioneel) Selecteer Standaard om aan te geven dat deze referentie de standaardreferentie is voor gebruik met Acrobat Reader DC-extensies.
1. Typ in het vak Alias een id voor de referentie. Deze id wordt gebruikt als de weergavenaam voor de referentie in Acrobat Reader DC-extensies. Deze alias wordt ook gebruikt om de referentie via programmacode te benaderen met de SDK voor AEM formulieren.

   >[!NOTE]
   >
   >De naam van de alias wordt automatisch omgezet in hoofdletters voor weergavedoeleinden. De naam van de alias is niet hoofdlettergevoelig wanneer u er in een proces naar verwijst.

1. Klik op Bestand kiezen om de referentie te zoeken, typ het wachtwoord van de referentie en klik op OK.

   Als het foutbericht &quot;Kan referentie niet importeren vanwege een onjuiste bestandsindeling of een onjuist wachtwoord&quot; wordt weergegeven, controleert u of het wachtwoord geldig is.

## Een Acrobat Reader DC-extensiereferentie verwijderen {#remove-a-acrobat-reader-dc-extensions-credential}

1. Klik in de beheerconsole op Instellingen > Betrouwbaarheidsopslagbeheer > Lokale referenties.
1. Selecteer de referentie en klik op Verwijderen.

## Referentie voor Acrobat Reader DC-extensies vervangen {#replace-a-acrobat-reader-dc-extensions-credential}

1. Klik in de beheerconsole op Instellingen > Betrouwbaarheidsopslagbeheer > Lokale referenties.
1. Noteer de alias van de bestaande referentie, selecteer deze en klik op Verwijderen.
1. Importeer de nieuwe referentie met exact dezelfde aliasnaam.

