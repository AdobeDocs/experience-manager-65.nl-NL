---
title: Just-in-Time gebruikersprovisioning
seo-title: Just-in-Time gebruikersprovisioning
description: Gebruik just-in-time levering om gebruikers aan het Beheer van de Gebruiker toe te voegen na succesvolle authentificatie en dynamisch relevante rollen en groepen aan de nieuwe gebruiker toe te wijzen.
seo-description: Gebruik just-in-time levering om gebruikers aan het Beheer van de Gebruiker toe te voegen na succesvolle authentificatie en dynamisch relevante rollen en groepen aan de nieuwe gebruiker toe te wijzen.
uuid: a5ad4698-70bb-487b-a069-7133e2f420c2
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/setting_up_and_organizing_users
products: SG_EXPERIENCEMANAGER/6.5/FORMS
discoiquuid: e80c3f98-baa1-45bc-b713-51a2eb5ec165
translation-type: tm+mt
source-git-commit: 1343cc33a1e1ce26c0770a3b49317e82353497ab
workflow-type: tm+mt
source-wordcount: '599'
ht-degree: 0%

---


# Just-in-Time gebruikersprovisioning {#just-in-time-user-provisioning}

AEM formulieren ondersteunen de just-in-time levering van gebruikers die nog niet in Gebruikersbeheer bestaan. Met just-in-time levering, worden de gebruikers automatisch toegevoegd aan het Beheer van de Gebruiker nadat hun geloofsbrieven met succes voor authentiek worden verklaard. Daarnaast worden relevante rollen en groepen dynamisch toegewezen aan de nieuwe gebruiker.

## Behoefte aan just-in-time gebruikerslevering {#need-for-just-in-time-user-provisioning}

Zo werkt traditionele verificatie:

1. Wanneer een gebruiker zich aanmeldt bij AEM formulieren, geeft Gebruikersbeheer de gebruikersgegevens opeenvolgend door aan alle beschikbare verificatieproviders. (De login geloofsbrieven omvatten een gebruikersbenaming/wachtwoordcombinatie, kaartje Kerberos, handtekening PKCS7, etc.)
1. De verificatieprovider valideert de referenties.
1. De authentificatieleverancier controleert dan of de gebruiker in het gegevensbestand van het Beheer van de Gebruiker bestaat. De volgende resultaten zijn mogelijk:

   **Bestaat:** Als de gebruiker huidig en ontgrendeld is, keert het Beheer van de Gebruiker authentificatiesucces terug. Als de gebruiker echter niet actief is of is vergrendeld, retourneert het Gebruikersbeheer een verificatiefout.

   **Bestaat niet:** gebruikersbeheer retourneert verificatiefout.

   **Ongeldig:** gebruikersbeheer retourneert verificatiefout.

1. Het resultaat dat door de authentificatieleverancier is teruggekeerd wordt geëvalueerd. Als de verificatieprovider het succes van de verificatie heeft geretourneerd, mag de gebruiker zich aanmelden. Anders, controleert het Beheer van de Gebruiker met de volgende authentificatieleverancier (stappen 2-3).
1. Verificatiefout wordt geretourneerd als geen enkele verificatieprovider de gebruikersgegevens valideert.

Wanneer just-in-time levering wordt uitgevoerd, wordt een nieuwe gebruiker dynamisch gecreeerd in het Beheer van de Gebruiker als één van de authentificatieleveranciers de geloofsbrieven van de gebruiker bevestigt. (Na stap 3 in de traditionele authentificatieprocedure, hierboven.)

## Pas-in-tijd gebruikersinrichting {#implement-just-in-time-user-provisioning} uitvoeren

### API&#39;s voor just-in-time provisioning {#apis-for-just-in-time-provisioning}

AEM formulieren bevatten de volgende API&#39;s voor instelbare provisioning:

```java
package com.adobe.idp.um.spi.authentication  ;
publ ic interface IdentityCreator {
/**
* Tries  to create a user with the  in formation  provided in the <code>UserProvisioningBO</code> object.
* If the user is successfully created, a valid AuthResponse is returned along with the information using which the user was created.
* It is the responsibility of the IdentityCreator to set the User obje ct  in the cre dential map with th e  ke y  <code>UMA u thenticationUtil.authenticatedUserKey</code>
* The credentials are available in the <code>UserProvisioningBO</code> object in the 'credentials' property.
* If the IdentityCreator is unable to create a user due to any reason, it returns <code>null</code>
* @param userBO An object of <code>com.adobe. i dp.um . spi.authenti c ationUserProvisioningBO</code>
* @return */public AuthResponse create(UserProvisioningBO userBO);
/**
* Returns the name of the IdentityCreator which will be registered in preferences.
* This name is used to associate the IdentityProvider with the Auth Provider Configuration in the domain.
* @return The name of the Identity Creator which is recognized in Configuration.
*/
public String getName();
}
package com.adobe.idp.um.spi.authentication;
import com.adobe.idp.um.api.infomodel.User;
public interface AssignmentProvider {
/**
* Tries to assign roles or permissions or group memberships to users created via Just-in-time provisioning.
* @param user The User created via the Just-in-time provisioning process.
* @return a Boolean flag indicating whether the assignment was successful or not.
*/
public Boolean assign(User user);
/**
* Returns the name of the AssignmentProvider through which it is registered under preferences.
* This name is used to associate the AssignmentProvider with the Auth Provider Configuration in the domain.
* @return The name of the AssignmentProvider which is recognized in Configuration.
*/public String getName();
}
```

### Overwegingen bij het creëren van een just-in-time-Toegelaten domein {#considerations-while-creating-a-just-in-time-enabled-domain}

* Zorg er tijdens het maken van een aangepaste `IdentityCreator` voor een hybride domein voor dat er een dummywachtwoord is opgegeven voor de lokale gebruiker. Laat dit wachtwoordveld niet leeg.
* Aanbeveling: Gebruik `DomainSpecificAuthentication` om gebruikersgeloofsbrieven tegen een specifiek domein te bevestigen.

### Creeer een enkel-in-tijd-toegelaten domein {#create-a-just-in-time-enabled-domain}

1. Schrijf een DSC die APIs in &quot;APIs voor just-in-time levering&quot;sectie uitvoert.
1. Implementeer de DSC op de formulierserver.
1. Creeer een just-in-time-Toegelaten domein:

   * Klik in Beheerconsole op Instellingen > Gebruikersbeheer > Domeinbeheer > Nieuw Enterprise-domein.
   * Configureer het domein en selecteer Enable Just In Time Provisioning. <!--Fix broken link (See Setting up and managing domains).-->
   * Voeg verificatieproviders toe. Tijdens het toevoegen van authentificatieleveranciers, op het Nieuwe scherm van de Authentificatie, selecteer een geregistreerde Maker van de Identiteit en een Leverancier van de Toewijzing.

1. Sla het nieuwe domein op.

## Achter de scènes {#behind-the-scenes}

Stel dat een gebruiker zich probeert aan te melden bij AEM formulieren en dat een verificatieprovider zijn gebruikersgegevens accepteert. Als de gebruiker nog niet bestaat in de gebruikersbeheerdatabase, mislukt de identiteitscontrole voor de gebruiker. AEM formulieren voeren nu de volgende handelingen uit:

1. Maak een `UserProvisioningBO`-object met de verificatiegegevens en plaats dit in een referentie-overzicht.
1. Gebaseerd op domeininformatie die door `UserProvisioningBO` is teruggekeerd, haal en haal geregistreerd `IdentityCreator` en `AssignmentProvider` voor het domein aan.
1. `IdentityCreator` aanroepen. Als het succesvol `AuthResponse` terugkeert, haal `UserInfo` van de referentie kaart. Geef deze door aan `AssignmentProvider` voor groep/rol-toewijzing en elke andere nabewerking nadat de gebruiker is gemaakt.
1. Als de gebruiker met succes is gemaakt, retourneert u de aanmeldingspoging van de gebruiker als geslaagd.
1. Voor hybride domeinen, trek gebruikersinformatie van de authentificatiegegevens die aan de authentificatieleverancier worden verstrekt. Als deze gegevens correct zijn opgehaald, maakt u de gebruiker ter plekke.

>[!NOTE]
>
>De just-in-time provisioning-functie wordt geleverd met een standaardimplementatie van `IdentityCreator` die u kunt gebruiken om dynamisch gebruikers te maken. De gebruikers worden gecreeerd met de informatie verbonden aan de folders in het domein.

