---
title: Nabewerking van brieven en interactieve communicatie
seo-title: Nabewerking van brieven
description: Na het verwerken van letters in Correspondence Management kunt u AEM en Forms-postprocessen maken, zoals afdrukken en e-mailen, en deze integreren met uw brieven.
seo-description: Na het verwerken van letters in Correspondence Management kunt u AEM en Forms-postprocessen maken, zoals afdrukken en e-mailen, en deze integreren met uw brieven.
uuid: 40cb349d-6ba2-4794-9ec6-dcab15c35b8d
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: correspondence-management
discoiquuid: 9b06c394-8e26-429c-b78f-22afa271aeb3
docset: aem65
feature: Correspondence Management
translation-type: tm+mt
source-git-commit: 48726639e93696f32fa368fad2630e6fca50640e
workflow-type: tm+mt
source-wordcount: '857'
ht-degree: 0%

---


# Na verwerking van letters en interactieve communicatie{#post-processing-of-letters-and-interactive-communications}

## Nabewerking {#post-processing}

De agenten kunnen postverwerkingswerkschema&#39;s op brieven en interactieve mededelingen associëren en uitvoeren. Nabewerkingsproces dat moet worden uitgevoerd, kan worden geselecteerd in de weergave Eigenschappen van de Letter-sjabloon. U kunt postprocessen instellen voor het e-mailen, afdrukken, faxen of archiveren van uw laatste brieven.

![Nabewerking](assets/ppoverview.png)

Om postprocessen met brieven of interactieve mededelingen te associëren, moet u eerst opstelling de postprocessen. Er kunnen twee typen workflows worden uitgevoerd op verzonden brieven:

1. **Forms Workflow:** Dit zijn de AEM Forms-workflows voor JEE-procesbeheer. Instructies voor het instellen van [Forms Workflow](#formsworkflow).

1. **AEM Workflow:** AEM workflows kunnen ook worden gebruikt als postprocessen voor verzonden brieven. Instructies voor het instellen van [AEM Workflow](../../forms/using/aem-forms-workflow.md).

## Forms Workflow {#formsworkflow}

1. Open in AEM Adobe Experience Manager Web Console Configuration voor uw server met behulp van de volgende URL: `https://<server>:<port>/<contextpath>/system/console/configMgr`

   ![Configuratiebeheer](assets/2configmanager-1.png)

1. Zoek op deze pagina AEM Forms Client SDK Configuration en vouw deze uit door erop te klikken.
1. Voer in Server-URL de naam van uw AEM Forms in op JEE-server, aanmeldingsgegevens in en klik op **Opslaan**.

   ![Geef een naam op voor de LiveCycle-server](assets/1cofigmanager.png)

1. Geef de gebruikersnaam en het wachtwoord op.
1. Zorg ervoor dat sun.util.agenda wordt toegevoegd aan Configuratie van de Firewall Deserialization.

   Ga naar Configuratie van de Firewall Deserialization en onder Gevoegde op lijst van gewenste personen klassen van pakketprefixen, voeg sun.util.agenda toe.

1. Nu zijn uw servers toegewezen en zijn de postprocessen in AEM Forms op JEE beschikbaar in de AEM gebruikersinterface terwijl het creëren van brieven.

   ![Letterscherm maken met vermelde postprocessen](assets/0configmanager.png)

1. Als u een proces/service wilt verifiëren, kopieert u de naam van een proces en gaat u terug naar de pagina Adobe Experience Manager Web Console Configurations > AEM Forms Client SDK Configuration en voegt u het proces toe als een nieuwe service.

   Als in de vervolgkeuzelijst Eigenschappen op de lettertypepagina bijvoorbeeld de naam van het proces wordt weergegeven als Forms Workflow -> ValidCCPostProcess/SaveXML, voegt u een servicenaam toe als `ValidCCPostProcess/SaveXML`.

1. Als u AEM Forms wilt gebruiken voor JEE-workflows voor naverwerking, stelt u de benodigde parameters en uitvoer in. De standaardwaarden van de parameters worden hieronder vermeld.

   Ga naar de pagina Configuraties van de Adobe Experience Manager-webconsole > **[!UICONTROL Correspondence Management Configurations]** en stel de volgende parameters in:

   1. **inPDFDoc (PDF-documentparameter):** Een PDF-document als invoer. Deze invoer bevat de gerenderde letter als invoer. De vermelde parameternamen kunnen worden geconfigureerd. Zij kunnen van configuraties van het Beheer van de Correspondentie van configuratie worden gevormd.
   1. **inXMLDoc (XML-gegevensparameter):** Een XML-document als invoer. Deze invoer bevat gegevens die door de gebruiker zijn ingevoerd in de vorm van XML.
   1. **inXDPDoc (XDP-documentparameter):** Een XML-document als invoer. Deze invoer bevat onderliggende layout (XDP).
   1. **inAttachmentDocs (parameter Bijlagedocumenten):** Een parameter voor lijstinvoer. Deze invoer bevat alle bijlagen als invoer.
   1. **redirectURL (Redirect URL Output):** Een uitvoertype dat de URL aangeeft waarnaar moet worden omgeleid.

   Uw formulierwerkstroom moet een PDF-documentparameter of een XML-gegevensparameter hebben als invoer met dezelfde naam als opgegeven in **[!UICONTROL Correspondence Management Configurations]**. Dit is vereist om het proces weer te geven in het vervolgkeuzemenu Verwerking.

## Instellingen voor de instantie Publiceren {#settings-on-the-publish-instance}

1. aanmelden bij `https://localhost:publishport/aem/forms`.
1. Navigeer naar **[!UICONTROL Letters]** om de gepubliceerde letter weer te geven die beschikbaar is op de publicatie-instantie.
1. Configureer de AEM DS-instellingen. Zie [AEM DS-instellingen configureren](../../forms/using/configuring-the-processing-server-url-.md).

>[!NOTE]
>
>Voordat u Forms- of AEM-workflows gebruikt, moet u de service voor DS-instellingen configureren voordat u gegevens van de publicatieserver verzendt. Anders zal de indiening van het formulier mislukken.

## Letter Instances Retrieval {#letter-instances-retrieval}

Opgeslagen letterinstanties kunnen verder worden gemanipuleerd, zoals het ophalen van letterinstanties en het verwijderen van letterinstanties, met behulp van de volgende API&#39;s die in LetterInstanceService zijn gedefinieerd.

<table>
 <tbody>
  <tr>
   <td><strong>Server-side API</strong></td>
   <td><strong>Handelingsnaam</strong></td>
   <td><strong>Beschrijving</strong></td>
  </tr>
  <tr>
   <td><p>Public LetterInstanceVO</p> <p>getLetterInstance(String letterInstanceId)</p> <p>Throws ICCException; </p> </td>
   <td>getLetterInstance</td>
   <td>Ophalen van de opgegeven letter </td>
  </tr>
  <tr>
   <td>Met Public void deleteLetterInstance(String letterInstanceId) wordt ICCException gegenereerd. </td>
   <td>deleteLetterInstance </td>
   <td>De opgegeven letter is verwijderd </td>
  </tr>
  <tr>
   <td>De lijst getAllLetterInstances (Vraag) werpt ICCException; </td>
   <td>getAllLetterInstances </td>
   <td>Deze API haalt brieveninstanties op die op de parameter van de inputvraag worden gebaseerd. Om alle brieveninstanties te halen, kan de vraagparameter als ongeldig worden overgegaan.<br /> </td>
  </tr>
  <tr>
   <td>Public Boolean letterInstanceExists(String letterInstanceName) genereert ICCException; </td>
   <td>letterInstanceExists </td>
   <td>Controleren of een LetterInstance bestaat met de opgegeven naam </td>
  </tr>
 </tbody>
</table>

## Een postproces koppelen aan een letter {#associating-a-post-process-with-a-letter}

Voer in de CCR-gebruikersinterface de volgende stappen uit om een postproces aan een letter te koppelen:

1. Houd de cursor boven een letter en tik op **Eigenschappen weergeven**.
1. Selecteer **Bewerken**.
1. Selecteer in de basiseigenschappen met de vervolgkeuzelijst Nabewerking het postproces dat u aan de letter wilt koppelen. In de vervolgkeuzelijst worden zowel de AEM- als Forms-gerelateerde postprocessen vermeld.
1. Tik **Opslaan**.
1. Na het vormen van de brief met het Proces van de Post, publiceer de brief en naar keuze op het publicatiegeval, specificeer de verwerkings URL in AEM dienst van Montages DS. Dit zorgt ervoor dat het postproces op de verwerkingsinstantie in werking wordt gesteld.

## Een ontwerpbrief opnieuw laden  {#reloaddraft}

Een instantie van een conceptbrief kan in gebruikersinterface worden opnieuw geladen door volgende url te gebruiken:

`https://<server>:<port>/aem/forms/`

`createcorrespondence.html?/random=$&cmLetterInstanceId=$<LetterInstanceId>`

LetterInstaceID: De unieke id van de verzonden letter.

Zie [Concepten opslaan en lettervarianten verzenden](../../forms/using/create-correspondence.md#savingdrafts) voor meer informatie over het opslaan van een conceptbrief.
