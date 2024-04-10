---
title: Identity Management
description: Meer informatie over de interne werking van identiteitsbeheer in AEM.
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: Security
content-type: reference
docset: aem65
exl-id: acb5b235-523e-4c01-9bd2-0cc2049f88e2
solution: Experience Manager, Experience Manager Sites
feature: Administering
role: Admin
source-git-commit: 315171dca4501718a34fd33f937334f7e7958963
workflow-type: tm+mt
source-wordcount: '1249'
ht-degree: 0%

---


# Identity Management{#identity-management}

Individuele bezoekers van uw website kunnen alleen worden geïdentificeerd wanneer u hun de mogelijkheid biedt zich aan te melden. Er zijn verschillende redenen waarom u een aanmeldingsfunctie wilt opgeven:

* [AEM Communities](/help/communities/overview.md)Sitebezoekers moeten zich aanmelden om inhoud naar de community te posten.
* [Gesloten gebruikersgroepen](/help/sites-administering/cug.md)

  Mogelijk moet u de toegang tot uw website (of gedeelten ervan) beperken tot specifieke bezoekers.

* [Personalisatie](/help/sites-administering/personalization.md) Toestaan dat bezoekers bepaalde aspecten configureren van hoe ze toegang krijgen tot uw website.

De functionaliteit voor aanmelden (en uitloggen) wordt geleverd door een [account met een **Profiel**](#profiles-and-user-accounts), die aanvullende informatie over de geregistreerde bezoeker (gebruiker) bevat. De eigenlijke registratie- en vergunningsprocedures kunnen verschillen:

* Zelfregistratie vanaf de website

  A [Community-site](/help/communities/sites-console.md) kan zo worden geconfigureerd dat bezoekers zich zelf kunnen registreren of zich kunnen aanmelden bij hun Facebook- of Twitter-accounts.

* Registratieverzoek van de website

  Voor een gesloten gebruikersgroep kunt u bezoekers toestaan om registratie aan te vragen, maar u kunt toestemming afdwingen door middel van een workflow.

* Registreer elk account in de auteursomgeving

  Als u een klein aantal profielen hebt, waarvoor toch toestemming nodig is, kunt u besluiten om elk profiel rechtstreeks te registreren.

Om bezoekers in staat te stellen zich te registreren, kan een reeks componenten en formulieren worden gebruikt om de vereiste identificatiegegevens te verzamelen, dan de extra (vaak facultatieve) profielinformatie. Nadat zij zich hebben geregistreerd, moeten zij ook de gegevens die zij hebben ingediend, kunnen controleren en bijwerken.

Aanvullende functionaliteit kan worden geconfigureerd of ontwikkeld:

* Vorm om het even welke omgekeerde replicatie die wordt vereist.
* Gebruikers toestaan hun profiel te verwijderen door samen met een workflow een formulier te ontwikkelen.

>[!NOTE]
>
>De in het profiel opgegeven informatie kan ook worden gebruikt om de gebruiker gerichte inhoud te bieden via [Segmenten](/help/sites-administering/campaign-segmentation.md) en [Campagnes](/help/sites-classic-ui-authoring/classic-personalization-campaigns.md).

## Registratie Forms {#registration-forms}

A [formulier](/help/sites-authoring/default-components.md#form-component) kan worden gebruikt om de registratiegegevens te verzamelen en genereert vervolgens het nieuwe account en profiel.

Gebruikers kunnen bijvoorbeeld een nieuw profiel aanvragen met de pagina Geometrixx
`http://localhost:4502/content/geometrixx-outdoors/en/user/register.html`

![Voorbeeld van registratieformulier](assets/registerform.png)

Na het verzenden van de aanvraag wordt de profielpagina geopend waar de gebruiker persoonlijke gegevens kan opgeven.

![Voorbeeldprofielpagina](assets/profilepage.png)

Het nieuwe account is ook zichtbaar in het dialoogvenster [Gebruikersconsole](/help/sites-administering/security.md).

## Aanmelden {#login}

De login component kan worden gebruikt om de login informatie te verzamelen, dan het login proces te activeren.

Hierdoor krijgt de bezoeker de standaardvelden van **Gebruikersnaam** en **Wachtwoord**, met een **Aanmelden** om het aanmeldingsproces te activeren wanneer de aanmeldingsgegevens worden ingevoerd.

Gebruikers kunnen zich bijvoorbeeld aanmelden of een account maken met de **Aanmelden** op de werkbalk Geometrixx, die de pagina gebruikt:

`http://localhost:4502/content/geometrixx-outdoors/en/user/sign-in.html`

![Voorbeeld van aanmeldpagina](assets/login.png)

## Afmelden {#logging-out}

Aangezien er een login mechanisme is, wordt een logout mechanisme ook vereist. Dit is beschikbaar als de **Afmelden** in Geometrixx.

## Een profiel weergeven en bijwerken {#viewing-and-updating-a-profile}

Afhankelijk van uw registratieformulier kan de bezoeker gegevens in zijn profiel hebben geregistreerd. Zij moeten dit in een later stadium kunnen bekijken en/of bijwerken. Dit kan met een gelijkaardige vorm worden gedaan; bijvoorbeeld in Geometrixx:

```
http://localhost:4502/content/geometrixx-outdoors/en/user/profile.html
```

Klik op **Mijn profiel** in de rechterbovenhoek van een pagina, bijvoorbeeld met de `admin` account:
`http://localhost:4502/home/users/a/admin/profile.form.html/content/geometrixx-outdoors/en/user/profile.html.`

U kunt een ander profiel weergeven met de [clientcontext](/help/sites-administering/client-context.md) (over de auteursomgeving en met voldoende privileges):

1. Open een pagina, bijvoorbeeld de pagina Geometrixx:

   `http://localhost:4502/cf#/content/geometrixx/en.html`

1. Klikken **Mijn profiel** in de rechterbovenhoek. U ziet het profiel van uw huidige account, bijvoorbeeld de beheerder.
1. Druk **control-alt-C** om de clientcontext te openen.
1. Klik in de linkerbovenhoek van de clientcontext op de knop **Een profiel laden** knop.

   ![Een profielpictogram laden](do-not-localize/loadprofile.png)

1. Selecteer een ander profiel in de vervolgkeuzelijst in het dialoogvenster, bijvoorbeeld **Alison Parker**.
1. Klikken **OK**.
1. Klik nogmaals op **Mijn profiel**. Het formulier wordt bijgewerkt met de gegevens van Alison.

   ![Voorbeeldprofiel van Alison](assets/profilealison.png)

1. U kunt nu **Profiel bewerken** of **Wachtwoord wijzigen** om de details bij te werken.

## Velden toevoegen aan de profieldefinitie {#adding-fields-to-the-profile-definition}

U kunt velden toevoegen aan de profieldefinitie. Als u bijvoorbeeld een veld Favoriete kleur wilt toevoegen aan het profiel Geometrixx:

1. Navigeer vanuit de websiteconsole naar Geometrixx Outdoors Site > Engels > Gebruiker > Mijn profiel.
1. Dubbelklik op de knop **Mijn profiel** pagina om deze te openen voor bewerking.
1. In de **Componenten** tabblad van sidekick breidt het **Formulier** sectie.
1. Sleep een **Vervolgkeuzelijst** van sidekick naar het formulier, net onder de **Over mij** veld.
1. Dubbelklik op de knop **Vervolgkeuzelijst** om het dialoogvenster voor configuratie te openen en voer in:

   * **Elementnaam** - `favoriteColor`
   * **Titel** - `Favorite Color`
   * **Items** - Verschillende kleuren toevoegen als items

   Klikken **OK** opslaan.

1. Sluit de pagina en ga terug naar de **Websites** en activeer de pagina Mijn profiel.

   De volgende keer dat u een profiel weergeeft, kunt u een favoriete kleur selecteren:

   ![Het favoriete kleurvoorbeeldveld van Alison Parker](assets/aparkerfavcolour.png)

   Het veld wordt opgeslagen onder het tabblad **profiel** deel van de desbetreffende gebruikersaccount:

   ![Gegevens van Alison Parker in CRXDE](assets/aparkercrxdelite.png)

## Profielstatussen {#profile-states}

Er zijn verscheidene gebruiksgevallen die vereisen wetend of een gebruiker (of eerder hun profiel) in een *specifieke staat* of niet.

Dit betekent dat een geschikte eigenschap in het gebruikersprofiel moet worden gedefinieerd:

* is zichtbaar en toegankelijk voor de gebruiker
* definieert twee statussen voor elke eigenschap
* Hiermee kunt u schakelen tussen de twee gedefinieerde statussen

Dit wordt gedaan met:

* [Providers](#state-providers)

  De twee statussen van een specifieke eigenschap en de overgangen tussen beide beheren.

* [Workflows](#workflows)

  Handelingen met betrekking tot de staten beheren.

U kunt meerdere statussen definiëren, bijvoorbeeld in Geometrixx:

* zich abonneren (of het afmelden) op berichten op nieuwsbrieven of commentaardraden
* toevoegen en verwijderen van een verbinding met een vriend

### Providers {#state-providers}

Een staatsleverancier beheert de huidige status van het betrokken eigendom, samen met de overgangen tussen de twee mogelijke statussen.

De leveranciers van de staat worden uitgevoerd als componenten, zodat kan voor uw project worden aangepast. In de Geometrixx omvatten deze:

* Onderwerp gebruikersforum/abonneeforum
* Vriend toevoegen/verwijderen

### Workflows {#workflows}

De leveranciers van de staat leiden een profielbezit en zijn staten.

Er is een workflow nodig om de acties met betrekking tot de staten uit te voeren. Wanneer u bijvoorbeeld een abonnement neemt op meldingen, wordt in de workflow de actie voor het feitelijke abonnement afgehandeld. Wanneer u zich niet meer abonneert op meldingen, wordt in de workflow het verwijderen van de gebruiker uit de abonnementenlijst afgehandeld.

## Profielen en gebruikersaccounts {#profiles-and-user-accounts}

Profielen worden als onderdeel van de[gebruikersaccount](/help/sites-administering/user-group-ac-admin.md).

Het profiel is te vinden onder `/home/users/geometrixx`:

![Profielen zoals weergegeven in CRXDE](assets/chlimage_1-138.png)

Bij een standaardinstallatie (auteur of publicatie) heeft iedereen toegang tot de volledige profielgegevens van alle gebruikers. iedereen is een &quot;*Geïntegreerde groep die automatisch alle bestaande gebruikers en groepen bevat. De ledenlijst kan niet worden bewerkt*&quot;.

Deze toegangsrechten worden bepaald door volgende vervangingsACL:

/home: iedereen kan jcr:read rep:glob = &#42;/profile&#42;

Dat maakt het mogelijk:

* forum, opmerkingen of blogberichten om informatie (zoals pictogram of volledige naam) weer te geven vanuit het juiste profiel
* koppelingen naar geometrixe profielpagina&#39;s

Als deze toegang niet geschikt is voor uw installatie, kunt u deze standaardinstellingen wijzigen.

Dit kan worden gedaan gebruikend **[Toegangsbeheer](/help/sites-administering/user-group-ac-admin.md#access-right-management)** tab:

![Het beheren van ACLs in CRXDE](assets/aclmanager.png)

## Profielcomponenten {#profile-components}

Er is ook een reeks profielcomponenten beschikbaar waarmee u de profielvereisten voor uw site kunt definiëren.

### Veld voor gecontroleerd wachtwoord {#checked-password-field}

Deze component bevat twee velden voor:

* de invoer van een wachtwoord
* een controle om te bevestigen dat het wachtwoord correct is ingevoerd.

Met standaardinstellingen wordt de component als volgt weergegeven:

![Het dialoogvenster Wachtwoord controleren](assets/dc_profiles_checkedpassword.png)

### Profiel Avatar Photo {#profile-avatar-photo}

Deze component biedt de gebruiker een mechanisme voor het selecteren en uploaden van een Avatar Photo-bestand.

![Avatar-kiezer](assets/dc_profiles_avatarphoto.png)

### Gedetailleerde naam profiel {#profile-detailed-name}

Met deze component kan de gebruiker een gedetailleerde naam invoeren.

![Dialoogvenster Gedetailleerde naam](assets/dc_profiles_detailedname.png)

### Profiel Geslacht {#profile-gender}

Met deze component kan de gebruiker zijn geslacht invoeren.

![Genderselector](assets/dc_profiles_gender.png)
