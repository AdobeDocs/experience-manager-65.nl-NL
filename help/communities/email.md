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
solution: Experience Manager
feature: Communities
source-git-commit: 1f56c99980846400cfde8fa4e9a55e885bc2258d
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
>E-mail voor berichten en abonnementen moet slechts op de [&#x200B; primaire uitgever &#x200B;](deploy-communities.md#primary-publisher) worden gevormd.

## Standaardconfiguratie e-mailservice {#default-mail-service-configuration}

De standaardmailservice is vereist voor zowel meldingen als abonnementen.

* Login aan de primaire uitgever met beheerdervoorrecht en toegang tot de [&#x200B; Console van het Web &#x200B;](../../help/sites-deploying/configuring-osgi.md):

   * Bijvoorbeeld, [&#x200B; http://localhost:4503/system/console/configMgr](http://localhost:4503/system/console/configMgr)

* Zoek de `Day CQ Mail Service` .
* Selecteer het pictogram Bewerken.

Dit is gebaseerd op de documentatie voor [&#x200B; het Vormen E-mailBericht &#x200B;](../../help/sites-administering/notification.md), maar met een verschil op dat het gebied `"From" address` ** vereist is en zou leeg moeten worden verlaten.

Bijvoorbeeld (alleen invullen met waarden voor illustratieve doeleinden):

![&#x200B; e-mail-config &#x200B;](assets/email-config.png)

* **[!UICONTROL SMTP server host name]**

  *(Vereist)* De te gebruiken server SMTP.

* **[!UICONTROL SMTP server port]**

  *(Vereist)* De SMTP serverhaven moet 25 of hoger zijn.

* **[!UICONTROL SMTP user]**

  *(Vereist)* De gebruiker SMTP.

* **[!UICONTROL SMTP password]**

  *(Vereist)* het wachtwoord van de gebruiker SMTP.

* **[!UICONTROL "From" address]**

  Leeg laten
* **[!UICONTROL SMTP use SSL]**

  Als deze optie is ingeschakeld, wordt een beveiligde e-mail verzonden. Zorg ervoor dat de haven aan 465 of zoals vereist voor een server SMTP wordt geplaatst.
* **[!UICONTROL Debug email]**

  Indien gecontroleerd, laat dit registreren van SMTP serverinteractie toe.

## AEM Communities E-mailconfiguratie {#aem-communities-email-configuration}

Zodra de [&#x200B; standaard postdienst &#x200B;](#default-mail-service-configuration) wordt gevormd, worden de twee bestaande instanties van `AEM Communities Email Reply Configuration` OSGi config, inbegrepen in de versie, functioneel.

Slechts moet de instantie voor abonnementen verder worden gevormd wanneer het toestaan van antwoord door e-mail.

1. [&#x200B; E-mail &#x200B;](#configuration-for-notifications) instantie:

   Voor meldingen, die geen ondersteuning bieden voor e-mailantwoorden, en deze mogen niet worden gewijzigd.

1. [&#x200B; Subscriptions-email &#x200B;](#configuration-for-subscriptions) instantie:

   Vereist configuratie om het creëren van post van antwoorde-mail volledig toe te laten.

U bereikt als volgt de e-mailconfiguratieinstanties van de Gemeenschappen:

* Login aan de primaire uitgever met beheerdervoorrecht en toegang tot de [&#x200B; Console van het Web &#x200B;](../../help/sites-deploying/configuring-osgi.md)

   * Bijvoorbeeld, [&#x200B; http://localhost:4503/system/console/configMgr](http://localhost:4503/system/console/configMgr)

* Zoek `AEM Communities Email Reply Configuration` .

![&#x200B; e-mail-antwoord-config &#x200B;](assets/email-reply-config.png)

### Configuratie voor meldingen {#configuration-for-notifications}

De instantie van `AEM Communities Email Reply Configuration` OSGi config met de Naam e-mail is de eigenschap van berichten. Deze functie bevat geen e-mailantwoord.

Wijzig deze configuratie niet.

* Zoek de `AEM Communities Email Reply Configuration` .
* Selecteer het pictogram Bewerken.
* Verifieer dat de **Naam** `email` is.

* Verifieer dat **post van antwoorde-mail** `unchecked` creeert is.

![&#x200B; vorm-e-mail-antwoord &#x200B;](assets/configure-email-reply.png)

### Configuratie voor abonnementen {#configuration-for-subscriptions}

Voor Gemeenschapsabonnementen is het mogelijk om de mogelijkheid voor een lid om inhoud te posten in of uit te schakelen door op een e-mail te antwoorden.

* Zoek de `AEM Communities Email Reply Configuration` .
* Selecteer het pictogram Bewerken.
* Verifieer dat de **Naam** `subscriptions-email` is.

  ![&#x200B; vorm-e-mail-abonnement &#x200B;](assets/configure-email-subscriptions.png)

* **[!UICONTROL Name]**

  *(Required)* `subscriptions-email`. Niet bewerken.

* **[!UICONTROL Create post from reply email]**

  Als deze optie is ingeschakeld, kan de ontvanger van een e-mailbericht met abonnement inhoud plaatsen door een antwoord te verzenden. Standaard is ingeschakeld.
* **[!UICONTROL Add tracked id to header]**

  De standaardwaarde is `Reply-To` .

* **[!UICONTROL Maximum length of Subject]**

  Als tracker-id aan de onderwerpregel wordt toegevoegd, is dit de maximumlengte van het onderwerp, met uitzondering van de bijgehouden id, waarna het wordt bijgesneden. Dit moet zo klein mogelijk zijn om te voorkomen dat bijgehouden id-informatie verloren gaat. De standaardwaarde is 200.

* **[!UICONTROL "Reply-To" email address]**

  Adres dat als &quot;antwoord-aan&quot;e-mailadres wordt gebruikt. De standaardwaarde is `no-reply@example.com` .

* **[!UICONTROL Reply-to-Delimiter]**

  Als tracker-id wordt toegevoegd aan de header die reageert, wordt dit scheidingsteken gebruikt. De standaardwaarde is `+` (plusteken).

* **[!UICONTROL Tracker Id prefix in subject]**

  Als tracker-id aan de onderwerpregel wordt toegevoegd, wordt dit voorvoegsel gebruikt. De standaardwaarde is `post#` .

* **[!UICONTROL Tracker id prefix in message body]**

  Als tracker-id aan de hoofdtekst van het bericht wordt toegevoegd, wordt dit voorvoegsel gebruikt. De standaardwaarde is `Please do not remove this:` .

* **[!UICONTROL Email as HTML]**: Als deze optie is ingeschakeld, wordt het inhoudstype van e-mail ingesteld op `"text/html;charset=utf-8"` . Standaard is ingeschakeld.

* **[!UICONTROL Default user name]**

  Deze naam wordt gebruikt voor geen naamgebruikers. De standaardwaarde is `no-reply@example.com` .

* **[!UICONTROL Templates root path]**

  De e-mail wordt samengesteld met behulp van een sjabloon die is opgeslagen op dit hoofdpad. De standaardwaarde is `/etc/community/templates/subscriptions-email` .

## Opiniepeilingimportmodule configureren {#configure-polling-importer}

Voor de e-mail die naar de gegevensopslagplaats moet worden gebracht, is het noodzakelijk om een opiniepeilingimporteur te vormen en zijn eigenschappen in de bewaarplaats manueel te vormen.

### Nieuwe importmodule voor opiniepeiling toevoegen {#add-new-polling-importer}

* Meld u aan bij de primaire uitgever met beheerdersrechten en blader naar de pollingimporterconsole:

  Bijvoorbeeld, [&#x200B; http://localhost:4503/etc/importers/polling.html](http://localhost:4503/etc/importers/polling.html)

* Selecteren **[!UICONTROL Add]**

  ![&#x200B; opiniepeiling-importeur &#x200B;](assets/polling-importer.png)

* **[!UICONTROL Type]**

  *(Vereist)* Trek neer om te selecteren `POP3 (over SSL)`.

* **[!UICONTROL URL]**

  *(Vereist)* De uitgaande postserver. Bijvoorbeeld `pop.gmail.com:995/INBOX?username=community-emailgmail.com&password=**&#x200B;**` .

* **[!UICONTROL Import to Path]**&ast;

  *(Required)* Reeks aan `/content/usergenerated/mailFolder/postEmails`
door aan de `postEmails` omslag te doorbladeren en **O.K.** te selecteren.

* **[!UICONTROL Update Interval in Seconds]**

  *(Facultatief)* de postserver die voor de standaard postdienst wordt gevormd kan vereisten betreffende de waarde van het updateinterval hebben. Voor Gmail is bijvoorbeeld een interval van `300` vereist.

* **[!UICONTROL Login]**

  *(Optioneel)*

* **[!UICONTROL Password]**

  *(Optioneel)*

* Selecteer **[!UICONTROL OK]** .

### Protocol aanpassen voor nieuwe pollingimportmodule {#adjust-protocol-for-new-polling-importer}

Nadat de nieuwe opiniepeilingsconfiguratie is opgeslagen, moeten de eigenschappen van de e-mailimportmodule met abonnement verder worden gewijzigd om het protocol te wijzigen van `POP3` in `emailreply` .

Gebruikend [&#x200B; CRXDE Lite &#x200B;](../../help/sites-developing/developing-with-crxde-lite.md):

* Login aan de primaire uitgever met beheerdervoorrecht en doorblader aan [&#x200B; https://&lt;server>:&lt;port>/crx/de/index.jsp#/etc/importers/polling &#x200B;](http://localhost:4503/crx/de/index.jsp#/etc/importers/polling).
* Selecteer de nieuwe configuratie en wijzig de volgende eigenschappen:

   * **feedType**: Vervang `pop3s` met **`emailreply`**
   * **bron**: Vervang bronprotocol `pop3s://` met **`emailreply://`**

![&#x200B; polling-protocol &#x200B;](assets/polling-protocol.png)

De rode driehoeken geven de gewijzigde eigenschappen aan. Sla de wijzigingen op:

* Selecteer **[!UICONTROL Save All]** .
