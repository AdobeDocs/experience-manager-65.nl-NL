---
title: Forms-centric workflow op OSGi installeren en configureren
description: Installeer en configureer AEM Forms Interactive Communications om zakelijke correspondentie, documenten, instructies, kennisgevingen van voordelen, marketingmails, facturen en welkomstkits te maken.
topic-tags: installing
docset: aem65
role: Admin, User, Developer
exl-id: 4b24a38a-c1f0-4c81-bb3a-39ce2c4892b1
solution: Experience Manager, Experience Manager Forms
feature: Interactive Communication,AEM Forms on OSGi
source-git-commit: d7b9e947503df58435b3fee85a92d51fae8c1d2d
workflow-type: tm+mt
source-wordcount: '1601'
ht-degree: 0%

---

# Forms-centric workflow op OSGi installeren en configureren{#installing-and-configuring-forms-centric-workflow-on-osgi}

## Inleiding {#introduction}

Ondernemingen verzamelen en verwerken gegevens uit meerdere formulieren, back-endsystemen en andere gegevensbronnen. De verwerking van gegevens omvat beoordelings- en goedkeuringsprocedures, herhalende taken en gegevensarchivering. U kunt bijvoorbeeld een formulier reviseren en converteren naar een PDF-document. Wanneer u deze taken handmatig uitvoert, kunnen deze taken veel tijd en vele middelen in beslag nemen.

U kunt de op formulieren gebaseerde workflow op OSGi[&#128279;](../../forms/using/aem-forms-workflow.md) gebruiken om snel aanpasbare workflows op basis van formulieren te maken. Met deze workflows kunt u workflows voor revisie en goedkeuring, workflows voor bedrijfsprocessen en andere herhalende taken automatiseren. Met deze workflows kunt u ook gemakkelijker documenten verwerken (PDF-documenten maken, samenvoegen, distribueren en archiveren, digitale handtekeningen toevoegen om de toegang tot documenten te beperken, formulieren met streepjescodes decoderen en meer) en een Adobe Sign-ondertekeningsworkflow gebruiken met formulieren en documenten.

Nadat deze workflows zijn ingesteld, kunnen ze handmatig worden geactiveerd om een gedefinieerd proces te voltooien of om programmatisch uit te voeren wanneer gebruikers een formulier of interactieve communicatie verzenden. De functie is opgenomen in het AEM Forms-invoegtoepassingspakket.

AEM Forms is een krachtig platform op bedrijfsniveau. Forms-gerichte workflow op OSGi is slechts een van de mogelijkheden van AEM Forms. Voor de volledige lijst van mogelijkheden, zie [ Inleiding aan AEM Forms ](introduction-aem-forms.md).

>[!NOTE]
>
>Met de op formulieren gebaseerde workflow op OSGi kunt u snel workflows voor verschillende taken bouwen en implementeren op de OSGi-stapel, zonder dat u de volwaardige procesbeheerfunctie op de JEE-stapel hoeft te installeren. Bekijk een [vergelijking](capabilities-osgi-jee-workflows.md) van de op formulieren gebaseerde AEM-workflows op OSGi en Procesbeheer op JEE om meer te weten te komen over de verschillen en overeenkomsten tussen de mogelijkheden.
>
>Als u na de vergelijking de procesbeheerfunctie op de JEE-stapel wilt installeren, raadpleegt [u AEM-formulieren installeren of upgraden op JEE](/help/forms/using/introduction-aem-forms.md) voor meer informatie over het installeren en configureren van de JEE-stapel en de mogelijkheden voor procesbeheer.

## Distributietopologie {#deployment-topology}

AEM Forms add-on package is een toepassing die op AEM wordt geïmplementeerd. U vereist slechts een minimum van één AEM Auteur of van de Verwerking instantie (productieauteur) om de Forms-centric werkschema op vermogen OSGi in werking te stellen. Een verwerkingsinstantie is a [ verhard AEM ](/help/forms/using/hardening-securing-aem-forms-environment.md) instantie van de Auteur. Voer geen daadwerkelijke ontwerpbewerkingen uit, zoals het maken van workflows of adaptieve formulieren, op de auteur van de productie.

De volgende topologie is indicatieve topologie om de Interactieve Mededelingen van AEM Forms, het Beheer van de Correspondentie, AEM Forms gegevensvangst, en Forms-Centric werkschema op mogelijkheden in werking te stellen OSGi. Voor gedetailleerde informatie over de topologie, zie [ Architectuur en plaatsingstopologieën voor AEM Forms ](/help/forms/using/aem-forms-architecture-deployment.md).

![ geadviseerd-topologie ](assets/recommended-topology.png)

AEM Forms Forms-centric workflow op OSGi voert AEM interface uit voor het maken van het workflowmodel en AEM op de Author-instanties van AEM Forms.

## Systeemvereisten {#system-requirements}

>[!NOTE]
>
>Skip aan de [ Volgende stappen ](../../forms/using/installing-configuring-forms-centric-workflow-on-osgi.md#next-steps) sectie van het document, als u reeds AEM Forms op OSGi zoals die in [ wordt verklaard installeert en gegevens vormt vangt mogelijkheden ](../../forms/using/installing-configuring-aem-forms-osgi.md) artikel.

Voordat u begint met het installeren en configureren van een op Forms gerichte workflow op OSGi, moet u ervoor zorgen dat:

* Hardware- en software-infrastructuur is aanwezig. Voor een gedetailleerde lijst van gesteunde hardware en software, zie [ technische vereisten ](/help/sites-deploying/technical-requirements.md).

* Het installatiepad van de AEM-instantie bevat geen witruimten.
* Er wordt een AEM-instantie uitgevoerd. In AEM terminologie is een &quot;instantie&quot; een kopie van AEM die op een server in de auteur- of publicatiemodus wordt uitgevoerd. U hebt minstens één AEM (Auteur of Verwerking) nodig om een Forms-centric workflow op OSGi uit te voeren:

   * **Auteur**: Een AEM die instantie wordt gebruikt om, inhoud tot stand te brengen te uploaden en uit te geven en de website te beheren. Wanneer de inhoud gereed is om live te gaan, wordt deze gekopieerd naar de publicatie-instantie.
   * **Verwerking:** A verwerkingsinstantie is a [ gehard AEM ](/help/forms/using/hardening-securing-aem-forms-environment.md) instantie van de Auteur. Nadat u de installatie hebt uitgevoerd, kunt u een instantie Auteur instellen en deze lastiger maken.

   * **Publish**: Een AEM instantie die de gepubliceerde inhoud aan het publiek over Internet of een intern netwerk dient.

* Er wordt voldaan aan de geheugenvereisten. AEM Forms-add-on-pakket vereist:

   * 15 GB tijdelijke ruimte voor Microsoft Windows-installaties.
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

1. Open [ Distributie van de Software ](https://experience.adobe.com/downloads). U hebt een Adobe ID nodig om u aan te melden bij de softwaredistributie.
1. Selecteer **[!UICONTROL Adobe Experience Manager]** beschikbaar in het koptekstmenu.
1. In de sectie **[!UICONTROL Filters]** :
   1. Selecteer **[!UICONTROL Forms]** in de vervolgkeuzelijst **[!UICONTROL Solution]** .
   2. Selecteer de versie en typ voor het pakket. U kunt de optie **[!UICONTROL Search Downloads]** ook gebruiken om de resultaten te filteren.
1. Selecteer de pakketnaam die van toepassing is op het besturingssysteem, selecteer **[!UICONTROL Accept EULA Terms]** en selecteer **[!UICONTROL Download]** .
1. Open [ Manager van het Pakket ](https://experienceleague.adobe.com/docs/experience-manager-65/administering/contentmanagement/package-manager.html) en klik **[!UICONTROL Upload Package]** om het pakket te uploaden.
1. Selecteer het pakket en klik op **[!UICONTROL Install]**.

   U kunt het pakket ook downloaden via de directe koppeling in het [artikel over afstandsverklaringen](https://helpx.adobe.com/aem-forms/kb/aem-forms-releases.html) van AEM Forms.

1. Nadat het pakket is geïnstalleerd, wordt u gevraagd om de AEM-instantie opnieuw op te starten. **Start de server niet meteen opnieuw op.** Voordat u de AEM Forms-server stopt, moet u wachten totdat de GEREGISTREERDE ServiceEvent- en ServiceEvent UNREGISTERED-berichten niet meer voorkomen in het [bestand AEM-Installation-Directory]/crx-quickstart/logs/error.log en het logboek stabiel is.

   >[!NOTE]
   >
   > U kunt het beste de opdracht &#39;Ctrl + C&#39; gebruiken om de SDK opnieuw op te starten. Als u de AEM SDK opnieuw start met een alternatieve methode, bijvoorbeeld door Java-processen te stoppen, kan dit leiden tot inconsistenties in de AEM-ontwikkelomgeving.

1. Herhaal stap 1-7 voor alle auteur- en Publish-instanties.

## Post-installatieconfiguraties {#post-installation-configurations}

AEM Forms heeft een aantal verplichte en optionele configuraties. Tot de verplichte configuraties behoren de BouncyCastle-bibliotheken en de serienummeringsagent. Tot de optionele configuraties behoren de configuratie van Dispatcher en Adobe Target.

### Verplichte configuraties na de installatie {#mandatory-post-installation-configurations}

#### RSA- en BouncyCastle-bibliotheken configureren  {#configure-rsa-and-bouncycastle-libraries}

Voer de volgende stappen uit op alle instanties van de Auteur en van Publish om de bibliotheken te laars afgevaardigde:

1. Stop de onderliggende AEM instantie.
1. Open het [ AEM installatiefolder ] \crx-quickstart\conf\sling.properties- dossier voor het uitgeven.

   Als u [ AEM installatiemap ] \crx-quickstart\bin\start.bat gebruikte om AEM te beginnen, dan de sling.properties die bij [ AEM_root ] \ crx-quickstart \ wordt gevestigd uit te geven.

1. Voeg de volgende eigenschappen toe aan het bestand sling.properties:

   ```shell
   sling.bootdelegation.class.com.rsa.jsafe.provider.JsafeJCE=com.rsa.*  
   ```

1. Sla het bestand op, sluit het en start het AEM.
1. Herhaal stap 1-4 voor alle auteur- en Publish-instanties.

#### Vorm de rangschikkingsagent {#configure-the-serialization-agent}

Voer de volgende stappen uit op alle instanties van de Auteur en van Publish om het pakket aan de lijst van gewenste personen toe te voegen:

1. Open AEM Configuration Manager in een browservenster. Het gebrek URL is https://&#39; [ server ]:[ haven ]&#39;/system/console/configMgr.
1. Onderzoek en open **Configuratie van de Firewall 0&rbrace; Deserialization.**
1. Voeg het {**pakket 0} sun.util.endar aan het** lijst van gewenste personen **gebied toe.** Klik op Opslaan.
1. Herhaal stap 1-3 voor alle auteur- en Publish-instanties.

### Optionele configuraties na installatie {#optional-post-installation-configurations}

#### Dispatcher configureren {#configure-dispatcher}

Dispatcher is een hulpprogramma voor het in cache plaatsen en taakverdeling voor AEM. AEM Dispatcher helpt ook AEM server tegen aanvallen te beschermen. U kunt de veiligheid van uw AEM instantie verhogen door Dispatcher samen met een onderneming-klasse Webserver te gebruiken. Als u [ Dispatcher ](https://helpx.adobe.com/experience-manager/dispatcher/using/dispatcher-configuration.html) gebruikt, dan voer de volgende configuraties voor AEM Forms uit:

1. Toegang voor AEM Forms configureren:

   Open het bestand dispatcher.any voor bewerking. Navigeer naar de filtersectie en voeg het volgende filter toe aan de filtersectie:

   `/0025 { /type "allow" /glob "* /bin/xfaforms/submitaction*" } # to enable AEM Forms submission`

   Sla het bestand op en sluit het. Voor gedetailleerde informatie over filters, zie {de documentatie van 0} Dispatcher [&#128279;](https://helpx.adobe.com/experience-manager/dispatcher/using/dispatcher-configuration.html).

1. Configureer de referentiefilterservice:

   Meld u als beheerder aan bij Apache Felix. Standaard URL van de configuratiemanager is https://&#39;server&#39;:[ port_number ]/system/console/configMgr. In het **menu van Configuraties**, selecteer de **Apache het Verdelen van de Filter van de Verwijzing** optie. In het Allow gebied van Gastheren, ga gastheernaam van de verzender in om het als verwijzer toe te staan en klik **sparen**. De opmaak van de vermelding is `https://'[server]:[port]'` .

#### Cache configureren {#configure-cache}

Caching is een mechanisme om gegevenstoegang te verkorten, latentie te verminderen, en input/output (I/O) snelheden te verbeteren. In de cache van adaptieve formulieren worden alleen de HTML-inhoud en de JSON-structuur van een adaptief formulier opgeslagen zonder dat vooraf ingevulde gegevens worden opgeslagen. Hierdoor wordt de tijd die nodig is om een adaptief formulier te genereren, verkort.

* Bij het gebruiken van het adaptieve vormengeheime voorgeheugen, gebruik [ AEM Dispatcher ](https://helpx.adobe.com/experience-manager/dispatcher/using/dispatcher-configuration.html) om cliëntbibliotheken (CSS en JavaScript) van een adaptieve vorm in het voorgeheugen onder te brengen.
* Zorg tijdens het ontwikkelen van aangepaste componenten dat de cache van adaptieve formulieren uitgeschakeld blijft op de server die voor ontwikkeling wordt gebruikt.

Voer de volgende stappen uit om de cache voor adaptieve formulieren te configureren:

1. Ga naar AEM webconsoleconfiguratiebeheer op `https://'[server]:[port]'/system/console/configMgr` .
1. Klik op **[!UICONTROL Adaptive Form and Interactive Communication Web Channel Configuration]** om de configuratiewaarden ervan te bewerken. In geef de dialoog van de configuratiewaarden uit, specificeer het maximumaantal vormen of documenten een geval van de server van AEM Forms in het **Aantal van het AanpassingsForms** gebied in cache kan plaatsen. De standaardwaarde is 100. Klik **sparen**.

   >[!NOTE]
   >
   >Om het geheime voorgeheugen onbruikbaar te maken, plaats de waarde op het Aantal van het AanpassingsForms gebied aan **0**. De cache wordt opnieuw ingesteld en alle formulieren en documenten worden uit de cache verwijderd wanneer u de cachemonfiguratie uitschakelt of wijzigt.

#### Adobe Sign configureren {#configure-adobe-sign}

Adobe Sign maakt workflows voor e-handtekeningen mogelijk voor adaptieve formulieren. E-handtekeningen verbeteren workflows om documenten te verwerken voor juridische documenten, verkoop, salarisadministratie, personeelsbeheer en nog veel meer gebieden.

In een typisch Adobe Sign en Forms-centric werkschema op scenario OSGi, vult een gebruiker een adaptieve vorm aan **van toepassing is voor de dienst**. Bijvoorbeeld een creditcardaanvraag en een burgerservicepakket. Wanneer een gebruiker het aanvraagformulier invult, verzendt en ondertekent, wordt een workflow voor goedkeuring/afwijzing gestart. De serviceprovider controleert de toepassing in AEM Postvak In en gebruikt Adobe Sign om de toepassing elektronisch te ondertekenen. Als u vergelijkbare workflows voor elektronische handtekeningen wilt inschakelen, kunt u Adobe Sign integreren met AEM Forms.

Om Adobe Sign met AEM Forms te gebruiken, [ integreer Adobe Sign met AEM Forms ](../../forms/using/adobe-sign-integration-adaptive-forms.md).

## Volgende stappen {#next-steps}

U hebt een omgeving geconfigureerd voor het gebruik van een op Forms gerichte workflow met OSGi-mogelijkheden. De volgende stappen voor het gebruik van de mogelijkheid zijn:

* [Forms-centric workflow gebruiken op OSGi](../../forms/using/aem-forms-workflow.md)
* [Referentie workflowstap](/help/sites-developing/workflows-step-ref.md)
* [Post-verwerking van brieven en interactieve communicatie](../../forms/using/submit-letter-topostprocess.md)
