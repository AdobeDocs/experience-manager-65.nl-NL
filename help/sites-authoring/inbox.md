---
title: Uw inbox
seo-title: Uw inbox
description: Het beheren van uw taken met inbox
seo-description: Het beheren van uw taken met inbox
uuid: ddd48019-ce69-4a47-be2b-5b66ae2fe3c8
contentOwner: Chris Bohnert
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: introduction
content-type: reference
discoiquuid: 8b607b55-2412-469f-856b-0a3dea4b0efb
translation-type: tm+mt
source-git-commit: 033c32c581fddd5f632ad534f57c84b4d74a4104

---


# Uw inbox{#your-inbox}

U kunt berichten van diverse gebieden van AEM, met inbegrip van werkschema&#39;s en projecten ontvangen; bijvoorbeeld , over :

* Taken:

   * deze kunnen ook op verschillende punten binnen de AEM UI worden gecreëerd, bijvoorbeeld in het kader van **projecten**;
   * these can be the product of a workflow **Create Task** or **Create Project Task** step.

* Workflows:

   * de werkpunten die acties vertegenwoordigen die u op paginainhoud moet uitvoeren;

      * dit is het product van werkschema **Deelnemende** stappen
   * mislukkingspunten, om beheerders toe te staan om de ontbroken stap opnieuw te proberen.


U ontvangt deze berichten in uw eigen Postvak In waar u ze kunt bekijken en actie kunt ondernemen.

>[!NOTE]
>
>De uit-van-de-doos AEM komt pre-geladen met administratieve taken die aan de groep van de beheerdergebruiker worden toegewezen. Zie [uit-van-de-doos Administratieve Taken](#out-of-the-box-administrative-tasks) voor details.

>[!NOTE]
>
>Zie ook voor meer informatie over de objecttypes:
>
>* [Projecten](/help/sites-authoring/touch-ui-managing-projects.md)
>* [Projecten - werken met taken](/help/sites-authoring/task-content.md)
>* [Workflows](/help/sites-authoring/workflows.md)
>* [Formulieren](/help/forms/home.md)
>



## Postvak In in de Koptekst {#inbox-in-the-header}

Van om het even welke consoles wordt het huidige aantal punten in uw inbox getoond in de kopbal. Het indicatielampje kan ook worden geopend om snel toegang te geven tot de pagina(&#39;s) waarvoor actie(s) nodig is of om toegang te krijgen tot het Postvak IN:

![wf-80](assets/wf-80.png)

>[!NOTE]
>
>Bepaalde acties zullen ook in de [kaartmening van het aangewezen middel](/help/sites-authoring/basic-handling.md#card-view)worden getoond.

## De uit-van-de-doos Administratieve Taken {#out-of-the-box-administrative-tasks}

De uit-van-de-doos AEM komt pre-geladen met vier taken die aan de groep van de beheerdergebruiker worden toegewezen.

* [Analyse en gerichte taken configureren](/help/sites-administering/opt-in.md)
* [De beveiligingscontrolelijst voor AEM toepassen](/help/sites-administering/security-checklist.md)
* Laat de Geaggregeerde Inzameling van de Statistieken van het Gebruik toe
* [HTTPS configureren](/help/sites-administering/ssl-by-default.md)

## Het openen van Inbox {#opening-the-inbox}

Om het AEM-bericht in het vak te openen:

1. Klik/tik op de indicator in de toolbar.

1. Selecteer **Alles bekijken**. De **AEM Inbox** wordt geopend. In de inbox ziet u items uit workflows, projecten en taken.
1. De standaardweergave is [Lijstweergave](#inbox-list-view), maar u kunt ook schakelen naar [Kalenderweergave](#inbox-calendar-view). Dit gebeurt met de weergavekiezer (werkbalk, rechtsboven).

   Voor beide meningen kunt u de Montages [van de](#inbox-view-settings)Mening ook bepalen; de beschikbare opties zijn afhankelijk van de huidige mening.

   ![wf-79](assets/inbox-list-view.png)

>[!NOTE]
>
>De inbox werkt als console, gebruik dus [Globale navigatie](/help/sites-authoring/basic-handling.md#global-navigation) of [Zoeken](/help/sites-authoring/search.md) om naar een andere locatie te gaan wanneer u klaar bent.

### Postvak IN - Lijstweergave {#inbox-list-view}

Deze mening maakt een lijst van alle punten, samen met zeer belangrijke relevante informatie:

![wf-82](assets/wf-82.png)

### Postvak IN - Agendaweergave {#inbox-calendar-view}

In deze weergave worden objecten weergegeven op basis van hun positie in de agenda en de exacte weergave die je hebt geselecteerd:

![wf-93](assets/wf-93.png)

U kunt:

* een specifieke weergave selecteren; **Tijdlijn**, **kolom**, **lijst**

* specify the tasks to display according to **Schedule**; **All**, **Planned**, **In Progress**, **Due Soon**, **Past Due**

* boor neer voor meer gedetailleerde informatie over een punt
* selecteer een datumwaaier om de mening te concentreren:

![wf-91](assets/wf-91.png)

### Postvak IN - Instellingen {#inbox-view-settings}

Voor beide meningen (Lijst en Kalender) kunt u montages bepalen:

* **Kalenderweergave**

   Voor de Mening **van de** Kalender kunt u vormen:

   * **Groep door**
   * **Planning** of **Geen**
   * **Kaartformaat**
   ![wf-92](assets/wf-92.png)

* **Lijstweergave**

   Voor de Mening **van de** Lijst kunt u het soortmechanisme vormen:

   * **Sorteerveld**
   * **Sorteervolgorde**
   ![wf-83](assets/inbox-settings.png)

### Postvak IN - Beheer {#inbox-admin-control}

Met de optie Beheerbeheer kunnen beheerders:

* Koptekst en logo aanpassen

* Controle de vertoning van navigatiekoppelingen beschikbaar in kopbal

De optie van de Controle Admin toont in de drop-down lijst van de meningsselecteur slechts als u een lid van de beheerders of werkschema-beheerders groep bent.

![beheerderscontrole](assets/admin-control.png)

* **Aanpassing van merken**

   * **Koptekst aanpassen:** Specificeer de tekst aan vertoning in de kopbal.

   * **Logo aanpassen:** Upload een beeld in het Digitale Beheer van Activa (DAM) en verwijs naar dat beeld om het in de kopbal te tonen.

* **Gebruikersnavigatie**
   * **Navigatieopties verbergen:** Selecteer deze optie om navigatieopties te verbergen beschikbaar in de kopbal. De navigatieopties omvatten verbindingen aan andere oplossingen, de verbinding van de Hulp, en de auteursopties beschikbaar bij het aftappen van het embleem of de tekst van de Manager van de Ervaring van Adobe.
* **Opslaan:** Tik/klik op deze optie om de instellingen op te slaan.

## Actie ondernemen voor een object {#taking-action-on-an-item}

1. Om een actie op een punt te nemen, selecteer de duimnagel voor het aangewezen punt. De pictogrammen voor de acties die op dat punt van toepassing zijn zullen in de toolbar worden getoond:

   ![wf-84](assets/wf-84.png)

   De acties zijn geschikt voor het punt en omvatten:

   * **Volledige** actie; bijvoorbeeld, een taak of werkschemapunt.
   * **Wijs**/**delegeer** een punt opnieuw toe.
   * **Een object openen** ; afhankelijk van het type item kan deze actie:

      * de eigenschappen van het item weergeven
      * open een aangewezen dashboard of tovenaar voor verdere actie
      * open documentatie
   * **Stap terug** naar een vorige stap.
   * Bekijk de nuttige lading voor een werkschema.
   * Creeer een project van het punt.
   >[!NOTE]
   >
   >Voor meer informatie, zie:
   >
   >* Werkstroomitems - [Deelnemen aan werkstromen](/help/sites-authoring/workflows-participating.md)


1. Afhankelijk van het geselecteerde item wordt een actie gestart. bijvoorbeeld :

   * er zal een dialoog op gang worden gebracht die aan de actie is aangepast .
   * een actietovenaar zal worden begonnen.
   * er wordt een documentatiepagina geopend .
   Bijvoorbeeld, zal **toe:wijzen** een dialoog openen:

   ![wf-85](assets/wf-85.png)

   Afhankelijk van of een dialoog, tovenaar, documentatiepagina is geopend u kunt:

   * de passende maatregelen bevestigen; bijv. Opnieuw toewijzen.
   * Annuleer de actie.
   * Achterpijl; bijvoorbeeld, als een actietovenaar of documentatiepagina is geopend, kunt u aan Inbox terugkeren.


## Een taak maken {#creating-a-task}

Van inbox kunt u taken tot stand brengen:

1. Selecteer **creëren**, dan **Taak**.
1. Complete the necessary fields in the **Basic** and **Advanced** tabs; only the **Title** is mandatory, all others are optional:

   * **Basis**:

      * **Titel**
      * **Project**
      * **Geadresseerde**
      * **Inhoud**; vergelijkbaar met Payload, is dit een verwijzing van de taak naar een locatie in de repository
      * **Beschrijving**
      * **Taakprioriteit**
      * **Begindatum**
      * **Vervaldatum**
   ![wf-86](assets/wf-86.png)

   * **Geavanceerd**

      * **Naam**: dit zal worden gebruikt om de URL te vormen; indien blanco, wordt deze gebaseerd op de **titel**.
   ![wf-87](assets/wf-87.png)

1. Selecteer **Verzenden**.

## Een project maken {#creating-a-project}

Voor bepaalde taken kunt u een [Project](/help/sites-authoring/projects.md) tot stand brengen dat op die taak wordt gebaseerd:

1. Selecteer de aangewezen taak, door te tikken/op de duimnagel te klikken.

   >[!NOTE]
   >
   >Slechts kunnen de gecreeerde taken gebruikend de **Create** optie van **Inbox** worden gebruikt om een project tot stand te brengen.
   >
   >De werkpunten (van een werkschema) kunnen niet worden gebruikt om een project tot stand te brengen.

1. Selecteer **Project maken** op de werkbalk om de wizard te openen.
1. Select the appropriate template, then **Next**.
1. Specificeer de vereiste eigenschappen:

   * **Basis**

      * **Titel**
      * **Beschrijving**
      * **Begindatum**
      * **Vervaldatum**
      * **Gebruiker** en rol
   * **Geavanceerd**

      * **Naam**
   >[!NOTE]
   >
   >Zie [het Creëren van een Project](/help/sites-authoring/touch-ui-managing-projects.md#creating-a-project) voor volledige informatie.

1. Selecteer **creëren** om de actie te bevestigen.

## Filtrerende Punten in AEM Inbox {#filtering-items-in-the-aem-inbox}

U kunt de vermelde punten filtreren:

1. Open het **AEM-vak**.

1. Open de filterkiezer:

   ![wf-88](assets/wf-88.png)

1. U kunt de punten filtreren die volgens een waaier van criteria worden vermeld, veel waarvan kan worden verfijnd; bijvoorbeeld :

   ![wf-89](assets/wf-89.png)

   >[!NOTE]
   >
   >Met de Montages [van de](#inbox-view-settings) Mening kunt u de soortorde ook vormen wanneer het gebruiken van de Mening [van de](#inbox-list-view)Lijst.

