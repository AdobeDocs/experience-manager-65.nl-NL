---
title: Interactieve communicatie installeren en configureren
seo-title: Interactieve communicatie installeren en configureren
description: Installeer en configureer AEM Forms Interactive Communications om zakelijke correspondentie, documenten, instructies, kennisgevingen van voordelen, marketingmails, facturen en welkomstkits te maken.
seo-description: Installeer en configureer AEM Forms Interactive Communications om zakelijke correspondentie, documenten, instructies, kennisgevingen van voordelen, marketingmails, facturen en welkomstkits te maken.
uuid: 8acb7f68-0b52-4acd-97e2-af31c9408e8d
topic-tags: installing
discoiquuid: 225f2bc1-6842-4c79-a66d-8024a29325c0
docset: aem65
translation-type: tm+mt
source-git-commit: 317fadfe48724270e59644d2ed9a90fbee95cf9f

---


# Interactieve communicatie installeren en configureren{#install-and-configure-interactive-communications}

## Inleiding {#introduction}

AEM Form heeft de mogelijkheid om het maken, samenstellen, beheren en leveren van beveiligde en interactieve documenten, zoals zakelijke correspondentie, documenten, instructies, kennisgevingen van voordelen, marketingmails, facturen en welkomstkits, te centraliseren. Dit vermogen is gekend als interactieve mededeling. De mogelijkheid is opgenomen in het invoegpakket voor AEM Forms. Het invoegpakket wordt geïmplementeerd op een instantie Auteur of Publiceren van AEM.

U kunt de interactieve communicatiemogelijkheid gebruiken om communicatie in meerdere indelingen te produceren. Bijvoorbeeld web en PDF. U kunt interactieve communicatie met AEM Workflow integreren om de geassembleerde communicatie te verwerken en aan klanten op het kanaal van hun keus te leveren. U kunt bijvoorbeeld een communicatie naar de eindgebruiker verzenden via e-mail.

Als u een upgrade uitvoert van een vorige versie en al hebt geïnvesteerd in het beheer van correspondentie, kunt u het [compatibiliteitspakket](../../forms/using/installing-configuring-intreactive-communication-correspondence-management.md#install-compatibility-package) installeren en het correspondentiebeheer blijven gebruiken. Voor informatie over de verschillen tussen interactieve mededeling en correspondentiebeheer, zie [Interactief Communicatieoverzicht](/help/forms/using/interactive-communications-overview.md#interactive-communications-vs-correspondence-management).

AEM Forms is een krachtig platform op bedrijfsniveau. Interactieve communicatie is slechts een van de mogelijkheden van AEM Forms. Voor de volledige lijst van mogelijkheden, zie [Inleiding aan Vormen](../../forms/using/introduction-aem-forms.md)AEM.

## Implementatietopologie {#deployment-topology}

AEM Forms add-on package is een toepassing die op AEM wordt geïmplementeerd. U vereist slechts een minimum van één instantie van de Auteur AEM en van de Verwerking om het Interactieve Communicatie vermogen in werking te stellen. De volgende topologie is indicatieve topologie om de Interactieve Mededelingen van de Vormen AEM, het Beheer van de Correspondentie in werking te stellen, Vormen AEM gegevens vangen, en vormen-Centric werkschema op mogelijkheden OSGi. Voor gedetailleerde informatie over de topologie, zie [Architectuur en plaatsingstopologieën voor Vormen](/help/forms/using/aem-forms-architecture-deployment.md)AEM.

![aanbevolen topologie](assets/recommended-topology.png)

AEM vormt Interactieve Communicatie loopbeheer, creatie, en agentengebruikersinterfaces op de instanties van de Auteur van Vormen AEM. De instanties van de Publish gastheer definitieve versie van interactieve mededelingen die klaar voor consumptie door eindgebruikers zijn.

## Systeemvereisten {#system-requirements}

Voordat u de mogelijkheden voor interactieve communicatie en correspondentiebeheer van AEM Forms gaat installeren en configureren, moet u ervoor zorgen dat:

* Hardware- en software-infrastructuur is aanwezig. Raadpleeg de [technische vereisten](/help/sites-deploying/technical-requirements.md)voor een gedetailleerde lijst met ondersteunde hardware en software.

* Het installatiepad van de AEM-instantie bevat geen spaties.
* Er wordt een AEM-instantie uitgevoerd. In AEM-terminologie is een &quot;instantie&quot; een kopie van AEM die wordt uitgevoerd op een server in de auteur- of publicatiemodus. U hebt ten minste één AEM-instantie (Auteur of Verwerking) nodig om interactieve communicatie- en correspondentiebeheermogelijkheden van AEM Forms uit te voeren:

   * **Auteur**: Een AEM-instantie die wordt gebruikt om inhoud te maken, te uploaden en te bewerken en om de website te beheren. Wanneer de inhoud gereed is om live te gaan, wordt deze gekopieerd naar de publicatie-instantie.
   * **Verwerking:** Een verwerkingsinstantie is een [verhard AEM Author](/help/forms/using/hardening-securing-aem-forms-environment.md) -instantie. Nadat u de installatie hebt uitgevoerd, kunt u een instantie Auteur instellen en deze lastiger maken.

   * **Publiceren**: Een AEM-instantie die de gepubliceerde inhoud via internet of een intern netwerk aan het publiek levert.

* Er wordt voldaan aan de geheugenvereisten. AEM Forms add-on package vereist:

   * 15 GB tijdelijke ruimte voor op Microsoft Windows gebaseerde installaties.
   * 6 GB tijdelijke ruimte voor UNIX-installaties.

* Extra eisen voor op UNIX gebaseerde systemen: Als u het op UNIX gebaseerde besturingssysteem gebruikt, installeert u de volgende pakketten via de installatiemedia van het desbetreffende besturingssysteem.

<table>
 <tbody>
  <tr>
   <td>uitzetten</td>
   <td>libxcb</td>
   <td>freetype</td>
   <td>libXau</td>
  </tr>
  <tr>
   <td>libSM</td>
   <td>zlib</td>
   <td>libICE</td>
   <td>libuuid</td>
  </tr>
  <tr>
   <td>glibc</td>
   <td>libXext</td>
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

## AEM Forms add-on-pakket installeren {#install-aem-forms-add-on-package}

AEM Forms add-on package is een toepassing die op AEM wordt geïmplementeerd. Het pakket bevat interactieve communicatie, correspondentiebeheer en andere mogelijkheden van AEM Forms. Voer de volgende stappen uit om het invoegpakket te installeren:

1. Meld u als beheerder aan bij de [AEM-server](https://localhost:4502) en open [pakketshare](https://localhost:4502/crx/packageshare). U hebt een Adobe-id nodig om u aan te melden bij het delen van het pakket.
1. Zoek in [AEM-pakketshare](https://localhost:4502/crx/packageshare/login.html)in **AEM 6.5 Forms add-on pakketten** of **nieuwste servicepakketten** op het pakket dat op uw besturingssysteem van toepassing is en klik op **Download**. Lees en accepteer de licentieovereenkomst en klik op **OK**. Het downloaden begint. Nadat u het bestand hebt gedownload, staat het woord **Gedownload** naast het pakket.

   U kunt het versienummer ook gebruiken om een add-on pakket te zoeken. Raadpleeg het [artikel over de release](https://helpx.adobe.com/aem-forms/kb/aem-forms-releases.html) van AEM Forms voor het versienummer van het meest recente pakket.

1. Klik op **Gedownload** nadat het downloaden is voltooid. U wordt omgeleid naar pakketbeheer. Zoek in pakketbeheer naar het gedownloade pakket en klik op **Installeren**.

   Als u het pakket handmatig downloadt via de directe koppeling in het [artikel met de release](https://helpx.adobe.com/aem-forms/kb/aem-forms-releases.html) van AEM Forms, meldt u zich aan bij pakketbeheer, klikt u op Pakket **** uploaden, selecteert u het gedownloade pakket en klikt u op Uploaden. Nadat het pakket is geüpload, klikt u op de pakketnaam en klikt u op **Installeren.**

1. Nadat het pakket is geïnstalleerd, wordt u gevraagd om de AEM-instantie opnieuw te starten. **Start de server niet onmiddellijk opnieuw.** Voordat u de AEM Forms-server stopt, wacht u tot de berichten ServiceEvent REGISTERED en ServiceEvent UNREGISTERED niet meer worden weergegeven in het bestand [AEM-Installation-Directory]/crx-quickstart/logs/error.log en het logbestand stabiel is.
1. Herhaal stap 1-4 voor alle instanties Auteur en Publiceren.

## Configuratie na installatie {#post-installation-configurations}

AEM Forms heeft een aantal verplichte en optionele configuraties. De verplichte configuraties omvatten het vormen bibliotheken BouncyCastle en serialization agent. De optionele configuraties zijn het configureren van dispatcher en Adobe Target.

### Verplichte configuraties na installatie {#mandatory-post-installation-configurations}

#### RSA- en BouncyCastle-bibliotheken configureren {#configure-rsa-and-bouncycastle-libraries}

Voer de volgende stappen op alle Auteur uit en publiceer instanties om de bibliotheken op te starten afvaardigen:

1. Stop de onderliggende AEM-instantie.
1. Open de [AEM-installatiemap]\crx-quickstart\conf\sling.properties.

   Als u de [AEM-installatiemap]\crx-quickstart\bin\start.bat hebt gebruikt om AEM te starten, bewerkt u de sling.properties op de locatie [AEM_root]\crx-quickstart\.

1. Voeg de volgende eigenschappen toe aan het bestand sling.properties:

   ```
   sling.bootdelegation.class.com.rsa.jsafe.provider.JsafeJCE=com.rsa.*
   sling.bootdelegation.class.org.bouncycastle.jce.provider.BouncyCastleProvider=org.bouncycastle.*
   ```

1. Sla het bestand op, sluit het en start de AEM-instantie.
1. Herhaal stap 1-4 voor alle instanties Auteur en Publiceren.

#### Vorm de rangschikkingsagent {#configure-the-serialization-agent}

Voer de volgende stappen uit op alle instanties Auteur en Publiceren om het pakket te whitelist:

1. Open AEM Configuration Manager in een browservenster. De standaard-URL is https://&#39;[server]:[port]&#39;/system/console/configMgr.
1. Zoek en open Configuratie van de Firewall van de **Deserialization**.
1. Voeg het pakket **sun.util.agenda** toe aan het veld **whitelist** . Klik op Opslaan.
1. Herhaal stap 1-3 voor alle instanties Auteur en Publiceren.

### Optionele configuraties na installatie {#optional-post-installation-configurations}

#### Compatibiliteitspakket installeren {#install-compatibility-package}

De interactieve mededeling is het gebrek en geadviseerde benadering om klantenmededelingen in Vormen AEM 6.5 tot stand te brengen. Als u een upgrade hebt uitgevoerd of een migratie hebt uitgevoerd van een vorige versie en u wilt doorgaan met het gebruik van letters (Correspondentiebeheer), installeert u het [AEMFD-compatibiliteitspakket](https://www.adobeaemcloud.com/content/marketplace/marketplaceProxy.html?packagePath=/content/companies/public/adobe/packages/cq640/fd/AEM-FORMS-6.4-COMPAT).

Met het compatibiliteitspakket AEMFD kunt u de volgende elementen van AEM 6.4 Forms, AEM 6.3 Forms en AEM 6.2 Forms op AEM 6.5 Forms gebruiken:

* Documentfragmenten
* Letters
* Gegevenswoordenboeken
* Afgekeurde sjablonen en pagina&#39;s voor adaptieve formulieren

#### Dispatcher configureren {#configure-dispatcher}

Dispatcher is een programma voor het in cache plaatsen en taakverdeling voor AEM. AEM Dispatcher helpt ook de AEM-server tegen aanvallen te beschermen. U kunt de beveiliging van uw AEM-instantie verhogen door de Dispatcher te gebruiken in combinatie met een webserver op bedrijfsniveau. Als u [Dispatcher](https://helpx.adobe.com/experience-manager/dispatcher/using/dispatcher-configuration.html)gebruikt, voert u de volgende configuraties voor AEM Forms uit:

1. Toegang voor AEM-formulieren configureren:

   Open het bestand dispatcher.any voor bewerking. Navigeer naar de filtersectie en voeg het volgende filter toe aan de filtersectie:

   `/0025 { /type "allow" /glob "* /bin/xfaforms/submitaction*" } # to enable AEM Forms submission`

   Sla het bestand op en sluit het. Raadpleeg de documentatie bij [Verzender](https://helpx.adobe.com/experience-manager/dispatcher/using/dispatcher-configuration.html)voor meer informatie over filters.

1. Configureer de referentiefilterservice:

   Meld u als beheerder aan bij het configuratiebeheer van Apache Felix. De standaard-URL van de configuratiemanager is https://&#39;server&#39;:[port_number]/system/console/configMgr. Selecteer in het menu **Configuraties** de optie **Filter** Apache-schuifverwijzing. Voer in het veld Hosts toestaan de hostnaam van de verzender in om het als referentie toe te staan en klik op **Opslaan**. De indeling van de invoer is https://&#39;[server]:[port]&#39;.

#### Adobe-doel integreren {#integrate-adobe-target}

Uw klanten zullen waarschijnlijk een interactieve mededeling verlaten als de ervaring het levert niet aansprekend is. Hoewel het voor de klanten frustrerend is, kan het het steunvolume en de kosten voor uw organisatie ook herstellen. Het is kritiek en uitdagend om de juiste klantenervaring te identificeren en te verstrekken die de omzettingssnelheid verhoogt. AEM-formulieren vormen de sleutel tot dit probleem.

AEM-formulieren worden geïntegreerd met Adobe Target, een Adobe Marketing Cloud-oplossing, om persoonlijke en boeiende ervaringen van klanten via meerdere digitale kanalen te bieden. Als u Adobe Target wilt gebruiken om interactieve communicatie aan te passen, [integreert u Adobe Target met AEM-formulieren](../../forms/using/ab-testing-adaptive-forms.md#setupandintegratetargetinaemforms).

#### SSL-communicatie configureren voor formuliergegevensmodel {#configure-ssl-communcation-for-form-data-model}

U kunt SSL-communicatie inschakelen voor het formuliergegevensmodel. Als u SSL-communicatie wilt inschakelen voor het formuliergegevensmodel, voegt u certificaten toe aan de Java Trust Store van alle exemplaren voordat u een AEM Forms-instantie start. U kunt de onderstaande opdracht uitvoeren om de certificaten toe te voegen:

`keytool -import -alias <alias-name> -file <pathTo .cer certificate file> -keystore <<pathToJRE>\lib\security\cacerts>`

## Volgende stappen {#next-steps}

U hebt een omgeving geconfigureerd voor het gebruik van de mogelijkheden voor interactieve communicatie en correspondentiebeheer. De volgende stappen zijn:

* [Overzicht van het correspondentiebeheer](/help/forms/using/interactive-communications-overview.md)

* [Een interactieve communicatie maken](../../forms/using/create-interactive-communication.md)

* [Een brief voor correspondentiebeheer maken](../../forms/using/create-letter.md)

