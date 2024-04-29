---
title: Status van TouchUI-functie
description: Opmerkingen bij de release die specifiek zijn voor [!DNL Adobe Experience Manager] Interface voor aanraakbediening.
exl-id: 7b71e8db-e8c6-4470-bc22-db3d4600b7fc
solution: Experience Manager
feature: Release Information
role: User,Admin,Architect,Developer
source-git-commit: 10268f617b8a1bb22f1f131cfd88236e7d5beb47
workflow-type: tm+mt
source-wordcount: '1076'
ht-degree: 0%

---

# Status van TouchUI-functie {#touch-ui-feature-status}

Adobe Experience Manager (AEM) 6.4 en hoger [Klassieke interface is vervangen](../release-notes/deprecated-removed-features.md). Adobe maakt geen verdere verhogingen aan Klassieke UI en de gebruikers worden aangemoedigd om de krachtige nieuwe eigenschappen te gebruiken beschikbaar in touch-Toegelaten UI.

AEM introduceerde vanaf versie 6.0 een nieuwe gebruikersinterface die de &#39;touch-UI&#39; (genaamd &#39;Touch UI&#39;) wordt genoemd en die is uitgelijnd op de [!DNL Adobe Experience Cloud] en de algemene richtlijnen voor de gebruikersinterface van de Adobe. Met bijna bereikte eigenschappariteit, is dit standaardUI in AEM met de erfenis geworden, Desktop-oriented interface die als &quot;klassieke UI wordt bedoeld.

Hoewel de meeste mogelijkheden aanwezig zijn in de interface met aanraakbediening, zijn er functies die nog niet zijn voltooid en in toekomstige versies zullen worden toegevoegd.

In de volgende lijst wordt de status van de mogelijkheden weergegeven, zoals geïmplementeerd in AEM 6.5.

Voor aanbevelingen voor klanten die aan AEM 6.5 bevorderen, zie [Aanbevelingen voor gebruikersinterface voor klanten](/help/sites-deploying/ui-recommendations.md).

>[!NOTE]
>
>Deze pagina behandelt alleen eigenschappariteit met klassieke UI. Mogelijkheden die zijn toegevoegd aan en uniek zijn voor de interface met aanraakfuncties en die niet aanwezig zijn in de klassieke interface, worden niet vermeld.

>[!NOTE]
>
>Deze lijst is volledig, maar niet uitputtend.

## Legenda {#legend}

* **Voltooid**: De functie is volledig beschikbaar in de interface met aanraakbediening.
* **Meestal**: De functie is voornamelijk beschikbaar in de interface met aanraakbediening.
* **Ontbreekt**: De functie is niet aanwezig in de interface met aanraakbediening. De klassieke interface moet hiervoor worden gebruikt.
* **Vervangen**: De functie is vervangen door een nieuwe implementatie die anders werkt.
* **Verwijderd**: De functie bestaat niet meer in de interface met aanraakbediening en wordt niet vervangen.

## Functiestatus: Sites-beheerder {#feature-status-sites-admin}

Dit is een lijst met mogelijkheden die de klassieke UI-sitebeheerder (`/siteadmin`) heeft en de status in de interface met aanraakbediening (`/sites.html`).

| Functie | Status | Opmerking |
|--- |--- |--- |
| Navigeren door sitehiërarchie | Voltooid | AEM 6.4 [inhoudsstructuurweergave](/help/sites-authoring/basic-handling.md#content-tree). |
| Workflow starten | Voltooid |  |
| Nieuwe pagina maken | Voltooid |  |
| Nieuwe site maken | Voltooid |  |
| Nieuwe start maken | Voltooid |  |
| Nieuwe live kopie maken | Voltooid |  |
| Map maken | Voltooid |  |
| Publicatiestatus tonen | Voltooid | Vanaf AEM 6.5 wordt de workflowstatus weergegeven in de lijstweergave. |
| Zoeken | Voltooid |  |
| Pagina kopiëren en plakken (dupliceren) | Voltooid |  |
| Pagina&#39;s verplaatsen | Voltooid |  |
| Pagina&#39;s publiceren | Voltooid |  |
| Pagina&#39;s zonder replicatierechten publiceren | Voltooid |  |
| Later publiceren | Voltooid |  |
| Boomstructuur publiceren | Voltooid |  |
| Publicatie van pagina&#39;s ongedaan maken | Voltooid |  |
| Publicatie van pagina&#39;s zonder replicatierechten ongedaan maken | Voltooid |  |
| Later verwijderen | Voltooid |  |
| Verwijderen | Voltooid |  |
| Vergrendelen/Ontgrendelen | Voltooid |  |
| Eigenschappen weergeven/bewerken | Voltooid |  |
| Machtigingen op pagina&#39;s instellen | Voltooid |  |
| Versiehistorie | Voltooid |  |
| Versie herstellen | Voltooid |  |
| Boomstructuur herstellen en verwijderde pagina&#39;s herstellen | Ontbreekt | Klassieke gebruikersinterface gebruiken. |
| Verschil tonen tussen oude en huidige versie | Voltooid |  |
| Acties voor live kopiëren (rollout) | Voltooid |  |
| Zie taalkopieën | Voltooid |  |
| Zoeken en vervangen | Ontbreekt | Klassieke gebruikersinterface gebruiken. |
| Melding in vak (JCR-gebeurtenissen) | Ontbreekt | Klassieke gebruikersinterface gebruiken. In de toekomst vervangen door een andere implementatie. |
| Verwijzingen | Voltooid | Weergave van inkomende paginakoppelingen toegevoegd aan AEM 6.5. |

## Functiestatus: Pagina-editor {#feature-status-page-editor}

Dit is een lijst met mogelijkheden in de klassieke UI Page Editor (`/cf#`) heeft en de status in de aanraakbediening (`/editor.html`).

| Functie | Status | Opmerking |
|--- |--- |--- |
| Webpagina&#39;s bewerken | Voltooid |  |
| Mobiele webpagina&#39;s bewerken | Voltooid |  |
| Inhoud bewerken die is geïmporteerd via Design Importer | Voltooid |  |
| E-mails bewerken | Voltooid |  |
| Hybride mobiele apps bewerken | Voltooid |  |
| Forms bewerken | Voltooid |  |
| Aanbiedingen bewerken | Voltooid |  |
| Workflowmodellen bewerken | Voltooid |  |
| Modus: Bewerken en Voorvertoning | Voltooid |  |
| Responsieve voorvertoning | Voltooid |  |
| Modus: Ontwerp bewerken | Voltooid |  |
| Modus: Basisstructuur | Voltooid |  |
| Modus: Live Copy-status | Voltooid |  |
| Annotaties toevoegen | Voltooid |  |
| Eigenschappen bewerken | Voltooid |  |
| Pagina voor uitrollen | Voltooid |  |
| Workflow starten en weergeven | Voltooid |  |
| Workflowpakket-verwerking | Meestal | Toegankelijk in de interface met aanraakbediening. De veelvoudige werkschemalading die nog in klassieke UI wordt voorgesteld. |
| Pagina vergrendelen/ontgrendelen | Voltooid |  |
| Pagina publiceren | Voltooid |  |
| Publicatie van pagina ongedaan maken | Voltooid |  |
| Pagina kopiëren | Verwijderd | Sitebeheerder gebruiken voor [pagina&#39;s kopiëren](/help/sites-authoring/managing-pages.md#copying-and-pasting-a-page). |
| Pagina verplaatsen | Verwijderd | Sitebeheerder gebruiken voor [pagina&#39;s verplaatsen](/help/sites-authoring/managing-pages.md#moving-or-renaming-a-page). |
| Pagina verwijderen | Verwijderd | Sitebeheerder gebruiken voor [pagina&#39;s verwijderen](/help/sites-authoring/managing-pages.md#deleting-a-page). |
| Referenties tonen | Verwijderd | Gebruik Sitebeheerder om de [gedetailleerde referentielijst](/help/sites-authoring/author-environment-tools.md#references). |
| Controlelogboek | Verwijderd | Sitebeheer en [open-activiteitspoor](/help/sites-authoring/author-environment-tools.md#events-timeline). |
| Versie maken | Verwijderd | Sitebeheerder gebruiken voor [nieuwe versies maken](/help/sites-authoring/working-with-page-versions.md#creating-a-new-version). |
| Versie herstellen | Verwijderd | Sitebeheerder gebruiken voor [versies herstellen](/help/sites-authoring/working-with-page-versions.md#reverting-to-a-page-version). |
| Starten wisselen | Verwijderd | Sitebeheerder gebruiken voor [schakelaar tussen lanceringen](/help/sites-authoring/launches-promoting.md). |
| Pagina vertalen | Verwijderd | Sitebeheerder gebruiken voor [pagina toevoegen aan vertaalprojecten](/help/sites-administering/tc-manage.md). |
| Tijdlijn verdraaien (kies de datum/tijd en blader door de site zoals deze vervolgens werd weergegeven) | Voltooid |  |
| Machtigingen instellen | Voltooid |  |
| Interface voor clientcontext | Vervangen | Gebruik de [ContextHub](/help/sites-authoring/ch-previewing.md) UI gaat verder. |
| Inhoudszoeker voor de verschillende mediatypen | Voltooid |  |
| Componentlijst | Voltooid |  |
| Componenten kopiëren en plakken | Voltooid |  |
| Lijst met componenten op het klembord | Ontbreekt |  |
| Ongedaan maken/Opnieuw | Voltooid |  |
| Inhoud naar tijdelijke aanduiding van onderdeel slepen | Voltooid |  |
| Sleep inhoud rechtstreeks in parsys placeholder met component auto-verwezenlijking | Voltooid |  |

## Status van functie: tekst-, tabel- en afbeeldingseditors {#feature-status-text-table-and-image-editors}

Dit is een lijst van mogelijkheden de klassieke Tekst UI, Lijst, en de Redacteur van het Beeld hebben en de status in touch-Toegelaten UI.

| Functie | Status | Opmerking |
|--- |--- |--- |
| RTF-editor | Voltooid | Geschikt op locatie, in dialoogvenster en op volledig scherm. |
| RTE-plug-ins in-/uitschakelen | Voltooid | U kunt de opdracht [Sjablooneditor](/help/sites-authoring/templates.md). |
| RTE gebruiken voor normale tekst | Voltooid |  |
| RTE-plug-in: koppelingen en anker | Voltooid |  |
| RTE-plug-in: tekentoewijzing | Voltooid |  |
| RTE-plug-in: kopiëren/plakken | Voltooid |  |
| RTE-plug-in: plakken uit Microsoft® Word | Voltooid |  |
| RTE-plug-in: zoeken en vervangen | Voltooid |  |
| RTE-plug-in: tekstindelingen (vet, ...) | Voltooid |  |
| RTE-plug-in: Subscript en superscript | Voltooid |  |
| RTE-plug-in: Uitvullen | Voltooid |  |
| RTE-plug-in: lijsten (opsommingstekens/nummers) | Voltooid |  |
| RTE-plug-in: alineaopmaak | Voltooid |  |
| RTE-plug-in: tekststijlen | Voltooid |  |
| RTE-plug-in: Broneditor (HTML bewerken) | Voltooid | Alleen beschikbaar in dialoogvenster en volledig scherm. |
| RTE-plug-in: Spellchecker | Voltooid |  |
| RTE-plug-in: Tabel (ingesloten tabeleditor) | Voltooid |  |
| RTE-plug-in: Ongedaan maken/Opnieuw | Voltooid |  |
| RTE-plug-in: inline afbeeldingen toestaan | Voltooid |  |
| Tabeleditor | Voltooid | Geschikt op locatie, in dialoogvenster en op volledig scherm. |
| Afbeelding naar tabelcel slepen | Voltooid | In regel bruikbaar |
| Afbeeldingseditor | Voltooid | Geschikt op locatie, in dialoogvenster en op volledig scherm. |
| IPE-plug-ins in-/uitschakelen | Voltooid | AEM 6.3 introduceerde een interface in de [Sjablooneditor](/help/sites-authoring/templates.md). |
| IPE-plug-in: Uitsnijden | Voltooid |  |
| IPE-plug-in: omdraaien | Voltooid |  |
| IPE-plug-in: Ongedaan maken/Opnieuw | Voltooid |  |
| IPE-plug-in: Afbeeldingskaart | Voltooid |  |
| IPE-plug-in: Roteren | Voltooid |  |
| IPE-plug-in: Zoomen | Voltooid |  |

## Functiestatus: Gereedschappen {#feature-status-tools}

Dit is een lijst met verschillende gereedschappen voor de klassieke gebruikersinterface en de status in de interface met aanraakbediening.

| Functie | Status | Opmerking |
|--- |--- |--- |
| Taakbeheer | Vervangen | 6.0 introduceerde Projecten en taken. |
| Workflow Inbox | Voltooid |  |
| Workflow naar paginasjabloonconfiguratie (`/etc/workflow/wcm/templates.html`) | Ontbreekt | Klassieke gebruikersinterface gebruiken. |
| Tagbeheer-interface | Voltooid |  |
| MSM/Blueprint Control Center | Voltooid |  |
| Gebruikersinterface van Blauwdrukbeheer | Voltooid |  |
| UI voor configuratie van uitrol | Ontbreekt | Klassieke gebruikersinterface gebruiken. |
| Gebruikersinterface, Groepen en machtigingeninterface | Meestal voltooid | Gebruik voor geavanceerde bewerkingen met bevoegdheden de klassieke gebruikersinterface. |
| Purperen (`/etc/versioning/purge.html`) | Ontbreekt | Klassieke gebruikersinterface gebruiken. |
| Externe koppelingencontrole (`/etc/linkchecker.html`) | Ontbreekt | Klassieke gebruikersinterface gebruiken. |
| Bulkeditor (`/etc/importers/bulkeditor.html`) | Ontbreekt | Klassieke gebruikersinterface gebruiken. |
| Miniaturen uploaden om deze toe te voegen of te overschrijven | Ontbreekt | Klassieke gebruikersinterface gebruiken. |
