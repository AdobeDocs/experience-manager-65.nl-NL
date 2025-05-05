---
title: Configureren  [!DNL Workfront for Experience Manager enhanced connector]
description: Configureren  [!DNL Workfront for Experience Manager enhanced connector]
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
| AEM as a Cloud Service | [ klik hier ](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/assets/integrations/workfront-connector-configure.html?lang=nl-NL) |
| AEM 6,5 | Dit artikel |

Een gebruiker met beheerdertoegang in [!DNL Adobe Experience Manager] vormt de verbeterde schakelaar na het installeren van het. Voor instructies om te installeren, zie [ de schakelaar ](/help/assets/workfront-integrations.md) installeren.

>[!IMPORTANT]
>
>* Voor Adobe is implementatie en configuratie van de [!DNL Adobe Workfront for Experience Manager enhanced connector] alleen via gecertificeerde partners of [!DNL Adobe Professional Services] vereist. Indien opgesteld en gevormd zonder een verklaarde partner of [!DNL Adobe Professional Services], wordt het niet gesteund door Adobe.
>
>* Adobe kan updates aan [!DNL Adobe Workfront] en [!DNL Adobe Experience Manager] vrijgeven die deze schakelaar overtollig maken; als dit voorkomt, kunnen klanten worden vereist om van het gebruik van deze schakelaar over te gaan.
>
>* Adobe ondersteunt verbeterde connectorversies 1.7.4 en hoger. Eerdere pre-release en aangepaste versies worden niet ondersteund. Om de verbeterde schakelaarversie te controleren, navigeer aan de `digital.hoodoo` groep beschikbaar in de linkerruit in [ Manager van het Pakket ](https://experienceleague.adobe.com/docs/experience-manager-65/administering/contentmanagement/package-manager.html?lang=nl-NL).
>
>* Zie [ de certificatieexamen van de Partner voor Workfront voor Experience Manager Assets verbeterde schakelaar ](https://solutionpartners.adobe.com/solution-partners/home/applications/experience_cloud/workfront/journey/dev_core.html). Voor informatie over het examen, zie {de Gids van het 0} Examen [&#128279;](https://express.adobe.com/page/Tc7Mq6zLbPFy8/).

## Gebeurtenisabonnementen configureren {#event-subscriptions}

Gebeurtenisabonnementen worden gebruikt om AEM op de hoogte te brengen van gebeurtenissen die plaatsvinden in [!DNL Adobe Workfront] . Er zijn drie [!DNL Workfront for Experience Manager enhanced connector] -functies die gebeurtenisabonnementen nodig hebben om te werken:

* Automatisch maken van aan een project gekoppelde mappen.
* Synchronisatie van wijzigingen in Workfront-document aangepaste formulierwaarden naar metagegevens van AEM element.
* Automatische bekendmaking van activa aan Brand Portal na voltooiing van het project.

Schakel gebeurtenisabonnementen in als u deze functies wilt gebruiken.

* Bewerk de configuratie met [!UICONTROL Workfront Tools] Cloud Servicen die u in stap 5 hebt gemaakt en selecteer de tab [!UICONTROL Event Subscriptions] .
* Selecteer de [!UICONTROL Workfront Custom Integration] die u in sectie 6 hebt gemaakt.
* Klik op [!UICONTROL Enable Workfront Event Subscriptions].

  ![ abonnement van de Gebeurtenis ](/help/assets/assets/event-subs.png)

## Gekoppelde mappen configureren {#linked-folders}

Voer de volgende stappen uit om u te abonneren op de gebeurtenissen:

1. Navigeer naar het tabblad **[!UICONTROL Event Subscriptions]** in de cloudservices.
1. Selecteer de aangepaste integratie die in [!DNL Workfront] is gemaakt.
1. Klik op **[!UICONTROL Enable Workfront Event Subscriptions]**.

### Configuratie van gekoppelde mapstructuur {#linked-folder-structure}

1. Ga naar het tabblad Gekoppelde projectmappen in de cloudservices.
1. Bovenliggend pad van gekoppelde map: selecteer een map in de DAM waar u de gekoppelde mappen wilt maken. Als het verlaten leeg blijft, zal het aan /content/dam in gebreke blijven. Controleer of het metagegevensschema voor Workfront Tools en het metagegevensschema voor de map Workfront Linked Folder zijn toegepast op de geselecteerde map.
1. Gekoppelde mapstructuur: voer door komma&#39;s gescheiden waarden in. Elke waarde moet `DE:<some-project-custom-form-field>`, Portfolio, Program, Year, Name of een letterlijke tekenreekswaarde zijn (deze laatste met aanhalingstekens). Deze is momenteel ingesteld op Portfolio,Programma,Jaar,DE:Projecttype,Naam.
1. Machtigingen configureren: voeg `jcr:all permissions` machtigingen toe aan de groep `/conf/workfront-tools/settings/cloudconfigs` for `wf-workfront-users` .
1. De functie voor het maken van gekoppelde mappen in Workfront met het selectievakje voor mapstructuurnamen moet zijn ingeschakeld als de titel van de map in Workfront alle mappen in de structuur moet bevatten. Anders is dit de titel van de laatste map.
1. Met submappen met meerdere velden kunt u een lijst opgeven met mappen die moeten worden gemaakt als een onderliggende map van de gekoppelde map.
1. Projectstatus: selecteer de status van het project om de gekoppelde map te maken.
1. Maak een gekoppelde map in projecten met een portfolio: lijst met Portfolio&#39;s waartoe het project moet behoren om de gekoppelde map te maken. Laat deze lijst leeg om de gekoppelde map voor alle projectportfolio te maken.
1. Maak een gekoppelde map in projecten met een aangepast formulierveld: aangepast formulierveld en de bijbehorende waarde die het project nodig heeft om de gekoppelde map te maken. Deze configuratie wordt genegeerd als deze leeg wordt gelaten. Selecteer `CUSTOM FORMS: Create DAM Linked Folder` voor het veld en voer `Yes` voor de waarde in.
1. Klik op Automatisch maken van gekoppelde mappen inschakelen. Als u teruggaat naar het tabblad Gebeurtenisabonnementen, ziet u dat er nu een gebeurtenis create is.

![ verbonden omslagconfiguratie ](/help/assets/assets/wf-linked-folder-config.png)

## Metagegevensschematoewijzing {#metadata-schema-mapping}

### Mapmetagegevenstoewijzing configureren {#folder-metadata-mapping}

Metagegevenstoewijzing tussen Workfront-projecten en AEM mappen wordt gedefinieerd in AEM schema&#39;s met metagegevens van mappen. Metagegevensschema&#39;s voor mappen moeten op de gebruikelijke wijze in AEM worden gemaakt en geconfigureerd. Workfront Tools voegt een automatisch aanvullen vervolgkeuzelijst toe aan het tabblad Settings-configuratie van elk formulierveld voor het schema van metagegevens van de map. In dit keuzemenu voor automatisch aanvullen kunt u opgeven aan welk Workfront-veld elke AEM mapeigenschap moet worden toegewezen.

Voer de volgende stappen uit om de toewijzingen te configureren:

1. Voeg `jcr:read` machtigingen toe aan de groep `/conf/global/settings/dam/adminui-extension/foldermetadataschema` for `wf-workfront-users` .
1. Navigeer naar **[!UICONTROL Tools]** > **[!UICONTROL Assets]** > **[!UICONTROL Folder Metadata Schemas]** .
1. Selecteer het schema voor metagegevens van de map dat u wilt bewerken en klik op Bewerken.
1. Selecteer het formulierveld voor het metagegevensschema van de map dat u wilt bewerken en selecteer het tabblad Instellingen in het rechterdeelvenster.
1. Selecteer in het veld [!UICONTROL Mapped from Workfront Field] de naam van het Workfront-veld dat u wilt toewijzen aan de geselecteerde AEM-mapeigenschap. Beschikbare opties zijn:

   * Aangepaste formuliervelden project
   * De gebieden van het Overzicht van het project (identiteitskaart, Naam, Beschrijving, Referentienummer, Geplande Voltooiingsdatum, Eigenaar van het Project, Sponsor van het Project, Portfolio of Programma)

![ meta-gegevens in kaart brengend config ](/help/assets/assets/wf-metadata-mapping-config2.png)

### Toewijzing van metagegevens van elementen configureren {#asset-metadata-mapping}

Metagegevenstoewijzing tussen Adobe Workfront-documenten en Assets wordt gedefinieerd binnen AEM metagegevensschema&#39;s. Metagegevensschema&#39;s moeten op de gebruikelijke wijze in AEM worden gemaakt en geconfigureerd. Workfront Tools voegt configuratieopties toe aan het tabblad Instellingen van elk formulierveld voor het metagegevensschema. Met deze opties kunt u opgeven aan welk Workfront-veld elke AEM eigenschap moet worden toegewezen.

Voer de volgende stappen uit om de toewijzingen te configureren:

1. Navigeer aan **Hulpmiddelen** > **Assets** > **Schema&#39;s van Meta-gegevens**.
1. Selecteer de vorm van het meta-gegevensschema u wenst uit te geven en **te klikken geeft** uit of creeer een meta-gegevensschema van kras.
1. Selecteer het de vormgebied van het meta-gegevensschema u wenst uit te geven en **het lusje van Montages** op het juiste paneel te selecteren.
1. Selecteer in [!DNL Workfront] Aangepast formulierveld de naam van het [!DNL Workfront] -veld dat u wilt toewijzen aan de geselecteerde AEM-eigenschap. Beschikbare opties zijn:

   * Aangepaste formuliervelden document
   * Aangepaste formuliervelden project
   * Aangepaste formuliervelden uitgeven
   * Aangepaste formuliervelden taak
   * De gebieden van het Overzicht van het project (identiteitskaart, Naam, Beschrijving, of Aantal van de Verwijzing)

1. Als het veld [!DNL Workfront] dat is geselecteerd in [!UICONTROL Workfront Custom Form Field] een Workfront User type-ahead veld is, moet u opgeven welk Workfront User-veld u wilt toewijzen. Controleer hiertoe de waarde Ophalen in het objectveld waarnaar wordt verwezen in Workfront en geef vervolgens de naam op van de [!UICONTROL Workfront User Custom Form Field] vanwaar u de waarde wilt ophalen die moet worden toegewezen.

   ![ configuratie van de meta-gegevenstoewijzing ](/help/assets/assets/wf-metadata-mapping-config1.png)

## Eigenschap Map {#map-property}

Met deze workflowstap kan een gebruiker een eigenschap toewijzen aan een [!DNL Workfront] aangepast formulier op een project, taak, uitgave of document. Het [!DNL Workfront] -artefact waarop deze stap betrekking heeft, wordt opgezocht aan de hand van een relatief pad van de laadbewerking. De eigenschappen die moeten worden toegewezen, worden beheerd vanuit de configuratie van het stappendialoogvenster.

**Type**: Dit gebied laat u het objecten van Workfront type selecteren dat de eigenschappen zouden moeten worden in kaart gebracht aan.

**Bezit van identiteitskaart**: Dit gebied laat u de weg aan identiteitskaart van het voorwerp van Workfront specificeren dat de eigenschappen zouden moeten worden in kaart gebracht aan. Het pad dat in dit veld wordt opgegeven, moet relatief zijn ten opzichte van de lading van de workflow.

**Toewijzingen van het Bezit**: Dit multifield laat u de afbeeldingen tussen AEM eigenschappen en de gebieden van Workfront specificeren. Elk item in het meerdere veld geeft één toewijzing op. Elke toewijzing moet de indeling `<workfront-field>=<aem-mapped-property>` hebben.

* De `workfront-field` kan

   * Een aangepast formulierveld dat door het voorvoegsel `DE:` wordt geïdentificeerd.
   * Een bewerkbaar veld met de naam ervan. De gebiedsnamen worden gevonden in [[!DNL Workfront]  API ontdekkingsreiziger ](https://experience.workfront.com/s/api-explorer).

* De `aem-mapped-property` kan zijn:

   * Een letterlijke waarde. Deze moeten door aanhalingstekens worden omringd.
   * Een AEM-eigenschap. Deze verwijzing moet relatief zijn ten opzichte van de lading van de workflow.
   * Een benoemde waarde. Deze moeten tussen haakjes staan.
   * Een samenvoeging van de bovenstaande drie items. Geef dit op met `{+}` .
   * Een wijziging van de bovenstaande 3 items door de waarde met `{replace(<value>,"old-char","new-char")}` te omringen.

* Voorbeelden zijn:

   * `status="INP"`
   * `DE:Asset Type=jcr:content/metadata/assetType`
   * `DE:Path={path}`
   * `URL="https://my-aem-author/assets.html"{+}{path}`

![ Configuratie aan kaartbezit ](/help/assets/assets/wf-map-property-config.png)

## Status instellen {#set-status}

Bewerk in de werkstroomeditor de eigenschappen van **[!UICONTROL Workfront - Set Status]** op het tabblad **[!UICONTROL Arguments]** .

![ geeft werkschema uit om status ](/help/assets/assets/wf-set-status.png) te plaatsen

## Synchronisatie van opmerkingen {#comments-sync}

1. Open **[!UICONTROL Tools]** > **[!UICONTROL Cloud Services]** > **[!UICONTROL Workfront Tools Configuration]** in [!DNL Experience Manager] , selecteer de configuratie en selecteer **[!UICONTROL Properties]** .

   ![ commentaarsynchronisatie ](/help/assets/assets/comments-sync1.png)

1. Selecteer de tab **[!UICONTROL Event Subscriptions]** en klik op de optie **[!UICONTROL Enable Comment Sync]** on **[!UICONTROL Send Comments made in Workfront to AEM]** .

   ![ de Synchronisatie wordt toegelaten ](/help/assets/assets/wf-comment-sync-enabled.png)

Voer de volgende stappen uit om de synchronisatie van opmerkingen van Workfront naar AEM te testen:

1. Navigeer naar een gekoppeld document in Workfront en voeg een opmerking toe op het tabblad Updates.

   ![ verlaten commentaar in Workfront ](/help/assets/assets/comments-sync2.png)

1. Navigeer in AEM naar hetzelfde gekoppelde document, selecteer het document en open de optie [!UICONTROL Timeline] in de linkernavigatie en selecteer [!UICONTROL Comments] . Op de linkerzijbalk worden de opmerkingen weergegeven die vanuit [!DNL Workfront] zijn gesynchroniseerd.

## Elementen {#asset-versions}

Om versiegeschiedenis van activa in AEM te handhaven, vorm activa versioning in AEM.

1. Open in Experience Manager **[!UICONTROL Tools]** > **[!UICONTROL Cloud Services]** > **[!UICONTROL Workfront Tools Configuration]** en open de tab **[!UICONTROL Advanced]** .

1. Selecteer optie **[!UICONTROL Store assets with the same name as versions of the existing asset]**. Als deze optie is ingeschakeld, kunnen elementen die met dezelfde naam en naar dezelfde locatie zijn geüpload als de versie van het bestaande element worden opgeslagen. Als deze optie uitgeschakeld is, wordt een nieuw element gemaakt met een andere naam (bijvoorbeeld `asset-name.pdf` en `asset-name-1.pdf` ).

1. Selecteer optie **[!UICONTROL Update asset metadata when creating a version]**. Als deze optie is ingeschakeld, worden de metagegevens van de elementen bijgewerkt wanneer een nieuwe versie van het element wordt gemaakt. Als deze optie is uitgeschakeld, blijven de metagegevens van het element behouden voordat de nieuwe versie wordt gemaakt.

![ vorm activa versioning ](/help/assets/assets/wf-config-versioning.png)

>[!NOTE]
>
>De versioning wordt niet ondersteund in gekoppelde mappen. Wanneer u een [!DNL Workfront] -proefdruk maakt met een document in een gekoppelde map, worden de opmerkingen en annotaties op de vorige versie van het element verwijderd.

## Aangepaste formulieren bijvoegen {#attach-custom-forms}

Met deze workflowstap kunnen gebruikers een aangepast formulier aan een [!DNL Workfront] artefact koppelen. Deze workflowstap kan aan elk workflowmodel worden toegevoegd. Het [!DNL Workfront] -artefact waarop deze stap betrekking heeft, wordt opgezocht aan de hand van een relatief pad vanaf de payload.

Bewerk de eigenschappen van de workflowstap [!UICONTROL Workfront - Attach custom form] in de workflow-editor in Experience Manager.

![ douaneformulieren ](/help/assets/assets/wf-custom-forms.png).

## Elementen automatisch publiceren {#auto-publish-assets}

1. Open in Experience Manager **[!UICONTROL Tools]** > **[!UICONTROL Cloud Services]** > **[!UICONTROL Workfront Tools Configuration]** en open de tab **[!UICONTROL Advanced]** .

1. Selecteer **[!UICONTROL Automatically publish assets when sent from Workfront]**. Met deze optie wordt het automatisch publiceren van elementen ingeschakeld wanneer deze van Workfront naar AEM worden verzonden. Deze functie kan voorwaardelijk worden ingeschakeld door een aangepast Workfront-formulierveld op te geven en de waarde op te geven waarop dit moet worden ingesteld. Wanneer een document naar AEM wordt verzonden, als het aan de voorwaarde voldoet, dan zal het element automatisch worden gepubliceerd.

1. Selecteer **[!UICONTROL Publish all project assets to Brand Portal upon project completion]**. Met deze optie schakelt u het automatisch publiceren van elementen in op [!DNL Brand Portal] wanneer de status van het Workfront-project waartoe deze behoren, wordt gewijzigd in `Complete` .

![ vorm auto-publiceer ](/help/assets/assets/wf-auto-publish-config.png)

## Aangepaste formulierupdates voor Workfront-documenten {#subscribe-workfront-doc-custom-form-updates}

Als u zich wilt abonneren op de wijzigingen in aangepaste [!DNL Workfront] -documentformulieren, selecteert u de desbetreffende optie op het tabblad **[!UICONTROL Advanced]** . Wanneer u zich abonneert op deze updates, worden de toegewezen [!DNL Experience Manager] metagegevensvelden bijgewerkt wanneer het corresponderende veld in het aangepaste formulier voor het [!DNL Workfront] -document wordt gewijzigd.

![ Configuratie van aangepaste formulieren voor Workfront-documenten in [!DNL Experience Manager]](/help/assets/assets/wf-custom-form-update.png)
