---
title: Handtekeningafbeeldingen van agent beheren
seo-title: Handtekeningafbeeldingen van agent beheren
description: Nadat u een lettertypesjabloon hebt gemaakt, kunt u dit gebruiken om correspondentie te maken in AEM Forms door gegevens, inhoud en bijlagen te beheren.
seo-description: Nadat u een lettertypesjabloon hebt gemaakt, kunt u dit gebruiken om correspondentie te maken in AEM Forms door gegevens, inhoud en bijlagen te beheren.
uuid: 48b2697e-6065-4e23-9aa8-333e7b11ede1
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: correspondence-management
discoiquuid: a81cdd53-f0fb-4ac5-b2ec-c19aeee7186e
docset: aem65
translation-type: tm+mt
source-git-commit: 317fadfe48724270e59644d2ed9a90fbee95cf9f

---


# Handtekeningafbeeldingen van agent beheren{#manage-agent-signature-images}

## Overzicht {#overview}

In het Beheer van de Correspondentie, kunt u een beeld gebruiken om agentenhandtekening in brieven terug te geven. Nadat u opstelling het beeld van de agentenhandtekening, terwijl het creëren van een brief, kunt u het beeld van de agentenhandtekening in de brief als handtekening van de afzenderagent teruggeven.

De agentSignatureImage DDE is een berekende DDE die het de handtekeningbeeld van de agent vertegenwoordigt. De uitdrukking voor dit gegevens verwerkte DDE gebruikt een nieuwe douanefunctie die door de bouwsteen van de Manager van de Uitdrukking wordt blootgesteld. Deze douanefunctie neemt agentID en agentFolder als inputparameters en haalt de beeldinhoud die op deze parameters wordt gebaseerd. Het SystemContext systeemgegevenswoordenboek geeft brieven in het Beheer van de Correspondentie toegang tot informatie in de huidige systeemcontext. De systeemcontext omvat informatie over de momenteel het programma geopende gebruiker en actieve configuratieparameters.

U kunt afbeeldingen toevoegen in de hoofdmap van de hoofdmap. In de Eigenschappen [van de Configuratie van het Beheer van de](/help/forms/using/cm-configuration-properties.md)Correspondentie, gebruikend het bezit van de Wortel van de Gebruiker van cm kunt u de omslag veranderen van waar het beeld van de agentenhandtekening wordt opgenomen.

De waarde van agentFolder DDE wordt genomen van de configuratieparameter CMUserRoot voor de de configuratieeigenschappen van het Beheer van de Correspondentie. Deze configuratieparameter wijst standaard naar de map/content/cmUserRoot in de CRX-opslagplaats. U kunt de waarde van de configuratie CMUserRoot in de Eigenschappen van de Configuratie veranderen.
U kunt ook de aangepaste standaardfunctie negeren om uw eigen logica te definiëren voor het ophalen van de afbeelding van de gebruikershandtekening.

## Handtekeningafbeelding voor agent toevoegen {#adding-agent-signature-image}

1. Zorg ervoor dat de afbeelding met de handtekening van de agent dezelfde naam heeft als de AEM-gebruikersnaam van de gebruiker. (Extensie is niet nodig voor de bestandsnaam van de afbeelding.)
1. Maak in CRX een map met de naam `cmUserRoot` in de inhoudsmap.

   1. Ga naar `https://'[server]:[port]'/crx/de`. Meld u indien nodig aan als beheerder.

   1. Klik met de rechtermuisknop op de **inhoudsmap** en selecteer **Maken** > Map **** maken.

      ![Map maken](assets/1_createnode_cmuserroot.png)

   1. Voer in het dialoogvenster Map maken de naam van de map in als `cmUserRoot`. Klik op Alles **opslaan**.

      >[!NOTE]
      >
      >cmUserRoot is de standaardplaats waar AEM het beeld van de agentenhandtekening zoekt. U kunt het echter wijzigen door de eigenschap Hoofdmap van CM-gebruiker in de configuratieeigenschappen [van](/help/forms/using/cm-configuration-properties.md)Correspondence Management te bewerken.

1. In de Ontdekkingsreiziger van de Inhoud, navigeer aan de omslag cmUserRoot en voeg het beeld van de agentenhandtekening in het toe.

   1. Ga naar `https://'[server]:[port]'/crx/explorer/index.jsp`. Meld u indien nodig aan als beheerder.
   1. Klik op **Inhoudsverkenner**. De Content Explorer wordt in een nieuw venster geopend.
   1. Navigeer in Content Explorer naar de map cmUserRoot en selecteer deze. Klik met de rechtermuisknop op de map **cmUserRoot** en selecteer **Nieuw knooppunt**.

      ![Nieuw knooppunt in cmUserRoot](assets/2_cmuserroot_newnode.png)

      Maak de volgende ingangen in de rij voor nieuwe knoop en klik dan het groene vinkje.

      **Naam:** JohnDoe (of de naam van uw dossier van de agentenhandtekening)

      **Type:** nt:bestand

      Onder de `cmUserRoot` map wordt een nieuwe map gemaakt met de naam `JohnDoe` (of de naam die u in de vorige stap hebt opgegeven).

   1. Klik op de nieuwe map die u hebt gemaakt (hier `JohnDoe`). In de Inhoudsverkenner wordt de inhoud van de map grijs weergegeven.

   1. Dubbelklik op de eigenschap **jcr:content** , stel het type in als **nt:resource** en klik op het groene vinkje om de vermelding op te slaan.

      Als de eigenschap niet aanwezig is, maakt u eerst een eigenschap met de naam jcr:content.

      ![jcr:content, eigenschap](assets/3_jcrcontentntresource.png)

      Een van de subeigenschappen van jcr:content is jcr:data, die grijs wordt weergegeven. Dubbelklik op jcr:data. De eigenschap wordt bewerkbaar en de knop Bestand kiezen wordt weergegeven in de vermelding. Klik op Bestand **** kiezen en selecteer het afbeeldingsbestand dat u als logo wilt gebruiken. Het afbeeldingsbestand hoeft geen extensie te hebben.

      ![JCR-gegevens](assets/5_jcrdata.png)
   Klik op Alles **opslaan**.

1. Zorg ervoor dat de XDP\layout die u in de letter gebruikt, een afbeeldingsveld linksonder heeft (of een andere geschikte plaats in de layout waar u de handtekening wilt weergeven) om de afbeelding van de handtekening te renderen.
1. Selecteer tijdens het maken van de correspondentie op het tabblad Gegevens een afbeeldingsveld voor de handtekeningafbeelding met de volgende stappen:

   1. Selecteer Systeem in het pop-upmenu Koppelingstype in het rechterdeelvenster.

   1. Selecteer agentSignatureImage DDE van de lijst in het paneel van het Element van Gegevens voor SystemContext DD.

   1. Sla de brief op.

1. Wanneer de letter wordt gerenderd, ziet u uw handtekening in de lettervoorvertoning in het afbeeldingsveld, afhankelijk van de layout.

   ![Handtekeningafbeelding van agent in de brief](assets/letterwithsignature.png)

