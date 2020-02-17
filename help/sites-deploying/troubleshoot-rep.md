---
title: Problemen met replicatie oplossen
seo-title: Problemen met replicatie oplossen
description: Dit artikel biedt informatie over hoe u problemen met replicatie kunt oplossen.
seo-description: Dit artikel biedt informatie over hoe u problemen met replicatie kunt oplossen.
uuid: 1662bf60-b000-4eb2-8834-c6da607128fe
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: configuring
discoiquuid: 0d055be7-7189-4587-8c7c-2ce34e22a6ad
docset: aem65
translation-type: tm+mt
source-git-commit: 38ef8fc8d80009c8ca79aca9e45cf10bd70e1f1e

---


# Problemen met replicatie oplossen{#troubleshooting-replication}

Deze pagina biedt informatie over hoe u problemen met replicatie kunt oplossen.

## Probleem {#problem}

De replicatie (niet-omgekeerde replicatie) ontbreekt om één of andere reden.

## Resolutie {#resolution}

Er zijn diverse redenen voor replicatie om te ontbreken. In dit artikel wordt uitgelegd welke aanpak u kunt volgen bij het analyseren van deze kwesties.

**Worden replicaties überhaupt geactiveerd wanneer u op de knop Activeren klikt? Als NIET dan het volgende doet:**

1. Ga naar /crx/explorer en login als admin.
1. &quot;Content Explorer&quot; openen
1. Zie of bestaat een knoop /bin/replicate of /bin/replicate.json. Als het knooppunt bestaat, verwijdert u het en slaat u het op.

**Worden de replicaties omhoog een rij gevormd in de rijen van de replicatieagent?**

Controleer dit door naar /etc/replication/agents.author.html te gaan dan op de replicatieagenten klikken om te controleren.

**Als één agentenrij of een paar agentenrijen vast zijn:**

1. Geeft de wachtrij de status **geblokkeerd** weer? Zo ja, wordt de publicatie-instantie dan niet uitgevoerd of reageert deze niet volledig? Controleer de publicatie-instantie om te zien wat er mis is (controleer de logbestanden en controleer of er een OutOfMemory-fout of een ander probleem is. Dan als het slechts over het algemeen langzaam is, neem draaddumps en analyseer hen.
1. Geeft de wachtrijstatus aan dat de **wachtrij actief is - # in behandeling**? De replicatietaak kan in feite vastzitten in een socket die wordt gelezen en die wacht op de reactie van de publiciteit of de verzender. Dit zou kunnen betekenen dat de publicatie instantie of de verzender onder hoge lading of vastzit in een slot. Neem draaddumps van auteur en publiceer in dit geval.

   * Open de draaddumps van auteur in een analysator van de draadstortplaats, controleer of het toont dat de sling van de replicatieagent de gebeurtenisbaan in socketRead geplakt is.
   * Open de draaddumps van publiceren in een analysator van de draadstortplaats, analyseer wat zou kunnen veroorzaken publiceer instantie om niet te antwoorden. U zou een draad met POST /bin/receive in zijn naam moeten zien, die de draad is die de replicatie van auteur ontvangt.

**Als alle agentenrijen worden geplakt**

1. Het is mogelijk dat een bepaald stuk inhoud niet onder /var/replication/data kan in series worden vervaardigd toe te schrijven aan de corruptie van de bewaarplaats of een andere kwestie. Ga naar logs/error.log voor een verwante fout. Ga als volgt te werk om het slechte replicatiepunt te wissen:

   1. Ga naar https://&lt;host>:&lt;port>/crx/de en meld u aan als beheerder.
   1. Klik op &quot;Gereedschappen&quot; in het bovenste menu.
   1. Klik op de vergrootglasknop.
   1. Selecteer XPath als Type.
   1. Voer in het vak &quot;Query&quot; deze query/jcr:root/var/eventing/jobs//element(*,slingevent:Job)-volgorde in door @slingevent:created
   1. Klik op Zoeken
   1. In de resultaten zijn de bovenste items de meest recente sling-gebeurtenistaken. Klik op elke replicatie en zoek de geplakte replicaties die overeenkomen met wat boven in de wachtrij wordt weergegeven.

1. Er kan iets mis zijn met het sling van de baanrijen van het gebeurteniskader. Start de bundel org.apache.sling.event opnieuw in de map/system/console.
1. Het kan zijn dat de verwerking van werk volledig is uitgeschakeld. U kunt dat controleren onder Felix Console op het tabblad Gebeurtenis. Controleren of het scherm wordt weergegeven - Apache Sling Event (JOB PROCESSING IS UITGESCHAKELD!)

   * Als dat het geval is, schakelt u Apache Sling Job Event Handler in op het tabblad Configuration in Felix Console. Mogelijk is het selectievakje &#39;Taakverwerking ingeschakeld&#39; uitgeschakeld. Als dat wordt gecontroleerd en nog steeds wordt weergegeven dat &#39;taakverwerking is uitgeschakeld&#39;, controleert u of er sprake is van een overlay onder /apps/system/config die de taakverwerking uitschakelt. Probeer een osgi:config-knooppunt voor jobmanager.enabled met een booleaanse waarde voor true te maken en controleer opnieuw of de activering is gestart en er geen taken meer in de wachtrij staan.

1. Het zou ook het geval kunnen zijn dat de configuratie DefaultJobManager in een inconsistente staat krijgt. Dit kan gebeuren wanneer iemand handmatig de configuratie van de &#39;Apache Sling Job Event Handler&#39; wijzigt via de OSGiconsole (Schakel bijvoorbeeld de eigenschap &#39;Job Processing Enabled&#39; uit en schakel deze weer in en sla de configuratie op).

   * Op dit punt wordt de configuratie DefaultJobManager die in crx-quickstart/launchpad/config/org/apache/sling/event/impl/jobs/DefaultJobManager.config wordt opgeslagen in een inconsistente staat. En alhoewel het bezit van de Gebeurtenis van de Baan van de &quot;Apache het Verdelen van de Baan van de Gebeurtenis&quot;om in gecontroleerde staat toont te zijn toegelaten, wanneer men aan het Verschuivende lusje van de Gebeurtenis navigeert, toont het het bericht - DE VERWERKING VAN DE TAAK WORDT UITGESCHAKELD en de replicatie werkt niet.
   * Om deze kwestie op te lossen, zou men aan de pagina van de Configuratie van de console moeten navigeren OSGi en de &quot;Apache Sling Job Event Handler&quot;configuratie schrappen. Dan begin de Hoofdknoop van de cluster opnieuw om de configuratie terug in een verenigbare staat te krijgen. Dit zou de kwestie moeten bevestigen en de replicatie zal beginnen opnieuw te werken.

**Een replication.log maken**

Soms kan het zeer nuttig zijn om al replicatieregistreren te plaatsen om in een afzonderlijk logboekdossier op het niveau van DEBUG worden toegevoegd. Dit doet u als volgt:

1. Ga naar https://host:port/system/console/configMgr en meld u aan als beheerder.
1. Zoek de Apache Sling Logging Logger-fabriek en maak een instantie door op de knop **+** rechts van de fabrieksconfiguratie te klikken. Hiermee wordt een nieuw logbestand gemaakt.
1. Stel de configuratie als volgt in:

   * Logniveau:DEBUG
   * Pad logbestand: logs/replication.log
   * Categorieën: com.day.cq.replication

1. Als u vermoedt dat het probleem op enigerlei wijze te maken heeft met sling, kunt u dit Java-pakket ook toevoegen onder categorieën:org.apache.sling.event

## Wachtrij replicatieagent pauzeren {#pausing-replication-agent-queue}

Soms kan het geschikt zijn om de replicatiewachtrij te pauzeren om de belasting van het auteursysteem te verminderen zonder deze uit te schakelen. Momenteel is dit alleen mogelijk door een hack van het tijdelijk configureren van een ongeldige poort. Vanaf 5.4 kon u pauzeknoop in replicatieagentenrij zien het één of andere beperking heeft

1. De status blijft niet bestaan. Dit betekent dat als u een server opnieuw opstart of een replicatiebundel wordt gerecycled, de status weer actief wordt.
1. De pauze is nutteloos voor een kortere periode (OOB 1 uur na geen activiteiten met replicatie door andere draden) en niet voor een langere tijd. Omdat er een functie in sling is die nutteloze draden vermijdt. Controleer in feite of een thread voor een taakwachtrij langer ongebruikt is, als dit het geval is, of er opschoningscycli zijn. Als gevolg van het opschoonprogramma stopt het de verbinding en daardoor gaat de gepauzeerde instelling verloren. Aangezien de banen worden voortgeduurd stelt het een nieuwe draad in werking om de rij te verwerken die geen details van de gepauzeerde configuratie heeft. Vanwege deze wachtrij wordt deze status ingeschakeld.

## Paginamachtigingen worden niet herhaald bij activering van de gebruiker {#page-permissions-are-not-replicated-on-user-activation}

Paginamachtigingen worden niet gerepliceerd omdat ze worden opgeslagen onder de knooppunten waartoe toegang wordt verleend, niet met de gebruiker.

In het algemeen mogen paginamachtigingen niet door de auteur worden gerepliceerd om te publiceren en zijn ze niet standaard. Dit komt doordat toegangsrechten in deze twee omgevingen verschillend moeten zijn. Daarom wordt het geadviseerd om ACLs bij te vormen publiceer afzonderlijk van auteur.

## Replicatiereeks geblokkeerd tijdens replicatie van naamruimtegegevens van Auteur voor publiceren {#replication-queue-blocked-when-replicating-namespace-information-from-author-to-publish}

In sommige gevallen wordt de replicatiewachtrij geblokkeerd wanneer wordt geprobeerd naamruimtegegevens te repliceren van de auteurinstantie naar de publicatieinstantie. Dit gebeurt omdat de replicatiegebruiker geen `jcr:namespaceManagement` voorrecht heeft. Om dit probleem te voorkomen, moet u ervoor zorgen dat:

* De replicatiegebruiker (zoals gevormd onder het [Vervoer](/help/sites-deploying/replication.md#replication-agents-configuration-parameters) tab>Gebruiker) bestaat ook op de Publish instantie.
* De gebruiker heeft lees- en schrijfrechten op het pad waar de inhoud is geïnstalleerd.
* De gebruiker heeft `jcr:namespaceManagement` bevoegdheden op opslagniveau. U kunt deze bevoegdheid als volgt toekennen:

1. Meld u aan bij CRX/DE ( `https://localhost:4502/crx/de/index.jsp`) als beheerder.
1. Klik op het tabblad **Toegangsbeheer** .
1. Selecteer **Opslagplaats**.
1. Klik op Bericht **** toevoegen (het plusteken).
1. Voer de naam van de gebruiker in.
1. Select `jcr:namespaceManagement` from the privileges list.
1. Klik op OK.

