---
title: Aangepaste formulieren en recorddocumenten lokaliseren met AEM vertaalworkflow
seo-title: Using AEM translation workflow to localize adaptive forms and document of record
description: Leer AEM vertaalworkflows gebruiken om adaptieve formulieren en recorddocumenten te lokaliseren.
seo-description: Learn to use AEM translation workflows to localize adaptive forms and document of record.
uuid: 6c87a283-0203-4cf7-989a-3770ddbbbd6e
content-type: reference
topic-tags: develop
discoiquuid: f5642571-9657-4ca1-93c5-4ae2eb91e967
noindex: true
feature: Adaptive Forms
exl-id: ebec03a3-67a0-4ecd-84bb-8580388e048a
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '753'
ht-degree: 0%

---

# Aangepaste formulieren en recorddocumenten lokaliseren met AEM vertaalworkflow {#using-aem-translation-workflow-to-localize-adaptive-forms-and-document-of-record}

Met gelokaliseerde formulieren hebt u een groter publiek in verschillende regio&#39;s. Met de vertaalworkflow van Adobe Experience Manager kunt u adaptieve formulieren en de bijbehorende documenten lokaliseren. U kunt **machinevertaling** of **menselijke vertalers** om een adaptief formulier te lokaliseren.

In dit artikel wordt uitgelegd hoe u AEM vertaalworkflow kunt gebruiken met adaptieve formulieren en opnamedocumenten.

## Een adaptief formulier en document van records lokaliseren met behulp van automatische vertaling {#localizing-an-adaptive-form-and-document-of-record-using-machine-translation}

De vertaalservice zet uw inhoud direct om in adaptieve vorm en in een document met opnamen. AEM Forms is vooraf geconfigureerd voor het gebruik van een proefversie van Microsoft Translator voor computervertaling. Voer de volgende stappen uit om automatische vertaling in te schakelen voor uw adaptieve formulieren en document of record:

1. Selecteer een formulier in de gebruikersinterface van AEM Forms en tik op **Woordenboek toevoegen** optie.
1. In **Woordenboek toevoegen aan vertaalproject** scherm, selecteert u de **Een nieuw vertaalproject maken** of **Toevoegen aan een bestaand vertaalproject** optie.
1. In de **Projecttitel** -veld, geeft u de titel op. Bijvoorbeeld, `Government Reference Site - German locale.`
1. In de **Doeltalen** veld, geef een landinstelling op (bijvoorbeeld `German(de)`) en klik op **Gereed**. U kunt meerdere landinstellingen opgeven. Het formulier wordt vertaald naar alle landinstellingen die zijn opgegeven in het dialoogvenster **Doeltalen** veld.
1. Klik in het dialoogvenster Woordenboek toegevoegd op **Projecten openen**. Open het nieuwe project in het scherm Projecten.
1. Klik op de knop **ovalen** onder aan het dialoogvenster **Omzettingsoverzicht** tegel. Het scherm Translation Summary wordt geopend.
1. Klik op de knop **Bewerken** pictogram boven aan **Omzettingsoverzicht** scherm. Open de **Vertaling** en selecteert u Machine Translation in het dialoogvenster **Omzettingsmethode** scherm. Selecteer de juiste **Vertaalbureau** en **Cloud Configuration**. Klik op de knop **Gereed** aan de bovenkant van het scherm.
1. Op de **Vertaaltaak** tegel, klik op de knop ![aem62forms_downarrow](assets/aem62forms_downarrow.png) en klik op **Start**. De status van de tegel verandert in Concept. Wanneer de vertaling is voltooid, verandert de status in **Gereed voor revisie**. Vernieuw de pagina na een paar minuten en controleer de status.
1. Nadat de status is gewijzigd in **Gereed voor revisie** op de **Vertaaltaak** Open het formulier in een browservenster. Er wordt een gelokaliseerde versie van het formulier weergegeven.

   >[!NOTE]
   >
   >* Voordat u de gelokaliseerde versie van het formulier opent in het browservenster, moet u controleren of de landinstelling van de browser is ingesteld op de landinstelling van het formulier. Als het formulier bijvoorbeeld wordt vertaald naar het Duits (de), stelt u de landinstelling van de browser in op het Duits (de).
   >* Adaptieve formuliercomponenten bieden geen ondersteuning voor RTL-talen (van rechts naar links). Bijvoorbeeld Hebreeuws.


   Het automatisch gegenereerde recorddocument wordt samen met het adaptieve formulier ook gelokaliseerd.

   Zie voor meer informatie over de instellingen en configuratie van Document of Record:

[Document met recordsjabloonconfiguratie](/help/forms/using/generate-document-of-record-for-non-xfa-based-adaptive-forms.md#p-document-of-record-template-configuration-p)

[Document met recordinstellingen](/help/forms/using/generate-document-of-record-for-non-xfa-based-adaptive-forms.md#p-document-of-record-settings-p)

1. [De brandinggegevens van het recorddocument aanpassen](/help/forms/using/generate-document-of-record-for-non-xfa-based-adaptive-forms.md) en zorg ervoor dat de landinstelling van de browser wordt ingesteld op de taal waarin u het Adaptief formulier hebt gelokaliseerd met de computertaal. Met de landinstelling van de browser kunt u de brandinggegevens in het recorddocument lokaliseren.
1. Tik op Voorvertoning genereren om het gelokaliseerde document met records te bekijken. Het document met record PDF wordt gegenereerd en geopend op een nieuw tabblad in uw browser.

## Een adaptief formulier en het bijbehorende document lokaliseren met behulp van menselijke vertaling {#localizing-an-adaptive-form-and-its-document-of-record-using-human-translation}

In menselijke vertaling wordt de inhoud naar een vertaalbureau gestuurd en vertaald door professionele vertalers. Wanneer de vertaalde inhoud is voltooid, wordt deze geretourneerd en in AEM geïmporteerd. Wanneer uw vertaalbureau is geïntegreerd met AEM, wordt de inhoud automatisch verzonden tussen AEM en de vertaalprovider.

Voor vertaling wordt een woordenboek met bestanden in XLIFF-indeling gedeeld met de professionele vertalers. Het woordenboek bevat een apart XLIFF-bestand voor elke landinstelling. Elk XLIFF-bestand bevat tekst die aan de eindgebruikers en plaatsaanduidingen voor de bijbehorende gelokaliseerde tekst wordt weergegeven.

Voer de volgende stappen uit om een formulier en het bijbehorende document te lokaliseren met behulp van Human Translators:

1. [AEM met uw vertaalserviceprovider verbinden](/help/sites-administering/tc-tic.md) en [configuraties voor vertaalintegratie maken](/help/sites-administering/tc-tic.md).

1. [Pagina&#39;s van uw master taal koppelen](/help/sites-administering/tc-tic.md) met de vertaalservice en frameworkconfiguraties.

1. [Het type inhoud identificeren](/help/sites-administering/tc-rules.md) om te vertalen.

1. [De inhoud voorbereiden voor vertaling](/help/sites-administering/tc-prep.md) door de master taal te ontwerpen en de basispagina&#39;s van taalkopieën te maken.

1. [Vertaalprojecten maken](/help/sites-administering/tc-manage.md) de te vertalen inhoud te verzamelen en het vertaalproces voor te bereiden.

1. Gebruik de vertaalprojecten om [het contentvertaalproces beheren](/help/sites-administering/tc-manage.md).

>[!NOTE]
>
>* Adaptieve formuliercomponenten bieden geen ondersteuning voor RTL-talen (van rechts naar links). Bijvoorbeeld Hebreeuws.
>

