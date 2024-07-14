---
title: XDP- en PDF-documenten ophalen in AEM Forms
description: Met AEM Forms kunt u formulieren en ondersteunde elementen uploaden en gebruiken met adaptieve formulieren. U kunt uploadformulieren en verwante bronnen ook als een ZIP-bestand bulksgewijs verzenden.
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: forms-manager
docset: aem65
role: Admin,User
exl-id: 9ecdc50a-31e3-46ae-948a-d1f6e6085734
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms,Foundation Components
source-git-commit: d7b9e947503df58435b3fee85a92d51fae8c1d2d
workflow-type: tm+mt
source-wordcount: '671'
ht-degree: 0%

---

# XDP- en PDF-documenten ophalen in AEM Forms{#getting-xdp-and-pdf-documents-in-aem-forms}

## Overzicht {#overview}

U kunt uw formulieren vanuit uw lokale bestandssysteem importeren in de CRX-opslagplaats door deze te uploaden naar AEM Forms. De uploadbewerking wordt ondersteund voor de volgende elementtypen:

* Formuliersjablonen (XFA-formulieren)
* PDF forms
* Document (vlakke PDF documenten)

U kunt de ondersteunde elementtypen afzonderlijk of als ZIP-archief uploaden. U kunt een element van het type `Resource` alleen uploaden naast een XFA-formulier in een ZIP-archief.

>[!NOTE]
>
>Zorg ervoor dat u lid bent van de `form-power-users` -groep en XDP-bestanden kunt uploaden. Neem contact op met de beheerder om lid te worden van de groep.

## Formulieren downloaden {#uploading-forms}

1. Meld u aan bij de gebruikersinterface van AEM Forms via `https://'[server]:[port]'/aem/forms.html` .
1. Navigeer naar de map waarin u het formulier of de map met formulieren wilt uploaden.
1. In de actietoolbar, creeer de uitgezochte **> Dossier** uploadt.

   ![ Dossiers van lokale opslagoptie onder Create ](assets/step.png)

1. In het dialoogvenster Formulier of pakketten uploaden kunt u bladeren naar het bestand dat u wilt uploaden en het bestand kiezen. In de bestandsbrowser worden alleen de ondersteunde bestandsindelingen (ZIP, XDP en PDF) weergegeven.

   >[!NOTE]
   >
   >Een bestandsnaam mag alleen alfanumerieke tekens, afbreekstreepjes of onderstrepingstekens bevatten.

1. Klik op Uploaden na bestandsselectie om de bestanden te uploaden of klik op Annuleren om het uploaden te annuleren. Een pop-up maakt een lijst van de activa die worden toegevoegd en de activa die bij de huidige plaats worden bijgewerkt.

   >[!NOTE]
   >
   >Voor een ZIP-bestand worden de relatieve paden van alle ondersteunde elementen weergegeven. Niet-ondersteunde elementen in het ZIP-bestand worden genegeerd en niet vermeld. Als het ZIP-archief echter alleen de niet-ondersteunde elementen bevat, wordt een foutbericht weergegeven in plaats van het pop-updialoogvenster.

   ![ uploadt dialoog wanneer het uploaden van een XFA vorm ](assets/upload-scr.png)

1. Als een of meer elementen een ongeldige bestandsnaam hebben, wordt een fout weergegeven. Corrigeer de in rood gemarkeerde bestandsnamen en upload ze opnieuw.

   ![ het bericht van de Fout wanneer het uploaden van een vorm XFA ](assets/upload-scr-err.png)

Wanneer het uploaden is voltooid, genereert een achtergrondworkflow miniaturen voor elk element op basis van de voorvertoning van het element. Nieuwere versies van elementen, indien geüpload, overschrijven de bestaande elementen.

### Beveiligde modus {#protected-mode}

Met AEM Forms-server kunt u JavaScript-code uitvoeren. Een kwaadaardige JavaScript-code kan schadelijk zijn voor een AEM Forms-omgeving. De beveiligde modus beperkt AEM Forms om XDP-bestanden alleen uit te voeren vanuit vertrouwde elementen en locaties. Alle XDP-gegevens die beschikbaar zijn in de gebruikersinterface van AEM Forms worden beschouwd als vertrouwde elementen.

De beveiligde modus is standaard ingeschakeld. Indien nodig kunt u de beveiligde modus uitschakelen:

1. Meld u als beheerder aan bij AEM webconsole. URL is https://&#39; [ server ]:[ haven ]&#39;/system/console/configMgr
1. Open Mobile Forms Configurations voor bewerking.
1. Deselecteer de Beschermde optie van de Wijze en klik **sparen**. De beveiligde modus is uitgeschakeld.

## XFA-formulieren waarnaar wordt verwezen bijwerken {#updating-referenced-xfa-forms}

In AEM Forms kan naar een XFA-formuliersjabloon worden verwezen door een adaptief formulier of een andere XFA-formuliersjabloon. Ook, kan een malplaatje naar een middel of een ander malplaatje verwijzen XFA.

Voor een adaptief formulier dat verwijst naar een XFA, zijn de velden gebonden aan de velden die beschikbaar zijn in de XFA. Bij het bijwerken van een formuliersjabloon probeert het bijbehorende adaptieve formulier te synchroniseren met de XFA. Voor meer details, zie [ Synchronizing adaptieve vormen met bijbehorende XFA ](../../forms/using/synchronizing-adaptive-forms-xfa.md).

Als u een formuliersjabloon verwijdert, wordt het afhankelijke adaptieve formulier of de afhankelijke formuliersjabloon beschadigd. Een dergelijk adaptief formulier wordt soms informeel een vuile vorm genoemd. In de gebruikersinterface van AEM Forms kunt u op de volgende twee manieren de vuile formulieren vinden.

* Er wordt een waarschuwingspictogram weergegeven op de miniatuur van het aangepaste formulier in de lijst met elementen. Het volgende bericht wordt weergegeven wanneer u de aanwijzer boven het waarschuwingspictogram houdt.\
  `Schema/Form Template for this adaptive form has been updated so go to Authoring mode and rebase it with new version.`

![ Waarschuwing voor een uit synchronisatie adaptieve vorm na het bijwerken van bijbehorende XFA ](assets/dirtyaf.png)

Er wordt een vlag onderhouden om aan te geven of een adaptief formulier bevuild is. Deze informatie is beschikbaar op de pagina met formuliereigenschappen, naast de metagegevens van het formulier. Alleen voor vuile adaptieve formulieren wordt met de eigenschap metadata `Model Refresh` de waarde `Recommended` weergegeven.

![ Verwijzing van een adaptieve vorm die uit synchronisatie met het model XFA ](assets/model-refresh.png) is
