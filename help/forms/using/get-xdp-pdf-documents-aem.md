---
title: XDP- en PDF-documenten ophalen in AEM-formulieren
seo-title: XDP- en PDF-documenten ophalen in AEM-formulieren
description: Met AEM Forms kunt u formulieren en ondersteunde elementen uploaden en gebruiken met adaptieve formulieren. U kunt uploadformulieren en verwante bronnen ook als een ZIP-bestand bulksgewijs verzenden.
seo-description: Met AEM Forms kunt u formulieren en ondersteunde elementen uploaden en gebruiken met adaptieve formulieren. U kunt uploadformulieren en verwante bronnen ook als een ZIP-bestand bulksgewijs verzenden.
uuid: cd49b4a8-c282-4059-95a0-c98f6c92ab14
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: forms-manager
discoiquuid: 28b9f1d6-6a52-458f-a8ed-a206502eda0d
docset: aem65
translation-type: tm+mt
source-git-commit: 317fadfe48724270e59644d2ed9a90fbee95cf9f

---


# XDP- en PDF-documenten ophalen in AEM-formulieren{#getting-xdp-and-pdf-documents-in-aem-forms}

## Overzicht {#overview}

U kunt uw formulieren vanuit uw lokale bestandssysteem importeren in de CRX-opslagplaats door deze te uploaden naar AEM Forms. De uploadbewerking wordt ondersteund voor de volgende elementtypen:

* Formuliersjablonen (XFA-formulieren)
* PDF-formulieren
* Document (vlakke PDF-documenten)

U kunt de ondersteunde elementtypen afzonderlijk of als ZIP-archief uploaden. U kunt een element van het type alleen `Resource`naast een XFA-formulier uploaden in een ZIP-archief.

>[!NOTE]
>
>Controleer of u lid bent van de `form-power-users` groep en XDP-bestanden kunt uploaden. Neem contact op met de beheerder om lid te worden van de groep.

## Formulieren uploaden {#uploading-forms}

1. Meld u aan bij de gebruikersinterface van AEM Forms door toegang te krijgen tot `https://'[server]:[port]'/aem/forms.html`.
1. Navigeer naar de map waarin u het formulier of de map met formulieren wilt uploaden.
1. Tik op **Maken > Bestand uploaden** op de werkbalk Handelingen.

   ![Bestanden van lokale opslagoptie bij Maken](assets/step.png)

1. In het dialoogvenster Formulier of pakketten uploaden kunt u bladeren naar het bestand dat u wilt uploaden en het bestand kiezen. In de bestandsbrowser worden alleen de ondersteunde bestandsindelingen (ZIP, XDP en PDF) weergegeven.

   >[!NOTE]
   >
   >Een bestandsnaam mag alleen alfanumerieke tekens, afbreekstreepjes of onderstrepingstekens bevatten.

1. Klik op Uploaden na bestandsselectie om de bestanden te uploaden of klik op Annuleren om het uploaden te annuleren. Een pop-up maakt een lijst van de activa die worden toegevoegd en de activa die bij de huidige plaats worden bijgewerkt.

   >[!NOTE]
   >
   >Voor een ZIP-bestand worden de relatieve paden van alle ondersteunde elementen weergegeven. Niet-ondersteunde elementen in het ZIP-bestand worden genegeerd en niet vermeld. Als het ZIP-archief echter alleen de niet-ondersteunde elementen bevat, wordt een foutbericht weergegeven in plaats van het pop-updialoogvenster.

   ![Het dialoogvenster Uploaden tijdens het uploaden van een XFA-formulier](assets/upload-scr.png)

1. Als een of meer elementen een ongeldige bestandsnaam hebben, wordt een fout weergegeven. Corrigeer de in rood gemarkeerde bestandsnamen en upload ze opnieuw.

   ![Foutbericht bij het uploaden van een XFA-formulier](assets/upload-scr-err.png)

Wanneer het uploaden is voltooid, genereert een achtergrondworkflow miniaturen voor elk element op basis van de voorvertoning van het element. Nieuwere versies van elementen, indien geüpload, overschrijven de bestaande elementen.

### Beveiligde modus {#protected-mode}

Met de AEM Forms-server kunt u JavaScript-code uitvoeren. Een kwaadaardige JavaScript-code kan schadelijk zijn voor een omgeving van AEM Forms. De beveiligde modus beperkt AEM Forms om XDP-bestanden alleen uit te voeren vanuit vertrouwde elementen en locaties. Alle XDP-gegevens die beschikbaar zijn in de gebruikersinterface van AEM Forms worden beschouwd als vertrouwde elementen.

De beveiligde modus is standaard ingeschakeld. Indien nodig kunt u de beveiligde modus uitschakelen:

1. Meld u als beheerder aan bij de AEM-webconsole. De URL is https://&#39;[server]:[port]&#39;/system/console/configMgr
1. Open Configuraties van mobiele formulieren voor bewerking.
1. Schakel de optie Beveiligde modus uit en klik op **Opslaan**. De beveiligde modus is uitgeschakeld.

## XFA-formulieren waarnaar wordt verwezen bijwerken {#updating-referenced-xfa-forms}

In AEM Forms kan een XFA-formuliersjabloon worden doorgestuurd door een adaptief formulier of een andere XFA-formuliersjabloon. Ook, kan een malplaatje naar een middel of een ander malplaatje verwijzen XFA.

Voor een adaptief formulier dat verwijst naar een XFA, zijn de velden gebonden aan de velden die beschikbaar zijn in de XFA. Bij het bijwerken van een formuliersjabloon probeert het bijbehorende adaptieve formulier te synchroniseren met de XFA. Zie Aangepaste formulieren [synchroniseren met de bijbehorende XFA](../../forms/using/synchronizing-adaptive-forms-xfa.md)voor meer informatie.

Als u een formuliersjabloon verwijdert, wordt het afhankelijke adaptieve formulier of de afhankelijke formuliersjabloon beschadigd. Een dergelijk adaptief formulier wordt soms informeel een vuile vorm genoemd. In de gebruikersinterface van AEM Forms kunt u de vuile formulieren op de volgende twee manieren vinden.

* Er wordt een waarschuwingspictogram weergegeven op de miniatuur van het aangepaste formulier in de lijst met elementen. Het volgende bericht wordt weergegeven wanneer u de aanwijzer boven het waarschuwingspictogram houdt.\
   `Schema/Form Template for this adaptive form has been updated so please go to Authoring mode and rebase it with new version.`

![Waarschuwing voor een adaptief formulier dat niet gesynchroniseerd is na het bijwerken van de bijbehorende XFA](assets/dirtyaf.png)

Er wordt een vlag onderhouden om aan te geven of een adaptief formulier bevuild is. Deze informatie is beschikbaar op de pagina met formuliereigenschappen, naast de metagegevens van het formulier. Alleen voor vuile adaptieve formulieren wordt een eigenschap metadata `Model Refresh` weergegeven met een `Recommended` waarde.

![Indicatie van een adaptief formulier dat niet synchroon is met het XFA-model](assets/model-refresh.png)

