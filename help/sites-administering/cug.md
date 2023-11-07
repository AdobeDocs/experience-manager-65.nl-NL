---
title: Een gesloten gebruikersgroep maken
description: Leer hoe u een gesloten gebruikersgroep maakt.
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: Security
content-type: reference
docset: aem65
exl-id: 9efba91d-45e8-42e1-9db6-490d21bf7412
source-git-commit: 49688c1e64038ff5fde617e52e1c14878e3191e5
workflow-type: tm+mt
source-wordcount: '747'
ht-degree: 0%

---

# Een gesloten gebruikersgroep maken{#creating-a-closed-user-group}

Gesloten gebruikersgroepen (CUG&#39;s) worden gebruikt om de toegang te beperken tot specifieke pagina&#39;s die zich op een gepubliceerde website bevinden. Dergelijke pagina&#39;s vereisen de toegewezen leden login en verstrekken veiligheidsgeloofsbrieven.

U configureert een dergelijk gebied binnen uw website als volgt:

* [de werkelijke gesloten gebruikersgroep maken en leden toewijzen](#creating-the-user-group-to-be-used).

* [deze groep toepassen op de vereiste pagina&#39;s](#applying-your-closed-user-group-to-content-pages) en selecteer (of maak) de aanmeldingspagina voor gebruik door de leden van de CUG; ook opgegeven bij het toepassen van een CUG op een inhoudspagina.

* [een koppeling van een of andere vorm maken naar ten minste één pagina in het beschermde gebied](#linking-to-the-cug-pages)anders is het niet zichtbaar.

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

1. Selecteer de **Groepen** van het volgende scherm.

   ![screenshot_2018-10-30at145502](assets/screenshot_2018-10-30at145502.png)

1. Druk op **Maken** in de rechterbovenhoek om een groep te maken.
1. Geef de nieuwe groep een naam, bijvoorbeeld `cug_access`.

   ![screenshot_2018-10-30at151459](assets/screenshot_2018-10-30at151459.png)

1. Ga naar de **Leden** en wijst u de vereiste gebruikers toe aan deze groep.

   ![screenshot_2018-10-30at151808](assets/screenshot_2018-10-30at151808.png)

1. Activeer om het even welke gebruikers die u aan uw CUG hebt toegewezen; in dit geval, alle leden van `cug_access`.
1. Activeer de gesloten gebruikersgroep zodat deze beschikbaar is in de publicatieomgeving; in dit voorbeeld `cug_access`.

## Gesloten gebruikersgroep toepassen op inhoudspagina&#39;s {#applying-your-closed-user-group-to-content-pages}

De CUG toepassen op een pagina of pagina&#39;s:

1. Navigeer naar de basispagina van de beperkte sectie die u aan uw CUG wilt toewijzen.
1. Selecteer de pagina door op de bijbehorende miniatuur te klikken en vervolgens de pagina te selecteren **Eigenschappen** in de bovenste werkbalk.

   ![screenshot_2018-10-30at162632](assets/screenshot_2018-10-30at162632.png)

1. Open in het volgende venster de **Geavanceerd** tab.

1. Omlaag schuiven naar de **Verificatievereiste** sectie.

   1. Activeer **Inschakelen** tickbox.

   1. Voeg het pad toe aan uw **Aanmeldingspagina**.
Dit is optioneel als de standaardaanmeldingspagina leeg blijft.

   ![CUG toegevoegd](assets/cug-authentication-requirement.png)

1. Ga vervolgens naar de **Machtigingen** en selecteert u **Gesloten gebruikersgroep bewerken**.

   ![screenshot_2018-10-30at163003](assets/screenshot_2018-10-30at163003.png)

   >[!NOTE]
   >
   >CUG&#39;s op het tabblad Machtigingen kunnen niet worden geïmplementeerd voor actieve kopieën van blauwdrukken. Plan dit rond wanneer het vormen van Levend Exemplaar.
   >
   >Zie voor meer informatie [deze pagina](closed-user-groups.md#aem-livecopy).

1. De **Gesloten gebruikersgroep bewerken** wordt geopend. Hier kunt u zoeken naar en uw CUG selecteren en vervolgens de groepselectie bevestigen met **Opslaan**.

   De groep wordt toegevoegd aan de lijst, bijvoorbeeld de groep **cug_access**.

   ![CUG toegevoegd](assets/cug-added.png)

1. Wijzigingen bevestigen met **Opslaan en sluiten**.

>[!NOTE]
>
>Zie [Identity Management](/help/sites-administering/identity-management.md) voor informatie over profielen in het publicatiemilieu en het verstrekken van vormen voor het programma openen en uit.

## Koppelen aan de CUG-pagina&#39;s {#linking-to-the-cug-pages}

Aangezien het doel van koppelingen naar de CUG-pagina&#39;s niet zichtbaar is voor de anonieme gebruiker, verwijdert de koppelingencontrole dergelijke koppelingen.

Om dit te voorkomen, is het raadzaam om niet-beveiligde omleidingspagina&#39;s te maken die verwijzen naar pagina&#39;s in het gebied CUG. De navigatie-items worden vervolgens gerenderd zonder dat de koppelingencontrole problemen ondervindt. Alleen wanneer de omleidingspagina daadwerkelijk wordt geopend, wordt de gebruiker omgeleid binnen het CUG-gebied - nadat hij of zij zijn of haar aanmeldingsgegevens heeft opgegeven.

## Dispatcher configureren voor CUG&#39;s {#configure-dispatcher-for-cugs}

Als u Dispatcher gebruikt, moet u een landbouwbedrijf van de Verzender met de volgende eigenschappen bepalen:

* [virtuele hosts](https://experienceleague.adobe.com/docs/experience-manager-dispatcher/using/configuring/dispatcher-configuration.html?lang=en#identifying-virtual-hosts-virtualhosts): Komt overeen met het pad naar de pagina&#39;s waarop de CUG van toepassing is.
* \sessionmanagement: zie hieronder.
* [cachegeheugen](https://experienceleague.adobe.com/docs/experience-manager-dispatcher/using/configuring/dispatcher-configuration.html?lang=en#configuring-the-dispatcher-cache-cache): Een cachemap die is toegewezen aan de bestanden waarop de CUG van toepassing is.

### Sessiebeheer voor Dispatcher configureren voor CUG&#39;s {#configuring-dispatcher-session-management-for-cugs}

Configureren [sessiebeheer in de dispatcher.any, bestand](https://experienceleague.adobe.com/docs/experience-manager-dispatcher/using/configuring/dispatcher-configuration.html?lang=en#enabling-secure-sessions-sessionmanagement) voor de CUG. De authentificatiemanager die wordt gebruikt wanneer de toegang voor de pagina&#39;s van de CUG wordt gevraagd bepaalt hoe u zittingsbeheer vormt.

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

1. Configureren [/sessionmanagement](https://experienceleague.adobe.com/docs/experience-manager-dispatcher/using/configuring/dispatcher-configuration.html?lang=en#enabling-secure-sessions-sessionmanagement) door `/directory`; bijvoorbeeld:

   ```xml
   /sessionmanagement
     {
     /directory "/usr/local/apache/.sessions"
     ...
     }
   ```

1. Set [/allowAuthorized](https://experienceleague.adobe.com/docs/experience-manager-dispatcher/using/configuring/dispatcher-configuration.html?lang=en#caching-when-authentication-is-used) tot `0`.
