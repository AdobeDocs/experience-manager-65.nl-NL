---
title: Een effectieve openingspagina voor nieuwsbrieven maken
description: Met een effectieve bestemmingspagina voor nieuwsbrieven krijgt u zoveel mogelijk personen die zich aanmelden voor uw nieuwsbrief (of andere campagne voor e-mailmarketing). U kunt de informatie die u van uw nieuwsbrief ontvangt gebruiken ondertekent-ups om lood te krijgen.
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: personalization
content-type: reference
docset: aem65
exl-id: c2fbf858-8815-426e-a2e5-f92bcf909ad0
solution: Experience Manager, Experience Manager Sites
feature: Authoring,Personalization
role: User
source-git-commit: 305227eff3c0d6414a5ae74bcf3a74309dccdd13
workflow-type: tm+mt
source-wordcount: '596'
ht-degree: 0%

---

# Een effectieve openingspagina voor nieuwsbrieven maken{#creating-an-effective-newsletter-landing-page}

Met een effectieve bestemmingspagina voor nieuwsbrieven krijgt u zoveel mogelijk personen die zich aanmelden voor uw nieuwsbrief (of andere campagne voor e-mailmarketing). U kunt de informatie die u van uw nieuwsbrief ontvangt gebruiken ondertekent-ups om lood te krijgen.

Als u een effectieve bestemmingspagina voor nieuwsbrieven wilt maken, moet u het volgende doen:

1. Maak een lijst voor de nieuwsbrief zodat mensen zich op de nieuwsbrief kunnen abonneren.
1. Maak het aanmeldingsformulier. Voeg tijdens dit proces een workflowstap toe waarmee de persoon die zich aanmeldt voor de nieuwsbrief automatisch wordt toegevoegd aan de lijst met leads.
1. Maak een bevestigingspagina waarop gebruikers worden bedankt voor hun aanmelding en waarin ze mogelijk een speciale actie kunnen uitvoeren.
1. Voeg theers toe.

>[!NOTE]
>
>Adobe is niet van plan deze mogelijkheid verder te verbeteren (Leads en lijsten beheren).
>De aanbeveling moet [&#x200B; Adobe Campaign en de integratie aan AEM &#x200B;](/help/sites-administering/campaign.md) gebruiken.

## Een lijst maken voor de nieuwsbrief {#creating-a-list-for-the-newsletter}

Creeer een lijst, bijvoorbeeld, **Nieuwsbrief van de Geometrixx**, in MCM voor nieuwsbrief die de mensen zouden moeten intekenen aan. Het creëren van lijsten wordt beschreven in [&#x200B; Creërend lijsten &#x200B;](/help/sites-classic-ui-authoring/classic-personalization-campaigns.md#creatingnewlists).

In het volgende voorbeeld ziet u een voorbeeld van een lijst:

![&#x200B; mcm_listcreate &#x200B;](assets/mcm_listcreate.png)

## Een aanmeldingsformulier maken {#create-a-sign-up-form}

Maak een registratieformulier voor nieuwsbrieven waarmee gebruikers zich op tags kunnen abonneren. De voorbeeldwebsite van de Geometrixx bevat een nieuwsbrief op de werkbalk Geometrixx waar u het formulier kunt maken.

Om uw eigen nieuwsbrief vorm tot stand te brengen, zie informatie over het creëren van vormen in de [&#x200B; documentatie van Forms &#x200B;](/help/sites-authoring/default-components.md#form). De nieuwsbrief gebruikt de markeringen van de bibliotheek van de Markering. Om extra markeringen toe te voegen, zie [&#x200B; Beleid van de Markering &#x200B;](/help/sites-authoring/tags.md#tagadministration).

De verborgen velden in het volgende voorbeeld bieden de minimale hoeveelheid informatie (e-mail). Daarnaast kunt u later meer velden toevoegen, maar dit heeft invloed op de conversiesnelheid.

In het volgende voorbeeld wordt een formulier gemaakt op https://localhost:4502/cf#/content/geometrixx/en/toolbar/newsletter.html.

1. Maak het formulier.

   ![&#x200B; mcm_newsletterpage &#x200B;](assets/mcm_newsletterpage.png)

1. Klik **uitgeven** in de component van de Vorm om de vorm te vormen om naar te gaan Dank u pagina (zie [&#x200B; Creërend Dank u Pagina&#39;s &#x200B;](#creating-a-thank-you-page)).

   ![&#x200B; dc_formstart_thankyou &#x200B;](assets/dc_formstart_thankyou.png)

1. Stel de handeling Formulier in (dat is wat er gebeurt wanneer u het formulier verzendt) en configureer de groep zodanig dat geregistreerde gebruikers worden toegewezen aan de lijst die u eerder hebt gemaakt (bijvoorbeeld geometrixx-nieuwsbrief).

   ![&#x200B; dc_formstart_thankyouadvanced &#x200B;](assets/dc_formstart_thankyouadvanced.png)

### Een pagina voor bedankt maken {#creating-a-thank-you-page}

Wanneer de gebruikers **&#x200B;**&#x200B;klikken nu abonneren, wilt u bedankt u pagina om automatisch te openen. Maak de pagina Bedankt op de pagina Geometrixx Newsletter. Nadat u het nieuwsbrief formulier hebt gemaakt, bewerkt u de component Formulier en voegt u het pad toe aan de pagina Hartelijk dank.

Het voorleggen van het verzoek neemt de gebruiker aan a **Dank u** pagina waarna zij een e-mail zullen ontvangen. Deze pagina Bedankt is gemaakt op /content/geometrixx/nl/toolbar/nieuwsbrief/bedankje.

![&#x200B; mcm_newsletter_thankyoupage &#x200B;](assets/mcm_newsletter_thankyoupage.png)

### Teasers toevoegen {#adding-teasers}

Voeg [&#x200B; meetapparaten &#x200B;](/help/sites-classic-ui-authoring/classic-personalization-campaigns.md#teasers) aan doelspecifiek publiek toe. U kunt bijvoorbeeld tellers toevoegen aan de pagina Vriendelijk bedankt en de pagina Nieuwsbrief.

Tasers toevoegen om een effectieve bestemmingspagina voor nieuwsbrieven te maken:

1. Maak een teasalinea voor een cadeau bij aanmelden. Selecteer **eerst** als strategie en omvat tekst die hen informeert welk cadeau zij zullen ontvangen.

   ![&#x200B; dc_teaser_thankyou &#x200B;](assets/dc_teaser_thankyou.png)

1. Maak een teasalinea voor de pagina Bedankt. Selecteer **eerst** als strategie en omvat tekst die erop wijst dat het geschenk op zijn manier is.

   ![&#x200B; chlimage_1-103 &#x200B;](assets/chlimage_1-103.png)

1. Maak een campagne met de twee theaters — neem er een aan met zaken en een zonder tags.

### Inhoud naar abonnees push {#pushing-content-to-subscribers}

Breng wijzigingen in pagina&#39;s aan via de nieuwsbrief-functionaliteit in de MCM. Vervolgens drukt u op bijgewerkte inhoud naar abonnees.

Zie [&#x200B; verzendend Nieuwsbrieven &#x200B;](/help/sites-classic-ui-authoring/classic-personalization-campaigns.md#newsletters).
