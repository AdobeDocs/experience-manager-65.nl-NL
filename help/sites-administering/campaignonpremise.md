---
title: Integreren met Adobe Campaign Classic
seo-title: Integreren met Adobe Campaign Classic
description: Leer hoe u AEM kunt integreren met Adobe Campaign Classic
seo-description: Leer hoe u AEM kunt integreren met Adobe Campaign Classic
uuid: 3c998b0e-a885-4aa9-b2a4-81b86f9327d3
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: integration
content-type: reference
discoiquuid: df94dd1b-1b65-478b-a28d-81807a8084b1
translation-type: tm+mt
source-git-commit: 684d2d5f73d571a15c8155e7870134c28dc892b7

---


# Integreren met Adobe Campaign Classic{#integrating-with-adobe-campaign-classic}

>[!NOTE]
>
>In deze documentatie wordt beschreven hoe u AEM kunt integreren met Adobe Campaign Classic, de on-premise oplossing. Als u Adobe Campaign Standard gebruikt, raadpleegt u [Integratie met Adobe Campagnestandaard](/help/sites-administering/campaignstandard.md) voor de desbetreffende instructies.

Met Adobe Campaign kunt u inhoud en formulieren voor e-maillevering rechtstreeks beheren in Adobe Experience Manager.

Om beide oplossingen samen tezelfdertijd te gebruiken, moet u hen eerst vormen om met elkaar te verbinden. Hiervoor moeten configuratiestappen worden uitgevoerd in zowel Adobe Campaign als Adobe Experience Manager. Deze stappen worden in dit document uitgebreid beschreven.

Als u met Adobe Campaign werkt in AEM, kunt u e-mail verzenden via Adobe Campaign. Dit wordt beschreven in [Werken met Adobe Campagne](/help/sites-authoring/campaign.md). Dit omvat ook het gebruik van formulieren op AEM-pagina&#39;s voor het bewerken van gegevens.

Bovendien kunnen de volgende onderwerpen van belang zijn bij de integratie van AEM met [Adobe-campagne](https://helpx.adobe.com/support/campaign/classic.html):

* [Aanbevolen procedures voor e-mailsjablonen](/help/sites-administering/best-practices-for-email-templates.md)
* [Problemen met de integratie van Adobe Campagne oplossen](/help/sites-administering/troubleshooting-campaignintegration.md)

Als u uw integratie met Adobe Campaign uitbreidt, wilt u wellicht de volgende pagina&#39;s zien:

* [Aangepaste extensies maken](/help/sites-developing/extending-campaign-extensions.md)
* [Aangepaste formuliertoewijzingen maken](/help/sites-developing/extending-campaign-form-mapping.md)

## Workflow voor AEM- en Adobe Campagne Integration {#aem-and-adobe-campaign-integration-workflow}

In deze sectie wordt een typische workflow beschreven tussen AEM en Adobe Campaign voor het maken van campagnes en het leveren van inhoud.

De typische werkstroom omvat het volgende en wordt in detail beschreven:

1. Maak uw campagne (zowel in Adobe Campaign als in AEM).
1. Voordat u de inhoud en levering koppelt, past u de inhoud aan in AEM en maakt u een levering in Adobe Campaign.
1. Inhoud en levering koppelen in Adobe Campaign.

### Uw campagne maken {#start-building-your-campaign}

Je begint op elk moment een campagne te ontwikkelen. Voordat u de inhoud koppelt, zijn AEM en AC onafhankelijk. Dit betekent dat marketers hun campagnes kunnen starten en zich kunnen richten in Adobe Campaign, terwijl makers van inhoud aan het ontwerp werken in AEM.

### Voordat inhoud en levering worden gekoppeld {#before-linking-content-and-delivery}

Voordat u de inhoud koppelt en een leveringsmechanisme maakt, moet u het volgende doen:

**In AEM**

* Persoonlijk maken met de verpersoonlijkingsvelden in de component **Tekst en personalisatie**

**In Adobe-campagne**

* Een levering van het type **AemContent maken**

### Inhoud koppelen en levering instellen {#linking-content-and-setting-delivery}

Nadat u de inhoud voor het verbinden en levering hebt voorbereid, bepaalt u precies hoe en waar om inhoud te verbinden.

Al deze stappen zijn voltooid in de Campagne van Adobe.

1. Geef op welke AEM-instantie moet worden gebruikt.
1. Synchroniseer de inhoud door op de knop Synchroniseren te klikken.
1. Open de inhoudkiezer om de inhoud te kiezen.

### Als u nog geen ervaring hebt met AEM {#if-you-are-new-to-aem}

Als u nog niet eerder met AEM werkt, zijn de volgende koppelingen wellicht handig om AEM te begrijpen:

* [AEM starten](/help/sites-deploying/deploy.md)
* [Replicatieagents begrijpen](/help/sites-deploying/replication.md)
* [Logbestanden zoeken en gebruiken](/help/sites-deploying/monitoring-and-maintaining.md#working-with-audit-records-and-log-files)
* [Inleiding tot het AEM-platform](/help/sites-deploying/platform.md)

## Adobe-campagne configureren {#configuring-adobe-campaign}

Het configureren van Adobe Campaign omvat het volgende:

1. Het AEM-integratiepakket installeren in Adobe Campaign.
1. Een externe account configureren.
1. Controleren of AEMResourceTypeFilter correct is geconfigureerd.

Bovendien zijn er geavanceerde configuraties die u kunt maken, die omvatten:

* Inhoudsblokken beheren
* Verpersoonlijkingsvelden beheren

Zie [Geavanceerde configuraties](#advanced-configurations).

>[!NOTE]
>
>Als u deze bewerkingen wilt uitvoeren, moet u de **beheerrol** in Adobe Campaign hebben.

### Vereisten {#prerequisites}

Zorg ervoor dat u de volgende elementen vooraf hebt:

* [Een AEM-ontwerpinstantie](/help/sites-deploying/deploy.md#getting-started)
* [Een AEM-publicatie-instantie](/help/sites-deploying/deploy.md#author-and-publish-installs)
* [Een Klassieke Adobe Campagne-instantie](https://helpx.adobe.com/support/campaign/classic.html) - inclusief een client en een server
* Internet Explorer 11

>[!NOTE]
>
>Raadpleeg de [upgradedocumentatie](https://docs.campaign.adobe.com/doc/AC6.1/en/PRO_Updating_Adobe_Campaign_Upgrading.html) voor meer informatie als u een eerdere versie uitvoert dan Adobe Campaign Classic build 8640. Merk op dat zowel de cliënt als het gegevensbestand aan zelfde bouwstijl moeten worden bevorderd.

>[!CAUTION]
>
>Voor de juiste werking van de integratiefuncties tussen AEM en Adobe Campaign [zijn bewerkingen nodig die worden beschreven in de secties Adobe Experience Manager](#configuring-adobe-campaign) [](#configuring-adobe-experience-manager) configureren en configureren.

### Het AEM-integratiepakket installeren {#installing-the-aem-integration-package}

U moet het pakket **AEM Integration** installeren in Adobe Campaign. Dit doet u als volgt:

1. Ga naar de Adobe Campagne-instantie die u wilt koppelen aan AEM.
1. *Selecteer* Gereedschappen *>* Geavanceerd *>* Pakket importeren... .

   ![chlimage_1-132](assets/chlimage_1-132a.png)

1. Klik op **Een standaardpakket** installeren en selecteer het pakket **AEM-integratie** .

   ![chlimage_1-133](assets/chlimage_1-133a.png)

1. Klik op **Volgende** en vervolgens **Starten**.

   Dit pakket bevat de **serveroperator** die wordt gebruikt om de AEM-server te verbinden met Adobe Campaign.

   >[!CAUTION]
   >
   >Door gebrek, wordt geen veiligheidsstreek gevormd voor deze exploitant. Als u via AEM verbinding wilt maken met Adobe Campaign, moet u er een selecteren.
   >
   >In het bestand **serverConf.xml** moet het kenmerk **allowUserPassword** van de geselecteerde beveiligingszone op **true** worden ingesteld om AEM te machtigen om Adobe Campagne te verbinden via aanmelding/wachtwoord.
   >
   >We raden u ten zeerste aan een beveiligingszone voor AEM te maken om beveiligingsproblemen te voorkomen. Raadpleeg de [installatiehandleiding](https://docs.campaign.adobe.com/doc/AC/en/INS_Additional_configurations_Configuring_Campaign_server.html)voor meer informatie.

   ![chlimage_1-134](assets/chlimage_1-134a.png)

### Een externe AEM-account configureren {#configuring-an-aem-external-account}

U moet een externe account configureren waarmee u Adobe Campaign kunt verbinden met uw AEM-instantie.

>[!NOTE]
>
>* Wanneer u het **AEM Integration** -pakket installeert, wordt een externe AEM-account gemaakt. U kunt de verbinding met uw instantie AEM van het vormen of nieuwe tot stand brengen.
>* Zorg er in AEM voor dat u het wachtwoord voor de externe gebruiker van de campagne instelt. U moet dit wachtwoord instellen om Adobe Campaign te verbinden met AEM. Login als beheerder en in de console van het gebruikersbeleid, onderzoek naar de campagne-verre gebruiker en klik **Vastgestelde Wachtwoord**.
>



Een externe AEM-account configureren:

1. Ga naar het knooppunt **Beheer** > **Platform** > **Externe accounts** .
1. Maak een nieuwe externe account en selecteer het **AEM** -type.
1. Voer de toegangsparameters voor uw AEM-ontwerpinstantie in: het serveradres en de id en het wachtwoord waarmee u verbinding maakt met deze instantie. Het wachtwoord voor de campagne-api-gebruikersaccount is hetzelfde als de externe gebruiker waarvoor u een wachtwoord instelt in AEM.

   >[!NOTE]
   >
   >Zorg ervoor dat het serveradres **niet** eindigt in een sluitslash. Voer bijvoorbeeld in `https://yourserver:4502` plaats van `https://yourserver:4502/`

   ![chlimage_1-135](assets/chlimage_1-135a.png) ![chlimage_1-136](assets/chlimage_1-136a.png)

1. Controleer of het selectievakje **Ingeschakeld** is ingeschakeld.

### De optie AEMResourceTypeFilter controleren {#verifying-the-aemresourcetypefilter-option}

De optie **AEMResourceTypeFilter** wordt gebruikt om typen AEM-bronnen te filteren die kunnen worden gebruikt in Adobe-campagne. Hierdoor kan Adobe Campaign AEM-inhoud ophalen die speciaal is ontworpen om alleen in Adobe Campaign te worden gebruikt.

Deze optie moet vooraf worden geconfigureerd; als u deze optie wijzigt, kan dit echter tot een niet-functionerende integratie leiden.

Om te verifiëren wordt de optie **AEMResourceTypeFilter** gevormd:

1. Ga naar **Platform** >**Opties**.
1. Controleer in de **optie AEMResourceTypeFilter** of de paden juist zijn. Dit veld moet de waarde bevatten:

   **mcm/campagne/componenten/nieuwsbrief,mcm/campagne/componenten/campagne_newsletterpage,mcm/neolane/components/nieuwsbrief**

   In sommige gevallen is de waarde als volgt:

   **mcm/campagne/componenten/nieuwsbrief**

   ![chlimage_1-137](assets/chlimage_1-137a.png)

## Adobe Experience Manager configureren {#configuring-adobe-experience-manager}

Om AEM te vormen, moet u het volgende doen:

* Configureer replicatie tussen instanties.
* Verbind AEM met de Campagne van Adobe via de Diensten van de Wolk.
* Configureer de externalizer.

### Replicatie tussen AEM-instanties configureren {#configuring-replication-between-aem-instances}

Inhoud die is gemaakt van de AEM-ontwerpinstantie wordt eerst naar de publicatieinstantie verzonden. U moet publiceren zodat de afbeeldingen in de nieuwsbrief beschikbaar zijn op de publicatie-instantie en aan ontvangers van de nieuwsbrief. De replicatieagent moet daarom worden gevormd om van de auteursinstantie AEM aan de het publiceren instantie AEM te herhalen.

>[!NOTE]
>
>Als u niet replicatie URL wilt gebruiken maar in plaats daarvan openbaar-onder ogen ziet URL gebruiken, kunt u **Openbare URL** in de volgende configuratie plaatsen die in OSGi (het embleem **van** AEM > **Hulpmiddelen** pictogram > **Verrichtingen** > **Web** **** ****> de ConfiguratieConsoleSGAEM Campaign Integratie - ConfiguratieUitgebreid):
**** Openbare URL: com.day.cq.mcm.campagne.impl.IntegrationConfigImpl#aem.mcm.campagne.publicUrl

Deze stap is ook nodig om bepaalde configuraties van ontwerpinstanties te repliceren in de publicatieinstantie.

Om replicatie tussen AEM instanties te vormen:

1. Selecteer in de ontwerpinstantie **AEM-logo**> **Gereedschapspictogram** > **Implementatie** > **Replicatie** > **agents op auteur****** en klik vervolgens op Default Agent.

   ![chlimage_1-138](assets/chlimage_1-138a.png)

   >[!NOTE]
   Gebruik geen localhost (dat wil zeggen een lokale kopie van AEM) wanneer u uw integratie met Adobe Campaign configureert, tenzij de publicatie- en auteurinstantie zich beide op dezelfde computer bevinden.

1. Tik of klik op **Bewerken** en selecteer het tabblad **Vervoer** .
1. Vorm URI door **localhost** met het IP adres of het adres van de AEM het publiceren instantie te vervangen.

   ![chlimage_1-139](assets/chlimage_1-139a.png)

### AEM verbinden met Adobe-campagne {#connecting-aem-to-adobe-campaign}

Voordat u AEM en Adobe Campaign samen kunt gebruiken, moet u het verband tussen beide oplossingen tot stand brengen zodat zij kunnen communiceren.

1. Maak verbinding met uw AEM-ontwerpinstantie.
1. Selecteer **AEM-logo** > **Gereedschapspictogram** > **Implementatie** > **Cloud Services** en **configureer nu** in de sectie Adobe Campagne.

   ![chlimage_1-140](assets/chlimage_1-140a.png)

1. Maak een nieuwe configuratie door een **titel** in te voeren en op **Maken** te klikken, of kies de bestaande configuratie die u met uw instantie van de Campagne van Adobe wilt verbinden.
1. Bewerk de configuratie zodat deze overeenkomt met de parameters van uw Adobe Campagne-instantie.

   * **Gebruikersnaam**: **aemserver**, de AEM-pakketoperator voor campagnes van Adobe die wordt gebruikt om de koppeling tussen de twee oplossingen tot stand te brengen.
   * **Wachtwoord**: Wachtwoord voor Adobe Campagne-serveroperator. Mogelijk moet u het wachtwoord voor deze operator opnieuw opgeven in Adobe Campaign.
   * **API-eindpunt**: Instantie-URL van Adobe Campagne.

1. Selecteer **Verbinding maken met Adobe-campagne** en klik op **OK**.

   ![chlimage_1-141](assets/chlimage_1-141a.png)

   >[!NOTE]
   Nadat u uw e-mail hebt [gemaakt en deze](/help/sites-authoring/campaign.md)hebt gepubliceerd, moet u de configuratie opnieuw publiceren naar uw publicatie-exemplaar.

   ![chlimage_1-142](assets/chlimage_1-142a.png)

>[!NOTE]
Als de verbinding ontbreekt, zorg ervoor u het volgende controleert:
* Er kan een certificaatprobleem optreden wanneer u een beveiligde verbinding met een Adobe Campagne-instantie (https) gebruikt. U moet het Adobe Campagne-instantiecertificaat toevoegen aan het **cacerts** -bestand van de JDK van uw AEM-instantie.
* Er moet een beveiligingszone worden geconfigureerd voor de [serveroperator](#connecting-aem-to-adobe-campaign) in Adobe Campaign. Bovendien moet in het bestand **serverConf.xml** het kenmerk **allowUserPassword** van de beveiligingszone op **true** worden ingesteld om AEM-verbinding met Adobe Campaign te autoriseren met de modus voor aanmelding/wachtwoord.

Zie [Problemen met uw integratie](/help/sites-administering/troubleshooting-campaignintegration.md)van AEM/Adobe-campagnes oplossen.

### De externalizer configureren {#configuring-the-externalizer}

U moet de externalizer [in AEM op uw auteursinstantie](/help/sites-developing/externalizer.md) vormen. ExternalAlizer is de dienst OSGi die u een middelweg in een externe en absolute URL laat omzetten. Deze service biedt een centrale plaats om die externe URL&#39;s te configureren en samen te stellen.

Zie [De externalizer](/help/sites-developing/externalizer.md) configureren voor algemene instructies. Voor de integratie van de Campagne van Adobe, zorg ervoor u de publicatieserver op `https://<host>:<port>/system/console/configMgr/com.day.cq.commons.impl.ExternalizerImpl`geen punt aan `localhost:4503` maar aan een server vormt die door de console van de Campagne van Adobe bereikbaar is.

Als de component verwijst naar `localhost:4503` een andere server die niet kan worden bereikt met Adobe Campaign, worden de afbeeldingen niet weergegeven op de Adobe Campaign-console.

![chlimage_1-143](assets/chlimage_1-143a.png)

## Geavanceerde configuraties {#advanced-configurations}

U kunt ook een aantal geavanceerde configuraties uitvoeren, namelijk:

* U kunt aanpassingsvelden en -blokken beheren.
* Deactiveer een verpersoonlijkingsblok.
* Doelextensiegegevens beheren.

### Verpersoonlijkingsvelden en -blokken beheren {#managing-personalization-fields-and-blocks}

De velden en blokken die beschikbaar zijn om personalisatie toe te voegen aan uw e-mailinhoud in AEM, worden beheerd door Adobe Campagne.

Er is een standaardlijst opgegeven, maar deze kan worden gewijzigd. U kunt ook aanpassingsvelden en blokken toevoegen of verbergen.

#### Een aanpassingsveld toevoegen {#adding-a-personalization-field}

Als u een nieuw aanpassingsveld wilt toevoegen aan de reeds beschikbare toepassingen, moet u het schema Adobe Campagne **nms:seedMember** als volgt uitbreiden:

>[!CAUTION]
Het veld dat u moet toevoegen, moet al zijn toegevoegd via een extensie van het ontvangende schema (**nms:ontvanger**). Voor meer informatie, zie de gids van de [Configuratie](https://docs.campaign.adobe.com/doc/AC6.1/en/CFG_Editing_schemas_Editing_schemas.html) .

1. Ga naar het knooppunt **Beheer** > **Configuratie** > **Gegevensschema&#39;s** in de Adobe Campagne-navigatie.
1. Selecteer **Nieuw**.

   ![chlimage_1-144](assets/chlimage_1-144a.png)

1. Selecteer in het pop-upvenster de optie De gegevens in de tabel **uitbreiden met een extensieschema** en klik op **Volgende**.

   ![chlimage_1-145](assets/chlimage_1-145a.png)

1. Voer de verschillende parameters van het uitgebreide schema in:

   * **Schema**: Selecteer het schema **nms:seedMember** . De overige velden in het venster worden automatisch ingevuld.
   * **Naamruimte**: pas namespace van het uitgebreide schema aan.

1. Bewerk de XML-code van het schema om het veld op te geven dat u daar wilt toevoegen. Raadpleeg de handleiding [Configuratie voor meer informatie over het uitbreiden van schema&#39;s in Adobe Campaign](https://docs.campaign.adobe.com/doc/AC6.1/en/CFG_Editing_schemas_Extending_a_schema.html).
1. Sla het schema op en werk de databasestructuur van de Adobe Campagne bij via de **opties** > **Geavanceerd** > **Databasestructuur** bijwerken in de console.
1. Maak de verbinding en maak vervolgens opnieuw verbinding met de Adobe Campagne-console om uw wijzigingen op te slaan. Het nieuwe veld wordt nu weergegeven in de lijst met personalisatievelden in AEM.

#### Voorbeeld {#example}

Als u een veld **Registratienummer** wilt toevoegen, moet u over de volgende elementen beschikken:

* De **nms:ontvankelijke** schemauitbreiding genoemd **cus:ontvanger** bevat:

```xml
<element desc="Recipient table (profiles)" img="nms:recipient.png" label="Recipients" labelSingular="Recipient" name="recipient">

  <attribute dataPolicy="smartCase" desc="Recipient registration number"
  label="Registration Number"
  length="50" name="registrationNumber" type="string"/>

</element>
```

De **nms:seedMember** schema-extensie genaamd **cus:seedMember** bevat:

```xml
<element desc="Seed to insert in the export files" img="nms:unknownad.png" label="Seed addresses" labelSingular="Seed" name="seedMember">

  <element name="custom_nms_recipient">
    <attribute name="registrationNumber"
    template="cus:recipient:recipient/@registrationNumber"/>
  </element>

</element>
```

Het veld **Registratienummer** maakt nu deel uit van de beschikbare verpersoonlijkingsvelden:

![chlimage_1-146](assets/chlimage_1-146.png)

#### Een personalisatieveld verbergen {#hiding-a-personalization-field}

Als u een verpersoonlijkingsgebied onder die wilt verbergen die reeds beschikbaar zijn, moet u het schema van de Campagne van Adobe **nms:zaadLid** uitbreiden zoals die in de [Adding a verpersoonlijkingsgebied](#adding-a-personalization-field) sectie wordt beschreven. Voer de volgende stappen uit:

1. Kopieer het veld dat u wilt ophalen uit het schema **nms:zaadlid** in het uitgebreide schema (**bijvoorbeeld cus:zaadlid** ).
1. Voeg het kenmerk **advanced=&quot;true&quot;** XML toe aan het veld. Het wordt niet meer weergegeven in de lijst met personalisatievelden in AEM.

   Als u bijvoorbeeld het veld **Tweede naam** wilt verbergen, moet het schema **cud:zaadlid** het volgende element bevatten:

   ```xml
   <element desc="Seed to insert in the export files" img="nms:unknownad.png" label="Seed addresses" labelSingular="Seed" name="seedMember">
   
     <element name="custom_nms_recipient">
       <attribute advanced="true" name="middleName"/>
     </element>
   
   </element>
   ```

### Een aanpassingsblok deactiveren {#deactivating-a-personalization-block}

Een van de beschikbare personalisatieklokken deactiveren:

1. Ga naar het knooppunt **Bronnen** > **Campagnebeheer** > **Aanpassingsblokken** in de Adobe Campagne-navigatie.
1. Selecteer het verpersoonlijkingsblok dat u in AEM wilt deactiveren.
1. Schakel het selectievakje **Visible in de aanpassingsmenu** &#39;s uit en sla uw wijzigingen op. Het blok wordt niet meer weergegeven in de lijst met aanpassingsblokken die beschikbaar zijn in Adobe Campaign.

   ![chlimage_1-147](assets/chlimage_1-147a.png)

### Doelextensiegegevens beheren {#managing-target-extension-data}

U kunt de gegevens van de doeluitbreiding voor verpersoonlijking ook opnemen. De gegevens van de uitbreiding van het doel (ook genoemd &quot;Gegevens van het Doel&quot;), komen uit het verrijken van of het toevoegen van gegevens in een vraag in een campagnewerkschema bijvoorbeeld. Voor meer informatie, verwijs naar het [Creëren van vragen](https://docs.campaign.adobe.com/doc/AC/en/PTF_Creating_queries_About_queries_in_Campaign.html) en het [Verrijken van gegevenssecties](https://docs.campaign.adobe.com/doc/AC/en/WKF_Use_cases_Enriching_data.html) .

>[!NOTE]
De gegevens in het doel zijn alleen beschikbaar als de AEM-inhoud is gesynchroniseerd met de levering van een Adobe-campagne. Zie In AEM gemaakte inhoud [synchroniseren met een levering vanuit Adobe Campaign](/help/sites-authoring/campaign.md#synchronizing-content-created-in-aem-with-a-delivery-from-adobe-campaign-classic).

![chlimage_1-148](assets/chlimage_1-148a.png)

