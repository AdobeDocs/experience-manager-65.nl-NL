---
title: E-mail naar e-mailserviceproviders publiceren
seo-title: E-mail naar e-mailserviceproviders publiceren
description: U kunt nieuwsbrieven aan de e-maildiensten zoals Ingenieur publiceren ExactTarget en Silverpop.
seo-description: U kunt nieuwsbrieven aan de e-maildiensten zoals Ingenieur publiceren ExactTarget en Silverpop.
uuid: 1a7adcfe-8e52-49f4-9a00-99ac99881225
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: personalization
content-type: reference
discoiquuid: b9618913-5433-4baf-9ff6-490a26860505
translation-type: tm+mt
source-git-commit: 016c705230dffec052c200b058a36cdbe0520fc4
workflow-type: tm+mt
source-wordcount: '1128'
ht-degree: 0%

---


# Een e-mail naar e-mailserviceproviders publiceren{#publishing-an-email-to-email-service-providers}

U kunt nieuwsbrieven aan de e-maildiensten zoals Ingenieur publiceren ExactTarget en Silverpop. In dit document wordt beschreven hoe u AEM kunt configureren om een nieuwsbrief naar deze e-mailservices te publiceren.

>[!NOTE]
>
>U moet de serviceprovider configureren voordat u een e-mail kunt maken en publiceren. Zie [Het vormen ExactTarget](/help/sites-administering/exacttarget.md) en [het Vormen Silverpop Ingenieur](/help/sites-administering/silverpop.md) voor meer informatie.

Voer de volgende stappen uit om uw e-mail naar het e-mailservicebureau te publiceren:

1. Maak een e-mail.
1. Pas de configuratie van de E-mailservice toe op de e-mail.
1. Publiceer de e-mail.

>[!NOTE]
>
>Als u e-mailproviders bijwerkt, een vliegtest uitvoert of een nieuwsbrief verzendt, mislukken deze bewerkingen als de nieuwsbrief niet eerst naar de instantie Publiceren wordt gepubliceerd of als de instantie Publiceren niet beschikbaar is. Vergeet niet uw nieuwsbrief te publiceren en ervoor te zorgen dat de instantie Publiceren actief is.

## Een e-mail {#creating-an-email} maken

Een e-mail of nieuwsbrief die u aan een e-maildienst wilt publiceren kan onder een campagne worden gecreeerd gebruikend het **malplaatje van het Nieuwsbrief**. U kunt ook de sjabloon **Geometrixx Outdoors E-mail** gebruiken. Voorbeeld-e-mail/nieuwsbrief-gebaseerd op **Geometrixx Outdoors E-mail** malplaatje zijn beschikbaar bij `https://<hostname>:<port>/cf#/content/campaigns/geometrixx-outdoors/e-mails.html`.

Een nieuwe e-mail tot stand brengen die aan de gevormde e-maildienst wordt gepubliceerd:

1. Ga naar **Websites** en **Campagnes**. Selecteer een campagne.
1. Klik **Nieuw** om het **Create Pagina** venster te openen.
1. Ga de titel, de naam in, en selecteer **Geometrixx Newsletter** malplaatje van de lijst van beschikbare malplaatjes.
1. Klik **Maken**.
1. Open het gemaakte e-mailbericht.
1. Schakel over naar de ontwerpmodus om de componenten te selecteren die u wilt weergeven in het hulpgedeelte.
1. Schakel over naar bewerkingsmodus en voeg inhoud (tekst, afbeeldingen, [e-mailgereedschappen](#adding-exacttarget-email-tools-to-your-email), [personalisatievariabelen](#adding-text-and-personalization-tool-to-your-e-mail) enzovoort) toe aan uw e-mail.

### ExactTarget-e-mailhulpprogramma&#39;s toevoegen aan uw e-mail {#adding-exacttarget-email-tools-to-your-email}

>[!NOTE]
>
>Deze sectie is specifiek voor de dienst ExactTarget.

De **E-mailhulpprogramma**-component voor ExactTarget kan meer e-mailfunctionaliteit toevoegen aan uw e-mail/nieuwsbrief.

1. Open een e-mail die naar ExactTarget moet worden gepubliceerd.
1. Voeg de component **ET - E-mailhulpmiddelen** aan uw pagina toe gebruikend sidekick. Open de component in de modus Bewerken.

   ![chlimage_1](assets/chlimage_1.gif)

1. Selecteer een optie in het menu **Opties**:

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
   <td>Subscription Center</td>
   <td>Een abonnementscentrum is een webpagina waarop een abonnee de berichten kan beheren die hij of zij van uw organisatie ontvangt.</td>
  </tr>
  <tr>
   <td>E-mailopenen bijhouden</td>
   <td>Een verborgen component die u toestaat om de ExactTarget volgende eigenschap te gebruiken.<br /> </td>
  </tr>
 </tbody>
</table>

>[!NOTE]
>
>Het vervolgkeuzemenu **Opties** wordt alleen gevuld als de ExactTarget-configuratie wordt toegepast op de e-mail. Zie [Configuratie van e-mailservice toepassen op e-mailinstellingen](#applying-e-mail-service-configuration-to-e-mail-settings) voor meer informatie.

1. Publiceer de e-mail naar ExactTarget.

   De e-mail met de e-mailhulpprogramma&#39;s is beschikbaar voor gebruik in de geconfigureerde ExactTarget-account.

>[!NOTE]
>
>* De URL&#39;s in de e-mailprogramma&#39;s worden alleen vervangen (in de ontvangen e-mail) door de werkelijke waarden wanneer een e-mailbericht wordt verzonden met **Eenvoudig verzenden** of **Met instructies verzenden**, maar niet **Testen verzenden**.
   >
   >
* Twee van de e-mailprogramma&#39;s zijn vereist: **Fysiek mailadres (vereist)** en **Profielcentrum (vereist)**. Wanneer e-mail aan ExactTarget wordt gepubliceerd, worden deze twee e-mail-hulpmiddelen toegevoegd aan de bodem van elke post door gebrek.

>



### Het hulpmiddel van de Tekst en van de Aanpassing aan uw e-mail {#adding-text-and-personalization-tool-to-your-e-mail} toevoegen

U kunt gepersonaliseerde gebieden in een e-mail toevoegen door **Tekst en Personalisatie** component aan de pagina toe te voegen:

1. Open de e-mail die u naar uw e-mailservice wilt publiceren.
1. Om verpersoonlijkingsgebied van uw e-maildienst toe te laten, voeg de kaderconfiguratie toe terwijl het vormen van de e-maildienst. Zie [Silverpop Engage configureren](/help/sites-administering/silverpop.md) en [Exact doel configureren](/help/sites-administering/exacttarget.md) voor meer informatie.
1. Voeg de component **Tekst &amp; Personalisatie** van sidekick toe. Deze component is het deel van nieuwsbrief groep. Open deze component in de bewerkingsmodus.

   ![chlimage_1-110](assets/chlimage_1-110a.png)

1. Voeg het vereiste gepersonaliseerde gebied aan de tekst toe door het gebied van het drop-down menu te selecteren en **Tussenvoegsel** te klikken.
1. Klik **OK** om te voltooien.

## Configuratie van e-mailservice toepassen op e-mailinstellingen {#applying-e-mail-service-configuration-to-e-mail-settings}

Om uw E-maildienstconfiguratie op een nieuwsbrief toe te passen:

1. Creeer een configuratie van de E-mailDienst.
1. Open uw e-mail/nieuwsbrief.
1. Open de instellingen voor e-mail/nieuwsbrief door te klikken op **Instellingen** of door te klikken op **Pagina-eigenschappen in** op het secundaire bestand.
1. Klik **Service toevoegen** in **Cloud Services** tabel. U ziet de lijst met services. Selecteer uw vereiste configuratie - of **ExactTarget** of **Silverpop** - van de lijst van de drop-down lijst.

   ![chlimage_1-5](assets/chlimage_1-5a.jpeg)

1. Klik **OK**.

## E-mails naar e-mailservice publiceren {#publishing-emails-to-email-service}

E-mails/nieuwsbrieven kunnen aan uw E-maildienst worden gepubliceerd door deze stappen te volgen:

1. Open het e-mailbericht.
1. Voordat u een e-mailbericht publiceert, moet u controleren of u de juiste configuratie op uw e-mail hebt toegepast.
1. Klik **Publiceren**. Hiermee wordt het venster **Nieuwsbrief publiceren naar e-mailprovider** geopend.
1. Vul het veld **Naam nieuwsbrief** in. Het e-mailbericht/de nieuwsbrief wordt gepubliceerd aan E-mail Service Provider met deze naam. Als er geen e-mailnaam wordt opgegeven, wordt de e-mail gepubliceerd met de paginanaam van de nieuwsbrief in AEM.
1. Klik **Publiceren**.

   ![chlimage_1-6](assets/chlimage_1-6.jpeg)

   AEM bevestigt dat u de e-mail kunt weergeven in ExactTarget of Silverpop Engage.

   In het geval van ExactTarget kan de gepubliceerde e-mail zijn bekeken door **Gepubliceerde e-mail weergeven** te klikken. Dit neemt u rechtstreeks aan de gepubliceerde nieuwsbrief in ExactTarget ([https://members.exacttarget.com/](https://members.exacttarget.com/).).

>[!NOTE]
>
>Als een e-mail/nieuwsbrief met dezelfde naam wordt gepubliceerd als een e-mail/nieuwsbrief die reeds is gepubliceerd, wordt de eerdere e-mail/nieuwsbrief niet vervangen. In plaats daarvan wordt een nieuwe e-mail/nieuwsbrief met dezelfde naam gemaakt (de id&#39;s van twee nieuwsbrieven zijn echter anders).
>
>Als u de e-mail/nieuwsbrief naar de e-mailserviceprovider publiceert, wordt ook de e-mail/nieuwsbrief naar de AEM-publicatie-instantie gepubliceerd.


### Een gepubliceerde e-mail {#updating-a-published-e-mail} bijwerken

Met de knop **Bijwerken** in het dialoogvenster Publiceren kunt u een nieuwsbrief bijwerken die al is gepubliceerd naar een e-mailserviceprovider. Als de nieuwsbrief nog niet is gepubliceerd en **Update** knoop wordt geklikt, wordt een **Newsletter niet gepubliceerd** berichtvertoningen.

Een gepubliceerde e-mail bijwerken:

1. Open de e-mail/nieuwsbrief die eerder is gepubliceerd aan een e-mailserviceprovider die u opnieuw wilt publiceren nadat u wijzigingen in de e-mail/nieuwsbrief hebt aangebracht.
1. Klik **Publiceren**. Het venster **Nieuwsbrief publiceren naar e-mailserviceprovider** wordt weergegeven. Klik **Update**.

   Als u wilt controleren of de e-mail/nieuwsbrief is bijgewerkt op ExactTarget, klikt u op **Gepubliceerde e-mail weergeven**. Hiermee gaat u naar de gepubliceerde e-mail in ExactTarget.

   Ga naar de Silverpop Engage-site om te controleren of de e-mail/nieuwsbrief is bijgewerkt via de Silverpop-e-mailservice.

