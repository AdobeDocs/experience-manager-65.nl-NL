---
title: E-mailmarketing
description: E-mailmarketing (bijvoorbeeld nieuwsbrieven) is een belangrijk onderdeel van elke marketingcampagne die u gebruikt om inhoud naar uw leads te sturen. In AEM kunt u nieuwsbrieven maken op basis van bestaande AEM inhoud en nieuwe inhoud toevoegen die specifiek is voor de nieuwsbrieven.
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: personalization
content-type: reference
docset: aem65
exl-id: a1d8b74e-67eb-4338-9e8e-fd693b1dbd48
solution: Experience Manager, Experience Manager Sites
feature: Authoring,Personalization
role: User
source-git-commit: 305227eff3c0d6414a5ae74bcf3a74309dccdd13
workflow-type: tm+mt
source-wordcount: '1767'
ht-degree: 0%

---


# E-mailmarketing{#e-mail-marketing}

>[!NOTE]
>
>De Adobe is niet van plan het e-mailvolgen van open/grenzen (niet leverbaar) verder te verbeteren die door AEM dienst SMTP worden verzonden.
>Aanbevolen wordt [Adobe Campaign en de integratie in AEM](/help/sites-administering/campaign.md).

E-mailmarketing (bijvoorbeeld nieuwsbrieven) is een belangrijk onderdeel van elke marketingcampagne die u gebruikt om inhoud naar uw leads te sturen. In AEM kunt u nieuwsbrieven maken op basis van bestaande AEM inhoud en nieuwe inhoud toevoegen die specifiek is voor de nieuwsbrieven.

Nadat u de nieuwsbrieven hebt gemaakt, kunt u deze direct of op een ander gepland tijdstip naar de specifieke groep gebruikers sturen (via een workflow). Bovendien kunnen gebruikers zich abonneren op nieuwsbrieven in de door hen gekozen indeling.

Daarnaast kunt AEM u de functionaliteit voor nieuwsbrieven beheren, waaronder het onderhouden van onderwerpen, het archiveren van nieuwsbrieven en het weergeven van nieuwsbrieven.

>[!NOTE]
>
>In Geometrixx wordt de e-maileditor automatisch geopend in de sjabloon voor nieuwsbrieven. U kunt de e-maileditor in andere sjablonen gebruiken die u e-mailberichten wilt verzenden, bijvoorbeeld in uitnodigingen. De e-maileditor geeft altijd weer wanneer een pagina wordt overgenomen van **mcm/componenten/nieuwsbrief/pagina**.

In dit document worden de basisbeginselen van het maken van nieuwsbrieven in AEM beschreven. Raadpleeg de volgende documenten voor gedetailleerde informatie over het werken met e-mailmarketing:

* [Een effectieve openingspagina voor nieuwsbrieven maken](/help/sites-classic-ui-authoring/classic-personalization-campaigns-email-landingpage.md)
* [Abonnementen beheren](/help/sites-classic-ui-authoring/classic-personalization-campaigns-email-subscriptions.md)
* [E-mail naar e-mailserviceproviders publiceren](/help/sites-classic-ui-authoring/classic-personalization-campaigns-email-newsletters.md)
* [Onbetaalde e-mails bijhouden](/help/sites-classic-ui-authoring/classic-personalization-campaigns-email-tracking-bounces.md)

>[!NOTE]
>
>Als u e-mailproviders bijwerkt, een vliegtest uitvoert of een nieuwsbrief verzendt, mislukken deze bewerkingen als de nieuwsbrief niet eerst naar de instantie Publiceren wordt gepubliceerd of als de instantie Publiceren niet beschikbaar is. Vergeet niet uw nieuwsbrief te publiceren en ervoor te zorgen dat de instantie Publiceren actief is.

## Een nieuwsbrief maken {#creating-a-newsletter-experience}

>[!NOTE]
>
>E-mailmeldingen moeten via de osgi-configuratie worden geconfigureerd. Zie [E-mailmelding configureren.](/help/sites-administering/notification.md)

1. Selecteer uw nieuwe campagne in de linkerruit, of klik het in de juiste ruit tweemaal.

1. Selecteer de lijstweergave met het pictogram:

   ![Pictogram lijstweergave](do-not-localize/mcm_icon_listview-1.png)

1. Klikken **Nieuw...**

   U kunt de **Titel**, **Naam** en type ervaring die moet worden opgedaan; in dit geval Newsletter.

   ![Dialoogvenster Ervaring maken](assets/mcm_createnewsletter.png)

1. Klikken **Maken**.

1. Er wordt direct een nieuw dialoogvenster geopend. Hier kunt u eigenschappen voor de nieuwsbrief ingaan.

   De **Standaardlijst met ontvangers** is een verplicht veld omdat dit het aanraakpunt voor de nieuwsbrief vormt (zie [Werken met lijsten](/help/sites-classic-ui-authoring/classic-personalization-campaigns.md#workingwithlists) voor meer informatie over lijsten).

   ![Dialoogvenster Pagina-eigenschappen](assets/mcm_newnewsletterdialog.png)

   * **Van naam**
Naam die als afzender van nieuwsbrief zou moeten verschijnen.

   * **Van adres**
E-mailadres dat moet worden weergegeven als de afzender van de nieuwsbrief.

   * **Onderwerp**
Onderwerp van de nieuwsbrief.

   * **Reageren op**
E-mailadres dat antwoorden op verzonden nieuwsbrief moet adresseren.

   * **Beschrijving**
Beschrijving van de nieuwsbrief.

   * **Op tijd**
De tijd waarop de nieuwsbrief moet worden verzonden.

   * **Standaardlijst met ontvangers**
Standaardlijst die de nieuwsbrief moet ontvangen.

   Deze kunnen later worden bijgewerkt via de **Eigenschappen...** in.

1. Klikken **OK** opslaan.

## Inhoud toevoegen aan nieuwsbrieven {#adding-content-to-newsletters}

U kunt inhoud, inclusief dynamische inhoud, op dezelfde manier aan uw nieuwsbrief toevoegen als in elke AEM. In Geometrixx, heeft het malplaatje van de Nieuwsbrief bepaalde componenten beschikbaar voor het toevoegen van en het wijzigen van inhoud in nieuwsbrieven.

1. Klik in de MCM op de knop **Campagnes** en dubbelklikt u op de nieuwsbrief waaraan u inhoud wilt toevoegen of bewerken. De nieuwsbrief wordt geopend.

1. Als componenten niet zichtbaar zijn, ga naar de mening van het Ontwerp en laat de noodzakelijke componenten (bijvoorbeeld, de componenten van de Nieuwsbrief) toe alvorens u begint uit te geven.
1. Voer eventueel nieuwe tekst, afbeeldingen of andere componenten in. In het voorbeeld Geometrixx zijn vier componenten beschikbaar: Tekst, Afbeelding, Kop en 2 kolommen. Uw nieuwsbrief kan meer of minder componenten hebben afhankelijk van hoe u het opstelling.

   >[!NOTE]
   >
   >U kunt nieuwsbrieven personaliseren door variabelen te gebruiken. In de nieuwsbrief van de Geometrixx zijn de variabelen beschikbaar in de component van de Tekst. Waarden voor de variabelen worden overgenomen van de gegevens in het gebruikersprofiel.

   ![Inhoud voor nieuwsbrieven bewerken](assets/mcm_newsletter_content.png)

1. Als u variabelen wilt invoegen, selecteert u de variabele in de lijst en klikt u **Invoegen**. Variabelen worden gevuld vanuit het profiel.

## Nieuwsbrieven aanpassen {#personalizing-newsletters}

U kunt nieuwsbrieven personaliseren door vooraf bepaalde variabelen in de component van de Tekst van nieuwsbrieven in Geometrixx op te nemen. Waarden voor de variabelen worden overgenomen van de gegevens in het gebruikersprofiel.

U kunt ook simuleren hoe een nieuwsbrief wordt gepersonaliseerd door de clientcontext te gebruiken en een profiel te laden.

Een nieuwsbrief personaliseren en simuleren hoe het eruit zal zien:

1. Open vanuit de MCM de nieuwsbrief waarvoor u instellingen wilt aanpassen.

1. Open de tekstcomponent die u wilt aanpassen.

1. Plaats de cursor op de gewenste plaats voor de variabele en selecteer een variabele in de vervolgkeuzelijst en klik op **Invoegen**. Doe dit voor zoveel variabelen als nodig en klik op **OK**.

   ![Variabelen toevoegen](assets/mcm_newsletter_variables.png)

1. Als u wilt simuleren hoe de variabele eruitziet wanneer deze wordt verzonden, drukt u op CTRL+ALT+c om de clientcontext te openen en selecteert u **Laden**. Selecteer de gebruiker in de lijst waarvan u het profiel wilt laden en klik op **OK**.

   De gegevens uit het profiel dat u hebt geladen, bevatten de variabelen.

   ![Variabelen testen](assets/mc_newsletter_testvariables.png)

## Nieuwsbrieven testen in verschillende e-mailclients {#testing-newsletters-in-different-e-mail-clients}

>[!NOTE]
>
>Alvorens nieuwsbrieven te verzenden, controleer de configuratie OSGi voor de Verbinding van CQ van de Dag uiterlijk bij `https://localhost:4502/system/console/configMgr`.
>
>De standaardwaarde van de parameter is `localhost:4502` en de bewerking kan niet voltooid zijn als de poort voor de actieve instantie is gewijzigd.

Schakel tussen algemene e-mailclients om te zien hoe uw nieuwsbrief eruit ziet voor uw leads. Standaard wordt uw nieuwsbrief geopend zonder dat een e-mailclient is geselecteerd.

Momenteel kunt u nieuwsbrieven in de volgende e-mailcliënten bekijken:

* Yahoo-mail
* Gmail
* Hotmail
* Thundervogel
* Microsoft Outlook 2007
* Apple Mail

Als u wilt schakelen tussen clients, klikt u op het bijbehorende pictogram om de nieuwsbrief in die e-mailclient weer te geven:

1. Open vanuit de MCM de nieuwsbrief waarvoor u instellingen wilt aanpassen.

1. Klik op een e-mailclient in de bovenste balk om te zien hoe de nieuwsbrief er in die client uitziet.

   ![E-mailclients schakelen](assets/chlimage_1-119.png)

1. Herhaal deze stap voor alle andere e-mailclients die u wilt zien.

   ![E-mailclients wijzigen](assets/chlimage_1-120.png)

## Newsletter-instellingen aanpassen {#customizing-newsletter-settings}

Hoewel alleen geautoriseerde gebruikers een nieuwsbrief kunnen verzenden, dient u het volgende aan te passen:

* De onderwerpregel, zodat gebruikers uw e-mail willen openen en er ook voor zorgen dat uw nieuwsbrief niet als spam wordt gemarkeerd.
* Het adres Van, bijvoorbeeld, `noreply@geometrixx.com`, zodat gebruikers een e-mail van een opgegeven adres ontvangen.

Nieuwsbrieven aanpassen:

1. Open vanuit de MCM de nieuwsbrief waarvoor u instellingen wilt aanpassen.

   ![Een nieuwsbrief openen](assets/mcm_newsletter_open.png)

1. Klik boven aan de nieuwsbrief op **Instellingen**.

   ![Instellingen voor nieuwsbrieven bewerken](assets/mcm_newsletter_settings.png)
1. Voer de **Van** e-mailadres

1. Wijzig de **Onderwerp** van het e-mailbericht, indien nodig.

1. Selecteer een **Standaardlijst met ontvangers** in de vervolgkeuzelijst.

1. Klikken **OK**.

   Wanneer u de nieuwsbrief test of verzendt, zullen de ontvangers e-mail met het gespecificeerde e-mailadres en onderwerp ontvangen.

## Nieuwsbrieven voor vliegtests {#flight-testing-newsletters}

Hoewel het testen van de vlucht niet verplicht is, kunt u het best testen voordat u een nieuwsbrief verstuurt om er zeker van te zijn dat het lijkt zoals u wilt.

Bij het testen van de vlucht kunt u het volgende doen:

* Bekijk de nieuwsbrief in [alle beoogde cliënten](#testing-newsletters-in-different-e-mail-clients).
* Controleer of de mailserver op de juiste wijze is ingesteld.
* Bepaal of je e-mail wordt gemarkeerd als spam. (Zorg ervoor dat u uzelf opneemt in de lijst met ontvangers.)

>[!NOTE]
>
>Als u e-mailproviders bijwerkt, een vliegtest uitvoert of een nieuwsbrief verzendt, mislukken deze bewerkingen als de nieuwsbrief niet eerst naar de instantie Publiceren wordt gepubliceerd of als de instantie Publiceren niet beschikbaar is. Vergeet niet uw nieuwsbrief te publiceren en ervoor te zorgen dat de instantie Publiceren actief is.

Voor nieuwsbrieven voor vliegproeven:

1. Open vanuit de MCM de nieuwsbrief die u wilt testen en verzenden.

1. Klik boven aan de nieuwsbrief op **Testen** om te testen voordat u gaat verzenden.

   ![Instellingen om een nieuwsbrief te testen](assets/mcm_newsletter_testsettings.png)

1. Voer het testadres in waarnaar de nieuwsbrief moet worden verzonden en klik op **Verzenden**. Als u het profiel wilt wijzigen, laadt u een ander profiel in de clientcontext. U doet dit door op CTRL+ALT+c te drukken en een profiel laden en laden te selecteren.

## Nieuwsbrieven verzenden {#sending-newsletters}

>[!NOTE]
>
>De Adobe is niet van plan het e-mailvolgen van open/grenzen (niet leverbaar) verder te verbeteren die door AEM dienst SMTP worden verzonden.
>Aanbevolen wordt [Adobe Campaign en de integratie in AEM](/help/sites-administering/campaign.md).

U kunt een nieuwsbrief vanuit de nieuwsbrief of de lijst verzenden. Beide procedures worden beschreven.

>[!NOTE]
>
>Alvorens nieuwsbrieven te verzenden, controleer de configuratie OSGi voor de Verbinding van CQ van de Dag uiterlijk bij `https://localhost:4502/system/console/configMgr`.
>
>De standaardwaarde van de parameter is `localhost:4502` en de bewerking kan niet voltooid zijn als de poort voor de actieve instantie is gewijzigd.

>[!NOTE]
>
>Als u e-mailproviders bijwerkt, een vliegtest uitvoert of een nieuwsbrief verzendt, mislukken deze bewerkingen als de nieuwsbrief niet eerst naar de instantie Publiceren wordt gepubliceerd of als de instantie Publiceren niet beschikbaar is. Vergeet niet uw nieuwsbrief te publiceren en ervoor te zorgen dat de instantie Publiceren actief is.

### Nieuwsbrieven verzenden vanuit een campagne {#sending-newsletters-from-a-campaign}

Een nieuwsbrief sturen vanuit de campagne:

1. Open vanuit de MCM de nieuwsbrief die u wilt verzenden.

   >[!NOTE]
   >
   >Voordat u een nieuwsbrief verzendt, moet u controleren of u het onderwerp van de nieuwsbrief en het oorspronkelijke e-mailadres hebt aangepast door [aanpassen, instellingen](#customizing-newsletter-settings).
   >
   >
   >[Vluchttest](#flight-testing-newsletters) de nieuwsbrief vóór verzending wordt aanbevolen.

1. Klik boven aan de nieuwsbrief op **Verzenden**. De wizard Nieuwsbrief wordt geopend.

1. Selecteer in de lijst met ontvangers de lijst waarop u de nieuwsbrief wilt ontvangen en klik op **Volgende**.

   ![Een nieuwsbrief verzenden](assets/mcm_newslettersend.png)

1. De installatie is voltooid. Klikken **Verzenden** om de nieuwsbrief daadwerkelijk te verzenden.

   ![Bevestiging voor nieuwsbrief verzonden](assets/mcm_newslettersendconfirm.png)

   >[!NOTE]
   >
   >Zorg ervoor dat u een van de ontvangers bent, zodat u zeker weet dat de nieuwsbrief is ontvangen.

### Nieuwsbrieven verzenden vanuit een lijst {#sending-newsletters-from-a-list}

Een nieuwsbrief verzenden vanuit een lijst:

1. Klik in de MCM op **Lijsten** in het linkerdeelvenster.

   >[!NOTE]
   >
   >Voordat u een nieuwsbrief verzendt, moet u controleren of u het onderwerp van de nieuwsbrief en het oorspronkelijke e-mailadres hebt aangepast door [aanpassen, instellingen](#customizing-newsletter-settings). U kunt een nieuwsbrief niet testen als u deze vanuit de lijst verzendt; u kunt [vliegproef](#flight-testing-newsletters) het als u het vanuit de nieuwsbrief verzendt.

1. Schakel het selectievakje in naast de lijst met leads waarnaar u een nieuwsbrief wilt verzenden.

1. In de **Gereedschappen** menu, selecteert u **Nieuwsbrief verzenden**. De **Nieuwsbrief verzenden** wordt geopend.

   ![Newletter-console](assets/mcm_newslettersendfromlist.png)

1. In de **Nieuwsbrief** veld, selecteer de nieuwsbrief die u wilt verzenden en klik op **Volgende**.

   ![Dialoogvenster Nieuwsbrief verzenden](assets/mcm_newslettersenddialog.png)

1. De installatie is voltooid. Klikken **Verzenden** om de geselecteerde nieuwsbrief naar de gespecificeerde lijst van lood te verzenden.

   ![Bevestigen](assets/mcm_newslettersenddialog_confirmation.png)

   Uw nieuwsbrief wordt verzonden naar de geselecteerde ontvangers.

## Abonneren op een nieuwsbrief {#subscribing-to-a-newsletter}

In deze sectie wordt beschreven hoe u zich op een nieuwsbrief kunt abonneren.

### Abonneren op een nieuwsbrief {#subscribing-to-a-newsletter-1}

Abonneren op een nieuwsbrief (de website van de Geometrixx als voorbeeld gebruiken):

1. Klikken **Websites** en navigeer naar de Geometrixx **Werkbalk** en open het.

   ![Voorbeeld van abonnement](assets/chlimage_1-121.png)

1. In de nieuwsbrief Geometrixx **Aanmelden** veld, voer uw e-mailadres in en klik op **Aanmelden**. U bent nu geabonneerd op de nieuwsbrief.
