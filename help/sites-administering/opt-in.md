---
title: Opteren in Adobe Analytics en Adobe Target
seo-title: Opteren in Adobe Analytics en Adobe Target
description: Leer hoe u zich aanmeldt bij Adobe Analytics en Adobe Target.
seo-description: Leer hoe u zich aanmeldt bij Adobe Analytics en Adobe Target.
uuid: 9090a0f3-d373-4826-aa68-6aa82c0fbfbb
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: integration
content-type: reference
discoiquuid: de466511-d82f-4ddb-8f6a-7ca9240fdeab
translation-type: tm+mt
source-git-commit: a3c303d4e3a85e1b2e794bec2006c335056309fb
workflow-type: tm+mt
source-wordcount: '1327'
ht-degree: 0%

---


# Naar Adobe Analytics en Adobe Target{#opting-into-adobe-analytics-and-adobe-target}

AEM heeft een opt-in procedure om u te helpen met Adobe Analytics en Adobe Target integreren. Dit is beschikbaar uit-van-de-doos, als vooraf geladen taak die aan de groep van de beheerdergebruiker wordt toegewezen.

Als u zich aanmeldt als beheerder, is deze taak (**Analytics configureren &amp; Targeting**) beschikbaar in [Inbox](/help/sites-authoring/inbox.md#out-of-the-box-administrative-tasks). Gebaseerd op de geloofsbrieven u levert, helpt het u deze diensten vormen en integreren.

U hebt de volgende opties voor het configureren van de integratie:

* Configureer de integratie via de taak.

   Dit kan onmiddellijk of later worden gedaan, zal de taak in Inbox blijven tot wat actie wordt ondernomen. In beide gevallen kan de configuratie rechtstreeks in de gebruikersinterface worden uitgevoerd of met behulp van een vooraf gedefinieerd `.properties`-bestand.

* Sluit af van de integratie.

   Overweeg deze optie als u de integratie [handmatig wilt configureren](/help/sites-administering/marketing-cloud.md). Zie ook [AEM integreren met Adobe Target en Adobe Analytics met behulp van DTM](https://helpx.adobe.com/experience-manager/using/integrate-digital-marketing-solutions.html).

* Configureer de instelling en provisioning met behulp van een script.

## De integratie {#configuring-the-integration} configureren

Opteren voor integratie met:

* Analyses om het gebruik van hun mogelijkheden van het volgen en van de analyse van pagina&#39;s toe te laten.
* Doel om het gebruik van hun verpersoonlijkingsmogelijkheden toe te laten.

Voor beide opties moet u de gegevens van de gebruikersaccount opgeven en de pagina&#39;s opgeven die worden bijgehouden.

>[!NOTE]
>
>U kunt desgewenst informatie over Analytics en Target-account opgeven met behulp van een eigenschappenbestand dat wordt gelezen bij het opstarten van de server. Zie [Accountinformatie verschaffen met behulp van een eigenschappenbestand](/help/sites-administering/opt-in.md#providing-account-information-using-a-properties-file).

Wanneer u zich bij de integratie aanmeldt, voert AEM de volgende taken uit:

* Maakt de wolkenconfiguraties die de verbinding met Analytics en Target toelaten.
* Maakt de frameworks die bepalen welke gegevens worden bijgehouden.
* Vormt de Web-pagina&#39;s om deze diensten te gebruiken.

>[!NOTE]
>
>AT.js is de standaardcliëntbibliotheek. Dit wordt gevormd onder uw [configuratie van de de wolkendiensten ](/help/sites-administering/target-configuring.md#creating-a-target-cloud-configuration).
>
>Adobe raadt u aan AT.js als clientbibliotheek te gebruiken.

Als u zich wilt aanmelden bij de vooraf geladen taak die buiten het vak valt:

1. Van uw [Inbox, selecteer en **Open** de Configure Analytics &amp; Targeting](/help/sites-authoring/inbox.md#taking-action-on-an-item) taak.

   ![optin-01](assets/optin-01.png)

1. Voor Analytics:

   1. Voer de gegevens van de gebruikersaccount voor Analytics in en klik op de bijbehorende knop **Toevoegen**.
   1. De juiste referenties worden geverifieerd.
   1. Als de account Analytics is geverifieerd, selecteert u de rapportsuite Analytics die u wilt gebruiken. AEM haalt die Analytics-rapportreeksen op. De status wordt bijgewerkt naar **Toegevoegd**.

1. Voor doel:

   1. Ga de informatie van de gebruikersrekening voor Doel in en klik dan de overeenkomstige **Add** knoop.
   1. De juiste referenties worden geverifieerd. De status wordt bijgewerkt naar **Toegevoegd**.

1. Selecteer **Volgende**.
1. Selecteer de sites waarvoor Analytics en/of Target moet worden gebruikt.

1. Selecteer **Done** om te voltooien.

   >[!CAUTION]
   >
   >Nadat u zich hebt aangemeld bij de configuratie, moet u de desbetreffende site of pagina&#39;s publiceren om deze wijzigingen te repliceren naar uw publicatie-instantie.

## Uitschakelen van integratie {#opting-out-of-the-integration}

Sluit de integratie met Analytics en Target af als u:

* Niet met deze producten integreren.
* Voorkeur om de integratie manueel te vormen.

   Zie [Integreren met Adobe Analytics](/help/sites-administering/adobeanalytics.md) en [Integreren met Adobe Target](/help/sites-administering/target.md) voor informatie over het handmatig configureren van de integratie.

Als u wilt afmelden, moet u de vooraf geladen taak voltooien:

* Van uw [Inbox, selecteer en **Complete** de Configure Analytics &amp; Targeting](/help/sites-authoring/inbox.md#taking-action-on-an-item) taak.

## Accountinformatie opgeven met een eigenschappenbestand {#providing-account-information-using-a-properties-file}

Installeer een eigenschappenbestand dat AEM leest bij het opstarten van de server om de accounteigenschappen voor de integratie met Analytics en Target te configureren. Wanneer u het eigenschappenbestand gebruikt, gebruikt de aanmeldwizard automatisch de eigenschappen van het bestand en wordt de cloudconfiguratie dienovereenkomstig gemaakt.

Het eigenschappenbestand is een tekstbestand met de naam marketingcloud.properties dat u opslaat in de werkmap die het AEM gebruikt (doorgaans dezelfde map als het JAR-bestand). Het bestand bevat de volgende eigenschappen:

* analytics.server: De URL van het datacenter Analytics dat u gebruikt.
* analytics.company: Het bedrijf dat aan uw Analytics gebruikersrekening wordt geassocieerd.
* analytics.username: Uw gebruikersnaam voor Analytics.
* analytics.geheime: Het geheim dat aan uw Analytics gebruikersnaam wordt geassocieerd.
* analytics.reportSuite: De naam van de te gebruiken analytische rapportsuite.
* target.clientCode: De clientcode die aan uw Target-account is gekoppeld.
* target.email: Het e-mailadres dat u gebruikt om uw Target-account te verifiëren.
* target.password: Het wachtwoord dat aan uw e-mailadres is gekoppeld.

Eigenschappen en waarden worden gescheiden met gelijke tekens (=). De eigenschappen Analytics hebben de voorvoegsel `analytics` en de eigenschappen Target hebben de voorvoegsel `target`. Om de dienst te vormen, verstrek waarden voor alle eigenschappen voor die dienst. Als u geen dienst wilt vormen, verstrek geen waarden voor die dienst.

Het volgende voorbeeld `.properties` dossier omvat de bezitswaarden voor het creëren van een wolkenconfiguratie voor Analytics:

```xml
analytics.server=https://test.omniture.com/login/
analytics.company=MyCompany
analytics.username=sbroders
analytics.secret=12345678
analytics.reportsuite=myreportsuite
target.clientcode=
target.email=
target.password=
```

In de volgende procedure wordt beschreven hoe u zich bij de integratie kunt aansluiten met behulp van het eigenschappenbestand.

1. Maak het `marketingcloud.properties`-bestand in de werkmap die het AEM gebruikt (auteurinstantie).

   >[!NOTE]
   >
   >De het werk folder is gewoonlijk de folder die de jar of `license.properties` dossier houdt.
   >
   >Nochtans, kan het ook als absolute weg door het systeembezit worden bepaald:
   >
   >`mac.provisioning.file.container`

1. Voeg de eigenschapswaarden toe volgens uw Analytics- en/of Target-accounts.
1. Start of start de server opnieuw op en meld u vervolgens aan met een beheerdersaccount.
1. Open de Configure Analytics &amp; Targeting taak zoals die in [het Vormen van de Integratie](/help/sites-administering/opt-in.md#configuring-the-integration) wordt beschreven. In plaats van om uw rekeningsinformatie te vragen, gebruikt de tovenaar de waarden van het `.properties` dossier.

   Selecteer **Add** voor de aangewezen dienst, dan met de tovenaar verder.

   ![optin-02](assets/optin-02.png)

## Informatie over de cloudconfiguraties {#about-the-cloud-configurations}

Wanneer u de integratie met Analytics en Target configureert, AEM automatisch de vereiste cloudconfiguraties en -frameworks. De cloudconfiguratie van Analytics heet bijvoorbeeld Provisioned Analytics Account.

U hoeft de cloudconfiguraties niet te wijzigen. Nochtans, kunt u het kader vormen zoals nodig. (Zie [Componentgegevens toewijzen met Adobe Analytics-eigenschappen](/help/sites-administering/adobeanalytics-mapping.md) en [Een doelframework toevoegen](/help/sites-administering/target.md).)

>[!NOTE]
>
>Wanneer u zich aanmeldt bij de Adobe Target-configuratietovenaar, wordt Accurate gericht inschakelen.
>
>Nauwkeurige het richten betekent dat de configuratie van de wolkendienst op de context wacht te laden alvorens inhoud te laden. Hierdoor kan het, in termen van prestaties, nauwkeuriger richten tot een paar milliseconde vertraging leiden alvorens inhoud te laden.
>
>Nauwkeurige het richten wordt altijd toegelaten op de auteursinstantie. Op de publicatieinstantie kunt u er echter voor kiezen de nauwkeurige oriëntatie globaal uit te schakelen door het vinkje naast Accurate gericht in de configuratie van de cloudservice (**http://localhost:4502/etc/cloudservices.html**) te wissen. U kunt nauwkeurige het richten voor individuele componenten ook nog uitzetten ongeacht uw plaatsen in de configuratie van de wolkendienst.
>
>Als u ***reeds*** gerichte componenten hebt gecreeerd en u dit het plaatsen verandert, beïnvloeden uw veranderingen niet die componenten. U moet om het even welke veranderingen in die component direct aanbrengen.

>[!CAUTION]
>
>Wanneer u in de configuratie van Analytics opteert en specifiek `reportsuite` wordt geselecteerd, dan is het kader beperkt tot publiceren looppas wijze. Dit betekent dat het bijhouden van wijzigingen alleen werkt op de publicatie-instantie.
>
>Als het volgen op een auteursinstantie eveneens nodig is zou de waarde in `all` moeten worden veranderd.

## Het vormen van de Opstelling en de Levering via Manuscript {#configuring-the-setup-and-provisioning-via-script}

Als beheerder, kunt u opstelling en levering met een manuscript eerder dan manueel het stappen door de tovenaar willen teweegbrengen. U kunt dit doen door:

* Verzenden van een verzoek van de POST naar **/libs/cq/cloudservicesprovisioning/content/autoprovisioning.json** met de vereiste parameters.

Welke parameters u verzendt hangt van het volgende af:

* Als u het **marketingcloud.properties** dossier wilt gebruiken dat met alle vereiste geloofsbrieven wordt gevuld, dan moet u de volgende parameters verzenden:

   * `automaticProvisioning`= `true`
   * `servicename`=  `analytics|target`
   * `path`=pad naar een AEM pagina om de gemaakte cloudservices te koppelen

   Bijvoorbeeld, zou een krullverzoek dat zowel tot Analytics als tot de configuraties van het Doel leidt en hen aan de wij.Retail pagina vastmaakt:

   ```shell
   curl -v -u admin:admin -X POST -d"automaticProvisioning=true&servicename=target&servicename=analytics&path=/content/we-retail" http://localhost:4502/libs/cq/cloudservicesprovisioning/content/autoprovisioning.json
   ```

* Als u niet het **marketingcloud.properties** dossier wilt gebruiken, dan zult u de geloofsbrieven evenals parameters moeten verzenden; bijvoorbeeld:

   * automaticProvisioning= `true`
   * servicename= `analytics|target`
   * path=path naar een AEM pagina om de gemaakte cloudservices te koppelen; meerdere paden kunnen worden gedefinieerd
   * analytics.server= `https://servername`
   * analytics.company= `Name of company`
   * analytics.username= `me`
   * analytics.geheime= `secret`
   * analytics.reportsuite= `we-retail`
   * target.clientCode= `mycompany`
   * target.email= `me@adobe.com`
   * target.password= `password`

   In dit geval, zou het curl verzoek dat zowel tot Analytics als tot configuraties leidt van het Doel en hen aan de wij-kleinhandel pagina vastmaakt zijn:

   ```shell
   curl -v -u admin:admin -X POST -d"automaticProvisioning=false&servicename=target&servicename=analytics&path=/content/we-retail&analytics.server=https://servername/&analytics.company=Name of company&analytics.username=me&analytics.secret=secret&analytics.reportsuite=weretail&target.clientcode=mycompany&target.email=me@adobe.com&target.password=password" http://localhost:4502/libs/cq/cloudservicesprovisioning/content/autoprovisioning.json
   ```

