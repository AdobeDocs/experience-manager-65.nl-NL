---
title: Status van TouchUI-functie
description: Nota's van de versie specifiek voor  [!DNL Adobe Experience Manager]  aanraking-Toegelaten UI.
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

Adobe Experience Manager (AEM) 6.4 vanaf [ Klassieke UI wordt afgekeurd ](../release-notes/deprecated-removed-features.md). Adobe maakt geen verdere verhogingen aan Klassieke UI en de gebruikers worden aangemoedigd om de krachtige nieuwe eigenschappen te gebruiken beschikbaar in touch-Toegelaten UI.

Vanaf versie 6.0 werd AEM een nieuwe gebruikersinterface geïntroduceerd die de &#39;aanraakinterface&#39; (de zogenaamde &#39;aanraakinterface&#39;) wordt genoemd en die is uitgelijnd op de [!DNL Adobe Experience Cloud] en de algemene richtlijnen voor de gebruikersinterface van de Adobe. Met bijna bereikte eigenschappariteit, is dit standaardUI in AEM met de erfenis geworden, Desktop-oriented interface die als &quot;klassieke UI wordt bedoeld.

Hoewel de meeste mogelijkheden aanwezig zijn in de interface met aanraakbediening, zijn er functies die nog niet zijn voltooid en in toekomstige versies zullen worden toegevoegd.

In de volgende lijst wordt de status van de mogelijkheden weergegeven, zoals geïmplementeerd in AEM 6.5.

Voor aanbevelingen voor klanten die aan AEM 6.5 bevorderen, zie {de aanbevelingen van het 0} gebruikersinterface voor klanten [&#128279;](/help/sites-deploying/ui-recommendations.md).

>[!NOTE]
>
>Deze pagina behandelt alleen eigenschappariteit met klassieke UI. Mogelijkheden die zijn toegevoegd aan en uniek zijn voor de interface met aanraakfuncties en die niet aanwezig zijn in de klassieke interface, worden niet vermeld.

>[!NOTE]
>
>Deze lijst is volledig, maar niet uitputtend.

## Legenda {#legend}

* **Volledig**: De eigenschap is volledig beschikbaar in aanraking-toegelaten UI.
* **hoofdzakelijk**: De eigenschap is hoofdzakelijk beschikbaar in aanraking-toegelaten UI.
* **Ontbrekend**: De eigenschap is niet aanwezig in aanraking-toegelaten UI, moet klassieke UI worden gebruikt om deze actie te doen.
* **Vervangen**: De eigenschap werd vervangen met een nieuwe implementatie die verschillend werkt.
* **Verwijderd**: De eigenschap bestaat niet meer in aanraking-toegelaten UI en zal niet worden vervangen.

## Functiestatus: Sites-beheerder {#feature-status-sites-admin}

Dit is een lijst met mogelijkheden die de klassieke UI-sitebeheerder (`/siteadmin`) heeft en de status in de interface met aanraakbediening (`/sites.html`).

| Functie | Status | Opmerking |
|--- |--- |--- |
| Navigeren door sitehiërarchie | Voltooid | AEM 6.4 introduceerde de mening van de a [ inhoudsboom ](/help/sites-authoring/basic-handling.md#content-tree). |
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
| Publish-pagina&#39;s | Voltooid |  |
| Publish-pagina&#39;s zonder replicatierechten | Voltooid |  |
| Publish later | Voltooid |  |
| Publish tree | Voltooid |  |
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

Dit is een lijst van mogelijkheden de klassieke Redacteur van de Pagina UI (`/cf#`) heeft en de status in aanraking-toegelaten (`/editor.html`).

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
| Publish-pagina | Voltooid |  |
| Publicatie van pagina ongedaan maken | Voltooid |  |
| Pagina kopiëren | Verwijderd | Admin van de Plaats van het gebruik aan [ exemplaarpagina&#39;s ](/help/sites-authoring/managing-pages.md#copying-and-pasting-a-page). |
| Pagina verplaatsen | Verwijderd | Plaats Admin van het gebruik aan [ bewegingspagina&#39;s ](/help/sites-authoring/managing-pages.md#moving-or-renaming-a-page). |
| Pagina verwijderen | Verwijderd | Het Admin van de Plaats van het gebruik aan [ schrapt pagina&#39;s ](/help/sites-authoring/managing-pages.md#deleting-a-page). |
| Referenties tonen | Verwijderd | Gebruik Plaats Admin om de [ gedetailleerde verwijzingslijst ](/help/sites-authoring/author-environment-tools.md#references) te zien. |
| Controlelogboek | Verwijderd | Admin van de Plaats van het gebruik en [ open activiteitenspoor ](/help/sites-authoring/author-environment-tools.md#events-timeline). |
| Versie maken | Verwijderd | De Admin van de Plaats van het gebruik om [ nieuwe versies ](/help/sites-authoring/working-with-page-versions.md#creating-a-new-version) tot stand te brengen. |
| Versie herstellen | Verwijderd | Het gebruik Admin van de Plaats aan [ herstelt versies ](/help/sites-authoring/working-with-page-versions.md#reverting-to-a-page-version). |
| Starten wisselen | Verwijderd | De Admin van de Plaats van het gebruik aan [ schakelaar tussen lanceringen ](/help/sites-authoring/launches-promoting.md). |
| Pagina vertalen | Verwijderd | Admin van de Plaats van het gebruik aan [ voegt pagina aan vertaalprojecten ](/help/sites-administering/tc-manage.md) toe. |
| Tijdlijn verdraaien (kies de datum/tijd en blader door de site zoals deze vervolgens werd weergegeven) | Voltooid |  |
| Machtigingen instellen | Voltooid |  |
| Interface voor clientcontext | Vervangen | Gebruik [ ContextHub ](/help/sites-authoring/ch-previewing.md) UI die door:gaan. |
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
| RTE-plug-ins in-/uitschakelen | Voltooid | Het kan worden gedaan gebruikend de [ Redacteur van het Malplaatje ](/help/sites-authoring/templates.md). |
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
| RTE-plug-in: Source Editor (HTML bewerken) | Voltooid | Alleen beschikbaar in dialoogvenster en volledig scherm. |
| RTE-plug-in: Spellchecker | Voltooid |  |
| RTE-plug-in: Tabel (ingesloten tabeleditor) | Voltooid |  |
| RTE-plug-in: Ongedaan maken/Opnieuw | Voltooid |  |
| RTE-plug-in: inline afbeeldingen toestaan | Voltooid |  |
| Tabeleditor | Voltooid | Geschikt op locatie, in dialoogvenster en op volledig scherm. |
| Afbeelding naar tabelcel slepen | Voltooid | In regel bruikbaar |
| Afbeeldingseditor | Voltooid | Geschikt op locatie, in dialoogvenster en op volledig scherm. |
| IPE-plug-ins in-/uitschakelen | Voltooid | AEM 6.3 introduceerde een UI in de [ Redacteur van het Malplaatje ](/help/sites-authoring/templates.md). |
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
| Workflow voor configuratie paginasjabloon (`/etc/workflow/wcm/templates.html`) | Ontbreekt | Klassieke gebruikersinterface gebruiken. |
| Tagbeheer-interface | Voltooid |  |
| MSM/Blueprint Control Center | Voltooid |  |
| Gebruikersinterface van Blauwdrukbeheer | Voltooid |  |
| UI voor configuratie van uitrol | Ontbreekt | Klassieke gebruikersinterface gebruiken. |
| Gebruikersinterface, Groepen en machtigingeninterface | Meestal voltooid | Gebruik voor geavanceerde bewerkingen met bevoegdheden de klassieke gebruikersinterface. |
| Versies wissen (`/etc/versioning/purge.html`) | Ontbreekt | Klassieke gebruikersinterface gebruiken. |
| External LinkChecker (`/etc/linkchecker.html`) | Ontbreekt | Klassieke gebruikersinterface gebruiken. |
| Bulkeditor (`/etc/importers/bulkeditor.html`) | Ontbreekt | Klassieke gebruikersinterface gebruiken. |
| Miniaturen uploaden om deze toe te voegen of te overschrijven | Ontbreekt | Klassieke gebruikersinterface gebruiken. |
