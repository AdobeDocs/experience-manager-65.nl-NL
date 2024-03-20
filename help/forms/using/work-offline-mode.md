---
title: Werken in de offlinemodus
description: Maak uw mobiele apparaat offline buiten het AEM Forms-netwerkbereik of in een volledig offline modus en werk aan de AEM Forms-app
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: forms-app
exl-id: ba4ceef1-510d-41ef-94b8-4834fb7de804
solution: Experience Manager, Experience Manager Forms
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '532'
ht-degree: 0%

---

# Werken in de offlinemodus {#working-in-the-offline-mode}

In de offlinemodus van de AEM Forms-app kunt u naadloos werken, zelfs als de app offline gaat. U kunt een formulier openen, bijwerken en verzenden zonder netwerkconnectiviteit nodig te hebben.

U begint met het werken aan de AEM Forms-app door uw app te synchroniseren met de AEM Forms-server. Alle aan u toegewezen formulieren worden gedownload in uw app. Voor AEM Forms on JEE worden taken opgehaald op het tabblad Taken en worden hiermee samenhangende formulieren en andere formulieren gestart op het tabblad Forms. Voor AEM Forms op OSGi wordt alleen Forms geladen op het tabblad Forms.

Ga voor meer informatie over het synchroniseren van de app naar [De app synchroniseren](/help/forms/using/sync-app.md).

## Forms offline beschikbaar maken {#making-forms-available-offline}

Wanneer u uw toepassing synchroniseert met de AEM Forms-server, worden de formulieren naar uw mobiele apparaat gedownload. De bijlagen die aan het formulier zijn gekoppeld, worden echter standaard niet gedownload. Dit houdt in dat als u online bent, u de bijlagen kunt bekijken. Als u er echter voor wilt zorgen dat u de bijlage kunt weergeven in de offline modus, wijzigt u de standaardinstellingen in uw app.

Als u wilt dat de bijbehorende bijlagen bij elk formulier worden gedownload, stelt u Bijlagen zoeken in op AAN. Zie voor meer informatie [Algemene instellingen bijwerken](/help/forms/using/update-general-settings.md).

Aangezien het downloaden van gegevens op het mobiele apparaat de prestaties van het apparaat kan beïnvloeden, wordt de instelling voor Vetbijlagen standaard ingesteld op UIT. De bijlagen worden opgehaald naar het apparaat voor elke taak die van de server wordt gedownload nadat de instelling is bijgewerkt naar ON. In de offlinemodus kan een gebruiker vervolgens werken aan alle taken die naar het apparaat worden gedownload nadat de **Bijlagen ophalen** aan AAN.

## Offlineservice configureren voor AEM Forms-app {#configuring-offline-service-for-aem-forms-app-br}

De offlineservice van de AEM Forms-app identificeert de bronnen die in een formulier worden gebruikt. De AEM Forms-app is afhankelijk van deze service voor informatie over formulierafhankelijkheden. Informatie over formulierafhankelijkheden is vereist om offline functies in te schakelen. De AEM Forms-app offline service plaatst de paden of URL&#39;s van de bronnen die in een formulier worden gebruikt in cache. Het cachegeheugen wordt bijgewerkt op basis van de wijzigingen in het formulier en de geldigheidsperiode die voor de offlineservice zijn geconfigureerd. Het in cache plaatsen van paden of URL&#39;s van de bronnen die in een formulier worden gebruikt, verbetert de prestaties op de server.

U configureert als volgt de offline component aan de serverzijde van de AEM Forms-app:

1. Navigeer in de auteurinstantie naar **Adobe Experience Manager** >**Gereedschappen** > **Forms** > **Forms App Offline Service configureren**.

   URL: `https://<server>:<port>/<context-path>/libs/fd/workspace-offline/gui/content/config.html`

1. Onder Algemene instellingen kunt u het volgende uitvoeren:

   * **Cache wissen**: Hiermee wist u de cache aan serverzijde van de formulierafhankelijkheden.
   * **Configuratie opnieuw instellen**: Hiermee herstelt u de offlineconfiguratie van de AEM Forms-toepassing.
   * **Geldigheid cache**: Geeft de geldigheidsperiode aan voor de offline cache aan de serverzijde.
   * **Paden voor middelenwaarneming**: Geeft paden aan waar de offlineservice de bron controleert. Als er wijzigingen optreden in de opgegeven paden, wordt de offlinecache van alle afhankelijke formulieren bijgewerkt. Bijvoorbeeld: `/etc/clientlibs/fd,/content/dam/images`.

1. In de **Handmatige broncache** kunt u opgeven welke afhankelijkheden van formulieren niet kunnen worden geïdentificeerd door de offlineservice. U kunt bronnen opgeven, zoals afbeeldingen die vanuit JavaScript zijn geladen. De AEM Forms-app downloadt deze bronnen ook voor de offline modus.
