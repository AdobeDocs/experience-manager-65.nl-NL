---
title: Serverinstellingen configureren
seo-title: Serverinstellingen configureren
description: Op de pagina Serverinstellingen hebt u toegang tot de instellingen voor e-mail, taakmeldingen en beheerdersmeldingen.
seo-description: Op de pagina Serverinstellingen hebt u toegang tot de instellingen voor e-mail, taakmeldingen en beheerdersmeldingen.
uuid: 73b51ac0-56e5-4748-bb33-e3986c69eb2d
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_forms_workflow
products: SG_EXPERIENCEMANAGER/6.5/FORMS
discoiquuid: e047a95e-0acb-438a-8d27-f005c0adc508
translation-type: tm+mt
source-git-commit: 1343cc33a1e1ce26c0770a3b49317e82353497ab
workflow-type: tm+mt
source-wordcount: '2657'
ht-degree: 0%

---


# Serverinstellingen configureren {#configuring-server-settings}

De pagina Serverinstellingen biedt toegang tot verschillende instellingen voor de formulierworkflow:

* **E-mailinstellingen** die uitgaande e-mailberichten inschakelen, samen met de instellingen van de e-mailserver die voor deze berichten worden gebruikt. (Zie E-mailinstellingen [configureren](configuring-server-settings.md#configuring-email-settings).)
* **Instellingen** voor taakmeldingen waarmee de berichten die in e-mailberichten naar eindgebruikers en groepen worden verzonden met betrekking tot hun taken kunnen worden ingeschakeld, uitgeschakeld of gewijzigd. (Zie Meldingen [configureren voor gebruikers en groepen](configuring-server-settings.md#configuring-notifications-for-users-and-groups).)
* **Instellingen** voor beheerdersmeldingen waarmee berichten die in e-mailmeldingen worden verzonden voor beheertaken worden ingeschakeld, uitgeschakeld of gewijzigd. (Zie Meldingen [configureren voor beheerders](configuring-server-settings.md#configuring-notifications-for-administrators).)

## E-mailinstellingen configureren {#configuring-email-settings}

U kunt een e-mailaccount opgeven voor de formulierserver, waarmee e-mailberichten worden verzonden naar gebruikers en beheerders van AEM-formulieren. Deze e-mailberichten worden gebruikt om gebruikers op de hoogte te brengen van en te herinneren aan taken die zij moeten voltooien, de gebruiker op de hoogte te stellen van taken die een deadline hebben bereikt en de beheerder op de hoogte te stellen van eventuele procesfouten.

Als u het verzenden van e-mailberichten tussen AEM-formulieren en gebruikers wilt inschakelen, configureert u de instellingen voor uitgaande e-mail op de pagina E-mailinstellingen. Uitgaande e-mail moet een server SMTP gebruiken.

Als u wilt dat AEM-formulieren binnenkomende e-mailberichten van gebruikers kunnen ontvangen en verwerken, maakt u een e-maileindpunt voor de service Volledige taak. (Zie [Creeer een E-maileindpunt voor de Volledige dienst](/help/forms/using/admin-help/configuring-email-endpoints.md#create-an-email-endpoint-for-the-complete-task-service)van de Taak).

Als uw processen zijn ontworpen en geïmplementeerd zonder dat e-mail vereist is, hoeft u geen van de opties te configureren op de pagina E-mailinstellingen.

### Instellingen voor uitgaande e-mail configureren {#configure-outgoing-email-settings}

1. Klik in de beheerconsole op Services > Formulierwerkstroom > Serverinstellingen > E-mailinstellingen.
1. Selecteer Uitgaande berichten inschakelen.
1. Typ in het vak SMTP-server de naam van de e-mailserver of het IP-adres. Alle e-mailberichten met meldingen vanuit de formulierwerkstroom worden verzonden vanaf deze e-mailserver.
1. Typ in de vakken Gebruikersnaam en Wachtwoord de aanmeldingsnaam en het wachtwoord dat moet worden gebruikt wanneer de SMTP-server verificatie vereist. Laat ze leeg als anonieme aanmelding is toegestaan.
1. Typ in het vak E-mailadres het e-mailadres dat u wilt gebruiken als het retouradres voor e-mailberichten die via de formulierworkflow worden verzonden.

   >[!NOTE]
   >
   >Als u de Server van de Uitwisseling van Microsoft gebruikt en het E-mailadres een ongeldig e-mailadres is, verzendt de server van de Uitwisseling van Microsoft geen e-mail naar de Lijsten van de Distributie. Om de kwestie op te lossen, selecteer afzonderlijk de **Enable Externe Communicatie** optie voor elke Lijst van de Distributie op de server van de Uitwisseling van Microsoft.

1. Klik op Opslaan.

>[!NOTE]
>
>Als u onjuiste informatie invoert, kunt u op Annuleren klikken om terug te keren naar de vorige weergegeven pagina.

### E-mailsjablonen configureren voor gebruik van de werkruimte AEM Forms {#configuring-email-templates-to-use-html-workspace}

>[!NOTE]
>
>De Flex-werkruimte is verouderd voor de release van AEM-formulieren.

Standaard bevatten de e-mails die door AEM-formulieren worden verzonden koppelingen naar (Vervangen voor AEM-formulieren op JEE) Flex Workspace. U kunt AEM-formulieren configureren om e-mailberichten met koppelingen naar de werkruimte van AEM Forms te verzenden. Zie [dit](/help/forms/using/features-html-workspace-available-flex.md) artikel voor meer informatie over de voordelen van AEM Forms Workspace over (Vervangen voor AEM-formulieren in JEE) Flex Workspace.

1. Klik in de beheerconsole op Home > Services > Formulierwerkstroom > Serverinstellingen > Taakmeldingen.
1. Taaktoewijzingssjabloon openen.
1. Plaats het malplaatje in de taakberichten aan het volgende: `https://@@notification-host@@:8080/lc/libs/ws/index.html?taskId=@@taskid@@`

   ```java
   https://@@notification-host@@:8080/lc/libs/ws/index.html?taskId=@@taskid@@
   ```

## Meldingen voor gebruikers en groepen configureren {#configuring-notifications-for-users-and-groups}

Op de pagina Taakmelding kunt u sjablonen configureren die in de formulierworkflow worden gebruikt om de e-mailmeldingen te genereren die naar gebruikers en groepen worden verzonden. U kunt de meldingen aanpassen en opmaken met variabelen voor de formulierwerkstroom.

U configureert de volgende typen meldingen voor gebruikers en groepen:

* herinneringen
* taaktoewijzingen
* termijnen

Als u e-mailberichten voor een groep wilt genereren, geeft u een e-mailadres voor de groep op in Gebruikersbeheer. <!--Fix broken link See Setting up and organizing users -->Wanneer een werkstroom voor formulieren een e-mailbericht naar een groep verzendt, ontvangt elk lid in de groep met een opgegeven e-mailadres het e-mailbericht. Wanneer een lid van de groep een e-mailbericht ontvangt en de taak wil claimen, moet het lid op de claimkoppeling in het e-mailbericht klikken. Hiermee wordt de pagina met taakdetails in Workspace geopend. Vanaf dat punt kan het lid aanspraak maken op of aanspraak maken op het werk.

>[!NOTE]
>
>De Flex-werkruimte is verouderd voor de release van AEM-formulieren.

### Herinneringen voor gebruikers of groepen configureren {#configure-reminders-for-users-or-groups}

U kunt herinneringsberichten naar de toegewezen gebruiker of groep verzenden wanneer een deadline om een taak te voltooien nadert. De regels om precies te bepalen wanneer een herinneringsbericht wordt verzonden worden bepaald door de procesontwikkelaar.

1. Klik in de beheerconsole op Services > Forms workflow > Server Settings > Task Notifications.
1. Klik onder Type bericht op Herinnering (voor gebruikers) of Groep - Herinnering (voor groepen).
1. Selecteer Herinnering inschakelen of Groep - Herinnering inschakelen.
1. (Alleen gebruikersmeldingen) Als u een bijlage van het formulier en de bijbehorende gegevens wilt opnemen in het e-mailbericht voor de herinnering, selecteert u Formuliergegevens opnemen.
1. Typ in het vak Onderwerp de tekst voor de onderwerpregel van het e-mailbericht. Dit veld is vooraf gevuld met standaardtekst. Zie De inhoud van meldingen [aanpassen voor meer informatie over het aanpassen van dit veld](configuring-server-settings.md#customizing-the-content-of-notifications).
1. Typ in het vak Berichtgevingssjabloon de tekst voor de hoofdtekst van het e-mailbericht. Dit veld is vooraf gevuld met standaardtekst. Zie De inhoud van meldingen [aanpassen voor meer informatie over het aanpassen van dit veld](configuring-server-settings.md#customizing-the-content-of-notifications).
1. Selecteer in de lijst Berichtindeling de indeling waarin het e-mailbericht wordt verzonden, HTML of Tekst. De standaardindeling is HTML.
1. Selecteer in de lijst E-mailcodering de coderingsindeling die u voor het e-mailbericht wilt gebruiken. Het gebrek is UTF-8, die de meeste gebruikers buiten Japan zullen gebruiken. Gebruikers in Japan kunnen ISO2022-JP selecteren.
1. Klik op Opslaan.

### Meldingen voor taaktoewijzing configureren voor gebruikers of groepen {#configure-task-assignment-notifications-for-users-or-groups}

U kunt taaktoewijzingsmeldingen verzenden naar een gebruiker of groep wanneer aan deze gebruikers of groepen een taak is toegewezen.

1. Klik in de beheerconsole op Services > Forms workflow > Server Settings > Task Notifications.
1. Onder het Type van Bericht, klik de Toewijzing van de Taak voor gebruikers of Groep - Taak Toewijzing voor groepen.
1. Selecteer Taaktoewijzing voor gebruikers inschakelen of Groep inschakelen - Taaktoewijzing voor groepen.
1. (Alleen gebruikersmeldingen) Als u een bijlage van het formulier en de bijbehorende gegevens wilt opnemen in het e-mailbericht voor de toewijzing van taken, selecteert u Formuliergegevens opnemen.
1. Typ in het vak Onderwerp de tekst voor de onderwerpregel van het e-mailbericht. Dit veld is vooraf gevuld met standaardtekst. Zie De inhoud van meldingen [aanpassen voor meer informatie over het aanpassen van dit veld](configuring-server-settings.md#customizing-the-content-of-notifications).
1. Typ in het vak Berichtgevingssjabloon de tekst voor de hoofdtekst van het e-mailbericht. Dit veld is vooraf gevuld met standaardtekst. Zie De inhoud van meldingen [aanpassen voor meer informatie over het aanpassen van dit veld](configuring-server-settings.md#customizing-the-content-of-notifications).
1. Selecteer in de lijst Berichtindeling de indeling waarin het e-mailbericht wordt verzonden, HTML of Tekst. De standaardindeling is HTML.
1. Selecteer in de lijst E-mailcodering de coderingsindeling die u voor het e-mailbericht wilt gebruiken. Het gebrek is UTF-8, die de meeste gebruikers buiten Japan zullen gebruiken. Gebruikers in Japan kunnen ISO2022-JP selecteren.
1. Klik op Opslaan.

### Tijdlijnmeldingen configureren voor gebruikers of groepen {#configure-deadline-notifications-for-users-or-groups}

U kunt deadline-meldingen verzenden naar gebruikers en groepen wanneer de deadline voor het uitvoeren van een toegewezen taak is verstreken. Een deadline-melding is doorgaans informatief omdat de gebruiker niet langer kan reageren op de toegewezen taak.

1. Klik in de beheerconsole op Services > Forms workflow > Server Settings > Task Notifications.
1. Onder het Type van Bericht, klik Deadline (voor gebruikers) of Groep - Deadline (voor groepen).
1. Selecteer Deadline inschakelen of Groep - Deadline inschakelen.
1. Typ in het vak Onderwerp de tekst voor de onderwerpregel van het e-mailbericht. Dit veld is vooraf gevuld met standaardtekst. Zie De inhoud van meldingen [aanpassen voor meer informatie over het aanpassen van dit veld](configuring-server-settings.md#customizing-the-content-of-notifications).
1. Typ in het vak Berichtgevingssjabloon de tekst voor de hoofdtekst van het e-mailbericht. Dit veld is vooraf gevuld met standaardtekst. Zie De inhoud van meldingen [aanpassen voor meer informatie over het aanpassen van dit veld](configuring-server-settings.md#customizing-the-content-of-notifications).
1. Selecteer in de lijst Berichtindeling de indeling waarin het e-mailbericht wordt verzonden, HTML of Tekst. De standaardindeling is HTML.
1. Selecteer in de lijst E-mailcodering de coderingsindeling die u voor het e-mailbericht wilt gebruiken. Het gebrek is UTF-8, die de meeste gebruikers buiten Japan zullen gebruiken. Gebruikers in Japan kunnen ISO2022-JP selecteren.
1. Klik op Opslaan.

### De tag DO NOT DELETE verbergen voor alle e-mails {#hide-the-do-not-delete-tag-for-all-emails}

U kunt e-mail configureren om te verbergen voor de tag NIET DELETE bijhouden in alle e-mails die worden verzonden in een humanitair proces. Zie [How to hide the &#39;DO-NOT-DELETE&#39; tag with CSS voor meer informatie](https://blogs.adobe.com/LiveCycleHelp/2013/09/how-to-hide-the-do-not-delete-tag-with-css.html)

## Meldingen voor beheerders configureren {#configuring-notifications-for-administrators}

U kunt sjablonen configureren die in de formulierworkflow worden gebruikt om de e-mailmeldingen te genereren die naar beheerders worden verzonden.

U configureert de volgende typen meldingen voor beheerders:

* stilgezette vertakking
* stilstaande bewerking

### Gestapelde filiaalmeldingen configureren {#configure-stalled-branch-notifications}

Als een vertakking (of opzettelijk of wegens een fout) ophoudt te werk te gaan, kunt u een e-mailbericht hebben dat wordt verzonden naar een beheerder of een andere gebruiker, die het probleem dan kan onderzoeken.

1. Klik in de beheerconsole op Services > Forms workflow > Server Settings > Administrator Notifications.
1. Klik onder Meldingstype op Vertakking stilzetten.
1. Selecteer Geroepen vertakking inschakelen.
1. Typ in het vak E-mailadres de adressen van de gebruikers die moeten worden gewaarschuwd wanneer een vertakking wordt geplaatst. Gebruik de notatie user@domain.com en scheidt elk adres met een komma. Dit e-mailadres is meestal bestemd voor een beheerder.
1. Typ in het vak Onderwerp de tekst voor de onderwerpregel van het e-mailbericht. Dit veld is vooraf gevuld met standaardtekst. Zie De inhoud van meldingen [aanpassen voor meer informatie over het aanpassen van dit veld](configuring-server-settings.md#customizing-the-content-of-notifications).
1. Typ in het vak Berichtgevingssjabloon de tekst voor de hoofdtekst van het e-mailbericht. Dit veld is vooraf gevuld met standaardtekst. Zie De inhoud van meldingen [aanpassen voor meer informatie over het aanpassen van dit veld](configuring-server-settings.md#customizing-the-content-of-notifications).
1. Selecteer in de lijst Berichtindeling de indeling waarin het e-mailbericht wordt verzonden, HTML of Tekst. De standaardindeling is HTML.
1. Selecteer in de lijst E-mailcodering de coderingsindeling die u voor het e-mailbericht wilt gebruiken. Het gebrek is UTF-8, die de meeste gebruikers buiten Japan gebruiken. Gebruikers in Japan kunnen ISO2022-JP selecteren.
1. Klik op Opslaan.

### Gestormde bewerkingsmeldingen configureren {#configure-stalled-operation-notifications}

Als een bewerking niet meer actief of vanwege een fout kan worden uitgevoerd, kunt u een e-mailbericht laten verzenden naar een beheerder of een andere gebruiker, die het probleem kan onderzoeken.

1. Klik in de beheerconsole op Services > Forms workflow > Server Settings > Administrator Notifications.
1. Klik onder Meldingstype op Gestuurde bewerking.
1. Selecteer Geroepen bewerking inschakelen.
1. Typ in het vak E-mailadressen de adressen van de gebruikers die moeten worden gewaarschuwd wanneer een bewerking stagneert. Gebruik de notatie user@domain.com en scheidt elk adres met een komma. Dit e-mailadres is meestal bestemd voor een beheerder.
1. Typ in het vak Onderwerp de tekst voor de onderwerpregel van het e-mailbericht. Dit veld is vooraf gevuld met standaardtekst. Zie De inhoud van meldingen [aanpassen voor meer informatie over het aanpassen van dit veld.](configuring-server-settings.md#customizing-the-content-of-notifications)
1. Typ in het vak Berichtgevingssjabloon de tekst voor de hoofdtekst van het e-mailbericht. Dit veld is vooraf gevuld met standaardtekst. Zie De inhoud van meldingen [aanpassen voor meer informatie over het aanpassen van dit veld](configuring-server-settings.md#customizing-the-content-of-notifications).
1. Klik op Opslaan.

## Inhoud van meldingen aanpassen {#customizing-the-content-of-notifications}

De pagina&#39;s Taakmeldingen en Beheerdersmeldingen bevatten verschillende functies waarmee u berichtberichten kunt aanpassen:

* rijke teksteditor
* variabele kiezer
* URL genereren

### RTF-editor {#rich-text-editor}

Het gebied van het Malplaatje van het Bericht is een rijke tekstredacteur die u toelaat om HTML voor de e-mailberichtberichten te produceren. Deze sjabloon biedt opmaakopties voor lettertypen en alinea&#39;s, die u vindt onder het vak Meldingssjabloon. U kunt onder andere lettertype, tekengrootte, stijl en kleur kiezen, en alinea-uitlijning en opsommingstekens gebruiken.

### URL genereren {#url-generation}

Alleen voor taakmeldingen bevat de workflow Formulieren twee vooraf gedefinieerde URL-configuraties die u vanuit de lijst Url Generation naar het vak Berichtgevingssjabloon kunt slepen en vervolgens kunt aanpassen:

* OpenTask is beschikbaar voor de berichttypen Herinnering en Taak toewijzen. Deze URL bevat een koppeling naar de taak in Workspace, zodat de gebruiker deze taak snel kan openen vanuit het e-mailbericht. Wanneer u de OpenTask URL naar het vakje van het Malplaatje van het Bericht sleept, is URL in het volgende formaat:

   `https://@@notification-host@@:<PORT>/workpace/Main.html?taskId=@@taskid@@`

* ClaimTask is beschikbaar voor de Groep - Herinnering en Groep - de berichttypes van de Taak van de Taak. Deze URL bevat een koppeling naar de pagina met taakdetails in Workspace, waar de gebruiker een claim kan indienen of een claim kan indienen en het werkitem kan openen. Wanneer u de ClaimTask URL aan het vakje van het Malplaatje van het Bericht sleept, is URL in het volgende formaat:

   `https://@@notification-host@@:<PORT>/workpace/Main.html?taskId=@@taskid@@`

>[!NOTE]
>
>De Flex-werkruimte is verouderd voor de release van AEM-formulieren.

Als uw oplossing in een gegroepeerd milieu wordt opgesteld, vervang `@@notification-host@@` met het clusteradres.

`<`*PORT *`>`is het poortnummer van de HTTP-listener voor de toepassingsserver. De standaard HTTP-listenerpoort voor de ondersteunde toepassingsservers is als volgt:

**JBoss:** 8080

**Oracle WebLogic Server:** 7001

**IBM WebSphere:** 9080

Om deze URLs correct te maken, vervang `<`*HAVEN *`>`met het havenaantal dat voor uw milieu aangewezen is.

>[!NOTE]
>
>Als u een andere aangepaste webtoepassing dan Forms gebruikt om gebruikers toegang tot de taken te geven, moet u in plaats daarvan een URL-indeling gebruiken die geschikt is voor uw aangepaste toepassing.

### Variabelekiezer {#variable-picker}

De lijst Variabele kiezer biedt nuttige variabelen die u kunt slepen en neerzetten in de vakken Onderwerp- of Meldingsjabloon. Wanneer u een variabele in de vakken Onderwerp of Meldingsjabloon neerzet, verandert deze in de werkelijke naam van de variabele voor de formulierworkflow, bijvoorbeeld met twee @-symbolen aan weerszijden `@@taskid@@`.

Voor herinneringen, taaktaken, en termijnen voor gebruikers en groepen, kunt u de volgende variabelen in de dozen van het Malplaatje van het Onderwerp en van het Bericht gebruiken:

**beschrijving** de inhoud van het bezit van de Beschrijving, zoals die in de gebruikersstap (beginpunt, de verrichting van de Taak toewijzen, of de Veelvoudige verrichting van Taken toewijzen) van het proces in Workbench wordt bepaald.

**instructies** De inhoud van het bezit van de Instructies van de Taak, zoals die in de gebruikersstap van het proces in Workbench wordt bepaald.

**notification-host** De hostnaam van de AEM-formuliertoepassingsserver.

**process-name** De naam van het proces.

**operation-name** De naam van de stap.

**taschild** De unieke id voor de huidige taak.

**De acties** produceren een genummerde lijst van geldige routes (bijvoorbeeld, goedkeuren, verwerpen) die de ontvanger kan klikken.

Daarnaast kunt u voor groepherinneringen, groepstaken en groepstermijnen ook het volgende gebruiken:

**group-name** De naam van de groep die het het werkpunt wordt toegewezen.

>[!NOTE]
>
>Wanneer een variabele geen waarde heeft, wordt niets geretourneerd.

Voor gestalte takken, kunt u de volgende variabelen in de dozen van het Malplaatje van het Onderwerp en van het Bericht gebruiken:

**vertakking-id** De vertakkings-id.

**proces-id** De procesinstantie-id.

**notification-host** De hostnaam van de AEM-formuliertoepassingsserver.

Voor gestalte verrichtingen, kunt u de volgende variabelen in de vakjes van het Malplaatje van het Onderwerp en van het Bericht gebruiken:

**action-id** De bewerking-id.

**vertakking-id** De vertakkings-id.

**proces-id** De procesinstantie-id.

**notification-host** De hostnaam van de AEM-formuliertoepassingsserver.

### Een variabele gebruiken in het vak Onderwerp {#using-a-variable-in-the-subject-box}

Als u de volgende tekst in het onderwerpvakje voor de berichten van de Taak typt:

`Please complete task @@taskid@@`

De gebruiker ontvangt een e-mailbericht met het volgende onderwerp als aan hem taak 376 is toegewezen:

`Please complete task 376`

### Variabelen gebruiken in het vak Berichtgevingssjabloon {#using-variables-in-the-notification-template-box}

Als u de volgende tekst in het vakje van het Malplaatje van het Bericht voor de Geleide berichten van de Tak typt:

`Branch @@branch-id@@ has stalled! You have received this notification from @@notification-host@@.`

De beheerder ontvangt een e-mailbericht met de volgende inhoud als het vertakkingsaantal 4868 is en de servernaam `ServerXYZ`:

`Branch 4868 has stalled! You have received this notification from ServerXYZ.`

## Verbindingen voor Business Activity Monitoring configureren {#configuring-business-activity-monitoring-connections}

De Controle van de bedrijfsactiviteit, een facultatieve module, verstrekt een reeks operationele dashboards die in real time zicht in uw verrichtingen en zeer belangrijke prestatiesindicatoren verstrekken.

Op de pagina van de Montages van de Configuratie BAM, plaatst u de verbindingen aan de server die BAM in werking stelt zodat de proces-verwante gebeurtenissen kunnen worden gevolgd en aan die server worden overgebracht.

1. Klik in de beheerconsole op Services > Forms workflow > Server Settings > BAM Configuration Settings.
1. Typ in het vak BAM-host de naam van de server waarop BAM wordt uitgevoerd. De standaardwaarde is localhost.
1. Typ in het vak BAM-poort de poort die u wilt gebruiken om verbinding te maken met de server waarop BAM wordt uitgevoerd. De standaard BAM-poort voor JBoss is 8080, WebLogic is 7001 en WebSphere is 9080.
1. Typ in het vak Serverhost de naam of het IP-adres van de server met hostformulieren. De standaardwaarde is localhost.
1. Typ in het vak Serverpoort het poortnummer dat door de formulierserver wordt gebruikt.
1. Typ in de vakken Gebruikersnaam en Wachtwoord de juiste gebruikersnaam en het juiste wachtwoord voor toegang tot de BAM-server. De standaardgebruikersnaam is CognosNowAdmin en het standaardwachtwoord is manager.
1. Klik op Opslaan.

