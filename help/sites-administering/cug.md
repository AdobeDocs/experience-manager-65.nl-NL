---
title: Een gesloten gebruikersgroep maken
seo-title: Een gesloten gebruikersgroep maken
description: Leer hoe u een gesloten gebruikersgroep maakt.
seo-description: Leer hoe u een gesloten gebruikersgroep maakt.
uuid: dc3c7dbd-2e86-43f9-9377-3b75053203b3
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: Security
content-type: reference
discoiquuid: 6ae57874-a9a1-4208-9001-7f44a1f57cbe
docset: aem65
translation-type: tm+mt
source-git-commit: 29328ff7fde4ed0e7f9728af1be911133259dc6c
workflow-type: tm+mt
source-wordcount: '808'
ht-degree: 0%

---


# Een gesloten gebruikersgroep maken{#creating-a-closed-user-group}

Gesloten gebruikersgroepen (CUG&#39;s) worden gebruikt om de toegang tot specifieke pagina&#39;s op een gepubliceerde website te beperken. Dergelijke pagina&#39;s vereisen de toegewezen leden login en verstrekken veiligheidsgeloofsbrieven.

U configureert een dergelijk gebied binnen uw website als volgt:

* [Maak de werkelijke gesloten gebruikersgroep en wijs leden](#creating-the-user-group-to-be-used) toe.

* [past deze groep toe op de vereiste ](#applying-your-closed-user-group-to-content-pages) pagina&#39;s en selecteert (of creeert) de login pagina voor gebruik door de leden van CUG; ook opgegeven bij het toepassen van een CUG op een inhoudspagina.

* [Maak een koppeling van een of andere vorm naar ten minste één pagina in het beschermde gebied](#linking-to-the-realm), anders is deze koppeling niet zichtbaar.
* [Configureer de ](#configure-dispatcher-for-cugs) Dispatcherif in gebruik.

>[!CAUTION]
>
>Gesloten gebruikersgroepen (CUG&#39;s) moeten altijd worden gemaakt met het oog op prestaties.
>
>Hoewel het aantal gebruikers en groepen in een CUG niet beperkt is, kan een hoog aantal CUG&#39;s op een pagina de renderprestaties vertragen.
>
>Bij het testen van de prestaties moet altijd rekening worden gehouden met het effect van CUG&#39;s.

## Het creëren van de te gebruiken Gebruikersgroep {#creating-the-user-group-to-be-used}

Een gesloten gebruikersgroep maken:

1. Ga naar **Gereedschappen - Beveiliging** vanaf het AEM introductiescherm.

   >[!NOTE]
   >
   >Zie [Gebruikers en groepen beheren](/help/sites-administering/security.md#managing-users-and-groups) voor volledige informatie over het maken en configureren van gebruikers en groepen.

1. Selecteer de **Groepen** kaart van het volgende scherm.

   ![screenshot_2018-10-30at145502](assets/screenshot_2018-10-30at145502.png)

1. Druk op de knop **Maken** in de rechterbovenhoek om een nieuwe groep te maken.
1. Geef de nieuwe groep een naam; bijvoorbeeld `cug_access`.

   ![screenshot_2018-10-30at151459](assets/screenshot_2018-10-30at151459.png)

1. Ga naar het tabblad **Leden** en wijs de vereiste gebruikers toe aan deze groep.

   ![screenshot_2018-10-30at151808](assets/screenshot_2018-10-30at151808.png)

1. Activeer om het even welke gebruikers die u aan uw CUG hebt toegewezen; in dit geval, alle leden van `cug_access`.
1. Activeer de gesloten gebruikersgroep zodat deze beschikbaar is in de publicatieomgeving; in dit voorbeeld, `cug_access`.

## De gesloten gebruikersgroep toepassen op inhoudspagina&#39;s {#applying-your-closed-user-group-to-content-pages}

De CUG toepassen op een pagina:

1. Navigeer naar de basispagina van de beperkte sectie die u aan uw CUG wilt toewijzen.
1. Selecteer de pagina door op de bijbehorende miniatuur te klikken en vervolgens op **Eigenschappen** in het bovenste deelvenster te klikken.

   ![screenshot_2018-10-30at162632](assets/screenshot_2018-10-30at162632.png)

1. Ga in het volgende venster naar het tabblad **Geavanceerd**.
1. Schuif omlaag en schakel het selectievakje in de sectie **Verificatievereiste** in.

1. Voeg hieronder uw configuratiepad toe en druk op Opslaan.
1. Ga vervolgens naar het tabblad **Machtigingen** en druk op de knop **Gesloten gebruikersgroep bewerken**.

   ![screenshot_2018-10-30at163003](assets/screenshot_2018-10-30at163003.png)

   >[OPMERKING!]
   >
   > CUG&#39;s op het tabblad Machtigingen kunnen niet worden teruggedraaid van Blauwdrukken naar Actieve kopieën. Plan dit probleem bij het configureren van Live Copy.
   >
   > Zie [deze pagina](closed-user-groups.md#aem-livecopy) voor meer informatie.

1. Zoek naar en voeg uw KUG in het volgende venster toe - in dit geval voeg de groep genoemd **cug_access** toe. Tot slot druk **sparen**.
1. Klik **Ingeschakeld** om te definiëren dat deze pagina (en eventuele onderliggende pagina&#39;s) tot een CUG behoren.
1. Geef de **Aanmeldingspagina** op die leden van de groep zullen gebruiken; bijvoorbeeld:

   `/content/geometrixx/en/toolbar/login.html`

   Dit is optioneel. Als de standaardaanmeldingspagina leeg blijft, wordt deze gebruikt.

1. Voeg **Toegestane Groepen** toe. Gebruik + om groepen toe te voegen of - om te verwijderen. Alleen leden van deze groepen mogen zich aanmelden en toegang krijgen tot de pagina&#39;s.
1. Wijs indien nodig een **Realm** (een naam voor de paginagroepen) toe. Laat leeg als u de paginatitel wilt gebruiken.
1. Klik **OK** om de specificatie op te slaan.

Zie [Identity Management](/help/sites-administering/identity-management.md) voor informatie over profielen in het publicatiemilieu en het verstrekken van vormen voor het programma openen en uit.

## Koppeling met de realiteit {#linking-to-the-realm}

Aangezien het doel van koppelingen naar CUG Realm niet zichtbaar is voor de anonieme gebruiker, verwijdert de koppelingencontrole dergelijke koppelingen.

Om dit te voorkomen, is het aan te raden om niet-beveiligde omleidingspagina&#39;s te maken die verwijzen naar pagina&#39;s in de CUG Realm. De navigatie-items worden vervolgens gerenderd zonder dat de koppelingencontrole problemen ondervindt. Alleen wanneer de gebruiker de omleidingspagina daadwerkelijk opent, wordt de gebruiker omgeleid in de CUG Realm - nadat hij of zij zijn of haar aanmeldingsgegevens heeft opgegeven.

## Dispatcher configureren voor CUG&#39;s {#configure-dispatcher-for-cugs}

Als u Dispatcher gebruikt, moet u een landbouwbedrijf van de Verzender met de volgende eigenschappen bepalen:

* [virtuele hosts](https://helpx.adobe.com/experience-manager/dispatcher/using/dispatcher-configuration.html#identifying-virtual-hosts-virtualhosts): Komt overeen met het pad naar de pagina&#39;s waarop de CUG van toepassing is.
* \sessionmanagement: zie hieronder.
* [cache](https://helpx.adobe.com/experience-manager/dispatcher/using/dispatcher-configuration.html#configuring-the-dispatcher-cache-cache): Een cachemap die is toegewezen aan de bestanden waarop de CUG van toepassing is.

### Het vormen het Beheer van de Zitting van de Ontvanger voor CUGs {#configuring-dispatcher-session-management-for-cugs}

Configureer [sessiebeheer in de dispatcher.any file](https://helpx.adobe.com/experience-manager/dispatcher/using/dispatcher-configuration.html#enabling-secure-sessions-sessionmanagement) voor de CUG. De authentificatiemanager die wordt gebruikt wanneer de toegang voor de pagina&#39;s van de CUG wordt gevraagd bepaalt hoe u zittingsbeheer vormt.

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

1. [/sessionmanagement](https://helpx.adobe.com/experience-manager/dispatcher/using/dispatcher-configuration.html#enabling-secure-sessions-sessionmanagement) configureren door `/directory` te definiëren; bijvoorbeeld:

   ```xml
   /sessionmanagement
     {
     /directory "/usr/local/apache/.sessions"
     ...
     }
   ```

1. Stel [/allowAuthorized](https://helpx.adobe.com/experience-manager/dispatcher/using/dispatcher-configuration.html#caching-when-authentication-is-used) in op `0`.

