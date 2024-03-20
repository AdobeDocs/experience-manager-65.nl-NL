---
title: Abonnementen beheren
description: Gebruikers kunnen worden gevraagd zich in te schrijven op de mailinglijsten van de e-mailprovider met de hulp van de formuliercomponent die op een AEM webpagina wordt gebruikt. Als u een AEM pagina met een aanmeldingsformulier wilt voorbereiden voor een abonnement op de mailinglijsten van uw e-mailservice, moet u de bijbehorende serviceconfiguratie toepassen op de AEM pagina die de potentiële abonnee zal bezoeken.
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: personalization
content-type: reference
exl-id: add05d22-3a11-49e9-a554-2315962552d5
solution: Experience Manager, Experience Manager Sites
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '917'
ht-degree: 0%

---

# Abonnementen beheren{#managing-subscriptions}

>[!NOTE]
>
>De Adobe is niet van plan deze mogelijkheid verder te verbeteren (Leads en lijsten beheren).
>De aanbeveling is om [Adobe Campaign en zijn AEM integratie](/help/sites-administering/campaign.md).

Gebruikers kunnen worden gevraagd zich in te schrijven op **E-mailserviceproviders** mailinglijsten met behulp van de **Formulier** op een AEM webpagina wordt gebruikt. Als u een AEM pagina met een aanmeldingsformulier wilt voorbereiden voor een abonnement op de mailinglijsten van uw e-mailservice, moet u de bijbehorende serviceconfiguratie toepassen op de AEM pagina die de potentiële abonnee zal bezoeken.

## Configuratie van e-mailservice toepassen op een pagina {#applying-email-service-configuration-to-a-page}

Een AEM pagina configureren:

1. Ga naar de **Websites** tab.
1. Selecteer de pagina die voor de dienst moet worden gevormd. Klik met de rechtermuisknop op de pagina en selecteer **Eigenschappen**.

1. Selecteren **Cloud Servicen** dan **Service toevoegen**. Selecteer een configuratie in de lijst met beschikbare configuraties.

   ![chlimage_1-164](assets/chlimage_1-164.png)

1. Klikken **OK**.

## Een aanmeldingsformulier op een AEM pagina maken voor het abonneren of afmelden van lijsten {#creating-a-sign-up-form-on-an-aem-page-for-subscribing-unsubscribing-to-lists}

Een aanmeldingsformulier maken en dit configureren voor abonnementen op de mailinglijsten van de e-mailprovider:

1. Open de AEM pagina die de gebruiker zal bezoeken.
1. Pas de configuratie van de E-mailserviceprovider toe op de pagina.

1. Voeg een **Formulier** naar de pagina door de component van het hulpstuk te slepen. Als de component niet beschikbaar is, schakelt u over naar de ontwerpmodus en schakelt u **Formulier** groep.
1. Klikken **Bewerken** in de **Begin van formulier** en naar de **Geavanceerd** tab.
1. In de **Formulier** vervolgkeuzelijst, selecteert u **E-mailservice: abonnee maken** en toevoegen aan lijst.
1. Open onder aan het dialoogvenster het dialoogvenster **Configuratie van handelingen** vervolgkeuzelijst waarin u een of meer abonnementlijsten kunt selecteren.
1. In de **Lijst selecteren** selecteert u de lijst waarop gebruikers zich moeten abonneren. U kunt meerdere lijsten toevoegen met de plusknop (**Item toevoegen**).

   ![chlimage_1-10](assets/chlimage_1-10.jpeg)

   >[!NOTE]
   >
   >Het dialoogvenster kan afwijken, afhankelijk van het e-mailservicebureau.

1. In de **Formulier** selecteert u de pagina Bedankt waarnaar gebruikers moeten gaan nadat ze het formulier hebben verzonden (Als dit leeg blijft, wordt het formulier na verzending opnieuw weergegeven.) Klikken **OK**. An **E-mailid** wordt weergegeven in het formulier. Hiermee kunt u een formulier maken waarin gebruikers hun e-mailadressen kunnen verzenden om zich te abonneren op een mailinglijst.
1. Voeg de **Verzenden** knopcomponent vanuit de **Formulier** in sidekick.

   Het formulier is klaar. Publiceer de pagina die in de bovenstaande stappen is geconfigureerd samen met de **dank u** pagina naar het publicatieexemplaar. Eventuele abonnees die de pagina bezoeken, kunnen het formulier invullen en zich abonneren op de lijst in de configuratie.

   >[!NOTE]
   >
   >Om het formulierabonnement correct in te stellen, [coderingssleutels van de auteur moeten worden geëxporteerd en geïmporteerd in de publicatie-instantie](#exporting-keys-from-author-and-importing-on-publish).

## Toetsen van auteur exporteren en importeren bij publicatie {#exporting-keys-from-author-and-importing-on-publish}

Als u wilt dat e-mailservices zich abonneren op of zich niet meer abonneren op het publicatieexemplaar, moet u de volgende stappen uitvoeren:

1. Navigeer in de auteurinstantie naar Package Manager.
1. Maak een pakket. Het filter instellen als `/etc/key`.
1. Het pakket maken en downloaden.
1. Navigeer naar Package Manager op de publicatie-instantie en upload dit pakket.
1. Navigeer naar de publicatieconsole en start de bundel met de naam **Adobe Granite Crypto-ondersteuning**.

## Gebruikers afmelden voor lijsten {#unsubscribing-users-from-lists}

Gebruikers afmelden bij lijsten:

1. Open de pagina-eigenschappen van de AEM pagina met het aanmeldingsformulier om het abonnement op een lead op te zeggen.
1. Pas de de dienstconfiguratie op de pagina toe.
1. Maak een aanmeldingsformulier op de pagina.
1. Selecteer de handeling tijdens het configureren van de component **E-mailservice**: **Abonnement op gebruiker opzeggen uit lijst.**
1. Selecteer in het keuzemenu de lijst waaruit de gebruiker bij het afmelden wordt verwijderd.

   ![chlimage_1-11](assets/chlimage_1-11.jpeg)

1. Exporteer de sleutels van de auteur om te publiceren.

## E-mails met automatische beantwoorders configureren voor e-mailservice {#configuring-auto-responder-emails-for-email-service}

Om een auto-antwoordapparaat e-mail voor een abonnee te vormen:

1. Open de pagina-eigenschappen van de AEM pagina die het aanmeldingsformulier hebben om auto responder voor een lead te configureren.
1. Pas de configuratie ExactTarget op de pagina toe.

1. Voeg een **Formulier** naar de pagina door de component van het hulpstuk te slepen. Als de component niet beschikbaar is, schakelt u over naar de ontwerpmodus en schakelt u de **Formulier** groep.
1. Klikken **Bewerken** in de **Begin van formulier** en naar de **Geavanceerd** tab.
1. In de **Formulier** vervolgkeuzelijst, selecteert u **E-mailservice: stuur de e-mail met de automatische beantwoorder.**
1. **Een e-mail selecteren** (Dit is de e-mail die als auto-antwoordapparaat wordt verzonden).

1. **Classificatie selecteren** (deze indeling wordt gebruikt om het e-mailbericht te verzenden).
1. Selecteer de **Bedankt** pagina (de pagina waarnaar gebruikers worden geleid wanneer ze het formulier verzenden).

   In de **Formulier** selecteert u de pagina Bedankt waarnaar gebruikers moeten gaan nadat ze het formulier hebben verzonden. (Als het formulier leeg blijft, wordt het opnieuw weergegeven bij verzending.) Klikken **OK**.

1. Exporteer de sleutels van de auteur om te publiceren.
1. Voeg de **Verzenden** knopcomponent vanuit de **Formulier** in sidekick.

   Het aanmeldingsformulier is klaar. Publiceer de pagina die in de bovenstaande stappen is geconfigureerd samen met de **dank u** pagina naar het publicatieexemplaar. Eventuele abonnees die de pagina bezoeken, kunnen het formulier invullen en bij het verzenden van het formulier ontvangt de bezoeker een e-mail met de automatische beantwoorder op de in het formulier ingevulde e-mail.

   >[!NOTE]
   >
   >Om het abonnement op het formulier correct te laten functioneren, [coderingssleutels van de auteur moeten worden geëxporteerd en geïmporteerd in de publicatie-instantie](#exporting-keys-from-author-and-importing-on-publish).

   ![chlimage_1-12](assets/chlimage_1-12.jpeg)
