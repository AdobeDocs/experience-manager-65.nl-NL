---
title: Back-upstrategieën voor gecontroleerde mappen
seo-title: Back-upstrategieën voor gecontroleerde mappen
description: In dit document wordt beschreven hoe gecontroleerde mappen worden beïnvloed door verschillende scenario's voor back-up en herstel, de beperkingen en resultaten van deze scenario's en hoe gegevensverlies tot een minimum kan worden beperkt.
seo-description: In dit document wordt beschreven hoe gecontroleerde mappen worden beïnvloed door verschillende scenario's voor back-up en herstel, de beperkingen en resultaten van deze scenario's en hoe gegevensverlies tot een minimum kan worden beperkt.
uuid: c61997b8-6c36-4bd9-90e5-411841a6c176
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/aem_forms_backup_and_recovery
products: SG_EXPERIENCEMANAGER/6.5/FORMS
discoiquuid: 6f775933-e989-4456-ad01-9bdf5dee3dad
translation-type: tm+mt
source-git-commit: 2cf9dcf2e9cf71c54e19e2c6ee825c9a8f00a9b7

---


# Back-upstrategieën voor gecontroleerde mappen {#backup-strategies-for-watched-folders}

Deze inhoud beschrijft hoe gecontroleerde omslagen door verschillende steun en terugwinningsscenario&#39;s, de beperkingen en de resultaten van deze scenario&#39;s worden beïnvloed, en hoe te om gegevensverlies te minimaliseren.

*Gecontroleerde map* is een bestandssysteemtoepassing die geconfigureerde servicebewerkingen aanroept waarmee het bestand in een van de volgende mappen in de controlemahiërarchie wordt gemanipuleerd:

* Invoer
* Werkgebied
* Uitvoer
* Mislukt
* Behouden

Een gebruiker of cliënttoepassing laat eerst het dossier of de omslag in de inputomslag vallen. Vervolgens wordt het bestand door de servicebewerking naar de werkgebiedmap verplaatst voor verwerking. Nadat de service de opgegeven bewerking heeft uitgevoerd, wordt het gewijzigde bestand opgeslagen in de uitvoermap. Verwerkte bronbestanden zijn verplaatst naar de map preserve en mislukte verwerkingsbestanden worden verplaatst naar de map met foutmeldingen. Wanneer het `Preserve On Failure` kenmerk voor de gecontroleerde map is ingeschakeld, worden mislukte verwerkte bronbestanden naar de map preserve verplaatst. (Zie [Gecontroleerde mapeindpunten](/help/forms/using/admin-help/configuring-watched-folder-endpoints.md#configuring-watched-folder-endpoints)configureren.)

U kunt een back-up maken van gecontroleerde mappen door een back-up van het bestandssysteem te maken.

>[!NOTE]
>
>Deze back-up is onafhankelijk van het back-up- en herstelproces van de database of documentopslag.

## Hoe gecontroleerde mappen werken {#how-watched-folders-work}

Met deze inhoud wordt het bewerkingsproces voor gecontroleerde mappen beschreven. Het is belangrijk dat we dit proces begrijpen voordat we een herstelplan ontwikkelen. In dit voorbeeld wordt het `Preserve On Failure` kenmerk voor de gecontroleerde map ingeschakeld. De bestanden worden verwerkt in de volgorde waarin ze aankomen.

In de volgende tabel wordt beschreven hoe vijf voorbeeldbestanden (file1, file2, file3, file4, file5) gedurende het proces worden bewerkt. In de tabel vertegenwoordigt de x-as tijd, zoals Tijd 1 of T1, en vertegenwoordigt de y-as mappen binnen de gecontroleerde maphiërarchie, zoals Invoer.

<table>
 <thead>
  <tr>
   <th><p>Map</p></th>
   <th><p>T1</p></th>
   <th><p>T2</p></th>
   <th><p>T3</p></th>
   <th><p>T4</p></th>
   <th><p>T5</p></th>
   <th><p>T6</p></th>
   <th><p>T7</p></th>
  </tr>
 </thead>
 <tbody>
  <tr>
   <td><p>Invoer</p></td>
   <td><p>file1, file2, file3, file4</p></td>
   <td><p>file2, file3, file4</p></td>
   <td><p>file3, file4</p></td>
   <td><p>file4</p></td>
   <td><p>leeg</p></td>
   <td><p>file5</p></td>
   <td><p>leeg</p></td>
  </tr>
  <tr>
   <td><p>Werkgebied</p></td>
   <td><p>leeg</p></td>
   <td><p>file1</p></td>
   <td><p>file2</p></td>
   <td><p>file3</p></td>
   <td><p>file4</p></td>
   <td><p>leeg</p></td>
   <td><p>file5</p></td>
  </tr>
  <tr>
   <td><p>Uitvoer</p></td>
   <td><p>leeg</p></td>
   <td><p>leeg</p></td>
   <td><p>file1_out</p></td>
   <td><p>file1_out, file2_out</p></td>
   <td><p>file1_out, file2_out</p></td>
   <td><p>file1_out, file2_out, file4_out</p></td>
   <td><p>file1_out, file2_out, file4_out</p></td>
  </tr>
  <tr>
   <td><p>Mislukt</p></td>
   <td><p>leeg</p></td>
   <td><p>leeg</p></td>
   <td><p>leeg</p></td>
   <td><p>leeg</p></td>
   <td><p>file3_fail, file3 </p></td>
   <td><p>file3_fail, file3 </p></td>
   <td><p>file3_fail, file3 </p></td>
  </tr>
  <tr>
   <td><p>Behouden</p></td>
   <td><p>leeg</p></td>
   <td><p>leeg</p></td>
   <td><p>file1 </p></td>
   <td><p>file1, file2 </p></td>
   <td><p>file1, file2 </p></td>
   <td><p>file1, file2, file4 </p></td>
   <td><p>file1, file2, file4 </p></td>
  </tr>
 </tbody>
</table>

In de volgende tekst wordt bestandmanipulatie voor elke keer beschreven:

**T1:** De vier voorbeeldbestanden worden in de invoermap geplaatst.

**T2:** Met de servicebewerking wordt file1 voor bewerking naar de werkgebiedmap verplaatst.

**T3:** Met de servicebewerking wordt file2 verplaatst naar de werkgebiedmap voor bewerking. De resultaten van file1 worden in de uitvoermap geplaatst en file1 wordt naar de opslagmap verplaatst.

**T4:** Met de servicebewerking wordt file3 voor bewerking in de werkgebiedmap geplaatst. Het plaatst de resultaten van file2 in de outputomslag, en het plaatst file2 in sparen omslag.

**T5:** Met de servicebewerking wordt file4 voor bewerking in de werkgebiedmap geplaatst. De manipulatie van file3 ontbreekt, en de de dienstverrichting plaatst het in de mislukkingsomslag.

**T6:** Met de servicebewerking wordt file5 in de invoermap geplaatst. Het plaatst de resultaten van file4 in de outputomslag, plaatst file4 in het bewaren omslag.

**T7:** Met de servicebewerking wordt file5 in de werkgebiedmap geplaatst om te worden bewerkt.

## Back-up maken van gecontroleerde mappen {#backing-up-watched-folders}

U wordt aangeraden een back-up te maken van het volledige gecontroleerde bestandssysteem naar een ander bestandssysteem.

## Gecontroleerde mappen herstellen {#restoring-watched-folders}

In deze sectie wordt beschreven hoe u gecontroleerde mappen kunt herstellen. Gecontroleerde mappen activeren vaak kortstondige processen die binnen een minuut worden voltooid. In dergelijke gevallen voorkomt het terugzetten van de gecontroleerde map met een back-up die om het uur wordt uitgevoerd, gegevensverlies niet.

Bijvoorbeeld, als een steun op tijd T1 wordt genomen en de server bij T7 ontbreekt, dan wordt file1, file2, file3, en file4 reeds gemanipuleerd. Het herstellen van de gecontroleerde map met een back-up op T1 voorkomt gegevensverlies niet.

Als er een recentere back-up is gemaakt, kunt u de bestanden herstellen. Bedenk bij het terugzetten van de bestanden in welke map met gecontroleerde maphiërarchie het huidige bestand zich bevindt:

**Werkgebied:** Bestanden in deze map worden opnieuw verwerkt nadat de gecontroleerde map is hersteld.

**Invoer:** Bestanden in deze map worden opnieuw verwerkt nadat de gecontroleerde map is hersteld.

**Resultaat:** Bestanden in deze map worden niet verwerkt.

**Uitvoer:** Bestanden in deze map worden niet verwerkt.

**Behouden:** Bestanden in deze map worden niet verwerkt.

## Strategieën om gegevensverlies te minimaliseren {#strategies-to-minimize-data-loss}

Met de volgende strategieën kunt u het gegevensverlies van de uitvoer- en invoermap tot een minimum beperken bij het herstellen van een gecontroleerde map:

* Maak regelmatig een back-up van de uitvoermappen en de mislukkingsmappen, bijvoorbeeld om het verlies van resultaat- en foutbestanden te voorkomen.
* Maak een back-up van de invoerbestanden in een andere map dan de gecontroleerde map. Dit zorgt ervoor dat bestanden na herstel beschikbaar zijn voor het geval u de bestanden niet kunt vinden in de uitvoermap of de map voor mislukkingen. Zorg ervoor dat uw schema voor het benoemen van bestanden consistent is.

   Als u bijvoorbeeld de uitvoer opslaat met de `%F.`*extensie *, heeft het uitvoerbestand dezelfde naam als het invoerbestand. Hierdoor kunt u bepalen welke invoerbestanden worden gemanipuleerd en welke opnieuw moeten worden verzonden. Als u alleen file1_out in de resultaatmap ziet en niet file2_out, file3_out en file4_out, moet u file2, file3 en file4 opnieuw verzenden.

* Als de beschikbare controlemap ouder is dan de tijd die nodig is om de taak te verwerken, moet u het systeem toestaan een nieuwe controlemap te maken en de bestanden automatisch in de invoermap te plaatsen.
* Als de meest recente beschikbare back-up niet recent genoeg is, is de back-uptijd korter dan de tijd die nodig is om de bestanden te verwerken en de gecontroleerde map wordt hersteld, is het bestand in een van de volgende verschillende stadia gemanipuleerd:

   * **Fase 1:** In de invoermap
   * **Fase 2:** Gekopieerd naar de werkgebiedmap, maar het proces wordt nog niet aangeroepen
   * **Fase 3:** Gekopieerd naar de werkgebiedmap en het proces wordt aangeroepen
   * **Fase 4:** Bezig met manipuleren
   * **Fase 5:** Resultaten geretourneerd
   Bestanden in werkgebied 1 worden gemanipuleerd. Als bestanden zich in werkgebied 2 of 3 bevinden, plaatst u ze in de invoermap zodat ze opnieuw kunnen worden gemanipuleerd.

   >[!NOTE]
   >
   >Als een bestand meerdere keren wordt bewerkt, wordt gegevensverlies voorkomen, maar kunnen de resultaten worden gedupliceerd.

## Conclusie {#conclusion}

Vanwege de dynamische en voortdurend veranderende aard van een gecontroleerde map, moeten gecontroleerde mappen worden hersteld met bestanden waarvan binnen een dag een back-up wordt gemaakt. U kunt het beste een back-up van de resultaten maken, de invoermap op een server opslaan en invoerbestanden bijhouden, zodat u de taak opnieuw kunt verzenden als er een fout optreedt.
