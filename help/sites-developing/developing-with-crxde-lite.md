---
title: Ontwikkelen met CRXDE Lite
description: CRXDE Lite is ingebed in Adobe Experience Manager (AEM) en laat u toe om standaardontwikkelingstaken in browser uit te voeren
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: development-tools
content-type: reference
docset: aem65
exl-id: 9e88ca55-ac3d-4857-b6b2-aeb732562664
solution: Experience Manager, Experience Manager Sites
feature: Developing,Developer Tools
role: Developer
source-git-commit: 305227eff3c0d6414a5ae74bcf3a74309dccdd13
workflow-type: tm+mt
source-wordcount: '2118'
ht-degree: 0%

---

# Ontwikkelen met CRXDE Lite{#developing-with-crxde-lite}

In deze sectie wordt beschreven hoe u uw Adobe Experience Manager-toepassing (AEM) kunt ontwikkelen met behulp van CRXDE Lite.

Raadpleeg de overzichtsdocumentatie voor meer informatie over de verschillende ontwikkelomgevingen die beschikbaar zijn.

CRXDE Lite is ingebed in AEM en laat u toe om standaardontwikkelingstaken in browser uit te voeren. Met CRXDE Lite kunt u een project maken, bestanden (zoals .jsp en .java), mappen, sjablonen, componenten, dialoogvensters, knooppunten, eigenschappen en bundels maken en bewerken tijdens het vastleggen.
CRXDE Lite wordt aanbevolen als u geen directe toegang hebt tot de AEM server. Of wanneer u een toepassing ontwikkelt door de componenten en Java™-bundels buiten de box uit te breiden of te wijzigen, of wanneer u geen speciale debugger nodig hebt, codevoltooiing en syntaxismarkering.

>[!NOTE]
>
>Vanaf AEM 6.5.5.0 is anonieme toegang tot CRXDE Lite niet meer mogelijk.
>Gebruikers worden omgeleid naar het aanmeldingsscherm.


>[!NOTE]
>
>De Adobe adviseert dat u [ AEM de Hulpmiddelen van de Ontwikkelaar voor Verduistering ](/help/sites-developing/aem-eclipse.md) en [ AEM de Uitbreiding van de Haakjes van HTML ](/help/sites-developing/aem-brackets.md) tijdens projectontwikkeling gebruikt.

## Aan de slag met CRXDE Lite {#getting-started-with-crxde-lite}

Ga als volgt te werk om aan de slag te gaan met CRXDE Lite:

1. AEM installeren.
1. Voer in uw browser `https://<host>:<port>/crx/de` in. Standaard is dit `https://localhost:4502/crx/de` .
1. Ga uw **gebruikersbenaming** en **wachtwoord** in. De standaardinstelling is `admin` en `admin` .

1. Klik **OK**.

De gebruikersinterface van CRXDE Lite ziet er als volgt uit in uw browser:

![ chlimage_1-18 ](assets/crx-interface.jpg)

U kunt nu CRXDE Lite gebruiken om uw toepassing te ontwikkelen.

## Overzicht van de gebruikersinterface {#overview-of-the-user-interface}

CRXDE Lite biedt de volgende functionaliteit:

<table>
 <tbody>
  <tr>
   <td>Bovenste schakelbalk</td>
   <td>Snel schakelen tussen CRXDE Lite, de Manager van het Pakket, en het Aandeel van het Pakket.</td>
  </tr>
  <tr>
   <td>Knooppuntwidget</td>
   <td><p>Geeft het pad naar het geselecteerde knooppunt weer.</p> <p>U kunt het ook gebruiken om aan een knoop te springen, door de weg door hand in te gaan, of het te kleven van ergens anders, en het drukken gaat binnen.</p> <p>Het biedt ook ondersteuning bij het zoeken naar knooppunten met een specifieke knooppuntnaam. Voer de naam in van het knooppunt dat u wilt zoeken en wacht (of druk op het zoeksymbool aan de rechterkant). U kunt proberen ingaand, bijvoorbeeld, het koord <em> eiken </em> in widget om te zien hoe het werkt. Als een bepaald knooppunt of bepaalde knooppunten in het verkennervenster wordt geladen, wordt de lijst weergegeven en kunt u het pad selecteren en op Enter drukken om naar het knooppunt te navigeren. Het werkt alleen voor de knooppunten die in de CRXDE-clienttoepassing in de browser zijn geladen. Als u de hele repository wilt doorzoeken, gebruikt u Extra en vervolgens Query.</p> </td>
  </tr>
  <tr>
   <td>Explorer-venster</td>
   <td><p>Toont een boom van alle knopen in de bewaarplaats.</p> <p>Klik een knoop zodat kunt u zijn eigenschappen op het <strong> Eigenschappen </strong> lusje tonen. Nadat u op een knooppunt hebt geklikt, kunt u een handeling op de werkbalk selecteren. Klik nogmaals op het knooppunt om de naam ervan te wijzigen.</p> <p>Structuurnavigatiefilter (binoculair pictogram): hiermee kunt u de knooppunten in de opslagplaats filteren waarvoor de naam de invoertekst bevat. Het is slechts op knopen van toepassing die plaatselijk zijn geladen.<br /> </p> </td>
  </tr>
  <tr>
   <td>Venster Bewerken</td>
   <td><p><strong> Huis </strong> tabel: laat u inhoud en/of documentatie zoeken en tot ontwikkelaarsmiddelen (documentatie, ontwikkelaarblog, kennisbasis) en steun (de homepage van de Adobe en steuncentrum) toegang hebben.<br /> </p> <p>Dubbelklik een dossier in de <strong> ruit van de Ontdekkingsreiziger </strong> zodat kunt u zijn inhoud tonen. Bijvoorbeeld een .jsp- of een .java-bestand. U kunt het dan wijzigen en de veranderingen bewaren.</p> <p>Zodra een dossier in <strong> wordt uitgegeven geeft </strong> ruit uit, zijn de volgende hulpmiddelen beschikbaar op de toolbar:<br /> </p> - <strong> toon in boom: </strong> toont het dossier in de bewaarplaatsboom.<br /> - <strong> Onderzoek/vervang... </strong>: doe onderzoek of vervang.<br /> <br /> tweemaal klikken de statuslijn van <strong> geeft </strong> ruit uit <strong> gaat naar lijn </strong> dialoog zodat kunt u een specifiek lijnaantal ingaan om te gaan.<br /> </td>
  </tr>
  <tr>
   <td>Het tabblad Eigenschappen <br /> </td>
   <td>Geeft de eigenschappen weer van het knooppunt dat u hebt geselecteerd. U kunt nieuwe eigenschappen toevoegen of bestaande eigenschappen schrappen.<br /> </td>
  </tr>
  <tr>
   <td>Het tabblad Toegangsbeheer</td>
   <td><p>Toon toestemmingen die op weg, bewaarplaats-niveau, of hoofd worden gebaseerd.</p> <p>De rechten worden opgesplitst in</p> <p>- <strong> Toepasselijk Beleid van het Toegangsbeheer </strong>: Het beleid dat op de selectie kan worden toegepast.</p> <p>- <strong> Lokaal Beleid van het Toegangsbeheer </strong>: Het beleid dat plaatselijk op de selectie wordt toegepast.</p> <p>- <strong> Effectief Beleid van het Toegangsbeheer </strong>: Het beleid dat voor de selectie wordt toegepast, zou plaatselijk kunnen worden geplaatst of van ouderknopen worden geërft.</p> <p>Opmerking. Om de informatie van het Toegangsbeheer bij allen te kunnen zien, moet de gebruiker die aan CRXDE Lite wordt aangemeld read-rights aan ACL ingangen hebben. De anonieme gebruiker kan deze informatie standaard niet zien. Meld u aan als beheerder om de informatie te zien, bijvoorbeeld.</p> </td>
  </tr>
  <tr>
   <td>Tabblad Replicatie</td>
   <td><p>Toon de replicatiestatus van de knoop. U kunt het knooppunt repliceren en herhalen.</p> </td>
  </tr>
  <tr>
   <td>Tabblad Console <br /> </td>
   <td><p><strong> Logboeken van de Server </strong>:</p> <p>Hier worden logboekberichten weergegeven. U kunt het logboekniveau vormen, de console ontruimen, bij de geselecteerde rolpositie spelden, en toelaten of onbruikbaar maken het tonen van berichten.<br /> </p> <p><strong> Controle van de Versie </strong>:</p> <p>Toont de berichten van de versiecontrole.<br /> </p> </td>
  </tr>
  <tr>
   <td>Het tabblad Build Info <br /> </td>
   <td>Toont informatie wanneer een bundel wordt gebouwd.<br /> </td>
  </tr>
  <tr>
   <td>Vernieuwen <br /> </td>
   <td>Hiermee vernieuwt u de selectie. Wijzigingen van andere gebruikers worden bijgewerkt in uw weergave van de opslagplaats. Wijzigingen die u hebt aangebracht, blijven ongewijzigd.<br /> </td>
  </tr>
  <tr>
   <td>Alles opslaan</td>
   <td><p><strong> sparen allen </strong>:<br /> </p> <p>Hiermee slaat u alle aangebrachte wijzigingen op. Totdat u op Opslaan klikt, zijn de wijzigingen tijdelijk en gaan deze verloren wanneer u de console afsluit.</p> <p><strong> terugkeren </strong>:</p> <p>Hiermee worden alle wijzigingen genegeerd die u hebt aangebracht in het geselecteerde knooppunt sinds de laatste opslaghandeling en wordt vervolgens de status van de opslagplaats voor het geselecteerde knooppunt opnieuw geladen.</p> <p><strong> terugkeert allen </strong>:</p> <p>Hiermee worden alle wijzigingen genegeerd die u hebt aangebracht in de gehele opslagplaats sinds de laatste opslaghandeling, en wordt vervolgens de status van de opslagplaats opnieuw geladen.</p> </td>
  </tr>
  <tr>
   <td>Maken... <br /> </td>
   <td><p>Drop-down menu om het volgende onder de geselecteerde knoop tot stand te brengen:<br /> </p> <p>- <strong> Knoop </strong>: een knoop met een willekeurig knooptype <br /> </p> <p>- <strong> Dossier </strong>: niet:dossierknoop en zijn geen:middel subnode</p> <p>- <strong> Omslag </strong>: niet:omslagknoop</p> <p>- <strong> Malplaatje </strong>: AEM malplaatje</p> <p>- <strong> Component </strong>: AEM component</p> <p>- <strong> Dialoog </strong>: AEM dialoog</p> </td>
  </tr>
  <tr>
   <td>Verwijderen <br /> </td>
   <td>Hiermee verwijdert u het geselecteerde knooppunt.<br /> </td>
  </tr>
  <tr>
   <td>Kopiëren</td>
   <td>Kopieert de geselecteerde knoop.<br /> </td>
  </tr>
  <tr>
   <td>Plakken <br /> </td>
   <td>Plakt de gekopieerde knoop onder de geselecteerde knoop.<br /> </td>
  </tr>
  <tr>
   <td>Verplaatsen...<br /> </td>
   <td>Hiermee verplaatst u het geselecteerde knooppunt naar het knooppunt dat via het dialoogvenster is ingesteld.</td>
  </tr>
  <tr>
   <td>Naam wijzigen...<br /> </td>
   <td>Verandert de naam van de geselecteerde knoop.<br /> </td>
  </tr>
  <tr>
   <td>Mixins ...<br /> </td>
   <td>Hiermee kunt u gemengde typen toevoegen aan het knooppunttype. De mixintypes worden meestal gebruikt om geavanceerde eigenschappen zoals versioning, toegangsbeheer toe te voegen, van verwijzingen voorzien, en het sluiten aan de knoop.</td>
  </tr>
  <tr>
   <td>Gereedschappen <br /> </td>
   <td><p>Vervolgkeuzemenu met de volgende gereedschappen:</p> <p>- <strong> Configuratie van de Server... </strong>: om tot de Console van Felix toegang te hebben.</p> <p>- <strong> Vraag... </strong>: om de bewaarplaats te vragen.</p> <p>- <strong> Bevoegdheden ... </strong>: aan open voorrechtbeheer, waar u voorrechten kunt bekijken en toevoegen.</p> <p>- <strong> Controle van de Toegang van de Test... </strong>: een plaats waar u de toestemming voor een bepaalde weg en/of een hoofd kunt testen.</p> <p>- <strong> Type van Knoop van de Uitvoer </strong>: om knooptypes in het systeem als knoopaantekening uit te voeren.</p> <p>- <strong> het Type van Knoop van de Invoer... </strong>: om knooptypes in te voeren gebruikend cnd aantekening.</p> <p>- <strong> installeer Foutopsporing van de SiteCatalyst... </strong>: instructies op hoe te om Foutopsporing van de Analyse te installeren.</p> </td>
  </tr>
  <tr>
   <td>Aanmeldingswidget <br /> </td>
   <td><p>Toont het programma geopende gebruikers en de werkruimte waarin zij, bijvoorbeeld, admin@crx.default worden geregistreerd.</p> <p>Klik op deze knop om u aan te melden of opnieuw aan te melden als specifieke gebruiker. Als u geen werkruimte opgeeft waarin u zich wilt aanmelden, wordt u aangemeld bij de standaardwerkruimte, crx.default.</p> <p>Als u de bewaarplaats als Anonieme gebruiker wilt doorbladeren, gebruik <strong> anoniem </strong> als login naam, en om het even welk wachtwoord (bijvoorbeeld, een ruimte of een punt).<br /> </p> <p>Als uw vergunning niet meer geldig is (bijvoorbeeld, is het verlopen), toont de login widget "<strong> Onbevoegd - Login... </strong>". Klik hierop om u opnieuw aan te melden.</p> </td>
  </tr>
 </tbody>
</table>

## Een map maken {#creating-a-folder}

Een map met CRXDE Lite maken:

1. Open CRXDE Lite in uw browser.
1. In de ruit van de Navigatie, klik de omslag met de rechtermuisknop aan waaronder u de omslag wilt tot stand brengen, **creeert...**, dan **leidt tot Omslag...**.

1. Ga de omslag **Naam** in en klik **O.K.**.

1. Klik **sparen allen** om de veranderingen op de server te bewaren.

## Een sjabloon maken {#creating-a-template}

Een sjabloon maken met CRXDE Lite:

1. Open CRXDE Lite in uw browser.
1. In de ruit van de Navigatie, klik de omslag met de rechtermuisknop aan waar u het malplaatje wilt tot stand brengen, **creeert...**, dan **leidt Malplaatje...**.

1. Ga het **Etiket** in, **Titel**, **Beschrijving**, **Type van Middel**, en **Rangschikkend** van het malplaatje. Klik op **Next**.

1. Deze stap is facultatief: plaats **Toegestane Wegen**. Klik **daarna**

1. Deze stap is facultatief: plaats **Toegestane Ouders**. Klik op **Next**.

1. Deze stap is facultatief: plaats de **Toegestane Kinderen**. Klik **OK**.

1. Klik **sparen allen** om de veranderingen op de server te bewaren.

Het leidt tot:

* Een knooppunt van het type `cq:Template` met sjablooneigenschappen

* Een onderliggende node van het type `cq:PageContent` met eigenschappen voor pagina-inhoud

U kunt eigenschappen aan uw malplaatje toevoegen: zie [ Creërend een Bezit ](#creating-a-property) sectie.

## Een component maken {#creating-a-component}

De hier beschreven functie is alleen beschikbaar als CQ5 is geïnstalleerd, dat wil zeggen als het knooppunttype `cq:Component` beschikbaar is in de repository.

Een component maken met CRXDE Lite:

1. Open CRXDE Lite in uw browser.
1. In de ruit van de Navigatie, klik de omslag met de rechtermuisknop aan waar u de component wilt tot stand brengen, **creeert...**, dan **creeer Component..**.

1. Ga het **Etiket** in, **Titel**, **Beschrijving**, **het Type van Middel van de Super**, en **Groep** van de component. Klik op **Next**.

1. Deze stap is facultatief: plaats de componenteneigenschappen **is Container,** **geen Decoratie**, **Naam van de Cel**, en **Weg van de Dialoog**. Klik op **Next**.

1. Deze stap is facultatief: plaats het componentenbezit **Toegestane Ouders**. Klik op **Next**.

1. Deze stap is facultatief: plaats het componentenbezit **Toegestane Kinderen**. Klik **OK**.

1. Klik **sparen allen** om de veranderingen op de server te bewaren.

Het leidt tot:

* Een knooppunt van het type `cq:Component`
* Componenteigenschappen
* Een .jsp-componentscript

## Een dialoogvenster maken {#creating-a-dialog}

Een dialoogvenster maken met CRXDE Lite:

1. Open CRXDE Lite in uw browser.
1. In de ruit van de Navigatie, klik de component met de rechtermuisknop aan waar u de dialoog wilt tot stand brengen, **creeert...**, dan **leidt tot Dialoog...**.

1. Ga het **Etiket** en de **Titel** in. Klik **OK**.

1. Klik **sparen Al** l om de veranderingen op de server te bewaren.

Er wordt een dialoogvenster gemaakt met de volgende structuur:

`dialog[cq:Dialog]/items[cq:Widget]/items[cq:WidgetCollection]/tab1[cq:Panel]`

U kunt het dialoogvenster nu aan uw wensen aanpassen door eigenschappen te wijzigen of knooppunten te maken.

U kunt een dialoogvenster ook bewerken met de Dialoogeditor. Als u dubbelklikt op het dialoogvenster in CRXDE Lite, wordt de editor weergegeven. Meer informatie over de Redacteur van de Dialoog kan [ hier ](/help/sites-developing/dialog-editor.md) worden gevonden.

## Een knooppunt maken {#creating-a-node}

Een knooppunt maken met CRXDE Lite:

1. Open CRXDE Lite in uw browser.
1. In de ruit van de Navigatie, klik de knoop met de rechtermuisknop aan waar u de knoop wilt tot stand brengen, **creeert...**, dan **leidt tot Knoop..**.
1. Ga de **Naam** en het **Type** in. Klik **OK**.
1. Klik **sparen allen** om de veranderingen op de server te bewaren.

U kunt het knooppunt nu aan uw behoeften aanpassen door eigenschappen te wijzigen of knooppunten te maken.

>[!NOTE]
>
>De meeste bewerkingen, waaronder Node maken, houden alle wijzigingen in het geheugen bij en slaan deze alleen op in de opslagplaats wanneer ze worden opgeslagen (met de knop Alles opslaan). Sommige bewerkingen, zoals verplaatsen, worden echter automatisch voortgezet.
>
>De validatie betreffende het al dan niet toestaan van het nieuwe knooppunt door het knooppunttype van het bovenliggende knooppunt wordt ook eerst uitgevoerd door de JCR-opslagruimte bij het opslaan van wijzigingen. Als u een foutbericht ontvangt tijdens het opslaan van een knooppunt, controleert u of de inhoudsstructuur geldig is (u kunt bijvoorbeeld geen `nt:unstructured` -knooppunt maken als onderliggend knooppunt van `nt:folder` -knooppunt).

## Een eigenschap maken {#creating-a-property}

Een eigenschap maken met CRXDE Lite:

1. Open CRXDE Lite in uw browser.
1. Selecteer in het navigatievenster het knooppunt waaraan u de nieuwe eigenschap wilt toevoegen.
1. In het **lusje van Eigenschappen** in de bodemruit, ga de **Naam**, het **Type** in, en de **Waarde**. Klik **toevoegen**.

1. Klik **sparen allen** om de veranderingen op de server te bewaren.

## Een script maken {#creating-a-script}

Een script maken:

1. Open CRXDE Lite in uw browser.
1. In de ruit van de Navigatie, klik de component met de rechtermuisknop aan waar u het manuscript wilt tot stand brengen, **creeert...**, dan **leidt tot Dossier...**.

1. Ga het Dossier **Naam** met inbegrip van zijn uitbreiding in. Klik **OK**.

1. Het nieuwe bestand wordt geopend als een tabblad in het deelvenster Bewerken.
1. Bewerk het bestand.
1. Klik **sparen allen** om de veranderingen te bewaren.

## Nodetypen exporteren en importeren {#exporting-and-importing-node-types}

Met CRXDE Lite, kunt u knooptype definities in [ invoeren en/of uitvoeren CND (Compacte Namespace en de Definitie van het Type van Knoop) ](https://jackrabbit.apache.org/jcr/node-type-notation.html).

Een definitie van het knooppunttype exporteren:

1. Open CRXDE Lite in uw browser.
1. Selecteer het vereiste knooppunt.
1. Selecteer **Hulpmiddelen** toen **het Type van Knoop van de Uitvoer**.

1. De definitie wordt in cnd-notatie weergegeven in uw browser. Sla indien nodig de gegevens op.

Een definitie van het knooppunttype importeren:

1. Open CRXDE Lite in uw browser.
1. Selecteer **Hulpmiddelen** toen **het Type van Knoop van de Invoer...**.

1. Voer in het tekstvak de CND-notatie voor de definitie in.
1. Controle **staat Update** toe als u een bestaande definitie bijwerkt.
1. Klik **Invoer**.

## Logboekregistratie {#logging}

Met CRXDE Lite kunt u het bestand `error.log` weergeven dat zich in het bestandssysteem bevindt op `<crx-install-dir>/crx-quickstart/server/logs` en dit filteren met het juiste logniveau. Ga als volgt te werk:

1. Open CRXDE Lite in uw browser.
1. In het **lusje van de Console** bij de bodem van het venster, in het drop-down menu op het recht, uitgezochte **Logboeken van de Server**.

1. Klik het **pictogram van het Einde** om de berichten te tonen.

U kunt:

* Pas de logboekparameters in de Console van de Felix aan door het **Logging van Configuraties** pictogram te klikken.
* Wis de berichten door het **pictogram van de Borstel** te klikken.
* Zet het bericht bij de selectie vast door het **Vastzetten** pictogram te klikken.
* Laat of maak het tonen van berichten onbruikbaar door het **pictogram van het Einde** te klikken.

## Toegangsbeheer {#access-control}

>[!NOTE]
>
>Zie [ Gebruikers, Groepen, en het Beleid van de Rechten van de Toegang ](/help/sites-administering/user-group-ac-admin.md) voor meer informatie.
