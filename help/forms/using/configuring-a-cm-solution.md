---
title: Een Correspondentiebeheeroplossing configureren
description: Leer hoe u een Correspondence Management-oplossing configureert in een AEM Forms-omgeving.
topic-tags: correspondence-management
content-type: reference
products: SG_EXPERIENCEMANAGER/6.3/FORMS
feature: Correspondence Management
exl-id: f7f5eb0d-a283-45ea-84d3-d6375d2bb95b
solution: Experience Manager, Experience Manager Forms
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '283'
ht-degree: 0%

---

# Een Correspondentiebeheeroplossing configureren {#configuring-a-correspondence-management-solution}

## URL van auteurinstantie voor VersionRestoreManagerImpl bepalen {#defining-author-instance-url-for-versionrestoremanagerimpl}

Gebruik de volgende stappen om een instantie-URL van de auteur te definiëren voor het terugzetten van de auteurversie:

1. Ga naar *https://:&lt;publishhost>:&lt;publishport>/lc/system/console/configMgr*. Meld u aan met de gebruikersgegevens van de OSGi Management Console. De standaardreferenties zijn admin/admin.
1. Zoeken en klikken op de knop **[!UICONTROL Edit]** pictogram naast **[!UICONTROL com.adobe.livecycle.content.activate.impl.VersionRestoreManagerImpl.name]** instellen.
1. In de **[!UICONTROL VersionRestoreManager Author URL]** Geef de URL van de instantie Auteur van VersionRestoreManager op.

   **URL-tekenreeks**:

   `https://<hostname>:<port>:/libs/fd/fdm/content/crud/lc.content.remote.activate.VersionRestoreManager`

   >[!NOTE]
   >
   >Als er meerdere auteur-instanties (geclusterd) zijn met een taakverdeler, geeft u de URL op naar het taakverdelingsmechanisme in het dialoogvenster **[!UICONTROL VersionRestoreManager Author URL]** veld.

1. Klik op **[!UICONTROL Save]**.

## De URL van de instantie Publish definiëren voor ActivationManagerImpl (public instance activation manager) {#defining-the-publish-instance-url-for-activationmanagerimpl-public-instance-activation-manager}

Voer de volgende stappen uit, zodat u de URL van de instantie Publiceren kunt definiëren voor het beheer voor activering van openbare instanties:

1. Ga naar *https://:&lt;authorhost>:&lt;authorport>/lc/system/console/configMgr*. Meld u aan met de gebruikersgegevens van de OSGi Management Console. De standaardreferenties zijn admin/admin.
1. Zoeken en klikken op de knop **[!UICONTROL Edit]** pictogram naast **[!UICONTROL com.adobe.livecycle.content.activate.impl.ActivationManagerImpl.name]** instellen.
1. In de **[!UICONTROL ActivationManager Publish URL]** Geef de URL op voor toegang tot de instantie Publish ActivationManager. U kunt de volgende URL&#39;s opgeven.

   * **Load Balancer URL (aanbevolen)**: Geef URL van taakverdelingsmechanisme op als u een webserver hebt die als taakverdelingsmechanisme fungeert vóór publicatiefarm (meerdere niet-geclusterde publicatieinstanties).
   * **Instance-URL publiceren**: Geef een URL voor een publicatieexemplaar op als u één publicatieexemplaar hebt of als de webserver die de publicatiecapaciteit doorstuurt, niet toegankelijk is vanuit de auteursomgeving vanwege beperkingen. Als de opgegeven publicatie-instantie is ingedrukt, is er een fallback-mechanisme waarmee aan de auteurzijde moet worden omgegaan.
   * **URL-tekenreeks**:

     `https://<hostname>:<port>:/libs/fd/fdm/content/crud/lc.content.remote.activate.activationManager`

1. Klik op **[!UICONTROL Save]**.

Voor meer informatie over het vormen van het Beheer van de Correspondentie, zie [Eigenschappen van Correspondentenbeheer](https://helpx.adobe.com/aem-forms/6-2/cm-configuration-properties.html).
