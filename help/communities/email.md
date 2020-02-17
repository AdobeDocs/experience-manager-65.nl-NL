---
title: E-mail configureren
seo-title: E-mail configureren
description: E-mailconfiguratie voor gemeenschappen
seo-description: E-mailconfiguratie voor gemeenschappen
uuid: e8422cc2-1594-43b0-b587-82825636cec1
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: b4d38e45-eaa0-4ace-a885-a2e84fdfd5a1
pagetitle: Configuring Email
translation-type: tm+mt
source-git-commit: 58fa0f05bae7ab5ba51491be3171b5c6ffbe870d

---


# E-mail configureren {#configuring-email}

AEM-gemeenschappen gebruiken e-mail voor

* [Publikaties](notifications.md)
* [Communityabonnementen](subscriptions.md)

De e-mailfunctie werkt standaard niet omdat hiervoor een SMTP-server en een SMTP-gebruiker moet worden opgegeven.

>[!CAUTION]
>
>E-mail voor meldingen en abonnementen moet alleen op de [primaire uitgever](deploy-communities.md#primary-publisher)worden geconfigureerd.

## Standaardconfiguratie e-mailservice {#default-mail-service-configuration}

De standaardmailservice is vereist voor zowel meldingen als abonnementen.

* Op de primaire uitgever
* Aangemeld met beheerdersrechten
* Toegang tot de [webconsole](../../help/sites-deploying/configuring-osgi.md)

   * Bijvoorbeeld: [http://localhost:4503/system/console/configMgr](http://localhost:4503/system/console/configMgr)

* Zoek de `Day CQ Mail Service`
* Het bewerkingspictogram selecteren

Dit is gebaseerd op de documentatie voor het [Vormen E-mailbericht](../../help/sites-administering/notification.md), maar met een verschil in dat het gebied `"From" address` niet ** wordt vereist en leeg zou moeten blijven.

Bijvoorbeeld (alleen invullen met waarden voor illustratieve doeleinden):

![chlimage_1-98](assets/chlimage_1-98.png)

* **[!UICONTROL hostnaam]** SMTP-server: *(vereist)* De SMTP-server die moet worden gebruikt.

* **[!UICONTROL SMTP-serverpoort]** *(vereist)* De SMTP-serverpoort moet 25 of hoger zijn.

* **[!UICONTROL SMTP-gebruiker]**: *(vereist)* De SMTP-gebruiker.

* **[!UICONTROL SMTP-wachtwoord]**: *(vereist)* Het wachtwoord van de SMTP-gebruiker.

* **[!UICONTROL Adres]**&quot;Van&quot;: Leeg laten
* **[!UICONTROL SMTP gebruikt SSL]**: Als deze optie is ingeschakeld, wordt beveiligde e-mail verzonden. Zorg ervoor dat de poort is ingesteld op 465 of zoals is vereist voor de SMTP-server.
* **[!UICONTROL Foutopsporing in e-mail]**: Indien gecontroleerd, laat registreren van SMTP serverinteractie toe.

## E-mailconfiguratie van AEM-gemeenschappen {#aem-communities-email-configuration}

Zodra de [standaardpostdienst](#default-mail-service-configuration) wordt gevormd, worden de twee bestaande instanties van `AEM Communities Email Reply Configuration` OSGi config, inbegrepen in de versie, functioneel.

Slechts moet de instantie voor abonnementen verder worden gevormd wanneer het toestaan van antwoord door e-mail.

1. ` [email](#configuration-for-notifications)` instance

   voor meldingen, die geen ondersteuning bieden voor e-mail met antwoorden en die niet mogen worden gewijzigd

1. ` [subscriptions-email](#configuration-for-subscriptions)` instance

   vereist configuratie om het creëren van post van antwoord e-mail volledig toe te laten

U bereikt als volgt de e-mailconfiguratieinstanties van de Gemeenschappen:

* Op de primaire uitgever
* Aangemeld met beheerdersrechten
* Toegang tot de [webconsole](../../help/sites-deploying/configuring-osgi.md)

   * Bijvoorbeeld: [http://localhost:4503/system/console/configMgr](http://localhost:4503/system/console/configMgr)

* Zoeken `AEM Communities Email Reply Configuration`

![chlimage_1-99](assets/chlimage_1-99.png)

### Configuratie voor meldingen {#configuration-for-notifications}

De instantie van `AEM Communities Email Reply Configuration` OSGi config met de e-mail van de Naam is telefoontifications eigenschap. Deze functie bevat geen e-mailantwoord.

Deze configuratie moet niet worden gewijzigd.

* Zoek de `AEM Communities Email Reply Configuration`
* Het bewerkingspictogram selecteren
* Controleer of de **naam** is `email`

* Controleren of **bericht maken van antwoordbericht** is `unchecked`

![chlimage_1-100](assets/chlimage_1-100.png)

### Configuratie voor abonnementen {#configuration-for-subscriptions}

Voor Gemeenschapsabonnementen is het mogelijk om de mogelijkheid voor een lid om inhoud te posten in of uit te schakelen door op een e-mail te antwoorden.

* Zoek de `AEM Communities Email Reply Configuration`
* Het bewerkingspictogram selecteren
* Controleer of de **naam** is `subscriptions-email`

![chlimage_1-101](assets/chlimage_1-101.png)

* **[!UICONTROL Naam]** : *(vereist)* `subscriptions-email`. Niet bewerken.

* **[!UICONTROL Berichten maken van antwoorde-mail]**: Als deze optie is ingeschakeld, kan de ontvanger van het e-mailbericht met abonnement inhoud posten door een antwoord te verzenden. Standaard is ingeschakeld.
* **[!UICONTROL Bijgehouden id toevoegen aan koptekst]**:Standaard is dit `Reply-To`.

* **[!UICONTROL Maximumlengte van onderwerp]**: Als tracker-id aan de onderwerpregel wordt toegevoegd, is dit de maximumlengte van het onderwerp, met uitzondering van de bijgehouden id, waarna het wordt bijgesneden. Deze waarde moet zo klein mogelijk zijn om te voorkomen dat bijgehouden id-informatie verloren gaat. De standaardwaarde is 200.
* **[!UICONTROL E-mailadres]**&quot;Van&quot;: *(vereist)* Adres dat de e-mail van de melding zou worden geleverd van. Waarschijnlijk de zelfde die gebruiker **** SMTP voor de [standaardpostdienst](#configuredefaultmailservice)wordt gespecificeerd. Standaard is dit `no-reply@example.com`.

* **[!UICONTROL Reageren op scheidingsteken]**: Als tracker-id wordt toegevoegd aan de header die reageert, wordt dit scheidingsteken gebruikt. De standaardwaarde is `+` (plusteken).

* **[!UICONTROL Prefix van Beheer-id in onderwerp]**: Als tracker-id aan de onderwerpregel wordt toegevoegd, wordt dit voorvoegsel gebruikt. Standaard is dit `post#`.

* **[!UICONTROL Voorvoegsel van tracker-id in berichttekst]**: Als tracker-id aan de hoofdtekst van het bericht wordt toegevoegd, wordt dit voorvoegsel gebruikt. Standaard is dit `Please do not remove this:`.

* **[!UICONTROL E-mailen als HTML]**: Als deze optie is ingeschakeld, wordt het inhoudstype van e-mail ingesteld op `"text/html;charset=utf-8"`. Standaard is ingeschakeld.

* **[!UICONTROL Standaardgebruikersnaam]**: Deze naam wordt gebruikt voor geen naamgebruikers. Standaard is dit `no-reply@example.com`.

* **[!UICONTROL Hoofdpad]** sjablonen: De e-mail wordt samengesteld met een sjabloon die op dit hoofdpad is opgeslagen. Standaard is dit `/etc/community/templates/subscriptions-email`.

## Opiniepeilingimportmodule configureren {#configure-polling-importer}

Om de e-mail in de gegevensopslagplaats te brengen, is het noodzakelijk om een opiniepeilingimporteur te vormen en zijn eigenschappen in de bewaarplaats manueel te vormen.

### Nieuwe importmodule voor opiniepeiling toevoegen {#add-new-polling-importer}

* Op de primaire uitgever
* Aangemeld met beheerdersrechten
* Blader naar de pollingimporterconsoleBijvoorbeeld [http://localhost:4503/etc/importers/polling.html](http://localhost:4503/etc/importers/polling.html)
* Selecteer **[!UICONTROL Toevoegen]**

![chlimage_1-102](assets/chlimage_1-102.png)

* **[!UICONTROL Type]**: *(vereist)* Trek omlaag om te selecteren `POP3 (over SSL).`

* **[!UICONTROL URL]**: *(vereist)* De uitgaande mailserver. Bijvoorbeeld, `pop.gmail.com:995/INBOX?username=community-emailgmail.com&password=****`

* **[!UICONTROL Importeren naar pad]**&amp;ast: *(vereist)* Stel dit in `/content/usergenerated/mailFolder/postEmails`door naar de `postEmails`map te bladeren en **OK te selecteren**

* **[!UICONTROL Interval bijwerken in seconden]**: *(facultatief)* de postserver die voor de standaard postdienst wordt gevormd kan vereisten betreffende de waarde van het updateinterval hebben. Het is bijvoorbeeld mogelijk dat Gmail een interval van `300`vereist.

* **[!UICONTROL Aanmelden]**: *(optioneel)*

* **[!UICONTROL Wachtwoord]**: *(optioneel)*

* Selecteer **[!UICONTROL OK]**

### Protocol aanpassen voor nieuwe pollingimportmodule {#adjust-protocol-for-new-polling-importer}

Nadat de nieuwe stemconfiguratie is opgeslagen, moeten de eigenschappen van de e-mailimportfunctie met abonnement verder worden gewijzigd om het protocol te wijzigen van `POP3` naar `emailreply`

Met [CRXDE Lite](../../help/sites-developing/developing-with-crxde-lite.md):

* Op de primaire uitgever
* Aangemeld met beheerdersrechten
* Ga naar [https://&lt;server>:&lt;port>/crx/de/index.jsp#/etc/importers/polling](http://localhost:4503/crx/de/index.jsp#/etc/importers/polling)
* Selecteer de nieuwe configuratie
* De volgende eigenschappen wijzigen

   * **feedType**: vervangen `pop3s` door **`emailreply`**
   * **bron**: protocol van bron vervangen `pop3s://` door **`emailreply://`**

![chlimage_1-103](assets/chlimage_1-103.png)

De rode driehoeken geven de gewijzigde eigenschappen aan. Sla de wijzigingen op:

* Alles **[!UICONTROL opslaan selecteren]**

