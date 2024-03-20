---
title: Prestaties van toepassingsservers verbeteren
description: In dit document worden optionele instellingen beschreven die u kunt configureren om de prestaties van de toepassingsserver voor AEM formulieren te verbeteren.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/maintaining_the_application_server
products: SG_EXPERIENCEMANAGER/6.5/FORMS
exl-id: 6e2f3d4c-2ead-45b3-98e7-32cacc7e2985
solution: Experience Manager, Experience Manager Forms
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '1870'
ht-degree: 0%

---

# Prestaties van toepassingsservers verbeteren{#enhancing-application-server-performance}

In deze inhoud worden optionele instellingen beschreven die u kunt configureren om de prestaties van de toepassingsserver voor AEM formulieren te verbeteren.

## Gegevensbronnen van toepassingsservers configureren {#configuring-application-server-data-sources}

AEM formulieren gebruiken de opslagplaats voor AEM formulieren als gegevensbron. De opslagplaats voor AEM formulieren slaat toepassingselementen op en bij uitvoering kunnen services elementen ophalen uit de opslagplaats als onderdeel van het voltooien van een geautomatiseerd bedrijfsproces.

Toegang tot de gegevensbron kan significant zijn, afhankelijk van het aantal AEM formuliermodules dat u gebruikt en het aantal gelijktijdige gebruikers dat de toepassing opent. De toegang van de gegevensbron kan worden geoptimaliseerd gebruikend verbinding het pooling. *Verbinding samenvoegen* Dit is een techniek die wordt gebruikt om de overhead van het maken van nieuwe databaseverbindingen te voorkomen telkens wanneer een toepassing of serverobject toegang tot de database vereist. Verbindingspooling wordt gewoonlijk gebruikt in web-based en ondernemingstoepassingen en wordt gewoonlijk behandeld door, maar niet beperkt tot, een toepassingsserver.

Het is belangrijk om uw parameters van de verbindingspool behoorlijk te vormen zodat u nooit uit verbindingen loopt, die toepassingsprestaties kunnen veroorzaken om te verslechteren.

Om de montages van de verbindingspool behoorlijk te vormen, is het belangrijk voor de beheerder van de toepassingsserver om de verbindingspool tijdens piekuren van de dag te controleren. De controle zorgt ervoor dat de voldoende verbindingen voor toepassingen en gebruikers te allen tijde beschikbaar zijn. De meeste toepassingsservers beschikken over controlegereedschappen.

U kunt diverse statistieken voor elke JDBC gegevensbroninstantie in uw domein controleren door de Console van het Beleid van de Server te gebruiken WebLogic. Raadpleeg de documentatie bij WebLogic voor meer informatie.

Wanneer de beheerder van de toepassingsserver de correcte montages van de verbindingspool bepaalt, moet die persoon deze informatie aan de gegevensbestandbeheerder meedelen. De gegevensbestandbeheerder heeft deze informatie nodig omdat het aantal gegevensbestandverbindingen het aantal verbindingen in de verbindingspool voor de gegevensbron evenaart. Voer vervolgens de stappen uit om de instellingen voor de verbindingspool voor uw toepassingsserver en het type gegevensbron te configureren, zoals hieronder wordt beschreven.

### Verbindingspoolinstellingen configureren voor WebLogic voor Oracle en MySQL {#configure-connection-pool-settings-for-weblogic-for-oracle-and-mysql}

1. Klik onder Domeinstructuur op Services > JDBC > Gegevensbronnen en klik in het rechterdeelvenster op IDP_DS.
1. Klik in het volgende scherm op het tabblad Configuratie > Verbindingspool en voer een waarde in de volgende vakken in:

   * Oorspronkelijke capaciteit
   * Maximale capaciteit
   * Capaciteitstoename
   * Cachegrootte instructie

1. Klik op Opslaan en vervolgens op Wijzigingen activeren.
1. Start WebLogic managed server opnieuw.

### Verbindingspoolinstellingen configureren voor WebLogic voor SQLServer {#configure-connection-pool-settings-for-weblogic-for-sqlserver}

1. Klik onder Midden wijzigen op Vergrendelen en bewerken.
1. Klik onder Domeinstructuur op Services > JDBC > Gegevensbronnen en klik in het rechterdeelvenster op EDC_DS.
1. Klik in het volgende scherm op het tabblad Configuratie > Verbindingspool en voer een waarde in de volgende vakken in:

   * Oorspronkelijke capaciteit
   * Maximale capaciteit
   * Capaciteitstoename
   * Cachegrootte instructie

1. Klik op Opslaan en vervolgens op Wijzigingen activeren.
1. Start WebLogic managed server opnieuw.

### Verbindingspool-instellingen voor WebSphere voor DB2 configureren {#configure-connection-pool-settings-for-websphere-for-db2}

1. Klik in de navigatiestructuur op Bronnen > JDBC > JDBC-providers. Klik in het rechterdeelvenster op de gegevensbron die u hebt gemaakt: DB2 Universal JDBC Driver Provider of LiveCycle - db2 - IDP_DS.
1. Klik onder Extra Eigenschappen op Gegevensbronnen en selecteer IDP_DS.
1. Klik in het volgende scherm onder Extra eigenschappen op Eigenschappen van Verbindingspool en voer een waarde in het vak Maximale verbindingen en Minimale verbindingen in.
1. Klik op OK of Toepassen en klik vervolgens op Direct opslaan naar hoofdconfiguratie.

### Verbindingspool-instellingen voor WebSphere voor Oracle configureren {#configure-connection-pool-settings-for-websphere-for-oracle}

1. Klik in de navigatiestructuur op Bronnen > JDBC > JDBC-providers. Klik in het rechterdeelvenster op de JDBC-gegevensbron voor het Oracle-stuurprogramma die u hebt gemaakt.
1. Klik onder Extra Eigenschappen op Gegevensbronnen en selecteer IDP_DS.
1. Klik in het volgende scherm onder Extra eigenschappen op Eigenschappen van Verbindingspool en voer een waarde in het vak Maximale verbindingen en Minimale verbindingen in.
1. Klik op OK of Toepassen en klik vervolgens op Direct opslaan naar hoofdconfiguratie.

### Verbindingspool-instellingen voor WebSphere voor SqlServer configureren {#configure-connection-pool-settings-for-websphere-for-sqlserver}

1. Klik in de navigatiestructuur op Bronnen > JDBC > JDBC-providers en klik in het rechterdeelvenster op de door de gebruiker gedefinieerde JDBC-gegevensbron voor stuurprogramma&#39;s die u hebt gemaakt.
1. Klik onder Extra Eigenschappen op Gegevensbronnen en selecteer IDP_DS.
1. Klik in het volgende scherm onder Extra eigenschappen op Eigenschappen van verbindingspool en voer een waarde in het vak Maximale verbindingen en Minimale verbindingen in:
1. Klik op OK of Toepassen en klik vervolgens op Direct opslaan naar hoofdconfiguratie.

## Inline documenten optimaliseren en invloed hebben op JVM-geheugen {#optimizing-inline-documents-and-impact-on-jvm-memory}

Als u doorgaans documenten van relatief kleine grootte verwerkt, kunt u de prestaties verbeteren die aan de overdrachtsnelheid en opslagruimte van het document zijn gekoppeld. Hiertoe implementeert u de volgende AEM productconfiguraties voor formulieren:

* Vergroot de standaardgrootte van inline-formulieren voor het document, zodat deze groter is dan de grootte van de meeste documenten.
* Voor het verwerken van grotere bestanden geeft u opslagmappen op die zich op een snelle-schijfsysteem of een RAM-schijf bevinden.

De maximale inlinegrootte en de opslagdirectory&#39;s (de map met tijdelijke bestanden voor AEM formulieren en de GDS-map) worden geconfigureerd in de beheerconsole.

### Documentgrootte en maximale inline-grootte {#document-size-and-maximum-inline-size}

Wanneer een document dat voor verwerking door AEM formulieren wordt verzonden kleiner is dan of gelijk is aan de standaardgrootte voor inline documenten, wordt het document inline opgeslagen op de server en wordt het document geserialiseerd als een Adobe Document-object. Het inline opslaan van documenten kan aanzienlijke prestatievoordelen hebben. Als u echter de formulierworkflow gebruikt, kan de inhoud ook in de database worden opgeslagen voor traceringsdoeleinden. Daarom kan het verhogen van de maximum gealigneerde grootte de gegevensbestandgrootte beïnvloeden.

Een document dat groter is dan de maximale inline-grootte wordt opgeslagen in het lokale bestandssysteem. Het object Document Adoben dat van en naar de server wordt overgedragen, is slechts een aanwijzer naar dat bestand.

Als documentinhoud is gealigneerd (dat wil zeggen, kleiner dan de maximale inlinegrootte), wordt de inhoud in de database opgeslagen als onderdeel van de serialisatielading van het document. Daarom kan het verhogen van de maximum gealigneerde grootte de gegevensbestandgrootte beïnvloeden.

**De maximale inline-grootte wijzigen**

1. Klik in de beheerconsole op Instellingen > Core System Settings > Configurations.
1. Voer een waarde in het vak Max. inline-grootte van standaarddocument in en klik op OK.

   >[!NOTE]
   >
   >De waarde van de eigenschap Max. inline grootte van document moet gelijk zijn voor AEM Forms in JEE-omgeving en AEM Forms in OSGi-bundel moet AEM Forms in JEE-omgeving bevatten. Met deze stappen werd alleen de waarde voor AEM Forms op JEE-omgeving bijgewerkt en niet voor AEM Forms op OSGi-bundel voor AEM Forms op JEE-omgeving.

1. Start de toepassingsserver opnieuw met de volgende systeemeigenschap:

   com.adobe.idp.defaultDocumentMaxInlineSize=`[value specified in Step 2]`

   >[!NOTE]
   >
   >De bovengenoemde systeemeigenschap negeert de waarde van de eigenschap Max Inline Size van het Document die is ingesteld voor AEM Forms op JEE-omgeving en AEM Forms op OSGi-bundel bevat AEM Forms op JEE-omgeving.

>[!NOTE]
>
>De standaard maximale inline grootte is 65536 bytes.

### Maximale heapgrootte voor JVM {#jvm-maximum-heap-size}

Als u de maximale inline-grootte verhoogt, hebt u meer geheugen nodig om de geserialiseerde documenten op te slaan. Daarom is in het algemeen ook een toename van de maximale heap-grootte van de JVM vereist.

Een zwaar geladen systeem dat vele documenten verwerkt kan snel het JVM heapgeheugen verzadigen. U voorkomt een OutOfMemoryError door de maximale heapgrootte van JVM te verhogen met een hoeveelheid die overeenkomt met de grootte van de inlinedocumenten vermenigvuldigd met het aantal documenten dat doorgaans op een bepaald moment wordt uitgevoerd.

Maximale toename van JVM voor heap = (grootte van inlinedocumenten) x (gemiddeld aantal verwerkte documenten).

**De maximale heapgrootte van JVM berekenen**

In dit voorbeeld is de huidige maximale JVM-heap ingesteld op 512 MB en de maximale inline-grootte is 64 KB. De server moet worden geconfigureerd voor het scenario waarin 10 taken tegelijkertijd worden uitgevoerd en elke taak 9 invoerbestanden en 1 resultaatbestand bevat (in totaal 10 bestanden per taak en 100 bestanden die tegelijkertijd worden verwerkt). Alle bestanden zijn kleiner dan 512 kB.

Als u alle bestanden inline wilt opslaan, stelt u de maximale inline-grootte in op ten minste 512 kB.

De vereiste toename van de maximale heap-grootte van de JVM wordt berekend met behulp van de volgende vergelijking:

(512 kB) x (100) = 51200 kB, of 50 MB

De maximale heapgrootte van JVM moet met 50 MB worden verhoogd voor een totaal van 562 MB.

**Samenvatting van heapfragmentatie**

Het plaatsen van de grootte van gealigneerde documenten aan grote waarden verhoogt het risico van een OutOfMemoryError op systemen die aan heapfragmentatie gevoelig zijn. Als u een document inline wilt opslaan, moet het JVM-heapgeheugen voldoende aaneengesloten ruimte hebben. Sommige besturingssystemen, JVM&#39;s en algoritmen voor het opruimen van ongewenste details zijn vatbaar voor heapfragmentatie. De fragmentatie vermindert de hoeveelheid aaneengesloten heapruimte en kan tot een OutOfMemoryError leiden zelfs wanneer voldoende totale vrije ruimte bestaat.

Bij eerdere bewerkingen op de toepassingsserver is de JVM-heap bijvoorbeeld gefragmenteerd gebleven en kan de afvalophaler de heap niet voldoende comprimeren om grote blokken vrije ruimte terug te winnen. Er kan een OutOfMemoryError optreden, ook al is de maximale heapgrootte van JVM aangepast voor een toename van de maximale inline-grootte.

Als u rekening wilt houden met heapfragmentatie, mag de grootte van het inlinedocument niet groter zijn dan 0,1% van de totale heapgrootte. Een JVM maximale heap-grootte van 512 MB kan bijvoorbeeld een maximale inline-grootte van 512 MB x 0,001 = 0,512 MB of 512 KB ondersteunen.

## Verbeteringen voor WebSphere-toepassingsserver {#websphere-application-server-enhancements}

Deze sectie beschrijft montages specifiek voor een milieu van de Server van de Toepassing WebSphere.

### Het maximale geheugen dat aan de JVM is toegewezen verhogen {#increasing-the-maximum-memory-allocated-to-the-jvm}

Als u de Manager van de Configuratie in werking stelt of probeert om Onderneming JavaBeans (EJB) te produceren, stel code door het nut van de bevellijn te gebruiken op *ejbopstellen* en er een OutOfMemory-fout optreedt, vergroot de hoeveelheid geheugen die aan de JVM is toegewezen.

1. Bewerk het JBImplementatiescript in het dialoogvenster *[appserver-hoofdmap]*/DeploymentTool/itp/ directory:

   * (Windows) `ejbdeploy.bat`
   * (Linux en UNIX) `ejbdeploy.sh`

1. Zoek de `-Xmx256M` en verander deze in een hogere waarde, zoals `-Xmx1024M`.
1. Sla het bestand op.
1. Voer de `ejbdeploy` bevel of herstelt gebruikend de Manager van de Configuratie.

## Windows Server 2003-prestaties verbeteren met LDAP {#improving-windows-server-2003-performance-with-ldap}

Deze inhoud beschrijft instellingen die specifiek zijn voor een Microsoft Windows Server 2003-besturingssysteemomgeving.

Het gebruiken van verbinding het groeperen op de onderzoeksverbinding kan het aantal havens nodig met wel 50% verminderen. Dit komt omdat die verbinding altijd dezelfde referenties gebruikt voor een bepaald domein en de context en verwante objecten expliciet worden gesloten.

### Vorm uw Server van Vensters voor verbinding het poolen {#configure-your-windows-server-for-connection-pooling}

1. Klik op Start > Uitvoeren om de registereditor te starten en typ in het vak Openen `regedit` en klik op OK.
1. Ga naar de registersleutel `HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\Tcpip\Parameters`
1. In de juiste ruit van de registratieredacteur, vind de TcpTimedWaitDelay waardenaam. Als de naam niet wordt weergegeven, kiest u Bewerken > Nieuw > DWORD-waarde in de menubalk om de naam toe te voegen.
1. Typ in het vak Naam `TcpTimedWaitDelay`

   >[!NOTE]
   >
   >Als er geen knipperende cursor wordt weergegeven en `New Value #` in het vak klikt u met de rechtermuisknop in het rechterdeelvenster, selecteert u Naam wijzigen en typt u in het vak Naam `TcpTimedWaitDelay`*.*

1. Herhaal stap 4 voor de waardenamen MaxUserPort, MaxHashTableSize en MaxFreeTcbs.
1. Dubbelklik in het rechterdeelvenster om de TcpTimedWaitDelay-waarde in te stellen. Selecteer Decimaal onder Basis en typ in het vak Waarde `30`.
1. Dubbelklik in het rechterdeelvenster om de waarde MaxUserPort in te stellen. Selecteer Decimaal onder Basis en typ in het vak Waarde `65534`.
1. Dubbelklik in het rechterdeelvenster om de waarde MaxHashTableSize in te stellen. Selecteer Decimaal onder Basis en typ in het vak Waarde `65536`.
1. Dubbelklik in het rechterdeelvenster om de waarde MaxFreeTcbs in te stellen. Selecteer Decimaal onder Basis en typ in het vak Waarde `16000`.

>[!NOTE]
>
>De ernstige problemen kunnen voorkomen als u het register verkeerd wijzigt door de Redacteur van de Registratie te gebruiken of door een andere methode te gebruiken. Voor deze problemen kan het nodig zijn het besturingssysteem opnieuw te installeren. Wijzig het register op eigen risico.
