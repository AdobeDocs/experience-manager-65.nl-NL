---
title: Opstelling en vorm de plaatsen van de de zelfdienstverwijzing van Web.Finance en van de Werknemer
seo-title: Opstelling en vorm de plaatsen van de de zelfdienstverwijzing van Web.Finance en van de Werknemer
description: De de verwijzingsplaatsen van AEM Forms tonen hoe u AEM Forms kunt gebruiken om werkschema's van begin tot eind in een organisatie uit te voeren.
seo-description: De de verwijzingsplaatsen van AEM Forms tonen hoe u AEM Forms kunt gebruiken om werkschema's van begin tot eind in een organisatie uit te voeren.
uuid: 199349b7-97bd-4eca-a2e7-19d6708fcbee
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: introduction
discoiquuid: 03886dd3-5873-4908-912b-fbbddb26c322
docset: aem65
translation-type: tm+mt
source-git-commit: 1dfc8fa91d3e5ae8ca49cf1f3cb739b59feb18cf
workflow-type: tm+mt
source-wordcount: '2788'
ht-degree: 0%

---


# Opstelling en vorm de plaatsen van de de zelfdienstverwijzing van Web.Finance en van de Werknemer{#set-up-and-configure-we-finance-and-employee-self-service-reference-sites}

AEM Forms bieden implementatie van referentiesites om aan te tonen hoe AEM Forms organisaties in de financiële-dienstensector en de overheid helpen bij het omvormen van hun complexe transacties in eenvoudige en aansprekende digitale ervaringen op elk gewenst moment.

Wij.De financiële referentieplaats trekt echte gebruiksgevallen om met bestaande en potentiële klanten, van het punt van eerste aanraking tot het beheren van correspondentie en transacties op een gepersonaliseerde en rendabele manier te werken.

Met de referentiesites kunt u de volgende belangrijke mogelijkheden van AEM Forms verkennen en weergeven.

* Vereenvoudigde ontwerpervaring met aantrekkelijke en responsieve adaptieve formulieren en interactieve communicatie.
* Interactieve Mededelingen om interactieve, gepersonaliseerde, en ontvankelijke klantenmededelingen tot stand te brengen die aan het apparaat het plaatsen en de lay-out aanpassen.
* Gegevensintegratie om verbinding te maken met verschillende gegevensbronnen om formuliergegevens vooraf in te vullen en te verzenden via een formuliergegevensmodel.
* Forms workflow om bedrijfsprocessen en workflows te automatiseren.
* Geavanceerde mogelijkheden voor gegevensbeheer en -verwerking door gebruikers.
* Integratie met Adobe Sign om adaptieve formulieren veilig te ondertekenen en te verzenden.
* Integratie met Adobe Target voor gerichte aanbevelingen en A/B-tests om het rendement van investeringen vanuit een formulier te maximaliseren.
* Integratie met Adobe Analytics om de prestaties van een formulier of campagne te meten en geïnformeerde beslissingen te nemen.
* Verbeterde functionaliteit voor het invullen van formulieren.

De referentiesites bieden herbruikbare elementen die u als sjablonen kunt gebruiken om uw eigen elementen te maken.

* Integratie met Adobe Sign om adaptieve formulieren veilig te ondertekenen en te verzenden.

* Integratie met Adobe Sign om adaptieve formulieren veilig te ondertekenen en te verzenden.

## Vereisten en stappen voor het instellen van referentiesites {#prerequisites-and-steps-to-set-up-reference-sites}

Voordat u de referentiesite instelt, moet u het volgende doen:

* **AEM-essentiële onderdelen** AEM QuickStart, AEM Forms add-on-pakket en referentiesite-pakketten. Zie de versies [van](https://helpx.adobe.com/aem-forms/kb/aem-forms-releases.html) AEM Forms voor toe:voegen-op en de pakketdetails van verwijzingsplaatsen.

* **Een dienst** SMTP U kunt om het even welke dienst gebruiken SMTP.

* **Adobe Sign-ontwikkelaarsaccount en Adobe Sign API-toepassing** Adobe Sign Developer account is vereist voor het gebruik van mogelijkheden voor digitale ondertekening. Zie [Adobe-ondertekening](https://acrobat.adobe.com/us/en/why-adobe/developer-form.html).

* Een lopende instantie van de Dynamiek 365 van Microsoft om met AEM Forms te integreren. Om de verwijzingsplaats in werking te stellen, voert u de steekproefgegevens in de instantie van de Dynamiek van Microsoft in om de interactieve mededeling vooraf in te vullen die in de verwijzingsplaats wordt gebruikt.
* Een actieve instantie van AEM met het pakket Forms add-on. Voor meer informatie, zie het [Installeren en het vormen AEM Forms](../../forms/using/installing-configuring-aem-forms-osgi.md).

Voer de volgende stappen in de geadviseerde opeenvolging uit aan opstelling en vorm de verwijzingsplaatsen.

<table>
 <tbody>
  <tr>
   <th><strong>Stap</strong></th>
   <th><strong>Configureren</strong></th>
   <th><strong>Opmerkingen</strong></th>
  </tr>
  <tr>
   <td><a href="#installandconfigureaemform">AEM Forms installeren en configureren</a></td>
   <td>Auteur en publicatie</td>
   <td>Installeer en configureer de auteur van AEM Forms en publiceer instanties.</td>
  </tr>
  <tr>
   <td><a href="#ssl">SSL configureren</a></td>
   <td>Author and Publish<br /> </td>
   <td>Schakel HTTP via SSL in voor veilige communicatie met Adobe Sign.</td>
  </tr>
  <tr>
   <td><p><a href="#externalizer">Configuratie van externe-alizer van de koppeling voor dag-CQ configureren</a></p> </td>
   <td>Author and Publish<br /> </td>
   <td><p>Verwijzingszaken voor gebruik op de site leveren e-mails voor verschillende transacties. Deze instelling is vereist voor levering via e-mail via nieuwsbrief. Hiermee zorgt u ervoor dat URL's en afbeeldingen verwijzen naar de publicatie-instantie. </p> </td>
  </tr>
  <tr>
   <td><a href="#cqmail">CQ-mailservice op dag configureren</a></td>
   <td>Auteur en publicatie</td>
   <td>Vereist voor e-mailcommunicatie.</td>
  </tr>
  <tr>
   <td><a href="#xss">Standaard XSS-configuratie overschrijven</a></td>
   <td>Publicatie</td>
   <td>Wordt gebruikt om $-, {- en }-tekens te overschrijven die door de XP-beveiliging worden geblokkeerd.</td>
  </tr>
  <tr>
   <td><a href="#aemds">AEM DS-instellingen configureren</a></td>
   <td>Auteur</td>
   <td>Configureer AEM DS voor het verzenden van formulieren op publicatieexemplaar en verwerkingsworkflows op de auteurinstantie.</td>
  </tr>
  <tr>
   <td><a href="#refsite">Referentiesites implementeren</a></td>
   <td>Auteur</td>
   <td>Implementeer pakketten met referentiesites op de auteur-instantie van AEM Forms.</td>
  </tr>
  <tr>
   <td><a href="../../forms/using/setup-reference-sites.md#optional-import-sample-data-into-microsoft-dynamics">Voorbeeldgegevens importeren in Microsoft Dynamics</a></td>
   <td>Auteur en publicatie</td>
   <td>Voorbeeldgegevens importeren voor toepassing via creditcard, hypotheektoepassing thuis en doorlopen van de toepassing voor thuisverzekering</td>
  </tr>
  <tr>
   <td><a href="../../forms/using/setup-reference-sites.md#configure-oauth-cloud-service-for-microsoft-dynamics">De OAuth-cloudservice voor Microsoft Dynamics configureren</a></td>
   <td>Auteur en publicatie</td>
   <td>Vorm de OAuth wolkendienst in AEM Forms om communicatie tussen AEM Forms en de Dynamiek van Microsoft toe te laten. </td>
  </tr>
  <tr>
   <td><a href="#scheduler">Adobe Sign Scheduler configureren</a></td>
   <td>Author and Publish<br /> </td>
   <td>Verander de configuratie van de planner om status om de twee minuten te controleren.</td>
  </tr>
  <tr>
   <td><a href="#sign-service">Referentiesite configureren, Adobe Sign Cloud Service</a></td>
   <td>Author and Publish<br /> </td>
   <td>Een configuratie die met de pakketten van verwijzingsplaatsen komt en herconfiguratie met geldige geloofsbrieven vereist.</td>
  </tr>
  <tr>
   <td><a href="#anonymous">Forms Common Configuration Service configureren voor anonieme gebruikers</a></td>
   <td>Publicatie</td>
   <td>Met de configuratie kunnen anonieme gebruikers een record genereren en verzenden, ondertekenen en documenten maken.</td>
  </tr>
  <tr>
   <td><a href="#fdm">Wijzig het Waggerbestand van de Rest Service voor het Model van de Gegevens van de Vorm</a></td>
   <td>Author and Publish<br /> </td>
   <td>Wijzig de service voor uw omgeving.</td>
  </tr>
 </tbody>
</table>

## AEM Forms installeren en configureren {#installandconfigureaemform}

Installeer en stel AEM Forms zoals die in het [Installeren en het vormen AEM Forms op OSGi](../../forms/using/installing-configuring-aem-forms-osgi.md)worden beschreven op.

>[!NOTE]
>
>Vorm replicatie en omgekeerde replicatieagenten als er meer dan één publiceer instanties zijn of de auteur en publiceer instanties zijn op verschillende machines.

## SSL configureren {#ssl}

SSL-configuratie is vereist voor communicatie met Adobe Sign-servers. Zie HTTP [via SSL](/help/sites-administering/ssl-by-default.md)inschakelen voor gedetailleerde stappen.

>[!CAUTION]
>
>Configureer geen geforceerde SSL op de `/etc/map` map.

## Configuratie van externe-alizer van de koppeling voor dag-CQ configureren {#externalizer}

In AEM, is **ExternalAlizer** de dienst OSGI die u toestaat om een middelweg programmatically om te zetten (b.v. /path/to/my/page) in een externe en absolute URL (bijvoorbeeld, https://www.mycompany.com/path/to/my/page) door het pad vooraf in te stellen met een vooraf geconfigureerde DNS. Zie URL&#39;s [extern maken](/help/sites-developing/externalizer.md).

>[!CAUTION]
>
>Voer geen externalisatie naar HTTPS URL uit als u een zelfondertekend certificaat voor SSL gebruikt.
>
>Gebruik ook localhost in plaats van de hostnaam voor de lokale server.

Voer de volgende stappen uit op zowel auteur- als publicatieinstanties:

1. Ga naar Configuratie OSGi in https://&lt;*hostname>*:&lt;*port>*/system/console/configMgr.
1. Zoek en tik de configuratie van de Verbinding Externalzer van de **Dag van CQ** .
Het dialoogvenster Day CQ Link Externalzer wordt geopend voor het bewerken van de configuratie.
1. In het dialoogvenster Day CQ Link Externalzer, in het veld Domains:

   * Geef voor de instantie van de auteur een publicatie-URL op die toegankelijk is via een extern systeem. Bijvoorbeeld een hostnaam of een publicatiewebserver.
   * Geef in de publicatie-instantie zowel de auteur als publicatie-URL&#39;s op.

1. Controleer in beide instanties of de URL van de lokale server is opgegeven in het veld Domains.
1. Tik op **Opslaan**. Wacht een tijdje op alle diensten opnieuw te beginnen.

## CQ-mailservice op dag configureren {#cqmail}

Voor de implementatie van een referentiesite moeten e-mails naar voorbeeldgebruikers worden verzonden wanneer deze formulieren invullen en verzenden. Door CQ-mailservice op de dag te configureren, kunt u SMTP-servicedetails leveren om geautomatiseerde e-mails naar klanten te verzenden. Zie E-mailmeldingen [configureren](/help/sites-administering/notification.md).

Voer de volgende stappen uit om de postdienst op te vormen publiceer instantie:

1. Ga naar Configuratie OSGi in https://&lt;*hostname>*:&lt;*port>*/system/console/configMgr.
1. Zoek en tik op CQ Mail Service **op** Dag om deze voor configuratie te openen.
1. Geef hostnaam en poortwaarden voor SMTP-servers op.
1. Tik op **Opslaan.**

>[!NOTE]
>
>U kunt uw collectieve dienst SMTP of openbare diensten zoals Gmail gebruiken. Voor het vormen van de dienst SMTP, zie de de dienstdocumentatie SMTP.

## Standaard XSS-configuratie overschrijven {#xss}

De e-mailsjablonen voor de website Web.Finance bevatten persoonlijke links in e-mails. Deze koppelingen hebben een tijdelijke aanduiding als `${placeholder}`. Deze plaatsaanduidingen worden vervangen door werkelijke waarden voordat ze e-mails verzenden. De standaard XSS-beveiligingsconfiguratie voor AEM staat accolades (**{}**) in de URL in HTML-inhoud niet toe. U kunt de standaardconfiguratie echter negeren door de volgende stappen uit te voeren bij een publicatie-instantie:

1. Kopiëren `/libs/cq/xssprotection/config.xml` naar `/apps/cq/xssprotection/config.xml`.
1. Open `/apps/cq/xssprotection/config.xml`.
1. Wijzig in de `common-regexps` sectie de `onsiteURL` vermelding als volgt en sla het bestand op.

   `<regexp name="onsiteURL" value="([\p{L}\p{N}\\\.\#@\$\{\}%\+&;\-_~,\?=/!\*\(\)]*|\#(\w)+)"/>`

>[!NOTE]
>
>accolades (**{}**) worden als geaccepteerde tekens opgenomen in de URL in HTML-inhoud.

Nadat u de SMTP-server hebt geconfigureerd, probeert u een formulier in te vullen met de persona Sarah Rose en het op te slaan als concept. Wanneer u opslaat als concept, krijgt u een optie om het concept via e-mail te ontvangen. Als u op de knop E-mail **** verzenden tikt en u een e-mail ontvangt met een koppeling naar het concept van de toepassing, is de configuratie van uw e-mail gelukt. Zorg ervoor dat u zich aanmeldt met de gegevens van Sarah om het concept te zien.

## AEM DS-instellingen configureren {#aemds}

AEM DS de montages van de Dienst worden vereist op de Publish instantie voor e-mailmededelingen in de gevallen van het het gebruik van de verwijzingsplaats. Voor gedetailleerde stappen om AEM DS de opstelling van de Dienst op de Publish instantie te vormen, zie [montages](../../forms/using/configuring-the-processing-server-url-.md)AEM DS vormen.

Geef in de AEM DS Settings Service voor AEM Forms-referentiesites de URL van de publicatieserver op in plaats van de URL van de verwerkingsserver.

>[!CAUTION]
>
>Plaats niet `/lc` in URL van de verwerkingsserver als u het voor AEM Forms OSGi vormt.

## Referentiesites implementeren {#refsite}

Installeer de pakketten met referentiesites met behulp van [Software Distribution](https://docs.adobe.com/content/help/en/experience-cloud/software-distribution/home.html).

* [Sitepakket AEM Forms FSI](https://www.adobeaemcloud.com/content/marketplace/marketplaceProxy.html?packagePath=/content/companies/public/adobe/packages/cq650/fd/AEM-FORMS-6.5-FSI-REF-SITE)
* [Sitepakket AEM Forms Gov](https://www.adobeaemcloud.com/content/marketplace/marketplaceProxy.html?packagePath=/content/companies/public/adobe/packages/cq650/fd/AEM-FORMS-6.5-GOV-REF-SITE)

Meer over leren hoe te om pakketten te gebruiken, zie [hoe te met Pakketten](/help/sites-administering/package-manager.md)werken.

Nadat u de pakketten hebt geïnstalleerd en de auteur hebt gestart en exemplaren hebt gepubliceerd, gaat u naar de volgende URL&#39;s in uw browser:

* `https://'[server]:[port]'/wegov`
* `https://'[server]:[port]'/wefinance`

Als de installatie is gelukt, hebt u toegang tot de bestemmingspagina&#39;s en Web.Finance.

## (Optioneel) Voorbeeldgegevens importeren in Microsoft Dynamics {#optional-import-sample-data-into-microsoft-dynamics}

De toepassing van de huishypotheek en de plaatsen van de autoverzekeringstoepassing worden gevormd om verslagen van de Dynamiek van Microsoft te gebruiken. Het pakket van de verwijzingsplaats installeert een douaneentiteit en steekproefverslagen die u in de Dynamiek van Microsoft kunt invoeren om de verwijzingsplaats in werking te stellen. Voer de volgende stappen uit om de voorbeeldgegevens te migreren en in te stellen:

U kunt als volgt de aangepaste entiteit importeren voor de toepassing voor automatische verzekering:

1. Download het **pakket met oplossingen WebFinanceAutoInsurance_1_0.zip** via `https://'[server]:[port]'/content/aemforms-refsite-collaterals/we-finance/auto-insurance/ms-dynamics/WeFinanceAutoInsurance_1_0.zip` de AEM-auteur.
1. Ga in de instantie van Microsoft Dynamics naar **Instellingen > Oplossingen** en klik op **Importeren**. Selecteer en importeer het pakket.

U kunt als volgt de aangepaste entiteit importeren voor de toepassing voor automatische verzekering:

1. Download het **AEMFormsFSIRefsite_1_0.zip** -pakket van `https://[author]:'port'/content/aemforms-refsite-collaterals/we-finance/home-mortgage/ms-dynamics/AEMFormsFSIRefsite_1_0.zip`. Selecteer en importeer het pakket.

1. Ga in de instantie van Microsoft Dynamics naar **Instellingen > Oplossingen** en klik op **Importeren**. Selecteer en importeer het pakket.

De gegevens van de klant en het verzekeringspolis importeren:

1. Download de bestanden **We.Finance Customers.csv, We.Finance Auto Insurance Renewals.csv**, en **home hypotheek** op de volgende locaties op uw AEM-auteur:

   * `https://'server':[port/content/aemforms-refsite-collaterals/we-finance/auto-insurance/ms-dynamics/We.Finance Customers.csv`
   * `https://'server':[port/content/aemforms-refsite-collaterals/we-finance/auto-insurance/ms-dynamics/We.Finance Auto Insurance Renewals.csv`
   * `https://'[server]:[port]'/content/aemforms-refsite-collaterals/we-finance/home-mortgage/ms-dynamics/Sarah%20Rose%20Contact.csv`

1. Ga als volgt te werk in de instantie Microsoft Dynamics:

   * Ga naar **Verkoop** > **We.Klanten** van Financiën en klik op **Importeren**.

   * Ga naar **Verkoop** > **We.Financiële automatische verzekering** en klik op **Importeren**.

   * Ga naar **Verkoop** > **We.Finance Home Mortgauge** en klik op **Importeren**.

## De OAuth-cloudservice voor Microsoft Dynamics configureren {#configure-oauth-cloud-service-for-microsoft-dynamics}

Vorm de OAuth wolkendienst in AEM Forms om communicatie tussen AEM Forms en de Dynamiek van Microsoft toe te laten. Voer de volgende stappen uit om de Cloud Service OAuth op auteur te vormen AEM en instanties te publiceren:

1. Ga in de auteur van AEM naar **Gereedschappen** > **Cloud Servicen** > **Gegevensbronnen** > **Algemeen**. Tik op het pictogram Dynamische integratie **van** opnieuw plaatsen en tik op Eigenschappen.
1. Ga naar Microsoft Azure Active Directory-account. Voeg de gekopieerde URL voor de configuratie van de cloudservice toe aan de instelling **Reageren-URL** voor uw geregistreerde toepassing. Sla de configuratie op.
1. In het lusje van de Montages van de Authentificatie, specificeer de Wortel **van de** Dienst, **Cliënt Id**, Geheime **** Cliënt, en **Middel URL** voor uw instantie van de Dynamica van Microsoft. Klik op **Verbinding maken met OAuth** die wordt omgeleid naar de aanmeldingspagina voor Microsoft Dynamics.
1. Geef uw aanmeldingsgegevens op. Nadat u zich hebt aangemeld, wordt u omgeleid naar de configuratiepagina van de cloudservice van AEM Forms. Klik op **Opslaan en sluiten**. De configuratie van de cloudservice wordt opgeslagen.
1. Ga naar **Forms** > **Data Integrations** > **We.Finance**. Selecteer Automatische verzekering (dynamiek) en klik op Bewerken. De entiteiten van de Dynamiek van Microsoft zijn vermeld onder de Bronnen van Gegevens tabel. Wacht tot alle entiteiten van de Dynamiek van Microsoft worden opgehaald en onder de gegevensbronnen tabel worden vermeld.
1. Selecteer de entiteit **AutoInsuranceRenewal** en klik op **Modelobject** testen. Geef in de sectie met invoerverzoeken de waarde voor de klant-id op als &quot;900001&quot; en klik op **Testen**. De sectie van de Output toont de verslagen die van de Dynamica van Microsoft voor klantenidentiteitskaart 900001 worden gehaald.
1. Geef in de sectie met invoerverzoeken de waarde voor de klant-id op als &quot;900001&quot; en klik op **Testen**. De sectie van de Output toont de verslagen die van de Dynamica van Microsoft voor klantenidentiteitskaart 900001 worden gehaald.
1. Herhaal stap 1-6 op de publicatie-instantie.

## Adobe Sign Scheduler configureren {#scheduler}

Doe het volgende op zowel auteur als publicatieinstanties:

1. Ga naar AEM Web Configuration Console op `https://'[server]:[port]'system/console/configMgr`.
1. Zoek en tik **[!UICONTROL Adobe Sign Configuration Service]** om het te openen voor configuratie.
1. Vorm **[!UICONTROL Status Update Scheduler Expression]** als **0 0/2 * * *?**.

   >[!NOTE]
   >
   >De bovenstaande plannerconfiguratie controleert de status van de Adobe-ondertekeningsservice elke twee minuten.

1. Tik op **[!UICONTROL Save]**.

## Referentiesite Adobe Sign Cloud Service configureren {#sign-service}

Doe het volgende op zowel auteur als publicatieinstanties:

1. Ga naar **Gereedschappen** > **Cloud Servicen** > **Adobe-ondertekening** > **Algemeen**. Selecteer **AEM Forms Referentie-site ondertekenen** en tik op Eigenschappen.

   >[!CAUTION]
   >
   >Zorg ervoor dat de `https://[host]:[ssl_port]/mnt/overlay/adobesign/cloudservices/adobesign/properties.html` URL wordt toegevoegd aan de lijst voor omleiding van de OAuth-configuratie van de Adobe Sign API-toepassing.

1. Geef de client-id en het geheim van de OAuth-configuratie voor de Adobe-toepassing ondertekenen op.
1. (Optioneel) Selecteer de **[!UICONTROL Enable Adobe Sign for attachments also]** optie en tik op **[!UICONTROL Connect to Adobe Sign]**. De bestanden die zijn gekoppeld aan een adaptief formulier, worden toegevoegd aan het corresponderende Adobe Sign-document dat is verzonden voor ondertekening.
1. Tik met uw Adobe-ondertekeningsgegevens op **[!UICONTROL Connect to Adobe Sign]** en meld u aan.

## Forms Common Configuration Service configureren {#anonymous}

Ga als volgt te werk op de publicatie-instantie om toegang tot anonieme gebruikers toe te staan:

1. Ga naar AEM Web Configuration Console op `https://'[server]:[port]'/system/console/configMgr`.
1. Zoek en tik **[!UICONTROL Forms Common Configuration Service]** om het te openen voor configuratie.
1. Configureer het **[!UICONTROL Allow]** veld voor **[!UICONTROL All Users]**.
1. Tik op **[!UICONTROL Save]**.

## Rest Service wijzigen voor formuliergegevensmodel {#fdm}

Doe het volgende op zowel auteur als publicatieinstanties:

1. Ga naar CRXDE om `https://'[server]:[port]'/crx/de/index.jsp`.
1. Navigeer naar **/conf/global/settings/cloudconfigs/fdm/roi-rest/jcr:content/swaggerFile** en open het gameterbestand.
1. Werk de host- en poortinstellingen naar wens bij in uw omgeving.
1. Sla de instellingen op.
1. (Alleen **** instantie Auteur) Ga naar **Gereedschappen** > **Cloud Servicen** > **Gegevensbronnen** > **Algemeen**. Selecteer **de rij-rij** en tik **Eigenschappen**.Tik de Montages **van de** Authentificatie van de Tik en reeks het Type **van** Authentificatie aan **Basisauthentificatie**. Geef `admin`/ op `admin`als gebruikersnaam/wachtwoord voor toegang tot de service. Tik op **Opslaan en sluiten**.

## Integreren met Marketing Cloud {#integrate-with-marketing-cloud}

U kunt de AEM Forms integreren met Adobe Analytics en Adobe Target. Hoewel Adobe Analytics u helpt rapporten te genereren en de prestaties van adaptieve formulieren te analyseren, helpt Adobe Target u om persoonlijke ervaringen op te doen en A/B-tests uit te voeren voor adaptieve formulieren.

Ga als volgt te werk om Adobe Analytics en Adobe Target in AEM Forms te configureren.

### Adobe Analytics configureren {#configureanalytics}

Dankzij de integratie van AEM Forms met Adobe Analytics kunt u controleren en analyseren hoe uw klanten omgaan met uw formulieren en documenten. Hiermee kunt u probleemgebieden herkennen en corrigeren en de conversiesnelheid verhogen.

Als u deze functionaliteit wilt ervaren op de referentiesite, configureert u uw Analytics-account zoals beschreven in Analytics [Configuring en Reports](../../forms/using/configure-analytics-forms-documents.md).

Om een rapport te produceren, worden de zaadgegevens gebundeld met de verwijzingsplaatsen. Voer de volgende handelingen uit voordat u zaadgegevens gebruikt:

1. Zorg ervoor dat wij.Finance analytische configuraties beschikbaar zijn in de AEM cloud services. U kunt cloudservices op een van de volgende manieren vinden:

   * Navigeer naar https://&lt;host>:&lt;port>/libs/cq/core/content/tools/cloudservices.html. **[!UICONTROL Tools>Cloud Services>Legacy Cloud Services]**
   * Klik op de **[!UICONTROL Cloud Services]** pagina onder **[!UICONTROL Adobe Analytics]** de sectie `Show Configurations`. U kunt de beschikbare configuraties van Web.Finance zien. Klik om de configuratie te openen. Klik op de configuratiepagina **[!UICONTROL Edit]**. Geef een geldig bedrijf, gebruikersnaam, gedeeld geheim (wachtwoord) en datacenter op en klik op **[!UICONTROL Connect to Analytics]**. Als het dialoogvenster Verbinding gelukt is, klikt u op **[!UICONTROL OK]** het configuratiedialoogvenster. Configureer het framework onder de Analytics-configuratie zoals beschreven in de [Configuring Analytics and Reports](../../forms/using/configure-analytics-forms-documents.md).

1. Ga naar https://&lt;*host*>:&lt;*port*>/system/console/configMgr en voer de volgende handelingen uit:

   * Zoek en klik op de **[!UICONTROL Web Console Configuration]** pagina **[!UICONTROL AEM Forms Analytics Configuration]**.

   * Op het **[!UICONTROL SiteCatalyst Framework]** gebied van de dialoog van de Configuratie van AEM Forms Analytics, selecteer wij-financiert (wij-financiert) of wij-gov (wij-gov).
   * Klik **[!UICONTROL Save]** en laat de pagina verfrissen.

1. Ga naar formulierbeheer op https://&lt;host>:&lt;port>/aem/forms en voer de volgende handelingen uit:

   * Open de map Web.Finance en selecteer het formulier waarvoor u het rapport wilt weergeven.
   * Klik op Analytics inschakelen op de werkbalk Handelingen. Nadat u analyses voor het formulier hebt ingeschakeld, klikt u op Analytics-rapport. Er wordt een leeg rapport gegenereerd. Nadat een leeg rapport wordt geproduceerd, moet u zaadgegevens verstrekken die van refsite pakket worden verscheept om analytische rapport voor demodoel te produceren.

   Referentiesites bieden analyses die gegevens bevatten over de aanvraag van een creditcard, hypotheek op woningen en gebruik van kinderondersteuning.

### Target configureren {#configure-target}

De referentiesite toont de integratie van AEM Forms met Adobe Target, waarmee u doelgerichte en gepersonaliseerde inhoud kunt opnemen in adaptieve documenten. Ook kunnen er A/B-tests voor adaptieve formulieren worden gemaakt.

Ga als volgt te werk om Target in AEM te configureren, zodat u de integratie in de referentiesite kunt ervaren:

1. Start de auteur quickstart met het jvm-argument `-Dabtesting.enabled=true` om A/B-tests op de server in te schakelen.

   >[!NOTE]
   >
   >Als de instantie AEM op JBoss loopt, die als dienst van de installatie van de Sleutel is begonnen, voeg de `-Dabtesting.enabled=true` parameter in de volgende ingang in het `jboss\bin\standalone.conf.bat` dossier toe:
   `set "JAVA_OPTS=%JAVA_OPTS% -Dadobeidp.serverName=server1 -Dfile.encoding=utf8 -Djava.net.preferIPv4Stack=true -Dabtesting.enabled=true"`

1. Ga naar `https://<hostname>:<port>/libs/cq/core/content/tools/cloudservices.html`.

1. Klik in de **[!UICONTROL Adobe Target]** sectie op **[!UICONTROL Show Configurations]**. U kunt de beschikbare Configuratie van de Configuratie van Wij.Financiën Target zien. Klik om de configuratie te openen. Klik op de configuratiepagina **[!UICONTROL Edit]**. Het **[!UICONTROL Edit Component]** dialoogvenster voor de configuratie wordt geopend.

1. Geef uw clientcode, e-mail en wachtwoord op die aan uw Target-account zijn gekoppeld. Selecteer API-type als **[!UICONTROL REST]**.
1. Klik op **[!UICONTROL Connect to Adobe target]**. Klik op de knop Target-account als de configuratie is voltooid. **[!UICONTROL OK]** U kunt zien dat de verpakte configuratie een Target Framework heeft.

1. Go to `https://<hostname>:<port>/system/console/configMgr`.

1. Klik op **[!UICONTROL AEM Forms Target Configuration]**.
1. Selecteer een Target-framework.
1. Geef in het **[!UICONTROL Target URLs]** veld de URL op naar AEM Forms. Bijvoorbeeld: `https://<hostname>:<port>/`.

1. Klik op **[!UICONTROL Save]**.

In gevallen waarin gebruik wordt gemaakt van creditcardaanvragen en Home Mortgauge wordt getoond hoe een A/B-test kan worden uitgevoerd en een rapport kan worden weergegeven voor demodoeleinden. Voor analyses, zie [Wij.Finance verwijzingsplaatsanalyse](../../forms/using/finance-reference-site-walkthrough.md).

## Volgende stap {#next-step}

Nu bent u allen klaar om de verwijzingsplaats te onderzoeken. Zie voor meer informatie over de workflow en stappen van de verwijzingssite:

* [We.Financiële referentiesite doorlopen](../../forms/using/finance-reference-site-walkthrough.md)
* [Werknemerslijst voor zelfbedieningsverwijzingssite](../../forms/using/employee-self-service-reference-site.md)

