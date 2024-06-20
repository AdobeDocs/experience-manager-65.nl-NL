---
title: Op OAuth2 gebaseerde verificatie configureren voor Microsoft® (Forms JEE OAuth); Office 365-mailserverprotocollen
description: Op OAuth2 gebaseerde verificatie configureren voor Microsoft® (Forms JEE OAuth); Office 365-mailserverprotocollen
exl-id: cd3da71f-892c-4fde-905f-71a64fb5d4e4
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
role: User, Developer
source-git-commit: 539da06db98395ae6eaee8103a3e4b31204abbb8
workflow-type: tm+mt
source-wordcount: '986'
ht-degree: 0%

---

# AEM Forms integreren met Microsoft® Office 365-mailserverprotocollen {#oauth2-support-for-the-microsoft-mail-server-protocols}

AEM Forms biedt OAuth 2.0-ondersteuning voor integratie met Microsoft® Office 365-mailserverprotocollen zodat organisaties zich kunnen houden aan de vereisten voor e-mail. U kunt de Azure Actieve Folder (Azure AD) OAuth 2.0 authentificatieservice gebruiken, om met diverse protocollen zoals IMAP, POP, of SMTP te verbinden en tot e-mailgegevens voor Bureau 365 toegang te hebben gebruikers. Hieronder vindt u stapsgewijze instructies voor het configureren van de Microsoft® Office 365-mailserverprotocollen voor verificatie via de OAuth 2.0-service:

1. Aanmelden bij [https://portal.azure.com/](https://portal.azure.com/) en zoek naar **Azure Active Directory** in de zoekbalk en klik op het resultaat.
U kunt ook rechtstreeks bladeren naar [https://portal.azure.com/#blade/Microsoft_AAD_IAM/ActiveDirectoryMenuBlade/Overview](https://portal.azure.com/#blade/Microsoft_AAD_IAM/ActiveDirectoryMenuBlade/Overview)
1. Klikken **Toevoegen** > **Toepassingsregistratie** > **Nieuwe registratie**.

   ![Toepassingsregistratie](/help/forms/using/assets/outh_outlook_microsoft_azure.png)

1. Vul de gegevens naar wens in en klik op **Registreren**.
   ![Ondersteunde account](/help/forms/using/assets/azure_suuportedaccountype.png)
In het bovenstaande geval: **Accounts in any organizational directory (Any Azure AD directory - Multihuurder) en persoonlijke Microsoft® accounts (bijvoorbeeld Skype, Xbox)** is geselecteerd.

   >[!NOTE]
   >
   > * Voor **Accounts in any organizational directory (Any Azure AD directory - Multihuurder)** toepassing, raadt de Adobe u aan een werkaccount te gebruiken in plaats van een persoonlijke e-mailaccount.
   > * **Alleen persoonlijke Microsoft®-accounts** toepassing wordt niet ondersteund.
   > * Adobe raadt u aan de **Microsoft®-account voor meerdere gebruikers en personen** toepassing.

1. Ga vervolgens naar **Certificaten en geheimen**, klikt u op **Nieuw clientgeheim** en volg de stappen op het scherm om een geheim te maken. Let erop dat u deze waarde van het geheim opneemt voor later gebruik.

   ![Geheime sleutel](/help/forms/using/assets/azure_secretkey.png)

1. Ga voor het toevoegen van machtigingen naar de nieuwe app en selecteer **API-machtigingen** > **Machtiging toevoegen** > **Microsoft® Graph** > **Gedelegeerde machtigingen**.
1. Selecteer de selectievakjes voor de onderstaande machtigingen voor de app en klik op **Machtiging toevoegen**:

   * `IMAP.AccessUser.All`
   * `Mail.Read`
   * `offline_access`
   * `POP.AccessAsUser.All`
   * `SMTP.Send`
   * `User.Read`

   ![API-machtiging](/help/forms/using/assets/azure_apipermission.png)

1. Selecteren **Verificatie** > **Een platform toevoegen** > **Web** en in de **URL omleiden** sectie, voeg om het even welke hieronder URIs (Universele Herkenningsteken van het Middel) toe als:
   * `https://login.microsoftonline.com/common/oauth2/nativeclient`
   * `http://localhost`

   In dit geval: `https://login.microsoftonline.com/common/oauth2/nativeclient` wordt gebruikt als een omleidings-URI.

1. Klikken **Configureren** na het toevoegen van elke URL en het configureren van uw instellingen volgens uw vereisten.
   ![URI omleiden](/help/forms/using/assets/azure_redirecturi.png)

   >[!NOTE]
   >
   > Het is verplicht **Toegangstokens** en **ID-tokens** selectievakjes.

1. Klikken **Overzicht** in het linkerdeelvenster en kopieer de waarden voor **Toepassings-id (client)**, **Directory (huurder)-id**, en **Clientgeheim** voor later gebruik.

   ![Overzicht](/help/forms/using/assets/azure_overview.png)

## De machtigingscode genereren {#generating-the-authorization-code}

Vervolgens moet u de machtigingscode genereren, zoals in de volgende stappen wordt uitgelegd:

1. Open de volgende URL in de browser nadat u deze hebt vervangen `clientID` met de `<client_id>` en `redirect_uri` met de URI voor omleiding van uw toepassing:

   ```https://login.microsoftonline.com/common/oauth2/v2.0/authorize?client_id=[clientid]&scope=IMAP.AccessAsUser.All%20POP.AccessAsUser.All%20SMTP.Send%20User.Read%20Mail.Read%20offline_access&response_type=code&redirect_uri=[redirect_uri]&prompt=login```

   >[!NOTE]
   >
   > Als er de enige huurderstoepassing is, vervang `common` met uw `[tenantid]` in de volgende URL voor het genereren van machtigingscode: `https://login.microsoftonline.com/[tenantid]/oauth2/v2.0/authorize?client_id=[[clientid]]&scope=IMAP.AccessAsUser.All%20POP.AccessAsUser.All%20SMTP.Send%20User.Read%20Mail.Read%20openid%20offline_access&response_type=code&redirect_uri=[redirect_uri]&prompt=login`

1. Wanneer u de bovenstaande URL typt, wordt u omgeleid naar het aanmeldingsscherm:
   ![Aanmeldingsscherm](/help/forms/using/assets/azure_loginscreen.png)

1. Voer het e-mailbericht in en klik op **Volgende** en het toepassingsmachtigingsscherm wordt weergegeven:

   ![Machtiging toestaan](/help/forms/using/assets/azure_permission.png)

1. Wanneer u toestemming toestaat, wordt u opnieuw gericht aan een nieuwe URL als: `https://login.microsoftonline.com/common/oauth2/nativeclient?code=<code>&session_state=[session_id]`

1. De waarde kopiëren van `<code>` vanaf de bovenstaande URL vanaf `0.ASY...` tot `&session_state` in de bovenstaande URL.

## Het genereren van het token Vernieuwen {#generating-the-refresh-token}

Vervolgens moet u het vernieuwingstoken genereren. Dit wordt in de volgende stappen uitgelegd:

1. Open de bevelherinnering en gebruik het volgende cURL bevel om te verfrissen Token te krijgen.

1. Vervang de `clientID`, `client_secret`, en `redirect_uri` met de waarden voor uw toepassing samen met de waarde van `<code>`:

   `curl -H "ContentType application/x-www-form-urlencoded" -d "client_id=[client-id]&scope=https%3A%2F%2Foutlook.office.com%2FIMAP.AccessAsUser.All%20https%3A%2F%2Foutlook.office.com%2FPOP.AccessAsUser.All%20https%3A%2F%2Foutlook.office.com%2FSMTP.Send%20https%3A%2F%2Foutlook.office.com%2FUser.Read%20https%3A%2F%2Foutlook.office.com%2FMail.Read%20offline_access&code=[code]&grant_type=authorization_code&redirect_uri=[redirect_uri]&client_secret=[secretkey_value]" -X POST https://login.microsoftonline.com/common/oauth2/v2.0/token`

   >[!NOTE]
   >
   > In één huurderstoepassing, om te produceren verfrist me gebruik het volgende cURL bevel en vervangt `common` met de `[tenantid]` in:
   >`curl -H "ContentType application/x-www-form-urlencoded" -d "client_id=[client-id]&scope=https%3A%2F%2Foutlook.office.com%2FIMAP.AccessAsUser.All%20https%3A%2F%2Foutlook.office.com%2FPOP.AccessAsUser.All%20https%3A%2F%2Foutlook.office.com%2FSMTP.Send%20https%3A%2F%2Foutlook.office.com%2FUser.Read%20https%3A%2F%2Foutlook.office.com%2FMail.Read%20offline_access&code=[code]&grant_type=authorization_code&redirect_uri=[redirect_uri]&client_secret=[secretkey_value]" -X POST https://login.microsoftonline.com/[tenantid]/oauth2/v2.0/token`

1. Noteer het token voor vernieuwen.

## E-mailservice configureren met OAuth 2.0-ondersteuning {#configureemailservice}

Configureer nu de e-mailservice op de nieuwste JEE-server door u aan te melden bij de beheerinterface:

1. Ga naar **Home** > **Service** > **Toepassingen en services** > **Servicebeheer** > **Email Service** de **Configuratie-e-mailservice** wordt weergegeven, geconfigureerd voor basisverificatie.

   >[!NOTE]
   >
   > Als u Auth 2.0-verificatieservice wilt inschakelen, moet u **Of de server SMTP authentificatie (SMTP voor authentiek verklaart) vereist** selectievakje.

1. Set **Verificatie-instellingen augustus 2.0** als `True`.
1. De waarden kopiëren van **Client-id** en **Clientgeheim** vanuit Azure Portal.
1. Kopieer de waarde van de gegenereerde **Token vernieuwen**.
1. Aanmelden bij **Workbench** en zoeken **E-mail 1.0** van **Activiteitenkiezer**.
1. Onder E-mail 1.0 zijn drie opties beschikbaar als:
   * **Verzenden met document**: verzendt e-mail met één bijlage.
   * **Verzenden met kaart met bijlagen**: verzendt e-mail met meerdere bijlagen.
   * **Ontvangen**: Ontvangt een e-mail van IMAP.

   >[!NOTE]
   >
   >* Het protocol van de Veiligheid van het Vervoer heeft de volgende geldige waarden: &quot;leeg&quot;, &quot;SSL&quot;of &quot;TLS&quot;. Waarden instellen voor **SMTP-transportbeveiliging** en **Vervoersbeveiliging ontvangen** tot **TLS** voor het toelaten van de authentificatiedienst van de Auth.
   >* **POP3-protocol** wordt niet ondersteund voor OAuth bij het gebruik van e-maileindpunten.

   ![Verbindingsinstellingen](/help/forms/using/assets/oauth_connectionsettings.png)

1. Test de toepassing door **Verzenden met document**.
1. Verlenen **TO** en **Van** adressen.
1. Roep de toepassing aan en er wordt een e-mail verzonden met de verificatie van 0 augustus 2.0.

   >[!NOTE]
   >
   >Indien gewenst, kunt u Auth 2.0 authentificatie veranderen die aan basisauthentificatie voor een bepaald proces in een werkbank plaatst. Stel hiertoe de **OAuth 2.0-verificatie** waarde als &#39;False&#39; onder **Algemene instellingen gebruiken** in de **Verbindingsinstellingen** tab.

## Taken verifiëren inschakelen {#enable_oauth_task}

1. Ga naar **Home** > **Services** > **Formulierworkflow** > **Serverinstellingen** > **E-mailinstellingen**
1. Als u Auth-taakmeldingen wilt inschakelen, selecteert u de optie **Auth inschakelen** selectievakje.
1. De waarden kopiëren van **Client-id** en **Clientgeheim** vanuit Azure Portal.
1. Kopieer de waarde van de gegenereerde **Token vernieuwen**.
1. Klikken **Opslaan** om de details op te slaan.

   ![Taakmelding](/help/forms/using/assets/task_notification.png)

   >[!NOTE]
   >
   > Meer informatie over taakmeldingen te verkrijgen, [klik hier](https://experienceleague.adobe.com/docs/experience-manager-65/content/forms/administrator-help/configuring-email-endpoints.html#create-an-email-endpoint-for-the-complete-task-service).

## Om e-maileindpunt te vormen {#configure_email_endpoint}

1. Ga naar **Home** > **Services** > **Toepassingen en services** > **Endpoint Management**
1. E-maileindpunt configureren **Verificatie-instellingen augustus 2.0** als `True`.
1. De waarden kopiëren van **Client-id** en **Clientgeheim** vanuit Azure Portal.
1. Kopieer de waarde van de gegenereerde **Token vernieuwen**.
1. Klikken **Opslaan** om de details op te slaan.

   ![Verbindingsinstellingen](/help/forms/using/assets/oauth_emailendpoint.png)

   >[!NOTE]
   >
   > Klik op voor meer informatie over het configureren van e-maileindpunten [Een e-maileindpunt configureren](https://experienceleague.adobe.com/docs/experience-manager-65/content/forms/administrator-help/configuring-email-endpoints.html).

## Problemen oplossen {#troubleshooting}

* Als de e-mailservice niet correct werkt, probeert u de `Refresh Token` zoals hierboven beschreven. Het duurt een paar minuten voordat de nieuwe waarde is geïmplementeerd.

* Fout bij het configureren van de gegevens van de e-mailserver in het eindpunt van de e-mail met Workbench. Probeer om het eindpunt als Admin UI in plaats van Workbench te vormen.
