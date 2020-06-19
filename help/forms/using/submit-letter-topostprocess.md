---
title: Nabewerking van brieven en interactieve communicatie
seo-title: Nabewerking van brieven
description: Met de functie voor het achteraf verwerken van brieven in Correspondence Management kunt u AEM- en Forms-nabewerkingsprocessen maken, zoals afdrukken en e-mail, en deze integreren met uw brieven.
seo-description: Met de functie voor het achteraf verwerken van brieven in Correspondence Management kunt u AEM- en Forms-nabewerkingsprocessen maken, zoals afdrukken en e-mail, en deze integreren met uw brieven.
uuid: 40cb349d-6ba2-4794-9ec6-dcab15c35b8d
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: correspondence-management
discoiquuid: 9b06c394-8e26-429c-b78f-22afa271aeb3
docset: aem65
translation-type: tm+mt
source-git-commit: b703c59d7d913fc890c713c6e49e7d89211fd998
workflow-type: tm+mt
source-wordcount: '855'
ht-degree: 0%

---


# Nabewerking van brieven en interactieve communicatie{#post-processing-of-letters-and-interactive-communications}

## Nabewerking {#post-processing}

De agenten kunnen postverwerkingswerkschema&#39;s op brieven en interactieve mededelingen associëren en uitvoeren. Nabewerkingsproces dat moet worden uitgevoerd, kan worden geselecteerd in de weergave Eigenschappen van de Letter-sjabloon. U kunt postprocessen instellen voor het e-mailen, afdrukken, faxen of archiveren van uw laatste brieven.

![Nabewerking](assets/ppoverview.png)

Om postprocessen met brieven of interactieve mededelingen te associëren, moet u eerst opstelling de postprocessen. Er kunnen twee typen workflows worden uitgevoerd op verzonden brieven:

1. **Workflow voor formulieren:** Dit zijn de AEM Forms op de werkstromen van het JEE procesbeheer. Instructies voor het instellen van de [Forms Workflow](#formsworkflow).

1. **AEM-workflow:** AEM-workflows kunnen ook worden gebruikt als postprocessen voor verzonden brieven. Instructies voor het instellen van de [AEM-workflow](../../forms/using/aem-forms-workflow.md).

## Forms Workflow {#formsworkflow}

1. Open in AEM de Configuratie van de Console van het Web van de Adobe Experience Manager voor uw server gebruikend volgende URL: `https://<server>:<port>/<contextpath>/system/console/configMgr`

   ![Configuratiebeheer](assets/2configmanager-1.png)

1. Voor deze pagina, bepaal de plaats van de Configuratie van SDK van de Cliënt van AEM Forms en breid het uit door het te klikken.
1. Voer in Server-URL de naam van uw AEM Forms in op de JEE-server, aanmeldingsgegevens en klik op **Opslaan**.

   ![Geef een naam op voor de LiveCycle-server](assets/1cofigmanager.png)

1. Geef de gebruikersnaam en het wachtwoord op.
1. Zorg ervoor dat sun.util.agenda wordt toegevoegd aan Configuratie van de Firewall Deserialization.

   Ga naar Configuratie van de Firewall Deserialization en onder Toegestane klassen van pakketprefixen, voeg sun.util.agenda toe.

1. Nu zijn uw servers toegewezen en zijn de postprocessen in AEM Forms op JEE beschikbaar in het gebruikersinterface AEM terwijl het creëren van brieven.

   ![Letterscherm maken met vermelde postprocessen](assets/0configmanager.png)

1. Om een proces/de dienst voor authentiek te verklaren, kopieer de naam van een proces en ga terug naar de pagina van Configuraties van de Console van de Adobe Experience Manager > de Configuratie van SDK van de Cliënt van AEM Forms en voeg het proces als nieuwe dienst toe.

   Als in de vervolgkeuzelijst Eigenschappen op de lettertypepagina bijvoorbeeld de naam van het proces wordt weergegeven als Forms Workflow -> ValidCCPostProcess/SaveXML, voegt u een servicenaam toe als `ValidCCPostProcess/SaveXML`.

1. Als u AEM Forms op JEE-workflows wilt gebruiken voor naverwerking, stelt u de benodigde parameters en uitvoer in. De standaardwaarden van de parameters worden hieronder vermeld.

   Ga naar de pagina van Configuraties van de Console van de Adobe Experience Manager > **[!UICONTROL Correspondence Management Configurations]** en opstelling de volgende parameters:

   1. **inPDFDoc (parameter PDF-document):** Een PDF-document als invoer. Deze invoer bevat de gerenderde letter als invoer. De vermelde parameternamen kunnen worden geconfigureerd. Zij kunnen van configuraties van het Beheer van de Correspondentie van configuratie worden gevormd.
   1. **inXMLDoc (parameter XML-gegevens):** Een XML-document als invoer. Deze invoer bevat gegevens die door de gebruiker zijn ingevoerd in de vorm van XML.
   1. **inXDPDoc (XDP-documentparameter):** Een XML-document als invoer. Deze invoer bevat onderliggende layout (XDP).
   1. **inAttachmentDocs (parameter Bijlagedocumenten):** Een parameter voor lijstinvoer. Deze invoer bevat alle bijlagen als invoer.
   1. **redirectURL (Redirect URL Output):** Een uitvoertype dat de URL aangeeft waarnaar moet worden omgeleid.
   De formulierwerkstroom moet een PDF-documentparameter of een XML-gegevensparameter hebben als invoer met dezelfde naam als opgegeven in **[!UICONTROL Correspondence Management Configurations]**. Dit is vereist om het proces weer te geven in het vervolgkeuzemenu Verwerking.

## Instellingen voor de instantie Publiceren {#settings-on-the-publish-instance}

1. aanmelden bij `https://localhost:publishport/aem/forms`.
1. Navigeer naar **[!UICONTROL Letters]** de gepubliceerde brief die beschikbaar is in de publicatie-instantie.
1. Configureer de AEM DS-instellingen. Zie [AEM DS-instellingen](../../forms/using/configuring-the-processing-server-url-.md)configureren.

>[!NOTE]
>
>Wanneer u Forms of AEM-workflows gebruikt, voordat u een verzending vanaf de publicatieserver maakt, is het nodig de service DS-instellingen te configureren. Anders zal de indiening van het formulier mislukken.

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
   <td>Deze API haalt brieveninstanties op die op de parameter van de inputvraag worden gebaseerd. Om alle letterinstanties op te halen, kan de vraagparameter als ongeldig worden overgegaan.<br /> </td>
  </tr>
  <tr>
   <td>Public Boolean letterInstanceExists(String letterInstanceName) genereert ICCException; </td>
   <td>letterInstanceExists </td>
   <td>Controleren of een LetterInstance bestaat met de opgegeven naam </td>
  </tr>
 </tbody>
</table>

## Een postproces koppelen aan een brief {#associating-a-post-process-with-a-letter}

Voer in de CCR-gebruikersinterface de volgende stappen uit om een postproces aan een letter te koppelen:

1. Houd de muisaanwijzer boven een letter en tik op **Weergave-eigenschappen**.
1. Selecteer **Bewerken**.
1. Selecteer in de basiseigenschappen met de vervolgkeuzelijst Nabewerking het postproces dat u aan de letter wilt koppelen. In de vervolgkeuzelijst worden zowel de AEM- als de Forms-gerelateerde postprocessen vermeld.
1. Tik op **Opslaan**.
1. Nadat u de letter hebt geconfigureerd met het Post Process, publiceert u de letter en eventueel op de publicatie-instantie en geeft u de verwerkings-URL op in de AEM DS Settings-service. Dit zorgt ervoor dat het postproces op de verwerkingsinstantie in werking wordt gesteld.

## Een ontwerpbrief opnieuw laden  {#reloaddraft}

Een instantie van een conceptbrief kan in gebruikersinterface worden opnieuw geladen door volgende url te gebruiken:

`https://<server>:<port>/aem/forms/`

`createcorrespondence.html?/random=$&cmLetterInstanceId=$<LetterInstanceId>`

LetterInstaceID: De unieke id van de verzonden letter.

Zie Concepten [opslaan en briefexemplaren](../../forms/using/create-correspondence.md#savingdrafts)verzenden voor meer informatie over het opslaan van een conceptbrief.
