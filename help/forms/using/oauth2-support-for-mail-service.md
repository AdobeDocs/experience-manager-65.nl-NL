---
title: OAuth2 Steun voor de Dienst van de Post
description: 'Oauth2 Steun voor de Dienst van de Post  '
source-git-commit: 081b0c70ceca0502cb84d7e1b68b0b12dc45a4e7
workflow-type: tm+mt
source-wordcount: '690'
ht-degree: 0%

---

# OAuth2 Steun voor de Dienst van de Post {#oauth2-support-for-the-mail-service}

AEM as a Cloud Service biedt OAuth2-ondersteuning voor zijn geïntegreerde e-mailservice, zodat organisaties zich aan de vereisten voor e-mail kunnen houden.

U kunt OAuth voor veelvoudige e-mailleveranciers vormen. Hieronder zijn geleidelijke instructies voor het vormen van de AEMDienst van de Post via OAuth2 met Microsoft Office 365 Vooruitzichten voor authentiek te verklaren. Andere verkopers kunnen op een gelijkaardige manier worden gevormd.

## Microsoft Outlook {#microsoft-outlook}

1. Ga naar [https://portal.azure.com/](https://portal.azure.com/) en aanmelden.
1. Zoeken naar **Azure Active Directory** in de zoekbalk en klik op het resultaat. U kunt ook rechtstreeks bladeren naar [https://portal.azure.com/#blade/Microsoft_AAD_IAM/ActiveDirectoryMenuBlade/Overview](https://portal.azure.com/#blade/Microsoft_AAD_IAM/ActiveDirectoryMenuBlade/Overview)
1. Klikken op **Toepassingsregistratie** - **Nieuwe registratie**

   ![](/help/forms/using/assets/outh_outlook.PNG)

1. Vul de gegevens naar wens in en klik op **Registreren**
1. Ga naar de nieuwe app en selecteer **API-machtigingen**
1. Ga naar **Machtiging toevoegen** - **Grafiekmachtigingen** - **Gedelegeerde machtigingen**
1. Selecteer de onderstaande machtigingen voor uw app en klik op **Machtiging toevoegen**:
   * `SMTP.Send`
   * `Mail.Read`
   * `Mail.Send`
   * `openid`
   * `offline_access`
1. Ga naar **Verificatie** - **Een platform toevoegen** - **Web** en in de **URL omleiden** de volgende URL&#39;s toevoegen: één met en één zonder een slash:
   * `http://localhost/`
   * `http://localhost`
1. Druk **Configureren** na het toevoegen van elke URL en het configureren van uw instellingen volgens uw vereisten
1. Ga vervolgens naar **Certificaten en geheimen**, klikt u op **Nieuw clientgeheim** en volg de stappen op het scherm om een geheim te maken. Let op dit geheim voor later gebruik
1. Druk **Overzicht** in het linkerdeelvenster en kopieer de waarden voor **Toepassings-id (client)** voor later gebruik.

Om opnieuw te verpakken, vereist u de volgende informatie om OAuth2 voor de dienst van de Post op de AEM kant te vormen:

* De Auth URL in de vorm: `https://login.microsoftonline.com/<ID>/oauth2/v2.0/authorize`
* De token-URL in het formulier: `https://login.microsoftonline.com/<ID>/oauth2/v2.0/token`
* De URL vernieuwen in het formulier: `https://login.microsoftonline.com/<ID>/oauth2/v2.0/token`
* Client-id
* Het clientgeheim

### Het genereren van het token Vernieuwen {#generating-the-refresh-token}

Vervolgens moet u het vernieuwingstoken genereren, zoals in een volgende stap wordt geïllustreerd.

U kunt dit doen door deze stappen te volgen:

1. Open de volgende URL in de browser nadat u deze hebt vervangen `clientID` met de specifieke waarden voor uw account:

   ```https://login.microsoftonline.com/common/oauth2/v2/authorize?client_id=<client_id>&scope=IMAP.AccessAsUser.A;;%20POP.AccessAsUser.All%20SMTP.Send%20User.Read&response_type=code&redirect-uri=http://loginmicrosoftonline.com/common/outh2/nativeclient&prompt=login```

1. Toestemming verlenen, waar dit ooit nodig is.
1. De URL wordt omgeleid naar een nieuwe locatie, in de volgende indeling: `http://localhost/?code=<code>&state=12345&session_state=4f984c6b-cc1f-47b9-81b2-66522ea83f81#`
1. Kopieer de waarde van `<code>` in het bovenstaande voorbeeld
1. Gebruik het volgende cURL bevel om te krijgen refreshToken. Vervang de clientID, clientSecret door de waarden voor uw account en de waarde voor `<code>`:

   ```
   curl -H “ContentType application/x-www-form-urlencoded” -d 
   "client_id=<client-id>
   &scope=https%3A%2F%2Foutlook.office.com%2FIMAP.AccessAsUser.All&code=M.R3_BAY.1bf609bf-25b3-2fcd-d910-02e02c53bc
   &grant_type=authorization_code
   &redirect_uri= https://login.microsoftonline.com/common/oauth2/nativeclient
   &client_secret=~1E8Q~cz-m6vgOb9m~SI.eF9jSVTbFUiP5f0” -X POST https://login.microsoftonline.com/common/oauth2/v2.0/token
   ```

1. Noteer refreshToken en accessToken.

### Tokens valideren {#validating-the-tokens}

Alvorens te werk te gaan om OAuth op de AEM kant te vormen, zorg ervoor om zowel accessToken als refreshToken met de hieronder procedure te bevestigen:

1. Genereer accessToken door te gebruiken vernieuwtToken in de vorige procedure wordt geproduceerd die. U kunt dit bereiken door de waarden voor `<client_id>`,`<client_secret>` samen met de `<refreshToken>`:

   ```
   curl -H “ContentType application/x-www-form-urlencoded” -d 
   "client_id=<client_id>
   &scope=https%3A%2F%2Foutlook.office.com%2FIMAP.AccessAsUser.All&code=<code>
   &grant_type=authorization_code
   &redirect_uri= https://login.microsoftonline.com/common/oauth2/nativeclient
   &client_secret=<client_secret>
   &refresh_token=<refresh_token” 
   -X POST https://login.microsoftonline.com/common/oauth2/v2.0/token
   ```

1. Verzend een post gebruikend accessToken, om te zien of werkt het behoorlijk.

>[!NOTE]
>
> U kunt de Postman API-verzameling ophalen vanuit [deze locatie](https://docs.microsoft.com/en-us/azure/active-directory/develop/v2-oauth2-auth-code-flow).

### E-mailservice configureren met ondersteuning voor Auth2.0 {#configureemailservice}

Nu moet u de e-mailservice op de nieuwste JEE-server configureren door u aan te melden in de interface van Admin:

1. Ga naar **Home** - **Service** - **Toepassingen en services** - **Servicebeheer** - **E-mailservice**
1. **Configuratie-e-mailservice** venster verschijnt, configureren **SMPT** en **IMP** servers voor basisverificatie.
1. Om de dienst van de de postauthentificatie van Vooruitzichten toe te laten, selecteer **Verificatie-instellingen augustus 2.0** selectievakje.
1. De waarden kopiëren van **Client-id** en **Clientgeheim** vanuit Azure Portal.
1. Kopieer de waarde van gegenereerd **Token vernieuwen**.
1. Klikken **Opslaan** om de details op te slaan.
1. Aanmelden bij werkbank en zoeken **E-mail 1.0** van **Activiteitenkiezer**.
1. Onder E-mail 1.0 zijn drie opties beschikbaar als:
   * **Verzenden met document**: Verzendt e-mail met één bijlage.
   * **Verzenden met kaart met bijlagen**: Hiermee verzendt u e-mail met meerdere bijlagen.
   * **Ontvangen**: Ontvangt een e-mail van POP3 of IMAP.
1. Test de toepassing door **Verzenden met document**
1. Verlenen **TO** en **Van** adressen.
1. Roep de toepassing aan en e-mail wordt verzonden gebruikend de authentificatie Auth2.0.

>[!NOTE]
>
> Als u Auth 2.0 authentificatie wilt veranderen die aan basisauthentificatie voor een bepaald proces in een werkbank plaatst, kunt u uncheck **Auth2.0-verificatie** selectievakje onder **Algemene instellingen gebruiken** in de **Verbindingsinstellingen** tab.

### Problemen oplossen {#troubleshooting}

Als de mailservice niet goed werkt, genereert u de `refreshToken` zoals hierboven beschreven. Het duurt een paar minuten voordat de nieuwe waarde is geïmplementeerd.


