---
title: Behandeling van GDPR-verzoeken voor de AEM Foundation
seo-title: Behandeling van GDPR-verzoeken voor de AEM Foundation
description: 'null'
seo-description: 'null'
uuid: d470061c-bbcf-4d86-9ce3-6f24a764ca39
contentOwner: sarchiz
discoiquuid: 8ee843b6-8cea-45fc-be6c-99c043f075d4
translation-type: tm+mt
source-git-commit: 85a3dac5db940b81da9e74902a6aa475ec8f1780

---


# Behandeling van GDPR-verzoeken voor de AEM Foundation{#handling-gdpr-requests-for-the-aem-foundation}

>[!IMPORTANT]
>
>GDPR wordt in de onderstaande secties als voorbeeld gebruikt, maar de betreffende details zijn van toepassing op alle regels inzake gegevensbescherming en privacy; zoals GDPR, CCPA enz.

## GDPR-ondersteuning van AEM Foundation {#aem-foundation-gdpr-support}

Op het niveau van de Stichting AEM, zijn de Persoonlijke Gegevens die wordt opgeslagen het Profiel van de Gebruiker. Daarom richt de informatie in dit artikel hoofdzakelijk hoe te om tot gebruikersprofielen toegang te hebben en te schrappen, om de verzoeken van de Toegang te richten GDPR en van de Schrapping respectievelijk.

## Een gebruikersprofiel openen {#accessing-a-user-profile}

### Handmatige stappen {#manual-steps}

1. Open de gebruikersbeheerconsole door naar **[!UICONTROL Instellingen - Beveiliging - Gebruikers]** te bladeren of door rechtstreeks naar `https://<serveraddress>:<serverport>/libs/granite/security/content/useradmin.html`

   ![useradmin2](assets/useradmin2.png)

1. Zoek vervolgens naar de desbetreffende gebruiker door de naam in de zoekbalk boven aan de pagina te typen:

   ![gebruikerszoekopdracht](assets/usersearch.png)

1. Tot slot open het gebruikersprofiel door het te klikken, dan controle onder het lusje van **[!UICONTROL Details]** .

   ![userprofile_small](assets/userprofile_small.png)

### HTTP-API {#http-api}

Zoals vermeld, verstrekt Adobe APIs voor de toegang tot van gebruikersgegevens, om automatisering te vergemakkelijken. Er zijn verschillende typen API&#39;s die u kunt gebruiken:

**UserProperties-API**

```shell
curl -u user:password http://localhost:4502/libs/granite/security/search/profile.userproperties.json\?authId\=cavery
```

**Verkopen-API**

*De startpagina van de gebruiker opzoeken:*

```xml
curl -g -u user:password 'http://localhost:4502/libs/granite/security/search/authorizables.json?query={"condition":[{"named":"cavery"}]}'
     {"authorizables":[{"type":"user","authorizableId_xss":"cavery","authorizableId":"cavery","name_xss":"Carlene Avery","name":"Carlene Avery","home":"/home/users/we-retail/DSCP-athB1NYLBXvdTuN"}],"total":1}
```

*Gebruikersgegevens ophalen*

Gebruikend de knoopweg van het huisbezit van de nuttige lading JSON die van het bovengenoemde bevel is teruggekeerd:

```shell
curl -u user:password  'http://localhost:4502/home/users/we-retail/DSCP-athB1NYLBXvdTuN/profile.-1.json'
```

```shell
curl -u user:password  'http://localhost:4502/home/users/we-retail/DSCP-athB1NYLBXvdTuN/profiles.-1.json'
```

## Een gebruiker uitschakelen en de bijbehorende profielen verwijderen {#disabling-a-user-and-deleting-the-associated-profiles}

### Gebruiker uitschakelen {#disable-user}

1. Open de console van het Beleid van de Gebruiker en onderzoek naar de gebruiker in kwestie, zoals hierboven beschreven.
1. Houd de muisaanwijzer boven de gebruiker en klik op het pictogram Selecteren. Het profiel wordt grijs om aan te geven dat het is geselecteerd.

1. Druk op de knop Uitschakelen in het bovenste menu om de gebruiker uit te schakelen:

   ![userdisable](assets/userdisable.png)

1. Bevestig ten slotte de actie:

   ![image2018-2-6_1-40-58](assets/image2018-2-6_1-40-58.png)

   De gebruikersinterface geeft vervolgens aan dat de gebruiker is gedeactiveerd door uit te graaien en een vergrendeling toe te voegen aan de profielkaart:

   ![gehandicapte gebruiker](assets/disableduser.png)

### Gebruikersprofielgegevens verwijderen {#delete-user-profile-information}

1. Meld u aan bij CRXDE Lite en zoek vervolgens naar de `[!UICONTROL userId]`:

   ![image2018-2-6_1-57-11](assets/image2018-2-6_1-57-11.png)

1. Open het gebruikersknooppunt onder `[!UICONTROL /home/users]` standaard:

   ![image2018-2-6_1-58-25](assets/image2018-2-6_1-58-25.png)

1. Verwijder profielknooppunten en alle onderliggende knooppunten. Afhankelijk van de AEM-versie zijn er twee indelingen voor de profielknooppunten:

   1. Het standaard privéprofiel onder `[!UICONTROL /profile]`
   1. `[!UICONTROL /profiles]`, voor nieuwe profielen die zijn gemaakt met AEM 6.5.
   ![image2018-2-6_2-0-4](assets/image2018-2-6_2-0-4.png)

### HTTP-API {#http-api-1}

De volgende procedures gebruiken het hulpmiddel van de `curl` bevellijn om te illustreren hoe te om de gebruiker met de **[!UICONTROL kavery]** `userId` onbruikbaar te maken en haar profielen te schrappen beschikbaar bij de standaardplaats.

* *De startpagina van de gebruiker opzoeken*

```shell
curl -g -u user:password 'http://localhost:4502/libs/granite/security/search/authorizables.json?query={"condition":[{"named":"cavery"}]}'
     {"authorizables":[{"type":"user","authorizableId_xss":"cavery","authorizableId":"cavery","name_xss":"Carlene Avery","name":"Carlene Avery","home":"/home/users/we-retail/DSCP-athB1NYLBXvdTuN"}],"total":1}
```

* *De gebruiker uitschakelen*

Gebruikend de knoopweg van het huisbezit van de nuttige lading JSON die van het bovengenoemde bevel is teruggekeerd:

```shell
curl -X POST -u user:password -FdisableUser="describe the reasons for disabling this user (GDPR in this case)" 'http://localhost:4502/home/users/we-retail/DSCP-athB1NYLBXvdTuN.rw.userprops.html'
```

* *Gebruikersprofiel(en) verwijderen*

Het gebruiken van de knoopweg van het huisbezit van de nuttige lading JSON die van het bevel van de rekeningsontdekking en het gekende uit de knoopplaatsen van het kaderprofiel is teruggekeerd:

```shell
curl -X POST -u user:password -H "Accept: application/json,**/**;q=0.9" -d ':operation=delete' 'http://localhost:4502/home/users/we-retail/DSCP-athB1NYLBXvdTuN/profile'
```

```shell
curl -X POST -u user:password -H "Accept: application/json,**/**;q=0.9" -d ':operation=delete' 'http://localhost:4502/home/users/we-retail/DSCP-athB1NYLBXvdTuN/profile'
```

