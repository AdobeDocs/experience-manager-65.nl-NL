---
title: Toepassingen van derden integreren in de AEM Forms-werkruimte
seo-title: Toepassingen van derden integreren in de AEM Forms-werkruimte
description: Integreer toepassingen van derden, zoals Correspondence Management, in de AEM Forms-werkruimte.
seo-description: Hoe kan ik-toepassingen van andere leveranciers, zoals Correspondence Management, integreren in de AEM Forms-werkruimte.
uuid: 7654cf86-b896-4db2-8f5d-6c1b2e6c229f
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: forms-workspace
discoiquuid: f70f21e3-3bec-490d-889e-faf496fb738b
docset: aem65
translation-type: tm+mt
source-git-commit: 1343cc33a1e1ce26c0770a3b49317e82353497ab
workflow-type: tm+mt
source-wordcount: '650'
ht-degree: 0%

---


# Toepassingen van derden integreren in de AEM Forms-werkruimte{#integrating-third-party-applications-in-aem-forms-workspace}

De werkruimte van AEM Forms ondersteunt het beheer van taken en voltooiingsactiviteiten voor formulieren en documenten. Deze formulieren en documenten kunnen XDP Forms, Flex®-formulieren of (afgekeurde) hulplijnen zijn die zijn gerenderd in XDP-, PDF-, HTML- of Flex-indeling.

Deze mogelijkheden worden verder versterkt. AEM Forms ondersteunt nu samenwerking met toepassingen van derden die functionaliteit ondersteunen die vergelijkbaar is met de AEM Forms-werkruimte. Een veelvoorkomend onderdeel van deze functionaliteit is de workflow van de toewijzing en de daaropvolgende goedkeuring van een taak. AEM Forms biedt een enkele uniforme ervaring voor AEM Forms-zakelijke gebruikers, zodat al dergelijke taaktoewijzingen of goedkeuringen voor de ondersteunde toepassingen kunnen worden verwerkt via de AEM Forms-werkruimte.

Laten we Correspondence Management bijvoorbeeld beschouwen als de voorbeeldkandidaat voor integratie met de AEM Forms-werkruimte. Correspondentiebeheer heeft het concept van een &#39;brief&#39;, die kan worden weergegeven en acties mogelijk maakt.

## Correspondentenbeheermiddelen maken {#create-correspondence-management-assets}

Begin door een malplaatje van het Beheer van de Correspondentie te creëren dat in de werkruimte van AEM Forms wordt teruggegeven. Zie [Een lettertypesjabloon maken](../../forms/using/create-letter.md) voor meer informatie.

Heb toegang tot het malplaatje van het Beheer van de Correspondentie bij zijn URL om te verifiëren of het malplaatje van het Beheer van de Correspondentie met succes kan worden teruggegeven. De URL heeft een patroon dat lijkt op `https://'[server]:[port]'/lc/content/cm/createcorrespondence.html?cmLetterId=encodedLetterId&cmUseTestData=1&cmPreview=0;`

waarbij `encodedLetterId` de URL-gecodeerde letter-id is. Geef dezelfde letter-id op wanneer u het renderproces voor werkruimtetaak in Workbench definieert.

## Een taak maken om een letter te renderen en te verzenden in AEM werkruimte {#create-a-task-to-render-and-submit-a-letter-in-aem-workspace}

Controleer voordat u deze stappen uitvoert of u lid bent van de volgende groepen:

* cm-agent-gebruikers
* WerkruimtGebruikers

Zie [Gebruikers toevoegen en configureren](/help/forms/using/admin-help/adding-configuring-users.md) voor meer informatie.

Gebruik de volgende stappen om een taak tot stand te brengen om een brief in AEM Werkruimte terug te geven en voor te leggen:

1. Start Workbench. Meld u als beheerder aan bij de localhost.
1. Klik op Bestand > Nieuw > Toepassing. Typ `CMDemoSample` in het veld Toepassingsnaam en klik op Voltooien.
1. Selecteer `CMDemoSample/1.0` en klik `NewProcess` met de rechtermuisknop aan. Typ `CMRenderer` in het naamveld en klik op Voltooien.
1. Sleep de activiteitskiezer voor het beginpunt en configureer deze:

   1. Selecteer in Presentatiegegevens de optie Een CRX-element gebruiken.

      ![useacrxasset](assets/useacrxasset.png)

   1. Blader naar een element. In het dialoogvenster Formulierelement selecteren worden op het tabblad Letters alle letters op de server weergegeven.

      ![Letter, tabblad](assets/letter_tab_new.png)

   1. Selecteer de juiste letter en klik op **OK**.

1. Klik op Actieprofielen beheren. Het dialoogvenster Actieprofiel beheren wordt geopend. Zorg ervoor dat het renderproces en het verzendproces op de juiste wijze zijn geselecteerd.
1. Als u de letter wilt openen met een XML-gegevensbestand voor gegevens, bladert u naar het desbetreffende gegevensbestand in het proces Gegevens voorbereiden en selecteert u dit.
1. Klik op OK.
1. Definieer de variabelen voor Uitvoer beginpunt en Taakbijlagen. De gedefinieerde variabelen bevatten gegevens van Start Point Output en Task Attachments.
1. (Optioneel) Als u een andere gebruiker aan de workflow wilt toevoegen, sleept u een activiteitskiezer, configureert u deze en wijst u deze toe aan een gebruiker. Schrijf een douaneomslag (hieronder steekproef wordt gegeven) of download en installeer DSC (hieronder gegeven) om het malplaatje van de Brief, de Output van het Punt van het Begin, en taakgehechtheid uit te breiden.

   Hieronder ziet u een voorbeeld van een aangepaste omslag:

   ```javascript
   public LetterInstanceInfo getLetterInstanceInfo(Document dataXML) throws Exception {
   try {
   if(dataXML == null)
   throw new Exception("dataXML is missing");
   
   CoreService coreService = getRemoteCoreService();
   if (coreService == null)
   throw new Exception("Unable to retrive service. Please verify connection details.");
   Map<String, Object> result = coreService.getLetterInstanceInfo(IOUtils.toString(dataXML.getInputStream(), "UTF-8"));
   LetterInstanceInfo letterInstanceInfo = new LetterInstanceInfo();
   
   List<Document> attachmentDocs = new ArrayList<Document>();
   List<byte[]> attachments = (List<byte[]>)result.get(CoreService.ATTACHMENT_KEY);
   if (attachments != null){
   for (byte[] attachment : attachments)
   { attachmentDocs.add(new Document(attachment)); }
   
   }
   letterInstanceInfo.setLetterAttachments(attachmentDocs);
   
   byte[] updateLayout = (byte[])result.get(CoreService.LAYOUT_TEMPLATE_KEY);
   if (updateLayout != null)
   { letterInstanceInfo.setLetterTemplate(new Document(updateLayout)); }
   
   else
   { throw new Exception("template bytes missing while getting Letter instance Info."); }
   
   return letterInstanceInfo;
   } catch (Exception e)
   { throw new Exception(e); }
   
   }
   ```

   [DSC ](assets/dscsample.zip)
voor downloaden van bestand ophalen: Een voorbeeld-DSC is beschikbaar in het bestand DSCSample.zip hierboven. Download en decomprimeer het bestand DSCSample.zip. Alvorens u de dienst van DSC gebruikt, moet u het vormen. Voor informatie, zie [Vorm de Dienst van DSC](../../forms/using/add-action-button-in-create-correspondence-ui.md#p-configure-the-dsc-service-p).

   Selecteer in het dialoogvenster Activiteiten definiëren de juiste activiteit, zoals getLetterInstanceInfo, en klik op **OK**.

1. Implementeer de toepassing. Als u hierom wordt gevraagd, checkt u de middelen in en slaat u deze op.
1. Meld u aan bij de werkruimte AEM formulieren op https://&#39;[server]:[poort]&#39;/lc/content/ws.
1. Open de taak die u hebt toegevoegd, CMRenderer. De letter Correspondence Management wordt weergegeven.

   ![werkruimte](assets/cminworkspace.png)

1. Vul de vereiste gegevens in en verzend de brief. Het venster wordt gesloten. Tijdens dit proces wordt de taak toegewezen aan de gebruiker die in stap 9 in de workflow is opgegeven.

   >[!NOTE]
   >
   >De knop Verzenden wordt pas ingeschakeld als alle vereiste variabelen in de letter zijn ingevuld.
