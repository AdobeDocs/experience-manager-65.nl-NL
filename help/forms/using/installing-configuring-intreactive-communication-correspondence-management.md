---
title: Interactieve communicatie installeren en configureren
description: Installeer en configureer interactieve communicatie met AEM-formulieren om zakelijke correspondenties, documenten, verklaringen, voordelenberichten, marketingmails, facturen en welkomstkits te maken.
topic-tags: installing
docset: aem65
role: Admin
exl-id: 37fcfad9-2f84-4f0c-aed8-e4a5a3303a06
solution: Experience Manager, Experience Manager Forms
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '1368'
ht-degree: 0%

---

# Interactieve communicatie installeren en configureren{#install-and-configure-interactive-communications}

## Inleiding {#introduction}

AEM Form heeft de mogelijkheid om het maken, samenstellen, beheren en leveren van beveiligde en interactieve documenten, zoals zakelijke correspondentie, documenten, instructies, kennisgevingen van voordelen, marketingmails, facturen en welkomstkits, te centraliseren. Dit vermogen is gekend als interactieve mededeling. De mogelijkheid is opgenomen in het invoegpakket voor AEM Forms. Het invoegpakket wordt geïmplementeerd op een instantie Auteur of Publiceren van AEM.

U kunt de interactieve communicatiemogelijkheid gebruiken om communicatie in meerdere indelingen te produceren. Bijvoorbeeld web en PDF. U kunt interactieve communicatie met AEM Workflow integreren om de geassembleerde communicatie te verwerken en te leveren aan klanten op het kanaal van hun keuze. U kunt bijvoorbeeld een communicatie naar de eindgebruiker verzenden via e-mail.

Als u een upgrade uitvoert van een vorige versie en al hebt geïnvesteerd in het beheer van correspondentie, kunt u de installatie van de [compatibiliteitspakket](../../forms/using/installing-configuring-intreactive-communication-correspondence-management.md#install-compatibility-package) het gebruik van het correspondentiebeheer voort te zetten. Voor informatie over de verschillen tussen interactief communicatie- en correspondentiebeheer raadpleegt u [Overzicht van interactieve communicatie](/help/forms/using/interactive-communications-overview.md#interactive-communications-vs-correspondence-management).

AEM Forms is een krachtig platform op bedrijfsniveau. Interactieve communicatie is slechts een van de mogelijkheden van AEM Forms. Voor de volledige lijst met mogelijkheden raadpleegt u [Inleiding tot AEM Forms](../../forms/using/introduction-aem-forms.md).

## Implementatietopologie {#deployment-topology}

AEM Forms add-on package is een toepassing die op AEM wordt geïmplementeerd. U vereist slechts een minimum van één AEM instantie van de Auteur en van de Verwerking om het Interactieve Communicatie vermogen in werking te stellen. De volgende topologie is indicatieve topologie om de Interactieve Mededelingen van AEM Forms, het Beheer van de Correspondentie, AEM Forms gegevensvangst, en Forms-Centric werkschema op mogelijkheden in werking te stellen OSGi. Voor gedetailleerde informatie over de topologie, zie [Architectuur en plaatsingstopologieën voor AEM Forms](/help/forms/using/aem-forms-architecture-deployment.md).

![aanbevolen topologie](assets/recommended-topology.png)

AEM Forms Interactive Communications voert admin, authoring en gebruikersinterfaces voor agent uit op de Author-instanties van AEM Forms. De instanties van de Publish gastheer definitieve versie van interactieve mededelingen die klaar voor consumptie door eindgebruikers zijn.

## Systeemvereisten {#system-requirements}

Voordat u de mogelijkheden voor interactief communicatie- en correspondentiebeheer van AEM Forms gaat installeren en configureren, moet u ervoor zorgen dat:

* Hardware- en software-infrastructuur is aanwezig. Voor een gedetailleerde lijst met ondersteunde hardware en software raadpleegt u [technische voorschriften](/help/sites-deploying/technical-requirements.md).

* Het installatiepad van de AEM-instantie bevat geen witruimten.
* Er wordt een AEM-instantie uitgevoerd. In AEM terminologie is een &quot;instantie&quot; een kopie van AEM die op een server in de auteur- of publicatiemodus wordt uitgevoerd. U hebt ten minste één AEM nodig (Auteur of Verwerking) om AEM Forms-functies voor interactieve communicatie en correspondentiebeheer uit te voeren:

   * **Auteur**: Een AEM die wordt gebruikt om inhoud te maken, te uploaden en te bewerken en om de website te beheren. Wanneer de inhoud gereed is om live te gaan, wordt deze gekopieerd naar de publicatie-instantie.
   * **Verwerking:** Een verwerkingsinstantie is een [AEM auteur](/help/forms/using/hardening-securing-aem-forms-environment.md) -instantie. Nadat u de installatie hebt uitgevoerd, kunt u een instantie Auteur instellen en deze lastiger maken.

   * **Publiceren**: een AEM-instantie die de gepubliceerde inhoud via internet of een intern netwerk aan het publiek levert.

* Aan de geheugenvereisten wordt voldaan. Voor het AEM Forms-invoegtoepassingspakket hebt u het volgende nodig:

   * 15 GB tijdelijke ruimte voor Microsoft® Windows-installaties.
   * 6 GB tijdelijke ruimte voor UNIX-installaties.

* Extra vereisten voor op UNIX gebaseerde systemen: als u het op UNIX gebaseerde besturingssysteem gebruikt, installeert u de volgende pakketten via de installatiemedia van het desbetreffende besturingssysteem.

<table>
 <tbody>
  <tr>
   <td>uitzetten</td>
   <td>libxcb</td>
   <td>freetype</td>
   <td>libXau</td>
  </tr>
  <tr>
   <td>Libsm</td>
   <td>zlib</td>
   <td>libICE</td>
   <td>libuuid</td>
  </tr>
  <tr>
   <td>glibc</td>
   <td>Libxext</td>
   <td><p>nss-softokn-freebl</p> </td>
   <td>fontconfig</td>
  </tr>
  <tr>
   <td>libX11</td>
   <td>libXrender</td>
   <td>libXrandr</td>
   <td>libXinerama</td>
  </tr>
 </tbody>
</table>

## AEM Forms-invoegtoepassing installeren {#install-aem-forms-add-on-package}

AEM Forms add-on package is een toepassing die op AEM wordt geïmplementeerd. Het pakket bevat interactieve AEM Forms-communicatie, correspondentiebeheer en andere mogelijkheden. Voer de volgende stappen uit om het invoegpakket te installeren:

1. Openen [Softwaredistributie](https://experience.adobe.com/downloads). U hebt een Adobe ID nodig om u aan te melden bij de softwaredistributie.
1. Selecteer **[!UICONTROL Adobe Experience Manager]** beschikbare opties in het kopmenu.
1. In de **[!UICONTROL Filters]** sectie:
   1. Selecteren **[!UICONTROL Forms]** van de **[!UICONTROL Solution]** vervolgkeuzelijst.
   2. Selecteer de versie en typ voor het pakket. U kunt ook de opdracht **[!UICONTROL Search Downloads]** om de resultaten te filteren.
1. Selecteer de pakketnaam die van toepassing is op het besturingssysteem. Selecteer **[!UICONTROL Accept EULA Terms]** en selecteert u **[!UICONTROL Download]**.
1. Open [Package Manager](https://experienceleague.adobe.com/docs/experience-manager-65/administering/contentmanagement/package-manager.html)  en klik om **[!UICONTROL Upload Package]** het pakket te uploaden.
1. Selecteer het pakket en klik op **[!UICONTROL Install]**.

   U kunt het pakket ook downloaden via de directe koppeling in het [artikel over afstandsverklaringen](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/forms-updates/aem-forms-releases.html?lang=en) van AEM Forms.

1. Nadat het pakket is geïnstalleerd, wordt u gevraagd om de AEM-instantie opnieuw op te starten. **Start de server niet meteen opnieuw op.** Voordat u de AEM Forms Server stopt, moet u wachten tot de GEREGISTREERDE en ServiceEvent UNREGISTERED-berichten niet meer voorkomen in het [bestand AEM-Installation-Directory]/crx-quickstart/logs/error.log en het logbestand stabiel is.

   >[!NOTE]
   >
   > Het wordt aanbevolen de SDK opnieuw te starten met de opdracht &#39;Ctrl + C&#39;. Het opnieuw opstarten van de AEM SDK met behulp van alternatieve methoden, bijvoorbeeld het stoppen van Java-processen, kan leiden tot inconsistenties in de AEM ontwikkelomgeving.

1. Herhaal stap 1-7 voor alle instanties Auteur en Publiceren.

## Configuratie na installatie {#post-installation-configurations}

AEM Forms heeft een paar verplichte en optionele configuraties. De verplichte configuraties omvatten het vormen bibliotheken BouncyCastle en serialization agent. De optionele configuraties zijn de configuratie van Dispatcher en Adobe Target.

### Verplichte configuraties na installatie {#mandatory-post-installation-configurations}

#### RSA- en BouncyCastle-bibliotheken configureren  {#configure-rsa-and-bouncycastle-libraries}

Voer de volgende stappen op alle Auteur uit en publiceer instanties om de bibliotheken op te starten afvaardigen:

1. Stop de onderliggende AEM instantie.
1. Open de [AEM installatiemap]\crx-quickstart\conf\sling.properties.

   Als u [AEM installatiemap]\crx-quickstart\bin\start.bat om AEM te starten, bewerkt u vervolgens de eigenschappen sling.properties op [AEM_root]\crx-quickstart\.

1. Voeg de volgende eigenschappen toe aan het bestand sling.properties:

   ```shell
   sling.bootdelegation.class.com.rsa.jsafe.provider.JsafeJCE=com.rsa.*
   ```

1. Sla het bestand op, sluit het en start het AEM.
1. Herhaal stap 1-4 voor alle instanties Auteur en Publiceren.

#### Vorm de rangschikkingsagent {#configure-the-serialization-agent}

Voer de volgende stappen uit op alle instanties Auteur en Publish om het pakket aan de lijst van gewenste personen toe te voegen:

1. Open AEM Configuration Manager in een browservenster. De standaard-URL is https://&#39;[server]:[poort]&quot;/system/console/configMgr.
1. Zoeken en openen **Configuratie van firewall voor deserialisatie**.
1. Voeg de **sun.util.agenda** aan de **lijst van gewenste personen** veld. Klik op Opslaan.
1. Herhaal stap 1-3 voor alle instanties Auteur en Publiceren.

### Optionele configuraties na installatie {#optional-post-installation-configurations}

#### Compatibiliteitspakket installeren {#install-compatibility-package}

Interactieve communicatie is de standaard en aanbevolen methode voor het maken van klantcommunicatie in AEM 6.5-formulieren. Als u een upgrade hebt uitgevoerd of gemigreerd vanuit een vorige versie en van plan bent om brieven te blijven gebruiken (Correspondence Management), installeert u het [AEMFD-compatibiliteitspakket](https://experienceleague.adobe.com/docs/experience-manager-65/forms/upgrade-aem-forms/aem-forms-osgi-upgrade/compatibility-package.html?lang=en).

Met het AEMFD-compatibiliteitspakket kunt u de volgende assets gebruiken uit AEM 6.4 Forms, AEM 6.3 Forms en AEM 6.2 Forms op AEM 6.5-formulieren:

* Documentfragmenten
* Letters
* Gegevenswoordenboeken
* Afgekeurde sjablonen en pagina&#39;s voor adaptieve formulieren

#### Dispatcher configureren {#configure-dispatcher}

Dispatcher is een Adobe Experience Manager-programma voor caching en taakverdeling dat wordt gebruikt met een webserver op bedrijfsniveau. Als u [Dispatcher](https://experienceleague.adobe.com/docs/experience-manager-dispatcher/using/configuring/dispatcher-configuration.html?lang=en)Voer vervolgens de volgende configuraties voor AEM Forms uit:

1. Toegang voor AEM Forms configureren:

   Open het bestand dispatcher.any voor bewerking. Navigeer naar de filtersectie en voeg het volgende filter toe aan de filtersectie:

   `/0025 { /type "allow" /glob "* /bin/xfaforms/submitaction*" } # to enable AEM Forms submission`

   Sla het bestand op en sluit het. Zie voor meer informatie over filters [Documentatie van Dispatcher](https://experienceleague.adobe.com/docs/experience-manager-dispatcher/using/configuring/dispatcher-configuration.html?lang=en).

1. Configureer de referentiefilterservice:

   Meld u als beheerder aan bij Apache Felix. De standaard-URL van het configuratiemanager is https://&#39;server&#39;:[port_number]/system/console/configMgr. In de **Configuraties** , selecteert u de **Filter Apache Sling Referrer** -optie. Voer in het veld Hosts toestaan de hostnaam van de Dispatcher in om het als referentie toe te staan en klik op **Opslaan**. De opmaak van de vermelding is https://&#39;[server]:[poort]&quot;.

#### Adobe Target integreren {#integrate-adobe-target}

Uw klanten zullen waarschijnlijk een interactieve mededeling verlaten als de ervaring het levert niet aansprekend is. Hoewel het voor de klanten frustrerend is, keert het ook het steunvolume en de kosten voor uw organisatie terug. Het is kritiek en uitdagend om de juiste klantenervaring te identificeren en te verstrekken die de omzettingssnelheid verhoogt. AEM formulieren vormen de sleutel tot dit probleem.

AEM formulieren kunnen worden geïntegreerd met Adobe Target, een Adobe Experience Cloud-oplossing, om persoonlijke en aantrekkelijke klantervaringen te bieden via meerdere digitale kanalen. Adobe Target gebruiken om interactieve communicatie aan te passen, [Adobe Target integreren met AEM Forms](../../forms/using/ab-testing-adaptive-forms.md#setupandintegratetargetinaemforms).

#### SSL-communicatie configureren voor formuliergegevensmodel  {#configure-ssl-communcation-for-form-data-model}

U kunt SSL-communicatie inschakelen voor het formuliergegevensmodel. Als u SSL-communicatie wilt inschakelen voor het formuliergegevensmodel, voegt u certificaten toe aan het Java™ Trust Store van alle exemplaren voordat u een AEM Forms-exemplaar start. U kunt de onderstaande opdracht uitvoeren om de certificaten toe te voegen:

`keytool -import -alias <alias-name> -file <pathTo .cer certificate file> -keystore <<pathToJRE>\lib\security\cacerts>`

## Volgende stappen {#next-steps}

U hebt een omgeving geconfigureerd voor het gebruik van interactieve communicatie- en correspondentiebeheermogelijkheden. Nu zijn de stappen voor het gebruik van deze mogelijkheid:

* [Overzicht van correspondentiebeheer](/help/forms/using/interactive-communications-overview.md)

* [Een interactieve communicatie maken](../../forms/using/create-interactive-communication.md)

* [Een brief voor correspondentiebeheer maken](../../forms/using/create-letter.md)
