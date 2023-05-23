---
title: Status van TouchUI-functie
description: Opmerkingen bij de release die specifiek zijn voor [!DNL Adobe Experience Manager] Interface voor aanraakbediening.
exl-id: 7b71e8db-e8c6-4470-bc22-db3d4600b7fc
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '1063'
ht-degree: 0%

---

# Status van TouchUI-functie {#touch-ui-feature-status}

AEM 6.4 en vanaf [Klassieke UI is afgekeurd](../release-notes/deprecated-removed-features.md). Adobe zal geen verdere verbeteringen aanbrengen in de klassieke gebruikersinterface en gebruikers worden aangeraden de krachtige nieuwe functies die beschikbaar zijn in de interface met aanraakbediening te benutten.

AEM introduceerde vanaf versie 6.0 een nieuwe gebruikersinterface die de &#39;touch-UI&#39; (gewoon &#39;touch-UI&#39; genoemd) wordt genoemd en die is uitgelijnd op de [!DNL Adobe Experience Cloud] en de algemene richtlijnen voor de gebruikersinterface van Adobe. Met bijna bereikte eigenschappariteit, is dit standaardUI in AEM met de erfenis geworden, Desktop-oriented interface die als &quot;klassieke UI wordt bedoeld.

Hoewel de meeste mogelijkheden aanwezig zijn in de interface met aanraakbediening, zijn er functies die nog niet zijn voltooid en in toekomstige versies zullen worden toegevoegd.

In de volgende lijst wordt de huidige status van de mogelijkheden weergegeven, zoals geïmplementeerd in AEM 6.5.

Voor aanbevelingen voor klanten die aan AEM 6.5 bevorderen, zie [Aanbevelingen voor gebruikersinterface voor klanten](/help/sites-deploying/ui-recommendations.md).

>[!NOTE]
>
>Deze pagina behandelt alleen eigenschappariteit met klassieke UI. Mogelijkheden die zijn toegevoegd aan en uniek zijn voor de interface met aanraakfuncties en die niet aanwezig zijn in de klassieke interface, worden niet vermeld.

>[!NOTE]
>
>Deze lijst is volledig, maar niet uitputtend.

## Legenda {#legend}

* **Voltooid**: De functie is volledig beschikbaar in de interface met aanraakbediening.
* **Meestal**: De functie is vooral beschikbaar in de interface met aanraakbediening.
* **Ontbreekt**: De functie is niet aanwezig in de interface met aanraakbediening. De klassieke interface moet hiervoor worden gebruikt.
* **Vervangen**: De functie is vervangen door een nieuwe implementatie die anders werkt.
* **Verwijderd**: De functie bestaat niet meer in de interface met aanraakbediening en wordt niet vervangen.

## Status van onderdeel: Sites-beheerder {#feature-status-sites-admin}

Dit is een lijst met mogelijkheden die de klassieke UI-sitebeheerder (`/siteadmin`) heeft en de status in de interface met aanraakbediening (`/sites.html`).

| Functie | Status | Opmerking |
|--- |--- |--- |
| Navigeren door sitehiërarchie | Voltooid | AEM 6.4 [inhoudsstructuurweergave](/help/sites-authoring/basic-handling.md#content-tree). |
| Workflow starten | Voltooid |  |
| Nieuwe pagina maken | Voltooid |  |
| Nieuwe site maken | Voltooid |  |
| Nieuwe start maken | Voltooid |  |
| Nieuwe bibliotheek maken | Voltooid |  |
| Map maken | Voltooid |  |
| Publicatiestatus tonen | Voltooid | Vanaf AEM 6.5 wordt de workflowstatus weergegeven in de lijstweergave. |
| Zoeken | Voltooid |  |
| Pagina kopiëren en plakken (dupliceren) | Voltooid |  |
| Pagina(&#39;s) verplaatsen | Voltooid |  |
| Pagina(&#39;s) publiceren | Voltooid |  |
| Pagina(&#39;s) zonder replicatierechten publiceren | Voltooid |  |
| Later publiceren | Voltooid |  |
| Boomstructuur publiceren | Voltooid |  |
| Publicatie van pagina(&#39;s) ongedaan maken | Voltooid |  |
| Publicatie van pagina(&#39;s) zonder replicatierechten ongedaan maken | Voltooid |  |
| Later verwijderen | Voltooid |  |
| Verwijderen | Voltooid |  |
| Vergrendelen/Ontgrendelen | Voltooid |  |
| Eigenschappen weergeven/bewerken | Voltooid |  |
| Machtigingen instellen op pagina(&#39;s) | Voltooid |  |
| Versiehistorie | Voltooid |  |
| Versie herstellen | Voltooid |  |
| Structuur herstellen en verwijderde pagina&#39;s herstellen | Ontbreekt | Klassieke UI gebruiken. |
| Verschil tonen tussen oude en huidige versie | Voltooid |  |
| Livecopy-acties (uitrollen) | Voltooid |  |
| Zie taalkopieën | Voltooid |  |
| Zoeken en vervangen | Ontbreekt | Klassieke UI gebruiken. |
| Melding in vak (JCR-gebeurtenissen) | Ontbreekt | Klassieke UI gebruiken. Wordt vervangen door een andere implementatie. |
| Verwijzingen | Voltooid | Weergave van inkomende paginakoppelingen die aan AEM 6.5 zijn toegevoegd. |

## Status van onderdeel: Pagina-editor {#feature-status-page-editor}

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
| Modus: Bewerken en voorvertonen | Voltooid |  |
| Responsieve voorvertoning | Voltooid |  |
| Modus: Ontwerp bewerken | Voltooid |  |
| Modus: Basisstructuur | Voltooid |  |
| Modus: Status van live kopiëren | Voltooid |  |
| Annotaties toevoegen | Voltooid |  |
| Eigenschappen bewerken | Voltooid |  |
| Pagina voor uitrollen | Voltooid |  |
| Workflow starten en weergeven | Voltooid |  |
| Workflowpakket-verwerking | Meestal | Volledig toegankelijk in interface met aanraakbediening. Er wordt nog steeds een lading van meerdere werkstromen weergegeven in een klassieke gebruikersinterface. |
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
| Tijdlijn verdraaien (kies datum/tijd en blader de site zoals deze vervolgens werd weergegeven) | Voltooid |  |
| Machtigingen instellen | Voltooid |  |
| Interface voor clientcontext | Vervangen | Gebruik de [ContextHub](/help/sites-authoring/ch-previewing.md) UI gaat verder. |
| Inhoudszoeker voor de verschillende mediatypen | Voltooid |  |
| Componentlijst | Voltooid |  |
| Componenten kopiëren en plakken | Voltooid |  |
| Lijst met componenten op het klembord | Ontbreekt |  |
| Ongedaan maken/Opnieuw | Voltooid |  |
| Inhoud naar tijdelijke aanduiding van onderdeel slepen | Voltooid |  |
| Sleep inhoud rechtstreeks in parsys placeholder met component auto-verwezenlijking | Voltooid |  |

## Status van onderdeel: Tekst-, tabel- en afbeeldingseditors {#feature-status-text-table-and-image-editors}

Dit is een lijst van mogelijkheden de klassieke Tekst UI, Lijst, en de Redacteur van het Beeld hebben en de status in touch-Toegelaten UI.

| Functie | Status | Opmerking |
|--- |--- |--- |
| RTF-editor | Voltooid | Geschikt op locatie, in dialoogvenster en op volledig scherm. |
| RTE-plug-ins in-/uitschakelen | Voltooid | Kan worden uitgevoerd met de [Sjablooneditor](/help/sites-authoring/templates.md). |
| RTE gebruiken voor normale tekst | Voltooid |  |
| RTE-plug-in: Koppelingen en ankers | Voltooid |  |
| RTE-plug-in: Tekentoewijzing | Voltooid |  |
| RTE-plug-in: Kopiëren/plakken | Voltooid |  |
| RTE-plug-in: Plakken vanuit Microsoft Word | Voltooid |  |
| RTE-plug-in: Zoeken en vervangen | Voltooid |  |
| RTE-plug-in: Tekstopmaak (vet, ...) | Voltooid |  |
| RTE-plug-in: Subscript en superscript | Voltooid |  |
| RTE-plug-in: Uitvullen | Voltooid |  |
| RTE-plug-in: Lijsten (opsommingstekens / nummers) | Voltooid |  |
| RTE-plug-in: Alineaopmaak | Voltooid |  |
| RTE-plug-in: Tekststijlen | Voltooid |  |
| RTE-plug-in: Broneditor (HTML bewerken) | Voltooid | Alleen beschikbaar in dialoogvenster en volledig scherm. |
| RTE-plug-in: Spellingcontrole | Voltooid |  |
| RTE-plug-in: Tabel (ingesloten tabeleditor) | Voltooid |  |
| RTE-plug-in: Ongedaan maken/Opnieuw | Voltooid |  |
| RTE-plug-in: In-line afbeeldingen toestaan | Voltooid |  |
| Tabeleditor | Voltooid | Geschikt op locatie, in dialoogvenster en op volledig scherm. |
| Afbeelding naar tabelcel slepen | Voltooid | In regel bruikbaar |
| Afbeeldingseditor | Voltooid | Geschikt op locatie, in dialoogvenster en op volledig scherm. |
| IPE-plug-ins in-/uitschakelen | Voltooid | AEM 6.3 introduceerde een interface in de [Sjablooneditor](/help/sites-authoring/templates.md). |
| IPE-plug-in: Uitsnijden | Voltooid |  |
| IPE-plug-in: Omdraaien | Voltooid |  |
| IPE-plug-in: Ongedaan maken/Opnieuw | Voltooid |  |
| IPE-plug-in: Afbeeldingskaart | Voltooid |  |
| IPE-plug-in: Roteren | Voltooid |  |
| IPE-plug-in: Zoomen | Voltooid |  |

## Status van onderdeel: Gereedschappen {#feature-status-tools}

Dit is een lijst met verschillende gereedschappen die de klassieke UI heeft en de status in de interface met aanraakbediening.

| Functie | Status | Opmerking |
|--- |--- |--- |
| Taakbeheer | Vervangen | 6.0 introduceerde Projecten en taken. |
| Workflow Inbox | Voltooid |  |
| Workflow naar paginasjabloonconfiguratie (`/etc/workflow/wcm/templates.html`) | Ontbreekt | Klassieke UI gebruiken. |
| Tagbeheer-interface | Voltooid |  |
| MSM/Blueprint Control Center | Voltooid |  |
| Gebruikersinterface van Blauwdrukbeheer | Voltooid |  |
| UI voor configuratie van uitrol | Ontbreekt | Klassieke UI gebruiken. |
| Gebruikersinterface, groepen en machtigingen | Meestal voltooid | Gebruik voor geavanceerde bewerkingen met bevoegdheden de klassieke gebruikersinterface. |
| Purperen (`/etc/versioning/purge.html`) | Ontbreekt | Klassieke UI gebruiken. |
| Controle van externe koppelingen (`/etc/linkchecker.html`) | Ontbreekt | Klassieke UI gebruiken. |
| Bulkeditor (`/etc/importers/bulkeditor.html`) | Ontbreekt | Klassieke UI gebruiken. |
| Miniaturen uploaden om deze toe te voegen of te overschrijven | Ontbreekt | Klassieke UI gebruiken. |
