---
title: De AEM-vertaalworkflow gebruiken om adaptieve formulieren en recorddocumenten te lokaliseren
seo-title: De AEM-vertaalworkflow gebruiken om adaptieve formulieren en recorddocumenten te lokaliseren
description: Leer hoe u met AEM-vertaalworkflows adaptieve formulieren en recorddocumenten kunt lokaliseren.
seo-description: Leer hoe u met AEM-vertaalworkflows adaptieve formulieren en recorddocumenten kunt lokaliseren.
uuid: 6c87a283-0203-4cf7-989a-3770ddbbbd6e
content-type: reference
topic-tags: develop
discoiquuid: f5642571-9657-4ca1-93c5-4ae2eb91e967
noindex: true
translation-type: tm+mt
source-git-commit: 5120bbdefea528ad6d07a9c99df565555b6a8444

---


# De AEM-vertaalworkflow gebruiken om adaptieve formulieren en recorddocumenten te lokaliseren {#using-aem-translation-workflow-to-localize-adaptive-forms-and-document-of-record}

Met gelokaliseerde formulieren hebt u een groter publiek in verschillende regio&#39;s. Met de vertaalworkflow van Adobe Experience Manager kunt u adaptieve formulieren en de bijbehorende documenten van records lokaliseren. U kunt **machinevertaling** of **menselijke vertalers** gebruiken om een adaptief formulier te lokaliseren.

In dit artikel wordt uitgelegd hoe u de AEM-vertaalworkflow kunt gebruiken met adaptieve formulieren en documenten.

## Een adaptief formulier en document van records lokaliseren met behulp van automatische vertaling {#localizing-an-adaptive-form-and-document-of-record-using-machine-translation}

De vertaalservice zet uw inhoud direct om in adaptieve vorm en in een document met opnamen. AEM Forms is vooraf geconfigureerd voor het gebruik van een proefversie van Microsoft Translator voor machinevertaling. Voer de volgende stappen uit om automatische vertaling in te schakelen voor uw adaptieve formulieren en document of record:

1. Selecteer een formulier in de interface voor AEM-formulieren en tik op de optie Woordenboek **** toevoegen.
1. Selecteer in het scherm Woordenboek **toevoegen aan vertaalproject** de optie **Een nieuw vertaalproject** maken of **Toevoegen aan een bestaand vertaalproject** .
1. Geef in het veld **Projecttitel** de titel op. Bijvoorbeeld, `Government Reference Site - German locale.`
1. Geef in het veld **Doeltalen** een landinstelling op (bijvoorbeeld `German(de)`) en klik op **Gereed**. U kunt meerdere landinstellingen opgeven. Het formulier wordt vertaald naar alle landinstellingen die zijn opgegeven in het veld **Doeltalen** .
1. Klik in het dialoogvenster Woordenboek toegevoegd op Projecten **** openen. Open het nieuwe project in het scherm Projecten.
1. Klik op de **ovalen** onder aan de tegel **Vertaaloverzicht** . Het scherm Translation Summary wordt geopend.
1. Klik op het pictogram **Bewerken** boven aan het scherm **Vertaaloverzicht** . Open het tabblad **Vertaling** en selecteer Machine Translation in het scherm **Translation Method** . Selecteer de juiste **vertaalprovider** en **Cloud Configuration**. Klik op het pictogram **Gereed** boven in het scherm.
1. Klik op het pictogram **Aem62forms_downarrow** in het onderdeel Taak ![omzetten en klik op](assets/aem62forms_downarrow.png) Start ****. De status van de tegel verandert in Concept. Nadat de vertaling is voltooid, verandert de status in **Gereed voor revisie**. Vernieuw de pagina na een paar minuten en controleer de status.
1. Nadat de status is gewijzigd in **Gereed voor revisie** op het onderdeel **Vertaaltaak** , opent u het formulier in een browservenster. Er wordt een gelokaliseerde versie van het formulier weergegeven.

   >[!NOTE]
   >
   >* Voordat u de gelokaliseerde versie van het formulier opent in het browservenster, moet u controleren of de landinstelling van de browser is ingesteld op de landinstelling van het formulier. Als het formulier bijvoorbeeld wordt vertaald naar het Duits (de), stelt u de landinstelling van de browser in op het Duits (de).
   >* Adaptieve formuliercomponenten bieden geen ondersteuning voor RTL-talen (van rechts naar links). Bijvoorbeeld Hebreeuws.


   Het automatisch gegenereerde recorddocument wordt samen met het adaptieve formulier ook gelokaliseerd.

   Zie voor meer informatie over de instellingen en configuratie van Document of Record:

   [Document met recordsjabloonconfiguratie](/help/forms/using/generate-document-of-record-for-non-xfa-based-adaptive-forms.md#p-document-of-record-template-configuration-p)

   [Document met recordinstellingen](/help/forms/using/generate-document-of-record-for-non-xfa-based-adaptive-forms.md#p-document-of-record-settings-p)

1. [Pas de brandinggegevens van het recorddocument](/help/forms/using/generate-document-of-record-for-non-xfa-based-adaptive-forms.md) aan en controleer of de landinstelling van de browser is ingesteld op de taal waarin u het adaptieve formulier hebt gelokaliseerd met behulp van de computertaal. Met de landinstelling van de browser kunt u de brandinggegevens in het recorddocument lokaliseren.
1. Tik op Voorvertoning genereren om het gelokaliseerde document met records te bekijken. Het document met de record-PDF wordt gegenereerd en geopend op een nieuw tabblad in uw browser.

## Een adaptief formulier en het bijbehorende document lokaliseren met behulp van menselijke vertaling {#localizing-an-adaptive-form-and-its-document-of-record-using-human-translation}

In menselijke vertaling wordt de inhoud naar een vertaalbureau gestuurd en vertaald door professionele vertalers. Wanneer de vertaalde inhoud is voltooid, wordt deze geretourneerd en in AEM geïmporteerd. Wanneer uw vertaalbureau is geïntegreerd met AEM, wordt inhoud automatisch verzonden tussen AEM en de vertaalprovider.

Voor vertaling wordt een woordenboek met bestanden in XLIFF-indeling gedeeld met de professionele vertalers. Het woordenboek bevat een apart XLIFF-bestand voor elke landinstelling. Elk XLIFF-bestand bevat tekst die aan de eindgebruikers en plaatsaanduidingen voor de bijbehorende gelokaliseerde tekst wordt weergegeven.

Voer de volgende stappen uit om een formulier en het bijbehorende document te lokaliseren met behulp van Human Translators:

1. [Verbind AEM met uw leverancier](/help/sites-administering/tc-tic.md) van de vertaaldienst en [creeer configuraties](/help/sites-administering/tc-tic.md)van het vertaalintegratieframework.

1. [Koppel de pagina&#39;s van uw taalstramien](/help/sites-administering/tc-tic.md) aan de vertaalservice en frameworkconfiguraties.

1. [Identificeer het type inhoud](/help/sites-administering/tc-rules.md) dat u wilt vertalen.

1. [Bereid de inhoud voor vertaling](/help/sites-administering/tc-prep.md) voor door het taalstramien te ontwerpen en de basispagina&#39;s van taalkopieën te maken.

1. [Maak vertaalprojecten](/help/sites-administering/tc-manage.md) om de inhoud te verzamelen die u wilt vertalen en om het vertaalproces voor te bereiden.

1. Gebruik de vertaalprojecten om het vertaalproces [van de inhoud te](/help/sites-administering/tc-manage.md)beheren.

>[!NOTE]
>
>* Adaptieve formuliercomponenten bieden geen ondersteuning voor RTL-talen (van rechts naar links). Bijvoorbeeld Hebreeuws.
>



