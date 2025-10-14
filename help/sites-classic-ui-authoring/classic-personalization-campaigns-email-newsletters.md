---
title: E-mail naar e-mailserviceproviders publiceren
description: U kunt nieuwsbrieven aan de e-maildiensten zoals Ingenieur publiceren ExactTarget en Silverpop.
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: personalization
content-type: reference
exl-id: c07692f7-3618-4e8c-96d7-4db09f2d9896
solution: Experience Manager, Experience Manager Sites
feature: Authoring,Personalization
role: User
source-git-commit: 305227eff3c0d6414a5ae74bcf3a74309dccdd13
workflow-type: tm+mt
source-wordcount: '1106'
ht-degree: 0%

---

# E-mail naar e-mailserviceproviders publiceren{#publishing-an-email-to-email-service-providers}

U kunt nieuwsbrieven aan de e-maildiensten zoals Ingenieur publiceren ExactTarget en Silverpop. In dit document wordt beschreven hoe u AEM kunt configureren om een nieuwsbrief naar deze e-mailservices te publiceren.

>[!NOTE]
>
>U moet de serviceprovider configureren voordat u een e-mail kunt maken en publiceren. Zie [&#x200B; het Vormen ExactTarget &#x200B;](/help/sites-administering/exacttarget.md) en [&#x200B; het Vormen SilverpopMogelijkheid &#x200B;](/help/sites-administering/silverpop.md) voor meer informatie.

Voer de volgende stappen uit om uw e-mail naar het e-mailservicebureau te publiceren:

1. Maak een e-mail.
1. Pas de configuratie van de E-mailservice toe op de e-mail.
1. Publish het e-mailbericht.

>[!NOTE]
>
>Als u e-mailproviders bijwerkt, een vliegtest uitvoert of een nieuwsbrief verzendt, mislukken deze bewerkingen als de nieuwsbrief niet eerst naar de Publish-instantie wordt gepubliceerd of als de Publish-instantie niet beschikbaar is. Publiceer uw nieuwsbrief en zorg ervoor dat het Publish-exemplaar actief is.

## Een e-mail maken {#creating-an-email}

Een e-mail of een bulletin dat u aan de e-maildienst wilt publiceren kan onder een campagne worden gecreeerd gebruikend het **Malplaatje van het Nieuwsbrief van de Geometrixx**. U kunt het **Geometrixx Outdoors E-mail** malplaatje ook gebruiken. De steekproef e-mail/nieuwsbrief-gebaseerd op het **Geometrixx Outdoors E-mail** malplaatje zijn beschikbaar bij `https://<hostname>:<port>/cf#/content/campaigns/geometrixx-outdoors/e-mails.html`.

Om een e-mail tot stand te brengen die aan de gevormde e-maildienst wordt gepubliceerd:

1. Ga naar **Websites** en dan **Campagnes**. Selecteer een campagne.
1. Klik **Nieuw** om **te openen creeer het venster van de Pagina**.
1. Ga de titel, de naam in, en selecteer het **Malplaatje van het Geometrixx- Nieuwsbrief** van de lijst van beschikbare malplaatjes.
1. Klik **creëren**.
1. Open het gemaakte e-mailbericht.
1. Schakel over naar de ontwerpmodus om de componenten te selecteren die u wilt weergeven in het hulpgedeelte.
1. De schakelaar om wijze uit te geven en beginnen inhoud (tekst, beelden, [&#x200B; e-mailhulpmiddelen &#x200B;](#adding-exacttarget-email-tools-to-your-email) toe te voegen, [&#x200B; verpersoonlijkingsvariabelen &#x200B;](#adding-text-and-personalization-tool-to-your-e-mail), etc.) aan uw e-mail.

### ExactTarget-e-mailhulpprogramma&#39;s toevoegen aan uw e-mail {#adding-exacttarget-email-tools-to-your-email}

>[!NOTE]
>
>Deze sectie is specifiek voor de dienst ExactTarget.

De **E-mailHulpmiddelen** component voor ExactTarget kan meer e-mailfunctionaliteit aan uw e-mail/bulletin toevoegen.

1. Open een e-mail die naar ExactTarget moet worden gepubliceerd.
1. Voeg de component **ET toe - E-mailHulpmiddelen** aan uw pagina gebruikend sidekick. Open de component in de modus Bewerken.

   ![&#x200B; chlimage_1 &#x200B;](assets/chlimage_1.gif)

1. Selecteer een optie van het **menu van Opties**:

<table>
 <tbody>
  <tr>
   <td>Fysiek mailadres (vereist)</td>
   <td>Deze component neemt het fysieke postingsadres van uw organisatie in uw e-mail op.</td>
  </tr>
  <tr>
   <td>Profielmidden (vereist)</td>
   <td>Het profielcentrum is een webpagina waar de abonnees de persoonlijke informatie kunnen ingaan en handhaven die u over hen houdt.</td>
  </tr>
  <tr>
   <td>E-mail weergeven als webpagina</td>
   <td>Met deze component kan de gebruiker de e-mail weergeven als een webpagina.</td>
  </tr>
  <tr>
   <td>Privacybeleid</td>
   <td>Deze component neemt de verbinding aan uw privacybeleid in e-mail op.<br /> </td>
  </tr>
  <tr>
   <td>Abonnementscentrum opzeggen</td>
   <td>Hiermee krijgt de gebruiker de mogelijkheid om zich af te melden bij uw mailinglijst.</td>
  </tr>
  <tr>
   <td>Abonnementencentrum</td>
   <td>Een abonnementscentrum is een webpagina waarop een abonnee de berichten kan beheren die hij of zij van uw organisatie ontvangt.</td>
  </tr>
  <tr>
   <td>E-mailopenen bijhouden</td>
   <td>Een verborgen component die u de functie ExactTarget het volgen laat gebruiken.<br /> </td>
  </tr>
 </tbody>
</table>

>[!NOTE]
>
>Het **drop-down menu van Opties** is slechts bevolkt als de configuratie ExactTarget op e-mail wordt toegepast. Zie [&#x200B; Toepassend de Configuratie van de E-mailDienst op E-mailmontages &#x200B;](#applying-e-mail-service-configuration-to-e-mail-settings) voor meer informatie.

1. Publish de e-mail naar ExactTarget.

   De e-mail met de e-mailhulpprogramma&#39;s is beschikbaar voor gebruik in de geconfigureerde ExactTarget-account.

>[!NOTE]
>
>* URLs binnen de e-mailhulpmiddelen wordt vervangen (in ontvangen e-mail) door hun daadwerkelijke waarden slechts wanneer e-mail wordt verzonden gebruikend **Eenvoudig verzendt** of **Geleide verzendt** maar niet **Test verzendt**.
>
>* Twee van de e-mailhulpmiddelen worden vereist: **Fysiek Mailing Adres (Vereist)** en **het Centrum van het Profiel (Vereist)**. Wanneer e-mail aan ExactTarget wordt gepubliceerd, worden deze twee e-mail-hulpmiddelen toegevoegd aan de bodem van elke post door gebrek.
>

### Tekst en Personalization-gereedschap toevoegen aan uw e-mail {#adding-text-and-personalization-tool-to-your-e-mail}

U kunt gepersonaliseerde gebieden in een e-mail toevoegen door de **Tekst en de component van Personalization** aan de pagina toe te voegen:

1. Open de e-mail die u naar uw e-mailservice wilt publiceren.
1. Om verpersoonlijkingsgebied van uw e-maildienst toe te laten, voeg de kaderconfiguratie toe terwijl het vormen van de e-maildienst. Zie [&#x200B; het vormen SilverpopMoeilijke &#x200B;](/help/sites-administering/silverpop.md) en [&#x200B; het vormen Exact Doel &#x200B;](/help/sites-administering/exacttarget.md) voor meer informatie.
1. Voeg de component **Tekst &amp; Personalization** van sidekick toe. Deze component is het deel van nieuwsbrief groep. Open deze component in de bewerkingsmodus.

   ![&#x200B; chlimage_1-110 &#x200B;](assets/chlimage_1-110a.png)

1. Voeg het vereiste gepersonaliseerde gebied aan de tekst toe door het gebied van het drop-down menu te selecteren en **Tussenvoegsel** te klikken.
1. Klik **O.K.** om te beëindigen.

## Configuratie van e-mailservice toepassen op e-mailinstellingen {#applying-e-mail-service-configuration-to-e-mail-settings}

Om uw E-maildienstconfiguratie op een nieuwsbrief toe te passen:

1. Creeer een configuratie van de E-mailDienst.
1. Open uw e-mail/nieuwsbrief.
1. Open de e-mail/nieuwsbrief montages door of **Montages** te klikken of door **Eigenschappen van de Pagina in** te klikken sidekick.
1. Klik **toevoegen de Dienst** in **Cloud Servicen** tabel. U ziet de lijst met services. Selecteer uw vereiste configuratie - of **ExactTarget** of **Silverpop** - van de lijst van de drop-down lijst.

   ![&#x200B; chlimage_1-5 &#x200B;](assets/chlimage_1-5a.jpeg)

1. Klik **OK**.

## E-mails naar e-mailservice publiceren {#publishing-emails-to-email-service}

E-mails/nieuwsbrieven kunnen aan uw E-maildienst worden gepubliceerd door deze stappen te volgen:

1. Open het e-mailbericht.
1. Voordat u een e-mailbericht publiceert, moet u controleren of u de juiste configuratie op uw e-mail hebt toegepast.
1. Klik **Publish**. Dit opent het **Nieuwsbrief van Publish aan E-mailDienstverlener** venster.
1. Vul het **gebied van de Naam van het 0&rbrace; Nieuwsbrief in.** Het e-mailbericht/de nieuwsbrief wordt gepubliceerd aan E-mail Service Provider met deze naam. Als er geen e-mailnaam wordt opgegeven, wordt de e-mail gepubliceerd met de paginanaam van de nieuwsbrief in AEM.
1. Klik **Publish**.

   ![&#x200B; chlimage_1-6 &#x200B;](assets/chlimage_1-6.jpeg)

   AEM bevestigt dat u de e-mail kunt weergeven in ExactTarget of Silverpop Engage.

   Als er ExactTarget is kan de gepubliceerde e-mail hebben bekeken door **Gepubliceerde E-mail van de Mening te klikken**. Dit neemt u rechtstreeks aan de gepubliceerde nieuwsbrief in ExactTarget ([&#x200B; https://members.exacttarget.com/ &#x200B;](https://members.exacttarget.com/).).

>[!NOTE]
>
>Als een e-mail/nieuwsbrief met dezelfde naam wordt gepubliceerd als een e-mail/nieuwsbrief die reeds is gepubliceerd, wordt de eerdere e-mail/nieuwsbrief niet vervangen. In plaats daarvan wordt een nieuwe e-mail/nieuwsbrief met dezelfde naam gemaakt (de id&#39;s van twee nieuwsbrieven zijn echter anders).
>
>Als u de e-mail/nieuwsbrief naar de e-mailserviceprovider publiceert, wordt ook de e-mail/nieuwsbrief naar de AEM-publicatie-instantie gepubliceerd.
>

### Een gepubliceerde e-mail bijwerken {#updating-a-published-e-mail}

De **knoop van de Update** op de de dialoogdoos van Publish laat u een nieuwsbrief bijwerken die reeds aan een E-mailDienstverlener wordt gepubliceerd. In het geval dat nieuwsbrief nog niet is gepubliceerd en de **knoop van de Update** wordt geklikt, wordt de a **Newsletter niet gepubliceerd** berichtvertoningen.

Een gepubliceerde e-mail bijwerken:

1. Open de e-mail/nieuwsbrief die eerder is gepubliceerd aan een e-mailserviceprovider die u opnieuw wilt publiceren nadat u wijzigingen in de e-mail/nieuwsbrief hebt aangebracht.
1. Klik **Publish**. Het **Nieuwsbrief van Publish aan E-mailDienstverlener** venstervertoningen. Klik **Update**.

   Om te controleren als e-mail/nieuwsbrief op ExactTarget is bijgewerkt, klik **Gepubliceerde E-mail van de Mening**. Hiermee gaat u naar de gepubliceerde e-mail in ExactTarget.

   Ga naar de Silverpop Engage-site om te controleren of de e-mail/nieuwsbrief is bijgewerkt via de Silverpop-e-mailservice.
