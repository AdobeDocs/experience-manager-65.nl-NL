---
title: Een gecontroleerde map maken of configureren
seo-title: Een gecontroleerde map maken of configureren
description: Leer hoe u een controlemap maakt of verwijdert of de eigenschappen van een bestaande controlemap wijzigt.
seo-description: Leer hoe u een controlemap maakt of verwijdert of de eigenschappen van een bestaande controlemap wijzigt.
uuid: 659d4d8c-99b8-40dd-b884-bfee4d476fe1
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: publish
discoiquuid: 0ce7b338-6686-49b3-b58b-e7ab6b670708
translation-type: tm+mt
source-git-commit: 726163106ddb80600eaa7cc09b1a2e9b035a223e

---


# Een gecontroleerde map maken of configureren {#create-or-configure-a-watched-folder}

Een beheerder kan een netwerkmap, ook wel een *controlemap* genoemd, zo configureren dat wanneer een gebruiker een bestand (zoals een PDF-bestand) in de controlemap plaatst, een vooraf geconfigureerde bewerking wordt gestart en het bestand wordt gemanipuleerd. Nadat de opgegeven bewerking is uitgevoerd, slaat de bewerking het gewijzigde bestand op in een opgegeven uitvoermap. Zie Help bij [Beheer](/help/forms/using/admin-help/configuring-watched-folder-endpoints.md)voor meer informatie over het beheren van een gecontroleerde map.

U kunt de gebruikersinterface voor gecontroleerde mappen gebruiken voor:

* Een controlemap maken
* Eigenschappen van een bestaande controlemap wijzigen
* Een gecontroleerde map verwijderen

## Een controlemap maken {#create-a-watched-folder}

Controleer het volgende voordat u een gecontroleerde map configureert:

* Gecontroleerde mappen zijn een geavanceerde functie van AEM-formulieren. Hiervoor is een invoegpakket voor AEM-formulieren vereist. Zorg ervoor dat het juiste invoegpakket voor AEM Forms is geïnstalleerd en geconfigureerd.
* U kunt de gecontroleerde map maken op een gedeelde of lokale opslaglocatie. Zorg ervoor dat gebruikers van AEM-formulieren die zijn geconfigureerd om de gecontroleerde map uit te voeren, lees- en schrijfmachtigingen hebben voor de gecontroleerde map.
* U kunt een service, workflow of script gebruiken om een bewerking met een gecontroleerde map te automatiseren. Zorg ervoor dat de bijbehorende service, workflow of een script is gemaakt en klaar is om te worden uitgevoerd. Voor informatie over het creëren van de Dienst, het Werkschema, en het Manuscript, zie [Verschillende methodes om dossiers](/help/forms/using/watched-folder-in-aem-forms.md#various-methods-for-processing-files)te verwerken.
* Een gecontroleerde map heeft verschillende eigenschappen. Zie [Gecontroleerde mapeigenschappen](watched-folder-in-aem-forms.md#watchedfolderproperties).

Voer de volgende stappen uit om een controlemap te maken:

1. Tik op het pictogram **Adobe Experience Manager** in de linkerbovenhoek van het scherm.
1. Tik op **Gereedschappen** > **Formulieren** > Gecontroleerde map **configureren.** Er wordt een lijst met al geconfigureerde gecontroleerde mappen weergegeven.
1. Tik op **Nieuw**. Er wordt een lijst weergegeven met velden die vereist zijn om de controlemap te maken:

   * **Naam**: Hiermee wordt de gecontroleerde map aangegeven. Gebruik voor de naam alleen alfanumerieke tekens.
   * **Pad**: Hier geeft u de locatie van de gecontroleerde map op. In een gegroepeerde omgeving, moet dit plaatsen aan een gedeelde netwerkomslag richten die voor elke gebruiker toegankelijk is die AEM op verschillende knopen van een cluster in werking stelt.
   * **Bestanden verwerken met**: Het type proces dat moet worden gestart. U kunt werkschema, manuscript, of de dienst specificeren.
   * **Servicenaam/Script-pad/workflowpad**: Het gedrag van het veld is gebaseerd op de waarde die is opgegeven voor het veld **Bestanden verwerken met** . U kunt de volgende waarden opgeven:

      * Geef voor Workflow het workflowmodel op dat moet worden uitgevoerd. Bijvoorbeeld /etc/workflow/models/&lt;workflow_naam>/jcr:content/model
      * Geef bij Script het JCR-pad op van het script dat moet worden uitgevoerd. Bijvoorbeeld /etc/watchfolder/test/testScript.ecma
      * Voor de Dienst, specificeer de filter die voor de plaats van de plaats van een dienst OSGi wordt gebruikt. De service is geregistreerd als een implementatie van com.adobe.aemfd.watchfolder.service.api.ContentProcessor Interface. De volgende code is bijvoorbeeld een aangepaste implementatie van de interface ContentProcessor met een aangepaste eigenschap (foo=bar).
   >[!NOTE]
   >
   >Als u **Service** hebt geselecteerd voor het veld **Bestanden verwerken met** , moet de waarde van het veld Servicenaam (inputProcessorType) tussen haakjes staan. Bijvoorbeeld (foo=bar).

   ```java
   @Component(metatype = true, immediate = true, label = "WF Test Service", description = "WF Test Service")
   @Service(value = {OutputWriter.class, ContentProcessor.class})
   @Property(name = "foo", value = "bar")
   public class OutputWriter implements ContentProcessor {
   ```

   * **Uitvoerbestandspatroon**: Geef een door puntkomma&#39;s (;) gescheiden lijst met patronen op die een gecontroleerde map gebruikt om de naam en locatie van uitvoerbestanden en -mappen te bepalen. Zie [Bestandspatronen](/help/forms/using/admin-help/configuring-watched-folder-endpoints.md#about-file-patterns)voor meer informatie over bestandspatronen.


1. Tik op **Geavanceerd**. Het geavanceerde tabblad bevat meer velden. De meeste van deze velden bevatten een standaardwaarde.

   * **Filter Payload Mapper:** Wanneer u een controlemap maakt, maakt deze een mappenstructuur in de map die wordt gecontroleerd. De mapstructuur heeft mappen voor werkgebied, resultaat, behoud, invoer en mislukking. De mappenstructuur kan dienen als invoerlading aan het werkschema en output van een werkschema goedkeuren. Het kan ook een lijst van mislukkingspunten maken, als om het even welk. De structuur van een lading is verschillend van de structuur van een gelete op omslag. U kunt aangepaste scripts schrijven om de structuur van een gecontroleerde map toe te wijzen aan de payload. Een dergelijk script wordt een payload mapfilter genoemd. Er zijn twee uitvoeringen beschikbaar voor de payload mapper box. Als u geen [aangepaste implementatie](/help/forms/using/watched-folder-in-aem-forms.md#creating-a-custom-payload-mapper-filter)hebt, gebruikt u een van de implementaties buiten de box:

      * **Standaardmapper:** Gebruik de standaard payload mapper om de invoer- en uitvoerinhoud van de gecontroleerde mappen in aparte invoer- en uitvoermappen in de payload te houden.
      * **Simple File-based payload mapper:** Gebruik de Simple File-based payload mapper om invoer- en uitvoerinhoud rechtstreeks in de payload-map te houden. Er wordt geen extra hiërarchie gemaakt, zoals de standaardmapper.
   * **Run-modus**: Geef de lijst met door komma&#39;s gescheiden toegestane uitvoermodi op voor uitvoering van de workflow.
   * **Nog niet actieve bestanden uitstellen na**: Geef op hoeveel seconden moet worden gewacht voordat een invoerbestand/map die al voor verwerking is opgepakt, wordt beschouwd als een time-out en gemarkeerd als een fout. Het time-outmechanisme activeert alleen wanneer de waarde voor deze eigenschap een positief getal is.
   * **Timed-out Staged Files verwijderen bij het draaien**: Als deze optie is ingeschakeld, wordt het mechanisme **Tijd uit gefaseerde bestanden na** alleen geactiveerd wanneer het wijzigen van de snelheid voor de gecontroleerde map is ingeschakeld.
   * **Invoermap scannen na elke:** Geef het tijdsinterval in seconden op voor het scannen van de controlemap op invoer. Tenzij de Throttle-instelling is ingeschakeld, moet het pollinterval langer zijn dan de tijd die nodig is om een gemiddelde taak te verwerken. anders, zou het systeem kunnen overbelast zijn. De waarde van het interval moet groter dan of gelijk aan één zijn.
   * **Bestandspatroon** uitsluiten: Geef een door puntkomma&#39;s (;) gescheiden lijst met patronen op die een gecontroleerde map gebruikt om te bepalen welke bestanden en mappen moeten worden gescand en opgepakt. Bestanden of mappen met het opgegeven patroon worden niet gescand voor verwerking. Zie [Bestandspatronen](/help/forms/using/admin-help/configuring-watched-folder-endpoints.md#about-file-patterns)voor meer informatie over bestandspatronen.
   * **Inclusief bestandspatroon**: Geef een door puntkomma&#39;s (;) gescheiden lijst met patronen op die in de gecontroleerde map wordt gebruikt om te bepalen welke mappen en bestanden worden gescand en opgehaald. Als bijvoorbeeld het Include Patroon van het Dossier input&amp;amp is;ast;, alle dossiers en omslagen die input&amp;amp aanpassen;ast; worden opgepakt. De standaardwaarde is &amp;ast; en geeft alle bestanden en mappen aan. Zie [Bestandspatronen](/help/forms/using/admin-help/configuring-watched-folder-endpoints.md#about-file-patterns)voor meer informatie over bestandspatronen.
   * **Wacht tijd:** Geef in milliseconden de tijd op die moet worden gewacht voordat u een map of bestand scant nadat deze is gemaakt. Als de wachttijd bijvoorbeeld 3.600.000 milliseconden (een uur) is en het bestand een minuut geleden is gemaakt, wordt dit bestand opgepikt nadat 59 minuten zijn verstreken. De standaardwaarde is 0.

      Deze instelling is handig om ervoor te zorgen dat alle inhoud van een bestand of map naar de invoermap wordt gekopieerd. Als u bijvoorbeeld een groot bestand hebt dat moet worden verwerkt en het downloaden van het bestand duurt tien minuten, stelt u de wachttijd in op 10&amp;ast;60 &amp;ast;1000 milliseconden. Met dit interval wordt voorkomen dat de gecontroleerde map het bestand scant als het nog geen tien minuten oud is.

   * **Resultaten verwijderen die ouder zijn dan:** Geef in aantal dagen op hoe lang u moet wachten voordat u de bestanden en mappen verwijdert die ouder zijn dan de opgegeven waarde. Deze instelling is handig om ervoor te zorgen dat de resultaatmap niet vol wordt. De waarde -1 dagen geeft aan dat u de resultatenmap nooit wilt verwijderen. De standaardwaarde is -1.
   * **Naam van resultaatmap:** Geef de naam op van de map waarin u de resultaten wilt opslaan. Als de resultaten niet in deze map worden weergegeven, controleert u de map met foutmeldingen. Alleen-lezen bestanden worden niet verwerkt en opgeslagen in de map met foutmeldingen. U kunt een absoluut of relatief pad gebruiken met de volgende bestandspatronen:

      * %F = voorvoegsel bestandsnaam
      * %E = bestandsnaamextensie
      * %Y = jaar (volledig)
      * %y = jaar (laatste twee cijfers)
      * %M = maand
      * %D = dag van de maand
      * %d = dag van het jaar
      * %H = uur (24-uurs klok)
      * %h = uur (12-uurs klok)
      * %m = minuut
      * %s = seconde
      * %l = millisecond
      * %R = willekeurig getal (tussen 0 en 9)
      * %P = proces- of taak-id
      * Als het op 17 juli 2009 bijvoorbeeld 8 uur &#39;s middags is en u C:/Test/WF0/failure/%Y/%M/%D/%H/ opgeeft, is de resultatenmap C:/Test/WF0/failure/2009/07/17/20.
      * Als het pad niet absoluut maar relatief is, wordt de map in de controlemap gemaakt. De standaardwaarde is result/%Y/%M/%D/. Dit is de resultatenmap in de gecontroleerde map. Zie [Bestandspatronen](/help/forms/using/admin-help/configuring-watched-folder-endpoints.md#about-file-patterns)voor meer informatie over bestandspatronen.
   * **Mapnaam mislukt:** Geef de map op waarin mislukte bestanden worden opgeslagen. Deze locatie is altijd relatief ten opzichte van de gecontroleerde map. U kunt bestandspatronen gebruiken, zoals beschreven in Resultaatmap.
   * **Mapnaam behouden:** Geef de map op waarin de bestanden worden opgeslagen nadat het scannen en ophalen is gelukt. Het pad kan een absolute, relatieve of null-map zijn. U kunt bestandspatronen gebruiken, zoals beschreven in Resultaatmap. De standaardwaarde is preserve/%Y/%M/%D/.
   * **Batchgrootte:** Geef het aantal bestanden of mappen op dat per scan moet worden opgepakt. Het voorkomt overbelasting op het systeem; te veel bestanden tegelijk scannen kan ertoe leiden dat de toepassing vastloopt. De standaardwaarde is 2.

      Als het scaninterval klein is, scannen de threads de invoermap vaak. Als bestanden vaak in de controlemap worden neergezet, moet u het scaninterval klein houden. Als de dossiers niet vaak worden gelaten vallen, gebruik een groter aftasteninterval zodat de andere diensten de draden kunnen gebruiken.

   * **Throttle On:** Als deze optie is ingeschakeld, wordt het aantal controletaken dat door AEM-formulieren op een bepaald moment wordt verwerkt, beperkt. De waarde voor Batchgrootte bepaalt het maximale aantal taken. For more information, see [throttling](/help/forms/using/admin-help/configuring-watched-folder-endpoints.md#about-throttling)
   * **Bestaande bestanden met dezelfde naam** overschrijven: Als u de waarde True instelt, worden de bestanden in de map results en preserve overschreven. Wanneer ingesteld op Onwaar, worden bestanden en mappen met het numerieke indexachtervoegsel gebruikt voor de naam. De standaardwaarde is False.
   * **Bestanden behouden bij fout:** Als u deze optie instelt op Waar, blijven de invoerbestanden behouden in het geval van een fout. De standaardwaarde is true.
   * **Bestanden opnemen met patroon:** Geef een door puntkomma&#39;s (;) gescheiden lijst met patronen op die in de gecontroleerde map wordt gebruikt om te bepalen welke mappen en bestanden worden gescand en opgehaald. Als bijvoorbeeld het Include-bestandspatroon wordt ingevoerd, worden alle bestanden en mappen opgehaald die overeenkomen met de invoer. Voor meer informatie, zie de Hulp van het [Beleid](/help/forms/using/admin-help/configuring-watched-folder-endpoints.md)
   * **Gecontroleerde map asynchroon aanroepen:** Identificeert het aanroepingstype als asynchroon of synchroon. De standaardwaarde is asynchroon. Asynchroon wordt aanbevolen voor langlevende processen, terwijl synchroon wordt aanbevolen voor voorbijgaande of kortstondige processen.
   * **Controlemap inschakelen:** Als deze optie is ingeschakeld, wordt de controlemap ingeschakeld. De standaardwaarde is True.



## Eigenschappen van een bestaande controlemap wijzigen {#modify-properties-of-an-existing-watched-folder}

U kunt niet alleen de naam van de gecontroleerde map wijzigen, maar ook alle eigenschappen van een bestaande controlemap wijzigen. Voer de volgende stappen uit om eigenschappen van een bestaande controlemap te wijzigen:

1. Tik op het pictogram **Adobe Experience Manager** in de linkerbovenhoek van het scherm.
1. Tik op **Gereedschappen** > **Formulieren** > Gecontroleerde map **configureren.** Er wordt een lijst met al geconfigureerde gecontroleerde mappen weergegeven.
1. Selecteer links in het scherm Gecontroleerde map de controlemap en tik op **Bewerken.** Er wordt een lijst weergegeven met velden die nodig zijn om de controlemap te maken. De velden op het tabblad **Standaard** zijn verplicht. Het geavanceerde tabblad bevat meer velden. De meeste van deze velden bevatten een standaardwaarde. U kunt deze eigenschappen naar wens wijzigen.
1. Tik op **Bijwerken** nadat u de eigenschappen hebt gewijzigd. De gewijzigde eigenschappen worden opgeslagen.

