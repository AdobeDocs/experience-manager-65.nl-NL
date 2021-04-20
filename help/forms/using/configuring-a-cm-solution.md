---
title: Een Correspondentiebeheeroplossing configureren
seo-title: Een Correspondentiebeheeroplossing configureren
description: Een Correspondentiebeheeroplossing configureren
uuid: 76b25004-fe47-44d7-9bed-7c0fd963306b
topic-tags: correspondence-management
content-type: reference
products: SG_EXPERIENCEMANAGER/6.3/FORMS
discoiquuid: 186ca75c-638b-4057-826e-cd5d56aa0397
feature: Correspondence Management
translation-type: tm+mt
source-git-commit: 48726639e93696f32fa368fad2630e6fca50640e
workflow-type: tm+mt
source-wordcount: '283'
ht-degree: 0%

---


# Een Correspondentiebeheeroplossing {#configuring-a-correspondence-management-solution} configureren

## URL van auteurinstantie voor VersionRestoreManagerImpl {#defining-author-instance-url-for-versionrestoremanagerimpl} bepalen

Gebruik de volgende stappen om een instantie-URL van de auteur te definiëren voor het terugzetten van de auteurversie:

1. Ga naar *https://:&lt;PublishHost>:&lt;PublishPort>/lc/system/console/configMgr*. Meld u aan met de gebruikersgegevens van de OSGi Management Console. De standaardreferenties zijn admin/admin.
1. Zoek en klik op het pictogram **[!UICONTROL Edit]** naast de instelling **[!UICONTROL com.adobe.livecycle.content.activate.impl.VersionRestoreManagerImpl.name]**.
1. Geef in het veld **[!UICONTROL VersionRestoreManager Author URL]** de URL van de instantie Auteur van VersionRestoreManager op.

   **URL-tekenreeks**:

   `https://<hostname>:<port>:/libs/fd/fdm/content/crud/lc.content.remote.activate.VersionRestoreManager`

   >[!NOTE]
   >
   >Als er meerdere auteur-instanties (geclusterd) zijn met een taakverdeler, geeft u de URL voor het taakverdelingsmechanisme op in het veld **[!UICONTROL VersionRestoreManager Author URL]**.

1. Klik op **[!UICONTROL Save]**.

## De URL van de instantie Publish definiëren voor ActivationManagerImpl (public instance activation manager) {#defining-the-publish-instance-url-for-activationmanagerimpl-public-instance-activation-manager}

Voer de volgende stappen uit om de URL van de instantie Publiceren te definiëren voor het beheer voor activering van openbare instanties:

1. Ga naar *https://:&lt;auteurshost>:&lt;auteurPort>/lc/system/console/configMgr*. Meld u aan met de gebruikersgegevens van de OSGi Management Console. De standaardreferenties zijn admin/admin.
1. Zoek en klik op het pictogram **[!UICONTROL Edit]** naast de instelling **[!UICONTROL com.adobe.livecycle.content.activate.impl.ActivationManagerImpl.name]**.
1. Geef in het veld **[!UICONTROL ActivationManager Publish URL]** de URL op voor toegang tot de instantie Publish ActivationManager. U kunt de volgende URL&#39;s opgeven.

   * **Load Balancer URL (aanbevolen)**: Geef een URL voor het taakverdelingsmechanisme op als u een webserver hebt die als taakverdelingsmechanisme fungeert vóór het publicatiefarm (meerdere niet-geclusterde publicatieinstanties).
   * **URL** van instantie publiceren: Geef een URL voor een publicatieexemplaar op als u één publicatieexemplaar hebt of als de webserver die de publicatiecapaciteit doorstuurt, niet toegankelijk is vanuit de auteursomgeving vanwege beperkingen. Als de opgegeven publicatie-instantie is ingedrukt, is er een fallback-mechanisme waarmee aan de auteurzijde moet worden omgegaan.
   * **URL-tekenreeks**:

      `https://<hostname>:<port>:/libs/fd/fdm/content/crud/lc.content.remote.activate.activationManager`

1. Klik op **[!UICONTROL Save]**.

Voor meer informatie over het vormen van het Beheer van de Correspondentie, zie [Eigenschappen van de Configuratie van het Beheer van de Correspondentie](https://helpx.adobe.com/aem-forms/6-2/cm-configuration-properties.html).
