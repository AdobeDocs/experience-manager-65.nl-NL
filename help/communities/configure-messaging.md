---
title: Berichtenonderdeel
description: Leer hoe te om de eigenschap van het Overseinen van AEM Communities te vormen om communautaire leden toe te staan om met elkaar meer privé in wisselwerking te staan.
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: authoring
content-type: reference
docset: aem65
exl-id: d121dc05-7d15-44ba-8d2d-b59d6c6480c8
solution: Experience Manager
feature: Communities
role: Admin
source-git-commit: 1f56c99980846400cfde8fa4e9a55e885bc2258d
workflow-type: tm+mt
source-wordcount: '952'
ht-degree: 0%

---

# Berichtenonderdeel {#messaging-feature}

Naast de openbaar zichtbare interacties die in forums en commentaren voorkomen, laat de overseineneigenschap van AEM Communities communityleden toe om met elkaar meer privé in wisselwerking te staan.

Deze eigenschap kan worden omvat wanneer a [ communautaire plaats ](/help/communities/overview.md#communitiessites) wordt gecreeerd.

De overseineneigenschap laat u het volgende doen:

**A** - verzend een bericht naar één of meerdere communautaire leden

**B** - verzend directe berichten in [ bulk aan de groepen van het communautaire lid ](/help/communities/messaging.md#group-messaging)

**C** - verzend een bericht met gehechtheid

**D** - door:sturen een bericht

**E** - antwoord aan een bericht

**F** - schrap een bericht

**G** - herstel een geschrapt bericht

![ overseinen-sectie ](assets/messaging-section.png)

![ herstel-bericht ](assets/restore-message.png)

Om de overseineneigenschap toe te laten en te wijzigen, zie:

* [ vorm Overseinen ](/help/communities/messaging.md) voor beheerders
* [ Hoofdzaak van het Overseinen ](/help/communities/essentials-messaging.md) voor ontwikkelaars

>[!NOTE]
>
>Het wordt niet gesteund om `Compose Message, Message, or Message List` componenten (die in `Communities` worden gevonden componentengroep) aan een pagina op auteur toe te voegen geeft wijze uit.

## Berichtcomponenten configureren {#configure-messaging-components}

Wanneer het overseinen voor een communautaire plaats wordt toegelaten, wordt het opstelling zonder verdere configuratie noodzakelijk. De informatie wordt verstrekt als er een behoefte is om de standaardconfiguratie te veranderen.

### Berichtlijst configureren (berichtvenster) {#configure-message-list-message-box}

Om de configuratie van de lijst van berichten voor **Inbox** te wijzigen, **Verzonden Punten**, en **afval** pagina&#39;s van de overseineneigenschap, open de plaats in [ auteur geeft wijze ](/help/communities/sites-console.md#authoring-site-content) uit.

1. Op `Preview` wijze, selecteer de **verbinding van Berichten** om de belangrijkste overseinenpagina te openen. Dan selecteer of **Inbox**, **Verzonden Punten** of **Afval** om de component voor die berichtlijst te vormen.

1. Selecteer in de modus `Edit` de component op de pagina.
1. U opent het configuratiedialoogvenster door overerving te annuleren door het pictogram `link` te selecteren.
Nadat de overerving is geannuleerd, is het mogelijk om het configuratiepictogram te selecteren om het configuratiedialoogvenster te openen.

1. Nadat de configuratie is voltooid, moet de overerving worden hersteld door het pictogram `broken link` te selecteren.

![ vorm-bericht-lijst ](assets/configure-message-list.png)

#### Het tabblad Basis {#basic-tab}

![ basis-lusje-messagelist ](assets/basic-tab-messagelist.png)

* **de selecteur van de Dienst**

  (*Vereiste*) reeks dit aan de waarde van het bezit **`serviceSelector.name`** van de [ Dienst van de Verrichtingen van het Overseinen van AEM Communities ](/help/communities/messaging.md#messaging-operations-service).

* **stelt Pagina** samen

  (*Vereist*) de pagina om te openen wanneer een lid de **`Reply`** knoop klikt. De doelpagina zou de **moeten bevatten samenstelt Bericht** vorm.

* **Antwoord/Mening als Middel**

  Als deze optie is ingeschakeld, verwijzen de URL van de reactie en de URL van de weergave naar een bron, of anders worden gegevens doorgegeven als queryparameters in de URL.

* **Vorm van de Vertoning van het Profiel**

  Het profielformulier dat moet worden gebruikt om het afzenderprofiel weer te geven.

* **omslag van het Afval**

  Als deze optie is ingeschakeld, worden in deze component Berichtlijst alleen berichten weergegeven die zijn gemarkeerd als verwijderd (prullenbak).

* **Wegen van de Omslag**

  (*Vereiste*) Verwijzend de waarden die voor **worden geplaatst inbox.path.name** en **sentitems.path.name** in de [ Dienst van de Verrichtingen van het Overseinen van AEM Communities ](/help/communities/messaging.md#messaging-operations-service). Wanneer het vormen voor `Inbox`, voeg één ingang toe gebruikend de waarde van **inbox.path.name**. Wanneer het vormen voor `Outbox`, voeg één ingang toe gebruikend de waarde van **sentitems.path.name**. Voeg bij de configuratie voor `Trash` twee items met beide waarden toe.

#### Tabblad Weergave {#display-tab}

![ vertoning-lusje-bericht-lijst ](assets/display-tab-message-list.png)

* **Markering Gelezen Knoop**

  Als gecontroleerd, vertoningen a `Read` knoop die een bericht toestaat om als gelezen worden gemerkt.

* **Knoop van het Teken Ongelezen**

  Als deze optie is ingeschakeld, wordt een knop `Mark Unread` weergegeven waarmee een bericht kan worden gemarkeerd als gelezen.

* **Knop van de Schrapping**

  Als deze optie is ingeschakeld, wordt een knop `Delete` weergegeven waarmee een bericht kan worden gemarkeerd als gelezen. Hiermee dupliceert u de verwijderfunctionaliteit als **`Message Options`** ook is ingeschakeld.

* **Opties van het Bericht**

  Als deze optie is ingeschakeld, worden knoppen **`Reply`** , **`Reply All`** , **`Forward`** en **`Delete`** weergegeven waarmee een bericht kan worden verzonden of verwijderd. Hiermee dupliceert u de verwijderfunctionaliteit als **`Delete Button`** ook is ingeschakeld.

* **Berichten per Pagina**

  Het opgegeven aantal is het maximumaantal berichten dat per pagina in een pagineringsschema wordt weergegeven. Als geen aantal wordt gespecificeerd (verlaten leeg), dan worden alle berichten getoond en er is geen paginering.

* **de patronen van de tijdstempel**

  Geef tijdstempelpatronen op voor een of meer talen. Standaard is dit voor en, de, fr, it, es, ja, zh_CN, ko_KR.

* **Gebruiker van de Vertoning**

  Kies **`Sender`** of **`Recipients`** , zodat u kunt bepalen of de afzender of de Ontvanger moet worden weergegeven.

### Samenstellingsbericht configureren {#configure-compose-message}

Om de configuratie van de samenstellen berichtpagina te wijzigen, open de plaats in [ auteur geeft wijze ](/help/communities/sites-console.md#authoring-site-content) uit.

* Op `Preview` wijze, selecteer de **verbinding van Berichten** om de belangrijkste overseinenpagina te openen. Selecteer vervolgens de knop Nieuw bericht zodat u de pagina `Compose Message` kunt openen.

* Selecteer in de modus `Edit` de hoofdcomponent op de pagina die de hoofdtekst van het bericht bevat.
* Als u het configuratievenster wilt openen, annuleert u de overerving door het pictogram `link` te selecteren.
Nadat de overerving is geannuleerd, is het mogelijk om het configuratiepictogram te selecteren om het configuratiedialoogvenster te openen.

* Nadat de configuratie is voltooid, moet de overerving worden hersteld door het pictogram `broken link` te selecteren.

![ config-compose-bericht ](assets/config-compose-message.png)

#### Het tabblad Basis {#basic-tab-1}

![ basis-lusje-compose ](assets/basic-tab-compose.png)

* **Redirect URL**

  Voer de URL in van de pagina die wordt weergegeven nadat het bericht is verzonden. Bijvoorbeeld `../messaging.html` .

* **annuleert URL**

  Voer de URL van de weergegeven pagina in als de afzender het bericht annuleert. Bijvoorbeeld `../messaging.html` .

* **Maximale lengte van Onderwerp van het Bericht**

  Het maximum aantal tekens dat is toegestaan in het veld Onderwerp. Bijvoorbeeld 500. Standaard is geen limiet.

* **Maximale lengte van het Lichaam van het Bericht**

  Het maximum aantal tekens dat is toegestaan in het veld Inhoud. Bijvoorbeeld 10000. Standaard is geen limiet.

* **de selecteur van de Dienst**

  (*Vereiste*) reeks dit aan de waarde van het bezit **`serviceSelector.name`** van de [ Dienst van de Verrichtingen van het Overseinen van AEM Communities ](/help/communities/messaging.md#messaging-operations-service).

#### Tabblad Weergave {#display-tab-1}

![ vertoning-lusje-compose ](assets/display-tab-compose.png)

* **toon Onderwerpgebied**

  Als deze optie is ingeschakeld, geeft u het veld `Subject` weer en schakelt u het toevoegen van een onderwerp aan het bericht in. Standaard is niet ingeschakeld.

* **Etiket van het Onderwerp**

  Voer de tekst in die u naast het veld `Subject` wilt weergeven. De standaardwaarde is `Subject` .

* **toon het Gebied van het Dossier van de Band**

  Als deze optie is ingeschakeld, geeft u het veld `Attachment` weer en schakelt u het toevoegen van bestandsbijlagen aan het bericht in. Standaard is niet ingeschakeld.

* **Band het Etiket van het Dossier**

  Voer de tekst in die u naast het veld `Attachment` wilt weergeven. De standaardwaarde is **`Attach File`** .

* **toon het Gebied van de Inhoud**

  Als deze optie is ingeschakeld, geeft u het veld `Content` weer en schakelt u het toevoegen van een berichttekst in. Standaard is niet ingeschakeld.

* **Etiket van de Inhoud**

  Voer de tekst in die u naast het veld `Content` wilt weergeven. De standaardwaarde is **`Body`** .

* **met Rich Text Editor**

  Als deze optie is ingeschakeld, wordt het gebruik van een tekstvak met aangepaste inhoud met een eigen RTF-editor aangegeven. Standaard is niet ingeschakeld.

* **de patronen van de tijdstempel**

  Geef tijdstempelpatronen op voor een of meer talen. Standaard is dit voor en, de, fr, it, es, ja, zh_CN, ko_KR.
