---
title: Referenties configureren voor gebruik met Acrobat Reader DC Extensions
description: Leer hoe u referenties configureert voor gebruik met Acrobat Reader DC Extensions.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_acrobat_reader_dc_extensions
products: SG_EXPERIENCEMANAGER/6.5/FORMS
exl-id: e8015d59-7587-46dc-a672-e0f1108102ad
solution: Experience Manager, Experience Manager Forms
role: User, Developer
source-git-commit: f6771bd1338a4e27a48c3efd39efe18e57cb98f9
workflow-type: tm+mt
source-wordcount: '546'
ht-degree: 0%

---

# Referenties configureren voor gebruik met Acrobat Reader DC Extensions{#configuring-credentials-for-use-with-acrobat-reader-dc-extensions}

Als u gebruiksrechten wilt toepassen op PDF-documenten, configureert u AEM formulieren met een geldige referentie voor Acrobat Reader DC Extensions. Tijdens de installatie van AEM formulieren kan een referentie zijn geconfigureerd. Als u de Acrobat Reader DC Extensions-referentie niet hebt geconfigureerd tijdens het uitvoeren van Configuration Manager of als u een nieuwe of vervangende referentie moet importeren, kunt u dit doen met de pagina&#39;s van het Betrouwbaarheidsbeleid.

Als u een evaluatiereferentie gebruikt, vervang het met een productieleferentie wanneer het bewegen aan uw productiemilieu. Als u een verlopen of evaluatiereferentie wilt bijwerken, verwijdert u eerst de oude Acrobat Reader DC Extensions-referentie.

Voor informatie over het verkrijgen van een referentie raadpleegt u [Installatie van AEM formulieren voorbereiden (één server)](https://helpx.adobe.com/pdf/aem-forms/6-3/prepare-install-single-server.pdf).

De Trust Store kan meer dan één Acrobat Reader DC Extensions-referentie bevatten. Wijs één van die geloofsbrieven als referentie van de Uitbreidingen van de standaardReader aan. De standaardreferentie wordt gebruikt wanneer een Workbench-gebruiker niet kan bepalen welke referentie moet worden gebruikt tijdens het maken van processen. Deze regels zijn van toepassing op standaardreferenties:

* Als u een Acrobat Reader DC Extensions-referentie importeert en de Trust Store bevat geen andere Acrobat Reader DC Extensions-referenties, wordt deze ingesteld als de standaardinstelling.
* Als u een Acrobat Reader DC Extensions-referentie importeert terwijl de optie Standaard is geselecteerd, wordt het standaardtype verwijderd uit een bestaande standaardreferentie. De geïmporteerde referentie wordt de standaardinstelling.
* U kunt geen standaard Acrobat Reader DC Extensions-referentie verwijderen. Om de standaardreferentie te schrappen, plaats eerst een andere referentie als gebrek. Een uitzondering op deze regel is dat als er slechts één referentie is, u het kunt schrappen alhoewel het het gebrek is.
* U kunt een standaard Acrobat Reader DC Extensions-referentie niet bijwerken.

>[!NOTE]
>
>U kunt geloofsbrieven ook invoeren en schrappen programmatically. (Zie [Programmeren met AEM formulieren](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/previous-updates/aem-previous-versions.html).)

## Een Acrobat Reader DC Extensions-referentie importeren {#import-a-acrobat-reader-dc-extensions-credential}

1. Klik in de beheerconsole op Instellingen > Betrouwbaarheidsopslagbeheer > Lokale referenties.
1. Klik op Importeren en selecteer Acrobat Reader DC Extensions Credential onder Type vertrouwde winkel.
1. (Optioneel) Selecteer Standaard om aan te geven dat deze referentie de standaardreferentie is voor gebruik met Acrobat Reader DC Extensions.
1. Typ in het vak Alias een id voor de referentie. Deze id wordt gebruikt als de weergavenaam voor de referentie in Acrobat Reader DC Extensions. Deze alias wordt ook gebruikt om de referentie via programmacode te benaderen met de SDK voor AEM formulieren.

   >[!NOTE]
   >
   >De naam van de alias wordt automatisch omgezet in hoofdletters voor weergavedoeleinden. De naam van de alias is niet hoofdlettergevoelig wanneer u er in een proces naar verwijst.

1. Klik op Bestand kiezen om de referentie te zoeken, typ het wachtwoord van de referentie en klik op OK.

   Als het foutbericht &quot;Kan referentie niet importeren vanwege een onjuiste bestandsindeling of een onjuist wachtwoord&quot; wordt weergegeven, controleert u of het wachtwoord geldig is.

## Een Acrobat Reader DC Extensions-referentie verwijderen {#remove-a-acrobat-reader-dc-extensions-credential}

1. Klik in de beheerconsole op Instellingen > Betrouwbaarheidsopslagbeheer > Lokale referenties.
1. Selecteer de referentie en klik op Verwijderen.

## Een Acrobat Reader DC Extensions-referentie vervangen {#replace-a-acrobat-reader-dc-extensions-credential}

1. Klik in de beheerconsole op Instellingen > Betrouwbaarheidsopslagbeheer > Lokale referenties.
1. Noteer de alias van de bestaande referentie, selecteer deze en klik op Verwijderen.
1. Importeer de nieuwe referentie met exact dezelfde aliasnaam.
