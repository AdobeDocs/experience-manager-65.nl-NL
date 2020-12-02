---
title: Berichtenonderdeel
seo-title: Berichtenonderdeel
description: Het vormen van de componenten van het Overseinen
seo-description: Het vormen van de componenten van het Overseinen
uuid: 8b99ded1-aec2-40c9-82d5-e2e404f614ca
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: authoring
content-type: reference
discoiquuid: 9d952604-f9ef-498f-937b-871817c80226
docset: aem65
translation-type: tm+mt
source-git-commit: f375b40c084ee363757b78c602091f38524b8b03
workflow-type: tm+mt
source-wordcount: '932'
ht-degree: 0%

---


# Berichtenonderdeel {#messaging-feature}

Naast de openbaar zichtbare interacties die in forums en commentaren voorkomen, laat de overseineneigenschap van AEM Communities communityleden toe om met elkaar meer privé in wisselwerking te staan.

Deze functie kan worden opgenomen wanneer een [communitysite](/help/communities/overview.md#communitiessites) wordt gemaakt.

De overseineneigenschap verstrekt de capaciteit om:

**A** - een bericht sturen naar een of meer leden van de community

**B** - directe berichten in  [bulk naar de groepen van leden van de gemeenschap verzenden](/help/communities/messaging.md#group-messaging)

**C** - een bericht met bijlagen verzenden

**D** - een bericht doorsturen

**E** -antwoord op een bericht

**F** - verwijder een bericht

**G** - een verwijderd bericht herstellen

![messaging-section](assets/messaging-section.png)

![herstelbericht](assets/restore-message.png)

Om de overseineneigenschap toe te laten en te wijzigen, zie:

* [Berichten ](/help/communities/messaging.md) voor beheerders configureren
* [Berichtenhoofdzaak ](/help/communities/essentials-messaging.md) voor ontwikkelaars

>[!NOTE]
>
>Het wordt niet ondersteund om `Compose Message, Message, or Message List`-componenten (gevonden in `Communities`componentgroep) toe te voegen aan een pagina in de bewerkingsmodus van de auteur.

## Berichtcomponenten {#configure-messaging-components} configureren

Wanneer het overseinen voor een communautaire plaats wordt toegelaten, wordt het opstelling zonder verdere configuratie noodzakelijk. De informatie wordt verstrekt als er een behoefte is om de standaardconfiguratie te veranderen.

### Berichtlijst configureren (berichtvenster) {#configure-message-list-message-box}

Als u de configuratie wilt wijzigen van de lijst met berichten voor **Inbox**, **Items verzenden** en **Prullenmand** pagina&#39;s van de berichtfunctie, opent u de site in [bewerkingsmodus auteur](/help/communities/sites-console.md#authoring-site-content).

1. In `Preview` wijze, selecteer **Berichten** verbinding om de belangrijkste overseinenpagina te openen. Selecteer vervolgens **Inbox**, **Items verzenden** of **Prullenmand** om de component voor die berichtlijst te configureren.

1. Selecteer in de modus `Edit` de component op de pagina.
1. U opent het configuratiedialoogvenster door overerving te annuleren door het pictogram `link` te selecteren.
Nadat de overerving is geannuleerd, is het mogelijk om het configuratiepictogram te selecteren om het configuratiedialoogvenster te openen.

1. Zodra de configuratie volledig is, is het noodzakelijk om overerving te herstellen door het `broken link` pictogram te selecteren.

![configure-message-list](assets/configure-message-list.png)

#### Standaardtabblad {#basic-tab}

![basic-tab-messagelist](assets/basic-tab-messagelist.png)

* **Servicekiezer**

   (*Required*) plaats dit aan de waarde van het bezit **`serviceSelector.name`** van [de Dienst van de Verrichtingen van het Overseinen van AEM Communities](/help/communities/messaging.md#messaging-operations-service).

* **Pagina samenstellen**

   (*Required*) de pagina om te openen wanneer een lid **`Reply`** knoop klikt. De doelpagina moet het formulier **Compose Message** bevatten.

* **Reageren/weergeven als bron**

   Als deze optie is ingeschakeld, verwijzen de URL van de reactie en de URL van de weergave naar een bron, anders worden gegevens doorgegeven als queryparameters in de URL.

* **Profielweergaveformulier**

   Het profielformulier dat moet worden gebruikt om het afzenderprofiel weer te geven.

* **Prullenmap**

   Als deze optie is ingeschakeld, worden in deze component Berichtlijst alleen berichten weergegeven die zijn gemarkeerd als verwijderd (prullenbak).

* **Mappaden**

   (*Required*) Verwijzen naar de waarden die zijn ingesteld voor **inbox.path.name** en **sentitems.path.name** in [AEM Communities Messaging Operations Service](/help/communities/messaging.md#messaging-operations-service). Wanneer het vormen voor `Inbox`, voeg één ingang toe gebruikend de waarde van **inbox.path.name**. Wanneer het vormen voor `Outbox`, voeg één ingang toe gebruikend de waarde van **sentitems.path.name**. Wanneer het vormen voor `Trash`, voeg twee ingangen met beide waarden toe.

#### Tabblad {#display-tab} weergeven

![display-tab-message-list](assets/display-tab-message-list.png)

* **Knop Markeren als lezen**

   Als deze optie is ingeschakeld, wordt een `Read`knop weergegeven waarmee een bericht kan worden gemarkeerd als gelezen.

* **Knop Markeren als ongelezen**

   Als deze optie is ingeschakeld, wordt een `Mark Unread`-knop weergegeven waarmee een bericht kan worden gemarkeerd als gelezen.

* **Knop Verwijderen**

   Als deze optie is ingeschakeld, wordt een `Delete`-knop weergegeven waarmee een bericht kan worden gemarkeerd als gelezen. Hiermee wordt de verwijderfunctionaliteit gedupliceerd als **`Message Options`** ook is ingeschakeld.

* **Berichtopties**

   Als deze optie is ingeschakeld, worden **`Reply`**, **`Reply All`**, **`Forward`** en **`Delete`** knoppen weergegeven waarmee een bericht kan worden verzonden of verwijderd. Hiermee wordt de verwijderfunctionaliteit gedupliceerd als **`Delete Button`** ook is ingeschakeld.

* **Berichten per pagina**

   Het opgegeven aantal is het maximumaantal berichten dat per pagina in een pagineringsschema wordt weergegeven. Als geen aantal wordt gespecificeerd (verlaten leeg), dan worden alle berichten getoond en er is geen paginering.

* **Tijdstempelpatronen**

   Geef tijdstempelpatronen op voor een of meer talen. Standaard is dit voor en, de, fr, it, es, ja, zh_CN, ko_KR.

* **Gebruiker weergeven**

   Kies **`Sender`** of **`Recipients`** om te bepalen of om de afzender of Ontvangers te tonen.

### Samenstellingsbericht {#configure-compose-message} configureren

Als u de configuratie van de pagina voor samenstellen van berichten wilt wijzigen, opent u de site in de bewerkingsmodus [auteur](/help/communities/sites-console.md#authoring-site-content).

* In `Preview` wijze, selecteer **Berichten** verbinding om de belangrijkste overseinenpagina te openen. Selecteer vervolgens de knop Nieuw bericht om de pagina `Compose Message` te openen.

* Selecteer in de modus `Edit` de hoofdcomponent op de pagina die de hoofdtekst van het bericht bevat.
* U opent het configuratiedialoogvenster door overerving te annuleren door het pictogram `link` te selecteren.
Nadat de overerving is geannuleerd, is het mogelijk om het configuratiepictogram te selecteren om het configuratiedialoogvenster te openen.

* Zodra de configuratie volledig is, is het noodzakelijk om overerving te herstellen door het `broken link` pictogram te selecteren.

![config-compose-bericht](assets/config-compose-message.png)

#### Standaardtabblad {#basic-tab-1}

![basic-tab-compose](assets/basic-tab-compose.png)

* **URL omleiden**

   Voer de URL in van de pagina die wordt weergegeven nadat het bericht is verzonden. Bijvoorbeeld, `../messaging.html`.

* **URL annuleren**

   Voer de URL van de weergegeven pagina in als de afzender het bericht annuleert. Bijvoorbeeld, `../messaging.html`.

* **Maximale lengte van onderwerp van bericht**

   Het maximum aantal tekens dat is toegestaan in het veld Onderwerp. Bijvoorbeeld 500. Standaard is geen limiet.

* **Maximale lengte van berichttekst**

   Het maximum aantal tekens dat is toegestaan in het veld Inhoud. Bijvoorbeeld 10000. Standaard is geen limiet.

* **Servicekiezer**

   (*Required*) plaats dit aan de waarde van het bezit **`serviceSelector.name`** van [de Dienst van de Verrichtingen van het Overseinen van AEM Communities](/help/communities/messaging.md#messaging-operations-service).

#### Tabblad {#display-tab-1} weergeven

![display-tab-compose](assets/display-tab-compose.png)

* **Onderwerpveld tonen**

   Als deze optie is ingeschakeld, geeft u het veld `Subject` weer en schakelt u het toevoegen van een onderwerp aan het bericht in. Standaard is niet ingeschakeld.

* **Onderwerplabel**

   Voer de tekst in die naast het veld `Subject` moet worden weergegeven. De standaardwaarde is `Subject`.

* **Veld Bestand bijvoegen tonen**

   Als deze optie is ingeschakeld, geeft u het veld `Attachment` weer en schakelt u het toevoegen van bestandsbijlagen aan het bericht in. Standaard is niet ingeschakeld.

* **Bestandslabel bijvoegen**

   Voer de tekst in die naast het veld `Attachment` moet worden weergegeven. De standaardwaarde is **`Attach File`**.

* **Inhoudsveld tonen**

   Indien ingeschakeld, toon het `Content` gebied en laat het toevoegen van een berichtlichaam toe. Standaard is niet ingeschakeld.

* **Inhoudslabel**

   Voer de tekst in die naast het veld `Content` moet worden weergegeven. De standaardwaarde is **`Body`**.

* **Met RTF-editor**

   Als deze optie is ingeschakeld, wordt het gebruik van een tekstvak met aangepaste inhoud met een eigen RTF-editor aangegeven. Standaard is niet ingeschakeld.

* **Tijdstempelpatronen**

   Geef tijdstempelpatronen op voor een of meer talen. Standaard is dit voor en, de, fr, it, es, ja, zh_CN, ko_KR.

