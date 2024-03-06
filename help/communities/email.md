---
title: E-mail configureren
description: Leer hoe u e-mailmeldingen en abonnementen voor Adobe Experience Manager Communities configureert.
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: administering
content-type: reference
pagetitle: Configuring Email
role: Admin
exl-id: bf97d388-f8ca-4e37-88e2-0c536834311e
source-git-commit: 9d497413d0ca72f22712581cf7eda1413eb8d643
workflow-type: tm+mt
source-wordcount: '724'
ht-degree: 0%

---

# E-mail configureren {#configuring-email}

AEM Communities gebruikt e-mail voor:

* [Publikaties](notifications.md)
* [Communityabonnementen](subscriptions.md)

Standaard is de e-mailfunctie niet functioneel omdat hiervoor een SMTP-server en SMTP-gebruiker moet worden opgegeven.

>[!CAUTION]
>
>E-mail voor meldingen en abonnementen moet alleen zijn geconfigureerd op de [primaire uitgever](deploy-communities.md#primary-publisher).

## Standaardconfiguratie e-mailservice {#default-mail-service-configuration}

De standaardmailservice is vereist voor zowel meldingen als abonnementen.

* Meld u aan bij de primaire uitgever met beheerdersrechten en open de [Webconsole](../../help/sites-deploying/configuring-osgi.md):

   * Bijvoorbeeld: [http://localhost:4503/system/console/configMgr](http://localhost:4503/system/console/configMgr)

* Zoek de `Day CQ Mail Service`.
* Selecteer het pictogram Bewerken.

Dit is gebaseerd op de documentatie voor [E-mailmelding configureren](../../help/sites-administering/notification.md), maar met een verschil op dat gebied `"From" address` is *niet* vereist en moet leeg blijven.

Bijvoorbeeld (alleen invullen met waarden voor illustratieve doeleinden):

![email-config](assets/email-config.png)

* **[!UICONTROL SMTP server host name]**

  *(Vereist)* De te gebruiken SMTP-server.

* **[!UICONTROL SMTP server port]**

  *(Vereist)* De SMTP serverhaven moet 25 of hoger zijn.

* **[!UICONTROL SMTP user]**

  *(Vereist)* De SMTP-gebruiker.

* **[!UICONTROL SMTP password]**

  *(Vereist)* Het wachtwoord van de SMTP-gebruiker.

* **[!UICONTROL "From" address]**

  Leeg laten
* **[!UICONTROL SMTP use SSL]**

  Als deze optie is ingeschakeld, wordt een beveiligde e-mail verzonden. Zorg ervoor dat de haven aan 465 of zoals vereist voor een server SMTP wordt geplaatst.
* **[!UICONTROL Debug email]**

  Indien gecontroleerd, laat dit registreren van SMTP serverinteractie toe.

## AEM Communities E-mailconfiguratie {#aem-communities-email-configuration}

Wanneer de [standaardmailservice](#default-mail-service-configuration) wordt gevormd, de twee bestaande instanties van `AEM Communities Email Reply Configuration` OSGi config, inbegrepen in de versie, wordt functioneel.

Slechts moet de instantie voor abonnementen verder worden gevormd wanneer het toestaan van antwoord door e-mail.

1. [E-mail](#configuration-for-notifications) -instantie:

   Voor meldingen, die geen ondersteuning bieden voor e-mailantwoorden, en deze mogen niet worden gewijzigd.

1. [Abonnementen-e-mail](#configuration-for-subscriptions) -instantie:

   Vereist configuratie om het creëren van post van antwoorde-mail volledig toe te laten.

U bereikt als volgt de e-mailconfiguratieinstanties van de Gemeenschappen:

* Meld u aan bij de primaire uitgever met beheerdersrechten en open de [Webconsole](../../help/sites-deploying/configuring-osgi.md)

   * Bijvoorbeeld: [http://localhost:4503/system/console/configMgr](http://localhost:4503/system/console/configMgr)

* Zoeken `AEM Communities Email Reply Configuration`.

![email-response-config](assets/email-reply-config.png)

### Configuratie voor meldingen {#configuration-for-notifications}

De instantie van `AEM Communities Email Reply Configuration` OSGi config met de Naam e-mail is telefoontifications eigenschap. Deze functie bevat geen e-mailantwoord.

Wijzig deze configuratie niet.

* Zoek de `AEM Communities Email Reply Configuration`.
* Selecteer het pictogram Bewerken.
* Controleer of de **Naam** is `email`.

* Controleren of **Bericht maken van e-mail met antwoord** is `unchecked`.

![configureren-e-mailantwoord](assets/configure-email-reply.png)

### Configuratie voor abonnementen {#configuration-for-subscriptions}

Voor Gemeenschapsabonnementen is het mogelijk om de mogelijkheid voor een lid om inhoud te posten in of uit te schakelen door op een e-mail te antwoorden.

* Zoek de `AEM Communities Email Reply Configuration`.
* Selecteer het pictogram Bewerken.
* Controleer of de **Naam** is `subscriptions-email`.

  ![configureren-e-mailabonnement](assets/configure-email-subscriptions.png)

* **[!UICONTROL Name]**

  *(Vereist)* `subscriptions-email`. Niet bewerken.

* **[!UICONTROL Create post from reply email]**

  Als deze optie is ingeschakeld, kan de ontvanger van een e-mailbericht met abonnement inhoud plaatsen door een antwoord te verzenden. Standaard is ingeschakeld.
* **[!UICONTROL Add tracked id to header]**

  Standaard is `Reply-To`.

* **[!UICONTROL Maximum length of Subject]**

  Als tracker-id aan de onderwerpregel wordt toegevoegd, is dit de maximumlengte van het onderwerp, met uitzondering van de bijgehouden id, waarna het wordt bijgesneden. Dit moet zo klein mogelijk zijn om te voorkomen dat bijgehouden id-informatie verloren gaat. De standaardwaarde is 200.

* **[!UICONTROL "Reply-To" email address]**

  Adres dat als &quot;antwoord-aan&quot;e-mailadres wordt gebruikt. Standaard is `no-reply@example.com`.

* **[!UICONTROL Reply-to-Delimiter]**

  Als tracker-id wordt toegevoegd aan de header die reageert, wordt dit scheidingsteken gebruikt. Standaard is `+` (plusteken).

* **[!UICONTROL Tracker Id prefix in subject]**

  Als tracker-id aan de onderwerpregel wordt toegevoegd, wordt dit voorvoegsel gebruikt. Standaard is `post#`.

* **[!UICONTROL Tracker id prefix in message body]**

  Als tracker-id aan de hoofdtekst van het bericht wordt toegevoegd, wordt dit voorvoegsel gebruikt. Standaard is `Please do not remove this:`.

* **[!UICONTROL Email as HTML]**: Indien ingeschakeld, wordt het inhoudstype van het e-mailbericht ingesteld als `"text/html;charset=utf-8"`. Standaard is ingeschakeld.

* **[!UICONTROL Default user name]**

  Deze naam wordt gebruikt voor geen naamgebruikers. Standaard is `no-reply@example.com`.

* **[!UICONTROL Templates root path]**

  De e-mail wordt samengesteld met behulp van een sjabloon die is opgeslagen op dit hoofdpad. Standaard is `/etc/community/templates/subscriptions-email`.

## Opiniepeilingimportmodule configureren {#configure-polling-importer}

Voor de e-mail die naar de gegevensopslagplaats moet worden gebracht, is het noodzakelijk om een opiniepeilingimporteur te vormen en zijn eigenschappen in de bewaarplaats manueel te vormen.

### Nieuwe importmodule voor opiniepeiling toevoegen {#add-new-polling-importer}

* Meld u aan bij de primaire uitgever met beheerdersrechten en blader naar de pollingimporterconsole:

  Bijvoorbeeld: [http://localhost:4503/etc/importers/polling.html](http://localhost:4503/etc/importers/polling.html)

* Selecteren **[!UICONTROL Add]**

  ![opiniepeiling-importeur](assets/polling-importer.png)

* **[!UICONTROL Type]**

  *(Vereist)* Omlaag trekken en selecteren `POP3 (over SSL)`.

* **[!UICONTROL URL]**

  *(Vereist)* De uitgaande mailserver. Bijvoorbeeld: `pop.gmail.com:995/INBOX?username=community-emailgmail.com&password=****`.

* **[!UICONTROL Import to Path]**&amp;asteren;

  *(Vereist)* Instellen op `/content/usergenerated/mailFolder/postEmails`
door naar de `postEmails`map en selecteer **OK**.

* **[!UICONTROL Update Interval in Seconds]**

  *(Optioneel)* De postserver die voor de standaard postdienst wordt gevormd kan vereisten betreffende de waarde van het updateinterval hebben. Voor Gmail kan bijvoorbeeld een interval van `300`.

* **[!UICONTROL Login]**

  *(Optioneel)*

* **[!UICONTROL Password]**

  *(Optioneel)*

* Selecteren **[!UICONTROL OK]**.

### Protocol aanpassen voor nieuwe pollingimportmodule {#adjust-protocol-for-new-polling-importer}

Zodra de nieuwe opiniepeilingsconfiguratie wordt bewaard, is het noodzakelijk eigenschappen van de invoer van e-mail van het abonnement verder te wijzigen om het protocol van te veranderen `POP3` tot `emailreply`.

Gebruiken [CRXDE Lite](../../help/sites-developing/developing-with-crxde-lite.md):

* Meld u aan bij de primaire uitgever met beheerdersrechten en blader naar [https://&lt;server>:&lt;port>/crx/de/index.jsp#/etc/importers/polling](http://localhost:4503/crx/de/index.jsp#/etc/importers/polling).
* Selecteer de nieuwe configuratie en wijzig de volgende eigenschappen:

   * **feedType**: Vervangen `pop3s` with **`emailreply`**
   * **bron**: Bronprotocol vervangen `pop3s://` with **`emailreply://`**

![opiniepeilingprotocol](assets/polling-protocol.png)

De rode driehoeken geven de gewijzigde eigenschappen aan. Sla de wijzigingen op:

* Selecteren **[!UICONTROL Save All]**.
