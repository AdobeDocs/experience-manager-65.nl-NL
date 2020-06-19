---
title: Voorkomen van CSRF-aanvallen
seo-title: Voorkomen van CSRF-aanvallen
description: Leer hoe te om de aanvallen van de dwars-plaats verzoekvervalsing (CSRF) te verhinderen en gebruikersgegevens te beschermen worden gecompromitteerd.
seo-description: Leer hoe te om de aanvallen van de dwars-plaats verzoekvervalsing (CSRF) te verhinderen en gebruikersgegevens te beschermen worden gecompromitteerd.
uuid: f3553826-f5eb-40ea-aeb7-90e4ad30598c
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_user_management
products: SG_EXPERIENCEMANAGER/6.5/FORMS
discoiquuid: a3cbffb7-c1d1-47c2-bcfd-70f1e2d81ac9
translation-type: tm+mt
source-git-commit: b703c59d7d913fc890c713c6e49e7d89211fd998
workflow-type: tm+mt
source-wordcount: '990'
ht-degree: 0%

---


# Voorkomen van CSRF-aanvallen {#preventing-csrf-attacks}

## Hoe CSRF-aanvallen werken {#how-csrf-attacks-work}

Corsite request forgery (CSRF) is een website-kwetsbaarheid waarbij een geldige browser van een gebruiker wordt gebruikt om een kwaadaardig verzoek te verzenden, mogelijk via een iFrame. Omdat de browser cookies op domeinbasis verzendt, kunnen de gegevens van de gebruiker in gevaar worden gebracht als de gebruiker momenteel is aangemeld bij een toepassing.

Neem bijvoorbeeld een scenario waarin u bent aangemeld bij de beheerconsole in een browser. U ontvangt een e-mailbericht met een koppeling. Klik op de koppeling om een nieuw tabblad in uw browser te openen. De pagina die u hebt geopend, bevat een verborgen iFrame die een kwaadaardig verzoek aan de formulierserver doet met behulp van het cookie van uw geverifieerde AEM-formuliersessie. Omdat Gebruikersbeheer een geldig cookie ontvangt, geeft het de aanvraag door.

## Aan het CSRF gerelateerde termen {#csrf-related-terms}

**Referentie:** Het adres van de bronpagina van waaruit een verzoek komt. Een webpagina op site1.com bevat bijvoorbeeld een koppeling naar site2.com. Als u op de koppeling klikt, wordt een aanvraag naar site2.com geplaatst. De verwijzer van dit verzoek is site1.com omdat het verzoek van een pagina wordt gemaakt de waarvan bron site1.com is.

**Toegestane URI&#39;s:** URI&#39;s identificeren bronnen op de formulierserver die worden aangevraagd, bijvoorbeeld /adminui of /contentSpace. Sommige middelen kunnen een verzoek toestaan om de toepassing van externe plaatsen in te gaan. Deze bronnen worden beschouwd als toegestane URI&#39;s. De formulierserver voert nooit een referentiecontrole uit vanuit toegestane URI&#39;s.

**Null-referentie:** Wanneer u een nieuw browservenster of tabblad opent, typt u een adres en drukt u op Enter. De referentie is dan null. Het verzoek is geheel nieuw en niet afkomstig van een bovenliggende webpagina. er is derhalve geen verwijzing naar het verzoek . De formulierserver kan een null-referentie ontvangen van:

* verzoeken die zijn gedaan op SOAP- of REST-eindpunten van Acrobat
* om het even welke Desktopcliënt die een HTTP- verzoek op een AEM vormt ZEEP of REST eindpunt
* wanneer een nieuw browservenster wordt geopend en de URL voor elke aanmeldingspagina van de webtoepassing voor AEM-formulieren wordt ingevoerd

Een null-referentie op de eindpunten SOAP en REST toestaan. Sta ook een ongeldige verwijzer op alle login van URI pagina&#39;s zoals /adminui en /contentSpace en hun overeenkomstige in kaart gebrachte middelen toe. Bijvoorbeeld, in kaart gebrachte servlet voor /contentSpace is /contentspace/faces/jsp/login.jsp, die een ongeldige verwijzingsuitzondering zou moeten zijn. Deze uitzondering is alleen vereist als u GET-filtering voor uw webtoepassing inschakelt. Uw toepassingen kunnen specificeren of om ongeldige verwijzers toe te staan. Zie &quot;Beveiligen tegen aanvallen van Smeedraaiingen tussen verschillende sites&quot; in [Verharding en beveiliging voor AEM-formulieren](https://help.adobe.com/en_US/livecycle/11.0/HardeningSecurity/index.html).

**Uitzondering toegestane verwijzing:** De toegestane Uitzondering van de Verwijzing is sublist van de lijst van toegestane verwijzers, waarvan de verzoeken worden geblokkeerd. Uitzonderingen voor toegestane verwijzingen zijn specifiek voor een webtoepassing. Als een subset van de toegestane referenties een bepaalde webtoepassing niet mag aanroepen, kunt u de referenties blokkeren via de toegestane uitzonderingen van de verwijzer. Uitzonderingen voor toegestane verwijzingen worden opgegeven in het bestand web.xml voor uw toepassing. (Zie &quot;Beveiligen tegen aanvallen van Svervalsingen voor verzoeken van andere sites&quot; in Hardening en beveiliging voor AEM-formulieren op de pagina Help en zelfstudies.)

## Hoe toegestaan werken referentie? {#how-allowed-referers-work}

De vormen van AEM verstrekken verwijzingsfiltreren, die aanvallen kunnen helpen CSRF verhinderen. Hieronder wordt beschreven hoe het filteren van verwijzingen werkt:

1. De formulierserver controleert de HTTP-methode die wordt gebruikt voor oproepen:

   * Als het POST is, voert de formulierserver de controle van de verwijzingskoptekst uit.
   * Als het GET is, overslaat de formulierserver de verwijzingscontrole, tenzij CSRF_CHECK_GETS is ingesteld op true, in welk geval de verwijzingskoptekstcontrole wordt uitgevoerd. CSRF_CHECK_GETS wordt gespecificeerd in het web.xml- dossier voor uw toepassing. (Zie &quot;Beveiliging tegen aanvallen van Svervalsingen van verzoeken voor andere sites&quot; in de handleiding [](https://help.adobe.com/en_US/livecycle/11.0/HardeningSecurity/index.html)Verharding en Beveiliging.)

1. De formulierserver controleert of de aangevraagde URI is toegestaan:

   * Als de URI is toegestaan, geeft de server de aanvraag door.
   * Als de aangevraagde URI niet is toegestaan, haalt de server de referentie van de aanvraag op.

1. Als er een verwijzing in het verzoek is, controleert de server of het een toegelaten verwijzer is. Als dit is toegestaan, controleert de server op een verwijzingsuitzondering:

   * Als het een uitzondering is, wordt het verzoek geblokkeerd.
   * Als het geen uitzondering is, wordt het verzoek overgegaan.

1. Als het verzoek geen verwijzing bevat, controleert de server of een null-verwijzing is toegestaan.

   * Als een null-referentie is toegestaan, wordt het verzoek doorgegeven.
   * Als een ongeldige verwijzer niet wordt toegestaan, controleert de server of gevraagde URI een uitzondering voor ongeldige verwijzer is en behandelt het verzoek dienovereenkomstig.

## Toegestane verwijzingen configureren {#configure-allowed-referers}

Wanneer u Configuration Manager uitvoert, worden de standaardhost en het IP-adres of de formulierserver toegevoegd aan de lijst Toegestane referenties. U kunt deze lijst bewerken in de beheerconsole.

1. Klik in de beheerconsole op Instellingen > Gebruikersbeheer > Configuratie > URL&#39;s van toegestane verwijzing configureren. De lijst Toegestane verwijzing wordt onder aan de pagina weergegeven.
1. Een toegestane verwijzing toevoegen:

   * Typ een hostnaam of IP-adres in het vak Toegestane referenties. Om meer dan één toegestane verwijzer tegelijkertijd toe te voegen, typ elke gastheernaam of IP adres op een nieuwe lijn.
   * Geef in de vakken HTTP-poort en HTTPS-poort op welke poorten HTTP, HTTPS of beide moeten worden toegestaan. Als u deze vakken leeg laat, worden de standaardpoorten (poort 80 voor HTTP en poort 443 voor HTTPS) gebruikt. Als u `0` (nul) invoert in de vakken, worden alle poorten op die server ingeschakeld. U kunt ook een specifiek poortnummer invoeren om alleen die poort in te schakelen.
   * Klik op Toevoegen.

1. Als u een item uit de lijst Toegestane verwijzing wilt verwijderen, selecteert u het item in de lijst en klikt u op Verwijderen.

   Als de Toegestane Lijst van de Verwijzing leeg is, houdt de eigenschap CSRF op werkend en het systeem wordt onveilig.

1. Nadat u de lijst Toegestane verwijzing hebt gewijzigd, start u de AEM-formulierserver opnieuw.

