---
title: Installeren  [!DNL Workfront for Experience Manager enhanced connector]
description: Installeren  [!DNL Workfront for Experience Manager enhanced connector]
role: Admin
feature: Workfront Integrations and Apps
exl-id: 087bc811-e8f8-4db5-b066-627a9b082f57
hide: true
solution: Experience Manager, Workfront
source-git-commit: 633b1378d97ea0544f27822fb5801caa3ed15f8e
workflow-type: tm+mt
source-wordcount: '426'
ht-degree: 1%

---

# Installeren [!DNL Workfront for Experience Manager enhanced connector] {#assets-integration-overview}

| Versie | Artikelkoppeling |
| -------- | ---------------------------- |
| AEM as a Cloud Service | [&#x200B; klik hier &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/assets/integrations/workfront-connector-install.html?lang=en) |
| AEM 6.5 | Dit artikel |

Een gebruiker met beheerdertoegang in [!DNL Adobe Experience Manager] installeert de verbeterde schakelaar. Alvorens u installeert, herzie de platformsteun en andere [&#x200B; eerste vereisten voor de schakelaar &#x200B;](https://one.workfront.com/s/csh?context=2467&pubname=the-new-workfront-experience).

>[!IMPORTANT]
>
>* Adobe vereist implementatie en configuratie van de [!DNL Adobe Workfront for Experience Manager enhanced connector] alleen via gecertificeerde partners of [!DNL Adobe Professional Services] . Indien geïmplementeerd en geconfigureerd zonder een gecertificeerde partner of [!DNL Adobe Professional Services] , wordt dit niet ondersteund door Adobe.
>
>* Adobe kan updates voor [!DNL Adobe Workfront] en [!DNL Adobe Experience Manager] vrijgeven die deze connector redundant maken. Als dit gebeurt, kunnen klanten worden gevraagd over te stappen van het gebruik van deze connector.
>
>* Adobe ondersteunt verbeterde connectorversies 1.7.4 en hoger. Eerdere pre-release en aangepaste versies worden niet ondersteund. Om de verbeterde schakelaarversie te controleren, navigeer aan de `digital.hoodoo` groep beschikbaar in de linkerruit in [&#x200B; Manager van het Pakket &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-65/administering/contentmanagement/package-manager.html?lang=en).
>
>* Zie [&#x200B; de certificatieexamen van de Partner voor Workfront voor Experience Manager Assets verbeterde schakelaar &#x200B;](https://solutionpartners.adobe.com/solution-partners/home/applications/experience_cloud/workfront/journey/dev_core.html). Voor informatie over het examen, zie {de Gids van het 0} Examen [.](https://express.adobe.com/page/Tc7Mq6zLbPFy8/)

Voer de volgende stappen uit om de aansluiting te installeren:

1. Download de schakelaar van [[!DNL Software Distribution]  verbinding &#x200B;](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/product/assets/workfront-tools.ui.apps.zip).
1. [&#x200B; vorm de firewall &#x200B;](https://one.workfront.com/s/document-item?bundleId=the-new-workfront-experience&topicId=Content%2FAdministration_and_Setup%2FGet_started-WF_administration%2Fconfigure-your-firewall.html).
1. Sta in de Dispatcher de HTTP-headers `authorization` , `username` en `apikey` toe. `GET` -, `POST` - en `PUT` -aanvragen toestaan aan `/bin/workfront-tools` .
1. Zorg ervoor dat de volgende paden niet bestaan in de [!DNL Experience Manager] -opslagplaats:

   * `/apps/dam/gui/coral/components/admin/schemaforms/formbuilder`
   * `/apps/dam/gui/coral/components/admin/folderschemaforms/formbuilder`
   * `/apps/dam/gui/content/foldermetadataschemaeditor`
   * `/apps/dam/cfm/models/editor/components/datatypeproperties`
   * `/apps/settings/dam/cfm/models/formbuilderconfig`

1. Installeer het pakket met [!UICONTROL Package Manager] . Om te weten hoe te om pakketten te installeren, zie {de documentatie van de Manager van het 0} Pakket [.](/help/sites-administering/package-manager.md)
1. Maak `wf-workfront-users` in [!DNL Experience Manager] Gebruikersgroep en wijs de machtiging `jcr:all` toe aan `/content/dam` .
1. Voeg een aangepaste eigenschap toe aan de waarde voor de index van het vak voor **`ntFolderDamLucene(/oak:index/ntFolderDamLucene)`** . Voer de volgende stappen uit:
   * Voeg een eigenschap **`nt:unstructured`** genaamd **`wfReferenceNumber`** toe aan:
     `/oak:index/ntFolderDamLucene/indexRules/nt:folder/properties/wfReferenceNumber`.
   * Wijzig de index van de `index /oak:index/ntFolderDamLucene` door de herindexmarkering om te draaien naar `true` .

Er wordt automatisch een systeemgebruiker `workfront-tools` gemaakt en de vereiste machtigingen worden automatisch beheerd. Alle gebruikers van [!DNL Workfront] die de schakelaar gebruiken worden automatisch toegevoegd als deel van deze groep.

>[!NOTE]
>
> Wanneer u bedrijfsproxyservers gebruikt, neemt u [!DNL workfront] op in de [!UICONTROL Apache HTTP Components Proxy Configuration PID] for the [!UICONTROL Enhanced Workfront Connector] om deze te herkennen. De vereiste PID-indeling is: `org.apache.http.proxyconfigurator~workfront` .

## De verbinding configureren tussen [!DNL Experience Manager] en [!DNL Workfront] {#configure-connection}

Ga als volgt te werk om een verbinding met Workfront te maken:

1. Selecteer [!DNL Experience Manager] > **[!UICONTROL Tools]** > **[!UICONTROL Cloud Services]** in **[!UICONTROL Workfront Tools Configuration]** .

1. Selecteer `workfront-tools` in het linkerpaneel en selecteer **[!UICONTROL Create]** optie in het hoger-juiste gebied van de pagina.

1. Geef in het dialoogvenster **[!UICONTROL Workfront Connection]** de vereiste details van de [!DNL Workfront] -implementatie op en selecteer de optie **[!UICONTROL Connect to Workfront]** . Zodra de verbinding is gelukt, wordt de aangepaste integratie van het [!DNL Workfront] -document automatisch gemaakt in de [!DNL Workfront] -omgeving.

   ![&#x200B; Verbinden [!DNL Experience Manager] en [!DNL Workfront]](/help/assets/assets/wf-connection-config.png)

1. Als u de verbinding wilt controleren, opent u deze in [!DNL Workfront] en controleert u of de API-sleutel gelijk is en of de verbinding **[!UICONTROL Enabled]** is. Selecteer hiervoor **[!UICONTROL Setup]** > **[!UICONTROL Documents]** > **[!UICONTROL Custom Integrations]** in [!DNL Workfront] .

## [!DNL Workfront for Experience Manager enhanced connector] bijwerken {#update-enhanced-connector-for-workfront}

Met Experience Manager Assets kunt u [!DNL Workfront for Experience Manager enhanced connector] bijwerken van een vorige versie naar de meest recente versie.

Ga als volgt te werk om [!DNL Workfront for Experience Manager enhanced connector] bij te werken naar de meest recente versie:

1. Download de recentste versie van de verbeterde schakelaar van [[!DNL Software Distribution]  verbinding &#x200B;](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/product/assets/workfront-tools.ui.apps.zip).
1. Installeer het pakket met [!UICONTROL Package Manager] . Om te weten hoe te om pakketten te installeren, zie {de documentatie van de Manager van het 0} Pakket [.](/help/sites-administering/package-manager.md)
