---
title: Strategie voor back-up en herstel in een geclusterde omgeving
seo-title: Strategie voor back-up en herstel in een geclusterde omgeving
description: Als in uw AEM-formulierimplementatie aanvullende aangepaste gegevens worden opgeslagen in een andere database, moet u een strategie implementeren om een back-up van deze gegevens te maken, zodat deze synchroon blijven met de AEM-formuliergegevens.
seo-description: Als in uw AEM-formulierimplementatie aanvullende aangepaste gegevens worden opgeslagen in een andere database, moet u een strategie implementeren om een back-up van deze gegevens te maken, zodat deze synchroon blijven met de AEM-formuliergegevens.
uuid: c29b989c-30ed-4a8e-bab8-9b7746291a33
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/aem_forms_backup_and_recovery
products: SG_EXPERIENCEMANAGER/6.5/FORMS
discoiquuid: c332985b-4556-4056-961a-fce2356da88d
translation-type: tm+mt
source-git-commit: b703c59d7d913fc890c713c6e49e7d89211fd998
workflow-type: tm+mt
source-wordcount: '1519'
ht-degree: 0%

---


# Strategie voor back-up en herstel in een geclusterde omgeving {#strategy-for-backup-and-restore-in-a-clustered-environment}

>[!NOTE]
>
>Als in uw AEM-formulierimplementatie aanvullende aangepaste gegevens worden opgeslagen in een andere database, moet u een strategie implementeren om een back-up van deze gegevens te maken, zodat deze synchroon blijven met de AEM-formuliergegevens. Bovendien moet de toepassing zo zijn ontworpen dat deze robuust genoeg is om een scenario af te handelen waarbij de extra databases niet meer synchroon zijn. Het wordt hoogst geadviseerd dat om het even welke gegevensbestandverrichting die wordt uitgevoerd in de context van een transactie wordt gedaan helpen een verenigbare staat handhaven.

U moet een back-up maken van de volgende onderdelen van het AEM-formuliersysteem om te herstellen van een fout:

* Database dat wordt gebruikt door AEM-formulieren
* GDS met langlevende gegevens en andere permanente documenten
* AEM-database (crx-repository)

>[!NOTE]
>
>U moet een back-up maken van alle andere gegevens die door de instelling van AEM-formulieren worden gebruikt, zoals klankkettertypen, verbindingsgegevens enzovoort.

## Een back-up maken van een geclusterde omgeving {#back-up-a-clustered-environment}

In dit onderwerp worden de volgende strategieën besproken om een back-up te maken van alle AEM-formulieren in een geclusterde omgeving:

* Offline back-up met downtime
* Offlineback-up zonder downtime (back-up van een tweede knooppunt dat is afgesloten)
* Onlineback-up zonder downtime maar vertraging in reactie
* Een back-up maken van het Bootstrap-eigenschappenbestand

### Offline back-up met downtime {#offline-backup-with-downtime}

1. Sluit de volledige cluster en de verwante diensten. (zie [Starten en stoppen van services](/help/forms/using/admin-help/starting-stopping-services.md#starting-and-stopping-services))
1. Voor om het even welke knoop, file het gegevensbestand, GDS, en Connectors. (zie [Bestanden waarvan een back-up moet worden gemaakt en die moeten worden hersteld](/help/forms/using/admin-help/files-back-recover.md#files-to-back-up-and-recover))
1. Voer de volgende stappen uit om een back-up te maken van de AEM-opslagplaats offline:

   1. Maak voor elk clusterknooppunt een back-up van het bestand dat de id van het clusterknooppunt bevat.
   1. Maak een back-up van alle bestanden van een secundair clusterknooppunt, inclusief submappen.
   1. Maak een back-up van de opslagplaats/systeem-id van elk clusterknooppunt afzonderlijk.
   Zie [Back-up en herstel](https://docs.adobe.com/docs/en/crx/current/administering/backup_and_restore.html)voor gedetailleerde stappen.

1. Maak een back-up van andere gegevens, zoals klantertypen.
1. Start de cluster opnieuw.

### Offline back-up zonder downtime {#offline-backup-with-no-downtime}

1. Ga de het rollen reservewijze in. (zie [De back-upmodi](/help/forms/using/admin-help/backing-aem-forms-data.md#entering-the-backup-modes)invoeren)

   Merk op dat wij de het rollen reservewijze na een terugwinning moeten verlaten.

1. Sluit om het even welke secundaire knopen van de cluster met betrekking tot AEM. (zie [Starten en stoppen van services](/help/forms/using/admin-help/starting-stopping-services.md#starting-and-stopping-services))
1. Voor om het even welke knoop, file het gegevensbestand, GDS, en Connectors. (zie [Bestanden waarvan een back-up moet worden gemaakt en die moeten worden hersteld](/help/forms/using/admin-help/files-back-recover.md#files-to-back-up-and-recover))
1. Voer de volgende stappen uit om een back-up te maken van de AEM-opslagplaats offline:

   1. Maak voor elk clusterknooppunt een back-up van het bestand dat de id van het clusterknooppunt bevat.
   1. Maak een back-up van alle bestanden van een secundair clusterknooppunt, inclusief submappen.
   1. Maak een back-up van repository/system.id van elk clusterknooppunt afzonderlijk.
   Zie [Back-up en herstel](https://docs.adobe.com/docs/en/crx/current/administering/backup_and_restore.html)voor gedetailleerde stappen.

1. Maak een back-up van andere gegevens, zoals klantertypen.
1. Start de cluster opnieuw.

### Onlineback-up zonder downtime maar vertraging in reactie {#online-backup-with-no-downtime-but-delay-in-response}

1. Ga de het rollen reservewijze in. (zie [De back-upmodi](/help/forms/using/admin-help/backing-aem-forms-data.md#entering-the-backup-modes)invoeren)

   Let erop dat u de modus voor rolback-ups na een herstelbewerking moet verlaten.

1. Sluit om het even welke secundaire knopen van de cluster met betrekking tot AEM. (zie [Starten en stoppen van services](/help/forms/using/admin-help/starting-stopping-services.md#starting-and-stopping-services))
1. Voor om het even welke knoop, file het gegevensbestand, GDS, en Connectors. (zie [Bestanden waarvan een back-up moet worden gemaakt en die moeten worden hersteld](/help/forms/using/admin-help/files-back-recover.md#files-to-back-up-and-recover))
1. Voer de volgende stappen uit om online een back-up van de AEM-opslagruimte te maken:

   1. Maak voor elk clusterknooppunt een back-up van het bestand dat het bestand cluster_node.id bevat.
   1. Maak een back-up van repository/system.id van elk clusterknooppunt afzonderlijk.
   1. Neem op elk secundair knooppunt een online back-up van de opslagplaats voor gedetailleerde stappen. Zie Online back-up.

1. Maak een back-up van andere gegevens, zoals klantertypen.
1. Start de cluster opnieuw.

### Een back-up maken van het Bootstrap-eigenschappenbestand {#back-up-the-bootstrap-properties-file}

Wanneer we een AEM-cluster maken, wordt een eigenschappenbestand in de toepassingsserver voor alle secundaire knooppunten gemaakt. U wordt aangeraden een back-up te maken van het Bootstrap-eigenschappenbestand. U kunt het bestand op de volgende locatie op uw toepassingsserver vinden:

* JBoss: in de directory BIN
* WebLogic: in de domeinmap
* WebSphere: in de profielmap

U moet een back-up maken van het bestand voor het scenario voor noodherstel van het secundaire AEM-knooppunt en dit vervangen op de opgegeven locatie op de toepassingsserver, indien hersteld.

## Herstel in een geclusterde omgeving {#recovery-in-a-clustered-environment}

In het geval van een storing in de gehele cluster of een enkele node, moet u deze herstellen met behulp van de back-up.

Voor één enkele knoopterugwinning, moet u enkel de enige knoop sluiten en de enige procedure van de knoopterugwinning in werking stellen.

Als de volledige cluster mislukt als gevolg van fouten zoals een crash van de database, moet u de volgende stappen uitvoeren. Herstellen is afhankelijk van de gebruikte methode voor back-up.

### Eén knooppunt herstellen {#restoring-a-single-node}

1. Stop het corrupte knooppunt.

   >[!NOTE]
   >
   >Als het beschadigde knooppunt een primair AEM-knooppunt is, sluit u het gehele clusterknooppunt af.

1. Maak het fysieke systeem opnieuw op basis van een systeemafbeelding.
1. Pas patches of updates toe op AEM-formulieren die zijn toegepast sinds de afbeelding is gemaakt. Deze informatie werd geregistreerd tijdens de reserveprocedure. AEM-formulieren moeten op hetzelfde patchniveau worden hersteld als toen een back-up van het systeem werd gemaakt.
1. (*Optioneel*) Als alle andere knooppunten goed werken, is het mogelijk dat de AEM-opslagruimte ook beschadigd is. In dit geval ziet u een bericht dat de opslagplaats niet synchroniseert in het bestand error.log van de AEM-opslagplaats.

   Voer de volgende stappen uit om de opslagplaats te herstellen.

   >[!NOTE]
   >
   >Als er online een gecomprimeerde back-up van de crx-dataopslag is gemaakt, decomprimeert u deze op een willekeurige locatie en volgt u het proces voor offline herstel.

   1. Verwijder de directory&#39;s voor gegevensopslagruimte, gedeelde mappen, versies en werkruimten in de directory clusterNode van het knooppunt.
   1. Herstel de back-up van het clusterknooppunt (inclusief submappen) naar het knooppunt.
   1. Verwijder het bestand clusterNode/revision.log op het knooppunt.
   1. Verwijder de .lock op het knooppunt, indien aanwezig.
   1. Verwijder de map repository/system.id op het knooppunt, indien aanwezig.
   1. &amp;Bestandsnaam verwijderen;ast;&amp;ast;/listener.properties op het knooppunt, indien aanwezig.
   1. Herstel repository/cluster_node.id voor afzonderlijke clusterknooppunten.

>[!NOTE]
>
>Overweeg de volgende punten:

* Als het mislukte knooppunt een primair AEM-knooppunt was, kopieert u alle inhoud van de secundaire opslagmap (crx-repository\crx.0000, waarbij 0000 cijfers kunnen zijn) naar de crx-repository\ dataopslagmap en verwijdert u de secundaire repository-map.
* Voordat u een clusterknooppunt opnieuw start, moet u ervoor zorgen dat u de gegevensopslagruimte /clustered.txt van het primaire knooppunt verwijdert.
* Zorg ervoor dat het primaire knooppunt eerst wordt gestart en dat andere knooppunten worden gestart zodra het volledig is opgestart.

### De gehele cluster herstellen {#restoring-the-entire-cluster}

1. Stop alle clusterknooppunten.
1. Herstel het fysieke systeem van een systeembeeld.
1. Pas patches of updates toe op AEM-formulieren die zijn toegepast sinds de afbeelding is gemaakt. Deze informatie werd geregistreerd in stap 1 van de reserveprocedure. AEM-formulieren moeten op hetzelfde patchniveau worden hersteld als toen een back-up van het systeem werd gemaakt.
1. Herstel de database, GDS en Connectors.
1. Ga als volgt te werk om de AEM-opslagplaats offline te herstellen:

   >[!NOTE]
   >
   >Als er online een gecomprimeerde back-up van de crx-dataopslag is gemaakt, decomprimeert u deze op een willekeurige locatie en volgt u het proces voor offline herstel.

   1. Verwijder op alle clusterknooppunten de directory&#39;s repository, shared, version en workspaces in de clusterNode directory.
   1. Verwijder alle bestanden en mappen in de gedeelde map.
   1. Herstel de back-up van het clusterknooppunt (inclusief submappen) naar één clusterknooppunten.
   1. Kopieer alle bestanden van het herstelde clusterknooppunt naar alle andere clusterknooppunten. Zodra gedaan, bevat elke clusterknoop de zelfde gegevens.
   1. Verwijder het bestand clusterNode/revision.log op alle clusterknooppunten.
   1. Verwijder de .lock op alle clusterknooppunten, indien aanwezig.
   1. Verwijder de eventuele repository/system.id.
   1. De bestanden &amp;amp verwijderen;ast;&amp;ast;/listener.properties op alle clusterknooppunten, indien aanwezig.
   1. Herstel repository/cluster_node.id voor afzonderlijke clusterknooppunten.

>[!NOTE]
>
>Overweeg de volgende punten:

* Als het mislukte knooppunt een primair AEM-knooppunt was, kopieert u alle inhoud van de secundaire opslagmap (het ziet eruit als crx-repository\crx.0000, waarbij 0000 cijfers kunnen zijn) naar de opslagplaats crx-repository\.
* Voordat u een clusterknooppunt opnieuw start, moet u ervoor zorgen dat u de gegevensopslagruimte /clustered.txt van het primaire knooppunt verwijdert.
* Zorg ervoor dat het primaire knooppunt eerst wordt gestart en dat andere knooppunten worden gestart zodra het volledig is opgestart.

## Knooppunt voor het maken van back-ups en het herstellen van Correspondentenbeheeroplossingen {#back-up-and-restore-correspondence-management-solution-publish-node}

De uitgeversknoop heeft geen primair-secundaire verhouding in een gegroepeerde milieu. U kunt een back-up maken van elk Publisher-knooppunt door [Back-up en Herstellen](https://docs.adobe.com/docs/en/crx/current/administering/backup_and_restore.html)te volgen.

### Eén uitgeversknooppunt herstellen {#recover-a-single-publisher-node}

1. Sluit de knoop die moet worden teruggekregen en doe geen publicatieactiviteit tot de knoop opnieuw omhoog is.
1. Herstel het knooppunt Publiceren met Back-up [herstellen](https://docs.adobe.com/docs/en/crx/current/administering/backup_and_restore.html#Restoring de Back-up).

### Een cluster herstellen {#recover-a-cluster}

1. Sluit de cluster af.
1. Herstel het knooppunt Publiceren met Back-up [herstellen](https://docs.adobe.com/docs/en/crx/current/administering/backup_and_restore.html#Restoring de Back-up).
1. Start het primaire knooppunt gevolgd door het secundaire knooppunt van de auteurcluster.

