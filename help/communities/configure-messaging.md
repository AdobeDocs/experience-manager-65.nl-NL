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

Deze functie kan worden opgenomen wanneer een [community-site](/help/communities/overview.md#communitiessites) wordt gemaakt.

De overseineneigenschap laat u het volgende doen:

**A** - een bericht sturen naar een of meer leden van de gemeenschap

**B** - directe berichten verzenden in [bulkgoederen naar groepen die lid zijn van de gemeenschap](/help/communities/messaging.md#group-messaging)

**C** - een bericht met bijlagen verzenden

**D** - een bericht doorsturen

**E** - antwoord op een bericht

**F** - een bericht verwijderen

**G** - verwijderde berichten herstellen

![messaging-section](assets/messaging-section.png)

![herstelbericht](assets/restore-message.png)

Om de overseineneigenschap toe te laten en te wijzigen, zie:

* [Berichten configureren](/help/communities/messaging.md) voor beheerders
* [Grondbeginselen van berichten](/help/communities/essentials-messaging.md) voor ontwikkelaars

>[!NOTE]
>
>Toevoegen wordt niet ondersteund `Compose Message, Message, or Message List` componenten (gevonden in `Communities`(componentgroep) naar een pagina in de bewerkingsmodus van de auteur.

## Berichtcomponenten configureren {#configure-messaging-components}

Wanneer het overseinen voor een communautaire plaats wordt toegelaten, wordt het opstelling zonder verdere configuratie noodzakelijk. De informatie wordt verstrekt als er een behoefte is om de standaardconfiguratie te veranderen.

### Berichtlijst configureren (berichtvenster) {#configure-message-list-message-box}

Om de configuratie van de lijst van berichten te wijzigen voor **Inbox**, **Verzonden items**, en **Prullenbak** pagina&#39;s van de overseineneigenschap, open de plaats in [bewerkingsmodus auteur](/help/communities/sites-console.md#authoring-site-content).

1. In `Preview` in, selecteert u de **Berichten** verbinding om de belangrijkste overseinenpagina te openen. Selecteer vervolgens **Inbox**, **Verzonden items** of **Prullenbak** om de component voor die berichtlijst te vormen.

1. In `Edit` selecteert u de component op de pagina.
1. Als u toegang wilt tot het configuratiedialoogvenster, annuleert u de overerving door het `link` pictogram.
Nadat de overerving is geannuleerd, is het mogelijk om het configuratiepictogram te selecteren om het configuratiedialoogvenster te openen.

1. Zodra de configuratie volledig is, is het noodzakelijk om overerving te herstellen door te selecteren `broken link` pictogram.

![configure-message-list](assets/configure-message-list.png)

#### Het tabblad Basis {#basic-tab}

![basic-tab-messagelist](assets/basic-tab-messagelist.png)

* **Servicekiezer**

  (*Vereist*) Stel deze in op de waarde van de eigenschap **`serviceSelector.name`** van de [AEM Communities Messaging Operations Service](/help/communities/messaging.md#messaging-operations-service).

* **Pagina samenstellen**

  (*Vereist*) De pagina die moet worden geopend wanneer een lid op de knop **`Reply`** knop. De doelpagina moet de **Bericht samenstellen** formulier.

* **Reageren/weergeven als bron**

  Als deze optie is ingeschakeld, verwijzen de URL van de reactie en de URL van de weergave naar een bron, of anders worden gegevens doorgegeven als queryparameters in de URL.

* **Profielweergaveformulier**

  Het profielformulier dat moet worden gebruikt om het afzenderprofiel weer te geven.

* **Prullenmap**

  Als deze optie is ingeschakeld, worden in deze component Berichtlijst alleen berichten weergegeven die zijn gemarkeerd als verwijderd (prullenbak).

* **Mappaden**

  (*Vereist*) Verwijzen naar de waarden die zijn ingesteld voor **inbox.path.name** en **sentitems.path.name** in de [AEM Communities Messaging Operations Service](/help/communities/messaging.md#messaging-operations-service). Wanneer het vormen voor een `Inbox`Voeg één item toe met de waarde van **inbox.path.name**. Wanneer het vormen voor een `Outbox`Voeg één item toe met de waarde van **sentitems.path.name**. Wanneer het vormen voor `Trash`Voeg twee items met beide waarden toe.

#### Tabblad Weergave {#display-tab}

![display-tab-message-list](assets/display-tab-message-list.png)

* **Knop Markeren als lezen**

  Als deze optie is ingeschakeld, wordt een `Read`knop waarmee een bericht kan worden gemarkeerd als gelezen.

* **Knop Markeren als ongelezen**

  Als deze optie is ingeschakeld, wordt een `Mark Unread` knop waarmee een bericht kan worden gemarkeerd als gelezen.

* **Knop Verwijderen**

  Als deze optie is ingeschakeld, wordt een `Delete` knop waarmee een bericht kan worden gemarkeerd als gelezen. Hiermee wordt de verwijderfunctie gedupliceerd als **`Message Options`** wordt ook gecontroleerd.

* **Berichtopties**

  Indien ingeschakeld, wordt weergegeven **`Reply`**, **`Reply All`**, **`Forward`**, en **`Delete`** knoppen waarmee een bericht kan worden weergegeven of verwijderd. Hiermee wordt de verwijderfunctie gedupliceerd als **`Delete Button`** wordt ook gecontroleerd.

* **Berichten per pagina**

  Het opgegeven aantal is het maximumaantal berichten dat per pagina in een pagineringsschema wordt weergegeven. Als geen aantal wordt gespecificeerd (verlaten leeg), dan worden alle berichten getoond en er is geen paginering.

* **Tijdstempelpatronen**

  Geef tijdstempelpatronen op voor een of meer talen. Standaard is dit voor en, de, fr, it, es, ja, zh_CN, ko_KR.

* **Gebruiker weergeven**

  Kies **`Sender`** of **`Recipients`** zodat kunt u bepalen of u de afzender of de Ontvangers wilt weergeven.

### Samenstellingsbericht configureren {#configure-compose-message}

Als u de configuratie van de pagina voor samenstellen van berichten wilt wijzigen, opent u de site in [bewerkingsmodus auteur](/help/communities/sites-console.md#authoring-site-content).

* In `Preview` in, selecteert u de **Berichten** verbinding om de belangrijkste overseinenpagina te openen. Selecteer vervolgens de knop Nieuw bericht om het dialoogvenster `Compose Message` pagina.

* In `Edit` Selecteer in de modus de hoofdcomponent op de pagina die de berichttekst bevat.
* Als u het configuratievenster wilt openen, annuleert u de overerving door de optie `link` pictogram.
Nadat de overerving is geannuleerd, is het mogelijk om het configuratiepictogram te selecteren om het configuratiedialoogvenster te openen.

* Zodra de configuratie volledig is, is het noodzakelijk om overerving te herstellen door te selecteren `broken link` pictogram.

![config-compose-bericht](assets/config-compose-message.png)

#### Het tabblad Basis {#basic-tab-1}

![basic-tab-compose](assets/basic-tab-compose.png)

* **URL omleiden**

  Voer de URL in van de pagina die wordt weergegeven nadat het bericht is verzonden. Bijvoorbeeld: `../messaging.html`.

* **URL annuleren**

  Voer de URL van de weergegeven pagina in als de afzender het bericht annuleert. Bijvoorbeeld: `../messaging.html`.

* **Maximale lengte van onderwerp van bericht**

  Het maximum aantal tekens dat is toegestaan in het veld Onderwerp. Bijvoorbeeld 500. Standaard is geen limiet.

* **Maximale lengte van berichttekst**

  Het maximum aantal tekens dat is toegestaan in het veld Inhoud. Bijvoorbeeld 10000. Standaard is geen limiet.

* **Servicekiezer**

  (*Vereist*) Stel deze in op de waarde van de eigenschap **`serviceSelector.name`** van de [AEM Communities Messaging Operations Service](/help/communities/messaging.md#messaging-operations-service).

#### Tabblad Weergave {#display-tab-1}

![display-tab-compose](assets/display-tab-compose.png)

* **Onderwerpveld tonen**

  Indien ingeschakeld, geeft u de optie `Subject` en schakelt u het toevoegen van een onderwerp aan het bericht in. Standaard is niet ingeschakeld.

* **Onderwerplabel**

  Voer de tekst in die u naast de knop `Subject` veld. Standaard is `Subject`.

* **Veld Bestand bijvoegen tonen**

  Indien ingeschakeld, geeft u de optie `Attachment` en schakel het toevoegen van bestandsbijlagen aan het bericht in. Standaard is niet ingeschakeld.

* **Bestandslabel bijvoegen**

  Voer de tekst in die u naast de knop `Attachment` veld. Standaard is **`Attach File`**.

* **Inhoudsveld tonen**

  Indien ingeschakeld, geeft u de optie `Content` en schakelt u het toevoegen van een berichttekst in. Standaard is niet ingeschakeld.

* **Content Label**

  Voer de tekst in die u naast de knop `Content` veld. Standaard is **`Body`**.

* **Met RTF-editor**

  Als deze optie is ingeschakeld, wordt het gebruik van een tekstvak met aangepaste inhoud met een eigen RTF-editor aangegeven. Standaard is niet ingeschakeld.

* **Tijdstempelpatronen**

  Geef tijdstempelpatronen op voor een of meer talen. Standaard is dit voor en, de, fr, it, es, ja, zh_CN, ko_KR.
