---
title: Identiteitsbeheer
seo-title: Identiteitsbeheer
description: Meer informatie over identiteitsbeheer in AEM.
seo-description: Meer informatie over identiteitsbeheer in AEM.
uuid: d9b83cd7-c47a-41a5-baa4-bbf385d13bfd
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: Security
content-type: reference
discoiquuid: 994a5751-7267-4a61-9bc7-01440a256c65
docset: aem65
translation-type: tm+mt
source-git-commit: a268b7046430cc17c8b59b9306cf3533d73bb4a2

---


# Identiteitsbeheer{#identity-management}

Individuele bezoekers van uw website kunnen alleen worden geïdentificeerd wanneer u hun de mogelijkheid biedt zich aan te melden. Er zijn verschillende redenen waarom u een aanmeldingsfunctie wilt opgeven:

* [AEM](/help/communities/overview.md)Communitiesbezoekers van de site moeten zich aanmelden om inhoud naar de community te posten.
* [Gesloten gebruikersgroepen](/help/sites-administering/cug.md)

   Mogelijk moet u de toegang tot uw website (of gedeelten ervan) beperken tot specifieke bezoekers.

* [Personalisatie](/help/sites-administering/personalization.md) bezoekers toestaan bepaalde aspecten van hoe zij tot uw website toegang hebben te vormen.

De functionaliteit voor aanmelden (en uitloggen) wordt geleverd door een [account met een **profiel **](#profiles-and-user-accounts), dat aanvullende informatie bevat over de geregistreerde bezoeker (gebruiker). De eigenlijke registratie- en vergunningsprocedures kunnen verschillen:

* Zelfregistratie vanaf de website

   Een [Community Site](/help/communities/sites-console.md) kan zo worden geconfigureerd dat bezoekers zichzelf kunnen registreren of zich kunnen aanmelden bij hun Facebook- of Twitter-accounts.

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
>De informatie die in het profiel is opgegeven, kan ook worden gebruikt om de gebruiker gerichte inhoud te bieden via [segmenten](/help/sites-administering/campaign-segmentation.md) en [campagnes](/help/sites-classic-ui-authoring/classic-personalization-campaigns.md).

## Registratieformulieren {#registration-forms}

Met een [formulier](/help/sites-authoring/default-components.md#form-component) kunt u de registratiegegevens verzamelen en vervolgens het nieuwe account en profiel genereren.

Gebruikers kunnen bijvoorbeeld een nieuw profiel aanvragen met de pagina Geometrixx`http://localhost:4502/content/geometrixx-outdoors/en/user/register.html`

![registerform](assets/registerform.png)

Na het verzenden van de aanvraag wordt de profielpagina geopend waar de gebruiker persoonlijke gegevens kan opgeven.

![profielpagina](assets/profilepage.png)

De nieuwe account is ook zichtbaar in de [gebruikersconsole](/help/sites-administering/security.md).

## Aanmelden {#login}

De login component kan worden gebruikt om de login informatie te verzamelen, dan het login proces te activeren.

Hierdoor krijgt de bezoeker de standaardvelden **Gebruikersnaam** en **Wachtwoord**, met de knop **Aanmelden** om het aanmeldingsproces te activeren wanneer de gegevens worden ingevoerd.

Gebruikers kunnen zich bijvoorbeeld aanmelden of een nieuwe account maken met de optie **Aanmelden** op de werkbalk Geometrixx, die de pagina gebruikt:

`http://localhost:4502/content/geometrixx-outdoors/en/user/sign-in.html`

![aanmelden](assets/login.png)

## Afmelden {#logging-out}

Aangezien er een login mechanisme is, wordt een logout mechanisme ook vereist. Dit is beschikbaar als de optie **Afmelden** in Geometrixx.

## Een profiel weergeven en bijwerken {#viewing-and-updating-a-profile}

Afhankelijk van uw registratieformulier kan de bezoeker gegevens in zijn profiel hebben geregistreerd. Zij moeten dit in een later stadium kunnen bekijken en/of bijwerken. Dit kan in een vergelijkbare vorm gebeuren; bijvoorbeeld in Geometrixx:

```
http://localhost:4502/content/geometrixx-outdoors/en/user/profile.html
```

Als u de details van uw profiel wilt zien, klikt u op **Mijn profiel** in de rechterbovenhoek van een pagina. bijvoorbeeld met de `admin` account:
`http://localhost:4502/home/users/a/admin/profile.form.html/content/geometrixx-outdoors/en/user/profile.html.`

U kunt een ander profiel bekijken gebruikend de [cliëntcontext](/help/sites-administering/client-context.md) (op het auteursmilieu en met voldoende voorrechten):

1. Open een pagina; Bijvoorbeeld de pagina Geometrixx:

   `http://localhost:4502/cf#/content/geometrixx/en.html`

1. Klik op **Mijn profiel** in de rechterbovenhoek. U ziet het profiel van uw huidige account; bijvoorbeeld de beheerder.
1. Druk **controle-alt-C** om de cliëntcontext te openen.
1. Klik in de linkerbovenhoek van de clientcontext op de knop **Profiel** laden.

   ![](do-not-localize/loadprofile.png)

1. Selecteer een ander profiel in de vervolgkeuzelijst in het dialoogvenster. bijvoorbeeld **Alison Parker**.
1. Click **OK**.
1. Klik nogmaals op **Mijn profiel**. Het formulier wordt bijgewerkt met de gegevens van Alison.

   ![winstbejag](assets/profilealison.png)

1. U kunt nu Profiel **** bewerken of Wachtwoord **** wijzigen gebruiken om de gegevens bij te werken.

## Velden toevoegen aan de profieldefinitie {#adding-fields-to-the-profile-definition}

U kunt velden toevoegen aan de profieldefinitie. U kunt bijvoorbeeld het veld Favoriete kleur toevoegen aan het profiel Geometrixx:

1. Navigeer vanuit de websiteconsole naar Geometrixx Outdoor Site > Engels > Gebruiker > Mijn profiel.
1. Dubbelklik op de pagina **Mijn profiel** om deze te openen voor bewerking.
1. Vouw de sectie **Formulier** uit op het tabblad **** Componenten van sidekick.
1. Sleep een **vervolgkeuzelijst** van Help naar het formulier, net onder het veld **Over mij** .
1. Dubbelklik op de component **Vervolgkeuzelijst** om het dialoogvenster voor configuratie te openen en voer de volgende gegevens in:

   * **Naam** element - `favoriteColor`
   * **Titel** - `Favorite Color`
   * **Items** - meerdere kleuren toevoegen als items
   Klik op **OK** om op te slaan.

1. Sluit de pagina, ga terug naar de console van **Websites** en activeer de Mijn pagina van het Profiel.

   De volgende keer dat u een profiel weergeeft, kunt u een favoriete kleur selecteren:

   ![aparkerfavcolor](assets/aparkerfavcolour.png)

   Het veld wordt opgeslagen in de sectie **Profiel** van de desbetreffende gebruikersaccount:

   ![aparkercrxdeliet](assets/aparkercrxdelite.png)

## Profielstatussen {#profile-states}

Er zijn een aantal gebruiksgevallen die vereisen wetend of een gebruiker (of eerder hun profiel) in een *specifieke staat* of niet is.

Dit betekent dat een geschikte eigenschap in het gebruikersprofiel moet worden gedefinieerd:

* is zichtbaar en toegankelijk voor de gebruiker
* definieert twee statussen voor elke eigenschap
* schakelt tussen de twee gedefinieerde statussen

Dit gebeurt met:

* [Providers](#state-providers)

   De twee statussen van een specifieke eigenschap en de overgangen tussen beide beheren.

* [Workflows](#workflows)

   Handelingen met betrekking tot de staten beheren.

Er kunnen meerdere statussen worden gedefinieerd; Bijvoorbeeld in Geometrixx zijn deze:

* zich abonneren (of het afmelden) op berichten op nieuwsbrieven of commentaardraden
* een verbinding met een vriend toevoegen en verwijderen

### Providers {#state-providers}

Een staatsleverancier beheert de huidige status van het betrokken eigendom, samen met de overgangen tussen de twee mogelijke statussen.

De leveranciers van de staat worden uitgevoerd als componenten, zodat kan voor uw project worden aangepast. In Geometrixx omvatten deze:

* Onderwerp gebruikersforum/abonneeforum
* Vriend toevoegen/verwijderen

### Workflows {#workflows}

De leveranciers van de staat leiden een profielbezit en zijn staten.

Er is een workflow nodig om de acties met betrekking tot de staten uit te voeren. Als u zich bijvoorbeeld abonneert op meldingen, wordt in de workflow de actie voor het feitelijke abonnement afgehandeld. wanneer u zich niet meer abonneert op meldingen , wordt in de workflow het verwijderen van de gebruiker uit de abonnementenlijst afgehandeld .

## Profielen en gebruikersaccounts {#profiles-and-user-accounts}

Profielen worden in de inhoudsopslagplaats opgeslagen als onderdeel van[de gebruikersaccount](/help/sites-administering/user-group-ac-admin.md).

Het profiel is te vinden onder `/home/users/geometrixx`:

![chlimage_1-138](assets/chlimage_1-138.png)

Bij een standaardinstallatie (auteur of publicatie) heeft iedereen toegang tot de volledige profielgegevens van alle gebruikers. iedereen is een &quot;*ingebouwde groep die automatisch alle bestaande gebruikers en groepen bevat. De ledenlijst kan niet worden bewerkt*.&quot;

Deze toegangsrechten worden bepaald door volgende vervangingsACL:

/home: iedereen kan jcr:read rep:glob = */profile*

Dat maakt het mogelijk:

* forum, opmerkingen of blogberichten om informatie (zoals pictogram of volledige naam) weer te geven vanuit het juiste profiel
* koppelingen naar geometrixe profielpagina&#39;s

Als deze toegang niet geschikt is voor uw installatie, kunt u deze standaardinstellingen wijzigen.

U doet dit op het tabblad **[Toegangsbeheer](/help/sites-administering/user-group-ac-admin.md#access-right-management)**:

![aclmanager](assets/aclmanager.png)

## Profielcomponenten {#profile-components}

Er is ook een reeks profielcomponenten beschikbaar waarmee u de profielvereisten voor uw site kunt definiëren.

### Veld voor gecontroleerd wachtwoord {#checked-password-field}

Deze component bevat twee velden voor:

* de invoer van een wachtwoord
* een controle om te bevestigen dat het wachtwoord correct is ingevoerd.

Met standaardinstellingen wordt de component als volgt weergegeven:

![dc_profiles_checkedpassword](assets/dc_profiles_checkedpassword.png)

### Profiel Avatar Photo {#profile-avatar-photo}

Deze component biedt de gebruiker een mechanisme voor het selecteren en uploaden van een Avatar Photo-bestand.

![dc_profiles_avatarphoto](assets/dc_profiles_avatarphoto.png)

### Gedetailleerde naam profiel {#profile-detailed-name}

Met deze component kan de gebruiker een gedetailleerde naam invoeren.

![dc_profiles_detailedname](assets/dc_profiles_detailedname.png)

### Profiel Geslacht {#profile-gender}

Met deze component kan de gebruiker zijn geslacht invoeren.

![dc_profiles_gender](assets/dc_profiles_gender.png)

