---
title: Uw Postvak IN
description: U kunt meldingen ontvangen van verschillende AEM, zoals meldingen over werkitems of taken die acties vertegenwoordigen die u moet uitvoeren op pagina-inhoud.
contentOwner: Chris Bohnert
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: introduction
content-type: reference
docset: aem65
exl-id: 52ea2ca2-eb1c-4bed-b52d-feef37c6afd6
solution: Experience Manager, Experience Manager Sites
feature: Authoring
role: User
source-git-commit: a28883778c5e8fb90cbbd0291ded17059ab2ba7e
workflow-type: tm+mt
source-wordcount: '569'
ht-degree: 0%

---

# Uw Postvak IN{#your-inbox}

U kunt meldingen ontvangen van verschillende AEM, zoals meldingen over werkitems of taken die acties vertegenwoordigen die u moet uitvoeren op pagina-inhoud.

U ontvangt deze meldingen in twee Postvakken, die worden gescheiden door het type meldingen:

* In de volgende sectie wordt een postvak weergegeven waarin de meldingen worden weergegeven die u ontvangt als gevolg van abonnementen.
* Een gespecialiseerde inbox voor werkschemapunten wordt beschreven in [ Deelnemend in het ](/help/sites-classic-ui-authoring/classic-workflows-participating.md) document van Werkschema&#39;s.

## Je meldingen bekijken {#viewing-your-notifications}

Om uw meldingen weer te geven:

1. Open het bericht in doos: in de **&#x200B;**&#x200B;console Websites, klik de gebruikersknoop in de hoogste juiste hoek en selecteer **Inbox van het Bericht**.

   ![ screen_shot_2012-02-08at105226am ](assets/screen_shot_2012-02-08at105226am.png)

   >[!NOTE]
   >
   >U kunt de console ook rechtstreeks in uw browser openen, bijvoorbeeld:
   >
   >
   >` https://<host>:<port>/libs/wcm/core/content/inbox.html`

1. Je meldingen worden weergegeven. U kunt desgewenst actie ondernemen:

   * [Abonneren op meldingen](#subscribing-to-notifications)
   * [Je meldingen verwerken](#processing-your-notifications)

   ![ chlimage_1-4 ](assets/chlimage_1-4.jpeg)

## Abonneren op meldingen {#subscribing-to-notifications}

Abonneren op meldingen:

1. Open het bericht in doos: in de **&#x200B;**&#x200B;console Websites, klik de gebruikersknoop in de hoogste juiste hoek en selecteer **Inbox van het Bericht**.

   ![ screen_shot_2012-02-08at105226am-1 ](assets/screen_shot_2012-02-08at105226am-1.png)

   >[!NOTE]
   >
   >U kunt de console ook rechtstreeks in uw browser openen, bijvoorbeeld:
   >
   >
   >`https://<host>:<port>/libs/wcm/core/content/inbox.html`

1. Klik **vormen...** in de upper-left hoek om de configuratiedialoog te openen.

   ![ screen_shot_2012-02-08at111056am ](assets/screen_shot_2012-02-08at111056am.png)

1. Selecteer het berichtkanaal:

   * **Inbox**: de berichten worden getoond in uw AEM Inbox.
   * **E-mail**: de berichten worden gemaild aan het e-mailadres dat in uw gebruikersprofiel wordt bepaald.

   >[!NOTE]
   >
   >Er moeten enkele instellingen zijn geconfigureerd om via e-mail op de hoogte te worden gesteld. Het is ook mogelijk om de e-mailsjabloon aan te passen of een e-mailsjabloon voor een nieuwe taal toe te voegen. Zie [ Vormend E-mailBericht ](/help/sites-administering/notification.md#configuringemailnotification) om e-mailberichten in AEM te vormen.

1. Selecteer de paginahandelingen waarvan u een melding wilt ontvangen:

   * Geactiveerd: wanneer een pagina is geactiveerd.
   * gedeactiveerd: wanneer een pagina is gedeactiveerd.
   * Verwijderd (syndicatie): wanneer een pagina is gerepliceerd met een verwijderactie, dat wil zeggen wanneer een verwijderactie op een pagina wordt gerepliceerd.
Wanneer een pagina wordt geschrapt of bewogen, wordt een schrappingsactie automatisch herhaald: de pagina wordt geschrapt op de broninstantie waar de schrappingsactie werd uitgevoerd en op de bestemmingsinstantie die door de replicatieagenten wordt bepaald.

   * Gewijzigd: wanneer een pagina is gewijzigd.
   * Gemaakt: wanneer een pagina is gemaakt.
   * Verwijderd: wanneer een pagina is verwijderd via de paginaverwijderactie.
   * Uitgerold: wanneer een pagina is uitgerold.

1. Definieer de paden van de pagina&#39;s waarvoor u een melding krijgt:

   * Klik **toevoegen** om een nieuwe rij aan de lijst toe te voegen.
   * Klik de **cel van de Weg** lijst en ga de weg, bijvoorbeeld, `/content/docs` in.

   * Om voor alle pagina&#39;s worden op de hoogte gebracht die tot subtree behoren, plaats **Exact?** aan **Nr**.
Om slechts voor acties op de pagina op de hoogte te worden gebracht die door de weg wordt bepaald, plaats **Exact?** aan **ja**.

   * Om de regel toe te staan, plaats **Regel** aan **toestaat**. Als de reeks aan **ontkent**, wordt de regel ontkend maar niet verwijderd en kan later worden toegestaan.

   Om een definitie te verwijderen, selecteer de rij door een lijstcel te klikken en **Schrapping** te klikken.

1. Klik **O.K.** om de configuratie te bewaren.

## Je meldingen verwerken {#processing-your-notifications}

Als u ervoor hebt gekozen om meldingen te ontvangen in uw AEM Postvak IN, wordt uw postvak IN gevuld met meldingen. U kunt [ uw berichten ](#viewing-your-notifications) bekijken, dan de vereiste berichten selecteren aan:

* Accepteer het door **te klikken goedkeurt**: de waarde in **Gelezen** kolom wordt geplaatst aan **waar**.

* Elimineer het door **Schrapping** te klikken.

![ chlimage_1-5 ](assets/chlimage_1-5.jpeg)
