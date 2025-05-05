---
title: Aangepaste formulieren en recorddocumenten lokaliseren met AEM vertaalworkflow
description: Leer AEM vertaalworkflows gebruiken om adaptieve formulieren en recorddocumenten te lokaliseren.
content-type: reference
topic-tags: develop
noindex: true
feature: Adaptive Forms,Foundation Components
exl-id: ebec03a3-67a0-4ecd-84bb-8580388e048a
solution: Experience Manager, Experience Manager Forms
role: User, Developer
source-git-commit: d7b9e947503df58435b3fee85a92d51fae8c1d2d
workflow-type: tm+mt
source-wordcount: '802'
ht-degree: 0%

---

# Aangepaste formulieren en recorddocumenten lokaliseren met AEM vertaalworkflow {#using-aem-translation-workflow-to-localize-adaptive-forms-and-document-of-record}

<span class="preview"> de Adobe adviseert gebruikend de moderne en verlengbare gegevens vangen [ Componenten van de Kern ](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/introduction.html?lang=nl-NL) voor [ het creëren van nieuwe Aangepaste Forms ](/help/forms/using/create-an-adaptive-form-core-components.md) of [ het toevoegen van Aangepaste Forms aan de pagina&#39;s van AEM Sites ](/help/forms/using/create-or-add-an-adaptive-form-to-aem-sites-page.md). Deze componenten betekenen een aanzienlijke vooruitgang in de aanmaak van Adaptive Forms en zorgen voor indrukwekkende gebruikerservaring. In dit artikel wordt een oudere aanpak beschreven voor de auteur Adaptive Forms die gebruikmaakt van stichtingscomponenten. </span>

Met gelokaliseerde formulieren hebt u een groter publiek in verschillende regio&#39;s. Met de vertaalworkflow van Adobe Experience Manager kunt u adaptieve formulieren en de bijbehorende documenten lokaliseren. U kunt **machinevertaling** of **menselijke vertalers** gebruiken om een adaptieve vorm te lokaliseren.

In dit artikel wordt uitgelegd hoe u AEM vertaalworkflow kunt gebruiken met adaptieve formulieren en opnamedocumenten.

## Een adaptief formulier en document van records lokaliseren met behulp van automatische vertaling {#localizing-an-adaptive-form-and-document-of-record-using-machine-translation}

De vertaalservice zet uw inhoud direct om in adaptieve vorm en in een document met opnamen. AEM Forms is vooraf geconfigureerd voor het gebruik van een proefversie van Microsoft Translator voor machinevertaling. Voer de volgende stappen uit om automatische vertaling in te schakelen voor uw adaptieve formulieren en document of record:

1. Voor AEM Forms UI, selecteer een vorm, en selecteer **voeg Woordenboek** optie toe.
1. In **voeg Woordenboek aan het scherm van het Project van de Vertaling** toe, selecteer **een nieuw vertaalproject** of **voeg aan een bestaand vertaalproject** optie toe.
1. Op het **gebied van de Titel van het Project**, specificeer de titel. Bijvoorbeeld: `Government Reference Site - German locale.`
1. Op het **gebied van de Talen van het Doel**, specificeer een scène (bijvoorbeeld, `German(de)`), en klik **Gedaan**. U kunt meerdere landinstellingen opgeven. De vorm wordt vertaald aan alle scènes die in het **gebied van de Talen van het Doel** worden gespecificeerd.
1. In het Woordenboek toegevoegde dialoogvakje, klik **Open Projecten**. Open het nieuwe project in het scherm Projecten.
1. Klik de **ellipsen** bij de bodem van de **Vertaling Summiere** tegel. Het scherm Translation Summary wordt geopend.
1. Klik **uitgeven** pictogram bij de bovenkant van het **Summiere van de Vertaling** scherm. Open het **Vertaal** lusje en selecteer de Vertaling van de Machine in het **Vertaalmethode** scherm. Selecteer de aangewezen **Vertaalleverancier** en **Configuratie van de Wolk**. Klik het **Gereed** pictogram bij de bovenkant van het scherm.
1. Op de **tegel van de VertaalBaan**, klik ![ aem62forms_downarrow ](assets/aem62forms_downarrow.png) pictogram, en klik **Begin**. De status van de tegel verandert in Concept. Na voltooiing van de vertaling, de statusveranderingen in **Klaar voor overzicht**. Vernieuw de pagina na een paar minuten en controleer de status.
1. Na de statusveranderingen in **Klaar voor overzicht** op de **Taal van de VertaalBaan**, open de vorm in een browser venster. Er wordt een gelokaliseerde versie van het formulier weergegeven.

   >[!NOTE]
   >
   >* Voordat u de gelokaliseerde versie van het formulier opent in het browservenster, moet u controleren of de landinstelling van de browser is ingesteld op de landinstelling van het formulier. Als het formulier bijvoorbeeld wordt vertaald naar het Duits (de), stelt u de landinstelling van de browser in op het Duits (de).
   >* Adaptieve formuliercomponenten bieden geen ondersteuning voor RTL-talen (van rechts naar links). Bijvoorbeeld Hebreeuws.

   Het automatisch gegenereerde recorddocument wordt samen met het adaptieve formulier ook gelokaliseerd.

   Zie voor meer informatie over de instellingen en configuratie van Document of Record:

[Document met recordsjabloonconfiguratie](/help/forms/using/generate-document-of-record-for-non-xfa-based-adaptive-forms.md#p-document-of-record-template-configuration-p)

[Document met recordinstellingen](/help/forms/using/generate-document-of-record-for-non-xfa-based-adaptive-forms.md#p-document-of-record-settings-p)

1. [ pas de het brandmerken informatie van het document van verslag ](/help/forms/using/generate-document-of-record-for-non-xfa-based-adaptive-forms.md) aan en zorg ervoor dat browser scène aan de zelfde taal wordt geplaatst waaraan u de Aangepaste Vorm gebruikend machinetaal hebt gelokaliseerd. Met de landinstelling van de browser kunt u de brandinggegevens in het recorddocument lokaliseren.
1. Als u het gelokaliseerde document met records wilt weergeven, selecteert u Voorvertoning genereren. Het document met record PDF wordt gegenereerd en geopend op een nieuw tabblad in uw browser.

## Een adaptief formulier en het bijbehorende document lokaliseren met behulp van menselijke vertaling {#localizing-an-adaptive-form-and-its-document-of-record-using-human-translation}

In menselijke vertaling wordt de inhoud naar een vertaalbureau gestuurd en vertaald door professionele vertalers. Wanneer de vertaalde inhoud is voltooid, wordt deze geretourneerd en in AEM geïmporteerd. Wanneer uw vertaalbureau is geïntegreerd met AEM, wordt de inhoud automatisch verzonden tussen AEM en de vertaalprovider.

Voor vertaling wordt een woordenboek met bestanden in XLIFF-indeling gedeeld met de professionele vertalers. Het woordenboek bevat een apart XLIFF-bestand voor elke landinstelling. Elk XLIFF-bestand bevat tekst die aan de eindgebruikers en plaatsaanduidingen voor de bijbehorende gelokaliseerde tekst wordt weergegeven.

Voer de volgende stappen uit om een formulier en het bijbehorende document te lokaliseren met behulp van Human Translators:

1. [ verbind AEM met uw leverancier van de vertaaldienst ](/help/sites-administering/tc-tic.md) en [ creeer configuraties van het kader van de vertaalintegratie ](/help/sites-administering/tc-tic.md).

1. [ associeer de pagina&#39;s van uw taalmeester ](/help/sites-administering/tc-tic.md) met de vertaaldienst en kaderconfiguraties.

1. [ identificeer het type van inhoud ](/help/sites-administering/tc-rules.md) om te vertalen.

1. [ bereidt de inhoud voor vertaling ](/help/sites-administering/tc-prep.md) voor door de taalmeester te ontwerpen en de wortelpagina&#39;s van taalexemplaren te creëren.

1. [ creeer vertaalprojecten ](/help/sites-administering/tc-manage.md) om de inhoud te verzamelen om te vertalen en het vertaalproces voor te bereiden.

1. Gebruik de vertaalprojecten om [ het proces van de inhoudvertaling ](/help/sites-administering/tc-manage.md) te beheren.

>[!NOTE]
>
>* Adaptieve formuliercomponenten bieden geen ondersteuning voor RTL-talen (van rechts naar links). Bijvoorbeeld Hebreeuws.
>
