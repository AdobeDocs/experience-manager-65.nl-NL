---
title: Uitgenodigde en lokale gebruikersaccounts beheren
description: Met documentbeveiliging kunt u uitgenodigde en lokale gebruikersaccounts zoeken, weergeven, bewerken, vergrendelen, ontgrendelen en verwijderen.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/working_with_document_security
products: SG_EXPERIENCEMANAGER/6.5/FORMS
feature: Document Security
exl-id: 23f71b34-a0cb-4664-bb8b-a60f33dc70d8
solution: Experience Manager, Experience Manager Forms
role: User, Developer
source-git-commit: 6a9806d8f40f711a610c130c63d9ab9b2460d075
workflow-type: tm+mt
source-wordcount: '1208'
ht-degree: 0%

---

# Uitgenodigde en lokale gebruikersaccounts beheren {#managing-invited-and-local-user-accounts}

>[!NOTE]
> 
> Zorg ervoor dat de gebruiker beheerdersrechten heeft om toegang te krijgen tot de beheerdersconsole.

Gebruik de pagina Uitgenodigde en lokale gebruikers om uw uitgenodigde en lokale gebruikers te beheren. Deze pagina wordt alleen weergegeven als aan de volgende voorwaarden is voldaan:

* U bent een beheerder aan wie de rol Uitgenodigde van het Beheer van de documentveiligheid en Lokale Gebruikers en de rol van de Gebruiker van de beleidsconsole wordt toegewezen. (Zie [ Creërend en vormend rollen ](/help/forms/using/admin-help/creating-configuring-roles.md#creating-and-configuring-roles).)
* Uitgenodigde gebruikersregistratie is ingeschakeld. (Zie [ Vormend uitgenodigde gebruikersregistratie ](/help/forms/using/admin-help/configuring-client-server-options.md#configuring-invited-user-registration).)

De pagina Uitgenodigde en Lokale gebruikers bevat twee tabbladen waarmee u uitgenodigde en lokale gebruikersaccounts kunt zoeken, weergeven, bewerken, vergrendelen, ontgrendelen en verwijderen.

U kunt ook handmatig e-mails sturen naar uitgenodigde gebruikers. U kunt dit bijvoorbeeld doen als de registratieperiode die door de e-mail is geautoriseerd, eindigt en de gebruiker de URL niet kan gebruiken om zich te registreren. In dit geval kunt u een registratiebericht opnieuw verzenden naar de uitgenodigde gebruiker. Wanneer de uitgenodigde gebruiker zich registreert en de rekening activeert, wordt de gebruiker een lokale gebruiker.

>[!NOTE]
>
>Uitgenodigde gebruikers kunnen ook rechtstreeks via de LDAP-directory worden toegevoegd die beveiligingsreferenties documenteert, of wanneer een gebruiker of beheerder een nieuwe gebruiker uitnodigt bij het maken of bewerken van een beleid en daarom een e-mail met een registratieuitnodiging start. Gebruikers kunnen nieuwe uitgenodigde gebruikers aan beleid toevoegen als u de optie Uitgenodigde gebruikersregistratie inschakelen op de Uitgenodigde pagina Gebruikersregistratie inschakelt.

## Een uitgenodigde gebruiker toevoegen {#add-an-invited-user}

U kunt een of meer uitgenodigde gebruikersaccounts tegelijk toevoegen aan de documentbeveiliging. Als u een uitgenodigde gebruikersaccount wilt toevoegen, hebt u het e-mailadres van de gebruiker nodig. Wanneer u een gebruiker toevoegt, verzendt de documentbeveiliging een registratie-e-mail waarin de gebruiker wordt uitgenodigd zich te registreren.

1. Klik in de beheerconsole op Services > Documentbeveiliging > Uitgenodigde en lokale gebruikers en klik vervolgens op Nieuwe gebruiker uitnodigen.
1. Typ het e-mailadres van de gebruikers die u wilt uitnodigen. Voer meerdere adressen op een regel in, gescheiden door een komma.

   Het bericht dat u hebt gemaakt toen u de uitgenodigde gebruikersregistratie inschakelde, wordt naar de gebruikers verzonden. (Zie [ Vormend uitgenodigde gebruikersregistratie ](/help/forms/using/admin-help/configuring-client-server-options.md#configuring-invited-user-registration).)

1. Klik op OK.

## Informatie weergeven over een lokale gebruiker {#view-information-about-a-local-user}

U kunt informatie weergeven over lokale gebruikers, zoals naam, e-mailadres, organisatie, registratiestatus en domein.

1. Klik in de beheerconsole op Services > Documentbeveiliging > Uitgenodigde en lokale gebruikers en klik vervolgens op Nieuwe gebruiker uitnodigen.
1. Klik op het tabblad Lokale gebruikers en klik op de pagina Lokale gebruikers beheren op het e-mailadres voor de gebruiker die u wilt weergeven.

   De gebruikersgegevens worden weergegeven en u kunt het wachtwoord van de gebruiker opnieuw instellen en het account deactiveren.

## Een e-mail verzenden naar een niet-geregistreerde externe gebruiker {#send-an-email-to-an-unregistered-external-user}

Wanneer u een uitgenodigde gebruiker toevoegt, verzendt de documentveiligheid automatisch een registratie-e-mailverzoek. U kunt ook handmatig een registratie-e-mailbericht genereren dat wordt verzonden naar een uitgenodigde gebruiker die zich nog niet heeft geregistreerd. U kunt dit bijvoorbeeld doen om een nieuwe uitnodiging te verzenden als de registratie-e-mail van een uitgenodigde gebruiker verloopt.

1. Klik in de beheerconsole op Services > Documentbeveiliging > Uitgenodigde en lokale gebruikers.
1. Schakel in de gebruikerslijst het selectievakje in waarnaar elke gebruiker een registratiebericht verzendt en klik op Uitnodiging-e-mail opnieuw verzenden.
1. Controleer de lijst met geselecteerde gebruikers en klik op OK.

## Een lokaal gebruikerswachtwoord opnieuw instellen {#reset-a-local-user-password}

U kunt wachtwoorden opnieuw instellen voor geactiveerde uitgenodigde gebruikers die zich bij documentveiligheid hebben geregistreerd maar hun wachtwoord vergeten. Wanneer u een wachtwoord opnieuw instelt, wordt een e-mail geproduceerd die een nieuw, tijdelijk wachtwoord voor de gebruiker bevat.

Wanneer u het registratieproces voor uitgenodigde gebruikers hebt ingeschakeld, hebt u een e-mailbericht gemaakt dat wordt verzonden naar gebruikers die hen vragen hun wachtwoorden opnieuw in te stellen. (Zie [ Vormend uitgenodigde gebruikersregistratie ](/help/forms/using/admin-help/configuring-client-server-options.md#configuring-invited-user-registration).)

1. Klik in de beheerconsole op Services > Documentbeveiliging > Uitgenodigde en lokale gebruikers en klik op het tabblad Lokale gebruikers.
1. Selecteer de gewenste gebruiker in de gebruikerslijst.
1. Klik op de pagina Lokale gebruiker beheren op Wachtwoord opnieuw instellen en klik op OK. Er wordt een e-mail met het wachtwoord voor opnieuw instellen met het nieuwe wachtwoord verzonden naar de gebruiker.

## Gebruikersaccounts in- of uitschakelen {#enable-or-disable-a-user-account}

U kunt lokale gebruikersaccounts uitschakelen om tijdelijk te voorkomen dat een gebruiker zich aanmeldt bij de documentbeveiliging. Wanneer u de account uitschakelt, kan de gebruiker geen documenten met een beleid gebruiken of beleidsregels maken of toepassen.

U kunt een lokale gebruikersaccount inschakelen die momenteel is uitgeschakeld. U kunt een uitgenodigde gebruikersrekening niet toelaten die als geregistreerd wordt vermeld. De geregistreerde status geeft aan dat de uitgenodigde gebruiker is geregistreerd, maar de account nog niet heeft geactiveerd via de koppeling in het activeringsbericht.

**Beperk een gebruikersrekening**

1. Klik in Beheerconsole op Services > Documentbeveiliging > Uitgenodigde en lokale gebruikers en klik op het tabblad Lokale gebruikers.
1. Selecteer de gewenste gebruiker in de gebruikerslijst.
1. Klik op Account uitschakelen op de pagina Details lokale gebruiker.

**herstelt een gebruikersrekening**

1. Klik op Uitgenodigd en Lokale gebruikers en klik op het tabblad Lokale gebruikers.
1. Selecteer de gewenste gebruiker in de gebruikerslijst.
1. Klik op de pagina Details lokale gebruiker op Account inschakelen.

## Een uitgenodigde gebruikersaccount verwijderen {#remove-an-invited-user-account}

U kunt uitgenodigde gebruikersrekeningen van documentveiligheid schrappen. U kunt bijvoorbeeld een account verwijderen wanneer een gebruiker zijn persoonlijke e-mailaccountgegevens wijzigt.

Als u een gebruikersaccount verwijdert, kan alleen u of een andere beheerder de account opnieuw instellen door de optie Uitgenodigde gebruiker toevoegen op de pagina Uitgenodigde gebruikers te selecteren. De gebruikers kunnen niet de geschrapte gebruikersrekening aan een beleid toevoegen, en geen uitnodigingsproces kan door die methode worden in werking gesteld.

>[!NOTE]
>
>Uitgenodigde gebruikers die zijn verwijderd via de gebruikersbeheerinterface van AEM formulieren, kunnen pas opnieuw worden uitgenodigd als ze opnieuw zijn verwijderd via de volgende procedure.

1. Klik in de beheerconsole op Services > Documentbeveiliging > Uitgenodigde en lokale gebruikers en klik op het tabblad Uitgenodigde gebruikers.
1. Schakel het selectievakje naast een of meer gebruikers in, klik op Verwijderen en klik op OK.

## Zoeken naar een uitgenodigde gebruikersaccount {#search-for-an-invited-user-account}

U kunt op uitgenodigde gebruikersrekeningen zoeken door een e-mailadres te gebruiken.

1. Klik in de beheerconsole op Services > Documentbeveiliging > Uitgenodigde en lokale gebruikers.
1. Typ het e-mailadres van de gebruiker in het vak Zoeken in en klik op Zoeken.

## Zoeken naar een lokale gebruikersaccount {#search-for-a-local-user-account}

U kunt naar een lokale gebruiker zoeken door het e-mailadres of de naam en het domein van de gebruiker te gebruiken.

1. Klik in de beheerconsole op Services > Documentbeveiliging > Uitgenodigde en lokale gebruikers en klik op het tabblad Lokale gebruikers.
1. Typ de zoekcriteria in het vak Zoeken, selecteer Naam of E-mail en klik op Zoeken.

## Een lokale gebruikersaccount verwijderen {#remove-a-local-user-account}

U kunt lokale gebruikersaccounts verwijderen uit de documentbeveiliging. U kunt bijvoorbeeld accounts verwijderen wanneer gebruikers hun persoonlijke e-mailaccountgegevens wijzigen.

1. Klik in de beheerconsole op Services > Documentbeveiliging > Uitgenodigde en lokale gebruikers en klik op het tabblad Lokale gebruikers.
1. Schakel het selectievakje naast een of meer gebruikers in, klik op Verwijderen en klik op OK.

## De gebruikerslijst sorteren {#sort-the-user-list}

U kunt gebruikers gemakkelijker vinden door de gebruikerslijst door kolomrubriek te sorteren. Driehoekpictogrammen naast de kolomkop geven aan welke kolom momenteel wordt gebruikt voor sorteren:

* Een naar boven wijzend driehoekje geeft de oplopende volgorde aan.
* Een naar beneden wijzend driehoekje geeft een aflopende volgorde aan.

   1. Klik in de beheerconsole op Services > Documentbeveiliging > Uitgenodigde en lokale gebruikers.
   1. Als u uitgenodigde gebruikers wilt sorteren, klikt u op het tabblad Uitgenodigde gebruikers en klikt u op de gewenste kolomkop.
   1. Als u lokale gebruikers wilt sorteren, klikt u op het tabblad Lokale gebruikers en klikt u op de gewenste kolomkop.
