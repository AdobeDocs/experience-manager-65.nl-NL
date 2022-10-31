---
title: Een gesloten gebruikersgroep maken
seo-title: Creating a Closed User Group
description: Leer hoe u een gesloten gebruikersgroep maakt.
seo-description: Learn how to create a Closed User Group.
uuid: dc3c7dbd-2e86-43f9-9377-3b75053203b3
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: Security
content-type: reference
discoiquuid: 6ae57874-a9a1-4208-9001-7f44a1f57cbe
docset: aem65
exl-id: 9efba91d-45e8-42e1-9db6-490d21bf7412
source-git-commit: a5f3e33a6abe7ac1bbd610a8528fd599d1ffd2aa
workflow-type: tm+mt
source-wordcount: '794'
ht-degree: 0%

---

# Een gesloten gebruikersgroep maken{#creating-a-closed-user-group}

Gesloten gebruikersgroepen (CUG&#39;s) worden gebruikt om de toegang tot specifieke pagina&#39;s op een gepubliceerde website te beperken. Dergelijke pagina&#39;s vereisen de toegewezen leden login en verstrekken veiligheidsgeloofsbrieven.

U configureert een dergelijk gebied binnen uw website als volgt:

* [de werkelijke gesloten gebruikersgroep maken en leden toewijzen](#creating-the-user-group-to-be-used).

* [deze groep toepassen op de vereiste pagina&#39;s](#applying-your-closed-user-group-to-content-pages) en selecteer (of maak) de aanmeldingspagina voor gebruik door de leden van de CUG; ook opgegeven bij het toepassen van een CUG op een inhoudspagina.

* [een koppeling van een of andere vorm maken naar ten minste één pagina in het beschermde gebied](#linking-to-the-realm)anders is het niet zichtbaar.
* [de Dispatcher configureren](#configure-dispatcher-for-cugs) indien in gebruik.

>[!CAUTION]
>
>Gesloten gebruikersgroepen (CUG&#39;s) moeten altijd worden gemaakt met het oog op prestaties.
>
>Hoewel het aantal gebruikers en groepen in een CUG niet beperkt is, kan een hoog aantal CUG&#39;s op een pagina de renderprestaties vertragen.
>
>Bij het testen van de prestaties moet altijd rekening worden gehouden met het effect van CUG&#39;s.

## Gebruikersgroep maken die moet worden gebruikt {#creating-the-user-group-to-be-used}

Een gesloten gebruikersgroep maken:

1. Ga naar **Gereedschappen - Beveiliging** van het AEM huisdier.

   >[!NOTE]
   >
   >Zie [Gebruikers en groepen beheren](/help/sites-administering/security.md#managing-users-and-groups) voor volledige informatie over het creëren van en het vormen van gebruikers en groepen.

1. Selecteer **Groepen** van het volgende scherm.

   ![screenshot_2018-10-30at145502](assets/screenshot_2018-10-30at145502.png)

1. Druk op **Maken** in de rechterbovenhoek om een nieuwe groep te maken.
1. Geef de nieuwe groep een naam; bijvoorbeeld: `cug_access`.

   ![screenshot_2018-10-30at151459](assets/screenshot_2018-10-30at151459.png)

1. Ga naar de **Leden** en wijst u de vereiste gebruikers toe aan deze groep.

   ![screenshot_2018-10-30at151808](assets/screenshot_2018-10-30at151808.png)

1. Activeer om het even welke gebruikers die u aan uw CUG hebt toegewezen; in dit geval, alle leden van `cug_access`.
1. Activeer de gesloten gebruikersgroep zodat deze beschikbaar is in de publicatieomgeving; in dit voorbeeld: `cug_access`.

## Gesloten gebruikersgroep toepassen op inhoudspagina&#39;s {#applying-your-closed-user-group-to-content-pages}

De CUG toepassen op een pagina:

1. Navigeer naar de basispagina van de beperkte sectie die u aan uw CUG wilt toewijzen.
1. Selecteer de pagina door op de bijbehorende miniatuur te klikken en vervolgens op **Eigenschappen** in het bovenste deelvenster.

   ![screenshot_2018-10-30at162632](assets/screenshot_2018-10-30at162632.png)

1. Ga in het volgende venster naar de **Geavanceerd** tab.
1. Schuif omlaag en schakel het selectievakje in het dialoogvenster **Verificatievereiste** sectie.

1. Voeg hieronder uw configuratiepad toe en druk op Opslaan.
1. Ga vervolgens naar de **Machtigingen** en druk op **Gesloten gebruikersgroep bewerken** knop.

   ![screenshot_2018-10-30at163003](assets/screenshot_2018-10-30at163003.png)

   >[!NOTE]
   >
   >CUG&#39;s op het tabblad Machtigingen kunnen niet worden geïmplementeerd voor actieve kopieën van blauwdrukken. Plan dit probleem bij het configureren van Live Copy.
   >
   >Zie voor meer informatie [deze pagina](closed-user-groups.md#aem-livecopy).

1. Zoek naar en voeg uw GIDS in het volgende venster toe - in dit geval voeg de genoemde groep toe **cug_access**. Tot slot, druk **Opslaan**.
1. Klikken **Ingeschakeld** om te bepalen dat deze pagina (en om het even welke kindpagina&#39;s) tot een CUG behoren.
1. Geef de **Aanmeldingspagina** de leden van de groep gebruiken; bijvoorbeeld:

   `/content/geometrixx/en/toolbar/login.html`

   Dit is optioneel. Als de standaardaanmeldingspagina leeg blijft, wordt deze gebruikt.

1. Voeg de **Toegestane groepen**. Gebruik + om groepen toe te voegen of - om te verwijderen. Alleen leden van deze groepen mogen zich aanmelden en toegang krijgen tot de pagina&#39;s.
1. Een **Realm** (een naam voor de paginagroepen), indien vereist. Laat leeg als u de paginatitel wilt gebruiken.
1. Klikken **OK** om de specificatie op te slaan.

Zie [Identity Management](/help/sites-administering/identity-management.md) voor informatie over profielen in het publicatiemilieu en het verstrekken van vormen voor het programma openen en uit.

## Koppeling met de realiteit {#linking-to-the-realm}

Aangezien het doel van koppelingen naar CUG Realm niet zichtbaar is voor de anonieme gebruiker, verwijdert de koppelingencontrole dergelijke koppelingen.

Om dit te voorkomen, is het aan te raden om niet-beveiligde omleidingspagina&#39;s te maken die verwijzen naar pagina&#39;s in de CUG Realm. De navigatie-items worden vervolgens gerenderd zonder dat de koppelingencontrole problemen ondervindt. Alleen wanneer de gebruiker de omleidingspagina daadwerkelijk opent, wordt de gebruiker omgeleid in de CUG Realm - nadat hij of zij zijn of haar aanmeldingsgegevens heeft opgegeven.

## Dispatcher configureren voor CUG&#39;s {#configure-dispatcher-for-cugs}

Als u Dispatcher gebruikt, moet u een landbouwbedrijf van de Verzender met de volgende eigenschappen bepalen:

* [virtuele hosts](https://helpx.adobe.com/experience-manager/dispatcher/using/dispatcher-configuration.html#identifying-virtual-hosts-virtualhosts): Komt overeen met het pad naar de pagina&#39;s waarop de CUG van toepassing is.
* \sessionmanagement: zie hieronder.
* [cachegeheugen](https://helpx.adobe.com/experience-manager/dispatcher/using/dispatcher-configuration.html#configuring-the-dispatcher-cache-cache): Een cachemap die is toegewezen aan de bestanden waarop de CUG van toepassing is.

### Sessiebeheer voor Dispatcher configureren voor CUG&#39;s {#configuring-dispatcher-session-management-for-cugs}

Configureren [sessiebeheer in de dispatcher.any, bestand](https://helpx.adobe.com/experience-manager/dispatcher/using/dispatcher-configuration.html#enabling-secure-sessions-sessionmanagement) voor de CUG. De authentificatiemanager die wordt gebruikt wanneer de toegang voor de pagina&#39;s van de CUG wordt gevraagd bepaalt hoe u zittingsbeheer vormt.

```xml
/sessionmanagement
    ...
    /header "Cookie:login-token"
    ...
```

>[!NOTE]
>
>Wanneer een landbouwbedrijf van de Verzender zitting-beheer toegelaten heeft, alle pagina&#39;s die de landbouwbedrijfhandvatten niet in het voorgeheugen onder worden gebracht. Om pagina&#39;s in het voorgeheugen onder te brengen die buiten CUG zijn, creeer een tweede landbouwbedrijf in dispatcher.any
>die de niet-CUG-pagina&#39;s afhandelt.

1. Configureren [/sessionmanagement](https://helpx.adobe.com/experience-manager/dispatcher/using/dispatcher-configuration.html#enabling-secure-sessions-sessionmanagement) door `/directory`; bijvoorbeeld:

   ```xml
   /sessionmanagement
     {
     /directory "/usr/local/apache/.sessions"
     ...
     }
   ```

1. Set [/allowAuthorized](https://helpx.adobe.com/experience-manager/dispatcher/using/dispatcher-configuration.html#caching-when-authentication-is-used) tot `0`.
