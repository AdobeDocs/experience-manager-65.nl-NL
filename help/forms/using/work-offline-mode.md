---
title: Werken in de offlinemodus
seo-title: Werken in de offlinemodus
description: Maak uw mobiele apparaat offline buiten uw AEM Forms-netwerkbereik of in een volledig offline modus en werk aan de AEM Forms-app
seo-description: Maak uw mobiele apparaat offline buiten uw AEM Forms-netwerkbereik of in een volledig offline modus en werk aan de AEM Forms-app
uuid: b900a0f8-90ce-486a-bde6-6cdf11bd2801
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: forms-app
discoiquuid: 9a3c6ab4-8bb9-40c7-8c56-59153b364887
translation-type: tm+mt
source-git-commit: 56c6cfd437ef185336e81373bd5f758205b96317
workflow-type: tm+mt
source-wordcount: '561'
ht-degree: 0%

---


# Werken in de offlinemodus {#working-in-the-offline-mode}

In de offlinemodus van de AEM Forms-app kunt u naadloos werken, zelfs als de app offline gaat. U kunt een formulier openen, bijwerken en verzenden zonder netwerkconnectiviteit nodig te hebben.

U begint met het werken aan de AEM Forms-app door uw app te synchroniseren met de AEM Forms-server. Alle aan u toegewezen formulieren worden gedownload in uw app. Voor AEM Forms on JEE worden taken opgehaald op het tabblad Taken en worden hiermee samenhangende formulieren en andere formulieren gestart op het tabblad Forms. Voor AEM Forms op OSGi wordt alleen Forms geladen op het tabblad Forms.

Zie [De app synchroniseren](/help/forms/using/sync-app.md) voor meer informatie over het synchroniseren van de app.

## Forms offline beschikbaar maken {#making-forms-available-offline}

Wanneer u uw toepassing synchroniseert met de AEM Forms-server, worden de formulieren naar uw mobiele apparaat gedownload. De bijlagen die aan het formulier zijn gekoppeld, worden echter standaard niet gedownload. Dit houdt in dat als u online bent, u de bijlagen kunt bekijken. Als u er echter voor wilt zorgen dat u de bijlage kunt weergeven in de offline modus, wijzigt u de standaardinstellingen in uw app.

Als u wilt dat de bijbehorende bijlagen bij elk formulier worden gedownload, stelt u Bijlagen zoeken in op AAN. Zie [Algemene instellingen bijwerken](/help/forms/using/update-general-settings.md) voor meer informatie.

Aangezien het downloaden van gegevens op het mobiele apparaat de prestaties van het apparaat kan beïnvloeden, wordt de instelling voor Vetbijlagen standaard ingesteld op UIT. De bijlagen worden opgehaald naar het apparaat voor elke taak die van de server wordt gedownload nadat de instelling is bijgewerkt naar ON. In de offlinemodus kan een gebruiker vervolgens werken aan alle taken die naar het apparaat worden gedownload nadat de opties **Bijlagen ophalen** op AAN zijn ingesteld.

## Offlineservice configureren voor AEM Forms-app {#configuring-offline-service-for-aem-forms-app-br}

De offlineservice van de AEM Forms-app identificeert de bronnen die in een formulier worden gebruikt. De AEM Forms-app is afhankelijk van deze service voor informatie over formulierafhankelijkheden. Informatie over formulierafhankelijkheden is vereist om offline functies in te schakelen. De AEM Forms-app offline service plaatst de paden of URL&#39;s van de bronnen die in een formulier worden gebruikt in cache. Het cachegeheugen wordt bijgewerkt op basis van de wijzigingen in het formulier en de geldigheidsperiode die voor de offlineservice zijn geconfigureerd. Het in cache plaatsen van paden of URL&#39;s van de bronnen die in een formulier worden gebruikt, verbetert de prestaties op de server.

U configureert als volgt de offline servercomponent van de AEM Forms-app:

1. Navigeer in de auteurinstantie naar **Adobe Experience Manager** >**Tools** > **Forms** > **Forms App Offline Service configureren**.

   URL: `https://<server>:<port>/<context-path>/libs/fd/workspace-offline/gui/content/config.html`

1. Onder Algemene instellingen kunt u het volgende uitvoeren:

   * **Cache** wissen: Hiermee wist u de cache aan serverzijde van de formulierafhankelijkheden.
   * **Configuratie** opnieuw instellen: Hiermee herstelt u de offlineconfiguratie van de AEM Forms-toepassing.
   * **Geldigheid** cache: Geeft de geldigheidsperiode aan voor de offlinecache aan de serverzijde.
   * **Paden** voor bronwaarneming: Specificeert wegen waar de off-line dienst voor middelveranderingen controleert. Als er wijzigingen optreden in de opgegeven paden, wordt de offlinecache van alle afhankelijke formulieren bijgewerkt. Bijvoorbeeld, `/etc/clientlibs/fd,/content/dam/images`.

1. Geef op het tabblad **Handmatige broncache** de formulierafhankelijkheden op die de offlineservice niet kan identificeren. U kunt bronnen opgeven, zoals afbeeldingen die vanuit JavaScript zijn geladen. De AEM Forms-app downloadt deze bronnen ook voor de offline modus.
