---
title: Voorkomen van CSRF-aanvallen
description: Leer hoe te om de aanvallen van de dwars-plaats verzoekvervalsing (CSRF) te verhinderen en gebruikersgegevens te beschermen worden gecompromitteerd.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_user_management
products: SG_EXPERIENCEMANAGER/6.5/FORMS
exl-id: e17fc114-eba5-4e1b-8e70-ad6af7008018
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms,Document Security
role: User, Developer
source-git-commit: d7b9e947503df58435b3fee85a92d51fae8c1d2d
workflow-type: tm+mt
source-wordcount: '955'
ht-degree: 0%

---

# Voorkomen van CSRF-aanvallen {#preventing-csrf-attacks}

## Hoe CSRF-aanvallen werken {#how-csrf-attacks-work}

Corsite request forgery (CSRF) is een kwetsbaarheid op een website waarbij de browser van een geldige gebruiker wordt gebruikt om een kwaadaardig verzoek te verzenden, mogelijk via een iFrame. Omdat de browser cookies op domeinbasis verzendt, kunnen de gegevens van de gebruiker in gevaar worden gebracht als de gebruiker is aangemeld bij een toepassing.

Neem bijvoorbeeld een scenario waarin u bent aangemeld bij de beheerconsole in een browser. U ontvangt een e-mailbericht met een koppeling. Klik op de koppeling om een nieuw tabblad in uw browser te openen. De pagina die u hebt geopend, bevat een verborgen iFrame die een kwaadaardig verzoek doet aan de Forms Server met behulp van het cookie van uw geverifieerde AEM formuliersessie. Omdat Gebruikersbeheer een geldig cookie ontvangt, geeft het de aanvraag door.

## Aan het CSRF gerelateerde termen {#csrf-related-terms}

**Verwijzing:** het adres van de bronpagina waarvan een verzoek komt. Een webpagina op site1.com bevat bijvoorbeeld een koppeling naar site2.com. Als u op de koppeling klikt, wordt een verzoek naar site2.com geplaatst. De referentie van dit verzoek is site1.com, omdat het verzoek is gedaan van een pagina waarvan de bron site1.com is.

**Gevoegde op lijst van gewenste personen URIs:** URIs identificeert middelen op de Server van Forms die, bijvoorbeeld, /adminui of /contentSpace worden gevraagd. Sommige middelen kunnen een verzoek toestaan om de toepassing van externe plaatsen in te gaan. Deze middelen worden beschouwd als op de lijst met gewenste personen staan URIs. De Forms-server voert nooit een referentiecontrole uit van op de lijst met gewenste personen staan URI&#39;s.

**Null verwijzing:** wanneer u een nieuw browser venster of een lusje opent, dan een adres typt en binnengaat drukt, is de verwijzer ongeldig. Het verzoek is volledig nieuw en niet afkomstig van een bovenliggende webpagina; er is dus geen referentie voor het verzoek. De Forms-server kan een null-referentie ontvangen van:

* verzoeken betreffende SOAP of REST-eindpunten van Acrobat
* om het even welke Desktopcliënt die een HTTP- verzoek op een AEM vormen SOAP of REST eindpunt indienen
* wanneer een nieuw browservenster wordt geopend en de URL voor elke aanmeldingspagina van AEM webtoepassing wordt ingevoerd

Een null-referentie op SOAP- en REST-eindpunten toestaan. Sta ook een ongeldige verwijzer op alle login van URI pagina&#39;s zoals /adminui en /contentSpace en hun overeenkomstige in kaart gebrachte middelen toe. Bijvoorbeeld, in kaart gebrachte servlet voor /contentSpace is /contentspace/faces/jsp/login.jsp, die een ongeldige verwijzingsuitzondering zou moeten zijn. Deze uitzondering is alleen vereist als u het filteren van GET voor uw webtoepassing inschakelt. Uw toepassingen kunnen specificeren of om ongeldige verwijzers toe te staan. Zie &quot;Beschermend tegen de aanvallen van de smeedmachine van het Verzoek van de Verhaal van de Deite&quot;in [ Verharding en Veiligheid voor AEM vormen ](https://help.adobe.com/en_US/livecycle/11.0/HardeningSecurity/index.html).

**Toegestane Uitzondering Referrer:** Toegestane Uitzondering Referrer is een sublist van de lijst van toegestane verwijzingen, waarvan de verzoeken worden geblokkeerd. Uitzonderingen voor toegestane verwijzingen zijn specifiek voor een webtoepassing. Als een subset van de toegestane referenties een bepaalde webtoepassing niet mag aanroepen, kunt u de referenties lijsten van gewezen personen door middel van toegestane uitzonderingen Referrer. Uitzonderingen voor toegestane verwijzingen worden opgegeven in het bestand web.xml voor uw toepassing. (Zie &quot;Beveiliging tegen aanvallen van Svervalsingen voor aanvragen van andere sites&quot; in Verharding en beveiliging voor AEM formulieren op de pagina Help en Tutorials.)

## Hoe toegelaten verwijzers werken {#how-allowed-referers-work}

AEM Forms verstrekt verwijzende filtreren, die kan helpen aanvallen CSRF verhinderen. Hieronder wordt beschreven hoe het filteren van referenties werkt:

1. De Forms-server controleert de HTTP-methode die wordt gebruikt voor oproepen:

   * Als het POST is, voert de Server van Forms de verwijzende kopbalcontrole uit.
   * Als het GET is, overslaat de Server van Forms de verwijzingscontrole, tenzij CSRF_CHECK_GETS aan waar wordt geplaatst, in welk geval het de verwijzende kopbalcontrole uitvoert. CSRF_CHECK_GETS wordt gespecificeerd in het web.xml- dossier voor uw toepassing. (Zie &quot;Beveiliging tegen de aanvallen van de Versmeedmachine van het Verzoek van de Depositoverkeer&quot;in [ het Verharden en gids van de Veiligheid ](https://help.adobe.com/en_US/livecycle/11.0/HardeningSecurity/index.html).)

1. De Forms-server controleert of de aangevraagde URI is gevoegd op lijst van gewenste personen:

   * Als URI wordt gevoegd op lijst van gewenste personen, geeft de server de aanvraag door.
   * Als gevraagde URI niet wordt gevoegd op lijst van gewenste personen, wint de server de verwijzer van het verzoek terug.

1. Als er een referentie in het verzoek is, controleert de server of het een toegestane referentie is. Als dit is toegestaan, controleert de server op een verwijzingsuitzondering:

   * Als het een uitzondering is, wordt het verzoek geblokkeerd.
   * Als het geen uitzondering is, wordt het verzoek overgegaan.

1. Als er geen verwijzer in het verzoek is, controleert de server of een ongeldige verwijzer wordt toegestaan.

   * Als een null-referentie is toegestaan, wordt het verzoek doorgegeven.
   * Als een ongeldige verwijzer niet wordt toegestaan, controleert de server of gevraagde URI een uitzondering voor ongeldige verwijzer is en behandelt het verzoek dienovereenkomstig.

## Toegestane verwijzingen configureren {#configure-allowed-referers}

Wanneer u de Manager van de Configuratie in werking stelt, worden de standaardgastheer en IP adres of de Server van Forms toegevoegd aan de Toegestane lijst van de Referentie. U kunt deze lijst bewerken in de beheerconsole.

1. Klik in de beheerconsole op Instellingen > Gebruikersbeheer > Configuratie > URL&#39;s van toegestane referenties configureren. De lijst Toegestane verwijzing wordt onder aan de pagina weergegeven.
1. Een toegestane referentie toevoegen:

   * Typ een hostnaam of IP-adres in het vak Toegestane referenties. Om meer dan één toegestane verwijzer tegelijkertijd toe te voegen, typ elke gastheernaam of IP adres op een nieuwe lijn.
   * Geef in de vakken HTTP-poort en HTTPS-poort op welke poorten HTTP, HTTPS of beide moeten worden toegestaan. Als u deze vakken leeg laat, worden de standaardpoorten (poort 80 voor HTTP en poort 443 voor HTTPS) gebruikt. Als u `0` (nul) in de vakjes ingaat, worden alle havens op die server toegelaten. U kunt ook een specifiek poortnummer invoeren om alleen die poort in te schakelen.
   * Klik toevoegen.

1. Als u een item uit de lijst Toegestane verwijzing wilt verwijderen, selecteert u het item in de lijst en klikt u op Verwijderen.

   Als de Toegestane Lijst van de Referentie leeg is, houdt de eigenschap CSRF op werkend en het systeem wordt onveilig.

1. Nadat u de lijst Toegestane verwijzing hebt gewijzigd, start u de AEM Forms-server opnieuw.
