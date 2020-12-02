---
title: Abonnementen beheren
seo-title: Abonnementen beheren
description: Gebruikers kunnen worden gevraagd zich in te schrijven op de mailinglijsten van de e-mailprovider met de hulp van de formuliercomponent die op een AEM webpagina wordt gebruikt. Als u een AEM pagina met een aanmeldingsformulier wilt voorbereiden voor een abonnement op de mailinglijsten van uw e-mailservice, moet u de bijbehorende serviceconfiguratie toepassen op de AEM pagina die de potentiële abonnee zal bezoeken.
seo-description: Gebruikers kunnen worden gevraagd zich in te schrijven op de mailinglijsten van de e-mailprovider met de hulp van de formuliercomponent die op een AEM webpagina wordt gebruikt. Als u een AEM pagina met een aanmeldingsformulier wilt voorbereiden voor een abonnement op de mailinglijsten van uw e-mailservice, moet u de bijbehorende serviceconfiguratie toepassen op de AEM pagina die de potentiële abonnee zal bezoeken.
uuid: b2578a3d-dba1-4114-b21a-5f34c0cccc5a
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: personalization
content-type: reference
discoiquuid: 295cb0a6-29db-42aa-824e-9141b37b5086
translation-type: tm+mt
source-git-commit: a3c303d4e3a85e1b2e794bec2006c335056309fb
workflow-type: tm+mt
source-wordcount: '977'
ht-degree: 0%

---


# Abonnementen{#managing-subscriptions} beheren

>[!NOTE]
>
>Adobe is niet van plan deze mogelijkheid verder te verbeteren (Leads en lijsten beheren).
>De aanbeveling is om Adobe Campaign en zijn AEM integratie te benutten.[](/help/sites-administering/campaign.md)

Gebruikers kunnen worden gevraagd zich in te schrijven op **mailinglijsten van de e-mailserviceprovider** met behulp van de **Form**-component die op een AEM webpagina wordt gebruikt. Als u een AEM pagina met een aanmeldingsformulier wilt voorbereiden voor een abonnement op de mailinglijsten van uw e-mailservice, moet u de bijbehorende serviceconfiguratie toepassen op de AEM pagina die de potentiële abonnee zal bezoeken.

## Configuratie van e-mailservice toepassen op een pagina {#applying-email-service-configuration-to-a-page}

Een AEM pagina configureren:

1. Navigeer naar het tabblad **Websites**.
1. Selecteer de pagina die voor de dienst moet worden gevormd. Klik met de rechtermuisknop op de pagina en selecteer **Eigenschappen**.

1. Selecteer **Cloud Services** dan **Service toevoegen**. Selecteer een configuratie in de lijst met beschikbare configuraties.

   ![chlimage_1-164](assets/chlimage_1-164.png)

1. Klik **OK**.

## Een aanmeldingsformulier op een AEM pagina maken voor het abonneren/opzeggen op lijsten {#creating-a-sign-up-form-on-an-aem-page-for-subscribing-unsubscribing-to-lists}

Een aanmeldingsformulier maken en dit configureren voor abonnementen op de mailinglijsten van de e-mailprovider:

1. Open de AEM pagina die de gebruiker zal bezoeken.
1. Pas de configuratie van de E-mailserviceprovider toe op de pagina.

1. Voeg een **Form** component aan de pagina toe door de component van sidekick te slepen. Als de component niet beschikbaar is, schakelt u over naar de ontwerpmodus en schakelt u de groep **Form** in.
1. Klik op **Bewerken** in de **Begin van formulier** balk en navigeer naar het tabblad **Geavanceerd**.
1. Selecteer **E-mailservice in het vervolgkeuzemenu** Form **: Abonnee** maken en toevoegen aan lijst.
1. Open onder aan het dialoogvenster de vervolgkeuzelijst **Actieconfiguratie**, waarmee u een of meer abonnementslijsten kunt selecteren.
1. Selecteer in **Selecteer lijst** de lijst waarop gebruikers zich moeten abonneren. U kunt veelvoudige lijsten toevoegen door de plus knoop (**Voeg Punt** toe) te gebruiken.

   ![chlimage_1-10](assets/chlimage_1-10.jpeg)

   >[!NOTE]
   >
   >Het dialoogvenster kan afwijken, afhankelijk van het e-mailservicebureau.

1. Selecteer op het tabblad **Formulier** de pagina Bedankt waarnaar gebruikers moeten gaan nadat ze het formulier hebben verzonden (Als het formulier leeg blijft, wordt het formulier na verzending opnieuw weergegeven.) Klik **OK**. Er verschijnt een **E-mailadres**-component in het formulier. Hiermee kunt u een formulier maken waarin gebruikers hun e-mailadres kunnen verzenden voor een abonnement of voor het afmelden van een mailinglijst.
1. Voeg de knopcomponent **Submit** toe uit de sectie **Form** in sidekick.

   Het formulier is klaar. Publiceer de pagina die in de bovenstaande stappen wordt gevormd samen met **dank u** pagina aan het publicatieexemplaar. Eventuele abonnees die de pagina bezoeken, kunnen het formulier invullen en zich abonneren op de lijst in de configuratie.

   >[!NOTE]
   >
   >Als u het formulierabonnement op de juiste wijze wilt laten functioneren, moeten [coderingssleutels van de auteur worden geëxporteerd en geïmporteerd in het publicatieexemplaar](#exporting-keys-from-author-and-importing-on-publish).

## Toetsen van auteur exporteren en importeren bij publicatie {#exporting-keys-from-author-and-importing-on-publish}

Als u wilt dat e-mailservices zich abonneren en zich niet meer abonneren op het publicatieexemplaar, moet u de volgende stappen uitvoeren:

1. Navigeer in de auteurinstantie naar Package Manager.
1. Maak een nieuw pakket. Stel het filter in op `/etc/key`.
1. Het pakket maken en downloaden.
1. Navigeer naar Package Manager op de publicatie-instantie en upload dit pakket.
1. Navigeer naar de publicatieconsole en start de bundel met de naam **Adobe granite Crypto Support** opnieuw.

## Gebruikers afmelden van lijsten {#unsubscribing-users-from-lists}

Gebruikers afmelden bij lijsten:

1. Open de pagina-eigenschappen van de AEM pagina met het aanmeldingsformulier om het abonnement op een lead op te zeggen.
1. Pas de de dienstconfiguratie op de pagina toe.
1. Maak een aanmeldingsformulier op de pagina.
1. Selecteer tijdens het configureren van de component de handeling **E-mailservice**: **Abonnement voor gebruiker opzeggen uit lijst.**
1. Selecteer in het keuzemenu de lijst waaruit de gebruiker bij het afmelden wordt verwijderd.

   ![chlimage_1-11](assets/chlimage_1-11.jpeg)

1. Exporteer de sleutels van de auteur om te publiceren.

## E-mails met automatische beantwoorders configureren voor e-mailservice {#configuring-auto-responder-emails-for-email-service}

Om een auto-antwoordapparaat e-mail voor een abonnee te vormen:

1. Open de pagina-eigenschappen van de AEM pagina die het aanmeldingsformulier hebben om auto responder voor een lead te configureren.
1. Pas de configuratie ExactTarget op de pagina toe.

1. Voeg een **Form** component aan de pagina toe door de component van sidekick te slepen. Als de component niet beschikbaar is, schakelt u over naar de ontwerpmodus en schakelt u de groep **Form** in.
1. Klik op **Bewerken** in de **Begin van formulier** balk en navigeer naar het tabblad **Geavanceerd**.
1. Selecteer **E-mailservice in het vervolgkeuzemenu** Form **: E-mail met automatische beantwoorder verzenden.**
1. **Selecteer een e-mail**  (dit is de e-mail die als auto-antwoordapparaat wordt verzonden).

1. **Selecteer Classificatie**  (deze indeling wordt gebruikt om het e-mailbericht te verzenden).
1. Selecteer de pagina **Bedankt** (de pagina waarnaar gebruikers worden geleid wanneer ze het formulier verzenden).

   Selecteer op het tabblad **Formulier** de pagina Bedankt waarnaar gebruikers moeten gaan nadat ze het formulier hebben verzonden. (Als het formulier leeg blijft, wordt het opnieuw weergegeven bij verzending.) Klik **OK**.

1. Exporteer de sleutels van de auteur om te publiceren.
1. Voeg de knopcomponent **Submit** toe uit de sectie **Form** in sidekick.

   Het aanmeldingsformulier is klaar. Publiceer de pagina die in de bovenstaande stappen wordt gevormd samen met **dank u** pagina aan het publicatieexemplaar. Eventuele abonnees die de pagina bezoeken, kunnen het formulier invullen en bij het verzenden van het formulier ontvangt de bezoeker een e-mail met de automatische beantwoorder op de in het formulier ingevulde e-mail.

   >[!NOTE]
   >
   >Als u het abonnement op het formulier voor aanmelding correct wilt laten werken, moet u [coderingssleutels van de auteur exporteren en importeren in de publicatieversie](#exporting-keys-from-author-and-importing-on-publish).

   ![chlimage_1-12](assets/chlimage_1-12.jpeg)

