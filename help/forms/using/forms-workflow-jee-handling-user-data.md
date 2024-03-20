---
title: Forms JEE-workflows | Gebruikersgegevens verwerken
description: Leer hoe u AEM Forms JEE-workflows kunt gebruiken voor het ontwerpen, maken en beheren van bedrijfsprocessen.
topic-tags: grdp
products: SG_EXPERIENCEMANAGER/6.5/FORMS
role: Admin
exl-id: 847fa303-8d1e-4a17-b90d-5f9da5ca2d77
solution: Experience Manager, Experience Manager Forms
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '1379'
ht-degree: 0%

---

# Forms JEE-workflows | Gebruikersgegevens verwerken {#forms-jee-workflows-handling-user-data}

AEM Forms JEE-workflows bieden tools voor het ontwerpen, maken en beheren van bedrijfsprocessen. Een workflowproces bestaat uit een reeks stappen die in een opgegeven volgorde worden uitgevoerd. Elke stap voert een specifieke actie uit zoals het toewijzen van een taak aan een gebruiker of het verzenden van een e-mailbericht. Een proces kan met activa, gebruikersrekeningen, en de diensten in wisselwerking staan, en kan worden teweeggebracht gebruikend om het even welke volgende methodes:

* Een proces starten vanuit de AEM Forms Workspace
* De service SOAP of RESTful gebruiken
* Een adaptief formulier indienen
* Gecontroleerde map gebruiken
* E-mail gebruiken

Ga voor meer informatie over het maken van het AEM Forms JEE-workflowproces naar [Workbench Help](https://www.adobe.com/go/learn_aemforms_workbench_65).

## Gebruikersgegevens en gegevensopslag {#user-data-and-data-stores}

Wanneer een proces wordt geactiveerd en tijdens het proces worden gegevens over de deelnemers aan het proces, gegevens die door deelnemers zijn ingevoerd in het formulier dat aan het proces is gekoppeld, en bijlagen die aan het formulier zijn toegevoegd, vastgelegd. De gegevens worden opgeslagen in de AEM Forms JEE-serverdatabase en als deze zijn geconfigureerd, worden sommige gegevens zoals bijlagen opgeslagen in de GDS-map (Global Document Storage). De GDS-map kan worden geconfigureerd op een gedeeld bestandssysteem of een database.

## Gebruikersgegevens openen en verwijderen {#access-and-delete-user-data}

Wanneer een proces wordt geactiveerd, worden een unieke procesinstantie-id en een langlevende aanroepings-id gegenereerd en gekoppeld aan de procesinstantie. U kunt gegevens voor een procesinstantie openen en verwijderen op basis van de langlevende aanroepings-id. U kunt de langlevende aanroepingsID van een procesinstantie met de gebruikersnaam van de procesinitiatiefnemer of procesdeelnemers aftrekken die hun taken hebben voorgelegd.

U kunt de procesinstantie-id voor een initiator echter niet identificeren in de volgende scenario&#39;s:

* **Proces geactiveerd door een gecontroleerde map**: Een procesinstantie kan niet worden geïdentificeerd met de initiator als het proces wordt geactiveerd door een gecontroleerde map. In dit geval wordt de gebruikersinformatie gecodeerd in de opgeslagen gegevens.
* **Proces dat is gestart van AEM publicatie-instantie**: Alle procesinstanties die worden geactiveerd via AEM publicatie-instantie, leggen geen informatie over de initiator vast. Gebruikersgegevens kunnen echter worden vastgelegd in het formulier dat is gekoppeld aan het proces, dat is opgeslagen in workflowvariabelen.
* **Verwerking gestart via e-mail**: De e-mailid van de afzender wordt vastgelegd als een eigenschap in een ondoorzichtige blob-kolom van het dialoogvenster `tb_job_instance` databasetabel, die niet rechtstreeks kan worden opgevraagd.

### Id&#39;s van procesinstanties identificeren wanneer de aanvrager of deelnemer van de workflow bekend is {#initiator-participant}

Voer de volgende stappen uit zodat u procesinstantie-id&#39;s kunt identificeren voor een workflowaanvrager of een deelnemer:

1. Voer het volgende bevel in het gegevensbestand van de Server van AEM Forms uit om belangrijkste identiteitskaart voor werkschemageinitiator of deelnemer van terug te winnen `edcprincipalentity` databasetabel.

   ```sql
   select id from edcprincipalentity where canonicalname='user_ID'
   ```

   De vraag keert belangrijkste identiteitskaart voor gespecificeerde terug `user_ID`.

1. (**Voor workflowinitiator**) Voer het volgende bevel uit om alle taken verbonden aan belangrijkste identiteitskaart voor de initiatiefnemer van terug te winnen `tb_task` databasetabel.

   ```sql
   select * from tb_task where start_task = 1 and create_user_id= 'initiator_principal_id'
   ```

   De vraag keert taken terug die door gespecificeerd worden in werking gesteld `initiator`_ `principal_id`. De taken zijn van twee typen:

   * **Voltooide taken**: Deze taken zijn verzonden en geven een alfanumerieke waarde weer in het dialoogvenster `process_instance_id` veld. Neem nota van alle procesinstantie IDs voor voorgelegde taken en ga met de stappen verder.
   * **Taken die zijn gestart maar niet zijn voltooid**: Deze taken zijn gestart, maar nog niet ingediend. De waarde in het dialoogvenster `process_instance_id` veld voor deze taken is **0** (nul). Neem in dit geval nota van de overeenkomstige taak-id&#39;s en zie [Werken met wezen](#orphan).

1. (**Voor workflowdeelnemers**) Voer het volgende bevel uit om procesinstantie IDs terug te winnen verbonden aan belangrijkste identiteitskaart van de procesdeelnemer voor de initiatiefnemer van `tb_assignment` databasetabel.

   ```sql
   select distinct a.process_instance_id from tb_assignment a join tb_queue q on a.queue_id = q.id where q.workflow_user_id='participant_principal_id'
   ```

   De vraag keert instantie IDs voor alle processen verbonden aan de deelnemer, met inbegrip van die terug waar de deelnemer geen taak heeft voorgelegd.

   Neem nota van alle procesinstantie IDs voor voorgelegde taken en ga met de stappen verder.

   Voor verweesde taken of taken waarbij `process_instance_id` is 0 (nul), neem nota van overeenkomstige taak IDs en zie [Werken met wezen](#orphan).

1. Volg de instructies in [Gebruikersgegevens uit workflowinstanties wissen op basis van procesinstantie-id&#39;s](/help/forms/using/forms-workflow-jee-handling-user-data.md#purge) zodat kunt u gebruikersgegevens voor geïdentificeerde procesinstantie-id&#39;s verwijderen.

### Id&#39;s van procesinstanties identificeren wanneer gebruikersgegevens worden opgeslagen in primitieve variabelen {#primitive}

Een workflow kan zo worden ontworpen dat de gebruikersgegevens worden vastgelegd in een variabele die als een blob in de database wordt opgeslagen. In dergelijke gevallen kunt u alleen gebruikersgegevens opvragen als deze zijn opgeslagen in een van de volgende primitieve variabelen:

* **String**: Bevat de gebruikers-id direct of als een subtekenreeks en kan worden opgevraagd met SQL.
* **Numeriek**: Bevat de gebruikers-id.
* **XML**: Bevat de gebruikers-id als een subtekenreeks in de tekst die is opgeslagen als tekstkolommen in de database en kan worden opgevraagd als tekenreeksen.

Voer de volgende stappen uit zodat u kunt bepalen of een werkschema dat gegevens in primitieve-type variabelen opslaat gegevens voor de gebruiker bevat:

1. Voer de volgende databaseopdracht uit:

   ```sql
   select database_table from omd_object_type where name='pt_<app_name>/<workflow_name>'
   ```

   De query retourneert een tabelnaam in `tb_<number>` bestandsindeling voor de opgegeven toepassing ( `app_name`) en workflow ( `workflow_name`).

   >[!NOTE]
   >
   >De waarde van `name` Deze eigenschap kan complex zijn als de workflow in submappen in de toepassing is genest. Zorg ervoor dat u het exacte volledige pad naar de workflow opgeeft, dat u kunt ophalen via het menu `omd_object_type` databasetabel.

1. Controleer de `tb_<number>` tabelschema. De tabel bevat variabelen die gebruikersgegevens voor de opgegeven workflow opslaan. De variabelen in de tabel komen overeen met de variabelen in de workflow.

   Identificeer en neem nota van de variabele die aan werkschemavariabele beantwoordt die de gebruiker - identiteitskaart bevat Als de geïdentificeerde variabele van primitief-type is, kunt u een vraag in werking stellen om werkschemamonstanties te bepalen verbonden aan een gebruiker - identiteitskaart

1. Voer het volgende gegevensbestandbevel uit. In dit bevel, `user_var` is de variabele van het primitieve type die gebruiker - identiteitskaart bevat

   ```sql
   select process_instance_id from <tb_name> where <user_var>=<user_ID>
   ```

   De query retourneert alle procesinstantie-id&#39;s die zijn gekoppeld aan de opgegeven `user_ID`.

1. Volg de instructies in [Gebruikersgegevens uit workflowinstanties wissen op basis van procesinstantie-id&#39;s](/help/forms/using/forms-workflow-jee-handling-user-data.md#purge) zodat kunt u gebruikersgegevens voor geïdentificeerde procesinstantie-id&#39;s verwijderen.

### Gebruikersgegevens uit workflowinstanties wissen op basis van procesinstantie-id&#39;s {#purge}

Nu u de procesinstantie-id&#39;s hebt geïdentificeerd die aan een gebruiker zijn gekoppeld, gaat u als volgt te werk om gebruikersgegevens te verwijderen uit de respectieve procesinstanties.

1. Voer de volgende opdracht uit, zodat u de aanroepings-id en -status voor een procesinstantie van lange duur kunt ophalen via de knop `tb_process_instance` tabel.

   ```sql
   select long_lived_invocation_id, status from tb_process_instance where id='process_instance_id'
   ```

   De query retourneert de langlevende aanroepings-id en status voor de opgegeven `process_instance_id`.

1. Een instantie van het publiek maken `ProcessManager` client ( `com.adobe.idp.workflow.client.ProcessManager`) met een `ServiceClientFactory` instantie met de juiste verbindingsinstellingen.

   Zie Java™ API-naslaggids voor meer informatie voor [Class ProcessManager](https://helpx.adobe.com/experience-manager/6-3/forms/ProgramLC/javadoc/com/adobe/idp/workflow/client/ProcessManager.html).

1. Controleer de status van de workflowinstantie. Als de status anders is dan 2 (COMPLETE) of 4 (TERMINATED), beëindigt u de instantie eerst door de volgende methode aan te roepen:

   `ProcessManager.terminateProcess(<long_lived_invocation_id>)`.

1. Wis de werkstroominstantie door de volgende methode aan te roepen:

   `ProcessManager.purgeProcessInstance(<long_lived_invocation_id>)`

   De `purgeProcessInstance` Methode verwijdert alle gegevens voor de opgegeven oproepings-id volledig uit de AEM Forms Server-database en GDS, indien geconfigureerd.

### Werken met wezen {#orphan}

Orphan-taken zijn de taken waarvan het omvattende proces is gestart maar nog niet is ingediend. In dit geval worden de `process_instance_id` is **0** (nul). Daarom kunt u gebruikersgegevens die voor wezen taken worden opgeslagen niet volgen gebruikend procesinstantie IDs. Nochtans, kunt u het vinden gebruikend taakidentiteitskaart voor een wezen taak. U kunt de taken-id&#39;s identificeren vanuit de `tb_task` tabel voor een gebruiker, zoals beschreven in [Id&#39;s van procesinstanties identificeren wanneer de aanvrager of deelnemer van de workflow bekend is](/help/forms/using/forms-workflow-jee-handling-user-data.md#initiator-participant).

Als u de taak-id&#39;s hebt, voert u de volgende handelingen uit om de bijbehorende bestanden en gegevens te wissen met een wezen-taak uit GDS en de database.

1. Voer de volgende opdracht uit in de AEM Forms Server-database, zodat u id&#39;s voor de geïdentificeerde taak-id&#39;s kunt ophalen.

   ```sql
   select id from tb_form_data where task_id=<task_id>
   ```

   De query retourneert een lijst met id&#39;s. Voor elke id ( `fd_id`) geretourneerd in de resultaten, maakt u als volgt een lijst met sessie-id-tekenreeksen:

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

      1. Alle markeringsbestanden en andere bestanden met de exacte bestandsnaam verwijderen als `<file_name_guid>` uit het bestandssysteem.

   1. **GDS in database**

      Voer de volgende bevelen voor elke zitting-identiteitskaart uit:

      ```sql
      delete from tb_dm_chunk where documentid in (select documentid from tb_dm_session_reference where sessionid=<session_id>)
      delete from tb_dm_session_reference where sessionid=<session_id>
      delete from tb_dm_deletion where sessionid=<session_id>
      ```

1. Voer de volgende opdrachten uit, zodat u gegevens voor taak-id&#39;s kunt verwijderen uit de AEM Forms Server-database:

   ```sql
   delete from tb_task_acl where task_id=<task_id>
   delete from tb_task_attachment where task_id=<task_id>
   delete from tb_form_data where task_id=<task_id>
   delete from tb_assignment where task_id=<task_id>
   delete from tb_task where id=<task_id>
   ```
