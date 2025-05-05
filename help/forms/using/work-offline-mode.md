---
title: Werken in de offlinemodus
description: Maak uw mobiele apparaat offline buiten het AEM Forms-netwerkbereik of in een volledig offline modus en werk aan de AEM Forms-app
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: forms-app
exl-id: ba4ceef1-510d-41ef-94b8-4834fb7de804
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
role: User, Developer
source-git-commit: e821be5233fd5f6688507096790d219d25903892
workflow-type: tm+mt
source-wordcount: '532'
ht-degree: 0%

---

# Werken in de offlinemodus {#working-in-the-offline-mode}

In de offlinemodus van de AEM Forms-app kunt u naadloos werken, zelfs als de app offline gaat. U kunt een formulier openen, bijwerken en verzenden zonder netwerkconnectiviteit nodig te hebben.

U begint met het werken aan de AEM Forms-app door uw app te synchroniseren met de AEM Forms-server. Alle aan u toegewezen formulieren worden gedownload in uw app. Voor AEM Forms on JEE worden taken opgehaald op het tabblad Taken en worden hiermee samenhangende formulieren en andere formulieren gestart op het tabblad Forms. Voor AEM Forms op OSGi wordt alleen Forms geladen op het tabblad Forms.

Voor details op hoe te om app te synchroniseren, zie [ Synchronizing app ](/help/forms/using/sync-app.md).

## Forms offline beschikbaar maken {#making-forms-available-offline}

Wanneer u uw toepassing synchroniseert met de AEM Forms-server, worden de formulieren naar uw mobiele apparaat gedownload. De bijlagen die aan het formulier zijn gekoppeld, worden echter standaard niet gedownload. Dit houdt in dat als u online bent, u de bijlagen kunt bekijken. Als u er echter voor wilt zorgen dat u de bijlage kunt weergeven in de offline modus, wijzigt u de standaardinstellingen in uw app.

Als u wilt dat de bijbehorende bijlagen bij elk formulier worden gedownload, stelt u Bijlagen zoeken in op AAN. Voor details, zie [ Bijwerkend algemene montages ](/help/forms/using/update-general-settings.md).

Aangezien het downloaden van gegevens op het mobiele apparaat de prestaties van het apparaat kan beïnvloeden, wordt de instelling voor Vetbijlagen standaard ingesteld op UIT. De bijlagen worden opgehaald naar het apparaat voor elke taak die van de server wordt gedownload nadat de instelling is bijgewerkt naar ON. Op de off-line wijze, kan een gebruiker aan alle taken dan werken die aan apparaat na het plaatsen van de **gehechtheid van de Ophalen** opties aan. worden gedownload

## Offlineservice configureren voor AEM Forms-app {#configuring-offline-service-for-aem-forms-app-br}

De offlineservice van de AEM Forms-app identificeert de bronnen die in een formulier worden gebruikt. De AEM Forms-app is afhankelijk van deze service voor informatie over formulierafhankelijkheden. Informatie over formulierafhankelijkheden is vereist om offline functies in te schakelen. De AEM Forms-app offline service plaatst de paden of URL&#39;s van de bronnen die in een formulier worden gebruikt in cache. Het cachegeheugen wordt bijgewerkt op basis van de wijzigingen in het formulier en de geldigheidsperiode die voor de offlineservice zijn geconfigureerd. Het in cache plaatsen van paden of URL&#39;s van de bronnen die in een formulier worden gebruikt, verbetert de prestaties op de server.

U configureert als volgt de offline component aan de serverzijde van de AEM Forms-app:

1. In de auteursinstantie, navigeer aan **Adobe Experience Manager** > **Hulpmiddelen** > **Forms** > **Vorm de Offlinedienst van Forms App**.

   URL: `https://<server>:<port>/<context-path>/libs/fd/workspace-offline/gui/content/config.html`

1. Onder Algemene instellingen kunt u het volgende uitvoeren:

   * **Duidelijk Geheime voorgeheugen**: ontruimt het geheime voorgeheugen van de serverzijde van de vormgebiedsdelen.
   * **Configuratie van het Terugstellen**: stelt de AEM Forms app off-line configuratie opnieuw in.
   * **Geldigheid van het Geheime voorgeheugen**: Specificeert de geldigheidsperiode voor het server-kant off-line geheime voorgeheugen.
   * **Paden van de Waarneming van het Middel**: Specificeert wegen waar de off-line dienst voor middelveranderingen controleert. Als er wijzigingen optreden in de opgegeven paden, wordt de offlinecache van alle afhankelijke formulieren bijgewerkt. Bijvoorbeeld `/etc/clientlibs/fd,/content/dam/images` .

1. In het **lusje van het Geheime voorgeheugen van het 1&rbrace; Hand van het Middel**, specificeer de vorm gebiedsdelen off-line dienst niet kan identificeren. U kunt bronnen opgeven, zoals afbeeldingen die vanuit JavaScript worden geladen. De AEM Forms-app downloadt deze bronnen ook voor de offline modus.
