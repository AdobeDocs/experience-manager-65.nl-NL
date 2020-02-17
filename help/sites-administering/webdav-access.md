---
title: WebDAV-toegang
seo-title: WebDAV-toegang
description: Meer informatie over WebDAV-toegang in AEM.
seo-description: Meer informatie over WebDAV-toegang in AEM.
uuid: b0ecaa5d-5454-42df-8453-404ece734c32
contentOwner: Chiradeep Majumdar
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: content
content-type: reference
discoiquuid: 1eaf7afe-a181-45df-8766-bd564b1ad22a
translation-type: tm+mt
source-git-commit: 1c1ade947f2cbd26b35920cfd10b1666b132bcbd

---


# WebDAV-toegang{#webdav-access}

Verbinding maken met AEM via WebDAV met KDE:

AEM biedt WebDAV-ondersteuning waarmee u inhoud in opslagruimten kunt weergeven en bewerken. Verbinding maken via WebDAV geeft u rechtstreeks via uw bureaublad toegang tot de opslagplaats voor inhoud. Tekst- en PDF-bestanden die via de WebDAV-verbinding aan de gegevensopslagruimte worden toegevoegd, worden automatisch met volledige tekst geïndexeerd en kunnen worden doorzocht met de standaard zoekinterfaces en via de standaard Java API&#39;s.

## Algemeen {#general}

[Gedetailleerde instructies per besturingssysteem](/help/sites-administering/webdav-access.md#connecting-via-webdav) zijn in dit document opgenomen, maar de inhoud van de instructies om via het WebDAV-protocol verbinding te maken met de opslagplaats, verwijst u naar de volgende locatie op de WebDAV-client:

```xml
http://localhost:4502
```

![chlimage_1-111](assets/chlimage_1-111a.png)

Deze URL biedt WebDAV toegang tot de standaardwerkruimte ( `crx.default`) wanneer deze wordt verbonden vanaf het niveau van het besturingssysteem. Hoewel het eenvoudiger is voor de gebruiker, biedt het hen niet de extra flexibiliteit om werkruimtenamen te specificeren, die kunnen worden verwezenlijkt gebruikend extra [WebDAV URLs](/help/sites-administering/webdav-access.md#webdav-urls).

AEM geeft de inhoud van de opslagplaats als volgt weer:

* Een knooppunt van het type `nt:folder` wordt weergegeven als een map. Knooppunten onder het `nt:folder` knooppunt worden weergegeven als de inhoud van de map.

* Een knooppunt van het type `nt:file` wordt weergegeven als een bestand. Knooppunten onder het `nt:file` knooppunt worden niet weergegeven, maar vormen de inhoud van het bestand.

Wanneer u WebDAV gebruikt om mappen en bestanden te maken en te bewerken, maakt en bewerkt AEM de benodigde `nt:folder` knooppunten en `nt:file` knooppunten. Als u WebDAV wilt gebruiken voor het importeren en exporteren van inhoud, moet u zoveel mogelijk met knooppunttypen `nt:file` en `nt:folder` knooppunttypen werken.

>[!NOTE]
>
>Controleer de [technische vereisten](/help/sites-deploying/technical-requirements.md#webdav-clients)voordat u WebDAV instelt.

## WebDAV-URL&#39;s {#webdav-urls}

De URL voor de WebDAV-server heeft de volgende structuur:

<table>
 <colgroup>
  <col width="100" />
  <col width="100" />
  <col width="100" />
  <col width="100" />
  <col width="100" />
 </colgroup>
 <tbody>
  <tr>
   <td>
    <code>
     <strong>URL Component</strong>
    </code></td>
   <td><code>https://&lt;host&gt;:&lt;port&gt;</code></td>
   <td><code>/&lt;crx-webapp-path&gt;</code></td>
   <td><code>/repository</code></td>
   <td><code>/&lt;workspace&gt;</code></td>
  </tr>
  <tr>
   <td>
    <code>
     <strong>Example</strong>
    </code></td>
   <td><code>http://localhost:4502</code></td>
   <td><code>/crx</code></td>
   <td><code>/repository</code></td>
   <td><code>/crx.default</code></td>
  </tr>
  <tr>
   <td><strong>Beschrijving</strong></td>
   <td>Host en poort waarop AEM wordt uitgevoerd</td>
   <td>Pad voor de webapp van de AEM-opslagplaats</td>
   <td>Pad waaraan WebDAV-servlet is toegewezen</td>
   <td>Naam van de werkruimte</td>
  </tr>
 </tbody>
</table>

Als u het element van de werkruimte in het pad wijzigt, kunt u andere werkruimten toewijzen dan de standaardwerkruimte ( `crx.default`). Als u bijvoorbeeld een werkruimte met de naam `staging`wilt toewijzen, gebruikt u de volgende URL:

```xml
http://localhost:4502/crx/repository/staging
```

## Verbinding maken via WebDAV {#connecting-via-webdav}

[Zoals hierboven](/help/sites-administering/webdav-access.md#general)is vermeld, wijst u uw WebDAV-client naar de locatie van de opslagplaats om verbinding te maken met uw opslagplaats via het WebDAV-protocol. Afhankelijk van uw besturingssysteem verschillen de stappen waarmee u verbinding maakt met uw client echter en is er mogelijk een configuratie van het vereiste besturingssysteem vereist.

Er zijn instructies voor het aansluiten van de volgende besturingssystemen:

* [Windows](/help/sites-administering/webdav-access.md#windows)
* [macOS](/help/sites-administering/webdav-access.md#macos)
* [Linux](/help/sites-administering/webdav-access.md#linux)

### Windows {#windows}

Als u een Microsoft Windows 7-systeem (en hoger) wilt verbinden met een AEM-instantie die niet is beveiligd met SSL, moet de optie voor het instellen van een basisverificatie via een onbeveiligd netwerk expliciet zijn ingeschakeld in Windows. Dit vereist een verandering in de Registratie van Vensters van WebClient.

Zodra het register wordt bijgewerkt, dan kan de instantie AEM als aandrijving worden in kaart gebracht.

#### Windows 7 en meer configuratie {#windows-and-greater-configuration}

Om de registratie bij te werken om basisauthentificatie over een onbeveiligd netwerk toe te staan:

1. Zoek de volgende registersubsleutel:

   ```xml
   HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\WebClient\Parameters
   ```

1. Stel de subsleutel voor de `BasicAuthLevel` registervermelding in op een waarde van `2` of hoger.

   Voeg de subsleutel toe als deze niet aanwezig is.

1. De registerwijziging treedt pas in werking als u het systeem opnieuw hebt gestart.

Zie [Microsoft Support KB 841215](https://support.microsoft.com/default.aspx/kb/841215) voor meer informatie over deze registerwijziging.

Zie [Microsoft Steun KB 2445570](https://support.microsoft.com/kb/2445570) voor informatie over het verbeteren van de verantwoordelijkheid van de Cliënt WebDav onder Vensters.

>[!NOTE]
>
>Adobe raadt u aan een Windows-gebruiker te maken met dezelfde referenties als de gebruiker in de opslagplaats, anders kunnen er machtigingsconflicten optreden.

#### Windows 8-configuratie {#windows-configuration}

Voor Windows 8 moet u ook de registervermelding wijzigen [zoals beschreven voor Windows 7 en hoger](/help/sites-administering/webdav-access.md#windows-and-greater-configuration). Nochtans, alvorens u dit kunt doen, moet de Ervaring van de Desktop worden toegelaten om de registratieingang te zien.

Om de Desktopervaring toe te laten, open de Manager **van de** Server, dan **Eigenschappen**, dan **voeg Eigenschappen** toe, dan de Ervaring **van de** Desktop.

Na het rebooten van de registratieingang die voor Vensters 7 en groter wordt beschreven is beschikbaar. Wijzig het zoals die voor Vensters 7 en groter wordt beschreven.

#### Verbinding maken in Windows {#connecting-in-windows}

Verbinding maken met AEM via WebDAV in een Windows-omgeving:

1. Open **Windows Verkenner** of de Ontdekkingsreiziger **van het** Dossier en klik op **Computer** of **Deze PC**.

   ![chlimage_1-112](assets/chlimage_1-112a.png)

1. Klik op **Netwerkstation** toewijzen om de wizard te starten.
1. Voer de toewijzingsdetails in:

   * **Station**: Kies een beschikbare letter
   * **Map**: `http://localhost:4502`
   * Controleer **Connect met verschillende referenties.**
   Klik op Voltooien

   ![chlimage_1-113](assets/chlimage_1-113a.png)

   >[!NOTE]
   >
   >Als AEM op een andere haven wordt gevestigd, gebruik dat havenaantal in plaats van 4502. Als u de opslagplaats voor inhoud niet op uw lokale computer uitvoert, vervangt u deze door `localhost` de respectievelijke servernaam of het IP-adres.

1. Voer gebruikersnaam `admin` en wachtwoord in `admin`. Adobe raadt u aan de vooraf geconfigureerde beheeraccount te gebruiken voor tests.

   ![chlimage_1-114](assets/chlimage_1-114a.png)

1. De wizard wordt gesloten en de nieuw toegewezen schijf wordt geopend in Windows Verkenner of het venster Bestandverkenner.

   ![chlimage_1-115](assets/chlimage_1-115a.png)

Windows heeft AEM nu toegewezen als een station via WebDAV en u kunt deze als elk ander station gebruiken.

### macOS {#macos}

Er zijn geen configuratiestappen vereist om via WebDAV verbinding te maken op MacOS. U hoeft alleen maar verbinding te maken met de WebDAV-server.

1. Navigeer naar een willekeurig **Finder** -venster en klik op **Ga** en **Verbind met server** of druk op **Command+k**.
1. Voer in het venster **Verbinding maken met server** de AEM-locatie in:

   * `http://localhost:4502`
   >[!NOTE]
   >
   >Als AEM op een andere haven wordt gevestigd, gebruik dat havenaantal in plaats van 4502. Als u de opslagplaats voor inhoud niet op uw lokale computer uitvoert, vervangt u deze door `localhost` de respectievelijke servernaam of het IP-adres.

1. Wanneer u voor authentificatie wordt veroorzaakt, ga gebruikersbenaming `admin` en wachtwoord in `admin`. Adobe raadt u aan de vooraf geconfigureerde beheeraccount te gebruiken voor tests.

macOS heeft nu verbinding met AEM via WebDAV en u kunt deze gebruiken als elke andere map op de Mac.

### Linux {#linux}

Voor verbinding via WebDAV op Linux is geen configuratie vereist, maar het omvat wel een paar stappen om de verbinding tot stand te brengen die afhankelijk is van uw desktopomgeving.

#### GNOME {#gnome}

Verbinding maken met AEM via WebDAV met GNOME:

1. Selecteer **Plaatsen** in Nautilus (bestandsverkenner) en selecteer **Verbinding maken met server**.
1. Selecteer WebDAV (HTTP) bij Servicetype in het venster **Verbinding maken met server** .

1. Voer in **Server**`http://localhost:4502/crx/repository/crx.default`

   >[!NOTE]
   >
   >Als AEM op een andere haven wordt gevestigd, gebruik dat havenaantal in plaats van 4502. Als u de opslagplaats voor inhoud niet op uw lokale computer uitvoert, vervangt u deze door `localhost` de respectievelijke servernaam of het IP-adres.

1. Voer in **map**`/dav`
1. Voer de gebruikersnaam in `admin`. Adobe raadt u aan de vooraf geconfigureerde beheeraccount te gebruiken voor tests.
1. Laat de poort leeg en voer een naam voor de verbinding in.
1. Klik op **Verbinden**. AEM vraagt om uw wachtwoord.
1. Voer het wachtwoord in `admin` en klik op **Verbinden**.

GNOME heeft nu AEM als een volume gemonteerd en u kunt het als elk ander volume gebruiken.

#### KDE {#kde}

1. Open de wizard Netwerkmap.
1. Selecteer **WebFolder**(webdav) en klik daarna.
1. Typ in **Naam** een naam voor de verbinding.
1. Voer in **Gebruiker** het advies in van `admin.` Adobe om de vooraf geconfigureerde beheerdersaccount te gebruiken.
1. Voer in **Server**`http://localhost:4502/crx/repository/crx.default`

   >[!NOTE]
   >
   >Als AEM op een andere haven wordt gevestigd, gebruik dat havenaantal in plaats van 4502. Als u de opslagplaats voor inhoud niet op uw lokale computer uitvoert, vervangt u deze door `localhost` de respectievelijke servernaam of het IP-adres

1. Voer in **map**`dav`

1. Klik op **Opslaan en Verbinden**.
1. Voer het wachtwoord in als u hierom wordt gevraagd `admin` en klik op **Verbinden**.

KDE heeft nu AEM als een volume gemonteerd en u kunt het als elk ander volume gebruiken.
