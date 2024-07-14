---
title: Op OAuth2 gebaseerde verificatie configureren voor Microsoft&reg (Forms JEE OAuth); Office 365-mailserverprotocollen
description: Op OAuth2 gebaseerde verificatie configureren voor Microsoft&reg (Forms JEE OAuth); Office 365-mailserverprotocollen
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

1. Login aan [ https://portal.azure.com/ ](https://portal.azure.com/) en onderzoek naar **Azure Actieve Folder** in de onderzoeksbar en klik het resultaat.
Alternatief, kunt u direct aan [ https://portal.azure.com/#blade/Microsoft_AAD_IAM/ActiveDirectoryMenuBlade/Overview ](https://portal.azure.com/#blade/Microsoft_AAD_IAM/ActiveDirectoryMenuBlade/Overview) doorbladeren
1. Klik **toevoegen** > **Registratie van de Toepassing** > **Nieuwe Registratie**.

   ![ de Registratie van de Toepassing ](/help/forms/using/assets/outh_outlook_microsoft_azure.png)

1. Vul de informatie volgens uw vereisten in, dan klik **Register**.
   ![ Gesteunde Rekening ](/help/forms/using/assets/azure_suuportedaccountype.png)
In het bovengenoemde geval, **Rekeningen in om het even welke organisatorische folder (Om het even welke Azure folder van de ADVERTENTIE - Multihuurder) en persoonlijke rekeningen Microsoft® (bijvoorbeeld, Skype, Xbox)** optie wordt geselecteerd.

   >[!NOTE]
   >
   > * Voor **Rekeningen in om het even welke organisatorische folder (Om het even welke Azure folder van de ADVERTENTIE - Multihuurder)** toepassing, adviseert de Adobe dat u een het werkrekening eerder dan een persoonlijke e-mailrekening gebruikt.
   > * **Persoonlijke Microsoft® rekeningen slechts** toepassing wordt niet gesteund.
   > * De Adobe adviseert dat u de **multi-huurder en persoonlijke Microsoft® rekening** toepassing gebruikt.

1. Daarna, ga naar **Certificaten en geheimen**, klik **Nieuw cliëntgeheim** en volg de stappen op het scherm om een geheim tot stand te brengen. Let erop dat u deze waarde van het geheim opneemt voor later gebruik.

   ![ Geheime Sleutel ](/help/forms/using/assets/azure_secretkey.png)

1. Voor het toevoegen van toestemmingen, ga naar pas gecreëerde app, en selecteer **API Toestemmingen** > **een Toestemming** toevoegen > **Grafiek Microsoft®** > **Gedelegeerde Toestemmingen**.
1. Selecteer checkboxes voor de hieronder toestemmingen voor app en klik **toevoegen Toestemming**:

   * `IMAP.AccessUser.All`
   * `Mail.Read`
   * `offline_access`
   * `POP.AccessAsUser.All`
   * `SMTP.Send`
   * `User.Read`

   ![ API Toestemming ](/help/forms/using/assets/azure_apipermission.png)

1. Selecteer **Authentificatie** > **een platform** toevoegen > **Web**, en in de **Redirect Urls** sectie, voeg om het even welke hieronder URIs (Universeel Herkenningsteken van het Middel) toe als:
   * `https://login.microsoftonline.com/common/oauth2/nativeclient`
   * `http://localhost`

   In dit geval wordt `https://login.microsoftonline.com/common/oauth2/nativeclient` gebruikt als een omleidings-URI.

1. Klik **vormen** na het toevoegen van elke URL en vorm uw montages volgens uw vereisten.
   ![ Redirect URI ](/help/forms/using/assets/azure_redirecturi.png)

   >[!NOTE]
   >
   > Het is verplicht om **tokens van de Toegang** en **tokens van identiteitskaart** checkboxes te selecteren.

1. Klik **Overzicht** in de linkerruit en kopieer de waarden voor **identiteitskaart van de Toepassing (cliënt)**, **Folder (huurder) identiteitskaart**, en **Geheime Cliënt** voor recenter gebruik.

   ![Overzicht](/help/forms/using/assets/azure_overview.png)

## De machtigingscode genereren {#generating-the-authorization-code}

Vervolgens moet u de machtigingscode genereren, zoals in de volgende stappen wordt uitgelegd:

1. Open de volgende URL in de browser nadat u `clientID` hebt vervangen door de `<client_id>` en `redirect_uri` door de URI voor omleiding van de toepassing:

   ```https://login.microsoftonline.com/common/oauth2/v2.0/authorize?client_id=[clientid]&scope=IMAP.AccessAsUser.All%20POP.AccessAsUser.All%20SMTP.Send%20User.Read%20Mail.Read%20offline_access&response_type=code&redirect_uri=[redirect_uri]&prompt=login```

   >[!NOTE]
   >
   > Als er één toepassing voor huurders is, vervangt u `common` door uw `[tenantid]` in de volgende URL voor het genereren van machtigingscode: `https://login.microsoftonline.com/[tenantid]/oauth2/v2.0/authorize?client_id=[[clientid]]&scope=IMAP.AccessAsUser.All%20POP.AccessAsUser.All%20SMTP.Send%20User.Read%20Mail.Read%20openid%20offline_access&response_type=code&redirect_uri=[redirect_uri]&prompt=login`

1. Wanneer u de bovenstaande URL typt, wordt u omgeleid naar het aanmeldingsscherm:
   ![ Login het Scherm ](/help/forms/using/assets/azure_loginscreen.png)

1. Ga e-mail in, klik **daarna** en het toepassingstoestemmingsscherm verschijnt:

   ![ Toestemming ](/help/forms/using/assets/azure_permission.png) toestaan

1. Wanneer u toestemming toestaat, wordt u omgeleid naar een nieuwe URL als: `https://login.microsoftonline.com/common/oauth2/nativeclient?code=<code>&session_state=[session_id]`

1. Kopieer de waarde van `<code>` van de bovenstaande URL van `0.ASY...` naar `&session_state` in de bovenstaande URL.

## Het genereren van het token Vernieuwen {#generating-the-refresh-token}

Vervolgens moet u het vernieuwingstoken genereren. Dit wordt in de volgende stappen uitgelegd:

1. Open de bevelherinnering en gebruik het volgende cURL bevel om te verfrissen Token te krijgen.

1. Vervang `clientID` , `client_secret` en `redirect_uri` door de waarden voor de toepassing en de waarde van `<code>` :

   `curl -H "ContentType application/x-www-form-urlencoded" -d "client_id=[client-id]&scope=https%3A%2F%2Foutlook.office.com%2FIMAP.AccessAsUser.All%20https%3A%2F%2Foutlook.office.com%2FPOP.AccessAsUser.All%20https%3A%2F%2Foutlook.office.com%2FSMTP.Send%20https%3A%2F%2Foutlook.office.com%2FUser.Read%20https%3A%2F%2Foutlook.office.com%2FMail.Read%20offline_access&code=[code]&grant_type=authorization_code&redirect_uri=[redirect_uri]&client_secret=[secretkey_value]" -X POST https://login.microsoftonline.com/common/oauth2/v2.0/token`

   >[!NOTE]
   >
   > Als u in één toepassing voor huurders een vernieuwingstoken wilt genereren, gebruikt u de volgende cURL-opdracht en vervangt u `common` door de instructie `[tenantid]` in:
   >`curl -H "ContentType application/x-www-form-urlencoded" -d "client_id=[client-id]&scope=https%3A%2F%2Foutlook.office.com%2FIMAP.AccessAsUser.All%20https%3A%2F%2Foutlook.office.com%2FPOP.AccessAsUser.All%20https%3A%2F%2Foutlook.office.com%2FSMTP.Send%20https%3A%2F%2Foutlook.office.com%2FUser.Read%20https%3A%2F%2Foutlook.office.com%2FMail.Read%20offline_access&code=[code]&grant_type=authorization_code&redirect_uri=[redirect_uri]&client_secret=[secretkey_value]" -X POST https://login.microsoftonline.com/[tenantid]/oauth2/v2.0/token`

1. Noteer het token voor vernieuwen.

## E-mailservice configureren met OAuth 2.0-ondersteuning {#configureemailservice}

Configureer nu de e-mailservice op de nieuwste JEE-server door u aan te melden bij de beheerinterface:

1. Ga naar **Huis** > **de Dienst** > **Toepassing en de Diensten** > **het Beheer van de Dienst** > **E-mailDienst**, verschijnt het **E-mail van de Configuratie dienst** venster, dat voor basisauthentificatie wordt gevormd.

   >[!NOTE]
   >
   > Om de authentificatiedienst van Auth 2.0 toe te laten, is het verplicht om **te selecteren of de server SMTP authentificatie (SMTP voor authentiek verklaart)** checkbox vereist.

1. Plaats **Auth 2.0 Montages van de Authentificatie** als `True`.
1. Kopieer de waarden van **identiteitskaart van de Cliënt** en **Geheime Cliënt** van Azure Portal.
1. Kopieer de waarde van het geproduceerde **verfrissen Token**.
1. Login aan **Werkbank** en onderzoek **e-mail 1.0** van **de Plukker van de Activiteit**.
1. Onder E-mail 1.0 zijn drie opties beschikbaar als:
   * **verzendt met Document**: verzendt e-mail met enige gehechtheid.
   * **verzendt met Kaart van Gehechtheid**: Verzendt e-mail met veelvoudige gehechtheid.
   * **ontvang**: Ontvangt een E-mail van IMAP.

   >[!NOTE]
   >
   >* Het protocol van de Veiligheid van het Vervoer heeft de volgende geldige waarden: &quot;leeg&quot;, &quot;SSL&quot;of &quot;TLS&quot;. Plaats waarden van **SMTP de Veiligheid van het Vervoer** en **ontvang de Veiligheid van het Vervoer** aan **TLS** voor het toelaten van de de authentificatiedienst van de Auth.
   >* **POP3 protocol** wordt niet gesteund voor OAuth terwijl het gebruiken van e-maileindpunten.

   ![ de Montages van de Verbinding ](/help/forms/using/assets/oauth_connectionsettings.png)

1. Test de toepassing door **te selecteren verzend met Document**.
1. Verstrek **AAN** en **van** adressen.
1. Roep de toepassing aan en er wordt een e-mail verzonden met de verificatie van 0 augustus 2.0.

   >[!NOTE]
   >
   >Indien gewenst, kunt u Auth 2.0 authentificatie veranderen die aan basisauthentificatie voor een bepaald proces in een werkbank plaatst. Om dit te doen, plaats **OAuth 2.0 de waarde van de Authentificatie** als &quot;Vals&quot;onder **Globale montages van het Gebruik** in de **Montages van de Verbinding** tabel.

## Taken verifiëren inschakelen {#enable_oauth_task}

1. Ga naar **Huis** > **de Diensten** > **Werkschema van de Vorm** > **de Montages van de Server** > **E-mailMontages**
1. Om de taakberichten van de Auth toe te laten, selecteer **toelaten checkbox van Auth**.
1. Kopieer de waarden van **identiteitskaart van de Cliënt** en **Geheime Cliënt** van Azure Portal.
1. Kopieer de waarde van het geproduceerde **verfrissen Token**.
1. Klik **sparen** om de details te bewaren.

   ![ Bericht van de Taak ](/help/forms/using/assets/task_notification.png)

   >[!NOTE]
   >
   > Om meer informatie met betrekking tot taakberichten te kennen, [ klik hier ](https://experienceleague.adobe.com/docs/experience-manager-65/content/forms/administrator-help/configuring-email-endpoints.html#create-an-email-endpoint-for-the-complete-task-service).

## Om e-maileindpunt te vormen {#configure_email_endpoint}

1. Ga naar **Huis** > **Diensten** > **Toepassing en de Diensten** > **Beheer van het Eindpunt**
1. Om e-maileindpunt te vormen, plaats **Auth 2.0 Montages van de Authentificatie** als `True`.
1. Kopieer de waarden van **identiteitskaart van de Cliënt** en **Geheime Cliënt** van Azure Portal.
1. Kopieer de waarde van het geproduceerde **verfrissen Token**.
1. Klik **sparen** om de details te bewaren.

   ![ de Montages van de Verbinding ](/help/forms/using/assets/oauth_emailendpoint.png)

   >[!NOTE]
   >
   > Om meer informatie te kennen bij het vormen van e-maileindpunten, klik [ een e-maileindpunt ](https://experienceleague.adobe.com/docs/experience-manager-65/content/forms/administrator-help/configuring-email-endpoints.html) vormen.

## Problemen oplossen {#troubleshooting}

* Als de e-mailservice niet correct werkt, probeert u de `Refresh Token` opnieuw te genereren zoals hierboven beschreven. Het duurt een paar minuten voordat de nieuwe waarde is geïmplementeerd.

* Fout bij het configureren van de gegevens van de e-mailserver in het eindpunt van de e-mail met Workbench. Probeer om het eindpunt als Admin UI in plaats van Workbench te vormen.
