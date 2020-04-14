---
title: Offloader middelenwerkstroom
seo-title: Offloader middelenwerkstroom
description: Meer informatie over de Offloader voor de workflow Middelen.
seo-description: Meer informatie over de Offloader voor de workflow Middelen.
uuid: d1c93ef9-a0e1-43c7-b591-f59d1ee4f88b
contentOwner: Chiradeep Majumdar
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: content
content-type: reference
discoiquuid: 91f0fd7d-4b49-4599-8f0e-fc367d51aeba
translation-type: tm+mt
source-git-commit: f24142064b15606a5706fe78bf56866f7f9a40ae

---


# Offloader middelenwerkstroom{#assets-workflow-offloader}

Met de Offloader van de middelenworkflow kunt u meerdere instanties van Adobe Experience Manager (AEM)-middelen inschakelen om de verwerkingsbelasting van de primaire instantie (leader) te verminderen. De verwerkingsbelasting wordt verdeeld over de instantie leader en de verschillende instanties offloader (worker) die u eraan toevoegt. Door de verwerkingsbelasting van elementen te verdelen, verhoogt u de efficiëntie en snelheid waarmee AEM-elementen elementen elementen verwerken. Daarnaast kunt u speciale bronnen toewijzen om elementen van een bepaald MIME-type te verwerken. U kunt bijvoorbeeld een specifiek knooppunt in uw topologie toewijzen om alleen InDesign-elementen te verwerken.

## Offloader-topologie configureren {#configure-offloader-topology}

Gebruik Configuration Manager om de URL voor de instantie leader en de hostnamen van instanties van offloader toe te voegen voor verbindingsaanvragen voor de instantie leader.

1. Tik/klik op het AEM-logo en kies **Gereedschappen** > **Bewerkingen** > **Webconsole** om Configuratiebeheer te openen.
1. Selecteer in de webconsole **Sling** > **Topologiebeheer**.

   ![chlimage_1-44](assets/chlimage_1-44a.png)

1. Tik/klik op de koppeling Discovery. **Oak Service** configureren op de pagina Topology Management.

   ![chlimage_1-45](assets/chlimage_1-45a.png)

1. Op de pagina van de Configuratie van de Dienst van de Ontdekking, specificeer schakelaar URL voor de leaderinstantie op het gebied van **Topology Connector URLs** .

   ![chlimage_1-46](assets/chlimage_1-46a.png)

1. In het veld Whitelist van **topologieconnector** geeft u IP-adres of hostnamen van offloader-instanties op die verbinding mogen maken met de leaderinstantie. Tik/klik op **Opslaan**.

   ![chlimage_1-47](assets/chlimage_1-47a.png)

1. Ga naar **Gereedschappen** > **Implementatie** > **Topologie** en tik/klik op de clusterweergave om de offloader-instanties weer te geven die zijn verbonden met de instantie van de leader.

## Offloading uitschakelen {#disable-offloading}

1. Tik/klik op het AEM-logo en kies **Gereedschappen** > **Implementatie** > **Offloaden**. Op de pagina **Offloading Browser** worden onderwerpen en de serverinstanties weergegeven die de onderwerpen kunnen gebruiken.

   ![chlimage_1-48](assets/chlimage_1-48a.png)

1. Schakel het *onderwerp com/adobe/granite/workflow/offloading* uit op de leaderinstanties waarmee gebruikers communiceren om AEM-elementen te uploaden of te wijzigen.

   ![chlimage_1-49](assets/chlimage_1-49a.png)

## Workflowdraagraketten configureren op de leaderinstantie {#configure-workflow-launchers-on-the-leader-instance}

Configureer workflowstartprogramma&#39;s om de workflow voor het ontladen [!UICONTROL van bedrijfsmiddelen bij] DAM Update op de leaderinstantie te gebruiken in plaats van de workflow voor **Dam Update Asset** .

1. Tik/klik op het AEM-logo en kies **Gereedschappen** > **Workflow** > **Launchers** om de **Workflow Launchers** -console te openen.

   ![chlimage_1-50](assets/chlimage_1-50a.png)

1. Zoek de twee configuraties van Launcher met respectievelijk **Node Created** en **Node Modified** van het gebeurtenistype **, die de workflow van de Elementen** van de Update vanDAM in werking stellen.
1. Schakel voor elke configuratie het selectievakje in en tik op het pictogram **Weergave-eigenschappen** op de werkbalk om het dialoogvenster **Opstarteigenschappen** weer te geven.

   ![chlimage_1-51](assets/chlimage_1-51a.png)

1. Kies in de lijst **Workflow** de optie [!UICONTROL DAM Asset Offloading] bijwerken en tik/klik op **Opslaan**.

   ![chlimage_1-52](assets/chlimage_1-52a.png)

1. Tik/klik op het AEM-logo en kies **Gereedschappen** > **Workflow** > **Modellen** om de pagina **Workflowmodellen** te openen.
1. Selecteer de workflow voor het ontladen [!UICONTROL van] DAM-elementen bijwerken en tik op de werkbalk op **Bewerken** of klik op Bewerken om de details weer te geven.

   ![chlimage_1-53](assets/chlimage_1-53a.png)

1. Geef het contextmenu weer voor de stap **DAM Workflow Offloading** en kies **Edit**. Verifieer de ingang op het gebied van het Onderwerp van de **Baan** van de Baan van het **Algemene lusje van Argumenten** van de configuratiedialoog.

   ![chlimage_1-54](assets/chlimage_1-54a.png)

## Workflowstartprogramma&#39;s uitschakelen op offloader-instanties {#disable-the-workflow-launchers-on-the-offloader-instances}

Schakel de workflowstartprogramma&#39;s uit die de workflow **DAM Update Asset** uitvoeren op de leaderinstantie.

1. Tik/klik op het AEM-logo en kies **Gereedschappen** > **Workflow** > **Launchers** om de **Workflow Launchers** -console te openen.

   ![chlimage_1-55](assets/chlimage_1-55a.png)

1. Zoek de twee configuraties van Launcher met respectievelijk **Node Created** en **Node Modified** van het gebeurtenistype **, die de workflow van de Elementen** van de Update vanDAM in werking stellen.
1. Schakel voor elke configuratie het selectievakje in en tik op het pictogram **Weergave-eigenschappen** op de werkbalk om het dialoogvenster **Opstarteigenschappen** weer te geven.

   ![chlimage_1-56](assets/chlimage_1-56a.png)

1. In de sectie **Activeren** sleept u de schuifregelaar om de werkstroomopstarter uit te schakelen en tikt of klikt u op **Opslaan** om deze uit te schakelen.

   ![chlimage_1-57](assets/chlimage_1-57a.png)

1. Upload elk element van het type afbeelding bij de instantie leader. Verifieer de duimnagels die voor de activa door de geverschuiven instantie worden geproduceerd en worden teruggevoerd.

