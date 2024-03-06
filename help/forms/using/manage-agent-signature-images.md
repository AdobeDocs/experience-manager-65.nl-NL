---
title: Afbeeldingen van handtekeningen van agent beheren
description: Nadat u een lettertypesjabloon hebt gemaakt, kunt u dit gebruiken om correspondentie te maken in AEM Forms door gegevens, inhoud en bijlagen te beheren.
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: correspondence-management
docset: aem65
feature: Correspondence Management
exl-id: f044ed75-bb72-4be1-aef6-2fb3b2a2697b
source-git-commit: 0aa929021aa724e4ec18d49fea26f8c0b0538bdc
workflow-type: tm+mt
source-wordcount: '692'
ht-degree: 0%

---

# Afbeeldingen van handtekeningen van agent beheren{#manage-agent-signature-images}

## Overzicht {#overview}

In het Beheer van de Correspondentie, kunt u een beeld gebruiken om agentenhandtekening in brieven terug te geven. Nadat u opstelling het beeld van de agentenhandtekening, terwijl het creëren van een brief, kunt u het beeld van de agentenhandtekening in de brief als handtekening van de afzenderagent teruggeven.

De agentSignatureImage DDE is een berekende DDE die het de handtekeningbeeld van de agent vertegenwoordigt. De uitdrukking voor dit gegevens verwerkte DDE gebruikt een nieuwe douanefunctie die door de bouwsteen van de Manager van de Uitdrukking wordt blootgesteld. Deze douanefunctie neemt agentID en agentFolder als inputparameters en haalt de beeldinhoud die op deze parameters wordt gebaseerd. Het SystemContext systeemgegevenswoordenboek geeft brieven in het Beheer van de Correspondentie toegang tot informatie in de huidige systeemcontext. De systeemcontext omvat informatie over de momenteel het programma geopende gebruiker en actieve configuratieparameters.

U kunt afbeeldingen toevoegen in de hoofdmap van de hoofdmap. In [Eigenschappen van Correspondentenbeheer](/help/forms/using/cm-configuration-properties.md)Met de eigenschap Hoofdmap van CM-gebruiker kunt u de map wijzigen van waaruit de afbeelding van de handtekening van de agent wordt opgehaald.

De waarde van agentFolder DDE wordt genomen van de configuratieparameter CMUserRoot voor de de configuratieeigenschappen van het Beheer van de Correspondentie. Deze configuratieparameter wijst standaard naar de map/content/cmUserRoot in de CRX-opslagplaats. U kunt de waarde van de configuratie CMUserRoot in de Eigenschappen van de Configuratie veranderen.
U kunt ook de aangepaste standaardfunctie negeren om uw eigen logica te definiëren voor het ophalen van de afbeelding van de gebruikershandtekening.

## Handtekeningafbeelding voor agent toevoegen {#adding-agent-signature-image}

1. Zorg ervoor dat de afbeelding met de handtekening van de agent dezelfde naam heeft als de gebruikersnaam AEM gebruiker. (Extensie is niet nodig voor de bestandsnaam van de afbeelding.)
1. Maak in CRX een map met de naam `cmUserRoot` in de inhoudsmap.

   1. Ga naar `https://'[server]:[port]'/crx/de`. Meld u indien nodig aan als beheerder.

   1. Klik met de rechtermuisknop op de knop **content** map en selecteer **Maken** > **Map maken**.

      ![Map maken](assets/1_createnode_cmuserroot.png)

   1. Voer in het dialoogvenster Map maken de naam van de map in als `cmUserRoot`. Klikken **Alles opslaan**.

      >[!NOTE]
      >
      >cmUserRoot is de standaardplaats waar AEM het beeld van de agentenhandtekening zoekt. U kunt het echter wijzigen door de eigenschap Hoofdmap van CM-gebruiker in het dialoogvenster [Eigenschappen van de Correspondentenbeheerconfiguratie](/help/forms/using/cm-configuration-properties.md).

1. In de Ontdekkingsreiziger van de Inhoud, navigeer aan de omslag cmUserRoot en voeg het beeld van de agentenhandtekening in het toe.

   1. Ga naar `https://'[server]:[port]'/crx/explorer/index.jsp`. Meld u indien nodig aan als beheerder.
   1. Klikken **Content Explorer**. De Inhoudsverkenner wordt in een nieuw venster geopend.
   1. Navigeer in Content Explorer naar de map cmUserRoot en selecteer deze. Klik met de rechtermuisknop op de knop **cmUserRoot** map en selecteer **Nieuw knooppunt**.

      ![Nieuw knooppunt in cmUserRoot](assets/2_cmuserroot_newnode.png)

      Maak de volgende ingangen in de rij voor nieuwe knoop en klik dan het groene vinkje.

      **Naam:** JohnDoe (of de naam van uw dossier van de agentenhandtekening)

      **Type:** nt:bestand

      Onder de `cmUserRoot` map, een nieuwe map genaamd `JohnDoe` (of de naam die u in de vorige stap hebt opgegeven) wordt gemaakt.

   1. Klik op de nieuwe map die u hebt gemaakt (hier `JohnDoe`). In de Inhoudsverkenner wordt de inhoud van de map grijs weergegeven.

   1. Dubbelklik op de knop **jcr:inhoud** eigenschap, het type instellen als **nt:resource** en klik vervolgens op het groene vinkje om de vermelding op te slaan.

      Als de eigenschap niet aanwezig is, maakt u eerst een eigenschap met de naam jcr:content.

      ![jcr:content, eigenschap](assets/3_jcrcontentntresource.png)

      Een van de subeigenschappen van jcr:content is jcr:data, die grijs wordt weergegeven. Dubbelklik op jcr:data. De eigenschap wordt bewerkbaar en de knop Bestand kiezen wordt weergegeven in de vermelding. Klikken **Bestand kiezen** en selecteert u het afbeeldingsbestand dat u als logo wilt gebruiken. Het afbeeldingsbestand hoeft geen extensie te hebben.

      ![JCR-gegevens](assets/5_jcrdata.png)

   Klikken **Alles opslaan**.

1. Zorg ervoor dat de XDP\layout die u in de letter gebruikt, een afbeeldingsveld linksonder heeft (of een andere geschikte plaats in de layout waar u de handtekening wilt weergeven) om de afbeelding van de handtekening te renderen.
1. Selecteer tijdens het maken van de correspondentie op het tabblad Gegevens een afbeeldingsveld voor de handtekeningafbeelding met de volgende stappen:

   1. Selecteer Systeem in het pop-upmenu Koppelingstype in het rechterdeelvenster.

   1. Selecteer agentSignatureImage DDE van de lijst in het paneel van het Element van Gegevens voor SystemContext DD.

   1. Sla de brief op.

1. Wanneer de letter wordt gerenderd, ziet u uw handtekening in de lettervoorvertoning in het afbeeldingsveld, afhankelijk van de layout.

   ![Handtekeningafbeelding van agent in de brief](assets/letterwithsignature.png)
