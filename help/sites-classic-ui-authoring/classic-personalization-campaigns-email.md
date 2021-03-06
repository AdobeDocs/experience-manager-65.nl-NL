---
title: E-mailmarketing
seo-title: E-mailmarketing
description: E-mailmarketing (bijvoorbeeld nieuwsbrieven) is een belangrijk onderdeel van elke marketingcampagne die u gebruikt om inhoud naar uw leads te sturen. In AEM kunt u nieuwsbrieven maken van bestaande AEM inhoud en nieuwe inhoud toevoegen die specifiek is voor de nieuwsbrieven.
seo-description: E-mailmarketing (bijvoorbeeld nieuwsbrieven) is een belangrijk onderdeel van elke marketingcampagne die u gebruikt om inhoud naar uw leads te sturen. In AEM kunt u nieuwsbrieven maken van bestaande AEM inhoud en nieuwe inhoud toevoegen die specifiek is voor de nieuwsbrieven.
uuid: 565943bf-fe37-4d5c-98c3-7c629c4ba264
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: personalization
content-type: reference
discoiquuid: 69ca5acb-83f9-4e1b-9639-ec305779c931
docset: aem65
translation-type: tm+mt
source-git-commit: 016c705230dffec052c200b058a36cdbe0520fc4
workflow-type: tm+mt
source-wordcount: '1803'
ht-degree: 0%

---


# E-mailmarketing{#e-mail-marketing}

>[!NOTE]
>
>Adobe is niet van plan om het e-mailvolgen van open/grenzen (niet te leveren) verder te verbeteren die door AEM dienst SMTP worden verzonden.
>De aanbeveling is om Adobe Campaign en de integratie in AEM[ te benutten.](/help/sites-administering/campaign.md)

E-mailmarketing (bijvoorbeeld nieuwsbrieven) is een belangrijk onderdeel van elke marketingcampagne die u gebruikt om inhoud naar uw leads te sturen. In AEM kunt u nieuwsbrieven maken van bestaande AEM inhoud en nieuwe inhoud toevoegen die specifiek is voor de nieuwsbrieven.

Nadat u de nieuwsbrieven hebt gemaakt, kunt u deze direct of op een ander gepland tijdstip naar de specifieke groep gebruikers sturen (via een workflow). Bovendien kunnen gebruikers zich abonneren op nieuwsbrieven in de door hen gekozen indeling.

Daarnaast kunt AEM u de functionaliteit voor nieuwsbrieven beheren, waaronder het onderhouden van onderwerpen, het archiveren van nieuwsbrieven en het weergeven van nieuwsbrieven.

>[!NOTE]
>
>In Geometrixx wordt de e-maileditor automatisch geopend in de sjabloon voor nieuwsbrieven. U kunt de e-maileditor in andere sjablonen gebruiken die u e-mailberichten wilt verzenden, bijvoorbeeld in uitnodigingen. De e-mailredacteur toont op om het even welk ogenblik een pagina van **mcm/componenten/nieuwsbrief/pagina** wordt ge??rft.

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

   ![](do-not-localize/mcm_icon_listview-1.png)

1. Klik **Nieuw..**

   U kunt de **Titel**, **Naam** en het type ervaring specificeren dat moet worden gecreeerd; in dit geval, Newsletter.

   ![mcm_createnewsletter](assets/mcm_createnewsletter.png)

1. Klik **Maken**.

1. Er wordt onmiddellijk een nieuw dialoogvenster geopend. Hier kunt u eigenschappen voor de nieuwsbrief ingaan.

   De **Standaardlijst met ontvangers** is een verplicht veld omdat dit het aanraakpunt voor de nieuwsbrief vormt (zie [Werken met lijsten](/help/sites-classic-ui-authoring/classic-personalization-campaigns.md#workingwithlists) voor meer informatie over lijsten).

   ![mcm_newsletterdialog](assets/mcm_newnewsletterdialog.png)

   * **Van**
NameName die als afzender van nieuwsbrief zou moeten verschijnen.

   * **Van adres**
AddressMail dat als afzender van nieuwsbrief zou moeten verschijnen.

   * ****
Onderwerp van de nieuwsbrief.

   * **Antwoord**
ToMail-adres dat antwoorden voor verzonden nieuwsbrief zou moeten adresseren.

   * ****
Beschrijving van de nieuwsbrief.

   * **On**
TimeThe op tijd voor het verzenden van de nieuwsbrief.

   * **Standaard Ontvangers**
ListDefault lijst die nieuwsbrief zou moeten ontvangen.
   Deze kunnen in een later stadium van **Eigenschappen worden bijgewerkt..**.

1. Klik **OK** om op te slaan.

## Inhoud toevoegen aan nieuwsbrieven {#adding-content-to-newsletters}

U kunt inhoud, inclusief dynamische inhoud, op dezelfde manier aan uw nieuwsbrief toevoegen als in elke AEM. In Geometrixx, heeft het malplaatje van de Nieuwsbrief bepaalde componenten beschikbaar voor het toevoegen van en het wijzigen van inhoud in nieuwsbrieven.

1. Klik in de MCM op het tabblad **Campagnes** en dubbelklik op de nieuwsbrief waaraan u inhoud wilt toevoegen of bewerken. De nieuwsbrief wordt geopend.

1. Als componenten niet zichtbaar zijn, ga naar de mening van het Ontwerp en laat de noodzakelijke componenten (bijvoorbeeld, de componenten van de Nieuwsbrief) toe alvorens u begint uit te geven.
1. Voer eventueel nieuwe tekst, afbeeldingen of andere componenten in. In het voorbeeld Geometrixx zijn vier componenten beschikbaar: Tekst, Afbeelding, Kop en 2 kolommen. Uw nieuwsbrief kan meer of minder componenten hebben afhankelijk van hoe u het opstelling.

   >[!NOTE]
   >
   >U kunt nieuwsbrieven personaliseren door variabelen te gebruiken. In de nieuwsbrief van de Geometrixx zijn de variabelen beschikbaar in de component van de Tekst. Waarden voor de variabelen worden overgenomen van de gegevens in het gebruikersprofiel.

   ![mcm_nieuwsbrief_content](assets/mcm_newsletter_content.png)

1. Als u variabelen wilt invoegen, selecteert u de variabele in de lijst en klikt u op **Invoegen**. Variabelen worden gevuld vanuit het profiel.

## Nieuwsbrieven aanpassen {#personalizing-newsletters}

U kunt nieuwsbrieven personaliseren door vooraf bepaalde variabelen in de component van de Tekst van nieuwsbrieven in Geometrixx op te nemen. Waarden voor de variabelen worden overgenomen van de gegevens in het gebruikersprofiel.

U kunt ook simuleren hoe een nieuwsbrief wordt gepersonaliseerd door de clientcontext te gebruiken en een profiel te laden.

Een nieuwsbrief personaliseren en simuleren hoe het eruit zal zien:

1. Open vanuit de MCM de nieuwsbrief waarvoor u instellingen wilt aanpassen.

1. Open de tekstcomponent die u wilt aanpassen.

1. Plaats de curseur waar u de variabele wilt verschijnen en selecteer een variabele van de drop-down lijst en klik **Tussenvoegsel**. Doe dit voor zo vele variabelen zoals vereist en klik **OK**.

   ![mcm_nieuwsbrief_variables](assets/mcm_newsletter_variables.png)

1. Als u wilt simuleren hoe de variabele eruitziet wanneer deze wordt verzonden, drukt u op CTRL+ALT+c om de clientcontext te openen en selecteert u **Laden**. Selecteer de gebruiker in de lijst waarvan u het profiel wilt laden en klik op **OK**.

   De gegevens uit het profiel dat u hebt geladen, bevatten de variabelen.

   ![mc_newsletter_testvariables](assets/mc_newsletter_testvariables.png)

## Nieuwsbrieven testen in verschillende e-mailclients {#testing-newsletters-in-different-e-mail-clients}

>[!NOTE]
>
>Alvorens nieuwsbrieven te verzenden, controleer de configuratie OSGi voor Dag CQ Verbinding Externalzer bij `https://localhost:4502/system/console/configMgr`.
>
>Standaard is de waarde van de parameter `localhost:4502` en kan de bewerking niet worden voltooid als de poort voor de actieve instantie wordt gewijzigd.

Schakel tussen algemene e-mailclients om te zien hoe uw nieuwsbrief eruit ziet voor uw leads. Standaard wordt uw nieuwsbrief geopend zonder dat een e-mailclient is geselecteerd.

Momenteel kunt u nieuwsbrieven in de volgende e-mailcli??nten bekijken:

* Yahoo-mail
* Gmail
* Hotmail
* Thundervogel
* Microsoft Outlook 2007
* Apple Mail

Als u wilt schakelen tussen clients, klikt u op het bijbehorende pictogram om de nieuwsbrief in die e-mailclient weer te geven:

1. Open vanuit de MCM de nieuwsbrief waarvoor u instellingen wilt aanpassen.

1. Klik op een e-mailclient in de bovenste balk om te zien hoe de nieuwsbrief er in die client uitziet.

   ![chlimage_1-119](assets/chlimage_1-119.png)

1. Herhaal deze stap voor alle andere e-mailclients die u wilt zien.

   ![chlimage_1-120](assets/chlimage_1-120.png)

## Newsletter-instellingen aanpassen {#customizing-newsletter-settings}

Hoewel alleen geautoriseerde gebruikers een nieuwsbrief kunnen verzenden, dient u het volgende aan te passen:

* De onderwerpregel, zodat gebruikers uw e-mail willen openen en er ook voor zorgen dat uw nieuwsbrief niet als spam wordt gemarkeerd.
* Het adres Van, bijvoorbeeld noreply@geometrixx.com, zodat de gebruikers e-mail van een gespecificeerd adres ontvangen.

De nieuwsbrief-instellingen aanpassen:

1. Open vanuit de MCM de nieuwsbrief waarvoor u instellingen wilt aanpassen.

   ![mcm_nieuwsbrief_open](assets/mcm_newsletter_open.png)

1. Klik boven aan de nieuwsbrief op **Instellingen**.

   ![mcm_nieuwsbrief_settings](assets/mcm_newsletter_settings.png)
1. Typ het **Van** e-mailadres

1. Wijzig, indien nodig, het **Onderwerp** van de e-mail.

1. Selecteer een **Standaardlijst met ontvangers** in de vervolgkeuzelijst.

1. Klik **OK**.

   Wanneer u de nieuwsbrief test of verzendt, zullen de ontvangers e-mail met het gespecificeerde e-mailadres en onderwerp ontvangen.

## Nieuwsbrieven voor het testen van vluchten {#flight-testing-newsletters}

Hoewel het testen van de vlucht niet verplicht is, kunt u het best testen voordat u een nieuwsbrief verstuurt om er zeker van te zijn dat het lijkt zoals u wilt.

Bij het testen van de vlucht kunt u het volgende doen:

* Bekijk de nieuwsbrief in [alle voorgenomen cli??nten](#testing-newsletters-in-different-e-mail-clients).
* Controleer of de mailserver juist is ingesteld.
* Bepaal of je e-mail wordt gemarkeerd als spam. (Zorg ervoor dat u uzelf opneemt in de lijst met ontvangers.)

>[!NOTE]
>
>Als u e-mailproviders bijwerkt, een vliegtest uitvoert of een nieuwsbrief verzendt, mislukken deze bewerkingen als de nieuwsbrief niet eerst naar de instantie Publiceren wordt gepubliceerd of als de instantie Publiceren niet beschikbaar is. Vergeet niet uw nieuwsbrief te publiceren en ervoor te zorgen dat de instantie Publiceren actief is.

Voor nieuwsbrieven voor vliegproeven:

1. Open vanuit de MCM de nieuwsbrief die u wilt testen en verzenden.

1. Klik boven aan de nieuwsbrief op **Test** om te testen voordat u de nieuwsbrief verzendt.

   ![mcm_nieuwsbrief_testsettings](assets/mcm_newsletter_testsettings.png)

1. Voer het teste-mailadres in waarnaar u de nieuwsbrief wilt verzenden en klik op **Verzenden**. Als u het profiel wilt wijzigen, laadt u een ander profiel in de clientcontext. U doet dit door op CTRL+ALT+c te drukken en een profiel laden en laden te selecteren.

## Nieuwsbrieven verzenden {#sending-newsletters}

>[!NOTE]
>
>Adobe is niet van plan om het e-mailvolgen van open/grenzen (niet te leveren) verder te verbeteren die door AEM dienst SMTP worden verzonden.
>De aanbeveling is om Adobe Campaign en de integratie in AEM[ te benutten.](/help/sites-administering/campaign.md)

U kunt een nieuwsbrief vanuit de nieuwsbrief of de lijst verzenden. Beide procedures worden beschreven.

>[!NOTE]
>
>Alvorens nieuwsbrieven te verzenden, controleer de configuratie OSGi voor Dag CQ Verbinding Externalzer bij `https://localhost:4502/system/console/configMgr`.
>
>Standaard is de waarde van de parameter `localhost:4502` en kan de bewerking niet worden voltooid als de poort voor de actieve instantie wordt gewijzigd.

>[!NOTE]
>
>Als u e-mailproviders bijwerkt, een vliegtest uitvoert of een nieuwsbrief verzendt, mislukken deze bewerkingen als de nieuwsbrief niet eerst naar de instantie Publiceren wordt gepubliceerd of als de instantie Publiceren niet beschikbaar is. Vergeet niet uw nieuwsbrief te publiceren en ervoor te zorgen dat de instantie Publiceren actief is.

### Nieuwsbrieven verzenden vanuit een campagne {#sending-newsletters-from-a-campaign}

Een nieuwsbrief sturen vanuit de campagne:

1. Open vanuit de MCM de nieuwsbrief die u wilt verzenden.

   >[!NOTE]
   >
   >Voordat u een nieuwsbrief verzendt, moet u ervoor zorgen dat u het onderwerp van de nieuwsbrief en het oorspronkelijke e-mailadres hebt aangepast door [de instellingen ervan aan te passen](#customizing-newsletter-settings).
   >
   >
   >[Het wordt aanbevolen de nieuwsbrief v????r verzending te ](#flight-testing-newsletters) testen.

1. Klik boven aan de nieuwsbrief op **Verzenden**. De wizard Nieuwsbrief wordt geopend.

1. Selecteer in de lijst van de ontvanger de lijst waarop u de nieuwsbrief wilt ontvangen en klik op **Volgende**.

   ![mcm_newslettersend](assets/mcm_newslettersend.png)

1. De installatie is voltooid. Klik **Send** om nieuwsbrief eigenlijk te verzenden.

   ![mcm_newslettersendconfirm](assets/mcm_newslettersendconfirm.png)

   >[!NOTE]
   >
   >Zorg ervoor dat u een van de ontvangers bent, zodat u zeker weet dat de nieuwsbrief is ontvangen.

### Nieuwsbrieven verzenden vanuit een lijst {#sending-newsletters-from-a-list}

Een nieuwsbrief verzenden vanuit een lijst:

1. Klik in het MCM-bestand op **Lijsten** in het linkerdeelvenster.

   >[!NOTE]
   >
   >Voordat u een nieuwsbrief verzendt, moet u ervoor zorgen dat u het onderwerp van de nieuwsbrief en het oorspronkelijke e-mailadres hebt aangepast door [de instellingen ervan aan te passen](#customizing-newsletter-settings). U kunt een nieuwsbrief niet testen als u het van de lijst verzendt; u kunt [vliegtest](#flight-testing-newsletters) het als u het van nieuwsbrief verzendt.

1. Schakel het selectievakje in naast de lijst met leads waarnaar u een nieuwsbrief wilt verzenden.

1. Selecteer **Nieuwsbrief verzenden** in het menu **Extra**. Het venster **Send Newsletter** wordt geopend.

   ![mcm_newslettersendfromlist](assets/mcm_newslettersendfromlist.png)

1. Selecteer in het veld **Nieuwsbrief** de nieuwsbrief die u wilt verzenden en klik op **Volgende**.

   ![mcm_newslettersenddialog](assets/mcm_newslettersenddialog.png)

1. De installatie is voltooid. Klik **Verzenden** om de geselecteerde nieuwsbrief naar de gespecificeerde lijst van lood te verzenden.

   ![mcm_newslettersenddialog_confirm](assets/mcm_newslettersenddialog_confirmation.png)

   Uw nieuwsbrief wordt verzonden naar de geselecteerde ontvangers.

## Abonneren op een nieuwsbrief {#subscribing-to-a-newsletter}

In deze sectie wordt beschreven hoe u zich op een nieuwsbrief kunt abonneren.

### Abonneren op een nieuwsbrief {#subscribing-to-a-newsletter-1}

Abonneren op een nieuwsbrief (de website van de Geometrixx als voorbeeld):

1. Klik **Websites** en navigeer naar de Geometrixx **Werkbalk** en open deze.

   ![chlimage_1-121](assets/chlimage_1-121.png)

1. Voer in het veld **Aanmelden** in het nieuwsbrief Geometrixx uw e-mailadres in en klik op **Aanmelden**. U bent nu geabonneerd op de nieuwsbrief.
