---
title: Uw Postvak In om taken te beheren
description: Uw taken beheren met de Postvak IN Adobe Experience Manager 6.5.
exl-id: 80b7f179-b011-4f90-b5ab-9ef8a669d271
solution: Experience Manager, Experience Manager Sites
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '1155'
ht-degree: 6%

---

# Uw Postvak IN{#your-inbox}

U kunt meldingen ontvangen van verschillende AEM, zoals workflows en projecten, bijvoorbeeld over:

* Taken:

   * Deze kunnen ook worden gemaakt op verschillende punten binnen de AEM-interface, bijvoorbeeld onder **Projecten**,
   * dit kan het resultaat zijn van een workflow **Taak maken** of **Projecttaak maken** stap.

* Workflows:

   * tijdelijke items die acties vertegenwoordigen die u op pagina-inhoud moet uitvoeren;

      * dit is het product van de workflow **Deelnemer** stappen

   * items zijn mislukt, zodat beheerders de mislukte stap opnieuw kunnen proberen.

U ontvangt deze meldingen in uw eigen Postvak IN waar u ze kunt bekijken en actie kunt ondernemen.

>[!NOTE]
>
>Uit-van-de-doos AEM wordt voorgeladen met administratieve taken die aan de groep van de beheerdergebruiker worden toegewezen. Zie [Administratieve taken buiten de box](#out-of-the-box-administrative-tasks) voor meer informatie.

>[!NOTE]
>
>Zie ook voor meer informatie over de objecttypen:
>
>* [Projecten](/help/sites-authoring/touch-ui-managing-projects.md)
>* [Projecten - werken met taken](/help/sites-authoring/task-content.md)
>* [Workflows](/help/sites-authoring/workflows.md)
>* [Forms](/help/forms/using/introduction-aem-forms.md)
>

## Postvak IN van koptekst {#inbox-in-the-header}

Van om het even welke consoles wordt het huidige aantal punten in uw inbox getoond in de kopbal. De indicator kan ook worden geopend om of snelle toegang tot de pagina&#39;s te verlenen die acties of toegang tot inbox vereisen:

![wf-80](assets/wf-80.png)

>[!NOTE]
>
>Bepaalde acties worden ook weergegeven in het gedeelte [kaartweergave van de juiste bron](/help/sites-authoring/basic-handling.md#card-view).

## Administratieve taken buiten de box  {#out-of-the-box-administrative-tasks}

Uit-van-de-doos AEM wordt voorgeladen met vier taken die aan de groep van de beheerdergebruiker worden toegewezen.

* [Analyse en doelgericht configureren](/help/sites-administering/opt-in.md)
* [De lijst AEM beveiligingscontrole toepassen](/help/sites-administering/security-checklist.md)
* Verzamelde verzameling van verbruiksstatistieken inschakelen
* [HTTPS configureren](/help/sites-administering/ssl-by-default.md)

## De Postvak IN openen {#opening-the-inbox}

U opent als volgt het AEM-vak:

1. Klik op de indicator op de werkbalk.

1. Selecteer **Alles bekijken**. De **AEM Inbox** wordt geopend. In de inbox ziet u items uit workflows, projecten en taken.
1. De standaardweergave is [Lijstweergave](#inbox-list-view), maar u kunt ook schakelen naar [Kalenderweergave](#inbox-calendar-view). Dit gebeurt met de weergavekiezer (werkbalk, rechtsboven).

   Voor beide weergaven kunt u ook definiëren [Instellingen weergeven](#inbox-view-settings); de beschikbare opties zijn afhankelijk van de huidige weergave.

   ![wf-79](assets/inbox-list-view.png)

>[!NOTE]
>
>De inbox werkt als console, gebruik dus [Globale navigatie](/help/sites-authoring/basic-handling.md#global-navigation) of [Zoeken](/help/sites-authoring/search.md) om naar een andere locatie te gaan wanneer u klaar bent.

### Postvak IN - Lijstweergave {#inbox-list-view}

In deze weergave worden alle items weergegeven, samen met belangrijke relevante informatie:

![wf-82](assets/wf-82.png)

### Postvak IN - Kalenderweergave {#inbox-calendar-view}

In deze weergave worden de items weergegeven op basis van hun positie in de kalender en de exacte weergave die u hebt geselecteerd:

![wf-93](assets/wf-93.png)

U kunt:

* een specifieke weergave te selecteren; **Tijdlijn**, **Kolom**, **Lijst**

* de taken opgeven die moeten worden weergegeven volgens **Schema**; **Alles**, **Geplant**, **In uitvoering**, **Binnenkort**, **Achterstallig**

* boor neer voor meer gedetailleerde informatie over een punt
* Selecteer een datumbereik waarop u de weergave wilt scherpstellen:

![wf-91](assets/wf-91.png)

### Postvak IN - Instellingen {#inbox-view-settings}

Voor beide weergaven (Lijst en Kalender) kunt u instellingen definiëren:

* **Kalenderweergave**

  Voor **Kalenderweergave** u kunt configureren:

   * **Groeperen op**
   * **Planning** of **Geen**
   * **Kaartgrootte**

  ![wf-92](assets/wf-92.png)

* **Lijstweergave**

  Voor **Lijstweergave** u kunt het sorteermechanisme configureren:

   * **Veld sorteren**
   * **Sorteervolgorde**

  ![wf-83](assets/inbox-settings.png)

### Inbox - Admin Control {#inbox-admin-control}

Met de optie Beheer beheren kunnen beheerders:

* De kolommen AEM Postvak IN aanpassen

* Koptekst en logo aanpassen

* De weergave van navigatiekoppelingen in koptekst bepalen

De optie Beheer is alleen zichtbaar voor de leden van de `administrators` of `workflow-administrators` groep.

* **Kolomaanpassing**: Pas een AEM Inbox aan om de standaardtitel van een kolom te wijzigen, de positie van een kolom opnieuw te ordenen en extra kolommen weer te geven op basis van de gegevens van een workflow.
   * **Kolom toevoegen**: Selecteer een kolom die u wilt toevoegen in AEM Postvak IN.
   * **Kolom bewerken**: Plaats de muisaanwijzer op de kolomtitel en selecteer ![bewerken](assets/edit.svg) om een kolomweergavenaam in te voeren.
   * **Kolom verwijderen**: Selecteer de ![delete](assets/delete_updated.svg) pictogram om de kolom uit AEM Inbox te verwijderen.
   * **Kolom verplaatsen**: Sleep de ![move](assets/move_updated.svg) pictogram om een kolom naar een nieuwe positie in AEM Inbox te verplaatsen.

  ![beheer](assets/admin-control-column-customize.png)

* **Aanpassing branding**

   * **Koptekst aanpassen:** Geef de tekst op die in de koptekst moet worden weergegeven ter vervanging van de standaardtekst **Adobe Experience Manager** tekst.

   * **Logo aanpassen:** Geef de afbeelding op die in de koptekst moet worden weergegeven als logo. Upload een afbeelding in Digital Asset Management (DAM) en verwijs naar die afbeelding in het veld.

* **Gebruikersnavigatie**
   * **Navigatieopties verbergen:** Selecteer deze optie om de beschikbare navigatieopties in de koptekst te verbergen. De navigatieopties omvatten verbindingen aan andere oplossingen, de verbinding van de Hulp, en de auteursopties beschikbaar op het Tikken van het embleem of de tekst van Adobe Experience Manager.
* **Opslaan:** Klik deze optie om de montages te bewaren.

## Actie ondernemen op een item {#taking-action-on-an-item}

>[!NOTE]
>
>Hoewel het mogelijk is meerdere items te selecteren, kunnen acties slechts op één item tegelijk worden uitgevoerd.


1. Als u een actie wilt uitvoeren op een item, selecteert u de miniatuur voor het desbetreffende item. Pictogrammen voor de acties die op dat item van toepassing zijn, worden weergegeven op de werkbalk:

   ![wf-84](assets/wf-84.png)

   De acties zijn geschikt voor het item en omvatten:

   * **Voltooid** handeling, bijvoorbeeld een taak of workflowitem.
   * **Opnieuw toewijzen**/**Delegeren** een object.
   * **Openen** een item; afhankelijk van het type item kan deze handeling:

      * itemeigenschappen weergeven
      * een geschikt dashboard of een geschikte wizard voor verdere actie openen
      * open gerelateerde documentatie

   * **Stap terug** naar een vorige stap.
   * Bekijk de lading voor een werkschema.
   * Maak een project van het item.

   >[!NOTE]
   >
   >Zie voor meer informatie:
   >
   >* Workflowitems - [Deelnemen aan workflows](/help/sites-authoring/workflows-participating.md)

1. Afhankelijk van het geselecteerde item wordt een handeling gestart, bijvoorbeeld:

   * er wordt een dialoog geopend die op de actie is toegesneden .
   * er wordt een wizard Handelingen gestart.
   * er wordt een documentatiepagina geopend .

   Bijvoorbeeld: **Opnieuw toewijzen** Hiermee wordt een dialoogvenster geopend:

   ![wf-85](assets/wf-85.png)

   Afhankelijk van of een dialoogvenster, wizard, documentatiepagina is geopend, kunt u:

   * Bevestig de juiste actie, bijvoorbeeld Opnieuw toewijzen.
   * Annuleer de handeling.
   * Pijl-terug; als bijvoorbeeld een wizard Handelingen of een documentatiepagina is geopend, kunt u terugkeren naar het Postvak IN.

## Een taak maken {#creating-a-task}

In het Postvak IN kunt u taken maken:

1. Selecteren **Maken** vervolgens **Taak**.
1. Vul de vereiste velden in het dialoogvenster **Basis** en **Geavanceerd** tabs; alleen de **Titel** is verplicht, zijn alle andere facultatief:

   * **Basis**:

      * **Titel**
      * **Project**
      * **Geadresseerde**
      * **Inhoud**; dit is een verwijzing van de taak naar een locatie in de repository, vergelijkbaar met Payload.
      * **Beschrijving**
      * **Taakprioriteit**
      * **Begindatum**
      * **Vervaldatum**

   ![wf-86](assets/wf-86.png)

   * **Geavanceerd**

      * **Naam**: dit wordt gebruikt om de URL te vormen; als deze leeg is, wordt deze gebaseerd op de **Titel**.

   ![wf-87](assets/wf-87.png)

1. Selecteren **Verzenden**.

## Een project maken {#creating-a-project}

Voor bepaalde taken kunt u een [Project](/help/sites-authoring/projects.md) op basis van die taak :

1. Selecteer de gewenste taak door op de miniatuur te tikken of te klikken.

   >[!NOTE]
   >
   >Alleen taken die zijn gemaakt met de **Maken** van de **Inbox** kan worden gebruikt om een project tot stand te brengen.
   >
   >Workitems (van een workflow) kunnen niet worden gebruikt om een project te maken.

1. Selecteer **Project maken** op de werkbalk om de wizard te openen.
1. Selecteer de gewenste sjabloon en **Volgende**.
1. Geef de vereiste eigenschappen op:

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
   >Zie [Een project maken](/help/sites-authoring/touch-ui-managing-projects.md#creating-a-project) voor volledige informatie.

1. Selecteren **Maken** om de actie te bevestigen.

## Items in AEM Postvak IN filteren {#filtering-items-in-the-aem-inbox}

U kunt de vermelde items filteren:

1. Open de **AEM Inbox**.

1. Open de filterkiezer:

   ![wf-88](assets/wf-88.png)

1. U kunt de vermelde items filteren op basis van een reeks criteria, waarvan er vele kunnen worden verfijnd, bijvoorbeeld:

   ![wf-89](assets/wf-89.png)

   >[!NOTE]
   >
   >Met [Instellingen weergeven](#inbox-view-settings) u kunt de sorteervolgorde ook configureren wanneer u de [Lijstweergave](#inbox-list-view).
