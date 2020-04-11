---
title: Werken in de offlinemodus
seo-title: Werken in de offlinemodus
description: Maak uw mobiele apparaat offline buiten het bereik van het AEM Forms-netwerk of in een volledig offline modus en werk in de app AEM Forms
seo-description: Maak uw mobiele apparaat offline buiten het bereik van het AEM Forms-netwerk of in een volledig offline modus en werk in de app AEM Forms
uuid: b900a0f8-90ce-486a-bde6-6cdf11bd2801
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: forms-app
discoiquuid: 9a3c6ab4-8bb9-40c7-8c56-59153b364887
translation-type: tm+mt
source-git-commit: 56c6cfd437ef185336e81373bd5f758205b96317

---


# Werken in de offlinemodus {#working-in-the-offline-mode}

In de offlinemodus van de app AEM Forms kunt u naadloos werken, zelfs als de app offline gaat. U kunt een formulier openen, bijwerken en verzenden zonder netwerkconnectiviteit nodig te hebben.

U begint met het werken aan de app AEM Forms door uw app te synchroniseren met de AEM Forms-server. Alle aan u toegewezen formulieren worden gedownload in uw app. Voor AEM Forms on JEE worden de taken opgehaald op het tabblad Taken en worden de bijbehorende formulieren en andere formulieren gestart op het tabblad Formulieren. Voor AEM-formulieren op OSGi worden alleen Forms geladen op het tabblad Formulieren.

Zie De app [synchroniseren voor meer informatie over het synchroniseren van de app](/help/forms/using/sync-app.md).

## Formulieren offline beschikbaar maken {#making-forms-available-offline}

Wanneer u uw app synchroniseert met de AEM Forms-server, worden de formulieren gedownload naar uw mobiele apparaat. De bijlagen die aan het formulier zijn gekoppeld, worden echter standaard niet gedownload. Dit houdt in dat als u online bent, u de bijlagen kunt bekijken. Als u er echter voor wilt zorgen dat u de bijlage kunt weergeven in de offline modus, wijzigt u de standaardinstellingen in uw app.

Als u wilt dat de bijbehorende bijlagen bij elk formulier worden gedownload, stelt u Bijlagen zoeken in op AAN. Zie Algemene instellingen [bijwerken voor meer informatie](/help/forms/using/update-general-settings.md).

Aangezien het downloaden van gegevens op het mobiele apparaat de prestaties van het apparaat kan beïnvloeden, wordt de instelling voor Vetbijlagen standaard ingesteld op UIT. De bijlagen worden opgehaald naar het apparaat voor elke taak die van de server wordt gedownload nadat de instelling is bijgewerkt naar ON. In de offlinemodus kan een gebruiker vervolgens werken aan alle taken die naar het apparaat worden gedownload nadat de opties voor **bijlage** ophalen op Aan zijn ingesteld.

## Offlineservice configureren voor de app AEM Forms {#configuring-offline-service-for-aem-forms-app-br}

De app-offlineservice van AEM Forms identificeert de bronnen die in een formulier worden gebruikt. De app AEM Forms is afhankelijk van deze service voor informatie over formulierafhankelijkheden. Informatie over formulierafhankelijkheden is vereist om offline functies in te schakelen. De app-offlineservice van AEM Forms plaatst de paden of URL&#39;s van de bronnen die in een formulier worden gebruikt in cache. Het cachegeheugen wordt bijgewerkt op basis van de wijzigingen in het formulier en de geldigheidsperiode die voor de offlineservice zijn geconfigureerd. Het in cache plaatsen van paden of URL&#39;s van de bronnen die in een formulier worden gebruikt, verbetert de prestaties op de server.

U configureert als volgt de offline component op de server van de app AEM Forms:

1. Ga in de auteurinstantie naar **Adobe Experience Manager** >**Gereedschappen** > **Formulieren** > Forms App Offline Service **** configureren.

   URL: `https://<server>:<port>/<context-path>/libs/fd/workspace-offline/gui/content/config.html`

1. Onder Algemene instellingen kunt u het volgende uitvoeren:

   * **Cache** wissen: Hiermee wist u de cache aan serverzijde van de formulierafhankelijkheden.
   * **Configuratie** opnieuw instellen: Hiermee herstelt u de offlineconfiguratie van de app AEM Forms.
   * **Geldigheid** cache: Geeft de geldigheidsperiode aan voor de offlinecache aan de serverzijde.
   * **Paden** voor bronwaarneming: Specificeert wegen waar de off-line dienst voor middelveranderingen controleert. Als er wijzigingen optreden in de opgegeven paden, wordt de offlinecache van alle afhankelijke formulieren bijgewerkt. Bijvoorbeeld, `/etc/clientlibs/fd,/content/dam/images`.

1. Geef op het tabblad **Handmatige broncache** de formulierafhankelijkheden op die de offlineservice niet kan identificeren. U kunt bronnen opgeven, zoals afbeeldingen die vanuit JavaScript zijn geladen. De app AEM Forms downloadt deze bronnen ook voor de offline modus.
