---
title: Forms JEE-workflows | Gebruikersgegevens verwerken
seo-title: Forms JEE-workflows | Gebruikersgegevens verwerken
description: Forms JEE-workflows | Gebruikersgegevens verwerken
uuid: 3b06ef19-d3c4-411e-9530-2c5d2159b559
topic-tags: grdp
products: SG_EXPERIENCEMANAGER/6.5/FORMS
discoiquuid: 5632a8df-a827-4e38-beaa-18b61c2208a3
translation-type: tm+mt
source-git-commit: a873cf3e7efd3bc9cd4744bf09078d9040efcdda
workflow-type: tm+mt
source-wordcount: '1371'
ht-degree: 0%

---


# Forms JEE-workflows | Gebruikersgegevens verwerken {#forms-jee-workflows-handling-user-data}

AEM Forms JEE-workflows bieden tools voor het ontwerpen, maken en beheren van bedrijfsprocessen. Een workflowproces bestaat uit een reeks stappen die in een opgegeven volgorde worden uitgevoerd. Elke stap voert een specifieke actie uit zoals het toewijzen van een taak aan een gebruiker of het verzenden van een e-mailbericht. Een proces kan met activa, gebruikersrekeningen, en de diensten in wisselwerking staan, en kan worden teweeggebracht gebruikend om het even welke volgende methodes:

* Een proces starten vanuit de AEM Forms Workspace
* De service SOAP of RESTful gebruiken
* Een adaptief formulier indienen
* Gecontroleerde map gebruiken
* E-mail gebruiken

Raadpleeg de Help bij [Workbench voor meer informatie over het maken van een AEM Forms JEE-workflowproces](http://www.adobe.com/go/learn_aemforms_workbench_65).

## Gebruikersgegevens en gegevensopslag {#user-data-and-data-stores}

Wanneer een proces wordt geactiveerd en tijdens het proces worden gegevens vastgelegd over de deelnemers aan het proces, gegevens die door deelnemers zijn ingevoerd in het formulier dat aan het proces is gekoppeld en bijlagen die aan het formulier zijn toegevoegd. De gegevens worden opgeslagen in de AEM Forms JEE-serverdatabase en als deze zijn geconfigureerd, worden sommige gegevens zoals bijlagen opgeslagen in de GDS-map (Global Document Storage). De GDS-map kan worden geconfigureerd op een gedeeld bestandssysteem of een database.

## Gebruikersgegevens openen en verwijderen {#access-and-delete-user-data}

Wanneer een proces wordt geactiveerd, worden een unieke procesinstantie-id en een langlevende aanroepings-id gegenereerd en gekoppeld aan de procesinstantie. U kunt gegevens voor een procesinstantie openen en verwijderen op basis van de langlevende aanroepings-id. U kunt de langlevende aanroepingsID van een procesinstantie met de gebruikersnaam van de procesinitiatiefnemer of procesdeelnemers aftrekken die hun taken hebben voorgelegd.

U kunt de procesinstantie-id voor een initiator echter niet identificeren in de volgende scenario&#39;s:

* **Het proces wordt geactiveerd door een gecontroleerde map**: Een procesinstantie kan niet met de initiator worden geïdentificeerd als het proces door een gecontroleerde omslag wordt teweeggebracht. In dit geval wordt de gebruikersinformatie gecodeerd in de opgeslagen gegevens.
* **Proces dat is gestart vanaf AEM publicatie-instantie**: Alle procesinstanties die worden geactiveerd via AEM publicatieinstantie, leggen geen informatie over de initiator vast. Gebruikersgegevens kunnen echter worden vastgelegd in het formulier dat is gekoppeld aan het proces, dat is opgeslagen in workflowvariabelen.
* **Verwerking gestart via e-mail**: De e-mailid van de afzender wordt vastgelegd als een eigenschap in een ondoorzichtige blob-kolom van de `tb_job_instance` databasetabel, die niet rechtstreeks kan worden gecontroleerd.

### Id&#39;s van procesinstanties identificeren wanneer de aanvrager of deelnemer van de workflow bekend is {#initiator-participant}

Voer de volgende stappen uit om procesinstantie-id&#39;s voor een workflowaanvrager of een deelnemer te identificeren:

1. Voer het volgende bevel in het servergegevensbestand van AEM Forms uit om belangrijkste identiteitskaart voor werkschemamonator of deelnemer van de `edcprincipalentity` gegevensbestandlijst terug te winnen.

   ```sql
   select id from edcprincipalentity where canonicalname='user_ID'
   ```

   De vraag keert belangrijkste identiteitskaart voor gespecificeerde terug `user_ID`.

1. (**Voor werkstroominitiator**) Voer het volgende bevel uit om alle taken verbonden aan belangrijkste identiteitskaart voor de initiatiefnemer van de `tb_task` gegevensbestandlijst terug te winnen.

   ```sql
   select * from tb_task where start_task = 1 and create_user_id= 'initiator_principal_id'
   ```

   De vraag keert taken terug die door gespecificeerde `initiator`_ `principal_id`worden in werking gesteld. De taken zijn van twee typen:

   * **Voltooide taken**: Deze taken zijn verzonden en geven een alfanumerieke waarde weer in het `process_instance_id` veld. Neem nota van alle procesinstantie IDs voor voorgelegde taken en ga met de stappen verder.
   * **Gestarte maar niet voltooide** taken: Deze taken zijn begonnen maar nog niet ingediend. De waarde in het `process_instance_id` veld voor deze taken is **0** (nul). In dit geval, neem nota van overeenkomstige taak IDs en zie [Werk met wezen taken](#orphan).

1. (**Voor werkschemadeelnemers**) voer het volgende bevel uit om procesinstantie IDs terug te winnen verbonden aan belangrijkste identiteitskaart van de procesdeelnemer voor de initiatiefnemer van de `tb_assignment` gegevensbestandlijst.

   ```sql
   select distinct a.process_instance_id from tb_assignment a join tb_queue q on a.queue_id = q.id where q.workflow_user_id='participant_principal_id'
   ```

   De vraag keert instantie IDs voor alle processen verbonden aan de deelnemer, met inbegrip van die terug waar de deelnemer geen taak heeft voorgelegd.

   Neem nota van alle procesinstantie IDs voor voorgelegde taken en ga met de stappen verder.

   Voor verweesde taken of taken waar 0 (nul) `process_instance_id` is, neem nota van overeenkomstige taak IDs en zie het [Werk met verweesde taken](#orphan).

1. Volg de instructies in [Leegmaken gebruikersgegevens van werkschemamonstanties die op de sectie van procesinstantie IDs](/help/forms/using/forms-workflow-jee-handling-user-data.md#purge) worden gebaseerd om gebruikersgegevens voor geïdentificeerde procesinstantie IDs te schrappen.

### Id&#39;s van procesinstanties identificeren wanneer gebruikersgegevens worden opgeslagen in primitieve variabelen {#primitive}

Een workflow kan zo worden ontworpen dat de gebruikersgegevens worden vastgelegd in een variabele die als een blob in de database wordt opgeslagen. In dergelijke gevallen kunt u alleen gebruikersgegevens opvragen als deze zijn opgeslagen in een van de volgende primitieve variabelen:

* **Tekenreeks**: Bevat de gebruiker - identiteitskaart direct of als substring en kan worden gevraagd gebruikend SQL.
* **Numeriek**: Bevat de gebruikersnaam rechtstreeks.
* **XML**: Bevat de gebruikers-id als een subtekenreeks in de tekst die is opgeslagen als tekstkolommen in de database en kan worden opgevraagd als tekenreeksen.

Voer de volgende stappen uit om te bepalen of een werkschema dat gegevens in primitieve-type variabelen opslaat gegevens voor de gebruiker bevat:

1. Voer de volgende databaseopdracht uit:

   ```sql
   select database_table from omd_object_type where name='pt_<app_name>/<workflow_name>'
   ```

   De query retourneert een tabelnaam in de `tb_<number>` indeling voor de opgegeven toepassing ( `app_name`) en workflow ( `workflow_name`).

   >[!NOTE]
   >
   >De waarde van de `name` eigenschap kan complex zijn als de workflow in submappen in de toepassing is genest. Zorg ervoor dat u het exacte volledige pad naar de workflow opgeeft, dat u kunt ophalen uit de `omd_object_type` databasetabel.

1. Controleer het `tb_<number>` tabelschema. De tabel bevat variabelen die gebruikersgegevens voor de opgegeven workflow opslaan. De variabelen in de tabel komen overeen met de variabelen in de workflow.

   Identificeer en neem nota van de variabele die aan werkschemavariabele beantwoordt die de gebruiker - identiteitskaart bevat Als de geïdentificeerde variabele van primitief-type is, kunt u een vraag in werking stellen om werkschemamonstanties te bepalen verbonden aan een gebruiker - identiteitskaart

1. Voer het volgende gegevensbestandbevel uit. In dit bevel, `user_var` is de primitieve-type variabele die gebruiker - identiteitskaart bevat

   ```sql
   select process_instance_id from <tb_name> where <user_var>=<user_ID>
   ```

   De query retourneert alle procesinstantie-id&#39;s die aan de opgegeven id zijn gekoppeld `user_ID`.

1. Volg de instructies in [Leegmaken gebruikersgegevens van werkschemamonstanties die op de sectie van procesinstantie IDs](/help/forms/using/forms-workflow-jee-handling-user-data.md#purge) worden gebaseerd om gebruikersgegevens voor geïdentificeerde procesinstantie IDs te schrappen.

### Gebruikersgegevens uit workflowinstanties wissen op basis van procesinstantie-id&#39;s {#purge}

Nu u de procesinstantie-id&#39;s hebt geïdentificeerd die aan een gebruiker zijn gekoppeld, gaat u als volgt te werk om gebruikersgegevens te verwijderen uit de respectieve procesinstanties.

1. Voer het volgende bevel uit om langlevende aanroepingsID en status voor een procesinstantie van de `tb_process_instance` lijst terug te winnen.

   ```sql
   select long_lived_invocation_id, status from tb_process_instance where id='process_instance_id'
   ```

   De query retourneert de langlevende aanroepings-id en status voor de opgegeven `process_instance_id`.

1. Maak een instantie van de openbare `ProcessManager` client ( `com.adobe.idp.workflow.client.ProcessManager`) met een `ServiceClientFactory` instantie met de juiste verbindingsinstellingen.

   Zie Java API-naslaggids voor [Class ProcessManager](https://helpx.adobe.com/experience-manager/6-3/forms/ProgramLC/javadoc/com/adobe/idp/workflow/client/ProcessManager.html)voor meer informatie.

1. Controleer de status van de workflowinstantie. Als de status anders is dan 2 (COMPLETE) of 4 (TERMINATED), beëindigt u de instantie eerst door de volgende methode aan te roepen:

   `ProcessManager.terminateProcess(<long_lived_invocation_id>)`.

1. Wis de werkstroominstantie door de volgende methode aan te roepen:

   `ProcessManager.purgeProcessInstance(<long_lived_invocation_id>)`

   De `purgeProcessInstance` methode verwijdert alle gegevens voor de opgegeven oproepings-id volledig uit de AEM Forms-serverdatabase en GDS, indien geconfigureerd.

### Werken met wezen {#orphan}

Orphan-taken zijn de taken waarvan het omvattende proces is gestart maar nog niet is ingediend. in dit geval `process_instance_id` is de waarde **0** (nul). Daarom kunt u gebruikersgegevens die voor wezen taken worden opgeslagen niet volgen gebruikend procesinstantie IDs. Nochtans, kunt u het vinden gebruikend taakidentiteitskaart voor een wezen taak. U kunt de taken-id&#39;s van de `tb_task` tabel voor een gebruiker identificeren, zoals wordt beschreven in Id&#39;s van [procesinstanties identificeren wanneer de aanvrager of deelnemer van de workflow bekend](/help/forms/using/forms-workflow-jee-handling-user-data.md#initiator-participant)is.

Als u de taak-id&#39;s hebt, voert u de volgende handelingen uit om de bijbehorende bestanden en gegevens te wissen met een wezen-taak uit GDS en de database.

1. Voer het volgende bevel op het servergegevensbestand van AEM Forms uit om identiteitskaarts voor geïdentificeerde taak IDs terug te winnen.

   ```sql
   select id from tb_form_data where task_id=<task_id>
   ```

   De query retourneert een lijst met id&#39;s. Voor elke id ( `fd_id`) die in de resultaten wordt geretourneerd, maakt u als volgt een lijst met sessie-id-tekenreeksen:

   * _ `wfattach<task_id>`
   * `_wftask<fd_id>`
   * `_wftaskformid<fd_id>`

1. Voer een van de volgende stappen uit, afhankelijk van het feit of uw GDS naar een bestandssysteem of database verwijst:

   1. **GDS in bestandssysteem**

      In het GDS-bestandssysteem:

      1. Zoek naar dossiers met de volgende koorden van zitting ID als hun uitbreidingen:
      * `_wfattach<task_id>`
      * `_wftask<fd_id>`
      * `_wftaskformid<fd_id>`

      De bestanden met deze extensies zijn de markeringsbestanden. Ze worden opgeslagen met bestandsnamen in de volgende indeling:

      `<file_name_guid>.session<session_id_string>`

      1. Verwijder alle markeringsbestanden en andere bestanden met exact dezelfde bestandsnaam als `<file_name_guid>` uit het bestandssysteem.
   1. **GDS in database**

      Voer de volgende bevelen voor elke zitting-identiteitskaart uit:

      ```sql
      delete from tb_dm_chunk where documentid in (select documentid from tb_dm_session_reference where sessionid=<session_id>)
      delete from tb_dm_session_reference where sessionid=<session_id>
      delete from tb_dm_deletion where sessionid=<session_id>
      ```




1. Voer de volgende opdrachten uit om gegevens voor taak-id&#39;s te verwijderen uit de AEM Forms-serverdatabase:

   ```sql
   delete from tb_task_acl where task_id=<task_id>
   delete from tb_task_attachment where task_id=<task_id>
   delete from tb_form_data where task_id=<task_id>
   delete from tb_assignment where task_id=<task_id>
   delete from tb_task where id=<task_id>
   ```

