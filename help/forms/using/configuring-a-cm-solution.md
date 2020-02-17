---
title: Een Correspondentiebeheeroplossing configureren
seo-title: Een Correspondentiebeheeroplossing configureren
description: 'null'
seo-description: 'null'
uuid: 76b25004-fe47-44d7-9bed-7c0fd963306b
topic-tags: correspondence-management
content-type: reference
products: SG_EXPERIENCEMANAGER/6.3/FORMS
discoiquuid: 186ca75c-638b-4057-826e-cd5d56aa0397
translation-type: tm+mt
source-git-commit: 5120bbdefea528ad6d07a9c99df565555b6a8444

---


# Een Correspondentiebeheeroplossing configureren {#configuring-a-correspondence-management-solution}

## URL van auteurinstantie voor VersionRestoreManagerImpl bepalen {#defining-author-instance-url-for-versionrestoremanagerimpl}

Gebruik de volgende stappen om een instantie-URL van de auteur te definiëren voor het terugzetten van de auteurversie:

1. Ga naar *https://:&lt;PublishHost>:&lt;PublishPort>/lc/system/console/configMgr*. Meld u aan met de gebruikersgegevens van de OSGi Management Console. De standaardreferenties zijn admin/admin.
1. Zoek en klik op het pictogram **[!UICONTROL Bewerken]** naast de instelling **[!UICONTROL com.adobe.livecycle.content.activate.impl.VersionRestoreManagerImpl.name]** .
1. Geef in het veld **[!UICONTROL VersionRestoreManager-auteur-URL]** de URL van de instantie Auteur van VersionRestoreManager op.

   **URL-tekenreeks**:

   `https://<hostname>:<port>:/libs/fd/fdm/content/crud/lc.content.remote.activate.VersionRestoreManager`

   >[!NOTE]
   >
   >Als er meerdere auteur-instanties (geclusterd) zijn die door een Load Balancer worden voorafgegaan, geeft u de URL voor het taakverdelingsmechanisme op in het veld **[!UICONTROL VersionRestoreManager-auteur-URL]** .

1. Click **[!UICONTROL Save]**.

## De URL van de instantie Publish definiëren voor ActivationManagerImpl (public instance activation manager) {#defining-the-publish-instance-url-for-activationmanagerimpl-public-instance-activation-manager}

Voer de volgende stappen uit om de URL van de instantie Publiceren te definiëren voor het beheer voor activering van openbare instanties:

1. Ga naar *https://:&lt;auteurshost>:&lt;auteurshaven>/lc/system/console/configMgr*. Meld u aan met de gebruikersgegevens van de OSGi Management Console. De standaardreferenties zijn admin/admin.
1. Zoek en klik op het pictogram **[!UICONTROL Bewerken]** naast de instelling **[!UICONTROL com.adobe.livecycle.content.activate.impl.ActivationManagerImpl.name]** .
1. Geef in het veld URL **[!UICONTROL voor publiceren van]** ActivationManager de URL op voor toegang tot de instantie Publish ActivationManager. U kunt de volgende URL&#39;s opgeven.

   * **Load Balancer URL (aanbevolen)**: Geef een URL voor het taakverdelingsmechanisme op als u een webserver hebt die als taakverdelingsmechanisme fungeert vóór het publicatiefarm (meerdere niet-geclusterde publicatieinstanties).
   * **URL** van instantie publiceren: Geef een URL voor een publicatieexemplaar op als u één publicatieexemplaar hebt of als de webserver die de publicatiecapaciteit doorstuurt, niet toegankelijk is vanuit de auteursomgeving vanwege beperkingen. Als de opgegeven publicatie-instantie is ingedrukt, is er een fallback-mechanisme waarmee aan de auteurzijde moet worden omgegaan.
   * **URL-tekenreeks**:

      `https://<hostname>:<port>:/libs/fd/fdm/content/crud/lc.content.remote.activate.activationManager`

1. Click **[!UICONTROL Save]**.

Voor meer informatie over het vormen van het Beheer van de Correspondentie, zie de Eigenschappen [van de Configuratie van het Beheer van de](https://helpx.adobe.com/aem-forms/6-2/cm-configuration-properties.html)Correspondentie.
