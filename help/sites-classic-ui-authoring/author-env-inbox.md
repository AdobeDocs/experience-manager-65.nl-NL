---
title: Uw inbox
seo-title: Uw inbox
description: U kunt meldingen ontvangen van verschillende AEM, zoals meldingen over werkitems of taken die acties vertegenwoordigen die u op pagina-inhoud moet uitvoeren.
seo-description: U kunt meldingen ontvangen van verschillende AEM, zoals meldingen over werkitems of taken die acties vertegenwoordigen die u op pagina-inhoud moet uitvoeren.
uuid: e7ba9150-957d-4f84-a570-2f3d83792472
contentOwner: Chris Bohnert
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: introduction
content-type: reference
discoiquuid: ce2a1475-49cf-43e6-bfb9-006884ce3881
docset: aem65
translation-type: tm+mt
source-git-commit: bcb1840d23ae538c183eecb0678b6a75d346aa50
workflow-type: tm+mt
source-wordcount: '611'
ht-degree: 0%

---


# Uw inbox{#your-inbox}

U kunt meldingen ontvangen van verschillende AEM, zoals meldingen over werkitems of taken die acties vertegenwoordigen die u op pagina-inhoud moet uitvoeren.

U ontvangt deze meldingen in twee Postvakken, die worden gescheiden door het type meldingen:

* In de volgende sectie wordt een postvak weergegeven waarin de meldingen worden weergegeven die u ontvangt als gevolg van abonnementen.
* Een gespecialiseerd Postvak IN voor workflowitems wordt beschreven in het document [Deelnemen aan Workflows](/help/sites-classic-ui-authoring/classic-workflows-participating.md).

## Uw meldingen bekijken {#viewing-your-notifications}

Om uw meldingen weer te geven:

1. Open het inbox van de melding: Klik in de **Websites**-console op de gebruikerstoets in de rechterbovenhoek en selecteer **Notification Inbox**.

   ![screen_shot_2012-02-08at105226am](assets/screen_shot_2012-02-08at105226am.png)

   >[!NOTE]
   >
   >U kunt tot de console ook direct in uw browser toegang hebben; bijvoorbeeld:
   >
   >
   >` https://<host>:<port>/libs/wcm/core/content/inbox.html`

1. Je meldingen worden weergegeven. U kunt desgewenst actie ondernemen:

   * [Abonneren op meldingen](#subscribing-to-notifications)
   * [Je meldingen verwerken](#processing-your-notifications)

   ![chlimage_1-4](assets/chlimage_1-4.jpeg)

## Abonneren op meldingen {#subscribing-to-notifications}

Abonneren op meldingen:

1. Open het inbox van de melding: Klik in de **Websites**-console op de gebruikerstoets in de rechterbovenhoek en selecteer **Notification Inbox**.

   ![screen_shot_2012-02-08at105226am-1](assets/screen_shot_2012-02-08at105226am-1.png)

   >[!NOTE]
   >
   >U kunt tot de console ook direct in uw browser toegang hebben; bijvoorbeeld:
   >
   >
   >`https://<host>:<port>/libs/wcm/core/content/inbox.html`

1. Klik **Configureren..** in de linkerbovenhoek om het configuratiedialoogvenster te openen.

   ![screen_shot_2012-02-08at111056am](assets/screen_shot_2012-02-08at111056am.png)

1. Selecteer het berichtkanaal:

   * **Postvak IN**: meldingen worden weergegeven in uw AEM Postvak IN.
   * **E-mail**: meldingen worden per e-mail verzonden naar het e-mailadres dat is gedefinieerd in uw gebruikersprofiel.

   >[!NOTE]
   >
   >U dient enkele instellingen te configureren om via e-mail op de hoogte te worden gesteld. Het is ook mogelijk om de e-mailsjabloon aan te passen of een e-mailsjabloon voor een nieuwe taal toe te voegen. Raadpleeg [E-mailmelding configureren](/help/sites-administering/notification.md#configuringemailnotification) om e-mailmeldingen in AEM te configureren.

1. Selecteer de paginahandelingen waarvan u een melding wilt ontvangen:

   * Geactiveerd: wanneer een pagina is geactiveerd.
   * gedeactiveerd: wanneer een pagina is gedeactiveerd.
   * Verwijderd (syndicatie): wanneer een pagina is verwijderd, dat wil zeggen wanneer een verwijderhandeling die op een pagina is uitgevoerd, wordt gerepliceerd.
Wanneer een pagina wordt verwijderd of verplaatst, wordt automatisch een verwijderactie gerepliceerd: de pagina wordt geschrapt op de broninstantie waar de schrappingsactie werd uitgevoerd en op de bestemmingsinstantie die door de replicatieagenten wordt bepaald.

   * Gewijzigd: wanneer een pagina is gewijzigd.
   * Gemaakt: wanneer een pagina is gemaakt.
   * Verwijderd: wanneer een pagina is verwijderd via de paginaverwijderactie.
   * Uitgelijnd: wanneer een pagina is uitgerold.

1. Definieer de paden van de pagina&#39;s waarvoor u een melding krijgt:

   * Klik **Add** om een nieuwe rij aan de lijst toe te voegen.
   * Klik op de tabelcel **Pad** en voer het pad in, bijvoorbeeld `/content/docs`.

   * Om op de hoogte te worden gesteld voor alle pagina&#39;s die tot de substructuur behoren, plaats **Exact?** naar  **Nee**.
Alleen een melding ontvangen voor handelingen op de pagina die door het pad worden gedefinieerd, stelt u **Exact in?** op  **Ja**.

   * Om de regel toe te staan, plaats **Regel** aan **Allow**. Als de reeks aan **ontkent**, wordt de regel ontkend maar niet verwijderd en kan later worden toegestaan.

   Als u een definitie wilt verwijderen, selecteert u de rij door op een tabelcel te klikken en op **Delete** te klikken.

1. Klik **OK** om de configuratie op te slaan.

## Uw meldingen verwerken {#processing-your-notifications}

Als u ervoor hebt gekozen om meldingen in uw AEM-postvak te ontvangen, vult uw postvak in met meldingen. U kunt uw meldingen [weergeven](#viewing-your-notifications) en vervolgens de gewenste meldingen selecteren voor:

* Goedkeuren door te klikken op **Goedkeuren**: De waarde in de **Read**-kolom wordt ingesteld op **true**.

* Verwijder het door **Delete** te klikken.

![chlimage_1-5](assets/chlimage_1-5.jpeg)
