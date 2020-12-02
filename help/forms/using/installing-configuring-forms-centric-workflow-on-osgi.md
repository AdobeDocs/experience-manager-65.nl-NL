---
title: Forms-centric workflow op OSGi installeren en configureren
seo-title: Forms-centric workflow op OSGi installeren en configureren
description: Installeer en configureer AEM Forms Interactive Communications om zakelijke correspondentie, documenten, instructies, kennisgevingen van voordelen, marketingmails, facturen en welkomstkits te maken.
seo-description: Installeer en configureer AEM Forms Interactive Communications om zakelijke correspondentie, documenten, instructies, kennisgevingen van voordelen, marketingmails, facturen en welkomstkits te maken.
uuid: 1ceae822-215a-4b83-a562-4609a09c3a54
topic-tags: installing
discoiquuid: de292a19-07db-4ed3-b13a-7a2f1cd9e0dd
docset: aem65
translation-type: tm+mt
source-git-commit: 35b2c9c8c79b3cc3d81e0b92ea17cd7d599fa7ee
workflow-type: tm+mt
source-wordcount: '1623'
ht-degree: 0%

---


# Forms-centric workflow installeren en configureren op OSGi{#installing-and-configuring-forms-centric-workflow-on-osgi}

## Inleiding {#introduction}

Ondernemingen verzamelen en verwerken gegevens van meerdere formulieren, back-endsystemen en andere gegevensbronnen. De verwerking van gegevens omvat toetsings- en goedkeuringsprocedures, herhaalde taken en archivering van gegevens. Een formulier reviseren en converteren naar PDF-document. Wanneer manueel gedaan, kunnen de herhalende taken veel tijd en middelen vergen.

U kunt [Forms-centric workflow op OSGi](../../forms/using/aem-forms-workflow.md) gebruiken om snel adaptieve workflows op basis van formulieren te maken. Deze workflows kunnen u helpen bij het automatiseren van workflows voor revisie en goedkeuring, workflows voor bedrijfsprocessen en andere herhalende taken. Met deze workflows kunt u ook documenten verwerken (PDF-documenten maken, samenstellen, distribueren en archiveren, digitale handtekeningen toevoegen om de toegang tot documenten te beperken, gecodeerde formulieren decoderen en meer) en de Adobe Sign-handtekeningworkflow gebruiken voor formulieren en documenten.

Nadat de werkstromen zijn ingesteld, kunnen deze handmatig worden geactiveerd om een gedefinieerd proces te voltooien of via programmacode worden uitgevoerd wanneer gebruikers een formulier of interactieve communicatie verzenden. De mogelijkheid is opgenomen in het invoegpakket voor AEM Forms.

AEM Forms is een krachtig platform op bedrijfsniveau. Forms-gerichte workflow op OSGi is slechts een van de mogelijkheden van AEM Forms. Voor de volledige lijst van mogelijkheden, zie [Inleiding aan AEM Forms](introduction-aem-forms.md).

>[!NOTE]
>
>Met Forms-centric werkschema op OSGi, kunt u werkschema&#39;s voor diverse taken op de stapel snel bouwen en opstellen OSGi, zonder het moeten het volledige vermogen van het Beheer van het Proces op de stapel van JEE installeren. Zie een [vergelijking](capabilities-osgi-jee-workflows.md) van de Forms-centric AEM Workflows op OSGi en Process Management op JEE om het verschil en de gelijkenissen in de mogelijkheden te leren.
>
>Na de vergelijking, als u verkiest om de capaciteit van het Beheer van het Proces op de stapel van JEE te installeren, zie [AEM Forms op JEE](/help/forms/home.md) voor gedetailleerde informatie over installeren en het vormen van de stapel van JEE en de mogelijkheden van het Beheer van het Proces installeren.

## Implementatietopologie {#deployment-topology}

AEM Forms add-on package is een toepassing die op AEM wordt geïmplementeerd. U hebt slechts een minimum van één AEM-auteur of -verwerkingsinstantie (productieauteur) nodig om de Forms-centrische workflow op OSGi-functionaliteit uit te voeren. Een verwerkingsinstantie is een [geharde AEM Auteur](/help/forms/using/hardening-securing-aem-forms-environment.md) instantie. Voer geen daadwerkelijke ontwerpbewerkingen uit, zoals het maken van workflows of adaptieve formulieren, op de auteur van de productie.

De volgende topologie is indicatieve topologie om de Interactieve Mededelingen van AEM Forms, het Beheer van de Correspondentie, AEM Forms gegevensvangst, en Forms-Centric werkschema op mogelijkheden in werking te stellen OSGi. Voor gedetailleerde informatie over de topologie, zie [Architectuur en plaatsingstopologieën voor AEM Forms](/help/forms/using/aem-forms-architecture-deployment.md).

![aanbevolen topologie](assets/recommended-topology.png)

AEM Forms Forms-centric workflow op OSGi voert AEM interface uit voor het maken van het workflowmodel en AEM op de Author-instanties van AEM Forms.

## Systeemvereisten {#system-requirements}

>[!NOTE]
>
>Ga naar de sectie [Volgende stappen](../../forms/using/installing-configuring-forms-centric-workflow-on-osgi.md#next-steps) van het document als u AEM Forms al op OSGi hebt geïnstalleerd, zoals uitgelegd in het [artikel mogelijkheden voor het vastleggen van gegevens installeren en configureren](../../forms/using/installing-configuring-aem-forms-osgi.md).

Voordat u begint met het installeren en configureren van een op Forms gerichte workflow op OSGi, moet u ervoor zorgen dat:

* Hardware- en software-infrastructuur is aanwezig. Zie [technische vereisten](/help/sites-deploying/technical-requirements.md) voor een gedetailleerde lijst met ondersteunde hardware en software.

* Het installatiepad van de AEM-instantie bevat geen witruimten.
* Er wordt een AEM-instantie uitgevoerd. In AEM terminologie is een &quot;instantie&quot; een kopie van AEM die op een server in de auteur- of publicatiemodus wordt uitgevoerd. U hebt minstens één AEM (Auteur of Verwerking) nodig om een Forms-centric workflow op OSGi uit te voeren:

   * **Auteur**: Een AEM die wordt gebruikt om inhoud te maken, te uploaden en te bewerken en om de website te beheren. Wanneer de inhoud gereed is om live te gaan, wordt deze gekopieerd naar de publicatie-instantie.
   * **Verwerken:** Een verwerkingsinstantie is een  [verhard AEM ](/help/forms/using/hardening-securing-aem-forms-environment.md) Authorinstance. Nadat u de installatie hebt uitgevoerd, kunt u een instantie Auteur instellen en deze lastiger maken.

   * **Publiceren**: Een AEM instantie die de gepubliceerde inhoud via internet of een intern netwerk aan het publiek levert.

* Er wordt voldaan aan de geheugenvereisten. AEM Forms-add-on-pakket vereist:

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

## AEM Forms-invoegtoepassing installeren {#install-aem-forms-add-on-package}

AEM Forms add-on package is een toepassing die op AEM wordt geïmplementeerd. Het pakket bevat een op Forms gerichte workflow voor OSGi en andere mogelijkheden. Voer de volgende stappen uit om het invoegpakket te installeren:

1. Open [Softwaredistributie](https://experience.adobe.com/downloads). U hebt een Adobe ID nodig om u aan te melden bij de softwaredistributie.
1. Tik **[!UICONTROL Adobe Experience Manager]** beschikbaar in het koptekstmenu.
1. In de sectie **[!UICONTROL Filters]**:
   1. Selecteer **[!UICONTROL Forms]** in de vervolgkeuzelijst **[!UICONTROL Solution]**.
   2. Selecteer de versie en typ voor het pakket. U kunt de optie **[!UICONTROL Search Downloads]** ook gebruiken om de resultaten te filteren.
1. Tik op de pakketnaam die van toepassing is op het besturingssysteem, selecteer **[!UICONTROL Accept EULA Terms]** en tik **[!UICONTROL Download]**.
1. Open [Pakketbeheer](https://docs.adobe.com/content/help/en/experience-manager-65/administering/contentmanagement/package-manager.html) en klik **[!UICONTROL Upload Package]** om het pakket te uploaden.
1. Selecteer het pakket en klik **[!UICONTROL Install]**.

   U kunt het pakket ook downloaden via de directe koppeling die wordt vermeld in het [AEM Forms-release](https://helpx.adobe.com/aem-forms/kb/aem-forms-releases.html)-artikel.

1. Nadat het pakket is geïnstalleerd, wordt u gevraagd om de AEM opnieuw te starten. **Start de server niet onmiddellijk opnieuw.** Voordat u de AEM Forms-server stopt, wacht u tot de berichten ServiceEvent REGISTERED en ServiceEvent UNREGISTERED niet meer voorkomen in het bestand  [AEM-Installation-Directory]/crx-quickstart/logs/error.log en het logbestand stabiel is.
1. Herhaal stap 1-7 voor alle instanties Auteur en Publiceren.

## Configuratie {#post-installation-configurations} na installatie

AEM Forms heeft een paar verplichte en optionele configuraties. De verplichte configuraties omvatten het vormen bibliotheken BouncyCastle en serialization agent. De optionele configuraties zijn het configureren van dispatcher en Adobe Target.

### Verplichte configuraties na installatie {#mandatory-post-installation-configurations}

#### RSA- en BouncyCastle-bibliotheken configureren {#configure-rsa-and-bouncycastle-libraries}

Voer de volgende stappen op alle Auteur uit en publiceer instanties om de bibliotheken op te starten afvaardigen:

1. Stop de onderliggende AEM instantie.
1. Open de [AEM installatiemap]\crx-quickstart\conf\sling.properties.

   Als u [AEM installatiemap]\crx-quickstart\bin\start.bat hebt gebruikt om AEM te starten, bewerkt u vervolgens de sling.properties op [AEM_root]\crx-quickstart\.

1. Voeg de volgende eigenschappen toe aan het bestand sling.properties:

   ```shell
   sling.bootdelegation.class.com.rsa.jsafe.provider.JsafeJCE=com.rsa.*  
   ```

1. Sla het bestand op, sluit het en start het AEM.
1. Herhaal stap 1-4 voor alle instanties Auteur en Publiceren.

#### Vorm de rangschikkingsagent {#configure-the-serialization-agent}

Voer de volgende stappen uit op alle instanties Auteur en Publish om het pakket aan de lijst van gewenste personen toe te voegen:

1. Open AEM Configuration Manager in een browservenster. De standaard-URL is https://&#39;[server]:[port]&#39;/system/console/configMgr.
1. **Configuratie van deserialization Firewall** doorzoeken en openen.
1. Voeg het pakket **sun.util.agenda** toe aan het **veld lijst van gewenste personen**. Klik op Opslaan.
1. Herhaal stap 1-3 voor alle instanties Auteur en Publiceren.

### Optionele configuraties {#optional-post-installation-configurations} na installatie

#### Dispatcher {#configure-dispatcher} configureren

Dispatcher is een programma voor het in cache plaatsen en taakverdeling voor AEM. AEM Dispatcher helpt ook AEM server tegen aanvallen te beschermen. U kunt de veiligheid van uw AEM instantie verhogen door Dispatcher samen met een onderneming-klasse Webserver te gebruiken. Als u [Dispatcher](https://helpx.adobe.com/experience-manager/dispatcher/using/dispatcher-configuration.html) gebruikt, dan voer de volgende configuraties voor AEM Forms uit:

1. Toegang voor AEM Forms configureren:

   Open het bestand dispatcher.any voor bewerking. Navigeer naar de filtersectie en voeg het volgende filter toe aan de filtersectie:

   `/0025 { /type "allow" /glob "* /bin/xfaforms/submitaction*" } # to enable AEM Forms submission`

   Sla het bestand op en sluit het. Zie [Documentatie van Dispatcher](https://helpx.adobe.com/experience-manager/dispatcher/using/dispatcher-configuration.html) voor gedetailleerde informatie over filters.

1. Configureer de referentiefilterservice:

   Meld u als beheerder aan bij het configuratiebeheer van Apache Felix. De standaard-URL van de configuratiemanager is https://&#39;server&#39;:[port_number]/system/console/configMgr. Selecteer in het menu **Configuraties** de optie **Apache-schuifverwijzaarfilter**. Voer in het veld Hosts toestaan de hostnaam van de verzender in om het als referentie toe te staan en klik op **Opslaan**. De opmaak van de vermelding is `https://'[server]:[port]'`.

#### Cache {#configure-cache} configureren

Caching is een mechanisme om gegevenstoegang te verkorten, latentie te verminderen, en input/output (I/O) snelheden te verbeteren. In de cache van adaptieve formulieren worden alleen HTML-inhoud en JSON-structuur van een adaptief formulier opgeslagen zonder dat vooraf ingevulde gegevens worden opgeslagen. Hierdoor wordt de tijd die nodig is om een adaptief formulier te genereren, verkort.

* Als u de cache voor adaptieve formulieren gebruikt, gebruikt u [AEM Dispatcher](https://helpx.adobe.com/experience-manager/dispatcher/using/dispatcher-configuration.html) om clientbibliotheken (CSS en JavaScript) van een adaptief formulier in cache te plaatsen.
* Zorg tijdens het ontwikkelen van aangepaste componenten dat de cache van adaptieve formulieren uitgeschakeld blijft op de server die voor ontwikkeling wordt gebruikt.

Voer de volgende stappen uit om de cache voor adaptieve formulieren te configureren:

1. Ga naar AEM webconsoleconfiguratiebeheer op `https://'[server]:[port]'/system/console/configMgr`.
1. Klik **Adaptive Form Configuration Service** om de configuratiewaarden ervan te bewerken. Geef in het dialoogvenster Configuratiewaarden bewerken het maximumaantal formulieren of documenten op dat een instantie van de AEM Forms-server in cache kan plaatsen in het veld **Aantal Adaptieve Forms**. De standaardwaarde is 100. Klik **Opslaan**.

   >[!NOTE]
   >
   >Als u de cache wilt uitschakelen, stelt u de waarde in het veld Aantal adaptieve Forms in op **0**. De cache wordt opnieuw ingesteld en alle formulieren en documenten worden uit de cache verwijderd wanneer u de cachemonfiguratie uitschakelt of wijzigt.

#### Adobe Sign {#configure-adobe-sign} configureren

Adobe Sign maakt workflows voor e-handtekeningen mogelijk voor adaptieve formulieren. E-handtekeningen verbeteren workflows om documenten te verwerken voor juridische documenten, verkoop, salarisadministratie, personeelsbeheer en nog veel meer gebieden.

In een typisch Adobe Sign en Forms-centric werkschema op scenario OSGi, vult een gebruiker een adaptief vorm aan **aanvraag voor de dienst**. Bijvoorbeeld een creditcardaanvraag en een burgerservicepakket. Wanneer een gebruiker het aanvraagformulier invult, verzendt en ondertekent, wordt een workflow voor goedkeuring/afwijzing gestart. De serviceprovider controleert de toepassing in AEM Postvak In en gebruikt Adobe Sign om de toepassing elektronisch te ondertekenen. Als u vergelijkbare workflows voor elektronische handtekeningen wilt inschakelen, kunt u Adobe Sign integreren met AEM Forms.

Als u Adobe Sign wilt gebruiken met AEM Forms, [Integreer Adobe Sign met AEM Forms](../../forms/using/adobe-sign-integration-adaptive-forms.md).

## Volgende stappen {#next-steps}

U hebt een omgeving geconfigureerd voor het gebruik van een op Forms gerichte workflow met OSGi-mogelijkheden. De volgende stappen voor het gebruik van de mogelijkheid zijn:

* [Forms-centric workflow gebruiken op OSGi](../../forms/using/aem-forms-workflow.md)
* [Referentie workflowstap](/help/sites-developing/workflows-step-ref.md)
* [Nabewerking van brieven en interactieve communicatie](../../forms/using/submit-letter-topostprocess.md)

