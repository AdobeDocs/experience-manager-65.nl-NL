---
title: Configureren [!DNL Workfront for Experience Manager enhanced connector]
description: Configureren [!DNL Workfront for Experience Manager enhanced connector]
role: Admin
feature: Workfront Integrations and Apps
exl-id: 2660de7c-0281-4884-98d9-e78f20cf571c
hide: true
solution: Experience Manager, Workfront
source-git-commit: 5ccac0aadce3971e66da052d393cbd33b61e94f7
workflow-type: tm+mt
source-wordcount: '1583'
ht-degree: 0%

---

# Configureren [!DNL Workfront for Experience Manager enhanced connector] {#assets-integration-overview}

| Versie | Artikelkoppeling |
| -------- | ---------------------------- |
| AEM as a Cloud Service | [Klik hier](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/assets/integrations/workfront-connector-configure.html?lang=en) |
| AEM 6,5 | Dit artikel |

Een gebruiker met beheerdertoegang in [!DNL Adobe Experience Manager] vormt de verbeterde schakelaar na het installeren van het. Zie voor instructies voor installatie [De connector installeren](/help/assets/workfront-integrations.md).

>[!IMPORTANT]
>
>* Adobe vereist implementatie en configuratie van de [!DNL Adobe Workfront for Experience Manager enhanced connector] alleen via gecertificeerde partners of [!DNL Adobe Professional Services]. Indien opgesteld en gevormd zonder een verklaarde partner of [!DNL Adobe Professional Services], wordt het niet ondersteund door Adobe.
>
>* Adobe kan updates vrijgeven voor [!DNL Adobe Workfront] en [!DNL Adobe Experience Manager] die deze schakelaar overtollig maken; als dit voorkomt, kunnen de klanten aan overgang van het gebruik van deze schakelaar worden vereist.
>
>* Adobe ondersteunt verbeterde connectorversies 1.7.4 en hoger. Eerdere pre-release en aangepaste versies worden niet ondersteund. Navigeer naar de `digital.hoodoo` groep beschikbaar in het linkerdeelvenster in [Pakketbeheer](https://experienceleague.adobe.com/docs/experience-manager-65/administering/contentmanagement/package-manager.html?lang=en).
>
>* Zie [Partnercertificatieexamen voor Workfront voor verbeterde connector voor Experience Manager Assets](https://solutionpartners.adobe.com/solution-partners/home/applications/experience_cloud/workfront/journey/dev_core.html). Voor informatie over het examen, zie [Handleiding voor Examen](https://express.adobe.com/page/Tc7Mq6zLbPFy8/).

## Gebeurtenisabonnementen configureren {#event-subscriptions}

Gebeurtenisabonnementen worden gebruikt om AEM op de hoogte te brengen van gebeurtenissen die plaatsvinden in [!DNL Adobe Workfront]. Er zijn drie [!DNL Workfront for Experience Manager enhanced connector] zijn de volgende functies die gebeurtenisabonnementen nodig hebben om te werken:

* Automatisch maken van aan een project gekoppelde mappen.
* Synchronisatie van wijzigingen in Workfront-document aangepaste formulierwaarden naar metagegevens van AEM element.
* Automatische bekendmaking van activa aan Brand Portal na voltooiing van het project.

Schakel gebeurtenisabonnementen in als u deze functies wilt gebruiken.

* Bewerken [!UICONTROL Workfront Tools] De configuratie van Cloud Servicen u in stap 5 creeerde en selecteert [!UICONTROL Event Subscriptions] tab.
* Selecteer de [!UICONTROL Workfront Custom Integration] die u in sectie 6 hebt gemaakt.
* Klik op [!UICONTROL Enable Workfront Event Subscriptions].

  ![Abonnement voor gebeurtenissen](/help/assets/assets/event-subs.png)

## Gekoppelde mappen configureren {#linked-folders}

Voer de volgende stappen uit om u te abonneren op de gebeurtenissen:

1. Ga naar de **[!UICONTROL Event Subscriptions]** in de cloudservices.
1. Selecteer de aangepaste integratie die u hebt gemaakt in [!DNL Workfront].
1. Klik op **[!UICONTROL Enable Workfront Event Subscriptions]**.

### Configuratie van gekoppelde mapstructuur {#linked-folder-structure}

1. Ga naar het tabblad Gekoppelde projectmappen in de cloudservices.
1. Bovenliggend pad van gekoppelde map: selecteer een map in de DAM waar u de gekoppelde mappen wilt maken. Als het verlaten leeg blijft, zal het aan /content/dam in gebreke blijven. Controleer of het metagegevensschema voor Workfront Tools en het metagegevensschema voor de map Workfront Linked Folder zijn toegepast op de geselecteerde map.
1. Gekoppelde mapstructuur: voer door komma&#39;s gescheiden waarden in. Elke waarde moet `DE:<some-project-custom-form-field>`, Portfolio, Program, Year, Name of een of andere &#39;Letterlijke tekenreekswaarde&#39; (deze laatste met aanhalingstekens). Deze is momenteel ingesteld op Portfolio,Programma,Jaar,DE:Projecttype,Naam.
1. Machtigingen configureren: toevoegen `jcr:all permissions` machtigingen voor `/conf/workfront-tools/settings/cloudconfigs` for `wf-workfront-users` groep.
1. De functie voor het maken van gekoppelde mappen in Workfront met het selectievakje voor mapstructuurnamen moet zijn ingeschakeld als de titel van de map in Workfront alle mappen in de structuur moet bevatten. Anders is dit de titel van de laatste map.
1. Met submappen met meerdere velden kunt u een lijst opgeven met mappen die moeten worden gemaakt als een onderliggende map van de gekoppelde map.
1. Projectstatus: selecteer de status van het project om de gekoppelde map te maken.
1. Maak een gekoppelde map in projecten met een portfolio: lijst met Portfolio&#39;s waartoe het project moet behoren om de gekoppelde map te maken. Laat deze lijst leeg om de gekoppelde map voor alle projectportfolio te maken.
1. Maak een gekoppelde map in projecten met een aangepast formulierveld: aangepast formulierveld en de bijbehorende waarde die het project nodig heeft om de gekoppelde map te maken. Deze configuratie wordt genegeerd als deze leeg wordt gelaten. Selecteren `CUSTOM FORMS: Create DAM Linked Folder` voor het veld en de invoer `Yes` voor de waarde.
1. Klik op Automatisch maken van gekoppelde mappen inschakelen. Als u teruggaat naar het tabblad Gebeurtenisabonnementen, ziet u dat er nu een gebeurtenis create is.

![gekoppelde mapconfiguratie](/help/assets/assets/wf-linked-folder-config.png)

## Metagegevensschematoewijzing {#metadata-schema-mapping}

### Mapmetagegevenstoewijzing configureren {#folder-metadata-mapping}

Metagegevenstoewijzing tussen Workfront-projecten en AEM mappen wordt gedefinieerd in AEM schema&#39;s met metagegevens van mappen. Metagegevensschema&#39;s voor mappen moeten op de gebruikelijke wijze in AEM worden gemaakt en geconfigureerd. Workfront Tools voegt een automatisch aanvullen vervolgkeuzelijst toe aan het tabblad Settings-configuratie van elk formulierveld voor het schema van metagegevens van de map. In dit keuzemenu voor automatisch aanvullen kunt u opgeven aan welk Workfront-veld elke AEM mapeigenschap moet worden toegewezen.

Voer de volgende stappen uit om de toewijzingen te configureren:

1. Toevoegen `jcr:read` machtigingen voor `/conf/global/settings/dam/adminui-extension/foldermetadataschema` for `wf-workfront-users` groep.
1. Navigeren naar **[!UICONTROL Tools]** > **[!UICONTROL Assets]** > **[!UICONTROL Folder Metadata Schemas]**.
1. Selecteer het schema voor metagegevens van de map dat u wilt bewerken en klik op Bewerken.
1. Selecteer het formulierveld voor het metagegevensschema van de map dat u wilt bewerken en selecteer het tabblad Instellingen in het rechterdeelvenster.
1. In [!UICONTROL Mapped from Workfront Field] in het veld selecteert u de naam van het Workfront-veld dat u wilt toewijzen aan de geselecteerde AEM-mapeigenschap. Beschikbare opties zijn:

   * Aangepaste formuliervelden project
   * De gebieden van het Overzicht van het project (identiteitskaart, Naam, Beschrijving, Referentienummer, Geplande Voltooiingsdatum, Eigenaar van het Project, Sponsor van het Project, Portfolio of Programma)

![metagegevenstoewijzing configureren](/help/assets/assets/wf-metadata-mapping-config2.png)

### Toewijzing van metagegevens van elementen configureren {#asset-metadata-mapping}

Metagegevenstoewijzing tussen Adobe Workfront-documenten en -elementen wordt gedefinieerd binnen AEM metagegevensschema&#39;s. Metagegevensschema&#39;s moeten op de gebruikelijke wijze in AEM worden gemaakt en geconfigureerd. Workfront Tools voegt configuratieopties toe aan het tabblad Instellingen van elk formulierveld voor het metagegevensschema. Met deze opties kunt u opgeven aan welk Workfront-veld elke AEM eigenschap moet worden toegewezen.

Voer de volgende stappen uit om de toewijzingen te configureren:

1. Navigeren naar **Gereedschappen** > **Activa** > **Metagegevensschema&#39;s**.
1. Selecteer het schema voor metagegevens dat u wilt bewerken en klik op **Bewerken** of maak een volledig nieuw metagegevensschema.
1. Selecteer het formulierveld voor het metagegevensschema dat u wilt bewerken en selecteer **Instellingen** in het rechterdeelvenster.
1. In [!DNL Workfront] Selecteer de naam van het veld Aangepast formulier [!DNL Workfront] veld dat u wilt toewijzen aan de geselecteerde AEM-eigenschap. Beschikbare opties zijn:

   * Aangepaste formuliervelden document
   * Aangepaste formuliervelden project
   * Aangepaste formuliervelden uitgeven
   * Aangepaste formuliervelden taak
   * De gebieden van het Overzicht van het project (identiteitskaart, Naam, Beschrijving, of Aantal van de Verwijzing)

1. Wanneer het [!DNL Workfront] veld geselecteerd in [!UICONTROL Workfront Custom Form Field] is een Workfront-veld voor gebruikerstypen. U moet dan opgeven welk Workfront-gebruikersveld u wilt toewijzen. Als u dit wilt doen, schakelt u de optie Waarde ophalen in het objectveld waarnaar wordt verwezen in Workfront in en geeft u vervolgens de naam op van de [!UICONTROL Workfront User Custom Form Field] waarvan de in kaart te brengen waarde moet worden opgehaald.

   ![configuratie metagegevenstoewijzing](/help/assets/assets/wf-metadata-mapping-config1.png)

## Eigenschap Map {#map-property}

Met deze workflowstap kan een gebruiker een eigenschap toewijzen aan een [!DNL Workfront] aangepast formulier op een project, taak, uitgave of document. De [!DNL Workfront] artefact deze stap beïnvloedt wordt omhoog gezocht gebruikend een relatieve weg van de lading. De eigenschappen die moeten worden toegewezen, worden beheerd vanuit de configuratie van het stappendialoogvenster.

**Type**: In dit veld kunt u het Workfront-objecttype selecteren waaraan de eigenschappen moeten worden toegewezen.

**ID-eigenschap**: In dit veld kunt u het pad opgeven naar de id van het Workfront-object waaraan de eigenschappen moeten worden toegewezen. Het pad dat in dit veld wordt opgegeven, moet relatief zijn ten opzichte van de lading van de workflow.

**Eigenschaptoewijzingen**: Met dit multifield kunt u de toewijzingen tussen AEM eigenschappen en Workfront-velden opgeven. Elk item in het meerdere veld geeft één toewijzing op. Elke toewijzing moet de indeling hebben `<workfront-field>=<aem-mapped-property>`.

* De `workfront-field` kan

   * Een aangepast formulierveld dat door het voorvoegsel wordt geïdentificeerd `DE:`.
   * Een bewerkbaar veld met de naam ervan. De veldnamen zijn te vinden in [[!DNL Workfront] API-verkenner](https://experience.workfront.com/s/api-explorer).

* De `aem-mapped-property` kan:

   * Een letterlijke waarde. Deze moeten door aanhalingstekens worden omringd.
   * Een AEM-eigenschap. Deze verwijzing moet relatief zijn ten opzichte van de lading van de workflow.
   * Een benoemde waarde. Deze moeten tussen haakjes staan.
   * Een samenvoeging van de bovenstaande drie items. Opgeven met `{+}`.
   * Een wijziging van de bovenstaande drie posten door de waarde met `{replace(<value>,"old-char","new-char")}`.

* Voorbeelden zijn:

   * `status="INP"`
   * `DE:Asset Type=jcr:content/metadata/assetType`
   * `DE:Path={path}`
   * `URL="https://my-aem-author/assets.html"{+}{path}`

![Configuratie aan kaarteigenschap](/help/assets/assets/wf-map-property-config.png)

## Status instellen {#set-status}

Bewerk de eigenschappen van **[!UICONTROL Workfront - Set Status]** in de **[!UICONTROL Arguments]** tab.

![Workflow bewerken om status in te stellen](/help/assets/assets/wf-set-status.png)

## Synchronisatie van opmerkingen {#comments-sync}

1. In [!DNL Experience Manager], toegang **[!UICONTROL Tools]** > **[!UICONTROL Cloud Services]** > **[!UICONTROL Workfront Tools Configuration]** selecteert u de configuratie en selecteert u **[!UICONTROL Properties]**.

   ![opmerkingen synchroniseren](/help/assets/assets/comments-sync1.png)

1. Selecteren **[!UICONTROL Event Subscriptions]** tabblad, klikt u op **[!UICONTROL Enable Comment Sync]** op **[!UICONTROL Send Comments made in Workfront to AEM]** -optie.

   ![Synchronisatie is ingeschakeld](/help/assets/assets/wf-comment-sync-enabled.png)

Voer de volgende stappen uit om de synchronisatie van opmerkingen van Workfront naar AEM te testen:

1. Navigeer naar een gekoppeld document in Workfront en voeg een opmerking toe op het tabblad Updates.

   ![commentaar in Workfront geven](/help/assets/assets/comments-sync2.png)

1. Navigeer naar hetzelfde gekoppelde document in AEM, selecteer het document en open het dialoogvenster [!UICONTROL Timeline] in de linkernavigatie en selecteer [!UICONTROL Comments]. Op de linkerzijbalk worden de opmerkingen weergegeven die zijn gesynchroniseerd vanuit [!DNL Workfront].

## Elementen {#asset-versions}

Om versiegeschiedenis van activa in AEM te handhaven, vorm activa versioning in AEM.

1. In Experience Manager, toegang **[!UICONTROL Tools]** > **[!UICONTROL Cloud Services]** > **[!UICONTROL Workfront Tools Configuration]** en opent u de **[!UICONTROL Advanced]** tab.

1. Selectie, optie **[!UICONTROL Store assets with the same name as versions of the existing asset]**. Als deze optie is ingeschakeld, kunnen elementen die met dezelfde naam en naar dezelfde locatie zijn geüpload als de versie van het bestaande element worden opgeslagen. Als deze optie is uitgeschakeld, wordt een nieuw element gemaakt met een andere naam (bijvoorbeeld `asset-name.pdf` en `asset-name-1.pdf`).

1. Selectie, optie **[!UICONTROL Update asset metadata when creating a version]**. Als deze optie is ingeschakeld, worden de metagegevens van de elementen bijgewerkt wanneer een nieuwe versie van het element wordt gemaakt. Als deze optie is uitgeschakeld, blijven de metagegevens van het element behouden voordat de nieuwe versie wordt gemaakt.

![middelenversie configureren](/help/assets/assets/wf-config-versioning.png)

>[!NOTE]
>
>De versioning wordt niet ondersteund in gekoppelde mappen. Wanneer u een [!DNL Workfront] Als u een document in een gekoppelde map weergeeft, worden de opmerkingen en aantekeningen in de vorige versie van het element verwijderd.

## Aangepaste formulieren bijvoegen {#attach-custom-forms}

Met deze workflowstap kunnen gebruikers een aangepast formulier aan een [!DNL Workfront] artefact. Deze workflowstap kan aan elk workflowmodel worden toegevoegd. De [!DNL Workfront] artefact deze stap beïnvloedt zal worden omhoog gezocht gebruikend een relatieve weg van de lading.

Bewerk in de werkstroomeditor in Experience Manager de eigenschappen van de [!UICONTROL Workfront - Attach custom form] workflowstap.

![aangepaste formulieren](/help/assets/assets/wf-custom-forms.png).

## Elementen automatisch publiceren {#auto-publish-assets}

1. In Experience Manager, toegang **[!UICONTROL Tools]** > **[!UICONTROL Cloud Services]** > **[!UICONTROL Workfront Tools Configuration]** en opent u de **[!UICONTROL Advanced]** tab.

1. Selecteer **[!UICONTROL Automatically publish assets when sent from Workfront]**. Met deze optie wordt het automatisch publiceren van elementen ingeschakeld wanneer deze van Workfront naar AEM worden verzonden. Deze functie kan voorwaardelijk worden ingeschakeld door een aangepast Workfront-formulierveld op te geven en de waarde op te geven waarop dit moet worden ingesteld. Wanneer een document naar AEM wordt verzonden, als het aan de voorwaarde voldoet, dan zal het element automatisch worden gepubliceerd.

1. Selecteer **[!UICONTROL Publish all project assets to Brand Portal upon project completion]**. Met deze optie wordt het automatisch publiceren van elementen ingeschakeld voor [!DNL Brand Portal] wanneer de status van het Workfront-project waartoe zij behoren, wordt gewijzigd in `Complete`.

![automatisch publiceren configureren](/help/assets/assets/wf-auto-publish-config.png)

## Aangepaste formulierupdates voor Workfront-documenten {#subscribe-workfront-doc-custom-form-updates}

Als u zich wilt abonneren op de wijzigingen in [!DNL Workfront] aangepaste formulieren documenteren, selecteert u de desbetreffende optie in het dialoogvenster **[!UICONTROL Advanced]** tab. Wanneer u zich abonneert op deze updates, wordt uw toegewezen [!DNL Experience Manager] metagegevensvelden wanneer het corresponderende veld in [!DNL Workfront] aangepast document wordt gewijzigd.

![Configuratie van aangepaste Workfront-formulierupdates voor documenten in [!DNL Experience Manager]](/help/assets/assets/wf-custom-form-update.png)
