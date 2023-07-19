---
title: Ontwikkelen met CRXDE Lite
seo-title: Developing with CRXDE Lite
description: CRXDE Lite is ingebed in AEM en laat u toe om standaardontwikkelingstaken in browser uit te voeren
seo-description: CRXDE Lite is embedded into AEM and enables you to perform standard development tasks in the browser
uuid: f4890354-d8b8-4fb9-af2f-3359f931f883
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: development-tools
content-type: reference
discoiquuid: 4537c1fb-f99c-42e2-a222-b037794bdb52
docset: aem65
exl-id: 9e88ca55-ac3d-4857-b6b2-aeb732562664
source-git-commit: 259f257964829b65bb71b5a46583997581a91a4e
workflow-type: tm+mt
source-wordcount: '2139'
ht-degree: 0%

---

# Ontwikkelen met CRXDE Lite{#developing-with-crxde-lite}

In deze sectie wordt beschreven hoe u uw AEM toepassing kunt ontwikkelen met behulp van CRXDE Lite.

Raadpleeg de overzichtsdocumentatie voor meer informatie over de verschillende ontwikkelomgevingen die beschikbaar zijn.

CRXDE Lite is ingebed in AEM en laat u toe om standaardontwikkelingstaken in browser uit te voeren. Met CRXDE Lite kunt u een project maken, bestanden (zoals .jsp en .java), mappen, sjablonen, componenten, dialoogvensters, knooppunten, eigenschappen en bundels maken en bewerken tijdens het vastleggen.
CRXDE Lite wordt aanbevolen wanneer u geen directe toegang hebt tot de AEM server, wanneer u een toepassing ontwikkelt door de componenten en Java-bundels die buiten de box vallen uit te breiden of te wijzigen of wanneer u geen speciale debugger, codevoltooiing en syntaxismarkering nodig hebt.

>[!NOTE]
>
>Vanaf AEM 6.5.5.0 is anonieme toegang tot CRXDE Lite niet meer mogelijk.
>Gebruikers worden omgeleid naar het aanmeldingsscherm.


>[!NOTE]
>
>Het wordt aanbevolen om de [AEM Developer Tools for Eclipse](/help/sites-developing/aem-eclipse.md) en de [AEM extensie HTML-haakjes](/help/sites-developing/aem-brackets.md) tijdens de projectontwikkeling.

## Aan de slag met CRXDE Lite {#getting-started-with-crxde-lite}

Ga als volgt te werk om aan de slag te gaan met CRXDE Lite:

1. AEM installeren.
1. Voer in uw browser `https://<host>:<port>/crx/de`. Standaard is dit `https://localhost:4502/crx/de`.
1. Voer uw **gebruikersnaam** en **password**. Standaard is dit `admin` en `admin`.

1. Klikken **OK**.

De gebruikersinterface van CRXDE Lite ziet er als volgt uit in uw browser:

![chlimage_1-18](assets/crx-interface.jpg)

U kunt nu CRXDE Lite gebruiken om uw toepassing te ontwikkelen.

## Overzicht van de gebruikersinterface {#overview-of-the-user-interface}

CRXDE Lite biedt de volgende functionaliteit:

<table>
 <tbody>
  <tr>
   <td>Bovenste schakelbalk</td>
   <td>Staat u toe om tussen CRXDE Lite, de Manager van het Pakket, en het Aandeel van het Pakket snel te schakelen.</td>
  </tr>
  <tr>
   <td>Knooppuntwidget</td>
   <td><p>Geeft het pad naar het momenteel geselecteerde knooppunt weer.</p> <p>U kunt het ook gebruiken om aan een knoop te springen, door de weg door hand in te gaan, of het te kleven van ergens anders, en het drukken gaat binnen.</p> <p>Het biedt ook ondersteuning voor het zoeken naar knooppunten met een specifieke knooppuntnaam. Voer de naam in van het knooppunt dat u wilt zoeken en wacht (of druk op het zoeksymbool aan de rechterkant). U kunt bijvoorbeeld proberen de tekenreeks in te voeren <em>eik</em> in de widget om te zien hoe deze werkt. Als een bepaald knooppunt of bepaalde knooppunten in het verkennervenster wordt geladen, wordt de lijst weergegeven en kunt u het pad selecteren en op Enter drukken om naar het knooppunt te navigeren. Het werkt alleen voor de knooppunten die momenteel in de CRXDE-clienttoepassing in de browser zijn geladen. Als u de hele repository wilt doorzoeken, gebruikt u Extra en vervolgens Query.</p> </td>
  </tr>
  <tr>
   <td>Explorer-venster</td>
   <td><p>Toont een boom van alle knopen in de bewaarplaats.</p> <p>Klik op een knooppunt om de eigenschappen ervan weer te geven in het dialoogvenster <strong>Eigenschappen</strong> tab. Nadat u op een knooppunt hebt geklikt, kunt u een handeling op de werkbalk selecteren. Klik nogmaals op het knooppunt om de naam ervan te wijzigen.</p> <p>Navigatiefilter (binoculair pictogram): Hiermee kunt u de knooppunten in de opslagplaats filteren waarvoor de naam de invoertekst bevat. Het is alleen van toepassing op knooppunten die lokaal zijn geladen.<br /> </p> </td>
  </tr>
  <tr>
   <td>Venster Bewerken</td>
   <td><p><strong>Home</strong> tab: kunt u zoeken in inhoud en/of documentatie en toegang krijgen tot bronnen voor ontwikkelaars (documentatie, blog voor ontwikkelaars, kennisbasis) en ondersteuning (Adobe homepage en ondersteuningscentrum).<br /> </p> <p>Dubbelklik op een bestand in het dialoogvenster <strong>Verkenner</strong> de inhoud ervan weergeven; zoals bijvoorbeeld een .jsp- of een .java-bestand. U kunt het dan wijzigen en de veranderingen bewaren.</p> <p>Als een bestand eenmaal is bewerkt in het dialoogvenster <strong>Bewerken</strong> zijn de volgende gereedschappen beschikbaar op de werkbalk:<br /> </p> - <strong>Tonen in boomstructuur: </strong>geeft het bestand weer in de gegevensopslagstructuur.<br /> - <strong>Zoeken/vervangen...</strong>: zoeken of vervangen.<br /> <br /> Dubbelklik op de statusregel van het dialoogvenster <strong>Bewerken</strong> opent het deelvenster <strong>Ga naar regel</strong> zodat u een specifiek regelnummer kunt invoeren om naar te gaan.<br /> </td>
  </tr>
  <tr>
   <td>Eigenschappen, tabblad<br /> </td>
   <td>Geeft de eigenschappen weer van het knooppunt dat u hebt geselecteerd. U kunt nieuwe eigenschappen toevoegen of bestaande eigenschappen verwijderen.<br /> </td>
  </tr>
  <tr>
   <td>Het tabblad Toegangsbeheer</td>
   <td><p>Toon toestemmingen die op huidige weg, bewaarplaats-niveau of hoofd worden gebaseerd.</p> <p>De rechten worden opgesplitst in</p> <p>- <strong>Toepasselijk toegangsbeheerbeleid</strong>: Het beleid dat op de huidige selectie kan worden toegepast.</p> <p>- <strong>Beleid voor lokaal toegangsbeheer</strong>: Het huidige beleid dat lokaal op de huidige selectie wordt toegepast.</p> <p>- <strong>Effectief beleid voor toegangscontrole</strong>: Het huidige beleid dat voor de huidige selectie wordt toegepast, kan lokaal worden ingesteld of van bovenliggende knooppunten worden overgeërfd.</p> <p>Opmerking. Om de informatie van het Toegangsbeheer bij allen te kunnen zien, moet de gebruiker die aan CRXDE Lite wordt aangemeld rechten hebben om ACL ingangen te lezen. De anonieme gebruiker kan deze informatie standaard niet zien. Meld u aan als bijvoorbeeld beheerder om de informatie te bekijken.</p> </td>
  </tr>
  <tr>
   <td>Tabblad Replicatie</td>
   <td><p>Toon de replicatiestatus van huidige knoop. U kunt het huidige knooppunt repliceren en herhalen.</p> </td>
  </tr>
  <tr>
   <td>Het tabblad Console<br /> </td>
   <td><p><strong>Serverlogboeken</strong>:</p> <p>Hier worden logboekberichten weergegeven. U kunt het logboekniveau vormen, de console ontruimen, bij de geselecteerde rolpositie vastzetten en het tonen van berichten toelaten/onbruikbaar maken.<br /> </p> <p><strong>Versiebeheer</strong>:</p> <p>Geeft versiebeheerberichten weer.<br /> </p> </td>
  </tr>
  <tr>
   <td>Tabblad Informatie samenstellen<br /> </td>
   <td>Hiermee geeft u informatie weer wanneer een bundel wordt gemaakt.<br /> </td>
  </tr>
  <tr>
   <td>Vernieuwen<br /> </td>
   <td>Hiermee vernieuwt u de huidige selectie. Wijzigingen van andere gebruikers worden bijgewerkt in uw weergave van de opslagplaats. Wijzigingen die u hebt aangebracht, blijven ongewijzigd.<br /> </td>
  </tr>
  <tr>
   <td>Alles opslaan</td>
   <td><p><strong>Alles opslaan</strong>:<br /> </p> <p>Hiermee slaat u alle aangebrachte wijzigingen op. Totdat u op Opslaan klikt, zijn de wijzigingen tijdelijk en gaan deze verloren wanneer u de console afsluit.</p> <p><strong>Vorige versie</strong>:</p> <p>Hiermee worden alle wijzigingen genegeerd die u hebt aangebracht in het geselecteerde knooppunt sinds de laatste opslaghandeling en wordt vervolgens de huidige status van de opslagruimte voor het geselecteerde knooppunt opnieuw geladen.</p> <p><strong>Alles herstellen</strong>:</p> <p>Hiermee worden alle wijzigingen genegeerd die u hebt aangebracht in de gehele opslagplaats sinds de laatste opslaghandeling, en wordt vervolgens de huidige status van de opslagplaats opnieuw geladen.</p> </td>
  </tr>
  <tr>
   <td>Maken...<br /> </td>
   <td><p>Vervolgkeuzemenu voor het maken van het volgende onder het geselecteerde knooppunt:<br /> </p> <p>- <strong>Knooppunt</strong>: een knooppunt met een willekeurig knooppunttype<br /> </p> <p>- <strong>Bestand</strong>: nt:bestandnode en het bijbehorende nt:resource subnode</p> <p>- <strong>Map</strong>: nt:mapknooppunt</p> <p>- <strong>Sjabloon</strong>: AEM sjabloon</p> <p>- <strong>Component</strong>: AEM</p> <p>- <strong>Dialoog</strong>: Dialoogvenster AEM</p> </td>
  </tr>
  <tr>
   <td>Verwijderen<br /> </td>
   <td>Hiermee verwijdert u het geselecteerde knooppunt.<br /> </td>
  </tr>
  <tr>
   <td>Kopiëren</td>
   <td>Kopieert het geselecteerde knooppunt.<br /> </td>
  </tr>
  <tr>
   <td>Plakken<br /> </td>
   <td>Hiermee wordt het gekopieerde knooppunt onder het geselecteerde knooppunt geplakt.<br /> </td>
  </tr>
  <tr>
   <td>Verplaatsen...<br /> </td>
   <td>Hiermee verplaatst u het geselecteerde knooppunt naar het knooppunt dat via het dialoogvenster is ingesteld.</td>
  </tr>
  <tr>
   <td>Naam wijzigen...<br /> </td>
   <td>Wijzigt de naam van het geselecteerde knooppunt.<br /> </td>
  </tr>
  <tr>
   <td>Mengsels ...<br /> </td>
   <td>Hiermee kunt u mixingtypen toevoegen aan het knooppunttype. De mixintypes worden meestal gebruikt om geavanceerde eigenschappen zoals versioning, toegangsbeheer toe te voegen, van verwijzingen voorzien, en het sluiten aan de knoop.</td>
  </tr>
  <tr>
   <td>Gereedschappen<br /> </td>
   <td><p>Vervolgkeuzemenu met de volgende gereedschappen:</p> <p>- <strong>Serverconfiguratie...</strong>: om toegang te krijgen tot de Felix-console.</p> <p>- <strong>Query uitvoeren...</strong>: om een query uit te voeren op de repository.</p> <p>- <strong>Bevoegdheden ...</strong>: om het beheer van bevoegdheden te openen, waar u bevoegdheden kunt weergeven en toevoegen.</p> <p>- <strong>Toegangsbeheer testen...</strong>: een plaats waar u de toestemming voor bepaalde weg en/of hoofd kunt testen.</p> <p>- <strong>Notitietype exporteren</strong>: om knooppunttypes in het systeem als knoopaantekening uit te voeren.</p> <p>- <strong>Nodetype importeren...</strong>: om knooppunttypen te importeren met gebruik van codenotatie.</p> <p>- <strong>Foutopsporing SiteCatalyst installeren...</strong>: instructies voor het installeren van Analytics Debugger.</p> </td>
  </tr>
  <tr>
   <td>Aanmeldingswidget<br /> </td>
   <td><p>Toont momenteel het programma geopende gebruikers en de werkruimte zij, bijvoorbeeld, admin@crx.default worden geregistreerd.</p> <p>Klik op deze knop om u aan te melden of opnieuw aan te melden als specifieke gebruiker. Als u geen werkruimte specificeert om aan login aan te melden, zult u in de standaardwerkruimte, crx.default worden geregistreerd.</p> <p>Als u de repository wilt doorbladeren als anonieme gebruiker, gebruikt u <strong>anoniem</strong> als de aanmeldingsnaam en een wachtwoord (bijvoorbeeld een spatie of een punt).<br /> </p> <p>Als uw vergunning niet meer geldig is (bijvoorbeeld, is het verlopen), toont login widget "<strong>Onbevoegd - Aanmelden..</strong>". Klik hierop om u opnieuw aan te melden.</p> </td>
  </tr>
 </tbody>
</table>

## Een map maken {#creating-a-folder}

Een map met CRXDE Lite maken:

1. Open CRXDE Lite in uw browser.
1. Klik in het navigatievenster met de rechtermuisknop op de map waaronder u de nieuwe map wilt maken en selecteer **Maken...** vervolgens **Map maken...**.

1. Voer de map in **Naam** en klik op **OK**.

1. Klikken **Alles opslaan** om de wijzigingen op de server op te slaan.

## Een sjabloon maken {#creating-a-template}

Een sjabloon maken met CRXDE Lite:

1. Open CRXDE Lite in uw browser.
1. Klik in het navigatievenster met de rechtermuisknop op de map waar u de sjabloon wilt maken en selecteer **Maken...** vervolgens **Sjabloon maken...**.

1. Voer de **Label**, **Titel**, **Beschrijving**, **Type bron** en **Rangorde** van de template. Klik op **Next**.

1. Deze stap is optioneel: instellen **Toegestane paden**. Klik op **Next**

1. Deze stap is optioneel: instellen **Toegestane bovenliggende elementen**. Klik op **Next**.

1. Deze stap is optioneel: instellen **Toegestane kinderen**. Klikken **OK**.

1. Klikken **Alles opslaan** om de wijzigingen op de server op te slaan.

Het leidt tot:

* Een knooppunt van het type `cq:Template` met sjablooneigenschappen

* Een onderliggende node van het type `cq:PageContent` met eigenschappen voor Pagina-inhoud

U kunt eigenschappen aan uw sjabloon toevoegen: verwijzen naar de [Een eigenschap maken](#creating-a-property) sectie.

## Een component maken {#creating-a-component}

De hier beschreven functie is alleen beschikbaar als CQ5 is geïnstalleerd, dat wil zeggen als het knooppunttype `cq:Component` is beschikbaar in de repository.

Een component maken met CRXDE Lite:

1. Open CRXDE Lite in uw browser.
1. Klik in het navigatievenster met de rechtermuisknop op de map waar u de component wilt maken en selecteer **Maken...** vervolgens **Component maken...**.

1. Voer de **Label**, **Titel**, **Beschrijving**, **Type superbron** en **Groep** van de component. Klik op **Next**.

1. Deze stap is optioneel: componenteigenschappen instellen **is container,** **Geen decoratie**, **Celnaam** en **Dialoogpad**. Klik op **Next**.

1. Deze stap is optioneel: de componenteigenschap instellen **Toegestane bovenliggende elementen**. Klik op **Next**.

1. Deze stap is optioneel: de componenteigenschap instellen **Toegestane kinderen**. Klikken **OK**.

1. Klikken **Alles opslaan** om de wijzigingen op de server op te slaan.

Het leidt tot:

* Een knooppunt van het type `cq:Component`
* Componenteigenschappen
* Een .jsp-componentscript

## Een dialoogvenster maken {#creating-a-dialog}

Een dialoogvenster maken met CRXDE Lite:

1. Open CRXDE Lite in uw browser.
1. Klik in het navigatievenster met de rechtermuisknop op de component waar u het dialoogvenster wilt maken en selecteer **Maken...** vervolgens **Dialoogvenster maken...**.

1. Voer de **Label** en de **Titel**. Klikken **OK**.

1. Klikken **Alles opslaan** Om de wijzigingen op de server op te slaan.

Er wordt een dialoogvenster gemaakt met de volgende structuur:

`dialog[cq:Dialog]/items[cq:Widget]/items[cq:WidgetCollection]/tab1[cq:Panel]`

U kunt het dialoogvenster nu aan uw wensen aanpassen door eigenschappen te wijzigen of nieuwe knooppunten te maken.

U kunt een dialoogvenster ook bewerken met de Dialoogeditor. Als u dubbelklikt op het dialoogvenster in CRXDE Lite, wordt de editor weergegeven. Meer informatie over de Dialoogeditor vindt u [hier](/help/sites-developing/dialog-editor.md).

## Een knooppunt maken {#creating-a-node}

Een knooppunt maken met CRXDE Lite:

1. Open CRXDE Lite in uw browser.
1. Klik in het navigatievenster met de rechtermuisknop op het knooppunt waar u het nieuwe knooppunt wilt maken en selecteer **Maken...** vervolgens **Knooppunt maken...**.
1. Voer de **Naam** en de **Type**. Klikken **OK**.
1. Klikken **Alles opslaan** om de wijzigingen op de server op te slaan.

U kunt het knooppunt nu aan uw behoeften aanpassen door eigenschappen te wijzigen of nieuwe knooppunten te maken.

>[!NOTE]
>
>De meeste bewerkingen, waaronder Node maken, houden alle wijzigingen in het geheugen bij en slaan deze alleen op in de opslagplaats wanneer ze worden opgeslagen (via de knop Alles opslaan). Sommige bewerkingen, zoals verplaatsen, worden echter automatisch voortgezet.
>
>De validatie met betrekking tot het al dan niet toestaan van het nieuwe knooppunt door het knooppunttype van het bovenliggende knooppunt wordt ook eerst uitgevoerd door de JCR-opslagruimte bij het opslaan van wijzigingen. Als u een foutbericht ontvangt tijdens het opslaan van een knooppunt, moet u controleren of de inhoudsstructuur geldig is (u kunt bijvoorbeeld geen `nt:unstructured` knooppunt als onderliggend element van `nt:folder` knooppunt).

## Een eigenschap maken {#creating-a-property}

Een eigenschap maken met CRXDE Lite:

1. Open CRXDE Lite in uw browser.
1. Selecteer in het navigatievenster het knooppunt waaraan u de nieuwe eigenschap wilt toevoegen.
1. In de **Eigenschappen** in het onderste venster typt u de **Naam** de **Type** en de **Waarde**. Klikken **Toevoegen**.

1. Klikken **Alles opslaan** om de wijzigingen op de server op te slaan.

## Een script maken {#creating-a-script}

Een nieuw script maken:

1. Open CRXDE Lite in uw browser.
1. Klik in het navigatievenster met de rechtermuisknop op de component waar u het script wilt maken en selecteer **Maken...** vervolgens **Bestand maken...**.

1. Voer het bestand in **Naam** , met inbegrip van de verlenging ervan. Klikken **OK**.

1. Het nieuwe bestand wordt geopend als een tabblad in het deelvenster Bewerken.
1. Bewerk het bestand.
1. Klikken **Alles opslaan** om de wijzigingen op te slaan.

## Nodetypen exporteren en importeren {#exporting-and-importing-node-types}

Met CRXDE Lite kunt u knooppunttypedefinities importeren en/of exporteren in [CND-notatie (compacte naamruimte en definitie van knooppunttype)](https://jackrabbit.apache.org/jcr/node-type-notation.html).

Een definitie van het knooppunttype exporteren:

1. Open CRXDE Lite in uw browser.
1. Selecteer het vereiste knooppunt.
1. Selecteren **Gereedschappen** dan **Notitietype exporteren**.

1. De definitie in cnd-notatie wordt in uw browser weergegeven. Sla de gegevens indien nodig op.

Een definitie van het knooppunttype importeren:

1. Open CRXDE Lite in uw browser.
1. Selecteren **Gereedschappen** dan **Node-type importeren...**.

1. Voer in het tekstvak de CND-notatie voor de definitie in.
1. Controleren **Update toestaan** als u een bestaande definitie bijwerkt.
1. Klikken **Importeren**.

## Logboekregistratie {#logging}

Met CRXDE Lite kunt u het bestand weergeven `error.log` die zich in het bestandssysteem bevindt op `<crx-install-dir>/crx-quickstart/server/logs` en filtreer het met het aangewezen logboekniveau. Ga als volgt te werk:

1. Open CRXDE Lite in uw browser.
1. In de **Console** onder aan het venster selecteert u in het keuzemenu rechts in het scherm de optie **Serverlogboeken**.

1. Klik op de knop **Stoppen** om de berichten weer te geven.

U kunt:

* Pas de logboekparameters in de Console van het Felix aan door te klikken **Logboekconfiguraties** pictogram.
* De berichten wissen door op de knop **Penseel** pictogram.
* Plaats het bericht op de huidige selectie door op de knop **Vastzetten** pictogram.
* De weergave van berichten in- of uitschakelen door op de knop **Stoppen** pictogram.

## Toegangsbeheer {#access-control}

>[!NOTE]
>
>Zie [Gebruikers, groepen en beheer van toegangsrechten](/help/sites-administering/user-group-ac-admin.md) voor meer informatie .
