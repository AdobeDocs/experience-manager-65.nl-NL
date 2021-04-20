---
title: Aangepaste formulieren en recorddocumenten lokaliseren met AEM vertaalworkflow
seo-title: Aangepaste formulieren en recorddocumenten lokaliseren met AEM vertaalworkflow
description: Leer AEM vertaalworkflows gebruiken om adaptieve formulieren en recorddocumenten te lokaliseren.
seo-description: Leer AEM vertaalworkflows gebruiken om adaptieve formulieren en recorddocumenten te lokaliseren.
uuid: 6c87a283-0203-4cf7-989a-3770ddbbbd6e
content-type: reference
topic-tags: develop
discoiquuid: f5642571-9657-4ca1-93c5-4ae2eb91e967
noindex: true
feature: Adaptive Forms
translation-type: tm+mt
source-git-commit: 48726639e93696f32fa368fad2630e6fca50640e
workflow-type: tm+mt
source-wordcount: '781'
ht-degree: 0%

---


# De AEM vertaalworkflow gebruiken om aangepaste formulieren en recorddocumenten te lokaliseren {#using-aem-translation-workflow-to-localize-adaptive-forms-and-document-of-record}

Met gelokaliseerde formulieren hebt u een groter publiek in verschillende regio&#39;s. Met de vertaalworkflow van Adobe Experience Manager kunt u adaptieve formulieren en de bijbehorende documenten lokaliseren. U kunt **machinevertaling** of **menselijke vertalers** gebruiken om een adaptief formulier te lokaliseren.

In dit artikel wordt uitgelegd hoe u AEM vertaalworkflow kunt gebruiken met adaptieve formulieren en opnamedocumenten.

## Een adaptief formulier en document van records lokaliseren met behulp van automatische vertaling {#localizing-an-adaptive-form-and-document-of-record-using-machine-translation}

De vertaalservice zet uw inhoud direct om in adaptieve vorm en in een document met opnamen. AEM Forms is vooraf geconfigureerd voor het gebruik van een proefversie van Microsoft Translator voor computervertaling. Voer de volgende stappen uit om automatische vertaling in te schakelen voor uw adaptieve formulieren en document of record:

1. Selecteer een formulier in de gebruikersinterface van AEM Forms en tik op de optie **Woordenboek toevoegen**.
1. In **voeg Woordenboek aan het scherm van het Project van de Vertaling toe**, selecteer **creeer een nieuw vertaalproject** of **voeg aan een bestaand vertaalproject** optie toe.
1. Geef in het veld **Projecttitel** de titel op. Bijvoorbeeld, `Government Reference Site - German locale.`
1. Geef in het veld **Doeltalen** een landinstelling op (bijvoorbeeld `German(de)`) en klik op **Done**. U kunt meerdere landinstellingen opgeven. Het formulier wordt vertaald naar alle landinstellingen die zijn opgegeven in het veld **Doeltalen**.
1. Klik in het dialoogvenster Woordenboek toegevoegd op **Projecten openen**. Open het nieuwe project in het scherm Projecten.
1. Klik op de **ellipsen** onder aan de tegel **Translation Summary**. Het scherm Translation Summary wordt geopend.
1. Klik op het pictogram **Bewerken** boven aan het scherm **Vertaaloverzicht**. Open de tab **Translation** en selecteer Machine Translation in het scherm **Translation Method**. Selecteer de juiste **Vertaalprovider** en **Cloudconfiguratie**. Klik op het pictogram **Done** boven aan het scherm.
1. Klik in de **Vertaaltaak**-tegel op het pictogram ![aem62forms_downarrow](assets/aem62forms_downarrow.png) en klik op **Start**. De status van de tegel verandert in Concept. Na voltooiing van de vertaling, verandert de status in **Klaar voor overzicht**. Vernieuw de pagina na een paar minuten en controleer de status.
1. Nadat de status is gewijzigd in **Gereed voor revisie** op de tegel **Vertaaltaak**, opent u het formulier in een browservenster. Er wordt een gelokaliseerde versie van het formulier weergegeven.

   >[!NOTE]
   >
   >* Voordat u de gelokaliseerde versie van het formulier opent in het browservenster, moet u controleren of de landinstelling van de browser is ingesteld op de landinstelling van het formulier. Als het formulier bijvoorbeeld wordt vertaald naar het Duits (de), stelt u de landinstelling van de browser in op het Duits (de).
   >* Adaptieve formuliercomponenten bieden geen ondersteuning voor RTL-talen (van rechts naar links). Bijvoorbeeld Hebreeuws.


   Het automatisch gegenereerde recorddocument wordt samen met het adaptieve formulier ook gelokaliseerd.

   Zie voor meer informatie over de instellingen en configuratie van Document of Record:

   [Document met recordsjabloonconfiguratie](/help/forms/using/generate-document-of-record-for-non-xfa-based-adaptive-forms.md#p-document-of-record-template-configuration-p)

   [Document met recordinstellingen](/help/forms/using/generate-document-of-record-for-non-xfa-based-adaptive-forms.md#p-document-of-record-settings-p)

1. [Pas de brandinggegevens van het document met ](/help/forms/using/generate-document-of-record-for-non-xfa-based-adaptive-forms.md) opnamen aan en controleer of de landinstelling van de browser is ingesteld op de taal waarin u het adaptieve formulier hebt gelokaliseerd met de computertaal. Met de landinstelling van de browser kunt u de brandinggegevens in het recorddocument lokaliseren.
1. Tik op Voorvertoning genereren om het gelokaliseerde document met records te bekijken. Het document met de record-PDF wordt gegenereerd en geopend op een nieuw tabblad in uw browser.

## Een adaptief formulier en het bijbehorende document lokaliseren met behulp van menselijke vertaling {#localizing-an-adaptive-form-and-its-document-of-record-using-human-translation}

In menselijke vertaling wordt de inhoud naar een vertaalbureau gestuurd en vertaald door professionele vertalers. Wanneer de vertaalde inhoud is voltooid, wordt deze geretourneerd en in AEM geïmporteerd. Wanneer uw vertaalbureau is geïntegreerd met AEM, wordt de inhoud automatisch verzonden tussen AEM en de vertaalprovider.

Voor vertaling wordt een woordenboek met bestanden in XLIFF-indeling gedeeld met de professionele vertalers. Het woordenboek bevat een apart XLIFF-bestand voor elke landinstelling. Elk XLIFF-bestand bevat tekst die aan de eindgebruikers en plaatsaanduidingen voor de bijbehorende gelokaliseerde tekst wordt weergegeven.

Voer de volgende stappen uit om een formulier en het bijbehorende document te lokaliseren met behulp van Human Translators:

1. [Sluit AEM aan bij uw ](/help/sites-administering/tc-tic.md) leverancier van vertaalservices en  [maak configuraties](/help/sites-administering/tc-tic.md) van vertaalintegratieframework.

1. [Koppel de pagina&#39;s van uw taalbeheersing ](/help/sites-administering/tc-tic.md) aan de vertaalservice en frameworkconfiguraties.

1. [Identificeer het type ](/help/sites-administering/tc-rules.md) inhoud dat u wilt vertalen.

1. [Bereid de inhoud voor voor ](/help/sites-administering/tc-prep.md) vertaling door de master taal te ontwerpen en de basispagina&#39;s van taalkopieën te maken.

1. [Maak vertaalprojecten ](/help/sites-administering/tc-manage.md) om de te vertalen inhoud te verzamelen en het vertaalproces voor te bereiden.

1. Gebruik de vertaalprojecten om het vertaalproces [te beheren van de inhoud](/help/sites-administering/tc-manage.md).

>[!NOTE]
>
>* Adaptieve formuliercomponenten bieden geen ondersteuning voor RTL-talen (van rechts naar links). Bijvoorbeeld Hebreeuws.

>



