---
title: Onbetaalde e-mails bijhouden
seo-title: Onbetaalde e-mails bijhouden
description: Wanneer u een nieuwsbrief naar veel gebruikers verzendt, bevat de lijst meestal enkele ongeldige e-mailadressen. Het verzenden van nieuwsbrieven naar die adressen stuitert terug. AEM kan die grenzen beheren en kan ophouden verzendend nieuwsbrieven naar die adressen te verzenden nadat de gevormde stuiterteller wordt overschreden.
seo-description: Wanneer u een nieuwsbrief naar veel gebruikers verzendt, bevat de lijst meestal enkele ongeldige e-mailadressen. Het verzenden van nieuwsbrieven naar die adressen stuitert terug. AEM kan die grenzen beheren en kan ophouden verzendend nieuwsbrieven naar die adressen te verzenden nadat de gevormde stuiterteller wordt overschreden.
uuid: 749959f2-e6f8-465f-9675-132464c65f11
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: personalization
content-type: reference
discoiquuid: fde9027b-9057-48c3-ae34-3f3258c5b371
translation-type: tm+mt
source-git-commit: 016c705230dffec052c200b058a36cdbe0520fc4

---


# Onbetaalde e-mails bijhouden{#tracking-bounced-emails}

>[!NOTE]
>
>Adobe is niet van plan het bijhouden van geopende/verzonden e-mailberichten door de AEM SMTP-service verder te verbeteren.
>
>De aanbeveling is om Adobe Campagne en zijn integratie [van AEM te](/help/sites-administering/campaign.md)gebruiken.

Wanneer u een nieuwsbrief naar veel gebruikers verzendt, bevat de lijst meestal enkele ongeldige e-mailadressen. Het verzenden van nieuwsbrieven naar die adressen stuitert terug. AEM kan die grenzen beheren en kan ophouden verzendend nieuwsbrieven naar die adressen te verzenden nadat de gevormde stuiterteller wordt overschreden. Door gebrek, wordt het stuiterende tarief geplaatst aan 3 maar configureerbaar.

Als u AEM wilt instellen om teruggestuurde e-mailberichten bij te houden, moet u AEM instellen om een bestaande postbus te opiniepeilen waar teruggestuurde e-mails worden ontvangen (dit is meestal het e-mailadres &#39;van&#39; dat u opgeeft waar u de nieuwsbrief verzendt). AEM pollt dit Postvak IN en importeert alle e-mailberichten onder het pad dat is opgegeven in de stemconfiguratie. Een werkschema wordt dan teweeggebracht om naar de verstopte e-mailadressen binnen de gebruikers te zoeken en bijwerkt de bounceCounter bezitswaarde van de gebruiker dienovereenkomstig bij. Nadat de gevormde maximumgrenzen worden overschreden, wordt de gebruiker verwijderd uit de nieuwsbrief lijst.

## De importmodule voor diervoeders configureren {#configuring-the-feed-importer}

Met de importfunctie kunt u herhaaldelijk inhoud uit externe bronnen importeren in uw opslagplaats. Met deze configuratie van de voederimporteur, controleert AEM de brievenbus van de afzender op verbrande e-mails.

De importmodule configureren voor het bijhouden van onaangekondigde e-mails:

1. Selecteer in **Gereedschappen** de importmodule voor diervoeders.

1. Klik op **Toevoegen** om een nieuwe configuratie te maken.

   ![chlimage_1](assets/chlimage_1a.png)

1. Voeg een nieuwe configuratie toe door het type te selecteren en informatie aan de opiniepeiling URL toe te voegen om de gastheer en de haven te vormen. Bovendien moet u wat post en protocol-specifieke parameters aan de vraag toevoegen URL. Stel de configuratie in op minstens eenmaal per dag.

   Alle configuraties hebben informatie nodig over het volgende in de opiniepeiling-URL:

   `username`: De gebruikersnaam die moet worden gebruikt voor verbinding

   `password`: Het wachtwoord dat moet worden gebruikt voor verbinding

   Afhankelijk van het protocol kunt u bovendien bepaalde instellingen configureren.

   **POP3-configuratie-eigenschappen:**

   `pop3.leave.on.server`: Bepaalt of om berichten op server al dan niet te verlaten. Ingesteld op true om berichten op de server te laten, anders false. Heeft als standaardwaarde true.

   **POP3-voorbeelden:**

   | pop3s://pop.gmail.com:995/INBOX?username=user&amp;password=secret | Pop3 via SSL gebruiken om verbinding te maken met GMail op poort 995 met gebruiker/geheim, zodat berichten standaard op de server blijven staan |
   |---|---|
   | pop3s://pop.gmail.com:995/INBOX?username=user&amp;password=secret&amp;pop3.leave.on.server=false | pop3s://pop.gmail.com:995/INBOX?username=user&amp;password=secret&amp;pop3.leave.on.server=false |

   **IMAP-configuratie-eigenschappen:**

   Hiermee kunt u markeringen instellen waarnaar u wilt zoeken.

   `imap.flag.SEEN`:Stel false in voor nieuwe/onzichtbare berichten, true voor al-gelezen berichten

   Zie [https://java.sun.com/products/javamail/javadocs/javax/mail/Flags.Flag.html](https://java.sun.com/products/javamail/javadocs/javax/mail/Flags.Flag.html) voor de volledige lijst met vlaggen.

   **IMAP-voorbeelden:**

   | imaps://imap.gmail.com:993/inbox?username=user&amp;password=secret | Het gebruiken van IMAP over SSL om met GMail op haven 993 met gebruiker/geheim te verbinden. Nieuwe berichten alleen standaard ophalen. |
   |---|---|
   | imaps://imap.gmail.com:993/inbox?username=user&amp;password=secret&amp;imap.flag.SEEN=true | Het gebruiken van IMAP over SSL om met GMail 93 met gebruiker/geheim te verbinden, slechts het krijgen van reeds gezien bericht. |
   | imaps://imap.gmail.com:993/inbox?username=user&amp;password=secret&amp;imap.flag.SEEN=true&amp;imap.flag.SEEN=false | Het gebruiken van IMAP over SSL om met GMail 93 met gebruiker/geheim te verbinden, die reeds wordt gelezen OF nieuwe berichten. |

1. Sla de configuratie op.

## De service-component voor nieuwsbrieven configureren {#configuring-the-newsletter-service-component}

Na het vormen van feed importeur, moet u van adres en stuiterteller vormen.

Om de nieuwsbrief dienst te vormen:

1. In de console OSGi bij `<host>:<port>/system/console/configMgr` en navigeer aan **Bulletin**.

1. Configureer de service en sla de wijzigingen op wanneer u klaar bent.

   ![chlimage_1-1](assets/chlimage_1-1a.png)

   De volgende configuraties kunnen worden ingesteld om het gedrag aan te passen:

   | Maximum voor stuitteller (max.bounce.count) | Bepaalt het aantal grenzen tot een gebruiker zal worden weggelaten wanneer het verzenden van een nieuwsbrief. Als u deze waarde instelt op 0, wordt de stuiteringscontrole volledig uitgeschakeld. |
   |---|---|
   | Activiteit geen cache (sent.activity.nocache) | Definieert de cache-instelling die moet worden gebruikt voor de verzonden activiteit van de nieuwsbrief |

   Zodra bewaard, doet de nieuwsbriefMCM dienst het volgende:

   * Schrijft een activiteit aan de gebruikers verborgen stroom na het succesvol verzenden van een nieuwsbrief.
   * Schrijft een activiteit als een stuit wordt ontdekt en de gebruikers stuiteren tegenveranderingen.
