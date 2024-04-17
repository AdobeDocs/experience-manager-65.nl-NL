---
title: WebDAV-toegang
description: Leer hoe u toegang krijgt tot Adobe Experience Manager met WebDAV.
contentOwner: Chiradeep Majumdar
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: content
content-type: reference
exl-id: 891ee66c-e49c-4561-8fef-e6e448a8aa1c
solution: Experience Manager, Experience Manager Sites
feature: Administering
role: Admin
source-git-commit: 66db4b0b5106617c534b6e1bf428a3057f2c2708
workflow-type: tm+mt
source-wordcount: '1118'
ht-degree: 0%

---

# WebDAV-toegang{#webdav-access}

Verbinding maken met AEM via WebDAV met KDE:

AEM biedt WebDAV-ondersteuning waarmee u inhoud in de opslagplaats kunt weergeven en bewerken. Verbinding maken via WebDAV geeft u rechtstreeks via uw bureaublad toegang tot de opslagplaats voor inhoud. Tekst- en PDF-bestanden die via de WebDAV-verbinding aan de opslagplaats worden toegevoegd, worden automatisch geïndexeerd met volledige tekst en kunnen worden gezocht met de standaardzoekinterfaces en met de standaard Java™ API&#39;s.

## Algemeen {#general}

[Gedetailleerde instructies per besturingssysteem](/help/sites-administering/webdav-access.md#connecting-via-webdav) zijn opgenomen in dit document, maar u kunt de WebDAV-client in feite via het WebDAV-protocol verbinden met uw gegevensopslagruimte door naar de volgende locatie te verwijzen:

```xml
http://localhost:4502
```

![chlimage_1-111](assets/chlimage_1-111a.png)

Deze URL biedt WebDAV toegang tot de standaardwerkruimte ( `crx.default`). Hoewel het eenvoudiger is voor de gebruiker, biedt het hen niet de extra flexibiliteit om werkruimtenamen te specificeren, die kunnen worden verwezenlijkt gebruikend extra [WebDAV-URL&#39;s](/help/sites-administering/webdav-access.md#webdav-urls).

AEM geeft de inhoud van de opslagplaats als volgt weer:

* Een knooppunt van het type `nt:folder` wordt weergegeven als een map. Knooppunten onder de knop `nt:folder` knooppunten worden weergegeven als de inhoud van de map.

* Een knooppunt van het type `nt:file` wordt weergegeven als een bestand. Knooppunten onder de knop `nt:file` wordt niet weergegeven, maar vormt de inhoud van het bestand.

Wanneer u WebDAV gebruikt om mappen en bestanden te maken en te bewerken, AEM maakt en bewerkt u de vereiste `nt:folder` en `nt:file` knooppunten. Als u WebDAV wilt gebruiken voor het importeren en exporteren van inhoud, moet u proberen te werken met `nt:file` en `nt:folder` knooppunttypes zoveel mogelijk.

>[!NOTE]
>
>Controleer voordat u WebDAV instelt het [Technische vereisten](/help/sites-deploying/technical-requirements.md#webdav-clients).

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
   <td>Pad voor de webapp van de AEM repository</td>
   <td>Pad waaraan WebDAV-servlet is toegewezen</td>
   <td>Naam van de werkruimte</td>
  </tr>
 </tbody>
</table>

Als u het werkruimte-element in het pad wijzigt, kunt u andere werkruimten toewijzen dan de standaardwerkruimte ( `crx.default`). Als u bijvoorbeeld een werkruimte met de naam `staging`en gebruikt u de volgende URL:

```xml
http://localhost:4502/crx/repository/staging
```

## Verbinding maken via WebDAV {#connecting-via-webdav}

[Zoals hierboven vermeld](/help/sites-administering/webdav-access.md#general)Als u verbinding wilt maken met de opslagplaats via het WebDAV-protocol, wijst u uw WebDAV-client naar de opslagplaats. Afhankelijk van uw besturingssysteem verschillen de stappen voor het aansluiten van uw client echter en is er mogelijk een vereiste configuratie van het besturingssysteem vereist.

Instructies voor het aansluiten van de volgende besturingssystemen zijn beschikbaar:

* [Windows](/help/sites-administering/webdav-access.md#windows)
* [macOS](/help/sites-administering/webdav-access.md#macos)
* [Linux](/help/sites-administering/webdav-access.md#linux)

### Windows {#windows}

Als u een Microsoft® Windows 7 (en hoger)-systeem wilt verbinden met een AEM die niet met SSL is beveiligd, moet de optie voor het instellen van een basisverificatie via een onbeveiligd netwerk expliciet zijn ingeschakeld in Windows. Deze capaciteit vereist een verandering in de Registratie van Vensters van WebClient.

Zodra de registratie wordt bijgewerkt, dan kan de AEM instantie als aandrijving worden in kaart gebracht.

#### Windows 7 en meer configuratie {#windows-and-greater-configuration}

Om de registratie bij te werken om basisauthentificatie over een onbeveiligd netwerk toe te staan:

1. Zoek de volgende registersubsleutel:

   ```xml
   HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\WebClient\Parameters
   ```

1. Stel de `BasicAuthLevel` registerentry-subkey voor een waarde van `2` of hoger.

   Voeg de subsleutel toe als deze niet aanwezig is.

1. Start het systeem opnieuw zodat de registerwijziging van kracht wordt.

>[!NOTE]
>
>Adobe raadt u aan een Windows-gebruiker te maken met dezelfde referenties als de gebruiker in de opslagplaats, anders kunnen er machtigingsconflicten optreden.

#### Windows 8-configuratie {#windows-configuration}

Voor Windows 8 wijzigt u de registervermelding [zoals beschreven in Windows 7 en hoger](/help/sites-administering/webdav-access.md#windows-and-greater-configuration). Nochtans, alvorens u deze taak doet, moet de Ervaring van de Desktop worden toegelaten om de registratieingang te zien.

Als u de desktopervaring wilt inschakelen, opent u **Serverbeheer** vervolgens **Functies** vervolgens **Functies toevoegen** vervolgens **Desktopbeleving**.

Na rebooting, is de registratieingang die voor Vensters 7 en groter wordt beschreven beschikbaar. Wijzig het zoals die voor Vensters 7 en groter wordt beschreven.

#### Verbinding maken in Windows {#connecting-in-windows}

Verbinding maken met AEM via WebDAV in een Windows-omgeving:

1. Openen **Windows Verkenner** of **Bestandsverkenner** en klik op **Computer** of **Deze pc**.

   ![chlimage_1-112](assets/chlimage_1-112a.png)

1. Klik op **Kaartnetwerkstation**.
1. Voer de toewijzingsdetails in:

   * **Drive**: Kies een beschikbare letter
   * **Map**: `http://localhost:4502`
   * Controleren **Verbinding maken met verschillende referenties**

   Klik op Voltooien

   ![chlimage_1-113](assets/chlimage_1-113a.png)

   >[!NOTE]
   >
   >Als AEM zich op een andere poort bevindt, gebruikt u dat poortnummer in plaats van 4502. Als u de opslagplaats voor inhoud niet op uw lokale computer uitvoert, vervangt u `localhost` met de respectieve servernaam of IP adres.

1. Gebruikersnaam invoeren `admin` en wachtwoord `admin`. Adobe raadt u aan de vooraf geconfigureerde beheerdersaccount te gebruiken voor het testen.

   ![chlimage_1-114](assets/chlimage_1-114a.png)

1. De wizard wordt gesloten en het nieuwe toegewezen station wordt geopend in Windows Verkenner of het venster Bestandverkenner.

   ![chlimage_1-115](assets/chlimage_1-115a.png)

Windows heeft nu AEM toegewezen als een station via WebDAV en u kunt deze als elk ander station gebruiken.

### macOS {#macos}

Er zijn geen configuratiestappen vereist om via WebDAV verbinding te maken op macOS. U kunt verbinding maken met de WebDAV-server.

1. Naar een willekeurige locatie navigeren **Finder** venster en klik op **Ga** en **Verbinding maken met server**, of druk op **Command+k**.
1. In de **Verbinding maken met server** Voer de AEM in:

   * `http://localhost:4502`

   >[!NOTE]
   >
   >Als AEM zich op een andere poort bevindt, gebruikt u dat poortnummer in plaats van 4502. Als u de opslagplaats voor inhoud niet op uw lokale computer uitvoert, vervangt u `localhost` met de respectieve servernaam of IP adres.

1. Wanneer u wordt gevraagd om verificatie, voert u gebruikersnaam in `admin` en wachtwoord `admin`. Adobe raadt u aan de vooraf geconfigureerde beheerdersaccount te gebruiken voor het testen.

macOS heeft nu verbinding met AEM via WebDAV en u kunt deze gebruiken als elke andere map op uw Mac.

### Linux® {#linux}

Voor verbinding via WebDAV op Linux® is geen configuratie vereist, maar het omvat wel een paar stappen om de verbinding tot stand te brengen die afhankelijk is van uw desktopomgeving.

#### GNOME {#gnome}

Verbinding maken met AEM via WebDAV met GNOME:

1. Selecteer in Nautilus (bestandsverkenner) de optie **Plaatsen** en selecteert u **Verbinding maken met server**.
1. In de **Verbinding maken met server** Selecteer WebDAV (HTTP) in Servicetype.

1. In **Server**, enter `http://localhost:4502/crx/repository/crx.default`

   >[!NOTE]
   >
   >Als AEM zich op een andere poort bevindt, gebruikt u dat poortnummer in plaats van 4502. Als u de opslagplaats voor inhoud niet op uw lokale computer uitvoert, vervangt u `localhost` met de respectieve servernaam of IP adres.

1. In **Map**, enter `/dav`
1. Voer de gebruikersnaam in `admin`. Adobe raadt u aan de vooraf geconfigureerde beheerdersaccount te gebruiken voor het testen.
1. Laat de poort leeg en voer een naam voor de verbinding in.
1. Klikken **Verbinden**. AEM vraagt u om uw wachtwoord.
1. Voer het wachtwoord in `admin` en klik op **Verbinden**.

GNOME heeft nu AEM gemonteerd als een volume en u kunt het gebruiken als elk ander volume.

#### KDE {#kde}

1. Open de wizard Netwerkmap.
1. Selecteren **WebFolder**(webdav) en klik op Volgende.
1. In **Naam**, typt u een naam voor de verbinding.
1. In **Gebruiker**, enter `admin.` Adobe raadt u aan de vooraf geconfigureerde beheerdersaccount te gebruiken.
1. In **Server**, enter `http://localhost:4502/crx/repository/crx.default`

   >[!NOTE]
   >
   >Als AEM zich op een andere poort bevindt, gebruikt u dat poortnummer in plaats van 4502. Als u de opslagplaats voor inhoud niet op uw lokale computer uitvoert, vervangt u `localhost` met de respectieve servernaam of IP adres

1. In **Map**, enter `dav`

1. Klikken **Opslaan en verbinden**.
1. Voer het wachtwoord in wanneer u hierom wordt gevraagd `admin` en klik op **Verbinden**.

KDE heeft nu AEM gemonteerd als een volume en u kunt het als elk ander volume gebruiken.
